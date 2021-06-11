---
title: Révision par l’administrateur des messages signalés
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
localization_priority: Normal
ms.collection:
- M365-security-compliance
description: Découvrez comment passer en revue les messages signalés et envoyer des commentaires à vos utilisateurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 217f5ebb1692d68b5dc70988888bf78d4bd36a0c
ms.sourcegitcommit: d0c160e89e17f451199bc4a85699effd2d935213
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/11/2021
ms.locfileid: "52893727"
---
# <a name="admin-review-for-reported-messages"></a>Révision par l’administrateur des messages signalés

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

> [!NOTE]
> Les informations de cet article concernent un produit d’aperçu qui peut être considérablement modifié avant sa publication commerciale. Ce document est fourni uniquement à des fins d’évaluation et d’exploration.

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online et Microsoft Defender pour Office 365, les administrateurs peuvent désormais renvoyer des messages de modèle aux utilisateurs finaux après avoir passé en revue les messages signalés. Cela peut être personnalisé pour votre organisation et en fonction du verdict de votre administrateur.

Cette fonctionnalité est conçue pour envoyer des commentaires à vos utilisateurs, mais ne modifie pas les verdicts des messages dans le système. Pour aider Microsoft à mettre à jour et à améliorer ses filtres, vous devez envoyer des messages pour analyse à l’aide de [la soumission d’administrateur.](admin-submission.md)

Vous ne pourrez marquer et avertir les utilisateurs des résultats de la révision que si le message a été signalé comme faux positifs ou [faux négatifs.](report-false-positives-and-false-negatives.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le portail Microsoft 365 Defender sur <https://security.microsoft.com/> . Pour aller directement à la page **Soumissions,** utilisez <https://security.microsoft.com/reportsubmission> .

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :
  - Administrateur de la gestion de l’organisation ou de la sécurité [dans Microsoft 365 portail Defender](permissions-microsoft-365-security-center.md).
  - Gestion de [l’organisation Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Vous aurez également besoin d’accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevrez une erreur qui indique spécifier une adresse de messagerie dans *votre domaine.* Pour plus d’informations sur l’activation ou la désactivation de l’accès Exchange Online PowerShell, consultez les rubriques suivantes :
  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Règles d’accès client Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="configure-the-messages-used-to-notify-users"></a>Configurer les messages utilisés pour avertir les utilisateurs

1. In the Microsoft 365 Defender portal, go to **Email & collaboration** Policies & \> **rules** Threat \> **policies** \> **Others** section User reported \> **message settings**.

2. Dans la page Soumissions d’utilisateurs, si vous souhaitez  spécifier le nom complet de l’expéditeur, cochez la case Spécifier l’adresse de messagerie Office 365 à utiliser en tant qu’expéditeur dans la section **Notifications** par courrier électronique pour les résultats de l’avis de l’administrateur, puis entrez le nom que vous souhaitez utiliser.  Il s’agit de l’adresse de messagerie qui sera visible dans Outlook et où les réponses seront envoyés.

3. Si vous souhaitez personnaliser l’un des modèles, cliquez sur **Personnaliser la notification par courrier électronique.** Dans ce flyout, vous serez en mesure de personnaliser uniquement les paramètres suivants :
    - Hameçonnage
    - Courrier indésirable
    - Aucune menace détectée
    - Formation de sensibilisation
    - Pied de page

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**. Pour effacer ces valeurs, cliquez **sur Ignorer** dans la page Soumissions de l’utilisateur.
