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
ms.localizationpriority: medium
search.appverid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Découvrez comment utiliser l’Explorateur de menaces et le rapport de détections en temps réel pour examiner les menaces dans le portail Microsoft 365 Defender et y répondre.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 65fa6e3f1c591f41544a1450def3e05259be3b6a
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474946"
---
# <a name="views-in-threat-explorer-and-real-time-detections"></a>Affichages dans l’Explorateur de menaces et détections en temps réel

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)


:::image type="content" source="../../media/explorer.png" alt-text="Page Explorateur de menaces" lightbox="../../media/explorer.png":::

[L’Explorateur](threat-explorer.md) de menaces (et le rapport de détections en temps réel) est un outil puissant, quasiment en temps réel, qui permet aux équipes des opérations de sécurité d’examiner les menaces sur le portail Microsoft 365 Defender et de répondre à ces menaces. L’Explorateur (et le rapport de détections en temps réel) affiche des informations sur les programmes malveillants et le hameçonnage suspectés dans le courrier électronique et les fichiers dans Office 365, ainsi que d’autres menaces et risques de sécurité pour votre organisation.

- Si vous avez [Microsoft Defender pour Office 365](defender-for-office-365.md) Plan 2, vous avez Explorer.
- Si vous avez Microsoft Defender pour Office 365 Plan 1, vous avez des détections en temps réel.

Lorsque vous ouvrez l’Explorateur pour la première fois (ou le rapport de détections en temps réel), l’affichage par défaut affiche les détections de programmes malveillants de messagerie électronique au cours des 7 derniers jours. Ce rapport peut également afficher les détections de Microsoft Defender pour Office 365, telles que les URL malveillantes détectées par [liens fiables](safe-links.md)et les fichiers malveillants détectés par [pièces jointes fiables](safe-attachments.md). Ce rapport peut être modifié pour afficher les données des 30 derniers jours (avec un abonnement Payant Microsoft Defender Office 365 P2). Les abonnements à la version d’essai incluent uniquement les données des sept derniers jours.

|Abonnement|Utilitaire|Jours de données|
|---|---|---|
|Version d’Office 365 Microsoft Defender pour P1|Détections en temps réel|7 |
|Microsoft Defender pour Office 365 P1 payant|Détections en temps réel|30|
|Microsoft Defender pour les tests Office 365 P1 payants Defender pour Office 365 version d’évaluation P2|Threat Explorer|7 |
|Version d’Office 365 Microsoft Defender pour P2|Threat Explorer|7 |
|Microsoft Defender pour Office 365 P2 payant|Threat Explorer|30|

> [!NOTE]
> Nous étendons bientôt la limite de rétention et de recherche des données de l’Explorateur (et des détections en temps réel) pour les clients d’essai de 7 à 30 jours. Cette modification est en cours de suivi dans le cadre de l’élément de feuille de route n. 70544 et est actuellement en phase de déploiement.

Utilisez le menu **Affichage** pour modifier les informations affichées. Les bulles vous aident à déterminer l’affichage à utiliser.

:::image type="content" source="../../media/all-email.png" alt-text="Menu Affichage de l’Explorateur de menaces" lightbox="../../media/all-email.png":::

Une fois que vous avez sélectionné un affichage, vous pouvez appliquer des filtres et configurer des requêtes pour effectuer une analyse plus approfondie. Les sections suivantes fournissent une brève vue d’ensemble des différents affichages disponibles dans l’Explorateur (ou détections en temps réel).

## <a name="email--malware"></a>Courrier électronique > programmes malveillants

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les programmes malveillants** \> **de** \> **messagerie**. Cet affichage affiche des informations sur les messages électroniques identifiés comme contenant des programmes malveillants.

:::image type="content" source="../../media/detection-technology.png" alt-text="Afficher les données relatives aux messages électroniques identifiés comme programmes malveillants" lightbox="../../media/detection-technology.png":::

Cliquez **sur Expéditeur** pour ouvrir votre liste d’options d’affichage. Cette liste permet d’afficher les données par expéditeur, destinataire, domaine de l’expéditeur, objet, technologie de détection, état de protection, etc.

Par exemple, pour voir les actions qui ont été prises sur les messages électroniques détectés, choisissez **l’état protection** dans la liste. Sélectionnez une option, puis cliquez sur le bouton Actualiser pour appliquer ce filtre à votre rapport.

:::image type="content" source="../../media/ThreatExplorerProtectionStatusOptions.png" alt-text="Options d’état de la protection contre les menaces pour l’Explorateur de menaces" lightbox="../../media/ThreatExplorerProtectionStatusOptions.png":::

Sous le graphique, affichez plus de détails sur des messages spécifiques. Lorsque vous sélectionnez un élément dans la liste, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

:::image type="content" source="../../media/ThreatExplorerMalwareItemSelectedFlyout.png" alt-text="Explorateur de menaces avec le flyout ouvert" lightbox="../../media/ThreatExplorerMalwareItemSelectedFlyout.png":::

## <a name="email--phish"></a>Hameçonnage > courrier électronique

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher le** \> **hameçonnage de** \> **messagerie**. Cet affichage affiche les messages électroniques identifiés comme tentatives de hameçonnage.

:::image type="content" source="../../media/phish.png" alt-text="Affichage des données relatives aux e-mails identifiés comme tentatives de hameçonnage" lightbox="../../media/phish.png":::

Cliquez **sur Expéditeur** pour ouvrir votre liste d’options d’affichage. Cette liste permet d’afficher les données par expéditeur, destinataire, domaine de l’expéditeur, adresse IP de l’expéditeur, domaine d’URL, verdict de clic, etc.

Par exemple, pour voir les actions qui ont été entreprises lorsque des utilisateurs ont cliqué sur des URL identifiées comme tentatives d’hameçonnage, choisissez Verdict de clic dans la liste, sélectionnez une ou plusieurs options, puis cliquez sur le bouton Actualiser.

:::image type="content" source="../../media/click-verdict.png" alt-text="Options de verdict de clic pour le rapport d’hameçonnage" lightbox="../../media/click-verdict.png":::

Sous le graphique, affichez plus de détails sur des messages spécifiques, des clics d’URL, des URL et l’origine du courrier électronique.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLs.png" alt-text="URL détectées comme hameçonnage dans les messages électroniques" lightbox="../../media/ThreatExplorerEmailPhishURLs.png":::

Lorsque vous sélectionnez un élément dans la liste, tel qu’une URL détectée, un volet volant s’ouvre, où vous pouvez en savoir plus sur l’élément que vous avez sélectionné.

:::image type="content" source="../../media/ThreatExplorerEmailPhishURLDetails.png" alt-text="Détails sur une URL détectée" lightbox="../../media/ThreatExplorerEmailPhishURLDetails.png":::

## <a name="email--submissions"></a>Envois > courrier électronique

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les** \> **envois** \> **de courrier électronique**. Cette vue affiche les messages électroniques que les utilisateurs ont signalés comme courrier indésirable, non indésirable ou hameçonnage.

:::image type="content" source="../../media/ThreatExplorerEmailUserReportedViewOptions.png" alt-text="Messages électroniques signalés par les utilisateurs" lightbox="../../media/ThreatExplorerEmailUserReportedViewOptions.png":::

Cliquez **sur Expéditeur** pour ouvrir votre liste d’options d’affichage. Cette liste permet d’afficher des informations par expéditeur, destinataires, type de rapport (la détermination de l’utilisateur que le courrier était indésirable, non indésirable ou hameçonnage), et bien plus encore.

Par exemple, pour afficher des informations sur les messages électroniques signalés comme tentatives d’hameçonnage,  \> cliquez sur **Type** de rapport de l’expéditeur, sélectionnez **Hameçonnage,** puis cliquez sur le bouton Actualiser.

![Hameçonnage sélectionné pour le filtre Type de rapport.](../../media/ThreatExplorerEmailUserReportedPhishSelected.png)

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, l’adresse IP de l’expéditeur, l’utilisateur qui a signalé le message comme courrier indésirable, non indésirable ou hameçonnage, etc.

:::image type="content" source="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png" alt-text="Messages signalés comme tentatives de hameçonnage" lightbox="../../media/ThreatExplorerEmailPhishUserReportedPhishDetails.png":::

Sélectionnez un élément dans la liste pour afficher des détails supplémentaires.

## <a name="email--all-email"></a>Courrier électronique > tous les messages électroniques

Pour afficher ce rapport, dans l’Explorateur, **sélectionnez Afficher tous** \> **les messages** \> **électroniques**. Cette vue présente une vue d’ensemble de l’activité de messagerie, y compris les e-mails identifiés comme malveillants en raison de l’hameçonnage ou des programmes malveillants, ainsi que tous les messages non malveillants (courrier électronique normal, courrier indésirable et courrier en nombre).

> [!NOTE]
> Si vous obtenez une erreur qui lit trop de données à **afficher,** ajoutez un filtre et, si nécessaire, réduisez la plage de dates que vous affichez.

Pour appliquer un filtre, choisissez **Expéditeur**, sélectionnez un élément dans la liste, puis cliquez sur le bouton Actualiser. Dans notre exemple, nous avons utilisé **la technologie De détection** comme filtre (plusieurs options sont disponibles). Afficher les informations par expéditeur, domaine de l’expéditeur, destinataires, objet, nom de fichier de pièce jointe, famille de programmes malveillants, état de protection (actions prises par vos fonctionnalités et stratégies de protection contre les menaces dans Office 365), technologie de détection (détection des programmes malveillants) et bien plus encore.

:::image type="content" source="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png" alt-text="Affichage des données sur le courrier électronique détecté par la technologie de détection" lightbox="../../media/0c032eb3-6021-4174-9f06-ff8f30c245ca.png":::

Sous le graphique, affichez plus de détails sur des messages électroniques spécifiques, tels que la ligne d’objet, le destinataire, l’expéditeur, l’état, etc.

## <a name="content--malware"></a>Programme malveillant > contenu

Pour afficher ce rapport, dans l’Explorateur (ou détections en temps réel), choisissez **Afficher les programmes** \> **malveillants de** \> **contenu**. Cette vue affiche les fichiers identifiés comme malveillants par [Microsoft Defender pour Office 365 dans SharePoint Online, OneDrive Entreprise et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Afficher les informations par famille de programmes malveillants, technologie de détection (détection des programmes malveillants) et charge de travail (OneDrive, SharePoint ou Teams).

:::image type="content" source="../../media/malware-family.png" alt-text="Affichage des données sur les programmes malveillants détectés" lightbox="../../media/malware-family.png":::

Sous le graphique, affichez plus de détails sur des fichiers spécifiques, tels que le nom de fichier de pièce jointe, la charge de travail, la taille du fichier, qui a modifié le fichier en dernier, et bien plus encore.

## <a name="click-to-filter-capabilities"></a>Fonctionnalités « Cliquer pour filtrer »

Avec l’Explorateur (et les détections en temps réel), vous pouvez appliquer un filtre en un clic. Cliquez sur un élément dans la légende et cet élément devient un filtre pour le rapport. Par exemple, supposons que nous regardions la vue Programmes malveillants dans l’Explorateur :

:::image type="content" source="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png" alt-text="Page Explorateur dans le portail de sécurité & conformité" lightbox="../../media/cab32fa2-66f1-4ad5-bc1d-2bac4dbeb48c.png":::

Le fait de **cliquer sur la déstonation atp** dans ce graphique entraîne un affichage comme celui-ci :

:::image type="content" source="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png" alt-text="L’Explorateur a été filtré pour afficher uniquement defender pour les Office 365 de détonation" lightbox="../../media/7241d7dd-27bc-467d-9db8-6e806c49df14.png":::

Dans cette vue, nous regardons maintenant les données des fichiers qui ont été désaxtérées par [Coffre pièces jointes](safe-attachments.md). Sous le graphique, nous pouvons voir des détails sur des messages électroniques spécifiques dont les pièces jointes ont été détectées Coffre pièces jointes.

:::image type="content" source="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png" alt-text="Détails spécifiques sur les messages électroniques avec pièces jointes détectées" lightbox="../../media/c91fb05c-d1d4-4085-acc6-f7008a415c2a.png":::

La sélection d’un ou de plusieurs éléments active le menu **Actions** , qui propose plusieurs choix parmi lesquels choisir les éléments sélectionnés.

:::image type="content" source="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png" alt-text="Processus de sélection d’un élément qui active le menu Actions" lightbox="../../media/95f127a4-1b2a-4a76-88b9-096e3ba27d1b.png":::

La possibilité de filtrer en un clic et d’accéder à des détails spécifiques peut vous faire gagner beaucoup de temps pour examiner les menaces.

## <a name="queries-and-filters"></a>Requêtes et filtres

L’Explorateur (ainsi que le rapport de détections en temps réel) dispose de plusieurs filtres et fonctionnalités d’interrogation puissants qui vous permettent d’explorer des détails, tels que les utilisateurs les plus ciblés, les principales familles de programmes malveillants, la technologie de détection et bien plus encore. Chaque type de rapport offre de nombreuses façons d’afficher et d’explorer des données.

> [!IMPORTANT]
> N’utilisez pas de caractères génériques, tels qu’un astérisque ou un point d’interrogation, dans la barre de requête de l’Explorateur (ou détections en temps réel). Lorsque vous recherchez des  messages électroniques dans le champ Objet, l’Explorateur (ou détections en temps réel) effectue une correspondance partielle et produit des résultats semblables à une recherche par caractères génériques.
