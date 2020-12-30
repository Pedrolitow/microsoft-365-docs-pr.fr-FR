---
title: Nouveautés de Microsoft Secure score
description: Décrit les nouvelles modifications apportées à Microsoft Secure score dans le centre de sécurité Microsoft 365.
keywords: score de sécurité Microsoft, score de sécurisation, score de sécurité Office 365, score de sécurité Microsoft, centre de sécurité Microsoft 365
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: ellevin
author: levinec
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
ms.openlocfilehash: 61ac8c627dd701ac354a5d60d4774a6443b4d41e
ms.sourcegitcommit: a8f3c633714e934f9ad026c3bc72157ed535dcfc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/29/2020
ms.locfileid: "49737986"
---
# <a name="whats-new-in-microsoft-secure-score"></a>Nouveautés de Microsoft Secure score

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité, nous avons apporté des modifications. Pour en savoir plus sur les modifications planifiées, consultez [la rubrique what’s from Microsoft Secure score ?](microsoft-secure-score-whats-coming.md)

Vous pouvez trouver https://security.microsoft.com/securescore le score de sécurité Microsoft à l’adresse dans le [Centre de sécurité Microsoft 365](overview-security-center.md).

## <a name="december-2020"></a>Décembre 2020

### <a name="added-six-accounts-related-improvement-actions-for-microsoft-defender-for-endpoint-previously-microsoft-defender-atp"></a>Ajout de six actions d’amélioration relatives aux comptes pour Microsoft Defender pour le point de terminaison (précédemment Microsoft Defender ATP) :

- Définir « longueur minimale du mot de passe » sur « 14 caractères ou plus »
- Définir « conserver l’historique des mots de passe » à « 24 ou plusieurs mots de passe »
- Définissez « âge maximal du mot de passe » sur « 60 » ou « moins de jours », mais pas sur « 0 »
- Définir « âge minimal du mot de passe » sur « 1 ou plusieurs jours »
- Désactivation du compte administrateur intégré
- Désactiver le compte invité intégré

## <a name="november-2020"></a>Novembre 2020

### <a name="removed-the-ability-to-create-servicenow-tickets-through-secure-score"></a>Suppression de la possibilité de créer des tickets ServiceNow via Secure score 

La possibilité de créer des tickets ServiceNow via le score de sécurité en accédant à **Share > ServiceNow** n’est plus disponible. Nous vous remercions pour vos commentaires et le support technique pendant que nous déterminons les étapes suivantes.

### <a name="added-three-services-related-improvement-actions-for-microsoft-defender-for-endpoint-previously-microsoft-defender-atp"></a>Ajout de trois actions d’amélioration liées aux services pour Microsoft Defender pour le point de terminaison (précédemment Microsoft Defender ATP) :

- Corriger le chemin d’accès non quoted service pour les services Windows
- Modifier le chemin d’accès exécutable de service en un emplacement protégé courant
- Modifier le compte de service pour éviter le mot de passe mis en cache dans le Registre Windows

## <a name="october-2020"></a>Octobre 2020

### <a name="remove-improvement-action-related-to-microsoft-defender-for-endpoint"></a>Supprimer l’action d’amélioration liée à Microsoft Defender pour le point de terminaison

- Activer la vérification du contenu Web de l’application Windows Store SmartScreen de Microsoft Defender pour avertir

## <a name="august-2020"></a>Août 2020

### <a name="updated-improvement-action-for-azure-active-directory"></a>Action d’amélioration mise à jour pour Azure Active Directory

- Activer la stratégie pour bloquer l’authentification héritée

## <a name="incompatibility-with-identity-secure-score-and-graph-api"></a>Incompatibilité avec le score de sécurité d’identité et l’API Graph

Dans la version récente de Microsoft Secure score, un modèle de notation amélioré a été publié. Ces modifications permettent d’obtenir une vue plus flexible et précise de votre position de sécurité. Toutefois, ces mises à jour ont rendu le score de sécurité Microsoft incompatible temporairement avec le score de sécurité d’identité et l’API Graph.

Dans le temps, le score de sécurité d’identité et l’API Graph adopteront le nouveau modèle de notation. Jusqu’à ce moment, les clients verront les différences entre les scores communiqués par Microsoft Secure score, Identity Secure score et l’API Graph. Nous nous excusons des désagréments que cela peut entraîner et nous travaillons pour garantir que ces expériences sont plus compatibles à l’avenir.

## <a name="updated-improvement-actions"></a>Actions d’amélioration mises à jour

- Ajout d’actions d’amélioration Azure Active Directory
- Ajout de Microsoft Defender pour les actions d’amélioration de l’identité
- Prise en charge des recommandations de sécurité pour la gestion des vulnérabilités de Microsoft Defender [& Vulnerability Management](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)
    - Toutes les recommandations de sécurité fournies par TVM sont désormais disponibles

## <a name="updated-interface-and-functionality"></a>Interface et fonctionnalité mises à jour

* Toutes les nouvelles mesures et tendances pour les CISO et les discussions au niveau des prospects
* Nouvelles façons de suivre et d’évaluer votre score
* Meilleure approche et compréhension pour les régressions de score
* Filtrage, balisage, recherche et regroupement de vos actions d’amélioration
* Gérer vos objectifs à venir à l’aide de projections de score et des actions planifiées
* Et bien plus encore !

## <a name="we-want-to-hear-from-you"></a>Votre avis nous intéresse

Si vous rencontrez des problèmes, informez-le en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluez votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivi de votre historique de score sécurisé Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)
