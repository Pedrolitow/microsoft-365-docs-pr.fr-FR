---
title: Présentation des Groupes Microsoft 365 pour les administrateurs
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
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
description: Découvrez les groupes Microsoft 365.
ms.openlocfilehash: 711ab7e7818b266d7cbdbe076e30355d29bc3eeb
ms.sourcegitcommit: 555d756c69ac9031d1fb928f2e1f9750beede066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47307264"
---
# <a name="overview-of-microsoft-365-groups-for-administrators"></a>Présentation des Groupes Microsoft 365 pour les administrateurs

Microsoft 365 groups est le service d’appartenance de base qui dirige tout le travail d’équipe dans Microsoft 365. Avec les groupes Microsoft 365, vous pouvez donner à un groupe de personnes l’accès à une collection de ressources de collaboration que ces personnes peuvent partager. Ces ressources sont les suivantes :

- Boîte de réception Outlook partagée
- Un calendrier partagé
- Une bibliothèque de documents SharePoint
- Un planificateur
- Un bloc-notes OneNote
- Power BI
- Yammer (si le groupe a été créé à partir de Yammer)
- Une équipe (si le groupe a été créé à partir de Teams)
- Feuille de route (si vous avez Project pour le Web)

Avec un groupe Microsoft 365, vous n’avez pas besoin d’attribuer manuellement des autorisations à chacune de ces ressources, car l’ajout de personnes au groupe leur accorde automatiquement les autorisations dont ils ont besoin pour les outils fournis par le groupe.

Tout utilisateur peut créer un groupe, sauf si vous [Limitez la création de groupe à un ensemble spécifique de personnes](manage-creation-of-groups.md). Notez que si vous limitez la création de groupe, les utilisateurs qui ne peuvent pas créer de groupes ne seront pas en mesure de créer des sites, des planificateurs ou des équipes SharePoint. Ces services nécessitent que les personnes qui les créent soient en mesure de créer un groupe. Les utilisateurs peuvent toujours participer à des activités de groupe, telles que la création de tâches dans le planificateur ou l’utilisation de la conversation Teams, à condition qu’ils soient membres du groupe.

Les groupes ont les rôles suivants :

- **Propriétaires** : les propriétaires de groupe peuvent ajouter ou supprimer des membres et avoir des autorisations uniques, telles que la possibilité de supprimer des conversations de la boîte de réception partagée ou de modifier des paramètres différents sur le groupe. Les propriétaires de groupe peuvent renommer le groupe, mettre à jour la description ou l’image, et plus encore.
- **Membres** : les membres peuvent accéder à tous les éléments du groupe, mais ils ne peuvent pas modifier les paramètres du groupe. Par défaut, les membres du groupe peuvent inviter des invités à rejoindre votre groupe, bien que vous puissiez [contrôler ce paramètre](manage-guest-access-in-groups.md).
- **Invités** : les invités de groupe sont membres de l’extérieur de votre organisation.

Seuls les administrateurs généraux, les administrateurs d’utilisateurs et les administrateurs de groupes peuvent créer et gérer des groupes dans le centre d’administration Microsoft 365. Vous ne pouvez pas être un administrateur délégué (par exemple, consultant désigné comme administrateur).

En tant qu’administrateur, vous pouvez :

- [Spécifier qui peut créer des groupes](manage-creation-of-groups.md)
- [Créer une stratégie d’attribution de noms pour les groupes de votre organisation](groups-naming-policy.md)
- [Choisir le domaine à utiliser lors de la création d’un groupe](choose-domain-to-create-groups.md)
- [Gérer l’accès invité aux groupes](manage-guest-access-in-groups.md)
- [Récupérer un groupe supprimé](restore-deleted-group.md) (dans les 30 jours suivant la suppression)

Si vous préférez un moyen plus automatisé de gérer le cycle de vie de vos groupes Microsoft 365, vous pouvez utiliser des stratégies d’expiration pour faire expirer les groupes à un intervalle de temps spécifique. Les propriétaires du groupe reçoivent un message électronique 30, 15 et 1 jour avant l’expiration du groupe qui leur permet de renouveler facilement le groupe s’il est toujours nécessaire. Consultez la rubrique relative à la [stratégie d’expiration de groupe Microsoft 365](office-365-groups-expiration-policy.md).

Vous pouvez administrer vos groupes à partir du centre d’administration 365 de Microsoft ou à [l’aide de PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-groups-with-powershel).

Si vous avez un grand nombre d’utilisateurs, comme dans une grande entreprise ou entreprise, vous pouvez avoir de nombreux utilisateurs qui créent des groupes à diverses fins. Nous vous recommandons vivement de consulter le [plan de gouvernance dans les groupes Microsoft 365](plan-for-groups-governance.md) pour obtenir les meilleures pratiques.

## <a name="group-limits"></a>Limites des groupes

Les limites suivantes s’appliquent aux groupes Microsoft 365 :

|Maximum...|Valeur|
|:---------|:----|
|Owners per group|100|
|Groups a user can create|250|
|Groupes qu’un administrateur peut créer|Nombre maximal de 500 000 par défaut pour le client|
|Nombre de membres|Plus de 1 000, même si seulement 1 000 peut accéder aux conversations de groupe simultanément. <br>Les utilisateurs peuvent remarquer des retards lors de l’accès au calendrier et aux conversations dans des groupes très volumineux dans Outlook.|
|Nombre de groupes dont un utilisateur peut être membre|1,000|
|Stockage de fichiers|1 téraoctet + 10 Go par utilisateur abonné + tout stockage supplémentaire acheté. Vous pouvez acheter une quantité illimitée de stockage supplémentaire.|
|Taille de la boîte aux lettres de groupe|50 Go|

Le nombre maximal par défaut de groupes Microsoft 365 qu’une organisation peut avoir est 500 000. Pour aller au-delà de la limite par défaut, vous devez contacter le support Microsoft. Pour plus d’informations sur les limites des groupes Microsoft 365, consultez la rubrique [groupes microsoft 365-aide de l’administrateur](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

La gestion de vos groupes Microsoft 365 est plus efficace lorsque vous disposez d’informations sur l’utilisation des groupes. Le centre d’administration Microsoft 365 dispose d’un outil de création de rapports qui vous permet de voir des éléments tels que l’utilisation du stockage, le nombre de groupes actifs dont vous disposez et même le mode d’utilisation des groupes par vos utilisateurs. Pour plus d’informations, reportez-vous à [la rubrique rapports Microsoft 365 dans le centre d’administration](../activity-reports/office-365-groups.md) .

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Vous pouvez créer des étiquettes de confidentialité que les utilisateurs de votre organisation peuvent définir lors de la création d’un groupe Microsoft 365. Avec les étiquettes de confidentialité, vous pouvez configurer les éléments suivants : 

- Confidentialité (publique ou privée)
- Accès des utilisateurs externes
- Accès aux appareils non gérés

Par exemple, vous pouvez créer une étiquette appelée *hautement confidentiel* et spécifier que tout groupe créé avec cette étiquette sera privé et non autoriser les utilisateurs externes. Lorsque les utilisateurs de votre organisation sélectionnent cette étiquette lors de la création d’un groupe, le groupe est défini sur privé et les membres du groupe ne sont pas autorisés à ajouter des utilisateurs externes au groupe.

> [!IMPORTANT]
> Si vous utilisez actuellement des étiquettes de classification, ces derniers ne seront plus disponibles pour les utilisateurs qui créent des groupes une fois que les étiquettes de sensibilité seront activées. 

Pour plus d’informations sur la création, la gestion et l’utilisation des étiquettes de confidentialité, voir [use sensitive labels to Protect content in Microsoft Teams, microsoft 365 Groups et SharePoint sites](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites).

## <a name="which-microsoft-365-plans-include-groups"></a>Quels sont les plans Microsoft 365 qui incluent des groupes ?

Tout abonnement Microsoft 365 avec Exchange Online et SharePoint Online prend en charge les groupes. Cela inclut les plans Business Essentials et Business Premium, ainsi que les plans entreprise E1, E3 et E5. Le groupe prend en la gestion des licences de la personne qui crée le groupe (également appelée « organisateur » du groupe). Tant que l’organisateur dispose de la licence appropriée pour toutes les fonctionnalités que vous souhaitez affecter au groupe, cette licence sera acheminée vers le groupe.

> [!NOTE]
> Pour plus d’informations sur les familles et plans de service Microsoft 365, consultez les [options de plan de microsoft 365](https://docs.microsoft.com/office365/servicedescriptions/office-365-platform-service-description/office-365-plan-options).

Si vous avez un plan Exchange uniquement, vous pouvez toujours obtenir la boîte de réception partagée et les fonctionnalités de calendrier partagé des groupes dans Outlook, mais vous n’obtiendrez pas la bibliothèque de documents, le planificateur ou l’une des autres fonctionnalités.

Les groupes Microsoft 365 fonctionnent avec Azure Active Directory (AAD). Les groupes dont vous disposez dépendent de l’abonnement Azure Active Directory dont vous disposez et de la ou des licences affectées à l’organisateur du groupe.

> [!IMPORTANT]
> Pour toutes les fonctionnalités de groupe, si vous disposez d’un abonnement Azure AD Premium, les utilisateurs peuvent rejoindre le groupe, qu’ils disposent ou non d’une licence AAD P1 qui leur est attribuée. La gestion des licences n’est pas appliquée.
> Périodiquement, nous générons des rapports d’utilisation qui vous indiquent quels utilisateurs ne disposent pas d’une licence et qu’ils ont besoin d’une licence pour être conformes aux exigences en matière de licences. Par exemple, imaginons qu’un utilisateur ne dispose pas d’une licence et qu’il est ajouté à un groupe dans lequel la stratégie de noms est appliquée. Le rapport vous signale qu’il a besoin d’une licence.

## <a name="related-articles"></a>Articles connexes

[En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Mettre à niveau les listes de distribution vers des groupes Microsoft 365](../manage/upgrade-distribution-lists.md)

[Gérer les groupes Microsoft 365 avec PowerShell](https://docs.microsoft.com/microsoft-365/enterprise/manage-microsoft-365-groups-with-powershell)

[Limites de SharePoint Online](https://docs.microsoft.com/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits)
