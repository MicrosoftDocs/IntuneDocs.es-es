---
title: "Integración del control de acceso de red con Intune"
titlesuffix: Azure portal
description: "Integración del control de acceso de red (NAC) con Intune"
keywords: 
author: andredm7
ms.author: andredm
manager: angrobe
ms.date: 06/23/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: aa7ecff7-8579-4009-8fd6-e17074df67de
ms.reviewer: davidra
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 6d75d996f4166fb2a760d1ccb518ca7a228c1a0d
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="network-access-control-nac-integration-with-intune"></a>Integración del control de acceso de red (NAC) con Intune

Intune se integra con partners de control de acceso de red para ayudar a las organizaciones a proteger los datos de empresa cuando los dispositivos intentan tener acceso a los recursos locales.

## <a name="how-do-intune-and-nac-solutions-help-protect-your-organization-resources"></a>¿Cómo Intune y las soluciones de NAC ayudan a proteger los recursos de su organización?

Las soluciones de NAC son las responsables de comprobar el estado de cumplimiento y la inscripción de dispositivos con Intune para tomar decisiones de control de acceso. Si el dispositivo no está inscrito o si está inscrito y no es compatible con las directivas de cumplimiento de dispositivos de Intune, el dispositivo debe redirigirse a Intune para su inscripción o para una comprobación de cumplimiento de dispositivos.

### <a name="example"></a>Ejemplo

Si el dispositivo está inscrito y es compatible con Intune, la solución de NAC debe permitir el acceso del dispositivo a los recursos de la empresa. Por ejemplo, a los usuarios se les puede permitir o denegar el acceso al intentar tener acceso a los recursos de VPN o Wi-Fi de la empresa.

## <a name="nac-and-conditional-access"></a>NAC y acceso condicional

NAC funciona con el acceso condicional para proporcionar decisiones de control de acceso.

- Vea [las formas comunes de usar el acceso condicional con Intune](conditional-access-intune-common-ways-use.md) para obtener más información.

## <a name="how-the-nac-integration-works"></a>Cómo funciona la integración de NAC

Aquí se muestra información general sobre cómo funciona la integración de NAC cuando está integrada con Intune, los tres primeros pasos explican el proceso de incorporación. Una vez que la solución de NAC está integrada con Intune, los pasos 4 a 9 describen la operación en curso.

![Cómo funciona NAC con Intune](./media/ca-intune-common-ways-2.png)

1.  Registre la solución de partner de NAC con Azure Active Directory (AAD), y conceda permisos delegados a la API de NAC de Intune.

2.  Configure la solución de partner de NAC con las opciones correctas incluida la URL de detección de Intune.

3.  Configure la solución de partner de NAC para la autenticación de certificados.

4.  El usuario se conecta al punto de acceso de Wi-Fi de la empresa o realiza una solicitud de conexión VPN.

5.  La solución de partner de NAC reenvía la información del dispositivo a Intune y pregunta a Intune sobre el estado de cumplimiento y la inscripción de dispositivos.

6.  Si el dispositivo no es compatible o no está inscrito, la solución de partner de NAC indica al usuario que inscriba o corrija el cumplimiento del dispositivo.

7.  El dispositivo intenta volver a comprobar su cumplimiento o su estado de inscripción.

8.  Una vez que el dispositivo está inscrito y es compatible, la solución de partner de NAC obtiene el estado de Intune.

9.  La conexión se establece correctamente lo que permite al dispositivo tener acceso a los recursos de empresa.

## <a name="next-steps"></a>Pasos siguientes

-   [Integrar Cisco ISE con Intune](http://www.cisco.com/c/en/us/td/docs/security/ise/2-1/admin_guide/b_ise_admin_guide_21/b_ise_admin_guide_20_chapter_01000.html)

-   [Integrar Citrix NetScaler con Intune](http://docs.citrix.com/en-us/netscaler-gateway/12/microsoft-intune-integration/configuring-network-access-control-device-check-for-netscaler-gateway-virtual-server-for-single-factor-authentication-deployment.html)

-   [Integrar HP Aruba Clear Pass con Intune](https://support.arubanetworks.com/Documentation/tabid/77/DMXModule/512/Command/Core_Download/Default.aspx?EntryId=23757)
