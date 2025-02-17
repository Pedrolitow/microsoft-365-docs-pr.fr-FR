---
title: Étape 6. Identifier les tâches de maintenance SOC
description: Identifiez les tâches de maintenance SOC lors de l’intégration de Microsoft 365 Defender dans vos opérations de sécurité.
keywords: incidents, alertes, examiner, corrélation, attaque, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque, étendues, opérations de sécurité, soc
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-m365dsecops
- tier2
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: b3d3df2fe96b0af79cafcaf5a7979d0c491bc816
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68092556"
---
# <a name="step-6-identify-soc-maintenance-tasks"></a>Étape 6. Identifier les tâches de maintenance SOC

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Voici les tâches périodiques ou nécessaires pour gérer votre SOC pour Microsoft 365 Defender.

|Activité|Description|Cadence|Équipe affectée|
|---|---|---|---|
|Collaboration d’administration de service avec SOC Teams|Administration des services périphériques tels que le suivi des ressources (CMDB), les licences d’application (nouvelles licences SaaS), les achats d’appareils (mises à niveau ou renouvellement des déploiements d’appareils) et d’autres modifications à l’échelle du client Microsoft 365 (Intune, Microsoft 365, etc.) susceptibles d’affecter le déploiement de produits Microsoft 365 Defender.|Hebdomadaire et selon les besoins|Ingénierie & SecOps|
|Mettre à jour les campagnes de protection contre le hameçonnage et la perte de données|Incorporez le cas d’utilisation soc et les leçons apprises auprès de l’organisation étendue (RH, juridique, formation, etc.).|Mensuellement et en fonction des besoins|Surveillance SOC|
|Déployer des scripts et des services d’automatisation, le cas échéant|Téléchargez et testez des scripts d’automatisation et des fichiers de configuration à partir de sites Microsoft approuvés pour améliorer Microsoft 365 Defender opérations.|Hebdomadaire et selon les besoins|Ingénierie et SecOps|
|Gestion du portail ou des licences|Vérifiez les annonces et le Centre Messages Microsoft pour Microsoft 365 Defender portail ou les besoins en matière de licences en fonction des mises à jour et des nouvelles fonctionnalités de Microsoft.|En semaines|Surveillance SOC|
|Mettre à jour les tickets d’escalade SOC|Toutes les équipes SOC mettent à jour les tickets d’escalade (tels que sentinel, tickets ServiceNow) qui leur sont attribués.|Journalière|Toutes les équipes SOC|
|Suivre l’activité de correction Gestion des vulnérabilités Microsoft Defender (MDVM)|Générez l’activité de correction du degré de sécurisation de la machine virtuelle MDVM et signalez-le aux propriétaires d’actifs via un portail intranet.|Journalière|Analyse|
|Générer un rapport de degré de sécurisation|L’équipe de supervision effectue le suivi et signale les améliorations du degré de sécurisation.|SOC hebdomadaire|Analyse|
|Exécuter l’exercice tabletop IR|Testez les playbooks d’équipe SOC dans l’exercice tabletop.|Selon vos besoins|Toutes les équipes SOC|

Intégrez ces tâches à vos processus SOC actuels.

## <a name="next-steps"></a>Prochaines étapes

Vous devez consulter les guides mentionnés dans ce contenu et dans la [bibliothèque Microsoft 365 Defender](/microsoft-365/security/defender) pour déterminer comment votre propre implémentation de Microsoft 365 Defender doit être structurée et intégrée.
