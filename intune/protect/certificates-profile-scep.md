---
title: 'Uso de perfiles de certificado SCEP con Microsoft Intune: Azure | Microsoft Docs'
description: Cree y asigne perfiles de certificado de Protocolo de inscripción de certificados simple (SCEP) con Microsoft Intune.
keywords: ''
author: brenduns
ms.author: brenduns
manager: dougeby
ms.date: 11/13/2019
ms.topic: conceptual
ms.service: microsoft-intune
ms.subservice: protect
ms.localizationpriority: high
ms.technology: ''
ms.reviewer: lacranda
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.collection: M365-identity-device-management
ms.openlocfilehash: b9f9d6626d26e919efbd3a3d8b5dd735ecb7fb62
ms.sourcegitcommit: 01fb3d844958a0e66c7b87623160982868e675b0
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 11/20/2019
ms.locfileid: "74199133"
---
# <a name="create-and-assign-scep-certificate-profiles-in-intune"></a>Creación y asignación de perfiles de certificado SCEP en Intune

Después de [configurar la infraestructura](certificates-scep-configure.md) para admitir certificados de Protocolo de inscripción de certificados simple (SCEP), puede crear y luego asignar perfiles de certificado SCEP a usuarios y dispositivos en Intune.

> [!IMPORTANT]  
> Antes de crear perfiles de certificado SCEP, los dispositivos que vayan a usarlos deben confiar en la entidad de certificación (CA) raíz de confianza. Use un *perfil de certificado de confianza* en Intune para aprovisionar el certificado de entidad de certificación raíz de confianza para usuarios y dispositivos. Para obtener información sobre el perfil de certificado de confianza, vea [Exportación del certificado de entidad de certificación raíz de confianza](certificates-configure.md#export-the-trusted-root-ca-certificate) y [Creación de perfiles de certificado de confianza](certificates-configure.md#create-trusted-certificate-profiles) en *Uso de certificados para la autenticación en Intune*.


## <a name="create-a-scep-certificate-profile"></a>Creación de un perfil de certificado SCEP

1. Inicie sesión en el [Centro de administración del Administrador de puntos de conexión de Microsoft](https://go.microsoft.com/fwlink/?linkid=2109431).

2. Seleccione **Dispositivos** > **Perfil de configuración** > **Crear perfil**.

3. Escriba las propiedades siguientes:

4. Escriba un **Nombre** y una **Descripción** para el perfil de certificado SCEP.

5. En la lista desplegable **Plataforma**, seleccione una [plataforma de dispositivo compatible](certificates-configure.md#supported-platforms-and-certificate-profiles) para este certificado SCEP.

6. En la lista desplegable **Tipos de perfil**, seleccione **Certificado SCEP**.  

   Para la plataforma **Android Enterprise**, *Tipo de perfil* se divide en dos categorías: *Solo el propietario del dispositivo* y *Solo perfil de trabajo*. Asegúrese de seleccionar el perfil de certificado de SCEP correcto para los dispositivos que administra.  

   Los perfiles de certificado de SCEP para *Solo el propietario del dispositivo* tienen las limitaciones siguientes:

   1. En Supervisión, la creación de informes de certificados no está disponible para los perfiles de certificado de SCEP de propietario del dispositivo.

   2. Intune no se puede usar para revocar certificados aprovisionados por perfiles de certificado SCEP para los propietarios de dispositivos. La revocación se puede administrar a través de un proceso externo o directamente con la entidad de certificación. 

7. Seleccione **Configuración** y, después, complete las opciones de configuración siguientes:

   - **Tipo de certificado**:

     *(Se aplica a:  Android, Android Enterprise, iOS, macOS, Windows 8.1 y versiones posteriores, y Windows 10 y versiones posteriores).*

     Seleccione un tipo en función de cómo vaya a usar el perfil de certificado:

     - **Usuario**: los certificados *Usuario* pueden contener atributos de usuario y dispositivo en el asunto y SAN del certificado.  
     - **Dispositivo**:  Los certificados *Dispositivo* solo pueden contener atributos de dispositivo en el asunto y SAN del certificado.

       Use **Dispositivo** para escenarios como, por ejemplo, dispositivos sin usuario (como quioscos) o dispositivos Windows. En los dispositivos Windows, el certificado se coloca en el almacén de certificados del equipo local.

   - **Formato de nombre del sujeto**:

     seleccione cómo Intune crea automáticamente el nombre del sujeto en la solicitud de certificado. Las opciones para el formato de nombre del firmante dependen del tipo de certificado que seleccione: **Usuario** o **Dispositivo**.

     > [!NOTE]
     > Existe un [problema conocido](#avoid-certificate-signing-requests-with-escaped-special-characters) en el uso de SCEP para obtener certificados cuando el nombre del firmante en la solicitud de firma de certificado (CSR) resultante incluye uno de los siguientes caracteres como carácter de escape (precedido por una barra diagonal inversa \\):
     > - \+
     > - ;
     > - ,
     > - =

     - **Tipo de certificado de usuario**

       Las opciones de formato para el *Formato de nombre del firmante* incluyen las siguientes:

       - **No configurado**.
       - **Nombre común**
       - **Nombre común, incluyendo la dirección de correo electrónico**
       - **Nombre común como correo electrónico**
       - **IMEI (Identidad de equipo móvil internacional)**
       - **Número de serie**
       - **Personalizado**: cuando se selecciona esta opción, se muestra también un cuadro de texto **Personalizado**. Use este campo para escribir un formato de nombre del firmante personalizado, incluidas las variables. El formato personalizado admite dos variables: **Nombre común (CN)** y **dirección de correo electrónico (E)** . **Nombre común (CN)** se puede establecer en cualquiera de las siguientes variables:

         - **CN={{UserName}}** : nombre principal de usuario, como janedoe@contoso.com.
         - **CN={{AAD_Device_ID}}** : identificador asignado al registrar un dispositivo en Azure Active Directory (AD). Este identificador normalmente se usa para autenticarse en Azure AD.
         - **CN={{SERIALNUMBER}}** : número de serie (SN) único que normalmente usa el fabricante para identificar un dispositivo.
         - **CN={{IMEINumber}}** : número exclusivo de identidad de equipo móvil internacional (IMEI) usado para identificar un teléfono móvil.
         - **CN={{OnPrem_Distinguished_Name}}** : Secuencia de nombres distintivos relativos separados por comas, como *CN=Jane Doe,OU=UserAccounts,DC=corp,DC=contoso,DC=com*.

           Para usar la variable *{{OnPrem_Distinguished_Name}}* , asegúrese de sincronizar el atributo de usuario *onpremisesdistinguishedname* mediante [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con la instancia de Azure AD.

         - **CN={{onPremisesSamAccountName}}** : los administradores pueden sincronizar el atributo samAccountName de Active Directory con Azure AD mediante Azure AD Connect en un atributo llamado *onPremisesSamAccountName*. Intune puede sustituir esa variable como parte de una solicitud de emisión de certificado en el asunto de un certificado. El atributo samAccountName es el nombre de inicio de sesión del usuario que se utiliza para admitir clientes y servidores de una versión anterior de Windows (anterior a Windows 2000). El formato de nombre de inicio de sesión de usuario es el siguiente: *NombreDeDominio\usuario de prueba*, o bien solo *usuario de prueba*.

            Para usar la variable *{{onPremisesSamAccountName}}* , asegúrese de sincronizar el atributo de usuario *onPremisesSamAccountName* mediante [Azure AD Connect](https://docs.microsoft.com/azure/active-directory/connect/active-directory-aadconnect) con la instancia de Azure AD.

         Mediante una combinación de una o muchas de estas variables y cadenas estáticas, puede crear un formato de nombre de firmante personalizado como este:  
         - **CN={{UserName}},E={{EmailAddress}},OU=Mobile,O=Finance Group,L=Redmond,ST=Washington,C=US**

         Ese ejemplo incluye un formato de nombre de firmante en el que se usan las variables CN y E, y cadenas para los valores Unidad organizativa, Organización, Ubicación, Estado y País. [CertStrToName](https://msdn.microsoft.com/library/windows/desktop/aa377160.aspx) describe esta función y sus cadenas admitidas.

      - **Tipo de certificado de dispositivo**

        Las opciones de formato para el formato de nombre del firmante incluyen las variables siguientes:

        - **{{AAD_Device_ID}}** o **{{AzureADDeviceId}}** : cualquiera de las variables se puede usar para identificar un dispositivo por su identificador de Azure AD.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}** *(Solo aplicable para dispositivos Windows y unidos a dominio)*
        - **{{MEID}}**

        Puede especificar estas variables, seguidas del texto de la variable, en el cuadro de texto. Por ejemplo, el nombre común de un dispositivo denominado *Dispositivo1* se puede agregar como **CN={{DeviceName}}Dispositivo1**.

        > [!IMPORTANT]
        > - Al especificar una variable, incluya el nombre de la variable entre corchetes { } como se muestra en el ejemplo, para evitar un error.  
        > - Una persona con acceso al dispositivo podría suplantar las propiedades del dispositivo que se usan en el *asunto* o *SAN*, como **IMEI**, **SerialNumber** y **FullyQualifiedDomainName**.
        > - Un dispositivo debe admitir todas las variables especificadas en un perfil de certificado para que ese perfil se instale en ese dispositivo.  Por ejemplo, si se usa **{{IMEI}}** en el nombre del firmante de un perfil SCEP y se asigna a un dispositivo que no tiene un número IMEI, se producirá un error en la instalación del perfil.

   - **Nombre alternativo del firmante**: seleccione cómo Intune crea de forma automática el nombre alternativo del firmante (SAN) en la solicitud de certificado. Las opciones para el formato de SAN dependen del tipo de certificado que haya seleccionado: **Usuario** o **Dispositivo**.

      - **Tipo de certificado de usuario**

        Seleccione entre los atributos disponibles:

        - **Dirección de correo electrónico**
        - **Nombre principal de usuario (UPN)**

        Por ejemplo, los tipos de certificado de usuario pueden incluir el nombre principal de usuario (UPN) en el nombre alternativo del firmante. Si un certificado de cliente se usa para autenticar un servidor de directivas de redes, establezca el nombre alternativo del firmante en el UPN.

      - **Tipo de certificado de dispositivo**

        Use la lista desplegable **Atributo** y seleccione un atributo, asigne un **Valor** y **agréguelo** al perfil de certificado. Puede agregar varios valores si selecciona atributos adicionales.

        Entre los atributos disponibles se incluyen los siguientes:

        - **Dirección de correo electrónico**
        - **Nombre principal de usuario (UPN)**
        - **DNS**

        Con el tipo de certificado *Dispositivo*, puede usar estas variables de certificado de dispositivo para el valor:

        - **{{AAD_Device_ID}}** o **{{AzureADDeviceId}}** : cualquiera de las variables se puede usar para identificar un dispositivo por su identificador de Azure AD.
        - **{{Device_Serial}}**
        - **{{Device_IMEI}}**
        - **{{SerialNumber}}**
        - **{{IMEINumber}}**
        - **{{WiFiMacAddress}}**
        - **{{IMEI}}**
        - **{{DeviceName}}**
        - **{{FullyQualifiedDomainName}}**
        - **{{MEID}}**

        Para especificar un valor para un atributo, incluya el nombre de la variable entre llaves, seguido del texto de esa variable. Por ejemplo, se puede agregar un valor para el atributo DNS **{{AzureADDeviceId}}.domain.com**, donde *.domain.com* es el texto. Para un usuario llamado *Usuario1*, una dirección de correo electrónico podría aparecer como {{FullyQualifiedDomainName}}User1@Contoso.com.

        > [!IMPORTANT]
        > - Cuando use una variable de certificado de dispositivo, incluya el nombre de la variable entre llaves { }.
        > - No use llaves **{ }** , símbolos de barra vertical **|** ni puntos y coma **;** en el texto que sigue a la variable.
        > - Una persona con acceso al dispositivo podría suplantar las propiedades del dispositivo que se usan en el *asunto* o *SAN*, como **IMEI**, **SerialNumber** y **FullyQualifiedDomainName**.
        > - Un dispositivo debe admitir todas las variables especificadas en un perfil de certificado para que ese perfil se instale en ese dispositivo.  Por ejemplo, si se usa **{{IMEI}}** en el SAN de un perfil SCEP y se asigna a un dispositivo que no tiene un número IMEI, se producirá un error en la instalación del perfil.

   - **Período de validez del certificado**:

     Puede especificar un valor inferior al período de validez de la plantilla de certificado, pero no uno superior. Si ha configurado la plantilla de certificado para [admitir un valor personalizado que se puede establecer desde la consola de Intune](certificates-scep-configure.md#modify-the-validity-period-of-the-certificate-template), use esta opción para especificar la cantidad de tiempo restante antes de que expire el certificado.

     Por ejemplo, si el período de validez del certificado en la plantilla de certificado es de dos años, puede especificar un valor de un año, pero no un valor de cinco años. El valor también debe ser menor que el período de validez restante del certificado de la CA emisora.

   - **Proveedor de almacenamiento de claves (KSP)** :

     *(Se aplica a:  Windows 8.1 y versiones posteriores, y Windows 10 y versiones posteriores)*

     Especifique dónde se almacena la clave del certificado. Elija entre los valores siguientes:

     - **Inscribirse en KSP Módulo de plataforma segura (TPM) si está presente, si no en KSP Software**
     - **Inscribirse en KSP del Módulo de plataforma segura (TPM) o se producirá un error**
     - **Inscribirse en Passport o se producirá un error (Windows 10 y versiones posteriores)**
     - **Inscribirse en el KSP Software**

   - **Uso de la clave**:

     Seleccione las opciones de uso de la clave para el certificado:

     - **Firma digital**: permite el intercambio de claves solo si una firma digital protege la clave.
     - **Cifrado de clave**: permite el intercambio de claves solo si la clave está cifrada.

   - **Tamaño de la clave (bits)** :

     seleccione el número de bits que contiene la clave.

   - **Algoritmo hash**:

     *(Se aplica a Android, Android Enterprise, Windows Phone 8.1, Windows 8.1 y versiones posteriores, y Windows 10)*

     Seleccione uno de los tipos de algoritmos hash disponibles para usar con este certificado. Seleccione el nivel máximo de seguridad que admiten los dispositivos de conexión.

   - **Certificado raíz**:

     Seleccione el *perfil de certificado de confianza* que ha configurado y asignado antes a los usuarios y dispositivos correspondientes para este perfil de certificado SCEP. El perfil de certificado de confianza se usa para aprovisionar usuarios y dispositivos con el certificado de entidad de certificación raíz de confianza. Para obtener información sobre el perfil de certificado de confianza, vea [Exportación del certificado de entidad de certificación raíz de confianza](certificates-configure.md#export-the-trusted-root-ca-certificate) y [Creación de perfiles de certificado de confianza](certificates-configure.md#create-trusted-certificate-profiles) en *Uso de certificados para la autenticación en Intune*. Si tiene una entidad de certificación raíz y una entidad de certificación emisora, seleccione el perfil de certificado raíz de confianza que está asociado a la entidad de certificación emisora.

   - **Uso mejorado de clave**:

     Agregue valores para la finalidad prevista del certificado. En la mayoría de los casos, el certificado requiere *autenticación de cliente* para que el usuario o dispositivo se pueda autenticar en un servidor. Puede agregar usos de la clave adicionales según sea necesario.

   - **Umbral de renovación (%)** :

     especifique qué porcentaje de la duración del certificado tiene que quedar para que el dispositivo solicite la renovación del certificado. Por ejemplo, si escribe 20, se intentará la renovación del certificado cuando haya caducado al 80 %. Los intentos de renovación proseguirán hasta que la renovación sea correcta. La renovación genera un certificado nuevo, lo que da como resultado un nuevo par de claves pública y privada.

   - **Direcciones URL de servidor SCEP**:

     especifique una o varias direcciones URL para los servidores SCEP que emiten certificados mediante SCEP. Por ejemplo, escriba algo como *https://ndes.contoso.com/certsrv/mscep/mscep.dll* . Puede agregar direcciones URL de SCEP adicionales para el equilibrio de carga según sea necesario, ya que las direcciones URL se insertan de forma aleatoria en el dispositivo con el perfil. Si uno de los servidores SCEP no está disponible, se producirá un error en la solicitud de SCEP y es posible que, en las comprobaciones posteriores del dispositivo, la solicitud de certificado se realice en el mismo servidor inactivo.

8. Seleccione **Aceptar** y, luego, **Crear**. El perfil se crea y aparece en la lista *Configuración del dispositivo - Perfiles*.

### <a name="avoid-certificate-signing-requests-with-escaped-special-characters"></a>Evitar solicitudes de firma de certificado con caracteres de escape especiales

Existe un problema conocido con las solicitudes de certificado SCEP y PKCS que incluyen un nombre del firmante (CN) con uno o varios de los siguientes caracteres especiales como carácter de escape. Los nombres de firmante que incluyen uno de los caracteres especiales como un carácter de escape dan como resultado un CSR con un nombre de firmante incorrecto. Un nombre de sujeto incorrecto produce un error de validación de desafío de SCEP de Intune y no se emite ningún certificado.

Los caracteres especiales son:
- \+
- ,
- ;
- =

Cuando el nombre del firmante incluya uno de los caracteres especiales, use una de las siguientes opciones para solucionar esta limitación:

- Encapsula el valor de CN que contiene el carácter especial entre comillas.  
- Quite el carácter especial del valor de CN.

**Por ejemplo**, tiene un nombre del firmante que aparece como *Test User (TestCompany, LLC*).  Un CSR que incluya un CN con la coma entre *TestCompany* y *LLC* presenta un problema.  Para evitar el problema se puede poner el CN entero ente comillas o se puede quitar la coma que hay entre *TestCompany* y *LLC*:

- **Agregar comillas**: *CN=* ”Test User (TestCompany, LLC)”,OU=UserAccounts,DC=corp,DC=contoso,DC=com*
- **Quitar la coma**: *CN=Test User (TestCompany LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

 Sin embargo, al intentar usar un carácter de barra diagonal inversa para escapar la coma, se producirá un error en los registros de CRP:
 
- **Coma de escape**: *CN=Test User (TestCompany\\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com*

El error es similar al siguiente:

```
Subject Name in CSR CN="Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com" and challenge CN=Test User (TESTCOMPANY\, LLC),OU=UserAccounts,DC=corp,DC=contoso,DC=com do not match  

  Exception: System.ArgumentException: Subject Name in CSR and challenge do not match

   at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

Exception:    at Microsoft.ConfigurationManager.CertRegPoint.ChallengeValidation.ValidationPhase3(PKCSDecodedObject pkcsObj, CertEnrollChallenge challenge, String templateName, Int32 skipSANCheck)

   at Microsoft.ConfigurationManager.CertRegPoint.Controllers.CertificateController.VerifyRequest(VerifyChallengeParams value
```

## <a name="assign-the-certificate-profile"></a>Asignar el perfil de certificado

Los perfiles de certificado SCEP se asignan de la misma manera que [se implementan perfiles de dispositivo](../configuration/device-profile-assign.md) para otros fines. Pero, antes de continuar, tenga en cuenta lo siguiente:

- Cuando asigna perfiles de certificado SCEP a grupos, el archivo de certificado de la entidad de certificación raíz de confianza (según lo especificado en el *perfil de certificado de confianza*) se instala en el dispositivo. El dispositivo usa el perfil de certificado SCEP para crear una solicitud de certificado para ese certificado de entidad de certificación raíz de confianza.

- El perfil de certificado SCEP solo se instala en los dispositivos que ejecutan la plataforma que ha especificado al crear el perfil de certificado.

- Puede asignar perfiles de certificado en recopilaciones de usuarios o en recopilaciones de dispositivos.

- Para publicar rápidamente un certificado en un dispositivo una vez inscrito el dispositivo, asigne el perfil de certificado en un grupo de usuarios (no en un grupo de dispositivos). Si lo asigna en un grupo de dispositivos, deberá efectuar un registro completo del dispositivo para que el dispositivo reciba directivas.

- Si usa la administración conjunta para Intune y Configuration Manager, en Configuration Manager, [establezca el control deslizante de la carga de trabajo](https://docs.microsoft.com/sccm/comanage/how-to-switch-workloads) de la directiva de acceso a los recursos en **Intune** o **Intune piloto**. Esta configuración permite que los clientes de Windows 10 inicien el proceso de solicitar el certificado.

- Aunque cree y asigne el perfil de certificado de confianza y el perfil de certificado SCEP por separado, los dos se deben asignar. Si no están instalados en un dispositivo, se produce un error en la directiva de certificado SCEP. Asegúrese de que los perfiles de certificado raíz de confianza también se implementan en los mismos grupos que el perfil SCEP.

> [!NOTE]
> En los dispositivos iOS, cuando hay un perfil de certificado SCEP asociado con un perfil adicional, como un perfil de Wi-Fi o VPN, el dispositivo recibe un certificado para cada uno de esos perfiles adicionales. Esto hace que el dispositivo iOS tenga varios certificados entregados por la solicitud de certificado SCEP.  Si solo quiere un certificado, tendrá que usar certificados PKCS en lugar de certificados SCEP.  Esto se debe a diferencias en la forma de entregar los certificados SCEP y PKCS a los dispositivos.

## <a name="next-steps"></a>Pasos siguientes

[Asignación de perfiles](../configuration/device-profile-assign.md)
