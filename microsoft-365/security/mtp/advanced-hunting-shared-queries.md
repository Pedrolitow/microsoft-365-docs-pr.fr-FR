---
title: Utiliser des requêtes partagées dans le repérage avancé de la Protection Microsoft contre les menaces
description: Commencez immédiatement le repérage des menaces à l’aide de requêtes prédéfinies et partagées. Partagez vos requêtes au public ou au sein de votre organisation.
keywords: chasse de menace, recherche de menace, recherche de menace informatique, protection contre les menaces Microsoft, Microsoft 365, MTP, M365, recherche, requête, télémétrie, détections personnalisées, schéma, Kusto, GitHub référentiel, mes requêtes, requêtes partagées
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: lomayor
author: lomayor
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: article
ms.openlocfilehash: 6f6468117f73d6cf7079ce50e8ea951422bfc073
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42087425"
---
# <a name="use-shared-queries-in-advanced-hunting"></a>Utiliser des requêtes partagées dans un repérage avancé

**S’applique à :**
- Protection Microsoft contre les menaces

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

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

## <a name="access-queries-in-the-github-repository"></a>Accéder aux requêtes dans le référentiel GitHub  
Les chercheurs en matière de sécurité Microsoft partagent régulièrement des requêtes de repérage avancée dans un [référentiel public désigné sur GitHub](https://github.com/microsoft/MTP-AHQ). Ce référentiel est ouvert aux contributions. Si vous souhaitez contribuer, [ veuillez rejoindre GitHub gratuitement](https://github.com/).

>[!tip]
>Les chercheurs en matière de sécurité Microsoft proposent également des requêtes de repérage avancé que vous pouvez utiliser pour localiser les activités et indicateurs associés aux menaces émergentes. Ces requêtes sont fournies dans le cadre du rapport de l’[analyse des menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/threat-analytics) dans le Centre de sécurité Microsoft Defender.

## <a name="related-topics"></a>Sujets associés
- [Repérage proactif des menaces](advanced-hunting-overview.md)
- [Apprendre le langage de requête](advanced-hunting-query-language.md)
- [Repérer les menaces sur divers appareils et e-mails](advanced-hunting-query-emails-devices.md)
- [Comprendre le schéma](advanced-hunting-schema-tables.md)
- [Appliquer les meilleures pratiques de requête](advanced-hunting-best-practices.md)
