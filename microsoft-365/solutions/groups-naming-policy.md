---
title: Stratégie de noms de groupes Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
description: Découvrez comment créer une stratégie d’attribution de noms pour les groupes Microsoft 365.
ms.openlocfilehash: acf660375508760bd2e9874a07454709849929b0
ms.sourcegitcommit: 222fb7fe2b26dde3d8591b61cc02113d6135012c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/06/2021
ms.locfileid: "49759823"
---
# <a name="microsoft-365-groups-naming-policy"></a>Stratégie de noms de groupes Microsoft 365

Vous pouvez utiliser une stratégie de noms de groupes pour appliquer une stratégie d’attribution de noms cohérente pour les groupes créés par les utilisateurs de votre organisation. Une stratégie d’attribution de noms peut vous aider, ainsi que vos utilisateurs, à identifier la fonction du groupe, de l’appartenance, de la région géographique ou de la personne qui a créé le groupe. La stratégie d’attribution de noms peut également aider à classer les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les noms de groupe et les alias.

La stratégie d’attribution de noms est appliquée aux groupes créés dans toutes les charges de travail de groupes (comme Outlook, Microsoft Teams, SharePoint, Planificateur, Yammer, etc.). Elle est appliquée à la fois au nom de groupe et à l’alias de groupe. Elle est également appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom du groupe, l’alias, la description ou l’avatar est modifié pour un groupe existant.

> [!TIP]
> Une stratégie de noms de groupes Microsoft 365 s’applique uniquement aux groupes Microsoft 365. Elle ne s’applique pas aux groupes de distribution créés dans Exchange Online. Pour créer une stratégie d’attribution de noms pour les groupes de distribution, voir Créer une stratégie de noms de groupes [de distribution.](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy)

La stratégie de noms de groupes comprend les fonctionnalités suivantes :

- Stratégie de noms de **préfixe-suffixe**: vous pouvez utiliser des préfixes ou des suffixes pour définir la convention d’attribution de noms des groupes (par exemple : « US \_ My Group \_ Engineering »). Les préfixes/suffixes peuvent être des chaînes fixes ou des attributs utilisateur tels que [Service] qui seront remplacés en fonction de l’utilisateur qui crée le groupe.

- **Mots bloqués personnalisés**: vous pouvez télécharger un ensemble de mots bloqués spécifiques à votre organisation qui seraient bloqués dans les groupes créés par les utilisateurs. (Par exemple : « PDG, Paie, RH »).

## <a name="licensing-requirements"></a>Critères de licence

L’utilisation d’une stratégie de noms Azure AD pour les groupes Microsoft 365 nécessite que vous possédiez, mais pas nécessairement attribuer une licence Azure Active Directory Premium P1 ou azure AD Basic EDU pour chaque utilisateur unique (y compris les invités) membre d’un ou plusieurs groupes Microsoft 365.

Cela est également requis pour l’administrateur qui crée la stratégie de noms de groupes.

## <a name="prefix-suffix-naming-policy"></a>Prefix-Suffix d’attribution de noms

Les préfixes et les suffixes peuvent être des chaînes fixes ou des attributs utilisateur.

### <a name="fixed-strings"></a>Chaînes fixes

Vous pouvez utiliser des chaînes courtes qui peuvent vous aider à différencier les groupes dans la liste d’erreurs d’erreur et la navigation gauche des charges de travail de groupe. Certains des suffixes de préfixe courants sont des mots clés tels que « Grp Name » (nom grp), « Name » \_ (nom), « Name » \# \_ (nom)

### <a name="attributes"></a>Attributs

Vous pouvez utiliser des attributs qui peuvent aider à identifier qui a créé le groupe comme [Service] et où il a été créé à partir de [Pays].

Exemples :

- Stratégie = « GRP [GroupName] [Department] »
- Service de l’utilisateur = Ingénierie
- Nom du groupe créé = « GRP My Group Engineering »

Les attributs Azure Active Directory (Azure AD) pris en charge sont [Department], [Company], [Office], [StateOrProvince], [CountryOrRegion] et [Title].

- Les attributs utilisateur non pris en compte sont considérés comme des chaînes fixes, par exemple [postalCode].

- Les attributs d’extension et les attributs personnalisés ne sont pas pris en charge.

Il est recommandé d’utiliser des attributs dont les valeurs sont remplies pour tous les utilisateurs de votre organisation et qui n’utilisent pas d’attributs dont les valeurs sont plus longues.

### <a name="things-to-look-out-for"></a>Éléments à rechercher

- Lors de la création de la stratégie, le nombre total de préfixes et de suffixes est limité à 53 caractères.

- Les préfixes et suffixes peuvent contenir des caractères spéciaux pris en charge dans le nom de groupe et l’alias de groupe. Lorsque les préfixes et suffixes contiennent des caractères spéciaux qui ne sont pas autorisés dans l’alias de groupe, ils sont appliqués uniquement au nom du groupe. Ainsi, dans ce cas, les préfixes et suffixes appliqués au nom de groupe sont différents de ceux appliqués à l’alias de groupe.

  > [!NOTE]
  > Un point (.) ou un trait d’union (-) est autorisé n’importe où dans le nom du groupe, sauf au début ou à la fin du nom. Un trait de soulignement (_) est autorisé n’importe où dans le nom du groupe, y compris au début ou à la fin du nom.

- Si vous utilisez Yammer groupes connectés à Office 365, évitez d’utiliser les caractères suivants dans votre stratégie d’attribution de noms : @, \# , \[ , , \] \<, and \> . Si ces caractères sont dans la stratégie d’attribution de noms, les Yammer utilisateurs ne pourront pas créer de groupes.

> [!Tip]
> - Utilisez des chaînes courtes comme suffixe.
> - Utilisez des attributs avec des valeurs.
> - Ne soyez pas trop créatif, la longueur totale du nom est de 264 caractères au maximum.
> - Téléchargez des mots bloqués spécifiques à votre organisation pour restreindre l’utilisation.

## <a name="custom-blocked-words"></a>Mots bloqués personnalisés

Vous pouvez entrer une liste séparée par des virgules de mots bloqués qui seront bloqués dans les noms de groupe et les alias.

Aucune recherche de sous-chaîne n’est effectuée ; plus précisément, une correspondance exacte entre le nom entré par l’utilisateur et les mots bloqués personnalisés est nécessaire pour déclencher un échec.

**Éléments à rechercher**:

- Les mots bloqués ne sont pas sensibles à la cas.

- Lorsqu’un utilisateur entre un mot bloqué, le client de groupe affiche un message d’erreur avec le mot bloqué.

- Il n’existe aucune restriction de caractère dans les mots bloqués utilisés.

- Il existe une limite de 5 000 mots qui peuvent être définies comme mots bloqués.

## <a name="admin-override"></a>Remplacement par l’administrateur

Certains administrateurs sont exemptés de ces stratégies, sur toutes les charges de travail de groupe et points de terminaison, afin qu’ils peuvent créer des groupes avec ces mots bloqués et avec leurs conventions d’attribution de noms souhaitées. Voici la liste des rôles d’administrateur exemptés de la stratégie de noms de groupes.

- Administrateur global

- Support partenaire de niveau 1

- Support partenaire de niveau 2

- Administrateur de compte d’utilisateur

## <a name="how-to-set-up-the-naming-policy"></a>Comment configurer la stratégie d’attribution de noms

Pour configurer une stratégie d’attribution de noms :

1. Dans [Azure Active Directory, sous](https://aad.portal.azure.com) **Gérer,** cliquez sur **Groupes.**
2. Sous **Paramètres,** cliquez sur **Stratégie d’attribution de noms.**
3. Sélectionnez **l’onglet Stratégie de noms de** groupes.
4. Sous **Stratégie actuelle,** choisissez si vous souhaitez exiger un préfixe ou un suffixe ou les deux, puis cochez les cases appropriées.
5. Choisissez entre **Attribut et** **Chaîne** pour chaque ligne, puis spécifiez l’attribut ou la chaîne.
6. Lorsque vous avez ajouté les préfixes et les suffixes dont vous avez besoin, cliquez sur **Enregistrer**.

![Capture d’écran des paramètres de stratégie d’attribution de noms de groupes dans Azure Active Directory](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>Rubriques connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](https://go.microsoft.com/fwlink/?linkid=868341)
