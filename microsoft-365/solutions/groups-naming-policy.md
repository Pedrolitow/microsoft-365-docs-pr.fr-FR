---
title: Microsoft 365 de noms de groupes
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
recommendations: false
description: Découvrez comment créer une stratégie d’attribution de noms pour Microsoft 365 groupes.
ms.openlocfilehash: 9fb75feb255ee6d58313f4cfaf3486c4a8cd63b4
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60213408"
---
# <a name="microsoft-365-groups-naming-policy"></a>Microsoft 365 de noms de groupes

Vous pouvez utiliser une stratégie de noms de groupes pour appliquer une stratégie d’attribution de noms cohérente pour les groupes créés par les utilisateurs de votre organisation. Une stratégie d’attribution de noms peut vous aider, ainsi que vos utilisateurs, à identifier la fonction du groupe, l’appartenance, la région géographique ou la personne qui a créé le groupe. La stratégie d’attribution de noms peut également aider à classer les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les noms de groupe et les alias.

La stratégie d’attribution de noms s’applique aux groupes créés dans toutes les charges de travail de groupes (par exemple, Outlook, Microsoft Teams, SharePoint, Planificateur, Yammer, etc.). Elle est appliquée à la fois au nom de groupe et à l’alias de groupe. Elle est également appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom du groupe, l’alias, la description ou l’avatar est modifié pour un groupe existant.

> [!TIP]
> Une stratégie Microsoft 365 noms de groupes s’applique uniquement Microsoft 365 groupes. Elle ne s’applique pas aux groupes de distribution créés dans Exchange Online. Pour créer une stratégie d’attribution de noms pour les groupes de distribution, voir Créer une stratégie de noms de groupes [de distribution.](/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy)

La stratégie de noms de groupes comprend les fonctionnalités suivantes :

- Stratégie de noms de **préfixe-suffixe**: vous pouvez utiliser des préfixes ou des suffixes pour définir la convention d’attribution de noms des groupes (par exemple : « US \_ My Group \_ Engineering »). Les préfixes/suffixes peuvent être des chaînes fixes ou des attributs utilisateur tels que [Service] qui seront remplacés en fonction de l’utilisateur qui crée le groupe.

- **Mots bloqués personnalisés**: vous pouvez télécharger un ensemble de mots bloqués spécifiques à votre organisation qui seraient bloqués dans les groupes créés par les utilisateurs. (Par exemple : « PDG, Paie, RH »).

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

L’utilisation d’une stratégie de noms Azure AD pour les groupes Microsoft 365 nécessite que vous possédiez, mais pas nécessairement attribuer une licence Azure Active Directory Premium P1 ou azure AD Basic EDU pour chaque utilisateur unique (y compris les invités) membre d’un ou de plusieurs groupes Microsoft 365.

Cela est également requis pour l’administrateur qui crée la stratégie de noms de groupes.

## <a name="prefix-suffix-naming-policy"></a>Prefix-Suffix d’attribution de noms

Les préfixes et les suffixes peuvent être des chaînes fixes ou des attributs utilisateur.

### <a name="fixed-strings"></a>Chaînes fixes

Vous pouvez utiliser des chaînes courtes qui peuvent vous aider à différencier les groupes dans la liste d’erreurs d’erreur et la navigation gauche des charges de travail de groupe. Certains des suffixes de préfixe courants sont des mots clés tels que « Grp Name » (nom grp), « Name » \_ (nom), « Name » \# \_ (nom)

### <a name="attributes"></a>Attributs

Vous pouvez utiliser des attributs qui peuvent aider à identifier qui a créé le groupe comme [Service] et où il a été créé à partir de [Pays].

Exemples :

- Policy = « GRP [GroupName] [Department] »
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

- Si vous utilisez des Yammer Office 365 connectés, évitez d’utiliser les caractères suivants dans votre stratégie d’attribution de noms : @, \# , \[ , , \] \<, and \> . Si ces caractères sont dans la stratégie d’attribution de noms, les Yammer utilisateurs ne pourront pas créer de groupes.

> [!Tip]
> - Utilisez des chaînes courtes comme suffixe.
> - Utilisez des attributs avec des valeurs.
> - Ne soyez pas trop créatif, la longueur totale du nom est de 264 caractères au maximum.
> - Télécharger mots bloqués spécifiques à votre organisation pour restreindre l’utilisation.

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

1. Dans [Azure Active Directory](https://aad.portal.azure.com), sous **Gérer,** cliquez sur **Groupes.**
2. Sous **Paramètres**, cliquez sur **Stratégie d’attribution de noms.**
3. Sélectionnez **l’onglet Stratégie de noms de** groupes.
4. Sous **Stratégie actuelle,** choisissez si vous souhaitez exiger un préfixe ou un suffixe ou les deux, puis cochez les cases appropriées.
5. Choisissez entre **Attribut et** **Chaîne** pour chaque ligne, puis spécifiez l’attribut ou la chaîne.
6. Lorsque vous avez ajouté les préfixes et les suffixes dont vous avez besoin, cliquez sur **Enregistrer**.

![Capture d’écran des paramètres de stratégie d’attribution de noms de groupes Azure Active Directory.](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>Rubriques connexes

[Planification pas à pas de la gouvernance de la collaboration](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](/azure/active-directory/enterprise-users/groups-settings-cmdlets)