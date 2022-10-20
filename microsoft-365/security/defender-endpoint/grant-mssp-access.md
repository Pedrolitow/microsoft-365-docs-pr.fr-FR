---
title: Accorder l’accès au fournisseur de services de sécurité managé (MSSP)
description: Effectuez les étapes nécessaires pour configurer l’intégration de MSSP au Microsoft Defender pour point de terminaison
keywords: fournisseur de services de sécurité managé, mssp, configure, integration
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: fcd01ba8a26f8ff997bfeed94e9f173607135eef
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68637925"
---
# <a name="grant-managed-security-service-provider-mssp-access-preview"></a>Accorder l’accès au fournisseur de services de sécurité managé (MSSP) (préversion)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!IMPORTANT]
> Certaines informations ont trait à un produit préalablement publié, qui peut être modifié de manière significative avant sa publication commerciale. Microsoft n’offre aucune garantie, explicite ou implicite, concernant les informations fournies ici.

Pour implémenter une solution d’accès délégué multilocataire, procédez comme suit :

1. Activez le [contrôle d’accès en fonction du rôle](rbac.md) dans Defender pour point de terminaison et connectez-vous à des groupes Active Directory (AD).

2. Configurez [les packages d’accès de gouvernance pour la](/azure/active-directory/governance/identity-governance-overview) demande d’accès et le provisionnement.

3. Gérer les demandes d’accès et les audits dans [Microsoft Myaccess](/azure/active-directory/governance/entitlement-management-request-approve).

## <a name="enable-role-based-access-controls-in-microsoft-defender-for-endpoint"></a>Activer les contrôles d’accès en fonction du rôle dans Microsoft Defender pour point de terminaison

1. **Créer des groupes d’accès pour les ressources MSSP dans Customer AAD: Groups**

    Ces groupes sont liés aux rôles que vous créez dans Defender pour point de terminaison. Pour ce faire, dans le locataire AD client, créez trois groupes. Dans notre exemple d’approche, nous créons les groupes suivants :

    - Analyste de niveau 1
    - Analyste de niveau 2
    - Approbateurs d’analystes MSSP

2. Créez des rôles Defender pour point de terminaison pour les niveaux d’accès appropriés dans Customer Defender pour point de terminaison.

    Pour activer RBAC dans le portail Microsoft 365 Defender client, **accédez aux paramètres > autorisations > rôles** et « Activer les rôles », à partir d’un compte d’utilisateur disposant de droits d’administrateur général ou d’administrateur de sécurité.

    :::image type="content" source="images/mssp-access.png" alt-text="Accès MSSP" lightbox="images/mssp-access.png":::

    Ensuite, créez des rôles RBAC pour répondre aux besoins du niveau SOC MSSP. Liez ces rôles aux groupes d’utilisateurs créés via « Groupes d’utilisateurs affectés ».

    Deux rôles possibles :

    - **Analystes de niveau 1**

      Effectuez toutes les actions à l’exception de la réponse en direct et gérez les paramètres de sécurité.

    - **Analystes de niveau 2**

      Fonctionnalités de niveau 1 avec ajout à la [réponse dynamique](live-response.md)

    Pour plus d’informations, consultez [Utiliser le contrôle d’accès en fonction du rôle](rbac.md).

## <a name="configure-governance-access-packages"></a>Configurer des packages d’accès à la gouvernance

1. **Ajouter MSSP en tant qu’organisation connectée dans AAD client : Gouvernance des identités**

    L’ajout de MSSP en tant qu’organisation connectée permet au MSSP de demander et d’avoir des accès approvisionnés.

    Pour ce faire, dans le locataire AD du client, accédez à Identity Governance : Organisation connectée. Ajoutez une nouvelle organisation et recherchez votre locataire d’analyste MSSP via l’ID de locataire ou le domaine. Nous vous suggérons de créer un locataire AD distinct pour vos analystes MSSP.

2. **Créer un catalogue de ressources dans Customer AAD: Identity Governance**

    Les catalogues de ressources sont une collection logique de packages d’accès, créés dans le locataire AD client.

    Pour ce faire, dans le locataire AD client, accédez à Identity Governance: Catalogs et ajoutez **New Catalog**. Dans notre exemple, nous l’appellerons **Accès MSSP**.

    :::image type="content" source="images/goverance-catalog.png" alt-text="Nouvelle page de catalogue" lightbox="images/goverance-catalog.png":::

    Pour plus d’informations, consultez [Créer un catalogue de ressources](/azure/active-directory/governance/entitlement-management-catalog-create).

3. **Créer des packages d’accès pour les ressources MSSP Client AAD : Gouvernance des identités**

    Les packages d’accès sont la collection de droits et d’accès qu’un demandeur accordera lors de l’approbation.

    Pour ce faire, dans le locataire AD client, accédez à Identity Governance: Access Packages et ajoutez **New Access Package**. Créez un package d’accès pour les approbateurs MSSP et chaque niveau d’analyste. Par exemple, la configuration d’analyste de niveau 1 suivante crée un package d’accès qui :

    - Requiert un membre du groupe AD **MSSP Analyst Approvers** pour autoriser de nouvelles demandes
    - A des révisions d’accès annuelles, où les analystes SOC peuvent demander une extension d’accès
    - Peut uniquement être demandée par les utilisateurs dans le locataire SOC MSSP
    - L’accès automatique expire après 365 jours

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/new-access-package.png" alt-text="Page Nouveau package d’accès" lightbox="images/new-access-package.png":::

    Pour plus d’informations, consultez [Créer un package d’accès](/azure/active-directory/governance/entitlement-management-access-package-create).

4. **Fournir un lien de demande d’accès aux ressources MSSP à partir d’AAD client : Gouvernance des identités**

    Le lien du portail Mon accès est utilisé par les analystes SOC MSSP pour demander l’accès via les packages d’accès créés. Le lien est durable, ce qui signifie que le même lien peut être utilisé au fil du temps pour les nouveaux analystes. La demande d’analyste est envoyée dans une file d’attente pour approbation par les **approbateurs d’analysteS MSSP**.

    > [!div class="mx-imgBorder"]
    > :::image type="content" source="images/access-properties.png" alt-text="Page Propriétés" lightbox="images/access-properties.png":::

    Le lien se trouve sur la page vue d’ensemble de chaque package d’accès.

## <a name="manage-access"></a>Gérer l’accès

1. Passez en revue et autorisez les demandes d’accès dans customer et/ou MSSP myaccess.

    Les demandes d’accès sont gérées dans le client Mon accès, par les membres du groupe Approbateurs d’analystes MSSP.

    Pour ce faire, accédez à myaccess du client à l’aide de : `https://myaccess.microsoft.com/@<Customer Domain>`.

    Exemple : `https://myaccess.microsoft.com/@M365x440XXX.onmicrosoft.com#/`

2. Approuvez ou refusez **les demandes** dans la section Approbations de l’interface utilisateur.

    À ce stade, l’accès aux analystes a été approvisionné et chaque analyste doit être en mesure d’accéder au portail Microsoft 365 Defender du client :`https://security.microsoft.com/?tid=<CustomerTenantId>`

## <a name="related-topics"></a>Voir aussi

- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
