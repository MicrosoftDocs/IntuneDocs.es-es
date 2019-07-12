---
title: Configuración de la aplicación Managed Home Screen de Microsoft
titleSuffix: Microsoft Intune
description: Obtenga información sobre cómo configurar la aplicación Managed Home Screen de Microsoft.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 05/16/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: 865c7f03-f525-4dfa-b3a8-d088a9106502
ms.reviewer: chmaguir
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: c3955710dfbe57023533f737f0ae69df80f863e6
ms.sourcegitcommit: 1dc9d4e1d906fab3fc46b291c67545cfa2231660
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/10/2019
ms.locfileid: "67735701"
---
# <a name="configure-the-microsoft-managed-home-screen-app-for-android-enterprise"></a>Configuración de la aplicación Managed Home Screen de Microsoft para Android Enterprise

Managed Home Screen es la aplicación que se usa para dispositivos Android Enterprise corporativos dedicados inscritos mediante Intune y que se ejecutan en modo de pantalla completa con varias aplicaciones. Para estos dispositivos, Managed Home Screen actúa como el iniciador de otras aplicaciones aprobadas para que se ejecuten sobre ella. Managed Home Screen proporciona a los administradores de TI la capacidad de personalizar sus dispositivos y de restringir las funcionalidades a las que puede acceder el usuario final. 

## <a name="when-to-configure-the-microsoft-managed-home-screen-app"></a>Cuándo configurar la aplicación Managed Home Screen de Microsoft

Normalmente, si las opciones están disponibles a través de Configuración del dispositivo, configúrelas ahí. De esta forma ahorra tiempo, minimiza los errores y obtendrá una mejor experiencia de soporte técnico de Intune. Sin embargo, actualmente algunas de las opciones de Managed Home Screen solo están disponibles a través de la hoja **Directivas de configuración de aplicaciones** de la consola de Intune. Use este documento para obtener información sobre cómo configurar las distintas opciones mediante el Diseñador de configuraciones o un script JSON. 

> [!NOTE]
> Actualmente es posible, y recomendable, establecer las aplicaciones permitidas y los vínculos web anclados a través de **Aplicaciones cliente** y **Configuración del dispositivo**. Para obtener la lista completa de opciones disponibles en **Configuración del dispositivo** que afectan a Managed Home Screen, vea [ Configuración del dispositivo dedicado](device-restrictions-android-for-work.md#dedicated-device-settings).  

En primer lugar, vaya a la consola de Intune en Azure Portal y seleccione **Aplicaciones cliente** > **Directivas de configuración de aplicaciones**. Agregue una directiva de configuración para **Dispositivos administrados** que se ejecutan en **Android** y elija **Managed Home Screen** como la aplicación asociada. Haga clic en **Opciones de configuración** para configurar las distintas opciones disponibles de Managed Home Screen. 

## <a name="choosing-a-configuration-settings-format"></a>Selección de un formato de opciones de configuración

Puede usar dos métodos para definir opciones de configuración para Managed Home Screen:

- El **Diseñador de configuraciones** permite configurar las opciones con una interfaz de usuario fácil de usar que le permite activar o desactivar características y establecer valores. En este método, hay algunas claves de configuración deshabilitadas con el tipo de valor `BundleArray`. Estas claves de configuración solo se pueden configurar mediante la especificación de datos JSON. 
- Los **datos JSON** permiten definir todas las claves de configuración posibles mediante un script JSON. 

Si agrega propiedades con el Diseñador de configuraciones, las puede convertir de forma automática en JSON si selecciona **Especificar datos JSON** en la lista desplegable **Formato de opciones de configuración**.

![Captura de pantalla de las opciones de Formato de opciones de configuración](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_01.png)

## <a name="using-configuration-designer"></a>Uso del Diseñador de configuraciones

El Diseñador de configuraciones le permite seleccionar opciones preestablecidas y sus valores asociados. 

![Captura de pantalla de las opciones de configuración agregadas](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_02.png)

En la tabla siguiente se enumeran las claves de configuración disponibles de Managed Home Screen, los tipos de valor, los valores predeterminados y sus descripciones. La descripción proporciona el comportamiento esperado del dispositivo según los valores seleccionados. En la tabla no se muestran las claves de configuración deshabilitadas en el Diseñador de configuraciones.

| Clave de configuración | Tipo de valor | Valor predeterminado | Descripción |
|---------------------------------------------------------------------------------------------------------------------------|-------------|------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Definir tamaño de la cuadrícula | cadena | Automático | Permite establecer el tamaño de la cuadrícula para las aplicaciones que se van a colocar en la pantalla principal administrada. Puede establecer el número de filas y columnas de la aplicación para definir el tamaño de la cuadrícula en el formato siguiente, `columns;rows`. Si define el tamaño de la cuadrícula, el número máximo de aplicaciones que se mostrarán en una fila de la pantalla principal será el número de filas que establezca, y el número máximo de aplicaciones que se mostrarán en una columna de la pantalla principal será el número de columnas que establezca. |
| Habilitar el encabezado de pantalla | bool | TRUE | Habilita el encabezado superior para las distintas vistas que ofrece la pantalla principal administrada, como la fuente o las tarjetas de fuente. Si habilita esta opción, los usuarios del dispositivo verán el encabezado. |
| Habilitar la barra de estado del dispositivo | bool | TRUE | Habilita la barra de estado de la pantalla principal (la barra superior en la que se muestran las conexiones actuales como Wi-Fi, etc.). Si habilita esta clave de configuración, el usuario final podrá ver en la barra de estado los iconos que representan las conexiones y las aplicaciones activas. |
| Habilitar la señal de notificaciones | bool | FALSE | Permite la señal de notificación para los iconos de aplicación que muestra el número de notificaciones nuevas en la aplicación. Si habilita esta opción, los usuarios finales verán señales de notificación en las aplicaciones que tienen notificaciones sin leer. Si mantiene deshabilitada esta configuración clave, el usuario final no verá ninguna notificación señalada para las aplicaciones que podrían tener notificaciones sin leer. |
| Bloquear la pantalla de inicio | bool | TRUE | Impide al usuario final mover los iconos de las aplicaciones en la pantalla principal. Si habilita esta clave de configuración, se bloquearán los iconos de las aplicaciones en la pantalla principal y el usuario final no podrá arrastrarlos y colocarlos en otras posiciones de la cuadrícula de la pantalla principal. Si se establece en `false`, los usuarios finales podrán mover los iconos de las aplicaciones y los vínculos web en Managed Home Screen.  |
| Establecer el fondo de pantalla del dispositivo | cadena | Default | Le permite establecer el fondo de pantalla que elija si escribe la dirección URL de la imagen que quiera establecer como fondo de pantalla. |
| Establecer el tamaño del icono de la aplicación | integer | 2 | Le permite establecer el tamaño de icono para las aplicaciones que se muestran en la pantalla principal. Puede elegir los valores siguientes en esta configuración para diferentes tamaños: 0 (el más pequeño), 1 (pequeño), 2 (estándar), 3 (grande) y 4 (el más grande). |
| Establecer el icono de la carpeta de aplicación | integer | 0 | Le permite definir la apariencia de las carpetas de aplicación en la pantalla principal. Puede elegir la apariencia entre los valores siguientes: Dark Square(0); Dark Circle(1); Light Square(2); Light Circle(3). |
| Habilitar gestos | bool | FALSE | Habilita la capacidad del usuario final de asignar acciones a diferentes gestos, como deslizarse hacia arriba o hacia abajo. Si deshabilita esta clave de configuración, los usuarios finales solo podrán deslizar a la derecha si hay una segunda página y volver a la página principal. |
| Habilitar desplazamiento vertical | bool | FALSE | Habilita el desplazamiento vertical en la pantalla principal administrada. Si habilita esta clave de configuración, el usuario final solo podrá navegar verticalmente a otras páginas, en lugar de deslizar horizontalmente. |
| Establecer tema de la pantalla principal | cadena | Theme.Light.Blue | Le permite elegir el tema de la pantalla principal a partir de un conjunto predefinido de temas con colores diferentes. Puede elegir los temas siguientes si escribe el valor de cadena en el formato siguiente.   Theme.Light.Green. Donde Light se puede reemplazar por Dark para un tema oscuro y Green (verde) se puede reemplazar por Blue, Yellow, Pink, Red, Orange y Purple (azul, amarillo, rosa, rojo, naranja y púrpura). |
| Habilitar acoplamiento | bool | FALSE | Habilita la sección de acoplamiento de aplicaciones en la parte inferior de la pantalla principal en la que se muestran las aplicaciones persistentes y el punto de entrada de todas las aplicaciones instaladas. Si habilita esta clave de configuración, el usuario final podrá acceder a las aplicaciones acopladas y también a la sección de todas las aplicaciones para ir a la lista de todas las aplicaciones instaladas en los dispositivos, con independencia de que se hayan agregado o no a la lista de permitidas. |
| Establecer la orientación de la pantalla | integer | 1 | Le permite establecer la orientación de la pantalla principal en modo vertical, horizontal o permitir el giro automático. Puede establecer la orientación si escribe los valores 1 (para el modo vertical), 2 (para el modo horizontal), 3 (para Girar automáticamente). |
| Habilitar la fuente de la pantalla principal | bool | FALSE | Habilita la fuente de la pantalla principal, que se puede ver si se desliza hacia la izquierda. Esta fuente muestra otro tipo de contenido, como noticias, el calendario, las aplicaciones de uso frecuente, la tarjeta del asistente de voz de Cortana, etc. Si lo habilita, el usuario final podrá deslizar hacia la izquierda en la pantalla principal para ir a la fuente. |
| Habilitar el modo de introducción | bool | FALSE | Permite a los usuarios finales agregar o quitar otras páginas en la pantalla principal a las que se puede acceder si se desliza el dedo hacia la derecha desde la pantalla predeterminada. Si habilita esta opción, el usuario final podrá agregar páginas a la derecha de la página predeterminada de la pantalla principal, también podrá cambiar la página predeterminada y acceder a la configuración de Managed Home Screen. |
| Habilitar la telemetría de dispositivo | bool | FALSE | Habilita toda la telemetría que se captura para la pantalla principal administrada. Si habilita esta opción, Microsoft podrá capturar la telemetría de uso del dispositivo, como el número de veces que se inicia una aplicación determinada en este dispositivo. |
| Establecer aplicaciones permitidas | bundleArray | FALSE | Le permite definir el conjunto de aplicaciones visibles en la pantalla principal de entre las instaladas en el dispositivo. Para definir las aplicaciones, escriba el nombre del paquete de aplicación de las aplicaciones que le gustaría hacer visibles; por ejemplo, com.microsoft.emmx hará que se pueda acceder a la configuración desde la pantalla principal. Las aplicaciones que incluya en la lista de permitidas en esta sección ya deben estar instaladas en el dispositivo para que se vean en la pantalla principal. |
| Establecer vínculos web anclados | bundleArray | FALSE | Le permite anclar sitios web como iconos de inicio rápido en la pantalla principal. Con esta configuración, puede definir la dirección URL y agregarla a la pantalla principal para que el usuario final inicie el explorador con un solo toque. |
| Habilitar la barra de búsqueda | bool | FALSE | Habilita la barra de búsqueda en la pantalla principal. Si habilita esta opción, los usuarios del dispositivo verán la barra de búsqueda en la pantalla principal, donde podrán escribir todo lo que quieran buscar en la Web. |
| Deshabilitar la aplicación de configuración | bool | FALSE | Deshabilita la página de configuración de Managed Home Screen. Si deshabilita esta opción, el usuario final del dispositivo no podrá acceder a la configuración de Managed Home Screen. |
| Habilitar protector de pantalla | bool | FALSE | Para habilitar o no el modo de protector de pantalla. Si se establece en true, puede configurar **screen_saver_image**, **screen_saver_show_time**, **inactive_time_to_show_screen_saver** y **media_detect_screen_saver**. |
| Imagen del protector de pantalla | cadena |   | Establezca la dirección URL de la imagen del protector de pantalla. Si no se establece ninguna dirección URL, los dispositivos mostrarán la imagen del protector de pantalla predeterminada cuando se active el protector de pantalla. La imagen predeterminada muestra el icono de la aplicación Managed Home Screen.  |
| Mostrar hora del protector de pantalla | integer | 0 | Ofrece la opción de establecer la cantidad de tiempo en segundos que el dispositivo mostrará el protector de pantalla durante el modo de protector de pantalla. Si se establece en 0, el protector de pantalla se mostrará en modo de protector de pantalla indefinidamente hasta que el dispositivo se active.  |
| Tiempo de inactividad para habilitar el protector de pantalla | integer | 30 | El número de segundos que el dispositivo está inactivo antes de desencadenar el protector de pantalla. Si se establece en 0, el dispositivo nunca pasará al modo de protector de pantalla. |
| Detectar medios antes de mostrar el protector de pantalla | bool | TRUE | Elija si en la pantalla del dispositivo se debe mostrar el protector de pantalla cuando se reproduce audio o vídeo en el dispositivo. Si se establece en true, el dispositivo no reproducirá audio o vídeo, con independencia del valor de **inactive_time_to_show_scree_saver**. Si se establece en false, en la pantalla del dispositivo se mostrará el protector de pantalla según el valor establecido en **inactive_time_to_show_screen_saver**.   |
| Habilitar botón de inicio virtual | bool | FALSE | Establezca esta opción en `True` para permitir que el usuario final tenga acceso a un botón de inicio de Managed Home Screen que lo devolverá a la pantalla de la aplicación desde la tarea actual en la que se encuentre.  |
| Tipo de botón de inicio virtual | cadena | Swipe_up | Use **swipe_up** para acceder al botón de inicio con un gesto de deslizar rápidamente hacia arriba. Use **float** para acceder a un botón de inicio fijo y persistente que el usuario final pueda mover por la pantalla. |
| Barra indicadora de la batería y la intensidad de la señal | bool | True  | Al establecer esta opción en `True` se muestra la barra indicadora de la batería y la intensidad de la señal. |
| Contraseña para salir del modo de bloqueo de tareas | cadena |   | Escriba un código de 4-6 dígitos para salir temporalmente del modo de bloqueo de tareas para solucionar problemas. |
| Mostrar configuración de Wi-Fi | bool | FALSE | Al establecer esta opción en `True` se permite al usuario final activar o desactivar la conexión Wi-Fi, o bien conectarse a otras redes Wi-Fi.  |
| Mostrar la configuración de Bluetooth | bool | FALSE | Al establecer esta opción en `True` se permite al usuario final activar o desactivar Bluetooth, o bien conectarse a otros dispositivos compatibles con Bluetooth.   |
| Las aplicaciones de la carpeta se ordenan por nombre. | bool | TRUE | Si selecciona `False`, los elementos de una carpeta aparecerán en el orden en que se hayan especificado. En caso contrario, aparecerán en la carpeta ordenados alfabéticamente.   |
| Orden de la aplicación habilitada | bool | FALSE | Si selecciona `True`, podrá establecer el orden de las aplicaciones, los vínculos web y las carpetas en la aplicación Managed Home Screen. Una vez habilitada, establezca el orden con **app_order**. El usuario final activará o desactivará Bluetooth y se conectará a los distintos dispositivos compatibles con Bluetooth.   |
| Orden de la aplicación | bundleArray | FALSE | Permite especificar el orden de las aplicaciones, los vínculos web y las carpetas en la aplicación Managed Home Screen. Para usar esta configuración, **Bloquear pantalla de inicio** debe estar habilitada, **Definir tamaño de la cuadrícula** deben estar definido y **Orden de la aplicación habilitada** debe establecerse en `True`.   |

## <a name="enter-json-data"></a>Especificar datos JSON

Especifique datos JSON para configurar todas las opciones disponibles para Managed Home Screen, así como las opciones deshabilitadas en el **Diseñador de configuraciones**.

![Captura de pantalla de los datos JSON agregados](./media/app-configuration-managed-home-screen-app/app-configuration-managed-home-screen-app_03.png)

Además de la lista de opciones configurables enumeradas en la tabla del **Diseñador de configuraciones** (anterior), en la tabla siguiente se proporcionan las claves de configuración que solo se pueden configurar a través de datos JSON.

|    Clave de configuración    |    Tipo de valor    |    Valor predeterminado    |    Descripción    |
|-------------------------------------------------|--------------------|-------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
|    Establecer aplicaciones permitidas    |    bundleArray    | <img alt="JSON - Example 1" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson01.png" width="300"> |    Le permite definir el conjunto de aplicaciones visibles en la pantalla principal de entre las instaladas en el dispositivo. Para definir las aplicaciones, escriba el nombre del paquete de aplicación de las aplicaciones que le gustaría hacer visibles; por ejemplo, com.android.settings hará que se pueda acceder a la configuración desde la pantalla principal. Las aplicaciones que incluya en la lista de permitidas en esta sección ya deben estar instaladas en el dispositivo para que se vean en la pantalla principal.    |
|    Establecer vínculos web anclados    |    bundleArray    | <img alt="JSON - Example 2" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson02.png" width="300"> |    Le permite anclar sitios web como iconos de inicio rápido en la pantalla principal. Con esta configuración, puede definir la dirección URL y agregarla a la pantalla principal para que el usuario final inicie el explorador con un solo toque.    |
|    Crear carpeta administrada para agrupar aplicaciones    |    bundleArray    | <img alt="JSON - Example 3" src="./media/app-configuration-managed-home-screen-app/defaultvaluejson03.png" width="300"> |    Le permite crear carpetas y asignarles un nombre, y agrupar aplicaciones dentro de estas carpetas. Los usuarios finales no podrán mover las carpetas, cambiarlas de nombre ni mover las aplicaciones dentro de las carpetas.   Las carpetas aparecerán en el orden en el que se hayan creado, y las aplicaciones dentro de las carpetas aparecerán en orden alfabético.         Nota: Todas las aplicaciones que quiera agrupar en carpetas se deben asignar como requeridas en el dispositivo y se deben haber agregado a Managed Home Screen.     |

Este es un ejemplo de script JSON con todas las claves de configuración disponibles incluidas:

```json
{
    "kind": "androidenterprise#managedConfiguration",
    "productId": "com.microsoft.launcher.enterprise",
    "managedProperty": [
        {
            "key": "keep_page_header",
            "valueBool": true
        },
        {
            "key": "keep_status_bar",
            "valueBool": true
        },
        {
            "key": "show_notification_badge",
            "valueBool": false
        },
        {
            "key": "lock_home_screen",
            "valueBool": true
        },
        {
            "key": "wallpaper",
            "valueString": "default"
        },
        {
            "key": "icon_size",
            "valueInteger": 2
        },
        {
            "key": "app_folder_icon",
            "valueInteger": 0
        },
        {
            "key": "gesture_on",
            "valueBool": false
        },
        {
            "key": "vertical_scrolling",
            "valueBool": false
        },
        {
            "key": "theme",
            "valueString": "Theme.Light.Blue"
        },
        {
            "key": "dock_enable",
            "valueBool": false
        },
        {
            "key": "screen_orientation",
            "valueInteger": 1
        },
        {
            "key": "feed_enable",
            "valueBool": false
        },
        {
            "key": "allow_overview_mode",
            "valueBool": false
        },
        {
            "key": "enable_telemetry",
            "valueBool": false
        },
        {
            "key": "applications",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": “app package name here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "weblinks",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "link",
                            "valueString": “link here”
                        },
                        {
                            "key": "label",
                            "valueString": “weblink label here”
                        }
                    ]
                }
            ]
        },
        {
            "key": "search_bar",
            "valueBool": false
        },
        {
            "key": "hide_settings",
            "valueBool": false
        },
        {
            "key": "show_virtual_home",
            "valueBool": false
        },
        {
            "key": "virtual_home_type",
            "valueString": "swipe_up"
        },
        {
            "key": "show_virtual_status_bar",
            "valueBool": true
        },
        {
            "key": "exit_lock_task_mode_code",
            "valueString": ""
        },
        {
            "key": "show_wifi_setting",
            "valueBool": false
        },
        {
            "key": "show_bluetooth_setting",
            "valueBool": false
        },
        {
            "key": "grid_size",
            "valueString": "4;5"
        },
        {
            "key": "app_order_enabled",
            "valueBool": true
        },
        {
            "key": "apps_in_folder_ordered_by_name",
            "valueBool": true
        },
        {
            "key": "app_orders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.Microsoft.emmx"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 1
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Work"
                        },
                        {
                            "key": "type",
                            "valueString": "managed_folder"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 2
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "package",
                            "valueString": "com.microsoft.launcher.enterprise"
                        },
                        {
                            "key": "type",
                            "valueString": "application"
                        },
                        {
                            "key": "class",
                            "valueString": "com.microsoft.launcher.launcher"
                        },
                        {
                            "key": "container",
                            "valueInteger": 1
                        },
                        {
                            "key": "position",
                            "valueInteger": 3
                        }
                    ]
                }
            ]
        },
        {
            "key": "managed_folders",
            "valueBundleArray": [
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Folder name here"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.emmx"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.bing"
                                        }
                                    ]
                                },
                                {
                                    "managedProperty": [
                                        {
                                            "key": "link",
                                            "valueString": "https://microsoft.com/"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                },
                {
                    "managedProperty": [
                        {
                            "key": "folder_name",
                            "valueString": "Example folder name 2"
                        },
                        {
                            "key": "applications",
                            "valueBundleArray": [
                                {
                                    "managedProperty": [
                                        {
                                            "key": "package",
                                            "valueString": "com.microsoft.office.word"
                                        }
                                    ]
                                }
                            ]
                        }
                    ]
                }
            ]
        }
    ]
}
```

## <a name="next-steps"></a>Pasos siguientes

- Para más información sobre los dispositivos dedicados de Android Enterprise, vea [Configuración de la inscripción en Intune de dispositivos dedicados de Android Enterprise](android-kiosk-enroll.md).
