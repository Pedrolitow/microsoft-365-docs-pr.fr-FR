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
ms.openlocfilehash: 8c606daccfd037cad4d894ab7f33ff02fcf172b5
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204166"
---
# <a name="manage-quarantined-messages-and-files-as-an-admin-in-eop"></a>Gérer les messages et fichiers mis en quarantaine en tant qu’administrateur dans Exchange Online PowerShell

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Pour plus d’informations, voir [Messages électroniques mis en quarantaine dans EOP.](quarantine-email-messages.md)

Les administrateurs peuvent afficher, libérer et supprimer tous les types de messages mis en quarantaine pour tous les utilisateurs. Seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants, hameçonnage à haut niveau de confiance ou suite à des règles de flux de messagerie (également appelées règles de transport). Les administrateurs peuvent également signaler des faux positifs à Microsoft.

Les administrateurs des organisations avec Microsoft Defender pour Office 365 peuvent également afficher, télécharger et supprimer des fichiers mis en quarantaine dans SharePoint Online, OneDrive Entreprise et Microsoft Teams.

Vous affichez et gérez les messages mis en quarantaine dans le Centre de sécurité & conformité ou dans PowerShell (Exchange Online PowerShell pour les organisations Microsoft 365 avec boîtes aux lettres dans Exchange Online ; EOP PowerShell autonome pour les organisations sans boîtes aux lettres Exchange Online).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre de conformité et sécurité, consultez <https://protection.office.com>. Pour ouvrir la page de quarantaine directement, accédez à <https://protection.office.com/quarantine>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour prendre des mesures sur les messages mis en quarantaine pour tous les  utilisateurs, vous devez être membre des groupes de rôles Gestion de l’organisation, Administrateur de la sécurité ou Administrateur de la mise en <sup>\*</sup> quarantaine.
  - Pour accéder en lecture seule aux messages mis en quarantaine pour  tous  les utilisateurs, vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.
  - <sup>\*</sup>Les membres du **groupe** de rôles Administrateur  de mise en quarantaine doivent également être membres du groupe de rôles Gestion de l’hygiène dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) pour pouvoir mettre en quarantaine les procédures dans Exchange Online PowerShell.

- Les messages mis en quarantaine sont conservés pendant une période par défaut avant d’être automatiquement supprimés :
  - 30 jours pour les messages mis en quarantaine par des stratégies anti-courrier indésirable (courrier indésirable, hameçonnage et courrier électronique en masse). Il s’agit de la valeur par défaut et de la valeur maximale. Pour configurer (plus bas) cette valeur, voir [Configurer des stratégies anti-courrier indésirable.](configure-your-spam-filter-policies.md)
  - 15 jours pour les messages contenant des programmes malveillants.
  - 15 jours pour les fichiers mis en quarantaine par pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams dans Defender pour Office 365.

  Lorsqu’un message arrive à expiration de la quarantaine, vous ne pouvez pas le récupérer.

## <a name="use-the-security--compliance-center-to-manage-quarantined-email-messages"></a>Utiliser le Centre de sécurité & conformité pour gérer les messages électroniques mis en quarantaine

### <a name="view-quarantined-email"></a>Afficher les e-mails mis en quarantaine

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Examiner** \> **Quarantaine**.

2. Vérifiez que l’option **Afficher les mis en quarantaine** est définie sur la valeur par défaut de **messagerie**.

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Modifier les colonnes** pour afficher jusqu’à sept colonnes. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

   - **Reçu**<sup>\*</sup>
   - **Expéditeur**<sup>\*</sup>
   - **Sujet**<sup>\*</sup>
   - **Raison de la quarantaine**<sup>\*</sup>
   - **Déplacer ?**<sup>\*</sup>
   - **Type de stratégie**<sup>\*</sup>
   - **Date d’expiration**
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
     - **Hameçonnage**: le  verdict de filtrage du courrier indésirable était le courrier de hameçonnage ou la protection anti-hameçonnage mis en quarantaine le message ([paramètres](set-up-anti-phishing-policies.md#spoof-settings) d’usurpation d’identité ou protection contre [l’usurpation d’identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Programme malveillant**
     - **Courrier indésirable**
     - **Hameçonnage à haut niveau de confiance**

   - **Type de stratégie** : filtrer les messages par type de stratégie :
     - **Stratégie anti-programme malveillant**
     - **Stratégie de pièces jointes sécurisées**
     - **Stratégie anti-hameçonnage**
     - **Stratégie de filtrage de contenu hébergé** (stratégie anti-courrier indésirable)
     - **Règle de transport**

   - **Destinataire du message** électronique : tous les utilisateurs ou uniquement les messages qui vous sont envoyés. Les utilisateurs finaux peuvent uniquement gérer les messages mis en quarantaine qui leur sont envoyés.

   Pour effacer le filtre, cliquez sur **Effacer**. Pour masquer le menu déroulant de filtrage, cliquez de nouveau sur **Filtrer**.

5. Utilisez **Trier les résultats par** (le bouton **ID de message** par défaut) et une valeur correspondante pour rechercher des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :

   - **ID du message** : l’identificateur global unique du message.

     Par exemple, [](message-trace-scc.md) vous avez utilisé le suivi des messages pour rechercher un message qui a été envoyé à un utilisateur de votre organisation, et vous déterminez que le message a été mis en quarantaine au lieu d’être remis. Assurez-vous d’inclure la valeur complète de l’ID du message, qui peut inclure des crochets ( \<\> ). Par exemple : `<79239079-d95a-483a-aacf-e954f592a0f6@XYZPR00BM0200.contoso.com>`.

   - **Adresse e-mail de l'expéditeur** : adresse e-mail d'un seul expéditeur.

   - **Nom de la stratégie** : utilisez le nom de stratégie complet indiqué dans le message. La recherche n’est pas sensible à la casse.

   - **Adresse e-mail du destinataire** : adresse e-mail d'un seul destinataire.

   - **Sujet** : utiliser l'intégralité du sujet du message. La recherche n’est pas sensible à la casse.

   - **Nom de** la stratégie : nom de la stratégie responsable de la mise en quarantaine du message.

   Après avoir entrer les critères de recherche, cliquez sur le ![Bouton actualiser](../../media/scc-quarantine-refresh.png) **Actualiser** pour filtrer les résultats.

Une fois le message spécifique mis en quarantaine trouvé, sélectionnez-le pour afficher des détails à son sujet et pour prendre des mesures (par exemple, afficher, déplacer, télécharger ou supprimer le message).

#### <a name="view-quarantined-message-details"></a>Afficher les détails des messages mis en quarantaine

Lorsque vous sélectionnez un message électronique dans la liste, les détails de message suivants s’affichent dans le volet déroulant **Détails** :

- **ID du message** : l’identificateur global unique pour le message.

- **Adresse de l’expéditeur**

- **Reçu** : Date et heure de réception du message.

- **Subject**

- **Raison de la** mise en quarantaine : indique si un message a été identifié comme courrier **indésirable,** en **bloc,** **hameçonnage,** correspond à une règle de flux de messagerie ( règle de **transport**), ou a été identifié comme contenant un programme **malveillant**.

- **Nombre de destinataires**

- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.

- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.

- **Déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.

- **Pas encore déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

Une fois que vous avez sélectionné un message, plusieurs options s’offrent à vous pour savoir comment les faire dans le volet volant **Détails** :

- **Message de publication**: dans le volet volant qui s’affiche, choisissez les options suivantes :

  - **Signaler les messages à Microsoft pour** analyse : cette option est sélectionnée par défaut et signale le message mis en quarantaine par erreur à Microsoft comme faux positif. Si le message a été mis en quarantaine en tant que courrier indésirable, en bloc, hameçonnage ou contenant un programme malveillant, le message est également signalé à l’équipe d’analyse du courrier indésirable de Microsoft. En fonction de leur analyse, les règles de filtrage du courrier indésirable à l’échelle du service peuvent être ajustées pour autoriser le message.

  - Choisissez l’une des options suivantes :
    - **Envoyer des messages à tous les destinataires**
    - **Envoyer des messages à des destinataires spécifiques**
    - **Diffuser des messages à d’autres** personnes : notez que la libération de messages de programmes malveillants à des personnes autres que des destinataires d’origine n’est pas prise en charge.

  Lorsque vous avez terminé, cliquez sur **Déplacer les messages**.

  Remarques sur la libération des messages :

  - Vous ne pouvez pas envoyer un message au même destinataire plusieurs fois.
  - Seuls les destinataires qui n’ont pas reçu le message apparaissent dans la liste des destinataires potentiels.

- **Afficher l’en-tête du message** : Sélectionnez ce lien pour afficher le texte d’en-tête du message. Pour analyser en profondeur les champs d'en-tête et les valeurs, copiez le texte d’en-tête du message dans le presse-papiers, puis sélectionnez **Analyseur d’en-tête de message Microsoft** pour accéder à l’analyseur de connectivité à distance (Faites un clic droit et sélectionnez **Ouvrir dans un nouvel onglet** si vous ne souhaitez pas laisser Microsoft 365 accomplir cette tâche). Collez l’en-tête du message dans la section analyseur d’en-tête de message de la page, puis sélectionnez **Analyser les en-têtes** :

- **Prévisualiser le message** : dans le volet déroulant qui apparaît, choisissez l’une des options suivantes :

  - **Mode Source** : affiche la version HTML du corps du message, dans laquelle tous les liens sont désactivés.
  - **Mode texte** : affiche le corps du message au format texte brut.

- **Supprimer de la quarantaine**: une fois que vous avez cliqué sur **Oui** dans l’avertissement qui s’affiche, le message est immédiatement supprimé sans être envoyé aux destinataires d’origine.

- **Télécharger le message** : dans le volet déroulant qui s’affiche, sélectionnez **Je comprends les risques liés au téléchargement de ce message** pour enregistrer une copie locale du message au format .eml.

- **Envoyer un message**: dans le volet volant qui s’affiche, choisissez les options suivantes :

  - **Type d’objet**: **e-mail** (par défaut), **URL** ou **pièce jointe**.

  - **Format de** soumission : **ID de message** réseau (par défaut, avec la valeur correspondante dans la zone **ID** de message réseau) ou fichier **(accédez** à un fichier .eml ou .msg local). Notez que si vous **sélectionnez Fichier,** puis **ID de message** réseau, la valeur initiale a disparu.

  - **Destinataires :** tapez au moment du bail un destinataire d’origine du message, ou cliquez sur **Sélectionner** tout pour identifier tous les destinataires. Vous pouvez également cliquer sur **Sélectionner tout,** puis supprimer de manière sélective des destinataires individuels.

  - **Raison de l’envoi** **: ne doit pas avoir été bloqué** (par défaut) ou doit avoir été **bloqué**.

  Lorsque vous avez terminé, cliquez sur **Envoyer.**

Si vous ne déplacez pas ou ne supprimez pas le message, il sera supprimé après l'expiration de la période de conservation de quarantaine par défaut.

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu’à 100), le volet déroulant **Actions groupées** s’affiche et vous pouvez effectuer les actions suivantes :

- **Déplacer les messages** : Les options sont les mêmes que lorsque vous déplacez un seul message, sauf que vous ne pouvez pas sélectionner **Déplacer les messages pour des destinataires spécifiques**. Vous pouvez seulement sélectionner **Déplacer le message pour tous les destinataires** ou **Déplacer les messages pour d'autres personnes**.

  > [!NOTE]
  > Envisagez le scénario suivant : john@gmail.com envoie un message à faith@contoso.com et john@subsidiary.contoso.com. Gmail bifurcate ce message en deux copies qui sont toutes deux acheminées vers la quarantaine en tant que hameçonnage dans Microsoft. Un administrateur publie ces deux messages admin@contoso.com. Le premier message publié qui atteint la boîte aux lettres d’administration est remis. Le deuxième message publié est identifié comme remise en double et est ignoré. Les messages sont identifiés comme doublons s’ils ont le même ID de message et le même temps de réception.

- **Supprimer des messages**: après avoir cliqué sur **Oui** dans l’avertissement qui s’affiche, les messages sont immédiatement supprimés sans être envoyés aux destinataires d’origine.

Lorsque vous avez terminé, cliquez sur **Fermer**.

## <a name="microsoft-defender-for-office-365-only-use-the-security--compliance-center-to-manage-quarantined-files"></a>Microsoft Defender pour Office 365 uniquement : utiliser le Centre de sécurité & conformité pour gérer les fichiers mis en quarantaine

> [!NOTE]
> Les procédures pour les fichiers mis en quarantaine dans cette section sont disponibles uniquement pour les abonnés à Microsoft Defender pour Office 365 Plan 1 et Plan 2.

Dans les organisations avec Defender pour Office 365, les administrateurs peuvent gérer les fichiers mis en quarantaine dans SharePoint Online, OneDrive Entreprise et Microsoft Teams. Pour activer la protection de ces fichiers, voir Activer les [pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.](turn-on-mdo-for-spo-odb-and-teams.md)

### <a name="view-quarantined-files"></a>Afficher les fichiers mis en quarantaine

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Examiner** \> **Quarantaine**.

2. Modifier **l’affichage mis en quarantaine** dans les fichiers de **valeurs.** Vous pouvez trier un champ en cliquant sur un en-tête de colonne disponible.

3. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Modifier les colonnes** pour afficher jusqu’à sept colonnes. Les colonnes par défaut sont marquées d’un astérisque ( <sup>\*</sup> :

   - **Utilisateur**<sup>\*</sup>
   - **Emplacement**<sup>\*</sup>
   - **Nom de fichier**<sup>\*</sup>
   - **URL du fichier**<sup>\*</sup>
   - **Taille du fichier**<sup>\*</sup>
   - **Expire**<sup>\*</sup>
   - **Déplacer ?**<sup>\*</sup>
   - **Détecté par**
   - **Modifié par heure**

4. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres disponibles sont :

   - **Date d’expiration** : filtrer les messages par date d'expiration de la quarantaine :
     - **Aujourd’hui**
     - **Dans les 2 prochains jours**
     - **Dans les 7 prochains jours**
     - Plage de date/heure personnalisée.
   - **Heure de réception**
   - **Raison de la mise** en quarantaine : la seule valeur disponible est **Programme malveillant.**
   - **Type de stratégie**

Une fois que vous avez trouvé un fichier mis en quarantaine spécifique, sélectionnez-le pour afficher les détails à son sujet et pour prendre des mesures (par exemple, afficher, libérer, télécharger ou supprimer le message).

#### <a name="view-quarantined-file-details"></a>Afficher les détails du fichier mis en quarantaine

Lorsque vous sélectionnez un fichier dans la liste, les détails suivants apparaissent dans le volet volant **Détails** :

- **Nom de fichier**
- **URL du** fichier : URL qui définit l’emplacement du fichier (par exemple, dans SharePoint Online).
- **Contenu malveillant détecté sur** Date/heure de mise en quarantaine du fichier.
- **Expire :** date à laquelle le fichier sera supprimé de la quarantaine.
- **Détecté par**: Defender pour Office 365 ou le moteur anti-programme malveillant de Microsoft.
- **Déplacer ?**
- **Nom du programme malveillant**
- **ID de document**: identificateur unique du document.
- **Taille du** fichier : en kilo-octets (Ko).
- **Organisation** ID unique de votre organisation.
- **Dernière modification**
- **Modifié par**: l’utilisateur qui a modifié le fichier en dernier.
- **Valeur SHA-256 bits (Secure Hash Algorithm)**: vous pouvez utiliser cette valeur de hachage pour identifier le fichier dans d’autres magasins de réputation ou à d’autres emplacements de votre environnement.

### <a name="take-action-on-quarantined-files"></a>Prendre des mesures sur les fichiers mis en quarantaine

Lorsque vous sélectionnez un fichier dans la liste, vous pouvez prendre les mesures suivantes sur le fichier dans le volet volant **Détails** :

- **Release files**: Select (default) or unselect **Report files to Microsoft for analysis,** and then click **Release files**.
- **Télécharger un fichier**
- **Supprimer le fichier de la quarantaine**

Si vous ne les relâchez pas ou ne les supprimez pas, ils seront supprimés à l’expiration de la période de rétention de mise en quarantaine par défaut.

#### <a name="actions-on-multiple-quarantined-files"></a>Actions sur plusieurs fichiers mis en quarantaine

Lorsque vous sélectionnez plusieurs fichiers mis en quarantaine dans la liste (jusqu’à 100), le volet volant **Actions** en bloc s’affiche où vous pouvez prendre les mesures suivantes :

- **Libérer des fichiers**
- **Supprimer des fichiers**: une fois que vous avez cliqué sur **Oui** dans l’avertissement qui s’affiche, les fichiers sont immédiatement supprimés.

## <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-view-and-manage-quarantined-messages-and-files"></a>Utiliser Exchange Online PowerShell ou EOP PowerShell autonome pour afficher et gérer les messages et fichiers mis en quarantaine

Les cmdlets que vous utilisez pour afficher et gérer les messages et les fichiers en quarantaine sont :

- [Delete-QuarantineMessage](/powershell/module/exchange/delete-quarantinemessage)

- [Export-QuarantineMessage](/powershell/module/exchange/export-quarantinemessage)

- [Get-QuarantineMessage](/powershell/module/exchange/get-quarantinemessage)

- [Preview-QuarantineMessage](/powershell/module/exchange/preview-quarantinemessage): notez que cette cmdlet est uniquement pour les messages, et non pour les fichiers de programmes malveillants provenant de pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams.

- [Release-QuarantineMessage](/powershell/module/exchange/release-quarantinemessage)