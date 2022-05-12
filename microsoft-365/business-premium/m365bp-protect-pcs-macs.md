---
title: Protéger les PC et Mac Windows 10 non gérés dans Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
ms.localizationpriority: high
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
description: Protégez les appareils non gérés ou BYOD contre les cyberattaques avec Microsoft 365 Business Premium. Comment configurer la cybersécurité pour les PC et Mac Windows.
ms.openlocfilehash: 0b13c208fd2cdd0fcadf7f5bc820d41b3621eebd
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65318831"
---
# <a name="protect-unmanaged-windows-10-pcs-and-macs-in-microsoft-365-business-premium"></a>Protéger les PC et Mac Windows 10 non gérés dans Microsoft 365 Business Premium

Cet objectif est axé sur la création d’une protection pour tous les PC et Mac Windows 10 non gérés qui ne sont pas inscrits dans Microsoft Intune. Il est très probable que votre petite entreprise ou campagne ait du personnel qui apporte ses propres appareils (BYOD) et ces appareils ne sont pas gérés. Les BYOD incluent les téléphones, tablettes et PC appartenant à l’utilisateur. 

>[!NOTE]
>Les utilisateurs BYOD doivent installer et exécuter l’application Portail d'entreprise pour inscrire ces appareils et recevoir l’accès aux ressources de l’entreprise.

Il est essentiel de vous assurer que vos utilisateurs de première ligne suivent ces instructions afin que les fonctionnalités de sécurité minimales soient configurées sur tous les appareils BYOD.

## <a name="windows-10"></a>[Windows 10](#tab/Windows10)

**Activer le chiffrement d’appareil**<p>
Le chiffrement d’appareil est disponible sur un large éventail d’appareils Windows et permet de protéger vos données en les chiffrant. Si vous activez le chiffrement de l’appareil, seules les personnes autorisées pourront accéder à votre appareil et à vos données. Pour obtenir des instructions, consultez [activer le chiffrement d’appareil](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) .

 Si le chiffrement de l’appareil n’est pas disponible sur votre appareil, vous pouvez activer le [chiffrement BitLocker](https://support.microsoft.com/help/4028713/windows-10-turn-on-device-encryption) standard à la place. (BitLocker n’est pas disponible sur Windows 10 Home edition.) 

**Protéger votre appareil avec Windows Secutity**<p>
Si vous avez Windows 10, vous obtenez la dernière protection antivirus avec Windows Security. Lorsque vous démarrez Windows 10 pour la première fois, Windows Security est activé et vous aide activement à protéger votre PC en recherchant les programmes malveillants, les virus et les menaces de sécurité. Windows Security utilise une protection en temps réel pour analyser tout ce que vous téléchargez ou exécutez sur votre PC.

Windows Update télécharge automatiquement les mises à jour de sécurité Windows pour assurer la sécurité de votre PC et le protéger contre les menaces.

Si vous disposez d’une version antérieure de Windows et que vous utilisez Microsoft Security Essentials, il est judicieux de passer à Windows Security. Pour plus d’informations, consultez [protéger mon appareil avec Windows Security](https://support.microsoft.com/help/17464/windows-10-help-protect-my-device-with-windows-security).

**Activer le Pare-feu Windows**<p>
Vous devez toujours exécuter le Pare-feu Windows même si un autre pare-feu déjà activé. La désactivation du Pare-feu Windows peut rendre votre appareil (et votre réseau, si vous en avez un) plus vulnérable(s) aux accès non autorisés. Pour obtenir des instructions, consultez [Activer ou désactiver le Pare-feu Windows](https://support.microsoft.com/help/4028544/windows-10-turn-windows-defender-firewall-on-or-off).

OK, mission terminée ! À présent, nous allons travailler sur la [sécurisation du système de messagerie](m365bp-protect-email-overview.md) contre le hameçonnage et d’autres attaques.

## <a name="mac"></a>[Mac](#tab/Mac)

**Utiliser FileVault pour chiffrer votre disque Mac**<p>
Le chiffrement du disque protège les données en cas de perte ou de vol des appareil. Le chiffrement intégral du disque FileVault permet d’empêcher les accès non autorisés aux informations sur votre disque de démarrage. Pour obtenir des instructions, consultez [Utiliser FileVault pour chiffrer le disque de démarrage sur votre Mac.](https://support.apple.com/HT204837)

**Protéger votre Mac contre les programmes malveillants**<p>
Microsoft vous recommande d’installer et d’utiliser un antivirus fiable sur votre Mac. Consultez l’article suivant pour obtenir la liste des choix suivants : [meilleur antivirus Mac 2019](https://www.macworld.co.uk/feature/mac-software/mac-antivirus-3672182/).

Vous pouvez également réduire le risque de logiciels malveillants en utilisant des logiciels provenant uniquement de sources fiables. Les paramètres des préférences Sécurité et confidentialité vous permettent de spécifier les sources des logiciels installés sur votre Mac. Pour plus d’informations, consultez [Protéger votre Mac contre les programmes malveillants](https://support.apple.com/kb/PH25087).

**Activer la protection pare-feu**<p>
Utilisez les paramètres du pare-feu pour protéger votre Mac contre les contacts indésirables émanant d’autres ordinateurs lorsque vous êtes connecté à Internet ou à un réseau. Sans cette protection, votre Mac peut être plus vulnérable aux accès non autorisés. Pour obtenir des instructions, consultez [À propos de pare-feu d’applications](https://support.apple.com/HT201642).

## <a name="next-mission"></a>Prochaine mission

OK, mission terminée ! À présent, nous allons travailler sur la [sécurisation du système de messagerie](m365bp-protect-email-overview.md) contre le hameçonnage et d’autres attaques.

