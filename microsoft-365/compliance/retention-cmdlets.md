---
title: Identifier les applets de commande PowerShell disponibles pour la rétention
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: normal
ms.collection:
- M365-security-compliance
- SPO_Content
- m365initiative-compliance
description: Identifiez les applets de commande PowerShell pour la rétention qui prennent en charge la configuration à grande échelle, l’automatisation ou qui peuvent être nécessaires pour les scénarios de configuration avancés.
ms.openlocfilehash: 5e31fb7b92dbc1dc83af8f7047041a7d0b4b23b2
ms.sourcegitcommit: 0c87abc17fbfe8aa43d61510101acdad0d491cd2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/05/2022
ms.locfileid: "66612148"
---
# <a name="powershell-cmdlets-for-retention-policies-and-retention-labels"></a>Applets de commande pour les stratégies et étiquettes de rétention

>*[Guide de sécurité et conformité pour les licences Microsoft 365](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance).*

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez les sections suivantes pour identifier les principales applets de commande PowerShell disponibles pour les stratégies de rétention et les étiquettes de rétention dont vous pourriez avoir besoin pour la configuration à grande échelle, les scripts automatisés ou les scénarios de configuration avancés. Pour obtenir la liste complète des applets de commande, consultez la [liste de stratégie et de rétention de conformité](/powershell/module/exchange#policy-and-compliance-retention) de la documentation PowerShell.

Avant d’utiliser ces applets de commande, vous devez d’abord vous [connecter au Centre de sécurité & conformité PowerShell](/powershell/exchange/connect-to-scc-powershell).

Dans les descriptions qui suivent, une stratégie de rétention peut faire référence à une stratégie de rétention (aucune étiquette) ou à une stratégie d’étiquette de rétention. Chaque stratégie définit s’il est statique ou adaptatif et les emplacements de la stratégie à appliquer. La stratégie nécessite ensuite une règle pour terminer la configuration.

Par exemple :
- Une stratégie de rétention a besoin d’une règle qui définit les paramètres de rétention, tels que la conservation pendant cinq ans, puis la suppression.

Lorsque vous utilisez des étiquettes de rétention, celles-ci contiennent les paramètres de rétention et leurs stratégies ont besoin de règles différentes :
- Une stratégie d’étiquette de rétention que vous publiez nécessite une règle qui définit les étiquettes qui doivent être affichées dans les applications.
- Une stratégie d’étiquette de rétention d’application automatique a besoin d’une règle qui définit l’étiquette à appliquer et les conditions d’application de l’étiquette.

## <a name="retention-cmdlets-for-most-locations"></a>Applets de commande de rétention pour la plupart des emplacements

Utilisez les applets de commande du tableau suivant lorsque les emplacements sont **e-mail Exchange**, **sites SharePoint**, **comptes OneDrive**, **Groupes Microsoft 365**, **Skype Entreprise**, **dossiers publics Exchange**, **messages de conversation Teams** ou **messages de canal Teams**.

N’utilisez pas ces applets de commande lorsque les emplacements sont pour les messages de canal privé Teams, les messages utilisateur Yammer ou les messages de la communauté Yammer. Ces emplacements ont d’autres applets de commande qui sont identifiées dans la [section suivante](#retention-cmdlets-specific-to-teams-private-channels-and-yammer).

|Applet de commande|Description|Emplacements applicables|
|:-----|:-----|:-----|:-----|
|[Enable-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) <br /><br /> [Get-ComplianceTagStorage](/powershell/module/exchange/enable-compliancetagstorage) |Opération unique pour créer un stockage ou afficher ce stockage pour les étiquettes de rétention |La messagerie électronique Exchange <br /><br />Sites SharePoint <br /><br /> Comptes OneDrive <br /><br /> Groupes Microsoft 365|
|[Get-ComplianceTag](/powershell/module/exchange/get-compliancetag)<br /><br> [New-ComplianceTag](/powershell/module/exchange/new-compliancetag) <br /><br> [Remove-ComplianceTag](/powershell/module/exchange/remove-compliancetag) <br /><br> [Set-ComplianceTag](/powershell/module/exchange/set-compliancetag) |Afficher, créer, supprimer, configurer des étiquettes de rétention |La messagerie électronique Exchange <br /><br /> Sites SharePoint <br /><br /> Comptes OneDrive<br /><br /> Groupes Microsoft 365|
|[Get-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/get-recordreviewnotificationtemplateconfig) <br /><br /> [Set-RecordReviewNotificationTemplateConfig](/powershell/module/exchange/remove-retentioncompliancepolicy)  |Afficher ou configurer la configuration pour les paramètres de notification de révision de suppression et de rappel |La messagerie électronique Exchange <br /><br /> Sites SharePoint <br /><br /> Comptes OneDrive <br /><br /> Groupes Microsoft 365|
|[Get-RetentionCompliancePolicy](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionCompliancePolicy](/powershell/module/exchange/new-retentioncompliancepolicy) <br /><br /> [Remove-RetentionCompliancePolicy](/powershell/module/exchange/remove-retentioncompliancepolicy) <br /><br /> [Set-RetentionCompliancePolicy](/powershell/module/exchange/set-retentioncompliancepolicy) |Afficher, créer, supprimer, configurer des stratégies pour la rétention |La messagerie électronique Exchange <br /><br /> Sites SharePoint <br /><br /> Comptes OneDrive<br /><br /> Groupes Microsoft 365 <br /><br /> Skype Entreprise <br /><br /> Dossiers publics Exchange <br /><br /> Messages de conversation Teams <br /><br /> Messages du canal Teams |
|[Get-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [New-RetentionComplianceRule](/powershell/module/exchange/get-retentioncompliancepolicy) <br /><br /> [Set-RetentionComplianceRule](/powershell/module/exchange/set-retentioncompliancerule) <br /><br /> [Remove-RetentionComplianceRule](/powershell/module/exchange/remove-retentioncompliancerule)  | Afficher, créer, configurer, supprimer des paramètres de police pour les étiquettes de rétention ou de rétention |La messagerie électronique Exchange <br /><br /> Sites SharePoint <br /><br /> Comptes OneDrive <br /><br /> Groupes Microsoft 365 <br /><br /> Skype Entreprise <br /><br /> Dossiers publics Exchange <br /><br /> Messages de conversation Teams <br /><br /> Messages du canal Teams |

## <a name="retention-cmdlets-specific-to-teams-private-channels-and-yammer"></a>Applets de commande de rétention spécifiques aux canaux privés Teams et Yammer

Utilisez les applets de commande suivantes lorsque les emplacements sont pour les **messages de canal privé Teams**, les **messages utilisateur Yammer** ou les **messages de la communauté Yammer**.

Lorsque les emplacements sont pour les messages de conversation Teams, les messages de canal Teams, les e-mails Exchange, les sites SharePoint, les comptes OneDrive, les Groupes Microsoft 365, les Skype Entreprise ou les dossiers publics Exchange, utilisez les applets de commande répertoriées dans la [section précédente](#retention-cmdlets-for-most-locations).

|Applet de commande|Description|Emplacements applicables|
|:-----|:-----|:-----|:-----|
|[Get-AppRetentionCompliancePolicy](/powershell/module/exchange/get-appretentioncompliancepolicy) <br /><br> [New-AppRetentionCompliancePolicy](/powershell/module/exchange/new-appretentioncompliancepolicy) <br /><br> [Remove-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) <br /><br> [Set-AppRetentionCompliancePolicy](/powershell/module/exchange/remove-appretentioncompliancepolicy) | Afficher, créer, supprimer, configurer des stratégies de rétention |Messages du canal privé Teams <br /><br /> Messages utilisateur de Yammer <br /><br /> Messages communautaires Yammer|
|[Get-AppRetentionComplianceRule](/powershell/module/exchange/get-appretentioncompliancerule) <br /><br /> [New-AppRetentionComplianceRule](/powershell/module/exchange/new-appretentioncompliancerule) <br /><br /> [Remove-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) <br /><br /> [Set-AppRetentionComplianceRule](/powershell/module/exchange/remove-appretentioncompliancerule) | Afficher, créer, supprimer, configurer les paramètres de rétention pour les stratégies de rétention |Messages du canal privé Teams <br /><br /> Messages utilisateur de Yammer <br /><br /> Messages communautaires Yammer|

## <a name="configuration-guidance"></a>Instructions de configuration

Utilisez les pages d’aide associées à chaque applet de commande pour obtenir des informations détaillées et des exemples.

Pour obtenir de l’aide guidée sur la création et la publication d’étiquettes de rétention, consultez [Créer et publier des étiquettes de rétention à l’aide de PowerShell](bulk-create-publish-labels-using-powershell.md).