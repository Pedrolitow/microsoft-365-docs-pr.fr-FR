---
title: Attribuer des autorisations eDiscovery dans le portail de conformité Microsoft Purview
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: 5b9a067b-9d2e-4aa5-bb33-99d8c0d0b5d7
description: Attribuez les autorisations nécessaires pour effectuer des tâches liées à eDiscovery à l’aide de la portail de conformité Microsoft Purview.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 112109d50f0f7e1f11687a325f8756cf2b355e5c
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419437"
---
# <a name="assign-ediscovery-permissions-in-the-compliance-portal"></a>Attribuer des autorisations eDiscovery dans le portail de conformité

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Si vous souhaitez que les utilisateurs utilisent l’un des [outils liés à eDiscovery](ediscovery.md) dans le portail de conformité Microsoft Purview, vous devez leur attribuer les autorisations appropriées. Pour ce faire, le moyen le plus simple consiste à ajouter à la personne le groupe de **rôles** approprié sur la page Autorisations dans le portail de conformité. Cette rubrique décrit les autorisations requises pour effectuer des tâches eDiscovery.

> [!TIP]
> Vous pouvez afficher vos propres autorisations sur la page de vue d’ensemble d’eDiscovery (Premium) dans le portail de conformité. Vous devez avoir au moins un rôle attribué pour que vos autorisations soient affichées.

Le groupe de rôles eDiscovery principal dans le portail de conformité est appelé **Gestionnaire eDiscovery**. Ce groupe de rôles comprend deux sous-groupes.
  
- **Gestionnaire eDiscovery** : un gestionnaire eDiscovery peut utiliser des outils de recherche eDiscovery pour rechercher des emplacements de contenu dans l’organisation et effectuer diverses actions liées à la recherche, telles que la préversion et l’exportation des résultats de recherche. Les membres peuvent également créer et gérer des cas dans Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium), ajouter et supprimer des membres à un cas, créer des conservations de cas, exécuter des recherches associées à un cas et accéder aux données de cas. Les gestionnaires eDiscovery peuvent uniquement consulter et gérer les incidents qu’ils créent. Ils ne peuvent pas accéder aux cas créés par d’autres gestionnaires eDiscovery, ni les gérer.
  
- **Administrateur eDiscovery** : un administrateur eDiscovery est membre du groupe de rôles gestionnaire eDiscovery et peut effectuer les mêmes tâches liées à la recherche de contenu et à la gestion de cas qu’un gestionnaire eDiscovery. De plus, un administrateur de découverte électronique peut :
  
  - Accédez à tous les cas répertoriés dans les pages **eDiscovery (Standard)** et **eDiscovery (Premium)** dans le portail de conformité.

  - Accéder à des données dans eDiscovery (Premium) pour tout cas au sein de l’organisation.
  
  - Gérer tous les cas eDiscovery après s’être ajouté en tant que membre du cas.
  
  - Supprimez des membres d’un cas eDiscovery. Seul un administrateur eDiscovery peut supprimer des membres d’un cas. Les utilisateurs qui sont membres du sous-groupe eDiscovery Manager ne peuvent pas supprimer de membres d’un cas, même si l’utilisateur a créé le cas.
  
  Pour les raisons pour lesquelles vous souhaiterez peut-être des administrateurs eDiscovery dans votre organisation, consultez [Plus d’informations](#more-information).

> [!NOTE]
> Pour analyser les données d’un utilisateur à l’aide d’eDiscovery (Premium), une licence Office 365 E5 ou Microsoft 365 E5 doit être attribuée à l’utilisateur (le gardien des données). Les utilisateurs disposant d’une licence Office 365 E1 ou Office 365 ou Microsoft 365 E3 peuvent également se faire attribuer une licence de module complémentaire Microsoft 365 E5 Conformité ou Microsoft 365 eDiscovery et Audit. Les administrateurs, les agents de conformité ou le personnel juridique affectés à des cas en tant que membres et qui utilisent eDiscovery (Premium) pour collecter, afficher et analyser des données n’ont pas besoin d’une licence E5. Pour plus d’informations sur les licences eDiscovery (Premium), consultez [Abonnements et licences dans eDiscovery (Premium).](overview-ediscovery-20.md#subscriptions-and-licensing)
  
## <a name="before-you-assign-permissions"></a>Avant d’attribuer des autorisations

- Vous devez être membre du groupe de rôles Gestion de l’organisation ou avoir le rôle Gestion des rôles pour attribuer des autorisations eDiscovery dans le portail de conformité.

- Vous pouvez utiliser l’applet de commande [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) dans security & Compliance Center PowerShell pour ajouter un groupe de sécurité à extension messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles gestionnaire eDiscovery. Toutefois, vous ne pouvez pas ajouter de groupe de sécurité à extension messagerie au sous-groupe Administrateurs eDiscovery. Pour [plus d’informations, consultez Plus d’informations](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>Attribution d’autorisations de eDiscovery

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a> et connectez-vous à l’aide d’un compte qui peut attribuer des autorisations.
  
2. Dans le volet gauche, sélectionnez **Autorisations**.

3. Dans la page **Autorisations & rôles** , sous **Centre de conformité**, cliquez sur **Rôles**.

4. Dans la page **Rôles du Centre de conformité** , sélectionnez **eDiscovery Manager**.
  
5. Dans la page de menu volant **eDiscovery Manager** , effectuez l’une des opérations suivantes en fonction des autorisations eDiscovery que vous souhaitez attribuer.
  
    **Pour faire d’un utilisateur un gestionnaire eDiscovery :** En regard **d’eDiscovery Manager**, **sélectionnez Modifier**. Dans la page de l’Assistant **Choisir le gestionnaire de découverte électronique** , cliquez sur ![Ajouter une icône.](../media/ITPro-EAC-AddIcon.gif) **Ajouter**. Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant que gestionnaire eDiscovery, puis sélectionnez **Ajouter**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**. Ensuite, dans la page de l’Assistant **Modifier choisir le gestionnaire eDiscovery** , **sélectionnez Enregistrer** pour enregistrer les modifications apportées à l’appartenance à eDiscovery Manager.
  
    **Pour faire d’un utilisateur un administrateur eDiscovery :** En regard de **l’administrateur eDiscovery**, **sélectionnez Modifier**. Dans la page **Choisir l’administrateur eDiscovery** , cliquez sur ![Ajouter une icône.](../media/ITPro-EAC-AddIcon.gif) **Ajouter**. Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant **qu’administrateur eDiscovery**, puis  **Ajoutez**. Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**. Ensuite, dans la page de l’Assistant **Édition choisir l’administrateur eDiscovery** , **sélectionnez Enregistrer** pour enregistrer les modifications apportées à l’appartenance à l’administrateur eDiscovery.
  
> [!NOTE]
> Vous pouvez également utiliser l’applet de commande **Add-eDiscoveryCaseAdmin** pour faire d’un utilisateur un administrateur eDiscovery. Toutefois, le rôle Gestion des cas doit être attribué à l’utilisateur avant de pouvoir utiliser cette applet de commande pour en faire un administrateur eDiscovery. Pour plus d’informations, consultez [Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin).
  
Dans la page **Autorisations** du portail de conformité, vous pouvez également attribuer aux utilisateurs des autorisations liées à eDiscovery en les ajoutant aux groupes de rôles Administrateur de conformité, Gestion de l’organisation et Réviseur. Pour obtenir une description des rôles RBAC liés à eDiscovery attribués à chacun de ces groupes de rôles, consultez [rôles RBAC liés à eDiscovery](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>Rôles RBAC liés à eDiscovery

Le tableau suivant répertorie les rôles RBAC liés à eDiscovery dans le portail de conformité et indique les groupes de rôles intégrés auxquels chaque rôle est attribué par défaut.
  
| Rôle | Administrateur de conformité | eDiscovery Manager & Administrator | Gestion de l’organisation | Relecteur |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Gestion des cas <br/> |![Coche.](../media/checkmark.png) <br/> |![Coche.](../media/checkmark.png) <br/> |![Marque de vérification.](../media/checkmark.png) <br/> | <br/> |
|Communication <br/> | <br/> |![Marque de vérification.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Recherche de conformité <br/> |![Coche.](../media/checkmark.png) <br/> |![Coche.](../media/checkmark.png) <br/> |![Coche.](../media/checkmark.png) <br/> | <br/> |
|Consignataire <br/> | <br/> |![Coche.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Exporter <br/> | <br/> |![Coche.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Suspension <br/>  |![Marque de vérification.](../media/checkmark.png) <br/> |![Coche.](../media/checkmark.png) <br/> |![Coche.](../media/checkmark.png) <br/> | <br/> |
|Aperçu <br/>  | <br/> |![Coche.](../media/checkmark.png) <br/> | <br/> | <br/> |
|Révision <br/>  | <br/> |![Coche.](../media/checkmark.png) <br/> | <br/> |![Coche](../media/checkmark.png) <br/> |
|Déchiffrer RMS <br/>  ||![Coche](../media/checkmark.png) <br/> |||
|Rechercher et vider <br/> | <br/> | <br/> |![Coche](../media/checkmark.png)<br/> | <br/> |
||||||
  
Les sections suivantes décrivent chacun des rôles RBAC liés à eDiscovery répertoriés dans le tableau précédent.

### <a name="case-management"></a>Gestion des cas

Ce rôle permet aux utilisateurs de créer, modifier, supprimer et contrôler l’accès aux cas eDiscovery (Standard) et eDiscovery (Premium) dans le portail de conformité. Comme expliqué précédemment, le rôle Gestion des cas doit être attribué à un utilisateur avant de pouvoir utiliser l’applet de commande **Add-eDiscoveryCaseAdmin** pour en faire un administrateur eDiscovery.

Pour plus d’informations, reportez-vous aux rubriques suivantes :

- [Prise en main d’eDiscovery (Standard)](get-started-core-ediscovery.md)

- [Prise en main de la découverte électronique (Premium)](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Communication

Ce rôle permet aux utilisateurs de gérer toutes les communications avec les consignatateurs identifiés dans un cas eDiscovery (Premium). Cela inclut la création de notifications de conservation, de rappels de conservation et d’escalades vers la gestion. L’utilisateur peut également suivre l’accusé de réception des notifications de conservation et gérer l’accès au portail des consignats utilisé par chaque gardien pour suivre les communications pour les cas où ils ont été identifiés en tant que consignat.

Pour plus d’informations, consultez [Work with communications in eDiscovery (Premium).](managing-custodian-communications.md)

### <a name="compliance-search"></a>Recherche de conformité

Ce rôle permet aux utilisateurs d’exécuter l’outil Recherche de contenu dans le portail de conformité pour rechercher des boîtes aux lettres et des dossiers publics, SharePoint sites en ligne, sites OneDrive Entreprise, conversations Skype Entreprise, groupes Microsoft 365 et Microsoft Teams, et groupes Yammer. Ce rôle permet à un utilisateur d’obtenir une estimation des résultats de la recherche et de créer des rapports d’exportation, mais d’autres rôles sont nécessaires pour lancer des actions de recherche de contenu telles que l’aperçu, l’exportation ou la suppression des résultats de recherche.

Dans recherche de contenu et eDiscovery (Standard), les utilisateurs auxquels le rôle Recherche de conformité est attribué mais qui n’ont pas le rôle Aperçu peuvent afficher un aperçu des résultats d’une recherche dans laquelle l’action d’aperçu a été lancée par un utilisateur auquel le rôle Aperçu a été attribué. L’utilisateur sans rôle Aperçu peut afficher un aperçu des résultats jusqu’à deux semaines après la création de l’action de préversion initiale.

De même, les utilisateurs de recherche de contenu et eDiscovery (Standard) qui se voient attribuer le rôle Recherche de conformité mais qui n’ont pas le rôle Exporter peuvent télécharger les résultats d’une recherche dans laquelle l’action d’exportation a été lancée par un utilisateur auquel le rôle d’exportation est attribué. L’utilisateur sans rôle d’exportation peut télécharger les résultats d’une recherche jusqu’à deux semaines après la création de l’action d’exportation initiale. Après cela, ils ne peuvent pas télécharger les résultats, sauf si une personne ayant le rôle Exporter redémarre l’exportation.

La période de grâce de deux semaines pour l’aperçu et l’exportation des résultats de recherche (sans les rôles de recherche et d’exportation correspondants) ne s’applique pas à eDiscovery (Premium). Les rôles d’aperçu et d’exportation doivent être attribués aux utilisateurs pour afficher un aperçu et exporter du contenu dans eDiscovery (Premium).

### <a name="custodian"></a>Consignataire

Ce rôle permet aux utilisateurs d’identifier et de gérer les consignatateurs pour les cas eDiscovery (Premium) et d’utiliser les informations de Azure Active Directory et d’autres sources pour rechercher des sources de données associées aux consignatateurs. L’utilisateur peut associer d’autres sources de données telles que des boîtes aux lettres, des sites SharePoint et des Teams à des consignatateurs dans un cas. L’utilisateur peut également placer une conservation légale sur les sources de données associées aux consignataires pour conserver le contenu dans le contexte d’un cas.

Pour plus d’informations, consultez [Work with custodians in eDiscovery (Premium).](managing-custodians.md)

### <a name="export"></a>Exporter

Le rôle permet aux utilisateurs d’exporter les résultats d’une recherche de contenu vers un ordinateur local. Il leur permet également de préparer les résultats de la recherche pour l’analyse dans eDiscovery (Premium).

Pour plus d’informations sur l’exportation des résultats [de recherche, consultez Exporter les résultats de la recherche à partir de portail de conformité Microsoft Purview](export-search-results.md).

### <a name="hold"></a>Suspension

Ce rôle permet aux utilisateurs de mettre le contenu en attente dans les boîtes aux lettres, les dossiers publics, les sites, les conversations Skype Entreprise et les groupes Microsoft 365. Lorsque le contenu est en attente, les propriétaires de contenu peuvent toujours modifier ou supprimer le contenu d’origine, mais le contenu sera conservé jusqu’à la suppression ou jusqu’à l’expiration de la mise en attente.

Pour plus d’informations sur les conservations, consultez :

- [Créer une conservation dans eDiscovery (Standard)](create-ediscovery-holds.md) 

- [Créer une conservation dans eDiscovery (Premium)](add-custodians-to-case.md)

### <a name="preview"></a>Aperçu

Ce rôle permet aux utilisateurs d’afficher une liste d’éléments qui ont été retournés à partir d’une recherche de contenu. Les utilisateurs peuvent également ouvrir et afficher chaque élément de la liste pour afficher son contenu.

### <a name="review"></a>Révision

Ce rôle permet aux utilisateurs d’accéder aux jeux de révision dans [eDiscovery (Premium).](overview-ediscovery-20.md) Les utilisateurs auxquels ce rôle est attribué peuvent voir et ouvrir la liste des cas dans la page **eDiscovery > Avancé** dans le portail de conformité dont ils sont membres. Une fois que l’utilisateur a accédé à un cas eDiscovery (Premium), il peut sélectionner **Les jeux de révision** pour accéder aux données de cas. Ce rôle ne permet pas à l’utilisateur d’afficher un aperçu des résultats d’une recherche de collection associée au cas ou d’effectuer d’autres tâches de recherche ou de gestion de cas. Les utilisateurs dotés de ce rôle peuvent uniquement accéder aux données d’un ensemble de révisions.

### <a name="rms-decrypt"></a>Déchiffrer RMS

Ce rôle permet aux utilisateurs d’afficher les messages électroniques protégés par des droits lors de l’aperçu des résultats de recherche et d’exporter les messages électroniques protégés par des droits déchiffrés. Ce rôle permet également aux utilisateurs d’afficher (et d’exporter) un fichier chiffré à l’aide d’une [technologie de chiffrement Microsoft](encryption.md) lorsque le fichier chiffré est joint à un message électronique inclus dans les résultats d’une recherche eDiscovery. En outre, ce rôle permet aux utilisateurs d’examiner et d’interroger les pièces jointes chiffrées qui sont ajoutées à un ensemble de révisions dans eDiscovery (Premium). Pour plus d’informations sur le déchiffrement dans eDiscovery, consultez [Déchiffrement dans Microsoft 365 outils eDiscovery](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Rechercher et vider

Ce rôle permet aux utilisateurs d’effectuer la suppression en bloc des données correspondant aux critères d’une recherche de contenu. Pour plus d’informations, consultez [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>Ajout de groupes de rôles en tant que membres de cas eDiscovery

Vous pouvez ajouter des groupes de rôles en tant que membres de cas eDiscovery (Standard) et eDiscovery (Premium) afin que les membres des groupes de rôles puissent accéder aux cas attribués et effectuer des tâches. Les rôles attribués au groupe de rôles définissent ce que les membres du groupe de rôles peuvent faire. Ensuite, l’ajout d’un groupe de rôles en tant que membre du cas permet aux membres d’accéder à ces tâches et d’effectuer ces tâches dans un cas spécifique. Pour plus d’informations sur l’ajout de groupes de rôles en tant que membres de cas, consultez :

- [Prise en main d’eDiscovery (Standard)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

- [Ajouter ou supprimer des membres d’un cas eDiscovery (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Dans cet esprit, il est important de savoir que si un rôle est ajouté ou supprimé d’un groupe de rôles, ce groupe de rôles est automatiquement supprimé en tant que membre de tout cas dont le groupe de rôles est membre. La raison en est que votre organisation ne fournit pas par inadvertance des autorisations supplémentaires aux membres d’un cas. De même, si un groupe de rôles est supprimé, il sera supprimé de tous les cas dont il était membre.

Avant d’ajouter ou de supprimer des rôles à un groupe de rôles qui peut être membre d’un cas eDiscovery, vous pouvez exécuter les commandes suivantes dans [Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) pour obtenir la liste des cas dont le groupe de rôles est membre. Après avoir mis à jour le groupe de rôles, vous rajoutez le groupe de rôles en tant que membre de ces cas.

### <a name="get-a-list-of-ediscovery-standard-cases-a-role-group-is-assigned-to"></a>Obtenir la liste des cas eDiscovery (Standard) auxquels un groupe de rôles est affecté

```powershell
Get-ComplianceCase -RoleGroup "Name of role group"
```

### <a name="get-a-list-of-ediscovery-premium-cases-a-role-group-is-assigned-to"></a>Obtenir la liste des cas eDiscovery (Premium) auxquels un groupe de rôles est affecté

```powershell
Get-ComplianceCase -RoleGroup "Name of role group" -CaseType AdvancedEdiscovery
```

## <a name="more-information"></a>Plus d’informations

- **Pourquoi créer un administrateur de découverte électronique ?** Comme indiqué précédemment, un administrateur de découverte électronique est membre du groupe de rôles de gestionnaire de découverte électronique, qui peut afficher tous les cas de découverte électronique, et y accéder, de votre organisation. Cette capacité d’accès à tous les cas de découverte électronique a deux objectifs importants :

  - Si une personne qui est le seul membre d’un cas de découverte électronique quitte votre organisation, personne (y compris les membres du groupe de rôles de gestion de l’organisation ou un autre membre du groupe de rôles de gestionnaire de découverte électronique) ne peut accéder à ce cas, car personne n’en est alors membre. Dans ce cas, il n’y aurait aucun moyen d’accéder aux données dans le cas. Toutefois, étant donné qu’un administrateur eDiscovery peut accéder à tous les cas eDiscovery de l’organisation, il peut afficher le cas et s’ajouter lui-même ou un autre responsable eDiscovery en tant que membre du cas.

  - Étant donné qu’un administrateur eDiscovery peut afficher et accéder à tous les cas eDiscovery (Standard) et eDiscovery (Premium), il peut auditer et superviser tous les cas et les recherches de conformité associées. Cela peut aider à empêcher toute utilisation abusive des recherches de conformité ou des cas eDiscovery. Étant donné que les administrateurs eDiscovery peuvent accéder aux informations potentiellement sensibles dans les résultats d’une recherche de conformité, vous devez limiter le nombre de personnes qui sont des administrateurs eDiscovery.

- **Puis-je ajouter un groupe en tant que membre du groupe de rôles gestionnaire eDiscovery ?** Comme expliqué précédemment, vous pouvez ajouter un groupe de sécurité à extension messagerie en tant que membre du sous-groupe gestionnaires eDiscovery dans le groupe de rôles eDiscovery Manager à l’aide de l’applet de commande **Add-RoleGroupMember** dans le Centre de sécurité & conformité PowerShell. Par exemple, vous pouvez exécuter la commande suivante pour ajouter un groupe de sécurité à extension messagerie au groupe de rôles eDiscovery Manager. 

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Exchange groupes de distribution et Groupes Microsoft 365 ne sont pas pris en charge. Vous devez utiliser un groupe de sécurité à extension messagerie, que vous pouvez créer dans Exchange Online PowerShell en exécutant `New-DistributionGroup -Type Security`. Vous pouvez également créer un groupe de sécurité à extension messagerie (et ajouter des membres) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a> ou dans le [Centre d'administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). La création d’un groupe de sécurité à extension messagerie peut prendre jusqu’à 60 minutes avant d’être ajouté au groupe de rôles gestionnaires eDiscovery.

    Comme indiqué précédemment, vous ne pouvez pas faire d’un groupe de sécurité à extension messagerie un administrateur eDiscovery à l’aide de l’applet de commande **Add-eDiscoveryCaseAdmin** dans le Centre de sécurité & conformité PowerShell. Vous pouvez uniquement ajouter des utilisateurs individuels en tant qu’administrateurs eDiscovery.

    Vous ne pouvez pas non plus ajouter un groupe de sécurité à extension messagerie en tant que membre d’un cas.
