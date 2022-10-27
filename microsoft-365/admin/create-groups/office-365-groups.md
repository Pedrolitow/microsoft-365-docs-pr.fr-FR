---
title: Présentation des Groupes Microsoft 365 pour les administrateurs
ms.reviewer: arvaradh
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
description: Avec Groupes Microsoft 365, vous pouvez favoriser le travail d’équipe dans Microsoft 365 en donnant à un groupe de personnes l’accès à une collection de ressources partagées.
ms.openlocfilehash: a3501217e90d7b131621abae95450899b0b835a1
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720369"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Présentation des Groupes Microsoft 365 pour les administrateurs

Microsoft 365 Groups est le service d'adhésion fondamental qui dirige tout le travail d'équipe dans Microsoft 365. Avec Microsoft 365 Groups, vous pouvez donner à un groupe de personnes l'accès à une collection de ressources partagées. Ces ressources sont les suivantes :

- Une boîte de réception Outlook partagée
- Un calendrier partagé
- Une bibliothèque de documents SharePoint
- Un planificateur
- Un bloc-notes OneNote
- Power BI
- Yammer (si le groupe a été créé à partir de Yammer)
- Une équipe (si le groupe a été créé à partir Teams)
- Feuille de route (si vous avez Project pour le web)
- Flux

Avec un groupe Microsoft 365, vous n’avez pas besoin d’attribuer manuellement des autorisations à chacune de ces ressources. L’ajout automatique de personnes au groupe leur donne les autorisations dont ils ont besoin.

Tout utilisateur peut créer un groupe, sauf si vous [limitez la création de groupe à un ensemble spécifique de personnes](../../solutions/manage-creation-of-groups.md). Si vous limitez la création de groupes, les utilisateurs qui ne peuvent pas créer de groupes ne pourront pas créer des sites SharePoint, des planificateurs, des équipes, des calendriers de groupes Outlook, des groupes Stream, des groupes Yammer, des bibliothèques partagées dans OneDrive ou des espaces de travail Power BI partagés. Ces services nécessitent que les personnes qui les créent puissent créer un groupe. Les utilisateurs peuvent toujours participer à des activités de groupe, telles que la création de tâches dans le Planificateur ou l’utilisation d’une conversation Teams, à condition qu’ils soient membres du groupe.

Les groupes ont les rôles suivants :

- **Propriétaires** : les propriétaires de groupe peuvent ajouter ou supprimer des membres et avoir des autorisations uniques, telles que la possibilité de supprimer des conversations de la boîte de réception partagée ou de modifier différents paramètres sur le groupe. Les propriétaires de groupe peuvent renommer le groupe, mettre à jour la description ou l’image, et bien plus encore.
- **Membres** : les membres peuvent accéder à tous les paramètres du groupe, mais ne peuvent pas modifier les paramètres du groupe. Par défaut, les membres du groupe peuvent inviter des invités à rejoindre votre groupe, mais vous pouvez [contrôler ce paramètre](manage-guest-access-in-groups.md).
- **Invités** - Les invités de groupe sont des membres extérieurs à votre organisation.

Seuls les administrateurs généraux, les administrateurs d’utilisateurs et les administrateurs de groupes peuvent créer et gérer des groupes dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">Centre d'administration Microsoft 365</a>. Vous ne pouvez pas être un administrateur délégué (par exemple, consultant désigné comme administrateur).

En tant qu’administrateur, vous pouvez :

- [Spécifier qui peut créer des groupes](../../solutions/manage-creation-of-groups.md)
- [Créer une stratégie de nommage pour les groupes de votre organisation](../../solutions/groups-naming-policy.md)
- [Choisir le domaine à utiliser lors de la création d’un groupe](../../solutions/choose-domain-to-create-groups.md)
- [Gérer l’accès invité aux groupes](manage-guest-access-in-groups.md)
- [Récupérer un groupe supprimé](restore-deleted-group.md) (dans les 30 jours suivant la suppression)

Si vous préférez une méthode plus automatisée pour gérer le cycle de vie de vos groupes Microsoft 365, vous pouvez utiliser des stratégies d’expiration pour faire expirer les groupes à un intervalle de temps spécifique. Les propriétaires du groupe recevront un e-mail 30, 15 et 1 jour avant l’expiration du groupe qui leur permet de renouveler le groupe si nécessaire. Voir : [Stratégie d’expiration du groupe Microsoft 365](../../solutions/microsoft-365-groups-expiration-policy.md).

Vous pouvez administrer vos groupes à partir du Centre d'administration Microsoft 365 ou [à l’aide de PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md).

Si vous avez de nombreux utilisateurs, par exemple dans une grande entreprise ou une grande entreprise, vous pouvez avoir de nombreux utilisateurs qui créent des groupes à diverses fins. Nous vous recommandons vivement de consulter [Planifier la gouvernance dans les groupes Microsoft 365 pour connaître](../../solutions/collaboration-governance-overview.md) les meilleures pratiques.

## <a name="group-limits"></a>Limites d’un groupe

Les limites suivantes s’appliquent aux Groupes Microsoft 365 :

|Maximum...|Valeur|
|:---------|:----|
|Owners per group|100|
|Groups a user can create|250|
|Groupes qu’un administrateur peut créer|Il n’existe aucune limite spécifique au groupe Microsoft 365. Il existe une limite globale d’objets Azure AD spécifique à chaque organisation. Un administrateur Azure AD capable de gérer des groupes dans l’organisation peut créer un nombre illimité de groupes Microsoft 365 jusqu’à la limite d’objets Azure AD. Consultez [Limites et restrictions du service AAD](/active-directory/enterprise-users/directory-service-limits-restrictions).|
|Nombre de membres|Plus de 1 000 personnes, mais seulement 1 000 peuvent accéder simultanément aux conversations de groupe. <br>Les utilisateurs peuvent remarquer des retards lors de l’accès au calendrier et aux conversations dans de grands groupes dans Outlook.|
|Nombre de groupes dont un utilisateur peut être membre|7,000|
|Stockage de fichiers|1 téraoctet + 10 Go par utilisateur abonné + tout autre stockage acheté. Vous pouvez acheter une quantité illimitée de stockage supplémentaire.|
|Taille de boîte aux lettres du groupe|50 Go|


La gestion de vos groupes Microsoft 365 est plus efficace lorsque vous disposez d’informations exploitables sur l’utilisation des groupes. L’Centre d'administration Microsoft 365 dispose d’un outil de création de rapports qui vous permet de voir l’utilisation du stockage, le nombre de groupes actifs dont vous disposez et la façon dont les utilisateurs utilisent les groupes. Pour plus d’informations, consultez [Rapports Microsoft 365 dans le Centre d’administration](../activity-reports/office-365-groups.md) .

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Vous pouvez créer des étiquettes de confidentialité que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un groupe Microsoft 365. Avec les étiquettes de confidentialité, vous pouvez configurer : 

- Confidentialité (publique ou privée)
- Accès des utilisateurs externes
- Accès aux appareils non gérés

Par exemple, vous pouvez créer une étiquette appelée *Hautement confidentiel* et spécifier que tout groupe créé avec cette étiquette sera privé et n’autorisera pas les utilisateurs externes. Lorsque les utilisateurs de votre organisation sélectionnent cette étiquette lors de la création du groupe, le groupe est défini sur privé et les membres du groupe ne sont pas autorisés à ajouter des utilisateurs externes au groupe.

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, elles ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois les étiquettes de confidentialité activées. 

Pour plus d’informations sur la création, la gestion et l’utilisation d’étiquettes de confidentialité, voir [Utiliser des étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint](../../compliance/sensitivity-labels-teams-groups-sites.md).

## <a name="which-microsoft-365-plans-include-groups"></a>Quels plans Microsoft 365 incluent des groupes ?

Tout abonnement Microsoft 365 qui a Exchange Online et SharePoint Online prend en charge les groupes. Cela inclut les plans Business Essentials et Business Premium, ainsi que les plans Enterprise E1, E3 et E5. Le groupe accepte la licence de la personne qui crée le groupe (également appelée « organisateur » du groupe). Tant que l’organisateur dispose de la licence appropriée pour les fonctionnalités que vous souhaitez que le groupe ait, cette licence est transmise au groupe.

> [!NOTE]
> Pour plus d’informations sur les familles et les plans de service Microsoft 365, consultez [Options de plan Microsoft 365](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).

Si vous disposez d’un plan Exchange uniquement, vous pouvez toujours obtenir les fonctionnalités de boîte de réception partagée et de calendrier partagé des groupes dans Outlook, mais vous n’obtiendrez pas la bibliothèque de documents, le Planificateur ou l’une des autres fonctionnalités.

Les groupes Microsoft 365 fonctionnent avec Azure Active Directory. Les fonctionnalités de groupes que vous obtenez dépendent de l’abonnement Azure Active Directory dont vous disposez et des licences attribuées à l’organisateur du groupe.

> [!IMPORTANT]
> Pour toutes les fonctionnalités de groupes, si vous disposez d’un abonnement Azure AD Premium, les utilisateurs peuvent rejoindre le groupe, qu’ils aient ou non une licence AAD P1 qui leur soit affectée. La gestion des licences n’est pas appliquée.
> Régulièrement, nous générerons des rapports d’utilisation qui vous indiquent quels utilisateurs ne disposent pas d’une licence, et nous avons besoin qu’une licence leur soit attribuée pour être conforme aux exigences de licence. Par exemple, supposons qu’un utilisateur n’a pas de licence et qu’il soit ajouté à un groupe où la stratégie de nommage est appliquée. Le rapport vous indique qu’ils ont besoin d’une licence.

## <a name="related-content"></a>Contenu associé

[En savoir plus sur Groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2) (article)\
[Mettre à niveau les listes de distribution vers Groupes Microsoft 365](../manage/upgrade-distribution-lists.md) (article)\
[Gérer Groupes Microsoft 365 avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (article)\
[Limites de SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) (article)\
[Organiser des groupes et des canaux dans Microsoft Stream](/stream/groups-channels-organization) (article)
