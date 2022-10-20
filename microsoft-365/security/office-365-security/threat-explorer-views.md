---
title: Affichages dans l’Explorateur de menaces et détections en temps réel
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
ms.date: 05/15/2020
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Découvrez comment utiliser l’Explorateur de menaces et le rapport de détections en temps réel pour examiner et répondre aux menaces dans le portail Microsoft 365 Defender.
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: dae696dea94a821a2fd3ae7b9fc6b175587bb246
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68628442"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Affichages dans l’Explorateur de menaces et détections en temps réel

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

:::image type="content" source="../../media/explorer.png" alt-text="Page Explorateur de menaces" lightbox="../../media/explorer.png":::

[L’Explorateur de menaces](threat-explorer.md) (et le rapport de détections en temps réel) est un outil puissant, en quasi-temps réel, qui permet aux équipes des opérations de sécurité d’examiner et de répondre aux menaces dans le portail Microsoft 365 Defender. L’Explorateur (et le rapport de détections en temps réel) affiche des informations sur les programmes malveillants suspects et les hameçonnages dans les e-mails et les fichiers dans Office 365, ainsi que d’autres menaces et risques de sécurité pour votre organisation.

- Si vous avez [Microsoft Defender pour Office 365](defender-for-office-365.md) plan 2, vous disposez de l’Explorateur.
- Si vous avez Microsoft Defender pour Office 365 Plan 1, vous disposez de détections en temps réel.

Lorsque vous ouvrez l’Explorateur pour la première fois (ou le rapport de détections en temps réel), l’affichage par défaut affiche les détections de programmes malveillants par e-mail au cours des 7 derniers jours. Ce rapport peut également afficher les détections de Microsoft Defender pour Office 365, telles que les URL malveillantes détectées par [liens fiables](safe-links.md)et les fichiers malveillants détectés par [pièces jointes fiables](safe-attachments.md). Ce rapport peut être modifié pour afficher les données des 30 derniers jours (avec un abonnement Payant Microsoft Defender Office 365 P2). Les abonnements à la version d’essai incluent uniquement les données des sept derniers jours.

|Abonnement|Utilitaire|Jours de données|
|---|---|---|
|Microsoft Defender pour Office 365 version d’évaluation P1|Détections en temps réel|7 |
|Microsoft Defender pour Office 365 P1 payé|Détections en temps réel|30|
|Microsoft Defender pour Office 365 test payant P1 Defender pour Office 365 version d’évaluation P2|Threat Explorer|7 |
|Microsoft Defender pour Office 365 version d’évaluation P2|Threat Explorer|7 |
|Microsoft Defender pour Office 365 P2 payé|Threat Explorer|30|

> [!NOTE]
> Nous étendrons bientôt la conservation des données de l’Explorateur (et les détections en temps réel) et la limite de recherche pour les locataires d’essai de 7 à 30 jours. Cette modification fait l’objet d’un suivi dans le cadre de l’élément de feuille de route n° 70544 et est actuellement en phase de déploiement.

Utilisez le menu **Affichage** pour modifier les informations affichées. Les bulles vous aident à déterminer l’affichage à utiliser.

:::image type="content" source="../../media/all-email.png" alt-text="Menu Affichage de l’Explorateur de menaces" lightbox="../../media/all-email.png":::

Une fois que vous avez sélectionné un affichage, vous pouvez appliquer des filtres et configurer des requêtes pour effectuer une analyse plus approfondie. Les sections suivantes fournissent une brève vue d’ensemble des différentes vues disponibles dans l’Explorateur (ou les détections en temps réel).

## <a name="email--malware"></a>programme malveillant Email >

Pour afficher ce rapport, dans l’Explorateur (ou dans les détections en temps réel), choisissez **Afficher** \> **Email** \> **programmes malveillants**. Cette vue affiche des informations sur les messages électroniques identifiés comme contenant des programmes malveillants.

:::image type="content" source="../../media/detection-technology.png" alt-text="Afficher les données sur les e-mails identifiés comme programmes malveillants" lightbox="../../media/detection-technology.png":::

Cliquez sur **Sender** pour ouvrir votre liste d’options d’affichage. Utilisez cette liste pour afficher les données par expéditeur, destinataires, domaine de l’expéditeur, objet, technologie de détection, état de protection, etc.

Par exemple, pour voir quelles actions ont été effectuées sur les messages électroniques détectés, choisissez **l’état de protection** dans la liste. Sélectionnez une option, puis cliquez sur le bouton Actualiser pour appliquer ce filtre à votre rapport.

:::image type="content" source="../../media/ThreatExplorerProtectionStatusOptions.png" alt-text="Options d’état de la protection contre les menaces pour l’Explorateur de menaces" lightbox="../../media/ThreatExplorerProtectionStatusOptions.png":::

Sous le graphique, affichez plus de détails sur des messages spécifiques. Lorsque vous sélectionnez un élément dans la liste, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

:::image type="content" source="../../media/ThreatExplorerMalwareItemSelectedFlyout.png" alt-text="Explorateur de menaces avec menu volant ouvert" lightbox="../../media/ThreatExplorerMalwareItemSelectedFlyout.png":::

## <a name="email--phish"></a>Email > Phish

Pour afficher ce rapport, dans l’Explorateur (ou dans les détections en temps réel), choisissez **Afficher** \> **Email** \> **Phish**. Cette vue affiche les messages électroniques identifiés comme tentatives d’hameçonnage.

:::image type="content" source="../../media/phish.png" alt-text="Afficher les données sur les e-mails identifiés comme tentatives d’hameçonnage" lightbox="../../media/phish.png":::

Cliquez sur **Sender** pour ouvrir votre liste d’options d’affichage. Utilisez cette liste pour afficher les données par expéditeur, destinataires, domaine de l’expéditeur, adresse IP de l’expéditeur, domaine d’URL, cliquez sur verdict, etc.

Par exemple, pour voir quelles actions ont été effectuées lorsque des personnes cliquent sur des URL identifiées comme tentatives d’hameçonnage, choisissez **Cliquez sur Verdict** dans la liste, sélectionnez une ou plusieurs options, puis cliquez sur le bouton Actualiser.

:::image type="content" source="../../media/click-verdict.png" alt-text="Options click verdict pour le rapport Phish" lightbox="../../media/click-verdict.png":::

Sous le graphique, affichez plus de détails sur des messages spécifiques, des clics d’URL, des URL et l’origine du courrier électronique.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLs.png" alt-text="URL détectées comme hameçonnage dans les e-mails" lightbox="../../media/ThreatExplorerEmailPhishURLs.png":::

Lorsque vous sélectionnez un élément dans la liste, tel qu’une URL détectée, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLDetails.png" alt-text="Détails sur une URL détectée" lightbox="../../media/ThreatExplorerEmailPhishURLDetails.png":::

## <a name="email--submissions"></a>Email > soumissions

Pour afficher ce rapport, dans l’Explorateur (ou dans les détections en temps réel), choisissez **Afficher** \> **Email** \> **Soumissions**. Cette vue affiche les e-mails signalés par les utilisateurs comme indésirables, et non comme courrier indésirable ou hameçonnage.

:::image type="content" source="../../media/ThreatExplorerEmailUserReportedViewOptions.png" alt-text="Messages Email signalés par les utilisateurs" lightbox="../../media/ThreatExplorerEmailUserReportedViewOptions.png":::

Cliquez sur **Sender** pour ouvrir votre liste d’options d’affichage. Utilisez cette liste pour afficher les informations par expéditeur, destinataires, type de rapport (la détermination de l’utilisateur que l’e-mail était indésirable, pas indésirable ou hameçonnage), etc.

Par exemple, pour afficher des informations sur les messages électroniques signalés comme tentatives d’hameçonnage, cliquez sur Type **de rapport** **de l’expéditeur**\>, sélectionnez **Hameçonnage**, puis cliquez sur le bouton Actualiser.

![Hameçonnage sélectionné pour le filtre Type de rapport.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, l’adresse IP de l’expéditeur, l’utilisateur qui a signalé le message comme indésirable, pas comme indésirable ou hameçonnage, etc.

:::image type="content" source="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png" alt-text="Messages signalés comme tentatives d’hameçonnage" lightbox="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png":::

Sélectionnez un élément dans la liste pour afficher des détails supplémentaires.

## <a name="email--all-email"></a>Email > tous les e-mails

Pour afficher ce rapport, dans l’Explorateur, choisissez **Afficher** \> **Email** \> **Tous les messages**. Cette vue affiche une vue d’ensemble de l’activité de messagerie, y compris les e-mails identifiés comme malveillants en raison du hameçonnage ou des programmes malveillants, ainsi que tous les messages non malveillants (courrier électronique normal, courrier indésirable et courrier en bloc).

> [!NOTE]
> Si vous obtenez une erreur qui lit **trop de données à afficher**, ajoutez un filtre et, si nécessaire, réduisez la plage de dates que vous affichez.

Pour appliquer un filtre, choisissez **Expéditeur**, sélectionnez un élément dans la liste, puis cliquez sur le bouton Actualiser. Dans notre exemple, nous avons utilisé **la technologie de détection** comme filtre (plusieurs options sont disponibles). Affichez les informations par expéditeur, domaine de l’expéditeur, destinataires, objet, nom de fichier de pièce jointe, famille de programmes malveillants, état de la protection (actions effectuées par vos stratégies et fonctionnalités de protection contre les menaces dans Office 365), technologie de détection (comment le programme malveillant a été détecté) et bien plus encore.

:::image type="content" source="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png" alt-text="Données d’affichage sur les e-mails détectés par la technologie de détection" lightbox="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png":::

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, le destinataire, l’expéditeur, l’état, etc.

## <a name="content--malware"></a>Programme malveillant > de contenu

Pour afficher ce rapport, dans l’Explorateur (ou dans les détections en temps réel), choisissez **Afficher** \> les **programmes malveillants** **de contenu**\>. Cette vue montre les fichiers identifiés comme malveillants par [Microsoft Defender pour Office 365 dans SharePoint Online, OneDrive Entreprise et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Affichez les informations par famille de programmes malveillants, la technologie de détection (comment le programme malveillant a été détecté) et la charge de travail (OneDrive, SharePoint ou Teams).

:::image type="content" source="../../media/malware-family.png" alt-text="Afficher les données relatives aux programmes malveillants détectés" lightbox="../../media/malware-family.png":::

Sous le graphique, affichez plus de détails sur des fichiers spécifiques, tels que le nom de fichier de la pièce jointe, la charge de travail, la taille du fichier, la dernière modification du fichier, etc.

## <a name="click-to-filter-capabilities"></a>Fonctionnalités de filtrage en un clic

Avec l’Explorateur (et les détections en temps réel), vous pouvez appliquer un filtre en un clic. Cliquez sur un élément dans la légende et cet élément devient un filtre pour le rapport. Par exemple, supposons que nous examinons la vue Programmes malveillants dans l’Explorateur :

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Page Explorateur dans le portail sécurité & conformité" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Le fait de cliquer sur la **détonation ATP** dans ce graphique génère une vue comme celle-ci :

:::image type="content" source="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png" alt-text="L’Explorateur filtré pour afficher uniquement Defender pour Office 365 résultats de la détonation" lightbox="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png":::

Dans cette vue, nous examinons maintenant les données des fichiers qui ont été détonés par [des pièces jointes sécurisées](safe-attachments.md). Sous le graphique, nous pouvons voir des détails sur des messages électroniques spécifiques contenant des pièces jointes détectées par des pièces jointes sécurisées.

:::image type="content" source="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png" alt-text="Détails spécifiques sur les messages électroniques avec pièces jointes détectées" lightbox="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png":::

La sélection d’un ou de plusieurs éléments active le menu **Actions** , qui offre plusieurs choix parmi lesquels choisir les éléments sélectionnés.

:::image type="content" source="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png" alt-text="Processus de sélection d’un élément qui active le menu Actions" lightbox="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png":::

La possibilité de filtrer en un clic et d’accéder à des détails spécifiques peut vous faire gagner beaucoup de temps dans l’examen des menaces.

## <a name="queries-and-filters"></a>Requêtes et filtres

L’Explorateur (ainsi que le rapport de détections en temps réel) dispose de plusieurs filtres puissants et de fonctionnalités d’interrogation qui vous permettent d’explorer les détails, tels que les utilisateurs les plus ciblés, les principales familles de programmes malveillants, la technologie de détection, etc. Chaque type de rapport offre différentes façons d’afficher et d’explorer des données.

> [!IMPORTANT]
> N’utilisez pas de caractères génériques, tels qu’un astérisque ou un point d’interrogation, dans la barre de requêtes de l’Explorateur (ou des détections en temps réel). Lorsque vous recherchez des messages électroniques dans le **champ Objet** , l’Explorateur (ou les détections en temps réel) effectuent une correspondance partielle et produisent des résultats similaires à une recherche par caractères génériques.
