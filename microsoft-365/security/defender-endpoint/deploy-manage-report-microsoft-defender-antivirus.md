---
title: Déployer, gérer et signaler l’antivirus Microsoft Defender
description: Vous pouvez déployer et gérer l’antivirus Microsoft Defender avec Intune, microsoft endpoint Configuration Manager, stratégie de groupe, PowerShell ou WMI
keywords: déployer, gérer, mettre à jour, protection, Antivirus Microsoft Defender
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.date: 09/02/2022
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.collection:
- M365-security-compliance
search.appverid: met150
ms.openlocfilehash: c3ecff1463232ceb4ecc3dccb98843a1230144cf
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67701299"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Déployer, gérer et signaler l’antivirus Microsoft Defender

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**

- Windows

Vous pouvez déployer, gérer et signaler l’antivirus Microsoft Defender de plusieurs façons.

Étant donné que le client antivirus Microsoft Defender est installé en tant que partie essentielle de Windows 10 et de Windows 11, le déploiement traditionnel d’un client sur vos points de terminaison ne s’applique pas.

Toutefois, dans la plupart des cas, vous devez toujours activer le service de protection sur vos points de terminaison avec Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Defender pour cloud ou stratégie de groupe Objects, qui est décrit dans le tableau suivant.

Vous verrez également d’autres liens pour :

- Gestion de la protection antivirus Microsoft Defender, y compris la gestion des mises à jour des produits et de la protection
- Création de rapports sur la protection antivirus Microsoft Defender

> [!IMPORTANT]
> Dans la plupart des cas, Windows 10 ou Windows 11 désactive l’antivirus Microsoft Defender s’il trouve un autre produit antivirus en cours d’exécution et à jour. Vous devez désactiver ou désinstaller des produits antivirus tiers pour que l’antivirus Microsoft Defender fonctionne. Si vous réactivez ou installez des produits antivirus tiers, Windows 10 ou Windows 11 désactive automatiquement l’Antivirus Microsoft Defender.

| Outil|Options de déploiement (<a href="#fn2" id="ref2">2</a>)|Options de gestion (configuration à l’échelle du réseau et déploiement de stratégie ou de base de référence) ([3](#fn3))|Options de création de rapports |
---|---|---|---
| Microsoft Intune|[Ajouter des paramètres endpoint protection dans Intune](/intune/endpoint-protection-configure)|[Configurer les paramètres de restriction d’appareil dans Intune](/intune/device-restrictions-configure)| [Utiliser la console Intune pour gérer les appareils](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|Utilisez le [rôle de système de site de point Endpoint Protection](/mem/configmgr/protect/deploy-use/endpoint-protection-site-role) et [activez Endpoint Protection avec des paramètres client personnalisés](/mem/configmgr/protect/deploy-use/endpoint-protection-configure-client).|Avec les stratégies [anti-programme malveillant par défaut et personnalisées](/microsoft-365/security/office-365-security/configure-anti-malware-policies) et la gestion des clients.|Avec les [alertes par défaut Configuration Manager surveillance de l’espace de travail](/mem/configmgr/apps/deploy-use/monitor-applications-from-the-console) et des e-mails. |
| stratégie de groupe et Active Directory (joints à un domaine)|Utilisez un objet stratégie de groupe pour déployer des modifications de configuration et vérifier que l’antivirus Microsoft Defender est activé.|Utilisez stratégie de groupe Objects (GPO) pour [configurer les options de mise à jour de l’Antivirus Microsoft Defender](/microsoft-365/security/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus) et [configurer Windows Defender fonctionnalités](/microsoft-365/security/defender-endpoint/configure-microsoft-defender-antivirus-features).|La création de rapports sur les points de terminaison n’est pas disponible avec stratégie de groupe. Vous pouvez générer une liste de stratégies de groupe pour déterminer si des paramètres ou des stratégies ne sont pas appliqués. |
| PowerShell|Déployez avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez les applets [de commande Set-MpPreference](/powershell/module/defender/set-mppreference) et [Update-MpSignature](/powershell/module/defender/update-mpsignature) disponibles dans le module Defender.|Utilisez les [applets de commande Get appropriées disponibles dans le module Defender](/powershell/module/defender). |
| Windows Infrastructure de gestion|Déployez avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez la [méthode Set de la classe MSFT_MpPreference](/previous-versions/windows/desktop/defender/set-msft-mppreference) et la [méthode Update de la classe MSFT_MpSignature](/previous-versions/windows/desktop/defender/update-msft-mpsignature).|Utilisez la classe [MSFT_MpComputerStatus](/previous-versions/windows/desktop/defender/msft-mpcomputerstatus) et la méthode get des classes associées dans le [fournisseur WMIv2 Windows Defender](/windows/win32/wmisdk/wmi-providers). |
| Microsoft Azure|Déployez Microsoft Antimalware pour Azure dans le [Portail Azure, à l’aide de la configuration de machine virtuelle Visual Studio ou à l’aide d’applets de commande Azure PowerShell](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). Vous pouvez également [installer Endpoint Protection dans Microsoft Defender pour cloud](/azure/defender-for-cloud/endpoint-protection-recommendations-technical).|Configurez [Microsoft Antimalware pour Machines Virtuelles et Services cloud avec Azure PowerShell applets de commande](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) ou [utilisez des exemples de code](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe).|Utilisez [Microsoft Antimalware pour Machines Virtuelles et Services cloud avec Azure PowerShell applets](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) de commande pour activer la surveillance. Vous pouvez également consulter les rapports d’utilisation dans Azure Active Directory pour déterminer les activités suspectes, notamment le rapport sur les appareils potentiellement infectés, et configurer un outil SIEM pour signaler [les journaux des événements et les codes d’erreur dans l’Antivirus Microsoft Defender](troubleshoot-microsoft-defender-antivirus.md) et ajouter cet outil en tant qu’application dans Azure AD. |

1. <span id="fn1" />La disponibilité de certaines fonctions et fonctionnalités, en particulier liées à la protection fournie par le cloud, diffère entre Microsoft Endpoint Manager (Current Branch) et System Center 2012 Configuration Manager. Dans cette bibliothèque, nous nous sommes concentrés sur Windows 10, Windows 11, Windows Server 2016 et Microsoft Endpoint Manager (Current Branch). Consultez [Utiliser la protection fournie par le cloud Microsoft dans l’Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) pour obtenir un tableau qui décrit les principales différences. [(Revenir à la table)](#ref2)

2. <span id="fn2" />Dans Windows 10 et Windows 11, l’antivirus Microsoft Defender est un composant disponible sans installation ni déploiement d’un autre client ou service. Il est automatiquement activé lorsque les produits antivirus tiers sont désinstallés ou obsolètes (sauf sur Windows Server 2016). Par conséquent, le déploiement traditionnel n’est pas nécessaire. Le déploiement ici fait référence à la garantie que le composant antivirus Microsoft Defender est disponible et activé sur les points de terminaison ou les serveurs. [(Revenir à la table)](#ref2)

3. <span id="fn3" />La configuration des fonctionnalités et de la protection, notamment la configuration des mises à jour de produit et de protection, sont décrites plus en détail dans la section [Configurer les fonctionnalités de l’Antivirus Microsoft Defender](configure-notifications-microsoft-defender-antivirus.md) dans cette bibliothèque. [(Revenir à la table)](#ref2)

## <a name="in-this-section"></a>Contenu de cette section

Article | Description
---|---
[Déployer et activer la protection antivirus Microsoft Defender](deploy-microsoft-defender-antivirus.md) | Bien que le client soit installé en tant que partie principale de Windows 10 ou Windows 11, et que le déploiement traditionnel ne s’applique pas, vous devez toujours activer le client sur vos points de terminaison avec Microsoft Endpoint Configuration Manager, Microsoft Intune ou objets stratégie de groupe.
[Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md) | La mise à jour de l’Antivirus Microsoft Defender comprend deux parties : la mise à jour du client sur les points de terminaison (mises à jour du produit) et la mise à jour du renseignement de sécurité (mises à jour de protection). Vous pouvez mettre à jour security intelligence de plusieurs façons, à l’aide de Microsoft Endpoint Configuration Manager, stratégie de groupe, PowerShell et WMI.
[Surveiller et signaler la protection antivirus Microsoft Defender](report-monitor-microsoft-defender-antivirus.md) | Vous pouvez utiliser Microsoft Intune, Microsoft Endpoint Configuration Manager, le complément Update Compliance pour Microsoft Operations Management Suite ou un produit SIEM tiers (en consommant des journaux des événements Windows) pour surveiller l’état de la protection et créer des rapports sur la protection des points de terminaison.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
    
