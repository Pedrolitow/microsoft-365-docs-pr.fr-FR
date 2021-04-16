---
title: Examiner les utilisateurs dans le Centre de sécurité Microsoft 365
description: examiner les utilisateurs dans le Centre de sécurité Microsoft 365
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, surveiller, signaler, identités, données, appareils, applications
ms.prod: m365-security
ms.mktglfcycl: deploy
localization_priority: Normal
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
ms.date: ''
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
search.appverid: met150
ms.custom: seo-marvel-jun2020
ms.technology: m365d
ms.openlocfilehash: 68fc924ee14932ebdf92ef76306ba00e352b6030
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861259"
---
# <a name="investigate-users-in-microsoft-365-security-center"></a>Examiner les utilisateurs dans le Centre de sécurité Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Une partie de votre enquête sur les incidents peut inclure des comptes d'utilisateur. Commencez par **l'onglet Utilisateurs** pour un incident à partir d'incidents **& alertes >** incident *>* **utilisateurs.** 

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Exemple de page Utilisateurs pour un incident":::

Pour obtenir un résumé rapide d'un compte d'utilisateur pour l'incident, cochez la coche en regard du nom du compte d'utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Exemple de volet récapitulatif du compte d'utilisateur pour un incident dans le Centre de sécurité Microsoft 365":::

À partir de là, vous pouvez sélectionner La page d'accès à **l'utilisateur** pour voir les détails d'un compte d'utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Exemple de page de compte d'utilisateur pour un incident dans le Centre de sécurité Microsoft 365":::

Vous pouvez également voir cette page en sélectionnant le nom du compte d'utilisateur dans la liste de la page **Utilisateurs.**

La page utilisateur du Centre de sécurité Microsoft 365 combine les informations de Microsoft Defender pour le point de terminaison, Microsoft Defender pour l'identité et Microsoft Cloud App Security (en fonction des licences dont vous avez la licence). 

Cette page affiche des informations spécifiques au risque de sécurité d'un compte d'utilisateur. Cela inclut un score qui permet d'évaluer les risques et les événements et alertes récents qui ont contribué au risque global de l'utilisateur.

À partir de cette page, vous pouvez faire les actions supplémentaires suivantes : 

- Marquer le compte d'utilisateur comme compromis
- Exiger que l'utilisateur se connecte à nouveau
- Suspendre le compte d'utilisateur
- Voir les paramètres du compte d'utilisateur Azure Active Directory (Azure AD)
- Afficher les fichiers du compte d'utilisateur
- Afficher les fichiers partagés avec cet utilisateur. 

Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Exemple d'actions sur un compte d'utilisateur pour un incident dans le Centre de sécurité Microsoft 365":::


<!--
You can access this page from multiple areas in the Microsoft 365 security center. You can access this page from a specific incident in the **Users** tab. Some alerts might include users as a specific affected asset. You can also search for users.  

Learn more about how to investigate users and potential risk [in this Cloud App Security tutorial](/cloud-app-security/tutorial-ueba#:~:text=To%20identify%20who%20your%20riskiest,user%20page%20to%20investigate%20them).

--> 

## <a name="related-topics"></a>Sujets associés

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)