---
title: Configurer la prise en charge des fournisseurs de services de sécurité gérés
description: Prendre les mesures nécessaires pour configurer l’intégration MSSP avec Microsoft Defender for Endpoint
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
ms.openlocfilehash: 95eaf9d6921fa0e238b1c4c703414a6c8e4f4c3b
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60554791"
---
# <a name="configure-managed-security-service-provider-integration"></a>Configurer l’intégration des fournisseurs de services de sécurité gérés

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Vous devez suivre les étapes de configuration suivantes pour activer l’intégration du fournisseur de services de sécurité géré (MSSP).

> [!NOTE]
> Les termes suivants sont utilisés dans cet article pour faire la distinction entre le fournisseur de services et le consommateur de services :
>
> - MSSP : organisations de sécurité qui offrent la surveillance et la gestion des périphériques de sécurité pour une organisation.
> - Clients MSSP : organisations qui engagent les services des MSSP.

L’intégration permettra aux MSSP d’agir comme suit :

- Accéder au portail Microsoft 365 Defender client MSSP
- Obtenir des notifications par courrier électronique et
- Récupérer des alertes via les outils de gestion des événements et des informations de sécurité (SIEM)

Avant que les MSSP ne prennent ces mesures, le client MSSP doit accorder l’accès à son client Defender for Endpoint afin que le MSSP puisse accéder au portail.

En règle générale, les clients MSSP prennent les étapes de configuration initiales pour accorder aux MSSP l’accès Windows Defender client central de sécurité. Une fois l’accès accordé, d’autres étapes de configuration peuvent être réalisées par le client MSSP ou le MSSP.

En règle générale, les étapes de configuration suivantes doivent être prises :

- **Accorder au MSSP l’accès Microsoft 365 Defender**

  Cette action doit être effectuée par le client MSSP. Il accorde au MSSP l’accès au client Defender for Endpoint du client MSSP.

- **Configurer les notifications d’alerte envoyées aux MSSP**

  Cette action peut être prise par le client MSSP ou MSSP. Cela permet aux MSSP de savoir quelles alertes ils doivent adresser pour le client MSSP.

- **Récupérer les alertes du client du client MSSP dans le système SIEM**

  Cette action est prise par le MSSP. Il permet aux MSSP de récupérer des alertes dans les outils SIEM.

- **Récupérer des alertes à partir du client MSSP client à l’aide des API**

  Cette action est prise par le MSSP. Il permet aux MSSP de récupérer des alertes à l’aide d’API.

## <a name="multi-tenant-access-for-mssps"></a>Accès multi-client pour les MSSP

Pour plus d’informations sur l’implémenter un accès délégué à plusieurs locataires, voir [Accès multi-locataire](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440)pour les fournisseurs de services de sécurité gérée.

## <a name="related-topics"></a>Voir aussi

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
