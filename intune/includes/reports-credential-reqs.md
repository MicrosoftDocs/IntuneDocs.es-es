<!-- This include is part of the Intune Data Warehouse documentation. -->

## <a name="azure-ad-and-intune-credential-requirements"></a>Requisitos de credenciales de Azure AD e Intune

La autenticación y la autorización se basan en las credenciales de Azure AD y en el control de acceso basado en roles (RBAC) de Intune. Todos los administradores globales y los administradores de servicios de Intune del inquilino tienen acceso al Almacén de datos de forma predeterminada. Use los roles de Intune para proporcionar acceso a más usuarios. Para ello, concédales acceso al **recurso de informes**.

Los requisitos para acceder al Almacén de datos de Intune (incluida la API) son:

  -  El usuario debe tener asignada una licencia de Intune.
  -  El usuario debe ser uno de los siguientes:
      -  Un administrador global de Azure AD.
      -  Un administrador del servicio de Intune.
      -  Un usuario con acceso basado en roles al recurso de **informes**.