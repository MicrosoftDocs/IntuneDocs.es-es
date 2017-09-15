---
title: "Instalación de aplicaciones de Office 365 ProPlus en dispositivos Windows 10 mediante Intune"
titlesuffix: Azure portal
description: "Obtenga información sobre cómo puede usar Intune para facilitar la instalación de aplicaciones de Office 365 en dispositivos Windows 10."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 08/14/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 3292671a-5f5a-429e-90f7-b20019787d22
ms.reviewer: aiwang
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: c3613c1e0482654d799329069f56ec0b0aac7772
ms.sourcegitcommit: e10dfc9c123401fabaaf5b487d459826c1510eae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 09/09/2017
---
# <a name="how-to-assign-office-365-proplus-2016-apps-to-windows-10-devices-with-microsoft-intune"></a>Asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos Windows 10 con Microsoft Intune

Este tipo de aplicación facilita la asignación de aplicaciones de Office 365 ProPlus 2016 a dispositivos que administre y que ejecuten Windows 10. También puede instalar aplicaciones para el cliente de escritorio de Microsoft Project Online y Microsoft Visio Pro para Office 365, si posee sus licencias. Las aplicaciones que desea que aparezcan como una aplicación en la lista de aplicaciones de la consola de Intune.


## <a name="before-you-start"></a>Antes de empezar

>[!IMPORTANT]
>Este método de instalación de Office solo se admite si no hay otras versiones de Microsoft Office instaladas en el dispositivo.

- Los dispositivos en los que implementa estas aplicaciones deben ejecutar Windows 10 Creator Update o una versión posterior.
- Intune solo admite agregar aplicaciones de Office desde el conjunto de aplicaciones de Office 365 ProPlus 2016.
- Si alguna aplicación de Office está abierta cuando Intune instala el conjunto de aplicaciones, es posible que los usuarios finales pierdan los datos de los archivos no guardados.
- Este método de instalación no se admite en dispositivos Windows 10S.
- Intune no admite la instalación de aplicaciones de escritorio de Office 365 desde la Tienda Windows (estas aplicaciones se conocen como Office Centennial) en un dispositivo al que ya haya implementado aplicaciones de Office 365 con Intune. Si instala esta configuración, puede provocar daños o la pérdida de datos.


## <a name="get-started"></a>Introducción

1.  Inicie sesión en el portal de Azure.
2.  Elija **More Services** >  (Más servicios) **Supervisión y administración** > **Intune**.
3.  En la hoja **Intune**, elija **Aplicaciones móviles**.
4.  En la carga de trabajo **Mobile Apps**, elija **Administrar** > **Aplicaciones**.
5.  Encima de la lista de aplicaciones, elija **Agregar**.
6.  En la hoja **Agregar aplicación**, elija **Office 365 ProPlus Suite (Windows 10)**.

## <a name="configure-the-app-suite"></a>Configuración del conjunto de aplicaciones

En este paso, elija las aplicaciones de Office que desea asignar a los dispositivos.

1.  En la hoja **Agregar aplicación**, elija **Configure App Suite** (Configurar conjunto de aplicaciones).
2.  En la hoja **Configure App Suite** (Configurar conjunto de aplicaciones), elija las aplicaciones Office estándar que desea asignar a dispositivos. Además, puede instalar aplicaciones para el cliente de escritorio de Microsoft Project Online y Microsoft Visio para Office 365, si posee sus licencias.
3.  Cuando haya terminado, haga clic en **Aceptar**.

>[!IMPORTANT]
> Una vez que crea el conjunto de aplicaciones, no puede editar sus propiedades. Si desea configurar otras propiedades, elimine el conjunto de aplicaciones y cree otro.

## <a name="configure-app-information"></a>Configuración de información de la aplicación

En este paso, proporcione información sobre el conjunto de aplicaciones. Esta información le ayuda a identificarlo en Intune y, además, ayuda a los usuarios finales a encontrarlo en la aplicación Portal de empresa.

1.  En la hoja **Agregar aplicación**, elija **App Suite Information** (Información del conjunto de aplicaciones).
2.  En la hoja **App Suite Information** (Información del conjunto de aplicaciones), especifique la información siguiente: 
    - **Nombre del conjunto**: escriba el nombre del conjunto tal como se muestra en el portal de empresa. Asegúrese de que todos los nombres de conjuntos que use sean únicos. Si el mismo nombre del conjunto ya existe, solo se muestra una de las aplicaciones a los usuarios en el portal de empresa.
    - **Descripción del conjunto**: escriba una descripción del conjunto de aplicaciones. Por ejemplo, podría mostrar las aplicaciones que seleccionó para incluir.
    - **Editor:** escriba el nombre del editor de la aplicación.
    - **Categoría**: de manera opcional, seleccione una o más categorías de aplicaciones integradas o una categoría que haya creado. Esto facilita que los usuarios encuentren el conjunto de aplicaciones cuando exploren el portal de empresa.
    - **Mostrar como aplicación destacada en Portal de empresa de Intune**: el conjunto de aplicaciones se muestra de forma destacada en la página principal de Portal de empresa de Intune cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre esta aplicación. La dirección URL se muestra a los usuarios en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente,, escriba un nombre para el propietario de esta aplicación, por ejemplo, **departamento de Recursos Humanos**.
    - **Notas**: escriba notas que le gustaría asociar a esta aplicación.
    - **Cargar icono**: Cargar un icono que se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3.  Cuando haya terminado, haga clic en **Aceptar**.

## <a name="configure-app-settings"></a>Configuración de aplicaciones

En este paso, configure las opciones de instalación para el conjunto de aplicaciones. La configuración se aplica a todas las aplicaciones que agregó al conjunto.

1.  En la hoja **Agregar aplicación**, elija **App Suite Settings** (Configuración del conjunto de aplicaciones).
2.  En la hoja **App Suite Settings** (Configuración del conjunto de aplicaciones), especifique la información siguiente: 
    - **Versión de Office**: elija si desea asignar la versión de 32 bits o de 64 bits de Office. Puede instalar la versión de 32 bits en dispositivos de 32 y 64 bits, pero en los dispositivos de 64 bits solo puede instalar la versión de 64 bits.
    - **Canal de actualización**: elija cómo Office se actualiza en los dispositivos. Para información sobre los distintos canales de actualización, consulte la introducción a los canales de actualización para Office 365 ProPlus. Elija de entre las siguientes opciones: 
        - **Actual**
        - **Diferida**
        - **Primera versión actual**
        - **Primera versión diferida**
    - **Automatically accept the app end user license agreement** (Aceptar automáticamente el contrato de licencia del usuario final de la aplicación): seleccione esta opción si no requiere que los usuarios finales acepten el contrato de licencia. De ese modo, Intune aceptará automáticamente el contrato.
    - **Use shared computer activation** (Usar activación en equipos compartidos): la activación en equipos compartidos se usa cuando varios usuarios comparten un equipo. Para más información, consulte la introducción a la activación de equipos compartidos para Office 365 ProPlus.
    - **Idiomas**: Office se instala automáticamente en cualquier idioma compatible que se instale con Windows en el dispositivo de los usuarios finales. Seleccione esta opción si desea instalar más idiomas con el conjunto de aplicaciones.

>[!IMPORTANT]
> Una vez que crea el conjunto de aplicaciones, no puede editar sus propiedades. Si desea configurar otras propiedades, elimine el conjunto de aplicaciones y cree otro.

## <a name="finish-up"></a>Finalizar

Cuando haya terminado, en la hoja **Agregar aplicación**, elija **Guardar**. La aplicación que ha creado aparece en la lista de aplicaciones.

## <a name="error-codes-when-installing-the-app-suite"></a>Códigos de error en la instalación del conjunto de aplicaciones

La tabla siguiente muestra los códigos de error comunes que podría encontrar y su significado.

### <a name="status-for-office-csp"></a>Estado de Office CSP: 

||||
|-|-|-|
|Estado|Fase|Descripción|
|1460 (ERROR_TIMEOUT)|Descarga|No se pudo descargar la Herramienta de implementación de Office|    
|13 (ERROR_INVALID_DATA)|-|No se puede comprobar la firma de la Herramienta de implementación de Office descargada| 
|Código de error de CertVerifyCertificateChainPolicy|-|No se pudo comprobar la certificación de la Herramienta de implementación de Office descargada|    
|997|WIP|Instalación| 
|0|Después de la instalación|La instalación se realizó correctamente|    
|1603 (ERROR_INSTALL_FAILURE)|-|No se pudo realizar ninguna comprobación de requisitos previos, como:<br>- SxS (se intentó instalar con MSI 2016 instalado)<br>- versión no coincidente<br>- etc.|     
|0x8000ffff (E_UNEXPECTED)|-|Se intentó instalar sin Office Hacer clic y ejecutar en la máquina.|    
|17002|-|No se pudo completar el escenario (instalación). Posibles razones:<br>- El usuario canceló la instalación<br>- Otra instalación canceló la instalación<br>- Sin espacio en disco durante la instalación<br>- Identificación de idioma desconocido| 
|17004|-|SKU desconocidas|   


### <a name="office-deployment-tool-error-codes"></a>Códigos de error de la Herramienta de implementación de Office

|||||
|-|-|-|-|
|Escenario|Código de retorno|UI|Nota| 
|Trabajo de desinstalación sin una instalación de Hacer clic y ejecutar activa|-2147418113, 0x8000ffff o 2147549183|Código de error: 30088-1008<br>Código de error: 30125-1011 (404)|Herramienta de implementación de Office| 
|Instalación cuando hay instalada una versión de MSI|1603|-|Herramienta de implementación de Office| 
|El usuario u otra instalación canceló la instalación|17002|-|Hacer clic y ejecutar| 
|Intentar instalar 64 bits en un dispositivo con 32 bits instalados.|1603|-|Código de devolución de la Herramienta de implementación de Office| 
|Intentar instalar una SKU desconocida (no es un caso de uso legítimo de Office CSP porque solo podemos pasar SKU válidas)|17004|-|Hacer clic y ejecutar| 
|Falta de espacio|17002|-|Hacer clic y ejecutar| 
|El cliente Hacer clic y ejecutar no se pudo iniciar (inesperado)|17000|-|Hacer clic y ejecutar| 
|El cliente Hacer clic y ejecutar no pudo poner el escenario en cola (inesperado)|17001|-|Hacer clic y ejecutar| 

## <a name="next-steps"></a>Pasos siguientes

Ahora puede asignar las aplicaciones a los grupos de su preferencia. Para obtener ayuda, consulte [Asignación de aplicaciones a grupos](/intune-azure/manage-apps/deploy-apps).

             


