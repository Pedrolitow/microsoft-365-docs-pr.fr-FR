---
title: Stratégie de noms de groupes Office 365
ms.reviewer: arvaradh
f1.keywords:
- NOCSH
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
ms.openlocfilehash: 11e2907462d325e4ad421914ae5a0deb5013e695
ms.sourcegitcommit: 812aab5f58eed4bf359faf0e99f7f876af5b1023
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/02/2020
ms.locfileid: "42352715"
---
# <a name="office-365-groups-naming-policy"></a>Stratégie de noms de groupes Office 365

Vous utilisez une stratégie de noms de groupes pour appliquer une stratégie d’attribution de noms cohérente pour les groupes créés par les utilisateurs de votre organisation. Une stratégie de noms peut vous aider, ainsi que vos utilisateurs, à identifier la fonction du groupe, de l’appartenance, de la région géographique ou de la personne qui a créé le groupe. La stratégie d’attribution de noms peut également aider à catégoriser les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les alias et les noms de groupes.

La stratégie de noms est appliquée aux groupes qui sont créés dans toutes les charges de travail de groupe (comme Outlook, Microsoft Teams, SharePoint, Planner, Yammer, etc.). Elle est appliquée à la fois au nom de groupe et à l’alias de groupe. Elle est appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom ou l’alias du groupe est modifié pour un groupe existant.

> [!TIP]
> Une stratégie de noms de groupes Office 365 s’applique uniquement aux groupes Office 365. Elle ne s’applique pas aux groupes de distribution créés dans Exchange Online. Pour créer une stratégie de noms pour les groupes de distribution, consultez [la rubrique Create a distribution Group Naming Policy](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-distribution-groups/create-group-naming-policy).

La stratégie de noms de groupes se compose des fonctionnalités suivantes :

- **Préfixe-suffixe stratégie de noms**: vous pouvez utiliser des préfixes ou des suffixes pour définir la Convention d’affectation de\_noms\_des groupes\_(par exemple, « GRP US My Group Engineering »). Les préfixes/suffixes peuvent être des chaînes fixes ou des attributs utilisateur comme [service] qui sont remplacés en fonction de l’utilisateur qui crée le groupe.

- **Mots bloqués personnalisés**: vous pouvez télécharger un ensemble de mots bloqués spécifiques à leur organisation qui seraient bloqués dans les groupes créés par les utilisateurs. (Par exemple : « PDG, paie, RH »).

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

Les attributs Azure Active Directory (Azure AD) pris en charge sont [service], [Company], [Office], [StateOrProvince], [CountryOrRegion], [title]

- Les attributs utilisateur non pris en charge sont considérés comme des chaînes fixes. Par exemple, "[CodePostal]"

- Les attributs d’extension et les attributs personnalisés ne sont pas pris en charge.

Il est recommandé d’utiliser des attributs dont les valeurs sont renseignées pour tous les utilisateurs de votre organisation et n’utilisent pas les attributs dont les valeurs sont plus longues.

### <a name="things-to-look-out-for"></a>Éléments à rechercher

- Pendant la création de la stratégie, la longueur de la chaîne des préfixes et des suffixes est limitée à 53 caractères.

- Les préfixes et les suffixes peuvent contenir des caractères spéciaux pris en charge dans le nom du groupe et l’alias de groupe. Lorsque les préfixes et les suffixes contiennent des caractères spéciaux qui ne sont pas autorisés dans l’alias de groupe, ils sont supprimés et appliqués à l’alias de groupe. Dans ce cas, les préfixes et les suffixes appliqués au nom de groupe diffèrent de ceux appliqués à l’alias de groupe.

- Si vous utilisez des groupes liés à Yammer Office 365, évitez d’utiliser les caractères suivants dans votre stratégie de noms \#: \[@ \], \<,, \>, et. Si ces caractères sont dans la stratégie de noms, les utilisateurs de Yammer ordinaires ne pourront pas créer de groupes.

## <a name="custom-blocked-words"></a>Mots bloqués personnalisés

Vous pouvez entrer une liste de mots bloqués séparés par des virgules qui seront bloqués dans les noms de groupe et les alias.

La vérification des mots bloqués est exécutée sur le nom de groupe entré par l’utilisateur. Par conséquent, si l’utilisateur entre « darnit »\_et « prefix » est la stratégie d'\_attribution de noms, « prefix darnit » échouera.

Aucune recherche de sous-chaîne n’est effectuée ; plus précisément, une correspondance exacte entre le nom entré par l’utilisateur et les mots bloqués personnalisés est requise pour déclencher un échec. La recherche de sous-chaîne n’est pas réalisée afin que les utilisateurs puissent utiliser certains mots courants, tels que « classe », même si « ass » est un mot bloqué.

**Éléments à rechercher**:

- Les mots bloqués ne sont pas sensibles à la casse.

- Lorsqu’un utilisateur entre un mot bloqué, le client de groupe affiche un message d’erreur avec le mot bloqué.

- Il n’existe pas de restrictions de caractères dans les mots bloqués utilisés.

- Il existe une limite supérieure de 5000 mots pouvant être définis en tant que mots bloqués.

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

## <a name="naming-policy-experiences-across-office-365-apps"></a>Application des stratégies d’appellation dans les applications Office 365

Les applications Office 365 ont été mises à jour pour afficher un aperçu du nom du groupe de stratégie d’appellation (avec préfixes et suffixes) lorsque l’utilisateur tape le nom et l’alias du groupe. Lorsque l’utilisateur entre des mots bloqués, un message d’erreur s’affiche afin qu’il puisse supprimer les mots bloqués.

## <a name="outlook-on-the-web"></a>Outlook sur le web

Outlook sur le Web (anciennement appelé Outlook Web App ou OWA) affiche la stratégie d’appellation nom décoré lorsque l’utilisateur tape un nom de groupe ou un alias de groupe. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche dans l’interface utilisateur avec le mot bloqué pour permettre à l’utilisateur de le supprimer. Les captures instantanées d’une expérience Web Outlook sont illustrées ci-dessous.

![Vue côte à côte de la stratégie de noms de groupes dans les groupes Office 365](../../media/1a21657a-c542-4d9e-ac7d-887ac542a9d9.png)

## <a name="outlook-desktop"></a>Bureau Outlook

Les groupes créés dans Outlook Desktop sont conformes à la stratégie d’attribution de noms. L’application de bureau Outlook n’affiche pas encore l’aperçu de la stratégie de noms et ne renvoie pas les erreurs Word bloquées personnalisées, lorsque l’utilisateur entre le nom du groupe. Toutefois, la stratégie de noms est automatiquement appliquée lors de la sélection de la fonction créer/modifier et les utilisateurs affichent des erreurs si le nom ou l’alias du groupe contient des mots bloqués personnalisés.

## <a name="microsoft-teams"></a>Microsoft Teams

Microsoft teams affiche le nom décoré de la stratégie de nom lorsque l’utilisateur tape un nom d’équipe. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche avec le mot bloqué pour permettre à l’utilisateur de le supprimer.

![Exemple de stratégie de noms de groupes dans Microsoft teams bloqué](../../media/7c904546-5853-4642-949a-a55dbb004eca.png)

## <a name="sharepoint"></a>SharePoint

SharePoint affiche le nom de la stratégie d’appellation lorsque l’utilisateur tape un nom de site ou une adresse de messagerie de groupe. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche, ainsi que le mot bloqué pour permettre à l’utilisateur de le supprimer.

![Stratégie de noms de groupes-nom bloqué du site SharePoint](../../media/cf0d6158-fd32-4a93-ac24-2e037102c42c.png)

## <a name="microsoft-stream"></a>Microsoft Stream

Microsoft Stream affiche le nom décoré de la stratégie de nom lorsque l’utilisateur tape un nom de groupe ou un alias de messagerie de groupe. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche avec le mot bloqué pour permettre à l’utilisateur de le supprimer.

![Exemple de stratégie de noms de groupes bloqué pour Microsoft Stream](../../media/9748f52a-3814-41a6-9ac1-4e8cd4c91011.png)

## <a name="outlook-ios-and-android-app"></a>Application Outlook iOS et Android

Les groupes créés dans les applications Outlook sont conformes à la stratégie d’attribution de noms. Outlook Mobile affiche l’aperçu de stratégie d’appellation lors de la saisie du nom du groupe. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche lors de la création du groupe, afin que l’utilisateur puisse supprimer le mot bloqué.

## <a name="planner"></a>Planificateur

Le planificateur est conforme à la stratégie d’attribution de noms. Planner affiche l’aperçu de la stratégie d’appellation lors de la saisie du nom du plan. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche lors de la création du plan, afin que l’utilisateur puisse supprimer le mot bloqué.

![Stratégie de noms de groupes-créer un exemple de blocage bloqué](../../media/ea692b44-3a56-4e6d-bcb8-8444fe5bbc4f.png)

## <a name="dynamics-365-for-customer-engagement"></a>Dynamics 365 pour l’engagement client

Dynamics 365 pour engagement client est conforme à la stratégie d’attribution de noms. Dynamics 365 affiche le nom décoré de la stratégie d’attribution de noms lorsque l’utilisateur tape un nom de groupe ou un alias de messagerie de groupe. Lorsque l’utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche avec le mot bloqué pour permettre à l’utilisateur de le supprimer.

![Dynamics 365](../../media/8190331c-6779-42bd-a6b3-f7007428c8ae.png)

## <a name="school-data-sync-sds"></a>School Data Sync (SDS)

Les groupes créés via SDS sont conformes à la stratégie d’attribution de noms, mais la stratégie de nom n’est pas appliquée automatiquement. Les administrateurs SDS doivent ajouter les préfixes et suffixes aux noms de classe pour lesquels les groupes doivent être créés, puis charger vers SDS. La création/modification des groupes échouait autrement.

## <a name="outlook-customer-manager-ocm"></a>Gestionnaire de clients Outlook (OCM)

Le gestionnaire de clients Outlook est compatible avec la stratégie d’attribution de noms. La stratégie de noms est automatiquement appliquée au groupe créé dans le gestionnaire de clients Outlook. Si l’un des mots de « l’équipe des ventes » est défini comme un mot bloqué personnalisé, la création du groupe dans le OCM est bloquée. L’utilisateur ne peut pas créer le groupe OCM et ne peut pas utiliser l’application OCM. "

## <a name="classroom-app"></a>Application de classe

Les groupes créés dans l’application de classe sont conformes à la stratégie de noms, mais la stratégie de noms n’est pas appliquée automatiquement et l’aperçu de stratégie d’appellation ne s’affiche pas pour les utilisateurs lors de la saisie d’un nom de groupe de la classe. Afin que les utilisateurs doivent entrer le nom du groupe de classes décoré avec des préfixes et des suffixes. Dans le cas contraire, la création ou la modification du groupe de salles de classe échouera avec des erreurs.

## <a name="power-bi"></a>Power BI

Les groupes créés dans les espaces de travail Power BI sont conformes à la stratégie d’attribution de noms, mais la stratégie de nom n’est pas appliquée automatiquement. De plus, l’aperçu de stratégie d’appellation ne s’affiche pas lorsque les utilisateurs entrent un nom d’espace de travail Power BI.

Le nom recommandé avec la stratégie d’attribution de noms appliquée-est indiqué dans les détails de l’erreur sur les espaces de travail de création ou de modification. Cela signifie que les utilisateurs doivent entrer le nom de l’espace de travail décoré avec des préfixes et des suffixes. Dans le cas contraire, la création ou la modification de l’espace de travail échoue avec des erreurs.

## <a name="yammer"></a>Yammer

Lorsqu’un utilisateur se connecte à Yammer avec son compte Azure Active Directory crée un groupe ou modifie un nom de groupe, le nom du groupe est conforme à la stratégie d’attribution de noms. Cela concerne les groupes connectés à Office 365 et tous les autres groupes Yammer.

Si un groupe connecté à Office 365 a été créé avant la stratégie de noms, le nom du groupe ne suit pas automatiquement les stratégies d’attribution de noms. Lorsqu’un utilisateur modifie le nom du groupe, il est invité à ajouter le préfixe et le suffixe.

Si la stratégie de noms inclut des caractères qui ne peuvent pas figurer dans les noms de groupes Yammer, seuls les administrateurs pourront créer un groupe connecté dans Yammer.

## <a name="staffhub"></a>StaffHub

Les équipes StaffHub ne suivent pas la stratégie d’attribution de noms, mais le groupe Office 365 sous-jacent le fait. Le nom de l’équipe StaffHub n’applique pas les préfixes et les suffixes et ne vérifie pas les mots bloqués personnalisés. Mais StaffHub applique les préfixes et les suffixes et supprime les mots bloqués du groupe Office 365 sous-jacent.

## <a name="exchange-powershell"></a>Exchange PowerShell

Les applets de commande Exchange PowerShell sont conformes à la stratégie d’attribution de noms. Les utilisateurs recevront des messages d’erreur appropriés avec des préfixes et suffixes suggérés et des mots bloqués personnalisés si la Convention d’affectation de noms n’est pas utilisée dans les noms de groupe et l’alias de groupe.

## <a name="azure-active-directory-powershell-cmdlets"></a>Applets de commande PowerShell Azure Active Directory

Les applets de commande PowerShell Azure Active Directory sont conformes à la stratégie d’attribution de noms. Les utilisateurs recevront des messages d’erreur appropriés avec des préfixes et suffixes suggérés et des mots bloqués personnalisés si la Convention d’affectation de noms n’est pas utilisée dans les noms de groupe et l’alias de groupe.

## <a name="exchange-admin-center"></a>Centre d’administration Exchange

Le centre d’administration Exchange est conforme à la stratégie d’attribution de noms. Lors de la création ou de la modification des actions, les utilisateurs reçoivent des messages d’erreur appropriés avec des préfixes et suffixes suggérés et des mots bloqués personnalisés si la Convention d’affectation de noms n’est pas utilisée dans les noms de groupe et l’alias de groupe.

## <a name="microsoft-365-admin-center"></a>Centre d’administration Microsoft 365

Le centre d’administration 365 de Microsoft est compatible avec la stratégie d’attribution de noms. Lors de la création ou de la modification des actions, la stratégie de noms est automatiquement appliquée. Les utilisateurs reçoivent des erreurs appropriées lorsqu’ils entrent des mots bloqués personnalisés. Le centre d’administration Microsoft 365 n’affiche pas l’aperçu de la stratégie de noms et ne renvoie pas les erreurs Word bloquées personnalisées, lorsque l’utilisateur entre le nom du groupe.

## <a name="azure-active-directory-portal"></a>Portail Azure Active Directory

Le portail Azure Active Directory est compatible avec la stratégie d’attribution de noms. Le portail Azure Active Directory affiche la stratégie d’appellation aperçu lors de la saisie du nom du groupe. Lorsqu’un utilisateur entre un mot bloqué personnalisé, un message d’erreur s’affiche lors de la création du groupe, afin que l’utilisateur puisse supprimer le mot bloqué.

## <a name="more-articles-on-naming-policy"></a>Autres articles sur la stratégie de noms

[Appliquer une stratégie d’attribution de noms pour les groupes Office 365 dans Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=868340)

[Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](https://go.microsoft.com/fwlink/?linkid=868341)
