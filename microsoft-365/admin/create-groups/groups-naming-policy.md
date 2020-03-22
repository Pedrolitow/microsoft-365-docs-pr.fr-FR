---
title: Stratégie de noms de groupes Office 365
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MST160
- MET150
- MOE150
ms.assetid: 6ceca4d3-cad1-4532-9f0f-d469dfbbb552
description: Découvrez comment créer une stratégie d’attribution de noms pour les groupes Office 365.
ms.openlocfilehash: 4325a5e0a1de0c3a83be71220abd256c204ec07d
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42894622"
---
# <a name="office-365-groups-naming-policy"></a>Stratégie de noms de groupes Office 365

Vous utilisez une stratégie de noms de groupes pour appliquer une stratégie d’attribution de noms cohérente pour les groupes créés par les utilisateurs de votre organisation. Une stratégie de noms peut vous aider, ainsi que vos utilisateurs, à identifier la fonction du groupe, de l’appartenance, de la région géographique ou de la personne qui a créé le groupe. La stratégie d’attribution de noms peut également aider à catégoriser les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les alias et les noms de groupes.

La stratégie de noms est appliquée aux groupes qui sont créés dans toutes les charges de travail de groupe (comme Outlook, Microsoft Teams, SharePoint, Planner, Yammer, etc.). Elle est appliquée à la fois au nom de groupe et à l’alias de groupe. Elle est appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom ou l’alias du groupe est modifié pour un groupe existant.

> [!TIP]
> Une stratégie de noms de groupes Office 365 s’applique uniquement aux groupes Office 365. Elle ne s’applique pas aux groupes de distribution créés dans Exchange Online. Pour créer une stratégie de noms pour les groupes de distribution, consultez [la rubrique Create a distribution Group Naming Policy](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

La stratégie de noms de groupes se compose des fonctionnalités suivantes :

- **Préfixe-suffixe stratégie de noms**: vous pouvez utiliser des préfixes ou des suffixes pour définir la Convention d’affectation de\_noms des\_groupes (par exemple : « US My Group Engineering »). Les préfixes/suffixes peuvent être des chaînes fixes ou des attributs utilisateur comme [service] qui sont remplacés en fonction de l’utilisateur qui crée le groupe.

- **Mots bloqués personnalisés**: vous pouvez télécharger un ensemble de mots bloqués spécifiques à votre organisation qui seraient bloqués dans les groupes créés par les utilisateurs. (Par exemple : « PDG, paie, RH »).

## <a name="licensing-requirements"></a>Critères de licence

L’utilisation de la stratégie d’attribution de noms Azure AD pour les groupes Office 365 nécessite que vous disposiez mais pas nécessairement d’une licence Azure Active Directory Premium P1 ou d’Azure AD basique EDU pour chaque utilisateur (y compris les invités) qui est membre d’un ou de plusieurs groupes Office 365.

Cela est également requis pour l’administrateur qui crée la stratégie de noms de groupes.

## <a name="prefix-suffix-naming-policy"></a>Préfixe-suffixe de nom de suffixe

Les préfixes et suffixes peuvent être des chaînes fixes ou des attributs d’utilisateur.

### <a name="fixed-strings"></a>Chaînes fixes

Vous pouvez utiliser des chaînes courtes qui peuvent vous aider à différencier les groupes dans la liste d’adresses globale et la navigation de gauche des charges de travail de groupe. Certains suffixes de préfixe courants sont des mots clés tels que\_« GRP name »\#, « name »\_, « Name »

### <a name="attributes"></a>Attributs

Vous pouvez utiliser des attributs qui peuvent aider à identifier qui a créé le groupe, comme [service] et où il a été créé à partir de comme [pays].

|||
|:-----|:-----|
|**Exemples**|Policy = "GRP [nom_groupe] [service]"|
||Service de l’utilisateur = ingénierie|
||Créé le nom du groupe = « GRP My Group Engineering »|

Les attributs Azure Active Directory (Azure AD) pris en charge sont [service], [Company], [Office], [StateOrProvince], [CountryOrRegion] et [title].

- Les attributs utilisateur non pris en charge sont considérés comme des chaînes fixes. Par exemple, "[CodePostal]"

- Les attributs d’extension et les attributs personnalisés ne sont pas pris en charge.

Il est recommandé d’utiliser des attributs dont les valeurs sont renseignées pour tous les utilisateurs de votre organisation et n’utilisent pas les attributs dont les valeurs sont plus longues.

### <a name="things-to-look-out-for"></a>Éléments à rechercher

- Pendant la création de la stratégie, la longueur de la chaîne des préfixes et des suffixes est limitée à 53 caractères.

- Les préfixes et les suffixes peuvent contenir des caractères spéciaux pris en charge dans le nom du groupe et l’alias de groupe. Lorsque les préfixes et les suffixes contiennent des caractères spéciaux qui ne sont pas autorisés dans l’alias de groupe, ils ne sont appliqués qu’au nom du groupe. Dans ce cas, les préfixes et les suffixes appliqués au nom de groupe diffèrent de ceux appliqués à l’alias de groupe.

- Si vous utilisez des groupes liés à Yammer Office 365, évitez d’utiliser les caractères suivants dans votre stratégie de noms \#: \[@ \], \<,, \>, et. Si ces caractères sont dans la stratégie de noms, les utilisateurs de Yammer ordinaires ne pourront pas créer de groupes.

## <a name="custom-blocked-words"></a>Mots bloqués personnalisés

Vous pouvez entrer une liste de mots bloqués séparés par des virgules qui seront bloqués dans les noms de groupe et les alias.

Aucune recherche de sous-chaîne n’est effectuée ; plus précisément, une correspondance exacte entre le nom entré par l’utilisateur et les mots bloqués personnalisés est requise pour déclencher un échec. La recherche de sous-chaîne n’est pas réalisée afin que les utilisateurs puissent utiliser certains mots courants, tels que « classe », même si « ass » est un mot bloqué.

**Éléments à rechercher**:

- Les mots bloqués ne sont pas sensibles à la casse.

- Lorsqu’un utilisateur entre un mot bloqué, le client de groupe affiche un message d’erreur avec le mot bloqué.

- Il n’existe pas de restrictions de caractères dans les mots bloqués utilisés.

- Il existe une limite de 5000 mots pouvant être définis en tant que mots bloqués.

## <a name="admin-override"></a>Remplacement par l’administrateur

Les administrateurs sélectifs sont exemptés de ces stratégies, pour toutes les charges de travail et les points de terminaison de groupe, afin qu’ils puissent créer des groupes avec ces mots bloqués et avec les conventions d’affectation de noms de votre choix. Voici la liste des rôles d’administrateur exemptés de la stratégie de noms de groupes.

- Administrateur global

- Prise en charge du niveau 1 du partenaire

- Prise en charge du niveau 2 du partenaire

- Administrateur de compte d’utilisateur

- Writers d’annuaire

## <a name="how-to-set-up-the-naming-policy"></a>Procédure de configuration de la stratégie de noms

Pour configurer une stratégie d’attribution de noms :

1. Dans [Azure Active Directory](https://aad.portal.azure.com), sous **gestion**, cliquez sur **groupes**.
2. Sous **paramètres**, cliquez sur **stratégie de noms**.
3. Choisissez l’onglet **stratégie d’attribution de noms de groupes** .
4. Sous **stratégie actuelle**, choisissez si vous souhaitez exiger un préfixe ou un suffixe, ou les deux, et activez les cases à cocher appropriées.
5. Choisissez entre **attribut** et **chaîne** pour chaque ligne, puis spécifiez l’attribut ou la chaîne.
6. Une fois que vous avez ajouté les préfixes et les suffixes dont vous avez besoin, cliquez sur **Enregistrer**.

![Capture d’écran des paramètres de stratégie d’attribution de noms de groupes dans Azure Active Directory](../../media/groups-naming-policy-azure.png)

> [!NOTE]
> Les équipes StaffHub ne suivent pas la stratégie d’attribution de noms, mais le groupe Office 365 sous-jacent le fait. Le nom de l’équipe StaffHub n’applique pas les préfixes et les suffixes et ne vérifie pas les mots bloqués personnalisés. Mais StaffHub applique les préfixes et les suffixes et supprime les mots bloqués du groupe Office 365 sous-jacent.

## <a name="more-articles-on-naming-policy"></a>Autres articles sur la stratégie de noms

[Appliquer une stratégie d’attribution de noms pour les groupes Office 365 dans Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=868340)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](https://go.microsoft.com/fwlink/?linkid=868341)
