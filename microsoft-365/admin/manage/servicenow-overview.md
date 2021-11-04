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
ms.openlocfilehash: 28b156cc9f9062863868550f2aac216b8d92a403
ms.sourcegitcommit: dc26169e485c3a31e1af9a5f495be9db75c49760
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/04/2021
ms.locfileid: "60754198"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow

**Microsoft 365 prise** en charge intégrée vous permet d’intégrer Microsoft 365 aide, de support et d’état du service à vos instances ServiceNow. Vous pouvez effectuer des recherches sur les problèmes connus et signalés par Microsoft, résoudre les incidents, effectuer des tâches à l’aide de solutions recommandées par Microsoft et, si nécessaire, faire appel au support technique de Microsoft.

Pour la Microsoft 365 **l’application de prise** en charge de l’intégration à partir du magasin ServiceNow, go to the [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Principales fonctionnalités

Voici les principales fonctionnalités que vous obtenez avec l’application d’intégration Microsoft 365 support technique dans votre instance ServiceNow :

- Incidents d’état du service : informations sur les incidents d’état du service Microsoft connus, y compris l’impact sur l’utilisateur, l’étendue, l’état actuel et la prochaine mise à jour attendue. À l’aide de l’apprentissage automatique, les incidents ServiceNow sont en correspondance avec les incidents d’état du service Microsoft en fonction du champ de description courte.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="Champ de description Incidents d’état du service.":::

- Solutions recommandées : des descriptions des tâches et des incidents sont utilisées pour recommander des solutions ciblées précises et des articles pertinents de Microsoft optimisés par l’apprentissage automatique. Vous pouvez également utiliser la recherche pour rechercher d’autres solutions, si nécessaire.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="Champ description des solutions recommandées.":::

- Demande de service Microsoft : faire resserrez les problèmes aux agents du support Microsoft et recevez des mises à jour d’état pour votre cas.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="Formulaire de demande de service.":::

## <a name="prerequisites"></a>Configuration requise

### <a name="permissions-requirements"></a>Conditions requises pour les autorisations

Pour poursuivre avec ce guide, assurez-vous que les autorisations suivantes sont disponibles et configurées pour vos environnements pendant tout le processus :

- Azure Active Directory administrateur (AAD) qui peut créer des applications AAD web

- Administrateur ServiceNow

- Microsoft 365 client

### <a name="configuration-highlights"></a>Points forts de la configuration

Pour configurer **l’Microsoft 365 prise en charge de l’intégration**:

- Inscrivez des applications dans Microsoft Azure Active Directory (AAD) pour l’authentification des appels d’API entrants et sortants.

- Créez des entités ServiceNow avec Microsoft AAD application pour le flux de données entrant et sortant.

- Intégrez l’instance ServiceNow au support Microsoft par le biais Microsoft 365 portail d’administration.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="Diagramme d’intégration ServiceNow.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>Dépendances d’application dans vos environnements ServiceNow

Autorisations requises :

- entité \_ oauth

- Profil \_ d’entité oauth \_

Une fois l Microsoft 365'application d’intégration de support technique installée, deux accès d’étendues croisées d’applications sont créés. Si elles ne sont pas créées correctement, créez-les manuellement.

## <a name="what-features-will-work-for-your-organization-based-on-your-configuration"></a>Quelles fonctionnalités fonctionneront pour votre organisation en fonction de votre configuration ?

Avant de définir une configuration pour Microsoft 365 l’intégration, examinez vos réponses à ces questions :

**Question \# 1 :** Votre environnement ServiceNow autorise-t-il l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants ?

**Question \# 2**: Si vous avez plusieurs clients, envisagez-vous d’utiliser un seul client intégré à votre environnement ServiceNow pour l’intégration Microsoft 365 prise en charge ?

En fonction de vos réponses aux questions ci-dessus, ce tableau vous indique les fonctionnalités disponibles et la façon de configurer Microsoft 365 l’intégration. Pour obtenir une description de chaque fonctionnalité, voir [Microsoft 365'intégration de prise en charge.](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f)

| Réponse \# à la question 1 | Réponse à \# la question 2 | Quelles fonctionnalités sont disponibles ? | Étapes de configuration |
|---------------------|---------------------|-----------|----------------|
| Oui                 | Oui/Non              | Demande de service Solutions recommandées pour les incidents d’état du service Microsoft | [Configurer l’Microsoft 365 prise en charge de l’intégration avec l’authentification de base ServiceNow](servicenow-basic-authentication.md) |
| Non                  | Oui                 | Demande de service Solutions recommandées pour les incidents d’état du service Microsoft | [Configurer l’intégration Microsoft 365 prise en charge avec AAD OAuth](servicenow-aad-oauth-token.md)                 |
| Non                  | Non                  | Solutions recommandées pour les incidents d’état du service                           | [Configurer l’intégration Microsoft 365 prise en charge pour Informations UNIQUEMENT](servicenow-service-health-incidents-solutions-only.md)                    |
