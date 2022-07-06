---
title: En savoir plus sur l’extension Microsoft Purview
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: Extension Microsoft Purview étend la surveillance et le contrôle des activités de fichiers et des actions de protection au navigateur Google Chrome
ms.openlocfilehash: 08078871765a75577475c93ba35cabda9ee3fd6a
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66622896"
---
# <a name="learn-about-the-microsoft-purview-extension"></a>En savoir plus sur l’extension Microsoft Purview

[La prévention des pertes de données des points de terminaison (endpoint DLP)](endpoint-dlp-learn-about.md) étend les capacités de surveillance et de protection des activités de [Microsoft Purview Data Loss Prevention (DLP)](dlp-learn-about-dlp.md) aux éléments sensibles qui se trouvent sur les appareils Windows 10. Une fois que les appareils sont intégrés aux solutions de conformité Microsoft Purview, les informations relatives à ce que les utilisateurs font avec les éléments sensibles sont rendues visibles dans [l’Explorateur d’activités](data-classification-activity-explorer.md) et vous pouvez appliquer des actions de protection à ces éléments via des [stratégies DLP](create-test-tune-dlp-policy.md).

Une fois l’extension installée sur un appareil Windows 10, les organisations peuvent surveiller lorsqu’un utilisateur tente d’accéder ou de télécharger un élément sensible sur un service cloud à l’aide de Google Chrome et d’appliquer des actions de protection via DLP.  

## <a name="activities-you-can-monitor-and-take-action-on"></a>Les activités que vous pouvez surveiller et sur lesquels vous pouvez agir

L’extension vous permet d’auditer et de gérer les types d’activités suivants que les utilisateurs effectuent sur des éléments sensibles sur des appareils exécutant Windows 10.

activité |description  | actions de stratégie prises en charge|
|---------|---------|---------|
|fichier copié dans le cloud  | Détecte lorsqu'un utilisateur tente de charger un élément sensible dans un domaine de service restreint par le biais du navigateur Chrome. |audit, blocage avec remplacement, blocage|
|fichier imprimé  |Détecte quand un utilisateur tente d’imprimer un élément sensible ouvert dans le navigateur Chrome sur une imprimante locale ou réseau |audit, blocage avec remplacement, blocage|
|Fichier copié dans le Presse-papiers |Détecte quand un utilisateur tente de copier des informations à partir d’un élément sensible en cours d’affichage dans le navigateur Chrome, puis de les coller dans une autre application, processus ou élément. |audit, blocage avec remplacement, blocage|
|Fichier copié dans un stockage amovible    | Détecte quand un utilisateur tente de copier un élément ou des informations sensibles d’un élément sensible ouvert dans le navigateur Chrome pour un support amovible ou un périphérique USB |audit, blocage avec remplacement, blocage|
|fichier copié sur le partage réseau  |Détecte quand un utilisateur tente de copier un élément ou des informations sensibles d’un élément sensible ouvert dans le navigateur Chrome vers un partage réseau ou un lecteur réseau mappé.|audit, blocage avec remplacement, blocage |

## <a name="deployment-process"></a>Processus de déploiement
1. [Prise en main des points de terminaison de protection contre la perte de données](endpoint-dlp-getting-started.md)
2. [Outils et méthodes d’intégration pour les appareils Windows 10](device-onboarding-overview.md)
3. [Installer l’extension sur vos appareils Windows 10](dlp-chrome-get-started.md)
4. [Créer ou modifier des stratégies DLP](create-test-tune-dlp-policy.md) qui limitent le chargement vers un service cloud ou l’accès par des actions de navigateurs non autorisé et les appliquent à vos appareils Windows 10

## <a name="next-steps"></a>Étapes suivantes

Consultez [Prise en main de l’Extension Microsoft Purview](dlp-chrome-get-started.md) pour des procédures et des scénarios de déploiement complets.

## <a name="see-also"></a>Voir aussi

- [Démarrage avec l’Extension Microsoft Purview](dlp-chrome-get-started.md)
- [Découvrir la protection contre la perte de données de point de terminaison](endpoint-dlp-learn-about.md)
- [Prise en main de la protection contre la perte de données de point de terminaison](endpoint-dlp-getting-started.md)
- [Utilisation de la prévention des pertes de données sur les points de terminaison](endpoint-dlp-using.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)
- [Gestion des risques internes](insider-risk-management.md)
