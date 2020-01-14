---
title: 'Escenario guiado: Aplicaciones móviles seguras de Microsoft Office'
titleSuffix: Microsoft Intune
description: Obtenga información sobre el escenario guiado para implementar aplicaciones móviles de Microsoft Office seguras desde el portal de administración de dispositivos de Microsoft 365.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/06/2020
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: dagerrit
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 3399cf006543c0a3554c4c6ec812554462d74231
ms.sourcegitcommit: a66b5916eaab9cb537e483064efc584a6a63a390
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/07/2020
ms.locfileid: "75691818"
---
# <a name="guided-scenario---secure-microsoft-office-mobile-apps"></a>Escenario guiado: Aplicaciones móviles seguras de Microsoft Office 

Si se sigue este escenario guiado en el portal de administración de dispositivos, se habilitará la protección de aplicaciones básica de Intune en dispositivos iOS y Android.

La protección de aplicaciones que se habilita aplicará las siguientes acciones: 
- Cifrar los archivos de trabajo
- Requerir un PIN para acceder a los archivos de trabajo
- Requerir que se restablezca el PIN después de cinco intentos fallidos
- Impedir que se hagan copias de seguridad de los archivos de trabajo en los servicios de copia de seguridad de iTunes, iCloud y Android  
- Requerir que los archivos de trabajo se guarden únicamente en OneDrive o SharePoint
- Impedir que las aplicaciones protegidas carguen archivos de trabajo en dispositivos con jailbreak o rooting
- Bloquear el acceso a los archivos de trabajo si el dispositivo lleva 720 minutos sin conectarse
- Quitar archivos de trabajo si el dispositivo lleva 90 días sin conectarse 

## <a name="background"></a>Contexto

Las aplicaciones móviles de Office, así como Microsoft Edge para dispositivos móviles, admiten la identidad dual. La identidad dual permite a las aplicaciones administrar archivos de trabajo de forma independiente de los archivos personales. 

![Imagen de datos corporativos frente a datos personales](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-01.png)

Las [directivas de protección de aplicaciones de Intune](~/apps/app-protection-policy.md) ayudan a proteger los archivos de trabajo almacenados en dispositivos inscritos en Intune. También puede usar directivas de protección de aplicaciones en dispositivos que poseen los empleados que no están inscritos para administración en Intune. En este caso, aunque la empresa no administre el dispositivo, deberá asegurarse de que los archivos de trabajo y los recursos de la empresa están protegidos.

Puede usar directivas de protección de aplicaciones para impedir a los usuarios que guarden archivos de trabajo en ubicaciones desprotegidas. También puede restringir el movimiento de datos a otras aplicaciones que no estén protegidas por directivas de protección. La configuración de directivas de protección de aplicaciones incluyen:
- Las directivas de reubicación de datos como **Guardar copias de los datos de la organización** y **Restringir funciones Cortar, Copiar y Pegar**.
- Opciones de directivas de acceso para requerir un PIN sencillo para el acceso o bloquear las aplicaciones administradas para que no se ejecuten en dispositivos con jailbreak o rooting

El acceso condicional basado en aplicación y la administración de aplicaciones cliente agregan una capa de seguridad al garantizar que solo las aplicaciones cliente que admiten las directivas de protección de aplicaciones de Intune pueden tener acceso a Exchange Online y a otros servicios de Office 365.

Puede bloquear las aplicaciones de correo electrónico integradas en iOS y Android cuando solo se permite a la aplicación Microsoft Outlook tener acceso a Exchange Online. Además, puede bloquear las aplicaciones que no tienen directivas de protección de aplicaciones de Intune aplicadas para que no puedan acceder a SharePoint Online.

En este ejemplo, el administrador ha aplicado directivas de protección de aplicaciones a la aplicación Outlook, seguidas de una regla de acceso condicional que agrega la aplicación Outlook a una lista de aplicaciones admitidas que pueden usarse al obtener acceso al correo electrónico corporativo.

![Flujo del proceso de acceso condicional de la aplicación de Outlook](./media/guided-scenarios-office-mobile/guided-scenarios-office-mobile-02.png)

## <a name="prerequisites"></a>Requisitos previos

Necesitará los siguientes permisos de administrador de Intune:

   - Permisos de lectura, creación, eliminación y asignación de aplicaciones administradas
   - Permisos de lectura, creación y asignación de conjuntos de directivas
   - Permiso de lectura de la organización

## <a name="step-1---introduction"></a>Paso 1: introducción

Si se sigue el escenario guiado de **protección de aplicaciones de Intune**, impedirá que los datos se compartan o se filtren fuera de la organización. 

Los usuarios de iOS y Android asignados deben escribir un PIN cada vez que abran una aplicación de Office. Tras cinco intentos de PIN incorrectos, los usuarios deben restablecer el PIN. Si ya se requiere un PIN de dispositivo, los usuarios no se verán afectados.

### <a name="what-you-will-need-to-continue"></a>Qué se necesita para continuar

Le preguntaremos por las aplicaciones que los usuarios necesitan y lo que es necesario para acceder a ellas. Asegúrese de tener la siguiente información a mano:
- Lista de las aplicaciones de Office aprobadas para su uso corporativo
- Cualquier requisito de PIN para iniciar aplicaciones aprobadas en dispositivos no administrados

## <a name="step-2---basics"></a>Paso 2: aspectos básicos

En este paso, debe especificar el **Prefijo** y una **Descripción** de la nueva directiva de protección de aplicaciones. Cuando agregue el **Prefijo**, se actualizarán los detalles relacionados con los recursos creados en el escenario guiado. Estos detalles permitirán encontrar más fácilmente las directivas más adelante por si necesita cambiar las asignaciones y la configuración. 

> [!TIP]
> Considere la posibilidad de tomar nota de los recursos que se crearán para, así, poder hacer referencia a ellos posteriormente.

## <a name="step-3---apps"></a>Paso 3: aplicaciones

Para ayudarle a empezar, en este escenario guiado ya se han seleccionado previamente las siguientes aplicaciones móviles para protegerlas en dispositivos iOS y Android:
- Microsoft Excel 
- Microsoft Word 
- Microsoft Teams 
- Microsoft Edge 
- Microsoft PowerPoint 
- Microsoft Outlook 
- Microsoft OneDrive 

En este escenario guiado también se configurarán estas aplicaciones para abrir vínculos web en Microsoft Edge con el fin de garantizar que los sitios de trabajo se abren en un explorador protegido.

Modifique la lista de aplicaciones administradas por directivas que quiera proteger. En la lista, agregue o quite aplicaciones. 

Cuando termine de seleccionar las aplicaciones, haga clic en **Siguiente**.

## <a name="step-4---configuration"></a>Paso 4: configuración

En este paso, debe configurar los requisitos de acceso y uso compartido de los archivos y correos electrónicos corporativos en estas aplicaciones. Los usuarios pueden guardar los datos de forma predeterminada en las cuentas de OneDrive y SharePoint de la organización.

| Setting | Descripción | Valor predeterminado |
|---------------------------------------------------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|---------------|
| Tipo de PIN | Los PIN numéricos se componen únicamente de números, mientras que los códigos de acceso pueden contener caracteres alfanuméricos y caracteres especiales.  Para configurar el tipo de código de acceso en iOS/iPadOS, es necesario que la aplicación tenga la versión 7.1.12 del SDK de Intune o una versión posterior. El tipo numérico no tiene ninguna restricción de versión para el SDK de Intune. | Numérico |
| Seleccionar la longitud mínima del PIN | especifique el número mínimo de dígitos en una secuencia de PIN. | 6 |
| Volver a comprobar los requisitos de acceso tras (minutos de inactividad) | Si la aplicación administrada por directivas lleva inactiva más tiempo que el número de minutos de inactividad aquí especificado, la aplicación pedirá que se vuelvan a comprobar los requisitos de acceso (esto es, el PIN, la configuración de inicio condicional) después de que se inicie la aplicación. | 30 |
| Impresión de datos de la organización | Si se establece en Bloquear, la aplicación no puede imprimir datos protegidos. | Bloquear |
| Abrir vínculos de aplicaciones administradas por directivas en exploradores no administrados | Si se establece en Bloquear, los vínculos de las aplicaciones administradas por directivas se deben abrir en un explorador administrado. | Bloquear |
| Copiar datos en aplicaciones no administradas | Si se establece en Bloquear, los datos administrados permanecerán en las aplicaciones administradas. | Allow |

## <a name="step-5---assignments"></a>Paso 5: asignaciones

En este paso, puede elegir los grupos de usuarios que quiere incluir para asegurarse de que tienen acceso a los datos corporativos. La protección de aplicaciones se asigna a usuarios, no a dispositivos, por lo que los datos corporativos serán seguros independientemente del dispositivo que se use y su estado de inscripción.

Los usuarios que no tengan asignadas directivas de protección de aplicaciones ni una configuración de acceso condicional podrán guardar datos de su perfil corporativo en aplicaciones personales y en un almacenamiento local no administrado de sus dispositivos móviles. También podrán conectarse a servicios de datos corporativos (como, por ejemplo, Microsoft Exchange) con sus aplicaciones personales.

## <a name="step-6---review--create"></a>Paso 6: revisión y creación

El último paso permite revisar un resumen de los valores que ha configurado. Una vez que haya revisado las opciones, haga clic en **Crear** para completar el escenario guiado. Tras completar el escenario guiado, se muestra una tabla de recursos. Puede editar estos recursos más adelante, pero una vez que salga de la vista de resumen, la tabla no se guardará.

> [!IMPORTANT]
> Cuando el escenario guiado se complete, se mostrará un resumen. Los recursos mencionados en este resumen se pueden modificar más adelante, pero la tabla en la que se muestran estos recursos no se guardará.
## <a name="next-steps"></a>Pasos siguientes

- Para mejorar la seguridad de los archivos de trabajo, asigne a los usuarios una directiva de acceso condicional basado en aplicaciones que impida que los servicios en la nube envíen archivos de trabajo a aplicaciones sin protección. Para más información, vea [Configuración de directivas de acceso condicional basado en la aplicación con Intune](~/protect/app-based-conditional-access-intune-create.md).

