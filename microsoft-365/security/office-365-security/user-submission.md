---
title: Paramètres de message signalés par l’utilisateur
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Les administrateurs peuvent apprendre à configurer une boîte aux lettres pour collecter le courrier indésirable et le hameçonnage signalés par les utilisateurs.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f09054a4ee57ce7105a7b2daffc65be5b91dc8f6
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839665"
---
# <a name="user-reported-message-settings"></a>Paramètres de message signalés par l’utilisateur

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online, vous pouvez spécifier une boîte aux lettres pour recevoir des messages que les utilisateurs signalent comme malveillants ou non malveillants. Lorsque les utilisateurs signalent des messages à l’aide des différentes options de création de rapports, vous pouvez utiliser cette boîte aux lettres pour intercepter les messages (envoyer à la boîte aux lettres personnalisée uniquement) ou recevoir des copies de messages (envoyer à la boîte aux lettres personnalisée et à Microsoft). Cette fonctionnalité fonctionne avec les options de création de rapports de messages suivantes :

- [Complément Message de rapport](enable-the-report-message-add-in.md)
- [Complément Report Phishing](enable-the-report-phish-add-in.md)
- [Outils de création de rapports tiers](#third-party-reporting-tools)

La remise de messages signalés par l’utilisateur à une boîte aux lettres personnalisée plutôt que directement à Microsoft permet à vos administrateurs de signaler manuellement et de manière sélective les messages à Microsoft à l’aide [de Administration soumission](admin-submission.md). Ces paramètres étaient auparavant appelés stratégie d’envoi d’utilisateurs.

  > [!NOTE]
  > Si la création de rapports a été [désactivée dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), l’activation des messages signalés par l’utilisateur ici remplace ce paramètre et permet aux utilisateurs de signaler à nouveau des messages dans Outlook sur le web.

## <a name="custom-mailbox-prerequisites"></a>Prérequis de boîte aux lettres personnalisée

Utilisez les articles suivants pour configurer les conditions préalables requises afin que les messages signalés par l’utilisateur soient envoyés à votre boîte aux lettres personnalisée :

- [Identifier la boîte aux lettres personnalisée en tant que boîte aux lettres SecOps dans la stratégie de remise avancée](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy)

- [Créez une stratégie anti-programme malveillant](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) pour la boîte aux **lettres** personnalisée où le vidage automatique de zéro heure (ZAP) pour les programmes malveillants est désactivé (la section \> Paramètres de protection **Activer le vidage automatique de zéro heure pour les programmes malveillants** n’est pas sélectionnée).

Si vous avez Microsoft Defender pour Office 365, vous devez également configurer les paramètres suivants afin que notre filtrage avancé n’affecte pas les utilisateurs qui signalent des messages :

- [Créez une stratégie de liens Coffre](set-up-safe-links-policies.md) pour la boîte aux lettres personnalisée où Coffre l’analyse des liens est désactivée (**sélectionnez l’action pour les URL potentiellement malveillantes inconnues dans** la section \> **Messages désactivés**).

- [Créez une stratégie de Coffre pièces jointes](set-up-safe-attachments-policies.md) pour la boîte aux lettres personnalisée où Coffre l’analyse des pièces jointes est désactivée (Coffre section \> Réponse **aux programmes malveillants inconnus des pièces jointes** **désactivée**).

Une fois que vous avez vérifié que votre boîte aux lettres répond à toutes les conditions préalables applicables, vous pouvez utiliser les procédures décrites dans cet article pour configurer la boîte aux lettres des soumissions d’utilisateurs.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/userSubmissionsReportMessage>.

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **administrateur de sécurité** dans les [autorisations du portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Vous devez accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevez une erreur semblable à celle-ci lors de la spécification de la boîte aux lettres d’envoi :

  > Spécifier une adresse e-mail dans votre domaine

  Pour plus d’informations sur l’activation ou la désactivation de l’accès à Exchange Online PowerShell, consultez les rubriques suivantes :

  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Règles d’accès client dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Utiliser le portail Microsoft 365 Defender pour configurer la boîte aux lettres des soumissions d’utilisateurs

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Stratégies & règles Stratégies** \> **de menace** \> Les **paramètres de message signalés par l’utilisateur** dans la section **Autres**. Pour accéder directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/userSubmissionsReportMessage>.

2. Dans la page **Soumissions de l’utilisateur**, ce que vous voyez est déterminé par le fait que le paramètre du **bouton Message de rapport microsoft Outlook** est **désactivé** ou **activé** :

   - **Bouton** \> Message de rapport Microsoft Outlook **activé** ![](../../media/scc-toggle-on.png): sélectionnez cette option si vous utilisez le complément Message de rapport, le complément Report Phishing ou le rapport intégré dans Outlook sur le web, puis configurez les paramètres suivants :
     - **Envoyez les messages signalés à** : Sélectionnez l’une des options suivantes :
       - **Microsoft** : la boîte aux lettres des soumissions utilisateur n’est pas utilisée (tous les messages signalés sont envoyés à Microsoft).
       - **Boîte aux lettres de Microsoft et de mon organisation** : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les soumissions d’utilisateurs sont envoyées à Microsoft à des fins d’analyse et à la boîte aux lettres personnalisée que votre équipe d’administration ou d’opérations de sécurité doit analyser.
       - **Boîte aux lettres de mon organisation** : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Utilisez cette option si vous souhaitez que le message ne soit envoyé qu’à un administrateur ou à l’équipe des opérations de sécurité pour l’analyse. Les messages ne seront pas envoyés à Microsoft, sauf si l’administrateur les transfère eux-mêmes.

          > [!IMPORTANT]
          > Les organisations du gouvernement américain (Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD) peuvent uniquement configurer **la boîte aux lettres de mon organisation**. Les deux autres options sont désactivées.
          >
          > Si les organisations sont configurées pour envoyer des messages signalés par l’utilisateur à la boîte aux lettres personnalisée uniquement, les messages signalés apparaissent dans les **messages signalés par l’utilisateur** , mais leurs résultats sont toujours vides (car ils n’auraient pas été réexécuter).

       Quelle que soit la valeur sélectionnée pour **envoyer les messages signalés**, les paramètres suivants sont disponibles :

       - **Permettre aux utilisateurs de choisir s’ils souhaitent signaler leur message à Microsoft**
       - **Sélectionnez les options de création de rapports disponibles pour les utilisateurs** : Sélectionnez au moins une des options suivantes :
         - **Demandez-moi avant d’envoyer le message**
         - **Toujours signaler le message**
         - **Ne jamais signaler le message**

          > [!CAUTION]
          > Si vous avez [désactivé la création de rapports de courrier indésirable dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) à l’aide de stratégies de boîte aux lettres Outlook sur le web, mais que vous avez configuré l’un des paramètres précédents pour signaler des messages à Microsoft, les utilisateurs seront en mesure de signaler des messages à Microsoft dans Outlook sur le web à l’aide du complément Message de rapport ou du complément Report Phishing.

     Laissez le **bouton Microsoft Outlook Report Message** activé ![](../../media/scc-toggle-on.png) **pour permettre** aux utilisateurs finaux de signaler des messages faux positifs à partir du portail de quarantaine.

     - **Section Expérience de création de rapports d’utilisateurs**
       - **Avant l’onglet Création de rapports** : dans les zones **titre** et **corps du message** , entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du complément Message de rapport ou du complément Report Phishing. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi (indésirable, pas indésirable, hameçonnage, etc.).
       - **Onglet Après la création de rapports** : dans les boîtes de message **Titre** et **Confirmation** , entrez le texte descriptif que les utilisateurs voient après avoir signalé un message à l’aide du complément Message de rapport ou du complément Hameçonnage de rapport. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi.
       - **Affichage uniquement lorsque l’utilisateur signale un hameçonnage** : vérifiez cette option si vous souhaitez afficher le message uniquement lorsqu’un e-mail est signalé comme hameçonnage. Si ce n’est pas le cas, les messages vérifiés s’affichent pour tout type de rapport.

       Comme indiqué sur la page, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

          > Votre e-mail sera envoyé tel quelle à Microsoft à des fins d’analyse. Certains e-mails peuvent contenir des informations personnelles ou sensibles.

   - Bouton Désactiver la désactivation du message  ![\> de rapport **Microsoft Outlook**.](../../media/scc-toggle-off.png) Sélectionnez cette option si vous utilisez des outils de création de rapports tiers au lieu du complément Message de rapport, du complément d’hameçonnage de rapport ou du rapport intégré dans Outlook sur le web, puis configurez les paramètres suivants :
     - Sélectionnez **Utiliser cette boîte aux lettres personnalisée pour recevoir les soumissions signalées par l’utilisateur**. Dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante qui peut recevoir des e-mails.

   - **Bouton Mettre en quarantaine les** messages de rapport : activez cette fonctionnalité si vous souhaitez permettre aux utilisateurs finaux de signaler des messages à partir d’une mise en quarantaine.

3. Lorsque vous avez terminé, cliquez sur **Confirmer**. Pour effacer ces valeurs, cliquez sur **Restaurer**.

## <a name="third-party-reporting-tools"></a>Outils de création de rapports tiers

Vous pouvez configurer des outils de création de rapports de messages tiers pour envoyer des messages signalés à la boîte aux lettres personnalisée. Pour ce faire, définissez le **bouton Message de rapport Microsoft Outlook** sur **Désactivé** et définissez la **boîte aux lettres de Mon organisation** sur une boîte aux lettres Office 365 de votre choix.

La seule exigence est que le message d’origine soit inclus en tant que . EML ou . Pièce jointe MSG (non compressée) dans le message envoyé à la boîte aux lettres personnalisée (ne vous contentez pas de transférer le message d’origine à la boîte aux lettres personnalisée). 

 > [!NOTE]
 > Si plusieurs pièces jointes sont présentes dans l’e-mail, la soumission est ignorée. Nous prenons uniquement en charge les e-mails avec une pièce jointe.

Les exigences de mise en forme des messages sont décrites dans la section suivante. La mise en forme est facultative, mais si elle ne suit pas le format prescrit, les rapports sont toujours soumis sous forme de hameçonnage.

## <a name="message-submission-format"></a>Format de soumission de message

Pour identifier correctement les messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée nécessitent une mise en forme spécifique. Si les messages n’utilisent pas ce format, les messages joints d’origine sont toujours identifiés comme des soumissions de hameçonnage.

Si vous souhaitez spécifier la raison signalée des messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée (ne modifiez pas la pièce jointe) doivent commencer par l’un des préfixes suivants dans l’objet (titre de l’enveloppe) :

- 1| ou Courrier indésirable :
- 2| ou non indésirable :
- 3| ou hameçonnage :

Par exemple :

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

- Ces deux messages sont signalés comme non indésirables en fonction de l’objet.
- Le reste est ignoré.

Les messages qui ne suivent pas ce format ne s’affichent pas correctement dans le portail Soumissions.
