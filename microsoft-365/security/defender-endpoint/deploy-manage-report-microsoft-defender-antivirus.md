---
title: Déployer, gérer et signaler l'Antivirus Microsoft Defender
description: Vous pouvez déployer et gérer l'Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, la stratégie de groupe, PowerShell ou WMI
keywords: déployer, gérer, mettre à jour, protection, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: a9cd04300e67f956b50f07c02f3dc00c515f02eb
ms.sourcegitcommit: 3fe7eb32c8d6e01e190b2b782827fbadd73a18e6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/13/2021
ms.locfileid: "51690734"
---
# <a name="deploy-manage-and-report-on-microsoft-defender-antivirus"></a>Déployer, gérer et signaler l'Antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Vous pouvez déployer, gérer et signaler l'Antivirus Microsoft Defender de plusieurs façons.

Étant donné que le client Antivirus Microsoft Defender est installé en tant que partie intégrante de Windows 10, le déploiement traditionnel d'un client sur vos points de terminaison ne s'applique pas.

Toutefois, dans la plupart des cas, vous devrez toujours activer le service de protection sur vos points de terminaison avec Microsoft Intune, Microsoft Endpoint Configuration Manager, Azure Defender ou les objets de stratégie de groupe, qui est décrit dans le tableau suivant.

Vous verrez également des liens supplémentaires pour :

- Gestion de la protection antivirus Microsoft Defender, y compris la gestion des mises à jour du produit et de la protection
- Rapports sur la protection antivirus Microsoft Defender

> [!IMPORTANT]
> Dans la plupart des cas, Windows 10 désactive l'Antivirus Microsoft Defender s'il trouve un autre produit antivirus en cours d'exécution et à jour. Vous devez désactiver ou désinstaller des produits antivirus tiers pour que l'Antivirus Microsoft Defender fonctionne. Si vous réactivez ou installez des produits antivirus tiers, Windows 10 désactive automatiquement l'Antivirus Microsoft Defender.

Outil|Options de déploiement (<a href="#fn2" id="ref2">2</a>)|Options de gestion (configuration et stratégie à l'échelle du réseau ou déploiement de base) ([3](#fn3))|Options de rapport  
---|---|---|---  
Microsoft Intune|[Ajouter des paramètres de protection des points de terminaison dans Intune](/intune/endpoint-protection-configure)|[Configurer les paramètres de restriction d'appareil dans Intune](/intune/device-restrictions-configure)| [Utiliser la console Intune pour gérer les appareils](/intune/device-management)  
Microsoft Endpoint Manager ([1](#fn1))|Utiliser le [rôle système de site point Endpoint Protection][] et activer [Endpoint Protection avec des paramètres client personnalisés][]|Avec des stratégies de logiciel [anti-programme malveillant][] par défaut et personnalisées et la [gestion des clients][]|Avec l'espace de [travail Configuration Manager Monitoring par][] défaut et les [alertes par courrier électronique][]  
Stratégie de groupe et Active Directory (joint au domaine)|Utilisez un objet de stratégie de groupe pour déployer les modifications de configuration et vérifier que l'Antivirus Microsoft Defender est activé.|Utiliser les objets de stratégie de groupe (G OBJETS) pour configurer les options de mise à jour de [l'Antivirus Microsoft Defender][] et configurer Windows Defender [fonctionnalités][]|Les rapports de point de terminaison ne sont pas disponibles avec la stratégie de groupe. Vous pouvez générer une liste de stratégies de groupe pour déterminer si des [paramètres ou des stratégies ne sont pas appliqués.][]
PowerShell|Déployer avec une stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez les cmdlets [Set-MpPreference] et [Update-MpSignature] disponibles dans le module Defender.|Utiliser les [cmdlets Get- appropriées disponibles dans le module Defender][]
Windows Infrastructure de gestion|Déployer avec une stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utiliser la [méthode Set de la classe MSFT_MpPreference et][] la méthode Update de la MSFT_MpSignature [classe][]|Utiliser la [MSFT_MpComputerStatus][] et la méthode get des classes associées dans le [Windows Defender WMIv2 Provider][]
Microsoft Azure|Déployez Microsoft Antimalware pour Azure dans le portail Azure, en utilisant Visual Studio configuration de machine virtuelle ou à l'aide [d'cmdlets Azure PowerShell.](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios) Vous pouvez également [installer endpoint protection dans Azure Defender*](/azure/security-center/security-center-install-endpoint-protection)|Configurer le logiciel anti-programme malveillant Microsoft pour les machines virtuelles et les [services cloud avec les cmdlets Azure PowerShell](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) ou utiliser des [exemples de code](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Utilisez [le logiciel anti-programme malveillant Microsoft pour les machines virtuelles](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) et les services cloud avec les cmdlets Azure PowerShell pour activer la surveillance. Vous pouvez également consulter les rapports d'utilisation dans [][] Azure Active Directory pour déterminer une activité suspecte, y compris le rapport des appareils potentiellement infectés, et configurer un outil SIEM pour signaler les événements de l'Antivirus [Microsoft Defender][] et ajouter cet outil en tant qu'application dans AAD.

1. <span id="fn1" />La disponibilité de certaines fonctions et fonctionnalités, en particulier liées à la protection cloud, diffère entre Microsoft Endpoint Manager (Current Branch) et System Center 2012 Configuration Manager. Dans cette bibliothèque, nous nous sommes concentrés sur Windows 10, Windows Server 2016 et Microsoft Endpoint Manager (Current Branch). Voir Utiliser la protection microsoft fournie par le [cloud dans l'Antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md) pour obtenir un tableau qui décrit les principales différences. [(Revenir au tableau)](#ref2)
  
2.  <span id="fn2" />Dans Windows 10, l'Antivirus Microsoft Defender est un composant disponible sans installation ni déploiement d'un client ou d'un service supplémentaire. Il est automatiquement activé lorsque des produits antivirus tiers sont désinstallés ou désinstallés (sauf sur[Windows Server 2016).](microsoft-defender-antivirus-on-windows-server.md) Le déploiement classique n'est donc pas requis. Le déploiement ici fait référence à la garantie que le composant Antivirus Microsoft Defender est disponible et activé sur les points de terminaison ou les serveurs. [(Revenir au tableau)](#ref2)

3. <span id="fn3" />La configuration des fonctionnalités et de la protection, y compris la configuration des mises à jour du produit et de la protection, est décrite plus en détail dans la section Configurer les fonctionnalités de [l'Antivirus Microsoft Defender](configure-notifications-microsoft-defender-antivirus.md) dans cette bibliothèque. [(Revenir au tableau)](#ref2)

[Rôle système de site point Endpoint Protection]: /configmgr/protect/deploy-use/endpoint-protection-site-role
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
[Méthode Set de la classe MSFT_MpPreference classe]:  /previous-versions/windows/desktop/defender/set-msft-mppreference
[Méthode update de la classe MSFT_MpSignature de mise à jour]:  /previous-versions/windows/desktop/defender/set-msft-mppreference
[MSFT_MpComputerStatus]:  /previous-versions/windows/desktop/defender/msft-mpcomputerstatus
[Windows Defender fournisseur WMIv2]: /previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal
[Set-MpPreference]:  https://technet.microsoft.com/itpro/powershell/windows/defender/set-mppreference.md
[Update-MpSignature]: /powershell/module/defender/update-mpsignature
[Get- cmdlets disponibles dans le module Defender]: /powershell/module/defender/
[Configurer les options de mise à jour de l'Antivirus Microsoft Defender]: manage-updates-baselines-microsoft-defender-antivirus.md
[Configurer les fonctionnalités Windows Defender de sécurité]: configure-microsoft-defender-antivirus-features.md
[Stratégies de groupe pour déterminer si des paramètres ou des stratégies ne sont pas appliqués]: /previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc771389(v=ws.11)
[Appareils potentiellement infectés]: /azure/active-directory/active-directory-reporting-sign-ins-from-possibly-infected-devices
[Événements de l'Antivirus Microsoft Defender]: troubleshoot-microsoft-defender-antivirus.md

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Déployer et activer la protection antivirus Microsoft Defender](deploy-microsoft-defender-antivirus.md) | Bien que le client soit installé en tant que partie intégrante de Windows 10 et que le déploiement classique ne s'applique pas, vous devrez quand même activer le client sur vos points de terminaison avec Microsoft Endpoint Configuration Manager, Microsoft Intune ou les objets de stratégie de groupe. 
[Gérer les mises à jour de l'Antivirus Microsoft Defender et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md) | La mise à jour de l'Antivirus Microsoft Defender se fait en deux parties : la mise à jour du client sur les points de terminaison (mises à jour du produit) et la mise à jour de l'intelligence de sécurité (mises à jour de la protection). Vous pouvez mettre à jour les informations de sécurité de différentes manières, à l'aide de Microsoft Endpoint Configuration Manager, d'une stratégie de groupe, de PowerShell et de WMI.
[Surveiller et signaler la protection antivirus Microsoft Defender](report-monitor-microsoft-defender-antivirus.md) | Vous pouvez utiliser Microsoft Intune, Microsoft Endpoint Configuration Manager, le module de conformité des mises à jour pour Microsoft Operations Management Suite ou un produit SIEM tiers (en consommant des journaux d'événements Windows) pour surveiller l'état de la protection et créer des rapports sur la protection des points de terminaison.