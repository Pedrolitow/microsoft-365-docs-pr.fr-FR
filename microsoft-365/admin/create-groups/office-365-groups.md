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
ms.localizationpriority: medium
ms.collection:
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
description: Avec Microsoft 365 groupes, vous pouvez piloter le travail d’équipe dans Microsoft 365 en donnant à un groupe de personnes l’accès à une collection de ressources partagées.
ms.openlocfilehash: 5aaf7598f3591efb330618f0be98ea3376816eca
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60165735"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Présentation des Groupes Microsoft 365 pour les administrateurs

Microsoft 365 Les groupes sont le service d’appartenance de base qui dirige tout le travail d’équipe dans Microsoft 365. Avec Microsoft 365 groupes, vous pouvez accorder à un groupe de personnes l’accès à une collection de ressources partagées. Ces ressources sont les suivantes :

- Une boîte de Outlook partagée
- Un calendrier partagé
- Bibliothèque SharePoint documents
- Un planificateur
- Un bloc-notes OneNote
- Power BI
- Yammer (si le groupe a été créé à partir de Yammer)
- Une équipe (si le groupe a été créé à partir Teams)
- Feuille de route (si vous avez Project pour le web)
- Stream

Avec un Microsoft 365, vous n’avez pas besoin d’attribuer manuellement des autorisations à chacune de ces ressources. L’ajout automatique de personnes au groupe leur donne les autorisations dont ils ont besoin.

Tout utilisateur peut créer un groupe, sauf si vous limitez la création de groupe [à un ensemble spécifique de personnes.](../../solutions/manage-creation-of-groups.md) Si vous limitez la création de groupes, les utilisateurs qui ne peuvent pas créer de groupes ne pourront pas créer de sites SharePoint, de planificateurs, d’équipes, de calendriers de groupe Outlook, de groupes de flux, de groupes Yammer, de bibliothèques partagées dans OneDrive ou d’espaces de travail Power BI partagés. Ces services nécessitent que les personnes qui les créent puissent créer un groupe. Les utilisateurs peuvent toujours participer à des activités de groupe, telles que la création de tâches dans le Planificateur ou l’utilisation de Teams conversation, à condition qu’ils soient membres du groupe.

Les groupes ont les rôles suivants :

- **Propriétaires** : les propriétaires de groupe peuvent ajouter ou supprimer des membres et avoir des autorisations uniques, telles que la possibilité de supprimer des conversations de la boîte de réception partagée ou de modifier différents paramètres sur le groupe. Les propriétaires de groupe peuvent renommer le groupe, mettre à jour la description ou l’image, etc.
- **Membres** : les membres peuvent accéder à tous les paramètres du groupe, mais ne peuvent pas modifier les paramètres du groupe. Par défaut, les membres du groupe peuvent inviter des invités à rejoindre votre groupe, même si vous pouvez [contrôler ce paramètre.](manage-guest-access-in-groups.md)
- **Invités** : les invités de groupe sont des membres extérieurs à votre organisation.

Seuls les administrateurs globaux, les administrateurs d’utilisateurs et les administrateurs de groupes peuvent créer et gérer des groupes dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">le Centre d'administration Microsoft 365</a>. Vous ne pouvez pas être un administrateur délégué (par exemple, consultant désigné comme administrateur).

En tant qu’administrateur, vous pouvez :

- [Spécifier qui peut créer des groupes](../../solutions/manage-creation-of-groups.md)
- [Créer une stratégie d’attribution de noms pour les groupes de votre organisation](../../solutions/groups-naming-policy.md)
- [Choisir le domaine à utiliser lors de la création d’un groupe](../../solutions/choose-domain-to-create-groups.md)
- [Gérer l’accès invité aux groupes](manage-guest-access-in-groups.md)
- [Récupérer un groupe supprimé](restore-deleted-group.md) (dans les 30 jours suivant la suppression)

Si vous préférez une façon plus automatisée de gérer le cycle de vie de vos groupes Microsoft 365, vous pouvez utiliser des stratégies d’expiration pour expirer des groupes à un intervalle de temps spécifique. Les propriétaires du groupe obtiennent un courrier électronique 30, 15 et 1 jour avant l’expiration du groupe qui leur permet de renouveler le groupe s’il est toujours nécessaire. Voir : Microsoft 365 [d’expiration de groupe.](../../solutions/microsoft-365-groups-expiration-policy.md)

Vous pouvez administrer vos groupes à partir du Centre d'administration Microsoft 365 ou à [l’aide de PowerShell.](../../enterprise/manage-microsoft-365-groups-with-powershell.md)

Si vous avez de nombreux utilisateurs, par exemple dans une grande entreprise ou une grande entreprise, il se peut que de nombreux utilisateurs créent des groupes à diverses fins. Nous vous recommandons vivement d’examiner [le Plan de gouvernance dans Microsoft 365 groupes pour](../../solutions/collaboration-governance-overview.md) les meilleures pratiques.

## <a name="group-limits"></a>Limites d’un groupe

Les limites suivantes s’appliquent Microsoft 365 groupes :

|Maximum...|Valeur|
|:---------|:----|
|Owners per group|100|
|Groups a user can create|250|
|Groupes qu’un administrateur peut créer|Limite de client par défaut maximale de 500 K|
|Nombre de membres|Plus de 1 000, mais seuls 1 000 peuvent accéder simultanément aux conversations de groupe. <br>Les utilisateurs peuvent remarquer des retards lors de l’accès au calendrier et aux conversations dans de grands groupes Outlook.|
|Nombre de groupes dont un utilisateur peut être membre|7,000|
|Stockage de fichiers|1 téraoctet + 10 Go par utilisateur abonné + tout autre stockage acheté. Vous pouvez acheter une quantité illimitée de stockage supplémentaire.|
|Taille de la boîte aux lettres de groupe|50 Go|

Le nombre maximal de groupes Microsoft 365 par défaut qu’une organisation peut avoir est de 500 000. Pour aller au-delà de la limite par défaut, vous devez contacter le Support Microsoft. Pour plus d’informations sur Microsoft 365 limites des groupes, voir groupes [Microsoft 365 - Aide de l’administrateur.](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

La gestion de Microsoft 365 groupes est plus efficace lorsque vous avez des informations actionnables sur l’utilisation des groupes. Le Centre d'administration Microsoft 365 dispose d’un outil de rapports qui vous permet de voir l’utilisation du stockage, le nombre de groupes actifs dont vous disposez et la façon dont les utilisateurs utilisent les groupes. Voir : [Microsoft 365 rapports dans le Centre d’administration pour](../activity-reports/office-365-groups.md) plus d’informations.

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Vous pouvez créer des étiquettes de niveau de sensibilité que les utilisateurs de votre organisation peuvent définir lorsqu’ils créent un Microsoft 365 de données. Avec les étiquettes de niveau de sensibilité, vous pouvez configurer : 

- Confidentialité (publique ou privée)
- Accès des utilisateurs externes
- Accès aux appareils nonmanagés

Par exemple, vous pouvez créer une étiquette appelée *Hautement* confidentiel et spécifier que tout groupe créé avec cette étiquette sera privé et n’autorisera pas les utilisateurs externes. Lorsque les utilisateurs de votre organisation sélectionnent cette étiquette lors de la création du groupe, le groupe est définie sur privé et les membres du groupe ne sont pas autorisés à ajouter des utilisateurs externes au groupe.

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, elles ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois les étiquettes de niveau de sensibilité activées. 

Pour plus d’informations sur la création, la gestion et l’utilisation d’étiquettes de sensibilité, voir Utiliser des étiquettes de niveau de sensibilité pour protéger le contenu dans Microsoft Teams, Microsoft 365 groupes et [sites SharePoint sites.](../../compliance/sensitivity-labels-teams-groups-sites.md)

## <a name="which-microsoft-365-plans-include-groups"></a>Quels plans Microsoft 365 les groupes sont-ils inclus ?

Tout abonnement Microsoft 365 qui dispose de Exchange Online et SharePoint Online prendra en charge les groupes. Cela inclut les plans Business Essentials et Business Premium, ainsi que les plans Enterprise E1, E3 et E5. Le groupe prend la gestion des licences de la personne qui crée le groupe (également appelée « organisateur » du groupe). Tant que l’organisateur dispose de la licence appropriée pour toutes les fonctionnalités que vous souhaitez que le groupe dispose, cette licence sera transmise au groupe.

> [!NOTE]
> Pour plus d’informations sur Microsoft 365 et les plans de service, voir [Microsoft 365 options de plan.](/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options)

Si vous disposez d’un plan Exchange uniquement, vous pouvez toujours obtenir la boîte de réception partagée et les fonctionnalités de calendrier partagé des groupes dans Outlook mais vous n’obtenez pas la bibliothèque de documents, le Planificateur ou les autres fonctionnalités.

Microsoft 365 groupes fonctionnent avec Azure Active Directory. Les fonctionnalités de groupes que vous obtenez dépendent de Azure Active Directory abonnement dont vous disposez et des licences attribuées à l’organisateur du groupe.

> [!IMPORTANT]
> Pour toutes les fonctionnalités de groupes, si vous disposez d’un abonnement Azure AD Premium, les utilisateurs peuvent rejoindre le groupe, qu’une licence AAD P1 leur soit attribuée ou non. La gestion des licences n’est pas appliquée.
> Régulièrement, nous allons générer des rapports d’utilisation qui vous indiquent quels utilisateurs manquent une licence et en ont besoin pour être conformes aux exigences de licence. Par exemple, supposons qu’un utilisateur n’a pas de licence et qu’il est ajouté à un groupe dans lequel la stratégie d’attribution de noms est appliquée. Le rapport indique qu’il a besoin d’une licence.

## <a name="related-content"></a>Contenu associé

[En savoir plus sur Microsoft 365 groupes](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2) de travail (article)\
[Mettre à niveau les listes](../manage/upgrade-distribution-lists.md) de distribution Microsoft 365 Groupes de distribution (article)\
[Gérer Microsoft 365 groupes avec PowerShell](../../enterprise/manage-microsoft-365-groups-with-powershell.md) (article)\
[SharePoint Online Limits](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits) (article)\
[Organiser des groupes et des canaux dans Microsoft Stream](/stream/groups-channels-organization) (article)
