---
title: Activer la protection du réseau
description: Activez la protection réseau avec stratégie de groupe, PowerShell ou Mobile Gestion des appareils et Configuration Manager.
keywords: Protection réseau, exploits, site web malveillant, ip, domaine, domaines, activer, activer
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: conceptual
author: denisebmsft
ms.author: deniseb
ms.reviewer: mkaminska
manager: dansimp
ms.subservice: mde
ms.collection: m365-security-compliance
ms.date: ''
search.appverid: met150
ms.openlocfilehash: 731f8215a3b22ebf7569930d40dc0a39ff1f00c3
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67690463"
---
# <a name="turn-on-network-protection"></a>Activer la protection du réseau

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**

- Windows
- Linux \(Afficher la [protection réseau pour Linux](network-protection-linux.md)\)
- macOS \(Afficher la [protection réseau pour macOS](network-protection-macos.md)\)

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

[La protection réseau](network-protection.md) permet d’empêcher les employés d’utiliser n’importe quelle application pour accéder à des domaines dangereux susceptibles d’héberger des escroqueries, des exploits et d’autres contenus malveillants sur Internet. Vous pouvez [auditer la protection réseau](evaluate-network-protection.md) dans un environnement de test pour voir quelles applications seraient bloquées avant d’activer la protection réseau.

[En savoir plus sur les options de configuration du filtrage réseau.](/mem/intune/protect/endpoint-protection-windows-10#network-filtering)

## <a name="check-if-network-protection-is-enabled"></a>Vérifier si la protection réseau est activée

Vérifiez si la protection réseau a été activée sur un appareil local à l’aide de l’éditeur du Registre.

1. Sélectionnez le bouton **Démarrer** dans la barre des tâches et tapez **regedit** pour ouvrir l’éditeur du Registre.

2. Choisissez **HKEY_LOCAL_MACHINE** dans le menu latéral.

3. Parcourez les menus imbriqués pour accéder aux stratégies **LOGICIELLEs** \>  \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

Si la clé est manquante, accédez à **SOFTWARE** \> **Microsoft** \> **Windows Defender** \> **Windows Defender Exploit Guard** \> **Network Protection**.

4. Sélectionnez **EnableNetworkProtection** pour voir l’état actuel de la protection réseau sur l’appareil :

   - 0, ou **désactivé**
   - 1 ou **activé**
   - 2, ou mode **Audit**

    :::image type="content" source="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png" alt-text="Clé de Registre De protection réseau" lightbox="../../media/95341270-b738b280-08d3-11eb-84a0-16abb140c9fd.png":::

## <a name="enable-network-protection"></a>Activer la protection réseau

Activez la protection réseau à l’aide de l’une des méthodes suivantes :

- [PowerShell](#powershell)
- [Gestion des périphériques mobiles (GPM)](#mobile-device-management-mdm)
- [Microsoft Endpoint Manager](#microsoft-endpoint-manager)
- [Stratégie de groupe](#group-policy)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)

### <a name="powershell"></a>PowerShell

1. Tapez **powershell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**.

2. Entrez l’applet de commande suivante :

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection Enabled
    ```

3. Facultatif : activez la fonctionnalité en mode audit à l’aide de l’applet de commande suivante :

    ```PowerShell
    Set-MpPreference -EnableNetworkProtection AuditMode
    ```

    Utilisez `Disabled` plutôt ou `AuditMode` `Enabled` désactivez la fonctionnalité.

### <a name="mobile-device-management-mdm"></a>Gestion des périphériques mobiles (GPM)

Utilisez le fournisseur de services de configuration (CSP) [./Vendor/MSFT/Policy/Config/Defender/EnableNetworkProtection](/windows/client-management/mdm/policy-csp-defender) pour activer ou désactiver la protection réseau ou activer le mode d’audit.

[Mettez à jour la plateforme anti-programme malveillant Microsoft Defender vers la dernière version](https://support.microsoft.com/topic/update-for-microsoft-defender-antimalware-platform-92e21611-8cf1-8e0e-56d6-561a07d144cc) avant d’activer ou de désactiver la protection réseau ou d’activer le mode d’audit.

### <a name="microsoft-endpoint-manager"></a>Microsoft Endpoint Manager

#### <a name="microsoft-defender-for-endpoint-baseline-method"></a>méthode de base de référence Microsoft Defender pour point de terminaison

1. Connectez-vous au Centre d’administration Microsoft Endpoint Manager (https://endpoint.microsoft.com).
2. Accédez aux **bases de référence de sécurité** >  des  >  points de terminaison **Microsoft Defender pour point de terminaison Base de référence**.
3. Sélectionnez **Créer un profil**, fournissez un nom pour votre profil, puis sélectionnez **Suivant**.
4. Dans la section **Paramètres de configuration** , accédez aux **règles de réduction de la surface d’attaque** > définir **Bloquer**, **Activer** ou **Auditer** pour **activer la protection réseau**. Sélectionnez **Suivant**.
5. Sélectionnez les **balises d’étendue** et **les affectations** appropriées selon les besoins de votre organisation.
7. Passez en revue toutes les informations, puis **sélectionnez Créer**.

#### <a name="antivirus-policy-method"></a>Méthode de stratégie antivirus
1. Connectez-vous au Centre d’administration Microsoft Endpoint Manager (https://endpoint.microsoft.com).
2. Accéder à **l’antivirus de sécurité de point de terminaison** > 
3. Sélectionner **Créer une stratégie**
4. Dans le menu volant **Créer une stratégie**, choisissez **Windows 10, Windows 11 et Windows Server** dans la liste **des plateformes**.
5. Choisissez **l’antivirus Microsoft Defender** dans la liste **des profils** , puis choisissez **Créer**
6. Indiquez un nom pour votre profil, puis sélectionnez **Suivant**.
7. Dans la section **Paramètres de configuration** , sélectionnez **Désactivé**, **Activé (mode bloc)** ou **Activé (mode audit)** pour **Activer la protection réseau**, puis **Suivant**.
8. Sélectionnez les **affectations** et **balises d’étendue** appropriées, selon les besoins de votre organisation.
9. Passez en revue toutes les informations, puis **sélectionnez Créer**.

#### <a name="configuration-profile-method"></a>Méthode de profil de configuration

1. Connectez-vous au Centre d’administration Microsoft Endpoint Manager (https://endpoint.microsoft.com).

2. Allez dans **Appareils** > **Profils de configuration** > **Créer un profil**.

3. Dans le menu volant **Créer un profil** , sélectionnez **Plateforme** et choisissez le **type de profil** en tant que **modèles**.

4. Dans le **nom du modèle**, choisissez **Endpoint Protection** dans la liste des modèles, puis sélectionnez **Créer**.

4. Accédez à **Endpoint Protection** > **Basics**, indiquez un nom pour votre profil, puis sélectionnez **Suivant**.

5. Dans la section **Paramètres de configuration** , accédez à **Microsoft Defender Exploit Guard** > **Network filtering** > **Network protection** > **Enable** or **Audit**. Sélectionnez **Suivant**.

6. Sélectionnez les **balises d’étendue**, **les affectations** et **les règles d’applicabilité** appropriées, selon les besoins de votre organisation. Les administrateurs peuvent définir d’autres exigences.

7. Passez en revue toutes les informations, puis **sélectionnez Créer**.

### <a name="group-policy"></a>Stratégie de groupe

Utilisez la procédure suivante pour activer la protection réseau sur les ordinateurs joints à un domaine ou sur un ordinateur autonome.

1. Sur un ordinateur autonome, **accédez à Démarrer** , puis tapez et **sélectionnez Modifier la stratégie de groupe**.

    *-Ou-*

    Sur un ordinateur de gestion stratégie de groupe joint à un domaine, ouvrez la [console de gestion stratégie de groupe](https://technet.microsoft.com/library/cc731212.aspx), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence sur **les composants** \> Windows **antivirus** \> Microsoft Defender **Windows Defender protection du réseau Exploit Guard**\>.

   > [!NOTE]
   > Sur les versions antérieures de Windows, le chemin de stratégie de groupe peut indiquer « Antivirus Windows Defender » au lieu de « Antivirus Microsoft Defender ».

4. Double-cliquez sur le paramètre **Empêcher les utilisateurs et les applications d’accéder aux sites web dangereux** et définissez l’option **sur Activé**. Dans la section Options, vous devez spécifier l’une des options suivantes :
    - **Bloquer** : les utilisateurs ne peuvent pas accéder à des adresses IP et des domaines malveillants.
    - **Désactiver (par défaut)** : la fonctionnalité de protection réseau ne fonctionnera pas. Les utilisateurs ne seront pas bloqués pour accéder à des domaines malveillants.
    - **Mode Audit** : si un utilisateur visite une adresse IP ou un domaine malveillant, un événement est enregistré dans le journal des événements Windows. Toutefois, l’utilisateur ne sera pas bloqué pour accéder à l’adresse.

   > [!IMPORTANT]
   > Pour activer entièrement la protection réseau, vous devez définir l’option stratégie de groupe **sur Activé** et également sélectionner **Bloquer** dans le menu déroulant options.

   > [!NOTE]
   > Facultatif : suivez les étapes décrites dans [Vérifier si la protection réseau est activée](#check-if-network-protection-is-enabled) pour vérifier que vos paramètres de stratégie de groupe sont corrects.

### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Ouvrez la console Gestionnaire de configuration.

2. Accédez à **Assets and Compliance** > **Endpoint Protection** >  **Windows Defender Exploit Guard**.

3. Sélectionnez **Créer une stratégie Exploit Guard** dans le ruban pour créer une stratégie.
   - Pour modifier une stratégie existante, sélectionnez la stratégie, puis sélectionnez **Propriétés** dans le ruban ou dans le menu contextuel. Modifiez l’option **Configurer la protection réseau** à partir de l’onglet **Protection réseau** .  

4. Dans la page **Général** , spécifiez un nom pour la nouvelle stratégie et vérifiez que l’option **de protection réseau** est activée.

5. Dans la page **Protection réseau** , sélectionnez l’un des paramètres suivants pour l’option **Configurer la protection réseau** :
   - **Bloquer**
   - **Audit**
   - **Disabled**

6. Effectuez le reste des étapes et enregistrez la stratégie.

7. Dans le ruban, sélectionnez **Déployer** pour déployer la stratégie sur un regroupement.

> [!IMPORTANT]
> Une fois que vous avez déployé une stratégie Exploit Guard à partir de Configuration Manager, les paramètres Exploit Guard ne seront pas supprimés des clients si vous supprimez le déploiement. `Delete not supported`est enregistré dans le fichier ExploitGuardHandler.log du client Configuration Manager si vous supprimez le déploiement d’Exploit Guard du client. <!--CMADO8538577-->
> Le script PowerShell suivant peut être exécuté dans le contexte SYSTEM pour supprimer ces paramètres :<!--CMADO9907132-->
>
> ```powershell
> $defenderObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_Defender02" -Filter "InstanceID='Defender' and ParentID='./Vendor/MSFT/Policy/Config'"
> $defenderObject.AttackSurfaceReductionRules = $null
> $defenderObject.AttackSurfaceReductionOnlyExclusions = $null
> $defenderObject.EnableControlledFolderAccess = $null
> $defenderObject.ControlledFolderAccessAllowedApplications = $null
> $defenderObject.ControlledFolderAccessProtectedFolders = $null
> $defenderObject.EnableNetworkProtection = $null
> $defenderObject.Put()
>
> $exploitGuardObject = Get-WmiObject -Namespace "root/cimv2/mdm/dmmap" -Class "MDM_Policy_Config01_ExploitGuard02" -Filter "InstanceID='ExploitGuard' and ParentID='./Vendor/MSFT/Policy/Config'"
> $exploitGuardObject.ExploitProtectionSettings = $null
> $exploitGuardObject.Put()
>```  

## <a name="see-also"></a>Voir aussi

- [Protection du réseau](network-protection.md)

- [Protection réseau pour Linux](network-protection-linux.md)

- [Protection réseau pour macOS](network-protection-macos.md)

- [Protection réseau et liaison TCP triple](network-protection.md#network-protection-and-the-tcp-three-way-handshake)

- [Évaluer la protection du réseau](evaluate-network-protection.md)

- [Résoudre les problèmes de protection réseau](troubleshoot-np.md)
