---
title: Supprimer un ancien employé
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- SPO_Content
ms.custom:
- MSStore_Link
- TRN_M365B
- OKR_SMB_Videos
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 44d96212-4d90-4027-9aa9-a95eddb367d1
description: 'Suivez cette liste de vérification pour supprimer un employé de Microsoft 365 et sécuriser les données. '
ms.openlocfilehash: 2372056cd6bee2387842c74dc2a35d71b88fae9e
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50904395"
---
# <a name="remove-or-delete-a-former-employee"></a>Supprimer ou supprimer un ancien employé

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](../microsoft-365-admin-center-preview.md?preserve-view=true&view=o365-21vianet).

::: moniker-end
  
## <a name="sign-out-now"></a>Déconnectez maintenant !

::: moniker range="o365-worldwide"

Regardez une courte vidéo sur la suppression d’un employé. <br><br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE1FOfR] 

Si vous avez trouvé cette vidéo utile, consultez les [séries de formations complètes pour les petites entreprises et les nouveaux utilisateurs de Microsoft 365](https://support.microsoft.com/office/6ab4bbcd-79cf-4000-a0bd-d42ce4d12816).

Pour empêcher un employé de se connecter :

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez la case à côté du nom de l’utilisateur, puis sélectionnez **Réinitialiser le mot de passe.**
3. Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser.** (Ne leur envoyez pas de message.)
4. Sélectionnez le nom de l’utilisateur pour aller  dans le volet de propriétés, puis sous l’onglet Compte, sélectionnez Lancer **la signature.**

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’utilisateur, puis **réinitialisez le mot de passe.**

3. Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser.** (Ne leur envoyez pas de message.)

4. Sélectionnez le nom de l’utilisateur pour aller  dans le volet de propriétés, puis sous l’onglet Compte, sélectionnez Lancer **la signature.**

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’utilisateur, puis **réinitialisez le mot de passe.**

3. Entrez un nouveau mot de passe, puis sélectionnez **Réinitialiser.** (Ne leur envoyez pas de message.)

4. Sélectionnez le nom de l’utilisateur pour aller  dans le volet de propriétés, puis sous l’onglet Compte, sélectionnez Lancer **la signature.**

::: moniker-end

> [!NOTE]
> Vous devez être un administrateur général pour lancer la signature.

Dans un délai d’une heure (ou après avoir quitté la page Microsoft 365 actuelle), ils sont invités à se ré-inscrire. Un jeton d’accès est bon pendant une heure, donc la chronologie dépend du temps qui reste sur ce jeton et de la façon dont il quitte la page web actuelle.
  
> [!IMPORTANT]
> Si l’utilisateur se trouve dans Outlook sur le web, il se peut qu’il ne soit pas immédiatement mis hors de l’application en cliquant dans sa boîte aux lettres. Dès qu’ils sélectionnent une autre vignette, telle que OneDrive, ou actualisent leur navigateur, la signature est lancée.
  
Pour utiliser PowerShell afin de déconnecter un utilisateur immédiatement, voir l'applet de commande [Revoke-AzureADUserAllRefreshToken](/powershell/module/azuread/revoke-azureaduserallrefreshtoken).
  
Pour plus d'informations sur le temps nécessaire pour supprimer l'accès d'un utilisateur au courrier électronique, voir [Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé](#what-you-need-to-know-about-terminating-an-employees-email-session).
  
## <a name="overview-of-all-the-steps-to-remove-an-employee-and-secure-data"></a>Vue d'ensemble de la procédure de suppression d'un employé et des données sécurisées

Nous avons souvent la question suivante : « Que dois-je faire pour protéger les données lorsqu’un employé quitte l’organisation ? » Cet article explique comment bloquer l’accès à Microsoft 365 et les étapes à suivre pour sécuriser vos données.
  
> [!NOTE]
> Si vous êtes un administrateur général, vous pouvez supprimer l’employé, envoyer son courrier électronique, choisir ce qu’il faut faire avec son contenu OneDrive à l’aide de la nouvelle expérience guidée. Pour plus d’informations, [voir Administrateur global : Supprimer un utilisateur.](remove-former-employee.md) Toutefois, nous vous recommandons d’effectuer toutes les étapes supplémentaires répertoriées ici pour vous assurer que l’employé n’a pas accès aux données de votre entreprise. 
  
En voici un résumé. Chaque étape est expliquée en détail dans cet article.
  
|||
|:-----|:-----|
|**Étape** <br/> |**Raison** <br/> |
|1. [Enregistrer le contenu de la boîte aux lettres d'un ancien employé](#save-the-contents-of-a-former-employees-mailbox) <br/> |Cela est utile pour la personne qui va reprendre le travail de l’employé, ou en cas de litige.  <br/> |
|2. [Transférer l'adresse e-mail d'un ancien employé à un autre employé ou la convertir en boîte aux lettres partagée](#forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox) <br/> |Cette étape vous permet de conserver l'adresse e-mail de l'ancien employé. Si certains de vos clients ou partenaires continuent d'envoyer du courrier à l'adresse de l'ancien employé, celui-ci est reçu par son remplaçant.  <br/> |
|3. [Réinitialiser et bloquer l'appareil mobile d'un ancien employé](#wipe-and-block-a-former-employees-mobile-device) <br/> |Cette étape supprime vos données professionnelles du téléphone ou de la tablette.  <br/> |
|4. [Bloquer l’accès d’un ancien employé aux données Microsoft 365](#block-a-former-employees-access-to-microsoft-365-data)<br/> |Cela empêche la personne d’accéder à son ancienne boîte aux lettres et données Microsoft 365.  <br/><br/> **Conseil**: lorsque vous bloquez l’accès d’un utilisateur, vous payez toujours pour sa licence. Pour arrêter de payer, supprimez la licence de votre abonnement (étape 5).  |
|5. [Déplacer le contenu OneDrive de l'employé](get-access-to-and-back-up-a-former-user-s-data.md) <br/> |Si vous supprimez uniquement la licence d'un utilisateur, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours.  <br/><br/> Avant de supprimer le compte, vous devez déplacer le contenu de son espace OneDrive à un autre emplacement qui vous est aisément accessible. Après avoir supprimé le compte d'un employé, le contenu de son espace OneDrive est conservé pendant **30** jours. Pendant ce temps, vous pouvez toutefois restaurer le compte de l'utilisateur et accéder à son contenu OneDrive. Si vous restaurez le compte de l'utilisateur, vous pouvez toujours accéder au contenu dans OneDrive même après 30 jours.  <br/> |
|5a. Que se passe si quelqu'un utilise son ordinateur personnel pour accéder à OneDrive et SharePoint ?  <br/> |Si quelqu'un utilise son ordinateur personnel au lieu d'un ordinateur fourni par la société pour télécharger des fichiers à partir de OneDrive et SharePoint, il n'y a aucun moyen pour vous d'effacer les fichiers que cette personne a stockés.  <br/><br/> Ils ont toujours accès à tous les fichiers qui ont été synchronisés avec leur ordinateur.  <br/> |
|6. [Supprimer et supprimer la licence Microsoft 365 d’un ancien employé](#remove-and-delete-the-microsoft-365-license-from-a-former-employee)<br/> |Si vous retirez une licence, vous pouvez l'affecter à quelqu'un d'autre. Vous pouvez également supprimer la licence pour ne plus payer pour celle-ci jusqu'à ce que vous embauchiez une autre personne.  <br/><br/> Lorsque vous retirez ou supprimez une licence, les anciens courriers, les contacts et le calendrier de l'utilisateur sont conservés pendant **30 jours** avant d'être supprimés définitivement. Si vous retirez ou supprimez une licence, mais pas le compte, vous pouvez toujours accéder au contenu enregistré dans l'espace OneDrive de l'utilisateur même après 30 jours.  <br/> |
|7. [Supprimer le compte d'utilisateur d'un ancien employé](#delete-a-former-employees-user-account)<br/> |Cela supprime le compte de votre centre d’administration. Ainsi, les choses restent claires et bien organisées.  <br/> |

## <a name="save-the-contents-of-a-former-employees-mailbox"></a>Enregistrer le contenu de la boîte aux lettres d'un ancien employé

Il existe deux façons d'enregistrer le contenu de la boîte aux lettres de l'ancien employé :
  
1. Ajoutez les adresses de courrier de l'ancien employé à votre version d'Outlook 2013 ou 2016, puis exportez les données vers un fichier .pst. Si nécessaire, vous pouvez importer les données dans un autre compte de courrier. Pour savoir comment procéder, voir [Accéder aux données d'un ancien utilisateur et les sauvegarder](get-access-to-and-back-up-a-former-user-s-data.md).

    OU

2. Placez une conservation pour litige ou une conservation inaltérable sur la boîte aux lettres avant de supprimer le compte d'utilisateur. La mise en place de cette option est beaucoup plus compliquée que la mise en place de la première option, mais elle peut s'avérer très utile si : votre offre Entreprise inclut les fonctionnalités d'archivage et de conservation légale, la mise en place de la conservation pour litige est envisageable et si vous disposez d'un service informatique compétent au niveau technique.

    Après avoir converti la boîte aux lettres en « boîte aux lettres inactive », les administrateurs, les responsables de la mise en conformité ou les gestionnaires d’enregistrements peuvent utiliser les outils eDiscovery de In-Place dans Exchange Online pour accéder au contenu et y effectuer des recherches.

    Les boîtes aux lettres inactives ne peuvent pas recevoir de courriers, et n'apparaissent pas dans le carnet d'adresses partagé de votre organisation ou d'autres listes.

    Pour savoir comment placer une boîte aux lettres en attente, voir Gérer les boîtes aux lettres [inactives dans Exchange Online.](../../compliance/create-and-manage-inactive-mailboxes.md)

## <a name="forward-a-former-employees-email-to-another-employee-or-convert-to-a-shared-mailbox"></a>Transférer l'adresse e-mail d'un ancien employé à un autre employé ou la convertir en boîte aux lettres partagée

Au cours de cette étape, vous allez affecter l'adresse de courrier de l'ancien employé à un autre employé, ou [convertir la boîte aux lettres de l'utilisateur en boîte aux lettres partagée](../email/convert-user-mailbox-to-shared-mailbox.md) que vous avez créée.
  
- La création d'une boîte aux lettres partagée est la solution la plus économique car aucune licence payante n'est requise **tant que la boîte aux lettres ne dépasse pas les 50 Go**. Au-delà de 50 Go, vous devrez acheter une licence.
- Si vous convertissez la boîte aux lettres en boîte aux lettres partagée, les anciens courriers seront également disponibles. Ceux-ci peuvent occuper beaucoup d'espace.
- Si vous transférez le courrier, seuls les  *nouveaux*  messages adressés à l'ancien employé seront envoyés à l'employé actuel.

 > [!IMPORTANT]
 > Si vous programmez le forwarding de courrier ou une boîte aux lettres partagée, à la fin, ne supprimez pas le compte de l’ancien employé. Le compte doit être présent pour ancrer la boîte aux lettres partagée ou de forwarding de courrier électronique.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sélectionnez **l’onglet** Courrier.
3. Under **Email Forwarding**, select **Manage email forwarding**.
4. Activez l'option **Transférer tous les messages envoyés à cette boîte aux lettres**. Dans la **zone d’adresse de** forwarding, tapez l’adresse e-mail de l’employé actuel qui va obtenir le courrier électronique.
5. Sélectionnez **Enregistrer**.
6. Souvenez-vous que vous ne devez pas supprimer le compte de l'ancien employé.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’employé que vous souhaitez bloquer et développez **Paramètres de messagerie.**

3. En plus **du forwarding de courrier électronique,** sélectionnez **Modifier.**

4. Activez l'option **Transférer tous les messages envoyés à cette boîte aux lettres**. Dans le champ **dresse de transfert**, tapez l'adresse de courrier de l'employé actuel (ou de la boîte aux lettres partagée) qui va recevoir le courrier.
  
5. Sélectionnez **Enregistrer**.

6. Souvenez-vous que vous ne devez pas supprimer le compte de l'ancien employé.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’employé que vous souhaitez bloquer et développez **Paramètres de messagerie.**

3. En plus **du forwarding de courrier électronique,** sélectionnez **Modifier.**

4. Activez l'option **Transférer tous les messages envoyés à cette boîte aux lettres**. Dans le champ **dresse de transfert**, tapez l'adresse de courrier de l'employé actuel (ou de la boîte aux lettres partagée) qui va recevoir le courrier.
  
5. Sélectionnez **Enregistrer**.

6. Souvenez-vous que vous ne devez pas supprimer le compte de l'ancien employé.

::: moniker-end

## <a name="wipe-and-block-a-former-employees-mobile-device"></a>Réinitialiser et bloquer l'appareil mobile d'un ancien employé

Si votre ancien employé avait un téléphone d’organisation, vous pouvez utiliser le Centre d’administration Exchange pour effacer et bloquer cet appareil afin que toutes les données de l’organisation ne se connectent plus à Office 365.

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.
2. Dans le Centre d'administration Exchange, accédez à **Destinataires** \> **Boîtes aux lettres**.
3. Sélectionnez l’utilisateur, puis sous **Appareils mobiles,** **sélectionnez Afficher les détails.**
4. Dans la page **Détails de l’appareil** mobile, sous **Appareils** mobiles, sélectionnez l’appareil mobile, sélectionnez Effacer le périphérique de effacement ![ des données, puis ](../../media/1c113a36-53cb-4974-884f-3ecd9535506e.png) bloquer . 
5. Sélectionnez **Enregistrer**.
   > [!TIP]
   > Assurez-vous de supprimer ou de désactiver l’utilisateur de votre service Blackberry Enterprise Local. Vous devez également désactiver les appareils Blackberry de l'utilisateur. Reportez-vous au guide d'administration des services Blackberry Business Cloud Services pour consulter les étapes spécifiques relatives à la désactivation de l'utilisateur.

## <a name="block-a-former-employees-access-to-microsoft-365-data"></a>Bloquer l’accès d’un ancien employé aux données Microsoft 365

 > [!IMPORTANT]
 > Le blocage d’un compte peut prendre jusqu’à 24 heures. Si vous devez empêcher immédiatement l’accès à [](reset-passwords.md) la session d’un utilisateur, vous devez réinitialiser son mot de passe, puis lancer un événement unique qui le permettra de se sortir des sessions Microsoft 365 sur tous les appareils. Voir [Déconnectez maintenant !](#sign-out-now)

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sous le nom de l’utilisateur, sélectionnez le symbole Bloquer **cet utilisateur.**
3. Sélectionnez **Bloquer la signature de l’utilisateur,** puis sélectionnez **Enregistrer.**

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’employé que vous souhaitez bloquer, puis sélectionnez Bloquer **la signature.**

3. Sélectionnez **Bloquer la signature de l’utilisateur,** puis sélectionnez **Enregistrer.**

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’employé que vous souhaitez bloquer, puis sélectionnez Bloquer **la signature.**

3. Sélectionnez **Bloquer la signature de l’utilisateur,** puis sélectionnez **Enregistrer.**

::: moniker-end

## <a name="block-a-former-employees-access-to-email-exchange-online"></a>Bloquer l'accès d'un ancien employé aux courriers (Exchange Online)

Si vous avez du courrier électronique dans le cadre de votre abonnement Microsoft 365, vous devez vous inscrire au Centre d’administration Exchange pour suivre ces étapes afin d’empêcher votre ancien employé d’accéder à sa messagerie électronique.
  
1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.
2. Dans le Centre d'administration Exchange, accédez à **Destinataires** \> **Boîtes aux lettres**.
3. Double-cliquez sur l’utilisateur et consultez la page **Fonctionnalités de boîte aux lettres.** Sous **Appareils mobiles,** sélectionnez Désactiver Exchange ActiveSync et Désactiver OWA pour les   **appareils,** puis répondez Oui aux deux lorsque vous y avez été invité.
4. Sous **Connectivité de messagerie,** **sélectionnez Désactiver et** **répondez Oui** à l’invite.

## <a name="remove-and-delete-the-microsoft-365-license-from-a-former-employee"></a>Supprimer et supprimer la licence Microsoft 365 d’un ancien employé

Ainsi, vous ne continuez pas à payer pour une licence après qu’une personne a quitté votre organisation, vous devez supprimer sa licence Microsoft 365, puis la supprimer de votre abonnement. Si vous décidez de ne pas supprimer la licence de votre abonnement, vous pouvez l'affecter à un autre utilisateur.
  
Lorsque vous effectuez cette opération, toutes les données de cet utilisateur sont conservées pendant 30 jours. Vous pouvez [accéder](get-access-to-and-back-up-a-former-user-s-data.md) aux données, ou [restaurer](restore-user.md) le compte si l'utilisateur revient. Après 30 jours, toutes les données de l’utilisateur (à l’exception des documents stockés sur SharePoint Online) sont définitivement supprimées de Microsoft 365 et ne peuvent pas être récupérées.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé que vous souhaitez bloquer, puis sélectionnez l’onglet **Licences et** applications.
3. Clear the check boxes for the license(s) you want to remove, and then select **Save changes**.

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’employé que vous souhaitez bloquer, puis en côté des **licences de produit,** sélectionnez **Modifier**.

3. Dans la page **Licences de produits,** désélecez les licences que vous souhaitez supprimer, puis sélectionnez **Enregistrer.**

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez l’employé que vous souhaitez bloquer, puis en côté des **licences de produit,** sélectionnez **Modifier**.

3. Dans la page **Licences de produits,** désélecez les licences que vous souhaitez supprimer, puis sélectionnez **Enregistrer.**

::: moniker-end

**Pour réduire le nombre de licences que vous** payez jusqu’à ce que vous recrutiez une autre personne, vous devez suivre les étapes suivantes :

::: moniker range="o365-worldwide"
1. Dans le Centre d’administration, allez sur **la** page Facturation de vos \> <a href="https://go.microsoft.com/fwlink/p/?linkid=842054" target="_blank">produits,</a> puis sélectionnez **l’onglet Produits.**
2. Sélectionnez l’abonnement dont vous souhaitez supprimer des licences.
3. Dans la page de détails, **sélectionnez Supprimer des licences.**
4. Dans le **volet Supprimer des licences,** sous Nouvelle quantité, dans la zone Nombre total de **licences,** entrez le nombre total de licences que vous souhaitez pour cet abonnement. Par exemple, si vous avez 25 licences et que vous souhaitez en supprimer une, entrez 24.
5. Sélectionnez **Enregistrer**.
::: moniker-end

::: moniker range="o365-germany"
1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847745" target="_blank">Abonnements</a>.
2. Sélectionnez **Ajouter/Supprimer des licences pour** supprimer la licence afin de ne pas payer pour cette licence tant que vous n’avez pas embauché une autre personne.
::: moniker-end

::: moniker range="o365-21vianet"
1. Dans le centre d’administration, accédez à la page **Facturation** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850626" target="_blank">Abonnements</a>.
2. Sélectionnez **Ajouter/Supprimer des licences pour** supprimer la licence afin de ne pas payer pour cette licence tant que vous n’avez pas embauché une autre personne.
::: moniker-end

Lorsque vous [ajoutez une autre](add-users.md) personne à votre entreprise, vous êtes invité à acheter une licence en même temps, en une seule étape !

Pour plus d’informations sur la gestion des licences utilisateur pour Microsoft 365 pour les entreprises, voir Attribuer des licences aux utilisateurs dans [Microsoft 365](../manage/assign-licenses-to-users.md)pour les entreprises et Désattribuer des licences à des utilisateurs dans [Microsoft 365](../manage/remove-licenses-from-users.md)pour les entreprises.
  
## <a name="how-the-deleted-employee-account-affects-skype-for-business"></a>Comment le compte supprimé d'un employé affecte Skype Entreprise

Lorsque vous supprimez une licence d'utilisateur d'Office 365, le numéro d'appel PSTN associé à l'utilisateur est libéré. Vous pouvez l'assigner à un autre utilisateur.
  
Si l'utilisateur appartient à un groupe de files d'attente, il ne sera plus une cible viable des agents de la file d'attente d'appels. Nous recommandons donc de supprimer également l'utilisateur des groupes associés à la file d'attente d'appels.

## <a name="set-up-call-forwarding-to-people-in-your-organization"></a>Configurer le forwarding d’appel vers des personnes de votre organisation

Si vous devez configurer le transfert d’appel pour le numéro de téléphone de l’employé licencié, le paramètre de transfert d’appel sous stratégies d’appel peut configurer le transfert dans lequel les appels entrants peuvent être transmis à d’autres utilisateurs ou faire sonner une autre personne en même temps. Pour plus d’informations, voir [Stratégies d’appel dans Microsoft Teams.](/microsoftteams/teams-calling-policy)
  
## <a name="delete-a-former-employees-user-account"></a>Supprimer le compte d'utilisateur d'un ancien employé

Une fois que vous avez enregistré et consulté les données utilisateur de l'ancien employé, vous pouvez supprimer le compte de l'ancien employé.
  
Ne supprimez pas le compte si vous avez configuré le transfert de courrier ou si vous l'avez converti en boîte aux lettres partagée. Les deux ont besoin du compte pour ancrer le transfert ou la boîte aux lettres partagée.

::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
2. Sélectionnez le nom de l’employé à supprimer.
3. Sous le nom de l’utilisateur, sélectionnez le symbole **Supprimer l’utilisateur.** Choisissez les options que vous souhaitez pour cet utilisateur, puis sélectionnez **Supprimer l’utilisateur.**

::: moniker-end

::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez le nom de l’employé à supprimer.

3. En haut de la page, sélectionnez **Supprimer l’utilisateur.** Choisissez les options que vous souhaitez pour cet utilisateur, puis sélectionnez **Supprimer l’utilisateur.**

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs >** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Sélectionnez le nom de l’employé à supprimer.

3. En haut de la page, sélectionnez **Supprimer l’utilisateur.** Choisissez les options que vous souhaitez pour cet utilisateur, puis sélectionnez **Supprimer l’utilisateur.**

::: moniker-end

Lorsque vous supprimez un utilisateur, le compte devient inactif pendant 30 jours environ. Vous disposez de cette durée pour restaurer le compte avant sa suppression définitive.
  
### <a name="does-your-organization-use-active-directory"></a>Votre organisation utilise Active Directory ?

Si votre organisation synchronise les comptes d’utilisateurs avec Microsoft 365 à partir d’un environnement Active Directory local, vous devez supprimer et restaurer ces comptes d’utilisateurs dans votre service Active Directory local. Vous ne pouvez pas les supprimer et les restaurer dans Office 365.
  
Pour découvrir comment supprimer et restaurer un compte d’utilisateur dans Active Directory, voir [Supprimer un compte d’utilisateur.](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/cc753730(v=ws.11))
  
Si vous utilisez Azure Active Directory, consultez l’cmdlet [Remove-MsolUser](https://go.microsoft.com/fwlink/?linkid=842230) PowerShell.
  
## <a name="what-you-need-to-know-about-terminating-an-employees-email-session"></a>Ce que vous devez savoir sur la clôture d'une session de messagerie d'un employé

Voici les informations sur la suppression de l'accès d'un employé au courrier électronique (Exchange).
  
|||
|:-----|:-----|
|**Ce que vous pouvez faire** <br/> |**Procédure à suivre** <br/> |
|Clôturer une session (par exemple, Outlook sur le web, Outlook, Exchange Active Sync, etc.) et forcer à ouvrir une nouvelle session  <br/> |Réinitialiser le mot de passe  <br/> |
|Clôturer une session et bloquer les sessions suivantes (pour tous les protocoles)  <br/> |Désactivez le compte. Par exemple, (dans le Centre d’administration Exchange ou à l’aide de PowerShell) :  <br/>  `Set-Mailbox user@contoso.com -AccountDisabled:$true` <br/> |
|Clôturer la session pour un protocole particulier (par exemple, ActiveSync)  <br/> |Désactivez le protocole. Par exemple, (dans le Centre d’administration Exchange ou à l’aide de PowerShell) :  <br/>  `Set-CASMailbox user@contoso.com -ActiveSyncEnabled:$false` <br/> |

Les opérations ci-dessus peuvent être réalisées à trois endroits :
  
|||
|:-----|:-----|
|**Si vous clôturez la session ici** <br/> |**Temps nécessaire** <br/> |
|Dans le centre d'administration Exchange ou à l'aide de PowerShell  <br/> |Le délai prévu est de moins de 30 minutes  <br/> |
|Dans le centre d'administration Azure Active Directory  <br/> |Le délai prévu est de 60 minutes  <br/> |
|Dans un environnement local  <br/> |Le délai prévu est de 3 heures ou plus  <br/> |

### <a name="how-to-get-fastest-response-for-account-termination"></a>Comment obtenir une réponse plus rapide à une demande de clôture de compte

 **Plus rapide**: utilisez le centre d'administration Exchange (avec PowerShell) ou le centre d'administration Azure Active Directory. Dans un environnement local, la synchronisation de la modification via DirSync peut prendre plusieurs heures.
  
 **Plus rapide pour un utilisateur ayant une présence locale et dans le centre de données Exchange**: clôturez la session via le centre d'administration Azure Active Directory/Exchange ET apportez la modification aussi dans l'environnement local. À défaut, la modification dans le centre d'administration Azure Active Directory/Exchange est remplacée par DirSync.
  
## <a name="related-articles"></a>Articles connexes

[Restaurer un utilisateur](restore-user.md)