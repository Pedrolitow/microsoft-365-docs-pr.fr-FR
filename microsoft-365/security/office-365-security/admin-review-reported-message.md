---
title: Révision par l’administrateur des messages signalés
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
ms.custom: ''
description: Découvrez comment passer en revue les messages signalés et comment envoyer des commentaires à vos utilisateurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2cb979260bde62903e97a4726083924101b8711a
ms.sourcegitcommit: c6a97f2a5b7a41b74ec84f2f62fabfd65d8fd92a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/12/2022
ms.locfileid: "61932794"
---
# <a name="admin-review-for-reported-messages"></a>Révision par l’administrateur des messages signalés

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online et Microsoft Defender pour Office 365, les administrateurs peuvent désormais renvoyer des messages de modèle aux utilisateurs finaux après avoir passé en revue les messages signalés. Les modèles peuvent être personnalisés pour votre organisation et basés sur le verdict de votre administrateur.

La fonctionnalité est conçue pour envoyer des commentaires à vos utilisateurs, mais ne modifie pas les verdicts des messages dans le système. Pour aider Microsoft à mettre à jour et à améliorer ses filtres, vous devez envoyer des messages pour analyse à l’aide de [la soumission d’administrateur.](admin-submission.md)

Vous ne pourrez marquer et avertir les utilisateurs des résultats de la révision que si le message a été signalé comme faux positifs ou [faux négatifs.](report-false-positives-and-false-negatives.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **Soumissions,** utilisez <https://security.microsoft.com/reportsubmission> .

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :
  - Administrateur de la gestion de l’organisation ou de la sécurité [dans Microsoft 365 Defender portail.](permissions-microsoft-365-security-center.md)
  - Gestion de [l’organisation Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Vous aurez également besoin d’accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevrez une erreur qui indique spécifier une adresse de messagerie dans *votre domaine.* Pour plus d’informations sur l’activation ou la désactivation de l’accès Exchange Online PowerShell, consultez les rubriques suivantes :
  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Règles d’accès client dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="notify-users-from-within-the-portal"></a>Avertir les utilisateurs à partir du portail

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com> , go to the **Submissions** page at **Email & collaboration** \> **Submissions**. Pour aller directement à la page **Soumissions,** utilisez <https://security.microsoft.com/reportsubmission> .

2. Cliquez **sur Messages signalés** par l’utilisateur, puis sélectionnez le message que vous souhaitez marquer et notifier.

3. Sélectionnez la marque en tant que et **notifier** la drop-down, puis sélectionnez Aucune menace **trouvée,** **Hameçonnage** ou **Courrier indésirable**.

   > [!div class="mx-imgBorder"]
   > ![Envoyer des messages à partir du portail.](../../media/admin-review-send-message-from-portal.png)

Le message signalé sera marqué comme faux positif ou faux négatif, et un message électronique sera automatiquement envoyé à partir du portail pour avertir l’utilisateur qui a signalé le message.

## <a name="customize-the-messages-used-to-notify-users"></a>Personnaliser les messages utilisés pour avertir les utilisateurs

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com> , go to the User **submissions** page at **Email & Collaboration** Policies & \> **Rules** \> **Threat** \> **Settings User reported message settings** in the **Others** section. Pour aller directement à la page **Soumissions de l’utilisateur,** utilisez <https://security.microsoft.com/userSubmissionsReportMessage> .

2. Dans la page Soumissions d’utilisateurs, si vous souhaitez  spécifier le nom complet de l’expéditeur, cochez la case Spécifier l’adresse de messagerie Office 365 à utiliser en tant qu’expéditeur dans la section **Notifications** par courrier électronique pour les résultats de l’avis de l’administrateur, puis entrez le nom que vous souhaitez utiliser.  L’adresse de messagerie qui sera visible dans Outlook et toutes les réponses y seront.

3. Si vous souhaitez personnaliser l’un des modèles, cliquez sur Personnaliser la **notification** par courrier électronique en bas de la page. Dans le volant qui s’ouvre, vous pouvez personnaliser uniquement les paramètres suivants :

    - Hameçonnage
    - Courrier indésirable
    - Aucune menace détectée
    - Pied de page

    > [!div class="mx-imgBorder"]
    > ![Personnaliser les messages envoyés aux utilisateurs.](../../media/admin-review-customize-message.png)

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**. Pour effacer ces valeurs, cliquez **sur Ignorer** dans la page **Soumissions de l’utilisateur.**
