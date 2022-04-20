---
title: Scénario de débordement de données de la série de solutions eDiscovery - Recherche et vidage
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MET150
ms.assetid: d945f7dd-f62f-4ca7-b3e7-469824cfd493
description: Utilisez eDiscovery et les outils de recherche pour gérer et répondre à un incident de débordement de données dans votre organisation.
ms.openlocfilehash: e9e81ae81c344bfc8773174c8650a1808faddd5e
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64948064"
---
# <a name="ediscovery-solution-series-data-spillage-scenario---search-and-purge"></a>Série de solutions eDiscovery : scénario de débordement de données - Recherche et vidage

 **Qu’est-ce que le déversement de données et pourquoi devriez-vous vous en soucier ?** Le déversement de données se fait lorsqu’un document confidentiel est libéré dans un environnement non approuvé. Lorsqu’un incident de débordement de données est détecté, il est important d’évaluer rapidement la taille et l’emplacement du déversement, d’examiner les activités des utilisateurs autour de celui-ci, puis de vider définitivement les données qui ont été renversées du système.
  
## <a name="data-spillage-scenario"></a>Scénario de débordement de données

Vous êtes responsable de la sécurité des informations chez Contoso. Vous êtes informé d’une situation de débordement de données où un employé partageait sans le savoir un document hautement confidentiel avec plusieurs personnes par e-mail. Vous souhaitez évaluer rapidement qui a reçu ce document en interne et en externe. Une fois identifié, vous souhaitez partager les conclusions de cas avec d’autres enquêteurs pour les examiner, puis supprimer définitivement les données de Office 365. Une fois l’enquête terminée, vous souhaitez générer un rapport contenant la preuve d’un renvoi permanent et d’autres détails de cas pour toute référence ultérieure.
  
### <a name="scope-of-this-article"></a>Étendue de cet article

Ce document fournit une liste d’instructions sur la façon de supprimer définitivement un message de Microsoft 365 afin qu’il ne soit pas accessible ou récupérable. Pour supprimer un message et le rendre récupérable jusqu’à l’expiration de la période de rétention des éléments supprimés, consultez [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).
  
## <a name="workflow-for-managing-data-spillage-incidents"></a>Flux de travail pour la gestion des incidents de débordement de données

Voici comment gérer un incident de débordement de données :

![Flux de travail en 8 étapes pour la gestion des incidents de débordement de données.](../media/O365-eDiscoverySolutions-DataSpillage-workflow.png)
  
[(Facultatif) Étape 1 : Gérer les personnes autorisées à accéder au cas et définir les limites de conformité](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries)<br/>
[Étape 2 : Créer un cas eDiscovery](#step-2-create-an-ediscovery-case)<br/>
[Étape 3 : Rechercher les données renversées](#step-3-search-for-the-spilled-data)<br/>
[Étape 4 : Examiner et valider les conclusions de cas](#step-4-review-and-validate-case-findings)<br/>
[Étape 5 : Utiliser le journal de suivi des messages pour vérifier comment les données renversées ont été partagées](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared)<br/>
[Étape 6 : Préparer les boîtes aux lettres](#step-6-prepare-the-mailboxes)<br/>
[Étape 7 : Supprimer définitivement les données renversées](#step-7-permanently-delete-the-spilled-data)<br/>
[Étape 8 : Vérifier, fournir une preuve de suppression et auditer](#step-8-verify-provide-a-proof-of-deletion-and-audit)<br/>

## <a name="things-to-know-before-you-start"></a>Choses à savoir avant de commencer

- Le flux de travail de débordement de données décrit dans cet article ne supprime pas les messages de conversation dans Microsoft Teams. Pour rechercher et supprimer Teams messages de conversation, consultez [Rechercher et vider les messages de conversation dans Teams](search-and-delete-Teams-chat-messages.md).

- Lorsqu’une boîte aux lettres est en attente, un message supprimé reste dans le dossier Éléments récupérables jusqu’à ce que la période de rétention expire ou que la conservation soit libérée. [L’étape 6](#step-6-prepare-the-mailboxes) décrit comment supprimer la conservation des boîtes aux lettres. Vérifiez auprès de vos services juridiques ou de gestion des enregistrements avant de supprimer la conservation. Votre organisation peut avoir une stratégie qui définit si une boîte aux lettres en attente ou un incident de débordement de données est prioritaire. 

- Pour contrôler les boîtes aux lettres utilisateur qu’un enquêteur de débordement de données peut rechercher et gérer qui peut accéder au cas, vous pouvez configurer des limites de conformité et créer un groupe de rôles personnalisé, décrit à [l’étape 1](#optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries). Pour ce faire, vous devez être membre du groupe de rôles Gestion de l’organisation ou être affecté au rôle de gestion des rôles. Si vous ou un administrateur de votre organisation avez déjà défini des limites de conformité, vous pouvez ignorer l’étape 1.

- Pour créer un cas, vous devez être membre du groupe de rôles gestionnaire eDiscovery ou être membre d’un groupe de rôles personnalisé auquel le rôle Gestion des cas est attribué. Si vous n’êtes pas membre, demandez à un administrateur Microsoft 365 de [vous ajouter au groupe de rôles du gestionnaire eDiscovery](assign-ediscovery-permissions.md).

- Pour créer et exécuter une recherche de contenu, vous devez être membre du groupe de rôles de gestionnaire de découverte électronique ou disposer du rôle de gestion de recherche de contenu. Pour supprimer des messages, vous devez être membre du groupe de rôles de gestion de l’organisation ou disposer du rôle de gestion de recherche et de purge. Pour plus d’informations sur l’ajout d’utilisateurs à un groupe de [rôles, consultez Affecter des autorisations eDiscovery](./assign-ediscovery-permissions.md).

- Pour effectuer une recherche dans les activités eDiscovery du journal d’audit à l’étape 8, l’audit doit être activé pour votre organisation. Vous pouvez rechercher les activités qui ont été effectuées au cours des 90 derniers jours. Pour en savoir plus sur l’activation et l’utilisation de l’audit, consultez la section [Auditer le processus d’examen des déversements de données](#auditing-the-data-spillage-investigation-process) à l’étape 8.

## <a name="optional-step-1-manage-who-can-access-the-case-and-set-compliance-boundaries"></a>(Facultatif) Étape 1 : Gérer les personnes autorisées à accéder au cas et définir les limites de conformité

Selon la pratique de votre organisation, vous devez contrôler qui peut accéder au cas eDiscovery utilisé pour examiner un incident de débordement de données et configurer les limites de conformité. Pour ce faire, le moyen le plus simple consiste à ajouter des enquêteurs en tant que membres d’un groupe de rôles existant dans le portail de conformité Microsoft Purview, puis à ajouter le groupe de rôles en tant que membre du cas eDiscovery. Pour plus d’informations sur les groupes de rôles eDiscovery intégrés et sur la façon d’ajouter des membres à un cas eDiscovery, consultez [Affecter des autorisations eDiscovery](assign-ediscovery-permissions.md).
  
Vous pouvez également créer un groupe de rôles qui s’aligne sur les besoins de votre organisation. Par exemple, vous souhaiterez peut-être qu’un groupe d’enquêteurs en cas de déversement de données dans l’organisation accède à tous les cas de débordement de données et collabore sur celui-ci. Pour ce faire, vous pouvez créer un groupe de rôles « Data Spillage Investigator », attribuer les rôles appropriés (Exporter, Déchiffrer RMS, Examiner, Aperçu, Recherche de conformité et Gestion des cas), ajouter les enquêteurs de débordement de données au groupe de rôles, puis ajouter le groupe de rôles en tant que membre du cas eDiscovery de débordement de données. Pour obtenir des instructions détaillées sur la procédure à suivre[, consultez Configurer les limites de conformité pour les enquêtes eDiscovery dans Office 365](set-up-compliance-boundaries.md). 
  
## <a name="step-2-create-an-ediscovery-case"></a>Étape 2 : Créer un cas eDiscovery

Un cas eDiscovery fournit un moyen efficace de gérer votre enquête sur les débordements de données. Vous pouvez ajouter des membres au groupe de rôles que vous avez créé à l’étape 1, ajouter le groupe de rôles en tant que membre d’un nouveau cas eDiscovery, effectuer des recherches itératives pour rechercher les données renversées, exporter un rapport à partager, suivre l’état du cas, puis renvoyer aux détails du cas si nécessaire. Envisagez d’établir une convention d’affectation de noms pour les cas de découverte électronique utilisés pour les incidents de débordement de données, et fournissez autant d’informations que possible dans le nom et la description du cas afin de pouvoir rechercher et faire référence à l’avenir si nécessaire.
  
Pour créer un cas, vous pouvez utiliser eDiscovery dans le Centre de sécurité et de conformité. Voir « Créer un cas » dans [Démarrage avec eDiscovery (Standard).](get-started-core-ediscovery.md#step-3-create-a-ediscovery-standard-case)
  
## <a name="step-3-search-for-the-spilled-data"></a>Étape 3 : Rechercher les données renversées

Maintenant que vous avez créé un cas et un accès managé, vous pouvez utiliser le cas pour effectuer une recherche itérative pour rechercher les données renversées et identifier les boîtes aux lettres qui contiennent les données renversées. Vous utiliserez la même requête de recherche que celle que vous avez utilisée pour rechercher les messages électroniques pour supprimer ces mêmes messages à [l’étape 7](#step-7-permanently-delete-the-spilled-data).
  
Pour créer une recherche de contenu associée à un cas eDiscovery, consultez [Rechercher du contenu dans un cas eDiscovery (Standard).](search-for-content-in-core-ediscovery.md)
  
> [!IMPORTANT]
> Les mots clés que vous utilisez dans la requête de recherche peuvent contenir les données réellement propagées que vous recherchez. Par exemple, si vous recherchez des documents contenant un numéro de sécurité sociale et que vous l’utilisez comme mot clé de recherche, vous devez supprimer la requête par la suite pour éviter tout débordement supplémentaire. Voir [Suppression de la requête de recherche à l’étape](#deleting-the-search-query) 8.
  
## <a name="step-4-review-and-validate-case-findings"></a>Étape 4 : Examiner et valider les conclusions de cas

Après avoir créé une recherche de contenu, vous devez vérifier et vérifier que les résultats de la recherche sont constitués uniquement des messages électroniques qui doivent être supprimés. Dans une recherche de contenu, vous pouvez afficher un aperçu d’un échantillonnage aléatoire de 1 000 messages électroniques sans exporter les résultats de la recherche pour éviter tout autre débordement de données. Vous pouvez en savoir plus sur les limitations de la préversion aux [limites de la recherche de contenu](limits-for-content-search.md).
  
Si vous avez plus de 1 000 boîtes aux lettres ou plus de 100 messages électroniques par boîte aux lettres à examiner, vous pouvez diviser la recherche initiale en plusieurs recherches à l’aide de mots clés ou de conditions supplémentaires, tels que la plage de dates ou l’expéditeur/destinataire, et examiner les résultats de chaque recherche individuellement. Veillez à noter toutes les requêtes de recherche à utiliser lorsque vous supprimez des messages à [l’étape 7](#step-7-permanently-delete-the-spilled-data).

Lorsque vous trouvez un e-mail contenant des données renversées, vérifiez les destinataires du message pour déterminer s’il a été partagé en externe. Pour poursuivre le suivi d’un message, vous pouvez collecter les informations de l’expéditeur et les plages de dates afin de pouvoir utiliser les journaux de suivi des messages. Ce processus est décrit à [l’étape 5](#step-5-use-message-trace-log-to-check-how-spilled-data-was-shared).

Après avoir vérifié les résultats de la recherche, vous souhaiterez peut-être partager vos résultats avec d’autres personnes pour une révision secondaire. Les personnes que vous avez affectées au cas à l’étape 1 peuvent examiner le contenu du cas dans eDiscovery et Microsoft Purview eDiscovery (Premium) et approuver les conclusions de cas. Vous pouvez également générer un rapport sans exporter le contenu réel. Vous pouvez également utiliser ce même rapport comme preuve de suppression, ce qui est décrit à [l’étape 8](#step-8-verify-provide-a-proof-of-deletion-and-audit).
  
 **Pour générer un rapport statistique :**
  
1. Accédez à la page **Recherche** dans le cas eDiscovery, puis cliquez sur la recherche pour laquelle vous souhaitez générer un rapport. 
    
2. Dans la page de menu volant, cliquez sur **Plus > Rapport d’exportation**.
 
      La page Exporter le rapport s’affiche.

    ![Sélectionnez la recherche, puis cliquez sur Plus > Exporter le rapport dans la page de menu volant.](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport1.png)
    
3. Sélectionnez **Tous les éléments, y compris ceux dont le format n’est pas reconnu, sont chiffrés ou n’ont pas été indexés pour d’autres raisons,** puis cliquez sur **Générer un rapport**.

4. Dans le cas eDiscovery, cliquez sur **Exporter** pour afficher la liste des travaux d’exportation. Vous devrez peut-être cliquer sur **Actualiser** pour mettre à jour la liste afin d’afficher le travail d’exportation que vous avez créé.

5. Cliquez sur le travail d’exportation, puis sur **Télécharger** le rapport dans la page de menu volant.
 
    ![Dans la page Exporter, cliquez sur l’exportation, puis sur « Télécharger le rapport ».](../media/O365-eDiscoverySolutions-DataSpillage-ExportReport2.png)

Le rapport **Résumé de l’exportation** contient le nombre d’emplacements trouvés avec les résultats et la taille des résultats de recherche. Vous pouvez l’utiliser pour comparer avec le rapport généré après la suppression et fournir une preuve de suppression. Le rapport **résultats** contient un résumé plus détaillé des résultats de la recherche, y compris l’objet, l’expéditeur, les destinataires, si l’e-mail a été lu, les dates et la taille de chaque message. Si l’un des détails de ce rapport contient ces données réellement renversées, veillez à supprimer définitivement le fichier Results.csv une fois l’enquête terminée.

Pour plus d’informations sur l’exportation de rapports, consultez [Exporter un rapport de recherche de contenu](export-a-content-search-report.md).
    
## <a name="step-5-use-message-trace-log-to-check-how-spilled-data-was-shared"></a>Étape 5 : Utiliser le journal de suivi des messages pour vérifier comment les données renversées ont été partagées

Pour examiner plus en détail si des e-mails contenant des données ont été partagées, vous pouvez éventuellement interroger les journaux de suivi des messages avec les informations de l’expéditeur et les informations de plage de dates que vous avez collectées à l’étape 4. La période de rétention pour la trace des messages est de 30 jours pour les données en temps réel et de 90 jours pour les données d’historique.
  
Vous pouvez utiliser la trace des messages dans le centre de sécurité et de conformité ou utiliser les applets de commande correspondantes dans Exchange Online PowerShell. Il est important de noter que le suivi des messages n’offre pas de garanties complètes sur l’exhaustivité des données retournées. Pour plus d’informations sur l’utilisation de la trace des messages, consultez : 
  
- [Suivi des messages dans le centre de conformité et de sécurité](../security/office-365-security/message-trace-scc.md)
    
- [Nouvelle trace de message dans le Centre de sécurité & conformité](https://techcommunity.microsoft.com/t5/exchange-team-blog/new-message-trace-in-office-365-security-038-compliance-center/ba-p/607893)
    
## <a name="step-6-prepare-the-mailboxes"></a>Étape 6 : Préparer les boîtes aux lettres

Une fois que vous avez vérifié et vérifié que les résultats de la recherche contiennent uniquement les messages qui doivent être supprimés, vous devez collecter une liste des adresses e-mail des boîtes aux lettres concernées à utiliser à l’étape 7 lorsque vous supprimez les données renversées. Vous devrez peut-être également préparer les boîtes aux lettres avant de pouvoir supprimer définitivement les messages électroniques selon que la récupération d’élément unique est activée sur les boîtes aux lettres contenant les données renversées ou si l’une de ces boîtes aux lettres est en attente.
  
### <a name="get-a-list-of-addresses-of-mailboxes-with-spilled-data"></a>Obtenir la liste des adresses des boîtes aux lettres avec des données renversées

Il existe deux façons de collecter une liste d’adresses e-mail de boîtes aux lettres avec des données renversées.

**Option 1 : Obtenir une liste d’adresses de boîtes aux lettres avec des données renversées**

1. Ouvrez le cas eDiscovery, accédez à la page **De recherche** et sélectionnez la recherche de contenu appropriée. 
    
2. Dans la page de menu volant, cliquez sur **Afficher les résultats**.
    
3. Dans la liste déroulante **Résultats individuels**, cliquez sur **Statistiques de recherche**.
    
4. Dans la liste déroulante **Type** , cliquez sur **Emplacements supérieurs**.
    
    ![Obtenez la liste des boîtes aux lettres qui contiennent les résultats de la recherche dans la page Emplacements supérieurs dans les statistiques de recherche.](../media/O365-eDiscoverySolutions-DataSpillage-TopLocations.png)

    Une liste de boîtes aux lettres contenant des résultats de recherche s’affiche. Le nombre d’éléments dans chaque boîte aux lettres qui correspondent à la requête de recherche s’affiche également.
    
5. Copiez les informations de la liste et enregistrez-les dans un fichier ou cliquez sur **Télécharger** pour télécharger les informations dans un fichier CSV. 
    
**Option 2 : Obtenir les emplacements de boîte aux lettres à partir du rapport d’exportation**

Ouvrez le rapport Résumé de l’exportation que vous avez téléchargé à [l’étape 4](#step-4-review-and-validate-case-findings). Dans la première colonne du rapport, l’adresse e-mail de chaque boîte aux lettres est répertoriée sous **Emplacements**.
  
### <a name="prepare-the-mailboxes-so-you-can-delete-the-spilled-data"></a>Préparer les boîtes aux lettres afin de pouvoir supprimer les données renversées

Si la récupération d’élément unique est activée ou si une boîte aux lettres est mise en attente, un message supprimé définitivement (purgé) est conservé dans le dossier Éléments récupérables. Ainsi, avant de pouvoir vider les données renversées, vous devez vérifier les configurations de boîte aux lettres existantes et désactiver la récupération d’élément unique et supprimer toute stratégie de conservation ou de rétention. Gardez à l’esprit que vous pouvez préparer une boîte aux lettres à la fois, puis exécuter la même commande sur différentes boîtes aux lettres ou créer un script PowerShell pour préparer plusieurs boîtes aux lettres en même temps.

- Consultez « Étape 1 : Collecter des informations sur la boîte aux lettres » dans [Supprimer les éléments du dossier Éléments récupérables des boîtes aux lettres cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-1-collect-information-about-the-mailbox) pour obtenir des instructions sur la façon de vérifier si la récupération d’élément unique est activée ou si la boîte aux lettres est mise en attente ou si elle est affectée à une stratégie de rétention. 

- Consultez « Étape 2 : Préparer la boîte aux lettres » dans [Supprimer les éléments du dossier Éléments récupérables des boîtes aux lettres cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-2-prepare-the-mailbox) pour obtenir des instructions sur la désactivation de la récupération d’élément unique. 

- Consultez « Étape 3 : Supprimer toutes les conservations de la boîte aux lettres » dans [Supprimer les éléments du dossier Éléments récupérables des boîtes aux lettres cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-3-remove-all-holds-from-the-mailbox) pour obtenir des instructions sur la suppression d’une stratégie de conservation ou de rétention d’une boîte aux lettres. 

- Consultez « Étape 4 : Supprimer la conservation différée de la boîte aux lettres » dans [Supprimer les éléments du dossier Éléments récupérables des boîtes aux lettres cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-4-remove-the-delay-hold-from-the-mailbox) pour obtenir des instructions sur la suppression de la conservation différée qui est placée sur la boîte aux lettres après la suppression de tout type de conservation.

> [!IMPORTANT]
> Vérifiez auprès de vos services juridiques ou de gestion des enregistrements avant de supprimer une stratégie de conservation ou de rétention. Votre organisation peut avoir une stratégie qui définit si une boîte aux lettres en attente ou un incident de débordement de données est prioritaire. 
  
Veillez à rétablir la boîte aux lettres aux configurations précédentes après avoir vérifié que les données renversées ont été supprimées définitivement. Consultez les détails de [l’étape 7](#step-7-permanently-delete-the-spilled-data).

## <a name="step-7-permanently-delete-the-spilled-data"></a>Étape 7 : Supprimer définitivement les données renversées

À l’aide des emplacements de boîte aux lettres que vous avez collectés et préparés à l’étape 6 et de la requête de recherche qui a été créée et affinée à l’étape 3 pour rechercher les messages électroniques contenant les données renversées, vous pouvez désormais supprimer définitivement les données renversées.  Comme expliqué précédemment, pour supprimer des messages, vous devez être membre du groupe de rôles Gestion de l’organisation ou être affecté au rôle de gestion de recherche et de vidage. Pour plus d’informations sur l’ajout d’utilisateurs à un groupe de [rôles, consultez Affecter des autorisations eDiscovery](./assign-ediscovery-permissions.md).

Pour supprimer les messages renversés, consultez [Rechercher et supprimer les messages électroniques](search-for-and-delete-messages-in-your-organization.md).

Gardez à l’esprit les limites suivantes lors de la suppression des données renversées :

- Le nombre maximal de boîtes aux lettres dans une recherche que vous pouvez utiliser pour supprimer des éléments en effectuant une action de recherche et de vidage est de 50 000. Si la recherche que vous créez à l’étape 3 recherche plus de 50 000 boîtes aux lettres, l’action de vidage échoue. Une recherche de plus de 50 000 boîtes aux lettres au cours d’une même recherche est probable, généralement lorsque la configuration de la recherche prend en compte toutes les boîtes aux lettres de votre organisation. Cette restriction s’applique même si moins de 50 000 boîtes aux lettres contiennent des éléments qui correspondent à la requête de recherche.

- Un maximum de 10 éléments par boîte aux lettres peuvent être supprimés à la fois. Sachant que la fonction de recherche et suppression de messages est censée être un outil de réponse aux incidents, cette limite permet de s’assurer que les messages sont rapidement supprimés des boîtes aux lettres. Cette fonctionnalité n’est pas conçue pour nettoyer les boîtes aux lettres des utilisateurs.

> [!IMPORTANT]
> Les éléments de courrier dans un ensemble de révisions dans un cas eDiscovery (Premium) ne peuvent pas être supprimés à l’aide des procédures décrites dans cet article. Cela est dû au fait que les éléments d’un jeu de révision sont des copies d’éléments du service en direct qui sont copiés et stockés à un emplacement stockage Azure. Cela signifie qu’elles ne seront pas retournées par une recherche de contenu que vous créez à l’étape 3. Pour supprimer des éléments d’un jeu de révision, vous devez supprimer le cas eDiscovery (Premium) qui contient le jeu de révisions. Pour plus d’informations, consultez [Fermer ou supprimer un cas eDiscovery (Premium).](close-or-delete-case.md)
  
## <a name="step-8-verify-provide-a-proof-of-deletion-and-audit"></a>Étape 8 : Vérifier, fournir une preuve de suppression et auditer

La dernière étape du flux de travail pour gérer un incident de débordement de données consiste à vérifier que les données renversées ont été supprimées définitivement de la boîte aux lettres en accédant au cas eDiscovery et en réexécutant la même requête de recherche qui a été utilisée pour supprimer ces données afin de confirmer qu’aucun résultat n’est retourné. Une fois que vous avez confirmé que les données renversées ont été supprimées définitivement, vous pouvez exporter un rapport et l’inclure (avec le rapport d’origine) comme preuve de suppression. Ensuite, vous pouvez [fermer le dossier](close-reopen-delete-core-ediscovery-cases.md) qui vous permettra de le rouvrir si vous devez y faire référence à l’avenir. En outre, vous pouvez également rétablir l’état précédent des boîtes aux lettres, supprimer la requête de recherche utilisée pour rechercher les données renversées et rechercher des enregistrements d’audit des tâches effectuées lors de la gestion de l’incident de débordement de données.
  
### <a name="reverting-the-mailboxes-to-their-previous-state"></a>Rétablir l’état précédent des boîtes aux lettres

Si vous avez modifié une configuration de boîte aux lettres à l’étape 6 pour préparer les boîtes aux lettres avant la suppression des données renversées, vous devez les rétablir à leur état précédent. Consultez « Étape 6 : Rétablir l’état précédent de la boîte aux [lettres » dans Supprimer les éléments dans le dossier Éléments récupérables des boîtes aux lettres basées sur le cloud en attente](delete-items-in-the-recoverable-items-folder-of-mailboxes-on-hold.md#step-6-revert-the-mailbox-to-its-previous-state).
  
### <a name="deleting-the-search-query"></a>Suppression de la requête de recherche

Si les mots clés de la requête de recherche que vous avez créée et utilisée à l’étape 3 contiennent certaines des données réellement propagées, vous devez supprimer la requête de recherche pour éviter tout débordement de données supplémentaire.
  
1. Dans le Centre de sécurité et de conformité, ouvrez le cas eDiscovery, accédez à la page **Recherche** et sélectionnez la recherche de contenu appropriée.

2. Dans la page de menu volant, cliquez sur **Supprimer**.

    ![Sélectionnez la recherche, puis cliquez sur Supprimer dans la page de menu volant.](../media/O365-eDiscoverySolutions-DataSpillage-DeleteSearch.png)

### <a name="auditing-the-data-spillage-investigation-process"></a>Audit du processus d’examen des déversements de données

Vous pouvez rechercher dans le journal d’audit les activités eDiscovery qui ont été effectuées pendant l’enquête. Vous pouvez également rechercher dans le journal d’audit pour renvoyer les enregistrements d’audit de la commande **New-ComplianceSearchAction -Purge** que vous avez exécutée à l’étape 7 pour supprimer les données renversées. Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Rechercher le journal d’audit](search-the-audit-log-in-security-and-compliance.md)

- [Rechercher des activités eDiscovery dans le journal d’audit](search-for-ediscovery-activities-in-the-audit-log.md)
