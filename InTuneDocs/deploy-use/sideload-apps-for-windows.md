---
title: Transferir localmente aplicaciones para Windows y Windows Phone | Microsoft Intune
description: "Aprenda a firmar aplicaciones de línea de negocios de modo que pueda usar Intune para implementarlas."
keywords: 
author: robstackmsft
manager: angrobe
ms.date: 12/07/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: e44f1756-52e1-4ed5-bf7d-0e80363a8674
translationtype: Human Translation
ms.sourcegitcommit: eeb85a28ea6f99a0123ec5df3b0d476a678b85cb
ms.openlocfilehash: 938e3a1914f379d115bf24ebd7d990f6e1d319a9


---
# <a name="sign-line-of-business-apps-so-they-can-be-deployed-to-windows-devices-with-intune"></a>Firma de aplicaciones de línea de negocio para que se puedan implementar en dispositivos Windows con Intune

Como administrador de Intune, puede implementar aplicaciones de línea de negocio (LOB) en dispositivos Windows y Windows 10 Mobile, incluida la aplicación del Portal de empresa. Para implementar aplicaciones .appx o .xap en dispositivos móviles Windows 10 y Windows 10, o para implementar cualquier aplicación LOB en dispositivos Windows 8.1 o Windows Phone 8.1, debe obtener un **certificado de firma de código móvil empresarial de Symantec **. El certificado de Symantec es de confianza para estas aplicaciones en los dispositivos Windows correspondientes. Puede usar su propia entidad de certificación para aplicaciones de Windows 10 y aplicaciones "universales". Este certificado se requiere para:

-   Firmar la aplicación del Portal de empresa para la implementación en equipos Windows, dispositivos Windows 10 Mobile y dispositivos Windows Phone

-   Firmar aplicaciones de línea de negocio de empresa para que Intune pueda implementarlas en dispositivos Windows

Los pasos que figuran a continuación le ayudarán a obtener los certificados necesarios y a firmar las aplicaciones. Necesitará una cuenta del Centro de desarrollo de Windows Phone y, a continuación, deberá adquirir un certificado de Symantec.


1. **Unirse al Centro de desarrollo de Windows Phone**<br>
   Únase al [Centro de desarrollo de Windows Phone](http://go.microsoft.com/fwlink/?LinkId=268442) usando información de cuenta corporativa al iniciar sesión para comprar su cuenta de la compañía. Esta solicitud deberá estar autorizada por un oficial de la empresa antes de recibir un certificado de firma de código.

2. **Obtener un certificado de empresa de Symantec**<br>
  Adquiera un certificado desde el [sitio web de Symantec](http://go.microsoft.com/fwlink/?LinkId=268441) mediante su identificador de Symantec. Después de adquirir el certificado, el aprobador corporativo que designase en su cuenta del Centro de desarrollo de Windows Phone recibirá un mensaje correo electrónico en el que se pide la aprobación de la solicitud de certificado. Para más información sobre el requisito de certificado de Symantec, vea [Why Windows Phone requires a Symantec certificate?](https://technet.microsoft.com/en-us/library/dn764959.aspx#BKMK_Symantec) (¿Por qué Windows Phone pide un certificado de Symantec?). Preguntas más frecuentes sobre la inscripción de dispositivos Windows.

3.  **Importar certificados**<br>
    Una vez que se apruebe la solicitud, recibirá un correo electrónico con instrucciones para la importación de certificados. Siga las instrucciones indicadas en el correo electrónico para importar los certificados.

4.  **Comprobar los certificados importados**<br>
    Para comprobar que los certificados se han importado correctamente, vaya al complemento **Certificados**, haga clic con el botón derecho en **Certificados** y seleccione **Buscar certificados**. En el campo **Contiene** , escriba "Symantec" y haga clic en **Buscar ahora**. Los certificados que haya importado deberían aparecer en los resultados.

    ![Buscar el certificado de Symantec](./media/wit.gif)

5. **Exportar un certificado de firma**<br>
    Después de comprobar que los certificados están presentes, puede exportar el archivo .pfx para firmar el Portal de empresa. Seleccione el certificado de Symantec con la "firma de código" **Propósito planteado**. Haga clic con el botón derecho en el certificado de firma de código y seleccione **Exportar**.

    ![Exportar el certificado de firma](./media/wit-walk-cert2.gif)

    En el **Asistente para exportar certificado**, seleccione **Sí, exportar la clave privada** y, a continuación, haga clic en **Siguiente**. Seleccione **Intercambio de información personal: PKCS #12 (.PFX) ** y active **Si es posible, incluir todos los certificados en la ruta de acceso de certificación**. Complete el asistente. Para obtener más información, consulte [Exportar un certificado con la clave privada](http://go.microsoft.com/fwlink/?LinkID=203031).

6.  **Cargar la aplicación en Intune**<br>
    Cargue el archivo de la aplicación firmada y el certificado de firma de código para que la aplicación esté disponible para los usuarios finales.

    1.  En la [consola de administración de Intune](http://manage.microsoft.com), haga clic en **Administración** &gt; **Windows Phone**.

    2.  Haga clic en **Cargar archivo de aplicación firmado** e inicie sesión con su identificador de administrador de Intune.

    3.  Agregue el archivo de certificado (.pfx) que ha exportado a **Certificado de firma de código** y cree una contraseña para el certificado.

    4.  Complete el asistente.

## <a name="example-download-sign-and-deploy-the-company-portal-app-for-windows-devices"></a>Ejemplo: Descarga, firma e implementación de la aplicación del Portal de empresa para dispositivos Windows

Puede implementar la aplicación del Portal de empresa en dispositivos Windows Phone y Windows 10 Mobile, con Intune en lugar de instalarla desde la Tienda Windows. Debe descargar la aplicación del Portal de empresa y firmarla con el certificado.  Esto solo es necesario si los usuarios no usan la Tienda de empresa y desea implementar el Portal de empresa en dispositivos Windows Phone 8.1.


1.  **Descargar Portal de empresa**

    Para implementar la aplicación del Portal de empresa mediante Intune, puede descargar la [aplicación del Portal de empresa de Microsoft Intune para Windows Phone 8.1](http://go.microsoft.com/fwlink/?LinkId=615799) del Centro de descarga y ejecutar el archivo ejecutable autoextraíble (.exe). Este archivo contiene dos archivos:

    -   CompanyPortal.appx: aplicación de instalación de Portal de empresa para Windows Phone 8.1

    -   WinPhoneCompanyPortal.ps1: script de PowerShell que se puede usar para firmar el archivo de aplicación de Portal de empresa para que se pueda implementar en dispositivos Windows Phone 8.1

    Como alternativa, puede descargar el Portal de empresa de Windows Phone 8.1 (paquete con licencia sin conexión) o el Portal de empresa de Windows 10 (paquete con licencia sin conexión) de la [Tienda Windows para empresas](http://businessstore.microsoft.com/). La aplicación del Portal de empresa se deberá adquirir con una licencia sin conexión y se deberá descargar el paquete apropiado para el uso sin conexión. Los listados de las plataformas de Windows 8 y Windows Phone 8 de la selección hacen referencia a sus homólogos de 8.1. Para obtener detalles sobre cómo hacer esto con Intune, vea [Administrar las aplicaciones adquiridas a través de la Tienda Windows para empresas con Microsoft Intune](manage-apps-you-purchased-from-the-windows-store-for-business-with-microsoft-intune.md).

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

6.  Implemente la aplicación Portal de empresa de Windows Phone 8.1 (SSP.appx). Para más información, consulte [Implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md).

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Cómo renovar el certificado de firma de código de empresa de Symantec

El certificado de Symantec que se usa para implementar aplicaciones móviles de Windows y Windows Phone se debe renovar periódicamente.

1.  Busque un correo electrónico de renovación enviado desde Symantec aproximadamente 14 días antes de la expiración del certificado. Este mensaje de correo contiene instrucciones de Symantec sobre cómo renovar el certificado de empresa.

    Para obtener información adicional sobre certificados de Symantec, visite [www.symantec.com](http://www.symantec.com) o llame al 1-877-438-8776 o al 1-650-426-3400.

2.  Vaya al sitio web (ejemplo: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e inicie sesión con el identificador de editor de Symantec y el correo electrónico asociado al certificado que recibió. Recuerde que para iniciar la renovación debe usar el mismo equipo que va a utilizar para descargar el certificado.

3.  Una vez aprobada y pagada por la renovación, descargue el certificado.

### <a name="how-to-install-the-updated-certificate-for-line-of-business-lob-apps"></a>Instalación del certificado actualizado para aplicaciones de línea de negocio (LOB)

1.  Firme la última versión de su aplicación de línea de negocio.

2.  Abra la [consola de administración de Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone** y haga clic en **Cargar aplicación firmada**.

3.  Cargue el Portal de empresa recién firmado. Necesitará el archivo SSP.xap recién firmado y el nuevo archivo .PFX que recibió de Symantec o el token de inscripción de la aplicación que se creó con este nuevo archivo .PFX.

4.  Una vez finalizada la carga, quite la versión antigua de Portal de empresa del área de trabajo **Software**  .

5.  Firme todas las aplicaciones de línea de negocio nuevas y actualizadas con el nuevo certificado. No es necesario retirar ni volver a implementar las aplicaciones existentes.



<!--HONumber=Dec16_HO2-->


