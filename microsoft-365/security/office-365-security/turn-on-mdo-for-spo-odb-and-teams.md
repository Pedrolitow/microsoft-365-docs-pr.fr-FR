---
title: Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Les administrateurs peuvent apprendre à activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams, notamment comment définir des alertes pour les fichiers détectés.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 8a1020193a49dd7b4871b9b9fec53d21073b03e6
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59202710"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams protects your organization from inadvertently sharing malicious files. Pour plus d’informations, [voir Coffre attachments for SharePoint, OneDrive, and Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Cet article contient les étapes permettant d’activer et de configurer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **Coffre pièces jointes,** ouvrez <https://security.microsoft.com/safeattachmentv2> .

- Pour activer les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams, vous devez être membre des  groupes  de rôles Gestion de l’organisation ou Administrateur de la sécurité dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Pour utiliser SharePoint Online PowerShell afin d’empêcher les personnes de télécharger [](/azure/active-directory/roles/permissions-reference#global-administrator) des fichiers malveillants, vous devez être membre des rôles Administrateur général ou Administrateur [SharePoint](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) dans Azure AD.

- Vérifiez que la journalisation d’audit est activée pour votre organisation. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

- Laissez jusqu’à 30 minutes pour que les paramètres prennent effet.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Étape 1 : utiliser le portail Microsoft 365 Defender pour activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams

1. Dans le portail Microsoft 365 Defender, go to **Policies & rules** Threat \> **policies** section \>  Coffre \> **Attachments**.

2. Dans la page **Coffre pièces jointes,** cliquez **sur Paramètres globaux.**

3. Dans la **section Paramètres globaux** qui **s’affiche,** allez dans la section Protéger les fichiers SharePoint, OneDrive et Microsoft Teams.

   Déplacez **l’activer pour Office 365** pour SharePoint, OneDrive et Microsoft Teams bascule vers la ![ droite.](../../media/scc-toggle-on.png) pour activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Utilisez Exchange Online PowerShell pour activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams

Si vous préférez utiliser PowerShell pour activer les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams, connectez-vous à [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Étape 2 : (recommandé) Utilisez SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants

Par défaut, les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager des fichiers malveillants détectés par les pièces jointes Coffre pour SharePoint, OneDrive et <sup>\*</sup> Microsoft Teams. Toutefois, ils peuvent supprimer et télécharger des fichiers malveillants.

<sup>\*</sup> Si les utilisateurs **accèdent à Gérer l’accès,** l’option **Partager** est toujours disponible.

Pour empêcher les utilisateurs de télécharger des fichiers malveillants, connectez-vous [à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) et exécutez la commande suivante :

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Remarques** :

- Ce paramètre affecte à la fois les utilisateurs et les administrateurs.
- Les utilisateurs peuvent toujours supprimer des fichiers malveillants.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>Étape 3 (recommandé) Utiliser le portail Microsoft 365 Defender pour créer une stratégie d’alerte pour les fichiers détectés

Vous pouvez créer une stratégie d’alerte qui vous avertit, ainsi qu’à d’autres administrateurs, lorsque Coffre Attachments for SharePoint, OneDrive et Microsoft Teams détecte un fichier malveillant. Pour en savoir plus sur les alertes, consultez stratégies [d’alerte.](../../compliance/alert-policies.md)

1. Dans le portail Microsoft 365 Defender, go to **Policies & Rules** Alert \> **policy** or open <https://security.microsoft.com/alertpolicies> .

2. Dans la page **Stratégie d’alerte,** cliquez **sur Nouvelle stratégie d’alerte.**

3. **L’Assistant Nouvelle stratégie** d’alerte s’ouvre dans un volant. Dans la page **Nom de votre** alerte, configurez les paramètres suivants :
   - **Nom**: tapez un nom unique et descriptif. Par exemple, fichiers malveillants dans les bibliothèques.
   - **Description**: tapez une description facultative. Par exemple, avertit les administrateurs lorsque des fichiers malveillants sont détectés dans SharePoint Online, OneDrive ou Microsoft Teams.
   - **Gravité :** sélectionnez **Faible,** **Moyen** ou **Élevé** dans la liste de listes.
   - **Catégorie :** sélectionnez **La gestion des menaces** dans la liste liste.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Créer des paramètres d’alerte,** configurez les paramètres suivants :
   - **Sur quoi voulez-vous alerter ?** \> **l’activité de section** consiste à sélectionner les programmes \> **malveillants détectés dans le fichier** dans la liste de listes.
   - **Comment voulez-vous que l’alerte soit déclenchée ?** section : laissez la valeur par défaut **Chaque fois qu’une activité correspond à la règle** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Définir vos destinataires,** configurez les paramètres suivants :
   - Vérifiez **que les notifications d’envoi** par courrier électronique sont sélectionnées. Dans la zone **Destinataires de** l’e-mail, sélectionnez un ou plusieurs administrateurs globaux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.
   - **Limite de notification quotidienne**: laissez la valeur par défaut **Aucune** limite sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Passer en revue vos paramètres,** examinez vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Dans la section **Voulez-vous activer** la stratégie immédiatement ? Laissez la valeur par défaut Oui, l’activer **immédiatement** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Terminer**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Utiliser Security & Compliance PowerShell pour créer une stratégie d’alerte pour les fichiers détectés

Si vous préférez utiliser PowerShell pour créer la même stratégie d’alerte que décrite dans la section précédente, connectez-vous au Centre de sécurité & conformité [PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez la commande suivante :

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Remarque**: la valeur _gravité par défaut_ est Faible. Pour spécifier Medium ou High, incluez le paramètre _Severity_ et la valeur dans la commande.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir New-ActivityAlert.](/powershell/module/exchange/new-activityalert)

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

- Pour vérifier que vous avez réussi à Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams, utilisez l’une des étapes suivantes :

  - Dans le portail Microsoft 365 Defender, go to **Policies & rules** Threat \> **Policies** section \>  Coffre \> **Attachments,** select Global **settings**, and verify the value of the **Turn on Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams** setting.

  - Dans Exchange Online PowerShell, exécutez la commande suivante pour vérifier le paramètre de propriété :

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Pour vérifier que vous avez réussi à bloquer le téléchargement de fichiers malveillants, ouvrez SharePoint Online PowerShell et exécutez la commande suivante pour vérifier la valeur de la propriété :

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Pour vérifier que vous avez correctement configuré une stratégie d’alerte pour les fichiers détectés, utilisez l’une des étapes suivantes :
  - Dans le portail Microsoft 365 Defender, sélectionnez **Stratégies &** Stratégie d’alerte Sélectionnez la stratégie d’alerte et vérifiez \>  \> les paramètres.
  - Dans Microsoft 365 Defender portail PowerShell, remplacez par le nom de la stratégie d’alerte, exécutez la commande suivante et vérifiez les valeurs \<AlertPolicyName\> des propriétés :

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Pour obtenir des informations détaillées sur la syntaxe et les paramètres, [voir Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Utilisez le [rapport d’état de la protection](view-email-security-reports.md#threat-protection-status-report) contre les menaces pour afficher les informations sur les fichiers détectés dans SharePoint, OneDrive et Microsoft Teams. Plus précisément, vous pouvez utiliser l’affichage des données **par : Affichage des programmes \> malveillants** de contenu.
