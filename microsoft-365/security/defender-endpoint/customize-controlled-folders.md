---
title: Personnaliser l’accès contrôlé aux dossiers
description: Ajoutez d’autres dossiers qui doivent être protégés par un accès contrôlé aux dossiers ou autorisez les applications qui bloquent de manière incorrecte les modifications apportées aux fichiers importants.
keywords: Accès contrôlé aux dossiers, windows 10, windows defender, ransomware, protéger, fichiers, dossiers, personnaliser, ajouter un dossier, ajouter une application, autoriser, ajouter un exécutable
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
localization_priority: Normal
audience: ITPro
author: denisebmsft
ms.author: deniseb
ms.reviewer: jcedola, dbodorin, vladiso, nixanm, anvascon
manager: dansimp
ms.date: 05/10/2021
ms.technology: mde
ms.topic: how-to
ms.openlocfilehash: e12368b6241a2c79eead66ed77b30b7864af3955
ms.sourcegitcommit: 68383240ef7a673d5f28e2ecfab9f105bf1d8c8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2021
ms.locfileid: "52326537"
---
# <a name="customize-controlled-folder-access"></a>Personnaliser l’accès contrôlé aux dossiers

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous souhaitez faire l’expérience de Defender pour point de terminaison ? [Inscrivez-vous à un essai gratuit.](https://www.microsoft.com/microsoft-365/windows/microsoft-defender-atp?ocid=docs-wdatp-assignaccess-abovefoldlink)

L’accès contrôlé aux dossiers vous permet de protéger les données précieuses contre les applications malveillantes et les menaces, telles que les ransomware. L’accès contrôlé aux dossiers est pris en charge sur les clients Windows Server 2019 et Windows 10. Cet article explique comment personnaliser les fonctionnalités d’accès contrôlé aux dossiers et comprend les sections suivantes :

- [Protéger des dossiers supplémentaires](#protect-additional-folders)
- [Ajouter des applications qui doivent être autorisées à accéder aux dossiers protégés](#allow-specific-apps-to-make-changes-to-controlled-folders)
- [Autoriser les fichiers exécutables signés à accéder aux dossiers protégés](#allow-signed-executable-files-to-access-protected-folders)
- [Personnaliser la notification](#customize-the-notification)

> [!IMPORTANT]
> L’accès contrôlé aux dossiers surveille les applications pour les activités détectées comme malveillantes. Parfois, les applications légitimes ne peuvent pas apporter de modifications à vos fichiers. Si l’accès contrôlé aux dossiers a un impact sur la productivité de votre organisation, vous pouvez envisager d’exécutez cette fonctionnalité en [mode audit](audit-windows-defender.md) pour en évaluer pleinement l’impact.

## <a name="protect-additional-folders"></a>Protéger des dossiers supplémentaires

L’accès contrôlé aux dossiers s’applique à de nombreux dossiers système et emplacements par défaut, y compris aux dossiers tels que **Documents,** **Images** et **Films.** Vous pouvez ajouter d’autres dossiers à protéger, mais vous ne pouvez pas supprimer les dossiers par défaut dans la liste par défaut.

L’ajout d’autres dossiers à l’accès contrôlé aux dossiers peut être utile dans les cas où vous ne stockez pas de fichiers dans les bibliothèques Windows par défaut ou lorsque vous avez modifié l’emplacement par défaut de vos bibliothèques.

Vous pouvez également spécifier des partages réseau et des lecteurs mappés. Les variables d’environnement et les caractères génériques sont pris en charge. Pour plus d’informations sur l’utilisation de caractères génériques, voir Utiliser des caractères génériques dans les listes d’exclusions de nom de fichier et de dossier ou [d’extension.](configure-extension-file-exclusions-microsoft-defender-antivirus.md)

Vous pouvez utiliser l’application de sécurité Windows, la stratégie de groupe, les cmdlets PowerShell ou les fournisseurs de services de configuration de gestion des appareils mobiles pour ajouter et supprimer des dossiers protégés.

### <a name="use-the-windows-security-app-to-protect-additional-folders"></a>Utiliser l’application Sécurité Windows pour protéger des dossiers supplémentaires

1. Ouvrez l’application Sécurité Windows en sélectionnant l’icône de bouclier dans la barre des tâches ou en recherchant la sécurité *dans* le menu Démarrer.

2. Sélectionnez **Virus & protection contre les** menaces, puis faites défiler vers le bas jusqu’à la section Protection contre les **ransomware.**

3. Sélectionnez **Gérer la protection contre les ransomware** pour ouvrir le volet protection contre les **ransomware.**

4. Sous la section **Accès contrôlé aux dossiers,** sélectionnez **Dossiers protégés.**

5. Sélectionnez **Oui** dans **l’invite contrôle d’accès** utilisateur. Le **volet Dossiers protégés** s’affiche.

6. Sélectionnez **Ajouter un dossier protégé et** suivez les invites pour ajouter des dossiers.

### <a name="use-group-policy-to-protect-additional-folders"></a>Utiliser une stratégie de groupe pour protéger des dossiers supplémentaires

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la[Console de gestion des stratégies de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true). 

2. Cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer, puis sélectionnez **Modifier.**

3. Dans votre Éditeur **de gestion des stratégies de** groupe, allez aux modèles d’administration des stratégies de **configuration**  >    >  **ordinateur.**

4. Développez l’arborescence **des composants Windows** de l’Antivirus  >  **Microsoft Defender**  >  **Windows Defender’accès contrôlé** aux  >  **dossiers** Exploit Guard. <br/>**REMARQUE**: sur les versions antérieures de Windows, vous pouvez voir **Windows Defender antivirus** au lieu de **l’Antivirus Microsoft Defender.**

5. Double-cliquez **sur Dossiers protégés configurés,** puis définissez l’option **sur Activé.** Sélectionnez **Afficher** et spécifiez chaque dossier à protéger.

6. Déployez votre objet de stratégie de groupe comme vous le faites généralement.

### <a name="use-powershell-to-protect-additional-folders"></a>Utiliser PowerShell pour protéger des dossiers supplémentaires

1. Tapez **PowerShell dans** le menu Démarrer, cliquez avec le **bouton droit sur Windows PowerShell** puis **sélectionnez Exécuter en tant qu’administrateur**

2. Tapez l’cmdlet PowerShell suivante, en remplaçant par le chemin d’accès du dossier `<the folder to be protected>` (par exemple : `"c:\apps\"`

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessProtectedFolders "<the folder to be protected>"
    ```
3. Répétez l’étape 2 pour chaque dossier que vous souhaitez protéger. Les dossiers protégés sont visibles dans l’application Sécurité Windows.

   :::image type="content" source="images/cfa-allow-folder-ps.png" alt-text="Fenêtre PowerShell avec cmdlet affichée":::

> [!IMPORTANT]
> Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste et non `Set-MpPreference` . `Set-MpPreference`L’utilisation de la cmdlet va supprimer la liste existante.

### <a name="use-mdm-csps-to-protect-additional-folders"></a>Utiliser des CSP mdm pour protéger des dossiers supplémentaires

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersList](/windows/client-management/mdm/policy-csp-defender#defender-guardedfolderslist) (CSP) pour permettre aux applications d’apporter des modifications aux dossiers protégés.

## <a name="allow-specific-apps-to-make-changes-to-controlled-folders"></a>Autoriser des applications spécifiques à apporter des modifications aux dossiers contrôlés

Vous pouvez spécifier si certaines applications sont toujours considérées comme sécurisées et accorder un accès en écriture aux fichiers dans les dossiers protégés. Autoriser les applications peut être utile si une application particulière que vous connaissez et que vous faites confiance est bloquée par la fonctionnalité d’accès contrôlé aux dossiers.

> [!IMPORTANT]
> Par défaut, Windows ajoute des applications qui sont considérées comme conviviales à la liste autorisée. Ces applications ajoutées automatiquement ne sont pas enregistrées dans la liste affichée dans l’application Sécurité Windows ou à l’aide des cmdlets PowerShell associées. Il n’est pas nécessaire d’ajouter la plupart des applications. Ajoutez uniquement des applications si elles sont bloquées et que vous pouvez vérifier leur fiabilité.

Lorsque vous ajoutez une application, vous devez spécifier son emplacement. Seule l’application à cet emplacement sera autorisée à accéder aux dossiers protégés. Si l’application (avec le même nom) se trouve à un autre emplacement, elle n’est pas ajoutée à la liste d’applications et peut être bloquée par l’accès contrôlé aux dossiers.

Une application ou un service autorisé dispose uniquement d’un accès en écriture à un dossier contrôlé après son démarrage. Par exemple, un service de mise à jour continue de déclencher des événements une fois autorisé jusqu’à ce qu’il soit arrêté et redémarré.

### <a name="use-the-windows-defender-security-app-to-allow-specific-apps"></a>Utiliser l’application Windows Defender security pour autoriser des applications spécifiques

1. Ouvrez l’application Sécurité Windows en recherchant sécurité dans le menu **Démarrer.**

2. Sélectionnez la **vignette & protection** contre les virus contre les menaces (ou l’icône de bouclier dans la barre de menus de gauche), puis sélectionnez Gérer la protection contre les **ransomware.**

3. Sous la section **Accès contrôlé aux dossiers,** **sélectionnez Autoriser une application via Accès contrôlé aux dossiers**

4. Sélectionnez **Ajouter une application autorisée et** suivez les invites pour ajouter des applications.

   :::image type="content" source="images/cfa-allow-app.png" alt-text="Ajouter un bouton d’application autorisé":::

### <a name="use-group-policy-to-allow-specific-apps"></a>Utiliser une stratégie de groupe pour autoriser des applications spécifiques

1. Sur votre appareil de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)?preserve=true)de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe que vous souhaitez configurer et sélectionnez **Modifier.**

2. Dans l’**Éditeur de gestion des stratégies de groupe**, accédez à **Configuration ordinateur**, puis sélectionnez **Modèles d’administration**.

3. Développez l’arborescence **des composants Windows** de l’Antivirus  >  **Microsoft Defender**  >  **Windows Defender’accès contrôlé** aux  >  **dossiers** Exploit Guard.

4. Double-cliquez sur le **paramètre Configurer les applications autorisées** et définissez l’option sur **Activé.** Sélectionnez **Afficher** et entrez chaque application.

### <a name="use-powershell-to-allow-specific-apps"></a>Utiliser PowerShell pour autoriser des applications spécifiques

1. Tapez **PowerShell dans** le menu Démarrer, cliquez avec le **bouton droit sur Windows PowerShell** puis **sélectionnez Exécuter en tant qu’administrateur**
2. Entrez l’cmdlet suivante :

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "<the app that should be allowed, including the path>"
    ```

    Par exemple, pour ajouter le fichier exécutable *test.exe* situé dans le dossier *C:\apps,* l’cmdlet serait la suivante :

    ```PowerShell
    Add-MpPreference -ControlledFolderAccessAllowedApplications "c:\apps\test.exe"
    ```

   Continuez à utiliser `Add-MpPreference -ControlledFolderAccessAllowedApplications` pour ajouter d’autres applications à la liste. Les applications ajoutées à l’aide de cette cmdlet s’affichent dans l’application Sécurité Windows.

   :::image type="content" source="images/cfa-allow-app-ps.png" alt-text="Cmdlet PowerShell pour autoriser une application":::

> [!IMPORTANT]
> Permet `Add-MpPreference` d’ajouter ou d’ajouter des applications à la liste. `Set-MpPreference`L’utilisation de la cmdlet va supprimer la liste existante.

### <a name="use-mdm-csps-to-allow-specific-apps"></a>Utiliser des CSP de gestion des applications mobiles pour autoriser des applications spécifiques

Utilisez le fournisseur de services de configuration [./Vendor/MSFT/Policy/Config/Defender/GuardedFoldersAllowedApplications](/windows/client-management/mdm/policy-csp-defender#defender-guardedfoldersallowedapplications) (CSP) pour permettre aux applications d’apporter des modifications aux dossiers protégés.

## <a name="allow-signed-executable-files-to-access-protected-folders"></a>Autoriser les fichiers exécutables signés à accéder aux dossiers protégés

Les indicateurs de certificat et de fichier Microsoft Defender pour point de terminaison peuvent autoriser les fichiers exécutables signés à accéder aux dossiers protégés. Pour plus d’informations sur l’implémentation, voir [Créer des indicateurs basés sur des certificats.](indicator-certificates.md)

> [!Note]
> Cela ne s’applique pas aux moteurs de script, y compris PowerShell

## <a name="customize-the-notification"></a>Personnaliser la notification

Pour plus d’informations sur la personnalisation de la notification lorsqu’une règle est déclenchée et bloque une application ou un fichier, voir Configurer les notifications d’alerte [dans Microsoft Defender pour le point de terminaison.](configure-email-notifications.md)

## <a name="see-also"></a>Voir aussi

- [Protéger les dossiers importants avec un accès contrôlé aux dossiers](controlled-folders.md)
- [Activer l’accès contrôlé aux dossiers](enable-controlled-folders.md)
- [Évaluer les règles de réduction de la surface d’attaque](evaluate-attack-surface-reduction.md)
