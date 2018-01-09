---
title: "Adición de aplicaciones de la Tienda Windows a Intune"
titleSuffix: Azure portal
description: "Obtenga información sobre cómo agregar aplicaciones de la tienda Windows a Intune\"."
keywords: 
author: Erikre
ms.author: erikre
manager: angrobe
ms.date: 05/04/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 07241b6d-86d8-4abb-83a2-3fc5feae5788
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 19339bee8b362b1168e62da9716dbfd3144e85e7
ms.sourcegitcommit: 833b1921ced35be140f0107d0b4205ecacd2753b
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/04/2018
---
# <a name="how-to-add-windows-store-apps-to-microsoft-intune"></a>Adición de aplicaciones de la tienda de Windows a Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]


1. Inicie sesión en el portal de Azure.
2. Elija **Más servicios** > **Supervisión y administración** > **Intune**.
3. En la hoja **Intune**, elija **Administrar aplicaciones**.
4. En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5. Encima de la lista de aplicaciones, elija **Agregar**.
6. En la hoja **Agregar aplicación**, elija **Información de la aplicación**.
7. En la hoja **Editar aplicación**, configure la siguiente información. Cuando haya terminado, haga clic en **Aceptar**. Dependiendo de la aplicación que haya elegido, algunos de los valores de esta hoja pueden haber sido rellenados automáticamente:
    - **Nombre de la aplicación**: escriba el nombre de la aplicación tal como se mostrará en el Portal de empresa. Asegúrese de que todos los nombres de aplicación que usa son únicos. Si el mismo nombre de aplicación existe dos veces, solo se mostrará a los usuarios una de las aplicaciones en el portal de empresa.
    - **Descripción de la aplicación**: escriba una descripción de la aplicación. Se mostrará a los usuarios en el portal de empresa.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **URL de la tienda de aplicaciones**: escriba la dirección URL de la tienda de aplicaciones de la aplicación que quiere crear.
    - **Sistema operativo mínimo**: en la lista, elija la versión mínima del sistema operativo en la que se puede instalar la aplicación. Si la aplicación se asigna a un dispositivo con un sistema operativo anterior, no se instalará.
    - **Categoría (opcional)**: seleccione una o varias de las categorías de aplicaciones integradas o una categoría que haya creado. Así les resultará más fácil a los usuarios encontrar la aplicación cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: la aplicación se muestra de forma destacada en la página principal del Portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se mostrará a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Cargar icono**: carga un icono que se asociará a la aplicación. Será el icono que se muestre con la aplicación cuando los usuarios examinen el portal de empresa.
8. Cuando haya terminado, en la hoja **Agregar aplicación**, elija **Guardar**.

La aplicación que ha creado se muestra en la lista de aplicaciones donde puede asignarla a los grupos que elija. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](apps-deploy.md).

## <a name="manually-assign-windows-10-company-portal-app"></a>Asignación manual de la aplicación del Portal de empresa para Windows 10
Los usuarios finales pueden instalar la aplicación del Portal de empresa desde la Microsoft Store para administrar dispositivos e instalar aplicaciones. Pero si sus necesidades empresariales requieren que asigne la aplicación del Portal de empresa, puede asignar manualmente dicha aplicación para Windows 10 directamente desde Intune, aunque no haya integrado Intune con la Tienda Microsoft para Empresas.

 > [!NOTE]
 > Esta opción requiere asignar actualizaciones manuales cada vez que se publica una actualización de la aplicación.

1. Inicie sesión con su cuenta en la [Tienda Microsoft para Empresas](https://www.microsoft.com/business-store) y adquiera la versión de **licencia sin conexión** de la aplicación del Portal de empresa.  
2. Cuando haya adquirido la aplicación, selecciónela en la página **Inventario**.  
3. Seleccione **Windows 10 all devices** (Todos los dispositivos Windows 10) como la **plataforma**, luego, la **arquitectura** correspondiente y, finalmente, haga clic en Descargar. No se necesita un archivo de licencia de la aplicación para esta aplicación.
![Imagen de Windows 10 all devices (Todos los dispositivos Windows 10) y los detalles del paquete de la arquitectura x86 para su descarga](./media/Win10CP-all-devices.png)
4. Descargue todos los paquetes en "Marcos necesarios". Debe hacerse para las arquitecturas x86, x64 y ARM, lo que produce un total de 9 paquetes, tal como se muestra a continuación.

![Imagen de los archivos de dependencia para descargar ](./media/Win10CP-dependent-files.png)
5. Antes de cargar la aplicación del Portal de empresa en Intune, cree una carpeta (por ejemplo, C:&#92;Company Portal) con los paquetes estructurados de la manera siguiente:
  1. Colocar el paquete del Portal de empresa en C:\Company Portal. Cree también una subcarpeta Dependencias en esta ubicación.  
  ![Imagen de la carpeta Dependencias guardada con el archivo APPXBUN](./media/Win10CP-Dependencies-save.png)
  2. Coloque los nueve paquetes de dependencias en la carpeta Dependencias.  
  Si las dependencias no se colocan con este formato, Intune no podrá reconocer y cargarlos durante la carga de los paquetes, con lo que se producirá el siguiente error.  
  ![La dependencia de aplicación de Windows para este instalador de software no se encontró en la carpeta de la aplicación. Puede continuar con la creación y asignación de esta aplicación, pero no se ejecutará hasta que se proporcione la dependencia de aplicación de Windows correspondiente.](./media/Win10CP-error-message.png)
6. Vuelva a Intune y cargue la aplicación del Portal de empresa como una nueva aplicación. Asígnela como una aplicación necesaria para el conjunto de usuarios de destino deseado.  

Consulte [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Implementación de appxbundle con dependencias a través de la MDM de Microsoft Intune) para obtener más información sobre cómo Intune controla las dependencias de aplicaciones universales.  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>¿Cómo puedo actualizar el Portal de empresa en los dispositivos de mis usuarios si ya han instalado las aplicaciones anteriores desde la Tienda?
Si los usuarios ya han instalado las aplicaciones del Portal de empresa para Windows 8.1 o Windows Phone 8.1 desde la Tienda, recibirán automáticamente la nueva versión sin que tengan que hacer nada. Si la actualización no se realiza, pida a los usuarios que comprueben que están habilitadas en sus dispositivos las actualizaciones automáticas para las aplicaciones de la Tienda.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente del Portal de empresa para Windows 8.1 a la versión para Windows 10?
La ruta de migración recomendada es eliminar la asignación de la aplicación del Portal de empresa para Windows 8.1 estableciendo la acción de asignación en "Desinstalar". Después, se puede asignar la aplicación del Portal de empresa para Windows 10 con cualquiera de las opciones anteriores.  

Si necesita transferir localmente la aplicación y asignó el Portal de empresa para Windows 8.1 sin firmar con el certificado de Symantec, siga los pasos de la sección anterior sobre la asignación directa a través de Intune para completar la actualización.

Si necesita transferir localmente la aplicación y firmó y asignó el Portal de empresa para Windows 8.1 con el certificado de firma de código de Symantec, siga los pasos descritos en la sección siguiente.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente y firmada del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 a la versión para Windows 10?
La ruta de migración recomendada es eliminar la asignación de la aplicación del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 estableciendo la acción de asignación en "Desinstalar". Después, se puede asignar con normalidad la aplicación del Portal de empresa para Windows 10.  

Si no, habrá que actualizar y firmar correctamente la aplicación del Portal de empresa para Windows 10 para garantiza que se respeta la ruta de actualización.  

Si la aplicación del Portal de empresa para Windows 10 está firmada y asignada de esta manera, debe repetir este proceso para cada nueva actualización de la aplicación cuando esté disponible en la Tienda. La aplicación no se actualizará automáticamente cuando se actualice la Tienda.  

Así es cómo tiene que firmar y asignar la aplicación:

1. Descargue el script de firma de la aplicación del Portal de empresa para Windows 10 con Microsoft Intune en [https://aka.ms/win10cpscript](https://aka.ms/win10cpscript).  Este script requiere instalar Windows SDK para Windows 10 en el equipo host. Si quiere descargar Windows SDK para Windows 10, visite [https://go.microsoft.com/fwlink/?LinkId=619296](https://go.microsoft.com/fwlink/?LinkId=619296).
2. Descargue la aplicación del Portal de empresa para Windows 10 desde la Tienda Microsoft para Empresas, tal como se describe anteriormente.  
3. Ejecute el script con los parámetros de entrada que se detallan en el encabezado del script para firmar la aplicación del Portal de empresa para Windows 10 (que detalla abajo). Las dependencias no tienen que pasarse al script. Solo se necesitan cuando la aplicación va a cargarse en la consola de administración de Intune.

|Parámetro | Descripción|
| ------------- | ------------- |
|InputWin10AppxBundle |La ruta de acceso donde se encuentra el archivo de origen appxbundle. |
|OutputWin10AppxBundle |La ruta de acceso de salida del archivo firmado appxbundle.  Win81Appx La ruta de acceso a la ubicación del archivo del Portal de empresa para Windows Phone 8.1 o Windows 8.1 (.APPX).|
|PfxFilePath |La ruta de acceso al archivo de certificado de firma de código móvil de empresa de Symantec (.PFX). |
|PfxPassword| La contraseña del certificado de firma de código móvil de empresa de Symantec. |
|PublisherId |El identificador del publicador de la empresa. Si está ausente, se usa el campo 'Asunto' del certificado de firma de código móvil empresarial de Symantec.|
|SdkPath | La ruta de acceso a la carpeta raíz de Windows SDK para Windows 10. Este argumento es opcional y está establecido de forma predeterminada en ${env:ProgramFiles(x86)}\Windows Kits\10.|
El script generará la versión firmada de la aplicación del Portal de empresa para Windows 10 cuando haya terminado de ejecutarse. Después, puede asignar la versión firmada de la aplicación como una aplicación LOB mediante Intune, que actualizará las versiones asignadas actualmente a esta nueva aplicación.  
