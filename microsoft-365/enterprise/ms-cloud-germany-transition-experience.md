---
title: Ce qui va changer après la migration vers Office 365 services dans les nouvelles régions de centres de données allemandes
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/11/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
ms.assetid: 706d5449-45e5-4b0c-a012-ab60501899ad
description: 'Résumé : Comprendre ce qui a changé pour passer de Microsoft Cloud Germany (Microsoft Cloud Deutschland) à Office 365 services dans la nouvelle région de centre de données allemande.'
ms.openlocfilehash: 42ac9e61632305a9e75bf7ba9de2cec3e3d658fb
ms.sourcegitcommit: 6c342a956b2dbc32be33bac1a23a5038490f1b40
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58531514"
---
# <a name="what-will-change-after-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Ce qui va changer après la migration vers Office 365 services dans les nouvelles régions de centres de données allemandes

Les migrations de clients sont conçues pour avoir un impact minimal sur les administrateurs et les utilisateurs. Toutefois, il existe des facteurs à prendre en compte pour chaque charge de travail. Consultez les sections suivantes pour mieux comprendre l’expérience de migration des charges de travail.

Voici les principales différences entre Microsoft Cloud Deutschland et Office 365 services dans les nouvelles régions de centres de données allemandes.

| Catégorie | Microsoft Cloud Allemagne (Microsoft Cloud Deutschland) | Services Office 365 dans les nouvelles régions de centre de données allemandes |
|:-------|:-----|:-------|
| Services Microsoft 365 disponibles pour un abonnement avec un seul client Office 365 | 15 services | 29 services <br><br> Pour plus d’informations, voir Quelle est la disponibilité des services entre les différentes offres [Office 365 de service cloud ?](ms-cloud-germany-transition.md#serv-avail) |
| Nouvelles fonctionnalités | Aucune nouvelle fonctionnalité n’est disponible. | De nouvelles fonctionnalités seront disponibles en cohérence avec Office 365 services. |
| Administrateur de données | Oui | Non |
| Collaboration entre clients Office 365 du monde entier | Non | Oui |
| Résidence des données client | Les données client sont stockées uniquement dans les centres de données allemands. | Microsoft stockera les données client suivantes au repos exclusivement en Allemagne : <ul><li> Exchange Online de boîte aux lettres (corps du courrier électronique, entrées de calendrier et contenu des pièces jointes) </li><li> SharePoint Contenu du site en ligne et fichiers stockés dans ce site, et fichiers chargés sur OneDrive Entreprise </li></ul> |
| Conditions applicables | [Conditions d’accès aux](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) services en ligne avec ce [supplément](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Conditions d’utilisation des services en ligne](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="azure-active-directory"></a>Azure Active Directory

Ce qui ne change pas :

- Le domaine initial du client (par exemple) avec un ID de client (GUID) et des domaines `contoso.onmicrosoft.de` personnalisés est persistant après la migration. 

- Les demandes d’authentification pour les ressources migrées vers des services Office 365 sont accordées par le service d’authentification Azure Office 365 services d’authentification ( `login.microsoftonline.com` ). Pendant la migration, les ressources qui restent en Office 365 Allemagne sont authentifiées par le service Azure Allemagne existant ( `login.microsoftonline.de` ).

Remarques à prendre en compte :

- Pour les comptes de domaine géré, une fois la copie du client Azure Active Directory initial (Azure AD) terminée (qui est la première étape de la migration d’Azure AD vers le service Azure AD des services Office 365), les modifications de mot de passe, les modifications de réinitialisation de mot de passe en libre-service (SSPR) et les réinitialisations de mot de passe par les administrateurs doivent être réalisées à partir des portails de service Office 365. À ce stade, les demandes de mise à jour des mots de passe à partir du service Allemagne n’aboutront pas, car le client Azure AD a été migré vers Office 365 services. Les réinitialisations des mots de passe de domaine fédérés ne sont pas affectées, car elles sont effectuées dans l’annuaire local.

- Les sign-ins Azure sont présentées dans le portail où l’utilisateur tente d’y accéder. Les journaux d’audit sont disponibles uniquement à partir du point Office 365 services après la transition. Avant la migration jusqu’à la fin de la migration, vous devez enregistrer les journaux de connexion et d’audit à partir du portail Microsoft Cloud Deutschland.

- Les réinitialisations de mot de passe, les modifications de mot de passe, la réinitialisation de mot de passe par un administrateur pour les organisations gérées (qui n’utilisent pas les services de fédération Active Directory) doivent être effectuées via le portail Office 365 services. Les tentatives des utilisateurs qui accèdent aux portails Microsoft Cloud Deutschland pour réinitialiser les mots de passe échouent.

- Les demandes des personnes soumises au règlement général sur la protection des données (R GDPR) sont exécutées à partir du portail d’administration Azure des services Office 365 pour les demandes futures. Toutes les données de diagnostic héritées ou non client résidant dans Microsoft Cloud Deutschland sont supprimées au moins 30 jours.

## <a name="subscriptions--licenses"></a>Abonnements & licences

- Office 365 abonnements Dynamics de Microsoft Cloud Deutschland sont transitionés vers la région allemande avec le déplacement d’Azure AD. L’organisation est ensuite mise à jour pour refléter les nouveaux abonnements Office 365 services. Pendant le bref processus de transfert d’abonnement, les modifications apportées aux abonnements sont bloquées.

- À mesure que le client passe aux services Office 365, ses abonnements et licences propres à l’Allemagne sont normalisés avec les nouvelles offres Office 365 services. Les abonnements Office 365 services sont achetés pour les abonnements transférés en Allemagne. Les utilisateurs qui ont des licences en Allemagne se Office 365 licences de services. À la fin de l’exécution, les abonnements Germany hérités sont annulés et supprimés du client Office 365 services en cours.

- Après la migration des charges de travail individuelles, des fonctionnalités supplémentaires sont disponibles via les services Office 365 (tels que Le Planificateur Microsoft et Power Automate) en raison des nouveaux abonnements aux services Office 365. Si cela est approprié pour votre organisation, le client ou l’administrateur de licences peut désactiver les nouveaux plans de service lorsque vous planifiez la gestion des changements afin d’introduire les nouveaux services. Pour obtenir des instructions sur la désactivation des plans de service attribués aux licences des utilisateurs, voir Désactiver l’accès aux services Microsoft 365 tout en attribuant des [licences utilisateur.](/office365/enterprise/powershell/disable-access-to-services-while-assigning-user-licenses)

## <a name="exchange-online"></a>Exchange Online

- Exchange URL de ressources sont transitionnables du point de terminaison hérité germany vers `outlook.office.de` le point de terminaison Office 365 services après `outlook.office365.com` la migration. Vos utilisateurs peuvent accéder à leur boîte aux lettres migrée à l’aide de l’URL héritée jusqu’à la fin de la migration. Les clients doivent migrer les utilisateurs vers la nouvelle URL dès que possible après Exchange migration commence pour éviter d’affecter le retrait de l’environnement allemand. Les URL Office 365 services de gestion pour Outlook services deviennent disponibles uniquement après le début Exchange migration.

- Les boîtes aux lettres sont migrées en tant que processus back-end. Les utilisateurs de votre organisation peuvent se voir dans Microsoft Cloud Deutschland ou dans la région allemande pendant la transition et faire partie de la même organisation Exchange (dans la même liste d’adresses globale).

- Les utilisateurs de Outlook Web App qui accèdent au service à l’aide d’une URL dans laquelle leur boîte aux lettres ne réside pas voient une invite d’authentification supplémentaire. Par exemple, si la boîte aux lettres de l’utilisateur se trouve dans les services Office 365 et que la connexion Outlook Web App de l’utilisateur utilise le point de terminaison hérité, l’utilisateur s’authentifiera d’abord sur , puis sur `outlook.office.de` `login.microsoftonline.de` `login.microsoftonline.com` . Une fois la migration terminée, l’utilisateur peut accéder à la nouvelle URL ( ), et il voit uniquement la demande de signature `https://outlook.office365.com` unique attendue. 

## <a name="sharepoint-online"></a>SharePoint Online

Dans SharePoint Online et OneDrive Entreprise, vous pouvez partager des éléments via Outlook. Après avoir enfoncé le Outlook, un lien partageable est créé et envoyé dans un nouveau message dans Outlook Web App.

Le partage d’éléments SharePoint Online et OneDrive Entreprise via Outlook ne fonctionne plus une fois la migration de SharePoint Online terminée. Nous savons qu’il s’agit d’un problème connu. Toutefois, étant donné que Outlook fonctionnalité se trouve dans le chemin de l’annulation, la résolution du problème n’est pas planifiée tant que l’annulation n’est pas déployée.

## <a name="office-services"></a>Office Services

Office Les services en ligne sont accessibles via `office.de` avant et pendant la transition. Après la transition des boîtes aux lettres des utilisateurs vers les services Office 365, les utilisateurs doivent commencer à utiliser les URL Office 365 services de messagerie. À mesure que les charges de travail suivantes migrent vers Office 365, leur interface à partir du portail office.com commence à fonctionner.

Le service (MRU) le plus récemment utilisé dans Office est un passage de Microsoft Cloud Deutschland à Office 365 services globaux, et non à une migration. Seuls les liens de la Office 365 services globaux sont visibles après la migration à partir du portail Office.com. Les liens de la base de données MRU provenant de Microsoft Cloud Deutschland ne sont pas visibles en tant que liaisons MRU dans Office 365 services globaux. Dans Office 365 services globaux, les liaisons de gestion des données sont accessibles uniquement une fois que la migration du client a atteint la phase 9.

## <a name="exchange-online-protection"></a>Exchange Online Protection

- Les fonctionnalités Exchange Online Protection (EOP) principales sont copiées dans une nouvelle région d’Allemagne.
- Office 365 Les utilisateurs du Centre de sécurité et conformité doivent passer à l’utilisation d’URL globales, dans le cadre `https://protection.office.com` de la migration.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

Les clients Skype Entreprise Online existants sont transférés vers Microsoft Teams. Pour plus d’informations, voir [https://aka.ms/SkypeToTeams-Home](/microsoftteams/upgrade-start-here) .

## <a name="office-365-video"></a>Office 365 Video

Office 365 La vidéo a été retirée le 1er mars 2021 et Office 365 Video ne sera pas pris en charge une fois la migration de SharePoint Online vers les nouvelles régions de centres de données allemandes terminée. Le contenu Office 365 vidéo sera migré dans le cadre de la migration de SharePoint Online. Toutefois, les vidéos de Office 365 vidéo ne seront pas lues dans l’interface utilisateur Office 365 vidéo après la migration SharePoint migration. En savoir plus sur la chronologie de la migration Office 365 la transition vidéo vers [Microsoft Stream (classique).](/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline)

## <a name="next-step"></a>Étape suivante

[Comprendre les actions et les impacts des phases de migration](ms-cloud-germany-transition-phases.md)

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)

Transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](/dynamics365/get-started/migrate-data-german-region)
- [Informations sur le programme de migration Power BI](/power-bi/admin/service-admin-migrate-data-germany)
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)
