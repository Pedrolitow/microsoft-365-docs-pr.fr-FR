---
title: Configurer la correction des détections de l'Antivirus Microsoft Defender
description: Configurer ce que l'Antivirus Microsoft Defender doit faire lorsqu'il détecte une menace et combien de temps les fichiers mis en quarantaine doivent être conservés dans le dossier de mise en quarantaine
keywords: correction, correction, suppression, menaces, mise en quarantaine, analyse, restauration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 03/16/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 7f41e9c5b38e93ce84fbd971e02ebc2d77432c3f
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690321"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Configurer la correction des détections de l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Lorsque l'Antivirus Microsoft Defender exécute une analyse, il tente de corriger ou de supprimer les menaces détectées. Vous pouvez configurer la façon dont l'Antivirus Microsoft Defender doit traiter certaines menaces, si un point de restauration doit être créé avant la correction et quand les menaces doivent être supprimées.

Cet article explique comment configurer ces paramètres à l'aide de la stratégie de groupe, mais vous pouvez également utiliser [Microsoft Endpoint Configuration Manager](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) et Microsoft [Intune.](/intune/device-restrictions-configure) 

Vous pouvez également utiliser [ `Set-MpPreference` l'cmdlet PowerShell](/powershell/module/defender/set-mppreference) ou la [ `MSFT_MpPreference` classe WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) pour configurer ces paramètres.

## <a name="configure-remediation-options"></a>Configurer les options de correction

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l'objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l'Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur et **sélectionnez Modèles d'administration.**

3. Développez l'arborescence **des composants Windows**  >  **de l'Antivirus Microsoft Defender.** 

4. Dans le tableau ci-dessous, sélectionnez un emplacement, puis modifiez la stratégie selon vos besoins. 

5. Sélectionnez **OK**.

|Emplacement | Paramètre | Description | Paramètre par défaut (s'il n'est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Créer un point de restauration du système | Un point de restauration système est créé chaque jour avant la tentative de nettoyage ou d'analyse | Désactivé|
|Analyser | Activer la suppression des éléments du dossier d'historique d'analyse | Spécifier le nombre de jours pendant combien d'éléments doivent être conservés dans l'historique d'analyse | 30 jours |
|Root | Désactiver la correction de routine | Vous pouvez spécifier si l'Antivirus Microsoft Defender remédie automatiquement aux menaces ou s'il doit demander à l'utilisateur du point de terminaison ce qu'il doit faire. | Désactivé (les menaces sont automatiquement corrigés) |
|Quarantaine | Configurer la suppression des éléments du dossier de mise en quarantaine | Spécifier le nombre de jours pendant combien d'éléments doivent être mis en quarantaine avant d'être supprimés | 90 jours |
|Menaces | Spécifier les niveaux d'alerte contre les menaces pour lesquels aucune action par défaut ne doit être prise lorsqu'elle est détectée | Chaque menace détectée par l'Antivirus Microsoft Defender se voit attribuer un niveau de menace (faible, moyen, élevé ou grave). Vous pouvez utiliser ce paramètre pour définir comment toutes les menaces pour chacun des niveaux de menace doivent être corrigés (mis en quarantaine, supprimés ou ignorés) | Non applicable |
|Menaces | Spécifier les menaces sur lesquelles l'action par défaut ne doit pas être prise lorsqu'elle est détectée | Spécifiez comment les menaces spécifiques (à l'aide de leur ID de menace) doivent être corrigés. Vous pouvez spécifier si la menace spécifique doit être mise en quarantaine, supprimée ou ignorée | Non applicable |

> [!IMPORTANT]
> L'Antivirus Microsoft Defender détecte et remédie aux fichiers en fonction de nombreux facteurs. Parfois, la réalisation d'une correction nécessite un redémarrage. Même si la détection est ultérieurement déterminée comme faux positif, le redémarrage doit être effectué pour s'assurer que toutes les autres étapes de correction ont été effectuées.
>
> Si vous êtes certain que l'Antivirus Microsoft Defender a mis en quarantaine un fichier basé sur un faux positif, vous pouvez le restaurer à partir de la quarantaine après le redémarrage de l'appareil. Voir [Restaurer les fichiers mis en quarantaine dans l'Antivirus Microsoft Defender.](restore-quarantined-files-microsoft-defender-antivirus.md)
> 
> Pour éviter ce problème à l'avenir, vous pouvez exclure des fichiers des analyses. Voir Configurer et valider les exclusions pour les analyses de [l'Antivirus Microsoft Defender.](configure-exclusions-microsoft-defender-antivirus.md)

Voir également Configurer les analyses complètes de [l'Antivirus Microsoft Defender requises](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) pour la correction afin d'obtenir d'autres paramètres liés à la correction.

## <a name="see-also"></a>Voir aussi

- [Configurer les options d'analyse de l'Antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Configurer des analyses de l'Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses de l'Antivirus Microsoft Defender à la demande](run-scan-microsoft-defender-antivirus.md)
- [Configurer les notifications qui apparaissent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
- [Configurer l'interaction de l'antivirus Microsoft Defender pour l'utilisateur final](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et des corrections de l'Antivirus Microsoft Defender](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)