---
title: Détails du client Azure Active Directory
description: Cette rubrique décrit les modifications apportées à votre compte AAD lors de l’inscription dans le bureau géré Microsoft
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.openlocfilehash: 6b2b30d8dedba1086bfa9268fb0fdbce20367c20
ms.sourcegitcommit: dd426c686b52cf79325f11022b2d99bc45285577
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2019
ms.locfileid: "35643945"
---
# <a name="azure-active-directory-tenant-details"></a>Détails du client Azure Active Directory
{Gory détails sur les comptes, les appels d’API, les perms, etc., etc.}


## <a name="data-transmitted-to-and-from-your-aad-account"></a>Données transmises vers et à partir de votre compte AAD


Données envoyées à votre compte à partir de Microsoft:

- Noms de groupes
- Configuration de la stratégie de sécurité
- Commandes de l’appareil
- Comptes d’utilisateur (msadmin, MSTest, mwaas_soc_ro, mwaas_wdgsoc)
- Affectation de licences E5 aux comptes d’utilisateurs
- Stratégies de mise à jour Windows pour les sonneries de mise à jour

Données envoyées à Microsoft à partir de votre compte:

- Données de mise à jour des périphériques, d’utilisation et de fiabilité
- Données de fiabilité et de déploiement d’application
- Mise à jour et données de déploiement de stratégie de sécurité
- Utilisateurs affectés aux appareils  

Les données transmises à partir de votre compte sont stockées dans des bases de données SQL Azure dans le client Microsoft hébergé aux États-Unis. Les données sont stockées et gérées conformément aux stratégies décrites dans {Microsoft Azure Security}. 

## <a name="api-permissions-and-calls"></a>Autorisations et appels d’API

**Lors de l’enregistrement:**

Autorisations d’API:
- DeviceManagementServiceConfig.ReadWrite.All
- Directory.AccessAsUser.All
- User.ReadWrite.All
- DeviceManagementConfiguration.ReadWrite.All
- DeviceManagementManagedDevices.ReadWrite.All
- Group.ReadWrite.All

Appels d’API:
- POST/organization/{organizationId}/setMobileDeviceManagementAuthority
- GET/POST/directoryRoles/{id}/members
- GET/POST/Users
- GET/POST/Groups
- CORRECTIF/Groups/{ID}
- GET/POST/deviceManagement/deviceConfigurations
- OBTENIR/deviceManagement/detectedApps

**Après l’enregistrement, lors de la gestion ordinaire:**

Autorisations d’API:
- DeviceManagementManagedDevices.ReadWrite.All
- DeviceManagementApps.ReadWrite.All
- DeviceManagementConfiguration.ReadWrite.All
- Reports.Read.All
- User.ReadWrite.All
- Group.ReadWrite.All
- Directory.AccessAsUser.All

Appels d’API:
- GET/POST/directoryRoles/{id}/members
- GET/PATCH/POST/Users
- GET/POST/Groups
- CORRECTIF/Groups/{ID}
- GET/POST/deviceManagement/deviceConfigurations
- GET/POST/deviceAppManagement/mobileApps
- OBTENIR/deviceManagement/detectedApps
- OBTENIR/Devices
- POST/Users/{ID | userPrincipalName}/assignLicense
- OBTENIR/subscribedSkus

## <a name="accounts-used-by-microsoft-managed-desktop"></a>Comptes utilisés par le bureau géré Microsoft





| Compte | Description  | Accès conditionnel  | 	Authentification multifacteur  | Pourquoi cela est-il correct? |
|---------|---------|---------|---------|--------------|
| msadmin @ * onmmicrosoft. com | Compte de service limité avec des privilèges d’administrateur, utilisé en tant qu’utilisateur Microsoft Intune et administrateur d’utilisateurs {qu’est-ce que c’est?} pour définir et configurer le client pour les appareils de bureau modernes Microsoft.Ne dispose pas d’autorisations de connexion interactive; effectue des opérations uniquement via le service.  | Exclus, car il ne provient pas de votre réseau        | Exclu car il n’existe aucune ouverture de session interactive        | Mot de passe stocké dans Azure Key Vault |
| MSTest @ * onmmicrosoft. com     |         |         |         |
| mssupport @ * onmmicrosoft. com     |         |         |         |
| msadminint @ * onmmicrosoft. com     |         |         |         |
