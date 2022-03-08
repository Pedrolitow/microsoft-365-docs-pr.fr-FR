---
title: Inscription manuelle pour les appareils existants
description: Inscrire des appareils existants afin qu’ils soient gérés par Microsoft Manged Desktop
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
manager: dougeby
ms.topic: article
audience: Admin
ms.openlocfilehash: 1d100cc3336dcb465e54f4b81d13d50ecd4bfe1e
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63319085"
---
# <a name="manual-registration-for-existing-devices"></a>Inscription manuelle pour les appareils existants

>[!NOTE]
>Cet article décrit les étapes à suivre pour réutiliser les appareils que vous avez déjà et les inscrire dans Microsoft Manged Desktop. Si vous travaillez avec de nouveaux appareils, suivez les étapes de l’étape Enregistrer les nouveaux [appareils Microsoft Manged Desktop vous-même](manual-registration.md) à la place. <br> <br> Le processus pour les partenaires est documenté dans la procédure [d’inscription des appareils par les partenaires](partner-registration.md).

Microsoft Manged Desktop pouvez utiliser de nouveaux appareils, ou vous pouvez réutiliser les appareils que vous avez peut-être déjà. Si vous réutilisez des appareils, vous devez les réimager. Vous pouvez inscrire des appareils avec des Microsoft Manged Desktop dans le portail Microsoft Endpoint Manager client.

## <a name="prepare-to-register-existing-devices"></a>Préparer l’inscription des appareils existants

**Pour inscrire des appareils existants :**

1. [Obtenez le hachage matériel pour chaque appareil.](#obtain-the-hardware-hash)
2. [Fusionnez les données de hachage](#merge-hash-data).
3. [Inscrivez les appareils dans Microsoft Manged Desktop](#register-devices-by-using-the-admin-portal).
4. [Vérifiez que l’image est correcte.](#check-the-image)
5. [Remettre l’appareil](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Obtenir le hachage matériel

Microsoft Manged Desktop identifie chaque appareil de manière unique en référentant son hachage matériel. Vous avez quatre options pour obtenir ces informations à partir des appareils que vous utilisez déjà.

**Pour obtenir le hachage matériel :**

- Demandez à votre fournisseur OEM le fichier d’inscription AutoPilot, qui inclut les hages matériels.
- Collecter des informations [dans Microsoft Endpoint Configuration Manager](#microsoft-endpoint-configuration-manager).
- Exécutez un script Windows PowerShell à l’aide [d’Active Directory](#active-directory-powershell-script-method), [](#manual-powershell-script-method) ou manuellement sur chaque appareil, et collectez les résultats dans un fichier.
- Démarrez chaque appareil, mais n’avez pas terminé l’Windows de configuration et collectez les hages sur un [disque mémoire amovible](#flash-drive-method).

#### <a name="microsoft-endpoint-configuration-manager"></a>Microsoft Endpoint Configuration Manager

Vous pouvez utiliser Microsoft Endpoint Configuration Manager pour collecter les hages matériels à partir d’appareils existants que vous souhaitez inscrire auprès Microsoft Manged Desktop. Si vous avez satisfait à toutes ces conditions préalables, vous êtes prêt à collecter les informations.

> [!IMPORTANT]
> Tous les appareils pour qui vous souhaitez obtenir ces informations doivent être en cours d Windows 10 version 1703 ou ultérieure.

**Pour collecter les informations de hachage matériel :**

1. Dans la console Configuration Manager, sélectionnez **Surveillance**.
2. Dans l’espace de travail Surveillance,  développez le nœud Rapports, développez **Rapports** et sélectionnez le nœud Matériel **-** Général.
3. Exécutez le rapport, **Windows autopilot Device Information** et affichez les résultats.
4. Dans la visionneuse de rapports,  sélectionnez l’icône Exporter, puis l’option **CSV (** délimitée par des virgules).
5. Après avoir enregistré le fichier, vous devez filtrer les résultats uniquement sur les appareils que vous prévoyez d’inscrire auprès Microsoft Manged Desktop. Ensuite, téléchargez les données dans Microsoft Manged Desktop.
    - Ouvrez Microsoft Endpoint Manager et accédez au menu **Appareils**.
    - Dans la section Microsoft Manged Desktop, sélectionnez **Appareils**.
    - **Sélectionnez + Inscrivez les** appareils, ce qui ouvre un fly-in pour inscrire de nouveaux appareils.

Pour plus d’informations, voir [Inscrire des appareils à l’aide du portail d’administration ci-dessous](#register-devices-by-using-the-admin-portal) .

#### <a name="active-directory-powershell-script-method"></a>Méthode de script PowerShell Active Directory

Dans un environnement Active Directory, `Get-WindowsAutoPilotInfo` vous pouvez utiliser l’applet de commande PowerShell pour collecter à distance les informations des appareils des groupes Active Directory à l’aide de WinRM. Vous pouvez également utiliser l’cmdlet `Get-AD Computer` et obtenir des résultats filtrés pour un nom de modèle matériel spécifique inclus dans le catalogue. Avant de continuer, confirmez ces conditions préalables, puis continuez.

**Pour utiliser la méthode de script PowerShell Active Directory :**

1. Assurez-vous que WinRM est activé.
1. Les appareils que vous souhaitez inscrire sont actifs sur le réseau. Autrement dit, ils ne sont pas déconnectés ou désactivés.
1. Assurez-vous que vous disposez d’un paramètre d’informations d’identification de domaine autorisé à s’exécuter à distance sur les appareils.
1. Assurez-vous Windows pare-feu permet d’accéder à WMI. Pour ce faire, procédez comme suit :

    - Ouvrez le **panneau Windows Defender pare-feu** et sélectionnez Autoriser une application ou une **fonctionnalité via Windows Defender pare-feu**.
    - **Recherchez Windows Management Instrumentation (WMI)** dans la liste, activez pour privé et **public**, puis sélectionnez **OK**.
1. Ouvrez une invite PowerShell avec des droits d’administration.
1. *Exécutez l’un* des scripts suivants :

    ```powershell
    Install-script -name Get-WindowsAutoPilotInfo 
    #example one – leverage Get-ADComputer to enumerate devices 
    Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname>
    ```

    ```powershell
    #example two – target specific devices: 
    Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
    ```

1. Accéder aux répertoires où il peut y avoir des entrées pour les appareils. Supprimez les entrées de chaque appareil de *tous* les répertoires, y Windows Server Active Directory services de domaine et Azure Active Directory. Le traitement complet peut prendre quelques heures.
1. Accéder aux services de gestion où il peut y avoir des entrées pour les appareils. Supprimez les entrées de  chaque appareil de tous les services de gestion, notamment Microsoft Endpoint Configuration Manager, Microsoft Intune et Windows Autopilot. Le traitement complet peut prendre quelques heures.

Vous pouvez maintenant enregistrer [des appareils](#register-devices-by-using-the-admin-portal).

#### <a name="manual-powershell-script-method"></a>Méthode de script PowerShell manuelle

**Pour utiliser la méthode de script Powershell manuelle :**

1. Ouvrez une invite PowerShell avec des droits d’administration.
2. Exécutez `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Exécutez `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. [Fusionnez les données de hachage.](#merge-hash-data)

#### <a name="flash-drive-method"></a>Méthode de lecteur Flash

**Pour utiliser la méthode de lecteur flash :**

1. Sur un appareil autre que celui que vous inscrivez, insérez un lecteur USB.
2. Ouvrez une invite PowerShell avec des droits d’administration.
3. Exécutez `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`.
4. Activer l’appareil que vous inscrivez, mais *ne démarrez pas l’expérience d’installation*. Si vous démarrez accidentellement l’expérience d’installation, vous devez réinitialiser ou réinitialiser l’appareil.
5. Insérez le lecteur USB, puis appuyez sur Shift + F10.
6. Ouvrez une invite PowerShell avec des droits d’administration, puis exécutez `cd <pathToUsb>`.
7. Exécutez `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`.
8. Exécutez `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
9. Supprimez le lecteur USB, puis fermez l’appareil en l’exécutant `shutdown -s -t 0`.
10. [Fusionnez les données de hachage.](#merge-hash-data)

> [!IMPORTANT]
> N’alimentation sur l’appareil que vous inscrivez à nouveau tant que vous n’avez pas terminé l’inscription pour celui-ci.

### <a name="merge-hash-data"></a>Fusionner les données de hachage

Si vous avez collecté les données de hachage matériel par le manuel PowerShell ou les méthodes de disque mémoire flash, vous devez combiner les données des deux fichiers CSV dans un seul fichier pour terminer l’inscription. Voici un exemple de script PowerShell pour faciliter l’accès :

```powershell
Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv
```

Une fois les données de hachage fusionnées dans un fichier CSV, vous pouvez désormais enregistrer [les appareils](#register-devices-by-using-the-admin-portal).

## <a name="register-devices-by-using-the-admin-portal"></a>Inscrire des appareils à l’aide du portail d’administration

Dans [Microsoft Endpoint Manager](https://endpoint.microsoft.com/), sélectionnez **Appareils dans** le volet de navigation de gauche. Dans la section Microsoft Manged Desktop, sélectionnez **Appareils**. Dans l Microsoft Manged Desktop de travail Appareils, sélectionnez **+** Inscrivez les appareils, ce qui ouvre un fly-in pour inscrire de nouveaux appareils.

<!-- Update with new picture [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Pour inscrire des appareils à l’aide du portail d’administration :**

1. Dans **le téléchargement de** fichier, fournissez un chemin d’accès au fichier CSV que vous avez créé précédemment.
2. Sélectionnez [un profil d’appareil](../service-description/profiles.md) dans le menu déroulant.
3. Sélectionnez **Enregistrer les appareils**. Le système ajoute les appareils à votre liste d’appareils sur le **blade Devices**. Les appareils sont marqués comme **étant en attente d’inscription**. L’inscription prend généralement moins de 10 minutes et, en cas de réussite, l’appareil s’affiche **comme prêt pour l’utilisateur**. **Prêt pour l’utilisateur** signifie qu’il est prêt et qu’il attend qu’un utilisateur commence à l’utiliser.

> [!NOTE]
> Si vous modifiez manuellement l’appartenance au groupe Azure Active Directory (AAD) d’un appareil, il sera automatiquement réassigné au groupe pour son profil d’appareil et supprimé des groupes en conflit.

Vous pouvez surveiller la progression de l’inscription de l’appareil sur la page principale. Les états possibles signalés sont les suivants :

| État | Description |
| ----- | ----- |
| Inscription en attente | L’inscription n’est pas encore terminée. Revenir plus tard. |
| Échec de l’inscription | L’inscription n’a pas pu être terminée. Pour plus d’informations, voir [Troubleshooting device registration](#troubleshooting-device-registration). |
| Prêt pour l’utilisateur | L’inscription a réussi. L’appareil est maintenant prêt à être remis à l’utilisateur. Microsoft Manged Desktop les guide tout au long de la première mise en place, vous n’avez donc pas besoin d’autres préparations. |
| Actif | L’appareil a été remis à l’utilisateur et il s’est inscrit auprès de votre client. Cet état indique également qu’ils utilisent régulièrement l’appareil. |
| Inactif | L’appareil a été remis à l’utilisateur et il s’est inscrit auprès de votre client. Toutefois, l’utilisateur n’a pas utilisé l’appareil récemment (au cours des sept derniers jours). |

### <a name="troubleshooting-device-registration"></a>Résolution des problèmes d’inscription de l’appareil

| Message d’erreur | Détails |
| ----- | ----- |
| Appareil in trouvé | Nous n’avons pas pu enregistrer cet appareil car nous n’avons pas pu trouver de correspondance pour le fabricant, le modèle ou le numéro de série fourni. Confirmez ces valeurs auprès de votre fournisseur d’appareils. |
| Hachage matériel non valide | Le hachage matériel que vous avez fourni pour cet appareil n’a pas été mis en forme correctement. Vérifiez à nouveau le hachage matériel, puis resoumettre. |
| Appareil déjà inscrit | Cet appareil est déjà inscrit dans votre organisation. Aucune action supplémentaire n’est requise. |
| Appareil revendiqué par une autre organisation | Cet appareil a déjà été revendiqué par une autre organisation. Vérifiez auprès de votre fournisseur d’appareils. |
| Erreur inattendue | Votre demande n’a pas pu être traitée automatiquement. Contactez le support technique et fournissez l’ID de demande : `<requestId>` |

## <a name="check-the-image"></a>Vérifier l’image

Si votre appareil est issu d’un fournisseur Microsoft Manged Desktop partenaire, l’image doit être correcte.

Vous pouvez également appliquer l’image vous-même si vous le souhaitez. To get started, contact the Microsoft representative you’re working with and they’ll provide you the location and steps for applying the image.

## <a name="deliver-the-device"></a>Remettre l’appareil

> [!IMPORTANT]
> Avant de remettre l’appareil à votre utilisateur, assurez-vous que vous avez obtenu et appliqué les [licences](../get-ready/prerequisites.md) appropriées pour cet utilisateur.

Si toutes les licences sont appliquées, vous pouvez préparer vos utilisateurs [à utiliser les appareils](get-started-devices.md). Ensuite, votre utilisateur peut démarrer l’appareil et passer à l’Windows d’installation.
