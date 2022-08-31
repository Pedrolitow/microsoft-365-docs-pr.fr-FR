---
title: Utiliser des requêtes partagées dans Microsoft 365 Defender repérage avancé
description: Commencez immédiatement le repérage des menaces à l’aide de requêtes prédéfinies et partagées. Partagez vos requêtes au public ou au sein de votre organisation.
keywords: repérage avancé, repérage de menaces, repérage de cybermenaces, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, référentiel github, mes requêtes, requêtes partagées
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-security-compliance
ms.topic: article
ms.openlocfilehash: d9e90d1c4e353b9ac460420867ed56632b1e5eeb
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67477118"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Utiliser des requêtes partagées dans un repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender
- Microsoft Defender pour point de terminaison

Les requêtes de [repérage avancé](advanced-hunting-overview.md) peuvent être partagées entre les utilisateurs au sein de la même organisation. Vous pouvez également enregistrer des requêtes qui ne sont accessibles qu’à vous. Vous pouvez également trouver des requêtes de communauté qui sont partagées publiquement sur GitHub. Ces requêtes enregistrées vous permettent de poursuivre rapidement des scénarios spécifiques de chasse aux menaces sans avoir à écrire des requêtes à partir de zéro.

Sous l’onglet Requêtes de la recherche avancée, vous trouverez les menus **déroulants pour les requêtes partagées**, **Mes requêtes** et **Les requêtes de la communauté**. Vous pouvez sélectionner une flèche orientée vers le bas pour développer un menu.


:::image type="content" source="../../media/advanced-hunting-shared-queries-1.png" alt-text="Requêtes partagées, Mes requêtes et requêtes communauté dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-shared-queries-1.png":::



## <a name="save-modify-and-share-a-query"></a>Enregistrer, modifier et partager une requête
Vous pouvez enregistrer une requête nouvelle ou existante pour qu’elle soit uniquement accessible à vous-même ou partagée avec d’autres utilisateurs au sein de votre organisation. 

1. Création ou modification d’une requête. 

2. Cliquez sur le bouton déroulant **Enregistrer la requête**, puis sélectionnez **Enregistrer sous**.
    
3. Entrez un nom pour la requête. 

   :::image type="content" source="../../media/shared-query-2.png" alt-text="Nouvelle requête sur le point d’être enregistrée dans le portail Microsoft 365 Defender" lightbox="../../media/shared-query-2.png":::

4. Sélectionnez le dossier dans lequel vous voulez enregistrer la requête.
    - **Requêtes partagées** : partagées avec tous les utilisateurs de votre organisation
    - **Mes requêtes** : accessibles uniquement à vous
    
5. Cliquez sur **Enregistrer**. 

## <a name="delete-or-rename-a-query"></a>Supprimer ou renommer une requête
1. Sélectionnez les trois points à droite d’une requête que vous souhaitez renommer ou supprimer.

    :::image type="content" source="../../media/advanced-hunting-del-save-query.png" alt-text="Renommer ou supprimer une requête dans la page Repérage avancé dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-del-save-query.png":::

2. Sélectionnez **Supprimer** et confirmer la suppression. Ou sélectionnez **Renommer** et attribuer un nouveau nom à la requête.

## <a name="create-a-direct-link-to-a-query"></a>Créer un lien direct vers une requête
Pour générer un lien qui ouvre votre requête directement dans l’éditeur de requête de chasse avancé, finalisez votre requête et sélectionnez **Le lien Partager**.

## <a name="access-community-queries-in-the-github-repo"></a>Accéder aux requêtes de la communauté dans le référentiel GitHub  
Les chercheurs en matière de sécurité Microsoft partagent régulièrement des requêtes de repérage avancée dans un [référentiel public désigné sur GitHub](https://github.com/Azure/Azure-Sentinel/tree/master/Hunting%20Queries/Microsoft%20365%20Defender). Les contributions à ce référentiel sont examinées avant d’être publiées. Si vous souhaitez contribuer, [ veuillez rejoindre GitHub gratuitement](https://github.com/).

Vous pouvez facilement trouver ces requêtes dans le menu déroulant **des requêtes de la Communauté** .

:::image type="content" source="../../media/advanced-hunting-shared-queries-2.png" alt-text="Requêtes de la communauté organisées par dossier dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-shared-queries-2.png":::

Les requêtes de la communauté sont regroupées dans des dossiers tels que *Campagnes*, *Collection*, *Évasion de défense*, etc. Des informations supplémentaires sur la requête sont fournies en tant que commentaires en ligne dans la requête elle-même. 

>[!tip]
>Les chercheurs en matière de sécurité Microsoft proposent également des requêtes de repérage avancé que vous pouvez utiliser pour localiser les activités et indicateurs associés aux menaces émergentes. Ces requêtes sont fournies dans le cadre des rapports [d’analyse des menaces](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) dans Microsoft 365 Defender.


## <a name="related-topics"></a>Voir aussi
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)