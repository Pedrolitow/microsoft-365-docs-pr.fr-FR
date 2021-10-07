---
title: Activer ou désactiver la fonctionnalité d’audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
ms.custom: seo-marvel-apr2020
description: Comment activer ou désactiver la fonctionnalité de recherche du journal d’audit dans le Centre de conformité Microsoft 365 pour activer ou désactiver la possibilité pour les administrateurs d’effectuer des recherches dans le journal d’audit.
ms.openlocfilehash: 1f5b9f6c63d98718af2ddb54aab73c4d7e423d2d
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60198648"
---
# <a name="turn-auditing-on-or-off"></a>Activer ou désactiver la fonctionnalité d’audit

L’enregistrement d’audit est désactivé par défaut pour Microsoft 365 et Office 365'entreprise. Toutefois, lors de la configuration d’une nouvelle Microsoft 365 ou Office 365 organisation, vous devez vérifier l’état d’audit de votre organisation. Pour obtenir des instructions, consultez la section Vérifier [l’état d’audit](#verify-the-auditing-status-for-your-organization) de votre organisation dans cet article. 

Lorsque l’audit dans le Centre de conformité Microsoft 365 est allumé, les activités des utilisateurs et des administrateurs de votre organisation sont enregistrées dans le journal d’audit et conservées pendant 90 jours, et jusqu’à un an en fonction de la licence attribuée aux utilisateurs. Toutefois, votre organisation peut avoir des raisons de ne pas vouloir enregistrer et conserver les données du journal d’audit. Dans ce cas, un administrateur global peut décider de désactiver l’audit dans Microsoft 365.

> [!IMPORTANT]
> Si vous désactiver l’audit dans Microsoft 365, vous ne pouvez pas utiliser l’API activité de gestion Office 365 ou Azure Sentinel pour accéder aux données d’audit de votre organisation. La suppression de l’audit en suivant les étapes de cet article signifie qu’aucun résultat ne sera renvoyé lorsque vous effectuerez une recherche dans le journal d’audit à l’aide du Centre de conformité Microsoft 365 ou lorsque vous exécutez la cmdlet **Search-UnifiedAuditLog** dans Exchange Online PowerShell. Cela signifie également que les journaux d’audit ne seront pas disponibles via l Office 365 API Activité de gestion ou Azure Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>Avant d’activer ou de désactiver l’audit

- Le rôle Journaux d’audit doit vous être attribué dans Exchange Online pour activer ou désactiver l’audit dans Microsoft 365 organisation. Par défaut, ce rôle est affecté aux groupes de rôles Gestion de la conformité et Gestion de l’organisation dans la page **Autorisations** du Centre d Exchange de conformité. Les administrateurs globaux Microsoft 365 sont membres du groupe de rôles Gestion de l’organisation dans Exchange Online.

    > [!NOTE]
    > Des autorisations doivent être attribuées aux utilisateurs Exchange Online pour activer ou désactiver l’audit. Si vous attribuez aux utilisateurs le rôle Journaux d’audit sur la page **Autorisations** de la Centre de conformité Microsoft 365, ils ne pourront pas activer ou désactiver l’audit. Cela est dû au fait que l’cmdlet sous-jacente est Exchange Online cmdlet PowerShell.

- Pour obtenir des instructions détaillées sur la recherche dans le journal d’audit, voir [Rechercher dans le journal d’audit.](search-the-audit-log-in-security-and-compliance.md) Pour plus d’informations sur l’API activité Microsoft 365 gestion des données, voir Prise en [Microsoft 365 API de gestion des données.](/office/office-365-management-api/get-started-with-office-365-management-apis)

## <a name="verify-the-auditing-status-for-your-organization"></a>Vérifier l’état d’audit de votre organisation

Pour vérifier que l’audit est allumé pour votre organisation, vous pouvez exécuter la commande suivante [dans Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell):

```powershell
Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
```

La valeur `True` de la propriété  _UnifiedAuditLogIngestionEnabled_ indique que l’audit est allumé. La valeur indique `False` que l’audit n’est pas allumé.

## <a name="turn-on-auditing"></a>Activer l’audit

Si l’audit n’est pas allumé pour votre organisation, vous pouvez l’activer dans le Centre de conformité Microsoft 365 ou à l’aide Exchange Online PowerShell. L’opération d’audit peut prendre plusieurs heures avant que vous ne retourniez les résultats lors de la recherche dans le journal d’audit.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>Utiliser le centre de conformité pour activer l’audit

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche du Centre de conformité Microsoft 365, cliquez sur **Audit.**

   Si l’audit n’est pas désactivé pour votre organisation, une bannière s’affiche pour vous invite à commencer à enregistrer l’activité des utilisateurs et des administrateurs.

   ![Bannière sur la page Audit.](../media/AuditingBanner.png)

3. Cliquez sur la **bannière Démarrer l’enregistrement de l’activité de l’utilisateur et de l’administrateur.**

   L’application de la modification peut prendre jusqu’à 60 minutes.

### <a name="use-powershell-to-turn-on-auditing"></a>Utiliser PowerShell pour activer l’audit

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la commande PowerShell suivante pour activer l’audit.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Un message s’affiche pour vous dire que l’application de la modification peut prendre jusqu’à 60 minutes.
  
## <a name="turn-off-auditing"></a>Désactiver l’audit

Vous devez utiliser Exchange Online PowerShell pour désactiver l’audit.
  
1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Exécutez la commande PowerShell suivante pour désactiver l’audit.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Après un certain temps, vérifiez que l’audit est désactivé. Il existe deux méthodes pour y parvenir :

    - Dans Exchange Online PowerShell, exécutez la commande suivante :

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      La valeur de  `False` la  _propriété UnifiedAuditLogIngestionEnabled_ indique que l’audit est désactivé.

    - Go to the **Audit** page in the Centre de conformité Microsoft 365.

      Si l’audit n’est pas désactivé pour votre organisation, une bannière s’affiche pour vous invite à commencer à enregistrer l’activité des utilisateurs et des administrateurs.

## <a name="audit-records-when-auditing-status-is-changed"></a>Enregistrements d’audit lorsque l’état d’audit est modifié

Les modifications apportées à l’état d’audit dans votre organisation sont elles-mêmes auditées. Cela signifie que les enregistrements d’audit sont enregistrés lorsque l’audit est allumé ou désactivé. Vous pouvez rechercher ces enregistrements d’audit dans Exchange journal d’audit de l’administrateur.

Pour rechercher dans le journal d’audit de l’administrateur Exchange les enregistrements d’audit générés lors de l’Exchange Online l’audit, exécutez la commande suivante [:](/powershell/exchange/connect-to-exchange-online-powershell)

```powershell
Search-AdminAuditLog -Cmdlets Set-AdminAuditLogConfig -Parameters UnifiedAuditLogIngestionEnabled
```

Les enregistrements d’audit pour ces événements contiennent des informations sur la modification de l’état d’audit, l’administrateur qui l’a modifié et l’adresse IP de l’ordinateur utilisé pour effectuer la modification. Les captures d’écran suivantes montrent les enregistrements d’audit qui correspondent à la modification de l’état d’audit dans votre organisation.

### <a name="audit-record-for-turning-on-auditing"></a>Enregistrement d’audit pour l' turning on auditing

![Enregistrement d’audit pour l' turning on auditing](../media/AuditStatusAuditingEnabled.png)

La valeur de la propriété CmdletParameters indique que l’enregistrement d’audit unifié a été allumé dans le centre de conformité ou en exécutant la `Confirm` cmdlet **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true.** 

### <a name="audit-record-for-turning-off-auditing"></a>Enregistrement d’audit pour la fin de l’audit

![Enregistrement d’audit pour la fin de l’audit](../media/AuditStatusAuditingDisabled.png)

La valeur de `Confirm` n’est pas incluse dans *la propriété CmdletParameters.* Cela indique que l’enregistrement d’audit unifié a été désactivé en exécutant la commande **Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false** commande.

Pour plus d’informations sur la recherche dans Exchange’audit de l’administrateur, voir [Search-AdminAuditLog](/powershell/module/exchange/search-adminauditlog).