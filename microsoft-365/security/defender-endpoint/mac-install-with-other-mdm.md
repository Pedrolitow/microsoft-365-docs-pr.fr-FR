---
title: Déploiement avec un autre système Mobile Gestion des appareils (MDM) pour Microsoft Defender pour point de terminaison sur Mac
description: Installez Microsoft Defender pour point de terminaison sur Mac sur d’autres solutions de gestion.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, deploy, macos, catalina, big sur, monterey, ventura, mde ou mac
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: mavel
author: maximvelichko
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier3
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 93e22b11bba51b1b1ac33306c0a01c375ed09d27
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768080"
---
# <a name="deployment-with-a-different-mobile-device-management-mdm-system-for-microsoft-defender-for-endpoint-on-macos"></a>Déploiement avec un autre système Mobile Gestion des appareils (MDM) pour Microsoft Defender pour point de terminaison sur macOS

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-investigateip-abovefoldlink)
 
## <a name="prerequisites-and-system-requirements"></a>Conditions préalables et configuration système requise

Avant de commencer, consultez [la Microsoft Defender pour point de terminaison principale sur la page macOS](microsoft-defender-endpoint-mac.md) pour obtenir une description des prérequis et de la configuration système requise pour la version actuelle du logiciel.


## <a name="approach"></a>Approche

> [!CAUTION]

> Actuellement, Microsoft prend officiellement en charge uniquement Intune et JAMF pour le déploiement et la gestion des Microsoft Defender pour point de terminaison sur macOS. Microsoft n’offre aucune garantie, expresse ou implicite, concernant les informations fournies ci-dessous.

Si votre organisation utilise une solution mobile Gestion des appareils (MDM) qui n’est pas officiellement prise en charge, cela ne signifie pas que vous ne pouvez pas déployer ou exécuter Microsoft Defender pour point de terminaison sur macOS.

Microsoft Defender pour point de terminaison sur macOS ne dépend d’aucune fonctionnalité propre au fournisseur. Il peut être utilisé avec n’importe quelle solution GPM qui prend en charge les fonctionnalités suivantes :

- Déployez un fichier .pkg macOS sur des appareils gérés.
- Déployer des profils de configuration système macOS sur des appareils gérés.
- Exécutez un outil/script arbitraire configuré par l’administrateur sur des appareils gérés.

La plupart des solutions MDM modernes incluent ces fonctionnalités, mais elles peuvent les appeler différemment.

Toutefois, vous pouvez déployer Defender pour point de terminaison sans la dernière exigence de la liste précédente :

- Vous ne pourrez pas collecter l’état de manière centralisée.
- Si vous décidez de désinstaller Defender pour point de terminaison, vous devez vous connecter localement à l’appareil client en tant qu’administrateur.

## <a name="deployment"></a>Déploiement

La plupart des solutions MDM utilisent le même modèle pour la gestion des appareils macOS, avec une terminologie similaire. Utilisez le [déploiement basé sur JAMF](mac-install-with-jamf.md) comme modèle.

### <a name="package"></a>Paquet

Configurez le déploiement d’un [package d’application requis](mac-install-with-jamf.md), avec le package d’installation (wdav.pkg) téléchargé à partir [de Microsoft 365 Defender portail](mac-install-with-jamf.md).

Pour déployer le package dans votre entreprise, suivez les instructions associées à votre solution MDM.

### <a name="license-settings"></a>Paramètres de licence

Configurez [un profil de configuration système](mac-install-with-jamf.md). 

Votre solution MDM peut l’appeler « Profil de paramètres personnalisés », car Microsoft Defender pour point de terminaison sur macOS ne fait pas partie de macOS.

Utilisez la liste de propriétés jamf/WindowsDefenderATPOnboarding.plist, qui peut être extraite d’un package d’intégration téléchargé à partir [de Microsoft 365 Defender portail](mac-install-with-jamf.md).
Votre système peut prendre en charge une liste de propriétés arbitraires au format XML. Vous pouvez charger le fichier jamf/WindowsDefenderATPOnboarding.plist tel qu’il est dans ce cas.
Vous pouvez également devoir d’abord convertir la liste de propriétés dans un autre format.

En règle générale, votre profil personnalisé a un ID, un nom ou un attribut de domaine. Vous devez utiliser exactement « com.microsoft.wdav.atp » pour cette valeur.
MDM l’utilise pour déployer le fichier de paramètres sur **/Library/Managed Preferences/com.microsoft.wdav.atp.plist** sur un appareil client, et Defender pour point de terminaison utilise ce fichier pour charger les informations d’intégration.

### <a name="kernel-extension-policy"></a>Stratégie d’extension du noyau

Configurez une stratégie d’extension KEXT ou noyau. Utilisez l’identificateur d’équipe **UBF8T346G9** pour autoriser les extensions de noyau fournies par Microsoft.

> [!CAUTION]
> Si votre environnement se compose d’appareils Apple Silicon (M1), ces machines ne doivent pas recevoir de profils de configuration avec des stratégies KEXT.
> Apple ne prend pas en charge KEXT sur ces machines. Le déploiement d’un tel profil échouerait sur les machines M1.

### <a name="system-extension-policy"></a>Stratégie d’extension système

Configurez une stratégie d’extension système. Utilisez l’identificateur d’équipe **UBF8T346G9** et approuvez les identificateurs de bundle suivants :

- com.microsoft.wdav.epsext
- com.microsoft.wdav.netext

### <a name="full-disk-access-policy"></a>Stratégie d’accès au disque complet

Accordez l’accès disque complet aux composants suivants :

- Microsoft Defender pour point de terminaison
    - Identificateur: `com.microsoft.wdav`
    - Type d’identificateur : ID d’offre groupée
    - Configuration requise du code : `identifier "com.microsoft.wdav" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

- extension de sécurité Microsoft Defender pour point de terminaison
    - Identificateur: `com.microsoft.wdav.epsext`
    - Type d’identificateur : ID d’offre groupée
    - Configuration requise du code : `identifier "com.microsoft.wdav.epsext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`

### <a name="network-extension-policy"></a>Stratégie d’extension réseau

Dans le cadre des fonctionnalités de détection et de réponse des points de terminaison, Microsoft Defender pour point de terminaison sur macOS inspecte le trafic de socket et signale ces informations au portail Microsoft 365 Defender. La stratégie suivante permet à l’extension réseau d’effectuer cette fonctionnalité.

- Type de filtre : Plug-in
- Identificateur du bundle de plug-ins : `com.microsoft.wdav`
- Filtrer l’identificateur d’offre groupée du fournisseur de données : `com.microsoft.wdav.netext`
- Condition requise désignée par le fournisseur de données de filtre : `identifier "com.microsoft.wdav.netext" and anchor apple generic and certificate 1[field.1.2.840.113635.100.6.2.6] /* exists */ and certificate leaf[field.1.2.840.113635.100.6.1.13] /* exists */ and certificate leaf[subject.OU] = UBF8T346G9`
- Sockets de filtre : `true`

## <a name="check-installation-status"></a>Vérifier l’état de l’installation

Exécutez [Microsoft Defender pour point de terminaison](mac-install-with-jamf.md) sur un appareil client pour vérifier l’état de l’intégration.
