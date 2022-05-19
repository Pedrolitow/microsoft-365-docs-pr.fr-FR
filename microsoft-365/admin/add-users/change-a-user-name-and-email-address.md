---
title: Modifier un nom d’utilisateur et une adresse de messagerie
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
- AdminTemplateSet
- adminvideo
- business_assist
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: fb5ac074-e203-4e1f-9843-b9d1a3e03297
description: Découvrez comment un administrateur général Microsoft 365 peut modifier l’adresse e-mail et le nom complet d’un utilisateur lorsque son nom change.
ms.openlocfilehash: f48cbf3428988ce50b9f8913dd4f6c4e47858b2d
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65466721"
---
# <a name="change-a-user-name-and-email-address"></a>Modifier un nom d’utilisateur et une adresse de messagerie

Vous devrez peut-être modifier l’adresse de messagerie et le nom complet d’une personne si, par exemple, elle se marie et change son nom.

> [!TIP]
> Si vous avez besoin d’aide pour suivre les étapes de cette rubrique, envisagez de [collaborer avec un spécialiste des petites entreprises Microsoft](https://go.microsoft.com/fwlink/?linkid=2186871). Avec Aide aux entreprises, vos employés et vous avez accès 24 heures sur 24 aux spécialistes des petites entreprises à mesure que vous développez votre entreprise, de l’intégration à l’utilisation quotidienne.

## <a name="watch-change-a-users-name-or-email-address"></a>Regardez : modifier le nom ou l’adresse de courrier d’un utilisateur

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1SJuc]

1. Dans la Centre d'administration Microsoft 365, sélectionnez **Utilisateurs** > <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">**actifs**</a>.
1. Sélectionnez l’utilisateur dans la liste des utilisateurs actifs.
1. Sélectionnez **Gérer les informations de contact**.
1. Modifiez le nom complet, puis sélectionnez **Enregistrer les modifications**.

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](../../business-video/index.yml).

## <a name="before-you-begin"></a>Avant de commencer

Vous devez être un[administrateur général](about-admin-roles.md) pour effectuer ces étapes.

## <a name="change-a-users-email-address"></a>Modifier l’adresse de courrier d’un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

1. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer le nom d’utilisateur**.

1. Dans la première case, saisissez la première partie de la nouvelle adresse e-mail. Si vous avez ajouté votre propre domaine à Microsoft 365, choisissez le domaine du nouvel alias de messagerie à l'aide de la liste déroulante. [Découvrez comment ajouter un domaine](../setup/add-domain.md).

1. Sélectionnez **Enregistrer les modifications**.

> [!IMPORTANT]
> IMPORTANT : Si vous recevez un message d’erreur, consultez la rubrique [Résolution des messages d’erreur](#resolve-error-messages).

## <a name="set-the-primary-email-address"></a>Définition de l’adresse de courrier principale

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les alias de courrier**.

3. Sélectionnez **Définir comme principale** pour l'adresse de courrier que vous souhaitez définir comme adresse principale pour cette personne.

   > [!IMPORTANT]
   > IMPORTANT : l’option Définir comme principale n’apparaît pas si vous avez acheté Microsoft 365 auprès de GoDaddy ou d’un autre service partenaire qui fournit une console de gestion. Au lieu de cela, connectez-vous à la console de gestion de GoDaddy ou du partenaire pour définir l’alias principal.
   >
   > De même, cette option n’apparaît que si vous êtes un administrateur général. Si elle n’apparait pas, vous n’êtes pas autorisé à modifier le nom et l’adresse de messagerie principale d’un utilisateur.

4. Vous verrez un gros avertissement jaune indiquant que vous êtes sur le point de modifier les informations de connexion de la personne. Sélectionnez **Enregistrer**, puis **Fermer**.

5. Communiquez les informations suivantes à la personne :

   - Cette modification peut prendre du temps.

   - Son nouveau nom d’utilisateur. Elle en aura besoin pour se connecter à Microsoft 365.

   - Si cette personne utilise Skype Entreprise Online, elle devra replanifier les réunions Skype Entreprise Online qu'elle a organisées et demander à ses contacts externes de mettre à jour les anciennes informations de contact la concernant.

   - Si cette personne utilise OneDrive, l’URL de cet emplacement a été modifiée. Si cette personne a des blocs-notes OneNote dans son espace OneDrive, elle aura sans doute besoin de les fermer, puis de les rouvrir dans OneNote. Si cette personne a des fichiers partagés provenant de son OneDrive, les liens vers les fichiers risquent de ne pas fonctionner et l’utilisateur peut partager de nouveau.

   - Si son mot de passe change aussi, elle sera invitée à entrer le nouveau mot de passe sur son appareil mobile ; sinon, la synchronisation ne sera pas effectuée.

## <a name="change-a-users-display-name"></a>Modifier le nom d’affichage d’un utilisateur

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>. 

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Sélectionnez le nom de l’utilisateur, puis sous l’onglet **Compte**, sélectionnez **Gérer les informations de contact**.

3. Dans la zone **Nom d’affichage**, tapez un nouveau nom pour la personne, puis sélectionnez **Enregistrer**.

   Si le message d'erreur « **Impossible de modifier l'utilisateur. Vérifiez les informations sur l'utilisateur et réessayez** » apparaît, voir [Résolution des messages d’erreur](#resolve-error-messages).

L'application de cette modification dans tous les services peut prendre jusqu'à 24 heures. Une fois la modification appliquée, la personne devra se connecter à Outlook, à Skype Entreprise et à SharePoint avec son nom d'utilisateur mis à jour.

## <a name="resolve-error-messages"></a>Résolution des messages d'erreur

### <a name="a-parameter-cannot-be-found-that-matches-parameter-name-emailaddresses"></a>« Impossible de trouver un paramètre correspondant au nom "EmailAddresses" »

Si le message d’erreur « **Impossible de trouver un paramètre correspondant au nom ’EmailAddresses** » s’affiche, cela signifie qu’il faut un peu plus de temps pour configurer votre client, ou votre domaine personnalisé si vous venez d’en ajouter un. Le processus de configuration peut prendre jusqu’à 4 heures. Patientez le temps que le processus de configuration ait le temps de terminer, puis réessayez. Si le problème persiste, appelez le [support](../../business-video/get-help-support.md) et demandez-lui d’effectuer une synchronisation complète pour vous.

### <a name="were-sorry-the-user-couldnt-be-edited-review-the-user-information-and-try-again"></a>«Nous sommes désolés, l'utilisateur n'a pas pu être édité. Vérifiez les informations de l'utilisateur et réessayez»

Si vous recevez le message **d’erreur « Nous sommes désolés, l’utilisateur n’a pas pu être modifié. Passez en revue les informations utilisateur et réessayez**. Cela signifie que vous n’êtes pas un administrateur général et que vous n’êtes pas autorisé à modifier le nom d’utilisateur. Recherchez l’administrateur général dans votre entreprise et demandez-lui d’apporter la modification.

## <a name="what-to-do-with-old-email-addresses"></a>Procédure à suivre avec les anciennes adresses de courrier

L’ancienne adresse e-mail principale d’une personne est conservée en tant qu’adresse e-mail supplémentaire. **Nous vous conseillons vivement de ne pas supprimer l’ancienne adresse de courrier.**

Certains continueront sans doute à envoyer des e-mails à l’ancienne adresse de la personne. Le fait de la supprimer risque d’entraîner la génération de notifications d’échec de remise. Microsoft l’achemine automatiquement vers la nouvelle adresse. De plus, évitez de réutiliser d’anciennes adresses e-mail SMTP et de les appliquer aux nouveaux comptes. Cela peut également provoquer la génération de notifications d’échec de remise ou la remise à une boîte aux lettres inattendue.

## <a name="what-if-the-persons-offline-address-book-wont-sync-with-the-global-address-list"></a>Que se passe-t-il si le carnet d’adresses en mode hors connexion d’une personne ne parvient pas à se synchroniser avec la liste d’adresses globale ?

Si une personne utilise Exchange Online ou si son compte est lié à l’environnement Exchange local de votre organisation, vous risquez de rencontrer cette erreur lorsque vous essayez de modifier un nom d’utilisateur et une adresse de messagerie : « Cet utilisateur est synchronisé avec votre environnement Active Directory local. Certains détails peuvent uniquement être modifiés via votre environnement Active Directory local. »

Cela est dû à l'adresse MOERA (Microsoft Online Email Routing Address). L'adresse MOERA est construite à partir de l'attribut _userPrincipalName_ de la personne dans Active Directory et est automatiquement attribuée au compte cloud lors de la synchronisation initiale. Une fois attribuée, elle ne peut plus être modifiée ou supprimée dans Microsoft 365. Vous pouvez ensuite modifier le nom d'utilisateur dans l'annuaire Active Directory, mais cela ne modifie pas l'adresse MOERA et vous risquez de rencontrer des problèmes lors de l'affichage du nom nouvellement modifié dans la liste d'adresses globale.

Pour résoudre ce problème, connectez-vous au module [Azure Active Directory Domain Services pour PowerShell](https://go.microsoft.com/fwlink/?LinkId=823193) avec vos informations d'identification d'administrateur Microsoft 365. et utilisez la syntaxe suivante :

```powershell
Set-MsolUserPrincipalName -UserPrincipalName anne.wallace@contoso.onmicrosoft.com -NewUserPrincipalName anne.jones@contoso.com
```

> [!TIP]
> Cela modifie l’attribut **userPrincipalName** de la personne et n’a aucune incidence sur son adresse de messagerie MoERA (Microsoft Online Email Routing Address). Toutefois, il est recommandé que l’UPN d’ouverture de session de la personne corresponde à son adresse SMTP principale.

Pour découvrir comment modifier le nom d'utilisateur de quelqu'un dans Active Directory, dans Windows Server 2003 et version ultérieure, voir [Renommer un compte d'utilisateur](/previous-versions/windows/it-pro/windows-server-2003/cc772952(v=ws.10)).

## <a name="related-content"></a>Contenu associé

[Ajouter un domaine](../setup/add-domain.md)
[Admins : réinitialiser un mot de passe pour un ou plusieurs utilisateurs](reset-passwords.md)
[Ajouter une autre adresse e-mail à un utilisateur](../email/add-another-email-alias-for-a-user.md)
[Créer une boîte aux lettres partagée](../email/create-a-shared-mailbox.md)
