---
title: Protéger les paramètres de sécurité avec la protection contre la falsifiation
ms.reviewer: mattcall, pahuijbr, hayhov, oogunrinde
manager: dansimp
description: Utilisez la protection contre la falsification pour empêcher les applications malveillantes de modifier les paramètres de sécurité importants.
keywords: programmes malveillants, defender, antivirus, protection contre la falsification
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
ms.openlocfilehash: dd3bbc2ef37879dd90509de35c45c8aa0c5aa9e3
ms.sourcegitcommit: aac7e002ec6e10a41baa2d0bd38614b0ed471a70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/27/2022
ms.locfileid: "62245374"
---
# <a name="protect-security-settings-with-tamper-protection"></a>Protéger les paramètres de sécurité avec la protection contre la falsifiation

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

La protection contre la falsification est disponible pour les appareils qui exécutent l’une des versions suivantes de Windows :

- Windows 10
- Windows 11
- Windows 10 Entreprise à sessions multiples
- Windows 11 Entreprise sessions multiples 
- Windows Server 2019
- Windows Server 2022
- Windows Server, version 1803 ou ultérieure
- Windows Server 2016
- Windows Server 2012 R2

> [!NOTE]
> La protection contre la falsification Windows Server 2012 R2 est disponible pour les appareils intégrés à l’aide du package de solution unifiée moderne. Pour plus d’informations, voir Nouvelle fonctionnalité dans la solution unifiée moderne pour [Windows Server 2012 R2 et 2016 Preview](/microsoft-365/security/defender-endpoint/configure-server-endpoints#new-functionality-in-the-modern-unified-solution-for-windows-server-2012-r2-and-2016-preview).

## <a name="overview"></a>Vue d’ensemble

Pendant certains types de cyberattaques, les acteurs malveillants tentent de désactiver les fonctionnalités de sécurité, telles que la protection antivirus, sur vos ordinateurs. Les acteurs malveillants aiment désactiver vos fonctionnalités de sécurité pour accéder plus facilement à vos données, installer des programmes malveillants ou exploiter vos données, votre identité et vos appareils. La protection contre la falsification permet d’éviter ce genre d’événements.

Avec la protection contre la falsification, les applications malveillantes ne peuvent pas prendre des mesures telles que :

- Désactivation de la protection contre les virus et les menaces
- Désactivation de la protection en temps réel
- La non-surveillance du comportement
- Désactivation de l’antivirus (par exemple, IOfficeAntivirus (IOAV))
- Désactivation de la protection cloud
- Suppression des mises à jour de l’intelligence de la sécurité
- Désactivation des actions automatiques sur les menaces détectées

### <a name="how-it-works"></a>Mode de fonctionnement

La protection contre la falsification verrouille Antivirus Microsoft Defender à ses valeurs par défaut sécurisées et empêche vos paramètres de sécurité d’être modifiés par le biais d’applications et de méthodes telles que :

- Configuration des paramètres dans l’Éditeur du Registre sur Windows appareil
- Modification des paramètres via les cmdlets PowerShell
- Modification ou suppression des paramètres de sécurité par le biais de la stratégie de groupe

La protection contre la falsification ne vous empêche pas d’afficher vos paramètres de sécurité. De plus, la protection contre la falsification n’affecte pas la façon dont les applications antivirus non Microsoft s’inscrivent auprès Sécurité Windows’application. Si votre organisation utilise Windows 10 Entreprise E5, les utilisateurs individuels ne peuvent pas modifier le paramètre de protection contre la falsification ; dans ce cas, la protection contre la falsification est gérée par votre équipe de sécurité.

### <a name="what-do-you-want-to-do"></a>Que souhaitez-vous faire ?

<br/><br/>

|Pour effectuer cette tâche...|Consultez cette section...|
|---|---|
|Gérer la protection contre les falsifications au sein de votre client <p> Utiliser le portail Microsoft 365 Defender pour activer ou désactiver la protection contre la falsification|[Gérer la protection contre les falsifications pour votre organisation à l’aide Microsoft 365 Defender](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)|
|Affiner les paramètres de protection contre la falsification dans votre organisation <p> Utilisez Intune (Microsoft Endpoint Manager) pour activer ou désactiver la protection contre la falsification. Vous pouvez configurer la protection contre la falsification pour certains ou tous les utilisateurs avec cette méthode.|[Gérer la protection contre la falsification pour votre organisation à l’aide Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)|
|Activer (ou désactiver) la protection contre la falsification pour votre organisation avec Configuration Manager|[Gérer la protection contre la falsification pour votre organisation à l’aide de l’attachement client avec Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)|
|Activer (ou désactiver) la protection contre la falsification pour un appareil individuel|[Gérer la protection contre les falsifications sur un appareil individuel](#manage-tamper-protection-on-an-individual-device)|
|Afficher les détails sur les tentatives de falsification sur les appareils|[Afficher des informations sur les tentatives de falsification](#view-information-about-tampering-attempts)|
|Passer en revue vos recommandations en matière de sécurité|[Examiner les recommandations de sécurité](#review-your-security-recommendations)|
|Consulter la liste des questions fréquemment posées (FAQ)|[Parcourir les FAQ](#view-information-about-tampering-attempts)|

Selon la méthode ou l’outil de gestion que vous utilisez pour activer la protection contre la falsification, il peut y avoir une dépendance sur la protection livrée par le cloud.

Le tableau suivant fournit des détails sur les méthodes, les outils et les dépendances.

<br/><br/>

|Comment la protection contre la falsification est activée|Dépendance à la protection cloud (MAPS)|
|---|---|
|Microsoft Intune|Non|
|Microsoft Endpoint Configuration Manager + attachement de client|Non|
|Microsoft 365 Defender portail ( [https://security.microsoft.com](https://security.microsoft.com) )|Oui|

## <a name="manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal"></a>Gérer la protection contre la falsification pour votre organisation à l’aide Microsoft 365 Defender portail

La protection contre la falsification peut être allumée ou désactivée pour votre client à l’aide du portail Microsoft 365 Defender ( [https://security.microsoft.com](https://security.microsoft.com) ). Voici quelques points à garder à l’esprit :

- Actuellement, l’option de gestion de la protection contre la falsification dans le portail Microsoft 365 Defender est mise en place par défaut pour les nouveaux déploiements. Pour les déploiements existants, la protection contre la falsification est disponible sur la base de l’opt-in. Pour l’opter, dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender,</a>choisissez Paramètres points de terminaison  \> **Fonctionnalités** avancées de protection contre la \>  \> **falsification.**

- Lorsque vous utilisez le portail Microsoft 365 Defender pour gérer la protection contre la falsification, vous n’avez pas besoin d’utiliser Intune ou la méthode d’attachement du client.

- Lorsque vous gérez la protection contre la falsification dans le portail Microsoft 365 Defender, le paramètre est appliqué à l’échelle du client, affectant tous vos appareils exécutant Windows 10, Windows 10 Entreprise multisession, Windows 11, Windows 11 Entreprise  multisessage, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 ou Windows Server 2022. Pour affiner la protection contre la falsification (par exemple, une protection [](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager) contre la falsification sur certains appareils, mais pas pour d’autres), utilisez Microsoft Endpoint Manager ou Configuration Manager avec attachement [client.](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)

- Si vous avez un environnement hybride, les paramètres de protection contre la falsification configurés dans Intune prévalent sur les paramètres configurés dans le portail Microsoft 365 Defender client.

### <a name="requirements-for-managing-tamper-protection-in-the-microsoft-365-defender-portal"></a>Conditions requises pour la gestion de la protection contre la falsification dans le portail Microsoft 365 Defender web

- Des autorisations appropriées doivent vous être [attribuées, telles](/microsoft-365/security/defender-endpoint/assign-portal-access) que l’administrateur global, l’administrateur de sécurité ou les opérations de sécurité.

- Vos Windows doivent être en cours d’exécution dans l’une des versions suivantes Windows :
  
  - Windows 10
  - Windows 11
  - Windows 10 Entreprise à sessions multiples
  - Windows 11 Entreprise sessions multiples 
  - Windows Server 2019
  - Windows Server 2022
  - Windows Server, version 1803 ou ultérieure
  - Windows Server 2016
  - Windows Server 2012 R2

Pour plus d’informations sur les publication, [voir Windows 10 de publication.](/windows/release-health/release-information)

- Vos appareils doivent être [intégrés à Microsoft Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/onboarding)

- Vos appareils doivent utiliser la version de plateforme anti-programme malveillant (ou supérieure) et la version du moteur `4.18.2010.7` anti-programme malveillant `1.1.17600.5` (ou version supérieure). ([Gérez Antivirus Microsoft Defender mises à jour et appliquez les lignes de base.)](manage-updates-baselines-microsoft-defender-antivirus.md)

- [La protection cloud](enable-cloud-protection-microsoft-defender-antivirus.md) doit être allumée.

### <a name="turn-tamper-protection-on-or-off-in-the-microsoft-365-defender-portal"></a>Activer (ou désactiver) la protection contre la falsification dans le Microsoft 365 Defender web

:::image type="content" source="../../media/mde-turn-tamperprotectionon.png" alt-text="Activer la protection contre la falsification dans Microsoft 365 Defender portail.":::

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Choisissez **Paramètres** \> **points de terminaison.**

3. Go to **General** \> **Advanced features,** and then turn tamper protection on.

## <a name="manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager"></a>Gérer la protection contre la falsification pour votre organisation à l’aide Microsoft Endpoint Manager

Si votre organisation utilise Microsoft Endpoint Manager (MEM), vous pouvez activer (ou désactiver) la protection contre la falsification pour votre organisation dans le Centre d’administration Microsoft Endpoint Manager ( [https://endpoint.microsoft.com](https://endpoint.microsoft.com) ). Utilisez Intune lorsque vous souhaitez affiner les paramètres de protection contre la falsification. Par exemple, si vous souhaitez activer la protection contre la falsification sur certains appareils, mais pas sur tous, utilisez Intune.

### <a name="requirements-for-managing-tamper-protection-in-endpoint-manager"></a>Conditions requises pour la gestion de la protection contre les falsifications dans Endpoint Manager

- Vos appareils doivent être [intégrés à Microsoft Defender pour le point de terminaison.](/microsoft-365/security/defender-endpoint/onboarding)

- Des autorisations appropriées doivent vous être [attribuées, telles](/microsoft-365/security/defender-endpoint/assign-portal-access) que l’administrateur global, l’administrateur de sécurité ou les opérations de sécurité.

- Votre organisation utilise Microsoft Endpoint Manager [pour gérer les appareils.](/mem/endpoint-manager-getting-started) (Microsoft Endpoint Manager (MEM) sont requises ; MeM est inclus dans Microsoft 365 E3/E5, Enterprise Mobility + Security E3/E5, Microsoft 365 Business Premium, Microsoft 365 F1/F3, Microsoft 365  Gouvernement G3/G5 et licences éducation correspondantes.)

- Vos Windows doivent être en cours d’Windows 11 ou Windows 10 [1709,](/windows/release-health/status-windows-10-1709) [1803,](/windows/release-health/status-windows-10-1803) [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019)ou ultérieure. (Pour plus d’informations sur les publication, voir [Windows 10 de publication.)](/windows/release-health/release-information)

- Vous devez utiliser la sécurité [](https://www.microsoft.com/wdsi/definitions) Windows avec les informations de sécurité mises à jour vers la version 1.287.60.0 (ou supérieure).

- Vos appareils doivent utiliser la plateforme anti-programme malveillant version 4.18.1906.3 (ou supérieure) et la version de moteur anti-programme malveillant (ou version `1.1.15500.X` supérieure). ([Gérez Antivirus Microsoft Defender mises à jour et appliquez les lignes de base.)](manage-updates-baselines-microsoft-defender-antivirus.md)

### <a name="turn-tamper-protection-on-or-off-in-microsoft-endpoint-manager"></a>Activer (ou désactiver) la protection contre la falsification dans Microsoft Endpoint Manager

![Activer la protection contre la falsification avec Endpoint Manager.](images/turnontamperprotectinmem.png)

1. Dans le [centre Microsoft Endpoint Manager' administration,](https://go.microsoft.com/fwlink/?linkid=2109431)allez à **l’Antivirus** de sécurité de point de terminaison, puis choisissez \> + Créer **une stratégie.**

   - Dans la **liste Plateforme,** **sélectionnez Windows 10 et ultérieures.**
   - Dans la **liste Profil,** sélectionnez **Sécurité Windows expérience utilisateur.**

2. Créez un profil qui inclut le paramètre suivant :

    - **Activer la protection contre la falsification pour empêcher la désactivation de Microsoft Defender : Activer**

3. Affectez le profil à un ou plusieurs groupes.
 
### <a name="manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006"></a>Gérer la protection contre la falsification pour votre organisation avec Configuration Manager, version 2006

Si vous utilisez la [version 2006](/mem/configmgr/core/plan-design/changes/whats-new-in-version-2006)de Configuration Manager, vous pouvez gérer les paramètres de protection contre la falsification sur Windows 10, Windows 10 Entreprise multisession, Windows 11, Windows 11 Entreprise sessions multiples, Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 et Windows Server 2022 à l’aide d’une méthode appelée attachement *de client*. L’attachement client vous permet de synchroniser vos appareils Configuration Manager locaux uniquement dans le Centre d’administration Microsoft Endpoint Manager, puis de fournir des stratégies de configuration de sécurité de point de terminaison aux collections & périphériques.

> [!NOTE]
> La procédure peut être utilisée pour étendre la protection contre la falsification aux appareils exécutant Windows 10, Windows 10 Entreprise multisession, Windows 11, Windows 11 Entreprise multisession, Windows Server 2019 et Windows Server 2022. Veillez à examiner les conditions préalables et d’autres informations dans les ressources mentionnées dans cette procédure.

1. Configurer l’attachement du client. Pour plus d’informations, voir Commencer : créer et déployer des stratégies de sécurité de point de [terminaison à partir du Centre d’administration.](/mem/configmgr/tenant-attach/endpoint-security-get-started)

2. Dans le [centre Microsoft Endpoint Manager' administration,](https://go.microsoft.com/fwlink/?linkid=2109431)allez à **l’Antivirus** de sécurité de point de terminaison, puis choisissez \> + Créer **une stratégie.**

   - Dans la **liste Plateforme,** sélectionnez **Windows 10, Windows 11 et Windows Server (ConfigMgr).**
   - Dans la **liste Profil,** sélectionnez **Sécurité Windows expérience utilisateur (prévisualisation).**

3. Déployez la stratégie sur votre collection d’appareils.

#### <a name="need-help-with-this-method"></a>Vous avez besoin d’aide avec cette méthode ?

Consultez les ressources suivantes :

- [Paramètres profil d’expérience Sécurité Windows client dans Microsoft Intune](/mem/intune/protect/antivirus-security-experience-windows-settings)
- [Blog tech Community : Annonce de la protection contre la falsification pour les clients d’attachement de client Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

## <a name="manage-tamper-protection-on-an-individual-device"></a>Gérer la protection contre les falsifications sur un appareil individuel

> [!NOTE]
> La protection contre la falsification bloque les tentatives de modification Antivirus Microsoft Defender paramètres par le biais du Registre.
>
> Pour vous assurer que la protection contre la falsification n’interfère pas avec les produits de  sécurité non Microsoft ou les scripts d’installation d’entreprise qui modifient ces paramètres, allez à **Sécurité Windows** et mettez à jour l’intelligence de sécurité vers la version 1.287.60.0 ou ultérieure. (Voir mises [à jour de l’intelligence de la sécurité.)](https://www.microsoft.com/wdsi/definitions)
>
> Une fois cette mise à jour réalisée, la protection contre la falsification continue de protéger vos paramètres de Registre et les journaux tentent de les modifier sans renvoyer d’erreurs.

Si vous êtes un particulier ou si vous n’êtes pas soumis aux paramètres gérés par une équipe de sécurité, vous pouvez utiliser l’application Sécurité Windows pour gérer la protection contre la falsification. Vous devez avoir les autorisations d’administrateur appropriées sur votre appareil pour modifier les paramètres de sécurité, tels que la protection contre la falsification.

Voici ce que vous voyez dans l’application Sécurité Windows:

![La protection contre la falsification est Windows 10 Famille.](images/tamperprotectionturnedon.png)

1. Sélectionnez **Démarrer** et commencez à taper *Sécurité.* Dans les résultats de la recherche, **sélectionnez Sécurité Windows**.

2. Sélectionnez **Virus & protection contre les virus &** les \> **paramètres de protection contre les menaces.**

3. Définissez **la protection contre la** falsification sur **On** ou **Off**.

## <a name="are-you-using-windows-server-2016-or-windows-version-1709-1803-or-1809"></a>Utilisez-vous Windows Server 2016 ou Windows version 1709, 1803 ou 1809 ?

Si vous utilisez Windows Server 2016, Windows 10 version 1709, 1803 ou [1809,](/windows/release-health/status-windows-10-1809-and-windows-server-2019)la **protection** contre la falsification ne s’Sécurité Windows l’application. À la place, vous pouvez utiliser PowerShell pour déterminer si la protection contre la falsification est activée.

Sur Windows Server 2016, l’application Paramètres ne reflète pas précisément l’état de la protection en temps réel lorsque la protection contre la falsification est activée.

#### <a name="use-powershell-to-determine-whether-tamper-protection-and-real-time-protection-are-turned-on"></a>Utiliser PowerShell pour déterminer si la protection contre la falsification et la protection en temps réel sont allumées

1. Ouvrez l Windows PowerShell appl.

2. Utilisez [l’cmdlet Get-MpComputerStatus](/powershell/module/defender/get-mpcomputerstatus?preserve-view=true&view=win10-ps) PowerShell.

3. Dans la liste des résultats, recherchez `IsTamperProtected` ou `RealTimeProtectionEnabled` . (La valeur true *signifie que* la protection contre la falsification est activée.)

## <a name="view-information-about-tampering-attempts"></a>Afficher des informations sur les tentatives de falsification

Les tentatives de falsification indiquent généralement des cyberattaques plus importantes. Les acteurs mauvais tentent de modifier les paramètres de sécurité afin de les rendre persistants et non détectés. Si vous faites partie de l’équipe de sécurité de votre organisation, vous pouvez afficher des informations sur ces tentatives, puis prendre les mesures appropriées pour atténuer les menaces.

Lorsqu’une tentative de falsification est détectée, une alerte est détectée dans le [portail Microsoft 365 Defender (](/microsoft-365/security/defender-endpoint/portal-overview) [https://security.microsoft.com](https://security.microsoft.com) ).

![Microsoft 365 Defender.](images/tamperattemptalert.png)

À [l’protection évolutive des points de terminaison](overview-endpoint-detection-response.md) [](advanced-hunting-overview.md) des fonctionnalités de recherche avancées dans Microsoft Defender pour point de terminaison, votre équipe des opérations de sécurité peut examiner et résoudre ces tentatives.

## <a name="review-your-security-recommendations"></a>Passer en revue vos recommandations en matière de sécurité

La protection contre la falsification s’intègre aux fonctionnalités [& gestion des](next-gen-threat-and-vuln-mgt.md) menaces et des vulnérabilités. [Les recommandations en matière de sécurité](tvm-security-recommendation.md) incluent la garantie que la protection contre la falsification est allumée. Par exemple, vous pouvez effectuer une recherche en cas *de falsification.* Dans les résultats, vous pouvez sélectionner **Activer la protection** contre la falsification pour en savoir plus et l’activer.

![Activer la protection contre la falsification.](images/tamperprotectsecurityrecos.png)

Pour en savoir plus sur la gestion & des menaces et des [vulnérabilités,](tvm-dashboard-insights.md#dashboard-insights---threat-and-vulnerability-management)voir Informations sur le tableau de bord - Gestion des menaces et des vulnérabilités .

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="on-which-versions-of-windows-can-i-configure-tamper-protection"></a>Sur quelles versions de Windows puis-je configurer la protection contre la falsification ?

Windows 10 OS [1709](/windows/release-health/status-windows-10-1709), [1803](/windows/release-health/status-windows-10-1803), [1809](/windows/release-health/status-windows-10-1809-and-windows-server-2019)ou ultérieur avec [Microsoft Defender pour Endpoint](/microsoft-365/security/defender-endpoint).
  
Windows 10 Entreprise à sessions multiples

Windows 11

Windows 11 Entreprise sessions multiples
  
Si vous utilisez Configuration Manager, version 2006, avec attachement client, la protection contre la falsification peut être étendue à Windows Server 2012 R2, Windows Server 2016, Windows Server 2019 et Windows Server 2022. Voir Attachement client : créer et déployer une stratégie antivirus de sécurité de point de terminaison [à partir du Centre d’administration (prévisualisation).](/mem/configmgr/tenant-attach/deploy-antivirus-policy)

### <a name="will-tamper-protection-affect-non-microsoft-antivirus-registration-in-the-windows-security-app"></a>La protection contre la falsification affectera-t-elle l’inscription d’antivirus non Microsoft dans l Sécurité Windows app; ?

Non. Les offres antivirus autres que Microsoft continueront à s’inscrire auprès de l’application Sécurité Windows microsoft.

### <a name="what-happens-if-microsoft-defender-antivirus-is-not-active-on-a-device"></a>Que se passe-t-il si Antivirus Microsoft Defender n’est pas actif sur un appareil ?

Les appareils intégrés à Microsoft Defender pour le point de terminaison Antivirus Microsoft Defender en mode passif. Dans ce cas, la protection contre la falsification continuera à protéger le service et ses fonctionnalités.

### <a name="how-do-i-turn-tamper-protection-on-or-off"></a>Comment activer ou désactiver la protection contre la falsification ?

Si vous êtes un utilisateur d’accueil, voir Gérer la protection contre [les falsifications sur un appareil individuel.](#manage-tamper-protection-on-an-individual-device)

Si vous êtes une organisation qui utilise [Microsoft Defender pour le](/microsoft-365/security/defender-endpoint)point de terminaison, vous devez être en mesure de gérer la protection contre les falsifications dans Intune de la même façon que vous gérez d’autres fonctionnalités de protection des points de terminaison. Consultez les sections suivantes de cet article :

- [Gérer la protection contre les falsifications à l’aide Microsoft Endpoint Manager](#manage-tamper-protection-for-your-organization-using-microsoft-endpoint-manager)
- [Gérer la protection contre les falsifications à l’aide Microsoft 365 Defender portail](#manage-tamper-protection-for-your-organization-using-the-microsoft-365-defender-portal)

### <a name="how-does-configuring-tamper-protection-in-intune-affect-how-i-manage-microsoft-defender-antivirus-with-group-policy"></a>Comment la configuration de la protection contre les falsifications dans Intune affecte-t-elle la façon dont je Antivirus Microsoft Defender avec la stratégie de groupe ?

La stratégie de groupe ne s’applique pas à la protection contre la falsification. Les modifications apportées Antivirus Microsoft Defender paramètres de protection sont ignorées lorsque la protection contre la falsification est en cours.

### <a name="if-we-use-microsoft-intune-to-configure-tamper-protection-does-it-apply-only-to-the-entire-organization"></a>Si nous utilisons Microsoft Intune pour configurer la protection contre la falsification, s’applique-t-elle uniquement à l’ensemble de l’organisation ?

Vous avez la flexibilité nécessaire pour configurer la protection contre la falsification avec Intune. Vous pouvez cibler l’ensemble de votre organisation ou sélectionner des appareils et des groupes d’utilisateurs spécifiques.

### <a name="can-i-configure-tamper-protection-with-microsoft-endpoint-configuration-manager"></a>Puis-je configurer la protection contre la falsification Microsoft Endpoint Configuration Manager ?

Si vous utilisez l’attachement de client, vous pouvez utiliser Microsoft Endpoint Configuration Manager. Consultez les ressources suivantes :

- [Gérer la protection contre la falsification pour votre organisation avec Configuration Manager, version 2006](#manage-tamper-protection-for-your-organization-with-configuration-manager-version-2006)
- [Blog tech Community : Annonce de la protection contre la falsification pour les clients d’attachement de client Configuration Manager](https://techcommunity.microsoft.com/t5/microsoft-endpoint-manager-blog/announcing-tamper-protection-for-configuration-manager-tenant/ba-p/1700246#.X3QLR5Ziqq8.linkedin)

### <a name="i-have-the-windows-e3-enrollment-can-i-use-configuring-tamper-protection-in-intune"></a>J’ai le Windows inscription E3. Puis-je utiliser la configuration de la protection contre la falsification dans Intune ?

Actuellement, la configuration de la protection contre la falsification dans Intune est disponible uniquement pour les clients qui ont [Microsoft Defender pour point de terminaison.](/microsoft-365/security/defender-endpoint)

### <a name="what-happens-if-i-try-to-change-microsoft-defender-for-endpoint-settings-in-intune-microsoft-endpoint-configuration-manager-and-windows-management-instrumentation-when-tamper-protection-is-enabled-on-a-device"></a>Que se passe-t-il si j’essaie de modifier les paramètres de Microsoft Defender for Endpoint dans Intune, Microsoft Endpoint Configuration Manager et Windows Management Instrumentation lorsque la protection contre la falsification est activée sur un appareil ?

Vous ne pourrez pas modifier les fonctionnalités protégées par la protection contre la falsification . ces demandes de modification sont ignorées.

### <a name="im-an-enterprise-customer-can-local-admins-change-tamper-protection-on-their-devices"></a>Je suis un client d’entreprise. Les administrateurs locaux peuvent-ils modifier la protection contre la falsification sur leurs appareils ?

Non. Les administrateurs locaux ne peuvent pas modifier ou modifier les paramètres de protection contre la falsification.

### <a name="what-happens-if-my-device-is-onboarded-with-microsoft-defender-for-endpoint-and-then-goes-into-an-off-boarded-state"></a>Que se passe-t-il si mon appareil est intégré à Microsoft Defender pour Endpoint, puis passe dans un état hors intégration ?

Si un appareil est désintérable à partir de Microsoft Defender pour le point de terminaison, la protection contre la falsification est allumée, qui est l’état par défaut pour les appareils non utilisés.

### <a name="if-the-status-of-tamper-protection-changes-are-alerts-shown-in-the-microsoft-365-defender-portal"></a>Si l’état de la protection contre la falsification change, les alertes s’affiche-t-elles sur le Microsoft 365 Defender web ?

Oui. L’alerte s’affiche [https://security.microsoft.com](https://security.microsoft.com) sous **Alertes.**

Votre équipe des opérations de sécurité peut également utiliser des requêtes de recherche, telles que l’exemple suivant :

`AlertInfo|where Title == "Tamper Protection bypass"`

[Afficher des informations sur les tentatives de falsification.](#view-information-about-tampering-attempts)

## <a name="see-also"></a>Voir aussi

[Sécurisation de Windows PC avec des Endpoint Protection pour Microsoft Intune](/intune/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune)

[Obtenir une vue d’ensemble de Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint)

[Mieux ensemble : Antivirus Microsoft Defender et Microsoft Defender pour point de terminaison](why-use-microsoft-defender-antivirus.md)
