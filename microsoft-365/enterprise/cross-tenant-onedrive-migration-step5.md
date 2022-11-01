---
title: Étape 5 de migration des données utilisateur entre locataires OneDrive
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
recommendations: true
audience: ITPro
ms.topic: article
ms.service: sharepoint-online
ms.subservice: sharepoint-migration
ms.localizationpriority: high
ms.collection:
- SPMigration
- M365-collaboration
- m365initiative-migratetom365
search.appverid: MET150
description: Étape 5 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: 5e8706b88b255132bb4db36cd6010668b36b3f26
ms.sourcegitcommit: b386eaa33e1e5cdea59916247082b6e6e6a3d99e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68807670"
---
# <a name="step-5-identity-mapping"></a>Étape 5 : Mappage d’identité

Il s’agit de l’étape 5 d’une solution conçue pour effectuer une migration OneDrive interlocataire. Pour plus d’informations, consultez [Vue d’ensemble de la migration OneDrive interlocataire](cross-tenant-onedrive-migration.md).

- Étape 1 : [Se connecter à la source et aux locataires cibles](cross-tenant-onedrive-migration-step1.md)
- Étape 2 : [Établir une relation de confiance entre le locataire source et le locataire cible](cross-tenant-onedrive-migration-step2.md) 
- Étape 3 : [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md) 
- Étape 4 : [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)  
- **Étape 5 : [Préparer le mappage d’identité](cross-tenant-onedrive-migration-step5.md)**
- Étape 6 : [Démarrer une migration OneDrive interlocataire](cross-tenant-onedrive-migration-step6.md)
- Étape 7 : [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)

## <a name="create-the-identity-mapping-file"></a>Créer le fichier de mappage d’identité 

Dans cette étape du processus de migration entre locataires, vous allez créer un seul fichier CSV (valeurs séparées par des virgules) qui contient le mappage des utilisateurs et des groupes sur le locataire source à leurs utilisateurs et groupes correspondants sur le locataire cible.

Nous vous recommandons de prendre le temps de vérifier vos mappages, en vous assurant qu’ils sont exacts avant de commencer les migrations vers le locataire cible.

Il existe une relation un-à-un dans le fichier de mappage d’identité.  Vous ne pouvez pas mapper le même utilisateur à plusieurs utilisateurs dans le locataire cible. Par exemple, si vous avez des instances où l’administrateur est le propriétaire de plusieurs comptes OneDrive, la propriété doit être modifiée pour correspondre à l’utilisateur correspondant que vous souhaitez migrer de source vers cible.  Si ce n’est pas le cas, ces fichiers de compte ne seront pas migrés.

**Exemple:** Dans cet exemple, l’administrateur possède plusieurs comptes OneDrive.

|Propriétaire du locataire source |Utilisateur du locataire cible|
|:-----|:-----|
|admin@source.com  |new.userA@target.com|
|admin@source.com |new.userB@target.com|
|admin@source.com |new.userC@target.com|


La migration interlocataire prend en charge ce scénario :

**Exemple**

|Propriétaire du locataire source|Utilisateur du locataire cible|
|:-----|:-----|
|userA@source.com|new.userA@target.com|
|userB@source.com|new.userB@target.com|
|userC@source.com|new.userC@target.com|


### <a name="create-the-csv-file"></a>Créer le fichier CSV

Six colonnes sont nécessaires dans votre fichier CSV. Les trois premières sont vos valeurs sources, chacune fournissant des détails sur l’emplacement actuel de vos données. Les trois colonnes restantes sont les informations correspondantes sur le locataire cible. Les six colonnes doivent être prises en compte dans le fichier. Créez votre fichier dans Excel et enregistrez-le en tant que fichier .csv. 

Les utilisateurs et les groupes sont inclus dans le même fichier. Selon qu’il s’agit d’un utilisateur ou d’un groupe, ce que vous entrez dans la colonne est différent. Dans chacune des colonnes, entrez des valeurs comme indiqué dans les exemples.  **N’incluez PAS d’en-têtes de colonne.**

|Column|Utilisateur|Group|
|:-----|:-----|:-----|
|1|Utilisateur|Group|
|2|SourceTenantCompanyID|SourceTenantCompanyID|
|3|SourceUserUpn|SourceGroupObjectID|
|4|TargetUserUpn|TargetGroupObjectID|
|5|TargetUserEmail|GroupName|
|6|UserType|GroupType|


>[!Important]
>N’incluez PAS d’en-têtes de colonne dans votre fichier CSV.  Dans les exemples ci-dessous, nous les incluons à titre indicatif uniquement. 

**Utilisateurs**. Entrez vos valeurs comme indiqué dans cet exemple pour les invités :

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-csv-mapping-users-columns.png" alt-text="format à utiliser pour le mappage des utilisateurs":::

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-csv-mapping-users-example.png" alt-text="exemple de fichier csv pour les utilisateurs":::

**Groupes**. Entrez vos valeurs comme indiqué dans cet exemple pour les invités :
</br>
:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-csv-mapping-groups-columns.png" alt-text="format du fichier CSV pour les groupes":::
</br>

*Exemple* :

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-csv-group-example.png" alt-text="Exemple d’ajout de groupes au fichier CSV":::


**Utilisateurs invités**. Vous pouvez mapper des comptes invités dans le locataire source aux comptes de membre dans le locataire cible. Vous pouvez également mapper un compte invité dans la source à un compte invité dans la cible si l’invité a été créé précédemment. Entrez vos valeurs comme indiqué dans cet exemple pour les invités :
</br>

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-csv-mapping-users-guests.png" alt-text="Exemple csv lors du mappage d’un invité à un membre":::

*Exemple de plusieurs utilisateurs dans un fichier CSV :* </br>

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-migration-csv-users-groups.png" alt-text="exemple d’utilisateurs et de groupes dans un fichier de mappage":::

## <a name="obtain-the-source-tenant-company-id"></a>Obtenir l’ID d’entreprise du locataire source
Pour obtenir l’ID de société du locataire source :

1. Connectez-vous en tant que Administration à votre [Portail Azure](https://ms.portal.azure.com/)
2. Sélectionnez ou recherchez **Azure Active Directory**.
3. Faites défiler vers le bas dans le volet gauche, puis sélectionnez **Propriétés**.
4. Recherchez le **champ ID de locataire**. L’ID de locataire requis se trouve dans cette zone.

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-azure-tenant-id.png" alt-text="obtention de l’ID de locataire source":::



## <a name="to-obtain-source-group-object-id"></a>Pour obtenir l’ID d’objet du groupe source :

1. Connectez-vous au locataire source en tant que Administration aux [groupes Azure](https://ms.portal.azure.com).
2. Recherchez le ou les groupes requis.
3. Sélectionnez l’instance de groupe requise, puis **Copier dans le Presse-papiers**.  Collez cette valeur dans la colonne sourceGroupObjectId de votre fichier CSV de mappage.
4. Si vous avez plusieurs groupes à mapper, répétez ces étapes pour chaque groupe.

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-source-group-objectid.png" alt-text="obtention de l’ID d’objet du groupe source":::

### <a name="to-obtain-target-group-object-id"></a>Pour obtenir l’ID d’objet du groupe cible :

1. Connectez-vous au locataire cible en tant que Administration aux [groupes Azure](https://ms.portal.azure.com)
2. Recherchez le ou les groupes requis.
3. Sélectionnez l’instance de groupe requise, puis **Copier dans le Presse-papiers**. Collez cette valeur dans la colonne targetGroupObjectId de votre fichier CSV de mappage.
4. Si vous avez plusieurs groupes à mapper, répétez la procédure ci-dessus pour obtenir ces targetGroupObjectId spécifiques.
5. Pour groupName, utilisez le même ID que le *TargetGroupObjectId* que vous avez obtenu.
 
:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-target-group-objectid.png" alt-text="comment obtenir l’ID d’objet cible":::

## <a name="upload-the-identity-map"></a>Charger la carte d’identité

Une fois le fichier de mappage d’identité préparé, l’administrateur SharePoint sur le locataire cible charge le fichier dans SharePoint. Cela permet au mappage d’identité de se produire automatiquement dans le cadre de la migration entre locataires.

>[!Important]
>Avant d’exécuter la commande *Add-SPOTenantIdentityMap –IdentityMapPath* , enregistrez et fermez le fichier identitymap.csv sur votre bureau/OneDrive/SharePoint. Si le fichier reste ouvert, vous recevez l’erreur suivante.
>
>*Add-SPOTenantIdentityMap : le processus ne peut pas accéder au fichier « C:\Users\myuser\Test-Identity-Map.csv », car il est utilisé par un autre processus.*


1. Pour charger la carte d’identité sur le locataire cible, exécutez la commande suivante.  Pour *-IdentityMapPath*, fournissez le chemin complet et le nom de fichier du fichier CSV de mappage d’identité.


```powershell
Add-SPOTenantIdentityMap –IdentityMapPath <identitymap.csv>  

```



>[!Important]
>Si vous apportez ou avez besoin d’apporter des modifications à votre carte d’identité pendant le cycle de vie de la migration, vous devez exécuter la commande *Add-SPOTenantIdentityMap –IdentityMapPath <identitymap.csv>* **chaque fois** qu’une modification est apportée pour vous assurer que ces modifications sont appliquées à la migration.

Le chargement d’une nouvelle carte d’identité remplacera la carte actuelle. Assurez-vous que toute révision ou ajout inclut TOUS les utilisateurs et groupes pour la migration complète. Votre carte d’identité doit toujours inclure toutes les personnes que vous souhaitez migrer.

Pour examiner les entrées de mappage dans le fichier de mappage d’identité pour un utilisateur particulier, utilisez la commande *Get-SPOTenantIdentityMappingUser* avec Field comme *SourceUserKey* et Value comme UPN de l’utilisateur que vous déplacez. 

**Exemple :**

```powershell

get-spoTenantIdentityMappingUser -Field SourceUserKey -Value usera@Contoso.onmicrosoft.com 
```

## <a name="verify-cross-tenant-compatibility-status"></a>Vérifier l’état de compatibilité entre locataires

Avant de commencer des migrations interlocataires, assurez-vous que les deux schémas de base de données SharePoint sont à jour et compatibles entre la source et la cible.

Pour effectuer cette vérification, exécutez l’applet de commande ci-dessous sur votre locataire source.

```Powershell

Get-SPOCrossTenantCompatibilityStatus –PartnerCrossTenantHostURL [Target tenant hostname]

Get-SPOCrossTenantCompatibilityStatus –PartnerCrossTenantHostURL https://m365x12395529-my.sharepoint.com
```

- Si les locataires sont compatibles, vous pouvez passer à l’étape suivante du démarrage des migrations interlocataires.  
- Si les locataires ne sont pas compatibles, vos locataires doivent être corrigés/mis à jour pour garantir la compatibilité.

>[!Note]
>Nous vous recommandons d’attendre une période de 24 heures. Si vos locataires sont toujours signalés comme *incompatibles*, contactez le support. 

>[!Note]
>Nous vous recommandons d’effectuer la vérification de l’état de compatibilité fréquemment et avant de démarrer n’importe quelle instance de migrations entre locataires. Si les locataires ne sont pas compatibles, cela peut entraîner l’échec des migrations entre locataires.


## <a name="step-6-start-a-onedrive-cross-tenant-migration"></a>Étape 6 : [Démarrer une migration interlocataire OneDrive](cross-tenant-onedrive-migration-step6.md)