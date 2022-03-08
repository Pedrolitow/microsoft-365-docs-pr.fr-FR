---
title: Didacticiels et simulations dans Microsoft Defender entreprise
description: En savoir plus sur plusieurs didacticiels pour vous aider à commencer à utiliser Defender pour Les entreprises
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: article
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: c955b85001a141933227873a1f74e681f74b004b
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63322938"
---
# <a name="tutorials-and-simulations-in-microsoft-defender-for-business"></a>Didacticiels et simulations dans Microsoft Defender entreprise

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Si vous avez terminé la configuration de Microsoft Defender pour les entreprises, vous vous demandez peut-être où commencer pour en savoir plus sur le fonctionnement de Defender entreprise. Cet article décrit les scénarios d’aperçu à essayer, ainsi que plusieurs didacticiels et simulations disponibles pour Defender for Business. Ces ressources sont conçues pour vous aider à voir comment Defender entreprise peut fonctionner pour votre organisation.

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="try-these-preview-scenarios"></a>Essayez ces scénarios d’aperçu

Le tableau suivant récapitule plusieurs scénarios à essayer avec Defender for Business. 
<br/><br/>


| Scénario  | Description  |
|---------|---------|
| Intégrer des appareils en utilisant un script local <br/>(*pas pour le déploiement de production*)     | Dans Defender entreprise, vous pouvez intégrer jusqu’à dix Windows 10 11 appareils à l’aide d’un script que vous téléchargez et exécutez sur chaque appareil. Approprié pour évaluer le fonctionnement de Defender for Business dans votre environnement, le script crée une relation d’Azure Active Directory (Azure AD) et inscrit l’appareil avec Microsoft Intune. Pour plus d’informations, [voir script local dans Defender for Business](mdb-onboard-devices.md#local-script-in-defender-for-business).         |
| Intégrer des appareils à l’aide Microsoft Intune     | Si vous utilisiez déjà Microsoft Intune avant d’obtenir Defender pour endpoint, vous pouvez continuer à utiliser Microsoft Intune pour intégrer des appareils. Essayez d’intégrer des appareils macOS, iOS et Android avec Microsoft Intune. Pour en savoir plus, [consultez l’inscription des appareils Microsoft Intune](/mem/intune/enrollment/device-enrollment).        |
| Modifier les stratégies de sécurité     | Si vous gérez vos stratégies de sécurité dans Defender for Business, utilisez la page **configuration** des appareils pour afficher et modifier vos stratégies. Pour plus d’informations, voir [Afficher ou modifier des stratégies dans Microsoft Defender entreprise](mdb-view-edit-policies.md).        |
| Exécuter une attaque simulée   | Plusieurs didacticiels et simulations sont disponibles dans Defender for Business. Ces didacticiels et simulations sont conçus pour vous montrer comment les fonctionnalités de protection contre les menaces de Defender for Business peuvent fonctionner pour votre organisation. Pour essayer un ou plusieurs des didacticiels, consultez les [didacticiels recommandés pour Microsoft Defender pour les entreprises](#recommended-tutorials-for-defender-for-business).         |
| Afficher les incidents dans Microsoft 365 Lighthouse     | Si vous [utilisez Fournisseur de solutions Microsoft Cloud Microsoft 365 Lighthouse](/partner-center/enrolling-in-the-csp-program), vous pourrez bientôt afficher les incidents sur les clients de vos clients dans votre portail Microsoft 365 Lighthouse client. Pour plus d’informations, [voir Microsoft 365 Lighthouse et Microsoft Defender for Business](mdb-lighthouse-integration.md).       |


## <a name="recommended-tutorials-for-defender-for-business"></a>Didacticiels recommandés pour Defender for Business

Le tableau suivant décrit les didacticiels recommandés pour les clients Defender entreprise :
<br/><br/>


| Didacticiel  | Description  |
|---------|---------|
| **Document drop backdoor**     | Simuler une attaque qui introduit un programme malveillant basé sur un fichier sur un périphérique de test. Le didacticiel décrit comment obtenir et utiliser le fichier de simulation, et ce qu’il faut surveiller dans Microsoft 365 Defender portail. <br/><br/>Ce didacticiel Microsoft Word être installé sur votre périphérique de test.   |
| **Didacticiel Live Response**     | Découvrez comment utiliser des commandes de base et avancées avec Live Response. Découvrez comment localiser un fichier suspect, corriger le fichier et collecter des informations sur un appareil.   |
| **Gestion & des menaces et des vulnérabilités (scénarios principaux)**     | Découvrez les Gestion des menaces et des vulnérabilités à travers trois scénarios : <br/><br/>1. Réduisez l’exposition aux menaces et vulnérabilités de votre organisation. <br/>2. Demander une correction. <br/>3. Créez une exception pour les recommandations de sécurité. <br/><br/> Les menaces et gestion des vulnérabilités utilisent une approche basée sur les risques pour la découverte, la hiér doncisation et la correction des vulnérabilités et des mauvaises configurations des points de terminaison.      |

Chaque didacticiel inclut un document pas à pas qui explique le scénario, son fonctionnement et les étapes à prendre.

> [!TIP]
> Vous verrez des références à Microsoft Defender pour point de terminaison dans les documents pas à pas. Les didacticiels répertoriés dans cet article peuvent être utilisés avec Defender pour Endpoint ou Defender pour Entreprise.

## <a name="how-to-access-the-tutorials"></a>Comment accéder aux didacticiels

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Dans le volet de navigation, sous **Points de terminaison**, choisissez **Didacticiels**.

3. Choisissez l’un des didacticiels suivants :

   - **Document drop backdoor**
   - **Didacticiel Live Response**
   - **Gestion & des menaces et des vulnérabilités (scénarios principaux)**

## <a name="next-steps"></a>Étapes suivantes

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)