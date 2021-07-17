---
title: Prévisualiser et tester Windows 11 avec Microsoft Manged Desktop
description: Comment obtenir Windows 11 dans votre environnement
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 8dee18909d82656bcfb3e63fdc078328c678e660
ms.sourcegitcommit: ea8de1b48adb6df92fb9351ea862184a9f16cbbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53461386"
---
# <a name="preview-and-test-windows-11-with-microsoft-managed-desktop"></a>Prévisualiser et tester Windows 11 avec Microsoft Manged Desktop

 Comment s’inscrire et participer au programme de test de compatibilité Windows 11 au sein de votre environnement Microsoft Manged Desktop. Pour plus d’informations Windows 11 et Microsoft Manged Desktop en général, voir [Windows 11 et Microsoft Manged Desktop](../intro/win11-overview.md). 

## <a name="check-device-eligibility"></a>Vérifier l’éligibilité de l’appareil

À ce jour, plus de 95 % des appareils Microsoft Manged Desktop répondent aux critères [d’éligibilité Windows 11](/windows/whats-new/windows-11-requirements). Vous pouvez demander des détails sur l’état d’éligibilité de vos appareils Microsoft Manged Desktop. Pour déposer la demande, suivez les étapes suivantes :

1. Ouvrez une nouvelle demande de service avec l Microsoft Manged Desktop d’ingénierie de service. Si vous avez besoin d’informations supplémentaires sur la façon de déposer la demande, consultez le [support de l’administrateur.](admin-support.md)
2. Utilisez ces valeurs pour les champs :
    - Titre : éligibilité Windows appareil 11
    - Type de demande : demande d’informations
    - Catégorie : Appareils
    - Sous-catégorie : Autre


## <a name="add-devices-to-the-windows-11-test-group"></a>Ajouter des appareils au groupe de test Windows 11

Commencez par ajouter des appareils au groupe d’appareils (**\[ Modern Workplace Windows \] 11 Pre-Release Test Devices**) créé pour tester et évaluer Windows 11. Les appareils de ce groupe obtiennent de nouvelles builds Windows 11 et Microsoft Manged Desktop configurations de base dès qu’elles sont disponibles et sont surveillées pour les problèmes de fiabilité.

Vous pouvez choisir n’importe quel appareil existant ou nouveau pour le test Windows 11, mais vous ne devez pas inscrire d’appareils de production dans ce groupe en raison du risque élevé de défauts ou de problèmes de compatibilité dans les builds pré-publiées. Les affectations de groupe d’appareils précédentes sont supprimées lors de l’affectation à ce groupe.

Pour inscrire vos appareils dans le groupe de test pré-version :

1. Ouvrez une nouvelle demande de service avec l Microsoft Manged Desktop d’ingénierie de service.
2. Utilisez ces valeurs pour les champs :
    - Titre : Windows 11 inscription à la compatibilité
    - Type de demande : demande de modification
    - Catégorie : Appareils
    - Sous-catégorie : affectation de groupe de déploiement
3. Dans le champ description, listez les numéros de série des appareils que vous souhaitez utiliser pour les tests Windows 11. Notez les appareils spécifiés qui, le cas sont, ne sont pas encore déployés dans votre Microsoft Manged Desktop client.

## <a name="prioritize-applications-to-submit-to-test-base"></a>Hiérarchiser les applications à soumettre à la base de test

Les applications critiques pour l’entreprise sont les meilleures candidats pour une validation plus importante dans un environnement Windows 11. Nous pouvons vous aider à hiérarchiser les applications pour Windows 11 en fonction des données d’utilisation et de fiabilité. Pour demander nos recommandations, suivez les étapes suivantes :

1. Ouvrez une nouvelle demande de service avec l Microsoft Manged Desktop d’ingénierie de service. Si vous avez besoin d’informations supplémentaires sur la façon de déposer la demande, consultez le [support de l’administrateur.](admin-support.md)
2. Utilisez ces valeurs pour les champs :
    - Titre : Windows 11 candidats à la base de test
    - Type de demande : demande d’informations
    - Catégorie : Applications
    - Sous-catégorie : Autre

## <a name="report-issues"></a>Signaler des problèmes

Si vous rencontrez Windows 11 problèmes de compatibilité avec vos applications métier ou Microsoft 365, signalez-nous ces problèmes pour examen et correction. Pour signaler un problème, suivez les étapes suivantes :

1. Ouvrez une nouvelle demande de service avec l Microsoft Manged Desktop d’ingénierie de service.
2. Utilisez ces valeurs pour les champs :
    - Titre : Windows 11 tests de compatibilité
    - Type de demande : Incident
    - Catégorie : Appareils
    - Sous-catégorie : mise à Windows/mise à jour
3. Décrivez le comportement et la façon dont il risque d’entraver votre activité dans un environnement de production.

Microsoft Manged Desktop trie et gère les problèmes avec les builds pré-publiées en fonction de l’impact sur la productivité. Bien que la description de notre service ne couvre pas les problèmes avec les builds pré-publiées, nous allons nous entretenir avec les administrateurs des clients pour nous assurer que les problèmes qui bloquent la productivité des utilisateurs sont résolus avant de commencer la migration au sein d’un client donné.
