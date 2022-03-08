---
title: Protéger les PC et Mac Windows 10 nonmanagés dans Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
- m365solution-smb
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Protégez les appareils byod non utilisés ou apportez vos propres appareils (BYOD) avec Microsoft 365 Business Premium.
ms.openlocfilehash: b3d783ba498337af7ff867fe749366abe1734da5
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330877"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs-in-microsoft-365-business-premium"></a>Protéger les PC et Mac Windows 10 nonmanagés dans Microsoft 365 Business Premium

Vous pouvez gérer les PC et Mac Windows 10 en les inscrivant dans Microsoft Intune, ce qui vous permet de vous assurer qu’ils sont sains et sécurisés avant d’accéder aux données de votre environnement. Toutefois, de nombreuses campagnes et petites entreprises incluent des employés qui apportent leurs propres appareils (BYOD), qui ne seront pas gérés par l’organisation. Pour ces PC et Mac non utilisés, utilisez cet article pour vous assurer que les fonctionnalités de sécurité minimales sont configurées.

<!--A Windows 10 PC is considered managed after you have completed the following two steps:

1. You (or the admin) set up device and data protection policies in the [setup  wizard](../business/set-up.md).

2. You have [connected your computer to Azure Active Directory](../business/set-up-windows-devices.md) and use your Microsoft 365 username and password to sign in.
3. --> 

## <a name="protect-a-computer-running-windows-10-or-a-mac"></a>Protéger un ordinateur exécutant Windows 10 ou un Mac

<!--If you have a PC that is running Windows 10 that is not connected to Microsoft 365, or a Mac, the Microsoft 365 protections do not apply to it, but here are some things you can do to keep your data secure on these devices as well:
-->
Si votre PC ou Mac Windows 10 n’est pas géré par votre organisation, assurez-vous de configurer ces fonctionnalités de sécurité.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**Activer le chiffrement de l’appareil**<p>

Le chiffrement d’appareil est disponible sur un large éventail d’appareils Windows et permet de protéger vos données en les chiffrant. Si vous allumez le chiffrement de l’appareil, seules les personnes autorisées pourront accéder à votre appareil et à vos données. Pour obtenir des instructions [, voir](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) activer le chiffrement de l’appareil.

 Si le chiffrement de l’appareil n’est pas disponible sur votre appareil, vous pouvez activer le chiffrement [BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) standard à la place. (BitLocker n’est pas disponible sur Windows 10 Édition Familiale.) 

**Protéger votre appareil avec la sécurité Windows**<p>
Si vous avez Windows 10, vous obtenez la dernière protection antivirus avec la sécurité Windows. Lorsque vous démarrez Windows 10 pour la première fois, la sécurité Windows est active et contribue activement à protéger votre PC en analysant les programmes malveillants (logiciels malveillants), les virus et les menaces de sécurité. La sécurité Windows utilise la protection en temps réel pour analyser tout ce que vous téléchargez ou exécutez sur votre PC.

Windows Update télécharge automatiquement les mises à jour de sécurité Windows pour assurer la sécurité de votre PC et le protéger contre les menaces.

Si vous avez une version antérieure de Windows et que vous utilisez Microsoft Security Essentials, il est bon de passer à la sécurité Windows. Pour plus d’informations, [voir l’aide pour protéger mon appareil avec la sécurité Windows](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Activer le Pare-feu Windows**<p>
Vous devez toujours exécuter le Pare-feu Windows même si un autre pare-feu est allumé. La désélration du Pare-feu Windows peut rendre votre appareil (et votre réseau, si vous en avez un) plus vulnérable aux accès non autorisés. Pour obtenir des instructions [, voir Activer ou désactiver le](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) Pare-feu Windows.

## <a name="mac"></a>[Mac](#tab/Mac)

**Utiliser FileVault pour chiffrer votre disque Mac**<p>
Le chiffrement de disque protège les données en cas de perte ou de vol d’appareils. Le chiffrement de disque intégral FileVault permet d’empêcher l’accès non autorisé aux informations sur votre disque de démarrage. Voir [utiliser FileVault pour chiffrer le disque de démarrage sur votre Mac](https://support.apple.com/HT204837) pour obtenir des instructions.

**Protéger votre mac contre les programmes malveillants**<p>
Microsoft vous recommande d’installer et d’utiliser des logiciels antivirus fiables sur votre Mac. Consultez l’article suivant pour obtenir la liste des choix : [Best Mac antivirus 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Vous pouvez également réduire le risque de programmes malveillants en utilisant des logiciels uniquement à partir de sources fiables. Les paramètres des préférences de confidentialité & sécurité vous permettent de spécifier les sources de logiciels installées sur votre Mac. Pour plus d’informations, [voir protéger votre Mac contre les programmes malveillants](https://support.apple.com/kb/PH25087).

**Activer la protection contre le pare-feu**<p>
Utilisez les paramètres de pare-feu pour protéger votre Mac contre les contacts indésirables initiés par d’autres ordinateurs lorsque vous êtes connecté à Internet ou à un réseau. Sans cette protection, votre Mac peut être plus vulnérable aux accès non autorisés. Pour obtenir des instructions [, voir le pare-feu](https://support.apple.com/HT201642) de l’application.
