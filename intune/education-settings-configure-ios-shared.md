---
title: "Configuración de dispositivos compartidos de Intune para la aplicación Classroom para iOS"
titleSuffix: Intune on Azure
description: "Conozca la configuración de Intune que puede usar para controlar los valores de configuración de la aplicación Classroom en los dispositivos iOS."
keywords: 
author: robstackmsft
ms.author: robstack
manager: angrobe
ms.date: 06/28/2017
ms.topic: article
ms.prod: 
ms.service: microsoft-intune
ms.technology: 
ms.assetid: 1381a5ce-c743-40e9-8a10-4c218085bb5f
ms.reviewer: heenamac
ms.suite: ems
ms.custom: intune-azure
ms.openlocfilehash: b95133d402b40085a61dedfdbd4abbb4eae73855
ms.sourcegitcommit: bb1a1e4e0bc26543a9c8fb52cb208e298c6b8e3f
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 08/19/2017
---
# <a name="how-to-configure-intune-education-settings-for-shared-ipad-devices"></a>Configuración del entorno educativo de Intune para dispositivos iPad compartidos

[!INCLUDE[azure_portal](./includes/azure_portal.md)]

Introducción a Intune admite la aplicación Classroom para iOS que ayuda a los profesores a guiar el aprendizaje y controlar los dispositivos de los estudiantes en el aula. Además, para la aplicación Classroom, Apple admite la capacidad de que los dispositivos iPad de los estudiantes se configure de manera que varios estudiantes puedan compartir un único dispositivo. Este documento le guía para conseguir este objetivo con Intune.
Para obtener información sobre la configuración de los dispositivos iPad (1:1) dedicados para usar la aplicación Classroom, vea [Configuración de Intune para la aplicación Classroom para iOS](education-settings-configure-ios.md).

## <a name="before-you-start"></a>Antes de empezar

Los requisitos previos para usar las funciones de iPad compartidas son:

- Instale [Apple School Manager](apple-school-manager-set-up-ios.md) y [School Data Sync (SDS)](https://support.office.com/article/Apple-School-Manager-integration-with-Intune-for-Education-and-School-Data-Sync-974bd1f9-2c7a-45cb-9447-b58166108617).
- Como parte de la instalación de Apple School Manager, configure [identificadores de Apple administrados](http://help.apple.com/schoolmanager/#/tes78b477c81) para los estudiantes. [Más información sobre los identificadores de Apple administrados](https://support.apple.com/en-us/HT205918).
- Cree un perfil de inscripción para los números de serie del dispositivo sincronizado desde Apple School Manager.

## <a name="step-1---import-your-school-data-into-azure-active-directory"></a>Paso 1: importar los datos de la escuela en Azure Active Directory

Use School Data Sync (SDS) de Microsoft para importar los registros de la escuela desde un sistema de información de estudiantes (SIS) existente a Azure Active Directory (Azure AD).
SDS sincroniza la información de su SIS y la almacena en Azure AD. Azure AD es un sistema de administración de Microsoft que ayuda a organizar los usuarios y los dispositivos. Luego, puede utilizar estos datos para administrar sus estudiantes y clases. [Obtenga más información sobre cómo implementar SDS](https://support.office.com/article/Overview-of-School-Data-Sync-and-Classroom-f3d1147b-4ade-4905-8518-508e729f2e91).

### <a name="how-to-import-data-using-sds"></a>Cómo importar datos con SDS

Puede importar información a SDS mediante uno de los siguientes métodos:

- [Archivos CSV](https://support.office.com/article/Follow-these-steps-71d5fe4a-aa51-4f35-9b53-348898a390a1): exporte manualmente y compile archivos de valores separados por comas (.csv)
- [API de PowerSchool](https://support.office.com/article/Follow-these-steps-851b5edc-558f-43a9-9122-b2d63458cb8f): proveedor de SIS que simplifica la sincronización con Azure AD
- [API inteligente](https://support.office.com/article/Follow-these-steps-f3d92fde-3ad0-48f3-80a1-1ad0ac4a3fae): solución de administración de identidades que se sincroniza directamente con Azure AD
- [OneRoster](https://support.office.com/article/Follow-these-steps-f43cbb2a-b502-497d-a8b1-783dc05a57ab): formato CSV que puede exportar y convertir para sincronizar con Azure AD

### <a name="find-out-more"></a>Obtenga más información

- [Obtener más información sobre la experiencia completa de sincronización de datos locales de escuelas en Azure AD](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect)
- [Obtener más información sobre School Data Sync de Microsoft](https://sds.microsoft.com/)
- [Obtener más información sobre las licencias en Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-licensing-whatis-azure-portal)


## <a name="step-2---create-and-assign-an-ios-education-profile-in-intune"></a>Paso 2: crear y asignar un perfil Educación de iOS en Intune

### <a name="configure-general-settings"></a>Configuración de las opciones generales

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
4. En la hoja **Configuración del dispositivo**, elija **Administrar** > **Perfiles**.
5. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
6. En la hoja **Crear perfil**, escriba un **nombre** y una **descripción** para el perfil Educación de iOS.
7. En la lista desplegable **Plataforma**, elija **iOS**.
8. En la lista desplegable **Tipo de perfil**, elija **Educación**.
9. Elija **Configuración** > **Configurar**.

A continuación, necesita certificados para establecer una relación de confianza entre los iPad de profesores y estudiantes. Se utilizan certificados para autenticar sin problemas y de forma silenciosa las conexiones entre los dispositivos sin tener que escribir nombres de usuario ni contraseñas.

>[!Important]
>Los certificados de profesores y estudiantes que use deben ser emitidos por diferentes entidades de certificación (CA). Debe crear dos nuevas CA subordinadas conectadas a la infraestructura de certificados existente; una para los profesores y otra para los estudiantes.

Los perfiles de educación de iOS solo admiten certificados PFX. No se admiten certificados SCEP.

Los certificados que crea deben admitir la autenticación de servidor además de la autenticación de usuario.

### <a name="configure-teacher-certificates"></a>Configuración de certificados de profesores

En la hoja **Educación**, elija **Teacher certificates** (Certificados de profesor).

#### <a name="configure-teacher-root-certificate"></a>Configuración de certificado raíz de profesor

En **Teacher root certificate** (Certificado raíz de profesor), elija el botón Examinar para seleccionar el certificado raíz del profesor con la extensión .cer (DER o Base64 codificado) o .P7B (con o sin la cadena completa).

#### <a name="configure-teacher-pkcs12-certificate"></a>Configuración de certificados de profesores PKCS#12

En **Teacher PKCS#12 certificate** (Certificado de profesor PKCS#12), configure los siguientes valores:

- **Formato de nombre de sujeto**: Intune agrega automáticamente el prefijo **líder**, para el certificado del profesor, y **miembro**, para el certificado de los estudiantes, a los nombres comunes del certificado.
- **Entidad de certificación**: entidad de certificación (CA) empresarial que se ejecuta en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes.
- **Nombre de la entidad de certificación**: escriba el nombre de la entidad de certificación.
- **Nombre de plantilla de certificado**: escriba el nombre de una plantilla de certificado que se haya agregado a una CA emisora.
- **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
- **Período de validez del certificado**: especifique la cantidad de tiempo que queda antes de que expire el certificado. Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.

Cuando haya terminado la configuración de los certificados de profesores, seleccione **Aceptar**.

### <a name="configure-student-certificates"></a>Configuración de certificados de estudiantes

1. En la **hoja Educación**, seleccione **Certificados de alumno**.
2. En la hoja **Certificados de alumno** de la lista **Tipo de certificados de dispositivo de alumno**, seleccione **iPad compartido**.

#### <a name="configure-student-root-certificate"></a>Configuración de certificado raíz de estudiantes

En **Certificado raíz de dispositivo**, seleccione el botón Examinar para seleccionar el certificado raíz del estudiante con la extensión .cer (DER o Base64 codificado) o .P7B (con o sin la cadena completa).

#### <a name="configure-device-pkcs12-certificate"></a>Configuración de certificados de dispositivos PKCS#12

En **Student PKCS#12 certificate** (Certificado de estudiante PKCS#12), configure los siguientes valores:

- **Formato de nombre de sujeto**: Intune agrega automáticamente el prefijo líder, para el certificado del profesor, y miembro, para el certificado de los dispositivos, a los nombres comunes del certificado.
- **Entidad de certificación**: entidad de certificación (CA) empresarial que se ejecuta en una edición Enterprise de Windows Server 2008 R2 o versión posterior. No se admiten CA independientes.
- **Nombre de la entidad de certificación**: escriba el nombre de la entidad de certificación.
- **Nombre de plantilla de certificado**: escriba el nombre de una plantilla de certificado que se haya agregado a una CA emisora.
- **Umbral de renovación (%)**: especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado.
- **Período de validez del certificado**: especifique la cantidad de tiempo que queda antes de que expire el certificado. Puede especificar un valor inferior al período de validez de la plantilla de certificado especificada, pero no superior. Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.

Cuando haya terminado la configuración de los certificados, haga clic en **Aceptar**.

### <a name="complete-certificate-setup"></a>Completar la configuración de certificado

1. En la hoja **Educación**, pulse **Aceptar**.
2. En la hoja **Create Profile** (Crear perfil), elija **Crear**.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="step-3---create-a-device-category"></a>Paso 3: Crear una categoría de dispositivo

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja de **Intune**, seleccione **Inscripción de dispositivos**.
4. En la hoja **Inscripción: información general**, seleccione **Categorías de dispositivos**.
5. En la hoja **Inscripción: categorías de dispositivos**, seleccione **Crear**.
6. En la hoja **Crear categoría de dispositivos**, escriba un **nombre** y una **descripción** para la categoría.
7. En la hoja **Crear categoría de dispositivos**, seleccione **Crear**.

La categoría de dispositivos se crea en la hoja **Inscripción: categorías de dispositivos**.

## <a name="step-4--create-a-dynamic-group"></a>Paso 4: Crear un grupo dinámico

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, seleccione **Grupos**.
4. En la hoja **Usuarios y grupos: todos los grupos**, seleccione **Nuevo grupo**.
5. En la hoja **Grupo**, escriba un **nombre** y una **descripción** para el grupo.
6. Desde la lista desplegable **Tipo de pertenencia**, seleccione **Dispositivo dinámico**.
7. Seleccione **Miembros del dispositivo dinámico** para crear reglas de pertenencia.
8. En la hoja **Reglas de pertenencia dinámica**:
1. Seleccione **deviceCategory** de la lista desplegable **Lugar donde agregar dispositivos**.
2. Seleccione **Igual a**.
3. Escriba la categoría de dispositivos que ha creado en el cuadro de texto en blanco
9. En la hoja **Reglas de pertenencia dinámica**, seleccione **Agregar consulta**.
10. En la hoja **Grupo**, pulse **Crear**.

El grupo dinámico se crea en la hoja **Usuarios y grupos: todos los grupos**.

## <a name="step-5--assign-a-device-to-a-category-carts"></a>Paso 5: Asignar un dispositivo a una categoría (Carros)

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Dispositivos**.
4. En la hoja **Dispositivos**, pulse **Todos los dispositivos**.
5. En la hoja **Dispositivos: todos los dispositivos**, seleccione un dispositivo.
6. En la hoja Dispositivos, pulse **Propiedades**.
7. En la hoja Propiedades del dispositivo, escriba la categoría de dispositivo en el cuadro de texto **Categoría de dispositivo**.
8. En la hoja Dispositivos, pulse **Guardar**.

Ahora el dispositivo está asociado a la categoría de dispositivo. Repita este proceso para todos los dispositivos que quiera asociar a la categoría de dispositivo que ha creado.

## <a name="step-6--create-classroom-profiles"></a>Paso 6: Crear perfiles de aulas

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
4. En la hoja **Configuración del dispositivo**, seleccione **Administrar** > **Perfiles de carro**.
5. En la hoja de perfiles, elija **Create Profile** (Crear perfil).
6. En la hoja **Crear asociación**, escriba un **nombre** y una **descripción**.
7. Pulse **Seleccionar clases** > **Configurar** para asociar grupos al perfil de carro.
8. Seleccione las clases que se van a incluir en el perfil de carro y, después, pulse **Seleccionar**. 
9. Pulse **Seleccionar carros** > **Configurar** para asociar grupos al perfil de carro.
10. Seleccione los grupos que se van a incluir en el perfil de carro y, después, pulse **Seleccionar**.
11. En la hoja **Crear asociación**, seleccione **Guardar** para guardar el perfil de carro.

El perfil se crea y aparece en la hoja de la lista de perfiles.

## <a name="step-7---assign-the-cart-profile-to-classes"></a>Paso 7: Asignar el perfil de carro a las clases

1. Inicie sesión en el portal de Azure.
2. Elija **More Services** >  (Más servicios) **Other** >  (Otros) **Intune**.
3. En la hoja **Intune**, elija **Configurar dispositivos**.
4. En la hoja **Configuración del dispositivo**, pulse **Supervisar** > **Estado de la asignación**.
5. En la hoja **Estado de la asignación**, seleccione el **Perfil de carro** que ha creado.
6. En la hoja **Perfil de carro**, pulse **Asignaciones** y, después, en **Incluir**, pulse **Seleccionar grupos para incluir**.
7. Seleccione las clases que quiere que se dirijan al perfil de carro (no seleccione un grupo) y, después, pulse **Seleccionar**. 
8. Cuando termine, elija **Guardar**.

La asignación se completa e Intune implementa el perfil de Classroom a los dispositivos de destino basándose en la asignación del aula.

## <a name="next-steps"></a>Pasos siguientes

Ahora los estudiantes pueden compartir dispositivos entre ellos y pueden seleccionar cualquier iPad del aula, iniciar sesión con un PIN y personalizarlo con su contenido. Para obtener más información sobre los dispositivos iPad compartidos, vea el [sitio web de Apple](https://www.apple.com/education/it/).
