---
title: Personnaliser l’accès contrôlé aux dossiers
description: Ajoutez d’autres dossiers qui doivent être protégés par un accès contrôlé aux dossiers ou autorisez les applications qui bloquent incorrectement les modifications apportées aux fichiers importants.
keywords: Accès contrôlé aux dossiers, windows 10, windows 11, windows defender, ransomware, protéger, fichiers, dossiers, personnaliser, ajouter un dossier, ajouter une application, autoriser, ajouter un exécutable
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.localizationpriority: medium
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: oogunrinde, dbodorin, vladiso, nixanm, anvascon
manager: dansimp
ms.technology: mde
ms.topic: how-to
ms.collection: M365-security-compliance
ms.date: ''
ms.openlocfilehash: 3d6f763bd2ac2c4352f1b200c05c3079bc615aaf
ms.sourcegitcommit: 7ac54e1952383d5cd5f084c6a9d247eb747d4904
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2022
ms.locfileid: "66139338"
---
# <a name="customize-controlled-folder-access"></a>Personnaliser l’accès contrôlé aux dossiers

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

> [!TIP]
> Vous voulez découvrir Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-assignaccess-abovefoldlink)

L’accès contrôlé aux dossiers vous permet de protéger les données précieuses contre les applications malveillantes et les menaces, telles que les ransomware. L’accès contrôlé aux dossiers est pris en charge sur les clients Windows Server 2019, Windows Server 2022, Windows 10 et Windows 11. Cet article explique comment personnaliser les fonctionnalités d’accès contrôlé aux dossiers et inclut les sections suivantes :

- [Protéger des dossiers supplémentaires](#protect-additional-folders)
- [Ajouter des applications qui doivent être autorisées à accéder aux dossiers protégés](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [Autoriser les fichiers exécutables signés à accéder aux dossiers protégés](#allow-signed-executable-files-to-access-protected-folders)
- [Personnaliser la notification](#customize-the-notification)

> [!IMPORTANT]
> L’accès contrôlé aux dossiers surveille les applications pour les activités détectées comme malveillantes. Parfois, les applications légitimes ne peuvent pas apporter de modifications à vos fichiers. Si l’accès contrôlé aux dossiers a un impact sur la productivité de votre organisation, vous pouvez envisager d’exécuter cette fonctionnalité en [mode audit](audit-windows-defender.md) pour évaluer entièrement l’impact.

## <a name="protect-additional-folders"></a>Protéger des dossiers supplémentaires

L’accès contrôlé aux dossiers s’applique à de nombreux dossiers système et emplacements par défaut, notamment des dossiers tels que **Documents**, **Images** et **Films**. Vous pouvez ajouter d’autres dossiers à protéger, mais vous ne pouvez pas supprimer les dossiers par défaut dans la liste par défaut.

L’ajout d’autres dossiers à l’accès contrôlé aux dossiers peut être utile dans les cas où vous ne stockez pas de fichiers dans les bibliothèques Windows par défaut, ou si vous avez modifié l’emplacement par défaut de vos bibliothèques.

Vous pouvez également spécifier des partages réseau et des lecteurs mappés. Les variables d’environnement et les caractères génériques sont pris en charge. Pour plus d’informations sur l’utilisation de caractères génériques, consultez [Utiliser des caractères génériques dans le nom de fichier et le chemin d’accès au dossier ou les listes d’exclusion d’extension](configure-extension-file-exclusions-microsoft-defender-antivirus.md).

Vous pouvez utiliser l’application Sécurité Windows, les stratégie de groupe, les applets de commande PowerShell ou les fournisseurs de services de configuration de gestion des appareils mobiles pour ajouter et supprimer des dossiers protégés.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Utiliser l’application Sécurité Windows pour protéger des dossiers supplémentaires

1. Ouvrez l’application Sécurité Windows en sélectionnant l’icône de bouclier dans la barre des tâches ou en recherchant la *sécurité* dans le menu Démarrer.

2. Sélectionnez **Virus & protection contre les menaces**, puis faites défiler jusqu’à la section **Protection contre les ransomware** .

3. Sélectionnez **Gérer la protection contre les rançongiciels** pour ouvrir le volet **Protection contre les ransomwares** .

4. Dans la section **Accès contrôlé aux dossiers** , sélectionnez **Dossiers protégés**.

5. Choisissez **Oui** à l’invite **de Access Control utilisateur**. Le volet **Dossiers protégés** s’affiche.

6. Sélectionnez **Ajouter un dossier protégé** et suivez les invites pour ajouter des dossiers.

### <a name="use-group-policy-to-protect-additional-folders"></a>Utiliser stratégie de groupe pour protéger des dossiers supplémentaires

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

3. Dans votre **éditeur de gestion stratégie de groupe**, accédez aux **modèles d’administration des** stratégies de configuration  \> \> de l’ordinateur.

4. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **Windows Defender’accès contrôlé aux dossiers** **Exploit Guard**\>. <br/>**REMARQUE** : Sur les versions antérieures de Windows, vous pouvez voir **Antivirus Windows Defender** au lieu de **Antivirus Microsoft Defender**.

5. Double-cliquez sur **Dossiers protégés configurés**, puis définissez l’option **sur Activé**. Sélectionnez **Afficher** et spécifiez chaque dossier que vous souhaitez protéger.

6. Déployez votre objet stratégie de groupe comme d’habitude.

### <a name="use-powershell-to-protect-additional-folders"></a>Utiliser PowerShell pour protéger des dossiers supplémentaires

1. Tapez **PowerShell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**

2. Tapez l’applet de commande PowerShell suivante, en remplaçant `<the folder to be protected>` le chemin du dossier (par `"c:\apps\"`exemple) :

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Répétez l’étape 2 pour chaque dossier que vous souhaitez protéger. Les dossiers protégés sont visibles dans l’application Sécurité Windows.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="Fenêtre PowerShell avec applet de commande affichée" lightbox="images/cfa-allow-folder-ps.png":::

> [!IMPORTANT]
> Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste et non `Set-MpPreference`. L’utilisation de l’applet `Set-MpPreference` de commande remplace la liste existante.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Utiliser des CSP GPM pour protéger des dossiers supplémentaires

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) (fournisseur de solutions Cloud) pour permettre aux applications d’apporter des modifications aux dossiers protégés.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Autoriser des applications spécifiques à apporter des modifications à des dossiers contrôlés

Vous pouvez spécifier si certaines applications sont toujours considérées comme sûres et accorder un accès en écriture aux fichiers dans des dossiers protégés. L’autorisation d’applications peut être utile si une application particulière que vous connaissez et dont vous avez confiance est bloquée par la fonctionnalité d’accès contrôlé aux dossiers.

> [!IMPORTANT]
> Par défaut, Windows ajoute des applications considérées comme conviviales à la liste autorisée. Ces applications ajoutées automatiquement ne sont pas enregistrées dans la liste affichée dans l’application Sécurité Windows ou à l’aide des applets de commande PowerShell associées. Vous n’avez pas besoin d’ajouter la plupart des applications. Ajoutez des applications uniquement si elles sont bloquées et que vous pouvez vérifier leur fiabilité.

Lorsque vous ajoutez une application, vous devez spécifier l’emplacement de l’application. Seule l’application à cet emplacement sera autorisée à accéder aux dossiers protégés. Si l’application (portant le même nom) se trouve à un autre emplacement, elle n’est pas ajoutée à la liste verte et peut être bloquée par l’accès contrôlé aux dossiers.

Une application ou un service autorisé dispose uniquement d’un accès en écriture à un dossier contrôlé après son démarrage. Par exemple, un service de mise à jour continue de déclencher des événements une fois qu’il est autorisé jusqu’à ce qu’il soit arrêté et redémarré.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Utiliser l’application de sécurité Windows Defender pour autoriser des applications spécifiques

1. Ouvrez l’application Sécurité Windows en recherchant **la sécurité** dans le menu Démarrer.

2. Sélectionnez la vignette **Virus & protection contre les menaces** (ou l’icône du bouclier dans la barre de menus de gauche), puis **sélectionnez Gérer la protection contre les ransomware**.

3. Dans la section **Accès contrôlé aux dossiers** , sélectionnez **Autoriser une application via l’accès contrôlé aux dossiers**

4. Sélectionnez **Ajouter une application autorisée** et suivez les invites pour ajouter des applications.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="Bouton Ajouter une application autorisée" lightbox="images/cfa-allow-app.png":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Utiliser stratégie de groupe pour autoriser des applications spécifiques

1. Sur votre appareil de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier**.

2. Dans l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence pour **Windows composants** \> **Antivirus Microsoft Defender** \> **Windows Defender’accès contrôlé aux dossiers** **Exploit Guard**\>.

4. Double-cliquez sur le paramètre **Configurer les applications autorisées** et définissez l’option **sur Activé**. Sélectionnez **Afficher** et entrez chaque application.

### <a name="use-powershell-to-allow-specific-apps"></a>Utiliser PowerShell pour autoriser des applications spécifiques

1. Tapez **PowerShell** dans le menu Démarrer, cliquez avec le bouton droit sur **Windows PowerShell** et sélectionnez **Exécuter en tant qu’administrateur**
2. Entrez l’applet de commande suivante :

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Par exemple, pour ajouter le *test.exe* exécutable situé dans le dossier *C:\apps*, l’applet de commande est la suivante :

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Continuez à l’utiliser `Add-MpPreference -ControlledFolderAccessAllowedApplications` pour ajouter d’autres applications à la liste. Les applications ajoutées à l’aide de cette applet de commande apparaissent dans l’application Sécurité Windows.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Applet de commande PowerShell pour autoriser une application" lightbox="images/cfa-allow-app-ps.png":::

> [!IMPORTANT]
> Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. L’utilisation de l’applet `Set-MpPreference` de commande remplace la liste existante.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Utiliser des CSP MDM pour autoriser des applications spécifiques

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/ControlledFolderAccessAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) (fournisseur de solutions Cloud) pour permettre aux applications d’apporter des modifications aux dossiers protégés.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>Autoriser les fichiers exécutables signés à accéder aux dossiers protégés

Microsoft Defender pour point de terminaison les indicateurs de certificat et de fichier peuvent autoriser les fichiers exécutables signés à accéder aux dossiers protégés. Pour plus d’informations sur l’implémentation, consultez [Créer des indicateurs basés sur des certificats](indicator-certificates.md).

> [!Note]
> Cela ne s’applique pas aux moteurs de script, y compris PowerShell

## <a name="customize-the-notification"></a>Personnaliser la notification

Pour plus d’informations sur la personnalisation de la notification lorsqu’une règle est déclenchée et bloque une application ou un fichier, consultez [Configurer les notifications d’alerte dans Microsoft Defender pour point de terminaison](configure-email-notifications.md).

## <a name="see-also"></a>Voir aussi

- [Protéger les dossiers importants avec accès contrôlé aux dossiers](controlled-folders.md)
- [Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md)
- [Activer les règles de réduction de la surface d’attaque](enable-attack-surface-reduction.md)
