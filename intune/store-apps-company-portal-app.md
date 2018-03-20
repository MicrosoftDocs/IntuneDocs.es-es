---
title: "Adición manual de la aplicación Portal de empresa para Windows 10"
titleSuffix: Microsoft Intune
description: "Obtenga información sobre cómo agregar manualmente la aplicación Portal de empresa de Windows 10."
keywords: 
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 03/06/2018
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: bfe1a2d3-f611-4dbb-adef-c0dff4d7b810
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 06ed9395d06e2d64edcedcaadfe819ad03f1d495
ms.sourcegitcommit: 8a235b7af6ec3932c29a76d0b1aa481d983054bc
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 03/12/2018
---
# <a name="manually-add-the-windows-10-company-portal-app-using-microsoft-intune"></a>Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Los usuarios finales pueden instalar la aplicación del Portal de empresa desde la Microsoft Store para administrar dispositivos e instalar aplicaciones. Pero si sus necesidades empresariales requieren que asigne la aplicación del Portal de empresa, puede asignar manualmente dicha aplicación para Windows 10 directamente desde Intune, aunque no haya integrado Intune con la Tienda Microsoft para Empresas.

 > [!NOTE]
 > Esta opción requiere asignar actualizaciones manuales cada vez que se publica una actualización de la aplicación.

## <a name="configure-settings-to-show-offline-apps"></a>Configuración de las opciones para mostrar las aplicaciones sin conexión
1. Vaya a [Microsoft Store para Empresas](https://www.microsoft.com/business-store) y asegúrese de haber iniciado sesión con la cuenta de administrador.
2. Haga clic en la pestaña **Administrar**, situada cerca de la parte superior de la ventana.
3. Haga clic en **Configuración**, en la columna de navegación de la izquierda.
4. En la sección **Experiencia de compra**, establezca **Mostrar aplicaciones sin conexión** en **Activado**. Esto mostrará las aplicaciones con licencia sin conexión en Microsoft Store para Empresas.

## <a name="download-the-offline-company-portal-app"></a>Descarga de la aplicación Portal de empresa sin conexión
1. Busque y seleccione la aplicación **Portal de empresa**.
2. Establezca **Tipo de licencia** en **Sin conexión**.
3. Haga clic en **Obtener la aplicación** para adquirir y agregar la aplicación Portal de empresa sin conexión al inventario.
4. Haga clic en **Administrar** en la página de la aplicación **Portal de empresa**.
5. Seleccione **Todos los dispositivos Windows 10** como la **plataforma** y, luego, los valores correspondientes para **Versión mínima**, **Arquitectura** y Descargar metadatos de la aplicación**. 
6. Haga clic en **Descargar** para guardar el archivo en el equipo local.

    ![Imagen de Todos los dispositivos Windows 10 y detalles del paquete de la arquitectura x86 para descargar](./media/Win10CP-all-devices.png)

7. Descargue todos los paquetes en "Marcos necesarios". Debe hacerse para las arquitecturas x86, x64 y ARM, lo que produce un total de 12 paquetes.
8. Antes de cargar la aplicación Portal de empresa en Intune, cree una carpeta (por ejemplo, C:&#92;Portal de empresa) con los paquetes estructurados de la manera siguiente:
  - Colocar el paquete del Portal de empresa en C:\Company Portal. Cree también una subcarpeta Dependencias en esta ubicación.  

    ![Imagen de la carpeta Dependencias guardada con el archivo APPXBUN](./media/Win10CP-Dependencies-save.png)

  - Coloque los paquetes de dependencias en la carpeta *Dependencias*. 

     > [!NOTE]
     > Si las dependencias no se colocan en el formato correcto, Intune no podrá reconocer ni cargar los archivos durante la carga de los paquetes, lo que producirá un error en la carga que se mostrará en pantalla.

9. Vuelva a Microsoft Intune en Azure Portal.
10. Cargue la aplicación Portal de empresa como una aplicación nueva. Asígnela como una aplicación necesaria para el conjunto de usuarios de destino deseado.  

Consulte [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Implementación de appxbundle con dependencias a través de la MDM de Microsoft Intune) para obtener más información sobre cómo Intune controla las dependencias de aplicaciones universales.  

## <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>¿Cómo puedo actualizar el Portal de empresa en los dispositivos de mis usuarios si ya han instalado las aplicaciones anteriores desde la Tienda?
Si los usuarios ya han instalado las aplicaciones del Portal de empresa para Windows 8.1 o Windows Phone 8.1 desde la Tienda, recibirán automáticamente la nueva versión sin que tengan que hacer nada. Si la actualización no se realiza, pida a los usuarios que comprueben que están habilitadas en sus dispositivos las actualizaciones automáticas para las aplicaciones de la Tienda.   

## <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente del Portal de empresa para Windows 8.1 a la versión para Windows 10?
La ruta de migración recomendada es eliminar la asignación de la aplicación Portal de empresa para Windows 8.1 estableciendo la acción de asignación en "Desinstalar". Después de realizar esta configuración, se puede asignar la aplicación Portal de empresa para Windows 10 con cualquiera de las opciones anteriores.  

Si necesita transferir localmente la aplicación y asignó el Portal de empresa para Windows 8.1 sin firmar con el certificado de Symantec, siga los pasos de la sección anterior sobre la asignación directa a través de Intune para completar la actualización.

Si necesita transferir localmente la aplicación y firmó y asignó el Portal de empresa para Windows 8.1 con el certificado de firma de código de Symantec, siga los pasos descritos en la sección siguiente.  

## <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente y firmada del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 a la versión para Windows 10?
La ruta de migración recomendada es eliminar la asignación de la aplicación del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 estableciendo la acción de asignación en "Desinstalar". Después de realizar la configuración, se puede asignar con normalidad la aplicación Portal de empresa para Windows 10.  

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

## <a name="next-steps"></a>Pasos siguientes

- [Asignación de aplicaciones a grupos](apps-deploy.md)

