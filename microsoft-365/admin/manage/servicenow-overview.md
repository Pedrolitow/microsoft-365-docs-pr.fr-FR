---
title: Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide d’installation et de configuration d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: cb36dfa2f0c27eee6112e7512a3dbc474c1dcf32
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68735702"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow

Le contenu suivant s’applique à l’application d’intégration de support Microsoft 365 avec une version minimale de **1.0.7**.

**L’intégration du support Microsoft 365** vous permet d’intégrer l’aide, le support et l’intégrité du service Microsoft 365 à vos instances ServiceNow. Vous pouvez rechercher les problèmes connus et signalés par Microsoft, résoudre les incidents, effectuer des tâches à l’aide des solutions recommandées par Microsoft et, si nécessaire, passer au support assisté par Microsoft.

Pour l’application **d’intégration de support Microsoft 365** à partir du Magasin ServiceNow, accédez au [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Principales fonctionnalités

Voici les principales fonctionnalités que vous obtiendrez avec l’application d’intégration du support Microsoft 365 dans votre instance ServiceNow :

- Incidents d’intégrité du service : informations sur les incidents connus liés à l’intégrité du service Microsoft, notamment l’impact sur l’utilisateur, l’étendue, l’état actuel et la prochaine mise à jour attendue. À l’aide du Machine Learning, les incidents ServiceNow sont mis en correspondance avec les incidents d’intégrité du service Microsoft en fonction du champ de description courte.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow_service_health_incidents.png" lightbox="../../media/ServiceNow-guide/servicenow_service_health_incidents.png" alt-text="Champ de description des incidents d’intégrité du service.":::

- Solutions recommandées : les descriptions des tâches et des incidents sont utilisées pour recommander des solutions ciblées précises et des articles pertinents de Microsoft optimisés par le Machine Learning. Vous pouvez également utiliser la recherche pour trouver d’autres solutions, si nécessaire.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow_recommended_articles.png" lightbox="../../media/ServiceNow-guide/servicenow_recommended_articles.png" alt-text="Champ de description des solutions recommandées.":::

- Demande de service Microsoft : transmettez les problèmes aux agents du support technique Microsoft et recevez des mises à jour d’état pour votre demande. Avec un flux de travail mis à jour, vous pouvez désormais créer une demande de service en ajoutant le titre, la description et les informations de contact de votre choix, comme dans le portail d’administration Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/SNOW_escalation.png" lightbox="../../media/ServiceNow-guide/SNOW_escalation.png" alt-text="Capture d’écran montrant le champ de description des solutions recommandées.":::

    :::image type="content" source="../../media/ServiceNow-guide/SNOW_escalation2.png" lightbox="../../media/ServiceNow-guide/SNOW_escalation2.png" alt-text="Capture d’écran montrant le champ de description des solutions recommandées.":::

## <a name="prerequisites"></a>Configuration requise

### <a name="permissions-requirements"></a>Exigences relatives aux autorisations

Pour suivre ce guide, vérifiez que les autorisations suivantes sont disponibles et configurées pour vos environnements pendant tout le processus :

- Administrateur Azure Active Directory (AAD) qui peut créer des applications Azure AD

- Administrateur ServiceNow

- Administrateur de locataire Microsoft 365

### <a name="configuration-highlights"></a>Points forts de la configuration

Pour configurer **l’intégration de la prise en charge de Microsoft 365** :

- Inscrire des applications dans Microsoft Azure Active Directory (AAD) pour l’authentification des appels d’API sortants et entrants.

- Créez des entités ServiceNow avec Microsoft Azure AD Application pour le flux de données sortant et entrant.

- Intégrez l’instance ServiceNow au support Microsoft via le portail d’administration Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="Diagramme d’intégration de ServiceNow.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>Dépendances d’application dans vos environnements ServiceNow

Autorisations requises :

- Entité oauth\_

- Profil d’entité\_oauth\_

Une fois l’application d’intégration du support Microsoft 365 installée, deux accès inter-étendues d’application sont créés. S’ils ne sont pas créés correctement, créez-les manuellement.

## <a name="set-up-the-integration"></a>Configurer l’intégration

Une fois que vous avez téléchargé l’application, accédez à l’Assistant Installation de Microsoft 365 dans votre environnement SNOW pour terminer le processus d’installation.

:::image type="content" source="../../media/ServiceNow-guide/Agree.png" lightbox="../../media/ServiceNow-guide/Agree.png" alt-text="Capture d’écran montrant le champ de description des solutions recommandées.":::

Pour en savoir plus sur les étapes, consultez les pages suivantes :
- Si vous souhaitez commencer sans configurer l’application d’intégration du support Microsoft 365, vous pouvez sélectionner l’option **Continuer sans configuration** . Cette option continuera à fournir des solutions recommandées de base.

    :::image type="content" source="../../media/ServiceNow-guide/No_setup.png" lightbox="../../media/ServiceNow-guide/No_setup.png" alt-text="Champ de description des solutions recommandées.":::
    
- Si votre environnement ServiceNow autorise l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants, suivez les instructions fournies dans [Configurer l’intégration de la prise en charge de Microsoft 365 avec l’authentification de base ServiceNow](servicenow-basic-authentication.md).
- Si votre environnement ServiceNow n’autorise PAS l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants, suivez les instructions fournies dans [Configurer l’intégration de la prise en charge de Microsoft 365 avec le jeton d’authentification Azure AD](servicenow-aad-oauth-token.md).
  - Cette configuration nécessite un locataire de l’authentification unique pour que le jeton d’authentification AAD fonctionne correctement.

Pour comprendre chaque fonctionnalité, consultez [Intégration de la prise en charge de Microsoft 365](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

> [!NOTE]
> Cette application n’est pas prise en charge dans les environnements réglementés ou restreints.

> [!IMPORTANT]
> L’application d’intégration de prise en charge de Microsoft 365 invite parfois les utilisateurs à formuler des commentaires sur l’application. Si vous ne souhaitez pas que les utilisateurs soient invités à envoyer des commentaires, désactivez cette fonctionnalité dans les paramètres de l’application. Pour plus d’informations sur les stratégies de commentaires Microsoft, consultez [En savoir plus sur les commentaires Microsoft pour votre organisation](/microsoft-365/admin/misc/feedback-user-control). Pour modifier les paramètres de commentaires, suivez les étapes du processus d’installation.
