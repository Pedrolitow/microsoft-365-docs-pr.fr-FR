---
title: Utiliser des étiquettes de confidentialité avec Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint (préversion publique)
f1.keywords:
- NOCSH
ms.author: cabailey
author: cabailey
manager: laurawi
ms.date: ''
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
description: Utilisez les étiquettes de confidentialité pour protéger le contenu des sites SharePoint et Microsoft Teams, ainsi que des Groupes Microsoft 365.
ms.openlocfilehash: 8717f6dc9f86ed8d0d9bab378588d70e2854e8e7
ms.sourcegitcommit: 40ec697e27b6c9a78f2b679c6f5a8875dacde943
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/23/2020
ms.locfileid: "44352486"
---
# <a name="use-sensitivity-labels-to-protect-content-in-microsoft-teams-microsoft-365-groups-and-sharepoint-sites-public-preview"></a>Utiliser les étiquettes de confidentialité pour protéger le contenu dans Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint (préversion publique)

>*[Guide de sécurité et conformité pour les licences Microsoft 365](https://aka.ms/ComplianceSD).*

Lorsque vous créez des étiquettes de confidentialité dans le [Centre de conformité Microsoft 365](https://protection.office.com/), vous pouvez désormais les appliquer aux conteneurs suivants : les sites Microsoft Teams et SharePoint et les Groupes Microsoft 365 ([anciennement groupes Office 365](https://techcommunity.microsoft.com/t5/microsoft-365-blog/office-365-groups-will-become-microsoft-365-groups/ba-p/1303601)). Utilisez les paramètres d’étiquette suivants pour renforcer la protection du contenu de ces conteneurs :

- Confidentialité (privée ou publique) de sites d’équipes Microsoft 365 connectés au groupe
- Accès des utilisateurs externes
- Accès à partir d’appareils enregistrés 

Lorsque vous appliquez cette étiquette à l’un des conteneurs pris en charge, l’étiquette applique automatiquement les options configurées au site ou au groupe connecté. 

Le contenu de ces conteneurs n’hérite toutefois pas des étiquettes pour les paramètres tels que le nom d’étiquette, les marques visuelles ou le chiffrement. Pour que les utilisateurs puissent étiqueter leurs documents sur des sites SharePoint ou des sites d’équipe, [Activer les étiquettes de confidentialité pour les fichiers Office dans SharePoint et OneDrive](sensitivity-labels-sharepoint-onedrive-files.md).

## <a name="about-the-public-preview-for-microsoft-teams-microsoft-365-groups-and-sharepoint-sites"></a>À propos de la préversion publique Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint

Les étiquettes de confidentialité pour Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint sont en mode Aperçu et peuvent changer avant la publication finale. Cette préversion publique ne fonctionne pas avec les réseaux de distribution de contenu Office 365 (CDN).

Avant d’activer cette préversion et de configurer des étiquettes de confidentialité pour les nouveaux paramètres, les utilisateurs peuvent afficher et appliquer des étiquettes de confidentialité dans leurs applications. Par exemple, à partir de Word :

![Étiquette de confidentialité affichée dans l’application de bureau Word](../media/sensitivity-label-word.png)

Après avoir activé et configuré cette préversion, les utilisateurs peuvent également voir et appliquer des étiquettes de confidentialité à Microsoft Teams, à des groupes Microsoft 365 et à des sites SharePoint. Par exemple, lorsque vous créez un nouveau site d’équipe à partir de SharePoint :

![Étiquette de confidentialité lors de la création d’un site d’équipe à partir de SharePoint](../media/sensitivity-labels-new-team-site.png)

## <a name="enable-this-preview-and-synchronize-labels"></a>Activez cette préversion et synchronisez des étiquettes

1. Cette fonctionnalité utilisant une fonctionnalité Azure Active Directory, suivez les instructions de la documentation Azure Active Directory pour activer la préversion : [Attribuer des étiquettes de confidentialité à des Groupes Microsoft 365 dans Azure Active Directory (préversion)](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels).

2. [Connectez-vous au Centre de sécurité et conformité Office 365 PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell). 
    
    Par exemple, dans une session PowerShell exécutée en tant qu’administrateur, connectez-vous à l’aide d’un compte d’administrateur général :
    
    ```powershell
    Set-ExecutionPolicy RemoteSigned
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session -DisableNameChecking
    ```

3. Exécutez la commande suivante pour synchroniser vos étiquettes de confidentialité avec Azure AD afin de pouvoir les utiliser avec des groupes Microsoft 365 :
    
    ```powershell
    Execute-AzureAdLabelSync
    ```

## <a name="how-to-configure-site-and-group-settings-when-you-create-or-edit-sensitivity-labels"></a>Configuration de paramètres de site et de groupe lorsque vous créez ou modifiez des étiquettes de confidentialité

Vous êtes maintenant prêt à créer ou modifier les étiquettes de confidentialité que vous souhaitez rendre disponibles pour des sites et des groupes. L’activation de la préversion permet de rendre une nouvelle page visible dans les assistants d’étiquetage de confidentialité : **Paramètres de site et de groupe**

Si vous avez besoin d’aide pour créer ou modifier une étiquette de confidentialité, consultez les instructions sur la [Création et configuration d’étiquettes de confidentialité](create-sensitivity-labels.md#create-and-configure-sensitivity-labels).

Dans cette nouvelle page de **Paramètres de site et de groupe**, configurez les paramètres :

- **Confidentialité des sites d’équipe connectés aux groupes Office 365**: conserver la valeur par défaut de **Publique-tous les membres de l’organisation peuvent accéder au site** si vous souhaitez que tous les membres de votre organisation accèdent au site d’équipe ou au groupe auquel cette étiquette est appliquée.
    
    Sélectionnez **Privé** si vous voulez limiter l’accès aux seuls membres approuvés au sein de votre organisation.
    
    Sélectionnez **Aucune-laisser l’utilisateur choisir qui peut accéder au site** lorsque vous voulez protéger le contenu dans le conteneur à l’aide de l’étiquette de confidentialité, tout en laissant les utilisateurs configurer eux-mêmes le paramètre de confidentialité proprement dit.
    
    Les paramètres **Publique** ou **Privé** pour définir et verrouiller le paramètre de confidentialité lorsque vous appliquez cette étiquette au conteneur. Votre paramètre remplace le paramètre précédemment configuré pour l’équipe ou le groupe et verrouille la valeur de confidentialité afin qu’elle puisse être modifiée uniquement en supprimant d’abord l’étiquette de confidentialité du conteneur. Une fois l’étiquette de confidentialité supprimée, le paramètre de confidentialité de l’étiquette peut à nouveau être modifié par les utilisateurs.

- **Accès des utilisateurs externes** : déterminez si le propriétaire du groupe peut [ajouter des invités au groupe](/office365/admin/create-groups/manage-guest-access-in-groups).

- **Appareils non gérés** : pour les [appareils non gérés](/sharepoint/control-access-from-unmanaged-devices), autorisez l’accès total, l’accès web uniquement ou bloquer totalement l’accès. 

![L’onglet Paramètres de site et de groupe](../media/edit-sensitivity-label-site-group2.png)

> [!IMPORTANT]
> Seuls ces paramètres de sites et de groupes prennent effet lorsque vous appliquez une étiquette à une équipe, un groupe ou un site. D’autres paramètres d’étiquette, tels que le chiffrement et le marquage de contenu, ne sont pas appliqués au contenu au sein de l’équipe, du groupe ou du site.
> 
> Déploiement progressif sur les clients : seules les étiquettes concernant les paramètres de site et de groupe peuvent être sélectionnées lorsque les utilisateurs créent des équipes, des groupes et des sites. Si vous pouvez appliquer une étiquette à un conteneur alors que les paramètres de site et de groupe ne sont pas activés, seul le nom d’étiquette est appliqué au conteneur.

Si votre étiquette de confidentialité n’est pas encore publiée, publiez-la dès maintenant en [l’ajoutant à une stratégie d’étiquette de confidentialité](create-sensitivity-labels.md#publish-sensitivity-labels-by-creating-a-label-policy). Les utilisateurs auxquels sont assignés une stratégie d’étiquette de confidentialité incluant cette étiquette pourront la sélectionner pour des sites et des groupes.

À partir de la stratégie d’étiquette, seul le paramètre de stratégie **Appliquer cette étiquette par défaut aux documents et aux e-mails** s’applique lorsque vous appliquez cette étiquette à des conteneurs. Les autres paramètres de stratégie ne sont pas appliqués, notamment l’étiquetage obligatoire, la justification de l’utilisateur et le lien vers la page d’aide personnalisée.

## <a name="sensitivity-label-management"></a>Gestion des étiquettes de confidentialité

> [!WARNING]
> La création, la modification et la suppression des étiquettes de confidentialité utilisées pour Microsoft Teams, les groupes Microsoft 365 et les sites SharePoint nécessitent une coordination soigneuse avec les stratégies de publication des étiquettes pour les utilisateurs. 

Évitez les erreurs de création pour les sites et les groupes pouvant affecter tous les utilisateurs à l’aide des instructions suivantes.

**Création et publication d’étiquettes :**

Une fois que vous avez créé et publié une étiquette de confidentialité, il peut s’écouler jusqu’à 24 heures pour que l’étiquette devienne visible pour les utilisateurs d’équipes, de groupes et de sites. Pour publier une étiquette pour tous les utilisateurs du client, procédez comme suit :

1. Créez l’étiquette de confidentialité et publiez-la pour quelques comptes d’utilisateur dans le locataire.

2. Patientez 24 heures.

3. Une fois cette attente de 24 heures écoulée, utilisez l’un des comptes utilisateur que vous avez spécifié à l’étape 1 pour créer une équipe, un groupe Microsoft 365 ou un site SharePoint avec l’étiquette que vous avez créée à l’étape 1.

4. S’il n’y a pas d’erreur pendant l’opération de création à l’étape 3, publiez l’étiquette pour tous les utilisateurs de votre client. En cas d’erreur, contactez le [Support Microsoft](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).

**Modification et suppression des étiquettes publiées :**

Modifier ou supprimer une étiquette de confidentialité avec les paramètres de site et de groupe activés alors que cette étiquette est incluse dans d’autres stratégies d’étiquette, peut entraîner des échecs de création pour toutes les équipes, tous les groupes et tous les sites. Pour éviter cette situation, suivez les instructions suivantes :

1. Supprimez l’étiquette de confidentialité de toutes les stratégies d’étiquette qui incluent l’étiquette.

2. Patientez 48 heures.

3. Une fois les 48 heures écoulées, essayez de créer une équipe, un groupe ou un site et vérifiez que l’étiquette n’est plus visible.

4. Si l’étiquette de confidentialité n’est pas visible, vous pouvez désormais modifier ou supprimer l’étiquette en toute sécurité. Si l’étiquette est toujours visible, contactez le [Support Microsoft](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).

## <a name="assign-sensitivity-labels-to-microsoft-365-groups"></a>Attribuer des étiquettes de confidentialité à des groupes Microsoft 365

Vous êtes désormais prêt à appliquer une ou plusieurs étiquettes de confidentialité à des Groupes Microsoft 365. Revenez à la documentation Azure Active Directory pour les instructions suivantes :

- [Attribuer une étiquette à un nouveau groupe dans le Portail Azure](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-a-new-group-in-azure-portal)

-  [Attribuer une étiquette à un groupe existant dans le Portail Azure](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#assign-a-label-to-an-existing-group-in-azure-portal)

-  [Supprimer une étiquette dans un groupe existant dans le Portail Azure](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#remove-a-label-from-an-existing-group-in-azure-portal).

## <a name="apply-a-sensitivity-label-to-a-new-team"></a>Appliquez une étiquette de confidentialité à une nouvelle équipe

Les utilisateurs peuvent sélectionner des étiquettes de confidentialité lorsqu’ils créent des équipes dans Microsoft Teams. Lorsqu’ils sélectionnent l’étiquette dans la liste déroulante **Confidentialité**, le paramètre de confidentialité peut être modifié pour refléter la configuration de l’étiquette. Selon le paramètre d’accès pour les utilisateurs externes que vous avez sélectionné pour l’étiquette, les utilisateurs peuvent ajouter ou non des personnes extérieures à l’organisation.

[En savoir plus sur les étiquettes de niveau de confidentialité pour Teams](https://docs.microsoft.com/microsoftteams/sensitivity-labels)

![Le paramètre de confidentialité lors de la création d’une équipe](../media/privacy-setting-new-team.png)

Une fois l’équipe créée, l’étiquette de confidentialité s’affiche dans le coin supérieur droit de tous les canaux.

![L’étiquette de confidentialité apparaît sur l’équipe](../media/privacy-setting-teams.png)

Le service applique automatiquement la même étiquette de confidentialité au groupe Microsoft 365 et au site d’équipe SharePoint connecté.

## <a name="apply-a-sensitivity-label-to-a-new-group-in-outlook-on-the-web"></a>Appliquez une étiquette de confidentialité à un nouveau groupe dans Outlook sur le web

Dans Outlook sur le web, lorsque vous créez un groupe, vous pouvez sélectionner ou modifier l’option de **Confidentialité** pour les étiquettes publiées :

![Création d’un groupe et sélection d’une option sous Confidentialité](../media/sensitivity-label-new-group.png)

## <a name="apply-a-sensitivity-label-to-a-new-site"></a>Appliquez une étiquette de confidentialité à un nouveau site

Les administrateurs et les utilisateurs finaux peuvent sélectionner des étiquettes de confidentialité lorsqu’ils [créent des sites d’équipe et des sites de communication modernes](/sharepoint/create-site-collection), et développent les **Paramètres avancés** :

![Création d’un site et sélection d’une option sous Confidentialité](../media/sensitivity-label-new-communication-site.png)

La liste déroulante affiche les noms d’étiquette pour la sélection, et l’icône d’aide affiche tous les noms d’étiquette avec leur info-bulle, ce qui peut aider les utilisateurs à déterminer l’étiquette correcte à appliquer.

Lorsque l’étiquette est appliquée et que les utilisateurs accèdent au site, ils voient le nom de l’étiquette et les stratégies appliquées. Par exemple, ce site est étiqueté comme **confidentiel** et le paramètre de confidentialité est défini sur **privé** :

![Un site avec une étiquette de confidentialité appliquée](../media/sensitivity-label-site.png)

## <a name="view-sensitivity-labels-in-the-sharepoint-admin-center"></a>Afficher des étiquettes de confidentialité dans le Centre d’administration SharePoint

Pour afficher les étiquettes de confidentialité appliquées, utilisez la page **Sites actifs** dans le nouveau Centre d’administration SharePoint. Il se peut que vous deviez tout d’abord ajouter la colonne de **Confidentialité** :

![Colonne Confidentialité de la page Sites actifs](../media/manage-site-sensitivity-labels.png)

[EN savoir plus sur la gestion des sites dans le nouveau Centre d’administration SharePoint](/sharepoint/manage-sites-in-new-admin-center).

## <a name="change-site-and-group-settings-for-a-label"></a>Modifier les paramètres de site et de groupe pour une étiquette

Lorsque vous apportez des modifications aux paramètres de site et de groupe pour une étiquette, vous devez exécuter les commandes PowerShell suivantes pour que vos équipes, sites et groupes puissent employer les nouveaux paramètres. Nous vous conseillons de ne pas modifier les paramètres de site et de groupe pour une étiquette une fois que vous avez appliqué l’étiquette de confidentialité à plusieurs équipes, groupes ou sites.

1. Tout d’abord,[connectez-vous au Centre de sécurité et conformité Office 365 PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell). 
    
    Par exemple, dans une session PowerShell exécutée en tant qu’administrateur, connectez-vous à l’aide d’un compte d’administrateur général :
    
    ```powershell
    Set-ExecutionPolicy RemoteSigned
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session -DisableNameChecking
    ```

2. Obtenez la liste des étiquettes de confidentialité et leurs GUID à l’aide de l’applet de commande [Get-Label](https://docs.microsoft.com/powershell/module/exchange/get-label?view=exchange-ps) :
    
    ```powershell
    Get-Label |ft Name, Guid
    ```

3. Notez le GUID de l’étiquette ou des étiquettes que vous avez modifiées.

4. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).
    
    Par exemple :
    
    ```powershell
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session
    ```
    
5. Exécutez l’applet de commande [Get-UnifiedGroup](https://docs.microsoft.com/powershell/module/exchange/get-unifiedgroup?view=exchange-ps), en indiquant votre GUID d’étiquette à la place du GUID d’exemple de « e48058ea-98e8-4940-8db0-ba1310fd955e » : 
    
    ```powershell
    $Groups= Get-UnifiedGroup | Where {$_.SensitivityLabel  -eq "e48058ea-98e8-4940-8db0-ba1310fd955e"}
    ```

6. Réappliquez l’étiquette de confidentialité pour chaque groupe, en spécifiant le GUID de votre étiquette à la place du GUID de l’exemple de « e48058ea-98e8-4940-8db0-ba1310fd955e » :
    
    ```powershell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "e48058ea-98e8-4940-8db0-ba1310fd955e"}
    ```

## <a name="support-for-the-sensitivity-labels"></a>Prise en charge des étiquettes de confidentialité

Vous pouvez utiliser les étiquettes de confidentialité que vous avez configurées pour les paramètres de sites et de groupes avec les applications et services suivants :

- SharePoint Online
- Équipes
- Outlook sur le web
- Centre d’administration SharePoint
- Centre d’administration d’Azure AD

Les autres services et applications dans lesquels vous ne pouvez pas à ce jour utiliser les étiquettes de confidentialité configurées pour des paramètres de sites et de groupes sont les suivants :

- Outlook pour Mac
- Outlook Mobile
- Version de bureau d’Outlook pour Windows
- Formulaires
- Dynamics 365
- Yammer
- Flux
- Planificateur
- Project
- PowerBI
- Centre d’administration Microsoft Teams
- Centre d’administration Microsoft 365
- Centre d’administration Exchange


## <a name="classic-azure-ad-group-classification"></a>Classification classique de groupes Azure Active Directory

Microsoft 365 ne prend plus en charge les anciennes classifications pour les nouveaux Groupes Microsoft 365 et sites SharePoint lorsque vous activez cette préversion. Toutefois, les groupes et sites existants affichent encore les anciennes valeurs de classification, sauf si vous les convertissez pour utiliser des étiquettes de confidentialité.

Pour consulter un exemple de la manière dont vous avez peut-être utilisé l’ancienne classification de groupe pour SharePoint, consultez la page [Classification des sites SharePoint « modernes »](https://docs.microsoft.com/sharepoint/dev/solution-guidance/modern-experience-site-classification).

Ces classifications ont été configurées à l’aide d’Azure AD PowerShell ou de la bibliothèque principale PnP et par définition de valeurs pour le paramètre `ClassificationList`. Si votre client a défini des valeurs de classification, celles-ci s’affichent lorsque vous exécutez la commande suivante à partir du [module AzureADPreview PowerShell](https://www.powershellgallery.com/packages/AzureADPreview) :

```powershell
   ($setting["ClassificationList"])
```

Pour convertir vos anciennes classifications en étiquettes de confidentialité, réalisez l’une des opérations suivantes :

- Utiliser des étiquettes existantes : spécifiez les paramètres d’étiquette souhaités pour des sites et des groupes en modifiant les étiquettes de confidentialité de diffusion existantes déjà publiées.

- Créer des étiquettes : spécifiez les paramètres d’étiquette souhaités pour des sites et des groupes en créant et en publiant des étiquettes de confidentialité portant les mêmes noms que vos classifications existantes.

Ensuite : 

1. Utilisez PowerShell pour appliquer les étiquettes de confidentialité aux groupes et sites SharePoint Microsoft 365 existants à l’aide du mappage de noms. Pour connaître les instructions, reportez-vous à la section suivante.

2. Supprimez les anciennes classifications dans les groupes et sites existants.

Bien que vous ne puissiez pas empêcher les utilisateurs de créer des groupes dans les applications et les services qui ne prennent pas encore en charge les étiquettes de confidentialité, vous pouvez exécuter un script PowerShell récurrent recherchant les nouveaux groupes créés par des utilisateurs à l’aide des anciennes classifications et les convertir pour utiliser des étiquettes de confidentialité. 

#### <a name="use-powershell-to-convert-classifications-for-microsoft-365-groups-to-sensitivity-labels"></a>Utilisez PowerShell pour convertir des classifications de Groupes Microsoft 365 en étiquettes de confidentialité

1. Tout d’abord,[connectez-vous au Centre de sécurité et conformité Office 365 PowerShell](/powershell/exchange/office-365-scc/connect-to-scc-powershell/connect-to-scc-powershell). 
    
    Par exemple, dans une session PowerShell exécutée en tant qu’administrateur, connectez-vous à l’aide d’un compte d’administrateur général :
    
    ```powershell
    Set-ExecutionPolicy RemoteSigned
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://ps.compliance.protection.outlook.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session -DisableNameChecking
    ```

2. Obtenez la liste des étiquettes de confidentialité et leurs GUID à l’aide de l’applet de commande [Get-Label](https://docs.microsoft.com/powershell/module/exchange/get-label?view=exchange-ps) :
    
    ```powershell
    Get-Label |ft Name, Guid
    ```

3. Notez les GUID des étiquettes de confidentialité que vous voulez appliquer à vos Groupes Microsoft 365.

4. [Connectez-vous à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell?view=exchange-ps).
    
    Par exemple :
    
    ```powershell
    $UserCredential = Get-Credential
    $Session = New-PSSession -ConfigurationName Microsoft.Exchange -ConnectionUri https://outlook.office365.com/powershell-liveid/ -Credential $UserCredential -Authentication Basic -AllowRedirection
    Import-PSSession $Session
    ```

5. Utilisez la commande suivante en tant qu’exemple pour obtenir la liste des groupes qui ont actuellement la classification « Général » :

   ```PowerShell
   $Groups= Get-UnifiedGroup | Where {$_.classification -eq "General"}
   ```

6. Pour chaque groupe, ajoutez le nouveau GUID de l’étiquette de confidentialité. Par exemple :

    ```PowerShell
    foreach ($g in $groups)
    {Set-UnifiedGroup -Identity $g.Identity -SensitivityLabelId "457fa763-7c59-461c-b402-ad1ac6b703cc"}
    ```

7. Répétez les étapes 5 et 6 pour les classifications de groupe restantes.

## <a name="auditing-sensitivity-label-activities"></a>Audit sur les activités des étiquettes de confidentialité

Si un utilisateur télécharge un document sur un site protégé par une étiquette de confidentialité et son document comporte une étiquette de confidentialité [plus élevée](sensitivity-labels.md#label-priority-order-matters) que celle du site, cette action n’est pas bloquée. Par exemple, vous avez appliqué l’étiquette **Général** à un site SharePoint, et une personne télécharge un document étiqueté comme **Confidentiel**. Une étiquette de confidentialité ayant une priorité plus élevée identifie un contenu plus sensible qu’un contenu présentant un ordre de priorité plus faible, cette situation peut devenir un problème de sécurité.

Bien que l’action ne soit pas bloquée, elle est auditée et génère automatiquement un courrier électronique à la personne qui a chargé le document et à l’administrateur du site. Par conséquent, l’utilisateur et les administrateurs peuvent identifier les documents comportant un mauvais alignement de la priorité d’étiquette et prendre des mesures, le cas échéant. Par exemple, supprimer ou déplacer le document téléchargé à partir du site. 

Il ne s’agit pas d’un problème de sécurité si le document comprend une étiquette de confidentialité de priorité inférieure à celle appliquée sur le site. Par exemple, un document marqué **Général** est téléchargé sur un site intitulé **Confidentiel**. Dans ce scénario, l’événement d’audit et l’e-mail ne sont pas générés.

Pour rechercher le journal d’audit pour cet événement, recherchez **Correspondance incorrecte des documents détectés** dans la catégorie **Activités de fichiers et de pages**. 

Le message électronique généré automatiquement a l’objet **Étiquette de confidentialité incompatible détectée** et que le courrier électronique décrit l’incompatibilité entre les étiquettes avec un lien vers le document et le site téléchargés. Il contient également un lien vers la documentation expliquant comment les utilisateurs peuvent modifier l’étiquette de confidentialité. Pour le moment, ces messages automatisés ne peuvent pas être désactivés ou personnalisés.

Lorsque quelqu’une personne ajoute ou supprime une étiquette de sensibilité sur ou à partir d’un site ou d’un groupe, ces activités sont également auditées, mais l’e-mail n’est pas généré automatiquement. 

Ces événements d’audit peuvent être consultés dans la catégorie [Activités des d’étiquette de confidentialité](search-the-audit-log-in-security-and-compliance.md#sensitivity-label-activities). Pour obtenir des instructions sur les recherches dans un journal d’audit, consultez [Effectuer des recherches dans le journal d’audit du Centre de sécurité et conformité](search-the-audit-log-in-security-and-compliance.md).

## <a name="troubleshoot-sensitivity-label-deployment"></a>Résoudre les problèmes de déploiement des étiquettes de confidentialité

Vous avez des problèmes avec des étiquettes de confidentialité pour Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint ? Vérifiez les éléments suivants :

### <a name="labels-not-visible-after-publishing"></a>Étiquettes non visibles après la publication
Si vous rencontrez des problèmes lors de la création d’un site ou d’un groupe Microsoft 365 après avoir activé ces paramètres ou modifié la description de l’étiquette de confidentialité, patientez quelques heures après avoir enregistré les modifications, puis essayez à nouveau de créer l’équipe ou le groupe. Si vous souhaitez en savoir plus, consultez [Planifier le déploiement après avoir créé ou modifié une étiquette de confidentialité](sensitivity-labels-sharepoint-onedrive-files.md#schedule-roll-out-after-you-create-or-change-a-sensitivity-label).

Si vous ne parvenez toujours pas à voir la nouvelle étiquette de confidentialité depuis SharePoint Online, contactez le [Support Microsoft](https://docs.microsoft.com/office365/admin/contact-support-for-business-products).

### <a name="team-group-or-sharepoint-site-creation-errors"></a>Erreurs de création d’équipe, de groupe ou de site SharePoint
Si vous rencontrez des erreurs de création lors de préversion publique, vous pouvez désactiver les étiquettes de confidentialité pour les Microsoft Teams, les Groupes Microsoft 365 et les sites SharePoint en utilisant les instructions suivante : [Activer la prise en charge des étiquettes de confidentialité dans PowerShell](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-assign-sensitivity-labels#enable-sensitivity-label-support-in-powershell). Toutefois, pour désactiver la préversion, à l’étape 5, désactivez la fonctionnalité à l’aide de `$setting["EnableMIPLabels"] = "False"`.

## <a name="additional-resources"></a>Ressources supplémentaires

Regardez l’enregistrement du webinaire et les questions traitées pour [Utilisation d’étiquettes de confidentialité avec Microsoft Teams, les groupes Office 365 et les sites SharePoint Online](https://techcommunity.microsoft.com/t5/security-privacy-and-compliance/using-sensitivity-labels-with-microsoft-teams-o365-groups-and/ba-p/1221885#M1380).

