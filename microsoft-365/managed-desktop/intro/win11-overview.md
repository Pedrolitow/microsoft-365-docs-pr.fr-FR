---
title: Microsoft Manged Desktop et Windows 11
description: Comment et quand Windows 11 est disponible dans le service
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 1c5f2a7f60097bb02cb11eaabd66cad88657c505
ms.sourcegitcommit: 2abc6bf9939b14a427647e88f319dbb70de49ca6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53458483"
---
# <a name="microsoft-managed-desktop-and-windows-11"></a>Microsoft Manged Desktop et Windows 11

Après l’annonce de Windows 11, vous avez peut-être commencé à planifier des migrations Windows 11 dans le cadre de vos efforts pour maintenir Windows 10 à jour. Cet article décrit les considérations importantes et la façon Microsoft Manged Desktop de prendre en charge les transitions fluides dans vos environnements. Pour plus d’informations Windows 11 lui-même, voir [Windows vue d’ensemble de 11.](/windows/whats-new/windows-11)

Pour obtenir les étapes spécifiques à suivre pour installer Windows 11 sur vos appareils Microsoft Manged Desktop, consultez La prévisualisation et testez Windows [11](../working-with-managed-desktop/test-win11-mmd.md)avec Microsoft Manged Desktop .

## <a name="timeline-for-windows-11"></a>Chronologie pour Windows 11

Windows 11 builds d’aperçu sont disponibles à partir du 28 juin 2021 jusqu’au Windows [programme Insider.](/windows-insider/) Nous prévoyons que les builds de publication seront généralement disponibles d’ici la fin de l’année civile 2021.

Vous pouvez installer les builds d’aperçu sur les appareils, qu’ils soient gérés Microsoft Manged Desktop ou non. Nous continuerons à prendre en charge Windows 10 en parallèle jusqu’à ce qu’il atteigne la fin de la prise en charge.

Lorsque Windows 11 est généralement disponible, nous allons tester davantage de validation. Nous prévoyons que janvier 2022 sera le plus tôt Windows 11 sera proposé aux Microsoft Manged Desktop de production via nos groupes de déploiement standard.

Nous consulterons et conseillons aux administrateurs de développer et d’implémenter des plans de migration pour chaque client en fonction de la préparation technique et des considérations de votre entreprise.

## <a name="assessing-pre-release-versions-of-windows-11"></a>Évaluation des versions pré-versions de Windows 11

Plus de 95 % des appareils Microsoft Manged Desktop sont éligibles pour Windows 11. Vous pouvez donc prévisualiser la mise à niveau sur les périphériques de test avant le déploiement de production. Pour plus d’informations Windows 11 système requis, voir [Windows 11.](/windows/whats-new/windows-11-requirements) Vous pouvez demander des détails sur l’état d’éligibilité de vos appareils Microsoft Manged Desktop.

Pour Microsoft Manged Desktop, vous pouvez demander d’ajouter des périphériques de test au groupe d’appareils d’appareils de test **\[ pré Windows 11 Modern Workplace \] Windows 11.** Ce groupe reçoit les Windows version d’évaluation 11, ainsi qu’une configuration Microsoft Manged Desktop base de référence. Microsoft Manged Desktop ne gère pas la cadence de publication des builds d’aperçu Windows 11, de sorte que les membres de ce groupe d’appareils peuvent recevoir des mises à jour plus fréquemment que Windows 10 groupes d’appareils.

Pour vos appareils qui ne sont pas gérés par Microsoft Manged Desktop, vous pouvez rejoindre le programme [Windows Insider](/windows-insider/) pour télécharger les builds d’aperçu et obtenir des conseils sur le déploiement de Windows 11 vous-même. Si des appareils exécutent des builds pré Windows 11 et les inscrivent ultérieurement dans Microsoft Manged Desktop, ils ne reviennent pas à Windows 10.

## <a name="support-for-pre-release-windows-11-devices"></a>Prise en charge de la version Windows 11 appareils

Les builds pré-publiées de n’importe quelle plateforme sont censés contenir des défauts et des problèmes de compatibilité des applications qui peuvent être identifiés et résolus avant la disponibilité générale. Par conséquent, nous considérons que les appareils exécutant des builds pré-publiées de Windows 11 sont des périphériques de test, mais nous les surveillons avec le reste de l’environnement pour les menaces de sécurité et ils sont soumis à la même réponse d’alerte de sécurité que les autres appareils Microsoft Manged Desktop.

Étant donné que nous nous engageons à vous aider à migrer vers Windows 11 tout en restant productif, nous vous encourageons à signaler les défauts que vous rencontrez avec les builds pré-publiées. Nous hiérarchisons les défauts qui bloqueront la productivité des utilisateurs lors du déploiement à grande échelle de Windows 11 et les défauts qui bloquent la productivité des utilisateurs sur Windows 10 appareils.

## <a name="testing-application-compatibility"></a>Test de la compatibilité des applications

La compatibilité des applications est l’un des problèmes les plus courants dans toute migration de plateforme en raison du risque de perturbation de la productivité. Nous utilisons plusieurs mesures proactives et réactives pour vous aider à être certain de la fluidité des transitions d’application vers Windows 11.

### <a name="proactive-measures"></a>Mesures proactives

**Applications courantes :** Microsoft teste de façon approfondie les applications et suites d’entreprise les plus courantes déployées sur des builds Windows 11. Nous travaillons avec des éditeurs de logiciels externes et des équipes produit internes pour résoudre les problèmes détectés lors des tests. Pour plus d’informations sur notre effort de test de compatibilité proactive, consultez le [blog sur la compatibilité des applications.](https://blogs.windows.com/windowsexperience/2019/01/15/application-compatibility-in-the-windows-ecosystem/)

 Applications métier : la [base](https://www.microsoft.com/testbase) de test est une ressource que les éditeurs d’applications et les administrateurs informatiques peuvent utiliser pour soumettre des applications et des cas de test pour que Microsoft s’exécute sur une machine virtuelle exécutant des builds Windows 11 dans un environnement Azure sécurisé. Les résultats, les analyses de test et l’analyse de régression pour chaque exécution de test sont disponibles sur un portail Azure privé. Microsoft Manged Desktop vous aideront à hiérarchiser vos applications métiers pour la validation en fonction des données d’utilisation et de fiabilité des applications. Pour plus d’informations sur la base de test, voir [Base de test Microsoft 365](https://techcommunity.microsoft.com/t5/windows-it-pro-blog/test-base-for-microsoft-365-microsoft-ignite-2021-updates/ba-p/2185566).

### <a name="reactive-measures"></a>Mesures réactives

Si vous rencontrez des problèmes de compatibilité d’application dans des environnements de test ou de production, vous pouvez obtenir une assistance en impliquant [Soutien](/fasttrack/products-and-capabilities) aux applications ou FastTrack, le cas échéant. Pour Windows 11, cela inclut toutes les fonctionnalités des applications Office, Microsoft Edge et Teams s’exécutant sur les dernières builds de système d’exploitation. L’Application Assure engage directement les éditeurs d’applications à hiérarchiser et résoudre les problèmes de compatibilité des applications.