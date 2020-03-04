---
title: Utilisation de l’Explorateur de contenu de la classification des données (préversion)
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
search.appverid:
- MOE150
- MET150
description: L’Explorateur de contenu vous permet d’afficher des éléments étiquetés en mode natif.
ms.openlocfilehash: 205ec6b4f2049e18ee95f25505d8a58d7eb7ac77
ms.sourcegitcommit: 9c335d110e0b499501edc8a31b987641819118a1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2020
ms.locfileid: "42409689"
---
# <a name="using-data-classification-content-explorer-preview"></a>Utilisation de l’Explorateur de contenu de la classification des données (préversion)

L’Explorateur de contenu de la classification des données vous permet d’afficher en mode natif les éléments qui ont été synthétisés dans la page vue d’ensemble.

## <a name="prerequisites"></a>Conditions préalables

Chaque compte accédant et utilisant l’Explorateur d’activités doit posséder une licence pour l’un de ces abonnements :

- Microsoft 365 (E5)
- Office 365 (E5)
- Complément Conformité avancée (E5)
- Complément Threat Intelligence avancé (E5)

## <a name="content-explorer"></a>Explorateur de contenu

L’Explorateur de contenu présente un instantané actuel des éléments qui ont une étiquette de confidentialité, une étiquette de rétention ou ont été classés comme un type d’informations sensibles au sein de votre organisation.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Une [stratégie DLP](data-loss-prevention-policies.md) peut contribuer à protéger les informations sensibles, définies selon des **types d’informations sensibles**. Microsoft 365 inclut des [définitions de pour de nombreux types d’informations sensibles courants](what-the-sensitive-information-types-look-for.md) dans de nombreuses régions différentes, prêtes à l’emploi. Par exemple, un numéro de carte bancaire, des numéros de compte bancaire, des numéros d’identification nationaux et des numéros de service Windows Live ID.

### <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Une [étiquette de confidentialité](sensitivity-labels.md) est tout simplement une balise qui indique la valeur de l’élément pour votre organisation. Elle peut être appliquée manuellement ou automatiquement. Une appliquée, elle est incorporée au document et elle le suit où qu’il aille. L’étiquette de confidentialité permet d’appliquer différents comportements de protection, tels que le filigrane ou le chiffrement obligatoires. Lorsque la protection de point de terminaison est activée, vous pouvez même empêcher un élément de quitter votre contrôle organisationnel.

Les étiquettes de confidentialité doivent être activées pour les fichiers stockés dans SharePoint et OneDrive pour que les données correspondantes apparaissent dans la page de classification des données. Pour en savoir plus, consulter [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive (préversion publique)](sensitivity-labels-sharepoint-onedrive-files.md).

### <a name="retention-labels"></a>Étiquettes de rétention

Les [étiquettes de rétention](labels.md) vous permettent de définir la durée de conservation d’un élément étiqueté et les étapes à suivre avant de le supprimer. Elles peuvent être appliquées manuellement ou automatiquement. Elles peuvent jouer un rôle en aidant votre organisation à respecter les exigences légales et réglementaires.

![capture d’écran réduite de l’Explorateur de contenu](../media/data-classification-content-explorer-1.png)

### <a name="permissions"></a>Autorisations

Deux rôles accordent l'accès à l'explorateur de contenu :

- **Visionneuse de liste de l’Explorateur de contenu**: l’appartenance à ce groupe de rôle vous permet d’afficher chaque élément et son emplacement. Le rôle `data classification list viewer` a été pré-attribué à ce groupe de rôles.

- **Visionneuse de contenu de l’Explorateur de contenu** : l’appartenance à ce groupe de rôles vous permet d’afficher le contenu de chaque élément de la liste. Le rôle `data classification content viewer` a été pré-attribué à ce groupe de rôles.

Le compte que vous utilisez pour accéder à l’Explorateur de contenu doit se trouver dans l’un des groupes de rôles ou les deux. Il s’agit de groupes de rôles indépendants qui ne sont pas cumulatifs. Par exemple, si vous voulez accorder à un compte la possibilité d’afficher les éléments et leur emplacement uniquement, attribuez des droits à la visionneuse de liste de l’Explorateur de contenu. Si vous souhaitez que ce même compte puisse également afficher le contenu des éléments de la liste, vous pouvez également octroyer des droits de visionneuse de contenu dans l’Explorateur de contenu.

Vous pouvez également attribuer l’un ou l’autre des rôles (ou les deux) à un groupe de rôles personnalisé afin de personnaliser l’accès à l’Explorateur de contenu.

Un administrateur général, un administrateur de conformité ou un administrateur de données peut attribuer l'appartenance nécessaire au groupe de rôle de la visionneuse de liste de l’explorateur de contenu et de la visionneuse de contenu de l'explorateur de contenu.

### <a name="how-to-use-content-explorer"></a>Utilisation de l’Explorateur de contenu

1. Ouvrez **Centre de conformité Microsoft 365**  > **Classification de données** > **Explorateur de contenu**.
2. Si vous connaissez le nom de l'étiquette ou le type d'informations sensibles, vous pouvez la taper dans la zone de recherche.
3. Vous pouvez également rechercher l'élément en développant le type d'étiquette et en sélectionnant l'étiquette dans la liste, un élément de la partie à l'étiquette de rétention de la liste est affiché ci-dessous.
4. Sélectionnez un emplacement sous **Tous les emplacements** et explorez la structure de dossiers vers l’élément.
5. Double-cliquez pour ouvrir l’élément en mode natif dans l’Explorateur de contenu.

## <a name="see-also"></a>Voir aussi

- [Étiquettes de confidentialité](sensitivity-labels.md)
- [Étiquettes de rétention](labels.md)
- [Éléments recherchés par les types d’informations sensibles](what-the-sensitive-information-types-look-for.md)
- [Vue d’ensemble des stratégies de rétention](retention-policies.md)
- [Vue d’ensemble de la protection contre la perte de données](data-loss-prevention-policies.md)
