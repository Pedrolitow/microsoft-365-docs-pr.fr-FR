---
title: Inscrivez vous-même les appareils existant
description: Enregistrer les appareils réutilisés vous avez peut-être déjà des utilisateurs pour qu’ils puissent être gérés par le bureau géré Microsoft
ms.prod: w10
author: jaimeo
ms.author: jaimeo
ms.localizationpriority: medium
ms.openlocfilehash: 51db9c88710605c6203023b343edc4359556d57d
ms.sourcegitcommit: 9aaedbab11fd1a1d289eeb8f853d321f32cb7edc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/17/2019
ms.locfileid: "37577770"
---
# <a name="register-existing-devices-yourself"></a>Inscrivez vous-même les appareils existant

>[!NOTE]
>Cette rubrique décrit la procédure à suivre pour réutiliser les appareils dont vous disposez déjà et les enregistrer dans le bureau géré Microsoft. Si vous travaillez avec des appareils de marque, suivez plutôt les étapes de la procédure [inscrire de nouveaux appareils dans Microsoft Managed Desktop](register-devices-self.md) .

Le processus pour les partenaires est documenté dans la [procédure permettant aux partenaires d’inscrire des appareils](register-devices-partner.md).

Microsoft Managed Desktop peut fonctionner avec les nouveaux appareils ou vous pouvez réutiliser des appareils que vous avez peut-être déjà (ce qui vous obligera à les réimager). Vous pouvez enregistrer des appareils à l’aide de Microsoft Managed Desktop sur le portail Azure.

## <a name="prepare-to-register-existing-devices"></a>Préparation à l’enregistrement des appareils existants


Pour enregistrer des appareils existants, procédez comme suit :

1. [Obtenez le hachage matériel de chaque périphérique.](#obtain-the-hardware-hash)
2. [Fusionner les données de hachage](#merge-hash-data)
3. [Inscrivez les appareils dans le bureau géré Microsoft](#register-devices).
4. [Vérifiez que l’image est correcte.](#check-the-image)
5. [Remise de l’appareil](#deliver-the-device)

### <a name="obtain-the-hardware-hash"></a>Obtenir le hachage matériel

Microsoft Managed Desktop identifie chaque appareil de manière unique en référençant son hachage matériel. Vous disposez de quatre options pour obtenir ces informations à partir d’appareils que vous utilisez déjà :

- Demandez à votre fournisseur OEM le fichier d’enregistrement automatique du pilote automatique, qui inclut les hachages matériels.
- Créez un rapport personnalisé dans le [Gestionnaire de configuration](#configuration-manager).
- Exécutez un script Windows PowerShell, soit à l’aide d' [Active Directory](#active-directory-powershell-script-method) , soit [manuellement](#manual-powershell-script-method) sur chaque appareil, et recueillez les résultats dans un fichier.
- Démarrez chaque périphérique--mais ne terminez pas l’expérience d’installation Windows--et [collectez les hachages sur un lecteur flash amovible](#flash-drive-method).

#### <a name="configuration-manager"></a>Configuration Manager

Vous pouvez utiliser System Center Configuration Manager pour collecter les hachages matériels à partir des appareils existants que vous souhaitez enregistrer avec le bureau géré Microsoft.

> [!IMPORTANT]
> Tous les appareils pour lesquels vous souhaitez obtenir ces informations doivent exécuter Windows 10, version 1703 ou ultérieure. Vous avez également besoin d’un appareil qui est un client du gestionnaire de configuration connecté au site de la succursale actuelle de System Center. Vous avez également besoin du rôle système de site de création de rapports dans votre environnement avec SQL Server Reporting Services activé. 

Si vous avez rempli toutes ces conditions préalables, vous êtes prêt à collecter les informations en procédant comme suit :

1. Dans la console Configuration Manager, sélectionnez **analyse**. 
2. Dans l’espace de travail analyse, développez **rapports**, puis sélectionnez **rapports**. 
3. Sous l’onglet **Accueil** , dans la section **créer** , sélectionnez **créer un rapport** pour ouvrir l’assistant créer un rapport. 
4. Sur la page d' **informations** , définissez les paramètres suivants : 
    - **Nom :** Spécifiez un nom pour le rapport. 
    - **Description :** Spécifiez une description pour le rapport. 
    - **Serveur :** Affiche le nom du serveur de rapports sur lequel vous créez ce rapport. 
    - **Chemin d’accès :** Sélectionnez **Parcourir** pour spécifier le dossier dans lequel vous souhaitez stocker le rapport. 
5. Sélectionnez **Suivant**. 
6. Sur la page **Résumé** , passez en revue les paramètres. Sélectionnez **précédent** pour modifier les paramètres ou cliquez sur **suivant** pour créer le rapport dans le gestionnaire de configuration. 
7. Sur la **dernière page,** sélectionnez **Fermer** pour quitter l’Assistant et ouvrir le **Générateur d’États** pour entrer les paramètres du rapport. Entrez votre compte d’utilisateur et votre mot de passe si vous y êtes invité, puis sélectionnez **OK.** Si le générateur de rapports n’est pas installé sur l’appareil, vous êtes invité à l’installer. Sélectionnez **exécuter pour installer le générateur**de rapports, qui est requis pour modifier et créer des rapports. 


**Dans le générateur de rapports Microsoft**, fournissez l’instruction SQL pour le rapport et procédez comme suit :

1. Dans le volet gauche, sélectionnez **jeux de données**, puis cliquez avec le bouton droit pour **Ajouter un jeu de données**.
2. Accédez à l’onglet **requête** , puis entrez le nom *DataSet0*. 
3. Sélectionnez **utiliser un jeu de données incorporé dans mon rapport**; Le générateur de rapports s’ouvre.
4. Dans le **Générateur de rapports**, sélectionnez source de **données :**. Sélectionnez la source de données par défaut, qui doit commencer par « AutoGen ». 
5. Choisissez **type de requête en tant que texte**, puis entrez la requête suivante :

```

SELECT comp.manufacturer0      AS Manufacturer,  
       comp.model0             AS Model,  
       bios.serialnumber0      AS Serial_Number,  
       mdm.devicehardwaredata0 AS HardwareHash  
FROM   Fn_rbac_gs_computer_system(@UserSIDs) comp  
       INNER JOIN Fn_rbac_gs_pc_bios(@UserSIDs) bios  
               ON comp.resourceid = bios.resourceid  
       INNER JOIN Fn_rbac_gs_mdm_devdetail_ext01(@UserSIDs) mdm  
               ON comp.resourceid = mdm.resourceid


```
5. Accédez à l’onglet **champ** , les valeurs Wehre pour le **nom de champ** et la source de **champ** doivent déjà être remplies. Si ce n’est pas le cas, sélectionnez **Ajouter**, puis sélectionnez **champ de requête**. Entrez le **nom du champ** et la **source du champ**.
6. Répétez l’opération pour chacune de ces valeurs : 
    - Constructeur 
    - Modèle 
    - Numéro_de_série 
    - HardwareHash
7. Sélectionnez **OK**.

**Ensuite, définissez l’affichage du rapport et créez le rapport** en procédant comme suit :

1. Sélectionnez **tableau ou matrice**; un nouvel Assistant s’ouvre.
2. Dans **choisir un jeu de données**, sélectionnez **choisir un jeu de données existant dans ce rapport ou un jeu de données partagé**.  
3. Sélectionnez **DataSet0** (valeur par défaut), puis cliquez sur **suivant**.
4. Faites glisser **fabricant**, **modèle**et **numéro de série** dans la zone **groupes de lignes** . Faites glisser **HardwareHash** dans la zone **valeurs** , puis sélectionnez **suivant**.
5. Désactivez les cases à cocher pour afficher les sous- **totaux et les totaux** et **développer/réduire les groupes**. Sélectionnez **Suivant**.
6. Sélectionnez **Terminer**.
7. Sélectionnez **exécuter** pour exécuter votre rapport. Vérifiez que le rapport fournit les informations que vous attendez. Si nécessaire, sélectionnez **conception** pour revenir au mode création afin de modifier le rapport.
8. Sélectionnez **Enregistrer** pour enregistrer le rapport sur le serveur de rapports. Vous pouvez exécuter le nouvel État dans le nœud rapports de l’espace de travail analyse. 

**Enfin, exportez le rapport et utilisez-le pour enregistrer des appareils** en procédant comme suit. (Vous devez uniquement suivre les étapes 1 et 2 de cette section si vous avez quitté l’installation après les étapes précédentes.) :

1. Dans la console Configuration Manager, sélectionnez **analyse**.
2. Dans **analyse**, développez **création**de rapports, puis sélectionnez **rapports**.
3. Recherchez le rapport à l’aide du nom que vous avez créé précédemment.
4. Cliquez avec le bouton droit sur ce rapport, puis sélectionnez **exécuter**.
5. Dans la boîte de dialogue qui s’ouvre, sélectionnez **Exporter** , puis **enregistrer en tant que CSV**.
6. Cette version du rapport extrait les hachages de tous les appareils Windows 10 avec lesquels le gestionnaire de configuration communique. Vous devrez filtrer les résultats sur les appareils que vous envisagez d’enregistrer avec le bureau géré Microsoft.


> [!IMPORTANT]
> La requête dans le gestionnaire de configuration n’autorise pas les espaces dans les noms de colonne exportés ; C’est pourquoi les étapes ont été entrées « Numéro_de_série » et « HardwareHash ». Maintenant que vous avez le fichier CSV exporté, vous devez modifier les en-têtes du rapport pour lire le *numéro de série* et le *hachage matériel* , comme indiqué ici avant de procéder à l’inscription de l’appareil.

Vous pouvez maintenant [enregistrer des appareils à l’aide du portail Azure](#register-devices-by-using-the-azure-portal).


#### <a name="active-directory-powershell-script-method"></a>Méthode de script PowerShell Active Directory

Dans un environnement Active Directory, vous pouvez utiliser l' `Get-MMDRegistrationInfo` applet de commande PowerShell pour collecter les informations à distance à partir de périphériques dans des groupes Active Directory à l’aide de WinRM. Vous pouvez également utiliser l' `Get-AD Computer` applet de commande et obtenir des résultats filtrés pour les noms de modèle de matériel spécifiques inclus dans le catalogue. Pour ce faire, vérifiez d’abord ces conditions préalables, puis passez aux étapes suivantes :

- WinRM est activé.
- Les appareils que vous souhaitez enregistrer sont actifs sur le réseau (c’est-à-dire qu’ils ne sont pas déconnectés ou désactivés).
- Assurez-vous que vous disposez d’un paramètre d’informations d’identification de domaine qui a l’autorisation de s’exécuter à distance sur les appareils.
- Assurez-vous que le pare-feu Windows autorise l’accès à WMI. Pour ce faire, procédez comme suit :
    1. Ouvrez le panneau de configuration du **pare-feu Windows Defender** et sélectionnez **autoriser une application ou une fonctionnalité via le pare-feu Windows Defender**.
    2. Recherchez **Windows Management Instrumentation (WMI)** dans la liste, activez à la fois **privé et public**, puis cliquez sur **OK**.

1.  Ouvrez une invite PowerShell avec des droits d’administration.
2.  Exécutez l' *un* des scripts suivants :
```powershell
Install-script -name Get-MMDRegistrationInfo 
#example one – leverage Get-ADComputer to enumerate devices 
Get-ADComputer -filter * | powershell -ExecutionPolicy Unrestricted Get-MMDRegistrationInfo.ps1 -credential Domainname\<accountname>
```
```powershell 
#example two – target specific devices: 
Set-ExecutionPolicy powershell -ExecutionPolicy Unrestricted Get-MMDRegistrationInfo.ps1 -credential Domainname\<accountname> -Name Machine1,Machine2,Machine3
```
3. Accéder à tous les répertoires où se trouvent des entrées pour les appareils. Supprimez les entrées de chaque périphérique de *tous les* répertoires, y compris les services de domaine Active Directory Windows Server et Azure Active Directory. N’oubliez pas que cette suppression peut prendre quelques heures.
4. Services de gestion d’accès où il peut y avoir des entrées pour les périphériques. Supprimez les entrées de chaque périphérique de *tous les* services de gestion, y compris System Center Configuration Manager, Microsoft Intune et Windows AutoPilot. N’oubliez pas que cette suppression peut prendre quelques heures.

À présent, vous pouvez procéder à l' [inscription des appareils](#register-devices).

#### <a name="manual-powershell-script-method"></a>Méthode de script PowerShell manuel

1.  Ouvrez une invite PowerShell avec des droits d’administration.
2.  Générer`Install-Script -Name Get-MMDRegistrationInfo`
3.  Générer`powershell -ExecutionPolicy Unrestricted Get-MMDRegistrationInfo -OutputFile <path>\hardwarehash.csv`
4. [Fusionnez les données de hachage.](#merge-hash-data)

#### <a name="flash-drive-method"></a>Flash Drive, méthode

1. Sur un appareil autre que celui que vous enregistrez, insérez un lecteur USB.
2. Ouvrez une invite PowerShell avec des droits d’administration.
3. Générer`Save-Script -Name Get-MMDRegistrationInfo -Path <pathToUsb>`
4. Activez l’appareil que vous enregistrez, mais *ne démarrez pas l’installation*. Si vous démarrez accidentellement le programme d’installation, vous devrez réinitialiser ou recréer l’image de l’appareil.
5. Insérez le lecteur USB, puis appuyez sur MAJ + F10.
6. Ouvrez une invite PowerShell avec des droits d’administration, puis `cd <pathToUsb>`exécutez.
7. Générer`Set-ExecutionPolicy -ExecutionPolicy Unrestricted`
8. Générer`.\Get-MMDRegistrationInfo -OutputFile <path>\hardwarehash.csv`
9. Supprimez le lecteur USB, puis arrêtez l’appareil en exécutant`shutdown -s -t 0`
10. [Fusionnez les données de hachage.](#merge-hash-data)

>[!IMPORTANT]
>Ne mettez pas sous tension le périphérique que vous enregistrez jusqu’à ce que vous ayez terminé son inscription. 



### <a name="merge-hash-data"></a>Fusionner les données de hachage

Si vous avez collecté les données de hachage du matériel à l’aide de la méthode manuelle PowerShell ou Flash Drive, il vous faut maintenant que les données des fichiers CSV soient combinées en un seul fichier pour terminer l’inscription. Voici un exemple de script PowerShell pour faciliter cette tâche :

`Import-CSV -Path (Get-ChildItem -Filter *.csv) | ConvertTo-Csv -NoTypeInformation | % {$_.Replace('"', '')} | Out-File .\aggregatedDevices.csv`

Une fois les données hachées fusionnées dans un fichier CSV, vous pouvez maintenant [enregistrer les appareils](#register-devices).

### <a name="register-devices"></a>Inscrire des appareils

Le fichier CSV doit être dans un format particulier pour l’inscription. Si vous avez collecté les données vous-même au cours des étapes précédentes, le format du fichier doit déjà être correct ; Si vous obtenez le fichier auprès d’un fournisseur, il se peut que vous deviez ajuster le format.

>[!NOTE]
>Pour des raisons de commodité, vous pouvez télécharger un [modèle](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/managed-desktop/get-started/downloads/device-registration-sample-partner.xlsx) pour ce fichier CSV.

Votre fichier doit inclure exactement les **mêmes en-têtes de colonne** que l’exemple (fabricant, modèle, etc.), mais vos propres données pour les autres lignes. Si vous utilisez le modèle, ouvrez-le dans un outil d’édition de texte tel que le bloc-notes, et pensez à laisser toutes les données de la ligne 1 uniquement, en entrant uniquement les données dans les lignes 2 et ci-dessous. 
    
  ```
 Manufacturer,Model,Serial Number,Hardware Hash
  SpiralOrbit,ContosoABC,000000000000,dGhpc2RldmljZWlzYW5tbWRkZXZpY2U
  
  
  ```

>[!NOTE]
>Si vous oubliez de modifier l’un des exemples de données, l’inscription échouera.

#### <a name="register-devices-by-using-the-azure-portal"></a>Inscrire des appareils à l’aide du portail Azure

Dans le portail Microsoft Managed Desktop [Azure](https://aka.ms/mmdportal), sélectionnez **périphériques** dans le volet de navigation de gauche. Sélectionnez **+ inscrire les appareils**; le survol s’ouvre :

[![Entrée brusque après la sélection d’appareils de Registre](images/register-devices-flyin-sterile.png)](images/register-devices-flyin-sterile.png)


[//]: # (Malheureusement, cela n’est pas vrai. Nous pouvons supprimer cette note, mais la laisser maintenant jusqu’à ce que nous ayons la possibilité de discuter.)

<!--Registering any existing devices with Managed Desktop will completely re-image them; make sure you've backed up any important data prior to starting the registration process.-->


Procédez comme suit :

1. Dans **chargement du fichier**, indiquez le chemin d’accès au fichier CSV que vous avez créé précédemment.
2. Si vous le souhaitez, vous pouvez ajouter un **ID de commande** ou un **ID d’achat** à vos fins de suivi. Il n’y a pas de mise en forme requise pour ces valeurs.
3. Sélectionnez **inscrire les appareils**. Le système ajoute les périphériques à votre liste d’appareils sur le panneau des **appareils**, marqué comme **inscription en attente**. L’inscription prend généralement moins de 10 minutes et, lorsque le périphérique s’affiche comme **prêt pour l’utilisateur** , ce qui signifie qu’il est prêt et qu’il attend qu’un utilisateur final commence à utiliser.


Vous pouvez surveiller la progression de l’inscription de l’appareil sur la page principale **des périphériques de bureau gérés par Microsoft** . Les États possibles sont les suivants :

| État | Description |
|---------------|-------------|
| Inscription en attente | L’inscription n’est pas encore terminée. Réactivez-vous plus tard. |
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
| Erreur inattendue | Votre demande n’a pas pu être traitée automatiquement. Contactez le support technique et indiquez l’ID de la demande :<requestId> |

### <a name="check-the-image"></a>Vérifier l’image

Si votre appareil vient d’un fournisseur de partenaires de bureau géré Microsoft, l’image doit être correcte.

Si vous le souhaitez, vous pouvez également appliquer l’image par vous-même. Pour commencer, contactez le représentant Microsoft avec lequel vous travaillez et ils vous fourniront l’emplacement et les étapes à suivre pour appliquer l’image.

### <a name="deliver-the-device"></a>Remise de l’appareil

> [!IMPORTANT]
> Avant de remettre l’appareil à votre utilisateur, vérifiez que vous avez obtenu et appliqué les [licences appropriées](../get-ready/prerequisites.md) pour cet utilisateur.

Si toutes les licences sont appliquées, vous pouvez [faire en sorte que vos utilisateurs soient prêts à utiliser les appareils](get-started-devices.md), puis votre utilisateur peut démarrer l’appareil et poursuivre l’installation de Windows.









