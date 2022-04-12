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
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- AdminTemplateSet
- admindeeplinkEXCHANGE
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 787d7a75-e201-46f3-a242-f698162ff09f
description: Découvrez comment mettre à niveau une ou plusieurs listes de distribution pour Groupes Microsoft 365 dans Outlook et comment utiliser PowerShell pour mettre à niveau plusieurs listes de distribution simultanément.
ms.openlocfilehash: 832d65854a6a18ad28e3d9fca6d1d11c17146c80
ms.sourcegitcommit: ac0ae5c2888e2b323e36bad041a4abef196c9c96
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/12/2022
ms.locfileid: "64782256"
---
# <a name="upgrade-distribution-lists-to-microsoft-365-groups-in-outlook"></a>Améliorer les listes de distribution vers les groupes Microsoft 365 dans Outlook

Vous pouvez mettre à niveau les listes de distribution vers Groupes Microsoft 365 dans Outlook. Il s’agit d’un excellent moyen d’offrir aux listes de distribution de votre organisation toutes les fonctionnalités et fonctionnalités de Groupes Microsoft 365. [Pourquoi vous devriez mettre à niveau vos listes de distribution vers des groupes dans Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

Vous pouvez mettre à niveau les DLL une par une, ou plusieurs en même temps.

## <a name="upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Mettre à niveau un ou plusieurs groupes de listes de distribution vers Groupes Microsoft 365 dans Outlook

Vous devez être administrateur général ou administrateur Exchange pour mettre à niveau un groupe de listes de distribution. Pour effectuer une mise à niveau vers Groupes Microsoft 365, le groupe de listes de distribution doit avoir un propriétaire avec une boîte aux lettres.

### <a name="use-the-new-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Utilisez le nouveau CENTRE pour mettre à niveau un ou plusieurs groupes de listes de distribution vers Groupes Microsoft 365 dans Outlook

1. Accédez au nouveau centre d’administration Exchange > **groupes de destinataires**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a>

2. Sélectionnez le groupe de liste de distribution (également appelé **groupe de distribution**) que vous souhaitez mettre à niveau vers Microsoft 365 groupe à partir de la page **Groupes**.

3. Sélectionnez le **groupe de distribution Mettre à niveau** dans la barre d’outils.

4. Dans la boîte de dialogue **Prêt pour la mise à niveau,** cliquez sur **Mettre à niveau**. Le processus commence immédiatement. Selon la taille et le nombre de groupes de liste de distribution que vous mettez à niveau, le processus peut prendre des minutes ou des heures.

> [!NOTE]
> Une bannière en haut indique la mise à niveau, par exemple, les *groupes de distribution ont été mis à niveau. Il faudra 5 minutes pour refléter les modifications. Filtrez par Microsoft 365 groupes pour voir les groupes de distribution mis à niveau*.

### <a name="use-the-classic-eac-to-upgrade-one-or-many-distribution-list-groups-to-microsoft-365-groups-in-outlook"></a>Utilisez l’EAC classique pour mettre à niveau un ou plusieurs groupes de listes de distribution vers Groupes Microsoft 365 dans Outlook

1. Accédez au centre d’administration Exchange > **groupes de destinataires**\>.<a href="https://go.microsoft.com/fwlink/?linkid=2183233" target="_blank"></a><br/>Vous verrez une notification indiquant que vous disposez de listes de distribution (également appelées **groupes de distribution**) qui peuvent être mises à niveau vers Groupes Microsoft 365.<br/> ![Sélectionnez le bouton Démarrage.](../../media/8cf838b4-2644-401f-a366-08c1eea183eb.png)

1. Sélectionnez une ou plusieurs listes de distribution (également appelées **groupes de distribution**) dans la page **des groupes** .<br/>![Sélectionnez un groupe de distribution.](../../media/2c303433-d60b-4100-a6ae-5809b03a8cdb.png)

1. Sélectionnez l’icône de mise à niveau.<br/>![Mettre à niveau vers l’icône Groupes Microsoft 365.](../../media/1e28cb3d-bff3-4be3-8329-1902d2d54720.png)

1. Dans la boîte de dialogue d’informations, sélectionnez **Oui** pour confirmer la mise à niveau. Le processus commence immédiatement. Selon la taille et le nombre de DLL que vous mettez à niveau, le processus peut prendre des minutes ou des heures.<br/>Si la liste de distribution ne peut pas être mise à niveau, une boîte de dialogue s’affiche. Voir [quelles listes de distribution ne peuvent pas être mises à niveau ?](#which-distribution-lists-cant-be-upgraded)

1. Si vous mettez à niveau plusieurs listes de distribution, utilisez la liste déroulante pour filtrer les listes de distribution qui ont été mises à niveau. Si la liste n’est pas terminée, patientez un certain temps, puis sélectionnez **Actualiser** pour voir ce qui a été correctement mis à niveau.<br/>Aucun avis ne vous indique quand le processus de mise à niveau est terminé pour toutes les DLL que vous avez sélectionnées. Vous pouvez résoudre ce problème en recherchant ce qui est répertorié sous **Disponible pour la mise à niveau** ou **les DLL mises à niveau**.

1. Si vous avez sélectionné une DL pour la mise à niveau, mais qu’elle est toujours affichée sur la page comme Disponible pour la mise à niveau, la mise à niveau n’a pas pu être effectuée. Découvrez [ce qu’il faut faire si la mise à niveau ne fonctionne pas](#what-to-do-if-the-upgrade-doesnt-work).

> [!NOTE]
> Si vous recevez les e-mails de synthèse de groupes, vous remarquerez peut-être en bas qu’il vous sera parfois proposé de mettre à niveau toutes les listes de distribution éligibles dont vous êtes le propriétaire. Pour plus d’informations sur les [e-mails digest, consultez La conversation de groupe dans Outlook](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22).

## <a name="what-to-do-if-the-upgrade-doesnt-work"></a>Que faire si la mise à niveau ne fonctionne pas

Les listes de distribution qui ne parviennent pas à mettre à niveau restent inchangées.

Si une ou plusieurs listes de distribution **éligibles** ne parviennent pas à être mises à niveau, 

1. Utilisez [ce script](https://aka.ms/DLToM365Group) pour rechercher d’éventuels problèmes qui peuvent empêcher la mise à niveau de la liste de distribution vers Microsoft 365 groupe, résoudre les problèmes signalés par le script et essayer une fois de plus de mettre à niveau la liste de distribution. 

2. Si le script ci-dessus n’aide pas ou si le problème persiste, [ouvrez un ticket de support](../../business-video/get-help-support.md). Le problème devra être remonté à l’équipe d’ingénierie des groupes pour qu’elle puisse déterminer le problème.

## <a name="how-to-use-powershell-to-upgrade-several-distribution-lists-at-the-same-time"></a>Comment utiliser PowerShell pour mettre à niveau plusieurs listes de distribution en même temps

Si vous avez l’expérience de l’utilisation de PowerShell, vous souhaiterez peut-être utiliser cette route au lieu d’utiliser l’interface utilisateur. Nous avons un ensemble d’applets de commande qui vous aideront à mettre à niveau les listes de distribution. Voir ci-dessous.

### <a name="upgrade-a-single-dl"></a>Mettre à niveau une seule DL

Pour mettre à niveau une seule DL, exécutez la commande suivante :

```PowerShell
Upgrade-DistributionGroup -DlIdentities <Dl SMTP address>
```

Par exemple, si vous souhaitez mettre à niveau une DL avec l’adresse SMTP dl1@contoso.com, exécutez la commande suivante :

```PowerShell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com
```

> [!NOTE]
> Vous pouvez également mettre à niveau une liste de distribution unique vers un groupe Microsoft 365 à l’aide de l’applet de commande PowerShell [New-UnifiedGroup](/powershell/module/exchange/new-unifiedgroup)

### <a name="upgrade-multiple-dls-in-a-batch"></a>Mettre à niveau plusieurs DLL dans un lot

Vous pouvez également passer plusieurs DLL en tant que lot et les mettre à niveau ensemble :

```PowerShell
Upgrade-DistributionGroup -DlIdentities <DL SMTP address1>, <DL SMTP address2>,
<DL SMTP address3>, <DL SMTP address4>
```

Par exemple, si vous souhaitez mettre à niveau cinq DLL avec une adresse `dl1@contoso.com` SMTP et`dl2@contoso.com`, `dl4@contoso.com` `dl3@contoso.com`et`dl5@contoso.com`, exécutez la commande suivante :

```powershell
Upgrade-DistributionGroup -DlIdentities dl1@contoso.com, dl2@contoso.com, dl3@contoso.com, dl4@contoso.com, dl5@contoso.com
```

### <a name="upgrade-all-eligible-dls"></a>Mettre à niveau toutes les DLL éligibles

Il existe deux façons de mettre à niveau toutes les DLL éligibles.

> [!NOTE]
> L’applet de commande Upgrade-DistributionGroup ne reçoit pas de données du pipeline, c’est pourquoi il est nécessaire d’utiliser l’opérateur « foreach-object{} » pour s’exécuter correctement.

1. Obtenez les DLL éligibles dans le locataire et mettez-les à niveau à l’aide de la commande de mise à niveau :

   ```PowerShell
   Get-EligibleDistributionGroupForMigration | Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

2. Obtenez la liste de toutes les DLL et mettez à niveau uniquement les DLL éligibles :

   ```PowerShell
   Get-DistributionGroup| Foreach-Object{
       Upgrade-DistributionGroup -DlIdentities $_.PrimarySMTPAddress
   }
   ```

## <a name="faq-about-upgrading-distribution-lists-to-microsoft-365-groups-in-outlook"></a>FAQ sur la mise à niveau des listes de distribution vers Groupes Microsoft 365 dans Outlook

### <a name="which-distribution-lists-cant-be-upgraded"></a>Quelles listes de distribution ne peuvent pas être mises à niveau ?

Vous pouvez uniquement mettre à niveau des listes de distribution gérées par le cloud, simples et non imbriqués. Le tableau ci-dessous répertorie les listes de distribution qui **NE PEUVENT PAS** être mises à niveau.

|Propriété|Éligible ?|
|---|---|
|Liste de distribution gérée localement.|Non|
|Listes de distribution imbriquées. La liste de distribution a des groupes enfants ou est membre d’un autre groupe.|Non|
|Listes de distribution avec **les membres RecipientTypeDetails** autres que **UserMailbox**, **SharedMailbox**, **TeamMailbox**, **MailUser**|Non|
|Liste de distribution qui compte plus de 100 propriétaires|Non|
|Liste de distribution qui n’a que des membres, mais pas de propriétaire|Non|
|Liste de distribution contenant des alias contenant des caractères spéciaux|Non|
|Si la liste de distribution est configurée pour être une adresse de transfert pour la boîte aux lettres partagée|Non|
|Si la DL fait partie de **Restriction de l’expéditeur** dans une autre DL.|Non|
|Groupes de sécurité|Non|
|Listes de distribution dynamiques|Non|
|Listes de distribution qui ont été converties en **RoomLists**|Non|

### <a name="check-which-dls-are-eligible-for-upgrade"></a>Vérifier les DLL éligibles à la mise à niveau

Si vous souhaitez vérifier si une DL est éligible ou non, vous pouvez exécuter la commande ci-dessous :

```PowerShell
Get-DistributionGroup <DL SMTP address> | Get-EligibleDistributionGroupForMigration
```

Si vous souhaitez vérifier les DLL éligibles à la mise à niveau, exécutez simplement la commande suivante :

```PowerShell
Get-EligibleDistributionGroupForMigration
```

### <a name="who-can-run-the-upgrade-scripts"></a>Qui pouvez exécuter les scripts de mise à niveau ?

Personnes disposant de droits d’administrateur général ou de Exchange.

### <a name="why-is-the-contact-card-still-showing-a-distribution-list-what-should-i-do-to-prevent-an-upgraded-distribution-list-from-showing-up-in-my-auto-suggest-list"></a>Pourquoi la carte de visite affiche-t-elle toujours une liste de distribution ? Que dois-je faire pour empêcher l’affichage d’une liste de distribution mise à niveau dans ma liste de suggestion automatique ?

- Pour Outlook : quand une personne tente d’envoyer un e-mail dans Outlook en tapant le nom du groupe Microsoft 365 après la migration, le destinataire est résolu en tant que liste de distribution au lieu du groupe. La carte de visite du destinataire sera la carte de visite des listes de distribution. Cela est dû au cache du destinataire ou au cache de noms nick dans Outlook. L’e-mail est envoyé correctement au groupe, mais peut entraîner une confusion pour l’expéditeur.<br/>Vous pouvez effectuer les étapes décrites dans cet article, [informations sur la Outlook liste de saisie semi-automatique](/outlook/troubleshoot/contacts/information-about-the-outlook-autocomplete-list) pour réinitialiser le cache, ce qui résout ce problème.

- Pour Outlook sur le web : en cas de Outlook sur le web, le destinataire de la liste de distribution reste dans le cache. Vous pouvez suivre les étapes décrites dans [Supprimer le nom suggéré ou l’adresse e-mail de la liste de saisie semi-automatique](https://support.microsoft.com/office/9E1419D9-E88F-445B-B07F-F558B8A37C58) pour actualiser le cache afin d’afficher la carte de visite du groupe.

### <a name="do-new-group-members-get-a-welcome-email-in-their-inbox"></a>Les nouveaux membres du groupe reçoivent-ils un e-mail de bienvenue dans leur boîte de réception ?

Non. Le paramètre permettant d’activer les messages d’accueil est défini sur false par défaut. Ce paramètre affecte à la fois les membres de groupe existants et nouveaux qui peuvent rejoindre une fois la migration terminée. Si le propriétaire du groupe autorise ultérieurement les utilisateurs invités, les utilisateurs invités ne recevront pas d’e-mail de bienvenue dans leur boîte de réception. Les membres invités peuvent continuer à travailler avec le groupe.

### <a name="what-if-one-or-some-of-the-dls-are-not-upgraded"></a>Que se passe-t-il si une ou une partie des DLL ne sont pas mises à niveau ?

Dans certains cas, bien que DL soit éligible, mais qu’il n’a pas pu être mis à niveau. Le DL n’est pas mis à niveau et reste en tant que DL.

- Lorsque l’administrateur a appliqué une stratégie **d’adresse e-mail** de groupe pour les groupes d’une organisation et qu’il tente de mettre à niveau des DLL qui ne répondent pas aux critères, la DL n’est pas mise à niveau

- Les DLL avec **MemberJoinRestriction** ou **MemberDepartRestriction** définies sur **Closed** n’ont pas pu être mises à niveau

- La création de groupes Microsoft 365 n’est autorisée qu’à un nombre restreint d’utilisateurs, en suivant les étapes de [cet article](/microsoft-365/solutions/manage-creation-of-groups). Dans ce scénario, si le propriétaire de la liste de distribution n’est pas autorisé à créer Microsoft 365 Groupe, la liste de distribution ne sera pas mise à niveau vers Microsoft 365 Groupe.
Solution de contournement : utilisez l’une des solutions de contournement suivantes pour le scénario ci-dessus :

1. Vérifiez que tous les utilisateurs mentionnés en tant que propriétaires du DL sont autorisés à créer le groupe M365, c’est-à-dire qu’ils sont membres du groupe de sécurité autorisé au groupe M365.

   OR

2. Remplacez temporairement le propriétaire du DL qui n’est pas autorisé à créer le groupe M365 par l’utilisateur autorisé à créer le groupe M365.

### <a name="what-happens-to-the-dl-if-the-upgrade-from-eac-fails"></a>Que se passe-t-il pour la DL en cas d’échec de la mise à niveau à partir d’EAC ?

La mise à niveau se produit uniquement lorsque l’appel est envoyé au serveur. Si la mise à niveau échoue, vos DL sont intactes. Ils fonctionneront comme avant.

### <a name="what-happens-to-message-approval-moderation-settings-on-distribution-groups-after-upgrading"></a>Qu’advient-il des paramètres d’approbation de message (modération) sur les groupes de distribution après la mise à niveau ?

Les paramètres d’approbation de message (modération) sont conservés et continuent de fonctionner correctement après la mise à niveau du groupe de distribution vers un groupe Microsoft 365.

## <a name="related-content"></a>Contenu associé

[Comparer des groupes](../create-groups/compare-groups.md) (article)\
[Explication Groupes Microsoft 365 à vos utilisateurs](../create-groups/explain-groups-knowledge-worker.md) (article)\
[Ajouter ou supprimer des membres de groupes Microsoft 365 à l’aide du Centre d’administration](../create-groups/add-or-remove-members-from-groups.md)
