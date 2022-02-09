---
title: Centre de messages
f1.keywords:
- CSH
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
- okr_smb
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 38fb3333-bfcc-4340-a37b-deda509c2093
description: Obtenez une vue d’Microsoft 365 centre de messages et son rôle dans le suivi des fonctionnalités nouvelles et modifiées et d’autres annonces importantes.
ms.openlocfilehash: 42549156172c0ed529dfb84619836c2e40f42fe8
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62463627"
---
# <a name="message-center"></a>Centre de messages

Pour suivre les modifications à venir, y compris les fonctionnalités nouvelles et modifiées, la maintenance planifiée ou d’autres annonces importantes, allez dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2070717" target="_blank">Centre de messages</a>.
  
Pour ouvrir le Centre de messages :

::: moniker range="o365-worldwide"

- Dans le centre d’administration, allez au **centre de messages d’état** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2070717" target="_blank">d’santé</a>.

::: moniker-end

::: moniker range="o365-21vianet"

- Dans le centre <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">d’administration</a>, allez au **centre de messages d’état** > **d’santé**.

::: moniker-end

Vous pouvez également utiliser [l’application Administration Microsoft 365 sur](https://go.microsoft.com/fwlink/p/?linkid=627216) votre appareil mobile pour afficher le centre de messages, ce qui constitue un excellent moyen de rester informé des notifications Push.

Pour vous désabonner des e-mails du Centre de messages, consultez [l’article Unsubscribe from Message center emails](#unsubscribe-from-message-center-emails) in this article.

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

<br>

****

|Question|Réponse|
|---|---|
|Qui pouvez-vous afficher les billets dans le Centre de messages ?|La plupart des utilisateurs qui ont reçu un rôle d’administrateur dans Microsoft 365 peuvent afficher les billets du centre de messages. [Voici une liste des rôles](#admin-roles-that-dont-have-access-to-the-message-center) d’administrateur qui n’ont pas accès au centre de messages. Vous pouvez également attribuer le rôle de lecteur du centre de messages aux utilisateurs qui doivent pouvoir lire et partager des billets du Centre de messages sans disposer d’autres privilèges d’administrateur.|
|Est-ce la seule façon pour Microsoft de communiquer les modifications Microsoft 365 ?|Non, mais le centre de messages est le principal moyen de communiquer le minutage des modifications individuelles dans Microsoft 365. Pour [plus d’informations sur les ressources supplémentaires, Microsoft 365](stay-on-top-of-updates.md) restez au fait des modifications apportées.|
|Comment puis-je voir les billets dans ma langue ?|Les publications du centre de messages sont écrites en anglais uniquement, mais vous pouvez contrôler si, par défaut, les publications sont affichées en anglais ou sont automatiquement traduites par machine dans votre langue préférée. Vous pouvez également choisir de traduire des billets par machine dans n’importe quelle langue prise en charge. Pour [plus d’informations, voir Traduction linguistique pour les publications](language-translation-for-message-center-posts.md) du centre de messages.|
|Puis-je prévisualiser les modifications ou les fonctionnalités avant qu’elles ne soient déployées dans mon organisation ?|Certaines modifications et nouvelles fonctionnalités peuvent être prévisualiser en optant pour le programme de publication ciblée. Pour l’opter, dans le Centre d’administration, **Paramètres** >  **Préférences** >  >  de profil **d’organisation de l’organisation**. (Dans le Centre d’administration, vous devrez  peut-être sélectionner Afficher tout en bas du volet de navigation gauche pour afficher **Paramètres**.) Vous pouvez choisir la version ciblée pour l’ensemble de votre organisation ou uniquement pour les utilisateurs sélectionnés. Pour plus [d’informations sur le programme, voir les options de publication standard](release-options-in-office-365.md) Microsoft 365 ciblées.|
|Puis-je déterminer la date exacte à laquelle une modification sera disponible pour mon organisation ?|Malheureusement, nous ne pouvons pas vous indiquer la date exacte à laquelle une modification sera apporté à votre organisation. Dans notre billet de centre de messages, nous fournirons autant d’informations que possible sur le minutage de la publication, en fonction de notre niveau de confiance. Nous travaillons sur des améliorations pour améliorer ce niveau de détail.|
|Ces messages sont-ils spécifiques à mon organisation ?|Nous faisons de notre mieux pour vous assurer que seuls les billets du Centre de messages affectent votre organisation. La Microsoft 365 comprend toutes les fonctionnalités que nous travaillons actuellement et que nous appliquons, mais toutes ces fonctionnalités ne s’appliquent pas à toutes les organisations.|
|Puis-je recevoir des billets du centre de messages par courrier électronique à la place ?|Oui. Vous pouvez choisir de vous envoyer un résumé hebdomadaire et jusqu’à deux autres adresses de messagerie. Le résumé hebdomadaire envoyé par courrier électronique est allumé par défaut. Si vous n’avez pas vos résumés hebdomadaires, vérifiez votre dossier de courrier indésirable. Pour plus [d’informations](#preferences) sur la façon de configurer le résumé hebdomadaire, voir la section Préférences de cet article.|
|Comment arrêter d’obtenir le résumé du centre de messages ?|Go to Message center in the admin center and select **Preferences**. Dans **l’onglet Courrier** électronique, désactiver l’option **m’envoyer des notifications par courrier électronique à partir du centre de messages**.|
|Comment puis-je m’assurer que les notifications de confidentialité des données sont reçues par les contacts de mon organisation ?|En tant qu’administrateur global, vous recevrez des messages de confidentialité des données pour votre organisation. En outre, vous pouvez attribuer le rôle de lecteur confidentialité du Centre de messages aux personnes qui doivent voir les messages de confidentialité des données. Les autres rôles d’administrateur ayant accès au Centre de messages ne peuvent pas afficher les messages de confidentialité des données.   <br/><br/>Pour plus d’informations, voir [Préférences](#preferences) dans cet article.|
|Pourquoi ne puis-je pas voir un message qui s’y trouvait précédemment ?|Pour gérer le nombre de messages dans le centre de messages, chaque message expire et est supprimé après un certain temps. En règle générale, les messages expirent 30 jours après la période décrite dans le corps du message.|
|

## <a name="filter-messages"></a>Filtrer les messages

Le centre de messages présente une vue de tous les messages actifs dans un format de tableau. Par défaut, il affiche le message le plus récent en haut de la liste. Vous pouvez sélectionner **Service** pour voir les messages de différents services, tels que Microsoft 365 Apps, SharePoint Online, etc.   Sous **Balise, vous** pouvez sélectionner **l’impact sur** l’administrateur **, la** confidentialité des **données, la** mise à jour des fonctionnalités **, la** mise à jour **majeure, la** nouvelle **fonctionnalité, la** mise en retrait ou les messages **d’impact sur l’utilisateur**. Sous **État du message** , vous pouvez sélectionner **Favoris**, Non **lu** ou **Mis à** jour.

L’onglet Archive affiche les messages que vous avez archivés. Pour archiver un message, dans le volet de message, sélectionnez **Archive**.

::: moniker range="o365-worldwide"

Utilisez les menus déroulant **Service**, **Balise** et **État de message** pour sélectionner un affichage filtré des messages. Par exemple, dans ce diagramme, les messages sont balisé par la balise **Impact de l’administrateur**.

Vous pouvez sélectionner n’importe quel en-tête de colonne, sauf **Service** et **Balise**, pour trier les messages dans l’ordre croissant ou décroissant.

:::image type="content" source="../../media/message-center-admin-impact1.png" alt-text="Affichage du centre de messages trié par impact sur l’administrateur.":::

::: moniker-end

::: moniker range="o365-21vianet"

Utilisez les menus déroulant **Service**, **Balise** et **État de message** pour sélectionner un affichage filtré des messages. Par exemple, dans ce diagramme, les messages sont balisé par **Impact de l’administrateur**.

Vous pouvez sélectionner n’importe quel en-tête de colonne, sauf **Service** et **Balises**, pour trier les messages dans l’ordre croissant ou décroissant.

::: moniker-end

### <a name="major-updates"></a>Mises à jour majeures

Les mises à jour majeures peuvent être examinées en sélectionnant la mise à jour **majeure dans la** **liste des** balises.

Les mises à jour majeures sont communiquées au moins 30 jours à l’avance lorsqu’une action est requise et peut inclure :

- Modifications apportées à la productivité quotidienne telles que la boîte de réception, les réunions, les délégations, le partage et l’accès
- Modifications apportées aux thèmes, composants Web Parts et autres composants qui peuvent affecter les fonctionnalités personnalisées
- Augmente ou diminue la capacité visible telle que le stockage, le nombre de règles, d’éléments ou de durées
- Modifications apportées à la  branding de produit qui peuvent :
  - Source de confusion pour l’utilisateur final,
  - Apporter des modifications aux processus du service d’aide et au matériel de référence, ou
  - Modifier une URL
- Un nouveau service ou une nouvelle application
- Modifications nécessitant une action de l’administrateur (exclusive des problèmes de prévention ou de correction)
- Modifications apportées à l’endroit où vos données sont stockées
  
### <a name="preferences"></a>Préférences

Si l’administration est distribuée au sein de votre organisation, il se peut que vous ne vouliez ou n’avez pas besoin de voir des billets sur tous Microsoft 365 services. Chaque administrateur peut :

- Définissez des préférences qui contrôlent les messages affichés dans le centre de messages.
- Filtrer les messages
- Définissez les préférences de messagerie pour recevoir un résumé hebdomadaire de tous les messages, des e-mails pour les mises à jour majeures uniquement et des e-mails pour les messages de confidentialité des données.  

::: moniker range="o365-worldwide"

1. **Sélectionnez Préférences en** haut du centre de messages.

2. Dans **l’onglet Affichage** personnalisé, assurez-vous que la case à cocher est sélectionnée pour chaque service que vous souhaitez surveiller. Cochez les cases des services que vous souhaitez filtrer en dehors de votre affichage Centre de messages.

3. Les e-mails Digest sont allumés par défaut et sont envoyés à votre adresse de messagerie principale. Pour arrêter de recevoir le résumé hebdomadaire, cochez la case Envoyer des **notifications** par courrier électronique à partir du centre de messages dans **l’onglet Courrier électronique**. 

   Vous pouvez également entrer jusqu’à deux adresses de messagerie, séparées par un point-virgule.

   Vous pouvez également choisir les e-mails que vous souhaitez obtenir, ainsi qu’un résumé hebdomadaire des services que vous sélectionnez.

4. **Sélectionnez Enregistrer** pour conserver vos modifications.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. **Sélectionnez Préférences en** haut du centre de messages.

2. Dans **l’onglet Affichage** personnalisé, assurez-vous que la case à cocher est sélectionnée pour chaque service que vous souhaitez surveiller. Cochez les cases des services que vous souhaitez filtrer en dehors de votre affichage Centre de messages.

3. Les e-mails Digest sont allumés par défaut et sont envoyés à votre adresse de messagerie principale. Pour arrêter de recevoir le résumé hebdomadaire, cochez la case Envoyer des **notifications** par courrier électronique à partir du centre de messages dans **l’onglet Courrier électronique**.

   Vous pouvez également entrer jusqu’à deux adresses de messagerie, séparées par un point-virgule.

   Vous pouvez également choisir les e-mails que vous souhaitez obtenir, ainsi qu’un résumé hebdomadaire des services que vous sélectionnez.

4. **Sélectionnez Enregistrer** pour conserver vos modifications.

::: moniker-end

### <a name="display-messages-in-your-preferred-language"></a>Afficher les messages dans votre langue préférée
  
Nous utilisons la traduction automatique pour afficher automatiquement les messages dans votre langue préférée. Pour plus d’informations sur la définition de votre langue, lisez [Traduction de langue pour les billets du Centre de messages](language-translation-for-message-center-posts.md).
  
> [!NOTE]
> Le résumé hebdomadaire et les billets envoyés par courrier électronique sont envoyés en anglais uniquement. Les destinataires peuvent [utiliser Traducteur pour Outlook](https://support.microsoft.com/office/3d7e12ed-99d6-406e-a453-b9db0d9653fa) pour lire le message dans leur langue préférée.

## <a name="monthly-active-users"></a>Utilisateurs actifs mensuels

Lorsque vous ouvrez un billet de centre de messages, nous vous indiquerons le nombre d’utilisateurs qui ont utilisé cette application ou service Microsoft 365 dans la section **Utilisateurs** actifs mensuels du Service &. Les chiffres sont les 28 derniers jours. Ces informations peuvent vous aider à hiérarchiser les modifications sur lesquelles vous devez travailler.

:::image type="content" source="../../media/msgctr-mau-teams.png" alt-text="Screenshot: Showing the Microsoft Teams Chat density page in the message center post with monthly active user data":::

Le nombre d’utilisateurs mensuels s’applique à tous les utilisateurs qui ont utilisé cette Microsoft 365 application ou service sur n’importe quel appareil.

> [!NOTE]
> Cette fonctionnalité n’est pas encore disponible pour tous Microsoft 365 applications et services. Nous vous le faire savoir lorsque la fonctionnalité n’est pas disponible.

## <a name="choose-columns"></a>Choisir les colonnes

Pour choisir des colonnes, dans **la page Centre** des messages, à l’extrême droite, sélectionnez Choisir  les colonnes **, puis**, dans le volet Choisir les colonnes, sélectionnez ceux que vous souhaitez afficher.

Voici une vue d’ensemble rapide des informations que vous verrez dans chaque colonne.

### <a name="column-information"></a>Informations sur les colonnes

<br>

****

|Colonne|Description|
|---|---|
|Coche|La sélection de la coche dans la ligne d’en-tête de colonne sélectionne tous les messages actuellement affichés. La sélection de la coche en regard d’un ou de plusieurs messages vous permet d’agir sur ces messages.|
|Titre du message|Les titres des messages sont de brèves descriptions des modifications à venir. Si le titre complet ne s’affiche pas, placez votre curseur sur celui-ci et l’intégralité du titre s’affiche dans une zone de fenêtre pop-up.|
|Service|Les icônes indiquent l’application à laquelle s’applique le message.|
|Plus d'options|D’autres options vous permet de faire disparaître un message, de le marquer comme lu ou non lu, ou de le partager avec un autre administrateur. Pour restaurer un message archivé, sélectionnez **l’onglet Archive** , cochez la coche en regard du message, puis sélectionnez **Restaurer**.|
|Balises| Vous pouvez choisir des balises dans la drop-down Tag pour filtrer les messages. <br> <p> **Confidentialité des données** : notification de confidentialité des données (limitée aux rôles d’administrateur général et de lecteur de confidentialité du centre de messages). <p> **Mise à jour** majeure : modifications communiquées au moins 30 jours à l’avance ([mises à jour majeures](#major-updates)). <p> **Retrait :** retrait d’un service ou d’une fonctionnalité. <p> **Nouvelle fonctionnalité :** nouvelle fonctionnalité ou nouveau service. <p> **Mise à jour de** fonctionnalité : mise à jour d’une fonctionnalité existante. <p> **Impact sur l’administrateur** : lorsque la modification a un impact clair sur l’administrateur des manières suivantes : modification de l’interface utilisateur, modification du flux de travail, contrôle disponible et Action spécifique/potentielle. <p> **Impact sur l’utilisateur** : lorsque la modification du service a un impact clair sur l’utilisateur : modification de l’interface utilisateur et modification du flux de travail. <p> **Message mis à jour** : lorsqu’un message est mis à jour.|
|Catégorie| Cela n’est pas affiché par défaut, mais peut être spécifié dans le panneau Choisir **des colonnes** . Les messages sont identifiés par l’une des trois catégories suivantes : <p> **Éviter ou résoudre les problèmes** : vous informe des problèmes connus qui affectent votre organisation et peut vous obliger à prendre des mesures pour éviter les interruptions de service. La prévention ou la correction des problèmes sont différentes des messages d’état du service, car ils vous invitent à être proactif pour éviter les problèmes. <p> **Planifier le changement** : vous informe des modifications apportées aux Microsoft 365 qui peuvent vous obliger à agir pour éviter les interruptions de service. Par exemple, nous allons vous faire savoir sur les modifications apportées à la requise du système ou sur les fonctionnalités qui sont supprimées. Nous essayons de fournir au moins 30 jours d’avis sur toute modification qui nécessite qu’un administrateur agisse pour que le service fonctionne normalement. <p> **Restez informé** : vous indique les fonctionnalités nouvelles ou mises à jour que nous sommes en train d’allumer dans votre organisation. Les fonctionnalités sont généralement annoncées en premier dans Microsoft 365 [feuille de route.](https://go.microsoft.com/fwlink/?linkid=2070821) <p> Peut également vous faire savoir sur la maintenance planifiée conformément à notre contrat de niveau de service. La maintenance planifiée peut entraîner un temps d’in Microsoft 365 insérez pas, vous ou vos utilisateurs, une fonctionnalité spécifique ou un service tel que le courrier électronique ou les OneDrive Entreprise.|
|Agir par|Nous n’avons des dates ici que si nous a faisons une modification qui nécessite que vous prenons une action avant une certaine échéance. Étant donné que nous utilisons rarement **la loi par** colonne, si vous voyez quelque chose ici, vous devez y prêter une attention particulière.|
|Dernière mise à jour|Date à laquelle le message a été publié ou mis à jour pour la dernière fois.|
|Message ID|Microsoft suit les publications de notre centre de messages par ID de message. Vous pouvez vous référer à cet ID si vous souhaitez envoyer des commentaires ou si vous appelez le support technique à propos d’un message particulier.|
|

### <a name="admin-roles-that-dont-have-access-to-the-message-center"></a>Rôles d’administrateur qui n’ont pas accès au centre de messages

- Administrateur de conformité
- Administrateur d’accès conditionnel
- Approbation d’accès Customer LockBox
- Administrateurs d’appareils
- Lecteurs d’annuaire
- Comptes de synchronisation d’annuaires
- Rédacteurs d’annuaire
- Administrateur du service Intune
- Administrateur de rôle privilégié
- Lecteur de rapports

## <a name="give-feedback-on-a-post"></a>Envoyer des commentaires sur un post

Dans le Centre de messages, vous pouvez sélectionner un message pour en voir les détails.

Si vous souhaitez transmettre des commentaires sur le message, dans le volet d’informations, sélectionnez l’icône **J’aime** ou **Je n’aime pas** au bas du volet des détails du message et fournissez éventuellement des commentaires dans la zone de texte qui s’affiche. Ne fournissez aucune information personnelle. Vous pouvez éventuellement sélectionner **Vous pouvez me contacter à propos de ce commentaire**, puis sélectionner **Envoyer**.

## <a name="share-a-message"></a>Partager un message

Vous voyez un message sur lequel une autre personne doit agir ? Vous pouvez partager le contenu du message avec tous les utilisateurs par courrier électronique :
  
1. Sélectionnez le message pour l’ouvrir, puis sélectionnez **Partager**.
  
2. Pour partager le message, entrez jusqu’à deux adresses de messagerie séparées par un deux-points. Vous pouvez envoyer des messages à des adresses de messagerie individuelles et de groupe. Si vous le souhaitez, vous pouvez choisir de recevoir une copie du message par courrier électronique (celui-ci sera envoyé à votre adresse de messagerie principale) ou d’ajouter un message personnel qui offre davantage de contexte aux destinataires.
  
3. Sélectionnez **Partager** pour envoyer l’e-mail.

## <a name="get-a-link"></a>Obtenir un lien

Vous devez faire un suivi avec un autre administrateur pour vous assurer qu'il est informé d'une modification et qu'il prend des mesures ? Vous pouvez générer un lien à partager par courrier électronique ou messagerie instantanée, par exemple, qui connectera l’utilisateur directement à ce message. La personne avec qui vous partagez le lien doit avoir accès au Centre de messages. Pour plus d'information, consultez [Rôles administratifs qui n'ont pas accès au centre de messages](message-center.md#admin-roles-that-dont-have-access-to-the-message-center).

1. Sélectionnez le message pour l'ouvrir.

2. Sélectionnez **Copier le lien**.

3. Utilisez Ctrl+V ou cliquez avec le bouton droit, puis sélectionnez **Coller** pour insérer le lien vers le document souhaité.

## <a name="read-and-unread-states"></a>États Lu et Non lu

Les messages non lus dans le Centre de messages s’affichent en gras. L’ouverture d’un message le marque comme lu. Vous pouvez marquer un message comme non lu.

Dans la page principale du Centre de messages, sélectionnez les points de suspension **Autres options** à côté d’un message, puis sélectionnez **Marquer comme non lu**.

Vous pouvez également ouvrir un message et le marquer comme non lu dans le panneau d’informations.
  
## <a name="archive-and-restore"></a>Archiver et restaurer

Si vous voyez un message qui ne vous concerne pas ou si vous avez peut-être déjà fait quelque chose, vous pouvez archiver le message pour le supprimer de la boîte de réception. L’affichage que vous voyez dans le Centre de messages est spécifique à votre compte d’utilisateur, aussi l’archivage à partir de votre affichage n’affecte pas les autres administrateurs. Il existe deux façons d’archiver un message.

- Dans la page principale du Centre de messages, sélectionnez un message, puis **Archiver** au-dessus de la liste des messages.
- Ouvrez le message, puis sélectionnez **Archiver** en haut du volet message.

Vous avez besoin de récupérer un message archivé ? Pas de problème.
  
1. Sélectionnez l’onglet **Archive** en haut du Centre de messages. La liste des messages archivés s’affiche.

1. Sélectionnez le message, sélectionnez **Restaurer**, et le message est restauré dans boîte de réception.

## <a name="favorite-messages"></a>Messages favoris

Pour marquer un message comme favori, survolez le titre du message pour voir une étoile **Favoris** :::image type="icon" source="../../media/favorite-star.png" border="false"::: que vous pouvez sélectionner juste après les points de suspension **Autres options**. Une fois que vous avez marqué des messages comme favoris, vous pouvez également les trier et les filtrer.

## <a name="scroll-messages-in-the-message-pane"></a>Faites défiler les messages dans le volet des messages

Lorsque vous ouvrez un message dans un volet de lecture, vous pouvez utiliser les flèches **Haut** et **Bas** :::image type="icon" source="../../media/updownarrows.png" border="false"::: en haut du volet pour passer au message suivant ou précédent dans la liste.

## <a name="track-your-message-center-tasks-in-planner"></a>Suivez les tâches de votre centre de messagerie dans Planner

De nombreuses informations utiles sur les changements apportés aux services Microsoft 365 arrivent dans le centre de messages Microsoft 365. Il peut être difficile de savoir quels changements nécessitent des tâches à accomplir, quand et par qui, et de suivre chaque tâche jusqu'à son achèvement. Vous pouvez également noter quelque chose et l'étiqueter pour le vérifier plus tard. Vous pouvez faire tout cela et bien plus encore lorsque vous synchronisez vos messages du centre d'administration Microsoft 365 avec Planificateur Microsoft. Pour plus d’informations, consultez [Effectuer le suivi de vos tâches de centre de messagerie dans Planificateur](/office365/planner/track-message-center-tasks-planner).

Pour une vue d’ensemble du Centre de messages, consultez [Centre de messages dans Microsoft 365](message-center.md). Pour découvrir comment définir vos préférences linguistiques afin d’activer la traduction automatique des publications du Centre de messages, consultez [Traduction pour les publications du Centre de messagerie](language-translation-for-message-center-posts.md). Si vous souhaitez programmer une autre façon d’obtenir des informations sur l’état du service en temps réel et des communications du centre de messages, veuillez référencer [l’API Working with service communications dans Microsoft Graph](/graph/api/resources/service-communications-api-overview?view=graph-rest-beta).

## <a name="unsubscribe-from-message-center-emails"></a>Se désabonner des messages électroniques du centre de messages

1. Les e-mails Digest sont allumés par défaut et sont envoyés à votre adresse de messagerie principale. Pour arrêter de recevoir le résumé hebdomadaire, sélectionnez **Préférences** , puis Courrier **électronique**.
    - Désélectez la **case Envoyer un résumé hebdomadaire de mes messages** .
    - La notification par courrier électronique pour les mises à jour majeures est un contrôle distinct. Si vous ne souhaitez pas recevoir de notifications par courrier électronique concernant les mises à jour majeures, vérifiez que la case à cocher Envoyer des courriers électroniques pour les mises à jour **majeures** n’est pas sélectionnée.
    - Pour arrêter de recevoir des notifications par courrier électronique concernant les messages  de confidentialité des données, vérifiez que la case à cocher Envoyer des messages de confidentialité des données n’est pas sélectionnée.  (Les messages de confidentialité des données ne sont pas inclus dans le résumé hebdomadaire.)

2. **Sélectionnez Enregistrer** pour conserver vos modifications.

## <a name="related-content"></a>Contenu associé

[Configurer les options de publication standard ou ciblée](../manage/release-options-in-office-365.md) (article)\
[Gérer les Office qui apparaissent dans Nouveautés](../manage/show-hide-new-features.md) (article)\
[Abonnements aux entreprises et documentation de facturation](../../commerce/index.yml) (page de lien)
