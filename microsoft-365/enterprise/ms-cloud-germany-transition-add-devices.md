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
description: 'Résumé : Informations supplémentaires sur les appareils sur les services lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) à Office 365 services dans la nouvelle région de centres de données allemande.'
ms.openlocfilehash: 27426a26befab85bf62a0a143861e447dd722724
ms.sourcegitcommit: 3e971b31435d17ceeaa9871c01e88e25ead560fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2021
ms.locfileid: "52861302"
---
# <a name="additional-device-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations supplémentaires sur l’appareil pour la migration à partir de Microsoft Cloud Deutschland

Les appareils joints à Azure AD et inscrits connectés à Microsoft Cloud Deutschland doivent être migrés après la phase 9 et avant la phase 10. La migration d’un appareil dépend du type d’appareil, du système d’exploitation et de la relation AAD. 

## <a name="frequently-asked-questions"></a>Foire aux questions

**Comment savoir si mon organisation est affectée ?**

Les administrateurs doivent vérifier s’ils ont des appareils inscrits ou joints `https://portal.microsoftazure.de` à Azure AD. Si votre organisation dispose d’appareils inscrits, vous êtes affecté.

**Quel est l’impact sur mes utilisateurs ?**

Les utilisateurs d’un appareil enregistré ne pourront plus se connecter une fois la [phase de migration 10](ms-cloud-germany-transition-phases.md#phase-9--10-azure-ad-finalization) terminée et les points de terminaison de Microsoft Cloud Deutschland désactivés.  

Assurez-vous que tous vos appareils sont enregistrés auprès du point de terminaison mondial avant que votre organisation ne soit déconnectée de Microsoft Cloud Deutschland.
  
**Quand mes utilisateurs ré-inscrivent-ils leurs appareils ?**

Il est essentiel pour votre réussite que vous désins inscrivez et réenregistrez vos appareils une fois la [phase 9](ms-cloud-germany-transition-phases.md#phase-9--10-azure-ad-finalization) terminée. Vous devez terminer la ré-inscription avant le démarrage de la phase 10, sinon vous risquez de perdre l’accès à votre appareil.

**Comment restaurer l’état de mon appareil après la migration ?**

Pour les appareils Windows d’entreprise enregistrés auprès d’Azure AD, les administrateurs pourront gérer la migration de ces appareils via des flux de travail déclenchés à distance qui désinsisteront les anciens états d’appareil.
  
Pour tous les autres appareils, y compris les appareils Windows personnels enregistrés dans Azure AD, l’utilisateur final doit effectuer ces étapes manuellement. Pour les appareils joints à Azure AD, les utilisateurs doivent avoir un compte d’administrateur local pour se désins inscrire, puis réenregistrer leurs appareils.

Consultez les instructions détaillées pour savoir comment restaurer correctement les états de l’appareil ci-dessous. 
 
**Comment savoir que tous mes appareils sont inscrits dans le cloud public ?**

Pour vérifier si vos appareils sont enregistrés dans le cloud public, vous devez exporter et télécharger la liste des appareils à partir du portail Azure AD vers une feuille de calcul Excel. Ensuite, filtrez les appareils inscrits (à l’aide de la colonne _registeredTime)_ après la phase de migration Distinct [de Microsoft Cloud Deutschland.](ms-cloud-germany-transition.md#how-is-the-migration-organized)

## <a name="additional-considerations"></a>Considérations supplémentaires
L’inscription de l’appareil est désactivée après la migration du client et ne peut pas être activée ou désactivée. 

Si Intune n’est pas utilisé, connectez-vous à votre abonnement et exécutez cette commande pour réactiver l’option :

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```
**IMPORTANT :** Le principal de service Intune sera activé après la migration commerciale, ce qui implique l’activation d’Azure AD Device Registration. Si vous avez bloqué l’inscription des appareils Azure AD avant la migration, vous devez désactiver le principal de service Intune avec PowerShell pour désactiver à nouveau l’inscription des appareils Azure AD avec le portail Azure AD. Vous pouvez désactiver le principal de service Intune avec cette commande dans la Azure Active Directory PowerShell pour Graph module.

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```


## <a name="azure-ad-join"></a>Azure AD Join
Cela s’applique Windows 10 appareils mobiles. 

Si un appareil est joint à Azure AD, il doit être déconnecté d’Azure AD et être de nouveau connecté. 

[![Azure AD Device ](../media/ms-cloud-germany-migration-opt-in/AAD-ReJoin-flow.png) Re-Join Flow](../media/ms-cloud-germany-migration-opt-in/AAD-ReJoin-flow.png#lightbox)


Si l’utilisateur est un administrateur sur l’appareil Windows 10, l’utilisateur peut désinsser l’appareil d’Azure AD et le rejoindre à nouveau. S’il n’a pas de privilèges d’administrateur, l’utilisateur a besoin des informations d’identification d’un compte d’administrateur local sur cet ordinateur. 


Un administrateur peut créer un compte d’administrateur local sur l’appareil en suivant ce chemin de configuration :

*Paramètres > comptes > autres comptes > informations d’identification inconnues > ajouter un utilisateur sans compte Microsoft*

### <a name="step-1-determine-if-the-device-is-azure-id-joined"></a>Étape 1 : Déterminer si l’appareil est joint à Azure ID
1.  Connectez-vous avec le courrier électronique et le mot de passe des utilisateurs.
2.  Accédez à Paramètres > comptes > Access Work ou School. 
3.  Rechercher un utilisateur dans la liste avec **connecté à... 's Azure AD**. 
4.  Si un utilisateur connecté existe, procédez à l’étape 2. Si ce n’est pas le cas, aucune action supplémentaire n’est requise.
### <a name="step-2-disconnect-the-device-from-azure-ad"></a>Étape 2 : Déconnecter l’appareil d’Azure AD
1.  Appuyez sur Déconnectez-vous sur le compte scolaire ou scolaire ou scolaire connecté.  
2.  Confirmez la déconnexion deux fois. 
3.  Entrez le nom d’utilisateur et le mot de passe de l’administrateur local. L’appareil est déconnecté.
4.  Redémarrez l’appareil.
### <a name="step-3-join-the-device-to-azure-ad"></a>Étape 3 : Joindre l’appareil à Azure AD
1.  l’utilisateur se connexion avec les informations d’identification de l’administrateur local
2.  Accédez **à Paramètres** **puis Comptes,** **puis Accéder au travail ou à l’établissement scolaire**
3.  Appuyez **sur Connecter**
4.  **IMPORTANT**: **appuyez sur Rejoindre Azure AD**
5.  Entrez l’adresse de messagerie et le mot de passe de l’utilisateur. L’appareil est connecté
6.  Redémarrer l’appareil 
7.  se signer avec votre adresse de messagerie et votre mot de passe

## <a name="azure-ad-registered-company-owned"></a>Azure AD Registered (propriété de l’entreprise)

Pour déterminer si l’Windows 10 est inscrit à Azure AD, exécutez la commande suivante sur l’appareil :

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

Pour Android, les utilisateurs doivent désins inscrire et réenregistrer leurs appareils. Vous pouvez le faire via l’application Microsoft Authenticator ou l’application Portail d’entreprise’application. 

- À partir de Microsoft Authenticator’application, les utilisateurs peuvent Paramètres > **inscription de l’appareil.** À partir de là, les utilisateurs peuvent désins inscrire et réenregistrer leur appareil.
 
- À partir de Portail d’entreprise, les utilisateurs peuvent se rendre sur l’onglet **Appareils** et supprimer l’appareil. Ensuite, réinscrivez l’appareil à l’aide Portail d’entreprise.
 
- Les utilisateurs peuvent également se désins inscrire et s’inscrire à la nouvelle inscription en supprimant le compte de la page des paramètres du compte, puis en ajoutant à nouveaux le compte de travail.

Pour désins inscrire et réenregistrer l’appareil sur Android à l’aide Microsoft Authenticator application :

1.  Ouvrez l Microsoft Authenticator appl; et Paramètres **.**
2.  Sélectionnez **Inscription de l’appareil.**
3.  Désinsinser l’appareil en sélectionnant **Désinsinsion**.
4.  Pour **l’inscription de** l’appareil, ré-inscrivez l’appareil en tapant votre adresse e-mail, puis sélectionnez **Enregistrer.**

Pour désins inscrire et réenregistrer un appareil Android à l’Paramètres page :

1.  Ouvrez **Device Paramètres** et go to **Accounts**.
2.  Sélectionnez le compte de travail que vous souhaitez ré-inscrire et **sélectionnez Supprimer le compte.**
3.  Une fois le compte supprimé, dans la **page** Comptes, sélectionnez Ajouter un **compte > compte de travail.**
4.  Pour **Workplace Join,** tapez votre adresse e-mail et **sélectionnez Rejoindre** pour terminer l’inscription de l’appareil.

Pour désins inscrire et réenregistrer l’appareil sur Android, Portail d’entreprise :

1.  Lancez Portail d’entreprise et allez sur **l’onglet** Appareils.
2.  Sélectionnez l’appareil pour voir les détails de l’appareil.
3.  Dans le menu des points de sélection (trois points), sélectionnez Supprimer l’appareil **et** terminez la suppression en confirmant dans la boîte de dialogue.
4.  Vous devez maintenant être déconnecté de l’application Portail d’entreprise’application. Sélectionnez **Se connectez** pour ré-inscrire l’appareil.

Pour plus d’informations sur les actions requises pendant la phase de migration de cette charge de travail, ou sur l’impact sur l’administration ou l’utilisation, examinez les informations sur Azure Active Directory (Azure AD) dans Des informations [Azure AD](ms-cloud-germany-transition-azure-ad.md)supplémentaires pour la migration à partir de Microsoft Cloud Deutschland .

## <a name="ios"></a>iOS

Sur les appareils iOS, un utilisateur doit supprimer manuellement tous les comptes mis en cache de l’Microsoft Authenticator, désins inscrire l’appareil et se dé dé connecter à partir de toutes les applications natives de l’appareil.

### <a name="step-1-if-present-remove-the-account-from-the-microsoft-authenticator-app"></a>Étape 1 : si elle est présente, supprimez le compte de l’application Microsoft Authenticator client

1. Appuyez sur le compte dans l Microsoft Authenticator appl;
2. Appuyez sur **Paramètres** icône dans le coin supérieur droit. Si vous ne voyez pas **l’icône Paramètres,** il se peut que vous n’utilisiez pas la dernière version de Microsoft Authenticator.
3. Appuyez sur **le bouton** Supprimer le compte.
4. Appuyez **sur toutes les applications sur cet appareil.**
 
### <a name="step-2-unregister-the-device-from-the-microsoft-authenticator-app"></a>Étape 2 : Désinsser l’appareil de l Microsoft Authenticator appel

1. Appuyez sur l’icône de menu dans le coin supérieur droit.
2. Appuyez **Paramètres** puis inscription **de l’appareil.**
4. Si votre compte s’affiche, **appuyez sur Désinsister l’appareil** et **continuez** dans la boîte de dialogue. Vous ne devriez voir aucun compte après cela.
 
### <a name="step-3-sign-out-from-individual-apps-if-necessary"></a>Étape 3 : Se sortir des applications individuelles si nécessaire

Les utilisateurs peuvent se rendre sur des applications individuelles telles que Outlook, Teams et OneDrive, et supprimer des comptes de ces applications.

## <a name="more-information"></a>Plus d’informations

Mise en place :

- [Migration de Microsoft Cloud Deutschland vers Office 365 services dans les nouvelles régions de centres de données allemandes](ms-cloud-germany-transition.md)
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
- [Prise en main de votre mise à niveau vers Microsoft Teams](/microsoftteams/upgrade-start-here)