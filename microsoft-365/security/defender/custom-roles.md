---
title: Rôles personnalisés pour le contrôle d’accès basé sur un rôle
description: Découvrez comment gérer des rôles personnalisés dans le portail Microsoft 365 Defender web
keywords: access, permissions, Microsoft 365 Defender, M365, security, MCAS, Sécurité des applications cloud, Microsoft Defender for Endpoint, scope, scoping, RBAC, roles-based access, custom roles-based access, roles-based auth, RBAC in MDO, roles, rolegroups, permissions inheritance, fine-grained permissions
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
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
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 95fa7c4821f28775c78175aa18a413b8cd1928e5
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60174410"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Rôles personnalisés dans le contrôle d’accès basé sur les rôles pour Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**

- Microsoft 365 Defender
 
Il existe deux types de rôles qui peuvent être utilisés pour accéder aux Microsoft 365 Defender :
- **Rôles Azure Active Directory (AD) globaux**
- **Rôles personnalisés**

L’accès aux Microsoft 365 Defender peut être géré collectivement à l’aide de rôles globaux [dans Azure Active Directory (AAD)](m365d-permissions.md)

Si vous avez besoin d’une plus grande flexibilité et d’un contrôle accru sur l’accès à des données de produit spécifiques, l’accès Microsoft 365 Defender peut également être géré avec la création de rôles personnalisés via chaque portail de sécurité respectif.  

Par exemple, un rôle personnalisé créé par le biais de Microsoft Defender pour le point de terminaison autoriserait l’accès aux données de produit pertinentes, y compris les données de point de terminaison dans le portail Microsoft 365 Defender. De même, un rôle personnalisé créé par le biais de Microsoft Defender pour Office 365 autoriserait l’accès aux données de produit pertinentes, y compris les données de collaboration & courrier électronique dans le portail Microsoft 365 Defender.

Les utilisateurs ayant des rôles personnalisés existants peuvent accéder aux données du portail Microsoft 365 Defender en fonction de leurs autorisations de charge de travail existantes, sans qu’aucune configuration supplémentaire ne soit requise.

## <a name="create-and-manage-custom-roles"></a>Créer et gérer des rôles personnalisés
Les rôles et autorisations personnalisés peuvent être créés et gérés individuellement via chacun des portails de sécurité suivants : 

- Microsoft Defender pour le point de terminaison : [modifier les rôles dans Microsoft Defender pour le point de terminaison](../defender-endpoint/user-roles.md)
- Microsoft Defender pour Office 365 : [autorisations](../office-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide) dans le Centre de sécurité & conformité
- Microsoft Cloud App Security : gérer [l’accès administrateur](/cloud-app-security/manage-admins)

Chaque rôle personnalisé créé via un portail individuel permet d’accéder aux données du portail produit approprié. Par exemple, un rôle personnalisé créé via Microsoft Defender pour le point de terminaison autorise uniquement l’accès à Defender pour les données de point de terminaison.

> [!TIP]
> Les autorisations et les rôles sont également accessibles via le portail Microsoft 365 Defender en sélectionnant Autorisations & rôles dans le volet de navigation. L’accès Microsoft Cloud App Security (MCAS) est géré via le portail MCAS et contrôle également l’accès à Microsoft Defender pour l’identité.  Voir [Microsoft Cloud App Security](/cloud-app-security/manage-admins)

> [!NOTE]
> Les rôles personnalisés créés Microsoft Cloud App Security ont également accès aux données Microsoft Defender for Identity. Les utilisateurs ayant des rôles d’administrateur de groupe d’utilisateurs ou d’administrateur d’Microsoft Cloud App Security d’application/d’instance ne peuvent pas accéder aux Microsoft Cloud App Security via le portail Microsoft 365 Defender utilisateur.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-defender-portal"></a>Gérer les autorisations et les rôles dans le portail Microsoft 365 Defender web
Les autorisations et les rôles peuvent également être gérés dans Microsoft 365 Defender portail :

1. Connectez-vous au portail Microsoft 365 Defender à l’security.microsoft.com.
2. Dans le volet de navigation, sélectionnez **Autorisations & rôles.**
3. Sous **l’en-tête Autorisations,** sélectionnez **Rôles.**

> [!NOTE]
> Cela s’applique uniquement à Defender pour Office 365 et Defender pour le point de terminaison. L’accès aux autres charges de travail doit être effectué dans leurs portails appropriés.


## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis
Le tableau suivant décrit les rôles et autorisations requis pour accéder à chaque expérience unifiée dans chaque charge de travail. Les rôles définis dans le tableau ci-dessous font référence à des rôles personnalisés dans des portails individuels et ne sont pas connectés à des rôles globaux dans Azure AD, même s’ils sont nommés de la même manière.

> [!NOTE]
> La gestion des incidents nécessite des autorisations de gestion pour tous les produits qui font partie de l’incident.
 
| **L’un des rôles suivants est requis pour Microsoft 365 Defender**  | **L’un des rôles suivants est requis pour Defender pour endpoint**  | **L’un des rôles suivants est requis pour Defender pour Office 365** | **L’un des rôles suivants est requis pour Sécurité des applications cloud** | 
|---------|---------|---------|---------|
| Affichage des données d’examen : <ul><li>Page d’alerte</li> <li>File d’attente des alertes</li> <li>Incidents</li>  <li>File d’attente des incidents</li> <li>Centre de notifications</li></ul>| Afficher les opérations de sécurité des données | <ul><li>Gérer les alertes en affichage seul </li> <li>Configuration de l'organisation</li><li>Journaux d'audit</li> <li>Afficher uniquement les journaux d’audit</li> <li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires en affichage seul</li></ul>  | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Affichage des données de recherche | Afficher les opérations de sécurité des données | <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li> <li>Destinataires en affichage seul</li> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Gestion des alertes et des incidents | Examen des alertes | <ul><li>Gérer des alertes</li> <li>Administrateur de la sécurité</li> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li></ul> |
| Correction du centre de mise à jour | Actions de correction actives : opérations de sécurité | Rechercher et purger | |
| Définition de détections personnalisées | Gérer les paramètres de sécurité |<ul><li>Gérer des alertes</li> <li>Administrateur de la sécurité</li></ul> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Analyses de menaces | Données sur les alertes et les incidents : <ul><li>Afficher les opérations de sécurité des données</li></ul>Atténuations TVM :<ul><li>Afficher les données : menaces et gestion des vulnérabilités</li></ul> | Données sur les alertes et les incidents :<ul> <li>Gérer les alertes en affichage seul</li> <li>Gérer des alertes</li> <li>Configuration de l'organisation</li><li>Journaux d'audit</li> <li>Afficher uniquement les journaux d’audit</li><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires en affichage seul</li> </ul> Tentatives de courrier électronique empêchées : <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires en affichage seul</li> | Non disponible pour les utilisateurs MCAS ou MDI |

Par exemple, pour afficher les données de recherche à partir de Microsoft Defender pour le point de terminaison, les autorisations d’opérations de sécurité des données sont requises.  

De même, pour afficher les données de recherche de Microsoft Defender Office 365, les utilisateurs doivent avoir l’un des rôles suivants :  

- Afficher les opérations de sécurité des données
- Lecteur Sécurité
- Administrateur de la sécurité
- Destinataires en affichage seul

## <a name="related-topics"></a>Rubriques connexes
- [Gérer l’accès aux Microsoft 365 Defender](m365d-permissions.md)
- [Gérer l’accès administrateur pour MCAS](/cloud-app-security/manage-admins)
