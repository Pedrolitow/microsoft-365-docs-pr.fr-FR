---
title: Collecter des données de diagnostic pour la conformité des mises à jour et les Windows Defender Antivirus Microsoft Defender
description: Utiliser un outil pour collecter des données afin de résoudre les problèmes de conformité des mises à jour lors de l’utilisation du Antivirus Microsoft Defender’évaluation
keywords: résoudre les problèmes, erreur, corriger, mettre à jour la conformité, oms, surveiller, signaler, Microsoft Defender AV
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.custom: nextgen
ms.date: 09/03/2018
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 273dc08dd3778451f14f9c78c984be8affc2d8fd
ms.sourcegitcommit: ea4bc3b005d86b029700e56015a47b8cc6dca2a1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2021
ms.locfileid: "58510012"
---
# <a name="collect-update-compliance-diagnostic-data-for-microsoft-defender-antivirus-assessment"></a>Collecter des données de diagnostic de conformité de mise à jour pour Antivirus Microsoft Defender évaluation


**S’applique à :**

- [Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/)

Cet article explique comment collecter des données de diagnostic qui peuvent être utilisées par le support microsoft et les équipes d’ingénierie pour vous aider à résoudre les problèmes que vous pouvez rencontrer lors de l’utilisation de la section évaluation Antivirus Microsoft Defender dans le module de conformité des mises à jour.

Avant d’essayer ce processus, assurez-vous que vous avez lu résolution des problèmes Antivirus Microsoft Defender [rapports,](troubleshoot-reporting.md)satisfait à toutes les conditions préalables requises et pris les autres suggestions de procédures de dépannage.

Sur au moins deux appareils qui ne sont pas signalés ou qui s’affichent dans Update Compliance, obtenez le fichier de diagnostic .cab en suivant les étapes suivantes :

1. Ouvrez une version de niveau administrateur de l’invite de commandes comme suit :

    a. Ouvrez **le** menu Démarrer.

    b. Tapez **cmd**. Cliquez avec le bouton droit sur **l’invite de** commandes, puis **sélectionnez Exécuter en tant qu’administrateur.**

    c. Spécifiez les informations d’identification de l’administrateur ou approuvez l’invite.

2. Accédez au répertoire Windows Defender de recherche. Par défaut, cette valeur est `C:\Program Files\Windows Defender`.

3. Tapez la commande suivante, puis appuyez sur **Entrée**

    ```Dos
    mpcmdrun -getfiles
    ```

4. Un .cab de diagnostic qui contient divers journaux de diagnostic est généré. L’emplacement du fichier est spécifié dans la sortie de l’invite de commandes. Par défaut, l’emplacement est `C:\ProgramData\Microsoft\Windows Defender\Support\MpSupportFiles.cab` .

5. Copiez ces .cab vers un emplacement accessible par le support Microsoft. Par exemple, il peut s’agit d’un dossier OneDrive protégé par mot de passe que vous pouvez partager avec nous.

6. Envoyez un courrier <a href="mailto:ucsupport@microsoft.com?subject=MDAV assessment issue&body=I%20am%20encountering%20the%20following%20issue%20when%20using%20Windows%20Defender%20AV%20in%20Update%20Compliance%3a%20%0d%0aI%20have%20provided%20at%20least%202%20support%20.cab%20files%20at%20the%20following%20location%3a%20%3Caccessible%20share%2c%20including%20access%20details%20such%20as%20password%3E%0d%0aMy%20OMS%20workspace%20ID%20is%3a%20%0d%0aPlease%20contact%20me%20at%3a"></a>électronique à l’aide du modèle de courrier électronique de prise en charge de la conformité des mises à jour et remplissez le modèle avec les informations suivantes :

    ```text
    I am encountering the following issue when using Microsoft Defender Antivirus in Update Compliance:

    I have provided at least 2 support .cab files at the following location: <accessible share, including access details such as password>

    My OMS workspace ID is:

    Please contact me at:
    ```

## <a name="see-also"></a>Voir aussi

- [Résoudre les problèmes de Windows Defender Antivirus Microsoft Defender rapports](troubleshoot-reporting.md)
