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
ms.openlocfilehash: f565a71b44d27076ea6ff0b25be5d5b3932913c9
ms.sourcegitcommit: 4d26a57c37ff7efbb8d235452c78498b06a59714
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/22/2021
ms.locfileid: "53052986"
---
# <a name="user-submissions-policy"></a>Stratégie de soumissions d’utilisateurs

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans Microsoft 365 organisations avec des boîtes aux lettres Exchange Online, vous pouvez spécifier une boîte aux lettres pour recevoir des messages que les utilisateurs signalent comme malveillants ou non malveillants. Lorsque les utilisateurs envoient des messages à l’aide des différentes options de création de rapports, vous pouvez utiliser cette boîte aux lettres pour intercepter des messages (envoyer à la boîte aux lettres personnalisée uniquement) ou recevoir des copies de messages (envoyer à la boîte aux lettres personnalisée et Microsoft). Cette fonctionnalité fonctionne avec les options de rapport de message suivantes :

- [Le add-in Message de rapport](enable-the-report-message-add-in.md)
- [Le module de signalement du hameçonnage](enable-the-report-phish-add-in.md)
- [Outils de rapports tiers](#third-party-reporting-tools)

La livraison des messages signalés par l’utilisateur à une boîte aux lettres personnalisée au lieu de directement à Microsoft permet à vos administrateurs de signaler de manière sélective et manuelle des messages à Microsoft à l’aide de la soumission [d’administrateur.](admin-submission.md)

  > [!NOTE]
  > Si la création de rapports a été désactivée [dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), l’activation des soumissions d’utilisateurs ici remplace ce paramètre et permet aux utilisateurs de signaler des messages Outlook sur le web nouveau.

## <a name="custom-mailbox-prerequisites"></a>Conditions préalables pour la boîte aux lettres personnalisée

Utilisez les articles suivants pour configurer les conditions préalables requises afin que les messages signalés par l’utilisateur retournent dans votre boîte aux lettres personnalisée :

- Ignorez le filtrage du courrier indésirable sur la boîte aux lettres personnalisée en créant une règle de flux de messagerie Exchange pour définir le niveau de confiance du courrier indésirable. Voir [Utiliser le EAC](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl#use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message) pour créer une règle de flux de messagerie qui définit le SCL d’un message pour définir le SCL pour contourner le filtrage du courrier **indésirable.**

- [Créez une stratégie Coffre](set-up-safe-attachments-policies.md) pièces jointes qui inclut la boîte aux lettres personnalisée dans laquelle l’analyse des pièces jointes Coffre est désactivée ( Coffre section De réponse aux programmes **malveillants inconnus** pièces jointes \> **désactivée**).

- [Créez une stratégie Coffre](set-up-safe-links-policies.md) liens qui inclut la boîte aux lettres personnalisée dans laquelle l’analyse des liens Coffre est désactivée ( Sélectionnez l’action pour les URL potentiellement malveillantes **inconnues** dans la section messages \> **désactivée).**

- Créez une stratégie [anti-programme](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) malveillant qui inclut la boîte aux lettres personnalisée dans laquelle la purge automatique d’heure zéro (ZAP) pour les programmes malveillants est désactivée (la section Paramètres de protection Activez la purge automatique heure zéro pour les programmes **malveillants** n’est pas \>  sélectionnée).

- Créez une stratégie [anti-courrier](configure-your-spam-filter-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-spam-policies) indésirable qui inclut la boîte aux lettres personnalisée dans laquelle ZAP pour le courrier indésirable et ZAP pour le hameçonnage sont désactivés **(la** section Purge automatique heure zéro activée pour la purge automatique \> **(ZAP)** n’est pas sélectionnée).

- Désactivez la règle de courrier indésirable dans la boîte aux lettres personnalisée. Utilisez [configurer les paramètres de courrier indésirable sur Exchange Online boîtes aux](configure-junk-email-settings-on-exo-mailboxes.md) lettres pour désactiver la règle de courrier indésirable. Une fois désactivé, EOP ne peut pas déplacer les messages vers le dossier Courrier indésirable en fonction de l’action de verdict de filtrage du courrier indésirable Déplacer le **message** vers le dossier Courrier indésirable ou la collection de listes sécurisées de la boîte aux lettres.

Une fois que vous avez vérifié que votre boîte aux lettres répond à toutes les conditions préalables applicables, vous pouvez utiliser les procédures de cet article pour configurer la boîte aux lettres d’envoi des utilisateurs.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com/>. Pour aller directement à la page **Soumissions,** utilisez <https://security.microsoft.com/reportsubmission> .

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :

  - **Administrateur de la gestion** **de l’organisation** ou de la sécurité [dans Microsoft 365 Defender portail.](permissions-in-the-security-and-compliance-center.md)
  - **Gestion de l’organisation** [dans Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups).

- Vous devez accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevrez une erreur qui ressemble à ceci lorsque vous spécifiez la boîte aux lettres de soumission :

  > Spécifier une adresse de messagerie dans votre domaine

  Pour plus d’informations sur l’activation ou la désactivation de l’accès Exchange Online PowerShell, consultez les rubriques suivantes :

  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell) 
  - [Règles d’accès client Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox"></a>Utiliser le portail Microsoft 365 Defender pour configurer la boîte aux lettres d’envoi des utilisateurs

1. In the Microsoft 365 Defender portal, go to **Policies & threat** \> **policies** \> **Others** section \> **User reported message settings** User \> **submissions**.

2. Dans la page **Soumissions d’utilisateurs,** ce que vous voyez est déterminé par le paramètre du bouton Message de rapport **Microsoft Outlook** est **Éteint** ou **Sur**:

   - **Bouton Signaler Outlook** \> Microsoft **On** ![ Bascule : sélectionnez cette option si vous utilisez le add-in Signaler un message, le module de signalement du hameçonnage ou la création de rapports intégrée dans Outlook sur le web, puis configurez les ](../../media/scc-toggle-on.png) paramètres suivants :
     - **Envoyez les messages signalés à**: Sélectionnez l’une des options suivantes :
       - **Microsoft**: la boîte aux lettres d’envoi utilisateur n’est pas utilisée (tous les messages signalés sont envoyés à Microsoft).
       - **Microsoft et la boîte aux lettres** de mon organisation : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les envois d’utilisateurs sont ensuite soumis à Microsoft pour analyse et à la boîte aux lettres personnalisée que votre équipe d’administration ou d’opérations de sécurité doit analyser.
       - **Boîte aux lettres de mon** organisation : dans la zone qui s’affiche, entrez l’adresse de messagerie d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Utilisez cette option si vous souhaitez que le message ne soit envoyé qu’à un administrateur ou à l’équipe des opérations de sécurité pour analyse en premier. Les messages ne sont pas envoyés à Microsoft, sauf si l’administrateur les a transmis eux-mêmes.

          > [!IMPORTANT]
          >
          > Les organisations gouvernementales américaines (Cloud de la communauté du secteur public, Cloud de la communauté du secteur public High et DoD) peuvent uniquement configurer la boîte aux lettres **de mon organisation.** Les deux autres options sont désactivées.
          >
          > Si les organisations sont configurées pour envoyer des messages à une boîte aux lettres personnalisée uniquement, les messages signalés ne seront pas envoyés pour réascaner et les résultats dans le portail Des messages signalés par l’utilisateur seront toujours vides.

       Quelle que soit la valeur que vous avez sélectionnée pour Envoyer les **messages** signalés, les paramètres suivants sont disponibles :

       - **Laisser les utilisateurs choisir s’ils souhaitent signaler leur message à Microsoft**
       - **Sélectionnez la section Options de rapport disponibles pour** les utilisateurs : sélectionnez au moins une des options suivantes :
         - **Demandez-moi avant d’envoyer le message.**
         - **Toujours signaler le message**
         - **Ne jamais signaler le message**

          > [!CAUTION]
          > Si vous avez désactivé la création de rapports de courrier indésirable dans [Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web) à l’aide de stratégies de boîte aux lettres Outlook sur le web, mais que vous avez configuré l’un des paramètres précédents pour signaler des messages à Microsoft, les utilisateurs pourront signaler des messages à Microsoft en Outlook sur le web à l’aide du module de signalement des messages ou du module de signalement du hameçonnage.

     - **Section Expérience de rapport utilisateur**
       - **Avant** de signaler  l’onglet : dans les zones Titre et corps du **message,** entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du add-in Signaler un message ou du module de signalement du hameçonnage. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi (courrier indésirable, non indésirable, hameçonnage, etc.).
       - **Onglet** Après rapport  :  dans les zones Titre et Confirmation, entrez le texte descriptif que les utilisateurs voient après qu’ils ont signalé un message à l’aide du add-in Report Message ou du add-in Report Phishing. Vous pouvez utiliser la variable %type% pour inclure le type d’envoi.

       Comme indiqué sur la page, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

          > Votre courrier électronique sera envoyé tel qu’il est à Microsoft pour analyse. Certains e-mails peuvent contenir des informations personnelles ou sensibles.

   - **Bouton Signaler Outlook** \> Microsoft **Off** ![ Basculez : sélectionnez cette option si vous utilisez des outils de création de rapports tiers à la place du module de rapport de message, du module de signalement du hameçonnage ou de la création de rapports intégrée dans Outlook sur le web, puis configurez les ](../../media/scc-toggle-off.png) paramètres suivants :
     - Sélectionnez **Utiliser cette boîte aux lettres personnalisée pour recevoir les soumissions signalées par l’utilisateur.** Dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante qui peut recevoir du courrier électronique.

   Lorsque vous avez terminé, cliquez sur **Confirmer.** Pour effacer ces valeurs, cliquez sur **Restaurer**

## <a name="third-party-reporting-tools"></a>Outils de rapports tiers

Vous pouvez configurer des outils de création de rapports de messages tiers pour envoyer des messages signalés à la boîte aux lettres personnalisée. Pour ce faire, vous devez définir le paramètre  du bouton  Message de rapport **Microsoft Outlook** sur Off et définir la boîte aux lettres de mon organisation sur une boîte aux lettres Office 365 de votre choix.

La seule condition est que le message d’origine soit inclus en tant que . EML ou . Pièce jointe MSG (non compressée) dans le message envoyé à la boîte aux lettres personnalisée (ne pas simplement transmettre le message d’origine à la boîte aux lettres personnalisée).

Les exigences de mise en forme des messages sont décrites dans la section suivante. La mise en forme est facultative, mais si elle ne suit pas le format prescrit, les rapports sont toujours soumis comme hameçonnage.

## <a name="message-submission-format"></a>Format de dépôt des messages

Pour identifier correctement les messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée nécessitent une mise en forme spécifique. Si les messages n’utilisent pas ce format, les messages joints d’origine sont toujours identifiés comme des envois de hameçonnage.

Pour identifier correctement les messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée doivent utiliser la syntaxe suivante pour l’objet (titre de l’enveloppe) :

`SafetyAPIAction|NetworkMessageId|SenderIp|FromAddress|(Message Subject)`

où SafetyAPIAction est l’une des valeurs d’un nombre integer suivantes :

- 1 : Courrier indésirable
- 2 : ne pas être indésirable
- 3 : Hameçonnage

Cet exemple utilise les valeurs suivantes :

- Le message est signalé comme hameçonnage.
- L’ID de message réseau est 49871234-6dc6-43e8-abcd-08d797f20abe.
- L’adresse IP de l’expéditeur est 167.220.232.101.
- L’adresse de l’test@contoso.com.
- La ligne d’objet du message est « tester l’envoi de hameçonnage »

`3|49871234-6dc6-43e8-abcd-08d797f20abe|167.220.232.101|test@contoso.com|(test phishing submission)`

Les messages qui ne suivent pas ce format ne s’afficheront pas correctement dans le portail soumissions.
