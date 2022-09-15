---
title: Étape 6. Surveiller les risques et la conformité des appareils aux bases de référence de sécurité
ms.author: bcarter
author: brendacarter
f1.keywords:
- connect Intune to Defender
- monitor device risk
- monitor device compliance
- deploy security baselines
manager: dougeby
audience: ITPro
description: Découvrez comment connecter Microsoft Intune à Defender pour point de terminaison et surveiller le risque de l’appareil en tant que condition d’accès.
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- highpri
- M365-security-compliance
- deploy security baselines
- m365solution-managedevices
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
keywords: ''
ms.openlocfilehash: 10b6e23042b777e2e747899999b093bd7d26e689
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67730724"
---
# <a name="step-6-monitor-device-risk-and-compliance-to-security-baselines"></a>Étape 6. Surveiller les risques et la conformité des appareils aux bases de référence de sécurité

Une fois que votre organisation a déployé Microsoft Defender pour point terminaison, vous pouvez obtenir des informations et une protection plus étendues de vos appareils en intégrant Microsoft Intune à Microsoft Defender pour point de terminaison. Pour les appareils mobiles, cela inclut la possibilité de surveiller les risques des appareils en tant que condition d’accès. Pour les appareils Windows, vous pouvez surveiller la conformité de ces appareils aux lignes de base de sécurité. 

Le déploiement de Microsoft Defender pour point de terminaison inclut l’intégration de points de terminaison. Si vous avez utilisé Intune pour intégrer des points de terminaison (recommandé), vous avez déjà connecté Microsoft Intune à Defender pour point de terminaison. Si vous avez utilisé une autre méthode pour intégrer des points de terminaison à Defender pour point de terminaison, consultez [Configuration de Microsoft Defender pour point de terminaison dans Intune](/mem/intune/protect/advanced-threat-protection-configure) pour vérifier que vous avez configuré la connexion de service à service entre Intune et Microsoft Defender pour point de terminaison. 


![Illustration de l’intégration de Defender pour point de terminaison et Microsoft Intune](../media/devices/devices-defender-for-endpoint-steps.png#lightbox)

Dans cette illustration :
- Microsoft Defender pour point de terminaison augmente considérablement la complexité de la protection contre les menaces pour les appareils. 
- Bien que Microsoft Intune vous permet de définir des stratégies de protection des applications et de gérer les appareils (y compris les modifications de configuration), Defender pour point de terminaison surveille en permanence vos appareils contre les menaces et peut prendre des mesures automatisées pour corriger les attaques. 
- Vous pouvez utiliser Intune pour intégrer des appareils à Defender pour point de terminaison. Dans ce cas, vous autorisez également ces appareils à utiliser la protection contre la perte de données de point de terminaison Microsoft Purview (Endpoint DLP).

Cet article comprend les étapes suivantes :
- Surveiller les risques des appareils
- Surveiller la conformité aux lignes de base de sécurité

Si Defender pour point de terminaison n’a pas encore été installé, travaillez avec l’administrateur de protection contre les menaces pour [configurer l’évaluation et l’environnement pilote](../security/defender/eval-defender-endpoint-overview.md). Vous pouvez travailler avec le groupe pilote pour tester les fonctionnalités de cet article.

## <a name="monitor-device-risk-as-a-condition-for-access"></a>Surveiller les risques des appareils comme condition d’accès

Une fois Microsoft Defender pour point de terminaison déployé, vous pouvez tirer parti des signaux de risque de menace. Cela vous permet de bloquer l’accès aux appareils en fonction de leur indice de risque. Microsoft recommande d’autoriser l’accès aux appareils avec un indice de risque moyen ou inférieur.

Pour Android et iOS/iPadOS, les signaux de menace peuvent être utilisés dans vos stratégies de protection des applications (APP). Pour plus d’informations sur cette configuration, voir [Créer et affecter une stratégie de protection des applications pour définir le niveau de risque de l’appareil](/mem/intune/protect/advanced-threat-protection-configure#create-and-assign-compliance-policy-to-set-device-risk-level).

Pour toutes les plateformes, vous pouvez définir le niveau de risque dans les stratégies existantes de conformité des appareils. Voir [Créer une stratégie d’accès conditionnel](/mem/intune/protect/advanced-threat-protection-configure#create-a-conditional-access-policy).

## <a name="deploy-security-baselines-and-monitor-compliance-to-these-settings"></a>Déployer les lignes de base de sécurité et surveiller la conformité à ces paramètres

S’applique à : Windows 10, Windows 11

L’article, [Étape 5. Déployer des profils de configuration](manage-devices-with-intune-configuration-profiles.md), recommande de commencer la prise en main des profils de configuration à l’aide des lignes de base de sécurité, disponibles pour Windows 10 et Windows 11. Microsoft Defender pour point de terminaison inclut également des lignes de base de sécurité fournissant des paramètres qui optimisent tous les contrôles de sécurité dans la pile Defender pour point de terminaison, y compris les paramètres de protection évolutive des points de terminaison (PEPT). Elles sont également déployées en utilisant Microsoft Intune.

Les appareils intégrés à Defender pour point de terminaison devraient être déployés sur les deux lignes de base : la ligne de base de sécurité Windows Intune pour sécuriser initialement Windows, puis la ligne de base de sécurité de Defender pour point de terminaison comme couche supplémentaire pour configurer de manière optimale les contrôles de sécurité Defender pour point de terminaison.

Pour tirer parti des données les plus récentes sur les risques et les menaces et réduire les conflits à mesure que les lignes de base évoluent, appliquez toujours les dernières versions des lignes de base sur tous les produits dès qu’elles sont publiées. 

L’utilisation de Defender pour point de terminaison vous permet de surveiller la conformité à ces lignes de base. 

![La carte de surveillance de la conformité aux lignes de base de sécurité](../media/devices/secconmgmt-baseline-card.png#lightbox)

Pour déployer les lignes de base de sécurité et surveiller la conformité à ces paramètres, suivez les étapes de ce tableau.


|Étape  |Description  |
|---------|---------|
|1     |Examinez les concepts clés et comparez Microsoft Defender pour point de terminaison et les linges de base de sécurité Windows Intune. <br><br>Pour plus d’informations sur les recommandations, voir [Augmenter la conformité à la ligne de base de sécurité de Microsoft Defender pour point de terminaison](../security/defender-endpoint/configure-machines-security-baseline.md).<br><br>Voir [Utiliser les lignes de base de sécurité pour configurer des appareils Windows dans Intune](/mem/intune/protect/security-baselines) afin d’examiner la liste des lignes de base de sécurité disponibles et de savoir comment éviter les conflits.         |
|2     |  Déployez les paramètres de base de référence de sécurité Windows. Vous l’avez peut-être déjà fait si vous avez suivi les instructions de l’[Étape 5. Déployer des profils de configuration](manage-devices-with-intune-configuration-profiles.md).        |
|3    |  Déployez les paramètres de ligne de base Defender pour point de terminaison pour Intune. Voir [Gérer les profils de ligne de base de sécurité Microsoft Intune](/mem/intune/protect/security-baselines-configure) pour créer le profil et choisir la version de ligne de base.<br><br>Vous pouvez également suivre les instructions ici : [Examiner et affecter la ligne de base de sécurité Microsoft Defender pour les points de terminaison](../security/defender-endpoint/configure-machines-security-baseline.md#review-and-assign-the-microsoft-defender-for-endpoint-security-baseline).     |
|4     | Dans Defender pour point de terminaison, examinez la [Carte de ligne de base de sécurité sur la gestion de la configuration des appareils](../security/defender-endpoint/configure-machines.md).          |


## <a name="next-steps"></a>Prochaines étapes
Accédez à [l’Étape 7. Implémenter la protection contre la perte de données avec des fonctionnalités de protection des informations sur les points de terminaison](manage-devices-with-intune-dlp-mip.md).