---
title: Didacticiels et simulations dans Microsoft Defender pour les PME
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
ms.openlocfilehash: 68695ee348b11fcc10f3a82d2cba2d2c168af666
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174383"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Didacticiels et simulations dans Microsoft Defender pour les PME

Si vous venez de terminer la configuration de Microsoft Defender pour les PME, vous vous demandez peut-être par où commencer à découvrir le fonctionnement de Defender entreprise. Cet article décrit certains scénarios à essayer, ainsi que plusieurs didacticiels et simulations disponibles pour Defender Entreprise. Ces ressources sont conçues pour vous aider à voir comment Defender entreprise peut fonctionner pour votre entreprise.

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="try-these-scenarios"></a>Essayez ces scénarios

Le tableau suivant récapitule plusieurs scénarios à essayer avec Defender entreprise :

| Scénario  | Description  |
|---------|---------|
| Intégrer des appareils en utilisant un script local     | Dans Defender entreprise, vous pouvez intégrer des appareils Windows et macOS à l’aide d’un script que vous téléchargez et exécutez sur chaque appareil. Le script crée une approbation avec Azure Active Directory (Azure AD) (si cette approbation n’existe pas déjà), inscrit l’appareil avec Microsoft Intune (si vous avez Intune) et l’intègre à Defender entreprise. Pour en savoir plus, consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).         |
| Intégrer des appareils à l’aide du centre d’administration Microsoft Endpoint Manager     | Si vous utilisiez déjà Intune avant d’obtenir Defender entreprise, vous pouvez continuer à utiliser Endpoint Manager centre d’administration pour intégrer des appareils. Essayez d’intégrer vos appareils Windows, macOS, iOS et Android avec Microsoft Intune. Pour plus d’informations, consultez [Inscription des appareils dans Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Modifier les stratégies de sécurité     | Si vous gérez vos stratégies de sécurité dans Defender entreprise, utilisez la page **de configuration de l’appareil** pour afficher et, si nécessaire, modifier vos stratégies. Defender entreprise est fourni avec des stratégies par défaut qui utilisent les paramètres recommandés pour sécuriser les appareils de votre entreprise dès qu’ils sont intégrés. Vous pouvez conserver vos stratégies par défaut, les modifier et définir les vôtres en fonction des besoins de votre entreprise. Pour en savoir plus, consultez [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](mdb-view-edit-policies.md).        |
| Exécuter une attaque simulée   | Plusieurs didacticiels et simulations sont disponibles dans Defender entreprise. Ces didacticiels et simulations sont conçus pour vous montrer de première main comment les fonctionnalités de protection contre les menaces de Defender entreprise peuvent fonctionner pour votre entreprise. Vous pouvez également utiliser une attaque simulée comme exercice d’entraînement pour votre équipe. Pour essayer un ou plusieurs didacticiels, consultez les [didacticiels recommandés pour Microsoft Defender pour les PME](#recommended-tutorials-for-defender-for-business).         |
| Afficher les incidents dans Microsoft 365 Lighthouse     | Si vous êtes un [Fournisseur de solutions Microsoft Cloud](/partner-center/enrolling-in-the-csp-program) à l’aide de Microsoft 365 Lighthouse, vous pouvez afficher les incidents sur les locataires de vos clients dans votre portail Microsoft 365 Lighthouse. Pour en savoir plus, consultez [Microsoft 365 Lighthouse et Microsoft Defender pour les PME](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Didacticiels recommandés pour Defender entreprise

Le tableau suivant décrit les didacticiels recommandés pour les clients Defender Entreprise :

| Didacticiel  | Description  |
|---------|---------|
| **Document drops backdoor**     | Simuler une attaque qui introduit des programmes malveillants basés sur des fichiers sur un appareil de test. Le didacticiel explique comment obtenir et utiliser le fichier de simulation et ce qu’il faut surveiller dans le portail Microsoft 365 Defender. <br/><br/>Ce didacticiel nécessite l’installation de Microsoft Word sur votre appareil de test.   |
| **Didacticiel sur la réponse en direct**     | Découvrez comment utiliser des commandes de base et avancées avec Live Response. Découvrez comment localiser un fichier suspect, corriger le fichier et collecter des informations sur un appareil.   |
| **Gestion des vulnérabilités & des menaces (scénarios principaux)**     | Découvrez Gestion des menaces et des vulnérabilités dans trois scénarios : <br/><br/>1. Réduisez l’exposition aux menaces et aux vulnérabilités de votre entreprise. <br/>2. Demandez une correction. <br/>3. Créez une exception pour les recommandations de sécurité. <br/><br/> Menace et gestion des vulnérabilités utilise une approche basée sur les risques pour la découverte, la hiérarchisation et la correction des vulnérabilités et des configurations incorrectes des points de terminaison.      |

Chaque didacticiel inclut un document pas à pas qui explique le scénario, son fonctionnement et ce qu’il faut faire.

> [!TIP]
> Vous verrez des références à Microsoft Defender pour point de terminaison dans les documents de procédure pas à pas. Les didacticiels répertoriés dans cet article peuvent être utilisés avec Defender pour point de terminaison ou Defender entreprise.

## <a name="how-to-access-the-tutorials"></a>Comment accéder aux didacticiels

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, sous **Points de terminaison**, choisissez **Didacticiels**.

3. Choisissez l’un des didacticiels suivants :

   - **Document drops backdoor**
   - **Didacticiel sur la réponse en direct**
   - **Gestion des vulnérabilités & des menaces (scénarios principaux)**

## <a name="next-steps"></a>Prochaines étapes

- [Gérer les appareils dans Microsoft Defender pour les PME](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)