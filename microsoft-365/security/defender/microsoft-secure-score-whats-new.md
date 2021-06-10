---
title: Nouveautés du score de sécurité Microsoft
description: Décrit les nouvelles modifications apportées au Niveau de sécurité Microsoft dans le centre Microsoft 365 sécurité microsoft.
keywords: score de sécurité Microsoft, score sécurisé, score de sécurité Office 365, score de sécurité Microsoft, Centre de sécurité Microsoft 365
ms.prod: m365-security
ms.mktglfcycl: deploy
localization_priority: Normal
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: b3f86dfbc1ae89eff61c680737061b01998a527b
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51933864"
---
# <a name="whats-new-in-microsoft-secure-score"></a>Nouveautés du score de sécurité Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Pour que le Niveau de sécurité Microsoft soit mieux représentatif de votre posture de sécurité, nous avons apporté quelques modifications. Pour en savoir plus sur les modifications planifiées, consultez [l’aide](microsoft-secure-score-whats-coming.md) de Microsoft Secure Score ?

Microsoft Secure Score se trouve dans https://security.microsoft.com/securescore le centre de sécurité [Microsoft 365.](overview-security-center.md)
    
## <a name="february-2021"></a>Février 2021

### <a name="compatibility-with-graph-api"></a>Compatibilité avec l’API Graph de connexion

Les recommandations de Niveau de sécurité Microsoft Graph api auront l’apparence et seront pondérées de la même manière que les recommandations que vous voyez actuellement dans le Centre de sécurité Microsoft 365 de sécurité Microsoft.

## <a name="january-2021"></a>Janvier 2021

### <a name="added-our-first-security-recommendation-for-microsoft-teams"></a>Ajout de notre première recommandation de sécurité pour Microsoft Teams

Microsoft Teams clients voient « Empêcher les utilisateurs anonymes de participer à des réunions » comme nouvelle action d’amélioration du score de sécurité.

## <a name="december-2020"></a>Décembre 2020

### <a name="added-six-accounts-related-improvement-actions-for-microsoft-defender-for-endpoint"></a>Ajout de six actions d’amélioration liées aux comptes pour Microsoft Defender pour Endpoint :

- Définir « Longueur minimale du mot de passe » sur « 14 caractères ou plus »
- Définir « Appliquer l’historique des mots de passe » sur « 24 mots de passe ou plus »
- Définir « Âge maximal du mot de passe » sur « 60 jours ou moins, mais pas 0 »
- Définir « Âge minimal du mot de passe » sur « 1 jour ou plus »
- Désactiver le compte Administrateur intégré
- Désactiver le compte invité intégré

## <a name="november-2020"></a>Novembre 2020

### <a name="removed-the-ability-to-create-servicenow-tickets-through-secure-score"></a>Suppression de la possibilité de créer des tickets ServiceNow via secure score 

La possibilité de créer des tickets ServiceNow via secure score en allant sur **Share > ServiceNow** n’est plus disponible. Merci de vos commentaires et de votre support continu pendant que nous déterminons les étapes suivantes.

### <a name="added-three-services-related-improvement-actions-for-microsoft-defender-for-endpoint"></a>Ajout de trois actions d’amélioration liées aux services pour Microsoft Defender for Endpoint :

- Corriger le chemin d’accès au service sans Windows services
- Modifier le chemin d’accès exécutable du service à un emplacement protégé commun
- Modifier le compte de service pour éviter le mot de passe mis en cache dans le Registre Windows

## <a name="october-2020"></a>Octobre 2020

### <a name="remove-improvement-action-related-to-microsoft-defender-for-endpoint"></a>Supprimer l’action d’amélioration liée à Microsoft Defender pour le point de terminaison

- Configurer la vérification Microsoft Defender SmartScreen Windows contenu web d’application du Store pour avertir

## <a name="august-2020"></a>Août 2020

### <a name="updated-improvement-action-for-azure-active-directory"></a>Action d’amélioration mise à jour pour Azure Active Directory

- Activer la stratégie pour bloquer l’authentification héritée

## <a name="incompatibility-with-identity-secure-score"></a>Incompatibilité avec identity secure score

Dans la version récente de Microsoft Secure Score, un modèle de score amélioré a été publié. Ces modifications permettent une vue plus souple et plus précise de votre posture de sécurité. Toutefois, ces mises à jour ont rendu le Score de sécurisation Microsoft temporairement incompatible avec identity secure score.

Dans le temps, identity Secure Score adoptera le nouveau modèle de score. En attendant, les clients constateront des différences dans les scores signalés par le Score de sécurité Microsoft et le score de sécurisation de l’identité. Nous vous excusons pour les désagréments que cela provoque et nous nous assurons que ces expériences seront plus compatibles à l’avenir.

## <a name="updated-improvement-actions"></a>Actions d’amélioration mises à jour

- Ajout d’Azure Active Directory d’amélioration
- Ajout d’actions d’amélioration de Microsoft Defender pour l’identité
- Prise en charge des recommandations de sécurité de Microsoft Defender for Endpoint [Threat & Vulnerability Management](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
    - Toutes les recommandations de sécurité publiées fournies par TVM sont désormais disponibles

## <a name="updated-interface-and-functionality"></a>Interface et fonctionnalités mises à jour

* Toutes les nouvelles vues de mesures et de tendances pour les discussions CISO et au niveau des responsables
* Nouvelles méthodes de suivi et d’évaluation de votre score
* Amélioration du suivi et de la compréhension des régressions de score
* Filtrer, baliser, rechercher et grouper vos actions d’amélioration
* Gérer vos objectifs futurs à l’aide de projections de score et d’actions planifiées
* Et bien plus encore !

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous avez des problèmes, faites-le nous savoir en publiant dans la communauté sécurité, confidentialité [& conformité.](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) Nous surveillons la communauté et fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluer votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivre votre historique du Score de sécurité Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)