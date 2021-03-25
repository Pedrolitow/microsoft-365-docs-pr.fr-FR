---
title: Configurer la prise en charge des fournisseurs de services de sécurité gérés
description: Prendre les mesures nécessaires pour configurer l’intégration MSSP avec Microsoft Defender for Endpoint
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
ms.openlocfilehash: 6786d423d20ec90c12d2ea712003acc787ed599d
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165248"
---
# <a name="configure-managed-security-service-provider-integration"></a>Configurer l’intégration des fournisseurs de services de sécurité gérés

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-mssp-support-abovefoldlink)
 
[!include[Prerelease information](../../includes/prerelease.md)]

Vous devez suivre les étapes de configuration suivantes pour activer l’intégration du fournisseur de services de sécurité géré (MSSP).

>[!NOTE]
>Les termes suivants sont utilisés dans cet article pour faire la distinction entre le fournisseur de services et le consommateur de services :
> - MSSP : organisations de sécurité qui offrent de surveiller et de gérer les appareils de sécurité d’une organisation.
> - Clients MSSP : organisations qui engagent les services des MSSP.

L’intégration permettra aux MSSP d’agir comme suit :

- Accéder au portail Centre de sécurité Microsoft Defender du client MSSP
- Obtenir des notifications par courrier électronique et 
- Récupérer des alertes via les outils de gestion des événements et des informations de sécurité (SIEM)

Avant que les MSSP ne prennent ces mesures, le client MSSP doit accorder l’accès à son client Defender for Endpoint afin que le MSSP puisse accéder au portail. 
 

En règle générale, les clients MSSP prennent les étapes de configuration initiales pour accorder aux MSSP l’accès à Windows Defender client central de sécurité. Une fois l’accès accordé, d’autres étapes de configuration peuvent être réalisées par le client MSSP ou le MSSP.


En règle générale, les étapes de configuration suivantes doivent être prises :


- **Accorder au MSSP l’accès au Centre de sécurité Microsoft Defender** <br>
Cette action doit être effectuée par le client MSSP. Il accorde au MSSP l’accès au client Defender for Endpoint du client MSSP.
 

- **Configurer les notifications d’alerte envoyées aux MSSP** <br>
Cette action peut être prise par le client MSSP ou MSSP. Cela permet aux MSSP de savoir quelles alertes ils doivent adresser pour le client MSSP.

- **Récupérer des alertes du client MSSP client dans le système SIEM** <br> Cette action est prise par le MSSP. Il permet aux MSSP de récupérer des alertes dans les outils SIEM.

- **Récupérer des alertes à partir du client MSSP client à l’aide des API** <br>
Cette action est prise par le MSSP. Il permet aux MSSP de récupérer des alertes à l’aide d’API.

## <a name="multi-tenant-access-for-mssps"></a>Accès multi-client pour les MSSP
Pour plus d’informations sur l’implémenter un accès délégué à plusieurs locataires, voir [Accès multi-locataire](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440)pour les fournisseurs de services de sécurité gérée.



## <a name="related-topics"></a>Voir aussi
- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Configurer les notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer des alertes à partir du client](fetch-alerts-mssp.md)

