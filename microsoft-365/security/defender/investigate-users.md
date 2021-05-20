---
title: Enquêter sur les utilisateurs dans Microsoft 365 Defender
description: Enquêter sur les utilisateurs pour un incident dans le centre Microsoft 365 sécurité de la ville.
keywords: sécurité, malware, Microsoft 365, M365, centre de sécurité, moniteur, rapport, identités, données, appareils, applications, incident, analyse, réponse
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
ms.openlocfilehash: 72eb111da2f342b78aa6161c7334a7252314b4a5
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572800"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>Enquêter sur les utilisateurs dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Une partie de votre enquête sur les incidents peut inclure des comptes d’utilisateurs. Commencez par **l’onglet** Utilisateurs pour un incident provenant **d’incidents & alertes** *>'incident* **> utilisateurs**. 

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Exemple d’une page utilisateurs pour un incident":::

Pour obtenir un résumé rapide d’un compte utilisateur pour l’incident, sélectionnez la marque de contrôle à côté du nom du compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Exemple du volet résumé du compte utilisateur pour un incident dans le centre de sécurité Microsoft 365'utilisateur":::

> [!NOTE]
> La page Utilisateur affiche Azure Active Directory organisation (Azure AD) ainsi que des groupes, vous aidant à comprendre les groupes et les autorisations associés à un utilisateur.

Dans cette page de survol, vous pouvez consulter les informations sur les menaces des utilisateurs, y compris les incidents actuels, les alertes actives et le niveau de risque, ainsi que l’exposition des utilisateurs, les comptes, les appareils et plus encore.

En outre, vous pouvez prendre des mesures directement dans le centre de sécurité Microsoft 365 pour s’adresser à un utilisateur compromis, confirmant que l’utilisateur est compromis ou l’obligeant à se connecter à nouveau.

De là, vous pouvez sélectionner Go **to user page pour voir** les détails d’un compte utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Exemple de page de compte utilisateur pour un incident dans le centre Microsoft 365 sécurité":::

Vous pouvez également voir cette page en sélectionnant le nom du compte utilisateur à partir de la liste sur la page **Utilisateurs.**

La page utilisateur Microsoft 365 centre de sécurité combine les informations de Microsoft Defender pour Endpoint, Microsoft Defender for Identity et Microsoft Cloud App Security (selon les licences que vous avez). 

Cette page affiche des informations spécifiques au risque de sécurité d’un compte utilisateur. Cela inclut un score qui permet d’évaluer les risques et les événements récents et les alertes qui ont contribué au risque global de l’utilisateur.

À partir de cette page, vous pouvez faire ces actions supplémentaires : 

- Marquer le compte utilisateur comme compromis
- Exiger de l’utilisateur qu’il se connecte à nouveau
- Suspendre le compte utilisateur
- Voir les paramètres Azure Active Directory compte utilisateur (Azure AD)
- Voir les fichiers appartenant au compte utilisateur
- Consultez les fichiers partagés avec cet utilisateur. 

Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Exemple des actions sur un compte utilisateur pour un incident dans le centre Microsoft 365 sécurité":::


<!--
You can access this page from multiple areas in the Microsoft 365 security center. You can access this page from a specific incident in the **Users** tab. Some alerts might include users as a specific affected asset. You can also search for users.  

Learn more about how to investigate users and potential risk [in this Cloud App Security tutorial](/cloud-app-security/tutorial-ueba#:~:text=To%20identify%20who%20your%20riskiest,user%20page%20to%20investigate%20them).

--> 

## <a name="next-steps"></a>Étapes suivantes

Au besoin pour les incidents en cours, poursuivez votre [enquête](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)