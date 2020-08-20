---
title: Nouveautés de Microsoft Secure score
description: Décrit les nouvelles modifications apportées à Microsoft Secure score dans le centre de sécurité Microsoft 365.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, Secure score, centre de sécurité, actions d’amélioration
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
ms.openlocfilehash: 644e12d3b9dfecc0a31c8d464033e41670bc7b88
ms.sourcegitcommit: 22fd8517707ed3ab6ef996247ad2aa372535ee56
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/19/2020
ms.locfileid: "46815230"
---
# <a name="whats-new-in-microsoft-secure-score"></a>Nouveautés de Microsoft Secure score

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité, nous avons apporté des modifications. Pour en savoir plus sur les modifications planifiées, consultez [la rubrique what’s from Microsoft Secure score ?](microsoft-secure-score-whats-coming.md).

## <a name="july-2020"></a>Juillet 2020

### <a name="adding-improvement-actions-for-azure-advanced-threat-protection"></a>Ajout d’actions d’amélioration pour Azure protection avancée contre les menaces

- Chemins de déplacement latéraux risqués
- Attributs de compte non sécurisés
- Activer les fonctionnalités de sécurité sur les approbations Active Directory
- Supprimer les attributs d’historique SID non sécurisé des entités

## <a name="june-2020"></a>Juin 2020

### <a name="removed-improvement-action-for-microsoft-defender-advanced-threat-protection"></a>Suppression de l’action d’amélioration pour la protection avancée contre les menaces Microsoft Defender

* Activer les règles de réduction de la surface d’attaque

### <a name="added-improvement-actions-for-microsoft-defender-advanced-threat-protection"></a>Ajout d’actions d’amélioration pour la protection avancée contre les menaces Microsoft Defender

* Empêcher Adobe Reader de créer des processus enfants
* Utiliser la protection avancée contre les ransomware
* Empêcher toutes les applications Office de créer des processus enfants
* Empêcher les applications Office de créer du contenu exécutable
* Bloquer JavaScript ou VBScript pour lancer le téléchargement de contenu exécutable
* Bloquer l’exécution des scripts potentiellement brouillés
* Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie Web
* Bloquer l’application de communication Office de la création de processus enfants
* Bloquer les processus non approuvés et non signés qui s’exécutent à partir de ports USB
* Blocage de la persistance via l’abonnement aux événements WMI
* Bloquer l’injection de code dans d’autres processus par les applications Office
* Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à un critère de récurrence, d’âge ou de liste approuvée
* Création de processus de bloc provenant de commandes PSExec et WMI
* Bloquer le vol d’informations d’identification à partir du sous-système Windows local Security Authority (lsass.exe)
* Bloquer les appels d’API Win32 à partir de macros Office

## <a name="incompatibility-with-identity-secure-score-and-graph-api"></a>Incompatibilité avec le score de sécurité d’identité et l’API Graph

Dans la version récente de Microsoft Secure score, un modèle de notation amélioré a été publié. Ces modifications permettent d’obtenir une vue plus flexible et précise de votre position de sécurité. Toutefois, ces mises à jour ont rendu le score de sécurité Microsoft incompatible temporairement avec le score de sécurité d’identité et l’API Graph.

Dans le temps, le score de sécurité d’identité et l’API Graph adopteront le nouveau modèle de notation. Jusqu’à ce moment, les clients verront les différences entre les scores communiqués par Microsoft Secure score, Identity Secure score et l’API Graph. Nous nous excusons des désagréments que cela peut entraîner et nous travaillons pour garantir que ces expériences sont plus compatibles à l’avenir.

## <a name="updated-improvement-actions"></a>Actions d’amélioration mises à jour

- Ajout d’actions d’amélioration Azure Active Directory
- Ajout d’actions d’amélioration de la protection avancée contre les menaces
- Prise en charge des recommandations de sécurité de la [& de gestion des vulnérabilités](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt) de Microsoft Defender ATP
    - Toutes les recommandations de sécurité fournies par TVM sont désormais disponibles

## <a name="updated-interface-and-functionality"></a>Interface et fonctionnalité mises à jour

* Toutes les nouvelles mesures et tendances pour les CISO et les discussions au niveau des prospects
* Nouvelles façons de suivre et d’évaluer votre score
* Meilleure approche et compréhension pour les régressions de score
* Filtrage, balisage, recherche et regroupement de vos actions d’amélioration
* Gérer vos objectifs à venir à l’aide de projections de score et des actions planifiées
* Et bien plus encore !

## <a name="we-want-to-hear-from-you"></a>Nous souhaitons être informés

Si vous rencontrez des problèmes, indiquez-nous en publiant dans la communauté [Security, Privacy & Compliance](https://techcommunity.microsoft.com/t5/Security-Privacy-Compliance/bd-p/security_privacy) . Nous Surveillez la communauté et vous fournirons de l’aide.

## <a name="related-resources"></a>Ressources connexes

- [Évaluez votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivi de votre historique de score sécurisé Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-coming.md)
