---
title: Découvrir la protection contre la perte de données des point de terminaison de Microsoft 365
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
description: 'La protection contre la perte de données des points de terminaison de Microsoft 365 étend la surveillance des activités de fichiers et les actions de protection pour ces fichiers aux points de terminaison. Les fichiers sont rendus visibles dans les solutions de conformité '
ms.openlocfilehash: 83608f005b9024583142515094b2d958b8f5d915
ms.sourcegitcommit: 2697938d2d4fec523b501c5e7b0b8ec8f34e59b0
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/12/2022
ms.locfileid: "63450343"
---
# <a name="learn-about-microsoft-365-endpoint-data-loss-prevention"></a>En savoir plus sur la protection contre la perte de données de point de terminaison Microsoft 365

Vous pouvez utiliser la prévention des pertes de données (DLP) de Microsoft 365 pour surveiller les actions prises sur les éléments que vous avez déterminés comme sensibles et pour aider à empêcher le partage involontaire de ces éléments. Pour plus d'informations sur la DLP, consultez [En savoir plus sur la prévention de la perte de données](dlp-learn-about-dlp.md).

**Protection contre la perte de données de point de terminaison** (Endpoint DLP) étend les fonctionnalités de surveillance et de protection des activités de DLP aux éléments sensibles qui sont stockés physiquement sur des appareils Windows 10, Windows 11 et macOS (Catalina 10.15 et versions ultérieures). Une fois que les appareils sont intégrés aux solutions de conformité Microsoft 365, les informations relatives à ce que les utilisateurs font avec les éléments sensibles sont rendues visibles dans [l’Explorateur d’activités](data-classification-activity-explorer.md) et vous pouvez appliquer des actions de protection à ces éléments via [stratégies DLP](create-test-tune-dlp-policy.md).

> [!TIP]
> Si vous recherchez le contrôle d’appareil pour le stockage amovible, consultez [Contrôle d’accès Stockage amovible Contrôle d’appareil Microsoft Defender pour Point de terminaison ](../security/defender-endpoint/device-control-removable-storage-access-control.md#microsoft-defender-for-endpoint-device-control-removable-storage-access-control).

> [!NOTE]
> Dans Microsoft 365 conformité, l’évaluation de la stratégie DLP des éléments sensibles se produit de manière centralisée, de sorte qu’il n’y a pas de délai pour que les stratégies et les mises à jour des stratégies soient distribuées aux appareils individuels. Lorsqu’une stratégie est mise à jour dans le centre de conformité, la synchronisation de ces mises à jour dans le service prend généralement environ une heure. Une fois les mises à jour de stratégie synchronisées, les éléments sur les appareils ciblés sont automatiquement réévalués la prochaine fois qu’ils sont consultés ou modifiés.

## <a name="endpoint-activities-you-can-monitor-and-take-action-on"></a>Activités de point de terminaison que vous pouvez surveiller et sur lesquels vous pouvez agir

Microsoft Endpoint DLP vous permet d’auditer et de gérer les types d’activités suivants que les utilisateurs prennent sur les éléments sensibles qui sont stockés physiquement sur des appareils Windows 10, Windows 11 ou macOS.

|Activité |Description  |Windows 10 1809 et ultérieures/ Windows 11| macOS Catalina 10.15 (préversion) | Auditable/restrictable|
|---------|---------|---------|---------|---------|
|téléchargement vers un service en ligne, ou accès par des navigateurs non autorisés    | Détecte lorsqu'un utilisateur tente de télécharger un article dans un domaine de service restreint ou d'accéder à un article par le biais d'un navigateur.  S’ils utilisent un navigateur répertorié dans DLP en tant que navigateur non autorisé, l’activité de chargement est bloquée et l’utilisateur est redirigé pour utiliser Microsoft Edge . Microsoft Edge autorisez ou bloquez le chargement ou l’accès en fonction de la configuration de la stratégie DLP         |Pris en charge | Pris en charge|auditable et restreint|
|copie vers une autre application    |Détecte lorsqu'un utilisateur tente de copier des informations d'un élément protégé et de les coller ensuite dans une autre application, un autre processus ou un autre élément. Copier et coller des informations dans la même application, le même processus ou le même élément n'est pas détecté par cette activité.|Pris en charge|Pris en charge         | auditable et restreint|
|copie sur support USB amovible |Détecte lorsqu'un utilisateur tente de copier un élément ou une information sur un support amovible ou un périphérique USB.|Pris en charge|Pris en charge         | auditable et restreint|
|copier vers un partage réseau    |Détecte lorsqu'un utilisateur tente de copier un élément vers un partage réseau ou un disque réseau mappé |Pris en charge|Pris en charge         |auditable et restreint|
|imprimer un document    |Détecte lorsqu'un utilisateur tente d'imprimer un élément protégé sur une imprimante locale ou réseau.|Pris en charge|Pris en charge|auditable et restreint         |
|copier vers une session à distance|Détecte lorsqu'un utilisateur tente de copier un élément vers une session de bureau à distance |Pris en charge|non pris en charge|  auditable et restreint|
|copier vers appareil Bluetooth|Détecte lorsqu'un utilisateur tente de copier un élément vers une application Bluetooth non autorisée (telle que définie dans la liste des applications Bluetooth non autorisées dans les paramètres DLP de point de terminaison).|Pris en charge|non pris en charge| auditable et restreint|
|créer un élément|Détecte lorsqu'un utilisateur crée un article|Pris en charge | |vérifiable|
|renommer un article|Détecte lorsqu'un utilisateur renomme un article|Pris en charge | |vérifiable|

## <a name="monitored-files"></a>Fichiers analysées

La DLP de point du terminaison prend en charge la surveillance de ces types de fichiers. La DLP procède à un audit des activités de ces types de fichiers, même s’il n’existe pas de correspondance de stratégie. 

- Fichiers Word
- Fichiers PowerPoint
- Fichiers Excel
- Fichiers .pdf
- Fichiers .csv
- Fichiers .tsv
- fichiers .txt
- Fichiers RTF
- fichiers c
- fichiers de classe
- fichiers CPP
- fichiers cs
- fichiers h
- fichiers Java
 
Si vous souhaitez surveiller les données des correspondances de stratégie uniquement, vous pouvez désactiver l'option **Toujours auditer l’activité du fichier pour les appareils** dans les paramètres globaux DLP du point de terminaison.

> [!NOTE]
> Si le paramètre **Toujours auditer l’activité du fichier pour les appareils** est activé, les activités sur les fichiers Word, PowerPoint, Excel, PDF, et .csv sont toujours auditées, même si l’appareil n’est ciblé par aucune stratégie.

> [!TIP]
> Pour vous assurer que les activités sont auditées pour tous les types de fichiers pris en charge, créez une [stratégie DLP personnalisée](create-test-tune-dlp-policy.md).

Le DLP du point de terminaison contrôle l’activité basée sur le type MIME, de sorte que les activités sont capturées même si l’extension de fichier est modifiée.

### <a name="file-types-preview"></a>Types de fichiers (aperçu)

Les types de fichiers sont un regroupement de formats de fichiers utilisés pour protéger des flux de travail ou des domaines d’activité spécifiques. Vous pouvez utiliser un ou plusieurs types de fichiers comme conditions dans vos stratégies DLP.

|Type de fichier |Application  |extensions de fichier surveillées  |
|---------|---------|---------|
|traitement de texte |Word, PDF | .doc, .docx,  .docm, .dot, .dotx, .dotm, .docb, .pdf |
|feuille de calcul    |Excel, CSV, TSV |.xls, .xlsx, .xlt, .xlm, .xlsm, .xltx, .xltm, .xlsb, .xlw, .csv, .tsv         |
|présentation |PowerPoint|.ppt, .pptx, .pos, .pps, .pptm, .potx, .potm, .ppam, .ppsx|
|archive  |outils d’archivage et de compression de fichiers | .zip, .zipx, .rar, .7z, .tar, .gz        |
|email    |Outlook |.pst, .ost, .msg         |

### <a name="file-extensions-preview"></a>Extensions de fichier (aperçu)

Si les types de fichiers ne couvrent pas les extensions de fichier que vous devez lister en tant que condition dans une stratégie, vous pouvez utiliser des extensions de fichier séparées par des virgules à la place.

> [!IMPORTANT]
> Les extensions de fichier et les options de types de fichiers ne peuvent pas être utilisés comme conditions dans la même règle. Si vous souhaitez les utiliser comme conditions dans la même stratégie, elles doivent être dans des règles distinctes. 

> [!IMPORTANT]
> Ces versions Windows prennent en charge les types de fichiers et les fonctionnalités d’extension de fichier suivants :
>- Windows 10 versions 20H1/20H2/21H1 (KB 5006738)
>- Windows 10 versions 19H1/19H2 (KB 5007189)
>- Windows 10 RS5 (KB 5006744)


## <a name="whats-different-in-endpoint-dlp"></a>Différences avec Endpoint DLP

Vous devez tenir compte d’un certain nombre de concepts supplémentaires avant d’approfondir le point de terminaison DLP.

### <a name="enabling-device-management"></a>Activation de la gestion des appareils

La gestion des appareils est une fonctionnalité qui permet d’assembler la télémétrie à partir d’appareils et de l’intégrer à des solutions de conformité Microsoft 365 telles que point de terminaison DLP et [ gestionnaire des risques Insider](insider-risk-management.md). Vous devez intégrer tous les appareils que vous voulez utiliser en tant qu’emplacements dans les stratégies DLP.

> [!div class="mx-imgBorder"]
> ![activer la gestion des appareils.](../media/endpoint-dlp-learn-about-1-enable-device-management.png)

L’intégration et déclassement sont gérés à l’aide de scripts téléchargés à partir du centre de gestion des appareils. Le centre inclut des scripts personnalisés pour chacune de ces méthodes de déploiement :

- script local (jusqu’à 10 ordinateurs)
- Stratégie de groupe
- System Center Configuration Manager, Version 1610 ou ultérieure
- Gestion des périphériques mobiles/Microsoft Intune
- Scripts d’intégration VDI pour les machines non persistantes

> [!div class="mx-imgBorder"]
> ![page d’intégration d’appareils.](../media/endpoint-dlp-learn-about-3-device-onboarding-page.png)

 Utilisez les procédures décrites dans [Prise en main des points de terminaison Microsoft 365 DLP](endpoint-dlp-getting-started.md) vers les appareils intégrés.

Si vous avez des appareils intégrés via [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/), ces derniers apparaissent automatiquement dans la liste des appareils. Vous pouvez activer **la surveillance des appareils pour** utiliser le point de terminaison DLP.

> [!div class="mx-imgBorder"]
> ![liste des appareils gérés.](../media/endpoint-dlp-learn-about-2-device-list.png)

### <a name="viewing-endpoint-dlp-data"></a>Affichage des données DLP de point de terminaison

Vous pouvez afficher les alertes liées aux stratégies DLP appliquées sur les appareils de point de terminaison en accédant au [Tableau de bord de Gestion des Alertes DLP.](dlp-configure-view-alerts-policies.md)

> [!div class="mx-imgBorder"]
> ![Information d’alerte.](../media/Alert-info-1.png)

Vous pouvez également afficher les détails de l’événement associé avec des métadonnées complètes dans le même tableau de bord

> [!div class="mx-imgBorder"]
> ![Informations sur un événement.](../media/Event-info-1.png)

Une fois qu’un appareil est intégré, les informations relatives aux activités auditées sont transmises dans l’Explorateur d’activités, même avant de configurer et déployer des stratégies DLP qui ont des périphériques comme emplacement.

> [!div class="mx-imgBorder"]
> ![événements DLP du point de terminaison dans l’explorateur d’activités.](../media/endpoint-dlp-learn-about-4-activity-explorer.png)

Point de terminaison DLP recueille de nombreuses informations sur l’activité auditée.

Par exemple, si un fichier est copié sur un support USB amovible, les attributs suivants apparaissent dans les détails de l’activité :

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
> ![copier dans les attributs d’activités usb.](../media/endpoint-dlp-learn-about-5-activity-attributes.png)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous en savez plus sur les points de terminaison DLP, vos prochaines étapes sont les suivantes :

1. [Intégrer Windows 10 ou Windows 11 appareils dans Microsoft 365 vue d’ensemble](device-onboarding-overview.md)
1. [Intégration des appareils macOS dans la vue d'ensemble de Microsoft 365 (aperçu)](device-onboarding-macos-overview.md#onboard-macos-devices-into-microsoft-365-overview-preview)
1. [Utilisation des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-using.md)

## <a name="see-also"></a>Voir aussi

- [Prise en main des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-getting-started.md)
- [Utilisation des points de terminaison de protection contre la perte de données Microsoft (préversion)](endpoint-dlp-using.md)
- [En savoir plus sur la prévention des pertes de données](dlp-learn-about-dlp.md)
- [Création, test et réglage d’une stratégie DLP](create-test-tune-dlp-policy.md)
- [Prise en main de l’explorateur d’activités](data-classification-activity-explorer.md)
- [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/)
- [Gestion des risques internes](insider-risk-management.md)
