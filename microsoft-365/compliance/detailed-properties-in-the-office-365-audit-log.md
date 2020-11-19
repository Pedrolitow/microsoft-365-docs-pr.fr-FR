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
description: Cet article fournit des descriptions des propriétés supplémentaires incluses lorsque vous exportez des résultats pour un enregistrement de journal d’audit Office 365.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 250db03e7d330ed013909925b44f8d9843f1197d
ms.sourcegitcommit: 5480982967a90ca3060a59676a6b29155f2de861
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49350700"
---
# <a name="detailed-properties-in-the-audit-log"></a>Propriétés détaillées dans le journal d’audit

Lorsque vous exportez les résultats d’une recherche de journal d’audit à partir du centre de sécurité & conformité, vous avez la possibilité de télécharger tous les résultats qui correspondent à vos critères de recherche. Pour ce faire, sélectionnez **Exporter** \> **les résultats : Télécharger tous les résultats** sur la page de **recherche du journal d’audit** . Pour plus d’informations, consultez [la rubrique Rechercher dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md).
  
 Lorsque vous exportez tous les résultats d’une recherche de journal d’audit, les données brutes du journal d’audit unifié sont copiées dans un fichier de valeurs séparées par des virgules (CSV) qui est téléchargé sur votre ordinateur local. Ce fichier contient des informations supplémentaires à partir de chaque enregistrement d’audit dans une colonne nommée **AuditData**. Cette colonne contient une propriété à valeurs multiples pour plusieurs propriétés de l’enregistrement du journal d’audit. Chacune des paires **propriété : valeur** de cette propriété à valeurs multiples est séparée par une virgule. 
  
Le tableau suivant décrit les propriétés incluses (en fonction du service dans lequel un événement se produit) dans la colonne **AuditData** à plusieurs propriétés. Le **service Office 365 qui a cette** colonne de propriété indique le service et le type d’activité (utilisateur ou administrateur) qui inclut la propriété. Pour plus d’informations sur ces propriétés ou sur les propriétés qui ne sont peut-être pas mentionnées dans cette rubrique, voir [Management Activity Activity Schema](https://go.microsoft.com/fwlink/p/?LinkId=717993).
  
> [!TIP]
> Vous pouvez utiliser la fonctionnalité transformation JSON de Power Query dans Excel pour fractionner la colonne **AuditData** en plusieurs colonnes afin que chaque propriété dispose de sa propre colonne. Cela vous permettra d’utiliser une ou plusieurs de ces propriétés pour trier et filtrer les valeurs. Pour savoir comment procéder, consultez la rubrique relative à l' [exportation, la configuration et l’affichage des enregistrements de journal d’audit](export-view-audit-log-records.md). 
  
|**Propriété**|**Description**|**Service Microsoft 365 ayant cette propriété**|
|:-----|:-----|:-----|
|Actor|L’utilisateur ou le compte de service qui a effectué l’action.|Azure Active Directory|
|AddOnName|Nom d’un module complémentaire ajouté, supprimé ou mis à jour dans une équipe. Le type de modules complémentaires de Microsoft teams est un bot, un connecteur ou un onglet.|Microsoft Teams|
|AddOnType|Type d’un module complémentaire ajouté, supprimé ou mis à jour dans une équipe. Les valeurs suivantes indiquent le type de module complémentaire.  <br/> **1** -indique un bot.<br/> **2** -indique un connecteur.<br/> **3** -indique un onglet.|Microsoft Teams|
|AzureActiveDirectoryEventType|Type d’événement Azure Active Directory. Les valeurs suivantes indiquent le type d’événement.  <br/> **0** -indique un événement de connexion au compte.<br/> **1** -indique un événement de sécurité d’application Azure.|Azure Active Directory|
|ChannelGuid|ID d’un canal Microsoft Teams. L’équipe dans laquelle se trouve le canal est identifiée par les propriétés **nom** et **TeamGuid** .|Microsoft Teams|
|ChannelName|Nom d’un canal Microsoft Teams. L’équipe dans laquelle se trouve le canal est identifiée par les propriétés **nom** et **TeamGuid** .|Microsoft Teams|
|Client|Le périphérique client, le système d’exploitation de l’appareil et le navigateur d’appareil utilisé pour l’événement de connexion (par exemple, Nokia Lumia 920 ; Windows Phone 8 ; Internet Explorer 11).|Azure Active Directory|
|ClientInfoString|Informations sur le client de messagerie qui a été utilisé pour effectuer l’opération, par exemple une version de navigateur, une version d’Outlook et des informations sur l’appareil mobile|Exchange (activité de boîte aux lettres)|
|ClientIP|Adresse IP du périphérique utilisé lors de la journalisation de l’activité. L’adresse IP apparaît au format d’adresse IPv4 ou IPv6.<br/><br/> Pour certains services, la valeur affichée dans cette propriété peut être l'adresse IP d'une application sécurisée (par exemple, Office sur les applications Web) qui appelle le service au nom d'un utilisateur et non l'adresse IP de l'appareil utilisé par la personne ayant effectué l'activité. <br/><br/>De plus, pour l’activité de l’administrateur (ou l’activité effectuée par un compte système) pour les événements associés à Azure Active Directory, l’adresse IP n’est pas consignée et la valeur de la propriété ClientIP est `null` . |Azure Active Directory, Exchange, SharePoint|
|CreationTime|Date et heure à l’heure UTC (temps universel coordonné) au moment où l’utilisateur a effectué l’activité.|Tous|
|DestinationFileExtension|Extension du fichier qui est copié ou déplacé. Cette propriété s’affiche uniquement pour les activités utilisateur les et FileMoved.|SharePoint|
|DestinationFileName|Le nom du fichier est copié ou déplacé. Cette propriété est affichée uniquement pour les actions les et FileMoved.|SharePoint|
|DestinationRelativeUrl|URL du dossier de destination dans lequel un fichier est copié ou déplacé. La combinaison des valeurs des propriétés **SiteUrl**, **DestinationRelativeURL** et **destinationFileName** est identique à la valeur de la propriété **ObjectID** , qui est le nom du chemin d’accès complet au fichier qui a été copié. Cette propriété s’affiche uniquement pour les activités utilisateur les et FileMoved.|SharePoint|
|EventSource|Identifie qu’un événement s’est produit dans SharePoint. Les valeurs possibles sont **SharePoint** et **ObjectModel**.|SharePoint|
|ExternalAccess|Pour l’activité d’administration Exchange, indique si la cmdlet a été exécutée par un utilisateur de votre organisation, par le personnel du centre de connaissances Microsoft ou par un compte de service de centre de de services, ou par un administrateur délégué. La valeur **False** indique que la cmdlet a été exécutée par un membre de votre organisation. La valeur **True** indique que la cmdlet a été exécutée par le personnel du centre de données, un compte de service du centre de données ou un administrateur délégué.  <br/> Pour l’activité des boîtes aux lettres Exchange, indique si un utilisateur a accédé à une boîte aux lettres à l’extérieur de votre organisation.|Exchange|
|ExtendedProperties|Propriétés étendues d’un événement Azure Active Directory.|Azure Active Directory|
|ID|ID de l’entrée de rapport. L’ID identifie de manière unique l’entrée de rapport.|Tous|
|InternalLogonType|Réservé à une utilisation interne.|Exchange (activité de boîte aux lettres)|
|ItemType|Type d’objet consulté ou modifié. Les valeurs possibles sont les suivants : **file**, **Folder**, **Web**, **site**, **client** et **DocumentLibrary**.|SharePoint|
|LoginStatus|Identifie les échecs de connexion qui ont pu se produire.|Azure Active Directory|
|LogonType|Type d’accès à la boîte aux lettres. Les valeurs suivantes indiquent le type d’utilisateur qui a accédé à la boîte aux lettres.  <br/><br/> **0** -indique un propriétaire de boîte aux lettres.<br/> **1** -indique un administrateur.<br/> **2** -indique un délégué. <br/>**3** -indique le service de transport dans le centre de Microsoft.<br/> **4** -indique un compte de service dans le centre de Microsoft. <br/>**6** -indique un administrateur délégué.|Exchange (activité de boîte aux lettres)|
|MailboxGuid|GUID Exchange de la boîte aux lettres consultée.|Exchange (activité de boîte aux lettres)|
|MailboxOwnerUPN|Adresse de messagerie du propriétaire de la boîte aux lettres consultée.|Exchange (activité de boîte aux lettres)|
|Members|Répertorie les utilisateurs qui ont été ajoutés ou supprimés d’une équipe. Les valeurs suivantes indiquent le type de rôles attribué à l’utilisateur.  <br/><br/> **1** -indique le rôle de propriétaire.<br/> **2** indique le rôle Membre.<br/> **3** indique le rôle Invité. <br/><br/>La propriété Members comprend également le nom de votre organisation et l’adresse e-mail du membre.|Microsoft Teams|
|ModifiedProperties (Name, NewValue, OldValue)|La propriété est incluse pour les événements d’administration, par exemple l’ajout d’un utilisateur en tant que membre d’un site ou d’un groupe d’administration d’une collection de sites. La propriété inclut le nom de la propriété qui a été modifiée (par exemple, le groupe administrateurs de site) la nouvelle valeur de la propriété modifiée (par exemple, l’utilisateur qui a été ajouté en tant qu’administrateur de site, et la valeur précédente de l’objet modifié.|All (activité de l’administrateur)|
|ObjectId|Pour la journalisation d’audit d’administration Exchange, il s’agit du nom de l’objet modifié par la cmdlet.  <br/> Pour l’activité SharePoint, le nom du chemin d’accès complet de l’URL du fichier ou du dossier auquel un utilisateur a accédé.  <br/> Pour l’activité Azure AD, le nom du compte d’utilisateur qui a été modifié.|Tous|
|Opération|Nom de l’activité de l’utilisateur ou de l’administrateur. La valeur de cette propriété correspond à la valeur sélectionnée dans la liste déroulante **activités** . Si l’option **afficher les résultats pour toutes les activités** a été sélectionnée, le rapport inclura les entrées de toutes les activités d’utilisateur et d’administration de tous les services. Pour obtenir une description des opérations/activités qui sont consignées dans le journal d’audit, consultez l’onglet **activités auditées** dans Rechercher dans le [Journal d’audit dans le Office 365](search-the-audit-log-in-security-and-compliance.md).  <br/> Pour une activité d’administration Exchange, cette propriété identifie le nom de la cmdlet qui a été exécutée.|Tous|
|OrganizationId|GUID de votre organisation.|Tous|
|Path|Nom de dossier de la boîte aux lettres dans laquelle se trouve le message consulté. Cette propriété identifie également le dossier dans lequel un message est créé ou copié/déplacé.|Exchange (activité de boîte aux lettres)|
|Paramètres|Pour l’activité d’administration Exchange, le nom et la valeur de tous les paramètres qui ont été utilisés avec la cmdlet identifiée dans la propriété Operation.|Exchange (activité d’administration)|
|RecordType|Type d’opération indiqué par l’enregistrement. Cette propriété indique le service ou la fonctionnalité dans laquelle l’opération a été déclenchée. Pour obtenir la liste des types d’enregistrements et leur valeur ENUM correspondante (qui correspond à la valeur affichée dans la propriété **RecordType** d’un enregistrement d’audit), voir [Record Log record type](https://docs.microsoft.com/office/office-365-management-api/office-365-management-activity-api-schema#auditlogrecordtype).| 
|ResultStatus|Indique si l’action (spécifiée dans la propriété **operation** ) a réussi ou non.  <br/> Pour l’activité d’administration Exchange, la valeur est **true** (réussite) ou **false** (échec).|Tous  <br/>|
|SecurityComplianceCenterEventType|Indique que l’activité était un événement du centre de sécurité & conformité. Toutes les activités de sécurité & du centre de conformité auront une valeur de **0** pour cette propriété.|Centre de sécurité et conformité|
|SharingType|Type d’autorisations de partage attribué à l’utilisateur avec lequel la ressource a été partagée. Cet utilisateur est identifié dans la propriété **UserSharedWith** .|SharePoint|
|Site|GUID du site où se trouve le fichier ou le dossier consulté par l’utilisateur.|SharePoint|
|SiteUrl|URL du site où se trouve le fichier ou le dossier consulté par l’utilisateur.|SharePoint|
|SourceFileExtension|Extension du fichier consulté par l’utilisateur. Cette propriété est vide si l’objet consulté est un dossier.|SharePoint|
|SourceFileName|Nom du fichier ou du dossier consulté par l’utilisateur.|SharePoint|
|SourceRelativeUrl|URL du dossier contenant le fichier consulté par l’utilisateur. La combinaison des valeurs des propriétés **SiteUrl**, **SourceRelativeURL** et **sourceFileName** est identique à la valeur de la propriété **ObjectID** , qui est le nom du chemin d’accès complet au fichier accédé par l’utilisateur.|SharePoint|
|Sujet|Ligne d’objet du message qui a été consulté.|Exchange (activité de boîte aux lettres)|
|TabType| Type d’onglet ajouté, supprimé ou mis à jour dans une équipe. Les valeurs possibles pour cette propriété sont les suivantes :  <br/><br/> **Code confidentiel Excel** -onglet Excel.  <br/> **Extension** -toutes les applications tierces et tierces ; telles que Schedule Class, VSTS et Forms.  <br/> Onglet **Notes** -OneNote.  <br/> **Pdfpin** -onglet PDF.  <br/> **Powerbi** -un onglet Power bi.  <br/> **Powerpointpin** -un onglet PowerPoint.  <br/> **Sharepointfiles** -un onglet SharePoint.  <br/> **Page Web** : onglet site Web épinglé.  <br/> **Wiki-onglet** -un onglet wiki.  <br/> **Wordpin** -un onglet Word.|Microsoft Teams|
|Target|Utilisateur sur lequel l’action (identifiée dans la propriété **operation** ) a été effectuée. Par exemple, si un utilisateur invité est ajouté à SharePoint ou à une équipe Microsoft, cet utilisateur est mentionné dans cette propriété.|Azure Active Directory|
|TeamGuid|ID d’une équipe dans Microsoft Teams.|Microsoft Teams|
|TeamName|Nom d’une équipe dans Microsoft Teams.|Microsoft Teams|
|UserAgent|Informations sur le navigateur de l’utilisateur. Ces informations sont fournies par le navigateur.|SharePoint|
|UserDomain|Informations d’identité sur l’organisation cliente de l’utilisateur (acteur) qui a effectué l’action.|Azure Active Directory|
|UserId|Utilisateur qui a effectué l’action (spécifié dans la propriété **operation** ) ayant provoqué l’enregistrement journalisé. Les enregistrements d’audit pour les activités effectuées par les comptes système (par exemple, SHAREPOINT\system ou NT AUTHORITY\SYSTEM) sont également inclus dans le journal d’audit. Une autre valeur commune pour la propriété UserId est app@sharepoint. Ceci indique que l'«utilisateur » qui a effectué l'activité était une application ayant obtenu les autorisations nécessaires dans SharePoint pour effectuer des actions à l’échelle de l’organisation (par exemple, effectuer une recherche de site SharePoint ou de compte OneDrive) au nom d’un utilisateur, d’un administrateur ou d’un service. Pour obtenir plus d'informations, consultez [L’application\@sharepoint de l’utilisateur dans des enregistrements d’audit](search-the-audit-log-in-security-and-compliance.md#the-appsharepoint-user-in-audit-records). |Tous|
|UserKey|Autre ID pour l’utilisateur identifié dans la propriété **userid** . Par exemple, cette propriété est renseignée avec l’ID unique Passport (PUID) pour les événements exécutés par les utilisateurs dans SharePoint. Cette propriété peut également spécifier la même valeur que celle de la propriété **userid** pour les événements survenus dans d’autres services et événements exécutés par des comptes système.|Tous|
|UserSharedWith|Utilisateur avec lequel une ressource a été partagée. Cette propriété est incluse si la valeur de la propriété **operation** est **SharingSet**. Cet utilisateur est également mentionné dans la colonne **partagé avec** du rapport.|SharePoint|
|UserType|Type d’utilisateur ayant effectué l’opération. Les valeurs suivantes indiquent le type d’utilisateur. <br/> <br/> **0** -un utilisateur normal. <br/>**2** -un administrateur de votre organisation Microsoft 365. <sup>1</sup> <br/>**3** -un compte d’administrateur ou de système de centre de connaissances Microsoft. <br/>**4** -un compte système. <br/>**5** -une application. <br/>**6** -un principal de service.<br/>**7** -une stratégie personnalisée.<br/>**8** -une stratégie système.|Tous|
|Version|Indique le numéro de version de l’activité (identifiée par la propriété **operation** ) qui est enregistrée.|Tous|
|Charge de travail|Service Microsoft 365 où l’activité s’est produite.|Tous|
||||

> [!NOTE]
><sup>1</sup> pour les événements associés à Azure Active Directory, la valeur d’un administrateur n’est pas utilisée dans un enregistrement d’audit. Les enregistrements d’audit pour les activités effectuées par les administrateurs indiquent qu’un utilisateur normal (par exemple, **usertype : 0**) a effectué l’activité. La propriété **userid** identifie la personne (utilisateur ordinaire ou administrateur) qui a effectué l’activité.<br/>

Les propriétés décrites ci-dessus s’affichent également lorsque vous cliquez sur **informations supplémentaires** lorsque vous affichez les détails d’un événement spécifique.
  
![Cliquez sur Informations supplémentaires pour afficher les propriétés détaillées de l’enregistrement d’événement du journal d’audit](../media/6df582ae-d339-4735-b1a6-80914fb77a08.png)
