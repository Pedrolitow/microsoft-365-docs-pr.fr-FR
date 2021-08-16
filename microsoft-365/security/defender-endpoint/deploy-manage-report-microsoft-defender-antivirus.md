---
title: Déployer, gérer et signaler les Antivirus Microsoft Defender
description: Vous pouvez déployer et gérer Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, stratégie de groupe, PowerShell ou WMI
keywords: déployer, gérer, mettre à jour, protection, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: normal
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 57f6f836948f377ad92234298c9935e80f27b2fc03f1e6d3f7f872e1107bf395
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53863666"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Déployer, gérer et signaler les Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez déployer, gérer et signaler des Antivirus Microsoft Defender de plusieurs façons.

Étant donné que Antivirus Microsoft Defender client est installé en tant que partie intégrante de Windows 10, le déploiement traditionnel d’un client sur vos points de terminaison ne s’applique pas.

Toutefois, dans la plupart des cas, vous devrez toujours activer le service de protection sur vos points de terminaison avec les objets de stratégie de groupe, Microsoft Intune, Microsoft Endpoint Configuration Manager ou Azure Defender, décrits dans le tableau suivant.

Vous verrez également des liens supplémentaires pour :

- Gestion Antivirus Microsoft Defender protection des données, y compris la gestion des mises à jour du produit et de la protection
- Reporting on Antivirus Microsoft Defender protection

> [!IMPORTANT]
> Dans la plupart des cas, Windows 10 désactive Antivirus Microsoft Defender s’il trouve un autre produit antivirus en cours d’exécution et à jour. Vous devez désactiver ou désinstaller des produits antivirus tiers pour que Antivirus Microsoft Defender fonctionne. Si vous réactivez ou installez des produits antivirus tiers, Windows 10 désactive automatiquement Antivirus Microsoft Defender.

Outil|Options de déploiement (<a href="#fn2" id="ref2">2</a>)|Options de gestion (configuration et stratégie à l’échelle du réseau ou déploiement de référence) ([3](#fn3))|Options de rapport  
---|---|---|---  
Microsoft Intune|[Ajouter des paramètres de protection des points de terminaison dans Intune](/intune/endpoint-protection-configure)|[Configurer les paramètres de restriction d’appareil dans Intune](/intune/device-restrictions-configure)| [Utiliser la console Intune pour gérer les appareils](/intune/device-management)  
Microsoft Endpoint Manager ([1](#fn1))|Utiliser le [rôle Endpoint Protection de site point][] et activer Endpoint Protection avec les [paramètres client personnalisés][]|Avec des stratégies de logiciel [anti-programme malveillant][] par défaut et personnalisées et la [gestion des clients][]|Avec l’espace de [travail Configuration Manager Monitoring par][] défaut et les [alertes par courrier électronique][]  
Stratégie de groupe et Active Directory (joint au domaine)|Utilisez un objet de stratégie de groupe pour déployer les modifications de configuration et Antivirus Microsoft Defender est activé.|Utiliser les objets de stratégie de groupe (G OBJETS) pour configurer les [options][] de mise à jour Antivirus Microsoft Defender et configurer [les Windows Defender de groupe][]|Les rapports de point de terminaison ne sont pas disponibles avec la stratégie de groupe. Vous pouvez générer une liste de stratégies de groupe pour déterminer si des [paramètres ou des stratégies ne sont pas appliqués.][]
PowerShell|Déployer avec une stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez les cmdlets [Set-MpPreference] et [Update-MpSignature] disponibles dans le module Defender.|Utiliser les [cmdlets Get- appropriées disponibles dans le module Defender][]
Windows Infrastructure de gestion|Déployer avec une stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utiliser la [méthode Set de la classe MSFT_MpPreference et][] la méthode Update de la MSFT_MpSignature [classe][]|Utiliser la [MSFT_MpComputerStatus][] et la méthode get des classes associées dans le [Windows Defender WMIv2 Provider][]
Microsoft Azure|Déployez Microsoft Antimalware azure dans le portail Azure, en utilisant Visual Studio configuration de machine virtuelle ou à l’Azure PowerShell [cmdlets.](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios) Vous pouvez également [installer endpoint protection dans Azure Defender*](/azure/security-center/security-center-install-endpoint-protection)|Configurer des Microsoft Antimalware pour les machines virtuelles et les services cloud avec [Azure PowerShell cmdlets ou](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) utiliser [des exemples de code](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Utilisez Microsoft Antimalware pour les machines virtuelles et les services cloud avec [Azure PowerShell cmdlets](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) pour activer la surveillance. Vous pouvez également consulter les rapports d’utilisation dans [][] Azure Active Directory pour déterminer les activités suspectes, notamment le rapport sur les appareils potentiellement infectés et configurer un outil SIEM pour signaler les événements [Antivirus Microsoft Defender][] et ajouter cet outil en tant qu’application dans AAD.

1. <span id="fn1" />La disponibilité de certaines fonctions et fonctionnalités, en particulier liées à la protection cloud, diffère entre Microsoft Endpoint Manager (Current Branch) et System Center 2012 Configuration Manager. Dans cette bibliothèque, nous nous sommes concentrés sur Windows 10, Windows Server 2016 et Microsoft Endpoint Manager (Current Branch). Voir [Utiliser la protection microsoft fournie](cloud-protection-microsoft-defender-antivirus.md) par le cloud Antivirus Microsoft Defender pour un tableau qui décrit les principales différences. [(Revenir au tableau)](#ref2)
  
2. <span id="fn2" />Dans Windows 10, Antivirus Microsoft Defender est un composant disponible sans installation ou déploiement d’un client ou d’un service supplémentaire. Il est automatiquement activé lorsque des produits antivirus tiers sont désinstallés ou désinstallés (sauf[sur Windows Server 2016](microsoft-defender-antivirus-on-windows-server.md)). Le déploiement classique n’est donc pas requis. Le déploiement ici fait référence à la garantie que le Antivirus Microsoft Defender est disponible et activé sur les points de terminaison ou les serveurs. [(Revenir au tableau)](#ref2)

3. <span id="fn3" />La configuration des fonctionnalités et de la protection, y compris la configuration des mises à jour du produit et de la protection, est décrite plus en détail dans la section Configurer [Antivirus Microsoft Defender fonctionnalités](configure-notifications-microsoft-defender-antivirus.md) de cette bibliothèque. [(Revenir au tableau)](#ref2)

[Endpoint Protection système de site de point]: /configmgr/protect/deploy-use/endpoint-protection-site-role
[stratégies de logiciel anti-programme malveillant par défaut et personnalisées]:  /configmgr/protect/deploy-use/endpoint-antimalware-policies
[gestion des clients]:  /configmgr/core/clients/manage/manage-clients
[activer Endpoint Protection avec les paramètres client personnalisés]:  /configmgr/protect/deploy-use/endpoint-protection-configure-client
[Espace de travail Surveillance de Configuration Manager]:  /configmgr/protect/deploy-use/monitor-endpoint-protection
[alertes par courrier électronique]:  /configmgr/protect/deploy-use/endpoint-configure-alerts
[Deploy the Microsoft Intune client to endpoints]: /intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune
[custom Intune policy]:  /intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune#configure-microsoft-intune-endpoint-protection
 [custom Intune policy]:  /intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune#configure-microsoft-intune-endpoint-protection 
[manage tasks]: /intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune#choose-management-tasks-for-endpoint-protection
[Monitor endpoint protection in the Microsoft Intune administration console]: /intune/deploy-use/help-secure-windows-pcs-with-endpoint-protection-for-microsoft-intune#monitor-endpoint-protection
[Définir la méthode de la classe MSFT_MpPreference classe]:  /previous-versions/windows/desktop/defender/set-msft-mppreference
[Méthode Update de la classe MSFT_MpSignature de mise à jour]:  /previous-versions/windows/desktop/defender/set-msft-mppreference
[MSFT_MpComputerStatus]:  /previous-versions/windows/desktop/defender/msft-mpcomputerstatus
[Windows Defender Fournisseur WMIv2]: /previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal
[Set-MpPreference]:  https://technet.microsoft.com/itpro/powershell/windows/defender/set-mppreference.md
[Update-MpSignature]: /powershell/module/defender/update-mpsignature
[Get- cmdlets disponibles dans le module Defender]: /powershell/module/defender/
[Configurer les options de mise à jour pour Antivirus Microsoft Defender]: manage-updates-baselines-microsoft-defender-antivirus.md
[Configurer les fonctionnalités Windows Defender de sécurité]: configure-microsoft-defender-antivirus-features.md
[Stratégies de groupe pour déterminer si des paramètres ou des stratégies ne sont pas appliqués]: /previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771389(v=ws.11)
[Appareils potentiellement infectés]: /azure/active-directory/active-directory-reporting-sign-ins-from-possibly-infected-devices
[Antivirus Microsoft Defender événements]: troubleshoot-microsoft-defender-antivirus.md

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Déployer et activer la protection Antivirus Microsoft Defender de sécurité](deploy-microsoft-defender-antivirus.md) | Bien que le client soit installé en tant que partie intégrante de Windows 10 et que le déploiement classique ne s’applique pas, vous devrez quand même activer le client sur vos points de terminaison avec des objets de stratégie de groupe, Microsoft Endpoint Configuration Manager Microsoft Intune ou Microsoft Endpoint Configuration Manager. 
[Gérer les mises Antivirus Microsoft Defender jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md) | La mise à jour des Antivirus Microsoft Defender se fait en deux parties : la mise à jour du client sur les points de terminaison (mises à jour des produits) et la mise à jour de l’intelligence de sécurité (mises à jour de la protection). Vous pouvez mettre à jour les informations de sécurité de plusieurs façons, à l’aide de Microsoft Endpoint Configuration Manager, d’une stratégie de groupe, de PowerShell et de WMI.
[Surveiller et signaler la protection Antivirus Microsoft Defender données](report-monitor-microsoft-defender-antivirus.md) | Vous pouvez utiliser Microsoft Intune, Microsoft Endpoint Configuration Manager, le module de conformité des mises à jour pour Microsoft Operations Management Suite ou un produit SIEM tiers (en consommant des journaux d’événements Windows) pour surveiller l’état de la protection et créer des rapports sur la protection des points de terminaison.