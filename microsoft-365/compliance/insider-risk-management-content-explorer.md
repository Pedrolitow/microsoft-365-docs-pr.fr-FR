---
title: Explorateur de contenu de gestion des risques Insiders
description: Découvrez l’Explorateur de contenu de gestion des risques inSided dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: e48b18ee905bc8589ad3fd6145630b436603ae15
ms.sourcegitcommit: f6840dfcfdbcadc53cda591fd6cf9ddcb749d303
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2020
ms.locfileid: "44327048"
---
# <a name="insider-risk-management-content-explorer"></a>Explorateur de contenu de gestion des risques Insiders

L’Explorateur de contenu de gestion des risques inSided permet aux utilisateurs d’avoir un rôle d' **enquêteur de gestion des risques Insiders** pour examiner le contexte et les détails des communications capturées dans les alertes. Pour toutes les alertes, les copies de données et les fichiers de messages sont archivés en tant qu’instantanés dans le temps des éléments, tout en conservant les fichiers et les messages d’origine dans les sources de stockage. La copie des données et des messages est transparente pour l’employé associé à l’alerte et pour le propriétaire du contenu. Les paramètres d’autorisation et les droits d’accès pour les données sont conservés pour le contenu copié, ainsi que les messages et analystes de risques, et les investigateurs ont besoin de ces autorisations et droits s’ils doivent ouvrir et afficher les fichiers. Chaque fichier et message reçoit automatiquement un ID de fichier unique dans le cas d’une gestion des risques inSided à des fins de gestion.

## <a name="column-options"></a>Options de colonne

Pour permettre aux analystes et aux investigateurs de risque d’examiner plus facilement les données et les messages capturés et d’examiner le contexte, plusieurs outils de filtrage et de tri sont inclus dans l’Explorateur de contenu. Pour le tri de base, les colonnes de classe **Date** et **fichier** prennent en charge le tri à l’aide des titres de colonne dans le volet de la file d’attente de contenu. D’autres colonnes de file d’attente peuvent être ajoutées à l’affichage pour fournir des tableaux croisés dynamiques différents sur les fichiers et les messages.

Pour ajouter ou supprimer des en-têtes de colonne pour la file d’attente de contenu, utilisez le contrôle **modifier les colonnes** et sélectionnez l’une des options de colonne suivantes. Ces colonnes correspondent aux conditions de propriété commune, de messagerie et de document prises en charge dans l’Explorateur de contenu et décrites plus loin dans cette rubrique.

| **Option de colonne** | **Description** |
|:------------------|:----------------|
| **Author** | Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et l’envoie par courrier électronique à une personne qui le charge ensuite sur SharePoint, le document conserve toujours l’auteur d’origine. |
| **Bcc** | Disponible pour les messages électroniques, les utilisateurs dans le champ de message CCI. |
| **Cc** | Disponible pour les messages électroniques, les utilisateurs dans le champ de message CC. |
| **Tracé transparent** | Chemin lisible par l’utilisateur qui décrit la source de l’élément. |
| **ID de conversation** | ID de conversation du message. |
| **Index des conversations** | Index des conversations à partir du message. |
| **Heure de création** | Heure de création du fichier ou du message électronique. |
| **Date** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de la dernière modification d’un document. |
| **Thème dominant** | Thème dominant calculé pour l’analyse. |
| **ID de jeu de courrier** | ID de groupe pour tous les messages dans le même groupe de courriers. |
| **ID de famille** | ID de famille groupe tous les éléments ; pour le courrier électronique, cela inclut le message et toutes les pièces jointes ; pour les documents, cela inclut le document et tous les éléments incorporés. |
| **Classe file** | Pour le contenu provenant de SharePoint et OneDrive : **document**; pour le contenu à partir d’Exchange : * * E-mail ou **pièce jointe**. |
| **ID de fichier** | Identificateur de document unique dans le cas. |
| **Icône de type de fichier** | Extension d’un fichier ; par exemple, docx, One, pptx ou xlsx. Il s’agit de la même propriété que la propriété de site FileExtension. |
| **ID** | Identificateur GUID du fichier. |
| **ID non modifiable** | ID non modifiable tel qu’il est stocké dans Office 365. |
| **Type inclusif** | Type inclusif calculé pour l’analyse : **0** -non inclus ; **1** -inclus ; **2** -inclus moins ; copie **3** -inclusive. |
| **Dernière modification** | Date de la dernière modification apportée à un document. |
| **Marqué comme représentant** | Un document de chaque ensemble de doublons exact est marqué comme représentant. |
| **Type de message** | Type de message électronique à rechercher. Valeurs possibles : contacts, documents, courrier électronique, données externes, télécopies, messagerie instantanée, journaux, réunions, Microsoft Teams (renvoie les éléments des conversations, des réunions et des appels dans Microsoft Teams), notes, publications, RSSFeeds, tâches, messagerie vocale |
| **Participants** | Liste de tous les participants d’un message ; par exemple, expéditeur, à, CC, CCI. |
| **ID de tableau croisé dynamique** | ID d’un tableau croisé dynamique. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. Il s’agit de la même propriété que la propriété de messagerie Received. |
| **Recipients** | Tous les champs de destinataire dans un message électronique. Ces champs sont à, CC et CCI. |
| **ID représentatif** | Identificateur numérique de chaque ensemble de doublons exacts. |
| **Sender** | Expéditeur d’un message électronique. |
| **Expéditeur/auteur** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Sent** | Date à laquelle un message électronique a été envoyé par l’expéditeur. Il s’agit de la même propriété que la propriété de messagerie Sent. |
| **Taille** | Pour la messagerie électronique et les documents, taille de l’élément (en octets). |
| **Subject** | Texte de la ligne d’objet d’un message électronique. |
| **Subject/title** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. Comme expliqué précédemment, la propriété Title est des métadonnées spécifiées dans les documents Microsoft Office. Vous pouvez taper le nom de plus d’un objet/titre, séparé par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Liste des thèmes** | Liste des thèmes telle qu’elle est calculée pour l’analyse. |
| **Titre** | Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document. |
| **To** | Destinataire d’un message électronique dans le champ à. |

## <a name="advanced-search-conditions"></a>Conditions de recherche avancées

Vous pouvez ajouter des conditions de recherche pour affiner l’étendue d’une recherche et renvoyer un ensemble de résultats plus raffiné. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est logiquement connectée à la requête de mot-clé (spécifiée dans la zone de mot clé) par un opérateur logique (représenté par c :c) qui est similaire à la fonctionnalité de l’opérateur AND. Cela signifie que les éléments doivent satisfaire à la fois la requête de mot clé et une ou plusieurs conditions à inclure dans les résultats de la recherche. C’est ainsi que les conditions contribuent à affiner vos résultats.

Pour les outils de recherche et de filtre avancés, développez le volet de **filtre** sur le côté gauche de la file d’attente de contenu. Sélectionnez le bouton **Ajouter une condition** pour ouvrir la liste condition :

### <a name="operators-used-with-conditions"></a>Opérateurs utilisés avec des conditions

|**Opérateur**|**Équivalent dans la requête**|**Description**|
|:-----------|:-------------------|:--------------|
| **After** |`property>date`| Utilisé avec les conditions de date. Renvoie les éléments qui ont été envoyés, reçus ou modifiés après la date spécifiée.|
| **Before** |`property<date`| Utilisé avec les conditions de date. Renvoie les éléments qui ont été envoyés, reçus ou modifiés avant la date spécifiée.|
| **Existant** |`date..date`| Utilisé avec les conditions de date et de taille. Lorsqu’il est utilisé avec une condition de date, renvoie les éléments qui ont été envoyés, reçus ou modifiés dans la plage de dates spécifiée. Lorsqu’il est utilisé avec une condition de taille, renvoie les éléments dont la taille est comprise dans la plage spécifiée.|
| **Contient tous les** |`(property:value) OR (property:value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui contiennent toutes les valeurs de chaîne spécifiées. |
| **Contient l’un des éléments** |`(property:value) OR (property:value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui contiennent une partie d’une ou plusieurs valeurs de chaîne spécifiées.|
| **Ne contient aucun de** |`-property:value`  <br/> `NOT property:value`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne contiennent aucune partie de la valeur de chaîne spécifiée.|
| **N’est pas égal à** |`-property=value`  <br/> `NOT property=value`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne contiennent pas la chaîne spécifique.|
| **Égal à** |`size=value`| Renvoie les éléments qui sont égaux à la taille spécifiée. <sup>1</sup>|
| **Est égal à l’un des éléments** |`(property=value) OR (property=value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui correspondent exactement à une ou plusieurs valeurs de chaîne spécifiées.|
| **Est égal à aucun** |`(property=value) OR (property=value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne correspondent à aucune ou plusieurs valeurs de chaîne spécifiées. |
| **Supérieur à** |`size>value`| Renvoie les éléments pour lesquels la propriété spécifiée est supérieure à la valeur spécifiée. <sup>1</sup>|
| **Supérieur ou égal** |`size>=value`| Renvoie les éléments pour lesquels la propriété spécifiée est supérieure ou égale à la valeur spécifiée. <sup>1</sup>|
| **Inférieur à** |`size<value`| Renvoie les éléments qui sont supérieurs ou égaux à la valeur spécifique. <sup>1</sup>|
| **Inférieur ou égal** |`size<=value`| Renvoie les éléments qui sont supérieurs ou égaux à la valeur spécifique. <sup>1</sup>|
| **Différent de** |`size<>value`| Renvoie les éléments qui ne sont pas égaux à la taille spécifiée. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> cet opérateur est disponible uniquement pour les conditions qui utilisent la propriété Size.

### <a name="common-property-conditions"></a>Conditions de propriété communes

| **Option de condition** | **Description** |
|:---------------------|:----------------|
| **Date** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de la dernière modification d’un document. |
| **Expéditeur/auteur** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur **OR**. |
| **Taille** | Pour la messagerie électronique et les documents, taille de l’élément (en octets). |
| **Subject/title** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. La propriété Title dans documents est une métadonnée spécifiée dans des documents Microsoft Office. Vous pouvez taper le nom de plus d’un objet/titre, séparé par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |

### <a name="email-property-conditions"></a>Conditions des propriétés de messagerie

Le tableau suivant répertorie les conditions de propriété de message électronique disponibles dans l’Explorateur de contenu.

| **Option de condition** | **Description** |
|:---------------------|:----------------|
| **Bcc** | Champ CCI d’un message électronique. |
| **Cc** | Champ CC d’un message électronique. |
| **Sécurité de messagerie** | Paramètre de sécurité du message. |
| **Sensibilité du courrier électronique** | Paramètre de confidentialité du message. |
| **ID de jeu de courrier** | ID de groupe pour tous les messages dans le même groupe de courriers. |
| **From** | Expéditeur d’un message électronique. |
| **Avec pièce jointe** | Indique si un message comporte une pièce jointe. Utilisez les valeurs **true** ou **false**. |
| **Importance** | Importance d'un message électronique, que l'expéditeur peut préciser lors de l'envoi. Par défaut, les messages sont envoyés avec une importance normale, à moins que l'expéditeur préfère une importance **haute** ou **faible**.   |
| **Date de fin de la réunion** | Date de fin de la réunion pour les réunions. |
| **Date de début de la réunion** | Date de début de réunion pour les réunions. |
| **Type de message** | Type de message électronique à rechercher. Valeurs possibles : contacts, documents, courrier électronique, données externes, télécopies, messagerie instantanée, journaux, réunions, Microsoft Teams (renvoie les éléments des conversations, des réunions et des appels dans Microsoft Teams), notes, publications, RSSFeeds, tâches, messagerie vocale |
| **Domaine du participant** | Liste de tous les domaines des participants d’un message. |
| **Participants** | Tous les champs de personnes dans un message électronique. Ces champs sont from, to, CC et BCC. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. |
| **Domaines de destinataires** | Liste de tous les domaines de destinataires d’un message. |
| **Sender** | Champ sender (from) pour les types de message.  Le format est **DisplayName \< SmtpAddress>**. |
| **Domaine de l’expéditeur** | Domaine de l’expéditeur. |
| **Subject** | Texte de la ligne d’objet d’un message électronique.  <br/> **Remarque :** Lorsque vous utilisez la propriété Subject dans une requête, la recherche renvoie tous les messages dans lesquels la ligne d’objet contient le texte que vous recherchez. En d’autres termes, la requête ne renvoie que les messages qui ont une correspondance exacte. Par exemple, si vous recherchez `subject:"Quarterly Financials"` , vos résultats incluent les messages dont l’objet est « trimestriel financials 2018 ». |
| **To** | Champ À d’un message électronique. |
| **Unique dans le groupe de courriers** | False s’il existe un doublon de la pièce jointe dans son jeu de courriers. |

## <a name="document-property-conditions"></a>Conditions des propriétés de document

Le tableau suivant répertorie les conditions de propriété documents disponibles dans l’Explorateur de contenu. Un grand nombre de ces conditions de propriété sont partagées avec les ensembles de révision inclus dans les [cas avancés de découverte électronique](document-metadata-fields-in-Advanced-eDiscovery.md).

| **Option de condition** | **Description** |
|:---------------------|:----------------|
| **Avocat-score de privilège client** | Avocat-score de contenu du modèle de privilège client. |
| **Author** | Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et l’envoie par courrier électronique à une personne qui le charge ensuite sur SharePoint, le document conserve toujours l’auteur d’origine. |
| **Étiquettes de conformité** | Étiquettes de conformité appliquées dans Office 365. |
| **Tracé transparent** | Chemin lisible par l’utilisateur qui décrit la source de l’élément. |
| **ID de conversation** | ID de conversation du message. |
| **Heure de création** | Heure de création du fichier ou du message électronique. |
| **Custodian** | Nom du dépositaire auquel l’élément a été associé. |
| **Thème dominant** | Thème dominant calculé pour l’analyse. |
| **ID de famille** | ID de famille groupe tous les éléments ; pour le courrier électronique, cela inclut le message et toutes les pièces jointes ; pour les documents, cela inclut le document et tous les éléments incorporés. |
| **Classe file** | Pour le contenu provenant de SharePoint et OneDrive : **document**; pour le contenu à partir d’Exchange : * * E-mail ou **pièce jointe**. |
| **Types de fichiers** | Extension d’un fichier ; par exemple, docx, One, pptx ou xlsx. |
| **A un participant à l’avocat** | True lorsqu’au moins un des participants figure dans la liste des avocats ; Sinon, la valeur est false. |
| **ID non modifiable** | ID non modifiable tel qu’il est stocké dans Office 365. |
| **Type inclusif** | Type inclusif calculé pour l’analyse : **0** -non inclus ; **1** -inclus ; **2** -inclus moins ; copie **3** -inclusive. |
| **Classe d’élément** | Classe d’élément fournie par Exchange Server ; par exemple, **IPM. Note** |
| **Dernière modification** | Date de la dernière modification apportée à un document. |
| **ID de chargement** | Load ID, dans lequel l’élément a été chargé dans un jeu de révision. |
| **Nom de l’emplacement** | Chaîne qui identifie la source de l’élément.  Pour Exchange, il s’agit de l’adresse SMTP de la boîte aux lettres. Pour SharePoint et OneDrive, l’URL de la collection de sites. |
| **Marqué comme représentant** | Un document de chaque ensemble de doublons exact est marqué comme représentant. |
| **Extension de fichier Native** | Extension native de l’élément. |
| **Nom de fichier natif** | Nom de fichier natif de l’élément. |
| **NdEtSortExclAttach** | Concaténation du jeu de messages électroniques et de la définition de l’adresse de messagerie pour un tri efficace lors de la révision ; D est ajouté en tant que préfixe aux ensembles ND et E est ajouté aux ensembles de messages électroniques. |
| **ID de tableau croisé dynamique** | ID d’un tableau croisé dynamique. |
| **Potentiellement privilégié** | True si le modèle de détection des privilèges du client estime que le document est potentiellement privilégié. |
| **État de traitement** | État de traitement après l’ajout de l’élément à un jeu de révision. |
| **Centile en lecture** | En lecture de centile pour le document en fonction de la pertinence. |
| **Score de pertinence** | Score de pertinence d’un document basé sur la pertinence. |
| **Balise de pertinence** | Score de pertinence d’un document basé sur la pertinence. |
| **ID représentatif** | Identificateur numérique de chaque ensemble de doublons exacts. |
| **Tags** | Balises appliquées dans un jeu de révision. |
| **Liste des thèmes** | Liste des thèmes telle qu’elle est calculée pour l’analyse. |
| **Titre** | Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document. |
| **A été résolu** | True si l’élément a été résolu, sinon false. |
| **Statistiques** | Nombre de mots dans un fichier. |
