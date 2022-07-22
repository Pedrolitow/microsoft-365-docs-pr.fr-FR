---
title: Créer des notifications pour les activités de correspondance de données exactes
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.date: ''
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
search.appverid:
- MOE150
- MET150
description: En savoir plus sur la création des notifications pour les activités de correspondance de données exactes.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 09bb41de09b6f44a9f556446c5a566322b44ad0d
ms.sourcegitcommit: 5aed330d8af523f0dffe5e392f1c79f047e38172
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2022
ms.locfileid: "66949126"
---
# <a name="create-notifications-for-exact-data-match-activities"></a>Créer des notifications pour les activités de correspondance de données exactes

Lorsque vous [créez des types d’informations sensibles personnalisés avec correspondance exacte de données (EDM),](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)un certain nombre d’activités sont créées dans le journal [d’audit.](search-the-audit-log-in-security-and-compliance.md#before-you-search-the-audit-log) Vous pouvez utiliser la cmdlet PowerShell [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert) pour créer des notifications qui vous avertiront de l’événement :

- `CreateSchema`
- `EditSchema`
- `RemoveSchema`
- `UploadDataFailed`
- `UploadDataCompleted`

> [!NOTE]
 La capacité de créer des notifications pour les activités de EDM n'est disponible que pour les clouds World Wide et de la communauté du secteur public (GCC) uniquement.

## <a name="pre-requisites"></a>Conditions préalables

Le compte que vous utilisez doit être l’un des suivants :

- Un administrateur global
- Administrateur de conformité
- Administrateur Exchange Online

Pour en avoir plus sur les autorisations DLP, consultez la section[Autorisations](data-loss-prevention-policies.md#permissions).

La classification basée sur EDM est incluse dans les abonnements suivants :

- Office 365 E5
- Microsoft 365 E5
- Microsoft 365 E5 Conformité
- Microsoft E5/A5 Information Protection et gouvernance

Si vous souhaitez en savoir plus les licences DLP, consultez la rubrique [Instructions relatives aux licences Microsoft 365 pour la sécurité et la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="configure-notifications-for-edm-activities"></a>Configurer les notifications pour les activités EDM

1. Connectez-vous au [PowerShell de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez l’applet de commande `New-ProtectionAlert` à l’aide de l’activité pour laquelle vous souhaitez créer la notification.  Par exemple, si vous souhaitez être averti de l'exécution de l'action `UploadDataCompleted`, exécutez :

    ```powershell
    New-ProtectionAlert -Name "EdmUploadCompleteAlertPolicy" -Category Others -NotifyUser <address to send notification to> -ThreatType Activity -Operation UploadDataCompleted -Description "Custom alert policy to track when EDM upload Completed" -AggregationType None
    ```
    
    Pour `UploadDataFailed` pouvez exécuter :
    
    ```powershell
    New-ProtectionAlert -Name "EdmUploadFailAlertPolicy" -Category Others -NotifyUser <SMTP address to send notification to> -ThreatType Activity -Operation UploadDataFailed -Description "Custom alert policy to track when EDM upload Failed" -AggregationType None -Severity High
    ```

## <a name="related-articles"></a>Articles connexes

- [En savoir plus sur les types d’informations sensibles exacts basés sur la correspondance de données](sit-learn-about-exact-data-match-based-sits.md#learn-about-exact-data-match-based-sensitive-information-types)
- [New-ProtectionAlert](/powershell/module/exchange/new-protectionalert)
