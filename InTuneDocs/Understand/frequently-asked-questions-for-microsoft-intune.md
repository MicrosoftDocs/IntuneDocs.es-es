---
# required metadata

title: Preguntas más frecuentes | Microsoft Intune
description:
keywords:
author: Nbigman
manager: jeffgilb
ms.date: 04/28/2016
ms.topic: article
ms.prod:
ms.service: microsoft-intune
ms.technology:
ms.assetid: a8126cca-9ec4-454b-a20b-dc1bb6797327

# optional metadata

#ROBOTS:
#audience:
#ms.devlang:
ms.reviewer: jeffgilb
ms.suite: ems
#ms.tgt_pltfrm:
#ms.custom:

---

# Preguntas más frecuentes sobre Intune
En este artículo se proporcionan respuestas a algunas de las preguntas más frecuentes sobre Intune. Si no ve una respuesta a su pregunta aquí, [háganoslo saber](https://microsoftintune.uservoice.com/)..

## Problemas generales

-   **¿Cómo puedo saber cuándo se ha actualizado el servicio de Intune?**

    Inicie sesión en su cuenta en manage.microsoft.com. En Información general de administración, elija **Ver estado del servicio**. La ubicación del inquilino y la programación de mantenimiento se muestran ahí. Obtenga información sobre las actualizaciones del servicio en el artículo [What's new (Novedades)](/intune/deploy-use/whats-new-in-microsoft-intune).

-   **Si un usuario cambia el nombre de un dispositivo dentro de la aplicación del portal de empresa, ¿cambiará ese nombre en Intune o Configuration Manager?**

    No, ese cambio de nombre es solo por conveniencia del usuario.

-   **¿Hay alguna funcionalidad de asistencia remota en Intune para dispositivos móviles?**

    No, no hay ninguna. Las aplicaciones de terceros como [Bomgar](http://www.bomgar.com/) y [TeamViewer](https://www.teamviewer.com/) podrían resultar útiles.

## Cuentas

-   **Si empiezo a evaluar Intune y creo un nuevo inquilino para la versión de prueba, ¿puedo agregar Office 365 a la evaluación mediante el mismo inquilino?**

    Sí. Simplemente inicie sesión con un administrador global desde su suscripción o inquilino existente de Intune, como *globaladmin@&lt;empresa&gt;.onmicrosoft.com*.

-   **¿Si asigno una autoridad de MDM a Intune durante una suscripción de prueba, ¿me sería difícil cambiar a un servicio de otra empresa si cambio de opinión acerca de Intune?**

    Aunque es difícil imaginar que no se quede con Intune, la elección de la autoridad de MDM no afecta a su capacidad de cambiarse a otro servicio. Se trata específicamente de elegir Intune o Intune con System Center Configuration Manager.

-   **¿Puedo usar mi nombre de dominio existente de Office 365 para mi siguiente cuenta de Intune?**

    Sí, si inicia sesión con el identificador de organización que está asociado con su dominio comprobado y su inquilino de Office 365 existente cuando cree la prueba de Intune o active las licencias.

    Intune usará el mismo dominio y los mismos usuarios que en su cuenta de Office 365. Tenga en cuenta que cada usuario de Office 365 tendría que estar habilitado como usuario de Intune, con una licencia de Intune. Esto lo tendría que hacer el administrador global que administra el inquilino.

## Inscripción

-   **¿Dónde pueden obtener información mis usuarios para inscribir sus dispositivos?**

    Puede usar o personalizar información desde las [End-user Intune enrollment instructions for IT administrators (Instrucciones de inscripción de Intune del usuario final para los administradores de TI)](https://gallery.technet.microsoft.com/End-user-Intune-enrollment-55dfd64a)..

-   **¿Cómo puedo solucionar problemas con la inscripción de dispositivos?**

    Encontrará métodos para solucionar problemas comunes de inscripción en [Troubleshoot device enrollment in Intune (Solución de problemas de inscripción de dispositivos en Intune)](/intune/troubleshoot/troubleshoot-device-enrollment-in-intune)..

-   **¿Cómo puedo recopilar registros de inscripción si un usuario tiene un problema de inscripción?**

    Siga [estas instrucciones](http://www.microsoft.com/en-us/download/46391)..

## Administración de dispositivos móviles

-   **MDM general**

    -   **¿Puede detectar Intune si un dispositivo está liberado mediante jailbreak?**

        Sí, en algunos sistemas operativos. Para más detalles sobre cómo administrar dispositivos con Jailbreak, vea [Create a device compliance policy (Crear una directiva de cumplimiento de dispositivos)](/intune/deploy-use/create-a-device-compliance-policy-in-microsoft-intune.md)..

    -   **¿Puedo borrar selectivamente datos corporativos de un dispositivo?**

        Sí. Para más información, vea [Help protect your data with remote wipe, remote lock, or passcode reset (Ayude a proteger sus datos mediante la eliminación remota, el bloqueo remoto o el restablecimiento de código de acceso)](/intune/deploy-use/use-remote-lock-and-passcode-reset-in-microsoft-intune.md)..

    -   **¿Hay alguna manera de bloquear determinados sitios web en el explorador del dispositivo móvil a través de Intune?**

        No en el explorador nativo de ninguna plataforma. Sin embargo, puede permitir o bloquear las direcciones URL cuando implemente el explorador web administrado por Intune en dispositivos iOS y Android. Para más información, vea [Manage Internet access using managed browser policies (Administrar el acceso a Internet mediante directivas de explorador administrado)](/intune/Deploy-Use/Manage-Internet-access-using-managed-browser-policies-with-Microsoft-Intune.md)..

    -   **¿Podemos impedir que un usuario desinstale una aplicación?**

        Por lo general, no. Sin embargo, en un dispositivo iOS supervisado puede impedir que un usuario desinstale una aplicación que se distribuyó con Apple Configurator. 

    -   **¿Hay alguna manera de administrar el uso de datos móviles?**

        No directamente, pero puede asegurarse de que la conexión Wi-Fi sea el método preferido para conectarse insertando perfiles Wi-Fi en los dispositivos, tal como se describe en [Help users connect to company networks using Wi-Fi profiles (Ayudar a los usuarios a conectarse a las redes de la empresa mediante perfiles de Wi-Fi)](/intune/Deploy-Use/wi-fi-connections-in-microsoft-intune.md). Además, algunas plataformas (por ejemplo, iOS y Android KNOX) permiten controlar ajustes como la itinerancia de voz y de datos.

    -   **¿Hay alguna forma de evitar que un usuario anule la inscripción de un dispositivo? ¿Qué ocurre si se trata de un dispositivo que pertenece a la empresa?**

        En general, no. Sin embargo, mediante la configuración personalizada de Windows Phone, puede evitar la cancelación de la inscripción de usuarios en Windows Phone 8.1. Además, en los dispositivos iOS que están supervisados o inscritos en el programa de inscripción de dispositivos Apple, es posible impedir que un usuario anule la inscripción de un dispositivo.

    -   **¿Puedo cambiar mi autoridad de MDM seleccionada?**

        Puede cambiar la autoridad de MDM en algunos casos. Para ello, póngase en contacto con el soporte técnico, como se describe en [How to get support for Microsoft Intune (Cómo obtener soporte técnico para Microsoft Intune)](/intune/Troubleshoot/How-to-get-support-for-Microsoft-Intune.md). En la siguiente tabla se describen los cambios que son posibles. Los cambios en la autoridad de MDM requieren volver a inscribir los dispositivos.

        ||**A:** Intune!**A:** O365|**A:** Configuration Manager con Intune|
        |**Desde:** Intune| |Yes&#42;|Yes|
        |**Desde:** O365||Yes&#42;||Yes|
        |**Desde:** Configuration Manager con Intune|Yes|Yes| |
        
        &#42;Las autoridades de MDM de Intune y O365 pueden coexistir, por lo que no tendrá que volver a inscribir dispositivos móviles.



-   **Windows**

    -   **¿Puedo transferir localmente una aplicación de la Tienda Windows?**

        Las aplicaciones disponibles públicamente no pueden transferirse localmente. Aunque es posible descargar el archivo XAP, no puede cargarlo a Intune porque es un archivo XAP público, cifrado y firmado con el certificado de firma de código del desarrollador. Solo puede transferir localmente las aplicaciones que desarrolle y firme con su propio certificado de firma de código.

    -   **¿Las aplicaciones de la Tienda de Windows Phone distribuidas a través del portal de empresa requieren que el usuario final tenga una cuenta Microsoft?**

        Sí, el usuario final no podrá obtener las aplicaciones sin una cuenta Microsoft. La excepción son las aplicaciones LOB privadas y transferidas localmente, que se pueden implementar en un dispositivo sin una cuenta Microsoft.

    -   **¿Es necesaria una cuenta Microsoft en un dispositivo Windows Phone 8.1 para que se pueda administrar mediante Intune?**

        No. Sin embargo, se necesitará para instalar la mayoría de las aplicaciones desde la tienda pública.

        **¿Por qué Windows Phone requiere un certificado de Symantec para la administración?**
        Windows Phone controla la instalación de aplicaciones. Cualquier usuario que tenga una cuenta de Microsoft puede instalar aplicaciones desde la Tienda de Windows Phone, o bien las empresas pueden instalar o realizar la instalación de prueba de aplicaciones de línea de negocio (LOB) desarrolladas internamente mediante un proceso especial que se describe en la documentación de Windows Phone. Al instalar las aplicaciones LOB, los dispositivos Windows Phone solo confían en un tipo especial de certificado emitido por Symantec. No puede usar ningún otro certificado generado por vía comercial o privada. Este requisito se aplica a todas soluciones de administración de dispositivos móviles, no solo a Intune.

        El certificado de Symantec crea un token de inscripción de aplicación (AET). El AET puede instalarse en un dispositivo cuando el dispositivo se inscribe para la administración de dispositivos móviles, o puede instalarse fuera de banda desde un sitio web seguro o desde un archivo adjunto de correo electrónico. Los administradores deben firmar todas las aplicaciones de LOB con el certificado de Symantec mediante las herramientas proporcionadas en el [Windows Phone SDK](http://go.microsoft.com/fwlink/?LinkId=268439). Cuando los usuarios intentan instalar aplicaciones de LOB, el sistema operativo Windows Phone comprueba la firma en el AET para compararla con la firma de la aplicación. Si las firmas coinciden, se puede continuar con la instalación. Si no se puede consultar el AET, se produce un error en la instalación. Existen varios motivos por los que quizás no se pueda consultar el AET:

        -   El AET nunca se instaló en el dispositivo

        -   El AET ha expirado

        -   El AET no se creó con el mismo certificado de Symantec utilizado para firmar la aplicación

        Windows Phone no requiere que el AET esté presente durante la inscripción de MDM, pero antes de la versión de noviembre de 2014, Intune necesitaba el AET y un ssp.xap firmado porque no existía ninguna otra manera de instalar el AET y ssp.xap excepto durante la inscripción.

    **¿Cómo se crea el AET para usuarios de Intune?**
  Cuando los administradores cargan el archivo .pfx para su certificado de Symantec, Intune crea automáticamente el AET y lo implementa en dispositivos Windows Phone inscritos. No es necesario que los administradores de Intune usen la herramienta AET Generator en el Windows Phone SDK.

      > [!IMPORTANT]
        > Intune no admite la creación manual del AET ni su implementación fuera de banda.

    **¿Qué cambios que se han producido para reducir la necesidad de un certificado de Symantec?**
       En la versión de noviembre de 2014, Intune realizó cambios para permitir situaciones en las que las empresas no tengan un certificado de Symantec.

       -   El Portal de empresa para Windows Phone 8.1 está disponible para su instalación desde la tienda, por lo que no necesita la firma de un certificado de Symantec y ni es necesario validarlo con respecto a un AET. En su lugar, la aplicación se valida como parte del proceso de publicación de la tienda.

        -   Los dispositivos Windows Phone 8.1 se pueden inscribir con o sin un AET en el teléfono. Si hay un AET disponible, se instalará la primera vez que el dispositivo se sincronice con Intune. Si no hay ningún AET, el dispositivo puede seguir administrándose mediante Intune y los usuarios pueden instalar el Portal de empresa desde la tienda y usar la mayoría de las características del Portal de empresa sin un certificado de Symantec para firmar aplicaciones.

        No hay ningún cambio en el requisito de Symantec para dispositivos Windows Phone 8. Los dispositivos Windows Phone 8 deben tener el ssp.xap firmado y el AET presentes durante la inscripción; de lo contrario, se bloqueará de inscripción.

        **¿Qué funcionalidad se admite si se inscribe un dispositivo Windows Phone 8.1 pero no hay ningún certificado de Symantec?**
        Si se inscribe un dispositivo Windows Phone 8.1 pero no hay ningún certificado de Symantec, puede:

        -   Crear directivas e insertarlas en el dispositivo

        -   Configurar la información de contacto del departamento de TI que se muestra en el Portal de empresa

        -   Crear vínculos profundos a la tienda e implementarlos en el Portal de empresa

        -   Crear vínculos a páginas web e implementarlos en el Portal de empresa

        -   Crear los términos y condiciones que deben aceptar los usuarios para poder usar el Portal de empresa

        Lo único que no puede hacer sin un certificado de Symantec es implementar aplicaciones de LOB.

        > [!IMPORTANT]
        > Intune Software Publisher no comprueba que las aplicaciones estén firmadas al cargarlas. Si implementa aplicaciones sin firmar, se producirá un error cuando los usuarios intenten instalarlas.

        **¿Qué pueden hacer los usuarios si tienen el Portal de empresa pero no hay ningún certificado de Symantec?**
        No es necesario que los dispositivos Windows Phone 8.1 estén inscritos para que los usuarios puedan instalar el Portal de empresa desde la tienda. Si el dispositivo no está inscrito, se solicitará a los usuarios que lo inscriban. Al tocar el mensaje del Portal de empresa, los usuarios acceden directamente a **Configuración/Área de trabajo**, donde pueden inscribir sus dispositivos.

        Incluso sin inscribir el dispositivo, los usuarios pueden realizar las siguientes acciones con el Portal de empresa instalado desde la tienda:

        -   Aceptar o rechazar los términos y condiciones configurados por el administrador. Si los usuarios rechazan los términos y condiciones, se cierra el Portal de empresa.

        -   Ver la información de contacto del departamento de TI

        -   Ver los dispositivos inscritos, entre ellos, los dispositivos iOS, Android y Windows

        -   Usar vínculos profundos a aplicaciones en la tienda

        -   Usar vínculos web para abrir páginas web

        Con el dispositivo inscrito, los usuarios pueden ver el dispositivo en la lista **Mis dispositivos** . Una vez inscrito, el dispositivo está sujeto a las directivas de Intune implementadas. Los dispositivos deben inscribirse para obtener el AET e instalar aplicaciones de LOB. A los dispositivos no inscritos que intenten instalar una aplicación de LOB se les solicitará que se inscriban.

        Lo único que los usuarios no pueden hacer si la empresa no tiene un certificado de Symantec es instalar aplicaciones de LOB implementadas por el administrador.

        **Nuestra empresa ya tiene un certificado y ha inscrito dispositivos Windows Phone 8.1. ¿Es necesario hacer algo diferente ahora que el Portal de empresa está disponible en la tienda?**
        El ssp.xap actual desde el centro de descarga sigue funcionando en dispositivos Windows Phone 8.1. Puede seguir indicando a los usuarios que se inscriban y obtengan el portal de empresa durante la instalación.

        **¿Cuáles son las ventajas y desventajas de que los usuarios obtengan el Portal de empresa desde la tienda?**
        Ventajas:

        -   Los usuarios obtienen vínculos profundos y vínculos web, incluso si el dispositivo Windows Phone 8.1 no está inscrito

        -   Cuando Microsoft actualiza el Portal de empresa, la aplicación de la tienda se actualiza automáticamente sin necesidad de que descargue, firme o vuelva a implementar el ssp.xap

        -   La documentación para los usuarios de Windows Phone 8.1, iOS, Android y Windows es coherente: “Ir a la tienda e instalar el Portal de empresa”.

        -   Los usuarios ven la aplicación tal y como se instala y reciben instrucciones de inscripción al abrirse

        Desventajas:

        -   Los usuarios ven una casilla para instalar un "**hub de empresa**", pero no hay nada que les dirija al Portal de empresa en la lista de aplicaciones del dispositivo

        -   No se solicita a los usuarios que acepten términos y condiciones personalizados hasta que abran el Portal de empresa

        En las siguientes circunstancias, puede seguir indicando a los usuarios que se inscriban e instalen el ssp.xap durante la inscripción:

        -   Si la empresa bloquea el acceso a la tienda desde los dispositivos Windows Phone, los usuarios deben instalar el ssp.xap durante la inscripción.

        -   Si los usuarios no tienen cuentas de Microsoft configuradas en sus dispositivos Windows Phone, no podrán instalar el Portal de empresa desde la tienda.

        -   Si la documentación existente para la inscripción de Windows Phone les indica que vayan primero a Configuración, Área de trabajo, es posible que se tarde un tiempo en actualizar los documentos y dirigir a los usuarios a la tienda.

        **¿Cuál es la diferencia entre el ssp.xap del centro de descarga y la aplicación de la tienda?**

        -   El Portal de empresa de la tienda no exige la firma de un certificado de Symantec para su instalación

        -   El Portal de empresa de la tienda presenta los términos y condiciones para el usuario pero no así el ssp.xap del centro de descarga

        -   El Portal de empresa de la tienda es un archivo .appx en lugar de .xap

        **¿Puedo obtener el archivo de Portal de empresa e insertarlo en los dispositivos de mis usuarios en lugar de enviarlos a la tienda?**
        Sí. La aplicación Portal de empresa se puede descargar para los siguientes sistemas operativos desde el centro de descarga:

        -   Windows Phone 8.1: [http://go.microsoft.com/fwlink/?LinkId=615799](http://go.microsoft.com/fwlink/?LinkId=615799)

        -   Windows Phone 8.0 : [http://go.microsoft.com/fwlink/?LinkId=268440](http://go.microsoft.com/fwlink/?LinkId=268440)

        -   Windows 8.1: [http://go.microsoft.com/fwlink/?LinkId=615800](http://go.microsoft.com/fwlink/?LinkId=615800)

        **¿Las empresas pueden seguir usando la herramienta de soporte para la administración de versión de prueba de Windows Intune de Windows Phone si no tienen un certificado de Symantec y seguir indicando a los usuarios que instalen el Portal de empresa desde la tienda?**
        Sí. Si necesita realizar una prueba de concepto que incluya la instalación de aplicaciones de LOB, la herramienta de administración de pruebas funciona con la versión de la tienda del portal de empresa. Sin embargo, puesto que el AET del certificado de Symantec ya no es necesario para inscribir dispositivos Windows Phone 8.1, las empresas pueden probar la instalación de aplicaciones mediante vínculos profundos a aplicaciones de la tienda.

        La herramienta de soporte para la administración de versión de prueba de Windows Intune de Windows Phone es solo para suscripciones de prueba de Intune.

        > [!IMPORTANT]
        > Use solo las pruebas de la herramienta de administración de pruebas. Los dispositivos inscritos con el AET desde la herramienta de administración de pruebas deben anular la inscripción y volver a inscribirse si el certificado de Symantec para la herramienta de administración de pruebas ya no está disponible, o bien si la empresa obtiene su propio certificado de Symantec para firmar aplicaciones.

        **¿Las empresas pueden comenzar sin ningún certificado de Symantec y, a continuación, agregar uno más tarde, incluso después de que se hayan inscrito dispositivos Windows Phone 8.1?**
        Sí. Incluso si ya se han inscrito dispositivos Windows Phone 8.1, puede obtener un certificado de Symantec, firmar el ssp.xap y cargar este archivo y el archivo pfx. A continuación, Intune generará el AET. Los dispositivos Windows Phone 8.1 obtendrán el AET la próxima vez que se sincronicen, hasta un máximo de ocho horas. Deje que pasen al menos ocho horas antes de implementar las aplicaciones de línea de negocio después de cargar los archivos xap y pfx.


-   **Android**

    -   **¿Cuánto tiempo se necesita para cifrar un dispositivo Android?**

        Esto depende principalmente de la velocidad del procesador del dispositivo y la cantidad de memoria total y utilizada. No es una función de Intune.

-   **iOS**

    -   **Al implementar aplicaciones de iOS con Intune, si se han cargado el archivo de manifiesto e IPA de la aplicación, ¿el dispositivo necesita que se especifique un identificador de Apple para continuar con la instalación?**

        No. Cuando Intune proporciona los bits (IPA cargado en Intune), las aplicaciones se transfieren localmente y no necesitan un identificador de Apple.

    -   **¿Hay alguna forma de habilitar la instalación de aplicaciones en iOS sin permitir el acceso a Apple Store?**

        No, pero puede habilitar App Store y usar aplicaciones permitidas y bloqueadas en iOS para vigilar lo que los usuarios están haciendo. Las aplicaciones LOB transferidas localmente no requieren acceso al App Store de Apple.

    -   **¿Las aplicaciones de Apple Store distribuidas a través del Portal de empresa requieren que el usuario final tenga una cuenta de iTunes?**

        Sí, el usuario final no podrá obtener las aplicaciones sin una cuenta de iTunes.

    -   **¿Puedo bloquear App Store?**

        Sí, pero esto bloqueará todas las instalaciones y actualizaciones de aplicaciones de la tienda de aplicaciones, no solo las iniciadas por el usuario final. Esto significa que cualquier aplicación pública de la tienda de aplicaciones que implemente desde Intune también produciría un error.

## Implementación de aplicaciones

-   **¿Cómo puedo agregar una aplicación recomendada?**

    En Intune, se denominan “aplicaciones destacadas” y se documentan en [Deploy apps in Microsoft Intune (Implementar aplicaciones en Microsoft Intune)](/Intune/Deploy-Use/deploy-apps-in-microsoft-intune.md)..

-   **¿Puedo obtener almacenamiento en nube adicional para las aplicaciones que quiero implementar?**

    Sí. Puede leer sobre esto en [Deploy apps (Implementar aplicaciones)](/Intune/Deploy-Use/deploy-apps.md), en la sección *Requisitos de almacenamiento en nube*..

## Seguridad

-   **¿Puede Intune exigir BitLocker?**

    El agente de OMA-DM en Windows 8.1/RT permite leer (obtener) el estado de cifrado. No puede establecerlo. Esto es así para Intune y otros servicios de administración de dispositivos móviles.

-   **Si cifro una tableta de Windows 8 mediante BitLocker, ¿puedo aplicar el borrado completo del dispositivo si un usuario no puede iniciar sesión correctamente varias veces consecutivas?**

    No hay ninguna opción de borrado completo en dispositivos Windows 8.1/RT en ningún servicio de administración de dispositivos móviles, incluido Intune. Intune permite el borrado selectivo de esos dispositivos. Para más información sobre el borrado selectivo en Intune, vea [Protect apps and data with Microsoft Intune (Proteger las aplicaciones y los datos con Microsoft Intune)](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)..

## Portal de empresa

-   **¿Puedo personalizar mi Portal de empresa?**

    Sí. En la consola de administración de Intune, vaya a **Administrador&gt;Portal de empresa** para ver esas configuraciones.

## Microsoft Intune con Configuration Manager

-   **Al usar Configuration Manager con Intune, ¿dónde administro mis dispositivos?**

    Administre todos los dispositivos desde la consola de Configuration Manager, aunque los dispositivos con el agente de Intune instalado aparezcan en la consola de Intune. Los dispositivos móviles no aparecerán en la consola de Intune.

-   **¿Puedo realizar un borrado selectivo de los dispositivos?**

    Si usa System Center 2012 R2 Configuration Manager o una versión posterior con Intune, puede realizar un borrado selectivo de los datos de la empresa. Para más información, vea [Protect apps and data with Microsoft Intune (Proteger aplicaciones y datos con Microsoft Intune)](/intune/Deploy-Use/protect-apps-and-data-with-microsoft-intune.md)..

-   **Si estoy usando Configuration Manager con Intune, ¿puedo seguir usando el Portal de administración de Intune?**

    Puede, pero solo los equipos PC que tengan instalado el agente de Intune se podrán administrar desde ese portal. También hay más información útil en el portal sobre las alertas del servicio, el estado del servicio, etc., pero la configuración de administración de dispositivos no se aplicará a los dispositivos inscritos.



<!--HONumber=May16_HO1-->


