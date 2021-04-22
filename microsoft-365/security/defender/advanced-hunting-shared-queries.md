---
title: Utiliser des requêtes partagées dans le hunting avancé Microsoft 365 Defender
description: Commencez immédiatement le repérage des menaces à l’aide de requêtes prédéfinies et partagées. Partagez vos requêtes au public ou au sein de votre organisation.
keywords: repérage avancé, repérage de menace, repérage de cybermenace, Microsoft 365 Defender, microsoft 365, m365, recherche, requête, télémétrie, détections personnalisées, schéma, kusto, référentiel github, mes requêtes, requêtes partagées
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: maccruz
author: schmurky
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: article
ms.technology: m365d
ms.openlocfilehash: 0194a752a0050fe68c5372bbfc93ea5f17d1d8e6
ms.sourcegitcommit: a8d8cee7df535a150985d6165afdfddfdf21f622
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2021
ms.locfileid: "51935760"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Utiliser des requêtes partagées dans un repérage avancé

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender



Les requêtes de [repérage avancé](advanced-hunting-overview.md) peuvent être partagées entre les utilisateurs au sein de la même organisation. Vous pouvez également trouver des requêtes partagées publiquement sur GitHub. Ces requêtes vous permettent d’effectuer rapidement des scénarios de repérage de menace spécifiques sans avoir à créer des requêtes.

![Image des requêtes partagées](../../media/advanced-hunting-shared-queries.png)

## <a name="save-modify-and-share-a-query"></a>Enregistrer, modifier et partager une requête
Vous pouvez enregistrer une requête nouvelle ou existante pour qu’elle soit uniquement accessible à vous-même ou partagée avec d’autres utilisateurs au sein de votre organisation. 

1. Création ou modification d’une requête. 

2. Cliquez sur le bouton déroulant **Enregistrer la requête**, puis sélectionnez **Enregistrer sous**.
    
3. Entrez un nom pour la requête. 

   ![Image de l’enregistrement d’une requête](../../media/advanced-hunting-save-query.png)

4. Sélectionnez le dossier dans lequel vous voulez enregistrer la requête.
    - **Requêtes partagées** : partagées avec tous les utilisateurs de votre organisation
    - **Mes requêtes** : accessibles uniquement à vous
    
5. Cliquez sur **Enregistrer**. 

## <a name="delete-or-rename-a-query"></a>Supprimer ou renommer une requête
1. Cliquez avec le bouton droit de la souris sur une requête que vous voulez renommer ou supprimer.

    ![Image de suppression de la requête](../../media/advanced_hunting_delete_rename.png)

2. Sélectionnez **Supprimer** et confirmer la suppression. Ou sélectionnez **Renommer** et attribuer un nouveau nom à la requête.

## <a name="create-a-direct-link-to-a-query"></a>Créer un lien direct vers une requête
Pour générer un lien qui ouvre votre requête directement dans l'éditeur de requête de recherche avancée, finalisez votre requête et sélectionnez **le lien partager.**

## <a name="access-queries-in-the-github-repository"></a>Accéder aux requêtes dans le référentiel GitHub  
Les chercheurs en matière de sécurité Microsoft partagent régulièrement des requêtes de repérage avancée dans un [référentiel public désigné sur GitHub](https://aka.ms/hunting-queries). Ce référentiel est ouvert aux contributions. Si vous souhaitez contribuer, [ veuillez rejoindre GitHub gratuitement](https://github.com/).

>[!tip]
>Les chercheurs en matière de sécurité Microsoft proposent également des requêtes de repérage avancé que vous pouvez utiliser pour localiser les activités et indicateurs associés aux menaces émergentes. Ces requêtes sont fournies dans le cadre du rapport de l’[analyse des menaces](/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) dans le Centre de sécurité Microsoft Defender.

## <a name="related-topics"></a>Sujets associés
- [Vue d’ensemble du repérage avancé](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Utiliser les résultats d’une requête](advanced-hunting-query-results.md)
- [Repérer des menaces sur les appareils, les e-mails, les applications et les identités](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)