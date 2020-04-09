---
title: Rechercher et débloquer les messages en quarantaine en tant qu’utilisateur dans Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Consumer/IW
ms.topic: article
ms.service: O365-seccomp
localization_priority: Priority
search.appverid:
- MET150
- MEW150
ms.assetid: efff08ec-68ff-4099-89b7-266e3c4817be
ms.collection:
- M365-security-compliance
description: En tant qu'utilisateur Office 365, vous pouvez afficher, déplacer et supprimer les messages mis en quarantaine (les messages dont vous êtes le destinataire et qui sont en quarantaine car considérés comme du courrier indésirable ou comme des e-mails de masse). Vous pouvez afficher et gérer vos messages mis en quarantaine dans le Centre de sécurité et de conformité.
ms.openlocfilehash: 03c7ce474119ae5ff130b987b58d5130d53c33d6
ms.sourcegitcommit: 053d42480d8aa3792ecb0027ddd53d383a029474
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/07/2020
ms.locfileid: "42941404"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-office-365"></a>Rechercher et déplacer les messages en quarantaine en tant qu’utilisateur dans Office 365

La quarantaine contient des messages potentiellement dangereux ou indésirables dans les organisations Office 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online. Si vous souhaitez en savoir plus, consultez l’article [La quarantaine dans Office 365](quarantine-email-messages.md).

En tant qu'utilisateur, vous pouvez afficher, déplacer et supprimer les messages mis en quarantaine car considérés comme du courrier indésirable, des e-mails de masse, ou (à partir d’avril 2020) de l’hameçonnage, si vous en êtes le destinataire. Vous pouvez afficher et gérer vos messages mis en quarantaine dans le centre de sécurité et de conformité ou (si un administrateur a utilisé cette configuration) dans les [notifications de courrier indésirable de l’utilisateur final](use-spam-notifications-to-release-and-report-quarantined-messages.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre de sécurité et conformité Office 365, accédez à <https://protection.office.com>. Pour ouvrir la page de quarantaine directement, accédez à <https://protection.office.com/quarantine>.

- Les administrateurs peuvent configurer la durée pendant laquelle les messages sont conservés dans la quarantaine avant d’être définitivement supprimés (stratégies anti-courrier indésirable). Les messages dont la mise en quarantaine est arrivée à expiration ne peuvent pas être récupérés. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

- Les administrateurs peuvent également [activer les notifications de courrier indésirable pour l’utilisateur final](configure-your-spam-filter-policies.md#configure-end-user-spam-notifications) dans les stratégies anti-courrier indésirable. Les utilisateurs peuvent débloquer les messages mis en quarantaine pour cause de courrier indésirable, directement à partir de ces notifications, mais ils ne peuvent pas débloquer les messages mis en quarantaine pour hameçonnage. Si vous souhaitez en savoir plus, consultez l’article [Notifications de courrier indésirable pour l’utilisateur final dans Office 365](use-spam-notifications-to-release-and-report-quarantined-messages.md).

- Les messages mis en quarantaine car considérés comme de l’hameçonnage, des programmes malveillants ou par règles de flux de messagerie (également appelés règles de transport) ne sont disponibles que pour les administrateurs. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans Office 365](manage-quarantined-messages-and-files.md).

- Vous ne pouvez déplacer un message et le signaler comme faux positif (légitime) qu'une seule fois.

## <a name="view-your-quarantined-messages"></a>Afficher les messages en quarantaine

1. Dans le Centre de sécurité et conformité, accédez à **Gestion des menaces** \> **Examiner** \> **Quarantaine**.

2. Vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Modifier les colonnes** pour afficher jusqu’à sept colonnes. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

   - **Reçu**<sup>\*</sup>

   - **Expéditeur**<sup>\*</sup>

   - **Sujet**<sup>\*</sup>

   - **Raison de la quarantaine**<sup>\*</sup>

   - **Déplacer ?**<sup>\*</sup>

   - **Type de stratégie**<sup>\*</sup>

   - **Expire**<sup>\*</sup>

   - **Destinataire**

   - **ID de message**

   - **Nom de la stratégie**

   - **Taille**

   - **Direction**

   Lorsque vous avez terminé, cliquez sur **Enregistrer** ou sur **Définir par défaut**.

3. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres disponibles sont :

   - **Date d’expiration** : filtrer les messages par date d'expiration de la quarantaine :

     - **Aujourd’hui**

     - **Dans les 2 prochains jours**

     - **Dans les 7 prochains jours**

     - **Personnaliser**: Entrer une **Date de début** et une **Date de fin**.

   - **Heure de réception**: Entrer une **Date de début** et une **Date de fin**.

   - **Raison de la mise en quarantaine :**

     - **E-mail de masse**

     - **Courrier indésirable**

     - **Hameçonnage** (à partir d’avril 2020)

   Pour effacer le filtre, cliquez sur **Effacer**. Pour masquer le menu déroulant de filtrage, cliquez de nouveau sur **Filtrer**.

4. Utilisez **Trier les résultats par** (le bouton **ID de message** par défaut) et une valeur correspondante pour rechercher des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :

   - **ID du message** : l’identificateur global unique du message. Si vous sélectionnez un message dans la liste, la valeur **ID du message** apparaît dans le volet déroulant **Détails** qui s’affiche. Les administrateurs peuvent utiliser le [suivi des messages](message-trace-scc.md) pour rechercher les messages et les valeurs d’ID de message correspondantes.

   - **Adresse e-mail de l'expéditeur** : adresse e-mail d'un seul expéditeur.

   - **Adresse e-mail du destinataire** : adresse e-mail d'un seul destinataire.

   - **Sujet** : utiliser l'intégralité du sujet du message. La recherche n’est pas sensible à la casse.

   Après avoir entrer les critères de recherche, cliquez sur le ![Bouton actualiser](../media/scc-quarantine-refresh.png) **Actualiser** pour filtrer les résultats.

Une fois le message spécifique mis en quarantaine trouvé, sélectionnez-le pour afficher des détails à son sujet et pour prendre des mesures (par exemple, afficher, déplacer, télécharger ou supprimer le message).

### <a name="export-message-results"></a>Exporter les résultats de message

1. Sélectionnez les messages qui vous intéressent, puis cliquez sur **Exporter les résultats**.

2. Cliquez sur **Oui** dans le message de confirmation qui vous avertit que la fenêtre du navigateur reste ouverte.

3. Lorsque l’exportation est prête, vous pouvez nommer et choisir l’emplacement de téléchargement du fichier .csv.

### <a name="view-quarantined-message-details"></a>Afficher les détails des messages mis en quarantaine

Lorsque vous sélectionnez un message électronique dans la liste, les détails de message suivants s’affichent dans le volet déroulant **Détails** :

- **ID du message** : l’identificateur global unique pour le message.

- **Adresse de l’expéditeur**

- **Reçu** : Date et heure de réception du message.

- **Subject**

- **Raison de la mise en quarantaine** : indique si un message a été identifié comme **Courrier indésirable**, **E-mail de masse** ou (à partir d’avril 2020) **Hameçonnage**.

- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.

- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.

- **Déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.

- **Pas encore déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

Après avoir sélectionné un message, vous pouvez effectuer les actions suivantes dans le volet déroulant **Détails** :

- **Déplacer le message** : dans le volet déroulant qui s’affiche, indiquez si vous souhaitez **Signaler les messages à Microsoft pour analyse**. Cette option est sélectionnée par défaut et signale à Microsoft le message mis en quarantaine par erreur comme un faux positif.

  Lorsque vous avez terminé, cliquez sur **Déplacer les messages**.

- **Afficher l’en-tête du message** : Sélectionnez ce lien pour afficher le texte d’en-tête du message. Pour analyser en profondeur les champs d'en-tête et les valeurs, copiez le texte d’en-tête du message dans le presse-papiers, puis sélectionnez **Analyseur d’en-tête de message Microsoft** pour accéder à l’analyseur de connectivité à distance (Faites un clic droit et sélectionnez **Ouvrir dans un nouvel onglet** si vous ne souhaitez pas laisser Office 365 accomplir cette tâche). Collez l’en-tête du message dans la section analyseur d’en-tête de message de la page, puis sélectionnez **Analyser les en-têtes** :

- **Prévisualiser le message** : dans le volet déroulant qui apparaît, choisissez l’une des options suivantes :

  - **Mode Source** : affiche la version HTML du corps du message, dans laquelle tous les liens sont désactivés.
  
  - **Mode texte** : affiche le corps du message au format texte brut.

- **Télécharger le message** : dans le volet déroulant qui s’affiche, sélectionnez **Je comprends les risques liés au téléchargement de ce message** pour enregistrer une copie locale du message au format .eml.

- **Supprimer de la quarantaine** : Le message est supprimé dès que vous cliquez sur **Oui** dans le message d’avertissement qui s’affiche.

Lorsque vous avez terminé, cliquez sur **Fermer**.

Si vous ne déplacez pas ou ne supprimez pas le message, il sera supprimé après l'expiration de la période de conservation de quarantaine par défaut.

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu’à 100), le volet déroulant **Actions groupées** s’affiche et vous pouvez effectuer les actions suivantes :

- **Déplacer les messages** : Les options sont les mêmes que lorsque vous déplacez un seul message, sauf que vous ne pouvez pas sélectionner **Déplacer les messages pour des destinataires spécifiques**. Vous pouvez seulement sélectionner **Déplacer le message pour tous les destinataires** ou **Déplacer les messages pour d'autres personnes**.

- **Supprimer des messages** : le message est immédiatement supprimé sans être envoyé aux destinataires d’origine dès que vous cliquez sur **Oui** dans le message d’avertissement qui s’affiche.

Lorsque vous avez terminé, cliquez sur **Fermer**.
