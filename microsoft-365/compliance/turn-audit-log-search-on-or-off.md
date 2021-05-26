---
title: Activer ou désactiver l’audit
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
description: Comment activer ou désactiver la fonctionnalité de recherche du journal d’audit dans le Centre de conformité Microsoft 365 pour activer ou désactiver la possibilité pour les administrateurs de rechercher dans le journal d’audit.
ms.openlocfilehash: 091331a40a2ab6bf3c05bb289d49f63ab2dd2794
ms.sourcegitcommit: 4f6ef4cd09c3ed36dc0be3702b0636bad6cff8a9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/26/2021
ms.locfileid: "52657732"
---
# <a name="turn-auditing-on-or-off"></a>Activer ou désactiver l’audit

Nous activons par défaut la journalisation d’audit pour les organisations d’entreprise Microsoft 365 et Office 365. Cela inclut les organisations disposant d’abonnements E3/G3 ou E5/G5. Lorsque l’audit dans le centre de conformité est allumé, les activités des utilisateurs et des administrateurs de votre organisation sont enregistrées dans le journal d’audit et conservées pendant 90 jours et jusqu’à un an en fonction de la licence attribuée aux utilisateurs. Toutefois, votre organisation peut avoir des raisons de ne pas vouloir enregistrer et conserver les données du journal d’audit. Dans ce cas, un administrateur global peut décider de désactiver l’audit dans Microsoft 365.

> [!IMPORTANT]
> Si vous désactiver l’audit dans Microsoft 365, vous ne pouvez pas utiliser l’API activité de gestion Office 365 ou Azure Sentinel pour accéder aux données d’audit de votre organisation. La suppression de l’audit en suivant les étapes de cet article signifie qu’aucun résultat ne sera renvoyé lorsque vous effectuerez une recherche dans le journal d’audit à l’aide du Centre de sécurité & conformité ou lorsque vous exécutez la cmdlet **Search-UnifiedAuditLog** dans Exchange Online PowerShell. Cela signifie également que les journaux d’audit ne seront pas disponibles via l Office 365 API Activité de gestion ou Azure Sentinel.
  
## <a name="before-you-turn-auditing-on-or-off"></a>Avant d’activer ou de désactiver l’audit

- Le rôle Journaux d’audit doit vous être attribué dans Exchange Online pour activer ou désactiver l’audit dans Microsoft 365 organisation. Par défaut, ce rôle est attribué aux groupes de rôles Gestion de la conformité et Gestion de l’organisation dans la page **Autorisations** du Centre d Exchange de conformité. Les administrateurs globaux Microsoft 365 sont membres du groupe de rôles Gestion de l’organisation dans Exchange Online. 

    > [!NOTE]
    > Des autorisations doivent être attribuées aux utilisateurs Exchange Online pour activer ou désactiver l’audit. Si vous attribuez aux utilisateurs le rôle Journaux d’audit sur la page **Autorisations** du Centre de sécurité & conformité, ils ne pourront pas activer ou désactiver l’audit. Cela est dû au fait que l’cmdlet sous-jacente est Exchange Online cmdlet PowerShell. 

- Pour obtenir des instructions détaillées sur la recherche dans le journal d’audit, voir Rechercher dans le journal d’audit dans le Centre de sécurité [& conformité.](search-the-audit-log-in-security-and-compliance.md) Pour plus d’informations sur l’API activité Microsoft 365 gestion, voir Prise en [Microsoft 365 API de gestion des données.](/office/office-365-management-api/get-started-with-office-365-management-apis)

- Pour vérifier que l’audit est allumé, vous pouvez exécuter la commande suivante dans Exchange Online PowerShell :

    ```powershell
    Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
    ```

    La valeur de  `True` la  _propriété UnifiedAuditLogIngestionEnabled_ indique que l’audit est allumé. 

## <a name="turn-on-auditing"></a>Activer l’audit

Si l’audit n’est pas allumé pour votre organisation, vous pouvez l’activer dans le centre de conformité ou à l’aide Exchange Online PowerShell. L’opération d’audit peut prendre plusieurs heures avant que vous ne renvoyiez des résultats lors de la recherche dans le journal d’audit.
  
### <a name="use-the-compliance-center-to-turn-on-auditing"></a>Utiliser le centre de conformité pour activer l’audit

1. Accédez à <https://compliance.microsoft.com> et connectez-vous.

2. Dans le volet de navigation gauche du centre Microsoft 365 conformité, cliquez sur Afficher **tout,** puis sur **Auditer.**

   Si l’audit n’est pas désactivé pour votre organisation, une bannière s’affiche pour vous invite à commencer à enregistrer l’activité des utilisateurs et des administrateurs.

   ![Bannière sur la page Audit](../media/39a9d35f-88d0-4bbe-a962-0be2f838e2bf.png)

3. Cliquez sur la **bannière Démarrer l’enregistrement de l’activité de l’utilisateur et de l’administrateur.**

   L’application de la modification peut prendre jusqu’à 60 minutes.

### <a name="use-powershell-to-turn-on-auditing"></a>Utiliser PowerShell pour activer l’audit

1. [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez la commande PowerShell suivante pour activer l’audit dans Office 365.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $true
    ```

    Un message s’affiche pour vous dire que l’application de la modification peut prendre jusqu’à 60 minutes.
  
## <a name="turn-off-auditing"></a>Désactiver l’audit

Vous devez utiliser Exchange Online PowerShell pour désactiver l’audit.
  
1. [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell)

2. Exécutez la commande PowerShell suivante pour désactiver l’audit.

    ```powershell
    Set-AdminAuditLogConfig -UnifiedAuditLogIngestionEnabled $false
    ```

3. Après un certain temps, vérifiez que l’audit est désactivé. Il existe deux méthodes pour y parvenir :

    - Dans Exchange Online PowerShell, exécutez la commande suivante :

      ```powershell
      Get-AdminAuditLogConfig | FL UnifiedAuditLogIngestionEnabled
      ```

      La valeur de  `False` la  _propriété UnifiedAuditLogIngestionEnabled_ indique que l’audit est désactivé.

    - Go to the **Audit** page in the Microsoft 365 compliance center.

      Si l’audit n’est pas désactivé pour votre organisation, une bannière s’affiche pour vous invite à commencer à enregistrer l’activité des utilisateurs et des administrateurs.
