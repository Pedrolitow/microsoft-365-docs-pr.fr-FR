---
title: Étape 1. Créer l’environnement d Microsoft 365 Defender évaluation de la sécurité
description: Configurer votre laboratoire d Microsoft 365 Defender d’essai ou votre environnement pilote en activant les licences d’essai. Ensuite, configurer Microsoft Defender pour l’identité (MDI) et toutes les autres évaluations M365D.
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
ms.openlocfilehash: 17751cf5f71d9754ad8d5c0c913ee3438b49b399
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63311618"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment"></a>Étape 1. Créer l’environnement d Microsoft 365 Defender évaluation de la sécurité

Il existe deux façons courantes de faire cette étape suivante dans l’évaluation. Ce document suppose que vous avez déjà un client Microsoft 365 production et activera les licences d’évaluation E5 pour évaluer les Microsoft 365 Defender dans *l’environnement actuel*. Une évaluation sur place vous permet de conserver les méthodes de sécurité avec l’achat de licences après la période d’évaluation.

La seconde consiste à [configurer votre environnement de laboratoire d Microsoft 365 Defender d’évaluation](setup-m365deval.md) à des fins d’évaluation. Notez qu’il n’y a peut-être pas beaucoup de signaux réels de l’entreprise.

## <a name="to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Pour activer les licences d’évaluation E5 afin d’évaluer Microsoft 365 Defender 

1. Connectez-vous à votre portail d’administration Microsoft 365 client existant.
2. **Sélectionnez Acheter des services** dans le menu de navigation.
3. Faites défiler vers le bas jusqu Office 365 section et sélectionnez le bouton **Détails** sous Office 365 E5 licence.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="La Office 365 section contient un bouton Détails à cliquer.":::

4. Sélectionnez **Démarrer le lien d’essai** gratuit.

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Cliquez sur « Démarrer l’essai gratuit » (frais de 35 $).":::

5. Confirmez votre demande et cliquez sur **le bouton Essayer maintenant** .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Il existe un bouton « Essayer maintenant » dans le panneau « Check out, confirm your order » (pour une version d’Office 365 E5 d’un mois pour 25 utilisateurs).":::

## <a name="next-steps"></a>Étapes suivantes

[Activer Microsoft 365 pour l’identité](eval-defender-identity-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)