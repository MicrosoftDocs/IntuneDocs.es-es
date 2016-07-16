---
title: Solucionar problemas de acceso condicional|Microsoft Intune
description: 
keywords: 
author: nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 433fc32c-ca9c-4bad-9616-852c72faf996
ms.reviewer: chrisgre
ms.suite: ems
translationtype: Human Translation
ms.sourcegitcommit: 4f79d2890c450a803bfb84ffa3c12b0de58a158c
ms.openlocfilehash: 373b9bf9794840f999d5e5b21fc411ff621a23e1


---

# Solucionar problemas de acceso condicional

En este tema se explica qué hacer cuando los usuarios no pueden obtener acceso a los recursos a través del acceso condicional de Intune. 

### Aspectos básicos para el éxito del acceso condicional

Para que el acceso condicional funcione, necesita las siguientes condiciones:

-   Intune tiene que administrar el dispositivo.
-   El usuario tiene que estar registrado con Azure Active Directory (AAD).
-   El dispositivo debe cumplir las directivas de cumplimiento configuradas en Intune. 
-   Si el usuario recupera el correo a través del cliente de correo nativo del dispositivo en lugar de hacerlo a través de Outlook, EAS debe estar activado en el dispositivo.

Es posible ver si estas condiciones se cumplen en un dispositivo en el Portal de administración de Azure y en el informe de inventario del dispositivo.





Normalmente, cuando un usuario intenta acceder al correo o a SharePoint recibe una solicitud de inscripción. Esa solicitud llevará al usuario al portal de empresa. Estas son las posibles explicaciones de este comportamiento y las soluciones sugeridas:

## Escenarios de autenticación moderna

### Problemas de inscripción

 -  El dispositivo no está inscrito, así que la inscripción solucionará el problema.
 -  El usuario inscribió el dispositivo, pero se produjo un error en la unión al área de trabajo. El usuario debe actualizar la inscripción desde el portal de empresa. 
 
### Problemas de cumplimiento

 -  El dispositivo no cumple la directiva de Intune. Algunos problemas comunes son los requisitos de cifrado y contraseña. Se redirigirá al usuario al portal de empresa, donde podrá configurar el dispositivo para que sea compatible.
 -  En el caso de los dispositivos iOS, un perfil de correo existente creado por el usuario bloqueará la implementación de un perfil compatible (creado por el administrador de Intune) desde Intune. Este es un problema común, ya que los usuarios de iOS suelen crear un perfil de correo y luego inscribirse. El portal de empresa informará al usuario de que no son compatibles debido a su perfil de correo configurado manualmente y le pedirá que quite ese perfil. El usuario debe quitar su perfil de correo para que se pueda implementar el perfil de Intune. Para evitar el problema, indique a los usuarios que se inscriban sin instalar un perfil de correo y que permitan que Intune implemente el perfil.  
 -  El registro de la información de cumplimiento de un dispositivo puede llevar un tiempo. Espere unos minutos y vuelva a intentarlo .

### Problemas de directivas

Al crear una directiva de cumplimiento y vincularla a una directiva de correo, las dos directivas deben implementarse en el mismo usuario, así que tenga cuidado al planear qué directivas se implementan en qué grupos. Los usuarios que tienen una sola directiva aplicada probablemente descubran que sus dispositivos no son compatibles.


## Escenarios de Exchange ActiveSync


- Un dispositivo Android inscrito y compatible puede recibir un aviso de cuarentena al intentar acceder a recursos corporativos. Antes de seleccionar el vínculo **Comenzar**, el usuario debe asegurarse de que el portal de empresa no estaba abierto cuando intentó acceder a los recursos. Los usuarios deben cerrar el portal de empresa, intentar acceder de nuevo a los recursos y luego seleccionar el vínculo **Comenzar**.

- Un dispositivo retirado puede seguir teniendo acceso durante varias horas después de la retirada. Esto es se debe a que Exchange almacena en caché los derechos de acceso durante 6 horas. Considere otras formas de proteger los datos en dispositivos retirados en este escenario.
- Posible problema, no se puede actualizar EASID a AAD. Una causa común de este problema es la limitación de peticiones, así que espere unos minutos e inténtelo de nuevo. 

## Recopilar registros de buzón OWA

Si los problemas de conectividad de Exchange continúan después de solucionar los problemas de implementación, recopile los registros de buzón OWA antes de ponerse en contacto con el servicio de soporte técnico de Microsoft como se explica en [Cómo obtener asistencia para Microsoft Intune](how-to-get-support-for-microsoft-intune.md).

1. Inicie sesión a través de OWA y seleccione el símbolo de configuración (engranaje) situado junto a su nombre en la esquina superior derecha. 
2. Seleccione **Opciones**.
3. Seleccione **Teléfono** (podría ser **Dispositivos móviles**) en la columna del lado izquierdo.
4. En el menú superior, seleccione **Dispositivos móviles**. 
5. Seleccione el dispositivo en la lista y luego **Iniciar registro**. 
6. Cuando se le pida, seleccione **Sí** en el cuadro de diálogo emergente. 
7. Realice la acción que causó el problema, para poder reproducirlo. 
8. Espere de 1 a 2 minutos y vuelva a la lista de teléfonos en OWA (asegúrese de que el teléfono esté seleccionado en ella) y en el menú superior seleccione **Recuperar registro**. 
9. Ahora debería tener un correo de usted mismo con datos adjuntos. Cuando abra una incidencia de soporte técnico, proporcione el contenido del correo al servicio de soporte técnico de Microsoft.


### Pasos siguientes
Si esta información para solucionar problemas no le ha ayudado, póngase en contacto con el servicio de soporte técnico de Microsoft como se indica en [How to get support for Microsoft Intune](how-to-get-support-for-microsoft-intune.md) (Cómo obtener soporte técnico de Microsoft Intune).



<!--HONumber=Jun16_HO4-->


