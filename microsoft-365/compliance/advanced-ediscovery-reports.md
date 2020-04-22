---
title: Rapports avancés de découverte électronique
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ROBOTS: NOINDEX, NOFOLLOW
description: ''
ms.openlocfilehash: 75e376288a85ca6def5cf3c3037f2faee57de63b
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43632269"
---
# <a name="advanced-ediscovery-reports-preview"></a>Rapports eDiscovery avancés (aperçu)

Les rapports avancés de découverte électronique vous aident à agréger des données de cas dans votre organisation afin de rationaliser l’analyse des données et la création de rapports organisationnels. La fonctionnalité Advanced eDiscovery Reports inclut plusieurs rapports intégrés pour vous aider à répondre à vos questions :

- Combien de dépositaires actifs s’y trouvent pour tous les cas dans mon organisation ?

- Combien de sources de données sont en attente pour tous les cas dans mon organisation ?

- Combien de notifications d’attente ont été émises au cours du dernier mois pour tous les cas de mon organisation ?

- Combien de cas actifs et fermés existe-t-il dans mon organisation ?

## <a name="before-you-begin"></a>Avant de commencer

- Pour accéder aux rapports eDiscovery avancés, vous devez être membre du groupe de rôles d’administrateur eDiscovery. En tant que membre de ce groupe de rôles, vous disposez des autorisations nécessaires pour afficher, filtrer et exporter les données dans les rapports. Pour plus d'informations, voir [Attribution d'autorisations eDiscovery](assign-ediscovery-permissions.md).

- Les rapports eDiscovery avancés sont actualisés quotidiennement. Par conséquent, il peut y avoir un retard lors de la création de nouveaux cas, de dépositaires, de sources de données et de communications, et de leur affichage dans le rapport correspondant.

Pour accéder aux rapports avancés eDiscovery :

1. Allez à https://protection.office.com.
  
2. Connectez-vous à l’aide de votre compte professionnel ou scolaire.
  
3. Dans le centre de sécurité & conformité, cliquez sur **ediscovery > Advanced eDiscovery**.
  
   Sur la page d’accueil de la **découverte électronique avancée** , les onglets des rapports sur les cas, les dépositaires, les sources de données et les communications s’affichent dans la partie supérieure de la page. 
  
   ![Rapports eDiscovery avancés sur la page d’accueil](../media/report-home.png)

5. Pour afficher un rapport, cliquez sur un onglet de rapport, puis si nécessaire, vous pouvez effectuer l’une des opérations suivantes :

   ![Vous pouvez filtrer ou télécharger des données de rapport](../media/AeDReportsFilterDownload.png)

   a. Cliquez sur **filtre** pour affiner les données du rapport. Vous pouvez filtrer sur différentes propriétés pour chaque rapport.
  
   b. Cliquez sur **Télécharger vers CSV** pour exporter les données du rapport dans un fichier CSV.

## <a name="case-report"></a>Rapport de cas

Le rapport de cas agrège les informations sur les cas de découverte électronique en cours et fermés au sein de votre organisation.

|Colonne        |Description|
|:-------------|:-------------|
|ID de cas | Identificateur unique de chaque cas.| 
|Nom de la case | Nom défini par l’utilisateur de l’incident.|
|Statut | Indique si la case est active ou fermée.|
|Date de création |Date de création du cas. Les dates sont au format UTC.|
|Dernière modification |Date de clôture ou de dernière mise à jour du cas. Les dates sont au format UTC.| 
|||

## <a name="custodian-report"></a>Rapport sur le dépositaire

Dans le flux de travail de découverte électronique, les personnes qui font l’objet d’un cas juridique ou d’une enquête sont appelés *dépositaires de données* (ou seulement des *dépositaires*) et sont définis comme des « personnes ayant le contrôle administratif d’un document ou d’un fichier électronique ». Le rapport dépositaire vous permet d’identifier tous les dépositaires dont les sources de données sont bloquées dans tous les cas de votre organisation.

|Colonne         |Description|
|:-------------|:-------------|
|Nom du dépositaire| Nom du dépositaire dans Active Directory.|
|NOM UPN du dépositaire | Nom d’utilisateur principal du dépositaire.|
|ID du dépositaire | Identificateur unique du dépositaire dans une casse donnée. |
|Nom de la case | Nom défini par l’utilisateur de l’incident.|
|État de suspension | Indique si le dépositaire est actuellement bloqué ou s’il a été lancé à partir de l’incident.|
|ID de cas | Identificateur unique de la demande de devis.|
|État de la communication |Indique si le dépositaire a reçu une notification de suspension légale ou non. |
|Dépositaire ajouté | Date à laquelle le dépositaire a été ajouté à la demande de devis. Les dates sont au format UTC.|
|||

## <a name="data-source-report"></a>Rapport de source de données

Vous pouvez utiliser un cas avancé de découverte électronique pour créer des suspensions afin de conserver le contenu qui peut être pertinent pour le cas. À l’aide des fonctionnalités de mise en attente avancée de eDiscovery, vous pouvez placer des suspensions sur des dépositaires et leurs sources de données. En outre, vous pouvez placer un blocage non privative de direction sur les boîtes aux lettres et les comptes OneDrive entreprise. Vous pouvez utiliser le rapport des sources de données pour agréger des détails sur les emplacements de contenu en attente pour tous les cas de votre organisation.

|Colonne        |Description|
| -------------|-------------|
|ID de cas |Identificateur unique de chaque cas. |
|Charge de travail |Indique le type d’emplacement de contenu placé en conservation (par exemple, Exchange ou SharePoint).
|Nom de l’emplacement |Indique l’adresse SMTP (pour les boîtes aux lettres Exchange) ou l’URL (pour les sites SharePoint) de l’emplacement du contenu. | 
|ID du dépositaire |Si la source de données appartient à un dépositaire, cette colonne indique l’identificateur unique du dépositaire dans un cas donné. Cette colonne est null pour les emplacements non privatives de cœur.|
|Nom du dépositaire |Nom du dépositaire dans Active Directory.| 
|Nom de la case |Nom défini par l’utilisateur de l’incident.| 
|Statut |Indique si l’emplacement de contenu est actuellement en conservation. | 
|ID de stratégie de conservation |Identificateur unique de la conservation qui contient l’emplacement du contenu. | 
|Date de création de la conservation |Indique la date de création de la stratégie de blocage. Les dates sont au format UTC. | 
|Nom de la stratégie de blocage |Nom de la conservation qui contient l’emplacement du contenu. |
|Date de modification de la conservation |Date de la dernière modification de la conservation. Les dates sont au format UTC.| 
|Suspension de la dernière modification par|Nom de l’utilisateur qui a modifié la conservation en dernier.| 
|||

## <a name="communication-report"></a>Rapport de communication

Votre organisation peut émettre des notifications de conservation légale pour informer les dépositaires de leur obligation de conserver les informations pertinentes dans le cadre d’un cas juridique ou d’une enquête. Vous pouvez utiliser le rapport de communication pour afficher des données d’agrégation sur les accusés de réception, les rappels, les escalades et d’autres types de communications.

|Colonne         |Description|
| -------------|-------------|
|ID de cas | Identificateur unique de la demande de devis.|
|Nom de la case | Nom défini par l’utilisateur de l’incident.|
|ID du dépositaire |Identificateur unique du dépositaire dans un cas donné.|
|Nom du dépositaire |Nom du dépositaire.|
|Type de notification |Indique le type de notification qui a été émise pour le dépositaire.|
|Officier émetteur |Nom de l’utilisateur qui a émis la notification de suspension légale.|
|Notification, événement|Indique le message de notification de conservation légale envoyé à l’utilisateur. Les valeurs possibles sont les suivantes : rappel, escalade, accusé de réception et émission de blocage.|
|Date d’envoi |Date à laquelle la communication a été émise. Pour les accusés de réception, cette colonne indique le moment où la notification a été reconnue par le dépositaire. Les dates sont au format UTC.|
|||
