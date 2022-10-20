---
title: laboratoire d’évaluation Microsoft Defender pour point de terminaison
description: Découvrez Microsoft Defender pour point de terminaison fonctionnalités, exécutez des simulations d’attaque et découvrez comment elle empêche, détecte et corrige les menaces.
keywords: évaluer Microsoft Defender pour point de terminaison, évaluation, laboratoire, simulation, windows 10, windows server 2019, laboratoire d’évaluation
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.service: microsoft-365-security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-evalutatemtp
- highpri
- tier1
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: b1525f13f0b870ac7bdf2fb98e4a74f4111b8c96
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630685"
---
# <a name="microsoft-defender-for-endpoint-evaluation-lab"></a>laboratoire d’évaluation Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-enablesiem-abovefoldlink)

L’exécution d’une évaluation complète du produit de sécurité peut être un processus complexe nécessitant une configuration fastidieuse de l’environnement et de l’appareil avant qu’une simulation d’attaque de bout en bout puisse réellement être effectuée. L’ajout de la complexité est le défi du suivi où les activités de simulation, les alertes et les résultats sont reflétés pendant l’évaluation.

Le laboratoire d’évaluation Microsoft Defender pour point de terminaison est conçu pour éliminer les complexités de la configuration de l’appareil et de l’environnement afin que vous puissiez vous concentrer sur l’évaluation des fonctionnalités de la plateforme, l’exécution de simulations et l’affichage des fonctionnalités de prévention, de détection et de correction en action.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4qLUM]

Avec l’expérience de configuration simplifiée, vous pouvez vous concentrer sur l’exécution de vos propres scénarios de test et les simulations prédéfines pour voir comment Defender pour point de terminaison fonctionne.

Vous aurez un accès complet aux puissantes fonctionnalités de la plateforme, telles que les investigations automatisées, la chasse avancée et l’analyse des menaces, ce qui vous permet de tester la pile de protection complète que Defender pour point de terminaison offre.

Vous pouvez ajouter des appareils Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 et Linux (Ubuntu) qui sont préconfigurés pour que les dernières versions du système d’exploitation et les composants de sécurité appropriés soit installés, ainsi qu’Office 2019 Standard.

Vous pouvez également installer des simulateurs de menaces. Defender pour point de terminaison s’est associé à des plateformes de simulation de menaces de pointe pour vous aider à tester les fonctionnalités de Defender pour point de terminaison sans avoir à quitter le portail.

Installez votre simulateur préféré, exécutez des scénarios dans le laboratoire d’évaluation et découvrez instantanément les performances de la plateforme, le tout disponible sans frais supplémentaires pour vous. Vous aurez également un accès pratique à un large éventail de simulations que vous pouvez accéder et exécuter à partir du catalogue de simulations.

## <a name="before-you-begin"></a>Avant de commencer

Vous devez respecter les [exigences de licence](minimum-requirements.md#licensing-requirements) ou disposer d’un accès d’essai à Microsoft Defender pour point de terminaison pour accéder au laboratoire d’évaluation.

Vous devez disposer **des autorisations Gérer les paramètres de sécurité** pour :

- Créer le labo
- Créer des appareils
- Réinitialiser le mot de passe
- Créer des simulations

Si vous avez activé le contrôle d’accès en fonction du rôle (RBAC) et créé au moins un groupe d’ordinateurs, les utilisateurs doivent avoir accès à Tous les groupes d’ordinateurs.

Pour plus d’informations, consultez [Créer et gérer des rôles](user-roles.md).

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink)

## <a name="get-started-with-the-lab"></a>Prise en main du labo

Vous pouvez accéder au labo à partir du menu. Dans le menu de navigation, sélectionnez **Évaluation et didacticiels > laboratoire d’évaluation**.

> [!NOTE]
>
> - Selon le type de structure d’environnement que vous sélectionnez, les appareils sont disponibles pour le nombre d’heures spécifié à partir du jour de l’activation.
> - Chaque environnement est approvisionné avec un ensemble limité d’appareils de test. Une fois que vous avez utilisé les appareils approvisionnés et que vous les avez supprimés, vous pouvez demander d’autres appareils.
> - Vous pouvez demander des ressources de laboratoire une fois par mois.

Vous avez déjà un labo ? Veillez à activer les nouveaux simulateurs de menaces et à disposer d’appareils actifs.

## <a name="setup-the-evaluation-lab"></a>Configurer le laboratoire d’évaluation

1. Dans le volet de navigation, sélectionnez **Évaluation & didacticiels** \> **Laboratoire d’évaluation**, puis sélectionnez **Le labo d’installation**.

   :::image type="content" source="../../media/evaluationtutormenu.png" alt-text="Page d’accueil du laboratoire d’évaluation" lightbox="../../media/evaluationtutormenu.png":::

2. En fonction de vos besoins d’évaluation, vous pouvez choisir de configurer un environnement avec moins d’appareils pour une période plus longue ou plus d’appareils pour une période plus courte. Sélectionnez votre configuration de laboratoire préférée, puis **sélectionnez Suivant**.

    :::image type="content" source="images/lab-creation-page.png" alt-text="Options de configuration du labo" lightbox="images/lab-creation-page.png":::

3. (Facultatif) Vous pouvez choisir d’installer des simulateurs de menaces dans le labo.

    :::image type="content" source="images/install-agent.png" alt-text="Page de l’agent des simulateurs d’installation" lightbox="images/install-agent.png":::

   > [!IMPORTANT]
   > Vous devez d’abord accepter et donner votre consentement aux conditions et aux instructions de partage d’informations.

4. Sélectionnez l’agent de simulation de menace que vous souhaitez utiliser et entrez vos détails. Vous pouvez également choisir d’installer des simulateurs de menaces ultérieurement. Si vous choisissez d’installer des agents de simulation de menaces pendant la configuration du labo, vous aurez l’avantage de les installer facilement sur les appareils que vous ajoutez.

   :::image type="content" source="images/lab-setup-summary.png" alt-text="Page récapitulative" lightbox="images/lab-setup-summary.png":::

5. Passez en revue le résumé et sélectionnez **Le labo d’installation**.

Une fois le processus d’installation du labo terminé, vous pouvez ajouter des appareils et exécuter des simulations.

## <a name="add-devices"></a>Ajouter des appareils

Lorsque vous ajoutez un appareil à votre environnement, Defender pour point de terminaison configure un appareil bien configuré avec les détails de la connexion. Vous pouvez ajouter Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 et Linux (Ubuntu).

L’appareil sera configuré avec la version la plus récente du système d’exploitation et d’Office 2019 Standard, ainsi que d’autres applications telles que Java, Python et SysIntenals.

Si vous avez choisi d’ajouter un simulateur de menaces pendant la configuration du labo, l’agent du simulateur de menaces est installé sur tous les appareils que vous ajoutez.

L’appareil est automatiquement intégré à votre locataire avec les composants de sécurité Windows recommandés activés et en mode audit, sans aucun effort de votre côté.

Les composants de sécurité suivants sont préconfigurés sur les appareils de test :

- [Réduction de la surface d’attaque](attack-surface-reduction.md)
- [Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md)
- [Accès contrôlé aux dossiers](controlled-folders.md)
- [Exploit Protection](enable-exploit-protection.md)
- [Protection du réseau](network-protection.md)
- [Détection d’applications potentiellement indésirables](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md)
- [Protection fournie par le cloud](cloud-protection-microsoft-defender-antivirus.md)
- [Microsoft Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview)

> [!NOTE]
> Microsoft Defender Antivirus est activé (pas en mode audit). Si Microsoft Defender Antivirus vous empêche d’exécuter votre simulation, vous pouvez désactiver la protection en temps réel sur l’appareil via Sécurité Windows. Pour plus d’informations, consultez [Configurer la protection always on](configure-real-time-protection-microsoft-defender-antivirus.md).

Les paramètres d’investigation automatisée dépendent des paramètres du locataire. Elle sera configurée pour être semi-automatisée par défaut. Pour plus [d’informations, consultez Vue d’ensemble des enquêtes automatisées](automated-investigations.md).

> [!NOTE]
> La connexion aux appareils de test est effectuée à l’aide de RDP. Assurez-vous que vos paramètres de pare-feu autorisent les connexions RDP.

1. Dans le tableau de bord, sélectionnez **Ajouter un appareil**.

2. Choisissez le type d’appareil à ajouter. Vous pouvez choisir d’ajouter Windows 10, Windows 11, Windows Server 2019, Windows Server 2016 et Linux (Ubuntu).

   :::image type="content" source="../../media/add-machine-optionsnew.png" alt-text="Configuration du labo avec les options d’appareil" lightbox="../../media/add-machine-optionsnew.png":::

   > [!NOTE]
   > Si un problème se produit avec le processus de création de l’appareil, vous serez averti et vous devrez envoyer une nouvelle demande. Si la création de l’appareil échoue, elle ne sera pas comptabilisée dans le quota global autorisé.

3. Les détails de la connexion sont affichés. Sélectionnez **Copier** pour enregistrer le mot de passe de l’appareil.

   > [!NOTE]
   > Le mot de passe n’est affiché qu’une seule fois. Veillez à l’enregistrer pour une utilisation ultérieure.

    :::image type="content" source="../../media/add-machine-eval-lab-new.png" alt-text="Appareil ajouté avec les détails de la connexion" lightbox="../../media/add-machine-eval-lab-new.png":::

4. La configuration de l’appareil commence. Cela peut prendre jusqu’à environ 30 minutes.

5. Consultez l’état des appareils de test, les niveaux de risque et d’exposition, ainsi que l’état des installations de simulateur en sélectionnant l’onglet **Appareils** .

   :::image type="content" source="images/machines-tab.png" alt-text="Onglet Appareils" lightbox="images/machines-tab.png":::
    

   > [!TIP]
   > Dans la colonne **d’état du simulateur** , vous pouvez pointer sur l’icône d’informations pour connaître l’état d’installation d’un agent.


## <a name="add-a-domain-controller"></a>Ajouter un contrôleur de domaine 

Ajoutez un contrôleur de domaine pour exécuter des scénarios complexes tels que le déplacement latéral et les attaques multiphases sur plusieurs appareils.


>[!NOTE]
>La prise en charge du domaine est disponible uniquement dans le portail Microsoft 365 Defender (security.microsoft.com).

1. Dans le tableau de bord, sélectionnez **Ajouter un appareil**.

2. Sélectionnez **Windows Server 2019**, puis **sélectionnez Définir comme contrôleur de domaine**. 

3. Une fois que votre contrôleur de domaine a été approvisionné, vous pouvez créer des appareils joints à un domaine en cliquant sur **Ajouter un appareil**. Sélectionnez ensuite Windows 10/Windows 11, puis **joignez-vous au domaine**. 

>[!NOTE]
>Un seul contrôleur de domaine peut être actif à la fois. L’appareil du contrôleur de domaine reste actif tant qu’un appareil actif y est connecté.



## <a name="request-for-more-devices"></a>Demander plus d’appareils

Lorsque tous les appareils existants sont utilisés et supprimés, vous pouvez demander d’autres appareils. Vous pouvez demander des ressources de laboratoire une fois par mois.

1. Dans le tableau de bord du labo d’évaluation, sélectionnez **Demander d’autres appareils**.

   :::image type="content" source="images/request-more-devices.png" alt-text="Option demander plus d’appareils" lightbox="images/request-more-devices.png":::

2. Choisissez votre configuration.
3. Envoyez la demande.

Lorsque la demande est envoyée avec succès, vous voyez une bannière de confirmation verte et la date de la dernière soumission.

Vous pouvez trouver l’état de votre demande sous l’onglet **Actions de l’utilisateur** , qui sera approuvé en quelques heures.

Une fois approuvés, les appareils demandés seront ajoutés à votre configuration lab et vous pourrez créer d’autres appareils.

> [!TIP]
> Pour tirer le meilleur parti de votre laboratoire, n’oubliez pas de consulter notre bibliothèque de simulations.

## <a name="simulate-attack-scenarios"></a>Simuler des scénarios d’attaque

Utilisez les appareils de test pour exécuter vos propres simulations d’attaque en vous connectant à eux.

Vous pouvez simuler des scénarios d’attaque à l’aide de :

- [Scénarios d’attaque « Do It Yourself »](https://security.microsoft.com/tutorials/all)
- Simulateurs de menaces

Vous pouvez également utiliser [la chasse avancée](advanced-hunting-overview.md) pour interroger des données et [l’analytique des](threat-analytics.md) menaces pour afficher des rapports sur les menaces émergentes.

### <a name="do-it-yourself-attack-scenarios"></a>Scénarios d’attaque par vous-même

Si vous recherchez une simulation prédéfine, vous pouvez utiliser nos [scénarios d’attaque « Do It Yourself ».](https://security.microsoft.com/tutorials/all) Ces scripts sont sécurisés, documentés et faciles à utiliser. Ces scénarios reflètent les fonctionnalités de Defender pour point de terminaison et vous guident tout au long de l’expérience d’investigation.

> [!NOTE]
> La connexion aux appareils de test est effectuée à l’aide de RDP. Assurez-vous que vos paramètres de pare-feu autorisent les connexions RDP.

1. Connectez-vous à votre appareil et exécutez une simulation d’attaque en sélectionnant **Se connecter**.

    :::image type="content" source="images/test-machine-table.png" alt-text="Bouton Se connecter pour les appareils de test" lightbox="images/test-machine-table.png":::


   :::image type="content" source="images/remote-connection.png" alt-text="Écran de connexion bureau à distance" lightbox="images/remote-connection.png":::

    Pour **les appareils Linux** : vous devez utiliser un client SSH local et la commande fournie. 


    > [!NOTE]
    > Si vous ne disposez pas d’une copie du mot de passe enregistrée lors de la configuration initiale, vous pouvez réinitialiser le mot de passe en sélectionnant **Réinitialiser le mot de passe** dans le menu :
    >
    > :::image type="content" source="images/reset-password-test-machine.png" alt-text="Option Réinitialiser le mot de passe" lightbox="images/reset-password-test-machine.png":::
    >
    > L’appareil remplacera son état par « Exécution de la réinitialisation du mot de passe », puis vous recevrez votre nouveau mot de passe dans quelques minutes.

3. Entrez le mot de passe qui a été affiché lors de l’étape de création de l’appareil.

   :::image type="content" source="images/enter-password.png" alt-text="Écran sur lequel vous entrez les informations d’identification" lightbox="images/enter-password.png":::

4. Exécutez des simulations d’attaque do-it-yourself sur l’appareil.

### <a name="threat-simulator-scenarios"></a>Scénarios de simulateur de menaces

Si vous avez choisi d’installer l’un des simulateurs de menaces pris en charge pendant la configuration du labo, vous pouvez exécuter les simulations intégrées sur les appareils du laboratoire d’évaluation.

L’exécution de simulations de menaces à l’aide de plateformes tierces est un bon moyen d’évaluer Microsoft Defender pour point de terminaison fonctionnalités dans les limites d’un environnement lab.

> [!NOTE]
>
> Avant de pouvoir exécuter des simulations, vérifiez que les exigences suivantes sont remplies :
>
> - Les appareils doivent être ajoutés au laboratoire d’évaluation
> - Les simulateurs de menaces doivent être installés dans le laboratoire d’évaluation

1. Dans le portail, sélectionnez **Créer une simulation**.

2. Sélectionnez un simulateur de menaces.

   :::image type="content" source="images/select-simulator.png" alt-text="Sélection du simulateur de menaces" lightbox="images/select-simulator.png":::

3. Choisissez une simulation ou parcourez la galerie de simulations pour parcourir les simulations disponibles.

    Vous pouvez accéder à la galerie de simulations à partir de :
    - Tableau de bord d’évaluation principal dans la vignette **Vue d’ensemble des simulations** ou
    - En naviguant à partir du volet **de navigation, évaluation et didacticiels** \> **Simulation & didacticiels**, puis sélectionnez **Le catalogue Simulations**.

4. Sélectionnez les appareils sur lesquels vous souhaitez exécuter la simulation.

5. Sélectionnez **Créer une simulation**.

6. Affichez la progression d’une simulation en sélectionnant l’onglet **Simulations** . Affichez l’état de simulation, les alertes actives et d’autres détails.

   :::image type="content" source="images/simulations-tab.png" alt-text="Onglet Simulations" lightbox="images/simulations-tab.png":::

Après avoir exécuté vos simulations, nous vous encourageons à parcourir la barre de progression du labo et à explorer **Microsoft Defender pour point de terminaison déclenché une investigation et une correction automatisées**. Découvrez les preuves collectées et analysées par la fonctionnalité.

Recherchez des preuves d’attaque par le biais d’une chasse avancée à l’aide du langage de requête enrichi et de la télémétrie brute et découvrez certaines menaces à l’échelle mondiale documentées dans l’analyse des menaces.

## <a name="simulation-gallery"></a>Galerie de simulations

Microsoft Defender pour point de terminaison a conclu un partenariat avec différentes plateformes de simulation de menaces pour vous donner un accès pratique pour tester les fonctionnalités de la plateforme directement à partir du portail.

Affichez toutes les simulations disponibles en allant dans le catalogue  **Simulations et didacticiels** \> **Simulations**  dans le menu.

Une liste d’agents de simulation de menace tiers pris en charge est répertoriée, et des types spécifiques de simulations ainsi que des descriptions détaillées sont fournis dans le catalogue.

Vous pouvez facilement exécuter n’importe quelle simulation disponible directement à partir du catalogue.

:::image type="content" source="images/simulations-catalog.png" alt-text="Catalogue de simulations" lightbox="images/simulations-catalog.png":::

Chaque simulation est accompagnée d’une description détaillée du scénario d’attaque et de références telles que les techniques d’attaque MITRE utilisées et les exemples de requêtes de chasse avancées que vous exécutez.

**Exemples :**

:::image type="content" source="images/simulation-details-aiq.png" alt-text="Exemple de volet détails de la description de la simulation pour les méthodes de persistance" lightbox="images/simulation-details-aiq.png":::

:::image type="content" source="images/simulation-details-sb.png" alt-text="Détails de la description de la simulation pour APT29" lightbox="images/simulation-details-sb.png":::

## <a name="evaluation-report"></a>Rapport d’évaluation

Les rapports de laboratoire récapitulent les résultats des simulations effectuées sur les appareils.

:::image type="content" source="images/eval-report.png" alt-text="Rapport d’évaluation" lightbox="images/eval-report.png":::

En un coup d’œil, vous serez rapidement en mesure de voir :

- Incidents déclenchés
- Alertes générées
- Évaluations sur le niveau d’exposition
- Catégories de menaces observées
- Sources de détection
- Enquêtes automatisées

## <a name="provide-feedback"></a>Envoyer des commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions à partir des fonctionnalités du produit et des résultats de l’évaluation.

Faites-nous part de votre opinion en sélectionnant **Fournir des commentaires**.

:::image type="content" source="images/send-us-feedback-eval-lab.png" alt-text="La page de commentaires" lightbox="images/send-us-feedback-eval-lab.png":::
