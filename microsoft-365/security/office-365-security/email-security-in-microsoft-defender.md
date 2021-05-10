---
title: Sécurité du courrier électronique avec l’Explorateur de menaces dans Microsoft Defender Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Afficher et examiner les tentatives de hameçonnage de programmes malveillants.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a2a6d3d10cfa21c0ad2da948bff130cb9336ebd8
ms.sourcegitcommit: de5fce90de22ba588e75e1a1d2e87e03b9e25ec7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/10/2021
ms.locfileid: "52297622"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Sécurité du courrier électronique avec l’Explorateur de menaces dans Microsoft Defender Office 365

Contenu de cet article :

- [Afficher les programmes malveillants détectés dans le courrier électronique](#view-malware-detected-in-email)
- [Afficher l’URL de hameçonnage et cliquer sur les données de verdict](#view-phishing-url-and-click-verdict-data)
- [Démarrer un examen et une réponse automatisés](#start-automated-investigation-and-response)

> [!NOTE]
> Cela fait partie d’une série de **3** articles sur l’Explorateur de menaces **,** la sécurité du courrier électronique et les bases de détection **en** temps réel et de l’Explorateur (telles que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont le repérage de menaces dans [l’Explorateur](threat-hunting-in-threat-explorer.md) de menaces et l’Explorateur de menaces et les informations de base sur les [détections en temps réel.](real-time-detections.md) 

Cet article explique comment afficher et examiner les programmes malveillants et les tentatives de hameçonnage détectés dans le courrier électronique par Microsoft 365 fonctionnalités de sécurité. 

**S’applique à**

- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

## <a name="view-malware-detected-in-email"></a>Afficher les programmes malveillants détectés dans le courrier électronique

Pour voir les programmes malveillants détectés dans les e-mails triés par la technologie Microsoft 365, utilisez la vue Courrier [> Programmes](threat-explorer-views.md#email--malware) malveillants de l’Explorateur (ou détections en temps réel). Les programmes malveillants étant l’affichage par défaut, ils peuvent être sélectionnés dès que vous ouvrez l’Explorateur.

1. Dans le Centre de sécurité & conformité ( ), choisissez l’Explorateur de gestion des <https://protection.office.com>  \>  menaces (ou **détections en temps réel).** (Cet exemple utilise l’Explorateur.) Si vous êtes dans le centre de sécurité Microsoft 365 convergé (faites défiler vers l’Explorateur de collaboration & https://security.microsoft.com/)   >  **messagerie.**

   À partir de là, commencez à l’affichage, choisissez une période particulière pour [](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through)examiner (si nécessaire) et concentrez vos filtres, comme le décrit l’Explorateur.

2. Dans le menu **Affichage,** sélectionnez **Programme** malveillant de \> **messagerie.**

   > [!div class="mx-imgBorder"]
   > ![Menu Afficher pour l’Explorateur](../../media/ExplorerViewEmailMalwareMenu.png)

3. Cliquez **sur Expéditeur,** puis choisissez **Technologie de** détection de \> **base.**

   Vos technologies de détection sont désormais disponibles en tant que filtres pour le rapport.

   > [!div class="mx-imgBorder"]
   > ![Technologies de détection de programmes malveillants](../../media/ExplorerEmailMalwareDetectionTech.png)

4. Choisissez une option. Sélectionnez ensuite **le bouton Actualiser** pour appliquer ce filtre.

   > [!div class="mx-imgBorder"]
   > ![Technologie de détection sélectionnée](../../media/ExplorerEmailMalwareDetectionTechATP.png)

   Le rapport est actualisé pour afficher les résultats détectés par les programmes malveillants détectés dans le courrier électronique, à l’aide de l’option technologique que vous avez sélectionnée. À partir de là, vous pouvez effectuer une analyse plus approfondie. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Afficher l’URL de hameçonnage et cliquer sur les données de verdict

Vous pouvez afficher les tentatives de hameçonnage par le biais d’URL dans le courrier électronique, y compris une liste d’URL qui ont été autorisées, bloquées et bloquées. Pour identifier les URL sur [](safe-links.md) qui vous avez cliqué, les liens sécurisés doivent être configurés. Veillez à configurer [](set-up-safe-links-policies.md) des stratégies de liens sécurisés pour la protection au moment du clic et la journalisation des verdicts de clic par liens sécurisés.

Pour passer en revue les URL de hameçonnage dans les [   >   ](threat-explorer-views.md#email--phish) messages et cliquer sur les URL des messages d’hameçonnage, utilisez l’affichage Hameçonnage de l’Explorateur ou les détections en temps réel.

1. Dans le Centre de sécurité & conformité ( ), choisissez l’Explorateur de gestion des <https://protection.office.com>  \>  menaces (ou **détections en temps réel).** (Cet exemple utilise l’Explorateur.)

2. Dans le menu **Affichage,** sélectionnez  \> **Hameçonnage de messagerie.**

   > [!div class="mx-imgBorder"]
   > ![Afficher le menu de l’Explorateur dans le contexte de hameçonnage](../../media/ExplorerViewEmailPhishMenu.png)

3. Cliquez **sur Expéditeur,** puis choisissez **URL Verdict** de \> **clic.**

4. Sélectionnez une ou plusieurs  options, telles que Blocked  et **Block overridden,** puis sélectionnez le bouton Actualiser sur la même ligne que les options à appliquer à ce filtre. (N’actualisez pas la fenêtre de votre navigateur.)

   > [!div class="mx-imgBorder"]
   > ![URL et verdicts de clic](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

   Le rapport est actualisé pour afficher deux tables d’URL différentes sous l’onglet URL sous le rapport :

   - **Les URL les plus fréquentes** sont les URL des messages que vous avez filtrés et le nombre d’actions de remise de courrier pour chaque URL. Dans l’affichage de courrier d’hameçonnage, cette liste contient généralement des URL légitimes. Les attaquants incluent un mélange d’URL bonnes et mauvaises dans leurs messages pour essayer de les remettre, mais ils rendent les liens malveillants plus intéressants. Le tableau des URL est trié par nombre total de messages électroniques, mais cette colonne est masquée pour simplifier l’affichage.

   - **Les clics les** plus fréquents sont les URL enveloppées de liens sécurisés sur qui vous avez cliqué, triées par nombre total de clics. Cette colonne n’est pas non plus affichée, pour simplifier l’affichage. Le nombre total par colonne indique le nombre de verdicts de clics de liens sécurisés pour chaque URL cliquée. Dans l’affichage courrier d’hameçonnage, il s’agit généralement d’URL suspectes ou malveillantes. Toutefois, l’affichage peut inclure des URL qui ne sont pas des menaces mais qui figurent dans des messages d’hameçonnage. Les clics d’URL sur les liens non ballés ne s’affiche pas ici.

   Les deux tableaux d’URL indiquent les PRINCIPALES URL des messages électroniques de hameçonnage par action de remise et emplacement. Les tableaux indiquent les clics d’URL qui ont été bloqués ou visités malgré un avertissement. Vous pouvez ainsi voir quels liens de mauvaises adresses ont été présentés aux utilisateurs et que les utilisateurs ont cliqué. À partir de là, vous pouvez effectuer une analyse plus approfondie. Par exemple, sous le graphique, vous pouvez voir les URL les plus fréquentes dans les messages électroniques bloqués dans l’environnement de votre organisation.

   > [!div class="mx-imgBorder"]
   > ![URL d’explorateur qui ont été bloquées](../../media/ExplorerPhishClickVerdictURLs.png)

   Sélectionnez une URL pour afficher des informations plus détaillées.

   > [!NOTE]
   > Dans la boîte de dialogue du volant d’URL, le filtrage des messages électroniques est supprimé pour afficher la vue complète de l’exposition de l’URL dans votre environnement. Cela vous permet de filtrer les messages électroniques qui vous préoccupent dans l’Explorateur, de rechercher des URL spécifiques qui sont des menaces potentielles, puis d’étendre votre compréhension de l’exposition des URL dans votre environnement (via la boîte de dialogue Détails de l’URL) sans avoir à ajouter de filtres d’URL à l’affichage De l’Explorateur lui-même.

### <a name="interpretation-of-click-verdicts"></a>Interprétation des verdicts de clic

Dans les volants d’e-mail ou d’URL, les clics principaux et dans nos expériences de filtrage, vous verrez différentes valeurs de verdict de clic :

- **Aucun :** Impossible de capturer le verdict pour l’URL. L’utilisateur a peut-être cliqué sur l’URL.
- **Autorisé :** L’utilisateur a été autorisé à accéder à l’URL.
- **Bloqué :** L’accès à l’URL a été bloqué pour l’utilisateur.
- **Verdict en attente :** La page en attente de détonation s’est présentée à l’utilisateur.
- **Blocked overridden:** L’utilisateur ne peut pas accéder directement à l’URL. Toutefois, l’utilisateur a overrode le bloc pour accéder à l’URL.
- **Verdict en attente contourné :** La page de détonation s’est présentée à l’utilisateur. Toutefois, l’utilisateur a overrode le message pour accéder à l’URL.
- **Erreur :** La page d’erreur s’est présentée à l’utilisateur, ou une erreur s’est produite lors de la capture du verdict.
- **Échec :** Une exception inconnue s’est produite lors de la capture du verdict. L’utilisateur a peut-être cliqué sur l’URL.

## <a name="start-automated-investigation-and-response"></a>Démarrer un examen et une réponse automatisés

> [!NOTE]
> Des fonctionnalités automatisées d’examen et de réponse sont disponibles dans *Microsoft Defender pour Office 365 Plan 2* et Office 365 *E5*.

[L’examen et la réponse automatisés](automated-investigation-response-office.md) peuvent faire gagner du temps et des efforts à votre équipe en matière d’opérations de sécurité pour examiner et réduire les cyberattaques. En plus de configurer des alertes qui peuvent déclencher un manuel de sécurité, vous pouvez démarrer un processus d’examen et de réponse automatisé à partir d’un affichage dans l’Explorateur. Pour plus d’informations, [voir l’exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur.](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer)

## <a name="other-articles"></a>Autres articles

[Examiner les e-mails avec la page Entité de messagerie](mdo-email-entity-page.md)
