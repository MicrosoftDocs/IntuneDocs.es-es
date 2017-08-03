---
title: "TÍTULO DEL ARTÍCULO | NOMBRE DEL SERVICIO"
description: 
keywords: 
author: GITHUB USERNAME
manager: ALIAS
ms.date: 04/28/2016
ms.topic: article
ms.prod: 
ms.service: 
ms.technology: 
ms.assetid: GET ONE FROM guidgenerator.com
ms.openlocfilehash: 68090a038cec49009b6bd0ce0515a075f62483b8
ms.sourcegitcommit: 02fb1274ae0dc11288f8bd9cd4799af144b8feae
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 07/13/2017
---
# <a name="metadata-and-markdown-template"></a>Metadatos y plantilla Markdown

Esta plantilla docs.ms contiene ejemplos de sintaxis Markdown, así como instrucciones sobre cómo definir los metadatos. Está disponible en el directorio raíz de cada repositorio EM Pilot (por ejemplo, ~/Azure-RMSDocs-pr /template.md) y está pensada para leerse como un archivo Markdown, aunque puede consultar [la versión publicada](https://stage.docs.microsoft.com/en-us/rights-management/template) para ver cómo se visualizan los ejemplos de Markdown.

Al crear un archivo Markdown, debe copiar la plantilla en un archivo nuevo, rellenar los metadatos como se indica aquí, definir el encabezado H1 encima del título del artículo y eliminar el contenido. 


## <a name="metadata"></a>Metadatos 

El bloque de metadatos completo está arriba, dividido en campos obligatorios y campos opcionales. Consulte la [hoja de referencia de metadatos OPS](https://ppe.msdn.microsoft.com/en-us/ce-csi-docs/ops/ops-onboarding/managing-content/content-meta-data) para obtener más detalles. Algunas notas fundamentales:

- **Debe** existir un espacio entre los dos puntos (:) y el valor de un elemento de metadatos.
- Si un elemento de metadatos opcional no tiene un valor, comente el elemento con una almohadilla (#). No lo deje vacío ni use "na". Si va a agregar un valor a un elemento que tiene un comentario, procure quitar la almohadilla (#).
- Los dos puntos en un valor (por ejemplo, un título) interrumpen el analizador de metadatos. En su lugar, use la codificación HTML &#58; (por ejemplo, "title: Azure Rights Management&#58; conceptos básicos | Azure RMS").
- **title**: este título aparecerá en los resultados del motor de búsqueda. El título debe finalizar con un carácter de línea vertical (|) seguido del nombre del servicio (vea el ejemplo de arriba). No es necesario (de hecho, probablemente no sea obligatorio) que el título sea idéntico al título del encabezado H1. Debe tener aproximadamente 65 caracteres (incluyendo la parte | NOMBRE DEL SERVICIO).
- **author**, **manager**, **reviewer**: el campo author debe contener el **nombre de usuario de Github** del creador, no el alias.  Los campos "manager" y "reviewer", por su parte, deben contener alias. ms.reviewer especifica el nombre del PM asociado con el artículo o el servicio.
- **ms.assetid**: este es el GUID del artículo desde CAPS. Al crear un archivo Markdown, obtenga un GUID de [https://www.guidgenerator.com](https://www.guidgenerator.com). 
- **ms.prod**, **ms.service**, **ms.technology**, **ms.devlang**, **ms.topic**, **ms.tgt_pltfrm**: [aquí](https://microsoft.sharepoint.com/teams/STBCSI/Insights/_layouts/15/WopiFrame.aspx?sourcedoc=%7b7A321BF1-0611-4184-84DA-A0E964C435FA%7d&file=WEDCS_MasterList_CSIValues.xlsx&action=default) se pueden encontrar posibles valores para estos elementos.

## <a name="basic-markdown-and-gfm"></a>Markdown básico y GFM

Se admite todo el Markdown básico y Markdown de estilo Github (GFM). Para más información al respecto, vea:

- [Sintaxis de Markdown de línea base](https://daringfireball.net/projects/markdown/syntax)
- [Documentación de Markdown de estilo Github (GFM)](https://guides.github.com/features/mastering-markdown)

## <a name="headings"></a>Encabezados

Arriba encontrará ejemplos de títulos de primer y segundo nivel. 

Solo **debe** haber un encabezado de primer nivel en el tema, que se mostrará como el título de página.  

Los encabezados de segundo nivel generarán la tabla de contenido de la página que aparece en la sección "En este artículo" debajo del título de página.

### <a name="third-level-heading"></a>Encabezado de tercer nivel
#### <a name="fourth-level-heading"></a>Encabezado de cuarto nivel
##### <a name="fifth-level-heading"></a>Encabezado de quinto nivel
###### <a name="sixth-level-heading"></a>Encabezado de sexto nivel

## <a name="text-styling"></a>Estilo del texto

*Cursiva* 

**Negrita** 

~~Tachado~~



## <a name="links"></a>Links

Para vincular a un archivo Markdown en el mismo repositorio, use [vínculos relativos](https://www.w3.org/TR/WD-html40-970917/htmlweb.html#h-5.1.2). 

- Ejemplo: [¿Qué es Azure Rights Management?](./understand-explore/what-is-azure-rights-management.md)

Para vincular a un encabezado en el mismo archivo Markdown, vea el origen del artículo publicado, busque el identificador del encabezado (por ejemplo, `id="blockquote"`) y vincule usando la estructura # + identificador (por ejemplo, `#blockquote`).

- Ejemplo: [Blockquotes](#blockquote)

Para vincular a un encabezado en un archivo Markdown en el mismo repositorio, use vinculación relativa + vinculación hashtag.

- Ejemplo: [información técnica del proceso de registro](./understand-explore/rms-for-individuals-user-signup.md#technical-overview-of-the-sign-up-process)

Para vincular a un archivo externo, use la dirección URL completa como vínculo.

- Ejemplo: [Github](http://www.github.com)

Si aparece una dirección URL en un archivo Markdown, se transformará en un vínculo interactivo.

- Ejemplo: http://www.github.com

## <a name="lists"></a>Listas

### <a name="ordered-lists"></a>Listas ordenadas

1. En esta 
1. Is
1. Un
1. Ordered
1. Lista  


#### <a name="ordered-list-with-an-embedded-list"></a>Lista ordenada con una lista incrustada

1. Aquí
1. comes
1. an
1. embedded
    1. Miss Scarlett
    1. Professor Plum
1. ordered
1. list


### <a name="unordered-lists"></a>Listas desordenadas

- En esta
- es
- un
- con viñetas
- list


##### <a name="unordered-list-with-an-embedded-lists"></a>Lista desordenada con una lista incrustada

- En esta 
- bulleted 
- list
    - Mrs. Peacock
    - Mr. Green
- contiene  
- otros
    1. Colonel Mustard
    1. Mrs. White
- lists


## <a name="horizontal-rule"></a>Regla horizontal

---

## <a name="tables"></a>Tablas

| Tablas        | Son           | Interesantes  |
| ------------- |:-------------:| -----:|
| la col. 3 está      | alineada a la derecha | 1600 $ |
| la col. 2 está      | centrada      |   $12 |
| col 1 is default | left-aligned     |    $1 |


## <a name="code"></a>Código

### <a name="codeblock"></a>Bloque de código

    function fancyAlert(arg) {
      if(arg) {
        $.docs({div:'#foo'})
      }
    }

### <a name="in-line-code"></a>Código en línea

Este es un ejemplo de `in-line code`.

## <a name="blockquotes"></a>Blockquotes

> La sequía dura desde hace diez millones de años y el reino de los terribles lagartos había terminado hace ya mucho. Aquí en el ecuador, en el continente que un día se conocería como África, la batalla por la existencia había alcanzado un nuevo clímax de ferocidad y aún no se había definido el vencedor. En esta tierra seca y estéril, solo el pequeño, el rápido o el fiero podría salir adelante o incluso esperar sobrevivir.

## <a name="images"></a>Imágenes

### <a name="static-image"></a>Imagen estática

![este es el texto alternativo](./media/AzRMS_elements.png)

### <a name="linked-image"></a>Imagen vinculada

[![texto alternativo para la imagen vinculada](./media/AzRMS_elements.png)](https://azure.microsoft.com) 

### <a name="animated-gif"></a>Gif animado

![gif animado](./media/hololens.gif)

## <a name="alerts"></a>Alertas

### <a name="note"></a>Nota

> [!NOTE]
> This is NOTE

### <a name="warning"></a>Advertencia

> [!WARNING]
> This is WARNING

### <a name="tip"></a>Sugerencia

> [!TIP]
> This is TIP

### <a name="important"></a>Importante

> [!IMPORTANT]
> This is IMPORTANT

## <a name="videos"></a>Vídeos

### <a name="channel-9"></a>Channel 9

<iframe src="http://channel9.msdn.com/Series/Azure-Active-Directory-Videos-Demos/Azure-Active-Directory-Connect-Express-Settings/player" width="960" height="540" allowFullScreen frameBorder="0"></iframe>


### <a name="youtube"></a>Youtube

<iframe width="420" height="315" src="https://www.youtube.com/embed/R6_eWWfNB54" frameborder="0" allowfullscreen></iframe>

## <a name="docsms-extentions"></a>docs.ms extentions

### <a name="button"></a>Botón

> [!div class="button"]
[vínculos del botón](/rights-management)

### <a name="selector"></a>Selector

> [!div class="op_single_selector"]
- [foo](/rights-management/template.md)
- [barra](/rights-management/scratch.md)

### <a name="step-by-step"></a>Paso a paso

>[!div class="step-by-step"]
[Anterior](https://www.example.com)
[Siguiente](https://www.example.com)