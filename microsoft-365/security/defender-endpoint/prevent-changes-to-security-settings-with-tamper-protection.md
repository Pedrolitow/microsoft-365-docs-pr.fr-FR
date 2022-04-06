---
title: Protéger les paramètres de sécurité avec la protection contre la falsifiation
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Utilisez la protection contre les falsifications pour empêcher les applications malveillantes de modifier les paramètres de sécurité importants.
keywords: programmes malveillants, defender, antivirus, protection contre les falsifications
ms.pagetype: security
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.custom:
- nextgen
- admindeeplinkDEFENDER
ms.technology: mde
ms.date: 01/18/2022
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.openlocfilehash: 3ccda70af88b8e99afde125311b074025242646a
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64667425"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Protéger les paramètres de sécurité avec la protection contre la falsifiation

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

La protection contre les falsifications est disponible pour les appareils qui exécutent l’une des versions suivantes de Windows :

- Windows 10
- Windows 11
- Windows 10 Entreprise à sessions multiples
- Windows 11 Entreprise multisession 
- Windows Server 2019
- Windows Server 2022
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> La protection contre les falsifications dans Windows Server 2012 R2 est disponible pour les appareils intégrés à l’aide du package de solution unifié moderne. Pour plus d’informations, consultez [Nouvelles fonctionnalités de la solution unifiée moderne pour Windows Server 2012 R2 et 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

## <a name="overview"></a>Présentation

Pendant certains types de cyberattaques, les mauvais acteurs essaient de désactiver les fonctionnalités de sécurité, telles que la protection antivirus, sur vos machines. Les acteurs malveillants aiment désactiver vos fonctionnalités de sécurité pour accéder plus facilement à vos données, installer des programmes malveillants ou exploiter vos données, votre identité et vos appareils. La protection contre les falsifications permet d’éviter que ces types de choses se produisent.

Avec la protection contre les falsifications, les applications malveillantes sont empêchées d’effectuer des actions telles que :

- Désactivation de la protection contre les virus et les menaces
- Désactivation de la protection en temps réel
- Désactivation de la surveillance du comportement
- Désactivation de l’antivirus (par exemple, IOfficeAntivirus (IOAV))
- Désactivation de la protection fournie par le cloud
- Suppression des mises à jour du renseignement de sécurité
- Désactivation des actions automatiques sur les menaces détectées

### <a name="how-it-works"></a>Mode de fonctionnement

La protection contre les falsifications verrouille essentiellement Antivirus Microsoft Defender à ses valeurs sécurisées par défaut et empêche la modification de vos paramètres de sécurité par le biais d’applications et de méthodes telles que :

- Configuration des paramètres dans l’Éditeur du Registre sur votre appareil Windows
- Modification des paramètres via les applets de commande PowerShell
- Modification ou suppression des paramètres de sécurité via stratégie de groupe

La protection contre les falsifications ne vous empêche pas d’afficher vos paramètres de sécurité. De plus, la protection contre les falsifications n’affecte pas la façon dont les applications antivirus non Microsoft s’inscrivent auprès de l’application Sécurité Windows. Si votre organisation utilise Windows 10 Entreprise E5, les utilisateurs individuels ne peuvent pas modifier le paramètre de protection contre les falsifications . Dans ce cas, la protection contre les falsifications est gérée par votre équipe de sécurité.

### <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

<br/><br/>

|Pour effectuer cette tâche...|Consultez cette section...|
|---|---|
|Gérer la protection contre les falsifications dans votre locataire <p> Utiliser le portail Microsoft 365 Defender pour activer ou désactiver la protection contre les falsifications|[Gérer la protection contre les falsifications pour votre organisation à l’aide de la Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Ajuster les paramètres de protection contre les falsifications dans votre organisation <p> Utilisez Intune (Microsoft Endpoint Manager) pour activer ou désactiver la protection contre les falsifications. Vous pouvez configurer la protection contre les falsifications pour certains utilisateurs ou tous les utilisateurs avec cette méthode.|[Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Activer ou désactiver la protection contre les falsifications pour votre organisation avec Configuration Manager|[Gérer la protection contre les falsifications pour votre organisation à l’aide de l’attachement de locataire avec Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Activer ou désactiver la protection contre les falsifications pour un appareil individuel|[Gérer la protection contre les falsifications sur un appareil individuel](#manage-tamper-protection-on-an-individual-device)|
|Afficher des détails sur les tentatives de falsification sur les appareils|[Afficher des informations sur les tentatives de falsification](#view-information-about-tampering-attempts)|
|Passez en revue vos recommandations de sécurité|[Passer en revue les recommandations de sécurité](#review-your-security-recommendations)|
|Consulter la liste des questions fréquentes (FAQ)|[Parcourir les questions fréquentes (FAQ)](#view-information-about-tampering-attempts)|

Selon la méthode ou l’outil de gestion que vous utilisez pour activer la protection contre les falsifications, il peut y avoir une dépendance vis-à-vis de la protection fournie par le cloud.

Le tableau suivant fournit des détails sur les méthodes, les outils et les dépendances.

<br/><br/>

|Activation de la protection contre les falsifications|Dépendance vis-à-vis de la protection fournie par le cloud (MAPS)|
|---|---|
|Microsoft Intune|Non|
|Microsoft Endpoint Configuration Manager + attachement de locataire|Non|
|portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com))|Oui|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Gérer la protection contre les falsifications pour votre organisation à l’aide du portail Microsoft 365 Defender

La protection contre les falsifications peut être activée ou désactivée pour votre locataire à l’aide du portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Voici quelques points à garder à l’esprit :

- Actuellement, l’option de gestion de la protection contre les falsifications dans le portail Microsoft 365 Defender est activée par défaut pour les nouveaux déploiements. Pour les déploiements existants, la protection contre les falsifications est disponible sur une base d’adhésion. Pour vous inscrire, dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, choisissez **Paramètres** \> points de terminaison **Fonctionnalités avancées** **de la protection contre les falsifications** \> \>.

- Lorsque vous utilisez le portail Microsoft 365 Defender pour gérer la protection contre les falsifications, vous n’avez pas besoin d’utiliser Intune ou la méthode d’attachement de locataire.

- Lorsque vous gérez la protection contre les falsifications dans le portail Microsoft 365 Defender, le paramètre est appliqué à l’échelle du locataire, ce qui affecte tous vos appareils qui exécutent Windows 10, Windows 10 Entreprise multisession, Windows 11 Windows 11 Entreprise  multisession, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 ou Windows Server 2022. Pour affiner la protection contre les falsifications (par exemple, la protection contre les falsifications sur certains appareils, mais désactivée pour d’autres), utilisez [Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) ou [Configuration Manager avec l’attachement de locataire](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006).

- Si vous avez un environnement hybride, les paramètres de protection contre les falsifications configurés dans Intune sont prioritaires sur les paramètres configurés dans le portail Microsoft 365 Defender.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Configuration requise pour la gestion de la protection contre les falsifications dans le portail Microsoft 365 Defender

- Vous devez disposer [des autorisations](/microsoft-365/security/defender-endpoint/assign-portal-access) appropriées, telles que l’administrateur général, l’administrateur de sécurité ou les opérations de sécurité.

- Vos appareils Windows doivent exécuter l’une des versions suivantes de Windows :
  
  - Windows 10
  - Windows 11
  - Windows 10 Entreprise à sessions multiples
  - Windows 11 Entreprise multisession 
  - Windows Server 2019
  - Windows Server 2022
  - Windows Server, version 1803 ou ultérieure
  - Windows Server 2016
  - Windows Server 2012 R2

Pour plus d’informations sur les versions, consultez [Windows 10 informations de publication](/windows/release-health/release-information).

- Vos appareils doivent être [intégrés à Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboarding).

- Vos appareils doivent utiliser la version `4.18.2010.7` de plateforme anti-programme malveillant (ou ultérieure) et la version `1.1.17600.5` du moteur anti-programme malveillant (ou ultérieure). ([Gérer Antivirus Microsoft Defender mises à jour et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).)

- [La protection fournie par le cloud](enable-cloud-protection-microsoft-defender-antivirus.md) doit être activée.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Activer ou désactiver la protection contre les falsifications dans le portail Microsoft 365 Defender

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Activer la protection contre les falsifications dans le portail Microsoft 365 Defender" lightbox="../../media/mde-turn-tamperprotectionon.png":::

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Choisissez **Paramètres** \> **points de terminaison**.

3. Accédez aux **fonctionnalités avancées générales**\>, puis activez la protection contre les falsifications.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Gérer la protection contre les falsifications pour votre organisation à l’aide de Microsoft Endpoint Manager

Si votre organisation utilise Microsoft Endpoint Manager (MEM), vous pouvez activer ou désactiver la protection contre les falsifications pour votre organisation dans le centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)). Utilisez Intune lorsque vous souhaitez affiner les paramètres de protection contre les falsifications. Par exemple, si vous souhaitez activer la protection contre les falsifications sur certains appareils, mais pas tous, utilisez Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Configuration requise pour la gestion de la protection contre les falsifications dans Endpoint Manager

- Vos appareils doivent être [intégrés à Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboarding).

- Vous devez disposer [des autorisations](/microsoft-365/security/defender-endpoint/assign-portal-access) appropriées, telles que l’administrateur général, l’administrateur de sécurité ou les opérations de sécurité.

- Votre organisation utilise [Microsoft Endpoint Manager pour gérer les appareils](/mem/endpoint-manager-getting-started). Des licences (Microsoft Endpoint Manager (MEM) sont requises ; MEM est inclus dans Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365  Gouvernement G3/G5, et licences d’éducation correspondantes.)

- Vos appareils Windows doivent exécuter Windows 11 ou Windows 10 [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) ou version ultérieure. (Pour plus d’informations sur les versions, consultez [Windows 10 informations de publication](/windows/release-health/release-information).)

- Vous devez utiliser Windows sécurité avec [le renseignement de sécurité](https://www.microsoft.com/wdsi/definitions) mis à jour vers la version 1.287.60.0 (ou ultérieure).

- Vos appareils doivent utiliser la plateforme anti-programme malveillant version 4.18.1906.3 (ou ultérieure) et la version `1.1.15500.X` du moteur anti-programme malveillant (ou version ultérieure). ([Gérer Antivirus Microsoft Defender mises à jour et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md).)

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Activer ou désactiver la protection contre les falsifications dans Microsoft Endpoint Manager

:::image type="content" source="images/turnontamperprotectinmem.png" alt-text="Activer la protection contre les falsifications avec Intune" lightbox="images/turnontamperprotectinmem.png":::

1. Dans le [centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **l’antivirus** de **sécurité** \> de point de terminaison, puis choisissez **+ Créer une stratégie**.

   - Dans la liste **des plateformes**, sélectionnez **Windows 10 et versions ultérieures**.
   - Dans la liste **des profils**, sélectionnez **Sécurité Windows expérience**.

2. Créez un profil qui inclut le paramètre suivant :

    - **Activer la protection contre les falsifications pour empêcher la désactivation de Microsoft Defender : Activer**

3. Affectez le profil à un ou plusieurs groupes.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Gérer la protection contre les falsifications pour votre organisation avec Configuration Manager, version 2006

Si vous utilisez la [version 2006 de Configuration Manager](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006), vous pouvez gérer les paramètres de protection contre les falsifications sur Windows 10, Windows 10 Entreprise multisession, Windows 11 Windows 11 Entreprise multisession, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 et Windows Server 2022 à l’aide d’une méthode appelée *attachement de locataire*. L’attachement de locataire vous permet de synchroniser vos appareils Configuration Manager locaux uniquement dans le centre d’administration Microsoft Endpoint Manager, puis de fournir des stratégies de configuration de sécurité de point de terminaison aux regroupements locaux & appareils.

> [!NOTE]
> La procédure peut être utilisée pour étendre la protection contre les falsifications aux appareils exécutant Windows 10, Windows 10 Entreprise multisession, Windows 11, Windows 11 Entreprise multisession, Windows Server 2019 et Windows Server 2022. Veillez à examiner les prérequis et d’autres informations dans les ressources mentionnées dans cette procédure.

1. Configurez l’attachement de locataire. Pour en savoir plus, consultez [Démarrage : Créer et déployer des stratégies de sécurité de point de terminaison à partir du Centre d’administration](/mem/configmgr/tenant-attach/endpoint-security-get-started).

2. Dans le [centre d’administration Microsoft Endpoint Manager](https://go.microsoft.com/fwlink/?linkid=2109431), accédez à **l’antivirus** de **sécurité** \> de point de terminaison, puis choisissez **+ Créer une stratégie**.

   - Dans la liste **des plateformes**, sélectionnez **Windows 10, Windows 11 et Windows Server (ConfigMgr).**
   - Dans la liste **des profils**, sélectionnez **Sécurité Windows expérience (préversion).**

3. Déployez la stratégie sur votre collection d’appareils.

#### <a name="need-help-with-this-method"></a>Vous avez besoin d’aide avec cette méthode ?

Consultez les ressources suivantes :

- [Paramètres pour le profil d’expérience Sécurité Windows dans Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Blog Tech Community : Annonce de la protection contre les falsifications pour les clients d’attachement de locataire Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Gérer la protection contre les falsifications sur un appareil individuel

> [!NOTE]
> La protection contre les falsifications bloque les tentatives de modification des paramètres Antivirus Microsoft Defender par le biais du Registre.
>
> Pour vous assurer que la protection contre les falsifications n’interfère pas avec les produits de sécurité non Microsoft ou les scripts d’installation d’entreprise qui modifient ces paramètres, accédez à **Sécurité Windows** et mettez à jour **security intelligence** vers la version 1.287.60.0 ou ultérieure. (Consultez [les mises à jour du renseignement de sécurité](https://www.microsoft.com/wdsi/definitions).)
>
> Une fois cette mise à jour effectuée, la protection contre les falsifications continue de protéger vos paramètres de Registre, et les journaux tentent de les modifier sans retourner d’erreurs.

Si vous êtes un utilisateur domestique ou que vous n’êtes pas soumis à des paramètres gérés par une équipe de sécurité, vous pouvez utiliser l’application Sécurité Windows pour gérer la protection contre les falsifications. Vous devez disposer des autorisations d’administrateur appropriées sur votre appareil pour modifier les paramètres de sécurité, tels que la protection contre les falsifications.

Voici ce que vous voyez dans l’application Sécurité Windows :

:::image type="content" source="images/tamperprotectionturnedon.png" alt-text="Activer la protection contre les falsifications dans Windows 10 Famille" lightbox="images/tamperprotectionturnedon.png":::

1. Sélectionnez **Démarrer**, puis commencez à taper *Sécurité*. Dans les résultats de la recherche, sélectionnez **Sécurité Windows**.

2. Sélectionnez **Virus & protection** \> contre les **menaces Virus & paramètres de protection contre les menaces**.

3. Définissez **la protection contre les falsifications** **sur Activé** ou **Désactivé**.

## <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>Utilisez-vous Windows Server 2016 ou Windows version 1709, 1803 ou 1809 ?

Si vous utilisez Windows Server 2016, Windows 10 version 1709, 1803 ou [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019), vous ne **verrez pas la protection contre les falsifications** dans l’application Sécurité Windows. Au lieu de cela, vous pouvez utiliser PowerShell pour déterminer si la protection contre les falsifications est activée.

Sur Windows Server 2016, l’application Paramètres ne reflète pas avec précision l’état de la protection en temps réel lorsque la protection contre les falsifications est activée.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Utiliser PowerShell pour déterminer si la protection contre les falsifications et la protection en temps réel sont activées

1. Ouvrez l’application Windows PowerShell.

2. Utilisez l’applet [de commande Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell.

3. Dans la liste des résultats, recherchez `IsTamperProtected` ou `RealTimeProtectionEnabled`. (La *valeur true signifie* que la protection contre les falsifications est activée.)

## <a name="view-information-about-tampering-attempts"></a>Afficher des informations sur les tentatives de falsification

Les tentatives de falsification indiquent généralement des cyberattaques plus importantes. Les acteurs malveillants tentent de modifier les paramètres de sécurité pour conserver et ne pas être détectés. Si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez afficher des informations sur ces tentatives, puis prendre les mesures appropriées pour atténuer les menaces.

Lorsqu’une tentative de falsification est détectée, une alerte est déclenchée dans le [portail Microsoft 365 Defender](/microsoft-365/security/defender-endpoint/portal-overview) ([https://security.microsoft.com](https://security.microsoft.com)).

:::image type="content" source="images/tamperattemptalert.png" alt-text="Portail Microsoft 365 Defender" lightbox="images/tamperattemptalert.png":::

À [l’aide de protection évolutive des points de terminaison](overview-endpoint-detection-response.md) et de fonctionnalités [de repérage avancées](advanced-hunting-overview.md) dans Microsoft Defender pour point de terminaison, votre équipe chargée des opérations de sécurité peut examiner et résoudre ces tentatives.

## <a name="review-your-security-recommendations"></a>Passez en revue vos recommandations de sécurité

La protection contre les falsifications s’intègre aux fonctionnalités de gestion des vulnérabilités [& des menaces](next-gen-threat-and-vuln-mgt.md) . [Les recommandations de sécurité](tvm-security-recommendation.md) incluent la garantie que la protection contre les falsifications est activée. Par exemple, vous pouvez effectuer une recherche sur la *falsification*. Dans les résultats, vous pouvez sélectionner **Activer la protection contre les falsifications** pour en savoir plus et l’activer.

:::image type="content" source="images/tamperprotectsecurityrecos.png" alt-text="Activation de la protection contre les falsifications dans le portail Centre de sécurité Microsoft Defender" lightbox="images/tamperprotectsecurityrecos.png":::

Pour en savoir plus sur threat & Vulnerability Management, consultez [Dashboard Insights - Gestion des menaces et des vulnérabilités](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management).

## <a name="frequently-asked-questions"></a>Foire aux questions

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>Sur quelles versions de Windows puis-je configurer la protection contre les falsifications ?

Windows 10 système d’exploitation [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019) ou version ultérieure avec [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint).
  
Windows 10 Entreprise à sessions multiples

Windows 11

Windows 11 Entreprise multisession
  
Si vous utilisez Configuration Manager, version 2006, avec attachement de locataire, la protection contre les falsifications peut être étendue à Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 et Windows Server 2022. Voir [Attachement de locataire : Créer et déployer une stratégie antivirus de sécurité de point de terminaison à partir du centre d’administration (préversion).](/mem/configmgr/tenant-attach/deploy-antivirus-policy)

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>La protection contre les falsifications affecte-t-elle l’inscription d’antivirus non-Microsoft dans l’application Sécurité Windows ?

Non. Les offres antivirus non Microsoft continueront de s’inscrire auprès de l’application Sécurité Windows.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Que se passe-t-il si Antivirus Microsoft Defender n’est pas actif sur un appareil ?

Les appareils qui sont intégrés à Microsoft Defender pour point de terminaison auront Antivirus Microsoft Defender en cours d’exécution en mode passif. Dans ce cas, la protection contre les falsifications continuera à protéger le service et ses fonctionnalités.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Comment faire activer ou désactiver la protection contre les falsifications ?

Si vous êtes un utilisateur domestique, consultez [Gérer la protection contre les falsifications sur un appareil individuel](#manage-tamper-protection-on-an-individual-device).

Si vous êtes une organisation qui utilise [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint), vous devez être en mesure de gérer la protection contre les falsifications dans Intune similaire à la façon dont vous gérez d’autres fonctionnalités de protection des points de terminaison. Consultez les sections suivantes de cet article :

- [Gérer la protection contre les falsifications à l’aide de Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Gérer la protection contre les falsifications à l’aide du portail Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Comment la configuration de la protection contre les falsifications dans Intune affecte-t-elle la façon dont je gère les Antivirus Microsoft Defender avec stratégie de groupe ?

La stratégie de groupe ne s’applique pas à la protection contre les falsifications. Les modifications apportées aux paramètres de Antivirus Microsoft Defender sont ignorées lorsque la protection contre les falsifications est activée.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Si nous utilisons Microsoft Intune pour configurer la protection contre les falsifications, s’applique-t-elle uniquement à l’ensemble de l’organisation ?

Vous disposez d’une certaine flexibilité dans la configuration de la protection contre les falsifications avec Intune. Vous pouvez cibler l’ensemble de votre organisation ou sélectionner des appareils et des groupes d’utilisateurs spécifiques.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Puis-je configurer la protection contre les falsifications avec Microsoft Endpoint Configuration Manager ?

Si vous utilisez l’attachement de locataire, vous pouvez utiliser Microsoft Endpoint Configuration Manager. Consultez les ressources suivantes :

- [Gérer la protection contre les falsifications pour votre organisation avec Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Blog Tech Community : Annonce de la protection contre les falsifications pour les clients d’attachement de locataire Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>J’ai l’inscription Windows E3. Puis-je utiliser la configuration de la protection contre les falsifications dans Intune ?

Actuellement, la configuration de la protection contre les falsifications dans Intune est disponible uniquement pour les clients qui ont [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint).

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Que se passe-t-il si j’essaie de modifier Microsoft Defender pour point de terminaison paramètres dans Intune, Microsoft Endpoint Configuration Manager et Windows Management Instrumentation lorsque la protection contre les falsifications est activée sur un appareil ?

Vous ne pourrez pas modifier les fonctionnalités protégées par la protection contre les falsifications ; ces demandes de modification sont ignorées.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Je suis un client d’entreprise. Les administrateurs locaux peuvent-ils modifier la protection contre les falsifications sur leurs appareils ?

Non. Les administrateurs locaux ne peuvent pas modifier les paramètres de protection contre les falsifications.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Que se passe-t-il si mon appareil est intégré à Microsoft Defender pour point de terminaison puis passe à un état hors-carte ?

Si un appareil est désintégré à partir de Microsoft Defender pour point de terminaison, la protection contre les falsifications est activée, qui est l’état par défaut pour les appareils non gérés.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Si l’état de la protection contre les falsifications change, les alertes sont-ils affichées dans le portail Microsoft 365 Defender ?

Oui. L’alerte s’affiche [https://security.microsoft.com](https://security.microsoft.com) sous **Alertes**.

Votre équipe des opérations de sécurité peut également utiliser des requêtes de chasse, comme l’exemple suivant :

`AlertInfo|where Title == "Tamper Protection bypass"`

[Afficher des informations sur les tentatives de falsification](#view-information-about-tampering-attempts).

## <a name="see-also"></a>Voir aussi

[Sécuriser Windows PC avec Endpoint Protection pour Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Obtenir une vue d’ensemble de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint)

[Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md)
