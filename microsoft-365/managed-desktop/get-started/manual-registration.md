---
title: Inscription manuelle
description: Inscrire les appareils à gérer par les Microsoft Manged Desktop
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
ms.openlocfilehash: aaa1446cbb1ffdc20b023f568a7fd41d6cf01848
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63330864"
---
# <a name="manual-registration"></a>Inscription manuelle

Microsoft Manged Desktop pouvez utiliser de nouveaux appareils, ou vous pouvez réutiliser les appareils que vous avez peut-être déjà. Si vous réutilisez des appareils, vous devez les réimager. Vous pouvez inscrire des appareils avec des Microsoft Manged Desktop dans le portail Microsoft Endpoint Manager client.

> [!NOTE]
> Vous travaillez avec un partenaire pour obtenir des appareils ? Si c’est le cas, vous n’avez pas besoin de vous soucier de l’obtention des hashes matériels ; Ils s’en chargeront pour vous. Assurez-vous que votre partenaire établit une relation avec vous dans [l’Partner Center](https://partner.microsoft.com/dashboard). Votre partenaire peut en savoir plus sur [l’aide de l’Centre partenaires](/partner-center/request-a-relationship-with-a-customer). <br><br>Une fois cette relation établie, votre partenaire enregistre simplement des appareils en votre nom ; aucune autre action n’est requise de votre part. Si vous souhaitez consulter les détails ou si votre partenaire a des questions, consultez [l’inscription du partenaire](partner-registration.md). Une fois les appareils inscrits, vous pouvez vérifier [l’image](#check-the-image) et [remettre](#deliver-the-device) les appareils à vos utilisateurs.

## <a name="prepare-to-register-brand-new-devices"></a>Préparer l’inscription de nouveaux appareils

Une fois que vous avez les nouveaux appareils en main, vous devez suivre les étapes suivantes :

1. [Obtenez le hachage matériel pour chaque appareil.](#obtain-the-hardware-hash)
2. [Fusionnez les données de hachage](#merge-hash-data).
3. [Inscrivez les appareils dans Microsoft Manged Desktop](#register-devices-by-using-the-admin-portal).
4. [Vérifiez que l’image est correcte.](#check-the-image)
5. [Remettre l’appareil](#deliver-the-device).

### <a name="obtain-the-hardware-hash"></a>Obtenir le hachage matériel

Microsoft Manged Desktop identifie chaque appareil de manière unique en référentant son hachage matériel. Vous avez trois options pour obtenir ces informations.

**Pour obtenir le hachage matériel :**

- Demandez à votre fournisseur OEM le fichier d’inscription AutoPilot, qui inclut les hages matériels.
- Exécutez [un script Windows PowerShell sur](#powershell-script-method) chaque appareil et collectez les résultats dans un fichier.
- Démarrez chaque appareil, mais n’avez pas terminé l’Windows de configuration et collectez les hages sur un [disque mémoire amovible](#flash-drive-method).

#### <a name="powershell-script-method"></a>Méthode de script PowerShell

Vous pouvez utiliser le script [ PowerShellGet-WindowsAutoPilotInfo.ps1](https://www.powershellgallery.com/packages/Get-WindowsAutoPilotInfo) sur le site web de la galerie PowerShell. Pour plus d’informations sur l’identification de l’appareil et le hachage matériel, voir Ajout d’appareils [Windows Autopilot](/mem/autopilot/add-devices#device-identification).

**Pour utiliser la méthode de script PowerShell :**

1. Ouvrez une invite PowerShell avec des droits d’administration.
2. Exécutez `Install-Script -Name Get-WindowsAutoPilotInfo`.
3. Exécutez `powershell -ExecutionPolicy Unrestricted Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`.
4. Exécutez `powershell -ExecutionPolicy restricted` cette exécution pour empêcher l’exécution de scripts non restreints ultérieurs.

#### <a name="flash-drive-method"></a>Méthode de lecteur Flash

**Pour utiliser la méthode de lecteur flash :**

1. Sur un appareil autre que celui que vous inscrivez, insérez un lecteur USB.
2. Ouvrez une invite PowerShell avec des droits d’administration.
3. Exécutez `Save-Script -Name Get-WindowsAutoPilotInfo -Path <pathToUsb>`
4. Activer l’appareil que vous inscrivez, mais *ne démarrez pas l’expérience d’installation*. Si vous démarrez accidentellement l’expérience d’installation, vous devez réinitialiser ou réinitialiser l’appareil.
5. Insérez le lecteur USB, puis appuyez sur Shift + F10.
6. Ouvrez une invite PowerShell avec des droits d’administration, puis exécutez `cd <pathToUsb>`.
7. Exécutez `Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Exécutez `.\Get-WindowsAutoPilotInfo -OutputFile <path>\hardwarehash.csv`
9. Supprimez le lecteur USB, puis fermez l’appareil en exécutant `shutdown -s -t 0`

> [!IMPORTANT]
> N’alimentation sur l’appareil que vous inscrivez à nouveau tant que vous n’avez pas terminé l’inscription pour celui-ci.

### <a name="merge-hash-data"></a>Fusionner les données de hachage

Les données des fichiers CSV doivent être combinées en un seul fichier pour terminer l’inscription. Voici un exemple de script PowerShell pour faciliter l’accès :

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`

> [!NOTE]
> Les colonnes supplémentaires ne sont pas pris en charge. Les guillemets ne sont pas pris en charge. Seuls les fichiers texte au format ANSI peuvent être utilisés (et non Unicode). Les en-têtes sont sensibles à la cas. La modification du fichier dans Excel et son enregistrement en tant que fichier CSV ne génèreront pas de fichier utilisable en raison de ces exigences. N’oubliez pas de conserver les zéros non élevés dans les numéros de série de l’appareil.

### <a name="register-devices-by-using-the-admin-portal"></a>Inscrire des appareils à l’aide du portail d’administration

Dans [Microsoft Endpoint Manager](https://endpoint.microsoft.com/), sélectionnez **Appareils dans** le volet de navigation de gauche. Dans la section Microsoft Manged Desktop, sélectionnez **Appareils**. Dans l Microsoft Manged Desktop de travail Appareils, sélectionnez **+** Inscrivez les appareils, ce qui ouvre un fly-in pour inscrire de nouveaux appareils.

<!-- [![Fly-in after selecting Register devices, listing devices with columns for assigned users, serial number, status, last-seen date, and age.](../../media/new-registration-ui.png)](../../media/new-registration-ui.png) -->

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->

**Pour inscrire des appareils à l’aide du portail d’administration :**

1. Dans **le téléchargement de** fichier, fournissez un chemin d’accès au fichier CSV que vous avez créé précédemment.
2. Sélectionnez [un profil d’appareil](../service-description/profiles.md) dans le menu déroulant.
3. Sélectionnez **Enregistrer les appareils**. Le système ajoute les appareils à votre liste d’appareils sur les **appareils,** marqués comme **étant en attente d’inscription**. L’inscription prend généralement moins de 10 minutes et, en cas de réussite, l’appareil s’affiche comme prêt pour l’utilisateur, ce qui signifie qu’il est prêt et en attente qu’un utilisateur commence à l’utiliser.

> [!NOTE]
> Si vous modifiez manuellement l’appartenance au groupe Azure Active Directory (AAD) d’un appareil, il sera automatiquement réassigné au groupe pour son profil d’appareil et supprimé des groupes en conflit.

Vous pouvez surveiller la progression de l’inscription de l’appareil sur la page principale. Les états possibles signalés sont les suivants :

| État | Description |
| -----|-----|
| Inscription en attente | L’inscription n’est pas encore terminée. Revenir plus tard. |
| Échec de l’inscription | L’inscription n’a pas pu être terminée. Pour plus d’informations, voir [Troubleshooting device registration](#troubleshooting-device-registration). |
| Prêt pour l’utilisateur | L’inscription a réussi. L’appareil est maintenant prêt à être remis à l’utilisateur. Microsoft Manged Desktop les guide tout au long de la première mise en place, vous n’avez donc pas besoin d’autres préparations. |
| Actif | L’appareil a été remis à l’utilisateur et il s’est inscrit auprès de votre client. Cet état indique également qu’ils utilisent régulièrement l’appareil. |
| Inactif | L’appareil a été remis à l’utilisateur et il s’est inscrit auprès de votre client. Toutefois, ils n’ont pas utilisé l’appareil récemment (au cours des sept derniers jours).  |

#### <a name="troubleshooting-device-registration"></a>Résolution des problèmes d’inscription de l’appareil

| Message d’erreur | Détails |
|-----| ----- |
| Appareil in trouvé | Nous n’avons pas pu enregistrer cet appareil car nous n’avons pas pu trouver de correspondance pour le fabricant, le modèle ou le numéro de série fourni. Confirmez ces valeurs auprès de votre fournisseur d’appareils. |
| Hachage matériel non valide | Le hachage matériel que vous avez fourni pour cet appareil n’a pas été mis en forme correctement. Vérifiez à nouveau le hachage matériel, puis resoumettre. |
| Appareil déjà inscrit | Cet appareil est déjà inscrit dans votre organisation. Aucune action supplémentaire n’est requise. |
| Appareil revendiqué par une autre organisation | Cet appareil a déjà été revendiqué par une autre organisation. Vérifiez auprès de votre fournisseur d’appareils. |
| Erreur inattendue | Votre demande n’a pas pu être traitée automatiquement. Contactez le support technique et fournissez l’ID de demande : `<requestId>` |

### <a name="check-the-image"></a>Vérifier l’image

Si votre appareil est issu d’un fournisseur de partenaire Bureau géré Microsoft, l’image doit être correcte.

Vous pouvez également appliquer l’image vous-même si vous le souhaitez. Pour commencer, contactez le représentant Microsoft avec qui vous travaillez. Le représentant vous fournira l’emplacement et les étapes d’application de l’image.

### <a name="autopilot-group-tag"></a>Balise de groupe Autopilot

Lorsque vous utilisez le portail d’administration pour inscrire des appareils, nous attribuons automatiquement la balise de groupe Autopilot associée au profil d’appareil répertorié dans Inscrire les appareils à l’aide de [l’Partner Center](partner-registration.md).
Le service surveille tous les appareils Bureau géré Microsoft quotidiennement et affecte la balise de groupe à ceux qui ne l’ont pas encore.

### <a name="deliver-the-device"></a>Remettre l’appareil

> [!IMPORTANT]
> Avant de remettre l’appareil à votre utilisateur, assurez-vous que vous avez obtenu et appliqué les [licences](../get-ready/prerequisites.md) appropriées pour cet utilisateur.

Si toutes les licences sont appliquées, vous pouvez préparer vos utilisateurs [à utiliser des appareils](get-started-devices.md). Ensuite, votre utilisateur peut démarrer l’appareil et passer à l’expérience d’installation de Windows.