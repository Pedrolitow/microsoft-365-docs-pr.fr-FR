---
title: Protection des ordinateurs Windows 10 et Mac non gérés
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
ms.audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- M365-subscription-management
- M365-identity-device-management
- M365-Campaigns
ms.custom:
- Adm_O365
- MiniMaven
- MSB365
search.appverid:
- BCS160
- MET150
- MOE150
description: Protégez-vous contre le hameçonnage et les autres attaques à l’aide de Microsoft 365 pour les campagnes.
ms.openlocfilehash: 7cb09d0cadcc70b96c5f1404defa5d0387947ca8
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41594795"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs"></a>Protection des ordinateurs Windows 10 et Mac non gérés

Vous pouvez gérer des PC Windows 10 et des Mac en les inscrivant dans Microsoft Intune, ce qui vous permet de vous assurer qu’ils sont sains et sécurisés avant d’accéder aux données de votre environnement. Toutefois, de nombreuses campagnes et petites entreprises incluent des personnes qui apportent leurs propres appareils (BYOD), qui ne seront pas gérées par l’organisation. Pour ces PC et Mac non gérés, utilisez cet article pour vous assurer que les fonctionnalités de sécurité minimales sont configurées. 

<!--A Windows 10 PC is considered managed after you have completed the following two steps:

1. You (or the admin) set up device and data protection policies in the [setup  wizard](../business/set-up.md).

2. You have [connected your computer to Azure Active Directory](../business/set-up-windows-devices.md) and use your Microsoft 365 Business username and password to sign in.
3. --> 

## <a name="protect-a-computer-running-windows-10-or-a-mac"></a>Protéger un ordinateur exécutant Windows 10 ou un Mac

<!--If you have a PC that is running Windows 10 that is not connected to Microsoft 365 Business, or a Mac, the Microsoft 365 Business protections do not apply to it, but here are some things you can do to keep your data secure on these devices as well:
-->
Si votre PC ou Mac Windows 10 n’est pas géré par votre organisation, veillez à configurer ces fonctionnalités de sécurité.

## <a name="windows-10tabwindows10"></a>[Windows 10](#tab/Windows10)
**Activer le chiffrement de l’appareil**<p>

Le chiffrement d’appareil est disponible sur un large éventail d’appareils Windows et vous aide à protéger vos données en les chiffrant. Si vous activez le chiffrement de l’appareil, seules les personnes autorisées pourront accéder à votre appareil et à vos données. Pour obtenir des instructions, voir [activer le chiffrement](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) de l’appareil.

 Si le chiffrement de l’appareil n’est pas disponible sur votre appareil, vous pouvez activer le [chiffrement BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) standard. (BitLocker n’est pas disponible dans Windows 10 édition familiale.) 


**Protéger votre appareil avec la sécurité Windows**<p>
Si vous disposez de Windows 10, vous obtiendrez la dernière protection antivirus avec Windows Security. Lorsque vous démarrez Windows 10 pour la première fois, la sécurité de Windows est activée et contribue activement à protéger votre PC en recherchant les programmes malveillants (logiciels malveillants), les virus et les menaces de sécurité. La sécurité Windows utilise la protection en temps réel pour analyser tout ce que vous téléchargez ou exécutez sur votre PC.

Windows Update télécharge automatiquement les mises à jour pour la sécurité Windows afin de protéger votre PC contre les menaces.

Si vous disposez d’une version antérieure de Windows et que vous utilisez Microsoft Security Essentials, nous vous recommandons de passer à la sécurité Windows. Pour plus d’informations, consultez la rubrique [Protégez mon appareil avec Windows Security](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Activer le pare-feu Windows**<p>
Vous devez toujours exécuter le pare-feu Windows même si vous avez un autre pare-feu activé. Désactiver le pare-feu Windows peut rendre votre appareil (et votre réseau, si vous en avez un) plus vulnérable aux accès non autorisés. Pour obtenir des instructions, voir [activer ou désactiver le pare-feu Windows](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off) .

## <a name="mactabmac"></a>[Mac](#tab/Mac)
**Utiliser FileVault pour chiffrer votre disque Mac**<p>
Le chiffrement de disque protège les données en cas de perte ou de vol des appareils. FileVault le chiffrement de disque complet empêche l’accès non autorisé aux informations de votre disquette de démarrage. Pour obtenir des instructions, voir [utiliser FileVault pour chiffrer la disquette de démarrage sur votre Mac](https://support.apple.com/HT204837) .

**Protéger votre Mac contre les programmes malveillants**<p>
Microsoft vous recommande d’installer et d’utiliser un logiciel antivirus fiable sur votre Mac. Consultez l’article suivant pour obtenir une liste de choix : [Best Mac antivirus 2019 ](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Vous pouvez également réduire le risque de programmes malveillants à l’aide de logiciels uniquement à partir de sources fiables. Les paramètres de sécurité & préférences de confidentialité vous permettent de spécifier les sources des logiciels installés sur votre Mac. Pour plus d’informations, consultez [la rubrique Protégez votre Mac contre les programmes malveillants](https://support.apple.com/kb/PH25087).

**Activer la protection de pare-feu**<p>
Utilisez les paramètres de pare-feu pour protéger votre Mac contre les contacts indésirables initiés par d’autres ordinateurs lorsque vous êtes connecté à Internet ou à un réseau. Sans cette protection, votre Mac peut être plus vulnérable aux accès non autorisés. Consultez [la rubrique à propos du pare-feu d’application](https://support.apple.com/HT201642) pour obtenir des instructions.
