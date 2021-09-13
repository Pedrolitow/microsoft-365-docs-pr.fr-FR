---
title: Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.
f1.keywords: NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Déployez le package de configuration sur un appareil vDI (Virtual Desktop Infrastructure) afin qu’il soit intégré au service de protection contre la perte de données Microsoft 365 point de terminaison.
ms.openlocfilehash: 1e4987ba2d261c715395ed1869f597da91b5cfed
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59183607"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Intégrer des périphériques d’infrastructure de bureau virtuel non persistants

**S’applique à :**
- [Microsoft 365 Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)

- Périphériques VDI (Virtual Desktop Infrastructure)

> [!WARNING]
> Microsoft 365 Endpoint data loss prevention support for Windows Virtual Desktop supports single session scenarios. Les scénarios de sessions multiples sur Windows Virtual Desktop ne sont actuellement pas pris en charge.

## <a name="onboard-vdi-devices"></a>Appareils VDI intégrés

Microsoft 365 La protection contre la perte de données de point de terminaison prend en charge l’intégration de session VDI (Virtual Desktop Infrastructure) non persistante.

> [!NOTE]
> Pour intégrer des sessions VDI non persistantes, les appareils VDI doivent être sur Windows 10 1809 ou supérieure.

Il peut y avoir des difficultés associées lors de l’intégration des VDIs. Les défis classiques de ce scénario sont les suivants :

- Intégration anticipée instantanée d’une session de courte durée, qui doit être intégré à Microsoft 365 protection contre la perte de données du point de terminaison avant la mise en service réelle.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Les périphériques VDI peuvent apparaître dans le centre de conformité Microsoft 365 les deux :

- Entrée unique pour chaque appareil.
Notez que dans  ce cas, le même nom d’appareil doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans surveillance.
- Plusieurs entrées pour chaque appareil - une pour chaque session.

Les étapes suivantes vous guident tout au long de l’intégration des appareils VDI et mettent en évidence les étapes pour les entrées simples et multiples.

> [!WARNING]
> Pour les environnements où il existe des configurations de ressources faibles, la procédure de démarrage VDI peut ralentir l’intégration de la protection contre la perte de données Microsoft 365 point de terminaison.

1. Ouvrez le fichier de package de configuration VDI .zip (*DeviceCompliancePackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service.

2. Dans le volet de navigation, sélectionnez **Paramètres** intégration de  >    >  **l’appareil.**

3. Dans le **champ Méthode de** déploiement, sélectionnez les **scripts d’intégration VDI pour les** points de terminaison non persistants.

4. Cliquez **sur Télécharger le package** et enregistrez .zip fichier.

5. Copiez les fichiers du dossier DeviceCompliancePackage extrait du fichier .zip dans l’image sous `golden/master` le chemin d’accès. `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`

6. Si vous n’implémentez pas une seule entrée pour chaque appareil, copiez DeviceComplianceOnboardingScript.cmd.

7. Si vous implémentez une entrée unique pour chaque appareil, copiez à la fois Onboard-NonPersistentMachine.ps1 et DeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > Si vous ne voyez pas le `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` dossier, il peut être masqué. Vous devez choisir l’option Afficher les fichiers **et dossiers masqués** dans l’Explorateur de fichiers.

8. Ouvrez une fenêtre Éditeur de stratégie de groupe locale et accédez à **Configuration** ordinateur  >  **Windows Paramètres**  >  **scripts de**  >  **démarrage.**

   > [!NOTE]
   > La stratégie de groupe de domaine peut également être utilisée pour l’intégration d’appareils VDI non persistants.

9. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :

   **Pour une entrée unique pour chaque appareil**

   Sélectionnez **l’onglet Scripts PowerShell,** puis cliquez sur Ajouter **(Windows** Explorer s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script PowerShell `Onboard-NonPersistentMachine.ps1` d’intégration.

   **Pour plusieurs entrées pour chaque appareil**:

   Sélectionnez **l’onglet Scripts,** puis cliquez sur Ajouter **(Windows** Explorer s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment). Accédez au script Bash `DeviceComplianceOnboardingScript.cmd` d’intégration.

10. Testez votre solution :
    1. Créez un pool avec un seul appareil.
    1. Logon à l’appareil.
    1. Ffage de la logo à partir de l’appareil.
    1. Se rendre sur l’appareil avec un autre utilisateur.
    1. **Pour une entrée unique pour chaque appareil :** vérifiez une seule entrée dans Centre de sécurité Microsoft Defender.
       **Pour plusieurs entrées pour chaque appareil :** vérifiez plusieurs entrées dans Centre de sécurité Microsoft Defender.

11. Cliquez **sur La liste Appareils** dans le volet de navigation.

12. Utilisez la fonction de recherche en entrant le nom de l’appareil et **sélectionnez Appareil** comme type de recherche.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour d’images VDI (Virtual Desktop Infrastructure) non persistantes

En tant que meilleure pratique, nous vous recommandons d’utiliser des outils de maintenance hors connexion pour mettre à jour les images de base/de base.

Par exemple, vous pouvez utiliser les commandes ci-dessous pour installer une mise à jour pendant que l’image reste hors connexion :

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Pour plus d’informations sur les commandes DISM et la maintenance hors connexion, consultez les articles ci-dessous :

- [Modifier une image Windows à l’aide de DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Options de gestion des images DISM Command-Line d’images](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Réduire la taille du magasin de composants dans une image de Windows hors connexion](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Si la maintenance hors connexion n’est pas une option viable pour votre environnement VDI non persistant, les étapes suivantes doivent être prises pour garantir la cohérence et l’état du capteur :

1. Après avoir démarré l’image maître pour la maintenance en ligne ou la correction, exécutez un script de mise hors service pour désactiver le capteur de protection contre la perte de données Microsoft 365 point de terminaison. Pour plus d’informations, voir [Les appareils hors-carte à l’aide d’un script local.](dlp-configure-endpoints-script.md#offboard-devices-using-a-local-script)

2. Assurez-vous que le capteur est arrêté en exécutant la commande ci-dessous dans une fenêtre CMD :

   ```console
   sc query sense
   ```

3. Service de l’image selon les besoins.

4. Exécutez les commandes ci-dessous à l’aide PsExec.exe (qui peut être téléchargé à partir de pour nettoyer le contenu du dossier cyber que le capteur a peut-être cumulé https://download.sysinternals.com/files/PSTools.zip) depuis le démarrage :

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Rescellez l’image de premier plan comme vous le feriez normalement.

## <a name="related-topics"></a>Rubriques connexes

- [Intégrer des Windows 10 à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Intégrer Windows 10 appareils à l’aide Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](dlp-configure-endpoints-script.md)
- [Résoudre les problèmes d’intégration de la Protection avancée contre les menaces Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
