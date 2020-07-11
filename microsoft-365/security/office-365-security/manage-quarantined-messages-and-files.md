---
title: Gérer les fichiers et les messages mis en quarantaine en tant qu’administrateur
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
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
description: Les administrateurs peuvent apprendre à afficher et à gérer les messages mis en quarantaine pour tous les utilisateurs dans Exchange Online Protection (EOP). Les administrateurs dans les organisations avec Office 365 Advanced Threat Protection (Office 365 ATP) peuvent également gérer les fichiers mis en quarantaine dans SharePoint Online, OneDrive entreprise et Microsoft Teams.
ms.openlocfilehash: 5e7c594669cf910404badd85c35671c284d4d91e
ms.sourcegitcommit: a5ed189fa789975f8c3ed39db1d52f2ef7d671aa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/10/2020
ms.locfileid: "45101680"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, consultez la rubrique [messages électroniques mis en quarantaine dans EOP](quarantine-email-messages.md).

Les administrateurs peuvent afficher, publier et supprimer tous les types de messages mis en quarantaine pour tous les utilisateurs. Seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants, le hameçonnage à haute fiabilité ou à la suite de règles de flux de messagerie (également appelées règles de transport). Les administrateurs peuvent également signaler les faux positifs à Microsoft.

Les administrateurs dans les organisations disposant d’Office 365 Advanced Threat Protection (Office 365 ATP) peuvent également afficher, télécharger et supprimer des fichiers mis en quarantaine dans SharePoint Online, OneDrive entreprise et Microsoft Teams.

Vous pouvez afficher et gérer les messages mis en quarantaine dans le centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ; environnement de ligne de commande Exchange autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre de conformité et sécurité, consultez <https://protection.office.com>. Pour ouvrir la page de quarantaine directement, accédez à <https://protection.office.com/quarantine>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Vous devez disposer d’autorisations pour pouvoir gérer la mise en quarantaine en tant qu’administrateur. Les autorisations sont contrôlées par le rôle de **mise en quarantaine** dans le centre de sécurité & conformité. Par défaut, ce rôle est affecté aux groupes de rôles gestion de l' **organisation** (administrateurs globaux), administrateur de **mise en quarantaine**et administrateur de **sécurité** dans le centre de sécurité & conformité. Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

- Les messages mis en quarantaine sont conservés pendant une période de temps par défaut avant d’être supprimés automatiquement :

  - Messages mis en quarantaine par des stratégies de blocage du courrier indésirable (courrier indésirable, hameçonnage et courrier en masse) : 30 jours. Il s’agit de la valeur par défaut et la valeur maximale. Pour configurer cette valeur, reportez-vous à la rubrique [configurer des stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

  - Messages contenant des programmes malveillants : 15 jours.

  Lorsqu’un message arrive à expiration en quarantaine, vous ne pouvez pas le récupérer.

## <a name="use-the-security--compliance-center-to-manage-quarantined-email-messages"></a>Utiliser le centre de sécurité & conformité pour gérer les messages électroniques mis en quarantaine

### <a name="view-quarantined-email"></a>Afficher le courrier en quarantaine

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Examiner** \> **Quarantaine**.

2. Vérifiez que l’option **Afficher les mis en quarantaine** est définie sur la valeur par défaut de **messagerie**.

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Modifier les colonnes** pour afficher jusqu’à sept colonnes. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

   - **Reçu**<sup>\*</sup>

   - **Expéditeur**<sup>\*</sup>

   - **Sujet**<sup>\*</sup>

   - **Raison de la quarantaine**<sup>\*</sup>

   - **Déplacer ?**<sup>\*</sup>

   - **Type de stratégie**<sup>\*</sup>

   - **Destinataire**

   - **ID de message**

   - **Nom de la stratégie**

   - **Taille**

   - **Direction**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** ou sur **Définir par défaut**.

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres disponibles sont :

   - **Date d’expiration** : filtrer les messages par date d'expiration de la quarantaine :

     - **Aujourd’hui**

     - **Dans les 2 prochains jours**

     - **Dans les 7 prochains jours**

     - **Personnaliser**: Entrer une **Date de début** et une **Date de fin**.

   - **Heure de réception**: Entrer une **Date de début** et une **Date de fin**.

   - **Raison de la mise en quarantaine :**

     - **Stratégie**: le message correspond aux conditions d’une règle de flux de messagerie (également appelée règle de transport).

     - **E-mail de masse**

     - **Hameçonnage**

     - **Programme malveillant**

     - **Courrier indésirable**

     - **Hameçonnage à niveau de confiance élevé**

   - **Destinataire du message**: tous les utilisateurs ou seulement les messages qui vous sont envoyés. Les utilisateurs finaux peuvent gérer uniquement les messages mis en quarantaine qui leur sont envoyés.

   Pour effacer le filtre, cliquez sur **Effacer**. Pour masquer le menu déroulant de filtrage, cliquez de nouveau sur **Filtrer**.

5. Utilisez **Trier les résultats par** (le bouton **ID de message** par défaut) et une valeur correspondante pour rechercher des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :

   - **ID du message** : l’identificateur global unique du message.

     Par exemple, vous avez utilisé le [suivi des messages](message-trace-scc.md) pour rechercher un message qui a été envoyé à un utilisateur de votre organisation, et vous déterminez que le message a été mis en quarantaine au lieu d’être remis. Veillez à inclure la valeur d’ID de message complète, qui peut inclure des chevrons ( \<\> ). Par exemple : `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Adresse e-mail de l'expéditeur** : adresse e-mail d'un seul expéditeur.

   - **Adresse e-mail du destinataire** : adresse e-mail d'un seul destinataire.

   - **Sujet** : utiliser l'intégralité du sujet du message. La recherche n’est pas sensible à la casse.

   Après avoir entrer les critères de recherche, cliquez sur le ![Bouton actualiser](../../media/scc-quarantine-refresh.png) **Actualiser** pour filtrer les résultats.

Une fois le message spécifique mis en quarantaine trouvé, sélectionnez-le pour afficher des détails à son sujet et pour prendre des mesures (par exemple, afficher, déplacer, télécharger ou supprimer le message).

#### <a name="export-message-results"></a>Exporter les résultats de message

1. Sélectionnez les messages qui vous intéressent, puis cliquez sur **Exporter les résultats**.

2. Cliquez sur **Oui** dans le message de confirmation qui vous avertit que la fenêtre du navigateur reste ouverte.

3. Lorsque l’exportation est prête, vous pouvez nommer et choisir l’emplacement de téléchargement du fichier .csv.

#### <a name="view-quarantined-message-details"></a>Afficher les détails des messages mis en quarantaine

Lorsque vous sélectionnez un message électronique dans la liste, les détails de message suivants s’affichent dans le volet déroulant **Détails** :

- **ID du message** : l’identificateur global unique pour le message.

- **Adresse de l’expéditeur**

- **Reçu** : Date et heure de réception du message.

- **Subject**

- **Raison**de la mise en quarantaine : indique si un message a été identifié **Bulk**comme **courrier indésirable**, **hameçon, hameçon**, correspond à une règle de flux de messagerie (**règle de transport**) ou a été identifié comme contenant un **programme malveillant**.

- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.

- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.

- **Déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.

- **Pas encore déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

Une fois que vous avez sélectionné un message, vous disposez de plusieurs options pour effectuer les messages dans le volet de la fenêtre de **Détails** :

- **Message de publication**: dans le volet flyout qui apparaît, choisissez les options suivantes :

  - **Signaler les messages à Microsoft pour analyse**: cette option est sélectionnée par défaut et signale le message en quarantaine à Microsoft comme un faux positif. Si le message a été mis en quarantaine en tant que courrier indésirable, en masse, hameçonnage ou contenant un programme malveillant, le message est également signalé à l’équipe d’analyse du courrier indésirable de Microsoft. En fonction de leur analyse, les règles de filtrage du courrier indésirable à l’échelle du service peuvent être ajustées pour autoriser le message.

  - Choisissez l’une des options suivantes :

    - **Diffuser les messages à tous les destinataires**

    - **Publier des messages à des destinataires spécifiques**

    - **Publier des messages vers d’autres personnes**

  Lorsque vous avez terminé, cliquez sur **Déplacer les messages**.

  Remarques sur la libération des messages :

  - Vous ne pouvez pas diffuser un message au même destinataire plus d’une fois.

  - Seuls les destinataires qui n’ont pas reçu le message s’affichent dans la liste des destinataires potentiels.

- **Afficher l’en-tête du message** : Sélectionnez ce lien pour afficher le texte d’en-tête du message. Pour analyser en profondeur les champs d'en-tête et les valeurs, copiez le texte d’en-tête du message dans le presse-papiers, puis sélectionnez **Analyseur d’en-tête de message Microsoft** pour accéder à l’analyseur de connectivité à distance (Faites un clic droit et sélectionnez **Ouvrir dans un nouvel onglet** si vous ne souhaitez pas laisser Microsoft 365 accomplir cette tâche). Collez l’en-tête du message dans la section analyseur d’en-tête de message de la page, puis sélectionnez **Analyser les en-têtes** :

- **Prévisualiser le message** : dans le volet déroulant qui apparaît, choisissez l’une des options suivantes :

  - **Mode Source** : affiche la version HTML du corps du message, dans laquelle tous les liens sont désactivés.
  
  - **Mode texte** : affiche le corps du message au format texte brut.

- **Supprimer de la quarantaine**: après avoir cliqué sur **Oui** dans le message d’avertissement qui s’affiche, le message est immédiatement supprimé sans être envoyé aux destinataires d’origine.

- **Télécharger le message** : dans le volet déroulant qui s’affiche, sélectionnez **Je comprends les risques liés au téléchargement de ce message** pour enregistrer une copie locale du message au format .eml.

- **Envoyer un message**: dans le volet flyout qui apparaît, choisissez les options suivantes :

  - **Type d’objet**: **e-mail** (par défaut), **URL**ou **pièce jointe**.

  - **Format d’envoi**: **ID de message réseau** (par défaut, avec la valeur correspondante dans la zone **ID de message réseau** ) ou **fichier** (accédez à un fichier. eml ou. MSG local). Notez que si vous sélectionnez **fichier** , puis **ID de message réseau**, la valeur initiale est supprimée.

  - **Destinataires**: saisissez au bail d’un destinataire d’origine du message, ou cliquez sur **Sélectionner tout** pour identifier tous les destinataires. Vous pouvez également cliquer sur **Sélectionner tout** , puis supprimer des destinataires de manière sélective.

  - **Raison du dépôt**: **ne doit pas avoir été bloqué** (par défaut) ou **doit avoir été bloqué**.

  Lorsque vous avez terminé, cliquez sur **Envoyer**.

Si vous ne déplacez pas ou ne supprimez pas le message, il sera supprimé après l'expiration de la période de conservation de quarantaine par défaut.

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu’à 100), le volet déroulant **Actions groupées** s’affiche et vous pouvez effectuer les actions suivantes :

- **Déplacer les messages** : Les options sont les mêmes que lorsque vous déplacez un seul message, sauf que vous ne pouvez pas sélectionner **Déplacer les messages pour des destinataires spécifiques**. Vous pouvez seulement sélectionner **Déplacer le message pour tous les destinataires** ou **Déplacer les messages pour d'autres personnes**.

  > [!NOTE]
  > Prenons le scénario suivant : john@gmail.com envoie un message à faith@contoso.com et john@subsidiary.contoso.com. Gmail bifurcation ce message en deux exemplaires qui sont tous deux routés en quarantaine en tant que hameçonnage dans Microsoft. Un administrateur publie ces deux messages dans admin@contoso.com. Le premier message publié qui atteint la boîte aux lettres d’administration est remis. Le deuxième message publié est identifié comme remise en double et est ignoré. Les messages sont identifiés comme étant des doublons s’ils ont le même ID de message et le même horaire de réception.

- **Supprimer des messages** : le message est immédiatement supprimé sans être envoyé aux destinataires d’origine dès que vous cliquez sur **Oui** dans le message d’avertissement qui s’affiche.

Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="atp-only-use-the-security--compliance-center-to-manage-quarantined-files"></a>ATP uniquement : utiliser le centre de sécurité & conformité pour gérer les fichiers mis en quarantaine

> [!NOTE]
> Les procédures des fichiers mis en quarantaine dans cette section sont uniquement disponibles pour les abonnés plan 1 et plan 2.

Dans les organisations avec ATP, les administrateurs peuvent gérer les fichiers mis en quarantaine dans SharePoint Online, OneDrive entreprise et Microsoft Teams.

### <a name="view-quarantined-files"></a>Afficher les fichiers en quarantaine

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Examiner** \> **Quarantaine**.

2. Modifier la **vue mise en quarantaine** sur les **fichiers**de valeurs par défaut. Vous pouvez effectuer un tri sur un champ en cliquant sur un en-tête de colonne disponible.

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Modifier les colonnes** pour afficher jusqu’à sept colonnes. Les colonnes par défaut sont marquées d’un astérisque ( <sup>\*</sup> ) :

   - **Utilisateur**<sup>\*</sup>

   - **Emplacements**<sup>\*</sup>

   - **Nom de fichier**<sup>\*</sup>

   - **URL du fichier**<sup>\*</sup>

   - **Taille de fichier**<sup>\*</sup>

   - **Expire**<sup>\*</sup>

   - **Déplacer ?**<sup>\*</sup>

   - **Détectés par**

   - **Modifié par heure**

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres disponibles sont :

   - **Date d’expiration** : filtrer les messages par date d'expiration de la quarantaine :

     - **Aujourd’hui**

     - **Dans les 2 prochains jours**

     - **Dans les 7 prochains jours**

     - Une plage date/heure personnalisée.

   - **Heure de réception**

   - **Raison**de la mise en quarantaine : la seule valeur disponible est **programme malveillant**.

Une fois que vous avez trouvé un fichier en quarantaine spécifique, sélectionnez le fichier pour en afficher les détails et effectuer une action (par exemple, afficher, publier, télécharger ou supprimer le message).

#### <a name="export-file-results"></a>Exporter les résultats des fichiers

1. Sélectionnez les fichiers qui vous intéressent, puis cliquez sur **Exporter les résultats**.

2. Cliquez sur **Oui** dans le message de confirmation qui vous avertit que la fenêtre du navigateur reste ouverte.

3. Lorsque l’exportation est prête, vous pouvez nommer et choisir l’emplacement de téléchargement du fichier .csv.

#### <a name="view-quarantined-file-details"></a>Afficher les détails des fichiers en quarantaine

Lorsque vous sélectionnez un fichier dans la liste, les détails de fichier suivants s’affichent dans le volet flyout de **Détails** :

- **Nom de fichier**

- **URL du fichier**: URL qui définit l’emplacement du fichier (par exemple, dans SharePoint Online).

- **Contenu malveillant détecté sur** Date/heure de mise en quarantaine du fichier.

- **Expire**: date à laquelle le fichier sera supprimé de la quarantaine.

- **Détecté par**: ATP (protection avancée contre les menaces) ou le moteur anti-programme malveillant de Microsoft.

- **Déplacer ?**

- **Nom du programme malveillant**

- **ID de document**: identificateur unique pour le document.

- **Taille du fichier**: en kilo-octets (Ko).

- **Organisation** ID unique de votre organisation.

- **Dernière modification**

- **Modifié par**: utilisateur qui a modifié le fichier pour la dernière fois.

- **Valeur 256-bit (SHA-256) de l’algorithme de hachage sécurisé**: vous pouvez utiliser cette valeur de hachage pour identifier le fichier dans d’autres magasins de réputation ou dans d’autres emplacements de votre environnement.

### <a name="take-action-on-quarantined-files"></a>Effectuer des actions sur les fichiers mis en quarantaine

Lorsque vous sélectionnez un fichier dans la liste, vous pouvez effectuer les actions suivantes sur le fichier dans le volet flyout de **Détails** :

- **Fichiers de version**: sélectionnez (par défaut) ou désélectionnez **les fichiers de rapports à Microsoft pour analyse**, puis cliquez sur **libérer les fichiers**.

- **Télécharger un fichier**

- **Supprimer le fichier de la quarantaine**

Si vous ne libérez pas ou ne supprimez pas les fichiers, ils seront supprimés une fois la période de rétention de quarantaine par défaut expirée.

#### <a name="actions-on-multiple-quarantined-files"></a>Actions sur plusieurs fichiers mis en quarantaine

Lorsque vous sélectionnez plusieurs fichiers mis en quarantaine dans la liste (jusqu’à 100), le volet flyout **actions en bloc** s’affiche et vous pouvez effectuer les actions suivantes :

- **Fichiers de version**

- **Supprimer des fichiers**: après avoir cliqué sur **Oui** dans le message d’avertissement qui s’affiche, les fichiers sont immédiatement supprimés.

1. À l’aide d’un compte professionnel ou scolaire disposant de privilèges d’administrateur général (ou des rôles de centre de sécurité & conformité appropriés) dans votre organisation, connectez-vous et [accédez au centre de sécurité & conformité](../../compliance/go-to-the-securitycompliance-center.md).

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Utiliser Exchange Online PowerShell ou l’environnement de ligne de commande Exchange EOP PowerShell autonome pour afficher et gérer les messages et les fichiers mis en quarantaine

Les cmdlets que vous utilisez pour afficher et gérer les messages et les fichiers en quarantaine sont les suivantes :

- [Delete-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/delete-quarantinemessage)

- [Export-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/export-quarantinemessage)

- [Get-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/get-quarantinemessage)

- [Preview-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/preview-quarantinemessage): Notez que cette applet de commande concerne uniquement les messages, pas les fichiers de programmes malveillants, pour SharePoint Online, OneDrive entreprise ou Teams.

- [Release-QuarantineMessage](https://docs.microsoft.com/powershell/module/exchange/release-quarantinemessage)
