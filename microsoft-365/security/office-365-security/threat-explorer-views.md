---
title: Affichages dans l’Explorateur de menaces et détections en temps réel
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: article
localization_priority: Normal
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez comment utiliser l’Explorateur de menaces et le rapport de détections en temps réel pour examiner les menaces et y répondre dans le Centre de sécurité & conformité.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: aef3f7fe69e5cbd1d70b7aee3284f0c5dc6416df
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50290284"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Affichages dans l’Explorateur de menaces et détections en temps réel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)


![Threat Explorer](../../media/ThreatExplorerFirstOpened.png)

[L’Explorateur](threat-explorer.md) de menaces (et le rapport sur les détections en temps réel) est un outil puissant, quasiment en temps réel, qui permet aux équipes des opérations de sécurité d’examiner et de répondre aux menaces dans le Centre de sécurité & conformité. L’Explorateur (et le rapport de détections en temps réel) affiche des informations sur les programmes malveillants et le hameçonnage suspectés dans le courrier électronique et les fichiers dans Office 365, ainsi que d’autres menaces et risques de sécurité pour votre organisation.

- Si vous avez [Microsoft Defender pour Office 365](office-365-atp.md) Plan 2, vous avez Explorer.
- Si vous avez Microsoft Defender pour Office 365 Plan 1, vous avez des détections en temps réel.

Lorsque vous ouvrez l’Explorateur pour la première fois (ou le rapport de détections en temps réel), l’affichage par défaut affiche les détections de programmes malveillants de messagerie électronique au cours des 7 derniers jours. Ce rapport peut également afficher les détections de Microsoft Defender pour Office 365, telles que les URL malveillantes détectées par les liens fiables [et](atp-safe-links.md)les fichiers malveillants détectés par les pièces [jointes fiables.](atp-safe-attachments.md) Ce rapport peut être modifié pour afficher les données des 30 derniers jours (avec un abonnement Payant Microsoft Defender pour Office 365 P2). Les abonnements à la version d’essai incluent uniquement les données des sept derniers jours.

****

|Abonnement|Utilitaire|Jours de données|
|---|---|---|
|Version d’essai de Microsoft Defender pour Office 365 P1|Détections en temps réel|7 |
|Microsoft Defender pour Office 365 P1 payant|Détections en temps réel|30|
|Essai payant de Microsoft Defender pour Office 365 P1 pour Office 365 P2|Threat Explorer|7 |
|Version d’essai de Microsoft Defender pour Office 365 P2|Threat Explorer|7 |
|Microsoft Defender pour Office 365 P2 payant|Threat Explorer|30|
|

Utilisez le menu **Affichage** pour modifier les informations affichées. Les bulles vous aident à déterminer l’affichage à utiliser.

![Menu Affichage de l’Explorateur de menaces](../../media/ThreatExplorerViewMenu.png)

Une fois que vous avez sélectionné un affichage, vous pouvez appliquer des filtres et configurer des requêtes pour effectuer une analyse plus approfondie. Les sections suivantes donnent un bref aperçu des différents affichages disponibles dans l’Explorateur (ou détections en temps réel).

## <a name="email--malware"></a>Courrier électronique > programmes malveillants

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les** programmes malveillants \> **de** \> **messagerie.** Cette vue affiche des informations sur les messages électroniques identifiés comme contenant des programmes malveillants.

![Afficher les données relatives aux e-mails identifiés comme programmes malveillants](../../media/ExplorerEmailMalwareMenu.png)

Cliquez **sur Expéditeur** pour ouvrir votre liste d’options d’affichage. Cette liste permet d’afficher les données par expéditeur, destinataire, domaine de l’expéditeur, objet, technologie de détection, état de protection, etc.

Par exemple, pour voir les actions qui ont été prises sur les messages électroniques détectés, choisissez **l’état protection** dans la liste. Sélectionnez une option, puis cliquez sur le bouton Actualiser pour appliquer ce filtre à votre rapport.

![Options d’état de la protection contre les menaces pour l’Explorateur de menaces](../../media/ThreatExplorerProtectionStatusOptions.png)

Sous le graphique, affichez plus de détails sur des messages spécifiques. Lorsque vous sélectionnez un élément dans la liste, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

![Explorateur de menaces avec le flyout ouvert](../../media/ThreatExplorerMalwareItemSelectedFlyout.png)

## <a name="email--phish"></a>Hameçonnage > courrier électronique

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher le** \> **hameçonnage de** \> **messagerie.** Cet affichage affiche les messages électroniques identifiés comme tentatives de hameçonnage.

![Afficher les données relatives aux e-mails identifiés comme tentatives d’hameçonnage](../../media/ThreatExplorerEmailPhish.png)

Cliquez **sur Expéditeur** pour ouvrir votre liste d’options d’affichage. Cette liste permet d’afficher les données par expéditeur, destinataire, domaine de l’expéditeur, adresse IP de l’expéditeur, domaine d’URL, verdict de clic, etc.

Par exemple, pour voir les actions qui ont été entreprises lorsque des personnes  ont cliqué sur des URL identifiées comme tentatives de hameçonnage, choisissez Verdict de clic dans la liste, sélectionnez une ou plusieurs options, puis cliquez sur le bouton Actualiser.

![Cliquez sur options de verdict pour le rapport d’hameçonnage](../../media/ThreatExplorerEmailPhishClickVerdictOptions.png)

Sous le graphique, affichez plus de détails sur des messages spécifiques, des clics d’URL, des URL et l’origine du courrier électronique.

![URL détectées comme hameçonnage dans les messages électroniques](../../media/ThreatExplorerEmailPhishURLs.png)

Lorsque vous sélectionnez un élément dans la liste, tel qu’une URL détectée, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

![Détails sur une URL détectée](../../media/ThreatExplorerEmailPhishURLDetails.png)

## <a name="email--submissions"></a>Envois > courrier électronique

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les** \>  \> **envois de courrier électronique.** Cette vue affiche les messages électroniques que les utilisateurs ont signalés comme courrier indésirable, non indésirable ou hameçonnage.

![Messages électroniques signalés par les utilisateurs](../../media/ThreatExplorerEmailUserReportedViewOptions.png)

Cliquez **sur Expéditeur** pour ouvrir votre liste d’options d’affichage. Cette liste permet d’afficher des informations par expéditeur, destinataire, type de rapport (la détermination de l’utilisateur que le courrier était indésirable, non indésirable ou hameçonnage), et bien plus encore.

Par exemple, pour afficher des informations sur les messages  électroniques signalés comme tentatives d’hameçonnage, cliquez sur Type de rapport de l’expéditeur, sélectionnez Hameçonnage, puis cliquez sur le \> bouton Actualiser. 

![Hameçonnage sélectionné pour le filtre Type de rapport](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, l’adresse IP de l’expéditeur, l’utilisateur qui a signalé le message comme courrier indésirable, non indésirable ou hameçonnage, etc.

![Messages signalés comme tentatives de hameçonnage](../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png)

Sélectionnez un élément dans la liste pour afficher des détails supplémentaires.

## <a name="email--all-email"></a>Courrier électronique > tous les messages électroniques

Pour afficher ce rapport, dans l’Explorateur, choisissez **Afficher tous** \> **les messages** \> **électroniques.** Cette vue présente une vue d’ensemble de l’activité de messagerie, y compris les messages électroniques identifiés comme malveillants en raison de l’hameçonnage ou des programmes malveillants, ainsi que tous les messages non malveillants (courrier électronique normal, courrier indésirable et courrier en nombre).

> [!NOTE]
> Si vous obtenez une erreur qui lit trop de données à **afficher,** ajoutez un filtre et, si nécessaire, réduisez la plage de dates que vous affichez.

Pour appliquer un filtre, choisissez **Expéditeur,** sélectionnez un élément dans la liste, puis cliquez sur le bouton Actualiser. Dans notre exemple, nous avons utilisé **la technologie de détection** comme filtre (plusieurs options sont disponibles). Afficher les informations par expéditeur, domaine de l’expéditeur, destinataires, objet, nom de fichier de pièce jointe, famille de programmes malveillants, état de protection (actions prises par vos fonctionnalités et stratégies de protection contre les menaces dans Office 365), technologie de détection (détection des programmes malveillants) et bien plus encore.

![Afficher les données sur le courrier électronique détecté par la technologie de détection](../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png)

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, le destinataire, l’expéditeur, l’état, etc.

## <a name="content--malware"></a>Programme malveillant > contenu

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les** programmes \> **malveillants de** \> **contenu.** Cette vue affiche les fichiers identifiés comme malveillants par Microsoft Defender pour [Office 365 dans SharePoint Online, OneDrive](atp-for-spo-odb-and-teams.md)Entreprise et Microsoft Teams.

Afficher les informations par famille de programmes malveillants, technologie de détection (détection des programmes malveillants) et charge de travail (OneDrive, SharePoint ou Teams).

![Afficher les données sur les programmes malveillants détectés](../../media/d11dc568-b091-4159-b261-df13d76b520b.png)

Sous le graphique, affichez plus de détails sur des fichiers spécifiques, tels que le nom de fichier de pièce jointe, la charge de travail, la taille du fichier, qui a modifié le fichier en dernier, et bien plus encore.

## <a name="click-to-filter-capabilities"></a>Fonctionnalités « Cliquer pour filtrer »

Avec l’Explorateur (et les détections en temps réel), vous pouvez appliquer un filtre en un clic. Cliquez sur un élément dans la légende et cet élément devient un filtre pour le rapport. Par exemple, supposons que nous regardions la vue Programmes malveillants dans l’Explorateur :

![Accès à l’Explorateur de gestion des \> menaces](../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png)

Le fait de **cliquer sur la déstonation atp** dans ce graphique entraîne une vue comme celle-ci :

![Explorateur filtré pour afficher uniquement les résultats de la détonation de Defender pour Office 365](../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png)

Dans cette vue, nous regardons maintenant les données des fichiers qui ont été détonés par des [pièces jointes sécurisées.](atp-safe-attachments.md) Sous le graphique, nous pouvons voir des détails sur des messages électroniques spécifiques dont des pièces jointes ont été détectées par des pièces jointes sécurisées.

![Détails spécifiques sur les messages électroniques avec pièces jointes détectées](../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png)

La sélection d’un ou de plusieurs éléments active le menu **Actions,** qui propose plusieurs choix parmi lesquels choisir pour les éléments sélectionnés.

![La sélection d’un élément active le menu Actions](../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png)

La possibilité de filtrer en un clic et d’accéder à des détails spécifiques peut vous faire gagner beaucoup de temps pour examiner les menaces.

## <a name="queries-and-filters"></a>Requêtes et filtres

L’Explorateur (ainsi que le rapport de détections en temps réel) dispose de plusieurs filtres et fonctionnalités d’interrogation puissants qui vous permettent d’explorer des détails, tels que les utilisateurs les plus ciblés, les principales familles de programmes malveillants, la technologie de détection et bien plus encore. Chaque type de rapport offre de nombreuses façons d’afficher et d’explorer des données.

> [!IMPORTANT]
> N’utilisez pas de caractères génériques, tels qu’un astérisque ou un point d’interrogation, dans la barre de requête de l’Explorateur (ou détections en temps réel). Lorsque vous recherchez des messages électroniques dans le champ Objet, l’Explorateur (ou détections en temps réel) effectue une correspondance partielle et produit des résultats semblables à une recherche par caractères génériques. 
