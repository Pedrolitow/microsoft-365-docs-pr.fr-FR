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
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Les administrateurs peuvent apprendre à activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams, notamment comment définir des alertes pour les fichiers détectés.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 55923b13cf47e0309a7246ba43dcb9adaf3c58ff
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66016007"
---
# <a name="turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Microsoft Defender pour Office 365 pour SharePoint, OneDrive et Microsoft Teams protège votre organisation contre le partage involontaire de fichiers malveillants. Pour plus d’informations, consultez [Coffre Pièces jointes pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Cet article contient les étapes d’activation et de configuration des pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Coffre Pièces jointes**, utilisez <https://security.microsoft.com/safeattachmentv2>.

- Pour activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** dans le portail Microsoft 365 Defender. Pour plus d’informations, consultez [Autorisations dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md).

- Pour utiliser SharePoint PowerShell en ligne pour empêcher les utilisateurs de télécharger des fichiers malveillants, vous devez être membre des rôles [Administrateur général](/azure/active-directory/roles/permissions-reference#global-administrator) ou [Administrateur SharePoint](/azure/active-directory/roles/permissions-reference#sharepoint-administrator) dans Azure AD.

- Vérifiez que la journalisation d’audit est activée pour votre organisation. Si vous souhaitez en savoir plus, veuillez consulter la rubrique [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

- Autorisez jusqu’à 30 minutes pour que les paramètres prennent effet.

## <a name="step-1-use-the-microsoft-365-defender-portal-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Étape 1 : Utiliser le portail Microsoft 365 Defender pour activer les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Stratégies & règles** \> **Stratégies de menace** \> **Coffre pièces jointes** dans la section **Stratégies**. Pour accéder directement à la page **Coffre Pièces jointes**, utilisez <https://security.microsoft.com/safeattachmentv2>.

2. Dans la page **Coffre Pièces jointes**, cliquez sur **Paramètres globaux**.

3. Dans les **paramètres globaux** qui s’affichent, accédez à la section **Protéger les fichiers dans SharePoint, OneDrive et Microsoft Teams** section.

   Déplacez la **Defender pour Office 365 d’activation pour SharePoint, OneDrive et Microsoft Teams** basculez vers la droite![.](../../media/scc-toggle-on.png) pour activer les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

### <a name="use-exchange-online-powershell-to-turn-on-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams"></a>Utilisez Exchange Online PowerShell pour activer les pièces jointes Coffre pour SharePoint, OneDrive et Microsoft Teams

Si vous préférez utiliser PowerShell pour activer Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) et exécutez la commande suivante :

```powershell
Set-AtpPolicyForO365 -EnableATPForSPOTeamsODB $true
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

## <a name="step-2-recommended-use-sharepoint-online-powershell-to-prevent-users-from-downloading-malicious-files"></a>Étape 2 : (recommandé) Utiliser SharePoint Online PowerShell pour empêcher les utilisateurs de télécharger des fichiers malveillants

Par défaut, les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager<sup>\*</sup> des fichiers malveillants détectés par Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams. Toutefois, ils peuvent supprimer et télécharger des fichiers malveillants.

<sup>\*</sup> Si les utilisateurs accèdent à **Gérer l’accès**, l’option **Partager** est toujours disponible.

Pour empêcher les utilisateurs de télécharger des fichiers malveillants, [connectez-vous à SharePoint Online PowerShell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online) et exécutez la commande suivante :

```powershell
Set-SPOTenant -DisallowInfectedFileDownload $true
```

**Remarques** :

- Ce paramètre affecte les utilisateurs et les administrateurs.
- Les utilisateurs peuvent toujours supprimer des fichiers malveillants.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

## <a name="step-3-recommended-use-the-microsoft-365-defender-portal-to-create-an-alert-policy-for-detected-files"></a>Étape 3 (recommandé) Utiliser le portail Microsoft 365 Defender pour créer une stratégie d’alerte pour les fichiers détectés

Vous pouvez créer une stratégie d’alerte qui vous avertit, vous et d’autres administrateurs, lorsque Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams détecte un fichier malveillant. Pour en savoir plus sur les alertes, consultez [Stratégies d’alerte](../../compliance/alert-policies.md).

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à **Stratégies & la stratégie** **d’alerte** des règles\>. Pour accéder directement à la page **Stratégie d’alerte**, utilisez <https://security.microsoft.com/alertpolicies>.

2. Dans la page **Stratégie d’alerte** , cliquez sur **Nouvelle stratégie d’alerte**.

3. **L’Assistant Nouvelle stratégie d’alerte** s’ouvre dans un menu volant. Dans la page **Nommer votre alerte**, configurez les paramètres suivants :
   - **Nom** : tapez un nom unique et descriptif. Par exemple, fichiers malveillants dans les bibliothèques.
   - **Description** : Tapez une description facultative. Par exemple, avertit les administrateurs quand des fichiers malveillants sont détectés dans SharePoint Online, OneDrive ou Microsoft Teams.
   - Gravité : sélectionnez **Faible**, **Moyen** ou **Élevé** dans la liste **déroulante**.
   - Catégorie : Sélectionnez **Gestion des menaces** dans la liste **déroulante**.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Créer des paramètres d’alerte** , configurez les paramètres suivants :
   - **Sur quoi voulez-vous alerter ?** **L’activité** de la section \> sélectionne \> les **programmes malveillants détectés dans le fichier dans** la liste déroulante.
   - **Comment voulez-vous que l’alerte soit déclenchée ?** section : Laissez la valeur par défaut **chaque fois qu’une activité correspond à la règle** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. Dans la page **Définir vos destinataires** , configurez les paramètres suivants :
   - Vérifiez que **l’option Envoyer des notifications par e-mail** est sélectionnée. Dans la zone **Destinataires de l’e-mail** , sélectionnez un ou plusieurs administrateurs généraux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.
   - **Limite de notification quotidienne** : laissez la valeur par défaut **Aucune limite** sélectionnée.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

6. Dans la page **Vérifier vos paramètres** , passez en revue vos paramètres. Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Dans la section **« Voulez-vous activer immédiatement la stratégie ?** », laissez la valeur par défaut **Oui, puis activez-la immédiatement** .

   Lorsque vous avez terminé, cliquez sur **Terminer**.

### <a name="use-security--compliance-powershell-to-create-an-alert-policy-for-detected-files"></a>Utiliser Security & Compliance PowerShell pour créer une stratégie d’alerte pour les fichiers détectés

Si vous préférez utiliser PowerShell pour créer la même stratégie d’alerte que celle décrite dans la section précédente, [connectez-vous à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez la commande suivante :

```powershell
New-ActivityAlert -Name "Malicious Files in Libraries" -Description "Notifies admins when malicious files are detected in SharePoint Online, OneDrive, or Microsoft Teams" -Category ThreatManagement -Operation FileMalwareDetected -NotifyUser "admin1@contoso.com","admin2@contoso.com"
```

**Remarque** : la valeur _de gravité_ par défaut est Faible. Pour spécifier moyen ou élevé, _incluez le paramètre de gravité_ et la valeur dans la commande.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [New-ActivityAlert](/powershell/module/exchange/new-activityalert).

### <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

- Pour vérifier que vous avez correctement activé Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams, effectuez l’une des étapes suivantes :

  - Dans le portail Microsoft 365 Defender, accédez à **la section** \> Stratégies **& règles** sur les stratégies \> de **menace** \> **Coffre Pièces jointes**, sélectionnez **Paramètres globaux** et vérifiez la valeur de l’option **Activer Defender pour Office 365 pour SharePoint. OneDrive et Microsoft Teams** paramètre.

  - Dans Exchange Online PowerShell, exécutez la commande suivante pour vérifier le paramètre de propriété :

    ```powershell
    Get-AtpPolicyForO365 | Format-List EnableATPForSPOTeamsODB
    ```

    Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-AtpPolicyForO365](/powershell/module/exchange/get-atppolicyforo365).

- Pour vérifier que vous avez réussi à empêcher des personnes de télécharger des fichiers malveillants, ouvrez SharePoint Online PowerShell et exécutez la commande suivante pour vérifier la valeur de la propriété :

  ```powershell
  Get-SPOTenant | Format-List DisallowInfectedFileDownload
  ```

  Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-SPOTenant](/powershell/module/sharepoint-online/Set-SPOTenant).

- Pour vérifier que vous avez correctement configuré une stratégie d’alerte pour les fichiers détectés, effectuez l’une des étapes suivantes :
  - Dans le portail Microsoft 365 Defender, accédez à **Stratégies & règles** \> **Stratégie d’alerte** \> sélectionnez la stratégie d’alerte, puis vérifiez les paramètres.
  - Dans Microsoft 365 Defender portail PowerShell, remplacez \<AlertPolicyName\> par le nom de la stratégie d’alerte, exécutez la commande suivante et vérifiez les valeurs de propriété :

    ```powershell
    Get-ActivityAlert -Identity "<AlertPolicyName>"
    ```

    Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-ActivityAlert](/powershell/module/exchange/get-activityalert).

- Utilisez le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) pour afficher des informations sur les fichiers détectés dans SharePoint, OneDrive et Microsoft Teams. Plus précisément, vous pouvez utiliser les **données d’affichage par : affichage Programmes malveillants de contenu\>**.
