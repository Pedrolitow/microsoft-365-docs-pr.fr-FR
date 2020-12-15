---
title: Attribuer des autorisations eDiscovery dans le centre de sécurité & conformité
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
description: Affecter les autorisations requises pour effectuer des tâches liées à la découverte électronique à l’aide du centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: f4271d7cc7a9c9239aadb8ca2357e000f4f45e80
ms.sourcegitcommit: 29eb89b8ba0628fbef350e8995d2c38369a4ffa2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/15/2020
ms.locfileid: "49682605"
---
# <a name="assign-ediscovery-permissions-in-the-security--compliance-center"></a>Attribuer des autorisations eDiscovery dans le centre de sécurité & conformité

Si vous souhaitez que les utilisateurs puissent utiliser l’un des [outils de découverte électronique](ediscovery.md) dans le centre de sécurité & conformité dans Office 365 ou le centre de conformité Microsoft 365, vous devez leur attribuer les autorisations appropriées. Pour ce faire, la manière la plus facile consiste à ajouter le groupe de rôles approprié pour la personne à la page **Autorisations** du Centre de sécurité et conformité. Cette rubrique décrit les autorisations requises pour effectuer des tâches de recherche de contenu et de découverte électronique à l’aide du centre de sécurité & conformité.
  
Le groupe de rôles de découverte électronique principal dans le centre de sécurité & conformité est appelé **Gestionnaire eDiscovery**. Ce groupe de rôles comprend deux sous-groupes.
  
- **gestionnaires eDiscovery** : un gestionnaire eDiscovery peut utiliser l’outil de recherche de contenu dans le centre de sécurité & Compliance Center pour rechercher des emplacements de contenu dans l’organisation et effectuer diverses actions liées à la recherche, telles que l’aperçu et l’exportation des résultats de recherche. Les membres peuvent également créer et gérer des cas dans la découverte électronique de base et la découverte électronique avancée, ajouter et supprimer des membres à un cas, créer des suspensions de cas, exécuter des recherches associées à un cas et accéder à des données de cas. Les gestionnaires eDiscovery peuvent uniquement consulter et gérer les incidents qu’ils créent. Ils ne peuvent pas accéder aux cas créés par d’autres gestionnaires eDiscovery, ni les gérer.
  
- **Administrateurs eDiscovery** : ils sont membre du groupe de rôles Gestionnaire eDiscovery et peuvent effectuer la même recherche de contenu et les mêmes tâches liées à la gestion des cas que les gestionnaires eDiscovery. De plus, un administrateur de découverte électronique peut :
  
  - Accédez à tous les cas répertoriés sur les pages **eDiscovery** et **eDiscovery avancées** dans le centre de conformité & Compliance Center.

  - Accéder à des données dans Advanced eDiscovery pour tout cas au sein de l’organisation.
  
  - Gérer tous les cas eDiscovery après s’être ajouté en tant que membre du cas.
  
  Consultez la section [plus d’informations](#more-information) pour connaître les raisons pour lesquelles vous pouvez souhaiter des administrateurs de découverte électronique dans votre organisation.

> [!NOTE]
> Pour analyser les données d’un utilisateur à l’aide de Advanced eDiscovery, l’utilisateur (le dépositaire des données) doit disposer d’une licence Office 365 E5 ou Microsoft 365 E5. Par ailleurs, les utilisateurs disposant d’une licence Office 365 E1 ou Office 365 ou Microsoft 365 E3 peuvent se voir attribuer une conformité Microsoft 365 E5 ou une licence de module complémentaire de découverte électronique et d’audit Microsoft 365. Les administrateurs, les responsables de la mise en conformité ou le personnel juridique qui sont affectés à des cas en tant que membres et utilisent Advanced eDiscovery pour collecter, afficher et analyser des données n’ont pas besoin d’une licence E5. Pour plus d’informations sur la gestion des licences eDiscovery avancée, consultez la rubrique [prise en main de Advanced eDiscovery](get-started-with-advanced-ediscovery.md).
  
## <a name="confirm-your-roles"></a>Vérifier vos rôles

- Vous devez être membre du groupe de rôles gestion de l’organisation ou disposer du rôle de gestion des rôles pour attribuer des autorisations eDiscovery dans le centre de sécurité & conformité.

- Vous pouvez utiliser la cmdlet [Add-RoleGroupMember](https://docs.microsoft.com/powershell/module/exchange/Add-RoleGroupMember) dans Security & Compliance Center PowerShell pour ajouter un groupe de sécurité à extension messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles gestionnaire de découverte électronique. Toutefois, vous ne pouvez pas ajouter un groupe de sécurité à extension messagerie au sous-groupe administrateurs eDiscovery. Pour plus d’informations, reportez-vous à la section [more information](#more-information) . 
  
## <a name="assign-ediscovery-permissions-in-the-security--compliance-center"></a>Attribuer des autorisations eDiscovery dans le centre de sécurité & conformité

1. Accédez à [https://protection.office.com](https://protection.office.com).
  
2. Connectez-vous à l’aide de votre compte scolaire ou professionnel.
  
3. Dans le volet gauche du centre de sécurité et de conformité, sélectionnez **autorisations**, puis sélectionnez la case à cocher en regard de **Gestionnaire eDiscovery**.
  
4. Sur la page de menu volant du **Gestionnaire eDiscovery** , effectuez l’une des opérations suivantes en fonction des autorisations de découverte électronique que vous souhaitez attribuer.
  
    **Pour faire d’un utilisateur un gestionnaire eDiscovery :** En regard de **Gestionnaire eDiscovery**, sélectionnez **modifier**. Dans la section **choisir un gestionnaire eDiscovery** , sélectionnez le lien hypertexte **choisir le gestionnaire eDiscovery** , puis ajouter une ![ icône ](../media/ITPro-EAC-AddIcon.gif) **Ajouter**. Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant que gestionnaire eDiscovery, puis sélectionnez **Ajouter**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **terminé**. Ensuite, dans la page d’édition choisir le menu volant du **Gestionnaire eDiscovery** , sélectionnez **Enregistrer** pour enregistrer les modifications apportées à l’appartenance au gestionnaire eDiscovery.
  
    **Pour faire d’un utilisateur un administrateur de découverte électronique :** En regard de **Gestionnaire eDiscovery**, sélectionnez **modifier**. Dans la section **choisir un administrateur** eDiscovery, sous administrateurs de la **découverte électronique**, sélectionnez **choisir un administrateur eDiscovery**, sélectionnez **modifier**, puis ajouter une ![ icône ](../media/ITPro-EAC-AddIcon.gif) **Ajouter**. Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant qu' **administrateur de découverte électronique**, puis  **Ajoutez**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **terminé**. Ensuite, dans la page d’édition choisir le menu volant **administrateur eDiscovery** , sélectionnez **Enregistrer** pour enregistrer les modifications apportées à l’appartenance de l’administrateur de découverte électronique.
  
> [!NOTE]
> Vous pouvez également utiliser l’applet de commande **Add-eDiscoveryCaseAdmin** pour faire d’un utilisateur un administrateur de découverte électronique. Toutefois, l’utilisateur doit se voir attribuer le rôle de gestion des cas avant de pouvoir utiliser cette applet de commande pour en faire un administrateur eDiscovery. Pour plus d’informations, voir [Add-eDiscoveryCaseAdmin](https://go.microsoft.com/fwlink/p/?LinkID=798217). 
  
Sur la page **autorisations** du centre de sécurité & conformité, vous pouvez également attribuer des autorisations liées à la découverte électronique aux utilisateurs en les ajoutant aux groupes de rôles Administrateur de conformité, gestion de l’organisation et réviseur. Pour obtenir une description des rôles RBAC liés à la découverte électronique affectés à chacun de ces groupes de rôles, consultez la section [rôles RBAC liés à eDiscovery](#rbac-roles-related-to-ediscovery) .

## <a name="rbac-roles-related-to-ediscovery"></a>Rôles RBAC liés à eDiscovery

Le tableau suivant répertorie les rôles RBAC liés à la découverte électronique dans le centre de sécurité & conformité et indique les groupes de rôles intégrés auxquels chaque rôle est affecté par défaut.
  
|**Role**|**Administrateur de conformité**|**Administrateur de & du gestionnaire eDiscovery**|**Gestion de l'organisation**|**Relecteur**|
|:-----|:-----:|:-----:|:-----:|:-----:|
|Gestion des cas <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Communication <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Recherche de conformité <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Custodian <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Exporter <br/> | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Suspension <br/>  |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |
|Aperçu <br/>  | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> | <br/> |
|Révision <br/>  | <br/> |![Coche](../media/checkmark.png) <br/> | <br/> |![Coche](../media/checkmark.png) <br/> |
|Déchiffrement RMS <br/>  ||![Coche](../media/checkmark.png) <br/> |||
|Recherche et purge <br/> | <br/> | <br/> |![Coche](../media/checkmark.png)           <br/> | <br/> |
||||
  
Les sections suivantes décrivent chacun des rôles RBAC liés à la découverte électronique figurant dans le tableau précédent.

### <a name="case-management"></a>Gestion des cas

Ce rôle permet aux utilisateurs de créer, de modifier, de supprimer et de contrôler l’accès à des cas de découverte électronique de base et de découverte électronique avancée dans le centre de conformité & Compliance Center. Comme expliqué précédemment, un utilisateur doit se voir attribuer le rôle de gestion des cas avant de pouvoir utiliser l’applet de commande **Add-eDiscoveryCaseAdmin** pour en faire un administrateur eDiscovery.

Pour plus d’informations, voir :

- [Prise en main de la découverte électronique de base](get-started-core-ediscovery.md)

- [Prise en main Advanced eDiscovery](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Communication

Ce rôle permet aux utilisateurs de gérer toutes les communications avec les dépositaires identifiés dans un cas avancé de découverte électronique. Il s’agit notamment de la création de notifications de blocage, d’attente de rappels et d’escalades à la direction. L’utilisateur peut également suivre les notifications de conservation des dépositaires et gérer l’accès au portail des dépositaires qui est utilisé par chaque dépositaire pour suivre les communications dans les cas où ils ont été identifiés en tant que dépositaire.

Pour plus d’informations, consultez la rubrique [utilisation des communications dans Advanced eDiscovery](managing-custodian-communications.md).

### <a name="compliance-search"></a>Recherche de conformité

Ce rôle permet aux utilisateurs d’exécuter l’outil de recherche de contenu dans le centre de conformité & de sécurité pour rechercher des boîtes aux lettres et des dossiers publics, des sites SharePoint Online, des sites OneDrive entreprise, des conversations Skype entreprise, des groupes Microsoft 365 et Microsoft Teams, ainsi que des groupes Yammer. Ce rôle permet à un utilisateur d’obtenir une estimation des résultats de la recherche et de créer des rapports d’exportation, mais des rôles supplémentaires sont nécessaires pour lancer des actions de recherche de contenu telles que l’aperçu, l’exportation ou la suppression de résultats de recherche.

Les utilisateurs auxquels le rôle de recherche de conformité est attribué mais qui n’ont pas le rôle Aperçu peuvent prévisualiser les résultats d’une recherche dans laquelle l’action d’aperçu a été initiée par un utilisateur auquel le rôle aperçu a été attribué. L’utilisateur sans rôle d’aperçu peut prévisualiser les résultats pendant deux semaines après la création de l’action d’évaluation initiale.

De même, les utilisateurs auxquels le rôle de recherche de conformité est attribué mais qui n’ont pas le rôle d’exportation peuvent télécharger les résultats d’une recherche dans laquelle l’action d’exportation a été initiée par un utilisateur auquel le rôle d’exportation est attribué. L’utilisateur sans rôle d’exportation peut télécharger les résultats d’une recherche jusqu’à deux semaines après la création de l’action d’exportation initiale. Après cela, ils ne peuvent pas télécharger les résultats, à moins qu’un utilisateur disposant du rôle d’exportation ne redémarre l’exportation.

Pour plus d’informations, consultez la rubrique [recherche de contenu dans Office 365](content-search.md).

### <a name="custodian"></a>Custodian

Ce rôle permet aux utilisateurs d’identifier et de gérer des dépositaires pour des cas avancés de découverte électronique et d’utiliser les informations d’Azure Active Directory et d’autres sources pour rechercher des sources de données associées à des dépositaires. L’utilisateur peut associer d’autres sources de données telles que des boîtes aux lettres, des sites SharePoint et des responsables de dépositaires dans un cas. L’utilisateur peut également placer un blocage légal sur les sources de données associées aux dépositaires pour conserver le contenu dans le contexte d’un cas.

Pour plus d’informations, consultez la rubrique [utiliser des dépositaires dans Advanced eDiscovery](managing-custodians.md).

### <a name="export"></a>Exporter

Le rôle permet aux utilisateurs d’exporter les résultats d’une recherche de contenu sur un ordinateur local. Elle leur permet également de préparer des résultats de recherche pour analyse dans Advanced eDiscovery.

Pour plus d’informations sur l’exportation des résultats de recherche, voir [Export Search Results from Security & Compliance Center](export-search-results.md).

### <a name="hold"></a>Suspension

Ce rôle permet aux utilisateurs de placer le contenu en conservation dans les boîtes aux lettres, les dossiers publics, les sites, les conversations Skype entreprise et les groupes Microsoft 365. Lorsque le contenu est en attente, les propriétaires de contenu peuvent toujours modifier ou supprimer le contenu d’origine, mais le contenu sera conservé jusqu’à la suppression ou jusqu’à l’expiration de la mise en attente.

Pour plus d’informations sur les suspensions, voir :

- [Créer une conservation dans la découverte électronique centrale](create-ediscovery-holds.md) 

- [Création d’une conservation dans Advanced eDiscovery](add-custodians-to-case.md#step-4-place-custodians-on-hold)

### <a name="preview"></a>Aperçu

Ce rôle permet aux utilisateurs d’afficher la liste des éléments renvoyés à partir d’une recherche de contenu. Les utilisateurs peuvent également ouvrir et afficher chaque élément de la liste pour afficher son contenu.

### <a name="review"></a>Révision

Ce rôle permet aux utilisateurs d’accéder aux données de cas dans [Advanced eDiscovery (standard)](office-365-advanced-ediscovery.md) (également appelé *Advanced eDiscovery v1*). Le principal objectif de ce rôle est de permettre aux utilisateurs d’accéder à Advanced eDiscovery (classique). Les utilisateurs auxquels ce rôle est attribué peuvent afficher et ouvrir la liste des incidents sur la page de **découverte électronique** dans le centre de sécurité & conformité dont ils sont membres. Une fois que l’utilisateur accède à un cas dans le centre de sécurité & conformité, il peut sélectionner **basculer vers Advanced eDiscovery** pour accéder aux données de cas et les analyser dans Advanced eDiscovery (classique). Ce rôle ne permet pas à l’utilisateur d’afficher un aperçu des résultats d’une recherche de contenu associée au cas ou d’effectuer d’autres tâches de recherche de contenu ou de gestion de cas.

> [!NOTE]
> Pour l’instant, les utilisateurs auxquels le rôle de révision (ou membre du groupe de rôles réviseur) est affecté ne peuvent pas accéder aux données dans [Advanced eDiscovery dans Microsoft 365](overview-ediscovery-20.md) (également appelé *Advanced eDiscovery v 2.0*). Pour ajouter des membres à un cas dans Advanced eDiscovery v 2.0 afin qu’ils puissent consulter les données des cas, un utilisateur doit être membre du groupe de rôles gestionnaire eDiscovery.

### <a name="rms-decrypt"></a>Déchiffrement RMS

Ce rôle permet aux utilisateurs d’afficher les messages électroniques protégés par des droits lors de l’aperçu des résultats de recherche et d’exporter les messages électroniques protégés par des droits. Ce rôle permet également aux utilisateurs d’afficher (et d’exporter) un fichier chiffré avec une [technologie de chiffrement Microsoft](encryption.md) lorsque le fichier chiffré est joint à un message électronique inclus dans les résultats d’une recherche de découverte électronique. De plus, ce rôle permet aux utilisateurs de passer en revue et d’interroger des pièces jointes chiffrées ajoutées à un jeu de réviseur dans Advanced eDiscovery. Pour plus d’informations sur le déchiffrement dans eDiscovery, consultez la rubrique [déchiffrement dans les outils eDiscovery de Microsoft 365](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Recherche et purge

Ce rôle permet aux utilisateurs de procéder à la suppression en bloc des données correspondant aux critères d’une recherche de contenu. Pour plus d’informations, consultez [la rubrique Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).

## <a name="more-information"></a>Plus d’informations

- **Pourquoi créer un administrateur de découverte électronique ?** Comme indiqué précédemment, un administrateur de découverte électronique est membre du groupe de rôles de gestionnaire de découverte électronique, qui peut afficher tous les cas de découverte électronique, et y accéder, de votre organisation. Cette capacité d’accès à tous les cas de découverte électronique a deux objectifs importants :

  - Si une personne qui est le seul membre d’un cas de découverte électronique quitte votre organisation, personne (y compris les membres du groupe de rôles de gestion de l’organisation ou un autre membre du groupe de rôles de gestionnaire de découverte électronique) ne peut accéder à ce cas, car personne n’en est alors membre. Dans ce cas, il n’y aurait aucun moyen d’accéder aux données dans le cas. Toutefois, étant donné qu’un administrateur de découverte électronique peut accéder à tous les cas eDiscovery au sein de l’organisation, il peut afficher le cas et s’ajouter eux-mêmes ou un autre gestionnaire eDiscovery en tant que membre du cas.

  - Étant donné qu’un administrateur eDiscovery peut consulter et accéder à tous les cas de découverte électronique de base et de découverte électronique avancée, il peut auditer et superviser tous les cas et les recherches de conformité associées. Cela peut vous aider à éviter toute utilisation abusive de recherches de conformité ou de cas de découverte électronique. Étant donné que les administrateurs eDiscovery peuvent accéder à des informations potentiellement sensibles dans les résultats d’une recherche de conformité, vous devez limiter le nombre de personnes qui sont des administrateurs eDiscovery.

- **Puis-je ajouter un groupe en tant que membre du groupe de rôles gestionnaire eDiscovery ?** Comme expliqué précédemment, vous pouvez ajouter un groupe de sécurité à extension messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles gestionnaire de découverte électronique à l’aide de la cmdlet **Add-RoleGroupMember** dans Security & PowerShell Center. Par exemple, vous pouvez exécuter la commande suivante pour ajouter un groupe de sécurité à extension messagerie au groupe de rôles gestionnaire eDiscovery. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Les groupes de distribution Exchange et les groupes Microsoft 365 ne sont pas pris en charge. Vous devez utiliser un groupe de sécurité à extension messagerie, que vous pouvez créer dans Exchange Online PowerShell à l’aide de la `New-DistributionGroup -Type Security` commande. Vous pouvez également créer un groupe de sécurité à extension messagerie (et ajouter des membres) dans le centre d’administration Exchange ou dans le centre d’administration Microsoft 365. La création d’une nouvelle sécurité à extension messagerie peut prendre jusqu’à 60 minutes après sa création pour pouvoir être ajoutée au groupe de rôles gestionnaires eDiscovery. 

    Comme indiqué précédemment, vous ne pouvez pas faire d’un groupe de sécurité à extension messagerie un administrateur de découverte électronique à l’aide de la cmdlet **Add-eDiscoveryCaseAdmin** dans la sécurité & Centre de conformité PowerShell. Vous pouvez uniquement ajouter des utilisateurs individuels en tant qu’administrateurs eDiscovery.

    Vous ne pouvez pas non plus ajouter un groupe de sécurité à extension messagerie en tant que membre d’un cas.
