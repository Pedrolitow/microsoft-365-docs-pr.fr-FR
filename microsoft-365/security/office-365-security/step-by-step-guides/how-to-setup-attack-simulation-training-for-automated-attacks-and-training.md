---
title: Comment configurer les attaques automatisées et l’entraînement dans le cadre de l’entraînement de simulation d’attaque
description: Étapes permettant d’automatiser l’entraînement de simulation d’attaque et d’envoyer une charge utile aux utilisateurs cibles. En suivant ce guide, vous allez apprendre à créer des flux d’attaque automatisés avec des techniques et charges utiles spécifiques.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: c522c9602874ca8b385a135a64c34ef0643abe82
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67106840"
---
# <a name="how-to-setup-automated-attacks-and-training-within-attack-simulation-training"></a>Comment configurer les attaques automatisées et l’entraînement dans le cadre de l’entraînement de simulation d’attaque

La formation sur la simulation d’attaque vous permet d’exécuter des simulations d’attaques bénignes sur votre organisation pour évaluer vos risques d’hameçonnage et apprendre à vos utilisateurs à mieux éviter les attaques par hameçonnage. En suivant ce guide, vous allez configurer des flux automatisés avec des techniques et charges utiles spécifiques qui s’exécutent lorsque les conditions spécifiées sont remplies, en lançant des simulations sur votre organisation.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 2 (inclus dans le cadre de l’E5).
- Autorisations suffisantes (rôle Administrateur de la sécurité).
- 5 à 10 minutes pour effectuer les étapes ci-dessous.

## <a name="send-a-payload-to-target-users"></a>Envoyer une charge utile aux utilisateurs cibles

1. Accédez à [l’entraînement de simulation d’attaque](https://security.microsoft.com/attacksimulator).
1. Choisissez **Automatisations de simulation dans** la barre de navigation supérieure.
1. **Appuyez sur Créer une automatisation**.
1. Nommez l’automatisation de simulation avec quelque chose de pertinent et mémorable. *Ensuite, je vous en passe*.
1. Choisissez les techniques que vous souhaitez utiliser dans le menu volant. *Ensuite, je vous en passe*.
1. Sélectionnez manuellement jusqu’à 20 charges utiles que vous souhaitez utiliser pour cette automatisation, ou sélectionnez Aléatoire. *Ensuite, je vous en passe*.
1. Si vous avez choisi OAuth comme charge utile, vous devez entrer le nom, le logo et l’étendue (autorisations) que vous souhaitez que l’application ait quand elle est utilisée dans une simulation. *Ensuite, je vous en passe*.
1. Choisissez qui cibler avec la charge utile, si vous choisissez l’ensemble de l’organisation, mettez en surbrillance la case d’option. *Ensuite, je vous en passe*.
1. Sinon, sélectionnez **Ajouter des utilisateurs** , puis recherchez ou filtrez les utilisateurs avec l’Assistant, puis appuyez sur Ajouter des utilisateurs. *Ensuite, je vous en passe*.
1. Personnalisez l’entraînement le cas échéant, sinon laissez l’option Affecter l’entraînement pour moi (recommandé) sélectionnée. *Ensuite, je vous en passe*.
1. Personnalisez la page d’accueil affichée lorsqu’un utilisateur est hameçonné le cas échéant, sinon laissez la valeur Par défaut de Microsoft. *Ensuite, je vous en passe*.
1. Choisissez si vous souhaitez recevoir des notifications de l’utilisateur final, si c’est le cas, sélectionnez les préférences de remise et personnalisez-les le cas échéant. *Ensuite, je vous en passe*.
1. Pour la planification de simulation, vous pouvez sélectionner **Aléatoire** ou **Fixe**. L’option recommandée est Aléatoire, une fois sélectionnée, *sélectionnez Suivant*.
1. Selon votre choix de randomisation ou de correction, les détails de la planification peuvent différer, mais sélectionnez les préférences sur le choix, y compris les dates de début et de fin de l’automatisation. *Ensuite, je vous en passe*.
1. Pour **Détails du lancement**, sélectionnez toutes les options finales souhaitées, telles que l’utilisation de charges utiles uniques ou le ciblage des récidivistes, puis sélectionnez *Suivant*.
1. **Envoyer** et l’automatisation de simulation est configurée.

## <a name="learn-more"></a>En savoir plus

Vous trouverez des conseils [complets sur les automatisations de simulation pour l’entraînement de simulation d’attaque - Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training-simulation-automations.md).
