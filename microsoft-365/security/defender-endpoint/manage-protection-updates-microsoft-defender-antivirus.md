---
title: Gérer comment et où Antivirus Microsoft Defender reçoit les mises à jour
description: Gérez l’ordre de retour de la façon dont Antivirus Microsoft Defender reçoit les mises à jour de protection.
keywords: mises à jour, lignes de base de sécurité, protection, ordre de base, ADL, MMPC, UNC, chemin d’accès au fichier, partage, wsus
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: manage
ms.sitesec: library
ms.pagetype: security
localization_priority: Normal
author: denisebmsft
ms.author: deniseb
ms.reviewer: pahuijbr
manager: dansimp
ms.custom: nextgen
ms.technology: mde
ms.topic: article
ms.openlocfilehash: 52fe64b096b24dfc52a97fb664e408c5aeb701f4
ms.sourcegitcommit: 686f192e1a650ec805fe8e908b46ca51771ed41f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2021
ms.locfileid: "52624208"
---
# <a name="manage-the-sources-for-microsoft-defender-antivirus-protection-updates"></a>Gérer les sources des mises à jour de la protection antivirus Microsoft Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]


**S’applique à :**

- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=22154037)

<a id="protection-updates"></a>
<!-- this has been used as anchor in VDI content -->

Il est essentiel de maintenir la protection antivirus à jour. Il existe deux composants pour la gestion des mises à jour de protection Antivirus Microsoft Defender : 
- *l’endroit* à partir de laquelle les mises à jour sont téléchargées ; et 
- *Lorsque les* mises à jour sont téléchargées et appliquées. 

Cet article explique comment spécifier l’endroit où les mises à jour doivent être téléchargées (c’est également ce qu’on appelle l’ordre de retour). Voir [Gérer Antivirus Microsoft Defender](manage-updates-baselines-microsoft-defender-antivirus.md) mises à jour et appliquer les lignes de base pour une vue d’ensemble sur le fonctionnement des mises à jour et la configuration d’autres aspects des mises à jour (par exemple, la planification des mises à jour).

> [!IMPORTANT]
> Antivirus Microsoft Defender Les mises à jour des informations de sécurité sont mises à jour via Windows Update et, à compter du lundi 21 octobre 2019, toutes les mises à jour de l’intelligence de sécurité seront signées exclusivement par SHA-2. Vos appareils doivent être mis à jour pour prendre en charge SHA-2 afin de mettre à jour vos informations de sécurité. Pour plus d’informations, voir [2019 SHA-2 Code Signing Support requirement for Windows and WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).  


<a id="fallback-order"></a>

## <a name="fallback-order"></a>Ordre de retour

En règle générale, vous configurez les points de terminaison pour télécharger individuellement les mises à jour à partir d’une source principale suivie d’autres sources par ordre de priorité, en fonction de la configuration de votre réseau. Les mises à jour sont obtenues à partir de sources dans l’ordre que vous spécifiez. Si une source n’est pas disponible, la source suivante de la liste est utilisée immédiatement.

Lorsque des mises à jour sont publiées, une logique est appliquée pour réduire la taille de la mise à jour. Dans la plupart des cas, seules les différences entre la dernière mise à jour et la mise à jour actuellement installée (appelée delta) sur l’appareil sont téléchargées et appliquées. Toutefois, la taille du delta dépend de deux facteurs principaux :
- L’âge de la dernière mise à jour sur l’appareil ; et 
- Source utilisée pour télécharger et appliquer les mises à jour. 

Plus les mises à jour sur un point de terminaison sont anciennes, plus le téléchargement est volumineux. Toutefois, vous devez également prendre en compte la fréquence de téléchargement. Une planification des mises à jour plus fréquente peut entraîner une utilisation plus fréquente du réseau, tandis qu’une planification moins fréquente peut entraîner des tailles de fichiers plus importantes par téléchargement. 

Il existe cinq emplacements où vous pouvez spécifier l’emplacement où un point de terminaison doit obtenir des mises à jour : 

- [Microsoft Update](https://support.microsoft.com/help/12373/windows-update-faq)
- [Windows Service de mise à jour du serveur](/windows-server/administration/windows-server-update-services/get-started/windows-server-update-services-wsus)
- [Microsoft Endpoint Configuration Manager](/configmgr/core/servers/manage/updates)
- [Partage de fichiers réseau](#unc-share)
- Mises à jour de l’intelligence de la sécurité pour Antivirus Microsoft Defender et autres logiciels anti-programme malveillant [Microsoft](https://www.microsoft.com/en-us/wdsi/defenderupdates) (votre stratégie et votre Registre peuvent être répertoriés en tant qu’intelligence de sécurité CENTRE DE PROTECTION MICROSOFT CONTRE LES PROGRAMMES MALVEILLANTS (MMPC), son ancien nom).)

Pour garantir le meilleur niveau de protection, Microsoft Update permet des mises à jour rapides, ce qui signifie des téléchargements plus petits sur une base fréquente. Les sources Windows de mise à jour du service de mise à jour du serveur, de Microsoft Endpoint Configuration Manager et de l’intelligence de sécurité Microsoft offrent des mises à jour moins fréquentes. Par conséquent, le delta peut être plus grand, ce qui entraîne des téléchargements plus importants. 

> [!IMPORTANT]
> Si vous avez définie les mises à jour de [la page](https://www.microsoft.com/security/portal/definitions/adl.aspx) d’aide à la sécurité Microsoft comme source de récupération après le service de mise à jour du serveur Windows ou Microsoft Update, les mises à jour sont téléchargées uniquement à partir des mises à jour de l’intelligence de sécurité lorsque la mise à jour actuelle est considérée comme étant hors date. (Par défaut, cela fait sept jours consécutifs que vous ne pouvez pas appliquer les mises à jour à partir du service de mise à jour du serveur Windows ou des services Microsoft Update).
> Toutefois, vous pouvez définir le nombre de jours avant que la protection ne soit signalée comme [étant hors date.](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date)<p>
> À compter du lundi 21 octobre 2019, les mises à jour des informations de sécurité seront exclusivement signées SHA-2. Les appareils doivent être mis à jour pour prendre en charge SHA-2 afin d’obtenir les dernières mises à jour de l’intelligence de sécurité. Pour plus d’informations, voir [2019 SHA-2 Code Signing Support requirement for Windows and WSUS](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus).

Chaque source présente des scénarios classiques qui dépendent de la façon dont votre réseau est configuré, en plus de la fréquence de publication des mises à jour, comme décrit dans le tableau suivant :

|Emplacement | Exemple de scénario |
|---|---|
|Windows Service de mise à jour du serveur | Vous utilisez Windows Server Update Service pour gérer les mises à jour de votre réseau.|
|Microsoft Update | Vous souhaitez que vos points de terminaison se connectent directement à Microsoft Update. Cela peut être utile pour les points de terminaison qui se connectent de manière irrégulière à votre réseau d’entreprise, ou si vous n’utilisez pas Windows Server Update Service pour gérer vos mises à jour.|
|Partage de fichiers | Vous avez des appareils non connectés à Internet (tels que des VM). Vous pouvez utiliser votre hôte de vm connecté à Internet pour télécharger les mises à jour sur un partage réseau, à partir duquel les VM peuvent obtenir les mises à jour. Consultez le [guide de déploiement VDI](deployment-vdi-microsoft-defender-antivirus.md) pour savoir comment les partages de fichiers peuvent être utilisés dans les environnements d’infrastructure de bureau virtuel (VDI).|
|Microsoft Endpoint Manager | Vous utilisez Microsoft Endpoint Manager pour mettre à jour vos points de terminaison.|
|Mises à jour des informations de sécurité pour Antivirus Microsoft Defender logiciel anti-programme malveillant Microsoft (anciennement appelé MMPC) |[Assurez-vous que vos appareils sont mis à jour pour prendre en charge SHA-2.](https://support.microsoft.com/help/4472027/2019-sha-2-code-signing-support-requirement-for-windows-and-wsus) Antivirus Microsoft Defender Les mises à jour de l’intelligence de sécurité sont Windows Update et, à compter du lundi 21 octobre 2019, les mises à jour de l’intelligence de sécurité seront signées exclusivement par SHA-2. <br/>Téléchargez les dernières mises à jour de protection en raison d’une infection récente ou pour mettre en service une image de base forte pour le [déploiement VDI.](deployment-vdi-microsoft-defender-antivirus.md) Cette option doit généralement être utilisée uniquement comme source de retour final, et non comme source principale. Elle sera utilisée uniquement si les mises à jour ne peuvent pas être téléchargées depuis Windows Server Update Service ou Microsoft Update pour un [nombre de jours spécifié.](/windows/threat-protection/microsoft-defender-antivirus/manage-outdated-endpoints-microsoft-defender-antivirus#set-the-number-of-days-before-protection-is-reported-as-out-of-date)|

Vous pouvez gérer l’ordre dans lequel les sources de mise à jour sont utilisées avec la stratégie de groupe, Microsoft Endpoint Configuration Manager, les cmdlets PowerShell et WMI.

> [!IMPORTANT]
> Si vous définissez Windows Server Update Service comme emplacement de téléchargement, vous devez approuver les mises à jour, quel que soit l’outil de gestion que vous utilisez pour spécifier l’emplacement. Vous pouvez configurer une règle d’approbation automatique avec Windows Server Update Service, ce qui peut être utile lorsque les mises à jour arrivent au moins une fois par jour. Pour plus d’informations, voir synchroniser les mises à jour de la protection des points de terminaison dans Windows service de mise [à jour du serveur.](/configmgr/protect/deploy-use/endpoint-definitions-wsus#to-synchronize-endpoint-protection-definition-updates-in-standalone-wsus)

Les procédures de cet article décrivent d’abord comment définir  la commande, puis comment configurer l’option de partage de fichiers si vous l’avez activée.

## <a name="use-group-policy-to-manage-the-update-location"></a>Utiliser une stratégie de groupe pour gérer l’emplacement de mise à jour

1. Sur votre ordinateur de gestion des stratégies de groupe, ouvrez la [Console](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc731212(v=ws.11))de gestion des stratégies de groupe, cliquez avec le bouton droit sur l’objet de stratégie de groupe à configurer, puis cliquez sur **Modifier.**

2. Dans **l’Éditeur de gestion des stratégies de** groupe, allez à **Configuration ordinateur.**

3. Cliquez **sur Stratégies** **puis Modèles d’administration.**

4. Développez l’arborescence **Windows composants > Windows Defender > mises** à jour des signatures et configurez les paramètres suivants :

   1.  Double-cliquez sur **le paramètre Définir l’ordre** des sources de téléchargement des mises à jour d’informations de sécurité et définissez l’option sur **Activé.**

   2.  Entrez l’ordre des sources, séparés par un seul canal, par exemple : `InternalDefinitionUpdateServer|MicrosoftUpdateServer|MMPC` , comme illustré dans la capture d’écran suivante.

   ![Capture d’écran du paramètre de stratégie de groupe répertoriant l’ordre des sources](images/defender/wdav-order-update-sources.png)

   3. Cliquez sur **OK**. Cela définira l’ordre des sources de mise à jour de la protection.

   4. Double-cliquez sur le paramètre Définir les **partages de fichiers** pour télécharger les mises à jour de l’intelligence de sécurité et définissez l’option **sur Activé.**

   5. Entrez la source du partage de fichiers. Si vous avez plusieurs sources, entrez chaque source dans l’ordre où elles doivent être utilisées, séparées par un seul canal. Utilisez [la notation UNC standard](/openspecs/windows_protocols/ms-dtyp/62e862f4-2a51-452e-8eeb-dc4ff5ee33cc) pour le chemin d’accès, par exemple : `\\host-name1\share-name\object-name|\\host-name2\share-name\object-name` .  Si vous n’entrez aucun chemin d’accès, cette source est ignorée lorsque l’VM télécharge les mises à jour.

   6. Cliquez sur **OK**. Cela définit l’ordre des partages de fichiers lorsque cette source est référencé dans le paramètre de stratégie de groupe Définir l’ordre des **sources...**

> [!NOTE]
> Pour Windows 10, versions 1703 jusqu’à 1809 inclus, le chemin d’accès de stratégie est **Windows Components > Antivirus Microsoft Defender > Signature Updates** For Windows 10, version 1903, le chemin d’accès de stratégie est **Windows Components > Antivirus Microsoft Defender > Security Intelligence Updates**

## <a name="use-configuration-manager-to-manage-the-update-location"></a>Utiliser Configuration Manager pour gérer l’emplacement de mise à jour

Pour [plus d’informations](/configmgr/protect/deploy-use/endpoint-definition-updates) sur la configuration Microsoft Endpoint Manager (branche actuelle), voir Configurer les mises à jour de l’intelligence de sécurité pour Endpoint Protection données.


## <a name="use-powershell-cmdlets-to-manage-the-update-location"></a>Utiliser les cmdlets PowerShell pour gérer l’emplacement de mise à jour

Utilisez les cmdlets PowerShell suivantes pour définir l’ordre de mise à jour.

```PowerShell
Set-MpPreference -SignatureFallbackOrder {LOCATION|LOCATION|LOCATION|LOCATION}
Set-MpPreference -SignatureDefinitionUpdateFileSharesSource {\\UNC SHARE PATH|\\UNC SHARE PATH}
```
Pour plus d’informations, consultez les articles suivants :
- [Set-MpPreference -SignatureFallbackOrder](/powershell/module/defender/set-mppreference)
- [Set-MpPreference -SignatureDefinitionUpdateFileSharesSource](/powershell/module/defender/set-mppreference#-signaturedefinitionupdatefilesharessources)
- [Utiliser les cmdlets PowerShell pour configurer et exécuter des Antivirus Microsoft Defender](use-powershell-cmdlets-microsoft-defender-antivirus.md)
- [Cmdlets Defender](/powershell/module/defender/index)

## <a name="use-windows-management-instruction-wmi-to-manage-the-update-location"></a>Utiliser Windows Management Instruction (WMI) pour gérer l’emplacement de mise à jour

Utilisez la [ **méthode Set** de la **classe MSFT_MpPreference**](/previous-versions/windows/desktop/legacy/dn455323(v=vs.85)) pour les propriétés suivantes :

```WMI
SignatureFallbackOrder
SignatureDefinitionUpdateFileSharesSource
```

Pour plus d’informations, consultez les articles suivants :
- [Windows Defender API WMIv2](/previous-versions/windows/desktop/defender/windows-defender-wmiv2-apis-portal)

## <a name="use-mobile-device-management-mdm-to-manage-the-update-location"></a>Utiliser la gestion des périphériques mobiles (MDM) pour gérer l’emplacement de mise à jour

Voir [Policy CSP - Defender/SignatureUpdateFallbackOrder](/windows/client-management/mdm/policy-csp-defender#defender-signatureupdatefallbackorder) pour plus d’informations sur la configuration de mdm.

## <a name="what-if-were-using-a-third-party-vendor"></a>Que se passe-t-il si nous utilisons un fournisseur tiers ?

Cet article explique comment configurer et gérer les mises à jour pour Antivirus Microsoft Defender. Toutefois, les fournisseurs tiers peuvent être utilisés pour effectuer ces tâches. 

Par exemple, supposons que Contoso a embauché Fabrikam pour gérer sa solution de sécurité, qui inclut Antivirus Microsoft Defender. Fabrikam utilise généralement [Windows Management Instrumentation,](./use-wmi-microsoft-defender-antivirus.md)des [cmdlets PowerShell](./use-powershell-cmdlets-microsoft-defender-antivirus.md)ou [Windows](./command-line-arguments-microsoft-defender-antivirus.md) ligne de commande pour déployer des correctifs et des mises à jour. 

> [!NOTE]
> Microsoft ne teste pas les solutions tierces pour la gestion des Antivirus Microsoft Defender.

<a id="unc-share"></a>
## <a name="create-a-unc-share-for-security-intelligence-updates"></a>Créer un partage UNC pour les mises à jour d’informations de sécurité

Configurer un partage de fichiers réseau (lecteur UNC/mappé) pour télécharger les mises à jour d’informations de sécurité à partir du site MMPC à l’aide d’une tâche programmée.

1. Sur le système sur lequel vous souhaitez mettre en service le partage et télécharger les mises à jour, créez un dossier dans lequel vous enregistrerez le script.
    ```DOS
    Start, CMD (Run as admin)
    MD C:\Tool\PS-Scripts\
    ```

2. Créez le dossier dans lequel vous allez enregistrer les mises à jour de signature.
    ```DOS
    MD C:\Temp\TempSigs\x64
    MD C:\Temp\TempSigs\x86
    ```

3. Téléchargez le script PowerShell à [partir www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4](https://www.powershellgallery.com/packages/SignatureDownloadCustomTask/1.4).

4. Cliquez **sur Téléchargement manuel.**

5. Cliquez **sur Télécharger le fichier nupkg brut.**

6. Extrayons le fichier.

7. Copiez le fichier SignatureDownloadCustomTask.ps1 dans le dossier que vous avez précédemment créé, C:\Tool\PS-Scripts\ .

8. Utilisez la ligne de commande pour configurer la tâche programmée.
    > [!NOTE]
    > Il existe deux types de mises à jour : complète et delta.
   - Pour le delta x64 :

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $true -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Pour x64 complet :

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x64 -isDelta $false -destDir C:\Temp\TempSigs\x64 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Pour le delta x86 :

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $true -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

   - Pour x86 complet :

       ```DOS
       Powershell (Run as admin)
    
       C:\Tool\PS-Scripts\
    
       ".\SignatureDownloadCustomTask.ps1 -action create -arch x86 -isDelta $false -destDir C:\Temp\TempSigs\x86 -scriptPath C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1 -daysInterval 1"
       ```

    > [!NOTE]
    > Lorsque les tâches programmées sont créées, vous pouvez les trouver dans le Programmeur des tâches sous Microsoft\Windows\Windows Defender
9. Exécutez chaque tâche manuellement et vérifiez que vous avez des données (mpam-d.exe, mpam-fe.exe et nis_full.exe) dans les dossiers suivants (vous avez peut-être choisi différents emplacements) :

   - C:\Temp\TempSigs\x86
   - C:\Temp\TempSigs\x64

   Si la tâche programmée échoue, exécutez les commandes suivantes :

    ```DOS
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $False -destDir C:\Temp\TempSigs\x64"
    
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x64 -isDelta $True -destDir C:\Temp\TempSigs\x64"
    
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $False -destDir C:\Temp\TempSigs\x86"
    
    C:\windows\system32\windowspowershell\v1.0\powershell.exe -NoProfile -executionpolicy allsigned -command "&\"C:\Tool\PS-Scripts\SignatureDownloadCustomTask.ps1\" -action run -arch x86 -isDelta $True -destDir C:\Temp\TempSigs\x86"
    ```
    > [!NOTE]
    > Des problèmes peuvent également être dus à la stratégie d’exécution.
    
10. Créez un partage pointant vers C:\Temp\TempSigs (par exemple, \\ serveur\mises à jour).
    > [!NOTE]
    > Au minimum, les utilisateurs authentifiés doivent avoir accès en lecture.
11. Définissez l’emplacement du partage dans la stratégie sur le partage.

    > [!NOTE]
    > N’ajoutez pas le dossier x64 (ou x86) dans le chemin d’accès. Le processus mpcmdrun.exe l’ajoute automatiquement.

## <a name="related-articles"></a>Articles connexes

- [Déployer Antivirus Microsoft Defender](deploy-manage-report-microsoft-defender-antivirus.md)
- [Gérer les mises Antivirus Microsoft Defender jour et appliquer les lignes de base](manage-updates-baselines-microsoft-defender-antivirus.md)
- [Gérer les mises à jour des points de terminaison qui ne sont plus à jour](manage-outdated-endpoints-microsoft-defender-antivirus.md)
- [Gérer les mises à jour forcées en fonction des événements](manage-event-based-updates-microsoft-defender-antivirus.md)
- [Gérer les mises à jour pour les appareils mobiles et les VM](manage-updates-mobile-devices-vms-microsoft-defender-antivirus.md)
- [Antivirus Microsoft Defender dans Windows 10](microsoft-defender-antivirus-in-windows-10.md)
