---
title: Configurer les notifications d’alerte envoyées aux MSSP
description: Configurer les notifications d’alerte envoyées aux MSSP
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
ms.openlocfilehash: 01e6e6c09561ecfaec861473a9be4d7a5659106a
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60553451"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>Configurer les notifications d’alerte envoyées aux MSSP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Cette étape peut être effectuée par le client MSSP ou MSSP. Les MSSP doivent avoir les autorisations appropriées pour configurer cette configuration au nom du client MSSP.

Une fois l’accès au portail accordé, des règles de notification d’alerte peuvent être créées afin que les messages électroniques soient envoyés aux MSSP lorsque des alertes associées au client sont créées et que des conditions définies sont remplies.

Pour plus d’informations, voir [Créer des règles pour les notifications d’alerte.](configure-email-notifications.md#create-rules-for-alert-notifications)

Ces cases à cocher doivent être cochées :

- **Inclure le nom de l’organisation** : le nom du client sera ajouté aux notifications par courrier électronique
- **Inclure un lien portail** propre au client : l’URL du lien d’alerte aura un paramètre spécifique au client (tid=target_tenant_id) qui permet un accès direct au portail client cible

## <a name="related-topics"></a>Voir aussi

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
