---
title: "Supervisión de información de aplicación y asignaciones"
titlesuffix: Azure portal
description: "Después de haber asignado una aplicación a usuarios o dispositivos, use esta información para que le ayude a supervisar su estado."
keywords: 
author: erikre
ms.author: erikre
manager: dougeby
ms.date: 11/21/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 64e5133d-1e23-4ee6-b556-f5d32c0e95da
ms.reviewer: mghadial
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: 85ecc9729d7c03cb760c14bda0ca4d6321af548e
ms.sourcegitcommit: a41ad9988a8c14e6b15123a9ea9bc29ac437a4ce
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2018
---
# <a name="how-to-monitor-app-information-and-assignments-with-microsoft-intune"></a>Supervisión de información de aplicación y asignaciones con Microsoft Intune

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Intune proporciona diversas maneras en las cuales puede supervisar las propiedades de las aplicaciones que administra, así como el estado de la asignación.

1. Inicie sesión en Azure Portal.
2. Elija **More Services** >  (Más servicios) **Supervisión y administración** + **Intune**.
3. En la carga de trabajo **Aplicaciones móviles**, elija **Aplicaciones** en el grupo **Administrar**.
5. En la lista de la hoja de aplicaciones, elija una aplicación. Verá la hoja **Estado de instalación del dispositivo** de <*nombre de la aplicación*> .

## <a name="app-overview-blade"></a>Hoja de información general sobre las aplicaciones

Puede usar la hoja <*nombre de la aplicación*> **Estado de instalación del dispositivo** para revisar los detalles sobre el estado de una aplicación en su entorno.

### <a name="essentials"></a>Essentials

En la sección **Essentials** se incluye la siguiente información sobre la aplicación:

 - **Publicador**  
Editor de la aplicación.
 - **Sistema operativo**  
El sistema operativo de la aplicación (Windows, iOS, Android, etc.)
 - **Crear**  
Fecha y hora de creación de esta revisión.
 - **Asignado**  
**Sí** o **No** si se ha asignado la aplicación.

### <a name="status"></a>Estado
Cada gráfico muestra recuentos para los estados siguientes:

 - **Instalado**  
El número de aplicaciones instaladas.
 - **Sin instalar**  
El número de aplicaciones sin instalar.
 - **Instalación pendiente**  
El número de aplicaciones en proceso de ser instaladas.
 - **Error**  
El número de errores de instalación.
 - **Desconocida**  
El número de aplicaciones con un estado desconocido.

### <a name="device-status"></a>Estado del dispositivo

El estado del dispositivo. Un gráfico de anillos en el que se muestra el estado de instalación de la aplicación en los dispositivos. Haga clic en el gráfico para abrir una lista de detalles sobre el estado del dispositivo. En la tabla de detalles se incluyen las columnas siguientes:

 - **Nombre del dispositivo**  
Nombre del dispositivo en plataformas que permiten asignar nombre a un dispositivo. En otras plataformas, Intune crea un nombre a partir de otras propiedades. Este atributo no puede estar disponible para todos los dispositivos.
 - **Nombre de usuario**  
Nombre del usuario.
 - **Plataforma**  
El sistema operativo del dispositivo (Windows, iOS, Android, etc.)
 - **Versión**  
El número de versión de la aplicación. Para las aplicaciones de línea de negocio se muestra el número de versión completa de la aplicación. El número de versión completo identifica una versión específica de la aplicación. El número aparece como _versión_(_compilación_). Por ejemplo, 2.2(2.2.17560800).
 - **Estado**  
El estado de la aplicación.
 - **Detalles de estado**  
Los detalles del estado.
 - **Última inserción en el repositorio**  
Fecha de la última sincronización de dispositivos con Intune.


### <a name="user-status"></a>Estado del usuario

El estado del usuario. Un gráfico de anillos en el que se muestra el estado de instalación de la aplicación para los usuarios. Haga clic en el gráfico para abrir una lista de detalles sobre el estado del dispositivo. En la tabla de detalles se incluyen las columnas siguientes:
 - **Nombre**  
El nombre del usuario en Azure AD.
 - **Nombre de usuario**  
El nombre único del usuario.
 - **Instalaciones**  
Número de instalaciones de aplicaciones usadas por el usuario.
 - **Errores**  
Número de errores de instalación del usuario.
 - **Sin instalar**  
Número de aplicaciones sin instalar por el usuario.


## <a name="next-steps"></a>Pasos siguientes

Para obtener más información sobre cómo trabajar con los datos de Intune, vea [Usar el almacenamiento de datos de Intune](reports-nav-create-intune-reports.md).