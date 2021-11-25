---
title: Accéder au portail Microsoft 365 Defender client MSSP
description: Accéder au portail Microsoft 365 Defender client MSSP
keywords: fournisseur de services de sécurité géré, mssp, configurer, intégration
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 5a359938dbee85ea64b5f46804761410cae1f48e
ms.sourcegitcommit: eb8c600d3298dca1940259998de61621e6505e69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/24/2021
ms.locfileid: "61166625"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>Accéder au portail Microsoft 365 Defender client MSSP

**S’applique à :**
- [ Microsoft Defender for Endpoint Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [ Microsoft Defender for Endpoint Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Ces étapes sont dirigées vers le MSSP.

Par défaut, les clients MSSP accèdent à Microsoft 365 Defender client via l’URL suivante : `https://securitycenter.windows.com/` .

Toutefois, les MSSP doivent utiliser une URL propre au client au format suivant : pour accéder au portail client  `https://securitycenter.windows.com?tid=customer_tenant_id` MSSP.

En règle générale, les MSSP doivent être ajoutés à chaque compte du client MSSP Azure AD qu’il a l’intention de gérer.

Utilisez les étapes suivantes pour obtenir l’ID de client MSSP, puis utilisez l’ID pour accéder à l’URL propre au client :

1. En tant que MSSP, connectez-vous Azure AD avec vos informations d’identification.

2. Basculez l’annuaire vers le client du MSSP.

3. Sélectionnez **Azure Active Directory > propriétés**. Vous trouverez l’ID de client dans le champ ID d’annuaire.

4. Accédez au portail client MSSP en remplaçant la `customer_tenant_id` valeur dans l’URL suivante : `https://securitycenter.windows.com/?tid=customer_tenant_id` .

## <a name="related-topics"></a>Rubriques connexes

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
