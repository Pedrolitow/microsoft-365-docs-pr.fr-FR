---
title: Étape 2 de migration des données utilisateur entre locataires OneDrive
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
description: Étape 2 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: 424636e01b89420979752c7c9b0e61d778319725
ms.sourcegitcommit: b386eaa33e1e5cdea59916247082b6e6e6a3d99e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68807626"
---
# <a name="step-2-establishing-trust-between-the-source-and-target-tenants"></a>Étape 2 : Établir l’approbation entre les locataires source et cible

Il s’agit de l’étape 2 d’une solution conçue pour effectuer une migration OneDrive interlocataire. Pour plus d’informations, consultez [Vue d’ensemble de la migration OneDrive interlocataire](cross-tenant-onedrive-migration.md).

- Étape 1 : [Se connecter à la source et aux locataires cibles](cross-tenant-onedrive-migration-step1.md)
- **Étape 2 : [Établir une relation de confiance entre le locataire source et le locataire cible](cross-tenant-onedrive-migration-step2.md)** 
- Étape 3 : [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md) 
- Étape 4 : [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)  
- Étape 5 : [Préparer le mappage d’identité](cross-tenant-onedrive-migration-step5.md)
- Étape 6 : [Démarrer une migration OneDrive interlocataire](cross-tenant-onedrive-migration-step6.md)
- Étape 7 : [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)

Après la connexion au locataire source et au locataire cible, l’étape suivante dans l’exécution d’une migration OneDrive interlocataire consiste à établir une relation de confiance entre les locataires.

Pour établir l’approbation, chaque administrateur de locataire SharePoint Online doit exécuter des commandes spécifiques sur les locataires source et cible. Une fois l’approbation demandée, l’administrateur du locataire cible reçoit un e-mail l’informant qu’un autre locataire tente d’établir une relation d’approbation.

>[!Note]
>La commande « trust » est spécifique à SharePoint Online. Il accorde uniquement l’autorisation à l’administrateur SharePoint sur le locataire source d’exécuter des opérations de migration OneDrive vers le locataire cible identifié. 
>
>*L’octroi d’une approbation ne donne à* l’administrateur aucune visibilité, autorisation ou possibilité de collaborer entre le locataire source et le locataire cible. 

>[!Important]
>Si vous êtes client Microsoft 365 Multi-Geo, vous devez établir une relation de confiance entre chaque zone géographique impliquée dans votre projet de migration.
>

## <a name="before-you-begin"></a>Avant de commencer

Avant d’exécuter les commandes d’approbation, obtenez les URL d’hôte interlocataire pour les locataires source et cible. Vous aurez besoin de ces URL lors de l’établissement de la relation d’approbation entre la source à la cible et la cible à source. 

**Pour obtenir les URL de l’hôte interlocataire :**

Sur les locataires source et cible, exécutez :

```powershell

Get-SPOCrossTenantHostURL
``` 

 
*Exemple:* Exécutez la commande sur le locataire source :

 :::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-hosturl-source.png" alt-text="exemple d’obtention de l’URL d’hôte pour la source":::

*Exemple:* Exécutez la commande sur le locataire cible :

:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-hosturl-target.png" alt-text="Exemple d’obtention de l’URL de l’hôte pour la cible":::
 


## <a name="run-the-trust-commands"></a>Exécuter les commandes d’approbation
Ces commandes envoient une requête au locataire avec lequel vous souhaitez établir une confiance.

1. Sur le locataire source, exécutez cette commande pour envoyer une demande d’approbation au locataire cible :

```powershell

Set-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>
 
``` 

</br>

2. Sur le locataire cible, exécutez cette commande pour envoyer une demande d’approbation au locataire source :

```powershell
Set-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Source -PartnerCrossTenantHostUrl <SOURCECrossTenantHostUrl>
```

 
### <a name="parameter-definitions"></a>Définitions de paramètres

|Paramètre|Définition|
|:-----|:-----|
|PartnerRole|Rôles du locataire partenaire avec lequel vous établissez la confiance.  Utilisez *source* si le locataire partenaire est la source des migrations OneDrive et *cible* si le locataire partenaire est la destination.
|PartnerCrossTenantHostURL|URL de l’hôte interlocataire du locataire partenaire. Le locataire partenaire peut le déterminer pour vous en exécutant *: Get-SPOCrossTenantHostURL* sur chacun des locataires.|

## <a name="sample-trust-email"></a>Exemple d’e-mail de confiance
Voici un exemple d’e-mail envoyé aux administrateurs généraux :


:::image type="content" source="../media/cross-tenant-migration/t2t-onedrive-trust-email.png" alt-text="exemple d’e-mail de confiance":::


**Objet:**  Locataire SPO [https://a830edad9050849mnaus093022-my.sharepoint.com/] [setuporupdate] Relation d’organisation [Scenario=MnA, Role=Source] avec nous

**Message:**  Locataire SPO [https://a830edad9050849mnaus093022-my.sharepoint.com/] [setuporupdate] Relation d’organisation [Scenario=MnA, Role=Source] avec nous


## <a name="step-3-verify-that-trust-has-been-established"></a>Étape 3 : [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md)