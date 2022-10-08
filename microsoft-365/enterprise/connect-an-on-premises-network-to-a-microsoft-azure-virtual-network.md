---
title: Connecter un réseau local à Microsoft Azure Virtual Network
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/21/2019
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- scotvorg
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: 81190961-5454-4a5c-8b0e-6ae75b9fb035
description: 'Résumé : Découvrez comment configurer un réseau virtuel Azure intersites pour les charges de travail de serveur Office avec une connexion VPN de site à site.'
ms.openlocfilehash: 2056f8b901a366143c5869c903002528439fce18
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68194860"
---
# <a name="connect-an-on-premises-network-to-a-microsoft-azure-virtual-network"></a>Connecter un réseau local à Microsoft Azure Virtual Network

Un réseau virtuel Azure entre différents locaux est connecté à votre réseau local, étendant ainsi votre réseau pour inclure des sous-réseaux et machines virtuelles hébergés dans les services d’infrastructure Azure. Cette connexion permet aux ordinateurs de votre réseau local d’accéder directement aux machines virtuelles dans Azure et inversement. 

Par exemple, un serveur de synchronisation d’annuaires s’exécutant sur une machine virtuelle Azure doit interroger vos contrôleurs de domaine locaux pour les modifications apportées aux comptes et synchroniser ces modifications avec votre abonnement Microsoft 365. Cet article vous montre comment configurer un réseau virtuel Azure intersite à l’aide d’une connexion de réseau privé virtuel (VPN) de site à site prête à héberger des machines virtuelles Azure.

## <a name="configure-a-cross-premises-azure-virtual-network"></a>Configurer un réseau virtuel Azure interstrés

Your virtual machines in Azure don't have to be isolated from your on-premises environment. To connect Azure virtual machines to your on-premises network resources, you must configure a cross-premises Azure virtual network. The following diagram shows the required components to deploy a cross-premises Azure virtual network with a virtual machine in Azure.
  
![Réseau local connecté à Microsoft Azure par une connexion VPN de site à site.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
 
In the diagram, there are two networks connected by a site-to-site VPN connection: the on-premises network and the Azure virtual network. The site-to-site VPN connection is:

- entre deux points de terminaison qui sont adressables et se trouvent sur l’Internet public ;
- terminée par un appareil VPN sur le réseau local et une passerelle VPN Azure sur le réseau virtuel Azure.

The Azure virtual network hosts virtual machines. Network traffic originating from virtual machines on the Azure virtual network gets forwarded to the VPN gateway, which then forwards the traffic across the site-to-site VPN connection to the VPN device on the on-premises network. The routing infrastructure of the on-premises network then forwards the traffic to its destination.

>[!Note]
>You can also use [ExpressRoute](https://azure.microsoft.com/services/expressroute/), which is a direct connection between your organization and Microsoft's network. Traffic over ExpressRoute does not travel over the public Internet. This article does not describe the use of ExpressRoute.
>
  
Pour configurer la connexion VPN entre votre réseau Azure Virtual Network et votre réseau local, procédez comme suit : 
  
1. **Local :** Définissez et créez un itinéraire réseau local pour l'espace d'adressage du réseau virtuel Azure qui pointe vers votre périphérique VPN local.
    
2. **Microsoft Azure** : Créez un réseau virtuel Azure avec une connexion VPN de site à site. 
    
3. **Local :** Configurez votre périphérique VPN matériel ou logiciel local pour marquer la fin de la connexion VPN en utilisant la sécurité du protocole Internet (IPsec).
    
Après avoir établi la connexion VPN de site à site, vous ajoutez des machines virtuelles Azure aux sous-réseaux du réseau virtuel.
  
## <a name="plan-your-azure-virtual-network"></a>Planification de votre réseau Azure Virtual Network
<a name="PlanningVirtual"></a>

### <a name="prerequisites"></a>Conditions préalables
<a name="Prerequisites"></a>

- An Azure subscription. For information about Azure subscriptions, go to the [How To Buy Azure page](https://azure.microsoft.com/pricing/purchase-options/).
    
- Un espace d’adressage IPv4 privé disponible à affecter au réseau virtuel et à ses sous-réseaux, avec suffisamment d’espace pour leur croissance afin d’accueillir le nombre de machines virtuelles nécessaires maintenant et à l’avenir.
    
- An available VPN device in your on-premises network to terminate the site-to-site VPN connection that supports the requirements for IPsec. For more information, see [About VPN devices for site-to-site virtual network connections](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
    
- La modification de votre infrastructure de routage pour que le trafic routé vers l'espace d'adressage du réseau virtuel Azure soit acheminé vers le périphérique VPN qui héberge la connexion VPN de site à site.
    
- Un proxy web fournissant un accès à Internet aux ordinateurs connectés au réseau local et au réseau virtuel Azure.
    
### <a name="solution-architecture-design-assumptions"></a>Hypothèses en matière de conception de l’architecture de la solution

La liste suivante répertorie les choix de conception qui ont été faits pour l’architecture de cette solution. 
  
- This solution uses a single Azure virtual network with a site-to-site VPN connection. The Azure virtual network hosts a single subnet that can contain multiple virtual machines. 
    
- You can use the Routing and Remote Access Service (RRAS) in Windows Server 2016 or Windows Server 2012 to establish an IPsec site-to-site VPN connection between the on-premises network and the Azure virtual network. You can also use other options, such as Cisco or Juniper Networks VPN devices.
    
- The on-premises network might still have network services like Active Directory Domain Services (AD DS), Domain Name System (DNS), and proxy servers. Depending on your requirements, it might be beneficial to place some of these network resources in the Azure virtual network.
    
For an existing Azure virtual network with one or more subnets, determine whether there is remaining address space for an additional subnet to host your needed virtual machines, based on your requirements. If you don't have remaining address space for an additional subnet, create an additional virtual network that has its own site-to-site VPN connection.
  
### <a name="plan-the-routing-infrastructure-changes-for-the-azure-virtual-network"></a>Planification des modifications d’infrastructure de routage pour le réseau virtuel Azure

Vous devez configurer votre infrastructure de routage locale pour acheminer le trafic destiné à l'espace d'adressage du réseau virtuel Azure au périphérique VPN local qui héberge la connexion VPN de site à site.
  
La méthode de mise à jour exacte de votre infrastructure de routage dépend de votre gestion des informations de routage, c’est-à-dire :
  
- Des mises à jour de la table de routage en fonction de la configuration manuelle.
    
- Des mises à jour de la table de routage en fonction des protocoles de routage, tels que le protocole RIP (Routing Information Protocol) ou le protocole OSPF (Open Shortest Path First).
    
Consultez votre spécialiste du routage pour vous assurer que le trafic destiné au réseau virtuel Azure est transféré au périphérique VPN local.
  
### <a name="plan-for-firewall-rules-for-traffic-to-and-from-the-on-premises-vpn-device"></a>Planification des règles de pare-feu pour le trafic vers et depuis le périphérique VPN local

Si votre périphérique VPN se trouve sur un réseau de périmètre qui dispose d’un pare-feu entre le réseau de périmètre et Internet, vous devrez peut-être configurer le pare-feu pour que les règles suivantes autorisent la connexion VPN de site à site.
  
- Trafic vers le périphérique VPN (entrant, à partir d’Internet) :
    
  - Adresse IP de destination du périphérique VPN et protocole IP 50
    
  - Adresse IP de destination du périphérique VPN et port 500 de destination UDP
    
  - Adresse IP de destination du périphérique VPN et port 4500 de destination UDP
    
- Trafic provenant du périphérique VPN (sortant, en direction d’Internet) :
    
  - Adresse IP source du périphérique VPN et protocole IP 50
    
  - Adresse IP source du périphérique VPN et port 500 source UDP
    
  - Adresse IP source du périphérique VPN et port 4500 source UDP
    
### <a name="plan-for-the-private-ip-address-space-of-the-azure-virtual-network"></a>Planification de l’espace d’adressage IP privé du réseau virtuel Azure

L'espace d'adressage IP privé du réseau virtuel Azure doit pouvoir prendre en charge les adresses utilisées par Azure pour héberger le réseau virtuel et au moins un sous-réseau disposant de suffisamment d'adresses pour vos machines virtuelles Azure.
  
Pour déterminer le nombre d’adresses nécessaires pour le sous-réseau, comptez le nombre de machines virtuelles dont vous avez besoin maintenant, estimez la croissance future, puis utilisez le tableau suivant pour déterminer la taille du sous-réseau.
  
|**Nombre de machines virtuelles nécessaires**|**Nombre de bits d'hôte requis**|**Taille du sous-réseau**|
|:-----|:-----|:-----|
|1-3  <br/> |3  <br/> |/29  <br/> |
|4-11  <br/> |4  <br/> |/28  <br/> |
|12-27  <br/> |5  <br/> |/27  <br/> |
|28-59  <br/> |6  <br/> |/26  <br/> |
|60-123  <br/> |7   <br/> |/25  <br/> |
   
### <a name="planning-worksheet-for-configuring-your-azure-virtual-network"></a>Planification de la feuille de travail pour la configuration de votre réseau virtuel Azure
<a name="worksheet"> </a>

Avant de créer un réseau virtuel Azure pour héberger des machines virtuelles, vous devez déterminer les paramètres nécessaires dans les tableaux suivants.
  
Pour les paramètres du réseau virtuel, remplissez le tableau V.
  
 **Tableau V : configuration de réseau virtuel entre différents locaux**
  
|**Élément**|**Élément Configuration**|**Description**|**Valeur**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |Nom du réseau virtuel  <br/> |Nom à affecter au réseau virtuel Azure (par exemple, DirSyncNet).  <br/> |![Ligne.](../media/Common-Images/TableLine.png) |
|2.  <br/> |Emplacement du réseau virtuel  <br/> |Centre de données Azure qui contiendra le réseau virtuel (par exemple, Ouest des États-Unis).  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |Adresse IP du périphérique VPN  <br/> |Adresse IPv4 publique de l'interface de votre périphérique VPN sur Internet. Renseignez-vous auprès de votre service informatique pour déterminer cette adresse.  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
|4.  <br/> |Espace d’adressage du réseau virtuel  <br/> |The address space (defined in a single private address prefix) for the virtual network. Work with your IT department to determine this address space. The address space should be in Classless Interdomain Routing (CIDR) format, also known as network prefix format. An example is 10.24.64.0/20.  <br/> |![Ligne.](../media/Common-Images/TableLine.png) <br/> |
|5.  <br/> |Clé partagée IPsec  <br/> |A 32-character random, alphanumeric string that will be used to authenticate both sides of the site-to-site VPN connection. Work with your IT or security department to determine this key value and then store it in a secure location. Alternately, see [Create a random string for an IPsec preshared key](https://social.technet.microsoft.com/wiki/contents/articles/32330.create-a-random-string-for-an-ipsec-preshared-key.aspx).  <br/> |![Ligne.](../media/Common-Images/TableLine.png) <br/> |
   
Remplissez le tableau S pour les sous-réseaux de cette solution.
  
- For the first subnet, determine a 28-bit address space (with a /28 prefix length) for the Azure gateway subnet. See [Calculating the gateway subnet address space for Azure virtual networks](/archive/blogs/solutions_advisory_board/calculating-the-gateway-subnet-address-space-for-azure-virtual-networks) for information about how to determine this address space.
    
- Pour le deuxième sous-réseau, indiquez un nom convivial, un espace d’adressage IP unique fondé sur l’espace d’adressage de réseau virtuel et une description de l’objectif.
    
Work with your IT department to determine these address spaces from the virtual network address space. Both address spaces should be in CIDR format.
  
 **Tableau S : sous-réseaux dans le réseau virtuel**
  
|**Élément**|**Nom du sous-réseau**|**Espace d'adressage de sous-réseau**|**Objectif**|
|:-----|:-----|:-----|:-----|
|1.  <br/> |GatewaySubnet  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |Sous-réseau utilisé par la passerelle Azure.  <br/> |
|2.  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
   
For the on-premises DNS servers that you want the virtual machines in the virtual network to use, fill in Table D. Give each DNS server a friendly name and a single IP address. This friendly name does not need to match the host name or computer name of the DNS server. Note that two blank entries are listed, but you can add more. Work with your IT department to determine this list.
  
 **Tableau D : serveurs DNS locaux**
  
|**Élément**|**Nom convivial du serveur DNS**|**Adresse IP du serveur DNS**|
|:-----|:-----|:-----|
|1.  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
   
Pour acheminer les paquets du réseau virtuel Azure vers le réseau de votre organisation par le biais de la connexion VPN de site à site, vous devez configurer le réseau virtuel avec un réseau local. Ce réseau local possède la liste des espaces d’adressage (au format CIDR) pour l’ensemble des emplacements sur le réseau local de votre organisation que les machines virtuelles du réseau virtuel doivent atteindre. Il peut s’agir de l’ensemble des emplacements sur le réseau local ou un sous-ensemble. La liste des espaces d’adressage qui définissent votre réseau local doit être unique et ne doit pas se chevaucher avec les espaces d’adressage utilisés pour ce réseau virtuel ou les autres réseaux virtuels intersites.
  
For the set of local network address spaces, fill in Table L. Note that three blank entries are listed but you will typically need more. Work with your IT department to determine this list.
  
 **Tableau L : préfixes d'adresse pour le réseau local**
  
|**Élément**|**Espace d'adressage du réseau local**|
|:-----|:-----|
|1.  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
|2.  <br/> |![Ligne.](../media/Common-Images/TableLine.png)  <br/> |
|3.  <br/> |![ligne](../media/Common-Images/TableLine.png)  <br/> |
   
## <a name="deployment-roadmap"></a>Feuille de route de déploiement
<a name="DeploymentRoadmap"> </a>

La création du réseau virtuel entre différents locaux et l'ajout de machines virtuelles dans Azure se composent de trois phases :
  
- Phase 1 : préparer votre réseau local.
    
- Phase 2 : créer le réseau virtuel entre différents locaux dans Azure.
    
- Phase 3 (facultative) : ajouter des machines virtuelles.
    
### <a name="phase-1-prepare-your-on-premises-network"></a>Phase 1 : préparer votre réseau local
<a name="Phase1"></a>

You must configure your on-premises network with a route that points to and ultimately delivers traffic destined for the address space of the virtual network to the router on the edge of the on-premises network. Consult with your network administrator to determine how to add the route to the routing infrastructure of your on-premises network.
  
Voici la configuration finale.
  
![Le réseau local doit disposer d’un itinéraire pour l’espace d’adressage du réseau virtuel qui pointe vers l’appareil VPN.](../media/90bab36b-cb60-4ea5-81d5-4737b696d41c.png)
  
### <a name="phase-2-create-the-cross-premises-virtual-network-in-azure"></a>Phase 2 : créer le réseau virtuel entre différents locaux dans Azure
<a name="Phase2"></a>

First, open an Azure PowerShell prompt. If you have not installed Azure PowerShell, see [Get started with Azure PowerShell](/powershell/azure/get-started-azureps).

 
Ensuite, connectez-vous à votre compte Azure avec cette commande.
  
```powershell
Connect-AzAccount
```

Obtenez le nom de votre abonnement à l’aide de la commande suivante.
  
```powershell
Get-AzSubscription | Sort SubscriptionName | Select SubscriptionName
```

Set your Azure subscription with these commands. Replace everything within the quotes, including the < and > characters, with the correct subscription name.
  
```powershell
$subscrName="<subscription name>"
Select-AzSubscription -SubscriptionName $subscrName
```

Next, create a new resource group for your virtual network. To determine a unique resource group name, use this command to list your existing resource groups.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Créez votre nouveau groupe de ressources avec ces commandes.
  
```powershell
$rgName="<resource group name>"
$locName="<Table V - Item 2 - Value column>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ensuite, créez le réseau virtuel Azure.
  
```powershell
# Fill in the variables from previous values and from Tables V, S, and D
$rgName="<name of your new resource group>"
$locName="<Azure location of your new resource group>"
$vnetName="<Table V - Item 1 - Value column>"
$vnetAddrPrefix="<Table V - Item 4 - Value column>"
$gwSubnetPrefix="<Table S - Item 1 - Subnet address space column>"
$SubnetName="<Table S - Item 2 - Subnet name column>"
$SubnetPrefix="<Table S - Item 2 - Subnet address space column>"
$dnsServers=@( "<Table D - Item 1 - DNS server IP address column>", "<Table D - Item 2 - DNS server IP address column>" )
$locShortName=(Get-AzResourceGroup -Name $rgName).Location

# Create the Azure virtual network and a network security group that allows incoming remote desktop connections to the subnet that is hosting virtual machines
$gatewaySubnet=New-AzVirtualNetworkSubnetConfig -Name "GatewaySubnet" -AddressPrefix $gwSubnetPrefix
$vmSubnet=New-AzVirtualNetworkSubnetConfig -Name $SubnetName -AddressPrefix $SubnetPrefix
New-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName -Location $locName -AddressPrefix $vnetAddrPrefix -Subnet $gatewaySubnet,$vmSubnet -DNSServer $dnsServers
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName -Location $locShortName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name $vnetName
$nsg=Get-AzNetworkSecurityGroup -Name $SubnetName -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name $SubnetName -AddressPrefix $SubnetPrefix -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
```

Voici la configuration finale.
  
![Le réseau virtuel n’est pas encore connecté au réseau local.](../media/54a37782-a6cc-4d48-b38d-73e128b44a82.png)
  
Utilisez ces commandes pour créer les passerelles pour la connexion VPN de site à site.
  
```powershell
# Fill in the variables from previous values and from Tables V and L
$vnetName="<Table V - Item 1 - Value column>"
$localGatewayIP="<Table V - Item 3 - Value column>"
$localNetworkPrefix=@( <comma-separated, double-quote enclosed list of the local network address prefixes from Table L, example: "10.1.0.0/24", "10.2.0.0/24"> )
$vnetConnectionKey="<Table V - Item 5 - Value column>"
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
# Attach a virtual network gateway to a public IP address and the gateway subnet
$publicGatewayVipName="PublicIPAddress"
$vnetGatewayIpConfigName="PublicIPConfig"
New-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$publicGatewayVip=Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName
$vnetGatewayIpConfig=New-AzVirtualNetworkGatewayIpConfig -Name $vnetGatewayIpConfigName -PublicIpAddressId $publicGatewayVip.Id -SubnetId $vnet.Subnets[0].Id
# Create the Azure gateway
$vnetGatewayName="AzureGateway"
$vnetGateway=New-AzVirtualNetworkGateway -Name $vnetGatewayName -ResourceGroupName $rgName -Location $locName -GatewayType Vpn -VpnType RouteBased -IpConfigurations $vnetGatewayIpConfig
# Create the gateway for the local network
$localGatewayName="LocalNetGateway"
$localGateway=New-AzLocalNetworkGateway -Name $localGatewayName -ResourceGroupName $rgName -Location $locName -GatewayIpAddress $localGatewayIP -AddressPrefix $localNetworkPrefix
# Create the Azure virtual network VPN connection
$vnetConnectionName="S2SConnection"
$vnetConnection=New-AzVirtualNetworkGatewayConnection -Name $vnetConnectionName -ResourceGroupName $rgName -Location $locName -ConnectionType IPsec -SharedKey $vnetConnectionKey -VirtualNetworkGateway1 $vnetGateway -LocalNetworkGateway2 $localGateway
```

Voici la configuration finale.
  
![Le réseau virtuel dispose maintenant d’une passerelle.](../media/82dd66b2-a4b7-48f6-a89b-cfdd94630980.png)
  
Next, configure your on-premises VPN device to connect to the Azure VPN gateway. For more information, see [About VPN Devices for site-to-site Azure Virtual Network connections](/azure/vpn-gateway/vpn-gateway-about-vpn-devices).
  
Pour configurer votre périphérique VPN, vous avez besoin des éléments suivants :
  
- L’adresse IPv4 publique de la passerelle VPN Azure pour votre réseau virtuel. Utilisez la commande **Get-AzPublicIpAddress -Name $vnetGatewayIpConfigName -ResourceGroupName $rgName** pour afficher cette adresse.
    
- La clé prépartagée IPsec pour la connexion VPN de site à site (Tableau V - Élément 5 - colonne Valeur).
    
Voici la configuration finale.
  
![Le réseau virtuel est désormais connecté au réseau local.](../media/6379c423-4f22-4453-941b-7ff32484a0a5.png)
  
### <a name="phase-3-optional-add-virtual-machines"></a>Phase 3 (facultative) : ajouter des machines virtuelles

Create the virtual machines you need in Azure. For more information, see [Create a Windows virtual machine with the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098).
  
Utilisez les paramètres suivants :
  
- Dans l’onglet **De base**, sélectionnez le même abonnement et le même groupe de ressources que votre réseau virtuel. Vous en aurez besoin ultérieurement pour vous connecter à la machine virtuelle. Dans la section **Détails de l’instance**, sélectionnez la taille de machine virtuelle appropriée. Enregistrez le nom d’utilisateur du compte administrateur et le mot de passe dans un emplacement sécurisé. 
    
- Dans l’onglet **Mise en réseau**, sélectionnez le nom de votre réseau virtuel et le sous-réseau pour l’hébergement de machines virtuelles (pas GatewaySubnet). Tous les autres paramètres conservent leurs valeurs par défaut.
    
Verify that your virtual machine is using DNS correctly by checking your internal DNS to ensure that Address (A) records were added for you new virtual machine. To access the Internet, your Azure virtual machines must be configured to use your on-premises network's proxy server. Contact your network administrator for additional configuration steps to perform on the server.
  
Voici la configuration finale.
  
![Le réseau virtuel héberge maintenant des machines virtuelles qui sont accessibles à partir du réseau local.](../media/86ab63a6-bfae-4f75-8470-bd40dff123ac.png)
  
## <a name="next-step"></a>Étape suivante
  
[Déployer la synchronisation d’annuaires Microsoft 365 dans Microsoft Azure](deploy-microsoft-365-directory-synchronization-dirsync-in-microsoft-azure.md)