---
title: Simuler une attaque de hameçonnage avec Microsoft Defender pour
ms.author: daniha
author: danihalfin
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
description: Découvrez comment simuler les attaques par hameçonnage et former vos utilisateurs à la prévention du hameçonnage avec la formation à la simulation d’attaque de Microsoft Defender pour Office 365.
ms.openlocfilehash: b9b8a431fc28942f5e11bc7ce2e805ca082cf36b
ms.sourcegitcommit: dab50e1cc5bba920720b80033c93457f5ca1c330
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2020
ms.locfileid: "48944503"
---
# <a name="simulate-a-phishing-attack"></a>Simulation d’une attaque par hameçonnage

La formation de simulation d’attaque via Microsoft Defender pour Office 365 vous permet d’exécuter des simulations d’attaques informatiques bénignes sur votre organisation afin de tester vos stratégies et pratiques de sécurité, ainsi que de former les employés de votre organisation à améliorer leur sensibilisation et à réduire leur susceptibilité aux attaques. Ce qui suit vous guide tout au long de la simulation d’une attaque par hameçonnage à l’aide de la formation à simulateur d’attaques.

[!INCLUDE [Prerelease information](../includes/prerelease.md)]

Pour lancer une attaque par hameçonnage simulée, accédez au [Centre de sécurité Microsoft 365](https://security.microsoft.com/). Sous **messagerie & collaboration** , cliquez sur **simulateur d’attaque** et sélectionnez l’onglet [**simulations**](https://security.microsoft.com/attacksimulator?viewid=simulations) .

Sous **simulations** , sélectionnez **+ lancer une simulation**.

![Lancer un bouton de simulation dans le centre de sécurité Microsoft 365](../../media/attack-sim-preview-launch.png)

> [!NOTE]
> À tout moment pendant la création de la simulation, vous pouvez enregistrer et fermer pour poursuivre la configuration de la simulation ultérieurement.

## <a name="selecting-a-social-engineering-technique"></a>Sélection d’une technique d’ingénierie sociale

Vous avez le choix entre 4 techniques différentes, organisée à partir de la [Mitre ATT&CK® Framework](https://attack.mitre.org/techniques/enterprise/). Différentes charges utiles sont disponibles pour différentes techniques.

- La collecte des **informations d’identification** tente de collecter des informations d’identification auprès des employés en les déplaçant vers un site Web de présentation bien connu avec des zones de saisie pour envoyer un nom d’utilisateur et un mot de passe.
- Une **pièce jointe malveillante** ajoute une pièce jointe malveillante à un message. Une fois ouvert, cette pièce jointe exécute un code arbitraire qui aidera l’agresseur à compromettre l’appareil de la cible.
- Le **lien dans la pièce jointe** est un type hybride de collecte des informations d’identification. Un agresseur insère une URL dans une pièce jointe de courrier électronique. L’URL dans la pièce jointe suit la même technique que la collecte des informations d’identification.
- Un **lien vers un programme malveillant** exécute un code arbitraire à partir d’un fichier hébergé sur un site de partage de fichiers connu. Un lien vers ce fichier malveillant est ajouté au message envoyé à la cible et cliquez dessus pour exécuter le fichier et aider l’agresseur à compromettre l’appareil de la cible.

> [!TIP]
> Le fait de cliquer sur **afficher les détails** dans la description de chaque technique affiche des informations supplémentaires sur la technique, ainsi que les étapes de simulation de cette technique.
>
> ![Étapes de simulation pour la collecte des informations d’identification dans le centre de sécurité de Microsoft 365](../../media/attack-sim-preview-sim-steps.png)

Une fois que vous avez sélectionné la technique et cliqué sur **suivant** , donnez un nom et éventuellement une description à votre simulation.

## <a name="selecting-a-payload"></a>Sélection d’une charge utile

Ensuite, vous devez sélectionner une charge utile dans le catalogue de charge utile préexistant.

Les charges utiles comportent un certain nombre de points de données pour vous aider à choisir :

- **Cliquer sur** le nombre de taux indique combien de personnes ont cliqué sur cette charge utile.
- **Taux d’endommagement prévu** : prévoit le pourcentage de personnes qui seront compromises par cette charge utile en fonction des données historiques de cette charge utile parmi les clients Microsoft Defender pour Office 365.
- **Simulations lancées** compte le nombre de fois que cette charge utile a été utilisée dans d’autres simulations.
- La **complexité** , disponible par le biais de **filtres** , est calculée en fonction du nombre d’indicateurs au sein de la charge utile qui permettent aux cibles de l’informatique d’être une attaque. Un plus grand nombre d’indicateurs entraîne une complexité moindre.
- **Source** , disponible par le biais de **filtres** , indique si la charge utile a été créée sur votre client ou fait partie du catalogue de charge utile préexistant de Microsoft (Global).

![Charge utile sélectionnée lors de la formation à la simulation d’attaque dans le centre de sécurité Microsoft 365](../../media/attack-sim-preview-select-payload.png)

Sélectionnez une charge utile dans la liste pour afficher un aperçu de la charge utile avec des informations supplémentaires le concernant.

Si vous souhaitez créer votre propre charge utile, lisez [Create a Payload for Attack Simulation Training](attack-simulation-training-payloads.md).

## <a name="audience-targeting"></a>Ciblage d’audience

À présent, il est temps de sélectionner l’audience de cette simulation. Vous pouvez choisir d' **inclure tous les utilisateurs de votre organisation** ou d' **inclure uniquement des utilisateurs et des groupes spécifiques**. 

Lorsque vous choisissez d' **inclure uniquement des utilisateurs et des groupes spécifiques,** vous pouvez :

- **Ajoutez des utilisateurs** , ce qui vous permet d’utiliser la recherche pour votre client, ainsi que les fonctionnalités avancées de recherche et de filtrage, telles que le ciblage des utilisateurs qui n’ont pas été ciblés par une simulation au cours des 3 derniers mois.
  ![Filtrage des utilisateurs dans formation à la simulation d’attaque sur le centre de sécurité Microsoft 365](../../media/attack-sim-preview-user-targeting.png)
- **Importer à partir de CSV** vous permet d’importer un ensemble prédéfini d’utilisateurs pour cette simulation.

## <a name="assigning-training"></a>Affectation d’une formation

Nous vous recommandons d’attribuer une formation à chaque simulation, car les employés qui passent par la formation sont moins exposés aux attaques similaires.

Vous pouvez choisir de recevoir une formation ou sélectionner des cours de formation et des modules vous-même.

Sélectionnez la **Date d’échéance** de la formation pour vous assurer que les employés terminent leur formation en temps voulu.

> [!NOTE]
> Si vous choisissez de sélectionner des cours et des modules vous-même, vous pourrez toujours voir le contenu recommandé, ainsi que tous les cours et modules disponibles.
>
> ![Ajout de formations recommandées lors de la formation à la simulation d’attaque dans le centre de sécurité Microsoft 365](../../media/attack-sim-preview-add-training.png)

Dans les étapes suivantes, vous devrez **Ajouter des formations** si vous avez choisi de le sélectionner vous-même et personnalisez votre page d’accueil de formation. Vous pouvez afficher un aperçu de la page d’accueil de la formation, ainsi que modifier l’en-tête et le corps de celle-ci.

## <a name="launch-details-and-review"></a>Détails du lancement et révision

Maintenant que tout est configuré, vous pouvez lancer cette simulation immédiatement ou la planifier à une date ultérieure. Vous devrez également choisir quand mettre fin à cette simulation. Nous allons arrêter de capturer l’interaction avec cette simulation au-delà de la période sélectionnée. 

**Activer la fourniture de fuseau horaire prenant en charge la région** pour transmettre des messages d’attaque simulés à vos employés pendant leurs heures de travail en fonction de leur région.

Une fois que vous avez fini, cliquez sur **suivant** et examinez les détails de votre simulation. Cliquez sur **modifier** sur l’un des composants pour revenir en arrière et modifier les détails à modifier. Une fois l’opération terminée, cliquez sur **Envoyer**.
