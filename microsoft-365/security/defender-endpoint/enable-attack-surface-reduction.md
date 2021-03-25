---
title: Activer les règles de réduction de la surface d’attaque
description: Activez les règles de réduction de la surface d’attaque (ASR) pour protéger vos appareils contre les attaques qui utilisent des macros, des scripts et des techniques d’injection courantes.
keywords: Réduction de la surface d’attaque, système de prévention des intrusions hôtes, règles de protection, anti-attaque, attaque, prévention des infections, activer, activer
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
audience: ITPro
author: levinec
ms.author: ellevin
ms.reviewer: ''
manager: dansimp
ms.technology: mde
ms.openlocfilehash: 1deec767c6af777b23ab5a91c9e719f690e0c048
ms.sourcegitcommit: 2a708650b7e30a53d10a2fe3164c6ed5ea37d868
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2021
ms.locfileid: "51165140"
---
# <a name="enable-attack-surface-reduction-rules"></a>Activer les règles de réduction de la surface d’attaque

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

>Vous souhaitez faire l’expérience de Defender for Endpoint ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

[Les règles de réduction de la surface](attack-surface-reduction.md) d’attaque (règles de réduction de la surface d’attaque) permettent d’éviter les actions que les programmes malveillants abusent souvent pour compromettre les appareils et les réseaux. Vous pouvez définir des règles de asr pour les appareils exécutant l’une des éditions et versions suivantes de Windows :
- Windows 10 Professionnel, [version 1709 ou](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows 10 Entreprise, [version 1709 ou](https://docs.microsoft.com/windows/whats-new/whats-new-windows-10-version-1709) ultérieure
- Windows Server, [version 1803 (canal semi-annuel)](https://docs.microsoft.com/windows-server/get-started/whats-new-in-windows-server-1803) ou version ultérieure
- [Windows Server 2019](https://docs.microsoft.com/windows-server/get-started-19/whats-new-19)

Chaque règle asr contient l’un des trois paramètres ci-après :

- Non configuré : désactiver la règle asr
- Bloquer : activer la règle asr
- Audit : évaluer l’impact de la règle asr sur votre organisation si elle est activée

Il est vivement recommandé d’utiliser des règles asr avec une licence Windows E5 (ou une référence de licence similaire) pour tirer parti des fonctionnalités avancées de surveillance et de rapport disponibles dans [Microsoft Defender pour point](https://docs.microsoft.com/windows/security/threat-protection) de terminaison (Defender pour point de terminaison). Toutefois, pour d’autres licences telles que Windows Professionnel ou E3 qui n’ont pas accès aux fonctionnalités avancées de surveillance et de rapport, vous pouvez développer vos propres outils de surveillance et de rapport en plus des événements générés à chaque point de terminaison lorsque des règles DE LAS sont déclenchées (par exemple, le forwarding d’événement).

> [!TIP]
> Pour en savoir plus sur les licences Windows, voir [Licences Windows 10](https://www.microsoft.com/licensing/product-licensing/windows10?activetab=windows10-pivot:primaryr5) et obtenir le guide des licences en [volume pour Windows 10.](https://download.microsoft.com/download/2/D/1/2D14FE17-66C2-4D4C-AF73-E122930B60F6/Windows-10-Volume-Licensing-Guide.pdf)

Vous pouvez activer les règles de réduction de la surface d’attaque à l’aide de l’une de ces méthodes :

- [Microsoft Intune](#intune)
- [Gestion des périphériques mobiles (MDM)](#mdm)
- [Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager)
- [Stratégie de groupe](#group-policy)
- [PowerShell](#powershell)

La gestion au niveau de l’entreprise telle qu’Intune ou Microsoft Endpoint Manager est recommandée. La gestion au niveau de l’entreprise permet de réécrire les paramètres de stratégie de groupe ou PowerShell en conflit au démarrage.

## <a name="exclude-files-and-folders-from-asr-rules"></a>Exclure des fichiers et des dossiers des règles de la asr

Vous pouvez exclure les fichiers et dossiers de l’évaluation par la plupart des règles de réduction de la surface d’attaque. Cela signifie que même si une règle de astérité détermine que le fichier ou le dossier contient un comportement malveillant, il ne bloquera pas l’exécution du fichier. Cela peut potentiellement permettre à des fichiers non sécurisés de s’exécuter et d’infecter vos appareils.

Vous pouvez également exclure les règles asr du déclenchement en fonction des hages de certificat et de fichier en permettant les indicateurs de certificat et de fichier Defender for Endpoint spécifiés. (Voir [Gérer les indicateurs.)](https://docs.microsoft.com/microsoft-365/security/defender-endpoint/manage-indicators)

> [!IMPORTANT]
> L’exclusion de fichiers ou de dossiers peut réduire considérablement la protection fournie par les règles de réduction de la réduction du nombre de messages. Les fichiers exclus sont autorisés à s’exécuter et aucun rapport ou événement n’est enregistré.
> Si les règles DER détectent des fichiers qui, selon vous, ne doivent pas être détectés, vous devez d’abord utiliser le [mode audit pour tester la règle.](evaluate-attack-surface-reduction.md)


Vous pouvez spécifier des fichiers ou des dossiers individuels (à l’aide de chemins d’accès aux dossiers ou de noms de ressources complets), mais vous ne pouvez pas spécifier les règles à laquelle les exclusions s’appliquent. Une exclusion est appliquée uniquement au démarrage de l’application ou du service exclu. Par exemple, si vous ajoutez une exclusion pour un service de mise à jour déjà en cours d’exécution, le service de mise à jour continue à déclencher des événements jusqu’à ce que le service soit arrêté et redémarré.

Les règles de la asr prise en charge des variables d’environnement et des caractères génériques. Pour plus d’informations sur l’utilisation de caractères génériques, voir Utiliser des caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou [d’extension.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-antivirus/configure-extension-file-exclusions-microsoft-defender-antivirus#use-wildcards-in-the-file-name-and-folder-path-or-extension-exclusion-lists)

Les procédures suivantes pour l’activation des règles de la asr. incluent des instructions pour exclure des fichiers et des dossiers.

## <a name="intune"></a>Intune

1. Sélectionnez **Profils de configuration**  >  **d’appareil.** Choisissez un profil de protection de point de terminaison existant ou créez-en un. Pour en créer un, sélectionnez Créer un **profil** et entrez des informations pour ce profil. Pour **le type de profil,** **sélectionnez Endpoint Protection**. Si vous avez choisi un profil existant, sélectionnez **Propriétés,** puis **Paramètres.**

2. Dans le **volet de protection des points** de terminaison, **sélectionnez Windows Defender Exploit Guard,** puis sélectionnez **Réduction de la surface d’attaque.** Sélectionnez le paramètre souhaité pour chaque règle de asr.

3. Sous **Exceptions de réduction de la surface d’attaque,** entrez des fichiers et dossiers individuels. Vous pouvez également sélectionner **Importer** pour importer un fichier CSV qui contient des fichiers et des dossiers à exclure des règles de la asr. Chaque ligne du fichier CSV doit être mise en forme comme suit :

   `C:\folder`, `%ProgramFiles%\folder\file`, `C:\path`

4. Sélectionnez **OK** dans les trois volets de configuration. Sélectionnez **Ensuite Créer** si vous créez un fichier de protection de point de terminaison ou **Enregistrer** si vous modifiez un fichier existant.

## <a name="mdm"></a>MDM

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductionrules) (CSP) pour activer et définir individuellement le mode pour chaque règle.

Voici un exemple de référence, à l’aide de [valeurs GUID pour les règles asr](attack-surface-reduction.md#attack-surface-reduction-rules).

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionRules`

`Value: 75668C1F-73B5-4CF0-BB93-3ECF5CB7CC84=2|3B576869-A4EC-4529-8536-B80A7769E899=1|D4F940AB-401B-4EfC-AADC-AD5F3C50688A=2|D3E037E1-3EB8-44C8-A917-57927947596D=1|5BEB7EFE-FD9A-4556-801D-275E5FFC04CC=0|BE9BA2D9-53EA-4CDC-84E5-9B1EEEE46550=1`

Les valeurs à activer, désactiver ou activer en mode audit sont :

- Disable = 0
- Bloc (activer la règle de la asr) = 1
- Audit = 2

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions](https://docs.microsoft.com/windows/client-management/mdm/policy-csp-defender#defender-attacksurfacereductiononlyexclusions) (CSP) pour ajouter des exclusions.

Exemple :

`OMA-URI path: ./Vendor/MSFT/Policy/Config/Defender/AttackSurfaceReductionOnlyExclusions`

`Value: c:\path|e:\path|c:\Exclusions.exe`

> [!NOTE]
> N’oubliez pas d’entrer des valeurs OMA-URI sans espaces.

## <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

1. Dans Microsoft Endpoint Configuration Manager, sélectionnez **Assets and Compliance**  >  **Endpoint Protection** Windows Defender Exploit  >  **Guard**.

2. Sélectionnez **Home**  >  **Create Exploit Guard Policy**.

3. Entrez un nom et une description, sélectionnez **Réduction de la surface** d’attaque, puis sélectionnez **Suivant**.

4. Choisissez les règles qui bloqueront ou auditeront les actions et sélectionnez **Suivant.**

5. Examinez les paramètres et **sélectionnez Suivant** pour créer la stratégie.

6. Une fois la stratégie créée, **fermez**.

## <a name="group-policy"></a>Stratégie de groupe

> [!WARNING]
> Si vous gérez vos ordinateurs et périphériques avec Intune, Configuration Manager ou toute autre plateforme de gestion au niveau de l’entreprise, le logiciel de gestion risque d’éviter les paramètres de stratégie de groupe en conflit au démarrage.

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](https://technet.microsoft.com/library/cc731212.aspx)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer et sélectionnez **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, sélectionnez **Configuration** ordinateur et sélectionnez **Modèles d’administration.**

3. Développez l’arborescence **des composants Windows** de l’Antivirus  >  **Microsoft Defender** Windows Defender réduction de la surface  >    >  **d’attaque** Exploit Guard.

4. Sélectionnez **Configurer les règles de réduction de la surface d’attaque** et **sélectionnez Activé.** Vous pouvez ensuite définir l’état individuel de chaque règle dans la section Options.

   Sélectionnez **Afficher...** et entrez l’ID de règle dans  la colonne Nom de la valeur et l’état choisi dans la colonne Valeur comme suit : 

   - Disable = 0
   - Bloc (activer la règle de la asr) = 1
   - Audit = 2

   ![Paramètre de stratégie de groupe affichant un ID de règle de réduction de la surface d’attaque vide et la valeur 1](/microsoft-365/security/defender-endpoint/images/asr-rules-gp)

5. Pour exclure des fichiers et des dossiers des règles de réduction de la surface d’attaque, sélectionnez le paramètre Exclure les fichiers et les chemins d’accès des règles de réduction de la **surface** d’attaque et définissez l’option **sur Activé.** Sélectionnez **Afficher** et entrez chaque fichier ou dossier dans la **colonne Nom de la** valeur. Entrez **0 dans** la colonne **Valeur** pour chaque élément.

> [!WARNING]
> N’utilisez pas de guillemets, car ils ne sont pas pris en charge pour la colonne Nom de la valeur ou la **colonne** Valeur. 

## <a name="powershell"></a>PowerShell

> [!WARNING]
> Si vous gérez vos ordinateurs et appareils avec Intune, Configuration Manager ou une autre plateforme de gestion au niveau de l’entreprise, le logiciel de gestion risque d’éviter les paramètres PowerShell en conflit au démarrage. Pour permettre aux utilisateurs de définir la valeur à l’aide de PowerShell, utilisez l’option « Défini par l’utilisateur » pour la règle dans la plateforme de gestion.

1. Tapez **powershell** dans le menu Démarrer, cliquez avec **le bouton droit sur Windows PowerShell** puis **sélectionnez Exécuter en tant qu’administrateur.**

2. Entrez l’cmdlet suivante :

    ```PowerShell
    Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Enabled
    ```

    Pour activer les règles asr en mode audit, utilisez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions AuditMode
    ```

    Pour désactiver les règles de asr, utilisez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionRules_Ids <rule ID> -AttackSurfaceReductionRules_Actions Disabled
    ```

    > [!IMPORTANT]
    > Vous devez spécifier l’état individuellement pour chaque règle, mais vous pouvez combiner des règles et des états dans une liste séparée par des virgules.
    >
    > Dans l’exemple suivant, les deux premières règles sont activées, la troisième est désactivée et la quatrième règle est activée en mode audit :
    >
    > ```PowerShell
    > Set-MpPreference -AttackSurfaceReductionRules_Ids <rule ID 1>,<rule ID 2>,<rule ID 3>,<rule ID 4> -AttackSurfaceReductionRules_Actions Enabled, Enabled, Disabled, AuditMode
    > ```

    Vous pouvez également utiliser le verbe `Add-MpPreference` PowerShell pour ajouter de nouvelles règles à la liste existante.

    > [!WARNING]
    > `Set-MpPreference` est toujours en cours de réécriture de l’ensemble de règles existant. Si vous souhaitez l’ajouter à l’ensemble existant, vous devez `Add-MpPreference` l’utiliser à la place.
    > Vous pouvez obtenir une liste de règles et leur état actuel à l’aide `Get-MpPreference` de .

3. Pour exclure des fichiers et des dossiers des règles de la asr, utilisez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -AttackSurfaceReductionOnlyExclusions "<fully qualified path or resource>"
    ```

    Continuez à `Add-MpPreference -AttackSurfaceReductionOnlyExclusions` l’utiliser pour ajouter d’autres fichiers et dossiers à la liste.

    > [!IMPORTANT]
    > Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. `Set-MpPreference`L’utilisation de la cmdlet va supprimer la liste existante.

## <a name="related-articles"></a>Articles connexes

- [Réduire les surfaces d’attaque avec des règles de réduction de la surface d’attaque](attack-surface-reduction.md)

- [Évaluer la réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)

- [FAQ sur la réduction de la surface d’attaque](attack-surface-reduction.md)
