---
title: Autorisations dans le Portail Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: article
audience: Admin
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: Les administrateurs peuvent apprendre comment gérer les autorisations dans le Portail Microsoft 365 Defender pour toutes les tâches liées à la sécurité.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: bd76eed421f4d926a956508961dc44a643dbb125
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64467090"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Autorisations dans le Portail Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous devez gérer des scénarios de sécurité qui couvrent tous les services de Microsoft 365. Et vous aurez besoin de la flexibilité requise pour accorder les autorisations d’administrateur aux bonnes personnes de votre organisation.

Le Portail Microsoft 365 Defender sur <https://security.microsoft.com> prend en charge la gestion directe des autorisations pour les utilisateurs qui effectuent des tâches de sécurité dans Microsoft 365. En utilisant le Portail Microsoft 365 Defender pour la gestion des autorisations, vous pouvez gérer les autorisations de façon centralisée pour toutes les tâches liées à la sécurité.

Pour gérer les autorisations dans le Portail Microsoft 365 Defender, accédez à **Autorisations et rôles** ou <https://security.microsoft.com/securitypermissions>. Vous devez être **administrateur général** ou membre du groupe de rôles **Gestion de l’organisation** dans le Portail Microsoft 365 Defender. Plus précisément, le rôle **Gestion des rôles** permet aux utilisateurs d’afficher, de créer et de modifier des groupes de rôles dans le Portail Microsoft 365 Defender. Par défaut, ce rôle est attribué uniquement au groupe de rôles **Gestion de l’organisation**.

> [!NOTE]
> Pour obtenir des informations sur le Centre de conformité Microsoft 365, voir [Autorisations dans le Centre de conformité Microsoft 365](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation entre les membres, les rôles et les groupes de rôles

Les autorisations dans le Portail Microsoft 365 Defender sont basées sur le modèle d’autorisations du contrôle d’accès en fonction du rôle (RBAC). RBAC est le même modèle d’autorisations que celui utilisé par la plupart des services Microsoft 365. Par conséquent, si vous êtes familiarisé avec la structure d’autorisations dans ces services, l’octroi d’autorisations dans le Portail Microsoft 365 Defender vous sera très familier.

Un **rôle** accorde les autorisations nécessaires pour effectuer un ensemble de tâches.

Un **groupe de rôles** est un ensemble de rôles qui permet aux utilisateurs d’effectuer leurs tâches dans le Portail Microsoft 365 Defender.

Le portail Microsoft 365 Defender> inclut des groupes de rôles par défaut pour les tâches et fonctions les plus courantes que vous devrez attribuer. En règle générale, nous vous recommandons d’ajouter simplement des utilisateurs individuels en tant que **membres** aux groupes de rôles par défaut.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Relation d’un groupe de rôles avec ses rôles et ses membres" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Rôles et groupes de rôles dans le Portail Microsoft 365 Defender

Les types de rôles et de groupes de rôles suivants sont disponibles dans la page **Autorisations et rôles** sur <https://security.microsoft.com/securitypermissions> dans le portail Microsoft 365 Defender :

- **Rôles Azure AD** : vous pouvez afficher les rôles et les utilisateurs attribués, mais vous ne pouvez pas les gérer directement dans le Portail Microsoft 365 Defender. Les rôles Azure AD sont des rôles centraux qui attribuent des autorisations pour **tous les services** Microsoft 365.

- **Les rôles de messagerie et de collaboration** : il s’agit des mêmes groupes de rôles que ceux disponibles dans le Centre de sécurité et de conformité, mais vous pouvez les gérer directement dans le Portail Microsoft 365 Defender. Les autorisations que vous attribuez ici sont spécifiques au Portail Microsoft 365 Defender, au Centre de conformité Microsoft 365 et au Centre de sécurité et de conformité, et ne couvrent pas toutes les autorisations nécessaires dans d’autres charges de travail Microsoft 365.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="Page Autorisations et rôles du portail Microsoft 365 Defender" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Les rôles d'administration Azure AD dans le Portail Microsoft 365 Defender

Lorsque vous ouvrez le portail Microsoft 365 Defender sur <https://security.microsoft.com> et accédez à **Rôles de messagerie et de collaboration** \> **Autorisations et rôles** \> **Rôles Azure AD**\>**Rôles** (ou directement à <https://security.microsoft.com/aadpermissions>), vous verrez les rôles Azure AD décrits dans cette section.

Lorsque vous sélectionnez un rôle, un menu volant d’informations contenant la description du rôle et les attributions d’utilisateurs s’affiche. Toutefois, pour gérer ces affectations, vous devez cliquer sur **Gérer les membres dans Azure AD** dans le menu volant des détails.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="Lien permettant de gérer les autorisations dans Azure Active Directory" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

Pour plus d’informations, consultez [Affichage et attribution des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rôle|Description|
|---|---|
|**Administrateur général**|Accède à toutes les fonctionnalités d’administration de tous les services Microsoft 365. Seuls les administrateurs généraux peuvent affecter d’autres rôles d’administrateur. Pour plus d’informations, consultez la section [Administrateur Général / Administrateur d’entreprise](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrateur de conformité des données**|Effectuez un suivi des données de votre organisation dans Microsoft 365, vérifiez qu’elles sont protégées et obtenez des informations sur des problèmes pour permettre d’atténuer les risques. Pour plus d’informations, voir [Administrateur de conformité des données](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrateur de conformité**|Aide votre organisation à respecter les exigences réglementaires, gérez les cas de découverte électronique et maintenez les stratégies de gouvernance des données sur les emplacements, les identités et les applications Microsoft 365. Pour plus d’informations, voir [Administrateur de conformité](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Opérateur de sécurité**|Consulter, examiner et répondre aux menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365. Pour plus d’informations, voir la section [Opérateur de sécurité](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Lecteur de sécurité**|Consultez et examinez les menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365, mais, contrairement à l’opérateur de sécurité, il n’est pas autorisé à répondre par une action. Pour plus d’informations, voir [Lecteur de sécurité](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrateur de sécurité**|Contrôlez la sécurité globale de votre organisation en gérant les stratégies de sécurité, en examinant les analyses de la sécurité et les rapports sur les produits Microsoft 365 et en se tenant à jour sur les menaces. Pour plus d’informations, voir [Administrateur de sécurité](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Lecteur général**|Version en lecture seule du rôle **Administrateur général**. Affiche tous les paramètres et informations administratives dans Microsoft 365. Pour plus d’informations, consultez [Lecteur général](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrateur de simulation d’attaque**|Créez et gérez tous les aspects de la création d’une [simulation d’attaque](attack-simulation-training.md), le lancement/la planification d’une simulation et l’examen des résultats de la simulation. Pour plus d’informations, voir [Administrateur de simulation d’attaque](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Auteur de la charge utile d’attaque**|Créez des charges utiles d’attaque, mais ne les lancez pas ou ne planifiez pas réellement. Pour plus d’informations, consultez [Auteur de charge utile d’attaque](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Rôles de collaboration et de messagerie dans le Portail Microsoft 365 Defender

Lorsque vous ouvrez le portail Microsoft 365 Defender sur <https://security.microsoft.com> et accédez à **Rôles d’e-mail et de collaboration** \> **Autorisations et rôles** \> **Rôles de messagerie et de collaboration**\>**Rôles** (ou directement sur <https://security.microsoft.com/emailandcollabpermissions>), vous verrez les mêmes groupes de rôles disponibles dans le Centre de sécurité et de conformité.

Pour plus d’informations sur ces groupes de rôles, consultez [Autorisations dans le Centre de Sécurité et de Conformité](permissions-in-the-security-and-compliance-center.md).

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Modifier l’abonnement au rôle de collaboration et de messagerie dans le Portail Microsoft 365 Defender

1. Dans le portail Microsoft 365 Defender à <https://security.microsoft.com>, accédez à **Rôles d’e-mail et de collaboration** \> **Autorisations et rôles** \> **Rôles de messagerie et de collaboration** \> **Rôles**. Pour accéder directement à la page **autorisations**, utilisez <https://security.microsoft.com/emailandcollabpermissions>.

2. Dans la page **Autorisations**, sélectionnez le groupe de rôles que vous souhaitez modifier dans la liste. Vous pouvez cliquer sur l’en-tête de colonne **Nom** pour trier la liste par nom, ou cliquer sur **Rechercher**![Icône de recherche.](../../media/m365-cc-sc-search-icon.png) pour rechercher le groupe de rôles.

3. Dans le menu volant des détails de groupe de rôles qui s’affiche, cliquez sur **Modifier** dans la section **Membres**.

4. Dans la page **Modifier Choisir les membres** qui s’affiche, effectuez l’une des étapes suivantes :
   - S’il n’existe aucun membre de groupe de rôles, cliquez sur **Choisir des membres**.
   - S’il existe des membres de groupe de rôles, cliquez sur **Modifier**.

5. Dans la page **Choisir les membres** qui s’affiche, effectuez l’une des étapes suivantes :

   - Cliquez sur **Ajouter**. Dans la liste des utilisateurs qui s’affiche, sélectionnez un ou plusieurs utilisateurs. Vous pouvez également cliquer sur **icône Rechercher**![Recherche.](../../media/m365-cc-sc-search-icon.png) pour rechercher et sélectionner des utilisateurs.

     Une fois que vous avez sélectionné les utilisateurs que vous souhaitez ajouter, cliquez sur **Ajouter**.

   - Cliquez sur **Supprimer**. Sélectionnez un ou plusieurs des membres existants. Vous pouvez également cliquer sur **icône Rechercher**![Recherche.](../../media/m365-cc-sc-search-icon.png) pour rechercher et sélectionner des membres.

     Une fois que vous avez sélectionné les utilisateurs que vous souhaitez supprimer, cliquez sur **Supprimer**.

6. De retour dans le menu volant **Choisir des membres** , cliquez sur **Terminé**.

7. Sur le page **Modifier Choisir les membres**, cliquez sur **Sauvegarder**.

8. Dans le menu volant détails du groupe de rôles, cliquez sur **Terminé**.
