---
title: Identité fédérée pour votre environnement de test Microsoft 365
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 05/26/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
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
ms.openlocfilehash: 0fb8c55f5b7291cdc6bcec636981a9d31015e723
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487683"
---
# <a name="federated-identity-for-your-microsoft-365-test-environment"></a>Identité fédérée pour votre environnement de test Microsoft 365

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

Microsoft 365 prend en charge l’identité fédérée. Cela signifie qu’au lieu d’effectuer la validation des informations d’identification, Microsoft 365 renvoie l’utilisateur qui se connecte à un serveur d’authentification fédérée approuvé par Microsoft 365. Si les informations d’identification de l’utilisateur sont correctes, le serveur d’authentification fédérée émet un jeton de sécurité que le client envoie ensuite à Microsoft 365 comme preuve d’authentification. L’identité fédérée autorise le déchargement et la montée en charge de l’authentification pour un abonnement Microsoft 365, ainsi que l’authentification avancée et les scénarios de sécurité.
  
Cet article explique comment configurer l’authentification fédérée pour votre environnement de test Microsoft 365, en procédant comme suit :

![L’authentification fédérée pour l’environnement de test Microsoft 365](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement à la version d’évaluation ou de production de Microsoft 365 E5.
    
- Un intranet d’organisation simplifié connecté à Internet, composé de cinq machines virtuelles sur un sous-réseau d’un réseau virtuel Azure (DC1, APP1, CLIENT1, ADFS1 et PROXY1). Azure AD Connect s’exécute sur APP1 pour synchroniser la liste des comptes dans le domaine des services de domaine Active Directory avec Microsoft 365. PROXY1 reçoit les demandes d’authentification entrantes. ADFS1 valide les informations d’identification avec DC1 et émet des jetons de sécurité.
    
La configuration de cet environnement de test implique cinq phases :
- [Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365](#phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment)
- [Phase 2 : Création du serveur AD FS](#phase-2-create-the-ad-fs-server)
- [Phase 3 : création du serveur proxy web (PROXY1)](#phase-3-create-the-web-proxy-server)
- [Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1](#phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1)
- [Phase 5: configuration de Microsoft 365 pour l’identité fédérée](#phase-5-configure-microsoft-365-for-federated-identity)
    
> [!NOTE]
> Vous ne pouvez pas configurer cet environnement de test avec un abonnement d’évaluation Azure.
  
## <a name="phase-1-configure-password-hash-synchronization-for-your-microsoft-365-test-environment"></a>Étape 1 : Configuration de la synchronisation de hachage de mot de passe pour votre environnement de test Microsoft 365

Suivez les instructions de la [synchronisation de hachage de mot de passe pour Microsoft 365](password-hash-sync-m365-ent-test-environment.md). La configuration obtenue se présente comme suit :
  
![Environnement de test de l’entreprise simulée avec la synchronisation de hachage de mot de passe](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase1.png)
  
Cette configuration se compose des éléments suivants : 
  
- Un abonnement d’évaluation ou payant Microsoft 365 E5.
- Un intranet d’organisation simplifié connecté à Internet, constitué des machines virtuelles DC1, APP1 et CLIENT1 sur un sous-réseau d’un réseau virtuel Azure. Azure AD Connect s’exécute sur APP1 pour synchroniser régulièrement le domaine des services de domaine Active Directory (AD DS) TESTLAB vers le client Azure AD de vos abonnements Microsoft 365.

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

La configuration obtenue se présente comme suit :
  
![Le serveur AD FS ajouté à la synchronisation d’annuaire pour l’environnement de test Microsoft 365](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase2.png)
  
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
  
Ensuite, ajoutez une règle au groupe de sécurité réseau pour le sous-réseau CorpNet afin d’autoriser le trafic entrant non sollicité provenant d’Internet vers l’adresse IP privée PROXY1's et le port TCP 443. Exécutez ces commandes dans l’invite de commande Azure PowerShell sur votre ordinateur local.
  
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
Ces commandes créent un enregistrement DNS A interne de sorte que les machines virtuelles sur le réseau virtuel Azure puissent résoudre le nom de domaine complet du service de Fédération interne en adresse IP privée ADFS1's.
  
La configuration obtenue se présente comme suit :
  
![Le serveur proxy d’application web ajouté à la synchronisation d’annuaire pour l’environnement de test Microsoft 365](../media/federated-identity-for-your-microsoft-365-dev-test-environment/federated-tlg-phase3.png)
  
## <a name="phase-4-create-a-self-signed-certificate-and-configure-adfs1-and-proxy1"></a>Phase 4 : création d’un certificat auto-signé et configuration d’ADFS1 et de PROXY1

Au cours de cette phase, vous créez un certificat numérique auto-signé pour votre nom de domaine complet du service FS (Federation Service) et vous configurez ADFS1 et PROXY1 en tant que batterie de serveurs AD FS.
  
Tout d’abord, utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle DC1 à l’aide des informations d’identification de CORP\\User1, puis ouvrez une invite de commande Windows PowerShell de niveau administrateur.
  
Ensuite, créez un compte de service AD FS avec cette commande à l’invite de commandes Windows PowerShell sur DC1 :
  
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
  
1. Sélectionnez **Démarrer**, entrez **mmc.exe**, puis appuyez sur **entrée**.
    
2. Sélectionnez **fichier**  >  **Ajouter/supprimer un composant logiciel enfichable**.
    
3. Dans **Ajouter ou supprimer des composants logiciels enfichables**, double-cliquez sur **certificats** dans la liste des composants logiciels enfichables disponibles, sélectionnez **compte d’ordinateur**, puis cliquez sur **suivant**.
    
4. Dans **Sélectionner un ordinateur**, sélectionnez **Terminer**, puis cliquez sur **OK**.
    
5. Dans le volet d’arborescence, ouvrez **Certificats (ordinateur local) > Personnel > Certificats**.
    
6. Sélectionnez et maintenez (ou cliquez avec le bouton droit) le certificat avec votre nom de domaine complet du service de Fédération, sélectionnez **toutes les tâches**, puis **Exporter**.
    
7. Sur la page d' **Accueil** , sélectionnez **suivant**.
    
8. Sur la page **Exporter la clé privée** , sélectionnez **Oui**, puis **suivant**.
    
9. Sur la page **format de fichier d’exportation** , sélectionnez **exporter toutes les propriétés étendues**, puis **suivant**.
    
10. Sur la page **sécurité** , sélectionnez **mot** de passe et saisissez un mot de passe dans **mot** de passe et confirmer le **mot de passe.**
    
11. Sur la page **fichier à exporter** , sélectionnez **Parcourir**.
    
12. Accédez au dossier **C : \\ certs** , entrez **SSL** dans **nom de fichier**, puis sélectionnez **Enregistrer.**
    
13. Sur la page **fichier à exporter** , sélectionnez **suivant**.
    
14. Sur la page **fin de l’Assistant Exportation du certificat** , sélectionnez **Terminer**. Lorsque vous y êtes invité, sélectionnez **OK**.
    
Ensuite, installez le service AD FS avec cette commande à l’invite de commande Windows PowerShell sur ADFS1 :
  
```powershell
Install-WindowsFeature ADFS-Federation -IncludeManagementTools
```

Attendez la fin de l’installation.
  
Ensuite, configurez le service AD FS en suivant ces étapes :
  
1. Sélectionnez **Démarrer**, puis sélectionnez l’icône **Gestionnaire de serveur** .
    
2. Dans le volet d’arborescence du gestionnaire de serveur, sélectionnez **AD FS**.
    
3. Dans la barre d’outils située en haut de la page, sélectionnez le symbole d’avertissement orange, puis sélectionnez **configurer le service de Fédération sur ce serveur**.
    
4. Sur la page d' **Accueil** de l’Assistant Configuration des services de fédération Active Directory (AD FS), sélectionnez **suivant**.
    
5. Sur la page **connexion à AD DS** , sélectionnez **suivant**.
    
6. Sur la page **Spécifier les propriétés de service** :
    
  - Pour **certificat SSL**, sélectionnez la flèche vers le bas, puis sélectionnez le certificat portant le nom de votre nom de domaine complet du service de Fédération.
    
  - Dans **nom complet du service de Fédération**, entrez le nom de votre organisation fictive.
    
  - Sélectionnez **Suivant**.
    
7. Sur la page **spécifier le compte de service** , sélectionnez **Sélectionner** pour le nom du **compte**.
    
8. Dans **Sélectionner l’utilisateur ou le compte de service**, entrez **ADFS-service**, sélectionnez **vérifier les noms**, puis cliquez sur **OK**.
    
9. Dans **mot de passe du compte**, entrez le mot de passe du compte ADFS-Service, puis cliquez sur **suivant**.
    
10. Sur la page **spécifier la base de données de configuration** , sélectionnez **suivant**.
    
11. Sur la page **examiner les options** , sélectionnez **suivant**.
    
12. Sur la page **vérifications des conditions préalables** , sélectionnez **configurer**.

13. Sur la page **résultats** , sélectionnez **Fermer**.
    
14. Sélectionnez **Démarrer**, sélectionnez l’icône alimentation, sélectionnez **redémarrer**, puis **Continuer**.
    
À partir du [portail Azure](https://portal.azure.com), connectez-vous à PROXY1 avec les informations d’identification du compte CORP\\User1.
  
Ensuite, suivez ces étapes pour installer le certificat auto-signé sur **PROXY1 et APP1**.
  
1. Sélectionnez **Démarrer**, entrez **mmc.exe**, puis appuyez sur **entrée**.
    
2. Sélectionnez **fichier > ajouter/supprimer un composant logiciel enfichable**.
    
3. Dans **Ajouter ou supprimer des composants logiciels enfichables**, double-cliquez sur **certificats** dans la liste des composants logiciels enfichables disponibles, sélectionnez **compte d’ordinateur**, puis cliquez sur **suivant**.
    
4. Dans **Sélectionner un ordinateur**, sélectionnez **Terminer**, puis cliquez sur **OK**.
    
5. Dans le volet de l’arborescence, ouvrez certificats personnels **(ordinateur local)**  >  **Personal**  >  **Certificates**.
    
6. Sélectionnez (ou cliquez avec le bouton droit) **personnel**, sélectionnez **toutes les tâches**, puis **Importer**.
    
7. Sur la page d' **Accueil** , sélectionnez **suivant**.
    
8. Sur la page **fichier à importer** , entrez ** \\ \\ adfs1 \\ certs \\ SSL. pfx**, puis cliquez sur **suivant**.
    
9. Sur la page **protection de clé privée** , saisissez le mot de passe du certificat dans **mot de passe**, puis cliquez sur **suivant.**
    
10. Sur la page **magasin de certificats** , sélectionnez **suivant.**
    
11. Sur la page **terminé** , sélectionnez **Terminer**.
    
12. Sur la page **magasin de certificats** , sélectionnez **suivant**.
    
13. Lorsque vous y êtes invité, sélectionnez **OK**.
    
14. Dans le volet de l’arborescence, sélectionnez **certificats**.
    
15. Sélectionnez (ou cliquez avec le bouton droit) le certificat, puis sélectionnez **copier**.
    
16. Dans le volet d’arborescence, ouvrez certificats d' **autorités de certification racines de confiance**  >  **Certificates**.
    
17. Déplacez le pointeur de la souris en dessous de la liste des certificats installés, sélectionnez et maintenez (ou cliquez avec le bouton droit), puis sélectionnez **coller**.
    
Ouvrez une invite de commande PowerShell de niveau administrateur et exécutez les commandes suivantes :
  
```powershell
Install-WindowsFeature Web-Application-Proxy -IncludeManagementTools
```

Attendez la fin de l’installation.
  
Suivez ces étapes pour configurer le service de proxy d’application web de manière à ce qu’il utilise ADFS1 comme serveur de fédération :
  
1. Sélectionnez **Démarrer**, puis gestionnaire de **serveur**.
    
2. Dans le volet de l’arborescence, sélectionnez **accès à distance**.
    
3. Dans la barre d’outils située en haut de la page, sélectionnez le symbole d’avertissement orange, puis sélectionnez **ouvrir l’Assistant proxy d’application Web**.
    
4. Sur la page d' **Accueil** de l’Assistant Configuration du proxy d’application Web, sélectionnez **suivant**.
    
5. Sur la page **Serveur de fédération** :
    
  - Dans la zone **nom du service de Fédération** , entrez le nom de domaine complet de votre service de Fédération.
    
  - Dans la zone **nom d’utilisateur** , entrez **Corp \\ utilisateur1**.
    
  - Dans la zone **mot de passe** , entrez le mot de passe du compte utilisateur1.
    
  - Sélectionnez **Suivant**.
    
6. Sur la page **certificat de proxy AD FS** , sélectionnez la flèche vers le bas, sélectionnez le certificat avec votre nom de domaine complet du service de Fédération, puis cliquez sur **suivant**.
    
7. Sur la page **confirmation** , sélectionnez **configurer**.
    
8. Sur la page **résultats** , sélectionnez **Fermer**.
    
## <a name="phase-5-configure-microsoft-365-for-federated-identity"></a>Phase 5: configuration de Microsoft 365 pour l’identité fédérée

Utilisez le [portail Azure](https://portal.azure.com) pour vous connecter à la machine virtuelle APP1 avec les informations d’identification du compte CORP\\User1.
  
Suivez ces étapes pour configurer Azure AD Connect et votre abonnement Microsoft 365 pour l’authentification fédérée :
  
1. Sur le bureau, double-cliquez sur **Azure AD Connect**.
    
2. Sur la page **Bienvenue dans Azure ad Connect** , sélectionnez **configurer**.
    
3. Sur la page **tâches supplémentaires** , sélectionnez **modifier la connexion de l’utilisateur**, puis cliquez sur **suivant**.
    
4. Sur la page **connexion à Azure ad** , entrez le nom et le mot de passe de votre compte d’administrateur général, puis cliquez sur **suivant**.
    
5. Sur la page de connexion de l' **utilisateur** , sélectionnez **Fédération avec AD FS**, puis **suivant**.
    
6. Sur la **page batterie de serveurs AD FS** , sélectionnez **utiliser une batterie de serveurs AD FS existante**, entrez **ADFS1** dans la zone **nom du serveur** , puis cliquez sur **suivant**.
    
7. Lorsque vous êtes invité à fournir les informations d’identification du serveur, entrez les informations d’identification du compte d’entreprise \\ utilisateur1, puis sélectionnez **OK**.
    
8. Sur la page informations d’identification d' **administrateur de domaine** , entrez **Corp \\ utilisateur1** dans la zone **nom d’utilisateur** , entrez le mot de passe du compte dans la zone **mot de passe** , puis cliquez sur **suivant**.
    
9. Sur la page **compte de service AD FS** , entrez **Corp \\ ADFS-service** dans la zone **nom d'** utilisateur du domaine, entrez le mot de passe du compte dans la zone **mot de passe** de l’utilisateur de domaine, puis cliquez sur **suivant**.
    
10. Sur la page **domaine Azure ad** , dans **domaine**, sélectionnez le nom du domaine que vous avez précédemment créé et ajouté à votre abonnement à la phase 1, puis cliquez sur **suivant**.
    
11. Sur la page **prêt à configurer** , sélectionnez **configurer**.
    
12. Sur la page **installation terminée** , sélectionnez **vérifier**.
    
    Des messages indiquant que la configuration intranet et Internet ont été vérifiés doivent s’afficher.
    
13. Sur la page **installation terminée** , sélectionnez **quitter**.
    
Pour vérifier que l’authentification fédérée fonctionne, procédez comme suit :
  
1. Ouvrez une nouvelle instance privée de votre navigateur sur votre ordinateur local et accédez à [https://admin.microsoft.com](https://admin.microsoft.com).
    
2. Pour les informations d’identification de connexion, entrez **User1@** \<*the domain created in Phase 1*> .
    
    Par exemple, si votre domaine de test est **testlab.contoso.com**, vous devez entrer « User1@testlab.contoso.com ». Appuyez sur la touche de **tabulation** ou autorisez Microsoft 365 à vous rediriger automatiquement.
    
    Une page **Votre connexion n’est pas privée** devrait s’afficher. Vous constatez que vous avez installé un certificat auto-signé sur ADFS1 que votre ordinateur de bureau ne peut pas valider. Dans un déploiement de production d’authentification fédérée, vous utiliseriez un certificat provenant d’une autorité de certification approuvée et vos utilisateurs ne verraient pas cette page.
    
3. Sur la page **votre connexion n’est pas privée** , sélectionnez **avancé**, puis sélectionnez **passer à \<*your federation service FQDN*> **. 
    
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

Lorsque vous êtes prêt à déployer l’authentification fédérée prête pour la production et la haute disponibilité pour Microsoft 365 dans Azure, consultez la rubrique [Deploy High Availability Federated Authentication for microsoft 365 in Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md).
  
