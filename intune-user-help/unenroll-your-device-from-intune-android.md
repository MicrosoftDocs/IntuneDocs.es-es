---
title: Cómo quitar un dispositivo Android de Intune | Microsoft Docs
description: Describe cómo anular la inscripción de un dispositivo Android de Intune.
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 03/23/2018
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: f40aab26-7613-48cc-a74e-de83df9465a4
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: ec3c0a1c8ce4e04f4d23fb01e7c2525d8f2eed5b
ms.sourcegitcommit: 5eba4bad151be32346aedc7cbb0333d71934f8cf
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 04/16/2018
---
# <a name="how-to-remove-your-android-device-from-intune"></a>Cómo quitar un dispositivo Android de Intune

Cuando quite su dispositivo Android de Intune, el dispositivo ya no podrá tener acceso a recursos de la empresa.  Para obtener más información sobre lo que ocurre cuando se deja de administrar un dispositivo, vea [¿Qué ocurre cuando se anula la inscripción de un dispositivo de Intune?](what-happens-if-you-unenroll-your-device-from-intune-android.md)

## <a name="removing-the-device-from-the-company-portal-app"></a>Quitar un dispositivo de la aplicación Portal de empresa

Para quitar el dispositivo de Intune y la aplicación Portal de empresa, siga estos pasos:

1. Toque los tres puntos verticales en la esquina superior derecha de la aplicación Portal de empresa de Intune para abrir el **menú de acciones**.

   ![Una imagen de la aplicación de Portal de empresa de Android con el menú de acciones abierto en la esquina superior derecha. La nueva opción "quitar portal de empresa" está disponible como la tercera opción, debajo de "mi perfil" y "configuración" y sobre "términos y condiciones", "ayuda y comentarios" e "información".](./media/android_remove_cp_menu_action_after_1705.png)

2. Pulse **Quitar Portal de empresa**.

3. Aparecerá una ventana emergente de confirmación, en la que se le preguntará si está seguro de quitar Portal de empresa de Intune. En ella se proporcionará información sobre lo que sucede cuando anula la inscripción del dispositivo. Después de leer este mensaje, pulse **Aceptar** para quitar la aplicación.

   ![Una imagen del cuadro de diálogo de confirmación, disponible después de seleccionar la nueva opción "quitar portal de empresa" del menú de acciones. El cuadro de diálogo informa al usuario que "al quitar Portal de empresa, el dispositivo ya no estará administrado por el equipo de soporte técnico de su empresa y podrá quitar el acceso a los datos, las aplicaciones y el correo electrónico de la empresa". Luego se le pide al usuario que seleccione "Sí" para confirmar que desea quitar la aplicación Portal de empresa.](./media/android_remove_cp_menu_confirmation_after_1705.png)

## <a name="removing-data-collected-by-the-company-portal-app"></a>Eliminación de datos recopilados por la aplicación Portal de empresa

Para quitar todos los datos que la aplicación Portal de empresa para Android almacena en el dispositivo:

-   Para borrar los datos de la aplicación, vaya a Aplicaciones, haga clic en la aplicación y luego en el botón "Borrar datos".
-   Elimine la carpeta "\storage\internal storage\Android\data\com.microsoft.windowsintune.companyportal".

¿Sigue necesitando ayuda? Póngase en contacto con el departamento de soporte técnico de la empresa. Para averiguar su información de contacto, vaya al [sitio web del portal de empresa](https://portal.manage.microsoft.com#HelpDeskDialog).
