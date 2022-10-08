---
title: Configuration de base légère
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 05/17/2022
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom:
- Ent_TLGs
- seo-marvel-apr2020
- admindeeplinkMAC
ms.assetid: 6f916a77-301c-4be2-b407-6cec4d80df76
description: Utilisez ce guide de laboratoire de test pour créer un environnement de test léger pour tester Microsoft 365 pour les entreprises.
ms.openlocfilehash: e9f3e3194317c8e2a4aaeba0bb23fdc70d3ac45e
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68208763"
---
# <a name="the-lightweight-base-configuration"></a>Configuration de base légère

*Ce guide de laboratoire de test peut être utilisé pour Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Cet article explique comment créer un environnement simplifié avec un abonnement Microsoft 365 E5 et un ordinateur exécutant Windows 10 Entreprise.

![Environnement de test Léger Microsoft 3656 Entreprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

La création d’un environnement de test léger implique cinq phases :

- [Phase 1 : Créer votre abonnement Microsoft 365 E5](#phase-1-create-your-microsoft-365-e5-subscription)
- [Phase 2 : configuration de votre abonnement d’évaluation Office 365](#phase-2-configure-your-office-365-trial-subscription)
- [Phase 3 : Ajoutez un abonnement d’évaluation Microsoft 365 E5.](#phase-3-add-a-microsoft-365-e5-trial-subscription)
- [Phase 4 : Création d’un ordinateur Windows 10 Entreprise](#phase-4-create-a-windows-10-enterprise-computer)
- [Phase 5 : Association de votre ordinateur Windows 10 à Azure AD](#phase-5-join-your-windows-10-computer-to-azure-ad)

Utilisez l’environnement résultant pour tester les fonctionnalités de [Microsoft 365 pour les entreprises](https://www.microsoft.com/microsoft-365/enterprise).

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)
  
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile des guides de laboratoire de test Microsoft 365 pour entreprise, consultez [Microsoft 365 for enterprise Test Lab Guide Stack](../downloads/Microsoft365EnterpriseTLGStack.pdf).

>[!NOTE]
>Nous vous recommandons d’imprimer cet article afin de consigner les informations dont vous aurez besoin dans cet environnement au cours des 30 jours de votre abonnement à la version d’évaluation Office 365. Vous pouvez facilement étendre l’abonnement d’évaluation pour une période supplémentaire de 30 jours. Pour un environnement de développement/test permanent, créez un nouvel abonnement payant avec un client Azure AD séparé et un nombre réduit de licences.

## <a name="phase-1-create-your-microsoft-365-e5-subscription"></a>Phase 1 : Créer votre abonnement Microsoft 365 E5

Nous commençons par un abonnement d’essai Microsoft 365 E5, puis nous y ajoutons l’abonnement Microsoft 365 E5.

>[!NOTE]
>Nous vous recommandons de créer un abonnement d’essai de Office 365 afin que votre environnement de test dispose d’un locataire Azure AD distinct de tous les abonnements payants dont vous disposez actuellement. Cette séparation signifie que vous pouvez ajouter et supprimer des utilisateurs et des groupes dans le locataire de test sans affecter vos abonnements de production.

Pour démarrer votre abonnement d’évaluation Microsoft 365 E5, vous avez besoin d’un nom d’entreprise fictif et d’un nouveau compte Microsoft.
  
1. We recommend that you use a variant of the company name Contoso for your company name, which is a fictitious company used in Microsoft sample content, but it isn't required. Record your fictitious company name here: ![Ligne.](../media/Common-Images/TableLine.png)

2. To sign up for a new Microsoft account, go to [https://outlook.com](https://outlook.com) and create an account with a new email account and address. You will use this account to sign up for Office 365.

    - Enregistrez le prénom et le nom de famille utilisés pour votre nouveau compte ici : ![Ligne.](../media/Common-Images/TableLine.png)

    - Enregistrez l’adresse du nouveau compte de messagerie ici : ![Ligne.](../media/Common-Images/TableLine.png)@outlook.com

### <a name="sign-up-for-an-office-365-e5-trial-subscription"></a>Inscription à un abonnement d’évaluation Office 365 E5

1. Dans votre navigateur, accédez à [https://aka.ms/e5trial](https://aka.ms/e5trial).

2. À l’étape 1 de la page **Merci d’avoir choisi Office 365 E5**, entrez votre nouvelle adresse de compte de messagerie.
3. À l’étape 2 du processus d’abonnement de piste, entrez les informations demandées, puis effectuez la vérification.
4. À l’étape 3, entrez un nom d’organisation, puis un nom de compte qui sera l’administrateur général de l’abonnement.
5. À l’étape 4, enregistrer l’URL de la page de connexion ici (sélectionnez-la et copiez-la) : ![Ligne.](../media/Common-Images/TableLine.png)
6. Enregistrez l’ID d’utilisateur ici : ![Line.](../media/Common-Images/TableLine.png). onmicrosoft.com  
   Enregistrez le mot de passe que vous avez entré dans un emplacement sécurisé.
   Cette valeur correspond au **nom de l’administrateur général**.
7. Sélectionnez **Atteindre le programme d’installation**.
8. Dans Office 365 E5 configuration, **sélectionnez Continuer à utiliser *votre organisation.onmicrosoft.com* pour l’e-mail et la connexion**, puis **sélectionnez Quitter et continuer ultérieurement**.

Le Centre d’administration Microsoft 365 doit s’afficher.

## <a name="phase-2-configure-your-office-365-trial-subscription"></a>Phase 2 : configuration de votre abonnement d’évaluation Office 365

Durant cette phase, configurez votre abonnement en y ajoutant des utilisateurs supplémentaires et assignez-leur des licences Office 365 E5.
  
Pour vous connecter à votre abonnement avec le module Azure Active Directory PowerShell pour Graph à partir de votre ordinateur, suivez les instructions de [Connexion à Microsoft 365 avec PowerShell](connect-to-microsoft-365-powershell.md#connect-with-the-azure-active-directory-powershell-for-graph-module).

Dans la **boîte de dialogue Windows PowerShell Demande d’informations d’identification**, entrez le nom de l’administrateur général (par exemple, *jdoe@contosotoycompany.onmicrosoft.com*) et le mot de passe.
  
Renseignez le nom de votre organisation (par exemple, *contosotoycompany*), le code de pays à deux caractères de votre emplacement, un mot de passe de compte commun, puis exécutez les commandes suivantes à partir de l’invite PowerShell :

```powershell
$orgName="<organization name>"
$loc="<two-character country code, such as US>"
$commonPW="<common user account password>"
$PasswordProfile=New-Object -TypeName Microsoft.Open.AzureAD.Model.PasswordProfile
$PasswordProfile.Password=$commonPW

$License = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicense
$License.SkuId = (Get-AzureADSubscribedSku | Where-Object -Property SkuPartNumber -Value "ENTERPRISEPREMIUM" -EQ).SkuID
$LicensesToAssign = New-Object -TypeName Microsoft.Open.AzureAD.Model.AssignedLicenses
$LicensesToAssign.AddLicenses = $License

for($i=2;$i -le 4; $i++) {
    $userUPN= "user$($i)@$($orgName).onmicrosoft.com"
    New-AzureADUser -DisplayName "User $($i)" -GivenName User -SurName $i -UserPrincipalName $userUPN -UsageLocation $loc -AccountEnabled $true -PasswordProfile $PasswordProfile -MailNickName "user$($i)"
    $userObjectID = (Get-AzureADUser -SearchString $userupn).ObjectID
    Set-AzureADUserLicense -ObjectId $userObjectID -AssignedLicenses $LicensesToAssign
}
```

> [!NOTE]
> L’utilisation ici d’un mot de passe courant est destinée à l’automatisation et à la simplification de la configuration pour un environnement de test. Bien évidemment, cela est hautement déconseillé pour les abonnements de production.

### <a name="record-key-information-for-future-reference"></a>Enregistrer les informations clés pour future référence

Si vous n’avez pas encore enregistré ces valeurs, enregistrez-les maintenant :
  
- nom Administrateur général : ![Ligne.](../media/Common-Images/TableLine.png).onmicrosoft.com(à partir de l’étape 6 de la phase 1)

    Enregistrez également le mot de passe de ce compte dans un emplacement sécurisé.

- Nom de l’organisation bénéficiant de l’abonnement à la version d’évaluation : ![Ligne.](../media/Common-Images/TableLine.png) (à partir de l’étape 4 de la phase 1)

- Pour répertorier les comptes pour Utilisateur 2, Utilisateur 3, Utilisateur 4 et Utilisateur 5, exécutez la commande suivante à partir de l’invite Module Windows Azure Active Directory pour Windows PowerShell :

  ```powershell
  Get-AzureADUser | Sort UserPrincipalName | Select UserPrincipalName
  ```

    Enregistrez les noms de compte ici :

  - Nom du compte de l’utilisateur 2 : utilisateur2@![Ligne.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - Nom du compte de l’utilisateur 3 : utilisateur3@![Ligne.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - Nom du compte de l’utilisateur 4 : utilisateur4@![Ligne.](../media/Common-Images/TableLine.png).onmicrosoft.com

  - Nom du compte de l’utilisateur 5 : utilisateur5@![Ligne.](../media/Common-Images/TableLine.png).onmicrosoft.com

    Enregistrez également les mots de passe communs de ces comptes dans un emplacement sécurisé.

### <a name="using-an-office-365-test-environment"></a>Utilisation d’un environnement de test Office 365

Si vous n’avez besoin que d’un environnement de test Office 365, vous n’avez pas besoin de lire le reste de cet article.

Pour obtenir des guides de laboratoire de test supplémentaires qui s’appliquent à la fois à Office 365 et à Microsoft 365, consultez [les guides de laboratoire de test Microsoft 365 pour entreprise](m365-enterprise-test-lab-guides.md).
  
## <a name="phase-3-add-a-microsoft-365-e5-trial-subscription"></a>Phase 3 : Ajoutez un abonnement d’évaluation Microsoft 365 E5.

Dans cette phase, vous vous inscrivez pour l’abonnement d’évaluation Microsoft 365 E5 et l’ajoutez à la même organisation que votre abonnement d’évaluation d’Office 365 E5.
  
Tout d’abord, ajoutez l’abonnement d’évaluation Microsoft 365 E5 et attribuez une licence Microsoft 365 à votre compte d’administrateur général.
  
1. Dans une fenêtre privée de navigateur Internet, utilisez les informations d’identification de votre compte d’administrateur général pour vous connecter au Centre d'administration Microsoft 365 à l’adresse [https://admin.microsoft.com](https://admin.microsoft.com).

2. Dans la page **Centre d'administration Microsoft 365**, dans le volet de navigation de gauche, sélectionnez <a href="https://go.microsoft.com/fwlink/p/?linkid=868433" target="_blank">**Services d’achat**</a> de **facturation** > .

3. Dans la page **Acheter des services**, sélectionnez **Microsoft 365 E5**, puis **sélectionnez Obtenir un essai gratuit**.

4. Dans la page **Microsoft 365 E5 d’évaluation**, décidez de recevoir un SMS ou un appel téléphonique, entrez votre numéro de téléphone, puis sélectionnez **Me texter** ou **m’appeler**. Effectuez la vérification.

5. Dans la page **Confirmer votre commande** , **sélectionnez Essayer maintenant**.

6. Dans la page **De confirmation de commande** , **sélectionnez Continuer**.

7. Dans la Centre d'administration Microsoft 365, sélectionnez **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.

8. Dans **Utilisateurs actifs**, sélectionnez votre compte d’administrateur.

9. Sélectionnez **licences et applications.**

10. Désactivez la licence pour Office 365 Entreprise E5 et activez la licence pour Microsoft 365 E5.

11. Sélectionnez **Enregistrer les modifications**, puis fermez le volet d’informations du compte d’utilisateur.

Ensuite, répétez les étapes 8 et 11 de la procédure précédente pour tous vos autres comptes (Utilisateur2, Utilisateur3, Utilisateur4 et Utilisateur5).
  
> [!NOTE]
> La durée de l’abonnement d’essai Microsoft 365 E5 est de 30 jours. Pour un environnement de test permanent, convertissez cet abonnement en abonnement payant avec un nombre réduit de licences.
  
Votre environnement de test comporte maintenant :
  
- Un abonnement d’évaluation de Microsoft 365 E5.
- Tous vos comptes d’utilisateur appropriés (l’administrateur général ou tous les cinq comptes d’utilisateur) sont activés pour utiliser Microsoft 365 E5.

Votre configuration résultante, qui ajoute Microsoft 365 E5, ressemble à ceci :
  
![Phase 3 de l’environnement de test Microsoft 3656 Entreprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase2.png)
  
## <a name="phase-4-create-a-windows-10-enterprise-computer"></a>Phase 4 : Création d’un ordinateur Windows 10 Entreprise

Au cours de cette phase, vous allez créer un ordinateur autonome exécutant Windows 10 Entreprise sous forme d’un ordinateur physique, d’une machine virtuelle ou d’une machine virtuelle Azure.
  
### <a name="physical-computer"></a>Ordinateur physique

Sur un ordinateur personnel, installez Windows 10 Entreprise. Vous pouvez télécharger la version d’évaluation Windows 10 Entreprise [ici](https://www.microsoft.com/software-download/windows10).
  
### <a name="virtual-machine"></a>Machine virtuelle

Utilisez l’hyperviseur de votre choix pour créer une machine virtuelle, puis installez Windows 10 Entreprise sur celle-ci. Vous pouvez télécharger la version d’évaluation Windows 10 Entreprise [ici](https://www.microsoft.com/software-download/windows10).
  
### <a name="virtual-machine-in-azure"></a>Machine virtuelle dans Azure

To create a Windows 10 virtual machine in Microsoft Azure, ***you must have a Visual Studio-based subscription***, which has access to the image for Windows 10 Enterprise. Other types of Azure subscriptions, such as trial and paid subscriptions, do not have access to this image. For the latest information, see [Use Windows client in Azure for dev/test scenarios](/azure/virtual-machines/windows/client-images).
  
> [!NOTE]
> [!REMARQUE] Les ensembles de commandes suivants utilisent la dernière version d'Azure PowerShell. Reportez-vous à la rubrique relative à la [prise en main des cmdlets Azure PowerShell](/powershell/azureps-cmdlets-docs/). Ces ensembles de commandes créent une machine virtuelle Windows 10 Entreprise nommée WIN10 ainsi que l’intégralité de son infrastructure requise, y compris un groupe de ressources, un compte de stockage et un réseau virtuel. Si vous êtes déjà familiarisé avec les services d’infrastructure Azure, adaptez ces instructions en fonction de votre infrastructure actuellement déployée.
  
Tout d’abord, lancez une invite Microsoft PowerShell.
  
Connectez-vous à votre compte Azure avec cette commande.
  
```powershell
Connect-AzAccount
```

Obtenez le nom de votre abonnement à l’aide de cette commande.
  
```powershell
Get-AzSubscription | Sort Name | Select Name
```

Définissez votre abonnement Azure. Remplacez tout ce qui se trouve entre guillemets, y compris les \< and > caractères, par le nom correct.
  
```powershell
$subscr="<subscription name>"
Get-AzSubscription -SubscriptionName $subscr | Select-AzSubscription
```

Ensuite, créez un nouveau groupe de ressources. Pour déterminer un nom de groupe de ressources unique, utilisez cette commande pour répertorier vos groupes de ressources existants.
  
```powershell
Get-AzResourceGroup | Sort ResourceGroupName | Select ResourceGroupName
```

Créez votre nouveau groupe de ressources avec ces commandes. Remplacez tout ce qui se trouve entre guillemets, y compris les \< and > caractères, par les noms corrects.
  
```powershell
$rgName="<resource group name>"
$locName="<location name, such as West US>"
New-AzResourceGroup -Name $rgName -Location $locName
```

Ensuite, créez un réseau virtuel et la machine virtuelle WIN10 avec ces commandes. Lorsque vous y êtes invité, indiquez le nom et le mot de passe du compte d’administrateur local pour WIN10, et enregistrez ces informations dans un emplacement sécurisé.
  
```powershell
$corpnetSubnet=New-AzVirtualNetworkSubnetConfig -Name Corpnet -AddressPrefix 10.0.0.0/24
New-AzVirtualNetwork -Name "M365Ent-TestLab" -ResourceGroupName $rgName -Location $locName -AddressPrefix 10.0.0.0/8 -Subnet $corpnetSubnet
$rule1=New-AzNetworkSecurityRuleConfig -Name "RDPTraffic" -Description "Allow RDP to all VMs on the subnet" -Access Allow -Protocol Tcp -Direction Inbound -Priority 100 -SourceAddressPrefix Internet -SourcePortRange * -DestinationAddressPrefix * -DestinationPortRange 3389
New-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName -Location $locName -SecurityRules $rule1
$vnet=Get-AzVirtualNetwork -ResourceGroupName $rgName -Name "M365Ent-TestLab"
$nsg=Get-AzNetworkSecurityGroup -Name Corpnet -ResourceGroupName $rgName
Set-AzVirtualNetworkSubnetConfig -VirtualNetwork $vnet -Name Corpnet -AddressPrefix "10.0.0.0/24" -NetworkSecurityGroup $nsg
$vnet | Set-AzVirtualNetwork
$pip=New-AzPublicIpAddress -Name WIN10-PIP -ResourceGroupName $rgName -Location $locName -AllocationMethod Dynamic
$nic=New-AzNetworkInterface -Name WIN10-NIC -ResourceGroupName $rgName -Location $locName -SubnetId $vnet.Subnets[0].Id -PublicIpAddressId $pip.Id
$vm=New-AzVMConfig -VMName WIN10 -VMSize Standard_A2_V2
$cred=Get-Credential -Message "Type the name and password of the local administrator account for WIN10."
$vm=Set-AzVMOperatingSystem -VM $vm -Windows -ComputerName WIN10 -Credential $cred -ProvisionVMAgent -EnableAutoUpdate
$vm=Set-AzVMSourceImage -VM $vm -PublisherName MicrosoftWindowsDesktop -Offer Windows-10 -Skus RS3-Pro -Version "latest"
$vm=Add-AzVMNetworkInterface -VM $vm -Id $nic.Id
$vm=Set-AzVMOSDisk -VM $vm -Name WIN10-TestLab-OSDisk -DiskSizeInGB 128 -CreateOption FromImage
New-AzVM -ResourceGroupName $rgName -Location $locName -VM $vm
```

## <a name="phase-5-join-your-windows-10-computer-to-azure-ad"></a>Phase 5 : Association de votre ordinateur Windows 10 à Azure AD

Lorsque l’ordinateur physique ou la machine virtuelle avec Windows 10 Entreprise est créée, connectez-vous avec un compte d’administrateur local.
  
> [!NOTE]
> Pour une machine virtuelle dans Azure, utilisez  [ces instructions](/azure/virtual-machines/windows/connect-logon) pour vous y connecter.
  
Ensuite, associez l’ordinateur WIN10 au client Azure AD de votre abonnement Microsoft 365 E5.
  
1. Sur le bureau de l’ordinateur WIN10, **sélectionnez Démarrer > Paramètres > Comptes > Accéder à la connexion professionnelle ou scolaire >.**

2. Dans la boîte de dialogue **Configurer un compte professionnel ou scolaire** , **sélectionnez Joindre cet appareil à Azure Active Directory**.

3. Dans le **compte professionnel ou scolaire**, entrez le nom du compte d’administrateur général de votre abonnement Microsoft 365 E5, puis sélectionnez **Suivant**.

4. Dans **Entrer le mot de passe**, entrez le mot de passe de votre compte d’administrateur général, puis sélectionnez **Se connecter**.

5. Lorsque vous êtes invité à vérifier qu’il s’agit de votre organisation, **sélectionnez Joindre**, puis sélectionnez **Terminé**.

6. Fermez la fenêtre Paramètres.

Ensuite, installez Applications Microsoft 365 pour les grandes entreprises sur l’ordinateur WIN10 :
  
1. Ouvrez le navigateur Microsoft Edge et connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec vos informations d’identification de compte d’administrateur général.

2. Sous l’onglet **Accueil de Microsoft Office** , sélectionnez **Installer Office**.

3. Lorsque vous y êtes invité, sélectionnez **Exécuter**, puis **sélectionnez Oui** pour **le contrôle de compte d’utilisateur**.

4. Attendez qu’Office termine l’installation. Lorsque vous voyez **que vous êtes tous définis!**, sélectionnez **Fermer** deux fois.

Votre environnement résultant ressemble à ceci :

![Phase 5 de l’environnement de test Microsoft 3656 Entreprise.](../media/lightweight-base-configuration-microsoft-365-enterprise/Phase4.png)

Cela inclut l’ordinateur WIN10 avec :

- rejoint le client Azure AD de votre abonnement Microsoft 365 E5 ;
- été inscrit en tant que périphérique Azure AD dans Microsoft Intune (EMS) ;
- Applications Microsoft 365 pour les grandes entreprises installé.
  
Vous êtes maintenant prêt à expérimenter d’autres fonctionnalités de [Microsoft 365 pour les entreprises](https://www.microsoft.com/microsoft-365/enterprise).
  
## <a name="next-steps"></a>Étapes suivantes

Découvrez les nouveaux ensembles de guides pour les tests de laboratoire :
  
- [Identité](m365-enterprise-test-lab-guides.md#identity)
- [Gestion des appareils mobiles](m365-enterprise-test-lab-guides.md#mobile-device-management)
- [Protection des informations](m365-enterprise-test-lab-guides.md#information-protection)

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
