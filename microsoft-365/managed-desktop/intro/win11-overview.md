---
title: Microsoft Managed Desktop et Windows 11
description: Comment et quand Windows 11 disponible dans le service
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.openlocfilehash: b7a4366281172254a893c20dfd7519e2e8ef36d1
ms.sourcegitcommit: 6f3bc00a5cf25c48c61eb3835ac069e9f41dc4db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/24/2022
ms.locfileid: "62170962"
---
# <a name="microsoft-managed-desktop-and-windows-11"></a>Microsoft Managed Desktop et Windows 11

Après l’annonce de Windows 11, vous avez peut-être commencé à planifier Windows 11 migrations dans le cadre de vos efforts pour maintenir Windows 10 à jour. Cet article décrit les considérations importantes et la façon Microsoft Manged Desktop la prise en charge des transitions fluides dans vos environnements. Pour plus d’informations sur Windows 11 lui-même, [voir Windows 11 vue d’ensemble.](/windows/whats-new/windows-11)

Pour obtenir des étapes spécifiques à suivre pour installer Windows 11 sur vos appareils Microsoft Manged Desktop, voir Aperçu et tester les Windows 11 avec [Microsoft Manged Desktop](../working-with-managed-desktop/test-win11-mmd.md).

## <a name="timeline-for-windows-10-and-windows-11"></a>Chronologie des Windows 10 et Windows 11

Windows 11 est devenu disponible le 4 octobre 2021. Il est prêt pour le déploiement grand public et d’entreprise et est une plateforme entièrement prise en charge. Nous allons commencer à planifier des déploiements pour tous les appareils Microsoft Manged Desktop à partir de janvier 2023, mais nous fournirons une prise en charge complète pour ceux qui souhaitent déployer Windows 11 plus tôt. Nous consulterons et conseillons aux administrateurs de développer et d’implémenter des plans de migration pour chaque client en fonction de la préparation technique et des considérations de votre entreprise.

Microsoft Manged Desktop continue de prendre en charge Windows 10 en parallèle jusqu’à ce qu’il atteigne la fin de la prise en charge de l’entreprise. Voir [les Windows 10 de publication pour](/windows/release-health/release-information) les informations de cycle de vie.



## <a name="assessing-pre-release-versions-of-windows-11"></a>Évaluation des versions pré-Windows 11

Plus de 95 % des appareils Microsoft Manged Desktop sont éligibles pour Windows 11, vous pouvez donc essayer la mise à niveau sur les périphériques de test avant le déploiement de production. Pour plus d’informations Windows 11 la Windows 11 système, [voir la Windows 11 requise.](/windows/whats-new/windows-11-requirements) 

Pour Microsoft Manged Desktop, vous pouvez ajouter des appareils au groupe [Windows 11 de test.](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#add-devices-to-the-windows-11-test-group) Ce groupe reçoit la Windows 11 de disponibilité générale, ainsi qu’une configuration Microsoft Manged Desktop base de référence. Une fois ajouté au groupe d’appareils, autorisez un à deux jours pour qu’un appareil sélectionne les nouveaux paramètres et soit proposé Windows 11.

Pour vos appareils qui ne sont pas gérés [](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/endpoint-manager-simplifies-upgrades-to-windows-11/ba-p/2771886) par Microsoft Manged Desktop, vous pouvez lire des Endpoint Manager pour en savoir plus sur le déploiement Windows 11 vous-même. Si vous avez des appareils Windows 11 et ultérieurs, inscrivez-les dans Microsoft Manged Desktop ; ils ne reviennent pas à Windows 10.

## <a name="support-for-pre-release-windows-11-devices"></a>Prise en charge des périphériques de Windows 11 pré-version

Pour ceux qui ont choisi d’Windows 11 avant la disponibilité générale, les builds d’aperçu peuvent être installées sur les appareils. Microsoft Manged Desktop appareils dans cet état ne seront pas proposés à la Windows 11 de disponibilité générale, mais seront toujours pris en charge pour résoudre les problèmes rencontrés. En outre, Microsoft Manged Desktop tous les appareils gérés pour les menaces de sécurité et répondra aux alertes, que l’appareil exécute ou non une version d’Windows 11 prévisualisation. 

Étant donné que nous nous engageons à vous aider à migrer vers Windows 11 tout en restant productif, nous vous encourageons à signaler les défauts que vous rencontrez avec la plateforme. Nous hiérarchisons les défauts qui bloqueront la productivité des utilisateurs lors du déploiement de Windows 11, et les défauts qui bloquent la productivité des utilisateurs sur Windows 10 appareils.

## <a name="testing-application-compatibility"></a>Test de la compatibilité des applications

La compatibilité des applications est l’un des problèmes les plus courants dans toute migration de plateforme en raison du risque de perturbation de la productivité. Nous utilisons plusieurs mesures proactives et réactives pour vous aider à être certain de la fluidité des transitions d’application vers Windows 11.

### <a name="proactive-measures"></a>Mesures proactives

**Applications courantes :** Microsoft teste de façon approfondie les applications et suites d’entreprise les plus courantes déployées sur des builds de Windows 11. Nous travaillons avec des éditeurs de logiciels externes et des équipes produit internes pour résoudre les problèmes détectés lors des tests. Pour plus d’informations sur notre effort de test de compatibilité proactive, consultez le [blog sur la compatibilité des applications.](https://blogs.windows.com/windowsexperience/2019/01/15/application-compatibility-in-the-windows-ecosystem/)

 Applications métier : la [base](https://www.microsoft.com/en-us/testbase) de test est une ressource que les éditeurs d’applications et les administrateurs informatiques peuvent utiliser pour soumettre des applications et des cas de test pour que Microsoft s’exécute sur une machine virtuelle exécutant des builds Windows 11 dans un environnement Azure sécurisé. Les résultats, les analyses de test et l’analyse de régression pour chaque exécution de test sont disponibles sur un portail Azure privé. Microsoft Manged Desktop vous aideront à hiérarchiser vos applications métiers pour la validation en fonction des données d’utilisation et de fiabilité des applications. Pour plus d’informations sur la base de test, voir [Base de test Microsoft 365](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/test-base-for-microsoft-365-microsoft-ignite-2021-updates/ba-p/2185566).

### <a name="reactive-measures"></a>Mesures réactives
Si vous rencontrez des problèmes de compatibilité d’application dans des environnements de test ou de production, vous pouvez bénéficier d’une prise en charge gratuite en ouvrant une demande [de service.](/microsoft-365/managed-desktop/working-with-managed-desktop/test-win11-mmd?view=o365-worldwide#report-issues) Par Windows 11, cela inclut toutes les fonctionnalités avec les applications Office, Microsoft Edge, Teams et métiers en cours d’exécution sur les dernières builds de système d’exploitation. Microsoft App Assure fait directement appel aux éditeurs d’applications pour hiérarchiser et résoudre les problèmes de compatibilité des applications si nécessaire.

