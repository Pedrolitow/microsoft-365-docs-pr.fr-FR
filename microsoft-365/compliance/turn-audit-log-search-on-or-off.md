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
description: Comment activer ou désactiver la fonctionnalité de recherche de journal d’audit dans le centre de sécurité & conformité afin d’activer ou de désactiver la capacité des administrateurs à rechercher dans le journal d’audit.
ms.openlocfilehash: 4571c90c4fa680acd8925e83e32ffcf07de7d626
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44819134"
---
# <a name="turn-audit-log-search-on-or-off"></a>Activer ou désactiver la recherche dans le journal d’audit

Vous (ou un autre administrateur) devez activer la journalisation d’audit pour pouvoir commencer à rechercher dans le journal d’audit. Lorsque la recherche du journal d’audit dans le centre de sécurité & conformité est activée, l’activité de l’utilisateur et de l’administrateur de votre organisation est enregistrée dans le journal d’audit et conservée pendant 90 jours, et jusqu’à un an en fonction de la licence attribuée aux utilisateurs. Toutefois, votre organisation peut avoir des raisons de ne pas vouloir enregistrer et conserver les données du journal d’audit. Dans ce cas, un administrateur général peut décider de désactiver l’audit dans Microsoft 365.

> [!IMPORTANT]
> Si vous désactivez la recherche de journal d’audit dans Microsoft 365, vous ne pouvez pas utiliser l’API activité de gestion d’Office 365 ou Azure sentinelle pour accéder aux données d’audit de votre organisation. La désactivation de la recherche du journal d’audit en suivant les étapes décrites dans cet article signifie qu’aucun résultat n’est renvoyé lorsque vous effectuez une recherche dans le journal d’audit à l’aide du centre de sécurité & conformité ou lorsque vous exécutez la cmdlet **Search-UnifiedAuditLog** dans Exchange Online PowerShell. Cela signifie également que les journaux d’audit ne seront pas disponibles via l’API activité de gestion d’Office 365 ou Azure sentinelle.
  
## <a name="before-you-turn-audit-log-search-on-or-off"></a>Avant d’activer ou de désactiver la recherche dans le journal d’audit

- Vous devez disposer du rôle journaux d’audit dans Exchange Online pour activer ou désactiver la recherche dans le journal d’audit dans votre organisation Microsoft 365. Par défaut, ce rôle est affecté aux groupes de rôles gestion de la conformité et gestion de l’organisation dans la page **autorisations** du centre d’administration Exchange. Les administrateurs globaux de Microsoft 365 sont membres du groupe de rôles gestion de l’organisation dans Exchange Online. 
    
    > [!NOTE]
    > Les utilisateurs doivent disposer d’autorisations dans Exchange Online pour activer ou désactiver la recherche dans le journal d’audit. Si vous affectez des utilisateurs au rôle journaux d’audit sur la page **autorisations** dans le centre de sécurité & conformité, ils ne pourront pas activer ou désactiver la recherche dans le journal d’audit. Cela est dû au fait que la cmdlet sous-jacente est une applet de commande Exchange Online. 
    
- Pour obtenir des instructions détaillées sur la recherche dans le journal d’audit, voir [Search the audit log dans le centre de sécurité & Compliance Center](search-the-audit-log-in-security-and-compliance.md). Pour plus d’informations sur l’API activité de gestion de Microsoft 365, reportez-vous à la rubrique [prise en main des API de gestion microsoft 365](https://docs.microsoft.com/office/office-365-management-api/get-started-with-office-365-management-apis).
    
## <a name="turn-on-audit-log-search"></a>Activer la recherche du journal d’audit

Vous pouvez utiliser le centre de sécurité & conformité ou PowerShell pour activer la recherche dans le journal d’audit dans Microsoft 365. L’activation de la recherche de journal d’audit peut prendre plusieurs heures avant de pouvoir renvoyer des résultats lors de la recherche dans le journal d’audit. Vous devez disposer du rôle journaux d’audit dans Exchange Online pour activer la recherche dans le journal d’audit.
  
### <a name="use-the-security--compliance-center-to-turn-on-audit-log-search"></a>Utiliser le centre de sécurité & conformité pour activer la recherche dans le journal d’audit

1. [Accédez au centre de sécurité & conformité](https://protection.office.com) et connectez-vous.

2. Dans le centre de sécurité & conformité, accédez **Search** à recherche dans le \> **Journal d’audit**de la recherche.

   Une bannière s’affiche indiquant que l’audit doit être activé pour enregistrer l’activité de l’utilisateur et de l’administrateur.

3. Cliquez sur **activer l’audit**.

    ![Cliquez sur Activer l’audit](../media/39a9d35f-88d0-4bbe-a962-0be2f838e2bf.png)
  
    La bannière est mise à jour pour indiquer que le journal d’audit est en cours de préparation et que vous pouvez rechercher l’activité de l’utilisateur et de l’administrateur en quelques heures.

### <a name="use-powershell-to-turn-on-audit-log-search"></a>Utiliser PowerShell pour activer la recherche dans le journal d’audit

1. [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=396554)

2. Exécutez la commande PowerShell suivante pour activer la recherche dans le journal d’audit dans Office 365.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Un message s’affiche indiquant que la modification peut prendre jusqu’à 60 minutes.
  
## <a name="turn-off-audit-log-search"></a>Désactiver la recherche de journal d’audit

Vous devez utiliser PowerShell à distance connecté à votre organisation Exchange Online pour désactiver la recherche de journal d’audit. De la même manière que pour activer la recherche dans le journal d’audit, vous devez disposer du rôle journaux d’audit dans Exchange Online pour désactiver la recherche de journal d’audit.
  
1. [Connexion à Exchange Online PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=396554)

2. Exécutez la commande PowerShell suivante pour désactiver la recherche dans le journal d’audit dans Office 365.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Après un certain temps, vérifiez que la recherche dans le journal d’audit est désactivée (désactivée). Vous pouvez procéder de deux manières :

    - Dans PowerShell, exécutez la commande suivante :

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

      La valeur de `False` pour la propriété _UnifiedAuditLogIngestionEnabled_ indique que la recherche du journal d’audit est désactivée. 

    - Dans le [Centre de sécurité & conformité](https://protection.office.com), accédez **Search** à recherche dans le \> **Journal d’audit**de la recherche.

      Une bannière s’affiche indiquant que l’audit doit être activé pour enregistrer l’activité de l’utilisateur et de l’administrateur.