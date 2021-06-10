---
title: Accéder au portail Centre de sécurité Microsoft Defender client MSSP
description: Accéder au portail Centre de sécurité Microsoft Defender client MSSP
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
ms.openlocfilehash: 97122decede91e8b4f059b3b66999ac12b300172
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51164856"
---
# <a name="access-the-microsoft-defender-security-center-mssp-customer-portal"></a>Accéder au portail Centre de sécurité Microsoft Defender client MSSP

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)

>Vous souhaitez découvrir Microsoft Defender pour le point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-mssp-support-abovefoldlink)




>[!NOTE] 
>Ces étapes sont dirigées vers le MSSP. 

Par défaut, les clients MSSP accèdent à Centre de sécurité Microsoft Defender client via l’URL suivante : `https://securitycenter.windows.com` .
 

Toutefois, les MSSP doivent utiliser une URL propre au client au format suivant : pour accéder au portail client  `https://securitycenter.windows.com?tid=customer_tenant_id` MSSP. 

En règle générale, les MSSP doivent être ajoutés à chaque azure AD du client MSSP qu’il a l’intention de gérer.


Utilisez les étapes suivantes pour obtenir l’ID de client MSSP client, puis utilisez l’ID pour accéder à l’URL propre au client :

1. En tant que MSSP, connectez-vous à Azure AD avec vos informations d’identification. 

2. Basculez l’annuaire vers le client du MSSP.

3.  Sélectionnez **Azure Active Directory > propriétés**. Vous trouverez l’ID de client dans le champ ID d’annuaire. 

4. Accédez au portail client MSSP en remplaçant la `customer_tenant_id` valeur dans l’URL suivante : `https://securitycenter.windows.com?tid=customer_tenant_id` .


## <a name="related-topics"></a>Voir aussi
- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
