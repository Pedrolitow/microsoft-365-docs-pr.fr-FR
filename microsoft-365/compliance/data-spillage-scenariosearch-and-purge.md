---
title: 'Scénario de débordement de données de la série de solutions eDiscovery : recherche et purge'
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: Utilisez eDiscovery et les outils de recherche pour gérer un incident de débordement de données dans votre organisation et y répondre.
ms.openlocfilehash: 340bf10dc57737c024d1ffcb3a441ba53bc917d6
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204125"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>Série de solutions eDiscovery : scénario de débordement de données : recherche et purge

 **Qu’est-ce que le débordement de données et pourquoi devez-vous vous en occuper ?** Le débordement de données se produit lorsqu’un document confidentiel est libéré dans un environnement non sécurisé. Lorsqu’un incident de débordement de données est détecté, il est important d’évaluer rapidement la taille et les emplacements du débordement, d’examiner les activités des utilisateurs qui l’entourent, puis de purger définitivement les données déversées du système. 
  
## <a name="data-spillage-scenario"></a>Scénario de débordement de données

Vous êtes responsable de la sécurité des informations chez Contoso. Vous êtes informé d’une situation de débordement de données dans laquelle un employé a partagé sans le savoir un document hautement confidentiel avec plusieurs personnes par courrier électronique. Vous souhaitez évaluer rapidement qui a reçu ce document en interne et en externe. Une fois identifié, vous souhaitez partager les conclusions des cas avec d’autres enquêteurs à examiner, puis supprimer définitivement les données de Office 365. Une fois l’examen terminé, vous souhaitez générer un rapport avec la preuve de la suppression définitive et d’autres détails de cas pour toute référence ultérieure.
  
### <a name="scope-of-this-article"></a>Portée de cet article

Ce document fournit une liste d’instructions sur la façon de supprimer définitivement un message d’Microsoft 365 afin qu’il ne soit ni accessible ni récupérable. Pour supprimer un message et le rendre récupérable jusqu’à l’expiration de la période de rétention des éléments supprimés, voir Rechercher et supprimer des messages électroniques [dans votre organisation.](search-for-and-delete-messages-in-your-organization.md)
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Flux de travail pour la gestion des incidents de débordement de données

Voici comment gérer un incident de débordement de données :

![Flux de travail en 8 étapes pour la gestion des incidents de débordement de données.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(Facultatif) Étape 1 : Gérer les personnes qui peuvent accéder au cas et définir des limites de conformité](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[Étape 2 : Créer un cas eDiscovery](#step-2-create-an-ediscovery-case)<br/>
[Étape 3 : Rechercher les données déversées](#step-3-search-for-the-spilled-data)<br/>
[Étape 4 : Examiner et valider les résultats des cas](#step-4-review-and-validate-case-findings)<br/>
[Étape 5 : Utiliser le journal de suivi des messages pour vérifier la façon dont les données déversées ont été partagées](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[Étape 6 : Préparer les boîtes aux lettres](#step-6-prepare-the-mailboxes)<br/>
[Étape 7 : Supprimer définitivement les données déversées](#step-7-permanently-delete-the-spilled-data)<br/>
[Étape 8 : Vérifier, fournir une preuve de suppression et audit](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Éléments à connaître avant de commencer

- Lorsqu’une boîte aux lettres est en conservation, un message supprimé reste dans le dossier Éléments récupérables jusqu’à l’expiration de la période de rétention ou la libération de la conservation. [L’étape 6](#step-6-prepare-the-mailboxes) décrit comment supprimer le hold des boîtes aux lettres. Consultez vos services juridiques ou de gestion des enregistrements avant de supprimer la archive. Votre organisation peut avoir une stratégie qui définit si une boîte aux lettres en attente ou un incident de débordement de données est prioritaire. 
    
- Pour contrôler les boîtes aux lettres utilisateur qu’un enquêteur de débordement de données peut rechercher et gérer qui peut accéder au cas, vous pouvez configurer des limites de conformité et créer un groupe de rôles personnalisé, décrit à l’étape [1.](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries) Pour ce faire, vous devez être membre du groupe de rôles Gestion de l’organisation ou avoir le rôle de gestion des rôles. Si vous ou un administrateur de votre organisation avez déjà fixé des limites de conformité, vous pouvez ignorer l’étape 1.
    
- Pour créer un cas, vous devez être membre du groupe de rôles Gestionnaire eDiscovery ou membre d’un groupe de rôles personnalisé affecté au rôle Gestion des cas. Si vous n’êtes pas membre, demandez à un administrateur Microsoft 365 de vous ajouter au groupe de rôles gestionnaire [eDiscovery.](assign-ediscovery-permissions.md)
    
- Pour créer et exécuter une recherche de contenu, vous devez être membre du groupe de rôles de gestionnaire de découverte électronique ou disposer du rôle de gestion de recherche de contenu. Pour supprimer des messages, vous devez être membre du groupe de rôles de gestion de l’organisation ou disposer du rôle de gestion de recherche et de purge. Pour plus d’informations sur l’ajout d’utilisateurs à un groupe de [rôles, voir Attribuer des autorisations eDiscovery](./assign-ediscovery-permissions.md).
    
- Pour effectuer des recherches dans les activités eDiscovery du journal d’audit à l’étape 8, l’audit doit être allumé pour votre organisation. Vous pouvez rechercher les activités effectuées au cours des 90 derniers jours. Pour en savoir plus sur la façon d’activer et d’utiliser l’audit, consultez la section [Auditer](#auditing-the-data-spillage-investigation-process) le processus d’examen de débordement de données à l’étape 8. 
    
## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(Facultatif) Étape 1 : Gérer les personnes qui peuvent accéder au cas et définir des limites de conformité

Selon votre pratique organisationnelle, vous devez contrôler qui peut accéder au cas eDiscovery utilisé pour examiner un incident de débordement de données et configurer des limites de conformité. Le moyen le plus simple de le faire consiste à ajouter des enquêteurs en tant que membres d’un groupe de rôles existant dans le Centre de conformité Microsoft 365, puis à ajouter le groupe de rôles en tant que membre du cas eDiscovery. Pour plus d’informations sur les groupes de rôles eDiscovery intégrés et sur la façon d’ajouter des membres à un cas [eDiscovery, voir Attribuer des autorisations eDiscovery](assign-ediscovery-permissions.md).
  
Vous pouvez également créer un groupe de rôles qui corresponde aux besoins de votre organisation. Par exemple, vous souhaitez peut-être qu’un groupe d’enquêteurs de débordement de données dans l’organisation accède à tous les cas de débordement de données et collabore sur ceux-là. Pour ce faire, créez un groupe de rôles « Enquêteur de débordement de données », attribuez les rôles appropriés (Exportation, Déchiffrement RMS, Révision, Aperçu, Recherche de conformité et Gestion des cas), ajoutez les enquêteurs de débordement de données au groupe de rôles, puis ajoutez le groupe de rôles en tant que membre du cas de découverte électronique de débordement de données. Pour obtenir des instructions détaillées sur la façon de faire, voir Configurer les limites de conformité pour les enquêtes [eDiscovery](set-up-compliance-boundaries.md) dans Office 365 pour obtenir des instructions détaillées sur la façon de le faire. 
  
## <a name="step-2-create-an-ediscovery-case"></a>Étape 2 : Créer un cas eDiscovery

Un cas eDiscovery permet de gérer efficacement votre enquête sur les débordements de données. Vous pouvez ajouter des membres au groupe de rôles que vous avez créé à l’étape 1, ajouter le groupe de rôles en tant que membre d’un nouveau cas eDiscovery, effectuer des recherches itératives pour rechercher les données déversées, exporter un rapport à partager, suivre l’état du cas, puis revenir aux détails du cas si nécessaire. Envisagez d’établir une convention d’attribution de noms pour les cas eDiscovery utilisés pour les incidents de débordement de données, et fournissez autant d’informations que possible dans le nom et la description du cas afin de pouvoir localiser et faire référence à l’avenir si nécessaire.
  
Pour créer un cas, vous pouvez utiliser eDiscovery dans le centre de sécurité et conformité. Voir « Créer un cas » dans [La mise en place de Core eDiscovery.](get-started-core-ediscovery.md#step-3-create-a-core-ediscovery-case)
  
## <a name="step-3-search-for-the-spilled-data"></a>Étape 3 : Rechercher les données déversées

Maintenant que vous avez créé un cas et un accès géré, vous pouvez utiliser ce cas pour rechercher de manière itérative les données qui se sont déversées et identifier les boîtes aux lettres qui contiennent les données en débordement. Vous utiliserez la même requête de recherche que celle utilisée pour rechercher les messages électroniques afin de supprimer ces mêmes messages à [l’étape 7.](#step-7-permanently-delete-the-spilled-data)
  
Pour créer une recherche de contenu associée à un cas eDiscovery, voir Rechercher du contenu dans un cas [eDiscovery principal.](search-for-content-in-core-ediscovery.md)
  
> [!IMPORTANT]
> Les mots clés que vous utilisez dans la requête de recherche peuvent contenir les données effectivement déversées que vous recherchez. Par exemple, si vous recherchez des documents contenant un numéro de sécurité sociale et que vous l’utilisez comme mot clé de recherche, vous devez supprimer la requête par la suite pour éviter tout débordement supplémentaire. Voir [Suppression de la requête de recherche à l’étape](#deleting-the-search-query) 8.
  
## <a name="step-4-review-and-validate-case-findings"></a>Étape 4 : Examiner et valider les résultats des cas

Après avoir créé une recherche de contenu, vous devez vérifier et vérifier que les résultats de la recherche sont constitués uniquement des messages électroniques qui doivent être supprimés. Dans une recherche de contenu, vous pouvez prévisualiser un échantillonnage aléatoire de 1 000 messages électroniques sans exporter les résultats de la recherche afin d’éviter toute débordement de données supplémentaire. Vous pouvez en savoir plus sur les limitations de prévisualisation aux [limites de recherche de contenu.](limits-for-content-search.md)
  
Si vous avez plus de 1 000 boîtes aux lettres ou plus de 100 messages électroniques par boîte aux lettres à réviser, vous pouvez diviser la recherche initiale en plusieurs recherches à l’aide de mots clés ou de conditions supplémentaires, telles que la plage de dates ou l’expéditeur/destinataire, et examiner les résultats de chaque recherche individuellement. Veillez à noter toutes les requêtes de recherche à utiliser lorsque vous supprimez des messages à [l’étape 7.](#step-7-permanently-delete-the-spilled-data)

Si un dépositaire ou un utilisateur final se voit attribuer une licence Office 365 E5, vous pouvez examiner jusqu’à 10 000 résultats de recherche à la fois à l’aide de Advanced eDiscovery. S’il y a plus de 10 000 messages électroniques à réviser, vous pouvez diviser la requête de recherche par plage de dates et examiner chaque résultat individuellement à mesure que les résultats de la recherche sont triés par date. Dans Advanced eDiscovery, vous pouvez baliser  les résultats de recherche à l’aide de l’étiquette en tant que fonctionnalité dans le panneau d’aperçu et filtrer le résultat de la recherche en fonction de la balise que vous avez étiquetée. Cela est utile lorsque vous collaborez avec un réviseur secondaire. À l’aide d’outils d’analyse supplémentaires dans Advanced eDiscovery, tels que la reconnaissance optique de caractères, le thread de messagerie électronique et le codage prédictif, vous pouvez rapidement traiter et examiner des milliers de messages et les marquer pour une révision plus approfondi. Voir [configuration rapide pour Advanced eDiscovery](./get-started-with-advanced-ediscovery.md).

Lorsque vous trouvez un message électronique contenant des données surdessées, vérifiez les destinataires du message pour déterminer s’il a été partagé en externe. Pour poursuivre le suivi d’un message, vous pouvez collecter des informations sur l’expéditeur et des plages de dates afin de pouvoir utiliser les journaux de suivi des messages. Ce processus est décrit à [l’étape 5.](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)

Après avoir vérifié les résultats de la recherche, vous pouvez partager vos résultats avec d’autres personnes pour un examen secondaire. Les personnes que vous avez affectées au cas à l’étape 1 peuvent examiner le contenu du cas à la fois dans eDiscovery et Advanced eDiscovery et approuver les résultats de cas. Vous pouvez également générer un rapport sans exporter le contenu réel. Vous pouvez également utiliser ce même rapport comme preuve de suppression, qui est décrit à [l’étape 8](#step-8-verify-provide-a-proof-of-deletion-and-audit).
  
 **Pour générer un rapport statistique :**
  
1. Go to the **Search** page in the eDiscovery case, and click the search that you want to generate a report for. 
    
2. Dans la page volante, cliquez sur **Plus > exporter le rapport.**
 
      La page Exporter le rapport s’affiche.

    ![Sélectionnez la recherche, puis cliquez sur Plus > exporter le rapport sur la page volante.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. Sélectionnez tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour **d’autres raisons,** puis cliquez sur Générer **un rapport.**

4. Dans le cas eDiscovery, cliquez sur **Exporter** pour afficher la liste des travaux d’exportation. Vous de devez peut-être cliquer sur **Actualiser** pour mettre à jour la liste afin d’afficher la tâche d’exportation que vous avez créée.

5. Cliquez sur la tâche d’exportation, puis cliquez sur **Télécharger** le rapport dans la page volante.
 
    ![Dans la page Exportation, cliquez sur l’exportation, puis sur « Télécharger le rapport ».](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

Le **rapport de synthèse d’exportation** contient le nombre d’emplacements trouvés avec les résultats et la taille des résultats de la recherche. Vous pouvez l’utiliser pour comparer le rapport généré après la suppression et fournir comme preuve de suppression. Le **rapport** des résultats contient un résumé plus détaillé des résultats de la recherche, y compris l’objet, l’expéditeur, les destinataires, si le message a été lu, les dates et la taille de chaque message. Si l’un des détails de ce rapport contient ces données effectivement déversées, n’oubliez pas de supprimer définitivement le fichier Results.csv une fois l’enquête terminée.

Pour plus d’informations sur l’exportation de rapports, voir [Exporter un rapport de recherche de contenu.](export-a-content-search-report.md)
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>Étape 5 : Utiliser le journal de suivi des messages pour vérifier la façon dont les données déversées ont été partagées

Pour rechercher plus en détail si le courrier électronique avec des données étendues a été partagé, vous pouvez éventuellement interroger les journaux de suivi des messages avec les informations de l’expéditeur et les informations de plage de dates que vous avez rassemblées à l’étape 4. La période de rétention pour le suivi des messages est de 30 jours pour les données en temps réel et de 90 jours pour les données historiques.
  
Vous pouvez utiliser le suivi des messages dans le centre de sécurité et conformité ou utiliser les cmdlets correspondantes dans Exchange Online PowerShell. Il est important de noter que le suivi des messages n’offre pas de garanties complètes sur l’intégralité des données renvoyées. Pour plus d’informations sur l’utilisation du suivi des messages, voir : 
  
- [Suivi des messages dans le centre de conformité et de sécurité](../security/office-365-security/message-trace-scc.md)
    
- [Nouveau suivi des messages dans le Centre de conformité & sécurité](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>Étape 6 : Préparer les boîtes aux lettres

Une fois que vous avez passé en revue et validé que les résultats de la recherche contiennent uniquement les messages qui doivent être supprimés, vous devez collecter une liste des adresses e-mail des boîtes aux lettres impactées à utiliser à l’étape 7 lorsque vous supprimez les données surdessées. Vous de devez également préparer les boîtes aux lettres avant de pouvoir supprimer définitivement les messages électroniques selon que la récupération d’élément unique est activée sur les boîtes aux lettres qui contiennent les données surdessées ou si l’une de ces boîtes aux lettres est en attente.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Obtenir une liste d’adresses de boîtes aux lettres avec des données surdessées

Il existe deux façons de collecter une liste d’adresses de messagerie de boîtes aux lettres avec des données surdessées.

**Option 1 : Obtenir une liste d’adresses de boîtes aux lettres avec des données surdessées**

1. Ouvrez le cas eDiscovery, allez sur la page **De** recherche et sélectionnez la recherche de contenu appropriée. 
    
2. Dans la page volante, cliquez sur **Afficher les résultats.**
    
3. Dans la liste déroulante **Résultats individuels**, cliquez sur **Statistiques de recherche**.
    
4. Dans la **liste bas Type,** cliquez sur **Emplacements supérieurs.**
    
    ![Obtenir la liste des boîtes aux lettres qui contiennent des résultats de recherche dans la page Emplacements principaux dans les statistiques de recherche.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Une liste de boîtes aux lettres contenant des résultats de recherche s’affiche. Le nombre d’éléments de chaque boîte aux lettres qui correspondent à la requête de recherche est également affiché.
    
5. Copiez les informations de la liste et enregistrez-les dans un fichier ou cliquez sur **Télécharger** pour les télécharger dans un fichier CSV. 
    
**Option 2 : obtenir des emplacements de boîtes aux lettres à partir du rapport d’exportation**

Ouvrez le rapport de synthèse d’exportation que vous avez téléchargé à [l’étape 4.](#step-4-review-and-validate-case-findings) Dans la première colonne du rapport, l’adresse de messagerie de chaque boîte aux lettres est répertoriée sous **Emplacements**.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Préparer les boîtes aux lettres afin de pouvoir supprimer les données déversées

Si la récupération d’élément unique est activée ou si une boîte aux lettres est placée en attente, un message supprimé définitivement (purgé) est conservé dans le dossier Éléments récupérables. Ainsi, avant de pouvoir purger les données déversées, vous devez vérifier les configurations de boîte aux lettres existantes, désactiver la récupération d’élément unique et supprimer toute conservation ou stratégie de rétention. N’oubliez pas que vous pouvez préparer une boîte aux lettres à la fois, puis exécuter la même commande sur différentes boîtes aux lettres ou créer un script PowerShell pour préparer plusieurs boîtes aux lettres en même temps.

- Pour obtenir des instructions sur la façon de vérifier si la récupération d’élément unique est activée ou si la boîte aux lettres est placée en conservation ou si une stratégie de rétention est affectée à une stratégie de rétention, voir « Étape 1 : Collecter des informations sur la boîte aux lettres » dans Supprimer les éléments du dossier Éléments [récupérables](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) des boîtes aux lettres en nuage. 

- Voir « Étape 2 : Préparer la boîte aux lettres » dans Supprimer des éléments du dossier Éléments [récupérables](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) des boîtes aux lettres en nuage en attente pour obtenir des instructions sur la désactivation de la récupération d’élément unique. 

- Voir « Étape 3 : Supprimer toutes les conservations de la boîte aux lettres » dans Supprimer les éléments du dossier Éléments [récupérables](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) des boîtes aux lettres en nuage en attente pour obtenir des instructions sur la suppression d’une conservation ou d’une stratégie de rétention d’une boîte aux lettres. 

- Voir « Étape 4 : Supprimer le délai d’attente de la boîte aux lettres » dans Supprimer les éléments du dossier Éléments [récupérables](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) des boîtes aux lettres en nuage en attente pour obtenir des instructions sur la suppression du délai d’attente qui est placé sur la boîte aux lettres après la suppression de tout type de mise en attente.

> [!IMPORTANT]
> Consultez vos services juridiques ou de gestion des enregistrements avant de supprimer une stratégie de conservation ou de rétention. Votre organisation peut avoir une stratégie qui définit si une boîte aux lettres en attente ou un incident de débordement de données est prioritaire. 
  
Veillez à revenir aux configurations précédentes de la boîte aux lettres après avoir vérifié que les données supprimées ont été définitivement supprimées. Consultez les détails de [l’étape 7.](#step-7-permanently-delete-the-spilled-data)

## <a name="step-7-permanently-delete-the-spilled-data"></a>Étape 7 : Supprimer définitivement les données déversées

À l’aide des emplacements de boîtes aux lettres que vous avez collectés et préparés à l’étape 6 et de la requête de recherche qui a été créée et affinée à l’étape 3 pour rechercher les messages électroniques qui contiennent les données déversées, vous pouvez désormais supprimer définitivement les données qui se sont déversées.  Comme indiqué précédemment, pour supprimer des messages, vous devez être membre du groupe de rôles Gestion de l’organisation ou avoir le rôle de gestion Recherche et purge. Pour plus d’informations sur l’ajout d’utilisateurs à un groupe de [rôles, voir Attribuer des autorisations eDiscovery](./assign-ediscovery-permissions.md).

Pour supprimer les messages déversés, voir [Rechercher et supprimer des messages électroniques.](search-for-and-delete-messages-in-your-organization.md)

Gardez les limites suivantes à l’esprit lors de la suppression des données déversées :

- Le nombre maximal de boîtes aux lettres dans une recherche que vous pouvez utiliser pour supprimer des éléments en faisant une action de recherche et de purge est de 50 000. Si la recherche que vous créez à l’étape 3 recherche plus de 50 000 boîtes aux lettres, l’action de purge échouera. Une recherche de plus de 50 000 boîtes aux lettres au cours d’une même recherche est probable, généralement lorsque la configuration de la recherche prend en compte toutes les boîtes aux lettres de votre organisation. Cette restriction s’applique même si moins de 50 000 boîtes aux lettres contiennent des éléments qui correspondent à la requête de recherche.

- Un maximum de 10 éléments par boîte aux lettres peuvent être supprimés à la fois. Sachant que la fonction de recherche et suppression de messages est censée être un outil de réponse aux incidents, cette limite permet de s’assurer que les messages sont rapidement supprimés des boîtes aux lettres. Cette fonctionnalité n’est pas conçue pour nettoyer les boîtes aux lettres des utilisateurs.

> [!IMPORTANT]
> Il n’est pas possible de supprimer les éléments de courrier d’un groupe de révision dans un cas Advanced eDiscovery à l’aide des procédures décrites dans cet article. Cela est dû au fait que les éléments d’un jeu à réviser sont des copies d’éléments du service en direct qui sont copiés et stockés dans un stockage Azure de données. Cela signifie qu’elles ne seront pas renvoyées par une recherche de contenu que vous créez à l’étape 3. Pour supprimer des éléments d’un groupe de révision, vous devez supprimer le cas Advanced eDiscovery qui contient l’entité de révision. Pour plus d’informations, consultez [Fermer ou supprimer un cas Advanced eDiscovery](close-or-delete-case.md).
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>Étape 8 : Vérifier, fournir une preuve de suppression et audit

L’étape finale du flux de travail pour gérer un incident de débordement de données consiste à vérifier que les données déverrouées ont été définitivement supprimées de la boîte aux lettres en allant dans le cas eDiscovery et en réaxant la même requête de recherche qui a été utilisée pour supprimer ces données afin de confirmer qu’aucun résultat n’est renvoyé. Une fois que vous avez confirmé que les données supprimées ont été définitivement supprimées, vous pouvez exporter un rapport et l’inclure (avec le rapport d’origine) comme preuve de suppression. Vous pouvez [ensuite fermer le cas](close-reopen-delete-core-ediscovery-cases.md) qui vous permettra de le rouvrir si vous devez y faire référence à l’avenir. En outre, vous pouvez également revenir à l’état précédent des boîtes aux lettres, supprimer la requête de recherche utilisée pour rechercher les données déversées et rechercher des enregistrements d’audit des tâches effectuées lors de la gestion de l’incident de débordement de données.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Reconnextage des boîtes aux lettres à leur état précédent

Si vous avez modifié une configuration de boîte aux lettres à l’étape 6 pour préparer les boîtes aux lettres avant la suppression des données supprimées, vous devez les revenir à leur état précédent. Voir « Étape 6 : Rétablir l’état précédent de la boîte aux lettres » dans Supprimer des éléments du dossier Éléments [récupérables](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state)des boîtes aux lettres en nuage en attente.
  
### <a name="deleting-the-search-query"></a>Suppression de la requête de recherche

Si les mots clés de la requête de recherche que vous avez créée et utilisée à l’étape 3 contiennent une partie de toutes les données effectivement déversées, vous devez supprimer la requête de recherche afin d’éviter tout débordement de données.
  
1. Dans le centre de sécurité et conformité, ouvrez le cas eDiscovery, allez sur la **page** De recherche et sélectionnez la recherche de contenu appropriée.

2. Dans la page volante, cliquez sur **Supprimer.**

    ![Sélectionnez la recherche, puis cliquez sur Supprimer dans la page volante.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Audit du processus d’examen de débordement de données

Vous pouvez rechercher dans le journal d’audit les activités eDiscovery effectuées au cours de l’examen. Vous pouvez également effectuer une recherche dans le journal d’audit pour renvoyer les enregistrements d’audit de la commande **New-ComplianceSearchAction -Purge** que vous avez mise en place à l’étape 7 pour supprimer les données surdessinées. Pour plus d’informations, consultez :

- [Rechercher le journal d’audit](search-the-audit-log-in-security-and-compliance.md)

- [Rechercher des activités eDiscovery dans le journal d’audit](search-for-ediscovery-activities-in-the-audit-log.md)
