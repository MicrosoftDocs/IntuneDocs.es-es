---
title: Restringir el acceso a redes con Cisco ISE | Microsoft Intune
description: Use Cisco ISE con Intune de forma que los dispositivos se inscriban y cumplan la directiva de Intune antes de que tengan acceso al WiFi y a la VPN controlada por Cisco ISE.
keywords: 
author: nbigman
manager: angrobe
ms.date: 06/24/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 5631bac3-921d-438e-a320-d9061d88726c
ms.reviewer: muhosabe
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 300df17fd5844589a1e81552d2d590aee5615897
ms.openlocfilehash: c516cffe416559d1d239010605227eda76c32c1b


---

# Usar Cisco ISE con Microsoft Intune
La integración de Intune con Cisco ISE le permite crear directivas de red en su entorno de ISE mediante el estado de cumplimiento y la inscripción de dispositivos de Intune. Estas directivas pueden trabajar para garantizar que el acceso a la red de su empresa está restringida a los dispositivos administrados por Intune y a los que cumplen con sus directivas.

## Configuración

Para habilitar esta integración, no necesita realizar ninguna configuración en su inquilino de Intune. Necesitará proporcionar permisos a su servidor de Cisco ISE para tener acceso a su inquilino de Intune y, una vez que esto se realice, tiene lugar el resto de la configuración en su servidor de Cisco ISE. En este artículo se proporcionan instrucciones sobre cómo proporcionar permisos a su servidor de ISE para tener acceso a su inquilino de Intune.

### Paso 1: Administrar los certificados
1. En la consola de Azure Active Directory (AAD), exporte el certificado.

    #### Internet Explorer 11

    a. Ejecute Internet Explorer como administrador e inicie sesión en la consola de AAD.

    b. Elija el icono de bloqueo en la barra de direcciones y elija **Ver certificado**.

    c. En la pestaña **Detalles** de las propiedades del certificado, elija **Copiar a archivo**.

    d. En la página **Asistente para exportación de certificados**, elija **Siguiente**.

    e. En la página **Formato de archivo de exportación**, deje el valor predeterminado, **DER binario codificado X.509 (.CER)** y elija **Siguiente**.  

    f. En la página **Archivo que se va a exportar**, elija **Examinar** para seleccionar una ubicación en la que guardar el archivo y proporcione un nombre de archivo. Aunque parezca que está eligiendo un archivo que se va a exportar, realmente está poniendo nombre al archivo en el que se guardará el certificado exportado. Elija **Siguiente** &gt; **Finalizar**.

    #### Safari

    a. Inicie sesión en la consola de AAD.

    b. Elija el icono de bloqueo &gt; **Más información**.

    c. Elija **Ver certificado** &gt; **Detalles**.

    d. Elija el certificado y, después, elija **Exportar**.  


    > [!IMPORTANT]
    > Compruebe la fecha de expiración del certificado, ya que tendrá que exportar e importar un certificado nuevo cuando este expire.



2. Desde la consola de ISE, importe el certificado de Intune (el archivo que ha exportado) en el almacén de **Certificados de confianza**.
3. En la consola de ISE, vaya a **Administración** > **Certificados** > **Certificados de sistema**.
4. Seleccione el certificado de ISE y, después, elija **Exportar**.
5. En un editor de texto, edite el certificado exportado:
 - Elimine ** -----BEGIN CERTIFICATE-----**.
 - Elimine ** -----END CERTIFICATE-----**.
 - Asegúrese de que todo el texto está en una única línea.

### Paso 2: Crear una aplicación para ISE en su inquilino de AAD
1. En la consola de Azure Active Directory (AAD), elija **Aplicaciones** > **Agregar una aplicación** > **Agregar una aplicación que mi organización está desarrollando**.
2. Proporcione un nombre y una dirección URL para la aplicación. La dirección URL puede ser el sitio web de su empresa.
3. Descargue el manifiesto de la aplicación (un archivo JSON).
4. Edite el archivo JSON de manifiesto. En la opción denominada **Credenciales de clave**, proporcione el texto del certificado editado del Paso 1 como el valor de configuración.
5. Guarde el archivo sin cambiar su nombre.
6. Proporcione permisos a la aplicación para la API de Microsoft Graph y Microsoft Intune.
    1. Para Microsoft Graph, elija lo siguiente:
        - **Permisos de la aplicación**: leer datos de directorio
        - **Permisos delegados**:
            - tener acceso a los datos de usuario en cualquier momento
          - Iniciar la sesión de usuarios
   2. Para la API de Microsoft Intune, en **Permisos de la aplicación**, elija **Obtener cumplimiento y estado del dispositivo de Intune**.

7. Elija **Ver extremos** y copie los valores siguientes para usarlos al configurar los valores de ISE:

|Valor en el Portal de AAD|Campo correspondiente del Portal de ISE|
|-------------------|---------------------------------|
|Extremo de API de Microsoft Azure AD Graph|Dirección URL de detección automática|
|Punto de conexión de token de OAuth 2.0|Dirección URL de emisión de token|
|Actualizar el código con el identificador de cliente|Identificador de cliente|


### Paso 3: Configurar las opciones de ISE
2. En la consola de administración de ISE, proporcione estos valores de configuración:
  - **Tipo de servidor**: Mobile Device Manager
  - **Tipo de autenticación**: OAuth: credenciales de cliente
  - **Detección automática**: Sí
  - **Dirección URL de detección automática**: escriba el valor del Paso 1
  - **Identificador de cliente**: escriba el valor del Paso 1
  - **Dirección URL de emisión de token**: escriba el valor del Paso 1



## Información compartida entre su inquilino de Intune y el servidor de Cisco ISE
En esta tabla se enumera la información compartida entre su inquilino de Intune y su servidor de Cisco ISE para los dispositivos que administra Intune.

|Propiedad|  Descripción|
|---------------|------------------------------------------------------------|
|complianceState|   Verdadero o falso (cadena) que indica si el dispositivo es compatible o no.|
|IsManaged| Verdadero o falso (indica si el cliente se administra mediante Intune o no).|
|macAddress|Dirección MAC del dispositivo.|
|serialNumber|El número de serie del dispositivo. Se aplica solo a dispositivos iOS.|
|IMEI|El IMEI (15 dígitos decimales: 14 dígitos más un dígito de control) o IMEISV (16 dígitos) incluye información sobre el origen, el modelo y el número de serie del dispositivo. La estructura del IMEI/SV se especifica en 3GPP TS 23.003. Se aplica solo a dispositivos con tarjetas SIM).|
|udid|El único identificador de dispositivo; una secuencia de 40 letras y números que es específica de los dispositivos iOS.|
|MEID|Identificador de equipo móvil; un identificador único global que identifica una pieza física de un equipo de estación móvil de CDMA. El formato de número se define mediante el informe 3GPP2 S. R0048 pero en términos prácticos, puede verse como un IMEI pero con dígitos hexadecimales. Un MEID tiene una longitud de 56 bits (14 dígitos hexadecimales). Consiste en tres campos, incluidos un código regional de 8 bits (RR), un código de fabricante de 24 bits y un número de serie asignado por el fabricante de 24 bits.|
|osVersion| Versión de sistema operativo del dispositivo.
|modelo|Modelo del dispositivo.
|fabricante|Fabricante del dispositivo.
|azureDeviceId| El identificador del dispositivo después de que haya unido el lugar de trabajo a Azure Active Directory. Será un GUID vacío para los dispositivos que no están unidos.|
|lastContactTimeUtc|La fecha y la hora en que el dispositivo se ha comprobado por última vez con el servicio de administración de Intune.


## Experiencia del usuario

Cuando un usuario intenta tener acceso a los recursos mediante un dispositivo que no está inscrito, recibirá una solicitud de inscripción como la que se muestra aquí:

![Ejemplo de solicitud de inscripción](../media/cisco-ise-user-iphone.png)

Cuando el usuario decide inscribirlo, se le redirige al proceso de inscripción de Intune. La experiencia de inscripción de usuario en Intune se describe en estos temas:

- [Inscriba el dispositivo Android en Intune](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Inscriba el dispositivo iOS en Intune](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Inscribir el dispositivo Mac OS X en Intune](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Inscriba el dispositivo Windows en Intune](/intune/enduser/enroll-your-device-in-intune-windows)</br>

Existe también un [conjunto descargable de instrucciones de inscripción](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) que puede usar para crear instrucciones personalizadas para su experiencia de usuario.


### Consulte también

[Guía del administrador del motor de los servicios de identidad de Cisco, versión 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)



<!--HONumber=Jul16_HO4-->


