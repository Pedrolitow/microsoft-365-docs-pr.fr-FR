---
title: Déployer la synchronisation d’annuaires Microsoft 365 dans Microsoft Azure
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/05/2018
audience: ITPro
ms.topic: conceptual
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
ms.assetid: b8464818-4325-4a56-b022-5af1dad2aa8b
description: Découvrez comment déployer Azure AD Connect sur une machine virtuelle dans Azure pour synchroniser des comptes entre votre annuaire local et le locataire Azure AD.
ms.openlocfilehash: a4eee43c00ebae3d489943d20e212c02c03a09ff
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68185642"
---
# <a name="deploy-microsoft-365-directory-synchronization-in-microsoft-azure"></a>Déployer la synchronisation d’annuaires Microsoft 365 dans Microsoft Azure

Azure Active Directory (Azure AD) Connect (anciennement l’outil de synchronisation d’annuaires, l’outil de synchronisation d’annuaires ou l’outil DirSync.exe) est une application que vous installez sur un serveur joint à un domaine pour synchroniser vos utilisateurs Active Directory local Domain Services (AD DS) avec le locataire Azure AD de votre abonnement Microsoft 365. Microsoft 365 utilise Azure AD pour son service d’annuaire. Votre abonnement Microsoft 365 inclut un locataire Azure AD. Ce client peut également être utilisé pour la gestion des identités de votre organisation avec d’autres charges de travail de cloud, y compris d’autres applications SaaS et des applications dans Azure.

Vous pouvez installer Azure AD Connect sur un serveur local, mais vous pouvez également l’installer sur une machine virtuelle dans Azure pour les raisons suivantes :
  
- Vous pouvez mettre en service et configurer les serveurs cloud plus rapidement, les rendant ainsi disponibles plus tôt pour vos utilisateurs.
- Azure offre une meilleure disponibilité de site avec moins d'efforts.
- Vous pouvez réduire le nombre de serveurs locaux de votre organisation.

Cette solution exige une connectivité entre votre réseau local et votre réseau virtuel Azure. Pour plus d’informations, reportez-vous à [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md). 
  
> [!NOTE]
> Cet article décrit la synchronisation d'un domaine unique dans une forêt unique. Azure AD Connect synchronise tous les domaines AD DS de votre forêt Active Directory avec Microsoft 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Microsoft 365, consultez La synchronisation d’annuaires [à forêts multiples avec un scénario de Sign-On unique](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
## <a name="overview-of-deploying-microsoft-365-directory-synchronization-in-azure"></a>Vue d’ensemble du déploiement de la synchronisation d’annuaires Microsoft 365 dans Azure

Le diagramme suivant montre Azure AD Connect s’exécutant sur une machine virtuelle dans Azure (le serveur de synchronisation d’annuaires) qui synchronise une forêt AD DS locale avec un abonnement Microsoft 365.
  
![Outil Azure AD Connect sur une machine virtuelle dans Azure synchronisant des comptes locaux avec le locataire Azure AD d’un abonnement Microsoft 365 avec le flux de trafic.](../media/CP-DirSyncOverview.png)
  
Dans le schéma, il existe deux réseaux connectés par une connexion VPN ou ExpressRoute de site à site. Il existe un réseau local où se trouvent les contrôleurs de domaine AD DS, ainsi qu’un réseau virtuel Azure avec un serveur de synchronisation d’annuaires, qui est une machine virtuelle exécutant [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594). Il existe deux principaux flux de trafic provenant du serveur de synchronisation d’annuaires :
  
-  Azure AD Connect interroge un contrôleur de domaine sur le réseau local concernant les modifications apportées aux comptes et aux mots de passe.
-  Azure AD Connect envoie les modifications apportées aux comptes et mots de passe à l’instance Azure AD de votre abonnement Microsoft 365. Étant donné que le serveur de synchronisation d’annuaires se trouve dans une partie étendue de votre réseau local, ces modifications sont envoyées via le serveur proxy du réseau local.
    
> [!NOTE]
> Cette solution décrit la synchronisation d’un domaine Active Directory unique dans une forêt Active Directory unique. Azure AD Connect synchronise tous les domaines Active Directory de votre forêt Active Directory avec Microsoft 365. Si vous avez plusieurs forêts Active Directory à synchroniser avec Microsoft 365, consultez La synchronisation d’annuaires [à forêts multiples avec un scénario de Sign-On unique](/azure/active-directory/hybrid/whatis-hybrid-identity). 
  
Le déploiement de cette solution comporte deux étapes principales :
  
1. Create an Azure virtual network and establish a site-to-site VPN connection to your on-premises network. For more information, see [Connect an on-premises network to a Microsoft Azure virtual network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
    
2. Installez [Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594) sur une machine virtuelle jointe à un domaine dans Azure, puis synchronisez le service AD DS local avec Microsoft 365. Pour cela, vous devez :
    
    Création d'un Ordinateur virtuel Azure pour exécuter Azure AD Connect.
    
    Installation et configuration d'[Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594).
    
    La configuration d’Azure AD Connect nécessite les informations d’identification (nom d’utilisateur et mot de passe) d’un compte d’administrateur Azure AD et d’un compte d’administrateur d’entreprise AD DS. Azure AD Connect s’exécute immédiatement et en continu pour synchroniser la forêt AD DS locale avec Microsoft 365.
    
Avant de déployer cette solution en production, vous pouvez utiliser les instructions de [la configuration de base d’entreprise simulée](simulated-ent-base-configuration-microsoft-365-enterprise.md) pour configurer cette configuration en tant que preuve de concept, pour des démonstrations ou pour l’expérimentation.
  
> [!IMPORTANT]
> Une fois la configuration d’Azure AD Connect terminée, les informations d’identification de compte d’administrateur d’entreprise AD DS ne sont pas enregistrées. 
  
> [!NOTE]
> Cette solution décrit la synchronisation d’une forêt AD DS unique avec Microsoft 365. La topologie décrite dans cet article ne représente qu'un seul moyen de mettre en œuvre cette solution. La topologie de votre organisation peut-être différer en fonction de vos besoins réseau unique et les considérations sur la sécurité. 
  
## <a name="plan-for-hosting-a-directory-sync-server-for-microsoft-365-in-azure"></a>Planifier l’hébergement d’un serveur de synchronisation d’annuaires pour Microsoft 365 dans Azure
<a name="PlanningVirtual"> </a>

### <a name="prerequisites"></a>Conditions préalables

Avant de commencer, passez en revue les conditions préalables suivantes pour cette solution :
  
- Examinez le contenu de planification associé dans[Planifier votre réseau virtuel Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#plan-your-azure-virtual-network). 
    
- Veillez à respecter toutes les[conditions préalables](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#prerequisites) relatives à la configuration du réseau virtuel Azure.
    
- Disposez d’un abonnement Microsoft 365 qui inclut la fonctionnalité d’intégration Active Directory. Pour plus d’informations sur les abonnements Microsoft 365, accédez à la [page des abonnements Microsoft 365](https://products.office.com/compare-all-microsoft-office-products?tab=2).
    
- Provisionnez une machine virtuelle Azure qui exécute Azure AD Connect pour synchroniser votre forêt AD DS locale avec Microsoft 365.
    
    Vous devez disposer des informations d’identification (noms et mots de passe) d’un compte d’administrateur d’entreprise AD DS et d’un compte d’administrateur Active Directory Azure.
    
### <a name="solution-architecture-design-assumptions"></a>Hypothèses en matière de conception de l’architecture de la solution

La liste suivante décrit les choix de conception effectués pour cette solution.
  
- Cette solution utilise un réseau virtuel Azure unique avec une connexion VPN de site à site. Le réseau virtuel Azure héberge un sous-réseau unique qui possède un serveur, le serveur de synchronisation d’annuaires qui exécute Azure AD Connect. 
    
- Sur le réseau local, un contrôleur de domaine et des serveurs DNS existent.
    
- Azure AD Connect effectue une synchronisation de hachage de mot de passe au lieu de l’authentification unique. Vous n’êtes pas obligé de déployer une infrastructure Services ADFS (AD FS). Pour en savoir plus sur la synchronisation de hachage de mot de passe et les options d’authentification unique, consultez [Choisir la méthode d’authentification appropriée pour votre solution d’identité hybride Azure Active Directory](/azure/active-directory/hybrid/choose-ad-authn).
    
Vous pouvez envisager d’autres choix de conception lorsque vous déployez cette solution dans votre environnement. Elles incluent notamment les éléments suivants :
  
- Si un réseau virtuel Azure existant comporte des serveurs DNS, déterminez si vous voulez que votre serveur de synchronisation d’annuaires les utilise pour la résolution de noms à la place des serveurs DNS sur le réseau local.
    
- If there are domain controllers in an existing Azure virtual network, determine whether configuring Active Directory Sites and Services may be a better option for you. The directory sync server can query the domain controllers in the Azure virtual network for changes in accounts and passwords instead of domain controllers on the on-premises network.
    
## <a name="deployment-roadmap"></a>Feuille de route de déploiement

Le déploiement d'Azure AD Connect sur une machine virtuelle dans Azure consiste en trois phases :
  
- Phase 1 : créer et configurer le réseau virtuel Azure
    
- Phase 2 : créer et configurer les machines virtuelles Azure
    
- Phase 3 : installer et configurer Azure AD Connect
    
Après le déploiement, vous devez également attribuer des emplacements et des licences pour les nouveaux comptes d’utilisateur dans Microsoft 365.


### <a name="phase-1-create-and-configure-the-azure-virtual-network"></a>Phase 1 : créer et configurer le réseau virtuel Azure

Pour créer et configurer le réseau virtuel Azure, effectuez la [phase 1 en préparant votre réseau local](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-1-prepare-your-on-premises-network) et la [phase 2 en créant le réseau virtuel entre différents locaux dans Azure](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md#phase-2-create-the-cross-premises-virtual-network-in-azure) décrites dans la feuille de route de déploiement de l’article [Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md).
  
Voici la configuration finale.
  
![Phase 1 du serveur de synchronisation d’annuaires pour Microsoft 365 hébergé dans Azure.](../media/aab6a9a4-eb78-4d85-9b96-711e6de420d7.png)
  
Cette illustration montre un réseau local connecté à un réseau virtuel Azure via une connexion VPN ou ExpressRoute de site à site.
  
### <a name="phase-2-create-and-configure-the-azure-virtual-machine"></a>Phase 2 : créer et configurer les machines virtuelles Azure

Create the virtual machine in Azure using the instructions [Create your first Windows virtual machine in the Azure portal](https://go.microsoft.com/fwlink/p/?LinkId=393098). Use the following settings:
  
- On the **Basics** pane, select the same subscription, location, and resource group as your virtual network. Record the user name and password in a secure location. You will need these later to connect to the virtual machine.
    
- Dans le volet **Choisir une taille**, choisissez la taille **A2 Standard**.
    
- On the **Settings** pane, in the **Storage** section, select the **Standard** storage type. In the **Network** section, select the name of your virtual network and the subnet for hosting the directory sync server (not the GatewaySubnet). Leave all other settings at their default values.
    
Vérifiez que votre serveur de synchronisation d’annuaires utilise correctement DNS en vérifiant votre DNS interne pour vous assurer qu’un enregistrement d’adresse (A) a été ajouté pour la machine virtuelle avec son adresse IP. 
  
Use the instructions in [Connect to the virtual machine and sign on](/azure/virtual-machines/windows/connect-logon) to connect to the directory sync server with a Remote Desktop Connection. After signing in, join the virtual machine to the on-premises AD DS domain.
  
For Azure AD Connect to gain access to Internet resources, you must configure the directory sync server to use the on-premises network's proxy server. You should contact your network administrator for any additional configuration steps to perform.
  
Voici la configuration finale.
  
![Phase 2 du serveur de synchronisation d’annuaires pour Microsoft 365 hébergé dans Azure.](../media/9d8c9349-a207-4828-9b2b-826fe9c06af3.png)
  
Cette illustration montre la machine virtuelle du serveur de synchronisation d’annuaires dans le réseau virtuel Azure.
  
### <a name="phase-3-install-and-configure-azure-ad-connect"></a>Phase 3 : installer et configurer Azure AD Connect

Procédez comme suit :
  
1. Connect to the directory sync server using a Remote Desktop Connection with an AD DS domain account that has local administrator privileges. See [Connect to the virtual machine and sign on](/azure/virtual-machines/windows/connect-logon).
    
2. À partir du serveur de synchronisation d’annuaires, ouvrez l’article [Configurer la synchronisation d’annuaires pour Microsoft 365](set-up-directory-synchronization.md) et suivez les instructions pour la synchronisation d’annuaires avec la synchronisation de hachage de mot de passe.
    
> [!CAUTION]
> Le programme d’installation crée le compte **AAD_xxxxxxxxxxxx** dans l’unité d’organisation (UO) Utilisateurs locaux. Ne déplacez pas ou ne supprimez pas ce compte, ou la synchronisation échouera.
  
Voici la configuration finale.
  
![Phase 3 du serveur de synchronisation d’annuaires pour Microsoft 365 hébergé dans Azure.](../media/3f692b62-b77c-4877-abee-83c7edffa922.png)
  
Cette illustration montre le serveur de synchronisation d’annuaires avec Azure AD Connect dans le réseau virtuel Azure entre différents locaux.
  
### <a name="assign-locations-and-licenses-to-users-in-microsoft-365"></a>Attribuer des emplacements et des licences aux utilisateurs dans Microsoft 365

Azure AD Connect ajoute des comptes à votre abonnement Microsoft 365 à partir du service AD DS local, mais pour que les utilisateurs se connectent à Microsoft 365 et utilisent ses services, les comptes doivent être configurés avec un emplacement et des licences. Utilisez ces étapes pour ajouter l’emplacement et activer les licences pour les comptes d’utilisateur appropriés :
  
1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com), puis cliquez sur **Administration**.
    
2. Dans le volet de navigation de gauche, cliquez sur **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.
3. Dans la liste des comptes d’utilisateur, sélectionnez la case à cocher en regard de l’utilisateur que vous souhaitez activer.
    
4. Sur la page de l'utilisateur, cliquez sur **Modifier** pour **Licences de produits**.
    
5. Sur la page **Licences de produit**, sélectionnez un emplacement pour l'utilisateur pour **Emplacement**, puis activez les licences appropriées pour l'utilisateur.
    
6. Lorsque vous avez terminé, cliquez sur **Enregistrer**, puis sur **Fermer** deux fois.
    
7. Revenez à l’étape 3 pour d’autres utilisateurs.
    
## <a name="see-also"></a>Voir aussi

[Centre de solutions et d'architecture Microsoft 365](../solutions/index.yml)
  
[Connecter un réseau local à Microsoft Azure Virtual Network](connect-an-on-premises-network-to-a-microsoft-azure-virtual-network.md)

[Télécharger Azure AD Connect](https://www.microsoft.com/download/details.aspx?id=47594)
  
[Configurer la synchronisation d’annuaires pour Microsoft 365](set-up-directory-synchronization.md)
