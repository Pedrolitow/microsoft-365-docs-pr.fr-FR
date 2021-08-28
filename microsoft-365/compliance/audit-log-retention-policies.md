---
title: Gérer les stratégies de rétention du journal d'audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Les stratégies de rétention du journal d’audit font partie des nouvelles fonctionnalités d’audit avancées de Microsoft 365. Une stratégie de rétention de journal d’audit vous permet de spécifier la durée de conservation des journaux d’audit dans votre organisation.
ms.openlocfilehash: 5427bbfc63381ab2763c0bf74adda978f4fc6af3
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58574867"
---
# <a name="manage-audit-log-retention-policies"></a>Gérer les stratégies de rétention du journal d'audit

Vous pouvez créer et gérer des stratégies de rétention de journal d’audit dans le Centre de conformité Microsoft 365. Les stratégies de rétention du journal d’audit font partie des nouvelles fonctionnalités d’audit avancées de Microsoft 365. Une stratégie de rétention de journal d’audit vous permet de spécifier la durée de conservation des journaux d’audit dans votre organisation. Vous pouvez conserver des journaux d’audit pendant 10 ans. Vous pouvez créer des stratégies en fonction des critères suivants :

- L'ensemble des activités d’un ou plusieurs services Microsoft 365
- Des activités spécifiques (dans un service Microsoft 365) effectuées par l'ensemble des utilisateurs ou par des utilisateurs spécifiques
- Un niveau de priorité indiquant la stratégie prioritaire si vous disposez de plusieurs stratégies au sein de votre organisation

## <a name="default-audit-log-retention-policy"></a>Une stratégie de rétention de journal d'audit par défaut

L'audit avancé de Microsoft 365 offre une stratégie de rétention du journal d’audit par défaut pour l'ensemble des organisations. Cette stratégie conserve tous les enregistrements d’audit Exchange Online, SharePoint Online, OneDrive Entreprise et Azure Active Directory pendant une durée d'un an. Cette stratégie par défaut conserve les enregistrements d’audit qui contenant la valeur **Exchange**, **SharePoint**, **OneDrive**, **AzureActiveDirectory** pour la propriété **Charge de travail** (service dans lequel l’activité s’est produite). La stratégie par défaut n'est pas modifiable. Pour obtenir la liste des types d’enregistrements par charge de travail qui sont inclus dans la stratégie par défaut, consultez la rubrique [Informations supplémentaires](#more-information) dans cet article.

> [!NOTE]
> La stratégie de rétention du journal d’audit par défaut s’applique uniquement aux enregistrements d’audit pour les activités effectuées par les utilisateurs auxquels une licence Office 365 ou Microsoft 365 E5 est attribuée ou qui disposent de la Conformité Microsoft 365 E5 ou E5 eDiscovery et d’une licence de complément d’audit. Si vous avez des utilisateurs non-E5 ou des utilisateurs invités dans votre organisation, leurs dossiers d'audit correspondants sont conservés pendant 90 jours.

## <a name="before-you-create-an-audit-log-retention-policy"></a>Avant de créer une stratégie de rétention de journal d’audit

- Le rôle Configuration de l'organisation doit vous être attribué dans le centre de conformité Microsoft 365 pour créer ou modifier une stratégie de rétention d'audit.

- Vous pouvez disposer de 50 stratégies de rétention du journal d’audit au maximum au sein de votre organisation.

- Pour conserver un journal d’audit pendant plus de 90 jours (et jusqu’à 1 an), l’utilisateur l’ayant généré (en effectuez une activité d’audit) doit se voir attribuer une licence Office 365 E5 ou Microsoft 365 E5 ou disposer d’une licence de module complémentaire Microsoft 365 E5 Conformité ou E5 eDiscovery et audit. Pour conserver les journaux d'audit pendant 10 ans, l'utilisateur qui génère le journal d'audit doit également se voir attribuer une licence complémentaire de rétention des journaux d'audit de 10 ans en plus d'une licence E5.

- Toutes les stratégies de rétention de journal d’audit personnalisées (créées par votre organisation) sont prioritaires sur la stratégie de rétention par défaut. Par exemple, si vous créez une stratégie de rétention de journal d’audit pour une activité de boîte aux lettres Exchange qui présente une période de rétention de moins d'un an, les enregistrements d’audit pour les activités de boîte aux lettres Exchange sont conservés pendant la durée plus courte spécifiée dans la stratégie personnalisée.

## <a name="create-an-audit-log-retention-policy"></a>Créer une stratégie de rétention de journal d’audit

1. Accédez à <https://compliance.microsoft.com> et connectez-vous avec un compte d’utilisateur auquel le rôle Configuration de l’organisation a été attribué dans la page Autorisations du centre de conformité Microsoft 365.

2. Dans le volet de navigation gauche du centre de conformité Microsoft 365, cliquez sur **Audit**.

3. Cliquez sur l’onglet **Stratégies de rétention d’audit**.

4. Cliquez sur **Créer une stratégie de rétention d'audit**, puis complétez les champs suivants dans la page de menu volant:

   ![Page de menu volant de la stratégie de rétention d'audit.](../media/CreateAuditLogRetentionPolicy.png)

   1. **Nom de la stratégie** Le nom de la stratégie de rétention du journal d’audit. Ce nom doit être unique dans votre organisation, et ne peut pas être modifié une fois la stratégie créée.

   2. **Description :** facultatif, mais utile pour fournir des informations sur la stratégie, telles que le type d’enregistrement ou la charge de travail, les utilisateurs spécifiés dans la stratégie et la durée.

   3. **Utilisateurs :** sélectionnez un ou plusieurs utilisateurs auxquels la stratégie doit être appliquée. Si vous laissez cette zone vierge, la stratégie s’applique à tous les utilisateurs. Si vous laissez le **Type d’enregistrement** vierge, vous devez alors sélectionner un utilisateur.

   4. **Type d’enregistrement :** le type d’enregistrement d’audit auquel la stratégie s’applique. Si vous laissez cette propriété vierge, vous devez sélectionner un utilisateur dans la zone **Utilisateurs**. Vous pouvez sélectionner un seul type d’enregistrement ou plusieurs types d’enregistrements :
      - Si vous sélectionnez un seul type d’enregistrement, le champ **Activités** s’affiche de façon dynamique. Vous pouvez utiliser la liste déroulante pour sélectionner les activités du type d’enregistrement sélectionné auquel la stratégie doit être appliquée. Si vous ne choisissez pas d'activité spécifique, la stratégie s’applique à toutes les activités du type d’enregistrement sélectionné.
      - Si vous sélectionnez plusieurs types d’enregistrements, vous n’avez pas la possibilité de sélectionner des activités. La stratégie s’applique à toutes les activités des types d’enregistrement sélectionnés.

   5. **Durée :** la durée de conservation des journaux d’audit qui correspondent aux critères de la stratégie.

   6. **Priorité :** cette valeur détermine l’ordre dans lequel les stratégies de rétention du journal d’audit sont traitées au sein de votre organisation. Une valeur faible implique une priorité élevée. Les priorités valides sont les valeurs numériques comprises entre **1** et **10 000**. La valeur **1** est la priorité la plus élevée et la valeur **10 000** est la priorité la plus faible. Par exemple, une stratégie avec une valeur de **5** sera prioritaire sur une stratégie ayant une valeur de **10**. Comme indiqué précédemment, toute stratégie de rétention de journal d’audit personnalisée est prioritaire sur la stratégie par défaut de votre organisation.

5. Cliquez sur **Enregistrer** pour créer le nouveau journal d'audit de la stratégie de rétention.

La nouvelle stratégie s’affiche dans la liste sur l’onglet **Stratégies de rétention de l’audit**.

## <a name="manage-audit-log-retention-policies-in-the-microsoft-365-compliance-center"></a>Gérer les stratégies de conservation des journaux d'audit dans le centre de conformité Microsoft 365

Les stratégies de rétention du journal d’audit sont répertoriées sur l’onglet **Stratégies de rétention d’audit** (également appelé *tableau de bord*). Vous pouvez utiliser le tableau de bord pour afficher, modifier, et supprimer des stratégies de rétention d’audit.

### <a name="view-policies-in-the-dashboard"></a>Afficher des stratégies dans le tableau de bord

Les stratégies de rétention du journal d’audit sont répertoriées dans le tableau de bord. L’un des avantages de l’affichage des stratégies dans le tableau de bord est que vous pouvez cliquer sur la colonne **Priorité** pour répertorier les stratégies selon la priorité d’application. Comme indiqué précédemment, une valeur plus basse indique une priorité plus élevée.

![Colonne de priorité dans le Tableau de bord des stratégies de rétention d’audit.](../media/AuditLogRetentionDashboardPriority.png)

Vous pouvez également sélectionner une stratégie pour afficher ses paramètres sur la page de menu volant.

> [!NOTE]
> La stratégie de rétention du journal d’audit par défaut de votre organisation n’est pas affichée dans le tableau de bord.

### <a name="edit-policies-in-the-dashboard"></a>Modifier des stratégies dans le tableau de bord

Pour modifier une stratégie, sélectionnez-la pour afficher la page de menu volant. Vous pouvez modifier un ou plusieurs paramètres, puis enregistrer vos modifications.

> [!IMPORTANT]
>
> Si vous utilisez la cmdlet **New-UnifiedAuditLogRetentionPolicy** , il est possible de créer une stratégie de rétention de journal d’audit des types d’enregistrements ou des activités qui ne sont pas disponibles dans l’outil **Créer une stratégie de rétention d’audit** dans le tableau de bord. Dans ce cas, vous ne pouvez pas modifier la stratégie (par exemple, modifier la durée de rétention ou ajouter et supprimer des activités) du tableau de bord **Stratégies de rétention d’audit**. Vous pouvez uniquement afficher et supprimer la stratégie dans le centre de conformité. Pour modifier la stratégie, vous devez utiliser la cmdlet [Set-UnifiedAuditLogRetentionPolicy dans le PowerShell du ](/powershell/module/exchange/set-unifiedauditlogretentionpolicy)Centre de sécurité et de conformité.
>
> **Conseil :** Un message affiche en haut de la page de menu volant les stratégies qui doivent être modifiées à l’aide de PowerShell.

### <a name="delete-policies-in-the-dashboard"></a>Supprimer des stratégies dans le tableau de bord

Pour supprimer une stratégie, cliquez sur **Supprimer** ![ Supprimer l’icône.](../media/92a9f8e0-d469-48da-addb-69365e7ffb6f.jpg) icône, puis confirmer la suppression de la stratégie. La stratégie est supprimée du tableau de bord, mais pourrait prendre au maximum 30 minutes pour être supprimée de votre organisation.

## <a name="create-and-manage-audit-log-retention-policies-in-powershell"></a>Créer et gérer des stratégies de rétention d’un journal d’audit dans PowerShell

Vous pouvez également utiliser le centre de sécurité & conformité PowerShell pour créer et gérer des stratégies de rétention d’un journal d’audit. L’une des raisons de l’utilisation de PowerShell est la création d’une stratégie pour un type ou une activité d’enregistrement qui n’est pas disponible dans l’interface utilisateur.

### <a name="create-an-audit-log-retention-policy-in-powershell"></a>Créer une stratégie de rétention de journal d’audit dans PowerShell

Pour créer une stratégie de rétention de journal d’audit dans PowerShell, suivez ces étapes :

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](/powershell/exchange/connect-to-scc-powershell).

2. Exécutez la commande suivante pour créer une stratégie de conservation des journaux d'audit :

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TenYears -Priority 100
   ```

   Cet exemple crée une stratégie de rétention de journal d’audit nommée « Stratégie d’audit Microsoft Teams » ayant les paramètres suivants :

   - Une description de la stratégie.
   - Conserve toutes les activités Microsoft Teams (telles que définies par le paramètre *RecordType*).
   - Conserve les journaux d'audit Microsoft Teams pendant 10 ans.
   - Une priorité de 100.

Voici un autre exemple de création d’une stratégie de rétention de journal d’audit. Cette stratégie conserve les journaux d’audit pour l’activité « Utilisateur connecté » pendant six mois pour l’utilisateur admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Pour plus d’informations, voir [New-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/new-unifiedauditlogretentionpolicy).

### <a name="view-policies-in-powershell"></a>Afficher des stratégies dans PowerShell

Utilisez la cmdlet [Get-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/get-unifiedauditlogretentionpolicy) dans le centre de sécurité & conformité PowerShell pour afficher des stratégies de rétention de journal d’audit.

Voici un exemple de commande pour l’affichage des paramètres de stratégies de rétention de journal d’audit au sein de votre organisation. Cette commande trie les stratégies de la priorité la plus élevée à la plus faible.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> La cmdlet **Get-UnifiedAuditLogRetentionPolicy** ne renvoie pas la stratégie de rétention de journal d’audit par défaut de votre organisation.

### <a name="edit-policies-in-powershell"></a>Modifier des stratégies dans PowerShell

Pour modifier une stratégie de rétention de journal d’audit existante, utilisez la cmdlet [Set-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/set-unifiedauditlogretentionpolicy) dans le centre de sécurité & conformité PowerShell.

### <a name="delete-policies-in-powershell"></a>Supprimer des stratégies dans PowerShell

Pour supprimer une stratégie de rétention de journal d’audit, utilisez la cmdlet [Remove-UnifiedAuditLogRetentionPolicy](/powershell/module/exchange/remove-unifiedauditlogretentionpolicy) dans le Centre de sécurité & conformité PowerShell. La suppression de la stratégie de votre organisation peut prendre jusqu’à 30 minutes.

## <a name="more-information"></a>Plus d’informations

Comme indiqué précédemment, les enregistrements d’audit pour des opérations dans Azure Active Directory, Exchange Online, SharePoint Online et OneDrive Entreprise sont par défaut conservés pendant un an. Le tableau suivant répertorie tous les types d’enregistrements (pour chaque service) inclus dans la stratégie de rétention par défaut du journal d’audit. Cela signifie que les journaux d’audit pour toute opération ayant ce type d’enregistrement sont conservés pendant un an, sauf si une stratégie de rétention de journal d’audit personnalisée est prioritaire pour un type d’enregistrement, une opération ou un utilisateur spécifique. La valeur Enum (affichée comme valeur de la propriété RecordType dans un enregistrement d’audit) pour chaque type d’enregistrement est affichée entre parenthèses.

<br>

****

|AzureActiveDirectory|Exchange |SharePoint ou OneDrive|
|---|---|---|
|AzureActiveDirectory (8)|ExchangeAdmin (1)|ComplianceDLPSharePoint (11)|
|AzureActiveDirectoryAccountLogon (9)|ExchangeItem (2)|ComplianceDLPSharePointClassification (33)|
|AzureActiveDirectoryStsLogon (15)|Campaign (62)|Project (35)|
||ComplianceDLPExchange (13)|SharePoint (4)|
||ComplianceSupervisionExchange (68)|SharePointCommentOperation (37)|
||CustomerKeyServiceEncryption (69)|SharePointContentTypeOperation (55)|
||ExchangeAggregatedOperation (19)|SharePointFieldOperation (56)|
||ExchangeItemAggregated (50)|SharePointFileOperation (6)|
||ExchangeItemGroup (3)|SharePointListOperation (36)|
||InformationBarrierPolicyApplication (53)|SharePointSharingOperation (14)|
||||
