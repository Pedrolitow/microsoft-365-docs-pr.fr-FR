---
title: Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
ms.openlocfilehash: 898b6a8f15d67fbf3530f6db269f47d5031f3676
ms.sourcegitcommit: 23c7e96d8ec31c676c458e7c71f1cc8a1e40a0e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/16/2022
ms.locfileid: "67359228"
---
# <a name="microsoft-365-support-integration-with-servicenow-configuration-overview"></a>Vue d’ensemble de l’intégration de la prise en charge Microsoft 365 avec la configuration ServiceNow

Le contenu suivant s’applique à l’application d’intégration de support Microsoft 365 avec une version minimale de **1.0.7**.

**L’intégration de la prise en charge de Microsoft 365** vous permet d’intégrer l’aide, le support et l’intégrité des services Microsoft 365 à vos instances ServiceNow. Vous pouvez rechercher des problèmes connus et signalés par Microsoft, résoudre des incidents, effectuer des tâches à l’aide de solutions recommandées par Microsoft et, si nécessaire, passer au support assisté par l’humain Microsoft.

Pour l’application **d’intégration de support Microsoft 365** à partir du Magasin ServiceNow, accédez au [ServiceNow Store](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

## <a name="key-features"></a>Principales fonctionnalités

Voici les principales fonctionnalités que vous obtiendrez avec l’application d’intégration de support Microsoft 365 dans votre instance ServiceNow :

- Incidents d’intégrité des services : informations sur les incidents d’intégrité des services Microsoft connus, notamment l’impact sur l’utilisateur, l’étendue, l’état actuel et la prochaine mise à jour attendue. À l’aide du Machine Learning, les incidents ServiceNow sont mis en correspondance avec les incidents d’intégrité du service Microsoft en fonction du champ de description abrégé.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-1.png" alt-text="Champ de description des incidents d’intégrité du service.":::

- Solutions recommandées : les descriptions des tâches et des incidents sont utilisées pour recommander des solutions ciblées précises et des articles pertinents de Microsoft alimentés par le Machine Learning. Vous pouvez également utiliser La recherche pour trouver d’autres solutions, si nécessaire.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-description-field-2.png" alt-text="Champ de description des solutions recommandées.":::

- Demande de service Microsoft : faites remonter les problèmes aux agents de support Microsoft et recevez des mises à jour d’état pour votre cas.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-service-request.png" lightbox="../../media/ServiceNow-guide/servicenow-overview-service-request.png" alt-text="Formulaire de demande de service.":::

## <a name="prerequisites"></a>Conditions préalables

### <a name="permissions-requirements"></a>Conditions requises pour les autorisations

Pour poursuivre ce guide, assurez-vous que les autorisations suivantes sont disponibles et configurées pour vos environnements pendant l’ensemble du processus :

- Administrateur Azure Active Directory (AAD) qui peut créer des applications Azure AD

- Administrateur ServiceNow

- Administrateur client Microsoft 365

### <a name="configuration-highlights"></a>Mises en évidence de la configuration

Pour configurer **l’intégration de la prise en charge de Microsoft 365** :

- Inscrivez des applications dans Microsoft Azure Active Directory (AAD) pour l’authentification des appels d’API sortants et entrants.

- Créez des entités ServiceNow avec Microsoft Azure AD Application pour le flux de données sortant et entrant.

- Intégrez l’instance ServiceNow au support Microsoft via le portail d’administration Microsoft 365.

    :::image type="content" source="../../media/ServiceNow-guide/servicenow-overview-integration-diagram.png" alt-text="Diagramme d’intégration de ServiceNow.":::

### <a name="application-dependencies-in-your-servicenow-environments"></a>Dépendances d’application dans vos environnements ServiceNow

Autorisations requises :

- entité oauth\_

- Profil d’entité\_oauth\_

Une fois l’application d’intégration du support Microsoft 365 installée, deux accès inter-étendues d’application sont créés. Si elles ne sont pas créées correctement, créez-les manuellement.

## <a name="setup-the-integration"></a>Configurer l’intégration

Une fois que vous avez téléchargé l’application, accédez à l’Assistant Installation de Microsoft 365 dans votre environnement SNOW pour terminer le processus d’installation.
:::image type="content" source="../../media/154124985-76e13e7d-b32e-4741-830b-bbb110d3ecbf.png" alt-text="Assistant Configuration de snow":::

Pour en savoir plus sur les étapes, consultez les pages suivantes :
- Si votre environnement ServiceNow autorise l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants, suivez les instructions de [configuration de l’intégration de la prise en charge de Microsoft 365 à l’authentification de base ServiceNow](servicenow-basic-authentication.md).
- Si votre environnement ServiceNow n’autorise PAS l’authentification de base (accès avec les informations d’identification de l’utilisateur ServiceNow) pour les appels de service web entrants, suivez les instructions fournies dans [Configurer l’intégration de la prise en charge de Microsoft 365 avec le jeton d’authentification Azure AD](servicenow-aad-oauth-token.md).
  - Cette configuration nécessite un locataire d’authentification unique pour que le jeton d’authentification AAD fonctionne correctement.

Pour comprendre chaque fonctionnalité, consultez [l’intégration de la prise en charge de Microsoft 365](https://store.servicenow.com/sn_appstore_store.do#!/store/application/6d05c93f1b7784507ddd4227cc4bcb9f).

> [!NOTE]
> Cette application n’est pas prise en charge dans les environnements réglementés ou restreints.

> [!IMPORTANT]
> L’application d’intégration de support Microsoft 365 invite parfois les utilisateurs à formuler des commentaires sur l’application. Si vous ne souhaitez pas que les utilisateurs soient invités à recevoir des commentaires, désactivez cette fonctionnalité dans les paramètres de l’application. Pour plus d’informations sur les stratégies de commentaires Microsoft, consultez [En savoir plus sur les commentaires de Microsoft pour votre organisation](/microsoft-365/admin/misc/feedback-user-control). Pour modifier les paramètres de commentaires, suivez les étapes du processus d’installation.
