---
title: Stratégie de soumissions d’utilisateurs
f1.keywords:
- NOCSH
ms.author: siosulli
author: siosulli
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à configurer une boîte aux lettres pour collecter le courrier indésirable et le hameçonnage signalés par les utilisateurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: d86c79f0f0ab74d1dfbb88e7803f4ee4d691ea73
ms.sourcegitcommit: 582555d2b4ef5f2e2494ffdeab2c1d49e5d6b724
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2021
ms.locfileid: "51501181"
---
# <a name="user-submissions-policy"></a>Stratégie de soumissions d’utilisateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec boîtes aux lettres Exchange Online, vous pouvez spécifier une boîte aux lettres pour recevoir des messages que les utilisateurs signalent comme malveillants ou non malveillants. Lorsque les utilisateurs envoient des messages à l’aide des différentes options de création de rapports, vous pouvez utiliser cette boîte aux lettres pour intercepter des messages (envoyer à la boîte aux lettres personnalisée uniquement) ou recevoir des copies de messages (envoyer à la boîte aux lettres personnalisée et Microsoft). Cette fonctionnalité fonctionne avec les options de rapport de message suivantes :

- [Le add-in Message de rapport](enable-the-report-message-add-in.md)

- [Le module de signalement du hameçonnage](enable-the-report-phish-add-in.md)

- [Rapports intégrés dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md) (anciennement Outlook Web App)

- [Rapports intégrés dans Outlook pour iOS et Android](report-junk-email-and-phishing-scams-in-outlook-for-iOS-and-Android.md)

  > [!NOTE]
  > Si la création de rapports a été désactivée dans Outlook sur le [web,](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web)l’activation des soumissions d’utilisateurs ici remplace ce paramètre et permet aux utilisateurs de signaler à nouveau les messages dans Outlook sur le web.

Vous pouvez également configurer des outils de rapports de messages tiers pour transmettre des messages à la boîte aux lettres que vous spécifiez.

La livraison des messages signalés par l’utilisateur à une boîte aux lettres personnalisée au lieu de directement à Microsoft permet à vos administrateurs de signaler de manière sélective et manuelle des messages à Microsoft à l’aide de la soumission [d’administrateur.](admin-submission.md)

## <a name="custom-mailbox-prerequisites"></a>Conditions préalables pour la boîte aux lettres personnalisée

Utilisez les articles suivants pour configurer les conditions préalables requises afin que les messages signalés par l’utilisateur retournent dans votre boîte aux lettres personnalisée :

- Ignorez le filtrage du courrier indésirable sur la boîte aux lettres personnalisée en créant une règle de flux de messagerie Exchange pour définir le niveau de confiance du courrier indésirable. Voir [Utiliser le EAC](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) pour créer une règle de flux de messagerie qui définit le SCL d’un message pour définir le SCL sur **-1**.

- Désactiver l’analyse des pièces jointes pour les programmes malveillants dans la boîte aux lettres personnalisée. Utilisez configurer des stratégies de pièces jointes sécurisées dans Defender pour [Office 365](set-up-safe-attachments-policies.md) pour créer une stratégie de pièces jointes sécurisées avec le paramètre **Off** for **Safe Attachments unknown malware response**.

- Désactiver l’analyse des URL sur les messages dans la boîte aux lettres personnalisée. Utilisez configurer des stratégies de liens sûrs dans Defender pour [Office 365](set-up-safe-links-policies.md) pour créer une stratégie de liens sécurisés avec le paramètre **Off** pour sélectionner l’action pour les URL potentiellement malveillantes inconnues dans les **messages.**

- Créez une stratégie anti-programme malveillant pour désactiver la purge automatique sans heure de programmes malveillants. Voir Utiliser le Centre de sécurité & conformité pour créer des stratégies [anti-programme](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies) malveillant afin de définir la **purge** automatique sans heure de programmes **malveillants sur Hors service.**

- Créez une stratégie de filtrage du courrier indésirable pour désactiver la purge automatique d’heure zéro (ZAP) pour le courrier indésirable et le hameçonnage dans la boîte aux lettres personnalisée. Voir Utiliser le Centre de sécurité & conformité pour créer des stratégies [anti-courrier](configure-your-spam-filter-policies.md#use-the-security--compliance-center-to-create-anti-spam-policies) indésirable et effacer les case à cocher **Sur** pour spam **ZAP** et **PHISH ZAP**.

- Désactivez la règle de courrier indésirable dans la boîte aux lettres personnalisée. Utilisez [configurer les paramètres du courrier indésirable sur les](configure-junk-email-settings-on-exo-mailboxes.md) boîtes aux lettres Exchange Online pour désactiver la règle de courrier indésirable. Une fois désactivé, EOP ne peut pas déplacer les messages vers le dossier Courrier indésirable en fonction de l’action de verdict de filtrage du courrier indésirable Déplacer le **message** vers le dossier Courrier indésirable ou la collection de listes sécurisées sur la boîte aux lettres.

Une fois que vous avez vérifié que votre boîte aux lettres répond à toutes les conditions préalables applicables, utilisez le Centre de sécurité & conformité pour configurer la boîte aux lettres d’envoi [des utilisateurs](#use-the-security--compliance-center-to-configure-the-user-submissions-mailbox) (dans cet article).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com/>. Pour aller directement à la page **soumissions de l’utilisateur,** utilisez <https://protection.office.com/userSubmissionsReportMessage> .

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **Administrateur de sécurité** dans le [Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).
  - **Gestion de l’organisation** [dans Exchange Online.](/Exchange/permissions-exo/permissions-exo#role-groups)

- Vous devez accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevrez une erreur qui ressemble à ceci lorsque vous spécifiez la boîte aux lettres de soumission :

  > Spécifier une adresse de messagerie dans votre domaine

  Pour plus d’informations sur l’activation ou la désactivation de l’accès à Exchange Online PowerShell, consultez les rubriques suivantes :

  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell) 
  - [Règles d’accès client dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-security--compliance-center-to-configure-the-user-submissions-mailbox"></a>Utiliser le Centre de sécurité & conformité pour configurer la boîte aux lettres d’envoi des utilisateurs

1. Dans le Centre de sécurité & conformité, go to **Threat management** \> **Policy** \> **User submissions**.

2. Dans la page **Soumissions d’utilisateurs** qui s’affiche, sélectionnez l’une des options suivantes :

      1. Activez la fonctionnalité Message de rapport pour **Outlook (recommandé)**: sélectionnez cette option si vous utilisez le add-in Report Message, le add-in Report Phishing ou la création de rapports intégrée dans Outlook sur le web, puis configurez les paramètres suivants :

    - **Personnalisez le message de confirmation de l’utilisateur final**: cliquez sur ce lien. Dans le **flyout personnaliser le message** de confirmation qui s’affiche, configurez les paramètres suivants :

        - **Avant** l’envoi  : dans les zones de message Titre et **Confirmation,** entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du module de signalement du message ou du module de signalement du hameçonnage. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi (courrier indésirable, non indésirable, hameçonnage, etc.).

            Comme indiqué, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

        > Votre courrier électronique sera envoyé tel qu’il est à Microsoft pour analyse. Certains e-mails peuvent contenir des informations personnelles ou sensibles.

        - **Après l’envoi**: cliquez ![ sur Développer ](../../media/scc-expand-icon.png) l’icône . Dans **les** zones De titre et de **confirmation,** entrez le texte descriptif que les utilisateurs voient après qu’ils ont publié un message à l’aide du module de signalement du message ou du module de signalement du hameçonnage. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi.

      Lorsque vous avez terminé, cliquez sur **Enregistrer**. Pour effacer ces valeurs, cliquez sur **Restaurer** sur la page **Soumissions de l’utilisateur.**
    
    - **Personnalisez les options de rapport de l’utilisateur final**: cliquez sur ce lien. Dans le volant **Personnaliser les options de rapport** de l’utilisateur final qui s’affiche, entrez le texte descriptif des options de signalement du courrier indésirable. 
Sous **Options pour afficher le moment où les messages sont** signalés, sélectionnez au moins une des options suivantes :
        - **Demandez-moi avant d’envoyer un rapport**
        - **Envoyer automatiquement des rapports**
        -  **Ne jamais envoyer de rapports** \
   Lorsque vous avez terminé, cliquez sur **Enregistrer**.
              - **Envoyez les messages signalés à**: Effectuer l’une des sélections suivantes :
              - **Microsoft (recommandé)**: la boîte aux lettres d’envoi de l’utilisateur n’est pas utilisée (tous les messages signalés sont envoyés à Microsoft).
              - **Microsoft et une boîte aux lettres personnalisée**: dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les envois d’utilisateurs sont ensuite soumis à Microsoft pour analyse et à la boîte aux lettres personnalisée que votre équipe d’administration ou d’opérations de sécurité doit analyser.
              - **Boîte aux lettres personnalisée uniquement**: dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Utilisez cette option si vous souhaitez que le message ne soit envoyé qu’à un administrateur ou à l’équipe des opérations de sécurité pour analyse en premier. Les messages ne sont pas envoyés à Microsoft, sauf si l’administrateur les a transmis eux-mêmes.

        > [!NOTE]
        > Les organisations gouvernementales américaines (GCC, GCC-H et DoD) peuvent uniquement configurer une boîte **aux lettres personnalisée.** Les deux autres options sont désactivées.

        > [!NOTE]
        > Si les organisations sont configurées pour envoyer des messages à une boîte aux lettres personnalisée uniquement, les messages signalés ne seront pas envoyés pour réascaner et les résultats dans le portail Des messages signalés par l’utilisateur seront toujours vides.

      Lorsque vous avez terminé, cliquez sur **Confirmer.**

      > [!CAUTION]
      > Si vous avez désactivé la création de rapports de courrier indésirable dans [Outlook sur](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) le web à l’aide des stratégies de boîte aux lettres Outlook sur le web, mais que vous configurez l’un des paramètres précédents pour signaler des messages à Microsoft, les utilisateurs pourront signaler des messages à Microsoft dans Outlook sur le web à l’aide du add-in Report Message ou du module de signalement du hameçonnage.


    1. Désactivez la fonctionnalité Message de rapport pour **Outlook**: sélectionnez cette option si vous utilisez des outils de création de rapports tiers à la place du module de rapport de message, du module de signalement du hameçonnage ou de la création de rapports intégrée dans Outlook sur le web, puis configurez les paramètres suivants :

          Sélectionnez **Utiliser cette boîte aux lettres personnalisée pour recevoir les soumissions signalées par l’utilisateur.** Dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres existante qui se trouve déjà dans Office 365. Il doit s’agit d’une boîte aux lettres existante dans Exchange Online qui peut recevoir des messages électroniques.

          Lorsque vous avez terminé, cliquez sur **Confirmer.**

## <a name="message-submission-format"></a>Format de dépôt des messages

Les messages envoyés à des boîtes aux lettres personnalisées doivent respecter un format de courrier d’envoi spécifique. L’objet (titre de l’enveloppe) de l’envoi doit être au format ci-après :

`SafetyAPIAction|NetworkMessageId|SenderIp|FromAddress|(Message Subject)`

où SafetyAPIAction est l’une des valeurs d’un nombre integer suivantes :

- 1 : Courrier indésirable
- 2 : ne pas être indésirable
- 3 : Hameçonnage

Dans l’exemple suivant :

- Le message est signalé comme hameçonnage.
- L’ID de message réseau est 49871234-6dc6-43e8-abcd-08d797f20abe.
- L’adresse IP de l’expéditeur est 167.220.232.101.
- L’adresse de l’test@contoso.com.
- La ligne d’objet du message est « tester l’envoi de hameçonnage »

`3|49871234-6dc6-43e8-abcd-08d797f20abe|167.220.232.101|test@contoso.com|(test phishing submission)`

Les messages qui ne suivent pas ce format ne s’afficheront pas correctement dans le portail soumissions.
