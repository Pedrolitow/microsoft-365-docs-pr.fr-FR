---
title: Activer ou désactiver la recherche dans le journal d’audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: e893b19a-660c-41f2-9074-d3631c95a014
ms.custom: seo-marvel-apr2020
description: Comment activer ou désactiver la fonctionnalité de recherche du journal d’audit dans le Centre de sécurité & conformité pour activer ou désactiver la possibilité pour les administrateurs de rechercher dans le journal d’audit.
ms.openlocfilehash: 3f3e1b913dd163e74f9e5359de772dfcbf3bd786
ms.sourcegitcommit: 355bd51ab6a79d5c36a4e4f57df74ae6873eba19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/04/2021
ms.locfileid: "50423675"
---
# <a name="turn-audit-log-search-on-or-off"></a>Activer ou désactiver la recherche dans le journal d’audit

Nous activons par défaut la journalisation d’audit pour les organisations d’entreprise Microsoft 365 et Office 365. Cela inclut les organisations disposant d’abonnements E3/G3 ou E5/G5. Lorsque la recherche dans le journal d’audit dans le centre de conformité est désactivée, les activités des utilisateurs et des administrateurs de votre organisation sont enregistrées dans le journal d’audit et conservées pendant 90 jours et jusqu’à un an en fonction de la licence attribuée aux utilisateurs. Toutefois, votre organisation peut avoir des raisons de ne pas vouloir enregistrer et conserver les données du journal d’audit. Dans ce cas, un administrateur global peut décider de désactiver l’audit dans Microsoft 365.

> [!IMPORTANT]
> Si vous désactiver la recherche dans le journal d’audit dans Microsoft 365, vous ne pouvez pas utiliser l’API Activité de gestion Office 365 ou Azure Sentinel pour accéder aux données d’audit de votre organisation. La suppression de la recherche dans le journal d’audit en suivant les étapes de cet article signifie qu’aucun résultat ne sera renvoyé lorsque vous effectuerez une recherche dans le journal d’audit à l’aide du Centre de sécurité & conformité ou lorsque vous exécutez la cmdlet **Search-UnifiedAuditLog** dans Exchange Online PowerShell. Cela signifie également que les journaux d’audit ne seront pas disponibles via l’API Activité de gestion Office 365 ou Azure Sentinel.
  
## <a name="before-you-turn-audit-log-search-on-or-off"></a>Avant d’activer ou de désactiver la recherche dans le journal d’audit

- Vous devez avoir le rôle Journaux d’audit dans Exchange Online pour activer ou désactiver la recherche dans le journal d’audit dans votre organisation Microsoft 365. Par défaut, ce rôle est affecté aux groupes de rôles Gestion de la conformité et Gestion de l’organisation dans la page **Autorisations** du Centre d’administration Exchange. Les administrateurs globaux dans Microsoft 365 sont membres du groupe de rôles Gestion de l’organisation dans Exchange Online. 
    
    > [!NOTE]
    > Des autorisations doivent être attribuées aux utilisateurs dans Exchange Online pour activer ou désactiver la recherche dans le journal d’audit. Si vous attribuez aux utilisateurs le rôle Journaux d’audit sur la page **Autorisations** du Centre de sécurité & conformité, ils ne pourront pas activer ou désactiver la recherche dans le journal d’audit. Cela est dû au fait que la cmdlet sous-jacente est une cmdlet Exchange Online PowerShell. 
    
- Pour obtenir des instructions détaillées sur la recherche dans le journal d’audit, consultez la recherche dans le journal d’audit dans le Centre de sécurité [& conformité.](search-the-audit-log-in-security-and-compliance.md) Pour plus d’informations sur l’API Activité de gestion Microsoft 365, voir Prise en charge des API de gestion [Microsoft 365.](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis)

- Pour vérifier que vous avez activé la recherche dans le journal d’audit, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

    La valeur de  `True` la  _propriété UnifiedAuditLogIngestionEnabled_ indique que la recherche dans le journal d’audit est désactivée. 
    
## <a name="turn-on-audit-log-search"></a>Activer la recherche dans le journal d’audit

Si la recherche dans le journal d’audit n’est pas désactivée pour votre organisation, vous pouvez l’activer dans le centre de conformité ou à l’aide d’Exchange Online PowerShell. L’ouverture de la recherche dans le journal d’audit peut prendre plusieurs heures avant de pouvoir renvoyer des résultats lors de la recherche dans le journal d’audit.
  
### <a name="use-the-compliance-center-to-turn-on-audit-log-search"></a>Utiliser le centre de conformité pour activer la recherche dans le journal d’audit

1. [Go to the compliance center](https://protection.office.com) and sign in.

2. Dans le centre de conformité, allez à la recherche **dans** le journal  >  **d’audit de recherche.**

   Si la recherche dans le journal d’audit n’est pas désactivée pour votre organisation, une bannière s’affiche pour vous dire que l’audit doit être allumé pour enregistrer l’activité des utilisateurs et des administrateurs.

3. Cliquez **sur Activer l’audit.**

    ![Cliquez sur Activer l’audit](../media/39a9d35f-88d0-4bbe-a962-0be2f838e2bf.png)
  
    La bannière est mise à jour pour dire que le journal d’audit est en cours de préparation et que vous pouvez rechercher l’activité des utilisateurs et des administrateurs dans quelques heures.

### <a name="use-powershell-to-turn-on-audit-log-search"></a>Utiliser PowerShell pour activer la recherche dans le journal d’audit

1. [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez la commande PowerShell suivante pour activer la recherche dans le journal d’audit dans Office 365.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Un message s’affiche pour vous dire que l’application de la modification peut prendre jusqu’à 60 minutes.
  
## <a name="turn-off-audit-log-search"></a>Désactiver la recherche dans le journal d’audit

Vous devez utiliser Exchange Online PowerShell pour désactiver la recherche dans le journal d’audit.
  
1. [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez la commande PowerShell suivante pour désactiver la recherche dans le journal d’audit.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Après un certain temps, vérifiez que la recherche dans le journal d’audit est désactivée. Vous pouvez procéder de deux manières :

    - Dans Exchange Online PowerShell, exécutez la commande suivante :

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      La valeur de  `False` la  _propriété UnifiedAuditLogIngestionEnabled_ indique que la recherche dans le journal d’audit est désactivée. 

    - Dans le centre [de conformité,](https://protection.office.com)allez à la recherche **dans** le journal \> **d’audit de recherche.**

      Une bannière s’affiche pour vous dire que l’audit doit être allumé pour enregistrer l’activité des utilisateurs et des administrateurs.
