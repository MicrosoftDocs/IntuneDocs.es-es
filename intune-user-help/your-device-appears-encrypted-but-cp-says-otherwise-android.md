---
title: El dispositivo Android parece estar cifrado | Microsoft Docs
description: ''
keywords: ''
author: lenewsad
ms.author: lanewsad
manager: dougeby
ms.date: 11/14/2017
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: ba593c08-1a78-4013-8525-b45a948772ec
searchScope:
- User help
ROBOTS: ''
ms.reviewer: arnab
ms.suite: ems
ms.custom: intune-enduser
ms.collection: M365-identity-device-management
ms.openlocfilehash: 55935b2f69f9573d8df5ea5ca32fb4587c652b26
ms.sourcegitcommit: 25e6aa3bfce58ce8d9f8c054bc338cc3dff4a78b
ms.translationtype: MTE75
ms.contentlocale: es-ES
ms.lasthandoff: 03/14/2019
ms.locfileid: "57389460"
---
# <a name="your-android-device-seems-to-be-encrypted-but-company-portal-says-otherwise"></a>El dispositivo Android parece estar cifrado, pero el Portal de empresa indica lo contrario

Al cifrar un dispositivo, se codifica la información que contiene mediante una clave secreta que solo usted conoce. Esto evita el acceso de usuarios no autorizados. Muchas organizaciones exigen a sus usuarios que cifren sus dispositivos Android antes de obtener acceso a los archivos, al correo electrónico o a los datos de la empresa.

## <a name="common-issues"></a>Problemas comunes

Las versiones más recientes de Android, especialmente desde la versión 7.0, requieren un código de acceso de inicio para garantizar que el dispositivo está completamente cifrado. Los distintos fabricantes de dispositivos tienen diferentes descripciones y ubicaciones para el código de acceso de inicio. En la mayoría de los casos, esta configuración se conoce como "Inicio seguro". 

## <a name="solutions"></a>Soluciones

### <a name="add-a-startup-pin"></a>Agregar un PIN de inicio

Ciertos dispositivos Android le exigen que cree un PIN de inicio para garantizar que el dispositivo sea seguro. Existen muchas versiones de Android de muchos fabricantes distintos. Para intentar corregir este problema, encuentre una ubicación en la aplicación de configuración para habilitar esta opción. Por ejemplo, en el Samsung Galaxy S7, habilita el inicio seguro en **Configuración** > **Pantalla de bloqueo y seguridad** > **Inicio seguro**.  

### <a name="encrypt-the-entire-device"></a>Cifrado de todo el dispositivo

Algunos dispositivos le ofrecerán la opción de cifrar todo el dispositivo o simplemente el espacio usado. Elija la opción de cifrar todo el dispositivo en lugar de solo el espacio usado. Si ya ha cifrado solo el espacio usado:

1. [Quite este dispositivo del Portal de empresa.](unenroll-your-device-from-intune-android.md)
2. Descifre el espacio usado.
3. Cifrado de todo el dispositivo
4. Vuelva a inscribir el dispositivo.

### <a name="downgrade-your-version-of-android"></a>Cambiar a la versión anterior de Android

Si el dispositivo ofrece la opción de cambiar a la versión Android 6.0+, hágalo. Si intenta cambiar el dispositivo a una versión anterior, existe riesgo de pérdida de datos. Si no, se recomienda que se ponga en contacto con el equipo de soporte técnico de su empresa para resolver este problema. Puede obtener información de contacto del equipo de soporte técnico de su empresa en el [sitio web del Portal de empresa](https://go.microsoft.com/fwlink/?linkid=2010980).

## <a name="specific-manufacturer-issues"></a>Problemas específicos del fabricante

Algunos dispositivos Android de la versión 7.0+ cifran los datos de maneras incoherentes con determinados estándares de la plataforma Android. Estos dispositivos podrían aparecer cifrados, aunque sean completamente nuevos. Intune reconoce que los métodos de cifrado de estos dispositivos ponen en peligro la información contenida en ellos. Principalmente, este riesgo proviene de usuarios malintencionados que tienen acceso físico al dispositivo.

> [!Note]
> Microsoft trabaja junto con los fabricantes para abordar cualquier problema que se encuentre durante las pruebas o que los usuarios informen. Este artículo se actualiza cada vez que hay nueva información disponible. 

## <a name="known-devices"></a>Dispositivos conocidos

### <a name="known-devices-that-can-be-updated-to-fix-this-issue"></a>Dispositivos conocidos que se pueden actualizar para corregir este problema

Si aún no ha actualizado el dispositivo a la versión más reciente de Android, vaya a su dispositivo **configuración** aplicación y seleccione **actualización**. Estos dispositivos podrían aparecer como no conformes hasta que actualice:  

- Huawei Honor 8
- Huawei P9

### <a name="known-devices-that-currently-cannot-be-updated-to-fix-this-issue"></a>Dispositivos conocidos que actualmente no se puede actualizar para corregir este problema
Los siguientes dispositivos siempre aparecerá cifrados y no se puede usar para tener acceso a recursos de la empresa. Para obtener acceso a recursos de la empresa, debe usar un dispositivo diferente.  

- Huawei Mate 8
- Dispositivos OPPO
- Dispositivos Vivo
- Smartphones Xiaomi Mi
