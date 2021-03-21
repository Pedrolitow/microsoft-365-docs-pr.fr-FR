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
description: 'Résumé : Informations supplémentaires sur les appareils sur les services lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) aux services Office 365 dans la nouvelle région de centres de données allemande.'
ms.openlocfilehash: 21188372f03af394fe1c0e227c1adeabbad02a85
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50928155"
---
# <a name="additional-device-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations supplémentaires sur l’appareil pour la migration à partir de Microsoft Cloud Deutschland

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

**Comment savoir si mon organisation est affectée ?**

Les administrateurs doivent `https://portal.microsoftazure.de` vérifier s’ils ont des appareils enregistrés. Si votre organisation dispose d’appareils inscrits, vous êtes affecté.

**Quel est l’impact sur mes utilisateurs ?**

Les utilisateurs d’un appareil enregistré ne pourront plus se connecter une fois votre migration entrée dans la phase finaliser la migration [Azure AD.](ms-cloud-germany-transition.md#how-is-the-migration-organized)  

Assurez-vous que tous vos appareils sont enregistrés auprès du point de terminaison mondial avant que votre organisation ne soit déconnectée de Microsoft Cloud Deutschland.
  
**Quand mes utilisateurs ré-inscrivent-ils leurs appareils ?**

Pour réussir, vous devez uniquement désins inscrire et réenregistrer vos appareils lors de la phase de migration Distinct [de Microsoft Cloud Deutschland.](ms-cloud-germany-transition.md#how-is-the-migration-organized)

**Comment restaurer l’état de mon appareil après la migration ?**

Pour les appareils Windows hybrides joints à Azure AD et dont l’entreprise est propriétaire et qui sont enregistrés auprès d’Azure AD, les administrateurs pourront gérer la migration de ces appareils via des flux de travail déclenchés à distance qui désinsèreront les anciens états d’appareil.
  
Pour tous les autres appareils, y compris les appareils Windows personnels inscrits dans Azure AD, l’utilisateur final doit effectuer ces étapes manuellement. Pour les appareils joints à Azure AD, les utilisateurs doivent avoir un compte d’administrateur local pour se désins inscrire, puis réenregistrer leurs appareils.

Microsoft publiera des instructions pour la restauration de l’état de l’appareil. 
 
**Comment savoir que tous mes appareils sont inscrits dans le cloud public ?**

Pour vérifier si vos appareils sont inscrits dans le cloud public, vous devez exporter et télécharger la liste des appareils à partir du portail Azure AD vers une feuille de calcul Excel. Ensuite, filtrez les appareils inscrits (à l’aide de la colonne _registeredTime)_ après la phase de migration Distinct [de Microsoft Cloud Deutschland.](ms-cloud-germany-transition.md#how-is-the-migration-organized)

L’inscription de l’appareil est désactivée après la migration du client et ne peut pas être activée ou désactivée. Si Intune n’est pas utilisé, connectez-vous à votre abonnement et exécutez cette commande pour réactiver l’option :

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```

## <a name="hybrid-azure-ad-join"></a>Jonction Azure AD Hybride

### <a name="windows-down-level"></a>Windows au niveau inférieur

Les appareils _Windows_ de niveau inférieur sont des appareils Windows qui exécutent actuellement des versions antérieures de Windows (par exemple, Windows 8.1 ou Windows 7) ou qui exécutent des versions de Windows Server antérieures à 2019 et 2016. Si ces appareils ont été enregistrés auparavant, vous devez les désins inscrire et les réins inscrire. 

Pour déterminer si un appareil windows de bas niveau a été précédemment joint à Azure AD, utilisez la commande suivante sur l’appareil :

```console
%programfiles%\Microsoft Workplace Join\autoworkplace /status
```

Si l’appareil a été précédemment joint à Azure AD et si l’appareil dispose d’une connectivité réseau aux points de terminaison Azure AD globaux, vous verrez le résultat suivant :

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

Les appareils concernés auront l'« état de l’appareil » avec la valeur « Unknown ». Si la sortie est « Appareil non joint » ou dont la valeur « État de l’appareil » est « OK », ignorez les instructions suivantes.

Uniquement pour les appareils qui indiquent que l’appareil est joint (en raison de deviceId, de l’empreinte numérique, et ainsi de suite) et dont la valeur « État de l’appareil » est « Inconnu », les administrateurs doivent exécuter la commande suivante dans le contexte d’un utilisateur de domaine qui se connecté sur un appareil de niveau inférieur :

```console
"%programfiles%\Microsoft Workplace Join\autoworkplace /leave"
```

La commande précédente ne doit être exécuté qu’une seule fois par utilisateur de domaine se signant sur l’appareil windows de niveau inférieur. Cette commande doit être exécuté dans le contexte de la signature de l’utilisateur du domaine. 

Une attention suffisante doit être prise pour ne pas exécuter cette commande lorsque l’utilisateur se signe par la suite. Lorsque la commande précédente s’exécute, elle effacera l’état joint de l’ordinateur hybride local joint à Azure AD pour l’utilisateur qui s’est inscrit. De plus, si l’ordinateur est toujours configuré pour être joint à Azure AD hybride dans le client, il tentera d’y participer lorsque l’utilisateur se joindra à nouveau.

### <a name="windows-current"></a>Windows Current

#### <a name="unjoin"></a>Unjoin

Pour déterminer si l’appareil Windows 10 a été précédemment joint à Azure AD, exécutez la commande suivante sur l’appareil :

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

Si l’appareil est joint à Azure AD hybride, l’administrateur voit le résultat suivant :

```console
+----------------------------------------------------------------------+
| Device State                                                         |
+----------------------------------------------------------------------+
 
             AzureAdJoined : YES
          EnterpriseJoined : NO
              DomainJoined : YES
```

Si la sortie est « AzureAdJoined : Non », ignorez les instructions suivantes.

Uniquement pour les appareils qui indiquent que l’appareil est joint à Azure AD, exécutez la commande suivante en tant qu’administrateur pour supprimer l’état joint de l’appareil.

```console
%SystemRoot%\system32\dsregcmd.exe /leave
```

La commande précédente ne doit être exécuté qu’une seule fois dans un contexte d’administration sur l’appareil Windows.

#### <a name="hybrid-ad-joinre-registration"></a>Hybrid AD Join\Re-Registration

L’appareil est automatiquement joint à Azure AD sans intervention de l’utilisateur ou de l’administrateur tant que l’appareil dispose d’une connectivité réseau aux points de terminaison Azure AD globaux. 


## <a name="azure-ad-join"></a>Azure AD Join

**IMPORTANT :** Le principal de service Intune sera activé après la migration commerciale, ce qui implique l’activation d’Azure AD Device Registration. Si vous avez bloqué l’inscription des appareils Azure AD avant la migration, vous devez désactiver le principal de service Intune avec PowerShell pour désactiver à nouveau l’inscription des appareils Azure AD avec le portail Azure AD. Vous pouvez désactiver le principal de service Intune avec cette commande dans le module Azure Active Directory PowerShell pour Graph.

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```

### <a name="unjoin"></a>Unjoin

Pour déterminer si l’appareil Windows 10 a été précédemment joint à Azure AD, l’utilisateur ou l’administrateur peut exécuter la commande suivante sur l’appareil :

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

Si l’appareil est joint à Azure AD, l’utilisateur ou l’administrateur verra le résultat suivant :

```console
+----------------------------------------------------------------------+
| Device State                                                         |
+----------------------------------------------------------------------+
 
             AzureAdJoined : YES
          EnterpriseJoined : NO
              DomainJoined : NO
```

Si la sortie est « AzureAdJoined : NO », ignorez les instructions suivantes.

Utilisateur : si l’appareil est joint à Azure AD, un utilisateur peut déjoinder l’appareil des paramètres. Vérifiez qu’il existe un compte d’administrateur local sur l’appareil avant de l’avoir désjoindée d’Azure AD. Le compte d’administrateur local est requis pour se remettre à l’appareil.

Administrateur : si l’administrateur de l’organisation souhaite déjoinder les appareils des utilisateurs joints à Azure AD, ils peuvent le faire en exécutant la commande suivante sur chacun des appareils à l’aide d’un mécanisme tel que la stratégie de groupe. L’administrateur doit vérifier qu’il existe un compte d’administrateur local sur l’appareil avant de l’avoir désjoindée d’Azure AD. Le compte d’administrateur local est nécessaire pour se remettre à l’appareil.

```console
%SystemRoot%\system32\dsregcmd.exe /leave
```

La commande précédente ne doit être exécuté qu’une seule fois dans un contexte d’administration sur l’appareil Windows. 

### <a name="azure-ad-joinre-registration"></a>Azure AD Join/Re-Registration

L’utilisateur peut joindre l’appareil à Azure AD à partir des paramètres Windows : Paramètres > Comptes > Accès Entreprise ou **Scolaire > Se connecter.**
 

## <a name="azure-ad-registered-company-owned"></a>Azure AD Registered (propriété de l’entreprise)

Pour déterminer si l’appareil Windows 10 est inscrit sur Azure AD, exécutez la commande suivante sur l’appareil :

```console
%SystemRoot%\system32\dsregcmd.exe /status
```

Si l’appareil est enregistré dans Azure AD, vous verrez la sortie suivante :

```console
+----------------------------------------------------------------------+
| User State                                                           |
+----------------------------------------------------------------------+
           WorkplaceJoined : YES
          WamDefaultSet : NO
          WamDefaultAuthority : organizations
```

Pour supprimer le compte Azure AD existant sur l’appareil :

- Pour supprimer le compte Azure AD enregistré sur l’appareil, utilisez CleanupWPJ, un outil que vous pouvez télécharger à partir [ d’ici :CleanupWPJ.zip](https://download.microsoft.com/download/8/e/f/8ef13ae0-6aa8-48a2-8697-5b1711134730/WPJCleanUp.zip).

- Extrayez le fichier ZIP et exécutez **WPJCleanup.cmd**. Cet outil lance le bon exécutable en fonction de la version de Windows sur l’appareil.

- À l’aide d’un mécanisme tel que la stratégie de groupe, l’administrateur peut exécuter la commande sur l’appareil dans le contexte de tout utilisateur connecté à l’appareil.

Pour désactiver les invites du Gestionnaire de comptes Web pour inscrire l’appareil dans Azure AD, ajoutez cette valeur de Registre : 

- Emplacement : HKLM\SOFTWARE\Policies\Microsoft\Windows\WorkplaceJoin
- Type : DWORD (32 bits)
- Nom : BlockAADWorkplaceJoin
- Données de valeur : 1

La présence de cette valeur de Registre doit bloquer l’accès à l’espace de travail et empêcher les utilisateurs de voir des invites pour rejoindre l’appareil.

## <a name="android"></a>Android

Pour Android, les utilisateurs doivent désins inscrire et réenregistrer leurs appareils. Pour ce faire, vous pouvez utiliser l’application Microsoft Authenticator ou l’application Portail d’entreprise. 

- À partir de l’application Microsoft Authenticator, les utilisateurs peuvent passer à **Paramètres >'inscription de l’appareil.** À partir de là, les utilisateurs peuvent désins inscrire et réenregistrer leur appareil.
 
- À partir du portail d’entreprise, les utilisateurs peuvent se rendre sur l’onglet **Appareils** et supprimer l’appareil. Après cela, ré-inscrire l’appareil à l’aide du portail d’entreprise.
 
- Les utilisateurs peuvent également se désins inscrire et s’inscrire à la nouvelle inscription en supprimant le compte de la page des paramètres du compte, puis en ajoutant à nouveaux le compte de travail.

Pour désins inscrire et réenregistrer l’appareil sur Android à l’aide de l’application Microsoft Authenticator :

1.  Ouvrez l’application Microsoft Authenticator et go to **Settings**.
2.  Sélectionnez **Inscription de l’appareil.**
3.  Désinsister l’appareil en sélectionnant **Unregister**.
4.  Pour **l’inscription de** l’appareil, ré-inscrivez l’appareil en tapant votre adresse e-mail, puis sélectionnez **Enregistrer.**

Pour désins inscrire et réenregistrer un appareil Android avec la page Paramètres Android :

1.  Ouvrez **Paramètres de l’appareil** et go to **Accounts**.
2.  Sélectionnez le compte de travail que vous souhaitez ré-inscrire et **sélectionnez Supprimer le compte.**
3.  Une fois le compte supprimé, dans la **page** Comptes, sélectionnez Ajouter un **compte > compte de travail.**
4.  For **Workplace Join**, type your email address and select **Join** to complete registering the device.

Pour désins inscrire et réenregistrer l’appareil sur Android à partir du portail d’entreprise :

1.  Lancez Le portail d’entreprise et allez dans **l’onglet Appareils.**
2.  Sélectionnez l’appareil pour voir les détails de l’appareil.
3.  Dans le menu points de sélection (trois points), sélectionnez Supprimer l’appareil **et** terminez la suppression en confirmant dans la boîte de dialogue.
4.  Vous devez maintenant être déconnecté de l’application Portail d’entreprise. Sélectionnez **Se connectez** pour ré-inscrire l’appareil.

Pour plus d’informations sur les actions requises pendant la phase de migration de cette charge de travail, ou sur l’impact sur l’administration ou l’utilisation, examinez les informations sur Azure Active Directory (Azure AD) dans Informations [Azure AD](ms-cloud-germany-transition-azure-ad.md)supplémentaires pour la migration à partir de Microsoft Cloud Deutschland .

## <a name="ios"></a>iOS

Sur les appareils iOS, un utilisateur doit supprimer manuellement tous les comptes mis en cache de Microsoft Authenticator, désinsister l’appareil et se dé dé connecter à partir des applications natives de l’appareil.

### <a name="step-1-if-present-remove-the-account-from-the-microsoft-authenticator-app"></a>Étape 1 : si elle est présente, supprimez le compte de l’application Microsoft Authenticator

1. Appuyez sur le compte dans l’application Microsoft Authenticator.
2. Appuyez **sur l’icône Paramètres** dans le coin supérieur droit. Si vous ne voyez pas l’icône **Paramètres,** il se peut que vous n’utilisiez pas la dernière version de Microsoft Authenticator.
3. Appuyez sur **le bouton** Supprimer le compte.
4. Appuyez **sur toutes les applications sur cet appareil.**
 
### <a name="step-2-unregister-the-device-from-the-microsoft-authenticator-app"></a>Étape 2 : Désinsser l’appareil de l’application Microsoft Authenticator

1. Appuyez sur l’icône de menu dans le coin supérieur droit.
2. Appuyez **sur Paramètres,** puis **sur Inscription de l’appareil.**
4. Si votre compte s’affiche, **appuyez sur Désinsister l’appareil** et **continuez** dans la boîte de dialogue. Vous ne devriez voir aucun compte après cela.
 
### <a name="step-3-sign-out-from-individual-apps-if-necessary"></a>Étape 3 : Se sortir des applications individuelles si nécessaire

Les utilisateurs peuvent se rendre sur des applications individuelles telles qu’Outlook, Teams et OneDrive, et supprimer des comptes de ces applications.

## <a name="more-information"></a>Informations supplémentaires

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers les services Office 365 dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
- [Aide à la migration de Microsoft Cloud Deutschland : ](https://aka.ms/germanymigrateassist)
- [Comment opter pour une migration](ms-cloud-germany-migration-opt-in.md)
- [Expérience client pendant la migration](ms-cloud-germany-transition-experience.md)

Transition :

- [Actions et impacts des phases de migration](ms-cloud-germany-transition-phases.md)
- [Pré-travail supplémentaire](ms-cloud-germany-transition-add-pre-work.md)
- Informations supplémentaires pour [Azure AD,](ms-cloud-germany-transition-azure-ad.md) [les appareils,](ms-cloud-germany-transition-add-devices.md) [les expériences](ms-cloud-germany-transition-add-experience.md)et [AD FS](ms-cloud-germany-transition-add-adfs.md).

Applications cloud :

- [Informations sur le programme de migration Dynamics 365](/dynamics365/get-started/migrate-data-german-region)
- [Informations sur le programme de migration Power BI](/power-bi/admin/service-admin-migrate-data-germany)
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)