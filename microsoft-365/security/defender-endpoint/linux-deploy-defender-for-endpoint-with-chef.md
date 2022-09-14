---
title: Guide pratique pour déployer Defender pour point de terminaison sur Linux avec Chef
description: Découvrez comment déployer Defender pour point de terminaison sur Linux avec Chef
keywords: microsoft, defender, atp, linux, scans, antivirus, microsoft defender pour point de terminaison (linux)
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: lovina-saldanha
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 0137202f08f5b9545d744c5fb81a7c4068a1f9c4
ms.sourcegitcommit: 9b133379196da2b3a4bb311b07ff274f43780f68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67687150"
---
# <a name="deploy-defender-for-endpoint-on-linux-with-chef"></a>Microsoft Defender pour point de terminaison Linux

**S’applique à :**

- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Avant de commencer : installez le décompression s’il n’est pas déjà installé.

Les composants Chef sont déjà installés et un référentiel Chef existe (chef générer un dépôt \<reponame\>) pour stocker le livre de recettes qui sera utilisé pour le déploiement sur Defender pour point de terminaison sur les serveurs Linux gérés par Chef.

Vous pouvez créer un livre de recettes dans votre référentiel existant en exécutant la commande suivante à partir du dossier des livres de recettes qui se trouve dans votre référentiel chef :

```bash
chef generate cookbook mdatp
```

Cette commande crée une structure de dossiers pour le nouveau livre de recettes appelé mdatp. Vous pouvez également utiliser un livre de recettes existant si vous en avez déjà un que vous souhaitez utiliser pour ajouter le déploiement MDE.
Une fois le livre de recettes créé, créez un dossier de fichiers dans le dossier du livre de recettes qui vient d’être créé :

```bash
mkdir mdatp/files
```

Transférez le fichier zip d’intégration du serveur Linux qui peut être téléchargé à partir du portail Microsoft 365 Defender vers ce nouveau dossier de fichiers.

Sur la station de travail Chef, accédez au dossier mdatp/recipes. Ce dossier est créé lors de la génération du livre de recettes. Utilisez votre éditeur de texte préféré (par exemple, vi ou nano) pour ajouter les instructions suivantes à la fin du fichier default.rb :

- include_recipe '::onboard_mdatp'
- include_recipe ':install_mdatp'

Ensuite, enregistrez et fermez le fichier default.rb.

Créez ensuite un fichier de recettes nommé install_mdatp.rb dans le dossier recettes et ajoutez ce texte au fichier :

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
   uri                "https://packages.microsoft.com/config/ubuntu/20.04/prod"
 end
 apt_package "mdatp"
when 'rhel'
 yum_repository 'microsoft-prod' do
   baseurl            "https://packages.microsoft.com/config/rhel/7/prod/"
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

Vous devez modifier le numéro de version, la distribution et le nom du dépôt pour qu’ils correspondent à la version sur laquelle vous effectuez le déploiement et au canal que vous souhaitez déployer.
Ensuite, vous devez créer un fichier onboard_mdatp.rb dans le dossier mdatp/recipies. Ajoutez le texte suivant à ce fichier :

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

Veillez à mettre à jour le nom du chemin d’accès à l’emplacement du fichier d’intégration.
Pour tester son déploiement sur la station de travail Chef, exécutez ``sudo chef-client -z -o mdatp``simplement .
Après votre déploiement, vous devez envisager de créer et de déployer un fichier de configuration sur les serveurs en fonction [des préférences définies pour Microsoft Defender pour point de terminaison sur Linux](/microsoft-365/security/defender-endpoint/linux-preferences).
Une fois que vous avez créé et testé votre fichier de configuration, vous pouvez le placer dans le dossier cookbook/mdatp/files où vous avez également placé le package d’intégration. Vous pouvez ensuite créer un fichier settings_mdatp.rb dans le dossier mdatp/recipies et ajouter ce texte :

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

Pour inclure cette étape dans la recette, ajoutez simplement include_recipe « : settings_mdatp » à votre fichier default.rb dans le dossier de la recette.
Vous pouvez également utiliser crontab pour planifier des mises à jour automatiques [Planifier une mise à jour du Microsoft Defender pour point de terminaison (Linux).](linux-update-MDE-Linux.md)

Désinstaller le livre de recettes MDATP :

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
