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
description: Découvrez comment utiliser l’Explorateur de menaces et le rapport de détections en temps réel pour examiner les menaces et y répondre dans le portail Microsoft 365 Defender.
ms.custom: seo-marvel-apr2020
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: 5861e5f4910c1ce1cbf75a408ca40c76630a47f9
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68720149"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Affichages dans l’Explorateur de menaces et détections en temps réel

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

:::image type="content" source="../../media/explorer.png" alt-text="Page De l’Explorateur des menaces" lightbox="../../media/explorer.png":::

[L’Explorateur](threat-explorer.md) de menaces (et le rapport sur les détections en temps réel) est un outil puissant et en quasi-temps réel qui permet aux équipes des opérations de sécurité d’examiner et de répondre aux menaces dans le portail Microsoft 365 Defender. L’Explorateur (et le rapport sur les détections en temps réel) affiche des informations sur les programmes malveillants et les hameçonnages suspects dans les e-mails et les fichiers dans Office 365, ainsi que sur d’autres menaces et risques de sécurité pour votre organisation.

- Si vous avez [Microsoft Defender pour Office 365](defender-for-office-365.md) Plan 2, vous disposez de l’Explorateur.
- Si vous avez Microsoft Defender pour Office 365 Plan 1, vous disposez de détections en temps réel.

Lorsque vous ouvrez l’Explorateur pour la première fois (ou le rapport de détections en temps réel), l’affichage par défaut affiche les détections de programmes malveillants par e-mail au cours des 7 derniers jours. Ce rapport peut également afficher les détections de Microsoft Defender pour Office 365, telles que les URL malveillantes détectées par [liens fiables](safe-links.md)et les fichiers malveillants détectés par [pièces jointes fiables](safe-attachments.md). Ce rapport peut être modifié pour afficher les données des 30 derniers jours (avec un abonnement Payant Microsoft Defender Office 365 P2). Les abonnements à la version d’essai incluent uniquement les données des sept derniers jours.

|Abonnement|Utilitaire|Jours de données|
|---|---|---|
|Microsoft Defender pour Office 365 essai P1|Détections en temps réel|7 |
|Microsoft Defender pour Office 365 P1 payé|Détections en temps réel|30|
|test payant Microsoft Defender pour Office 365 P1 Defender pour Office 365 essai P2|Threat Explorer|7 |
|Microsoft Defender pour Office 365 essai P2|Threat Explorer|7 |
|Microsoft Defender pour Office 365 P2 payé|Threat Explorer|30|

> [!NOTE]
> Nous allons bientôt étendre la limite de conservation et de recherche des données de l’Explorateur (et des détections en temps réel) pour les locataires d’essai de 7 à 30 jours. Cette modification fait l’objet d’un suivi dans le cadre de la feuille de route 70544 et est actuellement en phase de déploiement.

Utilisez le menu **Affichage** pour modifier les informations affichées. Les bulles vous aident à déterminer l’affichage à utiliser.

:::image type="content" source="../../media/all-email.png" alt-text="Menu Affichage de l’Explorateur de menaces" lightbox="../../media/all-email.png":::

Une fois que vous avez sélectionné un affichage, vous pouvez appliquer des filtres et configurer des requêtes pour effectuer une analyse plus approfondie. Les sections suivantes fournissent une brève vue d’ensemble des différentes vues disponibles dans l’Explorateur (ou des détections en temps réel).

## <a name="email--malware"></a>programme malveillant Email >

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher** \> **Email** \> **programmes malveillants**. Cette vue affiche des informations sur les messages électroniques identifiés comme contenant des programmes malveillants.

:::image type="content" source="../../media/detection-technology.png" alt-text="Afficher les données relatives aux e-mails identifiés comme des programmes malveillants" lightbox="../../media/detection-technology.png":::

Cliquez sur **Expéditeur** pour ouvrir votre liste d’options d’affichage. Utilisez cette liste pour afficher les données par expéditeur, destinataires, domaine de l’expéditeur, objet, technologie de détection, état de protection, etc.

Par exemple, pour voir quelles actions ont été effectuées sur les messages électroniques détectés, choisissez **État de la protection** dans la liste. Sélectionnez une option, puis cliquez sur le bouton Actualiser pour appliquer ce filtre à votre rapport.

:::image type="content" source="../../media/ThreatExplorerProtectionStatusOptions.png" alt-text="Options État de la protection contre les menaces pour l’Explorateur de menaces" lightbox="../../media/ThreatExplorerProtectionStatusOptions.png":::

Sous le graphique, affichez plus de détails sur des messages spécifiques. Lorsque vous sélectionnez un élément dans la liste, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

:::image type="content" source="../../media/ThreatExplorerMalwareItemSelectedFlyout.png" alt-text="Explorateur de menaces avec le menu volant ouvert" lightbox="../../media/ThreatExplorerMalwareItemSelectedFlyout.png":::

## <a name="email--phish"></a>Email > Hameçonnage

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher** \> **Email** \> **Hameçonnage**. Cet affichage affiche les messages électroniques identifiés comme des tentatives d’hameçonnage.

:::image type="content" source="../../media/phish.png" alt-text="Afficher les données relatives aux e-mails identifiés comme des tentatives d’hameçonnage" lightbox="../../media/phish.png":::

Cliquez sur **Expéditeur** pour ouvrir votre liste d’options d’affichage. Utilisez cette liste pour afficher les données par expéditeur, destinataires, domaine de l’expéditeur, adresse IP de l’expéditeur, domaine d’URL, verdict de clic, etc.

Par exemple, pour voir quelles actions ont été effectuées lorsque des personnes ont cliqué sur des URL identifiées comme des tentatives d’hameçonnage, choisissez **Cliquer sur verdict** dans la liste, sélectionnez une ou plusieurs options, puis cliquez sur le bouton Actualiser.

:::image type="content" source="../../media/click-verdict.png" alt-text="Options de verdict de clic pour le rapport Hameçonnage" lightbox="../../media/click-verdict.png":::

Sous le graphique, affichez plus de détails sur les messages, les clics d’URL, les URL et l’origine des e-mails spécifiques.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLs.png" alt-text="Url détectées comme hameçonnage dans les e-mails" lightbox="../../media/ThreatExplorerEmailPhishURLs.png":::

Lorsque vous sélectionnez un élément dans la liste, tel qu’une URL détectée, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLDetails.png" alt-text="Détails d’une URL détectée" lightbox="../../media/ThreatExplorerEmailPhishURLDetails.png":::

## <a name="email--submissions"></a>Email > soumissions

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher** \> **Email** \> **soumissions**. Cet affichage affiche les e-mails signalés par les utilisateurs comme courrier indésirable, et non comme courrier indésirable ou par hameçonnage.

:::image type="content" source="../../media/ThreatExplorerEmailUserReportedViewOptions.png" alt-text="Messages Email signalés par les utilisateurs" lightbox="../../media/ThreatExplorerEmailUserReportedViewOptions.png":::

Cliquez sur **Expéditeur** pour ouvrir votre liste d’options d’affichage. Utilisez cette liste pour afficher les informations par expéditeur, destinataires, type de rapport (la détermination de l’utilisateur que l’e-mail est indésirable, pas indésirable ou hameçonnage) et bien plus encore.

Par exemple, pour afficher des informations sur les messages électroniques signalés comme des tentatives d’hameçonnage, cliquez sur **Type de rapport** **de l’expéditeur**\>, sélectionnez **Hameçonnage**, puis cliquez sur le bouton Actualiser.

![Hameçonnage sélectionné pour le filtre Type de rapport.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, l’adresse IP de l’expéditeur, l’utilisateur qui a signalé le message comme étant indésirable, pas comme courrier indésirable ou hameçonnage, etc.

:::image type="content" source="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png" alt-text="Messages signalés comme tentatives d’hameçonnage" lightbox="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png":::

Sélectionnez un élément dans la liste pour afficher des détails supplémentaires.

## <a name="email--all-email"></a>Email > Tous les e-mails

Pour afficher ce rapport, dans l’Explorateur, choisissez **Afficher** \> **Email** \> **tous les messages**. Cette vue affiche une vue d’ensemble de l’activité des e-mails, y compris les e-mails identifiés comme malveillants en raison d’un hameçonnage ou d’un programme malveillant, ainsi que tous les messages non malveillants (courrier normal, courrier indésirable et courrier en bloc).

> [!NOTE]
> Si vous obtenez une erreur qui lit **Trop de données à afficher**, ajoutez un filtre et, si nécessaire, réduisez la plage de dates que vous affichez.

Pour appliquer un filtre, choisissez **Expéditeur**, sélectionnez un élément dans la liste, puis cliquez sur le bouton Actualiser. Dans notre exemple, nous avons utilisé **la technologie de détection** comme filtre (plusieurs options sont disponibles). Affichez les informations par expéditeur, domaine de l’expéditeur, destinataires, objet, nom de fichier de pièce jointe, famille de logiciels malveillants, état de protection (actions effectuées par vos fonctionnalités et stratégies de protection contre les menaces dans Office 365), technologie de détection (comment le programme malveillant a été détecté) et bien plus encore.

:::image type="content" source="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png" alt-text="Afficher les données sur les e-mails détectés par la technologie de détection" lightbox="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png":::

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, le destinataire, l’expéditeur, l’état, etc.

## <a name="content--malware"></a>Programme malveillant > de contenu

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les** \> **programmes malveillants** **de contenu**\>. Cette vue affiche les fichiers identifiés comme malveillants par [Microsoft Defender pour Office 365 dans SharePoint Online, OneDrive Entreprise et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Affichez les informations par famille de programmes malveillants, technologie de détection (comment le programme malveillant a été détecté) et charge de travail (OneDrive, SharePoint ou Teams).

:::image type="content" source="../../media/malware-family.png" alt-text="Afficher les données sur les programmes malveillants détectés" lightbox="../../media/malware-family.png":::

Sous le graphique, vous trouverez plus de détails sur des fichiers spécifiques, tels que le nom de fichier de la pièce jointe, la charge de travail, la taille du fichier, la dernière modification du fichier, etc.

## <a name="click-to-filter-capabilities"></a>Fonctionnalités « Démarrer en un clic »

Avec l’Explorateur (et les détections en temps réel), vous pouvez appliquer un filtre en un clic. Cliquez sur un élément dans la légende et cet élément devient un filtre pour le rapport. Par exemple, si vous cliquez sur **La détonation ATP** dans ce graphique, une vue semblable à celle-ci est la suivante :

:::image type="content" source="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png" alt-text="L’Explorateur a filtré pour afficher uniquement Defender pour Office 365 résultats de la détonation" lightbox="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png":::

Dans cette vue, nous examinons maintenant les données des fichiers qui ont été détonés par [des pièces jointes fiables](safe-attachments.md). Sous le graphique, nous pouvons voir des détails sur des messages électroniques spécifiques contenant des pièces jointes détectées par des pièces jointes sécurisées.

:::image type="content" source="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png" alt-text="Détails spécifiques sur les messages électroniques contenant des pièces jointes détectées" lightbox="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png":::

La sélection d’un ou de plusieurs éléments active le menu **Actions** , qui offre plusieurs choix parmi lesquels choisir les éléments sélectionnés.

:::image type="content" source="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png" alt-text="Processus de sélection d’un élément qui active le menu Actions" lightbox="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png":::

La possibilité de filtrer en un clic et d’accéder à des détails spécifiques peut vous faire gagner beaucoup de temps dans l’investigation des menaces.

## <a name="queries-and-filters"></a>Requêtes et filtres

L’Explorateur (ainsi que le rapport sur les détections en temps réel) dispose de plusieurs filtres et fonctionnalités d’interrogation puissants qui vous permettent d’explorer les détails, tels que les utilisateurs les plus ciblés, les principales familles de programmes malveillants, la technologie de détection, etc. Chaque type de rapport offre une variété de façons d’afficher et d’explorer les données.

> [!IMPORTANT]
> N’utilisez pas de caractères génériques, tels qu’un astérisque ou un point d’interrogation, dans la barre de requête de l’Explorateur (ou des détections en temps réel). Lorsque vous recherchez des messages électroniques dans le **champ Objet** , l’Explorateur (ou les détections en temps réel) effectue une correspondance partielle et génère des résultats similaires à ceux d’une recherche générique.
