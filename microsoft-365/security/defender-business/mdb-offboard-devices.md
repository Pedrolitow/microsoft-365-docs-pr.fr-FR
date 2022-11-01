---
title: Retirer un appareil d’Microsoft Defender pour entreprises
description: Découvrez comment supprimer ou désactiver un appareil d’Microsoft Defender pour entreprises.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 08/11/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365-initiative-defender-business
- tier1
ms.openlocfilehash: c87446bc9ce25287f2d615e72c11a56619742186
ms.sourcegitcommit: 0c72639cc3dc74667a6b14343d303f318e70d457
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/01/2022
ms.locfileid: "68804836"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>Retirer un appareil d’Microsoft Defender pour entreprises

À mesure que les appareils sont remplacés ou mis hors service, ou que les besoins de votre entreprise changent, vous pouvez désactiver les appareils de Defender pour les entreprises. La désintégration d’un appareil entraîne l’arrêt de l’envoi de données à Defender pour Les Entreprises. Toutefois, les données reçues avant le retrait sont conservées jusqu’à six (6) mois.

> [!IMPORTANT]
> Les procédures décrites dans cet article décrivent comment supprimer un appareil de la surveillance par Defender pour Les Entreprises. Si vous utilisez Microsoft Intune pour gérer des appareils et que vous préférez supprimer l’appareil de Intune, consultez [Supprimer des appareils à l’aide de la réinitialisation, de la mise hors service ou de la désinscription manuelle de l’appareil](/mem/intune/remote-actions/devices-wipe).

## <a name="what-to-do"></a>Procédure

1. Sélectionnez un onglet :

   - **Windows 10 ou 11**
   - **Mac**
   - **Serveurs** (Windows Server ou Linux Server)
   - **Mobile** (pour les appareils iOS/iPadOS ou Android)

2. Suivez les instructions de l’onglet sélectionné.
3. Passez aux étapes suivantes. 

## <a name="windows-10-or-11"></a>[**Windows 10 ou 11**](#tab/Windows1011)

## <a name="windows-10-or-11"></a>Windows 10 ou 11

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres**, puis choisissez **Points de terminaison**.

3. Sous **Gestion des appareils**, choisissez **Retrait**.

4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous **Désinscrit un appareil**, dans la section **Méthode de déploiement**, choisissez **Script local**. 

5. Dans l’écran de confirmation, passez en revue les informations, puis choisissez **Télécharger** pour continuer.

6. Select **Download offboarding package**. We recommend saving the offboarding package to a removable drive.

7. Exécutez le script sur chaque appareil que vous souhaitez déclasser.

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser votre tableau de bord Gestion des vulnérabilités Microsoft Defender dans Microsoft Defender pour entreprises](mdb-view-tvm-dashboard.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises](mdb-view-edit-create-policies.md)
- [Gérer les appareils dans Microsoft Defender pour entreprises](mdb-manage-devices.md)

## <a name="mac"></a>[**Mac**](#tab/mac)

## <a name="offboard-a-mac"></a>Dé-bord d’un Mac

1. Accédez à **Finder** > **Applications**. 

2. Cliquez avec le bouton droit sur **Microsoft Defender pour entreprises**, puis choisissez **Déplacer vers la Corbeille**. <br/>--- ou --- <br/> Utilisez la commande suivante : `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser votre tableau de bord Gestion des vulnérabilités Microsoft Defender dans Microsoft Defender pour entreprises](mdb-view-tvm-dashboard.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises](mdb-view-edit-create-policies.md)
- [Gérer les appareils dans Microsoft Defender pour entreprises](mdb-manage-devices.md)


## <a name="servers"></a>[**Servers**](#tab/Servers)

## <a name="servers"></a>Serveurs

Choisissez le système d’exploitation pour votre serveur :

- [Windows Server](#windows-server)
- [Serveur Linux](#linux-server)

### <a name="windows-server"></a>Windows Server

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** > **Points de terminaison**, puis sous **Gestion des** appareils, choisissez **Désintégrer**.

3. Sélectionnez un système d’exploitation, tel que **Windows Server 1803, 2019 et 2022**, puis, dans la section **Méthode de déploiement** , choisissez **Script local**. 

4. Sélectionnez **Télécharger le package**. Nous vous recommandons d’enregistrer le package de désintéglage sur un lecteur amovible. Le dossier compressé est appelé `WindowsDefenderATPOffboardingPackage_valid_until_YYYY-MM-DD.zip` (où `YYYY-MM-DD` est la date d’expiration du package).

5. Sur votre appareil Windows Server, extrayez le contenu du dossier compressé à un emplacement tel que le dossier Desktop.  

6. Ouvrez une invite de commandes en tant qu’administrateur.

7. Tapez l’emplacement du fichier de script. Par exemple, si vous avez copié le fichier dans le dossier Desktop, vous devez taper `%userprofile%\Desktop\WindowsDefenderATPOffboardingScript_valid_until_2022-11-11.cmd` (où `YYYY-MM-DD` est la date d’expiration du package), puis appuyer sur Entrée (ou sélectionner **OK**).

### <a name="linux-server"></a>Serveur Linux

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres** > **Points de terminaison**, puis sous **Gestion des** appareils, choisissez **Désintégrer**.

3. Sélectionnez **Serveur Linux** pour le système d’exploitation, puis dans la section **Méthode de déploiement** , choisissez **Script local**. 

4. Sélectionnez **Télécharger le package**. Nous vous recommandons d’enregistrer le package de désintéglage sur un lecteur amovible. Le dossier compressé est appelé `WindowsDefenderATPOffboardingPackage_valid_until_YYYY-MM-DD.zip` (où `YYYY-MM-DD` est la date d’expiration du package).

5. Sur votre appareil Linux Server, extrayez le contenu du dossier compressé à un emplacement tel que le dossier Desktop.  

6. Ouvrez un terminal et accédez au répertoire où se trouve le `MicrosoftDefenderATPOffboardingLinuxServer_valid_until_YYYY-MM-DD` fichier (où `YYYY-MM-DD` est la date d’expiration du fichier).

7. Tapez `python MicrosoftDefenderATPOffboardingLinuxServer_valid_until_YYYY-MM-DD.py` dans le terminal.

> [!TIP]
> Pour plus d’informations, consultez Les instructions de [désinstallation](../defender-endpoint/linux-resources.md) dans le Microsoft Defender pour point de terminaison sur Linux.

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser votre tableau de bord Gestion des vulnérabilités Microsoft Defender dans Microsoft Defender pour entreprises](mdb-view-tvm-dashboard.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises](mdb-view-edit-create-policies.md)
- [Gérer les appareils dans Microsoft Defender pour entreprises](mdb-manage-devices.md)

## <a name="mobile-devices"></a>[**Appareils mobiles**](#tab/mobiles)

## <a name="mobile-devices"></a>Appareils mobiles

Vous pouvez utiliser Microsoft Intune pour gérer les appareils mobiles, tels que les appareils iOS, iPadOS et Android.

Consultez [Microsoft Intune gestion des appareils](/mem/intune/remote-actions/device-management).

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser votre tableau de bord Gestion des vulnérabilités Microsoft Defender dans Microsoft Defender pour entreprises](mdb-view-tvm-dashboard.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises](mdb-view-edit-create-policies.md)
- [Gérer les appareils dans Microsoft Defender pour entreprises](mdb-manage-devices.md)