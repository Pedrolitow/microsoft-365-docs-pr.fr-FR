---
title: Paramètres des messages signalés par l’utilisateur
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
ms.openlocfilehash: 525b761b09a68c3e44443cec7bf718d9eaa4d8d1
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327208"
---
# <a name="user-reported-message-settings"></a>Paramètres des messages signalés par l’utilisateur

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online, vous pouvez spécifier une boîte aux lettres pour recevoir des messages que les utilisateurs signalent comme malveillants ou non malveillants. Lorsque les utilisateurs signalent des messages à l’aide des différentes options de création de rapports, vous pouvez utiliser cette boîte aux lettres pour intercepter des messages (envoyer à la boîte aux lettres personnalisée uniquement) ou recevoir des copies de messages (envoyer à la boîte aux lettres personnalisée et Microsoft). Cette fonctionnalité fonctionne avec les options de rapport de message suivantes :

- [Le add-in Message de rapport](enable-the-report-message-add-in.md)
- [Le module de signalement du hameçonnage](enable-the-report-phish-add-in.md)
- [Outils de rapports tiers](#third-party-reporting-tools)

La livraison des messages signalés par l’utilisateur à une boîte aux lettres personnalisée au lieu de directement à Microsoft permet à vos administrateurs de signaler de manière sélective et manuelle des messages à Microsoft à l’aide de la soumission [d’administrateur](admin-submission.md). Ces paramètres étaient auparavant appelés stratégie d’envoi utilisateur.

  > [!NOTE]
  > Si la création de rapports a été désactivée dans [Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), l’activation des messages signalés par l’utilisateur ici remplace ce paramètre et permet aux utilisateurs de signaler les messages Outlook sur le web nouveau.

## <a name="custom-mailbox-prerequisites"></a>Conditions préalables pour la boîte aux lettres personnalisée

Utilisez les articles suivants pour configurer les conditions préalables requises afin que les messages signalés par l’utilisateur se placent dans votre boîte aux lettres personnalisée :

- Ignorez le filtrage du courrier indésirable sur la boîte aux lettres personnalisée en créant une règle de flux de messagerie Exchange pour définir le niveau de confiance du courrier indésirable. Voir [Utiliser le EAC](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) pour créer une règle de flux de messagerie qui définit le SCL d’un message pour définir le SCL sur Contourner le filtrage **du courrier indésirable**.

- Créez une stratégie [anti-programme](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) malveillant qui inclut la boîte aux lettres personnalisée dans laquelle la purge automatique d’heure zéro (ZAP) pour les programmes malveillants est désactivée (la section Paramètres de protection **Activez la purge** \> automatique heure zéro pour les programmes **malveillants** n’est pas sélectionnée).

- Créez une stratégie [anti-courrier](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) indésirable qui inclut la boîte aux lettres personnalisée dans laquelle ZAP pour le courrier indésirable et ZAP pour le hameçonnage sont désactivés **(la** section \> Purge automatique heure zéro activée pour la purge automatique (**ZAP)** n’est pas sélectionnée).

Si vous avez Microsoft Defender pour Office 365, vous devez également configurer les paramètres suivants afin que notre filtrage avancé n’a pas d’impact sur les utilisateurs signalant des messages :

- [Créez une stratégie de liens Coffre](set-up-safe-links-policies.md) qui inclut la boîte aux lettres personnalisée dans laquelle l’analyse des liens Coffre est désactivée (sélectionnez l’action pour les URL potentiellement malveillantes **inconnues** dans la section \> Messages **désactivée**).

- [Créez une stratégie Coffre pièces jointes](set-up-safe-attachments-policies.md) qui inclut la boîte aux lettres personnalisée dans laquelle l’analyse des pièces jointes Coffre est désactivée Coffre (section \> Pièces **jointes inconnues** de la réponse aux programmes malveillants **désactivée**).

Une fois que vous avez vérifié que votre boîte aux lettres répond à toutes les conditions préalables applicables, vous pouvez utiliser les procédures de cet article pour configurer la boîte aux lettres de soumission des utilisateurs.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/reportsubmission>.

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :

  - **Administrateur de la gestion** **de l’organisation** ou de la sécurité [dans les autorisations du Microsoft 365 Defender web](permissions-microsoft-365-security-center.md).

- Vous devez accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevrez une erreur qui ressemble à ceci lorsque vous spécifiez la boîte aux lettres de soumission :

  > Spécifier une adresse de messagerie dans votre domaine

  Pour plus d’informations sur l’activation ou la désactivation de l’accès Exchange Online PowerShell, consultez les rubriques suivantes :

  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Règles d’accès client dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Utiliser le portail Microsoft 365 Defender pour configurer la boîte aux lettres d’envoi des utilisateurs

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com>, go to **Policies &** \> **Threat policies Threat policies** \> **User reported message settings** in the **Others** section. Pour aller directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/reportsubmission>.

2. Dans la page **Soumissions d’utilisateurs**, ce que vous voyez est déterminé par le paramètre du bouton Message de rapport **Microsoft Outlook** est **Éteint** ou **Sur** :

   - Bouton Signaler le message  ![\> de **Microsoft Outlook** Sur bascule :](../../media/scc-toggle-on.png) sélectionnez cette option si vous utilisez le module de notification de message, le module de signalement du hameçonnage ou la création de rapports intégrée dans Outlook sur le web, puis configurez les paramètres suivants :
     - **Envoyez les messages signalés à** : Sélectionnez l’une des options suivantes :
       - **Microsoft** : la boîte aux lettres d’envoi utilisateur n’est pas utilisée (tous les messages signalés sont envoyés à Microsoft).
       - **Boîte aux lettres de Microsoft** et de mon organisation : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les envois d’utilisateurs sont ensuite soumis à Microsoft pour analyse et à la boîte aux lettres personnalisée que votre équipe d’administration ou d’opérations de sécurité doit analyser.
       - **Boîte aux lettres de mon** organisation : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Utilisez cette option si vous souhaitez que le message ne soit envoyé qu’à un administrateur ou à l’équipe des opérations de sécurité pour analyse en premier. Les messages ne sont pas envoyés à Microsoft, sauf si l’administrateur les a transmis eux-mêmes.

          > [!IMPORTANT]
          > Les organisations gouvernementales américaines (Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD) peuvent uniquement configurer la boîte aux lettres **de mon organisation**. Les deux autres options sont désactivées.
          >
          > Si les organisations sont configurées pour envoyer des messages à une boîte aux lettres personnalisée uniquement, les messages signalés ne seront pas envoyés pour la rescanée et les résultats dans le portail Des messages signalés par l’utilisateur seront toujours vides.

       Quelle que soit la valeur sélectionnée pour Envoyer les **messages** signalés, les paramètres suivants sont disponibles :

       - **Laisser les utilisateurs choisir s’ils souhaitent signaler leur message à Microsoft**
       - **Sélectionnez la section Options de rapport disponibles** pour les utilisateurs : sélectionnez au moins une des options suivantes :
         - **Demandez-moi avant d’envoyer le message**
         - **Toujours signaler le message**
         - **Ne jamais signaler le message**

          > [!CAUTION]
          > Si vous avez désactivé la création de rapports de courrier indésirable dans [Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) à l’aide de stratégies de boîte aux lettres Outlook sur le web, mais que vous avez configuré l’un des paramètres précédents pour signaler des messages à Microsoft, les utilisateurs pourront signaler des messages à Microsoft en Outlook sur le web à l’aide du module de signalement des messages ou du module de signalement du hameçonnage.

     Laissez le **paramètre De message de** ![](../../media/scc-toggle-on.png) Outlook Microsoft sur Le bouton Bascule pour permettre aux utilisateurs finaux de signaler des messages faux positifs à partir du portail de mise en quarantaine.

     - **Section Expérience de rapport utilisateur**
       - **Avant** de signaler l’onglet  : dans les zones Titre et corps du **message**, entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du add-in Signaler un message ou du module de signalement du hameçonnage. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi (courrier indésirable, non indésirable, hameçonnage, etc.).
       - **Onglet** Après rapport : dans les  zones Titre et **Confirmation**, entrez le texte descriptif que les utilisateurs voient après avoir signalé un message à l’aide du module de signalement du message ou du module de signalement du hameçonnage. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi.
       - **Affichage uniquement lorsque l’utilisateur signale** un hameçonnage : cochez cette option si vous souhaitez afficher le message uniquement lorsqu’un e-mail est signalé comme hameçonnage. Si ce n’est pas le cas, les messages vérifiés s’afficheront pour n’importe quel type de rapport.

       Comme indiqué sur la page, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

          > Votre courrier électronique sera envoyé tel qu’il est à Microsoft pour analyse. Certains e-mails peuvent contenir des informations personnelles ou sensibles.

   - Bouton Message de rapport **Microsoft Outlook** \>  ![Désélectrable:](../../media/scc-toggle-off.png) sélectionnez cette option si vous utilisez des outils de création de rapports tiers à la place du module de rapport de message, du module de signalement du hameçonnage ou de la création de rapports intégrée dans Outlook sur le web, puis configurez les paramètres suivants :
     - Sélectionnez **Utiliser cette boîte aux lettres personnalisée pour recevoir les soumissions signalées par l’utilisateur**. Dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante qui peut recevoir du courrier électronique.

   - **Bouton De message de rapport de mise en** quarantaine : activez cette fonctionnalité si vous souhaitez permettre aux utilisateurs finaux de signaler des messages en quarantaine.

   Lorsque vous avez terminé, cliquez sur **Confirmer**. Pour effacer ces valeurs, cliquez sur **Restaurer**

## <a name="third-party-reporting-tools"></a>Outils de rapports tiers

Vous pouvez configurer des outils de création de rapports de messages tiers pour envoyer des messages signalés à la boîte aux lettres personnalisée. Pour ce faire, vous devez définir le paramètre du bouton Message de rapport **Microsoft Outlook** sur  « Off » et  définir la boîte aux lettres de mon organisation sur une boîte aux lettres Office 365 de votre choix.

La seule condition est que le message d’origine soit inclus en tant que . EML ou . Pièce jointe MSG (non compressée) dans le message envoyé à la boîte aux lettres personnalisée (ne pas simplement transmettre le message d’origine à la boîte aux lettres personnalisée).

Les exigences de mise en forme des messages sont décrites dans la section suivante. La mise en forme est facultative, mais si elle ne suit pas le format prescrit, les rapports sont toujours soumis comme hameçonnage.

## <a name="message-submission-format"></a>Format de dépôt des messages

Pour identifier correctement les messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée nécessitent une mise en forme spécifique. Si les messages n’utilisent pas ce format, les messages joints d’origine sont toujours identifiés comme des envois de hameçonnage.

Si vous souhaitez spécifier la raison signalée des messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée (ne modifiez pas la pièce jointe) doivent commencer par l’un des préfixes suivants dans l’objet (titre de l’enveloppe) :

- 1| ou courrier indésirable :
- 2| ou non indésirable
- 3| ou hameçonnage

Par exemple :

`3|This part is ignored by the system` <br>
`Not Junk:This part of the subject is ignored as well`

- Ces deux messages sont signalés comme non indésirables en fonction de l’objet.
- Le reste est ignoré.


Les messages qui ne suivent pas ce format ne s’afficheront pas correctement dans le portail soumissions.
