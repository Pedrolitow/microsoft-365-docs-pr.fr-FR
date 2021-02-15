---
title: Réseau virtuel entre différents locaux simulé dans un environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 11/14/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: seo-marvel-apr2020
description: 'Résumé : créer un réseau virtuel entre différents locaux simulé dans Microsoft Azure en tant qu’environnement de test Microsoft 365.'
ms.openlocfilehash: ce8b1963e97decc58820bff7b563bb835a843772
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487647"
---
# <a name="simulated-cross-premises-virtual-network-in-a-microsoft-365-test-environment"></a>Réseau virtuel entre différents locaux simulé dans un environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les entreprises et Office 365 Entreprise.*

Cet article vous guide tout au long de la création d’un environnement de cloud hybride simulé avec Microsoft Azure, à l’aide de deux réseaux virtuels Azure. Voici la configuration obtenue. 
  
![Phase 3 de l’environnement de test de réseau virtuel intersites simulé, avec la machine virtuelle DC2 dans XPrem VNet](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Cette configuration simule un environnement de production cloud hybride Azure IaaS et comprend les éléments suivants :
  
- Un réseau local simulé et simplifié hébergé dans un réseau virtuel Azure (réseau virtuel TestLab).
    
- Un réseau virtuel intersites simulé hébergé dans Azure (XPrem).
    
- Une relation d’homologation VNet entre les deux réseaux virtuels.
    
- Un contrôleur de domaine secondaire dans le réseau virtuel XPrem.
    
Ces éléments offrent une base commune à partir de laquelle vous pouvez : 
  
- Développer et tester des applications dans un environnement cloud hybride Azure IaaS simulé.
    
- Créer des configurations de test d’ordinateurs, certains au sein du réseau virtuel TestLab et d’autres au sein du réseau virtuel XPrem, afin de simuler les charges de travail informatiques dans un environnement cloud hybride.
    
Les trois phases principales pour configurer cet environnement de test sont les suivantes :
  
1. Configurer le réseau virtuel TestLab.
    
2. Créer le réseau virtuel intersites.
    
3. Configurer DC2
    
> [!NOTE]
> Cette configuration nécessite un abonnement payant à Azure. 

Vous pouvez utiliser l’environnement résultant pour tester les fonctionnalités de [Microsoft 365](https://www.microsoft.com/microsoft-365/enterprise) pour entreprise à l’aide de guides de laboratoire de [test](m365-enterprise-test-lab-guides.md) supplémentaires ou par vous-même.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Go to [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf) for a visual map to all the articles in the Microsoft 365 for enterprise Test Lab Guide stack.

## <a name="phase-1-configure-the-testlab-virtual-network"></a>Phase 1 : configurer le réseau virtuel TestLab

Suivez les instructions de la **phase 1** de la [configuration entreprise de base simulée](simulated-ent-base-configuration-microsoft-365-enterprise.md) pour configurer les ordinateurs DC1, APP1 et CLIENT1 du réseau virtuel Azure appelé TestLab.
  
Il s’agit de votre configuration actuelle. 
  
![Configuration de base d’une entreprise simulée dans Azure](../media/simulated-cross-premises-microsoft-365-enterprise/25a010a6-c870-4690-b8f3-84421f8bc5c7.png)
  
## <a name="phase-2-create-the-xprem-virtual-network"></a>Phase 2 : Créer le réseau virtuel XPrem

Dans cette phase, vous devez créer et configurer le nouveau réseau virtuel XPrem et le connecter au réseau virtuel TestLab avec l’homologation VNet.
  
Tout d’abord, démarrez une invite PowerShell Azure sur votre ordinateur local.
  
> [!NOTE]
> Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](https://docs.microsoft.com/powershell/azureps-cmdlets-docs/). 
  
Connectez-vous à votre compte Azure avec cette commande.
  
```powershell
Connect-AzAccount
```

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Définissez votre abonnement Azure. Remplacez tout le texte entre guillemets, y compris les caractères \< and >, avec les noms corrects.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Créez ensuite le réseau virtuel XPrem et protégez-le avec un groupe de sécurité réseau, à l’aide des commandes suivantes.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$Testnet=New-AzVirtualNetworkSubnetConfig -Name "Testnet" -AddressPrefix 192.168.0.0/24
New-AzVirtualNetwork -Name "XPrem" -ResourceGroupName $rgName -Location $locName -AddressPrefix 192.168.0.0/16 -Subnet $Testnet -DNSServer 10.0.0.4
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
$nsg=Get-AzNetworkSecurityGroup -Name "Testnet" -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name "Testnet" -AddressPrefix 192.168.0.0/24 -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Vous devez ensuite créer la relation d’homologation VNet entre les réseaux virtuels TestLab et XPrem, à l’aide des commandes suivantes.
  
```powershell
$rgName="<name of the resource group that you used for your TestLab virtual network>"
$vnet1=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name TestLab
$vnet2=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name XPrem
Add-AzVirtualNetworkPeering -Name TestLab2XPrem -VirtualNetwork $vnet1 -RemoteVirtualNetworkId $vnet2.Id
Add-AzVirtualNetworkPeering -Name XPrem2TestLab -VirtualNetwork $vnet2 -RemoteVirtualNetworkId $vnet1.Id
```

Il s’agit de votre configuration actuelle. 
  
![Phase 2 de l’environnement de test de réseau virtuel intersites simulé, avec XPrem VNet et la relation d’homologation VNet](../media/simulated-cross-premises-microsoft-365-enterprise/cac5e999-69c7-4f4c-bfce-a7f4006115ef.png)
  
## <a name="phase-3-configure-dc2"></a>Phase 3 : Configurer DC2

Dans cette phase, vous devez créer la machine virtuelle DC2 dans le réseau virtuel XPrem, puis la configurer comme un contrôleur de domaine répliqué.
  
Tout d’abord, créez une machine virtuelle pour DC2. Exécutez ces commandes dans l’invite de commande Azure PowerShell sur votre ordinateur local.
  
```powershell
$rgName="<your resource group name>"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name XPrem -ResourceGroupName $rgName
$pip=New-AzPublicIpAddress -Name DC2-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name DC2-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress 192.168.0.4
$vm=New-AzVMConfig -VMName DC2 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for DC2."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName DC2 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "DC2-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
$diskConfig=New-AzDiskConfig -AccountType "Standard_LRS" -Location $locName -CreateOption Empty -DiskSizeGB 20
$dataDisk1=New-AzDisk -DiskName "DC2-DataDisk1" -Disk $diskConfig -ResourceGroupName $rgName
$vm=Add-AzVMDataDisk -VM $vm -Name "DC2-DataDisk1" -CreateOption Attach -ManagedDiskId $dataDisk1.Id -Lun 1
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ensuite, connectez-vous à la nouvelle machine virtuelle DC2 à partir du [portail Azure](https://portal.azure.com) à l’aide du nom de compte et du mot de passe de l’administrateur local.
  
Ensuite, configurez une règle de pare-feu Windows pour autoriser le trafic afin d’effectuer des tests de connectivité de base. Exécutez ces commandes à l’invite de commande Windows PowerShell de niveau administrateur sur DC2. 
  
```powershell
Set-NetFirewallRule -DisplayName "File and Printer Sharing (Echo Request - ICMPv4-In)" -enabled True
ping dc1.corp.contoso.com
```

La commande ping doit aboutir à quatre réponses réussies à partir de l’adresse IP 10.0.0.4. Il s’agit d’un test du trafic sur la relation d’homologation VNet. 
  
Ensuite, ajoutez le disque de données supplémentaire en tant que nouveau volume avec la lettre de lecteur F: avec cette commande de l’invite de commande Windows PowerShell sur DC2.
  
```powershell
Get-Disk | Where PartitionStyle -eq "RAW" | Initialize-Disk -PartitionStyle MBR -PassThru | New-Partition -AssignDriveLetter -UseMaximumSize | Format-Volume -FileSystem NTFS -NewFileSystemLabel "WSAD Data"
```

Configurez ensuite DC2 en tant que contrôleur de domaine répliqué pour le domaine corp.contoso.com. Exécutez les commandes suivantes à partir de l’invite de commande Windows PowerShell sur DC2.
  
```powershell
Install-WindowsFeature AD-Domain-Services -IncludeManagementTools
Install-ADDSDomainController -Credential (Get-Credential CORP\User1) -DomainName "corp.contoso.com" -InstallDns:$true -DatabasePath "F:\NTDS" -LogPath "F:\Logs" -SysvolPath "F:\SYSVOL"
```

Notez que vous devez fournir à la fois le mot de passe CORP\\User1 et le mot de passe du mode restauration des services d’annuaire, puis redémarrer DC2. 
  
Maintenant que le réseau virtuel XPrem possède son propre serveur DNS (DC2), vous devez configurer le réseau virtuel XPrem pour utiliser ce serveur DNS. Exécutez ces commandes à partir de l’invite de commande Azure PowerShell sur votre ordinateur local.
  
```powershell
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -name "XPrem"
$vnet.DhcpOptions.DnsServers="192.168.0.4" 
Set-AzVirtualNetwork -VirtualNetwork $vnet
Restart-AzVM -ResourceGroupName $rgName -Name "DC2"
```

À partir du portail Azure sur votre ordinateur local, connectez-vous à DC1 avec les informations d’identification CORP\\User1. Pour configurer le domaine CORP afin que les ordinateurs et les utilisateurs utilisent leur contrôleur de domaine local pour l’authentification, exécutez les commandes suivantes à partir d’une invite de commande Windows PowerShell de niveau administrateur sur DC1.
  
```powershell
New-ADReplicationSite -Name "TestLab" 
New-ADReplicationSite -Name "XPrem"
New-ADReplicationSubnet -Name "10.0.0.0/8" -Site "TestLab"
New-ADReplicationSubnet -Name "192.168.0.0/16" -Site "XPrem"
```

Il s’agit de votre configuration actuelle. 
  
![Phase 3 de l’environnement de test de réseau virtuel intersites simulé, avec la machine virtuelle DC2 dans XPrem VNet](../media/simulated-cross-premises-microsoft-365-enterprise/df458c56-022b-4688-ab18-056c3fd776b4.png)
  
Votre environnement cloud hybride Azure simulé est prêt pour le test.
  
Vous êtes maintenant prêt à expérimenter des fonctionnalités supplémentaires de [Microsoft 365 pour entreprise.](https://www.microsoft.com/microsoft-365/enterprise)
  
## <a name="next-steps"></a>Étapes suivantes

Découvrez les nouveaux ensembles de guides pour les tests de laboratoire :
  
- [Identité](m365-enterprise-test-lab-guides.md#identity)
- [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Protection des informations](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
