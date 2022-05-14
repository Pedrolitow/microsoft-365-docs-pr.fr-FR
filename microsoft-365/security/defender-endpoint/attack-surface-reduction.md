---
title: Utiliser des règles de réduction de la surface d’attaque pour empêcher l’infection des programmes malveillants
description: Les règles de réduction de la surface d’attaque peuvent aider à empêcher les exploits d’utiliser des applications et des scripts pour infecter les appareils avec des programmes malveillants.
keywords: Règles de réduction de la surface d’attaque, asr, hanches, système de prévention des intrusions de l’hôte, règles de protection, anti-exploitation, antiexploitation, exploit, prévention des infections, Microsoft Defender pour point de terminaison
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
ms.collection:
- m365initiative-m365-defender
- M365-security-compliance
ms.date: 1/18/2022
ms.openlocfilehash: a1ae7d53ac69b4756417704b4938ff4fb41f9e41
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65418803"
---
# <a name="attack-surface-reduction-rules-overview"></a>Vue d’ensemble des règles de réduction de la surface d’attaque

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

## <a name="why-attack-surface-reduction-rules-are-important"></a>Pourquoi les règles de réduction de la surface d’attaque sont importantes

La surface d’attaque de votre organisation inclut tous les emplacements où un attaquant peut compromettre les appareils ou les réseaux de votre organisation. Réduire votre surface d’attaque signifie protéger les appareils et le réseau de votre organisation, ce qui laisse aux attaquants moins de moyens d’effectuer des attaques. La configuration des règles de réduction de la surface d’attaque dans Microsoft Defender pour point de terminaison peut vous aider !

Les règles de réduction de la surface d’attaque ciblent certains comportements logiciels, tels que :

- Lancement de fichiers exécutables et de scripts qui tentent de télécharger ou d’exécuter des fichiers
- Exécution de scripts masqués ou suspects
- Exécution de comportements que les applications n’initient généralement pas pendant le travail quotidien normal

De tels comportements logiciels sont parfois observés dans les applications légitimes. Toutefois, ces comportements sont souvent considérés comme risqués, car ils sont couramment utilisés par les attaquants par le biais de programmes malveillants. Les règles de réduction de la surface d’attaque peuvent limiter les comportements à risque basés sur les logiciels et contribuer à la sécurité de votre organisation.

Pour plus d’informations sur la configuration des règles de réduction de la surface d’attaque, consultez [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md).

## <a name="assess-rule-impact-before-deployment"></a>Évaluer l’impact des règles avant le déploiement

Vous pouvez évaluer la façon dont une règle de réduction de la surface d’attaque peut affecter votre réseau en ouvrant la recommandation de sécurité pour cette règle dans [Gestion des menaces et des vulnérabilités](/windows/security/threat-protection/#tvm).

:::image type="content" source="images/asrrecommendation.png" alt-text="La recommandation ASR" lightbox="images/asrrecommendation.png":::

Dans le volet des détails de la recommandation, recherchez l’impact utilisateur pour déterminer le pourcentage de vos appareils pouvant accepter une nouvelle stratégie activant la règle en mode de blocage sans affecter la productivité.

[Pour plus](enable-attack-surface-reduction.md#requirements) d’informations sur les systèmes d’exploitation pris en charge et les exigences supplémentaires, consultez l’article « Activer les règles de réduction de la surface d’attaque ».

## <a name="audit-mode-for-evaluation"></a>Mode d’audit pour l’évaluation

Utilisez le [mode audit](audit-windows-defender.md) pour évaluer la façon dont les règles de réduction de la surface d’attaque affectent votre organisation si elles sont activées. Exécutez d’abord toutes les règles en mode audit afin de comprendre comment elles affectent vos applications métier. De nombreuses applications métier sont écrites avec des problèmes de sécurité limités, et elles peuvent effectuer des tâches d’une manière similaire aux programmes malveillants. En surveillant les données d’audit et [en ajoutant des exclusions pour les](enable-attack-surface-reduction.md#exclude-files-and-folders-from-asr-rules) applications nécessaires, vous pouvez déployer des règles de réduction de la surface d’attaque sans réduire la productivité.

## <a name="warn-mode-for-users"></a>Mode d’avertissement pour les utilisateurs

(**NOUVEAU**!) Avant d’avertir les fonctionnalités du mode, les règles de réduction de la surface d’attaque activées pouvaient être définies sur le mode audit ou le mode bloc. Avec le nouveau mode d’avertissement, chaque fois que le contenu est bloqué par une règle de réduction de la surface d’attaque, les utilisateurs voient une boîte de dialogue qui indique que le contenu est bloqué. La boîte de dialogue offre également à l’utilisateur la possibilité de débloquer le contenu. L’utilisateur peut ensuite réessayer son action et l’opération se termine. Lorsqu’un utilisateur débloque du contenu, celui-ci reste débloqué pendant 24 heures, puis le blocage reprend.

Le mode d’avertissement permet à votre organisation de mettre en place des règles de réduction de la surface d’attaque sans empêcher les utilisateurs d’accéder au contenu dont ils ont besoin pour effectuer leurs tâches.

### <a name="requirements-for-warn-mode-to-work"></a>Configuration requise pour que le mode d’avertissement fonctionne

Le mode d’avertissement est pris en charge sur les appareils exécutant les versions suivantes de Windows :

- [Windows 10, version 1809](/windows/whats-new/whats-new-windows-10-version-1809) ou version ultérieure
- Windows 11
- [Windows Server, version 1809](/windows-server/get-started/whats-new-in-windows-server-1809) ou ultérieure

Antivirus Microsoft Defender doit s’exécuter avec une protection en temps réel en [mode Actif](/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state).

Assurez-vous également que [Antivirus Microsoft Defender et les mises à jour anti-programme malveillant](/windows/security/threat-protection/microsoft-defender-antivirus/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions) sont installées.

- Condition de mise en production minimale de la plateforme : `4.18.2008.9`
- Condition de mise en production minimale du moteur : `1.1.17400.5`

Pour plus d’informations et pour obtenir vos mises à jour, consultez [Update for Microsoft Defender antimalware platform](https://support.microsoft.com/help/4052623/update-for-microsoft-defender-antimalware-platform).

### <a name="cases-where-warn-mode-is-not-supported"></a>Cas où le mode d’avertissement n’est pas pris en charge

Le mode d’avertissement n’est pas pris en charge pour trois règles de réduction de la surface d’attaque lorsque vous les configurez dans Microsoft Endpoint Manager. (Si vous utilisez stratégie de groupe pour configurer vos règles de réduction de la surface d’attaque, le mode d’avertissement est pris en charge.) Les trois règles qui ne prennent pas en charge le mode d’avertissement lorsque vous les configurez dans Microsoft Endpoint Manager sont les suivantes :

- [Empêcher JavaScript ou VBScript de lancer le contenu exécutable téléchargé](attack-surface-reduction-rules-reference.md#block-javascript-or-vbscript-from-launching-downloaded-executable-content) (GUID `d3e037e1-3eb8-44c8-a917-57927947596d`)
- [Bloquer la persistance via l’abonnement aux événements WMI](attack-surface-reduction-rules-reference.md#block-persistence-through-wmi-event-subscription) (GUID `e6db77e5-3df2-4cf1-b95a-636979351e5b`)
- [Utiliser une protection avancée contre les ransomware](attack-surface-reduction-rules-reference.md#use-advanced-protection-against-ransomware) (GUID `c1db55ab-c21a-4637-bb3f-a12568109d35`)

En outre, le mode d’avertissement n’est pas pris en charge sur les appareils exécutant des versions antérieures de Windows. Dans ce cas, les règles de réduction de la surface d’attaque configurées pour s’exécuter en mode d’avertissement s’exécutent en mode bloc.

## <a name="notifications-and-alerts"></a>Notifications et alertes

Chaque fois qu’une règle de réduction de la surface d’attaque est déclenchée, une notification s’affiche sur l’appareil. Vous pouvez [personnaliser la notification](attack-surface-reduction-rules-deployment-implement.md#customize-attack-surface-reduction-rules) avec les informations et les coordonnées de l’entreprise.

En outre, lorsque certaines règles de réduction de la surface d’attaque sont déclenchées, des alertes sont générées.

Les notifications et les alertes générées peuvent être affichées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

Pour plus d’informations sur les fonctionnalités de notification et d’alerte, consultez : Informations sur les [alertes par règle et les notifications](attack-surface-reduction-rules-reference.md#per-rule-alert-and-notification-details), dans l’article référence sur les **règles de réduction de la surface** d’attaque.

## <a name="advanced-hunting-and-attack-surface-reduction-events"></a>Événements avancés de chasse et de réduction de la surface d’attaque

Vous pouvez utiliser la chasse avancée pour afficher les événements de réduction de la surface d’attaque. Pour simplifier le volume de données entrantes, seuls les processus uniques pour chaque heure sont visibles avec la chasse avancée. L’heure d’un événement de réduction de la surface d’attaque est la première fois que cet événement est vu dans l’heure.

Par exemple, supposons qu’un événement de réduction de la surface d’attaque se produise sur 10 appareils pendant l’heure de 14h00. Supposons que le premier événement s’est produit à 2:15, et le dernier à 2:45. Avec la chasse avancée, vous verrez une instance de cet événement (même si elle s’est réellement produite sur 10 appareils) et son horodatage sera 14h15.

Pour plus d’informations sur la chasse avancée, consultez [La chasse proactive contre les menaces avec la chasse avancée](advanced-hunting-overview.md).

## <a name="attack-surface-reduction-features-across-windows-versions"></a>Fonctionnalités de réduction de la surface d’attaque dans Windows versions

Vous pouvez définir des règles de réduction de la surface d’attaque pour les appareils qui exécutent l’une des éditions et versions suivantes de Windows :

- Windows 10 Professionnel, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) ou ultérieure
- Windows 10 Entreprise, [version 1709](/windows/whats-new/whats-new-windows-10-version-1709) ou ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](/windows-server/get-started/whats-new-in-windows-server-1803) ou ultérieure
- [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
- [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
- [Windows Server 2012 R2](/win32/srvnodes/what-s-new-for-windows-server-2012-r2)

  >[!NOTE]
  >Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [Intégrer des serveurs Windows](configure-server-endpoints.md#windows-server-2012-r2-and-windows-server-2016) pour que cette fonctionnalité fonctionne.

Bien que les règles de réduction de la surface d’attaque ne nécessitent pas de [licence Windows E5](/windows/deployment/deploy-enterprise-licenses), si vous avez Windows E5, vous bénéficiez de fonctionnalités de gestion avancées. Les fonctionnalités avancées disponibles uniquement dans Windows E5 sont les suivantes :

- Surveillance, analytique et flux de travail disponibles dans [Defender pour point de terminaison](microsoft-defender-endpoint.md)
- Fonctionnalités de création de rapports et de configuration dans [Microsoft 365 Defender](/microsoft-365/security/defender/overview-security-center).

Ces fonctionnalités avancées ne sont pas disponibles avec une licence Windows Professional ou Windows E3. Toutefois, si vous disposez de ces licences, vous pouvez utiliser observateur d'événements et Antivirus Microsoft Defender journaux pour passer en revue vos événements de règle de réduction de la surface d’attaque.

## <a name="review-attack-surface-reduction-events-in-the-microsoft-365-defender-portal"></a>Examiner les événements de réduction de la surface d’attaque dans le portail Microsoft 365 Defender

Defender pour point de terminaison fournit des rapports détaillés pour les événements et les blocs dans le cadre de scénarios d’investigation d’alerte.

Vous pouvez interroger des données Defender pour point de terminaison dans [Microsoft 365 Defender](microsoft-defender-endpoint.md) à l’aide de [la chasse avancée](/microsoft-365/security/defender/advanced-hunting-query-language). 

Voici un exemple de requête :

```kusto
DeviceEvents
| where ActionType startswith 'Asr'
```

## <a name="review-attack-surface-reduction-events-in-windows-event-viewer"></a>Examiner les événements de réduction de la surface d’attaque dans Windows observateur d'événements

Vous pouvez consulter le journal des événements Windows pour afficher les événements générés par les règles de réduction de la surface d’attaque :

1. Téléchargez le [package d’évaluation](https://aka.ms/mp7z2w) et extrayez le fichier *cfa-events.xml* à un emplacement facilement accessible sur l’appareil.

2. Entrez les mots, *observateur d'événements*, dans le menu Démarrer pour ouvrir le Windows observateur d'événements.

3. Sous **Actions**, sélectionnez **Importer un affichage personnalisé...**.

4. Sélectionnez le fichier *cfa-events.xml* à partir duquel il a été extrait. Vous pouvez également [copier le code XML directement](event-views.md).

5. Sélectionnez **OK**.

Vous pouvez créer une vue personnalisée qui filtre les événements pour afficher uniquement les événements suivants, qui sont tous liés à l’accès contrôlé aux dossiers :

|ID d’événement|Description|
|---|---|
|5007|Événement lorsque les paramètres sont modifiés|
|1121|Événement lorsque la règle se déclenche en mode bloc|
|1122|Événement lors de l’déclenchement d’une règle en mode Audit|

La « version du moteur » répertoriée pour les événements de réduction de la surface d’attaque dans le journal des événements est générée par Defender pour point de terminaison, et non par le système d’exploitation. Defender pour point de terminaison étant intégré à Windows 10 et Windows 11, cette fonctionnalité fonctionne sur tous les appareils avec Windows 10 ou Windows 11 installés.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
