---
title: Stratégie de nommage des groupes Microsoft 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-subscription-management
- Adm_O365
- m365solution-collabgovernance
search.appverid:
- MET150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
recommendations: false
description: Découvrez comment créer une stratégie de nommage pour les groupes Microsoft 365.
ms.openlocfilehash: fd48c975a812eaf015dd5afe0e808103b7fa6d1e
ms.sourcegitcommit: fce27da5140691b013a6f7c0ea9c88b4ea4b7c10
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/23/2022
ms.locfileid: "67986815"
---
# <a name="microsoft-365-groups-naming-policy"></a>Stratégie de nommage des groupes Microsoft 365

Vous pouvez utiliser une stratégie de nommage de groupe pour appliquer une stratégie de nommage cohérente pour les groupes créés par les utilisateurs de votre organisation. Une stratégie de nommage peut vous aider, vous et vos utilisateurs, à identifier la fonction du groupe, l’appartenance, la région géographique ou qui a créé le groupe. La stratégie de nommage peut également aider à catégoriser les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les noms de groupe et les alias.

La stratégie de nommage est appliquée aux groupes créés sur toutes les charges de travail de groupes (comme Outlook, Microsoft Teams, SharePoint, Planner, Yammer, etc.). Il est appliqué à la fois au nom du groupe et à l’alias de groupe. Elle est également appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom, l’alias, la description ou l’avatar du groupe est modifié pour un groupe existant.

> [!TIP]
> Une stratégie de nommage de groupe Microsoft 365 s’applique uniquement aux groupes Microsoft 365. Il ne s’applique pas aux groupes de distribution créés dans Exchange Online. Pour créer une stratégie d’affectation de noms pour les groupes de distribution, consultez [Créer une stratégie d’affectation de noms de groupe de distribution](/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

La stratégie de noms de groupes comprend les fonctionnalités suivantes :

- **Stratégie d’affectation de noms de préfixe-suffixe** : vous pouvez utiliser des préfixes ou des suffixes pour définir la convention d’affectation de noms des groupes (par exemple : « US\_My Group\_Engineering »). Les préfixes/suffixes peuvent être des chaînes fixes ou des attributs utilisateur tels que [Department] qui seront remplacés en fonction de l’utilisateur qui crée le groupe.

- **Mots bloqués personnalisés** : vous pouvez charger un ensemble de mots bloqués spécifiques à votre organisation qui seraient bloqués dans les groupes créés par les utilisateurs. (Par exemple : « CEO, Payroll, HR »).

## <a name="licensing-requirements"></a>Conditions d'octroi de licence

L’utilisation d’une stratégie de noms Azure AD pour les groupes Microsoft 365 nécessite que vous possédiez, mais pas nécessairement attribuer une licence Azure Active Directory Premium P1 ou une licence AZURE AD Basic EDU pour chaque utilisateur unique (y compris les invités) membre d’un ou plusieurs utilisateurs Microsoft 365 groupes.

Cela est également requis pour l’administrateur qui crée la stratégie d’affectation de noms de groupes.

## <a name="prefix-suffix-naming-policy"></a>Prefix-Suffix stratégie de nommage

Les préfixes et suffixes peuvent être des chaînes fixes ou des attributs utilisateur.

### <a name="fixed-strings"></a>Chaînes fixes

Vous pouvez utiliser des chaînes courtes qui peuvent vous aider à différencier les groupes dans la barre d’accès et la navigation à gauche des charges de travail de groupe. Certains des suffixes de préfixes courants sont des mots clés tels que « Grp\_Name », «\# Name », «\_ Name »

### <a name="attributes"></a>Attributs

Vous pouvez utiliser des attributs qui peuvent vous aider à identifier qui a créé le groupe comme [Département] et où il a été créé à partir de [Country].

Exemples :

- Policy = « GRP [GroupName] [Department] »
- Service de l’utilisateur = Ingénierie
- Nom du groupe créé = « GRP My Group Engineering »

Les Azure Active Directory (Azure AD) pris en charge sont [Department], [Company], [Office], [StateOrProvince], [CountryOrRegion] et [Title].

- Les attributs utilisateur non pris en charge sont considérés comme des chaînes fixes, par exemple [postalCode].

- Les attributs d’extension et les attributs personnalisés ne sont pas pris en charge.

Il est recommandé d'utiliser des attributs dont les valeurs sont renseignées pour tous les utilisateurs de votre organisation et de ne pas utiliser d'attributs dont les valeurs sont plus longues.

### <a name="things-to-look-out-for"></a>Éléments à prendre en charge

- Lors de la création de la stratégie, la longueur totale des préfixes et des suffixes est limitée à 53 caractères.

- Les préfixes et suffixes peuvent contenir des caractères spéciaux pris en charge dans le nom du groupe et l’alias de groupe. Lorsque les préfixes et suffixes contiennent des caractères spéciaux qui ne sont pas autorisés dans l’alias de groupe, ils sont appliqués uniquement au nom du groupe. Dans ce cas, les préfixes et suffixes appliqués au nom de groupe sont donc différents de celui appliqué à l’alias de groupe.

  > [!NOTE]
  > Un point (.) ou un trait d’union (-) est autorisé n’importe où dans le nom du groupe, sauf au début ou à la fin du nom. Un trait de soulignement (_) est autorisé n’importe où dans le nom du groupe, y compris au début ou à la fin du nom.

- Si vous utilisez Yammer Office 365 groupes connectés, évitez d’utiliser les caractères suivants dans votre stratégie de nommage : @, \#, \[, \]\<, and \>. Si ces caractères sont dans la stratégie d’attribution de noms, les Yammer utilisateurs ne pourront pas créer de groupes.

> [!Tip]
> - Utilisez des chaînes courtes comme suffixe.
> - Utilisez des attributs avec des valeurs.
> - Ne soyez pas trop créatif, la longueur totale du nom a un maximum de 264 caractères.
> - Chargez des mots bloqués spécifiques à votre organisation pour restreindre l’utilisation.

## <a name="custom-blocked-words"></a>Mots bloqués personnalisés

Vous pouvez entrer une liste séparée par des virgules de mots bloqués qui seront bloqués dans les noms de groupe et les alias.

Aucune recherche de sous-chaîne n’est effectuée; Plus précisément, une correspondance exacte entre le nom entré par l’utilisateur et les mots bloqués personnalisés est nécessaire pour déclencher un échec.

**Éléments à prendre en charge** :

- Les mots bloqués ne respectent pas la casse.

- Lorsqu’un utilisateur entre un mot bloqué, le client de groupe affiche un message d’erreur avec le mot bloqué.

- Il n’existe aucune restriction de caractère dans les mots bloqués utilisés.

- Il existe une limite de 5 000 mots qui peuvent être définis en tant que mots bloqués.

## <a name="admin-override"></a>remplacement de Administration

Certains administrateurs sont exemptés de ces stratégies, sur toutes les charges de travail et points de terminaison de groupe, afin qu’ils puissent créer des groupes avec ces mots bloqués et avec les conventions d’affectation de noms souhaitées. Voici la liste des rôles d’administrateur exemptés de la stratégie de nommage de groupe.

- Administrateur global

- Prise en charge de niveau 1 du partenaire

- Prise en charge de niveau 2 du partenaire

- Administrateur de compte d’utilisateur

## <a name="how-to-set-up-the-naming-policy"></a>Comment configurer la stratégie d’affectation de noms

Pour configurer une stratégie de nommage :

1. Dans [Azure Active Directory](https://aad.portal.azure.com), sous **Gérer**, cliquez sur **Groupes**.
2. Sous **Paramètres**, cliquez sur **Stratégie de nommage**.
3. Choisissez l’onglet **Stratégie d’affectation de noms** de groupe.
4. Dans **la stratégie actuelle**, choisissez si vous souhaitez exiger un préfixe ou un suffixe ou les deux, puis activez les cases à cocher appropriées.
5. Choisissez entre **Attribut** et **Chaîne** pour chaque ligne, puis spécifiez l’attribut ou la chaîne.
6. Une fois que vous avez ajouté les préfixes et suffixes dont vous avez besoin, cliquez sur **Enregistrer**.

![Capture d’écran des paramètres de stratégie d’affectation de noms de groupes dans Azure Active Directory.](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>Voir aussi

[Recommandations en matière de planification de la gouvernance de collaboration](collaboration-governance-overview.md#collaboration-governance-planning-recommendations)

[Créer votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](/azure/active-directory/enterprise-users/groups-settings-cmdlets)