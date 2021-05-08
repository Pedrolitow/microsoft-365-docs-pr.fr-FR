---
title: Détection et réponse des points de terminaison en mode blocage
description: En savoir plus sur protection évolutive des points de terminaison en mode bloc
keywords: Microsoft Defender pour le point de terminaison, mde, PEPT en mode bloc, blocage en mode passif
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
ms.date: 05/05/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: d7ab8afd1d643933dc71a5bef1385b9ab95b553f
ms.sourcegitcommit: ff20f5b4e3268c7c98a84fb1cbe7db7151596b6d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/06/2021
ms.locfileid: "52245803"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Détection et réponse des points de terminaison (PEPT) en mode blocage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Qu’est-ce PEPT en mode bloc ?

[La détection et la](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) réponse des points de terminaison (PEPT) en mode blocage offrent une protection contre les artefacts malveillants, même lorsque Antivirus Microsoft Defender est en cours d’exécution en mode passif. Lorsqu’elle est PEPT, elle bloque les artefacts ou comportements malveillants détectés sur un appareil. PEPT en mode blocage fonctionne en arrière-plan pour corriger les artefacts malveillants détectés après une violation. 

PEPT en mode bloc est également intégré aux [menaces](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt)& gestion des vulnérabilités . L’équipe de sécurité de [](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/tvm-security-recommendation) votre organisation reçoit une recommandation de sécurité pour activer PEPT en mode blocage s’il n’est pas déjà activé. 

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="recommandation pour activer l’PEPT en mode blocage":::

> [!NOTE]
> Pour obtenir la meilleure protection possible, veillez à déployer Microsoft Defender pour les lignes de base **[de point de terminaison.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/configure-machines-security-baseline)**

## <a name="what-happens-when-something-is-detected"></a>Que se passe-t-il lorsqu’un quelque chose est détecté ?

Lorsque PEPT en mode bloc est allumé et qu’un artefact malveillant est détecté, Microsoft Defender pour le point de terminaison bloque et remédie à cet artefact. Vous verrez l’état de détection **bloqué** ou interdit **en tant** qu’actions terminées dans le centre [de l’action.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/respond-machine-alerts#check-activity-details-in-action-center)

L’image suivante montre une instance des logiciels indésirables détectés et bloqués par PEPT en mode blocage :

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="PEPT en mode blocage a détecté quelque chose":::


## <a name="enable-edr-in-block-mode"></a>Activer PEPT en mode bloc

> [!IMPORTANT]
> Assurez-vous que [les conditions](#requirements-for-edr-in-block-mode) requises sont remplies avant d’PEPT en mode bloc.

1. Go to the Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) and sign in. 

2. Choisissez **Paramètres**  >  **fonctionnalités avancées.**

3. Activer PEPT **en mode bloc.**

> [!NOTE]
> PEPT en mode bloc ne peut être allumé que dans le Centre de sécurité Microsoft Defender. Vous ne pouvez pas utiliser les clés de Registre, Intune ou les stratégies de groupe pour activer ou désactiver les PEPT en mode bloc.

## <a name="requirements-for-edr-in-block-mode"></a>Conditions requises pour PEPT en mode bloc

|Conditions requises  |Détails  |
|---------|---------|
|Autorisations |Rôle Administrateur général ou Administrateur de la sécurité attribué [dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Voir [Autorisations de base.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/basic-permissions) |
|Système d’exploitation     |L’une des versions suivantes : <br/>- Windows 10 (toutes les releases) <br/>- Windows Server, version 1803 ou plus récente <br/>- Windows Server 2019  <p>**REMARQUE**: PEPT en mode bloc n’est pas pris en charge sur Windows Server 2016.       |
|Windows Inscription E5     |Windows E5 est inclus dans les abonnements suivants : <br/>- Microsoft 365 E5 <br/>- Microsoft 365 E3 avec l’offre Protection contre les menaces & identité <br/><br/>Voir [Composants,](https://docs.microsoft.com/microsoft-365/enterprise/microsoft-365-overview?view=o365-worldwide&preserve-view=true#components) [fonctionnalités et fonctionnalités pour chaque plan.](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans)       |
|Antivirus Microsoft Defender  |Antivirus Microsoft Defender doit être installé et s’exécute en mode actif ou passif. (Vous pouvez utiliser Antivirus Microsoft Defender’une solution antivirus non Microsoft.) [Confirmez Antivirus Microsoft Defender est en mode actif ou passif.](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode) |
|Protection fournie par le cloud |Assurez-vous Antivirus Microsoft Defender est configuré de telle sorte que la protection livrée [par le cloud soit activée.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/enable-cloud-protection-microsoft-defender-antivirus) |
|Antivirus Microsoft Defender logiciel anti-programme malveillant |Assurez-vous que votre client est à jour. À l’aide de PowerShell, exécutez la cmdlet [Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus?view=win10-ps&preserve-view=true) en tant qu’administrateur. Dans la **ligne AMProductVersion,** vous devriez voir **4.18.2001.10** ou version supérieure. |
|Antivirus Microsoft Defender de recherche |Assurez-vous que votre moteur est à jour. À l’aide de PowerShell, exécutez la cmdlet [Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus?view=win10-ps&preserve-view=true) en tant qu’administrateur. Dans la **ligne AMEngineVersion,** vous devriez voir **1.1.16700.2** ou version supérieure. |

> [!IMPORTANT]
> Pour obtenir la meilleure valeur de protection, assurez-vous que votre solution antivirus est configurée pour recevoir des mises à jour régulières et des fonctionnalités essentielles, et que vos [exclusions sont configurées.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-exclusions-microsoft-defender-antivirus) PEPT en mode bloc respecte les exclusions définies pour Antivirus Microsoft Defender.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées 

### <a name="do-i-need-to-turn-edr-in-block-mode-on-even-when-i-have-microsoft-defender-antivirus-running-on-devices"></a>Ai-je besoin d’activer PEPT en mode blocage, même lorsque j’ai Antivirus Microsoft Defender en cours d’exécution sur des appareils ?

Nous vous recommandons de PEPT en mode blocage, que Antivirus Microsoft Defender s’exécute en mode passif ou actif. PEPT mode bloc fournit une autre couche de défense avec Microsoft Defender pour endpoint. Il permet à Defender for Endpoint d’prendre des mesures en fonction des détections de PEPT de comportement post-violation. 

### <a name="will-edr-in-block-mode-have-any-impact-on-a-users-antivirus-protection"></a>Les PEPT en mode blocage auront-ils un impact sur la protection antivirus d’un utilisateur ? 

PEPT en mode blocage n’affecte pas la protection antivirus tierce en cours d’exécution sur les appareils des utilisateurs. PEPT en mode blocage fonctionne si la solution antivirus principale manque quelque chose ou s’il existe une détection post-violation. PEPT en mode bloc fonctionne comme Antivirus Microsoft Defender en [mode passif,](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/microsoft-defender-antivirus-compatibility#functionality-and-features-available-in-each-state)sauf qu’il bloque et remédie également aux artefacts ou comportements malveillants détectés. 

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Pourquoi dois-je maintenir la Antivirus Microsoft Defender à jour ? 

Comme Antivirus Microsoft Defender détecte et remédie aux éléments malveillants, il est important de le maintenir à jour. Pour que PEPT en mode bloc soit efficace, il utilise les derniers modèles d’apprentissage des appareils, les détections comportementales et l’heuristique. La [pile de fonctionnalités defender](https://docs.microsoft.com/windows/security/threat-protection) pour point de terminaison fonctionne de manière intégrée. Pour obtenir la meilleure valeur de protection, vous devez Antivirus Microsoft Defender à jour.  

### <a name="why-do-we-need-cloud-protection-on"></a>Pourquoi avons-nous besoin de la protection cloud ? 

La protection cloud est nécessaire pour activer la fonctionnalité sur l’appareil. La protection cloud permet à [Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection) de fournir la dernière et la plus grande protection en fonction de notre étendue et de notre profondeur d’intelligence de la sécurité, ainsi que des modèles d’apprentissage du comportement et des appareils.

### <a name="how-do-i-set-microsoft-defender-antivirus-to-passive-mode"></a>Comment définir Antivirus Microsoft Defender en mode passif ?

Voir [Activer Antivirus Microsoft Defender et vérifier qu’il est en mode passif.](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/switch-to-microsoft-defender-setup#enable-microsoft-defender-antivirus-and-confirm-its-in-passive-mode)

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Comment puis-je confirmer Antivirus Microsoft Defender est en mode actif ou passif ?

Pour vérifier si Antivirus Microsoft Defender est en cours d’exécution en mode actif ou passif, vous pouvez utiliser l’invite de commandes ou PowerShell sur un appareil exécutant Windows.

#### <a name="use-powershell"></a>Utiliser PowerShell

1. Sélectionnez le menu Démarrer, commencez à taper, puis `PowerShell` ouvrez Windows PowerShell dans les résultats.

2. Tapez `Get-MpComputerStatus`.

3. Dans la liste des résultats, dans la ligne **AMRunningMode,** recherchez l’une des valeurs suivantes :   
   - `Normal`
   - `Passive Mode`  
   - `SxS Passive Mode`

Pour plus d’informations, [voir Get-MpComputerStatus](https://docs.microsoft.com/powershell/module/defender/get-mpcomputerstatus).

#### <a name="use-command-prompt"></a>Utiliser l’invite de commandes

1. Sélectionnez le menu Démarrer, commencez à taper, puis ouvrez `Command Prompt` Windows invite de commandes dans les résultats.

2. Tapez `sc query windefend`.

3. Dans la liste des résultats, dans la **ligne STATE,** confirmez que le service est en cours d’exécution.

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Combien de temps faut-il pour que PEPT en mode bloc soit désactivé ?

Si vous avez choisi de désactiver les PEPT en mode blocage, cela peut prendre jusqu’à 30 minutes pour que le système désactive cette fonctionnalité.

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016"></a>Le PEPT en mode bloc est-il pris en charge sur Windows Server 2016 ?

Non. PEPT en mode bloc est pris en charge par les versions suivantes de Windows :

- Windows 10 (toutes les publications)
- Windows Serveur, version 1803 ou plus récente 
- Windows Server 2019 

## <a name="see-also"></a>Voir aussi

- [Blog tech Community : Présentation des PEPT en mode blocage : arrêt des attaques dans leurs pistes](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)
- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)
- [Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/why-use-microsoft-antivirus)

