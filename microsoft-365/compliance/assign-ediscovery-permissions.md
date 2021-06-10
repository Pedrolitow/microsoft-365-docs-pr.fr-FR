---
title: Attribuer des autorisations eDiscovery dans le centre Microsoft 365 conformité
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5b9a067b-9d2e-4aa5-bb33-99d8c0d0b5d7
description: Attribuez les autorisations requises pour effectuer des tâches liées à eDiscovery à l’aide du centre Microsoft 365 conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 63afafbb8254169e266e5a3305df64aa9d271f79
ms.sourcegitcommit: 3b9fab82d63aea41d5f544938868c5d2cbf52d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/05/2021
ms.locfileid: "52782452"
---
# <a name="assign-ediscovery-permissions-in-the-microsoft-365-compliance-center"></a>Attribuer des autorisations eDiscovery dans le centre Microsoft 365 conformité

Si vous souhaitez que les personnes utilisent l’un des outils liés à [eDiscovery](ediscovery.md) dans le centre de conformité Microsoft 365, vous devez leur attribuer les autorisations appropriées. Le moyen le plus simple de le faire consiste à ajouter à la personne le groupe de rôles approprié sur la page **Autorisations** dans le centre de conformité. Cette rubrique décrit les autorisations requises pour effectuer des tâches eDiscovery.
  
Le groupe de rôles principal lié à eDiscovery dans Microsoft 365 conformité est appelé **Gestionnaire eDiscovery**. Ce groupe de rôles comprend deux sous-groupes.
  
- Gestionnaires **eDiscovery** : un gestionnaire eDiscovery peut utiliser les outils de recherche eDiscovery pour rechercher des emplacements de contenu dans l’organisation et effectuer diverses actions liées à la recherche, telles que la prévisualisation et l’exportation des résultats de recherche. Les membres peuvent également créer et gérer des cas dans Core eDiscovery et Advanced eDiscovery, ajouter et supprimer des membres à un cas, créer des cas en tant que cas, exécuter des recherches associées à un cas et accéder aux données de cas. Les gestionnaires eDiscovery peuvent uniquement consulter et gérer les incidents qu’ils créent. Ils ne peuvent pas accéder aux cas créés par d’autres gestionnaires eDiscovery, ni les gérer.
  
- **Administrateurs eDiscovery** : ils sont membre du groupe de rôles Gestionnaire eDiscovery et peuvent effectuer la même recherche de contenu et les mêmes tâches liées à la gestion des cas que les gestionnaires eDiscovery. De plus, un administrateur de découverte électronique peut :
  
  - Accédez à tous les cas répertoriés dans les pages core **eDiscovery** et **Advanced eDiscovery** dans le centre Microsoft 365 conformité.

  - Accéder à des données dans Advanced eDiscovery pour tout cas au sein de l’organisation.
  
  - Gérer tous les cas eDiscovery après s’être ajouté en tant que membre du cas.
  
  Pour les raisons pour lesquelles vous souhaitez peut-être des administrateurs eDiscovery dans votre organisation, consultez [plus d’informations.](#more-information)

> [!NOTE]
> Pour analyser les données d’un utilisateur à l’aide de Advanced eDiscovery, l’utilisateur (le dépositaire des données) doit se voir attribuer une licence Office 365 E5 ou Microsoft 365 E5 licence. Par ailleurs, les utilisateurs titulaires d’une licence Office 365 E1 ou Office 365 ou Microsoft 365 E3 peuvent se voir attribuer une licence de module Microsoft 365 E5 Conformité ou Microsoft 365 eDiscovery et Audit. Les administrateurs, les responsables de la mise en conformité ou le personnel juridique affectés à des cas en tant que membres et qui utilisent Advanced eDiscovery pour collecter, afficher et analyser des données n’ont pas besoin d’une licence E5. Pour plus d’informations sur Advanced eDiscovery licences, voir [Abonnements et licences dans Advanced eDiscovery](overview-ediscovery-20.md#subscriptions-and-licensing).
  
## <a name="before-you-assign-permissions"></a>Avant d’attribuer des autorisations

- Vous devez être membre du groupe de rôles Gestion de l’organisation ou avoir le rôle Gestion des rôles pour attribuer des autorisations eDiscovery dans le centre de conformité Microsoft 365'organisation.

- Vous pouvez utiliser la cmdlet [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) dans le Centre de sécurité & conformité PowerShell pour ajouter un groupe de sécurité à messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles Gestionnaire eDiscovery. Toutefois, vous ne pouvez pas ajouter un groupe de sécurité à messagerie au sous-groupe Administrateurs eDiscovery. Pour plus d’informations, voir [plus d’informations.](#more-information) 
  
## <a name="assign-ediscovery-permissions"></a>Attribution d’autorisations de eDiscovery

1. Go to <https://compliance.microsoft.com> and sign in using an account that can assign permissions.
  
2. Dans le volet gauche du centre de conformité Microsoft 365, sélectionnez **Autorisations.**

3. Dans la page **Autorisations & rôles,** sous **Centre** de conformité, cliquez sur **Rôles**.

4. Dans la page **Rôles du Centre de** conformité, sélectionnez **gestionnaire eDiscovery.**
  
5. Dans la page volant **eDiscovery Manager,** faites l’une des opérations suivantes en fonction des autorisations eDiscovery que vous souhaitez attribuer.
  
    **Pour faire d’un utilisateur un gestionnaire eDiscovery :** En plus **du Gestionnaire eDiscovery,** sélectionnez **Modifier.** Dans la page **Choisir l’Assistant Gestionnaire eDiscovery,** cliquez sur ![ Ajouter une ](../media/ITPro-EAC-AddIcon.gif) **icône.** Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant que gestionnaire eDiscovery, puis sélectionnez **Ajouter**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**. Ensuite, dans la page Modifier l’Assistant Choisir le gestionnaire **eDiscovery,** sélectionnez **Enregistrer** pour enregistrer les modifications apportées à l’appartenance au gestionnaire eDiscovery.
  
    **Pour faire d’un utilisateur un administrateur eDiscovery :** En plus **de l’administrateur eDiscovery,** sélectionnez **Modifier.** Dans la page **Choisir un administrateur de découverte électronique,** cliquez sur Ajouter une ![ ](../media/ITPro-EAC-AddIcon.gif) **icône.** Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant qu’administrateur **eDiscovery,** puis  **ajoutez**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**. Ensuite, dans la page Modifier l’Assistant Choisir  l’administrateur **eDiscovery,** sélectionnez Enregistrer pour enregistrer les modifications apportées à l’appartenance à l’administrateur eDiscovery.
  
> [!NOTE]
> Vous pouvez également utiliser la cmdlet **Add-eDiscoveryCaseAdmin** pour faire d’un utilisateur un administrateur eDiscovery. Toutefois, le rôle Gestion des cas doit être attribué à l’utilisateur avant de pouvoir utiliser cette cmdlet pour en faire un administrateur eDiscovery. Pour plus d’informations, [voir Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin). 
  
Dans la page Autorisations du Centre de conformité Microsoft 365, vous pouvez également attribuer aux utilisateurs des autorisations liées à la découverte électronique en les ajoutant aux groupes de **rôles** Administrateur de conformité, Gestion de l’organisation et Réviseur. Pour obtenir une description des rôles RBAC liés à eDiscovery attribués à chacun de ces groupes de rôles, voir rôles RBAC liés à [eDiscovery.](#rbac-roles-related-to-ediscovery)

## <a name="rbac-roles-related-to-ediscovery"></a>Rôles RBAC liés à eDiscovery

Le tableau suivant répertorie les rôles RBAC liés à eDiscovery dans le centre de conformité Microsoft 365 et indique les groupes de rôles intégrés affectés par défaut à chaque rôle.
  
| Role | Administrateur de conformité | Gestionnaire eDiscovery & administrateur | Gestion de l’organisation | Relecteur |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Gestion des cas <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Communication <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Recherche de conformité <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Consignataire <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Exporter <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Suspension <br/>  |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Aperçu <br/>  | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Révision <br/>  | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |![Coche](../media/checkmark.png) <br/> |
|Déchiffrement RMS <br/>  ||![Coche](../media/checkmark.png) <br/> |||
|Recherche et purge <br/> | <br/> | <br/> |![Coche](../media/checkmark.png)           <br/> | <br/> |
||||
  
Les sections suivantes décrivent chacun des rôles RBAC liés à eDiscovery répertoriés dans le tableau précédent.

### <a name="case-management"></a>Gestion des cas

Ce rôle permet aux utilisateurs de créer, de modifier, de supprimer et de contrôler l’accès à core eDiscovery et à Advanced eDiscovery cas dans le centre Microsoft 365 conformité. Comme indiqué précédemment, un utilisateur doit se voir attribuer le rôle Gestion des cas avant de pouvoir utiliser la cmdlet **Add-eDiscoveryCaseAdmin** pour en faire un administrateur eDiscovery.

Pour plus d’informations, voir :

- [Prise en main de la découverte électronique de base](get-started-core-ediscovery.md)

- [Prise en main Advanced eDiscovery](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Communication

Ce rôle permet aux utilisateurs de gérer toutes les communications avec les dépositaires identifiés dans Advanced eDiscovery cas. Cela inclut la création de notifications de mise en attente, de rappels de mise en attente et d’escalades vers la direction. L’utilisateur peut également suivre l’accusé de réception des notifications de conservation et gérer l’accès au portail des dépositaires utilisé par chaque dépositaire pour suivre les communications pour les cas où ils ont été identifiés comme dépositaires.

Pour plus d’informations, voir [Travailler avec les communications dans Advanced eDiscovery](managing-custodian-communications.md).

### <a name="compliance-search"></a>Recherche de conformité

Ce rôle permet aux utilisateurs d’exécuter l’outil de recherche de contenu dans le Centre de conformité Microsoft 365 pour rechercher des boîtes aux lettres et des dossiers publics, des sites SharePoint Online, des sites OneDrive Entreprise, des conversations Skype Entreprise, des groupes Microsoft 365 et des groupes Microsoft Teams et Yammer. Ce rôle permet à un utilisateur d’obtenir une estimation des résultats de recherche et de créer des rapports d’exportation, mais d’autres rôles sont nécessaires pour lancer des actions de recherche de contenu telles que l’aperçu, l’exportation ou la suppression des résultats de recherche.

Les utilisateurs qui ont le rôle De recherche de conformité mais ne disposent pas du rôle Aperçu peuvent afficher un aperçu des résultats d’une recherche dans laquelle l’action de prévisualisation a été initiée par un utilisateur auquel le rôle Aperçu est attribué. L’utilisateur sans le rôle Aperçu peut afficher un aperçu des résultats pendant deux semaines après la création de l’action d’aperçu initiale.

De même, les utilisateurs qui ont le rôle De recherche de conformité mais n’ont pas le rôle Exporter peuvent télécharger les résultats d’une recherche dans laquelle l’action d’exportation a été lancée par un utilisateur auquel le rôle d’exportation est attribué. L’utilisateur sans le rôle d’exportation peut télécharger les résultats d’une recherche pendant deux semaines après la création de l’action d’exportation initiale. Après cela, ils ne peuvent pas télécharger les résultats, sauf si une personne avec le rôle Export redémarre l’exportation.

Pour plus d’informations, [voir Recherche de contenu dans Office 365](content-search.md).

### <a name="custodian"></a>Consignataire

Ce rôle permet aux utilisateurs d’identifier et de gérer les dépositaires pour les cas Advanced eDiscovery et d’utiliser les informations provenant de Azure Active Directory et d’autres sources pour rechercher des sources de données associées aux dépositaires. L’utilisateur peut associer d’autres sources de données telles que des boîtes aux lettres, SharePoint sites et Teams des dépositaires dans un cas. L’utilisateur peut également placer en conservation légale les sources de données associées aux dépositaires pour conserver le contenu dans le contexte d’un cas.

Pour plus d’informations, [voir Travailler avec les dépositaires dans Advanced eDiscovery](managing-custodians.md).

### <a name="export"></a>Exporter

Le rôle permet aux utilisateurs d’exporter les résultats d’une recherche de contenu vers un ordinateur local. Il leur permet également de préparer les résultats de recherche pour analyse dans Advanced eDiscovery.

Pour plus d’informations sur l’exportation des résultats de recherche, voir Exporter les résultats de recherche à [partir Microsoft 365 centre de conformité.](export-search-results.md)

### <a name="hold"></a>Suspension

Ce rôle permet aux utilisateurs de placer le contenu en attente dans des boîtes aux lettres, des dossiers publics, des sites, des conversations Skype Entreprise et des groupes Microsoft 365 données. Lorsque le contenu est en attente, les propriétaires de contenu peuvent toujours modifier ou supprimer le contenu d’origine, mais le contenu sera conservé jusqu’à la suppression ou jusqu’à l’expiration de la mise en attente.

Pour plus d’informations sur les maintiens en place, voir :

- [Créer une attente dans Core eDiscovery](create-ediscovery-holds.md) 

- [Créer une attente dans Advanced eDiscovery](add-custodians-to-case.md)

### <a name="preview"></a>Aperçu

Ce rôle permet aux utilisateurs d’afficher une liste d’éléments qui ont été renvoyés par une recherche de contenu. Les utilisateurs peuvent également ouvrir et afficher chaque élément de la liste pour afficher son contenu.

### <a name="review"></a>Révision

Ce rôle permet aux utilisateurs d’accéder aux jeux de révision [Advanced eDiscovery](overview-ediscovery-20.md). Les utilisateurs affectés à ce rôle peuvent voir et ouvrir la liste des cas sur la page **eDiscovery >** Advanced dans le Centre de conformité Microsoft 365 dont ils sont membres. Une fois que l’utilisateur a accédé Advanced eDiscovery cas, il peut sélectionner les ensembles de révision **pour** accéder aux données de cas. Ce rôle ne permet pas à l’utilisateur d’afficher un aperçu des résultats d’une recherche de collection associée au cas ou d’effectuer d’autres tâches de recherche ou de gestion des cas. Les utilisateurs ayant ce rôle peuvent uniquement accéder aux données d’un jeu à réviser.

### <a name="rms-decrypt"></a>Déchiffrement RMS

Ce rôle permet aux utilisateurs d’afficher des messages électroniques protégés par des droits lors de l’aperçu des résultats de recherche et d’exporter des messages électroniques protégés par des droits déchiffrés. Ce rôle permet également aux utilisateurs d’afficher (et d’exporter) un fichier chiffré avec une technologie de chiffrement [Microsoft](encryption.md) lorsque le fichier chiffré est joint à un message électronique inclus dans les résultats d’une recherche de découverte électronique. En outre, ce rôle permet aux utilisateurs d’examiner et d’interroger des pièces jointes chiffrées qui sont ajoutées à un groupe de révision dans Advanced eDiscovery. Pour plus d’informations sur le déchiffrement dans eDiscovery, voir Déchiffrement dans [Microsoft 365 outils eDiscovery](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Recherche et purge

Ce rôle permet aux utilisateurs d’effectuer une suppression en bloc de données correspondant aux critères d’une recherche de contenu. Pour plus d’informations, [voir Rechercher et supprimer des messages électroniques dans votre organisation.](search-for-and-delete-messages-in-your-organization.md)

## <a name="more-information"></a>Plus d’informations

- **Pourquoi créer un administrateur de découverte électronique ?** Comme indiqué précédemment, un administrateur de découverte électronique est membre du groupe de rôles de gestionnaire de découverte électronique, qui peut afficher tous les cas de découverte électronique, et y accéder, de votre organisation. Cette capacité d’accès à tous les cas de découverte électronique a deux objectifs importants :

  - Si une personne qui est le seul membre d’un cas de découverte électronique quitte votre organisation, personne (y compris les membres du groupe de rôles de gestion de l’organisation ou un autre membre du groupe de rôles de gestionnaire de découverte électronique) ne peut accéder à ce cas, car personne n’en est alors membre. Dans ce cas, il n’y aurait aucun moyen d’accéder aux données dans le cas. Toutefois, étant donné qu’un administrateur eDiscovery peut accéder à tous les cas eDiscovery dans l’organisation, il peut afficher le cas et s’ajouter lui-même ou un autre gestionnaire eDiscovery en tant que membre du cas.

  - Étant donné qu’un administrateur eDiscovery peut afficher et accéder à tous les cas eDiscovery et Advanced eDiscovery principaux, il peut auditer et surveiller tous les cas et les recherches de conformité associées. Cela permet d’éviter toute utilisation abusive des recherches de conformité ou des cas eDiscovery. Et comme les administrateurs eDiscovery peuvent accéder à des informations potentiellement sensibles dans les résultats d’une recherche de conformité, vous devez limiter le nombre de personnes qui sont des administrateurs eDiscovery.

- **Puis-je ajouter un groupe en tant que membre du groupe de rôles Gestionnaire eDiscovery ?** Comme expliqué précédemment, vous pouvez ajouter un groupe de sécurité à messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles Gestionnaire eDiscovery à l’aide de la cmdlet **Add-RoleGroupMember** dans le Centre de sécurité & conformité PowerShell. Par exemple, vous pouvez exécuter la commande suivante pour ajouter un groupe de sécurité à messagerie au groupe de rôles Gestionnaire eDiscovery. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange groupes de distribution et Microsoft 365 de distribution ne sont pas pris en charge. Vous devez utiliser un groupe de sécurité à messagerie, que vous pouvez créer dans Exchange Online PowerShell en exécutant `New-DistributionGroup -Type Security` . Vous pouvez également créer un groupe de sécurité à messagerie (et ajouter des membres) dans le centre d’administration Exchange ou dans le centre d’administration Microsoft 365 messagerie. L’ajout d’une nouvelle sécurité à messagerie au groupe de rôles gestionnaires eDiscovery peut prendre jusqu’à 60 minutes après sa création. 

    Comme indiqué précédemment, vous ne pouvez pas faire d’un groupe de sécurité à messagerie un administrateur eDiscovery à l’aide de la cmdlet **Add-eDiscoveryCaseAdmin** dans le Centre de sécurité & conformité PowerShell. Vous pouvez uniquement ajouter des utilisateurs individuels en tant qu’administrateurs eDiscovery.

    Vous ne pouvez pas non plus ajouter un groupe de sécurité à messagerie en tant que membre d’un cas.