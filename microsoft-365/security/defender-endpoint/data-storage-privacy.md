---
title: Microsoft Defender pour le stockage et la confidentialité des données des points de terminaison
description: Découvrez comment Microsoft Defender pour point de terminaison gère la confidentialité et les données qu’il collecte.
keywords: Microsoft Defender pour le point de terminaison, stockage et confidentialité des données, stockage, confidentialité, gestion des licences, géolocalisation, rétention des données, données
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 70607eb90fa6c1614ed10e90e4d6ee9cf36f7204
ms.sourcegitcommit: 87d994407fb69a747239b8589ad11ddf9b47e527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2021
ms.locfileid: "53595701"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Microsoft Defender pour le stockage et la confidentialité des données des points de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

Cette section traite de certaines des questions les plus fréquemment posées concernant la confidentialité et la gestion des données pour Defender for Endpoint.

> [!NOTE]
> Ce document explique les détails relatifs au stockage des données et à la confidentialité relatifs à Defender for Endpoint. Pour plus d’informations sur Defender for Endpoint et d’autres produits et services tels que Antivirus Microsoft Defender et Windows 10, voir déclaration de confidentialité [Microsoft.](https://go.microsoft.com/fwlink/?linkid=827576) Consultez également [Windows 10 FAQ sur la confidentialité](https://go.microsoft.com/fwlink/?linkid=827577) pour plus d’informations.

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Quelles données Microsoft Defender for Endpoint collecte-t-il ?

Microsoft Defender pour le point de terminaison collecte et stocke des informations à partir de vos appareils configurés dans un client dédié et séparé propre au service à des fins d’administration, de suivi et de rapport.

Les informations collectées comprennent les données de fichier (telles que les noms de fichiers, les tailles et les hages), les données de processus (processus en cours d’exécution, hèses), les données de Registre, les données de connexion réseau (IPS et ports hôtes) et les détails de l’appareil (tels que les identificateurs de périphérique, les noms et la version du système d’exploitation).

Microsoft stocke ces données en toute sécurité Microsoft Azure et les maintient conformément aux pratiques de confidentialité de Microsoft et aux stratégies du Centre de [gestion de la confidentialité Microsoft.](https://go.microsoft.com/fwlink/?linkid=827578)

Ces données permettent à Defender for Endpoint de :

- Identifier de manière proactive les indicateurs d’attaque dans votre organisation
- Générer des alertes si une attaque possible a été détectée
- Fournissez à vos opérations de sécurité une vue des appareils, des fichiers et des URL liés aux signaux de menace de votre réseau, ce qui vous permet d’examiner et d’explorer la présence de menaces de sécurité sur le réseau.

Microsoft n’utilise pas vos données pour la publicité.

## <a name="data-protection-and-encryption"></a>Protection et chiffrement des données

Le service Defender for Endpoint utilise des technologies de protection des données de pointe basées sur Microsoft Azure infrastructure.

Il existe différents aspects pertinents pour la protection des données que notre service prend en charge. Le chiffrement est l’un des plus critiques et inclut le chiffrement des données au repos, le chiffrement en cours d’utilisation et la gestion des clés avec le coffre de clés. Pour plus d’informations sur les autres technologies utilisées par le service Defender for Endpoint, consultez la vue d’ensemble du [chiffrement Azure.](/azure/security/security-azure-encryption-overview)

Dans tous les scénarios, les données sont chiffrées au minimum à l’aide du chiffrement [AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) 256 bits.

## <a name="data-storage-location"></a>Emplacement de stockage de données

Defender for Endpoint fonctionne dans les centres Microsoft Azure de données de l’Union européenne, du Royaume-Uni ou des États-Unis. Les données client collectées par le service peuvent être stockées dans : (a) l’emplacement géographique du client identifié lors de l’approvisionnement ou, (b) si Defender for Endpoint utilise un autre service en ligne Microsoft pour traiter ces données, la géolocalisation telle que définie par les règles de stockage de données de cet autre service en ligne.

Les données client sous forme pseudonyme peuvent également être stockées dans les systèmes de stockage et de traitement centraux aux États-Unis.

Une fois configuré, vous ne pouvez pas modifier l’emplacement où vos données sont stockées. Cela permet de réduire au minimum les risques de conformité en sélectionnant activement les emplacements géographiques où vos données résideront.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Mes données sont-elles isolées des autres données client ?

Oui, vos données sont isolées par l’authentification d’accès et la séparation logique basée sur l’identificateur client. Chaque client peut uniquement accéder aux données collectées à partir de sa propre organisation et aux données génériques que Microsoft fournit.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Comment Microsoft empêche-t-il les activités malveillantes internes et les abus des rôles à privilège élevé ?

Les développeurs et les administrateurs Microsoft ont, par conception, reçu des privilèges suffisants pour exécuter leurs tâches affectées afin d’exploiter et de faire évoluer le service. Microsoft déploie des combinaisons de contrôles de prévention, de surveillance et réactifs, y compris les mécanismes suivants pour vous protéger contre les activités non autorisées des développeurs et/ou des administrations :

- Contrôle d’accès étroit aux données sensibles
- Combinaisons de contrôles qui améliorent grandement la détection indépendante des activités malveillantes
- Plusieurs niveaux de surveillance, de journalisation et de rapport

En outre, Microsoft effectue des vérifications en arrière-plan de certains membres du personnel opérationnel et limite l’accès aux applications, aux systèmes et à l’infrastructure réseau en proportion du niveau de vérification en arrière-plan. Le personnel opérationnel suit un processus formel lorsqu’il est requis d’accéder au compte d’un client ou à des informations connexes dans l’exécution de ses tâches.

L’accès aux données pour les services déployés dans les centres de données publics Microsoft Azure est accordé uniquement au personnel opérationnel qui a été filtrer et approuvé pour gérer les données soumises à certaines réglementations et exigences gouvernementales, telles que FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 et CJIS.

## <a name="is-data-shared-with-other-customers"></a>Les données sont-elles partagées avec d’autres clients ?

Non. Les données client sont isolées des autres clients et ne sont pas partagées. Toutefois, les informations sur les données résultant du traitement par Microsoft et qui ne contiennent pas de données spécifiques au client peuvent être partagées avec d’autres clients. Chaque client peut uniquement accéder aux données collectées à partir de sa propre organisation et aux données génériques que Microsoft fournit.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Combien de temps Microsoft stockera-t-il mes données ? Qu’est-ce que la stratégie de rétention des données de Microsoft ?

### <a name="at-service-onboarding"></a>Intégration au service

Par défaut, les données sont conservées pendant 180 jours . toutefois, vous pouvez spécifier la stratégie de rétention des données pour vos données. Cela détermine la durée pendant combien de temps Window Defender pour Endpoint stockera vos données. Vous avez la possibilité de choisir entre un mois et six mois pour répondre aux besoins de conformité réglementaire de votre entreprise.

### <a name="at-contract-termination-or-expiration"></a>À la résiliation ou à l’expiration du contrat

Vos données seront conservées et disponibles pendant la période de grâce ou le mode suspendu de la licence. À la fin de cette période, ces données seront effacées des systèmes de Microsoft pour les rendre irrécables, au plus tard 180 jours après la résiliation ou l’expiration du contrat.

### <a name="advanced-hunting-data"></a>Données de recherche avancée

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Microsoft peut-il nous aider à maintenir la conformité réglementaire ?

Microsoft fournit aux clients des informations détaillées sur les programmes de sécurité et de conformité de Microsoft, notamment des rapports d’audit et des packages de conformité, pour aider les clients à évaluer Defender pour les services Endpoint par rapport à leurs propres exigences légales et réglementaires. Defender pour le point de terminaison a obtenu un certain nombre de certifications, notamment ISO, SOC, FedRAMP High et PCI, et continue à poursuivre des certifications nationales, régionales et spécifiques au secteur.

En fournissant aux clients des services conformes et vérifiés de manière indépendante, Microsoft leur permet de se conformer plus facilement à l’infrastructure et aux applications qu’ils exécutent.

Pour plus d’informations sur les rapports de certification Defender for Endpoint, consultez [le Centre de confiance Microsoft.](https://servicetrust.microsoft.com/) 

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-datastorage-belowfoldlink)
