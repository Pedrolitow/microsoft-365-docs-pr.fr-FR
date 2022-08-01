---
title: Désintégrage d’un appareil à partir de Microsoft Defender pour entreprises
description: Découvrez comment supprimer ou déconnecter un appareil de Microsoft Defender pour entreprises.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: bd6ea78daa1a19d84efc23c34bdb58704484c0d1
ms.sourcegitcommit: fa90763559239c4c46c5e848939126763879d8e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/13/2022
ms.locfileid: "66992111"
---
# <a name="offboard-a-device-from-microsoft-defender-for-business"></a>Désintégrage d’un appareil à partir de Microsoft Defender pour entreprises

Si vous souhaitez déconnecter un appareil, utilisez l’une des procédures suivantes :

- [Désintégrage d’un appareil Windows](#offboard-a-windows-device)
- [Désintégrage d’un Mac](#offboard-a-mac)

## <a name="offboard-a-windows-device"></a>Désintégrage d’un appareil Windows

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Dans le volet de navigation, choisissez **Paramètres**, puis choisissez **Points de terminaison**.

3. Sous **Gestion des appareils**, choisissez **Retrait**.

4. Sélectionnez un système d’exploitation, tel que **Windows 10 et 11**, puis, sous **Désinscrit un appareil**, dans la section **Méthode de déploiement**, choisissez **Script local**. 

5. Dans l’écran de confirmation, passez en revue les informations, puis choisissez **Télécharger** pour continuer.

6. Sélectionnez **Télécharger le package de retrait** Nous vous recommandons d’enregistrer le package de retrait sur un lecteur amovible.

7. Exécutez le script sur chaque appareil que vous souhaitez déclasser.

## <a name="offboard-a-mac"></a>Désintégrage d’un Mac

1. Accédez à **Applications du finder** > . 

2. Cliquez avec le bouton droit sur **Microsoft Defender pour entreprises**, puis **choisissez Déplacer vers la corbeille**. <br/>--- ou --- <br/> Utilisez la commande suivante : `sudo '/Library/Application Support/Microsoft/Defender/uninstall/uninstall'`.

> [!IMPORTANT]
> Le retrait d’un appareil entraîne l’arrêt de l’envoi de données à Defender pour les PME. Toutefois, les données reçues avant le retrait sont conservées jusqu’à six (6) mois.

## <a name="next-steps"></a>Prochaines étapes

- [Utiliser votre tableau de bord Threat & Vulnerability Management dans Microsoft Defender pour entreprises](mdb-view-tvm-dashboard.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises](mdb-view-edit-create-policies.md)
- [Gérer les appareils dans Microsoft Defender pour entreprises](mdb-manage-devices.md)