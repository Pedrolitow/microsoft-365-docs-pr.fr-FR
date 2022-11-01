---
title: Data Residency pour SharePoint Online et OneDrive Entreprise
description: Data Residency pour SharePoint Online et OneDrive Entreprise
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.service: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.date: ''
ms.reviewer: dmwmsft
ms.custom:
- it-pro
ms.collection:
- M365-subscription-management
ms.openlocfilehash: b2ffb535ae34a2d5af836c14cd88dd295d7d574f
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68805421"
---
# <a name="data-residency-for-sharepoint-online-and-onedrive-for-business"></a>Data Residency pour SharePoint Online et OneDrive Entreprise

## <a name="data-residency-commitments-available"></a>**Data Residency engagements disponibles**

### <a name="product-terms"></a>Conditions du produit

Conditions requises :

- _Le locataire_ dispose d’un pays d’inscription inclus dans _la zone géographique de la région_ locale, l’Union européenne ou le États-Unis.

**Engagement:**

_Pour connaître la langue actuelle, reportez-vous aux Conditions relatives au [produit de confidentialité et de sécurité](https://www.microsoft.com/licensing/terms/product/PrivacyandSecurityTerms/all) et consultez la section intitulée « Emplacement des données client au repos pour les principaux services en ligne »._

### <a name="advanced-data-residency-add-on"></a>Module complémentaire Data Residency avancé

Conditions requises :

1. _Le client_ a un pays d’inscription inclus dans _Région locale Geography_ ou _Expanded Local Region Geography_.
1. _Le locataire_ dispose d’un abonnement advanced Data Residency valide pour tous les utilisateurs du _locataire_.
1. Les données client de l’abonnement SharePoint Online sont approvisionnées dans _Région locale Geography_ ou _Expanded Local Region Geography_.

**Engagement:**

Reportez-vous à la [page Engagement ADR](m365-dr-commitments.md#sharepoint-onlineonedrive-for-business) pour connaître l’engagement spécifique des données client au repos pour SharePoint Online et OneDrive Entreprise.

### <a name="multi-geo-add-on"></a>Module complémentaire multigéographique

Conditions requises :

1. _Les locataires_ disposent d’un abonnement multigéographique valide qui couvre tous les utilisateurs affectés à une _zone géographique satellite_
1. Le client doit avoir un Accord Entreprise actif.
1.Le nombre total d’unités multigéographiques achetées doit être supérieur à 5 % du nombre total de sièges éligibles dans le _locataire_.

**Engagement:** Les clients peuvent affecter des utilisateurs de SharePoint Online/OneDrive Entreprise à n’importe quelle _zone géographique satellite_ prise en charge par multigéographique (voir la section 4.1.3). Les données client suivantes seront stockées dans la _zone géographique satellite_ appropriée : le contenu du site SharePoint Online et les fichiers stockés dans ce site, ainsi que les fichiers chargés sur OneDrive Entreprise.  

## <a name="multi-geo-capabilities-in-sharepoint-online--onedrive-for-business"></a>**Fonctionnalités multigéographiques dans SharePoint Online /OneDrive Entreprise**

Les fonctionnalités multigéographiques dans OneDrive et SharePoint Online permettent de contrôler les ressources partagées telles que les sites d’équipe SharePoint et les boîtes aux lettres de groupe Microsoft 365 stockées au repos dans une _zone géographique_ ou une _région locale_ spécifiée.

Chaque utilisateur, boîte aux lettres de groupe et site SharePoint a un emplacement de données préféré (PDL) qui indique la _zone géographique_ de la macro ou la _zone géographique de la région locale_ (emplacement où les données associées doivent être stockées. Les données personnelles des utilisateurs (boîte aux lettres Exchange et OneDrive) ainsi que les Groupes Microsoft 365 ou les sites SharePoint qu’ils créent peuvent être stockés à l’emplacement géographique de _la macro ou_ des _zones géographiques de la région locale_ spécifié pour répondre aux exigences de résidence des données. Vous pouvez spécifier différents administrateurs pour chaque emplacement _géographique de la région macro_ ou de _la zone géographique de la région locale_ .

Les utilisateurs profitent d’une expérience transparente lors de l’utilisation des services Microsoft 365, y compris les applications Office, OneDrive et Recherche. Pour plus d’informations, consultez Expérience utilisateur dans un environnement multigéographique.

### <a name="onedrive"></a>**OneDrive**

Le OneDrive de chaque utilisateur peut être provisionné ou déplacé par un administrateur vers un emplacement _géographique satellite_ conformément au PDL de l’utilisateur. Les fichiers personnels sont ensuite conservés dans cet emplacement _géographique satellite_ , bien qu’ils puissent être partagés avec des utilisateurs situés dans d’autres emplacements _Géographique de la région_ macro ou _de la région locale_ .

### <a name="sharepoint-sites-and-groups"></a>**Sites et groupes SharePoint**
La gestion de la fonctionnalité géo multiple est disponible via le Centre d’administration SharePoint.

Lorsqu’un utilisateur crée un site connecté à un groupe SharePoint dans un environnement multigéographique, son PDL est utilisé pour déterminer l’emplacement _géographique de la région_ macro ou de la _région locale où_ le site et sa boîte aux lettres de groupe associée sont créés. (Si la valeur PDL de l’utilisateur n’a pas été définie ou a été définie sur _Macro Région Géographique_ ou Emplacement _géographique de la région locale_ qui n’a pas été configuré en tant qu’emplacement _géographique satellite_ , le site et la boîte aux lettres sont créés dans la _zone géographique approvisionnée principale_.)

Les services Microsoft 365 autres qu’Exchange, OneDrive, SharePoint et Teams ne sont pas disponibles avec multigéographique. Toutefois, Groupes Microsoft 365 créées par ces services seront configurées avec le PDL du créateur et leur boîte aux lettres de groupe Exchange, le site SharePoint est approvisionné dans la _zone géographique de la macro_ ou la _zone géographique de la région locale_ correspondante.

### <a name="managing-the-multi-geo-environment"></a>**Gestion de l’environnement multigéographique**

La configuration et la gestion de votre environnement multigéographique s’effectuent via le centre d’administration SharePoint.

#### <a name="sharepoint-storage-quotas-in-multi-geo-environments"></a>**Quotas de stockage SharePoint dans des environnements multi-géographiques**

Par défaut, tous les emplacements _Geography_ d’un environnement multigéographique partagent le quota de stockage _client_ disponible.

Avec le paramètre de quota de stockage géographique SharePoint, vous pouvez gérer le quota de stockage pour chaque emplacement _Geography_ . Lorsque vous allouez un quota de stockage pour un emplacement _Geography_ , il devient la quantité maximale de stockage disponible pour cet emplacement _Geography_ et est déduit du quota de stockage _client_ disponible. Le quota de stockage _client_ restant disponible est ensuite partagé entre les emplacements _Geography_ configurés pour lesquels aucun quota de stockage spécifique n’a été alloué.

Le quota de stockage SharePoint pour n’importe quel emplacement _Geography_ peut être alloué par l’administrateur SharePoint Online en se connectant à la _zone géographique approvisionnée principale_. _Les administrateurs geography_ pour les emplacements _Geography satellite_ peuvent afficher le quota de stockage, mais ne peuvent pas l’allouer.

#### <a name="configure-a-storage-quota-for-a-_geography_-location"></a>**Configurer un quota de stockage pour un emplacement _Géographique_**

Utilisez [l’interpréteur de commandes Microsoft Office SharePoint Online Management Shell](https://www.microsoft.com/download/details.aspx?id=35588) et connectez-vous à l’emplacement _Géographique approvisionné principal_ pour allouer le quota de stockage à un emplacement _Geography_.

Pour allouer un quota de stockage à un emplacement, exécutez la cmdlet suivante :

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB <value>
```

Pour afficher le quota de stockage pour l’emplacement _Géographique_ actuel, exécutez :

```powershell
Get-SPOGeoStorageQuota
```

Pour afficher le quota de stockage pour tous les emplacements _Geography_ , exécutez :

```powershell
Get-SPOGeoStorageQuota -AllLocations
```

Pour supprimer le quota de stockage alloué pour un emplacement _Geography_ , définissez `StorageQuota value = 0`:

```powershell
Set-SPOGeoStorageQuota -GeoLocation <geolocationcode> -StorageQuotaMB 0
```

### <a name="move-a-onedrive-site"></a>Déplacer un site OneDrive

#### <a name="move-a-onedrive-site-to-a-different-_geography_-location"></a>Déplacer un site OneDrive vers un autre emplacement _géographique_

Avec le déplacement _de_ OneDrive Geography, vous pouvez déplacer le OneDrive d’un utilisateur vers un autre emplacement _Geography_ . Le déplacement _de la zone géographique_ OneDrive est effectué par l’administrateur SharePoint Online ou l’administrateur général Microsoft 365. Avant de commencer un déplacement _de zone géographique_ OneDrive, veillez à informer l’utilisateur dont OneDrive est déplacé et recommandez-lui de fermer tous les fichiers pendant la durée du déplacement. (Si l’utilisateur a ouvert un document à l’aide du client Office pendant le déplacement, le document doit être enregistré dans le nouvel emplacement une fois le déplacement terminé.) Le déplacement peut être planifié pour une heure ultérieure, si vous le souhaitez.

Le service OneDrive utilise Stockage Blob Azure pour stocker du contenu. L’objet blob de stockage associé au OneDrive de l’utilisateur sera déplacé de l’emplacement source vers l’emplacement _géographique_ de destination dans les 40 jours suivant la mise à la disposition de l’utilisateur. L’accès au OneDrive de l’utilisateur est restauré dès que le OneDrive de destination est disponible.

Pendant la fenêtre de déplacement de OneDrive _Geography_ (environ 2 à 6 heures), le OneDrive de l’utilisateur est défini en lecture seule. L’utilisateur peut toujours accéder à ses fichiers via l’application Synchronisation OneDrive ou son site OneDrive dans SharePoint Online. Une fois le déplacement de OneDrive _Geography_ terminé, l’utilisateur est automatiquement connecté à son OneDrive à l’emplacement _géographique_ de destination lorsqu’il accède à OneDrive dans le lanceur d’applications Microsoft 365. L’application de synchronisation commence automatiquement la synchronisation à partir du nouvel emplacement.

Les procédures décrites dans cet article nécessitent le [module Microsoft SharePoint Online PowerShell](https://www.microsoft.com/download/details.aspx?id=35588).

#### <a name="communicating-to-your-users"></a>Communication avec vos utilisateurs

Lorsque vous déplacez des sites OneDrive entre des emplacements _Geography_ , il est important de communiquer à vos utilisateurs ce à quoi s’attendre. Cela peut vous aider à atténuer la confusion des utilisateurs et les appels à votre support technique. Email vos utilisateurs avant le déplacement et indiquez-leur les informations suivantes : -Quand le déplacement est censé commencer et combien de temps il est prévu qu’il prenne -À quel emplacement _Geography_ leur OneDrive se déplace et l’URL pour accéder au nouvel emplacement -Ils doivent fermer leurs fichiers et ne pas apporter de modifications pendant le déplacement.
- Les autorisations de fichier et le partage ne changent pas suite au déplacement.
-À quoi s’attendre de l’expérience utilisateur dans un environnement multigéographique

N’oubliez pas d’envoyer un courrier électronique à vos utilisateurs une fois le déplacement terminé pour les avertir qu’ils peuvent reprendre leur travail dans OneDrive.

#### <a name="scheduling-onedrive-site-moves"></a>Planification de déplacements de site OneDrive

Vous pouvez planifier des déplacements de site OneDrive à l’avance (décrit plus loin dans cet article). Nous vous recommandons de commencer avec un petit nombre d’utilisateurs pour valider vos workflows et stratégies de communication. Une fois que vous êtes à l’aise avec le processus, vous pouvez planifier les déplacements comme suit : -Vous pouvez planifier jusqu’à 4 000 déplacements à la fois.
- À mesure que les déplacements commencent, vous pouvez en planifier davantage, avec un maximum de 4 000 déplacements en attente dans la file d’attente et à une heure donnée.
- La taille maximale d’un OneDrive pouvant être déplacé est de 1 téraoctet (1 To).

#### <a name="moving-a-onedrive-site"></a>**Déplacement d’un site OneDrive**
Pour effectuer un déplacement _de zone géographique_ OneDrive, l’administrateur _client_ doit d’abord définir l’emplacement de données préféré (PDL) de l’utilisateur sur l’emplacement _Géographique_ approprié. Une fois que la pdL est définie, attendez au moins 24 heures que la mise à jour pdl soit synchronisée entre les emplacements _Geography_ avant de commencer le déplacement de OneDrive _Geography_ .

Lorsque vous utilisez les applets de commande de déplacement _Geography_ , connectez-vous au service SPO à l’emplacement _OneDrive Geography_ actuel de l’utilisateur, à l’aide de la syntaxe suivante :

```powershell
Connect-SPOService -url https://<tenantName>-admin.sharepoint.com
```

Par exemple : pour déplacer OneDrive de l’utilisateur « Matt@contosoenergy.onmicrosoft.com », connectez-vous au centre d’Administration d’EUR SharePoint, car le OneDrive de l’utilisateur se trouve dans l’emplacement _EUR Geography_ :

```powershell
Connect-SPOService -url https://contosoenergyeur-admin.sharepoint.com
```

#### <a name="validating-the-environment"></a>**Validation de l’environnement**
  
Avant de commencer un déplacement _de zone géographique_ OneDrive, nous vous recommandons de valider l’environnement.

Pour vous assurer que tous les emplacements _Geography_ sont compatibles, exécutez :

```powershell
Get-SPOGeoMoveCrossCompatibilityStatus
```

Vous verrez une liste de vos emplacements _Geography_ et si le contenu peut être déplacé entre sera indiqué comme « Compatible ». Si la commande renvoie « Incompatible », réessayez de valider l’état plus tard.

Si un OneDrive contient, par exemple, un sous-site, il ne peut pas être déplacé. Vous pouvez utiliser la cmdlet Start-SPOUserAndContentMove avec le paramètre -ValidationOnly pour contrôler si le site OneDrive peut être déplacé :

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UPN> -DestinationDataLocation <DestinationDataLocation> -ValidationOnly
```

  This will return Success if the OneDrive is ready to be moved or Fail if there is a legal hold or subsite that would prevent the move. Once you have validated that the OneDrive is ready to move, you can start the move.

#### <a name="start-a-onedrive-geo-move"></a>**Démarrer un déplacement géographique OneDrive**

Pour démarrer le déplacement, exécutez :

```powershell
Start-SPOUserAndContentMove -UserPrincipalName <UserPrincipalName> -DestinationDataLocation <DestinationDataLocation>
```

À l’aide de ces paramètres :

- _UserPrincipalName_ : UPN de l’utilisateur dont le site OneDrive est déplacé.
- _DestinationDataLocation_ : Geo-Location où oneDrive doit être déplacé. Cela doit être identique à l’emplacement de données préféré de l’utilisateur.

Par exemple, pour déplacer le site OneDrive de matt@contosoenergy.onmicrosoft.com de l’emplacement EUR à AUS, exécutez :

```powershell
Start-SPOUserAndContentMove -UserPrincipalName matt@contosoenergy.onmicrosoft.com -DestinationDataLocation AUS
```

Pour planifier un déplacement _geography_ pour une date ultérieure, utilisez l’un des paramètres suivants :

- _PreferredMoveBeginDate_ : le déplacement commencera probablement à l’heure spécifiée. L’heure doit être spécifiée en temps universel coordonné (UTC).
- _PreferredMoveEndDate_ – The move will likely be completed by this specified time, on a best effort basis. Time must be specified in Coordinated Universal Time (UTC).

#### <a name="cancel-a-onedrive-_geography_-move"></a>**Annuler un déplacement _de zone géographique_ OneDrive**
  
Vous pouvez arrêter le déplacement _Geography_ du OneDrive d’un utilisateur, à condition que le déplacement ne soit pas en cours ou terminé à l’aide de l’applet de commande :

```powershell
Stop-SPOUserAndContentMove – UserPrincipalName <UserPrincipalName>
```

où _UserPrincipalName_ est l’UPN de l’utilisateur dont vous souhaitez arrêter le déplacement du site OneDrive.

#### <a name="determining-current-status"></a>**Déterminer l’état actuel**

Vous pouvez vérifier l’état d’un _déplacement géographique_ OneDrive dans ou hors de la _zone Geography_ à laquelle vous êtes connecté à l’aide de l’applet de commande Get-SPOUserAndContentMoveState.

Les états de déplacement sont décrits dans le tableau suivant.

|Statut|Description|
|---|---|
|NotStarted|Le déplacement n’a pas démarré|
|InProgress (_n_/4)|Le déplacement est en cours dans l’un des états suivants : <ul><li>Validation (1/4)</li><li>Sauvegarde (2/4)</li><li>Restauration (3/4)</li><li>Nettoyage (4/4)</li></ul>|
|Opération réussie|Le déplacement a réussi.|
|Échec|Le déplacement a échoué.|

Pour rechercher l’état du déplacement d’un utilisateur spécifique, utilisez le paramètre _UserPrincipalName_ :

```powershell
Get-SPOUserAndContentMoveState -UserPrincipalName <UPN>
```

Pour rechercher l’état de tous les déplacements dans ou hors de l’emplacement _Geography_ auquel vous êtes connecté, utilisez le paramètre _MoveState_ avec l’une des valeurs suivantes : NotStarted, InProgress, Success, Failed, All.

```powershell
Get-SPOUserAndContentMoveState -MoveState <value>
```

Vous pouvez également ajouter le paramètre _Verbose_ pour obtenir des descriptions plus détaillées de l’état de déplacement.

#### <a name="user-experience"></a>**Expérience utilisateur**

Les utilisateurs de OneDrive doivent remarquer une interruption minimale si leur OneDrive est déplacé vers un autre emplacement _Geography_ . À l’exception d’un bref état en lecture seule lors du déplacement, les liens et autorisations existants continuent de fonctionner comme prévu après le déplacement.

#### <a name="users-onedrive"></a>**OneDrive de l’utilisateur**

Pendant que le déplacement est en cours, le OneDrive de l’utilisateur est défini sur lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers son OneDrive dans le nouvel emplacement _Geography_  lorsqu’il accède à OneDrive le lanceur d’applications Microsoft 365 ou un navigateur web.

#### <a name="permissions-on-onedrive-content"></a>**Autorisations sur le contenu OneDrive**

Les utilisateurs disposant d’autorisations sur le contenu OneDrive continueront d’avoir accès au contenu pendant le déplacement et une fois celui-ci terminé.

#### <a name="onedrive-sync-app"></a>**application Synchronisation OneDrive**

L’application Synchronisation OneDrive détecte et transfère automatiquement la synchronisation vers le nouvel emplacement OneDrive une fois le déplacement de OneDrive _Geography_ terminé. L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer une autre action. (Version 17.3.6943.0625 ou ultérieure de l’application de synchronisation requise.) Si un utilisateur met à jour un fichier alors que le déplacement de OneDrive _Geography_ est en cours, l’application de synchronisation l’informe que les chargements de fichiers sont en attente pendant le déplacement.

#### <a name="sharing-links"></a>**Liens de partage**

Une fois le déplacement de OneDrive _Geography_ terminé, les liens partagés existants pour les fichiers qui ont été déplacés sont automatiquement redirigés vers le nouvel emplacement _Geography_ .

#### <a name="onenote-experience"></a>**Expérience OneNote**

Le client OneNote win32 et l’application UWP (universelle) détectent et synchronisent automatiquement les blocs-notes vers le nouvel emplacement OneDrive une fois le déplacement de OneDrive _Geography_ terminé. L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer une autre action. Le seul indicateur visible pour l’utilisateur est l’échec de la synchronisation du bloc-notes lorsque le déplacement de OneDrive _Géographie_ est en cours. Cette expérience est disponible sur les versions suivantes du client OneNote :

- OneNote win32 – Version 16.0.8326.2096 (et versions ultérieures)
- OneNote UWP – Version 16.0.8431.1006 (et versions ultérieures)
- Application mobile OneNote : Version 16.0.8431.1011 (et versions ultérieures)

#### <a name="teams-app"></a>**Application Teams**

Une fois le déplacement de OneDrive _Geography_ terminé, les utilisateurs ont accès à leurs fichiers OneDrive sur l’application Teams. En outre, les fichiers partagés via la conversation Teams à partir de leur OneDrive avant le déplacement _geography_ continueront de fonctionner une fois le déplacement terminé.

#### <a name="onedrive-mobile-app-ios"></a>**Application mobile OneDrive (iOS)**

Une fois le déplacement de OneDrive _Geography_ terminé, l’utilisateur doit se déconnecter et se reconnecter à l’application mobile iOS pour effectuer la synchronisation avec le nouvel emplacement OneDrive.

#### <a name="existing-followed-groups-and-sites"></a>**Sites et groupes suivis existants**

Les sites et groupes suivis s’affichent dans le OneDrive de l’utilisateur, quel que soit son emplacement _géographique_ . Les sites et les groupes hébergés dans un autre emplacement _Geography_ s’ouvrent dans un onglet distinct.

#### <a name="delve-geo-url-updates"></a>**Mises à jour des URL géographiques Delve**

Les utilisateurs seront envoyés à la _zone géographique_ Delve correspondant à leur PDL uniquement après le déplacement de leur OneDrive vers la nouvelle _zone géographique_.

### <a name="move-a-sharepoint-site"></a>**Déplacer un site SharePoint**
#### <a name="move-a-sharepoint-site-to-a-different-_geography_-location"></a>**Déplacer un site SharePoint vers un autre emplacement _Géographique_**

Avec le déplacement _géographique_ du site SharePoint, vous pouvez déplacer des sites SharePoint vers d’autres emplacements _Geography_ au sein de votre environnement multigéographique.
Les types de site suivants peuvent être déplacés entre les emplacements _Geography_ :

- Sites microsoft 365 connectés à un groupe, y compris les sites associés à Microsoft Teams
- Sites modernes sans association de groupe Microsoft 365
- Sites SharePoint classiques
- Sites de communication

Vous devez être administrateur général ou administrateur SharePoint pour déplacer un site entre des emplacements _Géographiques_ .
Il existe une fenêtre en lecture seule pendant le déplacement _géographique_ du site SharePoint d’environ 4 à 6 heures, en fonction du contenu du site

#### <a name="best-practices"></a>**Meilleures pratiques**

- Essayez d’effectuer un déplacement de site SharePoint sur un site de test pour vous familiariser avec la procédure.
- Avant de planifier ou d’effectuer le déplacement, vérifiez si le site peut être déplacé.
- Autant que possible, planifiez les déplacements intersites en dehors des heures d’ouverture afin de réduire l’impact sur les utilisateurs.
- Avant de déplacer des sites, communiquez avec les utilisateurs concernés.

#### <a name="communicating-to-your-users"></a>**Communication avec vos utilisateurs**

Lorsque vous déplacez des sites SharePoint entre des emplacements _Geography_ , il est important de communiquer aux utilisateurs des sites (généralement toute personne ayant la possibilité de modifier le site) à quoi s’attendre. Cela peut vous aider à atténuer la confusion des utilisateurs et les appels à votre support technique. Avant de déplacer des sites, envoyez un courrier électronique à leurs utilisateurs pour leur communiquer les informations suivantes :

- date de début et durée prévues du déplacement ;
- Emplacement _géographique_ vers lequel le site est déplacé et URL pour accéder au nouvel emplacement
- nécessité de fermer les fichiers et de ne pas y apporter de modifications durant le déplacement ;
- absence de modification des autorisations et des partages de fichiers en raison du déplacement ;
- changement d’expérience utilisateur dans un environnement multigéographique.

Une fois le déplacement terminé, n’oubliez pas d’envoyer un courrier aux utilisateurs de vos sites pour les avertir qu’ils peuvent reprendre leur travail.

#### <a name="scheduling-sharepoint-site-moves"></a>**Planification des déplacements de sites SharePoint**

Vous pouvez planifier les déplacements de sites SharePoint (voir plus loin dans cet article). Vous pouvez planifier les déplacements comme suit :

- Vous pouvez planifier jusqu’à 4 000 déplacements à la fois.
- Lorsque les déplacements commencent, vous pouvez planifier plus d’informations, avec un maximum de 4 000 déplacements dans la file d’attente et à un moment donné.
- La taille maximale d’un site SharePoint qui peut être déplacé est de 1 téraoctet (1 To).

Pour planifier un déplacement _géographique_ d’un site SharePoint pour une date ultérieure, incluez l’un des paramètres suivants lorsque vous démarrez le déplacement :

- PreferredMoveBeginDate : le déplacement commencera probablement à l’heure spécifiée.
- PreferredMoveEndDate : le déplacement sera probablement effectué à l’heure spécifiée, au mieux.

L’heure doit être exprimée en Temps universel coordonné (UTC) pour les deux paramètres.

#### <a name="moving-the-site"></a>**Déplacement du site**

Le _déplacement géographique_ du site SharePoint nécessite que vous vous connectiez et effectuez le déplacement à partir de l’URL de Administration SharePoint à l’emplacement _Geography_ où se trouve le site.

Par exemple, si l’URL du site est `https://contosohealthcare.sharepoint.com/sites/Turbines`, connectez-vous à l’URL de Administration SharePoint à l’adresse `https://contosohealthcare-admin.sharepoint.com`:

```powershell
Connect-SPOService -Url https://contosohealthcare-admin.sharepoint.com
```

#### <a name="validating-the-environment"></a>**Validation de l’environnement**

Avant de planifier le déplacement d’un site, nous vous recommandons de vérifier que celui-ci peut être déplacé.

Il n’est pas possible de déplacer des sites avec :

- Business Connectivity Services
- InfoPath Forms
- Modèles d’IRM (Gestion des Droits relatifs à l’Information) appliqués

Pour vous assurer que tous les emplacements _Geography_ sont compatibles, exécutez `Get-SPOGeoMoveCrossCompatibilityStatus`. Cela affiche tous vos emplacements _Geography_ et indique si l’environnement est compatible avec l’emplacement _Géographique_ de destination.

Pour vérifier si votre site peut être déplacé, utilisez la cmdlet `Start-SPOSiteContentMove` avec le paramètre `-ValidationOnly`. Par exemple :

```PowerShell
Start-SPOSiteContentMove -SourceSiteUrl <SourceSiteUrl> -ValidationOnly -DestinationDataLocation <DestinationLocation>
```

Cette cmdlet retourne _Success_ si le site peut être déplacé, ou _Fail_ en cas de blocage du déplacement.

#### <a name="start-a-sharepoint-site-_geography_-move-for-a-site-with-no-associated-microsoft-365-group"></a>**Démarrer un déplacement _géographique_ d’un site SharePoint pour un site sans groupe Microsoft 365 associé**
  
Par défaut, l’URL initiale du site devient l’URL de l’emplacement _Géographique_ de destination. Par exemple :

`https://Contoso.sharepoint.com/sites/projectx` devient `https://ContosoEUR.sharepoint.com/sites/projectx`

Pour les sites sans association de groupe Microsoft 365, vous pouvez également renommer le site à l’aide du `-DestinationUrl` paramètre . Par exemple :

<https://Contoso.sharepoint.com/sites/projectx> devient `https://ContosoEUR.sharepoint.com/sites/projecty`

Pour commencer à déplacer le site, exécutez la cmdlet suivante :

```powershell
Start-SPOSiteContentMove -SourceSiteUrl <siteURL> -DestinationDataLocation <DestinationDataLocation> -DestinationUrl <DestinationSiteURL>
```

#### <a name="start-a-sharepoint-site-_geography_-move-for-a-microsoft-365-group-connected-site"></a>**Démarrer un déplacement _géographique_ d’un site SharePoint pour un site connecté à un groupe Microsoft 365**

  Pour déplacer un site connecté à un groupe Microsoft 365, l’administrateur général ou l’administrateur SharePoint doit d’abord modifier l’attribut Preferred Data Location (PDL) pour le groupe Microsoft 365.

Pour définir la pdl pour un groupe Microsoft 365 :

```PowerShell
Set-SPOUnifiedGroup -PreferredDataLocation <PDL> -GroupAlias <GroupAlias>
Get-SPOUnifiedGroup -GroupAlias <GroupAlias>
```

Une fois l’emplacement par défaut des données mis à jour, vous pouvez commencer à déplacer le site :

```PowerShell
Start-SPOUnifiedGroupMove -GroupAlias <GroupAlias> -DestinationDataLocation <DestinationDataLocation>
```

#### <a name="cancel-a-sharepoint-site-_geography_-move"></a>**Annuler un déplacement _géographique_ d’un site SharePoint**

Vous pouvez arrêter un déplacement _géographique_ d’un site SharePoint, à condition que le déplacement ne soit pas en cours ou terminé à l’aide de l’applet de commande Stop-SPOSiteContentMove.

#### <a name="determining-the-status-of-a-sharepoint-site-_geography_-move"></a>**Détermination de l’état d’un déplacement _géographique_ d’un site SharePoint**

Vous pouvez déterminer l’état d’un déplacement de site dans notre zone _géographique_ à laquelle vous êtes connecté à l’aide des applets de commande suivantes :

- [Get-SPOSiteContentMoveState](/powershell/module/sharepoint-online/get-spositecontentmovestate) (sites non connectés à un groupe)
- [Get-SPOUnifiedGroupMoveState](/powershell/module/sharepoint-online/get-spounifiedgroupmovestate) (sites connectés à un groupe)

Pour spécifier le site dont vous voulez voir l’état de déplacement, utilisez le paramètre `-SourceSiteUrl`.

Les états de déplacement sont décrits dans le tableau suivant.

****

|Statut|Description|
|---|---|
|Ready to Trigger|Le déplacement n’a pas commencé.|
|Scheduled|Le déplacement est en file d’attente mais n’a pas encore commencé.|
|InProgress (n/4)|Le déplacement est en cours dans l’un des états suivants : Validation (1/4), Sauvegarde (2/4), Restauration (3/4), Nettoyage (4/4).|
|Opération réussie|Le déplacement a réussi.|
|Échec|Le déplacement a échoué.|
|

Vous pouvez également appliquer l’option `-Verbose` pour voir des informations supplémentaires sur le déplacement.

#### <a name="user-experience"></a>**Expérience utilisateur**

Les utilisateurs du site doivent remarquer une interruption minimale lorsque leur site est déplacé vers un autre emplacement _Geography_ . À l’exception d’un bref état en lecture seule lors du déplacement, les liens et autorisations existants continuent de fonctionner comme prévu après le déplacement.

#### <a name="site"></a>**Site**

Pendant que le déplacement est en cours, le site est défini sur lecture seule. Une fois le déplacement terminé, l’utilisateur est dirigé vers le nouveau site dans le nouvel emplacement _Geography_ lorsqu’il clique sur des signets ou d’autres liens vers le site.

#### <a name="permissions"></a>**Autorisations**

Les utilisateurs disposant d’autorisations d’accès au site continuent de pouvoir y accéder durant et après le déplacement.

#### <a name="sync-app"></a>**Synchroniser l’application**

L’application de synchronisation détecte et transfère automatiquement la synchronisation vers le nouvel emplacement du site une fois le déplacement du site terminé. L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer un autre action. (Version 17.3.6943.0625 ou ultérieure de l’application de synchronisation requise.) Si un utilisateur met à jour un fichier alors que le déplacement est en cours, l’application de synchronisation l’informe que les chargements de fichiers sont en attente pendant le déplacement.

#### <a name="sharing-links"></a>**Liens de partage**
Une fois le déplacement _géographique_ du site SharePoint terminé, les liens partagés existants pour les fichiers qui ont été déplacés sont automatiquement redirigés vers le nouvel emplacement _Geography_ .

#### <a name="most-recently-used-files-in-office-mru"></a>**Fichiers récents dans Office**

Une fois le déplacement terminé, le service Fichiers récents est mis à jour avec l’URL du site et les URL de son contenu. Cela vaut pour Word, Excel et PowerPoint.

#### <a name="onenote-experience"></a>**Expérience OneNote**

Le client OneNote Win32 et l’application UWP (plateforme Windows universelle) détectent et synchronisent automatiquement et sans difficulté les blocs-notes sur le nouvel emplacement du site une fois celui-ci déplacé. L’utilisateur n’a pas besoin de se reconnecter ou d’effectuer un autre action. Le seul indicateur pour l’utilisateur est un échec éventuel de synchronisation de bloc-notes durant le déplacement du site. Cette expérience est disponible sur les versions de client OneNote suivantes : -OneNote win32 – Version 16.0.8326.2096 (et versions ultérieures) -OneNote UWP – Version 16.0.8431.1006 (et versions ultérieures) -Application mobile OneNote – Version 16.0.8431.1011 (et versions ultérieures)

#### <a name="teams-applicable-to-microsoft-365-group-connected-sites"></a>**Teams (applicable aux sites connectés au groupe Microsoft 365)**

Une fois le déplacement _géographique_ du site SharePoint terminé, les utilisateurs ont accès à leurs fichiers de site de groupe Microsoft 365 sur l’application Teams. En outre, les fichiers partagés via la conversation Teams à partir de leur site avant le déplacement _geography_ continueront de fonctionner une fois le déplacement terminé.
Le déplacement _géographique_ d’un site SharePoint ne prend pas en charge le déplacement de canaux privés d’une _zone Géographique_ vers une autre. Les canaux privés restent dans la _zone géographique_ d’origine.

#### <a name="sharepoint-mobile-app-iosandroid"></a>**Application SharePoint Mobile (iOS/Android)**
L’application mobile SharePoint est compatible avec la _géographie_ et peut détecter le nouvel emplacement _Geography_ du site.

#### <a name="sharepoint-workflows"></a>**Flux de travail SharePoint**
Les flux de travail SharePoint 2013 doivent être republié après le déplacement du site. Les flux de travail SharePoint 2010 devraient continuer de fonctionner normalement.

#### <a name="apps"></a>**Applications**
Si vous déplacez un site avec des applications, vous devez rétablir l’application dans le nouvel emplacement _Geography_ du site, car l’application et ses connexions peuvent ne pas être disponibles dans l’emplacement _Géographique_ de destination.

#### <a name="power-automate"></a>**Power Automate**
Dans la plupart des cas, les flux Power Automate continueront de fonctionner après un déplacement _géographique_ d’un site SharePoint. Nous vous conseillons de les tester une fois le déplacement terminé.

#### <a name="power-apps"></a>**Power Apps**

Power Apps doit être recréé à l’emplacement de destination.

#### <a name="data-movement-between-geo-locations"></a>**Déplacement de données entre emplacements géographiques**

SharePoint utilise Stockage Blob Azure pour son contenu, tandis que les métadonnées associées aux sites et à ses fichiers sont stockées dans SharePoint. Une fois que le site a été déplacé de son emplacement _géographique_ source vers son emplacement _Géographique_ de destination, le service déplace également le stockage Blob associé. Le déplacement du Stockage Blob prend environ 40 jours. Cela n’aura aucun impact sur l’interaction des utilisateurs avec les données.

Vous pouvez vérifier l’état du déplacement du stockage Blob à l’aide de l’applet [de commande Get-SPOCrossGeoMoveReport](/powershell/module/sharepoint-online/get-spocrossgeomovereport) .
****

### <a name="enabling-sharepoint-multi-geo-in-your-_satellite-geography_-location"></a>**Activation de SharePoint Multi-Géo dans votre emplacement _géographique satellite_**

Cet article s’adresse aux administrateurs globaux ou SharePoint qui ont créé un emplacement _géographique_ multigéographique **par satellite avant** que SharePoint Multi-Géo fonctionnalités ne soient mises à la disposition générale le 27 mars 2019 et qui n’ont pas activé SharePoint Multi-Géo dans leur ou leurs emplacements _géographiques satellites_.

>[!NOTE]
>Si vous avez ajouté un nouvel emplacement _Geography_ **après le 27 mars 2019,** vous n’avez pas besoin d’effectuer ces instructions, car votre nouvel emplacement _Geography_ sera déjà activé pour OneDrive et SharePoint Multi-Géo.

Ces instructions vous permettent d’activer SharePoint dans votre emplacement _géographique satellite_, afin que vos utilisateurs de satellites multigéographiques puissent tirer parti des fonctionnalités OneDrive et SharePoint Multi-Géo dans O365.

>[!IMPORTANT]
>Veuillez noter qu’il s’agit d’une activation possible. Une fois que vous avez défini le mode SPO, vous ne pouvez pas rétablir votre _locataire_ en mode OneDrive uniquement multigéographique sans escalade avec prise en charge.

#### <a name="to-set-a-_geography_-location-into-spo-mode"></a>**Pour définir un emplacement _Geography_ en mode SPO**

Pour définir un emplacement _Geography_ en mode SPO, connectez-vous à l’emplacement _Geography_ que vous souhaitez définir en mode SPO :

1. Ouvrez votre outil SharePoint Online Management Shell
2. Se connecter-SPOService-URL « https://$tenantGeo-admin.sharepoint.com »- informations d’identification $credential
3. Set-SPOMultiGeoExperience</br></br>
![Set-SPOMultiGeoExperience.](../media/Set-SPO-MultiGeo.jpg)
4. Cette opération prend généralement environ une heure pendant que nous effectuons différentes republiations dans le service et réappablons votre _locataire_. Après au moins 1 heure, veuillez effectuer une SPOMultiGeoExperience Get.  Cela vous indique si cet emplacement _Geography_ est en mode SPO.</br></br>
![Image de Set-SPOMultiGeoExperience.](../media/Get-SPO-MultiGeo.jpg)

>[!Note]
>Certains caches du service sont mis à jour toutes les 24 heures. Il est donc possible que, pendant une période allant jusqu’à 24 heures, votre _zone géographique satellite_ se comporte par intermittence comme si elle était encore en mode ODB. Cela n’entraîne pas de problème d’ordre technique.

## <a name="migration"></a>Migration

Lors du déplacement de SharePoint Online, les données des services suivants sont également déplacées :
  
- OneDrive Entreprise
- Services vidéo Microsoft 365
- Office dans un navigateur
- Applications Microsoft 365 pour les entreprises
- Visio Pro pour Microsoft 365

Une fois que nous avons terminé le déplacement de vos données SharePoint Online, vous pouvez voir certains des effets suivants.
  
### <a name="microsoft-365-video-services"></a>Microsoft 365 Video Services

- Le déplacement de vidéos prend plus de temps que le déplacement d'autres contenus dans SharePoint Online.
- Une fois le contenu de SharePoint Online déplacé, vous ne pourrez pas lire les vidéos pendant une certaine période.
- Nous supprimons les copies transcodées du centre de données précédent et les transcodons à nouveau dans le nouveau centre de données.

### <a name="search"></a>Rechercher

Dans le cadre du déplacement de vos données SharePoint Online, nous migrons vos paramètres de recherche et d'index vers un nouvel emplacement. Jusqu'à la **fin** du déplacement de vos données SharePoint Online, nous continuons de desservir vos utilisateurs depuis l'index situé dans l'emplacement d'origine. Dans le nouvel emplacement, la fonction recherche démarre automatiquement une analyse de votre contenu une fois le déplacement de vos données SharePoint Online terminé. À ce moment-là, nous desservirons vos utilisateurs depuis l'index migré. Les modifications apportées à votre contenu après la migration ne sont pas prises en compte dans l’index migré tant que l’analyse ne les a pas récupérées. La plupart des clients ne remarquent pas que les résultats sont moins frais une fois que nous avons terminé le déplacement de leurs données SharePoint Online, mais certains clients peuvent constater une actualisation réduite dans les 24 à 48 premières heures.
  
Les fonctionnalités de recherche suivantes sont concernées :
  
- Résultats de la recherche et composants WebPart de recherche : Les résultats n’incluent pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées.
- Delve : Delve n’inclut pas les modifications qui se sont produites après la migration jusqu’à ce que l’analyse les ait récupérées.
- Popularity and Search Reports for the site: Counts for Excel reports in the new location only include migrated counts and counts from usage reports that have run after we completed moving your SharePoint Online data. Any counts from the interim period are lost and can't be recovered. This period is typically a couple of days. Some customers might experience shorter or longer losses.
- Portail vidéo : les nombres et les statistiques de vue dépendent des statistiques des rapports Excel. Par conséquent, ils sont perdus pendant le même nombre de jours que les rapports Excel.
- eDiscovery (découverte électronique) : Les éléments modifiés au cours de la migration ne sont pas affichés avant que l’analyse n’ait récupéré les modifications.
- Protection contre la perte de données (DLP) : Les politiques ne sont pas appliquées sur les éléments qui changent avant que l’analyse n’ait récupéré les modifications.

Dans le cadre de la migration, la _zone géographique approvisionnée principale_ change et tout le nouveau contenu est stocké au repos dans la nouvelle _zone géographique approvisionnée principale_. Le contenu existant sera déplacé en arrière-plan sans aucun impact pour vous pendant 90 jours après la première modification de l’emplacement des données SharePoint Online dans le centre d’administration.

## <a name="how-can-i-determine-customer-data-location"></a>Comment puis-je déterminer l’emplacement des données client ?

Vous trouverez l’emplacement réel des données dans _le Centre de Administration du locataire_.  En tant qu’administrateur _client_, vous pouvez trouver l’emplacement réel des données, pour les données validées, en accédant à Administration->Paramètres->Paramètres de l’organisation->Profil de l’organisation->Emplacement des données. Si vous n’avez pas créé de _locataire_ , vous pouvez en _créer un lors_ de l’inscription à une version d’évaluation M365.
