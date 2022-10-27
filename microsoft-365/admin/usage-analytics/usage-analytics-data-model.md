---
title: Modèle de données d'analyse de l'utilisation de Microsoft 365
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 08c5307c-4a6b-4761-8410-a6c96725760f
description: 'Découvrez comment l’analytique de l’utilisation se connecte à une API et fournit une tendance mensuelle d’utilisation de différents services Microsoft 365.  '
ms.openlocfilehash: 4954b463946ba436afd14390526eefe188447a46
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68730484"
---
# <a name="microsoft-365-usage-analytics-data-model"></a>Modèle de données d'analyse de l'utilisation de Microsoft 365

## <a name="data-for-the-microsoft-365-usage-analytics-tables"></a>Données pour les tables d’analyse de l’utilisation de Microsoft 365

L’analytique de l’utilisation de Microsoft 365 se connecte à une API qui expose un modèle de données multidimensionnel. Les API utilisées par Microsoft 365 Usage Analytics pour générer ses données proviennent des différentes API Graph en disponibilité générale. La fonction de l’API d’analyse de l’utilisation de Microsoft 365 n’est pas en disponibilité générale.
  
> [!NOTE]
> Pour plus d’informations, consultez [Utilisation des rapports d’utilisation de Microsoft 365 dans Microsoft Graph](/graph/api/resources/report). 
  
Cette API fournit des informations sur la tendance mensuelle d’utilisation des différents services Microsoft 365. Pour connaître les données exactes renvoyées par l'API, reportez-vous à la table de la section suivante.
  
## <a name="data-tables-returned-by-the-microsoft-365-reporting-api"></a>Tables de données retournées par l’API de création de rapports Microsoft 365

|**Nom de la table**|**Informations contenues dans la table**|**Plage de dates**|
|:-----|:-----|:-----|
|Utilisation du produit par les locataires  <br/> |Contient les totaux mensuels des utilisateurs actifs et activés, des utilisateurs retenus d’un mois à l’autre, des utilisateurs pour la première fois et des utilisateurs actifs cumulés.  <br/> |Contient des données mensuelles agrégées pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Activité produit des locataires  <br/> |Contient les totaux mensuels des activités et le nombre d’utilisateurs actifs pour différentes activités au sein des produits.  <br/> Voir [Définition d'un utilisateur actif](active-user-in-usage-reports.md) pour plus d'informations sur les activités produit renvoyées dans cette table de données.  <br/> |Contient des données mensuelles agrégées pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Licences Office des locataires  <br/> |Contient des données sur le nombre d'abonnements Microsoft Office attribués à des utilisateurs.  <br/> |Contient des données d’état de fin de mois pour une période de 12 mois propagée, y compris le mois partiel en cours.  <br/> |
|Utilisation des boîtes aux lettres par les locataires  <br/> |Contient des données sur la boîte aux lettres de l’utilisateur, pour le nombre total de boîtes aux lettres et la façon dont le stockage est utilisé.  <br/> |Contient des données d’état de fin de mois pour une période de 12 mois propagée, y compris le mois partiel en cours.  <br/> |
|Utilisation du client par les locataires  <br/> |Contient des données sur le nombre d'utilisateurs qui utilisent activement un client ou des appareils spécifiques pour se connecter à Exchange Online, Skype Entreprise et Yammer.  <br/> |Contient des données mensuelles agrégées pour une période de 12 mois consécutifs, mois en cours compris.  <br/> |
|Utilisation de SharePoint Online par les locataires  <br/> |Contient des données sur les sites SharePoint. Celles-ci couvrent les sites d'équipe ou les sites de groupe, avec notamment le nombre total de sites, le nombre de documents stockés sur un site, le nombre de fichiers par type d'activité et l'espace de stockage utilisé.  <br/> |Contient des données d’état de fin de mois pour une période de 12 mois propagée, y compris le mois partiel en cours.  <br/> |
|Utilisation de OneDrive Entreprise par les locataires  <br/> |Contient des données sur les comptes OneDrive, comme le nombre de comptes, le nombre de documents stockés sur les différents comptes OneDrive, l'espace de stockage utilisé et le nombre de fichiers par type d'activité.  <br/> |Contient des données d’état de fin de mois pour une période de 12 mois propagée, y compris le mois partiel en cours.  <br/> |
|Utilisation du Groupes Microsoft 365 client  <br/> |Contient des données sur Groupes Microsoft 365 utilisation, notamment Mailbox, SharePoint et Yammer.  <br/> |Contient des données d’état de fin de mois pour une période de 12 mois propagée, y compris le mois partiel en cours.  <br/> |
|Activation d'Office par les locataires  <br/> |Contient des données sur le nombre d’activations d’abonnement Office, le nombre d’activations par appareil (Android/iOS/Mac/PC), les activations par plan de service, par exemple, Applications Microsoft 365 pour les grandes entreprises, Visio, Project.  <br/> |Contient des données d’état de fin de mois pour une période de 12 mois propagée, y compris le mois partiel en cours.  <br/> |
|État utilisateur  <br/> |Contient des métadonnées sur les utilisateurs, comme le nom d'affichage, les produits attribués, l'emplacement, le service, le titre et la société. Ces données concernent les utilisateurs auxquels une licence a été attribuée au cours du dernier mois complet. Chaque utilisateur est représenté de manière unique par un ID utilisateur.  <br/> |Ces données concernent les utilisateurs qui disposaient d'une licence au cours du mois complet écoulé.  <br/> |
|Activité utilisateur  <br/> |Contient des informations par utilisateur sur les activités effectuées par les utilisateurs sous licence.  <br/> Voir [Définition d'un utilisateur actif](active-user-in-usage-reports.md) pour plus d'informations sur les activités produit renvoyées dans cette table de données.  <br/> |Ces données concernent les utilisateurs ayant effectué une activité au cours du mois complet écoulé, tous services confondus.  <br/> |
   
Développez les sections suivantes pour afficher des informations détaillées sur chaque table de données.
  
### <a name="data-table---user-state"></a>Table de données - État utilisateur

Ce tableau fournit des détails au niveau utilisateur pour tous les utilisateurs auxquels une licence leur a été attribuée au cours du dernier mois complet. Elle affiche des données provenant d'Azure Active Directory.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|UserId  <br/> |ID utilisateur unique qui représente un utilisateur et permet la jointure avec d’autres tables de données dans le jeu de données.  <br/> |
|Timeframe  <br/> |Mois correspondant aux données de cette table.  <br/> |
|UPN  <br/> |Nom d'utilisateur principal unique qui identifie l'utilisateur afin de pouvoir l'associer à d'autres sources de données externes.  <br/> |
|DisplayName  <br/> |Nom d'affichage de l'utilisateur.  <br/> |
|IDType  <br/> |Le type d’ID est défini sur 1 si l’utilisateur est un utilisateur Yammer qui se connecte à l’aide de son ID Yammer ou 0 s’il se connecte à Yammer à l’aide de son ID Microsoft 365.  <br/> La valeur est 1 pour représenter que cet utilisateur se connecte à Yammer avec son ID Yammer et non son ID Microsoft 365  <br/> |
|HasLicenseEXO  <br/> |Définissez la valeur true si une licence est attribuée à l’utilisateur et qu’il est activé pour utiliser Exchange le dernier jour du mois.  <br/> |
|HasLicenseODB  <br/> |Définissez la valeur true si une licence est attribuée à l’utilisateur et qu’il est autorisé à utiliser OneDrive Entreprise le dernier jour du mois.  <br/> |
|HasLicenseSPO  <br/> |Définissez la valeur true si une licence est attribuée à l’utilisateur et qu’il est autorisé à utiliser SharePoint Online le dernier jour du mois.  <br/> |
|HasLicenseYAM  <br/> |Définissez la valeur true si une licence est attribuée à l’utilisateur et qu’il est activé pour utiliser Yammer le dernier jour du mois.  <br/> |
|HasLicenseSFB  <br/> |Définissez la valeur true si une licence est attribuée à l’utilisateur et qu’il est activé pour utiliser Skype Entreprise le dernier jour du mois.  <br/> |
|HasLicenseTeams  <br/> |Définissez la valeur true si une licence est attribuée à l’utilisateur et qu’il est possible d’utiliser Microsoft Teams le dernier jour du mois.  <br/> |
|Société  <br/> |Données Azure Active Directory relatives à la société de l'utilisateur.  <br/> |
|Department  <br/> |Données Azure Active Directory relatives au service de l'utilisateur.  <br/> |
|LocationCity  <br/> |Données Azure Active Directory relatives à la ville de l'utilisateur.  <br/> |
|LocationCountry  <br/> |Données Azure Active Directory relatives au pays de l'utilisateur.  <br/> |
|LocationState  <br/> |Données Azure Active Directory relatives à l'État de l'utilisateur.  <br/> |
|LocationOffice  <br/> |Bureau de l'utilisateur.  <br/> |
|Title  <br/> |Données Azure Active Directory relatives au titre de l'utilisateur.  <br/> |
|Deleted  <br/> |True si l’utilisateur a été supprimé de Microsoft 365 au cours du dernier mois complet.  <br/> |
|DeletedDate  <br/> |Date à laquelle l’utilisateur a été supprimé de Microsoft 365.  <br/> |
|YAM_State  <br/> |Les états de l’utilisateur dans le système Yammer peuvent être actifs, supprimés ou suspendus.  <br/> |
|YAM_ActivationDate  <br/> |Date à laquelle l'utilisateur est devenu actif dans Yammer.  <br/> |
|YAM_DeletionDate  <br/> |Date à laquelle l'utilisateur a été supprimé dans Yammer.  <br/> |
|YAM_SuspensionDate  <br/> |Date à laquelle l'utilisateur a été suspendu dans Yammer.  <br/> |
   
### <a name="data-table---user-activity"></a>Table de données - Activité utilisateur

Cette table contient des données sur l'activité effectuée par chaque utilisateur au cours du mois précédent, tous services confondus.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|UserID  <br/> |ID utilisateur unique qui représente un utilisateur et permet la jointure avec d’autres tables de données dans le jeu de données.  <br/> |
|IDType  <br/> |Le type d’ID est défini sur 1 si l’utilisateur est un utilisateur Yammer qui se connecte à l’aide de son ID Yammer ou 0 s’il se connecte à Yammer à l’aide de son ID Microsoft 365.  <br/> La valeur est 1 pour représenter que cet utilisateur se connecte à Yammer avec son ID Yammer et non son ID Microsoft 365  <br/> |
|Timeframe  <br/> |Mois correspondant aux données de cette table.  <br/> |
|EXO_EmailSent  <br/> |Nombre d'e-mails envoyés.  <br/> |
|EXO_EmailReceived  <br/> |Nombre d'e-mails reçus.  <br/> |
|EXO_EmailRead  <br/> |Nombre d’activités de lecture d’e-mails effectuées par l’utilisateur, il peut s’agir de plusieurs fois de lire un e-mail déjà lu ou d’un e-mail reçu précédemment.  <br/> |
|EXO_AppointmentCreated  <br/> |Nombre de rendez-vous créés.  <br/> |
|EXO_MeetingAccepted  <br/> |Nombre de réunions acceptées.  <br/> |
|EXO_MeetingCancelled  <br/> |Nombre de réunions annulées.  <br/> |
|EXO_MeetingDeclined  <br/> |Nombre de réunions refusées.  <br/> |
|EXO_MeetingSent  <br/> |Nombre de réunions envoyées.  <br/> |
|ODB_FileViewedModified  <br/> |Nombre de fichiers avec lesquels l'utilisateur a interagi (créations, mises à jour, suppressions, affichages, téléchargements, etc.), toutes instances de OneDrive Entreprise confondues.  <br/> |
|ODB_FileSynched  <br/> |Nombre de fichiers synchronisés par l'utilisateur, toutes instances de OneDrive Entreprise confondues.  <br/> |
|ODB_FileSharedInternally  <br/> |Nombre de fichiers que cet utilisateur a partagés en interne à partir de n’importe quel OneDrive Entreprise, ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|ODB_FileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l'utilisateur, toutes instances de OneDrive Entreprise confondues.  <br/> |
|ODB_AccessedByOwner  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur leur propre OneDrive Entreprise.  <br/> |
|ODB_AccessedByOthers  <br/> |Nombre de sites avec lesquels cet utilisateur a interagi et qui résident sur le OneDrive Entreprise d’un autre utilisateur.  <br/> |
|SPO_GroupFileViewedModified  <br/> |Nombre de fichiers avec lesquels cet utilisateur a interagi sur n’importe quel site de groupe.  <br/> |
|SPO_GroupFileSynched  <br/> |Nombre de fichiers synchronisés par l'utilisateur, tous sites de groupe confondus.  <br/> |
|SPO_GroupFileSharedInternally  <br/> |Nombre de fichiers qui ont été partagés avec des utilisateurs au sein de l’organisation ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|SPO_GroupFileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l'utilisateur, tous sites de groupe confondus.  <br/> |
|SPO_GroupAccessedByOwner  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur un site de groupe dont il est propriétaire.  <br/> |
|SPO_GroupAccessedByOthers  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur un site de groupe dont un autre utilisateur est propriétaire.  <br/> |
|SPO_OtherFileViewedModified  <br/> |Nombre de fichiers avec lesquels cet utilisateur a interagi sur un autre site.  <br/> |
|SPO_OtherFileSynched  <br/> |Nombre de fichiers que cet utilisateur a synchronisés à partir d’un autre site.  <br/> |
|SPO_OtherFileSharedInternally  <br/> |Nombre de fichiers que cet utilisateur a partagés en interne à partir d’un autre site ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes). <br/> |
|SPO_OtherFileSharedExternally  <br/> |Nombre de fichiers que cet utilisateur a partagés en externe à partir de n’importe quel autre site.  <br/> |
|SPO_OtherAccessedByOwner  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur un autre site dont il est propriétaire.  <br/> |
|SPO_OtherAccessedByOthers  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur un autre site dont un autre utilisateur est propriétaire.  <br/> |
|SPO_TeamFileViewedModified  <br/> |Nombre de fichiers avec lesquels l'utilisateur a interagi, tous sites d'équipe confondus.  <br/> |
|SPO_TeamFileSynched  <br/> |Nombre de fichiers synchronisés par l'utilisateur, tous sites d'équipe confondus.  <br/> |
|SPO_TeamFileSharedInternally  <br/> |Nombre de fichiers que cet utilisateur a partagés en interne à partir d’un site d’équipe ou avec des utilisateurs au sein de groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|SPO_TeamFileSharedExternally  <br/> |Nombre de fichiers partagés en externe par l'utilisateur, tous sites d'équipe confondus.  <br/> |
|SPO_TeamAccessedByOwner  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur un site d’équipe dont il est propriétaire.  <br/> |
|SPO_TeamAccessedByOthers  <br/> |Nombre de sites avec lesquels l’utilisateur a interagi et qui résident sur un site d’équipe dont un autre utilisateur est propriétaire.  <br/> |
|Teams_ChatMessages  <br/> |Nombre de messages de conversation envoyés.  <br/> |
|Teams_ChannelMessage  <br/> |Nombre de messages publiés sur les canaux.  <br/> |
|Teams_CallParticipate  <br/> |Nombre d’appels que l’utilisateur a participé.  <br/> |
|Teams_MeetingParticipate  <br/> |Nombre de réunions que l’utilisateur a rejointes.  <br/> |
|Teams_HasOtherAction  <br/> |Valeur booléenne si l’utilisateur a effectué d’autres actions dans Microsoft Teams.  <br/> |
|YAM_MessagePost  <br/> |Nombre de messages Yammer que cet utilisateur a publiés.  <br/> |
|YAM_MessageLiked  <br/> |Nombre de messages Yammer que cet utilisateur a aimés.  <br/> |
|YAM_MessageRead  <br/> |Nombre de messages Yammer lus par cet utilisateur.  <br/> |
|SFB_P2PSummary  <br/> |Nombre de sessions P2P auxquelles l'utilisateur a participé.  <br/> |
|SFB_ConfOrgSummary  <br/> |Nombre de sessions de conférence organisées par l'utilisateur.  <br/> |
|SFB_ConfPartSummary  <br/> |Nombre de sessions de conférence auxquelles l'utilisateur a participé.  <br/> |

> [!NOTE]
> Teams_HasOtherAction signifie que l’utilisateur est considéré comme actif, mais qu’il a une valeur nulle pour les messages de conversation, les appels 1:1, les messages de canal, le nombre total de réunions et les réunions organisées.
   
### <a name="data-table---tenant-product-usage"></a>Table de données - Utilisation du produit par les locataires

Ce tableau fournit des données d’adoption d’un mois à l’autre en termes d’activation, d’activité, de retour et de nouveaux utilisateurs pour chaque produit dans Microsoft 365. Les valeurs De Microsoft 365 représentent l’utilisation active dans l’un des produits.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|Product  <br/> |Nom des produits pour lesquels les informations d'utilisation sont synthétisées. La valeur Microsoft 365 dans la colonne product représente l’activité sur tous les produits  <br/> |
|Timeframe  <br/> |Month value. There will be one row per product per month for the last 12 months including the current partial month.  <br/> |
|EnabledUsers  <br/> |Nombre d’utilisateurs autorisés à utiliser le produit pour la valeur d’intervalle de temps, si un utilisateur a été activé pendant une partie du mois, ils sont toujours comptabilisés.  <br/> |
|ActiveUsers  <br/> |Nombre d’utilisateurs qui ont effectué une activité intentionnelle dans le produit pour la valeur d’intervalle de temps.  <br/> A user is counted as active for a product in a particular month, if they have performed one of the key activities in the product. The key activities are available in the **Tenant Product Activity** table.  <br/> |
|CumulativeActiveUsers  <br/> |Nombre d'utilisateurs activés pour utiliser un produit et ayant utilisé ce produit jusqu'au mois pris en compte au moins une fois depuis le début de la collecte des données dans le nouveau système d'utilisation.  <br/> |
|MoMReturningUsers  <br/> |Nombre d'utilisateurs ayant été actifs au cours du mois pris en compte et qui étaient également actifs au cours du mois précédent.  <br/> |
|FirstTimeUsers  <br/> |Nombre d'utilisateurs devenus actifs au cours de la période prise en compte pour la première fois depuis la collecte des données dans le nouveau système d'utilisation.  <br/> Un utilisateur est comptabilisé comme nouvel utilisateur au cours d'un mois donné si une activité de celui-ci est détectée pour la première fois depuis le début de la collecte des données dans le nouveau système de création de rapports. Une fois compté comme utilisateur pour la première fois, même si cet utilisateur a un écart important dans son activité, il ne sera plus jamais compté comme un utilisateur pour la première fois  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-product-activity"></a>Table de données - Activité produit des locataires

Ce tableau fournit les totaux mensuels des activités et le nombre d’utilisateurs actifs pour diverses activités au sein des produits.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|Timeframe  <br/> |Month value. There will be one row per product per month for the last 12 months including the current partial month.  <br/> |
|Produit  <br/> |Nom du produit dans Microsoft 365 pour lequel les données d’utilisation sont disponibles.  <br/> |
|Activité  <br/> |Nom de l'activité liée à un produit, utilisé pour présenter l'utilisation active du produit.  <br/> |
|ActivityCount  <br/> |Nombre total d'actions comptabilisées pour chaque activité effectuée à l'aide du produit, tous utilisateurs actifs confondus.  <br/> **Remarque :** pour les activités SharePoint Online et OneDrive Entreprise, cette valeur représente le nombre de documents distincts avec lesquels les utilisateurs ont interagi.  <br/> |
|ActiveUserCount  <br/> |Nombre d'utilisateurs ayant effectué une activité à l'aide du produit.  <br/> |
|TotalDurationInMinute  <br/> |Nombre de minutes d'utilisation d'une session audio ou vidéo dans le cadre d'une activité Skype Entreprise applicable, tous utilisateurs actifs confondus.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-mailbox-usage"></a>Table de données - Utilisation des boîtes aux lettres par les locataires

Ce tableau se compose de données récapitulatives pour tous les utilisateurs Exchange Online sous licence qui ont une boîte aux lettres utilisateur. Elle contient un état de fin de mois englobant toutes les boîtes aux lettres utilisateur. Les données de cette table ne sont pas additives sur plusieurs mois. Dans cette table, les données du mois précédent représentent l'état le plus récent.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|TotalMailboxes  <br/> |Nombre de boîtes aux lettres utilisateur pour l’abonnement Microsoft 365.  <br/> |
|IssueWarningQuota  <br/> |Quota total pour l’émission d’un avertissement dans les boîtes aux lettres de tous les utilisateurs.  <br/> |
|ProhibitSendQuota  <br/> |Quota total au-delà duquel une interdiction d'envoi s'applique à toutes les boîtes aux lettres utilisateur.  <br/> |
|ProhibitSendReceiveQuota  <br/> |Quota total au-delà duquel une interdiction de réception s'applique à toutes les boîtes aux lettres utilisateur.  <br/> |
|TotalItemBytes  <br/> |Espace de stockage utilisé par toutes les boîtes aux lettres utilisateur, en octets.  <br/> |
|MailboxesNoWarning  <br/> |Nombre de boîtes aux lettres utilisateur n'ayant pas atteint la limite de stockage déclenchant un avertissement.  <br/> |
|MailboxesIssueWarning  <br/> |Nombre de boîtes aux lettres utilisateur ayant atteint le quota de stockage et auxquelles un avertissement a été envoyé.  <br/> |
|MailboxesExceedSendQuota  <br/> |Nombre de boîtes aux lettres utilisateur ayant dépassé le quota d'envoi.  <br/> |
|MailboxesExceedSendReceiveQuota  <br/> |Nombre de boîtes aux lettres utilisateur qui ont dépassé le quota d’envoi/réception.  <br/> |
|DeletedMailboxes  <br/> |Nombre de boîtes aux lettres utilisateur supprimées au cours de la période prise en compte.  <br/> |
|Timeframe  <br/> |Mois.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-client-usage"></a>Table de données - Utilisation du client par les locataires

Ce tableau fournit des données récapitulatives d’un mois à l’autre sur les clients que les utilisateurs utilisent pour se connecter à Exchange Online, Skype Entreprise et Yammer. Cette table ne contient pas encore de données d’utilisation du client pour SharePoint Online et OneDrive Entreprise.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|Produit  <br/> |Nom du produit dans Microsoft 365 pour lequel les données d’utilisation du client sont disponibles.  <br/> |
|Clientid  <br/> |Nom de chaque appareil utilisé pour se connecter au produit.  <br/> |
|UserCount  <br/> |Nombre d'utilisateurs ayant utilisé chacun des clients pour chaque produit.  <br/> |
|Timeframe  <br/> |Mois  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-sharepoint-online-usage"></a>Table de données - Utilisation de SharePoint Online par les locataires

Ce tableau se compose de données récapitulatives d’un mois à l’autre sur l’utilisation ou l’activité des sites SharePoint Online. Cela concerne uniquement les sites d’équipe et les sites de groupe. L’état de fin de mois des sites SharePoint Online est représenté dans cette colonne, par exemple, si un utilisateur a créé cinq documents et utilisé 10 Mo pour le stockage total, puis supprimé certains fichiers et ajouté d’autres fichiers de sorte qu’à la fin du mois pour les fichiers soit sept au total qui utilisent cinq Mo de stockage,  la valeur de représentée dans cette table est l’état de fin de mois. Cette table est masquée pour éviter le nombre d’agrégations en double et est utilisée comme source pour créer deux tables de référence.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|SiteType  <br/> |Valeur du type de site (tout/équipe/groupe) (tout représentant l'un ou l'autre de ces 2 types de sites).  <br/> |
|TotalSites  <br/> |Nombre de sites qui existaient à la fin de la période prise en compte.  <br/> |
|DocumentCount  <br/> |Nombre total de documents qui existaient sur le site à la fin de la période prise en compte.  <br/> |
|Diplansed  <br/> |Somme de l'espace de stockage total utilisé à la fin de la période prise en compte, tous sites confondus.  <br/> |
|ActivityType  <br/> |Nombre de sites ayant enregistré les différents types d'activité de fichier (tout/fichiers actifs/fichiers partagés en externe/fichiers partagés en interne/fichiers synchronisés).  <br/> Représente l’activité de fichier qui a été effectuée.  <br/> |
|SitesWithOwnerActivities  <br/> |Nombre de sites actifs, où le propriétaire a effectué une activité de fichier particulière sur son propre site. Vous pouvez obtenir le propriétaire du site à partir de la commande PowerShell **get-sposite**. Il s’agit de la personne responsable du site.   <br/> |
|SitesWithNonOwnerActivities  <br/> |Somme des sites actifs du mois, où des utilisateurs autres que le propriétaire ont effectué une activité de fichier particulière. Vous pouvez obtenir le propriétaire du site à partir de la commande PowerShell **get-sposite**. Il s’agit de la personne responsable du site. <br/> |
|ActivityTotalSites  <br/> |Number of sites that recorded any activity during the timeframe. If a site that had activity earlier in the timeframe, and was deleted by the end of the timeframe, it would still be counted in the active site total for that timeframe.  <br/> |
|Timeframe  <br/> |This column has the date value. Used as Many to one relationship for Calendar table.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-onedrive-usage"></a>Table de données - Utilisation du client OneDrive

Cette table contient des données sur les comptes OneDrive, comme le nombre de comptes, le nombre de documents stockés sur les différents comptes OneDrive, l'espace de stockage utilisé et le nombre de fichiers par type d'activité. L'état de fin de mois des comptes OneDrive Entreprise y est représenté. Par exemple, si un utilisateur a créé un cinq documents qui a utilisé 10 Mo de stockage, puis en a supprimé quelques-uns et ajouté d’autres fichiers de sorte qu’à la fin du mois, il dispose de sept fichiers qui utilisent cinq Mo de stockage, la valeur de fin de mois est représentée dans cette table à la fin du mois.
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|SiteType  <br/> |La valeur est « OneDrive ».  <br/> |
|TotalSites  <br/> |Nombre de comptes OneDrive Entreprise qui existaient à la fin de la période prise en compte.  <br/> |
|DocumentCount  <br/> |Nombre total de documents qui existaient à la fin de la période prise en compte, tous comptes OneDrive Entreprise confondus.  <br/> |
|Diplansed  <br/> |Le stockage total utilisé a été additionné sur tous les comptes OneDrive à la fin de la période.  <br/> |
|ActivityType  <br/> |Nombre de comptes ayant enregistré les différents types d'activité de fichier (tout/fichiers actifs/fichiers partagés en externe/fichiers partagés en interne/fichiers synchronisés).  <br/> Tout représente une activité de fichier quelconque.  <br/> |
|SitesWithOwnerActivities  <br/> |Nombre de comptes OneDrive Entreprise actifs, où le propriétaire a effectué une activité de fichier particulière sur son propre compte.  <br/> |
|SitesWithNonOwnerActivities  <br/> |Nombre de comptes OneDrive Entreprise, où des utilisateurs autres que le propriétaire ont effectué une activité de fichier particulière.  <br/> |
|ActivityTotalSites  <br/> |Number of OneDrive for Business accounts that recorded any activity during the timeframe. If a OneDrive for Business account had activity earlier in the timeframe, and was deleted by the end of the timeframe, it would still be counted in the active OneDrive for Business account for that timeframe.  <br/> |
|Timeframe  <br/> |This column has the date value. Used as Many to one relationship for Calendar table.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
   
### <a name="data-table---tenant-microsoft-365-groups-usage"></a>Table de données - Utilisation des Groupes Microsoft 365 locataires

Ce tableau fournit des données sur la façon dont Groupes Microsoft 365 est utilisé au sein de l’organisation.
  
****

|**Nom de colonne**|**Description de la colonne**|
|:-----|:-----|
|Délai  <br/> |Mois. La colonne contient une ligne par produit et par mois pour les 12 derniers mois, mois en cours compris.  <br/> |
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
|SPO_FileAccessedActiveGroups  <br/> |Nombre de groupes SharePoint auxquels des activités d’accès aux fichiers ont été effectuées.  <br/> |
|SPO_FileSyncedActiveGroups  <br/> |Nombre de groupes SharePoint qui ont des activités synchronisées avec des fichiers.  <br/> |
|SPO_FileSharedInternallyActiveGroups  <br/> |Nombre de groupes SharePoint qui ont des activités partagées en interne ou avec des groupes (qui peuvent inclure des utilisateurs externes).  <br/> |
|SPO_FileSharedExternallyActiveGroups  <br/> |Nombre de groupes SharePoint qui ont partagé des activités externes.  <br/> |
|SPO_TotalActivities  <br/> |Nombre d’activités SharePoint.  <br/> |
|SPO_FileAccessedActivities  <br/> |Nombre d’activités de fichier SharePoint consultées.  <br/> |
|SPO_FileSyncedActivities  <br/> |Nombre d’activités synchronisées de fichiers SharePoint.  <br/> |
|SPO_FileSharedInternallyActivities  <br/> |Nombre d’activités partagées de fichiers SharePoint en interne ou avec des groupes (qui peuvent inclure des membres externes).  <br/> |
|SPO_FileSharedExternallyActivities  <br/> |Nombre d’activités de fichier SharePoint partagées en externe.  <br/> |
|SPO_TotalFiles  <br/> |Nombre de fichiers SharePoint.  <br/> |
|SPO_ActiveFiles  <br/> |Nombre de fichiers SharePoint actifs.  <br/> |
|SPO_StorageUsed  <br/> |Quantité de stockage SharePoint utilisée.  <br/> |
|YAM_TotalGroups  <br/> |Nombre de groupes Yammer.  <br/> |
|YAM_ActiveGroups  <br/> |Nombre de groupes Yammer actifs.  <br/> |
|YAM_LikedActiveGroups  <br/> |Nombre de groupes Yammer qui ont des activités similaires.  <br/> |
|YAM_PostedActiveGroups  <br/> |Nombre de groupes Yammer qui ont des activités de publication.  <br/> |
|YAM_ReadActiveGroups  <br/> |Nombre de groupes Yammer qui ont des activités de lecture.  <br/> |
|YAM_TotalActivities  <br/> |Nombre d’activités Yammer.  <br/> |
|YAM_LikedActivities  <br/> |Nombre d’activités yammer similaires.  <br/> |
|YAM_PostedActivties  <br/> |Nombre d’activités de publication Yammer.  <br/> |
|YAM_ReadActivites  <br/> |Nombre d’activités de lecture Yammer.  <br/> |

### <a name="data-table---tenant-office-licenses"></a>Table de données - Licences Office client

Ce tableau fournit des données récapitulatives d’un mois à l’autre sur l’attribution de licence pour les utilisateurs. 
  
|**Nom de la colonne**|**Description de la colonne**|
|:-----|:-----|
|LicenseName  <br/> |Nom de la licence.  <br/> |
|AssignedCount  <br/> |Nombre de licences affectées.  <br/> |
|Timeframe  <br/> |Mois.  <br/> |

### <a name="data-table---tenant-office-activation"></a>Table de données - Activation d'Office par les locataires

Le tableau fournit des données sur le nombre d’activations d’abonnements Office dans les plans de service, par exemple, Microsoft 365 Apps pour les entreprises, Visio, Project. Elle fournit également des données sur le nombre d'activations par appareil (Android/iOS/Mac/PC).
  
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
|Timeframe  <br/> |This column has the date value. Used as Many to one relationship for Calendar table.  <br/> |
|Content Date  <br/> |Si la période prise en compte est le mois en cours, cette valeur correspond à la date des données les plus récentes disponibles pour le mois en cours.  <br/> Si la période prise en compte est le mois précédent, cette valeur correspond à la date des données les plus récentes du mois précédent.  <br/> |
