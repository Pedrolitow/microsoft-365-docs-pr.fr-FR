---
title: Liens fiables ATP pour Teams, safelinks, liens fiables, bloquer les liens malveillants, Office 365 ATP, liens approuvés de teams, empêcher les utilisateurs de cliquer sur les liens incorrects, liens malveillants
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
audience: Admin
ms.date: 02/28/2020
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: Les équipes auront désormais accès à des liens fiables au moment de votre clic. Que vous utilisiez des conversations de conversation 1-on-1, entre des groupes ou des canaux, et des onglets, si vous disposez d’un abonnement à la protection avancée contre les menaces pour Office 365, vous pouvez activer et utiliser cette fonctionnalité de sécurité.
ms.openlocfilehash: 88fe9756188eb16a2347d3c0cd4a98b4003ff457
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43635997"
---
<!--06/21/2019-->

# <a name="safe-links-in-teams"></a>Liens fiables dans Teams

> [!IMPORTANT]
> Cette fonctionnalité est en préversion **publique** pour les clients du programme d’adoption de la technologie Microsoft Teams (TAP) du 28 février 2020. Cette note sera supprimée de l’article lorsque les liens fiables de teams sont plus largement disponibles.

Microsoft Teams, une application Microsoft Cloud pour la gestion de votre travail, utilise déjà des pièces jointes fiables (pour Office 365), mais il aura maintenant accès à des liens fiables au moment de votre clic. Que vous utilisiez des conversations de conversation 1-on-1, entre des groupes ou des canaux, et des onglets, si vous disposez d’un abonnement à la protection avancée contre les menaces pour Office 365, vous pouvez activer et utiliser cette mesure de sécurité.

Voici le principe de fonctionnement : 

1. Lorsque vous démarrez l’application Teams, Microsoft 365 vérifie que l’utilisateur appartient à une organisation disposant d’Office 365 ATP et que l’utilisateur fait partie d’une stratégie de liens approuvés active avec sa protection activée pour Microsoft Teams.

2. Si les éléments ci-dessus sont vrais, les URL seront validées au moment du clic dans les conversations, les conversations de groupe, les canaux et dans les onglets pour cet utilisateur.
 
## <a name="what-will-users-experience"></a>Qu’est-ce que les utilisateurs peuvent expérimenter ? 

Tous les utilisateurs protégés bénéficieront de cette expérience avec des URL dangereuses : 

- Si vous avez cliqué sur le lien d’une conversation Teams, d’une conversation de groupe ou de canaux, une page s’affiche dans le navigateur par défaut. Si vous avez cliqué sur le lien à partir d’un onglet épinglé, la page s’affiche dans l’interface utilisateur de teams sous cet onglet, et l’option d’ouverture dans le navigateur est désactivée pour des raisons de sécurité.

- Cet utilisateur ne pourra pas continuer à passer sur le site de l’URL.

Si l’utilisateur qui a envoyé le lien n’est pas protégé par la protection avancée contre les menaces d’Office 365, il est libre de cliquer sur l’URL sur son ordinateur et de résoudre le problème. Il est ainsi doublement important que les administrateurs soient conscients de l’identité de leurs utilisateurs protégés.

![Une page de liens fiables pour les équipes qui signalent un lien malveillant et bloque le transit vers la page.](/microsoft-365/media/TP_SafelinksForTeams_Malicious.png)

Le fait de cliquer sur *le bouton de retour de* cette page dans teams le ferme (ou peut entraîner la fermeture d’une page vierge par les utilisateurs). Toutefois, le fait de cliquer à nouveau sur le lien entraînera une nouvelle évaluation de la réputation du site afin de réafficher cette page.

> [!NOTE]
>Certains administrateurs de Microsoft 365 vont activer le message **continuer quand même** sur la page de blocage. Toutefois, si les liens fiables mesurent la réputation d’un site et le trouvent manquant, aucune autre opération de clic ne doit être effectuée. Il n’est pas recommandé que les utilisateurs contournent les mesures de sécurité. N’hésitez pas à évaluer ces éléments avant d’activer la fonctionnalité continuer. 

