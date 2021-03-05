---
title: Présentation des Groupes Microsoft 365 pour les administrateurs
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
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
description: En savoir plus sur les groupes Microsoft 365.
ms.openlocfilehash: 75bc743ed8f1965d0ed8a1967e6eac1bd6e0178b
ms.sourcegitcommit: 375168ee66be862cf3b00f2733c7be02e63408cf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50453680"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Présentation des Groupes Microsoft 365 pour les administrateurs

Groupes Microsoft 365 est le service d’appartenance de base qui dirige tout le travail d’équipe dans Microsoft 365. Avec Groupes Microsoft 365, vous pouvez accorder à un groupe de personnes l’accès à une collection de ressources partagées. Ces ressources sont les suivantes :

- Boîte de réception Outlook partagée
- Un calendrier partagé
- Une bibliothèque de documents SharePoint
- Un planificateur
- Un bloc-notes OneNote
- Power BI
- Yammer (si le groupe a été créé à partir de Yammer)
- Une équipe (si le groupe a été créé à partir de Teams)
- Feuille de route (si vous avez Project pour le web)
- Flux

Avec un groupe Microsoft 365, vous n’avez pas besoin d’attribuer manuellement des autorisations à chacune de ces ressources. L’ajout automatique de personnes au groupe leur donne les autorisations dont ils ont besoin.

Tout utilisateur peut créer un groupe, sauf si vous limitez la création de groupe [à un ensemble spécifique de personnes.](manage-creation-of-groups.md) Si vous limitez la création de groupes, les utilisateurs qui ne peuvent pas créer de groupes ne pourront pas créer de sites SharePoint, de planificateurs ou d’équipes. Ces services nécessitent que les personnes qui les créent puissent créer un groupe. Les utilisateurs peuvent toujours participer à des activités de groupe, telles que la création de tâches dans le Planificateur ou l’utilisation de la conversation Teams, à condition qu’ils soient membres du groupe.

Les groupes ont les rôles suivants :

- **Propriétaires** : les propriétaires de groupe peuvent ajouter ou supprimer des membres et avoir des autorisations uniques, telles que la possibilité de supprimer des conversations de la boîte de réception partagée ou de modifier différents paramètres sur le groupe. Les propriétaires de groupe peuvent renommer le groupe, mettre à jour la description ou l’image, etc.
- **Membres** : les membres peuvent accéder à tous les paramètres du groupe, mais ne peuvent pas modifier les paramètres du groupe. Par défaut, les membres du groupe peuvent inviter des invités à rejoindre votre groupe, même si vous pouvez [contrôler ce paramètre.](manage-guest-access-in-groups.md)
- **Invités** : les invités de groupe sont des membres extérieurs à votre organisation.

Seuls les administrateurs globaux, les administrateurs d’utilisateurs et les administrateurs de groupes peuvent créer et gérer des groupes dans le Centre d’administration Microsoft 365. Vous ne pouvez pas être un administrateur délégué (par exemple, consultant désigné comme administrateur).

En tant qu’administrateur, vous pouvez :

- [Spécifier qui peut créer des groupes](manage-creation-of-groups.md)
- [Créer une stratégie d’attribution de noms pour les groupes de votre organisation](groups-naming-policy.md)
- [Choisir le domaine à utiliser lors de la création d’un groupe](choose-domain-to-create-groups.md)
- [Gérer l’accès invité aux groupes](manage-guest-access-in-groups.md)
- [Récupérer un groupe supprimé](restore-deleted-group.md) (dans les 30 jours suivant la suppression)

Si vous préférez une façon plus automatisée de gérer le cycle de vie de vos groupes Microsoft 365, vous pouvez utiliser des stratégies d’expiration pour expirer des groupes à un intervalle de temps spécifique. Les propriétaires du groupe obtiennent un courrier électronique 30, 15 et 1 jour avant l’expiration du groupe qui leur permet de renouveler le groupe si nécessaire. Voir : [Stratégie d’expiration de groupe Microsoft 365.](office-365-groups-expiration-policy.md)

Vous pouvez administrer vos groupes à partir du Centre d’administration Microsoft 365 ou à [l’aide de PowerShell.](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-groups-with-powershell)

Si vous avez de nombreux utilisateurs, par exemple dans une grande entreprise ou une grande entreprise, il se peut que de nombreux utilisateurs créent des groupes à diverses fins. Nous vous recommandons vivement de consulter le Plan de gouvernance dans les groupes [Microsoft 365](plan-for-groups-governance.md) pour les meilleures pratiques.

## <a name="group-limits"></a>Limites de groupe

Les limites suivantes s’appliquent aux groupes Microsoft 365 :

|Maximum...|Valeur|
|:---------|:----|
|Owners per group|100|
|Groups a user can create|250|
|Groupes qu’un administrateur peut créer|Limite de client par défaut maximale de 500 K|
|Nombre de membres|Plus de 1 000, mais seuls 1 000 peuvent accéder simultanément aux conversations de groupe. <br>Les utilisateurs peuvent remarquer des retards lors de l’accès au calendrier et aux conversations dans de grands groupes dans Outlook.|
|Nombre de groupes dont un utilisateur peut être membre|7,000|
|Stockage de fichiers|1 téraoctet + 10 Go par utilisateur abonné + tout autre stockage acheté. Vous pouvez acheter une quantité illimitée de stockage supplémentaire.|
|Taille de la boîte aux lettres de groupe|50 Go|

Le nombre maximal par défaut de groupes Microsoft 365 qu’une organisation peut avoir est de 500 000. Pour aller au-delà de la limite par défaut, vous devez contacter le Support Microsoft. Pour plus d’informations sur les limites des groupes Microsoft 365, voir [Groupes Microsoft 365 - Aide de l’administrateur.](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

La gestion de vos groupes Microsoft 365 est plus efficace lorsque vous avez des informations actionnables sur l’utilisation des groupes. Le Centre d’administration Microsoft 365 dispose d’un outil de rapports qui vous permet de voir l’utilisation du stockage, le nombre de groupes actifs dont vous disposez et la façon dont les utilisateurs utilisent les groupes. Voir : [Rapports Microsoft 365 dans le Centre d’administration](../activity-reports/office-365-groups.md) pour plus d’informations.

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Vous pouvez créer des étiquettes de niveau de sensibilité que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe Microsoft 365. Avec les étiquettes de niveau de sensibilité, vous pouvez configurer : 

- Confidentialité (publique ou privée)
- Accès des utilisateurs externes
- Accès aux appareils nonmanagés

Par exemple, vous pouvez créer une étiquette appelée *Hautement* confidentiel et spécifier que tout groupe créé avec cette étiquette sera privé et n’autorisera pas les utilisateurs externes. Lorsque les utilisateurs de votre organisation sélectionnent cette étiquette lors de la création du groupe, le groupe est définie sur privé et les membres du groupe ne sont pas autorisés à ajouter des utilisateurs externes au groupe.

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, elles ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois les étiquettes de niveau de sensibilité activées. 

Pour plus d’informations sur la création, la gestion et l’utilisation d’étiquettes de sensibilité, voir Utiliser des étiquettes de niveau de sensibilité pour protéger le contenu dans Microsoft Teams, les groupes [Microsoft 365](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites)et les sites SharePoint.

## <a name="which-microsoft-365-plans-include-groups"></a>Quels plans Microsoft 365 incluent des groupes ?

Tout abonnement Microsoft 365 avec Exchange Online et SharePoint Online prendra en charge les groupes. Cela inclut les plans Business Essentials et Business Premium, ainsi que les plans Entreprise E1, E3 et E5. Le groupe prend la gestion des licences de la personne qui crée le groupe (également appelée « organisateur » du groupe). Tant que l’organisateur dispose de la licence appropriée pour toutes les fonctionnalités que vous souhaitez que le groupe dispose, cette licence sera transmise au groupe.

> [!NOTE]
> Pour plus d’informations sur les familles et plans de service Microsoft 365, voir les options de [plan Microsoft 365.](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options)

Si vous disposez d’un plan Exchange uniquement, vous pouvez toujours obtenir la boîte de réception partagée et les fonctionnalités de calendrier partagé des groupes dans Outlook, mais vous n’obtenez pas la bibliothèque de documents, le Planificateur ou les autres fonctionnalités.

Les groupes Microsoft 365 fonctionnent avec Azure Active Directory. Les fonctionnalités de groupes que vous obtenez dépendent de l’abonnement Azure Active Directory dont vous disposez et des licences attribuées à l’organisateur du groupe.

> [!IMPORTANT]
> Pour toutes les fonctionnalités des groupes, si vous disposez d’un abonnement Azure AD Premium, les utilisateurs peuvent rejoindre le groupe, qu’une licence AAD P1 leur soit attribuée ou non. La gestion des licences n’est pas appliquée.
> Régulièrement, nous allons générer des rapports d’utilisation qui vous indiquent quels utilisateurs manquent une licence et en ont besoin pour être conformes aux exigences de licence. Par exemple, supposons qu’un utilisateur n’a pas de licence et qu’il est ajouté à un groupe dans lequel la stratégie d’attribution de noms est appliquée. Le rapport indique qu’il a besoin d’une licence.

## <a name="related-articles"></a>Articles connexes

[En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Mettre à niveau les listes de distribution vers groupes Microsoft 365](../manage/upgrade-distribution-lists.md)

[Gérer les groupes Microsoft 365 avec PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-groups-with-powershell)

[Limites de SharePoint Online](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)

[Organiser des groupes et des canaux dans Microsoft Stream](https://docs.microsoft.com/stream/groups-channels-organization)
