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
description: Les stratégies de rétention du journal d’audit font partie des nouvelles fonctionnalités d’audit avancées de Microsoft 365. Une stratégie de rétention de journal d’audit vous permet de spécifier la durée de conservation des journaux d’audit dans votre organisation.
ms.openlocfilehash: 99561fbb71a9d919a6275b79370394e85ec25c39
ms.sourcegitcommit: 7f2a9927129f6c8a9c51f975ccf7fb5b40fbb8cd
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/10/2020
ms.locfileid: "41867883"
---
# <a name="manage-audit-log-retention-policies"></a>Gérer les stratégies de rétention du journal d'audit

Vous pouvez créer et gérer des stratégies de rétention du journal d’audit dans le Centre de sécurité & conformité. Les stratégies de rétention du journal d’audit font partie des nouvelles fonctionnalités d’audit avancées de Microsoft 365. Une stratégie de rétention de journal d’audit vous permet de spécifier la durée de conservation des journaux d’audit dans votre organisation. Vous pouvez conserver des journaux d’audit pendant un an. Vous pouvez créer des stratégies en fonction des critères suivants :

- L'ensemble des activités d’un ou plusieurs services Microsoft 365

- Des activités précises (dans un service particulier) effectuées par l'ensemble des utilisateurs ou par des utilisateurs spécifiques

- Un niveau de priorité indiquant la stratégie prioritaire si vous disposez de plusieurs stratégies au sein de votre organisation

## <a name="default-audit-log-retention-policy"></a>Une stratégie de rétention de journal d'audit par défaut

L'audit avancé de Microsoft 365 offre une stratégie de rétention de journal d’audit par défaut pour l'ensemble des organisations. Cette stratégie conserve tous les enregistrements d’audit Exchange, SharePoint et Azure Active Directory pendant une durée d'un an. Cette stratégie par défaut conserve les enregistrements d’audit contenant la valeur de **AzureActiveDirectory**, **Exchange**ou **SharePoint** pour la propriété **Charge de travail** (il s’agit du service dans lequel l’activité s’est produite). La stratégie par défaut n'est pas modifiable. Pour obtenir la liste des types d’enregistrements par charge de travail qui sont inclus dans la stratégie par défaut, consultez la rubrique [Informations supplémentaires](#more-information) dans cet article.

> [!NOTE]
> La stratégie de rétention du journal d’audit par défaut s’applique uniquement aux enregistrements d’audit pour les activités effectuées par les utilisateurs auxquels une licence Office 365 ou Microsoft 365 E5 est attribuée ou qui disposent d’une licence de composant de conformité E5 Microsoft 365 E5 Conformité. Si vous avez des utilisateurs non E5 au sein de votre organisation, les enregistrements d’audit correspondants sont conservés pendant 90 jours.

## <a name="before-you-begin"></a>Avant de commencer

- Pour créer ou modifier une stratégie de rétention d’audit, vous devez être avoir un rôle de Configuration de l’organisation dans le Centre de sécurité & conformité.

- Vous pouvez disposer de 50 stratégies de rétention du journal d’audit au maximum au sein de votre organisation.

- Pour conserver un journal d’audit pendant plus de 90 jours, l’utilisateur ayant généré le journal d’audit doit se voir attribuer une licence Office 365 ou Microsoft 365 E5 ou disposer d’une licence de composant de conformité E5 Microsoft 365.

- Toutes les stratégies de rétention du journal d’audit personnalisées (créées par votre organisation) sont prioritaires sur la stratégie de rétention par défaut. Par exemple, si vous créez une stratégie de rétention de journal d’audit pour une activité de boîte aux lettres Exchange qui présente une période de rétention de moins d'un an, les enregistrements d’audit pour les activités de boîte aux lettres Exchange sont conservés pendant la durée plus courte spécifiée dans la stratégie personnalisée.

## <a name="create-an-audit-log-retention-policy-in-the-security--compliance-center"></a>Créer une stratégie de rétention du journal d’audit dans le Centre de sécurité & conformité.

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous avec le compte d’utilisateur auquel le rôle Configuration de l’organisation est attribué dans le Centre de sécurité & conformité. 

2. Dans le volet gauche du Centre de sécurité et de conformité, cliquez sur **Recherche** > **Recherche dans le journal d’audit**.

    La page **Recherche dans le journal d’audit** s’affiche.

    ![La page Recherche dans le journal d’audit](media/AuditLogRetentionPolicy1.png)

3. Cliquez sur **Nouvelle stratégie de rétention**, puis complétez les champs suivants dans la page de menu volant :

    ![Page de menu volant de la stratégie de rétention de journal d'audit](media/AuditLogRetentionPolicy2.png)

   a. **Nom :** le nom de la stratégie de rétention du journal d’audit. Ce nom doit être unique dans toute votre organisation.
   
   b. **Description :** facultatif, mais utile pour fournir des informations sur la stratégie, telles que le type d’enregistrement ou la charge de travail, les utilisateurs spécifiés dans la stratégie et la durée.

   c. **Types d’enregistrement :** le type d’enregistrement d’audit auquel la stratégie s’applique. Si vous sélectionnez plusieurs types d’enregistrements, vous ne pouvez pas sélectionner les activités, car la stratégie s’applique à toutes les activités des types d’enregistrement sélectionnés. De plus, si vous laissez cette propriété vierge, vous devez sélectionner un utilisateur dans la zone **Utilisateurs**.

   d. **Activités :** utilisez cette zone pour sélectionner les activités du type d’enregistrement que vous avez sélectionné. Vous pouvez choisir des activités spécifiques auxquelles s'applique la stratégie. Si vous ne choisissez pas d'activité spécifique, la stratégie s’applique à toutes les activités du type d’enregistrement sélectionné.

   e. **Utilisateurs :** sélectionnez un ou plusieurs utilisateurs auxquels la stratégie doit être appliquée. Si vous laissez cette zone vierge, la stratégie s’applique à tous les utilisateurs. Si vous laissez les **Types d’enregistrement** vierges, vous devez sélectionner un utilisateur.

   f. **Durée :** la durée de conservation des journaux d’audit qui correspondent aux critères de la stratégie.

   g. **Priorité :** cette valeur détermine l’ordre dans lequel les stratégies de rétention du journal d’audit sont traitées au sein de votre organisation. Une valeur plus haute implique une priorité élevée. Par exemple, une stratégie avec une valeur de priorité de **5** sera prioritaire sur une stratégie ayant une valeur de priorité de **0**. Comme indiqué précédemment, toute stratégie de rétention de journal d’audit personnalisée est prioritaire sur la stratégie par défaut de votre organisation.

6. Cliquez sur **Enregistrer** pour créer le nouveau journal d'audit de la stratégie de rétention. 

Rien n’indique pour le moment que la stratégie de rétention a été correctement créée. Consultez la rubrique suivante sur l’affichage des propriétés des stratégies de rétention du journal d’audit.

## <a name="create-an-audit-log-retention-policy-in-powershell"></a>Créer une stratégie de rétention de journal d’audit dans PowerShell

Vous pouvez également utiliser le Centre de sécurité et conformité Office 365 PowerShell pour créer des stratégies de rétention de journal d’audit. 

1. [Se connecter à l’interface PowerShell du Centre de sécurité et conformité](https://docs.microsoft.com/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell).

2. Pour créer une stratégie de rétention, exécutez la commande suivante. 

   ```powershell
   New-UnifiedAuditLogRetentionPolicy -Name "Microsoft Teams Audit Policy" -Description "One year retention policy for all Microsoft Teams activities" -RecordTypes MicrosoftTeams -RetentionDuration TwelveMonths -Priority 100
   ```
    
    Cet exemple crée une stratégie de rétention de journal d’audit nommée « Stratégie d’audit Microsoft Teams » ayant les paramètres suivants :

   - Une description de la stratégie.

   - Conserve toutes les activités Microsoft Teams (telles que définies par le paramètre *RecordType*).

   - Conserve les journaux d'audit Microsoft Teams pendant un an.

   - Une priorité de 100.

Voici un autre exemple de création d’une stratégie de rétention de journal d’audit. Cette stratégie conserve les journaux d’audit pour l’activité « Utilisateur connecté » pendant six mois pour l’utilisateur admin@contoso.onmicrosoft.com.

```powershell
New-UnifiedAuditLogRetentionPolicy -Name "SixMonth retention for admin logons" -RecordTypes AzureActiveDirectoryStsLogon -Operations UserLoggedIn -UserIds admin@contoso.onmicrosoft.com -RetentionDuration SixMonths -Priority 25
```

Pour plus d’informations, voir [New-UnifiedAuditLogRetentionPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/new-unifiedauditlogretentionpolicy).

## <a name="view-audit-log-retention-policies"></a>Afficher les stratégies de rétention du journal d'audit

La seule façon d’afficher des stratégies de rétention de journal d’audit personnalisé à ce jour est d’utiliser l’applet de commande **Get-UnifiedAuditRetentionPolicy** dans le Centre de sécurité & conformité PowerShell. Voici un exemple de commande qui permet d’afficher les paramètres (que vous avez configurés à l’étape précédente) pour les stratégies de rétention du journal d’audit au sein de votre organisation. Cette commande trie les stratégies de la priorité la plus élevée à la plus faible.

```powershell
Get-UnifiedAuditLogRetentionPolicy | Sort-Object -Property Priority -Descending | FL Priority,Name,Description,RecordTypes,Operations,UserIds,RetentionDuration
```

> [!NOTE]
> Pour l’instant, l’applet de commande **Get-UnifiedAuditLogRetentionPolicy** ne renvoie pas la stratégie par défaut du journal d’audit pour votre organisation.

Pour plus d’informations, voir [Get-UnifiedAuditLogRetentionPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/get-unifiedauditlogretentionpolicy).

## <a name="more-information"></a>Plus d’informations

- Pour modifier une stratégie de rétention de journal d’audit existante, utilisez l’applet de commande **UnifiedAuditLogRetentionPolicy** dans le Centre de sécurité & conformité PowerShell. Pour plus d’informations, voir [Set-UnifiedAuditLogRetentionPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/set-unifiedauditlogretentionpolicy).

- Pour supprimer une stratégie de rétention de journal d’audit, utilisez l’applet de commande **Remove-UnifiedAuditLogRetentionPolicy** dans le Centre de sécurité & conformité PowerShell. La suppression complète de la stratégie peut prendre jusqu’à 30 minutes. Pour plus d’informations, voir [Remove-UnifiedAuditLogRetentionPolicy](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/remove-unifiedauditlogretentionpolicy).

- Comme indiqué précédemment, les enregistrements d’audit pour les opérations dans Azure Active Directory, Exchange et SharePoint sont conservés pendant un an. Le tableau suivant répertorie tous les types d’enregistrements (pour chaque service) inclus dans la stratégie de rétention par défaut du journal d’audit. Cela signifie que les journaux d’audit pour toute opération ayant ce type d’enregistrement sont conservés pendant un an, sauf si une stratégie de rétention de journal d’audit personnalisée est prioritaire pour un type d’enregistrement, une opération ou un utilisateur spécifique. La valeur Enum (affichée comme valeur de la propriété RecordType dans un enregistrement d’audit) pour chaque type d’enregistrement est affichée entre parenthèses.

   |AzureActiveDirectory |Exchange  |SharePoint|
   |:---------|:---------|:---------|
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
