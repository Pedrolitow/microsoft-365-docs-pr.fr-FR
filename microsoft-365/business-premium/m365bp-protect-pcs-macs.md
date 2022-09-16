---
title: Protéger les PC et Mac Windows non gérés dans Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: other
ms.date: 09/15/2022
ms.localizationpriority: high
ms.collection:
- M365-Campaigns
- m365solution-smb
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
- MOE150
description: Protégez les appareils non gérés ou BYOD contre les cyberattaques avec Microsoft 365 Business Premium. Comment configurer la cybersécurité pour les PC et Mac Windows.
ms.openlocfilehash: 453978e05de59327472247419cbeb0d87fe8ce61
ms.sourcegitcommit: c29af68260ba8676083674b3c70209bff2c2e362
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/16/2022
ms.locfileid: "67737629"
---
# <a name="protect-unmanaged-windows-pcs-and-macs-in-microsoft-365-business-premium"></a>Protéger les PC et Mac Windows non gérés dans Microsoft 365 Business Premium

Cet objectif est axé sur la création d’une protection pour tous les PC et Mac Windows 10 non gérés qui ne sont pas inscrits dans Microsoft Intune. Il est très probable que votre petite entreprise ou votre campagne dispose d'un personnel qui apporte ses propres appareils (BYOD), et que ces appareils ne sont pas toujours disponibles. Les appareils BYOD incluent les téléphones, tablettes et PC appartenant à l’utilisateur.

> [!NOTE]
> Les utilisateurs BYOD doivent installer et exécuter l’application Portail d'entreprise pour inscrire ces appareils et recevoir l’accès aux ressources de l’entreprise.

Il est essentiel de vous assurer que vos utilisateurs de première ligne suivent ces instructions afin que les fonctionnalités de sécurité minimales soient configurées sur tous les appareils BYOD.

## <a name="windows-10-or-11"></a>[Windows 10 ou 11](#tab/Windows10-11)

## <a name="windows-10-or-11"></a>Windows 10 ou 11

### <a name="turn-on-device-encryption"></a>Activer le chiffrement d’appareil

Le chiffrement d’appareil est disponible sur un large éventail d’appareils Windows et permet de protéger vos données en les chiffrant. Si vous activez le chiffrement de l’appareil, seules les personnes autorisées pourront accéder à votre appareil et à vos données. Pour obtenir des instructions, consultez [activer le chiffrement d’appareil](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) .

 Si le chiffrement de l’appareil n’est pas disponible sur votre appareil, vous pouvez activer le [chiffrement BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) standard à la place. (BitLocker n’est pas disponible sur Windows 10 Home edition.) 

### <a name="protect-your-device-with-windows-security"></a>Protéger votre appareil avec Windows Secutity

Si vous avez Windows 10 ou 11, vous obtenez la dernière protection antivirus avec Windows Security. Lorsque vous démarrez Windows 10 pour la première fois, Windows Security est activé et vous aide activement à protéger votre PC en recherchant les programmes malveillants, les virus et les menaces de sécurité. Windows Security utilise une protection en temps réel pour analyser tout ce que vous téléchargez ou exécutez sur votre PC.

Windows Update télécharge automatiquement les mises à jour de sécurité Windows pour assurer la sécurité de votre PC et le protéger contre les menaces.

Si vous disposez d’une version antérieure de Windows et que vous utilisez Microsoft Security Essentials, il est judicieux de passer à Windows Security. Pour plus d’informations, consultez [protéger mon appareil avec Windows Security](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

### <a name="turn-on-windows-defender-firewall"></a>Activation du pare-feu Windows Defender

Vous devez toujours exécuter le Pare-feu Windows Defender même si un autre pare-est activé. La désactivation du Pare-feu Windows Defender peut rendre votre appareil (et votre réseau, si vous en avez un) plus vulnérable(s) aux accès non autorisés. Pour obtenir des instructions, consultez [Activer ou désactiver le Pare-feu Windows](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off).

## <a name="next-mission"></a>Prochaine mission

OK, mission terminée ! À présent, nous allons travailler sur la [sécurisation du système de messagerie](m365bp-protect-email-overview.md) contre le hameçonnage et d’autres attaques.

## <a name="mac"></a>[Mac](#tab/Mac)

## <a name="mac"></a>Mac

### <a name="use-filevault-to-encrypt-your-mac-disk"></a>Utiliser FileVault pour chiffrer votre disque Mac

Le chiffrement du disque protège les données en cas de perte ou de vol des appareil. Le chiffrement intégral du disque FileVault permet d’empêcher les accès non autorisés aux informations sur votre disque de démarrage. Pour obtenir des instructions, consultez [Utiliser FileVault pour chiffrer le disque de démarrage sur votre Mac.](https://support.apple.com/HT204837)

### <a name="protect-your-mac-from-malware"></a>Protéger votre Mac contre les programmes malveillants

Microsoft vous recommande d’installer et d’utiliser un antivirus fiable sur votre Mac. Consultez l’article suivant pour obtenir la liste des choix suivants : [meilleur antivirus Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Vous pouvez également réduire le risque de logiciels malveillants en utilisant des logiciels provenant uniquement de sources fiables. Les paramètres des préférences Sécurité et confidentialité vous permettent de spécifier les sources des logiciels installés sur votre Mac. Pour plus d’informations, consultez [Protéger votre Mac contre les programmes malveillants](https://support.apple.com/kb/PH25087).

### <a name="turn-on-firewall-protection"></a>Activez la protection du pare-feu

Utilisez les paramètres du pare-feu pour protéger votre Mac contre les contacts indésirables émanant d’autres ordinateurs lorsque vous êtes connecté à Internet ou à un réseau. Sans cette protection, votre Mac peut être plus vulnérable aux accès non autorisés. Pour obtenir des instructions, consultez [À propos de pare-feu d’applications](https://support.apple.com/HT201642).

## <a name="next-mission"></a>Prochaine mission

OK, mission terminée ! À présent, nous allons travailler sur la [sécurisation de l’utilisation des e-mails contre le](m365bp-protect-email-overview.md) hameçonnage et d’autres attaques.