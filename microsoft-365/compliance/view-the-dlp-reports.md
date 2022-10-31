---
title: Affichage des rapports de protection contre la perte de données
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/7/2018
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- tier1
- purview-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
description: Utilisez les rapports DLP dans Office 365 pour afficher le nombre de correspondances de stratégie DLP, de remplacements ou de faux positifs et voir s’ils sont tendances à la hausse ou à la baisse au fil du temps.
ms.openlocfilehash: b2d006730cfa8688d664a4fc60ab13c27c7dec7f
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68793717"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Affichage des rapports de protection contre la perte de données

Après avoir créé vos stratégies de protection contre la perte de données (DLP) Microsoft Purview, vous devez vérifier qu’elles fonctionnent comme vous le souhaitez et vous aider à rester conforme. Avec les rapports DLP dans le portail de conformité Microsoft Purview, vous pouvez rapidement afficher :

- **Correspondances de stratégie DLP** Ce rapport montre le nombre de correspondances de stratégie DLP au fil du temps. Vous pouvez filtrer les rapports par date, emplacement, stratégie ou action. Vous pouvez utiliser ce rapport pour :

  - Optimiser ou affiner vos stratégies DLP lorsque vous les exécutez en mode test. Vous pouvez afficher la règle spécifique qui correspond au contenu.

  - Vous concentrer sur des périodes de temps spécifiques et comprendre les raisons des pics et des tendances.

  - Découvrir les processus d’entreprise qui enfreignent les stratégies DLP de votre organisation.

  - Comprendre l’impact professionnel des stratégies DLP en affichant les actions appliquées au contenu.

  - Vérifier la conformité avec une stratégie DLP spécifique en affichant les correspondances pour cette stratégie.

  - Afficher la liste des principaux utilisateurs et répéter les utilisateurs qui contribuent aux incidents au sein de votre organisation.

  - Consulter la liste des principaux types d’informations sensibles au sein de votre organisation.

- **Incidents DLP** Ce rapport affiche également les correspondances de stratégie au fil du temps, comme le rapport de correspondances de stratégie. Toutefois, le rapport de correspondances de stratégie affiche les correspondances au niveau d’une règle ; par exemple, si un e-mail correspond à trois règles différentes, le rapport de correspondance de stratégie affiche trois éléments de ligne différents. En revanche, le rapport d’incidents affiche les correspondances au niveau d’un élément ; Par exemple, si un e-mail correspond à trois règles différentes, le rapport d’incidents affiche un élément de ligne unique pour ce contenu.

  Étant donné que les nombres de rapports sont agrégés différemment, le rapport de correspondances de stratégie est préférable pour identifier les correspondances avec des règles spécifiques et affiner les stratégies DLP. Le rapport sur les incidents est plus pertinent pour identifier des éléments de contenu spécifiques qui posent problème pour vos stratégies protection contre la perte de données.

- **Faux positifs et remplacements DLP** Si votre stratégie DLP permet aux utilisateurs de la remplacer ou de signaler un faux positif, ce rapport affiche le nombre de ces instances au fil du temps. Vous pouvez filtrer les rapports par date, emplacement, ou stratégie. Vous pouvez utiliser ce rapport pour :

  - Optimiser ou affiner vos stratégies DLP en examinant les stratégies qui impliquent un nombre élevé de faux positifs.

  - Afficher les motifs présentés par les utilisateurs lorsqu'ils passent outre une stratégie.

  - Découvrir où les stratégies DLP entrent en conflit avec des processus professionnels valides en raison d'un nombre élevé de remplacements de l’utilisateur.

Tous les rapports DLP peuvent afficher les données de la période de quatre mois la plus récente. Les données les plus récentes peuvent nécessiter jusqu'à 24 heures avant de s’afficher dans les rapports.

Vous trouverez ces rapports dans le tableau de **bord** rapports portail de conformité Microsoft Purview  \> \>.

![La stratégie DLP correspond au rapport.](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Afficher la justification soumise par un utilisateur pour un remplacement

Si votre stratégie DLP autorise les utilisateurs à la remplacer, vous pouvez utiliser le rapport faux positifs et remplacer pour afficher le texte envoyé par les utilisateurs dans le conseil de stratégie.

![Champ de justification dans les détails du rapport de faux positif et de remplacement DLP.](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)

## <a name="take-action-on-insights-and-recommendations"></a>Agir sur les insights et les recommandations

Les rapports peuvent afficher des insights et des recommandations dans lesquels vous pouvez cliquer sur l’icône d’avertissement rouge pour afficher des détails sur les problèmes potentiels et prendre des mesures correctives possibles.

![Cliquez sur une icône d’insights pour afficher les détails et les actions à entreprendre.](../media/51782036-7299-4960-8175-75c2b1637159.png)

## <a name="permissions-for-dlp-reports"></a>Autorisations pour les rapports DLP

Pour afficher les rapports DLP dans le portail de conformité Purview, vous devez disposer des éléments suivants :

- **Rôle Lecteur de sécurité** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de l’organisation et Lecteur de la sécurité dans le Centre d’administration Exchange.

- **Rôle Afficher uniquement gestion de la conformité DLP** dans le portail de conformité Purview. Par défaut, ce rôle est attribué aux groupes de rôles Administrateur de conformité, Gestion de l’organisation, Administrateur de la sécurité et Lecteur de sécurité dans le portail de conformité Purview.

- **Rôle Afficher uniquement les destinataires** dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de la conformité, Gestion de l’organisation et Gestion de l’organisation View-Only dans le Centre d’administration Exchange.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>Rechercher les applets de commande pour les rapports DLP

Pour utiliser les applets de commande de création de rapports DLP, procédez comme suit :

1. [Se connecter à la sécurité et conformité PowerShell](/powershell/exchange/connect-to-scc-powershell)

2. Utilisez ces applets de commande :

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
   - [Get-DlpSiDetectionsReport](/powershell/module/exchange/get-dlpsidetectionsreport)

Toutefois, les rapports DLP doivent extraire des données de Microsoft 365, y compris Exchange Online. Pour cette raison, les applets de commande suivantes pour les rapports DLP sont disponibles dans Exchange Online PowerShell. Pour utiliser les applets de commande pour ces rapports DLP, procédez comme suit :

1. [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Utilisez ces applets de commande :

   - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
   - [Get-MailDetailDlpPolicyReport](/powershell/module/exchange/get-maildetaildlppolicyreport)
