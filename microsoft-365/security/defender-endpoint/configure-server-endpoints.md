---
title: Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison
description: Intégrer des serveurs Windows afin qu’ils puissent envoyer des données de capteur au capteur Microsoft Defender pour point de terminaison.
keywords: serveur d’intégration, serveur, 2012r2, 2016, 2019, intégration de serveur, gestion des appareils, configuration de serveurs Microsoft Defender pour point de terminaison, intégration de serveurs Microsoft Defender pour point de terminaison, intégration serveurs Microsoft Defender pour point de terminaison
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
author: mjcaparas
ms.author: macapara
ms.localizationpriority: medium
ms.date: 08/10/2022
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365-initiative-defender-endpoint
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 6e0b53da9117577ec0d0cee98431e30d265f96dc
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67711540"
---
# <a name="onboard-windows-servers-to-the-microsoft-defender-for-endpoint-service"></a>Intégrer des serveurs Windows au service Microsoft Defender pour point de terminaison

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- Windows Server 2012 R2
- Windows Server 2016
- Windows Server Semi-Annual Enterprise Channel
- Windows Server 2019 et versions ultérieures
- Windows Server 2019 Core Edition
- Windows Server 2022
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-configserver-abovefoldlink)

Defender pour point de terminaison étend la prise en charge pour inclure également le système d’exploitation Windows Server. Cette prise en charge fournit des fonctionnalités avancées de détection des attaques et d’investigation en toute transparence via la console Microsoft 365 Defender. La prise en charge de Windows Server fournit des informations plus approfondies sur les activités du serveur, la couverture de la détection des attaques de noyau et de mémoire, et permet des actions de réponse.

Cette rubrique explique comment intégrer des serveurs Windows spécifiques à Microsoft Defender pour point de terminaison.

Pour obtenir des conseils sur le téléchargement et l’utilisation de Sécurité Windows bases de référence pour les serveurs Windows, consultez [Sécurité Windows Lignes de base](/windows/device-security/windows-security-baselines).

## <a name="windows-server-onboarding-overview"></a>Vue d’ensemble de l’intégration de Windows Server

Vous devez suivre les étapes générales suivantes pour intégrer correctement les serveurs.

:::image type="content" source="images/server-onboarding-tools-methods.png" alt-text="Illustration du flux d’intégration pour les serveurs Windows et les appareils Windows 10" lightbox="images/server-onboarding-tools-methods.png":::

## <a name="integration-with-microsoft-defender-for-servers"></a>Intégration à Microsoft Defender pour serveurs

Microsoft Defender pour point de terminaison s’intègre en toute transparence à Microsoft Defender pour serveurs. Vous pouvez intégrer automatiquement des serveurs, faire en fait apparaître des serveurs surveillés par Microsoft Defender pour cloud dans Defender pour point de terminaison et effectuer des investigations détaillées en tant que client Microsoft Defender pour cloud.

Pour plus d’informations, consultez [Intégration à Microsoft Defender pour le cloud](azure-server-integration.md).

> [!NOTE]
> Pour Windows Server 2012 R2 et 2016 exécutant la solution unifiée moderne, vous pouvez soit installer/mettre à niveau manuellement la nouvelle solution sur ces machines, soit utiliser l’intégration pour déployer automatiquement ou mettre à niveau les serveurs couverts par votre plan Microsoft Defender pour Server respectif. Pour plus d’informations sur l’utilisation du commutateur sur [Protéger vos points de terminaison avec la solution EDR intégrée de Defender pour Cloud , Microsoft Defender pour point de terminaison](/azure/defender-for-cloud/integration-defender-for-endpoint?tabs=windows).
> - Lorsque vous utilisez Microsoft Defender pour cloud pour surveiller les serveurs, un locataire Defender pour point de terminaison est automatiquement créé (aux États-Unis pour les utilisateurs américains, dans l’UE pour les utilisateurs européens et au Royaume-Uni pour les utilisateurs du Royaume-Uni).
Les données collectées par Defender pour point de terminaison sont stockées dans l’emplacement géographique du locataire, comme identifié lors de l’approvisionnement.
> - Si vous utilisez Defender pour point de terminaison avant d’utiliser Microsoft Defender pour cloud, vos données sont stockées à l’emplacement que vous avez spécifié lors de la création de votre locataire, même si vous intégrez Microsoft Defender pour Cloud ultérieurement.
> - Une fois configuré, vous ne pouvez pas modifier l’emplacement où vos données sont stockées. Si vous devez déplacer vos données vers un autre emplacement, vous devez contacter pomoc techniczna firmy Microsoft pour réinitialiser le locataire.
> - L’intégration entre Microsoft Defender pour serveurs et Microsoft Defender pour point de terminaison a été étendue pour prendre en charge Windows Server 2022, [Windows Server 2019 et Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)
> - La surveillance des points de terminaison de serveur utilisant cette intégration a été désactivée pour Office 365 clients GCC.

**Windows Server 2012 R2 et Windows Server 2016** :

- Télécharger les packages d’installation et d’intégration
- Appliquer le package d’installation
- Suivez les étapes d’intégration de l’outil correspondant

**Windows Server Semi-Annual Enterprise Channel et Windows Server 2019** :

- Télécharger le package d’intégration
- Suivez les étapes d’intégration de l’outil correspondant

>[!IMPORTANT]
>Pour pouvoir acheter Microsoft Defender pour point de terminaison référence SKU server, vous devez avoir déjà acheté un minimum combiné des licences d’abonnement Windows E5/A5, Microsoft 365 E5/A5 ou Microsoft 365 E5 Sécurité suivantes.  Pour plus d’informations sur les licences, consultez les [termes du produit](https://www.microsoft.com/licensing/terms/productoffering/MicrosoftDefenderforEndpointServer/all).

### <a name="new-windows-server-2012-r2-and-2016-functionality-in-the-modern-unified-solution"></a>Nouvelles fonctionnalités Windows Server 2012 R2 et 2016 dans la solution unifiée moderne

L’implémentation précédente de l’intégration Windows Server 2012 R2 et Windows Server 2016 nécessitait l’utilisation de Microsoft Monitoring Agent (MMA).

Le nouveau package de solution unifiée facilite l’intégration des serveurs en supprimant les dépendances et les étapes d’installation. En outre, ce package de solution unifié est fourni avec les améliorations majeures suivantes :

- [Antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/microsoft-defender-antivirus-windows) avec [protection nouvelle génération](/microsoft-365/security/defender-endpoint/next-generation-protection) pour Windows Server 2012 R2
- [Règles de réduction de la surface d’attaque (ASR)](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)
- [Protection réseau](/microsoft-365/security/defender-endpoint/network-protection)
- [Accès contrôlé aux dossiers](/microsoft-365/security/defender-endpoint/controlled-folders)
- [Blocage d’applications potentiellement indésirables (PUA)](/microsoft-365/security/defender-endpoint/detect-block-potentially-unwanted-apps-microsoft-defender-antivirus)
- [Fonctionnalités de détection améliorées](/microsoft-365/security/defender-endpoint/overview-endpoint-detection-response)
- [Fonctionnalités de réponse étendues sur les](/microsoft-365/security/defender-endpoint/respond-machine-alerts) appareils et [les fichiers](/microsoft-365/security/defender-endpoint/respond-file-alerts)
- [EDR en mode bloc](/microsoft-365/security/defender-endpoint/edr-in-block-mode)
- [Réponse en direct](/microsoft-365/security/defender-endpoint/live-response)
- [Investigation et réponse automatisées (AIR)](/microsoft-365/security/defender-endpoint/automated-investigations)
- [Protection contre les falsifications](/microsoft-365/security/defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection)

Selon le serveur que vous intègrez, la solution unifiée installe l’antivirus Microsoft Defender et/ou le capteur EDR. Le tableau suivant indique quel composant est installé et ce qui est intégré par défaut.

|Version du serveur|Av|EDR|
|----|----|----|
|Windows Server 2012 R2 SP1|![Oui.](images/svg/check-yes.svg)|![Oui.](images/svg/check-yes.svg)|
|Windows Server 2016|Intégré|![Oui.](images/svg/check-yes.svg)|
|Windows Server 2019 ou version ultérieure|Intégré|Intégré|

Si vous avez déjà intégré vos serveurs à l’aide de MMA, suivez les instructions fournies dans la [migration de serveur](server-migration.md) pour migrer vers la nouvelle solution.

#### <a name="known-issues-and-limitations-in-the-new-unified-solution-package-for-windows-server-2012-r2-and-2016"></a>Problèmes connus et limitations dans le nouveau package de solution unifié pour Windows Server 2012 R2 et 2016

Les spécificités suivantes s’appliquent au nouveau package de solution unifiée pour Windows Server 2012 R2 et 2016 :

- Une mise à jour du système d’exploitation peut introduire un problème d’installation sur des machines avec des disques plus lents en raison d’un délai d’expiration avec l’installation du service. L’installation échoue avec le message « Impossible de trouver c:\program files\windows defender\mpasdesc.dll, - 310 WinDefend ». Utilisez le dernier package d’installation, ainsi que le dernier script [install.ps1](https://github.com/microsoft/mdefordownlevelserver) pour faciliter l’effacement de l’installation ayant échoué si nécessaire.
- Vérifiez que les exigences de connectivité spécifiées dans [Activer l’accès aux URL de service Microsoft Defender pour point de terminaison dans le serveur proxy](/microsoft-365/security/defender-endpoint/configure-proxy-internet?enable-access-to-microsoft-defender-for-endpoint-service-urls-in-the-proxy-server) sont remplies. Ils sont équivalents à ces exigences pour Windows Server 2019.
- Nous avons identifié un problème de connectivité Windows Server 2012 R2 au cloud lorsque TelemetryProxyServer statique est utilisé **et** que les URL de liste de révocation de certificats (CRL) ne sont pas accessibles à partir du contexte du compte SYSTEM. L’atténuation immédiate consiste à utiliser une autre option de proxy (« à l’échelle du système ») qui fournit une telle connectivité, ou à configurer le même proxy via le paramètre WinInet sur le contexte du compte SYSTÈME.
Vous pouvez également utiliser les instructions fournies dans La [solution de contournement pour un problème connu avec TelemetryProxyServer sur les machines déconnectées](#workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines) pour installer un certificat comme solution de contournement.
- Auparavant, l’utilisation de Microsoft Monitoring Agent (MMA) sur Windows Server 2016 et les versions ultérieures permettait à la passerelle OMS/Log Analytics de fournir une connectivité aux services cloud Defender. La nouvelle solution, comme Microsoft Defender pour point de terminaison sur Windows Server 2019, Windows Server 2022 et Windows 10, ne prend pas en charge cette passerelle.
- Sur Windows Server 2016, vérifiez que l’antivirus Microsoft Defender est installé, qu’il est actif et à jour. Vous pouvez télécharger et installer la dernière version de la plateforme à l’aide de Windows Update. Vous pouvez également télécharger le package de mise à jour manuellement à partir du [catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) ou de [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).
- Sur Windows Server 2012 R2, il n’existe aucune interface utilisateur pour l’antivirus Microsoft Defender. En outre, l’interface utilisateur sur Windows Server 2016 autorise uniquement les opérations de base. Pour effectuer des opérations sur un appareil localement, [reportez-vous à Gérer les Microsoft Defender pour point de terminaison avec PowerShell, WMI et MPCmdRun.exe](/microsoft-365/security/defender-endpoint/manage-mde-post-migration-other-tools). Par conséquent, les fonctionnalités qui reposent spécifiquement sur l’interaction de l’utilisateur, par exemple lorsque l’utilisateur est invité à prendre une décision ou à effectuer une tâche spécifique, peuvent ne pas fonctionner comme prévu. Il est recommandé de désactiver ou de ne pas activer l’interface utilisateur, ni d’exiger l’interaction de l’utilisateur sur un serveur géré, car cela peut avoir un impact sur la fonctionnalité de protection.
- Toutes les règles de réduction de la surface d’attaque ne sont pas disponibles sur tous les systèmes d’exploitation. Consultez [les règles de réduction de la surface d’attaque (ASR](/microsoft-365/security/defender-endpoint/attack-surface-reduction-rules)).
- Pour activer [la protection réseau](/microsoft-365/security/defender-endpoint/network-protection), d’autres configurations sont nécessaires :
  - `Set-MpPreference -EnableNetworkProtection Enabled`
  - `Set-MpPreference -AllowNetworkProtectionOnWinServer 1`
  - `Set-MpPreference -AllowNetworkProtectionDownLevel 1`
  - `Set-MpPreference -AllowDatagramProcessingOnWinServer 1`

  En outre, sur les machines avec un volume élevé de trafic réseau, les tests de performances dans votre environnement sont fortement recommandés avant d’activer cette fonctionnalité à grande échelle. Vous devrez peut-être tenir compte de la consommation supplémentaire de ressources.
- Sur Windows Server 2012 R2, les événements réseau peuvent ne pas être renseignés dans la chronologie. Ce problème nécessite une Windows Update publiée dans le cadre du [correctif cumulatif mensuel du 12 octobre 2021 (KB5006714).](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e)
- Les mises à niveau du système d’exploitation ne sont pas prises en charge. Désinstégez-le, puis désinstallez-le avant la mise à niveau.
- Les exclusions automatiques pour les **rôles serveur** ne sont pas prises en charge sur Windows Server 2012 R2 . Toutefois, les exclusions intégrées pour les fichiers de système d’exploitation le sont. Pour plus d’informations sur l’ajout d’exclusions, consultez [les recommandations d’analyse antivirus pour les ordinateurs d’entreprise qui exécutent des versions actuellement prises en charge de Windows](https://support.microsoft.com/topic/virus-scanning-recommendations-for-enterprise-computers-that-are-running-currently-supported-versions-of-windows-kb822158-c067a732-f24a-9079-d240-3733e39b40bc).
- Sur les machines qui ont été mises à niveau à partir de la solution MMA précédente et que le capteur EDR est une version (préversion) antérieure à 10.8047.22439.1056, la désinstallation et le rétablissement de la solution basée sur MMA peuvent entraîner des blocages. Si vous utilisez une telle préversion, mettez à jour à l’aide de KB5005292.
- Pour déployer et intégrer la nouvelle solution à l’aide de Microsoft Endpoint Manager, ce processus nécessite actuellement la création d’un package. Pour plus d’informations sur le déploiement de programmes et de scripts dans Configuration Manager, consultez [Packages et programmes dans Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs). MECM 2107 avec le correctif cumulatif ou ultérieur est requis pour prendre en charge la gestion de la configuration de stratégie à l’aide du nœud Endpoint Protection.

## <a name="workaround-for-a-known-issue-with-telemetryproxyserver-on-disconnected-machines"></a>Solution de contournement pour un problème connu avec TelemetryProxyServer sur les machines déconnectées

Description du problème : lorsque vous utilisez le paramètre TelemetryProxyServer pour spécifier un proxy à utiliser par le composant EDR de Microsoft Defender pour point de terminaison, sur les ordinateurs qui n’ont aucun autre moyen d’accéder à l’URL de liste de révocation de certificats (CRL), un certificat intermédiaire manquant entraîne l’échec de la connexion du capteur EDR au service cloud.

Scénario affecté : -Microsoft Defender pour point de terminaison avec sense version number 10.8048.22439.1065 ou versions antérieures en préversion s’exécutant sur Windows Server 2012 R2 -Utilisation de la configuration proxy TelemetryProxyServer ; d’autres méthodes ne sont pas affectées

Contournement:
1. Vérifiez que l’ordinateur exécute Sense version 10.8048.22439.1065 ou ultérieure en installant à l’aide du dernier package disponible à partir de la page d’intégration ou en appliquant KB5005292.
2. Télécharger et décompresser le certificat à partir de https://github.com/microsoft/mdefordownlevelserver/blob/main/InterCA.zip
3. Importez le certificat dans le magasin « Autorités de certification intermédiaires » approuvé par l’ordinateur local.
Vous pouvez utiliser la commande PowerShell : Import-Certificate -FilePath .\InterCA.cer -CertStoreLocation Cert:\LocalMachine\Ca

## <a name="integration-with-microsoft-defender-for-cloud"></a>Intégration de à Microsoft Defender pour le cloud

Microsoft Defender pour point de terminaison s’intègre en toute transparence à Microsoft Defender pour cloud. Vous pouvez intégrer automatiquement des serveurs, faire en fait apparaître des serveurs surveillés par Microsoft Defender pour cloud dans Defender pour point de terminaison et effectuer des investigations détaillées en tant que client Microsoft Defender pour cloud. 

Pour plus d’informations, consultez [Intégration à Microsoft Defender pour le cloud](azure-server-integration.md). Les serveurs Linux intégrés via Microsoft Defender pour cloud auront leur configuration initiale définie pour exécuter l’antivirus Defender en [mode passif](/defender-endpoint/microsoft-defender-antivirus-compatibility#microsoft-defender-antivirus-and-non-microsoft-antivirusantimalware-solutions).

> [!NOTE]
> - L’intégration entre Microsoft Defender pour serveurs et Microsoft Defender pour point de terminaison a été étendue pour prendre en charge Windows Server 2022, [Windows Server 2019 et Windows Virtual Desktop (WVD).](/azure/security-center/release-notes#microsoft-defender-for-endpoint-integration-with-azure-defender-now-supports-windows-server-2019-and-windows-10-virtual-desktop-wvd-in-preview)
> - La surveillance des points de terminaison de serveur utilisant cette intégration a été désactivée pour Office 365 clients GCC.

## <a name="windows-server-2012-r2-and-windows-server-2016"></a>Windows Server 2012 R2 et Windows Server 2016

### <a name="prerequisites"></a>Prerequisites

#### <a name="prerequisites-for-windows-server-2012-r2"></a>Prérequis pour Windows Server 2012 R2

Si vous avez entièrement mis à jour vos machines avec le dernier package [de cumul mensuel](https://support.microsoft.com/topic/october-12-2021-kb5006714-monthly-rollup-4dc4a2cd-677c-477b-8079-dcfef2bda09e) , il **n’existe pas** d’autres prérequis.

Le package d’installation vérifie si les composants suivants ont déjà été installés via une mise à jour :

- [Mise à jour pour l’expérience client et la télémétrie de diagnostic](https://support.microsoft.com/help/3080149/update-for-customer-experience-and-diagnostic-telemetry)
- [Mise à jour pour le runtime C universel dans Windows](https://support.microsoft.com/topic/update-for-universal-c-runtime-in-windows-c0514201-7fe6-95a3-b0a5-287930f3560c)

#### <a name="prerequisites-for-windows-server-2016"></a>Prérequis pour Windows Server 2016

- La mise à jour de la pile de maintenance (SSU) du 14 septembre 2021 ou une version ultérieure doit être installée.
- La dernière mise à jour cumulative (LCU) du 20 septembre 2018 ou une version ultérieure doit être installée.  Il est recommandé d’installer les derniers SSU et LCU disponibles sur le serveur
- Activez la fonctionnalité antivirus Microsoft Defender et assurez-vous qu’elle est à jour. Pour plus d’informations sur l’activation de l’antivirus Defender sur Windows Server, consultez [Réactiver l’antivirus Defender sur Windows Server s’il a été désactivé](enable-update-mdav-to-latest-ws.md#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-disabled) et [réactiver l’antivirus Defender sur Windows Server s’il a été désinstallé](enable-update-mdav-to-latest-ws.md#re-enable-microsoft-defender-antivirus-on-windows-server-if-it-was-uninstalled).
- Téléchargez et installez la dernière version de la plateforme à l’aide de Windows Update. Vous pouvez également télécharger le package de mise à jour manuellement à partir du [catalogue Microsoft Update](https://www.catalog.update.microsoft.com/Search.aspx?q=KB4052623) ou de [MMPC](https://go.microsoft.com/fwlink/?linkid=870379&arch=x64).

#### <a name="prerequisites-for-running-with-third-party-security-solutions"></a>Conditions préalables à l’exécution avec des solutions de sécurité tierces

Si vous envisagez d’utiliser une solution anti-programme malveillant tierce, vous devez exécuter l’antivirus Microsoft Defender en mode passif. Vous devez vous rappeler de définir le mode passif pendant le processus d’installation et d’intégration.

> [!NOTE]
> Si vous installez Microsoft Defender pour point de terminaison sur des serveurs avec McAfee Endpoint Security (ENS) ou VirusScan Enterprise (VSE), la version de la plateforme McAfee devra peut-être être mise à jour pour garantir que l’antivirus Microsoft Defender n’est pas supprimé ou désactivé. Pour plus d’informations, notamment les numéros de version spécifiques requis, consultez [l’article du Centre de connaissances McAfee](https://kcm.trellix.com/corporate/index?page=content&id=KB88214).

#### <a name="update-package-for-microsoft-defender-for-endpoint-on-windows-server-2012-r2-and-2016"></a>Package de mise à jour pour Microsoft Defender pour point de terminaison sur Windows Server 2012 R2 et 2016

Pour recevoir régulièrement des améliorations et des correctifs pour le composant capteur EDR, assurez-vous Windows Update [KB5005292](https://go.microsoft.com/fwlink/?linkid=2168277) est appliqué ou approuvé. En outre, pour conserver les composants de protection mis à jour, consultez [Gérer les mises à jour de l’Antivirus Microsoft Defender et appliquer des lignes de base](/microsoft-365/security/defender-endpoint/manage-updates-baselines-microsoft-defender-antivirus#monthly-platform-and-engine-versions).

Si vous utilisez Windows Server Update Services (WSUS) et/ou Microsoft Endpoint Configuration Manager, cette nouvelle « mise à jour Microsoft Defender pour point de terminaison pour le capteur EDR » est disponible dans la catégorie « Microsoft Defender pour point de terminaison ».

### <a name="onboarding-steps-summary"></a>Résumé des étapes d’intégration

- ÉTAPE 1 : [Télécharger les packages d’installation et d’intégration](#step-1-download-installation-and-onboarding-packages)
- ÉTAPE 2 : [Appliquer le package d’installation et d’intégration](#step-2-apply-the-installation-and-onboarding-package)
- ÉTAPE 3 : [Effectuer les étapes d’intégration](#step-3-complete-the-onboarding-steps)

### <a name="step-1-download-installation-and-onboarding-packages"></a>ÉTAPE 1 : Télécharger les packages d’installation et d’intégration

Vous devez télécharger les packages **d’installation** et **d’intégration** à partir du portail.

> [!NOTE]
> Le package d’installation est mis à jour tous les mois. Veillez à télécharger le dernier package avant l’utilisation.

> [!div class="mx-imgBorder"]
> ![Image du tableau de bord d’intégration](images/install-agent-onboard.png)

   > [!NOTE]
   > Sur Windows Server 2012R2, l’Antivirus Microsoft Defender sera installé par le package d’installation et sera actif, sauf si vous le définissez en mode passif. Sur Windows Server 2016, l’antivirus Microsoft Defender doit être installé en tant que fonctionnalité (voir [Basculer vers MDE](/microsoft-365/security/defender-endpoint/switch-to-mde-phase-2#re-enable-microsoft-defender-antivirus-on-windows-server-2016)) d’abord et entièrement mis à jour avant de poursuivre l’installation.
   >
   > Si vous exécutez une solution anti-programme malveillant non Microsoft, veillez à ajouter des exclusions pour l’antivirus Microsoft Defender ([à partir de cette liste de processus Microsoft Defender sous l’onglet Processus Defender](https://download.microsoft.com/download/6/b/f/6bfff670-47c3-4e45-b01b-64a2610eaefa/mde-urls-commercial.xlsx)) à la solution non-Microsoft avant l’installation.  Il est également recommandé d’ajouter des solutions de sécurité non-Microsoft à la liste d’exclusions antivirus Defender.

Le **package d’installation** contient un fichier MSI qui installe l’agent Microsoft Defender pour point de terminaison.

Le **package d’intégration** contient les fichiers suivants :

- `OptionalParamsPolicy` - contient le paramètre qui active la collecte d’exemples
- `WindowsDefenderATPOnboardingScript.cmd` - contient le script d’intégration

Pour télécharger les packages, procédez comme suit :

1. Dans Microsoft 365 Defender, accédez à **Paramètres > 裝置管理 > Intégration**.

2. Sélectionnez **Windows Server 2012 R2 et 2016**.

3. Sélectionnez **Télécharger le package d’installation** et enregistrez le fichier .msi.

4. Sélectionnez **Télécharger le package d’intégration** et enregistrez le fichier .zip.

5. Installez le package d’installation à l’aide de l’une des options permettant d’installer l’antivirus Microsoft Defender. L’installation nécessite des autorisations d’administration.

### <a name="step-2-apply-the-installation-and-onboarding-package"></a>ÉTAPE 2 : Appliquer le package d’installation et d’intégration

Dans cette étape, vous allez installer les composants de prévention et de détection requis avant d’intégrer votre appareil à l’environnement cloud Microsoft Defender pour point de terminaison, afin de préparer l’ordinateur à l’intégration. Vérifiez que toutes les [conditions préalables ont été remplies](#prerequisites) .

   > [!NOTE]
   > L’antivirus Microsoft Defender sera installé et sera actif, sauf si vous le définissez en mode passif.

#### <a name="options-to-install-the-microsoft-defender-for-endpoint-packages"></a>Options d’installation des packages Microsoft Defender pour point de terminaison

Dans la section précédente, vous avez téléchargé un package d’installation. Le package d’installation contient le programme d’installation de tous les composants Microsoft Defender pour point de terminaison.

Vous pouvez utiliser l’une des options suivantes pour installer l’agent :

- [Installer à l’aide de la ligne de commande](#install-microsoft-defender-for-endpoint-using-the-command-line)
- [Installer à l’aide d’un script](#install-microsoft-defender-for-endpoint-using-a-script)
- [Appliquer les packages d’installation et d’intégration à l’aide de نهج المجموعة](#apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy)

##### <a name="install-microsoft-defender-for-endpoint-using-the-command-line"></a>Installer Microsoft Defender pour point de terminaison à l’aide de la ligne de commande

Utilisez le package d’installation de l’étape précédente pour installer Microsoft Defender pour point de terminaison.

Exécutez la commande suivante pour installer Microsoft Defender pour point de terminaison :

```console
Msiexec /i md4ws.msi /quiet
```

Pour désinstaller, vérifiez que la machine est d’abord désinstégée à l’aide du script de désintégrage approprié. Utilisez ensuite لوحة التحكم \> programmes \> et fonctionnalités pour effectuer la désinstallation.

Vous pouvez également exécuter la commande de désinstallation suivante pour désinstaller Microsoft Defender pour point de terminaison :

```console
Msiexec /x md4ws.msi /quiet
```

Pour que la commande ci-dessus réussisse, vous devez utiliser le même package que celui que vous avez utilisé pour l’installation.

Le `/quiet` commutateur supprime toutes les notifications.

> [!NOTE]
> L’Antivirus Microsoft Defender ne passe pas automatiquement en mode passif. Vous pouvez choisir de définir l’antivirus Microsoft Defender pour qu’il s’exécute en mode passif si vous exécutez une solution antivirus/anti-programme malveillant non Microsoft. Pour les installations en ligne de commande, le composant antivirus Microsoft Defender facultatif `FORCEPASSIVEMODE=1` est immédiatement paramétré en mode passif pour éviter toute interférence. Ensuite, pour vous assurer que l’Antivirus Defender reste en mode passif après l’intégration pour prendre en charge des fonctionnalités telles que le bloc EDR, définissez la clé de Registre « ForceDefenderPassiveMode ».

La prise en charge de Windows Server fournit des informations plus approfondies sur les activités du serveur, la couverture de la détection des attaques de noyau et de mémoire, et permet des actions de réponse.

##### <a name="install-microsoft-defender-for-endpoint-using-a-script"></a>Installer Microsoft Defender pour point de terminaison à l’aide d’un script

Vous pouvez utiliser le [script du programme d’installation](server-migration.md#installer-script) pour automatiser l’installation, la désinstallation et l’intégration. 
> [!NOTE]
> Le script d’installation est signé. Toute modification apportée au script invalide la signature. Lorsque vous téléchargez le script à partir de GitHub, l’approche recommandée pour éviter toute modification accidentelle consiste à télécharger les fichiers sources sous forme d’archive zip, puis à l’extraire pour obtenir le fichier install.ps1 (sur la page code principale, cliquez sur le menu déroulant Code et sélectionnez « Télécharger zip »).

Ce script peut être utilisé dans différents scénarios, y compris ceux décrits dans [les scénarios de migration de serveur de la solution Microsoft Defender pour point de terminaison MMA précédente](/microsoft-365/security/defender-endpoint/server-migration) et pour le déploiement à l’aide de نهج المجموعة comme décrit ci-dessous.

##### <a name="apply-the-microsoft-defender-for-endpoint-installation-and-onboarding-packages-using-group-policy"></a>Appliquer les packages d’installation et d’intégration Microsoft Defender pour point de terminaison à l’aide de la stratégie de groupe

1. Créez une stratégie de groupe : <br> Ouvrez la [console de gestion نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur **نهج المجموعة Objets** que vous souhaitez configurer, puis cliquez sur **Nouveau**. Entrez le nom du nouvel objet de stratégie de groupe dans la boîte de dialogue qui s’affiche, puis cliquez sur **OK**.

2. Ouvrez la [console de gestion نهج المجموعة](/internet-explorer/ie11-deploy-guide/group-policy-and-group-policy-mgmt-console-ie11) (GPMC), cliquez avec le bouton droit sur l’objet نهج المجموعة (GPO) que vous souhaitez configurer, puis cliquez sur **Modifier**.

3. Dans **l’éditeur de gestion نهج المجموعة**, accédez à **Configuration de l’ordinateur**, puis **Préférences**, puis **aux paramètres du Panneau de configuration**.

4. Cliquez avec le bouton droit sur **Tâches planifiées**, **pointez sur Nouveau**, puis cliquez sur **Tâche immédiate (Au moins Windows 7).**

5. Dans la fenêtre **Tâche** qui s’ouvre, accédez à l’onglet **Général** . Sous **Options de sécurité** , cliquez sur **Modifier l’utilisateur ou le groupe** et tapez SYSTEM, puis cliquez sur **Vérifier les noms** , puis **SUR OK**. NT AUTHORITY\SYSTEM apparaît sous la forme du compte d’utilisateur sous lequel la tâche s’exécutera.

6. Sélectionnez **Exécuter si l’utilisateur est connecté ou non** et cochez la case **Exécuter avec les privilèges les plus élevés** .

7. Dans le champ Nom, tapez un nom approprié pour la tâche planifiée (par exemple, Defender pour le déploiement de point de terminaison).

8. Accédez à l’onglet **Actions** et **sélectionnez Nouveau...** Vérifiez que **démarrer un programme** est sélectionné dans le champ **Action** . Le [script du programme d’installation](server-migration.md#installer-script) gère l’installation et effectue immédiatement l’étape d’intégration une fois l’installation terminée. Sélectionnez *C:\Windows\System32\WindowsPowerShell\v1.0\powershell.exe* puis fournissez les arguments :

    ```console
     -ExecutionPolicy RemoteSigned \\servername-or-dfs-space\share-name\install.ps1 -OnboardingScript \\servername-or-dfs-space\share-name\windowsdefenderatponboardingscript.cmd
    ```

    > [!NOTE]

    > Le paramètre de stratégie d’exécution recommandé est `Allsigned`. Cela nécessite l’importation du certificat de signature du script dans le magasin serveurs de publication approuvés de l’ordinateur local si le script s’exécute en tant que système sur le point de terminaison.

    Remplacez \\servername-or-dfs-space\share-name par le chemin UNC, en utilisant le nom de domaine complet (FQDN) du fichier *install.ps1* partagé. Le package d’installation md4ws.msi doit être placé dans le même répertoire.  Assurez-vous que les autorisations du chemin UNC autorisent l’accès en écriture au compte d’ordinateur qui installe le package, pour prendre en charge la création de fichiers journaux. Si vous souhaitez désactiver la création de fichiers journaux (non recommandé), vous pouvez utiliser les paramètres -noETL -noETW.

    Pour les scénarios dans lesquels vous souhaitez que l’antivirus Microsoft Defender coexiste avec des solutions anti-programme malveillant non Microsoft, ajoutez le paramètre $Passive pour définir le mode passif pendant l’installation.

9. Sélectionnez **OK** et fermez toutes les fenêtres GPMC ouvertes.

10. Pour lier l’objet de stratégie de groupe à une unité d’organisation, cliquez avec le bouton droit et sélectionnez **Lier un objet de stratégie de groupe existant**. Dans la boîte de dialogue qui s’affiche, sélectionnez l’objet نهج المجموعة que vous souhaitez lier. Cliquez sur **OK**.

Pour plus de paramètres de configuration, consultez [Configurer les exemples de paramètres de collecte](configure-endpoints-gp.md#configure-sample-collection-settings) et [autres paramètres de configuration recommandés](configure-endpoints-gp.md#other-recommended-configuration-settings).

### <a name="step-3-complete-the-onboarding-steps"></a>ÉTAPE 3 : Effectuer les étapes d’intégration

Les étapes suivantes s’appliquent uniquement si vous utilisez une solution anti-programme malveillant tierce. Vous devez appliquer le paramètre de mode passif de l’Antivirus Microsoft Defender suivant. Vérifiez qu’il a été correctement configuré :

1. Définissez l’entrée de Registre suivante :
    - Chemin: `HKLM\SOFTWARE\Policies\Microsoft\Windows Advanced Threat Protection`
    - Nom : `ForceDefenderPassiveMode`
    - Type: `REG_DWORD`
    - Valeur : `1`

   :::image type="content" source="images/atp-verify-passive-mode.png" alt-text="Résultat de la vérification en mode passif" lightbox="images/atp-verify-passive-mode.png":::

> [!IMPORTANT]
>
> - Le package d’intégration pour Windows Server 2012 R2, 2016, 2019 et 2022 via Microsoft Endpoint Manager est actuellement fourni en tant que script. Pour plus d’informations sur le déploiement de programmes et de scripts dans Configuration Manager, consultez [Packages et programmes dans Configuration Manager](/configmgr/apps/deploy-use/packages-and-programs).
> - Un script local convient à une preuve de concept, mais ne doit pas être utilisé pour le déploiement en production. Pour un déploiement de production, nous vous recommandons d’utiliser نهج المجموعة ou Configuration Manager de point de terminaison Microsoft.

## <a name="windows-server-semi-annual-enterprise-channel-sac-windows-server-2019-and-windows-server-2022"></a>Windows Server Semi-Annual Enterprise Channel (SAC), Windows Server 2019 et Windows Server 2022

### <a name="download-package"></a>Télécharger le package

1. Dans Microsoft 365 Defender, accédez à **Paramètres > 裝置管理 > Intégration**.

2. Sélectionnez **Windows Server 1803 et 2019**.

3. Sélectionnez **Télécharger le package**. Enregistrez-le en tant que WindowsDefenderATPOnboardingPackage.zip.

4. Suivez les étapes fournies dans la section [Terminer les étapes d’intégration](#step-3-complete-the-onboarding-steps) .

## <a name="verify-the-onboarding-and-installation"></a>Vérifier l’intégration et l’installation

Vérifiez que l’Antivirus Microsoft Defender et les Microsoft Defender pour point de terminaison sont en cours d’exécution.

## <a name="run-a-detection-test-to-verify-onboarding"></a>Exécuter un test de détection pour vérifier l’intégration

Après l’intégration de l’appareil, vous pouvez choisir d’exécuter un test de détection pour vérifier qu’un appareil est correctement intégré au service. Pour plus d’informations, consultez [Exécuter un test de détection sur un appareil Microsoft Defender pour point de terminaison nouvellement intégré](run-detection-test.md).

> [!NOTE]
> L’exécution de l’Antivirus Microsoft Defender n’est pas obligatoire, mais elle est recommandée. Si un autre produit du fournisseur d’antivirus est la solution principale de protection des points de terminaison, vous pouvez exécuter l’antivirus Defender en mode passif. Vous pouvez uniquement confirmer que le mode passif est activé après avoir vérifié que Microsoft Defender pour point de terminaison capteur (SENSE) est en cours d’exécution.

1. Exécutez la commande suivante pour vérifier que l’Antivirus Microsoft Defender est installé :

    > [!NOTE]
    > Cette étape de vérification n’est requise que si vous utilisez l’antivirus Microsoft Defender comme solution de logiciel anti-programme malveillant actif.

    ```DOS
    sc.exe query Windefend
    ```

    Si le résultat est « Le service spécifié n’existe pas en tant que service installé », vous devez installer l’antivirus Microsoft Defender.

    Pour plus d’informations sur l’utilisation de نهج المجموعة pour configurer et gérer l’antivirus Microsoft Defender sur vos serveurs Windows, consultez [Utiliser نهج المجموعة paramètres pour configurer et gérer l’antivirus Microsoft Defender](use-group-policy-microsoft-defender-antivirus.md).

2. Exécutez la commande suivante pour vérifier que Microsoft Defender pour point de terminaison est en cours d’exécution :

    ```DOS
    sc.exe query sense
    ```

    Le résultat doit indiquer qu’il est en cours d’exécution. Si vous rencontrez des problèmes d’intégration, consultez [Résolution des problèmes d’intégration](troubleshoot-onboarding.md).

## <a name="run-a-detection-test"></a>Exécuter un test de détection

Suivez les étapes décrites dans [Exécuter un test de détection sur un appareil nouvellement intégré](run-detection-test.md) pour vérifier que le serveur fait rapport à Defender pour le service point de terminaison.

## <a name="next-steps"></a>Prochaines étapes

Une fois les appareils intégrés au service, vous devez configurer les composants individuels de Microsoft Defender pour point de terminaison. Suivez [l’ordre d’adoption](prepare-deployment.md#adoption-order) pour être guidé sur l’activation des différents composants.

## <a name="offboard-windows-servers"></a>Désintégrage des serveurs Windows

Vous pouvez déconnecter Windows Server 2012 édition R2, Windows Server 2016, Windows Server (SAC), Windows Server 2019 et Windows Server 2019 Core dans la même méthode disponible pour Windows 10 appareils clients.

- [Désins border des appareils à l’aide de نهج المجموعة](configure-endpoints-gp.md#offboard-devices-using-group-policy)
- [Désins border des appareils à l’aide de Configuration Manager](configure-endpoints-sccm.md#offboard-devices-using-configuration-manager)
- [Désintégrage des appareils à l’aide des outils de 裝置管理 mobile](configure-endpoints-mdm.md#offboard-devices-using-mobile-device-management-tools)
- [Désintégrage des appareils à l’aide d’un script local](configure-endpoints-script.md#offboard-devices-using-a-local-script)

Après la désintégration, vous pouvez procéder à la désinstallation du package de solution unifié sur Windows Server 2012 R2 et Windows Server 2016.

Pour les autres versions de serveur Windows, vous avez deux options pour déconnecter les serveurs Windows du service :

- Désinstaller l’agent MMA
- Supprimer la configuration de l’espace de travail Defender pour point de terminaison

> [!NOTE]
> Ces instructions de désintégrage pour d’autres versions de serveur Windows s’appliquent également si vous exécutez les Microsoft Defender pour point de terminaison précédentes pour Windows Server 2016 et Windows Server 2012 R2 qui nécessite le MMA. Les instructions pour migrer vers la nouvelle solution unifiée se trouvent [dans les scénarios de migration de serveur dans Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/server-migration).

## <a name="related-topics"></a>Voir aussi

- [Intégrer des versions antérieures de Windows](onboard-downlevel.md)
- [Intégrer des appareils Windows 10](configure-endpoints.md)
- [Intégrer des appareils non Windows](configure-endpoints-non-windows.md)
- [Configurer les paramètres de proxy et de connectivité Internet](configure-proxy-internet.md)
- [Exécuter un test de détection sur un appareil Defender pour point de terminaison nouvellement intégré](run-detection-test.md)
- [Résolution des problèmes d’intégration Microsoft Defender pour point de terminaison](troubleshoot-onboarding.md)
