---
title: Simuler une attaque par hameçonnage avec Microsoft Defender pour Office 365
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à simuler des attaques par hameçonnage et à former leurs utilisateurs à la prévention du hameçonnage à l’aide d’une formation sur la simulation d’attaques dans Microsoft Defender Office 365.
ms.technology: mdo
ms.openlocfilehash: 40baa8aa3eda6f0f6045115d45e2dac1426c4455
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59204450"
---
# <a name="simulate-a-phishing-attack"></a>Simuler une attaque par hameçonnage

**S’applique** [à Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

La formation sur la simulation d’attaques dans Microsoft Defender pour Office 365 vous permet d’exécuter des simulations de cyberattaque anodins sur votre organisation pour tester vos stratégies et pratiques de sécurité, ainsi que pour former vos employés afin qu’ils augmentent leur sensibilisation et diminuent leur tendance aux attaques. Cet article vous explique la création d’une attaque par hameçonnage simulée à l’aide d’une formation à la simulation d’attaques.

Pour plus d’informations sur la formation à la simulation d’attaque, voir [Commencer à utiliser la formation sur la simulation d’attaque.](attack-simulation-training-get-started.md)

Pour lancer une attaque par hameçonnage simulée, ouvrez le portail Microsoft 365 Defender ( ), allez à la formation sur la simulation d’attaques par & collaboration et passez à l’onglet <https://security.microsoft.com/>  \>  **[Simulations.](https://security.microsoft.com/attacksimulator?viewid=simulations)**

Sous **Simulations,** **sélectionnez + Lancer une simulation.**

![Lancez un bouton de simulation dans le portail Microsoft 365 Defender web.](../../media/attack-sim-preview-launch.png)

> [!NOTE]
> À tout moment lors de la création de la simulation, vous pouvez enregistrer et fermer pour continuer à configurer la simulation ultérieurement.

## <a name="selecting-a-social-engineering-technique"></a>Sélection d’une technique d’ingénierie sociale

Sélectionnez parmi 4 techniques différentes, organisées à partir de l’infrastructure&[CK ® MITRE ATT.](https://attack.mitre.org/techniques/enterprise/) Différentes charges utiles sont disponibles pour différentes techniques :

- **La collecte des** informations d’identification tente de collecter des informations d’identification en prenant les utilisateurs vers un site web bien connu avec des zones d’entrée pour envoyer un nom d’utilisateur et un mot de passe.
- **Une pièce jointe malveillante** ajoute une pièce jointe malveillante à un message. Lorsque l’utilisateur ouvre la pièce jointe, un code arbitraire est exécuté pour aider l’attaquant à compromettre l’appareil de la cible.
- **Le lien dans la pièce jointe** est un type d’hybridation de la saisie des informations d’identification. Un attaquant insère une URL dans une pièce jointe d’un e-mail. L’URL dans la pièce jointe suit la même technique que la saisie des informations d’identification.
- **Un lien vers un programme** malveillant exécutera du code arbitraire à partir d’un fichier hébergé sur un service de partage de fichiers connu. Le message envoyé à l’utilisateur contient un lien vers ce fichier malveillant. Ouverture du fichier et aide l’attaquant à compromettre l’appareil de la cible.
- **L’URL de** lecteur par est l’endroit où l’URL malveillante dans le message conduit l’utilisateur vers un site web familier qui s’exécute en mode silencieux et/ou installe le code de code sur l’appareil de l’utilisateur.

> [!TIP]
> Le fait de cliquer sur **Afficher les détails** dans la description de chaque technique permet d’afficher des informations supplémentaires et les étapes de simulation de la technique.
>
> ![Étapes de simulation pour la recherche d’informations d’identification dans le cadre d’une formation sur la simulation d’attaque dans Microsoft 365 Defender portail.](../../media/attack-sim-preview-sim-steps.png)

Une fois que vous avez sélectionné la technique et cliqué sur **Suivant,** donnez à votre simulation un nom et éventuellement une description.

## <a name="selecting-a-payload"></a>Sélection d’une charge utile

Ensuite, vous devez sélectionner une charge utile dans le catalogue de charge utile pré-existant.

Les charges utiles ont un certain nombre de points de données pour vous aider à choisir :

- **Le taux de** clics compte le nombre de personnes qui ont cliqué sur cette charge utile.
- **Le taux de compromis** prévue prévoit le pourcentage de personnes qui seront compromises par cette charge utile en fonction des données historiques de la charge utile dans Microsoft Defender pour Office 365 clients.
- **Les simulations lancées** comptent le nombre de fois que cette charge utile a été utilisée dans d’autres simulations.
- **La** complexité, disponible par le biais **de filtres,** est calculée en fonction du nombre d’indicateurs au sein de la charge utile ciblée par des indices en tant qu’attaque. Plus il y a d’indicateurs, plus la complexité est faible.
- **La source,** disponible **via** des filtres, indique si la charge utile a été créée sur votre client ou fait partie du catalogue de charge utile pré-existant de Microsoft (global).

![Charge utile sélectionnée dans le cadre d’une formation sur la simulation d’attaques Microsoft 365 Defender portail.](../../media/attack-sim-preview-select-payload.png)

Sélectionnez une charge utile dans la liste pour afficher un aperçu de la charge utile avec des informations supplémentaires à son sujet.

Si vous souhaitez créer votre propre charge utile, lisez créer une charge utile pour [l’entraînement de simulation d’attaque.](attack-simulation-training-payloads.md)

## <a name="audience-targeting"></a>Ciblage d’audience

Il est maintenant temps de sélectionner l’audience de cette simulation. Vous pouvez choisir **d’inclure tous les utilisateurs de votre** organisation ou d’inclure uniquement des utilisateurs et des groupes **spécifiques.**

Lorsque vous choisissez **d’inclure uniquement des utilisateurs et des groupes spécifiques,** vous pouvez :

- Ajoutez des utilisateurs, ce qui vous permet de tirer parti de la recherche pour votre client, ainsi que des fonctionnalités avancées de recherche et de filtrage, telles que le ciblage d’utilisateurs qui n’ont pas été ciblés par une simulation au cours des 3 derniers mois.

  ![Filtrage des utilisateurs lors d’une formation sur la simulation d’attaques Microsoft 365 Defender portail.](../../media/attack-sim-preview-user-targeting.png)

- **L’importation à partir de CSV** vous permet d’importer un ensemble prédéféré d’utilisateurs pour cette simulation.

## <a name="assigning-training"></a>Affectation d’une formation

Nous vous recommandons d’affecter une formation pour chaque simulation, car les employés qui s’entraînent sont moins susceptibles d’être exposés à des attaques similaires.

Vous pouvez choisir de vous attribuer une formation ou de sélectionner vous-même des cours et des modules de formation.

Sélectionnez la **date d’échéance de** la formation pour vous assurer que les employés terminent leur formation en temps voulu.

> [!NOTE]
> Si vous choisissez de sélectionner vous-même des cours et des modules, vous pourrez toujours voir le contenu recommandé ainsi que tous les cours et modules disponibles.
>
> ![Ajout d’une formation recommandée dans le cadre d’une formation sur la simulation d’attaques dans Microsoft 365 Defender portail.](../../media/attack-sim-preview-add-training.png)

Dans les étapes **suivantes,** vous devrez ajouter des formations si vous avez choisi de la sélectionner vous-même et de personnaliser votre page d’arrivée de formation. Vous pourrez afficher un aperçu de la page d’accueil de formation, ainsi que modifier l’en-tête et le corps de celui-ci.

## <a name="launch-details-and-review"></a>Détails du lancement et révision

Maintenant que tout est configuré, vous pouvez lancer cette simulation immédiatement ou la planifier pour une date ultérieure. Vous devrez également choisir quand mettre fin à cette simulation. Nous arrêterons la capture de l’interaction avec cette simulation au-delà de l’heure sélectionnée.

**Activez la remise de fuseau horaire** de région pour remettre des messages d’attaque simulée à vos employés pendant leurs heures de travail en fonction de leur région.

Une fois que vous avez terminé, cliquez sur **Suivant** et examinez les détails de votre simulation. Cliquez sur **Modifier** sur l’un des composants pour revenir en arrière et modifier les détails qui doivent être modifiés. Une fois terminé, cliquez sur **Envoyer.**

> [!NOTE]
> Certaines marques, logos, symboles, insignias et autres identificateurs source bénéficient d’une protection maximale en vertu de lois et lois locales, nationales et fédérales. L’utilisation non autorisée de ces indicateurs peut imposer des sanctions aux utilisateurs, y compris des amendes pénales. Bien qu’il ne s’agit pas d’une liste complète, il s’agit notamment des personnes à l’emploi de Lasc, du vice-président et de l’espion, du CENTRE d’enquêtes sur la sécurité sociale, de la sécurité sociale, du service de sécurité sociale des États-Unis et du service de revenu interne des États-Unis. Au-delà de ces catégories de marques, l’utilisation et la modification d’une marque tierce impliquent un risque inhérent. L’utilisation de vos propres marques et logos dans une charge utile serait moins risqué, en particulier lorsque votre organisation autorise l’utilisation. Si vous avez d’autres questions sur ce qui est approprié ou non à utiliser lors de la création ou de la configuration d’une charge utile, vous devez consulter vos conseillers juridiques.
