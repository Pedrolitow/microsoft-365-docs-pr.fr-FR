---
title: Centre de messages dans le Centre d'administration Microsoft 365
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
description: Obtenez une vue d’ensemble du Centre de messages Microsoft 365 et de son rôle dans le suivi des fonctionnalités nouvelles et modifiées et d’autres annonces importantes.
ms.openlocfilehash: 403b16f0f1624034a1224dfe53841a81ee53d572
ms.sourcegitcommit: 2f6a7410e9919f753a759c1ada441141e18f06fd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/30/2022
ms.locfileid: "67085660"
---
# <a name="track-new-and-changed-features-in-the-microsoft-365-message-center"></a>Suivre les fonctionnalités nouvelles et modifiées dans le Centre de messages Microsoft 365

Pour suivre les modifications à venir, notamment les fonctionnalités nouvelles et modifiées, la maintenance planifiée ou d’autres annonces importantes, accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2070717" target="_blank">Centre</a> des messages.
  
Pour ouvrir le centre de messages :

::: moniker range="o365-worldwide"

- Dans le centre d’administration, **accédez au** <a href="https://go.microsoft.com/fwlink/p/?linkid=2070717" target="_blank">Centre de messages</a> d’intégrité.>

::: moniker-end

::: moniker range="o365-21vianet"

- Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">centre d’administration</a>, **accédez au** **Centre de messages** d’intégrité.>

::: moniker-end

Vous pouvez également utiliser [l’application Administration Microsoft 365](https://go.microsoft.com/fwlink/p/?linkid=627216) sur votre appareil mobile pour afficher le Centre de messages, ce qui est un excellent moyen de rester à jour avec les notifications Push.

Pour vous désabonner des e-mails du Centre de messages, consultez [Désabonnement des e-mails du Centre de](#unsubscribe-from-message-center-emails) messages dans cet article.

## <a name="frequently-asked-questions"></a>Foire aux questions

<br>

****

|Question|Réponse|
|---|---|
|Qui peut afficher les billets dans le Centre de messages ?|La plupart des utilisateurs auxquels un rôle d’administrateur a été attribué dans Microsoft 365 peuvent afficher les publications du Centre de messages. [Voici une liste](#admin-roles-that-dont-have-access-to-the-message-center) des rôles d’administrateur qui n’ont pas accès au Centre de messages. Vous pouvez également attribuer le rôle Lecteur du Centre de messages aux utilisateurs qui doivent être en mesure de lire et de partager des publications du Centre de messages sans avoir d’autres privilèges d’administrateur.|
|Est-ce la seule façon dont Microsoft communiquera les modifications concernant Microsoft 365 ?|Non, mais le Centre des messages est le principal moyen de communiquer le minutage des modifications individuelles dans Microsoft 365. Pour plus d’informations sur les ressources supplémentaires, consultez [Rester informé des modifications apportées à Microsoft 365](stay-on-top-of-updates.md) .|
|Comment puis-je voir des billets dans ma langue ?|Les billets du centre de messages sont écrits uniquement en anglais, mais vous pouvez contrôler si, par défaut, les publications sont affichées en anglais ou sont automatiquement traduites à l’ordinateur dans la langue de votre choix. Vous pouvez également sélectionner la traduction automatique de billets dans n’importe quelle langue prise en charge. Pour plus d’informations, consultez [La traduction de langue pour les billets du Centre](language-translation-for-message-center-posts.md) de messages.|
|Puis-je afficher un aperçu des modifications ou des fonctionnalités avant leur déploiement dans mon organisation ?|Vous pouvez afficher un aperçu de certaines modifications et de nouvelles fonctionnalités en optant pour le programme de mise en production ciblée. Pour participer, dans le centre d’administration, accédez aux **préférences** >  de **publication** du **profil** >  d’organisation **paramètres** >  de l’organisation. (Dans le centre d’administration, vous devrez peut-être sélectionner **Afficher tout** en bas du volet de navigation gauche pour voir **Paramètres**.) Vous pouvez choisir la version ciblée pour l’ensemble de votre organisation ou uniquement pour les utilisateurs sélectionnés. Pour plus d’informations sur le programme, consultez [les options de publication standard ou ciblée dans Microsoft 365](release-options-in-office-365.md) .|
|Puis-je déterminer la date exacte à laquelle une modification sera disponible pour mon organisation ?|Malheureusement, nous ne pouvons pas vous dire la date exacte à laquelle une modification sera apportée à votre organisation. Dans notre billet du Centre de messages, nous fournirons autant d’informations que possible sur le calendrier de la publication, en fonction de notre niveau de confiance. Nous travaillons à des améliorations pour améliorer ce niveau de détail.|
|Ces messages sont-ils spécifiques à mon organisation ?|Nous faisons de notre mieux pour vous assurer que vous ne voyez que les publications du Centre de messages qui affectent votre organisation. La feuille de route Microsoft 365 inclut toutes les fonctionnalités sur laquelle nous travaillons actuellement et que nous déployons, mais toutes ces fonctionnalités ne s’appliquent pas à toutes les organisations.|
|Puis-je recevoir des messages électroniques du centre de messages à la place ?|Oui. Vous pouvez choisir d’envoyer un résumé hebdomadaire par e-mail à vous et jusqu’à deux autres adresses e-mail. La synthèse hebdomadaire par e-mail est activée par défaut. Si vous n’obtenez pas vos synthèses hebdomadaires, vérifiez votre dossier de courrier indésirable. Pour plus d’informations sur la configuration de la synthèse hebdomadaire, consultez la section [Préférences](#preferences) de cet article.|
|Comment faire arrêter d’obtenir la synthèse du centre de messages ?|Accédez au Centre de messages dans le centre d’administration et sélectionnez **Préférences**. Sous l’onglet **Email**, désactivez l’option permettant de **m’envoyer des notifications par e-mail à partir du centre de messages**.|
|Comment puis-je m’assurer que les notifications de confidentialité des données sont reçues par les bons contacts de mon organisation ?|En tant qu’administrateur général, vous recevrez des messages de confidentialité des données pour votre organisation. En outre, vous pouvez attribuer le rôle de lecteur de confidentialité du Centre de messages aux personnes qui doivent voir les messages de confidentialité des données. Les autres rôles d’administrateur ayant accès au Centre de messages ne peuvent pas afficher les messages de confidentialité des données.   <br/><br/>Pour plus d’informations, consultez [Préférences](#preferences) dans cet article.|
|Pourquoi ne puis-je pas voir un message qui existait précédemment ?|Pour gérer le nombre de messages dans le centre de messages, chaque message expire et est supprimé après un certain temps. En règle générale, les messages expirent 30 jours après la période décrite dans le corps du message.|
|

## <a name="filter-messages"></a>Filtrer les messages

Le centre de messages présente une vue de tous les messages actifs dans un format de tableau. Par défaut, il affiche le message le plus récent en haut de la liste. Vous pouvez sélectionner **Service** pour afficher les messages de différents services, tels que Microsoft 365 Apps, SharePoint Online, etc.   Sous **Balise**, vous pouvez sélectionner **Administration impact**, **Confidentialité des données**, **Mise à jour des fonctionnalités**, **Mise à jour majeure**, **Nouvelle fonctionnalité**, **Mise hors service** ou **Messages d’impact utilisateur**. Sous **l’état Message** , vous pouvez sélectionner **Favoris**, **Non lus** ou **Messages mis à jour** .

L’onglet Archive affiche les messages que vous avez archivés. Pour archiver un message, dans le volet des messages, sélectionnez **Archiver**.

::: moniker range="o365-worldwide"

Utilisez les menus déroulant **Service**, **Balise** et **État de message** pour sélectionner un affichage filtré des messages. Par exemple, dans ce diagramme, les messages sont balisé par la balise **Impact de l’administrateur**.

Vous pouvez sélectionner n’importe quel en-tête de colonne, sauf **Service** et **Balise**, pour trier les messages dans l’ordre croissant ou décroissant.

:::image type="content" source="../../media/message-center-admin-impact1.png" alt-text="Affichage du centre de messages trié par impact Administration.":::

::: moniker-end

::: moniker range="o365-21vianet"

Utilisez les menus déroulant **Service**, **Balise** et **État de message** pour sélectionner un affichage filtré des messages. Par exemple, dans ce diagramme, les messages sont balisé par **Impact de l’administrateur**.

Vous pouvez sélectionner n’importe quel en-tête de colonne, sauf **Service** et **Balises**, pour trier les messages dans l’ordre croissant ou décroissant.

::: moniker-end

### <a name="major-updates"></a>Mises à jour majeures

Les mises à jour majeures peuvent être examinées en sélectionnant la **mise à jour majeure** dans la liste déroulante **Balises** .

Les mises à jour majeures sont communiquées au moins 30 jours à l’avance lorsqu’une action est requise et peut inclure :

- Modifications apportées à la productivité quotidienne, telles que la boîte de réception, les réunions, les délégations, le partage et l’accès
- Modifications apportées aux thèmes, composants WebPart et autres composants susceptibles d’affecter les fonctionnalités personnalisées
- Augmente ou diminue la capacité visible, telle que le stockage, le nombre de règles, d’éléments ou de durées
- Modifications apportées à la personnalisation du produit qui peuvent :
  - Provoquer la confusion de l’utilisateur final,
  - Entraînez des modifications apportées aux processus du support technique et aux documents de référence, ou
  - Modifier une URL
- Un nouveau service ou une nouvelle application
- Modifications nécessitant une action d’administration (sans empêcher ou corriger les problèmes)
- Modifications apportées à l’emplacement de stockage de vos données
  
### <a name="preferences"></a>Préférences

Si l’administration est distribuée au sein de votre organisation, il se peut que vous ne souhaitiez pas ou n’ayez pas besoin de voir des publications sur tous les services Microsoft 365. Chaque administrateur peut :

- Définissez les préférences qui contrôlent les messages affichés dans le Centre de messages.
- Filtrer les messages
- Définissez les préférences de courrier pour recevoir un résumé hebdomadaire de tous les messages, e-mails pour les mises à jour majeures uniquement et e-mails pour les messages de confidentialité des données.  

::: moniker range="o365-worldwide"

1. Sélectionnez **Préférences** en haut du centre de messages.

2. Dans l’onglet **Affichage personnalisé** , vérifiez que la case à cocher est cochée pour chaque service que vous souhaitez surveiller. Désactivez les cases à cocher des services que vous souhaitez filtrer hors de votre affichage centre de messages.

3. Les e-mails Digest sont activés par défaut et envoyés à votre adresse e-mail principale. Pour arrêter de recevoir la synthèse hebdomadaire, **désactivez la case à cocher Envoyer des notifications par e-mail à partir du centre de messages** **dans l’onglet Email**. 

   Vous pouvez également entrer jusqu’à deux adresses e-mail, séparées par un point-virgule.

   Vous pouvez également choisir les e-mails que vous souhaitez obtenir, ainsi qu’un résumé hebdomadaire des services que vous sélectionnez.

4. Sélectionnez **Enregistrer** pour conserver vos modifications.
  
::: moniker-end

::: moniker range="o365-21vianet"

1. Sélectionnez **Préférences** en haut du centre de messages.

2. Dans l’onglet **Affichage personnalisé** , vérifiez que la case à cocher est cochée pour chaque service que vous souhaitez surveiller. Désactivez les cases à cocher des services que vous souhaitez filtrer hors de votre affichage centre de messages.

3. Les e-mails Digest sont activés par défaut et envoyés à votre adresse e-mail principale. Pour arrêter de recevoir la synthèse hebdomadaire, **désactivez la case à cocher Envoyer des notifications par e-mail à partir du centre de messages** **dans l’onglet Email**.

   Vous pouvez également entrer jusqu’à deux adresses e-mail, séparées par un point-virgule.

   Vous pouvez également choisir les e-mails que vous souhaitez obtenir, ainsi qu’un résumé hebdomadaire des services que vous sélectionnez.

4. Sélectionnez **Enregistrer** pour conserver vos modifications.

::: moniker-end

### <a name="display-messages-in-your-preferred-language"></a>Afficher les messages dans la langue de votre choix
  
Nous utilisons la traduction automatique pour afficher automatiquement les messages dans votre langue préférée. Pour plus d’informations sur la définition de votre langue, lisez [Traduction de langue pour les billets du Centre de messages](language-translation-for-message-center-posts.md).
  
> [!NOTE]
> Le résumé hebdomadaire et tous les billets envoyés par e-mail sont envoyés en anglais uniquement. Les destinataires peuvent utiliser [Translator pour Outlook pour](https://support.microsoft.com/office/3d7e12ed-99d6-406e-a453-b9db0d9653fa) lire le message dans leur langue préférée.

## <a name="monthly-active-users"></a>Utilisateurs actifs mensuels

Lorsque vous ouvrez un billet de centre de messages, nous vous indiquerons le nombre d’utilisateurs qui ont utilisé cette application ou service Microsoft 365 dans la section **Service & utilisateurs actifs mensuels** . Les nombres sont pour les 28 derniers jours. Ces informations peuvent vous aider à hiérarchiser les modifications sur lesquelles vous devez travailler.

:::image type="content" source="../../media/msgctr-mau-teams.png" alt-text="Capture d’écran : Affichage de la page densité de conversation Microsoft Teams dans le billet du centre de messages avec les données utilisateur actives mensuelles":::

Le nombre d’utilisateurs mensuels s’applique à tous les utilisateurs qui ont utilisé cette application ou service Microsoft 365 sur n’importe quel appareil.

> [!NOTE]
> Cette fonctionnalité n’est pas encore disponible pour toutes les applications et services Microsoft 365. Nous vous informerons quand la fonctionnalité n’est pas disponible.

## <a name="choose-columns"></a>Choisir les colonnes

Pour choisir des colonnes, dans la page **Centre** de messages, à l’extrême droite, **sélectionnez Choisir des colonnes**, puis, dans le volet **Choisir des colonnes, sélectionnez** celles que vous souhaitez afficher.

Voici une vue d’ensemble rapide des informations que vous verrez dans chaque colonne.

### <a name="column-information"></a>Informations sur les colonnes

<br>

****

|Colonne|Description|
|---|---|
|Coche|La sélection de la coche dans la ligne d’en-tête de colonne permet de sélectionner tous les messages actuellement affichés. La sélection de la coche en regard d’un ou de plusieurs messages vous permet d’agir sur ces messages.|
|Titre du message|Les titres des messages sont de brèves descriptions des modifications à venir. Si le titre complet ne s’affiche pas, placez le curseur sur celui-ci et l’intégralité du titre s’affiche dans une zone contextuelle.|
|Service|Les icônes indiquent l’application à laquelle le message s’applique.|
|Plus d'options|D’autres options vous permettent de masquer un message, de le marquer comme lu ou non lu, ou de le partager avec un autre administrateur. Pour restaurer un message archivé, sélectionnez l’onglet **Archive** , cochez la case en regard du message, puis sélectionnez **Restaurer**.|
|Balises| Vous pouvez choisir des balises dans la liste déroulante Tag pour filtrer les messages. <br> <p> **Confidentialité des données** : notification de confidentialité des données (limitée aux rôles d’administrateur général et de lecteur de confidentialité du Centre de messages). <p> **Mise à jour majeure** : les modifications ont été communiquées au moins 30 jours à l’avance ([mises à jour majeures](#major-updates)). <p> **Mise hors service** : mise hors service d’un service ou d’une fonctionnalité. <p> **Nouvelle fonctionnalité** : Nouvelle fonctionnalité ou service. <p> **Mise à jour des fonctionnalités** : mise à jour vers une fonctionnalité existante. <p> **Administration impact** : lorsque la modification affecte clairement l’administrateur des manières suivantes : modification de l’interface utilisateur, modification du flux de travail, contrôle disponible et action spécifique/potentielle. <p> **Impact sur l’utilisateur** : lorsque la modification apportée au service affecte clairement l’utilisateur : modification de l’interface utilisateur et modification du flux de travail. <p> **Message mis à jour** : lorsqu’un message est mis à jour.|
|Catégorie| Cette option n’est pas affichée par défaut, mais peut être spécifiée dans le panneau **Choisir des colonnes** . Les messages sont identifiés par l’une des trois catégories suivantes : <p> **Prévenir ou résoudre les problèmes** : vous informe des problèmes connus qui affectent votre organisation et peut vous obliger à prendre des mesures pour éviter les interruptions de service. La prévention ou la résolution des problèmes diffèrent des messages État des services, car ils vous invitent à être proactif pour éviter les problèmes. <p> **Planifier la modification** : vous informe des modifications apportées à Microsoft 365 qui peuvent vous obliger à agir pour éviter les interruptions de service. Par exemple, nous vous informerons des modifications apportées à la configuration requise ou des fonctionnalités qui sont supprimées. Nous essayons de fournir un préavis d’au moins 30 jours de toute modification qui nécessite qu’un administrateur agisse pour que le service s’exécute normalement. <p> **Restez informé** : indique les fonctionnalités nouvelles ou mises à jour que nous activons dans votre organisation. Les fonctionnalités sont généralement annoncées en premier dans la [feuille de route Microsoft 365](https://go.microsoft.com/fwlink/?linkid=2070821). <p> Peut également vous informer sur la maintenance planifiée conformément à notre contrat de niveau de service. La maintenance planifiée peut entraîner un temps d’arrêt, où vous ou vos utilisateurs ne pouvez pas accéder à Microsoft 365, à une fonctionnalité spécifique ou à un service tel qu’un e-mail ou OneDrive Entreprise.|
|Agir par|Nous n’aurons des dates ici que si nous apportons une modification qui vous oblige à prendre une mesure avant une certaine échéance. Étant donné que nous utilisons rarement la **Loi par** colonne, si vous voyez quelque chose ici, vous devez y prêter une attention particulière.|
|Dernière mise à jour|Date à laquelle le message a été publié ou mis à jour pour la dernière fois.|
|Message ID|Microsoft effectue le suivi de nos publications du Centre de messages par ID de message. Vous pouvez faire référence à cet ID si vous souhaitez envoyer des commentaires ou si vous appelez le support technique à propos d’un message particulier.|
|

### <a name="admin-roles-that-dont-have-access-to-the-message-center"></a>Administration rôles qui n’ont pas accès au Centre de messages

- Administrateur de conformité
- Administrateur d’accès conditionnel
- Approbateur d'accès à Customer Lockbox
- Administrateurs d’appareils
- Lecteurs d’annuaires
- Comptes de synchronisation d’annuaires
- Enregistreurs d’annuaires
- Administrateur du service Intune
- Administrateur de rôle privilégié
- Lecteur de rapports

## <a name="give-feedback-on-a-post"></a>Envoyer des commentaires sur un post

Dans le Centre de messages, vous pouvez sélectionner un message pour en voir les détails.

Si vous souhaitez transmettre des commentaires sur le message, dans le volet d’informations, sélectionnez l’icône **J’aime** ou **Je n’aime pas** au bas du volet des détails du message et fournissez éventuellement des commentaires dans la zone de texte qui s’affiche. Ne fournissez aucune information personnelle. Vous pouvez éventuellement sélectionner **Vous pouvez me contacter à propos de ce commentaire**, puis sélectionner **Envoyer**.

> [!NOTE]
> Si vous utilisez Microsoft 365 pour le secteur public - GCC, Microsoft 365 pour le secteur public - GCC High et Office 365 Secteur Public - DoD, vous ne pourrez pas fournir de commentaires sur un billet.

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

Pour une vue d’ensemble du Centre de messages, consultez [Centre de messages dans Microsoft 365](message-center.md). Pour découvrir comment définir vos préférences linguistiques afin d’activer la traduction automatique des publications du Centre de messages, consultez [Traduction pour les publications du Centre de messagerie](language-translation-for-message-center-posts.md). Si vous souhaitez programmer une autre façon d’obtenir des informations d’intégrité du service en temps réel et des communications du Centre de messages, consultez [l’API Utilisation des communications de service dans Microsoft Graph](/graph/api/resources/service-communications-api-overview).

## <a name="unsubscribe-from-message-center-emails"></a>Se désabonner des e-mails du Centre de messages

1. Les e-mails Digest sont activés par défaut et envoyés à votre adresse e-mail principale. Pour arrêter de recevoir le résumé hebdomadaire, sélectionnez **Préférences**, puis **Email**.
    - Désélectionnez la case à cocher **Envoyer un résumé hebdomadaire de mes messages** .
    - Email notification pour les mises à jour majeures est un contrôle distinct. Si vous ne souhaitez pas recevoir d’avis par e-mail concernant les mises à jour majeures, vérifiez que la case à cocher **Envoyer des e-mails pour les mises à jour majeures** n’est pas cochée.
    - Pour arrêter de recevoir des notifications sur les messages de confidentialité des données, vérifiez que la case à cocher **Envoyer des e-mails pour les messages de confidentialité des données** n’est pas cochée.  (Les messages de confidentialité des données ne sont pas inclus dans le résumé hebdomadaire.)

2. Sélectionnez **Enregistrer** pour conserver vos modifications.

## <a name="related-content"></a>Contenu associé

[Configurer les options de publication standard ou ciblée](../manage/release-options-in-office-365.md) (article)\
[Gérer les fonctionnalités Office qui apparaissent dans Nouveautés](../manage/show-hide-new-features.md) (article)\
[Abonnements professionnels et documentation de facturation](../../commerce/index.yml) (page de lien)
