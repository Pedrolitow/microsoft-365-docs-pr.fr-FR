---
title: Inscrivez vous-même les nouveaux appareils
description: Inscrire des appareils vous-même afin qu’ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: 48c69a71a98e381123a8f87acc20a34eb6e99806
ms.sourcegitcommit: 34ebec8e2bd54ba3d4ccfd9724797665c965c17f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2020
ms.locfileid: "49071488"
---
# <a name="register-new-devices-yourself"></a>Inscrivez vous-même les nouveaux appareils

Microsoft Managed Desktop peut fonctionner avec les nouveaux appareils ou vous pouvez réutiliser des appareils que vous avez peut-être déjà (ce qui vous obligera à les réimager). Vous pouvez enregistrer des appareils avec le bureau géré Microsoft dans le portail du gestionnaire de points de terminaison Microsoft.

> [!NOTE]
> Vous travaillez avec un partenaire pour obtenir des appareils ? Si c’est le cas, vous n’avez pas à vous soucier de l’obtention des hachages matériels ; ils s’occupent de cela pour vous. Assurez-vous que votre partenaire établit une relation avec vous dans le [Centre de partenaires](https://partner.microsoft.com/dashboard). Votre partenaire peut en savoir plus sur [l’aide du centre de partenaires](https://docs.microsoft.com/partner-center/request-a-relationship-with-a-customer). Une fois que cette relation est établie, votre partenaire enregistrera simplement les appareils de votre part, aucune autre action n’est requise de votre part. Si vous souhaitez consulter les détails ou si votre partenaire a des questions, consultez les [étapes pour les partenaires d’inscription des appareils](register-devices-partner.md). Une fois les appareils enregistrés, vous pouvez procéder à la [vérification de l’image](#check-the-image) et à [la remise des périphériques](#deliver-the-device) à vos utilisateurs.

## <a name="prepare-to-register-brand-new-devices"></a>Préparation à l’enregistrement de nouveaux appareils


Une fois que vous avez les nouveaux appareils en main, procédez comme suit :

1. [Obtenez le hachage matériel de chaque périphérique.](#obtain-the-hardware-hash)
2. [Fusionner les données de hachage](#merge-hash-data)
3. [Inscrivez les appareils dans le bureau géré Microsoft](#register-devices-by-using-the-admin-portal).
4. [Vérifiez que l’image est correcte.](#check-the-image)
5. [Remise de l’appareil](#deliver-the-device)

### <a name="obtain-the-hardware-hash"></a>Obtenir le hachage matériel

Microsoft Managed Desktop identifie chaque appareil de manière unique en référençant son hachage matériel. Vous disposez de trois options pour obtenir ces informations :

- Demandez à votre fournisseur OEM le fichier d’enregistrement automatique du pilote automatique, qui inclut les hachages matériels.
- Exécutez un [script Windows PowerShell](#powershell-script-method) sur chaque appareil et recueillez les résultats dans un fichier.
- Démarrez chaque périphérique--mais ne terminez pas l’expérience d’installation Windows--et [collectez les hachages sur un lecteur flash amovible](#flash-drive-method).

#### <a name="powershell-script-method"></a>Méthode de script PowerShell

Vous pouvez utiliser le script PowerShell [Get-WindowsAutoPilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) sur le site Web de la Galerie PowerShell. Pour plus d’informations sur l’identification du périphérique et le hachage du matériel, consultez la rubrique [Ajout de périphériques à Windows AutoPilot](https://docs.microsoft.com/mem/autopilot/add-devices#device-identification).

1.  Ouvrez une invite PowerShell avec des droits d’administration.
2.  Générer `Install-Script -Name Get-WindowsAutoPilotInfo`
3.  Générer `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
4.  Exécutez `powershell -ExecutionPolicy restricted` pour empêcher l’exécution des scripts non restreints suivants.


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

>[!IMPORTANT]
>Ne mettez pas sous tension le périphérique que vous enregistrez jusqu’à ce que vous ayez terminé son inscription. 


### <a name="merge-hash-data"></a>Fusionner les données de hachage

Les données des fichiers CSV doivent être regroupées en un seul fichier pour terminer l’inscription. Voici un exemple de script PowerShell pour faciliter cette tâche :

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`


#### <a name="register-devices-by-using-the-admin-portal"></a>Inscrire des appareils à l’aide du portail d’administration

Dans le [Gestionnaire de points de terminaison Microsoft](https://endpoint.microsoft.com/), sélectionnez **périphériques** dans le volet de navigation de gauche. Recherchez la section bureau géré Microsoft du menu et sélectionnez **appareils**. Dans l’espace de travail périphériques de bureau gérés Microsoft, sélectionnez **+ inscrire les appareils** qui ouvrent un survol pour enregistrer de nouveaux appareils.

<!-- [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->


<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->


Procédez comme suit :

1. Dans **chargement du fichier** , indiquez le chemin d’accès au fichier CSV que vous avez créé précédemment.
3. Sélectionnez **inscrire les appareils**. Le système ajoute les périphériques à votre liste d’appareils sur le panneau des **appareils** , marqué comme **inscription en attente**. L’inscription prend généralement moins de 10 minutes et, lorsque le périphérique s’affiche comme **prêt pour l’utilisateur** , ce qui signifie qu’il est prêt et qu’il attend qu’un utilisateur commence à utiliser.


Vous pouvez surveiller la progression de l’enregistrement de l’appareil sur la page principale. Les États possibles sont les suivants :

| État | Description |
|---------------|-------------|
| Inscription en attente | L’inscription n’est pas encore terminée. Réactivez-vous plus tard. |
| Échec de l’inscription | L’inscription n’a pas pu aboutir. Pour plus d’informations, consultez la rubrique [Troubleshooting Device Registration](#troubleshooting-device-registration) . |
| Prêt pour l’utilisateur | L’inscription a réussi et l’appareil est maintenant prêt à être remis à l’utilisateur. Microsoft Managed Desktop les guide tout au long du paramétrage, il n’est donc pas nécessaire d’effectuer d’autres préparatifs. |
| Actif | L’appareil a été remis à l’utilisateur et il a été enregistré auprès de votre client. Cela indique également qu’ils utilisent régulièrement l’appareil. |
| Inactive | L’appareil a été remis à l’utilisateur et il a été enregistré auprès de votre client. Toutefois, ils n’ont pas utilisé le périphérique récemment (au cours des 7 derniers jours).  | 

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





