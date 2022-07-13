---
title: Créer l’environnement d’évaluation Microsoft 365 Defender pour une plus grande cybersécurité et XDR
description: Découvrez ce qui est inclus dans le Microsoft 365 Defender XDR que vous évaluerez et récupérez votre laboratoire d’essai ou environnement pilote Microsoft 365 Defender en activant les licences d’essai. Commencez votre parcours de cybersécurité XDR ici et découvrez comment effectuer ce test en production.
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
- zerotrust-solution
ms.topic: how-to
ms.technology: m365d
ms.openlocfilehash: fb097532fe809fa1b1ec4c29a9a489bcb4ea2871
ms.sourcegitcommit: 61b22df76e0f81e5ef11c587b129287886151c79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66747964"
---
# <a name="step-1-create-the-microsoft-365-defender-evaluation-environment-for-greater-cyber-security"></a>Étape 1. Créer l’environnement d’évaluation Microsoft 365 Defender pour une plus grande sécurité informatique

Vous pouvez en savoir plus sur cette solution Microsoft Defender XDR et la générer en suivant les étapes qui sont distribuées dans le reste de cette série :

- [Comment créer l’environnement](eval-create-eval-environment.md)
- Configurer ou en savoir plus sur chaque technologie de ce XDR Microsoft
    - [Microsoft Defender pour l’identité](eval-defender-identity-overview.md)
    - [Microsoft Defender pour Office](eval-defender-office-365-overview.md)
    - [Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)
    - [Microsoft Defender for Cloud Apps](eval-defender-mcas-overview.md)
- [Comment examiner et répondre à l’aide de ce XDR](eval-defender-investigate-respond.md)
- [Promouvoir l’environnement d’essai en production](eval-defender-promote-to-production.md)
- [Revenir à la vue d’ensemble](eval-overview.md)

Les étapes de cette série s’exécutent de bout en bout, de l’apprentissage des concepts sous-jacents à la Microsoft 365 Defender XDR à sa création, et à la mise en production de l’environnement d’évaluation.

Il existe deux façons courantes d’effectuer cette étape suivante de l’évaluation. Cette série part du principe que vous disposez déjà d’un locataire Microsoft 365 de production et active les licences d’évaluation E5 pour évaluer Microsoft 365 Defender dans *l’environnement actuel*. Une évaluation sur place vous permet de conserver toutes les méthodes de sécurité avec l’achat de licences après la période d’évaluation.

La deuxième consiste à [configurer votre environnement de laboratoire d’essai Microsoft 365 Defender](setup-m365deval.md) à des fins d’évaluation. Notez qu’il peut ne pas avoir beaucoup de signaux réels de l’entreprise lors des tests.

## <a name="you-will-need-to-activate-e5-trial-licenses-to-evaluate-microsoft-365-defender"></a>Vous devez activer les licences d’évaluation E5 pour évaluer Microsoft 365 Defender

1. Connectez-vous à votre portail d’administration de locataire Microsoft 365 existant.
2. Sélectionnez **Acheter des services** dans le menu de navigation.
3. Faites défiler jusqu’à la section Office 365 et sélectionnez **Le bouton Détails** sous Office 365 E5 licence.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-license-details.png" alt-text="Bouton Détails dans le portail Microsoft 365 Defender" lightbox="../../media/mdo-eval/2_mdo-eval-license-details.png":::

4. Sélectionnez **le lien Démarrer la version d’évaluation gratuite** .

   :::image type="content" source="../../media/mdo-eval/3-m365-purchase-button.png" alt-text="Bouton Démarrer l’essai gratuit dans le portail Microsoft 365 Defender" lightbox="../../media/mdo-eval/3-m365-purchase-button.png":::

5. Confirmez votre demande, puis cliquez sur **le bouton Essayer maintenant** .

   :::image type="content" source="../../media/mdo-eval/4_mdo-trial-order.png" alt-text="Bouton Essayer maintenant dans le portail Microsoft 365 Defender" lightbox="../../media/mdo-eval/4_mdo-trial-order.png":::

## <a name="go-to-the-next-step"></a>Passer à l’étape suivante

[Découvrez comment activer Microsoft 365 pour Identity](eval-defender-identity-overview.md)

Ou revenez à la vue d’ensemble pour [Évaluer et piloter Microsoft 365 Defender](eval-overview.md)
