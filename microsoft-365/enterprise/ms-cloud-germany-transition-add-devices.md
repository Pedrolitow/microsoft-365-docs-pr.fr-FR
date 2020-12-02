---
title: Informations supplémentaires sur l’appareil pour la migration à partir de Microsoft Cloud Deutschland
ms.author: andyber
author: andybergen
manager: laurawi
ms.date: 12/01/2020
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- CSH
ms.custom:
- Ent_TLGs
description: 'Résumé : informations supplémentaires sur les services lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) vers les services Office 365 dans la nouvelle région de centre de données allemande.'
ms.openlocfilehash: da05a3c2eb6a8d579c53d403a1ef575c389eda12
ms.sourcegitcommit: 38d828ae8d4350ae774a939c8decf30cb36c3bea
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/02/2020
ms.locfileid: "49551952"
---
# <a name="additional-device-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations supplémentaires sur l’appareil pour la migration à partir de Microsoft Cloud Deutschland

## <a name="frequently-asked-questions"></a>Foire aux questions

**Comment puis-je savoir si mon organisation est concernée ?**

Les administrateurs doivent vérifier `https://portal.microsoftazure.de` s’ils disposent d’appareils inscrits. Si votre organisation a enregistré des appareils, vous en êtes affecté.

**Quel est l’impact sur mes utilisateurs ?**

Les utilisateurs d’un appareil inscrit ne seront plus en mesure de se connecter après la fin de la migration de la phase de migration [Azure ad](ms-cloud-germany-transition.md#how-is-the-migration-organized) .  

Assurez-vous que tous vos appareils sont inscrits auprès du point de terminaison international avant la déconnexion de votre organisation de Microsoft Cloud Deutschland.
  
**Quand mes utilisateurs réenregistrent-ils leurs appareils ?**

Il est essentiel pour votre réussite de ne pas enregistrer et ré-enregistrer vos appareils pendant la phase [de migration distincte de Microsoft Cloud Deutschland](ms-cloud-germany-transition.md#how-is-the-migration-organized) .

**Comment restaurer l’état de mon appareil après la migration ?**

Pour les appareils Windows hybrides, joints et appartenant à l’entreprise, qui sont enregistrés avec Azure AD, les administrateurs pourront gérer la migration de ces appareils via des flux de travail déclenchés à distance qui annuleront l’inscription des anciens États des appareils.
  
Pour tous les autres appareils, y compris les appareils Windows personnels inscrits dans Azure AD, l’utilisateur final doit effectuer ces étapes manuellement. Pour les appareils joints à Azure AD, les utilisateurs doivent disposer d’un compte d’administrateur local pour annuler l’inscription, puis ré-enregistrer leurs appareils.

Microsoft publiera des instructions sur la manière de restaurer correctement l’état de l’appareil. 
 
**Comment puis-je savoir que tous les appareils sont inscrits dans le cloud public ?**

Pour vérifier si vos appareils sont enregistrés dans le cloud public, vous devez exporter et télécharger la liste des périphériques depuis le portail Azure AD vers une feuille de calcul Excel. Ensuite, filtrez les périphériques inscrits (à l’aide de la colonne _registeredTime_ ) après la phase [de migration Deutschland de Microsoft Cloud](ms-cloud-germany-transition.md#how-is-the-migration-organized) .

L’inscription de l’appareil est désactivée après la migration du client et ne peut pas être activée ou désactivée. Si Intune n’est pas utilisé, connectez-vous à votre abonnement et exécutez cette commande pour réactiver l’option :

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```

## <a name="windows-hybrid-azure-ad-join"></a>Participation Windows hybride Azure AD

### <a name="windows-down-level"></a>Windows de bas niveau

Les _appareils de bas niveau Windows_ sont des appareils Windows qui exécutent actuellement des versions antérieures de Windows (telles que Windows 8,1 ou Windows 7) ou qui exécutent des versions de Windows Server antérieures à 2019 et 2016. Si de tels appareils ont été enregistrés auparavant, vous devrez annuler l’inscription et ré-enregistrer ces périphériques. 

Pour déterminer si un appareil de bas niveau de Windows a été précédemment joint à Azure AD, utilisez la commande suivante sur l’appareil :

```console
%programfiles%\Microsoft Workplace Join\autoworkplace /status
```

Si l’appareil a été précédemment joint à Azure AD et que l’appareil dispose d’une connectivité réseau aux points de terminaison Azure AD globaux, vous verrez le résultat suivant :

```console
+----------------------------------------------------------------------+
| Device Details                                                       |
+----------------------------------------------------------------------+
         DeviceId : AEE2B956-DA62-48D0-BB47-046DD992A110
       Thumbprint : 00fdfa2de5c32feae57489873a13aa6a3ff7433b
             User : user1@<tenantname>.de
Private key state : Okay
     Device state : Unknown
```

Le « État du périphérique » dont la valeur est « inconnu » est affecté aux appareils concernés. Si la sortie est « appareil non joint » ou dont la valeur « État de l’appareil » est « OK », ignorez les instructions suivantes.

Les administrateurs doivent exécuter la commande suivante dans le contexte d’un utilisateur de domaine qui se connecte sur un appareil de bas niveau uniquement pour les appareils qui indiquent que l’appareil est joint (en vertu d’un deviceId, d’une empreinte, etc.) et dont la valeur « État du périphérique » est « inconnue » :

```console
"%programfiles%\Microsoft Workplace Join\autoworkplace /leave"
```

La commande précédente ne doit être exécutée qu’une seule fois par utilisateur de domaine qui se connecte sur l’appareil bas Windows. Cette commande doit être exécutée dans le contexte de la connexion de l’utilisateur de domaine. 

Il faut veiller à ne pas exécuter cette commande lorsque l’utilisateur se connecte par la suite. Lorsque la commande précédente est exécutée, elle efface l’état de jonction de l’ordinateur hybride Azure AD-joint local de l’utilisateur qui s’est connecté. De plus, si l’ordinateur est toujours configuré pour être lié à Azure AD-joint au client, il essaiera de se joindre lorsque l’utilisateur se reconnecte.

### <a name="windows-current"></a>Windows actuel

#### <a name="unjoin"></a>Se désinscrire

Pour déterminer si l’appareil Windows 10 a été précédemment joint à Azure AD, exécutez la commande suivante sur l’appareil :

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

Si le périphérique est hybride Azure AD-joint, l’administrateur voit apparaître la sortie suivante :

```console
+----------------------------------------------------------------------+
| Device State                                                         |
+----------------------------------------------------------------------+
 
             AzureAdJoined : YES
          EnterpriseJoined : NO
              DomainJoined : YES
```

Si la sortie est « AzureAdJoined : no », ignorez les instructions suivantes.

Pour les appareils qui indiquent que l’appareil est joint à Azure AD, exécutez la commande suivante en tant qu’administrateur pour supprimer l’état de jonction de l’appareil.

```console
%SystemRoot%\system32\dsregcmd.exe /leave
```

La commande précédente ne doit être exécutée qu’une seule fois dans un contexte administratif sur l’appareil Windows.

#### <a name="hybrid-ad-joinre-registration"></a>Join\Re-Registration hybride AD

L’appareil est automatiquement joint à Azure AD sans intervention de l’utilisateur ou de l’administrateur tant que l’appareil dispose d’une connectivité réseau aux points de terminaison Azure AD globaux. 


## <a name="windows-azure-ad-join"></a>Participation à Windows Azure AD

### <a name="unjoin"></a>Se désinscrire

Pour déterminer si l’appareil Windows 10 a été précédemment joint à Azure AD, l’utilisateur ou l’administrateur peut exécuter la commande suivante sur l’appareil :

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

Si l’appareil est lié à Azure AD, l’utilisateur ou l’administrateur voit apparaître la sortie suivante :

```console
+----------------------------------------------------------------------+
| Device State                                                         |
+----------------------------------------------------------------------+
 
             AzureAdJoined : YES
          EnterpriseJoined : NO
              DomainJoined : NO
```

Si la sortie est « AzureAdJoined : NO », ignorez les instructions suivantes.

Utilisateur : si l’appareil est joint Azure AD, un utilisateur peut se déconnecter du périphérique des paramètres. Vérifiez qu’il existe un compte d’administrateur local sur l’appareil avant de procéder à la connexion de l’appareil à Azure AD. Le compte d’administrateur local est nécessaire pour se reconnecter à l’appareil.

Administrateur : si l’administrateur de l’organisation souhaite dissocier les appareils des utilisateurs Azure AD-joints, il peut le faire en exécutant la commande suivante sur chacun des périphériques à l’aide d’un mécanisme tel que la stratégie de groupe. L’administrateur doit vérifier qu’il existe un compte d’administrateur local sur l’appareil avant de rejoindre l’appareil à partir d’Azure AD. Le compte administrateur local est nécessaire pour se reconnecter à l’appareil.

```console
%SystemRoot%\system32\dsregcmd.exe /leave
```

La commande précédente ne doit être exécutée qu’une seule fois dans un contexte administratif sur l’appareil Windows. 

### <a name="azure-ad-joinre-registration"></a>Participation/ré-inscription Azure AD

L’utilisateur peut joindre l’appareil à Azure AD à partir des paramètres Windows : **paramètres > les comptes > accès professionnel ou scolaire > connecter**.
 

## <a name="windows-azure-ad-registered-company-owned"></a>Windows Azure AD inscrit (propriétaire de l’entreprise)

Pour déterminer si le périphérique Windows 10 est enregistré dans Azure AD – enregistré, exécutez la commande suivante sur l’appareil :

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

Si le périphérique est inscrit à Azure AD, le résultat suivant s’affiche :

```console
+----------------------------------------------------------------------+
| User State                                                           |
+----------------------------------------------------------------------+
           WorkplaceJoined : YES
          WamDefaultSet : NO
          WamDefaultAuthority : organizations
```

Pour supprimer le compte Azure AD existant inscrit sur l’appareil :

- Pour supprimer le compte Azure AD – inscrit sur l’appareil, utilisez CleanupWPJ, un outil que vous pouvez télécharger à partir de cet emplacement : [CleanupWPJ.zip](https://download.microsoft.com/download/8/e/f/8ef13ae0-6aa8-48a2-8697-5b1711134730/WPJCleanUp.zip).

- Extrayez le fichier ZIP et exécutez **WPJCleanup. cmd**. Cet outil lancera le fichier exécutable approprié en fonction de la version de Windows sur l’appareil.

- À l’aide d’un mécanisme comme la stratégie de groupe, l’administrateur peut exécuter la commande sur l’appareil dans le contexte d’un utilisateur connecté sur l’appareil.

Pour désactiver les invites du gestionnaire de comptes Web pour inscrire l’appareil dans Azure AD, ajoutez la valeur de Registre suivante : 

- Emplacement : HKLM\SOFTWARE\Policies\Microsoft\Windows\WorkplaceJoin
- Type : DWORD (32 bits)
- Nom : BlockAADWorkplaceJoin
- Données de la valeur : 1

La présence de cette valeur de registre doit bloquer la jonction Workplace et empêcher les utilisateurs de se connecter à l’appareil.

## <a name="android"></a>Android

Pour Android, les utilisateurs doivent annuler l’inscription et ré-enregistrer leurs appareils. Cette opération peut être réalisée via l’application Microsoft Authenticator ou l’application portail d’entreprise. 

- À partir de l’application Microsoft Authenticator, les utilisateurs peuvent accéder aux **paramètres > inscription de l’appareil**. À partir de là, les utilisateurs peuvent annuler l’inscription et ré-enregistrer leur appareil.
 
- À partir du portail d’entreprise, les utilisateurs peuvent accéder à l’onglet **appareils** et supprimer l’appareil. Ensuite, ré-Inscrivez l’appareil à l’aide du portail d’entreprise.
 
- Les utilisateurs peuvent également annuler l’inscription et procéder à une nouvelle inscription en supprimant le compte de la page Paramètres du compte, puis en rajoutant le compte professionnel.

Pour annuler l’inscription et ré-enregistrer l’appareil sur Android à l’aide de l’application Microsoft Authenticator :

1.  Ouvrez l’application Microsoft Authenticator et accédez à **paramètres**.
2.  Sélectionnez **inscription de l’appareil**.
3.  Annulez l’inscription de l’appareil en sélectionnant **Annuler l’inscription**.
4.  Pour l’inscription de l' **appareil**, inscrivez de nouveau l’appareil en saisissant votre adresse de messagerie, puis sélectionnez **Enregistrer**.

Pour annuler l’inscription et ré-enregistrer un appareil Android à l’aide de la page des paramètres Android :

1.  Ouvrez **paramètres du périphérique** et accédez à **comptes**.
2.  Sélectionnez le compte professionnel que vous souhaitez réenregistrer et sélectionnez Supprimer le **compte**.
3.  Une fois le compte supprimé, dans la page **comptes** , sélectionnez **ajouter un compte > compte professionnel**.
4.  Pour **Workplace Join**, tapez votre adresse de messagerie et sélectionnez **join** pour terminer l’inscription de l’appareil.

Pour annuler l’inscription et ré-enregistrer l’appareil sur Android à partir du portail d’entreprise :

1.  Lancez le portail d’entreprise et accédez à l’onglet **appareils** .
2.  Sélectionnez l’appareil pour afficher les détails de l’appareil.
3.  Dans le menu points de suspension (trois points), sélectionnez **Supprimer l’appareil**, puis terminez la suppression en procédant à la confirmation dans la boîte de dialogue.
4.  Vous devez maintenant être déconnecté de l’application portail d’entreprise. Sélectionnez **se connecter** pour réenregistrer l’appareil.

Pour plus d’informations sur les actions requises pendant la phase de migration de cette charge de travail, ou sur l’impact de l’administration ou de l’utilisation, consultez les informations relatives à Azure Active Directory dans [la rubrique informations générales supplémentaires pour la migration à partir de Microsoft Cloud Deutschland](ms-cloud-germany-transition-add-general.md#azure-active-directory).

## <a name="ios"></a>iOS

Sur les appareils iOS, un utilisateur doit supprimer manuellement les comptes mis en cache de l’authentificateur Microsoft, annuler l’inscription de l’appareil et se déconnecter des applications natives sur l’appareil.

### <a name="step-1-if-present-remove-the-account-from-the-microsoft-authenticator-app"></a>Étape 1 : le cas échéant, supprimez le compte de l’application Microsoft Authenticator.

1. Appuyez sur le compte dans l’application Microsoft Authenticator.
2. Appuyez sur l’icône **paramètres** dans le coin supérieur droit. Si vous ne voyez pas l’icône **paramètres** , il se peut que vous n’utilisiez pas la dernière version de Microsoft Authenticator.
3. Appuyez sur le bouton **supprimer le compte** .
4. Appuyez **sur toutes les applications sur cet appareil**.
 
### <a name="step-2-unregister-the-device-from-the-microsoft-authenticator-app"></a>Étape 2 : annuler l’inscription de l’appareil dans l’application Microsoft Authenticator

1. Appuyez sur l’icône de menu dans le coin supérieur droit.
2. Appuyez sur **paramètres** , puis sur **inscription de l’appareil**.
4. Si votre compte est affiché, appuyez sur **Annuler l’inscription** de l’appareil et **continuez** dans la boîte de dialogue. Aucun compte ne doit être affiché.
 
### <a name="step-3-sign-out-from-individual-apps-if-necessary"></a>Étape 3 : Déconnectez-vous des applications individuelles si nécessaire

Les utilisateurs peuvent accéder à des applications individuelles telles qu’Outlook, teams et OneDrive, et supprimer des comptes de ces applications.

## <a name="more-information"></a>Plus d’informations

Mise en route :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centre de connaissances allemand](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client lors de la migration](ms-cloud-germany-transition-experience.md)

Navigation par le biais de la transition :

- [Actions et impacts sur les phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour les [services](ms-cloud-germany-transition-add-general.md), les [appareils](ms-cloud-germany-transition-add-devices.md), les [expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications Cloud :

- [Informations sur le programme de migration Dynamics 365](https://aka.ms/d365ceoptin)
- [Informations sur le programme de migration Power BI](https://aka.ms/pbioptin)
- [Prise en main de votre mise à niveau vers Microsoft Teams](https://aka.ms/SkypeToTeams-Home)
