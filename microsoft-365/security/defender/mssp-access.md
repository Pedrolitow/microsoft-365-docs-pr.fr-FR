---
title: Fournir un accès au fournisseur de services de sécurité managé (MSSP)
description: En savoir plus sur les modifications apportées par le Centre de sécurité Microsoft Defender au portail Microsoft 365 Defender
keywords: Prise en main du portail Microsoft 365 Defender, Microsoft Defender pour Office 365, Microsoft Defender pour point de terminaison, MDO, MDE, volet unique de verre, portail convergé, portail de sécurité, portail de sécurité Defender
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
ms.openlocfilehash: 4eccd4d6140810bae4caef5e194082aeb3054217
ms.sourcegitcommit: 3b194dd6f9ce531ae1b33d617ab45990d48bd3d0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2022
ms.locfileid: "66102369"
---
# <a name="provide-managed-security-service-provider-mssp-access"></a>Fournir un accès au fournisseur de services de sécurité managé (MSSP) 

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

[!INCLUDE [Prerelease](../includes/prerelease.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Pour implémenter une solution d’accès délégué multilocataire, procédez comme suit :

1. Activez le [contrôle d’accès en fonction du rôle](/microsoft-365/security/defender-endpoint/rbac) pour Defender pour point de terminaison via le portail Microsoft 365 Defender et connectez-vous à des groupes Azure Active Directory (Azure AD).

2. Configurez [la gestion des droits d’utilisation pour les utilisateurs externes](/azure/active-directory/governance/entitlement-management-external-users) dans Azure AD Identity Governance pour activer les demandes d’accès et l’approvisionnement.

3. Gérer les demandes d’accès et les audits dans [Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint-in-microsoft-365-defender-portal"></a>Activer les contrôles d’accès en fonction du rôle dans Microsoft Defender pour point de terminaison dans Microsoft 365 Defender portail

1. **Créer des groupes d’accès pour les ressources MSSP dans Customer AAD: Groups**

    Ces groupes sont liés aux rôles que vous créez dans Defender pour point de terminaison dans Microsoft 365 Defender portail. Pour ce faire, dans le locataire AD client, créez trois groupes. Dans notre exemple d’approche, nous créons les groupes suivants :

    - Analyste de niveau 1
    - Analyste de niveau 2
    - Approbateurs d’analystes MSSP  

2. Créez des rôles Defender pour point de terminaison pour les niveaux d’accès appropriés dans Customer Defender pour point de terminaison dans Microsoft 365 Defender rôles et groupes du portail.

    Pour activer RBAC dans le portail Microsoft 365 Defender client, accédez aux **rôles Autorisations > Points de terminaison & groupes > rôles** avec un compte d’utilisateur avec des droits d’administrateur général ou d’administrateur de sécurité.

    :::image type="content" source="../../media/mssp-access.png" alt-text="Détails de l’accès MSSP dans le portail Microsoft 365 Defender" lightbox="../../media/mssp-access.png":::

    Ensuite, créez des rôles RBAC pour répondre aux besoins du niveau SOC MSSP. Liez ces rôles aux groupes d’utilisateurs créés via « Groupes d’utilisateurs affectés ».

    Deux rôles possibles :

    - **Analystes de niveau 1** <br>
      Effectuez toutes les actions à l’exception de la réponse en direct et gérez les paramètres de sécurité.

    - **Analystes de niveau 2** <br>
      Fonctionnalités de niveau 1 avec ajout à la [réponse dynamique](/microsoft-365/security/defender-endpoint/live-response).

    Pour plus d’informations, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](/microsoft-365/security/defender-endpoint/rbac).

## <a name="configure-governance-access-packages"></a>Configurer des packages d’accès à la gouvernance

1. **Ajouter MSSP en tant qu’organisation connectée dans AAD client : Gouvernance des identités**

    L’ajout de MSSP en tant qu’organisation connectée permet au MSSP de demander et d’avoir des accès approvisionnés. 

    Pour ce faire, dans le locataire AD du client, accédez à Identity Governance : Organisation connectée. Ajoutez une nouvelle organisation et recherchez votre locataire d’analyste MSSP via l’ID de locataire ou le domaine. Nous vous suggérons de créer un locataire AD distinct pour vos analystes MSSP.

2. **Créer un catalogue de ressources dans Customer AAD: Identity Governance**

    Les catalogues de ressources sont une collection logique de packages d’accès, créés dans le locataire AD client.

    Pour ce faire, dans le locataire AD client, accédez à Identity Governance: Catalogs et ajoutez **New Catalog**. Dans notre exemple, nous l’appellerons **Accès MSSP**.

    :::image type="content" source="../../media/goverance-catalog.png" alt-text="Un nouveau catalogue dans le portail Microsoft 365 Defender" lightbox="../../media/goverance-catalog.png":::


    Pour plus d’informations, consultez [Créer un catalogue de ressources](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Créer des packages d’accès pour les ressources MSSP Client AAD : Gouvernance des identités**

    Les packages d’accès sont la collection de droits et d’accès qu’un demandeur accordera lors de l’approbation. 

    Pour ce faire, dans le locataire AD client, accédez à Identity Governance: Access Packages et ajoutez **New Access Package**. Créez un package d’accès pour les approbateurs MSSP et chaque niveau d’analyste. Par exemple, la configuration d’analyste de niveau 1 suivante crée un package d’accès qui :

    - Requiert un membre du groupe AD **MSSP Analyst Approvers** pour autoriser de nouvelles demandes
    - A des révisions d’accès annuelles, où les analystes SOC peuvent demander une extension d’accès
    - Peut uniquement être demandée par les utilisateurs dans le locataire SOC MSSP
    - L’accès automatique expire après 365 jours

    :::image type="content" source="../../media/new-access-package.png" alt-text="Détails d’un nouveau package d’accès dans le portail Microsoft 365 Defender" lightbox="../../media/new-access-package.png":::

    Pour plus d’informations, consultez [Créer un package d’accès](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Fournir un lien de demande d’accès aux ressources MSSP à partir d’AAD client : Gouvernance des identités**

    Le lien du portail Mon accès est utilisé par les analystes SOC MSSP pour demander l’accès via les packages d’accès créés. Le lien est durable, ce qui signifie que le même lien peut être utilisé au fil du temps pour les nouveaux analystes. La demande d’analyste est envoyée dans une file d’attente pour approbation par les **approbateurs d’analysteS MSSP**.

    :::image type="content" source="../../media/access-properties.png" alt-text="Propriétés d’accès dans le portail Microsoft 365 Defender" lightbox="../../media/access-properties.png":::

    Le lien se trouve sur la page vue d’ensemble de chaque package d’accès.

## <a name="manage-access"></a>Gérer l’accès

1. Passez en revue et autorisez les demandes d’accès dans customer et/ou MSSP myaccess.

    Les demandes d’accès sont gérées dans le client Mon accès, par les membres du groupe Approbateurs d’analystes MSSP.

    Pour ce faire, accédez à myaccess du client à l’aide de : `https://myaccess.microsoft.com/@<Customer Domain>`.

    Exemple : `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Approuvez ou refusez les demandes dans la section **Approbations** de l’interface utilisateur.

     À ce stade, l’accès aux analystes a été approvisionné et chaque analyste doit être en mesure d’accéder au portail Microsoft 365 Defender du client :

    `https://security.microsoft.com/?tid=<CustomerTenantId>` avec les autorisations et rôles qui leur ont été attribués.
