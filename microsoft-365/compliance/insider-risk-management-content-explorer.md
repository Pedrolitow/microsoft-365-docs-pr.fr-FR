---
title: Explorateur de contenu de gestion des risques internes
description: En savoir plus sur l’Explorateur de contenu de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: ac5c423bffaa40d1b8cfbc50c68b1ca3f98ed0e6
ms.sourcegitcommit: 8b1bd7ca8cd81e4270f0c1e06d2b6ca81804a6aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2021
ms.locfileid: "50819849"
---
# <a name="insider-risk-management-content-explorer"></a>Explorateur de contenu de gestion des risques internes

L’Explorateur  de contenu de gestion des risques internes permet aux utilisateurs affectés au rôle *Enquêteurs* de gestion des risques internes d’examiner le contexte et les détails du contenu associé à l’activité dans les alertes. Les données de cas dans l’Explorateur de contenu sont actualisées quotidiennement pour inclure de nouvelles activités. Pour toutes les alertes confirmées dans un cas, les copies des données et des fichiers de messages sont archivées sous forme de capture instantanée dans le temps des éléments, tout en conservant les fichiers et messages d’origine dans les sources de stockage. La copie des données et des messages est transparente pour l’utilisateur associé à l’alerte et pour le propriétaire du contenu. Dans les nouveaux cas, le contenu à remplir dans l’Explorateur de contenu prend généralement environ une heure. Pour les cas avec de grandes quantités de contenu, la création d’une capture instantanée peut prendre plus de temps. Si le contenu est toujours en cours de chargement dans l’Explorateur de contenu, vous verrez un indicateur de progression qui affiche le pourcentage d’achèvement.

Dans certains cas, les données associées à un cas peuvent ne pas être disponibles en tant que capture instantanée pour révision dans l’Explorateur de contenu. Cette situation peut se produire lorsque des données de cas ont été supprimées ou déplacées, ou lorsqu’une erreur temporaire se produit lors du traitement des données de cas. Si cette situation se produit, sélectionnez **Afficher** les fichiers dans la barre d’avertissement pour afficher les noms de fichiers, le chemin d’accès et la raison de l’échec de chaque fichier. Si nécessaire, ces informations peuvent être exportées vers un fichier .csv (valeurs séparées par des virgules).

Si le contenu inclut des autorisations de gestion des droits de l’information, ces autorisations sont conservées pour le contenu copié et les *utilisateurs affectés* au rôle Enquêteurs de gestion des risques internes auront besoin de ces autorisations et droits s’ils ont besoin d’ouvrir et d’afficher les fichiers. Un ID de fichier unique est automatiquement attribué à chaque fichier et message dans le cas de gestion des risques internes à des fins de gestion. Les documents associés aux activités des indicateurs de périphérique ne sont pas inclus dans l’Explorateur de contenu.

![Explorateur de contenu de gestion des risques internes](../media/insider-risk-content-explorer.png)

>[!Note]
>L’Explorateur de contenu inclut les activités liées Microsoft Office fichiers. Les activités au niveau du site, par exemple lorsqu’un site SharePoint est supprimé ou si les autorisations de site sont modifiées, ne sont pas incluses dans l’Explorateur de contenu.

## <a name="column-options"></a>Options de colonne

Pour faciliter l’examen des données et des messages capturés et le contexte du cas par les analystes et enquêteurs de risque, plusieurs outils de filtrage et de tri sont inclus dans l’Explorateur de contenu. Pour le tri de base, les colonnes **date** et classe **de** fichier la prise en charge du tri à l’aide des titres des colonnes dans le volet de file d’attente de contenu. D’autres colonnes de file d’attente peuvent être ajoutés à l’affichage pour fournir différents tableaux croisés dynamiques sur les fichiers et les messages.

Pour ajouter ou supprimer des en-tête  de colonne pour la file d’attente de contenu, utilisez le contrôle Modifier les colonnes et sélectionnez l’une des options de colonne suivantes. Ces colonnes s’appuient sur les conditions communes, de messagerie et de propriété de document pris en charge dans l’Explorateur de contenu et répertoriées plus loin dans cet article.

| **Option de colonne** | **Description** |
|:------------------|:----------------|
| **Author** | Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et l’envoie par courrier électronique à une autre personne qui le télécharge ensuite sur SharePoint, le document conserve l’auteur d’origine. |
| **Bcc** | Disponible pour les messages électroniques, les utilisateurs dans le champ de message Bcc. |
| **Cc** | Disponible pour les messages électroniques, les utilisateurs dans le champ de message Cc. |
| **Chemin composé** | Chemin lisible par l’homme qui décrit la source de l’élément. |
| **Conversation ID** | ID de conversation du message. |
| **Index de conversation** | Index de conversation du message. |
| **Heure de création** | Heure de création du fichier ou du message électronique. |
| **Date (UTC)** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de la dernière modification d’un document. La date est au temps universel coordonné (UTC).|
| **Thème dominant** | Thème dominant tel que calculé pour l’analyse. |
| **ID de jeu de messages électroniques** | ID de groupe pour tous les messages dans le même ensemble de messages électroniques. |
| **ID de famille** | L’ID de famille rassemble tous les éléments ; pour le courrier électronique, cette colonne inclut le message et toutes les pièces jointes ; pour les documents, cette colonne inclut le document et tous les éléments incorporés. |
| **Classe de fichier** | Pour le contenu de SharePoint et OneDrive : **Document**; pour le contenu d’Exchange : **e-mail** ou **pièce jointe**. |
| **ID de fichier** | Identificateur de document unique dans le cas. |
| **Icône de type de fichier** | Extension d’un fichier ; par exemple, docx, one, pptx ou xlsx. Ce champ est la même propriété que la propriété de site FileExtension. |
| **ID** | Identificateur GUID du fichier. |
| **ID non modifiable** | ID non permutable stocké dans Office 365. |
| **Type d’inclusion** | Type d’inclusion calculé pour **l’analyse : 0** - non inclus ; **1** - inclus ; **2** - inclus moins ; **3** : copie incluse. |
| **Dernière modification** | Date de la dernière modification apportée à un document. |
| **Marqué comme représentant** | Un document de chaque ensemble de doublons exacts est marqué comme représentant. |
| **Type de message** | Type de message électronique à rechercher. Valeurs possibles : contacts, documents, courrier électronique, données externes, télécopies, messagerie instantanée, journaux, réunions, microsoft teams (renvoie des éléments de conversations, de réunions et d’appels dans Microsoft Teams), notes, billets, flux RSS, tâches, messagerie vocale |
| **Participants** | Liste de tous les participants d’un message ; par exemple, Sender, To, Cc, Bcc. |
| **ID de tableau croisé dynamique** | ID d’un tableau croisé dynamique. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. Ce champ est la même propriété que la propriété De messagerie reçu. |
| **Destinataires** | Tous les champs de destinataire dans un message électronique. Ces champs sont À, Cc et Cci. |
| **ID représentant** | Identificateur numérique de chaque ensemble de doublons exacts. |
| **Sender** | Expéditeur d’un message électronique. |
| **Sender/Author** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Types d’informations sensibles** | Types d’informations sensibles identifiés dans le contenu. |
| **Étiquettes de confidentialité** | Étiquettes de niveau de sensibilité appliquées au contenu. |
| **Sent** | Date à laquelle un message électronique a été envoyé par l’expéditeur. Ce champ est la même propriété que la propriété de messagerie envoyé. |
| **Taille** | Pour la messagerie électronique et les documents, taille de l’élément (en octets). |
| **Subject** | Texte de la ligne d’objet d’un message électronique. |
| **Objet/Titre** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. Comme indiqué précédemment, la propriété Title est une métadonnées spécifiée dans Microsoft Office documents. Vous pouvez taper le nom de plusieurs sujet/titre, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Liste des thèmes** | Liste des thèmes telle que calculée pour l’analyse. |
| **Titre** | Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document. |
| **Pour** | Destinataire d’un message électronique dans le champ À. |

## <a name="advanced-search-conditions"></a>Conditions de recherche avancées

Vous pouvez ajouter des conditions de recherche pour restreindre l’étendue d’une recherche et renvoyer un ensemble de résultats plus affiné. Chaque condition ajoute une clause à la requête de recherche qui est créée et exécutée lorsque vous démarrez la recherche. Une condition est connectée logiquement à la requête de mot clé (spécifiée dans la zone de mot clé) par un opérateur logique (représenté par c:c) qui est similaire en fonctionnalité à l’opérateur AND. Cela signifie que les éléments doivent satisfaire la requête de mot clé et une ou plusieurs conditions à inclure dans les résultats de la recherche. Cette fonctionnalité permet d’affiner vos résultats.

Pour les outils de  recherche et de filtrage avancés, développez le volet Filtre sur le côté gauche de la file d’attente de contenu. Sélectionnez **le bouton Ajouter une condition** pour ouvrir la liste des conditions :

### <a name="operators-used-with-conditions"></a>Opérateurs utilisés avec des conditions

|**Opérateur**|**Équivalent dans la requête**|**Description**|
|:-----------|:-------------------|:--------------|
| **After** |`property>date`| Utilisé avec les conditions de date. Renvoie les éléments qui ont été envoyés, reçus ou modifiés après la date spécifiée.|
| **Before** |`property<date`| Utilisé avec les conditions de date. Renvoie les éléments qui ont été envoyés, reçus ou modifiés avant la date spécifiée.|
| **Between** |`date..date`| Utilisé avec les conditions de date et de taille. Lorsqu’il est utilisé avec une condition de date, renvoie les éléments qui ont été envoyés, reçus ou modifiés dans la plage de dates spécifiée. Lorsqu’il est utilisé avec une condition de taille, renvoie les éléments dont la taille est comprise dans la plage spécifiée.|
| **Contient tous les éléments** |`(property:value) OR (property:value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui contiennent toutes les valeurs de chaîne spécifiées. |
| **Contient l’un des éléments** |`(property:value) OR (property:value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui contiennent une partie d’une ou plusieurs valeurs de chaîne spécifiées.|
| **Contient aucun des éléments** |`-property:value`  <br/> `NOT property:value`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne contiennent aucune partie de la valeur de chaîne spécifiée.|
| **N’est égal à aucun des** |`-property=value`  <br/> `NOT property=value`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne contiennent pas la chaîne spécifique.|
| **Égal à** |`size=value`| Renvoie les éléments qui sont égaux à la taille spécifiée. <sup>1</sup>|
| **Est égal à l’un des éléments** |`(property=value) OR (property=value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui correspondent exactement à une ou plusieurs valeurs de chaîne spécifiées.|
| **N’est égal à aucun des** |`(property=value) OR (property=value)`| Utilisé avec les conditions des propriétés qui spécifient une valeur de chaîne. Renvoie les éléments qui ne correspondent pas à une ou plusieurs valeurs de chaîne spécifiées. |
| **Supérieur à** |`size>value`| Renvoie les éléments dont la propriété spécifiée est supérieure à la valeur spécifiée. <sup>1</sup>|
| **Supérieur ou égal** |`size>=value`| Renvoie les éléments dont la propriété spécifiée est supérieure ou égale à la valeur spécifiée. <sup>1</sup>|
| **Inférieur à** |`size<value`| Renvoie les éléments supérieurs ou égaux à la valeur spécifique. <sup>1</sup>|
| **Inférieur ou égal** |`size<=value`| Renvoie les éléments supérieurs ou égaux à la valeur spécifique. <sup>1</sup>|
| **Différent de** |`size<>value`| Renvoie les éléments qui ne sont pas égaux à la taille spécifiée. <sup>1</sup>|

> [!NOTE]
> <sup>1</sup> Cet opérateur est disponible uniquement pour les conditions qui utilisent la propriété Size.

### <a name="common-property-conditions"></a>Conditions de propriété courantes

| **Option condition** | **Description** |
|:---------------------|:----------------|
| **Date** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de la dernière modification d’un document. |
| **Sender/Author** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur **OR**. |
| **Taille** | Pour la messagerie électronique et les documents, taille de l’élément (en octets). |
| **Objet/Titre** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. La propriété Title dans les documents est une métadonnées spécifiée dans Microsoft Office documents. Vous pouvez taper le nom de plusieurs sujet/titre, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |

### <a name="email-property-conditions"></a>Conditions de propriété de messagerie

Le tableau suivant répertorie les conditions de propriété des messages électroniques disponibles dans l’Explorateur de contenu.

| **Option condition** | **Description** |
|:---------------------|:----------------|
| **Bcc** | Champ Bcc d’un message électronique. |
| **Cc** | Champ Cc d’un message électronique. |
| **Sécurité de la messagerie** | Paramètre de sécurité du message. |
| **Sensibilité de l’e-mail** | Paramètre de sensibilité du message. |
| **ID de jeu de messages électroniques** | ID de groupe pour tous les messages dans le même ensemble de messages électroniques. |
| **From** | Expéditeur d’un message électronique. |
| **A une pièce jointe** | Indique si un message a une pièce jointe. Utilisez les valeurs **true** ou **false**. |
| **Importance** | Importance d'un message électronique, que l'expéditeur peut préciser lors de l'envoi. Par défaut, les messages sont envoyés avec une importance normale, à moins que l'expéditeur préfère une importance **haute** ou **faible**.   |
| **Date de fin de réunion** | Date de fin de réunion pour les réunions. |
| **Date de début de la réunion** | Date de début de réunion pour les réunions. |
| **Type de message** | Type de message électronique à rechercher. Valeurs possibles : contacts, documents, courrier électronique, données externes, télécopies, messagerie instantanée, journaux, réunions, microsoft teams (renvoie des éléments de conversations, de réunions et d’appels dans Microsoft Teams), notes, billets, flux rss, tâches, messagerie vocale |
| **Domaine du participant** | Liste de tous les domaines des participants d’un message. |
| **Participants** | Tous les champs de personnes dans un message électronique. Ces champs sont De, À, Cc et Cci. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. |
| **Domaines des destinataires** | Liste de tous les domaines des destinataires d’un message. |
| **Sender** | Champ Expéditeur (De) pour les types de messages.  Le format **est \<SmtpAddress> DisplayName**. |
| **Domaine de l’expéditeur** | Domaine de l’expéditeur. |
| **Subject** | Texte de la ligne d’objet d’un message électronique.  <br/> **Remarque :** Lorsque vous utilisez la propriété Subject dans une requête, la recherche renvoie tous les messages dans lesquels la ligne d’objet contient le texte que vous recherchez. En d’autres termes, la requête ne retourne pas uniquement les messages qui ont une correspondance exacte. Par exemple, si vous recherchez, vos résultats incluront des messages dont l’objet est « `subject:"Quarterly Financials"` Quarterly Financials 2018 ». |
| **Pour** | Champ À d’un message électronique. |
| **Unique dans l’ensemble de courriers électroniques** | False s’il existe un doublon de la pièce jointe dans son ensemble de courriers électroniques. |

## <a name="document-property-conditions"></a>Conditions des propriétés de document

Le tableau suivant répertorie les conditions de propriété de documents disponibles dans l’Explorateur de contenu. Bon nombre de ces conditions de propriété sont partagées avec des ensembles de révision inclus dans [les cas Advanced eDiscovery](document-metadata-fields-in-Advanced-eDiscovery.md).

| **Option condition** | **Description** |
|:---------------------|:----------------|
| **Score de privilège client-avocat** | Score de contenu du modèle de privilège client-avocat. |
| **Author** | Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et l’envoie par courrier électronique à une autre personne qui le télécharge ensuite sur SharePoint, le document conserve l’auteur d’origine. |
| **Étiquettes de conformité** | Étiquettes de conformité appliquées dans Office 365. |
| **Chemin composé** | Chemin lisible par l’homme qui décrit la source de l’élément. |
| **Conversation ID** | ID de conversation du message. |
| **Heure de création** | Heure de création du fichier ou du message électronique. |
| **Custodian** | Nom du dépositaire à qui l’élément a été associé. |
| **Thème dominant** | Thème dominant tel que calculé pour l’analyse. |
| **ID de famille** | L’ID de famille rassemble tous les éléments ; pour le courrier électronique, ce champ inclut le message et toutes les pièces jointes ; pour les documents, ce champ inclut le document et tous les éléments incorporés. |
| **Classe de fichier** | Pour le contenu de SharePoint et OneDrive : **Document**; pour le contenu à partir d’Exchange : **Courrier électronique ou **pièce jointe**. |
| **Types de fichiers** | Extension d’un fichier ; par exemple, docx, one, pptx ou xlsx. |
| **A un participant avocat** | True lorsqu’au moins l’un des participants est trouvé dans la liste des avocats ; Sinon, la valeur est False. |
| **ID non modifiable** | ID non permutable stocké dans Office 365. |
| **Type d’inclusion** | Type d’inclusion calculé pour **l’analyse : 0** - non inclus ; **1** - inclus ; **2** - inclus moins ; **3** : copie incluse. |
| **Classe d’élément** | Classe d’élément fournie par le serveur Exchange ; par exemple, **IPM. Remarque** |
| **Dernière modification** | Date de la dernière modification apportée à un document. |
| **ID de chargement** | ID de chargement, dans lequel l’élément a été chargé dans un jeu à réviser. |
| **Nom de l’emplacement** | Chaîne qui identifie la source de l’élément.  Pour exchange, ce champ sera l’adresse SMTP de la boîte aux lettres. Pour SharePoint et OneDrive, l’URL de la collection de sites. |
| **Marqué comme représentant** | Un document de chaque ensemble de doublons exacts est marqué comme représentant. |
| **Extension de fichier native** | Extension native de l’élément. |
| **Nom de fichier natif** | Nom de fichier natif de l’élément. |
| **NdEtSortExclAttach** | Concatenation de l’ensemble de messages électroniques et de l’ensemble de ND pour un tri efficace au moment de la révision ; D est ajouté en tant que préfixe aux jeux de ND et E aux ensembles de courriers électroniques. |
| **ID de tableau croisé dynamique** | ID d’un tableau croisé dynamique. |
| **Potentiellement privilégié** | True si le modèle de détection des privilèges client-avocat considère le document comme potentiellement privilégié. |
| **État du traitement** | État du traitement après l’ajout de l’élément à un jeu à réviser. |
| **Lire le centile** | Lire le centile du document en fonction de la pertinence. |
| **Score de pertinence** | Score de pertinence d’un document en fonction de la pertinence. |
| **Balise de pertinence** | Score de pertinence d’un document en fonction de la pertinence. |
| **ID représentant** | Identificateur numérique de chaque ensemble de doublons exacts. |
| **Tags** | Balises appliquées dans un jeu à réviser. |
| **Liste des thèmes** | Liste des thèmes telle que calculée pour l’analyse. |
| **Titre** | Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document. |
| **A été corrigé** | True si l’élément a été corrigé, sinon False. |
| **Statistiques** | Nombre de mots dans un fichier. |
