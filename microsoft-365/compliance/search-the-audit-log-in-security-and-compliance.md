---
title: Rechercher dans le journal d’audit dans le Centre de conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
description: Utilisez le Centre de conformité Microsoft 365 pour rechercher le journal d’audit unifié pour afficher les activités des utilisateurs et des administrateurs de votre organisation.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
ms.openlocfilehash: ff963c9bad09657899e9b163dacce46e6a246c6a
ms.sourcegitcommit: cafca45069819a44c7cf8c67f6c1e105de1b3393
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2022
ms.locfileid: "62520245"
---
# <a name="search-the-audit-log-in-the-compliance-center"></a>Recherchez le journal d’audit dans le centre de conformité

Vous avez besoin de déterminer si un utilisateur a consulté un document spécifique ou supprimé définitivement un élément de sa boîte aux lettres ? Vous pouvez utiliser l’outil de recherche de journal d’audit dans le Centre de conformité Microsoft 365 afin de rechercher le journal d’audit unifié pour afficher les activités des utilisateurs et des administrateurs de votre organisation. Des milliers d’opérations utilisateur et administrateur effectuées dans des dizaines de services et solutions Microsoft 365 sont capturées, enregistrées et conservées dans le journal d’audit unifié de votre organisation. Les utilisateurs de votre organisation peuvent utiliser l’outil de recherche du journal d’audit pour rechercher, afficher et exporter (vers un fichier CSV) les enregistrements d’audit pour ces opérations.

## <a name="microsoft-365-services-that-support-auditing"></a>Services Microsoft 365 qui prennent en charge l’audit

Pourquoi un journal d’audit unifié ? Vous pouvez rechercher dans le journal d’audit les activités effectuées dans différents services Microsoft 365. Le tableau suivant répertorie les services et fonctionnalités Microsoft 365 (par ordre alphabétique) pris en charge par le journal d’audit unifié.

| Service ou fonctionnalité Microsoft 365 | Types d’enregistrement|
|:---------|:---------|
| Azure Active Directory|AzureActiveDirectory, AzureActiveDirectoryAccountLogon, AzureActiveDirectoryStsLogon |
| Azure Information Protection|AipDiscover, AipSensitivityLabelAction, AipProtectionAction, AipFileDeleted, AipHeartBeat |
| Conformité des communications|ComplianceSuperVisionExchange|
| Explorateur de contenu|LabelContentExplorer|
| Protection contre la perte de données (DLP)|ComplianceDLPSharePoint, ComplianceDLPExchange, DLPEndpoint|
| Dynamics 365|CRM|
| eDiscovery|Découverte, AeD|
| Correspondances exactes de données|MipExactDataMatch|
| Exchange Online|ExchangeAdmin, ExchangeItem, ExchangeItemAggregated |
| Formulaires|MicrosoftForms|
| Cloisonnement de l’information|InformationBarrierPolicyApplication|
| Microsoft 365 Defender|AirInvestigation, AirManualInvestigation, AirAdminActionInvestigation, MS365DCustomDetection|
| Microsoft Teams|MicrosoftTeams|
| MyAnalytics|MyAnalyticsSettings|
| OneDrive Entreprise|OneDrive|
| Power Apps|PowerAppsApp, PowerAppsPlan|
| Power Automate|MicrosoftFlow|
| Power BI|PowerBIAudit|
| Quarantaine|Quarantaine|
| Stratégies de rétention et étiquettes de rétention|MIPLabel, MipAutoLabelExchangeItem, MipAutoLabelSharePointItem, MipAutoLabelSharePointPolicyLocation|
| Types d’informations sensibles|DlpSensitiveInformationType|
| Étiquettes de confidentialité|MIPLabel, SensitivityLabelAction, SensitivityLabeledFileAction, SensitivityLabelPolicyMatch|
| SharePoint Online|SharePoint, SharePointFileOperation,SharePointSharingOperation, SharePointListOperation, SharePointCommentOperation |
| Flux|MicrosoftStream|
| Threat Intelligence|ThreatIntelligence, ThreatIntelligenceUrl, ThreatFinder, ThreatIntelligenceAtpContent|
| Workplace Analytics|WorkplaceAnalytics|
| Yammer|Yammer|
|||

Pour plus d’informations sur les opérations auditées dans chacun des services répertoriés dans le tableau précédent, voir la section [Activités auditées](#audited-activities) dans cet article.

Le tableau précédent identifie également la valeur de type d’enregistrement à utiliser pour rechercher dans le journal d’audit les activités dans le service correspondant à l’aide de la cmdlet **Search-UnifiedAuditLog** dans Exchange Online PowerShell ou à l’aide d’un script PowerShell. Certains services ont plusieurs types d’enregistrement pour différents types d’activités au sein du même service. Pour obtenir une liste plus complète des types d’enregistrement d’audit, voir [Schéma de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).

 Pour plus d’informations sur l’utilisation de PowerShell pour effectuer des recherches dans le journal d’audit, voir :

- [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog)

- [Utiliser un script PowerShell pour effectuer une recherche dans le journal d’audit](audit-log-search-script.md)

## <a name="before-you-search-the-audit-log"></a>Avant de rechercher dans le journal d’audit

Avant de commencer à effectuer une recherche dans le journal d’audit, veillez à lire ce qui suit.

- Nous activons par défaut la recherche dans le journal d’audit pour les organisations d’entreprise Microsoft 365 et Office 365. Pour vérifier que vous avez activé la recherche dans le journal d’audit, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :

  ```powershell
  Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
  ```

  La valeur `True` de la propriété *UnifiedAuditLogIn élémentsenabled* indique que vous avez activé la recherche dans le journal d’audit. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md).

- Vous devez avoir le rôle Journaux d’audit en affichage seul ou Journaux d’audit dans Exchange Online pour pouvoir effectuer des recherches dans le journal d’audit. Par défaut, ces rôles sont affectés aux groupes de rôles Gestion de la conformité et Gestion de l’organisation sur la page **Autorisations** dans le Centre d’administration Exchange. Les administrateurs globaux dans votre client Office 365 et Microsoft 365 sont automatiquement des membres du groupe de rôle Gestion de l'organisation dans Exchange Online. Pour permettre à un utilisateur d’effectuer des recherches dans le journal d’audit avec le niveau minimal de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter le rôle Journaux d’audit en affichage seul ou Journaux d’audit, puis ajouter l’utilisateur en tant que membre du nouveau groupe de rôles. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](/Exchange/permissions-exo/role-groups).

  > [!IMPORTANT]
  > Si vous affectez le rôle Journaux d’audit en affichage seul ou Journaux d’audit à un utilisateur dans la page **Autorisations** dans le Centre de conformité Microsoft 365, celui-ci ne pourra pas effectuer de recherches dans le journal d’audit. Vous devez affecter les autorisations dans Exchange Online. En effet, la cmdlet sous-jacente utilisée pour les recherches dans le journal d’audit est une cmdlet Exchange Online.

- Lorsqu’une activité auditée est effectuée par un utilisateur ou un administrateur, un enregistrement d’audit est généré et stocké dans le journal d’audit pour votre organisation. La durée pendant laquelle un enregistrement d'audit est conservé (et consultable dans le journal d'audit) dépend de votre abonnement Office 365 ou Microsoft 365 Entreprise, et en particulier du type de licence attribuée à des utilisateurs spécifiques.

  - Pour les utilisateurs titulaires d’une licence Office 365 E5 ou d’une licence Microsoft 365 E5, ou les utilisateurs disposant d’une licence complémentaire de conformité Microsoft 365 E5 Conformité ou d’une licence Microsoft 365 E5 eDiscovery et Audit, les enregistrements d’audit pour l’activité Azure Active Directory, Exchange et SharePoint sont conservés pendant un an par défaut. Les organisations peuvent également créer des stratégies de rétention du journal d’audit pour conserver les enregistrements d’audit pour les activités dans d’autres services pendant un an. Pour plus d’informations, voir [gérer les stratégies de rétention du journal d’audit](audit-log-retention-policies.md).

    > [!NOTE]
    > Si votre organisation a participé au programme d’aperçu privé pour la conservation d’un an de rapports d’audit, la durée de conservation des enregistrements d’audit générés avant la date de lancement générale de la disponibilité ne sera pas réinitialisée.

  - Pour les utilisateurs auxquels toute autre licence Office 365 ou Microsoft 365 (non E5) est attribuée, les enregistrements d’audit sont conservés pendant 90 jours. Pour obtenir la liste des abonnements Office 365 et Microsoft 365 prenant en charge la journalisation d’audit unifiée, voir [la description de service du Centre de sécurité et conformité](/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

    > [!NOTE]
    > Même lorsque l’audit de boîtes aux lettres est activé par défaut, vous remarquerez peut-être que les événements d’audit de boîtes aux lettres de certains utilisateurs sont introuvables dans les recherches du journal d’audit dans le Centre de conformité Microsoft 365 ou via l’API Activité de gestion Office 365. Pour plus d’informations, consultez la rubrique [Plus d’informations sur la journalisation d’audit de boîtes aux lettres](enable-mailbox-auditing.md#more-information).

- Si vous souhaitez désactiver la recherche dans le journal d’audit pour votre organisation, vous pouvez exécuter la commande suivante dans une session PowerShell distante connectée à votre organisation Exchange Online :

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Pour réactiver la recherche d’audit, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Pour plus d’informations, consultez l’article [Désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md).

- Comme indiqué précédemment, la cmdlet sous-jacente utilisée pour effectuer une recherche dans le journal d’audit est une cmdlet Exchange Online, à savoir **Search-UnifiedAuditLog**. Cela signifie que vous pouvez utiliser cette cmdlet pour effectuer une recherche dans le journal d’audit au lieu d’utiliser l’outil de recherche sur la page **Audit** de la Centre de conformité Microsoft 365. Vous devez exécuter cette cmdlet dans PowerShell distant connecté à votre organisation Exchange Online. Pour plus d’informations, voir [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog).

  Pour plus d’informations sur l’exportation des résultats de recherche renvoyés par l’applet de commande **Search-UnifiedAuditLog** vers un fichier CSV, voir la section «conseils pour l'exportation et l’affichage du journal d’audit» dans [exporter, configurer et afficher les enregistrements du journal d’audit.](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Si vous souhaitez télécharger des données par programmation à partir du journal d’audit, nous vous recommandons d’utiliser l’API Activité de gestion Office 365 au lieu d’utiliser un script PowerShell. L’API Activité de gestion Office 365 est un service web REST que vous pouvez utiliser pour développer des solutions de surveillance des opérations, de la sécurité et de la conformité pour votre organisation. Pour plus d’informations, consultez [Référence de l’API Activité de gestion Office 365](/office/office-365-management-api/office-365-management-activity-api-reference).

- Azure Active Directory (Azure AD) est le service d’annuaire pour Microsoft 365. Le journal d’audit unifié contient les activités des utilisateurs, des groupes, des applications, des domaines et des annuaires effectuées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d’administration Microsoft 365</a> ou le portail de gestion Azure. Pour consulter la liste complète des événements Azure AD, voir [Événements de rapport d’audit d’Azure Active Directory](/azure/active-directory/reports-monitoring/concept-audit-logs).

- Après la survenue d’un événement, le renvoi de l'enregistrement de journal d’audit correspondant dans les résultats de la recherche d'un journal peut prendre jusqu’à 30 minutes, voir 24 heures. Le tableau suivant répertorie les délais en fonction des services dans Microsoft 365.

  |Service ou fonctionnalité Microsoft 365|30 minutes|24 heures|
  |---|:---:|:---:|
  |Defender pour Microsoft 365 et Threat Intelligence|![Coche.](../media/checkmark.png)||
  |Azure Active Directory (événements de connexion utilisateur)||![Coche.](../media/checkmark.png)|
  |Azure Active Directory (événements administrateur)||![Coche.](../media/checkmark.png)|
  |Protection contre la perte de données|![Coche.](../media/checkmark.png)||
  |Dynamics 365 CRM||![Coche.](../media/checkmark.png)|
  |eDiscovery|![Coche.](../media/checkmark.png)||
  |Exchange Online|![Coche.](../media/checkmark.png)||
  |Microsoft Power Automate||![Coche.](../media/checkmark.png)|
  |Microsoft Stream|![Coche.](../media/checkmark.png)||
  |Microsoft Teams|![Coche.](../media/checkmark.png)||
  |Power Apps||![Coche.](../media/checkmark.png)|
  |Power BI|![Coche.](../media/checkmark.png)||
  |Centre de conformité Microsoft 365|![Coche.](../media/checkmark.png)||
  |Étiquettes de confidentialité||![Coche.](../media/checkmark.png)|
  |Sharepoint Online et OneDrive Entreprise|![Coche.](../media/checkmark.png)||
  |Workplace Analytics|![Coche.](../media/checkmark.png)||
  |Yammer||![Coche.](../media/checkmark.png)|
  |Microsoft Forms|![Coche.](../media/checkmark.png)||
  ||||

- L’enregistrement d’audit pour Power BI n’est pas activé par défaut. Pour rechercher des activités Power BI dans le journal d’audit, vous devez activer l’audit dans le portail d’administration Power BI. Pour consulter des instructions, voir la section «journaux d’audit» du [portail d’administration Power BI](/power-bi/service-admin-portal#audit-logs).

## <a name="search-the-audit-log"></a>Effectuer une recherche dans le journal d’audit

Pour effectuer une recherche dans le journal d’audit dans Microsoft 365, vous devez procéder comme suit. 

[Étape 1 : effectuer une recherche dans le journal d’audit](#step-1-run-an-audit-log-search)

[Étape 2 : consulter les résultats de la recherche](#step-2-view-the-search-results)

[Étape 3 : exporter les résultats de la recherche dans un fichier](#step-3-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>Étape 1 : effectuer une recherche dans le journal d’audit

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

    > [!TIP]
    > Utilisez une session de navigation privée (et non une session normale) pour accéder au Centre de conformité Microsoft 365, car cela empêche l’utilisation des informations d’identification avec lesquelles vous êtes actuellement connecté. Appuyez sur **CTRL+SHIFT+N** pour ouvrir une session de navigation InPrivate dans Microsoft Edge ou une session de navigation privée dans Google Chrome (appelée fenêtre incognito).

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Audit**.

    La page **Audit** s’affiche.

    ![Configurez les critères, puis cliquez sur Rechercher pour générer un rapport.](../media/AuditLogSearchPage1.png)

    > [!NOTE]
    > Si le lien **Commencer à enregistrer les activités des utilisateurs et des administrateurs** apparaît, cliquez dessus pour activer l’audit. Si ce lien n’apparaît pas, l’audit est déjà été activé pour votre organisation.

3. Sur l’onglet **Recherche**, configurez les critères de recherche suivants : 

   1. **Date de début** et **Date de fin** : Les sept derniers jours sont sélectionnés par défaut. Sélectionnez une plage de dates et d’heures pour afficher les événements survenus pendant cette période. La date et l’heure sont présentées dans l’heure locale. La plage de dates maximale que vous pouvez spécifier est de 90 jours. Une erreur s’affiche si la plage de dates sélectionnée est supérieure à 90 jours.

    > [!TIP]
    > Si vous utilisez la plage de dates maximale de 90 jours, sélectionnez l’heure actuelle pour l’option **Date de début**. Dans le cas contraire, un message d’erreur indiquant que la date de début est antérieure à la date de fin apparaît. Si vous avez activé l’audit au cours des 90 derniers jours, la plage de dates maximale ne peut pas commencer avant la date à laquelle l’audit a été activé.

   2. **Activités** : Cliquez sur la liste déroulante pour afficher les activités que vous pouvez rechercher. Les activités des utilisateurs et des administrateurs sont organisées au sein de groupes d’activités liées. Vous pouvez sélectionner des activités spécifiques ou cliquer sur le nom d’un groupe d’activités pour sélectionner toutes les activités du groupe. Vous pouvez également cliquer sur une activité sélectionnée pour effacer la sélection. Une fois la recherche terminée, seules les entrées du journal d’audit correspondant aux activités sélectionnées apparaissent. La sélection de l’option **Afficher les résultats pour toutes les activités** affiche les résultats de toutes les activités effectuées par l’utilisateur ou le groupe d’utilisateurs sélectionné.<br/><br/>Plus de 100 activités utilisateur et administrateur sont enregistrées dans le journal d’audit. Cliquez sur l’onglet **Activités auditées** pour consulter les descriptions de chaque activité pour les différents services.

   3. **Utilisateurs** : Cliquez dans cette zone, puis sélectionnez un ou plusieurs utilisateurs pour lesquels afficher les résultats. Les entrées du journal d’audit pour l’activité sélectionnée effectuée par les utilisateurs que vous sélectionnez dans cette zone apparaissent dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs (et les comptes de service) dans votre organisation.

   4. **Fichier, dossier ou site** : Tapez l’entièreté ou une partie du nom d’un fichier ou d’un dossier pour rechercher les activités liées au fichier ou au dossier qui contient le mot clé spécifié. Vous pouvez également spécifier l’URL d’un fichier ou d’un dossier. Si vous utilisez une URL, veillez à entre l’URL complète. Si vous ne tapez qu’une partie de l’URL, n’incluez aucun caractère spécial ou espace.<br/><br/>Laissez cette zone vide pour renvoyer les entrées correspondant à tous les fichiers et dossiers dans votre organisation.

    > [!TIP]
    >
    > - Si vous recherchez toutes les activités concernant un **site**, ajoutez le symbole générique (\*) après l’URL pour renvoyer toutes les entrées de ce site ; par exemple, `"https://contoso-my.sharepoint.com/personal*"`
    >
    > - Si vous recherchez toutes les activités associées à **un fichier**, ajoutez le symbole générique (\*) avant le nom de fichier pour renvoyer toutes les entrées de ce fichier, par exemple, `"*Customer_Profitability_Sample.csv"`.

4. Cliquez sur **Rechercher** pour effectuer la recherche à l’aide de vos critères de recherche. 

   Les résultats de recherche sont chargés, puis affichés sur une nouvelle page. Une fois la recherche terminée, le nombre de résultats détectés est affiché. Un maximum de 5 000 événements s’affichent par incréments de 150 événements. Si plus de 5 000 événements correspondent aux critères de recherche, les 5 000 événements les plus récents sont affichés.

   ![Le nombre de résultats affichés une fois la recherche terminée.](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>Conseils pour effectuer une recherche dans le journal d’audit

- Vous pouvez sélectionner des activités spécifiques à rechercher en cliquant sur le nom des activités. Vous pouvez également rechercher toutes les activités dans un groupe (par exemple, **Activités des fichiers et des dossiers**) en cliquant sur le nom du groupe. Si une activité est sélectionnée, vous pouvez cliquer dessus pour annuler la sélection. Vous pouvez également utiliser la zone de recherche pour afficher les activités qui contiennent le mot clé que vous tapez.

  ![Cliquez sur le nom d’un groupe d’activités pour sélectionner toutes les activités](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Vous devez sélectionner **Afficher les résultats pour toutes les activités** dans la liste **Activités** pour afficher les entrées du journal d’audit de l’administrateur Exchange. Les événements dans ce journal d’audit affichent un nom de cmdlet (par exemple, **Set-Mailbox**) dans la colonne **Activité** des résultats. Pour plus d’informations, cliquez sur l’onglet **activités auditées** dans cette rubrique, puis sur **activités de l’administrateur Exchange**.

  De même, certaines activités d’audit n’ont pas d’élément correspondant dans la liste **Activités**. Si vous connaissez le nom de l’opération correspondant à ces activités, vous pouvez effectuer une recherche sur toutes les activités, puis filtrer les opérations après l’exportation des résultats de la recherche dans un fichier CSV.

- Cliquez sur **Effacer** pour effacer les critères de recherche actuels. La plage de dates reprend la valeur par défaut des sept derniers jours. Vous pouvez également cliquer sur **Effacer tout pour afficher les résultats correspondant à toutes les activités** pour annuler toutes les activités sélectionnées.

- Si 5 000 résultats sont détectés, vous pouvez partir du principe que plus de 5 000 événements correspondent aux critères de recherche. Vous pouvez affiner les critères de recherche et relancer la recherche pour renvoyer moins de résultats. Vous pouvez également exporter tous les résultats de recherche en sélectionnant **Exporter les résultats** > \> **Télécharger tous les résultats**.

### <a name="step-2-view-the-search-results"></a>Étape 2 : consulter les résultats de la recherche

Les résultats d’une recherche dans le journal d’audit apparaissent sous **Résultats** sur la page **Recherche dans le journal d’audit**. Comme indiqué précédemment, un maximum de 5 000 événements (les plus récents) peut s’afficher, par incréments de 150. Pour afficher davantage d’événements, vous pouvez utiliser la barre de défilement du volet **Résultats** ou appuyer sur **Maj+Fin** afin d’afficher les 150 événements suivants.

Les résultats contiennent les informations suivantes sur chaque événement renvoyé par la recherche :

- **Date :** Date et heure (à votre heure locale) auxquelles l’événement s’est produit.

- **Adresse IP :** Adresse IP de l’appareil utilisé lors de l’enregistrement de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.

   > [!NOTE]
  > Pour certains services, la valeur affichée dans ce champ peut être l'adresse IP d'une application sécurisée (par exemple, Office sur les applications Web) qui appelle le service au nom d'un utilisateur et non l'adresse IP de l'appareil utilisé par la personne ayant effectué l'activité. Par ailleurs, pour l’activité d’administration (ou l’activité effectuée par un compte système) pour les événements relatifs à Azure Active Directory, l’adresse IP n’est pas enregistrée et la valeur affichée dans ce champ est `null`.

- **Utilisateur** : Utilisateur (ou compte de service) qui a effectué l’action ayant déclenché l’événement.

- **Activité :** Activité effectuée par l’utilisateur. Cette valeur correspond aux activités que vous avez sélectionnées dans la liste déroulante **Activités**. Pour un événement figurant dans le journal d’audit de l’administrateur Exchange, la valeur dans cette colonne est une cmdlet Exchange.

- **Élément :** Objet qui a été créé ou modifié suite à l’activité correspondante. Par exemple, fichier consulté ou modifié, ou compte d’utilisateur mis à jour. Certaines activités n’ont pas de valeur dans cette colonne.

- **Détails :** Détails supplémentaires sur une activité. Là encore, toutes les activités n’ont pas de valeur.

> [!TIP]
> Cliquez sur un en-tête de colonne sous **Résultats** pour trier les résultats. Vous pouvez trier les résultats par ordre croissant ou décroissant. Cliquez sur l’en-tête **Date** pour trier les résultats du plus ancien au plus récent, ou du plus récent au plus ancien.

#### <a name="view-the-details-for-a-specific-event"></a>Afficher les détails d’un événement spécifique

Vous pouvez afficher davantage d’informations sur un événement en cliquant sur l’enregistrement d’événement dans la liste des résultats de recherche. La page du menu volant s’affiche contenant les propriétés détaillées de l’enregistrement d’événement. Les propriétés affichées dépendent du service dans lequel l’événement se produit. 

### <a name="step-3-export-the-search-results-to-a-file"></a>Étape 3 : exporter les résultats de la recherche dans un fichier

Vous pouvez exporter les résultats d’une recherche dans le journal d’audit dans un fichier de valeurs séparées par des virgules (.csv) sur votre ordinateur local. Vous pouvez ouvrir ce fichier dans Microsoft Excel et utiliser des fonctionnalités telles que la recherche, le tri, le filtrage et le fractionnement d’une colonne (dont les cellules contiennent plusieurs propriétés) en plusieurs colonnes.

1. Effectuez une recherche dans le journal d’audit, puis modifiez les critères de recherche jusqu’à obtenir les résultats souhaités.

2. Sur la page des résultats de la recherche, cliquez sur **Exporter** > **Télécharger tous les résultats**.

   Toutes les entrées du journal d'audit qui répondent aux critères de recherche sont exportées vers un fichier CSV. Les données brutes du journal d’audit sont enregistrées dans un fichier CSV. Des informations supplémentaires de l’entrée du journal d’audit sont incluses dans une colonne appelée **AuditData** dans le CSV.

     > [!IMPORTANT]
     > Vous pouvez télécharger un maximum de 50 000 entrées dans un fichier .csv à partir d’une seule recherche dans le journal d’audit. Si 50 000 résultats sont téléchargés dans le fichier .csv, vous pouvez partir du principe que plus de 50 000 événements remplissent les critères de recherche. Pour exporter davantage de résultats, essayez d’utiliser une plage de dates pour réduire le nombre d’entrées du journal d’audit. Vous devrez peut-être effectuer plusieurs recherches avec des plages de dates plus réduites pour exporter plus de 50 000 entrées.

3. Une fois le processus d'exportation terminé, un message s'affiche en haut de la fenêtre et vous invite à ouvrir le fichier CSV et à l'enregistrer sur votre ordinateur local. Vous pouvez également accéder au fichier CSV dans le dossier Téléchargements.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Informations supplémentaires sur l'exportation et l'affichage des résultats de recherche dans le journal d'audit

- Lorsque vous téléchargez tous les résultats de la recherche, le fichier CSV contient les colonnes **CreationDate**, **UserIds**, **Opérations** et **AuditData**. La colonne **AuditData** contient des informations supplémentaires sur chaque événement (semblables aux informations détaillées affichées sur la page du menu volant lorsque vous affichez les résultats de la recherche dans le Centre de conformité). Les données de cette colonne se composent d’un objet JSON qui contient plusieurs propriétés de l’enregistrement du journal d’audit. Chaque pair *property:value* dans l’objet JSON est séparée par une virgule. Vous pouvez utiliser l’outil transformation JSON de l’éditeur Power Query dans Excel pour fractionner la colonne **AuditData** en plusieurs colonnes de sorte que chaque propriété dans l’objet JSON ait sa propre colonne. Cela vous permettra d’utiliser une ou plusieurs de ces propriétés pour trier et filtrer les valeurs. Pour obtenir des instructions pas à pas à l’aide de l’éditeur Power Query pour transformer l’objet JSON, voir [exporter, configurer et afficher des enregistrements de journal d’audit](export-view-audit-log-records.md).

  Après avoir fractionné la colonne **AuditData**, vous pouvez filtrer sur la colonne **Opérations** pour afficher les propriétés détaillées pour un type d’activité spécifique.

- Lorsque vous téléchargez tous les résultats d’une requête de recherche qui contient les événements de différents services, la colonne **AuditData** du fichier .csv contient différentes propriétés selon le service dans lequel l’action a été effectuée. Par exemple, les entrées des journaux d’audit Exchange et Azure AD incluent une propriété nommée **ResultStatus** qui indique si l’action a réussi ou non. Cette propriété n’est pas incluse pour les événements dans SharePoint. De même, les événements SharePoint ont une propriété qui identifie l’URL de site pour les activités liées aux fichiers et dossiers. Pour modifier ce comportement, vous pouvez utiliser des recherches différentes pour exporter les résultats des activités d’un service.

  Pour consulter une description des propriétés répertoriées dans la colonne **AuditData** du fichier .csv lorsque vous téléchargez tous les résultats, et du service auquel s’applique chacune d’elles, voir [Propriétés détaillées dans le journal d’audit](detailed-properties-in-the-office-365-audit-log.md).

## <a name="audited-activities"></a>Activités auditées

Les tableaux de cette section décrivent les activités auditées dans Microsoft 365. Vous pouvez rechercher ces événements dans le journal d’audit dans le Centre de sécurité et conformité.

Ces tableaux regroupent des activités connexes ou les activités d’un service spécifique. Les tableaux incluent le nom convivial affiché dans la liste déroulante **Activités** et le nom de l’opération correspondante qui apparaît dans les informations détaillées d’un enregistrement d’audit et le fichier .csv lorsque vous exportez les résultats de recherche. Pour consulter des descriptions des informations détaillées, voir [Propriétés détaillées dans le journal d’audit](detailed-properties-in-the-office-365-audit-log.md).

Pour accéder à un tableau spécifique, cliquez sur l’un des liens suivants.

:::row:::
    :::column:::
        [Activités des fichiers et pages](#file-and-page-activities)
    :::column-end:::
    :::column:::
        [Activités des dossiers](#folder-activities)
    :::column-end:::
    :::column:::
        [Activités de liste SharePoint](#sharepoint-list-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités de demande d’accès et de partage](#sharing-and-access-request-activities)
    :::column-end:::
    :::column:::
        [Activités de synchronisation](#synchronization-activities)
    :::column-end:::
    :::column:::
        [Activités d’autorisations de site](#site-permissions-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités d’administration des sites](#site-administration-activities)
    :::column-end:::
    :::column:::
        [Activités de la boîte aux lettres Exchange](#exchange-mailbox-activities)
    :::column-end:::
    :::column:::
        [Activités d’administration des utilisateurs](#user-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités d’administration des groupes Azure AD](#azure-ad-group-administration-activities)
    :::column-end:::
    :::column:::
        [Activités d’administration des applications](#application-administration-activities)
    :::column-end:::
    :::column:::
        [Activités d’administration des rôles](#role-administration-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités d’administration de l’annuaire](#directory-administration-activities)
    :::column-end:::
    :::column:::
        [Activités de découverte électronique](#ediscovery-activities)
    :::column-end:::
    :::column:::
        [Activités avancées eDiscovery](#advanced-ediscovery-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités dans Power BI](#power-bi-activities)
    :::column-end:::
    :::column:::
        [Microsoft Workplace Analytics](#workplace-analytics-activities)
    :::column-end:::
    :::column:::
        [Activités dans Microsoft Teams](#microsoft-teams-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités Santé Microsoft Teams](#microsoft-teams-healthcare-activities)
    :::column-end:::
    :::column:::
        [Activités Shifts dans Microsoft Teams](#microsoft-teams-shifts-activities)
    :::column-end:::
    :::column:::
        [Activités dans Yammer](#yammer-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités Microsoft Power Automate](#microsoft-power-automate-activities)
    :::column-end:::
    :::column:::
        [Activités Microsoft Power Apps](#microsoft-power-apps-activities)
    :::column-end:::
    :::column:::
        [Activités de Microsoft Stream](#microsoft-stream-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités de l’Explorateur de contenu](#content-explorer-activities)
    :::column-end:::
    :::column:::
        [Activités de mise en quarantaine](#quarantine-activities)
    :::column-end:::
    :::column:::
        [Activités Microsoft Forms](#microsoft-forms-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités des étiquettes de confidentialité](#sensitivity-label-activities)
    :::column-end:::
    :::column:::
        [Stratégie de rétention et activités d’étiquette de rétention](#retention-policy-and-retention-label-activities)
    :::column-end:::
    :::column:::
        [Activités de récapitulatif des tâches par courrier électronique](#briefing-email-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités myAnalytics](#myanalytics-activities)
    :::column-end:::
    :::column:::
        [Activités des obstacles aux informations](#information-barriers-activities)
    :::column-end:::
    :::column:::
        [Activités de révision avant destruction](#disposition-review-activities)
    :::column-end:::
:::row-end:::

:::row:::
    :::column:::
        [Activités de conformité des communications](#communication-compliance-activities)
    :::column-end:::
    :::column:::
        [Activités de rapport](#report-activities)
    :::column-end:::
    :::column:::
        [Activités administrateur Exchange](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Activités des fichiers et pages

Le tableau suivant décrit les activités des fichiers et pages dans SharePoint Online et OneDrive Entreprise.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Fichier consulté|FileAccessed|Le compte d’utilisateur ou système consulte un fichier.|
|(aucun)|FileAccessedExtended|Cet événement est lié à l’activité « Fichier consulté » (FileAccessed). Un événement FileAccessedExtended est consigné lorsque la même personne accède à un fichier pendant une période prolongée (jusqu'à 3 heures). <br/><br/> L’objectif de la journalisation des événements FileAccessedExtended consiste à réduire le nombre d’événements FileAccessed enregistrés lorsqu’un fichier est consulté de manière continue. Cela permet de réduire le bruit généré par l’enregistrement de plusieurs événements FileAccessed pour ce qui est en fait l’activité d’un seul et même utilisateur et vous permettre de vous concentrer sur l’événement FileAccessed initial (plus important).|
|Étiquette de rétention modifiée pour un fichier|ComplianceSettingChanged|Une étiquette de rétention a été appliquée à un document ou supprimée de celui-ci. Cet événement est déclenché lorsqu’une étiquette de rétention est appliquée manuellement ou automatiquement à un message.|
|État de l’enregistrement modifié sur verrouillé|LockRecord|État de l’enregistrement d’une étiquette de rétention qui classifie un document en tant qu’enregistrement verrouillé. Cela signifie que le document ne peut pas être modifié ou supprimé. Seuls les utilisateurs ayant au moins l’autorisation de collaborateur pour un site peuvent changer le statut d’enregistrement d’un document.|
|Modifier l’état de l’enregistrement sur verrouillé|UnlockRecord|État de l’enregistrement d’une étiquette de rétention qui classifie un document en tant qu’enregistrement déverrouillé. Cela signifie que le document peut être modifié ou supprimé. Seuls les utilisateurs ayant au moins l’autorisation de collaborateur pour un site peuvent changer le statut d’enregistrement d’un document.|
|Fichier archivé|FileCheckedIn|Un utilisateur archive un document qu’il a extrait d’une bibliothèque de documents.|
|Fichier extrait|FileCheckedOut|Un utilisateur extrait un document d’une bibliothèque de documents. Les utilisateurs peuvent extraire et modifier les documents partagés avec eux.|
|Fichier copié|FileCopied|Un utilisateur copie un document à partir d’un site. Le fichier copié peut être enregistré dans un autre dossier sur le site.|
|Fichier supprimé|FileDeleted|Un utilisateur supprime un document d’un site.|
|Fichier supprimé de la Corbeille|FileDeletedFirstStageRecycleBin|Un utilisateur supprime un fichier de la Corbeille d’un site.|
|Fichier supprimé de la Corbeille second niveau|FileDeletedSecondStageRecycleBin|Un utilisateur supprime un fichier de la Corbeille second niveau d’un site.|
|Fichier étant identifié comme un enregistrement supprimé|RecordDelete|Un document ou e-mail identifié comme étant un enregistrement a été supprimé. Un élément est considéré comme un enregistrement lorsqu’une étiquette de rétention qui identifie les éléments comme étant un enregistrement est appliquée au contenu.|
|Détection de correspondance incorrecte des documents|DocumentSensitivityMismatchDetected|Un utilisateur télécharge un document sur un site protégé par une étiquette de confidentialité et le document comporte une étiquette de confidentialité plus élevée que celle du site. Par exemple, un document marqué Confidentiel est chargé sur un site intitulé Général. <br/><br/> Cet événement ne se déclenche pas si le document comprend une étiquette de confidentialité de priorité inférieure à celle appliquée sur le site. Par exemple, un document marqué Général est téléchargé sur un site intitulé Confidentiel. Pour plus d’informations sur la priorité d'étiquettes de confidentialité, consultez la [Priorité d’étiquette (importance de l'ordre)](sensitivity-labels.md#label-priority-order-matters).|
|Détection d’un programme malveillant dans le fichier|FileMalwareDetected|Le moteur antivirus de SharePoint détecte un programme malveillant dans un fichier.|
|Extraction de fichier ignorée|FileCheckOutDiscarded|Un utilisateur ignore (ou annule) un fichier extrait. Les modifications qu’il a apportées au fichier le temps de son extraction sont ignorées et ne sont pas enregistrées dans la version du document dans la bibliothèque de documents.|
|Fichier téléchargé|FileDownloaded|Un utilisateur télécharge un document à partir d’un site.|
|Fichier modifié|FileModified|Le compte d’utilisateur ou système modifie le contenu ou les propriétés d’un document sur un site.|
|(aucun)|FileModifiedExtended|Cet événement est lié à l’activité « Fichier modifié » (FileModified). Un événement FileModifiedExtended est consigné lorsque la même personne modifie un fichier pendant une période prolongée (jusqu'à 3 heures). <br/><br/> L’objectif de la journalisation des événements FileModifiedExtended consiste à réduire le nombre d’événements FileModified enregistrés lorsqu’un fichier est modifié de manière continue. Cela permet de réduire le bruit généré par l’enregistrement de plusieurs événements FileModified pour ce qui est en fait l’activité d’un seul et même utilisateur et vous permettre de vous concentrer sur l’événement FileModified initial (plus important).|
|Fichier déplacé|FileMoved|Un utilisateur déplace un document de son emplacement actuel sur un site vers un nouvel emplacement.|
|(aucun)|FilePreviewed|Un utilisateur affiche l’aperçu de fichiers sur un site SharePoint ou OneDrive Entreprise. Ces événements se produisent généralement dans des volumes élevés basés sur une activité unique, comme l’affichage d’une galerie d’images.|
|Requête de recherche effectuée|SearchQueryPerformed|Un compte d’utilisateur ou système effectue une recherche dans SharePoint ou OneDrive Entreprise. Certains scénarios courants dans lesquels un compte de service effectue une requête de recherche incluent l’application d’une stratégie de rétention et de conservation eDiscovery aux sites et comptes OneDrive, et lors de l'application automatique d'étiquettes de rétention ou de confidentialité au contenu du site.|
|Recyclé un fichier | Fichier recyclé | L'utilisateur déplace un fichier dans la corbeille SharePoint. |
|Recyclé un dossier | DossierRecyclé | L'utilisateur déplace un dossier dans la corbeille SharePoint. |
|Recyclage de toutes les versions mineures du fichier|FileVersionsAllMinorsRecycled|L’utilisateur supprime toutes les versions mineures de l’historique des versions d’un fichier. Les versions supprimées sont déplacées vers la Corbeille du site.|
|Recyclage de toutes les versions du fichier|FileVersionsAllRecycled|L’utilisateur supprime toutes les versions de l’historique des versions d’un fichier. Les versions supprimées sont déplacées vers la Corbeille du site.|
|Recyclage d’une version du fichier|FileVersionRecycled|L’utilisateur supprime une version de l’historique des versions d’un fichier. La version supprimée est déplacée vers la Corbeille du site.|
|Fichier renommé|FileRenamed|Un utilisateur renomme un document sur un site.|
|Fichier restauré|FileRestored|Un utilisateur restaure un document à partir de la Corbeille d’un site.|
|Fichier téléchargé|FileUploaded|Un utilisateur charge un document vers un dossier sur un site.|
|Page affichée|PageViewed|Un utilisateur affiche une page sur un site. Ceci n’inclut pas l’utilisation d’un navigateur web pour afficher les fichiers dans une bibliothèque de documents.|
|(aucun)|PageViewedExtended|Cet événement est lié à l’activité « Page affichée » (PageViewed). Un événement PageViewedExtended est consigné lorsque la même personne affiche une page web pendant une période prolongée (jusqu'à 3 heures). <br/><br/> L’objectif de la journalisation des événements PageViewedExtended consiste à réduire le nombre d’événements PageViewed enregistrés lorsqu’une page est affichée de manière continue. Cela permet de réduire le bruit généré par l’enregistrement de plusieurs événements PageViewed pour ce qui est en fait l’activité d’un seul et même utilisateur et vous permettre de vous concentrer sur l’événement PageViewed initial (plus important).|
|Affichage signalé par le client|ClientViewSignaled|Le client d’un utilisateur (comme un site web ou une application mobile) signale que la page indiquée a été consultée par l’utilisateur. Cette activité est souvent journalisée à la suite d’un événement PagePrefetched pour une page. <br/><br/>**Remarque**: les événements ClientViewSignaled étant signalés par le client, plutôt que le serveur, il est possible que l’événement ne soit pas consigné par le serveur et, par conséquent, qu’il n’apparaisse pas dans le journal d’audit. Il est également possible que les informations dans l’enregistrement d’audit ne soient pas dignes de confiance. Toutefois, comme l’identité de l’utilisateur est validée par le jeton utilisé pour créer le signal, l’identité de l’utilisateur répertoriée dans l’enregistrement d’audit correspondant est exacte. |
|(aucun)|PagePrefetched|Le client d’un utilisateur (comme un site web ou une application mobile) demande la page indiquée afin de vous aider à améliorer les performances lorsque l’utilisateur y accède. Cet événement est enregistré pour indiquer que le contenu de la page a été remis au client de l’utilisateur. Cet événement n’indique pas si l’utilisateur a accédé à la page. <br/><br/> Lorsque le contenu de la page est affiché par le client (conformément à la requête de l’utilisateur), un événement ClientViewSignaled est généré. Tous les clients ne prennent pas en charge l’indication d’une pré-récupération ; par conséquent, certaines activités préalablement récupérées peuvent être enregistrées en tant qu’événements PageViewed.|
||||

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>Forum aux questions sur les événements FileAccessed et FilePreviewed

**Des activités non-utilisateur peuvent-elles déclencher des enregistrements d’audit FilePreviewed contenant un agent utilisateur tel que « OneDriveMpc-Transform_Thumbnail » ?**

Nous ne connaissons pas de situations dans lesquelles les actions non-utilisateur génèrent des événements de ce type. Les actions d’utilisateur telles que l’ouverture d’une carte de profil utilisateur (en cliquant sur son nom ou son adresse e-mail dans un message dans Outlook sur le web) génèrent des événements similaires.

**Les appels à OneDriveMpc-Transform_Thumbnail sont-ils toujours déclenchés intentionnellement par l’utilisateur ?**

Non. Mais des événements similaires peuvent être enregistrés suite à une récupération préalable du navigateur.

**Si un événement FilePreviewed provenant d’une adresse IP enregistrée par Microsoft s’affiche, cela signifie-t-il que l’aperçu s’affiche sur l’écran de l’appareil de l’utilisateur ?**

Non. L’événement a peut-être été consigné suite à la récupération préalable du navigateur.

**Y a-t-il des scénarios dans lesquels un utilisateur consultant un aperçu d’un document génère des événements FileAccessed ?**

Les événements FilePreviewed et FileAccessed indiquent que l’appel d’un utilisateur a provoqué une lecture du fichier (ou une lecture d’un rendu miniature de celui-ci). Bien que ces événements soient conçus pour s’aligner sur les intentions d’aperçu ou d’accès, la distinction entre les événements ne constitue pas une garantie de l’intention de l’utilisateur.

#### <a name="the-appsharepoint-user-in-audit-records"></a>L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit

Dans les enregistrements d’audit relatives à certaines activités de fichier (et d’autres activités liées à SharePoint), vous pouvez remarquer que l’utilisateur ayant effectué l’activité (identifié dans les champs Utilisateur et UserId) est app@sharepoint. Cela indique que l' « Utilisateur » ayant effectué l’activité était une application. Dans ce cas, l’application a obtenu des autorisations dans SharePoint pour effectuer des actions à l’échelle de l’organisation (par exemple, effectuer une recherche de site SharePoint ou de compte OneDrive) au nom d’un utilisateur, d’un administrateur ou d’un service. Ce processus d’octroi d’autorisations à une application est appelé accès par *Application SharePoint uniquement*. Cela signifie que l’authentification présentée à SharePoint pour effectuer une action a été faite par une application au lieu d’un utilisateur. C’est la raison pour laquelle l’utilisateur app@sharepoint est trouvé dans certains enregistrements d’audit. Pour obtenir plus d'informations, consultez [Accorder l’accès en utilisant l'application SharePoint uniquement](/sharepoint/dev/solution-guidance/security-apponly-azureacs).

Par exemple, app@sharepoint est souvent considéré comme l’utilisateur des événements « Requête de recherche effectuée » et « Fichier consulté ». La raison est qu’une application de votre organisation avec accès Application SharePoint uniquement effectue des requêtes de recherche et accède à des fichiers lors de l’application de stratégies de rétention à des comptes OneDrive ainsi qu'à des sites.

Voici d'autres scénarios dans lesquels app@sharepoint peut être identifié, dans un enregistrement d'audit, en tant qu'utilisateur ayant effectué une activité :

- Groupes Microsoft 365. Lorsqu’un utilisateur ou un administrateur crée un nouveau groupe, des enregistrements d’audit sont générés pour établir une collection de sites, mettre à jour des listes et ajouter des membres à un groupe SharePoint. Ces tâches exécutent une application pour le compte de l’utilisateur qui a créé le groupe.

- Microsoft Teams. À l'instar des groupes Microsoft 365, les enregistrements d'audit sont générés pour créer une collection de sites, mettre à jour des listes et ajouter des membres à un groupe SharePoint lorsqu'une équipe est créée.

- Fonctionnalités de conformité. Lorsqu'un administrateur implémente des fonctionnalités de conformité, comme des stratégies de rétention, des conservations eDiscovery et des étiquettes de confidentialité appliquées automatiquement.

Dans ces scénarios ainsi que d’autres, vous remarquerez également que plusieurs enregistrements d’audit avec app@sharepoint comme utilisateur spécifié ont été créés dans un bref laps de temps, souvent à quelques secondes les uns des autres. Cela indique également qu’ils ont probablement été déclenchés par un tâche initiée par le même utilisateur. En outre, les champs ApplicationDisplayName et EventData de l’enregistrement d’audit peuvent vous aider à identifier le scénario ou l'application ayant déclenché l'événement.

### <a name="folder-activities"></a>Activités des dossiers

Le tableau suivant décrit les activités des fichiers dans SharePoint Online et OneDrive Entreprise. Comme expliqué précédemment, les enregistrements d’audit pour certaines activités SharePoint indiquent que l'utilisateur app@sharepoint a effectué l’activité de la part de l’utilisateur ou de l’administrateur ayant lancé l’action. Pour obtenir plus d'informations, consultez [L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Dossier copié|FolderCopied|Un utilisateur copie un dossier à partir d’un site vers un autre emplacement dans SharePoint ou OneDrive Entreprise.|
|Dossier créé|FolderCreated|Un utilisateur crée un dossier sur un site.|
|Dossier supprimé|FolderDeleted|Un utilisateur supprime un dossier d’un site.|
|Dossier supprimé de la Corbeille|FolderDeletedFirstStageRecycleBin|Un utilisateur supprime un dossier de la Corbeille sur un site.|
|Dossier supprimé de la Corbeille second niveau|FolderDeletedSecondStageRecycleBin|Un utilisateur supprime un dossier de la Corbeille second niveau sur un site.|
|Dossier modifié|FolderModified|Un utilisateur modifie un dossier sur un site. Cela inclut la modification des métadonnées du dossier (par exemple, modification des balises et propriétés).|
|Dossier déplacé|FolderMoved|Un utilisateur déplace un dossier vers un autre emplacement sur un site.|
|Dossier renommé|FolderRenamed|Un utilisateur renomme un dossier sur un site.|
|Dossier restauré|FolderRestored|Un utilisateur restaure un dossier supprimé de la Corbeille sur un site.|
||||

### <a name="sharepoint-list-activities"></a>Activités de liste SharePoint

Le tableau suivant décrit les activités liées à la façon dont les utilisateurs interagissent avec les listes et les éléments de liste dans SharePoint Online. Comme expliqué précédemment, les enregistrements d’audit pour certaines activités SharePoint indiquent que l'utilisateur app@sharepoint a effectué l’activité de la part de l’utilisateur ou de l’administrateur ayant lancé l’action. Pour obtenir plus d'informations, consultez [L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Liste créée|ListCreated|Un utilisateur a créé une liste SharePoint.|
|Colonne de liste créée|ListColumnCreated|Un utilisateur a créé une colonne de liste SharePoint. Une colonne de liste est une colonne jointe à une ou plusieurs listes SharePoint.|
|Type de contenu de liste créé|ListContentTypeCreated|Un utilisateur a créé un type de contenu de liste. Un type de contenu de liste est un type de contenu attaché à une ou plusieurs listes SharePoint.|
|Élément de liste créé|ListItemCreated|Un utilisateur a créé un élément dans une liste SharePoint existante.|
|Colonne de site créée|SiteColumnCreated|Un utilisateur a créé une colonne de site SharePoint. Une colonne de site est une colonne qui n’est pas jointe à une liste. Une colonne de site est également une structure de métadonnées pouvant être utilisée par n’importe quelle liste d’un site Web donné.|
|Type de contenu de site créé|ContentType du site créé|Un utilisateur a créé un type de contenu de site. Un type de contenu de site est un type de contenu attaché au site parent.|
|Liste supprimée|ListDeleted|Un utilisateur a supprimé une liste SharePoint.|
|Colonne de liste supprimée|Colonne de liste supprimée|Un utilisateur a supprimé une colonne de liste SharePoint.|
|Type de contenu de liste supprimé|ListContentTypeDeleted|Un utilisateur a supprimé un type de contenu de liste.|
|Élément de liste supprimé|Élément de liste supprimé|Un utilisateur a supprimé un élément de liste SharePoint.|
|Colonne de site supprimée|SiteColumnDeleted|Un utilisateur a supprimé une colonne de site SharePoint.|
|Type de contenu de site supprimé|SiteContentTypeDeleted|Un utilisateur a supprimé un type de contenu de site.|
|Élément de liste recyclé|ListItemRecycled|Un utilisateur a déplacé un élément de liste SharePoint dans la corbeille.|
|Liste restaurée|ListRestored|Un utilisateur a restauré un élément de liste SharePoint depuis la corbeille.|
|Élément de liste restauré|ListItemRestored|Un utilisateur a restauré un élément de liste SharePoint depuis la corbeille.|
|Liste mise à jour|ListUpdated|Un utilisateur a mis à jour une liste SharePoint en modifiant une ou plusieurs propriétés.|
|Colonne de liste mise à jour|ListColumnUpdated|Un utilisateur a mis à jour une colonne de liste SharePoint en modifiant une ou plusieurs propriétés.|
|Type de contenu de liste mis à jour|ListContentTypeUpdated|Un utilisateur a mis à jour un type de contenu de liste en modifiant une ou plusieurs propriétés.|
|Élément de liste mis à jour|ListItemUpdated|Un utilisateur a mis à jour un élément de liste SharePoint en modifiant une ou plusieurs propriétés.|
|Colonne de site mise à jour|SiteColumnUpdated|Un utilisateur a mis à jour une colonne de site SharePoint en modifiant une ou plusieurs propriétés.|
|Type de contenu de site mis à jour|SiteContentTypeUpdated|Un utilisateur a mis à jour un type de contenu de site en modifiant une ou plusieurs propriétés.|
|Élément de liste consulté|ListItemViewed|Un utilisateur a affiché un élément de liste Microsoft Office SharePoint Online.|
||||

### <a name="sharing-and-access-request-activities"></a>Activités de demande d’accès et de partage

Le tableau suivant décrit les activités de demande d’accès et de partage d’utilisateurs dans SharePoint Online et OneDrive Entreprise. Pour les événements de partage, la colonne **Détails** sous **Résultats** identifie le nom de l’utilisateur ou du groupe avec lequel l’élément était partagé et si cet utilisateur ou groupe est un membre de votre organisation ou un invité. Pour plus d’informations, voir [Utiliser l’audit du partage dans le journal d’audit](use-sharing-auditing.md).

> [!NOTE]
> Les utilisateurs peuvent être des *membres* ou des *invités* en fonction de la propriété UserType de l’objet utilisateur. Un membre est généralement un employé, tandis qu’un invité est généralement un collaborateur externe à votre organisation. Lorsqu’un utilisateur accepte une invitation de partage (et ne fait pas déjà partie de votre organisation), un compte invité est créé pour lui dans l’annuaire de votre organisation. Dès lors que l’utilisateur invité a un compte dans votre annuaire, des ressources peuvent être partagées directement avec lui (sans invitation).

|Nom convivial|Opération|Description|
|:-----|:-----|:-----|
|Ajout d’un niveau d’autorisation à la collection de sites|PermissionLevelAdded|Un niveau d’autorisation a été ajouté à une collection de sites.|
|Demande d’accès acceptée|AccessRequestAccepted|Une demande d’accès à un site, un dossier ou un document a été acceptée et l’utilisateur à l’origine de la demande s’est vu octroyé l’accès.|
|Invitation de partage acceptée|SharingInvitationAccepted|L’utilisateur (membre ou invité) a accepté une invitation de partage et s’est vu octroyer l’accès à une ressource. Cet événement inclut des informations sur l’utilisateur invité et l’adresse de messagerie utilisée pour accepter l’invitation (ils peuvent être différents). Cette activité est souvent accompagnée d’un deuxième événement qui décrit la manière dont l’utilisateur s’est vu octroyer l’accès à la ressource (par exemple, en ajoutant l’utilisateur à un groupe ayant accès à la ressource).|
|Invitation de partage bloquée|SharingInvitationBlocked|Une invitation de partage envoyée par un utilisateur de votre organisation est bloquée par une stratégie de partage externe qui autorise ou refuse le partage externe en fonction du domaine de l’utilisateur cible. Dans ce cas, l’invitation de partage a été bloquée car : <br/> Le domaine de l’utilisateur cible n’est pas inclus dans la liste des domaines autorisés. <br/> Ou <br/> Le domaine de l’utilisateur cible est inclus dans la liste des domaines bloqués. <br/> Pour plus d’informations sur l’autorisation ou le blocage du partage externe en fonction des domaines, voir [Restreindre le partage des domaines dans SharePoint Online et OneDrive Entreprise](/sharepoint/restricted-domains-sharing).|
|Demande d’accès créée|AccessRequestCreated|Un utilisateur demande l’accès à un site, un dossier ou un document auquel il n’est pas autorisé à accéder.|
|Création d’un lien d’entreprise partageable |CompanyLinkCreated|L’utilisateur a créé un lien à l’échelle de l’entreprise vers une ressource. Les liens à l’échelle de l’entreprise ne peuvent être utilisés que par les membres de votre organisation. Ils ne peuvent pas être utilisés par les invités.|
|Création d’un lien anonyme|AnonymousLinkCreated|L’utilisateur a créé un lien anonyme vers une ressource. Toute personne disposant de ce lien peut accéder à la ressource sans être authentifiée.|
|Lien sécurisé créé|SecureLinkCreated|Un lien de partage sécurisé a été créé sur cet élément.|
|Invitation de partage créée|SharingInvitationCreated|Un utilisateur a partagé une ressource dans SharePoint Online ou OneDrive Entreprise avec un utilisateur qui ne figure pas dans l’annuaire de votre organisation.|
|Lien sécurisé supprimé|SecureLinkDeleted|Un lien de partage sécurisé a été supprimé.|
|Demande d’accès refusée |AccessRequestDenied|Une demande d’accès à un site, un dossier ou un document a été refusée.|
|Suppression d’un lien d’entreprise partageable|CompanyLinkRemoved|L’utilisateur a supprimé un lien à l’échelle de l’entreprise vers une ressource. Le lien ne peut plus être utilisé pour accéder à la ressource.|
|Suppression d’un lien anonyme|AnonymousLinkRemoved|L’utilisateur a supprimé un lien anonyme vers une ressource. Le lien ne peut plus être utilisé pour accéder à la ressource.|
|Fichier, dossier ou site partagé|SharingSet|L’utilisateur (membre ou invité) a partagé un fichier, un dossier ou un site dans SharePoint ou OneDrive Entreprise avec un utilisateur dans l’annuaire de votre organisation. La valeur dans la colonne **Détails** pour cette activité identifie le nom de l’utilisateur avec lequel la ressource a été partagée et si cet utilisateur est un membre ou un invité. <br/><br/> Cette activité est souvent accompagnée d'un deuxième événement qui décrit comment l'utilisateur a obtenu l'accès à la ressource. Par exemple, l'ajout de l'utilisateur à un groupe qui a accès à la ressource.|
|Demande d’accès mise à jour|AccessRequestUpdated|Une demande d’accès à un élément a été mise à jour.|
|Mise à jour d’un lien anonyme |AnonymousLinkUpdated|L’utilisateur a mis à jour un lien anonyme vers une ressource. Le champ mise à jour est inclus dans la propriété EventData lorsque vous exportez les résultats de recherche.|
|Invitation de partage mise à jour|SharingInvitationUpdated|Une invitation de partage externe a été mise à jour.|
|Utilisation d’un lien anonyme |AnonymousLinkUsed|Un utilisateur anonyme a consulté une ressource à l’aide d’un lien anonyme. L’identité de l’utilisateur peut être inconnue, mais vous pouvez obtenir d’autres informations telles que l’adresse IP de l’utilisateur.|
|Fichier, dossier ou site non partagé|SharingRevoked|Un utilisateur (membre ou invité) a cessé de partager un fichier, un dossier ou un site précédemment partagé avec un autre utilisateur.|
|Utilisation d’un lien d’entreprise partageable|CompanyLinkUsed|Un utilisateur a consulté une ressource à l’aide d’un lien à l’échelle de l’entreprise.|
|Lien sécurisé utilisé|SecureLinkUsed|Un utilisateur a utilisé un lien sécurisé.|
|Utilisateur ajouté à un lien sécurisé.|AddedToSecureLink|Un utilisateur a été ajouté à la liste des entités pouvant utiliser un lien de partage sécurisé.|
|Utilisateur supprimé d’un lien sécurisé.|RemovedFromSecureLink|Un utilisateur a été supprimé de la liste des entités pouvant utiliser un lien de partage sécurisé.|
|Invitation de partage retirée|SharingInvitationRevoked|Un utilisateur a retiré une invitation de partage à une ressource. |
||||

### <a name="synchronization-activities"></a>Activités de synchronisation

Le tableau suivant décrit les activités de synchronisation dans SharePoint Online et OneDrive Entreprise.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Ordinateur autorisé à synchroniser des fichiers|ManagedSyncClientAllowed|Un utilisateur a réussi à établir une relation de synchronisation avec un site. La relation de synchronisation est établie, car l'ordinateur de l'utilisateur est membre d'un domaine qui a été ajouté à la liste des domaines (*liste des destinataires approuvés*) pouvant accéder aux bibliothèques de documents dans votre organisation. <br/><br/> Pour plus d’informations sur cette fonctionnalité, reportez-vous à l’article [Utilisation des cmdlet Windows PowerShell pour activer la synchronisation de OneDrive pour les domaines figurant dans la liste des destinataires approuvés](/powershell/module/sharepoint-online/).|
|Ordinateur non autorisé à synchroniser des fichiers|UnmanagedSyncClientBlocked|L'utilisateur essaie d'établir une relation de synchronisation avec un site à partir d'un ordinateur qui n'est pas membre du domaine de votre organisation ou qui est membre d'un domaine qui n'a pas été ajouté à la liste des domaines (appelée *liste des destinataires approuvés*) qui peuvent accéder aux bibliothèques de documents de votre organisation. La relation de synchronisation n'est pas autorisée et l'ordinateur de l'utilisateur ne peut pas synchroniser, télécharger ou charger des fichiers sur une bibliothèque de documents.<br/><br/> Pour plus d’informations sur cette fonctionnalité, reportez-vous à l’article [Utilisation des cmdlet Windows PowerShell pour activer la synchronisation de OneDrive pour les domaines figurant dans la liste des destinataires approuvés](/powershell/module/sharepoint-online/).|
|Fichiers téléchargés sur l’ordinateur|FileSyncDownloadedFull|L’utilisateur télécharge un fichier sur son ordinateur à partir d’une bibliothèque de documents SharePoint ou de OneDrive Entreprise à l’aide de l’application de synchronisation OneDrive (OneDrive.exe).|
|Modifications du fichier téléchargées sur l’ordinateur|FileSyncDownloadedPartial|Cet événement a été déprécié avec l’ancienne application de synchronisation OneDrive Entreprise (Groove.exe).|
|Fichiers téléchargés dans la bibliothèque de documents|FileSyncUploadedFull|Un utilisateur charge un nouveau fichier ou les modifications apportées à un fichier dans SharePoint bibliothèque de documents ou de OneDrive Entreprise à l’aide de l’application de synchronisation OneDrive (OneDrive.exe).|
|Modifications du fichier téléchargées dans la bibliothèque de documents|FileSyncUploadedPartial|Cet événement a été déprécié avec l’ancienne application de synchronisation OneDrive Entreprise (Groove.exe).|
||||

### <a name="site-permissions-activities"></a>Activités d’autorisations de site

Le tableau suivant répertorie les événements liés à l’attribution d’autorisations dans SharePoint et l’utilisation des groupes pour accorder (et révoquer) l’accès aux sites. Comme expliqué précédemment, les enregistrements d’audit pour certaines activités SharePoint indiquent que l'utilisateur app@sharepoint a effectué l’activité de la part de l’utilisateur ou de l’administrateur ayant lancé l’action. Pour obtenir plus d'informations, consultez [L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Administrateur de collection de site ajouté|SiteCollectionAdminAdded|L’administrateur de collection de sites ou le propriétaire ajoute une personne en tant qu’administrateur de collection de sites pour un site. Les administrateurs de collection de sites disposent du niveau d’autorisation Contrôle total sur la collection de sites et tous les sous-sites. Cette activité est également enregistrée lorsqu’un administrateur se donne accès au compte OneDrive d’un utilisateur (en modifiant le profil utilisateur dans le Centre d’administration SharePoint ou à l’aide du [Centre d’administration Microsoft 365](/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data)).|
|Utilisateur ou groupe ajouté au groupe SharePoint|AddedToGroup|L’utilisateur a ajouté un membre ou un invité à un groupe SharePoint. Il s’agit peut-être d’une action intentionnelle ou du résultat d’une autre activité (par exemple, événement de partage).|
|Fin de l’héritage des niveaux d’autorisation|PermissionLevelsInheritanceBroken|Un élément a été modifié afin qu’il n’hérite plus des niveaux d’autorisation de son parent.|
|Fin de l’héritage de partage|SharingInheritanceBroken|Un élément a été modifié afin qu’il n’hérite plus des autorisations de partage de son parent.|
|Groupe créé|GroupAdded|L'administrateur ou le propriétaire du site crée un groupe pour un site ou effectue une tâche qui entraîne la création d'un groupe. Par exemple, la première fois qu'un utilisateur crée un lien pour partager un fichier, un groupe système est ajouté au site OneDrive Entreprise de l'utilisateur. Cet événement peut également venir d'un utilisateur créant un lien avec des autorisations de modification vers un fichier partagé.|
|Groupe supprimé|GroupRemoved|Un utilisateur supprime un groupe d’un site.|
|Paramètre de demande d’accès modifié|WebRequestAccessModified|Les paramètres de demande d’accès ont été modifiés sur un site.|
|Paramètre «les membres peuvent partagés» modifié|WebMembersCanShareModified|Le paramètre **les membres peuvent partager** a été modifié sur un site.|
|Modification du niveau d’autorisation sur une collection de sites|PermissionLevelModified|Un niveau d’autorisation a été modifié sur une collection de sites.|
|Autorisations de site modifiées|SitePermissionsModified|L'administrateur ou le propriétaire du site (ou le compte système) modifie le niveau d'autorisation attribué à un groupe sur un site. Cette activité est également enregistrée si toutes les autorisations sont supprimées d'un groupe.<br/><br/> **Remarque**: cette opération est déconseillée dans SharePoint Online. Pour rechercher des événements connexes, vous pouvez rechercher d’autres activités liées à une autorisation, telles que **Administrateur de collection de sites ajoutée**, **Utilisateur ou groupe ajouté à un groupe SharePoint**, **Utilisateur autorisé à créer des groupes**, **Groupe créé** et **Groupe supprimé**.|
|Suppression d’un niveau d’autorisation dans une collection de sites|PermissionLevelRemoved|Un niveau d’autorisation a été supprimé d’une collection de sites.|
|Administrateur de collection de site supprimé|SiteCollectionAdminRemoved|L’administrateur de collection de sites ou le propriétaire supprime une personne en tant qu’administrateur de collection de sites pour un site. Cette activité est également enregistrée lorsqu’un administrateur se supprime de la liste des administrateurs de collections de sites pour le compte OneDrive d’un utilisateur (en modifiant le profil utilisateur dans le centre d’administration SharePoint).  Pour renvoyer cette activité dans les résultats de la recherche dans le journal d’audit, vous devez rechercher toutes les activités.|
|Utilisateur ou groupe supprimé au groupe SharePoint|RemovedFromGroup|L’utilisateur a supprimé un membre ou un invité d’un groupe SharePoint. Il s’agit peut-être d’une action intentionnelle ou du résultat d’une autre activité (par exemple, événement d’annulation de partage).|
|Autorisations d’administrateur de site demandées|SiteAdminChangeRequest|Un utilisateur demande à être ajouté en tant qu'administrateur de collection de sites pour une collection de sites. Les administrateurs de collection de sites disposent d'autorisations de contrôle total pour la collection de sites et tous les sous-sites.|
|Restauration de l’héritage de partage|SharingInheritanceReset|Une modification a été apportée afin qu’un élément hérite des autorisations de partage de son parent.|
|Groupe mis à jour|GroupUpdated|Un administrateur ou propriétaire de site modifie les paramètres d'un groupe pour un site. Cela peut inclure la modification du nom du groupe, des autorisations d'affichage ou de modification d'appartenance au groupe, et du mode de gestion des demandes d'appartenance.|
||||

### <a name="site-administration-activities"></a>Activités d’administration des sites

Le tableau suivant répertorie les événements qui résultent de tâches d’administration de site dans SharePoint Online. Comme expliqué précédemment, les enregistrements d’audit pour certaines activités SharePoint indiquent que l'utilisateur app@sharepoint a effectué l’activité de la part de l’utilisateur ou de l’administrateur ayant lancé l’action. Pour obtenir plus d'informations, consultez [L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Ajout de l’emplacement de données autorisé|AllowedDataLocationAdded|Un administrateur SharePoint ou général a ajouté un emplacement de données autorisé dans un environnement à plusieurs emplacements géographiques.|
|Agent utilisateur exempté ajouté|ExemptUserAgentSet|Un administrateur SharePoint ou général a ajouté un agent utilisateur à la liste des agents utilisateurs exemptés dans le centre d’administration SharePoint.|
|Ajout d’un administrateur d’emplacement géographique|GeoAdminAdded|Un administrateur SharePoint ou général a ajouté un utilisateur en tant qu’administrateur géo d’un emplacement.|
|Utilisateur autorisé à créer des groupes|AllowGroupCreationSet|Un administrateur ou propriétaire de site ajoute un niveau d’autorisation à un site qui permet à un utilisateur auquel cette autorisation est octroyée de créer un groupe pour ce site.|
|Annulation du géodéplacement d’un site|SiteGeoMoveCancelled|Un administrateur SharePoint ou global annule correctement un déplacement géospatial de site SharePoint ou OneDrive. La fonctionnalité Multigéographie permet à une organisation de couvrir plusieurs géographies de centre de données Microsoft (appelées géos). Pour plus d’informations, voir [Fonctionnalités multigéographiques de OneDrive et SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Modification d’une stratégie de partage|SharingPolicyChanged|Un administrateur SharePoint ou général a modifié une stratégie de partage SharePoint à l’aide du Centre d’administration Microsoft 365, du Centre d’administration SharePoint ou de SharePoint Online Management Shell. Les modifications apportées aux paramètres de la stratégie de partage de votre organisation sont enregistrées. La stratégie modifiée est identifiée dans le champ **ModifiedProperties** des propriétés détaillées de l’enregistrement d’événement.|
|Modification de la stratégie d’accès aux appareils|DeviceAccessPolicyChanged|Un administrateur SharePoint ou général a modifié la stratégie relative aux appareils non gérés de votre organisation. Cette stratégie contrôle l’accès à SharePoint, OneDrive et Microsoft 365 sur les appareils qui ne sont pas associés à votre organisation. La configuration de cette stratégie nécessite un abonnement Enterprise Mobility + Security. Pour plus d’informations, voir [Contrôler l’accès à partir des appareils non gérés](/sharepoint/control-access-from-unmanaged-devices).|
|Agents utilisateurs exemptés modifiés|CustomizeExemptUsers|Un administrateur SharePoint ou général a personnalisé la liste des agents utilisateurs exemptés dans le Centre d'administration SharePoint. Vous pouvez spécifier les agents utilisateurs qui ne recevront pas de page web entière à indexer. Cela signifie que lorsqu'un agent utilisateur que vous avez spécifié comme exclus rencontre un formulaire InfoPath, le formulaire est renvoyé sous forme de fichier XML, au lieu d'une page web entière. Cela accélère l'indexation des formulaires InfoPath.|
|Modification de la stratégie d’accès au réseau|NetworkAccessPolicyChanged|Un administrateur SharePoint ou général a modifié la stratégie d’accès basée sur l’emplacement (également appelée limite réseau approuvée) dans le Centre d’administration SharePoint ou à l’aide de SharePoint Online PowerShell. Ce type de stratégie détermine qui peut accéder aux ressources SharePoint et OneDrive de votre organisation en fonction des plages d’adresses IP autorisées que vous spécifiez. Pour plus d’informations, voir [Contrôler l’accès aux données SharePoint Online et OneDrive en fonction d’emplacements réseau définis](/sharepoint/control-access-based-on-network-location).|
|Géodéplacement de site effectué|SiteGeoMoveCompleted|Un géodéplacement planifié par un administrateur général de votre organisation a été effectué avec succès. La fonctionnalité Multigéographie permet à une organisation de couvrir plusieurs géographies de centre de données Microsoft (appelées géos). Pour plus d’informations, voir [Fonctionnalités multigéographiques de OneDrive et SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Connexion Envoyé à créée|SendToConnectionAdded|Un administrateur SharePoint ou général crée une nouvelle connexion Envoyer à sur la page de gestion des enregistrements dans le Centre d'administration SharePoint. Une connexion Envoyer à spécifie les paramètres d'un référentiel de documents ou d'un centre d'enregistrements. Lorsque vous créez une connexion Envoyer à, un organisateur de contenu peut soumettre des documents à l'emplacement spécifié.|
|Collection de sites créée|SiteCollectionCreated|Un administrateur SharePoint ou global crée une collection de sites dans votre organisation SharePoint Online ou un utilisateur configure son site OneDrive Entreprise.|
|Site hub orphelin supprimé|HubSiteOrphanHubDeleted|Un administrateur SharePoint ou général a supprimé un site hub orphelin, qui est un site concentrateur qui n’a pas de sites associé. Un concentrateur orphelin est probablement dû à la suppression du site concentrateur d’origine.|
|Connexion Envoyé à supprimée|SendToConnectionRemoved|L’administrateur SharePoint ou général supprime une connexion Envoyer à sur la page de gestion des enregistrements dans le Centre d’administration SharePoint.|
|Site supprimé|SiteDeleted|L’administrateur de site supprime un site.|
|Aperçu du document activé|PreviewModeEnabledSet|Un administrateur de site active l’aperçu des documents pour un site.|
|Flux de travail hérité activé|LegacyWorkflowEnabledSet|L’administrateur de site ou le propriétaire ajoute le type de contenu Tâche de flux de travail SharePoint 2013 au site. Les administrateurs globaux peuvent également activer des flux de travail pour l’organisation entière dans le Centre d’administration SharePoint.|
|Office à la demande activé|OfficeOnDemandSet|L'administrateur de site active Office à la demande, qui permet aux utilisateurs d'accéder à la dernière version des applications de bureau Office. Office à la demande est activé dans le Centre d'administration SharePoint et nécessite un abonnement Microsoft 365 qui comprend des applications Office complètes et installées.|
|Source de résultats activée pour les recherches de personnes|PeopleResultsScopeSet|Un administrateur de site crée l’origine des résultats pour les recherches de personnes pour un site.|
|Flux RSS activés|NewsFeedEnabledSet|L'administrateur ou le propriétaire du site active les flux RSS d'un site. Les administrateurs généraux peuvent activer les flux RSS pour l'ensemble de l'organisation dans le Centre d'administration SharePoint.|
|Site joint au site concentrateur|HubSiteJoined|Un propriétaire de site associe son site à un site concentrateur.|
|Quota de collection de sites modifié|SiteCollectionQuotaModified|L’administrateur de site modifie le quota d’une collection de sites.|
|Site hub inscrit|HubSiteRegistered|Un administrateur SharePoint ou global crée un site concentrateur. Le résultat est que le site est inscrit pour être un site concentrateur.|
|Emplacement des données autorisées supprimé|AllowedDataLocationDeleted|Un administrateur SharePoint ou général a supprimé un emplacement de données autorisé dans un environnement à plusieurs emplacements géographiques.|
|Administrateur d’emplacement géographique supprimé|GeoAdminDeleted|Un administrateur SharePoint ou général a supprimé un utilisateur en tant qu’administrateur géo d’un emplacement.|
|Site renommé|SiteRenamed|Un administrateur ou propriétaire de site renomme un site.|
|Planification du géodéplacement d’un site|SiteGeoMoveScheduled|Un administrateur SharePoint ou global planifie correctement un déplacement géospatial de site SharePoint ou OneDrive. La fonctionnalité Multigéographie permet à une organisation de couvrir plusieurs géographies de centre de données Microsoft (appelées géos). Pour plus d’informations, voir [Fonctionnalités multigéographiques de OneDrive et SharePoint Online](../enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-microsoft-365.md).|
|Site hôte défini|HostSiteSet|Un administrateur SharePoint ou général modifie le site désigné pour l’hébergement de sites personnels ou OneDrive Entreprise.|
|Définir un quota de stockage pour un emplacement géographique|GeoQuotaAllocated|Un administrateur SharePoint ou général a configuré un quota de stockage pour un environnement à plusieurs emplacements géographiques.|
|Site disjoint d’un site concentrateur|HubSiteUnjoined|Un propriétaire de site dissocie son site d’un site concentrateur.|
|Site concentrateur non enregistré|HubSiteUnregistered|Un administrateur SharePoint ou global annule l’enregistrement d’un site concentrateur. Lorsqu’un site concentrateur est supprimé, il ne fonctionne plus en tant que site concentrateur.|
||||

### <a name="exchange-mailbox-activities"></a>Activités de la boîte aux lettres Exchange

Le tableau suivant répertorie les activités qui peuvent être enregistrées par la journalisation d’audit de la boîte aux lettres. Les activités de boîte aux lettres effectuées par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur sont enregistrées automatiquement dans le journal d’audit pendant 90 jours au maximum. Un administrateur peut désactiver la journalisation d’audit des boîtes aux lettres pour tous les utilisateurs de votre organisation. Dans ce cas, aucune action de boîte aux lettres pour un utilisateur n’est enregistrée. Pour plus d’informations, voir [Gérer l’audit de boîte aux lettres](enable-mailbox-auditing.md).

 Vous pouvez également rechercher des activités de boîte aux lettres à l’aide de l’applet de commande [Search-MailboxAuditLog](/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Éléments de boîte aux lettres consultés|MailItemsAccessed|Les messages sont lus ou consultés dans la boîte aux lettres. Les enregistrements d’audit pour cette activité sont déclenchés de deux manières : lorsqu’un client de courrier (par exemple, Outlook) effectue une opération de liaison sur des messages ou lorsque des protocoles de courrier (par exemple, Exchange ActiveSync ou IMAP) synchronisent des éléments dans un dossier de courrier. Cette activité est uniquement enregistrée pour les utilisateurs disposant d’une licence Office 365 ou Microsoft 365 E5. L’analyse des enregistrements d’audit pour cette activité est utile lorsque vous êtes à la recherche d'un compte de messagerie compromis. Pour plus d'informations, voir la section "Événements d'audit avancé" dans [Audit avancé](advanced-audit.md#advanced-audit-events). |
|Autorisations de boîtes aux lettres de délégué ajoutées|Add-MailboxPermission|Un administrateur a attribué l’autorisation de boîte aux lettres FullAccess à un utilisateur (appelé délégué) à la boîte aux lettres d’une autre personne. L’autorisation FullAccess permet au délégué d’ouvrir la boîte aux lettres d’un autre utilisateur ainsi que de lire et de gérer le contenu de la boîte aux lettres. L’enregistrement d’audit de cette activité est également généré lorsqu’un compte système dans le service Microsoft 365 effectue régulièrement des tâches de maintenance pour le compte de votre organisation. Une tâche courante effectuée par un compte système consiste à mettre à jour les autorisations pour les boîtes aux lettres système. Pour plus d’informations, voir [Comptes système dans les enregistrements d’audits de boîte aux lettres Exchange.](#system-accounts-in-exchange-mailbox-audit-records)|
|Utilisateur ajouté ou supprimé avec accès délégué au dossier calendrier|UpdateCalendarDelegation|Un utilisateur a été ajouté ou supprimé en tant que délégué au calendrier de la boîte aux lettres d’un autre utilisateur. La délégation de calendrier donne à une autre personne les mêmes autorisations d’organisation pour gérer le calendrier du propriétaire de la boîte aux lettres.|
|Autorisations ajoutées au dossier|AddFolderPermissions|Une autorisation de dossier a été ajoutée. Les autorisations de dossier contrôlent quels utilisateurs de votre organisation peuvent accéder aux dossiers dans une boîte aux lettres et aux messages situés dans ces dossiers.|
|Messages copiés vers un autre dossier|Copy|Un message a été copié vers un autre dossier.|
|Élément de boîte aux lettres créé|Créer|Un élément est créé dans le dossier Calendrier, Contacts, Notes ou Tâches de la boîte aux lettres.  Par exemple, une nouvelle demande de réunion est créée. Notez que la création, l’envoi ou la réception d’un message ne sont pas audités. De même, la création d’un dossier de boîte aux lettres n’est pas auditée.|
|Nouvelle règle de boîte de réception créée dans Outlook Web App|New-InboxRule|Un propriétaire de boîte aux lettres ou un autre utilisateur ayant accès à la boîte aux lettres a créé une règle de boîte de réception dans Outlook Web App.|
|Messages supprimés du dossier Éléments supprimés|SoftDelete|Un message a été supprimé définitivement ou non du dossier Éléments supprimés. Ces éléments sont déplacés vers le dossier Éléments récupérables. Les messages sont également déplacés vers le dossier Éléments récupérables lorsqu’un utilisateur les sélectionne et appuie sur **Maj+Suppr**.|
|Message étiqueté en tant qu’enregistrement|ApplyRecordLabel|Un message a été classifié en tant qu’enregistrement. Ceci se produit lorsqu’une étiquette de rétention qui classifie le contenu en tant qu’enregistrement est manuellement ou automatiquement appliquée à un message.|
|Messages déplacés vers un autre dossier|Move|Un message a été déplacé vers un autre dossier.|
|Messages déplacés vers le dossier Éléments supprimés|MoveToDeletedItems|Un message a été supprimé et déplacé vers le dossier Éléments supprimés.|
|Autorisation de dossier modifiée|UpdateFolderPermissions|Une autorisation de dossier a été modifiée. Les autorisations de dossier contrôlent quels utilisateurs de votre organisation peuvent accéder aux dossiers de boîte aux lettres et aux messages du dossier.|
|Règle de boîte de réception modifiée à partir d’Outlook Web App|Set-InboxRule|Un propriétaire de boîte aux lettres ou un autre utilisateur ayant accès à la boîte aux lettres a modifié une règle de boîte de réception dans Outlook Web App.|
|Messages supprimés définitivement de la boîte aux lettres|HardDelete|Un courrier a été supprimé définitivement du dossier Éléments récupérables (supprimé définitivement de la boîte aux lettres).|
|Autorisations de boîtes aux lettres de délégué supprimées|Remove-MailboxPermission|Un administrateur a supprimé l’autorisation FullAccess (qui était attribuée à un délégué) à partir de la boîte lettres d’un autre utilisateur. Une fois l’autorisation FullAccess supprimée, le délégué ne peut pas ouvrir l’autre boîte aux lettres ni accéder au contenu.|
|Autorisations supprimées du dossier|RemoveFolderPermissions|Une autorisation de dossier a été supprimée. Les autorisations de dossier contrôlent quels utilisateurs de votre organisation peuvent accéder aux dossiers dans une boîte aux lettres et aux messages situés dans ces dossiers.|
|Message envoyé|Envoyer|Un message a été envoyé, répondu ou transféré. Cette activité est uniquement enregistrée pour les utilisateurs disposant d’une licence Office 365 ou Microsoft 365 E5. Pour plus d'informations, voir la section « Événements d'audit avancé » dans [Audit avancé](advanced-audit.md#advanced-audit-events).|
|Message envoyé à l’aide d’autorisations Envoyer en tant que|SendAs|Un message a été envoyé à l'aide de l'autorisation SendAs. Cela signifie qu'un autre utilisateur a envoyé le message comme s'il provenait du propriétaire de la boîte aux lettres.|
|Message envoyé à l’aide d’autorisations Envoyer de la part de|SendOnBehalf|Un message a été envoyé à l’aide de l’autorisation SendOnBehalf. Cela signifie qu’un autre utilisateur a envoyé le message de la part du propriétaire de la boîte aux lettres. Le message indique au destinataire de la part de qui le message a été envoyé et qui a envoyé réellement le message.|
|Règles de boîte de réception mises à jour à partir du client Outlook|UpdateInboxRules|Un propriétaire de boîte aux lettres ou un autre utilisateur ayant accès à la boîte aux lettres a modifié une règle de boîte de réception dans le client Outlook.|
|Message mis à jour|Update|Un message (ou ses propriétés) a été modifié.|
|Utilisateur connecté à la boîte aux lettres|MailboxLogin|L’utilisateur s’est connecté à sa boîte aux lettres.|
|Étiqueter un message en tant qu’enregistrement||Un utilisateur a appliqué une étiquette de rétention à un message électronique. Cette étiquette est configurée pour identifier l’élément en tant qu’enregistrement. |
||||

#### <a name="system-accounts-in-exchange-mailbox-audit-records"></a>Comptes système dans les enregistrements d’audits de boîte aux lettres Exchange

Dans les enregistrements d’audit de certaines activités de boîte aux lettres (en particulier **Add-MailboxPermissions**), vous pouvez remarquer que l’utilisateur qui a effectué l’activité (et est identifié dans les champs User et UserId) est NT AUTHORITY\SYSTEM ou NT AUTHORITY\SYSTEM(Microsoft.Exchange.Servicehost). Cela indique que l'« utilisateur » qui a effectué l’activité était un compte système dans le service Exchange dans le cloud Microsoft. Ce compte système effectue souvent des tâches de maintenance planifiées pour le compte de votre organisation. Par exemple, une activité auditée courante effectuée par le compte NT AUTHORITY\SYSTEM(Microsoft.Exchange.ServiceHost) consiste à mettre à jour les autorisations sur discoverySearchMailbox, qui est une boîte aux lettres système. L’objectif de cette mise à jour est de vérifier que l’autorisation FullAccess (qui est la valeur par défaut) est affectée au groupe de rôles Gestion de la découverte pour DiscoverySearchMailbox. Cela garantit que les administrateurs eDiscovery peuvent effectuer les tâches nécessaires dans leur organisation.

Un autre compte d’utilisateur système qui peut être identifié dans un enregistrement d’audit pour **Add-MailboxPermission** est Administrator@apcprd03.prod.outlook.com. Ce compte de service est également inclus dans les enregistrements d’audit de boîte aux lettres liés à la vérification et à la mise à jour de l’autorisation FullAccess est attribué au groupe de rôles Gestion de la découverte pour la boîte aux lettres système DiscoverySearchMailbox. Plus précisément, les enregistrements d’audit qui identifient le compte Administrator@apcprd03.prod.outlook.com sont généralement déclenchés lorsque le personnel du support Microsoft exécute un outil de diagnostic de rôle RBAC pour le compte de votre organisation.

### <a name="user-administration-activities"></a>Activités d’administration des utilisateurs

Le tableau suivant répertorie les activités d’administration des utilisateurs enregistrées quand un administrateur ajoute ou modifie un compte d’utilisateur via le [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) ou le portail de gestion Azure.

> [!NOTE]
> Les noms d’opération répertoriés dans la colonne **Opération** de ce tableau contiennent un point ( `.` ). Vous devez inclure le point dans le nom de l’opération si vous spécifiez l’opération dans une commande PowerShell lors de la recherche dans le journal d’audit, la création de stratégies de rétention d’audit, la création de stratégies d’alerte, ou la création d’alertes d’activité. Utilisez également des guillemets doubles (`" "`) pour contenir le nom de l’opération.

|Activité|Opération|Description|
|:-----|:-----|:-----|
|Utilisateur ajouté|Ajouter un utilisateur.|Un compte d’utilisateur a été créé.|
|Licence utilisateur modifiée|Modifier une licence d’utilisateur.|La licence attribuée à un utilisateur a été modifiée. Pour identifier les licences modifiées, voir l’activité **Utilisateur mis à jour** correspondante.|
|Mot de passe utilisateur modifié|Modifier un mot de passe d’utilisateur.|Un utilisateur modifie son mot de passe. La réinitialisation du mot de passe en libre-service doit être activée (pour tous les utilisateurs ou les utilisateurs sélectionnés) au sein de votre organisation pour permettre aux utilisateurs de réinitialiser leur mot de passe. Vous pouvez également effectuer le suivi de l’activité de réinitialisation du mot de passe en libre-service dans Azure Active Directory. Pour plus d’informations, veuillez consulter la page [Options de création de rapports pour la gestion des mots de passe Azure AD](/azure/active-directory/authentication/howto-sspr-reporting).
|Utilisateur supprimé|Supprimez l’utilisateur.|Un compte d’utilisateur a été supprimé.|
|Réinitialiser le mot de passe de l’utilisateur|Réinitialiser un mot de passe d’utilisateur.|Un administrateur réinitialise le mot de passe d’un utilisateur.|
|Propriété définie qui force l’utilisateur à changer de mot de passe.|Définir la modification forcée d’un mot de passe d’utilisateur.|Un administrateur a défini la propriété qui force un utilisateur à modifier son mot de passe lors de sa prochaine connexion à Microsoft 365.|
|Propriétés de licence définies|Définir des propriétés de licence.|Un administrateur modifie les propriétés d’une licence attribuée à un utilisateur.|
|Utilisateur mis à jour|Mettre à jour un utilisateur.|Un administrateur modifie une ou plusieurs propriétés d’un compte d’utilisateur. Pour obtenir la liste des propriétés utilisateur qui peuvent être mises à jour, voir la section « Attributs de "Mettre à jour l’utilisateur" » dans [Événements de rapport d’audit d’Azure Active Directory](/azure/active-directory/reports-monitoring/concept-audit-logs).|
||||

### <a name="azure-ad-group-administration-activities"></a>Activités d’administration des groupes Azure AD

Le tableau suivant répertorie les activités d’administration des groupes enregistrées lorsqu’un administrateur ou un utilisateur crée ou modifie un groupe Microsoft 365 ou lorsqu’un administrateur crée ou un groupe de sécurité à l’aide du [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) ou du portail de gestion Azure. Pour plus d’informations sur les groupes Microsoft 365, voir [Afficher, créer et supprimer des groupes dans le Centre d'administration Microsoft 365](../admin/create-groups/create-groups.md).

> [!NOTE]
> Les noms d’opération répertoriés dans la colonne **Opération** de ce tableau contiennent un point ( `.` ). Vous devez inclure le point dans le nom de l’opération si vous spécifiez l’opération dans une commande PowerShell lors de la recherche dans le journal d’audit, la création de stratégies de rétention d’audit, la création de stratégies d’alerte, ou la création d’alertes d’activité. Utilisez également des guillemets doubles (`" "`) pour contenir le nom de l’opération.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Groupe ajouté|Ajouter un groupe.|Un groupe a été créé.|
|Membre ajouté au groupe|Ajouter un membre à un groupe.|Un membre a été ajouté à un groupe.|
|Groupe supprimé|Supprimer un groupe.|Un groupe a été supprimé.|
|Membre supprimé du groupe|Supprimer un membre d’un groupe.|Un membre a été supprimé d’un groupe.|
|Groupe mis à jour|Mettre à jour un groupe.|Une propriété d’un groupe a été modifiée.|
||||

### <a name="application-administration-activities"></a>Activités d’administration des applications

Le tableau suivant répertorie les activités d’administration des applications enregistrés lorsqu’un administrateur ajoute ou modifie une application enregistrée dans Azure AD. Les applications qui utilisent Azure AD pour l’authentification doivent être enregistrées dans l’annuaire.

> [!NOTE]
> Les noms d’opération répertoriés dans la colonne **Opération** de ce tableau contiennent un point ( `.` ). Vous devez inclure le point dans le nom de l’opération si vous spécifiez l’opération dans une commande PowerShell lors de la recherche dans le journal d’audit, la création de stratégies de rétention d’audit, la création de stratégies d’alerte, ou la création d’alertes d’activité. Utilisez également des guillemets doubles (`" "`) pour contenir le nom de l’opération.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Entrée de délégation ajoutée|Ajouter une entrée de délégation.|Une autorisation d’authentification a été créée/accordée à une application dans Azure AD.|
|Principal de service ajouté|Ajouter un principal du service.|Une application a été enregistrée dans Azure AD. Une application est représentée par un principal de service dans l’annuaire.|
|Informations d’identification ajoutées à un principal de service |Ajouter des informations d’identification d’un principal du service.|Des informations d’identification ont été ajoutées à un principal de service dans Azure AD. Un principal de service représente une application dans l’annuaire.|
|Entrée de délégation supprimée|Supprimer une entrée de délégation.|Une autorisation d’authentification a été supprimée d’une application dans Azure AD.|
|Principal de service supprimé de l’annuaire|Supprimer un principal du service.|Une application a été supprimée ou désinscrite de Azure AD. Une application est représentée par un principal de service dans l’annuaire.|
|Les informations d’identification ont été supprimées du principal de service |Supprimer des informations d’identification d’un principal du service.|Des informations d’identification ont été supprimées d’un principal de service dans Azure AD. Un principal de service représente une application dans l’annuaire.|
|Entrée de délégation définie|Définir une entrée de délégation.|Une autorisation d’authentification a été mise à jour pour une application dans Azure AD.|
||||

### <a name="role-administration-activities"></a>Activités d’administration des rôles

Le tableau suivant répertorie les activités d’administration des rôles Azure AD journalisées quand un administrateur gère les rôles d’administrateur via le [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) ou le portail de gestion Azure.

> [!NOTE]
> Les noms d’opération répertoriés dans la colonne **Opération** de ce tableau contiennent un point ( `.` ). Vous devez inclure le point dans le nom de l’opération si vous spécifiez l’opération dans une commande PowerShell lors de la recherche dans le journal d’audit, la création de stratégies de rétention d’audit, la création de stratégies d’alerte, ou la création d’alertes d’activité. Utilisez également des guillemets doubles (`" "`) pour contenir le nom de l’opération.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Membre ajouté au rôle|Ajouter un membre à un rôle.|Un utilisateur a été ajouté à un rôle d’administrateur dans Microsoft 365.|
|Utilisateur supprimé d’un rôle d’annuaire|Supprimer un membre d’un rôle.|Un utilisateur a été supprimé d’un rôle d’administrateur dans Microsoft 365.|
|Définition des informations de contact d’une entreprise|Définir des informations de contact professionnel.|Les préférences de contact au niveau de l’entreprise ont été mises à jour pour votre organisation. Cela inclut les adresses de messagerie pour les messages liés à un abonnement envoyés par Microsoft 365, ainsi que les notifications techniques relatives aux services.|
||||

### <a name="directory-administration-activities"></a>Activités d’administration de l’annuaire

Le tableau suivant répertorie les activités liées à l’annuaire et au domaine Azure AD journalisées quand un administrateur gère son organisation via le [Centre d’administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339) ou le portail de gestion Azure.

> [!NOTE]
> Les noms d’opération répertoriés dans la colonne **Opération** de ce tableau contiennent un point ( `.` ). Vous devez inclure le point dans le nom de l’opération si vous spécifiez l’opération dans une commande PowerShell lors de la recherche dans le journal d’audit, la création de stratégies de rétention d’audit, la création de stratégies d’alerte, ou la création d’alertes d’activité. Utilisez également des guillemets doubles (`" "`) pour contenir le nom de l’opération.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Domaine ajouté à l’entreprise|Ajouter un domaine à une entreprise.|Un domaine a été ajouté à votre organisation.|
|Partenaire ajouté à l’annuaire|Ajouter un partenaire à une entreprise.|Un partenaire (administrateur délégué) a été ajouté à votre organisation.|
|Domaine supprimé de l’entreprise|Supprimer un domaine d’une entreprise.|Un domaine a été supprimé de votre organisation.|
|Partenaire supprimé de l’annuaire|Supprimer un partenaire d’une entreprise.|Un partenaire (administrateur délégué) a été supprimé de votre organisation.|
|Définition des informations sur la société|Définir des informations d’une entreprise.|Les informations de l’entreprise ont été mises à jour pour votre organisation. Cela inclut les adresses de messagerie pour les messages liés à un abonnement envoyés par Microsoft 365, ainsi que les notifications techniques relatives aux services Microsoft 365.|
|Définition de l’authentification de domaine|Définir une authentification de domaine.|Le paramètre d’authentification de domaine a été modifié pour votre organisation.|
|Paramètres de fédération mis à jour pour un domaine|Définir des paramètres de fédération sur un domaine.|Les paramètres de la fédération (partage externe) ont été modifiés pour votre organisation.|
|Stratégie de mot de passe définie|Définir une stratégie de mot de passe.|Les contraintes de longueur et de caractères applicables aux mots de passe utilisateur ont été modifiées dans votre organisation.|
|Activation de la synchronisation Azure AD|Définir un indicateur DirSyncEnabled.|La propriété qui active un annuaire pour la synchronisation Azure AD a été définie.|
|Domaine mis à jour|Mettre à jour un domaine.|Les paramètres d’un domaine dans votre organisation ont été mis à jour.|
|Domaine vérifié|Vérifier un domaine.|La propriété d’un domaine par votre organisation a été vérifiée.|
|Domaine de courrier vérifié par courrier électronique|Vérifier un domaine vérifié d’e-mail.|Une vérification de courrier électronique a été effectuée pour vérifier que votre organisation est propriétaire d’un domaine.|
||||

### <a name="ediscovery-activities"></a>Activités de découverte électronique

Les activités liées à la recherche de contenu et la découverte électronique effectuées dans le centre de sécurité et conformité ou via l’exécution des cmdlets PowerShell correspondantes sont enregistrées dans le journal d’audit. Cela inclut les activités suivantes :

- création et gestion des cas de découverte électronique ;

- création, démarrage et modification des recherches de contenu ;

- exécution des actions de recherche de contenu, telles que l’aperçu, l’exportation et la suppression des résultats de recherche ;

- configuration des autorisations de filtrage de la recherche de contenu ;

- gestion du rôle d’administrateur eDiscovery.

Pour consulter la liste et une description détaillée des activités de découverte électronique enregistrées, voir [Rechercher les activités de découverte électronique dans le journal d’audit](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> Une trentaine de minutes peut être nécessaire avant que les événements résultant des activités répertoriées sous l’élément **Activités de découverte électronique** et **activités Advanced eDiscovery** de la liste déroulante **Activités** s’affichent dans les résultats de la recherche. Inversement, 24 heures peuvent être nécessaires avant que les événements correspondant aux activités de l’applet de commande eDiscovery s’affichent dans les résultats de la recherche.

### <a name="advanced-ediscovery-activities"></a>Activités avancées eDiscovery

Vous pouvez également effectuer une recherche dans le journal d’audit des activités dans Advanced eDiscovery. Pour obtenir une description de ces activités, consultez la section « activités Advanced eDiscovery » dans [Rechercher des activités eDiscovery dans le journal d’audit](search-for-ediscovery-activities-in-the-audit-log.md#advanced-ediscovery-activities).

### <a name="power-bi-activities"></a>Activités dans Power BI

Vous pouvez effectuer une recherche dans le journal d’audit des activités dans Power BI. Pour plus d’informations sur les activités Power BI, voir la section «activités vérifiées par Power BI» dans [utilisation de l'audit au sein de votre organisation](/power-bi/service-admin-auditing#activities-audited-by-power-bi).

L’enregistrement d’audit pour Power BI n’est pas activé par défaut. Pour rechercher des activités Power BI dans le journal d’audit, vous devez activer l’audit dans le portail d’administration Power BI. Pour consulter des instructions, voir la section «journaux d’audit» du [portail d’administration Power BI](/power-bi/service-admin-portal#audit-logs).

### <a name="workplace-analytics-activities"></a>Activités de Workplace Analytics

Analyse du temps de travail explique comment les groupes collaborent au sein de votre organisation. Le tableau suivant répertorie les activités effectuées par les utilisateurs auxquels est attribué le rôle d’administrateur ou les rôles d’analyste dans Workplace Analytics. Les utilisateurs dotés du rôle d’analyste ont un accès total à toutes les fonctionnalités du service et utilisent le produit pour effectuer l’analyse. Les utilisateurs dotés du rôle d’administrateur peuvent configurer les paramètres de confidentialité et les valeurs par défaut du système, et peuvent préparer, charger et vérifier les données organisationnelles dans Workplace Analytics. Pour plus d'informations, voir [Workplace Analytics](/workplace-analytics/index-orig).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Lien OData consulté|AccessedOdataLink|Les analystes ont accédé au lien OData pour une requête.|
|Requête annulée|CanceledQuery|Un analyste a annulé une requête en cours d’exécution.|
|Exclusion de réunion créée|MeetingExclusionCreated|Un analyste a créé une règle d’exclusion de réunion.|
|Résultat supprimé|DeletedResult|Un analyste a supprimé un résultat de requête.|
|Fichier téléchargé|DownloadedReport|Un analyste a téléchargé un résultat de requête.|
|Requête exécutée|ExecutedQuery|Un analyste a exécuté une requête.|
|Paramètres d’accès aux données mis à jour|UpdatedDataAccessSetting|Un administrateur a mis à jour les paramètres d’accès aux données.|
|Paramètre de confidentialité mis à jour|UpdatedPrivacySetting|Paramètres de confidentialité mis à jour par l’administrateur; par exemple, taille de groupe minimale.|
|Données d’organisation téléchargées|UploadedOrgData|Fichier de données d’organisation téléchargé par l’administrateur.|
|Utilisateur connecté<sup>*</sup>| Utilisateur connecté |Un utilisateur connecté à son compte d'utilisateur Microsoft 365.|
|Utilisateur déconnecté<sup>*</sup>| UserLoggedOff |Un utilisateur s'est déconnecté de son compte d'utilisateur Microsoft 365.
|Exploration de la consultation|ViewedExplore|Un analyste a consulté les visualisations dans un ou plusieurs onglets de page exploration.|
||||

> [!NOTE]
> <sup>*</sup>Il s'agit des activités de connexion et de déconnexion Azure Active Directory Domain Services. Ces activités sont enregistrées même si Workplace Analytics n'est pas activé dans votre organisation. Pour plus d'informations sur les activités de connexion des utilisateurs, consultez [Journaux de connexion dans Azure Active Directory Domain Services](/azure/active-directory/reports-monitoring/concept-sign-ins).

### <a name="microsoft-teams-activities"></a>Activités dans Microsoft Teams 

Vous pouvez effectuer une recherche dans le journal d’audit des activités des utilisateurs et des administrateurs dans Microsoft Teams. Teams est un espace de travail centré sur la conversation dans Microsoft 365. Il rassemble les conversations, réunions, fichiers et notes d’une équipe dans un emplacement unique. Pour obtenir une description des activités Teams qui font l’objet d’un audit, consultez [Rechercher dans le journal d’audit des événements dans Microsoft Teams](/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Activités Santé Microsoft Teams

Si votre organisation utilise l’application [Patients](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) dans Microsoft Teams, vous pouvez effectuer une recherche dans le journal d’audit pour consulter les activités liées à l’application Patients. Si votre environnement est configuré pour prendre en charge l’application Patients, un groupe d’activités supplémentaire pour ces activités est disponible dans la liste du sélecteur **Activitiés**.

![Les activités Microsoft Teams pour la santé dans les activités de la liste du sélecteur.](../media/TeamsHealthcareAuditActivities.png)

Pour obtenir une description des activités de l’application Patients, voir les [journaux d’audit pour l’application Patients](/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>Activités Shifts dans Microsoft Teams

Si votre organisation utilise l’application Shifts dans Microsoft Teams, vous pouvez effectuer une recherche dans le journal d’audit pour consulter les activités liées à cette application. Si votre environnement est configuré pour prendre en charge l’application Shifts, un groupe d’activités supplémentaire pour ces activités est disponible dans la liste du sélecteur **Activités**.

Pour obtenir une description des activités de l’application Shifts, consultez [Rechercher dans le journal d’audit des événements dans Microsoft Teams](/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>Activités dans Yammer

Le tableau suivant répertorie les activités des utilisateurs et des administrateurs dans Yammer qui sont enregistrées dans le journal d’audit. Pour renvoyer des activités Yammer du journal d’audit, vous devez sélectionner **Afficher les résultats pour toutes les activités** dans la liste **Activités**. Utilisez les zones des plages de dates et la liste **Utilisateurs** pour limiter les résultats de la recherche.

> [!NOTE]
> Certaines activités d'audit de Yammer ne sont disponibles que dans l'audit avancé. Cela signifie que les utilisateurs doivent se voir attribuer la licence appropriée avant que ces activités ne soient enregistrées dans le journal d'audit. Pour plus d'informations sur les activités disponibles uniquement dans l'audit avancé, voir [Audit avancé](advanced-audit.md#advanced-audit-events) dans Microsoft 365 . Pour connaître les conditions de licence de l'audit avancé, consultez la section [Solutions d'audit dans Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>Dans le tableau suivant, les activités d'audit avancé sont marquées d'un astérisque (*).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Modification d’une stratégie de rétention des données|SoftDeleteSettingsUpdated|Un administrateur vérifié met à jour le paramètre de stratégie de rétention des données de réseau en vue d’une suppression définitive ou réversible. Seuls des administrateurs vérifiés peuvent effectuer cette opération.|
|Modification de configuration réseau|NetworkConfigurationUpdated|Un administrateur réseau ou vérifié modifie la configuration du réseau Yammer. Cela inclut la définition d’un intervalle pour l’exportation de données et l’activation de la conversation instantanée.|
|Modification des paramètres de profil réseau|ProcessProfileFields|Un administrateur réseau ou vérifié modifie les informations qui apparaissent sur les profils de membre des utilisateurs du réseau.|
|Modification du mode Contenu privé|SupervisorAdminToggled|Un administrateur vérifié active ou désactive le *mode contenu privé*. Ce mode permet à un administrateur d’afficher les publications dans des groupes privés et les messages privés entre utilisateurs individuels (ou groupes d’utilisateurs). Seuls les administrateurs vérifiés peuvent effectuer cette opération.|
|Modification de la configuration de la sécurité|NetworkSecurityConfigurationUpdated|Un administrateur vérifié met à jour la configuration de sécurité du réseau Yammer. Cela inclut la définition des stratégies d’expiration de mot de passe et les restrictions d’adresses IP. Seuls les administrateurs vérifiés peuvent effectuer cette opération.|
|Création de fichier|FileCreated|Un utilisateur charge un fichier.|
|Groupe créé|GroupCreation|L’utilisateur crée un groupe.|
|Message créé<sup>*</sup>|MessageCréé|L’utilisateur crée un groupe.|
|Groupe supprimé|GroupDeletion|Un groupe est supprimé de Yammer.|
|Message supprimé|MessageDeleted|Un utilisateur supprime un message.|
|Fichier téléchargé|FileDownloaded|Un utilisateur télécharge un fichier.|
|Données exportées|DataExport|Un administrateur vérifié exporte des données de réseau Yammer. Seuls les administrateurs vérifiés peuvent effectuer cette opération.|
|Échec de l'accès à la communauté<sup>*</sup>|CommunityAccessFailure|L'utilisateur n'a pas réussi à accéder à une communauté.|
|Échec de l'accès au fichier<sup>*</sup>|FileAccessFailure|L'utilisateur n'a pas réussi à accéder à un fichier.|
|Échec de l'accès au message<sup>*</sup>|MessageAccessFailure|L'utilisateur n'a pas réussi à accéder à un message.|
|Partage de fichier|FileShared|Un utilisateur partage un fichier avec un autre utilisateur.|
|Suspension d’un utilisateur du réseau|NetworkUserSuspended|Un administrateur réseau ou vérifié suspend (désactive) un utilisateur de Yammer.|
|Utilisateur suspendu|UserSuspension|Un compte d’utilisateur est suspendu (désactivé).|
|Mise à jour de la description d’un fichier|FileUpdateDescription|Un utilisateur modifie la description d’un fichier.|
|Mise à jour d’un nom de fichier|FileUpdateName|Un utilisateur modifie le nom d’un fichier.|
|Message mis à jour<sup>*</sup>|MessageUpdated|Un utilisateur met à jour un message.|
|Affichage d’un fichier|FileVisited|Un utilisateur affiche un fichier.|
|Message affiché<sup>*</sup>|MessageViewed|Un utilisateur affiche un message.|
||||

### <a name="microsoft-power-automate-activities"></a>Activités Microsoft Power Automate

Vous pouvez effectuer une recherche dans le journal d’audit des activités dans Power Automate (précédemment appelé Microsoft Flow). Ces activités incluent la création, la modification et la suppression de flux, et la modification des autorisations de flux. Pour plus d’informations sur l’audit des activités de Power Automate, voir le blog [événements d’audit de Microsoft Flow désormais disponible dans le Centre de conformité Microsoft 365](https://flow.microsoft.com/blog/security-and-compliance-center).

### <a name="microsoft-power-apps-activities"></a>Activités Microsoft Power Apps

Vous pouvez effectuer une recherche dans le journal d’audit pour consulter les activités liées aux applications dans Power Apps. Ces activités incluent la création, le lancement et la publication d’une application. L’attribution d’autorisations à des applications est également auditée. Pour obtenir une description de toutes les activités Power Apps, voir [Journalisation des activités pour Power Apps](/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>Activités de Microsoft Stream

Vous pouvez effectuer une recherche dans le journal d’audit des activités dans Microsoft Stream. Ces activités incluent les activités de vidéo effectuées par les utilisateurs, les activités de canal de groupe et les activités d’administrateur telles que la gestion des utilisateurs, la gestion des paramètres d’organisation et l’exportation de rapports. Pour obtenir une description de ces activités, voir «Actions enregistrées dans Stream» dans [Journaux d’audit dans Microsoft Stream](/stream/audit-logs#actions-logged-in-stream).

### <a name="content-explorer-activities"></a>Activités de l’Explorateur de contenu

Le tableau suivant répertorie les activités de l’Explorateur de contenu qui sont enregistrées dans le journal d’audit. Explorateur de contenu, accessible sur l’outil classifications de données, dans le Centre de conformité Microsoft 365. Pour plus d’informations, voir [Utilisation de l’Explorateur de contenu](data-classification-content-explorer.md).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Élément consulté|LabelContentExplorerAccessedItem|Un administrateur (ou utilisateur membre du groupe de rôles Visionneuse de contenu de l’Explorateur de contenu) utilise l’Explorateur de contenu pour afficher un e-mail ou un document SharePoint/OneDrive.|
||||

### <a name="quarantine-activities"></a>Activités de mise en quarantaine

Le tableau suivant illustre une liste d’activités que vous pouvez rechercher dans le journal d’audit. Si vous souhaitez en savoir plus sur la mise en quarantaine, consultez l’article [Mettre les e-mails en quarantaine](../security/office-365-security/quarantine-email-messages.md).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Message de quarantaine supprimé|QuarantineDelete|Un utilisateur a supprimé un message électronique considéré comme dangereux.|
|Message de quarantaine exporté|QuarantineExport|Un utilisateur a exporté un message électronique considéré comme dangereux.|
|Message de quarantaine visualisé|QuarantinePreview|Un utilisateur a visualisé un message électronique considéré comme dangereux.|
|Message de quarantaine publié|QuarantineRelease|Un utilisateur a publié un message électronique de quarantaine considéré comme dangereux.|
|En-tête du message de quarantaine consulté|QuarantineViewHeader|Un utilisateur a affiché l’en-tête d’un message électronique considéré comme dangereux.|
||||

### <a name="microsoft-forms-activities"></a>Activités Microsoft Forms

Les tableaux de cette section présentent les activités des utilisateurs et des administrateurs de Microsoft Forms qui sont enregistrées dans le journal d'audit. Microsoft Forms est un outil de formulaire/questionnaire/enquête utilisé pour collecter des données pour analyse. Dans les descriptions ci-dessous, certaines opérations contiennent d’autres paramètres d’activité.

Si une activité Forms est réalisée par un co-auteur ou un répondant anonyme, elle est enregistrée de façon légèrement différente. Pour plus d’informations, voir la section [Activités Forms réalisées par des co-auteurs ou des répondants anonymes](#forms-activities-performed-by-coauthors-and-anonymous-responders).

> [!NOTE]
> Certaines activités de formulaires d'audit ne sont disponibles que dans l'audit avancé. Cela signifie que les utilisateurs doivent se voir attribuer la licence appropriée avant que ces activités ne soient enregistrées dans le journal d'audit. Pour plus d'informations sur les activités disponibles uniquement dans l'audit avancé, voir [Audit avancé](advanced-audit.md#advanced-audit-events) dans Microsoft 365 . Pour connaître les conditions de licence de l'audit avancé, consultez la section [Solutions d'audit dans Microsoft 365](auditing-solutions-overview.md#licensing-requirements). <br/><br/>Dans le tableau suivant, les activités d'audit avancé sont marquées d'un astérisque (*).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Commentaire créé|CreateComment|Le propriétaire du formulaire ajoute un commentaire ou une note à un questionnaire.|
|Formulaire créé|CreateForm|Le propriétaire du formulaire crée un nouveau formulaire. <br><br>La propriété DataMode:string indique que le formulaire actuel est défini pour synchroniser avec un classeur Excel existant ou nouveau si la valeur de propriété est égal à DataSync. La propriété ExcelWorkbookLink:string indique l’ID du classeur Excel associé du formulaire actuel.|
|Formulaire modifié|EditForm|Le propriétaire du formulaire modifie un formulaire tel que la création, la suppression ou la modification d’une question. La propriété *EditOperation:string* indique le nom de l’opération de modification. Voici les opérations possibles :<br/>– CreateQuestion<br/>– CreateQuestionChoice <br/>– DeleteQuestion <br/>– DeleteQuestionChoice <br/>– DeleteFormImage <br/>– DeleteQuestionImage <br/>– UpdateQuestion <br/>– UpdateQuestionChoice <br/>– UploadFormImage/Bing/Onedrive <br/>– UploadQuestionImage <br/>– ChangeTheme <br><br>FormImage inclut tout emplacement au sein duquel l’utilisateur peut charger une image, par exemple dans une requête ou en tant que thème d’arrière-plan.|
|Formulaire déplacé|MoveForm|Le propriétaire du formulaire déplace un formulaire. <br><br>La propriété DestinationUserId:string indique l'ID d'utilisateur de la personne qui a déplacé le formulaire. La propriété NewFormId:String est le nouvel ID du formulaire nouvellement copié. La propriété IsDelegateAccess:boolean indique que l’action de déplacement du formulaire actuel est effectuée via la page de délégué administrateur.|
|Formulaire supprimé|DeleteForm|Un propriétaire d’un formulaire supprime une équipe. Cela inclut SoftDelete (option de suppression utilisée et formulaire déplacé vers la corbeille) et HardDelete (corbeille vidée).|
|Formulaire consulté (moment de la création)|ViewForm|Le propriétaire du formulaire ouvre un formulaire existant pour modification. <br><br>La propriété AccessDenied:boolean indique que l’accès du formulaire actuel est refusé en raison de la vérification d’autorisation. La propriété FromSummaryLink:boolean indique que la demande actuelle provient de la page de lien du résumé.|
|Formulaire prévisualisé|PreviewForm|Propriétaire du formulaire affiche un aperçu d’un formulaire à l’aide de la fonction d’aperçu.|
|Données exportées|ExportForm|Le propriétaire du formulaire exporte les résultats vers Excel. <br><br>La propriété ExportFormat:string indique si le fichier Excel est téléchargé ou en ligne.|
|Formulaire de partage autorisé pour la copie|AllowShareFormForCopy|Le propriétaire du formulaire crée un lien modèle pour partager le formulaire avec d'autres utilisateurs. Cet événement est consigné lorsque le propriétaire du formulaire clique sur pour générer l’URL du modèle.|
|Formulaire de partage non autorisé pour copie|DisallowShareFormForCopy|Le propriétaire du formulaire supprime le lien modèle.|
|Co-auteur du formulaire ajouté|AddFormCoauthor|Un utilisateur utilise un lien de collaboration pour vous aider à concevoir et afficher les réponses. Cet événement est consigné lorsqu’un utilisateur utilise une URL espace collaboration (pas lorsque espace collaboration URL est générée pour la première fois).|
|Co-auteur du formulaire supprimé|RemoveFormCoauthor|Le propriétaire du formulaire supprime un lien de collaboration.|
|Page de réponse consultée|ViewRuntimeForm|Un utilisateur a ouvert une page de réponse à afficher. Cet événement est consigné, que l’utilisateur envoie ou non une réponse.|
|Réponse créée|CreateResponse|Similaire à la réception d'une nouvelle réponse.  Un utilisateur a soumis une réponse à un formulaire. <br><br>La propriété ResponseId:string et la propriété ResponderId:string indiquent quel résultat est affiché. <br><br>Pour un répondant anonyme, la propriété ResponderId sera null.|
|Réponse mise à jour|UpdateResponse|Le propriétaire du formulaire a mis à jour un commentaire ou une note sur un questionnaire. <br><br>La propriété ResponseId:string et la propriété ResponderId:string indiquent quel résultat est affiché. <br><br>Pour un répondant anonyme, la propriété ResponderId sera null.|
|Toutes les réponses supprimées|DeleteAllResponses|Le propriétaire du formulaire supprime toutes les données de réponse.|
|Réponse supprimée|DeleteResponse|Un propriétaire d’un formulaire supprime une réponse. <br><br>La propriété ResponseId:string indique la réponse en cours de suppression.|
|Réponses consultées|ViewResponses|Propriétaire du formulaire affiche la liste agrégée des réponses. <br><br>La propriété ViewType : String indique si le propriétaire du formulaire affiche les détails ou les agrégats|
|Réponse consultée|ViewResponse|Le propriétaire du formulaire affiche une réponse spécifique. <br><br>La propriété ResponseId:string et la propriété ResponderId:string indiquent quel résultat est affiché. <br><br>Pour un répondant anonyme, la propriété ResponderId sera null.|
|Lien de synthèse créé|GetSummaryLink|Le propriétaire du formulaire crée un lien de résultats de synthèse pour partager les résultats.|
|Lien de synthèse supprimé|DeleteSummaryLink|Le propriétaire du formulaire supprime le lien de synthèse des résultats.|
|Formulaire mis à jour état d’hameçonnage|UpdatePhishingStatus|Cet événement est enregistré chaque fois que la valeur détaillée de l’état de sécurité interne est modifiée, que cela modifie l’état de sécurité final ou non (par exemple, le formulaire est désormais Fermé ou Ouvert). Cela signifie que vous pouvez rencontrer des événements en double même si l’état de sécurité final n’a pas été modifié. Voici les valeurs d’état possibles pour cet événement :<br/>– Retirer <br/>– Retirer par l’administrateur <br/>– Admin débloqué <br/>– Bloqué automatiquement <br/>– Débloqué automatiquement <br/>– Utilisateur signalé <br/>– Réinitialiser l’utilisateur signalé|
|État de l’hameçonnage de l’utilisateur mis à jour|UpdateUserPhishingStatus|Cet événement est enregistré chaque fois que la valeur de l’état de sécurité de l’utilisateur est modifiée. La valeur de l’état de l’utilisateur dans l’enregistrement d’audit est définie sur **Confirmé comme hameçonnage** lorsque l’utilisateur créé un formulaire d’hameçonnage qui est supprimé par l’équipe de sécurité de Microsoft Online. Si un administrateur débloque l’utilisateur, la valeur de l’état de l’utilisateur est définie sur **Réinitialiser en tant qu’utilisateur normal**.|
|Invitation Forms Pro envoyée|ProInvitation|L’utilisateur clique pour activer une version d’évaluation Pro.|
|Paramètres de formulaire mis à jour<sup>*</sup> |UpdateFormSetting|Le propriétaire du formulaire met à jour un ou plusieurs paramètres de formulaire. <br><br>La propriété FormSettingName:string indique le nom des paramètres sensibles mis à jour. La propriété NewFormSettings:string indique la nouvelle valeur et le nom des paramètres mis à jour. Propriété thankYouMessageContainsLink:booléen indique que le message de remerciement mis à jour contient un lien URL.|
|Paramètres d’utilisateur mis à jour|UpdateUserSetting|Le propriétaire du formulaire met à jour un paramètre d’utilisateur. <br><br>La propriété UserSettingName:string indique le nom et la nouvelle valeur du paramètre|
|Formulaires répertoriés<sup>*</sup>|ListForms|Le propriétaire du formulaire affiche une liste de formulaires. <br><br>La propriété ViewType:string indique l'affichage que le propriétaire du formulaire consulte : Tous les formulaires, Partagés avec moi ou les Formulaires de groupe|
|Réponse envoyée|SubmitResponse|Un utilisateur envoie une réponse à un formulaire. <br><br>La propriété IsInternalForm:boolean indique si le répondant fait partie de la même organisation que le propriétaire du formulaire.|
|Paramètre activé : tout le monde peut répondre.<sup>*</sup>|AllowAnonymousResponse|Le propriétaire du formulaire active le paramètre autorisant tout le monde à répondre au formulaire.|
|Paramètre désactivé : tout le monde peut répondre<sup>*</sup>.|DisallowAnonymousResponse|Le propriétaire du formulaire désactive le paramètre autorisant tout le monde à répondre au formulaire.|
|Paramètre activé : des personnes spécifiques peuvent répondre au paramètre<sup>*</sup>.|EnableSpecificResponse|Le propriétaire du formulaire active le paramètre autorisant uniquement des personnes ou des groupes spécifiques de l’organisation actuelle à répondre au formulaire.|
|Paramètre désactivé : des personnes spécifiques peuvent répondre<sup>*</sup>.|DisableSpecificResponse|Le propriétaire du formulaire désactive le paramètre autorisant uniquement des personnes ou des groupes spécifiques de l’organisation actuelle à répondre au formulaire.|
|Ajout d'un répondeur spécifique<sup>*</sup>|AddSpecificResponder|Le propriétaire du formulaire ajoute un nouvel utilisateur ou un nouveau groupe à la liste des répondeurs spécifiques.|
|Suppression du répondeur spécifique<sup>*</sup>|RemoveSpecificResponder|Le propriétaire du formulaire supprime un utilisateur ou un groupe à la liste des répondeurs spécifiques.|
|Collaboration désactivée<sup>*</sup>|DisableCollaboration|Le propriétaire de formulaire désactive le paramètre de collaboration sur le formulaire.|
|Activation de la collaboration d’un compte professionnel ou scolaire Office 365<sup>*</sup>|EnableWorkOrSchoolCollaboration|Le propriétaire du formulaire active le paramètre autorisant les utilisateurs ayant un compte professionnel ou scolaire Microsoft 365 à afficher et modifier le formulaire.|
|Collaboration activée des personnes de mon organisation<sup>*</sup>|EnableSameOrgCollaboration|Le propriétaire du formulaire active le paramètre autorisant les utilisateurs de l’organisation actuelle à afficher et modifier le formulaire.|
|Collaboration activée de personnes spécifiques<sup>*</sup>|EnableSpecificCollaboaration|Le propriétaire du formulaire active le paramètre autorisant uniquement des personnes ou des groupes spécifiques de l’organisation actuelle à afficher et modifier le formulaire.|
|Connecté à un classeur Excel<sup>*</sup>|ConnectToExcelWorkbook|Formulaire connecté à un classeur Excel. <br><br>La propriété ExcelWorkbookLink:string indique l’ID du classeur Excel associé du formulaire actuel.|
|Collection créée|CollectionCreated|Le propriétaire du formulaire a créé une collection.|
|Collection mise à jour|CollectionUpdated|Le propriétaire du formulaire a mis à jour une propriété de collection.|
|Collection supprimée de la Corbeille|CollectionHardDeleted|Propriétaire du formulaire a supprimé définitivement une collection de la Corbeille.|
|Collection déplacée vers la Corbeille|CollectionSoftDeleted|Le propriétaire du formulaire a déplacé une collection vers la Corbeille.|
|Collection renommée|CollectionRenamed|Le propriétaire du formulaire a modifié le nom d’une collection.|
|Un formulaire a été déplacé dans la collection|MovedFormIntoCollection|Le propriétaire du formulaire a déplacé un formulaire dans une collection.|
|Un formulaire a été déplacé hors de la collection|MovedFormOutofCollection|Le propriétaire du formulaire a déplacé un formulaire d’une collection.|
||||

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Activités Forms réalisées par des co-auteurs et des répondants anonymes

Forms prend en charge la collaboration pendant la conception des formulaires et l’analyse des réponses. Un collaborateur de formulaire est appelé *co-auteur*. Les co-auteurs peuvent effectuer les mêmes actions que le propriétaire d’un formulaire, excepté supprimer ou déplacer un formulaire. Forms vous permet également de créer un formulaire dans lequel les répondants restent anonymes.  Ce qui signifie qu’un répondant n’a pas besoin d’être connecté à votre organisation pour répondre à un formulaire.

Le tableau suivant décrit les activités d’audit et les informations figurant dans l’enregistrement d’audit pour les activités réalisées par les co-auteurs et les répondants anonymes.

|Type d’activité|Utilisateur interne ou externe|Identifiant de l’utilisateur connecté|Organisation connectée à|Type d’utilisateur Forms|
|:-----|:-----|:-----|:-----|:-----|
|Activités de co-création|Interne|UPN|Organisation du propriétaire du formulaire|Co-auteur|
|Activités de co-création|Externe|UPN<br>|Organisation du co-auteur<br>|Co-auteur|
|Activités de co-création|Externe|`urn:forms:coauthor#a0b1c2d3@forms.office.com`<br>(La deuxième partie de l’identifiant est hachée de façon différente pour chaque utilisateur).|Organisation du propriétaire du formulaire<br>|Co-auteur|
|Activités de réponse|Externe|UPN<br>|Organisation du répondant<br>|Répondant|
|Activités de réponse|Externe|`urn:forms:external#a0b1c2d3@forms.office.com`<br>(La deuxième partie de l’identifiant d’utilisateur est hachée de façon différente pour chaque utilisateur).|Organisation du propriétaire du formulaire|Répondant|
|Activités de réponse|Anonyme|`urn:forms:anonymous#a0b1c2d3@forms.office.com`<br>(La deuxième partie de l’identifiant d’utilisateur est hachée de façon différente pour chaque utilisateur).|Organisation du propriétaire du formulaire|Répondant|
||||

### <a name="sensitivity-label-activities"></a>Activités des étiquettes de confidentialité

Le tableau suivant répertorie les événements qui résultent de l’utilisation d’[étiquettes de confidentialité](sensitivity-labels.md).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Étiquette de confidentialité appliquée au site|SensitivityLabelApplied|Une étiquette de confidentialité a été appliquée à un site SharePoint ou Teams.|
|Suppression de l'étiquette de confidentialité sur le site|SensitivityLabelRemoved|Une étiquette de confidentialité a été supprimée sur un site SharePoint ou Teams.|
|Étiquette de confidentialité appliquée au fichier|FileSensitivityLabelApplied|Une étiquette de niveau de confidentialité a été appliquée à un document à l’aide des Microsoft 365 Apps Office sur le Web. ou une stratégie d’étiquetage automatique.|
|Étiquette de confidentialité modifiée appliquée au fichier|FileSensitivityLabelChanged<br /><br>SensitivityLabelUpdated|Une étiquette de niveau de confidentialité différente a été appliquée à un document. <br /><br>Les opérations de cette activité sont différentes en fonction de la façon dont l’étiquette a été modifiée :<br /> Office sur le Web ou une stratégie d’étiquetage automatique (FileSensitivityLabelChanged) <br /> Microsoft 365 Apps (SensitivityLabelUpdated)|
|Étiquette de confidentialité modifiée sur un site|SensitivityLabelChanged|Une étiquette de niveau de confidentialité différente a été appliquée à un site Microsoft Office SharePoint Online ou Teams.|
|Suppression de l'étiquette de confidentialité sur le document|FileSensitivityLabelRemoved|Une étiquette de confidentialité a été supprimée d’un document à l’aide d’applications Microsoft 365, d’Office sur le Web, d’une stratégie d’étiquetage automatique ou de l’applet de commande [Unlock-SPOSensitivityLabelEncryptedFile](/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile).|
||||

### <a name="retention-policy-and-retention-label-activities"></a>Stratégie de rétention et activités d’étiquette de rétention

Le tableau suivant décrit les activités de configuration des [stratégies de rétention et des étiquettes de rétention](retention.md) lorsqu’elles ont été créées, reconfigurées ou supprimées.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
| Appartenance à l’étendue adaptative modifiée |ApplicableAdaptiveScopeChange |Des utilisateurs, des sites ou des groupes ont été ajoutés ou supprimés de l’étendue adaptative. Ces modifications sont le résultat de l’exécution de la requête de l’étendue. Étant donné que les modifications sont initiées par le système, l’utilisateur signalé s’affiche en tant que GUID plutôt qu’en tant que compte d’utilisateur.|
| Paramètres configurés pour une stratégie de rétention |NewRetentionComplianceRule |L’administrateur a configuré les paramètres de rétention pour une nouvelle stratégie de rétention. Les paramètres de rétention incluent la durée de conservation des éléments et ce qu’il advient des éléments à l’expiration de la période de rétention (comme la suppression d’éléments, la conservation des éléments ou leur conservation puis leur suppression). Cette activité correspond également à l’exécution du cmdlet [New-RetentionComplianceRule](/powershell/module/exchange/new-retentioncompliancerule).|
| Étendue adaptative créée |NewAdaptiveScope |L’administrateur a créé une étendue adaptative.|
| Étiquette de rétention créée |NewComplianceTag |Un administrateur a créé une étiquette de rétention.|
| Stratégie de rétention créée |NewRetentionCompliancePolicy|Un administrateur a créé une stratégie de rétention.|
| Étendue adaptative supprimée | RemoveAdaptiveScope| L’administrateur a supprimé une étendue adaptative.|
| Paramètres supprimés d’une stratégie de rétention| RemoveRetentionComplianceRule<br/>| Un administrateur a supprimé les paramètres de configuration d’une stratégie de rétention. Cette activité est probablement enregistrée lorsqu’un administrateur supprime une stratégie de rétention ou exécute le cmdlet [Remove-RetentionComplianceRule](/powershell/module/exchange/Remove-RetentionComplianceRule).|
| Étiquette de rétention supprimée |RemoveComplianceTag | Un administrateur a supprimé une étiquette de rétention.|
| Stratégie de rétention supprimée |RemoveRetentionCompliancePolicy<br/> |Un administrateur a supprimé une stratégie de rétention. |
| Option d’enregistrement réglementaire activée pour les étiquettes de rétention<br/> |SetRestrictiveRetentionUI |Un administrateur a exécuté le cmdlet [RegulatoryComplianceUI](/powershell/module/exchange/set-regulatorycomplianceui) afin qu’un administrateur puisse ensuite sélectionner l’option de configuration de l’interface utilisateur pour une étiquette de rétention et identifier le contenu en tant qu’enregistrement réglementaire.|
| Étendue adaptative mise à jour | SetAdaptiveScope | L’administrateur a modifié la description ou la requête pour une étendue adaptative existante. |
| Paramètres mis à jour pour une stratégie de rétention | SetRetentionComplianceRule | L’administrateur a modifié les paramètres de rétention d’une stratégie de rétention existante. Les paramètres de rétention incluent la durée de conservation des éléments et ce qu’il advient des éléments à l’expiration de la période de rétention (comme la suppression d’éléments, la conservation des éléments ou leur conservation puis leur suppression). Cette activité correspond également à l’exécution du cmdlet [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule). |
| Étiquette de rétention mise à jour |SetComplianceTag  | Un administrateur a mis à jour une étiquette de rétention existante.|
| Stratégie de rétention mise à jour |SetRetentionCompliancePolicy |Un administrateur a mis à jour une stratégie de rétention existante. Les mises à jour qui déclenchent cet événement incluent l’ajout ou l’exclusion d’emplacements de contenu auxquels la stratégie de rétention est appliquée.|
||||

### <a name="briefing-email-activities"></a>Activités de récapitulatif des tâches par courrier électronique

Le tableau suivant répertorie les activités de l’e-mail de Récapitulatif des tâches qui sont enregistrées dans le journal d’audit Microsoft 365. Pour plus d’informations sur le courrier de Récapitulatif des tâches, consultez :

- [Présentation du courrier électronique de récapitulatif des tâches](/Briefing/be-overview)

- [Configurer le courrier électronique de récapitulatif des tâches](/Briefing/be-admin)

|**Nom convivial**|**Opération**|**Description**|
|:----|:-----|:-----|
|Paramètres de confidentialité de l’organisation mis à jour|UpdatedOrganizationBriefingSettings|Un administrateur met à jour les paramètres de confidentialité de l’organisation pour le courrier de récapitulatif des tâches. |
|Paramètres de confidentialité de l’utilisateur mis à jour|UpdatedUserBriefingSettings|Un administrateur met à jour les paramètres de confidentialité de l’utilisateur pour le courrier de récapitulatif des tâches.
||||

### <a name="myanalytics-activities"></a>Activités MyAnalytics

Le tableau suivant répertorie les activités dans MyAnalytics qui sont enregistrées dans le journal d’audit Microsoft 365. Pour plus d’informations sur MyAnalytics, consultez [MyAnalytics pour les administrateurs](/workplace-analytics/myanalytics/overview/mya-for-admins).

|**Nom convivial**|**Opération**|**Description**|
|:-----|:-----|:-----|
|Mise à jour des paramètres de l'organisation MyAnalytics|UpdatedOrganizationMyAnalyticsSettings|Un administrateur met à jour les paramètres au niveau de l’organisation pour MyAnalytics. |
|Mise à jour des paramètres MyAnalytics de l'utilisateur|UpdatedUserMyAnalyticsSettings|Un administrateur met à jour les paramètres utilisateur pour MyAnalytics.|
||||

### <a name="information-barriers-activities"></a>Activités des obstacles aux informations

Le tableau suivant répertorie les activités du cloisonnement de l’information qui sont enregistrées dans le journal d’audit Microsoft 365. Pour plus d’informations sur les obstacles à l’information, consultez [sur les obstacles aux informations dans Microsoft 365](information-barriers.md).

|**Nom convivial**|**Opération**|**Description**|
|:----------------|:------------|:--------------|
| Ajout de segments à un site | SegmentsAdded | Un administrateur général ou un propriétaire de site SharePoint a ajouté un ou plusieurs segments d’information qui empêchent l’accès à un site. |
| Modification de segments d'un site | SegmentsChanged | Un administrateur SharePoint ou un administrateur général a modifié un ou plusieurs segments de obstacles aux informations pour un site. |
| Suppression de segments d'un site | Segmentsremoved | Un administrateur SharePoint ou un administrateur général a supprimé un ou plusieurs segments de obstacles aux informations d’un site. |
||||

### <a name="disposition-review-activities"></a>Activités de la révision avant destruction

Le tableau suivant répertorie les activités d'un réviseur de disposition lorsqu'un élément atteint la fin de sa période de conservation configurée. Pour plus d'informations, consultez la section [Visualisation et élimination du contenu](disposition.md#viewing-and-disposing-of-content).

|**Nom convivial**|**Opération**|**Description**|
|:-----|:-----|:-----|
|Destruction approuvée|ApproveDisposal|Un réviseur de destruction a approuvé la destruction de l’élément pour le déplacer vers l’étape suivante de destruction. Si l’élément était la seule ou la dernière étape de la révision avant destruction, l’approbation de la destruction a marqué l’élément comme éligible pour la suppression définitive.|
|Étendue de la période de rétention|ExtendRetention|Un réviseur de destruction a étendu la période de rétention de l’élément.|
|Élément réétiqueté|RelabelItem|Un réviseur de destruction a de nouveau étiqueté l’étiquette de rétention.|
|Réviseurs ajoutés|AddReviewer|Un réviseur de destruction a ajouté un ou plusieurs autres utilisateurs à la phase d’examen de la révision avant destruction actuelle.|
||||

### <a name="communication-compliance-activities"></a>Activités de conformité des communications

Le tableau suivant répertorie les activités de conformité de la communication qui sont enregistrées dans le journal d’audit Microsoft 365. Pour plus d’informations, [voir En savoir plus sur la conformité des communications dans Microsoft 365](communication-compliance.md).

|**Nom convivial**|**Opération**|**Description**|
|:-----|:-----|:-----|
|Mise à jour de stratégie|SupervisionPolicyCreated, SupervisionPolicyUpdated, SupervisionPolicyDeleted|Un administrateur de conformité des communications a effectué une mise à jour de stratégie.|
|Correspondance de stratégie|SupervisionRuleMatch|Un utilisateur a envoyé un message qui correspond à la condition d’une stratégie.|
|Balise appliquée aux messages|SupervisoryReviewTag|Les balises sont appliquées aux messages ou les messages sont résolus.|
||||

### <a name="report-activities"></a>Activités de rapport

Le tableau suivant répertorie les activités des rapports d’utilisation enregistrés dans le journal d’audit Microsoft 365.

|**Nom convivial**|**Opération**|**Description**|
|:-----|:-----|:-----|
|Mise à jour des paramètres de confidentialité du rapport d’utilisation|UpdateUsageReportsPrivacySetting|Les paramètres de confidentialité des rapports d’utilisation ont été mis à jour par l’administrateur. |
||||

### <a name="exchange-admin-audit-log"></a>Journal d’audit de l’administrateur Exchange

La journalisation d’audit de l’administrateur Exchange (activée par défaut dans Microsoft 365) enregistre un événement dans le journal d’audit lorsqu’un administrateur (ou un utilisateur auquel des autorisations d’administration ont été attribuées) apporte une modification dans votre organisation Exchange. Les modifications apportées à l’aide du Centre d’administration Exchange ou en exécutant une cmdlet dans Exchange Online PowerShell sont enregistrées dans le journal d’audit de l’administrateur Exchange. Les applets de commande qui commencent par les verbes **Get-**, **Search-** ou **Test-** ne sont pas enregistrées dans le journal d’audit. Pour plus d’informations sur la journalisation d’audit de l’administrateur dans Exchange, voir [Journalisation d’audit de l’administrateur](/exchange/administrator-audit-logging-exchange-2013-help).

> [!IMPORTANT]
> Certaines cmdlets Exchange Online qui ne sont pas enregistrées dans le journal d’audit de l’administrateur Exchange (ou dans le journal d’audit). Bon nombre de ces applets de commande sont liées à la maintenance du service Exchange Online et sont exécutées par le personnel du centre de données Microsoft ou les comptes de service. Ces applets de commande ne sont pas enregistrées, car elles génèrent un grand nombre d’événements d’audit «bruyants». S’il existe une cmdlet Exchange Online qui n’est pas en cours d’audit, envoyez une demande de modification de conception (DCR) au Support Microsoft.

Voici quelques conseils pour rechercher des activités d’administrateur Exchange dans le journal d’audit :

- Pour renvoyer les entrées du journal d'audit de l'administrateur Exchange, vous devez sélectionner **Afficher les résultats pour toutes les activités** dans la liste **Activités**. Utilisez les zones de plage de dates et la liste **Utilisateurs** pour affiner les résultats de la recherche des cmdlets exécutées par un administrateur Exchange spécifique dans une plage de dates spécifique.

- Pour afficher les événements du journal d’audit de l’administrateur Exchange, cliquez sur la colonne **Activité** pour trier les noms de cmdlet par ordre alphabétique.

- Pour obtenir des informations sur les cmdlets exécutées, les paramètres et valeurs de paramètres utilisés et les objets affectés, vous devez exporter les résultats de recherche et sélectionner l’option **Télécharger tous les résultats**. Pour plus d’informations, voir [Exporter, configurer et afficher des enregistrements du journal d’audit](export-view-audit-log-records.md).

- Vous pouvez également utiliser la `Search-UnifiedAuditLog -RecordType ExchangeAdmin` commande dans Exchange Online PowerShell pour renvoyer uniquement les enregistrements d’audit du journal d’audit de l’administrateur Exchange. L’exécution de l’entrée de journal d’audit correspondante dans les résultats de la recherche peut prendre jusqu’à 30 minutes après l’exécution d’une applet de commande Exchange. Pour plus d’informations, voir [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog). Pour plus d’informations sur l’exportation des résultats de recherche renvoyés par l’applet de commande **Search-UnifiedAuditLog** vers un fichier CSV, voir la section «conseils pour l'exportation et l’affichage du journal d’audit» dans [exporter, configurer et afficher les enregistrements du journal d’audit.](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Vous pouvez également afficher les événements dans le journal d’audit de l’administrateur Exchange à l’aide du centre d’administration Exchange ou à l’aide de la fonction **Search-AdminAuditLog** dans Exchange Online PowerShell. Il s’agit d’un bon moyen de rechercher spécifiquement les activités effectuées par les administrateurs Exchange Online. Pour plus d’informations, voir :

  - [Consulter le journal d’audit de l’administrateur](/exchange/security-and-compliance/exchange-auditing-reports/view-administrator-audit-log)

  - [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog)

   Gardez à l’esprit que les mêmes activités d’administrateur Exchange sont enregistrées dans le journal d’audit de l’administrateur Exchange et dans le journal d’audit.

## <a name="frequently-asked-questions"></a>Foire aux questions

**Quels services Microsoft 365 font actuellement l’objet d’un audit ?**

Les services les plus utilisés tels que Exchange Online, SharePoint Online, OneDrive Entreprise, Azure Active Directory, Microsoft Teams, Dynamics 365, Defender pour Office 365 et Power BI font l’objet d’un audit. Pour obtenir la liste des services audités, voir le [ldébut de cet article](search-the-audit-log-in-security-and-compliance.md).

**Quelles activités sont auditées par le service d’audit dans Microsoft 365 ?**

Consultez la section [Activités auditées](#audited-activities) dans cet article pour obtenir la liste et la description des activités auditées.

**Combien de temps faut-il pour que l’enregistrement d’audit soit disponible une fois qu’un événement s’est produit ?**

Après la survenue d’un événement, l’apparition de l’entrée de journal d’audit correspondante dans les résultats de la recherche peut prendre entre 30 minutes et 24 heures. Pour plus d’informations sur la disponibilité des événements dans les différents services, consultez le tableau dans la section [Avant d’effectuer la recherche dans le journal d’audit](#before-you-search-the-audit-log) de cet article.

**Pendant combien de temps les enregistrements d’audit sont-ils conservés ?**

Comme indiqué précédemment, les enregistrements d’audit pour les activités effectuées par les utilisateurs ayant reçu une licence Office 365 E5 ou Microsoft E5 (ou les utilisateurs disposant d’une licence de composant additionnel Microsoft 365 E5) sont conservés pendant un an. Pour tous les autres abonnements prenant en charge la journalisation d’audit unifiée, les enregistrements d’audit sont conservés pendant 90 jours.

**Puis-je accéder aux données d’audit par programme ?**

Oui. L’API d’activité de gestion d’Office 365 est utilisée pour extraire les journaux d’audit par programme.  Pour commencer, consultez l’article relatif à la [prise en main des API de gestion Office 365](/office/office-365-management-api/get-started-with-office-365-management-apis).

**Existe-t-il d’autres méthodes pour obtenir des journaux d’audit autres que l’utilisation du centre de sécurité et conformité ou de l’API d’activité de gestion d’Office 365 ?**

Non. Ce sont les deux seuls moyens d'obtenir les données du service d'audit.

**Est-ce que je dois activer l’audit de chaque service pour lequel je souhaite capturer les journaux d’audit ?**

Dans la plupart des services, l’audit est activé par défaut une fois que vous avez activé l’audit pour votre organisation, comme décrit dans la section [Avant d’effectuer la recherche dans le journal d’audit](#before-you-search-the-audit-log) dans cet article.

**Le service d’audit prend-il en charge la suppression des doublons d’enregistrements ?**

Non. Le pipeline de service d’audit est presque en temps réel et ne peut donc pas prendre en charge la déduplication.

**Où sont stockées les données d’audit ?**

Nous avons actuellement des déploiements de pipeline d’audit dans les régions NA (Amérique du Nord), EMEA (Europe, Moyen-Orient et Afrique) et APAC (Asie-Pacifique). Les clients domiciliés dans ces régions verront leurs données d'audit stockées dans la région. Pour les client domiciliés dans de différentes régions, les données d'audit collectées de toutes les régions seront stockées uniquement dans la région du siège principal du client. Toutefois, il peut arriver que nous déplacions les données entre ces régions afin d’équilibrer la charge, uniquement lors de problèmes liés aux sites actifs. Lorsque nous effectuons ces activités, les données en transit sont chiffrées. 

**Les données d’audit sont-elles chiffrées ?**

Les données d’audit sont stockées dans les boîtes aux lettres Exchange (données au repos) situées dans la même région où le pipeline unifié d’audit est déployé. Les données de boîte aux lettres au repos ne sont pas cryptées par Exchange. Toutefois, le chiffrement de niveau service chiffre toutes les données de boîte aux lettres, car les serveurs Exchange dans les centres de données Microsoft sont chiffrés via BitLocker. Pour plus d’informations, voir [Chiffrement Microsoft 365 pour Skype Entreprise, OneDrive Entreprise, SharePoint Online et Exchange Online](/compliance/assurance/assurance-encryption-for-microsoft-365-services).

Les données en transit sont toujours chiffrées.
