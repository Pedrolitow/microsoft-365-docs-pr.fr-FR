---
title: Créer l’Microsoft 365 Defender d’évaluation pour une cybersécurité et une XDR renforcées
description: Découvrez les fonctionnalités incluses dans la Microsoft 365 Defender XDR que vous évaluerez, puis resserez votre laboratoire d’évaluation ou votre environnement pilote Microsoft 365 Defender en activant les licences d’évaluation. Commencez votre parcours de cybersécurité XDR ici et découvrez comment mettre ce test en production.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/19/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: d81d33a01802ebdf8ef0ea67a9ee74fc69b79384
ms.sourcegitcommit: 8423f47fce3905a48db9daefe69c21c841da43a0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/15/2022
ms.locfileid: "63504730"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Étape 1. Créer l’environnement d Microsoft 365 Defender d’évaluation pour une cybersécurité accrue

LYou peut en savoir plus sur cette solution Microsoft Defender XDR et la développer dans les étapes qui sont distribuées dans le reste de cette série :

- [Comment créer l’environnement](eval-create-eval-environment.md)
- Configurer ou en savoir plus sur chaque technologie de cette XDR Microsoft
    - [Microsoft Defender pour l’identité](eval-defender-identity-overview.md)
    - [Microsoft Defender pour Office](eval-defender-office-365-overview.md)
    - [Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)
    - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Comment examiner et répondre à l’aide de cette XDR](eval-defender-investigate-respond.md)
- [Promouvoir l’environnement d’essai en production](eval-defender-promote-to-production.md)
- [Retour à la vue d’ensemble](eval-overview.md)

Les étapes de cette série s’exécutent de bout en bout, de l’apprentissage des concepts sous-Microsoft 365 Defender XDR à sa création et à la mise en production de l’environnement d’évaluation.

Il existe deux façons courantes de faire cette étape suivante dans l’évaluation. Cette série suppose que vous avez déjà un client Microsoft 365 production et activera les licences d’évaluation E5 pour évaluer les Microsoft 365 Defender dans *l’environnement actuel*. Une évaluation sur place vous permet de conserver les méthodes de sécurité avec l’achat de licences après la période d’évaluation.

La seconde consiste à [configurer votre environnement de laboratoire d Microsoft 365 Defender d’évaluation](setup-m365deval.md) à des fins d’évaluation. Notez qu’il n’y a peut-être pas beaucoup de signaux réels de l’entreprise pendant le test.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Vous devez activer les licences d’évaluation E5 pour évaluer Microsoft 365 Defender

1. Connectez-vous à votre portail d’administration Microsoft 365 client existant.
2. **Sélectionnez Acheter des services** dans le menu de navigation.
3. Faites défiler vers le bas jusqu Office 365 section et sélectionnez le bouton **Détails** sous Office 365 E5 licence.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="La Office 365 section contient un bouton Détails à cliquer.":::

4. Sélectionnez **Démarrer le lien d’essai** gratuit.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Cliquez sur « Démarrer l’essai gratuit » (frais de 35 $).":::

5. Confirmez votre demande et cliquez sur **le bouton Essayer maintenant** .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Il existe un bouton « Essayer maintenant » dans le panneau « Check out, confirm your order » (pour une version d’Office 365 E5 d’un mois pour 25 utilisateurs).":::

## <a name="go-to-the-next-step"></a>Passer à l’étape suivante

[Découvrez comment activer la Microsoft 365 pour l’identité](eval-defender-identity-overview.md)

Ou revenir à la vue d’ensemble de [l’évaluation et de la Microsoft 365 Defender](eval-overview.md)