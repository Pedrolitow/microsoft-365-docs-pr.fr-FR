---
title: Sécurité des e-mails avec l’Explorateur de menaces dans Microsoft Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: MSFTTracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 05/05/2021
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Affichez et examinez les tentatives de hameçonnage de programmes malveillants.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 637e387ca457c9795892791a1a6d9326107fc6fb
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65648192"
---
# <a name="email-security-with-threat-explorer-in-microsoft-defender-for-office-365"></a>Sécurité des e-mails avec l’Explorateur de menaces dans Microsoft Defender pour Office 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Contenu de cet article :

- [Afficher les programmes malveillants détectés dans l’e-mail](#view-malware-detected-in-email)
- [Afficher l’URL de hameçonnage et cliquer sur les données de verdict](#view-phishing-url-and-click-verdict-data)
- [Démarrer une investigation et une réponse automatisées](#start-automated-investigation-and-response)

> [!NOTE]
> Cela fait partie d’une série de 3 articles sur **l’Explorateur de menaces,** la **sécurité des e-mails** et **les détections de l’Explorateur et en temps réel** (telles que les différences entre les outils et les autorisations nécessaires pour les utiliser). Les deux autres articles de cette série sont la [chasse aux menaces dans l’Explorateur de menaces](threat-hunting-in-threat-explorer.md) et [l’Explorateur de menaces et les détections en temps réel](real-time-detections.md).

Cet article explique comment afficher et examiner les tentatives de programmes malveillants et de hameçonnage détectées par e-mail par Microsoft 365 fonctionnalités de sécurité.

## <a name="view-malware-detected-in-email"></a>Afficher les programmes malveillants détectés dans l’e-mail

Pour voir les programmes malveillants détectés dans les e-mails triés par technologie Microsoft 365, utilisez la vue [**Programmes malveillants par e-mail \>**](threat-explorer-views.md#email--malware) de l’Explorateur (ou détections en temps réel). Les programmes malveillants étant l’affichage par défaut, ils peuvent être sélectionnés dès que vous ouvrez l’Explorateur.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration**, puis choisissez **Explorer** ou **Détections en temps réel**. Pour accéder directement à la page, utilisez <https://security.microsoft.com/threatexplorer> ou <https://security.microsoft.com/realtimereports>.

   Cet exemple utilise **l’Explorateur**.

   À partir de là, commencez par la vue, choisissez un laps de temps particulier pour examiner (si nécessaire) et concentrez vos filtres, conformément à la [procédure pas à pas de l’Explorateur](threat-hunting-in-threat-explorer.md#threat-explorer-walk-through).

2. Dans la liste déroulante **Afficher**, vérifiez que les **programmes malveillants** par **e-mail** \> sont sélectionnés.

3. Cliquez sur **Sender**, puis choisissez **La technologie de détection** **de base** \> dans la liste déroulante.

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech-newimg.png" alt-text="La technologie de détection des programmes malveillants" lightbox="../../media/exploreremailmalwaredetectiontech-newimg.png":::

   Vos technologies de détection sont désormais disponibles en tant que filtres pour le rapport.

4. Choisissez une option, puis cliquez sur **Actualiser** pour appliquer ce filtre (n’actualisez pas votre fenêtre de navigateur).

   :::image type="content" source="../../media/exploreremailmalwaredetectiontech2-new.png" alt-text="technologie de détection sélectionnée" lightbox="../../media/exploreremailmalwaredetectiontech2-new.png":::

   Le rapport est actualisé pour afficher les résultats détectés par les programmes malveillants par e-mail, à l’aide de l’option de technologie que vous avez sélectionnée. À partir de là, vous pouvez effectuer une analyse plus approfondie.

### <a name="report-a-message-as-clean-in-explorer"></a>Signaler un message comme propre dans l’Explorateur

Vous pouvez utiliser l’option **De nettoyage** de rapport dans l’Explorateur pour signaler un message comme faux positif. 

1. Dans le portail Microsoft 365 Defender, accédez à **Email & Collaboration** \> **Explorer**, puis, dans la liste déroulante **Affichage**, vérifiez que **Phish** est sélectionné.

2. Vérifiez que vous êtes sous l’onglet **E-mail** , puis, dans la liste des messages signalés, sélectionnez celui que vous souhaitez signaler comme propre. 

3. Cliquez sur **Actions** pour développer la liste des options.

4. Faites défiler la liste des options pour accéder à la section **Démarrer la nouvelle soumission** , puis sélectionnez **Rapport propre**. Un menu volant s’affiche.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/report-clean-option-explorer.png" alt-text="Option De nettoyage de rapport dans l’Explorateur" lightbox="../../media/report-clean-option-explorer.png":::

5. Basculez le curseur sur **Activé**. Dans la liste déroulante, spécifiez le nombre de jours pendant lesquels vous souhaitez supprimer le message, ajoutez une note si nécessaire, puis **sélectionnez Envoyer**. 

## <a name="view-phishing-url-and-click-verdict-data"></a>Afficher l’URL de hameçonnage et cliquer sur les données de verdict

Vous pouvez afficher les tentatives d’hameçonnage par le biais d’URL par e-mail, y compris une liste d’URL qui ont été autorisées, bloquées et remplacées. Pour identifier les URL qui ont été cliqués, [Coffre liens](safe-links.md) doivent être configurés. Veillez à configurer [Coffre stratégies de liens](set-up-safe-links-policies.md) pour la protection du temps de clic et la journalisation des verdicts de clic par Coffre Liens.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & Collaboration**, puis choisissez **Explorer** ou **Détections en temps réel**. Pour accéder directement à la page, utilisez <https://security.microsoft.com/threatexplorer> ou <https://security.microsoft.com/realtimereports>.

   Cet exemple utilise **l’Explorateur**.

2. Dans la liste déroulante **Affichage**, choisissez **Phish e-mail**\>.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerViewEmailPhishMenu.png" alt-text="Menu Affichage de l’Explorateur dans le contexte de hameçonnage" lightbox="../../media/ExplorerViewEmailPhishMenu.png":::

3. Cliquez sur **Expéditeur**, puis choisissez **URL** \> **Cliquez sur Verdict** dans la liste déroulante.

4. Dans les options qui s’affichent, sélectionnez une ou plusieurs options, telles que **Bloquer** et **Bloquer remplacé**, puis cliquez sur **Actualiser** (n’actualisez pas votre fenêtre de navigateur).

    :::image type="content" source="../../media/threatexploreremailphishclickverdict-new.png" alt-text="Les URL et cliquez sur verdicts" lightbox="../../media/threatexploreremailphishclickverdict-new.png":::

   Le rapport est actualisé pour afficher deux tables d’URL **différentes** sous l’onglet URL du rapport :

   - **Les URL principales** sont les URL dans les messages que vous avez filtrés et le nombre d’actions de remise de courrier pour chaque URL. Dans la vue e-mail Phish, cette liste contient généralement des URL légitimes. Les attaquants incluent une combinaison d’URL bonnes et incorrectes dans leurs messages pour essayer de les remettre, mais ils rendent les liens malveillants plus intéressants. La table des URL est triée par nombre total d’e-mails, mais cette colonne est masquée pour simplifier l’affichage.

   - **Les clics supérieurs** sont les URL Coffre encapsulées liens qui ont été cliqués, triées par nombre total de clics. Cette colonne n’est pas non plus affichée pour simplifier l’affichage. Les nombres totaux par colonne indiquent la Coffre Les liens cliquent sur le nombre de verdicts pour chaque URL cliqué. Dans la vue e-mail Phish, il s’agit généralement d’URL suspectes ou malveillantes. Toutefois, la vue peut inclure des URL qui ne sont pas des menaces, mais qui sont dans des messages de hameçonnage. Les clics d’URL sur les liens non mappés ne s’affichent pas ici.

   Les deux tables d’URL affichent les URL les plus élevées dans les e-mails d’hameçonnage par action de remise et emplacement. Les tableaux affichent les clics d’URL qui ont été bloqués ou visités en dépit d’un avertissement, afin que vous puissiez voir quels liens incorrects potentiels ont été présentés aux utilisateurs et que les utilisateurs ont cliqué. À partir de là, vous pouvez effectuer une analyse plus approfondie. Par exemple, sous le graphique, vous pouvez voir les URL principales dans les messages électroniques qui ont été bloqués dans l’environnement de votre organisation.

   > [!div class="mx-imgBorder"]
   > :::image type="content" source="../../media/ExplorerPhishClickVerdictURLs.png" alt-text="URL de l’Explorateur qui ont été bloquées" lightbox="../../media/ExplorerPhishClickVerdictURLs.png":::

   Sélectionnez une URL pour afficher des informations plus détaillées.

   > [!NOTE]
   > Dans la boîte de dialogue de menu volant d’URL, le filtrage sur les messages électroniques est supprimé pour afficher l’affichage complet de l’exposition de l’URL dans votre environnement. Cela vous permet de filtrer les messages électroniques qui vous préoccupent dans l’Explorateur, de rechercher des URL spécifiques qui sont des menaces potentielles, puis de développer votre compréhension de l’exposition des URL dans votre environnement (via la boîte de dialogue Détails de l’URL) sans avoir à ajouter de filtres d’URL à l’affichage Explorateur lui-même.

### <a name="interpretation-of-click-verdicts"></a>Interprétation des verdicts de clic

Dans les menus volants e-mail ou URL, les clics principaux et dans nos expériences de filtrage, vous verrez différentes valeurs de verdict de clic :

- **Aucun:** Impossible de capturer le verdict pour l’URL. L’utilisateur a peut-être cliqué sur l’URL.
- **Autorisé:** L’utilisateur a été autorisé à accéder à l’URL.
- **Bloqué:** L’utilisateur n’a pas pu accéder à l’URL.
- **Verdict en attente :** La page en attente de détonation a été présentée à l’utilisateur.
- **Remplacé bloqué :** L’utilisateur n’a pas pu accéder directement à l’URL. Mais l’utilisateur remplace le bloc pour accéder à l’URL.
- **Le verdict en attente a été contourné :** La page de détonation a été présentée à l’utilisateur. Mais l’utilisateur remplace le message pour accéder à l’URL.
- **Erreur:** La page d’erreur a été présentée à l’utilisateur ou une erreur s’est produite lors de la capture du verdict.
- **Échec:** Une exception inconnue s’est produite lors de la capture du verdict. L’utilisateur a peut-être cliqué sur l’URL.

## <a name="start-automated-investigation-and-response"></a>Démarrer une investigation et une réponse automatisées

> [!NOTE]
> Les fonctionnalités d’investigation et de réponse automatisées sont disponibles dans *Microsoft Defender pour Office 365 Plan 2* et *Office 365 E5*.

[L’investigation et la réponse automatisées](automated-investigation-response-office.md) peuvent faire gagner du temps et des efforts à votre équipe chargée des opérations de sécurité pour examiner et atténuer les cyberattaques. En plus de configurer des alertes qui peuvent déclencher un playbook de sécurité, vous pouvez démarrer un processus d’investigation et de réponse automatisé à partir d’une vue dans l’Explorateur. Pour plus d’informations, consultez [Exemple : un administrateur de sécurité déclenche une enquête à partir de l’Explorateur](automated-investigation-response-office.md#example-a-security-administrator-triggers-an-investigation-from-threat-explorer).

## <a name="other-articles"></a>Autres articles

[Examiner les e-mails à l’aide de la page Entité de messagerie](mdo-email-entity-page.md)
