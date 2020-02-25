---
title: Offre pour l'authentification multifacteur des déploiements Office 365
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 043807b2-21db-4d5c-b430-c8a6dee0e6ba
ROBOTS: NOINDEX, NOFOLLOW
description: Découvrez l’authentification multifacteur dans Office 365 et les étapes que vous devez suivre pour la configurer.
ms.openlocfilehash: c3d5e83b951e4fd4a05cb18408ecb3d26e397cf9
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42254212"
---
# <a name="plan-for-multi-factor-authentication-for-office-365-deployments"></a>Offre pour l'authentification multifacteur des déploiements Office 365

[] L'authentification multifacteur (MFA) est une méthode d'authentification qui requiert l'utilisation de plusieurs méthodes de vérification, et ajoute une deuxième couche de sécurité aux connexions et transactions des utilisateurs. Elle fonctionne en exigeant au moins deux des méthodes de vérification suivantes :
  
- code d'accès généré de façon aléatoire ;
    
- appel téléphonique ;
    
- carte à puce (virtuelle ou physique) ; 
    
- appareil biométrique. 
    
## <a name="multi-factor-authentication-in-office-365"></a>Authentification multifacteur dans Office 365

Office 365 utilise l’authentification multifacteur pour fournir la sécurité supplémentaire et est gérée à partir du centre d’administration Microsoft 365. Office 365 offre le sous-ensemble suivant de fonctionnalités d'authentification multifacteur Azure dans le cadre de l'abonnement : 
  
- possibilité d'activer et d'appliquer l'authentification multifacteur pour des utilisateurs finaux ;
    
- utilisation d'une application mobile (en ligne, avec mot de passe à usage unique [OTP]) comme deuxième facteur d'authentification ;
    
- utilisation d'un appel téléphonique comme deuxième facteur d'authentification ;
    
- utilisation d'un SMS comme deuxième facteur d'authentification ;
    
- mots de passe d'application pour les clients non navigateurs (par exemple, le logiciel de communication Microsoft Lync 2013) ;
    
- message d'accueil Microsoft par défaut lors des appels téléphonique d'authentification.
    
Pour obtenir la liste complète des fonctionnalités inédites, voir la [comparaison des fonctionnalités de l'authentification multifacteur Azure suivant les versions](https://go.microsoft.com/fwlink/?LinkId=506927). Vous pouvez toujours obtenir l'ensemble complet des fonctionnalités en achetant le service Azure Multi-Factor Authentication. 
  
Vous obtenez un sous-ensemble différent de fonctionnalités selon que vous disposez d'un déploiement exclusivement cloud pour Office 365 ou d'une configuration hybride avec authentification unique et services AD FS (Active Directory Federation Services). 
  
|**Où gérez-vous votre client Office 365 ?**|**Options du deuxième facteur d'authentification multifacteur**|
|:-----|:-----|
|Cloud uniquement  <br/> |Authentification multifacteur Azure Active Directory (texte ou un appel téléphonique)  <br/> |
|Configuration hybride, gérée en local  <br/> | Si vous gérez l'identité des utilisateurs localement, vous disposez des choix suivants :  <br/>  Carte à puce physique ou virtuelle (AD FS)  <br/> [Azure MFA](https://go.microsoft.com/fwlink/p/?LinkId=526677) (module pour AD FS)  <br/>  Authentification multifacteur Azure AD  <br/> |
   
  
L'illustration suivante montre comment les applications pour appareil Office 2013 (sous Windows) mises à jour permettent aux utilisateurs de se connecter en utilisant une authentification multifacteur. Les applications pour appareil Office2013 prennent en charge l'authentification multifacteur via l'utilisation de la [bibliothèque d'authentification Active Directory (ADAL)](https://go.microsoft.com/fwlink/p/?LinkId=526684). Azure AD héberge une page web dans via laquelle les utilisateurs peuvent se connecter. Le fournisseur d'identité peut être Azure AD ou un fournisseur d'identité fédéré comme AD FS. Les étapes d'authentification pour des utilisateurs fédérés sont les suivantes :
  
1. Azure AD redirige l'utilisateur vers la page web de connexion hébergée par le fournisseur d'identité de l'enregistrement pour le client Office 365. Le fournisseur d'identité est déterminé par le domaine spécifié dans le nom de connexion de l'utilisateur.
    
2. L'utilisateur se connecte à la page web de connexion sur son appareil. 
    
3. Le fournisseur d'identité renvoie un jeton à Azure AD une fois l'utilisateur correctement connecté.
    
4. Azure AD renvoie un jeton web JSON (JWT) à l'application d'appareil Office, et celle-ci est authentifiée à l'aide d'un JWT auprès d'Office 365. 
    
Cela est détaillé dans la figure suivante :
  
![Modern authentication for Office 2013 device apps.](../media/dc37645c-b899-4715-b162-d7653bd0aebd.png)
  
## <a name="software-requirements"></a>Configuration logicielle requise

Pour activer l'authentification multifacteur pour les applications clientes Office 2013, vous devez disposer des logiciels suivants (version ci-dessous ou version ultérieure), selon que vous disposez d'une [Installations de type Démarrer en un clic](#click-to-run-based-installations) ou d'une [Installations basées sur MSI](#msi-based-installations).
  
Pour déterminer si votre installation d'Office est de type Démarrer en un clic ou basée sur MSI :
  
1. Démarrez Outlook 2013.
    
2. Dans le menu **fichier** , choisissez **compte Office**.
    
3. Pour les installations Démarrer en un clic d'Outlook 2013, l'élément **Options de mise à jour** s'affiche. Pour les installations basées sur MSI, l'élément **Options de mise à jour** ne s'affiche pas. 
    
    ![Graphic that shows how to tell if Office 2013 install is click-to-run or MSI-based](../media/1e75143f-9e37-4e0c-9610-43a80771571e.png)
  
### <a name="click-to-run-based-installations"></a>Installations de type Démarrer en un clic

Pour des installations de type Démarrer en un clic, vous devez disposer des logiciels suivants, dans la version indiquée ou dans une version ultérieure. Si votre version du fichier n'est pas égale ou supérieure à la version indiquée, mettez-la à jour en suivant les étapes ci-dessous.
  
|**Nom de fichier**|**Chemin d'installation sur votre ordinateur**|**Version de fichier**|
|:-----|:-----|:-----|
|MSO. FICHIER  <br/> |C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\MSO.DLL  <br/> |15.0.4753.1001  <br/> |
|CSI. FICHIER  <br/> |CSI.DLL C:\Program Files\Microsoft Office 15\root\office15\csi.dll  <br/> |15.0.4753.1000  <br/> |
|Groove. EXE  <br/> |C:\Program Files\Microsoft Office 15\root\office15\GROOVE.exe  <br/> |15.0.4763.1000  <br/> |
|Outlook. exe  <br/> |C:\Program Files\Microsoft Office 15\root\office15\OUTLOOK.exe  <br/> |15.0.4753.1002  <br/> |
|Adal. FICHIER  <br/> |C:\Program Files\Microsoft Office 15\root\vfs\ProgramFilesCommonx86\Microsoft Shared\OFFICE15\ADAL.DLL  <br/> |1.0.2016.624  <br/> |
|Iexplore. exe  <br/> |C:\Program Files\Internet Explorer  <br/> |variable  <br/> |
   
### <a name="msi-based-installations"></a>Installations basées sur MSI

Pour des installations basées sur MSI, vous devez disposer des logiciels suivants, dans la version indiquée ou dans une version ultérieure. Si votre version du fichier n'est pas égale ou supérieure à la version indiquée, mettez-la à jour en suivant le lien figurant dans la colonne Où obtenir la mise à jour.
  
|**Nom de fichier**|**Chemin d'installation sur votre ordinateur**|**Où obtenir la mise à jour**|**Version**|
|:-----|:-----|:-----|:-----|
|MSO. FICHIER  <br/> |C:\Program Files\Common Files\Microsoft Shared\OFFICE15\MSO.DLL  <br/> |[KB3085480](https://support.microsoft.com/kb/3085480) <br/> |15.0.4753.1001  <br/> |
|CSI. FICHIER  <br/> |C:\Program Files\Common Files\Microsoft Shared\OFFICE15\Csi.dll  <br/> |[KB3085504](https://support.microsoft.com/kb/3085504) <br/> |15.0.4753.1000  <br/> |
|Groove. exe  <br/> |C:\Program Files\Microsoft Office\Office15\GROOVE.EXE  <br/> |[KB3085509](https://support.microsoft.com/kb/3085509) <br/> |15.0.4763.1000  <br/> |
|Outlook. exe  <br/> |C:\Program Files\Microsoft Office\Office15\OUTLOOK.EXE  <br/> |[KB3085495](https://support.microsoft.com/kb/3085495) <br/> |15.0.4753.1002  <br/> |
|Adal. FICHIER  <br/> |C:\Program Files\Common Files\Microsoft Shared\OFFICE15\ADAL.DLL  <br/> |[KB3055000](https://support.microsoft.com/kb/3055000) <br/> |1.0.2016.624  <br/> |
|Iexplore. exe  <br/> |C:\Program Files\Internet Explorer  <br/> |[MS14-052](https://support.microsoft.com/kb/2977629) <br/> |Non applicable  <br/> |
   
## <a name="enable-mfa"></a>Activer l’authentification multifacteur

Pour activer l'authentification multifacteur, vous devez procéder comme suit :
  
1. Activez les clients pour l'authentification moderne :
    
  - [Activez l'authentification moderne pour Office 2013 sur les appareils Windows](enable-modern-authentication.md) . 
    
  - Configurez Azure MFA avec des services d'annuaire tiers.
    
    Consultez les [scénarios avancés avec Azure Multi-Factor Authentication et les solutions VPN tierces](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-nps-vpn) pour obtenir des informations sur des fournisseurs d’identité spécifiques acceptés par ce programme. 
    
2. [Configurer l'authentification multifacteur pour les utilisateurs d'Office 365](set-up-multi-factor-authentication.md) .
    
3. Indiquez aux utilisateurs comment se connecter à l'aide de l'authentification multifacteur : [Se connecter à Office 365 avec la vérification en deux étapes](https://support.office.com/article/2b856342-170a-438e-9a4f-3c092394d3cb.aspx).
    
> [!IMPORTANT]
> Si vous avez activé vos utilisateurs pour l'authentification multifacteur Azure AD, et ceux-ci disposent d'appareils Office 2013 non activés pour l'authentification moderne, ils doivent utiliser des mots de passe d'application sur ces appareils. Pour plus d'informations sur les mots de passe d'application ainsi que quand, où et comment les utiliser, voir ici : [Mots de passe d'application avec l'authentification multifacteur Azure (Azure MFA)](https://go.microsoft.com/fwlink/p/?LinkId=528178). 
  
## <a name="faq"></a>Forum aux questions

[Article wiki du FAQ sur l'authentification moderne dans Office 2013](https://go.microsoft.com/fwlink/p/?LinkId=530064)
  
 **Known issues:**
  
[Authentification moderne Office 2013 et Office 365 ProPlus : Informations à connaître avant l'intégration](https://social.technet.microsoft.com/wiki/contents/articles/30214.office-2013-and-office-365-proplus-modern-authentication-things-to-know-before-onboarding.aspx)
  
 **Résolution des problèmes d'authentification multifacteur Azure :**
  
Voir [Questions fréquentes relatives à Azure Multi-Factor Authentication](https://support.microsoft.com/help/2937344/troubleshooting-azure-multi-factor-authentication-issues).
  
[Comment faire pour résoudre les problèmes de connexion avec l'authentification moderne d'Office 2013 lorsque vous utilisez AD FS](https://support.microsoft.com/kb/3052203/)
  
 **Quand les ID secondaires ne fonctionnent pas :**
  
[Utilisation de PowerShell pour corriger les noms d'utilisateur principal en double](https://go.microsoft.com/fwlink/p/?LinkId=396730)
  
[Script de résolution des noms d'utilisateurs principaux en double](https://go.microsoft.com/fwlink/p/?LinkId=396725)
  
 **Filtrage d'accès client :**
  
[Stratégies d'authentification moderne et de filtrage d'accès client dans Office 2013 et Office 365 ProPlus : Informations à connaître avant l'intégration](https://social.technet.microsoft.com/wiki/contents/articles/30214.office-2013-and-office-365-proplus-modern-authentication-things-to-know-before-onboarding.aspx)
  
 **Quelles applications prennent en charge l'authentification multifacteur ?**
  
|**Windows**|**Mac**|**iOS**|**Téléphone Android**|**Tablette Android**|
|:-----|:-----|:-----|:-----|:-----|
|L'authentification moderne pour Word 2013, Word 2016, Excel 2013, Excel 2016, PowerPoint 2013, PowerPoint 2016, OneNote 2013, OneNote 2016, Project 2013, Project 2016, Visio 2013, Visio 2016, Lync 2013 et Skype Entreprise est prise en charge dans cette version.  <br/> |L'authentification moderne pour Word 2016 pour Mac, Excel 2016 pour Mac et PowerPoint 2016 pour Mac est prise en charge dans cette version.  <br/> |L'authentification moderne pour Word pour iPad, Excel pour iPad et PowerPoint pour iPad est prise en charge dans cette version.  <br/> |L'authentification moderne pour Word pour Android, Excel pour Android et PowerPoint pour Android est prise en charge dans cette version.  <br/> |L'authentification moderne pour Word pour Android, Excel pour Android et PowerPoint pour Android est prise en charge dans cette version.  <br/> |
|L'authentification moderne pour Outlook 2013 et Outlook 2016 est prise en charge dans cette version.  <br/> |L'authentification moderne pour Outlook 2016 pour Mac est prise en charge dans cette version.  <br/> |L'authentification moderne pour Outlook pour iPad est prise en charge dans cette version.  <br/> |||
   

