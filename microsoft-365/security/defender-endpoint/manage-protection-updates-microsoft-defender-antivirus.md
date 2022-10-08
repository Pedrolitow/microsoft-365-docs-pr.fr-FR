---
title: Gérer comment et où Microsoft Defender Antivirus reçoit les mises à jour
description: Gérez l’ordre de secours pour la façon dont Microsoft Defender Antivirus reçoit les mises à jour de protection.
keywords: mises à jour, bases de référence de sécurité, protection, ordre de secours, ADL, MMPC, UNC, chemin de fichier, partage, wsus
ms.service: microsoft-365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
ms.localizationpriority: medium
ms.topic: article
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.subservice: mde
ms.collection:
- m365-security
- tier2
search.appverid: met150
ms.openlocfilehash: c794e03ec7879c78d2023cee3f54bba830831a2a
ms.sourcegitcommit: 99b174a8d431092b3cf7d650593248671297fd91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/30/2022
ms.locfileid: "68300341"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Gérer les sources des mises à jour de la protection antivirus Microsoft Defender

> [!IMPORTANT]
> Les clients qui ont appliqué la mise à jour du moteur Microsoft Defender de mars 2022 (**1.1.19100.5**) ont peut-être rencontré une utilisation élevée des ressources (processeur et/ou mémoire). Microsoft a publié une mise à jour (**1.1.19200.5**) qui résout les bogues introduits dans la version antérieure. Il est recommandé aux clients de mettre à jour cette nouvelle version du moteur antivirus (**1.1.19200.5**). Pour vous assurer que les problèmes de performances sont entièrement résolus, il est recommandé de redémarrer les ordinateurs après l’application de la mise à jour. Pour plus d’informations, consultez [les versions mensuelles de la plateforme et du moteur](manage-updates-baselines-microsoft-defender-antivirus.md#monthly-platform-and-engine-versions).

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- Antivirus Microsoft Defender

**Plateformes**
- Windows

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Il est essentiel de maintenir votre protection antivirus à jour. Il existe deux composants pour gérer les mises à jour de protection pour Microsoft Defender Antivirus :

- *D’où* les mises à jour sont téléchargées ; Et
- *Lorsque* les mises à jour sont téléchargées et appliquées.

Cet article explique comment spécifier l’emplacement à partir duquel les mises à jour doivent être téléchargées (il s’agit également de l’ordre de secours). Consultez [La rubrique Gérer les mises à jour antivirus Microsoft Defender et appliquer des bases de référence](manage-updates-baselines-microsoft-defender-antivirus.md) pour obtenir une vue d’ensemble du fonctionnement des mises à jour et de la configuration d’autres aspects des mises à jour (tels que la planification des mises à jour).

> [!IMPORTANT]
> Microsoft Defender mises à jour du renseignement de sécurité antivirus et mises à jour de la plateforme sont fournies par le biais de Windows Update et à partir du lundi 21 octobre 2019, toutes les mises à jour du renseignement de sécurité seront signées exclusivement SHA-2. Vos appareils doivent être mis à jour pour prendre en charge SHA-2 afin de mettre à jour vos informations de sécurité. Pour plus d’informations, consultez [l’exigence de prise en charge de la signature de code SHA-2 2 2019 pour Windows et WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

<a id="fallback-order"></a>

## <a name="fallback-order"></a>Ordre de secours

En règle générale, vous configurez des points de terminaison pour télécharger individuellement les mises à jour à partir d’une source primaire suivie d’autres sources par ordre de priorité, en fonction de votre configuration réseau. Mises à jour sont obtenues à partir de sources dans l’ordre que vous spécifiez. Si les mises à jour de la source actuelle sont obsolètes, la source suivante dans la liste est utilisée immédiatement.

Lorsque des mises à jour sont publiées, une logique est appliquée pour réduire la taille de la mise à jour. Dans la plupart des cas, seules les différences entre la dernière mise à jour et la mise à jour actuellement installée (appelée delta) sur l’appareil sont téléchargées et appliquées. Toutefois, la taille du delta dépend de deux facteurs principaux :

- Âge de la dernière mise à jour sur l’appareil ; Et
- Source utilisée pour télécharger et appliquer des mises à jour.

Plus les mises à jour sur un point de terminaison sont anciennes, plus le téléchargement est important. Toutefois, vous devez également prendre en compte la fréquence de téléchargement. Une planification de mise à jour plus fréquente peut entraîner une utilisation plus importante du réseau, tandis qu’une planification moins fréquente peut entraîner des tailles de fichiers plus élevées par téléchargement.

Il existe cinq emplacements où vous pouvez spécifier où un point de terminaison doit obtenir des mises à jour :

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- Service <sup> [de mise à jour Windows Server](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus) [[1](#fn1)]<sup></sup>  
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [Partage de fichiers réseau](#unc-share)
- [Mises à jour du renseignement de sécurité pour Microsoft Defender Antivirus et autres logiciels anti-programme malveillant](/microsoft-365/security/defender-endpoint/manage-protection-update-schedule-microsoft-defender-antivirus) <sup>Microsoft [[2](#fn1)]<sup></sup>

(<a id="fn1">1</a>) Intune serveur de mise à jour de définition interne : si vous utilisez SCCM/SUP pour obtenir des mises à jour de définition pour Microsoft Defender Antivirus et que vous devez accéder à Windows Update sur les appareils clients bloqués, vous pouvez passer à la cogestion et décharger la charge de travail endpoint protection vers Intune. Dans la stratégie anti-programme malveillant configurée dans Intune il existe une option pour « serveur de mise à jour de définition interne » qui peut être configurée pour utiliser WSUS local comme source de mise à jour. Cela vous permet de contrôler les mises à jour du serveur WU officiel qui sont approuvées pour l’entreprise, ainsi que d’aider à proxyer et à enregistrer le trafic réseau vers le réseau windows UPdates officiel.

(<a id="fn1">2</a>) Votre stratégie et votre registre peuvent être répertoriés en tant que renseignement de sécurité Centre de protection Microsoft contre les programmes malveillants (MMPC), son ancien nom.

Pour garantir le meilleur niveau de protection, Microsoft Update permet des versions rapides, ce qui signifie des téléchargements plus petits sur une base fréquente. Le service de mise à jour Windows Server, le point de terminaison Microsoft Configuration Manager, les mises à jour du renseignement de sécurité Microsoft et les sources de mises à jour de plateforme fournissent des mises à jour moins fréquentes. Ainsi, le delta peut être plus grand, ce qui entraîne des téléchargements plus importants.

> [!NOTE]
> Les mises à jour de plateforme contiennent des mises à jour du moteur et sont publiées à une cadence mensuelle.
Les mises à jour du renseignement de sécurité sont également remises plusieurs fois par jour, mais ce package ne contient pas de moteur.


> [!IMPORTANT]
> Si vous avez défini les mises à jour de [page Microsoft Security Intelligence](https://www.microsoft.com/security/portal/definitions/adl.aspx) comme source de secours après Windows Server Update Service ou Microsoft Update, les mises à jour sont téléchargées uniquement à partir des mises à jour de sécurité et de la plateforme lorsque la mise à jour actuelle est considérée comme obsolète. (Par défaut, cela fait sept jours consécutifs qu’il n’est pas possible d’appliquer des mises à jour à partir du service Windows Server Update ou des services Microsoft Update).
> Toutefois, vous pouvez [définir le nombre de jours avant que la protection ne soit signalée comme étant obsolète](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus).<p>
> À compter du lundi 21 octobre 2019, les mises à jour du renseignement de sécurité et les mises à jour de plateforme seront signées exclusivement sha-2. Les appareils doivent être mis à jour pour prendre en charge SHA-2 afin d’obtenir les dernières mises à jour de sécurité et de plateforme. Pour plus d’informations, consultez [l’exigence de prise en charge de la signature de code SHA-2 2 2019 pour Windows et WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Chaque source a des scénarios classiques qui dépendent de la façon dont votre réseau est configuré, en plus de la fréquence à laquelle elles publient des mises à jour, comme décrit dans le tableau suivant :

|Emplacement|Exemple de scénario|
|---|---|
|Service de mise à jour Windows Server|Vous utilisez Windows Server Update Service pour gérer les mises à jour de votre réseau.|
|Microsoft Update|Vous souhaitez que vos points de terminaison se connectent directement à Microsoft Update. Cela peut être utile pour les points de terminaison qui se connectent de manière irrégulière à votre réseau d’entreprise, ou si vous n’utilisez pas Windows Server Update Service pour gérer vos mises à jour.|
|Partage de fichiers|Vous disposez d’appareils non connectés à Internet (tels que des machines virtuelles). Vous pouvez utiliser votre hôte de machine virtuelle connecté à Internet pour télécharger les mises à jour vers un partage réseau, à partir duquel les machines virtuelles peuvent obtenir les mises à jour. Consultez le [guide de déploiement VDI](deployment-vdi-microsoft-defender-antivirus.md) pour savoir comment les partages de fichiers peuvent être utilisés dans des environnements d’infrastructure de bureau virtuel (VDI).|
|Microsoft Endpoint Manager|Vous utilisez Microsoft Endpoint Manager pour mettre à jour vos points de terminaison.|
|Mises à jour du renseignement de sécurité et mises à jour de plateforme pour Microsoft Defender Antivirus et autres logiciels anti-programme malveillant Microsoft (anciennement appelés MMPC)|[Assurez-vous que vos appareils sont mis à jour pour prendre en charge SHA-2](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus). Microsoft Defender mises à jour de la plateforme et du renseignement de sécurité antivirus sont fournies par le biais de Windows Update, et à compter du lundi 21 octobre 2019, les mises à jour de sécurité et les mises à jour de la plateforme seront signées exclusivement sha-2. <br/>Téléchargez les dernières mises à jour de protection en raison d’une infection récente ou pour aider à approvisionner une image de base forte pour le [déploiement VDI](deployment-vdi-microsoft-defender-antivirus.md). Cette option doit généralement être utilisée uniquement comme source de secours finale, et non comme source principale. Elle ne sera utilisée que si les mises à jour ne peuvent pas être téléchargées à partir de Windows Server Update Service ou de Microsoft Update pendant [un nombre spécifié de jours](/microsoft-365/security/defender-endpoint/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date).|

Vous pouvez gérer l’ordre dans lequel les sources de mise à jour sont utilisées avec stratégie de groupe, microsoft endpoint Configuration Manager, les applets de commande PowerShell et WMI.

> [!IMPORTANT]
> Si vous définissez Windows Server Update Service comme emplacement de téléchargement, vous devez approuver les mises à jour, quel que soit l’outil de gestion que vous utilisez pour spécifier l’emplacement. Vous pouvez configurer une règle d’approbation automatique avec Windows Server Update Service, qui peut être utile lorsque les mises à jour arrivent au moins une fois par jour. Pour en savoir plus, consultez [synchroniser les mises à jour endpoint protection dans le service Windows Server Update autonome](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus).

Les procédures décrites dans cet article décrivent d’abord comment définir l’ordre, puis comment configurer l’option **Partage de fichiers** si vous l’avez activée.

## <a name="use-group-policy-to-manage-the-update-location"></a>Utiliser stratégie de groupe pour gérer l’emplacement de mise à jour

1. Sur votre machine de gestion stratégie de groupe, ouvrez la [console de gestion stratégie de groupe](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11)), cliquez avec le bouton droit sur l’objet stratégie de groupe que vous souhaitez configurer, puis cliquez sur **Modifier**.

2. Dans **l’éditeur de gestion stratégie de groupe**, accédez à **la configuration de l’ordinateur**.

3. Cliquez sur **Stratégies** , puis **sur Modèles d’administration**.

4. Développez l’arborescence sur **les composants** \> Windows **Windows Defender** \> **mises à jour de signature** et configurez les paramètres suivants :

   1. Double-cliquez sur **définir l’ordre des sources pour télécharger le paramètre des mises à jour du renseignement de sécurité** et définissez l’option **sur Activé**.

   2. Entrez l’ordre des sources, séparés par un seul canal, par exemple : `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC`comme illustré dans la capture d’écran suivante.

      :::image type="content" source="../../media/wdav-order-update-sources.png" alt-text="Paramètre de stratégie de groupe répertoriant l’ordre des sources" lightbox="../../media/wdav-order-update-sources.png":::

   3. Sélectionnez **OK**. Cela définit l’ordre des sources de mise à jour de protection.

   4. Double-cliquez sur **définir les partages de fichiers pour télécharger le paramètre des mises à jour du renseignement de sécurité** et **définissez** l’option sur Activé.

   5. Spécifiez la source du partage de fichiers. Si vous avez plusieurs sources, entrez chaque source dans l’ordre dans lequel elles doivent être utilisées, séparées par un seul canal. Utilisez la [notation UNC standard](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) pour la notation du chemin d’accès, par exemple : `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name`. Si vous n’entrez aucun chemin d’accès, cette source est ignorée lorsque la machine virtuelle télécharge les mises à jour.

   6. Cliquez sur **OK**. Cela définit l’ordre des partages de fichiers lorsque cette source est référencée dans le paramètre **Définir l’ordre des sources... stratégie de** groupe.

> [!NOTE]
> Pour Windows 10, versions 1703 jusqu’à et y compris 1809, le chemin d’accès de la stratégie est **Composants Windows > Microsoft Defender Antivirus > Signature Mises à jour** Pour Windows 10, version 1903, le chemin d’accès de la stratégie est **Composants Windows > Microsoft Defender  Antivirus > Mises à jour security intelligence**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Utiliser Configuration Manager pour gérer l’emplacement de mise à jour

Pour plus d’informations sur la configuration de Microsoft Endpoint Manager (current branch), consultez [Configurer l’Mises à jour security intelligence pour Endpoint Protection](/configmgr/protect/deploy-use/endpoint-definition-updates).

## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Utiliser des applets de commande PowerShell pour gérer l’emplacement de mise à jour

Utilisez les applets de commande PowerShell suivantes pour définir l’ordre de mise à jour.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```

Pour plus d’informations, consultez les articles suivants :

- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Utiliser des applets de commande PowerShell pour configurer et exécuter Microsoft Defender Antivirus](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Applets de commande antivirus Defender](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Utiliser l’instruction de gestion Windows (WMI) pour gérer l’emplacement de mise à jour

Utilisez la [méthode **Set** de la classe **MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Pour plus d’informations, consultez les articles suivants :

- [WINDOWS DEFENDER API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Utiliser Mobile Gestion des appareils (MDM) pour gérer l’emplacement de mise à jour

Pour plus d’informations sur la configuration de GPM, consultez Le fournisseur de solutions cloud de stratégie [- Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) .

## <a name="what-if-were-using-a-third-party-vendor"></a>Que se passe-t-il si nous utilisons un fournisseur tiers ?

Cet article explique comment configurer et gérer les mises à jour pour Microsoft Defender Antivirus. Toutefois, des fournisseurs tiers peuvent être utilisés pour effectuer ces tâches.

Par exemple, supposons que Contoso a embauché Fabrikam pour gérer sa solution de sécurité, qui inclut Microsoft Defender Antivirus. Fabrikam utilise généralement [Windows Management Instrumentation](./use-wmi-microsoft-defender-antivirus.md), les [applets de commande PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md) ou [la ligne de commande Windows](./command-line-arguments-microsoft-defender-antivirus.md) pour déployer des correctifs et des mises à jour.

> [!NOTE]
> Microsoft ne teste pas les solutions tierces pour gérer Microsoft Defender Antivirus.

<a id="unc-share"></a>

## <a name="create-a-unc-share-for-security-intelligence-and-platform-updates"></a>Créer un partage UNC pour les mises à jour de sécurité et de plateforme

Configurez un partage de fichiers réseau (UNC/lecteur mappé) pour télécharger les mises à jour de sécurité et de plateforme à partir du site MMPC à l’aide d’une tâche planifiée.

1. Sur le système sur lequel vous souhaitez approvisionner le partage et télécharger les mises à jour, créez un dossier dans lequel vous enregistrerez le script.

    ```console
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. Créez le dossier dans lequel vous allez enregistrer les mises à jour de signature.

    ```console
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Téléchargez le script PowerShell à partir de [www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. Cliquez sur **Télécharger manuellement**.

5. Cliquez sur **Télécharger le fichier nupkg brut**.

6. Extrayez le fichier.

7. Copiez le fichier SignatureDownloadCustomTask.ps1 dans le dossier que vous avez créé précédemment. `C:\Tool\PS-Scripts\`

8. Utilisez la ligne de commande pour configurer la tâche planifiée.

   > [!NOTE]
   > Il existe deux types de mises à jour : complète et delta.

   - Pour le delta x64 :

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Pour x64 complet :

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Pour le delta x86 :

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Pour x86 complet :

       ```powershell
       Powershell (Run as admin)

       C:\Tool\PS-Scripts\

       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   > [!NOTE]
   > Lorsque les tâches planifiées sont créées, vous pouvez les trouver dans le planificateur de tâches sous `Microsoft\Windows\Windows Defender`.

9. Exécutez chaque tâche manuellement et vérifiez que vous disposez de données (`mpam-d.exe`et`mpam-fe.exe``nis_full.exe`) dans les dossiers suivants (vous avez peut-être choisi différents emplacements) :

   - `C:\Temp\TempSigs\x86`
   - `C:\Temp\TempSigs\x64`

   Si la tâche planifiée échoue, exécutez les commandes suivantes :

    ```console
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"

    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```

    > [!NOTE]
    > Les problèmes peuvent également être dus à la stratégie d’exécution.

10. Créez un partage pointant vers `C:\Temp\TempSigs` (par exemple, `\\server\updates`).

    > [!NOTE]
    > Au minimum, les utilisateurs authentifiés doivent disposer d’un accès en lecture. Cette exigence s’applique également aux ordinateurs de domaine, au partage et au NTFS (sécurité).

11. Définissez l’emplacement du partage dans la stratégie sur le partage.

    > [!NOTE]
    > N’ajoutez pas le dossier x64 (ou x86) dans le chemin d’accès. Le processus mpcmdrun.exe l’ajoute automatiquement.

> [!TIP]
> Si vous recherchez des informations relatives à l’antivirus pour d’autres plateformes, consultez :
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur macOS](mac-preferences.md)
> - [Microsoft Defender pour point de terminaison sur Mac](microsoft-defender-endpoint-mac.md)
> - [Paramètres de stratégie antivirus macOS pour Antivirus Microsoft Defender pour Intune](/mem/intune/protect/antivirus-microsoft-defender-settings-macos)
> - [Définir les préférences pour Microsoft Defender pour point de terminaison sur Linux](linux-preferences.md)
> - [Microsoft Defender pour point de terminaison Linux](microsoft-defender-endpoint-linux.md)
> - [Configurer Defender pour point de terminaison pour des fonctionnalités Android](android-configure.md)
> - [configurer Microsoft Defender pour point de terminaison sur les fonctionnalités iOS](ios-configure-features.md)

## <a name="related-articles"></a>Articles connexes

- [Déployer Microsoft Defender Antivirus](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises à jour de Antivirus Microsoft Defender et appliquer des lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les points de terminaison obsolètes](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les machines virtuelles](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
