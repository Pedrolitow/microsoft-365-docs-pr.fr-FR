---
title: Configurer le délai d’expiration du bloc cloud Microsoft Defender Antivirus
description: Vous pouvez configurer la durée pendant laquelle Microsoft Defender Antivirus bloque l’exécution d’un fichier en attendant une détermination du cloud.
keywords: Microsoft Defender Antivirus, logiciel anti-programme malveillant, sécurité, defender, cloud, délai d’expiration, bloc, période, secondes
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: article
ms.date: 10/18/2021
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: db2bddee6bae8c314dfcb1d721f5742a00b04584
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193122"
---
# <a name="configure-the-cloud-block-timeout-period"></a>Configurer le délai de blocage du cloud

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

Lorsque Microsoft Defender Antivirus trouve un fichier suspect, il peut empêcher l’exécution du fichier pendant qu’il interroge le [service cloud antivirus Microsoft Defender](cloud-protection-microsoft-defender-antivirus.md).

La période par défaut pendant laquelle le fichier est [bloqué](configure-block-at-first-sight-microsoft-defender-antivirus.md) est de 10 secondes. Si vous êtes administrateur de sécurité, vous pouvez spécifier plus de temps d’attente avant que le fichier ne soit autorisé à s’exécuter. L’extension du délai d’expiration du bloc cloud peut vous aider à vous assurer qu’il y a suffisamment de temps pour recevoir une détermination appropriée du service cloud Microsoft Defender Antivirus.

## <a name="prerequisites-to-use-the-extended-cloud-block-timeout"></a>Conditions préalables à l’utilisation du délai d’expiration du bloc cloud étendu

[Bloquer à la première consultation](configure-block-at-first-sight-microsoft-defender-antivirus.md) et ses prérequis doivent être activés avant de pouvoir spécifier un délai d’expiration prolongé.

## <a name="specify-the-extended-timeout-period-using-microsoft-endpoint-manager"></a>Spécifier le délai d’expiration prolongé à l’aide de Microsoft Endpoint Manager

Vous pouvez spécifier le délai d’expiration du bloc cloud avec une [stratégie de sécurité de point de terminaison dans Microsoft Endpoint Manager](/mem/intune/protect/endpoint-security-policy).

1. Accédez au centre d’administration Endpoint Manager ([https://endpoint.microsoft.com/](https://endpoint.microsoft.com/)) et connectez-vous.

2. Sélectionnez **Sécurité** des points de terminaison, puis, sous **Gérer**, choisissez **Antivirus**.

3. Sélectionnez (ou créez) une stratégie antivirus.

4. Dans la section **Paramètres de configuration** , développez **la protection cloud**. Ensuite, dans la **zone Microsoft Defender délai d’expiration étendu de l’antivirus en secondes**, spécifiez le temps supplémentaire, en secondes, de 1 seconde à 50 secondes. Tout ce que vous spécifiez est ajouté aux 10 secondes par défaut.

5. (Cette étape est facultative) Apportez d’autres modifications à votre stratégie antivirus. (Vous avez besoin d’aide ? Consultez [Paramètres de Microsoft Defender stratégie antivirus dans Microsoft Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-windows).)

6. Choisissez **Suivant**, puis terminez la configuration de votre stratégie.

## <a name="specify-the-extended-timeout-period-using-group-policy"></a>Spécifier le délai d’expiration prolongé à l’aide de stratégie de groupe

Vous pouvez utiliser stratégie de groupe pour spécifier un délai d’expiration étendu pour les vérifications cloud.

1. Sur votre ordinateur de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **La configuration de l’ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence sur **les composants** \> Windows Microsoft Defender **MpEngine** **antivirus**\>.

4. Double-cliquez sur **Configurer la vérification cloud étendue** et vérifiez que l’option est activée. 

   Spécifiez la durée supplémentaire nécessaire pour empêcher l’exécution du fichier en attendant une détermination du cloud. Spécifiez le temps supplémentaire, en secondes, de 1 seconde à 50 secondes. Tout ce que vous spécifiez est ajouté aux 10 secondes par défaut.

5. Sélectionnez **OK**.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md) 
