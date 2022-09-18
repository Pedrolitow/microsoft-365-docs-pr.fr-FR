---
title: Gérer les fichiers et les messages mis en quarantaine en tant qu’administrateur
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MOE150
- MED150
- MET150
ms.assetid: 065cc2cf-2f3a-47fd-a434-2a20b8f51d0c
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent apprendre à afficher et à gérer les messages mis en quarantaine pour tous les utilisateurs dans Exchange Online Protection (EOP). Les administrateurs des organisations avec Microsoft Defender pour Office 365 peuvent également gérer les fichiers mis en quarantaine dans SharePoint Online, OneDrive Entreprise et Microsoft Teams.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: fd1d9d60140ebce0f718a2f23e192ada37b2f3bd
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67797975"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, consultez [messages électroniques mis en quarantaine dans EOP](quarantine-email-messages.md).

Les administrateurs peuvent afficher, libérer et supprimer tous les types de messages mis en quarantaine pour tous les utilisateurs. Les administrateurs peuvent également signaler des faux positifs à Microsoft.

Par défaut, seuls les administrateurs peuvent gérer les messages qui ont été mis en quarantaine sous forme de programmes malveillants, d’hameçonnage à haut niveau de confiance ou à la suite de règles de flux de messagerie (également appelées règles de transport). Toutefois, les administrateurs peuvent utiliser des _stratégies de quarantaine_ pour définir ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine (pour les fonctionnalités prises en charge). Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

Les administrateurs des organisations avec Microsoft Defender pour Office 365 peuvent également gérer les fichiers qui ont été mis en quarantaine par [des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](mdo-for-spo-odb-and-teams.md).

Vous affichez et gérez les messages mis en quarantaine dans le portail Microsoft 365 Defender ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans Exchange Online boîtes aux lettres).

Regardez cette courte vidéo pour découvrir comment gérer les messages mis en quarantaine en tant qu’administrateur. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWGGPF]

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>. Pour accéder directement à la page de **mise en quarantaine**, utilisez <https://security.microsoft.com/quarantine>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour prendre des mesures sur les messages mis en quarantaine pour tous les utilisateurs, vous devez être membre des groupes de **rôles Gestion de l’organisation**, **Administrateur de la sécurité ou Administrateur**<sup>\*</sup> de **la quarantaine**. Pour envoyer des messages à Microsoft, vous devez être membre du groupe de **rôles Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux messages mis en quarantaine pour tous les utilisateurs, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.
  - <sup>\*</sup>Les membres du groupe de **rôles Administrateur** de la quarantaine dans Email & rôles de **collaboration** dans le [portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md#email--collaboration-roles-in-the-microsoft-365-defender-portal) doivent également être membres du groupe de rôles Gestion de **l’hygiène** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) pour effectuer des procédures de quarantaine dans Exchange Online PowerShell .

- Les messages mis en quarantaine sont conservés pendant une période de temps par défaut en fonction de la raison pour laquelle ils ont été mis en quarantaine. Une fois la période de rétention expirée, les messages sont automatiquement supprimés et ne sont pas récupérables. Pour plus d’informations, consultez [messages électroniques mis en quarantaine dans EOP et Defender pour Office 365](quarantine-email-messages.md).

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-email-messages"></a>Utiliser le portail Microsoft 365 Defender pour gérer les messages électroniques mis en quarantaine

### <a name="view-quarantined-email"></a>Afficher les e-mails mis en quarantaine

1. Dans le portail Microsoft 365 Defender à <https://security.microsoft.com>, accédez à **E-mail et collaboration**\>**Examiner**\>**Mise en quarantaine**. Pour accéder directement à la page de **mise en quarantaine**, utilisez <https://security.microsoft.com/quarantine>.

2. Dans la page **Quarantaine**, vérifiez que l’onglet **Email** est sélectionné.

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour modifier les colonnes qui s'affichent. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

   - **Heure de réception**<sup>\*</sup>
   - **Sujet**<sup>\*</sup>
   - **Expéditeur**<sup>\*</sup>
   - **Raison de la quarantaine**<sup>\*</sup>
   - **Libérer le statut**<sup>\*</sup>
   - **Type de stratégie**<sup>\*</sup>
   - **Expire**<sup>\*</sup>
   - **Destinataire**
   - **ID de message**
   - **Nom de la stratégie**
   - **Taille du message**
   - **Direction du courrier**
   - **Balise de destinataire**

   Lorsque vous avez terminé, cliquez sur **Appliquer**.

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres suivants sont disponibles dans le menu déroulant **Filtres** qui apparaît :
   - **ID du message** : l’identificateur global unique du message.

     Par exemple, vous avez utilisé la [trace des messages](message-trace-scc.md) pour rechercher un message qui a été envoyé à un utilisateur de votre organisation, et vous déterminez que le message a été mis en quarantaine au lieu d’être remis. Veillez à inclure la valeur d’ID de message complète, qui peut inclure des crochets (\<\>). Par exemple : `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Adresse de l’expéditeur**
   - **Adresse du destinataire**
   - **Sujet**
   - **Heure reçue** : Saisissez une **heure de début** et une **heure de fin** (date).
   - **Date d’expiration** : filtrer les messages par date d'expiration de la quarantaine :
     - **Aujourd’hui**
     - **Dans les 2 prochains jours**
     - **Dans les 7 prochains jours**
     - **Heure reçue** : Saisissez une **heure de début** et une **heure de fin** (date).
   - **Balise de destinataire**
   - **Raison de la mise en quarantaine :**
     -  **Règle de transport** (règle de flux de courrier)
     - **E-mail de masse**
     - **Courrier indésirable**
     - **Programmes malveillants** : stratégies anti-programme malveillant dans les stratégies EOP ou Pièces jointes sécurisées dans Defender pour Office 365. La valeur **type de** stratégie indique quelle fonctionnalité a été utilisée.
     - **Hameçonnage** : Le verdict du filtre anti-spam était **hameçonnant** ou la protection anti-phishing a mis le message en quarantaine ([paramètres d'usurpation](set-up-anti-phishing-policies.md#spoof-settings) ou [protection contre l'usurpation d'identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Hameçonnage à haute fiabilité**
   - **Destinataire** : **Tous les utilisateurs** ou **uniquement moi**. Les utilisateurs finaux peuvent uniquement gérer les messages mis en quarantaine qui leur sont envoyés.
   - **Statut de la version** : Une des valeurs suivantes :
     - **Révision requise.**
     - **Approuvé**
     - **Refusé**
     - **Publication demandée**
     - **Date de publication**
   - **Type de stratégie** : filtrer les messages par type de stratégie :
     - **Stratégie anti-programme malveillant**
     - **Stratégie de pièces jointes fiables**
     - **Politique de lutte contre l'hameçonnage**
     - **Stratégie anti-courrier indésirable**
     -  **Règle de transport** (règle de flux de courrier)

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres, cliquez sur ![l'icône Effacer les filtres.](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

5. Utilisez la zone **de recherche** et une valeur correspondante pour rechercher des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :
   - Adresse de messagerie de l’expéditeur
   - Objet. Utiliser l'intégralité du sujet du message La recherche n’est pas sensible à la casse.

   Après avoir saisi les critères de recherche, appuyez sur ENTRÉE pour filtrer les résultats.

   > [!NOTE]
   > La zone **de recherche** de la page **de mise en quarantaine** principale recherche uniquement les éléments en quarantaine dans l’affichage actuel, et non la mise en quarantaine entière. Pour rechercher tous les éléments mis en quarantaine, utilisez l'option **Filtre** et le menu déroulant **Filtres** qui en résulte. 

Une fois le message spécifique mis en quarantaine trouvé, sélectionnez-le pour afficher des détails à son sujet et pour prendre des mesures (par exemple, afficher, déplacer, télécharger ou supprimer le message).

#### <a name="view-quarantined-message-details"></a>Afficher les détails des messages mis en quarantaine

Lorsque vous sélectionnez un message mis en quarantaine dans la liste, les informations suivantes sont disponibles dans le flyout de détails qui apparaît.

:::image type="content" source="../../media/quarantine-message-details-flyout.png" alt-text="Les détails du menu volant d'un message en quarantaine" lightbox="../../media/quarantine-message-details-flyout.png":::

- **ID du message** : l’identificateur global unique pour le message. Disponible dans le champ **d’en-tête Message-ID de l’en-tête** de message.
- **Adresse de l’expéditeur**
- **Reçu** : Date et heure de réception du message.
- **Subject**
- **Raison de la mise en quarantaine** : indique si un message a été identifié comme **courrier indésirable**, **en bloc**, **hameçonnage**, correspond à une règle de flux de courrier (**règle de transport**) ou s’il a été identifié comme contenant des **programmes malveillants**.
- **Type de stratégie**
- **Nom de la stratégie**
- **Nombre de destinataires**
- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.
- **Balise de destinataire** : pour plus d’informations, consultez [les balises utilisateur dans Microsoft Defender pour Office 365](user-tags.md).
- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.
- **Déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.
- **Pas encore déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

Pour donner suite au message, consultez la section suivante.

> [!NOTE]
> Pour rester dans le menu déroulant des détails, mais changer le message en quarantaine que vous regardez, utilisez les flèches haut et bas en haut du menu déroulant.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Les flèches vers le haut et les flèches vers le bas des détails du menu flottant d'un message en quarantaine" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

Après avoir sélectionné un message en quarantaine dans la liste, les actions suivantes sont disponibles dans le flyout des détails :

:::image type="content" source="../../media/quarantine-message-details-flyout-actions.png" alt-text="Actions disponibles dans le menu volant détaillé d’un message mis en quarantaine" lightbox="../../media/quarantine-message-details-flyout-actions.png":::

- ![Icône de version d’e-mail](../../media/m365-cc-sc-check-mark-icon.png) **E-mail**<sup>\*</sup> de publication : dans le volet de menu volant qui s’affiche, configurez les options suivantes :
  - **Ajouter l’expéditeur à la liste verte de votre organisation** : sélectionnez cette option pour empêcher la mise en quarantaine des messages de l’expéditeur.
  - Sélectionnez l’une des options suivantes :
    - **Mise en production pour tous les destinataires**
    - **Libérer vers des destinataires spécifiques** : sélectionnez les destinataires dans la zone **Destinataires** qui s’affiche
  - **Envoyer une copie de ce message à d’autres destinataires** : sélectionnez cette option et entrez les adresses e-mail du destinataire dans la zone **Destinataires** qui s’affiche.

    > [!NOTE]
    > Pour envoyer une copie du message à d’autres destinataires, vous devez également publier le message au moins l’un des destinataires d’origine (sélectionnez **Libérer pour tous les destinataires** ou **Libérer vers des destinataires spécifiques**).

  - **Envoyez le message à Microsoft pour améliorer la détection (faux positif)** : cette option est sélectionnée par défaut et signale le message mis en quarantaine à Microsoft comme faux positif. Si le message a été mis en quarantaine en tant que courrier indésirable, en bloc, hameçonnage ou contenant des programmes malveillants, le message est également signalé à l’équipe Microsoft Spam Analysis Team. En fonction des résultats de leur analyse, les règles de filtrage du courrier indésirable à l’échelle du service peuvent être ajustées pour permettre le passage du message.

  - **Autoriser des messages comme celui-ci** : cette option est désactivée par défaut (![désactiver la désactivation).](../../media/scc-toggle-off.png) Activez-le (![activez](../../media/scc-toggle-on.png) le bouton bascule) pour empêcher temporairement la mise en quarantaine des messages contenant des URL, des pièces jointes et d’autres propriétés similaires. Lorsque vous activez cette option, les options suivantes sont disponibles :
    - **Supprimer après** : sélectionnez la durée pendant laquelle vous souhaitez autoriser des messages comme celui-ci. Sélectionnez **1 jour** à **30 jours**. La valeur par défaut est 30.
    - **Remarque facultative** : entrez une description utile pour l’autorisation.

  Lorsque vous avez terminé, cliquez sur **Publier le message**.

  Remarques sur la publication de messages :

  - Vous ne pouvez pas libérer un message au même destinataire plusieurs fois.
  - Seuls les destinataires qui n’ont pas reçu le message apparaissent dans la liste des destinataires potentiels.
  - Seuls les membres du groupe de **rôles Administrateurs de la sécurité** peuvent voir et utiliser **l’option Envoyer le message à Microsoft pour améliorer la détection (faux positif)** et **autoriser des messages comme celui-ci** .

- ![Icône Partager l’e-mail.](../../media/m365-cc-sc-share-email-icon.png) **Partager un e-mail** : dans le menu volant qui s’affiche, ajoutez un ou plusieurs destinataires pour recevoir une copie du message. Lorsque vous avez terminé, cliquez sur **Partager**.

Les actions suivantes sont disponibles après avoir cliqué sur ![l’icône Autres actions.](../../media/m365-cc-sc-more-actions-icon.png) **Autres actions** :

- ![Afficher l’icône des en-têtes de messages.](../../media/m365-cc-sc-view-message-headers-icon.png) **Afficher les en-têtes de message** : Sélectionnez ce lien pour voir le texte de l'en-tête du message. Le flyout de **l'en-tête de message** apparaît avec les liens suivants :
  - **Copier l'en-tête du message** : Cliquez sur ce lien pour copier l'en-tête du message (tous les champs d'en-tête) dans votre presse-papiers.
  - **Analyseur d'en-tête de message Microsoft Corporation** : Pour analyser en profondeur les champs et les valeurs de l'en-tête, cliquez sur ce lien pour accéder à l'analyseur d'en-tête de message. Collez l'en-tête du message dans la section **Insérez l'en-tête du message que vous souhaitez analyser** (CTRL+V ou cliquez avec le bouton droit de la souris et choisissez **Coller**), puis cliquez sur **Analyser les en-têtes**.

- ![Icône de prévisualisation de message ](../../media/m365-cc-sc-preview-message-icon.png) **Prévisualisation de message** : Dans le menu flottant qui apparaît, sélectionnez l'un des onglets suivants :
  - **Affichage Source** : affiche la version HTML du corps du message, dans laquelle tous les liens sont désactivés.
  - **Texte simple** : affiche le corps du message au format texte brut.

- ![Supprimer de l’icône de mise en quarantaine.](../../media/m365-cc-sc-delete-icon.png) **Supprimer de la mise en quarantaine** : après avoir cliqué sur **Oui** dans l’avertissement qui s’affiche, le message est immédiatement supprimé sans être envoyé aux destinataires d’origine.

- ![Icône Télécharger l’e-mail.](../../media/m365-cc-sc-download-icon.png) **Télécharger l’e-mail** : dans le menu volant qui s’affiche, configurez les paramètres suivants :
  - **Motif du téléchargement du fichier** : entrez du texte descriptif.
  - **Créer un mot de passe** et **confirmer le mot de passe** : entrez un mot de passe requis pour ouvrir le fichier de message téléchargé.

  Lorsque vous avez terminé, cliquez sur **Télécharger**, puis **Terminé** pour enregistrer une copie locale du message. Le fichier de message .eml est enregistré dans un fichier compressé nommé Mise en quarantaine Messages.zip dans votre dossier **Téléchargements** . Si le fichier .zip existe déjà, un nombre est ajouté au nom de fichier (par exemple, Messages mis en quarantaine(1).zip).

- ![Icône de blocage de l’expéditeur.](../../media/m365-cc-sc-block-sender-icon.png) **Bloquer l'expéditeur** : Ajouter l'expéditeur à la liste des expéditeurs bloqués dans **votre** boîte aux lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

- ![Icône Envoyer uniquement.](../../media/m365-cc-sc-create-icon.png) **Envoyer uniquement** : signale le message à Microsoft à des fins d’analyse. Dans le menu volant qui s’affiche, choisissez les options suivantes :
  - **Sélectionnez le type d’envoi** : **Email** (par défaut), **URL** ou **Fichier**.
  - **Ajoutez l’ID de message réseau ou chargez le fichier e-mail** : sélectionnez l’une des options suivantes :
    - **Ajouter l’ID de message réseau de messagerie** (par défaut, avec la valeur correspondante dans la zone)
    - **Charger le fichier e-mail (.msg ou eml)** : cliquez sur **Parcourir les fichiers** pour rechercher et sélectionner le fichier de message .msg ou .eml à envoyer.
  - **Choisissez un destinataire qui a rencontré un problème** : sélectionnez un ou plusieurs destinataires originaux du message pour analyser les stratégies qui leur ont été appliquées.
  - **Sélectionnez une raison pour l’envoi à Microsoft** : choisissez l’une des options suivantes :
    - **Ne doit pas avoir été bloqué (faux positif)** (valeur par défaut) : les options suivantes sont disponibles :
      - **Autoriser des messages comme celui-ci** : cette option est désactivée par défaut (![désactiver la désactivation).](../../media/scc-toggle-off.png) Activez-le (![activez](../../media/scc-toggle-on.png) le bouton bascule) pour empêcher temporairement la mise en quarantaine des messages contenant des URL, des pièces jointes et d’autres propriétés similaires. Lorsque vous activez cette option, les options suivantes sont disponibles :
        - **Supprimer après** : sélectionnez la durée pendant laquelle vous souhaitez autoriser des messages comme celui-ci. Sélectionnez **1 jour** à **30 jours**. La valeur par défaut est 30.
        - **Remarque facultative** : entrez une description utile pour l’autorisation.
    - **Aurait dû être bloqué (faux négatif).**

  Lorsque vous avez terminé, cliquez sur **Envoyer**.

<sup>\*</sup> Cette option n'est pas disponible pour les messages qui ont déjà été validés (la **valeur du statut** Validé est **publiée**).

Si vous ne libérez pas ou ne supprimez pas le message, il sera supprimé après l'expiration de la période de conservation en quarantaine par défaut (comme indiqué dans la **colonne Expiration**).

> [!NOTE]
> Sur un appareil mobile, le texte de description n'est pas disponible sur les icônes d'action.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-mobile-actions.png" alt-text="Détails d’un message mis en quarantaine avec les actions disponibles mises en surbrillance" lightbox="../../media/quarantine-message-details-flyout-mobile-actions.png":::
>
> Les icônes dans l'ordre et leurs descriptions correspondantes sont résumées dans le tableau suivant :
>
> |Icône|Description|
> |---:|---|
> |![Icône de version d’e-mail](../../media/m365-cc-sc-check-mark-icon.png)|**Version d’e-mail**|
> |![Icône Partager l’e-mail.](../../media/m365-cc-sc-share-email-icon.png)|**Partager un e-mail**|
> |![Afficher l’icône des en-têtes de messages.](../../media/m365-cc-sc-view-message-headers-icon.png)|**Afficher les en-têtes de messages**|
> |![Afficher l’icône de prévisualisation du message.](../../media/m365-cc-sc-preview-message-icon.png)|**Afficher une prévisualisation du message**|
> |![Supprimer de l’icône de mise en quarantaine.](../../media/m365-cc-sc-delete-icon.png)|**Supprimer de la quarantaine**|
> |![Icône Télécharger l’e-mail.](../../media/m365-cc-sc-download-icon.png)|**Télécharger l’e-mail**|
> |![Icône de blocage de l’expéditeur.](../../media/m365-cc-sc-block-sender-icon.png)|**Bloquer l’expéditeur**|
> |![Icône Envoyer uniquement.](../../media/m365-cc-sc-create-icon.png)|**Envoyer uniquement**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu'à 100) en cliquant dans la zone vide à gauche de la première colonne, la liste déroulante **Actions en vrac** s'affiche et vous permet d'effectuer les actions suivantes :

:::image type="content" source="../../media/quarantine-message-bulk-actions.png" alt-text="Liste déroulante actions en bloc pour les messages en quarantaine" lightbox="../../media/quarantine-message-bulk-actions.png":::

- ![Icône de version d’e-mail](../../media/m365-cc-sc-check-mark-icon.png) **Messages de publication** : libère les messages à tous les destinataires. Dans le menu volant qui s’affiche, vous pouvez choisir les options suivantes, qui sont les mêmes que lorsque vous publiez un seul message :
  - **Ajouter un expéditeur à la liste verte de votre organisation**
  - **Envoyer une copie de ce message à d’autres destinataires**
  - **Envoyer le message à Microsoft pour améliorer la détection (faux positif)**
  - **Autorisez les messages comme suit** :
    - **Supprimer après** : **1 jour** à **30 jours**
    - **Remarque facultative**

  Lorsque vous avez terminé, cliquez sur **Publier le message**.

  > [!NOTE]
  > Considérez le scénario suivant : john@gmail.com envoie un message à faith@contoso.com et john@subsidiary.contoso.com. Gmail bifurque ce message en deux copies qui sont toutes les deux routées en quarantaine en tant que hameçonnage dans Microsoft. Un administrateur libère ces deux messages dans admin@contoso.com. Le premier message publié qui atteint la boîte aux lettres d’administration est remis. Le deuxième message publié est identifié comme remise en double et ignoré. Les messages sont identifiés comme des doublons s’ils ont le même ID de message et l’heure de réception.

- ![Supprimer de l’icône de mise en quarantaine.](../../media/m365-cc-sc-delete-icon.png) **Supprimer les messages** : après avoir cliqué sur **Oui** dans l’avertissement qui s’affiche, les messages sont immédiatement supprimés de la quarantaine sans être envoyés aux destinataires d’origine.
- ![Icône Télécharger l’e-mail.](../../media/m365-cc-sc-download-icon.png) **Télécharger des messages**
- ![Icône Envoyer uniquement.](../../media/m365-cc-sc-create-icon.png) **Envoyer uniquement**

## <a name="use-the-microsoft-365-defender-portal-to-manage-quarantined-files-in-defender-for-office-365"></a>Utilisez le portail Microsoft 365 Defender pour gérer les fichiers mis en quarantaine dans Defender pour Office 365

> [!NOTE]
> Les procédures pour les fichiers mis en quarantaine dans cette section sont disponibles uniquement pour les abonnés plan 1 ou Plan 2 Microsoft Defender pour Office 365.

Dans les organisations avec Defender pour Office 365, les administrateurs peuvent gérer les fichiers qui ont été mis en quarantaine par des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams. Pour activer la protection de ces fichiers, consultez [Activer les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md).

> [!NOTE]
> Les fichiers mis en quarantaine dans SharePoint ou OneDrive sont supprimés après 30 jours, mais les fichiers bloqués restent dans SharePoint ou OneDrive dans l’état bloqué.

### <a name="view-quarantined-files"></a>Afficher les fichiers mis en quarantaine

1. Dans le portail Microsoft 365 Defender à <https://security.microsoft.com>, accédez à **E-mail et collaboration**\>**Examiner**\>**Mise en quarantaine**. Pour accéder directement à la page de **mise en quarantaine**, utilisez <https://security.microsoft.com/quarantine>.

2. Dans la page **Quarantaine**, sélectionnez l’onglet **Fichiers** (**Email** est l’onglet par défaut).

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour modifier les colonnes affichées. Les colonnes par défaut sont marquées d’un astérisque (<sup>\*</sup>) :
   - **Utilisateur**<sup>\*</sup>
   - **Emplacement**<sup>\*</sup>
   - **Nom de fichier de pièce jointe**<sup>\*</sup>
   - **URL du fichier**<sup>\*</sup>
   - **Taille du fichier**
   - **Libérer le statut**<sup>\*</sup>
   - **Expire**<sup>\*</sup>
   - **Détecté par**
   - **Modifié par heure**

   Lorsque vous avez terminé, cliquez sur **Appliquer** ou **Annuler**.

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres suivants sont disponibles dans le menu déroulant **Filtres** qui apparaît :
   - **Heure reçue** : **heure de début** et **heure de fin** (date).
   - **Expire** : **heure de début** et **heure de fin** (date).
   - **Raison de la quarantaine** : la seule valeur disponible est **Malware**.
   - **Type de stratégie**

   Lorsque vous avez terminé, cliquez sur **Appliquer** ou **Annuler**.

Une fois que vous avez trouvé un fichier en quarantaine spécifique, sélectionnez le fichier pour afficher les détails à son sujet et pour prendre des mesures à son sujet (par exemple, afficher, libérer, télécharger ou supprimer le fichier).

#### <a name="view-quarantined-file-details"></a>Afficher les détails du fichier mis en quarantaine

Lorsque vous sélectionnez un fichier mis en quarantaine dans la liste, les informations suivantes sont disponibles dans le menu volant des détails qui s’ouvre :

:::image type="content" source="../../media/quarantine-file-details-flyout.png" alt-text="Menu volant des détails d’un fichier mis en quarantaine" lightbox="../../media/quarantine-file-details-flyout.png":::

- **Nom de fichier**
- **URL du fichier** : URL qui définit l’emplacement du fichier (par exemple, dans SharePoint Online).
- **Contenu malveillant détecté le** Date/heure de mise en quarantaine du fichier.
- **Expire** : date à laquelle le fichier sera supprimé de la quarantaine.
- **Détecté par**
- **Libéré?**
- **Nom du programme malveillant**
- **ID de document** : identificateur unique du document.
- **Taille du fichier** : en kilo-octets (Ko).
- **Organisation** ID unique de votre organisation.
- **Dernière modification**
- **Modifié par** : l’utilisateur qui a modifié le fichier pour la dernière fois.
- **Valeur 256 bits (SHA-256) de l’algorithme** de hachage sécurisé : vous pouvez utiliser cette valeur de hachage pour identifier le fichier dans d’autres magasins de réputation ou à d’autres emplacements de votre environnement.

Pour prendre des mesures sur le fichier, consultez la section suivante.

> [!NOTE]
> Pour rester dans le menu volant des détails, mais modifier le fichier mis en quarantaine que vous examinez, utilisez les flèches haut et bas en haut du menu volant.
>
> :::image type="content" source="../../media/quarantine-file-details-flyout-up-down-arrows.png" alt-text="Flèches vers le haut et le bas dans le menu volant des détails des fichiers mis en quarantaine" lightbox="../../media/quarantine-file-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-files"></a>Prendre des mesures sur les fichiers mis en quarantaine

Une fois que vous avez sélectionné un fichier mis en quarantaine dans la liste, les actions suivantes sont disponibles dans le menu volant des détails :

:::image type="content" source="../../media/quarantine-file-details-flyout-actions.png" alt-text="Actions dans le menu volant des détails d’un fichier mis en quarantaine" lightbox="../../media/quarantine-file-details-flyout-actions.png":::

- ![Icône de fichier release.](../../media/m365-cc-sc-check-mark-icon.png) **Fichier de**<sup>\*</sup> publication : dans le volet de menu volant qui s’affiche, activez ou désactivez **les fichiers rapport à Microsoft à des fins d’analyse**, puis cliquez sur **Publier**.
- ![Icône de fichier release.](../../media/m365-cc-sc-check-mark-icon.png)
- ![Icône Télécharger le fichier.](../../media/m365-cc-sc-download-icon.png) **Fichier de téléchargement** : dans le menu volant qui s’affiche, sélectionnez **Je comprends les risques liés au téléchargement de ce fichier**, puis cliquez sur **Télécharger** pour enregistrer une copie locale du fichier.
- ![Supprimer de l’icône de mise en quarantaine.](../../media/m365-cc-sc-delete-icon.png) **Supprimer de la mise en quarantaine** : une fois que vous avez cliqué sur **Oui** dans l’avertissement qui s’affiche, le fichier est immédiatement supprimé.
- ![Icône de blocage de l’expéditeur.](../../media/m365-cc-sc-block-sender-icon.png) **Bloquer l'expéditeur** : Ajouter l'expéditeur à la liste des expéditeurs bloqués dans **votre** boîte aux lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Cette option n’est pas disponible pour les fichiers qui ont déjà été publiés (la valeur **d’état Released** est **Released**).

Si vous ne relâchez pas ou ne supprimez pas le fichier, il sera supprimé une fois la période de rétention de quarantaine par défaut expirée (comme indiqué dans la colonne **Expires** ).

#### <a name="take-action-on-multiple-quarantined-files"></a>Prendre des mesures sur plusieurs fichiers mis en quarantaine

Lorsque vous sélectionnez plusieurs fichiers mis en quarantaine dans la liste (jusqu’à 100) en cliquant dans la zone vide à gauche de la colonne **Objet** , la liste déroulante **Actions en bloc** s’affiche et vous pouvez effectuer les actions suivantes :

:::image type="content" source="../../media/quarantine-file-bulk-actions.png" alt-text="Liste déroulante actions en bloc pour les fichiers en quarantaine" lightbox="../../media/quarantine-file-bulk-actions.png":::

- ![Icône de fichier release.](../../media/m365-cc-sc-check-mark-icon.png) **Fichier de publication** : dans le volet de menu volant qui s’affiche, activez ou désactivez **les fichiers rapport à Microsoft à des fins d’analyse**, puis cliquez sur **Publier**.
- ![Supprimer de l’icône de mise en quarantaine.](../../media/m365-cc-sc-delete-icon.png) **Supprimer de la mise en quarantaine** : une fois que vous avez cliqué sur **Oui** dans l’avertissement qui s’affiche, le fichier est immédiatement supprimé.
- ![Icône Télécharger le fichier.](../../media/m365-cc-sc-download-icon.png) **Fichier de téléchargement** : dans le menu volant qui s’affiche, sélectionnez **Je comprends les risques liés au téléchargement de ce fichier**, puis cliquez sur **Télécharger** pour enregistrer une copie locale du fichier.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour afficher et gérer les messages et fichiers mis en quarantaine

Les applets de commande que vous utilisez pour afficher et gérer des messages et des fichiers en quarantaine sont décrites dans la liste suivante :

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)
- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)
- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)
- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage) : notez que cette applet de commande s’applique uniquement aux messages, et non aux fichiers en quarantaine des pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.
- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)

## <a name="for-more-information"></a>Pour plus d'informations

[FAQ sur les messages mis en quarantaine](quarantine-faq.yml)
