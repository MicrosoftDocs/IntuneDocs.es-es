---
title: El dispositivo Android parece estar cifrado
description: 
keywords: 
author: barlanmsft
ms.author: barlan
manager: angrobe
ms.date: 05/25/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope: User help
ROBOTS: 
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.openlocfilehash: 269ad7968242f8f5ce7095c9c73347987675e846
ms.sourcegitcommit: 34cfebfc1d8b81032f4d41869d74dda559e677e2
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/01/2017
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>El dispositivo Android parece estar cifrado, pero el Portal de empresa indica lo contrario

Al cifrar un dispositivo, se codifica la información que contiene mediante una clave secreta que solo usted conoce, lo que evita el acceso de usuarios no autorizados. Para asegurarnos de que su información está protegida, la organización le pide que cifre su dispositivo Android antes de poder acceder a archivos, correos electrónicos o datos de la empresa.

## <a name="common-issues"></a>Problemas comunes

Las versiones más recientes de Android, especialmente desde la versión 7.0, requieren un código de acceso de inicio para garantizar que el dispositivo está completamente cifrado. Los distintos fabricantes de dispositivos tienen diferentes descripciones y ubicaciones para el código de acceso de inicio. En la mayoría de los casos, se conoce como "Inicio seguro". 

## <a name="solutions"></a>Soluciones

### <a name="add-a-startup-pin"></a>Agregar un PIN de inicio

Ciertos dispositivos Android requerirán que cree un PIN de inicio para garantizar que el dispositivo esté seguro. Existen muchas versiones de Android de muchos fabricantes distintos. Para intentar corregir este problema, encuentre una ubicación en la aplicación de configuración para habilitar esta opción. Por ejemplo, en el Samsung Galaxy S7, habilita el inicio seguro en **Configuración** > **Pantalla de bloqueo y seguridad** > **Inicio seguro**.  

### <a name="downgrade-your-version-of-android"></a>Cambiar a la versión anterior de Android
Si el dispositivo ofrece la opción de cambiar a la versión Android 6.0+, hágalo. Si intenta cambiar el dispositivo a una versión anterior, existe riesgo de pérdida de datos. Si no, se recomienda que se ponga en contacto con el administrador de TI para resolver este problema. Puede obtener información de contacto del administrador de TI en el [sitio web del Portal de empresa](http://portal.manage.microsoft.com).

## <a name="specific-manufacturer-issues"></a>Problemas específicos del fabricante

Algunos dispositivos Android de la versión 7.0+ cifran los datos de maneras no coherentes con determinados estándares de la plataforma Android. Estos dispositivos parecen venir cifrados de fábrica, pero Intune reconoce los métodos usados como si la información del dispositivo estuviera en peligro por parte de usuarios malintencionados con acceso físico al dispositivo.

> [!Note]
> Microsoft trabaja junto con los fabricantes para abordar cualquier problema que se encuentre durante las pruebas o que los usuarios informen. Este artículo se actualizará cada vez que haya nueva información disponible. 

## <a name="known-devices"></a>Dispositivos conocidos

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Dispositivos conocidos que se pueden actualizar para corregir este problema

Si tiene uno de los dispositivos siguientes, puede experimentar este problema si no ha actualizado el dispositivo a la versión más reciente de Android. Puede instalar las actualizaciones de estos dispositivos en **Configuración** > **Actualizar**. 

- [Huawei Honor 8](http://consumer.huawei.com/en/support/mobile-phones/honor8_en-sup.htm)
- [Huawei P9](http://consumer.huawei.com/mobile-phones/p9/index.html)

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Dispositivos conocidos que actualmente no se puede actualizar para corregir este problema

- [Huawei Mate 8](http://consumer.huawei.com/en/mobile-phones/mate8/index.htm)
- [Smartphones Xiaomi Mi](https://xiaomi-mi.com/mi-smartphones/)
