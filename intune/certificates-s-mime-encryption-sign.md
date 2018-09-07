---
title: 'Firma y cifrado de correo electrónico S/MIME: Azure | Microsoft Docs'
description: Use o habilite S/MIME para firmar y cifrar mensajes de correo electrónico en Microsoft Intune
keywords: ''
author: MandiOhlinger
ms.author: mandia
manager: dougeby
ms.date: 08/21/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 3a31a43cfe45060891c30a7f159123a30b43173d
ms.sourcegitcommit: 488be75cbee88455b33c68a3ec2acb864d461bf8
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/22/2018
ms.locfileid: "41910673"
---
# <a name="smime-email-signing-and-encryption-in-intune"></a>Firma y cifrado de correo electrónico S/MIME en Intune

> [!IMPORTANT]
> Hemos aplicado algunas mejoras a la característica S/MIME descrita en este artículo. Como resultado, la característica S/MIME se ha quitado temporalmente en Intune. Cuando esta característica se publique, quitaremos esta nota.

S/MIME proporciona un nivel adicional de seguridad para las comunicaciones de correo electrónico mediante el cifrado y el descifrado. Microsoft Intune puede usar S/MIME para firmar y cifrar mensajes de correo electrónico para dispositivos móviles que ejecutan iOS, Windows, Windows Phone, Android y macOS.

En los dispositivos iOS, puede crear un perfil de correo electrónico administrado por Intune que use S/MIME y certificados para firmar y cifrar los mensajes de correo electrónico entrantes y salientes. Para otras plataformas, es posible que S/MIME sea o no compatible. Si es compatible, puede instalar los certificados que usan el cifrado y la firma S/MIME. Después, los usuarios finales pueden habilitar S/MIME en su aplicación de correo electrónico.

Para obtener más información sobre la firma y el cifrado de correo electrónico S/MIME, vea [S/MIME para la firma y el cifrado de mensajes](https://docs.microsoft.com/Exchange/policy-and-compliance/smime).

## <a name="signing-certificates"></a>Certificados de firma

Los certificados que se usan para la firma permiten que la aplicación de correo electrónico cliente se comunique de forma segura con el servidor de correo electrónico.

Para usar certificados de firma, cree una plantilla en la entidad de certificación que se centre en la firma. En la entidad de certificación de Microsoft Active Directory, en [Configurar la plantilla de certificado de servidor](https://docs.microsoft.com/windows-server/networking/core-network-guide/cncg/server-certs/configure-the-server-certificate-template) se enumeran los pasos para crear plantillas de certificado.

Los certificados de firma en Intune usan certificados PKCS. En [Configuración y uso de certificados PKCS con Intune](certficates-pfx-configure.md) se describe cómo implementar y usar el certificado PKCS en el entorno de Intune. Estos pasos incluyen:

- Descargar e instalar Microsoft Intune Certificate Connector para admitir las solicitudes de certificado PKCS.
- Crear un perfil de certificado raíz de confianza para los dispositivos. Este paso incluye el uso de certificados raíz de confianza e intermedios para la entidad de certificación y, después, la implementación del perfil en los dispositivos.
- Crear un perfil de certificado PKCS mediante la plantilla de certificado que se creó. Este perfil emite certificados de firma para los dispositivos e implementa el perfil de certificado PKCS en los dispositivos.

También se puede importar un certificado de firma para un usuario específico. El certificado de firma se implementa en todos los dispositivos que inscribe un usuario. Para importar certificados en Intune, use los [cmdlets de PowerShell de GitHub](https://github.com/Microsoft/Intune-Resource-Access). Para implementar un certificado PKCS importado en Intune que se va a usar para la firma de correo electrónico, siga los pasos descritos en [Configuración y uso de certificados PKCS con Intune](certficates-pfx-configure.md). Estos pasos incluyen:

- Descargar e instalar el Conector de certificado PFX para Microsoft Intune. Este conector proporciona certificados PKCS importados a los dispositivos.
- Importar certificados de firma de correo electrónico S/MIME a Intune.
- Crear un perfil de certificado PKCS importado. Este perfil proporciona los certificados PKCS importados a los dispositivos del usuario adecuado.

## <a name="encryption-certificates"></a>Certificados de cifrado

Los certificados que se usan para el cifrado confirman que un correo electrónico cifrado solo se puede descifrar por el destinatario previsto. El cifrado S/MIME es una capa adicional de seguridad que se puede usar en las comunicaciones por correo electrónico.

Al enviar un correo electrónico cifrado a otro usuario, se obtiene la clave pública del certificado de cifrado de ese usuario y se cifra el correo electrónico que se envía. El destinatario descifra el correo electrónico con la clave privada en su dispositivo. Los usuarios pueden tener un historial de los certificados usados para cifrar el correo electrónico. Cada uno de esos certificados se debe implementar en todos los dispositivos de un usuario específico para que su correo electrónico se descifre de forma correcta.

Se recomienda que los certificados de cifrado de correo electrónico no se creen en Intune. Aunque Intune es compatible con la emisión de certificados PKCS que admiten el cifrado, Intune crea un certificado único por dispositivo. Un certificado único por dispositivo no es ideal para un escenario de cifrado S/MIME, donde el certificado de cifrado se debe compartir entre todos los dispositivos del usuario.

Para implementar certificados S/MIME con Intune, debe importar a Intune todos los certificados de cifrado de un usuario. Después, Intune implementa todos esos certificados en cada dispositivo que el usuario inscriba. Para importar certificados en Intune, use los [cmdlets de PowerShell de GitHub](https://github.com/Microsoft/Intune-Resource-Access).

Para implementar un certificado PKCS importado en Intune que se usa para el cifrado de correo electrónico, siga los pasos descritos en [Configuración y uso de certificados PKCS con Intune](certficates-pfx-configure.md). Estos pasos incluyen:

- Descargar e instalar el Conector de certificado PFX para Microsoft Intune. Este conector proporciona certificados PKCS importados a los dispositivos.
- Importar los certificados de cifrado de correo electrónico S/MIME a Intune.
- Crear un perfil de certificado PKCS importado. Este perfil proporciona los certificados PKCS importados a los dispositivos del usuario adecuado.

 > [!NOTE]
 > Intune elimina los certificados S/MIME importados cuando se quitan los datos de la empresa, o bien cuando se anula la inscripción de los usuarios de la administración. Pero los certificados no se revocan en la entidad de certificación.

## <a name="smime-email-profiles"></a>Perfiles de correo electrónico S/MIME

Después de crear los perfiles de certificado de firma y cifrado S/MIME, puede [habilitar S/MIME para el correo electrónico nativo de iOS](email-settings-ios.md).