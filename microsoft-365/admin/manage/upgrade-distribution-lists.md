---
title: Mettre à niveau les listes de distribution vers des groupes Microsoft 365 dans Outlook
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Découvrez comment mettre à niveau une ou plusieurs listes de distribution vers des groupes Microsoft 365 dans Outlook, et comment utiliser PowerShell pour mettre à niveau plusieurs listes de distribution simultanément.
ms.openlocfilehash: a1fb974be4838ebe98c2c55fe8694e89e27d636e
ms.sourcegitcommit: 3951147f74510e2ead6c11ceab92854f0937426b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/08/2020
ms.locfileid: "45083573"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Mettre à niveau les listes de distribution vers des groupes Microsoft 365 dans Outlook

Vous pouvez mettre à niveau les listes de distribution vers des groupes Microsoft 365 avec Outlook. Il s’agit d’un excellent moyen d’accorder à la distribution de votre organisation toutes les fonctionnalités des groupes Microsoft 365. [Pourquoi devriez-vous mettre à niveau vos listes de distribution vers des groupes dans Outlook ?](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Vous pouvez mettre à niveau les listes de distribution une par une ou plusieurs simultanément.

## <a name="upgrade-one-or-many-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Mettre à niveau une ou plusieurs listes de distribution vers des groupes Microsoft 365 dans Outlook

Vous devez être un administrateur général ou un administrateur Exchange pour mettre à niveau une liste de distribution. Pour effectuer une mise à niveau vers les groupes Microsoft 365, un groupe de distribution doit avoir un propriétaire avec une boîte aux lettres. 

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>.

2. Dans le centre d’administration Exchange, accédez à groupes de **destinataires** \> **Groups**.<br/>Vous verrez une notification indiquant que des listes de distribution (également appelées **groupes de distribution** ) sont éligibles pour être mises à niveau vers les groupes Microsoft 365.<br/> ![Sélectionnez le bouton prise en main](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

3. Sélectionnez une ou plusieurs listes de distribution (également appelées **groupe de distribution** ) dans la page **groupes** .<br/>![Sélectionner un groupe de distribution](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

4. Sélectionnez l’icône de mise à niveau.<br/>![Icône de mise à niveau vers les groupes Microsoft 365](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

5. Dans la boîte de dialogue informations, sélectionnez **Oui** pour confirmer la mise à niveau. Le processus commence immédiatement. En fonction de la taille et du nombre de listes de distribution que vous mettez à niveau, le processus peut prendre des minutes ou des heures.<br/>Si la liste de distribution ne peut pas être mise à niveau, une boîte de dialogue s’affiche. [Quels sont les listes de distribution qui ne peuvent pas être mises à niveau ?](#which-distribution-lists-cannot-be-upgraded).

6. Si vous mettez à niveau plusieurs listes de distribution, utilisez la liste déroulante pour filtrer les listes de distribution qui ont été mises à niveau. Si la liste n’est pas complète, patientez un certain temps, puis sélectionnez **Actualiser** pour voir ce qui a été correctement mis à niveau.<br/>Aucune notification ne vous indique quand le processus de mise à niveau est terminé pour toutes les listes de distribution que vous avez sélectionnées. Vous pouvez le faire en vous recherchant dans la section **disponible pour la mise à niveau** ou les **listes de distribution**de contenu.

7. Si vous avez sélectionné une LD pour la mise à niveau, mais qu’elle apparaît toujours sur la page comme disponible pour la mise à niveau, la mise à niveau a échoué. Consultez [la procédure à suivre si la mise à niveau ne fonctionne pas](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Si vous obtenez les messages de résumé des groupes que vous pouvez remarquer dans la partie inférieure, il est parfois proposé de vous permettre de mettre à niveau toutes les listes de distribution éligibles dont vous êtes propriétaire. Pour plus d’informations sur les e-mails de résumé [, consultez la rubrique utiliser une conversation de groupe dans Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) .


## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Procédure à suivre en cas de non-fonctionnement de la mise à niveau

Les listes de distribution dont la mise à niveau échoue restent inchangées.

Si une ou plusieurs listes de distribution **éligibles** ne peuvent pas être mises à niveau, ouvrez un [ticket de support](../contact-support-for-business-products.md). Le problème doit être remonté vers l’équipe d’ingénierie des groupes pour qu’il soit possible de déterminer le problème.

Il est possible que la liste de distribution n’ait pas été mise à niveau en raison d’une panne de service, mais très improbable. Si vous le souhaitez, patientez quelques instants, puis réessayez de mettre à niveau la nouvelle DL.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Comment utiliser PowerShell pour mettre à niveau plusieurs listes de distribution en même temps

Si vous avez recours à PowerShell, il se peut que vous souhaitiez utiliser cet itinéraire au lieu d’utiliser l’interface utilisateur. Nous disposons d’un ensemble d’applets de commande qui vous aideront à mettre à niveau les listes de distribution. Voir ci-dessous.

### <a name="upgrade-a-single-dl"></a>Mettre à niveau une seule LD

Pour mettre à niveau une seule DL, exécutez la commande suivante :

```PowerShell
Upgrade-DistributionGroup -DlIdentities \<Dl SMTP address\>`
```

Par exemple, si vous souhaitez mettre à niveau une distribution de listes de distribution avec l’adresse SMTP dl1@contoso.com, exécutez la commande suivante :

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com`
```

> [!NOTE]
> Vous pouvez également mettre à niveau une seule liste de distribution vers un groupe Microsoft 365 à l’aide de l’applet de commande PowerShell [New-UnifiedGroup](https://go.microsoft.com/fwlink/?LinkID=786379)

### <a name="upgrade-multiple-dls-in-a-batch"></a>Mettre à niveau plusieurs listes de distribution dans un lot

Vous pouvez également transmettre plusieurs listes de distribution par lots et les mettre à niveau ensemble :

```PowerShell
Upgrade-DistributionGroup -DlIdentities \<DL SMTP address1\>, \< DL SMTP address2\>,
\< DL SMTP address3\>, \< DL SMTP address 4\>
```

Par exemple, si vous souhaitez mettre à niveau cinq listes de distribution avec adresse SMTP `dl1@contoso.com` et, `dl2@contoso.com` et, `dl3@contoso.com` `dl4@contoso.com` `dl5@contoso.com` exécutez la commande suivante :

`Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com`

### <a name="upgrade-all-eligible-dls"></a>Mettre à niveau toutes les listes de distribution éligibles

Il existe deux façons de mettre à niveau toutes les listes de distribution éligibles.

> [!NOTE]
> La cmdlet Upgrade-DistributionGroup ne reçoit pas de données du pipeline, pour cette raison, il est nécessaire d’utiliser l’opérateur « ForEach-Object {} » pour s’exécuter correctement.

1. Obtenez les listes de distribution éligibles dans le client et mettez-les à niveau à l’aide de la commande de mise à niveau :

```PowerShell
Get-EligibleDistributionGroupForMigration | Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

2. Obtenir la liste de toutes les listes de distribution et mettre à niveau uniquement les listes de distribution éligibles :

```PowerShell
Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Forum aux questions sur la mise à niveau des listes de distribution vers des groupes Microsoft 365 dans Outlook

### <a name="which-distribution-lists-cannot-be-upgraded"></a>Quelles listes de distribution ne peuvent pas être mises à niveau ?

Vous ne pouvez mettre à niveau que des listes de distribution non imbriquées gérées dans le Cloud, simples et non imbriquées. Le tableau ci-dessous répertorie les listes de distribution qui **ne peuvent pas** être mises à niveau.

|**Propriété**|**Exclus?**|
|:-----|:-----|
|Liste de distribution gérée locale.  <br/> |Non  <br/> |
|Listes de distribution imbriquées. La liste de distribution a des groupes enfants ou est membre d’un autre groupe.  <br/> |Non  <br/> |
|Listes de distribution avec des membres **RecipientTypeDetails** autres que **UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**  <br/> |Non  <br/> |
|Liste de distribution contenant plus de 100 propriétaires  <br/> |Non  <br/> |
|Liste de distribution qui ne possède que des membres mais pas de propriétaire  <br/> |Non  <br/> |
|Liste de distribution avec un alias contenant des caractères spéciaux  <br/> |Non  <br/> |
|Si la liste de distribution est configurée pour être une adresse de transfert pour la boîte aux lettres partagée  <br/> |Non  <br/> |
|Si la LD fait partie de la restriction de l' **expéditeur** dans une autre DL.  <br/> |Non  <br/> |
|Groupes de sécurité  <br/> |Non  <br/> |
|Listes de distribution dynamique  <br/> |Non  <br/> |
|Listes de distribution qui ont été converties en **RoomLists**  <br/> |Non  <br/> |
|Listes de distribution où **MemberJoinRestriction** et/ou **MemberDepartRestriction** sont **fermés**  <br/> |Non  <br/> |

### <a name="how-do-i-check-which-dls-are-eligible-for-upgrade"></a>Comment puis-je vérifier quelles listes de distribution sont éligibles pour la mise à niveau ?

Si vous souhaitez vérifier si une LD est éligible ou non, vous pouvez exécuter la commande ci-dessous :

`Get-DistributionGroup \<DL SMTP address\> | Get-EligibleDistributionGroupForMigration`

Si vous souhaitez vérifier quelles listes de distribution sont éligibles pour la mise à niveau, exécutez la commande suivante :

`Get-EligibleDistributionGroupForMigration`

### <a name="who-can-run-the-upgrade-scripts"></a>Qui peut exécuter les scripts de mise à niveau ?

Personnes disposant de droits d’administrateur général ou d’administrateur Exchange.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-a-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Pourquoi la carte de visite affiche-t-elle toujours une liste de distribution ? Que dois-je faire pour empêcher qu’une liste de distribution mise à niveau ne s’affiche dans ma liste de suggestions automatiques ?

- Pour Outlook : lorsqu’une personne tente d’envoyer un courrier électronique dans Outlook en tapant le nom du groupe Microsoft 365 après la migration, le destinataire est résolu en tant que liste de distribution au lieu du groupe. La carte de visite du destinataire est la carte de visite des listes de distribution. Cela est dû au cache de destinataires ou au cache de noms Nick dans Outlook. Le message électronique est envoyé au groupe, mais risque de confusion pour l’expéditeur.<br/>Vous pouvez effectuer les étapes de cette rubrique, des [informations sur la liste de saisie semi-automatique Outlook](https://go.microsoft.com/fwlink/?LinkID=798736) pour réinitialiser le cache, ce qui permet de résoudre ce problème.

- Pour Outlook sur le Web : dans le cas d’Outlook sur le Web, le destinataire de la liste de distribution restera dans le cache. Vous pouvez suivre les étapes de la section [supprimer le nom suggéré ou l’adresse de messagerie de la liste de saisie semi-automatique](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) pour actualiser le cache pour afficher la carte de visite du groupe.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Les nouveaux membres du groupe reçoivent-ils un message électronique de bienvenue dans leur boîte de réception ?

Non. Le paramètre permettant d’activer les messages de bienvenue est défini sur false par défaut. Ce paramètre affecte les membres de groupe existants et nouveaux qui peuvent rejoindre une fois la migration terminée. Si le propriétaire du groupe peut par la suite autoriser les utilisateurs invités, les utilisateurs invités ne reçoivent pas de courrier de bienvenue dans leur boîte de réception. Les membres invités peuvent continuer à travailler avec le groupe.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Que se passe-t-il si une ou plusieurs listes de distribution ne sont pas mises à niveau ?

Dans certains cas, si DL est éligible mais n’a pas pu être mis à niveau. La LD ne peut pas être mise à niveau et reste en tant que DL.

- Où l’administrateur a appliqué la **stratégie d’adresse de messagerie de groupe** pour les groupes au sein d’une organisation et tente de mettre à niveau les listes de distribution qui ne répondent pas aux critères, la DL ne bénéficie pas de la mise à niveau

- Les listes de distribution avec **MemberJoinRestriction** ou **MemberDepartRestriction** définies sur **fermé**n’ont pas pu être mises à niveau

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Qu’arrive-t-il à la DL si la mise à niveau à partir de l’erreur de l’administration Exchange

La mise à niveau se produit uniquement lorsque l’appel est envoyé au serveur. Si la mise à niveau échoue, vos listes de distribution seront intactes. Ils fonctionneront comme s’ils utilisaient.


