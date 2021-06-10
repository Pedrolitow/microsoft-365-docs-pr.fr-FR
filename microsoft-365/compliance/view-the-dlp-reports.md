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
- M365-security-compliance
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-apr2020
description: Utilisez les rapports DLP dans Office 365 pour afficher le nombre de correspondances, remplacements ou faux positifs de stratégie DLP et voir s’ils sont à la hausse ou à la baisse au fil du temps.
ms.openlocfilehash: 742f0ef0334e714c7f31cbc2f97559993454f6b7
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50928388"
---
# <a name="view-the-reports-for-data-loss-prevention"></a>Affichage des rapports de protection contre la perte de données

Après avoir créé vos stratégies de protection contre la perte de données (DLP), vous devez vérifier qu’elles fonctionnent comme prévu et vous aident à maintenir la conformité. Avec les rapports DLP dans le Centre de conformité de &amp; sécurité, vous pouvez rapidement afficher :
  
- **Correspondances de stratégie DLP** Ce rapport indique le nombre de correspondances de stratégies DLP au fil du temps. Vous pouvez filtrer les rapports par date, emplacement, stratégie ou action. Vous pouvez utiliser ce rapport pour : 
    
  - Optimiser ou affiner vos stratégies DLP lorsque vous les exécutez en mode test. Vous pouvez afficher la règle spécifique qui correspond au contenu.
    
  - Vous concentrer sur des périodes de temps spécifiques et comprendre les raisons des pics et des tendances.
    
  - Découvrir les processus d’entreprise qui enfreignent les stratégies DLP de votre organisation.
    
  - Comprendre l’impact professionnel des stratégies DLP en affichant les actions appliquées au contenu.
    
  - Vérifier la conformité avec une stratégie DLP spécifique en affichant les correspondances pour cette stratégie.
    
  - Afficher la liste des principaux utilisateurs et répéter les utilisateurs qui contribuent aux incidents au sein de votre organisation.
    
  - Consulter la liste des principaux types d’informations sensibles au sein de votre organisation.
    
- **Incidents DLP** Ce rapport affiche également les correspondances de stratégie au fil du temps, comme le rapport de correspondances de stratégie. Toutefois, le rapport de correspondances de stratégie affiche les correspondances au niveau d’une règle ; par exemple, si un e-mail correspond à trois règles différentes, le rapport de correspondances de stratégie affiche trois lignes différentes. En revanche, le rapport des incidents affiche les correspondances au niveau de l’élément ; par exemple, si un message électronique correspond à trois règles différentes, le rapport d’incidents affiche un élément de ligne unique pour cet élément de contenu. 
    
  Étant donné que le nombre de rapports est agrégé différemment, le rapport de correspondances de stratégie est préférable pour identifier les correspondances avec des règles spécifiques et affiner les stratégies DLP. Le rapport sur les incidents est plus pertinent pour identifier des éléments de contenu spécifiques qui posent problème pour vos stratégies protection contre la perte de données.
    
- **Remplacements et faux positifs DLP** Si votre stratégie DLP permet aux utilisateurs de la remplacer ou de signaler un faux positif, ce rapport indique le nombre de ces instances au fil du temps. Vous pouvez filtrer les rapports par date, emplacement, ou stratégie. Vous pouvez utiliser ce rapport pour : 
    
  - Optimiser ou affiner vos stratégies DLP en examinant les stratégies qui impliquent un nombre élevé de faux positifs.
    
  - Afficher les motifs présentés par les utilisateurs lorsqu'ils passent outre une stratégie.
    
  - Découvrir où les stratégies DLP entrent en conflit avec des processus professionnels valides en raison d'un nombre élevé de remplacements de l’utilisateur.
    
Tous les rapports DLP peuvent afficher les données de la période de quatre mois la plus récente. Les données les plus récentes peuvent nécessiter jusqu'à 24 heures avant de s’afficher dans les rapports.
  
Vous trouverez ces rapports dans le tableau de bord des rapports du Centre de &amp; \> **conformité** \> **de sécurité.**
  
![Rapport sur les correspondances de stratégie DLP](../media/117d20c9-d379-403f-ad68-1f5cd6c4e5cf.png)
  
## <a name="view-the-justification-submitted-by-a-user-for-an-override"></a>Afficher la justification envoyée par un utilisateur pour un remplacement

Si votre stratégie DLP autorise les utilisateurs à la remplacer, vous pouvez utiliser le rapport faux positifs et remplacer pour afficher le texte envoyé par les utilisateurs dans le conseil de stratégie.
  
![Champ Justification dans les détails du rapport DLP sur les faux positifs et les remplacements](../media/e11e3126-026d-4e77-a16d-74a0686d1fa3.png)
  
## <a name="take-action-on-insights-and-recommendations"></a>Prendre des mesures sur les informations et les recommandations

Les rapports peuvent afficher des informations et des recommandations dans le cas où vous pouvez cliquer sur l’icône d’avertissement rouge pour afficher des détails sur les problèmes potentiels et prendre des mesures correctives possibles.
  
![Cliquer sur une icône d’informations pour voir les détails et les actions à prendre](../media/51782036-7299-4960-8175-75c2b1637159.png)
  
## <a name="permissions-for-dlp-reports"></a>Autorisations pour les rapports DLP

Pour afficher les rapports DLP dans le Centre de sécurité & conformité, vous devez avoir :

- **Rôle lecteur sécurité** dans le centre d Exchange’administration. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de l’organisation et Lecteur de sécurité dans Exchange’administration centrale.

- **Rôle de gestion de la conformité DLP** en affichage seul dans le Centre de sécurité & conformité. Par défaut, ce rôle est attribué aux groupes de rôles Administrateur de conformité, Gestion de l’organisation, Administrateur de la sécurité et Lecteur sécurité dans le Centre de sécurité & conformité.

- **Rôle Destinataires en affichage** seul dans le centre Exchange’administration. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de la conformité, Gestion de l’organisation View-Only Gestion de l’organisation dans Exchange d’administration.

## <a name="find-the-cmdlets-for-the-dlp-reports"></a>Rechercher les cmdlets pour les rapports DLP

Pour utiliser la plupart des applets de commande du Centre de conformité et de sécurité, vous devez :
  
1. [Connecter au Centre de conformité de sécurité à &amp; l’aide de PowerShell à distance](/powershell/exchange/connect-to-scc-powershell&amp;clcid=0x409)
    
2. Utiliser l’une de ces [ &amp; cmdlets du Centre](/powershell/exchange/exchange-online-powershell) de conformité de la sécurité
    
Toutefois, les rapports DLP doivent extraire des d’Office 365, y compris Exchange Online. Pour cette raison, les cmdlets pour les rapports DLP sont disponibles dans Exchange Online Powershell, et non dans le Centre de conformité de &amp; sécurité Powershell. Par conséquent, pour utiliser les applets de commande pour les rapports DLP, vous devez :
  
1. [Vous connecter à Exchange Online à l'aide de Remote PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)
    
2. Utilisez l’une de ces applets de commande pour les rapports DLP :
    
      - [Get-DlpDetectionsReport](/powershell/module/exchange/get-dlpdetectionsreport)
    
      - [Get-DlpDetailReport](/powershell/module/exchange/get-dlpdetailreport)
