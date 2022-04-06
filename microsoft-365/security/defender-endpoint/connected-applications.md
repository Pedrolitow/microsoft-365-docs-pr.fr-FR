---
title: Applications connectées dans Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Afficher les applications partenaires connectées qui utilisent le protocole OAuth 2.0 standard pour s’authentifier et fournir des jetons à utiliser avec les API Microsoft Defender for Endpoint.
keywords: partenaires, applications, tiers, connexions, sentinelone, recherche, bitdefender, corrata, morphisec, paloalto, ziften, meilleure mobilité
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 9e15103f4366d0717af9cec44d516b4b16a7160a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64475562"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Applications connectées dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les applications connectées s’intègrent à la plateforme Defender for Endpoint à l’aide des API.

Les applications utilisent le protocole OAuth 2.0 standard pour s’authentifier et fournir des jetons à utiliser avec les API Microsoft Defender for Endpoint. En outre, les applications Azure Active Directory (Azure AD) permettent aux administrateurs client de définir un contrôle explicite sur les API accessibles à l’aide de l’application correspondante.

Vous devez suivre ces [étapes pour](/microsoft-365/security/defender-endpoint/apis-intro) utiliser les API avec l’application connectée.

Dans le menu de navigation de gauche, sélectionnez Partenaires **& API** (sous Points de terminaison **) >** **applications connectées**.

## <a name="view-connected-application-details"></a>Afficher les détails de l’application connectée

La page Applications connectées fournit des informations sur Azure AD applications connectées à Microsoft Defender for Endpoint dans votre organisation. Vous pouvez passer en revue l’utilisation des applications connectées : dernière expérience, nombre de demandes au cours des dernières 24 heures et tendances des demandes au cours des 30 derniers jours.

:::image type="content" source="images/connected-apps.png" alt-text="Applications connectées" lightbox="images/connected-apps.png":::
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Modifier, reconfigurer ou supprimer une application connectée

Le **lien Ouvrir les paramètres de** l’application ouvre la page Azure AD gestion des applications correspondante dans le portail Azure. À partir du portail Azure, vous pouvez gérer les autorisations, reconfigurer ou supprimer les applications connectées.
