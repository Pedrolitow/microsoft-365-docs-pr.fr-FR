---
title: Configurer les notifications d’alerte envoyées aux MSSP
description: Configurer les notifications d’alerte envoyées aux MSSP
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
ms.openlocfilehash: b086014e718c504d990271536c69a7aba16311ce
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67678842"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>Configurer les notifications d’alerte envoyées aux MSSP

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-mssp-support-abovefoldlink)

> [!NOTE]
> Cette étape peut être effectuée par le client MSSP ou MSSP. Les MSSP doivent disposer des autorisations appropriées pour configurer cela pour le compte du client MSSP.

Une fois l’accès au portail accordé, des règles de notification d’alerte peuvent être créées afin que les e-mails soient envoyés aux MSSP lorsque des alertes associées au locataire sont créées et que les conditions définies sont remplies.

Pour plus d’informations, consultez [Créer des règles pour les notifications d’alerte](configure-email-notifications.md#create-rules-for-alert-notifications).

Ces cases à cocher doivent être cochées :

- **Inclure le nom de l’organisation** : le nom du client sera ajouté aux notifications par e-mail
- **Inclure un lien de portail spécifique au locataire** - L’URL du lien d’alerte aura un paramètre spécifique au locataire (tid=target_tenant_id) qui permet un accès direct au portail du locataire cible

## <a name="related-topics"></a>Voir aussi

- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
