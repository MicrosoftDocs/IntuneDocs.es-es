---
title: Creación de un perfil de certificado en Microsoft Intune - Azure | Microsoft Docs
description: Para sus dispositivos, agregue o cree un perfil de certificado configurando un entorno de certificados PKCS o SCEP, exporte el certificado público, cree el perfil en Azure Portal y asigne el SCEP o PKCS a los perfiles de certificado de Microsoft Intune en Azure Portal
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 09/03/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 5eccfa11-52ab-49eb-afef-a185b4dccde1
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 74b920deeb5255f6f938f0c8b07eaab6d765e68e
ms.sourcegitcommit: 88b6e6d70f5fa15708e640f6e20b97a442ef07c5
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/02/2019
ms.locfileid: "71722974"
---
# <a name="use-certificates-for-authentication-in-microsoft-intune"></a>Uso de certificados para la autenticación en Microsoft Intune  

Use certificados con Intune para autenticar a los usuarios en las aplicaciones y los recursos corporativos a través de VPN, Wi-Fi o perfiles de correo electrónico. Cuando se usan certificados para autenticar estas conexiones, los usuarios finales no tendrán que escribir nombres de usuario ni contraseñas, lo que facilita su acceso. Los certificados también se usan para firmar y cifrar el correo electrónico mediante S/MIME.

Intune admite los tipos de certificado siguientes:  

- Protocolo de inscripción de certificados simple (SCEP)  
- PKCS#12 (o PFX)  
- Certificados PKCS importados

Para implementar estos certificados, debe crear y asignar perfiles de certificado a los dispositivos.  

Cada perfil de certificado individual que cree es compatible con una sola plataforma. Por ejemplo, si usa certificados PKCS, creará un perfil de certificado PKCS para Android y un perfil de certificado PKCS independiente para iOS. Si también usa certificados SCEP para esas dos plataformas, tendrá que crear un perfil de certificado SCEP para Android y otro para iOS.  

**Consideraciones generales**:  
- Si no tiene una entidad de certificación (CA) empresarial, debe crearla o usar una de [uno de los asociados admitidos](certificate-authority-add-scep-overview.md#third-party-certification-authority-partners).
- Si usa perfiles de certificado SCEP con Servicios de certificados de Active Directory de Microsoft, configurará un servidor de Servicio de inscripción de dispositivos de red (NDES).
- Si usa SCEP con uno de nuestros asociados de entidad de certificación, tendrá que [integrarlo con Intune](certificate-authority-add-scep-overview.md#set-up-third-party-ca-integration).
- Los perfiles de certificado SCEP y PKCS requieren que descargue, instale y configure Microsoft Intune Certificate Connector. 
- Los certificados PCKS importados requieren que descargue, instale y configure el Conector de certificado PFX para Microsoft Intune.
- Los certificados PKCS importados requieren que exporte los certificados desde la entidad de certificación y los importe en Microsoft Intune. Vea [el proyecto PFXImport de PowerShell](https://github.com/Microsoft/Intune-Resource-Access/tree/develop/src/PFXImportPowershell)
- Para que un dispositivo use perfiles de certificado SCEP, PCKS o PKCS importados, ese dispositivo debe confiar en la entidad de certificación raíz. Un *perfil de certificado de confianza* se usa para implementar el certificado de entidad de certificación raíz de confianza en los dispositivos.  

## <a name="supported-platforms-and-certificate-profiles"></a>Plataformas compatibles y perfiles de certificado  
| Plataforma              | Perfil de certificado de confianza | Perfil de certificado PKCS | Perfil de certificado SCEP | Perfil de certificado PKCS importado  |
|--|--|--|--|---|
| Administrador de dispositivos Android | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png)|  ![Compatible.](./media/certificates-configure/green-check.png) |
| Android Enterprise <br> - Propietario del dispositivo   | ![Compatible.](./media/certificates-configure/green-check.png) |   |  |   |
| Android Enterprise <br> - Perfil de trabajo    | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) |
| iOS                   | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) |
| macOS                 | ![Compatible.](./media/certificates-configure/green-check.png) |   |![Compatible.](./media/certificates-configure/green-check.png)|![Compatible.](./media/certificates-configure/green-check.png)|
| Windows Phone 8,1     |![Compatible.](./media/certificates-configure/green-check.png)  |  | ![Compatible.](./media/certificates-configure/green-check.png)| ![Compatible.](./media/certificates-configure/green-check.png) |
| Windows 8.1 y posterior |![Compatible.](./media/certificates-configure/green-check.png)  |  |![Compatible.](./media/certificates-configure/green-check.png) |   |
| Windows 10 y versiones posteriores  | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) | ![Compatible.](./media/certificates-configure/green-check.png) |

## <a name="export-the-trusted-root-ca-certificate"></a>Exportación del certificado de entidad de certificación raíz de confianza  
Para usar certificados PKCS, SCEP y PKCS importados, los dispositivos deben confiar en la entidad de certificación raíz. Para establecer esta confianza, exporte el certificado de entidad de certificación (CA) raíz de confianza, así como cualquier certificado de entidad de certificación intermedia o emisora, como un certificado público (.cer). Puede obtener estos certificados de la entidad de certificación emisora o desde cualquier dispositivo que confíe en ella.  

Para exportar el certificado, consulte la documentación de la entidad de certificación. Tendrá que exportar el certificado público como un archivo .cer.  No exporte la clave privada, un archivo .pfx.  

Usará este archivo .cer al [crear perfiles de certificado de confianza](#create-trusted-certificate-profiles) para implementar ese certificado en los dispositivos.  

## <a name="create-trusted-certificate-profiles"></a>creación de perfiles de certificado de confianza  
Cree un perfil de certificado de confianza antes de poder crear un perfil de certificado SCEP, PKCS o PKCS importado. La implementación de un perfil de certificado de confianza garantiza que cada dispositivo reconozca la legitimidad de la entidad de certificación. Los perfiles de certificado SCEP hacen referencia directamente a un perfil de certificado de confianza. Los perfiles de certificado PKCS no hacen referencia directamente al perfil de certificado de confianza, pero sí al servidor en el que se hospeda la entidad de certificación. Los perfiles de certificado PKCS importados no hacen referencia directamente al perfil de certificado de confianza, pero pueden usarlo en el dispositivo. La implementación de un perfil de certificado de confianza en los dispositivos garantiza que se establece esta confianza. Cuando un dispositivo no confía en la entidad de certificación raíz, se producirá un error en la directiva de perfil de certificado SCEP o PKCS.  

Cree un perfil de certificado de confianza independiente para cada plataforma de dispositivo que quiera admitir, como lo haría con los perfiles de certificado SCEP, PCKS y PKCS importados.  


### <a name="to-create-a-trusted-certificate-profile"></a>Para crear un perfil de certificado de confianza  

1. Inicie sesión en el [portal de Intune](https://aka.ms/intuneportal).  
2. Seleccione **Configuración del dispositivo** > **Administrar** > **Perfiles** > **Crear perfil**.  
3. Escriba un **Nombre y descripción** para el perfil de certificado de confianza.  
4. En la lista desplegable **Plataforma**, seleccione la plataforma de dispositivo para este certificado de confianza.  
5. En la lista desplegable **Tipos de perfil**, elija **Certificado de confianza**.  
6. Busque el archivo .cer de certificado de entidad de certificación raíz de confianza que ha exportado para usarlo con este perfil de certificado y, después, seleccione **Aceptar**.  
7. Solo para dispositivos Windows 8.1 y Windows 10, seleccione el **almacén de destino** del certificado de confianza. Las opciones son:  
   - **Almacén de certificados de equipo - Raíz**
   - **Almacén de certificados de equipo - Intermedio**
   - **Almacén de certificados de usuario - Intermedio**
8. Cuando haya terminado, elija **Aceptar**, vuelva al panel **Crear perfil** y seleccione **Crear**.
El perfil aparece en la lista de perfiles del panel de vista *Configuración del dispositivo - Perfiles*, con un tipo de perfil de **Certificado de confianza**.  Asegúrese de asignar este perfil a los dispositivos que vayan a usar certificados SCEP o PCKS. Para asignar el perfil a grupos, vea [Asignación de perfiles de dispositivo](../configuration/device-profile-assign.md).

> [!NOTE]  
> Es posible que los dispositivos Android muestren un mensaje que indica que un tercero ha instalado un certificado de confianza.  

## <a name="additional-resources"></a>Recursos adicionales  
- [Asignar perfiles de dispositivo](../configuration/device-profile-assign.md)  
- [Usar S/MIME para firmar y cifrar mensajes de correo electrónico](certificates-s-mime-encryption-sign.md)  
- [Uso de entidades de certificación de terceros](certificate-authority-add-scep-overview.md)  

## <a name="next-steps"></a>Pasos siguientes  
Después de crear y asignar perfiles de certificado de confianza, cree perfiles de certificado SCEP, PKCS o PKCS importados para cada plataforma que quiera usar. Para continuar, vea los artículos siguientes:  
- [Configuración de la infraestructura para admitir certificados SCEP con Intune](certificates-scep-configure.md)  
- [Configuración y administración de certificados PKCS con Intune](certficates-pfx-configure.md)  
- [Creación de un perfil de certificado PKCS importado](certificates-imported-pfx-configure.md#create-a-pkcs-imported-certificate-profile)  

