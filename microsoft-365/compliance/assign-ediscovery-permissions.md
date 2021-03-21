---
title: Attribuer des autorisations eDiscovery dans le Centre de conformité & sécurité
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
description: Attribuez les autorisations requises pour effectuer des tâches liées à eDiscovery à l’aide du Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 98a731a726798ef463fd6b11f9be84c9f8cc95c0
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50919942"
---
# <a name="assign-ediscovery-permissions-in-the-security--compliance-center"></a>Attribuer des autorisations eDiscovery dans le Centre de conformité & sécurité

Si vous souhaitez que les personnes utilisent l’un des outils liés à [eDiscovery](ediscovery.md) dans le Centre de sécurité & conformité dans Office 365 ou le Centre de conformité Microsoft 365, vous devez leur attribuer les autorisations appropriées. Pour ce faire, la manière la plus facile consiste à ajouter le groupe de rôles approprié pour la personne à la page **Autorisations** du Centre de sécurité et conformité. Cette rubrique décrit les autorisations requises pour effectuer des tâches liées à eDiscovery et à la recherche de contenu à l’aide du Centre de sécurité & conformité.
  
Le principal groupe de rôles liés à eDiscovery dans le Centre de sécurité & conformité est appelé **Gestionnaire eDiscovery**. Ce groupe de rôles comprend deux sous-groupes.
  
- Gestionnaires **eDiscovery** : un gestionnaire eDiscovery peut utiliser l’outil de recherche de contenu dans le Centre de sécurité & conformité pour rechercher des emplacements de contenu dans l’organisation et effectuer diverses actions liées à la recherche, telles que l’aperçu et l’exportation des résultats de recherche. Les membres peuvent également créer et gérer des cas dans Core eDiscovery et Advanced eDiscovery, ajouter et supprimer des membres à un cas, créer des cas en tant que cas, exécuter des recherches associées à un cas et accéder aux données de cas. Les gestionnaires eDiscovery peuvent uniquement consulter et gérer les incidents qu’ils créent. Ils ne peuvent pas accéder aux cas créés par d’autres gestionnaires eDiscovery, ni les gérer.
  
- **Administrateurs eDiscovery** : ils sont membre du groupe de rôles Gestionnaire eDiscovery et peuvent effectuer la même recherche de contenu et les mêmes tâches liées à la gestion des cas que les gestionnaires eDiscovery. De plus, un administrateur de découverte électronique peut :
  
  - Accédez à tous les cas répertoriés dans les pages **eDiscovery et** **Advanced eDiscovery** dans le Centre de sécurité & conformité.

  - Accéder à des données dans Advanced eDiscovery pour tout cas au sein de l’organisation.
  
  - Gérer tous les cas eDiscovery après s’être ajouté en tant que membre du cas.
  
  Pour les raisons pour lesquelles vous souhaitez peut-être des administrateurs eDiscovery dans votre organisation, consultez [plus d’informations.](#more-information)

> [!NOTE]
> Pour analyser les données d’un utilisateur à l’aide d’Advanced eDiscovery, l’utilisateur (le dépositaire des données) doit se voir attribuer une licence Office 365 E5 ou Microsoft 365 E5. Par ailleurs, les utilisateurs ayant une licence Office 365 E1 ou Office 365 ou Microsoft 365 E3 peuvent se voir attribuer une licence de module de conformité Microsoft 365 E5 ou de découverte électronique et d’audit Microsoft 365. Les administrateurs, les responsables de la mise en conformité ou le personnel juridique affectés à des cas en tant que membres et qui utilisent Advanced eDiscovery pour collecter, afficher et analyser des données n’ont pas besoin d’une licence E5. Pour plus d’informations sur les licences Advanced eDiscovery, consultez La mise en [place d’Advanced eDiscovery.](get-started-with-advanced-ediscovery.md)
  
## <a name="confirm-your-roles"></a>Confirmer vos rôles

- Vous devez être membre du groupe de rôles Gestion de l’organisation ou avoir le rôle Gestion des rôles pour attribuer des autorisations eDiscovery dans le Centre de sécurité & conformité.

- Vous pouvez utiliser la cmdlet [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) dans le Centre de sécurité & conformité PowerShell pour ajouter un groupe de sécurité à messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles Gestionnaire eDiscovery. Toutefois, vous ne pouvez pas ajouter un groupe de sécurité à messagerie au sous-groupe Administrateurs eDiscovery. Pour plus d’informations, voir [plus d’informations.](#more-information) 
  
## <a name="assign-ediscovery-permissions-in-the-security--compliance-center"></a>Attribuer des autorisations eDiscovery dans le Centre de conformité & sécurité

1. Accédez à [https://protection.office.com](https://protection.office.com).
  
2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.
  
3. Dans le volet gauche du centre de sécurité et conformité, sélectionnez **Autorisations,** puis cochez la case en regard du Gestionnaire **eDiscovery.**
  
4. Dans la page de flyout du Gestionnaire **eDiscovery,** faites l’une des opérations suivantes en fonction des autorisations eDiscovery que vous souhaitez attribuer.
  
    **Pour faire d’un utilisateur un gestionnaire eDiscovery :** En plus **du Gestionnaire eDiscovery,** sélectionnez **Modifier.** Dans la section Choisir le gestionnaire **eDiscovery,** sélectionnez le lien hypertexte Choisir le gestionnaire **eDiscovery,** puis sélectionnez Ajouter une icône ![ ](../media/ITPro-EAC-AddIcon.gif) **Ajouter.** Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant que gestionnaire eDiscovery, puis sélectionnez **Ajouter**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**. Ensuite, dans la page de modification choisissez le gestionnaire  **eDiscovery,** sélectionnez Enregistrer pour enregistrer les modifications apportées à l’appartenance au Gestionnaire eDiscovery.
  
    **Pour faire d’un utilisateur un administrateur eDiscovery :** En plus **du Gestionnaire eDiscovery,** sélectionnez **Modifier.** In the **Choose eDiscovery Administrator** section, Under **eDiscovery Administrators**, select **Choose eDiscovery Administrator**, select **Edit**, and then select Add ![ Icon ](../media/ITPro-EAC-AddIcon.gif) **Add**. Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant qu’administrateur **eDiscovery,** puis  **ajoutez**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**. Ensuite, dans la page de modification choisissez l’administrateur  **eDiscovery,** sélectionnez Enregistrer pour enregistrer les modifications apportées à l’appartenance à l’administrateur eDiscovery.
  
> [!NOTE]
> Vous pouvez également utiliser la cmdlet **Add-eDiscoveryCaseAdmin** pour faire d’un utilisateur un administrateur eDiscovery. Toutefois, le rôle Gestion des cas doit être attribué à l’utilisateur avant de pouvoir utiliser cette cmdlet pour en faire un administrateur eDiscovery. Pour plus d’informations, [voir Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin). 
  
Dans la page Autorisations du Centre de sécurité & conformité, vous pouvez également attribuer aux utilisateurs des **autorisations** liées à la découverte électronique en les ajoutant aux groupes de rôles Administrateur de conformité, Gestion de l’organisation et Réviseur. Pour obtenir une description des rôles RBAC liés à eDiscovery attribués à chacun de ces groupes de rôles, voir rôles RBAC liés à [eDiscovery.](#rbac-roles-related-to-ediscovery)

## <a name="rbac-roles-related-to-ediscovery"></a>Rôles RBAC liés à eDiscovery

Le tableau suivant répertorie les rôles RBAC liés à eDiscovery dans le Centre de sécurité & conformité et indique les groupes de rôles intégrés affectés par défaut à chaque rôle.
  
| Role | Administrateur de conformité | Gestionnaire eDiscovery & administrateur | Gestion de l’organisation | Relecteur |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Gestion des cas <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Communication <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Recherche de conformité <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Consignataire <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Exporter <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Suspension <br/>  |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Preview <br/>  | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Révision <br/>  | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |![Coche](../media/checkmark.png) <br/> |
|Déchiffrement RMS <br/>  ||![Coche](../media/checkmark.png) <br/> |||
|Recherche et purge <br/> | <br/> | <br/> |![Coche](../media/checkmark.png)           <br/> | <br/> |
||||
  
Les sections suivantes décrivent chacun des rôles RBAC liés à eDiscovery répertoriés dans le tableau précédent.

### <a name="case-management"></a>Gestion des cas

Ce rôle permet aux utilisateurs de créer, modifier, supprimer et contrôler l’accès aux cas eDiscovery principaux et Advanced eDiscovery dans le Centre de sécurité & conformité. Comme indiqué précédemment, un utilisateur doit se voir attribuer le rôle Gestion des cas avant de pouvoir utiliser la cmdlet **Add-eDiscoveryCaseAdmin** pour en faire un administrateur eDiscovery.

Pour plus d’informations, consultez :

- [Prise en main de la découverte électronique de base](get-started-core-ediscovery.md)

- [Prise en main Advanced eDiscovery](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Communication

Ce rôle permet aux utilisateurs de gérer toutes les communications avec les dépositaires identifiés dans un cas Advanced eDiscovery. Cela inclut la création de notifications de mise en attente, de rappels de mise en attente et d’escalades vers la direction. L’utilisateur peut également suivre l’accusé de réception des notifications de conservation et gérer l’accès au portail des dépositaires utilisé par chaque dépositaire pour suivre les communications dans les cas où ils ont été identifiés comme dépositaires.

Pour plus d’informations, voir [Work with communications in Advanced eDiscovery](managing-custodian-communications.md).

### <a name="compliance-search"></a>Recherche de conformité

Ce rôle permet aux utilisateurs d’exécuter l’outil de recherche de contenu dans le Centre de sécurité & conformité pour rechercher des boîtes aux lettres et des dossiers publics, des sites SharePoint Online, des sites OneDrive Entreprise, des conversations Skype Entreprise, des groupes Microsoft 365 et Microsoft Teams et des groupes Yammer. Ce rôle permet à un utilisateur d’obtenir une estimation des résultats de recherche et de créer des rapports d’exportation, mais des rôles supplémentaires sont nécessaires pour lancer des actions de recherche de contenu telles que l’aperçu, l’exportation ou la suppression des résultats de recherche.

Les utilisateurs qui ont le rôle de recherche de conformité mais ne disposent pas du rôle Aperçu peuvent afficher un aperçu des résultats d’une recherche dans laquelle l’action d’aperçu a été initiée par un utilisateur auquel le rôle Aperçu est attribué. L’utilisateur sans le rôle Aperçu peut afficher un aperçu des résultats pendant deux semaines après la création de l’action d’aperçu initiale.

De même, les utilisateurs qui ont le rôle De recherche de conformité mais n’ont pas le rôle Exporter peuvent télécharger les résultats d’une recherche dans laquelle l’action d’exportation a été lancée par un utilisateur auquel le rôle d’exportation est attribué. L’utilisateur sans le rôle d’exportation peut télécharger les résultats d’une recherche pendant deux semaines après la création de l’action d’exportation initiale. Après cela, ils ne peuvent pas télécharger les résultats, sauf si une personne ayant le rôle Export redémarre l’exportation.

Pour plus d’informations, [voir Recherche de contenu dans Office 365.](content-search.md)

### <a name="custodian"></a>Consignataire

Ce rôle permet aux utilisateurs d’identifier et de gérer les dépositaires des cas Advanced eDiscovery et d’utiliser les informations d’Azure Active Directory et d’autres sources pour rechercher les sources de données associées aux dépositaires. L’utilisateur peut associer d’autres sources de données telles que des boîtes aux lettres, des sites SharePoint et Teams à des dépositaires dans un cas. L’utilisateur peut également placer une conservation légale sur les sources de données associées aux dépositaires pour conserver le contenu dans le contexte d’un cas.

Pour plus d’informations, [voir Travailler avec des dépositaires dans Advanced eDiscovery.](managing-custodians.md)

### <a name="export"></a>Exporter

Le rôle permet aux utilisateurs d’exporter les résultats d’une recherche de contenu vers un ordinateur local. Il leur permet également de préparer les résultats de recherche pour analyse dans Advanced eDiscovery.

Pour plus d’informations sur l’exportation des résultats de recherche, voir [Export search results from Security & Compliance Center](export-search-results.md).

### <a name="hold"></a>Suspension

Ce rôle permet aux utilisateurs de placer le contenu en attente dans les boîtes aux lettres, les dossiers publics, les sites, les conversations Skype Entreprise et les groupes Microsoft 365. Lorsque le contenu est en attente, les propriétaires de contenu peuvent toujours modifier ou supprimer le contenu d’origine, mais le contenu sera conservé jusqu’à la suppression ou jusqu’à l’expiration de la mise en attente.

Pour plus d’informations sur les maintiens en place, voir :

- [Créer une attente dans Core eDiscovery](create-ediscovery-holds.md) 

- [Créer une attente dans Advanced eDiscovery](add-custodians-to-case.md)

### <a name="preview"></a>Preview

Ce rôle permet aux utilisateurs d’afficher une liste d’éléments qui ont été renvoyés par une recherche de contenu. Les utilisateurs peuvent également ouvrir et afficher chaque élément de la liste pour afficher son contenu.

### <a name="review"></a>Révision

Ce rôle permet aux utilisateurs d’accéder aux jeux de révision [dans Advanced eDiscovery](overview-ediscovery-20.md). Les utilisateurs qui se voient attribuer ce rôle peuvent voir et ouvrir la liste des cas sur la page **eDiscovery >** Avancé du Centre de conformité Microsoft 365 dont ils sont membres. Une fois que l’utilisateur a accédé à un cas Advanced eDiscovery, il peut sélectionner ensembles de révision **pour** accéder aux données de cas. Ce rôle ne permet pas à l’utilisateur d’afficher un aperçu des résultats d’une recherche de collection associée au cas ou d’effectuer d’autres tâches de recherche ou de gestion des cas. Les utilisateurs ayant ce rôle peuvent uniquement accéder aux données d’un jeu à réviser.

### <a name="rms-decrypt"></a>Déchiffrement RMS

Ce rôle permet aux utilisateurs d’afficher des messages électroniques protégés par des droits lors de l’aperçu des résultats de recherche et d’exporter des messages électroniques protégés par des droits déchiffrés. Ce rôle permet également aux utilisateurs d’afficher (et d’exporter) un fichier chiffré avec une technologie de chiffrement [Microsoft](encryption.md) lorsque le fichier chiffré est joint à un message électronique inclus dans les résultats d’une recherche de découverte électronique. En outre, ce rôle permet aux utilisateurs d’examiner et d’interroger des pièces jointes chiffrées qui sont ajoutées à un jeu à réviser dans Advanced eDiscovery. Pour plus d’informations sur le déchiffrement dans eDiscovery, voir Déchiffrement dans les outils [eDiscovery de Microsoft 365.](ediscovery-decryption.md)

### <a name="search-and-purge"></a>Recherche et purge

Ce rôle permet aux utilisateurs d’effectuer une suppression en bloc de données correspondant aux critères d’une recherche de contenu. Pour plus d’informations, [voir Rechercher et supprimer des messages électroniques dans votre organisation.](search-for-and-delete-messages-in-your-organization.md)

## <a name="more-information"></a>Plus d’informations

- **Pourquoi créer un administrateur de découverte électronique ?** Comme indiqué précédemment, un administrateur de découverte électronique est membre du groupe de rôles de gestionnaire de découverte électronique, qui peut afficher tous les cas de découverte électronique, et y accéder, de votre organisation. Cette capacité d’accès à tous les cas de découverte électronique a deux objectifs importants :

  - Si une personne qui est le seul membre d’un cas de découverte électronique quitte votre organisation, personne (y compris les membres du groupe de rôles de gestion de l’organisation ou un autre membre du groupe de rôles de gestionnaire de découverte électronique) ne peut accéder à ce cas, car personne n’en est alors membre. Dans ce cas, il n’y aurait aucun moyen d’accéder aux données dans le cas. Toutefois, étant donné qu’un administrateur eDiscovery peut accéder à tous les cas eDiscovery dans l’organisation, il peut afficher le cas et s’ajouter lui-même ou un autre gestionnaire eDiscovery en tant que membre du cas.

  - Étant donné qu’un administrateur eDiscovery peut afficher et accéder à tous les cas eDiscovery principaux et Advanced eDiscovery, il peut auditer et surveiller tous les cas et les recherches de conformité associées. Cela permet d’éviter toute utilisation abusive des recherches de conformité ou des cas eDiscovery. Et comme les administrateurs eDiscovery peuvent accéder à des informations potentiellement sensibles dans les résultats d’une recherche de conformité, vous devez limiter le nombre de personnes qui sont des administrateurs eDiscovery.

- **Puis-je ajouter un groupe en tant que membre du groupe de rôles Gestionnaire eDiscovery ?** Comme indiqué précédemment, vous pouvez ajouter un groupe de sécurité à messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles Gestionnaire eDiscovery à l’aide de la cmdlet **Add-RoleGroupMember** dans le Centre de sécurité & conformité PowerShell. Par exemple, vous pouvez exécuter la commande suivante pour ajouter un groupe de sécurité à messagerie au groupe de rôles Gestionnaire eDiscovery. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Les groupes de distribution Exchange et les groupes Microsoft 365 ne sont pas pris en charge. Vous devez utiliser un groupe de sécurité à messagerie, que vous pouvez créer dans Exchange Online PowerShell en exécutant `New-DistributionGroup -Type Security` . Vous pouvez également créer un groupe de sécurité à messagerie (et ajouter des membres) dans le Centre d’administration Exchange ou dans le Centre d’administration Microsoft 365. L’ajout d’une nouvelle sécurité à messagerie au groupe de rôles gestionnaires eDiscovery peut prendre jusqu’à 60 minutes après sa création. 

    Comme indiqué précédemment, vous ne pouvez pas faire d’un groupe de sécurité à messagerie un administrateur eDiscovery à l’aide de la cmdlet **Add-eDiscoveryCaseAdmin** dans le Centre de sécurité & conformité PowerShell. Vous pouvez uniquement ajouter des utilisateurs individuels en tant qu’administrateurs eDiscovery.

    Vous ne pouvez pas non plus ajouter un groupe de sécurité à messagerie en tant que membre d’un cas.