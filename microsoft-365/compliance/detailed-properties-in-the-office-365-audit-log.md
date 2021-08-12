---
title: Propriétés détaillées dans le journal d’audit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MOE150
- BCS160
- MET150
ms.assetid: ce004100-9e7f-443e-942b-9b04098fcfc3
description: Cet article fournit des descriptions des propriétés supplémentaires incluses lorsque vous exportez des résultats pour un enregistrement Office 365'audit.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: a3641b40b76c2839f5cd29c22c28dfb5652ce42515d4e0ffe7e3edce0dcd3a7f
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53808139"
---
# <a name="detailed-properties-in-the-audit-log"></a>Propriétés détaillées dans le journal d’audit

Lorsque vous exportez les résultats d’une recherche dans le journal d’audit à partir du Centre de sécurité & conformité, vous avez la possibilité de télécharger tous les résultats qui répondent à vos critères de recherche. Pour ce faire, sélectionnez **Exporter** les résultats Télécharger tous les résultats sur la page de recherche du \>  journal **d’audit.** Pour plus d’informations, [voir Rechercher dans le journal d’audit.](search-the-audit-log-in-security-and-compliance.md)
  
 Lorsque vous exportez tous les résultats d’une recherche dans le journal d’audit, les données brutes du journal d’audit unifié sont copiées dans un fichier de valeurs séparées par des virgules (CSV) téléchargé sur votre ordinateur local. Ce fichier contient des informations supplémentaires à partir de chaque enregistrement d’audit dans une colonne nommée **AuditData**. Cette colonne contient une propriété à valeurs multiples pour plusieurs propriétés de l’enregistrement du journal d’audit. Chacune des paires de propriétés **: valeur** dans cette propriété à valeurs multiples est séparée par une virgule. 
  
Le tableau suivant décrit les propriétés qui sont incluses (selon le service dans lequel un événement se produit) dans la colonne **AuditData à** propriétés multiples. Le **Office 365 service qui possède** cette colonne de propriété indique le service et le type d’activité (utilisateur ou administrateur) qui inclut la propriété. Pour plus d’informations sur ces propriétés ou sur les propriétés qui ne sont peut-être pas répertoriées dans cette rubrique, voir Schéma de l’API Activité [de gestion.](/office/office-365-management-api/office-365-management-activity-api-schema)
  
> [!TIP]
> Vous pouvez utiliser la fonctionnalité de transformation JSON dans Power Query dans Excel pour fractionner la colonne **AuditData** en plusieurs colonnes afin que chaque propriété ait sa propre colonne. Cela vous permettra d’utiliser une ou plusieurs de ces propriétés pour trier et filtrer les valeurs. Pour savoir comment faire, voir Exporter, configurer et afficher les enregistrements du [journal d’audit.](export-view-audit-log-records.md) 
  
|**Propriété**|**Description**|**Microsoft 365 service qui possède cette propriété**|
|:-----|:-----|:-----|
|Actor|Compte d’utilisateur ou de service qui a effectué l’action.|Azure Active Directory|
|AddOnName|Nom d’un module qui a été ajouté, supprimé ou mis à jour dans une équipe. Le type de modules Microsoft Teams est un bot, un connecteur ou un onglet.|Microsoft Teams|
|AddOnType|Type d’un module qui a été ajouté, supprimé ou mis à jour dans une équipe. Les valeurs suivantes indiquent le type de modules.  <br/> **1** : indique un bot.<br/> **2** : indique un connecteur.<br/> **3** - Indique un onglet.|Microsoft Teams|
|AzureActiveDirectoryEventType|Type de Azure Active Directory événement. Les valeurs suivantes indiquent le type d’événement.  <br/> **0** : indique un événement de connexion de compte.<br/> **1** : indique un événement de sécurité d’application Azure.|Azure Active Directory|
|ChannelGuid|ID d’un canal Microsoft Teams de distribution. L’équipe dans qui se trouve le canal est identifiée par les propriétés **TeamName** et **TeamGuid.**|Microsoft Teams|
|ChannelName|Nom d’un canal Microsoft Teams de distribution. L’équipe dans qui se trouve le canal est identifiée par les propriétés **TeamName** et **TeamGuid.**|Microsoft Teams|
|Client|L’appareil client, le système d’exploitation de l’appareil et le navigateur d’appareil utilisés pour l’événement de connexion (par exemple, Nokia Lumia 920 ; Windows Phone 8; IE Mobile 11).|Azure Active Directory|
|ClientInfoString|Informations sur le client de messagerie qui a été utilisé pour effectuer l’opération, telles qu’une version de navigateur, une version Outlook et des informations sur l’appareil mobile|Exchange (activité de boîte aux lettres)|
|ClientIP|Adresse IP du périphérique utilisé lors de la journalisation de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.<br/><br/> Pour certains services, la valeur affichée dans cette propriété peut être l'adresse IP d'une application sécurisée (par exemple, Office sur les applications Web) qui appelle le service au nom d'un utilisateur et non l'adresse IP de l'appareil utilisé par la personne ayant effectué l'activité. <br/><br/>En outre, pour l’activité d’administrateur (ou l’activité effectuée par un compte système) pour les événements liés à Azure Active Directory, l’adresse IP n’est pas enregistrée et la valeur de la propriété ClientIP est `null` . |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Date et heure à l’heure UTC (temps universel coordonné) au moment où l’utilisateur a effectué l’activité.|Tous|
|DestinationFileExtension|Extension du fichier qui est copié ou déplacé. Cette propriété s’affiche uniquement pour les activités de l’utilisateur FileCopied et FileMoved.|SharePoint|
|DestinationFileName|Le nom du fichier est copié ou déplacé. Cette propriété s’affiche uniquement pour les actions FileCopied et FileMoved.|SharePoint|
|DestinationRelativeUrl|URL du dossier de destination dans lequel un fichier est copié ou déplacé. La combinaison des valeurs pour **siteURL**, **DestinationRelativeURL** et la propriété **DestinationFileName** est identique à la valeur de la propriété **ObjectID,** qui est le nom du chemin d’accès complet pour le fichier qui a été copié. Cette propriété s’affiche uniquement pour les activités de l’utilisateur FileCopied et FileMoved.|SharePoint|
|EventSource|Identifie qu’un événement s’est produit dans SharePoint. Les valeurs possibles **sont SharePoint** **et ObjectModel**.|SharePoint|
|ExternalAccess|Pour Exchange d’administration, spécifie si la cmdlet a été exécuté par un utilisateur de votre organisation, par le personnel du centre de données Microsoft ou un compte de service de centre de données, ou par un administrateur délégué. La valeur **False** indique que la cmdlet a été exécutée par un membre de votre organisation. La valeur **True** indique que la cmdlet a été exécutée par le personnel du centre de données, un compte de service du centre de données ou un administrateur délégué.  <br/> Pour Exchange’activité de boîte aux lettres, spécifie si une boîte aux lettres a été accessible par un utilisateur extérieur à votre organisation.|Exchange|
|ExtendedProperties|Propriétés étendues d’un Azure Active Directory événement.|Azure Active Directory|
|ID|ID de l’entrée de rapport. L’ID identifie de manière unique l’entrée du rapport.|Tous|
|InternalLogonType|Réservé à une utilisation interne.|Exchange (activité de boîte aux lettres)|
|ItemType|Type d’objet consulté ou modifié. Les valeurs **possibles sont Fichier,** **Dossier,** **Web,** **Site,** **Client** et **DocumentLibrary**.|SharePoint|
|LoginStatus|Identifie les échecs de connexion qui ont pu se produire.|Azure Active Directory|
|LogonType|Type d’accès aux boîtes aux lettres. Les valeurs suivantes indiquent le type d’utilisateur qui a accédé à la boîte aux lettres.  <br/><br/> **0** : indique un propriétaire de boîte aux lettres.<br/> **1** : indique un administrateur.<br/> **2** : indique un délégué. <br/>**3** : indique le service de transport dans le centre de données Microsoft.<br/> **4** - Indique un compte de service dans le centre de données Microsoft. <br/>**6** - Indique un administrateur délégué.|Exchange (activité de boîte aux lettres)|
|MailboxGuid|GUID Exchange de la boîte aux lettres consultée.|Exchange (activité de boîte aux lettres)|
|MailboxOwnerUPN|Adresse de messagerie du propriétaire de la boîte aux lettres consultée.|Exchange (activité de boîte aux lettres)|
|Members|Répertorie les utilisateurs qui ont été ajoutés ou supprimés d’une équipe. Les valeurs suivantes indiquent le type de rôles attribué à l’utilisateur.  <br/><br/> **1** : indique le rôle propriétaire.<br/> **2** indique le rôle Membre.<br/> **3** indique le rôle Invité. <br/><br/>La propriété Members comprend également le nom de votre organisation et l’adresse e-mail du membre.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|La propriété est incluse pour les événements d’administration, par exemple l’ajout d’un utilisateur en tant que membre d’un site ou d’un groupe d’administration d’une collection de sites. La propriété inclut le nom de la propriété qui a été modifiée (par exemple, le groupe Administrateur de site) la nouvelle valeur de la propriété modifiée (par exemple, l’utilisateur qui a été ajouté en tant qu’administrateur de site et la valeur précédente de l’objet modifié).|Tout (activité de l’administrateur)|
|ObjectId|Pour la journalisation d’audit d’administration Exchange, il s’agit du nom de l’objet modifié par la cmdlet.  <br/> Pour SharePoint' activité, le nom complet du chemin d’URL du fichier ou du dossier accessible par un utilisateur.  <br/> Pour l’activité Azure AD, nom du compte d’utilisateur modifié.|Tous|
|Opération|Nom de l’activité de l’utilisateur ou de l’administrateur. La valeur de cette propriété correspond à la valeur qui a été sélectionnée dans la liste de **listes** listes des activités. Si **afficher les résultats pour toutes les activités** a été sélectionné, le rapport inclut des entrées pour toutes les activités des utilisateurs et des administrateurs pour tous les services. Pour obtenir une description des opérations/activités consignées dans  le journal d’audit, consultez l’onglet Activités auditées dans Rechercher dans le journal d’audit dans le [Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> Pour une activité d’administration Exchange, cette propriété identifie le nom de la cmdlet qui a été exécutée.|Tous|
|OrganizationId|GUID de votre organisation.|Tous|
|Path|Nom de dossier de la boîte aux lettres dans laquelle se trouve le message consulté. Cette propriété identifie également le dossier dans lequel un message est créé ou copié/déplacé.|Exchange (activité de boîte aux lettres)|
|Paramètres|Pour Exchange d’administration, le nom et la valeur de tous les paramètres qui ont été utilisés avec la cmdlet identifiée dans la propriété Operation.|Exchange (activité de l’administrateur)|
|RecordType|Type d’opération indiqué par l’enregistrement. Cette propriété indique le service ou la fonctionnalité dans qui l’opération a été déclenchée. Pour obtenir la liste des types d’enregistrement et leur valeur ENUM correspondante (qui est la valeur affichée dans la propriété **RecordType** d’un enregistrement d’audit), voir Type d’enregistrement du journal [d’audit.](/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype)| 
|ResultStatus|Indique si l’action (spécifiée dans la propriété **Operation)** a réussi ou non.  <br/> Pour Exchange’activité de l’administrateur, la valeur est **True** (réussite) ou **False** (échec).|Tous  <br/>|
|SecurityComplianceCenterEventType|Indique que l’activité était un événement du Centre de sécurité & conformité. Toutes les activités & conformité et sécurité auront une valeur **de 0** pour cette propriété.|Centre de sécurité et conformité|
|SharingType|Type d’autorisations de partage attribuées à l’utilisateur avec qui la ressource a été partagée. Cet utilisateur est identifié dans la **propriété UserSharedWith.**|SharePoint|
|Site|GUID du site où se trouve le fichier ou le dossier consulté par l’utilisateur.|SharePoint|
|SiteUrl|URL du site où se trouve le fichier ou le dossier consulté par l’utilisateur.|SharePoint|
|SourceFileExtension|Extension du fichier consulté par l’utilisateur. Cette propriété est vide si l’objet consulté est un dossier.|SharePoint|
|SourceFileName|Nom du fichier ou du dossier consulté par l’utilisateur.|SharePoint|
|SourceRelativeUrl|URL du dossier contenant le fichier consulté par l’utilisateur. La combinaison des valeurs pour **siteURL**, **SourceRelativeURL** et la propriété **SourceFileName** est identique à la valeur de la propriété **ObjectID,** qui est le nom du chemin d’accès complet pour le fichier accessible par l’utilisateur.|SharePoint|
|Sujet|Ligne d’objet du message qui a été consulté.|Exchange (activité de boîte aux lettres)|
|TabType| Type d’onglet ajouté, supprimé ou mis à jour dans une équipe. Les valeurs possibles pour cette propriété sont les suivantes :  <br/><br/> **Excel épingle -** Un onglet Excel'  <br/> **Extension** : toutes les applications tierces et tierces ; par exemple, Planification des classes, VSTS et Formulaires.  <br/> **Remarques** - OneNote onglet.  <br/> **Pdfpin** - Onglet PDF.  <br/> **Powerbi** : un onglet Power BI’onglet.  <br/> **Powerpointpin** - Un onglet PowerPoint’onglet.  <br/> **Sharepointfiles** - Un onglet SharePoint'  <br/> **Page Web** : onglet de site web épinglé.  <br/> **Wiki-tab** : onglet Wiki.  <br/> **Wordpin** - Onglet Word.|Microsoft Teams|
|Target|Utilisateur sur qui l’action (identifiée dans la **propriété Operation)** a été effectuée. Par exemple, si un utilisateur invité est ajouté à SharePoint ou à une équipe Microsoft, cet utilisateur est répertorié dans cette propriété.|Azure Active Directory|
|TeamGuid|ID d’une équipe dans Microsoft Teams.|Microsoft Teams|
|TeamName|Nom d’une équipe dans Microsoft Teams.|Microsoft Teams|
|UserAgent|Informations sur le navigateur de l’utilisateur. Ces informations sont fournies par le navigateur.|SharePoint|
|UserDomain|Informations d’identité sur l’organisation du client de l’utilisateur (acteur) qui a effectué l’action.|Azure Active Directory|
|UserId|L’utilisateur qui a effectué l’action (spécifiée dans la propriété **Operation)** qui a entraîné la journal de l’enregistrement. Les enregistrements d’audit pour les activités effectuées par les comptes système (tels que SHAREPOINT\system ou NT AUTHORITY\SYSTEM) sont également inclus dans le journal d’audit. Une autre valeur courante pour la propriété UserId est app@sharepoint. Ceci indique que l'«utilisateur » qui a effectué l'activité était une application ayant obtenu les autorisations nécessaires dans SharePoint pour effectuer des actions à l’échelle de l’organisation (par exemple, effectuer une recherche de site SharePoint ou de compte OneDrive) au nom d’un utilisateur, d’un administrateur ou d’un service. Pour obtenir plus d'informations, consultez [L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records). |Tous|
|UserKey|ID de remplacement pour l’utilisateur identifié dans la **propriété UserID.** Par exemple, cette propriété est remplie avec l’ID unique (PUID) passport pour les événements effectués par les utilisateurs dans SharePoint. Cette propriété peut également spécifier la même valeur que la propriété **UserID** pour les événements se produisant dans d’autres services et événements exécutés par des comptes système.|Tous|
|UserSharedWith|Utilisateur avec lequel une ressource a été partagée. Cette propriété est incluse si la valeur de la propriété **Operation** est **SharingSet**. Cet utilisateur est également répertorié dans la colonne **Partagé avec** dans le rapport.|SharePoint|
|UserType|Type d’utilisateur ayant effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur. <br/> <br/> **0** : utilisateur normal. <br/>**2** : un administrateur de votre organisation Microsoft 365 de gestion. <sup>1</sup> <br/>**3** : un compte d’administrateur de centre de données Microsoft ou un compte système de centre de données. <br/>**4** - Un compte système. <br/>**5** - Application. <br/>**6** - Principal de service.<br/>**7** - Une stratégie personnalisée.<br/>**8** : une stratégie système.|Tous|
|Version|Indique le numéro de version de l’activité (identifiée par la propriété **Operation)** enregistrée.|Tous|
|Charge de travail|Le Microsoft 365 service dans lequel l’activité s’est produite.|Tous|
||||

> [!NOTE]
><sup>1 Pour</sup> les Azure Active Directory, la valeur d’un administrateur n’est pas utilisée dans un enregistrement d’audit. Les enregistrements d’audit pour les activités effectuées par les administrateurs indiquent qu’un utilisateur normal (par exemple, **UserType : 0**) a effectué l’activité. La **propriété UserID** identifie la personne (utilisateur normal ou administrateur) qui a effectué l’activité.<br/>

Les propriétés décrites ci-dessus s’affichent également lorsque vous cliquez sur **Plus** d’informations lors de l’affichage des détails d’un événement spécifique.
  
![Cliquez sur Informations supplémentaires pour afficher les propriétés détaillées de l’enregistrement d’événement du journal d’audit](../media/6df582ae-d339-4735-b1a6-80914fb77a08.png)