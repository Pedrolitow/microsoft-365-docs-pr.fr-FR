---
title: Étape 7 de migration des données utilisateur entre locataires OneDrive
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
description: Étape 7 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: acd9130b6058ef0dceae0dcc8c6e60699a4fd39e
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805364"
---
# <a name="step-7--post-migration-steps"></a>Étape 7 : Étapes post-migration

## <a name="removing-trust-relationship"></a>Suppression d’une relation d’approbation

>[!Important]
>Veillez à supprimer la relation d’approbation sur les locataires source et cible avant l’expiration de vos licences de locataire source. Une fois les licences expirées, la commande de suppression d’approbation ne fonctionne pas sur la source.

1. Sur le locataire source, exécutez cette commande pour supprimer la relation d’approbation entre le locataire source et le locataire cible.

```powershell
Remove-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>

```
</br>

2. Sur le locataire cible, exécutez cette commande pour supprimer la relation d’approbation entre le locataire cible et le locataire source.

```powershell

Remove-SPOCrossTenantRelationship -Scenario MnA -PartnerRole Target -PartnerCrossTenantHostUrl <TARGETCrossTenantHostUrl>

```


### <a name="parameter-definitions"></a>Définitions de paramètres

|Paramètre|Définition|
|:-----|:-----|
|PartnerRole|Rôles du locataire partenaire avec lequel vous établissez la confiance.  Utilisez *source* si le locataire partenaire est la source des migrations OneDrive, et *cible* si le locataire partenaire est la destination.
|PartnerCrossTenantHostURL|URL de l’hôte interlocataire du locataire partenaire.  Le locataire partenaire peut le déterminer pour vous en exécutant *: Get-SPOCrossTenantHostURL* sur chacun des locataires.|


## <a name="other-post-migration-steps"></a>Autres étapes post-migration

Une fois la migration terminée, les utilisateurs OneDrive doivent se connecter à l’aide de leur nouvelle identité et resynchroniser leurs fichiers sur leurs appareils sur le locataire cible.

### <a name="onedrive-for-business"></a>OneDrive Entreprise
Avec leurs nouvelles informations d’identification, les utilisateurs doivent se connecter à OneDrive à l’aide du lanceur d’applications Microsoft 365 ou d’un navigateur web.

### <a name="permissions-on-onedrive-content"></a>Autorisations sur le contenu OneDrive
Les utilisateurs disposant de l’autorisation d’accéder au contenu OneDrive continueront d’y accéder, à condition qu’ils aient été inclus dans le fichier de mappage d’identité

### <a name="onedrive-sync-client"></a>Client de synchronisation OneDrive
L’utilisateur doit se connecter au **client de synchronisation OneDrive** et à son nouvel emplacement OneDrive à l’aide de sa nouvelle identité. Une fois cette étape terminée, les fichiers et dossiers commencent à se resynchroniser sur l’appareil.

### <a name="sharing-links"></a>Liens de partage
Les liens partagés existants pour les fichiers migrés sont automatiquement redirigés vers le nouvel emplacement cible.
