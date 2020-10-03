---
title: Activer l’ATP Office 365-SharePoint, OneDrive & teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Découvrez comment activer la protection avancée contre les menaces pour SharePoint, OneDrive et Teams, y compris comment définir des alertes pour les fichiers détectés.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 0c717a89492ea1160f26f26f13be6c36f348c79c
ms.sourcegitcommit: 3a0accd616ca94d6ba7f50e502552b45e9661a95
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/03/2020
ms.locfileid: "48350654"
---
# <a name="turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Activer PACM pour SharePoint, OneDrive et Microsoft Teams.

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

Office 365 Advanced Threat Protection (ATP) for SharePoint, OneDrive et Microsoft teams protège votre organisation contre le partage accidentel de fichiers malveillants. Pour plus d’informations, reportez-vous à la rubrique [ATP pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md).

Cet article décrit la procédure d’activation et de configuration de la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com>. Pour accéder directement à la page **pièces jointes approuvées ATP** , ouvrez <https://protection.office.com/safeattachmentv2> .

- Pour activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** dans le centre de sécurité & conformité. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

- Pour utiliser SharePoint Online PowerShell afin d’empêcher les utilisateurs de télécharger des fichiers malveillants, vous devez être membre des rôles administrateur [général](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#global-administrator--company-administrator) ou [administrateur SharePoint](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles#sharepoint-administrator) dans Azure ad.

- Vérifiez que la journalisation d’audit est activée pour votre organisation. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

- Autorisez jusqu’à 30 minutes pour que les paramètres prennent effet.

## <a name="step-1-use-the-security--compliance-center-to-turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Étape 1 : utiliser le centre de sécurité & conformité pour activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP**et cliquez sur **paramètres globaux**.

2. Dans les **paramètres globaux** , sélectionnez le passage à la sortie qui s’affiche, puis cliquez sur le paramètre Activer la protection avancée contre les menaces **pour SharePoint, OneDrive et Microsoft teams** . Déplacez le bouton bascule vers la droite sur Activer pour activer la protection avancée contre les menaces ![ ](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png) pour SharePoint, OneDrive et Microsoft Teams.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="use-exchange-online-powershell-to-turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Utiliser Exchange Online PowerShell pour activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams

Si vous préférez utiliser PowerShell pour activer la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams, [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Étape 2 : (recommandé) utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants

Par défaut, les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager des fichiers malveillants détectés par la protection avancée contre les menaces. Toutefois, ils peuvent supprimer et télécharger des fichiers malveillants.

Pour empêcher les utilisateurs de télécharger des fichiers malveillants, [Connectez-vous à SharePoint Online PowerShell](https://docs.microsoft.com/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) et exécutez la commande suivante :

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Remarques** :

- Ce paramètre affecte les utilisateurs et les administrateurs.
- Les utilisateurs peuvent toujours supprimer des fichiers malveillants.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-security--compliance-center-to-create-an-alert-policy-for-detected-files"></a>Étape 3 (recommandé) utiliser le centre de sécurité & conformité pour créer une stratégie d’alerte pour les fichiers détectés

Vous pouvez créer une stratégie d’alerte qui vous avertit, ainsi que d’autres administrateurs, lorsque la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft teams détecte un fichier malveillant. Pour en savoir plus sur les alertes, voir [créer des alertes d’activité dans le centre de sécurité & conformité](../../compliance/create-activity-alerts.md).

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), accédez à **alertes** d' \> **alerte** ou ouvrez <https://protection.office.com/alertpolicies> .

2. Sur la page **stratégies d’alerte** , cliquez sur **nouvelle stratégie d’alerte**.

3. L’Assistant **nouvelle stratégie d’alerte** s’ouvre en un passage. Sur la page **nommer votre alerte** , configurez les paramètres suivants :

   - **Nom**: tapez un nom unique et descriptif. Par exemple, des fichiers malveillants dans les bibliothèques.
   - **Description**: tapez une description facultative. Par exemple, avertir les administrateurs lorsque des fichiers malveillants sont détectés dans SharePoint Online, OneDrive ou Microsoft Teams.
   - **Gravité**: laissez la valeur par défaut **faible** sélectionnée ou sélectionnez **moyenne** ou **élevée**.
   - **Sélectionnez une catégorie**: sélectionnez **gestion des menaces**.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Sur la page **créer des paramètres d’alerte** , configurez les paramètres suivants :

   - **Sur quoi souhaitez-vous alerter ?: activité**: sélectionnez **programmes malveillants détectés dans le fichier**.
   - **Comment voulez-vous que l’alerte soit déclenchée ?**: conservez la valeur par défaut **chaque fois qu’une activité correspond à la règle** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Sur la page **définir vos destinataires** , configurez les paramètres suivants :

   - **Envoyer des notifications par courrier électronique**: Vérifiez que ce paramètre est sélectionné. Dans la zone **destinataires du message** , sélectionnez un ou plusieurs administrateurs globaux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.
   - **Limite quotidienne des notifications**: laissez la valeur par défaut **aucune limite** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Sur la page **vérifier vos paramètres** , passez en revue les paramètres, puis cliquez sur **modifier** dans n’importe quelle section pour apporter des modifications.

   Dans la section souhaitez **-vous activer la stratégie immédiatement ?** , conservez la valeur par défaut **Oui, activez-** la immédiatement.

   Lorsque vous avez terminé, cliquez sur **Terminer**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Utiliser la sécurité & PowerShell de conformité pour créer une stratégie d’alerte pour les fichiers détectés

Si vous préférez utiliser PowerShell pour créer la même stratégie d’alerte que celle décrite dans la section précédente, [Connectez-vous au centre de sécurité & Compliance Center PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-scc-powershell) et exécutez la commande suivante :

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Remarque**: la valeur de _gravité_ par défaut est faible. Pour spécifier une valeur moyenne ou élevée, incluez le paramètre de _gravité_ et la valeur dans la commande.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [New-ActivityAlert](https://docs.microsoft.com/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

- Pour vérifier que vous avez bien activé la protection avancée contre les menaces pour SharePoint, OneDrive et Microsoft Teams, procédez comme suit :

  - Dans le [Centre de sécurité & conformité](https://protection.office.com), accédez à la stratégie de **gestion des menaces** \> **Policy** \> **pièces jointes approuvées ATP**, sélectionnez **paramètres globaux**et vérifiez la valeur du paramètre **activer l’ATP pour SharePoint, OneDrive et Microsoft teams** .

  - Dans Exchange Online PowerShell, exécutez la commande suivante pour vérifier le paramètre de la propriété :

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/get-atppolicyforo365).

- Pour vérifier que vous avez bien bloqué le téléchargement de fichiers malveillants, ouvrez SharePoint Online PowerShell et exécutez la commande suivante pour vérifier la valeur de la propriété :

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant).

- Pour vérifier que vous avez bien configuré une stratégie d’alerte pour les fichiers détectés, procédez comme suit :

  - Dans le centre de sécurité & conformité, accédez à **alertes** \> **Alert Policies** \> , sélectionnez la stratégie d’alerte et vérifiez les paramètres.

  - Dans sécurité & Centre de conformité PowerShell, remplacez \<AlertPolicyName\> par le nom de la stratégie d’alerte, exécutez la commande suivante et vérifiez les valeurs des propriétés :

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Get-ActivityAlert](https://docs.microsoft.com/powershell/module/exchange/get-activityalert).

- Utilisez le [rapport d’état de protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) pour afficher les informations sur les fichiers détectés dans SharePoint, OneDrive et Microsoft Teams. Plus précisément, vous pouvez utiliser l’affichage **des données en : affichage des \> programmes malveillants de contenu** .
