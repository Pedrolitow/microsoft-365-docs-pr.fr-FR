---
title: Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 07/21/2020
audience: ITPro
ms.topic: conceptual
f1_keywords:
- ms.o365.cc.DLPLandingPage
ms.service: O365-seccomp
localization_priority: Priority
ms.collection:
- M365-security-compliance
- m365solution-mip
- m365initiative-compliance
search.appverid:
- MET150
description: 'La prévention des pertes de données du Point de terminaison Microsoft 365 étend la surveillance des activités des fichiers et des actions de protection de ces aux points de terminaison. Les fichiers sont rendus visibles dans les solutions de conformité Microsoft 365 '
ms.openlocfilehash: 39474f54440ba33c8d7140981c1495a5c46bf0fc
ms.sourcegitcommit: 48195345b21b409b175d68acdc25d9f2fc4fc5f1
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/30/2021
ms.locfileid: "53226682"
---
# <a name="learn-about-microsoft-365-endpoint-data-loss-prevention"></a>En savoir plus sur la protection contre la perte de données de point de terminaison Microsoft 365

Vous pouvez utiliser la protection contre la perte de données (DLP) de Microsoft 365 pour contrôler les actions effectuées sur les éléments que vous avez jugés confidentiels et contribuer à empêcher le partage involontaire de ces éléments. Si vous souhaitez en savoir plus sur DLP, veuillez consulter la rubrique [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md).

**Les points de terminaison contre la protection contre la perte de données** (Endpoint DLP) étend les fonctionnalités de surveillance et de protection des activités de DLP aux éléments sensibles sur les appareils Windows 10. Une fois que les appareils sont intégrés aux solutions de conformité Microsoft 365, les informations relatives à ce que les utilisateurs font avec les éléments sensibles sont rendues visibles dans [l’Explorateur d’activités](data-classification-activity-explorer.md) et vous pouvez appliquer des actions de protection à ces éléments via [stratégies DLP](create-test-tune-dlp-policy.md).

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>Activités de point de terminaison que vous pouvez surveiller et sur lesquels vous pouvez agir

Les points de terminaison Microsoft DLP vous permet d’auditer et de gérer les types d’activités suivants que les utilisateurs prennent sur les appareils exécutant Windows 10.

|Activité |Description  | Auditable/restreint|
|---------|---------|---------|
|téléchargement vers un service en ligne, ou accès par des navigateurs non autorisés    | Détecte lorsqu'un utilisateur tente de télécharger un article dans un domaine de service restreint ou d'accéder à un article par le biais d'un navigateur.  S'ils utilisent un navigateur qui est répertorié dans DLP comme étant un navigateur non autorisé, l'activité de téléchargement sera bloquée et l'utilisateur sera redirigé pour utiliser Edge Chromium. Edge Chromium autorisera ou bloquera alors le téléchargement ou l'accès en fonction de la configuration de la politique DLP         |auditable et restreint|
|copie vers une autre application    |Détecte lorsqu'un utilisateur tente de copier des informations d'un élément protégé et de les coller ensuite dans une autre application, un autre processus ou un autre élément. Copier et coller des informations dans la même application, le même processus ou le même élément n'est pas détecté par cette activité.         | auditable et restreint|
|copie sur support USB amovible |Détecte lorsqu'un utilisateur tente de copier un élément ou une information sur un support amovible ou un périphérique USB.         | auditable et restreint|
|copier vers un partage réseau    |Détecte lorsqu'un utilisateur tente de copier un élément vers un partage réseau ou un disque réseau mappé         |auditable et restreint|
|imprimer un document    |Détecte lorsqu'un utilisateur tente d'imprimer un élément protégé sur une imprimante locale ou réseau.| auditable et restreint         |
|copier vers une session à distance|Détecte lorsqu'un utilisateur tente de copier un élément vers une session de bureau à distance |  auditable et restreint|
|copier vers appareil Bluetooth|Détecte lorsqu'un utilisateur tente de copier un élément vers une application Bluetooth non autorisée (telle que définie dans la liste des applications Bluetooth non autorisées dans les paramètres DLP de point de terminaison).| auditable et restreint|
|créer un élément|Détecte lorsqu'un utilisateur crée un article| vérifiable|
|renommer un article|Détecte lorsqu'un utilisateur renomme un article| vérifiable|

## <a name="monitored-files"></a>Fichiers analysées

La DLP de point du terminaison prend en charge la surveillance de ces types de fichiers :

- Fichiers Word
- Fichiers PowerPoint
- Fichiers Excel
- Fichiers .pdf
- Fichiers .csv
- Fichiers .tsv
- fichiers .txt
- Fichiers RTF
- fichiers c
- fichiers de classe
- fichiers CPP
- fichiers cs
- fichiers h
- fichiers Java

Par défaut, la DLP du point de terminaison audite les activités de ces types de fichiers, même s’il n’existe pas de correspondance de stratégie. Si vous souhaitez surveiller les données des correspondances de stratégie uniquement, vous pouvez désactiver l'option **Toujours auditer l’activité du fichier pour les appareils** dans les paramètres globaux DLP du point de terminaison. Si ce paramètre est utilisé, les activités sur les fichiers Word, PowerPoint, Excel, PDF, et .csv sont toujours auditées, même si l’appareil n’est ciblé par aucune stratégie.

Le DLP du point de terminaison contrôle l’activité basée sur le type MIME, de sorte que les activités sont capturées même si l’extension de fichier est modifiée.

## <a name="whats-different-in-endpoint-dlp"></a>Différences avec Endpoint DLP

Vous devez tenir compte d’un certain nombre de concepts supplémentaires avant d’approfondir le point de terminaison DLP.

### <a name="enabling-device-management"></a>Activation de la gestion des appareils

La gestion des appareils est une fonctionnalité qui permet d’assembler la télémétrie à partir d’appareils et de l’intégrer à des solutions de conformité Microsoft 365 telles que point de terminaison DLP et [ gestionnaire des risques Insider](insider-risk-management.md). Vous devez intégrer tous les appareils que vous voulez utiliser en tant qu’emplacements dans les stratégies DLP.

> [!div class="mx-imgBorder"]
> ![activer la gestion des appareils](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

L’intégration et déclassement sont gérés à l’aide de scripts téléchargés à partir du centre de gestion des appareils. Le centre inclut des scripts personnalisés pour chacune de ces méthodes de déploiement :

- script local (jusqu’à 10 ordinateurs)
- Stratégie de groupe
- System Center Configuration Manager, Version 1610 ou ultérieure
- Gestion des périphériques mobiles/Microsoft Intune
- Scripts d’intégration VDI pour les machines non persistantes

> [!div class="mx-imgBorder"]
> ![page d’intégration d’appareils](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Utilisez les procédures décrites dans [Prise en main des points de terminaison Microsoft 365 DLP](endpoint-dlp-getting-started.md) vers les appareils intégrés.

Si vous avez des appareils intégrés via [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/), ces derniers apparaissent automatiquement dans la liste des appareils.

> [!div class="mx-imgBorder"]
> ![liste des appareils gérés](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Affichage des données DLP de point de terminaison

Vous pouvez afficher les alertes liées aux stratégies DLP appliquées sur les appareils de point de terminaison en accédant au [Tableau de bord de Gestion des Alertes DLP.](dlp-configure-view-alerts-policies.md)

> [!div class="mx-imgBorder"]
> ![Information d’alerte](../media/Alert-info-1.png)

Vous pouvez également afficher les détails de l’événement associé avec des métadonnées complètes dans le même tableau de bord

> [!div class="mx-imgBorder"]
> ![Informations sur un événement](../media/Event-info-1.png)

Une fois qu’un appareil est intégré, les informations relatives aux activités auditées sont transmises dans l’Explorateur d’activités, même avant de configurer et déployer des stratégies DLP qui ont des périphériques comme emplacement.

> [!div class="mx-imgBorder"]
> ![événements DLP du point de terminaison dans l’explorateur d’activités](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Point de terminaison DLP recueille de nombreuses informations sur l’activité auditée.

Par exemple, si un fichier est copié sur un support USB amovible, les attributs suivants apparaissent dans les détails de l’activité :

- type d’activité
- IP Client
- Chemin d’accès du fichier
- horodatage arrivé
- nom du fichier
- utilisateur
- extension du fichier
- taille du fichier
- type d’informations sensibles (le cas échéant)
- valeur SHA1
- valeur SHA256
- nom de fichier précédent
- emplacement
- parent
- chemin d’accès
- type d’emplacement source
- platform
- nom du périphérique
- type d’emplacement de destination
- application ayant effectué la copie
- ID de l’appareil Microsoft Defender pour point de terminaison (le cas échéant)
- fabricant de l’appareil multimédia amovible
- modèle d’appareil multimédia amovible
- numéro de série de l’appareil multimédia amovible

> [!div class="mx-imgBorder"]
> ![copier dans les attributs d’activités usb](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous en savez plus sur les points de terminaison DLP, vos prochaines étapes sont les suivantes :

1. [Prise en main des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-getting-started.md)
2. [Utilisation des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-using.md)

## <a name="see-also"></a>Voir aussi

- [Prise en main des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-getting-started.md)
- [Utilisation des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-using.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)
- [Gestion des risques internes](insider-risk-management.md)
