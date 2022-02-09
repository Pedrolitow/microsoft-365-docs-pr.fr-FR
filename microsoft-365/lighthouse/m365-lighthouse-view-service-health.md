---
title: Afficher l’état du service client
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment afficher l’état du service client.
ms.openlocfilehash: b7361865e0ad3f070e128207a92669f3515e9969
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62466148"
---
# <a name="view-tenant-service-health"></a>Afficher l’état du service client

> [!NOTE]
> Les fonctionnalités décrites dans cet article sont en prévisualisation, peuvent faire l’objet de changements et sont uniquement disponibles pour les partenaires qui répondent aux [exigences](m365-lighthouse-requirements.md). Si votre organisation n’a pas Microsoft 365 Lighthouse, [consultez s’inscrire pour Microsoft 365 Lighthouse](m365-lighthouse-sign-up.md).

Vous pouvez afficher l’état du service pour les clients que vous gérez dans Microsoft 365 Lighthouse. L’état du service inclut des incidents et des conseils pour plusieurs services, notamment Microsoft Intune, les services d’identité Azure Active Directory (Azure AD) et les services cloud de gestion des périphériques mobiles (MDM). Vous pouvez également voir combien de vos locataires gérés sont affectés par des incidents. Par exemple, si l’un de vos clients rencontre des problèmes, vous pouvez consulter la page État du service pour déterminer s’il s’agit d’un problème connu avec une résolution en cours ou si une modification récente peut les avoir impacté. Cela peut vous faire gagner du temps lors de la résolution des problèmes et réduire les appels de support.

Si vous ne pouvez pas vous connecter à l’organisation, vous pouvez utiliser la page état d’état du [service Microsoft 365](https://status.office365.com/) pour vérifier si des problèmes connus vous empêchent de vous connecter à votre client partenaire. En outre, inscrivez-vous pour suivre [@MSFT365status](https://twitter.com/MSFT365Status) sur Twitter pour voir des informations sur des incidents de service spécifiques.

## <a name="before-you-begin"></a>Avant de commencer

Pour afficher l’état du service, vous aurez besoin d’un rôle Azure AD dans le client partenaire avec l’ensemble de propriétés suivant : **microsoft.office365.serviceHealth/allEntities/allTasks**. Pour obtenir la liste des rôles Azure AD, voir [Azure AD rôles intégrés](/azure/active-directory/roles/permissions-reference).

## <a name="view-service-health-status-for-all-tenants"></a>Afficher l’état d’état du service pour tous les clients

1. Dans le volet de navigation gauche de l’écran, sélectionnez **État du service**.

2. Dans la page **État du service** , examinez l’état actuel du service, notamment :

   -   Nombre total d’incidents
   -   Nombre total d’avis affectant l’un des locataires gérés
   -   Nombre de services avec incidents actifs.

3. Sous **l’onglet Tous les services** , examinez les problèmes par service.

4. Sous **l’onglet Tous les problèmes** , examinez tous les problèmes actuels.

## <a name="review-issue-details"></a>Examiner les détails du problème

1. Dans le volet de navigation gauche de l’écran, sélectionnez **État du service**.

2. Dans la page **État du service** , sélectionnez l’onglet **Tous les services** ou **Tous les problèmes** .

3. Sélectionnez un problème dans la liste.

4. Dans le volet d’informations sur les problèmes, examinez des informations détaillées, notamment le type de problème, les locataires affectés, l’impact sur l’utilisateur et l’historique des problèmes.

Sous **l’onglet Locataires affectés** , vous pouvez exporter une liste de locataires affectés vers un fichier de valeurs séparées par des points communs (.cvs) afin de pouvoir le partager avec vos équipes de support technique.

## <a name="related-content"></a>Contenu associé
[Comment vérifier l’état Microsoft 365 service](/microsoft-365/enterprise/view-service-health) (article)
