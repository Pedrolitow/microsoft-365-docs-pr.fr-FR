---
title: Fonctionnalités du score de sécurité Microsoft
description: Décrit les nouvelles modifications apportées à Microsoft Secure score dans le centre de sécurité Microsoft 365.
keywords: score de sécurité Microsoft, score de sécurisation, score de sécurité Office 365, score de sécurité Microsoft, centre de sécurité Microsoft 365, actions d’amélioration
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
ms.openlocfilehash: 82ec67cae86525c055b2232667cccb603830d15f
ms.sourcegitcommit: c51de5e1a4cb9c4a7a9854a4226b32453d9e73e0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2020
ms.locfileid: "48779247"
---
# <a name="whats-coming-to-microsoft-secure-score"></a>Fonctionnalités du score de sécurité Microsoft

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Nous apportons des modifications à l’avenir proche pour faire en sorte que [Microsoft Secure](microsoft-secure-score.md) évalue un meilleur représentant de votre position de sécurité et améliore l’utilisation. Votre score et le score maximal possible peuvent varier.

## <a name="proposed-changes"></a>Proposed changes

### <a name="november-2020"></a>Novembre 2020

Suppression de la possibilité de créer des tickets ServiceNow via le score de sécurité en accédant à **Share > ServiceNow** .

- La période d’aperçu du connecteur ServiceNow se termine. Cette fonctionnalité n’est plus disponible à la fin du 2020. Nous vous remercions pour vos commentaires et le support technique pendant que nous déterminons les étapes suivantes.

Ajout de 18 actions d’amélioration relatives à Microsoft Defender pour le point de terminaison (précédemment Microsoft Defender ATP) :

Recommandations relatives à la réduction de la surface d’attaque (ASR) :
- Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie Web
- Empêcher toutes les applications Office de créer des processus enfants
- Empêcher les applications Office de créer du contenu exécutable
- Bloquer l’injection de code dans d’autres processus par les applications Office
- Bloquer JavaScript ou VBScript pour lancer le téléchargement de contenu exécutable
- Bloquer l’exécution des scripts potentiellement brouillés
- Bloquer les appels d’API Win32 à partir de macros Office
- Bloquer l’exécution des fichiers exécutables sauf s’ils répondent à un critère de récurrence, d’âge ou de liste approuvée
- Utiliser la protection avancée contre les ransomware
- Bloquer le vol d’informations d’identification à partir du sous-système Windows local Security Authority (lsass.exe)
- Création de processus de bloc provenant de commandes PSExec et WMI
- Bloquer les processus non approuvés et non signés qui s’exécutent à partir de ports USB
- Bloquer l’application de communication Office de la création de processus enfants
- Empêcher Adobe Reader de créer des processus enfants
- Blocage de la persistance via l’abonnement aux événements WMI

Recommandations relatives aux services :
- Corriger le chemin d’accès non quoted service pour les services Windows
- Modifier le chemin d’accès exécutable de service en un emplacement protégé courant
- Modifier le compte de service pour éviter le mot de passe mis en cache dans le Registre Windows

## <a name="related-resources"></a>Ressources connexes

- [Présentation de Microsoft Secure score](microsoft-secure-score.md)
- [Évaluez votre posture de sécurité](microsoft-secure-score-improvement-actions.md)
- [Suivi de votre historique de score sécurisé Microsoft et atteindre les objectifs](microsoft-secure-score-history-metrics-trends.md)
- [Nouveautés](microsoft-secure-score-whats-new.md)
