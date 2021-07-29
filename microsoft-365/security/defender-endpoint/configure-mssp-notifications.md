---
title: Configurer les notifications d’alerte envoyées aux MSSP
description: Configurer les notifications d’alerte envoyées aux MSSP
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
ms.openlocfilehash: d5a4d5f89cf865ad78202ede1fb637d59ab7fbda
ms.sourcegitcommit: 87d994407fb69a747239b8589ad11ddf9b47e527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2021
ms.locfileid: "53595834"
---
# <a name="configure-alert-notifications-that-are-sent-to-mssps"></a>Configurer les notifications d’alerte envoyées aux MSSP 

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-mssp-support-abovefoldlink)


>[!NOTE]
>Cette étape peut être effectuée par le client MSSP ou MSSP. Les MSSP doivent avoir les autorisations appropriées pour configurer cette configuration au nom du client MSSP.

Une fois l’accès au portail accordé, des règles de notification d’alerte peuvent être créées afin que les messages électroniques soient envoyés aux MSSP lorsque des alertes associées au client sont créées et que des conditions définies sont remplies.

 
Pour plus d’informations, voir [Créer des règles pour les notifications d’alerte.](configure-email-notifications.md#create-rules-for-alert-notifications)
 

Ces cases à cocher doivent être cochées :
- **Inclure le nom de l’organisation** : le nom du client sera ajouté aux notifications par courrier électronique
- **Inclure un lien portail** propre au client : l’URL du lien d’alerte aura un paramètre spécifique au client (tid=target_tenant_id) qui permet un accès direct au portail client cible


## <a name="related-topics"></a>Voir aussi
- [Accorder l’accès MSSP au portail](grant-mssp-access.md)
- [Accéder au portail client MSSP](access-mssp-portal.md)
- [Récupérer les alertes d’un client](fetch-alerts-mssp.md)
