---
title: Agregar aplicaciones Win32 a Microsoft Intune
titlesuffix: ''
description: Obtenga información sobre cómo agregar, entregar y administrar aplicaciones Win32 con Microsoft Intune. En este tema se proporciona información general sobre las funciones de entrega y de administración de aplicaciones Win32 de Intune e información sobre la solución de problemas de aplicaciones Win32.
keywords: ''
author: Erikre
ms.author: erikre
manager: dougeby
ms.date: 01/23/2019
ms.topic: article
ms.prod: ''
ms.service: microsoft-intune
ms.technology: ''
ms.assetid: efdc196b-38f3-4678-ae16-cdec4303f8d2
ms.reviewer: mghadial
ms.suite: ems
search.appverid: MET150
ms.custom: intune-azure
ms.openlocfilehash: cb52a9755dffd20e6d3d66419855cc4ee7fca293
ms.sourcegitcommit: 06f62ae989da6c60bac4a52ccd41b429f7367d8c
ms.translationtype: HT
ms.contentlocale: es-ES
ms.lasthandoff: 01/25/2019
ms.locfileid: "55068329"
---
# <a name="intune-standalone---win32-app-management-public-preview"></a>Intune independiente: administración de aplicaciones Win32 (versión preliminar pública)

Intune independiente admite capacidades increíbles de administración de aplicaciones Win32. Aunque es posible que los clientes conectados a la nube usen Configuration Manager para la administración de aplicaciones Win32, los clientes que solo utilicen Intune tendrán mayores capacidades de administración para sus aplicaciones Win32 de línea de negocio (LOB). En este tema se proporciona información general sobre la característica de administración de aplicaciones Win32 de Intune e información sobre la solución de problemas.

## <a name="prerequisites-for-public-preview"></a>Requisitos previos para la versión preliminar pública

- Windows 10 versión 1607 o posteriores (versiones Enterprise, Pro y Education)
- El cliente de Windows 10 debe: 
    - haberse unido a Azure Active Directory (AAD) o Azure Active Directory híbrido, y
    - haberse inscrito en Intune (administrado por MDM)
- El tamaño de la aplicación Windows está limitado a 8 GB por aplicación en la versión preliminar pública 

## <a name="prepare-the-win32-app-content-for-upload"></a>Preparar el contenido de la aplicación Win32 para la carga

Use la [herramienta de preparación de la carga de aplicaciones Win32 en Microsoft Intune](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) para procesar previamente las aplicaciones Win32. La herramienta de empaquetado convierte los archivos de instalación de aplicaciones al formato *.intunewin*. La herramienta de empaquetado también detecta algunos de los atributos requeridos por Intune para determinar el estado de instalación de la aplicación. Después de usar esta herramienta en la carpeta de instalación de aplicaciones, podrá crear una aplicación Win32 en la consola de Intune.

Puede descargar la [herramienta de preparación de la carga de aplicaciones Win32 en Microsoft Intune](https://github.com/Microsoft/Intune-Win32-App-Packaging-Tool) desde GitHub.

### <a name="available-command-line-parameters"></a>Parámetros de línea de comandos disponibles 

|    **Parámetro de línea de comandos**    |    **Descripción**    |
|:------------------------------:|:----------------------------------------------------------:|
|    `-h`     |    Ayuda    |
|    `-c <setup_folder>`     |    Carpeta de configuración para todos los archivos de instalación.    |
|   ` -s <setup_file>`     |    Archivo de instalación (como *setup.exe* o *setup.msi*).    |
|    `-o <output_folder>`     |    Carpeta de salida del archivo *.intunewin* generado.    |
|    `-q`       |    Modo silencioso    |

### <a name="example-commands"></a>Comandos de ejemplo

|    **Comando de ejemplo**    |    **Descripción**    |
|:-----------------------------------------------------------------------------------------:|:--------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------:|
|    `IntuneWinAppUtil -h`    |    Este comando muestra información de uso de la herramienta.    |
|    `IntuneWinAppUtil -c <setup_folder> -s <source_setup_file> -o <output_folder> <-q>`    |    Este comando generará el archivo `.intunewin` desde la carpeta de origen especificada y el archivo de instalación. En el archivo de instalación MSI, esta herramienta recupera la información necesaria para Intune. Si se especifica `-q`, el comando se ejecuta en modo silencioso y si el archivo de salida ya existe, se sobrescribe. Además, si la carpeta de salida no existe, se creará automáticamente.    |

Al generar un archivo *.intunewin* archivo, coloque los archivos a los que tenga que hacer referencia en una subcarpeta de la carpeta de instalación. Después, utilice una ruta de acceso relativa para hacer referencia al archivo específico que necesita. Por ejemplo:

**Carpeta de origen de la instalación:** *c:\testapp\v1.0*<br>
**Archivo de licencia:** *c:\testapp\v1.0\licenses\license.txt*

Haga referencia al archivo *license.txt* mediante la ruta de acceso relativa *licenses\license.txt*.

## <a name="create-assign-and-monitor-a-win32-app"></a>Crear, asignar y supervisar una aplicación Win32

De forma bastante similar a una aplicación de línea de negocio (LOB), puede agregar una aplicación Win32 a Microsoft Intune. Este tipo de aplicación, lo acostumbran a escribir en la empresa o terceros. En los pasos siguientes se proporcionan instrucciones para ayudarle a agregar una aplicación Windows a Intune.

### <a name="step-1-specify-the-software-setup-file"></a>Paso 1: Especificación del archivo de instalación de software

1.  Inicie sesión en el [Portal de Azure](https://portal.azure.com/).
2.  Seleccione **Todos los servicios** > **Intune**. Intune se encuentra en la sección **Supervisión y administración**.
3.  En el panel **Intune**, seleccione **Aplicaciones cliente** > **Aplicaciones** > **Agregar**.
4.  En el panel de aplicaciones **Agregar**, seleccione **Vista previa de la aplicación Windows (Win32) -** en la lista desplegable.

    ![Captura de pantalla de la hoja Agregar aplicación - Cuadro de lista desplegable Agregar tipo](./media/apps-win32-app-01.png)

### <a name="step-2-upload-the-app-package-file"></a>Paso 2: Carga del archivo de paquete de aplicaciones

1.  En el panel **Agregar aplicación**, seleccione **Archivo del paquete de aplicaciones** para seleccionar un archivo. Se mostrará el panel del archivo del paquete de aplicaciones.

    ![Captura de pantalla de la hoja del archivo del paquete de aplicaciones](./media/apps-win32-app-02.png)

2.  En el panel **Archivo del paquete de aplicaciones**, seleccione el botón Examinar. Después seleccione un archivo de instalación de Windows con la extensión *.intunewin*.
3.  Cuando haya terminado, seleccione **Aceptar**.

### <a name="step-3-configure-app-information"></a>Paso 3: Configuración de información de la aplicación

1.  En el panel **Agregar aplicación**, seleccione **Información de la aplicación** para configurar la aplicación.
2.  En el panel **Información de la aplicación**, configure la información siguiente. Algunos de los valores de este panel podrían rellenarse automáticamente.
    - **Nombre**: escriba el nombre de la aplicación tal como aparece en el portal de empresa. Si el mismo nombre de aplicación existe dos veces, se mostrarán las dos aplicaciones en el portal de empresa.
    - **Descripción**: Escriba una descripción de la aplicación. La descripción aparece en el portal de empresa.
    - **Publicador**: Escriba el nombre del publicador de la aplicación.
    - **Categoría**: seleccione una o varias de las categorías de aplicaciones integradas o seleccione una categoría que haya creado. Las categorías facilitan a los usuarios encontrar la aplicación cuando exploran el portal de empresa.
    - **Mostrar como aplicación destacada en el Portal de empresa**: Muestra la aplicación de forma destacada en la página principal del portal de empresa cuando los usuarios buscan aplicaciones.
    - **Dirección URL de información**: opcionalmente, escriba la dirección URL de un sitio web que contenga información sobre la aplicación. La dirección URL aparece en el portal de empresa.
    - **Dirección URL de privacidad**: opcionalmente, escriba la dirección URL de un sitio web que contenga información de privacidad sobre la aplicación. La dirección URL aparece en el portal de empresa.
    - **Desarrollador**: opcionalmente, escriba el nombre del desarrollador de la aplicación.
    - **Propietario**: opcionalmente, escriba un nombre para el propietario de esta aplicación. Un ejemplo es **Departamento de Recursos Humanos**.
    - **Notas**: escriba las notas que desea asociar a esta aplicación.
    - **Logotipo**: cargue un icono que esté asociado a la aplicación. El icono se muestra con la aplicación cuando los usuarios examinan el portal de empresa.
3.  Cuando haya terminado, seleccione **Aceptar**.

### <a name="step-4-configure-app-installation-details"></a>Paso 4: Configuración de los detalles de instalación de la aplicación
1.  En el panel **Agregar aplicación**, seleccione **Programa** para configurar los comandos de instalación y desinstalación de aplicaciones para la aplicación.
2.  Para instalar la aplicación, agregue la línea de comandos para completar la instalación. 

    Por ejemplo, si el nombre de archivo de la aplicación es **MyApp123**, agregue lo siguiente: `msiexec /i “MyApp123.msi”`

3.  Agregar la línea de comandos de desinstalación completa para desinstalar la aplicación a partir del GUID de la aplicación. 

    Por ejemplo: `msiexec /x “{12345A67-89B0-1234-5678-000001000000}”`

    > [!NOTE]
    > Puede configurar una aplicación Win32 para instalarla en un contexto de **usuario** o **sistema**. El contexto de **usuario** hace referencia a un único usuario determinado. El contexto de **sistema** hace referencia a todos los usuarios de un dispositivo Windows 10.
    >
    > Los usuarios finales no tienen que iniciar sesión en el dispositivo para instalar las aplicaciones Win32.

4.  Cuando haya terminado, seleccione **Aceptar**.

### <a name="step-5-configure-app-requirements"></a>Paso 5: Configuración de los requisitos de la aplicación

1.  En el panel **Agregar aplicación**, seleccione **Requisitos** para configurar los requisitos que deben cumplir los dispositivos para que se pueda instalar la aplicación.
2.  En el panel **Requisitos**, configure la siguiente información. Algunos de los valores de este panel podrían rellenarse automáticamente.
    - **Arquitectura del sistema operativo**: elija las arquitecturas necesarias para instalar la aplicación.
    - **Versión mínima del sistema operativo**: seleccione el sistema operativo necesario para instalar la aplicación.
    - **Espacio en disco necesario (MB)**: también puede agregar el espacio libre en disco necesario en la unidad del sistema para instalar la aplicación.
    - **Memoria física requerida (MB)**: también puede agregar la memoria física (RAM) necesaria para instalar la aplicación.
    - **Número mínimo de procesadores lógicos necesarios**: también puede agregar el número mínimo de procesadores lógicos necesarios para instalar la aplicación.
    - **Velocidad de CPU mínima requerida (MHz)**: opcionalmente, puede agregar la velocidad de CPU mínima necesaria para instalar la aplicación.
3.  Cuando haya terminado, seleccione **Aceptar**.

### <a name="step-6-configure-app-detection-rules"></a>Paso 6: Configuración de reglas de detección de aplicaciones

1.  En el panel **Agregar aplicación**, seleccione **Reglas de detección** para configurar las reglas para detectar la presencia de la aplicación.
2.  En **Formato de las reglas**, seleccione cómo se detectará la presencia de la aplicación. Puede optar por configurar manualmente las reglas de detección o por usar un script personalizado para detectar la presencia de la aplicación. Debe elegir una regla de detección como mínimo. 

    > [!NOTE]
    > En el panel **Reglas de detección**, puede agregar varias reglas. Deben cumplirse las condiciones de **todas** las reglas para detectar la aplicación.

    - **Configurar manualmente las reglas de detección**: puede seleccionar uno de los siguientes tipos de regla:
        1.  **MSI**: compruébelo en función de la comprobación de versión de MSI. Esta opción solo puede agregarse una vez. Al elegir este tipo de regla, tiene dos opciones:
            - **Código de producto MSI**: agregue un código de producto MSI válido para la aplicación.
            - **Comprobación de versión del producto MSI**: seleccione **Sí** para que se compruebe la versión de producto MSI además del código de producto MSI.
        2.  **Archivo**: compruébelo en función de la fecha, la versión, el tamaño o la detección de la carpeta o del archivo.
            - **Ruta de acceso**: la ruta de acceso completa de la carpeta que contiene el archivo o la carpeta que se tiene que detectar.
            - **Archivo o carpeta**: el archivo o la carpeta que se va a detectar.
            - **Método de detección**: seleccione el tipo de método de detección utilizado para validar la presencia de la aplicación.
            - **Asociado con una aplicación de 32 bits en clientes de 64 bits**: seleccione **Sí** para expandir las variables de entorno de ruta de acceso en el contexto de 32 bits en clientes de 64 bits. Seleccione **No** (valor predeterminado) para expandir cualquier variable de ruta de acceso en el contexto de 64 bits en clientes de 64 bits. Los clientes de 32 bits siempre usan el contexto de 32 bits.
            
            **Ejemplos de detección basada en archivos**
            1.  Compruebe que el archivo existe.
         
                ![Captura de pantalla del panel Regla de detección - Existencia del archivo](./media/apps-win32-app-03.png)
        
            2.  Compruebe que la carpeta existe.
         
                ![Captura de pantalla del panel Regla de detección - Existencia de la carpeta](./media/apps-win32-app-04.png)
        
        3. **Registro**: comprobación basada en el valor, la cadena, el entero o la versión.
            - **Ruta de acceso clave**: la ruta de acceso completa de la entrada del registro que contiene el valor que se va a detectar.
            - **Nombre del valor**: nombre del valor del registro que se va a detectar. Si este valor está vacío, la detección se realizará en la clave. El valor (predeterminado) de una clave se usará como valor de detección si el método de detección no es la existencia del archivo o de la carpeta.
            - **Método de detección**: seleccione el tipo de método de detección utilizado para validar la presencia de la aplicación.
            - **Asociado con una aplicación de 32 bits en clientes de 64 bits**: seleccione **Sí** para buscar el registro de 32 bits en clientes de 64 bits. Seleccione **No** (valor predeterminado) para buscar el registro de 64 bits en clientes de 64 bits. Los clientes de 32 bits siempre buscan el registro de 32 bits.
            
            **Ejemplos para la detección basada en registros**
            1.  Compruebe que la clave del registro existe.
            
                ![Captura de pantalla del panel Regla de detección - la clave del registro existe](./media/apps-win32-app-05.png)    
            
            2.  Compruebe que el valor del registro existe (**no está disponible en versión preliminar**).
        
                ![Captura de pantalla del panel Regla de detección - el valor del registro existe](./media/apps-win32-app-06.png)    
        
            3.  Compruebe si la cadena de valores de registro son iguales.
        
                ![Captura de pantalla del panel Regla de detección - la cadena del valor del registro es igual](./media/apps-win32-app-07.png)    
     
    - **Usar un script de detección personalizada**: especifique el script de PowerShell que se usará para detectar esta aplicación. 
    
        1.  **Archivo de script**: seleccione un script de PowerShell que detectará la presencia de la aplicación en el cliente. La aplicación se detectará cuando el script devuelva un código de salida del valor 0 y escriba un valor de cadena en STDOUT.

        2.  **Ejecutar script como proceso de 32 bits en clientes de 64 bits**: seleccione **Sí** para ejecutar el script en un proceso de 32 bits en clientes de 64 bits. Seleccione **No** (valor predeterminado) para ejecutar el script en un proceso de 64 bits en clientes de 64 bits. Los clientes de 32 bits ejecutan el script en un proceso de 32 bits.

        3.  **Exigir la comprobación de firma del script**: seleccione **Sí** para comprobar si el script está firmado por un editor de confianza. Esto permitirá que el script se ejecute sin mostrar advertencias ni mensajes. El script se ejecutará desbloqueado. Seleccione **No** (valor predeterminado) para ejecutar el script con una confirmación del usuario final sin comprobación de firmas.
    
            El agente de Intune comprueba los resultados del script. Lee los valores escritos por el script en la secuencia de salida estándar (STDOUT), la secuencia de error estándar (STDERR) y el código de salida. Si el script sale con un valor distinto de cero, se produce un error en el script y el estado de detección de la aplicación es no instalada. Si el código de salida es cero y STDOUT contiene datos, el estado de detección de la aplicación es Instalada. 

            > [!NOTE]
            > Cuando el script existe con el valor de 0, significa que el script se ha ejecutado correctamente. El segundo canal de salida indica que se ha detectado la aplicación: los datos de STDOUT indican que la aplicación se encontró en el cliente. No buscamos una cadena concreta de STDOUT.

        4.  Después de agregar las reglas, seleccione **Agregar** > **Aceptar**.

### <a name="step-7-configure-app-return-codes"></a>Paso 7: Configuración de los códigos de retorno de la aplicación

1.  En el panel **Agregar aplicación**, seleccione **Códigos de retorno** para agregar los códigos de retorno que se usan para especificar el comportamiento de reintento de instalación de la aplicación o el comportamiento posterior a la instalación. Las entradas del código de retorno se agregan de forma predeterminada durante la creación de la aplicación. En cambio, puede agregar códigos de retorno adicionales o cambiar los códigos de retorno existentes. 
2.  En el panel **Códigos de retorno**, agregue códigos de retorno adicionales o modifique los existentes.
    - **Error**: valor devuelto que indica un error de instalación de la aplicación.
    - **Reinicio en frío**: el código de retorno del reinicio en frío no permite que se instalen más aplicaciones Win32 en el cliente sin llevar a cabo un reinicio. 
    - **Reinicio en caliente**: el código de retorno del reinicio en caliente permite que la siguiente aplicación Win32 se instale sin que el cliente se tenga que reiniciar. Es necesario llevar a cabo un reinicio para completar la instalación de la aplicación actual.
    - **Reintento**: el código de retorno de reintento intentará instalar la aplicación tres veces, esperando 5 minutos entre un intento y el siguiente. 
    - **Correcto**: el valor devuelto que indica que la aplicación se ha instalado correctamente.
3.  Seleccione **Aceptar** cuando haya agregado o modificado la lista de códigos de retorno.

### <a name="step-8-add-the-app"></a>Paso 8: Agregar la aplicación

1.  En el panel **Agregar aplicación**, compruebe que ha configurado correctamente la información de la aplicación.
2.  Seleccione **Agregar** para cargar la aplicación en Intune.

### <a name="step-9-assign-the-app"></a>Paso 9: Asignación de la aplicación

1.  En el panel de la aplicación, seleccione **Asignaciones**.
2.  Seleccione **Agregar grupo** para abrir el panel **Agregar grupo** que está relacionado con la aplicación.
3.  Para la aplicación específica, seleccione un **tipo de asignación**:
    - **Disponible para dispositivos inscritos**: los usuarios instalan la aplicación desde la aplicación o el sitio web del Portal de empresa.
    - **Requerido**: la aplicación se instala en los dispositivos de los grupos seleccionados.
    - **Desinstalar**: la aplicación se desinstala de dispositivos de los grupos seleccionados.
4.  Seleccione **Grupos incluidos** y asigne los grupos que usarán esta aplicación.
5.  En el panel **Asignar**, seleccione **Aceptar** para completar la selección de grupos incluidos.
6.  Si quiere excluir algún grupo de usuarios para que no se vea afectado por esta asignación de aplicaciones, seleccione **Excluir grupos**.
7.  En el panel **Agregar grupo**, seleccione **Aceptar**.
8.  En el panel **Asignaciones** de la aplicación, seleccione **Guardar**.

En este momento ha completado los pasos para agregar una aplicación Win32 a Intune. Para obtener información sobre la supervisión y la asignación de aplicaciones, vea [Asignación de aplicaciones a grupos con Microsoft Intune](https://docs.microsoft.com/intune/apps-deploy) y [Supervisión de información y asignaciones de aplicaciones con Microsoft Intune](https://docs.microsoft.com/intune/apps-monitor).

## <a name="delivery-optimization"></a>Optimización de entrega

Los clientes Windows 10 RS3 y versiones posterior descargarán contenido de aplicaciones Win32 de Intune mediante un componente de Optimización de distribución del cliente Windows 10. La Optimización de distribución proporciona la funcionalidad punto a punto está activada de manera predeterminada. La Optimización de distribución se puede configurar según la directiva de grupo y, en el futuro, a través de MDM de Intune. Para más información, consulte el artículo sobre la [Optimización de distribución para Windows 10](https://docs.microsoft.com/windows/deployment/update/waas-delivery-optimization). 

## <a name="install-required-and-available-apps-on-devices"></a>Instalar aplicaciones obligatorias y disponibles en dispositivos

El usuario final verá las notificaciones del sistema de Windows en las instalaciones de aplicaciones obligatorias y disponibles. En la siguiente imagen se muestra una notificación del sistema de ejemplo donde la instalación de la aplicación no finaliza hasta que se reinicia el dispositivo. 

![Captura de pantalla de notificaciones del sistema de Windows para la instalación de una aplicación](./media/apps-win32-app-08.png)    

La siguiente imagen notifica al usuario final que se están realizando cambios de la aplicación en el dispositivo.

![Captura de pantalla que notifica al usuario que se están realizando cambios en la aplicación](./media/apps-win32-app-09.png)    

## <a name="toast-notifications-for-win32-apps"></a>Notificaciones del sistema para aplicaciones Win32 
Si es necesario, puede suprimir notificaciones del sistema para el usuario final por asignación de aplicaciones. En Intune, seleccione **Aplicaciones cliente** > **Aplicaciones** > seleccione la aplicación > **Asignaciones** > **Incluir grupos**. 

## <a name="troubleshoot-win32-app-issues"></a>Solucionar los problemas de aplicaciones Win32
Normalmente los registros de agente en el equipo cliente se encuentran en `C:\ProgramData\Microsoft\IntuneManagementExtension\Logs`. Puede aprovechar `CMTrace.exe` para ver estos archivos de registro. *CMTrace.exe* se puede descargar en las [herramientas de cliente de SCCM](https://docs.microsoft.com/sccm/core/support/tools). 

![Captura de pantalla de los registros del agente en el equipo cliente](./media/apps-win32-app-10.png)    

### <a name="troubleshooting-areas-to-consider"></a>Áreas de la solución de problemas para tener en cuenta
- Compruebe la orientación para asegurarse de que el agente está instalado en el dispositivo. Si una aplicación Win32 o PowerShell se orientan a un grupo, se creará una directiva de instalación del agente para el grupo de seguridad.
- Compruebe la versión del sistema operativo: Windows 10 1607 y versiones posteriores.  
- Compruebe que Windows 10 SKU, Windows 10 S o las versiones de Windows que se ejecutan con el modo S habilitado no admiten la instalación de MSI.

## <a name="next-steps"></a>Pasos siguientes

- Para obtener más información sobre agregar aplicaciones en Intune, vea [Incorporación de aplicaciones a Microsoft Intune](apps-add.md).
