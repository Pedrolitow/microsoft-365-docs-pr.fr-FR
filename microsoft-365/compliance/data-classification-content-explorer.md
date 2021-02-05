---
title: Prise en main de l’explorateur de contenu
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MOE150
- MET150
description: L’Explorateur de contenu vous permet d’afficher des éléments étiquetés en mode natif.
ms.openlocfilehash: 19ad68d3c32046754e366919e8c4e66336945624
ms.sourcegitcommit: d354727303d9574991b5a0fd298d2c9414e19f6c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2021
ms.locfileid: "50080723"
---
# <a name="get-started-with-content-explorer"></a>Prise en main de l’explorateur de contenu

L’Explorateur de contenu de la classification des données vous permet d’afficher en mode natif les éléments qui ont été synthétisés dans la page vue d’ensemble.

![capture d’écran réduite de l’explorateur de contenu](../media/data-classification-content-explorer-1.png)

## <a name="prerequisites"></a>Conditions préalables

Chaque compte qui accède et utilise la classification de données doit posséder une licence pour l’un des abonnements suivants :

- Microsoft 365 (E5)
- Office 365 (E5)
- Complément Conformité avancée (E5)
- Complément Threat Intelligence avancé (E5)
- Microsoft 365 E5/A5, Protection des informations et gouvernance
- Conformité Microsoft 365 E5/A5


### <a name="permissions"></a>Autorisations

Pour accéder à l’onglet Explorateur de contenu, un compte doit être affecté à une appartenance dans l’un de ces rôles ou groupes de rôles. 

**Groupes de rôles Microsoft 365**

- Administrateur général
- Administrateur de conformité
- Administrateur de sécurité
- Administrateur de conformité des données

> [!IMPORTANT]
> L’appartenance à ces groupes de rôles ne vous permet pas d’afficher la liste des éléments ou le contenu des éléments dans l’explorateur de contenu.

### <a name="required-permissions-to-access-items-in-content-explorer"></a>Autorisations requises pour accéder aux éléments dans l’explorateur de contenu

L’accès à l’explorateur de contenu est fortement restreint, car il vous permet de lire le contenu de fichiers numérisés.

> [!IMPORTANT]
> Ces autorisations remplacent les autorisations attribuées localement aux éléments, ce qui permet d’afficher le contenu. 

Il existe deux rôles qui octroient l’accès à l’Explorateur de contenu et l’accès à celui-ci à l’aide du [Centre de sécurité et de conformité Microsoft](https://protection.office.com/permissions):

- **Visionneuse de liste de l’explorateur de contenu** : l’appartenance à ce groupe de rôle vous permet d’afficher chaque élément et son emplacement dans la liste. Le rôle `data classification list viewer` a été pré-attribué à ce groupe de rôles.

- **Visionneuse de contenu de l’Explorateur de contenu** : l’appartenance à ce groupe de rôles vous permet d’afficher le contenu de chaque élément de la liste. Le rôle `data classification content viewer` a été pré-attribué à ce groupe de rôles.

Le compte que vous utilisez pour accéder à l’Explorateur de contenu doit se trouver dans l’un des groupes de rôles ou les deux. Il s’agit de groupes de rôles indépendants qui ne sont pas cumulatifs. Par exemple, si vous voulez accorder à un compte la possibilité d’afficher les éléments et leur emplacement uniquement, attribuez des droits à la visionneuse de liste de l’Explorateur de contenu. Si vous souhaitez que ce même compte puisse également afficher le contenu des éléments de la liste, vous pouvez également octroyer des droits de visionneuse de contenu dans l’Explorateur de contenu.

Vous pouvez également attribuer l’un ou l’autre des rôles (ou les deux) à un groupe de rôles personnalisé afin de personnaliser l’accès à l’Explorateur de contenu.

Un administrateur général, un administrateur de conformité ou un administrateur de données peut attribuer l'appartenance nécessaire au groupe de rôle de la visionneuse de liste de l’explorateur de contenu et de la visionneuse de contenu de l'explorateur de contenu.

## <a name="content-explorer"></a>Explorateur de contenu

L’Explorateur de contenu présente un instantané actuel des éléments qui ont une étiquette de confidentialité, une étiquette de rétention ou ont été classés comme un type d’informations sensibles au sein de votre organisation.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Une [stratégie DLP](data-loss-prevention-policies.md) peut contribuer à protéger les informations sensibles, définies selon des **types d’informations sensibles**. Microsoft 365 inclut des [définitions pour de nombreux types d’informations sensibles courants](sensitive-information-type-entity-definitions.md) provenant de nombreuses régions différentes qui sont prêtes à l’emploi. Par exemple, un numéro de carte bancaire, des numéros de compte bancaire, des numéros d’identification nationaux et des numéros de service Windows Live ID.

> [!NOTE]
> Actuellement, l’explorateur de contenu n’analyse pas les types d’informations sensibles dans Exchange Online.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Une [étiquette de confidentialité](sensitivity-labels.md) est tout simplement une balise qui indique la valeur de l’élément pour votre organisation. Elle peut être appliquée manuellement ou automatiquement. Une appliquée, elle est incorporée au document et elle le suit où qu’il aille. L’étiquette de confidentialité permet d’appliquer différents comportements de protection, tels que le filigrane ou le chiffrement obligatoires.

Les étiquettes de confidentialité doivent être activées pour les fichiers stockés dans SharePoint et OneDrive pour que les données correspondantes apparaissent dans la page de classification des données. Pour plus d’informations, voir [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

### <a name="retention-labels"></a>Étiquettes de rétention

Les [étiquettes de rétention](retention.md) vous permettent de définir la durée de conservation d’un élément étiqueté et les étapes à suivre avant de le supprimer. Elles peuvent être appliquées manuellement ou automatiquement. Elles peuvent jouer un rôle en aidant votre organisation à respecter les exigences légales et réglementaires.

### <a name="how-to-use-content-explorer"></a>Utilisation de l’Explorateur de contenu

1. Ouvrez **Centre de conformité Microsoft 365**  > **Classification de données** > **Explorateur de contenu**.
2. Si vous connaissez le nom de l’étiquette ou le type d’informations sensibles, vous pouvez le taper dans la zone de filtre.
3. Vous pouvez également rechercher l’élément en développant le type d’étiquette et en sélectionnant l’étiquette dans la liste.
4. Sélectionnez un emplacement sous **Tous les emplacements** et explorez la structure de dossiers vers l’élément.
5. Double-cliquez pour ouvrir l’élément en mode natif dans l’Explorateur de contenu.

### <a name="export"></a>Exporter
Le contrôle des **exportations** crée un fichier .csv qui contient une liste de tout ce qui s’affiche dans le volet **Tous les emplacements**.

![Contrôle des exportations de la classification des données](../media/data_classification_export_control.png)


### <a name="search"></a>Rechercher

Lorsque vous explorez un emplacement, par exemple, un dossier Exchange, ou un site SharePoint ou OneDrive, l’outil de **recherche** s’affiche.

![Outil de recherche dans l’explorateur de contenu](../media/data_classification_search_tool.png)


L’étendue de l’outil de recherche définie ce qui s’affiche dans le volet **Tous les emplacements** et ce que vous pouvez rechercher varie en fonction de l’emplacement sélectionné. 

Lorsque **Exchange** est l’emplacement sélectionné, vous pouvez effectuer une recherche sur l’adresse de messagerie complète de la boîte aux lettres, par exemple `user@domainname.com`.

Lorsque **SharePoint** ou **OneDrive** sont les emplacement sélectionnés, l’outil de recherche s’affiche lorsque vous explorez les noms, les dossiers et les fichiers du site. 

> [!NOTE]
> **OneDrive** Nous avons écouté vos précieux commentaires sur l’intégration de OneDrive pendant notre programme d’évaluation. Sur la base de ces commentaires, la fonctionnalité OneDrive restera en préversion jusqu’à ce que tous les correctifs soient en place. En fonction de votre client, certains utilisateurs peuvent ne pas voir OneDrive comme un emplacement. Nous apprécions votre soutien sans faille sur ce projet.

Vous pouvez effectuer une recherche sur les éléments suivants :


|valeur|exemple  |
|---------|---------|
|nom complet du site    |`https://contoso.onmicrosoft.com/sites/sitename`    |
|nom du dossier racine : obtient tous les sous-dossiers    | `/sites`        |
|nom du fichier    |    `RES_Resume_1234.txt`     |
|texte au début du nom de fichier| `RES`|
|texte après un caractère de soulignement (_) dans le nom de fichier|`Resume` ou `1234`| 
|extension du fichier|`txt`|


## <a name="see-also"></a>Voir aussi

- [En savoir plus sur les étiquettes de niveau de confidentialité](sensitivity-labels.md)
- [En savoir plus sur les stratégies et les balises de rétention](retention.md)
- [Définitions d’entités des types d’informations sensibles.md](sensitive-information-type-entity-definitions.md)
- [Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md)
