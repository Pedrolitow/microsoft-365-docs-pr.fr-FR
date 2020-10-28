---
title: Périphériques VDI (Virtual Desktop Infrastructure) non persistants
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
description: Déployez le package de configuration sur un périphérique VDI (Virtual Desktop Infrastructure) de sorte qu’il soit intégré au service de protection contre la perte de données de point de terminaison Microsoft 365.
ms.openlocfilehash: ce5ad0ba6af3e18a6f6c53e1860fc47a77c38770
ms.sourcegitcommit: 6647055154002c7d3b8f7ce25ad53c9636bc8066
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2020
ms.locfileid: "48769417"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-vdi-devices"></a>Périphériques VDI (Virtual Desktop Infrastructure) non persistants

**S’applique à :**
- [Microsoft 365 protection contre la perte de données (DLP)](/microsoft-365/compliance/endpoint-dlp-learn-about)

- Périphériques VDI (Virtual Desktop Infrastructure)

>[!WARNING]
> Microsoft 365 la prise en charge de la protection contre la perte de données pour Windows Virtual Desktop prend en charge les scénarios à session unique. Les scénarios multisession sur le bureau virtuel Windows ne sont actuellement pas pris en charge.

## <a name="onboard-vdi-devices"></a>Périphériques VDI intégrés

La protection contre la perte de données de point de terminaison Microsoft 365 prend en charge l’intégration de session VDI non persistante. 

>[!Note]
>Pour intégrer des sessions VDI non persistantes, les périphériques VDI doivent être sur Windows 10 1809 ou version ultérieure.

Il peut être associé à des défis lors de l’intégration de VDIs. Les problèmes suivants sont les suivants :

- Intégration instantanée précoce d’une session courte, qui doit être intégrée à la protection contre la perte de données du point de terminaison de Microsoft 365 avant la mise en service réelle.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Les périphériques VDI peuvent apparaître dans le centre de conformité Microsoft 365 :

- Entrée unique pour chaque appareil.  
Notez que dans ce cas, le *même* nom de périphérique doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans assistance.
- Plusieurs entrées pour chaque appareil-un pour chaque session.

Les étapes suivantes vous guident à travers le processus d’intégration des périphériques VDI et mettent en évidence les étapes d’une ou plusieurs entrées.

>[!WARNING]
> Pour les environnements pour lesquels il existe des configurations de ressources faibles, la procédure de démarrage VDI peut ralentir l’intégration de la protection contre la perte de données de point de terminaison de Microsoft 365. 

1.  Ouvrez le fichier. zip du package de configuration VDI ( *DeviceCompliancePackage.zip* ) que vous avez téléchargé à partir de l’Assistant d’intégration de service.

2.  Dans le volet de navigation, sélectionnez **paramètres** d’intégration de l'  >  **appareil**  >  **Onboarding** .

3. Dans le champ **méthode de déploiement** , sélectionnez **scripts d’intégration VDI pour les points de terminaison non persistants** .

5. Cliquez sur **Télécharger le package** et enregistrez le fichier. zip.

6. Copiez les fichiers à partir du dossier DeviceCompliancePackage extrait du fichier. zip dans l' `golden/master` image sous le chemin d’accès `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` . 

7. Si vous n’implémentez pas une seule entrée pour chaque périphérique, copiez DeviceComplianceOnboardingScript. cmd.

8. Si vous implémentez une entrée unique pour chaque périphérique, copiez les Onboard-NonPersistentMachine.ps1 et DeviceComplianceOnboardingScript. cmd.
    
    > [!NOTE]
    > Si le dossier n’apparaît pas `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` , il est peut-être masqué. Vous devez choisir l’option **afficher les fichiers et les dossiers cachés** dans l’Explorateur de fichiers.

9. Ouvrez une fenêtre d’éditeur de stratégie de groupe locale et accédez à configuration de l' **ordinateur**  >  scripts de **Paramètres Windows** -  >  **Scripts**  >  **démarrage** .

   > [!NOTE]
   > La stratégie de groupe de domaine peut également être utilisée pour l’intégration d’appareils VDI non persistants.

4. En fonction de la méthode que vous souhaitez mettre en œuvre, suivez les étapes appropriées :

   **Pour une entrée unique pour chaque appareil**
   
   Sélectionnez l’onglet **scripts PowerShell** , puis cliquez sur **Ajouter** (l’Explorateur Windows s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration plus haut). Naviguez jusqu’à script PowerShell d’intégration `Onboard-NonPersistentMachine.ps1` .
   
   **Pour plusieurs entrées pour chaque périphérique** :
   
   Sélectionnez l’onglet **scripts** , puis cliquez sur **Ajouter** (l’Explorateur Windows s’ouvre directement dans le chemin d’accès où vous avez copié le script d’intégration plus haut). Naviguez jusqu’au script d’intégration `DeviceComplianceOnboardingScript.cmd` .

5. Testez votre solution :

   1. Créez un pool avec un seul appareil.
      
   1. Connectez-vous à l’appareil.
      
   1. Déconnexion de l’appareil.

   1. Connectez-vous à l’appareil avec un autre utilisateur.
      
   1. **Pour une entrée unique pour chaque appareil** : Vérifiez une seule entrée dans le centre de sécurité Microsoft Defender.<br>
      **Pour plusieurs entrées pour chaque périphérique** : Vérifiez plusieurs entrées dans le centre de sécurité Microsoft Defender.

6. Cliquez sur **liste des périphériques** dans le volet de navigation.

7. Utilisez la fonction de recherche en entrant le nom du périphérique et sélectionnez **appareil** comme type de recherche.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour des images VDI (Virtual Desktop Infrastructure) non persistantes
En guise de meilleure pratique, nous vous recommandons d’utiliser les outils de maintenance hors ligne pour corriger les images de référence/des images principales.<br>
Par exemple, vous pouvez utiliser les commandes ci-dessous pour installer une mise à jour alors que l’image reste en mode hors connexion :

```console
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing" 
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Pour plus d’informations sur les commandes DISM et la maintenance hors connexion, reportez-vous aux articles suivants :
- [Modifier une image Windows à l’aide de DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Options de Command-Line de gestion des images DISM](https://docs.microsoft.com/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Réduire la taille du magasin de composants dans une image Windows hors connexion](https://docs.microsoft.com/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Si la maintenance hors connexion n’est pas une option viable pour votre environnement VDI non persistant, les étapes suivantes doivent être prises pour garantir la cohérence et l’intégrité du capteur :

1. Après le démarrage de l’image principale pour la maintenance en ligne ou la mise à jour corrective, exécutez un script par débarquement pour désactiver le capteur de protection contre la perte de données de point de terminaison de Microsoft 365. Pour plus d’informations, consultez [la rubrique débarquement Devices using a local script](dlp-configure-endpoints-script.md#offboard-devices-using-a-local-script).

2. Assurez-vous que le capteur est arrêté en exécutant la commande ci-dessous dans une fenêtre CMD :

   ```console
   sc query sense
   ```

3. Effectuer la maintenance de l’image selon vos besoins.

4. Exécutez les commandes ci-dessous en utilisant PsExec.exe (qui peut être téléchargé à partir du https://download.sysinternals.com/files/PSTools.zip) pour nettoyer le contenu du dossier Cyber que le capteur a pu accumuler depuis le démarrage) :

    ```console
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE “HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Ré-scellez l’image Golden/Master comme vous le feriez normalement.

## <a name="related-topics"></a>Voir aussi
- [Périphériques Windows 10 embarqués à l’aide de la stratégie de groupe](dlp-configure-endpoints-gp.md)
- [Appareils intégrés Windows 10 à l’aide du gestionnaire de configuration de point de terminaison Microsoft](dlp-configure-endpoints-sccm.md)
- [Périphériques Windows 10 intégrés à l’aide des outils de gestion des appareils mobiles](dlp-configure-endpoints-mdm.md)
- [Périphériques Windows 10 embarqués à l’aide d’un script local](dlp-configure-endpoints-script.md)
- [Résoudre les problèmes d’intégration de la protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
