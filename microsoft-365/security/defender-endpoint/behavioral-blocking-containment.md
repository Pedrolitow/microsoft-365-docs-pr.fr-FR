---
title: Blocage et confinement comportementaux
description: En savoir plus sur les fonctionnalités de blocage comportemental et d’endiguement à Pertahanan Microsoft untuk Titik Akhir
keywords: Pertahanan Microsoft untuk Titik Akhir, EDR en mode bloc, blocage en mode passif
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.collection: m365-security-compliance
search.appverid: met150
ms.openlocfilehash: ba259111f758bfb2ce34210e436f9838c0ccf060
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67740486"
---
# <a name="behavioral-blocking-and-containment"></a>Blocage et confinement comportementaux

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="overview"></a>Vue d’ensemble

Le paysage des menaces d’aujourd’hui est envahi par les [programmes malveillants sans fichier](/windows/security/threat-protection/intelligence/fileless-threats) et qui vit hors de la terre, les menaces hautement polymorphes qui mutent plus rapidement que les solutions traditionnelles peuvent suivre, et les attaques gérées par l’homme qui s’adaptent à ce que les adversaires trouvent sur les appareils compromis. Les solutions de sécurité traditionnelles ne sont pas suffisantes pour arrêter de telles attaques ; vous avez besoin de fonctionnalités d’intelligence artificielle (IA) et d’apprentissage des appareils (ML), telles que le blocage comportemental et l’endiguement, inclus dans [Defender pour point de terminaison](/windows/security).

Les fonctionnalités de blocage comportemental et d’endiguement peuvent aider à identifier et à arrêter les menaces, en fonction de leurs comportements et de leurs arborescences de traitement, même lorsque la menace a démarré l’exécution. Les composants et fonctionnalités de protection de nouvelle génération, EDR et Defender pour point de terminaison fonctionnent ensemble dans les fonctionnalités de blocage comportemental et d’endiguement.

:::image type="content" source="images/mdatp-next-gen-EDR-behavblockcontain.png" alt-text="Blocage et confinement comportementaux dans le portail Microsoft Defender ATP" lightbox="images/mdatp-next-gen-EDR-behavblockcontain.png":::

Les fonctionnalités de blocage et d’endiguement comportementaux fonctionnent avec plusieurs composants et fonctionnalités de Defender pour point de terminaison pour arrêter immédiatement les attaques et empêcher la progression des attaques.

- [La protection de nouvelle génération](microsoft-defender-antivirus-in-windows-10.md) (qui inclut l’antivirus Microsoft Defender) peut détecter les menaces en analysant les comportements et arrêter les menaces qui ont commencé à s’exécuter.

- [La détection et la réponse](overview-endpoint-detection-response.md) des points de terminaison (EDR) reçoivent des signaux de sécurité sur votre réseau, vos appareils et le comportement du noyau. Lorsque des menaces sont détectées, des alertes sont créées. Plusieurs alertes du même type sont agrégées en incidents, ce qui facilite l’examen et la réponse de votre équipe des opérations de sécurité.

- [Defender pour point de terminaison](overview-endpoint-detection-response.md) dispose d’un large éventail d’optiques entre les identités, les e-mails, les données et les applications, en plus du réseau, du point de terminaison et des signaux de comportement du noyau reçus via EDR. Composant de [Microsoft 365 Defender](../defender/microsoft-365-defender.md), Defender pour point de terminaison traite et met en corrélation ces signaux, déclenche des alertes de détection et connecte les alertes associées dans les incidents.

Avec ces fonctionnalités, d’autres menaces peuvent être évitées ou bloquées, même si elles commencent à s’exécuter. Chaque fois que des comportements suspects sont détectés, la menace est contenue, des alertes sont créées et les menaces sont arrêtées dans leurs traces.

L’image suivante montre un exemple d’alerte déclenchée par des fonctionnalités de blocage comportemental et d’endiguement :

:::image type="content" source="images/blocked-behav-alert.png" alt-text="Page Alertes avec une alerte via le blocage comportemental et l’endiguement" lightbox="images/blocked-behav-alert.png":::

## <a name="components-of-behavioral-blocking-and-containment"></a>Composants du blocage comportemental et de l’endiguement

- **[Règles de réduction de la surface d’attaque](attack-surface-reduction.md) basées sur des stratégies sur le client** Les comportements d’attaque courants prédéfinis ne peuvent pas s’exécuter, selon vos règles de réduction de la surface d’attaque. Lorsque de tels comportements tentent de s’exécuter, ils peuvent être considérés dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> comme des alertes d’information. Les règles de réduction de la surface d’attaque ne sont pas activées par défaut ; vous configurez vos stratégies dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

- **[Blocage comportemental du client](client-behavioral-blocking.md)** Les menaces sur les points de terminaison sont détectées via le Machine Learning, puis sont bloquées et corrigées automatiquement. (Le blocage comportemental du client est activé par défaut.)

- **[Le blocage des boucles de commentaires](feedback-loop-blocking.md)** (également appelé protection rapide) les détections de menaces sont observées par le biais de l’intelligence comportementale. Les menaces sont arrêtées et empêchées de s’exécuter sur d’autres points de terminaison. (Le blocage de boucle de commentaires est activé par défaut.)

- **[Détection et réponse des points de terminaison (EDR) en mode bloc](edr-in-block-mode.md)** Les artefacts ou comportements malveillants observés par le biais de la protection post-violation sont bloqués et contenus. L’EDR en mode bloc fonctionne même si l’antivirus Microsoft Defender n’est pas la solution antivirus principale. (EDR en mode bloc n’est pas activé par défaut ; vous l’activez à Microsoft 365 Defender.)

Attendez-vous à plus d’informations dans le domaine du blocage comportemental et de l’endiguement, car Microsoft continue d’améliorer les fonctionnalités et fonctionnalités de protection contre les menaces. Pour voir ce qui est planifié et en cours de déploiement, consultez la [feuille de route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap).

## <a name="examples-of-behavioral-blocking-and-containment-in-action"></a>Exemples de blocage comportemental et d’endiguement en action

Les fonctionnalités de blocage comportemental et d’endiguement ont bloqué des techniques d’attaquant telles que les suivantes :

- Vidage des informations d’identification de LSASS
- Injection interprojection
- Creusement de processus
- Contournement du contrôle de compte d’utilisateur
- Falsification de l’antivirus (par exemple, désactivation ou ajout du programme malveillant en tant qu’exclusion)
- Contact de la commande et du contrôle (C&C) pour télécharger des charges utiles
- Exploration de pièces
- Modification de l’enregistrement de démarrage
- Attaques pass-the-hash
- Installation du certificat racine
- Tentative d’exploitation pour différentes vulnérabilités

Vous trouverez ci-dessous deux exemples concrets de blocage comportemental et d’endiguement en action.

### <a name="example-1-credential-theft-attack-against-100-organizations"></a>Exemple 1 : Attaque par vol d’informations d’identification contre 100 organisations

Comme décrit dans [La poursuite à chaud des menaces insaisissables: Le blocage basé sur le comportement piloté par l’IA arrête les attaques dans leurs traces](https://www.microsoft.com/security/blog/2019/10/08/in-hot-pursuit-of-elusive-threats-ai-driven-behavior-based-blocking-stops-attacks-in-their-tracks), une attaque par vol d’informations d’identification contre 100 organisations à travers le monde a été arrêtée par des fonctionnalités de blocage comportemental et d’endiguement. Les messages électroniques de harponnage qui contenaient un document de leurre ont été envoyés aux organisations ciblées. Si un destinataire a ouvert la pièce jointe, un document distant associé a pu exécuter du code sur l’appareil de l’utilisateur et charger un programme malveillant Lokibot, qui a volé des informations d’identification, exfiltré les données volées et a attendu d’autres instructions d’un serveur de commande et de contrôle.

Les modèles device-learning basés sur le comportement dans Defender pour point de terminaison ont intercepté et arrêté les techniques de l’attaquant à deux points de la chaîne d’attaque :

- La première couche de protection a détecté le comportement d’attaque. Les classifieurs Device-Learning dans le cloud ont correctement identifié la menace et ont immédiatement demandé à l’appareil client de bloquer l’attaque.
- La deuxième couche de protection, qui a permis d’arrêter les cas où l’attaque a dépassé la première couche, a détecté un creux de processus, a arrêté ce processus et supprimé les fichiers correspondants (tels que Lokibot).

Pendant que l’attaque a été détectée et arrêtée, des alertes, telles qu’une « alerte d’accès initial », ont été déclenchées et affichées dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender/microsoft-365-defender).

:::image type="content" source="images/behavblockcontain-initialaccessalert.png" alt-text="Alerte d’accès initial dans le portail Microsoft 365 Defender" lightbox="images/behavblockcontain-initialaccessalert.png":::

Cet exemple montre comment les modèles device-learning basés sur le comportement dans le cloud ajoutent de nouvelles couches de protection contre les attaques, même après leur exécution.

### <a name="example-2-ntlm-relay---juicy-potato-malware-variant"></a>Exemple 2 : Relais NTLM - Variante de programme malveillant Juicy Potato

Comme décrit dans le récent billet de blog, [Blocage comportemental et confinement : transformation de l’optique en protection](https://www.microsoft.com/security/blog/2020/03/09/behavioral-blocking-and-containment-transforming-optics-into-protection), en janvier 2020, Defender pour point de terminaison a détecté une activité d’élévation de privilèges sur un appareil d’une organisation. Une alerte appelée « Escalade de privilèges possible à l’aide du relais NTLM » a été déclenchée.

:::image type="content" source="images/NTLMalertjuicypotato.png" alt-text="Une alerte NTLM pour les programmes malveillants Juicy Potato" lightbox="images/NTLMalertjuicypotato.png":::

La menace s’est avérée être un programme malveillant; il s’agissait d’une nouvelle variante, non vu avant, d’un outil de piratage notoire appelé Juicy Potato, qui est utilisé par les attaquants pour obtenir l’élévation des privilèges sur un appareil.

Quelques minutes après le déclenchement de l’alerte, le fichier a été analysé et confirmé comme étant malveillant. Son processus a été arrêté et bloqué, comme illustré dans l’image suivante :

:::image type="content" source="images/Artifactblockedjuicypotato.png" alt-text="Artefact bloqué"  lightbox="images/Artifactblockedjuicypotato.png":::

Quelques minutes après le blocage de l’artefact, plusieurs instances du même fichier ont été bloquées sur le même appareil, empêchant le déploiement d’un plus grand nombre d’attaquants ou d’autres programmes malveillants sur l’appareil.

Cet exemple montre qu’avec les fonctionnalités de blocage comportemental et d’endiguement, les menaces sont détectées, contenues et bloquées automatiquement.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="next-steps"></a>Prochaines étapes

- [Mer informasjon sur Defender pour point de terminaison](overview-endpoint-detection-response.md)

- [Configurer vos règles de réduction de la surface d’attaque](attack-surface-reduction.md)

- [Activer EDR en mode bloc](edr-in-block-mode.md)

- [Voir l’activité récente sur les menaces globales](https://www.microsoft.com/wdsi/threats)

- [Obtenir une vue d’ensemble de Microsoft 365 Defender](../defender/microsoft-365-defender.md)
