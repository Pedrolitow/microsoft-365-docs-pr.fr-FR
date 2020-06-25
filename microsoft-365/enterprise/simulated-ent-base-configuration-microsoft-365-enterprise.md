---
title: Configuration de base d’une entreprise simulée pour Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Utilisez ce Guide de Laboratoire Test afin de créer une simulation d’environnement de test dédiée à Microsoft 365 Entreprise.
ms.openlocfilehash: 486429bf9e1c0a88c9beb01a092f968256c1fa77
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44818494"
---
# <a name="the-simulated-enterprise-base-configuration"></a>Configuration de base d’une entreprise simulée

*Ce Guide de Laboratoire Test peut être utilisé pour les environnements de test Microsoft 365 Enterprise et Office 365 Enterprise.*

Vous trouverez dans cet article des instructions détaillées pour créer un environnement simplifié pour Microsoft 365 Entreprise qui comprend :

- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet simplifié d’une organisation connecté à Internet, composé de trois machines virtuelles sur un réseau virtuel Azure (DC1, APP1 et CLIENT1).
 
![Configuration de base d’une entreprise simulée](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)

Vous pouvez utiliser l’environnement obtenu pour tester les fonctions et le bon fonctionnement de[Microsoft 365 Enterprise](https://www.microsoft.com/microsoft-365/enterprise), par vous-même ou en suivant les conseils des [guides de laboratoire de test](m365-enterprise-test-lab-guides.md).

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Accédez au [Guide de laboratoire de laboratoire de test Microsoft 365 Entreprise](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) d’une carte visuelle à tous les Articles de la pile de guides de laboratoires de test Microsoft 365 Enterprise.

## <a name="phase-1-create-a-simulated-intranet"></a>Phase 1: Créer un intranet simulé

Dans cette phase, vous allez créer un intranet simulé dans les services d’infrastructure Azure comprenant un contrôleur de domaine Windows Server Active Directory, un serveur d’application et un ordinateur client. 

Vous utiliserez ces ordinateurs dans des[Guides de laboratoire de Test Microsoft 365 Enterprise](m365-enterprise-test-lab-guides.md)supplémentaires afin de configurer et montrer l’identité hybride et les autres fonctionnalités.

### <a name="method-1-build-your-simulated-intranet-with-an-azure-resource-manager-template"></a>Méthode 1: Créer votre intranet simulé avec un Modèle de Gestion de Ressources Azure 

In this method, you use an Azure Resource Manager (ARM) template to build out the simulated intranet. ARM templates contain all of the instructions to create the Azure networking infrastructure, the virtual machines, and their configuration.

Avant de déployer le modèle, parcourez le[modèle de la page Lisez-moi](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) et obtenez les informations suivantes prêtes :

- The public DNS domain name of your test environment (testlab.\<your public domain>). You'll need to enter this name in the **Domain Name field** of the **Custom deployment** page.
- A DNS label prefix for the URLs of the public IP addresses of your virtual machines. You'll need to enter this label in the **Dns Label Prefix** field of the **Custom deployment** page.

Après avoir lu via les instructions, cliquez sur **déployer vers Azure** sur la [page modèle LISEZMOI](https://github.com/maxskunkworks/TLG/tree/master/tlg-base-config_3-vm.m365-ems) pour commencer.

>[!Note]
>L’Intranet simulé créé par le modèle GRA nécessite un abonnement payant à Azure.
>

Voici votre configuration une fois le modèle terminé.

![L’intranet simulé dans les services d’infrastructure Azure.](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)

### <a name="method-2-build-your-simulated-intranet-with-azure-powershell"></a>Méthode 2 : Créer votre intranet simulé avec Azure PowerShell

En utilisant cette méthode, vous utilisez Windows PowerShell et le module Azure PowerShell afin de créer l’infrastructure de réseau, les machines virtuelles et leur configuration.

Use this method if you want to get experience creating elements of Azure infrastructure one step at a time with PowerShell. You can then customize the PowerShell command blocks for your own deployment of other virtual machines in Azure.

#### <a name="step-1-create-dc1"></a>Phase 1: création de DC1

Durant cette phase, nous allons créer un réseau virtuel Azure et ajouter la machine virtuelle DC1 qui est un contrôleur de domaine pour un domaine Windows Server Active Directory (AD).

Tout d’abord, démarrez une invite de commandes Windows PowerShell sur votre ordinateur local.
  
> [!NOTE]
> The following command sets use the latest version of Azure PowerShell. See [Get started with Azure PowerShell cmdlets](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). 
  
Connectez-vous à votre compte Azure avec la commande suivante.
  
```powershell
Connect-AzAccount
```

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Set your Azure subscription. Replace everything within the quotes, including the < and > characters, with the correct name.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Next, create a new resource group for your simulated enterprise test lab. To determine a unique resource group name, use this command to list your existing resource groups.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Create your new resource group with these commands. Replace everything within the quotes, including the < and > characters, with the correct names.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Next, you create the TestLab virtual network that will host the Corpnet subnet of the simulated enterprise environment and protect it with a network security group. Fill in the name of your resource group and run these commands at the PowerShell command prompt on your local computer.
  
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

Ensuite, vous créez la machine virtuelle DC1 et le configurez comme contrôleur de domaine pour le **testlab.**\<your public domain> Domaine AD DS et serveur DNS pour les machines virtuelles du réseau virtuel TestLab. Par exemple, si votre nom de domaine public est ** <span>contoso</span>.com**, la machine virtuelle DC1 sera un contrôleur de domaine pour le **<span>testlab</span>. contoso.com** domaine.
  
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

You will be prompted for a user name and password for the local administrator account on DC1. Use a strong password and record both the name and password in a secure location.
  
Ensuite, connectez-vous à la machine virtuelle DC1.
  
1. Dans le [Portail Azure](https://portal.azure.com), cliquez sur **Groupes de Ressources >** [nom de votre nouveau groupe de ressources] **> DC1 > Se connecter**.
    
2. In the open pane, click **Download RDP file**. Open the DC1.rdp file that is downloaded, and then click **Connect**.
    
3. Spécifiez le nom du compte Administrateur local DC1 :
    
   - Pour Windows 7 :
    
     In the **Windows Security** dialog box, click **Use another account**. In **User name**, type **DC1\\**[Local administrator account name].
    
   - Pour Windows 8 ou Windows 10 :
    
     In the **Windows Security** dialog box, click **More choices**, and then click **Use a different account**. In **User name**, type **DC1\\**[Local administrator account name].
    
4. Dans **Mot de passe**, tapez le mot de passe du compte Administrateur local, puis cliquez sur **OK**.
    
5. Quand vous y êtes invité, cliquez sur **Oui**.
    
Ensuite, ajoutez un disque de données supplémentaire en tant que nouveau volume avec la lettre de lecteur F:, à l’aide de la commande suivante, dans l’invite de commande Windows PowerShell au niveau administrateur sur DC1.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Ensuite, configurez DC1 comme un contrôleur de domaine et un serveur DNS pour le domaine **testlab.**\<your public domain> . Spécifiez votre nom de domaine public, supprimez les \< and > caractères, puis exécutez ces commandes dans une invite de commandes Windows PowerShell au niveau de l’administrateur sur DC1.
  
```powershell
$yourDomain="<your public domain>"
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSForest -DomainName testlab.$yourDomain -DatabasePath "F:\NTDS" -SysvolPath "F:\SYSVOL" -LogPath "F:\Logs"
```
You will need to specify a safe mode administrator password. Store this password in a secure location.
  
Notez que l’exécution de ces commandes peut prendre quelques minutes.
  
Après le redémarrage de DC1, reconnectez-vous à la machine virtuelle DC1.
  
1. Dans le [Portail Azure](https://portal.azure.com), cliquez sur **Groupes de Ressources >** [nom de votre groupe de ressources] **> DC1 > Se connecter**.
    
2. Exécutez le fichier DC1.rdp qui est téléchargé, puis cliquez sur **Se connecter**.
    
3. In **Windows Security**, click **Use another account**. In **User name**, type **TESTLAB\\**[Local administrator account name].
    
4. Dans **Mot de passe**, tapez le mot de passe du compte Administrateur local, puis cliquez sur **OK**.
    
5. Quand vous y êtes invité, cliquez sur **Oui**.
    
Next, create a user account in Active Directory that will be used when logging in to TESTLAB domain member computers. Run this command at an administrator-level Windows PowerShell command prompt.
  
```powershell
New-ADUser -SamAccountName User1 -AccountPassword (read-host "Set user password" -assecurestring) -name "User1" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```

Note that this command prompts you to supply the User1 account password. Because this account will be used for remote desktop connections for all TESTLAB domain member computers, choose a strong password. Record the User1 account password and store it in a secured location.
  
Next, configure the new User1 account as a domain, enterprise, and schema administrator. Run this command at the administrator-level Windows PowerShell command prompt.
  
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
  
![Phase 1 de la configuration de base de l’entreprise simulée](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase1.png)
  
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
  
Pour vérifier la résolution de noms et les communications réseau entre APP1 et DC1, exécutez la commande **ping dc1.testlab.**\<your public domain name> et vérifiez qu’il y a quatre réponses.
  
Maintenant, associez la machine virtuelle APP1 au domaine TESTLAB avec ces commandes à l’invite Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
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
  
![Phase 2 de la configuration de base de l’entreprise simulée](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase2.png)
  
#### <a name="step-3-configure-client1"></a>Phase 3:Configurer CLIENT1

Durant cette phase, vous allez créer et configurer CLIENT1, qui se comporte comme un ordinateur portable, une tablette ou un ordinateur de bureau classique sur l’intranet.

> [!NOTE]  
> The following command set creates CLIENT1 running Windows Server 2016 Datacenter, which can be done for all types of Azure subscriptions. If you have a Visual Studio-based Azure subscription, you can create CLIENT1 running Windows 10 with the [Azure portal](https://portal.azure.com). 
  
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
  
Pour vérifier la résolution de noms et les communications réseau entre CLIENT1 et DC1, exécutez la commande **ping dc1.testlab.**\<your public domain name> dans une invite de commandes Windows PowerShell et vérifiez qu’il y a quatre réponses.
  
Maintenant, associez la machine virtuelle CLIENT1 au domaine TESTLAB avec ces commandes à l’invite Windows PowerShell.
  
```powershell
$yourDomain="<your public domain name>"
Add-Computer -DomainName ("testlab." + $yourDomain)
Restart-Computer
```

Les informations d’identification de votre compte de domaine TESTLAB\\Utilisateur1 doivent être fournies après l’exécution de la commande **Add-Computer**.
  
Après le redémarrage de CLIENT1, connectez-vous en utilisant le mot de passe et le nom du compte TESTLAB\\Utilisateur1 et ouvrez une invite de commandes Windows PowerShell de niveau administrateur.
  
Ensuite, vérifiez que vous pouvez accéder aux ressources web et de partage de fichiers sur APP1 de CLIENT1.
  
1. Dans le Gestionnaire de Serveur, dans le volet de l’arborescence, cliquez sur **Serveur Local**.
    
2. Dans **Propriétés pour CLIENT1**, cliquez sur **Activer** à côté de **Configuration de sécurité renforcée d’Internet Explorer**.
    
3. Dans **Configuration de sécurité renforcée d’Internet Explorer**, cliquez sur **Désactiver** pour **Administrateurs** et **Utilisateurs**, puis cliquez sur **OK**.
    
4. Sur l’écran d’accueil, cliquez sur **Internet Explorer**, puis sur **OK**.
    
5. Dans la barre d’adresses, tapez **http<span>://</span>app1.testab.**\<your public domain name>**/**, puis appuyez sur ENTRER. La page web Internet Information Services par défaut pour APP1 s’affiche.
    
6. Dans la barre des tâches du bureau, cliquez sur l’icône de l’Explorateur de fichiers.
    
7. In the address bar, type **\\\\app1\\Files**, and then press ENTER. You should see a folder window with the contents of the Files shared folder.
    
8. In the **Files** shared folder window, double-click the **Example.txt** file. You should see the contents of the Example.txt file.
    
9. Fermez les fenêtres de dossiers partagés **Exemple.txt - Bloc-notes** et **Fichiers**.
    
Il s’agit de votre configuration actuelle.
  
![Phase 3 de la configuration de base de l’entreprise simulée](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase3.png)


## <a name="phase-2-create-your-microsoft-365-e5-subscription"></a>Phase 2 : Création de votre abonnement Microsoft 365 E5

In this phase, you create a new Microsoft 365 E5 subscription that uses a new Azure AD tenant, one that is separate from your production subscription. You can do this in two ways:

- Utiliser un abonnement d’évaluation de Microsoft 365 E5. 

  The Microsoft 365 E5 trial subscription is 30 days, which can be easily extended to 60 days. When the trial subscription expires, you must either convert it to a paid subscription or create a new trial subscription. Creating new trial subscriptions means you will leave your configuration, which could include complex scenarios, behind.  

- Utiliser un abonnement de production de Microsoft 365 E5 distinct avec un nombre réduit de licences.

  This is an additional cost, but ensures that you have a working test environment to try features, configurations, and scenarios that does not expire. You can use the same test environment over the long term for proofs of concept, demonstration to peers and management, and application development and testing. This is the recommended method.

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Inscription à un abonnement d’évaluation Office 365 E5

Connectez-vous à CLIENT1 avec le compte CORP\User1 à partir du Portail Microsoft Azure.

Pour créer un abonnement d’évaluation Office 365 E5, suivez les instructions de [phase 1](lightweight-base-configuration-microsoft-365-enterprise.md#phase-1-create-your-office-365-e5-subscription) du Guide de laboratoire de test de la configuration de base légère.

Pour configurer un abonnement d’évaluation Office 365 E5, suivez les instructions de [phase 2](lightweight-base-configuration-microsoft-365-enterprise.md#phase-2-configure-your-office-365-trial-subscription) du Guide de laboratoire de test de la configuration de base légère.

#### <a name="using-an-office-365-e5-test-environment"></a>Utilisation d’un environnement de test Office 365 E5

Si vous avez simplement besoin d’un environnement de test Office 365, vous pouvez vous arrêter ici. 

Pour plus d’informations sur les guides de labo de test, voir [les guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md) pour Office 365 et Microsoft 365.

### <a name="add-a-microsoft-365-e5-trial-subscription"></a>Ajouter un abonnement d’évaluation de Microsoft 365 E5.

Pour configurer un abonnement d’évaluation Microsoft 365 E5 et configurer des comptes d’utilisateur avec licences, suivez les instructions de [phase 3](lightweight-base-configuration-microsoft-365-enterprise.md#phase-3-add-a-microsoft-365-e5-trial-subscription) du Guide de laboratoire de test de la configuration de base légère.

  
## <a name="results"></a>Résultats

Votre environnement de test comporte maintenant :
  
- Abonnement d’évaluation de Microsoft 365 E5.
- Tous vos comptes d’utilisateurs appropriés sont configurés pour utiliser Microsoft 365 E5.
- Un intranet simulé et simplifié.
    
Il s’agit de votre configuration finale.
  
![Phase 2 de la configuration de base de l’entreprise simulée](../media/simulated-ent-base-configuration-microsoft-365-enterprise/Phase4.png)
  
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
