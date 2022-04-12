---
title: Déployer, gérer et créer des rapports sur Antivirus Microsoft Defender
description: Vous pouvez déployer et gérer des Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, stratégie de groupe, PowerShell ou WMI
keywords: déployer, gérer, mettre à jour, protéger Antivirus Microsoft Defender
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 10/18/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 4e0d249f7805c47be55ec42f3362ca1952c20ca3
ms.sourcegitcommit: 4f56b4b034267b28c7dd165e78ecfb4b5390087d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64788499"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Déployer, gérer et créer des rapports sur Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender 

**Plateformes**
- Windows

Vous pouvez déployer, gérer et créer des rapports sur Antivirus Microsoft Defender de plusieurs façons.

Étant donné que le client Antivirus Microsoft Defender est installé en tant que partie essentielle de Windows 10 et de Windows 11, le déploiement traditionnel d’un client sur vos points de terminaison ne s’applique pas.

Toutefois, dans la plupart des cas, vous devrez toujours activer le service de protection sur vos points de terminaison avec Microsoft Intune, Microsoft Endpoint Configuration Manager, Microsoft Defender pour le cloud ou stratégie de groupe  Objets, décrits dans le tableau suivant.

Vous verrez également des liens supplémentaires pour :

- Gestion de la protection Antivirus Microsoft Defender, notamment la gestion des mises à jour des produits et de la protection
- Création de rapports sur la protection Antivirus Microsoft Defender

> [!IMPORTANT]
> Dans la plupart des cas, Windows 10 ou Windows 11 désactivera Antivirus Microsoft Defender s’il trouve un autre produit antivirus en cours d’exécution et à jour. Vous devez désactiver ou désinstaller des produits antivirus tiers avant que Antivirus Microsoft Defender ne fonctionne. Si vous réactivez ou installez des produits antivirus tiers, Windows 10 ou Windows 11 désactive automatiquement Antivirus Microsoft Defender.

Outil|Options de déploiement (<a href="#fn2" id="ref2">2</a>)|Options de gestion (configuration à l’échelle du réseau et déploiement de stratégie ou de base de référence) ([3](#fn3))|Options de création de rapports
---|---|---|---
Microsoft Intune|[Ajouter des paramètres endpoint protection dans Intune](/intune/endpoint-protection-configure)|[Configurer les paramètres de restriction d’appareil dans Intune](/intune/device-restrictions-configure)| [Utiliser la console Intune pour gérer les appareils](/intune/device-management)
Microsoft Endpoint Manager ([1](#fn1))|Utiliser le [rôle de système de site de point Endpoint Protection][] et [activer Endpoint Protection avec les paramètres client personnalisés][]|Avec [stratégies anti-programme malveillant par défaut et personnalisées][] et [gestion des clients][]|Avec les [Configuration Manager espace de travail de surveillance][] et [alertes par e-mail][]
stratégie de groupe et Active Directory (joints à un domaine)|Utilisez un objet stratégie de groupe pour déployer des modifications de configuration et vérifier que Antivirus Microsoft Defender est activé.|Utiliser stratégie de groupe Objects (GPO) pour [Configurer les options de mise à jour pour Antivirus Microsoft Defender][] et [Configurer les fonctionnalités Windows Defender][]|La création de rapports sur les points de terminaison n’est pas disponible avec stratégie de groupe. Vous pouvez générer une liste de [Stratégies de groupe pour déterminer si des paramètres ou des stratégies ne sont pas appliqués][]
PowerShell|Déployez avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez les applets de commande [Set-MpPreference] et [Update-MpSignature] disponibles dans le module Defender.|Utiliser les [applets de commande Get- disponibles dans le module Defender][]
Windows Infrastructure de gestion|Déployez avec stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utiliser la [méthode Set de la classe MSFT_MpPreference][] et la [méthode Update de la classe MSFT_MpSignature][]|Utiliser la classe [MSFT_MpComputerStatus][] et la méthode get des classes associées dans le [Windows Defender fournisseur WMIv2][]
Microsoft Azure|Déployez Microsoft Antimalware pour Azure dans le [Portail Azure, à l’aide de Visual Studio configuration de machine virtuelle ou d’applets de commande Azure PowerShell](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios). Vous pouvez également [installer Endpoint Protection dans Microsoft Defender pour le cloud*](/azure/security-center/security-center-install-endpoint-protection)|Configurer [Microsoft Antimalware pour Machines Virtuelles et Services cloud avec des applets de commande Azure PowerShell](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) ou [utiliser des exemples de code](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Utilisez [Microsoft Antimalware pour Machines Virtuelles et Services cloud avec Azure PowerShell applets](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) de commande pour activer la surveillance. Vous pouvez également consulter les rapports d’utilisation dans Azure Active Directory pour déterminer l’activité suspecte, y compris le rapport [Éventuellement des appareils infectés][] et configurer un outil SIEM pour signaler les [événements Antivirus Microsoft Defender][] et ajouter cet outil en tant qu’application dans AAD.

1. <span id="fn1" />La disponibilité de certaines fonctions et fonctionnalités, en particulier liées à la protection fournie par le cloud, diffère entre Microsoft Endpoint Manager (Current Branch) et System Center Configuration Manager 2012. Dans cette bibliothèque, nous nous sommes concentrés sur Windows 10, Windows 11, Windows Server 2016 et Microsoft Endpoint Manager (Current Branch). Consultez [Utiliser la protection fournie par le cloud Microsoft dans Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) pour obtenir un tableau qui décrit les principales différences. [(Revenir à la table)](#ref2)

2. <span id="fn2" />Dans Windows 10 et Windows 11, Antivirus Microsoft Defender est un composant disponible sans installation ni déploiement d’un client ou d’un service supplémentaire. Il est automatiquement activé lorsque les produits antivirus tiers sont désinstallés ou obsolètes (sauf sur Windows Server 2016). Le déploiement traditionnel n’est donc pas nécessaire. Le déploiement ici fait référence à la garantie que le composant Antivirus Microsoft Defender est disponible et activé sur les points de terminaison ou les serveurs. [(Revenir à la table)](#ref2)

3. <span id="fn3" />La configuration des fonctionnalités et de la protection, notamment la configuration des mises à jour de produit et de protection, sont décrites plus en détail dans la section [Configurer les fonctionnalités Antivirus Microsoft Defender](configure-notifications-microsoft-defender-antivirus.md) de cette bibliothèque. [(Revenir à la table)](#ref2)

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Déployer et activer Antivirus Microsoft Defender protection](deploy-microsoft-defender-antivirus.md) | Bien que le client soit installé en tant que partie principale de Windows 10 ou Windows 11, et que le déploiement traditionnel ne s’applique pas, vous devez toujours activer le client sur vos points de terminaison avec Microsoft Endpoint Configuration Manager, Microsoft Intune ou objets stratégie de groupe.
[Gérer les mises à jour Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md) | Il existe deux parties à mettre à jour Antivirus Microsoft Defender : la mise à jour du client sur les points de terminaison (mises à jour du produit) et la mise à jour du renseignement de sécurité (mises à jour de protection). Vous pouvez mettre à jour le renseignement de sécurité de plusieurs façons, à l’aide de Microsoft Endpoint Configuration Manager, stratégie de groupe, PowerShell et WMI.
[Surveiller et signaler la protection Antivirus Microsoft Defender](report-monitor-microsoft-defender-antivirus.md) | Vous pouvez utiliser Microsoft Intune, Microsoft Endpoint Configuration Manager, le complément Update Compliance pour Microsoft Operations Management Suite ou un produit SIEM tiers (en consommant Windows journaux des événements) pour surveiller l’état de la protection et créer des rapports sur la protection des points de terminaison.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison sur les fonctionnalités Android](android-configure.md)
> - [Configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)
    
