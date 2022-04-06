---
title: Essayez Microsoft Defender pour Office 365
description: ''
keywords: ''
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: article
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
ms.custom: ''
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: bda7d0cc95132f1f421fc49e5fc6e7453267c4b0
ms.sourcegitcommit: bcbcbd4ddc72ad2fed629619d23fac5827d072bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/29/2022
ms.locfileid: "64507263"
---
# <a name="try-microsoft-defender-for-office-365"></a>Essayez Microsoft Defender pour Office 365

> [!NOTE]
> La fonctionnalité décrite dans cet article est en prévisualisation, n’est pas disponible dans toutes les organisations et peut faire l’objet de changements.

Le portail **d’essai** unifié du portail Microsoft 365 Defender fournit un point d’entrée unique pour les expériences Évaluation et Évaluation distinctes pour Microsoft Defender pour Office 365. L’objectif est de vous permettre d’essayer les fonctionnalités de Defender pour Office 365 Plan 2 pendant 30 jours avant de vous y engager pleinement. Toutefois, il existe des différences dans les expériences d’évaluation en fonction de la nature de Microsoft 365 organisation :

- Vous avez déjà Microsoft 365 boîtes aux lettres, mais vous utilisez actuellement un service ou un appareil tiers pour la protection de la messagerie. Les messages provenant d’Internet circulent via le service de protection avant d’être envoyés à Microsoft 365 organisation. Microsoft 365 protection contre les programmes malveillants est aussi faible que possible (elle n’est jamais complètement éteinte ; par exemple, la protection contre les programmes malveillants est toujours appliquée).

  ![Le courrier circule à partir d’Internet via le service ou l’appareil de protection tiers avant d’être Microsoft 365.](../../media/mdo-migration-before.png)

  Dans ces environnements, vous pouvez uniquement essayer Defender pour Office 365 *en mode audit*. Vous n’avez pas besoin de modifier votre flux de messagerie (enregistrements MX) pour essayer Defender pour Office 365.

- Vous avez déjà une Microsoft 365 organisation. Les messages provenant d’Internet Microsoft 365 directement, mais votre abonnement actuel Exchange Online Protection [(EOP)](exchange-online-protection-overview.md) [ou Defender pour Office 365 Plan 1](overview.md#microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

  ![Les messages circulent d’Internet vers Microsoft 365, avec une protection contre EOP et/ou Defender pour Office 365 Plan 1.](../../media/mdo-trial-mail-flow.png)

  Dans ces environnements, vous pouvez essayer Defender pour Office 365 en mode *audit* ou *en mode blocage*.

Vous êtes invité à démarrer votre version d’essai dans différents emplacements Defender pour Office 365 fonctionnalités dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>. The centralized location to start your trial is on the **Trials** page at <https://security.microsoft.com/atpEvaluation>.

Le reste de cet article explique la différence entre le mode blocage du mode audit, la configuration des évaluations et d’autres détails.

## <a name="overview-of-defender-for-office-365"></a>Vue d’ensemble Defender pour Office 365

Defender pour Office 365 aide les organisations à sécuriser leur entreprise en offrant une gamme complète de fonctionnalités. Pour plus d’informations, [voir Microsoft Defender pour Office 365](defender-for-office-365.md).

Vous pouvez également en savoir plus sur Defender pour Office 365 ce [guide interactif](https://aka.ms/MS365D.InteractiveGuide).

![Microsoft Defender pour Office 365 diagramme conceptuel.](../../media/microsoft-defender-for-office-365.png)

## <a name="policies-in-blocking-mode-or-audit-mode"></a>Stratégies en mode blocage ou en mode audit

Lorsque vous évaluez Defender pour Office 365, les stratégies qui contrôlent les fonctionnalités de protection Microsoft 365 sont présentes :

- **Exchange Online Protection (EOP)** : aucune stratégie nouvelle ou spéciale n’est créée. Les stratégies EOP existantes peuvent agir sur des messages (par exemple, envoyer des messages vers le dossier Courrier indésirable ou en quarantaine) :

  - [Stratégies anti-programme malveillant](anti-malware-protection.md)
  - [Protection contre le courrier indésirable entrant](anti-spam-protection.md)
  - [Protection anti-usurpation dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings)

  Les stratégies par défaut de ces fonctionnalités sont toujours en cours, s’appliquent à tous les destinataires et sont toujours appliquées en dernier (après les stratégies personnalisées).

- **Defender pour Office 365** : les stratégies qui sont exclusives aux Defender pour Office 365 sont créées pour votre évaluation des Defender pour Office 365 :

  - [Protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
  - [Coffre pièces jointes pour les messages électroniques](safe-attachments.md)
  - [Coffre liens pour les messages électroniques et les Microsoft Teams](safe-links.md)

  Toutefois, la nature de ces stratégies est différente en mode de blocage et en mode audit :

  - **Mode audit :** des stratégies normales sont créées, mais les stratégies sont configurées uniquement pour *détecter les menaces* . Defender pour Office 365 détecte les messages dangereux pour la signalement, mais les messages ne sont pas mis en quarantaine (par exemple, les messages détectés ne sont pas mis en quarantaine).

  - **Mode de blocage** : les stratégies sont créées à l’aide du modèle Standard pour [les stratégies de sécurité prédéfinës](preset-security-policies.md). Defender pour Office 365 détecte et *prend des mesures sur* les messages dangereux (par exemple, les messages *détectés* sont mis en quarantaine).

  La sélection par défaut et recommandée consiste à étenduer ces stratégies Defender pour Office 365 à tous les utilisateurs de l’organisation. Toutefois, pendant ou après l’installation, vous pouvez modifier l’attribution de stratégie pour des utilisateurs, des groupes ou des domaines de messagerie spécifiques.

**Remarques** :

- Coffre liens désaxiquent les URL dans le flux de messagerie. Pour empêcher le détonation d’URL spécifiques, utilisez la liste d’adresses client autoriser/bloquer. Pour plus d’informations, [voir Manage the Tenant Allow/Block List](tenant-allow-block-list.md).
- Coffre liens ne encapsule pas les liens d’URL dans les corps des messages électroniques.
- Les paramètres de stratégie d’évaluation sont décrits dans la section [Paramètres de stratégie d’évaluation](#evaluation-policy-settings) plus loin dans cet article.

## <a name="set-up-an-evaluation-in-audit-mode"></a>Configurer une évaluation en mode audit

1. Cliquez sur **Démarrer l’évaluation**.

2. Dans la **boîte de dialogue Activer la protection** , **sélectionnez Non, je souhaite uniquement** signaler, puis cliquez sur **Continuer**.

3. Dans la **boîte de dialogue Sélectionner les utilisateurs à inclure** , configurez les paramètres suivants :

   - **Tous les utilisateurs** : il s’agit de l’option par défaut et recommandée.
   - **Sélectionnez des** utilisateurs : si vous sélectionnez cette option, vous devez sélectionner à qui s’applique l’évaluation :
     - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés dans votre organisation.
     - **Groupes** : groupes de distribution, groupes de sécurité à extension messagerie ou groupes Microsoft 365 spécifiés dans votre organisation.
     - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

     Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

     Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   > [!NOTE]
   > Vous pouvez modifier ces sélections une fois que vous avez terminé la configuration de l’évaluation.

   Lorsque vous avez terminé, cliquez sur **Continuer**.

4. Dans la **boîte de dialogue Aide-nous à comprendre votre flux de messagerie** , configurez les options suivantes :

   - **Partager des données avec Microsoft** : cette option est sélectionnée par défaut, mais vous pouvez effacer la case à cocher si vous le souhaitez.

   - L’une des options suivantes est automatiquement sélectionnée en fonction de notre détection de l’enregistrement MX pour votre domaine :

     - **J’utilise un** fournisseur de services tiers et/ou local : l’enregistrement MX de votre domaine pointe ailleurs que Microsoft 365. Cette sélection nécessite les paramètres supplémentaires suivants après avoir cliqué sur **Suivant** :

       1. Dans la **boîte de dialogue Paramètres** tiers ou local, configurez les paramètres suivants :

          - **Sélectionnez un fournisseur de services tiers** : sélectionnez l’une des valeurs suivantes :
            - **Barracuda**
            - **IronPort**
            - **Mimecast**
            - **Proofpoint**
            - **Sophos**
            - **Symantec**
            - **Trend Micro**
            - **Other**

          - **Connecteur à appliquer à cette évaluation** : sélectionnez le connecteur utilisé pour le flux de messagerie dans Microsoft 365.

            [Le filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (également appelé ignorer la *liste*) est automatiquement configuré sur le connecteur que vous spécifiez.

            Lorsqu’un service ou un appareil tiers se trouve à partir de Microsoft 365, le filtrage amélioré pour les connecteurs identifie correctement la source des messages Internet et améliore considérablement la précision de la pile de filtrage Microsoft (en particulier l’intelligence contre l’usurpation d’informations[, ainsi](anti-spoofing-protection.md) que les fonctionnalités post-violation dans l’Explorateur de menaces et la réponse d’investigation automatisée [& (AIR)](automated-investigation-response-office.md)).[](threat-explorer.md)

          - **List each gateway IP address your messages pass through**: This setting is available only if you selected **Other** for **Select a third party service provider**. Entrez une liste séparée par des virgules des adresses IP utilisées par le service ou l’appareil de protection tiers pour envoyer des messages Microsoft 365.

          Lorsque vous avez terminé, cliquez sur **Suivant**.

       2. Dans la boîte de dialogue règles de flux de messagerie **Exchange**, déterminez si vous avez besoin d’une règle de flux de messagerie Exchange Online (également appelée règle de transport) qui ignore le filtrage du courrier indésirable pour les messages entrants provenant du service ou du périphérique de protection tiers.

          Il est probable que vous avez déjà une règle de flux de messagerie SCL=-1 dans Exchange Online qui permet à tous les messages entrants provenant du service de protection de contourner (la plupart) le filtrage Microsoft 365 courrier indésirable. De nombreux services de protection encouragent cette méthode de règle de flux de courrier indésirable (SCL) pour Microsoft 365 clients qui utilisent leurs services.

          Comme expliqué à l’étape précédente, le filtrage amélioré des connecteurs est automatiquement configuré sur le connecteur que vous spécifiez comme source de courrier à partir du service de protection.

          L’utilisation du filtrage amélioré pour les connecteurs sans règle SCL=-1 pour le courrier entrant provenant du service de protection améliorera considérablement les fonctionnalités de détection des fonctionnalités de protection EOP telles que l’usurpation d’informations [et pourrait](anti-spoofing-protection.md) avoir un impact sur la remise de ces messages nouvellement détectés (par exemple, déplacement vers le dossier Courrier indésirable ou mise en quarantaine). Cet impact est limité aux stratégies EOP ; comme indiqué précédemment, les stratégies Defender pour Office 365 sont créées en mode audit.

          Pour créer une règle de flux de messagerie SCL=-1 ou pour passer en revue vos règles existantes, cliquez sur le bouton Exchange centre d’administration sur la page. Pour plus d’informations, voir Utiliser des règles de flux de messagerie pour définir le niveau de confiance du courrier indésirable [(SCL) dans les messages Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

          Lorsque vous avez terminé, cliquez sur **Terminer**.

     - **J’utilise uniquement Microsoft Exchange Online** : les enregistrements MX de votre domaine pointent vers Microsoft 365. Il ne reste rien à configurer, donc cliquez sur **Terminer**.

5. Une boîte de dialogue de progression s’affiche lorsque votre évaluation est définie. Lorsque la mise en place est terminée, cliquez sur **Terminé**.

## <a name="set-up-an-evaluation-in-blocking-mode"></a>Configurer une évaluation en mode blocage

1. Cliquez sur **Démarrer l’évaluation**.

2. Dans la **boîte de dialogue Activer la protection** , sélectionnez **Oui, protégez mon** organisation en bloquant les menaces, puis cliquez sur **Continuer**.

3. Dans la **boîte de dialogue Sélectionner les utilisateurs à inclure** , configurez les paramètres suivants :

   - **Tous les utilisateurs** : il s’agit de l’option par défaut et recommandée.
   - **Sélectionnez des** utilisateurs : si vous sélectionnez cette option, vous devez sélectionner à qui s’applique l’évaluation :
     - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés dans votre organisation.
     - **Groupes** : groupes de distribution, groupes de sécurité à extension messagerie ou groupes Microsoft 365 spécifiés dans votre organisation.
     - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

     Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

     Pour les utilisateurs ou les groupes, vous pouvez utiliser la plupart des identifiants (nom, nom d'affichage, alias, adresse e-mail, nom de compte, etc.), mais le nom d'affichage correspondant est affiché dans les résultats. Pour les utilisateurs, entrez un astérisque (\*) seul pour voir toutes les valeurs disponibles.

   > [!NOTE]
   > Vous pouvez modifier ces sélections une fois que vous avez terminé la configuration de l’évaluation.

   Lorsque vous avez terminé, cliquez sur **Continuer**.

4. Une boîte de dialogue de progression s’affiche lorsque votre évaluation est définie. Lorsque l’installation est terminée, cliquez sur **Terminé**.

## <a name="reporting-in-audit-mode"></a>Rapports en mode audit

- Le [rapport d’état de la protection contre](view-email-security-reports.md#threat-protection-status-report) les menaces affiche les détections par Defender pour Office 365 dans les affichages suivants :
  - [Afficher les données par programme malveillant et \> répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--malware-and-chart-breakdown-by-detection-technology)
  - [Afficher les données par courrier indésirable et \> répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--spam-and-chart-breakdown-by-detection-technology)
  - [Afficher les données par hameçonnage de messagerie électronique \> et répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--phish-and-chart-breakdown-by-detection-technology)

- Dans [l’Explorateur](threat-explorer.md) de menaces, les messages détectés par l’évaluation Defender pour Office 365 afficher la bannière suivante dans les détails de l’entrée :

  ![Bannière de notification dans les détails du message que l Defender pour Office 365 évaluation a détecté un message électronique malveillant.](../../media/evalv2-detection-banner.png)

<!--- This stuff is likely not applicable for V2 reporting --->

La **page Microsoft Defender pour Office 365 d’évaluation** <https://security.microsoft.com/atpEvaluation> suivante consolide les rapports pour les stratégies de l’évaluation :

- Protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage
- Liens sûrs
- Pièces jointes fiables

Par défaut, les graphiques montrent les données des 30 derniers jours, mais vous pouvez filtrer la plage de dates en cliquant sur l’icône ![Calendrier.](../../media/m365-cc-sc-add-internal-icon.png) **30 jours et** sélection parmi les valeurs supplémentaires suivantes inférieures à 30 jours :

- 24 heures
- 7 jours
- 14 jours
- Plage de dates personnalisée

Vous pouvez cliquer sur Télécharger ![l’icône.](../../media/m365-cc-sc-download-icon.png) **Téléchargez-le** pour télécharger les données du graphique dans un .csv de données.

## <a name="required-permissions"></a>Autorisations requises

Les autorisations requises dans **Azure AD** pour configurer une évaluation de Defender pour Microsoft 365 sont décrites dans la liste suivante :

- **Créer, modifier ou supprimer une évaluation** : administrateur de sécurité ou administrateur général.
- **Afficher les stratégies d’évaluation et les rapports** : administrateur de sécurité ou lecteur sécurité.

Pour plus d’informations sur Azure AD autorisations d’accès dans le portail Microsoft 365 Defender, voir Azure AD [rôles dans le portail Microsoft 365 Defender web](permissions-microsoft-365-security-center.md#azure-ad-roles-in-the-microsoft-365-defender-portal)

## <a name="evaluation-policy-settings"></a>Paramètres de stratégie d’évaluation

Les paramètres du Defender pour Office 365 spécifiquement créés pour l’évaluation sont décrits dans les tableaux suivants :

**Paramètres de stratégie d’évaluation anti-hameçonnage** :

|Paramètre|Valeur|
|---|---|
|AdminDisplayName|Stratégie d’évaluation|
|AuthenticationFailAction|MoveToJmf|
|Activé|True|
|EnableFirstContactSafetyTips|False|
|EnableMailboxIntelligence|Vrai|
|EnableMailboxIntelligenceProtection|Vrai|
|EnableOrganizationDomainsProtection|False|
|EnableSimilarDomainsSafetyTips|False|
|EnableSimilarUsersSafetyTips|False|
|EnableSpoofIntelligence|True|
|EnableSuspiciousSafetyTip|False|
|EnableTargetedDomainsProtection|False|
|EnableTargetedUserProtection|False|
|EnableUnauthenticatedSender|True|
|EnableUnusualCharactersSafetyTips|False|
|EnableViaTag|True|
|Guid|Valeur GUID|
|ImpersonationProtectionState|Manual|
|IsDefault|False|
|MailboxIntelligenceProtectionAction|NoAction|
|MailboxIntelligenceProtectionActionRecipients|{}|
|MailboxIntelligenceQuarantineTag|DefaultFullAccessPolicy|
|Nom|Stratégie d’évaluation|
|PhishThresholdLevel|1|
|RecommendedPolicyType|Évaluation|
|SpoofQuarantineTag|DefaultFullAccessPolicy|
|TargetedDomainActionRecipients|{}|
|TargetedDomainProtectionAction|NoAction|
|TargetedDomainQuarantineTag|DefaultFullAccessPolicy|
|TargetedUserActionRecipients|{}|
|TargetedUserProtectionAction|NoAction|
|TargetedUserQuarantineTag|DefaultFullAccessPolicy|
|||
|AntiPhishPolicyLevelDataList|blank|
|AntiSpoofEnforcementType|Importante|
|AuthenticationSafetyTipText|blank|
|AuthenticationSoftPassSafetyTipText|blank|
|EnableAuthenticationSafetyTip|False|
|EnableAuthenticationSoftPassSafetyTip|False|
|PolicyTag|blank|
|SimilarUsersSafetyTipsCustomText|blank|
|TreatSoftPassAsAuthenticated|True|
|UnusualCharactersSafetyTipsCustomText|blank|
|||
|ExcludedDomains|{}|
|ExcludedSenders|{}|
|TargetedDomainsToProtect|{}|
|TargetedUsersToProtect|{}|

**Coffre stratégie d’évaluation des pièces jointes** :

|Paramètre|Valeur|
|---|---|
|Action|Autoriser|
|ActionOnError|True|
|AdminDisplayName|Stratégie d’évaluation|
|ConfidenceLevelThreshold|80|
|Activer|True|
|EnableOrganizationBranding|False|
|Guid|Valeur GUID|
|IsBuiltInProtection|False|
|IsDefault|False|
|Nom|Stratégie d’évaluation|
|OperationMode|Delay|
|QuarantineTag|AdminOnlyAccessPolicy|
|RecommendedPolicyType|Évaluation|
|Rediriger|False|
|RedirectAddress|{}|
|ScanTimeout|30|

**Coffre de stratégie d’évaluation des liens :**

|Paramètre|Valeur|
|---|---|
|AdminDisplayName|Stratégie d’évaluation|
|AllowClickThrough|False|
|CustomNotificationText|blank|
|DeliverMessageAfterScan|Vrai|
|DisableUrlRewrite|Vrai|
|DoNotRewriteUrls|{}|
|EnableForInternalSenders|False|
|EnableOrganizationBranding|False|
|EnableSafeLinksForTeams|True|
|Guid|Valeur GUID|
|IsBuiltInProtection|False|
|IsDefault|False|
|IsEnabled|Vrai|
|LocalizedNotificationTextList|{}|
|Nom|« EvaluationPolicy »|
|RecommendedPolicyType|Évaluation|
|ScanUrls|True|
|TrackClicks|True|
|||
|DoNotAllowClickThrough|blank|
|DoNotTrackUserClicks|False|
|EnableSafeLinksForEmail|Vrai|
|EnableSafeLinksForOffice|True|
|ExcludedUrls|{}|
|WhiteListedUrls|blank|
