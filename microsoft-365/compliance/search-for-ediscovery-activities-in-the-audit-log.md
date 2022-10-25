---
title: Rechercher des activités eDiscovery dans le journal d’audit
description: Découvrez les événements enregistrés lorsque les utilisateurs auxquels des autorisations eDiscovery sont affectées effectuent des tâches de recherche de contenu, eDiscovery (Standard) et eDiscovery (Premium) dans le portail de conformité Microsoft Purview.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- tier1
- purview-compliance
- ediscovery
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 48d619ad07d1bd07cfe13c2759a1bcf121e627d8
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688523"
---
# <a name="search-for-ediscovery-activities-in-the-audit-log"></a>Rechercher des activités eDiscovery dans le journal d’audit

Activités liées à la recherche de contenu et à la découverte électronique (pour Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium)) qui sont effectuées dans portail de conformité Microsoft Purview  ou en exécutant les applets de commande PowerShell correspondantes sont enregistrées dans le journal d’audit. Les événements sont enregistrés lorsque des administrateurs ou des gestionnaires eDiscovery (ou des autorisations eDiscovery affectées par l’utilisateur) effectuent les tâches de recherche de contenu et eDiscovery (Standard) suivantes dans le portail de conformité :
  
- Création et gestion des cas eDiscovery (Standard) et eDiscovery (Premium).
- Création, démarrage et modification des recherches de contenu.
- Exécution d’actions de recherche, telles que l’aperçu, l’exportation et la suppression des résultats de recherche.
- Gestion des consignataires et des jeux de révision dans eDiscovery (Premium).
- Configuration du filtrage des autorisations pour la recherche de contenu.
- Gestion du rôle Administrateur eDiscovery.
  
Pour plus d’informations sur la recherche dans le journal d’audit, les autorisations requises et l’exportation des résultats de recherche, consultez [Rechercher dans le journal d’audit dans le portail de conformité](search-the-audit-log-in-security-and-compliance.md).
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-to-search-for-and-view-ediscovery-activities"></a>Comment rechercher et afficher des activités eDiscovery

Actuellement, vous devez effectuer quelques opérations spécifiques pour afficher les activités eDiscovery dans le journal d’audit. Voici comment procéder.
  
1. Accédez au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) et connectez-vous à l’aide de votre compte professionnel ou scolaire.

2. Dans le volet de navigation gauche du portail de conformité, sélectionnez **Audit**.

3. Dans la liste déroulante **Activités** , sous **Activités eDiscovery** ou **Activités eDiscovery (Premium),** sélectionnez une ou plusieurs activités à rechercher.

    > [!NOTE]
    > La liste déroulante **Activités** comprend également un groupe d’activités nommées **activités d’applet de commande eDiscovery** qui retournent des enregistrements à partir du journal d’audit de l’applet de commande.
  
4. Sélectionnez une plage de dates et d’heures pour afficher les événements eDiscovery qui se sont produits au cours de cette période.

5. Dans la zone **Utilisateurs** , sélectionnez un ou plusieurs utilisateurs pour ant afficher les résultats de la recherche. Laissez cette zone vide pour renvoyer les entrées pour tous les utilisateurs.

6. Sélectionnez **Rechercher** pour exécuter la recherche à l’aide de vos critères de recherche.

7. Une fois les résultats de la recherche affichés, vous pouvez sélectionner **Filtrer les résultats** pour filtrer ou trier les enregistrements d’activité résultants. Malheureusement, vous ne pouvez pas utiliser le filtrage pour exclure explicitement certaines activités. 

8. Pour afficher les détails d’une activité, sélectionnez l’enregistrement d’activité dans la liste des résultats de la recherche. 

    Une page volante **Détails** s’affiche et contient les propriétés détaillées de l’enregistrement d’événement. Pour afficher des détails supplémentaires, sélectionnez **Plus d’informations**. Pour obtenir une description de ces propriétés, consultez la section [Propriétés détaillées pour les activités eDiscovery](#detailed-properties-for-ediscovery-activities) .

9. Si vous le souhaitez, vous pouvez exporter les résultats de la recherche dans le journal d’audit dans un fichier CSV, puis utiliser la fonctionnalité Power Query Excel pour mettre en forme et filtrer ces enregistrements. Pour plus d’informations, consultez [Exporter, configurer et afficher des enregistrements du journal d’audit](export-view-audit-log-records.md).

## <a name="ediscovery-activities"></a>Activités de découverte électronique

Le tableau suivant décrit les activités de recherche de contenu et eDiscovery (Standard) qui sont enregistrées lorsqu’un administrateur ou un responsable eDiscovery effectue une activité liée à eDiscovery à l’aide du portail de conformité. Certaines activités effectuées dans eDiscovery (Premium) peuvent être retournées lorsque vous recherchez des activités dans cette liste.
  
> [!NOTE]
> Les activités eDiscovery décrites dans cette section fournissent des informations similaires aux activités d’applet de commande eDiscovery décrites dans la section suivante. Nous vous recommandons d’utiliser les activités eDiscovery décrites dans cette section, car elles apparaîtront dans les résultats de la recherche dans le journal d’audit dans les 30 minutes. L’affichage des activités d’applet de commande eDiscovery dans les résultats de recherche du journal d’audit peut prendre jusqu’à 24 heures.
  
|**Nom convivial**|**Opération**|**Applet de commande correspondante**|**Description**|
|:-----|:-----|:-----|:-----|
|Ajout d’un membre au cas eDiscovery  <br/> |CaseMemberAdded  <br/> |Add-ComplianceCaseMember  <br/> |Un utilisateur a été ajouté en tant que membre d’un cas eDiscovery. En tant que membre d’un cas, un utilisateur peut effectuer diverses tâches liées à un cas selon que les autorisations nécessaires lui ont été attribuées ou non.  <br/> |
|Recherche de contenu modifiée  <br/> |SearchUpdated  <br/> |Set-ComplianceSearch  <br/> |Une recherche de contenu existante a été modifiée. Les modifications peuvent inclure l’ajout ou la suppression d’emplacements de contenu ou la modification de la requête de recherche.  <br/> |
|Modification de l’appartenance de l’administrateur eDiscovery  <br/> |CaseAdminUpdated  <br/> |Update-eDiscoveryCaseAdmin  <br/> |La liste des administrateurs eDiscovery de votre organisation a été modifiée. Cette activité est journalisée lorsque la liste des administrateurs eDiscovery est remplacée par un groupe de nouveaux utilisateurs. Si un seul utilisateur est ajouté ou supprimé, l’opération CaseAdminAdded est journalisée.  <br/> |
|Changement de cas eDiscovery  <br/> |CaseUpdated  <br/> |Set-ComplianceCase  <br/> |Un cas eDiscovery a été modifié. Les modifications incluent la fermeture d’un cas ouvert ou la réouverture d’un cas fermé.  <br/> |
|Modification de l’appartenance au cas eDiscovery  <br/> |CaseMemberUpdated  <br/> |Update-ComplianceCaseMember  <br/> |La liste d’appartenances d’un cas eDiscovery a été modifiée. Cette activité est journalisée lorsque tous les membres sont remplacés par un groupe de nouveaux utilisateurs. Si un seul membre est ajouté ou supprimé, l’opération CaseMemberAdded ou CaseMemberRemoved est journalisée.  <br/> |
|Filtre d’autorisations de recherche modifié  <br/> |SearchPermissionUpdated  <br/> |Set-ComplianceSecurityFilter  <br/> |Un filtre d’autorisations de recherche a été modifié.  <br/> |
|Modification de la requête de recherche pour la conservation de cas eDiscovery  <br/> |HoldUpdated  <br/> |Set-CaseHoldRule  <br/> |Une conservation basée sur les requêtes associée à un cas eDiscovery a été modifiée. Les modifications possibles incluent la modification de la requête ou de la plage de dates pour une conservation basée sur une requête.  <br/> |
|Élément d’aperçu de recherche de contenu téléchargé  <br/> |PreviewItemDownloaded  <br/> |S/O  <br/> |Un utilisateur a téléchargé un élément sur son ordinateur local (en cliquant sur le lien **Télécharger l’élément d’origine** ) lors de l’aperçu des résultats de la recherche.  <br/> |
|Élément d’aperçu de la recherche de contenu répertorié  <br/> |PreviewItemListed  <br/> |S/O  <br/> |Un utilisateur a cliqué sur **Aperçu des résultats de la recherche** pour afficher la page des résultats de recherche en aperçu, qui répertorie jusqu’à 1 000 éléments des résultats d’une recherche.  <br/> |
|Élément d’aperçu de recherche de contenu affiché  <br/> |PreviewItemRendered  <br/> |S/O  <br/> |Un gestionnaire eDiscovery a affiché un élément en cliquant dessus lors de l’aperçu des résultats de la recherche.  <br/> |
|Recherche de contenu créée  <br/> |SearchCreated  <br/> |New-ComplianceSearch  <br/> |Une nouvelle recherche de contenu a été créée.  <br/> |
|Administrateur eDiscovery créé  <br/> |CaseAdminAdded  <br/> |Add-eDiscoveryCaseAdmin  <br/> |Un utilisateur a été ajouté en tant qu’administrateur eDiscovery dans l’organisation.  <br/> |
|Cas eDiscovery créé  <br/> |CaseAdded  <br/> |New-ComplianceCase  <br/> |Un cas eDiscovery a été créé. Lorsqu’un cas est créé, il vous suffit de lui donner un nom. D’autres tâches liées à la casse, telles que l’ajout de membres, la création de conservations et la création de recherches de contenu associées au cas, entraînent la journaliser des événements supplémentaires.  <br/> |
|Filtre d’autorisations de recherche créé  <br/> |SearchPermissionCreated  <br/> |New-ComplianceSecurityFilter  <br/> |Un filtre d’autorisations de recherche a été créé.  <br/> |
|Requête de recherche créée pour la conservation de cas eDiscovery  <br/> |HoldCreated  <br/> |New-CaseHoldRule  <br/> |Une conservation basée sur les requêtes associée à un cas eDiscovery a été créée.  <br/> |
|Recherche de contenu supprimé  <br/> |SearchRemoved  <br/> |Remove-ComplianceSearch  <br/> |Une recherche de contenu existante a été supprimée.  <br/> |
|Administrateur eDiscovery supprimé  <br/> |CaseAdminRemoved  <br/> |Remove-eDiscoveryCaseAdmin  <br/> |Un administrateur eDiscovery a été supprimé de votre organisation.  <br/> |
|Cas eDiscovery supprimé  <br/> |CaseRemoved  <br/> |Remove-ComplianceCase  <br/> |Un cas eDiscovery a été supprimé. Toute conservation associée au cas doit être supprimée avant que le cas puisse être supprimé.  <br/> |
|Filtre d’autorisations de recherche supprimées  <br/> |SearchPermissionRemoved  <br/> |Remove-ComplianceSecurityFilter  <br/> |Un filtre d’autorisations de recherche a été supprimé.  <br/> |
|Requête de recherche supprimée pour la conservation de cas eDiscovery  <br/> |HoldRemoved  <br/> |Remove-CaseHoldRule  <br/> |Une conservation basée sur les requêtes associée à un cas eDiscovery a été supprimée. La suppression de la requête de la conservation est souvent le résultat de la suppression d’une conservation. Lorsqu’une requête de conservation ou de conservation est supprimée, les emplacements de contenu qui étaient en attente sont libérés.  <br/> |
|Exportation téléchargée de la recherche de contenu  <br/> |SearchExportDownloaded  <br/> |S/O  <br/> |Un utilisateur a téléchargé les résultats d’une recherche de contenu sur son ordinateur local. Une **activité de recherche de contenu démarrée** doit être lancée avant que les résultats de la recherche puissent être téléchargés.  <br/> |
|Aperçu des résultats de la recherche de contenu  <br/> |SearchPreviewed  <br/> |S/O  <br/> |Un utilisateur a affiché un aperçu des résultats d’une recherche de contenu.  <br/> |
|Résultats purgés de la recherche de contenu  <br/> |SearchResultsPurged  <br/> |New-ComplianceSearchAction  <br/> |Un utilisateur a vidé les résultats d’une recherche de contenu en exécutant la commande **New-ComplianceSearchAction -Purge** .  <br/> |
|Suppression de l’analyse de la recherche de contenu  <br/> |RemovedSearchResultsSentToZoom  <br/> |Remove-ComplianceSearchAction  <br/> |Une action de préparation de recherche de contenu (pour préparer les résultats de la recherche pour eDiscovery (Premium)) a été supprimée. Si l’action de préparation date de moins de deux semaines, les résultats de recherche préparés pour eDiscovery (Premium) ont été supprimés de la zone de stockage Microsoft Azure. Si l’action de préparation date de plus de 2 semaines, cet événement indique que seule l’action de préparation correspondante a été supprimée.  <br/> |
|Suppression de l’exportation de la recherche de contenu  <br/> |RemovedSearchExported  <br/> |Remove-ComplianceSearchAction  <br/> |Une action d’exportation de recherche de contenu a été supprimée. Si l’action d’exportation date de moins de deux semaines, les résultats de la recherche qui ont été chargés dans la zone de stockage Microsoft Azure ont été supprimés. Si l’action d’exportation date de plus de 2 semaines, cet événement indique que seule l’action d’exportation correspondante a été supprimée.  <br/> |
|Membre supprimé du cas eDiscovery  <br/> |CaseMemberRemoved  <br/> |Remove-ComplianceCaseMember  <br/> |Un utilisateur a été supprimé en tant que membre d’un cas eDiscovery.  <br/> |
|Suppression des résultats de l’aperçu de la recherche de contenu  <br/> |RemovedSearchPreviewed  <br/> |Remove-ComplianceSearchAction  <br/> |Une action d’aperçu de recherche de contenu a été supprimée.  <br/> |
|Suppression de l’action de vidage effectuée sur la recherche de contenu  <br/> |RemovedSearchResultsPurged  <br/> |Remove-ComplianceSearchAction  <br/> |Une action de vidage de recherche de contenu a été supprimée.  <br/> |
|Rapport de recherche supprimé  <br/> |SearchReportRemoved  <br/> |Remove-ComplianceSearchAction  <br/> |Une action de rapport d’exportation de recherche de contenu a été supprimée.  <br/> |
|Début de l’analyse de la recherche de contenu  <br/> |SearchResultsSentToZoom  <br/> |New-ComplianceSearchAction  <br/> |Les résultats d’une recherche de contenu ont été préparés pour analyse dans eDiscovery (Premium).  <br/> |
|Recherche de contenu démarrée  <br/> |SearchStarted  <br/> |Start-ComplianceSearch  <br/> |Une recherche de contenu a été lancée. Lorsque vous créez ou modifiez une recherche de contenu à l’aide du portail de conformité, la recherche est automatiquement démarrée.<br/> |
|Début de l’exportation de la recherche de contenu  <br/> |SearchExported  <br/> |New-ComplianceSearchAction  <br/> |Un utilisateur a exporté les résultats d’une recherche de contenu.  <br/> |
|Rapport d’exportation démarré  <br/> |SearchReport  <br/> |New-ComplianceSearchAction  <br/> |Un utilisateur a exporté un rapport de recherche de contenu.  <br/> |
|Recherche de contenu arrêtée  <br/> |SearchStopped  <br/> |Stop-ComplianceSearch  <br/> |Un utilisateur a arrêté une recherche de contenu.  <br/> |
|(aucun)|CaseViewed|Get-ComplianceCase|Un utilisateur a consulté un cas eDiscovery (Standard) dans le portail de conformité. L’enregistrement d’audit de cet événement inclut le nom du cas qui a été consulté. |
|(aucun)|SearchViewed|Get-ComplianceSearch|Un utilisateur a consulté une recherche de contenu dans le portail de conformité en accédant à la recherche sous l’onglet **Recherches** dans un cas eDiscovery (Standard) ou en y accédant sur la page **de recherche de contenu** . L’enregistrement d’audit de cet événement inclut l’identité de la recherche qui a été consultée.|
|(aucun)|ViewedSearchExported|Get-ComplianceSearchAction -Exporter|Un utilisateur a affiché une exportation de recherche de contenu dans le portail de conformité en accédant à l’exportation sous l’onglet **Exportations** de la page **de recherche de contenu** . Cette activité est également journalisée lorsqu’un utilisateur affiche une exportation associée à un cas eDiscovery (Standard).|
|(aucun)|ViewedSearchPreviewed|Get-ComplianceSearchAction -Préversion|Un utilisateur a affiché un aperçu des résultats d’une recherche de contenu dans le portail de conformité. Cette activité est également journalisée lorsqu’un utilisateur affiche un aperçu des résultats d’une recherche associée à un cas eDiscovery (Standard).|
|||||
  
## <a name="ediscovery-premium-activities"></a>Activités eDiscovery (Premium)

Le tableau suivant décrit les activités eDiscovery (Premium) enregistrées dans le journal d’audit. Ces activités peuvent être utilisées pour vous aider à suivre la progression de l’activité dans un cas eDiscovery (Premium).

|**Nom convivial**|**Opération**|**Description**|
|:-----|:-----|:-----|
|Ajouter des données dans un autre ensemble à réviser|AddWorkingSetQueryToWorkingSet|L’utilisateur a ajouté des documents d’un ensemble à réviser à un autre.|
|Données ajoutées au groupe à réviser|AddQueryToWorkingSet|L’utilisateur a ajouté les résultats de la recherche à partir d’une recherche de contenu associée à un cas eDiscovery (Premium) à un jeu de révision.|
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

## <a name="ediscovery-cmdlet-activities"></a>Activités d’applet de commande eDiscovery

Le tableau suivant répertorie les enregistrements du journal d’audit d’applet de commande qui sont enregistrés lorsqu’un administrateur ou un utilisateur effectue une activité liée à eDiscovery à l’aide du portail de conformité ou en exécutant l’applet de commande correspondante dans Security & Compliance PowerShell. Les informations détaillées dans l’enregistrement du journal d’audit sont différentes pour les activités d’applet de commande répertoriées dans ce tableau et les activités eDiscovery décrites dans la section précédente.
  
Comme indiqué précédemment, l’affichage des activités d’applet de commande eDiscovery dans les résultats de recherche dans le journal d’audit peut prendre jusqu’à 24 heures.
  
> [!TIP]
> Les applets de commande de la colonne **Operation** du tableau suivant sont liées à la rubrique d’aide correspondante sur TechNet. Accédez à la rubrique d’aide sur les applets de commande pour obtenir une description des paramètres disponibles pour chaque applet de commande. Le paramètre et la valeur du paramètre qui ont été utilisés avec une applet de commande sont inclus dans l’entrée du journal d’audit pour chaque activité d’applet de commande eDiscovery journalisée. 
  
|**Nom convivial**|**Opération (applet de commande)**|**Description**|
|:-----|:-----|:-----|
|Conservation créée dans le cas eDiscovery  <br/> |[New-CaseHoldPolicy](/powershell/module/exchange/new-caseholdpolicy) <br/> |Une conservation a été créée pour un cas eDiscovery. Une conservation peut être créée avec ou sans spécification d’une source de contenu. Si des sources de contenu sont spécifiées, elles sont identifiées dans l’entrée du journal d’audit.  <br/> |
|Conservation supprimée d’un cas eDiscovery  <br/> |[Remove-CaseHoldPolicy](/powershell/module/exchange/remove-caseholdpolicy) <br/> |Une conservation associée à un cas eDiscovery a été supprimée. La suppression d’une conservation libère tous les emplacements de contenu de la conservation. La suppression de la conservation entraîne également la suppression des règles de conservation de la casse associées à la conservation (voir **Remove-CaseHoldRule** ci-dessous).  <br/> |
|Conservation modifiée dans le cas eDiscovery  <br/> |[Set-CaseHoldPolicy](/powershell/module/exchange/set-caseholdpolicy) <br/> |Une conservation associée à une eDiscovery a été modifiée. Les modifications possibles incluent l’ajout ou la suppression d’emplacements de contenu ou la désactivation (désactivation) de la conservation.  <br/> |
|Requête de recherche créée pour la conservation de cas eDiscovery  <br/> |[New-CaseHoldRule](/powershell/module/exchange/new-caseholdrule) <br/> |Une conservation basée sur les requêtes associée à un cas eDiscovery a été créée.  <br/> |
|Requête de recherche supprimée pour la conservation de cas eDiscovery  <br/> |[Remove-CaseHoldRule](/powershell/module/exchange/remove-caseholdrule) <br/> |Une conservation basée sur les requêtes associée à un cas eDiscovery a été supprimée. La suppression de la requête de la conservation est souvent le résultat de la suppression d’une conservation. Lorsqu’une requête de conservation ou de conservation est supprimée, les emplacements de contenu qui étaient en attente sont libérés.  <br/> |
|Modification de la requête de recherche pour la conservation de cas eDiscovery  <br/> |[Set-CaseHoldRule](/powershell/module/exchange/set-caseholdrule) <br/> |Une conservation basée sur les requêtes associée à un cas eDiscovery a été modifiée. Les modifications possibles incluent la modification de la requête ou de la plage de dates pour une conservation basée sur une requête.  <br/> |
|Cas eDiscovery créé  <br/> |[New-ComplianceCase](/powershell/module/exchange/new-compliancecase) <br/> |Un cas eDiscovery a été créé. Lorsqu’un cas est créé, il vous suffit de lui donner un nom. D’autres tâches liées à la casse, telles que l’ajout de membres, la création de conservations et la création de recherches de contenu associées au cas, entraînent la journaliser des événements supplémentaires.  <br/> |
|Cas eDiscovery supprimé  <br/> |[Remove-ComplianceCase](/powershell/module/exchange/remove-compliancecase) <br/> |Un cas eDiscovery a été supprimé. Toute conservation associée au cas doit être supprimée avant que le cas puisse être supprimé.  <br/> |
|Changement de cas eDiscovery  <br/> |[Set-ComplianceCase](/powershell/module/exchange/set-compliancecase) <br/> |Un cas eDiscovery a été modifié. Les modifications incluent la fermeture d’un cas ouvert ou la réouverture d’un cas fermé.  <br/> |
|Ajout d’un membre au cas eDiscovery  <br/> |[Add-ComplianceCaseMember](/powershell/module/exchange/add-compliancecasemember) <br/> |Un utilisateur a été ajouté en tant que membre d’un cas eDiscovery. En tant que membre d’un cas, un utilisateur peut effectuer diverses tâches liées à un cas selon que les autorisations nécessaires lui ont été attribuées ou non.  <br/> |
|Membre supprimé du cas eDiscovery  <br/> |[Remove-ComplianceCaseMember](/powershell/module/exchange/remove-compliancecasemember) <br/> |Un utilisateur a été supprimé en tant que membre d’un cas eDiscovery.  <br/> |
|Modification de l’appartenance au cas eDiscovery  <br/> |[Update-ComplianceCaseMember](/powershell/module/exchange/update-compliancecasemember) <br/> |La liste d’appartenances d’un cas eDiscovery a été modifiée. Cette activité est journalisée lorsque tous les membres sont remplacés par un groupe de nouveaux utilisateurs. Si un seul membre est ajouté ou supprimé, l’opération **Add-ComplianceCaseMember** ou **Remove-ComplianceCaseMember** est journalisée.  <br/> |
|Recherche de contenu créée  <br/> |[New-ComplianceSearch](/powershell/module/exchange/new-compliancesearch) <br/> |Une nouvelle recherche de contenu a été créée.  <br/> |
|Recherche de contenu supprimé  <br/> |[Remove-ComplianceSearch](/powershell/module/exchange/remove-compliancesearch) <br/> |Une recherche de contenu existante a été supprimée.  <br/> |
|Recherche de contenu modifiée  <br/> |[Set-ComplianceSearch](/powershell/module/exchange/set-compliancesearch) <br/> |Une recherche de contenu existante a été modifiée. Les modifications peuvent inclure l’ajout ou la suppression d’emplacements de contenu qui font l’objet d’une recherche et la modification de la requête de recherche.  <br/> |
|Recherche de contenu démarrée  <br/> |[Start-ComplianceSearch](/powershell/module/exchange/start-compliancesearch) <br/> |Une recherche de contenu a été lancée. Lorsque vous créez ou modifiez une recherche de contenu à l’aide de l’interface graphique graphique du portail de conformité, la recherche est automatiquement démarrée. Si vous créez ou modifiez une recherche à l’aide de l’applet de commande **New-ComplianceSearch** ou **Set-ComplianceSearch** , vous devez exécuter l’applet **de commande Start-ComplianceSearch** pour démarrer la recherche.  <br/> |
|Recherche de contenu arrêtée  <br/> |[Stop-ComplianceSearch](/powershell/module/exchange/stop-compliancesearch) <br/> |Une recherche de contenu en cours d’exécution a été arrêtée.  <br/> |
|Action de recherche de contenu créée  <br/> |[New-ComplianceSearchAction](/powershell/module/exchange/new-compliancesearchaction) <br/> |Une action de recherche de contenu a été créée. Les actions de recherche de contenu incluent l’aperçu des résultats de recherche, l’exportation des résultats de recherche, la préparation des résultats de recherche pour analyse dans eDiscovery (Premium) et la suppression définitive des éléments qui correspondent aux critères de recherche d’une recherche de contenu.  <br/> |
|Action de recherche de contenu supprimé  <br/> |[Remove-ComplianceSearchAction](/powershell/module/exchange/remove-compliancesearchaction) <br/> |Une action de recherche de contenu a été supprimée.  <br/> |
|Filtre d’autorisations de recherche créé  <br/> |[New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter) <br/> |Un filtre d’autorisations de recherche a été créé.  <br/> |
|Filtre d’autorisations de recherche supprimées  <br/> |[Remove-ComplianceSecurityFilter](/powershell/module/exchange/remove-compliancesecurityfilter) <br/> |Un filtre d’autorisations de recherche a été supprimé.  <br/> |
|Filtre d’autorisations de recherche modifié  <br/> |[Set-ComplianceSecurityFilter](/powershell/module/exchange/set-compliancesecurityfilter) <br/> |Un filtre d’autorisations de recherche a été modifié.  <br/> |
|Administrateur eDiscovery créé  <br/> |[Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin) <br/> |Un utilisateur a été ajouté en tant qu’administrateur eDiscovery dans votre organisation.  <br/> |
|Administrateur eDiscovery supprimé  <br/> |[Remove-eDiscoveryCaseAdmin](/powershell/module/exchange/remove-ediscoverycaseadmin) <br/> |Un administrateur eDiscovery a été supprimé de votre organisation.  <br/> |
|Modification de l’appartenance de l’administrateur eDiscovery  <br/> |[Update-eDiscoveryCaseAdmin](/powershell/module/exchange/update-ediscoverycaseadmin) <br/> |La liste des administrateurs eDiscovery de votre organisation a été modifiée. Cette activité est journalisée lorsque la liste des administrateurs eDiscovery est remplacée par un groupe de nouveaux utilisateurs. Si un seul utilisateur est ajouté ou supprimé, l’opération **Add-eDiscoveryCaseAdmin** ou **Remove-eDiscoveryCaseAdmin** est journalisée.  <br/> |
|(aucun)|[Get-ComplianceCase](/powershell/module/exchange/get-compliancecase) <br/>|Cette activité est journalisée lorsqu’un utilisateur a consulté une liste de cas eDiscovery (Standard) ou eDiscovery (Premium). Cette activité est également journalisée lorsqu’un utilisateur consulte un cas spécifique dans eDiscovery (Standard). Lorsqu’un utilisateur affiche un cas spécifique, l’enregistrement d’audit inclut l’identité du cas qui a été consulté. Si l’utilisateur n’a consulté qu’une liste de cas, l’enregistrement d’audit ne contient pas d’identité de cas.|
|(aucun)|[Get-ComplianceSearch](/powershell/module/exchange/get-compliancesearch)|Cette activité est journalisée lorsqu’un utilisateur a consulté une liste de recherches de contenu ou de recherches associées à un cas eDiscovery (Standard). Cette activité est également journalisée lorsqu’un utilisateur consulte une recherche de contenu spécifique ou une recherche spécifique associée à un cas eDiscovery (Standard). Lorsqu’un utilisateur affiche une recherche spécifique, l’enregistrement d’audit inclut l’identité de la recherche qui a été consultée. Si l’utilisateur n’a consulté qu’une liste de recherches, l’enregistrement d’audit ne contient pas d’identité de recherche.
|(aucun)|[Get-ComplianceSearchAction](/powershell/module/exchange/get-compliancesearchaction)|Cette activité est journalisée lorsqu’un utilisateur a consulté une liste d’actions de recherche de conformité (telles que des exportations, des aperçus ou des purges) ou des actions associées à un cas eDiscovery (Standard). Cette activité est également journalisée lorsqu’un utilisateur affiche une action de recherche de conformité spécifique (telle qu’une exportation) ou une action spécifique associée à un cas eDiscovery (Standard). Lorsqu’un utilisateur affiche une action de recherche, l’enregistrement d’audit inclut l’identité de l’action de recherche qui a été consultée. Si l’utilisateur n’a consulté qu’une liste d’actions, l’enregistrement d’audit ne contient pas d’identité d’action.|
||||

## <a name="detailed-properties-for-ediscovery-activities"></a>Propriétés détaillées pour les activités eDiscovery

Le tableau suivant décrit les propriétés incluses dans la page de menu volant d’une activité eDiscovery répertoriées dans les résultats de la recherche. Ces propriétés sont également incluses dans le fichier CSV lorsque vous exportez les résultats de la recherche dans le journal d’audit. Un enregistrement de journal d’audit pour une activité eDiscovery n’inclut pas toutes les propriétés détaillées répertoriées ci-dessous.
  
> [!TIP]
> Lorsque vous exportez les résultats de la recherche, le fichier CSV contient une colonne nommée **AudtiData**, qui contient les propriétés détaillées décrites dans le tableau suivant dans une propriété à valeurs multiples. Vous pouvez utiliser la fonctionnalité Power Query dans Excel pour fractionner cette colonne en plusieurs colonnes afin que chaque propriété ait sa propre colonne. Cela vous permet de trier et de filtrer sur une ou plusieurs de ces propriétés. Pour plus d’informations, consultez la section « Exporter les résultats de la recherche vers un fichier » dans [Rechercher dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md#step-3-export-the-search-results-to-a-file). 
  
|**Propriété**|**Description**|
|:-----|:-----|
|Cas  <br/> |Identité (GUID) du cas eDiscovery qui a été créé, modifié ou supprimé.  <br/> |
|ClientApplication  <br/> |Les activités d’applet de commande eDiscovery ont la valeur **EMC** pour cette propriété. Cela indique que l’activité a été effectuée à l’aide de l’interface graphique graphique du portail de conformité ou en exécutant l’applet de commande dans PowerShell.  <br/> |
|ClientIP  <br/> |Adresse IP du périphérique utilisé lors de la journalisation de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.  <br/> |
|ClientRequestId  <br/> | Pour les activités eDiscovery, cette propriété est généralement vide.  <br/> |
|CmdletVersion  <br/> |Numéro de build de la version du portail de conformité en cours d’exécution dans votre organisation.  <br/> |
|CreationTime  <br/> |Date et heure en temps universel coordonné (UTC) à laquelle l’activité eDiscovery a été terminée.  <br/> |
|EffectiveOrganization  <br/> |Nom de l’organisation Microsoft 365.  <br/> |
|ExchangeLocations  <br/> |Le Exchange Online boîtes aux lettres qui sont incluses dans une recherche de contenu ou mises en attente dans un cas eDiscovery.  <br/> |
|Exclusions  <br/> |Emplacements de boîte aux lettres ou de site exclus d’une recherche de contenu ou d’une conservation dans un cas eDiscovery.  <br/> |
|ExtendedProperties  <br/> |Propriétés supplémentaires d’une recherche de contenu, d’une action de recherche de contenu ou d’une conservation dans un cas eDiscovery, telles que le GUID de l’objet et les paramètres d’applet de commande et d’applet de commande correspondants qui ont été utilisés lors de l’exécution de l’activité.  <br/> |
|ID  <br/> |ID de l’entrée de rapport. L’ID identifie de manière unique l’entrée du journal d’audit.  <br/> |
|NonPIIParameters  <br/> |Liste des paramètres (sans valeurs) qui ont été utilisés avec l’applet de commande identifiée dans la propriété Operation. Les paramètres répertoriés dans cette propriété sont les mêmes que ceux répertoriés dans la propriété Parameters.  <br/> |
|ObjectId  <br/> |GUID ou nom de l’objet (par exemple, une recherche de contenu ou un cas eDiscovery (Standard) qui a été créé, consulté, modifié ou supprimé par l’activité répertoriée dans la propriété Operation. Cet objet est également identifié dans la colonne Item dans les résultats de recherche du journal d’audit.  <br/> |
|ObjectType  <br/> |Type d’objet eDiscovery que l’utilisateur a créé, supprimé ou modifié ; par exemple, une action de recherche de contenu (aperçu, exportation ou vidage), un cas eDiscovery ou une recherche de contenu.  <br/> |
|Opération  <br/> |Nom de l’opération qui correspond à l’activité eDiscovery qui a été effectuée.  <br/> |
|OrganizationId  <br/> |GUID de votre organisation Microsoft 365.  <br/> |
|Parameters  <br/> |Nom et valeur des paramètres utilisés avec l’applet de commande correspondante.  <br/> |
|PublicFolderLocations  <br/> |Les emplacements de dossiers publics dans Exchange Online inclus dans une recherche de contenu ou mis en attente dans un cas eDiscovery.  <br/> |
|Requête  <br/> |Requête de recherche associée à l’activité, telle qu’une recherche de contenu ou une conservation basée sur une requête.  <br/> |
|RecordType  <br/> |Type d’opération indiqué par l’enregistrement. La valeur **18** indique un événement lié à une activité répertoriée dans la section [activités de l’applet de commande eDiscovery](#ediscovery-cmdlet-activities) . La valeur **24** indique un événement lié à une activité répertoriée dans la section [Comment rechercher et afficher des activités eDiscovery](#how-to-search-for-and-view-ediscovery-activities) .  <br/> |
|ResultStatus  <br/> |Indique si l’action (indiquée dans la propriété Operation) a réussi ou non.  <br/> |
|SecurityComplianceCenterEventType  <br/> |Indique que l’activité était un événement du portail de conformité. Toutes les activités eDiscovery auront la valeur **0** pour cette propriété.  <br/> |
|SharepointLocations  <br/> |Sites SharePoint Online inclus dans une recherche de contenu ou mis en attente dans un cas eDiscovery.  <br/> |
|StartTime  <br/> |Date et heure utc (Temps universel coordonné) auxquelles l’activité eDiscovery a démarré.  <br/> |
|UserId  <br/> |Utilisateur qui a effectué l’activité (spécifiée dans la propriété Operation) qui a entraîné la journaliser l’enregistrement. Les enregistrements de l’activité eDiscovery effectuée par des comptes système (tels que NT AUTHORITY\SYSTEM) sont également inclus dans le journal d’audit.  <br/> |
|UserKey  <br/> |Autre ID pour l’utilisateur identifié dans la propriété UserId. Pour les activités eDiscovery, la valeur de cette propriété est généralement identique à la propriété UserId.  <br/> |
|UserServicePlan  <br/> |Abonnement utilisé par votre organisation. Pour les activités eDiscovery, cette propriété est généralement vide.  <br/> |
|UserType  <br/> |Type d’utilisateur ayant effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur.  <br/> 0 Un utilisateur normal. 2 Un administrateur dans votre organisation. 3 Un compte de système de centre de données ou administrateur de centre de données Microsoft. 4 Un compte système. 5 Une application. 6 Un principal de service. |
|Version  <br/> |Indique le numéro de version de l’activité (identifiée par la propriété Operation) enregistrée.  <br/> |
|Charge de travail  <br/> |Service où l’activité s’est produite. Pour les activités eDiscovery, la valeur est **SecurityComplianceCenter**.  <br/> |
