---
title: Attribuer des autorisations eDiscovery dans le portail de conformité Microsoft Purview
description: Attribuez les autorisations requises pour effectuer des tâches liées à eDiscovery à l’aide de la portail de conformité Microsoft Purview.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
- ediscovery
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkCOMPLIANCE
ms.openlocfilehash: 97f080bf273a0a2e7e8694d7ae4923a32e0c38c7
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68662201"
---
# <a name="assign-ediscovery-permissions-in-the-compliance-portal"></a>Attribuer des autorisations eDiscovery dans le portail de conformité

Si vous souhaitez que les utilisateurs utilisent [l’un des outils liés à la découverte](ediscovery.md) électronique dans le portail de conformité Microsoft Purview, vous devez leur attribuer les autorisations appropriées. Le moyen le plus simple d’attribuer des rôles consiste à ajouter à la personne le groupe de rôles approprié dans la page **Autorisations** du portail de conformité. Cet article décrit les autorisations requises pour effectuer des tâches eDiscovery.

> [!TIP]
> Vous pouvez afficher vos propres autorisations sur la page de vue d’ensemble eDiscovery (Premium) du portail de conformité. Vous devez avoir au moins un rôle attribué pour que vos autorisations s’affichent.

Le groupe de rôles principal lié à eDiscovery dans le portail de conformité est appelé **gestionnaire eDiscovery**. Il existe deux sous-groupes au sein de ce groupe de rôles :
  
- **Gestionnaire eDiscovery** : un gestionnaire eDiscovery peut utiliser les outils de recherche eDiscovery pour rechercher des emplacements de contenu dans l’organisation et effectuer diverses actions liées à la recherche, telles que l’aperçu et l’exportation des résultats de recherche. Les membres peuvent également créer et gérer des cas dans Microsoft Purview eDiscovery (Standard) et Microsoft Purview eDiscovery (Premium), ajouter et supprimer des membres dans un cas, créer des conservations de cas, exécuter des recherches associées à un cas et accéder aux données de cas. Les gestionnaires eDiscovery peuvent uniquement consulter et gérer les incidents qu’ils créent. Ils ne peuvent pas accéder aux cas créés par d’autres gestionnaires eDiscovery, ni les gérer.
  
- **Administrateur eDiscovery** : un administrateur eDiscovery est membre du groupe de rôles Gestionnaire eDiscovery et peut effectuer les mêmes tâches liées à la recherche de contenu et à la gestion des cas qu’un gestionnaire eDiscovery peut effectuer. De plus, un administrateur de découverte électronique peut :
  
  - Accédez à tous les cas répertoriés dans les pages **eDiscovery (Standard)** et **eDiscovery (Premium)** dans le portail de conformité.
  - Accéder à des données dans eDiscovery (Premium) pour tout cas au sein de l’organisation.
  - Gérer tous les cas eDiscovery après s’être ajouté en tant que membre du cas.
  - Supprimer des membres d’un cas eDiscovery. Seul un administrateur eDiscovery peut supprimer des membres d’un cas. Les utilisateurs qui sont membres du sous-groupe eDiscovery Manager ne peuvent pas supprimer des membres d’un cas, même si l’utilisateur a créé le cas.
  
  Pour connaître les raisons pour lesquelles vous souhaitez des administrateurs eDiscovery dans votre organisation, consultez [Plus d’informations](#more-information).

> [!NOTE]
> Pour analyser les données d’un utilisateur à l’aide d’eDiscovery (Premium), l’utilisateur (le dépositaire des données) doit se voir attribuer une licence Office 365 E5 ou Microsoft 365 E5. Les utilisateurs disposant d’une licence Office 365 E1 ou Office 365 ou Microsoft 365 E3 peuvent également se voir attribuer une licence Microsoft 365 E5 Conformité ou microsoft 365 eDiscovery et Audit. Les administrateurs, les responsables de la conformité ou le personnel juridique affectés à des cas en tant que membres et qui utilisent eDiscovery (Premium) pour collecter, afficher et analyser des données n’ont pas besoin d’une licence E5. Pour plus d’informations sur les licences eDiscovery (Premium), consultez [Abonnements et licences dans eDiscovery (Premium)](overview-ediscovery-20.md#subscriptions-and-licensing).
  
[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="before-you-assign-permissions"></a>Avant d’attribuer des autorisations

- Vous devez être membre du groupe de rôles *Gestion de l’organisation* ou attribuer le rôle *Gestion des* rôles pour attribuer des autorisations eDiscovery dans le portail de conformité.

- Vous pouvez utiliser l’applet de commande [Add-RoleGroupMember](/powershell/module/exchange/Add-RoleGroupMember) dans Security & Compliance PowerShell pour ajouter un groupe de sécurité à extension messagerie en tant que membre du sous-groupe *Gestionnaires eDiscovery* dans le groupe de rôles *Gestionnaire eDiscovery* . Toutefois, vous ne pouvez pas ajouter un groupe de sécurité à extension messagerie au sous-groupe *Administrateurs eDiscovery* . Pour plus d’informations, consultez [Plus d’informations](#more-information).
  
## <a name="assign-ediscovery-permissions"></a>Attribution d’autorisations de eDiscovery

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077149" target="_blank">portail de conformité</a> et connectez-vous à l’aide d’un compte qui peut attribuer des autorisations.
2. Dans le volet gauche, sélectionnez **Autorisations**.
3. Dans la page **Autorisations & rôles** , sous **Solutions Microsoft Purview**, sélectionnez **Rôles**.

   Pour accéder directement à cette page, utilisez <https://compliance.microsoft.com/compliancecenterpermissions>.

4. Dans la page **Groupes de rôles pour les solutions Microsoft Purview** , sélectionnez **Gestionnaire eDiscovery**.
5. Dans le volet volant **du Gestionnaire eDiscovery** , effectuez l’une des opérations suivantes en fonction des autorisations eDiscovery que vous souhaitez attribuer.
  
    **Pour faire d’un utilisateur un gestionnaire eDiscovery :**
    - En regard **d’eDiscovery Manager**, sélectionnez **Modifier**.
    - Dans la page De l’Assistant **Choisir eDiscovery Manager** , sélectionnez ![Ajouter une icône.](../media/ITPro-EAC-AddIcon.gif) **Ajouter**. 
    - Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant que gestionnaire eDiscovery, puis sélectionnez **Ajouter**. 
    - Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**.
    - Dans la page Modification de l’Assistant **Choisir eDiscovery Manager** , sélectionnez **Enregistrer** pour enregistrer les modifications apportées à l’appartenance à eDiscovery Manager.
  
    **Pour faire d’un utilisateur un administrateur eDiscovery :**
    - En regard de **Administrateur eDiscovery**, sélectionnez **Modifier**.
    - Dans la page **Choisir un administrateur eDiscovery** , sélectionnez ![Ajouter une icône.](../media/ITPro-EAC-AddIcon.gif) **Ajouter**.
    - Sélectionnez l’utilisateur (ou les utilisateurs) que vous souhaitez ajouter en tant **qu’administrateur eDiscovery**, puis  **Ajouter**. 
    - Lorsque vous avez terminé d’ajouter des utilisateurs, sélectionnez **Terminé**.
    - Dans la page Modification de l’Assistant **Choisir un administrateur eDiscovery** , sélectionnez **Enregistrer** pour enregistrer les modifications apportées à l’appartenance de l’administrateur eDiscovery.
  
> [!NOTE]
> Vous pouvez également utiliser l’applet **de commande Add-eDiscoveryCaseAdmin** pour faire d’un utilisateur un administrateur eDiscovery. Toutefois, le rôle *Gestion des* incidents doit être attribué à l’utilisateur avant de pouvoir utiliser cette applet de commande pour en faire un administrateur eDiscovery. Pour plus d’informations, consultez [Add-eDiscoveryCaseAdmin](/powershell/module/exchange/add-ediscoverycaseadmin).
  
Dans la page **Autorisations** du portail de conformité, vous pouvez également attribuer aux utilisateurs des autorisations liées à eDiscovery en les ajoutant aux groupes de rôles *Administrateur de conformité*, *Gestion de l’organisation* et *Réviseur* . Pour obtenir une description des rôles de contrôle d’accès en fonction du rôle liés à eDiscovery attribués à chacun de ces groupes de rôles, consultez [Rôles de contrôle d’accès en fonction du rôle liés à eDiscovery](#rbac-roles-related-to-ediscovery).

## <a name="rbac-roles-related-to-ediscovery"></a>Rôles RBAC liés à eDiscovery

Le tableau suivant répertorie les rôles de contrôle d’accès en fonction du rôle liés à eDiscovery dans le portail de conformité et indique les groupes de rôles intégrés auxquels chaque rôle est attribué par défaut.
  
| Rôle | Administrateur de conformité | Administrateur & gestionnaire eDiscovery | Gestion de l’organisation | Relecteur |
|:-----|:-----:|:-----:|:-----:|:-----:|
|Gestion des cas|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Marque de vérification.](../media/checkmark.png)||
|Communication||![Coche.](../media/checkmark.png)|||
|Recherche de conformité|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)|![Coche.](../media/checkmark.png)||
|Consignataire||![Coche.](../media/checkmark.png)|||
|Exporter||![Coche.](../media/checkmark.png)|||
|Suspension|![Coche.](../media/checkmark.png)|![Marque de vérification.](../media/checkmark.png)|![Coche.](../media/checkmark.png)||
|Gérer les étiquettes d’ensemble de révision| |![Marque de vérification.](../media/checkmark.png)|||
|Aperçu||![Coche.](../media/checkmark.png)|||
|Révision||![Marque de vérification.](../media/checkmark.png)||![Coche](../media/checkmark.png)|
|Déchiffrement RMS||![Coche](../media/checkmark.png)|||
|Rechercher et vider|||![Coche](../media/checkmark.png)||
  
Les sections suivantes décrivent chacun des rôles de contrôle d’accès en fonction du rôle liés à eDiscovery répertoriés dans le tableau précédent.

### <a name="case-management"></a>Gestion des cas

Ce rôle permet aux utilisateurs de créer, modifier, supprimer et contrôler l’accès aux cas eDiscovery (Standard) et eDiscovery (Premium) dans le portail de conformité. Comme expliqué précédemment, le rôle *Gestion des* cas doit être attribué à un utilisateur avant de pouvoir utiliser l’applet **de commande Add-eDiscoveryCaseAdmin** pour en faire un administrateur eDiscovery.

Pour plus d’informations, consultez l’article suivant :

- [Prise en main d’eDiscovery (Standard)](get-started-core-ediscovery.md)
- [Prise en main de la découverte électronique (Premium)](get-started-with-advanced-ediscovery.md)

### <a name="communication"></a>Communication

Ce rôle permet aux utilisateurs de gérer toutes les communications avec les consignataires identifiés dans un cas eDiscovery (Premium). Cela inclut la création de notifications de mise en attente, de rappels de suspension et d’escalades vers la gestion. L’utilisateur peut également suivre l’accusé de réception des notifications de conservation et gérer l’accès au portail du consignataire utilisé par chaque dépositaire pour suivre les communications dans les cas où il a été identifié en tant que dépositaire.

Pour plus d’informations, consultez [Utiliser des communications dans eDiscovery (Premium).](managing-custodian-communications.md)

### <a name="compliance-search"></a>Recherche de conformité

Ce rôle permet aux utilisateurs d’exécuter l’outil De recherche de contenu dans le portail de conformité pour rechercher des boîtes aux lettres et des dossiers publics, des sites SharePoint Online, des sites OneDrive Entreprise, des conversations Skype Entreprise, des groupes Microsoft 365 et Microsoft Teams et des groupes Yammer. Ce rôle permet à un utilisateur d’obtenir une estimation des résultats de la recherche et de créer des rapports d’exportation, mais d’autres rôles sont nécessaires pour lancer des actions de recherche de contenu telles que l’aperçu, l’exportation ou la suppression des résultats de recherche.

Dans Recherche de contenu et eDiscovery (Standard), les utilisateurs auxquels le rôle *Recherche de conformité* n’est pas  attribué peuvent afficher un aperçu des résultats d’une recherche dans laquelle l’action d’aperçu a été lancée par un utilisateur auquel le rôle *Aperçu* est attribué. L’utilisateur qui n’a pas le rôle *Préversion* peut afficher un aperçu des résultats pendant deux semaines au maximum après la création de l’action d’aperçu initiale.

De même, les utilisateurs de recherche de contenu et d’eDiscovery (Standard) auxquels le rôle *Recherche de conformité* est attribué, mais qui n’ont pas le rôle *Exporter* , peuvent télécharger les résultats d’une recherche dans laquelle l’action d’exportation a été lancée par un utilisateur auquel le rôle *Exporter* est attribué. L’utilisateur sans le rôle *Exporter* peut télécharger les résultats d’une recherche pendant jusqu’à deux semaines après la création de l’action d’exportation initiale. Après cela, ils ne peuvent pas télécharger les résultats, sauf si une personne disposant du rôle *Exporter* redémarre l’exportation.

La période de grâce de deux semaines pour l’aperçu et l’exportation des résultats de recherche (sans les rôles de recherche et d’exportation correspondants) ne s’applique pas à eDiscovery (Premium). Les rôles *Aperçu* et *Exportation* doivent être attribués aux utilisateurs pour afficher un aperçu et exporter du contenu dans eDiscovery (Premium).

### <a name="custodian"></a>Consignataire

Ce rôle permet aux utilisateurs d’identifier et de gérer les consignataires pour les cas eDiscovery (Premium) et d’utiliser les informations d’Azure Active Directory et d’autres sources pour rechercher les sources de données associées aux consignataires. L’utilisateur peut associer d’autres sources de données, telles que des boîtes aux lettres, des sites SharePoint et Teams, à des consignataires dans un cas. L’utilisateur peut également placer une conservation légale sur les sources de données associées aux consignataires pour préserver le contenu dans le contexte d’un cas.

Pour plus d’informations, consultez [Utiliser des consignataires dans eDiscovery (Premium).](managing-custodians.md)

### <a name="export"></a>Exporter

Le rôle permet aux utilisateurs d’exporter les résultats d’une recherche de contenu vers un ordinateur local. Il leur permet également de préparer les résultats de la recherche pour l’analyse dans eDiscovery (Premium).

Pour plus d’informations sur l’exportation des résultats de recherche, consultez [Exporter les résultats de la recherche à partir de portail de conformité Microsoft Purview](export-search-results.md).

### <a name="hold"></a>Suspension

Ce rôle permet aux utilisateurs de mettre du contenu en attente dans des boîtes aux lettres, des dossiers publics, des sites, des conversations Skype Entreprise et des groupes Microsoft 365. Lorsque le contenu est en attente, les propriétaires de contenu peuvent toujours modifier ou supprimer le contenu d’origine, mais le contenu sera conservé jusqu’à la suppression ou jusqu’à l’expiration de la mise en attente.

Pour plus d’informations sur les conservations, consultez :

- [Créer une conservation dans eDiscovery (Standard)](create-ediscovery-holds.md) 
- [Créer une conservation dans eDiscovery (Premium)](add-custodians-to-case.md)

### <a name="manage-review-set-tags"></a>Gérer les étiquettes d’ensemble de révision

Ce rôle permet aux utilisateurs de créer, de modifier et de supprimer des balises de jeu de révision pour les cas auxquels ils peuvent accéder. Les utilisateurs auront au moins besoin du rôle *Révision* et de ce rôle pour [gérer les étiquettes](/microsoft-365/compliance/tagging-documents#creating-and-applying-tags) pendant les révisions.

### <a name="preview"></a>Aperçu

Ce rôle permet aux utilisateurs d’afficher une liste d’éléments retournés à partir d’une recherche de contenu. Les utilisateurs peuvent également ouvrir et afficher chaque élément de la liste pour afficher son contenu.

### <a name="review"></a>Révision

Ce rôle permet aux utilisateurs d’accéder aux jeux de révision dans [eDiscovery (Premium).](overview-ediscovery-20.md) Les utilisateurs auxquels ce rôle est attribué peuvent voir et ouvrir la liste des cas dans la page **eDiscovery > Avancé** du portail de conformité dont ils sont membres. Une fois que l’utilisateur a accédé à un cas eDiscovery (Premium), il peut sélectionner **Vérifier les jeux** pour accéder aux données de cas. Ce rôle ne permet pas à l’utilisateur d’afficher un aperçu des résultats d’une recherche de collection associée au cas ou d’effectuer d’autres tâches de recherche ou de gestion de cas. Les utilisateurs disposant de ce rôle peuvent uniquement accéder aux données d’un jeu de révision.

### <a name="rms-decrypt"></a>Déchiffrement RMS

Ce rôle permet aux utilisateurs d’afficher les messages électroniques protégés par des droits lorsqu’ils affichent un aperçu des résultats de recherche et d’exporter des messages électroniques protégés par des droits déchiffrés. Ce rôle permet également aux utilisateurs d’afficher (et d’exporter) un fichier chiffré avec une [technologie de chiffrement Microsoft](encryption.md) lorsque le fichier chiffré est joint à un message électronique inclus dans les résultats d’une recherche eDiscovery. En outre, ce rôle permet aux utilisateurs d’examiner et d’interroger les pièces jointes chiffrées qui sont ajoutées à un jeu de révision dans eDiscovery (Premium). Pour plus d’informations sur le déchiffrement dans eDiscovery, consultez [Déchiffrement dans les outils eDiscovery de Microsoft 365](ediscovery-decryption.md).

### <a name="search-and-purge"></a>Rechercher et vider

Ce rôle permet aux utilisateurs d’effectuer une suppression en bloc des données correspondant aux critères d’une recherche de contenu. Pour plus d’informations, consultez [Rechercher et supprimer des messages électroniques dans votre organisation](search-for-and-delete-messages-in-your-organization.md).

## <a name="adding-role-groups-as-members-of-ediscovery-cases"></a>Ajout de groupes de rôles en tant que membres des cas eDiscovery

Vous pouvez ajouter des groupes de rôles en tant que membres des cas eDiscovery (Standard) et eDiscovery (Premium) afin que les membres des groupes de rôles puissent accéder aux tâches et les effectuer dans les cas attribués. Les rôles attribués au groupe de rôles définissent ce que les membres du groupe de rôles peuvent faire. Ensuite, l’ajout d’un groupe de rôles en tant que membre du cas permet aux membres d’accéder à ces tâches et d’effectuer ces tâches dans un cas spécifique. Pour plus d’informations sur l’ajout de groupes de rôles en tant que membres de cas, consultez :

- [Prise en main d’eDiscovery (Standard)](get-started-core-ediscovery.md#step-4-optional-add-members-to-a-ediscovery-standard-case)

- [Ajouter ou supprimer des membres d’un cas eDiscovery (Premium)](add-or-remove-members-from-a-case-in-advanced-ediscovery.md)

Avec cette exigence à l’esprit, il est important de savoir que si un rôle est ajouté ou supprimé d’un groupe de rôles, ce groupe de rôles sera automatiquement supprimé en tant que membre de tout cas dont le groupe de rôles est membre. La raison en est de protéger votre organisation contre l’octroi par inadvertance d’autorisations supplémentaires aux membres d’un cas. De même, si un groupe de rôles est supprimé, il sera supprimé de tous les cas dont il était membre.

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
  - Étant donné qu’un administrateur eDiscovery peut afficher et accéder à tous les cas eDiscovery (Standard) et eDiscovery (Premium), il peut auditer et superviser tous les cas et les recherches de conformité associées. Cette fonctionnalité peut aider à empêcher toute utilisation incorrecte des recherches de conformité ou des cas d’eDiscovery. Et étant donné que les administrateurs eDiscovery peuvent accéder aux informations potentiellement sensibles dans les résultats d’une recherche de conformité, vous devez limiter le nombre de personnes qui sont des administrateurs eDiscovery.

- **Puis-je ajouter un groupe en tant que membre du groupe de rôles Gestionnaire eDiscovery ?** Comme expliqué précédemment, vous pouvez ajouter un groupe de sécurité à extension messagerie en tant que membre du sous-groupe Gestionnaires *eDiscovery* dans le groupe de rôles Gestionnaire de découverte électronique à l’aide de l’applet de commande **Add-RoleGroupMember** dans Security & Compliance PowerShell. Par exemple, vous pouvez exécuter la commande suivante pour ajouter un groupe de sécurité à extension messagerie au groupe de rôles *Gestionnaire eDiscovery* .

  ```powershell
  Add-RoleGroupMember "eDiscovery Manager" -Member <name of security group>
  ```

    Les groupes de distribution Exchange et les Groupes Microsoft 365 ne sont pas pris en charge. Vous devez utiliser un groupe de sécurité à extension messagerie, que vous pouvez créer dans Exchange Online PowerShell en exécutant `New-DistributionGroup -Type Security`. Vous pouvez également créer un groupe de sécurité à extension messagerie (et ajouter des membres) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a> ou dans le [Centre d'administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=2024339). Jusqu’à 60 minutes peuvent être nécessaires après sa création pour qu’un nouveau groupe de sécurité à extension messagerie puisse être ajouté au groupe de rôles Gestionnaires eDiscovery.

    En outre, comme indiqué précédemment, vous ne pouvez pas faire d’un groupe de sécurité à extension messagerie un administrateur eDiscovery à l’aide de l’applet **de commande Add-eDiscoveryCaseAdmin** dans Security & Compliance PowerShell. Vous pouvez uniquement ajouter des utilisateurs individuels en tant qu’administrateurs eDiscovery.

    Vous ne pouvez pas non plus ajouter un groupe de sécurité à extension messagerie en tant que membre d’un cas.
