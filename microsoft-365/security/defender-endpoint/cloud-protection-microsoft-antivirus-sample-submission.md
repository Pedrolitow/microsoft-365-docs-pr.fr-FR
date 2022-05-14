---
title: Protection cloud et soumission d’exemples au Antivirus Microsoft Defender
description: En savoir plus sur la protection et la Antivirus Microsoft Defender fournies par le cloud
keywords: Antivirus Microsoft Defender, technologies de nouvelle génération, soumission d’exemples d’antivirus, av de nouvelle génération, machine learning, logiciel anti-programme malveillant, sécurité, defender, cloud, protection fournie par le cloud
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 02/24/2022
ms.collection: M365-security-compliance
ms.openlocfilehash: 08f8e0c861bfd19f11c5b011d0a8db41ce3e73bc
ms.sourcegitcommit: ebbe8713297675db5dcb3e0d9c3ae5e746b99196
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/14/2022
ms.locfileid: "65419943"
---
# <a name="cloud-protection-and-sample-submission-at-microsoft-defender-antivirus"></a>Protection cloud et soumission d’exemples au Antivirus Microsoft Defender

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Antivirus Microsoft Defender utilise de nombreux mécanismes intelligents pour détecter les programmes malveillants. L’une des fonctionnalités les plus puissantes est la possibilité d’appliquer la puissance du cloud pour détecter les programmes malveillants et effectuer une analyse rapide. La protection cloud et la soumission automatique d’exemples fonctionnent avec Antivirus Microsoft Defender pour vous protéger contre les menaces nouvelles et émergentes. 

Si un fichier suspect ou malveillant est détecté, un exemple est envoyé au service cloud à des fins d’analyse pendant que Antivirus Microsoft Defender bloque le fichier. Dès qu’une décision est prise, ce qui se produit rapidement, le fichier est libéré ou bloqué par Antivirus Microsoft Defender. 

Cet article fournit une vue d’ensemble de la protection cloud et de la soumission automatique d’exemples à Antivirus Microsoft Defender. Pour en savoir plus sur la protection cloud, consultez [Protection cloud et Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Fonctionnement de la protection cloud et de la soumission d’exemples

Pour comprendre le fonctionnement de la protection cloud avec l’envoi d’exemples, il peut être utile de comprendre comment Defender pour point de terminaison protège contre les menaces. Microsoft Intelligent Security Graph surveille les données sur les menaces à partir d’un vaste réseau de capteurs. Microsoft superpose des modèles Machine Learning basés sur le cloud qui peuvent évaluer des fichiers en fonction des signaux du client et du vaste réseau de capteurs et de données dans le Graph de sécurité intelligente. Cette approche offre à Defender pour point de terminaison la possibilité de bloquer de nombreuses menaces jamais vues auparavant. 

L’image suivante illustre le flux de la protection cloud et de l’exemple de soumission avec Antivirus Microsoft Defender :

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Flux de protection fourni par le cloud" lightbox="images/cloud-protection-flow.png":::

Antivirus Microsoft Defender et la protection cloud bloquent automatiquement la plupart des nouvelles menaces jamais vues à la première consultation à l’aide des méthodes suivantes :

1. Modèles Machine Learning légers basés sur le client, bloquant les programmes malveillants nouveaux et inconnus.

2. Analyse comportementale locale, arrêt des attaques basées sur des fichiers et sans fichier.

3. Antivirus haute précision, détection de programmes malveillants courants par le biais de techniques génériques et heuristiques.

4. Une protection avancée basée sur le cloud est fournie pour les cas où Antivirus Microsoft Defender en cours d’exécution sur le point de terminaison nécessite plus d’intelligence pour vérifier l’intention d’un fichier suspect.

   1. Si Antivirus Microsoft Defender ne parvient pas à déterminer clairement, les métadonnées de fichier sont envoyées au service de protection cloud. Souvent en millisecondes, le service de protection cloud peut déterminer en fonction des métadonnées si le fichier est malveillant ou non une menace.  

      - La requête cloud de métadonnées de fichier peut être le résultat d’un comportement, d’une marque du web ou d’autres caractéristiques où un verdict clair n’est pas déterminé.
      - Une petite charge utile de métadonnées est envoyée, avec l’objectif d’atteindre le verdict d’un programme malveillant ou non d’une menace. Les métadonnées n’incluent pas d’informations d’identification personnelle (PII). Les informations telles que les noms de fichiers sont hachées.
      - Peut être synchrone ou asynchrone. Pour l’synchrone, le fichier ne s’ouvre pas tant que le cloud n’a pas rendu un verdict. Pour des raisons asynchrones, le fichier s’ouvre pendant que la protection cloud effectue son analyse.
      - Les métadonnées peuvent inclure des attributs PE, des attributs de fichier statique, des attributs dynamiques et contextuels, etc. (voir [Exemples de métadonnées envoyées au service de protection cloud](#examples-of-metadata-sent-to-the-cloud-protection-service)).

   2. Après examen des métadonnées, si Antivirus Microsoft Defender protection cloud ne peut pas parvenir à un verdict concluant, il peut demander un échantillon du fichier pour une inspection plus approfondie. Cette demande respecte la configuration des paramètres pour l’exemple de soumission :

      1. **Envoyer automatiquement des exemples sécurisés** (par défaut)
         - Coffre exemples sont des échantillons considérés comme ne contenant pas couramment des données d’identification personnelle telles que : .bat, .scr, .dll, .exe.
         - Si le fichier est susceptible de contenir des informations personnelles, l’utilisateur reçoit une demande d’autorisation de soumission d’exemple de fichier.
         - Cette option est la valeur par défaut sur Windows, macOS et Linux.

      2. **Toujours demander**
         - S’il est configuré, l’utilisateur est toujours invité à donner son consentement avant l’envoi du fichier
         - Ce paramètre n’est pas disponible dans macOS protection cloud

      3. **Envoyer tous les exemples automatiquement**
         - S’il est configuré, tous les exemples sont envoyés automatiquement
         - Si vous souhaitez que les exemples de soumission incluent des macros incorporées dans la documentation Word, vous devez choisir « Envoyer tous les exemples automatiquement »
         - Ce paramètre n’est pas disponible sur macOS protection cloud

      4. **Ne pas envoyer**
         - Empêche « bloquer à la première consultation » en fonction de l’analyse de l’exemple de fichier
         - « Ne pas envoyer » équivaut au paramètre « Désactivé » dans macOS stratégie
         - Les métadonnées sont envoyées pour les détections même lorsque l’envoi d’exemples est désactivé

   3. Une fois les métadonnées et/ou les fichiers envoyés à la protection cloud, vous pouvez utiliser **des exemples**, **des détonations** ou des modèles Machine Learning d’analyse **big data** pour parvenir à un verdict. La désactivation de la protection fournie par le cloud limite l’analyse à ce que le client peut fournir via des modèles Machine Learning locaux et des fonctions similaires.

> [!IMPORTANT]
> [Bloquer à la première consultation (BAFS)](configure-block-at-first-sight-microsoft-defender-antivirus.md) fournit une détonation et une analyse pour déterminer si un fichier ou un processus est sûr. BAFS peut retarder momentanément l’ouverture d’un fichier jusqu’à ce qu’un verdict soit rendu. Si vous désactivez l’envoi d’exemples, BAFS est également désactivé et l’analyse des fichiers est limitée aux métadonnées uniquement. Nous vous recommandons de conserver l’exemple de soumission et BAFS activés. Pour en savoir plus, voir [Qu’est-ce que « bloquer à la première consultation » ?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Niveaux de protection cloud

La protection cloud est activée par défaut à Antivirus Microsoft Defender. Nous vous recommandons de maintenir la protection cloud activée, bien que vous puissiez configurer le niveau de protection pour votre organisation. Voir [Spécifier le niveau de protection fourni par le cloud pour Antivirus Microsoft Defender](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Exemples de paramètres de soumission

En plus de configurer votre niveau de protection cloud, vous pouvez configurer vos exemples de paramètres de soumission. Vous pouvez choisir parmi plusieurs options :

- **Envoyer automatiquement des exemples sécurisés**  (comportement par défaut)
- **Envoyer tous les exemples automatiquement**  
- **Ne pas envoyer d’exemples**  

Pour plus d’informations sur les options de configuration à l’aide de Intune, de Configuration Manager, d’un objet de stratégie de groupe ou de PowerShell, consultez [Activer la protection cloud sur Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Exemples de métadonnées envoyées au service de protection cloud

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Exemples de métadonnées envoyées à la protection cloud dans le portail Antivirus Microsoft Defender" lightbox="images/cloud-protection-metadata-sample.png":::

Le tableau suivant répertorie des exemples de métadonnées envoyées pour analyse par la protection cloud :

| Type | Attribut |
|:---|:---|
| Attributs de machine | `OS version` <br/> `Processor` <br/> `Security settings` |
| Attributs dynamiques et contextuels | **Processus et installation** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Comportemental** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Locale** <br/> `Locale setting` <br/> `Geographical location` |
| Attributs de fichier statiques | **Hachages partiels et complets** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Propriétés de fichier** <br/>`FileName` <br/> `FileSize` <br/><br/> **Informations sur le signataire** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Les exemples sont traités comme des données client

Au cas où vous vous demandez ce qui se passe avec les exemples d’envois, Defender pour point de terminaison traite tous les exemples de fichiers comme des données client. Microsoft respecte les choix géographiques et de rétention des données sélectionnés par votre organisation lors de l’intégration à Defender pour point de terminaison. 

En outre, Defender pour point de terminaison a reçu plusieurs certifications de conformité, ce qui démontre l’adhésion continue à un ensemble sophistiqué de contrôles de conformité :

- ISO 27001
- ISO 27018
- SOC I, II, III
- PCI

Pour plus d’informations, reportez-vous aux ressources suivantes :

- [Offres de conformité Azure](/azure/storage/common/storage-compliance-offerings) 
- [Portail d’approbation de service](https://servicetrust.microsoft.com)
- [Microsoft Defender pour point de terminaison le stockage et la confidentialité des données](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Autres scénarios d’envoi d’exemples de fichiers

Il existe deux autres scénarios où Defender pour point de terminaison peut demander un exemple de fichier qui n’est pas lié à la protection cloud à Antivirus Microsoft Defender. Ces scénarios sont décrits dans le tableau suivant :

| Scénario | Description |
|:---|:---|
|Collecte manuelle d’exemples de fichiers dans le portail Microsoft 365 Defender | Lors de l’intégration d’appareils à Defender pour point de terminaison, vous pouvez configurer les paramètres de [protection évolutive des points de terminaison (PEPT)](overview-endpoint-detection-response.md) . Par exemple, il existe un paramètre permettant d’activer des exemples de collections à partir de l’appareil, qui peuvent facilement être confondus avec les exemples de paramètres de soumission décrits dans cet article. <br/><br/>Le paramètre PEPT contrôle la collecte d’exemples de fichiers à partir d’appareils lorsqu’il est demandé via le portail Microsoft 365 Defender et est soumis aux rôles et autorisations déjà établis. Ce paramètre peut autoriser ou bloquer la collecte de fichiers à partir du point de terminaison pour des fonctionnalités telles que l’analyse approfondie dans le portail Microsoft 365 Defender. Si ce paramètre n’est pas configuré, la valeur par défaut consiste à activer la collecte d’exemples. <br/><br/>En savoir plus sur les paramètres de configuration de Defender pour point de terminaison, consultez : [Outils et méthodes d’intégration pour les appareils Windows 10 dans Defender pour point de terminaison](configure-endpoints.md) |
| Analyse automatisée du contenu d’investigation et de réponse | Lorsque [des investigations automatisées](automated-investigations.md) s’exécutent sur des appareils (lorsqu’elles sont configurées pour s’exécuter automatiquement en réponse à une alerte ou exécutées manuellement), les fichiers identifiés comme suspects peuvent être collectés à partir des points de terminaison pour une inspection plus approfondie. Si nécessaire, la fonctionnalité d’analyse de contenu de fichier pour les investigations automatisées peut être désactivée dans le portail Microsoft 365 Defender. <br/><br/> Les noms d’extension de fichier peuvent également être modifiés pour ajouter ou supprimer des extensions pour d’autres types de fichiers qui seront automatiquement envoyés lors d’une investigation automatisée. <br/><br/> Pour plus d’informations, consultez [Gérer les chargements de fichiers Automation](manage-automation-file-uploads.md). |

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la protection nouvelle génération](next-generation-protection.md)

[Configurez la correction des détections Antivirus Microsoft Defender.](configure-remediation-microsoft-defender-antivirus.md)
