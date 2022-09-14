---
title: Afficher les rapports sur la sécurité des e-mails
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 3a137e28-1174-42d5-99af-f18868b43e86
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à rechercher et à utiliser les rapports de sécurité par e-mail disponibles dans le portail Microsoft 365 Defender.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 28f5a19abd0a2a1ddc0d2bab3863176d2470c980
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67672422"
---
# <a name="view-email-security-reports-in-the-microsoft-365-defender-portal"></a>Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Divers rapports sont disponibles dans le portail Microsoft 365 Defender pour vous aider à <https://security.microsoft.com> voir comment les fonctionnalités de sécurité des e-mails, telles que les fonctionnalités anti-courrier indésirable et anti-programme malveillant dans Microsoft 365, protègent votre organisation. Si vous disposez [des autorisations nécessaires](#what-permissions-are-needed-to-view-these-reports), vous pouvez afficher et télécharger ces rapports comme décrit dans cet article.

> [!NOTE]
>
> Certains rapports de la page **des rapports de collaboration Email &** nécessitent des Microsoft Defender pour Office 365. Pour plus d’informations sur ces rapports, consultez [Afficher les rapports Defender pour Office 365 dans le portail Microsoft 365 Defender](view-reports-for-mdo.md).
>
> Les rapports liés au flux de messagerie se trouvent désormais dans le Centre d’administration Exchange. Pour plus d’informations sur ces rapports, consultez [les rapports de flux de courrier dans le nouveau centre d’administration Exchange](/exchange/monitoring/mail-flow-reports/mail-flow-reports).

Regardez cette courte vidéo pour découvrir comment utiliser des rapports pour comprendre l’efficacité des Defender pour Office 365 dans votre organisation.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWBkxB]

## <a name="email-security-report-changes-in-the-microsoft-365-defender-portal"></a>Email modifications apportées au rapport de sécurité dans le portail Microsoft 365 Defender

Les rapports Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 du portail Microsoft 365 Defender qui ont été remplacés, déplacés ou dépréciés sont décrits dans le tableau suivant.

|Rapport et applets de commande dépréciés|Nouveau rapport et applets de commande|ID du Centre de messages|Date|
|---|---|:---:|:---:|
|**traçage d’URL** <br/><br/> Get-URLTrace|[Rapport sur la protection des URL](view-reports-for-mdo.md#url-protection-report) <br/><br/> [Get-SafeLinksAggregateReport](/powershell/module/exchange/get-safelinksaggregatereport) <br> [Get-SafeLinksDetailReport](/powershell/module/exchange/get-safelinksdetailreport)|MC239999|Juin 2021|
|**Rapport d’e-mail envoyé et reçu** <br/><br/> Get-MailTrafficReport <br> Get-MailDetailReport|[Rapport sur l’état de la protection contre les menaces](#threat-protection-status-report) <br> [Rapport d’état du flux de courrier](#mailflow-status-report) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport) <br> [Get-MailFlowStatusReport](/powershell/module/exchange/get-mailflowstatusreport)|MC236025|Juin 2021|
|**Rapport de transfert** <br/><br/> pas d’applets de commande|[Rapport de messages transférés automatiquement dans le CAE](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report) <br/><br/> pas d’applets de commande|MC250533|Juin 2021|
|**Rapport sur les types de fichiers pièces jointes fiables** <br/><br/> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Rapport d’état de la protection contre les menaces : afficher les données par Email \> malware](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250532|Juin 2021|
|**Rapport de destruction des messages pièces jointes fiables** <br/><br/> Get-AdvancedThreatProtectionTrafficReport <br> Get-MailDetailMalwareReport|[Rapport d’état de la protection contre les menaces : afficher les données par Email \> malware](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250531|Juin 2021|
|**Logiciels malveillants détectés dans le rapport d’e-mail** <br/><br/> Get-MailTrafficReport <br> Get-MailDetailMalwareReport|[Rapport d’état de la protection contre les menaces : afficher les données par Email \> malware](#view-data-by-email--malware-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250530|Juin 2021|
|**Rapport de détection du courrier indésirable** <br/><br/> Get-MailTrafficReport <br> Get-MailDetailSpamReport|[Rapport d’état de la protection contre les menaces : afficher les données par Email \> courrier indésirable](#view-data-by-email--spam-and-chart-breakdown-by-detection-technology) <br/><br/> [Get-MailTrafficATPReport](/powershell/module/exchange/get-mailtrafficatpreport) <br> [Get-MailDetailATPReport](/powershell/module/exchange/get-maildetailatpreport)|MC250529|Octobre 2021|
|Get-AdvancedThreatProtectionDocumentReport <br/><br/> Get-AdvancedThreatProtectionDocumentDetail|[Get-ContentMalwareMdoAggregateReport](/powershell/module/exchange/get-contentmalwaremdoaggregatereport) <br/><br/> [Get-ContentMalwareMdoDetailReport](/powershell/module/exchange/get-contentmalwaremdodetailreport)|MC343433|Mai 2022|
|**Rapport de règle de transport Exchange** <br/><br/> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|[Rapport de règle de transport Exchange dans le CENTRE](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report) <br/><br/> [Get-MailTrafficPolicyReport](/powershell/module/exchange/get-mailtrafficpolicyreport) <br> [Get-MailDetailTransportRuleReport](/powershell/module/exchange/get-maildetailtransportrulereport)|MC316157|Avril 2022|
|Get-MailTrafficTopReport|[Rapport des principaux expéditeurs et destinataires](view-email-security-reports.md#top-senders-and-recipients-report) <br/><br/> [Get-MailTrafficSummaryReport](/powershell/module/exchange/get-mailtrafficsummaryreport) <br/><br/> **Remarque** : Les fonctionnalités de création de rapports de chiffrement ne sont pas remplacées dans Get-MailTrafficTopReport.|MC315742|Avril 2022|

## <a name="compromised-users-report"></a>Rapport sur les utilisateurs compromis

> [!NOTE]
> Ce rapport est disponible dans les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online. Il n’est pas disponible dans les organisations de Exchange Online Protection (EOP) autonomes.

Le rapport **Utilisateurs compromis** indique le nombre de comptes d’utilisateurs marqués comme **suspects** ou **restreints** au cours des 7 derniers jours. Les comptes dans l’un de ces états sont problématiques, voire compromis. Avec une utilisation fréquente, vous pouvez utiliser le rapport pour repérer les pics, voire les tendances, dans des comptes suspects ou restreints. Pour plus d’informations sur les utilisateurs compromis, consultez [Répondre à un compte de messagerie compromis](responding-to-a-compromised-email-account.md).

:::image type="content" source="../../media/compromised-users-report-widget.png" alt-text="Widget Utilisateurs compromis sur la page des rapports de collaboration Email &" lightbox="../../media/compromised-users-report-widget.png":::

La vue d’agrégation affiche les données des 90 derniers jours et la vue détaillée affiche les données des 30 derniers jours.

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, **recherchez les utilisateurs compromis**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/CompromisedUsers>.

Dans la page **Utilisateurs compromis** , le graphique affiche les informations suivantes pour la plage de dates spécifiée :

- **Restreint** : le compte d’utilisateur n’a pas pu envoyer de courrier électronique en raison de modèles hautement suspects.
- **Suspect** : le compte d’utilisateur a envoyé des e-mails suspects et risque d’être limité à l’envoi d’e-mails.

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Heure de création**
- **ID d'utilisateur**
- **Action**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** : **date de début** et **date de fin**.
- **Activité** : **restreinte** ou **suspecte**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **Utilisateurs compromis** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

:::image type="content" source="../../media/compromised-users-report-activity-view.png" alt-text="Vue Rapport dans le rapport Utilisateurs compromis" lightbox="../../media/compromised-users-report-activity-view.png":::

## <a name="exchange-transport-rule-report"></a>Rapport de règle de transport Exchange

Le rapport sur les **règles de transport Exchange** montre l’effet des règles de flux de courrier (également appelées règles de transport) sur les messages entrants et sortants de votre organisation.

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, recherchez **la règle de transport Exchange**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/ETRRuleReport>.

:::image type="content" source="../../media/transport-rule-report-widget.png" alt-text="Widget de règle de transport Exchange dans la page des rapports de collaboration Email &" lightbox="../../media/transport-rule-report-widget.png":::

Dans la page du **rapport de règle de transport Exchange** , les graphiques et les données disponibles sont décrits dans les sections suivantes.
> [!NOTE]
> Le **rapport de règle de transport Exchange** est désormais disponible dans le CENTRE. Pour plus d’informations, consultez [le rapport sur les règles de transport Exchange dans le nouveau CENTRE](/exchange/monitoring/mail-flow-reports/mfr-exchange-transport-rule-report).

### <a name="chart-breakdown-by-direction"></a>Répartition du graphique par direction

:::image type="content" source="../../media/transport-rule-report-etr-direction-view.png" alt-text="Vue Direction des règles de transport Exchange dans le rapport de règle de transport Exchange" lightbox="../../media/transport-rule-report-etr-direction-view.png":::

Si vous sélectionnez **La répartition du graphique par direction**, les graphiques suivants sont disponibles :

- **Afficher les données selon les règles de transport Exchange** : nombre de messages **entrants** et **sortants** qui ont été affectés par les règles de flux de courrier.
- **Afficher les données en fonction des règles de transport Exchange DLP** : nombre de messages **entrants** et **sortants** affectés par les règles de flux de courrier de protection contre la perte de données (DLP).

Les informations suivantes sont affichées dans le tableau de détails sous le graphique :

- **Date**
- **Stratégie DLP** (**afficher les données par règles de transport Exchange DLP** uniquement)
- **Règle de transport**
- **Sujet**
- **Adresse de l’expéditeur**
- **Adresse du destinataire**
- **Gravité**
- **Direction**

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** **date de début** et **date de fin**.
- **Direction** : **sortant et** **entrant**.
- **Gravité** : **gravité élevée**, **gravité moyenne** et **gravité faible**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **du rapport de règle de transport Exchange** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="chart-breakdown-by-severity"></a>Répartition du graphique par gravité

:::image type="content" source="../../media/transport-rule-report-etr-severity-view.png" alt-text="Vue Gravité des règles de transport Exchange dans le rapport de règle de transport Exchange" lightbox="../../media/transport-rule-report-etr-severity-view.png":::

Si vous sélectionnez **La répartition du graphique par gravité**, les graphiques suivants sont disponibles :

- **Afficher les données selon les règles de transport Exchange** : nombre de messages de **gravité élevée**, **de gravité moyenne** et **de gravité faible** . Vous définissez le niveau de gravité en tant qu’action dans la règle (**auditez cette règle avec le niveau de gravité** ou _SetAuditSeverity_). Pour plus d’informations, consultez [les actions de règle de flux de courrier dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rule-actions).

- **Afficher les données selon les règles de transport DLP Exchange** : nombre de messages de **gravité élevée**, **de gravité moyenne** et **de gravité faible** qui ont été affectés par les règles de flux de messagerie DLP.

Les informations suivantes sont affichées dans le tableau de détails sous le graphique :

- **Date**
- **Stratégie DLP** (**afficher les données par règles de transport Exchange DLP** uniquement)
- **Règle de transport**
- **Sujet**
- **Adresse de l’expéditeur**
- **Adresse du destinataire**
- **Gravité**
- **Direction**

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** **Date de début** et **date de fin**
- **Direction** : **trafic sortant** et **entrant**
- **Gravité** : **gravité élevée**, **gravité moyenne** et **gravité faible**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **du rapport de règle de transport Exchange** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

## <a name="forwarding-report"></a>Rapport de transfert

> [!NOTE]
> Ce rapport est maintenant disponible dans le CAE. Pour plus d’informations, consultez le [rapport des messages transférés automatiquement dans le nouveau CENTRE](/exchange/monitoring/mail-flow-reports/mfr-auto-forwarded-messages-report).

## <a name="mailflow-status-report"></a>Rapport d’état du flux de courrier

Le **rapport d’état du flux** de courrier est un rapport intelligent qui affiche des informations sur les e-mails entrants et sortants, les détections de courrier indésirable, les programmes malveillants, les e-mails identifiés comme « bons » et les informations sur les e-mails autorisés ou bloqués en périphérie. Il s’agit du seul rapport qui contient des informations de protection de périphérie et indique la quantité de courriers électroniques bloqués avant d’être autorisés dans le service pour évaluation par Exchange Online Protection (EOP). Il est important de comprendre que si un message est envoyé à cinq destinataires, nous le comptabilisons comme cinq messages différents et non comme un seul message.

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, recherchez le **résumé de l’état du flux** de courrier, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/mailflowStatusReport>.

:::image type="content" source="../../media/mail-flow-status-report-widget.png" alt-text="Widget récapitulatif de l’état du flux de courrier dans la page Email & rapports de collaboration" lightbox="../../media/mail-flow-status-report-widget.png":::

### <a name="type-view-for-the-mailflow-status-report"></a>Affichage de type pour le rapport d’état mailflow

:::image type="content" source="../../media/mail-flow-status-report-type-view.png" alt-text="Vue Type dans le rapport d’état mailflow" lightbox="../../media/mail-flow-status-report-type-view.png":::

Dans la page **rapport d’état du flux** de courrier, l’onglet **Type** est sélectionné par défaut. Le graphique affiche les informations suivantes pour la plage de dates spécifiée :

- **Bon courrier** : Email qui n’est pas un courrier indésirable ou qui sont autorisés par les stratégies utilisateur ou organisationnelle.
- **Total**
- **Programmes malveillants** : Email bloqués en tant que programmes malveillants par différents filtres.
- **E-mail de hameçonnage** : Email bloqué en tant que hameçonnage par différents filtres.
- **Courrier indésirable** : Email bloqué en tant que courrier indésirable par différents filtres.
- **Protection edge** : Email qui est rejetée au niveau du périmètre/de la périphérie avant d’être évaluée par EOP ou Defender pour Office 365.
- **Messages de règle** : Email messages qui ont été pris en compte par des règles de flux de courrier (également appelées règles de transport).

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Direction**
- **Type (Type)**
- **24 heures**
- **3 jours**
- **7 jours**
- **15 jours**
- **30 jours**

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** : **date de début** et **date de fin**.
- **Direction du courrier** : **entrant et** **sortant**.
- **Type** :
  - **Bon courrier**
  - **Programme malveillant**
  - **Courrier indésirable**
  - **Protection edge**
  - **Messages de règle**
  - **Courriers hameçons**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

De retour sur la page rapport **d’état mailflow** , si vous cliquez sur **Choisir une catégorie pour plus d’informations**, vous pouvez sélectionner parmi les valeurs suivantes :

- **E-mail d’hameçonnage** : cette sélection vous dirige vers le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- **Programmes malveillants par e-mail** : cette sélection vous dirige vers le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- **Détections de courrier indésirable** : cette sélection vous dirige vers le [rapport Détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).
- **Courrier indésirable bloqué edge** : cette sélection vous dirige vers le [rapport Détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).

Dans la page **rapport d’état mailflow** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Icône Créer une planification](#schedule-report)** et ![exporter.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="direction-view-for-the-mailflow-status-report"></a>Vue Direction pour le rapport d’état mailflow

:::image type="content" source="../../media/mail-flow-status-report-direction-view.png" alt-text="Vue Direction dans le rapport d’état mailflow" lightbox="../../media/mail-flow-status-report-direction-view.png":::

Si vous cliquez sur l’onglet **Direction** , le graphique affiche les informations suivantes pour la plage de dates spécifiée :

- **Entrants**
- **Sortant**

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** : **date de début** et **date de fin**.
- **Direction du courrier** : **entrant et** **sortant**.
- **Type** :
  - **Bon courrier**
  - **Programme malveillant**
  - **Courrier indésirable**
  - **Protection edge**
  - **Messages de règle**
  - **Courriers hameçons**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

De retour sur la page rapport **d’état mailflow** , si vous cliquez sur **Choisir une catégorie pour plus d’informations**, vous pouvez sélectionner parmi les valeurs suivantes :

- **E-mail d’hameçonnage** : cette sélection vous dirige vers le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- **Programmes malveillants par e-mail** : cette sélection vous dirige vers le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report).
- **Détections de courrier indésirable** : cette sélection vous dirige vers le [rapport Détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).
- **Courrier indésirable bloqué edge** : cette sélection vous dirige vers le [rapport Détections de courrier indésirable](view-email-security-reports.md#spam-detections-report).

Dans la page **rapport d’état mailflow** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **Icône Créer une planification** et ![exporter.](../../media/m365-cc-sc-download-icon.png) Des boutons **d’exportation** sont disponibles.

### <a name="mailflow-view-for-the-mailflow-status-report"></a>Affichage du flux de courrier pour le rapport d’état du flux de courrier

La vue **Flux** de courrier vous montre comment les fonctionnalités de protection contre les menaces par e-mail de Microsoft filtrent les e-mails entrants et sortants dans votre organisation. Cette vue utilise un diagramme de flux horizontal (appelé diagramme _Sankey_ ) pour fournir des détails sur le nombre total de courriers électroniques et la façon dont les fonctionnalités de protection contre les menaces configurées, notamment la protection edge, les logiciels anti-programmes malveillants, l’anti-hameçonnage, la lutte contre le courrier indésirable et l’usurpation d’identité affectent ce nombre.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view.png" alt-text="Vue Mailflow dans le rapport d’état mailflow" lightbox="../../media/mail-flow-status-report-mailflow-view.png":::

La vue d’agrégation et la vue de table de détails autorisent 90 jours de filtrage.

Les informations contenues dans le diagramme sont codées en couleur par **EOP** ou **Defender pour Office 365** technologies.

Le diagramme est organisé en bandes horizontales suivantes :

- **Bande d’e-mail totale** : cette valeur est toujours affichée en premier.
- **Bloc edge** et bande **traitée** :
  - **Bloc edge** : messages filtrés à la périphérie et identifiés comme Edge Protection.
  - **Traité** : messages gérés par la pile de filtrage.
- Bande Résultats :
  - **Bloc de règles** : messages traités par des règles de flux de messagerie Exchange (règles de transport).
  - **Bloc de programmes malveillants** : messages identifiés comme programmes malveillants par différents filtres.<sup>\*</sup>
  - **Bloc phish** : messages identifiés comme hameçonnage lors du traitement par différents filtres.<sup>\*</sup>
  - **Blocage du courrier indésirable** : messages identifiés comme courrier indésirable pendant le traitement par différents filtres.<sup>\*</sup>
  - **Bloc d’emprunt d’identité** : messages détectés comme emprunt d’identité d’utilisateur ou emprunt d’identité de domaine dans Defender pour Office 365.<sup>\*</sup>
  - **Bloc de détonation** : messages détectés pendant la détonation de fichier ou d’URL par des stratégies de pièces jointes sécurisées ou des stratégies liens sécurisés dans Defender pour Office 365.<sup>\*</sup>
  - **ZAP supprimé** : messages supprimés par vidage automatique de zéro heure (ZAP).<sup>\*</sup>
  - **Remis** : messages remis aux utilisateurs en raison d’une autorisation.<sup>\*</sup>

Si vous pointez sur une bande horizontale dans le diagramme, vous verrez le nombre de messages associés.

<sup>\*</sup> Si vous cliquez sur cet élément, le diagramme est développé pour afficher d’autres détails. Pour obtenir une description de chaque élément dans les nœuds développés, consultez [Technologies de détection](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-details.png" alt-text="Détails du bloc d’hameçonnage en mode Flux de courrier dans le rapport d’état Mailflow" lightbox="../../media/mail-flow-status-report-mailflow-view-details.png":::

Le tableau des détails sous le diagramme affiche les informations suivantes :

- **Date**
- **Nombre total d’e-mails**
- **Edge filtré**
- **Messages de règle**
- **Moteur anti-programme malveillant, pièces jointes sécurisées, règle filtrée**
- **Emprunt d’identité DMARC, usurpation d’identité, hameçonnage filtré**
- **Détection de détonation**
- **Anti-courrier indésirable filtré**
- **ZAP supprimé**
- **Messages où aucune menace n’a été détectée**

Si vous sélectionnez une ligne dans la table de détails, une répartition supplémentaire du nombre d’e-mails s’affiche dans le menu volant des détails qui s’affiche.

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** **date de début** et **date de fin**.
- **Direction** : **sortant et** **entrant**.

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

De retour sur la page rapport **d’état mailflow** , vous pouvez cliquer sur **Afficher les tendances** pour afficher les graphiques de tendance dans le menu volant **Tendances du flux** de courrier qui s’affiche.

:::image type="content" source="../../media/mail-flow-status-report-mailflow-view-show-trends.png" alt-text="Menu volant Tendances du flux de courrier en mode Flux de courrier dans le rapport d’état mailflow" lightbox="../../media/mail-flow-status-report-mailflow-view-show-trends.png":::

Dans la page **rapport d’état du flux de courrier** , l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **Le bouton Exporter** est disponible.

## <a name="malware-detections-report"></a>Rapport sur les détections de programmes malveillants

> [!NOTE]
> Ce rapport a été déprécié. Les mêmes informations sont disponibles dans le [rapport d’état de la protection contre les menaces](#threat-protection-status-report).

## <a name="mail-latency-report"></a>Rapport de latence de courrier

Le **rapport de latence** du courrier dans Defender pour Office 365 contient des informations sur la latence de remise et de détonation du courrier au sein de votre organisation. Pour plus d’informations, consultez le [rapport de latence du courrier](view-reports-for-mdo.md#mail-latency-report).

## <a name="spam-detections-report"></a>Rapport sur la détection des courriers indésirables

> [!NOTE]
> Ce rapport a été déprécié. Les mêmes informations sont disponibles dans le [rapport d’état de la protection contre les menaces](#threat-protection-status-report).

## <a name="spoof-detections-report"></a>Rapport des détections d’usurpation d’identité

Le rapport **des détections** d’usurpation d’identité affiche des informations sur les messages qui ont été bloqués ou autorisés en raison de l’usurpation d’identité. Pour plus d’informations sur l’usurpation d’identité, consultez [la protection contre l’usurpation d’identité dans EOP](anti-spoofing-protection.md).

La vue d’agrégation du rapport autorise 90 jours de filtrage, tandis que l’affichage détaillé n’autorise que dix jours de filtrage.

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, recherchez **les détections d’usurpation d’identité**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/SpoofMailReport>.

:::image type="content" source="../../media/spoof-detections-widget.png" alt-text="Widget Détections d’usurpation d’identité dans la page des rapports de collaboration Email &" lightbox="../../media/spoof-detections-widget.png":::

Le graphique affiche les informations suivantes :

- **Passer**
- **Échouer**
- **SoftPass**
- **Aucune**
- **Other**

Lorsque vous pointez sur un jour (point de données) dans le graphique, vous pouvez voir le nombre de messages usurpés détectés et pourquoi.

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date (UTC)** **Date de début** et **date de fin**
- **Résultat** :
  - **Passer**
  - **Échouer**
  - **SoftPass**
  - **Aucune**
  - **Other**
- **Type d’usurpation** d’identité : **interne** et **externe**

:::image type="content" source="../../media/spoof-detections-report-page.png" alt-text="Page du rapport de courrier d’usurpation d’identité dans le portail Microsoft 365 Defender" lightbox="../../media/spoof-detections-report-page.png":::

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Date**
- **Utilisateur usurpé**
- **Envoi d’une infrastructure**
- **Type d’usurpation d’identité**
- **Résultat**
- **Code de résultat**
- **SPF**
- **DKIM**
- **DMARC**
- **Nombre de messages**

Pour plus d’informations sur les codes de résultat d’authentification composite, consultez [les en-têtes de message anti-courrier indésirable dans Microsoft 365](anti-spam-message-headers.md).

Dans la page **Détections d’usurpation** d’identité, icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

## <a name="submissions-report"></a>Rapport sur les soumissions

Le rapport **Soumissions affiche des** informations sur les éléments que les administrateurs ont signalés à Microsoft à des fins d’analyse. Pour plus d’informations, consultez [Utiliser Administration Soumission pour envoyer des courriers indésirables, des hameçonnages, des URL et des fichiers suspects à Microsoft](admin-submission.md).

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, **recherchez Soumissions**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/adminSubmissionReport>. Pour accéder aux [soumissions d’administrateur dans le portail Microsoft 365 Defender](admin-submission.md), cliquez sur **Accéder aux soumissions**. Les administrateurs pourront afficher le rapport pendant les 30 derniers jours.

:::image type="content" source="../../media/submissions-report-widget.png" alt-text="Widget Soumissions dans la page Email & rapports de collaboration" lightbox="../../media/submissions-report-widget.png":::

Le graphique affiche les informations suivantes :

- **Pending**
- **Terminée**

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date signalée** : **heure de début** et **heure de fin**
- **Type de soumission** :
  - **Courrier électronique**
  - **URL**
  - **Fichier**
- **ID de soumission**
- **ID de message réseau**
- **Sender**
- **Name**
- **Soumis par**
- **Raison de l’envoi** :
  - **Pas de courrier indésirable**
  - **Hameçonnage**
  - **Programme malveillant**
  - **Courrier indésirable**
- **État de rescan** :
  - **Pending**
  - **Terminée**

Le tableau des détails sous le graphique affiche les mêmes informations et contient les mêmes options **De groupe** ou **personnaliser les colonnes** que dans l’onglet **Soumis pour analyse** de Email & **soumissions** de **collaboration**\>. Pour plus d’informations, consultez [Afficher les soumissions d’administrateur de messagerie à Microsoft](admin-submission.md#view-email-admin-submissions-to-microsoft).

Dans la page **Soumissions** , le bouton **[Exporter](#export-report)** est disponible.

:::image type="content" source="../../media/submissions-report-page.png" alt-text="Page du rapport Soumissions dans le portail Microsoft 365 Defender" lightbox="../../media/submissions-report-page.png":::

## <a name="threat-protection-status-report"></a>Rapport sur l’état de la protection contre les menaces

Le rapport **d’état de la protection contre les menaces** est disponible dans EOP et Defender pour Office 365 ; toutefois, les rapports contiennent des données différentes. Par exemple, les clients EOP peuvent afficher des informations sur les programmes malveillants détectés dans le courrier électronique, mais pas sur les fichiers [malveillants détectés par les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Le rapport fournit le nombre de messages électroniques contenant du contenu malveillant, tels que des fichiers ou des adresses de site web (URL) qui ont été bloqués par le moteur anti-programme malveillant, le [vidage automatique de zéro heure (ZAP)](zero-hour-auto-purge.md) et Defender pour Office 365 [fonctionnalités telles que les liens sécurisés](safe-links.md), [les pièces jointes sécurisées et les fonctionnalités](safe-attachments.md) de protection contre l’emprunt d’identité [dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365). Vous pouvez utiliser ces informations pour identifier les tendances ou déterminer si les stratégies d’organisation doivent être ajuster.

**Remarque** : Il est important de comprendre que si un message est envoyé à cinq destinataires, nous le comptabilisons comme cinq messages différents et non comme un seul message.

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, recherchez l’état **de la protection contre les menaces**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez l’une des URL suivantes :

- Defender pour Office 365 :<https://security.microsoft.com/reports/TPSAggregateReportATP>
- EOP: <https://security.microsoft.com/reports/TPSAggregateReport>

:::image type="content" source="../../media/threat-protection-status-report-widget.png" alt-text="Widget d’état de la protection contre les menaces dans la page des rapports de collaboration Email &" lightbox="../../media/threat-protection-status-report-widget.png":::

Par défaut, le graphique affiche les données des 7 derniers jours. Si vous cliquez sur **Filtrer** dans la page rapport **d’état de la protection contre les menaces** , vous pouvez sélectionner une plage de dates de 90 jours (les abonnements d’évaluation peuvent être limités à 30 jours). Le tableau de détails autorise le filtrage pendant 30 jours.

Les vues disponibles sont décrites dans les sections suivantes.

### <a name="view-data-by-overview"></a>Afficher les données par vue d’ensemble

:::image type="content" source="../../media/threat-protection-status-report-overview-view.png" alt-text="Vue Vue d’ensemble dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-overview-view.png":::

Dans la vue **Afficher les données par vue d’ensemble** , les informations de détection suivantes sont affichées dans le graphique :

- **programmes malveillants Email**
- **Email hameçonnage**
- **Email courrier indésirable**
- **Programme malveillant de contenu**

Aucune table de détails n’est disponible sous le graphique.

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **date de début** et **date de fin**.
- **Détection** : les mêmes valeurs que dans le graphique.
- **Protégé par** : **MDO** (Defender pour Office 365) et **EOP**.
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes fiables**
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

### <a name="view-data-by-email--phish-and-chart-breakdown-by-detection-technology"></a>Afficher les données par Email \> phish et répartition des graphiques par technologie de détection

:::image type="content" source="../../media/threat-protection-status-report-phishing-detection-tech-view.png" alt-text="Vue de la technologie de détection pour les e-mails de hameçonnage dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-phishing-detection-tech-view.png":::

> [!NOTE]
> Depuis mai 2021, les détections de hameçonnage dans les e-mails ont été mises à jour pour inclure **les pièces jointes de message** qui contiennent des URL de hameçonnage. Cette modification peut déplacer une partie du volume de détection hors des **données d’affichage en Email \> vue Programmes malveillants** et dans les **données d’affichage par Email \> vue Phish**. En d’autres termes, les pièces jointes de message avec des URL de hameçonnage qui étaient traditionnellement identifiées comme des programmes malveillants peuvent maintenant être identifiées comme hameçonnage à la place.

Dans la **vue Afficher les données par Email \> phish** et **répartition du graphique par** la vue Technologie de détection, les informations suivantes sont affichées dans le graphique :

- **Filtre avancé** : signaux d’hameçonnage basés sur le Machine Learning.
- **Campagne**<sup>\*</sup> : messages identifiés dans le cadre d’une [campagne](campaigns.md).
- **Détonation**<sup>\*</sup> de fichier : [des pièces jointes sécurisées](safe-attachments.md) ont détecté une pièce jointe malveillante lors de l’analyse de la détonation.
- Réputation <sup>\*</sup>**de détonation de** fichier : pièces jointes précédemment détectées par les détonations de [pièces jointes sécurisées](safe-attachments.md) dans d’autres organisations Microsoft 365.
- **Réputation du** fichier : le message contient un fichier précédemment identifié comme malveillant dans d’autres organisations Microsoft 365.
- **Correspondance des empreintes digitales** : le message ressemble étroitement à un message malveillant détecté précédemment.
- **Filtre général** : Signaux d’hameçonnage basés sur des règles d’analyste.
- **Marque d’emprunt d’identité** : emprunt d’identité de l’expéditeur de marques connues.
- **Domaine d’emprunt d’identité**<sup>\*</sup> : emprunt d’identité des domaines d’expéditeur que vous possédez ou que vous avez spécifiés pour la protection dans les [stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).
- **Utilisateur d’emprunt d’identité**<sup>\*</sup> : emprunt d’identité d’expéditeurs protégés que vous avez spécifiés dans les [stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) ou appris par le biais de l’intelligence de boîte aux lettres.
- **Emprunt d’identité d’intelligence de**<sup>\*</sup> boîte aux lettres : détections d’emprunt d’identité à partir de l’intelligence de boîte aux lettres dans les [stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).
- **Détection d’analyse mixte** : plusieurs filtres ont contribué au verdict du message.
- **Usurpation DMARC** : le message a échoué à [l’authentification DMARC](use-dmarc-to-validate-email.md).
- **Usurpation d’identité de domaine externe** : usurpation d’adresse e-mail de l’expéditeur à l’aide d’un domaine externe à votre organisation.
- **Usurpation d’identité intra-organisation** : usurpation d’adresse e-mail de l’expéditeur à l’aide d’un domaine interne à votre organisation.
- **Détonation**<sup>\*</sup> d’URL : [Des liens fiables](safe-links.md) ont détecté une URL malveillante dans le message lors de l’analyse de la détonation.
- Réputation <sup>\*</sup>**de détonation d’URL** : URL précédemment détectées par les détonations Safe [Links](safe-links.md) dans d’autres organisations Microsoft 365.
- **Réputation malveillante de l’URL** : le message contient une URL précédemment identifiée comme malveillante dans d’autres organisations Microsoft 365.

<sup>\*</sup>Defender pour Office 365 uniquement

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Technologie de détection** : valeurs de technologie de détection identiques du graphique.
- **État de remise**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Détection** : les mêmes valeurs que dans le graphique.
- **Protégé par** : **MDO** (Defender pour Office 365) ou **EOP**
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes fiables**
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **tout** ou la stratégie spécifiée.
- **Destinataires**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="view-data-by-email--spam-and-chart-breakdown-by-detection-technology"></a>Afficher les données par Email \> le courrier indésirable et la répartition des graphiques par technologie de détection

:::image type="content" source="../../media/threat-protection-status-report-spam-detection-tech-view.png" alt-text="Vue de la technologie de détection du courrier indésirable dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-spam-detection-tech-view.png":::

Dans la **vue Afficher les données par Email \> courrier indésirable** et **la répartition du graphique par** la vue Technologie de détection, les informations suivantes sont affichées dans le graphique :

- **Filtre avancé** : signaux d’hameçonnage basés sur le Machine Learning.
- **En bloc** : le [niveau de réclamation en bloc (BCL)](bulk-complaint-level-values.md) du message dépasse le seuil défini pour le courrier indésirable.
- **Réputation du domaine** : le message provenait d’un domaine précédemment identifié comme étant l’envoi de courrier indésirable dans d’autres organisations Microsoft 365.
- **Correspondance des empreintes digitales** : le message ressemble étroitement à un message malveillant détecté précédemment.
- **Réputation d’adresse IP** : le message provient d’une source précédemment identifiée comme étant l’envoi de courrier indésirable dans d’autres organisations Microsoft 365.
- **Détection d’analyse mixte** : plusieurs filtres ont contribué au verdict du message.
- **Réputation malveillante de l’URL** : le message contient une URL précédemment identifiée comme malveillante dans d’autres organisations Microsoft 365.

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Technologie de détection** : valeurs de technologie de détection identiques du graphique.
- **État de remise**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Détection** : les mêmes valeurs que dans le graphique.
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes fiables**
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **tout** ou la stratégie spécifiée.
- **Destinataires**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="view-data-by-email--malware-and-chart-breakdown-by-detection-technology"></a>Afficher les données par Email \> les programmes malveillants et la répartition des graphiques par technologie de détection

:::image type="content" source="../../media/threat-protection-status-report-malware-detection-tech-view.png" alt-text="Vue de la technologie de détection pour les programmes malveillants dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-malware-detection-tech-view.png":::

> [!NOTE]
> Depuis mai 2021, les détections de programmes malveillants dans les e-mails ont été mises à jour pour inclure **des URL dangereuses dans les** pièces jointes des messages. Cette modification peut déplacer une partie du volume de détection hors des **données d’affichage par Email \> vue Phish** et dans les **données d’affichage par Email \> vue Programmes malveillants**. En d’autres termes, les URL dangereuses dans les pièces jointes de message qui étaient traditionnellement identifiées comme hameçonnage maintenant peuvent être identifiées comme des programmes malveillants à la place.

Dans la **vue Afficher les données par Email \> programmes malveillants** et **la répartition du graphique par** technologie de détection, les informations suivantes sont affichées dans le graphique :

- **Détonation**<sup>\*</sup> de fichier : [des pièces jointes sécurisées](safe-attachments.md) ont détecté une pièce jointe malveillante lors de l’analyse de la détonation.
- Réputation <sup>\*</sup>**de détonation de** fichier : pièces jointes précédemment détectées par les détonations de [pièces jointes sécurisées](safe-attachments.md) dans d’autres organisations Microsoft 365.
- **Réputation du** fichier : le message contient un fichier précédemment identifié comme malveillant dans d’autres organisations Microsoft 365.
- **Moteur anti-programme malveillant**<sup>\*</sup> : détection à partir de moteurs anti-programmes malveillants.
- **Bloc de type de fichier de stratégie anti-programme malveillant** : le message a été bloqué en raison du type de fichier de la pièce jointe ([filtrage courant des pièces jointes dans les stratégies anti-programmes malveillants](anti-malware-protection.md)).
- **Détonation**<sup>\*</sup> d’URL : [Des liens fiables](safe-links.md) ont détecté une URL malveillante dans le message lors de l’analyse de la détonation.
- Réputation <sup>\*</sup> **de détonation d’URL**> : URL précédemment détectées par des détonations de [liens fiables](safe-links.md) dans d’autres organisations Microsoft 365.
- **Campagne**<sup>\*</sup> : messages identifiés dans le cadre d’une [campagne](campaigns.md).

<sup>\*</sup>Defender pour Office 365 uniquement

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Technologie de détection** : valeurs de technologie de détection identiques du graphique.
- **État de la remise**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Détection** : les mêmes valeurs que dans le graphique.
- **Protégé par** : **MDO** (Defender pour Office 365) ou **EOP**
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes fiables**
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **tout** ou la stratégie spécifiée.
- **Destinataires**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="chart-breakdown-by-policy-type"></a>Répartition du graphique par type de stratégie

:::image type="content" source="../../media/threat-protection-status-report-phishing-policy-type-view.png" alt-text="Vue Type de stratégie pour les e-mails de hameçonnage, courrier indésirable ou courrier malveillant dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-phishing-policy-type-view.png":::

Dans Les **données d’affichage par Email \> Hameçonnage**, **Afficher les données par Email \> Courrier indésirable** ou **Afficher les données par Email \> affichages programmes malveillants**, la sélection de la **répartition du graphique par type de** stratégie affiche les informations suivantes dans le graphique :

- **Anti-programme malveillant**
- **Pièces jointes sécurisées**<sup>\*</sup>
- **Anti-hameçonnage**
- **Anti-spam**
- **Règle de flux de courrier** (également appelée règle de transport)
- **Autres**

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Technologie de détection** : valeurs de technologie de détection identiques du graphique.
- **État de remise**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Détection** : valeurs de la technologie de détection, comme décrit précédemment dans cet article et dans [les technologies de détection](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).
- **Protégé par** : **MDO** (Defender pour Office 365) ou **EOP**
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes fiables**
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **tout** ou la stratégie spécifiée.
- **Destinataires**

<sup>\*</sup>Defender pour Office 365 uniquement

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="chart-breakdown-by-delivery-status"></a>Répartition du graphique par état de remise

:::image type="content" source="../../media/threat-protection-status-report-phishing-delivery-status-view.png" alt-text="Vue État de la remise pour les e-mails de hameçonnage et les e-mails de programmes malveillants dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-phishing-delivery-status-view.png":::

Dans les **vues Afficher les données par Email \> Hameçonnage**, **Afficher les données par Email \> Courrier indésirable** ou **Afficher les données par Email \> affichages programmes malveillants**, la sélection de la **répartition du graphique par état de remise** affiche les informations suivantes dans le graphique :

- **Boîte aux lettres hébergée : Boîte de réception**
- **Boîte aux lettres hébergée : Courrier indésirable**
- **Boîte aux lettres hébergée : dossier personnalisé**
- **Boîte aux lettres hébergée : éléments supprimés**
- **Transmis**
- **Serveur local : livré**
- **Mise en quarantaine**
- **Échec de la remise**
- **Abandonné**

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Technologie de détection** : valeurs de technologie de détection identiques du graphique.
- **État de remise**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Détection** : valeurs de la technologie de détection, comme décrit précédemment dans cet article et dans [les technologies de détection](/office/office-365-management-api/office-365-management-activity-api-schema#detection-technologies).
- **Protégé par** : **MDO** (Defender pour Office 365) ou **EOP**
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes fiables**
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **tout** ou la stratégie spécifiée.
- **Destinataires**

<sup>\*</sup>Defender pour Office 365 uniquement

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="view-data-by-content--malware"></a>Afficher les données par programme malveillant de contenu \>

:::image type="content" source="../../media/threat-protection-status-report-content-malware-view.png" alt-text="Affichage Des programmes malveillants de contenu dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-content-malware-view.png":::

Dans la vue **Afficher les données par programme malveillant de contenu\>**, les informations suivantes sont affichées dans le graphique pour Microsoft Defender pour Office 365 organisations :

- **Moteur anti-programme malveillant** : fichiers malveillants détectés dans SharePoint, OneDrive et Microsoft Teams par la [détection de virus intégrée dans Microsoft 365](virus-detection-in-spo.md).
- **Détonation MDO** : fichiers [malveillants détectés par des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).
- **Réputation du** fichier : le message contient un fichier précédemment identifié comme malveillant dans d’autres organisations Microsoft 365.

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date (UTC)**
- **Nom de fichier des pièces jointes**
- **Charge de travail**
- **Technologie de détection** : valeurs de technologie de détection identiques du graphique.
- **Taille du fichier**
- **Dernière modification de l’utilisateur**

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **date de début** et **date de fin**.
- **Détection** : les mêmes valeurs que dans le graphique.
- **Charge de travail** : **Teams**, **SharePoint** et **OneDrive**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Créer une planification](#schedule-report)**, ![icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **[Demander un rapport](#request-report)** et ![exporter l’icône.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

### <a name="view-data-by-system-override-and-chart-breakdown-by-reason"></a>Afficher les données par remplacement système et répartition du graphique par raison

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png" alt-text="Remplacement de message et répartition du graphique par motif dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-reason.png":::

Dans les **données d’affichage par remplacement système** et **la répartition du graphique par vue Raison** , les informations de raison de remplacement suivantes sont affichées dans le graphique :

- **Ignorer localement**
- **Autorisation IP**
- **Règle de transport Exchange** (règle de flux de messagerie)
- **Expéditeurs autorisés par l’organisation**
- **Domaines autorisés par l’organisation**
- **ZAP non activé**
- **Expéditeur sécurisé de l’utilisateur**
- **Domaine sécurisé de l’utilisateur**
- **Simulation d’hameçonnage** : pour plus d’informations, consultez [Configurer la remise de simulations de hameçonnage tierces aux utilisateurs et les messages non filtrés dans les boîtes aux lettres SecOps](configure-advanced-delivery.md).
- **Filtre tiers**

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Remplacement du système**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Motif** : les mêmes valeurs que le graphique.
- **Emplacement de remise** : **dossier Courrier indésirable non activé** ou **boîte aux lettres SecOps**.
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** : **Tout**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **Tous**
- **Destinataires**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **[Le bouton Exporter](#export-report)** est disponible.

### <a name="view-data-by-system-override-and-chart-breakdown-by-delivery-location"></a>Afficher les données par remplacement système et répartition du graphique par emplacement de remise

:::image type="content" source="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png" alt-text="Remplacement de message et répartition du graphique par emplacement de remise dans le rapport d’état de la protection contre les menaces" lightbox="../../media/threat-protection-status-report-system-override-view-breakdown-by-delivery-location.png":::

Dans la **vue Afficher les données par remplacement système** et **la répartition du graphique par emplacement de remise** , les informations de raison de remplacement suivantes sont affichées dans le graphique :

- **Dossier Courrier indésirable non activé**
- **Boîte aux lettres SecOps** : pour plus d’informations, consultez [Configurer la remise de simulations d’hameçonnage tierces aux utilisateurs et les messages non filtrés aux boîtes aux lettres SecOps](configure-advanced-delivery.md).

Dans le tableau d’informations sous le graphique, les informations suivantes sont disponibles :

- **Date**
- **Sujet**
- **Expéditeur**
- **Destinataires**
- **Remplacement du système**
- **IP de l’expéditeur**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Date (UTC)** **Date de début** et **date de fin**
- **Raison**
  - **Ignorer localement**
  - **Autorisation IP**
  - **Règle de transport Exchange** (règle de flux de messagerie)
  - **Expéditeurs autorisés par l’organisation**
  - **Domaines autorisés par l’organisation**
  - **ZAP non activé**
  - **Expéditeur sécurisé de l’utilisateur**
  - **Domaine sécurisé de l’utilisateur**
  - **Simulation d’hameçonnage** : pour plus d’informations, consultez [Configurer la remise de simulations de hameçonnage tierces aux utilisateurs et les messages non filtrés dans les boîtes aux lettres SecOps](configure-advanced-delivery.md).
  - **Filtre tiers**
- **Emplacement de remise** : **dossier Courrier indésirable non activé** ou **boîte aux lettres SecOps**.
- **Direction** :
  - **All**
  - **Entrants**
  - **Sortant**
- **Balise** : **tout** ou la balise utilisateur spécifiée (y compris les comptes de priorité). Pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).
- **Domaine** : **tout** ou [un domaine accepté](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains).
- **Type de stratégie** :
  - **All**
  - **Anti-programme malveillant**
  - **Pièces jointes sécurisées**<sup>\*</sup>
  - **Anti-hameçonnage**
  - **Anti-spam**
  - **Règle de flux de courrier** (règle de transport)
  - **Autres**
- **Nom de la stratégie (affichage de table de détails uniquement)** : **Tous**
- **Destinataires**

<sup>\*</sup>Defender pour Office 365 uniquement

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **État de la protection contre les menaces** , l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **[Le bouton Exporter](#export-report)** est disponible.

## <a name="top-malware-report"></a>Rapport sur les programmes malveillants les plus répandus

Le rapport **top des programmes malveillants** présente les différents types de programmes malveillants détectés par [la protection anti-programme malveillant dans EOP](anti-malware-protection.md).

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, **recherchez les programmes malveillants principaux**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/TopMalware>.

:::image type="content" source="../../media/top-malware-report-widget.png" alt-text="Widget Top malware sur la page des rapports de collaboration Email &" lightbox="../../media/top-malware-report-widget.png":::

Lorsque vous pointez sur un coin dans le graphique à secteurs, vous pouvez voir le nom d’un type de programme malveillant et le nombre de messages détectés comme ayant ce programme malveillant.

Dans la page **Haut du rapport sur les programmes malveillants** , une version plus grande du graphique en secteurs s’affiche. Le tableau des détails sous le graphique affiche les informations suivantes :

- **Programmes les plus malveillants**
- **Count**

Si vous cliquez sur **Filtrer**, vous pouvez spécifier une plage de dates avec **date de début** et **date de fin**.

Dans la page **Des programmes malveillants supérieurs** , l’icône Créer une ![planification.](../../media/m365-cc-sc-create-icon.png) **[Icône Créer une planification](#schedule-report)** et ![exporter.](../../media/m365-cc-sc-download-icon.png) Des boutons **[d’exportation](#export-report)** sont disponibles.

:::image type="content" source="../../media/top-malware-report-view.png" alt-text="Affichage du rapport Sur les programmes malveillants" lightbox="../../media/top-malware-report-view.png":::

## <a name="top-senders-and-recipients-report"></a>Rapport des principaux expéditeurs et destinataires

Le rapport **des principaux expéditeurs et destinataires** est disponible dans EOP et Defender pour Office 365 ; toutefois, les rapports contiennent des données différentes. Par exemple, les clients EOP peuvent afficher des informations sur les principaux destinataires de programmes malveillants, de courrier indésirable et d’hameçonnage (usurpation d’identité), mais pas sur les programmes malveillants [détectés par les pièces jointes sécurisées](safe-attachments.md) ou le hameçonnage détecté par [la protection contre l’emprunt d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365).

Les principaux **expéditeurs et destinataires** affichent les principaux expéditeurs de messages de votre organisation, ainsi que les principaux destinataires des messages détectés par EOP et les fonctionnalités de protection Defender pour Office 365. Par défaut, le rapport affiche les données de la semaine dernière, mais les données sont disponibles pour les 90 derniers jours.

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, **recherchez les principaux expéditeurs et destinataires du rapport**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez l’une des URL suivantes :

- Defender pour Office 365 :<https://security.microsoft.com/reports/TopSenderRecipientsATP>
- EOP: <https://security.microsoft.com/reports/TopSenderRecipient>

:::image type="content" source="../../media/top-senders-and-recipients-widget.png" alt-text="Widget Principaux expéditeurs et destinataires dans le tableau de bord Rapports" lightbox="../../media/top-senders-and-recipients-widget.png":::

Lorsque vous pointez sur un coin dans le graphique en secteurs, vous pouvez voir le nombre de messages pour l’expéditeur ou le destinataire.

Dans la page **Principaux expéditeurs et destinataires** , une version plus grande du graphique en secteurs s’affiche. Les graphiques suivants sont disponibles :

- **Afficher les données des principaux expéditeurs de courrier** (il s’agit de l’affichage par défaut)
- **Afficher les données des principaux destinataires du courrier**
- **Afficher les données des principaux destinataires du courrier indésirable**
- **Afficher les données des principaux destinataires de programmes malveillants** (EOP)
- **Afficher les données des principaux destinataires du hameçonnage**
- **Afficher les données des principaux destinataires de programmes malveillants (MDO)**
- **Afficher les données des principaux destinataires de hameçonnage (MDO)**

Les données changent en fonction de votre sélection.

Lorsque vous pointez sur un coin dans le graphique en secteurs, vous pouvez voir le nombre de messages pour cet expéditeur ou destinataire spécifique.

Le tableau des détails sous le graphique affiche les expéditeurs ou les destinataires et le nombre de messages en fonction de la vue que vous avez sélectionnée.

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant **Date de début** et **Date de fin**. Les utilisateurs peuvent également filtrer par balises utilisateur. 

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Dans la page **Principaux expéditeurs et destinataires** , l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **Le bouton Exporter** est disponible.

:::image type="content" source="../../media/top-senders-and-recipients-report-view.png" alt-text="Affichage Afficher les données pour les expéditeurs de courrier supérieur dans le rapport Meilleurs expéditeurs et destinataires" lightbox="../../media/top-senders-and-recipients-report-view.png":::

## <a name="url-protection-report"></a>Rapport sur la protection des URL

Le **rapport de protection d’URL** est disponible uniquement dans Microsoft Defender pour Office 365. Pour plus d’informations, consultez le [rapport de protection des URL](view-reports-for-mdo.md#url-protection-report).

## <a name="user-reported-messages-report"></a>Rapport des messages signalés par l’utilisateur

> [!IMPORTANT]
> Pour que le rapport des **messages signalés par l’utilisateur** fonctionne correctement, la **journalisation d’audit doit être activée** pour votre environnement Microsoft 365. Cela est généralement effectué par une personne qui a le rôle Journaux d’audit attribué dans Exchange Online. Pour plus d’informations, consultez [Activer ou désactiver la recherche dans le journal d’audit Microsoft 365](../../compliance/turn-audit-log-search-on-or-off.md).

Le rapport des **messages signalés par l’utilisateur** affiche des informations sur les messages électroniques signalés par les utilisateurs comme indésirables, tentatives d’hameçonnage ou courriers corrects à l’aide du [complément Message](enable-the-report-message-add-in.md) de rapport ou du [complément De hameçonnage de rapport](enable-the-report-phish-add-in.md).

Pour afficher le rapport dans le portail Microsoft 365 Defender, accédez à **Rapports** \> **Email & collaboration** \> **Email & rapports de collaboration**. Dans la page **Email & rapports de collaboration**, recherchez **les messages signalés par l’utilisateur**, puis cliquez sur **Afficher les détails**. Pour accéder directement au rapport, ouvrez <https://security.microsoft.com/reports/userSubmissionReport>. Pour accéder aux [soumissions d’administrateur dans le portail Microsoft 365 Defender](admin-submission.md), cliquez sur **Accéder aux soumissions**.

:::image type="content" source="../../media/user-reported-messages-widget.png" alt-text="Widget de messages signalés par l’utilisateur dans la page des rapports de collaboration Email &" lightbox="../../media/user-reported-messages-widget.png":::

Vous pouvez filtrer le graphique et la table de détails en cliquant sur **Filtrer** et en sélectionnant une ou plusieurs des valeurs suivantes dans le menu volant qui s’affiche :

- **Date signalée** : **heure de début** et **heure de fin**
- **Auteur du rapport**
- **Sujet de l’e-mail**
- **ID signalé du message**
- **ID de message réseau**
- **Sender**
- **Motif signalé**
  - **Pas de courrier indésirable**
  - **Hameçonnage**
  - **Courrier indésirable**
- **Simulation de hameçonnage** : **Oui** ou **non**

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Pour regrouper les entrées, cliquez sur **Grouper** et sélectionnez l’une des valeurs suivantes dans la liste déroulante :

- **Aucune**
- **Raison**
- **Sender**
- **Auteur du rapport**
- **Résultat de la nouvelle analyse**
- **Simulation de hameçonnage**

:::image type="content" source="../../media/user-reported-messages-report.png" alt-text="Rapport des messages signalés par l’utilisateur" lightbox="../../media/user-reported-messages-report.png":::

Le tableau des détails sous le graphique affiche les informations suivantes :

- **Sujet de l’e-mail**
- **Auteur du rapport**
- **Date signalée**
- **Sender**
- **Motif signalé**
- **Résultat de la nouvelle analyse**
- **Balises** : pour plus d’informations sur les balises utilisateur, consultez [Balises utilisateur](user-tags.md).

Pour envoyer un message à Microsoft à des fins d’analyse, sélectionnez l’entrée de message dans le tableau, cliquez sur **Envoyer à Microsoft pour analyse** , puis sélectionnez l’une des valeurs suivantes dans la liste déroulante :

- **Nettoyer le rapport**
- **Signaler le hameçonnage**
- **Signaler un programme malveillant**
- **Signaler le courrier indésirable** »
- **Déclencher une enquête** (Defender pour Office 365)

Dans la page **Messages signalés par l’utilisateur** , l’icône ![Exporter.](../../media/m365-cc-sc-download-icon.png) **[Le bouton Exporter](#export-report)** est disponible.

## <a name="what-permissions-are-needed-to-view-these-reports"></a>Quelles sont les autorisations nécessaires pour afficher ces rapports ?

Pour afficher et utiliser les rapports décrits dans cet article, vous devez être membre de l’un des groupes de rôles suivants dans le portail Microsoft 365 Defender :

- **Gestion de l'organisation**
- **Administrateur de sécurité**
- **Lecteur de sécurité**
- **Lecteur général**

Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

**Remarque** : l’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d'administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le portail Microsoft 365 Defender _et_ les autorisations pour d’autres fonctionnalités dans Microsoft 365. Pour plus d’informations, consultez la rubrique [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).

## <a name="what-if-the-reports-arent-showing-data"></a>Que se passe-t-il si les rapports n’affichent pas de données ?

Si vous ne voyez pas de données dans vos rapports, vérifiez les filtres que vous utilisez et vérifiez que vos stratégies sont correctement configurées. Pour en savoir plus, consultez [Protéger contre les menaces](protect-against-threats.md).

## <a name="schedule-report"></a>Rapport de planification

1. Dans la page principale du rapport spécifique, cliquez sur ![l’icône Créer une planification.](../../media/m365-cc-sc-create-icon.png) **Créez une planification**.
2. **L’Assistant Création d’un rapport planifié s’ouvre**. Dans la page **Du rapport planifié par nom** , passez en revue ou personnalisez la valeur **Name** , puis cliquez sur **Suivant**.
3. Dans la page **Définir les préférences** , configurez les paramètres suivants :
   - **Fréquence** : sélectionnez l’une des valeurs suivantes :
     - **Hebdomadaire** (par défaut)
     - **Mensuelle**
   - **Date de début** : date de début de la génération du rapport. La valeur par défaut est aujourd’hui.
   - **Date d’expiration** : à la fin de la génération du rapport. La valeur par défaut est d’un an à partir d’aujourd’hui.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Destinataires** , choisissez les destinataires du rapport. La valeur par défaut est votre adresse e-mail, mais vous pouvez en ajouter d’autres.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Révision** , passez en revue vos sélections. Vous pouvez cliquer sur le bouton **Précédent** ou le lien **Modifier** dans les sections respectives pour apporter des modifications.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

### <a name="managed-existing-scheduled-reports"></a>Rapports planifiés existants gérés

Pour gérer les rapports planifiés que vous avez déjà créés, procédez comme suit :

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **développer Email & collaboration** \> **sélectionnez Gérer les planifications**.

   Pour accéder directement à la page **Gérer les planifications** , utilisez <https://security.microsoft.com/ManageSubscription>.

2. Dans la page **Gérer les planifications** , les informations suivantes s’affichent pour chaque rapport planifié :
   - **Date de début de la planification**
   - **Nom de la planification**
   - **Type de rapport**
   - **Frequency**
   - **Dernier envoi**

   Recherchez le rapport planifié existant que vous souhaitez modifier.

3. Après avoir sélectionné le rapport planifié, effectuez l’une des actions suivantes dans le menu volant des détails qui s’ouvre :
   - **Modifier le nom** : cliquez sur ce bouton, modifiez le nom du rapport dans le menu volant qui s’affiche, puis cliquez sur **Enregistrer**.
   - **Supprimer la planification** : cliquez sur ce bouton, lisez l’avertissement qui s’affiche (les rapports précédents ne seront plus disponibles pour téléchargement), puis cliquez sur **Enregistrer**.
   - **Section Planifier les détails** : Cliquez sur **Modifier les préférences** pour modifier les paramètres suivants :
     - **Fréquence** : **hebdomadaire** ou **mensuelle**
     - **Date de début**
     - **Date d’expiration**

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   - **Section Destinataires** : Cliquez sur **Modifier les destinataires** pour ajouter ou supprimer des destinataires pour le rapport planifié. Lorsque vous avez terminé, cliquez sur **Enregistrer**

   Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="request-report"></a>Rapport de demande

1. Dans la page principale du rapport spécifique, cliquez sur ![l’icône Demander un rapport.](../../media/m365-cc-sc-download-icon.png) **Rapport de demande**.
2. L’Assistant **Création d’un rapport à la demande** s’ouvre. Dans la page **Du nom du rapport à la demande** , examinez ou personnalisez la valeur **Name** , puis cliquez sur **Suivant**.
3. Dans la page **Définir les préférences** , passez en revue ou configurez les paramètres suivants :
   - **Date de début** : date de début de la génération du rapport. La valeur par défaut est il y a un mois.
   - **Date d’expiration** : à la fin de la génération du rapport. La valeur par défaut est aujourd’hui.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Destinataires** , choisissez les destinataires du rapport. La valeur par défaut est votre adresse e-mail, mais vous pouvez en ajouter d’autres.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Révision** , passez en revue vos sélections. Vous pouvez cliquer sur le bouton **Précédent** ou le lien **Modifier** dans les sections respectives pour apporter des modifications.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

6. Une fois le rapport créé, vous accédez à la page Nouvelle création du **rapport à la demande** , où vous pouvez cliquer sur **Créer un autre rapport** ou **Terminé**.

   Le rapport est également disponible dans la page **Rapports pour téléchargement** , comme décrit dans la section suivante.

### <a name="download-reports"></a>Télécharger des rapports existants

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Rapports** \> **, développez Email & collaboration** \> sélectionnez **Rapports à télécharger**.

   Pour accéder directement à la page **Rapports à télécharger** , utilisez <https://security.microsoft.com/ReportsForDownload>.

2. Dans la page **Rapports à télécharger** , les informations suivantes s’affichent pour chaque rapport disponible :
   - **Date de début**
   - **Name**
   - **Type de rapport**
   - **Dernier envoi**
   - **Direction**

   Recherchez et sélectionnez le rapport que vous souhaitez télécharger.

## <a name="export-report"></a>Exporter le rapport

Dans la page principale du rapport spécifique, cliquez sur ![l’icône Exporter.](../../media/m365-cc-sc-download-icon.png) **Exporter** (si ce lien est disponible). Un menu volant **des conditions d’exportation** s’affiche dans lequel vous pouvez configurer les paramètres suivants :

- **Sélectionnez une vue à exporter** : sélectionnez l’une des valeurs suivantes :
  - **Résumé** : Les données sont disponibles pour les 90 derniers jours.
  - Détails : Les données sont disponibles pour les 30 **derniers** jours.
- **Date (UTC)** : **date de début** et **date de fin**.

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Exporter**. Dans la boîte de dialogue qui s’ouvre, vous pouvez choisir d’ouvrir le fichier, d’enregistrer le fichier ou de mémoriser la sélection.

Chaque fichier .csv exporté est limité à 150 000 lignes. Si les données contiennent plus de 150 000 lignes, plusieurs fichiers .csv sont créés.

## <a name="related-topics"></a>Voir aussi

[Protection anti-courrier indésirable dans EOP](anti-spam-protection.md)

[Protection contre les programmes malveillants dans EOP](anti-malware-protection.md)

[Rapports intelligents et insights dans le portail Microsoft 365 Defender](reports-and-insights-in-security-and-compliance.md)

[Afficher les rapports de flux de courrier dans le portail Microsoft 365 Defender](view-mail-flow-reports.md)

[Afficher les rapports pour Defender pour Office 365](view-reports-for-mdo.md)
