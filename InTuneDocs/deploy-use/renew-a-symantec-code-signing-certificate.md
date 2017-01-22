---
title: "Renovar un certificado de firma de código empresarial de Symantec para usarlo con Intune | Microsoft Docs"
description: "Guía para renovar certificados de Symantec que se usan para administrar determinados dispositivos móviles Windows y Windows Phone"
keywords: 
author: staciebarker
ms.author: stabar
manager: angerobe
ms.date: 07/25/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: c4813044-a925-4273-b0ec-e992fd55850a
ms.reviewer: damionw
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 928e4e8097b9cd326e0863a45b183226a7eae056
ms.openlocfilehash: acd1ab3a988adc4fee2a57ff4be82bac8e92a435


---

# <a name="renew-a-symantec-enterprise-code-signing-certificate-for-windows-devices"></a>Renovar un certificado de firma de código empresarial de Symantec para dispositivos Windows

[!INCLUDE[classic-portal](../includes/classic-portal.md)]

El certificado de Symantec que se usa para implementar aplicaciones móviles de Windows y Windows Phone se debe renovar periódicamente.

## <a name="how-to-renew-the-symantec-enterprise-code-signing-certificate"></a>Cómo renovar el certificado de firma de código de empresa de Symantec

1.  Busque un correo electrónico de renovación enviado desde Symantec aproximadamente 14 días antes de la expiración del certificado. Este mensaje de correo contiene instrucciones de Symantec sobre cómo renovar el certificado de empresa.

    Para obtener información adicional sobre certificados de Symantec, visite [www.symantec.com](http://www.symantec.com) o llame al 1-877-438-8776 o al 1-650-426-3400.

2.  Vaya al sitio web (ejemplo: [https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do](https://products.websecurity.symantec.com/orders/enrollment/microsoftCert.do)) e inicie sesión con el identificador de editor de Symantec y el correo electrónico asociado al certificado que recibió. Recuerde que para iniciar la renovación debe usar el mismo equipo que va a utilizar para descargar el certificado.

3.  Una vez aprobada y pagada por la renovación, descargue el certificado.

## <a name="how-to-install-the-updated-certificate-for-windows-phone-80"></a>Cómo instalar el certificado actualizado para Windows Phone 8.0

1.  Descargue y firme la aplicación Portal de empresa de Windows Phone más reciente que encontrará aquí: [http://www.microsoft.com/es-es/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Abra la consola de administración de Intune ([https://admin.manage.microsoft.com](https://admin.manage.microsoft.com)), vaya a **Administración**, **Administración de dispositivos móviles** &gt; **Windows Phone** y haga clic en **Cargar aplicación firmada**.

3.  Cargue el Portal de empresa recién firmado. Necesitará el archivo SSP.xap recién firmado y el nuevo archivo .PFX que recibió de Symantec o el token de inscripción de la aplicación que se creó con este nuevo archivo .PFX.

4.  Una vez finalizada la carga, quite la versión antigua de Portal de empresa en el área de trabajo **Software** de la consola de administración de Intune.

5.  Firme de nuevo todas las aplicaciones de línea de negocio de empresa con el mismo certificado y cargue y reemplace las aplicaciones existentes.

Proporcionar un archivo firmado SSP.xap es actualmente la única manera de facilitar el certificado de firma de código actualizado. Para admitir aplicaciones de línea de negocio firmadas, deberá firmar y cargar una aplicación Portal de empresa, aunque los usuarios instalen la aplicación Portal de empresa desde la Tienda.

## <a name="how-to-install-the-updated-certificate-for-windows-phone-81-and-later-devices"></a>Cómo instalar el certificado actualizado para Windows Phone 8.1 y dispositivos posteriores

1.  Descargue y firme la aplicación Portal de empresa de Windows Phone más reciente del centro de descarga que encontrará aquí: [http://www.microsoft.com/es-es/download/details.aspx?id=36060](http://www.microsoft.com/en-us/download/details.aspx?id=36060).

2.  Abra la [consola de administración de Intune](https://admin.manage.microsoft.com) (https://admin.manage.microsoft.com), vaya a **Administración** &gt; **Administración de dispositivos móviles** &gt; **Windows Phone** y haga clic en **Cargar aplicación firmada**.

3.  Cargue el Portal de empresa recién firmado. Necesitará el archivo SSP.xap recién firmado y el nuevo archivo .PFX que recibió de Symantec o el token de inscripción de la aplicación que se creó con este nuevo archivo .PFX.

4.  Una vez finalizada la carga, quite la versión antigua de Portal de empresa del área de trabajo **Software**  .

5.  Firme todas las aplicaciones de línea de negocio nuevas y actualizadas con el nuevo certificado. No es necesario retirar ni volver a implementar las aplicaciones existentes.


### <a name="see-also"></a>Consulte también
[Configurar la administración de Windows Phone 8.0](set-up-windows-phone-8.0-management-with-microsoft-intune.md)
[Configurar la administración de Windows Phone](set-up-windows-phone-management-with-microsoft-intune.md)



<!--HONumber=Dec16_HO2-->


