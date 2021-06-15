---
title: Protéger les paramètres de sécurité avec la protection contre la falsifiation
ms.reviewer: shwjha, hayhov
manager: dansimp
description: Utilisez la protection contre la falsification pour empêcher les applications malveillantes de modifier les paramètres de sécurité importants.
keywords: programmes malveillants, defender, antivirus, protection contre la falsification
search.product: eADQiWindows 10XVcnh
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.technology: mde
ms.date: 05/17/2021
ms.openlocfilehash: f6217cccf79b951c3103e1024ac74669d68645cd
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925934"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Protéger les paramètres de sécurité avec la protection contre la falsifiation

**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

La protection contre la falsification est disponible pour les appareils qui exécutent l’une des versions suivantes de Windows :

- Windows 10
- Windows Server 2019
- Windows Serveur, version 1803 ou ultérieure
- Windows Server 2016

## <a name="overview"></a>Vue d’ensemble

Pendant certains types de cyberattaques, les acteurs malveillants tentent de désactiver les fonctionnalités de sécurité, telles que la protection antivirus, sur vos ordinateurs. Les acteurs malveillants aiment désactiver vos fonctionnalités de sécurité pour accéder plus facilement à vos données, installer des programmes malveillants ou exploiter vos données, votre identité et vos appareils. La protection contre la falsification permet d’éviter ce genre d’événements.

Avec la protection contre la falsification, les applications malveillantes ne peuvent pas prendre des mesures telles que :

- Désactivation de la protection contre les virus et les menaces
- Désactivation de la protection en temps réel
- La non-surveillance du comportement
- Désactivation de l’antivirus (par exemple, IOfficeAntivirus (IOAV))
- Désactivation de la protection cloud
- Suppression des mises à jour de l’intelligence de la sécurité

### <a name="how-it-works"></a>Mode de fonctionnement

La protection contre la falsification verrouille Antivirus Microsoft Defender et empêche vos paramètres de sécurité d’être modifiés par le biais d’applications et de méthodes telles que :

- Configuration des paramètres dans l’Éditeur du Registre sur Windows appareil
- Modification des paramètres via les cmdlets PowerShell
- Modification ou suppression des paramètres de sécurité par le biais de stratégies de groupe

La protection contre la falsification ne vous empêche pas d’afficher vos paramètres de sécurité. De plus, la protection contre la falsification n’affecte pas la façon dont les applications antivirus tierces s’inscrivent auprès Sécurité Windows’application. Si votre organisation utilise Windows 10 Entreprise E5, les utilisateurs individuels ne peuvent pas modifier le paramètre de protection contre la falsification. dans ce cas, la protection contre la falsification est gérée par votre équipe de sécurité.

### <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

| Pour effectuer cette tâche... | Consultez cette section... |
|:---|:---|
| Gérer la protection contre les falsifications au sein de votre client <p>Utiliser le Centre de sécurité Microsoft Defender pour activer ou désactiver la protection contre la falsification | [Gérer la protection contre la falsification pour votre organisation à l’aide du Centre de sécurité Microsoft Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center) |
| Affiner les paramètres de protection contre la falsification dans votre organisation <p>Utilisez Intune (Microsoft Endpoint Manager) pour activer ou désactiver la protection contre la falsification. Vous pouvez configurer la protection contre la falsification pour certains ou tous les utilisateurs avec cette méthode. | [Gérer la protection contre les falsifications pour votre organisation à l’aide d’Intune](#manage-tamper-protection-for-your-organization-using-intune) |
| Activer (ou désactiver) la protection contre la falsification pour votre organisation avec Configuration Manager | [Gérer la protection contre la falsification pour votre organisation à l’aide de l’attachement client avec Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006) |
| Activer (ou désactiver) la protection contre la falsification pour un appareil individuel | [Gérer la protection contre la falsification sur un appareil individuel](#manage-tamper-protection-on-an-individual-device) |
| Afficher les détails sur les tentatives de falsification sur les appareils | [Afficher des informations sur les tentatives de falsification](#view-information-about-tampering-attempts) |
| Passer en revue vos recommandations en matière de sécurité | [Examiner les recommandations de sécurité](#review-your-security-recommendations) |
| Consulter la liste des questions fréquemment posées (FAQ) | [Parcourir les FAQ](#view-information-about-tampering-attempts) |

Selon la méthode ou l’outil de gestion que vous utilisez pour activer la protection contre la falsification, il peut y avoir une dépendance sur MAPS (protection livrée par le cloud). 

Le tableau suivant fournit des détails sur les méthodes, les outils et les dépendances.

| Comment la protection contre la falsification est activée  | Dépendance à MAPS (protection cloud)    |
|:----|:----|
| Microsoft Intune  | Non |
| Microsoft Endpoint Configuration Manager + attachement de client  |     Non  |
| Centre de sécurité Microsoft Defender ( [https://securitycenter.microsoft.com](https://securitycenter.microsoft.com) )    |     Oui |
| Microsoft 365 de sécurité ( [https://security.microsoft.com](https://security.microsoft.com) )  |     Oui  |

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center"></a>Gérer la protection contre la falsification pour votre organisation à l’aide du Centre de sécurité Microsoft Defender

La protection contre la falsification peut être allumée ou désactivée pour votre client à l’aide de la Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ). Voici quelques points à garder à l’esprit :

- Actuellement, l’option de gestion de la protection contre la falsification dans le Centre de sécurité Microsoft Defender est mise en place par défaut pour les nouveaux déploiements. Pour les déploiements existants, la protection contre la falsification est disponible sur une base d’opt-in, avec l’intention d’opter pour la méthode par défaut dans un futur proche. (Pour l’opter, dans le Centre de sécurité Microsoft Defender, choisissez **Paramètres**  >  **Fonctionnalités avancées**  >  **Protection contre la falsification**.) 

- Lorsque vous utilisez la Centre de sécurité Microsoft Defender pour gérer la protection contre la falsification, vous n’avez pas besoin d’utiliser Intune ou la méthode d’attachement du client.

- Lorsque vous gérez la protection contre les falsifications dans le Centre de sécurité Microsoft Defender, le paramètre est appliqué à l’échelle du client, affectant tous vos appareils exécutant Windows 10, Windows Server 2016 ou Windows Server 2019. Pour affiner la protection contre la falsification (par exemple, une protection contre la falsification sur certains appareils, mais pas pour d’autres), utilisez [Intune](#manage-tamper-protection-for-your-organization-using-intune) ou Configuration Manager avec attachement [client.](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)

- Si vous avez un environnement hybride, les paramètres de protection contre la falsification configurés dans Intune prévalent sur les paramètres configurés dans le Centre de sécurité Microsoft Defender. 

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-defender-security-center"></a>Conditions requises pour la gestion de la protection contre les falsifications dans le Centre de sécurité Microsoft Defender

- Vous devez avoir les [autorisations appropriées, telles](/microsoft-365/security/defender-endpoint/assign-portal-access)que l’administrateur global, l’administrateur de sécurité ou les opérations de sécurité.

- Vos Windows doivent être en cours d’exécution dans l’une des versions suivantes Windows :
   - Windows 10
   - [Windows Server 2019](/windows-server/get-started-19/whats-new-19)
   - Windows Serveur, version [1803 ou](/windows/release-health/status-windows-10-1803) ultérieure
   - [Windows Server 2016](/windows-server/get-started/whats-new-in-windows-server-2016)
   - Pour plus d’informations sur les releases, [voir Windows 10 release information](/windows/release-health/release-information).

- Vos appareils doivent être [intégrés à Microsoft Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/onboarding)

- Vos appareils doivent utiliser la plateforme anti-programme malveillant version 4.18.2010.7 (ou supérieure) et la version 1.1.17600.5 (ou supérieure) du moteur anti-programme malveillant. ([Gérez Antivirus Microsoft Defender mises à jour et appliquez les lignes de base.)](manage-updates-baselines-microsoft-defender-antivirus.md)

- [La protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md) doit être allumée.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-defender-security-center"></a>Activer (ou désactiver) la protection contre la falsification dans le Centre de sécurité Microsoft Defender 

![Activer la protection contre la falsification dans le Centre de sécurité Microsoft Defender](images/mde-turn-tamperprotect-on.png)

1. Go to the Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) and sign in.

2. Choisissez **Paramètres**.

3. Go to **General**  >  **Advanced features,** and then turn tamper protection on.

## <a name="manage-tamper-protection-for-your-organization-using-intune"></a>Gérer la protection contre les falsifications pour votre organisation à l’aide d’Intune

Si vous faites partie de l’équipe de sécurité de votre organisation et que votre abonnement inclut [Intune,](/intune/fundamentals/what-is-intune)vous pouvez activer (ou désactiver) la protection contre la falsification pour votre organisation dans le Centre d’administration Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ). Utilisez Intune lorsque vous souhaitez affiner les paramètres de protection contre la falsification. Par exemple, si vous souhaitez activer la protection contre la falsification sur certains appareils, mais pas sur tous, utilisez Intune.

### <a name="requirements-for-managing-tamper-protection-in-intune"></a>Conditions requises pour la gestion de la protection contre les falsifications dans Intune

- Vous devez avoir les [autorisations appropriées, telles](/microsoft-365/security/defender-endpoint/assign-portal-access)que l’administrateur global, l’administrateur de sécurité ou les opérations de sécurité.

- Votre organisation utilise [Intune pour gérer les appareils.](/intune/fundamentals/what-is-device-management) ([Les licences Intune](/intune/fundamentals/licenses) sont requises ; Intune est inclus dans Microsoft 365 E5.)

- Vos Windows doivent s’Windows 10 os [1709,](/windows/release-health/status-windows-10-1709) [1803,](/windows/release-health/status-windows-10-1803) [1809 ou](/windows/release-health/status-windows-10-1809-and-windows-server-2019) ultérieur. (Pour plus d’informations sur les publication, voir [Windows 10 de publication.)](/windows/release-health/release-information)

- Vous devez utiliser la sécurité [](https://www.microsoft.com/wdsi/definitions) Windows avec les informations de sécurité mises à jour vers la version 1.287.60.0 (ou supérieure).

- Vos appareils doivent utiliser la plateforme anti-programme malveillant version 4.18.1906.3 (ou supérieure) et la version 1.1.15500.X (ou supérieure) du moteur anti-programme malveillant. ([Gérez Antivirus Microsoft Defender mises à jour et appliquez les lignes de base.)](manage-updates-baselines-microsoft-defender-antivirus.md)

### <a name="turn-tamper-protection-on-or-off-in-intune"></a>Activer (ou désactiver) la protection contre la falsification dans Intune

![Activer la protection contre la falsification avec Intune](images/turnontamperprotect-MEM.png)

1. Go to the [Microsoft Endpoint Manager admin center](https://endpoint.microsoft.com) and sign in with your work or school account.

2. Sélectionnez **profils**  >  **de configuration des appareils.**

3. Créez un profil qui inclut les paramètres suivants :
    - **Plateforme : Windows 10 et ultérieures**
    - **Type de profil : Protection des points de terminaison**
    - **Catégorie : Centre de sécurité Microsoft Defender**
    - **Protection contre les falsifications : activée**

4. Affectez le profil à un ou plusieurs groupes.

### <a name="are-you-using-windows-os-1709-1803-or-1809"></a>Utilisez-vous Windows OS 1709, 1803 ou 1809 ?

Si vous utilisez Windows 10 OS [1709,](/windows/release-health/status-windows-10-1709) [1803](/windows/release-health/status-windows-10-1803)ou [1809,](/windows/release-health/status-windows-10-1809-and-windows-server-2019)la **protection** contre la falsification ne s’Sécurité Windows l’application. À la place, vous pouvez utiliser PowerShell pour déterminer si la protection contre la falsification est activée.

#### <a name="use-powershell-to-determine-whether-tamper-protection-is-turned-on"></a>Utiliser PowerShell pour déterminer si la protection contre la falsification est allumée

1. Ouvrez l Windows PowerShell appl.

2. Utilisez [l’cmdlet Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell.

3. Dans la liste des résultats, recherchez `IsTamperProtected` . (La valeur true signifie *que* la protection contre la falsification est activée.)

## <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Gérer la protection contre la falsification pour votre organisation avec Configuration Manager, version 2006

Si vous utilisez la [version 2006](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006)de Configuration Manager, vous pouvez gérer les paramètres de protection contre la falsification sur Windows 10, Windows Server 2016 et Windows Server 2019 à l’aide d’une méthode appelée attachement de *client.* L’attachement de client vous permet de synchroniser vos appareils Configuration Manager locaux uniquement dans le Centre d’administration Microsoft Endpoint Manager, puis de fournir des stratégies de configuration de sécurité de point de terminaison aux collections & périphériques.

:::image type="content" source="images/win-security- exp-policy-endpt-security.png" alt-text="Sécurité Windows expérience utilisateur Endpoint Manager":::

> [!NOTE]
> La procédure peut être utilisée pour étendre la protection contre la falsification aux appareils exécutant Windows 10 et Windows Server 2019. Veillez à examiner les conditions préalables et d’autres informations dans les ressources mentionnées dans cette procédure.

1. Configurer l’attachement du client. Pour plus d’informations, [voir Microsoft Endpoint Manager de l’attachement du client : synchronisation de l’appareil et actions de l’appareil.](/mem/configmgr/tenant-attach/device-sync-actions)

2. Dans le [centre Microsoft Endpoint Manager' administration,](https://go.microsoft.com/fwlink/?linkid=2109431)allez à **l’Antivirus** de sécurité de point de terminaison, puis choisissez  >  + Créer **une stratégie.**<br/> 
   - Dans la **liste Plateforme,** **sélectionnez Windows 10 et Windows Server (ConfigMgr).**  
   - Dans la **liste Profil,** sélectionnez **Sécurité Windows expérience utilisateur (prévisualisation).** <br/>

3. Déployez la stratégie sur votre collection d’appareils.

### <a name="need-help-with-this-method"></a>Vous avez besoin d’aide avec cette méthode ? 

Consultez les ressources suivantes :

- [Paramètres profil d’expérience Sécurité Windows client dans Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Blog tech Community : Annonce de la protection contre la falsification pour les clients d’attachement de client Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Gérer la protection contre la falsification sur un appareil individuel

> [!NOTE]
> La protection contre la falsification bloque les tentatives de modification Antivirus Microsoft Defender paramètres de protection par le biais du Registre.
>
> Pour vous assurer que la protection contre la falsification n’interfère pas avec les produits de sécurité  tiers ou les scripts d’installation d’entreprise qui modifient ces paramètres, allez à **Sécurité Windows** et mettez à jour l’intelligence de sécurité vers la version 1.287.60.0 ou ultérieure. (Voir mises [à jour de l’intelligence de la sécurité.)](https://www.microsoft.com/wdsi/definitions)
>
> Une fois cette mise à jour réalisée, la protection contre la falsification continue de protéger vos paramètres de Registre et les journaux tentent de les modifier sans renvoyer d’erreurs.

Si vous êtes un utilisateur de base ou si vous n’êtes pas soumis aux paramètres gérés par une équipe de sécurité, vous pouvez utiliser l’application Sécurité Windows pour gérer la protection contre la falsification. Vous devez avoir les autorisations d’administration appropriées sur votre appareil pour modifier les paramètres de sécurité, tels que la protection contre la falsification.

Voici ce que vous voyez dans l’application Sécurité Windows:

![La protection contre la falsification est Windows 10 Famille](images/tamperprotectionturnedon.png)

1. Sélectionnez **Démarrer** et commencez à taper *Sécurité.* Dans les résultats de la recherche, **sélectionnez Sécurité Windows**.

2. Sélectionnez **Virus & protection contre les virus &** les  >  **paramètres de protection contre les menaces.**

3. Définissez **la protection contre la** falsification sur **On** ou **Off**.

## <a name="view-information-about-tampering-attempts"></a>Afficher des informations sur les tentatives de falsification

Les tentatives de falsification indiquent généralement des cyberattaques plus importantes. Les acteurs mauvais tentent de modifier les paramètres de sécurité afin de les rendre persistants et non détectés. Si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez afficher des informations sur ces tentatives, puis prendre les mesures appropriées pour atténuer les menaces.

Lorsqu’une tentative de falsification est détectée, une alerte est Centre de sécurité Microsoft Defender [(](/microsoft-365/security/defender-endpoint/portal-overview) [https://securitycenter.windows.com](https://securitycenter.windows.com) ).

![Centre de sécurité Microsoft Defender](images/tamperattemptalert.png)

À [l’protection évolutive des points de terminaison](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response) [](/microsoft-365/security/defender-endpoint/advanced-hunting-overview) et aux fonctionnalités de recherche avancées dans Microsoft Defender pour le point de terminaison, votre équipe des opérations de sécurité peut examiner et résoudre ces tentatives.

## <a name="review-your-security-recommendations"></a>Passer en revue vos recommandations en matière de sécurité

La protection contre la falsification s’intègre aux fonctionnalités [& gestion](/microsoft-365/security/defender-endpoint/next-gen-threat-and-vuln-mgt) des menaces et des vulnérabilités. [Les recommandations en matière de sécurité](/microsoft-365/security/defender-endpoint/tvm-security-recommendation) incluent la garantie que la protection contre la falsification est allumée. Par exemple, vous pouvez effectuer une *recherche* sur falsification, comme illustré dans l’image suivante :

![La protection contre la falsification entraîne des recommandations de sécurité](/images/securityrecs-tamperprotect.jpg)

Dans les résultats, vous pouvez sélectionner **Activer la protection** contre la falsification pour en savoir plus et l’activer.

![Activer la protection contre la falsification](images/tamperprotectsecurityrecos.png)

Pour en savoir plus sur la gestion & des menaces et des vulnérabilités, voir [Threat & Vulnerability Management dans Centre de sécurité Microsoft Defender](/microsoft-365/security/defender-endpoint/tvm-dashboard-insights#threat--vulnerability-management-in-microsoft-defender-security-center).

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="to-which-windows-os-versions-is-configuring-tamper-protection-is-applicable"></a>À quelles versions Windows système d’exploitation configure la protection contre la falsification ?

Windows 10 OS [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), ou ultérieur avec [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint).

Si vous utilisez Configuration Manager, version 2006, avec attachement client, la protection contre la falsification peut être étendue à Windows Server 2019. Voir l’attachement client : créer et déployer une stratégie antivirus de sécurité de point de terminaison [à partir du centre d’administration (prévisualisation).](/mem/configmgr/tenant-attach/deploy-antivirus-policy)

### <a name="will-tamper-protection-have-any-impact-on-third-party-antivirus-registration"></a>La protection contre la falsification aura-t-elle un impact sur l’inscription d’antivirus tiers ?

Non. Les offres antivirus tierces continueront de s’inscrire auprès Sécurité Windows’application.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Que se passe-t-il si Antivirus Microsoft Defender n’est pas actif sur un appareil ?

Les appareils intégrés à Microsoft Defender pour le point de terminaison Antivirus Microsoft Defender en mode passif. La protection contre la falsification continuera à protéger le service et ses fonctionnalités. 

### <a name="how-can-i-turn-tamper-protection-onoff"></a>Comment activer/désactiver la protection contre les falsifications ?

Si vous êtes un particulier, consultez Gérer [la protection contre les falsifications sur un appareil individuel.](#manage-tamper-protection-on-an-individual-device)

Si vous êtes une organisation qui utilise [Microsoft Defender pour le](/microsoft-365/security/defender-endpoint)point de terminaison, vous devez être en mesure de gérer la protection contre les falsifications dans Intune de la même façon que vous gérez d’autres fonctionnalités de protection des points de terminaison. Consultez les sections suivantes de cet article : 

- [Gérer la protection contre les falsifications à l’aide d’Intune](#manage-tamper-protection-for-your-organization-using-intune)
- [Gérer la protection contre les falsifications à l’aide de Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Gérer la protection contre les falsifications à l’aide Centre de sécurité Microsoft Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-defender-security-center) 

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-through-my-group-policy"></a>Comment la configuration de la protection contre les falsifications dans Intune affecte-t-elle la façon dont je Antivirus Microsoft Defender par le biais de ma stratégie de groupe ?

Votre stratégie de groupe normale ne s’applique pas à la protection contre la falsification et les modifications apportées aux paramètres de Antivirus Microsoft Defender sont ignorées lorsque la protection contre la falsification est en cours. 

### <a name="for-microsoft-defender-for-endpoint-is-configuring-tamper-protection-in-intune-targeted-to-the-entire-organization-only"></a>Pour Microsoft Defender pour le point de terminaison, la configuration de la protection contre la falsification dans Intune s’adresse-t-elle uniquement à l’ensemble de l’organisation ?

La configuration de la protection contre la falsification dans Intune ou Microsoft Endpoint Manager peut cibler l’ensemble de votre organisation et des appareils et groupes d’utilisateurs spécifiques.

### <a name="can-i-configure-tamper-protection-in-microsoft-endpoint-configuration-manager"></a>Puis-je configurer la protection contre les falsifications dans Microsoft Endpoint Configuration Manager ?

Si vous utilisez l’attachement de client, vous pouvez utiliser Microsoft Endpoint Configuration Manager. Consultez les ressources suivantes :
- [Gérer la protection contre la falsification pour votre organisation avec Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Blog tech Community : Annonce de la protection contre la falsification pour les clients d’attachement de client Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>J’ai le Windows inscription E3. Puis-je utiliser la configuration de la protection contre les falsifications dans Intune ?

Actuellement, la configuration de la protection contre la falsification dans Intune est disponible uniquement pour les clients qui ont [Microsoft Defender pour point de terminaison.](/microsoft-365/security/defender-endpoint)

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Que se passe-t-il si j’essaie de modifier les paramètres de Microsoft Defender for Endpoint dans Intune, Microsoft Endpoint Configuration Manager et Windows Management Instrumentation lorsque la protection contre la falsification est activée sur un appareil ?

Vous ne pourrez pas modifier les fonctionnalités protégées par la protection contre la falsification . ces demandes de modification sont ignorées.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Je suis un client d’entreprise. Les administrateurs locaux peuvent-ils modifier la protection contre la falsification sur leurs appareils ?

Non. Les administrateurs locaux ne peuvent pas modifier ou modifier les paramètres de protection contre la falsification.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Que se passe-t-il si mon appareil est intégré à Microsoft Defender pour Endpoint, puis passe dans un état hors intégration ?

Si un appareil est désintérable à partir de Microsoft Defender pour le point de terminaison, la protection contre la falsification est allumée, qui est l’état par défaut pour les appareils non utilisés. 

### <a name="will-there-be-an-alert-about-tamper-protection-status-changing-in-the-microsoft-defender-security-center"></a>Y aura-t-il une alerte concernant la modification de l’état de la protection contre la falsification dans Centre de sécurité Microsoft Defender ?

Oui. L’alerte s’affiche [https://securitycenter.microsoft.com](https://securitycenter.microsoft.com) sous **Alertes.**

Votre équipe des opérations de sécurité peut également utiliser des requêtes de recherche, telles que l’exemple suivant :

`DeviceAlertEvents | where Title == "Tamper Protection bypass"`

[Afficher des informations sur les tentatives de falsification.](#view-information-about-tampering-attempts)

## <a name="see-also"></a>Voir aussi

[Sécurisation de Windows PC avec des Endpoint Protection pour Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Obtenir une vue d’ensemble de Microsoft Defender pour le point de terminaison](/microsoft-365/security/defender-endpoint)

[Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md)