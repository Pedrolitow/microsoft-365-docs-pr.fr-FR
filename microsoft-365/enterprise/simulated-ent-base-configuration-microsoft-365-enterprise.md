---
title: Configuration de base d’une entreprise simulée pour Microsoft 365
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Utilisez ce Guide de Laboratoire Test afin de créer une simulation d’environnement de test dédiée à Microsoft 365 Entreprise.
ms.openlocfilehash: 98eb336a0f63f47b4b79de44c46fcd81f1d9c9f6
ms.sourcegitcommit: 2bdd7b535a7d2a4896df130b7047f8c85f4d47b4
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2019
ms.locfileid: "38711878"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Configuration de base d’une entreprise simulée

*Ce Guide de Laboratoire Test peut être utilisé pour les environnements de test Microsoft 365 Enterprise et Office 365 Enterprise.*

Vous trouverez dans cet article des instructions détaillées pour créer un environnement simplifié pour Microsoft 365 Entreprise qui comprend :

- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet simplifié d’une organisation connecté à Internet, composé de trois machines virtuelles sur un réseau virtuel Azure (DC1, APP1 et CLIENT1).
 
![Configuration de base d’une entreprise simulée](media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Vous pouvez utiliser l’environnement obtenu pour tester les fonctions et le bon fonctionnement de[Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise), par vous-même ou en suivant les conseils des [guides de laboratoire de test](m365-enterprise-test-lab-guides.md).

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.

## <a name="phase-1-create-a-simulated-intranet"></a>Phase 1: Créer un intranet simulé

Dans cette phase, vous allez créer un intranet simulé dans les services d’infrastructure Azure comprenant un contrôleur de domaine Windows Server Active Directory, un serveur d’application et un ordinateur client. 

Vous utiliserez ces ordinateurs dans des[Guides de laboratoire de Test Microsoft 365 Enterprise](m365-enterprise-test-lab-guides.md)supplémentaires afin de configurer et montrer l’identité hybride et les autres fonctionnalités.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Méthode 1: Créer votre intranet simulé avec un Modèle de Gestion de Ressources Azure 

En utilisant cette méthode, vous utilisez un modèle de Gestion des Ressources Azure(GRA) pour assembler intranet simulé. PROCESSEUR modèles contiennent toutes les instructions pour créer l’infrastructure réseau Azure, machines virtuelles et leur configuration.

Avant de déployer le modèle, parcourez le[modèle de la page Lisez-moi](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) et obtenez les informations suivantes prêtes :

- Le nom de domaine DNS public de votre environnement de test (testlab.\< votre domaine public >). Vous devez entrer ce nom dans le**champ Nom de Domaine** de la page**déploiement Personnalisé**.
- Un préfixe d’étiquette DNS pour les URL d’adresses IP publiques de vos machines virtuelles. Vous devez entrer cette étiquette dans le**préfixe d’étiquette Dns** champ de la page**déploiement Personnalisé**.

Après avoir lu via les instructions, cliquez sur **déployer vers Azure** sur la [page modèle LISEZMOI](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) pour commencer.

>[!Note]
>L’Intranet simulé créé par le modèle GRA nécessite un abonnement payant à Azure.
>

Voici votre configuration une fois le modèle terminé.

![L’intranet simulé dans les services d’infrastructure Azure.](media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Méthode 2 : Créer votre intranet simulé avec Azure PowerShell

En utilisant cette méthode, vous utilisez Windows PowerShell et le module Azure PowerShell afin de créer l’infrastructure de réseau, les machines virtuelles et leur configuration.

Utilisez cette méthode si vous souhaitez acquérir de l’expérience en créant des éléments d’infrastructure Azure, une étape après l’autre, avec PowerShell. Vous pouvez alors personnaliser les blocs de commande PowerShell pour votre propre déploiement d’autres machines virtuelles dans Azure.

#### <a name="step-1-create-dc1"></a>Phase 1: création de DC1

Durant cette phase, nous allons créer un réseau virtuel Azure et ajouter la machine virtuelle DC1 qui est un contrôleur de domaine pour un domaine Windows Server Active Directory (AD).

Tout d’abord, démarrez une invite de commandes Windows PowerShell sur votre ordinateur local.
  
> [!NOTE]
> Les ensembles de commandes suivants utilisent la dernière version d’Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). 
  
Connectez-vous à votre compte Azure avec la commande suivante.
  
```powershell
Connect-AzAccount
```

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Définissez votre abonnement Azure. Remplacez tout le texte entre guillemets, y compris les caractères < et >, avec le nom correct.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Ensuite, créez un nouveau groupe de ressources pour le laboratoire de test de votre entreprise simulée. Pour choisir un nom de groupe de ressources unique, utilisez cette commande pour répertorier les groupes de ressources existants.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Créez votre nouveau groupe de ressources avec ces commandes. Remplacez tout le texte entre guillemets, y compris les caractères < et >, par les noms corrects.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ensuite, créez le réseau virtuel TestLab qui hébergera le sous-réseau du réseau de l’environnement de l’entreprise simulée et protégez-le avec un groupe de sécurité de réseau. Indiquez le nom de votre groupe de ressources et exécutez les commandes suivantes à l’invite de commandes PowerShell sur votre ordinateur local.
  
```powershell
$rgName="<name of your new resource group>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Dans cette étape, nous créons la machine virtuelle DC1 et la configurons en tant que contrôleur de domaine pour votre domaine public**testlab.**\< AD DS (Active Directory Domain Services) et un serveur DNS pour les machines virtuelles du réseau virtuel TestLab. Par exemple, si votre nom de domaine public est ** <span>contoso</span>.com**, la machine virtuelle DC1 sera un contrôleur de domaine pour le **<span>testlab</span>. contoso.com** domaine.
  
Pour créer une machine virtuelle Azure pour DC1, indiquez d’abord le nom de votre groupe de ressources, puis exécutez ces commandes à l’invite de commandes PowerShell sur votre ordinateur local.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 10.0.0.4
$vm=New-AzVMConfig -VMName DC1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC1-OS" -DiskSizeInGB 128 -CreateOption FromImage
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC1-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC1-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Vous serez invité à indiquer un nom d’utilisateur et un mot de passe pour le compte d’administrateur local sur DC1. Utilisez un mot de passe et enregistrez le nom et le mot de passe dans un endroit sûr.
  
Ensuite, connectez-vous à la machine virtuelle DC1.
  
1. Dans le [Portail Azure](https://portal.azure.com), cliquez sur **Groupes de Ressources >** [nom de votre nouveau groupe de ressources] **> DC1 > Se connecter**.
    
2. Dans le volet ouvert, cliquez sur **Télécharger le fichier RDP**. Ouvrez le fichier DC1.rdp qui est téléchargé, puis cliquez sur **Se connecter**.
    
3. Spécifiez le nom du compte Administrateur local DC1 :
    
   - Pour Windows 7 :
    
     Dans la boîte de dialogue **Sécurité Windows**, cliquez sur **Utiliser un autre compte**. Dans **Nom d’utilisateur**, tapez **DC1\\**[nom du compte Administrateur local].
    
   - Pour Windows 8 ou Windows 10 :
    
     Dans la boîte de dialogue **Sécurité Windows**, cliquez sur **Autres choix**, puis cliquez sur **Utiliser un autre compte**. Dans **Nom d’utilisateur**, tapez **DC1\\**[nom de compte Administrateur local].
    
4. Dans **Mot de passe**, tapez le mot de passe du compte Administrateur local, puis cliquez sur **OK**.
    
5. Quand vous y êtes invité, cliquez sur **Oui**.
    
Ensuite, ajoutez un disque de données supplémentaire en tant que nouveau volume avec la lettre de lecteur F:, à l’aide de la commande suivante, dans l’invite de commande Windows PowerShell au niveau administrateur sur DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Maintenant, configurez DC1 comme un contrôleur de domaine et un serveur DNS pour le domaine **testlab.**\<votre domaine public>. Indiquez le nom de votre domaine public, supprimez les caractères \< et >, puis exécutez ces commandes à l’invite de commandes Windows PowerShell de niveau administrateur sur DC1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
Vous devez spécifier un mot de passe administrateur en mode sans échec. Conservez ce mot de passe dans un endroit sûr.
  
Notez que l’exécution de ces commandes peut prendre quelques minutes.
  
Après le redémarrage de DC1, reconnectez-vous à la machine virtuelle DC1.
  
1. Dans le [Portail Azure](https://portal.azure.com), cliquez sur **Groupes de Ressources >** [nom de votre groupe de ressources] **> DC1 > Se connecter**.
    
2. Exécutez le fichier DC1.rdp qui est téléchargé, puis cliquez sur **Se connecter**.
    
3. Dans **Sécurité Windows**, cliquez sur **Utiliser un autre compte**. Dans **Nom d’utilisateur**, tapez **TESTLAB\\**[nom du compte Administrateur local].
    
4. Dans **Mot de passe**, tapez le mot de passe du compte Administrateur local, puis cliquez sur **OK**.
    
5. Quand vous y êtes invité, cliquez sur **Oui**.
    
Ensuite, dans Active Directory, créez un compte d’utilisateur qui sera utilisé pour la connexion aux ordinateurs membres du domaine TESTLAB. Exécutez cette commande à l’invite de commandes Windows PowerShell de niveau administrateur.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Notez que cette commande vous invite à renseigner le mot de passe du compte Utilisateur1 (User1). Étant donné que ce compte est utilisé pour les connexions de bureau à distance pour tous les ordinateurs membres du domaine TESTLAB, choisissez un mot de passe fort. Enregistrez le mot de passe du compte Utilisateur1 et stockez-le dans un endroit sûr.
  
Maintenant, configurez le nouveau compte Utilisateur1 comme un administrateur de schéma, d’entreprise et de domaine. Exécutez cette commande à l’invite de commandes Windows PowerShell de niveau administrateur.
  
```powershell
$yourDomain="<your public domain>"
$domainName = "testlab."+$yourDomain
$userName="user1@" + $domainName
$userSID=(New-Object System.Security.Principal.NTAccount($userName)).Translate([System.Security.Principal.SecurityIdentifier]).Value
$groupNames=@("Domain Admins","Enterprise Admins","Schema Admins")
ForEach ($name in $groupNames) {Add-ADPrincipalGroupMembership -Identity $userSID -MemberOf (Get-ADGroup -Identity $name).SID.Value}
```

Fermez la session Bureau à distance avec DC1 et reconnectez-vous à l’aide du compte TESTLAB\\Utilisateur1.
  
Ensuite, pour autoriser le trafic pour l’outil Ping, exécutez cette commande à l’invite de commandes Windows PowerShell de niveau administrateur.
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
```

Il s’agit de votre configuration actuelle.
  
![Phase 1 de la configuration de base de l’entreprise simulée](media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
#### <a name="step-2-configure-app1"></a>Phase 2:Configurer APP1

Durant cette phase, vous allez créer et configurer APP1, qui est un serveur d’applications qui fournit initial des services web et de partage de fichiers.

Pour créer une machine virtuelle Azure pour APP1, renseignez d’abord le nom de votre groupe de ressources, puis exécutez ces commandes à l’invite de commandes sur votre ordinateur local.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name APP1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name APP1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName APP1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for APP1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName APP1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "APP1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ensuite, connectez-vous à la machine virtuelle APP1 en utilisant le nom du compte Administrateur local APP1 et le mot de passe, et ouvrez une invite de commande Windows PowerShell.
  
Pour vérifier la résolution du nom et la communication réseau entre APP1 et DC1, exécutez la commande **ping dc1.testlab.**\<votre nom de domaine public> et vérifiez que quatre réponses apparaissent.
  
Maintenant, associez la machine virtuelle APP1 au domaine TESTLAB avec ces commandes à l’invite Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab" + $yourDomain)
Restart-Computer
```

Les informations d’identification du compte de domaine TESTLAB\\Utilisateur1 doivent être fournies après l’exécution de la commande **Add-Computer**.
  
Après le redémarrage d’APP1, connectez-vous en utilisant le compte TESTLAB\\Utilisateur1 et ouvrez une invite de commandes Windows PowerShell de niveau administrateur.
  
Transformez APP1 en serveur web en exécutant cette commande à l’invite de commandes Windows PowerShell de niveau supérieur sur APP1.
  
```powershell
Install-WindowsFeature Web-WebServer -IncludeManagementTools
```

Ensuite, créez un dossier partagé et un fichier de texte dans le dossier sur APP1 avec ces commandes PowerShell.
  
```powershell
New-Item -path c:\files -type directory
Write-Output "This is a shared file." | out-file c:\files\example.txt
New-SmbShare -name files -path c:\files -changeaccess TESTLAB\User1
```

Il s’agit de votre configuration actuelle.
  
![Phase 2 de la configuration de base de l’entreprise simulée](media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>Phase 3:Configurer CLIENT1

Durant cette phase, vous allez créer et configurer CLIENT1, qui se comporte comme un ordinateur portable, une tablette ou un ordinateur de bureau classique sur l’intranet.

> [!NOTE]  
> Le jeu de commandes suivant crée CLIENT1 en exécutant Windows Server 2016 Datacenter, pour tous les types d’abonnements Azure. Si vous avez un abonnement Azure basé sur Visual Studio, vous pouvez créer CLIENT1 en exécutant Windows 10, avec le [portail Azure](https://portal.azure.com). 
  
Pour créer une machine virtuelle Azure pour CLIENT1, renseignez d’abord le nom de votre groupe de ressources, puis exécutez ces commandes à l’invite de commandes sur votre ordinateur local.
  
```powershell
$rgName="<resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name TestLab -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name CLIENT1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name CLIENT1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName CLIENT1 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for CLIENT1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName CLIENT1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "CLIENT1-OS" -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ensuite, connectez-vous à la machine virtuelle CLIENT1 en utilisant le nom du compte Administrateur local CLIENT1 et le mot de passe, et ouvrez une invite de commande Windows PowerShell de niveau administrateur.
  
Pour vérifier la résolution du nom et la communication réseau entre CLIENT1 et DC1, exécutez la commande **ping dc1.testlab.**\<votre nom de domaine public> à l’invite de commandes Windows PowerShell et vérifiez que quatre réponses apparaissent.
  
Maintenant, associez la machine virtuelle CLIENT1 au domaine TESTLAB avec ces commandes à l’invite Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab" + $yourDomain)
Restart-Computer
```

Les informations d’identification de votre compte de domaine TESTLAB\\Utilisateur1 doivent être fournies après l’exécution de la commande **Add-Computer**.
  
Après le redémarrage de CLIENT1, connectez-vous en utilisant le mot de passe et le nom du compte TESTLAB\\Utilisateur1 et ouvrez une invite de commandes Windows PowerShell de niveau administrateur.
  
Ensuite, vérifiez que vous pouvez accéder aux ressources web et de partage de fichiers sur APP1 de CLIENT1.
  
1. Dans le Gestionnaire de Serveur, dans le volet de l’arborescence, cliquez sur **Serveur Local**.
    
2. Dans **Propriétés pour CLIENT1**, cliquez sur **Activer** à côté de **Configuration de sécurité renforcée d’Internet Explorer**.
    
3. Dans **Configuration de sécurité renforcée d’Internet Explorer**, cliquez sur **Désactiver** pour **Administrateurs** et **Utilisateurs**, puis cliquez sur **OK**.
    
4. Sur l’écran d’accueil, cliquez sur **Internet Explorer**, puis sur **OK**.
    
5. Dans la barre d’adresses, tapez **http<span>://</span>app1.testab.**\<votre nom de domaine public>**/**, puis appuyez sur ENTRÉE. La page web Internet Information Services par défaut pour APP1 s’affiche.
    
6. Dans la barre des tâches du bureau, cliquez sur l’icône de l’Explorateur de fichiers.
    
7. Dans la barre d’adresses, tapez **\\\\app1\\Files**, puis appuyez sur ENTRÉE. Une fenêtre de dossiers avec le contenu du dossier partagé Fichiers apparaît.
    
8. Dans la fenêtre du dossier partagé **Fichiers**, double-cliquez sur le fichier **Exemple.txt**. Le contenu du fichier Exemple.txt s’affiche.
    
9. Fermez les fenêtres de dossiers partagés **Exemple.txt - Bloc-notes** et **Fichiers**.
    
Il s’agit de votre configuration actuelle.
  
![Phase 3 de la configuration de base de l’entreprise simulée](media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)


## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>Phase 2 : Création de votre abonnement Microsoft 365 E5

Durant cette phase, vous allez créer un nouvel abonnement Microsoft 365 E5 qui utilise un nouveau client Azure AD commun, différent de votre abonnement de production. Vous pouvez procéder de deux façons :

- Utiliser un abonnement d’évaluation de Microsoft 365 E5. 

  L’abonnement à la version d’évaluation Microsoft 365 E5 est valable 30 jours et peut être porté facilement à 60 jours. Quand l’abonnement à la version d’évaluation expire, soit vous le convertissez en abonnement payant, soit vous créez un nouvel abonnement à la version d’évaluation. Si vous choisissez cette dernière option, vous ne pourrez pas conserver votre configuration et les scénarios complexes qu’elle peut contenir.  

- Utiliser un abonnement de production de Microsoft 365 E5 distinct avec un nombre réduit de licences.

  Cette solution a un coût supplémentaire, mais elle vous permet de bénéficier d’un environnement de test opérationnel pour essayer des fonctionnalités, des configurations et des scénarios sans contrainte de temps. Vous pouvez utiliser le même environnement de test sur le long terme pour valider la faisabilité des concepts, réaliser des démonstrations auprès de vos pairs et de votre direction, et développer et tester des applications. Nous vous recommandons d’utiliser cette méthode.

Pour démarrer votre abonnement d’évaluation Microsoft 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.
  
1. Nous vous recommandons d’utiliser une variante du nom d’entreprise Contoso pour le nom de votre entreprise. Il s’agit d’une entreprise fictive utilisée dans le contenu d’exemple de Microsoft. Toutefois, cette étape n’est pas obligatoire. Indiquer le nom fictif de votre entreprise ici : ![](./media/Common-Images/TableLine.png)
    
2. Pour ouvrir un nouveau compte Microsoft, accédez à [https://outlook.com](https://outlook.com) et créez un compte avec un nouveau compte de messagerie et une nouvelle adresse. Vous utiliserez ce compte pour vous inscrire à Office 365.
    
  - Indiquer le prénom et le nom de famille utilisés pour votre nouveau compte ici : ![](./media/Common-Images/TableLine.png)
    
  - Indiquer l’adresse du nouveau compte de messagerie ici : ![](./media/Common-Images/TableLine.png)@outlook.com
    
### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Inscription à un abonnement d’évaluation Office 365 E5

Nous allons commencer avec un abonnement d’évaluation Office 365 E5, puis ajouter l’abonnement Microsoft 365 E5 à celui-ci.

1. Pour l’environnement de développement/test Office 365 d’entreprise simulé, connectez-vous à CLIENT1 avec le compte CORP\Utilisateur1 à partir du portail Azure.  Dans l’écran d’accueil, exécutez Microsoft Edge et accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).
    
2. Sur la page **Bienvenue, nous allons faire connaissance**, indiquez les informations suivantes :
    
  - votre emplacement physique ;
    
  - le prénom et le nom utilisés pour votre nouveau compte Microsoft ;
    
  - votre nouvelle adresse de compte de messagerie ;
    
  - un numéro de téléphone professionnel ;
    
  - le nom de votre entreprise fictive ;
    
  - la taille de votre entreprise (250 à 999 personnes).
    
3. Cliquez sur **Encore une dernière étape**.
    
4. Sur la page **Créer votre identifiant utilisateur**, entrez un nom d’utilisateur dérivé de votre nouvelle adresse de messagerie, le nom de votre entreprise fictive après le signe @ (supprimez tous les espaces dans le nom), puis un mot de passe (deux fois) pour ce nouveau compte Office 365. 
    
    Enregistrez le mot de passe saisi dans un emplacement sécurisé.
    
    Enregistrez le nom de votre entreprise fictive, ou **nom de l’organisation**, ici : ![](./media/Common-Images/TableLine.png)
    
5. Cliquez sur **Créer mon compte**.
    
6. Sur la page **Prouvez que vous n’êtes pas un robot.**, tapez le numéro de votre téléphone compatible avec du texte, puis cliquez sur **M’envoyer un SMS**.
    
7. Saisissez le code de vérification qui vous été envoyé par message, puis cliquez sur **Suivant**.
    
8. Enregistrez l’URL de la page de connexion ici (sélectionnez-la et copiez-la) : ![](./media/Common-Images/TableLine.png)
    
9. Enregistrez l’identifiant utilisateur ici (sélectionnez-le et copiez-le) : ![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Cette valeur correspond au **nom de l’administrateur général Office 365**.
    
10. Cliquez sur le lien **Nous sommes prêts** lorsqu’il s’affiche.
    
11. Sur la page suivante, attendez qu’Office 365 termine la configuration et que tous les titres soient visibles.
    
Vous devriez voir la page principale du portail Office 365 à partir de laquelle vous pouvez accéder aux services Office et au Centre d’administration Microsoft 365.
  
Vous avez créé un abonnement d’évaluation d’Office 365 pour que votre environnement de développement/test ait un client Azure AD distinct de tout abonnement payant que vous utilisez actuellement. Cette séparation signifie que vous pouvez ajouter et supprimer des utilisateurs et groupes dans le client test sans incidence sur vos abonnements de production.
    
### <a name="configure-your-office-365-e5-trial-subscription"></a>Configuration de votre abonnement d’évaluation Office 365 E5

Ensuite, configurez votre abonnement Office 365 E5 en y ajoutant des utilisateurs supplémentaires et assignez-les aux licences Office 365 E5.
  
Suivez les instructions dans [Se connecter à Office 365 PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/connect-to-office-365-powershell#connect-with-the-azure-active-directory-powershell-for-graph-module) pour vous connecter à votre abonnement Office 365 avec le module Graph Azure Active Directory PowerShell pour l’ordinateur virtuel CLIENT1.
    
Dans la boîte de dialogue Demande d’informations d’identification Windows PowerShell, saisissez le nom de l’administrateur général Office 365 (exemple : jdoe@contosotoycompany.onmicrosoft.com) et le mot de passe.
  
Entrez le nom de votre organisation (exemple : contosotoycompany) et le code de pays à deux caractères pour indiquer votre emplacement, ainsi qu’un mot de passe de compte commun, puis exécutez les commandes suivantes à partir de l’invite PowerShell :

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$userUPN= "user2@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 2" -GivenName User -SurName 2 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user2"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user3@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 3" -GivenName User -SurName 3 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user3"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign

$userUPN= "user4@" + $orgName + ".onmicrosoft.com"
New-AzureADUser -DisplayName "User 4" -GivenName User -SurName 4 -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user4"
$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License
Set-AzureADUserLicense -ObjectId $userUPN -AssignedLicenses $LicensesToAssign
```
> [!NOTE]
> L’utilisation ici d’un mot de passe courant est pour l’automatisation et la simplicité de configuration pour un environnement de développement et de test. Bien évidemment, cela est hautement déconseillé pour les abonnements de production. 

#### <a name="record-key-information-for-future-reference"></a>Enregistrer les informations clés pour future référence

Nous vous recommandons d’imprimer cet article afin de consigner les informations dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un client Azure AD séparé et un nombre réduit de licences.

Enregistrez les valeurs suivantes :
  
- Nom de l’administrateur général Office 365 : ![](./media/Common-Images/TableLine.png).onmicrosoft.com (indiqué à l’étape 9 de la phase 2)
    
    Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.
    
- Nom de l’organisation de l’abonnement d’évaluation : ![](./media/Common-Images/TableLine.png) (indiqué à l’étape 4 de la phase 2)
    
- Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :
    
  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Enregistrez les noms de compte ici :
    
  - Nom du compte Utilisateur 2 : user2@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte Utilisateur 3 : user3@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte Utilisateur 4 : user4@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
  - Nom du compte Utilisateur 5 : user5@![](./media/Common-Images/TableLine.png).onmicrosoft.com
    
    Enregistrez également les mots de passe communs de ces comptes dans un emplacement sécurisé.
   

#### <a name="using-an-office-365-e5-devtest-environment"></a>Utilisation d’un environnement de développement/test Office 365 E5

Si vous avez simplement besoin d’un environnement Office 365 pour le développement et le test, vous pouvez vous arrêter ici. 

Pour plus d’informations sur les guides de labo de test, voir [les guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md) pour Office 365 et Microsoft 365.
  
### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Ajouter un abonnement d’évaluation de Microsoft 365 E5.

Ensuite, vous vous inscrivez pour l’abonnement d’évaluation Microsoft 365 E5 et l’ajoutez à la même organisation que votre abonnement d’évaluation d’Office 365 E5.
  
Tout d’abord, ajoutez l’abonnement d’évaluation Microsoft 365 E5 et attribuez une licence Microsoft 365 à votre compte d’administrateur général.
  
1. Utilisez une instance privée d’un navigateur Internet pour vous connecter au centre d’administration Microsoft 365 sur [https://admin.microsoft.com](https://admin.microsoft.com)à l’aide de vos informations d’identification de compte d’administrateur général.
    
2. Sur la page **Centre d’administration Microsoft 365**, dans le volet de navigation de gauche, cliquez sur **Facturation > Acheter des services**.
    
3. Sur la page**acheter des services**, recherchez l’élément **Microsoft 365 E5**. Pointez votre souris dessus et cliquez sur **Démarrer l’essai gratuit**.

4. Sur la page **version d’évaluation de Microsoft 365 E5**, choisissez de recevoir un SMS ou un appel, entrez votre numéro de téléphone, puis cliquez sur **envoyer un SMS** ou **m’appeler**.

5. Dans la page **Confirmer votre commande**, cliquez sur **Essayer maintenant**.

6. Dans la page **Réception de la commande**, cliquez sur **Continuer**.

7. Dans le centre d’administration Microsoft 365, cliquez sur **utilisateurs actifs**et votre compte d’administrateur.

8. Cliquez sur **modifier** pour **licences de produits**.

9. Désactivez la licence pour Office 365 Entreprise E5 et activer la licence pour Microsoft 365 E5.

10. Cliquez sur **Enregistrer > Fermer > Fermer**.

Ensuite, répétez les étapes 8 et 11 de la procédure précédente pour tous vos autres comptes (Utilisateur2, Utilisateur3, Utilisateur4 et Utilisateur5).
  
> [!NOTE]
> L’abonnement d’évaluation de Microsoft 365 E5 est de 30 jours. Pour un environnement de test permanent, convertissez cet abonnement en abonnement payant avec un nombre réduit de licences. 
  
### <a name="results"></a>Résultats

Votre environnement de test comporte maintenant :
  
- Abonnement d’évaluation de Microsoft 365 E5.
- Tous vos comptes d’utilisateurs appropriés sont configurés pour utiliser Microsoft 365 E5.
- Un intranet simulé et simplifié.
    
Il s’agit de votre configuration finale.
  
![Phase 2 de la configuration de base de l’entreprise simulée](media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
Vous êtes désormais prêt à profiter des fonctionnalités supplémentaires de [Microsoft 365 Entreprise](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Étapes suivantes

Découvrez les nouveaux ensembles de guides pour les tests de laboratoire :
  
- [Identité](m365-enterprise-test-lab-guides.md#identity)
- [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Protection des informations](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
