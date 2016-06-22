---
# required metadata

title: Implementar aplicaciones | Microsoft Intune
description:
keywords:
author: robstackmsft
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: ad5ea85c-aa2e-4110-a184-172cd0b8f270

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: mghadial
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Implementar aplicaciones con Microsoft Intune

En este tema se explican algunos de los conceptos que es preciso conocer para empezar a implementar aplicaciones con Microsoft Intune.

## El editor de software de Intune
El **editor de software de Microsoft Intune** se inicia al agregar o modificar aplicaciones en la consola de administrador de Microsoft Intune. En este editor se selecciona y configura un tipo de instalador de software que permitirá cargar aplicaciones (programas si son equipos o aplicaciones si son dispositivos móviles) para almacenarlas en el almacenamiento en nube de Intune, o bien vincularlas a una tienda en línea o una aplicación web.

### Requisitos
Antes de empezar a usar el editor de software de Microsoft Intune, es necesario instalar la versión completa de [Microsoft .NET Framework 4.0](https://www.microsoft.com/download/details.aspx?id=17851). Tras instalarlo, puede que tenga que reiniciar el equipo para que el editor de software se abra correctamente.

## Espacio de almacenamiento en nube
Todas las aplicaciones que implemente mediante el tipo de instalación del instalador de software se deben empaquetar y cargar en el almacenamiento en nube de Microsoft Intune. Una suscripción de prueba de Intune incluye 2 gigabytes (GB) de almacenamiento en nube destinados a almacenar actualizaciones y aplicaciones administradas. Una suscripción de pago incluye 20 GB y la posibilidad de adquirir más almacenamiento.

En el nodo **Uso del almacenamiento** del área de trabajo **Administración** puede ver la cantidad de espacio que está usando y adquirir más almacenamiento.

Las siguientes reglas rigen la compra de más almacenamiento en nube para Intune:

-   Debe tener una suscripción de pago activa para poder adquirir almacenamiento adicional.

-   Solo los administradores de facturación o los administradores globales de su servicio de Microsoft Online pueden adquirir almacenamiento adicional a través del portal de administración de Office 365. Para administrar, agregar o eliminar estos administradores, debe ser administrador global e iniciar sesión en el portal de administración de Office 365.

-   Si es un cliente de licencias por volumen que ha adquirido Intune o el complemento de Microsoft Intune a través de un Contrato Enterprise, póngase en contacto con su gestor de cuentas de Microsoft o su partner de Microsoft para obtener información relativa a los precios y para adquirir más almacenamiento.

#### Requisitos de espacio de almacenamiento en nube

-   Todos los archivos asociados a una aplicación deben estar en la misma ubicación y estar accesibles para Intune.

-   El tamaño máximo de archivo de cualquier archivo que se cargue es de 2 GB.

-   Para cargar archivos, se necesita una velocidad de Internet mínima de 768 Kbps.

## Acciones de implementación de aplicaciones
Al implementar aplicaciones, puede elegir una de las siguientes acciones de implementación:

-   **Instalación requerida:** la aplicación se instala en el dispositivo sin intervención por parte del usuario final.

    > [!TIP] En los dispositivos iOS que no estén en modo supervisado y en todos los dispositivos Android, el usuario debe aceptar la oferta de la aplicación antes de instalarla.
    >
    > Ya no podrá crear nuevas implementaciones de aplicaciones para dispositivos que ejecuten sistemas operativos anteriores a iOS 7.1. Cualquier implementación de aplicaciones que se realice en dispositivos que ejecuten un sistema operativo anterior a iOS 7.1 seguirá funcionando e Intune se encargará de administrarlas.
    > 
    >  Si un usuario final desinstala una aplicación que ha implementado como una instalación necesaria, Intune volverá a instalar automáticamente la aplicación tras el siguiente ciclo de inventario, que normalmente se produce cada 7 días.

-   **Instalación disponible:** la aplicación aparece en el portal de empresa y los usuarios finales pueden solicitar instalarla.

-   **Desinstalar** : la aplicación se desinstala del dispositivo.

-   **No aplicable** : la aplicación no aparece en el portal de empresa y no está instalada en los dispositivos.

#### Saber qué acciones de implementación están disponibles para cada tipo de instalador

|Tipo de instalador|Instalación requerida|Instalación disponible|Desinstalar|No aplicable|
|------------------|--------------------|---------------------|-------------|------------------|
|Paquete de aplicación de Windows (implementado para un grupo de usuarios)|Sí|Sí|Sí|Sí|
|Paquete de aplicación de Windows (se implementa en un grupo de dispositivos)|Sí|No|Sí|Sí|
|Paquete de aplicación para dispositivos móviles (se implementa para un grupo de usuarios)|Sí|Sí|Sí|Sí|
|Paquete de aplicación para dispositivos móviles (se implementa para un grupo de dispositivos)|Sí|No|Sí|Sí|
|Windows Installer (se implementa para un grupo de usuarios)|No|Sí|No|Sí|
|Windows Installer (se implementa para un grupo de dispositivos)|Sí|No|Sí|Sí|
|Vínculo externo (se implementa para un grupo de usuarios)|No|Sí|No|Sí|
|Vínculo externo (se implementa para un grupo de dispositivos)|No|No|No|No|
|Aplicación iOS administrada desde la tienda de aplicaciones (se implementa para un grupo de usuarios)|Sí|Sí|Sí|Sí|
|Aplicación iOS administrada desde la tienda de aplicaciones (se implementa para un grupo de dispositivos)|Sí|No|Sí|Sí|
> [!TIP] Si, al implementar aplicaciones, selecciona grupos tanto de usuarios como de dispositivos, la aplicación solo se puede implementar como una **instalación disponible**.

## Conflictos de implementación
Cuando un dispositivo recibe dos implementaciones, con la misma acción de implementación, se aplican las siguientes reglas:

-   Las implementaciones para un grupo de dispositivos tienen prioridad sobre las implementaciones para un grupo de usuarios. Sin embargo, si una aplicación se implementa para un grupo de usuarios con la acción de implementación **Disponible** y la misma aplicación se implementa también para un grupo de dispositivos con la acción de implementación **No aplicable**, la aplicación estará disponible en el portal de la compañía para que los usuarios la instalen.

-   El intento del administrador de TI tiene prioridad sobre la del usuario final.

-   Una acción de instalación tiene prioridad sobre una de desinstalación.

-   Si un dispositivo recibe una instalación requerida y una instalación disponible, ambas acciones se combinan (la aplicación es necesaria y está disponible).


## Pasos siguientes

Obtenga información sobre cómo [implementar aplicaciones en Microsoft Intune](deploy-apps-in-microsoft-intune.md).

<!--HONumber=Jun16_HO2-->


