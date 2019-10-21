---
title: Configuración de la aplicación Portal de empresa
titleSuffix: Microsoft Intune
description: Aprenda a aplicar personalización de marca específica de la compañía a la aplicación Portal de empresa de Intune.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 09/17/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.localizationpriority: high
ms.technology: ''
ms.assetid: dec6f258-ee1b-4824-bf66-29053051a1ae
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: 419fd15f747c8b41377f3aca94c4b96d7c4910c1
ms.sourcegitcommit: b8127c7a62d9ac4d0f768980fa1424567bb58733
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 10/15/2019
ms.locfileid: "72350003"
---
# <a name="how-to-configure-the-microsoft-intune-company-portal-app"></a>Configuración de la aplicación Portal de empresa de Microsoft Intune

[!INCLUDE [azure_portal](../includes/azure_portal.md)]

El Portal de empresa de Intune es el lugar donde los usuarios tienen acceso a los datos de la compañía y pueden realizar tareas habituales como, por ejemplo, inscribir dispositivos, instalar aplicaciones y buscar información de ayuda del departamento de TI. Además, la aplicación Portal de empresa permite al usuario acceder de forma segura a los recursos de la empresa. La aplicación Portal de empresa ofrece diversas páginas, como Inicio, Aplicaciones, Detalles de la aplicación, Dispositivos y Detalles del dispositivo. Para buscar rápidamente aplicaciones en el Portal de empresa, puede filtrar las aplicaciones en la página Aplicaciones.

> [!IMPORTANT]
> Para admitir Firebase Cloud Messaging (FCM) de Google, debe actualizar la aplicación Portal de empresa de Android a la versión más reciente. Para más información, consulte Novedades: [Actualización de la aplicación Portal de empresa de Android a la versión más reciente](../fundamentals/whats-new.md#update-your-android-company-portal-app-to-the-latest-version-).

> [!Tip]
> Al personalizar el portal de empresa, los valores de configuración se aplicarán tanto al sitio web como a las aplicaciones del portal de empresa. Tenga en cuenta que los usuarios deben tener una licencia de Intune asignada para tener acceso al sitio web Portal de empresa.

Con la personalización del Portal de empresa de Intune, podrá ofrecer una experiencia conocida y útil a los usuarios finales. Para ello, en el portal de Intune, seleccione **Aplicaciones cliente** > **Branding and customization** (Personalización de marca y personalización) y establezca la configuración necesaria.

Cuando un usuario instala una aplicación de iOS desde el Portal de empresa recibirá un mensaje. Esto sucede cuando la aplicación iOS está vinculada a la tienda de aplicaciones, a un programa de compras por volumen (VPP) o a una aplicación de línea de negocio (LOB). El mensaje permite a los usuarios aceptar la acción o permitir la administración de la aplicación. El mensaje mostrará el nombre de la empresa o, cuando este no esté disponible, se mostrará **Portal de empresa**. 

> [!Note]
> Si usa Azure Government, se ofrecen registros de aplicaciones para que el usuario final decida cómo compartirá cuando inicie el proceso para pedir ayuda para un problema. Pero si no usa Azure Government, el Portal de empresa para Windows 10 enviará registros de aplicaciones directamente a Microsoft cuando el usuario inicie el proceso de pedir ayuda para un problema. Si se envían los registros de aplicaciones a Microsoft, será más fácil solucionar los problemas. 

## <a name="company-information-and-privacy-statement"></a>Información de la empresa y declaración de privacidad de la empresa
El nombre de la empresa se muestra como título del portal de empresa. La declaración de privacidad se muestra cuando el usuario hace clic en el vínculo de privacidad.

| Nombre de campo | Longitud máxima | Más información |
|---|---|---|
|**Nombre de la empresa**| 40 | Este nombre se muestra como título del Portal de empresa y aparece como texto a lo largo de la experiencia del usuario de Intune. |
| **URL de la declaración de privacidad** |     79     | Puede especificar su propia declaración de privacidad de la empresa, que aparece cuando los usuarios hacen clic en los vínculos de privacidad del portal de empresa. Debe especificar una dirección URL válida en el formato `<https://www.contoso.com>`. |

> [!NOTE]
> De acuerdo con la directiva de Microsoft y de Apple, no vendemos a terceros los datos recopilados por nuestro servicio por ningún motivo.

## <a name="support-information"></a>Información de soporte técnico
Escriba la información de soporte técnico de la compañía para que los empleados dispongan de un contacto para preguntas relacionadas con Intune.

|Nombre de campo|Longitud máxima|Más información|
|---|---|---|
|**Nombre de contacto** | 40 | Se trata del nombre que se muestra en la página **Ayuda y soporte técnico**. |
|**Número de teléfono** | 20 | Este número de contacto se muestra en la página **Ayuda y soporte técnico** para que los empleados puedan ponerse en contacto con usted para solicitar ayuda. |
|**Dirección de correo electrónico**| 40 | Se trata de la dirección de contacto que se muestra en la página **Ayuda y soporte técnico**. Debe especificar una dirección de correo electrónico válida en el formato `alias@domainname.com`. |
|**Nombre del sitio web**| 40 | Este nombre es el nombre descriptivo que se muestra para la dirección URL del sitio web de soporte. Si especifica una dirección URL de sitio web de soporte sin nombre descriptivo, se mostrará Ir a sitio web de TI en la página **Ayuda y soporte técnico** del Portal de empresa. |
|**URL del sitio web**| 150 | Si tiene un sitio web de soporte que desea que utilicen los usuarios finales, especifique la dirección URL aquí. La dirección URL debe tener el formato `https://www.contoso.com`. Si no especifica una dirección URL, no se mostrará ningún sitio web de soporte en la página **Ayuda y soporte técnico** del Portal de empresa. |
| **Información adicional**| 120 | Se muestra en la página **Ayuda y soporte técnico**. |


## <a name="company-identity-branding-customization"></a>Personalización de la marca de identidad de la empresa
Puede personalizar su portal de empresa con su logotipo de empresa, nombre de empresa, color de tema y fondo.

### <a name="theme-color-and-logo-in-the-company-portal"></a>Color de tema y logotipo en el Portal de empresa
Aplique un color de tema al Portal de empresa. Seleccione un color estándar o escriba un código hexadecimal de seis dígitos de un color personalizado.

|Nombre de campo|Más información|
|---|---|
|**Seleccionar un color estándar o escribir un código hexadecimal de seis dígitos**| Elija **Estándar** para seleccionar visualmente un color. Elija **Personalizado** para seleccionar un color específico según un valor de código hexadecimal.|
|**Elegir color de tema**| Seleccione el color del tema que se aplicará al portal de empresa. Puede elegir un color estándar o escribir un código hexadecimal concreto. |
|**Mostrar**| Seleccione si se mostrará **Nombre y logotipo de empresa**, **Company logo only** (Solo logotipo de empresa) o **Company name only** (Solo nombre de empresa). |
|**Cargar el logotipo de empresa**|Puede cargar el logotipo de la empresa para que se muestre en el Portal de empresa. Tenga en cuenta que el color del texto se selecciona automáticamente para proporcionar el nivel más alto de contraste. Para obtener la mejor apariencia, cargue un logotipo con un fondo transparente.<p><ul><li>Tamaño máximo de imagen: 400 px x 400 px</li><li>Tamaño máximo de archivo: 750 KB</li><li>Tipo de archivo: PNG, JPG o JPEG</li></ul>|

Después de cargar el logotipo, en el área de vista previa se mostrará el logotipo de con el color del tema. Si decide mostrar el nombre de la empresa, se mostrará en blanco o negro en el Portal de empresa y se seleccionará automáticamente para proporcionar el nivel más alto de contraste según el color del tema. En el área de vista previa de la pantalla no se mostrará el nombre de la empresa. 

### <a name="logo-to-use-on-white-or-light-backgrounds"></a>Logotipo para usar en fondos claros o blancos
Elija un logotipo que encaje mejor en fondos blancos o claros.

|Nombre de campo|Más información|
|---|---|
|**Cargar el logotipo**| Esta opción está disponible si ha elegido mostrar el logotipo de la empresa. Para obtener la mejor apariencia, cargue un logotipo con un fondo transparente.<p><ul><li>Tamaño máximo de imagen: 400 px x 400 px</li><li>Tamaño máximo de archivo: 750 KB</li><li>Tipo de archivo: PNG, JPG o JPEG</li></ul>|

### <a name="brand-image-for-company-portal"></a>Imagen de marca del Portal de empresa

Muestra una imagen de marca que refleja la marca de la empresa. Después de guardar los cambios, puede elegir **Preview your settings** (Vista previa de la configuración) en el portal web de Intune, en la parte superior de la hoja para ver qué aspecto tendrá la configuración. Tenga en cuenta que solo podrá obtener una vista previa de la imagen de marca en un dispositivo iOS y no el portal web de Intune. 

|Nombre de campo|Más información|
|---|---|
|**Upload your brand image** (Cargar imagen de marca)| Esta opción permite mostrar una imagen de marca. En el Portal de empresa de iOS, muestra una imagen de fondo en la página de perfil del usuario.<p><ul><li>Ancho de imagen recomendado: Mayor que 1125 píxeles (se requiere que sea por lo menos 650 píxeles )</li><li>Tamaño máximo de imagen: 1,3 MB</li><li>Tipo de archivo: PNG, JPG o JPEG</li></ul>|

La imagen de marca adecuada puede mejorar la confianza del usuario en el Portal de empresa, ya que presenta un fuerte sentido de marca de la empresa. Estas son algunas sugerencias que puede tener en cuenta para adquirir, elegir y optimizar la imagen para el Portal de empresa. 

- Póngase en contacto con el departamento de marketing o imágenes de la empresa. Es posible que ya tengan un conjunto aprobado de imágenes de marca. Es posible que también le ayuden a optimizar las imágenes según sea necesario. 

- Considere tanto la composición horizontal como la vertical. La imagen debe tener suficiente espacio de fondo rodeando el punto focal. La imagen puede recortarse de forma diferente según el tamaño, la orientación y la plataforma del dispositivo. 

- Evite usar una imagen estándar genérica. La imagen debe reflejar la marca de la empresa y resultar familiar a los usuarios. Si no tiene una, es mejor no usar ninguna que usar una imagen genérica que no aporte ningún significado para el usuario. 

- Quite los metadatos que sean innecesarios. El archivo de imagen puede incluir metadatos, como el perfil de la cámara, la ubicación geográfica, el título, la leyenda, etc. Use una herramienta de optimización de imágenes para eliminar esta información y mantener la calidad al tiempo que cumple los límites de tamaño de archivo. 

Después de agregar o cambiar una imagen de marca en Intune, es posible que el usuario final no vea el cambio en los dispositivos iOS hasta que el Portal de empresa haya reconocido el cambio durante el inicio y se haya reiniciado luego para mostrar la imagen de marca. 

### <a name="brand-image-examples"></a>Ejemplos de imagen de marca

En la siguiente imagen se muestra un ejemplo de imagen de personalización de marca de iPad:

![Captura de pantalla de la imagen de personalización de marca de iPhone de ejemplo](./media/company-portal-app/company-portal-app-03.png)

En la siguiente imagen se muestra un ejemplo de imagen de personalización de marca de iPhone:

![Captura de pantalla de la imagen de personalización de marca de iPad de ejemplo](./media/company-portal-app/company-portal-app-02.png)

## <a name="privacy-statement-customization"></a>Personalización de la declaración de privacidad

Puede personalizar la declaración de privacidad que aparece para su organización en dispositivos iOS administrados. Este mensaje indica los elementos que su organización no puede ver o realizar en los dispositivos iOS administrados.

En **Personalización del Portal de empresa** > **Mensaje de administración de dispositivos y privacidad**, puede:

- Aceptar el **Valor predeterminado** para usar la lista tal y como se muestra, o bien
- Elegir **Personalizar** para personalizar la lista de elementos que su organización no puede ver o realizar en los dispositivos iOS administrados. Puede usar [markdown](https://daringfireball.net/projects/markdown/) para agregar viñetas, negritas, cursivas y vínculos.

## <a name="windows-company-portal-keyboard-shortcuts"></a>Métodos abreviados de teclado del Portal de empresa de Windows

Los usuarios finales pueden desencadenar acciones de navegación, aplicación y dispositivo en el Portal de empresa de Windows mediante métodos abreviados de teclado (aceleradores).

Los siguientes métodos abreviados de teclado están disponibles en la aplicación del Portal de empresa de Windows.

| Área | Descripción | Método abreviado de teclado |
|:------------------:|:--------------:|:-----------------:|
| Menú de navegación | Navegación | Alt+M |
|  | Inicio | Alt+H |
|  | Todas las aplicaciones | Alt+A |
|  | Aplicaciones instaladas | Alt+I |
|  | Enviar comentarios | Alt+F |
|  | Mi perfil | Alt+U |
|  | Configuración | Alt+T |
| Página principal, icono de dispositivo | Cambiar nombre | F2 |
|  | Quitar | Ctrl+D o Eliminar |
|  | Comprobar acceso | Ctrl+M o F9 |
| Detalles del dispositivo | Cambiar nombre | F2 |
|  | Quitar | Ctrl+D o Eliminar |
|  | Comprobar acceso | Ctrl+M o F9 |
| Detalles de la aplicación | Instalar | Ctrl+I |
| Dispositivos | Available | Ctrl+D |

Los usuarios finales también podrán ver los accesos directos disponibles en la aplicación Portal de empresa de Windows.

![Captura de pantalla de los accesos directos disponibles en el Portal de empresa de Windows](./media/company-portal-app/company-portal-app-01.png)

## <a name="user-self-service-device-actions-from-the-company-portal"></a>Acciones de dispositivo de autoservicio de usuario desde el Portal de empresa

Los usuarios pueden realizar acciones en sus dispositivos locales o remotos a través del sitio web o la aplicación Portal de empresa. Las acciones que puede realizar un usuario varían según la plataforma y la configuración del dispositivo. En todos los casos, las acciones de dispositivo remoto solo las puede realizar el usuario primario del dispositivo.
- **Retirar**: quita el dispositivo de la administración de Intune. En el sitio web o la aplicación Portal de empresa, esto se muestra como **Quitar**.
- **Borrar**: esta acción inicia un restablecimiento del dispositivo. En el sitio web Portal de empresa, se muestra como **Restablecer** o **Restablecimiento de la configuración de fábrica** en la aplicación Portal de empresa de iOS.
- **Cambiar nombre**: esta acción cambia el nombre del dispositivo que el usuario puede ver en el Portal de empresa. No cambia el nombre del dispositivo local, solo la lista del Portal de empresa.
- **Sincronizar**: esta acción inicia una inserción en el repositorio del dispositivo en el servicio Intune. Esto se muestra como **Comprobar estado** en el Portal de empresa.
- **Bloqueo remoto**: bloquea el dispositivo y requiere un PIN para desbloquearlo.
- **Restablecer código de acceso**: esta acción se usa para restablecer el código de acceso del dispositivo. En los dispositivos iOS, se quitará el código de acceso y se solicitará al usuario final que especifique un nuevo código en la configuración. En los dispositivos Android compatibles, Intune genera un nuevo código de acceso que se muestra temporalmente en el Portal de empresa.
- **Recuperación de clave**: esta acción se utiliza para recuperar una clave de recuperación personal para dispositivos macOS cifrados desde el sitio web Portal de empresa. 

### <a name="self-service-actions"></a>Acciones de autoservicio

Algunas plataformas y configuraciones no realizar permiten acciones de autoservicio en el dispositivo. En la tabla siguiente se ofrecen más detalles sobre las acciones de autoservicio:

|     Plataforma    |    Retirar    |    Eliminación de datos     |    Cambiar nombre<sup>(4)</sup>    |    Sincronización    |    Bloqueo remoto    |    Restablecer el código de acceso    |    Recuperación de clave    |
|------------------------|--------------------|--------------------|-----------------|-----------------|--------------------------|--------------------------|--------------------|
|    Windows 10<sup>(3)</sup>    |    Disponible<sup>(1)</sup>    |    Available    |    Available    |    Available    |    Solo en Windows Phone    |    Solo en Windows Phone    |    N/D    |
|    iOS<sup>(3)</sup>    |    Available    |    Available    |    Available    |    Available    |    Available    |    Available    |    N/D    |
|    MacOS<sup>(3)</sup><sup>(5)</sup>    |    Available    |    N/D    |    Available    |    Available    |    Available    |    N/D    |    Disponible<sup>(2)</sup>    |
|    Android<sup>(3)</sup>    |    Disponible<sup>(7)</sup>    |    Disponible<sup>(7)</sup>    |    Available    |    Available    |    Available    |    Disponible<sup>(6)</sup>    |    N/D    |


<sup>(1) </sup> La función Retirar siempre está bloqueada en dispositivos Windows unidos a Azure AD.<br>
<sup>(2)</sup> La recuperación de clave personal para MacOS solo está disponible a través del sitio web Portal de empresa.<br> 
<sup>(3)</sup> Todas las acciones remotas se deshabilitan si se usa una inscripción del administrador de inscripción de dispositivos.<br>
<sup>(4) </sup> Rename solo cambia el nombre del dispositivo en la aplicación o el sitio web Portal de empresa, no en el dispositivo.<br>
<sup>(5) </sup> el borrado remoto no está disponible en los dispositivos MacOS.<br>
<sup>(6)</sup> En algunas configuraciones de Android Enterprise no se admite el restablecimiento del código de acceso. Para más información, consulte [Restablecimiento o eliminación del código de acceso de un dispositivo en Intune](../remote-actions/device-passcode-reset.md).<br>
<sup>(7)</sup> Las funciones Retirar y Borrar no están disponibles en escenarios de Propietario del dispositivo Android Enterprise (COPE, COBO, COSU).<br> 

## <a name="next-steps"></a>Pasos siguientes

- [Adición manual de la aplicación Portal de empresa para Windows 10 con Microsoft Intune](company-portal-app.md)
