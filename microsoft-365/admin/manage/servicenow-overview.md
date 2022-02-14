---
title: Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide de configuration et d’installation d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: 0629b322a52702ef293ff1f73661359b410f2d69
ms.sourcegitcommit: 355ab75eb7b604c6afbe9a5a1b97ef16a1dec4fc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/14/2022
ms.locfileid: "62806011"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow

**Microsoft 365'intégration du support** technique vous permet d’intégrer Microsoft 365 aide, de support et d’état du service à vos instances ServiceNow. Vous pouvez effectuer des recherches sur les problèmes connus et signalés par Microsoft, résoudre les incidents, effectuer des tâches à l’aide de solutions recommandées par Microsoft et, si nécessaire, faire appel au support technique de Microsoft.

Pour obtenir la **Microsoft 365 l’application de prise** en charge de l’intégration à partir du magasin ServiceNow, go to the [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Principales fonctionnalités

Voici les principales fonctionnalités que vous obtenez avec l’application d’intégration Microsoft 365 support technique dans votre instance ServiceNow :

- Incidents d’état du service : informations sur les incidents connus d’état du service Microsoft, notamment l’impact sur l’utilisateur, l’étendue, l’état actuel et la prochaine mise à jour attendue. À l’aide de l’apprentissage automatique, les incidents ServiceNow sont en correspondance avec les incidents d’état du service Microsoft en fonction du champ de description courte.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="Champ de description Incidents d’état du service.":::

- Solutions recommandées : des descriptions des tâches et des incidents sont utilisées pour recommander des solutions ciblées précises et des articles pertinents de Microsoft optimisés par l’apprentissage automatique. Vous pouvez également utiliser la recherche pour rechercher d’autres solutions, si nécessaire.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="Champ description des solutions recommandées.":::

- Demande de service Microsoft : faire resserrez les problèmes aux agents du support Microsoft et recevez des mises à jour d’état pour votre cas.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="Formulaire de demande de service.":::

## <a name="prerequisites"></a>Configuration requise

### <a name="permissions-requirements"></a>Conditions requises pour les autorisations

Pour poursuivre avec ce guide, assurez-vous que les autorisations suivantes sont disponibles et configurées pour vos environnements pendant tout le processus :

- Azure Active Directory (AAD) qui peut créer des applications Azure AD

- Administrateur ServiceNow

- Microsoft 365 client

### <a name="configuration-highlights"></a>Points forts de la configuration

Pour configurer Microsoft 365 **l’intégration :**

- Inscrivez des applications dans Microsoft Azure Active Directory (AAD) pour l’authentification des appels d’API entrants et sortants.

- Créez des entités ServiceNow avec Microsoft Azure AD Application pour le flux de données sortant et entrant.

- Intégrez l’instance ServiceNow au support Microsoft par le biais Microsoft 365 portail d’administration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="Diagramme d’intégration ServiceNow.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>Dépendances d’application dans vos environnements ServiceNow

Autorisations requises :

- oauthentity\_

- oauthentityprofile\_\_

Une fois l Microsoft 365'application d’intégration de support technique installée, deux accès d’étendues croisées d’applications sont créés. Si elles ne sont pas créées correctement, créez-les manuellement.

## <a name="what-configuration-is-right-for-your-organization"></a>Quelle est la configuration qui est la bonne pour votre organisation ?

Avant de configurer une configuration pour Microsoft 365 l’intégration, comprenez comment votre environnement ServiceNow est installé.

- Si votre environnement ServiceNow autorise l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants, suivez les instructions de la procédure [Set up Microsoft 365 pour](servicenow-basic-authentication.md) prendre en charge l’intégration avec l’authentification de base ServiceNow.
- Si votre environnement ServiceNow n’autorise PAS l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants, suivez les instructions de la procédure [Set up Microsoft 365 support integration with Azure AD Auth Token](servicenow-aad-oauth-token.md).
  - Cette configuration nécessite un client DSO pour que le jeton AAD auth fonctionne correctement.

Pour comprendre chaque fonctionnalité, consultez la [Microsoft 365 l’intégration](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).
