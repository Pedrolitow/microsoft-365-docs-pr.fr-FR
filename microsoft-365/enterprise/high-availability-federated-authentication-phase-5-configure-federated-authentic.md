---
title: Authentification fédérée à haute disponibilité Phase 5 Configurer l’authentification fédérée pour Microsoft 365
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 11/25/2019
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- scotvorg
- Ent_O365
f1.keywords:
- CSH
ms.custom: Ent_Solutions
ms.assetid: 0f1dbf52-5bff-44cc-a264-1b48641af98f
description: 'Résumé : Configurer Azure AD Connect pour votre authentification fédérée haute disponibilité pour Microsoft 365 dans Microsoft Azure.'
ms.openlocfilehash: b97dd8a14e046786443c2479767f02cf5a336db2
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68178820"
---
# <a name="high-availability-federated-authentication-phase-5-configure-federated-authentication-for-microsoft-365"></a>Phase 5 de l’authentification fédérée à haute disponibilité : configurer l’authentification fédérée pour Microsoft 365

Dans cette dernière phase de déploiement de l’authentification fédérée à haute disponibilité pour Microsoft 365 dans les services d’infrastructure Azure, vous obtenez et installez un certificat émis par une autorité de certification publique, vérifiez votre configuration, puis installez et exécutez Azure AD Connect sur le serveur de synchronisation d’annuaires. Azure AD Connect configure votre abonnement Microsoft 365 et vos Services ADFS (AD FS) et serveurs proxy d’application web pour l’authentification fédérée.
  
Consultez [Déployer l’authentification fédérée haute disponibilité pour Microsoft 365 dans Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md) pour toutes les phases.
  
## <a name="get-a-public-certificate-and-copy-it-to-the-directory-synchronization-server"></a>Obtenir un certificat public et le copier sur le serveur de synchronisation d’annuaires

Obtenez auprès d’une autorité de certification publique un certificat numérique avec les propriétés suivantes :
  
- Un certificat X.509 approprié pour créer des connexions SSL.
    
- La propriété étendue d’autre nom de sujet (Subject Alternative Name, SAN) est définie sur le nom de domaine complet du service de fédération (exemple : fs.contoso.com).
    
- Le certificat doit contenir la clé privée et être stocké au format PFX.
    
Additionally, your organization computers and devices must trust the public certification authority that is issuing the digital certificate. This trust is established by having a root certificate from the public certification authority installed in the trusted root certification authorities store on your computers and devices. Computers running Microsoft Windows typically have a set of these types of certificates installed from commonly-used certification authorities. If the root certificate from your public certification authority is not already installed, you must deploy this to the computers and devices of your organization.
  
Pour plus d'informations sur les certificats requis pour l'authentification fédérée, consultez la rubrique [Configuration requise pour l'installation et la configuration de la fédération](/azure/active-directory/connect/active-directory-aadconnect-prerequisites#prerequisites-for-federation-installation-and-configuration).
  
Lorsque vous recevez le certificat, copiez-le dans un dossier sur le lecteur C: du serveur de synchronisation d’annuaires. Par exemple, nommez le fichier SSL.pfx et stockez-le dans le dossier C:\\Certs sur le serveur de synchronisation d’annuaires.
  
## <a name="verify-your-configuration"></a>Vérifier votre configuration

Vous devez maintenant être prêt à configurer Azure AD Connect et l’authentification fédérée pour Microsoft 365. Pour vous en assurer, utilisez la liste de vérification suivante :
  
- Le domaine public de votre organisation est ajouté à votre abonnement Microsoft 365.
    
- Les comptes d’utilisateur Microsoft 365 de votre organisation sont configurés pour le nom de domaine public de votre organisation et peuvent se connecter avec succès.
    
- Vous avez déterminé le nom de domaine complet d’un service de fédération à partir de votre nom de domaine public.
    
- Un enregistrement DNS A public au nom de domaine complet de votre service de fédération pointe vers l’adresse IP publique de l’équilibreur de charge Azure connecté à Internet pour les serveurs proxy d’application web.
    
- Un enregistrement DNS A privé au nom de domaine complet de votre service de fédération pointe vers l’adresse IP privée de l’équilibreur de charge Azure interne pour les serveurs AD FS.
    
- Un certificat numérique d’autorité de certification public adapté aux connexions SSL avec le san défini sur votre nom de domaine complet de service de fédération est un fichier PFX stocké sur votre serveur de synchronisation d’annuaires.
    
- Le certificat racine de l'autorité de certification publique est installé dans la banque Autorités de certification racines de confiance de vos ordinateurs et appareils.
    
Voici un exemple pour l’organisation Contoso :
  
**Exemple de configuration pour une infrastructure d'authentification fédérée haute disponibilité dans Azure**

![Exemple de configuration de l’infrastructure d’authentification fédérée Microsoft 365 à haute disponibilité dans Azure.](../media/ac1a6a0d-0156-4407-9336-6e4cd6db8633.png)
  
## <a name="run-azure-ad-connect-to-configure-federated-authentication"></a>Exécutez Azure AD Connect pour configurer l’authentification fédérée

L’outil Azure AD Connect configure les serveurs AD FS, les serveurs proxy d’application web et Microsoft 365 pour l’authentification fédérée en procédant comme suit :
  
1. Créez une connexion bureau à distance à votre serveur de synchronisation d’annuaires avec un compte de domaine disposant de privilèges d’administrateur local.
    
2. À partir du bureau du serveur de synchronisation d’annuaires, ouvrez Internet Explorer et accédez à [https://aka.ms/aadconnect](https://aka.ms/aadconnect).
    
3. Sur la page de **Microsoft Azure Active Directory Connect**, cliquez sur **Télécharger**, puis cliquez sur **Exécuter**.
    
4. Sur la page **Bienvenue dans Azure AD Connect**, cliquez sur **J'accepte**, puis sur **Continuer**.
    
5. Sur la page **Configuration rapide**, cliquez sur **Personnaliser**.
    
6. Sur la page **Installer les composants nécessaires**, cliquez sur **Installer**.
    
7. Sur la page **Connexion utilisateur**, cliquez sur **Fédération avec AD FS**, puis sur **Suivant**.
    
8. Dans la page **Se connecter à Azure AD** , tapez le nom et le mot de passe d’un **administrateur Azure AD DC** ou d’un compte **d’administrateur général** pour votre abonnement Microsoft 365, puis cliquez sur **Suivant**.
    
9. Dans la page **Connecter vos répertoires**, vérifiez que votre forêt Active Directory local Domain Services (AD DS) est sélectionnée dans **la forêt**, tapez le nom et le mot de passe d’un compte d’administrateur de domaine, cliquez sur **Ajouter un répertoire**, puis cliquez sur **Suivant**.
    
10. Sur la page **Configuration la connexion à Azure AD**, cliquez sur **Suivant**.
    
11. Sur la page **Filtrage par domaine ou unité d'organisation**, cliquez sur **Suivant**.
    
12. Sur la page **Identification de manière unique de vos utilisateurs**, cliquez sur **Suivant**.
    
13. Sur la page **Filtrer les utilisateurs et appareils**, cliquez sur **Suivant**.
    
14. Sur la page **Fonctionnalités facultatives**, cliquez sur **Suivant**.
    
15. Sur la page **Batterie de serveurs AD FS**, cliquez sur **Configurer une nouvelle batterie AD FS**.
    
16. Cliquez sur **Parcourir** et spécifiez l'emplacement et le nom du certificat SSL de l''autorité de certification publique.
    
17. Lorsque vous y êtes invité, entrez le mot de passe du certificat, puis cliquez sur **OK**.
    
18. Vérifiez que le **nom de sujet** et le **nom du service de fédération** sont définis sur le nom de domaine complet de votre service de fédération, puis cliquez sur **Suivant**.
    
19. Sur la page **Serveurs AD FS**, entrez le nom de votre premier serveur AD FS (Tableau M - Élément 4 - Colonne Nom de machine virtuelle), puis cliquez sur **Ajouter**.
    
20. Entrez le nom de votre deuxième serveur AD FS deuxième (Tableau M - élément 5 - colonne Nom de machine virtuelle), cliquez sur **Ajouter**, puis sur **Suivant**.
    
21. Sur la page **Serveurs proxy d'application Web**, entrez le nom de votre premier serveur proxy d'application Web (Tableau M - Élément 6 - Colonne Nom de machine virtuelle), puis cliquez sur **Ajouter**.
    
22. Entrez le nom de votre deuxième serveur proxy d'application web (Tableau M - élément 7 - colonne Nom de machine virtuelle), cliquez sur **Ajouter**, puis sur **Suivant**.
    
23. Sur la page **Informations d'identification d'administrateur de domaine**, saisissez le nom d'utilisateur et le mot de passe d'un compte d'administrateur de domaine, puis cliquez sur **Suivant**.
    
24. Sur la page **Compte de service AD DS**, saisissez le nom d'utilisateur et le mot de passe d'un compte d'administrateur d'entreprise, puis cliquez sur **Suivant**.
    
25. Sur la page **Domaine Azure AD**, sous **Domaine**, sélectionnez le nom de domaine DNS de votre organisation, puis sur cliquez sur **Suivant**.
    
26. Sur la page **Prêt à configurer**, cliquez sur **Installer**.
    
27. On the **Installation complete** page, click **Verify**. You should see two messages indicating that both the intranet and Internet configuration was successfully verified.
    
  - Le message intranet doit répertorier l’adresse IP privée de l’équilibreur de charge Azure interne pour vos serveurs AD FS.
    
  - Le message Internet doit répertorier l’adresse IP publique de l’équilibreur de charge Azure connecté à Internet pour vos serveurs proxy d’application web.
    
28. Sur la page **Installation terminée**, cliquez sur **Quitter**.
    
Voici la configuration finale, avec les noms d’espace réservé pour les serveurs.
  
**Phase 5 : Configuration finale d'une infrastructure d'authentification fédérée haute disponibilité dans Azure**

![Configuration finale de l’infrastructure d’authentification fédérée Microsoft 365 à haute disponibilité dans Azure.](../media/c5da470a-f2aa-489a-a050-df09b4d641df.png)
  
Votre infrastructure d’authentification fédérée à haute disponibilité pour Microsoft 365 dans Azure est terminée.
  
## <a name="see-also"></a>Voir aussi

[Déployer une authentification fédérée haute disponibilité pour Microsoft 365 dans Azure](deploy-high-availability-federated-authentication-for-microsoft-365-in-azure.md)
  
[Identité fédérée pour votre environnement de développement/test Microsoft 365](federated-identity-for-your-microsoft-365-dev-test-environment.md)
  
[Centre de solutions et d'architecture Microsoft 365](../solutions/index.yml)

[Identité fédérée pour Microsoft 365](https://support.office.com/article/Understanding-Office-365-identity-and-Azure-Active-Directory-06a189e7-5ec6-4af2-94bf-a22ea225a7a9#bk_federated)
