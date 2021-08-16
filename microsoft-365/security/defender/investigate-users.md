---
title: Examiner les utilisateurs dans Microsoft 365 Defender
description: Examiner les utilisateurs à la recherche d’un incident dans Microsoft 365 Defender portail.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, surveiller, signaler, identités, données, appareils, applications, incident, analyser, réponse
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
ms.openlocfilehash: cc09593c7a8ceef04d0a61cc9bd7d5624943b28f
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58247118"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>Examiner les utilisateurs dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Une partie de votre enquête sur les incidents peut inclure des comptes d’utilisateur. Commencez par **l’onglet Utilisateurs** pour un incident à partir d’incidents **& alertes >** incident *>* **utilisateurs.** 

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Exemple de page Utilisateurs pour un incident":::

Pour obtenir un résumé rapide d’un compte d’utilisateur pour l’incident, cochez la coche en regard du nom du compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Exemple de volet récapitulatif du compte d’utilisateur pour un incident dans le portail Microsoft 365 Defender utilisateur":::

> [!NOTE]
> La page Utilisateur affiche Azure Active Directory organisation (Azure AD) ainsi que des groupes, vous aidant à comprendre les groupes et les autorisations associés à un utilisateur.

Dans cette page volante, vous pouvez passer en revue les informations sur les menaces des utilisateurs, notamment les incidents actuels, les alertes actives et le niveau de risque, ainsi que l’exposition des utilisateurs, les comptes, les appareils, etc.

En outre, vous pouvez prendre des mesures directement dans le portail Microsoft 365 Defender pour traiter un utilisateur compromis, en confirmant que l’utilisateur est compromis ou en exigeant qu’il se connecte à nouveau.

À partir de là, vous pouvez sélectionner La page d’accès à **l’utilisateur** pour voir les détails d’un compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Exemple de page de compte d’utilisateur pour un incident dans le portail Microsoft 365 Defender utilisateur":::

Vous pouvez également voir cette page en sélectionnant le nom du compte d’utilisateur dans la liste de la page **Utilisateurs.**

la page Microsoft 365 Defender portail d’entreprise combine les informations de Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité et Microsoft Cloud App Security (en fonction des licences dont vous avez la licence). 

Cette page affiche des informations spécifiques au risque de sécurité d’un compte d’utilisateur. Cela inclut un score qui permet d’évaluer les risques et les événements et alertes récents qui ont contribué au risque global de l’utilisateur.

À partir de cette page, vous pouvez faire les actions supplémentaires suivantes : 

- Marquer le compte d’utilisateur comme compromis
- Exiger que l’utilisateur se connecte à nouveau
- Suspendre le compte d’utilisateur
- Voir les paramètres Azure Active Directory compte d’utilisateur (Azure AD)
- Afficher les fichiers du compte d’utilisateur
- Afficher les fichiers partagés avec cet utilisateur. 

Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Exemple d’actions sur un compte d’utilisateur pour un incident dans le portail Microsoft 365 Defender":::


<!--
You can access this page from multiple areas in the Microsoft 365 Defender portal. You can access this page from a specific incident in the **Users** tab. Some alerts might include users as a specific affected asset. You can also search for users.  

Learn more about how to investigate users and potential risk [in this Cloud App Security tutorial](/cloud-app-security/tutorial-ueba#:~:text=To%20identify%20who%20your%20riskiest,user%20page%20to%20investigate%20them).

--> 

## <a name="next-steps"></a>Prochaines étapes

Si nécessaire pour les incidents in-process, poursuivez votre [enquête.](investigate-incidents.md)

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)