---
title: Applications connectées dans Microsoft Defender pour point de terminaison
ms.reviewer: ''
description: Afficher les applications partenaires connectées qui utilisent le protocole OAuth 2.0 standard pour s’authentifier et fournir des jetons à utiliser avec les API Microsoft Defender for Endpoint.
keywords: partenaires, applications, tiers, connexions, sentinelone, recherche, bitdefender, corrata, morphisec, paloalto, ziften, meilleure mobilité
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
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 06ef716e9deee7b20e8615bd22c93130ee18b77f
ms.sourcegitcommit: 4fb1226d5875bf5b9b29252596855a6562cea9ae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52845581"
---
# <a name="connected-applications-in-microsoft-defender-for-endpoint"></a>Applications connectées dans Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)


>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Les applications connectées s’intègrent à la plateforme Defender for Endpoint à l’aide des API. 

Les applications utilisent le protocole OAuth 2.0 standard pour s’authentifier et fournir des jetons à utiliser avec les API Microsoft Defender for Endpoint.  En outre, Azure Active Directory applications (Azure AD) permettent aux administrateurs client de définir un contrôle explicite sur les API accessibles à l’aide de l’application correspondante.
 
Vous devez suivre ces [étapes](/microsoft-365/security/defender-endpoint/apis-intro) pour utiliser les API avec l’application connectée.
 
## <a name="access-the-connected-application-page"></a>Accéder à la page de l’application connectée
Dans le menu de navigation de gauche, sélectionnez **Partenaires & API**  >  **connectées aux applications AAD.**

 
## <a name="view-connected-application-details"></a>Afficher les détails de l’application connectée
La page Applications connectées fournit des informations sur les applications Azure AD connectées à Microsoft Defender pour endpoint dans votre organisation. Vous pouvez passer en revue l’utilisation des applications connectées : dernière expérience, nombre de demandes au cours des dernières 24 heures et tendances des demandes au cours des 30 derniers jours.

![Image des applications connectées](images/connected-apps.png)
 
## <a name="edit-reconfigure-or-delete-a-connected-application"></a>Modifier, reconfigurer ou supprimer une application connectée
Le **lien Ouvrir les paramètres de l’application** ouvre la page de gestion des applications Azure AD correspondante dans le portail Azure. À partir du portail Azure, vous pouvez gérer les autorisations, reconfigurer ou supprimer les applications connectées.
