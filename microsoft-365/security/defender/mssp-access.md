---
title: Fournir un accès au fournisseur de services de sécurité gérés (MSSP)
description: En savoir plus sur les modifications apportées Centre de sécurité Microsoft Defender au portail Microsoft 365 Defender web
keywords: Getting started with the Microsoft 365 Defender portal, Microsoft Defender for Office 365, Microsoft Defender for Endpoint, MDO, MDE, single pane of glass, converged portal, security portal, defender security portal
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
manager: dansimp
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.openlocfilehash: f0148a8bfe18c7636e95ceae7b268cc70b2e58ed
ms.sourcegitcommit: 3b8e009ea1ce928505b8fc3b8926021fb91155f3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/28/2022
ms.locfileid: "64500413"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Fournir un accès au fournisseur de services de sécurité gérés (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Pour implémenter une solution d’accès délégué multi-locataire, prenez les mesures suivantes :

1. [Activez le contrôle d’accès](/windows/security/threat-protection/microsoft-defender-atp/rbac) basé sur les rôles pour Defender pour le point de terminaison via le portail Microsoft 365 Defender et connectez-vous à des groupes Azure Active Directory (Azure AD).

2. Configurer des [packages d’accès de gouvernance pour](/azure/active-directory/governance/identity-governance-overview) la demande d’accès et l’approvisionnement.

3. Gérer les demandes d’accès et les audits [dans Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Activer les contrôles d’accès basés sur les rôles dans Microsoft Defender pour le point de terminaison dans Microsoft 365 Defender portail

1. **Créer des groupes d’accès pour les ressources MSSP dans Customer AAD: Groups**

    Ces groupes seront liés aux rôles que vous créez dans Defender for Endpoint dans Microsoft 365 Defender portail. Pour ce faire, dans le client AD client, créez trois groupes. Dans notre exemple d’approche, nous créons les groupes suivants :

    - Analyste de niveau 1
    - Analyste de niveau 2
    - Approuveurs d’analyste MSSP  

2. Créez des rôles Defender pour les points de terminaison pour les niveaux d’accès appropriés dans Customer Defender for Endpoint Microsoft 365 Defender rôles et groupes portail.

    Pour activer RBAC dans le portail d’Microsoft 365 Defender du client, accédez aux **autorisations > Rôles points de terminaison & groupes > Rôles** avec un compte d’utilisateur avec des droits d’administrateur général ou d’administrateur de sécurité.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Détails de l’accès MSSP dans le portail Microsoft 365 Defender" lightbox="../../media/mssp-access.png":::

    Ensuite, créez des rôles RBAC pour répondre aux besoins du niveau SOC MSSP. Lier ces rôles aux groupes d’utilisateurs créés via « Groupes d’utilisateurs affectés ».

    Deux rôles possibles :

    - **Analystes de niveau 1** <br>
      Effectuez toutes les actions à l’exception de la réponse en direct et gérez les paramètres de sécurité.

    - **Analystes de niveau 2** <br>
      Fonctionnalités de niveau 1 avec ajout à la [réponse en direct](/windows/security/threat-protection/microsoft-defender-atp/live-response)

    Pour plus d’informations, voir [Utiliser le contrôle d’accès basé sur un rôle](/windows/security/threat-protection/microsoft-defender-atp/rbac).

## <a name="configure-governance-access-packages"></a>Configurer les packages d’accès de gouvernance

1. **Ajouter MSSP en tant qu’organisation connectée dans customer AAD : Identity Governance**

    L’ajout du MSSP en tant qu’organisation connectée permettra au MSSP de demander et de mettre en service des accès. 

    Pour ce faire, dans le client AD client, accédez à Gouvernance des identités : Organisation connectée. Ajoutez une nouvelle organisation et recherchez votre client d’analyste MSSP via un ID de client ou un domaine. Nous vous suggérons de créer un client AD distinct pour vos analystes MSSP.

2. **Créer un catalogue de ressources dans Customer AAD: Identity Governance**

    Les catalogues de ressources sont une collection logique de packages d’accès, créés dans le client Client AD.

    Pour ce faire, dans le client AD client, accédez à Gouvernance des identités : catalogues et ajoutez **nouveau catalogue**. Dans notre exemple, nous allons l’appeler **Accès MSSP**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Un nouveau catalogue dans le portail Microsoft 365 Defender web" lightbox="../../media/goverance-catalog.png":::


    Pour plus d’informations, voir [Créer un catalogue de ressources](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Créer des packages d’accès pour les ressources MSSP AAD : Gouvernance des identités**

    Les packages d’accès sont la collection de droits et d’accès accordés à un demandeur lors de l’approbation. 

    Pour ce faire, dans le client AD client, accédez à Gouvernance des identités : packages d’accès et ajoutez **un nouveau package d’accès**. Créez un package d’accès pour les approuveurs MSSP et chaque niveau d’analyste. Par exemple, la configuration suivante de l’analyste de niveau 1 crée un package d’accès qui :

    - Nécessite un membre du groupe AD **MSSP Analyst Approvers** pour autoriser les nouvelles demandes
    - Possède des révisions d’accès annuel, où les analystes SOC peuvent demander une extension d’accès
    - Peut uniquement être demandé par les utilisateurs dans le client SOC MSSP
    - L’accès automatique expire après 365 jours

    :::image type="content" source="../../media/new-access-package.png" alt-text="Détails d’un nouveau package d’accès dans le portail Microsoft 365 Defender" lightbox="../../media/new-access-package.png":::

    Pour plus d’informations, voir [Créer un package d’accès](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Fournir un lien de demande d’accès aux ressources MSSP à partir de customer AAD: Identity Governance**

    Le lien du portail Mon accès est utilisé par les analystes SOC MSSP pour demander l’accès via les packages d’accès créés. Le lien est durable, ce qui signifie qu’il peut être utilisé au fil du temps pour de nouveaux analystes. La demande d’analyste est entrée dans une file d’attente pour approbation par les approuveurs **d’analyste MSSP**.

    :::image type="content" source="../../media/access-properties.png" alt-text="Propriétés d’accès dans le portail Microsoft 365 Defender web" lightbox="../../media/access-properties.png":::

    Le lien se trouve sur la page de vue d’ensemble de chaque package d’accès.

## <a name="manage-access"></a>Gérer l’accès

1. Examiner et autoriser les demandes d’accès dans Customer et/ou MSSP myaccess.

    Les demandes d’accès sont gérées dans le client Mon accès, par les membres du groupe d’approbations d’analyste MSSP.

    Pour ce faire, accédez à la myaccess du client à l’aide de : `https://myaccess.microsoft.com/@<Customer Domain>`.

    Exemple : `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Approuver ou refuser des demandes dans la section **Approbations** de l’interface utilisateur.

     À ce stade, l’accès analyste a été mis en service et chaque analyste doit pouvoir accéder au portail Microsoft 365 Defender client :

    `https://security.microsoft.com/?tid=<CustomerTenantId>` avec les autorisations et les rôles qui leur ont été attribués.

> [!IMPORTANT]
> L’accès délégué à Microsoft Defender pour le point de terminaison dans le portail Microsoft 365 Defender permet actuellement d’accéder à un seul client par fenêtre de navigateur.
