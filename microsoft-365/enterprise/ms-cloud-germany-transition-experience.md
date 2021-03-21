---
title: Nouveautés de la migration vers les services Office 365 dans les nouvelles régions de centres de données allemandes
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
description: 'Résumé : Comprendre ce qui a changé pour passer de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemande.'
ms.openlocfilehash: cadad596011bbcde02b61f01e949c93a5a62a1c3
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50923825"
---
# <a name="what-has-changed-for-the-migration-to-office-365-services-in-the-new-german-datacenter-regions"></a>Nouveautés de la migration vers les services Office 365 dans les nouvelles régions de centres de données allemandes

Les migrations de clients sont conçues pour avoir un impact minimal sur les administrateurs et les utilisateurs. Toutefois, il existe des facteurs à prendre en compte pour chaque charge de travail. Consultez les sections suivantes pour mieux comprendre l’expérience de migration des charges de travail.

Voici les principales différences entre les services Microsoft Cloud Deutschland et Office 365 dans les nouvelles régions de centres de données allemandes.

| Catégorie | Microsoft Cloud Deutschland (Microsoft Cloud Deutschland) | Services Office 365 dans les nouvelles régions de centre de données allemandes |
|:-------|:-----|:-------|
| Services Microsoft 365 disponibles pour un abonnement avec un seul client Office 365 | 15 services | 29 services <br><br> Pour plus d’informations, voir Quelle est la disponibilité des services entre les différentes offres de [services cloud Office 365 ?](ms-cloud-germany-transition.md#serv-avail) |
| Nouvelles fonctionnalités | Aucune nouvelle fonctionnalité n’est disponible. | De nouvelles fonctionnalités seront disponibles conformément aux services Office 365. |
| Administrateur de données | Oui | Non |
| Collaboration entre clients Office 365 du monde entier | Non | Oui |
| Résidence des données client | Les données client sont stockées uniquement dans les centres de données allemands. | Microsoft stockera les données client suivantes au repos exclusivement en Allemagne : <ul><li> Contenu de boîte aux lettres Exchange Online (corps du message électronique, entrées de calendrier et contenu des pièces jointes) </li><li> Contenu du site SharePoint Online et fichiers stockés dans ce site, et fichiers téléchargés vers OneDrive Entreprise </li></ul> |
| Conditions applicables | [Conditions d’accès aux](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) services en ligne avec ce [supplément](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=64) | [Conditions d’utilisation d’Online Services](https://www.microsoftvolumelicensing.com/DocumentSearch.aspx?Mode=3&DocumentTypeId=46) |
||||

## <a name="azure-active-directory"></a>Azure Active Directory

Ce qui ne change pas :

- Le domaine initial du client (par exemple) avec un ID de client (GUID) et des domaines `contoso.onmicrosoft.de` personnalisés est persistant après la migration. 

- Les demandes d’authentification pour les ressources migrées vers les services Office 365 sont accordées par le service d’authentification Azure des services Office 365 ( `login.microsoftonline.com` ). Pendant la migration, les ressources qui restent dans Office 365 Germany sont authentifiées par le service Azure Allemagne existant ( `login.microsoftonline.de` ).

Remarques à prendre en compte :

- Pour les comptes de domaine géré, une fois la copie du client Azure Active Directory (Azure AD) initial terminée (qui est la première étape de la migration d’Azure AD vers le service Azure AD des services Office 365), les modifications de mot de passe, les modifications de réinitialisation de mot de passe en libre-service (SSPR) et les réinitialisations de mot de passe par les administrateurs doivent être réalisées à partir des portails de service Office 365. Les demandes de mise à jour des mots de passe à partir du service Allemagne ne aboutront pas à ce stade, car le client Azure AD a été migré vers les services Office 365. Les réinitialisations des mots de passe de domaine fédéré ne sont pas affectées, car elles sont effectuées dans l’annuaire local.

- Les sign-ins Azure sont présentées dans le portail où l’utilisateur tente d’y accéder. Les journaux d’audit sont disponibles uniquement à partir du point de terminaison des services Office 365 après la transition. Avant la migration jusqu’à la fin de la migration, vous devez enregistrer les journaux de connexion et d’audit à partir du portail Microsoft Cloud Deutschland.

- Les réinitialisations de mot de passe, les modifications de mot de passe, la réinitialisation de mot de passe par un administrateur pour les organisations gérées (qui n’utilisent pas les services de fédération Active Directory) doivent être effectuées via le portail des services Office 365. Les tentatives des utilisateurs qui accèdent aux portails Microsoft Cloud Deutschland pour réinitialiser les mots de passe échouent.

- Les demandes des personnes soumises au Règlement général sur la protection des données (R GDPR) sont exécutées à partir du portail d’administration Azure des services Office 365 pour les demandes futures. Toutes les données de diagnostic héritées ou non client résidant dans Microsoft Cloud Deutschland sont supprimées au moins 30 jours.

## <a name="subscriptions--licenses"></a>Abonnements & licences

- Les abonnements Office 365 et Dynamics de Microsoft Cloud Deutschland sont transitionés vers la région allemande avec le déplacement d’Azure AD. L’organisation est ensuite mise à jour pour refléter les nouveaux abonnements aux services Office 365. Pendant le bref processus de transfert d’abonnement, les modifications apportées aux abonnements sont bloquées.

- Au cours de la transition du client vers les services Office 365, ses abonnements et licences propres à l’Allemagne sont normalisés avec les nouvelles offres de services Office 365. Les abonnements aux services Office 365 correspondants sont achetés pour les abonnements transférés en Allemagne. Des licences de services Office 365 seront attribuées aux utilisateurs qui ont des licences En Allemagne. À la fin de l’exécution, les abonnements hérités en Allemagne sont annulés et supprimés du client de services Office 365 actuel.

- Après la migration des charges de travail individuelles, des fonctionnalités supplémentaires sont disponibles via les services Office 365 (tels que Le Planificateur Microsoft et Microsoft Flow) en raison des nouveaux abonnements aux services Office 365. Si cela est approprié pour votre organisation, le client ou l’administrateur de licences peut désactiver les nouveaux plans de service lorsque vous planifiez la gestion des changements afin d’introduire les nouveaux services. Pour obtenir des instructions sur la désactivation des plans de service affectés aux licences des utilisateurs, voir Désactiver l’accès aux [services Microsoft 365](/office365/enterprise/powershell/disable-access-to-services-while-assigning-user-licenses)tout en attribuant des licences utilisateur.

## <a name="exchange-online"></a>Exchange Online

- Les URL des ressources Exchange migrent du point de terminaison hérité d’Allemagne vers le point de terminaison des `outlook.office.de` services Office 365 `outlook.office365.com` après la migration. Vos utilisateurs peuvent accéder à leur boîte aux lettres migrée à l’aide de l’URL héritée jusqu’à la fin de la migration. Les clients doivent migrer les utilisateurs vers la nouvelle URL dès que possible après le début de la migration d’Exchange pour éviter d’affecter le retrait de l’environnement allemand. Les URL des services Office 365 pour les services Outlook deviennent disponibles uniquement après le début de la migration d’Exchange.

- Les boîtes aux lettres sont migrées en tant que processus back-end. Les utilisateurs de votre organisation peuvent se voir dans Microsoft Cloud Deutschland ou dans la région allemande pendant la transition et faire partie de la même organisation Exchange (dans la même liste d’adresses globale).

- Les utilisateurs d’Outlook Web App qui accèdent au service à l’aide d’une URL dans laquelle leur boîte aux lettres ne réside pas voient une invite d’authentification supplémentaire. Par exemple, si la boîte aux lettres de l’utilisateur se trouve dans les services Office 365 et que la connexion Outlook Web App de l’utilisateur utilise le point de terminaison hérité, l’utilisateur s’authentifiera d’abord sur , puis sur `outlook.office.de` `login.microsoftonline.de` `login.microsoftonline.com` . Une fois la migration terminée, l’utilisateur peut accéder à la nouvelle URL ( ), et il voit uniquement la demande de signature `https://outlook.office365.com` unique attendue. 

## <a name="office-services"></a>Office Services

Les services Office Online sont accessibles avant `office.de` et pendant la transition. Après la transition des boîtes aux lettres des utilisateurs vers les services Office 365, les utilisateurs doivent commencer à utiliser les URL des services Office 365. À mesure que les charges de travail suivantes migrent vers les services Office 365, leur interface à partir du portail office.com commence à fonctionner.

## <a name="exchange-online-protection"></a>Exchange Online Protection

- Les fonctionnalités d’Exchange Online Protection (EOP) principales sont copiées dans une nouvelle région d’Allemagne.
- Les utilisateurs du Centre de sécurité et conformité Office 365 doivent passer à l’utilisation d’URL globales, dans le cadre `https://protection.office.com` de la migration.

## <a name="skype-for-business-online"></a>Skype Entreprise Online

Les clients Skype Entreprise Online existants sont transférés vers Microsoft Teams. Pour plus d’informations, voir [https://aka.ms/SkypeToTeams-Home](/microsoftteams/upgrade-start-here) .

## <a name="office-365-video"></a>Office 365 Video

Office 365 Video a été retiré le 1er mars 2021 et Office 365 Video ne sera plus pris en charge une fois la migration de SharePoint Online vers les nouvelles régions de centres de données allemandes terminée. Le contenu d’Office 365 Video sera migré dans le cadre de la migration de SharePoint Online. Toutefois, les vidéos dans Office 365 Video ne seront pas lues dans l’interface utilisateur Office 365 Video après la migration de SharePoint. En savoir plus sur la chronologie de migration sur [la transition d’Office 365 Video vers Microsoft Stream (classique).](/stream/migrate-from-office-365#microsoft-cloud-deutschland-timeline)

## <a name="next-step"></a>Étape suivante

[Comprendre les actions et les impacts des phases de migration](ms-cloud-germany-transition-phases.md)

## <a name="more-information"></a>Informations supplémentaires

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)

Transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](/dynamics365/get-started/migrate-data-german-region)
- [Informations sur le programme de migration Power BI](/power-bi/admin/service-admin-migrate-data-germany)
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)