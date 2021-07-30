---
title: Résoudre les problèmes liés aux outils de rapport pour Microsoft Defender AV
description: Identifier et résoudre les problèmes courants lors de la tentative de signalement de l’état de protection de l’Antivirus Microsoft Defender dans Update Compliance
keywords: résoudre les problèmes, erreur, corriger, mettre à jour la conformité, oms, surveiller, signaler, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 32de0d16d2a8e754a36d0def296b3913e2fc04d5
ms.sourcegitcommit: d817a3aecb700f7227a05cd165ffa7dbad67b09d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/29/2021
ms.locfileid: "53649802"
---
# <a name="troubleshoot-microsoft-defender-antivirus-reporting-in-update-compliance"></a>Résoudre des problèmes de rapports antivirus Microsoft Defender dans Conformité de la mise à jour

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

> [!IMPORTANT]
> Le 31 mars 2020, la fonctionnalité de Antivirus Microsoft Defender mise à jour de conformité sera supprimée. Vous pouvez continuer à définir et à passer en revue les stratégies de conformité de sécurité à l’aide de [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager), ce qui permet un contrôle plus fin des fonctionnalités de sécurité et des mises à jour.

Vous pouvez utiliser Antivirus Microsoft Defender conformité des mises à jour. Vous verrez l’état des licences E3, B, F1, VL et Pro licences. Toutefois, pour les licences E5, vous devez utiliser le [portail Microsoft Defender pour points de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) Pour en savoir plus sur les options de licence, [voir Windows 10 options de licence de produit.](https://www.microsoft.com/licensing/product-licensing/windows10.aspx)

Lorsque vous utilisez [Windows Analytics Update Compliance](/windows/deployment/update/update-compliance-using#wdav-assessment) pour obtenir des rapports sur l’état de protection des appareils ou des points de terminaison de votre réseau qui utilisent Antivirus Microsoft Defender, vous pouvez rencontrer des problèmes ou des problèmes.

En règle générale, les indicateurs les plus courants d’un problème sont :
- Vous ne voyez qu’un petit nombre ou un sous-ensemble de tous les appareils que vous attendiez à voir
- Vous ne voyez aucun appareil
- Les rapports et les informations que vous voyez sont obsolètes (plus de quelques jours)

Pour les codes d’erreur courants et les ID d’événement liés au service Antivirus Microsoft Defender qui ne sont pas liés à la mise à jour de conformité, voir [Antivirus Microsoft Defender événements.](troubleshoot-microsoft-defender-antivirus.md) 

La résolution de ces problèmes se fait en trois étapes :

1. Vérifier que vous avez satisfait à toutes les conditions préalables
2. Vérifier votre connectivité au service Windows Defender cloud
3. Envoyer les journaux de support

>[!IMPORTANT]
>L’apparition des appareils dans update Compliance prend généralement 3 jours.


## <a name="confirm-prerequisites"></a>Confirmer les conditions préalables

Pour que les appareils s’affichent correctement dans Update Compliance, vous devez respecter certains prérequis pour le service de conformité des mises à jour et pour les Antivirus Microsoft Defender :

>[!div class="checklist"]
>- Les points de terminaison utilisent Antivirus Microsoft Defender comme seule application de protection antivirus. [L’utilisation d’une autre application antivirus](microsoft-defender-antivirus-compatibility.md) entraîne la désactivation de Microsoft Defender AV et le point de terminaison n’est pas signalé dans Update Compliance.
> - [La protection cloud est activée.](enable-cloud-protection-microsoft-defender-antivirus.md)
> - Les points de terminaison [peuvent se connecter au cloud de Microsoft Defender AV](configure-network-connections-microsoft-defender-antivirus.md#validate-connections-between-your-network-and-the-cloud)
> - Si le point de terminaison Windows 10 version 1607 ou antérieure, les données de diagnostic Windows 10 doivent être définies sur [le niveau Amélioré.](/windows/configuration/configure-windows-diagnostic-data-in-your-organization#enhanced-level)
> - Cela fait 3 jours que toutes les conditions requises ont été satisfaites

« Vous pouvez utiliser Antivirus Microsoft Defender conformité des mises à jour. Vous verrez l’état des licences E3, B, F1, VL et Pro licences. Toutefois, pour les licences E5, vous devez utiliser le portail Microsoft Defender pour les points de terminaison (/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints). Pour en savoir plus sur les options de licence, voir Windows 10 options de licence de produit »

Si les conditions préalables ci-dessus ont toutes été remplies, vous devrez peut-être passer à l’étape suivante pour collecter des informations de diagnostic et nous les envoyer.

> [!div class="nextstepaction"]
> [Collecter des données de diagnostic pour la résolution des problèmes de conformité des mises à jour](collect-diagnostic-data.md)  

## <a name="related-topics"></a>Voir aussi

- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)