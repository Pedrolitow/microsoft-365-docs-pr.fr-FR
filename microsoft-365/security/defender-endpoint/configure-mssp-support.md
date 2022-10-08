---
title: Configurer la prise en charge des fournisseurs de services de sécurité managés
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
ms.topic: article
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 1e0ab5ee7e038653beebae044cb2517ee5ebf39a
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68167250"
---
# <a name="configure-managed-security-service-provider-integration"></a>Configurer l’intégration des fournisseurs de services de sécurité gérés

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

[!include[Prerelease information](../../includes/prerelease.md)]

Vous devez suivre les étapes de configuration suivantes pour activer l’intégration du fournisseur de services de sécurité managé (MSSP).

> [!NOTE]
> Les termes suivants sont utilisés dans cet article pour faire la distinction entre le fournisseur de services et le consommateur de services :
>
> - MSSP : organisations de sécurité qui offrent de surveiller et de gérer des appareils de sécurité pour une organisation.
> - Clients MSSP : organisations qui engagent les services de MSSP.

L’intégration permettra aux MSSP d’effectuer les actions suivantes :

- Accéder au portail Microsoft 365 Defender du client MSSP
- Recevoir des notifications par e-mail et
- Récupérer des alertes par le biais d’outils de gestion des événements et des informations de sécurité (SIEM)

Avant que les MSSP puissent effectuer ces actions, le client MSSP doit accorder l’accès à son locataire Defender pour point de terminaison afin que le MSSP puisse accéder au portail.

En règle générale, les clients MSSP prennent les étapes de configuration initiales pour accorder aux MSSP l’accès à leur locataire Windows Defender Security Central. Une fois l’accès accordé, d’autres étapes de configuration peuvent être effectuées par le client MSSP ou le MSSP.

En général, les étapes de configuration suivantes doivent être effectuées :

- **Accorder au MSSP l’accès à Microsoft 365 Defender**

  Cette action doit être effectuée par le client MSSP. Il accorde au MSSP l’accès au locataire Defender pour point de terminaison du client MSSP.

- **Configurer les notifications d’alerte envoyées aux MSSP**

  Cette action peut être effectuée par le client MSSP ou MSSP. Cela permet aux MSSP de savoir quelles alertes ils doivent traiter pour le client MSSP.

- **Récupérer des alertes du locataire du client MSSP dans le système SIEM**

  Cette action est effectuée par le MSSP. Il permet aux MSSP d’extraire des alertes dans les outils SIEM.

- **Récupérer des alertes à partir du locataire du client MSSP à l’aide d’API**

  Cette action est effectuée par le MSSP. Il permet aux MSSP d’extraire des alertes à l’aide d’API.

## <a name="multi-tenant-access-for-mssps"></a>Accès multilocataire pour les MSSP

Pour plus d’informations sur la façon d’implémenter un accès délégué multilocataire, consultez [l’accès multilocataire pour les fournisseurs de services de sécurité gérée](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/multi-tenant-access-for-managed-security-service-providers/ba-p/1533440).

## <a name="related-topics"></a>Voir aussi

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Configurer des notifications d’alerte](configure-mssp-notifications.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
