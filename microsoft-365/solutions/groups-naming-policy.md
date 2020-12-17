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
ms.openlocfilehash: 9bc0a4c7e1ae6ad532c97b442a2bc50880a942fc
ms.sourcegitcommit: 884ac262443c50362d0c3ded961d36d6b15d8b73
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/16/2020
ms.locfileid: "49698674"
---
# <a name="microsoft-365-groups-naming-policy"></a>Stratégie de noms de groupes Microsoft 365

Vous pouvez utiliser une stratégie de noms de groupes pour appliquer une stratégie d’attribution de noms cohérente pour les groupes créés par les utilisateurs au sein de votre organisation. Une stratégie de noms peut vous aider, ainsi que vos utilisateurs, à identifier la fonction du groupe, de l’appartenance, de la région géographique ou de la personne qui a créé le groupe. La stratégie d’attribution de noms peut également aider à catégoriser les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les alias et les noms de groupes.

La stratégie de noms est appliquée aux groupes qui sont créés dans toutes les charges de travail de groupe (comme Outlook, Microsoft Teams, SharePoint, Planner, Yammer, etc.). Elle est appliquée à la fois au nom de groupe et à l’alias de groupe. Elle est appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom ou l’alias du groupe est modifié pour un groupe existant.

> [!TIP]
> Une stratégie de noms de groupes Microsoft 365 s’applique uniquement aux groupes Microsoft 365. Elle ne s’applique pas aux groupes de distribution créés dans Exchange Online. Pour créer une stratégie de noms pour les groupes de distribution, consultez [la rubrique Create a distribution Group Naming Policy](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

La stratégie de noms de groupes se compose des fonctionnalités suivantes :

- **Préfixe-suffixe stratégie de noms**: vous pouvez utiliser des préfixes ou des suffixes pour définir la Convention d’affectation de noms des groupes (par exemple : « US \_ My Group \_ Engineering »). Les préfixes/suffixes peuvent être des chaînes fixes ou des attributs utilisateur comme [service] qui sont remplacés en fonction de l’utilisateur qui crée le groupe.

- **Mots bloqués personnalisés**: vous pouvez télécharger un ensemble de mots bloqués spécifiques à votre organisation qui seraient bloqués dans les groupes créés par les utilisateurs. (Par exemple : « PDG, paie, RH »).

## <a name="licensing-requirements"></a>Critères de licence

L’utilisation de la stratégie d’attribution de noms Azure AD pour les groupes Microsoft 365 nécessite que vous disposiez, mais pas nécessairement d’une licence Azure Active Directory Premium P1 ou d’Azure AD basique EDU pour chaque utilisateur (y compris les invités) qui est membre d’un ou de plusieurs groupes Microsoft 365.

Cela est également requis pour l’administrateur qui crée la stratégie de noms de groupes.

## <a name="prefix-suffix-naming-policy"></a>Stratégie de noms de Prefix-Suffix

Les préfixes et suffixes peuvent être des chaînes fixes ou des attributs d’utilisateur.

### <a name="fixed-strings"></a>Chaînes fixes

Vous pouvez utiliser des chaînes courtes qui peuvent vous aider à différencier les groupes dans la liste d’adresses globale et la navigation de gauche des charges de travail de groupe. Certains suffixes de préfixe courants sont des mots clés tels que « GRP \_ Name », « \# Name », « \_ Name »

### <a name="attributes"></a>Attributs

Vous pouvez utiliser des attributs qui peuvent aider à identifier qui a créé le groupe, comme [service] et où il a été créé à partir de comme [pays].

Exemples :

- Policy = "GRP [nom_groupe] [service]"
- Service de l’utilisateur = ingénierie
- Créé le nom du groupe = « GRP My Group Engineering »

Les attributs Azure Active Directory (Azure AD) pris en charge sont [service], [Company], [Office], [StateOrProvince], [CountryOrRegion] et [title].

- Les attributs utilisateur non pris en charge sont considérés comme des chaînes fixes, par exemple, [CodePostal].

- Les attributs d’extension et les attributs personnalisés ne sont pas pris en charge.

Il est recommandé d’utiliser des attributs dont les valeurs sont renseignées pour tous les utilisateurs de votre organisation et n’utilisent pas les attributs dont les valeurs sont plus longues.

### <a name="things-to-look-out-for"></a>Éléments à rechercher

- Pendant la création de la stratégie, la longueur de la chaîne des préfixes et des suffixes est limitée à 53 caractères.

- Les préfixes et les suffixes peuvent contenir des caractères spéciaux pris en charge dans le nom du groupe et l’alias de groupe. Lorsque les préfixes et les suffixes contiennent des caractères spéciaux qui ne sont pas autorisés dans l’alias de groupe, ils ne sont appliqués qu’au nom du groupe. Dans ce cas, les préfixes et les suffixes appliqués au nom de groupe diffèrent de ceux appliqués à l’alias de groupe.

  > [!NOTE]
  > Un point (.) ou un tiret (-) est autorisé n’importe où dans le nom du groupe, sauf au début ou à la fin du nom. Un trait de soulignement (_) est autorisé n’importe où dans le nom du groupe, y compris au début ou à la fin du nom.

- Si vous utilisez des groupes liés à Yammer Office 365, évitez d’utiliser les caractères suivants dans votre stratégie de noms : @, \# , \[ , \] , \<, and \> . Si ces caractères sont dans la stratégie de noms, les utilisateurs de Yammer ordinaires ne pourront pas créer de groupes.

> [!Tip]
> - Utiliser des chaînes courtes comme suffixe.
> - Utilisez des attributs avec des valeurs.
> - Ne soyez pas trop créatif, la longueur totale du nom est de 264 caractères au maximum.
> - Charger les mots bloqués spécifiques de votre organisation pour restreindre l’utilisation.

## <a name="custom-blocked-words"></a>Mots bloqués personnalisés

Vous pouvez entrer une liste de mots bloqués séparés par des virgules qui seront bloqués dans les noms de groupe et les alias.

Aucune recherche de sous-chaîne n’est effectuée ; plus précisément, une correspondance exacte entre le nom entré par l’utilisateur et les mots bloqués personnalisés est requise pour déclencher un échec.

**Éléments à rechercher**:

- Les mots bloqués ne sont pas sensibles à la casse.

- Lorsqu’un utilisateur entre un mot bloqué, le client de groupe affiche un message d’erreur avec le mot bloqué.

- Il n’existe pas de restrictions de caractères dans les mots bloqués utilisés.

- Il existe une limite de 5000 mots pouvant être définis en tant que mots bloqués.

## <a name="admin-override"></a>Remplacement par l’administrateur

Certains administrateurs sont exemptés de ces stratégies, pour toutes les charges de travail et les points de terminaison de groupe, afin qu’ils puissent créer des groupes avec ces mots bloqués et avec les conventions d’affectation de noms de votre choix. Voici la liste des rôles d’administrateur exemptés de la stratégie de noms de groupes.

- Administrateur global

- Prise en charge du niveau 1 du partenaire

- Prise en charge du niveau 2 du partenaire

- Administrateur de compte d’utilisateur

## <a name="how-to-set-up-the-naming-policy"></a>Procédure de configuration de la stratégie de noms

Pour configurer une stratégie d’attribution de noms :

1. Dans [Azure Active Directory](https://aad.portal.azure.com), sous **gestion**, cliquez sur **groupes**.
2. Sous **paramètres**, cliquez sur **stratégie de noms**.
3. Choisissez l’onglet **stratégie d’attribution de noms de groupes** .
4. Sous **stratégie actuelle**, choisissez si vous souhaitez exiger un préfixe ou un suffixe, ou les deux, et activez les cases à cocher appropriées.
5. Choisissez entre **attribut** et **chaîne** pour chaque ligne, puis spécifiez l’attribut ou la chaîne.
6. Une fois que vous avez ajouté les préfixes et les suffixes dont vous avez besoin, cliquez sur **Enregistrer**.

![Capture d’écran des paramètres de stratégie d’attribution de noms de groupes dans Azure Active Directory](../media/groups-naming-policy-azure.png)

## <a name="related-topics"></a>Voir aussi

[Planification de la gouvernance de collaboration étape par étape](collaboration-governance-overview.md#collaboration-governance-planning-step-by-step)

[Création de votre plan de gouvernance de collaboration](collaboration-governance-first.md)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](https://go.microsoft.com/fwlink/?linkid=868341)
