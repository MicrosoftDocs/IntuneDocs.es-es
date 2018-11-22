---
title: 'Integración del control de acceso de red con Microsoft Intune: Azure | Microsoft Docs'
description: Las soluciones de control de acceso de red (NAC) comprueban la inscripción y el cumplimiento de los dispositivos con Intune. NAC incluye determinados comportamientos y funciona con acceso condicional. Vea los pasos necesarios para la integración y obtenga una lista de soluciones de socios.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/19/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 00f660d2ac228fbebe218c53482d00e59f09ce56
ms.sourcegitcommit: be6f6b750635ebc7956dd2d60a0e131d124b2fc3
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/19/2018
ms.locfileid: "51947333"
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integración del control de acceso de red (NAC) con Intune

Intune se integra con partners de control de acceso de red para ayudar a las organizaciones a proteger los datos de empresa cuando los dispositivos intentan tener acceso a los recursos locales.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>¿Cómo Intune y las soluciones de NAC ayudan a proteger los recursos de su organización?

Las soluciones de NAC comprueban el estado de inscripción y cumplimiento de los dispositivos con Intune para tomar decisiones de control de acceso. Si el dispositivo no está inscrito o está inscrito pero no es conforme con las directivas de cumplimiento de dispositivos de Intune, debe redirigirse a Intune para su inscripción o para una comprobación de cumplimiento.

### <a name="example"></a>Ejemplo

Si el dispositivo está inscrito y es compatible con Intune, la solución de NAC debe permitir el acceso del dispositivo a los recursos de la empresa. Por ejemplo, a los usuarios se les puede permitir o denegar el acceso al intentar tener acceso a los recursos de VPN o Wi-Fi de la empresa.

## <a name="feature-behaviors"></a>Comportamientos de la característica

Los dispositivos que se están sincronizando activamente a Intune no pueden pasar de **Compatible** / **No compatible** a **No sincronizado** (o **Desconocido**). El estado **Desconocido** está reservado a los dispositivos recién inscritos cuyo cumplimiento aún no se ha evaluado.

En el caso de los dispositivos cuyo acceso a los recursos está bloqueado, el servicio de bloqueo debe redirigir a todos los usuarios al [portal de administración](https://portal.manage.microsoft.com) para determinar por qué el dispositivo está bloqueado.  Si los usuarios visitan esta página, la compatibilidad de sus dispositivos se vuelve a evaluar sincrónicamente.

## <a name="nac-and-conditional-access"></a>NAC y acceso condicional

NAC funciona con el acceso condicional para proporcionar decisiones de control de acceso. Para obtener más información, vea [Formas comunes de usar el acceso condicional con Intune](conditional-access-intune-common-ways-use.md).

## <a name="how-the-nac-integration-works"></a>Cómo funciona la integración de NAC

La siguiente lista presenta información general sobre cómo funciona la integración de NAC al integrarse con Intune. Los tres primeros pasos, 1-3, explican el proceso de incorporación. Una vez que la solución de NAC está integrada con Intune, los pasos del 4 al 9 describen la operación en curso.

![Cómo funciona NAC con Intune](./media/ca-intune-common-ways-2.png)

1. Registre la solución de partner de NAC con Azure Active Directory (AAD), y conceda permisos delegados a la API de NAC de Intune.
2. Configure la solución de partner de NAC con las opciones correctas incluida la URL de detección de Intune.
3. Configure la solución de partner de NAC para la autenticación de certificados.
4. El usuario se conecta al punto de acceso de Wi-Fi de la empresa o realiza una solicitud de conexión VPN.
5. La solución de partner de NAC reenvía la información del dispositivo a Intune y pregunta a Intune sobre el estado de cumplimiento y la inscripción de dispositivos.
6. Si el dispositivo no es compatible o no está inscrito, la solución del asociado de NAC indica al usuario que inscriba o corrija el cumplimiento del dispositivo.
7. El dispositivo intenta volver a comprobar su cumplimiento y su estado de inscripción, cuando procede.
8. Una vez que el dispositivo está inscrito y es compatible, la solución de partner de NAC obtiene el estado de Intune.
9. La conexión se establece correctamente lo que permite al dispositivo tener acceso a los recursos de empresa.

## <a name="use-nac-for-vpn-on-your-ios-devices"></a>Uso de NAC para VPN en dispositivos iOS  
NAC para Cisco Legacy AnyConnect, F5 Access Legacy y Citrix VPN se admite sin tener que habilitar NAC en el perfil de VPN.

También se admite NAC para Citrix SSO. Para habilitar NAC para Citrix SSO en iOS:
- Utilice Citrix Gateway 12.0.59 o superior.  
- Los usuarios deben tener instalado Citrix SSO 1.1.6 o posterior.
- [Integre NetScaler con Intune para NAC](https://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html) tal y como se describe en la documentación del producto de Citrix.
- En la configuración de VPN base, para **Habilitar el control de acceso a la red (NAC)**, active la casilla **Acepto**.

Al usar Citrix SSO para iOS, la conexión VPN se desconecta cada 24 horas por motivos de seguridad. VPN se puede volver a conectar inmediatamente.


**El control de acceso de red no se admite actualmente para los siguientes clientes de VPN en iOS**:
-   Cisco AnyConnect
-   F5 Access

Estamos trabajando con nuestros asociados para lanzar una solución de NAC para estos clientes más recientes. Cuando haya una solución lista, se actualizará este artículo con información adicional. 


## <a name="next-steps"></a>Pasos siguientes

- [Integrar Cisco ISE con Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)
- [Integrar Citrix NetScaler con Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)
- [Integrar HP Aruba Clear Pass con Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=31271)
- [Integrar Squadra Security Removable Media Manager (secRMM) con Intune](http://www.squadratechnologies.com/StaticContent/ProductDownload/secRMM/9.9.0.0/secRMMIntuneAccessControlSetupGuide.pdf)
