---
title: Accéder au portail client Microsoft 365 Defender MSSP
description: Accéder au portail client Microsoft 365 Defender MSSP
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
ms.collection: M365-security-compliance
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: e9ce4b06816e6b7e90b7878803fb985ef16e984a
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67698670"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>Accéder au portail client Microsoft 365 Defender MSSP

**S’applique à :**
- [Microsoft Defender pour point de terminaison plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [plan Microsoft Defender pour point de terminaison 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Ces étapes sont dirigées vers le MSSP.

Par défaut, les clients MSSP accèdent à leur locataire Microsoft 365 Defender via l’URL suivante : `https://security.microsoft.com/`.

Toutefois, les MSSP devront utiliser une URL spécifique au locataire au format suivant :  `https://security.microsoft.com?tid=customer_tenant_id` pour accéder au portail client MSSP.

En général, les MSSP doivent être ajoutés à chacun des services Azure AD du client MSSP qu’ils envisagent de gérer.

Utilisez les étapes suivantes pour obtenir l’ID de locataire client MSSP, puis utilisez l’ID pour accéder à l’URL propre au locataire :

1. En tant que MSSP, connectez-vous à Azure AD avec vos informations d’identification.

2. Basculez le répertoire vers le locataire du client MSSP.

3. Sélectionnez **Les propriétés > Azure Active Directory**. Vous trouverez l’ID de locataire dans le champ ID d’annuaire.

4. Accédez au portail client MSSP en remplaçant la `customer_tenant_id` valeur dans l’URL suivante : `https://security.microsoft.com/?tid=customer_tenant_id`.

## <a name="related-topics"></a>Voir aussi

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
