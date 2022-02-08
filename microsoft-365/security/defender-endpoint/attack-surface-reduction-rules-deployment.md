---
title: Conditions préalables au déploiement des règles asr
description: Fournit une vue d’ensemble et des instructions préalables sur le déploiement de règles de réduction de la surface d’attaque (ASR).
keywords: 'Déploiement des règles de réduction de la surface d’attaque, déploiement de la réduction de la surface d’attaque, activer les règles d’attaque, configurer la réduction de la surface d’attaque, système de prévention des intrusions hôte, règles de protection, règles anti-attaque, règles d’attaque, règles de prévention des infections, Microsoft Defender pour le point de terminaison, configurer des règles de réduction de la surface d’attaque'
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: 'oogunrinde, sugamar'
manager: dansimp
ms.custom: asr
ms.technology: mde
ms.topic: article
ms.collection: m365solution-scenario
ms.date: 1/18/2022
---

# <a name="asr-rules-deployment-prerequisites"></a>Conditions préalables au déploiement des règles asr

## <a name="before-you-begin"></a>Avant de commencer

Les surfaces d’attaque sont tous les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Les surfaces d’attaque de votre organisation incluent tous les endroits où un attaquant peut compromettre les appareils ou réseaux de votre organisation. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’attaque. La configuration des règles de réduction de la surface d’attaque (ASR), l’une des nombreuses fonctionnalités de sécurité de Microsoft Defender for Endpoint, peut vous aider.

Les règles asr ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts obscurcis ou suspects
- Comportements que les applications n’ont généralement pas pendant le travail quotidien normal

En réduisant les différentes surfaces d’attaque, vous pouvez empêcher les attaques de se produire en premier lieu.

Lors de votre préparation initiale, il est essentiel de comprendre les fonctionnalités des systèmes que vous allez mettre en place. Comprendre les fonctionnalités vous aidera à déterminer les règles de la asr qui sont les plus importantes pour la protection de votre organisation. En outre, vous devez respecter plusieurs conditions préalables lors de la préparation de votre déploiement de la asr.

>[!IMPORTANT]
>Ce guide fournit des images et des exemples pour vous aider à décider comment configurer les règles de la asr. Ces images et exemples peuvent ne pas refléter les meilleures options de configuration pour votre environnement.

Avant de commencer, examinez La vue d’ensemble de la réduction de [la surface](overview-attack-surface-reduction.md) d’attaque et la [démystification](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) des règles de réduction de la surface d’attaque - Partie 1 pour obtenir des informations de base. Pour comprendre les domaines de couverture et l’impact potentiel, familiarisez-vous avec l’ensemble actuel de règles asr. voir [la référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md).

Les règles de réduction de la surface d’attaque ne sont qu’une fonctionnalité des fonctionnalités de réduction de la surface d’attaque dans Microsoft Defender for Endpoint. Ce document détaille le déploiement efficace des règles de la asr pour arrêter les menaces avancées telles que les ransomware gérés par l’homme et d’autres menaces.  

### <a name="rules-by-category"></a>Règles par catégorie

Comme indiqué dans utiliser les règles de réduction de [la surface](attack-surface-reduction.md) d’attaque pour empêcher l’infection par des programmes malveillants, il existe plusieurs règles de réduction de la surface d’attaque dans MDE que vous pouvez activer pour protéger votre organisation. Voici les règles décomposées par catégorie :

<br/>

| Menaces polymorphes | Mouvement latéral lors & vol d’informations d’identification | Règles des applications de productivité |  Règles de messagerie | Règles de script | Règles de non-respect des règles |
|:---|:---|:---|:---|:---|:---|
| Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à une prévalence (1 000 ordinateurs), à l’âge (24 heures) ou à des critères de listes fiables | Bloquer les créations de processus provenant de commandes PSExec et WMI | Empêcher Office applications de créer du contenu exécutable | Bloquer le contenu exécutable du client de messagerie et de la messagerie web | Bloquer le code JS/VBS/PS/macro obscurci | Bloquer l’utilisation abusive des pilotes signés vulnérables exploités <sup>[[1](#fn1)]<sup></sup>  |
| Bloquer les processus non signés et non signés qui s’exécutent à partir du port USB | Bloquer le vol d’informations d Windows du sous-système de l’autorité de sécurité locale (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Empêcher Office applications de créer des processus enfants |  Empêcher uniquement les applications Office communication de créer des processus enfants | Empêcher JS/VBS de lancer du contenu exécutable téléchargé | |
| Utiliser la protection avancée contre les ransomware | Bloquer la persistance via un abonnement à des événements WMI | Empêcher Office applications d’injecter du code dans d’autres processus | Empêcher Office applications de communication de créer des processus enfants | | |
| | | Empêcher Adobe Reader de créer des processus enfants | | | |

(<a id="fn1">1</a>) Bloquer l’utilisation abusive des pilotes _signés vulnérables exploités_ n’est pas disponible actuellement dans la sécurité des points de terminaison MEM. Vous pouvez configurer cette règle à l’aide [de l’OMA-URI MEM](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Certaines règles de réduction de la réduction du bruit génèrent un bruit considérable, mais ne bloquent pas les fonctionnalités. Par exemple, si vous êtes en train de mettre à jour Chrome ; Chrome accède à lsass.exe ; les mots de passe sont stockés dans lsass sur l’appareil. Toutefois, Chrome ne doit pas accéder aux appareils lsass.exe. Si vous activez la règle pour bloquer l’accès au lsass, elle génère un grand nombre d’événements. Ces événements sont de bons événements, car le processus de mise à jour logicielle ne doit pas lsass.exe. L’activation de cette règle empêchera les mises à jour Chrome d’accéder à l’application lsass, mais ne bloquera pas la mise à jour de Chrome ; Cela est également vrai pour les autres applications qui appellent inutilement des lsass.exe. La _règle de blocage d’accès à lsass_ bloque les appels inutiles à l’application, mais ne bloque pas l’exécution de l’application.

### <a name="infrastructure-requirements"></a>Conditions requises en matière d’infrastructure

Bien qu’il soit possible d’implémenter plusieurs méthodes d’implémentation des règles de la asr, ce guide est basé sur une infrastructure composée des points ci-après :

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- Windows 10 et Windows 11 périphériques
- Microsoft Defender pour le point de terminaison E5 ou Windows licences E5

Pour tirer pleinement parti des règles et des rapports de la asrx Microsoft 365 Defender, nous vous recommandons d’utiliser une licence E5 Windows E5 et A5. En savoir plus : [Conditions minimales requises pour Microsoft Defender pour le point de terminaison](minimum-requirements.md).

>[!Note]
>Il existe plusieurs méthodes pour configurer les règles de la asr. Les règles asr peuvent être configurées à l’aide de : Microsoft Endpoint Manager (MEM), PowerShell, stratégie de groupe, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Si vous utilisez une configuration d’infrastructure différente de celle répertoriée pour les conditions requises pour l’infrastructure _(_ ci-dessus), vous pouvez en savoir plus sur le déploiement de règles de réduction de la surface d’attaque à l’aide d’autres configurations ici : Activer les règles de réduction de la [surface](enable-attack-surface-reduction.md) d’attaque.  

### <a name="asr-rules-dependencies"></a>Dépendances des règles asr

Antivirus Microsoft Defender doit être activée et configurée en tant que solution antivirus principale et doit être en mode suivant :

- Solution antivirus/anti-programme malveillant principale  
- État : mode actif

Antivirus Microsoft Defender ne doit pas être dans l’un des modes suivants :

- Passive
- Mode passif avec détection et réponse des points de terminaison (PEPT) en mode blocage
- Analyse périodique limitée (LPS)
- Désactivé

Voir : [Protection et](cloud-protection-microsoft-defender-antivirus.md) protection cloud Antivirus Microsoft Defender.

### <a name="cloud-protection-maps-must-be-enabled"></a>La protection cloud (MAPS) doit être activée

Antivirus Microsoft Defender fonctionne en toute transparence avec les services cloud de Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard, fournissant sans doute la meilleure protection antivirus. La protection cloud est essentielle pour empêcher les violations de programmes malveillants et constitue un composant essentiel des règles de la asr.
[Activer la protection cloud dans Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Antivirus Microsoft Defender composants doivent être des versions actuelles

Les versions de Antivirus Microsoft Defender suivantes ne doivent pas être plus anciennes que la version la plus disponible :

- **Antivirus Microsoft Defender version de mise à jour de la** plateforme : Antivirus Microsoft Defender plateforme est mise à jour tous les mois.
- **Antivirus Microsoft Defender version du moteur** : le moteur Antivirus Microsoft Defender est mis à jour tous les mois.
- **Antivirus Microsoft Defender** la sécurité : Microsoft met continuellement à jour l’intelligence de sécurité Microsoft Defender (également appelée, définition et signature) pour répondre aux dernières menaces et affiner la logique de détection.

Le fait Antivirus Microsoft Defender versions actuelles permet de réduire les règles de réduction de la réduction des résultats faux positifs et Antivirus Microsoft Defender fonctionnalités de détection. Pour plus d’informations sur les versions actuelles et la mise à jour des différents composants de Antivirus Microsoft Defender, consultez la [Antivirus Microsoft Defender prise en charge de la plateforme](manage-updates-baselines-microsoft-defender-antivirus.md).

## <a name="asr-rules-deployment-steps"></a>Étapes de déploiement des règles asr

Comme avec toute nouvelle implémentation à grande échelle susceptible d’avoir un impact sur vos opérations métier, il est important d’être méthodique dans la planification et l’implémentation. En raison des fonctionnalités puissantes des règles de protection contre les programmes malveillants dans la prévention des programmes malveillants, une planification et un déploiement attentifs de ces règles sont nécessaires pour s’assurer qu’elles fonctionnent au mieux pour vos flux de travail client uniques. Pour travailler dans votre environnement, vous devez planifier, tester, implémenter et mettre en œuvre les règles de la asr avec soin.  

> [!div class="mx-imgBorder"]
> ![Phases de déploiement des règles asr](images/asr-rules-deployment-phases.png)

>[!Note]
>Pour les clients qui utilisent un système HIPS non Microsoft et qui sont en transition vers microsoft Defender pour les règles de réduction de la surface d’attaque du point de terminaison : Microsoft recommande aux clients d’exécuter leur solution HIPS côte à côte avec leur déploiement de règles de réduction de la surface d’attaque jusqu’au moment où vous basculez du mode Audit au mode Blocage. N’oubliez pas que vous devez joindre votre fournisseur d’antivirus tiers pour obtenir des recommandations d’exclusion.  

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiements

[Phase 1 : Planifier](attack-surface-reduction-rules-deployment-plan.md)

[Phase 2 : Tester](attack-surface-reduction-rules-deployment-test.md)

[Phase 3 : Implémenter](attack-surface-reduction-rules-deployment-implement.md)

[Phase 4 : Opérationnaliser](attack-surface-reduction-rules-deployment-operationalize.md)

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

[Référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)

[FAQ sur la réduction de la surface d’attaque](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

[Protection par le cloud et antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[Activer la protection cloud dans Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

[Configurer et valider des exclusions en fonction de l’extension, du nom ou de l’emplacement](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[Antivirus Microsoft Defender prise en charge de la plateforme](manage-updates-baselines-microsoft-defender-antivirus.md)

[Vue d’ensemble de l’inventaire dans Microsoft 365 Apps’administration centrale](/deployoffice/admincenter/inventory)

[Créer un plan de déploiement pour Windows](/windows/deployment/update/create-deployment-plan)

[Utiliser un contrôle d’accès basé sur un rôle (RBAC) et des balises d’étendue pour le service it distribué dans Intune](/mem/intune/fundamentals/scope-tags)

[Attribuer des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Sites de gestion

[Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)

[Réduction de la surface d’attaque](https://security.microsoft.com/asr?viewid=detections)

[Configurations des règles asr](https://security.microsoft.com/asr?viewid=configuration)

[Exclusions de règles asr](https://security.microsoft.com/asr?viewid=exclusions)
