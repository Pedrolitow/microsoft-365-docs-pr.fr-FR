---
title: Supprimer les utilisateurs bloqués du portail Utilisateurs restreints
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
ms.localizationpriority: high
search.appverid:
- MET150
ms.assetid: 712cfcc1-31e8-4e51-8561-b64258a8f1e5
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à supprimer des utilisateurs de la page Utilisateurs restreints dans le portail Microsoft 365 Defender. Les utilisateurs sont ajoutés au portail Utilisateurs restreints pour avoir envoyé du courrier indésirable sortant, généralement en raison de la compromission d’un compte.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 229dfbb7a0441f4a6cb6632432c0032f4ce4308e
ms.sourcegitcommit: fdd0294e6cda916392ee66f5a1d2a235fb7272f8
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/29/2022
ms.locfileid: "65130733"
---
# <a name="remove-blocked-users-from-the-restricted-users-portal-in-microsoft-365"></a>Supprimer les utilisateurs bloqués du portail Utilisateurs restreints dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si un utilisateur dépasse l’une des limites d’envoi sortant, comme spécifié dans [les limites de service](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits#sending-limits-across-office-365-options) ou dans [les stratégies anti-courrier indésirable sortantes](configure-the-outbound-spam-policy.md), l’utilisateur ne peut pas envoyer d’e-mails, mais il peut continuer à en recevoir.

L'utilisateur est ajouté à la page **Utilisateurs restreints** dans le portail Microsoft 365 Defender. Lorsqu'il essaie d'envoyer un e-mail, le message est renvoyé dans un rapport de non-livraison (également appelé NDR ou messages de rebond) avec le code d'erreur [5.1.8](/Exchange/mail-flow-best-practices/non-delivery-reports-in-exchange-online/fix-error-code-5-1-8-in-exchange-online) et le texte suivant :

> «Votre message n’a pas pu être remis parce que vous n’avez pas été reconnu comme expéditeur valide. Le plus souvent, il est possible que votre adresse de messagerie soit susceptible d’envoyer du courrier indésirable et qu’elle ne soit plus autorisée à envoyer du courrier électronique.  Contactez votre administrateur pour obtenir de l’aide. Le serveur distant a renvoyé' 550 5.1.8 accès refusé, expéditeur sortant incorrect».

Les administrateurs peuvent supprimer des utilisateurs de la page **Utilisateurs restreints** dans Microsoft 365 Defender ou dans Exchange Online PowerShell.

## <a name="learn-more-on-restricted-entities"></a>En savoir plus sur les entités restreintes

Une entité restreinte est une entité qui n’a pas pu envoyer de courrier électronique, car elle a été potentiellement compromise ou a dépassé la limite d’envoi.

Il existe 2 types d’entités restreintes : 

- **Utilisateur restreint** : découvrez pourquoi un utilisateur peut être restreint et comment gérer les utilisateurs restreints (cet article).  

- **Connecteur restreint** : pour plus d’informations sur la raison pour laquelle un connecteur peut être restreint et sur la façon de gérer les connecteurs restreints, consultez [Supprimer les connecteurs bloqués du portail d’entités restreintes](remove-blocked-connectors.md). 

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Utilisateurs restreints**, utilisez <https://security.microsoft.com/restrictedusers>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour supprimer des utilisateurs du portail Utilisateurs restreints, vous devez être membre des groupes de rôles **Management de l’organisation** ou **Administrateur de sécurité**.
  - Pour l’accès en lecture seule au portail Utilisateurs restreints, vous devez être membre du groupe de rôles **Lecteur global** ou **Lecteur de sécurité**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de [Microsoft 365](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Un expéditeur dépassant la limite du nombre de messages sortants est un indicateur de compte compromis. Avant de supprimer l’utilisateur du portail Utilisateurs restreints, veillez à suivre les étapes nécessaires pour reprendre le contrôle de son compte. Pour plus informations, voir [Réponse à un compte de messagerie compromis dans Office 365](responding-to-a-compromised-email-account.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-user-from-the-restricted-users-list"></a>Utiliser le portail Microsoft 365 Defender pour supprimer un utilisateur de la liste des Utilisateurs restreints

1. Dans le portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **Courrier électronique et collaboration**\>**Examiner**\>**Utilisateurs restreints**. Pour accéder directement à la page **Utilisateurs restreints**, utilisez <https://security.microsoft.com/restrictedusers>.

2. Dans la page **Utilisateurs restreints** , recherchez et sélectionnez l’utilisateur que vous souhaitez débloquer en cliquant sur l’utilisateur.

3. Cliquez sur l’action **Débloquer** qui s’affiche.

4. Dans le menu volant **Débloquer l’utilisateur** qui s’affiche, lisez les détails sur le compte restreint. Vous devez suivre les recommandations pour vous assurer que vous effectuez les actions appropriées au cas où le compte est compromis.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

5. L’écran suivant comporte des recommandations pour empêcher toute compromission ultérieure. L’activation de l’authentification multifacteur (MFA) et la réinitialisation du mot de passe constituent une bonne défense.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

6. Cliquez sur **Oui** pour confirmer la modification.

   > [!NOTE]
   > La suppression de toutes les restrictions de l’utilisateur peut prendre jusqu’à 1heure.

## <a name="verify-the-alert-settings-for-restricted-users"></a>Vérifier les paramètres d’alerte pour les utilisateurs restreints

La stratégie d’alerte par défaut nommée **Utilisateur pour lequel l’envoi de courrier est restreint** avertit automatiquement les administrateurs lorsque les utilisateurs ne peuvent pas envoyer de messages sortants. Vous pouvez vérifier ces paramètres et ajouter des utilisateurs à avertir. Pour plus d'informations sur les stratégies d'alerte, voir Stratégies [d'alerte dans Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Pour que les alertes fonctionnent, la recherche dans le journal d’audit doit être activée. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

1. Dans le portail Microsoft 365 Defender sur <https://security.microsoft.com>, accédez à **E-mail et collaboration** \> **Stratégies & règles** \> **Alerte**. Pour accéder directement à la page **Stratégie d’alerte**, utilisez <https://security.microsoft.com/alertpolicies>.

2. Dans la page **Stratégie d’alerte**, recherchez et sélectionnez l’alerte nommée **Utilisateur restreint pour l’envoi d’e-mail**. Vous pouvez trier les stratégies par nom ou utiliser la zone de **recherche** pour rechercher la stratégie.

3. Dans le menu volant **Utilisateur restreint pour l’envoi d’e-mail** qui s’affiche, vérifiez ou configurez les paramètres suivants :
   - **État** : vérifiez que l’alerte est activée ![Activer](../../media/scc-toggle-on.png).
   - **Destinataires de courrier** : cliquez sur **Modifier** et vérifiez ou configurez les paramètres suivants dans le menu volant **Modifier les destinataires** qui apparaît :
     - **Envoyer des notifications par e-mail**: vérifiez que cette option est sélectionnée (**Activé**).
     - **Destinataires du courrier** : la valeur par défaut est **TenantAdmins** (c’est-à-dire membres de type **Administrateur général**). Pour ajouter des destinataires, cliquez sur une zone vide de la zone. Une liste de destinataires apparaît, puis vous pouvez commencer à saisir un nom pour filtrer et sélectionner un destinataire. Vous pouvez supprimer un destinataire existant de la zone en cliquant sur l’![ icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) à côté de leur nom.
     - **Limite quotidienne de notification** : la valeur par défaut est **Aucune limite**, mais vous pouvez sélectionner une limite pour le nombre maximal de notifications par jour.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. De retour dans le menu roulant **Utilisateur pour lequel l’envoi de courrier est restreint**, cliquez sur **Fermer**.

## <a name="use-exchange-online-powershell-to-view-and-remove-users-from-the-restricted-users-list"></a>Utiliser Exchange Online PowerShell pour afficher et supprimer des utilisateurs de la liste des Utilisateurs restreints

Pour afficher cette liste d’utilisateurs pour lesquels l’envoi de courrier est restreint, exécutez la commande suivante :

```powershell
Get-BlockedSenderAddress
```

Pour afficher les détails d’un utilisateur spécifique, remplacez \<emailaddress\> par son adresse e-mail, puis exécutez la commande suivante :

```powershell
Get-BlockedSenderAddress -SenderAddress <emailaddress>
```

Pour des informations détaillées sur la syntaxe et les paramètres, voir [Get-BlockedSenderAddress](/powershell/module/exchange/get-blockedsenderaddress).

Pour supprimer un utilisateur de la liste Utilisateurs restreints, remplacez \<emailaddress\> par son adresse e-mail, puis exécutez la commande suivante :

```powershell
Remove-BlockedSenderAddress -SenderAddress <emailaddress>
```

Pour des informations détaillées sur la syntaxe et les paramètres, voir [Remove-BlockedSenderAddress](/powershell/module/exchange/remove-blockedsenderaddress).
