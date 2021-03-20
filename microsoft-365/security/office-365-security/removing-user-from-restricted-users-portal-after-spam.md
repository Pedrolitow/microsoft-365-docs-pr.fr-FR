---
title: Retirer les utilisateurs bloqués du portail des utilisateurs restreints
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
f1_keywords:
- ms.exch.eac.ActionCenter.Restricted.Users.RestrictedUsers
localization_priority: Priority
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent découvrir comment supprimer des utilisateurs du portail des utilisateurs restreints dans Office 365. Les utilisateurs sont ajoutés au portail Utilisateurs restreints pour avoir envoyé du courrier indésirable sortant, généralement en raison de la compromission d’un compte.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 2b4f77f1edf0024a0324736adb2a8bfd6cc51470
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50908217"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-office-365"></a>Retirer les utilisateurs bloqués du portail Utilisateurs restreints dans Office 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

Si un utilisateur dépasse l’une des limites d’envoi sortant, comme spécifié dans [les limites de service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou dans [les stratégies anti-courrier indésirable sortantes](configure-the-outbound-spam-policy.md), l’utilisateur ne peut pas envoyer d’e-mails, mais il peut continuer à en recevoir.

L’utilisateur est ajouté au portail Utilisateurs restreints dans le Centre de sécurité et conformité. Lorsqu’il essaie d’envoyer des e-mail, le message est renvoyé dans une notification d’échec de remise (ou notification de non-remise) avec le code d’erreur [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) et le texte suivant :

> «Votre message n’a pas pu être remis parce que vous n’avez pas été reconnu comme expéditeur valide. Le plus souvent, il est possible que votre adresse de messagerie soit susceptible d’envoyer du courrier indésirable et qu’elle ne soit plus autorisée à envoyer du courrier électronique.  Contactez votre administrateur pour obtenir de l’aide. Le serveur distant a renvoyé' 550 5.1.8 accès refusé, expéditeur sortant incorrect».

Les administrateurs peuvent supprimer des utilisateurs du portail Expéditeurs restreints dans le centre de sécurité et conformité ou dans Exchange Online PowerShell.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Centre de sécurité et conformité sur <https://protection.office.com/>. Pour accéder directement à la page **Utilisateurs restreints**, utilisez <https://protection.office.com/restrictedusers>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour supprimer des utilisateurs du portail Utilisateurs restreints, vous devez être membre des groupes de rôles **Management de l’organisation** ou **Administrateur de sécurité**.
  - Pour l’accès en lecture seule au portail Utilisateurs restreints, vous devez être membre du groupe de rôles **Lecteur global** ou **Lecteur de sécurité**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Un expéditeur dépassant la limite du nombre de messages sortants est un indicateur de compte compromis. Avant de supprimer l’utilisateur du portail Utilisateurs restreints, veillez à suivre les étapes nécessaires pour reprendre le contrôle de son compte. Pour plus informations, voir [Réponse à un compte de messagerie compromis dans Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-security--compliance-center-to-remove-a-user-from-the-restricted-users-list"></a>Utiliser le Centre de sécurité et conformité pour supprimer un utilisateur de la liste Utilisateurs restreints

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Examiner** \> **Utilisateurs restreints**.

2. Recherchez et sélectionnez l’utilisateur que vous souhaitez débloquer. Dans la colonne **Actions**, cliquez sur **Débloquer**.

3. Une fenêtre permet d’accéder aux informations relatives au compte dont l’envoi est restreint. Nous vous conseillons de suivre les recommandations afin de vous assurer que vous effectuez les actions appropriées au cas où le compte serait réellement compromis. Sélectionnez **Suivant** lorsque vous avez terminé.

4. L’écran suivant comporte des recommandations pour empêcher toute compromission ultérieure. L’activation de l’authentification multifacteur (MFA) et la modification des mots de passe constituent une bonne défense. Lorsque vous avez terminé, cliquez sur **débloquer l’utilisateur**.

5. Cliquez sur **Oui** pour confirmer la modification.

   > [!NOTE]
   > La suppression de toutes les restrictions de l’utilisateur peut prendre jusqu’à 24 heures.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Vérifier les paramètres d’alerte pour les utilisateurs restreints

La stratégie d’alerte par défaut nommée **Utilisateur pour lequel l’envoi de courrier est restreint** avertit automatiquement les administrateurs lorsque les utilisateurs ne peuvent pas envoyer de messages sortants. Vous pouvez vérifier ces paramètres et ajouter des utilisateurs à avertir. Pour plus d’informations sur les stratégies d’alerte, accédez à [Stratégies d’alerte dans le centre de sécurité et conformité](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Pour que les alertes fonctionnent, la recherche dans le journal d’audit doit être activée. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

1. Dans le Centre de sécurité et conformité, accédez à **Alertes** \> **Stratégies d’alerte**.

2. Recherchez et sélectionnez l’alerte **Utilisateur pour lequel l’envoi de courrier est restreint**.

3. Dans le menu volant qui apparaît, vérifiez ou configurez les paramètres suivants :

   - **État** : vérifiez que l’alerte est activée ![Activer](../../media/scc-toggle-on.png).

   - **Destinataires de courrier** : cliquez sur **Modifier** et vérifiez ou configurez les paramètres suivants dans le menu volant **Modifier les destinataires** qui apparaît :

     - **Envoyer des notifications par courrier** : vérifiez que la case est cochée (**Activé**).

     - **Destinataires du courrier** : la valeur par défaut est **TenantAdmins** (c’est-à-dire membres de type **Administrateur général**). Pour ajouter des destinataires, cliquez sur une zone vide de la zone. Une liste de destinataires apparaît, puis vous pouvez commencer à saisir un nom pour filtrer et sélectionner un destinataire. Vous pouvez supprimer un destinataire existant de la zone en cliquant sur ![Icône Supprimer](../../media/scc-remove-icon.png) en regard de son nom.

     - **Limite quotidienne de notification** : la valeur par défaut est **Aucune limite**, mais vous pouvez sélectionner une limite pour le nombre maximal de notifications par jour.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. De retour dans le menu roulant **Utilisateur pour lequel l’envoi de courrier est restreint**, cliquez sur **Fermer**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Utiliser Exchange Online PowerShell pour afficher et supprimer des utilisateurs de la liste Utilisateurs restreints

Pour afficher cette liste d’utilisateurs pour lesquels l’envoi de courrier est restreint, exécutez la commande suivante :

```powershell
Get-BlockedSenderAddress
```

Pour afficher les détails d’un utilisateur spécifique, remplacez \<emailaddress\> par son adresse e-mail, puis exécutez la commande suivante :

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Pour des informations détaillées sur la syntaxe et les paramètres, voir [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Pour supprimer un utilisateur de la liste Utilisateurs restreints, remplacez \<emailaddress\> par son adresse e-mail, puis exécutez la commande suivante :

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Pour des informations détaillées sur la syntaxe et les paramètres, voir [Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).