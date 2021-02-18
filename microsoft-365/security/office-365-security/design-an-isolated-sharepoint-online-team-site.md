---
title: Conception d’un site d’équipe SharePoint Online isolé
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/15/2017
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid:
- MET150
ms.collection: Ent_O365
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 775a4e9e-3135-4a48-b32f-bbdd9f2bd0aa
description: Concevoir des sites d’équipe SharePoint Online isolés, y compris déterminer les niveaux d’autorisation, attribuer des autorisations aux utilisateurs avec des groupes d’accès et des groupes Azure AD imbrmbrés.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 0d53f3b45e3f406dfb0b38bcc910bd34876acb08
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50288334"
---
# <a name="design-an-isolated-sharepoint-online-team-site"></a>Conception d’un site d’équipe SharePoint Online isolé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)


 **Résumé :** Découvrez comment concevoir des sites d’équipe SharePoint Online.

Cet article vous aide à faire les bons choix de conception avant de créer un site d’équipe SharePoint Online isolé.

## <a name="phase-1-determine-your-sharepoint-groups-and-permission-levels"></a>Phase 1 : choix des groupes SharePoint et des niveaux d’autorisation

Chaque site d’équipe SharePoint Online par défaut est créé avec les groupes SharePoint suivants :

- \<site name> Membres

- \<site name> Visiteurs

- \<site name> Propriétaires

Ces groupes sont distincts des groupes Microsoft 365 et Azure Active Directory (AD) et sont la base de l’attribution d’autorisations pour les ressources du site.

L’ensemble des autorisations qui déterminent ce que le membre d’un groupe SharePoint peut faire dans un site est un niveau d’autorisation. Il existe trois niveaux d’autorisation par défaut pour un site d’équipe SharePoint Online : Modification, Lecture et Contrôle total. Le tableau suivant indique la corrélation par défaut des groupes SharePoint et les niveaux d’autorisation affectés :

****

|Groupe SharePoint|Niveau d’autorisation|
|---|---|
|\<site name> Membres|Modifier|
|\<site name> Visiteurs|Lire|
|\<site name> Propriétaires|Contrôle total|
|

 **Conseil :** vous pouvez créer des groupes SharePoint et des niveaux d’autorisation supplémentaires. Cependant, nous vous recommandons d’utiliser les groupes SharePoint par défaut et les niveaux d’autorisation pour votre site SharePoint Online isolé.

Voici les groupes et les niveaux d’autorisation SharePoint par défaut.

![Groupes Et niveaux d’autorisation SharePoint par défaut pour un site SharePoint Online.](../../media/3f892ab4-6479-42f0-a505-1ba0ef94b9c6.png)

## <a name="phase-2-assign-permissions-to-users-with-access-groups"></a>Phase 2 : attribution des autorisations aux utilisateurs membres de groupes d’accès

Vous pouvez attribuer des autorisations aux utilisateurs en ajoutant leur compte d’utilisateur, ou un groupe Microsoft 365 ou Azure AD dont le compte d’utilisateur est membre, aux groupes SharePoint. Une fois ajoutés, les comptes d’utilisateurs, directement ou indirectement via l’appartenance à un groupe Microsoft 365 ou Azure AD, se voient attribuer le niveau d’autorisation associé au groupe SharePoint.

En prenant l’exemple des groupes SharePoint par défaut :

- Le niveau **\<site name> d’autorisation** Modifier est attribué aux membres du groupe  SharePoint Membres, qui peut inclure des comptes d’utilisateur et des groupes.

- Le niveau **\<site name> d’autorisation** Lecture est attribué aux membres du groupe  Visiteurs SharePoint, qui peut inclure des comptes d’utilisateur et des groupes.

- Le niveau  d’autorisation Contrôle total est attribué aux membres du groupe SharePoint Propriétaires, qui peut inclure des comptes d’utilisateur et des groupes. **\<site name>**

 **Conseil :** même si vous pouvez gérer les autorisations dans chaque compte d’utilisateur, nous vous recommandons plutôt d’utiliser un seul groupe Azure AD, appelé groupe d’accès. Cela simplifie la gestion des autorisations via l’appartenance au groupe d’accès, plutôt que via la gestion de la liste des comptes d’utilisateur pour chaque groupe SharePoint.

Les groupes Azure AD pour Microsoft 365 sont différents groupes Microsoft 365. Les groupes Azure AD apparaissent dans le Centre d’administration Microsoft 365 avec leur **type** de sécurité et n’ont pas d’adresse de messagerie.  Les groupes Azure AD peuvent être gérés dans :

- Services de domaine Active Directory (AD DS) ;

    Il s’agit de groupes qui ont été créés dans votre infrastructure AD DS locale et synchronisés avec votre abonnement Microsoft 365. Dans le Centre d’administration Microsoft 365, ces groupes ont l’état Synchronisé **avec Active Directory.** 

- Office 365

    Ce sont des groupes qui ont été créés à l’aide du Centre d’administration Microsoft 365, du portail Azure ou de Microsoft PowerShell. Dans le Centre d’administration Microsoft 365, ces groupes ont **l’état** **Cloud.**

 **Meilleure pratique :** Si vous utilisez AD DS en local et que vous effectuez une synchronisation avec votre abonnement Microsoft 365, effectuez la gestion de vos utilisateurs et groupes avec AD DS.

Pour les sites d’équipe SharePoint Online isolés, voici à quoi ressemble la structure recommandée du groupe :

****

|Groupe SharePoint|Groupe d’accès basé sur Azure AD|Niveau d’autorisation|
|---|---|---|
|\<site name> Membres|\<site name> Membres|Modifier|
|\<site name> Visiteurs|\<site name> Visionneuses|Lire|
|\<site name> Propriétaires|\<site name> Administrateurs|Contrôle total|
|

 **Meilleure pratique :** Bien que vous pouvez utiliser des groupes Microsoft 365 ou Azure AD en tant que membres de groupes SharePoint, nous vous recommandons d’utiliser des groupes Azure AD. Les groupes Azure AD, gérés via AD DS ou Microsoft 365, vous offrent plus de flexibilité pour utiliser des groupes imbrmbrés afin d’attribuer des autorisations.

Voici les groupes SharePoint par défaut configurés pour utiliser les groupes d’accès basés sur Azure AD.

![Utilisation de groupes d’accès en tant que membres des groupes de sites SharePoint Online par défaut.](../../media/50a76328-ae69-483e-9029-ac4e7357b5ef.png)

Lorsque vous concevez les trois groupes d’accès, rappelez-vous de ceci :

- Il ne doit y avoir que quelques membres dans le groupe d’accès **\<site name> Administrateurs,** correspondant à un petit nombre d’administrateurs SharePoint Online qui gèrent le site d’équipe.

- La plupart des membres de votre site font partie des groupes **\<site name> d’accès Membres** **\<site name> ou** Visionneuses. Étant donné que les membres du site dans le groupe d’accès **\<site name> Membres** ont la possibilité de supprimer ou de modifier des ressources dans le site, réfléchissez attentivement à son appartenance. En cas de doute, ajoutez le membre du site au groupe **\<site name> d’accès Visionneuses.**

Voici un exemple des groupes SharePoint et des groupes d’accès pour un site isolé nommé ProjectX.

![Exemple d’utilisation de groupes d’accès pour un site SharePoint Online nommé ProjectX.](../../media/13afe542-9ffd-4671-9f48-210a0e2a502a.png)

## <a name="phase-3-use-nested-azure-ad-groups"></a>Phase 3 : Utiliser des groupes Azure AD imbrmbrés

Pour un projet impliquant un petit nombre d’utilisateurs, vous pouvez ajouter, dans la plupart des cas, un seul niveau de groupes d’accès basés sur Azure AD aux groupes SharePoint du site. Toutefois, si vous avez un grand nombre de personnes et que ces personnes sont déjà membres de groupes Azure AD établis, vous pouvez plus facilement attribuer des autorisations SharePoint à l’aide de groupes imbrmbrés ou de groupes qui contiennent d’autres groupes en tant que membres.

Par exemple, vous souhaitez créer un site d’équipe SharePoint Online isolé pour favoriser la collaboration entre les responsables des services ventes, marketing, ingénierie, juridique et support technique, mais ils ont déjà leur propre groupe de comptes de responsable. Au lieu de créer un groupe pour les nouveaux membres du site et d’y placer tous les comptes de responsable un par un, placez les groupes de responsables existants pour chaque service dans le nouveau groupe.

 Si vous partagez un abonnement Microsoft 365 entre plusieurs organisations, un seul niveau d’appartenance à un groupe pour un site isolé d’une organisation peut devenir difficile à gérer en raison du nombre important de comptes d’utilisateurs. Dans ce cas, vous pouvez utiliser les groupes Azure AD imbriqués pour chaque organisation dont les groupes gèrent les autorisations.

Pour utiliser les groupes Azure AD imbriqués, procédez comme suit :

1. Identifiez ou créez les groupes Azure AD qui contiendront les comptes d’utilisateur et ajoutez les comptes d’utilisateur en tant que membres.

2. Créez le groupe d’accès basé sur Azure AD conteneur qui contiendra les autres groupes Azure AD et ajoutez ces groupes en tant que membres.

3.  Pour définir le niveau d’accès approprié pour le groupe d’accès conteneur, identifiez le groupe SharePoint et définissez le niveau d’autorisation correspondant.

> [!NOTE]
> Vous ne pouvez pas utiliser les groupes Microsoft 365 imbrmbrés.

Voici un exemple de groupes Azure AD imbrmbrés pour le groupe d’accès aux membres ProjectX.

![Exemple d’utilisation de groupes d’accès imbrmbrés pour le groupe d’accès Membres pour le site ProjectX.](../../media/2abca710-bf9e-4ce8-9bcd-a8e128264fb1.png)

Étant donné que tous les comptes d’utilisateur des équipes responsables de la recherche, de l’ingénierie et du projet sont destinés à être membres du site, il est plus facile d’ajouter leurs groupes Azure AD au groupe d’accès Membres ProjectX.

## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt à créer et à configurer un site isolé en production, consultez la rubrique [Deploy an isolated SharePoint Online team site](deploy-an-isolated-sharepoint-online-team-site.md).

## <a name="see-also"></a>Voir aussi

[Sites d'équipe SharePoint Online isolés](isolated-sharepoint-online-team-sites.md)

[Gestion d’un site d’équipe SharePoint Online isolé](manage-an-isolated-sharepoint-online-team-site.md)

[Déploiement d’un site d’équipe SharePoint Online isolé](deploy-an-isolated-sharepoint-online-team-site.md)
