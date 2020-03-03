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
ms.openlocfilehash: efb75f26d66258880c9defa94869f27e18685052
ms.sourcegitcommit: 9224a7a5886c0c5fa0bc12bd9f7234a0eba90023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42372002"
---
# <a name="whats-coming-in-microsoft-secure-score"></a>Qu’est-ce qui arrive dans le score de sécurité Microsoft ?

Pour faire en sorte que Microsoft Secure score un meilleur représentant de votre position de sécurité et améliore la convivialité, nous apportons des modifications dans le futur proche. Votre score et le score maximal possible seront modifiés. Toutefois, cela n’implique pas de modification de votre position de sécurité.

Pour en savoir plus sur les modifications récentes, consultez [la rubrique what’s New in Microsoft Secure score ?](microsoft-secure-score.md#whats-new)

## <a name="march-16th-2020"></a>16 mars 2020

### <a name="removing-improvement-actions-that-dont-meet-expectations-for-reliable-measurement-or-dont-provide-a-useful-representation-of-security-posture"></a>Suppression des actions d’amélioration qui ne répondent pas aux attentes en matière de mesure fiable ou ne fournissent pas une représentation utile de la position de la sécurité

Pour vous assurer que le score de sécurité de Microsoft est significatif et que chaque action d’amélioration est mesurable et fiable, nous supprimons les actions d’amélioration suivantes.

- Stocker des documents utilisateur dans OneDrive entreprise
- Configurer des stratégies de pièces jointes approuvées ATP Office 365
- Configurer les liens fiables Office 365 pour vérifier les URL
- Ne pas autoriser la délégation de boîte aux lettres
- Autoriser les liens de partage d’invités anonymes pour les sites et les documents
- Activer la console de sécurité des applications Cloud
- Configurer le délai d’expiration pour les liens de partage externe

### <a name="supporting-security-defaults-for-azure-ad-improvement-actions"></a>Prise en charge des paramètres de sécurité par défaut pour les actions d’amélioration Azure AD

Le score de sécurité Microsoft mettra à jour les actions d’amélioration afin de prendre en charge les paramètres de [sécurité par défaut dans Azure ad](https://docs.microsoft.com/azure/active-directory/fundamentals/concept-fundamentals-security-defaults), ce qui facilite la protection de votre organisation à l’aide de paramètres de sécurité préconfigurés pour les attaques courantes.

Cela aura une incidence sur les actions d’amélioration suivantes :

- S’assurer que tous les utilisateurs peuvent effectuer l’authentification multifacteur pour un accès sécurisé
- Exiger MFA pour les rôles d’administration
- Activer la stratégie pour bloquer l’authentification héritée
