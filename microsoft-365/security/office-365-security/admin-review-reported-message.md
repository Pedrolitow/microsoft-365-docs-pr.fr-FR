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
- m365-security
ms.custom: ''
description: Découvrez comment passer en revue les messages signalés et envoyer des commentaires à vos utilisateurs.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 4fbb592512eb9bc872a5c721f48e43ec5ad25a2a
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68066825"
---
# <a name="admin-review-for-reported-messages"></a>Révision par l’administrateur des messages signalés

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec Exchange Online boîtes aux lettres et Microsoft Defender pour Office 365, les administrateurs peuvent désormais renvoyer des messages modèles aux utilisateurs finaux après avoir examiné les messages signalés. Les modèles peuvent être personnalisés pour votre organisation et en fonction du verdict de votre administrateur.

La fonctionnalité est conçue pour envoyer des commentaires à vos utilisateurs, mais ne modifie pas les verdicts des messages dans le système. Pour aider Microsoft à mettre à jour et à améliorer ses filtres, vous devez envoyer des messages à des fins d’analyse à l’aide [de Administration soumission](admin-submission.md).

Vous ne pourrez marquer et informer les utilisateurs des résultats de la révision que si le message a été signalé comme [faux positifs ou faux négatifs](report-false-positives-and-false-negatives.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :
  - Gestion de l’organisation ou administrateur de sécurité dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).
  - Gestion de l’organisation dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Vous aurez également besoin d’accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevez une erreur indiquant *spécifier une adresse e-mail dans votre domaine*. Pour plus d’informations sur l’activation ou la désactivation de l’accès à Exchange Online PowerShell, consultez les rubriques suivantes :
  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Règles d’accès client dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="notify-users-from-within-the-portal"></a>Avertir les utilisateurs à partir du portail

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions** de **Email &** \> **collaboration.** Pour accéder directement à la page **Soumissions** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Cliquez sur **Messages signalés par l’utilisateur**, puis sélectionnez le message que vous souhaitez marquer et notifier.

3. Sélectionnez la **marque et notifiez** la liste déroulante, puis sélectionnez **Aucune menace trouvée**, **Hameçonnage** ou **Courrier indésirable**.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/admin-review-send-message-from-portal.png" alt-text="Page affichant les messages signalés par l’utilisateur" lightbox="../../media/admin-review-send-message-from-portal.png":::

Le message signalé est marqué comme faux positif ou faux négatif, et un e-mail est automatiquement envoyé à partir du portail pour avertir l’utilisateur qui a signalé le message.

## <a name="customize-the-messages-used-to-notify-users"></a>Personnaliser les messages utilisés pour informer les utilisateurs

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à la page **Soumissions de l’utilisateur** dans Email & Stratégies de **collaboration** \> & stratégies de **menace** \> **de règles** \> **. Les paramètres de message signalés par l’utilisateur** dans la section **Autres**. Pour accéder directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/userSubmissionsReportMessage>.

2. Dans la page **Soumissions de l’utilisateur**, si vous souhaitez spécifier le nom d’affichage de l’expéditeur, cochez la case **Spécifier Office 365 adresse e-mail à utiliser comme expéditeur** sous la section **Email notifications pour les résultats de la révision administrateur**, puis entrez le nom que vous souhaitez utiliser. L’adresse e-mail qui sera visible dans Outlook et toutes les réponses y seront envoyées.

3. Si vous souhaitez personnaliser l’un des modèles, cliquez sur **Personnaliser la notification par e-mail** en bas de la page. Dans le menu volant qui s’ouvre, vous pouvez personnaliser uniquement les éléments suivants :

    - Hameçonnage
    - Indésirable
    - Aucune menace détectée
    - Pied de page

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="../../media/admin-review-customize-message.png" alt-text="Page Personnaliser le message de confirmation" lightbox="../../media/admin-review-customize-message.png":::

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**. Pour effacer ces valeurs, cliquez sur **Ignorer** dans la page **Soumissions de l’utilisateur** .
