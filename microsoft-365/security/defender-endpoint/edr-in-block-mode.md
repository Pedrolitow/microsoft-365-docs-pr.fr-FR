---
title: Détection et réponse des points de terminaison en mode blocage
description: En savoir plus sur protection évolutive des points de terminaison en mode bloc
keywords: Microsoft Defender pour le point de terminaison, mde, PEPT en mode bloc, blocage du mode passif
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.prod: m365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.date: 03/18/2022
ms.collection: m365-security-compliance
ms.technology: mde
ms.openlocfilehash: 151fb8de088531b9a9f053fc2b5d3c433055e21f
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64473120"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Détection et réponse de point de terminaison (EDR) en mode bloc

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Qu’est-PEPT en mode bloc ?

[La](overview-endpoint-detection-response.md) détection et la réponse des points de terminaison (PEPT) en mode bloc offrent une protection supplémentaire contre les artefacts malveillants lorsque Antivirus Microsoft Defender n’est pas le produit antivirus principal et s’exécute en mode passif. PEPT en mode bloc fonctionne en arrière-plan pour corriger les artefacts malveillants détectés par PEPT fonctionnalités. Ces artefacts ont peut-être été manqués par le produit antivirus principal non Microsoft. Pour les appareils exécutant Antivirus Microsoft Defender comme antivirus principal, la PEPT en mode blocage fournit une couche supplémentaire de défense en permettant aux Antivirus Microsoft Defender d’agir automatiquement sur les détections de PEPT comportemental après violation.

> [!IMPORTANT]
> PEPT en mode blocage ne fournit pas toute la protection disponible lorsque Antivirus Microsoft Defender protection en temps réel est activée. Toutes les fonctionnalités qui dépendent Antivirus Microsoft Defender être la solution antivirus active ne fonctionneront pas, y compris les exemples clés suivants :
>
> - La protection en temps réel, y compris l’analyse à l’accès, n’est pas disponible Antivirus Microsoft Defender en mode passif. Pour en savoir plus sur les paramètres de stratégie de protection en temps réel, voir Activer et configurer **[Antivirus Microsoft Defender protection toujours active](configure-real-time-protection-microsoft-defender-antivirus.md)**.
>
> - Les fonctionnalités telles **[que les règles de protection](network-protection.md)** du réseau et de réduction de la **[surface](attack-surface-reduction.md)** d’attaque sont disponibles uniquement lorsque Antivirus Microsoft Defender est en cours d’exécution en mode actif.
>
> Votre solution antivirus non-Microsoft devrait fournir ces fonctionnalités.

PEPT mode bloc est intégré aux [menaces](next-gen-threat-and-vuln-mgt.md) & gestion des vulnérabilités. L’équipe de sécurité de votre organisation reçoit une recommandation de sécurité pour activer PEPT en mode blocage s’il n’est pas déjà activé.[](tvm-security-recommendation.md)

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="Recommandation d’activer la PEPT en mode bloc" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> Pour obtenir la meilleure protection possible, veillez à déployer **[Microsoft Defender pour les lignes de base de point de terminaison](configure-machines-security-baseline.md)**.

## <a name="what-happens-when-something-is-detected"></a>Que se passe-t-il lorsqu’un quelque chose est détecté ?

Lorsque PEPT en mode bloc est allumé et qu’un artefact malveillant est détecté, Microsoft Defender pour le point de terminaison bloque et remédie à cet artefact. Votre équipe des opérations de sécurité verra l’état  de détection bloqué ou interdit dans le centre de [gestion des actions](respond-machine-alerts.md#check-activity-details-in-action-center), répertorié comme actions terminées.

L’image suivante montre une instance de logiciel indésirable qui a été détectée et bloquée par PEPT en mode blocage :

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Détection par le PEPT en mode bloc" lightbox="images/edr-in-block-mode-detection.png":::


## <a name="enable-edr-in-block-mode"></a>Activer PEPT en mode bloc

> [!IMPORTANT]
> À partir de la version de plateforme 4.18.2202.X, vous pouvez désormais définir PEPT en mode blocage pour cibler des groupes d’appareils spécifiques à l’aide de CSP Intune. Vous pouvez continuer à définir des PEPT à l’échelle du client en mode <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">bloc dans Microsoft 365 Defender portail.</a> PEPT en mode blocage est principalement recommandé pour les appareils qui exécutent Antivirus Microsoft Defender en mode passif (une solution antivirus non Microsoft est installée et active sur l’appareil). 

> [!TIP]
> Assurez-vous que [les conditions requises](#requirements-for-edr-in-block-mode) sont remplies avant d’PEPT en mode bloc.

### <a name="security-portal"></a>Portail de sécurité 

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com/](https://security.microsoft.com/)) and sign in.

2. Choisissez **Paramètres** \> **fonctionnalités générales** \> avancées **des points de** \> **terminaison**.

3. Faites défiler vers le bas, puis activez **Activer PEPT en mode bloc**.

### <a name="intune"></a>Intune

Pour créer une stratégie personnalisée dans Intune, voir [Deploy OMA-URIs to target a CSP through Intune, and a comparison to on-premises](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Pour plus d’informations sur le CSP Defender utilisé pour PEPT en mode bloc, voir « Configuration/PassiveRemediation » sous [CSP Defender](/windows/client-management/mdm/defender-csp).


## <a name="requirements-for-edr-in-block-mode"></a>Conditions requises pour PEPT en mode bloc

Le tableau suivant répertorie les conditions requises pour PEPT en mode bloc :

|Conditions requises|Détails|
|---|---|
|Autorisations|Le rôle Administrateur général ou Administrateur de la sécurité doit être attribué [dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Pour plus d’informations, voir [Autorisations de base](basic-permissions.md).|
|Système d’exploitation|Les appareils doivent être en cours d’exécution dans l’une des versions Windows : <br/>- Windows 11 <br/>- Windows 10 (toutes les publications)<br/>- Windows Server 2022 <br/>- Windows Server 2019<br/>- Windows Server, version 1803 ou plus récente<br/>- Windows Server 2016 et Windows Server 2012 R2 (avec la [nouvelle solution cliente unifiée](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview))<sup>[[1](#fn1)]</sup>  |
|Microsoft Defender pour point de terminaison|Les appareils doivent être intégrés à Defender pour le point de terminaison. Consultez les articles suivants : <br/>- [Conditions minimales requises pour Microsoft Defender pour le point de terminaison](minimum-requirements.md)<br/>- [Intégrer des appareils et configurer Microsoft Defender pour les fonctionnalités de point de terminaison](onboard-configure.md)<br/>- [Intégrer Windows serveurs au service Defender for Endpoint](configure-server-endpoints.md)<br/>- [Nouvelles Windows Server 2012 R2 et 2016 dans la solution unifiée moderne (prévisualisation)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) |
|Antivirus Microsoft Defender|Les appareils doivent être Antivirus Microsoft Defender et s’exécutent en mode actif ou passif. [Confirmez Antivirus Microsoft Defender est en mode actif ou passif](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Protection fournie par le cloud|Antivirus Microsoft Defender doivent être configurées de telle manière que la [protection cloud soit activée](enable-cloud-protection-microsoft-defender-antivirus.md).|
|Antivirus Microsoft Defender plateforme|Les appareils doivent être à jour. Pour confirmer, à l’aide de PowerShell, exécutez l’cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la **ligne AMProductVersion** , vous devriez voir **4.18.2001.10** ou version supérieure. <p> Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Antivirus Microsoft Defender de recherche|Les appareils doivent être à jour. Pour confirmer, à l’aide de PowerShell, exécutez l’cmdlet [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la **ligne AMEngineVersion** , vous devriez voir **1.1.16700.2** ou version supérieure. <p> Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) [Consultez l’PEPT en mode bloc pris en charge sur Windows Server 2016 et Windows Server 2012 R2 ?](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> Pour obtenir la meilleure valeur de protection, assurez-vous que votre solution antivirus est configurée pour recevoir des mises à jour régulières et des [fonctionnalités essentielles, et que vos exclusions sont configurées](configure-exclusions-microsoft-defender-antivirus.md). PEPT en mode bloc respecte les exclusions définies pour Antivirus Microsoft Defender, mais pas les indicateurs définis pour Microsoft Defender pour [](manage-indicators.md) endpoint.

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>Puis-je spécifier des exclusions PEPT en mode bloc ?

Si vous obtenez un faux positif, vous pouvez envoyer le fichier pour analyse sur le [site Renseignement de sécurité Microsoft soumission](https://www.microsoft.com/en-us/wdsi/filesubmission).

Vous pouvez également définir une exclusion pour Antivirus Microsoft Defender. Voir [Configurer et valider les exclusions pour Antivirus Microsoft Defender analyses](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Ai-je besoin d’activer PEPT en mode blocage si j’ai Antivirus Microsoft Defender en cours d’exécution sur des appareils ?

L’objectif principal des PEPT en mode blocage est de corriger les détections post-violation qui ont été manquées par un produit antivirus non Microsoft. Toutefois, nous vous recommandons de PEPT en mode bloc, qu’Antivirus Microsoft Defender s’exécute en mode passif ou actif.

- Lorsque Antivirus Microsoft Defender est en mode passif, PEPT en mode bloc fournit une autre couche de défense avec Microsoft Defender pour le point de terminaison.

- Lorsque Antivirus Microsoft Defender est en mode actif, la PEPT en mode blocage ne fournit pas d’analyse supplémentaire, mais elle permet aux Antivirus Microsoft Defender d’agir automatiquement sur les détections de PEPT comportemental post-violation.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>La PEPT en mode blocage affectera-t-elle la protection antivirus d’un utilisateur ?

PEPT en mode blocage n’affecte pas la protection antivirus tierce en cours d’exécution sur les appareils des utilisateurs. PEPT en mode blocage fonctionne si la solution antivirus principale manque quelque chose ou s’il existe une détection post-violation. PEPT en mode bloc fonctionne comme Antivirus Microsoft Defender en mode passif, sauf que les PEPT en mode blocage bloquent et remédient également aux artefacts ou comportements malveillants détectés.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Pourquoi dois-je maintenir la Antivirus Microsoft Defender à jour ?

Comme Antivirus Microsoft Defender détecte et remédie aux éléments malveillants, il est important de le maintenir à jour. Pour que PEPT en mode bloc soit efficace, il utilise les derniers modèles d’apprentissage des appareils, les détections comportementales et l’heuristique. La [pile de fonctionnalités defender pour point](microsoft-defender-endpoint.md) de terminaison fonctionne de manière intégrée. Pour obtenir la meilleure valeur de protection, vous devez Antivirus Microsoft Defender à jour. Voir [Gérer Antivirus Microsoft Defender mises à jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Pourquoi avons-nous besoin de la protection cloud (MAPS) ?

La protection cloud est nécessaire pour activer la fonctionnalité sur l’appareil. La protection cloud permet à [Defender for Endpoint](microsoft-defender-endpoint.md) de fournir la dernière et la plus grande protection en fonction de notre étendue et de notre profondeur d’intelligence de la sécurité, ainsi que des modèles d’apprentissage comportementaux et des appareils.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Quelle est la différence entre le mode actif et le mode passif ?

Pour les points de terminaison exécutant Windows 10, Windows 11, Windows Server, version 1803 ou ultérieure, Windows Server 2019 ou Windows Server 2022 lorsque Antivirus Microsoft Defender est en mode actif, il est utilisé comme antivirus principal sur l’appareil. Lors de l’exécution en mode passif, Antivirus Microsoft Defender n’est pas le produit antivirus principal. Dans ce cas, les menaces ne sont pas Antivirus Microsoft Defender en temps réel.

> [!NOTE]
> Antivirus Microsoft Defender peut s’exécuter en mode passif uniquement lorsque l’appareil est intégré à Microsoft Defender pour endpoint.

Pour plus d’informations, [voir Antivirus Microsoft Defender compatibilité.](microsoft-defender-antivirus-compatibility.md)

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Comment puis-je confirmer Antivirus Microsoft Defender est en mode actif ou passif ?

Pour vérifier si Antivirus Microsoft Defender est en cours d’exécution en mode actif ou passif, vous pouvez utiliser l’invite de commandes ou PowerShell sur un appareil exécutant Windows.

|Méthode|Procedure|
|---|---|
|PowerShell|1. Sélectionnez le menu Démarrer, `PowerShell`commencez à taper, puis ouvrez Windows PowerShell dans les résultats.<br/><br/>2. Tapez `Get-MpComputerStatus`.<br/><br/>3. Dans la liste des résultats, dans la ligne **AMRunningMode** , recherchez l’une des valeurs suivantes :<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Pour plus d’informations, [voir Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Invite de commandes|1. Sélectionnez le menu Démarrer, `Command Prompt`commencez à taper, puis ouvrez Windows’invite de commandes dans les résultats.<br/><br/>2. Tapez `sc query windefend`.<br/><br/>3. Dans la liste des résultats, dans la ligne **STATE** , confirmez que le service est en cours d’exécution. |

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Comment puis-je confirmer que PEPT en mode bloc est Antivirus Microsoft Defender en mode passif ?

Vous pouvez utiliser PowerShell pour vérifier que PEPT en mode bloc est Antivirus Microsoft Defender en mode passif.

1. Sélectionnez le menu Démarrer, commencez à taper`PowerShell`, puis ouvrez Windows PowerShell dans les résultats.

2. Tapez `Get-MPComputerStatus|select AMRunningMode`.

3. Confirmez que le résultat, `EDR Block Mode`, s’affiche.

   > [!TIP]
   > Si Antivirus Microsoft Defender est en mode actif, vous le verrez `Normal` à la place de `EDR Block Mode`. Pour plus d’informations, [voir Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>Le PEPT en mode bloc est-il pris en charge sur Windows Server 2016 et Windows Server 2012 R2 ?

Si Antivirus Microsoft Defender est en cours d’exécution en mode actif ou passif, PEPT en mode bloc est pris en charge des versions suivantes de Windows :

- Windows 11
- Windows 10 (toutes les publications)
- Windows Server, version 1803 ou plus récente 
- Windows Server 2022
- Windows Server 2019 
- Windows Server 2016 et Windows Server 2012 R2 (avec la [nouvelle solution cliente unifiée](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview))

Avec la [nouvelle solution cliente](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution-preview) unifiée pour Windows Server 2016 et Windows Server 2012 R2, vous pouvez exécuter PEPT en mode blocage en mode passif ou actif.

> [!NOTE]
> Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions des serveurs Windows [intégrés](configure-server-endpoints.md) pour que cette fonctionnalité fonctionne. 

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Combien de temps faut-il pour que PEPT en mode bloc soit désactivé ?

Si vous choisissez de désactiver PEPT en mode blocage, la désactivation de cette fonctionnalité peut prendre jusqu’à 30 minutes pour le système.

## <a name="see-also"></a>Voir aussi

- [Blog tech Community : Présentation des PEPT en mode blocage : arrêt des attaques dans leurs pistes](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)
