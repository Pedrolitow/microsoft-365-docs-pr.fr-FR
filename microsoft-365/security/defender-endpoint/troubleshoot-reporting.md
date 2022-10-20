---
title: Résoudre les problèmes liés aux outils de création de rapports pour Microsoft Defender Antivirus
description: Identifier et résoudre les problèmes courants lors de la tentative de signalement dans Microsoft Defender’état de protection antivirus dans Update Compliance
keywords: résoudre les problèmes, erreur, correction, conformité des mises à jour, oms, surveiller, signaler Microsoft Defender Antivirus
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection:
- m365-security
- tier3
search.appverid: met150
ms.openlocfilehash: 4215d9fcb83829429275321bfde4172491dffa57
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68646064"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Résoudre des problèmes de rapports antivirus Microsoft Defender dans Conformité de la mise à jour

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> [!IMPORTANT]
> Le 31 mars 2020, la fonctionnalité de création de rapports antivirus Microsoft Defender update Compliance sera supprimée. Vous pouvez continuer à définir et à passer en revue les stratégies de conformité de sécurité à l’aide de [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager), ce qui permet un contrôle plus précis sur les fonctionnalités de sécurité et les mises à jour.

Vous pouvez utiliser Microsoft Defender Antivirus avec mise à jour de conformité. Vous verrez l’état des licences E3, B, F1, VL et Pro. Toutefois, pour les licences E5, vous devez utiliser le [portail Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Pour en savoir plus sur les options de licence, consultez [Windows 10 options de licence de produit](https://www.microsoft.com/licensing/product-licensing/windows10.aspx).

Lorsque vous utilisez [la conformité des mises à jour Windows Analytics pour obtenir des rapports sur l’état de protection des appareils ou des points de terminaison](/windows/deployment/update/update-compliance-using#wdav-assessment) de votre réseau qui utilisent Microsoft Defender Antivirus, vous pouvez rencontrer des problèmes ou des problèmes.

En règle générale, les indicateurs les plus courants d’un problème sont les suivants :

- Vous ne voyez qu’un petit nombre ou un sous-ensemble de tous les appareils que vous vous attendiez à voir
- Vous ne voyez aucun appareil du tout
- Les rapports et les informations que vous voyez sont obsolètes (plus de quelques jours)

Pour connaître les codes d’erreur courants et les ID d’événement liés au service antivirus Microsoft Defender qui ne sont pas liés à Update Compliance, consultez [Microsoft Defender événements Antivirus](troubleshoot-microsoft-defender-antivirus.md).

Il existe trois étapes pour résoudre ces problèmes :

1. Vérifiez que vous avez rempli toutes les conditions préalables
2. Vérifier votre connectivité au service cloud Windows Defender
3. Envoyer les journaux d’activité de support

> [!IMPORTANT]
> Il faut généralement 3 jours pour que les appareils commencent à apparaître dans Update Compliance.

## <a name="confirm-prerequisites"></a>Confirmer les prérequis

Pour que les appareils s’affichent correctement dans Update Compliance, vous devez respecter certaines conditions préalables pour le service Update Compliance et pour Microsoft Defender Antivirus :

>[!div class="checklist"]
>
> - Les points de terminaison utilisent Microsoft Defender Antivirus comme seule application de protection antivirus. [L’utilisation d’une autre application antivirus entraîne la désactivation de Microsoft Defender Antivirus](microsoft-defender-antivirus-compatibility.md) et le point de terminaison n’est pas signalé dans Update Compliance.
> - [La protection fournie par le cloud est activée](enable-cloud-protection-microsoft-defender-antivirus.md).
> - Les points de [terminaison peuvent se connecter au cloud antivirus Microsoft Defender](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Si le point de terminaison est en cours d’exécution Windows 10 version 1607 ou antérieure, [Windows 10 données de diagnostic doivent être définies sur le niveau Amélioré](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level).
> - Il y a 3 jours que toutes les exigences n’ont pas été satisfaites

« Vous pouvez utiliser Microsoft Defender Antivirus avec Update Compliance. Vous verrez l’état des licences E3, B, F1, VL et Pro. Toutefois, pour les licences E5, vous devez utiliser le portail Microsoft Defender pour point de terminaison (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Pour en savoir plus sur les options de licence, consultez Windows 10 options de licences de produit »

Si les conditions préalables ci-dessus ont toutes été remplies, vous devrez peut-être passer à l’étape suivante pour collecter les informations de diagnostic et nous les envoyer.

> [!div class="nextstepaction"]
> [Collecter des données de diagnostic pour la résolution des problèmes de conformité des mises à jour](collect-diagnostic-data.md)

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
