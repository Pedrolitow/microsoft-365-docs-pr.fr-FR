---
title: 'Effectuer des recherches dans le journal d’audit depuis le Centre de sécurité et conformité '
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- Strat_O365_IP
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: 0d4d0f35-390b-4518-800e-0c7ec95e946c
description: Vous pouvez utiliser le Centre de sécurité et conformité Office 365 ou le Centre de conformité Microsoft 365 pour rechercher dans le journal d’audit unifié les activités des utilisateurs et des administrateurs de votre organisation.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: aa47cc0c460e77a6faadd5cb2ff7d46c62ed88ab
ms.sourcegitcommit: 20d1158c54a5058093eb8aac23d7e4dc68054688
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/21/2020
ms.locfileid: "49376653"
---
# <a name="search-the-audit-log-in-the-compliance-center"></a>Rechercher le journal d'audit dans le centre de conformité

Vous avez besoin de savoir si un utilisateur a consulté un document spécifique ou a supprimé un élément de sa boîte aux lettres ? Si c'est le cas, vous pouvez utiliser le Centre de conformité Microsoft 365 pour effectuer une recherche dans le journal d'audit unifié afin d'afficher l'activité des utilisateurs et des administrateurs de votre organisation. Pourquoi un journal d'audit unifié ? Parce que vous pouvez rechercher les types d'[activité des utilisateurs et des administrateurs](#audited-activities) suivants dans Microsoft 365 :

- Activité des utilisateurs dans SharePoint Online et OneDrive Entreprise

- Activité utilisateur dans Exchange Online (enregistrement d’audit de boîte aux lettres Exchange) 

- Activité des administrateurs dans SharePoint Online

- Activité des administrateurs dans Azure Active Directory (service d’annuaire pour Microsoft 365)

- Activité des administrateurs dans Exchange Online (journalisation d’audit de l’administrateur Exchange)

- Activités eDiscovery dans le Centre de conformité et sécurité

- Activités utilisateur et administrateur dans Power BI

- Activités utilisateur et administrateur dans Microsoft Teams

- Activités utilisateur et administrateur dans Dynamics 365

- Activités utilisateur et administrateur dans Yammer

- Activités utilisateur et administrateur dans Microsoft Power Automate

- Activités utilisateur et administrateur dans Microsoft Stream

- Activité d’analystes et d’administrateurs dans Microsoft Workplace Analytics

- Activités utilisateur et administrateur dans Microsoft Power Apps

- Activités utilisateur et administrateur dans Microsoft Forms

- Activité des utilisateurs et des administrateurs relative aux étiquettes de confidentialité pour les sites qui utilisent SharePoint Online ou Microsoft Teams

## <a name="requirements-to-search-the-audit-log"></a>Configuration requise pour effectuer une recherche dans le journal d’audit

Avant d'effectuer une recherche dans le journal d'audit, veuillez lire ce qui suit.

- Vous (ou un autre administrateur) devez d'abord activer la journalisation d'audit avant de pouvoir commencer la recherche dans le journal d'audit. Pour l'activer, cliquez sur **Activer l'audit** sur la page **Recherche dans le journal d'audit** dans le Centre de sécurité et de conformité. (Si vous ne voyez pas ce lien, cela signifie que l'audit a déjà été activé pour votre organisation.) Une fois que vous l'avez activé, un message s'affiche et vous indique que le journal d'audit est en cours de préparation et que vous pourrez lancer une recherche dans quelques heures, lorsque la préparation sera terminée. Cette opération n'est effectuée qu'une seule fois. Si vous souhaitez en savoir plus, consultez l'article [Activer ou désactiver la recherche dans le journal d'audit](turn-audit-log-search-on-or-off.md).

  > [!NOTE]
  > L'audit par défaut est en cours d'activation. En attendant, vous pouvez l'activer en suivant la procédure décrite précédemment.

- Vous devez disposer du rôle Journaux d'audit en lecture seule ou Journaux d'audit dans Exchange Online pour rechercher le journal d'audit. Par défaut, ces rôles sont attribués aux groupes de rôles Gestion de la conformité et Gestion de l'organisation sur la page **Autorisations** du centre d'administration Exchange. Notez que les administrateurs généraux dans Office 365 et Microsoft 365 sont automatiquement ajoutés en tant que membres du groupe de rôles Gestion de l'organisation dans Exchange Online. Pour donner à un utilisateur la possibilité de rechercher dans le journal d'audit avec le niveau minimum de privilèges, vous pouvez créer un groupe de rôles personnalisé dans Exchange Online, ajouter le rôle Journaux d'audit ou Journaux d'audit en lecture seule, puis ajouter l'utilisateur en tant que membre du nouveau groupe de rôles. Si vous souhaitez en savoir plus, consultez l'article [Gérer les groupes de rôles dans Exchange Online.](https://go.microsoft.com/fwlink/p/?LinkID=730688)

  > [!IMPORTANT]
  > Si vous attribuez à un utilisateur le rôle Journaux d'audit en lecture seule ou Journaux d'audit sur la page **Autorisations** du Centre de sécurité et de conformité, il ne pourra pas rechercher dans le journal d'audit. Vous devez attribuer les autorisations dans Exchange Online. Cela est dû au fait que la cmdlet sous-jacente utilisée pour rechercher le journal d'audit est une cmdlet Exchange Online.

- Lorsqu'une activité auditée est effectuée par un utilisateur ou un administrateur, un enregistrement d'audit est généré et stocké dans le journal d'audit de votre organisation. La durée de conservation d'un enregistrement d'audit (et de recherche dans le journal d'audit) dépend de votre abonnement Office 365 ou Microsoft 365 Entreprise, et plus particulièrement du type de licence attribuée à des utilisateurs spécifiques.

  - Pour les utilisateurs auxquels une licence Office 365 E5 ou Microsoft 365 E5 a été attribuée (ou les utilisateurs avec une licence complémentaire Microsoft 365 E5 Conformité ou Microsoft 365 E5 eDiscovery et Audit), les enregistrements d'audit pour l'activité Azure Active Directory, Exchange et SharePoint sont conservés pour un année par défaut. Les organisations peuvent également créer des stratégies de rétention des journaux d'audit pour conserver les enregistrements d'audit des activités d'autres services pendant une période maximale d'un an. Si vous souhaitez en savoir plus, consultez l'article [Gérer les stratégies de rétention des journaux d'audit](audit-log-retention-policies.md).

    > [!NOTE]
    > Si votre organisation a participé au programme de préversion privée pour la conservation des enregistrements d'audit sur une période d'un an, la durée de conservation des enregistrements d'audit générés avant la date de lancement de la disponibilité générale ne sera pas réinitialisée.

  - Pour les utilisateurs auxquels est attribuée une autre licence Office 365 ou Microsoft 365 (non E5), les enregistrements d'audit sont conservés pendant 90 jours. Pour obtenir la liste des abonnements Office 365 et Microsoft 365 prenant en charge la journalisation d'audit unifiée, consultez [la description du service du centre de sécurité et de conformité](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-securitycompliance-center).

    > [!NOTE]
    > Même lorsque l'audit de boîte aux lettres, activé par défaut, est activé, vous remarquerez peut-être que les événements d'audit de boîte aux lettres pour certains utilisateurs ne sont pas trouvés dans les recherches du journal d'audit dans le centre de sécurité et de conformité ou via l'API Activité de gestion Office 365. Si vous souhaitez en savoir plus, consultez l'article [En savoir plus sur la journalisation d'audit des boîtes aux lettres](enable-mailbox-auditing.md#more-information).

- Si vous souhaitez désactiver la recherche dans le journal d'audit pour votre organisation, vous pouvez exécuter la commande suivante dans une session PowerShell distante connectée à votre organisation Exchange Online :

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
  ```

    Pour réactiver la recherche d’audit, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :

  ```powershell
  Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
  ```

  Si vous souhaitez en savoir plus, consultez l'article [Désactiver la recherche dans le journal d'audit](turn-audit-log-search-on-or-off.md).

- Comme indiqué précédemment, la cmdlet sous-jacente utilisée pour rechercher le journal d'audit est une cmdlet Exchange Online. Cette cmdlet est **Search-UnifiedAuditLog**. Cela signifie que vous pouvez utiliser cette cmdlet pour effectuer une **Recherche dans le journal d'audit** au lieu d'utiliser la page Recherche du journal d'audit dans le Centre de sécurité et de conformité. Vous devez exécuter cette cmdlet dans une session PowerShell distante connectée à votre organisation Exchange Online. Si vous souhaitez en savoir plus, consultez l'article [Search-UnifiedAuditLog](https://go.microsoft.com/fwlink/p/?linkid=834776).

  Si vous souhaitez en savoir plus sur l'exportation des résultats de la recherche renvoyés par la cmdlet **Search-UnifiedAuditLog** vers un fichier CSV, consultez la section « Conseils pour l'exportation et l'affichage du journal d'audit » dans l'article [Exporter, configurer et afficher les enregistrements du journal d'audit.](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Si vous souhaitez télécharger les données du journal d'audit de façon programmée, nous vous recommandons d'utiliser l'API Activité de gestion Office 365 plutôt qu'un script PowerShell. L'API Activité de gestion Office 365 est un service web REST que vous pouvez utiliser pour développer des solutions de surveillance des opérations, de la sécurité et de la conformité pour votre organisation. Si vous souhaitez en savoir plus, consultez l'article [Référence de l'API Activité de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-reference).

- Après un événement, l'apparition de l'enregistrement de journal d'audit correspondant dans les résultats de la recherche peut prendre jusqu'à 30 minutes, voir 24 heures. Le tableau suivant répertorie les délais en fonction des services dans Office 365.

  |Service ou fonctionnalité Microsoft 365|30 minutes|24 heures|
  |:-----|:-----:|:-----:|
  |Defender pour Office 365 et veille contre les menaces|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Azure Active Directory (événements de connexion utilisateur)||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  |Azure Active Directory (événements administrateur)||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  |Protection contre la perte de données|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Dynamics 365 CRM||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  |eDiscovery|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Exchange Online|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Microsoft Power Automate||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  |Microsoft Project|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Microsoft Stream|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Microsoft Teams|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Power Apps||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  |Power BI|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Centre de sécurité et conformité|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Étiquettes de confidentialité||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  |Sharepoint Online et OneDrive Entreprise|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Workplace Analytics|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Yammer||![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)||
  |Microsoft Forms|![Coche](../media/f3b4c351-17d9-42d9-8540-e48e01779b31.png)|
  ||||

- Azure Active Directory (Azure AD) est le service d'annuaire de Office 365. Le journal d'audit unifié contient les activités des utilisateurs, des groupes, des applications, des domaines et des annuaires, effectuées dans le centre d'administration Microsoft 365 ou dans le portail de gestion Azure. Pour obtenir la liste complète des événements Azure AD, consultez l'article [Rapports d'activité d'audit dans le portail Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=616549).

- La journalisation d'audit pour Power BI n'est pas activée par défaut. Pour rechercher des activités Power BI dans le journal d'audit, vous devez activer l'audit dans le portail d'administration Power BI. Pour obtenir des instructions, consultez la section « Journaux d'audit » dans le [portail d'administration Power BI](https://docs.microsoft.com/power-bi/service-admin-portal#audit-logs).

## <a name="search-the-audit-log"></a>Effectuer une recherche dans le journal d'audit

> [!NOTE]
> Un problème est survenu avec les activités Azure AD indisponibles dans l'outil de recherche dans le journal d'audit du 22 octobre 2020 au 6 novembre 2020. Ces activités incluent les activités d'administration des utilisateurs Azure AD, les activités d'administration des groupes, les activités d'administration des applications, les activités d'administration des rôles et les activités d'administration de l'annuaire. Les événements manquants pour la période d'impact seront disponibles dans les prochains jours et devraient être terminés au plus tard le 20 novembre 2020. Dans certains cas, les clients peuvent remarquer des données d'événements en double pour les événements générés entre le 26 octobre 2020 et le 5 novembre 2020.
    
Pour effectuer une recherche dans le journal d'audit dans Office 365, vous devez procéder comme suit.

[Étape 1 : effectuer une recherche dans le journal d’audit](#step-1-run-an-audit-log-search)

[Étape 2 : consulter les résultats de la recherche](#step-2-view-the-search-results)

[Étape 3 : filtrer les résultats de la recherche](#step-3-filter-the-search-results)

[Étape 4 : exporter les résultats de la recherche dans un fichier](#step-4-export-the-search-results-to-a-file)

### <a name="step-1-run-an-audit-log-search"></a>Étape 1 : effectuer une recherche dans le journal d’audit

1. Accédez à [https://protection.office.com](https://protection.office.com).

    > [!TIP]
    > Utilisez une session de navigation privée (pas une session normale) pour accéder au Centre de sécurité et de conformité, car cela empêchera l'utilisation des informations d'identification avec lesquelles vous êtes actuellement connecté. Pour ouvrir une session de navigation InPrivate dans Internet Explorer ou Microsoft Edge, appuyez simplement sur CTRL+MAJ+P. Pour ouvrir une session de navigation privée dans Google Chrome (appelée fenêtre de navigation privée), appuyez sur CTRL+MAJ+N.

2. Connectez-vous à l'aide de votre compte professionnel ou scolaire.

3. Dans le volet gauche du Centre de sécurité et de conformité, cliquez sur **Recherche** puis sur **Recherche du journal d’audit**.

    La page **Recherche dans le journal d’audit** s’affiche.

    ![Configurez les critères, puis cliquez sur Rechercher pour générer un rapport](../media/8639d09c-2843-44e4-8b4b-9f45974ff7f1.png)

    > [!NOTE]
    > Vous devez activer la journalisation d'audit avant d'effectuer une recherche dans le journal d'audit. Si le lien **Commencer à enregistrer les activités des utilisateurs et des administrateurs** apparaît, cliquez dessus pour activer l'audit. Si ce lien n'apparaît pas, l'audit est déjà été activé pour votre organisation.

4. Configurez les critères de recherche suivants : 

   1. **Activités** : cliquez sur la liste déroulante pour afficher les activités que vous pouvez rechercher. Les activités des utilisateurs et des administrateurs sont organisées en groupes d'activités connexes. Vous pouvez sélectionner des activités spécifiques ou cliquer sur le nom du groupe d'activités pour sélectionner toutes les activités du groupe. Vous pouvez également cliquer sur une activité sélectionnée pour effacer la sélection. Après avoir exécuté la recherche, seules les entrées du journal d'audit pour les activités sélectionnées sont affichées. Si vous sélectionnez **Afficher les résultats** pour toutes les activités, les résultats de toutes les activités effectuées par l'utilisateur ou le groupe d'utilisateurs sélectionné s'affichent.

      Plus de 100 activités des utilisateurs et des administrateurs sont enregistrées dans le journal d'audit. Cliquez sur l'onglet **Activités auditées** de la section de cet article pour voir les descriptions de chaque activité dans chacun des différents services.

   1. **Date de début** et **Date de fin** : les sept derniers jours sont sélectionnés par défaut. Sélectionnez une plage de dates et d'heures pour afficher les événements qui se sont produits pendant cette période. La date et l'heure sont présentées au format Temps universel coordonné (UTC). La plage de dates maximale que vous pouvez spécifier est de 90 jours. Une erreur s'affiche si la plage de dates sélectionnée est supérieure à 90 jours.

      > [!TIP]
      > Si vous utilisez la plage de dates maximale de 90 jours, sélectionnez l'heure actuelle pour l'option **Date de début**. Dans le cas contraire, un message d'erreur indiquant que la date de début est antérieure à la date de fin apparaît. Si vous avez activé l'audit au cours des 90 derniers jours, la plage de dates maximale ne peut pas commencer avant la date à laquelle l'audit a été activé.

   1. **Utilisateurs** : cliquez sur cette case, puis sélectionnez un ou plusieurs utilisateurs pour lesquels afficher les résultats de la recherche. Les entrées du journal d'audit pour l'activité sélectionnée, exécutée par les utilisateurs que vous sélectionnez dans cette zone, sont affichées dans la liste des résultats. Laissez cette zone vide pour renvoyer les entrées de tous les utilisateurs (et comptes de service) de votre organisation.

   1. **Fichier, dossier ou site** : saisissez tout ou une partie du nom d'un fichier ou d'un dossier pour rechercher une activité liée au fichier du dossier contenant le mot-clé spécifié. Vous pouvez également spécifier l'URL d'un fichier ou d'un dossier. Si vous utilisez une URL, assurez-vous de saisir le chemin d'accès complet de l'URL. Si vous saisissez une partie de l'URL, n'incluez pas de caractères spéciaux ou d'espaces.

      Laissez cette zone vide pour renvoyer les entrées de tous les fichiers et dossiers de votre organisation.

      > [!TIP]
      >
      > - Si vous recherchez toutes les activités concernant un **site**, ajoutez le symbole générique (\*) après l’URL pour renvoyer toutes les entrées de ce site ; par exemple, `"https://contoso-my.sharepoint.com/personal*"`
      >
      > - Si vous recherchez toutes les activités associées à **un fichier**, ajoutez le symbole générique (\*) avant le nom de fichier pour renvoyer toutes les entrées de ce fichier, par exemple, `"*Customer_Profitability_Sample.csv"`.

5. Cliquez sur **Rechercher** pour effectuer la recherche à l'aide de vos critères de recherche.

   Les résultats de la recherche sont chargés et après quelques instants, ils s'affichent sous **Résultats**. Lorsque la recherche est terminée, le nombre de résultats trouvés s'affiche. Un maximum de 5 000 événements seront affichés dans le volet **Résultats** par incréments de 150 événements. Si plus de 5 000 événements répondent aux critères de recherche, les 5 000 événements les plus récents sont affichés.

   ![Le nombre de résultats s'affiche une fois la recherche terminée](../media/986216f1-ca2f-4747-9480-e232b5bf094c.png)

#### <a name="tips-for-searching-the-audit-log"></a>Conseils pour effectuer une recherche dans le journal d'audit

- Vous pouvez sélectionner des activités spécifiques à rechercher en cliquant sur le nom de l'activité. Vous pouvez également rechercher toutes les activités d'un groupe (telles que les **Activités de fichiers et de dossiers**) en cliquant sur le nom du groupe. Si une activité est sélectionnée, vous pouvez cliquer dessus pour annuler la sélection. Vous pouvez également utiliser la zone de recherche pour afficher les activités qui contiennent le mot-clé que vous saisissez.

  ![Cliquez sur le nom d'un groupe d'activités pour sélectionner toutes les activités](../media/3cde97cb-6f35-47c0-8612-ecd9c6ac36a3.png)

- Vous devez sélectionner **Afficher les résultats de toutes les activités** dans la liste **Activités** pour afficher les événements du journal d'audit de l'administrateur Exchange. Les événements de ce journal d'audit affichent un nom de cmdlet (par exemple, **Set-Mailbox**) dans la colonne **Activité** des résultats. Si vous souhaitez en savoir plus, cliquez sur l'onglet **Activités auditées** de cette rubrique, puis sur **Activités des administrateurs Exchange**.

  De même, certaines activités d'audit n'ont pas d'élément correspondant dans la liste **Activités**. Si vous connaissez le nom de l'opération pour ces activités, vous pouvez rechercher toutes les activités, puis filtrer les résultats en tapant le nom de l'opération dans la zone de la colonne **Activité**. Consultez la section [Étape 3 : filtrer les résultats de la recherche](#step-3-filter-the-search-results) pour en savoir plus sur le filtrage des résultats.

- Cliquez sur **Effacer** pour effacer les critères de recherche actuels. La plage de dates reprend la valeur par défaut des sept derniers jours. Vous pouvez également cliquer sur **Effacer tout pour afficher les résultats correspondant à toutes les activités** afin d'annuler toutes les activités sélectionnées.

- Si 5 000 résultats sont trouvés, vous pouvez probablement supposer qu'il y a plus de 5 000 événements répondant aux critères de recherche. Vous pouvez soit affiner les critères de recherche et réexécuter la recherche pour afficher moins de résultats, soit exporter tous les résultats de la recherche en sélectionnant **Exporter les résultats** \> **Télécharger tous les résultats**.

### <a name="step-2-view-the-search-results"></a>Étape 2 : consulter les résultats de la recherche

Les résultats d'une recherche dans le journal d'audit apparaissent sous **Résultats** sur la page **Recherche dans le journal d'audit**. Comme indiqué précédemment, un maximum de 5 000 événements (les plus récents) peut s'afficher, par incréments de 150. Pour afficher davantage d'événements, vous pouvez utiliser la barre de défilement du volet **Résultats** ou appuyer sur **Maj+Fin** afin d'afficher les 150 événements suivants.

Les résultats contiennent les informations suivantes sur chaque événement renvoyé par la recherche :

- **Date** : la date et l'heure (au format UTC) auxquelles l'événement s'est produit.

- **Adresse IP** : l'adresse IP de l'appareil qui a été utilisée lors de la journalisation de l'activité. L'adresse IP s'affiche au format d'adresse IPv4 ou IPv6.

   > [!NOTE]
  > Pour certains services, la valeur affichée dans ce champ peut être l'adresse IP d'une application approuvée (par exemple, les applications Office sur le web) appelant le service au nom d'un utilisateur et non l'adresse IP de l'appareil utilisé par la personne qui effectué l'activité. En outre, pour l'activité d'administration (ou l'activité effectuée par un compte système) pour les événements liés à Azure Active Directory, l'adresse IP n'est pas enregistrée et la valeur affichée dans ce champ est `null`.

- **Utilisateur** : utilisateur (ou compte de service) qui a effectué l'action ayant déclenché l'événement.

- **Activité** : l'activité effectuée par l'utilisateur. Cette valeur correspond aux activités que vous avez sélectionnées dans la liste déroulante **Activités**. Pour un événement du journal d'audit de l'administrateur Exchange, la valeur de cette colonne est une cmdlet Exchange.

- **Élément** : l'objet qui a été créé ou modifié suite à l'activité correspondante. Par exemple, le fichier qui a été affiché ou modifié ou le compte d'utilisateur qui a été mis à jour. Certaines activités n'ont pas de valeur dans cette colonne.

- **Informations** : Informations supplémentaires sur une activité. Cette fois encore, certaines activités n'ont pas de valeur.

> [!TIP]
> Cliquez sur un en-tête de colonne sous **Résultats** pour trier les résultats. Vous pouvez trier les résultats par ordre alphabétique croissant ou décroissant. Cliquez sur l'en-tête **Date** pour trier les résultats du plus ancien au plus récent, ou du plus récent au plus ancien.

#### <a name="view-the-details-for-a-specific-event"></a>Afficher les détails d'un événement spécifique

Vous pouvez afficher plus de détails sur un événement en cliquant sur l'enregistrement de l'événement dans la liste des résultats de la recherche. Une page **Détails** s'affiche et contient les propriétés détaillées de l'enregistrement de l'événement. Les propriétés affichées dépendent du service dans lequel l'événement se produit. Pour afficher ces détails, cliquez sur **Informations supplémentaires**. Pour obtenir des descriptions, consultez l'article [Propriétés détaillées dans le journal d'audit](detailed-properties-in-the-office-365-audit-log.md).

![Cliquez sur Informations supplémentaires pour afficher les propriétés détaillées de l'enregistrement de l'événement du journal d'audit](../media/6df582ae-d339-4735-b1a6-80914fb77a08.png)

### <a name="step-3-filter-the-search-results"></a>Étape 3 : filtrer les résultats de la recherche

Vous pouvez également filtrer les résultats d'une recherche dans le journal d'audit. Cette fonctionnalité permet de filtrer rapidement les résultats pour un utilisateur ou une activité spécifique. Vous pouvez créer une recherche large au départ, puis filtrer rapidement les résultats pour afficher des événements spécifiques. Vous pouvez ensuite affiner les critères de recherche, puis relancer la recherche pour renvoyer un jeu de résultats plus petit et concis.

Pour filtrer les résultats :

1. Effectuez une recherche dans le journal d’audit.

2. Lorsque les résultats sont affichés, cliquez sur **Filtrer les résultats**.

   Les zones de mot clé apparaissent sous chaque en-tête de colonne.

3. Cliquez sur l'une des cases sous un en-tête de colonne et saisissez un mot ou une phrase, en fonction de la colonne sur laquelle vous filtrez. Les résultats se réajusteront dynamiquement pour afficher les événements correspondant à votre filtre.

   ![Tapez un mot dans le filtre pour afficher les événements correspondant au filtre](../media/542dc323-a997-402c-934b-cc5e218e50bc.png)

4. Pour effacer un filtre, cliquez sur le **X** dans la zone de filtre, ou cliquez sur **Masquer le filtrage**.

> [!TIP]
> Pour afficher les événements du journal d'audit de l'administrateur Exchange, tapez un **-** (tiret) dans la zone du filtre **Activité**. Cela affichera les noms des cmdlets, qui sont affichés dans la colonne **Activité** pour les événements des administrateurs Exchange. Ensuite, vous pouvez trier les noms des cmdlets par ordre alphabétique.

### <a name="step-4-export-the-search-results-to-a-file"></a>Étape 4 : exporter les résultats de la recherche dans un fichier

Vous pouvez exporter les résultats d'une recherche dans le journal d'audit vers un fichier de valeurs séparées par des virgules (CSV) sur votre ordinateur local. Vous pouvez ouvrir ce fichier dans Microsoft Excel et utiliser des fonctionnalités telles que la recherche, le tri, le filtrage et le fractionnement d'une seule colonne (qui contient plusieurs propriétés) en plusieurs colonnes.

1. Effectuez une recherche dans le journal d'audit, puis modifiez les critères de recherche jusqu'à obtenir les résultats souhaités.

2. Cliquez sur **Exporter les résultats**, puis sélectionnez l'une des options suivantes :

   - **Enregistrer les résultats chargés** : choisissez cette option pour exporter uniquement les entrées affichées sous **Résultats** sur la page **Recherche du journal d'audit**. Le fichier CSV téléchargé contient les mêmes colonnes (et données) affichées sur la page (date, utilisateur, activité, élément et détails). Une colonne supplémentaire (nommée **Plus**) est incluse dans le fichier CSV qui contient plus d'informations sur l'entrée du journal d'audit. Étant donné que vous exportez les mêmes résultats qui sont chargés (et visibles) sur la page **Recherche du journal d'audit**, un maximum de 5 000 entrées sont exportées.

   - **Télécharger tous les résultats** : choisissez cette option pour exporter toutes les entrées du journal d'audit qui répondent aux critères de recherche. Pour un grand ensemble de résultats de recherche, choisissez cette option pour télécharger toutes les entrées du journal d'audit en plus des 5 000 enregistrements d'audit qui peuvent être affichés sur la page **Recherche du journal d'audit**. Cette option télécharge les données brutes du journal d'audit dans un fichier CSV et contient des informations supplémentaires à partir de l'entrée du journal d'audit dans une colonne nommée **AuditData**. Le téléchargement du fichier peut prendre plus de temps si vous choisissez cette option d'exportation car le fichier peut être beaucoup plus volumineux que celui qui a été téléchargé si vous choisissez l'autre option.

     > [!IMPORTANT]
     > Vous pouvez télécharger un maximum de 50 000 entrées dans un fichier .csv à partir d'une seule recherche dans le journal d'audit. Si 50 000 résultats sont téléchargés dans le fichier .csv, vous pouvez partir du principe que plus de 50 000 événements remplissent les critères de recherche. Pour exporter davantage de résultats, essayez d'utiliser une plage de dates pour réduire le nombre d'entrées du journal d'audit. Vous devrez peut-être effectuer plusieurs recherches avec des plages de dates plus réduites pour exporter plus de 50 000 entrées.

3. Une fois que vous avez sélectionné une option d'exportation, un message apparaît en bas de la fenêtre. Il vous invite à ouvrir le fichier .csv, à l'enregistrer dans le dossier Téléchargements ou à l'enregistrer dans un dossier spécifique.

#### <a name="more-information-about-exporting-and-viewing-audit-log-search-results"></a>Informations supplémentaires sur l'exportation et l'affichage des résultats de recherche dans le journal d'audit

- Si vous téléchargez tous les résultats de la recherche, le fichier CSV contient une colonne nommée **AuditData**, qui contient des informations supplémentaires sur chaque événement. Les données de cette colonne se composent d'un objet JSON qui contient plusieurs propriétés de l'enregistrement du journal d'audit. Chaque paire *propriété : valeur* de l'objet JSON est séparée par une virgule. Vous pouvez utiliser l'outil de transformation JSON dans l'éditeur Power Query dans Excel pour diviser la colonne **AuditData** en plusieurs colonnes afin que chaque propriété de l'objet JSON ait sa propre colonne. Cela vous permet de trier et de filtrer une ou plusieurs de ces propriétés. Si vous souhaitez obtenir des instructions pas à pas sur l'utilisation de l'éditeur Power Query pour transformer l'objet JSON, consultez l'article [Exporter, configurer et afficher les enregistrements du journal d'audit](export-view-audit-log-records.md).

  Après avoir divisé la colonne **AuditData**, vous pouvez filtrer la colonne **Opérations** pour afficher les propriétés détaillées pour un type d'activité spécifique.

- L'option **Télécharger tous les résultats** télécharge les données brutes du journal d'audit vers un fichier CSV. Ce fichier contient des noms de colonne différents (CreationDate, UserIds, Operation, AuditData) de ceux du fichier téléchargé si vous sélectionnez l'option **Enregistrer les résultats chargés**. Les valeurs des deux fichiers CSV différents pour la même activité peuvent également être différentes. Par exemple, l'activité de la colonne **Action** du fichier CSV peut avoir une valeur différente du nom « facile à retenir » affiché dans la colonne **Activité** de la page **Recherche dans le journal d'audit**. Par exemple, MailboxLogin vs Utilisateur connecté à la boîte aux lettres.

- Lorsque vous téléchargez tous les résultats d'une requête de recherche qui contient des événements provenant de différents services, la colonne **AuditData** du fichier CSV contient des propriétés différentes selon le service dans lequel l'action a été effectuée. Par exemple, les entrées des journaux d'audit Exchange et Azure AD incluent une propriété nommé **ResultStatus** qui indique si l'action a réussi ou non. Cette propriété n'est pas incluse pour les événements dans SharePoint. De même, les événements SharePoint ont une propriété qui identifie l'URL du site pour les activités liées aux fichiers et aux dossiers. Pour atténuer ce comportement, vous pouvez utiliser différentes recherches pour exporter les résultats des activités à partir d'un seul service.

  Pour obtenir une description des propriétés répertoriées dans la colonne **AuditData** du fichier .csv lorsque vous téléchargez tous les résultats, et du service auquel s'applique chacune d'elles, consultez l'article [Propriétés détaillées dans le journal d'audit](detailed-properties-in-the-office-365-audit-log.md).

## <a name="audited-activities"></a>Activités auditées

Les tableaux de cette section décrivent les activités qui sont auditées dans Office 365. Vous pouvez rechercher ces événements en effectuant une recherche dans le journal d'audit dans le centre de sécurité et de conformité.

Ces tableaux regroupent les activités liées ou les activités d'un service spécifique. Les tableaux incluent le nom facile à retenir affiché dans la liste déroulante **Activités** et le nom de l'opération correspondante qui apparaît dans les informations détaillées d'un enregistrement d'audit et dans le fichier CSV lorsque vous exportez les résultats de la recherche. Pour obtenir une description des informations détaillées, consultez l'article [Propriétés détaillées dans le journal d'audit](detailed-properties-in-the-office-365-audit-log.md).

Pour accéder à un tableau spécifique, cliquez sur l'un des liens suivants.

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
        [Activités dans Power BI](#power-bi-activities)
    :::column-end:::
    :::column:::
        [Microsoft Workplace Analytics](#microsoft-workplace-analytics-activities)
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
        [Activités administrateur Exchange](#exchange-admin-audit-log)
    :::column-end:::
:::row-end:::

### <a name="file-and-page-activities"></a>Activités des fichiers et pages

Le tableau suivant décrit les activités des fichiers et pages dans SharePoint Online et OneDrive Entreprise.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Fichier consulté|FileAccessed|Le compte d’utilisateur ou système consulte un fichier.|
|(aucun)|FileAccessedExtended|Cet événement est lié à l'activité « Fichier consulté » (FileAccessed). Un événement FileAccessedExtended est enregistré lorsque la même personne accède à un fichier pendant une période prolongée (jusqu'à 3 heures). <br/><br/> L'objectif de la journalisation des événements FileAccessedExtended consiste à réduire le nombre d'événements FileAccessed enregistrés lorsqu'un fichier est consulté de manière continue. Cela permet de réduire le bruit généré par l'enregistrement de plusieurs événements FileAccessed pour ce qui est en fait l'activité d'un seul et même utilisateur et vous permet de vous concentrer sur l'événement FileAccessed initial (plus important).|
|Étiquette de rétention modifiée pour un fichier|ComplianceSettingChanged|Une étiquette de rétention a été appliquée à un document ou supprimée de celui-ci. Cet événement est déclenché lorsqu'une étiquette de rétention est appliquée manuellement ou automatiquement à un message.|
|État de l'enregistrement modifié sur verrouillé|LockRecord|L'état d'enregistrement d'une étiquette de rétention qui classe un document comme enregistrement a été verrouillé. Cela signifie que le document ne peut pas être modifié ou supprimé. Seuls les utilisateurs ayant au moins l'autorisation de contributeur pour un site peuvent modifier le statut d'enregistrement d'un document.|
|État de l'enregistrement modifié sur déverrouillé|UnlockRecord|L'état d'enregistrement d'une étiquette de rétention qui classe un document comme enregistrement a été déverrouillé. Cela signifie que le document peut être modifié ou supprimé. Seuls les utilisateurs ayant au moins l'autorisation de contributeur pour un site peuvent modifier le statut d'enregistrement d'un document.|
|Fichier archivé|FileCheckedIn|Un utilisateur archive un document qu’il a extrait d’une bibliothèque de documents.|
|Fichier extrait|FileCheckedOut|Un utilisateur extrait un document d’une bibliothèque de documents. Les utilisateurs peuvent extraire et modifier les documents partagés avec eux.|
|Fichier copié|FileCopied|Un utilisateur copie un document à partir d’un site. Le fichier copié peut être enregistré dans un autre dossier sur le site.|
|Fichier supprimé|FileDeleted|Un utilisateur supprime un document d’un site.|
|Fichier supprimé de la Corbeille|FileDeletedFirstStageRecycleBin|Un utilisateur supprime un fichier de la Corbeille d’un site.|
|Fichier supprimé de la Corbeille second niveau|FileDeletedSecondStageRecycleBin|Un utilisateur supprime un fichier de la Corbeille second niveau d’un site.|
|Fichier étant identifié comme un enregistrement supprimé|RecordDelete|Un document marqué comme enregistrement a été supprimé. Un document est considéré comme un enregistrement lorsqu'une étiquette de rétention qui marque le contenu comme un enregistrement est appliquée au document.|
|Correspondance incorrecte de la confidentialité des documents détectée|DocumentSensitivityMismatchDetected|L'utilisateur télécharge un document sur un site protégé par une étiquette de confidentialité et le document a une étiquette de confidentialité de priorité plus élevée que l'étiquette de confidentialité appliquée au site. Par exemple, un document étiqueté comme Confidentiel est téléchargé sur un site étiqueté comme Général.<br/><br/> Cet événement n'est pas déclenché si le document a une étiquette de confidentialité de priorité inférieure à l'étiquette de confidentialité appliquée au site. Par exemple, un document étiqueté comme Général est téléchargé sur un site étiqueté comme Confidentiel. Si vous souhaitez en savoir plus sur la priorité des étiquettes de confidentialité, consultez l'article [Priorité des étiquettes (l'ordre est important)](sensitivity-labels.md#label-priority-order-matters).|
|Logiciel malveillant détecté dans le fichier|FileMalwareDetected|Le moteur antivirus de SharePoint détecte un programme malveillant dans un fichier.|
|Extraction de fichier ignorée|FileCheckOutDiscarded|Un utilisateur ignore (ou annule) un fichier extrait. Les modifications qu’il a apportées au fichier le temps de son extraction sont ignorées et ne sont pas enregistrées dans la version du document dans la bibliothèque de documents.|
|Fichier téléchargé|FileDownloaded|Un utilisateur télécharge un document à partir d’un site.|
|Fichier modifié|FileModified|Le compte d’utilisateur ou système modifie le contenu ou les propriétés d’un document sur un site.|
|(aucun)|FileModifiedExtended|Cet événement est lié à l'activité « Fichier modifié » (FileModified). Un événement FileModifiedExtended est enregistré lorsque la même personne modifie un fichier pendant une période prolongée (jusqu'à 3 heures). <br/><br/> L'objectif de la journalisation des événements FileModifiedExtended consiste à réduire le nombre d'événements FileModified enregistrés lorsqu'un fichier est modifié de manière continue. Cela permet de réduire le bruit généré par l'enregistrement de plusieurs événements FileModified pour ce qui est en fait l'activité d'un seul et même utilisateur et vous permet de vous concentrer sur l'événement FileModified initial (plus important).|
|Fichier déplacé|FileMoved|Un utilisateur déplace un document de son emplacement actuel sur un site vers un nouvel emplacement.|
|(aucun)|FilePreviewed|L'utilisateur affiche l'aperçu des fichiers sur un site SharePoint ou OneDrive Entreprise. Ces événements se produisent généralement dans des volumes élevés basés sur une seule activité, comme l'affichage d'une galerie d'images.|
|Requête de recherche effectuée|SearchQueryPerformed|Le compte utilisateur ou le compte système effectue une recherche dans SharePoint ou OneDrive Entreprise. Certains scénarios courants dans lesquels un compte de service effectue une requête de recherche incluent l'application d'une stratégie de rétention et de conservation eDiscovery aux sites et aux comptes OneDrive, et l'application automatique d'étiquettes de rétention ou de confidentialité au contenu du site.|
|Recyclage de toutes les versions mineures du fichier|FileVersionsAllMinorsRecycled|L’utilisateur supprime toutes les versions mineures de l’historique des versions d’un fichier. Les versions supprimées sont déplacées vers la Corbeille du site.|
|Recyclage de toutes les versions du fichier|FileVersionsAllRecycled|L’utilisateur supprime toutes les versions de l’historique des versions d’un fichier. Les versions supprimées sont déplacées vers la Corbeille du site.|
|Recyclage d’une version du fichier|FileVersionRecycled|L’utilisateur supprime une version de l’historique des versions d’un fichier. La version supprimée est déplacée vers la Corbeille du site.|
|Fichier renommé|FileRenamed|Un utilisateur renomme un document sur un site.|
|Fichier restauré|FileRestored|Un utilisateur restaure un document à partir de la Corbeille d’un site.|
|Fichier téléchargé|FileUploaded|Un utilisateur charge un document vers un dossier sur un site.|
|Page affichée|PageViewed|Un utilisateur affiche une page sur un site. Ceci n’inclut pas l’utilisation d’un navigateur web pour afficher les fichiers dans une bibliothèque de documents.|
|(aucun)|PageViewedExtended|Cet événement est lié à l'activité « Page affichée » (PageViewed). Un événement PageViewedExtended est enregistré lorsque la même personne affiche une page web pendant une période prolongée (jusqu'à 3 heures). <br/><br/> L'objectif de la journalisation des événements PageViewedExtended consiste à réduire le nombre d'événements PageViewed enregistrés lorsqu'une page est affichée de manière continue. Cela permet de réduire le bruit généré par l'enregistrement de plusieurs événements PageViewed pour ce qui est en fait l'activité d'un seul et même utilisateur et vous permet de vous concentrer sur l'événement PageViewed initial (plus important).|
|Affichage signalé par le client|ClientViewSignaled|Le client d'un utilisateur (comme un site web ou une application mobile) a signalé que la page indiquée a été consultée par l'utilisateur. Cette activité est souvent enregistrée à la suite d'un événement PagePrefetched pour une page.<br/><br/>**REMARQUE** : les événements ClientViewSignaled étant signalés par le client, plutôt que par le serveur, il est possible que l'événement ne soit pas enregistré par le serveur et, par conséquent, qu'il n'apparaisse pas dans le journal d'audit. Il est également possible que les informations dans l'enregistrement d'audit ne soient pas fiables. Toutefois, comme l'identité de l'utilisateur est validée par le jeton utilisé pour créer le signal, l'identité de l'utilisateur répertoriée dans l'enregistrement d'audit correspondant est exacte. |
|(aucun)|PagePrefetched|Le client d'un utilisateur (comme un site web ou une application mobile) a demandé la page indiquée pour permettre d'améliorer les performances si l'utilisateur y accède. Cet événement est enregistré pour indiquer que le contenu de la page a été diffusé au client de l'utilisateur. Cet événement n'est pas une indication définitive que l'utilisateur a accédé à la page. <br/><br/> Lorsque le contenu de la page est rendu par le client (conformément à la demande de l'utilisateur), un événement ClientViewSignaled doit être généré. Tous les clients ne prennent pas en charge l'indication d'une pré-extraction, et par conséquent, certaines activités pré-extraites peuvent, à la place, être enregistrées en tant qu'événements PageViewed.|
||||

#### <a name="frequently-asked-questions-about-fileaccessed-and-filepreviewed-events"></a>Foire aux questions sur les événements FileAccessed et FilePreviewed

**Des activités non-utilisateur peuvent-elles déclencher des enregistrements d'audit FilePreviewed contenant un agent utilisateur tel que « OneDriveMpc-Transform_Thumbnail » ?**

Nous n'avons pas connaissance de scénarios dans lesquels des actions non utilisateur génèrent des événements comme ceux-ci. Les actions des utilisateurs, comme l'ouverture d'une carte de profil utilisateur (en cliquant sur leur nom ou leur adresse e-mail dans un message dans Outlook sur le web) génèrent des événements similaires.

**Les appels à OneDriveMpc-Transform_Thumbnail sont-ils toujours déclenchés intentionnellement par l'utilisateur ?**

Non, mais des événements similaires peuvent être enregistrés à la suite de la pré-extraction du navigateur.

**Si un événement FilePreviewed provenant d'une adresse IP enregistrée par Microsoft s'affiche, cela signifie-t-il que l'aperçu s'affiche sur l'écran de l'appareil de l'utilisateur ?**

Non. L'événement a peut-être été enregistré à la suite d'une pré-extraction du navigateur.

**Y a-t-il des scénarios dans lesquels un utilisateur consultant un aperçu d'un document génère des événements FileAccessed ?**

Les événements FilePreviewed et FileAccessed indiquent que l'appel d'un utilisateur a conduit à une lecture du fichier (ou à une lecture d'un rendu miniature du fichier). Bien que ces événements soient destinés à s'aligner sur l'intention d'aperçu par rapport à l'intention d'accès, la distinction d'événement n'est pas une garantie de l'intention de l'utilisateur.

#### <a name="the-appsharepoint-user-in-audit-records"></a>L'utilisateur app\@sharepoint dans des enregistrements d'audit

Dans les enregistrements d'audit pour certaines activités de fichier (et d'autres activités liées à SharePoint), vous pouvez constater que l'utilisateur qui a effectué l'activité (identifié dans les champs User et UserId) est app@sharepoint. Cela indique que « l'utilisateur » qui a effectué l'activité était une application. Dans ce cas, l'application a reçu des autorisations dans SharePoint pour effectuer des actions à l'échelle de l'organisation (telles que rechercher un site SharePoint ou un compte OneDrive) pour le compte d'un utilisateur, d'un administrateur ou d'un service. Ce processus d'octroi d'autorisations à une application est appelé accès *Application SharePoint uniquement*. Cela indique que l'authentification présentée à SharePoint pour effectuer une action a été effectuée par une application, et non un utilisateur. C'est pourquoi l'utilisateur app@sharepoint est identifié dans certains enregistrements d'audit. Si vous souhaitez en savoir plus, consultez l'article [Accorder l'accès avec l'application SharePoint uniquement](https://docs.microsoft.com/sharepoint/dev/solution-guidance/security-apponly-azureacs).

Par exemple, app@sharepoint est souvent identifié comme étant l'utilisateur pour les événements « Requête de recherche effectuée » et « Fichier consulté ». En effet, une application avec un accès Application SharePoint uniquement dans votre organisation effectue des requêtes de recherche et accède aux fichiers lors de l'application de stratégies de rétention aux sites et aux comptes OneDrive.

Voici d'autres scénarios dans lesquels app@sharepoint peut être identifié, dans un enregistrement d'audit, en tant qu'utilisateur ayant effectué une activité :

- Groupes Microsoft 365. Lorsqu'un utilisateur ou un administrateur crée un nouveau groupe, des enregistrements d'audit sont générés pour créer une collection de sites, mettre à jour des listes et ajouter des membres à un groupe SharePoint. Ces tâches sont effectuées par une application au nom de l'utilisateur qui a créé le groupe.

- Microsoft Teams. À l'instar des groupes Microsoft 365, les enregistrements d'audit sont générés pour créer une collection de sites, mettre à jour des listes et ajouter des membres à un groupe SharePoint lorsqu'une équipe est créée.

- Fonctionnalités de conformité. Lorsqu'un administrateur implémente des fonctionnalités de conformité, comme des stratégies de rétention, des conservations eDiscovery et des étiquettes de confidentialité appliquées automatiquement.

Dans ces scénarios et d'autres, vous remarquerez également que plusieurs enregistrements d'audit avec app@sharepoint en tant qu'utilisateur spécifié ont été créés dans un court laps de temps, souvent à quelques secondes d'intervalle. Cela indique également qu'ils ont probablement été déclenchés par la même tâche initiée par l'utilisateur. En outre, les champs ApplicationDisplayName et EventData dans l'enregistrement d'audit peuvent vous aider à identifier le scénario ou l'application qui a déclenché l'événement.

### <a name="folder-activities"></a>Activités des dossiers

Le tableau suivant décrit les activités de dossier dans SharePoint Online et OneDrive Entreprise. Comme expliqué précédemment, les enregistrements d'audit pour certaines activités SharePoint indiqueront que l'utilisateur app@sharepoint a effectué l'activité pour le compte de l'utilisateur ou de l'administrateur qui a lancé l'action. Si vous souhaitez en savoir plus, consultez la section [L'utilisateur app\@sharepoint dans des enregistrements d'audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Dossier copié|FolderCopied|Un utilisateur copie un dossier à partir d’un site vers un autre emplacement dans SharePoint ou OneDrive Entreprise.|
|Dossier créé|FolderCreated|Un utilisateur crée un dossier sur un site.|
|Dossier supprimé|FolderDeleted|Un utilisateur supprime un dossier d’un site.|
|Dossier supprimé de la Corbeille|FolderDeletedFirstStageRecycleBin|Un utilisateur supprime un dossier de la Corbeille sur un site.|
|Dossier supprimé de la Corbeille second niveau|FolderDeletedSecondStageRecycleBin|Un utilisateur supprime un dossier de la Corbeille second niveau sur un site.|
|Dossier modifié|FolderModified|Un utilisateur modifie un dossier sur un site. Cela inclut la modification des métadonnées du dossier (par exemple, modification des balises et propriétés).|
|Dossier déplacé|FolderMoved|Un utilisateur déplace un dossier vers un autre emplacement sur un site.|
|Dossier renommé|FolderRenamed|Un utilisateur renomme un dossier sur un site.|
|Dossier restauré|FolderRestored|Un utilisateur restaure un dossier supprimé de la Corbeille sur un site.|
||||

### <a name="sharepoint-list-activities"></a>Activités des liste SharePoint

Le tableau suivant décrit les activités liées à l'interaction des utilisateurs avec des listes et des éléments de liste dans SharePoint Online. Comme expliqué précédemment, les enregistrements d'audit pour certaines activités SharePoint indiqueront que l'utilisateur app@sharepoint a effectué l'activité pour le compte de l'utilisateur ou de l'administrateur qui a lancé l'action. Si vous souhaitez en savoir plus, consultez la section [L'utilisateur app\@sharepoint dans des enregistrements d'audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Liste créée|ListCreated|Un utilisateur a créé une liste SharePoint.|
|Colonne de liste créée|ListColumnCreated|Un utilisateur a créé une colonne de liste SharePoint. Une colonne de liste est une colonne attachée à une ou plusieurs listes SharePoint.|
|Type de contenu de liste créé|ListContentTypeCreated|Un utilisateur a créé un type de contenu de liste. Un type de contenu de liste est un type de contenu associé à une ou plusieurs listes SharePoint.|
|Élément de liste créé|ListItemCreated|Un utilisateur a créé un élément dans une liste SharePoint existante.|
|Colonne de site créée|SiteColumnCreated|Un utilisateur a créé une colonne de site SharePoint. Une colonne de site est une colonne qui n'est pas associée à une liste. Une colonne de site est également une structure de métadonnées qui peut être utilisée par n'importe quelle liste dans un site web donné.|
|Type de contenu de site créé|ContentType du site créé|Un utilisateur a créé un type de contenu de site. Un type de contenu de site est un type de contenu associé au site parent.|
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
||||

### <a name="sharing-and-access-request-activities"></a>Activités de demande d'accès et de partage

Le tableau suivant décrit les activités de partage de l'utilisateur et de demande d'accès dans SharePoint Online et OneDrive Entreprise. Pour les événements de partage, la colonne **Détails** sous **Résultats** identifie le nom de l'utilisateur ou du groupe avec lequel l'élément a été partagé et si cet utilisateur ou groupe est membre ou invité de votre organisation. Si vous souhaitez en savoir plus, consultez l'article [Utiliser l'audit de partage dans le journal d'audit](use-sharing-auditing.md).

> [!NOTE]
> Les utilisateurs peuvent être des *membres* ou des *invités* en fonction de la propriété UserType de l'objet utilisateur. Un membre est généralement un employé et un invité est généralement un collaborateur extérieur à votre organisation. Lorsqu'un utilisateur accepte une invitation de partage (et ne fait pas déjà partie de votre organisation), un compte d'invité est créé pour lui dans l'annuaire de votre organisation. Une fois que l'utilisateur invité a un compte dans votre annuaire, les ressources peuvent être partagées directement avec lui (sans avoir besoin d'une invitation).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Ajout d’un niveau d’autorisation à la collection de sites|PermissionLevelAdded|Un niveau d’autorisation a été ajouté à une collection de sites.|
|Demande d’accès acceptée|AccessRequestAccepted|Une demande d’accès à un site, un dossier ou un document a été acceptée et l’utilisateur à l’origine de la demande s’est vu octroyé l’accès.|
|Invitation de partage acceptée|SharingInvitationAccepted|Un utilisateur (membre ou invité) a accepté une invitation de partage et s’est vu octroyer l’accès à une ressource. Cet événement inclut des informations sur l’utilisateur invité et l’adresse de courrier utilisée pour accepter l’invitation (ils peuvent être différents). Cette activité est souvent accompagnée d’un deuxième événement qui décrit la manière dont l’utilisateur s’est vu octroyer l’accès à la ressource (par exemple, en ajoutant l’utilisateur à un groupe ayant accès à la ressource). |
|Invitation de partage bloquée|SharingInvitationBlocked|Une invitation de partage envoyée par un utilisateur de votre organisation est bloquée par une stratégie de partage externe qui autorise ou refuse le partage externe en fonction du domaine de l’utilisateur cible. Dans ce cas, l’invitation de partage a été bloquée car : <br/> Le domaine de l'utilisateur cible n'est pas inclus dans la liste des domaines autorisés. <br/> Ou <br/> Le domaine de l’utilisateur cible est inclus dans la liste des domaines bloqués. <br/> Pour plus d’informations sur l’autorisation ou le blocage du partage externe en fonction des domaines, voir [Restreindre le partage des domaines dans SharePoint Online et OneDrive Entreprise](https://docs.microsoft.com/sharepoint/restricted-domains-sharing).|
|Demande d’accès créée|AccessRequestCreated|Un utilisateur demande l’accès à un site, un dossier ou un document auquel il n’est pas autorisé à accéder.|
|Création d’un lien d’entreprise partageable |CompanyLinkCreated|Un utilisateur a créé un lien à l'échelle de l'entreprise vers une ressource. Les liens à l'échelle de l'entreprise ne peuvent être utilisés que par les membres de votre organisation. Ils ne peuvent pas être utilisés par les invités.|
|Lien anonyme créé|AnonymousLinkCreated|Un utilisateur a créé un lien anonyme vers une ressource. Toute personne disposant de ce lien peut accéder à la ressource sans être authentifiée.|
|Lien sécurisé créé|SecureLinkCreated|Un lien de partage sécurisé a été créé sur cet élément.|
|Invitation de partage créée|SharingInvitationCreated|Un utilisateur a partagé une ressource dans SharePoint Online ou OneDrive Entreprise avec un utilisateur qui ne figure pas dans l’annuaire de votre organisation.|
|Lien sécurisé supprimé|SecureLinkDeleted|Un lien de partage sécurisé a été supprimé.|
|Demande d’accès refusée |AccessRequestDenied|Une demande d’accès à un site, un dossier ou un document a été refusée.|
|Suppression d’un lien d’entreprise partageable|CompanyLinkRemoved|Un utilisateur a supprimé un lien à l’échelle de l’entreprise vers une ressource. Le lien ne peut plus être utilisé pour accéder à la ressource.|
|Suppression d’un lien anonyme |AnonymousLinkRemoved|Un utilisateur a supprimé un lien anonyme vers une ressource. Le lien ne peut plus être utilisé pour accéder à la ressource.|
|Fichier, dossier ou site partagé|SharingSet|L'utilisateur (membre ou invité) a partagé un fichier, un dossier ou un site dans SharePoint ou OneDrive Entreprise avec un utilisateur dans l'annuaire de votre organisation. La valeur de la colonne **Détail** de cette activité identifie le nom de l'utilisateur avec lequel la ressource a été partagée et si cet utilisateur est un membre ou un invité.<br/><br/> Cette activité est souvent accompagnée d'un deuxième événement qui décrit comment l'utilisateur a obtenu l'accès à la ressource. Par exemple, l'ajout de l'utilisateur à un groupe qui a accès à la ressource.|
|Demande d'accès mise à jour|AccessRequestUpdated|Une demande d’accès à un élément a été mise à jour.|
|Mise à jour d’un lien anonyme |AnonymousLinkUpdated|Un utilisateur a mis à jour un lien anonyme vers une ressource. Le champ mise à jour est inclus dans la propriété EventData lorsque vous exportez les résultats de recherche.|
|Invitation de partage mise à jour|SharingInvitationUpdated|Une invitation de partage externe a été mise à jour.|
|Utilisation d’un lien anonyme |AnonymousLinkUsed|Un utilisateur anonyme a accédé à une ressource en utilisant un lien anonyme. L'identité de l'utilisateur peut être inconnue, mais vous pouvez obtenir d'autres informations comme l'adresse IP de l'utilisateur.|
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
|Ordinateur autorisé à synchroniser des fichiers|ManagedSyncClientAllowed|Un utilisateur a réussi à établir une relation de synchronisation avec un site. La relation de synchronisation est établie, car l'ordinateur de l'utilisateur est membre d'un domaine qui a été ajouté à la liste des domaines (*liste des destinataires approuvés*) pouvant accéder aux bibliothèques de documents dans votre organisation. <br/><br/> Si vous souhaitez en savoir plus sur cette fonctionnalité, consultez l'article [Utiliser des cmdlets Windows PowerShell pour activer la synchronisation de OneDrive pour les domaines figurant dans la liste des destinataires approuvés](https://go.microsoft.com/fwlink/p/?LinkID=534609).|
|Ordinateur non autorisé à synchroniser des fichiers|UnmanagedSyncClientBlocked|L'utilisateur essaie d'établir une relation de synchronisation avec un site à partir d'un ordinateur qui n'est pas membre du domaine de votre organisation ou qui est membre d'un domaine qui n'a pas été ajouté à la liste des domaines (appelée *liste des destinataires approuvés*) qui peuvent accéder aux bibliothèques de documents de votre organisation. La relation de synchronisation n'est pas autorisée et l'ordinateur de l'utilisateur ne peut pas synchroniser, télécharger ou charger des fichiers sur une bibliothèque de documents.<br/><br/> Si vous souhaitez en savoir plus sur cette fonctionnalité, consultez l'article [Utiliser des cmdlets Windows PowerShell pour activer la synchronisation de OneDrive pour les domaines figurant dans la liste des destinataires approuvés](https://go.microsoft.com/fwlink/p/?LinkID=534609).|
|Fichiers téléchargés sur l’ordinateur|FileSyncDownloadedFull|Un utilisateur établit une relation de synchronisation et télécharge des fichiers pour la première fois sur son ordinateur à partir d’une bibliothèque de documents.|
|Modifications du fichier téléchargées sur l’ordinateur|FileSyncDownloadedPartial|Un utilisateur télécharge des modifications apportées à des fichiers à partir d’une bibliothèque de documents. Cette activité indique que les modifications apportées à des fichiers dans la bibliothèque de documents ont été téléchargées sur l’ordinateur de l’utilisateur. Seules les modifications ont été téléchargées, car la bibliothèque de documents a été téléchargée précédemment par l’utilisateur (comme indiqué par l’activité **Fichiers téléchargés sur l’ordinateur**).|
|Fichiers téléchargés dans la bibliothèque de documents|FileSyncUploadedFull|Un utilisateur établit une relation de synchronisation et charge des fichiers pour la première fois à partir de son ordinateur dans une bibliothèque de documents.|
|Modifications du fichier téléchargées dans la bibliothèque de documents|FileSyncUploadedPartial|L'utilisateur réussit à télécharger les modifications apportées aux fichiers dans une bibliothèque de documents. Cet événement indique que toutes les modifications apportées à la version locale d'un fichier à partir d'une bibliothèque de documents sont téléchargées avec succès dans la bibliothèque de documents. Seules les modifications sont téléchargées car ces fichiers ont été précédemment téléchargés par l'utilisateur (comme indiqué par l'activité **Fichiers téléchargés vers la bibliothèque de documents**).|
||||

### <a name="site-permissions-activities"></a>Activités d'autorisations de site

Le tableau suivant répertorie les événements liés à l'attribution d'autorisations dans SharePoint et à l'utilisation de groupes pour accorder (et révoquer) l'accès aux sites. Comme expliqué précédemment, les enregistrements d'audit pour certaines activités SharePoint indiqueront que l'utilisateur app@sharepoint a effectué l'activité pour le compte de l'utilisateur ou de l'administrateur qui a lancé l'action. Si vous souhaitez en savoir plus, consultez la section [L'utilisateur app\@sharepoint dans des enregistrements d'audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Administrateur de collection de site ajouté|SiteCollectionAdminAdded|L'administrateur ou le propriétaire de la collection de sites ajoute une personne en tant qu'administrateur de la collection de sites pour un site. Les administrateurs de collection de sites disposent d'autorisations de contrôle total pour la collection de sites et tous les sous-sites. Cette activité est également enregistrée lorsqu'un administrateur se donne lui-même accès au compte OneDrive d'un utilisateur (en modifiant le profil utilisateur dans le Centre d'administration SharePoint ou en [utilisant le Centre d'administration Microsoft 365](https://docs.microsoft.com/office365/admin/add-users/get-access-to-and-back-up-a-former-user-s-data)).|
|Utilisateur ou groupe ajouté au groupe SharePoint|AddedToGroup|L'utilisateur a ajouté un membre ou un invité à un groupe SharePoint. Cela peut être une action intentionnelle ou le résultat d'une autre activité, comme un événement de partage.|
|Fin de l'héritage des niveaux d'autorisation|PermissionLevelsInheritanceBroken|Un élément a été modifié afin qu’il n’hérite plus des niveaux d’autorisation de son parent.|
|Fin de l’héritage de partage|SharingInheritanceBroken|Un élément a été modifié afin qu’il n’hérite plus des autorisations de partage de son parent.|
|Groupe créé|GroupAdded|L'administrateur ou le propriétaire du site crée un groupe pour un site ou effectue une tâche qui entraîne la création d'un groupe. Par exemple, la première fois qu'un utilisateur crée un lien pour partager un fichier, un groupe système est ajouté au site OneDrive Entreprise de l'utilisateur. Cet événement peut également venir d'un utilisateur créant un lien avec des autorisations de modification vers un fichier partagé.|
|Groupe supprimé|GroupRemoved|Un utilisateur supprime un groupe d’un site.|
|Paramètre de demande d’accès modifié|WebRequestAccessModified|Les paramètres de demande d’accès ont été modifiés sur un site.|
|Paramètre «les membres peuvent partagés» modifié|WebMembersCanShareModified|Le paramètre **les membres peuvent partager** a été modifié sur un site.|
|Modification du niveau d’autorisation sur une collection de sites|PermissionLevelModified|Un niveau d’autorisation a été modifié sur une collection de sites.|
|Autorisations de site modifiées|SitePermissionsModified|L'administrateur ou le propriétaire du site (ou le compte système) modifie le niveau d'autorisation attribué à un groupe sur un site. Cette activité est également enregistrée si toutes les autorisations sont supprimées d'un groupe.<br/><br/> **REMARQUE** : cette opération est obsolète dans SharePoint Online. Pour rechercher des événements associés, vous pouvez rechercher d'autres activités liées aux autorisations, comme **Administrateur de collection de sites ajouté**, **Utilisateur ou groupe ajouté à un groupe SharePoint**, **Utilisateur autorisé à créer des groupes**, **Groupe créé**, et **Groupe supprimé.**|
|Niveau d'autorisation dans une collection de sites supprimé|PermissionLevelRemoved|Un niveau d’autorisation a été supprimé d’une collection de sites.|
|Administrateur de collection de site supprimé|SiteCollectionAdminRemoved|L'administrateur ou le propriétaire de la collection de sites supprime une personne en tant qu'administrateur de la collection de sites pour un site. Cette activité est également enregistrée lorsqu'un administrateur se supprime de la liste des administrateurs de collection de sites pour le compte OneDrive d'un utilisateur (en modifiant le profil utilisateur dans le Centre d'administration SharePoint). Pour renvoyer cette activité dans les résultats de la recherche du journal d'audit, vous devez rechercher toutes les activités.|
|Utilisateur ou groupe supprimé d'un groupe SharePoint|RemovedFromGroup|L'utilisateur a supprimé un membre ou un invité d'un groupe SharePoint. Cela peut être une action intentionnelle ou le résultat d'une autre activité, comme un événement de non-partage.|
|Autorisations d'administrateur de site demandées|SiteAdminChangeRequest|Un utilisateur demande à être ajouté en tant qu'administrateur de collection de sites pour une collection de sites. Les administrateurs de collection de sites disposent d'autorisations de contrôle total pour la collection de sites et tous les sous-sites.|
|Restauration de l'héritage de partage|SharingInheritanceReset|Une modification a été apportée afin qu’un élément hérite des autorisations de partage de son parent.|
|Groupe mis à jour|GroupUpdated|Un administrateur ou propriétaire de site modifie les paramètres d'un groupe pour un site. Cela peut inclure la modification du nom du groupe, des autorisations d'affichage ou de modification d'appartenance au groupe, et du mode de gestion des demandes d'appartenance.|
||||

### <a name="site-administration-activities"></a>Activités d'administration des sites

Le tableau suivant répertorie les événements résultant des tâches d'administration de site dans SharePoint Online. Comme expliqué précédemment, les enregistrements d'audit pour certaines activités SharePoint indiqueront que l'utilisateur app@sharepoint a effectué l'activité pour le compte de l'utilisateur ou de l'administrateur qui a lancé l'action. Si vous souhaitez en savoir plus, consultez la section [L'utilisateur app\@sharepoint dans des enregistrements d'audit](#the-appsharepoint-user-in-audit-records).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Ajout de l’emplacement de données autorisé|AllowedDataLocationAdded|Un administrateur SharePoint ou général a ajouté un emplacement de données autorisé dans un environnement à plusieurs emplacements géographiques.|
|Agent utilisateur exempté ajouté|ExemptUserAgentSet|Un administrateur SharePoint ou général a ajouté un agent utilisateur à la liste des agents utilisateurs exemptés dans le centre d’administration SharePoint.|
|Ajout d’un administrateur d’emplacement géographique|GeoAdminAdded|Un administrateur SharePoint ou général a ajouté un utilisateur en tant qu’administrateur géo d’un emplacement.|
|Utilisateur autorisé à créer des groupes|AllowGroupCreationSet|Un administrateur ou propriétaire de site ajoute un niveau d’autorisation à un site qui permet à un utilisateur auquel cette autorisation est octroyée de créer un groupe pour ce site.|
|Annulation du géodéplacement d’un site|SiteGeoMoveCancelled|Un administrateur SharePoint ou général annule un déplacement géographique de site SharePoint ou OneDrive. La fonctionnalité Multigéographique permet à une organisation de s'étendre sur plusieurs zones géographiques de centres de données Microsoft, appelées zones géographiques. Si vous souhaitez en savoir plus, consultez l'article [Fonctionnalités multigéographiques dans OneDrive et SharePoint Online](https://go.microsoft.com/fwlink/?linkid=860840).|
|Stratégie de partage modifiée|SharingPolicyChanged|Un administrateur SharePoint ou général a modifié une stratégie de partage SharePoint à l'aide du portail d'administration Microsoft 365, du portail d'administration SharePoint ou de l'environnement de ligne de commande SharePoint Online Management Shell. Toutes les modifications des paramètres de la stratégie de partage dans votre organisation sont enregistrées. La stratégie qui a été modifiée est identifiée dans le champ **ModifiedProperties** dans les propriétés détaillées de l'enregistrement de l'événement.|
|Stratégie d'accès aux appareils modifiée|DeviceAccessPolicyChanged|Un administrateur SharePoint ou général a modifié la stratégie des appareils non gérés pour votre organisation. Cette stratégie contrôle l'accès à SharePoint, OneDrive et Microsoft 365 à partir d'appareils qui ne sont pas joints à votre organisation. La configuration de cette stratégie nécessite un abonnement Enterprise Mobility & Security. Si vous souhaitez en savoir plus, consultez l'article [Contrôler l'accès à partir des appareils non gérés](https://docs.microsoft.com/sharepoint/control-access-from-unmanaged-devices).|
|Agents utilisateurs exclus modifiés|CustomizeExemptUsers|Un administrateur SharePoint ou général a personnalisé la liste des agents utilisateurs exemptés dans le Centre d'administration SharePoint. Vous pouvez spécifier les agents utilisateurs qui ne recevront pas de page web entière à indexer. Cela signifie que lorsqu'un agent utilisateur que vous avez spécifié comme exclus rencontre un formulaire InfoPath, le formulaire est renvoyé sous forme de fichier XML, au lieu d'une page web entière. Cela accélère l'indexation des formulaires InfoPath.|
|Stratégie d'accès au réseau modifiée|NetworkAccessPolicyChanged|Un administrateur SharePoint ou général a modifié la stratégie d'accès basée sur l'emplacement (également appelée limite de réseau approuvée) dans le Centre d'administration SharePoint ou à l'aide de SharePoint Online PowerShell. Ce type de stratégie détermine qui peut accéder aux ressources SharePoint et OneDrive dans votre organisation en fonction des plages d'adresses IP autorisées que vous spécifiez. Si vous souhaitez en savoir plus, consultez l'article [Contrôler l'accès aux données SharePoint Online et OneDrive en fonction de l'emplacement réseau](https://docs.microsoft.com/sharepoint/control-access-based-on-network-location).|
|Déplacement géographique de site effectué|SiteGeoMoveCompleted|Un déplacement géographique de site planifié par un administrateur général de votre organisation a été effectué avec succès. La fonctionnalité multigéographique permet à une organisation de s'étendre sur plusieurs zones géographiques de centres de données Microsoft, appelées zones géographiques. Si vous souhaitez en savoir plus, consultez l'article [Fonctionnalités multigéographiques dans OneDrive et SharePoint Online dans Office 365](https://go.microsoft.com/fwlink/?linkid=860840).|
|Connexion Envoyé à créée|SendToConnectionAdded|Un administrateur SharePoint ou général crée une nouvelle connexion Envoyer à sur la page de gestion des enregistrements dans le Centre d'administration SharePoint. Une connexion Envoyer à spécifie les paramètres d'un référentiel de documents ou d'un centre d'enregistrements. Lorsque vous créez une connexion Envoyer à, un organisateur de contenu peut soumettre des documents à l'emplacement spécifié.|
|Collection de sites créée|SiteCollectionCreated|Un administrateur SharePoint ou global crée une collection de sites dans votre organisation SharePoint Online ou un utilisateur configure son site OneDrive Entreprise.|
|Site hub orphelin supprimé|HubSiteOrphanHubDeleted|Un administrateur SharePoint ou général a supprimé un hub orphelin, qui est un hub auquel aucun site n'est associé. Un hub orphelin est probablement dû à la suppression de l'hub d'origine.|
|Connexion Envoyé à supprimée|SendToConnectionRemoved|L’administrateur SharePoint ou général supprime une connexion Envoyer à sur la page de gestion des enregistrements dans le Centre d’administration SharePoint.|
|Site supprimé|SiteDeleted|L’administrateur de site supprime un site.|
|Aperçu du document activé|PreviewModeEnabledSet|Un administrateur de site active l’aperçu des documents pour un site.|
|Flux de travail hérité activé|LegacyWorkflowEnabledSet|L'administrateur ou le propriétaire du site ajoute le type de contenu Tâche de flux de travail SharePoint 2013 au site. Les administrateurs généraux peuvent également activer les flux de travail pour l'ensemble de l'organisation dans le Centre d'administration SharePoint.|
|Office à la demande activé|OfficeOnDemandSet|L'administrateur de site active Office à la demande, qui permet aux utilisateurs d'accéder à la dernière version des applications de bureau Office. Office à la demande est activé dans le Centre d'administration SharePoint et nécessite un abonnement Microsoft 365 qui comprend des applications Office complètes et installées.|
|Source de résultats activée pour les recherches de personnes|PeopleResultsScopeSet|Un administrateur de site crée l’origine des résultats pour les recherches de personnes pour un site.|
|Flux RSS activés|NewsFeedEnabledSet|L'administrateur ou le propriétaire du site active les flux RSS d'un site. Les administrateurs généraux peuvent activer les flux RSS pour l'ensemble de l'organisation dans le Centre d'administration SharePoint.|
|Site joint au site hub|HubSiteJoined|Un propriétaire de site associe son site à un site concentrateur.|
|Site hub inscrit|HubSiteRegistered|Un administrateur SharePoint ou général crée un site hub. Le site est donc inscrits en tant que site hub.|
|Emplacement des données autorisées supprimé|AllowedDataLocationDeleted|Un administrateur SharePoint ou général a supprimé un emplacement de données autorisé dans un environnement à plusieurs emplacements géographiques.|
|Administrateur d’emplacement géographique supprimé|GeoAdminDeleted|Un administrateur SharePoint ou général a supprimé un utilisateur en tant qu’administrateur géo d’un emplacement.|
|Site renommé|SiteRenamed|Un administrateur ou propriétaire de site renomme un site.|
|Planification du géodéplacement d’un site|SiteGeoMoveScheduled|Un administrateur SharePoint ou général planifie un déplacement géographique de site SharePoint ou OneDrive. La fonctionnalité multigéographique permet à une organisation de s'étendre sur plusieurs zones géographiques de centres de données Microsoft, appelées zones géographiques. Si vous souhaitez en savoir plus, consultez l'article [Fonctionnalités multigéographiques dans OneDrive et SharePoint Online dans Office 365](https://go.microsoft.com/fwlink/?linkid=860840).|
|Site hôte défini|HostSiteSet|Un administrateur SharePoint ou général modifie le site désigné pour l’hébergement de sites personnels ou OneDrive Entreprise.|
|Définir un quota de stockage pour un emplacement géographique|GeoQuotaAllocated|Un administrateur SharePoint ou général a configuré un quota de stockage pour un environnement à plusieurs emplacements géographiques.|
|Site disjoint d’un site concentrateur|HubSiteUnjoined|Un propriétaire de site dissocie son site d’un site concentrateur.|
|Site concentrateur non enregistré|HubSiteUnregistered|Un administrateur SharePoint ou général annule l'inscription d'un site en tant que site hub. Lorsqu'un site hub n'est pas inscrit, il ne fonctionne plus comme un site hub.|
||||

### <a name="exchange-mailbox-activities"></a>Activités de la boîte aux lettres Exchange

Le tableau suivant répertorie les activités qui peuvent être enregistrées par la journalisation d'audit de boîte aux lettres. Les activités de boîte aux lettres effectuées par le propriétaire de la boîte aux lettres, un utilisateur délégué ou un administrateur sont automatiquement enregistrées dans le journal d'audit pendant 90 jours maximum. Il est possible pour un administrateur de désactiver la journalisation d'audit des boîtes aux lettres pour tous les utilisateurs de votre organisation. Dans ce cas, aucune action de boîte aux lettres pour aucun utilisateur n'est enregistrée. Si vous souhaitez en savoir plus, consultez l'article [Gérer l'audit des boîtes aux lettres](enable-mailbox-auditing.md).

 Vous pouvez également rechercher des activités de boîte aux lettres à l'aide de la cmdlet [Search-MailboxAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-mailboxauditlog) dans Exchange Online PowerShell.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Éléments de boîte aux lettres consultés|MailItemsAccessed|Les messages ont été lus ou consultés dans la boîte aux lettres. Les enregistrements d'audit pour cette activité sont déclenchés de deux manières : lorsqu'un client de messagerie (comme Outlook) effectue une opération de liaison sur les messages ou lorsque des protocoles de messagerie (comme Exchange ActiveSync ou IMAP) synchronisent des éléments dans un dossier de messagerie. Cette activité n'est enregistrée que pour les utilisateurs disposant d'une licence Office 365 ou Microsoft 365 E5. L'analyse des enregistrements d'audit pour cette activité est utile lors de l'enquête sur un compte de messagerie compromis. Si vous souhaitez en savoir plus, consultez la section « Accès aux événements cruciaux pour les enquêtes » dans [Audit avancé](advanced-audit.md#access-to-crucial-events-for-investigations). |
|Autorisations de boîtes aux lettres de délégué ajoutées|AddMailboxPermissions|Un administrateur a attribué l'autorisation de boîte aux lettres FullAccess à un utilisateur (appelé délégué) pour la boîte aux lettres d'une autre personne. L'autorisation FullAccess permet au délégué d'ouvrir la boîte aux lettres de l'autre personne, de lire et de gérer le contenu de celle-ci.|
|Utilisateur ajouté ou supprimé avec accès délégué au dossier calendrier|UpdateCalendarDelegation|Un utilisateur a été ajouté ou supprimé en tant que délégué au calendrier pour la boîte aux lettres d'un autre utilisateur. La délégation de calendrier donne à quelqu'un d'autre, dans la même organisation, les autorisations de gérer le calendrier du propriétaire de la boîte aux lettres.|
|Autorisations ajoutées au dossier|AddFolderPermissions|Une autorisation de dossier a été ajoutée. Les autorisations de dossier déterminent quels utilisateurs de votre organisation peuvent accéder aux dossiers dans une boîte aux lettres et aux messages situés dans ces dossiers.|
|Messages copiés vers un autre dossier|Copy|Un message a été copié vers un autre dossier.|
|Élément de boîte aux lettres créé|Create|Un élément est créé dans le dossier Calendrier, Contacts, Notes ou Tâches de la boîte aux lettres. Par exemple, une nouvelle demande de réunion est créée. La création, l'envoi ou la réception d'un message ne sont pas audités. De plus, la création d'un dossier de boîte aux lettres n'est pas auditée.|
|Nouvelle règle de boîte de réception créée dans Outlook Web App|New-InboxRule|Un propriétaire de boîte aux lettres ou un autre utilisateur ayant accès à la boîte aux lettres a créé une règle de boîte de réception dans Outlook Web App.|
|Messages supprimés du dossier Éléments supprimés|SoftDelete|Un message a été supprimé, définitivement ou non, du dossier Éléments supprimés. Ces éléments sont déplacés vers le dossier Éléments récupérables. Les messages sont également déplacés vers le dossier Éléments récupérables quand un utilisateur les sélectionne et appuie sur **Maj+Suppr**.|
|Message étiqueté en tant qu'enregistrement|ApplyRecordLabel|Un message a été classé comme étant un enregistrement. Cela se produit lorsqu'une étiquette de rétention qui classe le contenu en tant qu'enregistrement est appliquée manuellement ou automatiquement à un message.|
|Messages déplacés vers un autre dossier|Move|Un message a été déplacé vers un autre dossier.|
|Messages déplacés vers le dossier Éléments supprimés|MoveToDeletedItems|Un message a été supprimé et déplacé vers le dossier Éléments supprimés.|
|Autorisation de dossier modifiée|UpdateFolderPermissions|Une autorisation de dossier a été modifiée. Les autorisations de dossier déterminent quels utilisateurs de votre organisation peuvent accéder aux dossiers de boîte aux lettres et aux messages du dossier.|
|Règle de boîte de réception modifiée à partir de Outlook Web App|Set-InboxRule|Un propriétaire de boîte aux lettres ou un autre utilisateur ayant accès à la boîte aux lettres a modifié une règle de boîte de réception dans Outlook Web App.|
|Messages supprimés définitivement de la boîte aux lettres|HardDelete|Un courrier a été supprimé définitivement du dossier Éléments récupérables (supprimé définitivement de la boîte aux lettres).|
|Autorisations de boîtes aux lettres de délégué supprimées|Supprimer-MailboxPermission|Un administrateur a supprimé l'autorisation FullAccess (qui était attribuée à un délégué) pour la boîte lettres d'une personne. Une fois l'autorisation FullAccess supprimée, le délégué ne peut plus ouvrir la boîte aux lettres de cette personne ni accéder à son contenu.|
|Autorisations supprimées du dossier|RemoveFolderPermissions|Une autorisation de dossier a été supprimée. Les autorisations de dossier déterminent quels utilisateurs de votre organisation peuvent accéder aux dossiers dans une boîte aux lettres et aux messages situés dans ces dossiers.|
|Message envoyé|Send|Un message a été envoyé, transféré ou a reçu une réponse. Cette activité n'est enregistrée que pour les utilisateurs disposant d'une licence Office 365 ou Microsoft 365 E5. Si vous souhaitez en savoir plus, consultez la section « Accès aux événements cruciaux pour les enquêtes » dans [Audit Avancé](advanced-audit.md#access-to-crucial-events-for-investigations).|
|Message envoyé à l'aide de l'autorisation Envoyer en tant que|SendAs|Un message a été envoyé à l'aide de l'autorisation SendAs. Cela signifie qu'un autre utilisateur a envoyé le message comme s'il provenait du propriétaire de la boîte aux lettres.|
|Message envoyé à l'aide de l'autorisation Envoyer de la part de|SendOnBehalf|Un message a été envoyé à l'aide de l'autorisation SendOnBehalf. Cela signifie qu'un autre utilisateur a envoyé le message au nom du propriétaire de la boîte aux lettres. Le message indique au destinataire à qui le message a été envoyé et qui a vraiment envoyé le message.|
|Règles de boîte de réception mises à jour à partir du client Outlook|UpdateInboxRules|Un propriétaire de boîte aux lettres ou un autre utilisateur ayant accès à la boîte aux lettres a modifié une règle de boîte de réception dans le client Outlook.|
|Message mis à jour|Update|Un message (ou ses propriétés) a été modifié.|
|Utilisateur connecté à la boîte aux lettres|MailboxLogin|L’utilisateur s’est connecté à sa boîte aux lettres.|
|Étiqueter un message en tant qu’enregistrement||Un utilisateur a appliqué une étiquette de rétention à un message électronique. Cette étiquette est configurée pour identifier l’élément en tant qu’enregistrement. |
||||

### <a name="user-administration-activities"></a>Activités d’administration des utilisateurs

Le tableau suivant répertorie les activités d’administration des utilisateurs enregistrées quand un administrateur ajoute ou modifie un compte d’utilisateur via le Centre d’administration Microsoft 365 ou le portail de gestion Azure.

|Activité|Opération|Description|
|:-----|:-----|:-----|
|Utilisateur ajouté|Ajouter un utilisateur|Un compte d’utilisateur a été créé.|
|Licence utilisateur modifiée|Change user license|La licence attribuée à un utilisateur a été modifiée. Pour identifier les licences modifiées, voir l’activité **Utilisateur mis à jour** correspondante.|
|Mot de passe utilisateur modifié|Modifier le mot de passe de l'utilisateur|Un utilisateur modifie son mot de passe. La réinitialisation du mot de passe en libre-service doit être activée (pour tous ou pour certains utilisateurs) dans votre organisation pour permettre aux utilisateurs de réinitialiser leur mot de passe. Vous pouvez également suivre l'activité de réinitialisation de mot de passe en libre-service dans Azure Active Directory. Si vous souhaitez en savoir plus, consultez l'article [Options de rapport pour la gestion des mots de passe Azure AD](https://docs.microsoft.com/azure/active-directory/authentication/howto-sspr-reporting).
|Utilisateur supprimé|Supprimer un utilisateur|Un compte d’utilisateur a été supprimé.|
|Réinitialiser le mot de passe de l’utilisateur|Reset user password|Un administrateur réinitialise le mot de passe d’un utilisateur.|
|Propriété définie qui force l’utilisateur à changer de mot de passe.|Forcer la réinitialisation du mot de passe de l'utilisateur|Un administrateur a défini la propriété qui force un utilisateur à modifier son mot de passe lors de sa prochaine connexion à Office 365.|
|Propriétés de licence définies|Propriétés de licence définies|Un administrateur modifie les propriétés d’une licence attribuée à un utilisateur.|
|Utilisateur mis à jour|Mettre à jour un utilisateur|L'administrateur modifie une ou plusieurs propriétés d'un compte d'utilisateur. Pour obtenir la liste des propriétés utilisateur qui peuvent être mises à jour, consultez la section « Mettre à jour les attributs utilisateur » dans les [Événements de rapport d'audit Azure Active Directory](https://go.microsoft.com/fwlink/p/?LinkID=616549).|
||||

### <a name="azure-ad-group-administration-activities"></a>Activités d'administration des groupes Azure AD

Le tableau suivant répertorie les activités d'administration de groupe qui sont enregistrées lorsqu'un administrateur ou un utilisateur crée ou modifie un groupe Microsoft 365 ou lorsqu'un administrateur crée un groupe de sécurité à l'aide du centre d'administration Microsoft 365 ou du portail de gestion Azure. Si vous souhaitez en savoir plus sur les groupes dans Office 365, consultez l'article [Afficher, créer et supprimer des groupes dans le centre d'administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/create-groups/create-groups).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Groupe ajouté|Add group|Un groupe a été créé.|
|Membre ajouté au groupe|Add member to group|Un membre a été ajouté à un groupe.|
|Groupe supprimé|Delete group|Un groupe a été supprimé.|
|Membre supprimé du groupe|Remove member from group|Un membre a été supprimé d’un groupe.|
|Groupe mis à jour|Update group|Une propriété d’un groupe a été modifiée.|
||||

### <a name="application-administration-activities"></a>Activités d'administration des applications

Le tableau suivant répertorie les activités d'administration d'application qui sont enregistrées lorsqu'un administrateur ajoute ou modifie une application inscrite dans Azure AD. Les applications qui s'appuient sur Azure AD pour l'authentification doivent être inscrites dans l'annuaire.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Entrée de délégation ajoutée|Ajouter Entrée de délégation|Une autorisation d’authentification a été créée/accordée à une application dans Azure AD.|
|Principal de service ajouté|Ajouter un principal de service|Une application a été inscrite dans Azure AD. Une application est représentée par un principal de service dans l'annuaire.|
|Informations d'identification ajoutées à un principal de service |Ajouter des informations d'identification à un principal de service|Les informations d'identification ont été ajoutées à un principal de service dans Azure AD. Un principal de service représente une application dans l'annuaire.|
|Entrée de délégation supprimée|Supprimer une entrée de délégation |Une autorisation d’authentification a été supprimée d’une application dans Azure AD.|
|Principal de service supprimé de l’annuaire|Supprimer le principal de service|Une application a été supprimée ou désinscrite de Azure AD. Une application est représentée par un principal de service dans l'annuaire.|
|Informations d'identification supprimées d'un principal de service|Supprimer les informations d'identification du principal de service|Les informations d'identification ont été supprimées d'un principal de service dans Azure AD. Un principal de service représente une application dans l'annuaire.|
|Entrée de délégation définie|Définition de l’entrée de délégation|Une autorisation d’authentification a été mise à jour pour une application dans Azure AD.|
||||

### <a name="role-administration-activities"></a>Activités d’administration des rôles

Le tableau suivant répertorie les activités d’administration des rôles Azure AD journalisées quand un administrateur gère les rôles d’administrateur via le Centre d’administration Microsoft 365 ou le portail de gestion Azure.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Membre ajouté au rôle|Ajouter un membre de rôle au rôle|Un utilisateur a été ajouté à un rôle d’administrateur dans Microsoft 365.|
|Utilisateur supprimé d’un rôle d’annuaire|Supprimer un membre de rôle d’un rôle|Un utilisateur a été supprimé d’un rôle d’administrateur dans Microsoft 365.|
|Définition des informations de contact d’une entreprise|Définir les informations de contact d'une entreprise|Mise à jour des préférences de contact au niveau de l'entreprise pour votre organisation. Cela inclut les adresses e-mail pour les e-mails liés à l'abonnement envoyés par Microsoft 365 et les notifications techniques concernant les services.|
||||

### <a name="directory-administration-activities"></a>Activités d'administration de l'annuaire

Le tableau suivant répertorie les activités liées à l’annuaire et au domaine Azure AD journalisées quand un administrateur gère son organisation via le Centre d’administration Microsoft 365 ou le portail de gestion Azure.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Domaine ajouté à l’entreprise|Ajouter un domaine à l’entreprise|Un domaine a été ajouté à votre organisation.|
|Partenaire ajouté à l’annuaire|Ajouter un partenaire à l’entreprise|Un partenaire (administrateur délégué) a été ajouté à votre organisation.|
|Domaine supprimé de l’entreprise|Supprimer le domaine de l’entreprise|Un domaine a été supprimé de votre organisation.|
|Partenaire supprimé de l’annuaire|Supprimer un partenaire de l’entreprise|Un partenaire (administrateur délégué) a été supprimé de votre organisation.|
|Définition des informations sur la société|Définir les informations de l'entreprise|Mise à jour des informations relatives à l'entreprise pour votre organisation. Cela inclut les adresses e-mail pour les e-mails liés à l'abonnement envoyés par Microsoft 365 et les notifications techniques concernant les services Microsoft 365.|
|Définition de l'authentification de domaine|Définition de l’authentification de domaine|Le paramètre d’authentification de domaine a été modifié pour votre organisation.|
|Paramètres de fédération mis à jour pour un domaine|Définir les paramètres de fédération du domaine|Les paramètres de la fédération (partage externe) ont été modifiés pour votre organisation.|
|Stratégie de mot de passe définie|Stratégie de mot de passe définie|Les contraintes de longueur et de caractères applicables aux mots de passe utilisateur ont été modifiées dans votre organisation.|
|Activation de la synchronisation Azure AD|Définir l’indicateur DirSyncEnabled à l’entreprise|La propriété qui active un annuaire pour la synchronisation Azure AD a été définie.|
|Domaine mis à jour|Mettre à jour le domaine|Les paramètres d’un domaine dans votre organisation ont été mis à jour.|
|Domaine vérifié|Verify domain|La propriété d’un domaine par votre organisation a été vérifiée.|
|Domaine de courrier vérifié par courrier électronique|Verify email verified domain|Une vérification de courrier électronique a été effectuée pour vérifier que votre organisation est propriétaire d’un domaine.|
||||

### <a name="ediscovery-activities"></a>Activités de eDiscovery

Les activités Recherche de contenu et eDiscovery, effectuées dans le centre de sécurité et de conformité ou en exécutant les cmdlets PowerShell correspondantes, sont enregistrées dans le journal d'audit. Cela comprend les activités suivantes :

- création et gestion des cas de eDiscovery

- création, démarrage et modification des recherches de contenu ;

- exécution des actions de recherche de contenu, telles que l’aperçu, l’exportation et la suppression des résultats de recherche ;

- configuration des autorisations de filtrage de la recherche de contenu ;

- gestion du rôle d’administrateur eDiscovery.

Pour consulter la liste et une description détaillée des activités de découverte électronique enregistrées, consultez l'article [Rechercher les activités eDiscovery dans le journal d'audit](search-for-ediscovery-activities-in-the-audit-log.md).

> [!NOTE]
> Une trentaine de minutes peuvent être nécessaires avant que les événements résultant des activités répertoriées sous **Activités eDiscovery** et **Activités Advanced eDiscovery** dans la liste déroulante **Activités** ne s'affichent dans les résultats de la recherche. Inversement, 24 heures peuvent être nécessaires avant que les événements correspondant aux activités de la cmdlet eDiscovery ne s'affichent dans les résultats de la recherche.

### <a name="advanced-ediscovery-activities"></a>Activités Advanced eDiscovery

Vous pouvez également rechercher dans le journal d'audit des activités dans Advanced eDiscovery. Pour obtenir une description de ces activités, consultez la section « Activités Advanced eDiscovery » dans l'article [Rechercher des activités eDiscovery dans le journal d'audit](search-for-ediscovery-activities-in-the-audit-log.md#advanced-ediscovery-activities).

### <a name="power-bi-activities"></a>Activités Power BI

Vous pouvez rechercher dans le journal d'audit des activités dans Power BI. Si vous souhaitez en savoir plus sur les activités Power BI, consultez la section « Activités auditées par Power BI » dans l'article [Utiliser l'audit au sein de votre organisation](https://docs.microsoft.com/power-bi/service-admin-auditing#activities-audited-by-power-bi).

La journalisation d'audit pour Power BI n'est pas activée par défaut. Pour rechercher des activités Power BI dans le journal d'audit, vous devez activer l'audit dans le portail d'administration Power BI. Pour obtenir des instructions, consultez la section « Journaux d'audit » dans le [portail d'administration Power BI](https://docs.microsoft.com/power-bi/service-admin-portal#audit-logs).

### <a name="microsoft-workplace-analytics-activities"></a>Activités de L'analyse du temps de travail Microsoft

L'analyse du temps de travail fournit des informations sur la manière dont les groupes collaborent au sein de votre organisation. Le tableau suivant répertorie les activités effectuées par les utilisateurs auxquels le rôle Administrateur ou les rôles Analyste sont attribués dans l'analyse du temps de travail. Les utilisateurs auxquels le rôle Analyste est attribué ont un accès complet à toutes les fonctionnalités du service et utilisent le produit pour effectuer des analyses. Les utilisateurs auxquels le rôle Administrateur est attribué peuvent configurer les paramètres de confidentialité et les valeurs par défaut du système, et peuvent préparer, télécharger et vérifier les données organisationnelles dans l'analyse du temps de travail. Si vous souhaitez en savoir plus, consultez l'article [Analyse du temps de travail](https://docs.microsoft.com/workplace-analytics/index-orig).

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
|Exploration de la consultation|ViewedExplore|Un analyste a consulté les visualisations dans un ou plusieurs onglets de page exploration.|
||||

### <a name="microsoft-teams-activities"></a>Activités dans Microsoft Teams

Vous pouvez rechercher dans le journal d'audit les activités des utilisateurs et des administrateurs dans Microsoft Teams. Teams est un espace de travail centré sur la discussion dans Office 365. Il rassemble les conversations, les réunions, les fichiers et les notes d'une équipe en un seul endroit. Pour obtenir une description des activités Teams auditées, consultez l'article [Rechercher dans le journal d'audit les événements de Microsoft Teams](https://docs.microsoft.com/microsoftteams/audit-log-events#teams-activities).

### <a name="microsoft-teams-healthcare-activities"></a>Activités de Microsoft Teams pour la santé

Si votre organisation utilise l'[application Patients](https://docs.microsoft.com/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-app-overview) dans Microsoft Teams, vous pouvez rechercher dans le journal d'audit les activités liées à l'utilisation de l'application Patients. Si votre environnement est configuré pour prendre en charge l'application Patients, un groupe d'activités supplémentaire pour ces activités est disponible dans la liste du sélecteur d'**Activités**.

![Activités de Microsoft Teams pour la santé dans la liste du sélecteur d'Activités](../media/TeamsHealthcareAuditActivities.png)

Pour obtenir une description des activités de l’application Patients, voir les [journaux d’audit pour l’application Patients](https://docs.microsoft.com/MicrosoftTeams/expand-teams-across-your-org/healthcare/patients-audit).

### <a name="microsoft-teams-shifts-activities"></a>Activités Plannings dans Microsoft Teams

Si votre organisation utilise l'application Plannings dans Microsoft Teams, vous pouvez rechercher dans le journal d'audit les activités liées à l'utilisation de l'application Plannings. Si votre environnement est configuré pour prendre en charge les applications Plannings, un groupe d'activités supplémentaire pour ces activités est disponible dans la liste du sélecteur d'**Activités**.

Pour obtenir une description des activités de l'application Shifts, consultez l'article [Rechercher dans le journal d'audit les événements de Microsoft Teams](https://docs.microsoft.com/microsoftteams/audit-log-events#shifts-in-teams-activities).

### <a name="yammer-activities"></a>Activités dans Yammer

Le tableau suivant répertorie les activités des utilisateurs et des administrateurs dans Yammer qui sont enregistrées dans le journal d'audit. Pour renvoyer les activités liées à Yammer à partir du journal d'audit, vous devez sélectionner **Afficher les résultats pour toutes les activités** dans la liste **Activités**. Utilisez les zones de plage de dates et la liste **Utilisateurs** pour affiner les résultats de la recherche.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Modification d’une stratégie de rétention des données|SoftDeleteSettingsUpdated|Un administrateur vérifié met à jour le paramètre de stratégie de rétention des données de réseau en vue d’une suppression définitive ou réversible. Seuls des administrateurs vérifiés peuvent effectuer cette opération.|
|Modification de configuration réseau|NetworkConfigurationUpdated|Un administrateur réseau ou vérifié modifie la configuration du réseau Yammer. Cela inclut la définition d’un intervalle pour l’exportation de données et l’activation de la conversation instantanée.|
|Modification des paramètres de profil réseau|ProcessProfileFields|Un administrateur réseau ou vérifié modifie les informations qui apparaissent sur les profils de membre des utilisateurs du réseau.|
|Modification du mode Contenu privé|SupervisorAdminToggled|L'administrateur vérifié active ou désactive le *mode Contenu privé*. Ce mode permet à un administrateur d'afficher les publications dans des groupes privés et d'afficher les messages privés à des utilisateurs individuels (ou des groupes d'utilisateurs). Seuls les administrateurs vérifiés peuvent effectuer cette opération.|
|Configuration de la sécurité modifiée|NetworkSecurityConfigurationUpdated|Un administrateur vérifié met à jour la configuration de sécurité du réseau Yammer. Cela inclut la définition des stratégies d’expiration de mot de passe et les restrictions d’adresses IP. Seuls des administrateurs vérifiés peuvent effectuer cette opération.|
|Création de fichier|FileCreated|Un utilisateur charge un fichier.|
|Groupe créé|GroupCreation|L’utilisateur crée un groupe.|
|Groupe supprimé|GroupDeletion|Un groupe est supprimé de Yammer.|
|Message supprimé|MessageDeleted|Un utilisateur supprime un message.|
|Fichier téléchargé|FileDownloaded|Un utilisateur télécharge un fichier.|
|Données exportées|DataExport|Un administrateur vérifié exporte des données de réseau Yammer. Seuls des administrateurs vérifiés peuvent effectuer cette opération.|
|Partage de fichier|FileShared|Un utilisateur partage un fichier avec un autre utilisateur.|
|Suspension d’un utilisateur du réseau|NetworkUserSuspended|Un administrateur réseau ou vérifié suspend (désactive) un utilisateur de Yammer.|
|Utilisateur suspendu|UserSuspension|Un compte d’utilisateur est suspendu (désactivé).|
|Mise à jour de la description d’un fichier|FileUpdateDescription|Un utilisateur modifie la description d’un fichier.|
|Mise à jour d’un nom de fichier|FileUpdateName|Un utilisateur modifie le nom d’un fichier.|
|Affichage d’un fichier|FileVisited|Un utilisateur affiche un fichier.|
||||

### <a name="microsoft-power-automate-activities"></a>Activités Microsoft Power Automate

Vous pouvez rechercher dans le journal d'audit des activités dans Power Automate (anciennement appelé Microsoft Flow). Ces activités incluent la création, la modification et la suppression de flux et la modification des autorisations de flux. Si vous souhaitez en savoir plus sur l'audit des activités Power Automate, consultez le blog [Les événements d'audit Microsoft Flow sont désormais disponibles dans le centre de sécurité et de conformité](https://flow.microsoft.com/blog/security-and-compliance-center).

### <a name="microsoft-power-apps-activities"></a>Activités Microsoft Power Apps

Vous pouvez rechercher dans le journal d'audit les activités liées aux applications dans Power Apps. Ces activités incluent la création, le lancement et la publication d'une application. L'attribution d'autorisations aux applications est également auditée. Pour obtenir une description de toutes les activités Power Apps, consultez l'article [Journalisation des activités pour Power Apps](https://docs.microsoft.com/power-platform/admin/logging-powerapps#what-events-are-audited).

### <a name="microsoft-stream-activities"></a>Activités de Microsoft Stream

Vous pouvez rechercher dans le journal d'audit des activités dans Microsoft Stream. Ces activités comprennent les activités vidéo effectuées par les utilisateurs, les activités de canal de groupe et les activités d'administration telles que la gestion des utilisateurs, la gestion des paramètres de l'organisation et l'exportation de rapports. Pour obtenir une description de ces activités, consultez la section « Actions enregistrées dans Stream » de l'article [Journaux d'audit dans Microsoft Stream](https://docs.microsoft.com/stream/audit-logs#actions-logged-in-stream).

### <a name="content-explorer-activities"></a>Activités de l'Explorateur de contenu

Le tableau suivant répertorie les activités de l'explorateur de contenu qui sont consignées dans le journal d'audit. L'explorateur de contenu est accessible via l'outil de classification des données dans le centre de conformité Microsoft 365. Si vous souhaitez en savoir plus, consultez l'article [Utiliser l'explorateur de contenu de classification de données](data-classification-content-explorer.md).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Élément consulté|LabelContentExplorerAccessedItem|Un administrateur (ou utilisateur membre du groupe de rôles Visionneuse de contenu de l’Explorateur de contenu) utilise l’Explorateur de contenu pour afficher un e-mail ou un document SharePoint/OneDrive.|
||||

### <a name="quarantine-activities"></a>Activités de mise en quarantaine

Le tableau suivant répertorie les activités de mise en quarantaine que vous pouvez rechercher dans le journal d'audit. Si vous souhaitez en savoir plus sur la mise en quarantaine, consultez l'article [Mettre en quarantaine les messages électroniques dans Office 365](../security/office-365-security/quarantine-email-messages.md).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Message de quarantaine supprimé|QuarantineDelete|Un utilisateur a supprimé un message électronique considéré comme dangereux.|
|Message de quarantaine exporté|QuarantineExport|Un utilisateur a exporté un message électronique considéré comme dangereux.|
|Message de quarantaine visualisé|QuarantinePreview|Un utilisateur a visualisé un message électronique considéré comme dangereux.|
|Message de quarantaine publié|QuarantineRelease|Un utilisateur a publié un message électronique de quarantaine considéré comme dangereux.|
|En-tête du message de quarantaine consulté|QuarantineViewHeader|Un utilisateur a affiché l’en-tête d’un message électronique considéré comme dangereux.|
||||

### <a name="microsoft-forms-activities"></a>Activités Microsoft Forms

Le tableau suivant répertorie les activités des utilisateurs et des administrateurs dans Microsoft Forms qui sont enregistrées dans le journal d'audit. Microsoft Forms est un outil de formulaires, questionnaire ou enquête, utilisé pour collecter des données à des fins d'analyse. 

Dans les descriptions ci-dessous, certaines opérations contiennent d'autres paramètres d'activité.

> [!NOTE]
> Si une activité Forms est effectuée par un co-auteur ou un participant anonyme, elle sera enregistrée légèrement différemment. Si vous souhaitez en savoir plus, consultez la section [Activités Forms effectuées par des co-auteurs et des participants anonymes](#forms-activities-performed-by-coauthors-and-anonymous-responders).

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Commentaire créé|CreateComment|Le propriétaire du formulaire ajoute un commentaire ou une note à un questionnaire.|
|Formulaire créé|CreateForm|Le propriétaire du formulaire crée un nouveau formulaire.|
|Formulaire modifié|EditForm|Le propriétaire du formulaire modifie un formulaire, par exemple en créant, en supprimant ou en modifiant une question. La propriété *EditOperation:string* indique le nom de l'opération de modification. Les opérations possibles sont :<br/>– CreateQuestion<br/>– CreateQuestionChoice <br/>– DeleteQuestion <br/>– DeleteQuestionChoice <br/>– DeleteFormImage <br/>– DeleteQuestionImage <br/>– UpdateQuestion <br/>– UpdateQuestionChoice <br/>– UploadFormImage/Bing/Onedrive <br/>– UploadQuestionImage <br/>– ChangeTheme <br><br>FormImage inclut tout emplacement au sein duquel l’utilisateur peut charger une image, par exemple dans une requête ou en tant que thème d’arrière-plan.|
|Formulaire déplacé|MoveForm|Le propriétaire du formulaire déplace un formulaire. <br><br>La propriété DestinationUserId:string indique l'ID utilisateur de la personne qui a déplacé le formulaire. La propriété NewFormId:string est le nouvel ID du formulaire nouvellement copié.|
|Formulaire supprimé|DeleteForm|Le propriétaire du formulaire supprime un formulaire. Cela inclut SoftDelete (option de suppression utilisée et formulaire déplacé vers la corbeille) et HardDelete (la corbeille est vidée).|
|Formulaire consulté (au moment de la conception)|ViewForm|Le propriétaire du formulaire ouvre un formulaire existant pour modification.|
|Formulaire prévisualisé|PreviewForm|Propriétaire du formulaire affiche un aperçu d’un formulaire à l’aide de la fonction d’aperçu.|
|Données exportées|ExportForm|Le propriétaire du formulaire exporte les résultats vers Excel. <br><br>La propriété ExportFormat:string indique si le fichier Excel est téléchargé ou en ligne.|
|Formulaire de partage autorisé pour la copie|AllowShareFormForCopy|Le propriétaire du formulaire crée un lien de modèle pour partager le formulaire avec d'autres utilisateurs. Cet événement est enregistré lorsque le propriétaire du formulaire clique pour générer l'URL du modèle.|
|Formulaire de partage non autorisé pour copie|DisallowShareFormForCopy|Le propriétaire du formulaire supprime le lien modèle.|
|Co-auteur du formulaire ajouté|AddFormCoauthor|Un utilisateur utilise un lien de collaboration pour aider à concevoir ou afficher les réponses. Cet événement est enregistré lorsqu'un utilisateur utilise une URL de collaboration (et non lors de la première génération de l'URL de collaboration).|
|Co-auteur du formulaire supprimé|RemoveFormCoauthor|Le propriétaire du formulaire supprime un lien de collaboration.|
|Page de réponse consultée|ViewRuntimeForm|L'utilisateur a ouvert une page de réponse à afficher. Cet événement est enregistré, que l'utilisateur soumette ou non une réponse.|
|Réponse créée|CreateResponse|Similaire à Recevoir une nouvelle réponse. Un utilisateur a répondu au formulaire. <br><br>La propriété ResponseId:string et la propriété ResponderId:string indiquent quel résultat est affiché. <br><br>Pour un répondant anonyme, la propriété ResponderId sera null.|
|Réponse mise à jour|UpdateResponse|Le propriétaire du formulaire a mis à jour un commentaire ou une note sur un questionnaire. <br><br>La propriété ResponseId:string et la propriété ResponderId:string indiquent quel résultat est affiché. <br><br>Pour un répondant anonyme, la propriété ResponderId sera null.|
|Toutes les réponses supprimées|DeleteAllResponses|Le propriétaire du formulaire supprime toutes les données de réponse.|
|Réponse supprimée|DeleteResponse|Un propriétaire d’un formulaire supprime une réponse. <br><br>La propriété ResponseId:string indique la réponse en cours de suppression.|
|Réponses consultées|ViewResponses|Propriétaire du formulaire affiche la liste agrégée des réponses. <br><br>La propriété ViewType : String indique si le propriétaire du formulaire affiche les détails ou les agrégats|
|Réponse consultée|ViewResponse|Le propriétaire du formulaire affiche une réponse spécifique. <br><br>La propriété ResponseId:string et la propriété ResponderId:string indiquent quel résultat est affiché. <br><br>Pour un répondant anonyme, la propriété ResponderId sera null.|
|Lien de synthèse créé|GetSummaryLink|Le propriétaire du formulaire crée un lien de résultats de synthèse pour partager les résultats.|
|Lien de synthèse supprimé|DeleteSummaryLink|Le propriétaire du formulaire supprime le lien de synthèse des résultats.|
|Formulaire mis à jour état d’hameçonnage|UpdatePhishingStatus|Cet événement est enregistré chaque fois que la valeur détaillée de l'état de sécurité interne est modifiée, que cela modifie l'état de sécurité final ou non (par exemple, le formulaire est désormais Fermé ou Ouvert). Cela signifie que vous pouvez voir des événements en double sans modification finale de l'état de sécurité. Les valeurs d'état possibles pour cet événement sont :<br/>– Retirer <br/>– Retirer par l’administrateur <br/>– Admin débloqué <br/>– Bloqué automatiquement <br/>– Débloqué automatiquement <br/>– Utilisateur signalé <br/>– Réinitialiser l’utilisateur signalé|
|État de l’hameçonnage de l’utilisateur mis à jour|UpdateUserPhishingStatus|Cet événement est enregistré chaque fois que la valeur de l'état de sécurité de l'utilisateur est modifiée. La valeur de l'état de l'utilisateur dans l'enregistrement d'audit est défini sur **Confirmé comme hameçonnage** lorsque l'utilisateur créé un formulaire d'hameçonnage qui est supprimé par l'équipe de sécurité de Microsoft Online. Si un administrateur débloque l'utilisateur, la valeur de l'état de l'utilisateur est définie sur **Réinitialiser en tant qu'utilisateur normal**.|
|Invitation Forms Pro envoyée|ProInvitation|L’utilisateur clique pour activer une version d’évaluation Pro.|
|Paramètres de formulaire mis à jour|UpdateFormSetting|Le propriétaire du formulaire met à jour un paramètre de formulaire. <br><br>La propriété FormSettingName:string indique le nom du paramètre et la nouvelle valeur.|
|Paramètres d’utilisateur mis à jour|UpdateUserSetting|Le propriétaire du formulaire met à jour un paramètre d’utilisateur. <br><br>La propriété UserSettingName:string indique le nom et la nouvelle valeur du paramètre|
|Formulaires répertoriés|ListForms|Le propriétaire du formulaire affiche une liste de formulaires. <br><br>La propriété ViewType:string indique l'affichage que le propriétaire du formulaire consulte : Tous les formulaires, Partagés avec moi ou les Formulaires de groupe|
|Réponse envoyée|SubmitResponse|Un utilisateur envoie une réponse à un formulaire. <br><br>La propriété IsInternalForm:boolean indique si le répondant fait partie de la même organisation que le propriétaire du formulaire.|
||||

#### <a name="forms-activities-performed-by-coauthors-and-anonymous-responders"></a>Activités Forms effectuées par des co-auteurs et des participants anonymes

Forms prend en charge la collaboration lors de la conception des formulaires et lors de l'analyse des réponses. Un collaborateur de formulaire est appelé *co-auteur*. Les co-auteurs peuvent effectuer les mêmes opérations que le propriétaire du formulaire, sauf supprimer ou déplacer un formulaire. Forms vous permet également de créer un formulaire auquel vous pouvez répondre de manière anonyme. Cela signifie que la personne qui répond n'a pas besoin d'être connecté à votre organisation pour répondre à un formulaire.

Le tableau suivant décrit les activités d'audit et les informations figurant dans l'enregistrement d'audit pour les activités réalisées par les co-auteurs et les participants anonymes.

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

Le tableau suivant répertorie les événements provoquant des activités d’étiquetage pour les sites SharePoint Online et Teams.

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
|Étiquette de confidentialité appliquée au site|SensitivityLabelApplied|Une étiquette de confidentialité a été appliquée à un site SharePoint ou Teams.|
|Suppression de l'étiquette de confidentialité sur le site|SensitivityLabelRemoved|Une étiquette de confidentialité a été supprimée sur un site SharePoint ou Teams.|
|Étiquette de confidentialité appliquée au fichier|FileSensitivityLabelApplied|Une étiquette de confidentialité a été appliquée à un document à l’aide d’Office sur le web ou d’une stratégie d’attribution automatique d’étiquette.|
|Étiquette de confidentialité modifiée appliquée au fichier|FileSensitivityLabelChanged|Une étiquette de confidentialité différente a été appliquée à un document à l’aide d’Office sur le web ou d’une stratégie d’attribution automatique d’étiquette.|
|Suppression de l'étiquette de confidentialité sur le document|FileSensitivityLabelRemoved|Une étiquette de confidentialité a été supprimée d'un document à l'aide de Office sur le web, d'une stratégie d'étiquetage automatique ou de la cmdlet [Unlock-SPOSensitivityLabelEncryptedFile](https://docs.microsoft.com/powershell/module/sharepoint-online/unlock-sposensitivitylabelencryptedFile).|
||||

### <a name="retention-policy-and-retention-label-activities"></a>Activités des stratégies de rétention et des étiquettes de rétention

|Nom facile à retenir|Opération|Description|
|:-----|:-----|:-----|
| Paramètres configurés pour une stratégie de rétention |NewRetentionComplianceRule |L'administrateur a configuré les paramètres de rétention pour une nouvelle stratégie de rétention. Les paramètres de rétention incluent la durée de conservation des éléments et ce qu'il advient des éléments à l'expiration de la période de rétention (comme la suppression d'éléments, la conservation des éléments ou leur conservation, puis leur suppression). Cette activité correspond également à l'exécution de la cmdlet [New-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/new-retentioncompliancerule).|
| Étiquette de rétention créée |NewComplianceTag |Un administrateur a créé une étiquette de rétention.|
| Stratégie de rétention créée |NewRetentionCompliancePolicy|Un administrateur a créé une stratégie de rétention.|
| Paramètres supprimés d’une stratégie de rétention| RemoveRetentionComplianceRule<br/>| L'administrateur a supprimé les paramètres de configuration d'une stratégie de rétention. Cette activité est plus susceptible d'être enregistrée lorsqu'un administrateur supprime une stratégie de rétention ou exécute la cmdlet [Remove-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/Remove-RetentionComplianceRule).|
| Étiquette de rétention supprimée |RemoveComplianceTag | Un administrateur a supprimé une étiquette de rétention.|
| Stratégie de rétention supprimée |RemoveRetentionCompliancePolicy<br/> |Un administrateur a supprimé une stratégie de rétention. |
| Option d’enregistrement réglementaire activée pour les étiquettes de rétention<br/> |SetRestrictiveRetentionUI |Un administrateur a exécuté le cmdlet [RegulatoryComplianceUI](https://docs.microsoft.com/powershell/module/exchange/set-regulatorycomplianceui) afin qu’un administrateur puisse ensuite sélectionner l’option de configuration de l’interface utilisateur pour une étiquette de rétention et identifier le contenu en tant qu’enregistrement réglementaire.|
| Paramètres mis à jour pour une stratégie de rétention | SetRetentionComplianceRule | L'administrateur a modifié les paramètres de rétention d'une stratégie de rétention existante. Les paramètres de rétention incluent la durée de conservation des éléments et ce qu'il advient des éléments à l'expiration de la période de rétention (comme la suppression des éléments, la conservation des éléments ou leur conservation, puis leur suppression). Cette activité correspond également à l'exécution de la cmdlet [Set-RetentionComplianceRule](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancerule). |
| Étiquette de rétention mise à jour |SetComplianceTag  | Un administrateur a mis à jour une étiquette de rétention existante.|
| Stratégie de rétention mise à jour |SetRetentionCompliancePolicy |L'administrateur a mis à jour une stratégie de rétention existante. Les mises à jour qui déclenchent cet événement incluent l'ajout ou l'exclusion d'emplacements de contenu auxquels la stratégie de rétention est appliquée.|

### <a name="exchange-admin-audit-log"></a>Journal d'audit de l'administrateur Exchange

La journalisation d'audit de l'administrateur Exchange (qui est activée par défaut dans Office 365) enregistre un événement dans le journal d'audit lorsqu'un administrateur (ou un utilisateur auquel des autorisations d'administration ont été attribuées) apporte une modification dans votre organisation Exchange Online. Les modifications apportées à l'aide du centre d'administration Exchange ou en exécutant une cmdlet dans Exchange Online PowerShell sont enregistrées dans le journal d'audit de l'administrateur Exchange. Les cmdlets qui commencent par les verbes **Get-**, **Search-** ou **Test-** ne sont pas enregistrées dans le journal d'audit. Si vous souhaitez en savoir plus sur la journalisation d'audit de l'administrateur dans Exchange, consultez l'article [Journalisation d'audit de l'administrateur](https://go.microsoft.com/fwlink/p/?LinkID=619225).

> [!IMPORTANT]
> Certaines cmdlets Exchange Online ne sont pas enregistrées dans le journal d'audit de l'administrateur Exchange (ou dans le journal d'audit). La plupart de ces cmdlets sont liées à la maintenance du service Exchange Online et sont exécutées par le personnel du centre de données Microsoft ou des comptes de service. Ces cmdlets ne sont pas enregistrées car elles entraîneraient un grand nombre d'événements d'audit « bruyants ». S'il existe une cmdlet Exchange Online qui n'est pas auditée, veuillez soumettre une suggestion au [forum de sécurité et de conformité Voice User](https://office365.uservoice.com/forums/289138-office-365-security-compliance) et demandez qu'elle soit activée pour l'audit. Vous pouvez également soumettre une demande de modification de conception au support Microsoft.

Voici quelques conseils pour rechercher les activités de l'administrateur Exchange dans le journal d'audit :

- Pour renvoyer les entrées du journal d'audit de l'administrateur Exchange, vous devez sélectionner **Afficher les résultats pour toutes les activités** dans la liste **Activités**. Utilisez les zones de plage de dates et la liste **Utilisateurs** pour affiner les résultats de la recherche des cmdlets exécutées par un administrateur Exchange spécifique dans une plage de dates spécifique.

- Pour afficher les événements du journal d'audit de l'administrateur Exchange, filtrez les résultats de la recherche et tapez un **-** (tiret) dans la zone de filtre **Activité**. Cela affiche les noms des cmdlets, qui sont affichés dans la colonne **Activité** pour les événements d'administration Exchange. Ensuite, vous pouvez trier les noms les cmdlets par ordre alphabétique.

  ![Tapez un tiret dans le champ Activités pour filtrer les événements d'administration Exchange](../media/7628e7aa-6263-474a-a28b-2dcf5694bb27.png)

- Pour obtenir des informations sur la cmdlet exécutée, les paramètres et les valeurs de paramètre utilisés et les objets affectés, vous pouvez exporter les résultats de la recherche en sélectionnant l'option **Télécharger tous les résultats**. Si vous souhaitez en savoir plus, consultez l'article [Exporter, configurer et afficher les enregistrements du journal d'audit](export-view-audit-log-records.md).

- Vous pouvez également utiliser la commande `Search-UnifiedAuditLog -RecordType ExchangeAdmin` dans Exchange Online PowerShell pour renvoyer uniquement les enregistrements d'audit du journal d'audit de l'administrateur Exchange. L'exécution d'une cmdlet Exchange peut prendre jusqu'à 30 minutes pour que l'entrée de journal d'audit correspondante soit renvoyée dans les résultats de la recherche. Si vous souhaitez en savoir plus, consultez l'article [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog). Si vous souhaitez en savoir plus sur l'exportation des résultats de la recherche renvoyés par la cmdlet **Search-UnifiedAuditLog** vers un fichier CSV, consultez la section « Conseils pour l'exportation et l'affichage du journal d'audit » de l'article [Exporter, configurer et afficher les enregistrements du journal d'audit](export-view-audit-log-records.md#tips-for-exporting-and-viewing-the-audit-log).

- Vous pouvez également afficher les événements dans le journal d'audit de l'administrateur Exchange à l'aide du centre d'administration Exchange ou en exécutant **Search-AdminAuditLog** dans Exchange Online PowerShell. C'est un bon moyen de rechercher spécifiquement les activités effectuées par les administrateurs Exchange Online. Si vous souhaitez obtenir des instructions, consultez les articles :

  - [Consulter le journal d'audit de l'administrateur](https://technet.microsoft.com/library/dn342832%28v=exchg.150%29.aspx)

  - [Search-AdminAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-adminauditlog)

   Gardez à l’esprit que les mêmes activités d’administrateur Exchange sont enregistrées dans le journal d’audit de l’administrateur Exchange et dans le journal d’audit.

## <a name="frequently-asked-questions"></a>Foire aux questions

**Quels services Microsoft 365 font actuellement l'objet d'un audit ?**

Les services les plus utilisés comme Exchange Online, SharePoint Online, OneDrive Entreprise, Azure Active Directory, Microsoft Teams, Dynamics 365, Defender pour Office 365 et Power BI sont audités. Consultez le [début de cet article](search-the-audit-log-in-security-and-compliance.md) pour obtenir une liste des services audités.

**Quelles activités sont auditées par le service d'audit dans Office 365 ?**

Consultez la section [Activités auditées](#audited-activities) dans cet article pour obtenir la liste et la description des activités auditées.

**Combien de temps faut-il pour que l'enregistrement d'audit soit disponible une fois qu'un événement s'est produit ?**

La plupart des données d'audit sont disponibles en 30 minutes, mais il peut s'écouler jusqu'à 24 heures après un événement pour que l'entrée du journal d'audit correspondante s'affiche dans les résultats de la recherche. Consultez le tableau de la section [Conditions requises pour effectuer une recherche dans le journal d'audit](#requirements-to-search-the-audit-log) de cet article qui indique le temps nécessaire pour que les événements des différents services soient disponibles.

**Pendant combien de temps les enregistrements d'audit sont-ils conservés ?**

Comme expliqué précédemment, les enregistrements d'audit des activités effectuées par les utilisateurs disposant d'une licence Office 365 E5 ou Microsoft E5 (ou par les utilisateurs disposant d'une licence complémentaire Microsoft 365 E5) sont conservés pendant un an. Pour tous les autres abonnements prenant en charge la journalisation d'audit unifiée, les enregistrements d'audit sont conservés pendant 90 jours.

**Puis-je accéder aux données d'audit par programme ?**

Oui. L'API Activité de gestion Office 365 est utilisée pour récupérer les journaux d'audit par programme. Pour commencer, consultez l'article [Prise en main des API de gestion Office 365](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis).

**Existe-t-il d'autres méthodes pour obtenir des journaux d'audit autres que l'utilisation du centre de sécurité et de conformité ou de l'API Activité de gestion Office 365 ?**

Non. Ce sont les deux seuls moyens d'obtenir les données du service d'audit.

**Est-ce que je dois activer l'audit de chaque service pour lequel je souhaite capturer les journaux d'audit ?**

Dans la plupart des services, l’audit est activé par défaut une fois que vous avez activé l’audit pour votre organisation, comme décrit dans la section [Configuration requise pour la recherche dans le journal d’audit](#requirements-to-search-the-audit-log) dans cet article.

**Le service d'audit prend-il en charge la suppression des enregistrements en double ?**

Non. Le pipeline de services d'audit fonctionne quasiment en temps réel et ne peut donc pas prendre en charge la déduplication.

**Les données d'audit circulent-elles entre les zones géographiques ?**

Non. Nous contrôlons actuellement les déploiements de pipeline dans les régions NA (Amérique du Nord), EMEA (Europe, Moyen-Orient et Afrique) et APAC (Asie-Pacifique). Cependant, nous pouvons faire circuler les données entre ces régions pour l'équilibrage de charge et uniquement lors de problèmes de site en direct. Lorsque nous effectuons ces activités, les données en transit sont chiffrées.

**Les données d'audit sont-elles chiffrées ?**

Les données d'audit sont stockées dans des boîtes aux lettres Exchange (données au repos) dans la même région dans laquelle le pipeline d'audit unifié est déployé. Les données de boîte aux lettres au repos ne sont pas chiffrées par Exchange. Toutefois, le chiffrement au niveau du service crypte toutes les données de boîte aux lettres car les serveurs Exchange des centres de données Microsoft sont chiffrés via BitLocker. Si vous souhaitez en savoir plus, consultez l'article [Chiffrement Office 365 pour Skype Entreprise, OneDrive Entreprise, SharePoint Online et Exchange Online](office-365-encryption-for-skype-onedrive-sharepoint-and-exchange.md).

Les données de messagerie en transit sont toujours chiffrées.
