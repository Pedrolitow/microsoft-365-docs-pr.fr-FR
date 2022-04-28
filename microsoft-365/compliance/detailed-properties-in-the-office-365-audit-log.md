---
title: Propriétés détaillées dans le journal d’audit
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- BCS160
- MET150
ms.assetid: ce004100-9e7f-443e-942b-9b04098fcfc3
description: Cet article fournit des descriptions des propriétés supplémentaires incluses lorsque vous exportez des résultats pour un enregistrement de journal d’audit Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 82fd42fc44d5738c47ec022de2bb1b5f53396ae2
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65098821"
---
# <a name="detailed-properties-in-the-audit-log"></a>Propriétés détaillées dans le journal d’audit

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Lorsque vous exportez les résultats d’une recherche dans le journal d’audit à partir du portail de conformité Microsoft Purview, vous avez la possibilité de télécharger tous les résultats qui répondent à vos critères de recherche. Pour ce faire, sélectionnez **Exporter les résultats** \> **Télécharger tous les résultats** dans la page Recherche dans le **journal d’audit** . Pour plus d’informations, consultez [Rechercher dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md).
  
 Lorsque vous exportez tous les résultats d’une recherche dans le journal d’audit, les données brutes du journal d’audit unifié sont copiées dans un fichier de valeurs séparées par des virgules (CSV) téléchargé sur votre ordinateur local. Ce fichier contient des informations supplémentaires à partir de chaque enregistrement d’audit dans une colonne nommée **AuditData**. Cette colonne contient une propriété à valeurs multiples pour plusieurs propriétés de l’enregistrement du journal d’audit. Chacune de ces **propriétés :** les paires valeur de cette propriété à valeurs multiples sont séparées par une virgule. 
  
Le tableau suivant décrit les propriétés incluses (en fonction du service dans lequel un événement se produit) dans la colonne **AuditData** à plusieurs propriétés. Le **service Office 365 qui contient cette colonne de propriétés** indique le service et le type d’activité (utilisateur ou administrateur) qui inclut la propriété. Pour plus d’informations sur ces propriétés ou sur les propriétés qui peuvent ne pas être répertoriées dans cette rubrique, consultez [schéma de l’API Activité](/office/office-365-management-api/office-365-management-activity-api-schema) de gestion.
  
> [!TIP]
> Vous pouvez utiliser la fonctionnalité de transformation JSON dans Power Query dans Excel pour fractionner la colonne **AuditData** en plusieurs colonnes afin que chaque propriété ait sa propre colonne. Cela vous permettra d’utiliser une ou plusieurs de ces propriétés pour trier et filtrer les valeurs. Pour savoir comment procéder, consultez [Exporter, configurer et afficher les enregistrements du journal d’audit](export-view-audit-log-records.md). 
  
|**Propriété**|**Description**|**Microsoft 365 service qui a cette propriété**|
|:-----|:-----|:-----|
|Actor|Compte d’utilisateur ou de service qui a effectué l’action.|Azure Active Directory|
|AddOnName|Nom d’un module complémentaire qui a été ajouté, supprimé ou mis à jour dans une équipe. Le type de modules complémentaires dans Microsoft Teams est un bot, un connecteur ou un onglet.|Microsoft Teams|
|AddOnType|Type d’un module complémentaire qui a été ajouté, supprimé ou mis à jour dans une équipe. Les valeurs suivantes indiquent le type de module complémentaire.  <br/> **1** - Indique un bot.<br/> **2** - Indique un connecteur.<br/> **3** - Indique un onglet.|Microsoft Teams|
|AzureActiveDirectoryEventType|Type d’événement Azure Active Directory. Les valeurs suivantes indiquent le type d’événement.  <br/> **0** - Indique un événement de connexion de compte.<br/> **1** - Indique un événement de sécurité des applications Azure.|Azure Active Directory|
|ChannelGuid|ID d’un canal Microsoft Teams. L’équipe dans laquelle se trouve le canal est identifiée par les propriétés **TeamName** et **TeamGuid** .|Microsoft Teams|
|ChannelName|Nom d’un canal Microsoft Teams. L’équipe dans laquelle se trouve le canal est identifiée par les propriétés **TeamName** et **TeamGuid** .|Microsoft Teams|
|Client|L’appareil client, le système d’exploitation de l’appareil et le navigateur d’appareil utilisés pour l’événement de connexion (par exemple, Nokia Lumia 920 ; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|Informations sur le client de messagerie utilisé pour effectuer l’opération, telles qu’une version du navigateur, une version Outlook et des informations sur l’appareil mobile|Exchange (activité de boîte aux lettres)|
|ClientIP|Adresse IP du périphérique utilisé lors de la journalisation de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.<br/><br/> Pour certains services, la valeur affichée dans cette propriété peut être l'adresse IP d'une application sécurisée (par exemple, Office sur les applications Web) qui appelle le service au nom d'un utilisateur et non l'adresse IP de l'appareil utilisé par la personne ayant effectué l'activité. <br/><br/>En outre, pour l’activité administrateur (ou l’activité effectuée par un compte système) pour les événements liés à Azure Active Directory, l’adresse IP n’est pas journalisée et la valeur de la propriété ClientIP est `null`. |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Date et heure à l’heure UTC (temps universel coordonné) au moment où l’utilisateur a effectué l’activité.|Tous|
|DestinationFileExtension|Extension du fichier qui est copié ou déplacé. Cette propriété s’affiche uniquement pour les activités utilisateur FileCopied et FileMoved.|SharePoint|
|DestinationFileName|Le nom du fichier est copié ou déplacé. Cette propriété s’affiche uniquement pour les actions FileCopied et FileMoved.|SharePoint|
|DestinationRelativeUrl|URL du dossier de destination dans lequel un fichier est copié ou déplacé. La combinaison des valeurs pour **SiteURL**, **DestinationRelativeURL** et la propriété **DestinationFileName** est identique à la valeur de la propriété **ObjectID** , qui est le nom de chemin d’accès complet du fichier qui a été copié. Cette propriété s’affiche uniquement pour les activités utilisateur FileCopied et FileMoved.|SharePoint|
|EventSource|Identifie qu’un événement s’est produit dans SharePoint. Les valeurs possibles sont **SharePoint** et **ObjectModel**.|SharePoint|
|ExternalAccess|Pour Exchange activité d’administrateur, spécifie si l’applet de commande a été exécutée par un utilisateur de votre organisation, par le personnel du centre de données Microsoft ou un compte de service de centre de données ou par un administrateur délégué. La valeur **False** indique que la cmdlet a été exécutée par un membre de votre organisation. La valeur **True** indique que la cmdlet a été exécutée par le personnel du centre de données, un compte de service du centre de données ou un administrateur délégué.  <br/> Pour Exchange activité de boîte aux lettres, spécifie si un utilisateur extérieur à votre organisation a accédé à une boîte aux lettres.|Exchange|
|ExtendedProperties|Propriétés étendues d’un événement Azure Active Directory.|Azure Active Directory|
|ID|ID de l’entrée de rapport. L’ID identifie de façon unique l’entrée de rapport.|Tous|
|InternalLogonType|Réservé à une utilisation interne.|Exchange (activité de boîte aux lettres)|
|ItemType|Type d’objet consulté ou modifié. Les valeurs possibles sont **File**, **Folder**, **Web**, **Site**, **Tenant** et **DocumentLibrary**.|SharePoint|
|LoginStatus|Identifie les échecs de connexion qui ont pu se produire.|Azure Active Directory|
|LogonType|Type d’accès aux boîtes aux lettres. Les valeurs suivantes indiquent le type d’utilisateur qui a accédé à la boîte aux lettres.  <br/><br/> **0** - Indique un propriétaire de boîte aux lettres.<br/> **1** - Indique un administrateur.<br/> **2** - Indique un délégué. <br/>**3** - Indique le service de transport dans le centre de données Microsoft.<br/> **4** - Indique un compte de service dans le centre de données Microsoft. <br/>**6** - Indique un administrateur délégué.|Exchange (activité de boîte aux lettres)|
|MailboxGuid|GUID Exchange de la boîte aux lettres consultée.|Exchange (activité de boîte aux lettres)|
|MailboxOwnerUPN|Adresse de messagerie du propriétaire de la boîte aux lettres consultée.|Exchange (activité de boîte aux lettres)|
|Members|Répertorie les utilisateurs qui ont été ajoutés ou supprimés d’une équipe. Les valeurs suivantes indiquent le type de rôles attribué à l’utilisateur.  <br/><br/> **1** - Indique le rôle Propriétaire.<br/> **2** indique le rôle Membre.<br/> **3** indique le rôle Invité. <br/><br/>La propriété Members comprend également le nom de votre organisation et l’adresse e-mail du membre.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|La propriété est incluse pour les événements d’administration, par exemple l’ajout d’un utilisateur en tant que membre d’un site ou d’un groupe d’administration d’une collection de sites. La propriété inclut le nom de la propriété qui a été modifiée (par exemple, le groupe Administrateur de site) la nouvelle valeur de la propriété modifiée (par exemple, l’utilisateur qui a été ajouté en tant qu’administrateur de site, et la valeur précédente de l’objet modifié.|Tout (activité d’administration)|
|ObjectId|Pour la journalisation d’audit d’administration Exchange, il s’agit du nom de l’objet modifié par la cmdlet.  <br/> Pour SharePoint activité, nom complet du chemin d’URL du fichier ou dossier accessible par un utilisateur.  <br/> Pour Azure AD activité, nom du compte d’utilisateur qui a été modifié.|Tous|
|Opération|Nom de l’activité de l’utilisateur ou de l’administrateur. La valeur de cette propriété correspond à la valeur qui a été sélectionnée dans la liste **déroulante Activités** . Si **les résultats d’affichage de toutes les activités ont été sélectionnés** , le rapport inclut des entrées pour toutes les activités utilisateur et administrateur pour tous les services. Pour obtenir une description des opérations/activités qui sont enregistrées dans le journal d’audit, consultez l’onglet **Activités auditées** dans [rechercher le journal d’audit dans le Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> Pour une activité d’administration Exchange, cette propriété identifie le nom de la cmdlet qui a été exécutée.|Tous|
|OrganizationId|GUID de votre organisation.|Tous|
|Path|Nom de dossier de la boîte aux lettres dans laquelle se trouve le message consulté. Cette propriété identifie également le dossier dans lequel un message est créé ou copié/déplacé.|Exchange (activité de boîte aux lettres)|
|Paramètres|Pour Exchange activité d’administrateur, nom et valeur de tous les paramètres utilisés avec l’applet de commande identifiée dans la propriété Operation.|Exchange (activité d’administration)|
|RecordType|Type d’opération indiqué par l’enregistrement. Cette propriété indique le service ou la fonctionnalité dans lequel l’opération a été déclenchée. Pour obtenir la liste des types d’enregistrements et leur valeur ENUM correspondante (qui est la valeur affichée dans la propriété **RecordType** dans un enregistrement d’audit), consultez [le type d’enregistrement du journal d’audit](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Indique si l’action (spécifiée dans la propriété **Operation** ) a réussi ou non.  <br/> Pour Exchange activité d’administrateur, la valeur est **True** (réussite) ou **False** (échec).|Tous  <br/>|
|SecurityComplianceCenterEventType|Indique que l’activité était un événement du portail de conformité. Toutes les activités du centre de conformité ont la valeur **0** pour cette propriété.|Centre de sécurité et conformité|
|SharingType|Type d’autorisations de partage affectées à l’utilisateur avec lequel la ressource a été partagée. Cet utilisateur est identifié dans la propriété **UserSharedWith** .|SharePoint|
|Site|GUID du site où se trouve le fichier ou le dossier consulté par l’utilisateur.|SharePoint|
|SiteUrl|URL du site où se trouve le fichier ou le dossier consulté par l’utilisateur.|SharePoint|
|SourceFileExtension|Extension du fichier consulté par l’utilisateur. Cette propriété est vide si l’objet consulté est un dossier.|SharePoint|
|SourceFileName|Nom du fichier ou du dossier consulté par l’utilisateur.|SharePoint|
|SourceRelativeUrl|URL du dossier contenant le fichier consulté par l’utilisateur. La combinaison des valeurs pour **SiteURL**, **SourceRelativeURL** et la propriété **SourceFileName** est la même que la valeur de la propriété **ObjectID** , qui est le nom du chemin d’accès complet pour le fichier auquel l’utilisateur accède.|SharePoint|
|Sujet|Ligne d’objet du message qui a été consulté.|Exchange (activité de boîte aux lettres)|
|TabType| Type d’onglet ajouté, supprimé ou mis à jour dans une équipe. Les valeurs possibles pour cette propriété sont les suivantes :  <br/><br/> **Excel épingler** : onglet Excel.  <br/> **Extension** : toutes les applications tierces et internes ; tels que la planification de classes, VSTS et les formulaires.  <br/> **Notes** - onglet OneNote.  <br/> **Pdfpin** - Onglet PDF.  <br/> **Powerbi** - Onglet Power BI.  <br/> **Powerpointpin** : onglet PowerPoint.  <br/> **Sharepointfiles** : onglet SharePoint.  <br/> **Page web** : onglet de site web épinglé.  <br/> **Onglet Wiki** - Onglet Wiki.  <br/> **Wordpin** - Onglet Word.|Microsoft Teams|
|Target|Utilisateur sur lequel l’action (identifiée dans la propriété **Operation** ) a été effectuée. Par exemple, si un utilisateur invité est ajouté à SharePoint ou à une équipe Microsoft, cet utilisateur est répertorié dans cette propriété.|Azure Active Directory|
|TeamGuid|ID d’une équipe dans Microsoft Teams.|Microsoft Teams|
|TeamName|Nom d’une équipe dans Microsoft Teams.|Microsoft Teams|
|UserAgent|Informations sur le navigateur de l’utilisateur. Ces informations sont fournies par le navigateur.|SharePoint|
|UserDomain|Informations d’identité sur l’organisation du locataire de l’utilisateur (acteur) qui a effectué l’action.|Azure Active Directory|
|UserId|Utilisateur qui a effectué l’action (spécifiée dans la propriété **Operation** ) qui a entraîné la journalisation de l’enregistrement. Les enregistrements d’audit pour l’activité effectuée par les comptes système (tels que SHAREPOINT\system ou NT AUTHORITY\SYSTEM) sont également inclus dans le journal d’audit. Une autre valeur courante pour la propriété UserId est app@sharepoint. Ceci indique que l'«utilisateur » qui a effectué l'activité était une application ayant obtenu les autorisations nécessaires dans SharePoint pour effectuer des actions à l’échelle de l’organisation (par exemple, effectuer une recherche de site SharePoint ou de compte OneDrive) au nom d’un utilisateur, d’un administrateur ou d’un service. <br/><br/>Pour plus d’informations, voir :<br/> [Utilisateur appsharepoint\@ dans les enregistrements d’audit](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records)<br/> ou <br/>[Comptes système dans Exchange enregistrements d’audit de boîte aux lettres](search-the-audit-log-in-security-and-compliance.md#system-accounts-in-exchange-mailbox-audit-records). |Tous|
|UserKey|ID de remplacement pour l’utilisateur identifié dans la propriété **UserID** . Par exemple, cette propriété est remplie avec l’ID unique passport (PUID) pour les événements effectués par les utilisateurs dans SharePoint. Cette propriété peut également spécifier la même valeur que la propriété **UserID** pour les événements qui se produisent dans d’autres services et événements effectués par des comptes système.|Tous|
|UserSharedWith|Utilisateur avec lequel une ressource a été partagée. Cette propriété est incluse si la valeur de la propriété **Operation** est **SharingSet**. Cet utilisateur est également répertorié dans la colonne **Partagé avec** le rapport.|SharePoint|
|UserType|Type d’utilisateur ayant effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur. <br/> <br/> **0** - Un utilisateur régulier. <br/>**2** - Un administrateur dans votre organisation Microsoft 365.<sup> 1</sup> <br/>**3** - Un compte système d’administrateur ou de centre de données Microsoft. <br/>**4** - Un compte système. <br/>**5** - Une application. <br/>**6** - Principal de service.<br/>**7** - Une stratégie personnalisée.<br/>**8** - Une stratégie système.|Tous|
|Version|Indique le numéro de version de l’activité (identifiée par la propriété **Operation** ) journalisée.|Tous|
|Charge de travail|Service Microsoft 365 où l’activité s’est produite.|Tous|
||||

> [!NOTE]
><sup>1</sup> Pour les événements liés à Azure Active Directory, la valeur d’un administrateur n’est pas utilisée dans un enregistrement d’audit. Les enregistrements d’audit des activités effectuées par les administrateurs indiquent qu’un utilisateur standard (par exemple, **UserType : 0**) a effectué l’activité. La propriété **UserID** identifie la personne (utilisateur ou administrateur régulier) qui a effectué l’activité.
