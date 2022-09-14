---
title: Applications connectées dans Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Affichez les applications partenaires connectées qui utilisent le protocole OAuth 2.0 standard pour s’authentifier et fournir des jetons à utiliser avec Microsoft Defender pour point de terminaison API.
keywords: partenaires, applications, tiers, connexions, sentinelone, lookout, bitdefender, corrata, morphisec, paloalto, ziften, better mobile
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
ms.topic: conceptual
ms.subservice: mde
ms.openlocfilehash: adf538a26b6d5514a740c696e524567ec55832f3
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67680304"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Applications connectées dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les applications connectées s’intègrent à la plateforme Defender pour point de terminaison à l’aide d’API.

Les applications utilisent le protocole OAuth 2.0 standard pour s’authentifier et fournir des jetons à utiliser avec Microsoft Defender pour point de terminaison API. En outre, les applications Azure Active Directory (Azure AD) permettent aux administrateurs de locataire de définir un contrôle explicite sur les API accessibles à l’aide de l’application correspondante.

Vous devez suivre [ces étapes](/microsoft-365/security/defender-endpoint/apis-intro) pour utiliser les API avec l’application connectée.

Dans le menu de navigation de gauche, sélectionnez **Partenaires & API** (sous **Points de terminaison**) > **Applications connectées**.

## <a name="view-connected-application-details"></a>Afficher les détails de l’application connectée

La page Applications connectées fournit des informations sur les applications Azure AD connectées à Microsoft Defender pour point de terminaison dans votre organisation. Vous pouvez passer en revue l’utilisation des applications connectées : dernière consultation, nombre de demandes au cours des dernières 24 heures et tendances des demandes au cours des 30 derniers jours.

:::image type="content" source="images/connected-apps.png" alt-text="Applications connectées" lightbox="images/connected-apps.png":::
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Modifier, reconfigurer ou supprimer une application connectée

Le lien **Ouvrir les paramètres de l’application** ouvre la page de gestion des applications Azure AD correspondante dans le Portail Azure. À partir du Portail Azure, vous pouvez gérer les autorisations, reconfigurer ou supprimer les applications connectées.
