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
ms.openlocfilehash: c32d4ff27d44600ebe182f0764cb47c638a354c7
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051665"
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

  - **Microsoft** : la boîte aux lettres des soumissions utilisateur n’est pas utilisée (tous les messages signalés sont envoyés à Microsoft pour analyse).

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

## <a name="use-exchange-online-powershell-to-configure-the-user-submissions-mailbox-for-email"></a>Utiliser Exchange Online PowerShell pour configurer la boîte aux lettres des soumissions d’utilisateurs pour les e-mails

Après vous [être connecté à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), vous utilisez les **\*applets de commande -ReportSubmissionPolicy** et **\*-ReportSubmissionRule** pour gérer et configurer la boîte aux lettres des soumissions utilisateur et les paramètres associés.

Dans Exchange Online PowerShell, les éléments de base des paramètres de boîte aux lettres des soumissions utilisateur sont les suivants :

- **Stratégie de soumission de rapport** : active ou désactive l’expérience de création de rapports intégrée de Microsoft, active ou désactive l’envoi de messages signalés à Microsoft, active ou désactive l’envoi de messages signalés à la boîte aux lettres d’envoi des utilisateurs, et la plupart des autres paramètres.
- **Règle de soumission de rapport** : spécifie l’adresse e-mail de la boîte aux lettres des soumissions utilisateur ou une valeur vide lorsque la boîte aux lettres des soumissions utilisateur n’est pas utilisée (messages de rapport à Microsoft uniquement).

La différence entre ces deux éléments n’est pas évidente lorsque vous gérez les paramètres de boîte aux lettres des soumissions d’utilisateurs dans le portail Microsoft 365 Defender :

- Il existe uniquement une stratégie de soumission de rapport nommée DefaultReportSubmissionPolicy et une règle de soumission de rapport nommée DefaultReportSubmissionRule par défaut.

  Si vous ne l’avez jamais fait <https://security.microsoft.com/userSubmissionsReportMessage>, il n’existe aucune stratégie de soumission de rapport ou règle de soumission de rapport (les applets de commande Get-ReportSubmissionPolicy et Get-ReportSubmissionRule ne retournent rien).

  Dès que vous visitez <https://security.microsoft.com/userSubmissionsReportMessage> et avant même de configurer des paramètres, la stratégie de soumission de rapport est créée avec les valeurs par défaut et est visible dans PowerShell.

  Comme après avoir configuré et enregistré les paramètres pour <https://security.microsoft.com/userSubmissionsReportMessage> spécifier une boîte aux lettres d’envoi d’utilisateurs (expérience de création de rapports intégrée Microsoft ou outils tiers), la règle de soumission de rapport nommée DefaultReportSubmissionRule est automatiquement créée. Notez qu’il faut plusieurs secondes avant que la règle soit visible dans PowerShell.

- Vous pouvez supprimer la règle de soumission de rapport et la recréer avec un nom différent, mais la règle est toujours associée à la stratégie de soumission de rapport dont vous ne pouvez pas modifier le nom. Nous vous recommandons donc de nommer la règle DefaultReportSubmissionRule chaque fois que vous créez ou recréez la règle.

- Lorsque vous spécifiez l’adresse e-mail de la boîte aux lettres des soumissions d’utilisateurs dans le portail Microsoft 365 Defender, cette valeur est principalement définie dans la règle de soumission de rapport, mais la valeur est également copiée dans les propriétés associées dans la stratégie de soumission de rapport. Dans PowerShell, lorsque vous définissez l’adresse e-mail dans la règle, la valeur n’est pas copiée dans les propriétés associées de la stratégie. Pour assurer la cohérence avec le portail Microsoft 365 Defender et pour plus de clarté, nous vous recommandons d’ajouter ou de mettre à jour l’adresse e-mail dans la stratégie et la règle.

### <a name="use-powershell-to-view-the-report-submission-policy-and-the-report-submission-rule"></a>Utiliser PowerShell pour afficher la stratégie de soumission de rapport et la règle de soumission de rapport

Pour afficher la stratégie de soumission de rapport, exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Get-ReportSubmissionPolicy
```

Pour afficher la règle de soumission de rapport, exécutez la commande suivante :

```powershell
Get-ReportSubmissionRule
```

Pour afficher simultanément la stratégie et la règle, exécutez les commandes suivantes :

```powershell
Write-Output -InputObject `r`n,"Report Submission Policy","-------------------------------------------------------------------------------------"; Get-ReportSubmissionPolicy; Write-Output -InputObject `r`n,"Report Submission Rule","-------------------------------------------------------------------------------------"; Get-ReportSubmissionRule
```

N’oubliez pas que si vous n’avez jamais créé <https://security.microsoft.com/userSubmissionsReportMessage> ou créé manuellement la stratégie de soumission de rapport ou la règle de soumission de rapport dans PowerShell, il n’existe aucune stratégie de soumission de rapport ou règle de soumission de rapport. Par conséquent, les applets de commande **Get-ReportSubmissionPolicy** et **Get-ReportSubmissionRule** ne retournent rien.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-ReportSubmissionPolicy](/powershell/module/exchange/get-reportsubmissionpolicy) et [Get-ReportSubmissionRule](/powershell/module/exchange/get-reportsubmissionrule).

### <a name="use-powershell-to-create-the-report-submission-policy-and-the-report-submission-rule"></a>Utiliser PowerShell pour créer la stratégie de soumission de rapport et la règle de soumission de rapport

Si les applets de commande **Get-ReportSubmissionPolicy** et **Get-ReportSubmissionRule** ne retournent aucune sortie, vous pouvez créer la stratégie de soumission de rapport et la règle de soumission de rapport. Si vous essayez de les créer lorsqu’ils existent déjà, une erreur s’affiche.

Créez toujours la stratégie de soumission de rapport en premier, car vous spécifiez la stratégie de soumission de rapport dans la règle de soumission de rapport.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-ReportSubmissionPolicy](/powershell/module/exchange/new-reportsubmissionpolicy) et [New-ReportSubmissionRule](/powershell/module/exchange/new-reportsubmissionrule).

#### <a name="use-powershell-to-enable-the-microsoft-integrated-reporting-experience-with-report-to-microsoft-only"></a>Utiliser PowerShell pour activer l’expérience de création de rapports intégrée à Microsoft avec le rapport à Microsoft uniquement

Cet exemple crée la stratégie de soumission de rapport avec les paramètres par défaut (les mêmes paramètres que lors de la première visite <https://security.microsoft.com/userSubmissionsReportMessage>, mais avant de configurer ou d’enregistrer les paramètres) :

- L’expérience de création de rapports intégrée à Microsoft est activée : bouton Bascule du **bouton Message de rapport Microsoft Outlook** : **activé**![](../../media/scc-toggle-on.png).

- Envoyer les messages signalés à Microsoft uniquement : **envoyer les messages signalés à** \> **Microsoft**.

- Aucune boîte aux lettres d’envoi d’utilisateur n’est nécessaire ou spécifiée. La règle de soumission de rapport n’est donc pas créée.

```powershell
New-ReportSubmissionPolicy
```

#### <a name="use-powershell-for-the-microsoft-integrated-reporting-experience-with-report-to-microsoft-and-the-user-submissions-mailbox"></a>Utiliser PowerShell pour l’expérience de création de rapports intégrée à Microsoft avec le rapport à Microsoft et la boîte aux lettres d’envoi des utilisateurs

Cet exemple crée la stratégie de soumission de rapport et la règle de soumission de rapport avec les paramètres suivants :

- L’expérience de création de rapports intégrée à Microsoft est activée : bouton Bascule du **bouton Message de rapport Microsoft Outlook** : **activé**![](../../media/scc-toggle-on.png). Dans l’applet de commande **New-ReportSubmissionPolicy** , la valeur par défaut du paramètre _EnableReportToMicrosoft_ est `$true` et la valeur par défaut du paramètre _EnableThirdPartyAddress_ est `$false`, donc vous n’avez pas besoin de les utiliser.

- Envoyer des messages signalés à Microsoft et à la boîte aux lettres d’envoi des utilisateurs : **Envoyez les messages signalés à** Microsoft et à \> **la boîte aux lettres de mon organisation** :

  - **New-ReportSubmissionPolicy**: `-ReportJunkToCustomizedAddress $true -ReportJunkAddresses <emailaddress> -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses <emailaddress> -ReportPhishToCustomizedAddress $true -ReportPhishAddresses <emailaddress>`.
  - **Set-ReportSubmissionRule** : `SentTo <emailaddress>`.

  Dans cet exemple, l’adresse e-mail de la boîte aux lettres des soumissions utilisateur est reportedmessages@contoso.com dans Exchange Online (vous ne pouvez pas spécifier d’adresse e-mail externe).

  > [!NOTE]
  > Vous devez utiliser la même valeur d’adresse e-mail dans tous les paramètres qui identifient la boîte aux lettres des soumissions utilisateur.

Les paramètres restants sont nécessaires pour créer la stratégie de soumission de rapport. Dans cet exemple, les valeurs par défaut sont utilisées. Si vous ne spécifiez pas les valeurs par défaut comme décrit dans cet exemple, des paramètres et des paramètres supplémentaires peuvent être nécessaires :

- **Laissez les utilisateurs choisir s’ils souhaitent signaler** sélectionné (`-DisableUserSubmissionOptions $false`) et **qu’aucune option de création de rapports Select disponible pour les utilisateurs** n’est sélectionnée (la valeur `0` par défaut _du paramètre UserSubmissionOptions_ est utilisée).
- **Section Expérience de création de rapports utilisateur** :
  - Rien n’est entré dans les zones **titre** et **corps du message** dans les onglets **Before reporting** ou **After reporting** (`-EnableCustomizedMsg $false`).
  - **Affichage uniquement lorsque l’utilisateur signale l’hameçonnage** sélectionné (`-OnlyShowPhishingDisclaimer $true`).
- **Email notifications pour la section des résultats de la révision par l’administrateur** :
  - **Spécifiez Office 365 adresse e-mail à utiliser comme expéditeur** non sélectionné (`-EnableCustomNotificationSender $false`).
  - **Lien Personnaliser les notifications** \> Personnaliser l’onglet **Pied de** page du menu volant \> **de confirmation** : **Afficher le logo de l’entreprise** non sélectionné (`-EnableOrganizationBranding $false`).
- **Personnalisez l’expérience de votre organisation lors de la création de rapports de menaces potentielles dans la section de mise en quarantaine** :

  Bouton bascule du **message de rapport de mise en quarantaine** : **activé**![.](../../media/scc-toggle-on.png) (`-DisableQuarantineReportingOption $false`).

```powershell
$usersub = "reportedmessages@contoso.com"

New-ReportSubmissionPolicy -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub -DisableUserSubmissionOptions $false -EnableCustomizedMsg $false -OnlyShowPhishingDisclaimer $true -EnableCustomNotificationSender $false -EnableOrganizationBranding $false -DisableQuarantineReportingOption $false

New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
```

#### <a name="use-powershell-for-the-microsoft-integrated-reporting-experience-with-report-to-the-user-submissions-mailbox-only"></a>Utiliser PowerShell pour l’expérience de création de rapports intégrée à Microsoft avec le rapport à la boîte aux lettres des soumissions d’utilisateurs uniquement

Cet exemple crée la stratégie de soumission de rapport et la règle de soumission de rapport avec les paramètres suivants :

- L’expérience de création de rapports intégrée à Microsoft est activée : bouton Bascule du **bouton Message de rapport Microsoft Outlook** : **activé**![](../../media/scc-toggle-on.png). Sur l’applet **de commande New-ReportSubmissionPolicy** : `-EnableReportToMicrosoft $false`. La valeur par défaut du paramètre _EnableThirdPartyAddress_ est `$false`, vous n’avez donc pas besoin de l’utiliser.

- Envoyer les messages signalés à la boîte aux lettres d’envoi des utilisateurs uniquement : **Envoyer les messages signalés à la** **boîte aux**\> lettres Mes organisations :

  - **New-ReportSubmissionPolicy**: `-ReportJunkToCustomizedAddress $true -ReportJunkAddresses <emailaddress> -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses <emailaddress> -ReportPhishToCustomizedAddress $true -ReportPhishAddresses <emailaddress>`.
  - **Set-ReportSubmissionRule** : `SentTo <emailaddress>`.

  Dans cet exemple, l’adresse e-mail de la boîte aux lettres des soumissions utilisateur est userreportedmessages@fabrikam.com dans Exchange Online (vous ne pouvez pas spécifier d’adresse e-mail externe).

  > [!NOTE]
  > Vous devez utiliser la même valeur d’adresse e-mail dans tous les paramètres qui identifient la boîte aux lettres des soumissions utilisateur.

Comme dans l’exemple précédent, les mêmes paramètres restants sont nécessaires pour créer la stratégie de soumission de rapport. Comme dans l’exemple précédent, les valeurs par défaut de ces paramètres sont également utilisées :

```powershell
$usersub = "userreportedmessages@fabrikam.com"

New-ReportSubmissionPolicy -EnableReportToMicrosoft $false -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub -DisableUserSubmissionOptions $false -EnableCustomizedMsg $false -OnlyShowPhishingDisclaimer $true -EnableCustomNotificationSender $false -EnableOrganizationBranding $false -DisableQuarantineReportingOption $false

New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
```

#### <a name="use-powershell-for-third-party-reporting-tools"></a>Utiliser PowerShell pour les outils de création de rapports tiers

Cet exemple crée la stratégie de soumission de rapport et la règle de soumission de rapport avec les paramètres suivants :

- L’expérience de création de rapports intégrée à Microsoft est désactivée : **bouton Bouton Message de rapport Microsoft Outlook** désactivé  ![](../../media/scc-toggle-off.png). Sur l’applet **de commande New-ReportSubmissionPolicy** : `-EnableReportToMicrosoft $false -EnableThirdPartyAddress $true`.

- Utilisez les paramètres suivants pour spécifier l’adresse e-mail de la boîte aux lettres des soumissions utilisateur :

  - **New-ReportSubmissionPolicy** : `-ThirdPartyReportAddresses <emailaddress>`
  - **Set-ReportSubmissionRule** : `SentTo <emailaddress>`.

  Dans cet exemple, l’adresse e-mail de la boîte aux lettres des soumissions utilisateur est thirdpartyreporting@wingtiptoys.com dans Exchange Online (vous ne pouvez pas spécifier d’adresse e-mail externe

  > [!NOTE]
  > Vous devez utiliser la même valeur d’adresse e-mail dans tous les paramètres qui identifient la boîte aux lettres des soumissions utilisateur.

Les paramètres restants sont nécessaires pour créer la stratégie de soumission de rapport avec succès. Dans cet exemple, les valeurs par défaut sont utilisées. Aucune autre option n’est disponible dans la stratégie de soumission de rapport lorsque vous désactivez l’expérience de création de rapports intégrée à Microsoft :

- **Personnalisez l’expérience de votre organisation lors de la création de rapports de menaces potentielles dans la section de mise en quarantaine** :

  Bouton bascule du **message de rapport de mise en quarantaine** : **activé**![.](../../media/scc-toggle-on.png) (`-DisableQuarantineReportingOption $false`).

```powershell
$usersub = "thirdpartyreporting@wingtiptoys.com"

New-ReportSubmissionPolicy -EnableReportToMicrosoft $false -EnableThirdPartyAddress $true -ThirdPartyReportAddresses $usersub -DisableQuarantineReportingOption $false

New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
```

### <a name="use-powershell-to-modify-the-report-submission-policy-and-the-report-submission-rule"></a>Utiliser PowerShell pour modifier la stratégie de soumission de rapport et la règle de soumission de rapport

Les mêmes paramètres sont disponibles lorsque vous modifiez la stratégie de soumission de rapport dans PowerShell que lorsque vous avez créé la stratégie, comme décrit dans [la section précédente](#use-powershell-to-create-the-report-submission-policy-and-the-report-submission-rule). La principale différence est que les paramètres supplémentaires requis pour créer la stratégie (par exemple, _DisableQuarantineReportingOption_) ne sont pas obligatoires depuis longtemps. Toutefois, vous devrez peut-être annuler ou annuler certains paramètres importants que vous avez précédemment configurés ou que vous n’avez pas configurés. De plus, vous devrez peut-être créer ou supprimer la règle de soumission de rapport pour autoriser ou empêcher la création de rapports à une boîte aux lettres d’envoi d’utilisateurs.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-ReportSubmissionPolicy](/powershell/module/exchange/set-reportsubmissionpolicy).

Les exemples suivants montrent comment modifier l’expérience de création de rapports utilisateur sans se soucier des paramètres ou des valeurs existants :

- Passez au **rapport d’expérience \> de création de rapports intégré Microsoft à Microsoft uniquement** :

  ```powershell
   Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $true -EnableThirdPartyAddress $false -ThirdPartyReportAddresses $null -ReportJunkToCustomizedAddress $false -ReportJunkAddresses $null -ReportNotJunkToCustomizedAddress $false -ReportNotJunkAddresses $null -ReportPhishToCustomizedAddress $false -ReportPhishAddresses $null

  Get-ReportSubmissionRule | Remove-ReportSubmissionRule
  ```

- Passez au **rapport d’expérience \> de création de rapports intégré Microsoft à Microsoft et à la boîte aux lettres des soumissions d’utilisateurs** (par exemple, reportedmessages@contoso.com) :

  ```powershell
  $usersub = "reportedmessages@contoso.com"

  Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $true -EnableThirdPartyAddress $false -ThirdPartyReportAddresses $null -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub
  ```

  La commande suivante n’est requise que si vous n’avez pas encore la règle de soumission de rapport :

  ```powershell
  New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
  ```

- Remplacez le **rapport d’expérience \> de création de rapports intégré Microsoft par la boîte aux lettres des soumissions d’utilisateurs uniquement** (par exemple, userreportedmessages@fabrikam.com) :

  ```powershell
  $usersub = "userreportedmessages@fabrikam.com"

  Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $false -EnableThirdPartyAddress $false -ThirdPartyReportAddresses $null -ReportJunkToCustomizedAddress $true -ReportJunkAddresses $usersub -ReportNotJunkToCustomizedAddress $true -ReportNotJunkAddresses $usersub -ReportPhishToCustomizedAddress $true -ReportPhishAddresses $usersub
  ```

  La commande suivante n’est requise que si vous n’avez pas encore la règle de soumission de rapport :

  ```powershell
  New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
  ```

- Passez aux **outils de création de rapports tiers** (par exemple, thirdpartyreporting@wingtiptoys.com) :

  ```powershell
  $usersub = "thirdpartyreporting@wingtiptoys.com"

  Set-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy -EnableReportToMicrosoft $false -EnableThirdPartyAddress $true -ThirdPartyReportAddresses $usersub -ReportJunkToCustomizedAddress $false -ReportJunkAddresses $null -ReportNotJunkToCustomizedAddress $false -ReportNotJunkAddresses $null -ReportPhishToCustomizedAddress $false -ReportPhishAddresses $null
  ```

  La commande suivante n’est requise que si vous n’avez pas encore la règle de soumission de rapport :

  ```powershell
  New-ReportSubmissionRule -Name DefaultReportSubmissionRule -ReportSubmissionPolicy DefaultReportSubmissionPolicy -SentTo $usersub
  ```

Le seul paramètre explicite que vous pouvez modifier dans la règle de soumission de rapport est l’adresse e-mail de la boîte aux lettres des soumissions utilisateur (valeur du paramètre _SentTo_ ). Par exemple :

```powershell
Get-ReportSubmissionRule | Set-ReportSubmissionRule -SentTo newemailaddress@contoso.com
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-ReportSubmissionRule](/powershell/module/exchange/set-reportsubmissionrule).

Pour désactiver temporairement l’envoi de messages électroniques à la boîte aux lettres d’envoi des utilisateurs (expérience de création de rapports intégrée Microsoft ou outils tiers) sans supprimer la règle de soumission de rapport, utilisez [Disable-ReportSubmissionRule](/powershell/module/exchange/disable-reportsubmissionrule). Par exemple :

```powershell
Get-ReportSubmissionRule | Disable-ReportSubmissionRule -Confirm:$false
```

Pour réactiver la règle de soumission de rapport, utilisez [Enable-ReportSubmissionRule](/powershell/module/exchange/enable-reportsubmissionrule). Par exemple :

```powershell
Get-ReportSubmissionRule | Disable-ReportSubmissionRule -Confirm:$false
```

### <a name="use-powershell-to-remove-the-report-submission-policy-and-the-report-submission-rule"></a>Utiliser PowerShell pour supprimer la stratégie de soumission de rapport et la règle de soumission de rapport

Pour recommencer avec les paramètres par défaut de la stratégie de soumission de rapport, vous pouvez la supprimer et la recréer. La suppression de la stratégie de soumission de rapport ne supprime pas la règle de soumission de rapport, et inversement.

Pour supprimer la stratégie de soumission de rapport, exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Remove-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy
```

Pour supprimer la règle de soumission de rapport, exécutez la commande suivante :

```powershell
Get-ReportSubmissionRule | Remove-ReportSubmissionRule
```

Pour supprimer la stratégie de soumission de rapport et la règle de soumission de rapport dans la même commande sans invite, exécutez la commande suivante :

```powershell
Remove-ReportSubmissionPolicy -Identity DefaultReportSubmissionPolicy; Get-ReportSubmissionRule | Remove-ReportSubmissionRule -Confirm:$false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Remove-ReportSubmissionPolicy](/powershell/module/exchange/remove-reportsubmissionpolicy) et [Remove-ReportSubmissionRule](/powershell/module/exchange/remove-reportsubmissionrule).
