---
title: Paramètres d’e-mail signalés par l’utilisateur pour le courrier indésirable, le hameçonnage, comme courrier malveillant
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: 07/19/2022
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: ''
description: Les administrateurs peuvent apprendre à identifier une boîte aux lettres personnalisée (également appelée boîte aux lettres de soumissions d’utilisateurs) pour collecter les messages de courrier indésirable et de hameçonnage signalés par les utilisateurs. D’autres paramètres complètent l’expérience de création de rapports pour les utilisateurs lorsqu’ils signalent des messages.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: e09b5f7d6f34ac1daa98430f1bc868b4ca644777
ms.sourcegitcommit: cd9df1a681265905eef99c039f7036b2fa6e8b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/07/2022
ms.locfileid: "67276303"
---
# <a name="user-reported-message-settings"></a>Paramètres des messages signalés par l’utilisateur

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online, vous pouvez diriger le courrier vers une boîte aux lettres personnalisée (également appelée boîte _aux lettres de soumissions d’utilisateurs_) lorsque les utilisateurs signalent des messages malveillants ou non malveillants. Lorsque les utilisateurs signalent des messages électroniques à l’aide des options de création de rapports prises en charge, les administrateurs peuvent configurer les paramètres de message signalés par l’utilisateur dans leur organisation pour envoyer des messages signalés à la boîte aux lettres d’envoi des utilisateurs. Vous pouvez configurer la boîte aux lettres de soumissions utilisateur pour intercepter les messages signalés par l’utilisateur (envoyer à la boîte aux lettres des soumissions utilisateur uniquement) ou recevoir des copies des messages signalés par l’utilisateur lorsque les utilisateurs signalent des messages à Microsoft. Ces paramètres étaient auparavant _appelés stratégie d’envoi d’utilisateurs_.

Les paramètres de message signalés par l’utilisateur et la boîte aux lettres d’envoi de l’utilisateur fonctionnent avec les options de création de rapports de messages suivantes :

- [Complément Message de rapport](enable-the-report-message-add-in.md)
- [Complément Report Phishing](enable-the-report-phish-add-in.md)
- [Outils de création de rapports tiers](#third-party-reporting-tools-options)

La remise de messages signalés par l’utilisateur à une boîte aux lettres de soumissions utilisateur au lieu de les envoyer directement à Microsoft permet aux administrateurs de signaler manuellement et de manière sélective les messages à Microsoft sur la page **Soumissions** à l’adresse <https://security.microsoft.com/reportsubmission>suivante : Pour plus d’informations, consultez [Administration soumission](admin-submission.md).

  > [!NOTE]
  > Si la création de rapports a été [désactivée dans Outlook sur le web](report-junk-email-and-phishing-scams-in-outlook-on-the-web-eop.md#disable-or-enable-junk-email-reporting-in-outlook-on-the-web), l’activation des messages signalés par l’utilisateur ici remplace ce paramètre et permet aux utilisateurs de signaler à nouveau des messages dans Outlook sur le web.

## <a name="configuration-requirements-for-the-user-submissions-mailbox"></a>Configuration requise pour la boîte aux lettres des soumissions d’utilisateurs

Avant de commencer, vous devez configurer Exchange Online Protection et Defender pour Office 365 afin que les messages signalés par l’utilisateur soient remis à la boîte aux lettres des soumissions utilisateur sans être filtrés comme décrit dans les étapes suivantes :

- Identifiez la boîte aux lettres des soumissions utilisateur en tant que boîte aux lettres SecOps. Pour obtenir des instructions, consultez [Utiliser le portail Microsoft 365 Defender pour configurer les boîtes aux lettres SecOps dans la stratégie de remise avancée](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).

- Créez une stratégie anti-programme malveillant personnalisée pour la boîte aux lettres d’envoi des utilisateurs avec les paramètres suivants :

  - Désactivez le vidage automatique de zéro heure (ZAP) pour **les programmes malveillants** (section \> Paramètres de protection **Activer le vidage automatique de zéro heure pour les programmes malveillants** n’est pas sélectionné ou `-ZapEnabled $false` dans PowerShell).

  - Désactivez le filtrage des pièces jointes courantes (section \>**Paramètres de protection** **Activer que le filtre de pièces jointes communs** n’est pas sélectionné ou `EnableFileFilter $false` dans PowerShell).
  
  Pour obtenir des instructions, consultez [Créer une stratégie anti-programme malveillant](configure-anti-malware-policies.md#use-the-microsoft-365-defender-portal-to-create-anti-malware-policies).

- Vérifiez que la boîte aux lettres des soumissions utilisateur n’est pas incluse dans les stratégies de sécurité prédéfinies **Standard** ou **Strict** . Pour obtenir des instructions, consultez [Stratégies de sécurité prédéfinies](preset-security-policies.md).

- **Defender pour Office 365** : Configurez les paramètres supplémentaires suivants :

  - Excluez la boîte aux lettres des soumissions d’utilisateurs de la stratégie de sécurité prédéfinies de **protection intégrée** . Pour obtenir des instructions, consultez [Stratégies de sécurité prédéfinies](preset-security-policies.md).

  - Créez une stratégie de pièces jointes sécurisées pour la boîte aux lettres des soumissions d’utilisateurs dans laquelle l’analyse des pièces jointes sécurisées, y compris la livraison dynamique, est désactivée (section \> Paramètres de la réponse aux programmes **malveillants inconnus paramètres** \> **pièces jointes non fiables** **désactivée** ou `-Enable $false` dans PowerShell). Pour obtenir des instructions, consultez [Configurer des stratégies de pièces jointes sécurisées dans Microsoft Defender pour Office 365](set-up-safe-attachments-policies.md).

  - Créez une stratégie de liens fiables pour la boîte aux lettres de soumissions d’utilisateurs où l’analyse des liens sécurisés dans le courrier électronique est désactivée (**URL & paramètres de protection activés** **: liens fiables vérifie une liste de liens connus et malveillants lorsque les utilisateurs cliquent sur des liens dans le courrier électronique** n’est pas sélectionné ou `EnableSafeLinksForEmail $false` dans PowerShell).\> Pour obtenir des instructions, consultez [Configurer des stratégies de liens fiables dans Microsoft Defender pour Office 365](set-up-safe-links-policies.md).

Une fois que vous avez vérifié que la boîte aux lettres répond à ces exigences, suivez les instructions de cet article pour identifier la boîte aux lettres des soumissions utilisateur et les autres paramètres de message signalés par l’utilisateur.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/userSubmissionsReportMessage>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Pour modifier la configuration des soumissions d’utilisateurs, vous devez être membre de l’un des groupes de rôles suivants :

  - **Gestion de l’organisation** ou **administrateur de sécurité** dans les [autorisations du portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Vous devez accéder à Exchange Online PowerShell. Si le compte que vous essayez d’utiliser n’a pas accès à Exchange Online PowerShell, vous recevez une erreur semblable à celle-ci lors de la spécification de la boîte aux lettres d’envoi :

  > Spécifier une adresse e-mail dans votre domaine

  Pour plus d’informations sur l’activation ou la désactivation de l’accès à Exchange Online PowerShell, consultez les rubriques suivantes :

  - [Activer ou désactiver l’accès à Exchange Online PowerShell](/powershell/exchange/disable-access-to-exchange-online-powershell)
  - [Règles d’accès client dans Exchange Online](/exchange/clients-and-mobile-in-exchange-online/client-access-rules/client-access-rules)

## <a name="use-the-microsoft-365-defender-portal-to-configure-the-user-submissions-mailbox-for-email"></a>Utiliser le portail Microsoft 365 Defender pour configurer la boîte aux lettres des envois d’utilisateurs pour les e-mails

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Stratégies & règles Stratégies** \> **de menace** \> Les **paramètres de message signalés par l’utilisateur** dans la section **Autres**. Pour accéder directement à la page **Soumissions de l’utilisateur** , utilisez <https://security.microsoft.com/userSubmissionsReportMessage>.

2. Dans la page **Soumissions d’utilisateurs** , ce que vous voyez est en grande partie déterminé par le bouton Bascule du **bouton Message de rapport Microsoft Outlook** :

   - **Sur** ![ Activer/désactiver .](../../media/scc-toggle-on.png) : vous utilisez l’expérience de création de rapports intégrée à Microsoft, qui inclut le complément Message de rapport, le complément d’hameçonnage de rapport ou le rapport intégré dans Outlook sur le web.

     Ce paramètre permet également aux utilisateurs de signaler des messages faux positifs à partir du portail de quarantaine.

   - **Désactivé** ![ Désactiver.](../../media/scc-toggle-off.png) : vous utilisez des outils de création de rapports de messages tiers au lieu de l’expérience de création de rapports intégrée à Microsoft.

Les options de configuration associées sont décrites dans les sections suivantes.

### <a name="microsoft-integrated-reporting-experience-options"></a>Options d’expérience de création de rapports intégrées Microsoft

Lorsque le **bouton Message de rapport Microsoft Outlook** **est** ![activé](../../media/scc-toggle-on.png), les paramètres suivants sont disponibles sur la page **Soumissions de l’utilisateur** :

- **Envoyer les messages signalés à la** section : Sélectionnez l’une des options suivantes :

  - **Microsoft** : les rapports utilisateur sont directement accessibles à Microsoft pour analyse. Seules les métadonnées telles que l’expéditeur, le destinataire, signalés par et les détails du message des rapports utilisateur sont fournies à l’administrateur client via le portail Microsoft 365 Defender.

  - **Boîte aux lettres de Microsoft et de mon organisation** : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante à utiliser comme boîte aux lettres de soumissions utilisateur. Les groupes de distribution ne sont pas autorisés. Les soumissions d’utilisateurs sont envoyées à Microsoft à des fins d’analyse et à la boîte aux lettres des soumissions d’utilisateurs pour qu’une équipe d’administrateurs ou d’opérations de sécurité analyse.

  - **Boîte aux lettres de mon organisation** : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante. Les groupes de distribution ne sont pas autorisés. Les soumissions d’utilisateurs sont envoyées uniquement à la boîte aux lettres des soumissions d’utilisateurs qu’un administrateur ou l’équipe des opérations de sécurité doit analyser. Les messages ne sont pas envoyés à Microsoft pour analyse, sauf si un administrateur envoie manuellement les messages.

  > [!IMPORTANT]
  > Dans les organisations du gouvernement des États-Unis (GCC, GCC High et DoD), la seule sélection disponible dans la section **Envoyer les messages signalés** est la **boîte aux lettres de mon organisation**. Les deux autres options sont grisées.
  >
  > Si vous avez utilisé [Outlook sur le web stratégies de boîte aux lettres](/exchange/clients-and-mobile-in-exchange-online/outlook-on-the-web/configure-outlook-web-app-mailbox-policy-properties) pour désactiver la création de rapports de courrier indésirable dans Outlook sur le web, mais que vous sélectionnez **Microsoft** ou **Microsoft et la boîte aux lettres de mon organisation**, les utilisateurs peuvent signaler des messages à Microsoft dans Outlook sur le web à l’aide du complément Message de rapport ou du complément Report Phishing.
  >
  > Si vous sélectionnez **la boîte aux lettres de mon organisation**, les messages signalés apparaissent dans **l’onglet Messages signalés par l’utilisateur** dans la page **Soumissions** à l’adresse <https://security.microsoft.com/reportsubmission>. Toutefois, la valeur **résultat** de ces messages sera toujours vide, car les messages n’ont pas été réexécuter.
  >
  > Si vous utilisez une [formation de simulation d’attaque](attack-simulation-training-get-started.md) ou un produit tiers pour effectuer des simulations d’hameçonnage, vous devez configurer la boîte aux lettres des soumissions utilisateur en tant que boîte aux lettres SecOps, comme décrit précédemment dans la section [Configuration requise pour la boîte aux lettres des soumissions utilisateur](#configuration-requirements-for-the-user-submissions-mailbox) plus haut dans cet article. Si ce n’est pas le cas, un utilisateur signalant un message peut déclencher une affectation d’entraînement dans le produit de simulation d’hameçonnage.

  Quelle que soit votre sélection, les paramètres suivants sont également disponibles dans la section **Envoyer les messages signalés à** la section :

  - **Laissez les utilisateurs choisir s’ils souhaitent signaler** : ce paramètre contrôle les options disponibles dans la section **Sélectionner les options de création de rapports disponibles pour les utilisateurs** :

    - **Laissez les utilisateurs choisir s’ils souhaitent signaler** la sélection : vous pouvez sélectionner certains paramètres, tous ou aucun, dans la section **Sélectionner les options de création de rapports disponibles pour les utilisateurs** .
    - **Laissez les utilisateurs choisir s’ils souhaitent signaler qu’ils** ne sont pas sélectionnés : vous ne pouvez sélectionner qu’un seul paramètre dans la section **Sélectionner les options de création de rapports disponibles pour les utilisateurs** .

    - **Sélectionnez les options de création de rapports disponibles pour les utilisateurs** :
      - **Demandez-moi avant d’envoyer le message**
      - **Toujours signaler le message**
      - **Ne jamais signaler le message**

- **Section Expérience de création de rapports** utilisateur : Les paramètres suivants sont disponibles :

  Comme indiqué sur la page, si vous sélectionnez une option qui envoie les messages signalés à Microsoft, le texte suivant est également ajouté à la notification :

  > Votre e-mail sera envoyé tel quelle à Microsoft à des fins d’analyse. Certains e-mails peuvent contenir des informations personnelles ou sensibles.

  - **Avant l’onglet Création de rapports** : dans les zones **titre** et **corps du message** , entrez le texte descriptif que les utilisateurs voient avant de signaler un message à l’aide du complément Message de rapport ou du complément Report Phishing. Vous pouvez utiliser la variable `%type%` pour inclure le type de soumission (courrier indésirable, non indésirable, hameçonnage, etc.).
  - **Onglet Après la création de rapports** : dans les boîtes de message **Titre** et **Confirmation** , entrez le texte descriptif que les utilisateurs voient après avoir signalé un message à l’aide du complément Message de rapport ou du complément Hameçonnage de rapport. Vous pouvez utiliser la variable `%type%` pour inclure le type de soumission.

  - **Affichage uniquement lorsque l’utilisateur signale un hameçonnage** : sélectionnez cette option pour afficher les notifications **Avant** et **Après la création de rapports** uniquement lorsque les utilisateurs signalent des messages comme hameçonnage. Sinon, les notifications s’affichent pour tous les messages signalés.

- **Email notifications pour la section des résultats de la révision administrateur** : Les paramètres suivants sont disponibles :

  - **Spécifiez Office 365 adresse e-mail à utiliser comme expéditeur** : sélectionnez ce paramètre et entrez l’adresse e-mail dans la zone qui s’affiche.
  
  - **Personnaliser les notifications** : cliquez sur ce lien pour personnaliser la notification par e-mail envoyée après un avis d’administrateur et marque un message signalé.

    Dans le menu volant **Personnaliser le message de confirmation** qui s’affiche, configurez les paramètres suivants :

    - **Onglets Hameçonnage**, **Courrier indésirable** et **Aucune menace trouvée** : dans le **texte du résultat** de révision sur certains, aucun ou tous les onglets, entrez le texte personnalisé à utiliser.
    - **Onglet Pied de page** : Les options suivantes sont disponibles :
      - **Texte du pied** de page : entrez le texte du pied de page de message personnalisé à utiliser.
      - **Afficher le logo de l’entreprise** : avant de sélectionner cette option, vous devez suivre les instructions fournies dans [Personnaliser le thème Microsoft 365 pour que votre organisation](../../admin/setup/customize-your-organization-theme.md) charge votre logo personnalisé.

  Lorsque vous avez terminé le menu volant **Personnaliser le message de confirmation** , cliquez sur **Confirmer**.

- **Personnalisez l’expérience de votre organisation lors de la création de rapports de menaces potentielles dans la section de mise en quarantaine** :

  **Bouton de message de rapport de mise en quarantaine** : vérifiez que ce paramètre est **activé**![.](../../media/scc-toggle-on.png) pour permettre aux utilisateurs de signaler des messages à partir d’une mise en quarantaine. Sinon, **désactivez** ![ce paramètre désactivé](../../media/scc-toggle-off.png).

Lorsque vous avez terminé sur la page **Soumissions de l’utilisateur** , cliquez sur **Enregistrer**. Pour restaurer les paramètres à leurs valeurs immédiatement antérieures, cliquez sur **Restaurer**.

### <a name="third-party-reporting-tools-options"></a>Options des outils de création de rapports tiers

Vous pouvez désactiver l’expérience de création de rapports intégrée à Microsoft pour utiliser des outils de création de rapports de messages tiers pour envoyer des messages signalés à la boîte aux lettres d’envoi des utilisateurs.

La seule exigence est que les messages d’origine sont inclus comme non compressés . EML ou . Pièces jointes MSG dans les messages envoyés à la boîte aux lettres d’envoi des utilisateurs. En d’autres termes, ne vous contentez pas de transférer les messages d’origine à la boîte aux lettres d’envoi des utilisateurs.

> [!NOTE]
> S’il existe plusieurs pièces jointes dans le message, la soumission est ignorée. Nous ne prenons en charge le message qu’avec une seule pièce jointe.

Les exigences de mise en forme des messages sont décrites dans la section suivante. La mise en forme est facultative, mais les messages signalés ne suivent pas le format prescrit. Les messages signalés sont toujours identifiés comme hameçonnage.

Lorsque **le bouton Message de rapport Microsoft Outlook** est **désactivé**![.](../../media/scc-toggle-off.png) Les paramètres suivants sont disponibles sur la page **Soumissions de l’utilisateur** :

- **Boîte aux lettres de Microsoft et de mon organisation** : dans la zone qui s’affiche, entrez l’adresse e-mail d’une boîte aux lettres Exchange Online existante à utiliser comme boîte aux lettres de soumissions utilisateur. Les groupes de distribution ne sont pas autorisés.

- **Personnalisez l’expérience de votre organisation lors de la création de rapports de menaces potentielles dans la section de mise en quarantaine** :

  **Bouton de message de rapport de mise en quarantaine** : vérifiez que ce paramètre est **activé**![.](../../media/scc-toggle-on.png) pour permettre aux utilisateurs de signaler des messages à partir d’une mise en quarantaine. Sinon, **désactivez** ![ce paramètre désactivé](../../media/scc-toggle-off.png).

Lorsque vous avez terminé sur la page **Soumissions de l’utilisateur** , cliquez sur **Enregistrer**. Pour restaurer les paramètres à leurs valeurs immédiatement antérieures, cliquez sur **Restaurer**.

#### <a name="message-submission-format"></a>Format de soumission de message

Pour identifier correctement les messages joints d’origine, les messages envoyés à la boîte aux lettres personnalisée nécessitent une mise en forme spécifique. Si les messages n’utilisent pas ce format, les messages joints d’origine sont toujours identifiés comme hameçonnage.

Pour spécifier la raison pour laquelle les messages joints d’origine ont été signalés, les messages envoyés à la boîte aux lettres d’envoi de l’utilisateur doivent répondre aux critères suivants :

- La pièce jointe du message d’origine n’est pas modifiée.
- La ligne Objet (titre de l’enveloppe) des messages envoyés à la boîte aux lettres des soumissions utilisateur doit commencer par l’une des valeurs de préfixe suivantes :
  - `1|` ou `Junk:`.
  - `2|` ou `Not junk:`.
  - `3|` ou `Phishing:`.

  Par exemple :

  - `3|This text in the Subject line is ignored by the system`
  - `Not Junk:This text in the Subject line is also ignored by the system`

  Les messages qui ne suivent pas ce format ne s’affichent pas correctement sur la page **Soumissions** à l’adresse <https://security.microsoft.com/reportsubmission>.
