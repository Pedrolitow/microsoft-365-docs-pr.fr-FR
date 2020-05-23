---
title: Spécifier une boîte aux lettres pour les soumissions d’utilisateurs de messages de courrier indésirable et de hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à configurer une boîte aux lettres pour collecter le courrier indésirable et le courrier indésirable transmis par les utilisateurs.
ms.openlocfilehash: d3ff44957864e3d5e959d6252d1d538cc715ae92
ms.sourcegitcommit: 8d9509e617ede7cc5ba933c54fb9300d2d1c6344
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/22/2020
ms.locfileid: "44347806"
---
# <a name="specify-a-mailbox-for-user-submissions-of-spam-and-phishing-messages-in-exchange-online"></a>Spécifier une boîte aux lettres pour les soumissions d’utilisateurs de messages de courrier indésirable et de hameçonnage dans Exchange Online

Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, vous pouvez spécifier une boîte aux lettres pour recevoir les messages signalés comme malveillants ou non malveillants par les utilisateurs. Lorsque les utilisateurs envoient des messages à l’aide des différentes options de création de rapports, vous pouvez utiliser cette boîte aux lettres pour intercepter des messages (Envoyer à la boîte aux lettres personnalisée uniquement) ou recevoir des copies de messages (Envoyer à la boîte aux lettres personnalisée et à Microsoft). Cette fonctionnalité fonctionne avec les options de signalement de message suivantes :

- [Complément de message de rapport](enable-the-report-message-add-in.md)

- [Création de rapports intégrée dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) (anciennement appelé Outlook Web App)

  > [!NOTE]
  > Si la création de rapports a été [désactivée dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), l’activation des soumissions d’utilisateurs ici remplacera ce paramètre et permettra aux utilisateurs de signaler à nouveau les messages dans Outlook sur le Web.

Vous pouvez également configurer des outils de création de rapports de messages tiers pour transférer des messages vers la boîte aux lettres que vous spécifiez.

La remise des messages signalés par l’utilisateur à une boîte aux lettres personnalisée au lieu de Microsoft permet à vos administrateurs de signaler des messages de façon sélective et manuelle à Microsoft à l’aide de la soumission de l' [administrateur](admin-submission.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour accéder directement à la page **soumissions** de l’utilisateur, utilisez <https://protection.office.com/userSubmissionsReportMessage> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Pour configurer la boîte aux lettres pour les soumissions des utilisateurs, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** . Pour des informations supplémentaires sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="use-the-security--compliance-center-to-configure-the-user-submissions-mailbox"></a>Utiliser le centre de sécurité & conformité pour configurer la boîte aux lettres d’envoi des utilisateurs

1. Dans le centre de sécurité & conformité, accédez à l’utilisateur de la stratégie de **gestion des menaces** \> **Policy** \> **User submissions**.

2. Dans la page **soumissions** de l’utilisateur qui s’affiche, sélectionnez l’une des options suivantes :

   a. **Activer la fonctionnalité de rapport de message pour Outlook (recommandé)**: sélectionnez cette option si vous utilisez le complément de rapport de message ou le complément de création de rapports dans Outlook sur le Web, puis configurez les paramètres suivants :

      - **Personnaliser le message de confirmation de l’utilisateur final**: cliquez sur ce lien. Dans la fenêtre mobile **personnaliser le message de confirmation** qui s’affiche, configurez les paramètres suivants :

      - **Avant l’envoi**: dans les zones de message de **titre** et de **confirmation** , entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du complément de message de rapport. Vous pouvez utiliser la variable% type% pour inclure le type d’envoi (courrier indésirable, pas courrier indésirable, hameçonnage, etc.).

        Comme indiqué, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

        > Votre courrier électronique sera envoyé tel quel à Microsoft pour analyse. Certains courriers électroniques peuvent contenir des informations personnelles ou sensibles.

      - **Après l’envoi**: cliquez sur ![ développer ](../../media/scc-expand-icon.png) . Dans les zones de **message** de **titre** et de confirmation, entrez le texte descriptif que les utilisateurs voient lorsqu’ils signalent un message à l’aide du complément de message de rapport. Vous pouvez utiliser la variable% type% pour inclure le type d’envoi.

      Lorsque vous avez terminé, cliquez sur **Enregistrer**. Pour effacer ces valeurs, cliquez sur **restaurer** sur la page **soumissions** de l’utilisateur.

      - **Envoyer les messages signalés à**: effectuez l’une des sélections suivantes :

        - **Microsoft (recommandé)**: la boîte aux lettres d’envoi n’est pas utilisée (tous les messages signalés sont transmis à Microsoft).

        - **Microsoft et une boîte aux lettres personnalisée**: dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les soumissions des utilisateurs seront dirigées vers Microsoft pour analyse et vers la boîte aux lettres personnalisée que votre administrateur ou votre équipe chargée des opérations de sécurité doit analyser.

        - **Boîte aux lettres personnalisée**: dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Utilisez cette option si vous souhaitez que le message soit uniquement destiné aux administrateurs ou à l’équipe des opérations de sécurité pour analyse. Les messages ne sont pas envoyés à Microsoft à moins que l’administrateur ne le transfère eux-mêmes.

        > [!NOTE]
        > Les organisations gouvernementales américaines (GCC, GCC-H et DoD) ne peuvent configurer que la **boîte aux lettres personnalisée**. Les deux autres options sont désactivées. 

      Lorsque vous avez terminé, cliquez sur **confirmer**.

      > [!CAUTION]
      > Si vous avez [désactivé la création de rapports de courrier indésirable dans Outlook sur le Web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) à l’aide des stratégies de boîte aux lettres Outlook sur le Web, mais que vous configurez l’un des paramètres précédents pour signaler les messages à Microsoft, les utilisateurs pourront signaler les messages à Microsoft dans Outlook sur le Web à l’aide du complément Report message.

   - **Désactiver la fonctionnalité de rapport de message pour Outlook**: sélectionnez cette option si vous utilisez des outils de création de rapports tiers à la place du complément de rapport de message ou de la création de rapports intégrée dans Outlook sur le Web, puis configurez les paramètres suivants :

      Sélectionnez **utiliser cette boîte aux lettres personnalisée pour recevoir des envois signalés par l’utilisateur**. Dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres existante qui se trouve déjà dans Office 365. Il doit s’agir d’une boîte aux lettres existante dans Exchange Online qui peut recevoir des courriers électroniques.

      Lorsque vous avez terminé, cliquez sur **confirmer**.

## <a name="message-submission-format"></a>Format de dépôt des messages

Les messages envoyés à des boîtes aux lettres personnalisées doivent suivre un format de message d’envoi spécifique. L’objet (titre de l’enveloppe) de l’envoi doit être au format suivant :

`SafetyAPIAction|NetworkMessgeId|SenderIp|FromAddress|(Message Subject)`

SafetyAPIAction est l’une des valeurs entières suivantes :

- 1 : courrier indésirable
- 2 : NotJunk
- 3 : hameçonnage

Dans l’exemple suivant :

- Le message est signalé comme hameçonnage.
- L’ID de message réseau est 49871234-6dc6-43e8-ABCD-08d797f20abe.
- L’adresse IP de l’expéditeur est 167.220.232.101.
- L’adresse de l’adresse est test@contoso.com.
- La ligne d’objet du message est « tester la soumission de hameçonnage »

`3|49871234-6dc6-43e8-abcd-08d797f20abe|167.220.232.101|test@contoso.com|(test phish submission)`

Les messages qui ne suivent pas ce format ne s’afficheront pas correctement dans le portail des dépôts.
