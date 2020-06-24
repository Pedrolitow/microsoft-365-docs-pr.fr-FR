---
title: Qu’est-ce qui arrive dans le score de sécurité Microsoft ?
description: Décrit Microsoft Secure score dans le centre de sécurité Microsoft 365, la façon dont les détails sont calculés et les administrateurs de la sécurité qui peuvent s’y attendre.
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
ms.openlocfilehash: 48ff6d6f5cac0991895c40cae90ca31657cfedff
ms.sourcegitcommit: bd5a08785b5ec320b04b02f8776e28bce5fb448f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/23/2020
ms.locfileid: "44844881"
---
# <a name="whats-coming-in-microsoft-secure-score"></a>Qu’est-ce qui arrive dans le score de sécurité Microsoft ?

Pour faire en sorte que [Microsoft Secure score](microsoft-secure-score.md) un meilleur représentant de votre position de sécurité et améliore la convivialité, nous apportons des modifications dans le futur proche. Votre score et le score maximal possible seront modifiés. Toutefois, cela n’implique pas de modification de votre position de sécurité.

Pour en savoir plus sur les modifications récentes, consultez [la rubrique what’s New in Microsoft Secure score ?](microsoft-secure-score.md#whats-new)

## <a name="june-2020"></a>Juin 2020

### <a name="remove-improvement-action-for-microsoft-defender-advanced-threat-protection"></a>Supprimer l’action d’amélioration pour la protection avancée contre les menaces Microsoft Defender

* Activer les règles de réduction de la surface d’attaque

### <a name="add-improvement-actions-for-microsoft-defender-advanced-threat-protection"></a>Ajouter des actions d’amélioration pour la protection avancée contre les menaces Microsoft Defender

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
