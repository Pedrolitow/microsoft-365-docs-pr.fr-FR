---
title: Inscrivez vous-même les appareils existant
description: Enregistrer les appareils réutilisés vous avez peut-être déjà des utilisateurs pour qu’ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: a9ff0e76448df183ac5c34c5832155e0b135d313
ms.sourcegitcommit: 22dab0f7604cc057a062698005ff901d40771692
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "46868987"
---
# <a name="register-existing-devices-yourself"></a>Inscrivez vous-même les appareils existant

>[!NOTE]
>Cette rubrique décrit la procédure à suivre pour réutiliser les appareils dont vous disposez déjà et les enregistrer dans le bureau géré Microsoft. Si vous travaillez avec des appareils de marque, suivez plutôt les étapes de la procédure [inscrire de nouveaux appareils dans Microsoft Managed Desktop](register-devices-self.md) .

Le processus pour les partenaires est documenté dans la [procédure permettant aux partenaires d’inscrire des appareils](register-devices-partner.md).

Microsoft Managed Desktop peut fonctionner avec les nouveaux appareils ou vous pouvez réutiliser des appareils que vous avez peut-être déjà (ce qui vous obligera à les réimager). Vous pouvez enregistrer des appareils à l’aide du portail d’administration de bureau géré Microsoft.

## <a name="prepare-to-register-existing-devices"></a>Préparation à l’enregistrement des appareils existants


Pour enregistrer des appareils existants, procédez comme suit :

1. [Obtenez le hachage matériel de chaque périphérique.](#obtain-the-hardware-hash)
2. [Fusionner les données de hachage](#merge-hash-data)
3. [Inscrivez les appareils dans le bureau géré Microsoft](#register-devices-by-using-the-admin-portal).
4. [Vérifiez que l’image est correcte.](#check-the-image)
5. [Remise de l’appareil](#deliver-the-device)

### <a name="obtain-the-hardware-hash"></a>Obtenir le hachage matériel

Microsoft Managed Desktop identifie chaque appareil de manière unique en référençant son hachage matériel. Vous disposez de quatre options pour obtenir ces informations à partir d’appareils que vous utilisez déjà :

- Demandez à votre fournisseur OEM le fichier d’enregistrement automatique du pilote automatique, qui inclut les hachages matériels.
- Collectez des informations dans le [Gestionnaire de configuration de point de terminaison Microsoft](#microsoft-endpoint-configuration-manager).
- Exécutez un script Windows PowerShell, soit à l’aide d' [Active Directory](#active-directory-powershell-script-method) , soit [manuellement](#manual-powershell-script-method) sur chaque appareil, et recueillez les résultats dans un fichier.
- Démarrez chaque périphérique--mais ne terminez pas l’expérience d’installation Windows--et [collectez les hachages sur un lecteur flash amovible](#flash-drive-method).

#### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

Vous pouvez utiliser le gestionnaire de configuration de point de terminaison Microsoft pour collecter les hachages matériels à partir des appareils existants que vous souhaitez enregistrer avec le bureau géré Microsoft.

> [!IMPORTANT]
> Tous les appareils pour lesquels vous souhaitez obtenir ces informations doivent exécuter Windows 10, version 1703 ou ultérieure. 

Si vous avez rempli toutes ces conditions préalables, vous êtes prêt à collecter les informations en procédant comme suit :

1. Dans la console Configuration Manager, sélectionnez **analyse**. 
2. Dans l’espace de travail analyse, développez le nœud **rapports** , développez **rapports**, puis sélectionnez le nœud **général matériel** . 
3. Exécutez le rapport, les **informations du périphérique Windows AutoPilot**et affichez les résultats.
4. Dans la visionneuse de rapports, sélectionnez l’icône **Exporter** , puis choisissez l’option **CSV (valeurs séparées par des virgules)** .
5. Après avoir enregistré le fichier, vous devez filtrer les résultats sur les appareils que vous prévoyez de vous inscrire auprès du bureau géré Microsoft et charger les données dans le [portail d’administration](https://aka.ms/mmdportal)de bureau géré Microsoft, sélectionnez **appareils** dans le volet de navigation de gauche. Sélectionnez **+ inscrire les appareils**; le survol s’ouvre :


Pour plus d’informations, reportez-vous à [la rubrique inscrire des appareils à l’aide du portail d’administration](#register-devices-by-using-the-admin-portal) .


#### <a name="active-directory-powershell-script-method"></a>Méthode de script PowerShell Active Directory

Dans un environnement Active Directory, vous pouvez utiliser l' `Get-WindowsAutoPilotInfo` applet de commande PowerShell pour collecter les informations à distance à partir de périphériques dans des groupes Active Directory à l’aide de WinRM. Vous pouvez également utiliser l' `Get-AD Computer` applet de commande et obtenir des résultats filtrés pour les noms de modèle de matériel spécifiques inclus dans le catalogue. Pour ce faire, vérifiez d’abord ces conditions préalables, puis passez aux étapes suivantes :

- WinRM est activé.
- Les appareils que vous souhaitez enregistrer sont actifs sur le réseau (c’est-à-dire qu’ils ne sont pas déconnectés ou désactivés).
- Assurez-vous que vous disposez d’un paramètre d’informations d’identification de domaine qui a l’autorisation de s’exécuter à distance sur les appareils.
- Assurez-vous que le pare-feu Windows autorise l’accès à WMI. Pour ce faire, procédez comme suit :

    1. Ouvrez le panneau de configuration du **pare-feu Windows Defender** et sélectionnez **autoriser une application ou une fonctionnalité via le pare-feu Windows Defender**.
    
    2. Recherchez **Windows Management Instrumentation (WMI)** dans la liste, activez à la fois **privé et public**, puis cliquez sur **OK**.

1.  Ouvrez une invite PowerShell avec des droits d’administration.

2.  Exécutez l' *un* des scripts suivants :

    ```powershell
    Install-script -name Get-WindowsAutoPilotInfo 
    #example one – leverage Get-ADComputer to enumerate devices 
    Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname>
    ```

    ```powershell 
    #example two – target specific devices: 
    Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
    ```

3. Accéder à tous les répertoires où se trouvent des entrées pour les appareils. Supprimez les entrées de chaque périphérique de *tous les* répertoires, y compris les services de domaine Active Directory Windows Server et Azure Active Directory. N’oubliez pas que cette suppression peut prendre quelques heures.

4. Services de gestion d’accès où il peut y avoir des entrées pour les périphériques. Supprimez les entrées de chaque périphérique de *tous les* services de gestion, y compris le gestionnaire de configuration de point de terminaison Microsoft, Microsoft Intune et Windows AutoPilot. N’oubliez pas que cette suppression peut prendre quelques heures.

À présent, vous pouvez procéder à l' [inscription des appareils](#register-devices-by-using-the-admin-portal).

#### <a name="manual-powershell-script-method"></a>Méthode de script PowerShell manuel

1.  Ouvrez une invite PowerShell avec des droits d’administration.
2.  Générer `Install-Script -Name Get-WindowsAutoPilotInfo`
3.  Générer `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
4. [Fusionnez les données de hachage.](#merge-hash-data)

#### <a name="flash-drive-method"></a>Flash Drive, méthode

1. Sur un appareil autre que celui que vous enregistrez, insérez un lecteur USB.
2. Ouvrez une invite PowerShell avec des droits d’administration.
3. Générer `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. Activez l’appareil que vous enregistrez, mais *ne démarrez pas l’installation*. Si vous démarrez accidentellement le programme d’installation, vous devrez réinitialiser ou recréer l’image de l’appareil.
5. Insérez le lecteur USB, puis appuyez sur MAJ + F10.
6. Ouvrez une invite PowerShell avec des droits d’administration, puis exécutez `cd <pathToUsb>` .
7. Générer `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Générer `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
9. Supprimez le lecteur USB, puis arrêtez l’appareil en exécutant `shutdown -s -t 0`
10. [Fusionnez les données de hachage.](#merge-hash-data)

>[!IMPORTANT]
>Ne mettez pas sous tension le périphérique que vous enregistrez jusqu’à ce que vous ayez terminé son inscription. 



### <a name="merge-hash-data"></a>Fusionner les données de hachage

Si vous avez collecté les données de hachage du matériel à l’aide de la méthode manuelle PowerShell ou Flash Drive, il vous faut maintenant que les données des fichiers CSV soient combinées en un seul fichier pour terminer l’inscription. Voici un exemple de script PowerShell pour faciliter cette tâche :

```powershell
Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv
```

Une fois les données hachées fusionnées dans un fichier CSV, vous pouvez maintenant [enregistrer les appareils](#register-devices-by-using-the-admin-portal).


#### <a name="register-devices-by-using-the-admin-portal"></a>Inscrire des appareils à l’aide du portail d’administration

À partir du portail d' [administration](https://aka.ms/mmdportal)de bureau géré Microsoft, sélectionnez **périphériques** dans le volet de navigation de gauche. Sélectionnez **+ inscrire les appareils**; le survol s’ouvre :

[![Entrée brusque après la sélection d’appareils de caisse, liste des appareils avec des colonnes pour les utilisateurs affectés, numéro de série, État, date de dernière vue et âge](../../media/new-registration-ui.png)](../../media/new-registration-ui.png)


<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->


Procédez comme suit :

1. Dans **chargement du fichier**, indiquez le chemin d’accès au fichier CSV que vous avez créé précédemment.

1. Sélectionnez **inscrire les appareils**. Le système ajoute les périphériques à votre liste d’appareils sur le panneau des **appareils**, marqué comme **AutopilotRegistrationRequested**. L’inscription prend généralement moins de 10 minutes et, lorsque le périphérique s’affiche comme **prêt pour l’utilisateur** , ce qui signifie qu’il est prêt et qu’il attend qu’un utilisateur commence à utiliser.


Vous pouvez surveiller la progression de l’inscription de l’appareil sur la page principale **des périphériques de bureau gérés par Microsoft** . Les États possibles sont les suivants :

| État | Description |
|---------------|-------------|
| AutopilotRegistrationRequested | L’inscription n’est pas encore terminée. Réactivez-vous plus tard. |
| Échec de l’inscription | L’inscription n’a pas pu aboutir. Pour plus d’informations, consultez la rubrique [Troubleshooting Device Registration](#troubleshooting-device-registration) . |
| Prêt pour l’utilisateur | L’inscription a réussi et l’appareil est maintenant prêt à être remis à l’utilisateur final. Microsoft Managed Desktop les guide tout au long du paramétrage, il n’est donc pas nécessaire d’effectuer d’autres préparatifs. |
| Actif | L’appareil a été remis à l’utilisateur final et il a été enregistré auprès de votre client. Cela indique également qu’ils utilisent régulièrement l’appareil. |
| Inactive | L’appareil a été remis à l’utilisateur final et il a été enregistré auprès de votre client. Toutefois, ils n’ont pas utilisé le périphérique récemment (au cours des 7 derniers jours).  | 

#### <a name="troubleshooting-device-registration"></a>Dépannage de l’inscription de l’appareil

| Message d’erreur | Détails |
|---------------|-------------|
| Appareil introuvable | Nous n’avons pas pu inscrire cet appareil, car nous n’avons pas pu trouver de correspondance pour le fabricant, le modèle ou le numéro de série fourni. Vérifiez ces valeurs auprès de votre fournisseur d’appareils. |
| Hachage matériel non valide | Le hachage matériel que vous avez fourni pour cet appareil n’a pas été correctement mis en forme. Vérifiez le hachage matériel, puis renvoyez-le. |
| L’appareil est déjà enregistré | Ce périphérique est déjà enregistré dans votre organisation. Aucune autre action n’est requise. |
| Appareil revendiqué par une autre organisation | Ce périphérique a déjà été revendiqué par une autre organisation. Vérifiez auprès de votre fournisseur d’appareils. |
| Erreur inattendue | Votre demande n’a pas pu être traitée automatiquement. Contactez le support technique et indiquez l’ID de la demande : <requestId> |

### <a name="check-the-image"></a>Vérifier l’image

Si votre appareil vient d’un fournisseur de partenaires de bureau géré Microsoft, l’image doit être correcte.

Si vous le souhaitez, vous pouvez également appliquer l’image par vous-même. Pour commencer, contactez le représentant Microsoft avec lequel vous travaillez et ils vous fourniront l’emplacement et les étapes à suivre pour appliquer l’image.

### <a name="deliver-the-device"></a>Remise de l’appareil

> [!IMPORTANT]
> Avant de remettre l’appareil à votre utilisateur, vérifiez que vous avez obtenu et appliqué les [licences appropriées](../get-ready/prerequisites.md) pour cet utilisateur.

Si toutes les licences sont appliquées, vous pouvez [faire en sorte que vos utilisateurs soient prêts à utiliser les appareils](get-started-devices.md), puis votre utilisateur peut démarrer l’appareil et poursuivre l’installation de Windows.









