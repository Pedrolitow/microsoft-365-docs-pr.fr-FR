---
title: Déployer, gérer et signaler les Antivirus Microsoft Defender
description: Vous pouvez déployer et gérer Antivirus Microsoft Defender avec Intune, Microsoft Endpoint Configuration Manager, stratégie de groupe, PowerShell ou WMI
keywords: déployer, gérer, mettre à jour, protection, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.collection: M365-security-compliance
ms.openlocfilehash: 9a71a641940be6b3acd3fbf6070ec907299c15ba
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60209972"
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
Microsoft Endpoint Manager ([1](#fn1))|Utiliser le rôle [Endpoint Protection de site point][] et [activer Endpoint Protection avec les paramètres client personnalisés][]|Avec [stratégies anti-programme malveillant par défaut et personnalisées][] et [gestion des clients][]|Avec les valeurs par défaut [Espace de travail Surveillance de Configuration Manager][] et [alertes par courrier électronique][]
Stratégie de groupe et Active Directory (joint au domaine)|Utilisez un objet de stratégie de groupe pour déployer les modifications de configuration et Antivirus Microsoft Defender est activé.|Utiliser des objets de stratégie de groupe pour [Configurer les options de mise à jour pour Antivirus Microsoft Defender][] et [Configurer les fonctionnalités Windows Defender][]|Les rapports de point de terminaison ne sont pas disponibles avec la stratégie de groupe. Vous pouvez générer une liste de [stratégies de groupe pour déterminer si des paramètres ou des stratégies ne sont pas appliqués][]
PowerShell|Déployer avec une stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez les cmdlets [Set-MpPreference] et [Update-MpSignature] disponibles dans le module Defender.|Utiliser les cmdlets [Get- disponibles dans le module Defender][]
Windows Infrastructure de gestion|Déployer avec une stratégie de groupe, Microsoft Endpoint Configuration Manager ou manuellement sur des points de terminaison individuels.|Utilisez la méthode [Set de la classe MSFT_MpPreference][] et la méthode [Update de la classe MSFT_MpSignature][]|Utilisez la classe [MSFT_MpComputerStatus][] et la méthode get des classes associées dans le [Windows Defender fournisseur WMIv2][]
Microsoft Azure|Déployez Microsoft Antimalware azure dans le portail Azure, en utilisant Visual Studio configuration de machine virtuelle ou à l’Azure PowerShell [cmdlets.](/azure/security/azure-security-antimalware#antimalware-deployment-scenarios) Vous pouvez également [installer endpoint protection dans Azure Defender*](/azure/security-center/security-center-install-endpoint-protection)|Configurer des Microsoft Antimalware pour les machines virtuelles et les services cloud avec [Azure PowerShell cmdlets ou](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) utiliser [des exemples de code](https://gallery.technet.microsoft.com/Antimalware-For-Azure-5ce70efe)|Utilisez Microsoft Antimalware pour les machines virtuelles et les services cloud avec [Azure PowerShell cmdlets](/azure/security/azure-security-antimalware#enable-and-configure-antimalware-using-powershell-cmdlets) pour activer la surveillance. Vous pouvez également consulter les rapports d’utilisation dans Azure Active Directory pour déterminer une activité suspecte, notamment le rapport [Appareils potentiellement infectés][] et configurer un outil SIEM pour signaler [événements Antivirus Microsoft Defender][] et ajouter cet outil en tant qu’application dans AAD.

1. <span id="fn1" />La disponibilité de certaines fonctions et fonctionnalités, en particulier liées à la protection cloud, diffère entre Microsoft Endpoint Manager (Current Branch) et System Center 2012 Configuration Manager. Dans cette bibliothèque, nous nous sommes concentrés sur Windows 10, Windows Server 2016 et Microsoft Endpoint Manager (Current Branch). Voir [Utiliser la protection microsoft fournie](cloud-protection-microsoft-defender-antivirus.md) par le cloud Antivirus Microsoft Defender pour un tableau qui décrit les principales différences. [(Revenir au tableau)](#ref2)

2. <span id="fn2" />Dans Windows 10, Antivirus Microsoft Defender est un composant disponible sans installation ou déploiement d’un client ou d’un service supplémentaire. Il est automatiquement activé lorsque des produits antivirus tiers sont désinstallés ou désinstallés (sauf[sur Windows Server 2016](microsoft-defender-antivirus-on-windows-server.md)). Le déploiement traditionnel n’est donc pas requis. Le déploiement ici fait référence à la garantie que le Antivirus Microsoft Defender est disponible et activé sur les points de terminaison ou les serveurs. [(Revenir au tableau)](#ref2)

3. <span id="fn3" />La configuration des fonctionnalités et de la protection, y compris la configuration des mises à jour du produit et de la protection, est décrite plus en détail dans la section Configurer [Antivirus Microsoft Defender fonctionnalités](configure-notifications-microsoft-defender-antivirus.md) de cette bibliothèque. [(Revenir au tableau)](#ref2)

## <a name="in-this-section"></a>Dans cette section

Rubrique | Description
---|---
[Déployer et activer la protection Antivirus Microsoft Defender de sécurité](deploy-microsoft-defender-antivirus.md) | Bien que le client soit installé en tant que partie intégrante de Windows 10 et que le déploiement classique ne s’applique pas, vous devrez quand même activer le client sur vos points de terminaison avec les objets de stratégie de groupe, Microsoft Endpoint Configuration Manager, Microsoft Intune ou.
[Gérer les mises Antivirus Microsoft Defender jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md) | La mise à jour des Antivirus Microsoft Defender se fait en deux parties : la mise à jour du client sur les points de terminaison (mises à jour des produits) et la mise à jour de l’intelligence de sécurité (mises à jour de la protection). Vous pouvez mettre à jour les informations de sécurité de plusieurs façons, à l’aide de Microsoft Endpoint Configuration Manager, d’une stratégie de groupe, de PowerShell et de WMI.
[Surveiller et signaler la protection Antivirus Microsoft Defender données](report-monitor-microsoft-defender-antivirus.md) | Vous pouvez utiliser Microsoft Intune, Microsoft Endpoint Configuration Manager, le module de conformité des mises à jour pour Microsoft Operations Management Suite ou un produit SIEM tiers (en consommant des journaux d’événements Windows) pour surveiller l’état de la protection et créer des rapports sur la protection des points de terminaison.