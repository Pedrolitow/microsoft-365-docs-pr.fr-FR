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
ms.date: 07/20/2021
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.technology: mde
ms.openlocfilehash: b5c2694437333f197f3c9b04fd1f10fb581cd4d2
ms.sourcegitcommit: 87d994407fb69a747239b8589ad11ddf9b47e527
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2021
ms.locfileid: "53596109"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Détection et réponse des points de terminaison (PEPT) en mode blocage

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Qu’est-ce PEPT en mode bloc ?

[La](overview-endpoint-detection-response.md) détection et la réponse des points de terminaison (PEPT) en mode bloc offrent une protection supplémentaire contre les artefacts malveillants lorsque Antivirus Microsoft Defender n’est pas le produit antivirus principal et s’exécute en mode passif. PEPT en mode blocage fonctionne en arrière-plan pour corriger les artefacts malveillants détectés par PEPT fonctionnalités. Ces artefacts ont peut-être été manqués par le produit antivirus principal non Microsoft. 

> [!IMPORTANT]
> PEPT en mode bloc ne fournit pas toute la protection disponible lorsque Antivirus Microsoft Defender protection en temps réel est activée. Toutes les fonctionnalités qui dépendent Antivirus Microsoft Defender être la solution antivirus active ne fonctionneront pas, y compris les exemples clés suivants : 
> 
> - La protection en temps réel, y compris l’analyse sur accès, n’est pas disponible lorsque Antivirus Microsoft Defender est en mode passif. Pour en savoir plus sur les paramètres de stratégie de protection en temps réel, voir Activer et **[configurer Antivirus Microsoft Defender protection toujours active.](configure-real-time-protection-microsoft-defender-antivirus.md)**
> - Les fonctionnalités telles **[que les règles de protection](network-protection.md)** du réseau et de réduction de la **[surface](attack-surface-reduction.md)** d’attaque sont disponibles uniquement lorsque Antivirus Microsoft Defender est en cours d’exécution en mode actif. 
> 
> Votre solution antivirus non-Microsoft devrait fournir ces fonctionnalités. 

PEPT en mode bloc est intégré aux [menaces](next-gen-threat-and-vuln-mgt.md)& gestion des vulnérabilités . L’équipe de sécurité de [](tvm-security-recommendation.md) votre organisation reçoit une recommandation de sécurité pour activer PEPT en mode blocage s’il n’est pas déjà activé. 

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="recommandation pour activer l’PEPT en mode blocage":::

> [!TIP]
> Pour obtenir la meilleure protection possible, veillez à déployer Microsoft Defender pour les lignes de base **[de point de terminaison.](configure-machines-security-baseline.md)**

## <a name="what-happens-when-something-is-detected"></a>Que se passe-t-il lorsqu’un quelque chose est détecté ?

Lorsque PEPT en mode bloc est allumé et qu’un artefact malveillant est détecté, Microsoft Defender pour le point de terminaison bloque et remédie à cet artefact. Votre équipe des opérations  de  sécurité verra l’état de détection bloqué ou interdit dans le centre de gestion [des](respond-machine-alerts.md#check-activity-details-in-action-center)actions, répertorié comme des actions terminées.

L’image suivante montre une instance des logiciels indésirables détectés et bloqués par PEPT en mode blocage :

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="PEPT en mode blocage a détecté quelque chose":::


## <a name="enable-edr-in-block-mode"></a>Activer PEPT en mode bloc

> [!TIP]
> Assurez-vous que [les conditions](#requirements-for-edr-in-block-mode) requises sont remplies avant d’PEPT en mode bloc.

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com/](https://security.microsoft.com/) ) and sign in. 

2. Choose **Paramètres**  >  **Endpoints**  >  **General**  >  **Advanced features**.

3. Faites défiler vers le bas, puis activez **Activer PEPT en mode bloc.**


> [!NOTE]
> PEPT en mode bloc ne peut être allumé que dans le portail Microsoft 365 Defender ( ) ou [https://security.microsoft.com](https://security.microsoft.com) l’ancien Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ). Vous ne pouvez pas utiliser les clés de Registre, les Microsoft Intune ou la stratégie de groupe pour activer ou désactiver les PEPT en mode blocage.

## <a name="requirements-for-edr-in-block-mode"></a>Conditions requises pour PEPT en mode bloc

| Conditions requises  | Détails  |
|---------|---------|
| Autorisations | Le rôle Administrateur général ou Administrateur de la sécurité doit être attribué [dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Pour plus d’informations, voir [Autorisations de base.](basic-permissions.md) |
| Système d’exploitation     | Les appareils doivent être en cours d’exécution dans l’une des versions Windows : <br/>- Windows 10 (toutes les releases) <br/>- Windows Server, version 1803 ou plus récente <br/>- Windows Server 2019 <br/>- Windows Server 2016 (uniquement lorsque Antivirus Microsoft Defender est en mode actif)     |
| Microsoft Defender pour point de terminaison     | Les appareils doivent être intégrés à Defender for Endpoint. Voir [conditions minimales requises pour Microsoft Defender pour le point de terminaison.](minimum-requirements.md)       |
| Antivirus Microsoft Defender  | Les appareils doivent être Antivirus Microsoft Defender et s’exécutent en mode actif ou passif. [Confirmez Antivirus Microsoft Defender est en mode actif ou passif.](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode) |
| Protection fournie par le cloud | Antivirus Microsoft Defender doivent être configurées de telle manière que la protection cloud [soit activée.](enable-cloud-protection-microsoft-defender-antivirus.md) |
| Antivirus Microsoft Defender plateforme | Les appareils doivent être à jour. Pour confirmer, à l’aide de PowerShell, exécutez l’cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la **ligne AMProductVersion,** vous devriez voir **4.18.2001.10** ou version supérieure. <p> Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md). |
| Antivirus Microsoft Defender de recherche | Les appareils doivent être à jour. Pour confirmer, à l’aide de PowerShell, exécutez l’cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la **ligne AMEngineVersion,** vous devriez voir **1.1.16700.2** ou version supérieure. <p> Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md). |

> [!IMPORTANT]
> Pour obtenir la meilleure valeur de protection, assurez-vous que votre solution antivirus est configurée pour recevoir des mises à jour régulières et des fonctionnalités essentielles, et que vos [exclusions sont configurées.](configure-exclusions-microsoft-defender-antivirus.md) PEPT en mode bloc respecte les exclusions définies pour Antivirus Microsoft Defender, [](manage-indicators.md) mais pas les indicateurs définis pour Microsoft Defender pour endpoint.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées 

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Ai-je besoin d’activer PEPT en mode blocage si j’ai Antivirus Microsoft Defender en cours d’exécution sur des appareils ?

L’objectif principal des PEPT en mode blocage est de corriger les détections post-violation qui ont été manquées par un produit antivirus non-Microsoft. Toutefois, nous vous recommandons de PEPT en mode bloc, que Antivirus Microsoft Defender s’exécute en mode passif ou actif. 

- Lorsque Antivirus Microsoft Defender est en mode passif, PEPT en mode bloc fournit une autre couche de défense avec Microsoft Defender pour le point de terminaison. 
- Lorsque Antivirus Microsoft Defender est en mode actif, PEPT en mode blocage ne fournit pas d’analyse supplémentaire, mais il permet à Defender for Endpoint d’agir automatiquement sur les détections de PEPT comportement après violation.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>La PEPT en mode blocage affectera-t-elle la protection antivirus d’un utilisateur ? 

PEPT en mode blocage n’affecte pas la protection antivirus tierce en cours d’exécution sur les appareils des utilisateurs. PEPT en mode blocage fonctionne si la solution antivirus principale manque quelque chose ou s’il existe une détection post-violation. PEPT en mode bloc fonctionne comme Antivirus Microsoft Defender en mode passif, sauf que les PEPT en mode blocage bloquent et remédient également aux artefacts ou comportements malveillants détectés.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Pourquoi dois-je maintenir la Antivirus Microsoft Defender à jour ? 

Comme Antivirus Microsoft Defender détecte et remédie aux éléments malveillants, il est important de le maintenir à jour. Pour que PEPT en mode bloc soit efficace, il utilise les derniers modèles d’apprentissage des appareils, les détections comportementales et l’heuristique. La [pile de fonctionnalités defender](microsoft-defender-endpoint.md) pour point de terminaison fonctionne de manière intégrée. Pour obtenir la meilleure valeur de protection, vous devez Antivirus Microsoft Defender à jour. Voir [Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base.](manage-updates-baselines-microsoft-defender-antivirus.md) 

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Pourquoi avons-nous besoin de la protection cloud (MAPS) ? 

La protection cloud est nécessaire pour activer la fonctionnalité sur l’appareil. La protection cloud permet à [Defender for Endpoint](microsoft-defender-endpoint.md) de fournir la dernière et la plus grande protection en fonction de notre étendue et de notre profondeur d’intelligence de la sécurité, ainsi que des modèles d’apprentissage du comportement et des appareils.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Quelle est la différence entre le mode actif et le mode passif ?

Pour les points de terminaison exécutant Windows 10, Windows Server, version 1803 ou ultérieure ou Windows Server 2019, lorsque Antivirus Microsoft Defender est en mode actif, il est utilisé comme antivirus principal sur l’appareil. Lors de l’exécution en mode passif, Antivirus Microsoft Defender n’est pas le produit antivirus principal. Dans ce cas, les menaces ne sont pas Antivirus Microsoft Defender en temps réel.

> [!NOTE]
> Antivirus Microsoft Defender peut s’exécuter en mode passif uniquement lorsque l’appareil est intégré à Microsoft Defender pour Endpoint.

Pour plus d’informations, [voir Antivirus Microsoft Defender compatibilité.](microsoft-defender-antivirus-compatibility.md)

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Comment puis-je confirmer Antivirus Microsoft Defender est en mode actif ou passif ?

Pour vérifier si Antivirus Microsoft Defender est en cours d’exécution en mode actif ou passif, vous pouvez utiliser l’invite de commandes ou PowerShell sur un appareil exécutant Windows.

|Méthode  |Procedure  |
|---------|---------|
| PowerShell     | 1. Sélectionnez le menu Démarrer, commencez à taper, puis `PowerShell` ouvrez Windows PowerShell dans les résultats. <p>2. `Get-MpComputerStatus` Tapez . <p>3. Dans la liste des résultats, dans la ligne **AMRunningMode,** recherchez l’une des valeurs suivantes : <br/>- `Normal` <br/>- `Passive Mode` <p>Pour plus d’informations, [voir Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).        |
|Invite de commandes     | 1. Sélectionnez le menu Démarrer, commencez à taper, puis Windows invite de commandes `Command Prompt` dans les résultats. <p>2. `sc query windefend` Tapez . <p>3. Dans la liste des résultats, dans la **ligne STATE,** confirmez que le service est en cours d’exécution.         |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Comment puis-je confirmer que PEPT en mode bloc est Antivirus Microsoft Defender en mode passif ?

Vous pouvez utiliser PowerShell pour vérifier que les PEPT en mode bloc sont Antivirus Microsoft Defender en mode passif.

1. Sélectionnez la menu Démarrer, commencez à taper, puis `PowerShell` ouvrez Windows PowerShell dans les résultats. 

2. Tapez `Get-MPComputerStatus | select AMRunningMode`.

3. Confirmez que le résultat, `EDR Block Mode` , s’affiche.

   > [!TIP]
   > Si Antivirus Microsoft Defender est en mode actif, vous le verrez `Normal` à la place de `EDR Block Mode` . Pour plus d’informations, [voir Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016"></a>Le PEPT en mode bloc est-il pris en charge sur Windows Server 2016 ?

Si Antivirus Microsoft Defender est en cours d’exécution en mode actif ou passif, PEPT en mode bloc est pris en charge des versions suivantes de Windows :

- Windows 10 (toutes les publications)
- Windows Serveur, version 1803 ou plus récente 
- Windows Server 2019 

#### <a name="what-about-windows-server-2016"></a>Qu’en est-il Windows Server 2016 ? 

Si Windows Server 2016 a Antivirus Microsoft Defender en mode actif et que le point de terminaison est intégré à Defender pour le point de terminaison, PEPT en mode bloc est techniquement pris en charge. Toutefois, PEPT en mode blocage est conçu pour être une protection supplémentaire lorsque Antivirus Microsoft Defender n’est pas la solution antivirus principale sur un point de terminaison. Dans ce cas, Antivirus Microsoft Defender s’exécute en mode passif. 

Actuellement, l’exécution Antivirus Microsoft Defender en mode passif n’est pas prise en charge sur Windows Server 2016. Pour plus d’informations, voir Antivirus Microsoft Defender solutions [antivirus/anti-programme malveillant non-Microsoft.](microsoft-defender-antivirus-compatibility.md#microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions)

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Combien de temps faut-il pour que PEPT en mode bloc soit désactivé ?

Si vous choisissez de désactiver PEPT en mode blocage, la désactivation de cette fonctionnalité peut prendre jusqu’à 30 minutes pour le système.

## <a name="see-also"></a>Voir aussi

- [Blog tech Community : Présentation des PEPT en mode blocage : arrêt des attaques dans leurs pistes](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)
- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)

