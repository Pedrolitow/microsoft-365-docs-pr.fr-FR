---
title: Créer un package
description: Comment créer votre package
search.appverid: MET150
author: Tinacyt
ms.author: tinachen
manager: rshastri
audience: Software-Vendor
ms.topic: troubleshooting
ms.date: 02/28/2022
ms.service: virtual-desktop
ms.localizationpriority: medium
ms.collection: TestBase-M365
ms.custom: ''
ms.reviewer: Tinacyt
f1.keywords: NOCSH
ms.openlocfilehash: 277c185b633263a12687eec5a8eb9a1a34e1dbed
ms.sourcegitcommit: 23a90ed17cddf3b0db8d4084c8424f0fabd7b1de
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/17/2022
ms.locfileid: "62888112"
---
# <a name="build-a-package"></a>Créer un package
Un package est un fichier .zip contenant les scripts binaires et de test de votre application, qui est la condition préalable à l’utilisation de la base de test. Ce démarrage rapide vous guide pour créer votre premier package, avec lequel vous pouvez effectuer des tests pré-box sur votre application. 
  
*    *Un test **OOB (Out-of-Box)** effectue une installation, un lancement, une fermeture et une désinstallation de votre application. Après l’installation, la routine de fermeture de lancement est répétée 30 fois avant l’opération de désinstallation unique. Le test OOB vous fournit une télémétrie normalisée sur votre package à comparer entre Windows builds.*  
    
Si vous le souhaitez, vous pouvez télécharger notre [exemple de package](https://aka.ms/testbase-sample-package) pour référencer et commencer par. 

## <a name="create-a-folder-structure"></a>Créer une structure de dossiers 

Sur votre ordinateur local, créez une structure de dossiers comme suit :<br> 
![Structure de dossiers utilisée pour créer le package](Media/buildpackage1.png)

Ces dossiers sont utilisés :
* **App\bin :** enregistrez les binaires d’application et de dépendance.<br> 
* **App\scripts** : enregistrez des scripts pour installer, lancer, fermer et désinstaller votre application.<br> 
* **App\logs**: scripts should output logs to this folder, then you can download and analyze logs after test is finished.<br> 

## <a name="copy-binary-files"></a>Copier des fichiers binaires
Copiez vos fichiers d’installation d’application **dans App\bin**. Si votre application a des dépendances, elles doivent être installées en premier. Copiez également les fichiers d’installation des dépendances **dans App\bin**.<br> 
![Emplacement des fichiers d’application dans le dossier](Media/buildpackage2.png)

## <a name="add-powershell-scripts"></a>Ajouter des scripts PowerShell
Pour effectuer un test OOB, vous devez ajouter des scripts PowerShell pour installer, lancer, fermer et désinstaller votre application.
> [!NOTE]  
> *Dans le test OOB, l’installation, le lancement et la fermeture de scripts sont requis, tandis que le script de désinstallation est facultatif*.
    
Le script doit être ajouté au dossier comme suit :  
![Emplacement des fichiers de scripts PowerShell dans le dossier](Media/buildpackage3.png)

Un script inclut généralement les comportements suivants :<br> 
-   **Exécutez les commandes pour installer/lancer/fermer/désinstaller l’application**. Par exemple, si votre application est un fichier MSI, [exécutez msiexec](/windows-server/administration/windows-commands/msiexec) pour l’installer. <br> 
-   **Vérifiez le résultat de l’opération d’installation/lancement/fermeture/désinstallation**, renvoyer le code de sortie zéro si le résultat est attendu. La base de test marque un script exécuté comme un échec s’il renvoie un code de sortie non nul.<br> 
-   **Enregistrez suffisamment de journaux**, enregistrez les journaux appropriés pour une utilisation ultérieure.<br> 

Reportez-vous aux exemples suivants. Vous pouvez simplement les copier dans vos fichiers et apporter des modifications en conséquence. <br>

**Exemple de script d’installation (App\scripts\install\job.ps1)**
```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"


        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Installing TestBaseM365 Digital Clock")
        push-location "..\..\bin"
        if ([Environment]::Is64BitProcess) {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        else {
            $installer_name = "TestBaseM365DigitalClock.msi"
        }
        $arguments = "/i "+$installer_name+" /quiet /L*v "+"$log_dir"+"\atp-client-installation.log"

        $installer = Start-Process msiexec.exe $arguments -wait -passthru
        pop-location

        if ($installer.exitcode -eq 0) {
            log("Installation succesful as $($installer.exitcode)")
        }
        else {
            log("Error: Installation failed as $($installer.exitcode)")
            $exit_code = $installer.exitcode
        }

        log("Installation script finished as $exit_code")
        pop-location
        exit $exit_code
```

**Exemple de script de lancement (App\scripts\launch\job.ps1)**
```powershell
        push-location $PSScriptRoot
        $exit_code = 0
        $script_name = $myinvocation.mycommand.name
        $log_dir = "$PSScriptRoot\..\..\logs"
        $log_file = "$log_dir\$script_name.log"

        if(-not (test-path -path $log_dir )) {
            new-item -itemtype directory -path $log_dir
        }

        Function log {
           Param ([string]$log_string)
           write-host $log_string
           add-content $log_file -value $log_string
        }

        log("Launch TestBaseM365 Digital Clock")

        $PROCESS_NAME = "DigitalClock"
        $exePath = "C:\Program Files\Test Base M365\DigitalClock\DigitalClock.exe"

        Start-Process -FilePath $exePath

         if (Get-Process -Name $PROCESS_NAME) {
                log("Launch successfully $PROCESS_NAME...") 
                $exit_code = 0
         }
         else {
            log("Not launched $PROCESS_NAME...") 
            $exit_code = 1
         }

        log("Launch script finished as $exit_code")
        pop-location
        exit $exit_code 
```

## <a name="compress-to-zip-file"></a>Compresser au fichier zip
Une fois les scripts et les fichiers binaires préparés, vous devez compresser le dossier dans un fichier zip. Cliquez avec le bouton droit sur le dossier Application, **sélectionnez Compresser au fichier ZIP**.<br>
![Compresser au fichier zip](Media/buildpackage4.png)


## <a name="verify-your-package-locally-optional"></a>Vérifier votre package localement (facultatif)
Après avoir construit le package zip, vous pouvez le télécharger sur votre compte de base de test. <br>
Toutefois, il est préférable d’exécuter le test localement pour vous assurer que les scripts fonctionnent correctement avant le téléchargement. Un test local permet d’identifier rapidement les problèmes et d’accélérer votre processus de téléchargement. Pour vérifier localement, suivez les étapes ci-dessous :<br>
1.  Préparer une machine virtuelle (machine virtuelle)<br>
    Nous vous recommandons d’utiliser une machine virtuelle pour ce test local, car un environnement Windows propre est actuellement nécessaire pour chaque test. Il est facile de créer une machine virtuelle Windows sur Azure (démarrage rapide : machine virtuelle [Windows](/azure/virtual-machines/windows/quick-create-portal)), vous pouvez sélectionner une version Windows appropriée (image) pour votre test, par exemple, *Windows 10 Professionnel, version 21H2.*<br>

2.  Copier votre package sur la VM<br>
    Il existe de nombreuses façons de copier votre fichier de package sur la VM. Si vous utilisez une VM Azure, vous pouvez choisir de :
     -  Copiez le fichier directement dans votre connexion Bureau à distance. <br>
     -  Utiliser le partage de fichiers Azure ([démarrage rapide : créer et gérer un fichier Azure](/azure/storage/files/storage-files-quick-create-use-windows))
    
    Vous pouvez créer un dossier spécifique pour ce test et copier le fichier de package sous ce dossier. par exemple, *C:\TestBase*.<br>
3.  Tester le package<br>
    Ouvrez Windows PowerShell, basculez vers le répertoire contenant le package, par exemple cd C:\TestBase, et commencez à exécuter vos tests sur le package :<br>
    a.  Extrayz le fichier de package.
     -  *Expand-Archive -LiteralPath C:\TestBase\App.zip -DestinationPath C:\TestBase*<br>
    
    b.  Exécutez le script d’installation.  
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    c.  Redémarrez la VM si nécessaire.<br>
    
    d.  Exécutez le script de lancement.
     -  *C:\TestBase\App\scripts\install\job.ps1*<br>
    
    e.  Exécutez un script de fermeture.
     -  *C:\TestBase\App\scripts\close\job.ps1*<br>
    
    f.  Exécutez un script de désinstallation (si vous en avez un).
     -  *C:\TestBase\App\scripts\uninstall\job.ps1*<br>
    
    Après chaque étape, vous pouvez vérifier s’il existe des problèmes dans votre script. Si tous les scripts s’exécutent comme prévu, votre package est prêt à être téléchargé vers votre compte de base de test.


## <a name="next-steps"></a>Étapes suivantes
[Télécharger package](uploadApplication.md)
 
 
