---
title: Supprimer les connecteurs bloqués du portail d’entités restreintes dans Microsoft 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.date: ''
ms.localizationpriority: medium
ms.assetid: ''
ms.collection:
- m365-security
ms.custom: ''
description: Découvrez comment supprimer les connecteurs bloqués dans Microsoft 365 Defender.
ms.subservice: mdo
ms.service: microsoft-365-security
search.appverid: met150
ms.openlocfilehash: e376676045a68d4127fbdd7eb05e0000c6e0788d
ms.sourcegitcommit: edc9d4dec92ca81cff39bbf9590f1cd3a75ec436
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2022
ms.locfileid: "68484300"
---
# <a name="remove-blocked-connectors-from-the-restricted-entities-portal"></a>Supprimer les connecteurs bloqués du portail d’entités restreintes

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**

- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Si un connecteur entrant est détecté comme potentiellement compromis, il est limité à l’envoi d’e-mails de relais. Le connecteur est ensuite ajouté à la page **Entités restreintes** dans le portail Microsoft 365 Defender. Lorsque le connecteur est utilisé pour envoyer un e-mail, le message est retourné dans un rapport de non-remise (également appelé NDR ou message rebondi) avec le code d’erreur 550;5.7.711 et le texte suivant :

> Votre message n’a pas pu être remis. La raison la plus courante est que le connecteur de messagerie de votre organisation est suspecté d’envoyer du courrier indésirable ou du hameçonnage et qu’il n’est plus autorisé à envoyer du courrier électronique. Contactez votre administrateur de messagerie pour obtenir de l’aide.
> Le serveur distant a retourné la valeur 550;5.7.711 Accès refusé, connecteur entrant incorrect. AS(2204).

Les administrateurs peuvent supprimer des connecteurs de la page Entités restreintes dans Microsoft 365 Defender ou dans Exchange Online PowerShell.

## <a name="learn-more-on-restricted-entities"></a>En savoir plus sur les entités restreintes

Une entité restreinte est une entité qui n’a pas pu envoyer de courrier électronique, car elle a été potentiellement compromise ou a dépassé la limite d’envoi.

Il existe 2 types d’entités restreintes :

- **Utilisateur restreint** : pour plus d’informations sur la raison pour laquelle un utilisateur peut être restreint et sur la façon de gérer les utilisateurs restreints, consultez [Supprimer les utilisateurs bloqués du portail d’entités restreintes](removing-user-from-restricted-users-portal-after-spam.md).

- **Connecteur restreint** : découvrez pourquoi un connecteur peut être restreint et comment gérer les connecteurs restreints (cet article).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Ouvrez le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>. Pour accéder directement à la page **Entités restreintes** , utilisez <https://security.microsoft.com/restrictedentities>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous devez disposer d’autorisations dans **Exchange Online** avant de pouvoir suivre les procédures mentionnées dans cet article :
  - Pour supprimer des connecteurs du portail d’entités restreintes, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule au portail d’entités restreintes, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Adding users to the corresponding Azure Active Directory role in the Microsoft 365 admin center gives users the required permissions _and_ permissions for other features in Microsoft 365. For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Avant de supprimer le connecteur du portail d’entités restreintes, veillez à suivre les étapes requises pour reprendre le contrôle du connecteur. Pour plus d’informations, consultez [Répondre à un connecteur compromis](respond-compromised-connector.md).

## <a name="use-the-microsoft-365-defender-portal-to-remove-a-connector-from-the-restricted-entities-list"></a>Utiliser le portail Microsoft 365 Defender pour supprimer un connecteur de la liste des entités restreintes

1. Dans le [portail Microsoft 365 Defender](https://security.microsoft.com), accédez à **Email & collaboration** \> **Vérifier** \> **les entités restreintes**. Pour accéder directement à la page **Entités restreintes** , utilisez <https://security.microsoft.com/restrictedentities>.

2. Dans la page **Entités restreintes** , recherchez et sélectionnez le connecteur que vous souhaitez débloquer en cliquant sur le connecteur.

3. Cliquez sur l’action **Débloquer** qui s’affiche.

4. Dans le menu volant **Débloquer l’entité** qui s’affiche, lisez les détails sur le connecteur restreint. Vous devez suivre les recommandations pour vous assurer que vous effectuez les actions appropriées au cas où le connecteur est compromis.

5. Lorsque vous avez terminé, cliquez sur **Débloquer**.

   > [!NOTE]
   > La suppression de toutes les restrictions du connecteur peut prendre jusqu’à 1 heure.

## <a name="verify-the-alert-settings-for-restricted-connectors"></a>Vérifier les paramètres d’alerte pour les connecteurs restreints

La stratégie d’alerte par défaut nommée **activité de connecteur suspecte** avertit automatiquement les administrateurs lorsque les connecteurs ne peuvent pas relayer le courrier électronique. Pour plus d'informations sur les stratégies d'alerte, voir Stratégies [d'alerte dans Microsoft 365](../../compliance/alert-policies.md).

> [!IMPORTANT]
> Pour que les alertes fonctionnent, la recherche dans le journal d’audit doit être activée. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

1. Dans le portail Microsoft 365 Defender, accédez à **Courrier électronique et stratégies de collaboration** \> **Stratégies & règles** \> **Alerte**.

2. Dans la page **Stratégie d’alerte** , recherchez et sélectionnez l’alerte nommée **Activité du connecteur suspect**. Vous pouvez trier les stratégies par nom ou utiliser la **Zone de recherche** pour rechercher la stratégie.

3. Dans le menu volant **d’activité suspecte du connecteur** qui s’affiche, vérifiez ou configurez les paramètres suivants :
   - **État** : vérifiez que l’alerte est activée ![Activer](../../media/scc-toggle-on.png).
   - **Destinataires de courrier** : cliquez sur **Modifier** et vérifiez ou configurez les paramètres suivants dans le menu volant **Modifier les destinataires** qui apparaît :
     - **Envoyer des notifications par e-mail**: vérifiez que cette option est sélectionnée (**Activé**).
     - **Destinataires du courrier** : la valeur par défaut est **TenantAdmins** (c’est-à-dire membres de type **Administrateur général**). Pour ajouter d’autres destinataires, cliquez sur une zone vide de la zone. Une liste de destinataires apparaît, puis vous pouvez commencer à saisir un nom pour filtrer et sélectionner un destinataire. Vous pouvez supprimer un destinataire existant de la zone en cliquant sur l’![ icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) à côté de leur nom.
     - **Limite de notification quotidienne** : la limite n’est pas supérieure à 3 notifications par connecteur par jour.

     Lorsque vous avez terminé, cliquez sur **Enregistrer**.

4. De retour sur le menu volant **activité suspecte du connecteur** , cliquez sur **Fermer**.

## <a name="use-exchange-online-powershell-to-view-and-remove-connectors-from-the-restricted-entities-list"></a>Utiliser Exchange Online PowerShell pour afficher et supprimer des connecteurs de la liste des entités restreintes

Pour afficher la liste des connecteurs qui ne peuvent pas envoyer de courrier électronique, exécutez la commande suivante :

```powershell
Get-BlockedConnector
```

Pour afficher des détails sur un connecteur spécifique, remplacez \<connectorId\> et exécutez la commande suivante :

```powershell
Get-BlockedConnector -ConnectorId <connectorId>
```

Pour supprimer un connecteur de la liste des entités restreintes, remplacez \<connectorId\> et exécutez la commande suivante :

```powershell
Remove-BlockedConnector -ConnectorId <connectorId>
```

## <a name="more-information"></a>Plus d’informations

- [Répondre à un connecteur compromis](respond-compromised-connector.md)
- [Supprimer les utilisateurs bloqués](removing-user-from-restricted-users-portal-after-spam.md)
