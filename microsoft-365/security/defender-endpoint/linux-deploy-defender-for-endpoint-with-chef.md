---
title: Comment déployer Defender pour endpoint sur Linux avec Chef
description: Découvrez comment déployer Defender pour Endpoint sur Linux avec Chef
keywords: microsoft, defender, atp, linux, analyses, antivirus, microsoft defender pour point de terminaison (linux)
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: v-lsaldanha
author: lovina-saldanha
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.technology: mde
ms.openlocfilehash: 362222e4737b1a8dd6b8a0a284bf3bfb1903c288
ms.sourcegitcommit: 22505ce322f68a2d0ce70d71caf3b0a657fa838a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/16/2021
ms.locfileid: "51861445"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Déployer Defender pour endpoint sur Linux avec Chef

Avant de commencer :

- Installez unzip s'il n'est pas déjà installé. Les composants Chef sont déjà installés et un référentiel Chef existe (le chef génère un référentiel ) pour stocker le guide de référence qui sera utilisé pour déployer defender pour point de terminaison sur les serveurs Linux gérés par <reponame> Chef.

Vous pouvez créer un nouveau classeur dans votre référentiel existant en exécutant la commande suivante à partir du dossier des classeurs qui se trouve dans votre référentiel de chef :</br>
`chef generate cookbook mdatp`

Cette commande crée une structure de dossiers pour le nouveau classeur appelé mdatp.  Vous pouvez également utiliser un livre de recettes existant si vous en avez déjà un que vous souhaitez utiliser pour ajouter le déploiement MDE.
Une fois le classeur créé, créez un dossier de fichiers à l'intérieur du dossier de classeur qui vient d'être créé :

`mkdir mdatp/files`

Transférez le fichier zip d'intégration Linux Server qui peut être téléchargé à partir du portail centre de sécurité Microsoft Defender vers ce nouveau dossier de fichiers.

Sur la station de travail Chef, accédez au dossier mdatp/recipes. Ce dossier est créé lors de la création du classeur. Utilisez votre éditeur de texte préféré (comme vi ou nano) pour ajouter les instructions suivantes à la fin du fichier default.rb :
-   include_recipe '::onboard_mdatp'
- include_recipe '::install_mdatp'

Enregistrez et fermez ensuite le fichier default.rb.
Créez ensuite un fichier de recette nommé install_mdatp.rb dans le dossier recettes et ajoutez ce texte au fichier :

```powershell

#Add Microsoft Defender   
Repo  
case node['platform_family']
when 'debian'
 apt_repository 'MDAPRepo' do
   arch               'amd64'
   cache_rebuild      true
   cookbook           false
   deb_src            false
   key                'BC528686B50D79E339D3721CEB3E94ADBE1229CF'
   keyserver          "keyserver.ubuntu.com"
   distribution       'focal'
   repo_name          'microsoft-prod'
   components         ['main']
   trusted            true
   uri                "https://packages.microsoft.com/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/rhel/7/prod/"
   description        "Microsoft Defender for Endpoint"
   enabled            true
   gpgcheck           true
   gpgkey             "https://packages.microsoft.com/keys/microsoft.asc"
 end
 if node['platform_version'] <= 8 then
    yum_package "mdatp"
 else
    dnf_package "mdatp"
 end
end
```

Vous devez modifier le numéro de version, la distribution et le nom du repo pour qu'il corresponde à la version que vous déployez et au canal que vous souhaitez déployer.
Ensuite, vous devez créer un onboard_mdatp.rb dans le dossier mdatp/recipies.  Ajoutez le texte suivant à ce fichier :

```powershell

#Create MDATP Directory
mdatp = "/etc/opt/microsoft/mdatp"
zip_path = "/path/to/chef-repo/cookbooks/mdatp/files/WindowsDefenderATPOnboardingPackage.zip"

directory "#{mdatp}" do
  owner 'root'
  group 'root'
  mode 0755
  recursive true
end

#Extract WindowsDefenderATPOnbaordingPackage.zip into /etc/opt/microsoft/mdatp

bash 'Extract Onbaording Json MDATP' do
  code <<-EOS
  unzip #{zip_path} -d #{mdatp}
  EOS
  not_if { ::File.exist?('/etc/opt/microsoft/mdatp/mdatp_onboard.json') }
end
```

Veillez à mettre à jour le nom du chemin d'accès à l'emplacement du fichier d'intégration.
Pour tester son déploiement sur la station de travail Chef, exécutez simplement ``sudo chef-client -z -o mdatp`` .
Après votre déploiement, vous devez envisager de créer et de déployer un fichier de configuration sur les serveurs en fonction des préférences définies pour Microsoft Defender ATP pour Linux - Sécurité  [Windows | Microsoft Docs](/windows/security/threat-protection/microsoft-defender-atp/linux-preferences).  
Une fois que vous avez créé et testé votre fichier de configuration, vous pouvez le placer dans le dossier de guide/mdatp/fichiers où vous avez également placé le package d'intégration.  Vous pouvez ensuite créer un fichier settings_mdatp.rb dans le dossier mdatp/recipies et ajouter ce texte :

```powershell
#Copy the configuration file
cookbook_file '/etc/opt/microsoft/mdatp/managed/mdatp_managed.json' do
  source 'mdatp_managed.json'
  owner 'root'
  group 'root'
  mode '0755'
  action :create
end
```

Pour inclure cette étape dans la recette, ajoutez simplement include_recipe « :: settings_mdatp » à votre fichier default.rb dans le dossier de la recette.
Vous pouvez également utiliser crontab pour planifier des mises à jour automatiques Planifier une mise à jour de [Microsoft Defender pour Endpoint (Linux).](linux-update-MDE-Linux.md)

Désinstallez le manuel MDATP :

```powershell
#Uninstall the Defender package
case node['platform_family']
when 'debian'
 apt_package "mdatp" do
   action :remove
 end
when 'rhel'
 if node['platform_version'] <= 8 
then
    yum_package "mdatp" do
      action :remove
    end
 else
    dnf_package "mdatp" do
      action :remove
    end
 end
end
```

