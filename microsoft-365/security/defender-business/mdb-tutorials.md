---
title: Didacticiels et simulations dans Microsoft Defender pour entreprises
description: Découvrez plusieurs didacticiels pour vous aider à commencer à utiliser Defender entreprise.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 029be738b8c916ec4eb16970ae2d2ff3c460f639
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66771971"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Didacticiels et simulations dans Microsoft Defender pour entreprises

Cet article décrit certains scénarios à essayer, ainsi que plusieurs didacticiels et simulations disponibles pour Defender Entreprise. Ces ressources montrent comment Defender entreprise peut fonctionner pour votre entreprise.


## <a name="try-these-scenarios"></a>Essayez ces scénarios

Le tableau suivant récapitule plusieurs scénarios à essayer avec Defender entreprise.

| Scénario  | Description  |
|---------|---------|
| Intégrer des appareils en utilisant un script local     | Dans Defender entreprise, vous pouvez intégrer des appareils Windows et Mac à l’aide d’un script que vous téléchargez et exécutez sur chaque appareil. Le script crée une approbation avec Azure Active Directory (Azure AD), si cette approbation n’existe pas déjà ; inscrit l’appareil avec Microsoft Intune, si vous avez Intune; et l’intègre à Defender entreprise. Pour plus d’informations, consultez [Intégrer des appareils à Defender entreprise](mdb-onboard-devices.md).         |
| Intégrer des appareils à l’aide du Centre d’administration Microsoft Endpoint Manager     | Si vous utilisiez déjà Intune avant d’obtenir Defender entreprise, vous pouvez continuer à utiliser Endpoint Manager centre d’administration pour intégrer des appareils. Essayez d’intégrer vos appareils Windows, Mac, iOS et Android avec Microsoft Intune. Pour plus d’informations, consultez [Inscription des appareils dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Modifier les stratégies de sécurité     | Si vous gérez vos stratégies de sécurité dans Defender entreprise, utilisez la page **de configuration de l’appareil** pour afficher et modifier vos stratégies. Defender entreprise est fourni avec des stratégies par défaut qui utilisent les paramètres recommandés pour sécuriser les appareils de votre entreprise dès qu’ils sont intégrés. Vous pouvez conserver les stratégies par défaut, les modifier et définir vos propres stratégies en fonction des besoins de votre entreprise. Pour en savoir plus, consultez [Afficher ou modifier des stratégies dans Defender entreprise](mdb-view-edit-policies.md).        |
| Exécuter une attaque simulée   | Plusieurs didacticiels et simulations sont disponibles dans Defender entreprise. Ces didacticiels et simulations montrent comment les fonctionnalités de protection contre les menaces de Defender entreprise peuvent fonctionner pour votre entreprise. Vous pouvez également utiliser une attaque simulée comme exercice d’entraînement pour votre équipe. Pour essayer les didacticiels, consultez [didacticiels recommandés pour Defender entreprise](#recommended-tutorials-for-defender-for-business).         |
| Afficher les incidents dans Microsoft 365 Lighthouse     | Si vous êtes fournisseur de [solutions cloud Microsoft](/partner-center/enrolling-in-the-csp-program) à l’aide de Microsoft 365 Lighthouse, vous pouvez afficher les incidents sur les locataires de vos clients dans votre portail Microsoft 365 Lighthouse. Pour en savoir plus, consultez [Microsoft 365 Lighthouse et Defender entreprise](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Didacticiels recommandés pour Defender entreprise

Le tableau suivant décrit les didacticiels recommandés pour les clients Defender entreprise.

| Didacticiel  | Description  |
|---------|---------|
| **Document Drops Backdoor**     | Simuler une attaque qui introduit des programmes malveillants basés sur des fichiers sur un appareil de test. Le didacticiel explique comment utiliser le fichier de simulation et ce qu’il faut surveiller dans le portail Microsoft 365 Defender. <p>Ce didacticiel nécessite l’installation de Microsoft Word sur votre appareil de test.   |
| **Réponse en direct**     | Découvrez comment utiliser des commandes de base et avancées avec Live Response. Découvrez comment localiser un fichier suspect, corriger le fichier et collecter des informations sur un appareil.   |
| **Gestion des vulnérabilités & des menaces (scénarios principaux)**     | Découvrez Gestion des menaces et des vulnérabilités dans trois scénarios :<ol><li>Réduisez l’exposition aux menaces et aux vulnérabilités de votre entreprise.</li><li>Demandez une correction.</li><li>Créez une exception pour les recommandations de sécurité.</li></ol> <p> Threat & Vulnerability Management utilise une approche basée sur les risques pour la découverte, la hiérarchisation et la correction des vulnérabilités et des erreurs de configuration des points de terminaison.      |

Chaque didacticiel inclut un document pas à pas qui explique le scénario, son fonctionnement et ce qu’il faut faire.

> [!TIP]
> Vous verrez des références à Microsoft Defender pour point de terminaison dans les documents de procédure pas à pas. Les didacticiels répertoriés dans cet article peuvent être utilisés avec Defender pour point de terminaison ou Defender entreprise.

## <a name="how-to-access-the-tutorials"></a>Comment accéder aux didacticiels

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, sous **Points de terminaison**, choisissez **Didacticiels**.

3. Choisissez l’un des didacticiels suivants :

   - **Document Drops Backdoor**
   - **Réponse en direct**
   - **Gestion des vulnérabilités & des menaces (scénarios principaux)**

## <a name="next-steps"></a>Prochaines étapes

- [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Defender entreprise](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)