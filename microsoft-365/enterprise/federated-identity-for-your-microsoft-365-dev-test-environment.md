---
title: Identité fédérée pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom:
- TLG
- Ent_TLGs
ms.assetid: 65a6d687-a16a-4415-9fd5-011ba9c5fd80
description: 'Résumé : Configurez l’authentification fédérée pour votre environnement de test Microsoft 365.'
ms.openlocfilehash: 0214c7778176641c6446106cf92ed173b81b71de
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65101026"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Identité fédérée pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour les Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Microsoft 365 prend en charge l’identité fédérée. Cela signifie qu’au lieu d’effectuer la validation des informations d’identification, Microsoft 365 renvoie l’utilisateur qui se connecte à un serveur d’authentification fédérée approuvé par Microsoft 365. Si les informations d’identification de l’utilisateur sont correctes, le serveur d’authentification fédérée émet un jeton de sécurité que le client envoie ensuite à Microsoft 365 comme preuve d’authentification. L’identité fédérée autorise le déchargement et la montée en charge de l’authentification pour un abonnement Microsoft 365, ainsi que l’authentification avancée et les scénarios de sécurité.
  
Cet article explique comment configurer l’authentification fédérée pour votre environnement de test Microsoft 365, ce qui donne les éléments suivants :

![Authentification fédérée pour Microsoft 365 environnement de test.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement Microsoft 365 E5 d’essai ou de production.
    
- Intranet d’organisation simplifié connecté à Internet, constitué de cinq machines virtuelles sur un sous-réseau d’un réseau virtuel Azure (DC1, APP1, CLIENT1, ADFS1 et PROXY1). Azure AD Connecter s’exécute sur APP1 pour synchroniser la liste des comptes du domaine services de domaine Active Directory avec Microsoft 365. PROXY1 reçoit les demandes d’authentification entrantes. ADFS1 valide les informations d’identification avec DC1 et émet des jetons de sécurité.
    
La configuration de cet environnement de test implique cinq phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Création du serveur AD FS](#phase-2-create-the-ad-fs-server)
- [Phase 3 : création du serveur proxy web (PROXY1)](#phase-3-create-the-web-proxy-server)
- [Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Phase 5: configuration de Microsoft 365 pour l’identité fédérée](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Vous ne pouvez pas configurer cet environnement de test avec un abonnement Azure Trial.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions de [synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). Votre configuration résultante ressemble à ceci :
  
![Entreprise simulée avec environnement de test de synchronisation de hachage de mot de passe.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un Microsoft 365 E5 abonnements d’évaluation ou payants.
- Intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connecter s’exécute sur APP1 pour synchroniser régulièrement le domaine services de domaine Active Directory TESTLAB (AD DS) avec le locataire Azure AD de vos abonnements Microsoft 365.

## <a name="phase-2-create-the-ad-fs-server"></a>Phase 2 : Création du serveur AD FS

Un serveur AD FS fournit une authentification fédérée entre Microsoft 365 et les comptes dans le domaine corp.contoso.com hébergé sur DC1.
  
Pour créer une machine virtuelle Azure pour ADFS1, indiquez le nom de votre abonnement et de votre groupe de ressources, ainsi que l’emplacement Azure de votre configuration de base, puis exécutez ces commandes à l’invite de commandes Azure PowerShell sur votre ordinateur local.
  
```powershell
$subscrName="<your Azure subscription name>"
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
Connect-AzAccount
Select-AzSubscription -SubscriptionName $subscrName
$staticIP="10.0.0.100"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name ADFS1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic = New-AzNetworkInterface -Name ADFS1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName ADFS1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for ADFS1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName ADFS1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "ADFS-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

Ensuite, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle ADFS1 à l’aide du nom de compte d’administrateur local ADFS1 et de votre mot de passe, puis ouvrez une invite de commande Windows PowerShell.
  
Pour vérifier la résolution du nom et la communication réseau entre ADFS1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.
  
Ensuite, associez la machine virtuelle ADFS1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur ADFS1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Votre configuration résultante ressemble à ceci :
  
![Serveur AD FS ajouté à DirSync pour Microsoft 365 environnement de test.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
## <a name="phase-3-create-the-web-proxy-server"></a>Phase 3 : création du serveur proxy web (PROXY1)

PROXY1 permet le traitement proxy des messages d’authentification entre les utilisateurs tentant de s’authentifier et ADFS1.
  
Pour créer une machine virtuelle Azure pour PROXY1, indiquez le nom de votre groupe de ressources et l’emplacement Azure, puis exécutez ces commandes à l’invite de commande Azure PowerShell sur votre ordinateur local.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
$vnetName="TlgBaseConfig-01-VNET"
# NOTE: If you built your simulated intranet with Azure PowerShell, comment the previous line with a "#" and remove the "#" from the next line.
#$vnetName="TestLab"
$staticIP="10.0.0.101"
$locName=(Get-AzResourceGroup -Name $rgName).Location
$vnet=Get-AzVirtualNetwork -Name $vnetName -ResourceGroupName $rgName
$pip = New-AzPublicIpAddress -Name PROXY1-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Static
$nic = New-AzNetworkInterface -Name PROXY1-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id -PrivateIpAddress $staticIP
$vm=New-AzVMConfig -VMName PROXY1 -VMSize Standard_D2_v2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for PROXY1."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName PROXY1 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsServer -Offer WindowsServer -Skus 2016-Datacenter -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name "PROXY1-OS" -DiskSizeInGB 128 -CreateOption FromImage -StorageAccountType "Standard_LRS"
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

> [!NOTE]
> Une adresse IP publique statique est affectée à PROXY1, car vous créez un enregistrement DNS public qui pointe vers celle-ci et elle ne doit pas être modifiée lorsque vous redémarrez la machine virtuelle PROXY1.
  
Ensuite, ajoutez une règle au groupe de sécurité réseau pour le sous-réseau CorpNet afin d’autoriser le trafic entrant non sollicité à partir d’Internet vers l’adresse IP privée proxy1 et le port TCP 443. Exécutez ces commandes dans l’invite de commande Azure PowerShell sur votre ordinateur local.
  
```powershell
$rgName="<the resource group name of your Base Configuration>"
Get-AzNetworkSecurityGroup -Name CorpNet -ResourceGroupName $rgName | Add-AzNetworkSecurityRuleConfig -Name "HTTPS-to-PROXY1" -Description "Allow TCP 443 to PROXY1" -Access "Allow" -Protocol "Tcp" -Direction "Inbound" -Priority 101 -SourceAddressPrefix "Internet" -SourcePortRange "*" -DestinationAddressPrefix "10.0.0.101" -DestinationPortRange "443" | Set-AzNetworkSecurityGroup
```

Ensuite, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle PROXY1 à l’aide du nom de compte d’administrateur local PROXY1 et de votre mot de passe, puis ouvrez une invite de commande Windows PowerShell sur PROXY1.
  
Pour vérifier la résolution du nom et la communication réseau entre PROXY1 et DC1, exécutez la commande **ping dc1.corp.contoso.com** et vérifiez qu’il y a quatre réponses.
  
Ensuite, associez la machine virtuelle PROXY1 au domaine CORP avec ces commandes à l’invite Windows PowerShell sur PROXY1.
  
```powershell
$cred=Get-Credential -UserName "CORP\User1" -Message "Type the User1 account password."
Add-Computer -DomainName corp.contoso.com -Credential $cred
Restart-Computer
```

Affichez l’adresse IP publique de PROXY1 avec ces commandes Azure PowerShell sur votre ordinateur local.
  
```powershell
Write-Host (Get-AzPublicIpaddress -Name "PROXY1-PIP" -ResourceGroup $rgName).IPAddress
```

Ensuite, utilisez votre fournisseur DNS public et créez un enregistrement A DNS public pour **fs.testlab.**\<*your DNS domain name*> qui renvoie l’adresse IP affichée par la commande **Write-Host**. **fs.testlab.**\<*your DNS domain name*> est désigné ci-après en tant que *nom de domaine complet du service FS (Federation Service)*.
  
Ensuite, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle DC1 à l’aide des informations d’identification de CORP\\User1, puis exécutez les commandes suivantes à une invite de commande Windows PowerShell de niveau administrateur :
  
```powershell
Add-DnsServerPrimaryZone -Name corp.contoso.com -ZoneFile corp.contoso.com.dns
Add-DnsServerResourceRecordA -Name "fs" -ZoneName corp.contoso.com -AllowUpdateAny -IPv4Address "10.0.0.100" -TimeToLive 01:00:00
```
Ces commandes créent un enregistrement DNS A interne afin que les machines virtuelles du réseau virtuel Azure puissent résoudre le nom de domaine complet du service de fédération interne en adresse IP privée ADFS1.
  
Votre configuration résultante ressemble à ceci :
  
![Serveur proxy d’application web ajouté à DirSync pour Microsoft 365 environnement de test.](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1

Au cours de cette phase, vous créez un certificat numérique auto-signé pour votre nom de domaine complet du service FS (Federation Service) et vous configurez ADFS1 et PROXY1 en tant que batterie de serveurs AD FS.
  
Tout d’abord, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle DC1 à l’aide des informations d’identification de CORP\\User1, puis ouvrez une invite de commande Windows PowerShell de niveau administrateur.
  
Ensuite, créez un compte de service AD FS avec cette commande à l’invite de commandes Windows PowerShell sur DC1 :
  
```powershell
New-ADUser -SamAccountName ADFS-Service -AccountPassword (read-host "Set user password" -assecurestring) -name "ADFS-Service" -enabled $true -PasswordNeverExpires $true -ChangePasswordAtLogon $false
```
Notez que cette commande vous invite à indiquer le mot de passe du compte. Choisissez un mot de passe fort et enregistrez-le dans un emplacement sécurisé. Vous en aurez besoin pour cette phase et pour la phase 5.
  
Utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle ADFS1 à l’aide des informations d’identification de CORP\\User1. Ouvrez une invite de commande Windows PowerShell de niveau administrateur sur ADFS1, indiquez votre nom de domaine complet du service FS (Federation Service), puis exécutez ces commandes pour créer un certificat auto-signé :
  
```powershell
$fedServiceFQDN="<federation service FQDN>"
New-SelfSignedCertificate -DnsName $fedServiceFQDN -CertStoreLocation "cert:\LocalMachine\My"
New-Item -path c:\Certs -type directory
New-SmbShare -name Certs -path c:\Certs -changeaccess CORP\User1
```

Ensuite, utilisez ces étapes pour enregistrer le nouveau certificat auto-signé en tant que fichier.
  
1. Sélectionnez **Démarrer**, entrez **mmc.exe**, puis **appuyez sur Entrée**.
    
2. Sélectionnez **FileAdd** > **/Remove Snap-in**.
    
3. Dans **Ajouter ou supprimer des composants logiciels enfichables**, double-cliquez sur **Certificats** dans la liste des composants logiciels enfichables disponibles, sélectionnez **Compte d’ordinateur**, puis sélectionnez **Suivant**.
    
4. Dans **Sélectionner un ordinateur**, sélectionnez **Terminer**, puis **sélectionnez OK**.
    
5. Dans le volet d’arborescence, ouvrez **Certificats (ordinateur local) > Personnel > Certificats**.
    
6. Sélectionnez et maintenez enfoncé (ou cliquez avec le bouton droit) le certificat avec votre nom de domaine complet de service de fédération, sélectionnez **Toutes les tâches**, puis sélectionnez **Exporter**.
    
7. Dans la page **d’accueil** , sélectionnez **Suivant**.
    
8. Dans la page **Exporter la clé privée** , sélectionnez **Oui**, puis **Suivant**.
    
9. Dans la page **Exporter le format de fichier** , sélectionnez **Exporter toutes les propriétés étendues**, puis **sélectionnez Suivant**.
    
10. Dans la page **Sécurité** , sélectionnez **Mot de passe** , entrez un mot **de passe dans Mot de passe** et **Confirmez le mot de passe.**
    
11. Dans la page **Fichier à exporter** , **sélectionnez Parcourir**.
    
12. Accédez au dossier **C:\\Certs** , entrez **SSL** dans **le nom de fichier**, puis **sélectionnez Enregistrer.**
    
13. Dans la page **Fichier à exporter** , sélectionnez **Suivant**.
    
14. Dans la page **Fin de l’Assistant Exportation de certificat** , sélectionnez **Terminer**. Lorsque vous y êtes invité, sélectionnez **OK**.
    
Ensuite, installez le service AD FS avec cette commande à l’invite de commande Windows PowerShell sur ADFS1 :
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Attendez la fin de l’installation.
  
Ensuite, configurez le service AD FS en suivant ces étapes :
  
1. Sélectionnez **Démarrer**, puis sélectionnez l’icône **Gestionnaire de serveur**.
    
2. Dans le volet arborescence de Gestionnaire de serveur, sélectionnez **AD FS**.
    
3. Dans la barre d’outils en haut, sélectionnez le symbole d’avertissement orange, puis **sélectionnez Configurer le service de fédération sur ce serveur**.
    
4. Dans la page **d’accueil** de l’Assistant Configuration Services ADFS, sélectionnez **Suivant**.
    
5. Dans la **page Connecter vers AD DS**, sélectionnez **Suivant**.
    
6. Sur la page **Spécifier les propriétés de service** :
    
  - Pour **le certificat SSL**, sélectionnez la flèche vers le bas, puis sélectionnez le certificat portant le nom de votre nom de domaine complet de service de fédération.
    
  - Dans **Le nom complet du service de fédération**, entrez le nom de votre organisation fictive.
    
  - Sélectionnez **Suivant**.
    
7. Dans la page **Spécifier le compte de service** , **sélectionnez Sélectionner** le **nom du compte**.
    
8. Dans **Sélectionner un compte d’utilisateur ou de service**, entrez **ADFS-Service**, **sélectionnez Vérifier les noms**, puis sélectionnez **OK**.
    
9. Dans **Le mot de passe du compte**, entrez le mot de passe du compte ADFS-Service, puis sélectionnez **Suivant**.
    
10. Dans la page **Spécifier la base de données de configuration** , sélectionnez **Suivant**.
    
11. Dans la page **Options de révision** , sélectionnez **Suivant**.
    
12. Dans la page **Vérifications des conditions préalables** , **sélectionnez Configurer**.

13. Dans la page **Résultats** , sélectionnez **Fermer**.
    
14. Sélectionnez **Démarrer**, sélectionnez l’icône d’alimentation, **redémarrez**, puis **sélectionnez Continuer**.
    
À partir du [portail Azure](https://portal.azure.com), connectez-vous à PROXY1 avec les informations d’identification du compte CORP\\User1.
  
Ensuite, suivez ces étapes pour installer le certificat auto-signé sur **PROXY1 et APP1**.
  
1. Sélectionnez **Démarrer**, entrez **mmc.exe**, puis **appuyez sur Entrée**.
    
2. Sélectionnez **Fichier > Ajouter/Supprimer un composant logiciel enfichable**.
    
3. Dans **Ajouter ou supprimer des composants logiciels enfichables**, double-cliquez sur **Certificats** dans la liste des composants logiciels enfichables disponibles, sélectionnez **Compte d’ordinateur**, puis sélectionnez **Suivant**.
    
4. Dans **Sélectionner un ordinateur**, sélectionnez **Terminer**, puis **sélectionnez OK**.
    
5. Dans le volet d’arborescence, ouvrez **Certificats (ordinateur local)** > **PersonalCertificates** > .
    
6. Sélectionnez Et maintenez (ou cliquez avec le bouton droit) **Personnel**, sélectionnez **Toutes les tâches**, puis sélectionnez **Importer**.
    
7. Dans la page **d’accueil** , sélectionnez **Suivant**.
    
8. Dans la page **Fichier à importer**, entrez **\\\\adfs1certsssl.pfx\\\\**, puis sélectionnez **Suivant**.
    
9. Dans la page **Protection de clé privée** , entrez le mot de passe du certificat dans **Mot de passe**, puis sélectionnez **Suivant.**
    
10. Dans la page **Magasin de certificats** , sélectionnez **Suivant.**
    
11. Dans la page **Fin** , sélectionnez **Terminer**.
    
12. Dans la page **Magasin de certificats** , sélectionnez **Suivant**.
    
13. Lorsque vous y êtes invité, sélectionnez **OK**.
    
14. Dans le volet d’arborescence, sélectionnez **Certificats**.
    
15. Sélectionnez et maintenez le certificat enfoncé (ou cliquez avec le bouton droit), puis sélectionnez **Copier**.
    
16. Dans le volet d’arborescence, ouvrez **Trusted Root Certification** **AuthoritiesCertificates** > .
    
17. Déplacez le pointeur de la souris sous la liste des certificats installés, sélectionnez et maintenez la touche enfoncée (ou cliquez avec le bouton droit), puis sélectionnez **Coller**.
    
Ouvrez une invite de commande PowerShell de niveau administrateur et exécutez les commandes suivantes :
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Attendez la fin de l’installation.
  
Suivez ces étapes pour configurer le service de proxy d’application web de manière à ce qu’il utilise ADFS1 comme serveur de fédération :
  
1. Sélectionnez **Démarrer**, puis **sélectionnez Gestionnaire de serveur**.
    
2. Dans le volet d’arborescence, sélectionnez **Accès à distance**.
    
3. Dans la barre d’outils en haut, sélectionnez le symbole d’avertissement orange, puis sélectionnez **Ouvrir l’Assistant Proxy d'application Web**.
    
4. Dans la page **d’accueil** de l’Assistant Configuration du Proxy d'application Web, sélectionnez **Suivant**.
    
5. Sur la page **Serveur de fédération** :
    
  - Dans la zone **Nom du service de fédération** , entrez le nom de domaine complet de votre service de fédération.
    
  - Dans la zone **Nom d’utilisateur**, entrez **CORPUser1\\**.
    
  - Dans la zone **Mot de passe** , entrez le mot de passe du compte User1.
    
  - Sélectionnez **Suivant**.
    
6. Dans la page **Certificat proxy AD FS** , sélectionnez la flèche vers le bas, sélectionnez le certificat avec votre nom de domaine complet de service de fédération, puis **sélectionnez Suivant**.
    
7. Dans la page **Confirmation** , **sélectionnez Configurer**.
    
8. Dans la page **Résultats** , sélectionnez **Fermer**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Phase 5: configuration de Microsoft 365 pour l’identité fédérée

Utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle APP1 avec les informations d’identification du compte CORP\\User1.
  
Suivez ces étapes pour configurer Azure AD Connect et votre abonnement Microsoft 365 pour l’authentification fédérée :
  
1. Sur le bureau, double-cliquez sur **Azure AD Connect**.
    
2. Dans la page **Bienvenue dans Azure AD Connecter**, **sélectionnez Configurer**.
    
3. Dans la page **Tâches supplémentaires** , **sélectionnez Modifier la connexion de l’utilisateur**, puis **sélectionnez Suivant**.
    
4. Dans la **Connecter de Azure AD** page, entrez le nom et le mot de passe de votre compte d’administrateur général, puis sélectionnez **Suivant**.
    
5. Dans la page **de connexion de l’utilisateur** , sélectionnez **Fédération avec AD FS**, puis **Suivant**.
    
6. Dans la page **de la batterie de serveurs AD FS** , **sélectionnez Utiliser une batterie de serveurs AD FS existante**, entrez **ADFS1** dans la zone **Nom du serveur** , puis sélectionnez **Suivant**.
    
7. Lorsque vous êtes invité à entrer les informations d’identification du serveur, entrez les informations d’identification du compte CORPUser1\\, puis sélectionnez **OK**.
    
8. Dans la page Informations d’identification de **l’administrateur de domaine**, entrez **CORPUser1\\** dans la zone **Nom d’utilisateur**, entrez le mot de passe du compte dans la zone **Mot de passe**, puis sélectionnez **Suivant**.
    
9. Dans la page **du compte de service AD FS**, entrez **CORPADFS-Service\\** dans la zone **Nom d’utilisateur du domaine**, entrez le mot de passe du compte dans la zone **Mot de passe de l’utilisateur de domaine**, puis sélectionnez **Suivant**.
    
10. Dans la page **domaine Azure AD**, dans **Domaine**, sélectionnez le nom du domaine que vous avez créé et ajouté à votre abonnement dans la phase 1, puis sélectionnez **Suivant**.
    
11. Dans la page **Prêt à configurer** , **sélectionnez Configurer**.
    
12. Dans la page **Installation terminée** , **sélectionnez Vérifier**.
    
    Vous devriez voir des messages indiquant que la configuration intranet et Internet a été vérifiée.
    
13. Dans la page **Installation terminée** , sélectionnez **Quitter**.
    
Pour vérifier que l’authentification fédérée fonctionne, procédez comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur sur votre ordinateur local et accédez à [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Pour les informations d’identification de connexion, entrez **user1@**\<*the domain created in Phase 1*>.
    
    Par exemple, si votre domaine de test est **testlab.contoso.com**, vous entrez « user1@testlab.contoso.com ». Appuyez **sur Tab** ou autorisez Microsoft 365 à vous rediriger automatiquement.
    
    Une page **Votre connexion n’est pas privée** devrait s’afficher. Vous voyez cela, car vous avez installé un certificat auto-signé sur ADFS1 que votre ordinateur de bureau ne peut pas valider. Dans un déploiement de production d’authentification fédérée, vous utiliseriez un certificat provenant d’une autorité de certification approuvée et vos utilisateurs ne verraient pas cette page.
    
3. Sur la page **Votre connexion n’est pas privée** , sélectionnez **Avancé**, puis **sélectionnez Continuer vers \<*your federation service FQDN*>**. 
    
4. Sur la page contenant le nom de votre organisation fictive, connectez-vous avec les éléments suivants :
    
  - **CORP\\User1** pour le nom ;
    
  - le mot de passe du compte User1.
    
    Vous devez voir la **page d’accueil Microsoft Office**.
    
Cette procédure montre que votre abonnement d’évaluation est fédéré avec le domaine corp.contoso.com AD DS hébergé sur DC1. Voici les principes de base du processus d’authentification :
  
1. Lorsque vous utilisez le domaine fédéré que vous avez créé à la phase 1 dans le nom de compte de connexion, Microsoft 365 redirige votre navigateur vers le nom de domaine complet de votre service FS (Federation Service) et PROXY1.
    
2. PROXY1 envoie la page de connexion de l’entreprise fictive à votre ordinateur local.
    
3. Lorsque vous envoyez CORP\\User1 et le mot de passe à PROXY1, il les transfère à ADFS1.
    
4. ADFS1 valide CORP\\User1 et le mot de passe avec DC1 et envoie un jeton de sécurité à votre ordinateur local.
    
5. Votre ordinateur local envoie le jeton de sécurité à Microsoft 365.
    
6. Microsoft 365 confirme que le jeton de sécurité a été créé par ADFS1 et autorise l’accès.
    
Votre abonnement d’évaluation est désormais configuré avec l’authentification fédérée. Vous pouvez utiliser cet environnement de développement/test pour les scénarios d’authentification avancés.
  
## <a name="next-step"></a>Étape suivante

Lorsque vous êtes prêt à déployer une authentification fédérée haute disponibilité prête pour la production pour Microsoft 365 dans Azure, consultez [Déployer l’authentification fédérée haute disponibilité pour Microsoft 365 dans Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
