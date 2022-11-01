---
title: Étape 4 de migration des données utilisateur entre locataires OneDrive
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
description: Étape 4 de la fonctionnalité de migration interlocataire OneDrive
ms.openlocfilehash: 107bb6e2b8ab08d871b0671491bc9098e02ed034
ms.sourcegitcommit: b386eaa33e1e5cdea59916247082b6e6e6a3d99e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68807736"
---
# <a name="step-4-pre-creating-users-and-groups"></a>Étape 4 : Précréer des utilisateurs et des groupes

Il s’agit de l’étape 4 d’une solution conçue pour effectuer une migration OneDrive interlocataire. Pour plus d’informations, consultez [Vue d’ensemble de la migration OneDrive interlocataire](cross-tenant-onedrive-migration.md).

- Étape 1 : [Se connecter à la source et aux locataires cibles](cross-tenant-onedrive-migration-step1.md)
- Étape 2 : [Établir une relation de confiance entre le locataire source et le locataire cible](cross-tenant-onedrive-migration-step2.md) 
- Étape 3 : [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md) 
- **Étape 4 : [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)**  
- Étape 5 : [Préparer le mappage d’identité](cross-tenant-onedrive-migration-step5.md)
- Étape 6 : [Démarrer une migration OneDrive interlocataire](cross-tenant-onedrive-migration-step6.md)
- Étape 7 : [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)


## <a name="identify-users-and-groups-to-be-migrated"></a>Identifier les utilisateurs et les groupes à migrer

Pour vous assurer que les autorisations OneDrive sont conservées dans le cadre de la migration, un fichier de mappage doit être créé pour aligner les utilisateurs du locataire source sur le locataire cible.

1. Identifiez la liste complète des sites OneDrive qui seront migrés de la source vers le locataire cible.
2. Préparez une liste complète des utilisateurs et des groupes qui seront migrés vers le locataire cible.

## <a name="pre-create-users-and-groups-on-the-target-tenant"></a>Précréer des utilisateurs et des groupes sur le locataire cible

1. Précréez des utilisateurs et des groupes en fonction des besoins dans l’annuaire du locataire cible.
2. Tous les utilisateurs dont les comptes OneDrive migrent vers le locataire cible doivent avoir de nouvelles identités d’utilisateur créées pour eux dans le locataire cible.
3. Tous les utilisateurs dont les comptes OneDrive migrent vers le locataire cible doivent se voir attribuer la licence OneDrive appropriée.
4. Tous les utilisateurs qui restent dans le locataire source mais qui ont besoin d’accéder aux ressources qui migrent vers le locataire cible doivent avoir de nouvelles identités invitées créées pour eux dans le locataire cible.
5. Les utilisateurs créés au préalable doivent être ajoutés en tant que membres de tous les groupes de sécurité ou groupes unifiés appropriés avant le début de la migration de OneDrive. 
6. Si le nom d’utilisateur ou de groupe existe déjà dans le locataire cible, créez un utilisateur ou un groupe avec un autre nom et notez-le pour l’étape suivante.
7. Nous vous recommandons de restreindre les créations de sites OneDrive dans le locataire cible pour empêcher les utilisateurs de créer des sites OneDrive.

>[!Note]
>Pour en savoir plus sur la restriction de la création de sites OneDrive, consultez [Désactiver la création OneDrive pour certains utilisateurs](/sharepoint/manage-user-profiles#disable-onedrive-creation-for-some-users)

## <a name="step-5-prepare-the-identity-mapping-file"></a>Étape 5 : [Préparer le fichier de mappage d’identité](cross-tenant-onedrive-migration-step5.md)