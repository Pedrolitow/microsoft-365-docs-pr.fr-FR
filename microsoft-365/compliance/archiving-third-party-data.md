---
title: Archiver des données tierces
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
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid: MOE150
ms.assetid: 0ce338d5-3666-4a18-86ab-c6910ff408cc
description: Les administrateurs peuvent importer des données tierces à partir de plateformes de réseaux sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents vers des boîtes aux lettres de votre organisation Microsoft 365. Cela vous permet d’archiver des données à partir de Facebook, de Twitter et d’autres sources de données tierces dans Microsoft 365. Vous pouvez ensuite utiliser et appliquer les fonctionnalités de conformité de Microsoft 365 (telles que la conservation légale, la découverte électronique, l’archivage inaltérable et les stratégies de rétention) pour les données tierces.
ms.openlocfilehash: 72afb48f74a30bac2904e857a33487a83eba48cd
ms.sourcegitcommit: f9b5eca20e025acc36635cbd1786ff3407295857
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/27/2020
ms.locfileid: "43027654"
---
# <a name="archive-third-party-data"></a>Archiver des données tierces

Microsoft 365 permet aux administrateurs d’importer et d’archiver des données tierces à partir de plateformes de médias sociaux, de plateformes de messagerie instantanée et de plateformes de collaboration sur des documents, vers des boîtes aux lettres de votre organisation Microsoft 365. Les exemples de sources de données tierces que vous pouvez importer dans Microsoft 365 incluent les services suivants : 
  
- **Social :** Facebook, LinkedIn, Twitter et Yammer

- **Messagerie instantanée :** Yahoo Messenger et GoogleTalk

- **Collaboration sur les documents :** Boîte et DropBox

- **Secteurs verticaux :** Gestion des relations client (par exemple, Salesforce chatter) et services financiers (par exemple, Bloomberg et Thomson Reuters)

- **Messagerie SMS/texte :** BlackBerry

Une fois les données tierces importées, vous pouvez appliquer les fonctionnalités de conformité de Microsoft 365 telles que la conservation pour litige, la découverte électronique, l’archivage inaltérable, l’audit, la conformité de la communication et les stratégies de rétention à ces données. Par exemple, lorsqu’une boîte aux lettres est placée en conservation pour litige, les données tierces sont conservées. Vous pouvez effectuer des recherches dans des données tierces à l’aide des outils eDiscovery de Microsoft. Vous pouvez également appliquer des stratégies d’archivage et de rétention à des données tierces, comme vous pouvez le faire pour Microsoft Data. En bref, l’archivage des données tierces dans Microsoft 365 peut aider votre organisation à respecter les stratégies gouvernementales et réglementaires.

Il existe deux façons d’importer et d’archiver des données tierces dans Microsoft 365 :

- **Utilisez un connecteur de données tiers dans le centre de conformité & de sécurité :** Utilisez un connecteur de données personnalisé disponible dans le centre de conformité Microsoft 365. Une fois que vous avez configuré et configuré le connecteur, il se connecte à la source de données tierce, convertit le contenu d’un élément en format de message électronique, puis importe l’élément dans une boîte aux lettres dans Microsoft 365. Actuellement, vous pouvez implémenter des connecteurs pour importer et archiver des données à partir de pages d’entreprise Facebook, de comptes Twitter d’entreprise, de LinkedIn, de Bloomberg ou de ressources humaines (RH) de votre organisation. Pour obtenir des instructions détaillées sur la configuration de l’un de ces connecteurs, voir :

   - **Facebook :** [utiliser un connecteur pour archiver des données Facebook](archive-facebook-data-with-sample-connector.md)

   - **Twitter :** [utiliser un connecteur pour archiver les données Twitter](archive-twitter-data-with-sample-connector.md)

   - **LinkedIn :** [configurer un connecteur pour l’archivage des données LinkedIn](archive-linkedin-data.md)

   - **Instant Bloomberg :** [configurer un connecteur pour l’archivage des données Bloomberg instantanées](archive-instant-bloomberg-data.md)

   - **Données RH :** [configurer un connecteur pour importer des données RH](import-hr-data.md)

- **Travaillez avec un partenaire Microsoft :** Votre organisation travaille avec un partenaire Microsoft qui fournira un connecteur personnalisé qui sera configuré pour extraire régulièrement les éléments de la source de données tierce, puis se connecter au Cloud de Microsoft par une API tierce et importer ces éléments dans Microsoft 365. Le connecteur partenaire convertit également le contenu d’un élément de la source de données tierce en message électronique, puis l’importe dans une boîte aux lettres dans Microsoft 365. Pour obtenir la liste des partenaires avec lesquels vous pouvez travailler et le processus pas à pas pour cette méthode, consultez [collaborer avec un partenaire pour archiver des données tierces dans Microsoft 365](work-with-partner-to-archive-third-party-data.md).
