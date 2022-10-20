---
title: Vue d’ensemble du déploiement des règles de réduction de la surface d’attaque (ASR) Microsoft Defender pour point de terminaison (MDE)
description: Fournit une vue d’ensemble et des instructions préalables sur le déploiement de règles de réduction de la surface d’attaque (ASR) Microsoft Defender pour point de terminaison (MDE). Liens vers des rubriques qui montrent comment planifier et déployer ASR, tester des règles ASR, configurer des règles ASR et activer des règles ASR.
keywords: Microsoft Defender pour point de terminaison (MDE) règles de réduction de la surface d’attaque, règles ASR intune, règles ASR defender, Windows 10 règles ASR, règles asr defender, rapport de règles ASR, déploiement de règles de réduction de la surface d’attaque Microsoft, observateur d’événements de règles ASR, activer les règles asr, configurer ASR, système de prévention des intrusions de l’hôte, règles de protection, règles anti-exploitation,  anti-exploitation, règles d’exploitation, règles de prévention des infections, Microsoft Defender pour point de terminaison, configurer des règles ASR
search.product: eADQiWindows 10XVcnh
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.service: microsoft-365-security
ms.subservice: mde
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.topic: conceptual
ms.collection:
- m365-security
- m365solution-asr-rules
- highpri
- tier1
ms.date: 09/18/2022
search.appverid: met150
ms.openlocfilehash: 4506ef953ba543ed5f45046cffc1fcfad49077e4
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68630641"
---
# <a name="attack-surface-reduction-asr-rules-deployment-overview"></a>Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)

Les surfaces d’attaque sont tous les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’attaquer. La configuration des règles de réduction de la surface d’attaque (ASR) Microsoft Defender pour point de terminaison (MDE) peut vous aider.

Les règles ASR ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts masqués ou suspects
- Comportements que les applications ne se produisent généralement pas pendant le travail quotidien normal

En réduisant les différentes surfaces d’attaque, vous pouvez empêcher les attaques de se produire en premier lieu.

Cette collection de déploiement fournit des informations sur les aspects suivants des règles ASR MDE :

- Exigences en matière de règles ASR
- planifier le déploiement de règles ASR
- tester les règles ASR
- configurer et activer des règles asr
- Meilleures pratiques en matière de réduction de la surface d’attaque
- Repérage avancé des règles ASR
- Visionneuse d’événements des règles ASR

## <a name="asr-rules-deployment-steps"></a>Étapes de déploiement des règles ASR

Comme pour toute nouvelle implémentation à grande échelle susceptible d’avoir un impact sur vos opérations métier, il est important d’être méthodique dans votre planification et votre implémentation. En raison des puissantes fonctionnalités des règles ASR pour empêcher les programmes malveillants, une planification et un déploiement prudents de ces règles sont nécessaires pour s’assurer qu’elles fonctionnent le mieux pour vos workflows clients uniques. Pour travailler dans votre environnement, vous devez planifier, tester, implémenter et mettre en œuvre les règles ASR avec soin.  

> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="Planifiez les règles de réduction de la surface d’attaque (ASR) Microsoft Defender pour point de terminaison (MDE), testez les règles MDE ASR, activez les règles MDE ASR, conservez les règles ASR." lightbox="images/asr-rules-deployment-phases.png":::

## <a name="important-pre-deployment-caveat"></a>Mise en garde préalable au déploiement importante

Pendant le processus de planification, d’audit et d’activation des règles ASR, il est recommandé d’activer les trois _règles de protection standard suivantes_. Consultez [les règles de réduction de la surface](attack-surface-reduction-rules-reference.md#attack-surface-reduction-rules-by-type) d’attaque par type pour obtenir des détails importants sur les deux types de règles ASR.

- [Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)](attack-surface-reduction-rules-reference.md#block-credential-stealing-from-the-windows-local-security-authority-subsystem)
- [Bloquer l’abus de pilotes signés vulnérables exploités](attack-surface-reduction-rules-reference.md#block-abuse-of-exploited-vulnerable-signed-drivers)
- [Bloquer la persistance via l’abonnement aux événements WMI (Windows Management Instrumentation)](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription)

En règle générale, vous pouvez activer les règles de protection standard avec un impact minimal à aucun notable pour l’utilisateur final. Pour obtenir une méthode simple permettant d’activer les règles de protection standard, consultez : [Option de protection standard simplifiée](attack-surface-reduction-rules-report.md#simplified-standard-protection-option)

> [!NOTE]
> Pour les clients qui utilisent un hips non Microsoft et qui passent à Microsoft Defender pour point de terminaison règles de réduction de la surface d’attaque : Microsoft conseille aux clients d’exécuter leur solution HIPS côte à côte avec leur déploiement de règles ASR jusqu’au moment où vous passez du mode Audit au mode Bloquer. Gardez à l’esprit que vous devez contacter votre fournisseur d’antivirus tiers pour obtenir des recommandations d’exclusion.  

## <a name="before-you-begin-testing-or-enabling-asr-rules"></a>Avant de commencer à tester ou à activer des règles ASR

Lors de votre préparation initiale, il est essentiel de comprendre les fonctionnalités des systèmes que vous allez mettre en place. Comprendre les fonctionnalités vous aidera à déterminer les règles ASR les plus importantes pour protéger votre organisation. En outre, vous devez vous occuper de plusieurs prérequis pour préparer votre déploiement ASR.

> [!IMPORTANT]
> Ce guide fournit des images et des exemples pour vous aider à décider comment configurer des règles ASR ; ces images et exemples peuvent ne pas refléter les meilleures options de configuration pour votre environnement.

Avant de commencer, passez [en revue la vue d’ensemble de la réduction de la surface d’attaque](overview-attack-surface-reduction.md) et [la démystification des règles de réduction de la surface d’attaque - Partie 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) pour obtenir des informations de base. Pour comprendre les domaines de couverture et d’impact potentiel, familiarisez-vous avec l’ensemble actuel de règles ASR; consultez la [référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md).  Pendant que vous vous familiarisez avec l’ensemble de règles ASR, prenez note des mappages GUID par règle ; voir : [règle ASR à matrice GUID](attack-surface-reduction-rules-reference.md#asr-rule-to-guid-matrix).

Les règles ASR ne sont qu’une des fonctionnalités de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison. Ce document décrit plus en détail le déploiement efficace de règles ASR pour arrêter les menaces avancées telles que les ransomwares gérés par l’homme et d’autres menaces.  

### <a name="asr-rules-list-by-category"></a>Liste de règles ASR par catégorie

Comme indiqué dans [Utiliser les règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants](attack-surface-reduction.md), il existe plusieurs règles de réduction de la surface d’attaque dans MDE que vous pouvez activer pour protéger votre organisation. Voici les règles réparties par catégorie :

<br/>

| Menaces polymorphes | Déplacement latéral & vol d’informations d’identification | Règles des applications de productivité |  règles de Email | Règles de script | Règles d’erreur |
|:---|:---|:---|:---|:---|:---|
| Empêcher l’exécution des fichiers exécutables, sauf s’ils répondent à une prévalence (1 000 machines), à un âge (24 heures) ou à des critères de liste approuvée | Bloquer les créations de processus provenant des commandes PSExec et WMI | Empêcher les applications Office de créer du contenu exécutable | Bloquer le contenu exécutable à partir du client de messagerie et de la messagerie web | Bloquer le code JS/VBS/PS/macro obfusqué | Bloquer l’abus de pilotes signés vulnérables exploités <sup>[[1](#fn1)]<sup></sup>  |
| Bloquer les processus non approuvés et non signés qui s’exécutent à partir d’USB | Bloquer le vol d’informations d’identification à partir du sous-système d’autorité de sécurité locale Windows (lsass.exe)<sup>[[2](#fn1)]<sup></sup>   | Empêcher les applications Office de créer des processus enfants |  Empêcher uniquement les applications de communication Office de créer des processus enfants | Empêcher JS/VBS de lancer le contenu exécutable téléchargé | |
| Utiliser une protection avancée contre les ransomware | Bloquer la persistance via l’abonnement aux événements WMI | Empêcher les applications Office d’injecter du code dans d’autres processus | Empêcher les applications de communication Office de créer des processus enfants | | |
| | | Empêcher Adobe Reader de créer des processus enfants | | | |

(<a id="fn1">1</a>) _L’abus de blocage des pilotes signés vulnérables exploités_ n’est actuellement pas disponible dans la sécurité des points de terminaison MEM. Vous pouvez configurer cette règle à l’aide de [MEM OMA-URI](enable-attack-surface-reduction.md#mem).

(<a id="fn1">2</a>) Certaines règles ASR génèrent un bruit considérable, mais ne bloquent pas les fonctionnalités. Par exemple, si vous mettez à jour Chrome ; Chrome accède à lsass.exe ; les mots de passe sont stockés dans lsass sur l’appareil. Toutefois, Chrome ne doit pas accéder à l’appareil local lsass.exe. Si vous activez la règle pour bloquer l’accès à lsass, elle génère un grand nombre d’événements. Ces événements sont de bons événements, car le processus de mise à jour logicielle ne doit pas accéder à lsass.exe. L’activation de cette règle empêche les mises à jour Chrome d’accéder à lsass, mais ne bloque pas la mise à jour de Chrome ; cela est également vrai pour les autres applications qui effectuent des appels inutiles à lsass.exe. _L’accès bloqué à la règle lsass_ bloque les appels inutiles à lsass, mais ne bloque pas l’exécution de l’application.

### <a name="asr-infrastructure-requirements"></a>Configuration requise pour l’infrastructure ASR

Bien que plusieurs méthodes d’implémentation des règles ASR soient possibles, ce guide est basé sur une infrastructure composée des éléments suivants :

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- appareils Windows 10 et Windows 11
- licences Microsoft Defender pour point de terminaison E5 ou Windows E5

Pour tirer pleinement parti des règles ASR et des rapports, nous vous recommandons d’utiliser une licence Microsoft 365 Defender E5 ou Windows E5 et A5. En savoir plus : [Configuration minimale requise pour Microsoft Defender pour point de terminaison](minimum-requirements.md).

>[!Note]
>Il existe plusieurs méthodes pour configurer des règles ASR. Les règles ASR peuvent être configurées à l’aide de : Microsoft Endpoint Manager (MEM), PowerShell, stratégie de groupe, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Si vous utilisez une configuration d’infrastructure différente de celle répertoriée pour _les exigences d’infrastructure_ (ci-dessus), vous pouvez en savoir plus sur le déploiement de règles de réduction de la surface d’attaque à l’aide d’autres configurations ici : [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>Dépendances des règles ASR

Microsoft Defender Antivirus doit être activé et configuré en tant que solution antivirus principale, et doit être en mode suivant :

- Solution antivirus/anti-programme malveillant principale  
- État : mode actif

Microsoft Defender Antivirus ne doit pas se trouver dans l’un des modes suivants :

- Passif
- Mode passif avec détection et réponse de point de terminaison (EDR) en mode bloc
- Analyse périodique limitée (LPS)
- Désactivé

Voir : [Protection fournie par le cloud et antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled-to-enable-asr-rules"></a>La protection cloud (MAPS) doit être activée pour activer les règles ASR

Microsoft Defender Antivirus fonctionne en toute transparence avec les services cloud Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard, offrant sans doute la meilleure défense antivirus. La protection cloud est essentielle pour empêcher les violations des programmes malveillants et un composant critique des règles ASR.
[Activez la protection fournie par le cloud dans Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions-for-asr-rules"></a>Microsoft Defender composants antivirus doivent être des versions actuelles pour les règles ASR

Les versions suivantes Microsoft Defender composant Antivirus ne doivent pas être plus de deux versions antérieures à la version la plus disponible :

- **Microsoft Defender version de mise à jour de la plateforme antivirus** : Microsoft Defender plateforme antivirus est mise à jour tous les mois.
- **Microsoft Defender version du moteur antivirus** : Microsoft Defender moteur antivirus est mis à jour tous les mois.
- **Microsoft Defender le renseignement de sécurité antivirus** : Microsoft met continuellement à jour Microsoft Defender renseignement de sécurité (également appelés « informations de définition et de signature ») pour traiter les menaces les plus récentes et affiner la logique de détection.

Maintenir Microsoft Defender versions antivirus à jour permet de réduire les résultats faux positifs des règles ASR et d’améliorer Microsoft Defender fonctionnalités de détection antivirus. Pour plus d’informations sur les versions actuelles et la mise à jour des différents composants antivirus Microsoft Defender, consultez Microsoft Defender prise en [charge de la plateforme Antivirus](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>Caveat

Certaines règles ne fonctionnent pas correctement si les scripts et les applications non signés et développés en interne sont en forte utilisation. Il est plus difficile de déployer des règles ASR si la signature de code n’est pas appliquée.

## <a name="additional-topics-in-this-deployment-collection"></a>Rubriques supplémentaires dans cette collection de déploiement

[Tester des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-test.md)

[Activer des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-implement.md)

[Utiliser des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-deployment-operationalize.md)

[Référence des règles de réduction de la surface d’attaque (ASR)](attack-surface-reduction-rules-reference.md)

## <a name="reference"></a>Référence

### <a name="blogs"></a>Blogs

[Démystifier les règles de réduction de la surface d’attaque - Partie 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420)

[Démystifier les règles de réduction de la surface d’attaque - Partie 2](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-2/ba-p/1326565)

[Démystifier les règles de réduction de la surface d’attaque - Partie 3](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-3/ba-p/1360968)

[Démystifier les règles de réduction de la surface d’attaque - Partie 4](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-4/ba-p/1384425)

### <a name="asr-rules-collection"></a>Collection de règles ASR

[Vue d’ensemble de la réduction de la surface d'attaque](overview-attack-surface-reduction.md)

[Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants](attack-surface-reduction.md)

[Activer les règles de réduction de la surface d’attaque - autres configurations](enable-attack-surface-reduction.md)

[Référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)

[FAQ sur la réduction de la surface d’attaque](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

[Protection par le cloud et antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[Activer la protection fournie par le cloud dans Microsoft Defender Antivirus](enable-cloud-protection-microsoft-defender-antivirus.md)

[Configurer et valider des exclusions en fonction de l’extension, du nom ou de l’emplacement](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

[prise en charge de la plateforme Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md)

[Vue d’ensemble de l’inventaire dans le centre d’administration Microsoft 365 Apps](/deployoffice/admincenter/inventory)

[Créer un plan de déploiement pour Windows](/windows/deployment/update/create-deployment-plan)

[Utiliser le contrôle d’accès en fonction du rôle (RBAC) et les balises d’étendue pour le service informatique distribué dans Intune](/mem/intune/fundamentals/scope-tags)

[Attribuer des profils d’appareil dans Microsoft Intune](/mem/intune/configuration/device-profile-assign#exclude-groups-from-a-profile-assignment)

### <a name="management-sites"></a>Sites de gestion

[Centre d’administration Microsoft Endpoint Manager](https://endpoint.microsoft.com/#home)

[Réduction de la surface d’attaque](https://security.microsoft.com/asr?viewid=detections)

[Configurations des règles ASR](https://security.microsoft.com/asr?viewid=configuration)

[Exclusions de règles ASR](https://security.microsoft.com/asr?viewid=exclusions)
