---
title: Configurer la correction pour la détection d’antivirus Microsoft Defender
description: Configurer ce que Antivirus Microsoft Defender doit faire lorsqu’il détecte une menace et combien de temps les fichiers mis en quarantaine doivent être conservés dans le dossier de mise en quarantaine
keywords: correction, correction, suppression, menaces, mise en quarantaine, analyse, restauration
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 03/16/2021
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 45886b94ec5ea11f01bfe23092eef4bd72691554
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274507"
---
# <a name="configure-remediation-for-microsoft-defender-antivirus-detections"></a>Configurer la correction pour la détection d’antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Lorsque Antivirus Microsoft Defender exécute une analyse, il tente de corriger ou de supprimer les menaces détectées. Vous pouvez configurer la façon dont Antivirus Microsoft Defender doit traiter certaines menaces, si un point de restauration doit être créé avant la correction et quand les menaces doivent être supprimées.

Cet article explique comment configurer ces paramètres à l’aide de la stratégie de groupe, mais vous pouvez également utiliser Microsoft Endpoint Configuration Manager [et](/configmgr/protect/deploy-use/endpoint-antimalware-policies#threat-overrides-settings) [Microsoft Intune](/intune/device-restrictions-configure). 

Vous pouvez également utiliser [ `Set-MpPreference` l’cmdlet PowerShell](/powershell/module/defender/set-mppreference) ou la [ `MSFT_MpPreference` classe WMI](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal) pour configurer ces paramètres.

## <a name="configure-remediation-options"></a>Configurer les options de correction

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur et **sélectionnez Modèles d’administration.**

3. Développez l’arborescence **Windows composants**  >  **Antivirus Microsoft Defender**. 

4. Dans le tableau ci-dessous, sélectionnez un emplacement, puis modifiez la stratégie selon vos besoins. 

5. Sélectionnez **OK**.

|Emplacement | Paramètre | Description | Paramètre par défaut (s’il n’est pas configuré) |
|:---|:---|:---|:---|
|Analyser | Créer un point de restauration du système | Un point de restauration système est créé chaque jour avant la tentative de nettoyage ou d’analyse | Désactivé|
|Analyser | Activer la suppression des éléments du dossier d’historique d’analyse | Spécifier le nombre de jours pendant combien d’éléments doivent être conservés dans l’historique d’analyse | 30 jours |
|Root | Désactiver la correction de routine | Vous pouvez spécifier si Antivirus Microsoft Defender les menaces sont automatiquement corrigés ou s’il doit demander à l’utilisateur du point de terminaison ce qu’il doit faire. | Désactivé (les menaces sont automatiquement corrigés) |
|Quarantaine | Configurer la suppression des éléments du dossier de mise en quarantaine | Spécifier le nombre de jours pendant combien d’éléments doivent être mis en quarantaine avant d’être supprimés | 90 jours |
|Menaces | Spécifier les niveaux d’alerte contre les menaces pour lesquels aucune action par défaut ne doit être prise lorsqu’elle est détectée | Chaque menace détectée par le Antivirus Microsoft Defender est affectée à un niveau de menace (faible, moyen, élevé ou grave). Vous pouvez utiliser ce paramètre pour définir comment toutes les menaces pour chacun des niveaux de menace doivent être corrigés (mis en quarantaine, supprimés ou ignorés) | Non applicable |
|Menaces | Spécifier les menaces sur lesquelles l’action par défaut ne doit pas être prise lorsqu’elle est détectée | Spécifiez comment les menaces spécifiques (à l’aide de leur ID de menace) doivent être corrigés. Vous pouvez spécifier si la menace spécifique doit être mise en quarantaine, supprimée ou ignorée | Non applicable |

> [!IMPORTANT]
> Antivirus Microsoft Defender détecte et remédie aux fichiers en fonction de nombreux facteurs. Parfois, la réalisation d’une correction nécessite un redémarrage. Même si la détection est ultérieurement déterminée comme faux positif, le redémarrage doit être effectué pour s’assurer que toutes les autres étapes de correction ont été effectuées.
>
> Si vous êtes certain Antivirus Microsoft Defender mis en quarantaine un fichier basé sur un faux positif, vous pouvez le restaurer à partir de la quarantaine après le redémarrage de l’appareil. Voir [Restaurer les fichiers mis en quarantaine dans Antivirus Microsoft Defender](restore-quarantined-files-microsoft-defender-antivirus.md).
> 
> Pour éviter ce problème à l’avenir, vous pouvez exclure des fichiers des analyses. Voir [Configurer et valider les exclusions pour Antivirus Microsoft Defender analyses.](configure-exclusions-microsoft-defender-antivirus.md)

Voir également Configurer des analyses complètes Antivirus Microsoft Defender des [corrections requises](scheduled-catch-up-scans-microsoft-defender-antivirus.md#remed) pour la correction.

## <a name="see-also"></a>Voir aussi

- [Configurer les options d’analyse de l’antivirus Microsoft Defender](configure-advanced-scan-types-microsoft-defender-antivirus.md)
- [Configurer des analyses de Antivirus Microsoft Defender programmées](scheduled-catch-up-scans-microsoft-defender-antivirus.md)
- [Configurer et exécuter des analyses à la demande avec l’antivirus Microsoft Defender](run-scan-microsoft-defender-antivirus.md).
- [Configurer les notifications qui s’affichent sur les points de terminaison](configure-notifications-microsoft-defender-antivirus.md)
- [Configurer l’interaction de l’utilisateur Antivirus Microsoft Defender fin](configure-end-user-interaction-microsoft-defender-antivirus.md)
- [Personnaliser, lancer et passer en revue les résultats des analyses et Antivirus Microsoft Defender correction](customize-run-review-remediate-scans-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)