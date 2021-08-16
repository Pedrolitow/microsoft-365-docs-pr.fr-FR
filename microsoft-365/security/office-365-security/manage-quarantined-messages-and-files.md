---
title: Gérer les fichiers et les messages mis en quarantaine en tant qu’administrateur
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 065cc2cf-2f3a-47fd-a434-2a20b8f51d0c
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent découvrir comment afficher et gérer les messages mis en quarantaine pour tous les utilisateurs dans Exchange Online Protection (EOP). Les administrateurs des organisations avec Microsoft Defender pour Office 365 peuvent également gérer les fichiers mis en quarantaine dans SharePoint Online, OneDrive Entreprise et Microsoft Teams.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: b041eff9b9849c0ab07f5a4c029d01cc98c4d2a5
ms.sourcegitcommit: 99817013bcb26b7ed051e011c8addb716cc91d8f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/13/2021
ms.locfileid: "58349423"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, voir [Messages électroniques mis en quarantaine dans EOP.](quarantine-email-messages.md)

Les administrateurs peuvent afficher, libérer et supprimer tous les types de messages mis en quarantaine pour tous les utilisateurs. Seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants, hameçonnage à haut niveau de confiance ou suite à des règles de flux de messagerie (également appelées règles de transport). Les administrateurs peuvent également signaler des faux positifs à Microsoft.

Les administrateurs des organisations avec Microsoft Defender pour Office 365 peuvent également gérer les fichiers mis en quarantaine par la mise en quarantaine par les pièces jointes Coffre pour [SharePoint, OneDrive](mdo-for-spo-odb-and-teams.md)et Microsoft Teams .

Vous affichez et gérez les messages mis en quarantaine dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres en Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>. Pour ouvrir la page **de** mise en quarantaine directement, utilisez <https://security.microsoft.com/quarantine> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour prendre des mesures sur les messages mis en quarantaine pour tous les  utilisateurs, vous devez être membre des groupes de rôles Gestion de l’organisation, Administrateur de la sécurité ou Administrateur de la mise en <sup>\*</sup> quarantaine.
  - Pour accéder en lecture seule aux messages mis en quarantaine pour  tous  les utilisateurs, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.
  - <sup>\*</sup>Les membres  du groupe de rôles Administrateur  de mise en quarantaine doivent également être membres du groupe de rôles Gestion de l’hygiène dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) pour pouvoir mettre en quarantaine des procédures dans Exchange Online PowerShell.

- Les messages mis en quarantaine sont conservés pendant une période par défaut avant d’être automatiquement supprimés :
  - 30 jours pour les messages mis en quarantaine par des stratégies anti-courrier indésirable (courrier indésirable, hameçonnage et courrier électronique en masse). Il s’agit de la valeur par défaut et de la valeur maximale. Pour configurer (plus bas) cette valeur, voir [Configurer des stratégies anti-courrier indésirable.](configure-your-spam-filter-policies.md)
  - 15 jours pour les messages contenant des programmes malveillants.
  - 15 jours pour les fichiers mis en quarantaine Coffre pièces jointes pour SharePoint, OneDrive et Microsoft Teams dans Defender pour Office 365.

  Lorsqu’un message arrive à expiration de la quarantaine, vous ne pouvez pas le récupérer.

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Utiliser le portail Microsoft 365 Defender pour gérer les messages électroniques mis en quarantaine

### <a name="view-quarantined-email"></a>Afficher les e-mails mis en quarantaine

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Évaluation** \> **Quarantaine**.
2. Dans la page **Quarantaine,** vérifiez que **l’onglet** Courrier est sélectionné.

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez **sur Personnaliser les colonnes**  pour modifier les colonnes affichées. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

   - **Heure reçue**<sup>\*</sup>
   - **Sujet**<sup>\*</sup>
   - **Expéditeur**<sup>\*</sup>
   - **Raison de la quarantaine**<sup>\*</sup>
   - **État de publication**<sup>\*</sup>
   - **Type de stratégie**<sup>\*</sup>
   - **Expire**<sup>\*</sup>
   - **Destinataire**
   - **ID de message**
   - **Nom de la stratégie**
   - **Taille du message**
   - **Sens du courrier**
   - **Balise de destinataire**

   Lorsque vous avez terminé, cliquez sur **Appliquer.**

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres suivants sont disponibles dans le volant **Filtres** qui s’affiche :
   - **ID du message** : l’identificateur global unique du message.

     Par exemple, [](message-trace-scc.md) vous avez utilisé le suivi des messages pour rechercher un message qui a été envoyé à un utilisateur de votre organisation, et vous déterminez que le message a été mis en quarantaine au lieu d’être remis. Assurez-vous d’inclure la valeur complète de l’ID du message, qui peut inclure des crochets ( \<\> ). Par exemple : `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Adresse de l’expéditeur**
   - **Adresse du destinataire**
   - **Subject**
   - **Heure reçue**: entrez une heure **de début** et une heure **de fin** (date).
   - **Expire :** filtrer les messages de la date d’expiration de la mise en quarantaine :
     - **Aujourd’hui**
     - **Dans les 2 prochains jours**
     - **Dans les 7 prochains jours**
     - **Personnaliser**: Entrer une **Date de début** et une **Date de fin**.
   - **Balise de destinataire**
   - **Raison de la mise en quarantaine :**
     - **Règle de transport** (règle de flux de messagerie)
     - **E-mail de masse**
     - **Courrier indésirable**
     - **Programme malveillant**
     - **Hameçonnage**: le verdict  de filtrage du courrier indésirable était le hameçonnage ou la protection anti-hameçonnage qui a mis en quarantaine le message ( paramètres d’usurpation d’identité ou [protection contre l’usurpation d’identité](configurer des [stratégies](set-up-anti-phishing-policies.md#spoof-settings) anti-hameçonnage.
     - **Hameçonnage à haute fiabilité**
   - **Destinataire**: **tous les utilisateurs** ou **uniquement moi**. Les utilisateurs finaux peuvent uniquement gérer les messages mis en quarantaine qui leur sont envoyés.
   - **État de publication**: L’une des valeurs suivantes :
     - **Révision des besoins**
     - **Approuvé**
     - **Refusé**
     - **Publication demandée**
     - **Released**
   - **Type de stratégie** : filtrer les messages par type de stratégie :
     - **Stratégie anti-programme malveillant**
     - **Coffre Stratégie de pièces jointes**
     - **Politique de lutte contre l'hameçonnage**
     - **Stratégie anti-courrier indésirable**
     - **Règle de transport** (règle de flux de messagerie)

   Lorsque vous avez terminé, cliquez sur **Appliquer.** Pour effacer les filtres, cliquez ![ sur Effacer les filtres icône Effacer ](../../media/m365-cc-sc-clear-filters-icon.png) **les filtres.**

5. Utilisez **la zone** de recherche et une valeur correspondante pour rechercher des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :
   - ID de message
   - Adresse de messagerie de l’expéditeur
   - Adresse de messagerie du destinataire
   - Objet. Utilisez l’objet entier du message. La recherche n’est pas sensible à la casse.
   - Nom de la stratégie. Utilisez le nom complet de la stratégie. La recherche n’est pas sensible à la casse.

   Une fois que vous avez entré les critères de recherche, appuyez sur Entrée pour filtrer les résultats.

Une fois le message spécifique mis en quarantaine trouvé, sélectionnez-le pour afficher des détails à son sujet et pour prendre des mesures (par exemple, afficher, déplacer, télécharger ou supprimer le message).

#### <a name="view-quarantined-message-details"></a>Afficher les détails des messages mis en quarantaine

Lorsque vous sélectionnez le message mis en quarantaine dans la liste, les informations suivantes sont disponibles dans le volant de détails qui s’affiche.

![Le volant de détails d’un message mis en quarantaine](../../media/quarantine-message-details-flyout.png)

- **ID du message** : l’identificateur global unique pour le message. Disponible dans le **champ d’en-tête Message-ID** dans l’en-tête du message.
- **Adresse de l’expéditeur**
- **Reçu** : Date et heure de réception du message.
- **Subject**
- **Raison de la** mise en quarantaine : indique si un message a été identifié comme courrier **indésirable,** en **bloc,** **hameçonnage,** correspond à une règle de flux de messagerie ( règle de **transport**), ou a été identifié comme contenant un programme **malveillant**.
- **Type de stratégie**
- **Nom de la stratégie**
- **Nombre de destinataires**
- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.
- **Balise destinataire**: pour plus d’informations, voir [Balises utilisateur dans Microsoft Defender pour Office 365](user-tags.md).
- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.
- **Déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.
- **Pas encore déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

Pour prendre des mesures sur le message, consultez la section suivante.

> [!NOTE]
> Pour rester dans le volant des détails, mais modifier le message mis en quarantaine que vous regardez, utilisez les flèches haut et bas en haut du volant.
>
> ![Flèches haut et bas dans le volant des détails d’un message mis en quarantaine](../../media/quarantine-message-details-flyout-up-down-arrows.png)

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

Une fois que vous avez sélectionné un message mis en quarantaine dans la liste, les actions suivantes sont disponibles dans le volant de détails :

![Actions disponibles dans le volant des détails d’un message mis en quarantaine](../../media/quarantine-message-details-flyout-actions.png)

- ![Release email icon ](../../media/m365-cc-sc-check-mark-icon.png) **Release email** <sup>\*</sup> : In the flyout pane that appears, configure the following options:
  - **Ajouter un expéditeur à la** liste d’adresses de votre organisation : sélectionnez cette option pour empêcher la mise en quarantaine des messages de l’expéditeur.
  - Choisissez l’une des options suivantes :
    - **Publication pour tous les destinataires**
    - **Libérer des destinataires spécifiques**: sélectionnez les destinataires dans la zone **Destinataires** qui s’affiche
  - **Envoyez une copie de ce message à d’autres destinataires**: sélectionnez cette option pour entrer les adresses de messagerie des destinataires dans la zone **Destinataires** qui s’affiche.

    > [!NOTE]
    > Pour envoyer une copie du message à d’autres destinataires, vous devez également libérer le message au moins l’un des destinataires d’origine (sélectionnez Release **to all recipients** or **Release to specific recipients**).

  - Envoyer le message à Microsoft pour améliorer la détection **(faux positif)**: cette option est sélectionnée par défaut et signale le message mis en quarantaine par erreur à Microsoft comme faux positif. Si le message a été mis en quarantaine en tant que courrier indésirable, en bloc, hameçonnage ou contenant un programme malveillant, le message est également signalé à l’équipe d’analyse du courrier indésirable de Microsoft. Selon les résultats de leur analyse, les règles de filtrage du courrier indésirable à l’échelle du service peuvent être ajustées pour autoriser le message.

  - **Autoriser les messages de** ce genre : cette option est désactivée par défaut ![ (bascule). ](../../media/scc-toggle-off.png) L’activer (activer) pour empêcher temporairement la mise en quarantaine des messages avec des URL, des pièces jointes et d’autres ![ ](../../media/scc-toggle-on.png) propriétés similaires. Lorsque vous activer cette option, les options suivantes sont disponibles :
    - **Supprimer après**: sélectionnez la durée pendant combien de temps vous souhaitez autoriser des messages comme celui-ci. Sélectionnez **1 jour** à **30 jours.** La valeur par défaut est 30.
    - **Remarque facultative**: entrez une description utile pour l’autoriser.

  Lorsque vous avez terminé, cliquez sur **Libérer le message.**

  Remarques sur la libération des messages :

  - Vous ne pouvez pas envoyer un message au même destinataire plusieurs fois.
  - Seuls les destinataires qui n’ont pas reçu le message apparaissent dans la liste des destinataires potentiels.

- ![Afficher les en-têtes de message icône Afficher les ](../../media/m365-cc-sc-eye-icon.png) **en-têtes** de message : choisissez ce lien pour afficher le texte de l’en-tête du message. Le **volant d’en-tête** message s’affiche avec les liens suivants :
- **Copier l’en-tête** du message : cliquez sur ce lien pour copier l’en-tête du message (tous les champs d’en-tête) dans le Presse-papiers.
- **Analyseur d’en-tête** de message Microsoft : pour analyser en profondeur les valeurs et les champs d’en-tête, cliquez sur ce lien pour aller à l’analyseur d’en-tête de message. Collez l’en-tête du message dans la section Insérer l’en-tête du **message** que vous souhaitez analyser (Ctrl+V ou cliquez avec le bouton droit et choisissez **Coller),** puis cliquez sur Analyser les en-têtes **.**

Les actions suivantes sont disponibles après que vous avez cliqué sur ![ l’icône Actions plus ](../../media/m365-cc-sc-more-actions-icon.png) **actions Plus d’actions**:

- ![Aperçu du message d’aperçu de l’icône de message : dans le volant qui s’affiche, ](../../media/m365-cc-sc-eye-icon.png) choisissez l’un des onglets suivants :
  - **Source**: affiche la version HTML du corps du message avec tous les liens désactivés.
  - **Texte simple**: affiche le corps du message en texte simple.

- ![Supprimer de l’icône Mettre en quarantaine Supprimer de la quarantaine : une fois que vous avez cliqué sur Oui dans l’avertissement qui s’affiche, le message est immédiatement supprimé sans être envoyé aux ](../../media/m365-cc-sc-delete-icon.png) destinataires d’origine. 

- ![Télécharger l’icône Télécharger le courrier électronique : dans le volant qui s’affiche, sélectionnez Je comprends les risques liés au téléchargement de ce message, puis cliquez sur Télécharger pour enregistrer une copie locale du message au ](../../media/m365-cc-sc-download-icon.png) format .eml.  

- ![Bloquer l’expéditeur de l’icône Expéditeur bloqué : ajoutez l’expéditeur à la liste des expéditeurs bloqués ](../../media/m365-cc-sc-block-sender-icon.png) dans votre **boîte aux** lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Envoyer uniquement ](../../media/m365-cc-sc-create-icon.png) **l’icône Envoyer**: signale le message à Microsoft pour analyse. Dans le volant qui s’affiche, choisissez les options suivantes :
  - **Sélectionnez le type de soumission**: **e-mail** (par défaut), **URL** ou **fichier**.
  - **Ajoutez l’ID de message réseau ou téléchargez le fichier de courrier** électronique : sélectionnez l’une des options suivantes :
    - **Ajouter l’ID du message** réseau de messagerie (par défaut, avec la valeur correspondante dans la zone)
    - Télécharger le fichier de messagerie **(.msg** ou  eml) : cliquez sur Parcourir les fichiers pour rechercher et sélectionner le fichier de message .msg ou .eml à envoyer.
  - **Choisissez un destinataire qui a eu un problème**: sélectionnez un (de préférence) ou plusieurs destinataires d’origine du message pour analyser les stratégies qui leur ont été appliquées.
  - **Sélectionnez une raison pour l’envoi à Microsoft**: choisissez l’une des options suivantes :
    - **Ne doit pas avoir été bloqué (faux positif)** (valeur par défaut) : les options suivantes sont disponibles :
      - **Autoriser les messages de** ce genre : cette option est désactivée par défaut ![ (bascule). ](../../media/scc-toggle-off.png) L’activer (activer) pour empêcher temporairement la mise en quarantaine des messages avec des URL, des pièces jointes et d’autres ![ ](../../media/scc-toggle-on.png) propriétés similaires. Lorsque vous activer cette option, les options suivantes sont disponibles :
        - **Supprimer après**: sélectionnez la durée pendant combien de temps vous souhaitez autoriser des messages comme celui-ci. Sélectionnez **1 jour** à **30 jours.** La valeur par défaut est 30.
        - **Remarque facultative**: entrez une description utile pour l’autoriser.
    - **Doit avoir été bloqué (faux négatif).**

  Lorsque vous avez terminé, cliquez sur **Envoyer**.

<sup>\*</sup> Cette option n’est pas disponible pour les messages qui ont déjà été publiés (la valeur **d’état Released** est **Released**).

Si vous ne relâchez pas ou ne supprimez pas le message, il sera supprimé à l’expiration de la période de rétention de mise en quarantaine par défaut (comme indiqué dans la **colonne Expires).**

> [!NOTE]
> Sur un appareil mobile, le texte de description n’est pas disponible sur les icônes d’action.
>
> ![Détails d’un message mis en quarantaine avec les actions disponibles mises en évidence](../../media/quarantine-message-details-flyout-mobile-actions.png)
>
> Les icônes dans l’ordre et leurs descriptions correspondantes sont résumées dans le tableau suivant :
>
> |Icône|Description|
> |---:|---|
> |![Icône Libérer l’e-mail](../../media/m365-cc-sc-check-mark-icon.png)|**Libérer le courrier électronique**|
> |![Afficher l’icône des en-têtes de message](../../media/m365-cc-sc-eye-icon.png)|**Afficher les en-têtes de message**|
> |![Afficher un aperçu de l’icône du message](../../media/m365-cc-sc-eye-icon.png)|**Aperçu du message**|
> |![Supprimer de l’icône de mise en quarantaine](../../media/m365-cc-sc-delete-icon.png)|**Supprimer de la quarantaine**|
> |![Icône Télécharger le courrier électronique](../../media/m365-cc-sc-download-icon.png)|**Télécharger le courrier électronique**|
> |![Icône Bloquer l’expéditeur](../../media/m365-cc-sc-block-sender-icon.png)|**Bloquer l’expéditeur**|
> |![Icône Envoyer uniquement](../../media/m365-cc-sc-create-icon.png)|**Envoyer uniquement**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu’à 100) en cliquant dans la zone vierge à gauche de la première colonne, la liste de listes de listes des **actions** en bloc s’affiche où vous pouvez prendre les mesures suivantes :

![Liste de listes de listes des actions en bloc pour les messages en quarantaine](../../media/quarantine-message-bulk-actions.png)

- ![Release email icon ](../../media/m365-cc-sc-check-mark-icon.png) **Release messages**: Releases messages to all recipients. Dans le volant qui s’affiche, vous pouvez choisir les options suivantes, qui sont les mêmes que lorsque vous publiez un seul message :
  - **Ajouter un expéditeur à la liste d’adresses de votre organisation**
  - **Envoyer une copie de ce message à d’autres destinataires**
  - **Envoyer le message à Microsoft pour améliorer la détection (faux positif)**
  - **Autorisez les messages comme ceci**:
    - **Supprimer après**: **1 jour** **à 30 jours**
    - **Note facultative**

  Lorsque vous avez terminé, cliquez sur **Libérer le message.**

  > [!NOTE]
  > Envisagez le scénario suivant : john@gmail.com envoie un message à faith@contoso.com et john@subsidiary.contoso.com. Gmail bifurcate ce message en deux copies qui sont toutes deux acheminées vers la quarantaine en tant que hameçonnage dans Microsoft. Un administrateur publie ces deux messages admin@contoso.com. Le premier message publié qui atteint la boîte aux lettres d’administration est remis. Le deuxième message publié est identifié comme remise en double et est ignoré. Les messages sont identifiés comme doublons s’ils ont le même ID de message et le même temps de réception.

- ![Supprimer de l’icône de mise en quarantaine Supprimer les messages : une fois que vous avez cliqué sur Oui dans l’avertissement qui s’affiche, les messages sont immédiatement supprimés de la quarantaine sans être envoyés aux ](../../media/m365-cc-sc-delete-icon.png) destinataires d’origine. 
- ![Télécharger les messages électroniques de ](../../media/m365-cc-sc-download-icon.png) **l’icône Télécharger**
- ![Icône Envoyer uniquement ](../../media/m365-cc-sc-create-icon.png) **Envoyer uniquement**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Utilisez le portail Microsoft 365 Defender pour gérer les fichiers mis en quarantaine dans Defender pour Office 365

> [!NOTE]
> Les procédures pour les fichiers mis en quarantaine dans cette section sont disponibles uniquement pour Microsoft Defender pour les abonnés Office 365 Plan 1 ou Plan 2.

Dans les organisations avec Defender pour Office 365, les administrateurs peuvent gérer les fichiers mis en quarantaine par les pièces jointes Coffre dans SharePoint Online, OneDrive Entreprise et Microsoft Teams. Pour activer la protection de ces fichiers, voir Activer Coffre pièces jointes pour [SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

### <a name="view-quarantined-files"></a>Afficher les fichiers mis en quarantaine

1. Dans le Portail Microsoft 365 Defender, accédez à **Messagerie et collaboration** \> **Évaluation** \> **Quarantaine**.
2. Dans la page **Quarantaine,** sélectionnez **l’onglet Fichiers** **(l’e-mail** est l’onglet par défaut).

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez **sur Personnaliser les colonnes** pour modifier les colonnes affichées. Les colonnes par défaut sont marquées d’un astérisque ( <sup>\*</sup> :
   - **Utilisateur**<sup>\*</sup>
   - **Emplacement**<sup>\*</sup>
   - **Attachment filename**<sup>\*</sup>
   - **URL du fichier**<sup>\*</sup>
   - **Taille du fichier**
   - **État de publication**<sup>\*</sup>
   - **Expire**<sup>\*</sup>
   - **Détecté par**
   - **Modifié par heure**

   Lorsque vous avez terminé, cliquez sur **Appliquer** ou **Annuler.**

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres suivants sont disponibles dans le volant **Filtres** qui s’affiche :
   - **Heure reçue**: **heure de début** et heure de **fin** (date).
   - **Expire :** heure **de début** et heure **de fin** (date).
   - **Raison de la mise** en quarantaine : la seule valeur disponible est **Programme malveillant.**
   - **Type de stratégie**

   Lorsque vous avez terminé, cliquez sur **Appliquer** ou **Annuler.**

Une fois que vous avez trouvé un fichier spécifique mis en quarantaine, sélectionnez-le pour afficher les détails à son sujet et pour agir dessus (par exemple, afficher, libérer, télécharger ou supprimer le fichier).

#### <a name="view-quarantined-file-details"></a>Afficher les détails du fichier mis en quarantaine

Lorsque vous sélectionnez un fichier en quarantaine dans la liste, les informations suivantes sont disponibles dans le volant de détails qui s’ouvre :

![Le volant de détails d’un fichier mis en quarantaine](../../media/quarantine-file-details-flyout.png)

- **Nom de fichier**
- **URL du** fichier : URL qui définit l’emplacement du fichier (par exemple, dans SharePoint Online).
- **Contenu malveillant détecté sur** Date/heure de mise en quarantaine du fichier.
- **Expire :** date à laquelle le fichier sera supprimé de la quarantaine.
- **Détecté par**
- **Déplacer ?**
- **Nom du programme malveillant**
- **ID de document**: identificateur unique du document.
- **Taille du** fichier : en kilo-octets (Ko).
- **Organisation** ID unique de votre organisation.
- **Dernière modification**
- **Modifié par**: l’utilisateur qui a modifié le fichier en dernier.
- **Valeur SHA-256 bits (Secure Hash Algorithm)**: vous pouvez utiliser cette valeur de hachage pour identifier le fichier dans d’autres magasins de réputation ou à d’autres emplacements de votre environnement.

Pour prendre des mesures sur le fichier, consultez la section suivante.

> [!NOTE]
> Pour rester dans le volant des détails, mais modifier le fichier mis en quarantaine que vous regardez, utilisez les flèches haut et bas en haut du volant.
>
> ![Flèches vers le haut et vers le bas dans le volant des détails d’un fichier mis en quarantaine](../../media/quarantine-file-details-flyout-up-down-arrows.png)

### <a name="take-action-on-quarantined-files"></a>Prendre des mesures sur les fichiers mis en quarantaine

Une fois que vous avez sélectionné un fichier mis en quarantaine dans la liste, les actions suivantes sont disponibles dans le volant de détails :

![Actions disponibles dans le volant de détails d’un fichier mis en quarantaine](../../media/quarantine-file-details-flyout-actions.png)

- ![Release file icon ](../../media/m365-cc-sc-check-mark-icon.png) **Release file** <sup>\*</sup> : In the flyout pane that appears, turn on or turn off **Report files to Microsoft for analysis,** and then click **Release**.
- ![Télécharger le fichier de téléchargement de l’icône de fichier : dans le volant qui s’affiche, sélectionnez Je comprends les risques liés au téléchargement de ce fichier, puis cliquez sur Télécharger pour enregistrer une copie ](../../media/m365-cc-sc-download-icon.png) locale du fichier.  
- ![Supprimer de l’icône Mettre en quarantaine Supprimer de la quarantaine : une fois que vous avez cliqué sur Oui dans l’avertissement qui s’affiche, le fichier ](../../media/m365-cc-sc-delete-icon.png) est immédiatement  supprimé.
- ![Bloquer l’expéditeur de l’icône Expéditeur bloqué : ajoutez l’expéditeur à la liste des expéditeurs bloqués ](../../media/m365-cc-sc-block-sender-icon.png) dans votre **boîte aux** lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Cette option n’est pas disponible pour les fichiers qui ont déjà été publiés (la valeur d’état **Released** est **Released**).

Si vous ne relâchez pas ou ne supprimez pas le fichier, il sera supprimé après l’expiration de la période de rétention de mise en quarantaine par défaut (comme indiqué dans la **colonne Expires).**

#### <a name="take-action-on-multiple-quarantined-files"></a>Prendre des mesures sur plusieurs fichiers mis en quarantaine

Lorsque vous sélectionnez plusieurs fichiers mis en quarantaine dans la liste (jusqu’à 100) en cliquant dans la zone vierge à gauche de la colonne Objet, la liste de listes de listes des **actions** en bloc s’affiche où vous pouvez prendre les mesures suivantes : 

![Liste de listes de listes des actions en bloc pour les fichiers en quarantaine](../../media/quarantine-file-bulk-actions.png)

- ![Release file icon ](../../media/m365-cc-sc-check-mark-icon.png) **Release file**: In the flyout pane that appears, turn on or turn off **Report files to Microsoft for analysis,** and then click **Release**.
- ![Supprimer de l’icône Mettre en quarantaine Supprimer de la quarantaine : une fois que vous avez cliqué sur Oui dans l’avertissement qui s’affiche, le fichier ](../../media/m365-cc-sc-delete-icon.png) est immédiatement  supprimé.
- ![Télécharger le fichier de téléchargement de l’icône de fichier : dans le volant qui s’affiche, sélectionnez Je comprends les risques liés au téléchargement de ce fichier, puis cliquez sur Télécharger pour enregistrer une copie ](../../media/m365-cc-sc-download-icon.png) locale du fichier.  

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour afficher et gérer les messages et fichiers mis en quarantaine

Les cmdlets que vous utilisez pour afficher et gérer les messages et les fichiers en quarantaine sont décrites dans la liste suivante :

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): notez que cette cmdlet est uniquement pour les messages, et non pour les fichiers mis en quarantaine à partir de Coffre Attachments for SharePoint, OneDrive et Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Pour plus d'informations

[FAQ sur les messages mis en quarantaine](quarantine-faq.yml)
