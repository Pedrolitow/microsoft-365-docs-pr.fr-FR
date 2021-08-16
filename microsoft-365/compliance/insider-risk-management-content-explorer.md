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
ms.openlocfilehash: b76194037dec0ca6a660d2024a35c3376f06eab2
ms.sourcegitcommit: a0185d6b0dd091db6e1e1bfae2f68ab0e3cf05e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58246480"
---
# <a name="insider-risk-management-content-explorer"></a>Explorateur de contenu de gestion des risques internes

L’Explorateur  de contenu de gestion des risques internes permet aux utilisateurs affectés du rôle *Enquêteurs* de gestion des risques internes d’examiner le contexte et les détails du contenu associé à l’activité dans les alertes. Les données de cas dans l’Explorateur de contenu sont actualisées quotidiennement pour inclure de nouvelles activités. Pour toutes les alertes confirmées dans un cas, les copies des données et des fichiers de messages sont archivées sous forme de capture instantanée dans le temps des éléments, tout en conservant les fichiers et messages d’origine dans les sources de stockage. Si nécessaire, les fichiers de données de cas peuvent être exportés en tant que fichier de document portable (PDF) ou au format de fichier d’origine.

Dans les nouveaux cas, le contenu à remplir dans l’Explorateur de contenu prend généralement environ une heure. Pour les cas avec de grandes quantités de contenu, la création d’une capture instantanée peut prendre plus de temps. Si le contenu est toujours en cours de chargement dans l’Explorateur de contenu, vous verrez un indicateur de progression qui affiche le pourcentage d’achèvement.

Dans certains cas, les données associées à un cas peuvent ne pas être disponibles en tant que capture instantanée pour révision dans l’Explorateur de contenu. Cette situation peut se produire lorsque des données de cas ont été supprimées ou déplacées, ou lorsqu’une erreur temporaire se produit lors du traitement des données de cas. Si cette situation se produit, sélectionnez **Afficher** les fichiers dans la barre d’avertissement pour afficher les noms de fichiers, le chemin d’accès et la raison de l’échec de chaque fichier. Si nécessaire, ces informations peuvent être exportées vers un .csv (valeurs séparées par des virgules).

Si le contenu inclut des autorisations de gestion des droits de l’information, ces autorisations sont conservées pour le contenu copié et les *utilisateurs affectés* au rôle Enquêteurs de gestion des risques internes auront besoin de ces autorisations et droits s’ils ont besoin d’ouvrir et d’afficher les fichiers. Un ID de fichier unique est automatiquement attribué à chaque fichier et message dans le cas de gestion des risques internes à des fins de gestion. Les documents associés aux activités des indicateurs de périphérique ne sont pas inclus dans l’Explorateur de contenu.

> [!NOTE]
> L’Explorateur de contenu inclut les activités des utilisateurs liées aux fichiers de service Microsoft 365, telles que l’activité des utilisateurs sur SharePoint, Exchange, Microsoft Teams et OneDrive Entreprise.

## <a name="column-options"></a>Options de colonne

Pour faciliter l’examen des données et des messages capturés par les analystes et enquêteurs de risque et le contexte du cas, plusieurs outils de filtrage et de tri sont inclus dans l’Explorateur de contenu. Pour le tri de base, les colonnes **date** et classe **de** fichier la prise en charge du tri à l’aide des titres des colonnes dans le volet de file d’attente de contenu. D’autres colonnes de file d’attente peuvent être ajoutés à l’affichage pour fournir différents tableaux croisés dynamiques sur les fichiers et les messages.

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
| **Classe de fichier** | Pour le contenu de SharePoint et OneDrive : **Document**; pour le contenu de Exchange : **e-mail** ou **pièce jointe**. |
| **ID de fichier** | Identificateur de document unique dans le cas. |
| **Icône de type de fichier** | Extension d’un fichier ; par exemple, docx, 1, pptx ou xlsx. Ce champ est la même propriété que la propriété de site FileExtension. |
| **ID** | Identificateur GUID du fichier. |
| **ID non modifiable** | ID non permutable tel qu’il est stocké dans Office 365. |
| **Type d’inclusion** | Type d’inclusion calculé pour **l’analyse : 0** - non inclus ; **1** - inclus ; **2** - inclus moins ; **3** : copie incluse. |
| **Dernière modification** | Date de la dernière modification apportée à un document. |
| **Marqué comme représentant** | Un document de chaque ensemble de doublons exacts est marqué comme représentant. |
| **Type de message** | Type de message électronique à rechercher. Valeurs possibles : contacts, documents, courrier électronique, données externes, télécopies, messagerie instantanée, journaux, réunions, microsoft teams (renvoie des éléments de conversations, de réunions et d’appels en Microsoft Teams), notes, billets, flux RSS, tâches, messagerie vocale |
| **Participants** | Liste de tous les participants d’un message ; par exemple, Sender, To, Cc, Bcc. |
| **ID de tableau croisé dynamique** | ID d’un tableau croisé dynamique. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. Ce champ est la même propriété que la propriété De messagerie reçu. |
| **Recipients** | Tous les champs de destinataire dans un message électronique. Ces champs sont À, Cc et Cci. |
| **ID représentant** | Identificateur numérique de chaque ensemble de doublons exacts. |
| **Sender** | Expéditeur d’un message électronique. |
| **Sender/Author** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Types d’informations sensibles** | Types d’informations sensibles identifiés dans le contenu. |
| **Étiquettes de confidentialité** | Étiquettes de niveau de sensibilité appliquées au contenu. |
| **Sent** | Date à laquelle un message électronique a été envoyé par l’expéditeur. Ce champ est la même propriété que la propriété de messagerie envoyé. |
| **Size** | Pour la messagerie électronique et les documents, taille de l’élément (en octets). |
| **Subject** | Texte de la ligne d’objet d’un message électronique. |
| **Objet/Titre** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. Comme indiqué précédemment, la propriété Title est une métadonnées spécifiée dans Microsoft Office documents. Vous pouvez taper le nom de plusieurs sujet/titre, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Liste des thèmes** | Liste des thèmes telle que calculée pour l’analyse. |
| **Title** | Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document. |
| **To** | Destinataire d’un message électronique dans le champ À. |

## <a name="filtering"></a>Filtrage

Vous pouvez utiliser un ou plusieurs filtres pour restreindre l’étendue d’une recherche et renvoyer un ensemble de résultats plus affiné. Pour définir un filtre, sélectionnez **Filtres** en haut de la file d’attente de contenu. De nombreux filtres incluent des options de filtrage supplémentaires pour aider à affiner les résultats renvoyés par le filtre. Par exemple, le filtre *Date* inclut des contrôles pour configurer une *date de* début et une *date de* fin pour le **filtre Date.** Sélectionnez un ou plusieurs éléments de filtre dans les catégories suivantes :

### <a name="common-filters"></a>Filtres courants

| **Filtre** | **Description** |
|:---------------------|:----------------|
| **Date (UTC)** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de la dernière modification d’un document. |
| **Sender/Author** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, la personne mentionnée dans le champ *Auteur* de Office documents. Vous pouvez saisir plusieurs noms, séparés par des virgules. |
| **Source** | Emplacement du document dans votre organisation. Par exemple, un emplacement SharePoint site spécifique. |
| **Objet/Titre** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. La propriété Title dans les documents est une métadonnées spécifiée dans Microsoft Office documents. Vous pouvez taper le nom de plusieurs sujet/titre, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |

### <a name="email-filters"></a>Filtres de messagerie

| **Filtre** | **Description** |
|:---------------------|:----------------|
| **Bcc** | Champ Bcc d’un message électronique. |
| **Cc** | Champ Cc d’un message électronique. |
| **A une pièce jointe** | Indique si un message a une pièce jointe. Les valeurs sont répertoriées comme **vrai** ou **faux**. |
| **Est-ce que la pièce jointe est un e-** | Si le document est une pièce jointe, la valeur est répertoriée comme **Oui**. |
| **Document incorporé** | Si le document est incorporé dans le message électronique, la valeur est répertoriée comme **Oui**. |
| **Pièce jointe inline** | Si le document est une pièce jointe inline dans le message électronique, la valeur est répertoriée comme **Oui**. |
| **Participants** | Tous les champs de personnes dans un message électronique. Ces champs sont De, À, Cc et Cci. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. |
| **Domaines des destinataires** | Liste de tous les domaines des destinataires d’un message. |
| **Recipients** | Destinataires du message électronique. |
| **Sender** | Champ Expéditeur (De) pour les types de messages.  Le format **est \<SmtpAddress> DisplayName**. |
| **Domaine de l’expéditeur** | Domaine de l’expéditeur. |
| **To** | Champ À d’un message électronique. |
| **Unique dans l’ensemble de courriers électroniques** | False s’il existe un doublon de la pièce jointe dans son ensemble de courriers électroniques. |

## <a name="document-filters"></a>Filtres de documents

| **Filters** | **Description** |
|:---------------------|:----------------|
| **Étiquettes de conformité** | Étiquettes de conformité appliquées dans Office 365. |
| **Heure de création (UTC)** | Date et heure de création du fichier ou du message électronique. La date et l’heure sont au temps universel coordonné (UTC). |
| **Date de dernière modification (UTC)** | Date de la dernière modification apportée à un document. La date et l’heure sont au temps universel coordonné (UTC). |
| **Extension de fichier** | Type d’extension du fichier. |
| **Événements d’activité de l’utilisateur** | Activité pour les éléments liés à une activité utilisateur spécifique dans un cas.  Par exemple, lorsque vous sélectionnez un lien vers « Explorer le contenu » pour une activité dans la **page** Activité de l’utilisateur d’un cas, ce filtre est utilisé pour afficher les éléments liés à cette activité. |
| **Produit de travail** | Type de produit de travail pour le document. Par exemple, les annotations ou les balises dans le document. |
