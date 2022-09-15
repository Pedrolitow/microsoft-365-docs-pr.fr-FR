---
title: Détection et réponse des points de terminaison en mode bloc
description: En savoir plus sur la détection et la réponse des points de terminaison en mode bloc
keywords: Microsoft Defender pour point de terminaison, mde, EDR en mode bloc, blocage en mode passif
ms.pagetype: security
author: denisebmsft
ms.author: deniseb
manager: dansimp
ms.reviewer: shwetaj
audience: ITPro
ms.topic: article
ms.service: microsoft-365-security
ms.localizationpriority: medium
ms.custom:
- next-gen
- edr
- admindeeplinkDEFENDER
ms.date: 08/19/2022
ms.collection: m365-security-compliance
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 8a0b8ebb8d839afd5417499fc010c829a6e33d99
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67698979"
---
# <a name="endpoint-detection-and-response-edr-in-block-mode"></a>Détection et réponse de point de terminaison (EDR) en mode bloc

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**

- Windows

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

## <a name="what-is-edr-in-block-mode"></a>Qu’est-ce qu’EDR en mode bloc ?

[La détection et la réponse](overview-endpoint-detection-response.md) des points de terminaison (EDR) en mode bloc offrent une protection supplémentaire contre les artefacts malveillants lorsque Microsoft Defender Antivirus (MDAV) n’est pas le produit antivirus principal et s’exécute en mode passif. EDR en mode bloc fonctionne en arrière-plan pour corriger les artefacts malveillants détectés par les fonctionnalités EDR. De tels artefacts peuvent avoir été manqués par le produit antivirus principal non-Microsoft. L’EDR en mode bloc permet à l’antivirus Microsoft Defender d’effectuer des actions en cas de détections EDR comportementales après violation. Consultez la section « [Dois-je activer EDR en mode bloc si j’ai l’antivirus Microsoft Defender ?](#do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices) » dans la section **Forum aux questions** .

> [!IMPORTANT]
> EDR en mode bloc ne fournit pas toutes les protections disponibles lorsque la protection en temps réel de l’Antivirus Microsoft Defender est activée. Certaines fonctionnalités qui dépendent de l’antivirus Microsoft Defender pour être la solution antivirus active ne fonctionneront pas, comme dans les exemples suivants :
>
> - La protection en temps réel, y compris l’analyse d’accès, n’est pas disponible lorsque l’Antivirus Microsoft Defender est en mode passif. Pour en savoir plus sur les paramètres de stratégie de protection en temps réel, consultez **[Activer et configurer la protection always on de l’antivirus Microsoft Defender](configure-real-time-protection-microsoft-defender-antivirus.md)**.
> - Des fonctionnalités telles que **[la protection réseau](network-protection.md)** et **[les règles de réduction de la surface d’attaque](attack-surface-reduction.md)** ne sont disponibles que lorsque l’Antivirus Microsoft Defender s’exécute en mode actif.
>
> Il est prévu que votre solution antivirus non-Microsoft inclut ces fonctionnalités.

EDR en mode bloc est intégré aux fonctionnalités de [gestion des menaces & des vulnérabilités](next-gen-threat-and-vuln-mgt.md) . L’équipe de sécurité de votre organisation recevra une [recommandation de sécurité](tvm-security-recommendation.md) pour activer EDR en mode bloc s’il n’est pas déjà activé. Cette recommandation concerne principalement les appareils qui utilisent une solution antivirus non Microsoft active (avec l’antivirus Microsoft Defender en mode passif). L’activation de l’EDR en mode bloc présente peu d’avantages lorsque l’antivirus Microsoft Defender est la solution antivirus principale sur les appareils.

:::image type="content" source="images/edrblockmode-TVMrecommendation.png" alt-text="Recommandation d’activer EDR en mode bloc" lightbox="images/edrblockmode-TVMrecommendation.png":::

> [!TIP]
> Pour obtenir la meilleure protection, veillez à **[déployer Microsoft Defender pour point de terminaison lignes de base](configure-machines-security-baseline.md)**.

Regardez cette vidéo pour savoir pourquoi et comment activer la détection et la réponse de point de terminaison (EDR) en mode bloc, activer le blocage comportemental et l’endiguement à chaque étape, de la pré-violation à la post-violation.
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4HjW2]

## <a name="what-happens-when-something-is-detected"></a>Que se passe-t-il lorsque quelque chose est détecté ?

Quand EDR en mode bloc est activé et qu’un artefact malveillant est détecté, Defender pour point de terminaison corrige cet artefact. Votre équipe des opérations de sécurité verra l’état de détection **comme Bloqué** ou **Empêché** dans le [Centre d’actions](respond-machine-alerts.md#check-activity-details-in-action-center), répertorié comme actions terminées. L’image suivante montre une instance de logiciels indésirables détectés et corrigés via EDR en mode bloc :

:::image type="content" source="images/edr-in-block-mode-detection.png" alt-text="Détection par EDR en mode bloc" lightbox="images/edr-in-block-mode-detection.png":::

## <a name="enable-edr-in-block-mode"></a>Activer EDR en mode bloc

> [!IMPORTANT]
> À compter de la plateforme version 4.18.2202.X, vous pouvez désormais définir EDR en mode bloc pour cibler des groupes d’appareils spécifiques à l’aide de Intune CSP. Vous pouvez continuer à définir EDR en mode bloc à l’échelle du locataire dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. L’EDR en mode bloc est principalement recommandé pour les appareils qui exécutent l’Antivirus Microsoft Defender en mode passif (une solution antivirus non Microsoft est installée et active sur l’appareil).

> [!TIP]
> Assurez-vous que les [exigences](#requirements-for-edr-in-block-mode) sont remplies avant d’activer EDR en mode bloc.

### <a name="security-portal"></a>Portail de sécurité

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)), puis connectez-vous.
1. Choisissez **les fonctionnalités avancées** **générales** \> \> **des points de terminaison de paramètres**\>.
1. Faites défiler vers le bas, puis **activez Activer EDR en mode bloc**.

### <a name="intune"></a>Intune

Pour créer une stratégie personnalisée dans Intune, consultez [Déployer OMA-URIs pour cibler un fournisseur de solutions Cloud via Intune et une comparaison avec l’environnement local](/troubleshoot/mem/intune/deploy-oma-uris-to-target-csp-via-intune).

Pour plus d’informations sur le fournisseur de solutions Cloud Defender utilisé pour EDR en mode bloc, consultez « Configuration/PassiveRemediation » sous [CSP Defender](/windows/client-management/mdm/defender-csp).

## <a name="requirements-for-edr-in-block-mode"></a>Configuration requise pour EDR en mode bloc

Le tableau suivant répertorie les exigences pour EDR en mode bloc :

|Conditions requises|Détails|
|---|---|
|Autorisations|Vous devez avoir le rôle Administrateur général ou Administrateur de sécurité attribué dans [Azure Active Directory](/azure/active-directory/fundamentals/active-directory-users-assign-role-azure-portal). Pour plus d’informations, consultez [Autorisations de base](basic-permissions.md).|
|Système d’exploitation|Les appareils doivent exécuter l’une des versions suivantes de Windows : <ul><li>Windows 11</li><li>Windows 10 (toutes les versions)</li><li>Windows Server 2019 ou version ultérieure</li><li>Windows Server, version 1803 ou ultérieure</li><li>Windows Server 2016 et Windows Server 2012 R2 \(avec la [nouvelle solution cliente unifiée](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution)\)</li></ul>|
|Microsoft Defender pour point de terminaison|Les appareils doivent être intégrés à Defender pour point de terminaison. Consultez les articles suivants : <br/>- [Exigences minimales pour Microsoft Defender pour point de terminaison](minimum-requirements.md)<br/>- [Intégrer des appareils et configurer des fonctionnalités Microsoft Defender pour point de terminaison](onboard-configure.md)<br/>- [Intégrer des serveurs Windows au service Defender pour point de terminaison](configure-server-endpoints.md)<br/>- [Nouvelles fonctionnalités Windows Server 2012 R2 et 2016 dans la solution unifiée moderne (préversion)](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) |
|Antivirus Microsoft Defender|L’Antivirus Microsoft Defender doit être installé et exécuté en mode actif ou passif sur les appareils. [Vérifiez que l’Antivirus Microsoft Defender est en mode actif ou passif](#how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode).|
|Protection fournie par le cloud|L’Antivirus Microsoft Defender doit être configuré de sorte que la [protection fournie par le cloud soit activée](enable-cloud-protection-microsoft-defender-antivirus.md).|
|Plateforme antivirus Microsoft Defender|Les appareils doivent être à jour. Pour confirmer, à l’aide de PowerShell, exécutez l’applet de commande [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la ligne **AMProductVersion** , vous devez voir **4.18.2001.10** ou version ultérieure. <p> Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).|
|Moteur antivirus Microsoft Defender|Les appareils doivent être à jour. Pour confirmer, à l’aide de PowerShell, exécutez l’applet de commande [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus) en tant qu’administrateur. Dans la ligne **AMEngineVersion** , vous devez voir **1.1.16700.2** ou version ultérieure. <p> Pour plus d’informations, consultez [Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).|

(<a id="fn1">1</a>) Voir [L’EDR en mode bloc est-il pris en charge sur Windows Server 2016 et Windows Server 2012 R2 ?](#is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2)

> [!IMPORTANT]
> Pour obtenir la meilleure valeur de protection, assurez-vous que votre solution antivirus est configurée pour recevoir des mises à jour régulières et [des fonctionnalités essentielles, et que vos exclusions sont configurées](configure-exclusions-microsoft-defender-antivirus.md). L’EDR en mode bloc respecte les exclusions définies pour l’antivirus Microsoft Defender, mais pas [les indicateurs](manage-indicators.md) définis pour Microsoft Defender pour point de terminaison.

## <a name="frequently-asked-questions"></a>Forum aux questions

### <a name="can-i-specify-exclusions-for-edr-in-block-mode"></a>Puis-je spécifier des exclusions pour EDR en mode bloc ?

En obtenant un faux positif, vous pouvez soumettre le fichier pour analyse sur le [site de soumission Renseignement de sécurité Microsoft](https://www.microsoft.com/en-us/wdsi/filesubmission).

Vous pouvez également définir une exclusion pour l’antivirus Microsoft Defender. Consultez [Configurer et valider les exclusions pour les analyses antivirus Microsoft Defender](configure-exclusions-microsoft-defender-antivirus.md).

### <a name="do-i-need-to-turn-edr-in-block-mode-on-if-i-have-microsoft-defender-antivirus-running-on-devices"></a>Dois-je activer EDR en mode bloc si l’antivirus Microsoft Defender s’exécute sur des appareils ?

L’objectif principal de l’EDR en mode bloc est de corriger les détections postérieures aux violations qui ont été manquées par un produit antivirus non-Microsoft. L’activation de l’EDR en mode bloc lorsque l’Antivirus Microsoft Defender est en mode actif présente un avantage minimal, car la protection en temps réel est censée intercepter et corriger les détections en premier. Nous vous recommandons d’activer EDR en mode bloc sur les points de terminaison où Microsoft Defender pour Antivirus s’exécute en mode passif. Les détections EDR peuvent être corrigées automatiquement par [la protection PUA](detect-block-potentially-unwanted-apps-microsoft-defender-antivirus.md) ou par [des fonctionnalités d’investigation automatisée & de correction](automated-investigations.md) en mode bloc.

### <a name="will-edr-in-block-mode-affect-a-users-antivirus-protection"></a>L’EDR en mode bloc affectera-t-il la protection antivirus d’un utilisateur ?

L’EDR en mode bloc n’affecte pas la protection antivirus tierce en cours d’exécution sur les appareils des utilisateurs. L’EDR en mode bloc fonctionne si la solution antivirus principale manque quelque chose ou s’il existe une détection post-violation. EDR en mode bloc fonctionne comme l’Antivirus Microsoft Defender en mode passif, sauf que l’EDR en mode bloc bloque et corrige également les artefacts ou comportements malveillants détectés.

### <a name="why-do-i-need-to-keep-microsoft-defender-antivirus-up-to-date"></a>Pourquoi dois-je maintenir l’antivirus Microsoft Defender à jour ?

Étant donné que l’Antivirus Microsoft Defender détecte et corrige les éléments malveillants, il est important de le tenir à jour. Pour que l’EDR en mode bloc soit efficace, il utilise les derniers modèles d’apprentissage des appareils, les détections comportementales et les heuristiques. La pile de fonctionnalités [Defender pour point de terminaison](microsoft-defender-endpoint.md) fonctionne de manière intégrée. Pour obtenir la meilleure valeur de protection, vous devez maintenir l’antivirus Microsoft Defender à jour. Consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).

### <a name="why-do-we-need-cloud-protection-maps-on"></a>Pourquoi avons-nous besoin d’une protection cloud (MAPS) activée ?

La protection cloud est nécessaire pour activer la fonctionnalité sur l’appareil. La protection cloud permet à [Defender pour point de terminaison](microsoft-defender-endpoint.md) de fournir la protection la plus récente et la plus efficace en fonction de notre étendue et de notre profondeur d’intelligence de sécurité, ainsi que des modèles d’apprentissage comportementaux et d’appareils.

### <a name="what-is-the-difference-between-active-and-passive-mode"></a>Quelle est la différence entre le mode actif et le mode passif ?

Pour les points de terminaison exécutant Windows 10, Windows 11, Windows Server, version 1803 ou ultérieure, Windows Server 2019 ou Windows Server 2022 lorsque l’antivirus Microsoft Defender est en mode actif, il est utilisé comme antivirus principal sur l’appareil. En mode passif, l’antivirus Microsoft Defender n’est pas le produit antivirus principal. Dans ce cas, les menaces ne sont pas corrigées par l’antivirus Microsoft Defender en temps réel.

> [!NOTE]
> L’Antivirus Microsoft Defender ne peut s’exécuter en mode passif que lorsque l’appareil est intégré à Microsoft Defender pour point de terminaison.

Pour plus d’informations, consultez [Compatibilité de l’antivirus Microsoft Defender](microsoft-defender-antivirus-compatibility.md).

### <a name="how-do-i-confirm-microsoft-defender-antivirus-is-in-active-or-passive-mode"></a>Comment faire confirmer que l’Antivirus Microsoft Defender est en mode actif ou passif ?

Pour vérifier si l’antivirus Microsoft Defender s’exécute en mode actif ou passif, vous pouvez utiliser l’invite de commandes ou PowerShell sur un appareil exécutant Windows.

|Méthode|Procedure|
|---|---|
|PowerShell|1. Sélectionnez le menu Démarrer, commencez à taper`PowerShell`, puis ouvrez Windows PowerShell dans les résultats.<br/><br/>2. Type `Get-MpComputerStatus`.<br/><br/>3. Dans la liste des résultats, dans la ligne **AMRunningMode** , recherchez l’une des valeurs suivantes :<br/>- `Normal`<br/>- `Passive Mode`<br/><br/>Pour en savoir plus, consultez [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).|
|Invite de commandes|<ol><li>Sélectionnez le menu Démarrer, commencez à taper `Command Prompt`, puis ouvrez l’invite de commandes Windows dans les résultats.</li><li>Tapez `sc query windefend`.</li><li>Dans la liste des résultats, dans la ligne **STATE** , vérifiez que le service est en cours d’exécution.</li></ol>|

### <a name="how-do-i-confirm-that-edr-in-block-mode-is-turned-on-with-microsoft-defender-antivirus-in-passive-mode"></a>Comment faire confirmer que l’EDR en mode bloc est activé avec l’Antivirus Microsoft Defender en mode passif ?

Vous pouvez utiliser PowerShell pour confirmer que l’EDR en mode bloc est activé avec l’antivirus Microsoft Defender exécuté en mode passif.

1. Sélectionnez le menu Démarrer, commencez à taper`PowerShell`, puis ouvrez Windows PowerShell dans les résultats.

2. Tapez `Get-MPComputerStatus|select AMRunningMode`.

3. Vérifiez que le résultat s’affiche `EDR Block Mode`.

   > [!TIP]
   > Si l’Antivirus Microsoft Defender est en mode actif, vous verrez `Normal` au lieu de `EDR Block Mode`. Pour en savoir plus, consultez [Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus).

### <a name="is-edr-in-block-mode-supported-on-windows-server-2016-and-windows-server-2012-r2"></a>EDR en mode bloc est-il pris en charge sur Windows Server 2016 et Windows Server 2012 R2 ?

Si l’Antivirus Microsoft Defender s’exécute en mode actif ou passif, EDR en mode bloc est pris en charge des versions suivantes de Windows :

- Windows 11
- Windows 10 (toutes les versions)
- Windows Server, version 1803 ou ultérieure
- Windows Server 2022
- Windows Server 2019
- Windows Server 2016 et Windows Server 2012 R2 (avec la [nouvelle solution cliente unifiée](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution))

Avec la [nouvelle solution cliente unifiée](configure-server-endpoints.md#new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution) pour Windows Server 2016 et Windows Server 2012 R2, vous pouvez exécuter EDR en mode bloc en mode passif ou en mode actif.

> [!NOTE]
> Windows Server 2016 et Windows Server 2012 R2 doivent être intégrés à l’aide des instructions fournies dans [les serveurs Windows intégrés](configure-server-endpoints.md) pour que cette fonctionnalité fonctionne.

### <a name="how-much-time-does-it-take-for-edr-in-block-mode-to-be-disabled"></a>Combien de temps faut-il pour désactiver EDR en mode bloc ?

Si vous choisissez de désactiver EDR en mode bloc, le système peut prendre jusqu’à 30 minutes pour désactiver cette fonctionnalité.

## <a name="see-also"></a>Voir aussi

- [Blog tech community : Présentation de l’EDR en mode bloc : Arrêt des attaques sur leurs traces](https://techcommunity.microsoft.com/t5/microsoft-defender-atp/introducing-edr-in-block-mode-stopping-attacks-in-their-tracks/ba-p/1596617)

- [Blocage et confinement comportementaux](behavioral-blocking-containment.md)
