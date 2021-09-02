---
title: Protection cloud et soumission d’exemples dans Antivirus Microsoft Defender
description: En savoir plus sur la protection et les Antivirus Microsoft Defender
keywords: Antivirus Microsoft Defender, technologies de nouvelle génération, soumission d’exemples antivirus, antivirus de nouvelle génération, machine learning, anti-programme malveillant, sécurité, defender, cloud, protection cloud
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 08/31/2021
ms.openlocfilehash: 5d9f6ace79d05eff795041732e045abf18d5f792
ms.sourcegitcommit: ef9cd046c47b340686a4f7bb123ea3b0a269769a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2021
ms.locfileid: "58864013"
---
# <a name="cloud-protection-and-sample-submission-in-microsoft-defender-antivirus"></a>Protection cloud et soumission d’exemples dans Antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)
- Antivirus Microsoft Defender

Antivirus Microsoft Defender utilise de nombreux mécanismes intelligents pour détecter les programmes malveillants. L’une des fonctionnalités les plus puissantes est la possibilité d’appliquer la puissance du cloud pour détecter les programmes malveillants et effectuer une analyse rapide. La protection cloud et l’envoi automatique d’échantillons fonctionnent avec Antivirus Microsoft Defender pour vous protéger contre les menaces nouvelles et émergentes. 

Si un fichier suspect ou malveillant est détecté, un échantillon est envoyé au service cloud pour analyse, Antivirus Microsoft Defender bloque le fichier. Dès qu’une décision est prise, ce qui se produit rapidement, le fichier est libéré ou bloqué par Antivirus Microsoft Defender. 

Cet article fournit une vue d’ensemble de la protection cloud et de l’envoi automatique d’échantillons dans Antivirus Microsoft Defender. Pour en savoir plus sur la protection cloud, voir [Protection cloud et Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

## <a name="how-cloud-protection-and-sample-submission-work-together"></a>Fonctionnement commun de la protection cloud et de l’envoi d’exemples

Pour comprendre comment la protection cloud fonctionne avec l’envoi d’exemples, il peut être utile de comprendre comment Defender pour le point de terminaison protège contre les menaces. La sécurité intelligente de Microsoft Graph les données sur les menaces à partir d’un vaste réseau de capteurs. Microsoft calques cloud machine learning models that can assess files based on signals from the client and the vast network of sensors and data in the Intelligent Security Graph. Cette approche permet à Defender for Endpoint de bloquer de nombreuses menaces jamais vues. 

L’image suivante illustre le flux de la protection cloud et de l’envoi d’exemples Antivirus Microsoft Defender :

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Flux de protection cloud":::

Antivirus Microsoft Defender protection cloud bloquent automatiquement la plupart des nouvelles menaces jamais vues à la première vue à l’aide des méthodes suivantes :

1. Modèles d’apprentissage automatique légers basés sur le client, bloquant les programmes malveillants nouveaux et inconnus.

2. Analyse comportementale locale, arrêt des attaques basées sur des fichiers et sans fichier.

3. Antivirus de haute précision, détectant les programmes malveillants courants par le biais de techniques génériques et heuristiques.

4. Une protection avancée basée sur le cloud est fournie pour les cas où Antivirus Microsoft Defender en cours d’exécution sur le point de terminaison a besoin d’une plus grande intelligence pour vérifier l’intention d’un fichier suspect.

   1. Dans le cas Antivirus Microsoft Defender impossible de déterminer clairement, les métadonnées de fichier sont envoyées au service de protection cloud. Souvent, en millisecondes, le service de protection cloud peut déterminer en fonction des métadonnées si le fichier est malveillant ou non une menace.  

      - La requête cloud de métadonnées de fichier peut être le résultat d’un comportement, d’une marque du site web ou d’autres caractéristiques dans le cas où un verdict clair n’est pas déterminé.
      - Une charge utile de métadonnées de petite taille est envoyée, dans le but d’atteindre un verdict de programmes malveillants ou de ne pas être une menace. Les métadonnées n’incluent pas d’informations d’identification personnelle (PII). Les informations telles que les noms de fichiers sont hachées.
      - Peut être synchrone ou asynchrone. Pour synchrone, le fichier ne s’ouvre pas tant que le cloud n’a pas rendu de verdict. Pour les données asynchrones, le fichier s’ouvre pendant que la protection cloud effectue son analyse.
      - Les métadonnées peuvent inclure des attributs PE, des attributs de fichiers statiques, des attributs dynamiques et contextuels, et bien plus encore (voir des exemples de métadonnées envoyées au [service de protection cloud).](#examples-of-metadata-sent-to-the-cloud-protection-service)

   2. Après avoir examiné les métadonnées, si Antivirus Microsoft Defender protection cloud ne peut pas parvenir à un verdict de première classe, elle peut demander un échantillon du fichier pour une inspection plus approfondie. Cette demande honore la configuration des paramètres pour l’envoi d’exemples :

      1. **Envoyer automatiquement des échantillons sûrs** (par défaut)
         - Coffre exemples sont des exemples considérés comme ne contenant pas fréquemment des données d’informations d'.bat, .scr, .dll, .exe.
         - Si le fichier est susceptible de contenir des pii, l’utilisateur reçoit une demande d’autoriser l’envoi d’exemples de fichier.
         - Cette option est la valeur par défaut sur Windows, macOS et Linux.

      2. **Always Prompt**
         - S’il est configuré, l’utilisateur est toujours invité à donner son consentement avant l’envoi du fichier.
         - Ce paramètre n’est pas disponible dans la protection cloud macOS

      3. **Envoyer tous les échantillons automatiquement**
         - S’il est configuré, tous les échantillons sont envoyés automatiquement
         - Si vous souhaitez inclure des macros incorporées dans des documents Word pour l’envoi d’exemples, vous devez choisir « Envoyer tous les exemples automatiquement »
         - Ce paramètre n’est pas disponible sur la protection cloud macOS

      4. **Ne pas envoyer**
         - Empêche « bloquer à la première vue » en fonction de l’analyse de l’exemple de fichier
         - « Ne pas envoyer » équivaut au paramètre « Désactivé » dans la stratégie macOS
         - Les métadonnées sont envoyées pour des détections, même lorsque l’envoi d’échantillons est désactivé

   3. Une fois les métadonnées et/ou les fichiers envoyés à la protection cloud, vous pouvez utiliser des **exemples,** des **détonations** ou des modèles d’apprentissage automatique d’analyse de **big data** pour parvenir à un verdict. La non-fonctionnalité de protection fournie par le cloud limite l’analyse à ce que le client peut fournir par le biais de modèles d’apprentissage automatique locaux et de fonctions similaires.

> [!IMPORTANT]
> [Le service Bloquer à la première consultation (BAFS)](configure-block-at-first-sight-microsoft-defender-antivirus.md) fournit une détonation et une analyse pour déterminer si un fichier ou un processus est sécurisé. BAFS peut retarder momentanément l’ouverture d’un fichier jusqu’à ce qu’un verdict soit atteint. Si vous désactivez l’envoi d’échantillons, BAFS est également désactivé et l’analyse de fichier est limitée aux métadonnées uniquement. Nous vous recommandons de conserver l’envoi d’échantillons et BAFS activés. Pour plus d’informations, [voir « Bloquer à la première vue » ?](configure-block-at-first-sight-microsoft-defender-antivirus.md#what-is-block-at-first-sight)

## <a name="cloud-protection-levels"></a>Niveaux de protection cloud

La protection cloud est activée par défaut dans Antivirus Microsoft Defender. Nous vous recommandons de maintenir la protection cloud activée, bien que vous pouvez configurer le niveau de protection pour votre organisation. Voir [Spécifier le niveau de protection cloud pour Antivirus Microsoft Defender](specify-cloud-protection-level-microsoft-defender-antivirus.md).

## <a name="sample-submission-settings"></a>Exemples de paramètres de soumission

En plus de configurer votre niveau de protection cloud, vous pouvez configurer vos paramètres d’envoi d’exemples. Vous pouvez choisir parmi plusieurs options :

- **Envoyer automatiquement des échantillons sécurisés**  (comportement par défaut)
- **Envoyer tous les échantillons automatiquement**  
- **Ne pas envoyer d’exemples**  

Pour plus d’informations sur les options de configuration à l’aide d’Intune, configuration Manager, GPO ou PowerShell, voir Activer la [protection cloud dans Antivirus Microsoft Defender](enable-cloud-protection-microsoft-defender-antivirus.md).

## <a name="examples-of-metadata-sent-to-the-cloud-protection-service"></a>Exemples de métadonnées envoyées au service de protection cloud

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Figure 2. Exemples de métadonnées envoyées à Microsoft Defender Cloud Protection":::

Le tableau suivant répertorie des exemples de métadonnées envoyées pour analyse par la protection cloud :

| Type | Attribut |
|:---|:---|
| Attributs de l’ordinateur | `OS version` <br/> `Processor` <br/> `Security settings` |
| Attributs dynamiques et contextuels | **Processus et installation** <br/> `ProcessName` <br/> `ParentProcess` <br/> `TriggeringSignature` <br/> `TriggeringFile` <br/> `Download IP and url` <br/> `HashedFullPath` <br/> `Vpath` <br/> `RealPath` <br/> `Parent/child relationships` <br/><br/>**Comportement** <br/> `Connection IPs` <br/> `System changes` <br/> `API calls` <br/> `Process injection` <br/><br/>**Locale** <br/> `Locale setting` <br/> `Geographical location` |
| Attributs de fichier statique | **Hashes partiels et complets** <br/> `ClusterHash` <br/> `Crc16` <br/> `Ctph` <br/> `ExtendedKcrcs` <br/> `ImpHash` <br/> `Kcrc3n` <br/> `Lshash` <br/> `LsHashs` <br/> `PartialCrc1` <br/> `PartialCrc2` <br/> `PartialCrc3` <br/> `Sha1` <br/> `Sha256` <br/><br/>**Propriétés de fichier** <br/>`FileName` <br/> `FileSize` <br/><br/> **Informations sur le signataire** <br/> `AuthentiCodeHash` <br/> `Issuer` <br/> `IssuerHash` <br/> `Publisher` <br/> `Signer` <br/> `SignerHash` |

## <a name="samples-are-treated-as-customer-data"></a>Les exemples sont traités comme des données client

Juste au cas où vous vous demanderiez ce qu’il advient des soumissions d’exemples, Defender for Endpoint traite tous les exemples de fichiers comme des données client. Microsoft honore les choix géographiques et de rétention des données que votre organisation a sélectionnés lors de l’intégration à Defender for Endpoint. 

En outre, Defender pour point de terminaison a reçu plusieurs certifications de conformité, ce qui démontre l’adhésion continue à un ensemble sophistiqué de contrôles de conformité :

- ISO 27001
- ISO 27018
- SOC I, II, III
- et PCI

Pour plus d’informations, reportez-vous aux ressources suivantes :

- [Offres de conformité Azure](/azure/storage/common/storage-compliance-offerings) 
- [Portail d’approbation de service](https://servicetrust.microsoft.com)
- [Microsoft Defender pour le stockage et la confidentialité des données des points de terminaison](data-storage-privacy.md#data-storage-location)

## <a name="other-file-sample-submission-scenarios"></a>Autres scénarios d’envoi d’exemples de fichiers

Il existe deux autres scénarios dans lequel Defender pour point de terminaison peut demander un exemple de fichier qui n’est pas lié à la protection cloud dans Antivirus Microsoft Defender. Ces scénarios sont décrits dans le tableau suivant :

| Scénario | Description |
|:---|:---|
|Collection d’exemples de fichiers manuelle dans le portail Microsoft 365 Defender web | Lors de l’intégration d’appareils à Defender pour endpoint, vous pouvez configurer les paramètres de [protection évolutive des points de terminaison (PEPT)](overview-endpoint-detection-response.md). Par exemple, il existe un paramètre permettant d’activer des exemples de collections à partir de l’appareil, qui peuvent facilement être confondus avec les paramètres d’envoi d’exemples décrits dans cet article. <br/><br/>Le paramètre PEPT contrôle la collecte d’exemples de fichiers à partir d’appareils lorsqu’il est demandé via le portail Microsoft 365 Defender et est soumis aux rôles et autorisations déjà établis. Ce paramètre peut autoriser ou bloquer la collecte de fichiers à partir du point de terminaison pour des fonctionnalités telles que l’analyse approfondie dans Microsoft 365 Defender portail. Si ce paramètre n’est pas configuré, la valeur par défaut est d’activer la collection d’échantillons. <br/><br/>En savoir plus sur les paramètres de configuration de Defender pour les points de terminaison, voir : Outils et méthodes d’intégration pour les Windows 10 [dans Defender for Endpoint](configure-endpoints.md) |
| Analyse automatisée du contenu d’examen et de réponse | Lorsque des [enquêtes](automated-investigations.md) automatisées sont en cours d’exécution sur des appareils (lorsqu’elles sont configurées pour s’exécuter automatiquement en réponse à une alerte ou s’exécutent manuellement), les fichiers identifiés comme suspects peuvent être collectés à partir des points de terminaison pour une inspection plus approfondie. Si nécessaire, la fonctionnalité d’analyse de contenu de fichier pour les examens automatisés peut être désactivée dans Microsoft 365 Defender portail. <br/><br/> Les noms d’extension de fichier peuvent également être modifiés pour ajouter ou supprimer des extensions pour d’autres types de fichiers qui seront automatiquement envoyés au cours d’un examen automatisé. <br/><br/> Pour plus d’informations, voir [Gérer les téléchargements de fichiers d’automatisation.](manage-automation-file-uploads.md) |

## <a name="see-also"></a>Voir aussi

[Vue d’ensemble de la protection nouvelle génération](next-generation-protection.md)
