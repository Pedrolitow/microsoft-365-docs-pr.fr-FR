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
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
description: Déployez le package de configuration sur un appareil vDI (Virtual Desktop Infrastructure) afin qu’il soit intégré au service de protection contre la perte de données de point de terminaison.
ms.openlocfilehash: 8a54d4ce3cfb4b3ba6571f2aee63cd60c2a6d71f
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66636136"
---
# <a name="onboard-non-persistent-virtual-desktop-infrastructure-devices"></a>Intégrer des appareils d’infrastructure de bureau virtuel non persistants

**S’applique à :**

- [Protection contre la perte de données (DLP) de point de terminaison](./endpoint-dlp-learn-about.md)
- [Gestion des risques internes](insider-risk-management.md)

- Appareils vDI (Virtual Desktop Infrastructure)

> [!WARNING]
> La prise en charge de la protection contre la perte de données de point de terminaison pour Windows Virtual Desktop prend en charge les scénarios de session unique. Les scénarios multisession sur Windows Virtual Desktop ne sont actuellement pas pris en charge.

## <a name="onboard-vdi-devices"></a>Intégrer des appareils VDI

Microsoft 365 prend en charge l’intégration de sessions d’infrastructure de bureau virtuel (VDI) non persistantes.

> [!NOTE]
> Pour intégrer des sessions VDI non persistantes, les appareils VDI doivent être sur Windows 10 1809 ou une version ultérieure.

Il peut y avoir des défis associés lors de l’intégration des VDIs. Voici les défis classiques de ce scénario :

- Intégration anticipée instantanée de sessions de courte durée, qui doivent être intégrées à Microsoft 365 avant l’approvisionnement réel.
- Le nom de l’appareil est généralement réutilisé pour les nouvelles sessions.

Les appareils VDI peuvent apparaître dans le portail de conformité Microsoft Purview comme suit :

- Entrée unique pour chaque appareil.
Notez que dans ce cas, le *même* nom d’appareil doit être configuré lors de la création de la session, par exemple à l’aide d’un fichier de réponses sans assistance.
- Plusieurs entrées pour chaque appareil , une pour chaque session.

Les étapes suivantes vous guident tout au long de l’intégration des appareils VDI et mettent en surbrillance les étapes pour les entrées uniques et multiples.

> [!WARNING]
> Pour les environnements où les configurations de ressources sont faibles, la procédure de démarrage VDI peut ralentir le processus d’intégration de l’appareil.

1. Obtenez le fichier .zip du package de configuration VDI (*DeviceCompliancePackage.zip*) à partir de [portail de conformité Microsoft Purview](https://compliance.microsoft.com).

2. Dans le volet de navigation, sélectionnez **Paramètres** > **Intégration de l’appareil** > **.**

3. Dans le champ **Méthode de déploiement** , sélectionnez les **scripts d’intégration VDI pour les points de terminaison non persistants**.

4. Cliquez sur **Télécharger le package** et enregistrez le fichier .zip.

5. Copiez les fichiers du dossier DeviceCompliancePackage extrait du fichier .zip dans l’image `golden` sous le chemin d’accès `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup`.

6. Si vous n’implémentez pas une seule entrée pour chaque appareil, copiez DeviceComplianceOnboardingScript.cmd.

7. Si vous implémentez une entrée unique pour chaque appareil, copiez Onboard-NonPersistentMachine.ps1 et DeviceComplianceOnboardingScript.cmd.

    > [!NOTE]
    > Si vous ne voyez pas le `C:\WINDOWS\System32\GroupPolicy\Machine\Scripts\Startup` dossier, il peut être masqué. Vous devez choisir l’option **Afficher les fichiers et dossiers masqués** dans Explorateur de fichiers.

8. Ouvrez une fenêtre d’éditeur de stratégie de groupe local et accédez au **démarrage** **des scripts de paramètres** >  >  Windows **de configuration** >  de l’ordinateur.

   > [!NOTE]
   > Les stratégie de groupe de domaine peuvent également être utilisées pour intégrer des appareils VDI non persistants.

9. Selon la méthode que vous souhaitez implémenter, suivez les étapes appropriées :

   **Pour une entrée unique pour chaque appareil**

   Sélectionnez l’onglet **Scripts PowerShell** , puis cliquez sur **Ajouter** (l’Explorateur Windows s’ouvre directement dans le chemin où vous avez copié le script d’intégration précédemment). Accédez au script `Onboard-NonPersistentMachine.ps1`PowerShell d’intégration.

   **Pour plusieurs entrées pour chaque appareil** :

   Sélectionnez l’onglet **Scripts** , puis cliquez sur **Ajouter** (l’Explorateur Windows s’ouvre directement dans le chemin où vous avez copié le script d’intégration précédemment). Accédez au script `DeviceComplianceOnboardingScript.cmd`Bash d’intégration.

10. Testez votre solution :
    1. Créez un pool avec un seul appareil.
    1. Connectez-vous à l’appareil.
    1. Déconnectez-vous de l’appareil.
    1. Connectez-vous à l’appareil avec un autre utilisateur.
    1. **Pour une entrée unique pour chaque appareil** : vérifiez une seule entrée dans Centre de sécurité Microsoft Defender.
       **Pour plusieurs entrées pour chaque appareil** : vérifiez plusieurs entrées dans Centre de sécurité Microsoft Defender.

11. Cliquez sur **La liste Appareils** dans le volet de navigation.

12. Utilisez la fonction de recherche en entrant le nom de l’appareil et en sélectionnant **Appareil** comme type de recherche.

## <a name="updating-non-persistent-virtual-desktop-infrastructure-vdi-images"></a>Mise à jour d’images d’infrastructure de bureau virtuel (VDI) non persistantes

En guise de bonne pratique, nous vous recommandons d’utiliser des outils de maintenance hors connexion pour corriger les images d’or.

Par exemple, vous pouvez utiliser les commandes ci-dessous pour installer une mise à jour pendant que l’image reste hors connexion :

```DOS
DISM /Mount-image /ImageFile:"D:\Win10-1909.vhdx" /index:1 /MountDir:"C:\Temp\OfflineServicing"
DISM /Image:"C:\Temp\OfflineServicing" /Add-Package /Packagepath:"C:\temp\patch\windows10.0-kb4541338-x64.msu"
DISM /Unmount-Image /MountDir:"C:\Temp\OfflineServicing" /commit
```

Pour plus d’informations sur les commandes DISM et la maintenance hors connexion, reportez-vous aux articles ci-dessous :

- [Modifier une image Windows à l’aide de DISM](/windows-hardware/manufacture/desktop/mount-and-modify-a-windows-image-using-dism)
- [Options de Command-Line de gestion des images DISM](/windows-hardware/manufacture/desktop/dism-image-management-command-line-options-s14)
- [Réduire la taille du magasin de composants dans une image Windows hors connexion](/windows-hardware/manufacture/desktop/reduce-the-size-of-the-component-store-in-an-offline-windows-image)

Si la maintenance hors connexion n’est pas une option viable pour votre environnement VDI non persistant, vous devez effectuer les étapes suivantes pour garantir la cohérence et l’intégrité des capteurs :

1. Après avoir démarré l’image d’or pour la maintenance ou la mise à jour corrective en ligne, exécutez un script de désintégrage pour désactiver le capteur de surveillance des appareils Microsoft 365. Pour plus d’informations, consultez [Offboard devices using a local script](device-onboarding-script.md#offboard-devices-using-a-local-script).

2. Vérifiez que le capteur est arrêté en exécutant la commande ci-dessous dans une fenêtre CMD :

   ```DOS
   sc query sense
   ```

3. Service de l’image en fonction des besoins.

4. Exécutez les commandes ci-dessous à l’aide de PsExec.exe (qui peuvent être téléchargées https://download.sysinternals.com/files/PSTools.zip) pour nettoyer le contenu du dossier cyber que le capteur a pu accumuler depuis le démarrage :

    ```DOS
    PsExec.exe -s cmd.exe
    cd "C:\ProgramData\Microsoft\Windows Defender Advanced Threat Protection\Cyber"
    del *.* /f /s /q
    REG DELETE "HKLM\SOFTWARE\Microsoft\Windows Advanced Threat Protection" /v senseGuid /f
    exit
    ```

5. Refermez l’image dorée comme vous le feriez normalement.

## <a name="related-topics"></a>Rubriques connexes

- [Intégrer des appareils Windows 10 et Windows 11 à l’aide de stratégie de groupe](device-onboarding-gp.md)
- [Intégrer des appareils Windows 10 et Windows 11 à l’aide de Microsoft Endpoint Configuration Manager](device-onboarding-sccm.md)
- [Intégrer les appareils Windows 10 et Windows 11 à l’aide des outils de gestion des périphériques mobiles](device-onboarding-mdm.md)
- [Intégrer les appareils Windows 10 et Windows 11 en utilisant un script local](device-onboarding-script.md)
- [Résoudre les problèmes d’intégration de Microsoft Defender Advanced Threat Protection](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding)
