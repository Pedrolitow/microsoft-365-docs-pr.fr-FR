---
title: Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)
description: Fournit une vue d’ensemble et des instructions préalables sur le déploiement de règles de réduction de la surface d’attaque (ASR).
keywords: Déploiement de règles de réduction de la surface d’attaque, déploiement ASR, activer des règles asr, configurer asr, système de prévention des intrusions de l’hôte, règles de protection, règles de lutte contre l’exploitation, règles d’exploitation, règles de prévention des infections, Pertahanan Microsoft untuk Titik Akhir, configurer des règles ASR
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: mde
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom: asr
ms.topic: article
ms.collection:
- M365-security-compliance
- m365solution-asr-rules
- highpri
ms.date: 1/18/2022
search.appverid: met150
ms.openlocfilehash: f67c8426267bfb2e4aa2724b46f546d161e057b8
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67740684"
---
# <a name="attack-surface-reduction-asr-rules-deployment-overview"></a>Vue d’ensemble du déploiement des règles de réduction de surface d’attaque (ASR)

Les surfaces d’attaque sont tous les endroits où votre organisation est vulnérable aux cybermenaces et aux attaques. Les surfaces d’attaque de votre organisation incluent tous les emplacements où un attaquant peut compromettre les appareils ou les réseaux de votre organisation. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’attaquer. La configuration des règles de réduction de la surface d’attaque (ASR), l’une des nombreuses fonctionnalités de sécurité disponibles dans Pertahanan Microsoft untuk Titik Akhir, peut vous aider.

Les règles ASR ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts masqués ou suspects
- Comportements que les applications ne se produisent généralement pas pendant le travail quotidien normal

En réduisant les différentes surfaces d’attaque, vous pouvez empêcher les attaques de se produire en premier lieu.

## <a name="before-you-begin"></a>Avant de commencer

Lors de votre préparation initiale, il est essentiel de comprendre les fonctionnalités des systèmes que vous allez mettre en place. Comprendre les fonctionnalités vous aidera à déterminer les règles ASR les plus importantes pour protéger votre organisation. En outre, vous devez vous occuper de plusieurs prérequis pour préparer votre déploiement ASR.

>[!IMPORTANT]
>Ce guide fournit des images et des exemples pour vous aider à décider comment configurer des règles ASR ; ces images et exemples peuvent ne pas refléter les meilleures options de configuration pour votre environnement.

Avant de commencer, passez [en revue la vue d’ensemble de la réduction de la surface d’attaque](overview-attack-surface-reduction.md) et [la démystification des règles de réduction de la surface d’attaque - Partie 1](https://techcommunity.microsoft.com/t5/microsoft-defender-for-endpoint/demystifying-attack-surface-reduction-rules-part-1/ba-p/1306420) pour obtenir des informations de base. Pour comprendre les domaines de couverture et d’impact potentiel, familiarisez-vous avec l’ensemble actuel de règles ASR; consultez la [référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md).  Pendant que vous vous familiarisez avec l’ensemble de règles ASR, prenez note des mappages GUID par règle ; voir : [règle ASR à matrice GUID](attack-surface-reduction-rules-reference.md#asr-rule-to-guid-matrix).

Les règles ASR ne sont qu’une des fonctionnalités de réduction de la surface d’attaque dans Pertahanan Microsoft untuk Titik Akhir. Ce document décrit plus en détail le déploiement efficace de règles ASR pour arrêter les menaces avancées telles que les ransomwares gérés par l’homme et d’autres menaces.  

### <a name="rules-by-category"></a>Règles par catégorie

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

### <a name="infrastructure-requirements"></a>Conditions requises en matière d’infrastructure

Bien que plusieurs méthodes d’implémentation des règles ASR soient possibles, ce guide est basé sur une infrastructure composée des éléments suivants :

- Azure Active Directory
- Microsoft Endpoint Management (MEM)
- appareils Windows 10 et Windows 11
- licences Pertahanan Microsoft untuk Titik Akhir E5 ou Windows E5

Pour tirer pleinement parti des règles ASR et des rapports, nous vous recommandons d’utiliser une licence Microsoft 365 Defender E5 ou Windows E5 et A5. Mer informasjon : [Exigences minimales pour Pertahanan Microsoft untuk Titik Akhir](minimum-requirements.md).

>[!Note]
>Il existe plusieurs méthodes pour configurer des règles ASR. Les règles ASR peuvent être configurées à l’aide de : Microsoft Endpoint Manager (MEM), PowerShell, نهج المجموعة, Microsoft System Center Configuration Manager (SCCM), MEM OMA-URI.
>Si vous utilisez une configuration d’infrastructure différente de celle répertoriée pour _les exigences d’infrastructure_ (ci-dessus), vous pouvez en savoir plus sur le déploiement de règles de réduction de la surface d’attaque à l’aide d’autres configurations ici : [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md).  

### <a name="asr-rules-dependencies"></a>Dépendances des règles ASR

L’antivirus Microsoft Defender doit être activé et configuré en tant que solution antivirus principale et doit être en mode suivant :

- Solution antivirus/anti-programme malveillant principale  
- État : mode actif

L’Antivirus Microsoft Defender ne doit pas se trouver dans l’un des modes suivants :

- Passif
- Mode passif avec détection et réponse de point de terminaison (EDR) en mode bloc
- Analyse périodique limitée (LPS)
- Désactivé

Consultez : [Protection fournie par le cloud et Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

### <a name="cloud-protection-maps-must-be-enabled"></a>La protection cloud (MAPS) doit être activée

L’antivirus Microsoft Defender fonctionne en toute transparence avec les services cloud Microsoft. Ces services de protection cloud, également appelés Microsoft Advanced Protection Service (MAPS), améliorent la protection en temps réel standard, offrant sans doute la meilleure défense antivirus. La protection cloud est essentielle pour empêcher les violations des programmes malveillants et un composant critique des règles ASR.
[Activez la protection fournie par le cloud dans l’Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

### <a name="microsoft-defender-antivirus-components-must-be-current-versions"></a>Les composants de l’Antivirus Microsoft Defender doivent être des versions actuelles

Les versions suivantes du composant Antivirus Microsoft Defender ne doivent pas être plus de deux versions antérieures à la version la plus disponible :

- **Version de mise à jour de la plateforme antivirus Microsoft Defender**  : la plateforme antivirus Microsoft Defender est mise à jour tous les mois.
- **Version du moteur antivirus Microsoft Defender** : le moteur antivirus Microsoft Defender est mis à jour tous les mois.
- **Intelligence de sécurité de l’antivirus Microsoft Defender** - Microsoft met continuellement à jour le renseignement de sécurité Microsoft Defender (également appelé, définition et signature) pour répondre aux menaces les plus récentes et affiner la logique de détection.

La mise à jour des versions de l’Antivirus Microsoft Defender permet de réduire les résultats faux positifs des règles ASR et d’améliorer les fonctionnalités de détection de l’antivirus Microsoft Defender. Pour plus d’informations sur les versions actuelles et la mise à jour des différents composants de l’Antivirus Microsoft Defender, consultez la prise en charge de la [plateforme antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="caveat"></a>Caveat

Certaines règles ne fonctionnent pas correctement si les scripts et les applications non signés et développés en interne sont en forte utilisation. Il est plus difficile de déployer des règles ASR si la signature de code n’est pas appliquée.

## <a name="asr-rules-deployment-steps"></a>Étapes de déploiement des règles ASR

Comme pour toute nouvelle implémentation à grande échelle susceptible d’avoir un impact sur vos opérations métier, il est important d’être méthodique dans votre planification et votre implémentation. En raison des puissantes fonctionnalités des règles ASR pour empêcher les programmes malveillants, une planification et un déploiement prudents de ces règles sont nécessaires pour s’assurer qu’elles fonctionnent le mieux pour vos workflows clients uniques. Pour travailler dans votre environnement, vous devez planifier, tester, implémenter et mettre en œuvre les règles ASR avec soin.  

> [!div class="mx-imgBorder"]
> :::image type="content" source="images/asr-rules-deployment-phases.png" alt-text="Phases de déploiement des règles ASR" lightbox="images/asr-rules-deployment-phases.png":::

>[!Note]
>Pour les clients qui utilisent un HIPS autre que Microsoft et qui passent à Pertahanan Microsoft untuk Titik Akhir règles de réduction de la surface d’attaque : Microsoft conseille aux clients d’exécuter leur solution HIPS côte à côte avec leur déploiement de règles ASR jusqu’au moment où vous passez du mode Audit au mode Bloquer. Gardez à l’esprit que vous devez contacter votre fournisseur d’antivirus tiers pour obtenir des recommandations d’exclusion.  

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

### <a name="asr-collection"></a>Collection ASR

[Vue d’ensemble de la réduction de la surface d'attaque](overview-attack-surface-reduction.md)

[Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants](attack-surface-reduction.md)

[Activer les règles de réduction de la surface d’attaque - autres configurations](enable-attack-surface-reduction.md)

[Référence des règles de réduction de la surface d’attaque](attack-surface-reduction-rules-reference.md)

[FAQ sur la réduction de la surface d’attaque](attack-surface-reduction-faq.yml)

### <a name="microsoft-defender"></a>Microsoft Defender

[Résoudre des faux négatifs/positifs dans Microsoft Defender pour point de terminaison](defender-endpoint-false-positives-negatives.md)

[Protection par le cloud et antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md)

[Activer la protection fournie par le cloud dans l’antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md)

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
