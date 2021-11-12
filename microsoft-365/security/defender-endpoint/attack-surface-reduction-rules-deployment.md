---
title: Déployer des règles de réduction de la surface d’attaque
description: Fournit des conseils pour déployer des règles de réduction de la surface d’attaque.
keywords: Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar, jcedola
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: f3ab66236697b52f0b267685be5247b9da88219d
ms.sourcegitcommit: 6dbf879f769a825ed7039363f3a91d676e355ee0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2021
ms.locfileid: "60947842"
---
# <a name="attack-surface-reduction-rules-deployment-guide"></a>Guide de déploiement des règles de réduction de la surface d’attaque

## <a name="before-you-begin"></a>Avant de commencer

Les surfaces d’attaque sont tous les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Les surfaces d’attaque de votre organisation incluent tous les endroits où un attaquant peut compromettre les appareils ou réseaux de votre organisation. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’attaque. La configuration des règles de réduction de la surface d’attaque (ASR), l’une des nombreuses fonctionnalités de sécurité de Microsoft Defender pour Endpoint, peut vous aider.

Les règles asr ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts obscurcis ou suspects
- Comportements que les applications n’ont généralement pas pendant le travail quotidien normal

En réduisant les différentes surfaces d’attaque, vous pouvez empêcher les attaques de se produire en premier lieu.

Lors de votre préparation initiale, il est essentiel de comprendre les fonctionnalités des systèmes que vous allez mettre en place. Comprendre les fonctionnalités vous aidera à déterminer les règles de la asr qui sont les plus importantes pour la protection de votre organisation.

>[!IMPORTANT]
>Ce guide fournit des images et des exemples pour vous aider à décider comment configurer les règles de la asr. Ces images et exemples peuvent ne pas refléter les meilleures options de configuration pour votre environnement.

Avant de commencer, examinez La vue d’ensemble de la réduction de [la surface](overview-attack-surface-reduction.md)d’attaque et la [démystification](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) des règles de réduction de la surface d’attaque - Partie 1 pour obtenir des informations de base. Pour comprendre les domaines de couverture et l’impact potentiel, familiarisez-vous avec l’ensemble actuel de règles asr. voir [Règles de réduction de la surface d’attaque.](attack-surface-reduction-rules.md)

Les règles de réduction de la surface d’attaque ne sont qu’une fonctionnalité des fonctionnalités de réduction de la surface d’attaque dans Microsoft Defender for Endpoint. Ce document détaille le déploiement efficace des règles de la asr pour arrêter les menaces avancées telles que les ransomware gérés par l’homme et d’autres menaces.  

### <a name="rules-by-category"></a>Règles par catégorie

Comme indiqué dans utiliser les règles de réduction de la surface d’attaque pour empêcher [l’infection](attack-surface-reduction.md)par des programmes malveillants, il existe plusieurs règles de réduction de la surface d’attaque dans MDE que vous pouvez activer pour protéger votre organisation. Voici les règles décomposées par catégorie :

<br/>

| Menaces polymorphes | Mouvement latéral lors & vol d’informations d’identification | Règles des applications de productivité |  Règles de messagerie | Règles de script | Règles de non-respect des règles |
|:---|:---|:---|:---|:---|:---|
| Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à une prévalence (1 000 ordinateurs), à l’âge (24 heures) ou à des critères de listes fiables | Bloquer les créations de processus provenant de commandes PSExec et WMI | Empêcher Office applications de créer du contenu exécutable | Bloquer le contenu exécutable du client de messagerie et de la messagerie web | Bloquer le code JS/VBS/PS/macro obscurci | Bloquer l’utilisation abusive des pilotes signés vulnérables <sup> exploités [[1](#fn1)]<sup></sup>  |
| Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB | Bloquer le vol d’informations d Windows du sous-système de l’autorité de sécurité locale (lsass.exe) <sup> [[2](#fn1)]<sup></sup>   | Empêcher Office applications de créer des processus enfants |  Empêcher uniquement les applications Office communication de créer des processus enfants | Empêcher JS/VBS de lancer du contenu exécutable téléchargé | |
| Utiliser la protection avancée contre les ransomware | Bloquer la persistance via un abonnement à des événements WMI | Empêcher Office applications d’injecter du code dans d’autres processus | Empêcher Office applications de communication de créer des processus enfants | | |
| | | Empêcher Adobe Reader de créer des processus enfants | | | |

(<a id="fn1">1</a>) Bloquer l’utilisation abusive des pilotes _signés vulnérables exploités_ n’est pas disponible actuellement dans la sécurité des points de terminaison MEM. Vous pouvez configurer cette règle à l’aide [de MEM OMA-URI](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Certaines règles de réduction de la réduction du bruit génèrent un bruit considérable, mais ne bloquent pas les fonctionnalités. Par exemple, si vous êtes en train de mettre à jour Chrome ; Chrome accède à lsass.exe ; les mots de passe sont stockés dans lsass sur l’appareil. Toutefois, Chrome ne doit pas accéder aux appareils lsass.exe. Si vous activez la règle pour bloquer l’accès au lsass, elle génère un grand nombre d’événements. Ces événements sont de bons événements, car le processus de mise à jour logicielle ne doit pas lsass.exe. L’activation de cette règle empêchera les mises à jour Chrome d’accéder à l’application lsass, mais ne bloquera pas la mise à jour de Chrome ; Cela est également vrai pour les autres applications qui appellent inutilement des lsass.exe. La règle de blocage d’accès à _lsass_ bloque les appels inutiles à l’application, mais ne bloque pas l’exécution de l’application.

### <a name="infrastructure-requirements"></a>Conditions requises en matière d’infrastructure

Bien qu’il soit possible d’implémenter plusieurs méthodes d’implémentation des règles de la asr, ce guide est basé sur une infrastructure composée des points ci-après :

- Azure Active Directory Domain Services
- Microsoft Endpoint Management (MEM)
- Windows 10 et Windows 11 périphériques
- Microsoft Defender pour le point de terminaison E5 ou Windows licences E5

Pour tirer pleinement parti des règles et des rapports de la asrx Microsoft 365 Defender, nous vous recommandons d’utiliser une licence E5 Windows E5 et A5. En savoir plus : [Conditions minimales requises pour Microsoft Defender pour le point de terminaison.](minimum-requirements.md)

>[!Note]
>Il existe plusieurs méthodes pour configurer les règles de la asr. Les règles asr peuvent être configurées à l’aide de : Microsoft Endpoint Manager (MEM), PowerShell, stratégie de groupe, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Si vous utilisez une configuration d’infrastructure  différente de celle répertoriée pour les conditions requises pour l’infrastructure (ci-dessus), vous pouvez en savoir plus sur le déploiement de règles de réduction de la surface d’attaque à l’aide d’autres configurations ici : Activez les règles de réduction de la [surface](enable-attack-surface-reduction.md)d’attaque.  

### <a name="asr-rules-dependencies"></a>Dépendances des règles asr

Antivirus Microsoft Defender doit être activée et configurée en tant que solution antivirus principale et doit être en mode suivant :

- Solution antivirus/anti-programme malveillant principale  
- État : mode actif

Antivirus Microsoft Defender ne doit pas être dans l’un des modes suivants :

- Passive
- Mode passif avec détection et réponse des points de terminaison (PEPT) en mode blocage
- Analyse périodique limitée (LPS)
- Désactivé

Voir : [Protection et](cloud-protection-microsoft-defender-antivirus.md)protection cloud Antivirus Microsoft Defender .

### <a name="cloud-protection-maps-must-be-enabled"></a>La protection cloud (MAPS) doit être activée

Antivirus Microsoft Defender fonctionne en toute transparence avec les services cloud de Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard, fournissant sans doute la meilleure protection antivirus. La protection cloud est essentielle pour empêcher les violations de programmes malveillants et constitue un composant essentiel des règles de la asr.
[Activer la protection cloud dans Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Antivirus Microsoft Defender composants doivent être des versions actuelles

Les versions de Antivirus Microsoft Defender suivantes ne doivent pas être plus anciennes que la version la plus disponible :

- **Antivirus Microsoft Defender version de mise à jour** de plateforme : Antivirus Microsoft Defender plateforme est mise à jour tous les mois.
- **Antivirus Microsoft Defender version du moteur** : le moteur Antivirus Microsoft Defender est mis à jour tous les mois.
- **Antivirus Microsoft Defender** la sécurité : Microsoft met continuellement à jour l’intelligence de sécurité Microsoft Defender (également appelée, définition et signature) pour répondre aux dernières menaces et affiner la logique de détection.

Le fait Antivirus Microsoft Defender versions actuelles permet de réduire les règles de réduction de la réduction des résultats faux positifs et Antivirus Microsoft Defender fonctionnalités de détection. Pour plus d’informations sur les versions actuelles et sur la mise à jour des différents composants de Antivirus Microsoft Defender, consultez la Antivirus Microsoft Defender prise en charge [de la plateforme.](manage-updates-baselines-microsoft-defender-antivirus.md)

## <a name="asr-rules-deployment-phases"></a>Phases de déploiement des règles asr

Comme avec toute nouvelle implémentation à grande échelle susceptible d’avoir un impact sur vos opérations métier, il est important d’être méthodique dans la planification et l’implémentation. En raison des fonctionnalités puissantes des règles de protection contre les programmes malveillants dans la prévention des programmes malveillants, une planification et un déploiement attentifs de ces règles sont nécessaires pour s’assurer qu’elles fonctionnent au mieux pour vos flux de travail client uniques. Pour travailler dans votre environnement, vous devez planifier, tester, implémenter et mettre en œuvre les règles de la asr avec soin.  

> [!div class="mx-imgBorder"]
> ![Phases de déploiement des règles asr](images/asr-rules-deployment-phases.png)

>[!Note]
>Pour les clients qui utilisent un système HIPS non Microsoft et qui sont en transition vers microsoft Defender pour les règles de réduction de la surface d’attaque du point de terminaison : Microsoft recommande aux clients d’exécuter leur solution HIPS côte à côte avec leur déploiement de règles de réduction de la surface d’attaque jusqu’au moment où vous basculez du mode Audit au mode Blocage. N’oubliez pas que vous devez joindre votre fournisseur d’antivirus tiers pour obtenir des recommandations d’exclusion.  

## <a name="phase-1-plan"></a>Phase 1 : Planifier

Commencer à tester les règles de la asr. implique de commencer avec la bonne unité commerciale. Vous souhaiterez commencer par un petit groupe de personnes dans une unité commerciale spécifique. Vous pouvez identifier certains champions de la RSA au sein d’une unité commerciale particulière qui peuvent fournir un impact réel sur les règles de la asr et vous aider à régler votre implémentation.

> [!div class="mx-imgBorder"]
> ![Étapes de planification des règles asr](images/asr-rules-planning-steps.png)

### <a name="start-with-the-right-business-unit"></a>Commencer avec la bonne unité commerciale

La façon dont vous sélectionnez l’unité d’entreprise pour déployer votre déploiement de règles de asr dépend de facteurs tels que :

- Taille de l’unité commerciale
- Disponibilité des champions de règles de la asr.  
- Distribution et utilisation des :
  - Logiciels
  - Dossiers partagés
  - Utilisation de scripts
  - Office macros
  - Autres entités affectées par les règles de la asr.

En fonction des besoins de votre entreprise, vous pouvez décider d’inclure plusieurs unités d’entreprise pour obtenir un large échantillonnage de logiciels, de dossiers partagés, de scripts, de macros, etc. À l’inverse, vous pouvez décider de limiter l’étendue de votre premier déploiement de règles asr à une seule unité commerciale, puis de répéter l’ensemble du processus de déploiement des règles de la asr dans vos autres unités d’entreprise, une par une.

### <a name="identify-asr--rules-champions"></a>Identifier les champions de règles de la asr.

Les champions des règles de RSA sont des membres de votre organisation qui vous aideront lors du déploiement initial des règles de la asr lors des phases préliminaires de test et d’implémentation. Vos champions sont généralement des employés qui sont plus techniquesment adap et qui ne sont pas déraillés par des pannes intermittentes de flux de travail. L’implication des champions se poursuit tout au long du développement plus large du déploiement des règles de la asr dans votre organisation. Vos champions de règles asr seront les premiers à découvrir chaque niveau du déploiement des règles de la asr.

Il est important de fournir un canal de commentaires et de réponse à vos champions de règles de asr pour vous avertir des interruptions de travail liées aux règles de la asr et recevoir les communications liées au déploiement des règles de la asr.

### <a name="get-inventory-of-line-of-business-apps-and-understand-the-business-unit-processes"></a>Obtenir l’inventaire des applications métier et comprendre les processus de l’unité métier

Il est essentiel de bien comprendre les applications et les processus par unité d’entreprise utilisés au sein de votre organisation pour réussir le déploiement des règles de la asr. En outre, il est impératif que vous compreniez la façon dont ces applications sont utilisées dans les différentes unités commerciales de votre organisation.
Pour commencer, vous devez obtenir un inventaire des applications approuvées pour être utilisées dans l’ensemble de l’organisation. Vous pouvez utiliser des outils tels que Microsoft 365 Apps centre d’administration pour vous aider à inventorier les applications logicielles. Voir : [Vue d’ensemble de l’inventaire dans Microsoft 365 Apps centre d’administration.](/deployoffice/admincenter/inventory)

### <a name="define-reporting-and-response-team--roles-and-responsibilities"></a>Définir les rôles et responsabilités de l’équipe de signalement et de réponse

Clairement l’articul des rôles et des responsabilités des personnes responsables de la surveillance et de la communication de l’état et de l’activité des règles de la asr. Par conséquent, il est important de déterminer :

- La personne ou l’équipe responsable de la collecte des rapports
- Comment et avec qui les rapports sont partagés
- Comment l’escalade est traitée pour les menaces nouvellement identifiées ou les blocages indésirables causés par les règles de la astéreur

Les rôles et responsabilités classiques sont les suivants :

- Administrateurs informatiques : implémentez des règles de asr, gérez les exclusions. Travailler avec différentes unités d’entreprise sur des applications et des processus. Assemblage et partage de rapports aux parties prenantes
- Analyste certifié du Centre d’opérations de sécurité (CSOC) : responsable de l’investissement de processus bloqués prioritaires, afin de déterminer si la menace est valide ou non
- Responsable de la sécurité des informations (CISO) : responsable de la sécurité globale et de l’état de santé de l’organisation

### <a name="ring-deployment"></a>Déploiement sonnerie

Pour les grandes entreprises, Microsoft recommande de déployer des règles asr dans des « anneaux ». Les anneaux sont des groupes d’appareils qui sont visuellement représentés sous forme de cercles concentriques qui s’imbriquent vers l’extérieur comme des anneaux d’arborescence qui ne se chevauchent pas. Lorsque l’anneau le plus au centre est correctement déployé, vous pouvez passer l’anneau suivant à la phase de test. Une évaluation approfondie de vos unités d’entreprise, de vos règles de RSA, de vos applications et de vos processus est impérative pour définir vos anneaux.
Dans la plupart des cas, votre organisation a conçu des anneaux de déploiement pour des déploiements par phases Windows mises à jour. Vous pouvez utiliser votre conception d’anneau existante pour implémenter des règles asr.
Voir : [Créer un plan de déploiement pour Windows](/windows/deployment/update/create-deployment-plan)

## <a name="phase-2-test"></a>Phase 2 : Test

Commencez le déploiement de vos règles de asr avec l’anneau 1.

> [!div class="mx-imgBorder"]
> ![Étapes de test des règles asr](images/asr-rules-testing-steps.png)

### <a name="step-1-test-asr-rules-using-audit"></a>Étape 1 : Tester les règles de la asr à l’aide de l’audit

Commencez la phase de test en 2013 en 2013, en 2013, en 2013, en 2013. En règle générale, il est recommandé d’activer toutes les règles (dans Audit) afin de pouvoir déterminer les règles déclenchées au cours de la phase de test. Notez que les règles définies sur Audit n’ont généralement pas d’impact sur les fonctionnalités de l’entité ou des entités à laquelle la règle est appliquée, mais génèrent des événements consignés pour l’évaluation ; n’a aucun effet sur les utilisateurs finaux.

#### <a name="configure-asr-rules-using-mem"></a>Configurer des règles asr à l’aide de MEM

Vous pouvez utiliser Microsoft Endpoint Manager de point de terminaison (MEM) pour configurer des règles asr personnalisées.

1. Ouvrir [Microsoft Endpoint Manager centre d’administration](https://endpoint.microsoft.com/#home)
2. Go to **Endpoint Security**  >  **Attack surface reduction**.
3. Sélectionner **Créer une stratégie**.
4. Dans **Plateforme,** **sélectionnez Windows 10 et ultérieures,** et dans **Profil,** sélectionnez Règles de réduction **de la surface d’attaque.**
  
    > [!div class="mx-imgBorder"]
    > ![Configurer le profil des règles de la asr.](images/asr-mem-create-profile.png)

5. Cliquez sur **Créer**.
6. Dans **l’onglet Basics** du volet Créer un profil, dans **Nom,** ajoutez un nom pour votre stratégie.  Dans **description,** ajoutez une description pour votre stratégie de règles de asr.
7. Dans **l’onglet Paramètres de configuration,** sous Règles de réduction de **la surface** d’attaque, définissez toutes les règles en **mode Audit.**

    > [!div class="mx-imgBorder"]
    > ![Définir des règles asr en mode Audit](images/asr-mem-configuration-settings.png)

    >[!Note]
    >Il existe des variantes dans certaines listes en mode de règles de récupération de l’attaque ; _Bloqués_ _et activés_ fournissent les mêmes fonctionnalités.

8. [Facultatif] Dans le volet **Balises** d’étendue, vous pouvez ajouter des informations de balise à des appareils spécifiques. Vous pouvez également utiliser des balises de contrôle d’accès et d’étendue basées sur les rôles pour vous assurer que les administrateurs qui ont les droits d’accès et de visibilité sur les objets Intune de droite. En savoir plus : Utilisez le contrôle d’accès basé sur un rôle [(RBAC)](/mem/intune/fundamentals/scope-tags)et les balises d’étendue pour le service it distribué dans Intune .
9. Dans le **volet Affectations,** vous pouvez déployer ou « affecter » le profil à vos groupes d’utilisateurs ou d’appareils. En savoir plus : [attribuer des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)
10. Examinez vos paramètres dans le **volet Révision +** Créer. Cliquez **sur Créer** pour appliquer les règles.

   > [!div class="mx-imgBorder"]
   > ![Activer la stratégie de règles asr](images/asr-mem-review-create.png)

Votre nouvelle stratégie de réduction de la surface d’attaque pour les règles de réduction de la surface d’attaque est répertoriée dans **endpoint security | Réduction de la surface d’attaque.**

   > [!div class="mx-imgBorder"]
   > ![Stratégie de règle ASR répertoriée](images/asr-mem-my-asr-rules.png)

### <a name="step-2-understand-the-attack-surface-reduction-rules-reporting-page-in-the-microsoft-365-defender-portal"></a>Étape 2 : Comprendre la page rapports des règles de réduction de la surface d’attaque dans le portail Microsoft 365 Defender attaque

La page de rapport des règles de réduction de la surface d’attaque se trouve **dans Microsoft 365 Defender portail signale** les règles de réduction de  >    >  **la surface d’attaque.** Cette page possède trois onglets :

- Detections
- Configuration
- Ajouter des exclusions

#### <a name="detections-tab"></a>Onglet Détections

Fournit une chronologie de 30 jours des événements d’audit et bloqués détectés.

> [!div class="mx-imgBorder"]
> ![Onglet Détections des règles de réduction de la surface d’attaque](images/asr-defender365-01.png)

Le volet Règles de réduction de la surface d’attaque fournit une vue d’ensemble des événements détectés par règle.

>[!Note]
>Il existe certaines variantes dans les rapports de règles de la asr. Microsoft est en train de mettre à jour le comportement des rapports de règles de la asr afin de fournir une expérience cohérente.

> [!div class="mx-imgBorder"]
> ![Détections de règles de réduction de la surface d’attaque](images/asr-defender365-01b.png)

Cliquez **sur Afficher les détections** pour ouvrir **l’onglet Détections.**

> [!div class="mx-imgBorder"]
> [![Détections des règles de réduction de la surface d’attaque ](images/asr-defender365-reports-detections.png) ](images/asr-defender365-reports-detections.png#lightbox)

Le **volet GroupBy** et **Filter** offre les options suivantes :

**GroupBy renvoie** l’ensemble des résultats aux groupes suivants :

- Aucun regroupement
- Fichier détecté
- Auditer ou bloquer
- Rule
- Application source
- Device
- Utilisateur
- Éditeur

> [!div class="mx-imgBorder"]
> [![Filtre GroupBy des règles de réduction de la surface d’attaque ](images/asr-defender365-reports-detections.png) ](images/asr-defender365-reports-detections.png#lightbox)

**Le** filtre ouvre la page **Filtrer sur les** règles, qui vous permet d’étenduer les résultats uniquement aux règles asr sélectionnées :

> [!div class="mx-imgBorder"]
> [![Filtre des règles de réduction de la surface d’attaque sur les règles ](images/asr-defender365-filter.png) ](images/asr-defender365-filter.png#lightbox)

>[!Note]
>Si vous avez une licence Microsoft Microsoft 365 Security E5 ou A5, Windows E5 ou A5, le lien suivant ouvre l’onglet [Réductions](https://security.microsoft.com/asr?viewid=detections) de la surface d’attaque de Microsoft Defender 365 > > détections.

#### <a name="configuration-tab"></a>Onglet Configuration

Répertorie, par ordinateur, l’état d’agrégation des règles de asr : Hors, Audit, Bloquer.

> [!div class="mx-imgBorder"]
> [![Onglet Configuration des règles de réduction de la surface d’attaque ](images/asr-defender365-configurations.png) ](images/asr-defender365-configurations.png#lightbox)

Sous l’onglet Configurations, vous pouvez vérifier, par appareil, quelles règles de récupération automatique sont activées et dans quel mode, en sélectionnant l’appareil pour lequel vous souhaitez passer en revue les règles de la asr.

> [!div class="mx-imgBorder"]
> [![Règles de réduction de la surface d’attaque activées et mode ](images/asr-defender365-configurations.settings.png) ](images/asr-defender365-configurations.settings.png#lightbox)

Le **lien De mise** en Microsoft Endpoint Manager ouvre le Centre d’administration Microsoft Endpoint Manager, où vous pouvez créer ou modifier une stratégie de protection de point de terminaison pour la asr.

> [!div class="mx-imgBorder"]
> [![Règles de réduction de la surface d’attaque dans MEM ](images/asr-defender365-05b-mem1.png) ](images/asr-defender365-05b-mem1.png#lightbox)

Dans endpoint security | Vue d’ensemble, **sélectionnez Réduction de la surface d’attaque**:

> [!div class="mx-imgBorder"]
> [![Réduction de la surface d’attaque dans mem ](images/asr-defender365-05b-mem2.png) ](images/asr-defender365-05b-mem2.png#lightbox)

Le point de terminaison sécurité | Le volet Réduction de la surface d’attaque s’ouvre :

> [!div class="mx-imgBorder"]
> [![Volet Asr de sécurité des points de terminaison ](images/asr-defender365-05b-mem3.png) ](images/asr-defender365-05b-mem3.png#lightbox)

>[!Note]
>Si vous avez une licence Microsoft Defender 365 E5 (ou Windows E5 ?), ce lien ouvre l’onglet [Configurations](https://security.microsoft.com/asr?viewid=configuration) des rapports Microsoft Defender 365 > réductions de la surface d’attaque >.

#### <a name="add-exclusions"></a>Ajouter des exclusions

Cet onglet fournit une méthode pour sélectionner les entités détectées (par exemple, les faux positifs) pour l’exclusion. Lorsque des exclusions sont ajoutées, le rapport fournit un résumé de l’impact attendu.

>[!Note]
> Antivirus Microsoft Defender exclusions av sont honorées par les règles de la asr.  Voir [Configurer et valider les exclusions en fonction de l’extension, du nom ou de l’emplacement.](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

> [!div class="mx-imgBorder"]
> [![Outil Asr de sécurité des points de terminaison ](Images/asr-defender365-06d.png) ](Images/asr-defender365-06d.png#lightbox)

> [!Note]
>Si vous avez une licence Microsoft Defender 365 E5 (ou Windows E5 ?), ce lien ouvre l’onglet Réductions [](https://security.microsoft.com/asr?viewid=exclusions) de la surface d’attaque de Microsoft Defender 36 > 5 > de la surface d’attaque.

### <a name="step-3-assess-impact"></a>Étape 3 : Évaluer l’impact

#### <a name="review"></a>Révision

Utilisez la page de création de rapports dans le portail Microsoft 365 Defender pour voir quelles règles de la ASR ont eu un impact sur le processus de l’unité d’entreprise, le cas besoin. Incluez les commentaires de vos champions de la RSA dans le cadre de ce processus. Examinez le rapport d’audit pour déterminer les règles qui ont le plus d’événements déclenchés/déclenchés et qui ont le moins d’événements.

Étant donné que les règles de réduction de la réduction des événements ciblent un large éventail de composants et que ces composants sont appelés à intervalles variables, il est difficile de prévoir le temps qu’il faudra pour obtenir un échantillonnage utile des événements déclenchés par des règles asr dans les anneaux de votre organisation ; Toutefois, Microsoft suggère un minimum de quatre semaines. Par exemple, certaines règles asr pour les applications Microsoft Office peuvent se déclencher plus rapidement et plus fréquemment que la règle de la asr à « Utiliser une protection avancée contre les ransomware ». De même, chaque anneau utilisera probablement des applications et d’autres composants soumis à des règles de asr différemment et avec une fréquence différente. Vous devez déterminer à quel moment le test est terminé en fonction des résultats dans votre organisation. Pour une meilleure compréhension, voir combien de temps dois-je tester une règle [asr en mode audit avant de l’activer ?](attack-surface-reduction-faq.yml#how-long-should-i-test-an-asr-rule-in-audit-mode-before-enabling-it-).

#### <a name="create-exclusions"></a>Créer des exclusions

Dans de nombreux cas, une organisation dispose de fichiers ou de dossiers de fichiers, par exemple connus comme étant sûrs, et qui peuvent contenir des aspects qui déclencheraient une règle de asr. le mode audit révélera ces fichiers et dossiers. Par exemple, votre organisation peut avoir une collection de documents Word ou Excel dont les macros sont activées à des fins spécifiques ; ces macros peuvent déclencher une règle de asr. Dans ce cas, si le mode audit identifie ces fichiers, vous souhaitez exclure ces fichiers ou dossiers afin d’empêcher qu’ils ne soient capturés par les règles de la asr. Voir [Exclure des fichiers et des dossiers](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules)

>[!Note]
>N’oubliez pas que Antivirus Microsoft Defender exclusions av sont honorées par les règles de la asr. Voir [Configurer et valider les exclusions en fonction de l’extension, du nom ou de l’emplacement.](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

Si vous déterminez qu’une règle a un impact négatif sur les opérations de l’entreprise, vous pouvez la laisser dans un audit afin de pouvoir continuer à capturer la règle ou la désactiver entièrement. Les exclusions sont facilement activées dans Microsoft 365 Defender règles **de** réduction de  >    >  **la surface d’attaque.** Sélectionnez simplement l’entité ou les entités pour lesquelles vous souhaitez créer une exclusion.

Les exclusions sont facilement activées dans Microsoft 365 Defender règles **de** réduction de  >    >  **la surface d’attaque.** Sélectionnez simplement l’entité ou les entités pour lesquelles vous souhaitez créer une exclusion.

> [!div class="mx-imgBorder"]
> [![AsR Create Exclusions ](images/asr-defender365-06d.png) ](images/asr-defender365-06d.png#lightbox)

#### <a name="create-exclusions-after-review"></a>Créer des exclusions après révision

Dans de nombreux cas, une organisation dispose de fichiers ou de dossiers de fichiers, par exemple connus comme étant sûrs, et qui peuvent contenir des aspects qui déclencheraient une règle de asr. le mode audit révélera ces fichiers et dossiers. Par exemple, votre organisation peut avoir une collection de documents Word ou Excel dont les macros sont activées à des fins spécifiques ; ces macros peuvent déclencher une règle de asr. Dans ce cas, si le mode audit identifie ces fichiers, vous souhaitez exclure ces fichiers ou dossiers afin d’empêcher qu’ils ne soient capturés par les règles de la asr. Voir [Exclure des fichiers et des dossiers.](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules)

>[!Note]
>N’oubliez pas que Antivirus Microsoft Defender exclusions av sont honorées par les règles de la asr. Voir [Configurer et valider les exclusions en fonction de l’extension, du nom ou de l’emplacement.](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

## <a name="phase-3-implement"></a>Phase 3 : Implémenter

La phase d’implémentation déplace l’anneau du test à l’état fonctionnel.

> [!div class="mx-imgBorder"]
> ![Étapes d’implémentation des règles asr](images/asr-rules-implementation-steps.png)

### <a name="step-1-transition-asr-rules-from-audit-to-block"></a>Étape 1 : Transition des règles de la asr à partir de l’audit vers le blocage

1. Une fois toutes les exclusions déterminées en mode audit, commencez à définir certaines règles asr en mode « bloquer », en commençant par la règle qui a le moins d’événements déclenchés. Voir « Activer [les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)».
2. Consultez la page de rapports dans le portail Microsoft 365 Defender' ; voir le rapport sur la protection contre les [menaces dans Microsoft Defender for Endpoint](threat-protection-reports.md). Examinez également les commentaires de vos champions de la asr.
3. Affinez les exclusions ou créez de nouvelles exclusions selon les besoins.
4. Revenir aux règles problématiques vers Audit.

  >[!Note]
  >Pour les règles problématiques (règles créant trop de bruit), il est préférable de créer des exclusions plutôt que de désactiver les règles ou de revenir à Audit. Vous devez déterminer ce qui est le mieux pour votre environnement.

  >[!Tip]
  >Lorsque ce paramètre est disponible, tirez parti du paramètre Du mode Avertissement dans les règles pour limiter les perturbations. L’activation des règles asr en mode Avertissement vous permet de capturer les événements déclenchés et d’afficher leurs perturbations potentielles, sans bloquer l’accès des utilisateurs finaux. En savoir plus : [mode d’avertissement pour les utilisateurs.](attack-surface-reduction.md#warn-mode-for-users)

#### <a name="how-does-warn-mode-work"></a>Comment fonctionne le mode Avertissement ?

Le mode Avertissement est en réalité une instruction bloquer, mais avec la possibilité pour l’utilisateur de « débloquer » les exécutions suivantes du flux ou de l’application donné. Le mode Avertissement se débloque sur une combinaison d’appareils, d’utilisateurs, de fichiers et de processus. Les informations du mode avertissement sont stockées localement et ont une durée de 24 heures.

### <a name="step-2-expand-deployment-to-ring-n--1"></a>Étape 2 : développer le déploiement pour sonner n + 1

Lorsque vous êtes certain d’avoir correctement configuré les règles asr pour l’anneau 1, vous pouvez élargir l’étendue de votre déploiement à l’anneau suivant (anneau n + 1).

Le processus de déploiement, étapes 1 à 3, est essentiellement le même pour chaque anneau suivant :

1. Règles de test dans Audit
2. Passer en revue les événements d’audit déclenchés par la asr dans le portail Microsoft 365 Defender
3. Créer des exclusions
4. Révision : affiner, ajouter ou supprimer des exclusions si nécessaire
5. Définir des règles sur « bloquer »
6. Examinez la page de rapports dans le portail Microsoft 365 Defender web.
7. Créez des exclusions.
8. Désactivez les règles problématiques ou revenir à Audit.

## <a name="phase-4-operationalize"></a>Phase 4 : Operationalize

Une fois que vous avez déployé entièrement les règles asr dans votre organisation, il est essentiel que votre organisation dispose de processus pour surveiller et répondre aux activités liées à la asr.

### <a name="manage-false-positives"></a>Gérer les faux positifs

Les faux positifs/négatifs peuvent se produire avec n’importe quelle solution de protection contre les menaces, y compris Microsoft Defender pour point de terminaison. Dans les solutions de protection des points de terminaison, les faux positifs sont des cas dans lesquels une entité (telle qu’un fichier ou un processus) est détectée et identifiée comme malveillante, bien que l’entité ne soit pas réellement une menace. En revanche, un faux négatif est une entité qui n’a pas été détectée comme une menace, mais qui est en fait malveillante.
Pour plus d’informations sur la présence de faux positifs et de faux négatifs, voir : Traiter les [faux positifs/négatifs dans Microsoft Defender pour endpoint](defender-endpoint-false-positives-negatives.md)

### <a name="keeping-up-with-reports"></a>Suivi des rapports

Un examen cohérent et régulier des rapports est un aspect essentiel de la maintenance du déploiement de vos règles de asr et de la conservation des nouvelles menaces émergentes. Votre organisation doit avoir programmé des révisions des événements de règles de la asr à une cadence qui restera à jour avec les événements signalés par les règles de la asr. Selon la taille de votre organisation, cette surveillance peut être quotidienne, horaire ou continue.

### <a name="hunting"></a>Repérage

L’une des fonctionnalités les plus puissantes et les plus Microsoft 365 Defender [est](https://securitycenter.microsoft.com) la recherche avancée. Si vous n’êtes pas familiarisé avec le chasse avancée, reportez-vous à la documentation : recherchez de manière proactive les menaces [avec le chasse avancée.](/windows/security/threat-protection/microsoft-defender-atp/advanced-hunting-overview)

> [!div class="mx-imgBorder"]
> [![Microsoft 365 Defender de recherche avancée ](images/asr-defender365-advanced-hunting2.png) ](images/asr-defender365-advanced-hunting2.png#lightbox)

Le repérage avancé est un outil de repérage de menaces basé sur une requête (Kusto Query Language) qui vous permet d’explorer jusqu’à 30 jours des données capturées (brutes) collectées par Microsoft Defender ATP Endpoint Detection and Response (PEPT) à partir de tous vos ordinateurs. Grâce au chasse avancée, vous pouvez inspecter de manière proactive les événements afin de localiser des indicateurs et des entités intéressants. L’accès flexible aux données facilite le repérage sans contrainte pour les menaces connues et potentielles.

Grâce à la recherche avancée, il est possible d’extraire des informations sur les règles de la asr, de créer des rapports et d’obtenir des informations détaillées sur le contexte d’un événement d’audit ou de blocage de règle asr donné.

Vous pouvez interroger les événements de règles asr à partir de la table DeviceEvents dans la section de recherche avancée du portail Microsoft 365 Defender. Par exemple, une requête simple, telle que celle ci-dessous, peut signaler tous les événements qui ont des règles de asr en tant que source de données, au cours des 30 derniers jours, et les synthétisera par le nombre ActionType, qui dans ce cas sera le nom de code réel de la règle asr.

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender ligne de commande de requête de recherche avancée](images/asr-defender365-advanced-hunting3.png)

> [!div class="mx-imgBorder"]
> [![Microsoft 365 Defender de requête de recherche avancée ](images/asr-defender365-advanced-hunting4.png) ](images/asr-defender365-advanced-hunting4.png#lightbox)

L’exemple ci-dessus indique que 187 événements ont été enregistrés pour AsrLsassCredentialTheft (102 pour Bloqué et 85 pour Audité), 2 événements pour AsrOfficeChildProcess (1 pour Audité et 1 pour Block) et 8 pour AsrPsexecWmiChildProcessAudited.

Si vous souhaitez vous concentrer sur la règle AsrOfficeChildProcess et obtenir des détails sur les fichiers et processus impliqués, modifiez le filtre pour ActionType et remplacez la ligne de synthèse par une projection des champs souhaités (dans ce cas, il s’agit de DeviceName, FileName, FolderPath, etc.).

> [!div class="mx-imgBorder"]
> ![Microsoft 365 Defender requête de recherche avancée axée sur](images/asr-defender365-advanced-hunting4b.png)

> [!div class="mx-imgBorder"]
> [![Microsoft 365 Defender résultats de requête de recherche avancée ](images/asr-defender365-advanced-hunting5b.png) ](images/asr-defender365-advanced-hunting5b.png#lightbox)

Le véritable avantage du repérage avancé est que vous pouvez mettre en forme les requêtes à votre convenance, de sorte que vous pouvez voir l’article exact de ce qui se passe, que vous vouliez identifier quelque chose sur un ordinateur individuel ou que vous vouliez extraire des informations de l’ensemble de votre environnement.

Pour plus d’informations sur les options de recherche supplémentaires, voir [Démystification](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)des règles de réduction de la surface d’attaque - Partie 3 .

## <a name="reference"></a>Référence

### <a name="blogs"></a>Blogs

[Démystification des règles de réduction de la surface d’attaque - Partie 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Démystification des règles de réduction de la surface d’attaque - Partie 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Démystification des règles de réduction de la surface d’attaque - Partie 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Démystification des règles de réduction de la surface d’attaque - Partie 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-collection"></a>Collection ASR

[Vue d’ensemble de la réduction de la surface d'attaque](overview-attack-surface-reduction.md)

[Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants](attack-surface-reduction.md)

[Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)

[Règles de réduction de la surface d’attaque](attack-surface-reduction-rules.md)

[FAQ sur la réduction de la surface d’attaque](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

[Protection par le cloud et antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[Activer la protection cloud dans Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

[Configurer et valider des exclusions en fonction de l’extension, du nom ou de l’emplacement](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[Antivirus Microsoft Defender prise en charge de la plateforme d’Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)

[Vue d’ensemble de l’inventaire dans Microsoft 365 Apps’administration centrale](/deployoffice/admincenter/inventory)

[Créer un plan de déploiement pour Windows](/windows/deployment/update/create-deployment-plan)

[Utiliser un contrôle d’accès basé sur un rôle (RBAC) et des balises d’étendue pour le service it distribué dans Intune](/mem/intune/fundamentals/scope-tags)

[Attribuer des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Sites de gestion

[Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)

[Réduction de la surface d’attaque](https://security.microsoft.com/asr?viewid=detections)

[Configurations des règles asr](https://security.microsoft.com/asr?viewid=configuration)

[Exclusions de règles asr](https://security.microsoft.com/asr?viewid=exclusions)
