---
title: Transferir localmente aplicaciones para Windows y Windows Phone
description: "Aprenda a firmar aplicaciones de línea de negocios de modo que pueda usar Intune para implementarlas."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 06/07/2017
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
ms.custom: intune-classic
ms.openlocfilehash: 790b9b0a5feb40cd22d366438fca566b93d2138b
ms.sourcegitcommit: 1c71fff769ca0097faf46fc2b58b953ff28386e8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/08/2017
---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Firma de aplicaciones de línea de negocio para que se puedan implementar en dispositivos Windows con Intune

[!INCLUDE[both-portals](./includes/note-for-both-portals.md)]

Como administrador de Intune, puede implementar aplicaciones de línea de negocio (LOB) en dispositivos Windows y Windows 10 Mobile, incluida la aplicación del Portal de empresa. Para implementar aplicaciones .appx o .xap en dispositivos móviles Windows 10 y Windows 10, o para implementar cualquier aplicación LOB en dispositivos Windows 8.1 o Windows Phone 8.1, debe obtener un **certificado de firma de código móvil empresarial de Symantec** . El certificado de Symantec es de confianza para estas aplicaciones en los dispositivos Windows correspondientes. Puede usar su propia entidad de certificación para aplicaciones de Windows 10 y aplicaciones "universales". Este certificado se requiere para:

-   Firmar la aplicación del Portal de empresa para la implementación en equipos Windows, dispositivos Windows 10 Mobile y dispositivos Windows Phone

-   Firmar aplicaciones de línea de negocio de empresa para que Intune pueda implementarlas en dispositivos Windows

Los pasos que figuran a continuación le ayudarán a obtener los certificados necesarios y a firmar las aplicaciones. Debe registrarse como desarrollador de Microsoft y, después, adquirir un certificado de Symantec.


1. **Registrarse como desarrollador de Microsoft**<br>
   [Regístrese como desarrollador de Microsoft](http://go.microsoft.com/fwlink/?LinkId=268442) con la información de la cuenta corporativa que utilizó cuando se registró para adquirirla. Esta solicitud deberá estar autorizada por un oficial de la empresa antes de recibir un certificado de firma de código.

2. **Obtener un certificado de empresa de Symantec**<br>
  Adquiera un certificado desde el [sitio web de Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) mediante su identificador de Symantec. Después de adquirir el certificado, el aprobador corporativo que designase cuando se registró como desarrollador de Microsoft recibirá un correo electrónico en el que se pide la aprobación de la solicitud de certificado. Para más información sobre el requisito de certificado de Symantec, vea [Why Windows Phone requires a Symantec certificate?](https://technet.microsoft.com/library/dn764959.aspx#BKMK_Symantec) (¿Por qué Windows Phone pide un certificado de Symantec?). Preguntas más frecuentes sobre la inscripción de dispositivos Windows.

3.  **Importar certificados**<br>
    Una vez que se apruebe la solicitud, recibirá un correo electrónico con instrucciones para la importación de certificados. Siga las instrucciones indicadas en el correo electrónico para importar los certificados.

4.  **Comprobar los certificados importados**<br>
    Para comprobar que los certificados se han importado correctamente, vaya al complemento **Certificados**, haga clic con el botón derecho en **Certificados** y seleccione **Buscar certificados**. En el campo **Contiene** , escriba "Symantec" y haga clic en **Buscar ahora**. Los certificados que haya importado deberían aparecer en los resultados.

    ![Buscar el certificado de Symantec](./media/wit.gif)

5. **Exportar un certificado de firma**<br>
    Después de comprobar que los certificados están presentes, puede exportar el archivo .pfx para firmar el portal de empresa. Seleccione el certificado de Symantec con la “firma de código” **Propósito planteado** . Haga clic con el botón derecho en el certificado de firma de código y seleccione **Exportar**.

    ![Exportar el certificado de firma](./media/wit-walk-cert2.gif)

    En el **Asistente para exportar certificado**, seleccione **Sí, exportar la clave privada** y, a continuación, haga clic en **Siguiente**. Seleccione **Intercambio de información personal: PKCS #12 (.PFX)**  y active **Si es posible, incluir todos los certificados en la ruta de acceso de certificación**. Complete el asistente. Para obtener más información, consulte [Exportar un certificado con la clave privada](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Cargar la aplicación en Intune**<br>
    Cargue el archivo de la aplicación firmada y el certificado de firma de código para que la aplicación esté disponible para los usuarios finales.

    1.  En el portal de Intune, haga clic en **Administración** &gt; **Windows Phone**.

    2.  Haga clic en **Cargar archivo de aplicación firmado** e inicie sesión con su identificador de administrador de Intune.

    3.  Agregue el archivo de certificado (.pfx) que ha exportado a **Certificado de firma de código** y cree una contraseña para el certificado.

    4.  Complete el asistente.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Ejemplo: Descarga, firma e implementación de la aplicación del Portal de empresa para dispositivos Windows

Puede implementar la aplicación del Portal de empresa en dispositivos Windows Phone y Windows 10 Mobile con Intune en lugar de instalarla desde la Microsoft Store. Debe descargar la aplicación del Portal de empresa y firmarla con el certificado.  Esto solo es necesario si los usuarios no usan la Tienda de empresa y desea implementar el Portal de empresa en dispositivos Windows Phone 8.1.


1.  **Descargar Portal de empresa**

    Para implementar la aplicación del Portal de empresa mediante Intune, puede descargar la [aplicación del Portal de empresa de Microsoft Intune para Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) del Centro de descarga y ejecutar el archivo ejecutable autoextraíble (.exe). Este archivo contiene dos archivos:

    -   CompanyPortal.appx: aplicación de instalación de Portal de empresa para Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1: script de PowerShell que se puede usar para firmar el archivo de aplicación de Portal de empresa para que se pueda implementar en dispositivos Windows Phone 8.1

    Como alternativa, puede descargar el Portal de empresa de Windows Phone 8.1 (paquete con licencia sin conexión) o el Portal de empresa de Windows 10 (paquete con licencia sin conexión) desde la [Tienda Microsoft para Empresas](http://businessstore.microsoft.com/). La aplicación del Portal de empresa se deberá adquirir con una licencia sin conexión y se deberá descargar el paquete apropiado para el uso sin conexión. Los listados de las plataformas de Windows 8 y Windows Phone 8 de la selección hacen referencia a sus homólogos de 8.1. Para obtener detalles sobre cómo hacerlo con Intune, vea [Administrar las aplicaciones adquiridas a través de la Tienda Microsoft para Empresas con Microsoft Intune](/intune-classic/deploy-use/manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune).

2.  **Descargar el SDK de Windows Phone** Descargue el SDK de Windows Phone 8.0 (http://go.microsoft.com/fwlink/?LinkId=615570) e instálelo en el equipo. Este SDK es necesario para generar un token de inscripción de aplicaciones.

3.  **Generar un archivo AETX** Genere un archivo de token de inscripción de aplicaciones (.aetx) a partir del archivo PFX de Symantec con AETGenerator.exe, parte del SDK de Windows Phone 8.0. Para obtener instrucciones sobre cómo crear un archivo AETX, consulte [Cómo generar un token de inscripción de aplicaciones para Windows Phone](https://msdn.microsoft.com/library/windows/apps/jj735576.aspx).

4.  **Descargar Windows SDK para Windows 8.1** Descargue e instale el [SDK de Windows Phone](http://go.microsoft.com/fwlink/?LinkId=613525) (http://go.microsoft.com/fwlink/?LinkId=613525). Tenga en cuenta que el script de PowerShell incluido con la aplicación Portal de empresa usa la ubicación de instalación predeterminada, `${env:ProgramFiles(x86)}\Windows Kits\8.1`. Si lo instala en otra ubicación, deberá incluir dicha ubicación en un parámetro de cmdlet.

5.  **Firmar el código de la aplicación mediante PowerShell** Como administrador, abra **Windows PowerShell** en el equipo host donde están instalados Windows SDK y el certificado de firma de código móvil empresarial de Symantec, vaya al archivo Sign-WinPhoneCompanyPortal.ps1 y ejecute el script.

    **Ejemplo 1**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -AetxPath 'C:\signing\cert.aetx'
    ```
    Este ejemplo firma el archivo CompanyPortal.appx en C:\temp\ y genera el archivo CompanyPortalEnterpriseSigned.appx. Usaría la contraseña de PFX 1234 y leería el identificador del editor del archivo PFX. También leería el identificador de la empresa del archivo cert.aetx.

    **Ejemplo 2**

    ```
    .\Sign-WinPhoneCompanyPortal.ps1 -InputAppx 'C:\temp\CompanyPortal.appx' -OutputAppx 'C:\temp\CompanyPortalEnterpriseSigned.appx' -PfxFilePath 'C:\signing\cert.pfx' -PfxPassword '1234' -PublisherId 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1' -EnterpriseId 1000000001
    ```
    Este ejemplo firma el archivo CompanyPortal.appx en C:\temp\ y genera el archivo CompanyPortalEnterpriseSigned.appx. Usaría la contraseña de PFX 1234 y el identificador del editor especificado.

    **Parámetros:**

    -   `-InputAppx` : ruta de acceso local al archivo CompanyPortal.appx entre comillas simples. Por ejemplo, 'C:\temp\CompanyPortal.appx'

    -   `-OutputAppx` : ruta de acceso local y nombre de archivo de la aplicación Portal de empresa firmada entre comillas simples. Por ejemplo, 'C:\temp\CompanyPortalEnterpriseSigned.appx'

    -   `-PfxFilePath` : ruta de acceso local y nombre de archivo del archivo PFX exportado del certificado de Symantec. Por ejemplo, 'C:\signing\cert.pfx'

    -   `-PfxPassword` : contraseña usada para firmar el archivo PFX entre comillas simples. Por ejemplo, '1234'

    -   `-AetxPath` : ruta de acceso local al archivo .aetx que se usa para leer el identificador de empresa si el argumento 'EnterpriseId' no está definido. Debe proporcionar este argumento o el identificador de la empresa. Por ejemplo, 'C:\signing\cert.aetx'

    -   `-PublisherId`: identificador del publicador de la empresa. Si está ausente, se usa el campo 'Asunto' del certificado de firma de código móvil empresarial de Symantec. Por ejemplo, 'OID.0.9.2342.19200300.100.1.1=1000000001, CN="Test, Inc.", OU=Test 1'

    -   `-SdkPath`: ruta de acceso a la carpeta raíz del SDK de Windows para Windows 8.1. Este argumento es opcional y está establecido de forma predeterminada en ${env:ProgramFiles(x86)}\Windows Kits\8.1.

    -   `-EnterpriseId`: identificador de la empresa. Debe proporcionar este argumento o 'AetxPath'. Si no se proporciona este argumento, el identificador de la empresa se lee del archivo AETX. Por ejemplo, 1000000001

6.  Implemente la aplicación Portal de empresa de Windows Phone 8.1 (SSP.appx). Para obtener instrucciones, vea [Adición de aplicaciones de línea de negocio (LOB) de Windows Phone a Microsoft Intune](lob-apps-windows-phone.md) ([portal clásico](/intune-classic/deploy-use/deploy-apps-in-microsoft-intune)).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Cómo renovar el certificado de firma de código de empresa de Symantec

El certificado de Symantec que se usa para implementar aplicaciones móviles de Windows y Windows Phone se debe renovar periódicamente.

1.  Busque un correo electrónico de renovación enviado desde Symantec aproximadamente 14 días antes de la expiración del certificado. Este mensaje de correo contiene instrucciones de Symantec sobre cómo renovar el certificado de empresa.

    Para obtener información adicional sobre certificados de Symantec, visite [www.symantec.com](http://www.symantec.com) o llame al 1-877-438-8776 o al 1-650-426-3400.

2.  Vaya al sitio web (ejemplo: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e inicie sesión con el identificador de editor de Symantec y el correo electrónico asociado al certificado que recibió. Recuerde que para iniciar la renovación debe usar el mismo equipo que va a utilizar para descargar el certificado.

3.  Una vez aprobada y pagada por la renovación, descargue el certificado.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Instalación del certificado actualizado para aplicaciones de línea de negocio (LOB)

1.  Firme la última versión de su aplicación de línea de negocio.

2.  Abra la consola de Intune y vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone** y haga clic en **Cargar aplicación firmada**.

3.  Cargue el Portal de empresa recién firmado. Necesitará el archivo SSP.xap recién firmado y el nuevo archivo .PFX que recibió de Symantec o el token de inscripción de la aplicación que se creó con este nuevo archivo .PFX.

4.  Una vez finalizada la carga, quite la versión antigua de Portal de empresa del área de trabajo **Software**  .

5.  Firme todas las aplicaciones de línea de negocio nuevas y actualizadas con el nuevo certificado. No es necesario retirar ni volver a implementar las aplicaciones existentes.

## <a name="manually-deploy-windows-10-company-portal-app"></a>Implementación manual de la aplicación del Portal de empresa para Windows 10
Puede implementar manualmente la aplicación del Portal de empresa para Windows 10 directamente desde Intune, aunque no haya integrado Intune con la Tienda Microsoft para Empresas.

 > [!NOTE]
 > Esta opción requiere implementar actualizaciones manuales cada vez que se publica una actualización de la aplicación.

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
  ![La dependencia de aplicación de Windows para este instalador de software no se encontró en la carpeta de la aplicación. Puede continuar con la creación e implementación de esta aplicación, pero no se ejecutará hasta que se proporcione la dependencia de aplicación de Windows correspondiente.](./media/Win10CP-error-message.png)
6. Vuelva a Intune y cargue la aplicación del Portal de empresa como una nueva aplicación. Impleméntela como una aplicación necesaria para el conjunto de usuarios de destino deseado.  

Consulte [Deploying an appxbundle with dependencies via Microsoft Intune MDM](https://blogs.technet.microsoft.com/configmgrdogs/2016/11/30/deploying-an-appxbundle-with-dependencies-via-microsoft-intune-mdm/) (Implementación de appxbundle con dependencias a través de la MDM de Microsoft Intune) para obtener más información sobre cómo Intune controla las dependencias de aplicaciones universales.  

### <a name="how-do-i-update-the-company-portal-on-my-users-devices-if-they-have-already-installed-the-older-apps-from-the-store"></a>¿Cómo puedo actualizar el Portal de empresa en los dispositivos de mis usuarios si ya han instalado las aplicaciones anteriores desde la Tienda?
Si los usuarios ya han instalado las aplicaciones del Portal de empresa para Windows 8.1 o Windows Phone 8.1 desde la Tienda, recibirán automáticamente la nueva versión sin que tengan que hacer nada. Si la actualización no se realiza, pida a los usuarios que comprueben que están habilitadas en sus dispositivos las actualizaciones automáticas para las aplicaciones de la Tienda.   

### <a name="how-do-i-upgrade-my-sideloaded-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente del Portal de empresa para Windows 8.1 a la versión para Windows 10?
La ruta de migración recomendada es eliminar la implementación de la aplicación del Portal de empresa para Windows 8.1 estableciendo la acción de implementación en "Desinstalar". Una vez hecho, se puede implementar la aplicación del Portal de empresa para Windows 10 con cualquiera de las opciones anteriores.  

Si necesita transferir localmente la aplicación e implementó el Portal de empresa para Windows 8.1 sin firmar con el certificado de Symantec, siga los pasos de la sección anterior Deploy directly via Intune (Implementación directa a través de Intune) para completar la actualización.

Si necesita transferir localmente la aplicación y firmó e implementó el Portal de empresa para Windows 8.1 con el certificado de firma de código de Symantec, siga los pasos descritos en la sección siguiente.  

### <a name="how-do-i-upgrade-my-signed-and-sideloaded-windows-phone-81-company-portal-app-or-windows-81-company-portal-app-to-the-windows-10-company-portal-app"></a>¿Cómo puedo actualizar mi aplicación transferida localmente y firmada del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 a la versión para Windows 10?
La ruta de migración recomendada es eliminar la implementación de la aplicación del Portal de empresa para Windows Phone 8.1 o del Portal de empresa para Windows 8.1 estableciendo la acción de implementación en "Desinstalar". Una vez hecho, se puede implementar con normalidad la aplicación del Portal de empresa para Windows 10.  

Si no, habrá que actualizar y firmar correctamente la aplicación del Portal de empresa para Windows 10 para garantiza que se respeta la ruta de actualización.  

Si la aplicación del Portal de empresa para Windows 10 está firmada e implementada de esta manera, debe repetir este proceso para cada nueva actualización de la aplicación cuando esté disponible en la Tienda. La aplicación no se actualizará automáticamente cuando se actualice la Tienda.  

Así es cómo tiene que firmar e implementar la aplicación:

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
El script generará la versión firmada de la aplicación del Portal de empresa para Windows 10 cuando haya terminado de ejecutarse. Después, puede implementar la versión firmada de la aplicación como una aplicación LOB mediante Intune, que actualizará las versiones implementadas actualmente a esta nueva aplicación.  
