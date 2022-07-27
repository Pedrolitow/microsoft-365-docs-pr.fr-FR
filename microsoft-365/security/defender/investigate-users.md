---
title: Examiner les utilisateurs dans Microsoft 365 Defender
description: Examinez les utilisateurs à la recherche d’un incident dans le portail Microsoft 365 Defender.
keywords: sécurité, programmes malveillants, Microsoft 365, M365, security center, monitor, rapport, identités, données, appareils, applications, incident, analyse, réponse
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
ms.openlocfilehash: 75fa4b76017c8fcb1f0ab65b5ed88440c04f47d2
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051621"
---
# <a name="investigate-users-in-microsoft-365-defender"></a>Examiner les utilisateurs dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

Une partie de votre enquête sur les incidents peut inclure des comptes d’utilisateur. Vous pouvez voir les détails des comptes d’utilisateur identifiés dans les alertes d’un incident dans le portail Microsoft 365 Defender à partir des **incidents & des alertes** \> **_incident_*_ \> _* Users**. Voici un exemple.

:::image type="content" source="../../media/investigate-incidents/incident-users.png" alt-text="Page Utilisateurs pour un incident dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-incidents/incident-users.png":::

Pour obtenir un résumé rapide d’un compte d’utilisateur pour l’incident, sélectionnez la coche en regard du nom du compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-pane.png" alt-text="Onglet Utilisateurs pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-users/incidents-ss-user-pane.png":::

> [!NOTE]
> La page utilisateur affiche l’organisation Azure Active Directory (Azure AD) ainsi que les groupes, ce qui vous aide à comprendre les groupes et les autorisations associés à un utilisateur.

Dans ce volet, vous pouvez consulter les informations sur les menaces des utilisateurs, notamment les incidents actuels, les alertes actives et le niveau de risque, ainsi que l’exposition des utilisateurs, les comptes, les appareils, etc.

En outre, vous pouvez prendre des mesures directement dans le portail Microsoft 365 Defender pour adresser un utilisateur compromis, par exemple en confirmant que le compte d’utilisateur est compromis ou en exigeant une nouvelle connexion.

À partir de là, vous pouvez sélectionner **Accéder à la page utilisateur** pour afficher les détails d’un compte d’utilisateur. Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details.png" alt-text="Détails du compte d’utilisateur dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-users/incidents-ss-user-details.png":::

Vous pouvez également voir cette page en sélectionnant le nom du compte d’utilisateur dans la liste de la page **Utilisateurs** .

Vous pouvez voir l’appartenance à un groupe pour l’utilisateur en sélectionnant le nombre sous **Groupes**. La sélection d’un groupe ouvre le volet **Groupes** , qui inclut des informations supplémentaires telles que la date de création et l’appartenance au groupe.

> [!NOTE]
> L’appartenance au groupe affiche uniquement les 1 000 premiers membres du groupe.

:::image type="content" source="../../media/investigate-users/user-group-membership.png" alt-text="Informations sur l’appartenance à un groupe pour un utilisateur dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-users/user-group-membership.png":::

En sélectionnant l’icône sous **Gestionnaire**, vous pouvez voir où se trouve l’utilisateur dans l’arborescence de l’organisation.

La page utilisateur du portail Microsoft 365 Defender combine les informations de Microsoft Defender pour point de terminaison, Microsoft Defender pour Identity et Microsoft Defender for Cloud Apps (selon les licences dont vous disposez).

Cette page affiche des informations spécifiques au risque de sécurité d’un compte d’utilisateur, qui inclut un score qui permet d’évaluer les risques et les événements et alertes récents qui ont contribué au risque global.

À partir de cette page, vous pouvez effectuer les actions supplémentaires suivantes :

- Marquer le compte d’utilisateur comme compromis
- Demander à l’utilisateur de se reconnecter
- Suspendre le compte d’utilisateur
- Voir les paramètres du compte d’utilisateur Azure AD
- Afficher les fichiers appartenant au compte d’utilisateur
- Afficher les fichiers partagés avec cet utilisateur.

Voici un exemple.

:::image type="content" source="../../media/investigate-users/incidents-ss-user-details-actions.png" alt-text="Section qui décrit les actions sur un compte d’utilisateur pour un incident dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-users/incidents-ss-user-details-actions.png":::

## <a name="view-lateral-movement-paths"></a>Afficher les chemins de mouvement latéral

En sélectionnant l’onglet **Chemins de mouvement latéral** , vous pouvez afficher une carte entièrement dynamique et cliquable qui vous fournit une représentation visuelle des chemins de mouvement latéral vers et à partir de cet utilisateur qui peuvent être utilisés pour infiltrer votre réseau.

La carte vous fournit une liste du nombre de tronçons entre les ordinateurs ou les utilisateurs qu’un attaquant doit atteindre et à partir de cet utilisateur pour compromettre un compte sensible. Si l’utilisateur dispose d’un compte sensible, vous pouvez voir le nombre de ressources et de comptes connectés directement.

Si aucun chemin de mouvement latéral potentiel n’a été détecté pour l’entité au cours des deux derniers jours, le graphique ne s’affiche pas. Sélectionnez une autre date à l’aide d’Afficher une date différente pour afficher les graphiques de chemins de mouvement latéral précédents découverts pour cette entité. Le rapport de chemin de mouvement latéral est toujours disponible pour vous fournir des informations sur les chemins de mouvement latéral potentiels découverts et peut être personnalisé par temps.

:::image type="content" source="../../media/investigate-users/lateral-movement-path.png" alt-text="Chemin de mouvement latéral d’un utilisateur dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-users/lateral-movement-path.png":::

Pour plus d’informations, consultez [les chemins de mouvement latéral](/defender-for-identity/use-case-lateral-movement-path).

## <a name="next-steps"></a>Prochaines étapes

Si nécessaire pour les incidents in-process, poursuivez votre [enquête](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Hiérarchiser les incidents](incident-queue.md)
- [Gérer les incidents](manage-incidents.md)
