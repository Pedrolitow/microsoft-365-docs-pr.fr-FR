---
title: Détection et réponse des points de terminaison en mode blocage
description: En savoir plus sur la détection et la réponse des points de terminaison en mode blocage
keywords: Microsoft Defender pour le point de terminaison, mde, EDR en mode bloc, blocage du mode passif
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.custom:
- next-gen
- edr
ms.date: 05/06/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: 78201fd20d689a6774eb5395aa787a2b15147972
ms.sourcegitcommit: 51b316c23e070ab402a687f927e8fa01cb719c74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/07/2021
ms.locfileid: "52274483"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Détection et réponse des points de terminaison (EDR) en mode blocage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Qu’est-ce que l’EDR en mode bloc ?

[La détection et la réponse](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) des points de terminaison (EDR) en mode blocage offrent une protection contre les artefacts malveillants, même lorsque l’Antivirus Microsoft Defender s’exécute en mode passif. Lorsqu’elle est allumée, l’EDR en mode blocage bloque les artefacts ou comportements malveillants détectés sur un appareil. L’EDR en mode blocage fonctionne en arrière-plan pour corriger les artefacts malveillants détectés après une violation. 

L’EDR en mode bloc est également intégrée à la gestion des [menaces & vulnérabilité.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) L’équipe de sécurité de [](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-security-recommendation) votre organisation reçoit une recommandation de sécurité pour activer EDR en mode blocage s’il n’est pas déjà activé. 

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="recommandation pour activer EDR en mode blocage":::

> [!NOTE]
> Pour obtenir la meilleure protection possible, veillez à déployer Microsoft Defender pour les lignes de base **[de point de terminaison.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)**

## <a name="what-happens-when-something-is-detected"></a>Que se passe-t-il lorsqu’un quelque chose est détecté ?

Lorsque l’EDR en mode bloc est allumé et qu’un artefact malveillant est détecté, Microsoft Defender pour le point de terminaison bloque et remédie cet artefact. Votre équipe des opérations  de  sécurité verra l’état de détection bloqué ou interdit dans le centre de gestion [des](respond-machine-alerts.md#check-activity-details-in-action-center)actions, répertorié comme des actions terminées.

L’image suivante montre une instance de logiciel indésirable détectée et bloquée via EDR en mode blocage :

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="L’EDR en mode bloc a détecté quelque chose":::


## <a name="enable-edr-in-block-mode"></a>Activer EDR en mode blocage

> [!IMPORTANT]
> Assurez-vous que [les conditions requises](#requirements-for-edr-in-block-mode) sont remplies avant d’allumer EDR en mode bloc.

1. Go to the Microsoft Defender Security Center ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) and sign in. 

2. Choose **Settings**  >  **Advanced features**.

3. Activer **EDR en mode bloc.**

> [!NOTE]
> EDR en mode blocage peut être uniquement allumé dans le Centre de sécurité Microsoft Defender. Vous ne pouvez pas utiliser les clés de Registre, Intune ou les stratégies de groupe pour activer ou désactiver l’EDR en mode blocage.

## <a name="requirements-for-edr-in-block-mode"></a>Conditions requises pour EDR en mode bloc

|Conditions requises  |Détails  |
|---------|---------|
|Autorisations |Rôle Administrateur général ou Administrateur de la sécurité attribué [dans Azure Active Directory.](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal) Voir [Autorisations de base.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/basic-permissions) |
|Système d’exploitation     |L’une des versions suivantes : <br/>- Windows 10 (toutes les publication) <br/>- Windows Server, version 1803 ou plus récente <br/>- Windows Server 2019 <br/>- Windows Server 2016 (uniquement lorsque l’Antivirus Microsoft Defender est en mode actif)     |
|Inscription à Windows E5     |Windows E5 est inclus dans les abonnements suivants : <br/>- Microsoft 365 E5 <br/>- Microsoft 365 E3 avec l’offre Protection contre les menaces & identité <br/><br/>Voir [Composants,](/microsoft-365/enterprise/microsoft-365-overview#components) [fonctionnalités et fonctionnalités pour chaque plan.](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)       |
|Antivirus Microsoft Defender  |L’Antivirus Microsoft Defender doit être installé et s’exécute en mode actif ou passif. (Vous pouvez utiliser l’Antivirus Microsoft Defender avec une solution antivirus non-Microsoft.) [Confirmez que l’Antivirus Microsoft Defender est en mode actif ou passif.](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode) |
|Protection fournie par le cloud |Assurez-vous que l’Antivirus Microsoft Defender est configuré de telle sorte que la protection livrée par le [cloud soit activée.](enable-cloud-protection-microsoft-defender-antivirus.md) |
|Client antivirus Microsoft Defender anti-programme malveillant |Assurez-vous que votre client est à jour. À l’aide de PowerShell, exécutez la cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la **ligne AMProductVersion,** vous devriez voir **4.18.2001.10** ou version supérieure. |
|Moteur antivirus Microsoft Defender |Assurez-vous que votre moteur est à jour. À l’aide de PowerShell, exécutez la cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la **ligne AMEngineVersion,** vous devriez voir **1.1.16700.2** ou version supérieure. |

> [!IMPORTANT]
> Pour obtenir la meilleure valeur de protection, assurez-vous que votre solution antivirus est configurée pour recevoir des mises à jour régulières et des fonctionnalités essentielles, et que vos [exclusions sont configurées.](configure-exclusions-microsoft-defender-antivirus.md) L’EDR en mode bloc respecte les exclusions définies pour l’Antivirus Microsoft Defender.

## <a name="frequently-asked-questions"></a>Foire aux questions 

### <a name="do-i-need-to-turn-edr-in-block-mode-on-even-when-i-have-microsoft-defender-antivirus-running-on-devices"></a>Ai-je besoin d’activer EDR en mode blocage, même lorsque l’Antivirus Microsoft Defender est en cours d’exécution sur les appareils ?

Nous vous recommandons de maintenir EDR en mode blocage, que l’Antivirus Microsoft Defender s’exécute en mode passif ou en mode actif. L’EDR en mode bloc fournit une autre couche de défense avec Microsoft Defender pour endpoint. Il permet à Defender for Endpoint d’prendre des mesures en fonction des détections EDR comportementales post-violation. 

### <a name="will-edr-in-block-mode-have-any-impact-on-a-users-antivirus-protection"></a>L’EDR en mode blocage aura-t-il un impact sur la protection antivirus d’un utilisateur ? 

L’EDR en mode blocage n’affecte pas la protection antivirus tierce en cours d’exécution sur les appareils des utilisateurs. L’EDR en mode blocage fonctionne si la solution antivirus principale manque quelque chose ou s’il existe une détection post-violation. L’EDR en mode blocage fonctionne comme l’Antivirus Microsoft Defender en [mode passif,](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state)sauf qu’il bloque et remédie également aux artefacts ou comportements malveillants détectés. 

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Pourquoi dois-je maintenir l’Antivirus Microsoft Defender à jour ? 

Étant donné que l’Antivirus Microsoft Defender détecte et remédie aux éléments malveillants, il est important de le maintenir à jour. Pour que l’EDR en mode bloc soit efficace, il utilise les derniers modèles d’apprentissage des appareils, les détections comportementales et l’heuristique. La [pile de fonctionnalités defender](microsoft-defender-endpoint.md) pour point de terminaison fonctionne de manière intégrée. Pour obtenir la meilleure valeur de protection, vous devez maintenir l’Antivirus Microsoft Defender à jour. Voir [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md) 

### <a name="why-do-we-need-cloud-protection-on"></a>Pourquoi avons-nous besoin de la protection cloud ? 

La protection cloud est nécessaire pour activer la fonctionnalité sur l’appareil. La protection cloud permet à [Defender for Endpoint](microsoft-defender-endpoint.md) de fournir la dernière et la plus grande protection en fonction de notre étendue et de notre profondeur d’intelligence de la sécurité, ainsi que des modèles d’apprentissage comportementaux et des appareils.

### <a name="how-do-i-set-microsoft-defender-antivirus-to-passive-mode"></a>Comment définir l’Antivirus Microsoft Defender en mode passif ?

Selon les systèmes d’exploitation, lorsque les appareils exécutant une solution antivirus/anti-programme malveillant non Microsoft sont intégrés à Defender pour le point de terminaison, l’Antivirus Microsoft Defender peut passer automatiquement en mode passif. Pour plus d’informations, [voir Antivirus et Microsoft Defender pour le point de terminaison.](microsoft-defender-antivirus-compatibility.md#antivirus-and-microsoft-defender-for-endpoint) 

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Comment vérifier que l’Antivirus Microsoft Defender est en mode actif ou passif ?

Pour vérifier si l’Antivirus Microsoft Defender s’exécute en mode actif ou passif, vous pouvez utiliser l’invite de commandes ou PowerShell sur un appareil exécutant Windows.


|Méthode  |Procedure  |
|---------|---------|
| PowerShell     | 1. Sélectionnez le menu Démarrer, commencez à taper, puis `PowerShell` ouvrez Windows PowerShell dans les résultats. <p>2. `Get-MpComputerStatus` Tapez . <p>3. Dans la liste des résultats, dans la ligne **AMRunningMode,** recherchez l’une des valeurs suivantes : <br/>- `Normal` <br/>- `Passive Mode` <br/>- `SxS Passive Mode` <p>Pour plus d’informations, [voir Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).        |
|Invite de commandes     | 1. Sélectionnez le menu Démarrer, commencez à taper, puis ouvrez l’invite de commandes `Command Prompt` Windows dans les résultats. <p>2. `sc query windefend` Tapez . <p>3. Dans la liste des résultats, dans la ligne **STATE,** confirmez que le service est en cours d’exécution.         |

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Combien de temps faut-il pour que l’EDR en mode bloc soit désactivé ?

Si vous avez choisi de désactiver l’EDR en mode blocage, la désactivation de cette fonctionnalité peut prendre jusqu’à 30 minutes pour le système.

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016"></a>EDR est-il pris en charge en mode blocage sur Windows Server 2016 ?

Si l’Antivirus Microsoft Defender s’exécute en mode actif ou passif, l’EDR en mode blocage est pris en charge par les versions suivantes de Windows :

- Windows 10 (toutes les publication)
- Windows Server, version 1803 ou plus récente 
- Windows Server 2019 

Si l’Antivirus Microsoft Defender de Windows Server 2016 est en cours d’exécution en mode actif et que le point de terminaison est intégré à Defender pour le point de terminaison, l’EDR en mode blocage est pris en charge. Toutefois, EDR en mode blocage est conçu pour être une protection supplémentaire lorsque l’Antivirus Microsoft Defender n’est pas la solution antivirus principale sur un point de terminaison. 

## <a name="see-also"></a>Voir aussi

- [Blog de la communauté technique : Présentation d’EDR en mode blocage : arrêt des attaques dans leurs pistes](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)
- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)
- [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/why-use-microsoft-antivirus)

