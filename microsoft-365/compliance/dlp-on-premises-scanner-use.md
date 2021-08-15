---
title: Utiliser le scanner local de prévention des pertes de données Microsoft 365
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Découvrez comment utiliser le scanneur de protection contre la perte de données Microsoft 365 en local pour analyser les données au repos, puis implémenter des actions de protection pour les partages de fichiers locaux, pour les dossiers locaux et les bibliothèques de documents SharePoint locales.
ms.openlocfilehash: 60befcd3ba35fe900c9fd90f84b484f9c49c280a53f7e6f31cd5ab17e729c34b
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53850974"
---
# <a name="use-the-microsoft-365-data-loss-prevention-on-premises-scanner"></a>Utiliser le scanner local de prévention des pertes de données Microsoft 365 

Pour vous familiariser avec les fonctionnalités locales DLP et la manière dont elles se trouvent dans les stratégies DLP, nous avons rassemblé certains scénarios que vous pouvez suivre.

> [!IMPORTANT]
> Ces scénarios locaux DLP ne sont pas les procédures officielles de création et de réglage des stratégies DLP. Reportez-vous aux rubriques ci-dessous lorsque vous devez utiliser les stratégies DLP dans les situations générales suivantes :
>
> - [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
> - [Prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md)
> - [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
> - [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)

### <a name="scenario-discover-files-matching-dlp-rules"></a>Scénario : découvrir les fichiers correspondant aux règles DLP

Les données du scanneur local DLP apparaissent dans plusieurs zones

#### <a name="activity-explorer"></a>Explorateur d’activités

 Microsoft DLP en local détecte les correspondances de règles DLP, puis les signale à [l’Explorateur d’activités](https://compliance.microsoft.com/dataclassification?viewid=activitiesexplorer).

#### <a name="microsoft-365-audit-log"></a>Journal d’audit Microsoft 365

Les correspondances de règle DLP sont disponibles dans l'interface utilisateur du journal d'audit, voir [Rechercher le journal d'audit dans le centre de conformité](search-the-audit-log-in-security-and-compliance.md) ou accessible par [Search-UnifiedAuditLog](/powershell/module/exchange/search-unifiedauditlog) dans PowerShell.

#### <a name="aip"></a>AIP

Les données de découverte sont disponibles dans un rapport local au format csv stocké sous :

**%localappdata%\Microsoft\MSIP\Scanner\Reports\DetailedReport_%timestamp%.csv report**.

 Recherchez les colonnes suivantes :

- Mode DLP
- État DLP
- Commentaire DLP
- Nom de la règle DLP
- Actions DLP 
- Propriétaire
- Autorisations NTFS actuelles (SDDL)
- Autorisations NTFS appliquées (SDDL)
- Type d’autorisations NTFS

### <a name="scenario-enforce-dlp-rule"></a>Scénario : appliquer une règle DLP

Si vous souhaitez appliquer des règles DLP aux fichiers analysés, vous devez activer la mise en application sur le travail d’analyse de contenu dans AIP et au niveau de la stratégie dans DLP.

#### <a name="configure-dlp-to-enforce-policy-actions"></a>Configurer DLP pour appliquer les actions de la stratégie

1. Ouvrez la [page Protection contre la perte de données](https://compliance.microsoft.com/datalossprevention?viewid=policies), puis sélectionnez la stratégie DLP ciblée pour les référentiels d’emplacements locaux que vous avez configurés dans AIP.
2. Modifiez la stratégie.
3. À la page **Test or turn on the policy** (Tester ou activer la stratégie), **Yes, turn it on right away** (Oui, l’activer immédiatement).

## <a name="see-also"></a>Voir aussi

- [En savoir plus sur le scanneur local de protection contre la perte de données](dlp-on-premises-scanner-learn.md)
- [Prise en main du scanner local de protection contre la perte de données](dlp-on-premises-scanner-get-started.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
