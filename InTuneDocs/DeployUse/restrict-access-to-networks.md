---
title: Restringir el acceso a redes con Cisco ISE | Microsoft Intune
description: Use Cisco ISE con Intune de forma que los dispositivos se inscriban y cumplan la directiva de Intune antes de que tengan acceso al Wi-Fi y a la VPN controlados por Cisco ISE.
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
ms.sourcegitcommit: 40194f4359d0889806e080a4855b8e1934b667f9
ms.openlocfilehash: 9d6b7198e3c2e30898a8ec83785c7f3b777eda5f


---

# Usar Cisco ISE con Microsoft Intune
La integración de Intune con Cisco Identity Services Engine (ISE) le permite crear directivas de red en su entorno de ISE mediante el estado de cumplimiento y la inscripción de dispositivos de Intune. Puede usar estas directivas para garantizar que el acceso a la red de la compañía esté restringido a los dispositivos administrados por Intune y a los que cumplen con sus directivas.

## Pasos de configuración

Para habilitar esta integración, no necesita realizar ninguna configuración en su inquilino de Intune. Necesitará proporcionar permisos a su servidor de Cisco ISE para tener acceso al inquilino de Intune. Después de completar este paso, el resto de la configuración tendrá lugar en su servidor de Cisco ISE. En este artículo se proporcionan instrucciones sobre cómo proporcionar permisos a su servidor de ISE para tener acceso a su inquilino de Intune.

### Paso 1: Administrar los certificados
1. En la consola de Azure Active Directory (Azure AD), exporte el certificado.

#### Internet Explorer 11


   a. Ejecute Internet Explorer como administrador e inicie sesión en la consola de Azure AD.

   b. Elija el icono de bloqueo en la barra de direcciones y elija **Ver certificados**.

   c. En la pestaña **Detalles** de las propiedades del certificado, elija **Copiar a archivo**.

   d. En la página **Asistente para exportación de certificados**, elija **Siguiente**.

   e. En la página **Formato de archivo de exportación**, deje el valor predeterminado, **DER binario codificado X.509 (.CER)** y elija **Siguiente**.  

   f. En la página **Archivo que se va a exportar**, elija **Examinar** para seleccionar una ubicación en la que guardar el archivo y proporcione un nombre de archivo. Aunque parezca que está eligiendo un archivo que se va a exportar, realmente está asignando un nombre al archivo en el que se guardará el certificado exportado. Elija **Siguiente** &gt; **Finalizar**.

#### Safari

 a. Inicie sesión en la consola de Azure AD.

b. Elija el icono de bloqueo &gt; **Más información**.

   c. Elija **Ver certificado** &gt; **Detalles**.

   d. Elija el certificado y, después, elija **Exportar**.  

> [!IMPORTANT]
>
> Compruebe la fecha de expiración del certificado, ya que tendrá que exportar e importar un certificado nuevo cuando este expire.


2. Desde la consola de ISE, importe el certificado de Intune (el archivo que ha exportado) en el almacén de **Certificados de confianza**.


### Obtener un certificado autofirmado de ISE 

1.  En la consola de ISE, vaya a **Administración** > **Certificados** > **Certificados de sistema** > **Generar certificado autofirmado**.  
2.       Exportar el certificado autofirmado.
3. En un editor de texto, edite el certificado exportado: [comentario]: <> Preferiría no colocar un punto al final de estas dos instrucciones, podría resultar confuso.
 - Elimine ** -----BEGIN CERTIFICATE-----**.
 - Elimine ** -----END CERTIFICATE-----**.
 
Asegúrese de que todo el texto está en una única línea.


### Paso 2: Crear una aplicación para ISE en su inquilino de Azure AD
1. En la consola de Azure AD, elija **Aplicaciones** > **Agregar una aplicación** > **Agregar una aplicación que mi organización está desarrollando**.
2. Proporcione un nombre y una dirección URL para la aplicación. La dirección URL puede ser el sitio web de su empresa.
3. Descargue el manifiesto de la aplicación (un archivo JSON).
4. Edite el archivo JSON de manifiesto. En la opción denominada **Credenciales de clave**, proporcione el texto del certificado editado del Paso 1 como el valor de configuración.
5. Guarde el archivo sin cambiar su nombre.
6. Proporcione permisos a la aplicación para la API de Microsoft Graph y Microsoft Intune.

 a. Para Microsoft Graph, elija lo siguiente:
    - **Permisos de la aplicación**: leer datos de directorio
    - **Permisos delegados**:
        - tener acceso a los datos de usuario en cualquier momento
        - Iniciar la sesión de usuarios

 b. Para la API de Microsoft Intune, en **Permisos de la aplicación**, elija **Obtener cumplimiento y estado del dispositivo de Intune**.

7. Elija **Ver extremos** y copie los valores siguientes para usarlos al configurar los valores de ISE:

|Valor del Portal de Azure AD|Campo correspondiente del Portal de ISE|
|-------------------|---------------------------------|
|Extremo de API de Microsoft Azure AD Graph|Dirección URL de detección automática|
|Punto de conexión de token de OAuth 2.0|Dirección URL de emisión de token|
|Actualizar el código con el identificador de cliente|Identificador de cliente|


### Paso 3: Configurar las opciones de ISE
En la consola de administración de ISE, proporcione estos valores de configuración:
  - **Tipo de servidor**: Mobile Device Manager
  - **Tipo de autenticación**: OAuth: credenciales de cliente
  - **Detección automática**: Sí
  - **Dirección URL de detección automática**: *escriba el valor del Paso 1*.
  - **Identificador de cliente**: *escriba el valor del Paso 1*.
  - **Dirección URL de emisión de token**: *escriba el valor del Paso 1*.



## Información compartida entre su inquilino de Intune y el servidor de Cisco ISE
En esta tabla se enumera la información compartida entre su inquilino de Intune y su servidor de Cisco ISE para los dispositivos que administra Intune.

|Propiedad|  Descripción|
|---------------|------------------------------------------------------------|
|complianceState|La cadena de verdadero o falso que indica si el dispositivo es compatible o no.|
|IsManaged|La cadena de verdadero o falso que indica si el cliente se administra mediante Intune o no.|
|macAddress|La dirección MAC del dispositivo.|
|serialNumber|El número de serie del dispositivo. Se aplica solo a dispositivos iOS.|
|IMEI|El número IMEI (15 dígitos decimales: 14 dígitos más un dígito de control) o IMEISV (16 dígitos) incluye información sobre el origen, el modelo y el número de serie del dispositivo. La estructura de este número se especifica en 3GPP TS 23.003. Se aplica solo a dispositivos con tarjetas SIM.|
|udid|El único identificador de dispositivo que es una secuencia de 40 letras y números. Es específico de los dispositivos iOS.|
|MEID|Identificador de equipo móvil que es un número único global que identifica una pieza física de un equipo de estación móvil de CDMA. El formato de número se define mediante el informe S.R0048 de 3GPP2. En cambio, en términos prácticos, pueden verse como un IMEI, pero con dígitos hexadecimales. Un MEID tiene una longitud de 56 bits (14 dígitos hexadecimales). Consiste en tres campos, incluidos un código regional de 8 bits (RR), un código de fabricante de 24 bits y un número de serie asignado por el fabricante de 24 bits.|
|osVersion|La versión del sistema operativo del dispositivo.
|modelo|El modelo del dispositivo.
|fabricante|El fabricante del dispositivo.
|azureDeviceId|El identificador del dispositivo después de que haya unido el área de trabajo a Azure AD. Es un GUID vacío para los dispositivos que no están unidos.|
|lastContactTimeUtc|La fecha y la hora en que el dispositivo se ha comprobado por última vez con el servicio de administración de Intune.


## Experiencia del usuario

Cuando un usuario intenta tener acceso a los recursos mediante un dispositivo que no está inscrito, recibirá una solicitud de inscripción como la que se muestra aquí:

![Ejemplo de solicitud de inscripción](../media/cisco-ise-user-iphone.png)

Cuando un usuario decide inscribirlo, se le redirige al proceso de inscripción de Intune. La experiencia de inscripción de usuario en Intune se describe en estos temas:

- [Inscriba el dispositivo Android en Intune](/intune/enduser/enroll-your-device-in-Intune-android)</br>
- [Inscriba el dispositivo iOS en Intune](/intune/enduser/enroll-your-device-in-intune-ios)</br>
- [Inscribir el dispositivo Mac OS X en Intune](/intune/enduser/enroll-your-device-in-intune-mac-os-x)</br>
- [Inscriba el dispositivo Windows en Intune](/intune/enduser/enroll-your-device-in-intune-windows)</br>

Existe también un [conjunto descargable de instrucciones de inscripción](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a) que puede usar para crear instrucciones personalizadas para su experiencia de usuario.


### Consulte también

[Guía del administrador del motor de los servicios de identidad de Cisco, versión 2.1](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html#task_820C9C2A1A6647E995CA5AAB01E1CDEF)



<!--HONumber=Sep16_HO1-->


