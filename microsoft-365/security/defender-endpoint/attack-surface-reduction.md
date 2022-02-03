---
title: Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants
description: Les règles de réduction de la surface d’attaque peuvent empêcher les attaques d’utiliser des applications et des scripts pour infecter les appareils à l’aide de programmes malveillants.
keywords: Règles de réduction de la surface d’attaque, asr, hips, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, Microsoft Defender pour point de terminaison
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
audience: ITPro
author: jweston-1
ms.author: v-jweston
ms.reviewer: oogunrinde, sugamar
manager: dansimp
ms.custom:
- asr
- admindeeplinkDEFENDER
ms.technology: mde
ms.topic: article
ms.collection: m365initiative-m365-defender
ms.date: 1/18/2022
ms.openlocfilehash: e56ffd44976d11986b6ccb6b3e8bc5cbf71e530c
ms.sourcegitcommit: 726a72f135358603c2fde3f4067d834536e6deb2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/03/2022
ms.locfileid: "62326944"
---
# <a name="attack-surface-reduction-rules-overview"></a>Vue d’ensemble des règles de réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

## <a name="why-attack-surface-reduction-rules-are-important"></a>Pourquoi les règles de réduction de la surface d’attaque sont-elles importantes ?

La surface d’attaque de votre organisation inclut tous les endroits où un attaquant peut compromettre les appareils ou les réseaux de votre organisation. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’effectuer des attaques. La configuration des règles de réduction de la surface d’attaque dans Microsoft Defender pour endpoint peut vous aider !

Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts obscurcis ou suspects
- Comportement d’une application qui n’est généralement pas initiée pendant le travail quotidien normal

De tels comportements logiciels sont parfois observés dans les applications légitimes. Toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment abusés par des personnes malveillantes par le biais de programmes malveillants. Les règles de réduction de la surface d’attaque peuvent limiter les comportements à risque logiciels et contribuer à la sécurité de votre organisation.

Pour plus d’informations sur la configuration des règles de réduction de la surface d’attaque, voir Activer les règles de réduction [de la surface d’attaque](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Évaluer l’impact des règles avant le déploiement

Vous pouvez évaluer l’impact d’une règle de réduction de la surface d’attaque sur votre réseau en ouvrant la recommandation de sécurité pour [cette règle dans Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="Contrôle de sécurité pour la règle de réduction de la surface d’attaque.":::

Dans le volet d’informations de recommandation, vérifiez l’impact sur l’utilisateur pour déterminer le pourcentage de vos appareils qui peuvent accepter une nouvelle stratégie autorisant la règle en mode de blocage sans affecter la productivité.

Pour plus [d’informations sur les](enable-attack-surface-reduction.md#requirements) systèmes d’exploitation pris en charge et d’autres informations sur les conditions requises, voir La procédure requise dans l’article « Activer les règles de réduction de la surface d’attaque ».

## <a name="audit-mode-for-evaluation"></a>Mode audit pour l’évaluation

Utilisez le [mode audit pour](audit-windows-defender.md) évaluer l’impact des règles de réduction de la surface d’attaque sur votre organisation si elle est activée. Exécutez d’abord toutes les règles en mode audit pour comprendre comment elles affectent vos applications métier. De nombreuses applications métier sont écrites avec des problèmes de sécurité limités et peuvent effectuer des tâches qui semblent similaires aux programmes malveillants. En surveillant les données d’audit et en ajoutant [des exclusions](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) pour les applications nécessaires, vous pouvez déployer des règles de réduction de la surface d’attaque sans réduire la productivité.

## <a name="warn-mode-for-users"></a>Mode Avertissement pour les utilisateurs

(**NOUVEAU**!) Avant d’avertir les fonctionnalités du mode, les règles de réduction de la surface d’attaque activées pouvaient être définies sur le mode audit ou le mode blocage. Avec le nouveau mode d’avertissement, chaque fois que le contenu est bloqué par une règle de réduction de la surface d’attaque, les utilisateurs voient une boîte de dialogue qui indique que le contenu est bloqué. La boîte de dialogue offre également à l’utilisateur la possibilité de débloquer le contenu. L’utilisateur peut ensuite réessayer son action et l’opération se termine. Lorsqu’un utilisateur débloque du contenu, il reste débloqué pendant 24 heures, puis bloque les reprises.

Le mode Avertissement aide votre organisation à mettre en place des règles de réduction de la surface d’attaque sans empêcher les utilisateurs d’accéder au contenu dont ils ont besoin pour effectuer leurs tâches.

### <a name="requirements-for-warn-mode-to-work"></a>Conditions requises pour que le mode d’avertissement fonctionne

Le mode Avertissement est pris en charge sur les appareils exécutant les versions suivantes de Windows :

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809) ou ultérieure
- Windows 11
- [Windows Server, version 1809 ou](/windows-server/get-started/whats-new-in-windows-server-1809) ultérieure

Antivirus Microsoft Defender doit être en cours d’exécution avec une protection en temps réel [en mode actif](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Assurez-vous également [que Antivirus Microsoft Defender mises](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) à jour du logiciel anti-programme malveillant sont installées.

- Conditions minimales requises pour la publication de la plateforme : `4.18.2008.9`
- Conditions minimales requises pour la publication du moteur : `1.1.17400.5`

Pour plus d’informations et pour obtenir vos mises à jour, voir Mise à jour [pour la plateforme anti-programme malveillant Microsoft Defender](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Cas où le mode d’avertissement n’est pas pris en charge

Le mode Avertissement n’est pas pris en charge pour trois règles de réduction de la surface d’attaque lorsque vous les configurez dans Microsoft Endpoint Manager. (Si vous utilisez une stratégie de groupe pour configurer vos règles de réduction de la surface d’attaque, le mode d’avertissement est pris en charge.) Les trois règles qui ne viennent pas en charge le mode d’avertissement lorsque vous les configurez Microsoft Endpoint Manager sont les suivantes :

- [Empêcher JavaScript ou VBScript de lancer le contenu exécutable](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) téléchargé (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`)
- [Bloquer la persistance via l’abonnement aux événements WMI](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [Utiliser la protection avancée contre les ransomware](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

En outre, le mode d’avertissement n’est pas pris en charge sur les appareils exécutant des versions antérieures Windows. Dans ce cas, les règles de réduction de la surface d’attaque configurées pour s’exécuter en mode avertissement s’exécutent en mode blocage.

## <a name="notifications-and-alerts"></a>Notifications et alertes

Chaque fois qu’une règle de réduction de la surface d’attaque est déclenchée, une notification s’affiche sur l’appareil. Vous pouvez [personnaliser la notification](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) avec les informations et les coordonnées de l’entreprise.

En outre, lorsque certaines règles de réduction de la surface d’attaque sont déclenchées, des alertes sont générées.

Les notifications et les alertes générées peuvent être vues dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender web</a>.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Événements de réduction de la surface d’attaque et de recherche avancée

Vous pouvez utiliser le hunting avancé pour afficher les événements de réduction de la surface d’attaque. Pour simplifier le volume des données entrantes, seuls les processus uniques pour chaque heure sont consultables avec le hunting avancé. L’heure d’un événement de réduction de la surface d’attaque est la première fois que cet événement est vu dans l’heure.

Par exemple, supposons qu’un événement de réduction de la surface d’attaque se produise sur 10 appareils pendant l’heure de 14 h 00. Supposons que le premier événement s’est produit à 2:15 et le dernier à 2:45. Avec le hunting avancé, vous verrez une instance de cet événement (même si elle s’est réellement produite sur 10 appareils) et son timestamp sera 14:15 PM.

Pour plus d’informations sur le chasse avancée, voir [La recherche proactive des menaces avec le chasse avancée](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Fonctionnalités de réduction de la surface d’attaque Windows versions

Vous pouvez définir des règles de réduction de la surface d’attaque pour les appareils qui exécutent l’une des éditions et versions suivantes de Windows :

- Windows 10 Professionnel, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions des serveurs Windows [intégrés](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) pour que cette fonctionnalité fonctionne. 


Bien que les règles de réduction de la surface d’attaque ne nécessitent [Windows licence E5](/windows/deployment/deploy-enterprise-licenses), si vous avez Windows E5, vous obtenez des fonctionnalités de gestion avancées. Les fonctionnalités avancées, disponibles uniquement dans Windows E5, sont les suivantes :

- Surveillance, analyse et flux de travail disponibles dans [Defender for Endpoint](microsoft-defender-endpoint.md)
- Fonctionnalités de rapport et de configuration [dans Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Ces fonctionnalités avancées ne sont pas disponibles avec une licence Windows Professional ou Windows E3. Toutefois, si vous avez ces licences, vous pouvez utiliser l’Observateur d’événements et les journaux Antivirus Microsoft Defender pour passer en revue vos événements de règle de réduction de la surface d’attaque.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Passer en revue les événements de réduction de la surface d’Microsoft 365 Defender d’attaque

Defender pour le point de terminaison fournit des rapports détaillés pour les événements et les blocages dans le cadre de scénarios d’investigation d’alerte.

Vous pouvez interroger Defender pour obtenir des données de point de [terminaison Microsoft 365 Defender](microsoft-defender-security-center.md) à l’aide [d’un chasse avancée](advanced-hunting-query-language.md). Si vous exécutez le [mode audit](audit-windows-defender.md), vous pouvez utiliser la recherche avancée pour comprendre l’impact des règles de réduction de la surface d’attaque sur votre environnement.

Voici un exemple de requête :

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Passer en revue les événements de réduction de la surface d’Windows l’Observateur d’événements

Vous pouvez consulter le journal Windows événements pour afficher les événements générés par les règles de réduction de la surface d’attaque :

1. Téléchargez le [package d’évaluation](https://aka.ms/mp7z2w) et *extrayez le fichiercfa-events.xml* un emplacement facilement accessible sur l’appareil.

2. Entrez les mots, *Observateur d’événements*, dans le menu Démarrer pour ouvrir l Windows’observateur d’événements.

3. Sous **Actions**, **sélectionnez Importer un affichage personnalisé...**.

4. Sélectionnez le fichier *cfa-events.xml'où* il a été extrait. Vous pouvez également [copier le XML directement](event-views.md).

5. Sélectionnez **OK**.

Vous pouvez créer une vue personnalisée qui filtre les événements pour afficher uniquement les événements suivants, tous liés à l’accès contrôlé aux dossiers :

|ID d’événement|Description|
|---|---|
|5007|Événement lorsque les paramètres sont modifiés|
|1121|Événement lorsque la règle se déclenche en mode blocage|
|1122|Événement lorsque la règle se déclenche en mode audit|

La « version du moteur » répertoriée pour les événements de réduction de la surface d’attaque dans le journal des événements est générée par Defender pour le point de terminaison, et non par le système d’exploitation. Defender pour le point de terminaison est intégré à Windows 10 et Windows 11, de sorte que cette fonctionnalité fonctionne sur tous les appareils sur Windows 10 ou Windows 11 installé.
