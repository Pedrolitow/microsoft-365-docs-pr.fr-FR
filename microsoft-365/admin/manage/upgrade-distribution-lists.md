---
title: Améliorer les listes de distribution vers les groupes Microsoft 365 dans Outlook
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
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Découvrez comment mettre à niveau une ou plusieurs listes de distribution vers Microsoft 365 Groupes dans Outlook et comment utiliser PowerShell pour mettre à niveau plusieurs listes de distribution simultanément.
ms.openlocfilehash: 298d349fcf0874dd4c2dbd85ff19101e40988aba
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58566963"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Améliorer les listes de distribution vers les groupes Microsoft 365 dans Outlook

Vous pouvez mettre à niveau les listes de distribution Microsoft 365 groupes Outlook. Il s’agit d’un excellent moyen de fournir aux listes de distribution de votre organisation toutes les fonctionnalités et fonctionnalités de Microsoft 365 groupes. [Pourquoi vous devriez mettre à niveau vos listes de distribution vers des groupes dans Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Vous pouvez mettre à niveau les DL une par une ou plusieurs en même temps.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Mettre à niveau un ou plusieurs groupes de listes de distribution vers Microsoft 365 groupes dans Outlook

Vous devez être administrateur global ou administrateur Exchange pour mettre à niveau un groupe de listes de distribution. Pour mettre à niveau vers Microsoft 365 groupes de distribution, le groupe de listes de distribution doit avoir un propriétaire avec une boîte aux lettres.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Utilisez le nouveau CENTRE D’EAC pour mettre à niveau un ou plusieurs groupes de listes de distribution vers Microsoft 365 groupes dans Outlook

1. Accédez au nouveau [centre Exchange’administration,](https://admin.exchange.microsoft.com)puis accédez à **Groupes de destinataires.** \> 

2. Sélectionnez le groupe de listes de distribution (également appelé groupe de **distribution)** que vous souhaitez mettre à niveau vers Microsoft 365 groupe à partir de la page **Groupes.**

3. Sélectionnez le **groupe de distribution Mise à niveau dans** la barre d’outils.

4. Dans la boîte de dialogue **Prêt pour la mise à niveau ?**, cliquez sur Mettre à **niveau.** Le processus commence immédiatement. Selon la taille et le nombre de groupes de listes de distribution que vous êtes en train de mettre à niveau, le processus peut prendre des minutes ou des heures.

> [!NOTE]
> Une bannière en haut indique que la mise à niveau, par exemple, les groupes *de distribution ont été mis à niveau. La réflexion des modifications prend 5 minutes. Filtrez par Microsoft 365 pour voir les groupes de distrubtion* mis à niveau.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Utiliser le CENTRE D’EAC classique pour mettre à niveau un ou plusieurs groupes de listes de distribution Microsoft 365 groupes dans Outlook

1. Go to the Classic <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Exchange admin center</a>.

2. Dans le Centre d’administration Exchange classique, allez à **Groupes de** \> **destinataires.**<br/>Vous verrez un avis indiquant que vous avez des listes de distribution (également appelées groupes de **distribution)** qui peuvent être mises à niveau vers Microsoft 365 groupes.<br/> ![Sélectionnez le bouton Démarrer.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

3. Sélectionnez une ou plusieurs listes de distribution (également appelées groupe de **distribution)** dans la page **des groupes.**<br/>![Sélectionnez un groupe de distribution.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

4. Sélectionnez l’icône de mise à niveau.<br/>![Mettre à niveau vers Microsoft 365'icône Groupes.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

5. Dans la boîte de dialogue d’informations, **sélectionnez Oui** pour confirmer la mise à niveau. Le processus commence immédiatement. Selon la taille et le nombre de DLs que vous êtes en train de mettre à niveau, le processus peut prendre des minutes ou des heures.<br/>Si la liste de distribution ne peut pas être mise à niveau, une boîte de dialogue s’affiche. Voir [quelles listes de distribution ne peuvent pas être mises à niveau ?](#which-distribution-lists-cant-be-upgraded)

6. Si vous êtes en train de mettre à niveau plusieurs listes de distribution, utilisez la liste de listes listes pour filtrer les listes de distribution qui ont été mises à niveau. Si la liste n’est pas terminée, patientez un peu plus longtemps, puis sélectionnez **Actualiser** pour voir ce qui a été correctement mis à niveau.<br/>Aucun avis ne vous indique à quel moment le processus de mise à niveau est terminé pour toutes les DL que vous avez sélectionnées. Vous pouvez le comprendre en cherchant à voir ce qui est répertorié sous **Disponible** pour la mise à niveau ou les **DL mises à niveau.**

7. Si vous avez sélectionné une DL pour la mise à niveau, mais qu’elle apparaît toujours sur la page comme disponible pour la mise à niveau, elle n’a pas réussi à mettre à niveau. Voir [que faire si la mise à niveau ne fonctionne pas](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Si vous avez reçu les e-mails de condensé de groupes, vous remarquerez peut-être en bas qu’il vous proposera parfois de mettre à niveau les listes de distribution éligibles dont vous êtes le propriétaire. Voir [Avoir une conversation de groupe dans Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) pour plus d’informations sur les e-mails digest.

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Que faire si la mise à niveau ne fonctionne pas

Les listes de distribution qui échouent à la mise à niveau restent inchangées.

Si une ou plusieurs listes **de** distribution éligibles ne peuvent pas être mises à niveau, ouvrez un [ticket de support.](../../business-video/get-help-support.md) Le problème doit être recalcalé à l’équipe d’ingénierie des groupes pour qu’il en soit ainsi.

Il est possible que la liste de distribution n’a pas été mise à niveau en raison d’une panne de service, mais peu probable. Si vous le souhaitez, patientez un certain temps, puis réessayez de mettre à niveau la DL.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Comment utiliser PowerShell pour mettre à niveau plusieurs listes de distribution en même temps

Si vous avez l’expérience de l’utilisation de PowerShell, vous pouvez utiliser cet itinéraire au lieu d’utiliser l’interface utilisateur. Nous avons un ensemble de cmdlets qui vous aideront à mettre à niveau les listes de distribution. Voir ci-dessous.

### <a name="upgrade-a-single-dl"></a>Mettre à niveau une seule DL

Pour mettre à niveau une seule DL, exécutez la commande suivante :

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Par exemple, si vous souhaitez mettre à niveau une DL avec des adresses SMTP dl1@contoso.com, exécutez la commande suivante :

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> Vous pouvez également mettre à niveau une liste de distribution unique vers un groupe Microsoft 365 à l’aide de l’cmdlet [PowerShell New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup)

### <a name="upgrade-multiple-dls-in-a-batch"></a>Mettre à niveau plusieurs DLs dans un lot

Vous pouvez également passer plusieurs DLs en tant que lot et les mettre à niveau ensemble :

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Par exemple, si vous souhaitez mettre à niveau cinq DLs avec l’adresse SMTP `dl1@contoso.com` `dl2@contoso.com` `dl3@contoso.com` et, `dl4@contoso.com` `dl5@contoso.com` et, exécutez la commande suivante :

`Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com`

### <a name="upgrade-all-eligible-dls"></a>Mettre à niveau toutes les DL éligibles

Il existe deux façons de mettre à niveau toutes les DL éligibles.

> [!NOTE]
> La cmdlet Upgrade-DistributionGroup ne reçoit pas de données du pipeline, pour cette raison, il est nécessaire d’utiliser l’opérateur « foreach-object » pour s’exécuter {} correctement.

1. Obtenez les DL éligibles dans le client et faites-les mettre à niveau à l’aide de la commande de mise à niveau :

```PowerShell
Get-EligibleDistributionGroupForMigration | Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

2. Obtenir la liste de toutes les DL et mettre à niveau uniquement les DL éligibles :

```PowerShell
Get-DistributionGroup| Foreach-Object{
    Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
}
```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>FAQ sur la mise à niveau de listes de distribution Microsoft 365 groupes dans Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Quelles listes de distribution ne peuvent pas être mises à niveau ?

Vous pouvez uniquement mettre à niveau des listes de distribution non imbrique, simples et gérées dans le cloud. Le tableau ci-dessous répertorie les listes de distribution qui **ne peuvent** pas être mises à niveau.

|**Property**|**Éligible ?**|
|:-----|:-----|
|Liste de distribution gérée sur site.  <br/> |Non  <br/> |
|Listes de distribution imbrmbrées. La liste de distribution possède des groupes enfants ou est membre d’un autre groupe.  <br/> |Non  <br/> |
|Listes de distribution dont le **membre RecipientTypeDetails** est autre que **UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**  <br/> |Non  <br/> |
|Liste de distribution avec plus de 100 propriétaires  <br/> |Non  <br/> |
|Liste de distribution qui ne possède que des membres, mais pas de propriétaire  <br/> |Non  <br/> |
|Liste de distribution avec alias contenant des caractères spéciaux  <br/> |Non  <br/> |
|Si la liste de distribution est configurée pour être une adresse de forwarding pour la boîte aux lettres partagée  <br/> |Non  <br/> |
|Si la DL fait partie de **la restriction de l’expéditeur** dans une autre DL.  <br/> |Non  <br/> |
|Groupes de sécurité  <br/> |Non  <br/> |
|Listes de distribution dynamique  <br/> |Non  <br/> |
|Listes de distribution qui ont été converties **en RoomLists**  <br/> |Non  <br/> |

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Vérifier les DL éligibles pour la mise à niveau

Si vous souhaitez vérifier si une DL est éligible ou non, vous pouvez exécuter la commande suivante :

`Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration`

Si vous souhaitez vérifier les DL éligibles pour la mise à niveau, exécutez simplement la commande suivante :

`Get-EligibleDistributionGroupForMigration`

### <a name="who-can-run-the-upgrade-scripts"></a>Qui pouvez exécuter les scripts de mise à niveau ?

Personnes ayant des droits d’administrateur global ou Exchange’administrateur.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Pourquoi la carte de visite affiche-t-elle toujours une liste de distribution ? Que dois-je faire pour empêcher l’affichage d’une liste de distribution mise à niveau dans ma liste de suggestions automatiques ?

- Par Outlook : lorsqu’une personne tente d’envoyer un courrier électronique dans Outlook en tapant le nom du groupe Microsoft 365 après la migration, le destinataire est résolu en tant que liste de distribution au lieu du groupe. La carte de visite du destinataire sera la carte de visite des listes de distribution. Cela est dû au cache de destinataires ou au cache de noms d’Outlook. L’e-mail est envoyé au groupe, mais peut être source de confusion pour l’expéditeur.<br/>Vous pouvez effectuer les étapes de cet article, Information [about the Outlook AutoComplete list](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) to reset the cache, which will fix this issue.

- Pour Outlook sur le web : en cas de Outlook sur le web, le destinataire de la liste de distribution reste dans le cache. Vous pouvez suivre [](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) les étapes de la procédure de suppression du nom suggéré ou de l’adresse de messagerie de la liste de mise à jour automatique pour actualiser le cache et voir la carte de visite du groupe.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Les nouveaux membres du groupe obtiennent-ils un e-mail de bienvenue dans leur boîte de réception ?

Non. Le paramètre permettant d’activer les messages d’accueil est false par défaut. Ce paramètre affecte à la fois les membres existants et les nouveaux membres du groupe qui peuvent rejoindre le groupe une fois la migration terminée. Si le propriétaire du groupe autorise ultérieurement les utilisateurs invités, les utilisateurs invités ne reçoivent pas de message électronique de bienvenue dans leur boîte de réception. Les membres invités peuvent continuer à travailler avec le groupe.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Que se passe-t-il si une ou certaines DL ne sont pas mises à niveau ?

Dans certains cas, la DL est éligible mais n’a pas pu être mise à niveau. La DL n’est pas mise à niveau et reste en tant que DL.

- Lorsque l’administrateur a appliqué la stratégie d’adresse de messagerie de groupe pour les groupes d’une organisation et qu’il essaie de mettre à niveau les DL qui ne remplissent pas les critères, la DL n’est pas mise à niveau 

- DLs with **MemberJoinRestriction** or **MemberDepartRestriction** set to **Closed**, could not be upgraded

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Qu’advient-il de la DL en cas d’échec de la mise à niveau à partir du EAC ?

La mise à niveau se produit uniquement lorsque l’appel est soumis au serveur. Si la mise à niveau échoue, vos DL sont intactes. Ils fonctionnent comme avant.

## <a name="related-content"></a>Contenu associé

[Comparer les groupes](../create-groups/compare-groups.md) (article)\
[Expliquer Microsoft 365 groupes à vos utilisateurs](../create-groups/explain-groups-knowledge-worker.md) (article)\
[Ajouter ou supprimer des membres de groupes Microsoft 365 à l’aide du Centre d’administration](../create-groups/add-or-remove-members-from-groups.md)
