---
title: Rechercher des activités eDiscovery dans le journal d’audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.collection: M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: 67cc7f42-a53d-4751-b929-6005c80798f7
description: Découvrez quels événements sont consignés lorsque les utilisateurs affectés aux autorisations eDiscovery effectuent une recherche de contenu, une découverte électronique principale et des tâches Advanced eDiscovery dans le Centre de conformité Microsoft 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: e033864b15032e66995be439e1de750da06e988b
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60151013"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Rechercher des activités eDiscovery dans le journal d’audit

Les activités liées à la recherche de contenu et à la découverte électronique (pour core eDiscovery et Advanced eDiscovery) effectuées dans Centre de conformité Microsoft 365 ou en exécutant les cmdlets PowerShell correspondantes sont enregistrées dans le journal d’audit. Les événements sont consignés lorsque les administrateurs ou les gestionnaires eDiscovery (ou tout utilisateur 2013 2013 2013) effectuent les tâches de recherche de contenu et de découverte électronique principale suivantes dans le Centre de conformité Microsoft 365 :
  
- Création et gestion de cas principaux Advanced eDiscovery de gestion

- Création, démarrage et modification de recherches de contenu

- Effectuer des actions de recherche, telles que l’aperçu, l’exportation et la suppression des résultats de recherche

- Gestion des dépositaires et des ensembles de révision dans Advanced eDiscovery

- Configuration du filtrage des autorisations pour la recherche de contenu

- gestion du rôle d’administrateur eDiscovery.
  
Pour plus d’informations sur la recherche dans le journal d’audit, les autorisations requises et l’exportation des résultats de recherche, voir Rechercher dans le journal [d’audit](search-the-audit-log-in-security-and-compliance.md)dans le Centre de conformité Microsoft 365 .
  
## <a name="how-to-search-for-and-view-ediscovery-activities"></a>Comment rechercher et afficher les activités eDiscovery

Actuellement, vous devez faire quelques actions spécifiques pour afficher les activités eDiscovery dans le journal d’audit. Voici comment procéder.
  
1. Allez sur <https://compliance.microsoft.com> et connectez-vous à l’aide de votre compte professionnel ou scolaire.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur **Audit.**

3. Dans la liste des **activités,** sous activités **eDiscovery** ou Advanced eDiscovery activités **de** découverte électronique, cliquez sur une ou plusieurs activités à rechercher.

    > [!NOTE]
    > La **liste** de listes des activités inclut également un groupe d’activités nommées activités de **cmdlet eDiscovery** qui retournent des enregistrements à partir du journal d’audit de la cmdlet.
  
4. Sélectionnez une plage de dates et d’heures pour afficher les événements eDiscovery qui se sont produits au cours de cette période.

5. Dans la **zone Utilisateurs,** sélectionnez un ou plusieurs utilisateurs pour afficher les résultats de la recherche. Laissez cette zone vide pour renvoyer des entrées pour tous les utilisateurs.

6. Cliquez sur **Rechercher** pour effectuer la recherche à l’aide de vos critères de recherche. 

7. Une fois les résultats de la  recherche affichés, vous pouvez cliquer sur Filtrer les résultats pour filtrer ou trier les enregistrements d’activité résultants. Malheureusement, vous ne pouvez pas utiliser le filtrage pour exclure explicitement certaines activités. 

8. Pour afficher les détails d’une activité, cliquez sur l’enregistrement d’activité dans la liste des résultats de recherche. 

    Une page **volante Détails** s’affiche et contient les propriétés détaillées de l’enregistrement d’événement. Pour afficher des détails supplémentaires, cliquez sur **Plus d’informations.** Pour obtenir une description de ces propriétés, consultez la section Propriétés détaillées des activités [eDiscovery.](#detailed-properties-for-ediscovery-activities)

9. Si vous le souhaitez, vous pouvez exporter les résultats de recherche du journal d’audit dans un fichier CSV, puis utiliser la fonctionnalité power query Excel pour mettre en forme et filtrer ces enregistrements. Pour plus d’informations, consultez [Exporter, configurer et afficher des enregistrements du journal d’audit](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>Activités de découverte électronique

Le tableau suivant décrit les activités de recherche de contenu et de découverte électronique principale qui sont enregistrées lorsqu’un administrateur ou un gestionnaire eDiscovery effectue une activité liée à eDiscovery à l’aide du Centre de conformité Microsoft 365. Certaines activités effectuées dans Advanced eDiscovery peuvent être renvoyées lorsque vous recherchez des activités dans cette liste.
  
> [!NOTE]
> Les activités eDiscovery décrites dans cette section fournissent des informations similaires aux activités de cmdlet eDiscovery décrites dans la section suivante. Nous vous recommandons d’utiliser les activités eDiscovery décrites dans cette section, car elles apparaîtront dans les résultats de recherche du journal d’audit dans un délai de 30 minutes. L’apparition des activités de cmdlet eDiscovery dans les résultats de la recherche dans le journal d’audit peut prendre jusqu’à 24 heures.
  
|**Nom convivial**|**Opération**|**Cmdlet correspondante**|**Description**|
|:-----|:-----|:-----|:-----|
|Membre ajouté au cas eDiscovery  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |Un utilisateur a été ajouté en tant que membre d’un cas eDiscovery. En tant que membre d’un cas, un utilisateur peut effectuer diverses tâches liées à la cas, selon qu’il a reçu ou non les autorisations nécessaires.  <br/> |
|Recherche de contenu modifiée  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |Une recherche de contenu existante a été modifiée. Les modifications peuvent inclure l’ajout ou la suppression d’emplacements de contenu ou la modification de la requête de recherche.  <br/> |
|Changement de l’appartenance à l’administrateur eDiscovery  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |La liste des administrateurs eDiscovery de votre organisation a été modifiée. Cette activité est consignée lorsque la liste des administrateurs eDiscovery est remplacée par un groupe de nouveaux utilisateurs. Si un seul utilisateur est ajouté ou supprimé, l’opération CaseAdminAdded est enregistrée.  <br/> |
|Cas eDiscovery modifié  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |Un cas eDiscovery a été modifié. Les modifications incluent la fermeture d’un cas ouvert ou la réouverture d’un cas fermé.  <br/> |
|Changement de l’appartenance au cas eDiscovery  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |La liste d’appartenance d’un cas eDiscovery a été modifiée. Cette activité est enregistrée lorsque tous les membres sont remplacés par un groupe de nouveaux utilisateurs. Si un seul membre est ajouté ou supprimé, l’opération CaseMemberAdded ou CaseMemberRemoved est enregistrée.  <br/> |
|Filtre d’autorisations de recherche modifié  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Un filtre d’autorisations de recherche a été modifié.  <br/> |
|Requête de recherche modifiée pour la attente de cas eDiscovery  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |Une attente basée sur une requête associée à un cas eDiscovery a été modifiée. Les modifications possibles incluent la modification de la requête ou de la plage de dates pour une mise en attente basée sur une requête.  <br/> |
|Élément d’aperçu de recherche de contenu téléchargé  <br/> |PreviewItemDownloaded  <br/> |S/O  <br/> |Un utilisateur a téléchargé un élément sur son  ordinateur local (en cliquant sur le lien Télécharger l’élément d’origine) lors de l’aperçu des résultats de recherche.  <br/> |
|Élément d’aperçu de recherche de contenu répertorié  <br/> |PreviewItemListed  <br/> |S/O  <br/> |Un utilisateur a **cliqué** sur les résultats de recherche d’aperçu pour afficher la page des résultats de la recherche d’aperçu, qui répertorie jusqu’à 1 000 éléments à partir des résultats d’une recherche.  <br/> |
|Élément d’aperçu de recherche de contenu présenté  <br/> |PreviewItemRendered  <br/> |S/O  <br/> |Un gestionnaire eDiscovery a vu un élément en cliquant dessus lors de l’aperçu des résultats de recherche.  <br/> |
|Recherche de contenu créée  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |Une nouvelle recherche de contenu a été créée.  <br/> |
|Administrateur eDiscovery créé  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |Un utilisateur a été ajouté en tant qu’administrateur eDiscovery dans l’organisation.  <br/> |
|Cas eDiscovery créé  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Un cas eDiscovery a été créé. Lorsqu’un cas est créé, vous ne devez lui donner qu’un nom. D’autres tâches liées à la cas, telles que l’ajout de membres, la création de holds et la création de recherches de contenu associées au cas, entraînent la consigner d’autres événements.  <br/> |
|Filtre d’autorisations de recherche créé  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Un filtre d’autorisations de recherche a été créé.  <br/> |
|Requête de recherche créée pour la attente de cas eDiscovery  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |Une attente basée sur une requête associée à un cas eDiscovery a été créée.  <br/> |
|Recherche de contenu supprimée  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |Une recherche de contenu existante a été supprimée.  <br/> |
|Administrateur eDiscovery supprimé  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |Un administrateur eDiscovery a été supprimé de votre organisation.  <br/> |
|Cas de découverte électronique supprimée  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |Un cas eDiscovery a été supprimé. Toute attente associée au cas doit être supprimée avant de pouvoir être supprimée.  <br/> |
|Filtre des autorisations de recherche supprimées  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Un filtre d’autorisations de recherche a été supprimé.  <br/> |
|Requête de recherche supprimée pour la attente de cas eDiscovery  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |Une attente basée sur une requête associée à un cas eDiscovery a été supprimée. La suppression de la requête de la attente est souvent le résultat de la suppression d’une attente. Lorsqu’une requête de mise en attente ou de mise en attente est supprimée, les emplacements de contenu qui étaient en attente sont libérés.  <br/> |
|Exportation téléchargée de la recherche de contenu  <br/> |SearchExportDownloaded  <br/> |S/O  <br/> |Un utilisateur a téléchargé les résultats d’une recherche de contenu sur son ordinateur local. Une **exportation démarrée de l’activité** de recherche de contenu doit être lancée avant que les résultats de la recherche ne soient téléchargés.  <br/> |
|Résultats prévisualés de la recherche de contenu  <br/> |SearchPreviewed  <br/> |S/O  <br/> |Un utilisateur a aperçu des résultats d’une recherche de contenu.  <br/> |
|Résultats supprimés de la recherche de contenu  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |Un utilisateur a purgé les résultats d’une recherche de contenu en exécutant la commande **New-ComplianceSearchAction -Purge.**  <br/> |
|Suppression de l’analyse de la recherche de contenu  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |Une action de préparation de recherche de contenu (pour préparer les résultats de la Advanced eDiscovery) a été supprimée. Si l’action de préparation a moins de deux semaines, les résultats de la recherche qui ont été préparés pour la Advanced eDiscovery ont été supprimés de la Microsoft Azure de stockage. Si l’action de préparation date de plus de 2 semaines, cet événement indique que seule l’action de préparation correspondante a été supprimée.  <br/> |
|Suppression de l’exportation de la recherche de contenu  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |Une action d’exportation de recherche de contenu a été supprimée. Si l’action d’exportation a eu moins de deux semaines, les résultats de la recherche qui ont été téléchargés vers la Microsoft Azure de stockage ont été supprimés. Si l’action d’exportation date de plus de 2 semaines, cet événement indique que seule l’action d’exportation correspondante a été supprimée.  <br/> |
|Membre supprimé du cas eDiscovery  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |Un utilisateur a été supprimé en tant que membre d’un cas eDiscovery.  <br/> |
|Suppression des résultats d’aperçu de la recherche de contenu  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |Une action d’aperçu de recherche de contenu a été supprimée.  <br/> |
|Action de purge supprimée effectuée sur la recherche de contenu  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |Une action de purge de recherche de contenu a été supprimée.  <br/> |
|Rapport de recherche supprimé  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |Une action de rapport d’exportation de recherche de contenu a été supprimée.  <br/> |
|Analyse démarrée de la recherche de contenu  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |Les résultats d’une recherche de contenu ont été préparés pour analyse dans Advanced eDiscovery.  <br/> |
|Recherche de contenu démarrée  <br/> |SearchStarted  <br/> |Start-ComplianceSearch  <br/> |Une recherche de contenu a été lancée. Lorsque vous créez ou modifiez une recherche de contenu à l’Centre de conformité Microsoft 365, la recherche est automatiquement démarrée.<br/> |
|Exportation démarrée de la recherche de contenu  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |Un utilisateur a exporté les résultats d’une recherche de contenu.  <br/> |
|Rapport d’exportation démarré  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |Un utilisateur a exporté un rapport de recherche de contenu.  <br/> |
|Recherche de contenu arrêtée  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |Un utilisateur a arrêté une recherche de contenu.  <br/> |
|(aucun)|CaseViewed|Get-ComplianceCase|Un utilisateur a vu un cas eDiscovery principal dans le centre de conformité. L’enregistrement d’audit pour cet événement inclut le nom du cas qui a été vu. |
|(aucun)|SearchViewed|Get-ComplianceSearch|Un utilisateur a vu une recherche de contenu dans  le centre de conformité en accédant à la recherche sous l’onglet Recherches dans un cas core eDiscovery ou en y accédant sur la **page** de recherche de contenu. L’enregistrement d’audit pour cet événement inclut l’identité de la recherche qui a été vue.|
|(aucun)|ViewedSearchExported|Get-ComplianceSearchAction -Export|Un utilisateur a vu une exportation de recherche de contenu dans le centre de conformité en accédant à l’exportation sous l’onglet Exportation **sur** la page **de recherche de** contenu. Cette activité est également consignée lorsqu’un utilisateur voit une exportation associée à un cas core eDiscovery.|
|(aucun)|ViewedSearchPreviewed|Get-ComplianceSearchAction -Preview|Un utilisateur a aperçu des résultats d’une recherche de contenu dans le centre de conformité. Cette activité est également consignée lorsqu’un utilisateur affiche un aperçu des résultats d’une recherche associée à un cas core eDiscovery.|
|||||
  
## <a name="advanced-ediscovery-activities"></a>Activités avancées eDiscovery

Le tableau suivant décrit les activités Advanced eDiscovery journal d’audit. Ces activités peuvent être utilisées pour vous aider à suivre la progression de l’activité dans Advanced eDiscovery cas.

|**Nom convivial**|**Opération**|**Description**|
|:-----|:-----|:-----|
|Ajouter des données dans un autre ensemble à réviser|AddWorkingSetQueryToWorkingSet|L’utilisateur a ajouté des documents d’un ensemble à réviser à un autre.|
|Données ajoutées au groupe à réviser|AddQueryToWorkingSet|Un utilisateur a ajouté les résultats de la recherche à partir d’une recherche de contenu associée à un cas avancé d’eDiscovery dans un groupe de révision.|
|Ajout de données ne relevant pas de Microsoft 365 à un jeu à réviser|AddNonOffice365DataToWorkingSet|L’utilisateur a ajouté des données ne relevant pas de Microsoft 365 à un jeu à réviser.|
|Ajout de documents corrigés au groupe révision|AddRemediatedData|L’utilisateur charge les documents qui comportent des erreurs d’indexation qui ont été corrigées dans un groupe de révision.|
|Données analysées dans le groupe révision|RunAlgo|L’utilisateur a exécuté Analytics sur les documents d’un groupe de révision.|
|Document annoté dans le groupe révision|AnnotateDocument|L’utilisateur a annoté un document dans un groupe de révision. L’annotation inclut rédiger du contenu dans un document.|
|Ensembles chargés comparés|LoadComparisonJob|Un utilisateur a comparé deux ensembles chargés différents dans un groupe de révision. Un ensemble chargé est activé lorsque les données d’une recherche de contenu associées au cas sont ajoutées à un groupe de révision.|
|Documents rédigés convertis au format PDF|BurnJob|L’utilisateur a converti tous les documents rédigés dans un ensemble de révision en fichiers PDF.|
|Ensemble de révision créée|CreateWorkingSet|L’utilisateur a créé un groupe de révision.|
|Configuration de la recherche de révision créée|CreateWorkingSetSearch|L’utilisateur a créé une requête de recherche qui effectue une recherche dans les documents d’un groupe de révision.|
|Balise créée|CreateTag|Un utilisateur a créé un groupe de balises dans un ensemble de révision. Un groupe de balises peut contenir une ou plusieurs balises enfant. Ces balises sont ensuite utilisées pour baliser des documents dans le groupe révision.|
|Recherche de la révision supprimée|DeleteWorkingSetSearch|Un utilisateur a supprimé une requête de recherche dans un groupe de révision.|
|Balise supprimée|DeleteTag|Un utilisateur a supprimé une balise ou une balise de groupe dans un groupe de révision.|
|Document téléchargé|DownloadDocument|Un utilisateur a téléchargé un document à partir d’un groupe de révision.|
|Balise modifiée|UpdateTag|Un utilisateur a modifié une balise dans un groupe de révision.|
|Exporter des documents d’un groupe de révision|ExportJob|L’utilisateur a exporté les documents à partir d’un groupe de révision.|
|Paramètre de casse modifié|UpdateCaseSettings|L’utilisateur a modifié les paramètres de casse. Les paramètres de casse incluent les informations de casse, les autorisations d’accès et les paramètres qui contrôlent le comportement des recherches et analyses.|
|Configuration de la recherche de révision modifiée|UpdateWorkingSetSearch|Un utilisateur a modifié une requête de recherche dans un groupe de révision.|
|Aperçu de configuration de la recherche de révision|PreviewWorkingSetSearch|Un utilisateur a visualisé les résultats d’une requête de recherche dans un ensemble de révision.|
|Documents d’erreur rectifiés|ErrorRemediationJob|L’utilisateur corrige les fichiers qui contiennent des erreurs d’indexation.|
|Document balisé|TagFiles|L’utilisateur a balisé un document dans un groupe de révision.|
|Résultats avec indicateur d’une requête|TagJob|L’utilisateur balise tous les documents qui correspondent aux critères de la requête de recherche dans un ensemble de révision.|
|Document visualisé dans le groupe révision|ViewDocument|Un utilisateur a consulté un document dans un groupe de révision.|
|||

## <a name="ediscovery-cmdlet-activities"></a>Activités de cmdlet eDiscovery

Le tableau suivant répertorie les enregistrements du journal d’audit des cmdlet qui sont enregistrés lorsqu’un administrateur ou un utilisateur effectue une activité liée à eDiscovery à l’aide du centre de conformité ou en exécutant la cmdlet correspondante dans le Centre de sécurité & conformité PowerShell. Les informations détaillées dans l’enregistrement du journal d’audit sont différentes pour les activités de cmdlet répertoriées dans ce tableau et les activités eDiscovery décrites dans la section précédente.
  
Comme indiqué précédemment, l’apparition des activités de cmdlet eDiscovery dans les résultats de la recherche dans le journal d’audit peut prendre jusqu’à 24 heures.
  
> [!TIP]
> Les cmdlets de la colonne **Opération** du tableau suivant sont liées à la rubrique d’aide de cmdlet correspondante sur TechNet. Pour obtenir une description des paramètres disponibles pour chaque cmdlet, voir la rubrique d’aide de la cmdlet. Le paramètre et la valeur de paramètre qui ont été utilisés avec une cmdlet sont inclus dans l’entrée du journal d’audit pour chaque activité de cmdlet eDiscovery enregistrée. 
  
|**Nom convivial**|**Opération (cmdlet)**|**Description**|
|:-----|:-----|:-----|
|Mis en attente dans le cas eDiscovery  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |Une attente a été créée pour un cas eDiscovery. Une attente peut être créée avec ou sans spécifier de source de contenu. Si des sources de contenu sont spécifiées, elles sont identifiées dans l’entrée du journal d’audit.  <br/> |
|Attente supprimée dans un cas eDiscovery  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |Une attente associée à un cas eDiscovery a été supprimée. La suppression d’une mise en attente libère tous les emplacements de contenu de la mise en attente. La suppression de la attente entraîne également la suppression des règles de cas associées à la attente (voir **Remove-CaseHoldRule ci-dessous).**  <br/> |
|Attente modifiée dans le cas eDiscovery  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |Une attente associée à une découverte électronique a été modifiée. Les modifications possibles incluent l’ajout ou la suppression d’emplacements de contenu ou la désactivation de l’attente.  <br/> |
|Requête de recherche créée pour la attente de cas eDiscovery  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |Une attente basée sur une requête associée à un cas eDiscovery a été créée.  <br/> |
|Requête de recherche supprimée pour la attente de cas eDiscovery  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |Une attente basée sur une requête associée à un cas eDiscovery a été supprimée. La suppression de la requête de la attente est souvent le résultat de la suppression d’une attente. Lorsqu’une requête de mise en attente ou de mise en attente est supprimée, les emplacements de contenu qui étaient en attente sont libérés.  <br/> |
|Requête de recherche modifiée pour la attente de cas eDiscovery  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |Une attente basée sur une requête associée à un cas eDiscovery a été modifiée. Les modifications possibles incluent la modification de la requête ou de la plage de dates pour une mise en attente basée sur une requête.  <br/> |
|Cas eDiscovery créé  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Un cas eDiscovery a été créé. Lorsqu’un cas est créé, vous ne devez lui donner qu’un nom. D’autres tâches liées à la cas, telles que l’ajout de membres, la création de holds et la création de recherches de contenu associées au cas, entraînent la consigner d’autres événements.  <br/> |
|Cas de découverte électronique supprimée  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |Un cas eDiscovery a été supprimé. Toute attente associée au cas doit être supprimée avant de pouvoir être supprimée.  <br/> |
|Cas eDiscovery modifié  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |Un cas eDiscovery a été modifié. Les modifications incluent la fermeture d’un cas ouvert ou la réouverture d’un cas fermé.  <br/> |
|Membre ajouté au cas eDiscovery  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |Un utilisateur a été ajouté en tant que membre d’un cas eDiscovery. En tant que membre d’un cas, un utilisateur peut effectuer diverses tâches liées à la cas, selon qu’il a reçu ou non les autorisations nécessaires.  <br/> |
|Membre supprimé du cas eDiscovery  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |Un utilisateur a été supprimé en tant que membre d’un cas eDiscovery.  <br/> |
|Changement de l’appartenance au cas eDiscovery  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |La liste d’appartenance d’un cas eDiscovery a été modifiée. Cette activité est enregistrée lorsque tous les membres sont remplacés par un groupe de nouveaux utilisateurs. Si un seul membre est ajouté ou supprimé, l’opération **Add-ComplianceCaseMember** ou **Remove-ComplianceCaseMember** est enregistrée.  <br/> |
|Recherche de contenu créée  <br/> |[New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) <br/> |Une nouvelle recherche de contenu a été créée.  <br/> |
|Recherche de contenu supprimée  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |Une recherche de contenu existante a été supprimée.  <br/> |
|Recherche de contenu modifiée  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |Une recherche de contenu existante a été modifiée. Les modifications peuvent inclure l’ajout ou la suppression d’emplacements de contenu recherchés et la modification de la requête de recherche.  <br/> |
|Recherche de contenu démarrée  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |Une recherche de contenu a été lancée. Lorsque vous créez ou modifiez une recherche de contenu à l’aide de l’interface utilisateur graphique du centre de conformité, la recherche est automatiquement démarrée. Si vous créez ou modifiez une recherche à l’aide de la cmdlet **New-ComplianceSearch** ou **Set-ComplianceSearch,** vous devez exécuter la cmdlet **Start-ComplianceSearch** pour démarrer la recherche.  <br/> |
|Recherche de contenu arrêtée  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |Une recherche de contenu en cours d’exécution a été arrêtée.  <br/> |
|Action de recherche de contenu créée  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |Une action de recherche de contenu a été créée. Les actions de recherche de contenu incluent l’aperçu des résultats de recherche, l’exportation des résultats de recherche, la préparation des résultats de recherche pour analyse dans Advanced eDiscovery et la suppression définitive des éléments qui correspondent aux critères de recherche d’une recherche de contenu.  <br/> |
|Action de recherche de contenu supprimée  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |Une action de recherche de contenu a été supprimée.  <br/> |
|Filtre d’autorisations de recherche créé  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Un filtre d’autorisations de recherche a été créé.  <br/> |
|Filtre des autorisations de recherche supprimées  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Un filtre d’autorisations de recherche a été supprimé.  <br/> |
|Filtre d’autorisations de recherche modifié  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Un filtre d’autorisations de recherche a été modifié.  <br/> |
|Administrateur eDiscovery créé  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |Un utilisateur a été ajouté en tant qu’administrateur eDiscovery dans votre organisation.  <br/> |
|Administrateur eDiscovery supprimé  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |Un administrateur eDiscovery a été supprimé de votre organisation.  <br/> |
|Changement de l’appartenance à l’administrateur eDiscovery  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |La liste des administrateurs eDiscovery de votre organisation a été modifiée. Cette activité est consignée lorsque la liste des administrateurs eDiscovery est remplacée par un groupe de nouveaux utilisateurs. Si un seul utilisateur est ajouté ou supprimé, l’opération **Add-eDiscoveryCaseAdmin** ou **Remove-eDiscoveryCaseAdmin** est enregistrée.  <br/> |
|(aucun)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|Cette activité est consignée lorsqu’un utilisateur a vu une liste de core eDiscovery ou Advanced eDiscovery cas. Cette activité est également consignée lorsqu’un utilisateur voit un cas spécifique dans Core eDiscovery. Lorsqu’un utilisateur affiche un cas spécifique, l’enregistrement d’audit inclut l’identité du cas qui a été vu. Si l’utilisateur n’a vu qu’une liste de cas, l’enregistrement d’audit ne contient pas d’identité de cas.|
|(aucun)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|Cette activité est consignée lorsqu’un utilisateur a vu une liste de recherches de contenu ou de recherches associées à un cas core eDiscovery. Cette activité est également consignée lorsqu’un utilisateur voit une recherche de contenu spécifique ou une recherche spécifique associée à un cas core eDiscovery. Lorsqu’un utilisateur affiche une recherche spécifique, l’enregistrement d’audit inclut l’identité de la recherche qui a été vue. Si l’utilisateur n’a vu qu’une liste de recherches, l’enregistrement d’audit ne contient pas d’identité de recherche.
|(aucun)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|Cette activité est enregistrée lorsqu’un utilisateur a vu une liste d’actions de recherche de conformité (telles que les exportations, les aperçus ou les purges) ou les actions associées à un cas core eDiscovery. Cette activité est également enregistrée lorsqu’un utilisateur voit une action de recherche de conformité spécifique (par exemple, une exportation) ou une action spécifique associée à un cas core eDiscovery. Lorsqu’un utilisateur affiche une action de recherche, l’enregistrement d’audit inclut l’identité de l’action de recherche qui a été vue. Si l’utilisateur n’a vu qu’une liste d’actions, l’enregistrement d’audit ne contient pas d’identité d’action.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>Propriétés détaillées des activités eDiscovery

Le tableau suivant décrit les propriétés incluses dans la page volante d’une activité eDiscovery répertoriée dans les résultats de la recherche. Ces propriétés sont également incluses dans le fichier CSV lorsque vous exportez les résultats de recherche du journal d’audit. Un enregistrement du journal d’audit pour une activité eDiscovery n’inclut pas toutes les propriétés détaillées répertoriées ci-dessous.
  
> [!TIP]
> Lorsque vous exportez les résultats de la recherche, le fichier CSV contient une colonne nommée **AudtiData**, qui contient les propriétés détaillées décrites dans le tableau suivant dans une propriété à valeurs multiples. Vous pouvez utiliser la fonctionnalité Power Query dans Excel pour fractionner cette colonne en plusieurs colonnes afin que chaque propriété possède sa propre colonne. Cela vous permettra de trier et de filtrer une ou plusieurs de ces propriétés. Pour plus d’informations, consultez la section « Exporter les résultats de la recherche dans un fichier » dans le journal [d’audit.](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file) 
  
|**Propriété**|**Description**|
|:-----|:-----|
|Cas  <br/> |Identité (GUID) du cas eDiscovery qui a été créé, modifié ou supprimé.  <br/> |
|ClientApplication  <br/> |Les activités de cmdlet eDiscovery ont une valeur **EMC** pour cette propriété. Cela indique que l’activité a été effectuée à l’aide de l’interface graphique graphique du centre de conformité ou en exécutant l’cmdlet dans PowerShell.  <br/> |
|ClientIP  <br/> |Adresse IP du périphérique utilisé lors de la journalisation de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.  <br/> |
|ClientRequestId  <br/> | Pour les activités eDiscovery, cette propriété est généralement vide.  <br/> |
|CmdletVersion  <br/> |Numéro de build de la version du centre de conformité en cours d’exécution dans votre organisation.  <br/> |
|CreationTime  <br/> |Date et heure au moment UTC (Temps universel coordonné) de fin de l’activité eDiscovery.  <br/> |
|EffectiveOrganization  <br/> |Nom de l’organisation Microsoft 365.  <br/> |
|ExchangeLocations  <br/> |Le Exchange Online boîtes aux lettres incluses dans une recherche de contenu ou placées en attente dans un cas eDiscovery.  <br/> |
|Exclusions  <br/> |Emplacements de boîtes aux lettres ou de sites exclus d’une recherche de contenu ou d’une attente dans un cas eDiscovery.  <br/> |
|ExtendedProperties  <br/> |Propriétés supplémentaires d’une recherche de contenu, d’une action de recherche de contenu ou d’un cas de découverte électronique, telles que le GUID de l’objet et les paramètres de cmdlet et de cmdlet correspondants qui ont été utilisés lors de l’activité.  <br/> |
|ID  <br/> |ID de l’entrée de rapport. L’ID identifie de manière unique l’entrée du journal d’audit.  <br/> |
|NonPIIParameters  <br/> |Liste des paramètres (sans aucune valeur) qui ont été utilisés avec la cmdlet identifiée dans la propriété Operation. Les paramètres répertoriés dans cette propriété sont les mêmes que ceux répertoriés dans la propriété Parameters.  <br/> |
|ObjectId  <br/> |GUID ou nom de l’objet (par exemple, une recherche de contenu ou un cas core eDiscovery) qui a été créé, accédé, modifié ou supprimé par l’activité répertoriée dans la propriété Operation. Cet objet est également identifié dans la colonne Élément dans les résultats de recherche du journal d’audit.  <br/> |
|ObjectType  <br/> |Le type d’objet eDiscovery que l’utilisateur a créé, supprimé ou modifié ; par exemple, une action de recherche de contenu (aperçu, exportation ou purge), un cas eDiscovery ou une recherche de contenu.  <br/> |
|Opération  <br/> |Nom de l’opération qui correspond à l’activité eDiscovery qui a été effectuée.  <br/> |
|OrganizationId  <br/> |GUID de votre organisation Microsoft 365 entreprise.  <br/> |
|Paramètres  <br/> |Nom et valeur des paramètres utilisés avec la cmdlet correspondante.  <br/> |
|PublicFolderLocations  <br/> |Emplacements de dossiers publics Exchange Online inclus dans une recherche de contenu ou placés en attente dans un cas eDiscovery.  <br/> |
|Requête  <br/> |Requête de recherche associée à l’activité, telle qu’une recherche de contenu ou une attente basée sur une requête.  <br/> |
|RecordType  <br/> |Type d’opération indiqué par l’enregistrement. La valeur **18** indique un événement lié à une activité répertoriée dans la section activités de [la cmdlet eDiscovery.](#ediscovery-cmdlet-activities) La valeur **24** indique un événement lié à une activité répertoriée dans la section Comment rechercher et afficher les activités [eDiscovery.](#how-to-search-for-and-view-ediscovery-activities)  <br/> |
|ResultStatus  <br/> |Indique si l’action (indiquée dans la propriété Operation) a réussi ou non.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Indique que l’activité était un événement du centre de conformité. Toutes les activités eDiscovery auront une valeur **de 0** pour cette propriété.  <br/> |
|SharepointLocations  <br/> |Les SharePoint sites en ligne inclus dans une recherche de contenu ou placés en attente dans un cas eDiscovery.  <br/> |
|StartTime  <br/> |Date et heure du début de l’activité eDiscovery en temps universel coordonné (UTC).  <br/> |
|UserId  <br/> |L’utilisateur qui a effectué l’activité (spécifiée dans la propriété Operation) qui a entraîné la journal de l’enregistrement. Les enregistrements pour l’activité eDiscovery effectuée par les comptes système (tels que NT AUTHORITY\SYSTEM) sont également inclus dans le journal d’audit.  <br/> |
|UserKey  <br/> |Autre ID pour l’utilisateur identifié dans la propriété UserId. Pour les activités eDiscovery, la valeur de cette propriété est généralement identique à celle de la propriété UserId.  <br/> |
|UserServicePlan  <br/> |Abonnement utilisé par votre organisation. Pour les activités eDiscovery, cette propriété est généralement vide.  <br/> |
|UserType  <br/> |Type d’utilisateur ayant effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur.  <br/> 0 Utilisateur normal. 2 Administrateur de votre organisation. 3 Un compte système d’administrateur de centre de données Microsoft ou de centre de données. 4 Un compte système. 5 Application. 6 Principal de service. |
|Version  <br/> |Indique le numéro de version de l’activité (identifiée par la propriété Operation) enregistrée.  <br/> |
|Charge de travail  <br/> |Service dans lequel l’activité s’est produite. Pour les activités eDiscovery, la valeur **est SecurityComplianceCenter**.  <br/> |
