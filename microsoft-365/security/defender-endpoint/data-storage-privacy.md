---
title: Microsoft Defender pour point de terminaison le stockage et la confidentialité des données
description: Découvrez comment Microsoft Defender pour point de terminaison gère la confidentialité et les données qu’il collecte.
keywords: Microsoft Defender pour point de terminaison, stockage et confidentialité des données, stockage, confidentialité, licences, géolocalisation, conservation des données, données
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 07b3ebb00001570bdfbde705c6eca5a84a660172
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68195366"
---
# <a name="microsoft-defender-for-endpoint-data-storage-and-privacy"></a>Microsoft Defender pour point de terminaison le stockage et la confidentialité des données

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

Cette section aborde certaines des questions les plus fréquemment posées sur la confidentialité et la gestion des données pour Defender pour point de terminaison.

> [!NOTE]
> Ce document explique les détails sur le stockage des données et la confidentialité liés à Defender pour point de terminaison. Pour plus d’informations sur Defender pour point de terminaison et d’autres produits et services tels que Microsoft Defender Antivirus et Windows, consultez [la Déclaration de confidentialité Microsoft](https://go.microsoft.com/fwlink/?linkid=827576). Pour plus d’informations, consultez également [la FAQ sur la confidentialité de Windows](https://go.microsoft.com/fwlink/?linkid=827577) .

## <a name="what-data-does-microsoft-defender-for-endpoint-collect"></a>Quelles sont les données collectées par Microsoft Defender pour point de terminaison ?

Microsoft Defender pour point de terminaison collecte et stocke des informations à partir de vos appareils configurés dans un client dédié et distinct propre au service à des fins d’administration, de suivi et de création de rapports.

Les informations collectées incluent les données de fichier (telles que les noms de fichiers, les tailles et les hachages), les données de processus (processus en cours d’exécution, hachages), les données de Registre, les données de connexion réseau (adresses IP et ports hôtes) et les détails de l’appareil (tels que les identificateurs d’appareil, les noms et la version du système d’exploitation).

Microsoft stocke ces données en toute sécurité dans Microsoft Azure et les gère conformément aux pratiques de confidentialité de Microsoft et aux [stratégies du Centre de gestion de la confidentialité Microsoft](https://go.microsoft.com/fwlink/?linkid=827578).

Ces données permettent à Defender pour point de terminaison de :

- Identifier de manière proactive les indicateurs d’attaque (IOA) dans votre organisation
- Générer des alertes si une attaque possible a été détectée
- Fournissez à vos opérations de sécurité une vue des appareils, fichiers et URL liés aux signaux de menace de votre réseau, ce qui vous permet d’examiner et d’explorer la présence de menaces de sécurité sur le réseau.

Microsoft n’utilise pas vos données pour la publicité.

## <a name="data-protection-and-encryption"></a>Protection et chiffrement des données

Le service Defender pour point de terminaison utilise des technologies de protection des données de pointe basées sur l’infrastructure Microsoft Azure.

Notre service s’occupe de divers aspects liés à la protection des données. Le chiffrement est l’un des plus critiques et inclut le chiffrement des données au repos, le chiffrement en vol et la gestion des clés avec Key Vault. Pour plus d’informations sur les autres technologies utilisées par le service Defender pour point de [terminaison, consultez la vue d’ensemble du chiffrement Azure](/azure/security/security-azure-encryption-overview).

Dans tous les scénarios, les données sont chiffrées à l’aide du [chiffrement AES](https://en.wikipedia.org/wiki/Advanced_Encryption_Standard) 256 bits au minimum.

## <a name="data-storage-location"></a>Emplacement de stockage de données

Defender pour point de terminaison fonctionne dans les centres de données Microsoft Azure dans l’Union européenne, au Royaume-Uni ou dans le États-Unis. Les données client collectées par le service peuvent être stockées dans : (a) l’emplacement géographique du locataire tel qu’identifié lors de l’approvisionnement ou, (b) si Defender pour point de terminaison utilise un autre service en ligne Microsoft pour traiter ces données, la géolocalisation telle que définie par les règles de stockage des données de cet autre service en ligne.

Les données client sous forme pseudonyme peuvent également être stockées dans les systèmes de stockage et de traitement centraux du États-Unis.

Une fois configuré, vous ne pouvez pas modifier l’emplacement où vos données sont stockées. Cela offre un moyen pratique de réduire les risques de conformité en sélectionnant activement les emplacements géographiques où vos données résideront.

## <a name="is-my-data-isolated-from-other-customer-data"></a>Mes données sont-ils isolées des autres données client ?

Oui, vos données sont isolées par le biais de l’authentification d’accès et de la séparation logique en fonction de l’identificateur du client. Chaque client peut uniquement accéder aux données collectées à partir de sa propre organisation et des données génériques fournies par Microsoft.

## <a name="how-does-microsoft-prevent-malicious-insider-activities-and-abuse-of-high-privilege-roles"></a>Comment Microsoft empêche-t-il les activités internes malveillantes et l’abus de rôles à privilèges élevés ?

Les développeurs et administrateurs Microsoft disposent, par conception, de privilèges suffisants pour s’acquitter de leurs tâches affectées afin d’exploiter et de faire évoluer le service. Microsoft déploie des combinaisons de contrôles préventifs, de détection et réactifs, notamment les mécanismes suivants pour vous protéger contre les activités de développement et/ou d’administration non autorisées :

- Contrôle d’accès serré aux données sensibles
- Combinaisons de contrôles qui améliorent considérablement la détection indépendante des activités malveillantes
- Plusieurs niveaux de surveillance, de journalisation et de création de rapports

En outre, Microsoft effectue des vérifications en arrière-plan de certains membres du personnel des opérations et limite l’accès aux applications, aux systèmes et à l’infrastructure réseau en proportion du niveau de vérification en arrière-plan. Le personnel des opérations suit un processus formel lorsqu’il est tenu d’accéder au compte d’un client ou à des informations connexes dans l’exercice de ses fonctions.

L’accès aux données des services déployés dans les centres de données Microsoft Azure Government est accordé uniquement au personnel d’exploitation qui a été filtré et approuvé pour gérer les données soumises à certaines réglementations et exigences gouvernementales, telles que FedRAMP, NIST 800.171 (DIB), ITAR, IRS 1075, DoD L4 et CJIS.

## <a name="is-data-shared-with-other-customers"></a>Les données sont-ils partagées avec d’autres clients ?

Non. Les données client sont isolées des autres clients et ne sont pas partagées. Toutefois, les insights sur les données résultant du traitement Microsoft, et qui ne contiennent pas de données spécifiques au client, peuvent être partagés avec d’autres clients. Chaque client peut uniquement accéder aux données collectées à partir de sa propre organisation et des données génériques fournies par Microsoft.

## <a name="how-long-will-microsoft-store-my-data-what-is-microsofts-data-retention-policy"></a>Combien de temps Microsoft stockera-t-il mes données ? Quelle est la stratégie de rétention des données de Microsoft ?

### <a name="at-service-onboarding"></a>Lors de l’intégration de service

Par défaut, les données sont conservées pendant 180 jours ; toutefois, vous pouvez spécifier la stratégie de rétention des données pour vos données. Cela détermine la durée pendant laquelle Microsoft Defender pour point de terminaison stockerez vos données. Il existe une possibilité de choisir entre un mois et six mois pour répondre aux besoins de conformité réglementaire de votre entreprise.

### <a name="at-contract-termination-or-expiration"></a>À la résiliation ou à l’expiration du contrat

Vos données seront conservées et seront disponibles pendant que la licence est en période de grâce ou en mode suspendu. À la fin de cette période, ces données seront effacées des systèmes de Microsoft pour les rendre irrécupéables, au plus tard 180 jours après la résiliation ou l’expiration du contrat.

### <a name="advanced-hunting-data"></a>Données de chasse avancées

Le repérage avancé est un outil de repérage de menaces basé sur des requêtes qui vous permet d’explorer jusqu’à 30 jours de données brutes.

## <a name="can-microsoft-help-us-maintain-regulatory-compliance"></a>Microsoft peut-il nous aider à maintenir la conformité réglementaire ?

Microsoft fournit aux clients des informations détaillées sur les programmes de sécurité et de conformité de Microsoft, notamment les rapports d’audit et les packages de conformité, afin d’aider les clients à évaluer defender pour les services de point de terminaison par rapport à leurs propres exigences légales et réglementaires. Defender pour point de terminaison a obtenu un certain nombre de certifications, notamment ISO, SOC, FedRAMP High et PCI, et continue de poursuivre des certifications nationales, régionales et spécifiques à l’industrie.

En fournissant aux clients des services conformes et vérifiés indépendamment, Microsoft permet aux clients d’obtenir plus facilement la conformité de l’infrastructure et des applications qu’ils exécutent.

Pour plus d’informations sur les rapports de certification Defender pour point de terminaison, consultez [le Centre de gestion de la confidentialité Microsoft](https://servicetrust.microsoft.com/). 

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-datastorage-belowfoldlink)
