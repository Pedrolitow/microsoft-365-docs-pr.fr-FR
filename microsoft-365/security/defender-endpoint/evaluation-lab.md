---
title: Laboratoire d’évaluation de Microsoft Defender for Endpoint
description: Découvrez les fonctionnalités de Microsoft Defender pour les points de terminaison, exécutez des simulations d’attaques et découvrez comment il empêche, détecte et remédie aux menaces.
keywords: évaluer Microsoft Defender pour le point de terminaison, évaluation, laboratoire, simulation, windows 10, windows server 2019, laboratoire d’évaluation
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-evalutatemtp
ms.topic: article
ms.technology: mde
ms.openlocfilehash: c1a51ec4d2e17275379eb40521f506e4a83d19ef
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59177667"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>Laboratoire d’évaluation de Microsoft Defender for Endpoint

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

La conduite d’une évaluation complète du produit de sécurité peut être un processus complexe nécessitant une configuration fastidieuse de l’environnement et de l’appareil avant qu’une simulation d’attaque de bout en bout puisse réellement être effectuée. L’ajout de la complexité est la difficulté de suivre l’endroit où les activités de simulation, les alertes et les résultats sont reflétés au cours de l’évaluation.

Le laboratoire d’évaluation de Microsoft Defender pour points de terminaison est conçu pour éliminer la complexité de la configuration des appareils et de l’environnement afin de pouvoir vous concentrer sur l’évaluation des fonctionnalités de la plateforme, l’exécution de simulations et l’utilisation des fonctionnalités de prévention, de détection et de correction.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Grâce à l’expérience de mise en place simplifiée, vous pouvez vous concentrer sur l’exécution de vos propres scénarios de test et des simulations pré-réalisées pour voir les résultats de Defender for Endpoint.

Vous aurez un accès complet aux fonctionnalités puissantes de la plateforme, telles que les enquêtes automatisées, le recherche avancée et l’analyse des menaces, ce qui vous permettra de tester la pile de protection complète que Defender pour Endpoint offre.

Vous pouvez ajouter des appareils Windows 10 ou Windows Server 2019 pré-configurés pour que les versions de système d’exploitation les plus récentes et les composants de sécurité en place, ainsi que Office 2019 Standard soit installé.

Vous pouvez également installer des simulateurs de menaces. Defender pour le point de terminaison s’est associé à des plateformes de simulation de menaces de pointe pour vous aider à tester les fonctionnalités de Defender for Endpoint sans avoir à quitter le portail.

Installez votre simulateur préféré, exécutez des scénarios dans le laboratoire d’évaluation et voyez instantanément les résultats de la plateforme, le tout disponible sans frais supplémentaires. Vous aurez également un accès pratique à un large éventail de simulations que vous pouvez accéder et exécuter à partir du catalogue de simulations.

## <a name="before-you-begin"></a>Avant de commencer

Vous devrez satisfaire [](minimum-requirements.md#licensing-requirements) aux exigences de licence ou avoir accès en version d’évaluation à Microsoft Defender for Endpoint pour accéder au laboratoire d’évaluation.

Vous devez avoir **les autorisations Gérer les paramètres** de sécurité pour :

- Créer l’atelier
- Créer des appareils
- Réinitialiser le mot de passe
- Créer des simulations

Si vous avez activé le contrôle d’accès basé sur un rôle (RBAC) et créé au moins un groupe d’ordinateurs, les utilisateurs doivent avoir accès à tous les groupes d’ordinateurs.

Pour plus d’informations, voir [Créer et gérer des rôles.](user-roles.md)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Mise en place de l’atelier

Vous pouvez accéder à l’atelier à partir du menu. Dans le menu de navigation, sélectionnez **Évaluation et didacticiels > laboratoire d’évaluation.**

> [!NOTE]
>
> - Selon le type de structure d’environnement que vous sélectionnez, les appareils seront disponibles pour le nombre d’heures spécifié à partir du jour de l’activation.
> - Chaque environnement est mis en service avec un ensemble limité de périphériques de test. Lorsque vous avez utilisé les appareils mis en service et que vous les avez supprimés, vous pouvez demander d’autres appareils.
> - Vous pouvez demander des ressources d’atelier une fois par mois.

Vous avez déjà un atelier ? Veillez à activer les nouveaux simulateurs de menaces et à avoir des appareils actifs.

## <a name="setup-the-evaluation-lab"></a>Configurer le laboratoire d’évaluation

1. Dans le volet de navigation, sélectionnez **Évaluation & didacticiels** \> **Laboratoire** d’évaluation, puis sélectionnez **Laboratoire d’installation.**

    :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Image de la page d’accueil du laboratoire d’évaluation.":::

2. En fonction de vos besoins d’évaluation, vous pouvez choisir de configurer un environnement avec moins d’appareils pendant une période plus longue ou plus d’appareils sur une période plus courte. Sélectionnez votre configuration d’atelier préférée, puis **sélectionnez Suivant.**

    ![Image des options de configuration de l’atelier.](images/lab-creation-page.png)

3. (Facultatif) Vous pouvez choisir d’installer des simulateurs de menaces dans l’atelier.

    ![Image de l’agent des simulateurs d’installation.](images/install-agent.png)

   > [!IMPORTANT]
   > Vous devez d’abord accepter et donner votre consentement aux conditions générales et aux déclarations de partage d’informations.

4. Sélectionnez l’agent de simulation de menace que vous souhaitez utiliser et entrez vos détails. Vous pouvez également choisir d’installer des simulateurs de menaces ultérieurement. Si vous choisissez d’installer des agents de simulation de menace lors de l’installation de l’atelier, vous profitez de leur installation pratique sur les appareils que vous ajoutez.

    ![Image de la page récapitulatif.](images/lab-setup-summary.png)

5. Examinez le résumé et sélectionnez **Le laboratoire d’installation.**

Une fois le processus de configuration de l’atelier terminé, vous pouvez ajouter des appareils et exécuter des simulations.

## <a name="add-devices"></a>Ajouter des appareils

Lorsque vous ajoutez un appareil à votre environnement, Defender pour le point de terminaison configure un appareil bien configuré avec des détails de connexion. Vous pouvez ajouter Windows 10 ou Windows des appareils Server 2019.

L’appareil sera configuré avec la version la plus récente du système d’exploitation et de Office 2019 Standard, ainsi que d’autres applications telles que Java, Python et SysIntenals.

Si vous avez choisi d’ajouter un simulateur de menaces lors de l’installation de l’atelier, l’agent de simulateur de menaces sera installé sur tous les appareils que vous ajoutez.

L’appareil est automatiquement intégré à votre client avec les composants de sécurité Windows recommandés, qui sont allumés et en mode audit, sans aucun effort de votre part.

Les composants de sécurité suivants sont pré-configurés dans les périphériques de test :

- [Réduction de la surface d’attaque](attack-surface-reduction.md)
- [Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Accès contrôlé aux dossiers](controlled-folders.md)
- [Exploit Protection](enable-exploit-protection.md)
- [Protection du réseau](network-protection.md)
- [Détection d’applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Antivirus Microsoft Defender sera en cours (pas en mode audit). Si Antivirus Microsoft Defender vous empêche d’utiliser votre simulation, vous pouvez désactiver la protection en temps réel sur l’appareil via Sécurité Windows. Pour plus d’informations, [voir Configure always-on protection](configure-real-time-protection-microsoft-defender-antivirus.md).

Les paramètres d’examen automatisé dépendent des paramètres du client. Elle sera configurée pour être semi-automatisée par défaut. Pour plus d’informations, voir [Vue d’ensemble des enquêtes automatisées.](automated-investigations.md)

> [!NOTE]
> La connexion aux périphériques de test est effectuée à l’aide de RDP. Assurez-vous que vos paramètres de pare-feu autorisent les connexions RDP.

1. Dans le tableau de bord, **sélectionnez Ajouter un appareil.**

2. Choisissez le type d’appareil à ajouter. Vous pouvez choisir d’ajouter Windows 10 ou Windows Server 2019.

    :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="configuration de l’atelier avec options d’appareil.":::

   > [!NOTE]
   > En cas de problème lors du processus de création de l’appareil, vous serez averti et vous devrez envoyer une nouvelle demande. Si la création de l’appareil échoue, elle n’est pas comptabilisée dans le quota autorisé global.

3. Les détails de connexion sont affichés. Sélectionnez **Copier** pour enregistrer le mot de passe de l’appareil.

   > [!NOTE]
   > Le mot de passe n’est affiché qu’une seule fois. N’oubliez pas de l’enregistrer pour une utilisation ultérieure.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Image de l’appareil ajouté avec les détails de connexion.":::

4. La mise en place de l’appareil commence. Cela peut prendre jusqu’à 30 minutes environ.

5. Consultez l’état des périphériques de test, les niveaux de risque et d’exposition, ainsi que l’état des installations de simulateur en sélectionnant l’onglet **Appareils.**

    ![Image de l’onglet Appareils.](images/machines-tab.png)

   > [!TIP]
   > Dans la colonne **État du** simulateur, vous pouvez pointer sur l’icône d’informations pour connaître l’état d’installation d’un agent.

## <a name="request-for-more-devices"></a>Demander plus d’appareils

Lorsque tous les appareils existants sont utilisés et supprimés, vous pouvez demander d’autres appareils. Vous pouvez demander des ressources d’atelier une fois par mois.

1. Dans le tableau de bord du laboratoire d’évaluation, **sélectionnez Demander plus d’appareils.**

   ![Image de demande pour plus d’appareils.](images/request-more-devices.png)

2. Choisissez votre configuration.
3. Envoyez la demande.

Lorsque la demande est envoyée avec succès, vous verrez une bannière de confirmation verte et la date de la dernière soumission.

Vous pouvez trouver l’état de votre demande dans l’onglet **Actions** de l’utilisateur, qui sera approuvé dans quelques heures.

Une fois approuvés, les appareils demandés sont ajoutés à la mise en place de votre atelier et vous pouvez en créer d’autres.

> [!TIP]
> Pour en savoir plus sur votre atelier, n’oubliez pas de consulter notre bibliothèque de simulations.

## <a name="simulate-attack-scenarios"></a>Simuler des scénarios d’attaque

Utilisez les périphériques de test pour exécuter vos propres simulations d’attaques en vous y connectant.

Vous pouvez simuler des scénarios d’attaque à l’aide des outils suivants :

- Scénarios d’attaque « Faire [vous-même »](https://security.microsoft.com/tutorials/all)
- Simulateurs de menaces

Vous pouvez également utiliser le service [de recherche avancée](advanced-hunting-overview.md) pour interroger les données et l’analyse des [menaces](threat-analytics.md) afin d’afficher des rapports sur les menaces émergentes.

### <a name="do-it-yourself-attack-scenarios"></a>Scénarios d’attaques do-it-yourself

Si vous recherchez une simulation pré-réalisée, vous pouvez utiliser nos [scénarios](https://security.microsoft.com/tutorials/all)d’attaque « Faites-le vous-même ». Ces scripts sont sûrs, documentés et faciles à utiliser. Ces scénarios reflèteront les fonctionnalités de Defender for Endpoint et vous feront découvrir l’expérience d’examen.

Si vous recherchez une simulation pré-réalisée, vous pouvez utiliser nos [scénarios](https://security.microsoft.com/tutorials/all)d’attaque « Faites-le vous-même ». Ces scripts sont sûrs, documentés et faciles à utiliser. Ces scénarios reflèteront les fonctionnalités de Defender for Endpoint et vous feront découvrir l’expérience d’examen.

> [!NOTE]
> La connexion aux périphériques de test est effectuée à l’aide de RDP. Assurez-vous que vos paramètres de pare-feu autorisent les connexions RDP.

1. Connecter sur votre appareil et exécutez une simulation d’attaque en **sélectionnant Connecter**.

    ![Image du bouton de connexion pour les périphériques de test.](images/test-machine-table.png)

2. Enregistrez le fichier RDP et lancez-le en sélectionnant **Connecter**.

    ![Image de la connexion bureau à distance.](images/remote-connection.png)

    > [!NOTE]
    > Si vous n’avez pas de copie du mot de passe enregistrée lors  de la configuration initiale, vous pouvez réinitialiser le mot de passe en sélectionnant Réinitialiser le mot de passe dans le menu :
    >
    > ![Image de réinitialisation du mot de passe.](images/reset-password-test-machine.png)
    >
    > L’appareil change son état en « Exécution de la réinitialisation du mot de passe », puis votre nouveau mot de passe vous sera présenté dans quelques minutes.

3. Entrez le mot de passe qui a été affiché lors de l’étape de création de l’appareil.

   ![Image de la fenêtre pour entrer les informations d’identification.](images/enter-password.png)

4. Exécutez des simulations d’attaques par vous-même sur l’appareil.

### <a name="threat-simulator-scenarios"></a>Scénarios de simulateur de menaces

Si vous avez choisi d’installer l’un des simulateurs de menaces pris en charge pendant l’installation de l’atelier, vous pouvez exécuter les simulations intégrées sur les périphériques du laboratoire d’évaluation.

L’exécution de simulations de menaces à l’aide de plateformes tierces est un bon moyen d’évaluer microsoft Defender pour les fonctionnalités de point de terminaison dans les limites d’un environnement de laboratoire.

> [!NOTE]
>
> Avant d’exécuter des simulations, assurez-vous que les conditions suivantes sont remplies :
>
> - Les appareils doivent être ajoutés au laboratoire d’évaluation
> - Les simulateurs de menaces doivent être installés dans le laboratoire d’évaluation

1. Dans le portail, **sélectionnez Créer une simulation.**

2. Sélectionnez un simulateur de menaces.

    ![Image de la sélection du simulateur de menaces.](images/select-simulator.png)

3. Choisissez une simulation ou parcourez la galerie de simulations pour parcourir les simulations disponibles.

    Vous pouvez obtenir la galerie de simulations à partir de :
    - Tableau de bord d’évaluation principal dans la **vignette Vue d’ensemble simulations** ou
    - En naviguant à partir  du volet de navigation Évaluation et didacticiels \> **Simulation & didacticiels,** puis sélectionnez Le catalogue **simulations**.

4. Sélectionnez les appareils sur lequel vous souhaitez exécuter la simulation.

5. Sélectionnez **Créer une simulation.**

6. Affichez la progression d’une simulation en sélectionnant **l’onglet Simulations.** Afficher l’état de simulation, les alertes actives et d’autres détails.

    ![Image de l’onglet Simulations.](images/simulations-tab.png)

Après avoir lancé vos simulations, nous vous encourageons à parcourir la barre de progression de l’atelier et à explorer Microsoft Defender pour le point de terminaison qui a déclenché une investigation et une correction **automatisées.** Consultez les preuves collectées et analysées par la fonctionnalité.

Recherchez des preuves d’attaque par le biais d’une recherche avancée à l’aide du langage de requête enrichi et de la télémétrie brute, puis consultez certaines menaces mondiales documentées dans l’analyse des menaces.

## <a name="simulation-gallery"></a>Galerie de simulations

Microsoft Defender pour le point de terminaison s’est associé à différentes plateformes de simulation de menaces pour vous donner un accès pratique pour tester les fonctionnalités de la plateforme directement à partir du portail.

Affichez toutes les simulations disponibles en allant au catalogue  **Simulations et** didacticiels \> **Simulations**  à partir du menu.

Une liste d’agents de simulation de menace tiers pris en charge est répertoriée, et des types spécifiques de simulations ainsi que des descriptions détaillées sont fournis dans le catalogue.

Vous pouvez facilement exécuter n’importe quelle simulation disponible directement à partir du catalogue.

![Image du catalogue de simulations.](images/simulations-catalog.png)

Chaque simulation est livré avec une description détaillée du scénario d’attaque et des références telles que les techniques d’attaque MITRE utilisées et des exemples de requêtes de recherche avancée que vous exécutez.

**Exemples :**

![Image de description de simulation détaillée1.](images/simulation-details-aiq.png)

![Image de description de simulation détaillée2.](images/simulation-details-sb.png)

## <a name="evaluation-report"></a>Rapport d’évaluation

Les rapports de laboratoire résument les résultats des simulations effectuées sur les appareils.

![Image du rapport d’évaluation.](images/eval-report.png)

En un coup d’œil, vous pourrez rapidement voir :

- Incidents déclenchés
- Alertes générées
- Évaluations du niveau d’exposition
- Catégories de menaces observées
- Sources de détection
- Enquêtes automatisées

## <a name="provide-feedback"></a>Envoyer des commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions à partir des fonctionnalités du produit et des résultats d’évaluation.

Faites-nous part de vos commentaires en sélectionnant **Fournir des commentaires.**

![Image de commentaires.](images/send-us-feedback-eval-lab.png)
