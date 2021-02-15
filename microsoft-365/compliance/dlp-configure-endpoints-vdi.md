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
description: Déployez le package de configuration sur un appareil VDI (Virtual Desktop Infrastructure) afin qu’il soit intégré au service de protection contre la perte de données de point de terminaison Microsoft 365.
ms.openlocfilehash: ce5ad0ba6af3e18a6f6c53e1860fc47a77c38770
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769417"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Intégrer les ordinateurs virtuels d’infrastructure de bureau virtuel (VDI) non persistants.

**S’applique à :**
- [Protection contre la perte de données de point de terminaison Microsoft 365 (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)

- Périphériques VDI (Virtual Desktop Infrastructure)

>[!WARNING]
> La prise en charge de la protection contre la perte de données de point de terminaison Microsoft 365 pour Windows Virtual Desktop prend en charge les scénarios de session unique. Les scénarios à sessions multiples sur Windows Virtual Desktop ne sont actuellement pas pris en charge.

## <a name="onboard-vdi-devices"></a>Appareils VDI intégrés

La protection contre la perte de données de point de terminaison Microsoft 365 prend en charge l’intégration de session VDI non persistante. 

>[!Note]
>Pour intégrer des sessions VDI non persistantes, les appareils VDI doivent être sur Windows 10 1809 ou une autre.

Il peut y avoir des difficultés associées lors de l’intégration des VDIs. Les défis classiques de ce scénario sont les suivants :

- Intégration anticipée instantanée d’une session de courte durée, qui doit être intégré à la protection contre la perte de données du point de terminaison Microsoft 365 avant la mise en service réelle.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Les appareils VDI peuvent apparaître dans le Centre de conformité Microsoft 365 sous la forme :

- Entrée unique pour chaque appareil.  
Notez que dans  ce cas, le même nom d’appareil doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans surveillance.
- Plusieurs entrées pour chaque appareil - une pour chaque session.

Les étapes suivantes vous guident tout au long de l’intégration des appareils VDI et mettent en évidence les étapes pour les entrées simples et multiples.

>[!WARNING]
> Pour les environnements où les configurations de ressources sont faibles, la procédure de démarrage VDI peut ralentir l’intégration de protection contre la perte de données de point de terminaison Microsoft 365. 

1.  Ouvrez le fichier .zip du package de configuration VDI (*DeviceCompliancePackage.zip*) que vous avez téléchargé à partir de l’Assistant d’intégration de service.

2.  Dans le volet de navigation, sélectionnez **Paramètres**  >  **Intégration de l’appareil.**  >  

3. Dans le **champ Méthode de** déploiement, sélectionnez les **scripts d’intégration VDI pour les** points de terminaison non persistants.

5. Cliquez **sur Télécharger le package** et enregistrez le fichier .zip.

6. Copiez les fichiers du dossier DeviceCompliancePackage extrait du fichier .zip dans l’image sous `golden/master` le chemin d’accès. `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` 

7. Si vous n’implémentez pas une seule entrée pour chaque appareil, copiez DeviceComplianceOnboardingScript.cmd.

8. Si vous implémentez une entrée unique pour chaque appareil, copiez à la fois Onboard-NonPersistentMachine.ps1 et DeviceComplianceOnboardingScript.cmd.
    
    > [!NOTE]
    > Si vous ne voyez pas le `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` dossier, il peut être masqué. Vous devez choisir l’option Afficher les fichiers **et dossiers masqués** dans l’Explorateur de fichiers.

9. Ouvrez une fenêtre Éditeur de stratégie de groupe locale et accédez au démarrage des scripts de  >  **paramètres Windows** de configuration  >    >  **ordinateur.**

   > [!NOTE]
   > La stratégie de groupe de domaine peut également être utilisée pour l’intégration d’appareils VDI non persistants.

4. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :

   **Pour une entrée unique pour chaque appareil**
   
   Sélectionnez **l’onglet Scripts PowerShell,** puis cliquez sur Ajouter (l’Explorateur Windows s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment).  Accédez au script PowerShell `Onboard-NonPersistentMachine.ps1` d’intégration.
   
   **Pour plusieurs entrées pour chaque appareil**:
   
   Sélectionnez **l’onglet Scripts,** puis cliquez sur Ajouter (l’Explorateur Windows s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration précédemment).  Accédez au script Bash `DeviceComplianceOnboardingScript.cmd` d’intégration.

5. Testez votre solution :

   1. Créez un pool avec un seul appareil.
      
   1. Se logo à l’appareil.
      
   1. Ffage de la logo à partir de l’appareil.

   1. Se rendre sur l’appareil avec un autre utilisateur.
      
   1. **Pour une entrée unique pour chaque appareil :** vérifiez une seule entrée dans le Centre de sécurité Microsoft Defender.<br>
      **Pour plusieurs entrées pour chaque appareil :** vérifiez plusieurs entrées dans le Centre de sécurité Microsoft Defender.

6. Cliquez **sur La liste Appareils** dans le volet de navigation.

7. Utilisez la fonction de recherche en entrant le nom de l’appareil et sélectionnez **Appareil** comme type de recherche.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour d’images DDI (Virtual Desktop Infrastructure) non persistantes
En tant que meilleure pratique, nous vous recommandons d’utiliser des outils de maintenance hors connexion pour mettre à jour les images de base/de base.<br>
Par exemple, vous pouvez utiliser les commandes ci-dessous pour installer une mise à jour pendant que l’image reste hors connexion :

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing" 
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Pour plus d’informations sur les commandes DISM et la maintenance hors connexion, consultez les articles ci-dessous :
- [Modifier une image Windows à l’aide de DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Options de gestion des images DISM Command-Line d’images](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Réduire la taille du magasin de composants dans une image Windows hors connexion](https://docs.microsoft.com/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Si la maintenance hors connexion n’est pas une option viable pour votre environnement VDI non persistant, les étapes suivantes doivent être prises pour garantir la cohérence et l’état du capteur :

1. Après avoir démarré l’image maître pour la maintenance en ligne ou la correction, exécutez un script de mise hors service pour désactiver le capteur de protection contre la perte de données du point de terminaison Microsoft 365. Pour plus d’informations, voir [Les appareils hors-carte à l’aide d’un script local.](dlp-configure-endpoints-script.md#offboard-devices-using-a-local-script)

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
- [Intégrer des appareils Windows 10 à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Intégrer des appareils Windows 10 à l’aide de Microsoft Endpoint Configuration Manager](dlp-configure-endpoints-sccm.md)
- [Intégrer les appareils Windows 10 à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Intégrer les appareils Windows 10 utilisant un script local](dlp-configure-endpoints-script.md)
- [Résoudre les problèmes d’intégration de microsoft Defender - Protection avancée contre les menaces](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
