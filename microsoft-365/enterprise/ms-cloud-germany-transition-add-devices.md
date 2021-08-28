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
description: 'Résumé : Informations supplémentaires sur les appareils sur les services lors du passage de Microsoft Cloud Germany (Microsoft Cloud Deutschland) à Office 365 services dans la nouvelle région de centres de données allemands.'
ms.openlocfilehash: 79234b1398e26af5a2848002ea606d97137e3053
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58573090"
---
# <a name="additional-device-information-for-the-migration-from-microsoft-cloud-deutschland"></a>Informations supplémentaires sur l’appareil pour la migration à partir de Microsoft Cloud Deutschland

Les appareils joints à Azure AD et inscrits connectés à Microsoft Cloud Deutschland doivent être migrés après la phase 9 et avant la phase 10. La migration d’un appareil dépend du type d’appareil, du système d’exploitation et de la relation Azure AD.

## <a name="azure-ad-joined-windows-10-devices"></a>Appareils joints à Azure AD Windows 10 appareils
Si un Windows 10 est joint à Azure AD, il doit être déconnecté d’Azure AD et doit être connecté à nouveau.

[![Azure AD Device Re-Join Flow. ](../media/ms-cloud-germany-migration-opt-in/AAD-ReJoin-flow.png)](../media/ms-cloud-germany-migration-opt-in/AAD-ReJoin-flow.png#lightbox)


Si l’utilisateur est un administrateur sur l’appareil Windows 10, il peut désinsser l’appareil d’Azure AD et le rejoindre à nouveau en trois étapes.

### <a name="step-1-determine-if-the-device-is-azure-id-joined"></a>Étape 1 : Déterminer si l’appareil est joint à Azure ID

1. Connectez-vous avec votre compte professionnel.
2. Go to **Paramètres**  >  **Accounts**  >  **Access Work or School**.
3. Rechercher un compte dans la liste avec **connecté à [...]' s Azure AD**.
4. Si un compte connecté existe, procédez à l’étape 2.

### <a name="step-2-disconnect-the-device-from-azure-ad"></a>Étape 2 : Déconnecter l’appareil d’Azure AD

1. Cliquez **sur Déconnecter** sur le compte scolaire ou scolaire ou scolaire connecté.
2. Confirmez la déconnexion deux fois.
3. Entrez un nom d’utilisateur et un mot de passe d’administrateur local. L’appareil est déconnecté.
4. Redémarrez l’appareil.

### <a name="step-3-join-the-device-to-azure-ad"></a>Étape 3 : Joindre l’appareil à Azure AD

1. Connectez-vous avec les informations d’identification de l’administrateur local.
2. Go to **Paramètres**  >  **Accounts**  >  **Access Work or School**.
3. Cliquez sur **Connecter**.
4. **IMPORTANT**: cliquez **sur Rejoindre Azure AD.**
5. Entrez l’adresse de messagerie et le mot de passe de votre compte de travail. L’appareil est connecté.
6. Redémarrez l’appareil.
7. Connectez-vous avec l’adresse e-mail et le mot de passe de votre compte de travail.

Si l’utilisateur n’est pas administrateur de l’appareil, un administrateur général Azure AD peut créer le compte d’administrateur local sur l’appareil en suivant ce chemin de configuration et l’un des deux :

*Paramètres > comptes > autres comptes > informations d’identification > ajouter un utilisateur sans compte Microsoft*

Pour re-rejoindre, les informations d’identification de n’importe quel compte de travail de votre organisation peuvent être utilisées dans cette étape.

Sachez que le compte de travail utilisé pour joindre l’appareil sera automatiquement promu en tant qu’administrateur de l’appareil.
Tout autre compte professionnel de l’organisation peut se connecter à l’appareil, mais ne dispose pas de privilèges d’administrateur.

## <a name="azure-ad-registered-workplace-joined-windows-10-devices"></a>Azure AD inscrit (joint à l’espace de travail) Windows 10 appareils

Si un Windows 10 est inscrit à Azure AD, il doit être déconnecté d’Azure AD et de nouveau connecté.

[![Azure AD Device Re-Registration Flow. ](../media/ms-cloud-germany-migration-opt-in/AAD-ReRegistration-flow.png)](../media/ms-cloud-germany-migration-opt-in/AAD-ReJoin-flow.png#lightbox)

### <a name="step-1-determine-if-the-device-is-azure-id-registered"></a>Étape 1 : Déterminer si l’appareil est inscrit sur Azure ID

1. Connectez-vous avec votre utilisateur.
2. Go to **Paramètres**  >  **Accounts**  >  **Access Work or School**.
3. Découvrez votre compte de travail dans la liste et vérifiez s’il **est connecté à [...]' s Azure AD**.

    Si votre compte de travail figure dans la liste mais n’est pas connecté à Azure AD, procédez à l’étape 2.

    Dans le cas contraire, votre appareil est joint à Azure AD et vous devez faire référence à [Azure AD Joined Windows 10 appareils.](#azure-ad-joined-windows-10-devices)

### <a name="step-2-disconnect-the-device-from-azure-ad"></a>Étape 2 : Déconnecter l’appareil d’Azure AD

1. Cliquez sur votre compte de travail. Les boutons *Informations et* *Déconnexion* apparaissent.
2. Cliquez sur **Déconnecter.**
3. Confirmez la suppression du compte de l’appareil en **cliquant** sur Oui .

### <a name="step-3-connect-the-device-to-azure-ad"></a>Étape 3 : Connecter l’appareil vers Azure AD

1. Cliquez sur **Connecter**.
2. Entrez l’adresse e-mail de votre compte de travail, puis cliquez sur **Suivant**.
3. Entrez le mot de passe de votre compte de travail, puis cliquez **sur Se connectez.**
4. Confirmez en cliquant sur **Terminé**. Votre compte de travail est de nouveau répertorié.

## <a name="android"></a>Android

Pour Android, les utilisateurs doivent désins inscrire et réenregistrer leurs appareils. Vous pouvez le faire via l’application Microsoft Authenticator ou l’application Portail d’entreprise’application.

- À partir de Microsoft Authenticator’application, les utilisateurs peuvent Paramètres > **inscription de l’appareil.** À partir de là, les utilisateurs peuvent désins inscrire et réenregistrer leur appareil.

- À partir de Portail d’entreprise, les utilisateurs peuvent se rendre sur l’onglet **Appareils** et supprimer l’appareil. Ensuite, réinscrivez l’appareil à l’aide Portail d’entreprise.

- Les utilisateurs peuvent également se désins inscrire et s’inscrire à la nouvelle inscription en supprimant le compte de la page des paramètres du compte, puis en ajoutant à nouveaux le compte de travail.

Pour désins inscrire et réenregistrer l’appareil sur Android à l’aide Microsoft Authenticator application :

1. Ouvrez l Microsoft Authenticator appl; et Paramètres **.**
2. Sélectionnez **Inscription de l’appareil.**
3. Désinsinser l’appareil en sélectionnant **Désinsinsion**.
4. Pour **l’inscription de** l’appareil, ré-inscrivez l’appareil en tapant votre adresse e-mail, puis sélectionnez **Enregistrer.**

Pour désins inscrire et réenregistrer un appareil Android à l’Paramètres page :

1. Ouvrez **Device Paramètres** et go to **Accounts**.
2. Sélectionnez le compte de travail que vous souhaitez ré-inscrire et **sélectionnez Supprimer le compte.**
3. Une fois le compte supprimé, dans la **page** Comptes, sélectionnez Ajouter un **compte > compte de travail.**
4. For **Workplace Join**, type your email address and select **Join** to complete registering the device.

Pour désins inscrire et réenregistrer l’appareil sur Android, Portail d’entreprise :

1. Lancez Portail d’entreprise et allez sur **l’onglet** Appareils.
2. Sélectionnez l’appareil pour voir les détails de l’appareil.
3. Dans le menu points de sélection (trois points), sélectionnez Supprimer l’appareil **et** terminez la suppression en confirmant dans la boîte de dialogue.
4. Vous devez maintenant être déconnecté de l’application Portail d’entreprise’application. Sélectionnez **Se connectez** pour ré-inscrire l’appareil.

Pour plus d’informations sur les actions requises pendant la phase de migration de cette charge de travail, ou sur l’impact sur l’administration ou l’utilisation, examinez les informations sur Azure Active Directory (Azure AD) dans Des informations [Azure AD](ms-cloud-germany-transition-azure-ad.md)supplémentaires pour la migration à partir de Microsoft Cloud Deutschland .

## <a name="ios"></a>iOS

Sur les appareils iOS, un utilisateur doit supprimer manuellement tous les comptes mis en cache de l’Microsoft Authenticator, désinsister l’appareil et se dé dé connecter à partir de toutes les applications natives de l’appareil.

### <a name="step-1-if-present-remove-the-account-from-the-microsoft-authenticator-app"></a>Étape 1 : si elle est présente, supprimez le compte de l’application Microsoft Authenticator client

1. Appuyez sur le compte dans l Microsoft Authenticator appl;
2. Appuyez sur **Paramètres** icône dans le coin supérieur droit. Si vous ne voyez pas **l’icône Paramètres,** il se peut que vous n’utilisiez pas la dernière version de Microsoft Authenticator.
3. Appuyez sur **le bouton** Supprimer le compte.
4. Appuyez **sur toutes les applications sur cet appareil.**

### <a name="step-2-unregister-the-device-from-the-microsoft-authenticator-app"></a>Étape 2 : Désinsser l’appareil de l Microsoft Authenticator appel

1. Appuyez sur l’icône de menu dans le coin supérieur droit.
2. Appuyez **Paramètres** puis inscription **de l’appareil.**
3. Si votre compte s’affiche, **appuyez sur Désinsister l’appareil** et **continuez** dans la boîte de dialogue. Vous ne devriez voir aucun compte après cela.

### <a name="step-3-sign-out-from-individual-apps-if-necessary"></a>Étape 3 : Se sortir des applications individuelles si nécessaire

Les utilisateurs peuvent se rendre sur des applications individuelles telles que Outlook, Teams et OneDrive, et supprimer des comptes de ces applications.

## <a name="frequently-asked-questions"></a>Foire aux questions

**Comment savoir si mon organisation est affectée ?**

Les administrateurs doivent vérifier s’ils ont des appareils Azure AD inscrits ou joints `https://portal.microsoftazure.de` à Azure AD. Si votre organisation dispose d’appareils Azure AD inscrits ou joints à Azure AD, votre organisation doit suivre les instructions de cette page.

**Quand mes utilisateurs ré-inscrivent-ils leurs appareils ?**

Pour réussir, vous devez uniquement désins inscrire et réenregistrer vos appareils une fois la [phase 9](ms-cloud-germany-transition-phases.md#phase-9--10-azure-ad-finalization) terminée. Vous devez terminer la ré-inscription avant le démarrage de la phase 10, sinon vous risquez de perdre l’accès à votre appareil.

**Comment savoir que tous mes appareils sont inscrits dans le cloud public ?**

Pour vérifier si vos appareils sont enregistrés dans le cloud public, vous devez exporter et télécharger la liste des appareils à partir du portail Azure AD vers une feuille de calcul Excel. Ensuite, filtrez les appareils inscrits (à l’aide de la colonne _registeredTime)_ après la date à laquelle votre organisation a passé la phase 9 du [processus de migration.](ms-cloud-germany-transition-phases.md#phase-9--10-azure-ad-finalization)

**Dois-je toujours ajouter le nom DNS comme indiqué dans Créer des enregistrements DNS pour Microsoft à l’aide [Windows DNS ?](/microsoft-365/admin/dns/create-dns-records-using-windows-based-dns?view=o365-worldwide#add-two-cname-records-for-mobile-device-management-mdm-for-microsoft)**

Cette entrée DNS n’est plus nécessaire pour réen inscrire à nouveau votre appareil. 

## <a name="additional-considerations"></a>Considérations supplémentaires

> [!IMPORTANT]
> Le principal de service Intune sera activé après la [phase 3](ms-cloud-germany-transition-phases.md#phase-3-subscription-transfer)du processus de migration, ce qui implique l’activation d’Azure AD Device Registration. Si vous avez bloqué l’inscription des appareils Azure AD avant la migration, vous devez désactiver le principal de service Intune avec PowerShell pour désactiver à nouveau l’inscription des appareils Azure AD avec le portail Azure AD. Vous pouvez désactiver le principal de service Intune avec cette commande dans la Azure Active Directory PowerShell pour Graph module.

```powershell
Get-AzureADServicePrincipal -All:$true |Where-object -Property AppId -eq "0000000a-0000-0000-c000-000000000000" | Set-AzureADServicePrincipal -AccountEnabled:$false
```

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
