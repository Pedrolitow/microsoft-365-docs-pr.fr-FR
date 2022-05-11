---
title: Déploiement avec un autre système mobile Gestion des appareils (GPM) pour Microsoft Defender pour point de terminaison sur Mac
description: Installez Microsoft Defender pour point de terminaison sur Mac sur d’autres solutions de gestion.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, macos, catalina, mojave, high sierra
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: mavel
author: maximvelichko
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 2fa64ee9822fe1f784788e2d1ead79e66eb200ef
ms.sourcegitcommit: 2d870e06e87b10d9e8ec7a7a8381353bc3bc59c7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65349735"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>Déploiement avec un autre système Mobile Gestion des appareils (MDM) pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Prérequis et configuration requise

Avant de commencer, consultez [la Microsoft Defender pour point de terminaison principale sur macOS page](microsoft-defender-endpoint-mac.md) pour obtenir une description des prérequis et de la configuration système requise pour la version actuelle du logiciel.


## <a name="approach"></a>Approche

> [!CAUTION]

> Actuellement, Microsoft prend officiellement en charge uniquement Intune et JAMF pour le déploiement et la gestion des Microsoft Defender pour point de terminaison sur macOS. Microsoft n’offre aucune garantie, expresse ou implicite, en ce qui concerne les informations fournies ci-dessous.

Si votre organisation utilise une solution Mobile Gestion des appareils (MDM) qui n’est pas officiellement prise en charge, cela ne signifie pas que vous ne pouvez pas déployer ou exécuter Microsoft Defender pour point de terminaison sur macOS.

Microsoft Defender pour point de terminaison sur macOS ne dépend d’aucune fonctionnalité propre au fournisseur. Il peut être utilisé avec n’importe quelle solution GPM qui prend en charge les fonctionnalités suivantes :

- Déployez un macOS .pkg sur des appareils gérés.
- Déployez macOS profils de configuration système sur des appareils gérés.
- Exécutez un script/outil arbitraire configuré par l’administrateur sur les appareils gérés.

La plupart des solutions MDM modernes incluent ces fonctionnalités, mais elles peuvent les appeler différemment.

Toutefois, vous pouvez déployer Defender pour point de terminaison sans la dernière exigence de la liste précédente :

- Vous ne pourrez pas collecter l’état de manière centralisée.
- Si vous décidez de désinstaller Defender pour point de terminaison, vous devez vous connecter à l’appareil client localement en tant qu’administrateur.

## <a name="deployment"></a>Déploiement

La plupart des solutions GPM utilisent le même modèle pour gérer macOS appareils, avec une terminologie similaire. Utilisez le [déploiement basé sur JAMF](mac-install-with-jamf.md) comme modèle.

### <a name="package"></a>Paquet

Configurez le déploiement d’un [package d’application requis](mac-install-with-jamf.md), avec le package d’installation (wdav.pkg) téléchargé à partir de [Microsoft 365 Defender portail](mac-install-with-jamf.md).

Pour déployer le package dans votre entreprise, suivez les instructions associées à votre solution GPM.

### <a name="license-settings"></a>Paramètres de licence

Configurez [un profil de configuration système](mac-install-with-jamf.md). 

Votre solution GPM peut l’appeler « Profil de Paramètres personnalisé », car Microsoft Defender pour point de terminaison sur macOS ne fait pas partie de macOS.

Utilisez la liste des propriétés, jamf/WindowsDefenderATPOnboarding.plist, qui peut être extraite d’un package d’intégration téléchargé à partir de [Microsoft 365 Defender portail](mac-install-with-jamf.md).
Votre système peut prise en charge d’une liste de propriétés arbitraire au format XML. Vous pouvez charger le fichier jamf/WindowsDefenderATPOnboarding.plist tel qu’il est dans ce cas.
Vous devrez peut-être d’abord convertir la liste de propriétés dans un format différent.

En règle générale, votre profil personnalisé a un ID, un nom ou un attribut de domaine. Vous devez utiliser exactement « com.microsoft.wdav.atp » pour cette valeur.
MDM l’utilise pour déployer le fichier de paramètres sur **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** sur un appareil client, et Defender pour point de terminaison utilise ce fichier pour charger les informations d’intégration.

### <a name="kernel-extension-policy"></a>Stratégie d’extension de noyau

Configurez une stratégie d’extension KEXT ou de noyau. Utilisez l’identificateur d’équipe **UBF8T346G9** pour autoriser les extensions de noyau fournies par Microsoft.

> [!CAUTION]
> Si votre environnement se compose d’appareils Apple Silicon (M1), ces machines ne doivent pas recevoir de profils de configuration avec des stratégies KEXT.
> Apple ne prend pas en charge KEXT sur ces machines, le déploiement de ce profil échouerait sur les machines M1.

### <a name="system-extension-policy"></a>Stratégie d’extension système

Configurez une stratégie d’extension système. Utilisez l’identificateur d’équipe **UBF8T346G9** et approuvez les identificateurs de bundle suivants :

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Stratégie d’accès au disque complet

Accordez l’accès au disque complet aux composants suivants :

- Microsoft Defender pour point de terminaison
    - Identificateur: `com.microsoft.wdav`
    - Type d’identificateur : ID de bundle
    - Exigence de code : `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- extension de sécurité Microsoft Defender pour point de terminaison
    - Identificateur: `com.microsoft.wdav.epsext`
    - Type d’identificateur : ID de bundle
    - Exigence de code : `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Stratégie d’extension réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender pour point de terminaison sur macOS inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

- Type de filtre : plug-in
- Identificateur du bundle de plug-ins : `com.microsoft.wdav`
- Identificateur de bundle du fournisseur de données de filtre : `com.microsoft.wdav.netext`
- Condition requise désignée par le fournisseur de données de filtre : `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Filtrer les sockets : `true`

## <a name="check-installation-status"></a>Vérifier l’état de l’installation

Exécutez [Microsoft Defender pour point de terminaison](mac-install-with-jamf.md) sur un appareil client pour vérifier l’état de l’intégration.
