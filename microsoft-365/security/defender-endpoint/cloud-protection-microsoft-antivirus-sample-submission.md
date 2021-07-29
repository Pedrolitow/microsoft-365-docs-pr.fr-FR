---
title: Protection fournie par le cloud Microsoft Defender Antivirus soumission d'échantillons
description: En savoir plus sur la protection et les Antivirus Microsoft Defender
keywords: Antivirus Microsoft Defender, technologies de nouvelle génération, soumission d’exemples antivirus, antivirus de nouvelle génération, machine learning, anti-programme malveillant, sécurité, defender, cloud, protection cloud
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
author: jweston-1
ms.author: v-jweston
ms.reviewer: shwjha
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.date: 07/22/2021
ms.openlocfilehash: 2d30777754f05b46336e28c237b2264cef6ac802
ms.sourcegitcommit: 3576c2fee77962b516236cb67dd3df847d61c527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/28/2021
ms.locfileid: "53622279"
---
# <a name="cloud-delivered-protection-antivirus-sample-submission"></a>Soumission d’exemples d’antivirus de protection dans le cloud

Microsoft Defender pour l’Antivirus de point de terminaison (antivirus Defender for Endpoint) utilise de nombreux mécanismes intelligents pour détecter les programmes malveillants. L’une des fonctionnalités les plus puissantes est la possibilité d’appliquer la puissance du cloud pour détecter les programmes malveillants. Defender for Endpoint antivirus Cloud Protection fonctionne avec l’antivirus Defender for Endpoint sur le point de terminaison pour prendre des décisions et protéger les points de terminaison contre les menaces nouvelles et émergentes.

## <a name="microsoft-defender-for-endpoint-antivirus-cloud-protection-overview"></a>Vue d’ensemble de la protection cloud de l’antivirus Microsoft Defender pour les points de terminaison

La protection cloud est activée par défaut dans Defender pour l’Antivirus Endpoint. Il est recommandé que les clients ne désactivent pas la protection cloud dans Defender pour l’antivirus endpoint.  Lorsque la protection cloud est activée, vous avez la possibilité de configurer les informations que l’antivirus Defender for Endpoint fournira au cloud (y compris la soumission d’exemples). La protection cloud est utile lorsqu’une détermination à haut niveau de confiance ne peut pas être prise en fonction d’autres caractéristiques.
La configuration de l’exemple de soumission pose des questions sur son fonctionnement . par exemple, comment les données sont stockées et utilisées. Les trois options d’envoi d’exemples de protection cloud qui posent le plus de questions sont les suivantes :

- « Envoyer automatiquement des échantillons sécurisés » (comportement par défaut)
- « Envoyer tous les échantillons automatiquement »,  
- « N’envoyez pas d’exemples. »  

Pour plus d’informations sur les options de configuration à l’aide d’Intune, configuration Manager, GPO ou PowerShell, voir Activer la protection cloud dans [Antivirus Microsoft Defender](/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus).  

## <a name="customer-data-cloud-protection-and-sample-submission"></a>Données client, protection cloud et soumission d’exemples

Lors de l’intégration à Defender pour le point de terminaison, Defender pour le point de terminaison traite tous les exemples de fichiers comme des données client, respectant les choix de rétention géographique et de données sélectionnés par le client. Les choix de rétention géographique et de données sont décrits ici : Microsoft Defender pour le stockage et la confidentialité des données [de point de terminaison.](/security/defender-endpoint/data-storage-privacy#data-storage-location)
Le produit a reçu plusieurs certifications de conformité, montrant qu’il est toujours conforme à un ensemble sophistiqué de contrôles de conformité :

- ISO 27001
- ISO 27018
- SOC I, II, III
- et PCI

[Les offres de conformité Azure](/azure/compliance/#compliance-offerings) fournissent plus d’informations sur ces certifications. Tous les artefacts de certification pour Microsoft Defender pour [](https://servicetrust.microsoft.com/) le point de terminaison se trouvent sur le portail d’autorisation des services de Microsoft dans chacun des rapports de certification Azure associés.

## <a name="cloud-protection-mechanisms"></a>Mécanismes de protection cloud

La sécurité intelligente de Microsoft Graph les données sur les menaces à partir d’un vaste réseau de capteurs. Nous superposons les modèles d’apprentissage automatique basés sur le cloud qui peuvent effectuer une évaluation basée sur les signaux du client et le vaste réseau de capteurs et de données dans la sécurité intelligente Graph. Ce modèle offre à Defender for Endpoint la possibilité de bloquer de nombreuses menaces jamais vues.

Defender for Endpoint antivirus and cloud protection automatically blocks most new, never-before-seen threats at first sight using the following methods:

1. Modèles d’apprentissage automatique légers basés sur le client, bloquant les programmes malveillants nouveaux et inconnus.

2. Analyse comportementale locale, arrêt des attaques basées sur des fichiers et sans fichier.

3. Antivirus de haute précision, détectant les programmes malveillants courants par le biais de techniques génériques et heuristiques.

4. Une protection avancée basée sur le cloud est fournie dans les cas où l’antivirus Defender for Endpoint en cours d’exécution sur le point de terminaison a besoin d’une plus grande intelligence pour vérifier l’intention d’un fichier suspect.

   1. Dans le cas où l’antivirus Microsoft Defender pour le point de terminaison ne peut pas effectuer une détermination claire, les métadonnées de fichier sont envoyées au service de protection cloud. En règle générale, le service de protection cloud peut déterminer si le fichier est sûr ou malveillant, en quelques millisecondes.  
      - La requête cloud de métadonnées de fichier peut être le résultat d’un comportement, d’une marque du site web ou d’autres caractéristiques dans le cas où un verdict clair n’est pas déterminé.
      - Une charge utile de métadonnées de petite taille est envoyée, dans le but d’atteindre un verdict clean vs malware
      - Les métadonnées peuvent inclure des attributs PE, des attributs de fichiers statiques, des attributs dynamiques et contextuels, et bien plus encore (figure 1).
      - N’inclut pas les informations d’identification personnelle (PII). Les informations telles que les noms de fichiers sont hachées
      - Peut être synchrone ou asynchrone. Pour synchrone, le fichier ne s’ouvre pas tant que le cloud n’a pas rendu de verdict. Pour les données asynchrones, le fichier s’ouvre pendant que le cloud effectue son analyse.

   2. Après avoir examiné les métadonnées, si la protection cloud de l’antivirus Defender for Endpoint ne peut pas atteindre un verdict de première classe, elle peut demander un échantillon du fichier pour une inspection plus approfondie. Cette demande honore la configuration des paramètres pour l’envoi d’exemples :

      1. **Envoyer automatiquement des échantillons sûrs** (par défaut)
         - Coffre exemples sont des exemples considérés comme ne contenant pas fréquemment des données d’informations d'.bat, .scr, .dll, .exe.
         - Si le fichier est susceptible de contenir des pii, l’utilisateur reçoit une demande d’autoriser l’envoi d’exemples de fichier.
         - Il s’agit de la valeur par défaut sur Windows, macOS et Linux.

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

   3. Une fois les métadonnées et/ou les fichiers envoyés au cloud Defender for Endpoint, vous pouvez utiliser des **exemples,** des **détonations** ou des modèles d’apprentissage automatique d’analyse de **big data** pour parvenir à un verdict. Ce modèle est illustré dans la figure 3. La fonctionnalité De protection fournie par le cloud limite l’analyse à ce que le client peut fournir par le biais de modèles d’apprentissage automatique locaux et de fonctions similaires.

_Figure 1 - Exemples de métadonnées envoyées à Microsoft Defender Cloud Protection_

:::image type="content" source="images/cloud-protection-metadata-sample.png" alt-text="Figure 1. Exemples de métadonnées envoyées à Microsoft Defender Cloud Protection":::

_Figure 2. Flux de protection cloud_

:::image type="content" source="images/cloud-protection-flow.png" alt-text="Figure 2. Flux de protection cloud":::

_Figure 3. Protection cloud et apprentissage automatique en couches_

:::image type="content" source="images/cloud-protection-detection-layered-machine-learning.png" lightbox="images/cloud-protection-detection-layered-machine-learning.png" alt-text="Figure 3. Protection cloud et apprentissage automatique en couches":::

> [!Note]
>
> Vous avez peut-être également entendu l’expression « Bloquer à la première vue (BAFS). » BAFS fait référence à l’analyse plus approfondie que le cloud peut fournir, y compris des éléments tels que la détonation pour fournir un verdict plus précis. Cela peut également inclure le retard d’ouverture d’un fichier en cours d’interrogation par la protection cloud jusqu’à ce qu’un verdict soit atteint. Si vous désactivez l'« envoi d’exemples », BAFS est désactivé, et vous ne pouvez pas faire l’analyse la plus complète et êtes limité à l’analyse des métadonnées de fichier uniquement.

## <a name="cloud-delivered-protection-levels"></a>Niveaux de protection cloud

La détection de programmes malveillants nécessite un équilibre entre fournir la protection la plus forte possible, tout en réduisant le nombre de faux positifs. Différents environnements peuvent avoir une tolérance de protection par rapport au risque de faux positifs. Les niveaux de protection cloud permettent au client de définir le niveau de tolérance approprié pour l’environnement spécifique. Lorsque vous activez la protection fournie par le cloud, le niveau de protection est automatiquement configuré pour fournir une détection forte sans augmenter le risque de détection de fichiers légitimes. Si vous souhaitez configurer un niveau de protection différent, voir [Spécifier](/security/threat-protection/microsoft-defender-antivirus/specify-cloud-protection-level-microsoft-defender-antivirus)le niveau de protection livré par le cloud pour Antivirus Microsoft Defender .  

> [!Note]
>
> La modification du niveau de protection peut entraîner un niveau plus élevé de faux positifs et doit être évaluée avec soin avant de changer.

## <a name="other-file-sample-submission-scenarios"></a>Autres scénarios d’envoi d’exemples de fichiers

Il existe deux autres scénarios dans lequel Defender pour le point de terminaison peut demander un exemple de fichier non lié aux paramètres de protection cloud mentionnés ci-dessus.  

### <a name="manual-file-sample-collection-by-security-admin-from-defender-for-endpoint-management-portal"></a>Collecte manuelle d’exemples de fichiers par l’administrateur de sécurité à partir de Defender pour le portail de gestion des points de terminaison

Lors de l’intégration d’appareils à Microsoft Defender pour endpoint PEPT il existe un paramètre permettant d’activer des exemples de collections à partir de l’appareil, qui peuvent être confondus avec les paramètres mentionnés ci-dessus. Ce paramètre contrôle la collecte d’exemples de fichiers à partir d’appareils lorsque cela est demandé via le portail d’administration defender pour point de terminaison . il est soumis aux rôles et autorisations déjà établis. Ce paramètre peut autoriser ou bloquer la collecte de fichiers à partir du point de terminaison pour des fonctionnalités telles que l’analyse approfondie dans le portail Defender for Endpoint. Si ce paramètre n’est pas configuré, la valeur par défaut est d’activer la collection d’échantillons.

[Autres paramètres de configuration de Defender pour les points de terminaison Paramètres](/configure-endpoints#additional-defender-for-endpoint-configuration-settings)

### <a name="automated-investigation-and-response-content-analysis"></a>Analyse automatisée du contenu d’examen et de réponse

Lorsque des enquêtes automatisées sont en cours d’exécution sur des appareils (lorsqu’elles sont configurées pour s’exécuter automatiquement en réponse à une alerte ou s’exécutent manuellement), les fichiers identifiés comme suspects peuvent être collectés à partir des points de terminaison pour une inspection plus approfondie. La fonctionnalité d’analyse de contenu de fichier pour les examens automatisés peut être désactivée dans le portail Defender for Endpoint. Les noms d’extension de fichier peuvent également être modifiés pour ajouter ou supprimer des extensions pour d’autres types de fichiers qui seront automatiquement envoyés au cours d’un examen automatisé.

[Gérer les chargements du fichier d’automatisation](/manage-automation-file-uploads)
