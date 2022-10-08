---
title: Comment exécuter des simulations d’attaque pour votre équipe
description: Étapes d’envoi d’une charge utile de simulation d’attaque à vos utilisateurs cibles pour votre équipe ou organisation à des fins d’entraînement. Les attaques simulées peuvent vous aider à identifier et à rechercher des utilisateurs, des stratégies et des pratiques vulnérables avant qu’une attaque réelle n’affecte votre organisation.
search.product: ''
ms.service: microsoft-365-security
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
ms.collection:
- m365-guidance-templates
- m365-security
- tier3
ms.topic: how-to
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: a76e73e5b602fef3dbd6820483a47c2ef32c9833
ms.sourcegitcommit: 4e42bafee965446f44f7f57d1defed2b9b24fce8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68233835"
---
# <a name="how-to-run-attack-simulations-for-your-team"></a>Comment exécuter des simulations d’attaque pour votre équipe

Exercice de simulation d'attaque vous permet d’exécuter des scénarios de cyberattaques réalistes mais bénins dans votre organisation. Les attaques simulées peuvent vous aider à identifier et à trouver des utilisateurs, des stratégies et des pratiques vulnérables avant qu’une attaque réelle n’affecte votre organisation, en tirant parti d’une formation intégrée ou personnalisée pour réduire les risques et mieux informer les utilisateurs finaux sur les menaces.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin

- Microsoft Defender pour Office 365 plan 2 (inclus dans le cadre de l’E5)
- Autorisations suffisantes (rôle Administrateur de sécurité)
- 5 à 10 minutes pour effectuer les étapes ci-dessous.

## <a name="send-a-payload-to-target-users"></a>Envoyer une charge utile aux utilisateurs cibles

1. Accédez à [Attack Simulation Training](https://security.microsoft.com/attacksimulator ) dans votre abonnement.
1. Choisissez **Simulations** dans la barre de navigation supérieure.
1. Sélectionnez **Lancer une simulation**.
1. Sélectionnez la technique que vous souhaitez utiliser dans le menu volant, puis appuyez sur **Suivant**.
1. Nommez la simulation avec quelque chose de pertinent/mémorable, puis appuyez sur **Suivant**.
1. Sélectionnez une charge utile appropriée dans l’Assistant, passez en revue les détails et personnalisez le cas échéant, lorsque vous êtes satisfait du choix, appuyez sur **Suivant**.
1. Choisissez qui cibler avec la charge utile. Si vous choisissez l’ensemble de l’organisation, mettez en surbrillance la case d’option et appuyez sur **Suivant**.
1. Sinon, sélectionnez **Ajouter des utilisateurs** , puis recherchez ou filtrez les utilisateurs avec l’Assistant. Sélectionnez Ajouter un ou plusieurs utilisateurs, puis **Suivant**.
1. Sous **Sélectionner la préférence de contenu d’entraînement**, laissez l’expérience de *formation Microsoft par défaut (recommandé)* ou sélectionnez *Rediriger vers une URL personnalisée* si vous souhaitez utiliser l’URL personnalisée. Si vous ne souhaitez attribuer aucune formation, sélectionnez *Aucune formation*.
    - Vous pouvez soit laisser Microsoft attribuer des cours de formation en sélectionnant *Affecter une formation pour moi* , soit choisir des modules spécifiques avec *sélectionner des cours de formation et des modules moi-même*
    - Sélectionnez une date d’échéance (30, 15 ou 7 jours) dans le menu déroulant.
    - Cliquez sur **Suivant** pour continuer.
1. Personnalisez la page d’accueil affichée lorsqu’un utilisateur est hameçonné, le cas échéant, ou quittez la valeur Par défaut de Microsoft.
    1. Sous **Indicateurs de charge utile**, cochez la case pour ajouter des indicateurs de charge utile à l’e-mail. L’ajout de charges utiles permet aux utilisateurs d’apprendre à identifier l’e-mail de hameçonnage. Sélectionnez *Ouvrir le panneau d’aperçu* pour afficher le message.
    1. Cliquez sur **Suivant** pour continuer.
1. Choisissez si vous souhaitez recevoir des notifications de l’utilisateur final et, le cas échéant, sélectionnez les préférences de remise et personnalisez-les si nécessaire.
    1. Notez que vous pouvez également sélectionner la *langue par défaut* pour la notification dans le menu déroulant **Sélectionner la langue par défaut** .
1. Sélectionnez quand lancer la simulation et la durée pendant laquelle elle doit être valide. Vous pouvez également activer la *remise de fuseau horaire prenant en charge la région*. Cette option fournit des messages d’attaque simulés à vos employés pendant *leurs heures de travail* en fonction de leur région. Sélectionnez **Suivant**.
1. Envoyez un test si vous êtes prêt. Passez en revue le résumé des choix. Cliquez sur **Envoyer**.

### <a name="further-reading"></a>Lire plus en détail

Pour savoir comment fonctionne la simulation d’attaque, consultez [Simuler une attaque par hameçonnage avec Exercice de simulation d'attaque - Office 365 | Microsoft Docs](../../office-365-security/attack-simulation-training.md)
