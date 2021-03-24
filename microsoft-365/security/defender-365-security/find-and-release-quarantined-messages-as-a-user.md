---
title: Rechercher et débloquer les messages mis en quarantaine en tant qu'utilisateur
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: Consumer/IW
ms.topic: how-to
localization_priority: Priority
search.appverid:
- MET150
- MEW150
ms.assetid: efff08ec-68ff-4099-89b7-266e3c4817be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les utilisateurs peuvent découvrir comment afficher et gérer les messages mis en quarantaine dans Exchange Online Protection (EOP) qui auraient dû leur être remis.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 961912427f9c343f8235f0ed8e990431669ff9e5
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51063382"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Rechercher et publier des messages mis en quarantaine en tant qu’utilisateur dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Si vous souhaitez en savoir plus, consultez l’article [La quarantaine dans EOP](quarantine-email-messages.md).

En tant qu'utilisateur, vous pouvez afficher, déplacer et supprimer les messages mis en quarantaine car considérés comme du courrier indésirable ou des e-mails de masse, si vous en êtes le destinataire. Depuis le 2020 avril, vous pouvez afficher ou supprimer les messages hameçonnage mis en quarantaine (pas d'hameçonnage de haute confiance) auxquels vous êtes destinataire. Vous pouvez afficher et gérer vos messages mis en quarantaine dans le centre de sécurité et de conformité ou (si un administrateur a utilisé cette configuration) dans les [notifications de courrier indésirable de l’utilisateur final](use-spam-notifications-to-release-and-report-quarantined-messages.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Centre de conformité et sécurité, consultez <https://protection.office.com>. Pour ouvrir la page de quarantaine directement, accédez à <https://protection.office.com/quarantine>.

- Les administrateurs peuvent configurer la durée pendant laquelle les messages sont conservés dans la quarantaine avant d’être définitivement supprimés (stratégies anti-courrier indésirable). Les messages dont la mise en quarantaine est arrivée à expiration ne peuvent pas être récupérés. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- Les administrateurs peuvent également [activer les notifications de courrier indésirable pour l’utilisateur final](configure-your-spam-filter-policies.md#configure-end-user-spam-notifications) dans les stratégies anti-courrier indésirable. Les utilisateurs peuvent débloquer les messages mis en quarantaine pour cause de courrier indésirable, directement depuis ces notifications. Les utilisateurs peuvent examiner les messages mis en quarantaine pour hameçonnage (pas les messages d’hameçonnage haute confiance) directement depuis ces notifications. Si vous souhaitez en savoir plus, veuillez consulter l’article [Notifications de courrier indésirable pour l’utilisateur final dans EOP](use-spam-notifications-to-release-and-report-quarantined-messages.md).

- Les messages mis en quarantaine car considérés comme de l’hameçonnage, des programmes malveillants ou par règles de flux de messagerie (également appelés règles de transport) ne sont disponibles que pour les administrateurs. Ils sont en revanche invisibles pour les utilisateurs. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

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
     - **Hameçonnage**

   - **Type de stratégie** : filtrer les messages par type de stratégie :
     - **Stratégie anti-hameçonnage**
     - **Stratégie de filtrage de contenu hébergé** (stratégie anti-courrier indésirable)

   Pour effacer le filtre, cliquez sur **Effacer**. Pour masquer le menu déroulant de filtrage, cliquez de nouveau sur **Filtrer**.

4. Utilisez **Trier les résultats par** (le bouton **ID de message** par défaut) et une valeur correspondante pour rechercher des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :

   - **ID du message** : l’identificateur global unique du message. Si vous sélectionnez un message dans la liste, la valeur **ID du message** apparaît dans le volet déroulant **Détails** qui s’affiche. Les administrateurs peuvent utiliser le [suivi des messages](message-trace-scc.md) pour rechercher les messages et les valeurs d’ID de message correspondantes.

   - **Adresse e-mail de l'expéditeur** : adresse e-mail d'un seul expéditeur.

   - **Nom de la stratégie** : utilisez le nom de stratégie complet indiqué dans le message. La recherche n’est pas sensible à la casse.

   - **Adresse e-mail du destinataire** : adresse e-mail d'un seul destinataire.

   - **Sujet** : utiliser l'intégralité du sujet du message. La recherche n’est pas sensible à la casse.

   Après avoir entrer les critères de recherche, cliquez sur le ![Bouton actualiser](../../media/scc-quarantine-refresh.png) **Actualiser** pour filtrer les résultats.

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

- **Raison de mise en quarantaine** : indique si un message a été identifié comme **courrier indésirable**, **courrier en nombre** ou **hameçonnage**.

- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.

- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.

- **Déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message a été envoyé.

- **Pas encore déplacé pour** : toutes les adresses e-mail (le cas échéant) auxquelles le message n'a pas encore été envoyé.

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

Après avoir sélectionné un message, vous pouvez effectuer les actions suivantes dans le volet déroulant **Détails** :

- **Déplacer le message** : dans le volet déroulant qui s’affiche, indiquez si vous souhaitez **Signaler les messages à Microsoft pour analyse**. Cette option est sélectionnée par défaut et signale à Microsoft le message mis en quarantaine par erreur comme un faux positif.

  Lorsque vous avez terminé, cliquez sur **Déplacer les messages**.

- **Afficher l’en-tête du message** : Sélectionnez ce lien pour afficher le texte d’en-tête du message. Pour analyser en profondeur les champs d'en-tête et les valeurs, copiez le texte d’en-tête du message dans le presse-papiers, puis sélectionnez **Analyseur d’en-tête de message Microsoft** pour accéder à l’analyseur de connectivité à distance (Faites un clic droit et sélectionnez **Ouvrir dans un nouvel onglet** si vous ne souhaitez pas laisser Microsoft 365 accomplir cette tâche). Collez l’en-tête du message dans la section analyseur d’en-tête de message de la page, puis sélectionnez **Analyser les en-têtes** :

- **Prévisualiser le message** : dans le volet déroulant qui apparaît, choisissez l’une des options suivantes :
  - **Mode Source** : affiche la version HTML du corps du message, dans laquelle tous les liens sont désactivés.
  - **Mode texte** : affiche le corps du message au format texte brut.

- **Supprimer de la quarantaine** : Le message est supprimé dès que vous cliquez sur **Oui** dans le message d’avertissement qui s’affiche.

Lorsque vous avez terminé, cliquez sur **Fermer**.

Si vous ne déplacez pas ou ne supprimez pas le message, il sera supprimé après l'expiration de la période de conservation de quarantaine par défaut.

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu’à 100), le volet déroulant **Actions groupées** s’affiche et vous pouvez effectuer les actions suivantes :

- **Déplacer les messages** : Les options sont les mêmes que lorsque vous déplacez un seul message, sauf que vous ne pouvez pas sélectionner **Déplacer les messages pour des destinataires spécifiques**. Vous pouvez seulement sélectionner **Déplacer le message pour tous les destinataires** ou **Déplacer les messages pour d'autres personnes**.

- **Supprimer des messages** : le message est immédiatement supprimé sans être envoyé aux destinataires d’origine dès que vous cliquez sur **Oui** dans le message d’avertissement qui s’affiche.

Lorsque vous avez terminé, cliquez sur **Fermer**.
