---
title: Examiner les utilisateurs dans Microsoft 365 Defender
description: Examiner les utilisateurs à la recherche d’un incident dans Microsoft 365 Defender portail.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, centre de sécurité, surveiller, signaler, identités, données, appareils, applications, incident, analyser, réponse
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
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
ms.openlocfilehash: d49ef6b31e6446f3452d0efdce2e918813eabcc6
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63327538"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>Examiner les utilisateurs dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Une partie de votre enquête sur les incidents peut inclure des comptes d’utilisateur. Vous pouvez voir les détails des comptes d’utilisateurs identifiés dans les alertes d’un incident dans le portail Microsoft 365 Defender à partir **d’Incidents & alerts** \> **_incident_*_ \> _* Users**. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Exemple de page Utilisateurs pour un incident." lightbox="../../media/investigate-incidents/incident-users.png":::

Pour obtenir un résumé rapide d’un compte d’utilisateur pour l’incident, cochez la coche en regard du nom du compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Exemple de volet récapitulatif du compte d’utilisateur pour un incident." lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> La page utilisateur affiche Azure Active Directory (Azure AD) ainsi que des groupes, ce qui vous aide à comprendre les groupes et les autorisations associés à un utilisateur.

Dans ce volet, vous pouvez examiner les informations sur les menaces des utilisateurs, notamment les incidents actuels, les alertes actives et le niveau de risque, ainsi que l’exposition des utilisateurs, les comptes, les appareils, etc.

En outre, vous pouvez prendre des mesures directement dans le portail Microsoft 365 Defender pour traiter un utilisateur compromis, par exemple en confirmant que le compte d’utilisateur est compromis ou en exigeant une nouvelle sign-in.

À partir de là, vous pouvez sélectionner La page d’accès à **l’utilisateur** pour voir les détails d’un compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Exemple de page de compte d’utilisateur pour un incident." lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

Vous pouvez également voir cette page en sélectionnant le nom du compte d’utilisateur dans la liste de la page **Utilisateurs** .

Vous pouvez voir l’appartenance à un groupe pour l’utilisateur en sélectionnant le numéro sous **Groupes**.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="Exemple d’appartenance à un groupe pour un utilisateur." lightbox="../../media/investigate-users/user-group-membership.png":::

En sélectionnant l’icône sous **Responsable**, vous pouvez voir où se trouve l’utilisateur dans l’arborescence de l’organisation.

La page utilisateur du portail Microsoft 365 Defender combine les informations de Microsoft Defender pour le point de terminaison, Microsoft Defender pour l’identité et Microsoft Defender pour les applications cloud (en fonction des licences dont vous avez la licence).

Cette page affiche des informations spécifiques au risque de sécurité d’un compte d’utilisateur, qui inclut un score qui permet d’évaluer les risques et les événements et alertes récents qui ont contribué au risque global.

À partir de cette page, vous pouvez faire les actions supplémentaires suivantes :

- Marquer le compte d’utilisateur comme compromis
- Exiger que l’utilisateur se connecte à nouveau
- Suspendre le compte d’utilisateur
- Voir les paramètres Azure AD compte d’utilisateur
- Afficher les fichiers du compte d’utilisateur
- Afficher les fichiers partagés avec cet utilisateur.

Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Exemple d’actions sur un compte d’utilisateur pour un incident." lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>Afficher les chemins de déplacement latéral

En sélectionnant l’onglet Chemins de déplacement latéral, vous pouvez afficher une carte entièrement dynamique et cliquable qui vous fournit une représentation visuelle des chemins de déplacement latéral vers et depuis cet utilisateur qui peuvent être utilisés pour insérez votre réseau.

La carte vous fournit une liste du nombre de sauts entre les ordinateurs ou les utilisateurs qu’un utilisateur malveillant doit utiliser pour compromettre un compte sensible, et si l’utilisateur dispose d’un compte sensible, vous pouvez voir le nombre de ressources et de comptes connectés directement.

Si un chemin de mouvement latéral potentiel n’a pas été détecté pour l’entité au cours des deux derniers jours, le graphique ne s’affiche pas. Sélectionnez une date différente à l’aide de l’affichage d’une autre date pour afficher les graphiques des chemins de déplacement latéral précédents découverts pour cette entité. Le rapport de déplacement latéral est toujours disponible pour vous fournir des informations sur les chemins de déplacement latéral potentiels détectés et peut être personnalisé par heure.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="Exemple de chemin de déplacement latéral pour un utilisateur." lightbox="../../media/investigate-users/lateral-movement-path.png":::

Pour plus d’informations, voir [Chemins de déplacement latéral](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>Étapes suivantes

Si nécessaire pour les incidents in-process, poursuivez votre [enquête](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)
