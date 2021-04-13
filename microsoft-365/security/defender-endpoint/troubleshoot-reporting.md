---
title: Résoudre les problèmes liés aux outils de rapport pour Microsoft Defender AV
description: Identifier et résoudre les problèmes courants lors de la tentative de signalement de l'état de protection de l'Antivirus Microsoft Defender dans Update Compliance
keywords: résoudre les problèmes, erreur, corriger, mettre à jour la conformité, oms, surveiller, signaler, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 3b1a1c807c86aa95148300298484319001b59963
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690771"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Résoudre les problèmes de rapport de l'Antivirus Microsoft Defender dans Update Compliance

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

> [!IMPORTANT]
> Le 31 mars 2020, la fonctionnalité de rapport de l'Antivirus Microsoft Defender de la conformité des mises à jour sera supprimée. Vous pouvez continuer à définir et à passer en revue les stratégies de conformité de sécurité à l'aide de [Microsoft Endpoint Manager,](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager)ce qui permet un contrôle plus fin sur les fonctionnalités de sécurité et les mises à jour.

Vous pouvez utiliser l'Antivirus Microsoft Defender avec update compliance. Vous verrez l'état des licences E3, B, F1, VL et Pro. Toutefois, pour les licences E5, vous devez utiliser le [portail Microsoft Defender pour points de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) Pour en savoir plus sur les options de licence, voir les options de licence de produit [Windows 10.](https://www.microsoft.com/licensing/product-licensing/windows10.aspx)

Lorsque vous utilisez la conformité des mises à jour [Windows Analytics](/windows/deployment/update/update-compliance-using#wdav-assessment) pour obtenir des rapports sur l'état de protection des appareils ou des points de terminaison de votre réseau qui utilisent l'Antivirus Microsoft Defender, vous pouvez rencontrer des problèmes ou des problèmes.

En règle générale, les indicateurs les plus courants d'un problème sont :
- Vous ne voyez qu'un petit nombre ou un sous-ensemble de tous les appareils que vous attendiez à voir
- Vous ne voyez aucun appareil
- Les rapports et informations que vous voyez sont obsolètes (plus de quelques jours)

Pour obtenir des codes d'erreur courants et des ID d'événement liés au service Antivirus Microsoft Defender qui ne sont pas liés à update compliance, consultez les événements de [l'Antivirus Microsoft Defender.](troubleshoot-microsoft-defender-antivirus.md) 

La résolution de ces problèmes se fait en trois étapes :

1. Vérifier que vous avez satisfait à toutes les conditions préalables
2. Vérifier votre connectivité au service Windows Defender cloud
3. Envoyer les journaux de support

>[!IMPORTANT]
>L'apparition des appareils dans update Compliance prend généralement 3 jours.


## <a name="confirm-prerequisites"></a>Confirmer les conditions préalables

Pour que les appareils s'affichent correctement dans Update Compliance, vous devez respecter certaines conditions préalables pour le service de conformité des mises à jour et pour l'Antivirus Microsoft Defender :

>[!div class="checklist"]
>- Les points de terminaison utilisent l'Antivirus Microsoft Defender comme seule application de protection antivirus. [L'utilisation d'une autre application antivirus](microsoft-defender-antivirus-compatibility.md) entraîne la désactivation de Microsoft Defender AV et le point de terminaison n'est pas signalé dans Update Compliance.
> - [La protection cloud est activée.](enable-cloud-protection-microsoft-defender-antivirus.md)
> - Les points de terminaison [peuvent se connecter au cloud de Microsoft Defender AV](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Si le point de terminaison exécute Windows 10 version 1607 ou antérieure, les données de [diagnostic Windows 10](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level)doivent être définies sur le niveau Amélioré.
> - Cela fait 3 jours que toutes les conditions requises ont été satisfaites

« Vous pouvez utiliser l'Antivirus Microsoft Defender avec update compliance. Vous verrez l'état des licences E3, B, F1, VL et Pro. Toutefois, pour les licences E5, vous devez utiliser le portail Microsoft Defender pour points de terminaison ( https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) . Pour en savoir plus sur les options de licence, voir les options de licence de produit Windows 10 »

Si les conditions préalables ci-dessus ont toutes été remplies, vous devrez peut-être passer à l'étape suivante pour collecter des informations de diagnostic et nous les envoyer.

> [!div class="nextstepaction"]
> [Collecter des données de diagnostic pour le dépannage de la conformité des mises à jour](collect-diagnostic-data.md)  

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer l'Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)