---
title: Afficher l’intégrité du service client dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: chboyd
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment afficher l’intégrité du service client.
ms.openlocfilehash: 968cea20e26a2b15bceb7cb28474e65e96a6afc0
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67590741"
---
# <a name="view-tenant-service-health-in-microsoft-365-lighthouse"></a>Afficher l’intégrité du service client dans Microsoft 365 Lighthouse

Vous pouvez afficher l’intégrité du service pour les locataires que vous gérez dans Microsoft 365 Lighthouse. État des services inclut des incidents et des conseils pour plusieurs services, notamment Microsoft Intune, les services d’identité Azure Active Directory (Azure AD) et les services cloud de gestion des appareils mobiles (GPM). Vous pouvez également voir combien de vos locataires gérés sont affectés par des incidents. Par exemple, si l’un de vos locataires rencontre des problèmes, vous pouvez consulter la page État des services pour déterminer s’il s’agit d’un problème connu avec une résolution en cours ou si une modification récente peut les affecter. Cela peut vous faire gagner du temps pour résoudre les problèmes et réduire les appels de support.

Si vous ne pouvez pas vous connecter à Lighthouse, vous pouvez utiliser la [page d’état d’intégrité du service Microsoft 365](https://status.office365.com/) pour rechercher les problèmes connus qui vous empêchent de vous connecter à votre locataire partenaire. En outre, inscrivez-vous pour suivre [@MSFT365status](https://twitter.com/MSFT365Status) sur Twitter pour voir des informations sur des incidents de service spécifiques.

## <a name="before-you-begin"></a>Avant de commencer

Pour afficher l’intégrité du service, vous avez besoin d’un rôle Azure AD dans le locataire partenaire avec l’ensemble de **propriétés suivant : microsoft.office365.serviceHealth/allEntities/allTasks**. Pour obtenir la liste des rôles Azure AD, consultez [les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Afficher l’état d’intégrité du service pour tous les locataires

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **État des services**.

2. Dans la page **État des services**, passez en revue l’état d’intégrité actuel du service, notamment :

   - Nombre total d’incidents
   - Nombre total d’avis affectant l’un des locataires gérés
   - Nombre de services avec des incidents actifs.

3. Sous l’onglet **Tous les services** , passez en revue les problèmes par service.

4. Sous l’onglet **Tous les problèmes** , passez en revue tous les problèmes actuels.

## <a name="review-issue-details"></a>Examiner les détails du problème

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **État des services**.

2. Dans la page **État des services**, sélectionnez l’onglet **Tous les services** ou **Tous les problèmes**.

3. Sélectionnez un problème dans la liste.

4. Dans le volet détails du problème, passez en revue les informations détaillées, notamment le type de problème, les locataires affectés, l’impact sur l’utilisateur et l’historique des problèmes.

Sous l’onglet **Locataires affectés** , vous pouvez exporter une liste de locataires affectés vers un fichier de valeurs séparées par des virgules (.csv) afin de pouvoir la partager avec vos équipes de support technique.

## <a name="related-content"></a>Contenu associé

[Comment vérifier l’intégrité du service Microsoft 365](/microsoft-365/enterprise/view-service-health) (article)\
[Problèmes connus avec Microsoft 365 Lighthouse](m365-lighthouse-known-issues.md) (article)\
[Afficher vos rôles Azure Active Directory dans Microsoft 365 Lighthouse](m365-lighthouse-view-your-roles.md) (article)
