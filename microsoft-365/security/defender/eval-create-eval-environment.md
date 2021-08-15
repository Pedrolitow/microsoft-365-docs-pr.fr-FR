---
title: Créer l’environnement d Microsoft 365 Defender évaluation de l’environnement
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
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: 6e89591b57be2bf79664547715906074b92b54649e1858bde9ffe06cb2be9335
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53867618"
---
# <a name="create-the-microsoft-365-defender-evaluation-environment"></a>Créer l’environnement d Microsoft 365 Defender évaluation de l’environnement

Il existe deux façons courantes de faire cette étape suivante dans l’évaluation. Ce document suppose que vous avez déjà un client M365 de production et activera les licences d’évaluation E5 pour évaluer M365 Defender dans *l’environnement actuel.* Une évaluation sur place vous permet de conserver toutes les méthodes de sécurité avec l’achat de licences après la période d’évaluation.

La seconde consiste à configurer votre environnement de laboratoire [d Microsoft 365 Defender d’évaluation](setup-m365deval.md) aux fins d’évaluation. Il n’y a peut-être pas beaucoup de signaux réels de l’entreprise, donc n’ignorez pas cette mise en garde.

## <a name="to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Pour activer les licences d’évaluation E5 afin d’évaluer Microsoft 365 Defender 
1. Connectez-vous à votre portail d’administration des clients M365 existant.
2. Sélectionnez *Acheter des services* dans le menu de navigation.
3. Faites défiler vers le *bas jusqu Office 365* section et sélectionnez le bouton « Détails » sous Office 365 E5 licence.

:::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="La Office 365 section contient un bouton Détails à cliquer.":::

4. Sélectionnez *Démarrer le lien d’essai* gratuit.

:::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Cliquez sur « Démarrer l’essai gratuit » (frais de 35 $).":::

5. Confirmez votre demande et cliquez sur le bouton Essayer *maintenant.*

:::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Il existe un bouton « Essayer maintenant » dans le panneau « Check out, confirm your order » (pour une version d’essai Office 365 E5 d’un mois pour 25 utilisateurs).":::

## <a name="next-steps"></a>Étapes suivantes
[Activer Microsoft 365 pour l’identité](eval-defender-identity-overview.md)

Revenir à la vue d’ensemble [de l’évaluation et de la Microsoft 365 Defender](eval-overview.md)