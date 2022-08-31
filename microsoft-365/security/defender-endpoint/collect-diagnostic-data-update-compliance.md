---
title: Collecter des données de diagnostic pour une mise à jour de la conformité de l’antivirus Microsoft Defender
description: Utilisez un outil pour collecter des données afin de résoudre les problèmes de conformité des mises à jour lors de l’utilisation du complément d’évaluation antivirus Microsoft Defender.
keywords: résolution des problèmes, erreur, correctif, conformité des mises à jour, oms, surveiller, rapport, Microsoft Defender AV, Antivirus Microsoft Defender
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.subservice: mde
ms.topic: article
ms.collection: M365-security-compliance
ms.openlocfilehash: b21201d5b3a24c570819ac903eb3a38058c362c8
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67479817"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-antivirus-assessment"></a>Collecter les données de diagnostic de conformité des mises à jour pour l’évaluation de l’antivirus Microsoft Defender


**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Cet article explique comment collecter des données de diagnostic qui peuvent être utilisées par les équipes de support et d’ingénierie Microsoft pour aider à résoudre les problèmes que vous pouvez rencontrer lors de l’utilisation de la section Évaluation de l’antivirus Microsoft Defender dans le complément Mise à jour de conformité.

Avant de tenter ce processus, assurez-vous d’avoir lu [la résolution des problèmes liés aux rapports de l’Antivirus Microsoft Defender](troubleshoot-reporting.md), de respecter toutes les conditions préalables requises et d’effectuer d’autres étapes de dépannage suggérées.

Sur au moins deux appareils qui ne signalent pas ou ne s’affichent pas dans Update Compliance, obtenez le fichier de diagnostic .cab en effectuant les étapes suivantes :

1. Ouvrez une version de niveau administrateur de l’invite de commandes comme suit :

    a. Ouvrez le menu **Démarrer** .

    b. Tapez **cmd**. Cliquez avec le bouton droit sur **l’invite de commandes** , puis **sélectionnez Exécuter en tant qu’administrateur**.

    c. Spécifiez les informations d’identification de l’administrateur ou approuvez l’invite.

2. Accédez au répertoire Windows Defender. Par défaut, cette valeur est `C:\Program Files\Windows Defender`.

3. Tapez la commande suivante, puis **appuyez sur Entrée**

    ```Dos
    mpcmdrun -getfiles
    ```

4. Un fichier .cab est généré et contient différents journaux de diagnostic. L’emplacement du fichier est spécifié dans la sortie de l’invite de commandes. Par défaut, l’emplacement est `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab`.

5. Copiez ces fichiers .cab à un emplacement accessible par le support Microsoft. Par exemple, un dossier OneDrive protégé par mot de passe que vous pouvez partager avec nous.

6. Envoyez un e-mail à l’aide du <a href="mailto:ucsupport@microsoft.com?subject=MDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a">modèle de messagerie de support de conformité des mises à jour</a> et renseignez le modèle avec les informations suivantes :

    ```text
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:

    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes de création de rapports sur l’antivirus Microsoft Defender](troubleshoot-reporting.md)
