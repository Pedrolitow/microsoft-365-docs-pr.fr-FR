---
title: Migration OneDrive interlocataire
ms.author: jhendr
author: JoanneHendrickson
manager: serdars
recommendations: true
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- SPMigration
- M365-collaboration
- m365initiative-migratetom365
search.appverid: MET150
description: Migration OneDrive interlocataire
ms.openlocfilehash: 0088e7088dd67fd3a4d189eacdacde5362d0ff73
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68814096"
---
# <a name="cross-tenant-onedrive-migration"></a>Migration OneDrive interlocataire

>[!Note]
> Les informations contenues dans cet article font référence à **la migration OneDrive interlocataire**. Pour la migration de boîtes aux lettres, consultez [Migration de boîtes aux lettres entre locataires](/microsoft-365/enterprise/cross-tenant-mailbox-migration).

## <a name="overview"></a>Vue d’ensemble

Pendant les fusions ou les cessions, vous avez généralement besoin de la possibilité de déplacer des comptes OneDrive d’utilisateurs vers un nouveau locataire Microsoft 365. Avec la migration OneDrive interlocataire, les administrateurs de locataires peuvent utiliser des outils familiers tels que *SharePoint Online PowerShell* pour effectuer la transition des utilisateurs vers leur nouvelle organisation.

Les administrateurs SharePoint de deux locataires distincts peuvent utiliser l’applet *de commande Set-SPOCrossTenantRelationship* pour établir une relation d’organisation, et la commande *Start-SPOCrossTenantUserContentMove* pour commencer les déplacements OneDrive interlocataires.

Jusqu’à 4 000 comptes OneDrive peuvent être planifiés pour la migration à l’avance à un moment donné. Une fois planifiées, les migrations se produisent sans que les données de l’utilisateur ne quittent jamais le cloud Microsoft 365 et avec une interruption minimale, ne nécessitant que quelques minutes où oneDrive d’un utilisateur sera en lecture seule. Une fois les migrations terminées, une redirection est placée à l’emplacement du OneDrive d’origine de l’utilisateur, de sorte que tous les liens vers des fichiers et des dossiers peuvent continuer à fonctionner dans le nouvel emplacement. 

Cette fonctionnalité n’est pas prise en charge pour les utilisateurs du cloud public, notamment GCC, Consumer, GCC de haut niveau ou DoD.

## <a name="licensing"></a>Licences

**La migration des données utilisateur interlocataires** est disponible en tant que module complémentaire aux plans d’abonnement Microsoft 365 suivants pour les clients Accord Entreprise. Les licences utilisateur sont par migration (frais ponctuels). Pour plus d’informations, contactez l’équipe de votre compte Microsoft.
 
Microsoft 365 Business Basic/Business Standard/Business Premium/F1/F3/E3/A3/E5/A5; Office 365 F3/E1/A1/E3/A3/E5/A5; Exchange Online; SharePoint Online; OneDrive Entreprise.


## <a name="prerequisites-and-settings"></a>Composants requis et paramètres

- **Microsoft Office SharePoint Online PowerShell**. Vérifiez que la version la plus récente est installée. [Télécharger SharePoint Online Management Shell à partir du Centre de téléchargement Microsoft officiel](/download/details.aspx?id=35588)

- **Désactivez le chiffrement du service avec la clé client activée.** Vérifiez que le chiffrement du service **n’est pas** activé pour le locataire OneDrive source avec la clé client Microsoft Purview activée. Si cette option est activée sur le locataire source, la migration échoue. [En savoir plus sur le chiffrement de service avec la clé client Microsoft Purview](/microsoft-365/compliance/customer-key-overview)

- Les comptes OneDrive sources doivent être définis sur Lecture/Écriture. S’il est défini sur Lecture seule, ils échouent.

## <a name="pre-create-target-accounts"></a>Précréer des comptes cibles

- Vérifiez que tous les utilisateurs et groupes identifiés pour la migration ont été précréé sur le locataire cible.
- Attribuez les licences appropriées à chaque utilisateur sur le locataire cible.
- Nous vous recommandons de restreindre la création de sites OneDrive dans le locataire cible pour empêcher les utilisateurs de créer des sites OneDrive. Si un site OneDrive existe déjà pour l’utilisateur sur le locataire cible, la migration échoue.  Vous ne pouvez pas remplacer un site existant.

>[!Note]
>Pour en savoir plus sur la restriction de la création de sites OneDrive, consultez [Désactiver la création de OneDrive pour certains utilisateurs](/sharepoint/manage-user-profiles#disable-onedrive-creation-for-some-users)


## <a name="path-size-limits"></a>Limites de taille de chemin d’accès

Microsoft limite le nombre de caractères dans un chemin à ne pas dépasser 400 caractères. Il s’agit de la limite complète du chemin d’accès, pas seulement du nom de fichier. Lors de la planification de vos migrations, passez en revue la longueur des noms d’URL OneDrive dans votre locataire cible. L’échec se produit souvent lorsque les fichiers ou les chemins d’accès aux dossiers de la source, combinés avec l’URL OneDrive sur la cible, dépassent la limite de 400 caractères. 

Une migration détecte si vous avez dépassé la limite de caractères. Collaborez avec le propriétaire du site pour mettre à jour la structure de répertoires de fichiers/dossiers afin de réduire la longueur des chemins d’accès aux fichiers.

Toute URL légale est acceptée lors de la création de votre mappage d’identité de la source vers la cible pour vos migrations. À l’heure actuelle, les noms d’utilisateur/URL qui contiennent un caractère d’apostrophe ( **'** ) dans un nom d’utilisateur/URL échouent avec une erreur « caractère non valide » lors de la tentative de migration.

>[!Tip]
>Nous vous recommandons de garder les noms d’URL OneDrive cibles courts pour éviter de dépasser la limite de caractères.

## <a name="onedrive-account-size-limits"></a>Limites de taille de compte OneDrive
Chaque compte OneDrive peut avoir un maximum de 2 To de contenu ou 1 million d’éléments.


## <a name="permissions"></a>Autorisations

Tous les utilisateurs et groupes inclus dans le fichier de mappage d’identité que vous avez chargé sur le locataire cible conservent les autorisations dans le locataire cible liées au site OneDrive migré.

## <a name="legal-holds"></a>Conservations légales
Les comptes OneDrive avec une stratégie de conservation appliquée seront bloqués lors de la migration.
Pour migrer ces comptes OneDrive, supprimez la stratégie de conservation, migrez, puis réappliquez la conservation si nécessaire sur le locataire cible.

## <a name="shared-files"></a>Fichiers partagés

Une fois qu’un compte OneDrive a été migré, toute personne qui clique sur un lien partagé vers l’ancien emplacement est redirigée vers le nouvel emplacement, à condition qu’elle ait toujours accès à la destination. 

Ces redirections restent jusqu’à ce que le locataire source soit déprovisionné. L’administrateur peut également supprimer de manière sélective les redirections site par site.

## <a name="how-does-it-work"></a>Comment cela fonctionne-t-il ?

- **Étape 1 :** [Se connecter à la source et aux locataires cibles](cross-tenant-onedrive-migration-step1.md).  
- **Étape 2 :** [Établir une relation de confiance entre le locataire source et le locataire cible](cross-tenant-onedrive-migration-step2.md) 
- **Étape 3 :** [Vérifier que l’approbation a été établie](cross-tenant-onedrive-migration-step3.md) 
- **Étape 4 :** [Précréer des utilisateurs et des groupes](cross-tenant-onedrive-migration-step4.md)  
- **Étape 5 :** [Préparer le mappage d’identité](cross-tenant-onedrive-migration-step5.md)
- **Étape 6 :** [Démarrer une migration OneDrive interlocataire](cross-tenant-onedrive-migration-step6.md)
- **Étape 7 :** [Étapes post-migration](cross-tenant-onedrive-migration-step7.md)

## <a name="step-1-connect-to-source-and-target-tenants"></a>Étape 1 : [Se connecter aux locataires source et cible](cross-tenant-onedrive-migration-step1.md)