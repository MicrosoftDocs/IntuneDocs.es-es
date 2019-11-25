---
title: 'Configurar opciones de Endpoint Protection en Microsoft Intune: Azure | Microsoft Docs'
description: Cree la configuración de Endpoint Protection al crear un perfil de dispositivo de macOS o Windows 10 en Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/18/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
mr.reviewer: karthib
ms.openlocfilehash: 45cdbfe98bca8f7b0e307ed47ad3f78193e6d04c
ms.sourcegitcommit: 15e099a9a1e18296580bb345610aee7cc4acd126
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/18/2019
ms.locfileid: "74164561"
---
# <a name="add-endpoint-protection-settings-in-intune"></a>Agregar la configuración de Endpoint Protection en Intune

Con Intune, puede usar perfiles de configuración de dispositivos para administrar características de seguridad de protección de puntos de conexión comunes en los dispositivos, incluidos:

- Firewall
- BitLocker
- Permitir o bloquear aplicaciones
- Microsoft Defender y cifrado

Por ejemplo, puede crear un perfil de Endpoint Protection que solo permita a los usuarios de macOS instalar aplicaciones desde Mac App Store. O bien, que habilite Windows SmartScreen al ejecutar aplicaciones en dispositivos de Windows 10.

Antes de crear un perfil, revise estos artículos que detallan la configuración de la protección de puntos de conexión que Intune puede administrar para cada plataforma compatible:

- [Configuración de macOS](endpoint-protection-macos.md)
- [Configuración de Windows 10](endpoint-protection-windows-10.md)

## <a name="create-a-device-profile-containing-endpoint-protection-settings"></a>Crear un perfil de dispositivo que contenga la configuración de Endpoint Protection

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. Escriba un **Nombre** y una **Descripción** para el perfil de Endpoint Protection.

4. En la lista desplegable **Plataforma**, seleccione la plataforma del dispositivo a la que quiere aplicar configuración personalizada. Actualmente, puede elegir una de las siguientes plataformas para la configuración de restricciones de dispositivos:

   - **macOS**
   - **Windows 10 y versiones posteriores**

5. En la lista desplegable de **Tipos de perfil**, pulse **Endpoint Protection**.

6. Dependiendo de la plataforma que haya elegido, las opciones que pueda configurar serán diferentes. Vea:

   - [Configuración de macOS](endpoint-protection-macos.md)
   - [Configuración de Windows 10](endpoint-protection-windows-10.md)

7. Después de ajustar la configuración aplicable, seleccione **Crear** en la página **Crear perfil**.

   Se creará el perfil y aparecerá en la página con la lista de perfiles. Para asignar este perfil a grupos, consulte [Asignación de perfiles de dispositivo](../configuration/device-profile-assign.md).

## <a name="add-custom-firewall-rules-for-windows-10-devices"></a>Adición de reglas de firewall personalizadas para dispositivos Windows 10

Cuando se configura el firewall de Microsoft Defender como parte de un perfil que incluye reglas de protección de punto de conexión para Windows 10, se pueden configurar reglas personalizadas para los firewalls. Las reglas personalizadas permiten expandir el conjunto predefinido de reglas de firewall compatibles con Windows 10.

Cuando planee perfiles con reglas de firewall personalizadas, tenga en cuenta la siguiente información, que podría afectar a la forma en que se elige agrupar las reglas de firewall en los perfiles:

- Cada perfil admite hasta 150 reglas de firewall. Si usa más de 150 reglas, cree perfiles adicionales, cada uno de ellos limitado a 150 reglas.

- En cada perfil, si se produce un error en una sola regla, se producirá un error en todas las reglas de ese perfil y no se aplicará ninguna al dispositivo.

- Cuando se produce un error en una regla, todas las reglas del perfil se notifican como erróneas. Intune no puede identificar la regla en concreto que ha producido el error.  

Las reglas de firewall que Intune puede administrar se detallan en el [proveedor del servicio de configuración (CSP) de firewall]( https://docs.microsoft.com/windows/client-management/mdm/firewall-csp) de Windows. Para revisar la lista de configuraciones de firewall personalizadas para dispositivos Windows 10 compatibles con Intune, consulte [Reglas de firewall personalizadas](endpoint-protection-windows-10.md#firewall-rules).

### <a name="to-add-custom-firewall-rules-to-an-endpoint-protection-profile"></a>Adición de reglas de firewall personalizadas a un perfil de protección de punto de conexión

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfiles de configuración** > **Crear perfil**.

3. En *Plataforma*, seleccione **Windows 10 y versiones posteriores** y, luego, en *Tipo de perfil* seleccione **Protección de punto de conexión**.

4. Seleccione **Firewall de Microsoft Defender** para abrir la página de configuración y, después, en *Reglas de firewall*, seleccione **Agregar** para abrir la página **Crear regla**.

5. Especifique la configuración de la regla de firewall y luego seleccione **Aceptar** para guardarla. Para revisar las opciones de reglas de firewall personalizadas disponibles en la documentación, consulte [Reglas de firewall personalizadas](endpoint-protection-windows-10.md#firewall-rules).

6. Después de guardar la regla, aparece en la página *Firewall de Microsoft Defender* de la lista de reglas.

7. Para modificar una regla, seleccione la regla de la lista para abrir la página **Editar regla**.

8. Para eliminar una regla de un perfil, seleccione los puntos suspensivos **(...)** de la regla y, luego, seleccione **Eliminar**.

9. Para cambiar el orden en que se muestran las reglas, seleccione el icono de *flecha arriba, flecha abajo* en la parte superior de la lista de reglas.

## <a name="next-steps"></a>Pasos siguientes

Para asignar un perfil a grupos, vea [Asignación de perfiles de dispositivo](../configuration/device-profile-assign.md).
