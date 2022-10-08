---
title: Rôles personnalisés pour le contrôle d’accès en fonction du rôle
description: Découvrez comment gérer des rôles personnalisés dans le portail Microsoft 365 Defender
keywords: access, permissions, Microsoft 365 Defender, M365, security, Defender for Cloud Apps, Microsoft Defender pour point de terminaison, scope, scoping, RBAC, role-based access, custom roles-based access, role-based auth, RBAC in MDO, roles, rolegroups, permissions inheritance, fine-grained permissions
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: 446c69b9f62effd1e2248d643afdf58eed3d11d4
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68055543"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Rôles personnalisés dans le contrôle d’accès en fonction du rôle pour Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**

- Microsoft 365 Defender
 
Il existe deux types de rôles qui peuvent être utilisés pour accéder à Microsoft 365 Defender :
- **Rôles Azure Active Directory (AD) globaux**
- **Rôles personnalisés**

L’accès à Microsoft 365 Defender peut être géré collectivement à l’aide de [rôles globaux dans Azure Active Directory (AAD)](m365d-permissions.md)

Si vous avez besoin d’une plus grande flexibilité et d’un contrôle sur l’accès à des données de produit spécifiques, Microsoft 365 Defender accès peut également être géré avec la création de rôles personnalisés via chaque portail de sécurité respectif.  

Par exemple, un rôle personnalisé créé via Microsoft Defender pour point de terminaison autoriserait l’accès aux données de produit pertinentes, y compris les données de point de terminaison dans le portail Microsoft 365 Defender. De même, un rôle personnalisé créé via Microsoft Defender pour Office 365 autoriserait l’accès aux données de produit pertinentes, y compris Email & données de collaboration dans le portail Microsoft 365 Defender.

Les utilisateurs disposant de rôles personnalisés existants peuvent accéder aux données dans le portail Microsoft 365 Defender en fonction de leurs autorisations de charge de travail existantes, sans configuration supplémentaire requise.

## <a name="create-and-manage-custom-roles"></a>Créer et gérer des rôles personnalisés
Les rôles et autorisations personnalisés peuvent être créés et gérés individuellement via chacun des portails de sécurité suivants : 

- Microsoft Defender pour point de terminaison : [modifier les rôles dans Microsoft Defender pour point de terminaison](../defender-endpoint/user-roles.md)
- Microsoft Defender pour Office 365 – [Autorisations dans le Centre de conformité & de sécurité](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide)
- Microsoft Defender for Cloud Apps : [gérer l’accès administrateur](/cloud-app-security/manage-admins)

Chaque rôle personnalisé créé via un portail individuel permet d’accéder aux données du portail de produit approprié. Par exemple, un rôle personnalisé créé via Microsoft Defender pour point de terminaison autorise uniquement l’accès aux données Defender pour point de terminaison.

> [!TIP]
> Les autorisations et les rôles sont également accessibles via le portail Microsoft 365 Defender en sélectionnant Autorisations & rôles dans le volet de navigation. L’accès à Microsoft Defender for Cloud Apps est géré via le portail Defender pour Cloud Apps et contrôle également l’accès à Microsoft Defender pour Identity.  Voir [Microsoft Defender for Cloud Apps](/cloud-app-security/manage-admins)

> [!NOTE]
> Les rôles personnalisés créés dans Microsoft Defender for Cloud Apps ont également accès à Microsoft Defender pour Identity données. Les utilisateurs disposant de rôles d’administrateur de groupe d’utilisateurs ou d’administrateur d’application/instance Microsoft Defender for Cloud Apps ne peuvent pas accéder aux données Microsoft Defender for Cloud Apps via le portail Microsoft 365 Defender.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>Gérer les autorisations et les rôles dans le portail Microsoft 365 Defender
Les autorisations et les rôles peuvent également être gérés dans le portail Microsoft 365 Defender :

1. Connectez-vous au portail Microsoft 365 Defender à security.microsoft.com.
2. Dans le volet de navigation, sélectionnez **Autorisations & rôles.**
3. Sous l’en-tête **Autorisations** , sélectionnez **Rôles**.

> [!NOTE]
> Cela s’applique uniquement à Defender pour Office 365 et Defender pour point de terminaison. L’accès aux autres charges de travail doit être effectué dans leurs portails appropriés.


## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis
Le tableau suivant décrit les rôles et les autorisations nécessaires pour accéder à chaque expérience unifiée dans chaque charge de travail. Les rôles définis dans le tableau ci-dessous font référence à des rôles personnalisés dans des portails individuels et ne sont pas connectés à des rôles globaux dans Azure AD, même s’ils sont également nommés.

> [!NOTE]
> La gestion des incidents nécessite des autorisations de gestion pour tous les produits qui font partie de l’incident.
 
| **L’un des rôles suivants est requis pour Microsoft 365 Defender**  | **L’un des rôles suivants est requis pour Defender pour point de terminaison**  | **L’un des rôles suivants est requis pour Defender pour Office 365** | **L’un des rôles suivants est requis pour Defender pour Cloud Apps** | 
|---------|---------|---------|---------|
| Affichage des données d’investigation : <ul><li>Page d’alerte</li> <li>File d’attente des alertes</li> <li>Incidents</li>  <li>File d’attente d’incidents</li> <li>Centre de notifications</li></ul>| Afficher les opérations de sécurité des données | <ul><li>Gérer les alertes en mode affichage uniquement </li> <li>Configuration de l'organisation</li><li>Journaux d’audit</li> <li>Afficher uniquement les journaux d’audit</li> <li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires d’affichage uniquement</li></ul>  | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Affichage des données de chasse | Afficher les opérations de sécurité des données | <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li> <li>Destinataires d’affichage uniquement</li> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Gestion des alertes et des incidents | Investigation des alertes | <ul><li>Gérer des alertes</li> <li>Administrateur de la sécurité</li> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li></ul> |
| Correction du centre d’actions | Actions de correction actives : opérations de sécurité | Rechercher et vider | |
| Définition de détections personnalisées | Gérer les paramètres de sécurité |<ul><li>Gérer des alertes</li> <li>Administrateur de la sécurité</li></ul> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Analyses de menaces | Données d’alertes et d’incidents : <ul><li>Afficher les opérations de sécurité des données</li></ul>Atténuations de la gestion des vulnérabilités Defender :<ul><li>Afficher les données - Gestion des menaces et des vulnérabilités</li></ul> | Données d’alertes et d’incidents :<ul> <li>Gérer les alertes en mode affichage uniquement</li> <li>Gérer des alertes</li> <li>Configuration de l'organisation</li><li>Journaux d’audit</li> <li>Afficher uniquement les journaux d’audit</li><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires d’affichage uniquement</li> </ul> Tentatives d’e-mail empêchées : <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires d’affichage uniquement</li> | Non disponible pour les utilisateurs Defender pour Cloud Apps ou MDI |

Par exemple, pour afficher les données de chasse à partir de Microsoft Defender pour point de terminaison, des autorisations d’opérations de sécurité des données sont requises.  

De même, pour afficher les données de chasse à partir de Microsoft Defender pour Office 365, les utilisateurs ont besoin de l’un des rôles suivants :  

- Afficher les opérations de sécurité des données
- Lecteur Sécurité
- Administrateur de la sécurité
- Destinataires d’affichage uniquement

## <a name="related-topics"></a>Voir aussi
- [Rôles RBAC](../office-365-security/migrate-to-defender-for-office-365-onboard.md#rbac-roles)
- [Gérer l’accès à Microsoft 365 Defender](m365d-permissions.md)
- [Gérer l’accès administrateur pour Defender pour Cloud Apps](/cloud-app-security/manage-admins)
