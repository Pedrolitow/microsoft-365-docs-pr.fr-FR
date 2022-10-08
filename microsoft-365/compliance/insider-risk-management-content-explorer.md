---
title: Explorateur de contenu de gestion des risques internes
description: En savoir plus sur l’Explorateur de contenu de gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- tier1
- purview-compliance
ms.openlocfilehash: 9bcd30f68f73d3596a55e1cd74a77aff32889df7
ms.sourcegitcommit: 50da6f1f6ef2274c17ed9729e7ad84395b0a9be2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/08/2022
ms.locfileid: "68503927"
---
# <a name="insider-risk-management-content-explorer"></a>Explorateur de contenu de gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou involontaires, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Créés avec la confidentialité par conception, les utilisateurs sont pseudonymes par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

**L’Explorateur de** contenu de gestion des risques internes permet aux utilisateurs ayant le rôle *d’enquêteurs de gestion des risques internes* d’examiner le contexte et les détails du contenu associé à l’activité dans les alertes. Les données de cas dans l’Explorateur de contenu sont actualisées quotidiennement pour inclure une nouvelle activité. Pour toutes les alertes confirmées dans un cas, les copies des fichiers de données et de messages sont archivées en tant qu’instantané dans le temps des éléments, tout en conservant les fichiers et messages d’origine dans les sources de stockage. Si nécessaire, les fichiers de données de cas peuvent être exportés en tant que fichier de document portable (PDF) ou au format de fichier d’origine.

Pour les nouveaux cas, le remplissage du contenu dans l’Explorateur de contenu prend généralement environ une heure. Pour les cas avec de grandes quantités de contenu, la création d’un instantané peut prendre plus de temps. Si le contenu est toujours en cours de chargement dans l’Explorateur de contenu, vous verrez un indicateur de progression qui affiche le pourcentage d’achèvement.

Dans certains cas, les données associées à un cas peuvent ne pas être disponibles en tant qu’instantané pour révision dans l’Explorateur de contenu. Cette situation peut se produire lorsque des données de cas ont été supprimées ou déplacées, ou lorsqu’une erreur temporaire se produit lors du traitement des données de cas. Si cette situation se produit, sélectionnez **Afficher les fichiers** dans la barre d’avertissement pour afficher les noms de fichiers, le chemin d’accès et la raison de l’échec de chaque fichier. Si nécessaire, ces informations peuvent être exportées vers un fichier .csv (valeurs séparées par des virgules).

Si le contenu inclut des autorisations De gestion des droits relatifs à l’information, ces autorisations sont conservées pour le contenu copié et les utilisateurs auxquels le rôle *Insider Risk Management Investigators* a été attribué auront besoin de ces autorisations et droits s’ils ont besoin d’ouvrir et d’afficher les fichiers. Un ID de fichier unique est automatiquement attribué à chaque fichier et message dans le cas de gestion des risques internes à des fins de gestion. Les documents associés aux activités d’indicateur d’appareil ne sont pas inclus dans l’Explorateur de contenu.

> [!NOTE]
> L’Explorateur de contenu inclut les activités des utilisateurs liées aux fichiers de service Microsoft 365, telles que l’activité utilisateur sur SharePoint, Exchange, Microsoft Teams et OneDrive Entreprise.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="column-options"></a>Options de colonne

Pour faciliter l’examen des données et des messages capturés par les analystes et les enquêteurs des risques et l’examen du contexte du cas, plusieurs outils de filtrage et de tri sont inclus dans l’Explorateur de contenu. Pour le tri de base, les colonnes de classe **Date** et **Fichier** prennent en charge le tri à l’aide des titres des colonnes dans le volet file d’attente de contenu. D’autres colonnes de file d’attente sont disponibles à ajouter à la vue pour fournir différents tableaux croisés dynamiques sur les fichiers et les messages.

Pour ajouter ou supprimer des en-têtes de colonne pour la file d’attente de contenu, utilisez le contrôle **Modifier les colonnes** et sélectionnez parmi les options de colonne suivantes. Ces colonnes correspondent aux conditions de propriétés communes, de courrier électronique et de document prises en charge dans l’Explorateur de contenu et répertoriées plus loin dans cet article.

| **Option Colonne** | **Description** |
|:------------------|:----------------|
| **Author** | Champ Auteur des documents Office (subsiste si un document est copié). Par exemple, si un utilisateur crée un document et qu’il l’envoie par e-mail à quelqu’un d’autre qui le charge ensuite dans SharePoint, le document conserve l’auteur d’origine. |
| **Bcc** | Disponible pour les messages électroniques, les utilisateurs dans le champ de message CCI. |
| **Cc** | Disponible pour les messages électroniques, les utilisateurs dans le champ Cc message. |
| **Chemin composé** | Chemin lisible par l’homme qui décrit la source de l’élément. |
| **Conversation ID** | ID de conversation du message. |
| **Index de conversation** | Index de conversation du message. |
| **Heure de création** | Heure de création du fichier ou de l’e-mail. |
| **Date (UTC)** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de dernière modification d’un document. La date est en temps universel coordonné (UTC).|
| **Thème dominant** | Thème dominant tel qu’il est calculé pour l’analytique. |
| **Email définir l’ID** | ID de groupe pour tous les messages du même ensemble de courriers électroniques. |
| **ID de famille** | L’ID de famille regroupe tous les éléments; pour l’e-mail, cette colonne inclut le message et toutes les pièces jointes ; pour les documents, cette colonne inclut le document et tous les éléments incorporés. |
| **Classe de fichier** | Pour le contenu de SharePoint et OneDrive : **Document** ; pour le contenu d’Exchange : **Email** ou **pièce jointe**. |
| **ID de fichier** | Identificateur de document unique dans le cas. |
| **Icône de type de fichier** | Extension d’un fichier ; par exemple, docx, un, pptx ou xlsx. Ce champ est la même propriété que la propriété de site FileExtension. |
| **ID** | Identificateur GUID du fichier. |
| **ID non modifiable** | ID immuable tel qu’il est stocké dans Office 365. |
| **Type inclusif** | Type inclusif calculé pour l’analytique : **0** - non inclusif ; **1** - inclus; **2** - inclus moins; **3** - copie inclusive. |
| **Dernière modification** | Date de la dernière modification apportée à un document. |
| **Marqué comme représentant** | Un document de chaque jeu de doublons exacts est marqué comme représentant. |
| **Type de message** | Type de message électronique à rechercher. Valeurs possibles : contacts, documents, e-mail, données externes, télécopies, messagerie instantanée, journaux, réunions, équipes Microsoft (renvoie des éléments de conversations, de réunions et d’appels dans Microsoft Teams), notes, billets, flux RSS, tâches, messagerie vocale |
| **Participants** | Liste de tous les participants d’un message ; par exemple, Sender, To, Cc, CCI. |
| **ID de tableau croisé dynamique** | ID d’un tableau croisé dynamique. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. Ce champ est la même propriété que la propriété De messagerie reçue. |
| **Destinataires** | Tous les champs du destinataire dans un e-mail. Ces champs sont To, Cc et Cci. |
| **ID représentatif** | Identificateur numérique de chaque jeu de doublons exacts. |
| **Sender** | Expéditeur d’un message électronique. |
| **Expéditeur/auteur** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, personne mentionnée dans le champ Auteur des documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Types d’informations sensibles** | Types d’informations sensibles identifiés dans le contenu. |
| **Étiquettes de confidentialité** | Étiquettes de confidentialité appliquées au contenu. |
| **Sent** | Date à laquelle un message électronique a été envoyé par l’expéditeur. Ce champ est la même propriété que la propriété d’e-mail envoyé. |
| **Size** | Pour la messagerie électronique et les documents, taille de l’élément (en octets). |
| **Sujet** | Texte de la ligne d’objet d’un message électronique. |
| **Objet/titre** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. Comme expliqué précédemment, la propriété Title est des métadonnées spécifiées dans les documents Microsoft Office. Vous pouvez taper le nom de plusieurs sujets/titres, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |
| **Liste de thèmes** | Les thèmes sont répertoriés comme calculés pour l’analytique. |
| **Titre** | Titre du document. Cette propriété correspond aux métadonnées spécifiées dans les documents Office. Il est différent du nom de fichier du document. |
| **Pour** | Destinataire d’un e-mail dans le champ À. |

## <a name="filtering"></a>Filtrage

Vous pouvez utiliser un ou plusieurs filtres pour affiner l’étendue d’une recherche et retourner un ensemble de résultats plus affiné. Pour définir un filtre, sélectionnez **Filtres** en haut de la file d’attente de contenu. De nombreux filtres incluent des options de filtrage supplémentaires pour aider à affiner les résultats retournés par le filtre. Par exemple, le filtre *Date* inclut des contrôles pour configurer une *date de début* et une *date de fin* pour le filtre **Date** . Sélectionnez un ou plusieurs éléments de filtre dans les catégories suivantes :

### <a name="common-filters"></a>Filtres courants

| **Filtre** | **Description** |
|:---------------------|:----------------|
| **Date (UTC)** | Pour la messagerie électronique, date à laquelle un message a été reçu par un destinataire ou envoyé par l’expéditeur. Pour les documents, date de dernière modification d’un document. |
| **Expéditeur/auteur** | Pour la messagerie électronique, personne ayant envoyé le message. Pour les documents, la personne citée dans le champ *Auteur* à partir de documents Office. Vous pouvez saisir plusieurs noms, séparés par des virgules. |
| **Source** | Emplacement du document dans votre organisation. Par exemple, un emplacement de site SharePoint spécifique. |
| **Objet/titre** | Pour la messagerie électronique, texte de la ligne d’objet d’un message. Pour les documents, titre du document. La propriété Title dans les documents est des métadonnées spécifiées dans les documents Microsoft Office. Vous pouvez taper le nom de plusieurs sujets/titres, séparés par des virgules. Deux ou plusieurs valeurs sont connectées logiquement par l’opérateur OR. |

### <a name="email-filters"></a>filtres Email

| **Filtre** | **Description** |
|:---------------------|:----------------|
| **Bcc** | Champ Cci d’un e-mail. |
| **Cc** | Champ Cc d’un e-mail. |
| **A une pièce jointe** | Indique si un message a une pièce jointe. Les valeurs sont répertoriées comme **true** ou **false**. |
| **Pièce jointe d’e-mail** | Si le document est une pièce jointe, la valeur est répertoriée comme **Oui**. |
| **Document incorporé** | Si le document est incorporé dans le message électronique, la valeur est répertoriée comme **Oui**. |
| **Est inclus dans la pièce jointe** | Si le document est une pièce jointe incluse dans le message électronique, la valeur est répertoriée comme **Oui**. |
| **Participants** | Tous les champs de personnes dans un e-mail. Ces champs sont From, To, Cc et Cci. |
| **Received** | Date à laquelle un message électronique a été reçu par un destinataire. |
| **Domaines de destinataire** | Liste de tous les domaines des destinataires d’un message. |
| **Destinataires** | Destinataires du message électronique. |
| **Sender** | Champ Expéditeur (à partir) pour les types de messages.  Format **DisplayName \<SmtpAddress>**. |
| **Domaine de l’expéditeur** | Domaine de l’expéditeur. |
| **Pour** | Champ À d’un message électronique. |
| **Unique dans l’ensemble de courriers électroniques** | False s’il existe un doublon de la pièce jointe dans son jeu de courriers électroniques. |

## <a name="document-filters"></a>Filtres de document

| **Filters** | **Description** |
|:---------------------|:----------------|
| **Étiquettes de conformité** | Étiquettes de conformité appliquées dans Office 365. |
| **Heure de création (UTC)** | Date et heure de création du fichier ou du message électronique. La date et l’heure sont en temps universel coordonné (UTC). |
| **Date de dernière modification (UTC)** | Date de la dernière modification apportée à un document. La date et l’heure sont en temps universel coordonné (UTC). |
| **Extension de fichier** | Type d’extension du fichier. |
| **Événements d’activité utilisateur** | Activité pour les éléments liés à une activité utilisateur spécifique dans un cas.  Par exemple, lorsque vous sélectionnez un lien vers « Explorer le contenu » pour une activité dans la page **Activité** utilisateur d’un cas, ce filtre est utilisé pour afficher les éléments liés à cette activité. |
| **Produit de travail** | Type de produit de travail pour le document. Par exemple, des annotations ou des balises dans le document. |
