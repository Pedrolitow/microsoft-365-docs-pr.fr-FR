---
title: Modèle de données d'analyse de l'utilisation de Microsoft 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: reference
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 08c5307c-4a6b-4761-8410-a6c96725760f
description: 'Découvrez comment l’analyse de l’utilisation se connecte à une API et fournit une tendance mensuelle de l’utilisation des différents services Microsoft 365.  '
ms.openlocfilehash: d2d08a46ad6bcf3659c78a381ce20d99ea805ac7
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42253546"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Modèle de données d'analyse de l'utilisation de Microsoft 365

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Données pour les tables d’analyse de l’utilisation de Microsoft 365

L’analyse de l’utilisation de Microsoft 365 se connecte à une API qui expose un modèle de données multidimensionnelles. The APIs are in preview and can be accessed at `https://reports.office.com/pbi/v1.0/\<tenantid\>` (replace the \<tenant id\> with your tenant GUID). 
  
> [!NOTE]
> Pour plus d’informations, consultez la rubrique [utilisation des rapports d’utilisation de microsoft 365 dans Microsoft Graph](https://go.microsoft.com/fwlink/p/?linkid=864336). 
  
Cette API fournit des informations sur la tendance mensuelle de l’utilisation des différents services Microsoft 365. Pour connaître les données exactes renvoyées par l'API, reportez-vous à la table de la section suivante.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Tables de données renvoyées par l’API de création de rapports Microsoft 365

|**Nom de la table**|**Informations contenues dans la table**|**Plage de dates**|
|:-----|:-----|:-----|
|Utilisation du produit par les locataires  <br/> |Contient le nombre total mensuel d'utilisateurs actifs activés, d'utilisateurs conservés au fil des mois, de nouveaux utilisateurs et d'utilisateurs actifs cumulés.  <br/> |Contient des données mensuelles agrégées pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Activité produit des locataires  <br/> |Contient le nombre total mensuel d'activités et d'utilisateurs actifs ayant accompli des activités diverses à l'aide des produits.  <br/> Voir [Définition d'un utilisateur actif](active-user-in-usage-reports.md) pour plus d'informations sur les activités produit renvoyées dans cette table de données.  <br/> |Contient des données mensuelles agrégées pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Licences Office des locataires  <br/> |Contient des données sur le nombre d'abonnements Microsoft Office attribués à des utilisateurs.  <br/> |Contient des données d'état de fin de mois pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Utilisation des boîtes aux lettres par les locataires  <br/> |Contient des données relatives aux boîtes lettres des utilisateurs : nombre total de boîtes aux lettres et utilisation de l'espace de stockage.  <br/> |Contient des données d'état de fin de mois pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Utilisation du client par les locataires  <br/> |Contient des données sur le nombre d'utilisateurs qui utilisent activement un client ou des appareils spécifiques pour se connecter à Exchange Online, Skype Entreprise et Yammer.  <br/> |Contient des données mensuelles agrégées pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Utilisation de SharePoint Online par les locataires  <br/> |Contient des données sur les sites SharePoint. Celles-ci couvrent les sites d'équipe ou les sites de groupe, avec notamment le nombre total de sites, le nombre de documents stockés sur un site, le nombre de fichiers par type d'activité et l'espace de stockage utilisé.  <br/> |Contient des données d'état de fin de mois pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Utilisation de OneDrive Entreprise par les locataires  <br/> |Contient des données sur les comptes OneDrive, comme le nombre de comptes, le nombre de documents stockés sur les différents comptes OneDrive, l'espace de stockage utilisé et le nombre de fichiers par type d'activité.  <br/> |Contient des données d'état de fin de mois pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Utilisation de groupes Microsoft 365 de client  <br/> |Contient des données sur l’utilisation des groupes Microsoft 365, notamment la boîte aux lettres, SharePoint et Yammer.  <br/> |Contient des données d'état de fin de mois pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Activation d'Office par les locataires  <br/> |Contient des données sur le nombre d'activations d'abonnements Office, le nombre d'activations par appareil (Android/iOS/Mac/PC) et les activations par plan de service (par exemple, Office ProPlus, Visio, Project).  <br/> |Contient des données d'état de fin de mois pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|État utilisateur  <br/> |Contient des métadonnées sur les utilisateurs, comme le nom d'affichage, les produits attribués, l'emplacement, le service, le titre et la société. Ces données concernent les utilisateurs auxquels une licence a été attribuée au cours du mois complet écoulé. Chaque utilisateur est désigné par un identifiant utilisateur unique.  <br/> |Ces données concernent les utilisateurs qui disposaient d'une licence au cours du mois complet écoulé.  <br/> |
|Activité utilisateur  <br/> |Contient des informations par utilisateur sur les activités effectuées par les utilisateurs sous licence.  <br/> Voir [Définition d'un utilisateur actif](active-user-in-usage-reports.md) pour plus d'informations sur les activités produit renvoyées dans cette table de données.  <br/> |Ces données concernent les utilisateurs ayant effectué une activité au cours du mois complet écoulé, tous services confondus.  <br/> |
   
Développez les sections suivantes pour afficher des informations détaillées sur chaque table de données.
  
### <a name="data-table---user-state"></a>Table de données - État utilisateur

Cette table fournit des détails sur tous les utilisateurs qui disposaient d'une licence au cours du mois complet écoulé. Elle affiche des données provenant d'Azure Active Directory.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|UserId  <br/> |Identifiant utilisateur unique qui représente un utilisateur et permet de l'associer à d'autres tables de données au sein du jeu de données.  <br/> |
|Timeframe  <br/> |Mois correspondant aux données de cette table.  <br/> |
|UPN  <br/> |Nom d'utilisateur principal unique qui identifie l'utilisateur afin de pouvoir l'associer à d'autres sources de données externes.  <br/> |
|DisplayName  <br/> |Nom d'affichage de l'utilisateur.  <br/> |
|IDType  <br/> |Le type d’ID est défini sur 1 si l’utilisateur est un utilisateur de Yammer qui se connecte à l’aide de son ID Yammer ou 0 s’il se connecte à Yammer à l’aide de son ID Microsoft 365.  <br/> La valeur est 1 pour indiquer que les utilisateurs se connectent à Yammer avec leur ID Yammer et non avec leur ID Microsoft 365  <br/> |
|HasLicenseEXO  <br/> |Valeur définie sur True si l'utilisateur dispose d'une licence et est activé pour utiliser Exchange.  <br/> |
|HasLicenseODB  <br/> |Valeur définie sur True si l'utilisateur dispose d'une licence et est activé pour utiliser OneDrive Entreprise.  <br/> |
|HasLicenseSPO  <br/> |Valeur définie sur True si l'utilisateur dispose d'une licence et est activé pour utiliser SharePoint Online.  <br/> |
|HasLicenseYAM  <br/> |Valeur définie sur True si l'utilisateur dispose d'une licence et est activé pour utiliser Yammer.  <br/> |
|HasLicenseSFB  <br/> |Valeur définie sur True si l'utilisateur dispose d'une licence et est activé pour utiliser Skype Entreprise.  <br/> |
|HasLicenseTeams  <br/> |Valeur définie sur true si l’utilisateur reçoit une licence et permet d’utiliser Microsoft Teams.  <br/> |
|Company  <br/> |Données Azure Active Directory relatives à la société de l'utilisateur.  <br/> |
|Department  <br/> |Données Azure Active Directory relatives au service de l'utilisateur.  <br/> |
|LocationCity  <br/> |Données Azure Active Directory relatives à la ville de l'utilisateur.  <br/> |
|LocationCountry  <br/> |Données Azure Active Directory relatives au pays de l'utilisateur.  <br/> |
|LocationState  <br/> |Données Azure Active Directory relatives à l'État de l'utilisateur.  <br/> |
|LocationOffice  <br/> |Bureau de l'utilisateur.  <br/> |
|Title  <br/> |Données Azure Active Directory relatives au titre de l'utilisateur.  <br/> |
|Deleted  <br/> |True si l’utilisateur a été supprimé de Microsoft 365 dans ce mois dernier complet.  <br/> |
|DeletedDate  <br/> |Date à laquelle l’utilisateur a été supprimé de Microsoft 365.  <br/> |
|YAM_State  <br/> |État de l'utilisateur dans le système Yammer (actif, supprimé ou suspendu).  <br/> |
|YAM_ActivationDate  <br/> |Date à laquelle l'utilisateur est devenu actif dans Yammer.  <br/> |
|YAM_DeletionDate  <br/> |Date à laquelle l'utilisateur a été supprimé dans Yammer.  <br/> |
|YAM_SuspensionDate  <br/> |Date à laquelle l'utilisateur a été suspendu dans Yammer.  <br/> |
   
### <a name="data-table---user-activity"></a>Table de données - Activité utilisateur

Cette table contient des données sur l'activité effectuée par chaque utilisateur au cours du mois précédent, tous services confondus.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|UserID  <br/> |Identifiant utilisateur unique qui représente un utilisateur et permet de l'associer à d'autres tables de données au sein du jeu de données.  <br/> |
|IDType  <br/> |Le type d’ID est défini sur 1 si l’utilisateur est un utilisateur de Yammer qui se connecte à l’aide de son ID Yammer ou 0 s’il se connecte à Yammer à l’aide de son ID Microsoft 365.  <br/> La valeur est 1 pour indiquer que les utilisateurs se connectent à Yammer avec leur ID Yammer et non avec leur ID Microsoft 365  <br/> |
|Timeframe  <br/> |Mois correspondant aux données de cette table.  <br/> |
|EXO_EmailSent  <br/> |Nombre d'e-mails envoyés.  <br/> |
|EXO_EmailReceived  <br/> |Nombre d'e-mails reçus.  <br/> |
|EXO_EmailRead  <br/> |Nombre d'activités de lecture d'e-mail effectuées par l'utilisateur. Il peut s'agir de la lecture d'un même e-mail à plusieurs reprises ou de la lecture d'un e-mail reçu depuis un certain temps.  <br/> |
|EXO_AppointmentCreated  <br/> |Nombre de rendez-vous créés.  <br/> |
|EXO_MeetingAccepted  <br/> |Nombre de réunions acceptées.  <br/> |
|EXO_MeetingCancelled  <br/> |Nombre de réunions annulées.  <br/> |
|EXO_MeetingDeclined  <br/> |Nombre de réunions refusées.  <br/> |
|EXO_MeetingSent  <br/> |Nombre de réunions envoyées.  <br/> |
|ODB_FileViewedModified  <br/> |Nombre de fichiers avec lesquels l'utilisateur a interagi (créations, mises à jour, suppressions, affichages, téléchargements, etc.), toutes instances de OneDrive Entreprise confondues.  <br/> |
|ODB_FileSynched  <br/> |Nombre de fichiers synchronisés par l'utilisateur, toutes instances de OneDrive Entreprise confondues.  <br/> |
|ODB_FileSharedInternally  <br/> |Nombre de fichiers partagés en interne par l’utilisateur à partir de n’importe quelle instance OneDrive entreprise, ou avec des utilisateurs appartenant à des groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|ODB_FileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l'utilisateur, toutes instances de OneDrive Entreprise confondues.  <br/> |
|ODB_AccessByOwner  <br/> |Nombre de fichiers résidant dans l'espace OneDrive Entreprise de l'utilisateur et avec lesquels il a interagi.  <br/> |
|ODB_AccessOthers  <br/> |Nombre de fichiers résidant dans l'espace OneDrive Entreprise d'un tiers et avec lesquels l'utilisateur a interagi.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Nombre de fichiers avec lesquels l'utilisateur a interagi, tous sites de groupe confondus.  <br/> |
|SPO_GroupFileSynched  <br/> |Nombre de fichiers synchronisés par l'utilisateur, tous sites de groupe confondus.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Le nombre de fichiers qui ont été partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l'utilisateur, tous sites de groupe confondus.  <br/> |
|SPO_GroupAccessByOwner  <br/> |Nombre de fichiers résidant sur un site de groupe appartenant à l'utilisateur et avec lesquels il a interagi.  <br/> |
|SPO_GroupAccessByOthers  <br/> |Nombre de fichiers résidant sur un site de groupe appartenant à un tiers et avec lesquels l'utilisateur a interagi.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Nombre de fichiers avec lesquels cet utilisateur a interagi sur un autre site.  <br/> |
|SPO_OtherFileSynched  <br/> |Nombre de fichiers synchronisés par l’utilisateur à partir de n’importe quel autre site.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Nombre de fichiers partagés en interne par l’utilisateur à partir de n’importe quel autre site, ou avec des utilisateurs appartenant à des groupes (qui peuvent inclure des utilisateurs externes). <br/> |
|SPO_OtherFileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l’utilisateur à partir de n’importe quel autre site.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi, qui se trouve sur un autre site dont ils sont propriétaires.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Nombre de sites auxquels l’utilisateur a interagi avec qui réside sur un autre site propriétaire.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Nombre de fichiers avec lesquels l'utilisateur a interagi, tous sites d'équipe confondus.  <br/> |
|SPO_TeamFileSynched  <br/> |Nombre de fichiers synchronisés par l'utilisateur, tous sites d'équipe confondus.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Nombre de fichiers partagés en interne par l’utilisateur à partir de n’importe quel site d’équipe, ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l'utilisateur, tous sites d'équipe confondus.  <br/> |
|SPO_TeamAccessByOwner  <br/> |Nombre de fichiers résidant sur un site d'équipe appartenant à l'utilisateur et avec lesquels il a interagi.  <br/> |
|SPO_TeamAccessByOthers  <br/> |Nombre de fichiers résidant sur un site d'équipe appartenant à un tiers et avec lesquels l'utilisateur a interagi.  <br/> |
|Teams_ChatMessages  <br/> |Nombre de messages de conversation envoyés.  <br/> |
|Teams_ChannelMessage  <br/> |Nombre de messages publiés sur des canaux.  <br/> |
|Teams_CallParticipate  <br/> |Nombre d’appels auxquels l’utilisateur a participé.  <br/> |
|Teams_MeetingParticipate  <br/> |Nombre de réunions auxquelles l’utilisateur a rejoint.  <br/> |
|Teams_HasOtherAction  <br/> |Valeur booléenne si l’utilisateur a effectué d’autres actions dans Microsoft Teams.  <br/> |
|YAM_MessagePost  <br/> |Nombre de messages Yammer publiés par l'utilisateur.  <br/> |
|YAM_MessageLiked  <br/> |Nombre de messages Yammer aimés par l'utilisateur.  <br/> |
|YAM_MessageRead  <br/> |Nombre de messages Yammer lus par l'utilisateur.  <br/> |
|SFB_P2PSummary  <br/> |Nombre de sessions P2P auxquelles l'utilisateur a participé.  <br/> |
|SFB_ConfOrgSummary  <br/> |Nombre de sessions de conférence organisées par l'utilisateur.  <br/> |
|SFB_ConfPartSummary  <br/> |Nombre de sessions de conférence auxquelles l'utilisateur a participé.  <br/> |
   
### <a name="data-table---tenant-product-usage"></a>Table de données - Utilisation du produit par les locataires

Cette table contient les données relatives à l’adoption du mois sur le mois en termes d’activation, d’activation, de retour et de la première fois pour chaque produit de Microsoft 365. La valeur Microsoft 365 représente une utilisation active dans l’un des produits.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|Product  <br/> |Nom des produits pour lesquels les informations d'utilisation sont synthétisées. La valeur Microsoft 365 dans la colonne Product représente l’activité de tous les produits  <br/> |
|Timeframe  <br/> |Mois. La colonne contient une ligne par produit et par mois pour les 12 derniers mois, mois en cours compris.  <br/> |
|EnabledUsers  <br/> |Nombre d'utilisateurs activés pour utiliser le produit au cours de la période concernée. Si un utilisateur n'a été activé qu'une partie du mois, il est malgré tout pris en compte.  <br/> |
|ActiveUsers  <br/> |Nombre d'utilisateurs ayant effectué une activité intentionnelle à l'aide du produit au cours de la période concernée.  <br/> Un utilisateur est comptabilisé comme actif au cours d'un mois donné s'il a effectué une des activités clés à l'aide du produit. Les activités clés sont disponibles dans la table **Activité produit des locataires**.  <br/> |
|CumulativeActiveUsers  <br/> |Nombre d'utilisateurs activés pour utiliser un produit et ayant utilisé ce produit jusqu'au mois pris en compte au moins une fois depuis le début de la collecte des données dans le nouveau système d'utilisation.  <br/> |
|MoMReturningUsers  <br/> |Nombre d'utilisateurs ayant été actifs au cours du mois pris en compte et qui étaient également actifs au cours du mois précédent.  <br/> |
|FirstTimeUsers  <br/> |Nombre d'utilisateurs devenus actifs au cours de la période prise en compte pour la première fois depuis la collecte des données dans le nouveau système d'utilisation.  <br/> Un utilisateur est comptabilisé comme nouvel utilisateur au cours d'un mois donné si une activité de celui-ci est détectée pour la première fois depuis le début de la collecte des données dans le nouveau système de création de rapports. Une fois comptabilisé comme nouvel utilisateur, il ne sera jamais recomptabilisé comme tel, même si l'écart entre deux activités est très important.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Table de données - Activité produit des locataires

Cette table contient le nombre total mensuel d'activités et d'utilisateurs actifs ayant accompli des activités diverses à l'aide des produits.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|Timeframe  <br/> |Mois. La colonne contient une ligne par produit et par mois pour les 12 derniers mois, mois en cours compris.  <br/> |
|Product  <br/> |Nom du produit dans Microsoft 365 pour lequel les données d’utilisation sont disponibles.  <br/> |
|Activity  <br/> |Nom de l'activité liée à un produit, utilisé pour présenter l'utilisation active du produit.  <br/> |
|ActivityCount  <br/> |Nombre total d'actions comptabilisées pour chaque activité effectuée à l'aide du produit, tous utilisateurs actifs confondus.  <br/> **Remarque :** pour les activités SharePoint Online et OneDrive Entreprise, cette valeur représente le nombre de documents distincts avec lesquels les utilisateurs ont interagi.  <br/> |
|ActiveUserCount  <br/> |Nombre d'utilisateurs ayant effectué une activité à l'aide du produit.  <br/> |
|TotalDurationInMinute  <br/> |Nombre de minutes d'utilisation d'une session audio ou vidéo dans le cadre d'une activité Skype Entreprise applicable, tous utilisateurs actifs confondus.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Table de données - Utilisation des boîtes aux lettres par les locataires

Cette table contient des données de synthèse sur tous les utilisateurs Exchange Online sous licence qui disposent d'une boîte aux lettres utilisateur. Elle contient un état de fin de mois englobant toutes les boîtes aux lettres utilisateur. Les données de cette table ne s'additionnent pas au fil des mois. Dans cette table, les données du mois précédent représentent l'état le plus récent.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|TotalMailboxes  <br/> |Nombre de boîtes aux lettres utilisateur pour l’abonnement Microsoft 365.  <br/> |
|IssueWarningQuota  <br/> |Quota total au-delà duquel un avertissement est envoyé à toutes les boîtes aux lettres utilisateur.  <br/> |
|ProhibitSendQuota  <br/> |Quota total au-delà duquel une interdiction d'envoi s'applique à toutes les boîtes aux lettres utilisateur.  <br/> |
|ProhibitSendReceiveQuota  <br/> |Quota total au-delà duquel une interdiction de réception s'applique à toutes les boîtes aux lettres utilisateur.  <br/> |
|TotalItemBytes  <br/> |Espace de stockage utilisé par toutes les boîtes aux lettres utilisateur, en octets.  <br/> |
|MailboxesNoWarning  <br/> |Nombre de boîtes aux lettres utilisateur n'ayant pas atteint la limite de stockage déclenchant un avertissement.  <br/> |
|MailboxesIssueWarning  <br/> |Nombre de boîtes aux lettres utilisateur ayant atteint le quota de stockage et auxquelles un avertissement a été envoyé.  <br/> |
|MailboxesExceedSendQuota  <br/> |Nombre de boîtes aux lettres utilisateur ayant dépassé le quota d'envoi.  <br/> |
|MailboxesExceedSendReceiveQuota  <br/> |Nombre de boîtes aux lettres utilisateur ayant dépassé le quota d'envoi ou de réception.  <br/> |
|DeletedMailboxes  <br/> |Nombre de boîtes aux lettres utilisateur supprimées au cours de la période prise en compte.  <br/> |
|Timeframe  <br/> |Mois.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Table de données - Utilisation du client par les locataires

Cette table fournit des données de synthèse mensuelles sur les clients utilisés par les utilisateurs pour se connecter à Exchange Online, Skype Entreprise et Yammer. Elle ne contient pas encore de données d'utilisation client pour SharePoint Online et OneDrive Entreprise.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|Produit  <br/> |Nom du produit dans Microsoft 365 pour lequel les données d’utilisation du client sont disponibles.  <br/> |
|Identifi  <br/> |Nom de chaque appareil utilisé pour se connecter au produit.  <br/> |
|Nombre  <br/> |Nombre d'utilisateurs ayant utilisé chacun des clients pour chaque produit.  <br/> |
|Timeframe  <br/> |Mois  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Table de données - Utilisation de SharePoint Online par les locataires

Cette table contient des données de synthèse mensuelles sur l'utilisation ou l'activité des sites SharePoint Online. Elle couvre uniquement les sites d'équipe et les sites de groupe. L'état de fin de mois des sites SharePoint Online est représenté dans cette colonne. Par exemple, si un utilisateur a créé 5 documents utilisant 10 Mo d'espace de stockage, puis a supprimé certains fichiers et en a ajouté de nouveaux pour obtenir en fin de mois un total de 7 fichiers utilisant 5 Mo d'espace de stockage, la valeur représentée dans cette table est l'état de fin de mois. Cette table est masquée afin d'éviter de comptabiliser deux fois les agrégations, et elle est utilisée comme source pour créer deux tables de référence.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|SiteType  <br/> |Valeur du type de site (tout/équipe/groupe) (tout représentant l'un ou l'autre de ces 2 types de sites).  <br/> |
|TotalSites  <br/> |Nombre de sites qui existaient à la fin de la période prise en compte.  <br/> |
|DocumentCount  <br/> |Nombre total de documents qui existaient sur le site à la fin de la période prise en compte.  <br/> |
|Dipland  <br/> |Somme de l'espace de stockage total utilisé à la fin de la période prise en compte, tous sites confondus.  <br/> |
|ActivityType  <br/> |Nombre de sites ayant enregistré les différents types d'activité de fichier (tout/fichiers actifs/fichiers partagés en externe/fichiers partagés en interne/fichiers synchronisés).  <br/> Tout représente une activité de fichier quelconque.  <br/> |
|SitesWithOwnerActivities  <br/> |Nombre de sites actifs, où le propriétaire a effectué une activité de fichier particulière sur son propre site.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Somme des sites actifs du mois, où des utilisateurs autres que le propriétaire ont effectué une activité de fichier particulière.  <br/> |
|ActivityTotalSites  <br/> |Nombre de sites ayant enregistré de l'activité au cours de la période prise en compte. Si un site a enregistré de l'activité plus tôt au cours de la période et qu'il a été supprimé à la fin de la période, il est malgré tout comptabilisé dans le total des sites actifs correspondant à cette période.  <br/> |
|Timeframe  <br/> |Cette colonne comporte une date. Elle est utilisée en tant que relation multiunivoque dans la table Calendrier.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Table de données-utilisation de OneDrive client

Cette table contient des données sur les comptes OneDrive, comme le nombre de comptes, le nombre de documents stockés sur les différents comptes OneDrive, l'espace de stockage utilisé et le nombre de fichiers par type d'activité. L'état de fin de mois des comptes OneDrive Entreprise y est représenté. Par exemple, si un utilisateur a créé 5 documents utilisant 10 Mo d'espace de stockage, puis a supprimé certains fichiers et en a ajouté de nouveaux pour obtenir en fin de mois un total de 7 fichiers utilisant 5 Mo d'espace de stockage, la valeur de fin de mois est représentée dans cette table à la fin du mois.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|SiteType  <br/> |La valeur est « OneDrive ».  <br/> |
|TotalSites  <br/> |Nombre de comptes OneDrive Entreprise qui existaient à la fin de la période prise en compte.  <br/> |
|DocumentCount  <br/> |Nombre total de documents qui existaient à la fin de la période prise en compte, tous comptes OneDrive Entreprise confondus.  <br/> |
|Dipland  <br/> |Somme de l'espace de stockage total utilisé à la fin de la période prise en compte, tous comptes OneDrive confondus.  <br/> |
|ActivityType  <br/> |Nombre de comptes ayant enregistré les différents types d'activité de fichier (tout/fichiers actifs/fichiers partagés en externe/fichiers partagés en interne/fichiers synchronisés).  <br/> Tout représente une activité de fichier quelconque.  <br/> |
|SitesWithOwnerActivities  <br/> |Nombre de comptes OneDrive Entreprise actifs, où le propriétaire a effectué une activité de fichier particulière sur son propre compte.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Nombre de comptes OneDrive Entreprise, où des utilisateurs autres que le propriétaire ont effectué une activité de fichier particulière.  <br/> |
|ActivityTotalSites  <br/> |Nombre de comptes OneDrive Entreprise ayant enregistré de l'activité au cours de la période prise en compte. Si un compte OneDrive Entreprise a enregistré de l'activité plus tôt au cours de la période et qu'il a été supprimé à la fin de la période, il est malgré tout comptabilisé dans le total des comptes OneDrive Entreprise actifs correspondant à cette période.  <br/> |
|Timeframe  <br/> |Cette colonne comporte une date. Elle est utilisée en tant que relation multiunivoque dans la table Calendrier.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Table de données-utilisation des groupes Microsoft 365 de clients

Ce tableau fournit des données sur la façon dont les groupes Microsoft 365 sont utilisés dans l’organisation.
  
****

|**Nom de colonne**|**Description de la colonne**|
|:-----|:-----|
|Janvier  <br/> |Mois. La colonne contient une ligne par produit et par mois pour les 12 derniers mois, mois en cours compris.  <br/> |
|GroupType  <br/> |Type de groupe (privé/public/any).  <br/> |
|TotalGroups  <br/> |Nombre de groupes dans chaque type de groupe.  <br/> |
|ActiveGroups  <br/> |Nombre de groupes actifs.  <br/> |
|MBX_TotalGroups  <br/> |Nombre de groupes de boîtes aux lettres.  <br/> |
|MBX_ActiveGroups  <br/> |Nombre de groupes de boîtes aux lettres actifs.  <br/> |
|MBX_TotalActivities  <br/> |Nombre d’activités de boîte aux lettres.  <br/> |
|MBX_TotalItems  <br/> |Nombre d’éléments de boîte aux lettres.  <br/> |
|MBX_StorageUsed  <br/> |Quantité de stockage de boîtes aux lettres utilisée.  <br/> |
|SPO_TotalGroups  <br/> |Nombre de groupes SharePoint.  <br/> |
|SPO_ActiveGroups  <br/> |Nombre de groupes SharePoint actifs.  <br/> |
|SPO_FileAccessedActiveGroups  <br/> |Nombre de groupes SharePoint dont les activités de fichier sont consultées.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Nombre de groupes SharePoint qui ont des activités synchronisées entre les fichiers.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Nombre de groupes SharePoint qui ont des activités partagées en interne ou avec des groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Nombre de groupes SharePoint qui ont des activités externes partagées.  <br/> |
|SPO_TotalActivities  <br/> |Nombre d’activités SharePoint.  <br/> |
|SPO_FileAccessedActivities  <br/> |Nombre d’activités d’accès aux fichiers SharePoint.  <br/> |
|SPO_FileSyncedActivities  <br/> |Nombre d’activités synchronisées de fichiers SharePoint.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Nombre d’activités partagées de fichiers SharePoint en interne ou avec des groupes (qui peuvent inclure des membres externes).  <br/> |
|SPO_FileSharedExternallyActivities  <br/> |Nombre d’activités externes partagées dans un fichier SharePoint.  <br/> |
|SPO_TotalFiles  <br/> |Nombre de fichiers SharePoint.  <br/> |
|SPO_ActiveFiles  <br/> |Nombre de fichiers SharePoint actifs.  <br/> |
|SPO_StorageUsed  <br/> |Quantité de stockage SharePoint utilisée.  <br/> |
|YAM_TotalGroups  <br/> |Nombre de groupes Yammer.  <br/> |
|YAM_ActiveGroups  <br/> |Nombre de groupes Yammer actifs.  <br/> |
|YAM_LikedActiveGroups  <br/> |Nombre de groupes Yammer ayant des activités similaires.  <br/> |
|YAM_PostedActiveGroups  <br/> |Nombre de groupes Yammer ayant des activités post.  <br/> |
|YAM_ReadActiveGroups  <br/> |Nombre de groupes Yammer qui ont des activités de lecture.  <br/> |
|YAM_TotalActivities  <br/> |Nombre d’activités Yammer.  <br/> |
|YAM_LikedActivities  <br/> |Nombre d’activités Yammer.  <br/> |
|YAM_PostedActivties  <br/> |Nombre d’activités de publication Yammer.  <br/> |
|YAM_ReadActivites  <br/> |Nombre d’activités de lecture Yammer.  <br/> |
   
### <a name="data-table---tenant-office-activation"></a>Table de données - Activation d'Office par les locataires

La table contient des données sur le nombre d'activations d'abonnements Office, tous plans de services confondus (par exemple, Office ProPlus, Visio, Project). Elle fournit également des données sur le nombre d'activations par appareil (Android/iOS/Mac/PC).
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|ServicePlanName  <br/> |Liste des noms de plan de service et nombre d'activations par appareil, comme illustré par les colonnes ci-dessous.  <br/> |
|TotalEnabled  <br/> |Nombre d'utilisateurs activés par nom de plan de service à la fin de la période prise en compte.  <br/> |
|TotalActivatedUsers  <br/> |Nombre d'utilisateurs ayant activé chaque plan de service à la fin de la période prise en compte.  <br/> |
|AndroidCount  <br/> |Nombre d'activations d'un appareil Android par plan de service à la fin de la période prise en compte.  <br/> |
|iOSCount  <br/> |Nombre d'activations d'un appareil iOS par plan de service à la fin de la période prise en compte.  <br/> |
|MacCount  <br/> |Nombre d'activations d'un appareil MAC par plan de service à la fin de la période prise en compte.  <br/> |
|PcCount  <br/> |Nombre d'activations d'un PC par plan de service à la fin de la période prise en compte.  <br/> |
|WinRtCount  <br/> |Nombre d'activations d'un appareil Windows Mobile par plan de service à la fin de la période prise en compte.  <br/> |
|Timeframe  <br/> |Cette colonne comporte une date. Elle est utilisée en tant que relation multiunivoque dans la table Calendrier.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   

