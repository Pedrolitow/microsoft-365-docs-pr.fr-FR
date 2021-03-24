---
title: Rôles personnalisés pour le contrôle d’accès basé sur un rôle
description: Découvrez comment gérer des rôles personnalisés dans le Centre de sécurité Microsoft 365
keywords: access, permissions, MTP, Microsoft Threat Protection, M365, security, MCAS, MDATP, Cloud App Security, Microsoft Defender Advanced Threat Protection, scope, scoping, RBAC, roles-based access, custom roles-based access, roles-based auth, RBAC in MDO, roles, rolegroups, permissions inheritance, fine-grained permissions
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 17d55a434cc0499b9b24039f19ec7ed3c94310e8
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51056634"
---
# <a name="custom-roles-in-role-based-access-control-for-microsoft-365-defender"></a>Rôles personnalisés dans le contrôle d’accès basé sur les rôles pour Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**

- Microsoft 365 Defender
 
Deux types de rôles peuvent être utilisés pour accéder à Microsoft 365 Defender :
- **Rôles Azure Active Directory (AD) globaux**
- **Rôles personnalisés**

L’accès à Microsoft 365 Defender peut être géré collectivement à l’aide de rôles globaux [dans Azure Active Directory (AAD)](m365d-permissions.md)

Si vous avez besoin de plus de flexibilité et de contrôle sur l’accès à des données de produit spécifiques, l’accès à Microsoft 365 Defender peut également être géré avec la création de rôles personnalisés via chaque portail de sécurité respectif.  

Par exemple, un rôle personnalisé créé via Microsoft Defender pour point de terminaison autoriserait l’accès aux données de produit pertinentes, y compris aux données de point de terminaison dans le Centre de sécurité Microsoft 365. De même, un rôle personnalisé créé par le biais de Microsoft Defender pour Office 365 autoriserait l’accès aux données de produit pertinentes, y compris aux données de collaboration des & de messagerie dans le Centre de sécurité Microsoft 365.

Les utilisateurs ayant des rôles personnalisés existants peuvent accéder aux données du Centre de sécurité Microsoft 365 en fonction de leurs autorisations de charge de travail existantes, sans configuration supplémentaire requise.

## <a name="create-and-manage-custom-roles"></a>Créer et gérer des rôles personnalisés
Les rôles et autorisations personnalisés peuvent être créés et gérés individuellement via chacun des portails de sécurité suivants : 

- Microsoft Defender pour le point de terminaison : [modifier les rôles dans Microsoft Defender pour le point de terminaison](../defender-endpoint/user-roles.md)
- Microsoft Defender pour Office 365 : [autorisations](../defender-365-security/permissions-in-the-security-and-compliance-center.md?preserve-view=true&view=o365-worldwide) dans le Centre de sécurité & conformité
- Microsoft Cloud App Security : gérer [l’accès administrateur](/cloud-app-security/manage-admins)

Chaque rôle personnalisé créé via un portail individuel permet d’accéder aux données du portail produit approprié. Par exemple, un rôle personnalisé créé via Microsoft Defender pour le point de terminaison autorise uniquement l’accès à Defender pour les données de point de terminaison.

> [!TIP]
> Les autorisations et les rôles sont également accessibles via le Centre de sécurité Microsoft 365 en sélectionnant Autorisations & rôles dans le volet de navigation. L’accès à Microsoft Cloud App Security (MCAS) est géré via le portail MCAS et contrôle également l’accès à Microsoft Defender pour l’identité.  Voir [Microsoft Cloud App Security](/cloud-app-security/manage-admins)

> [!NOTE]
> Les rôles personnalisés créés dans Microsoft Cloud App Security ont également accès aux données Microsoft Defender pour l’identité. Les utilisateurs ayant des rôles d’administrateur de groupe d’utilisateurs ou d’administrateur d’applications/instances Microsoft Cloud App Security ne peuvent pas accéder aux données Microsoft Cloud App Security via le Centre de sécurité Microsoft 365.

## <a name="manage-permissions-and-roles-in-the-microsoft-365-security-center"></a>Gérer les autorisations et les rôles dans le Centre de sécurité Microsoft 365
Les autorisations et les rôles peuvent également être gérés dans le Centre de sécurité Microsoft 365 :

1. Connectez-vous au Centre de sécurité Microsoft 365 security.microsoft.com.
2. Dans le volet de navigation, sélectionnez **Autorisations & rôles.**
3. Sous **l’en-tête Autorisations,** sélectionnez **Rôles.**

> [!NOTE]
> Cela s’applique uniquement à Defender pour Office 365 et Defender pour point de terminaison. L’accès aux autres charges de travail doit être effectué dans leurs portails appropriés.


## <a name="required-roles-and-permissions"></a>Rôles et des autorisations requis
Le tableau suivant décrit les rôles et les autorisations requis pour accéder à chaque expérience unifiée dans chaque charge de travail. Les rôles définis dans le tableau ci-dessous font référence à des rôles personnalisés dans des portails individuels et ne sont pas connectés à des rôles globaux dans Azure AD, même s’ils sont nommés de la même manière.

> [!NOTE]
> La gestion des incidents nécessite des autorisations de gestion pour tous les produits qui font partie de l’incident.
 
| **L’un des rôles suivants est requis pour Microsoft 365 Defender**  | **L’un des rôles suivants est requis pour Defender for Endpoint**  | **L’un des rôles suivants est requis pour Defender pour Office 365** | **L’un des rôles suivants est requis pour Cloud App Security** | 
|---------|---------|---------|---------|
| Affichage des données d’examen : <ul><li>Page d’alerte</li> <li>File d’attente des alertes</li> <li>Incidents</li>  <li>File d’attente des incidents</li> <li>Centre de notifications</li></ul>| Afficher les opérations de sécurité des données | <ul><li>Gérer les alertes en affichage seul </li> <li>Configuration de l'organisation</li><li>Journaux d'audit</li> <li>Afficher uniquement les journaux d’audit</li> <li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires en affichage seul</li></ul>  | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Affichage des données de recherche | Afficher les opérations de sécurité des données | <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li> <li>Destinataires en affichage seul</li> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Gestion des alertes et des incidents | Examen des alertes | <ul><li>Gérer les alertes</li> <li>Administrateur de la sécurité</li> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li></ul> |
| Correction du centre de mise à jour | Actions de correction actives : opérations de sécurité | Rechercher et purger | |
| Définition de détections personnalisées | Gérer les paramètres de sécurité |<ul><li>Gérer les alertes</li> <li>Administrateur de la sécurité</li></ul> | <ul><li>Administrateur global</li> <li>Administrateur de la sécurité</li> <li>Administrateur de mise en conformité</li> <li>Opérateur de sécurité</li> <li>Lecteur Sécurité</li> <li>Lecteur général</li></ul> |
| Analyses de menaces | Données sur les alertes et les incidents : <ul><li>Afficher les opérations de sécurité des données</li></ul>Atténuations TVM :<ul><li>Afficher les données : gestion des menaces et des vulnérabilités</li></ul> | Données sur les alertes et les incidents :<ul> <li>Gérer les alertes en affichage seul</li> <li>Gérer les alertes</li> <li>Configuration de l'organisation</li><li>Journaux d'audit</li> <li>Afficher uniquement les journaux d’audit</li><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires en affichage seul</li> </ul> Tentatives de courrier électronique empêchées : <ul><li>Lecteur Sécurité</li> <li>Administrateur de la sécurité</li><li>Destinataires en affichage seul</li> | Non disponible pour les utilisateurs MCAS ou MDI |

Par exemple, pour afficher les données de recherche à partir de Microsoft Defender pour le point de terminaison, les autorisations d’opérations de sécurité des données sont requises.  

De même, pour afficher les données de recherche à partir de Microsoft Defender pour Office 365, les utilisateurs doivent avoir l’un des rôles suivants :  

- Afficher les opérations de sécurité des données
- Lecteur Sécurité
- Administrateur de la sécurité
- Destinataires en affichage seul

## <a name="related-topics"></a>Voir aussi
- [Gérer l’accès à Microsoft 365 Defender](m365d-permissions.md)
- [Gérer l’accès administrateur pour MCAS](/cloud-app-security/manage-admins)
