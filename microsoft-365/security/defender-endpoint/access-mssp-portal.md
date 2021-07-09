---
title: Accéder au portail Microsoft 365 Defender client MSSP
description: Accéder au portail Microsoft 365 Defender client MSSP
keywords: fournisseur de services de sécurité géré, mssp, configurer, intégration
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 8583b28adecd892ec6875faa934fd7ab08e5db11
ms.sourcegitcommit: 0d1b065c94125b495e9886200f7918de3bda40b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2021
ms.locfileid: "53339585"
---
# <a name="access-the-microsoft-365-defender-mssp-customer-portal"></a>Accéder au portail Microsoft 365 Defender client MSSP

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-mssp-support-abovefoldlink)




>[!NOTE] 
>Ces étapes sont dirigées vers le MSSP. 

Par défaut, les clients MSSP accèdent à Centre de sécurité Microsoft Defender client via l’URL suivante : `https://securitycenter.windows.com` .
 

Toutefois, les MSSP doivent utiliser une URL propre au client au format suivant : pour accéder au portail client  `https://securitycenter.windows.com?tid=customer_tenant_id` MSSP. 

En règle générale, les MSSP doivent être ajoutés à chaque azure AD du client MSSP qu’il a l’intention de gérer.


Utilisez les étapes suivantes pour obtenir l’ID de client MSSP, puis utilisez l’ID pour accéder à l’URL propre au client :

1. En tant que MSSP, connectez-vous à Azure AD avec vos informations d’identification. 

2. Basculez l’annuaire vers le client du MSSP.

3.  Sélectionnez **Azure Active Directory > propriétés**. Vous trouverez l’ID de client dans le champ ID d’annuaire. 

4. Accédez au portail client MSSP en remplaçant la `customer_tenant_id` valeur dans l’URL suivante : `https://securitycenter.windows.com?tid=customer_tenant_id` .


## <a name="related-topics"></a>Voir aussi
- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
