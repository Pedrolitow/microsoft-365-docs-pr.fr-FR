---
title: Utiliser des étiquettes de confidentialité avec Microsoft Teams, les groupes Office 365 et les sites SharePoint (préversion publique)
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 12/05/2019
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
description: Vous pouvez appliquer des étiquettes à Microsoft Teams, aux groupes Office 365 et aux sites SharePoint.
ms.openlocfilehash: e69968ad5939069ca8ae1611f3bbdc674f9dd7de
ms.sourcegitcommit: 2468bcb01625f97a322459814d81b9faad717859
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/05/2019
ms.locfileid: "39871250"
---
# <a name="use-sensitivity-labels-with-microsoft-teams-office-365-groups-and-sharepoint-sites-public-preview"></a>Utiliser des étiquettes de confidentialité avec Microsoft Teams, les groupes Office 365 et les sites SharePoint (préversion publique)

Lorsque vous créez des étiquettes de confidentialité dans le [Centre de conformité microsoft 365](https://protection.office.com/), vous pouvez les appliquer à Microsoft Teams, aux groupes Office 365 et aux sites SharePoint. Vous pouvez associer des stratégies aux étiquettes pour contrôler :

- Paramètres publics/privés
- Accès invité
- Accès à partir d’appareils non gérés

Lorsque vous appliquez une étiquette à une équipe ou un groupe, l’étiquette s’applique automatiquement au site d’équipe SharePoint connecté et inversement.

À présent, vous pouvez également activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive. [En savoir plus](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="about-the-public-preview-for-microsoft-teams-office-365-groups-and-sharepoint-sites"></a>À propos de la préversion publique pour Microsoft Teams, les groupes Office 365 et les sites SharePoint

Les étiquettes de sensibilité pour Microsoft Teams, les groupes Office 365 et les sites SharePoint sont progressivement déployés sur les clients et peuvent changer avant la version finale.

La préversion publique ne fonctionne pas avec les réseaux de distribution de contenu (CDN) Office 365.

## <a name="overview"></a>Vue d'ensemble

Lorsque vous publiez des étiquettes de confidentialité, les utilisateurs d’Office 365 ont accès à la même liste d’étiquettes.

Ces images présentent les éléments suivants :

- Affichage de la liste lors de la création d’un site d’équipe à partir de SharePoint

- Lorsque vous affichez la liste dans Word

![Étiquette de critère de diffusion lors de la création d’un site d’équipe à partir de SharePoint](media/sensitivity-label-new-team-site.png)

![Étiquette de confidentialité affichée dans l’application Word de bureau](media/sensitivity-label-word.png)

## <a name="enable-this-preview-by-using-azure-powershell"></a>Activer cet aperçu à l’aide d’Azure PowerShell

1. Connectez-vous à Azure en tant qu’administrateur général à l’aide d’Azure PowerShell. Pour obtenir des instructions, consultez la rubrique [se connecter avec Azure PowerShell](/powershell/azure/authenticate-azureps).

2. Exécutez la commande suivante :

```powershell
  Connect-AzureAD
  $setting=(Get-AzureADDirectorySetting | where -Property DisplayName -Value "Group.Unified" -EQ)
  if ($setting -eq $null)
  {
    $template = Get-AzureADDirectorySettingTemplate -Id 62375ab9-6b52-47ed-826b-58e47e0e304b
    $setting = $template.CreateDirectorySetting()
    $setting["EnableMIPLabels"] = "True"
    New-AzureADDirectorySetting -DirectorySetting $setting
  }
  else
  {
    $setting["EnableMIPLabels"] = "True"
    Set-AzureADDirectorySetting -Id $setting.Id -DirectorySetting $setting
  }
```

Office 365 n’utilise plus les anciennes classifications pour les nouveaux groupes et les sites SharePoint lorsque vous activez cet aperçu. Si vous avez utilisé la [Classification de site Azure ad](/sharepoint/dev/solution-guidance/modern-experience-site-classification) ($Setting ["ClassificationList"]), les groupes et les sites existants affichent toujours les anciennes classifications. Pour afficher les nouvelles classifications, convertissez-les. Pour plus d’informations sur la façon de les convertir, voir [si vous avez utilisé une classification de site Azure ad classique](#if-you-used-classic-azure-ad-site-classification). 

## <a name="set-site-and-group-settings-when-you-create-or-edit-sensitivity-labels"></a>Définir les paramètres de site et de groupe lors de la création ou de la modification des étiquettes de confidentialité

Une fois l’aperçu activé, procédez comme suit pour créer ou modifier des étiquettes de confidentialité. Vous devez effectuer ces étapes pour que les nouvelles étiquettes de sensibilité fonctionnent avec les sites et les groupes, même si vous avez déjà défini des étiquettes. La synchronisation des modifications apportées à ces paramètres peut prendre jusqu’à 24 heures.

1. Dans le centre de conformité Microsoft 365, sélectionnez**Etiquettes**de **classification** > .

2. Sélectionnez **créer une étiquette**. Si vous avez déjà une étiquette, passez à l’étape suivante.

3. Sélectionnez les options souhaitées, puis sous l’onglet **paramètres de site et de groupe** , choisissez :

    - Confidentialité (publique/privée) : privé signifie que seuls les membres approuvés de votre organisation peuvent voir ce qui se trouve à l’intérieur du groupe. Les autres utilisateurs de votre organisation ne peuvent pas voir ce qui se trouve dans le groupe. [En savoir plus](https://support.office.com/article/36236e39-26d3-420b-b0ac-8072d2d2bedc)
    - Accès invité : vous pouvez contrôler si des invités peuvent être ajoutés à un groupe. [En savoir plus sur la gestion de l’accès invité dans les groupes Office 365](/office365/admin/create-groups/manage-guest-access-in-groups)
    - Périphériques non gérés : ce paramètre vous permet de bloquer ou de limiter l’accès au contenu SharePoint à partir d’appareils qui ne sont pas liés à une publicité hybride ou qui ne sont pas conformes dans Intune. Si vous sélectionnez appareils non gérés, vous devez accéder à Azure AD pour terminer la configuration de la stratégie. Pour plus d’informations, consultez la rubrique [contrôler l’accès à partir d’appareils non gérés](/sharepoint/control-access-from-unmanaged-devices).

![Onglet Paramètres de site et de groupe](media/edit-sensitivity-label-site-group.png)

> [!IMPORTANT]
> Seuls les paramètres de site et de groupe prennent effet lorsque vous appliquez une étiquette à une équipe, un groupe ou un site. D’autres paramètres, tels que le chiffrement et le marquage de contenu, ne sont pas appliqués à tout le contenu au sein de l’équipe, du groupe ou du site. De même, si vous créez une étiquette et que vous n’activez pas les paramètres de site et de groupe, l’étiquette reste disponible lorsque les utilisateurs créent des équipes, des groupes et des sites, mais il ne peut rien faire lorsque les utilisateurs l’appliquent.

[En savoir plus sur la publication d’une étiquette de sensibilité](/microsoft-365/compliance/sensitivity-labels#what-label-policies-can-do)

## <a name="troubleshoot-sensitivity-label-deployment"></a>Résoudre les problèmes de déploiement des étiquettes de confidentialité

Si vous rencontrez des problèmes lorsque vous créez un groupe teams ou Office 365 après avoir activé ces paramètres ou modifié la description d’une étiquette de sensibilité, enregistrez l’étiquette, patientez quelques heures, puis réessayez de créer le groupe Team 365 ou Office. Pour plus d’informations, consultez [la rubrique planifier un déploiement après avoir créé ou modifié une étiquette de critère de diffusion](sensitivity-labels-sharepoint-onedrive-files.md#schedule-roll-out-after-you-create-or-change-a-sensitivity-label).

Si vous ne parvenez toujours pas à voir la nouvelle étiquette de sensibilité à partir de SharePoint Online, contactez immédiatement le support Microsoft.

## <a name="apply-a-sensitivity-label-to-a-new-team"></a>Appliquer une étiquette de critère de diffusion à une nouvelle équipe

Les utilisateurs peuvent sélectionner des étiquettes de confidentialité lorsqu’ils créent de nouvelles équipes dans Microsoft Teams. Lorsqu’ils sélectionnent le niveau de confidentialité, le paramètre de confidentialité change si nécessaire. Selon le paramètre d’accès invité que vous avez sélectionné pour l’étiquette, les utilisateurs peuvent ou ne peuvent pas ajouter des personnes en dehors de l’organisation à l’équipe.

![Paramètre de confidentialité lors de la création d’une équipe](media/privacy-setting-new-team.png)

Une fois l’équipe créée, l’étiquette de sensibilité apparaît dans le coin supérieur droit de tous les canaux.

![L’étiquette de sensibilité apparaît dans l’équipe.](media/privacy-setting-teams.png)

Le service applique automatiquement la même étiquette de confidentialité au groupe Office 365 et au site d’équipe SharePoint connecté.

## <a name="apply-a-sensitivity-label-to-a-new-group"></a>Application d’une étiquette de critère de diffusion à un nouveau groupe

Dans Outlook sur le Web, la zone nouvelle **sensibilité** contient des étiquettes publiées. Si les utilisateurs souhaitent obtenir plus d’informations, ils peuvent cliquer sur l’icône d’aide pour lire les détails sur les étiquettes disponibles et les stratégies associées.

![Création d’un groupe et sélection d’une option sous sensibilité](media/sensitivity-label-new-group.png)

## <a name="apply-a-sensitivity-label-to-a-new-site"></a>Appliquer une étiquette de critère de diffusion à un nouveau site

Les administrateurs et les utilisateurs finaux peuvent sélectionner des étiquettes de confidentialité lors de la création de sites d’équipe et de sites de communication modernes.

[Découvrez comment créer un site dans le nouveau centre d’administration SharePoint](/sharepoint/create-site-collection)

Lorsque les utilisateurs créent des sites d’équipe et de communication modernes, une étiquette de sensibilité est déjà sélectionnée par défaut. Les utilisateurs peuvent sélectionner l’icône aide pour en savoir plus sur les étiquettes.

![Création d’un site et sélection d’une option sous sensibilité](media/sensitivity-label-new-communication-site.png)

Lorsque les utilisateurs accèdent au site, ils peuvent voir le nom de l’étiquette et des stratégies appliquées.

![Un site auquel une étiquette de sensibilité est appliquée](media/sensitivity-label-site.png)

## <a name="manage-sensitivity-labels-in-the-sharepoint-admin-center"></a>Gérer les étiquettes de confidentialité dans le centre d’administration SharePoint

Pour afficher et modifier les étiquettes, utilisez la page sites actifs dans le nouveau centre d’administration SharePoint.

![Colonne critère de diffusion de la page sites actifs](media/manage-site-sensitivity-labels.png)

[En savoir plus sur la gestion des sites dans le nouveau centre d’administration SharePoint](/sharepoint/manage-sites-in-new-admin-center).

## <a name="change-site-and-group-settings-for-a-label"></a>Modifier les paramètres de site et de groupe d’une étiquette

Il est recommandé de ne pas modifier les paramètres après avoir appliqué une étiquette à plusieurs équipes, groupes ou sites. Si vous devez effectuer une modification, vous devez utiliser un script Azure AD PowerShell pour appliquer les mises à jour manuellement. Cette méthode garantit que toutes les équipes, les sites et les groupes existants appliquent le nouveau paramètre.

## <a name="support-for-the-new-sensitivity-labels"></a>Prise en charge des nouvelles étiquettes de sensibilité

Les applications et services suivants prennent en charge les étiquettes de sensibilité dans cet aperçu :

- Centre de conformité Microsoft 365
- SharePoint
- Outlook sur le web
- Teams
- Centre d’administration SharePoint
- Centre d’administration Azure AD

Vous ne pouvez pas utiliser les applications et services suivants pour créer des groupes Office 365 avec les nouvelles étiquettes de sensibilité :

- Outlook pour Mac
- Outlook Mobile  
- Bureau Outlook pour Windows
- Formulaires  
- Dynamics 365  
- Yammer  
- Stream  
- Planificateur  
- Project  
- PowerBI  
- Centre d’administration teams  
- Centre d’administration Microsoft 365  
- Centre d’administration Exchange

## <a name="if-you-used-classic-azure-ad-site-classification"></a>Si vous avez utilisé une classification de site Azure AD classique

Office 365 ne prend plus en charge les anciennes classifications pour les nouveaux groupes et les sites SharePoint lorsque vous activez cet aperçu. Toutefois, les groupes et les sites existants affichent toujours les anciennes classifications, sauf si vous les convertissez. Les anciennes classifications incluent la classification de sites « modernes » que vous avez configurée, éventuellement via Azure AD PowerShell ou la bibliothèque principale PnP, qui `ClassificationList` a défini des valeurs pour le paramètre.

Par exemple, dans PowerShell :

```powershell
   ($setting["ClassificationList"])
```

Pour plus d’informations sur l’ancienne méthode de classification, voir la rubrique sur la [classification des sites SharePoint « moderne »](https://docs.microsoft.com/sharepoint/dev/solution-guidance/modern-experience-site-classification).

En fonction de votre déploiement actuel, vous disposez de deux options pour convertir vos anciennes classifications en nouvelles classifications.

### <a name="if-you-never-used-sensitivity-labels-unified-microsoft-information-protection-labels-for-files-and-email"></a>Si vous n’avez jamais utilisé les étiquettes de critère de diffusion (étiquettes de protection des informations Microsoft) pour les fichiers et le courrier électronique

Nous vous recommandons d'effectuer les actions suivantes :

1. Créez des étiquettes de sensibilité dans le centre de conformité Microsoft 365 portant le même nom que vos classifications existantes.
2. Utilisez PowerShell pour appliquer les nouvelles étiquettes aux groupes Office 365 existants et aux sites SharePoint à l’aide du mappage de nom.
3. Supprimez les anciennes classifications.

Les applications et les services qui prennent en charge les nouvelles étiquettes de sensibilité les affichent. Vous créez des équipes, des groupes et des sites avec les nouvelles étiquettes. Les utilisateurs peuvent toujours créer des groupes à partir d’applications et de services qui ne prennent pas en charge les nouvelles étiquettes. Toutefois, les utilisateurs ne peuvent pas appliquer une étiquette à ces groupes. Utilisez PowerShell pour appliquer les nouvelles étiquettes de sensibilité à ces groupes.

Vous pouvez conserver vos anciennes classifications ; Toutefois, nous vous recommandons vivement d’utiliser PowerShell pour appliquer les nouvelles étiquettes de sensibilité à ces groupes.

Les applications et les services qui prennent en charge les nouvelles étiquettes de sensibilité seront créés avec les nouvelles étiquettes. Lorsque les utilisateurs créent des groupes à partir d’applications et de services qui ne prennent pas en charge les nouvelles étiquettes, ils peuvent sélectionner une classification.

### <a name="if-you-use-sensitivity-labels-unified-microsoft-information-protection-labels-for-files-and-email"></a>Si vous utilisez des étiquettes de confidentialité (étiquettes de protection des informations Microsoft unifiées) pour les fichiers et le courrier électronique

Dès que vous activez cet aperçu, accédez à chaque étiquette dans le centre de conformité Microsoft 365 et appliquez les stratégies de votre choix pour les sites et les groupes. Les utilisateurs commencent à voir les étiquettes existantes disponibles pour les sites et les groupes.

### <a name="prepare-the-sharepoint-online-management-shell-before-you-relabel-office-365-groups"></a>Préparer SharePoint Online Management Shell avant de réattribuer un nouveau libellé aux groupes Office 365

Avant d’appliquer de nouvelles étiquettes, vérifiez que vous utilisez la dernière version de SharePoint Online Management Shell. Si vous disposez déjà de la dernière version, vous pouvez continuer et [attribuer un nouveau libellé aux groupes Office 365 avec de nouvelles étiquettes de confidentialité](#relabel-office-365-groups-with-new-sensitivity-labels).

Pour préparer SharePoint Online Management Shell pour l’aperçu :

1. Si vous avez installé une version antérieure de SharePoint Online Management Shell, accédez à **Ajouter ou supprimer des programmes** et désinstaller « SharePoint Online Management Shell ».

2. Dans un navigateur Web, accédez à la page du centre de téléchargement et [Téléchargez la dernière version de SharePoint Online Management Shell](https://go.microsoft.com/fwlink/p/?LinkId=255251).

3. Sélectionnez votre langue, puis cliquez sur **Télécharger**.

4. Choisissez entre le fichier x64 et x86. msi. Téléchargez le fichier x64 si vous exécutez la version 64 bits de Windows ou le fichier x86 si vous exécutez la version 32 bits. Si vous ne le Sachez pas, consultez [la version du système d’exploitation Windows que je suis en cours d’exécution ?](https://support.microsoft.com/help/13443/windows-which-operating-system).

5. Après avoir téléchargé le fichier, exécutez le fichier et suivez les étapes de l’Assistant d’installation.

### <a name="relabel-office-365-groups-with-new-sensitivity-labels"></a>Attribution d’un nouveau libellé aux groupes Office 365 avec de nouvelles étiquettes de sensibilité

1. Assurez-vous que vous utilisez la dernière version de SharePoint Online Management Shell. Pour obtenir des instructions, consultez [la rubrique prepare the SharePoint Online Management Shell avant de réattribuer un nouveau libellé aux groupes Office 365](#prepare-the-sharepoint-online-management-shell-before-you-relabel-office-365-groups).

2. À l’aide d’un compte professionnel ou scolaire disposant des privilèges d’administrateur général ou d’administrateur SharePoint dans Office 365, connectez-vous à SharePoint Online Management Shell. Pour savoir comment procéder, reportez-vous à l’article [Prise en main de SharePoint Online Management Shell](/powershell/sharepoint/sharepoint-online/connect-sharepoint-online).

3. Exécutez la commande suivante pour obtenir la liste des étiquettes de sensibilité et leurs GUID.

    ```PowerShell
    Set-ExecutionPolicy RemoteSigned
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid -Authentication Basic -AllowRedirection -Credential $UserCredential
    Import-PSSession $Session
    Get-Label |ft Name, Guid  
    ```

4. Notez le GUID de l’étiquette que vous souhaitez remplacer. Par exemple, l’étiquette « général ».

5. Utilisez la commande suivante pour obtenir la liste des groupes qui ont la classification « General ». Lorsque vous exécutez cette commande, vous vous connectez à Exchange Online PowerShell et exécutez la cmdlet Get-UnifiedGroup.

   ```PowerShell
   Set-ExecutionPolicy RemoteSigned
   $UserCredential = Get-Credential
   $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
   Import-PSSession $Session
   ```

6. Pour chaque groupe, ajoutez le GUID de l’étiquette de la nouvelle sensibilité.

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```
