---
title: Autorisations dans le Portail Microsoft 365 Defender
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
ms.audience: Admin
ms.topic: conceptual
audience: Admin
ms.localizationpriority: high
ms.collection:
- m365-security
search.appverid:
- MOE150
- MET150
description: Les administrateurs peuvent apprendre comment gérer les autorisations dans le Portail Microsoft 365 Defender pour toutes les tâches liées à la sécurité.
ms.custom:
- seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 10cbbb5c374e75b9bf16430de1b478fa5ee320d4
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68815526"
---
# <a name="permissions-in-the-microsoft-365-defender-portal"></a>Autorisations dans le Portail Microsoft 365 Defender

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Vous devez gérer des scénarios de sécurité qui couvrent tous les services de Microsoft 365. Et vous aurez besoin de la flexibilité requise pour accorder les autorisations d’administrateur aux bonnes personnes de votre organisation.

Le Portail Microsoft 365 Defender sur <https://security.microsoft.com> prend en charge la gestion directe des autorisations pour les utilisateurs qui effectuent des tâches de sécurité dans Microsoft 365. En utilisant le Portail Microsoft 365 Defender pour la gestion des autorisations, vous pouvez gérer les autorisations de façon centralisée pour toutes les tâches liées à la sécurité.

Pour gérer les autorisations dans le Portail Microsoft 365 Defender, accédez à **Autorisations et rôles** ou <https://security.microsoft.com/securitypermissions>. Vous devez être **administrateur général** ou membre du groupe de rôles **Gestion de l’organisation** dans le Portail Microsoft 365 Defender. Plus précisément, le rôle **Gestion des rôles** permet aux utilisateurs d’afficher, de créer et de modifier des groupes de rôles dans le Portail Microsoft 365 Defender. Par défaut, ce rôle est attribué uniquement au groupe de rôles **Gestion de l’organisation**.

> [!NOTE]
> Pour plus d’informations sur les autorisations dans le portail de conformité Microsoft Purview, consultez [Autorisations dans le portail de conformité Microsoft Purview](../../compliance/microsoft-365-compliance-center-permissions.md).

## <a name="relationship-of-members-roles-and-role-groups"></a>Relation entre les membres, les rôles et les groupes de rôles

Les autorisations dans le Portail Microsoft 365 Defender sont basées sur le modèle d’autorisations du contrôle d’accès en fonction du rôle (RBAC). RBAC est le même modèle d’autorisations que celui utilisé par la plupart des services Microsoft 365. Par conséquent, si vous êtes familiarisé avec la structure d’autorisations dans ces services, l’octroi d’autorisations dans le Portail Microsoft 365 Defender vous sera très familier.

Un **rôle** accorde les autorisations nécessaires pour effectuer un ensemble de tâches.

Un **groupe de rôles** est un ensemble de rôles qui permet aux utilisateurs d’effectuer leurs tâches dans le Portail Microsoft 365 Defender.

The Microsoft 365 Defender portal> includes default role groups for the most common tasks and functions that you'll need to assign. Generally, we recommend simply adding individual users as **members** to the default role groups.

:::image type="content" source="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png" alt-text="Relation d’un groupe de rôles avec ses rôles et ses membres" lightbox="../../media/2a16d200-968c-4755-98ec-f1862d58cb8b.png":::

## <a name="roles-and-role-groups-in-the-microsoft-365-defender-portal"></a>Rôles et groupes de rôles dans le Portail Microsoft 365 Defender

Les types de rôles et de groupes de rôles suivants sont disponibles dans la page **Autorisations et rôles** sur <https://security.microsoft.com/securitypermissions> dans le portail Microsoft 365 Defender :

- **Rôles Azure AD** : vous pouvez afficher les rôles et les utilisateurs attribués, mais vous ne pouvez pas les gérer directement dans le Portail Microsoft 365 Defender. Les rôles Azure AD sont des rôles centraux qui attribuent des autorisations pour **tous les services** Microsoft 365.

- **Email & rôles de collaboration** : vous pouvez afficher et gérer ces groupes de rôles directement dans le portail Microsoft 365 Defender. Ces autorisations sont spécifiques au portail Microsoft 365 Defender et au portail de conformité Microsoft Purview, et ne couvrent pas toutes les autorisations nécessaires dans les autres charges de travail Microsoft 365.

:::image type="content" source="../../media/m365-sc-permissions-and-roles-page.png" alt-text="Page Autorisations et rôles du portail Microsoft 365 Defender" lightbox="../../media/m365-sc-permissions-and-roles-page.png":::

### <a name="azure-ad-roles-in-the-microsoft-365-defender-portal"></a>Les rôles d'administration Azure AD dans le Portail Microsoft 365 Defender

Lorsque vous ouvrez le portail Microsoft 365 Defender sur <https://security.microsoft.com> et accédez à **Rôles de messagerie et de collaboration** \> **Autorisations et rôles** \> **Rôles Azure AD**\>**Rôles** (ou directement à <https://security.microsoft.com/aadpermissions>), vous verrez les rôles Azure AD décrits dans cette section.

Lorsque vous sélectionnez un rôle, un menu volant d’informations contenant la description du rôle et les attributions d’utilisateurs s’affiche. Toutefois, pour gérer ces affectations, vous devez cliquer sur **Gérer les membres dans Azure AD** dans le menu volant des détails.

:::image type="content" source="../../media/permissions-manage-in-azure-ad-link.png" alt-text="Lien permettant de gérer les autorisations dans Azure Active Directory" lightbox="../../media/permissions-manage-in-azure-ad-link.png":::

Pour plus d’informations, consultez [Affichage et attribution des rôles d’administrateur dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-manage-roles-portal).

|Rôle|Description|
|---|---|
|**Administrateur général**|Accède à toutes les fonctionnalités d’administration de tous les services Microsoft 365. Seuls les administrateurs généraux peuvent affecter d’autres rôles d’administrateur. Pour plus d’informations, consultez la section [Administrateur Général / Administrateur d’entreprise](/azure/active-directory/roles/permissions-reference#global-administrator--company-administrator).|
|**Administrateur de conformité des données**|Keep track of your organization's data across Microsoft 365, make sure it's protected, and get insights into any issues to help mitigate risks. For more information, see [Compliance Data Administrator](/azure/active-directory/roles/permissions-reference#compliance-data-administrator).|
|**Administrateur de conformité**|Help your organization stay compliant with any regulatory requirements, manage eDiscovery cases, and maintain data governance policies across Microsoft 365 locations, identities, and apps. For more information, see [Compliance Administrator](/azure/active-directory/roles/permissions-reference#compliance-administrator).|
|**Opérateur de sécurité**|Consulter, examiner et répondre aux menaces actives envers vos utilisateurs, appareils et contenus Microsoft 365. Pour plus d’informations, voir la section [Opérateur de sécurité](/azure/active-directory/roles/permissions-reference#security-operator).|
|**Lecteur de sécurité**|View and investigate active threats to your Microsoft 365 users, devices, and content, but (unlike the Security operator) they do not have permissions to respond by taking action. For more information, see [Security Reader](/azure/active-directory/roles/permissions-reference#security-reader).|
|**Administrateur de sécurité**|Control your organization's overall security by managing security policies, reviewing security analytics and reports across Microsoft 365 products, and staying up-to-speed on the threat landscape. For more information, see [Security Administrator](/azure/active-directory/roles/permissions-reference#security-administrator).|
|**Lecteur général**|Version en lecture seule du rôle **Administrateur général**. Affiche tous les paramètres et informations administratives dans Microsoft 365. Pour plus d’informations, consultez [Lecteur général](/azure/active-directory/roles/permissions-reference#global-reader).|
|**Administrateur de simulation d’attaque**|Create and manage all aspects of [attack simulation](attack-simulation-training.md) creation, launch/scheduling of a simulation, and the review of simulation results. For more information, see [Attack Simulation Administrator](/azure/active-directory/roles/permissions-reference#attack-simulation-administrator).|
|**Auteur de la charge utile d’attaque**|Créez des charges utiles d’attaque, mais ne les lancez pas ou ne planifiez pas réellement. Pour plus d’informations, consultez [Auteur de charge utile d’attaque](/azure/active-directory/roles/permissions-reference#attack-payload-author).|

### <a name="email--collaboration-roles-in-the-microsoft-365-defender-portal"></a>Rôles de collaboration et de messagerie dans le Portail Microsoft 365 Defender

Dans le portail Microsoft 365 Defender à <https://security.microsoft.com> \> **Email &** page \> Rôles de collaboration \> **Autorisations & rôles** Email & rôles de **collaboration** \> **Rôles** (ou directement sur <https://security.microsoft.com/emailandcollabpermissions>), vous verrez les mêmes groupes de rôles que disponibles dans le portail de conformité Microsoft Purview à l’adresse <https://compliance.microsoft.com> \> \> **Page Autorisations des**  **solutions** \> Microsoft Purview Rôles (ou directement à l’adresse <https://compliance.microsoft.com/compliancecenterpermissions>).

Pour plus d’informations sur ces groupes de rôles, consultez [Rôles et groupes de rôles dans les portails de conformité Microsoft 365 Defender et Microsoft Purview](permissions-in-the-security-and-compliance-center.md)

#### <a name="modify-email--collaboration-role-membership-in-the-microsoft-365-defender-portal"></a>Modifier l’abonnement au rôle de collaboration et de messagerie dans le Portail Microsoft 365 Defender

1. In the Microsoft 365 Defender portal at <https://security.microsoft.com>, go to **Email & collaboration roles** \> **Permissions & roles** \> **Email & collaboration roles** \> **Roles**. To go directly to the **Permissions** page, use <https://security.microsoft.com/emailandcollabpermissions>.

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
