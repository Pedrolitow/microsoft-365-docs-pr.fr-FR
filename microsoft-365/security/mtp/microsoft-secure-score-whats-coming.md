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
ms.openlocfilehash: 234ae17ab31d56d1bbd65f1aa8ed29475e9cd155
ms.sourcegitcommit: d818828c66cf98b0b0037ba8b3cb790c940281b7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43583714"
---
# <a name="whats-coming-in-microsoft-secure-score"></a>Qu’est-ce qui arrive dans le score de sécurité Microsoft ?

Pour faire en sorte que [Microsoft Secure score](microsoft-secure-score.md) un meilleur représentant de votre position de sécurité et améliore la convivialité, nous apportons des modifications dans le futur proche. Votre score et le score maximal possible seront modifiés. Toutefois, cela n’implique pas de modification de votre position de sécurité.

Pour en savoir plus sur les modifications récentes, consultez [la rubrique what’s New in Microsoft Secure score ?](microsoft-secure-score.md#whats-new)

## <a name="april-21st-2020"></a>21 avril 2020

### <a name="removing-improvement-actions-that-dont-meet-expectations-for-reliable-measurement-or-dont-provide-a-useful-representation-of-security-posture"></a>Suppression des actions d’amélioration qui ne répondent pas aux attentes en matière de mesure fiable ou ne fournissent pas une représentation utile de la position de la sécurité

Pour vous assurer que le score de sécurité de Microsoft est significatif et que chaque action d’amélioration est mesurable et fiable, nous supprimons les actions d’amélioration suivantes.

- Appliquer des protections IRM aux documents
- Appliquer des stratégies de protection contre la perte de données

### <a name="adding-azure-ad-improvement-action-to-preview"></a>Ajout de l’action d’amélioration Azure AD à l’aperçu

Ajout de l’action d’amélioration Azure Active Directory suivante à la [version préliminaire de Microsoft Secure score](microsoft-secure-score-preview.md):

- Ne pas autoriser les utilisateurs à accorder un consentement aux applications non gérées (actuellement disponible dans la version publiée)

### <a name="adding-azure-atp-improvement-actions-to-preview"></a>Ajout d’actions d’amélioration ATP DAV à l’aperçu

Ajout des actions d’amélioration d’Azure protection avancée contre les menaces suivantes à la [version préliminaire de Microsoft Secure score](microsoft-secure-score-preview.md):

- Désactiver le service spouleur d’impression sur les contrôleurs de domaine
- Modifier les délégations Kerberos non sécurisées pour empêcher l’emprunt d’identité
- Protéger et gérer les mots de passe d’administrateur local avec Microsoft couvre
- Réduire le risque de trajet latéral vers les entités sensibles
- Supprimer des comptes dormants de groupes sensibles
- Supprimer les attributs d’historique SID non sécurisé des entités
- Résoudre les attributs de compte non sécurisé
- Arrêter l’exposition en texte clair des informations d’identification
- Arrêter la communication des protocoles hérités
- Arrêter l’utilisation du chiffrement faible

### <a name="support-for-microsoft-defender-atp-threat--vulnerability-management-tvm-security-recommendations-in-preview"></a>Prise en charge de la protection contre les vulnérabilités de la & Microsoft Defender ATP (TVM) en aperçu

Toutes les recommandations de sécurité fournies par TVM seront également disponibles dans la [version preview de Microsoft Secure score](microsoft-secure-score-preview.md).
