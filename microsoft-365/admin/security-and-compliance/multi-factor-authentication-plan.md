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
ms.openlocfilehash: 715baeb0355ab203e890f2c87cf0751eff69e7f8
ms.sourcegitcommit: dbbdeca5a6cd048e1bde9e820a8b8a0d6022c7a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "43503994"
---
# <a name="plan-for-multi-factor-authentication-for-office-365-deployments"></a>Offre pour l'authentification multifacteur des déploiements Office 365

[] L'authentification multifacteur (MFA) est une méthode d'authentification qui requiert l'utilisation de plusieurs méthodes de vérification, et ajoute une deuxième couche de sécurité aux connexions et transactions des utilisateurs. Elle nécessite une étape de vérification supplémentaire avec des informations au-delà du mot de passe du compte d’utilisateur, telles que :
  
- code d'accès généré de façon aléatoire ;
    
- appel téléphonique ;
    
- carte à puce (virtuelle ou physique) ; 
    
- appareil biométrique. 
    
## <a name="mfa-in-office-365"></a>MFA dans Office 365

Office 365 utilise MFA pour une sécurité de connexion supplémentaire et peut être géré pour chaque compte d’utilisateur individuel à partir du centre d’administration Microsoft 365. Office 365 propose le sous-ensemble suivant de fonctionnalités d’authentification multifacteur Azure dans le cadre de votre abonnement : 
  
- Possibilité d’activer et d’appliquer l’authentification multifacteur pour les utilisateurs finaux
    
- utilisation d'une application mobile (en ligne, avec mot de passe à usage unique [OTP]) comme deuxième facteur d'authentification ;
    
- utilisation d'un appel téléphonique comme deuxième facteur d'authentification ;
    
- utilisation d'un SMS comme deuxième facteur d'authentification ;
    
- Les mots de passe d’application pour les clients qui ne sont pas des navigateurs (par exemple, le logiciel de communication Microsoft Lync 2013)
    
- message d'accueil Microsoft par défaut lors des appels téléphonique d'authentification.
    
Pour obtenir la liste complète des fonctionnalités inédites, voir la [comparaison des fonctionnalités de l'authentification multifacteur Azure suivant les versions](https://go.microsoft.com/fwlink/?LinkId=506927). Vous pouvez toujours obtenir l'ensemble complet des fonctionnalités en achetant le service Azure Multi-Factor Authentication. 
  
Vous obtenez un sous-ensemble de fonctionnalités différent selon que vous disposez d’une identité Cloud uniquement ou hybride pour Office 365 ou de l’authentification fédérée avec Active Directory Federation Services (AD FS). 
  
|**Où gérer votre client Office 365 ?** | **Options du deuxième facteur de MFA**|

|:-----|:-----| | Cloud uniquement  <br/> | Authentification multifacteur Azure (appel texte ou téléphone)  <br/> | | Configuration hybride, géré en local  <br/> | Si vous gérez l’identité de l’utilisateur en local, vous disposez des choix suivants :  <br/>  Carte à puce physique ou virtuelle (lors de l’utilisation d’AD FS)  <br/> [Authentification multifacteur Azure](https://go.microsoft.com/fwlink/p/?LinkId=526677) (module pour AD FS)  <br/>  Authentification multifacteur Azure Active Directory (Azure AD)  <br/> |
   
  
L'illustration suivante montre comment les applications pour appareil Office 2013 (sous Windows) mises à jour permettent aux utilisateurs de se connecter en utilisant une authentification multifacteur. 

![Modern authentication for Office 2013 device apps.](../../media/dc37645c-b899-4715-b162-d7653bd0aebd.png)

Les applications d’appareils Office 2013 prennent en charge l’authentification multifacteur via l’utilisation de la [bibliothèque d’authentification Active Directory (Adal)](https://go.microsoft.com/fwlink/p/?LinkId=526684). Azure AD héberge une page web dans via laquelle les utilisateurs peuvent se connecter. Le fournisseur d'identité peut être Azure AD ou un fournisseur d'identité fédéré comme AD FS. Les étapes d'authentification pour des utilisateurs fédérés sont les suivantes :
  
1. Azure AD redirige l'utilisateur vers la page web de connexion hébergée par le fournisseur d'identité de l'enregistrement pour le client Office 365. Le fournisseur d'identité est déterminé par le domaine spécifié dans le nom de connexion de l'utilisateur.
    
2. L'utilisateur se connecte à la page web de connexion sur son appareil. 
    
3. Le fournisseur d'identité renvoie un jeton à Azure AD une fois l'utilisateur correctement connecté.
    
4. Azure AD renvoie un jeton web JSON (JWT) à l'application d'appareil Office, et celle-ci est authentifiée à l'aide d'un JWT auprès d'Office 365. 
    
  
## <a name="requirements-for-office-2013-client-apps"></a>Configuration requise pour les applications clientes Office 2013

Pour activer l'authentification multifacteur pour les applications clientes Office 2013, vous devez disposer des logiciels suivants (version ci-dessous ou version ultérieure), selon que vous disposez d'une [Installations de type Démarrer en un clic](#click-to-run-based-installations) ou d'une [Installations basées sur MSI](#msi-based-installations).
  
Pour déterminer si votre installation d'Office est de type Démarrer en un clic ou basée sur MSI :
  
1. Démarrez Outlook 2013.
    
2. Dans le menu **fichier** , choisissez **compte Office**.
    
3. Pour les installations Démarrer en un clic d'Outlook 2013, l'élément **Options de mise à jour** s'affiche. Pour les installations basées sur MSI, l'élément **Options de mise à jour** ne s'affiche pas. 
    
    ![Comment savoir si votre installation d’Office 2013 est « démarrer en un clic » ou en mode MSI](../../media/1e75143f-9e37-4e0c-9610-43a80771571e.png)

SOR plus d’informations, consultez le [Forum aux questions sur l’article wiki sur l’authentification moderne](https://go.microsoft.com/fwlink/p/?LinkId=530064).
  
### <a name="click-to-run-based-installations"></a>Installations de type Démarrer en un clic

Pour les installations « démarrer en un clic », vous devez disposer des logiciels suivants, dont la version de fichier est indiquée ci-dessous ou une version de fichier ultérieure. Si votre version du fichier n'est pas égale ou supérieure à la version indiquée, mettez-la à jour en suivant les étapes ci-dessous.
  
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

Pour activer l’authentification multifacteur pour votre abonnement Office 365, procédez comme suit :
  
1. Si nécessaire, [activez l’authentification moderne pour Office 2013 sur les appareils Windows](enable-modern-authentication.md).
    
2. Pour l’authentification fédérée, configurez l’authentification multifacteur Azure avec votre service d’annuaire tiers.
    
    Consultez la rubrique [scénarios avancés avec Azure Multi-Factor Authentication et des solutions VPN tierces](https://docs.microsoft.com/azure/active-directory/authentication/howto-mfaserver-nps-vpn) pour obtenir des informations sur des fournisseurs d’identité spécifiques acceptés par ce programme. 
    
3. [Configurez l’authentification multifacteur pour Office 365](set-up-multi-factor-authentication.md).
    
4. Indiquez à vos utilisateurs comment [configurer l’authentification multifacteur pour leur compte d’utilisateur Office 365](https://support.office.com/article/set-up-2-step-verification-for-office-365-ace1d096-61e5-449b-a875-58eb3d74de14). Une fois qu’ils ont configuré leur méthode d’authentification secondaire, leurs futures connexions nécessiteront une authentification multifacteur.
    
> [!IMPORTANT]
> Si vous avez activé vos utilisateurs pour l’authentification multifacteur Azure et qu’ils ont des appareils exécutant Office 2013 qui ne sont pas activés pour l’authentification moderne, ils doivent utiliser des mots de passe d’application. Pour plus d’informations sur les mots de passe d’application et sur le mode d’utilisation des mots de passe, consultez les [mots de passe d’application avec l’authentification Azure Multi_Factor](https://go.microsoft.com/fwlink/p/?LinkId=528178). 
  
## <a name="known-issues"></a>Problèmes connus
  
[Office 2013 et Office 365 ProPlus authentification moderne : éléments à savoir avant l’intégration](https://social.technet.microsoft.com/wiki/contents/articles/30214.office-2013-and-office-365-proplus-modern-authentication-things-to-know-before-onboarding.aspx)
  
 **Résolution des problèmes d'authentification multifacteur Azure :**
  
Voir [résoudre les problèmes liés à l’authentification multifacteur Azure](https://support.microsoft.com/help/2937344/troubleshooting-azure-multi-factor-authentication-issues).
  
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
   

