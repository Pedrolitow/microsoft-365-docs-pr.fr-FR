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
ms.localizationpriority: high
search.appverid:
- MET150
- MEW150
ms.assetid: efff08ec-68ff-4099-89b7-266e3c4817be
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les utilisateurs peuvent découvrir comment afficher et gérer les messages mis en quarantaine dans Exchange Online Protection (EOP) qui auraient dû leur être remis.
ms.subservice: mdo
ms.service: microsoft-365-security
adobe-target: true
ms.openlocfilehash: eb53982c581dc44a4a8f0b4144803a43dfdc9aa0
ms.sourcegitcommit: 2dedd0f594b817779e034afa6c4418def2382a22
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2022
ms.locfileid: "67796937"
---
# <a name="find-and-release-quarantined-messages-as-a-user-in-eop"></a>Rechercher et publier des messages mis en quarantaine en tant qu’utilisateur dans EOP

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 avec des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection (EOP) autonomes sans boîtes aux lettres Exchange Online, la quarantaine contient des messages potentiellement dangereux ou indésirables. Si vous souhaitez en savoir plus, consultez l’article [La quarantaine dans EOP](quarantine-email-messages.md).

En tant qu’utilisateur ordinaire (et non administrateur), les fonctionnalités **par défaut** à votre disposition en tant que destinataire d’un message mis en quarantaine sont décrites dans le tableau suivant :

|Raison de la mise en quarantaine :|Afficher|Débloquer|Supprimer|
|---|:---:|:---:|:---:|
|**Stratégies anti-courrier indésirable**||||
|En nombre|![Coche.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|
|Courrier indésirable|![Coche.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|Courrier fortement suspecté d’être indésirable|![Marque de vérification.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|
|Hameçonnage|![Coche.](../../media/checkmark.png)|![Coche](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|Hameçonnage à haute fiabilité||||
|**Stratégies anti-hameçonnage**||||
|Protection contre l’usurpation d’intelligence dans EOP|![Marque de vérification.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|Protection contre l’emprunt d’identité de l’utilisateur dans Defender pour Office 365|![Marque de vérification.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|
|Protection contre l’usurpation de domaine dans Defender pour Office 365|![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|
|Protection de la veille des boîtes aux lettres dans Defender pour Office 365|![Coche.](../../media/checkmark.png)|![Coche.](../../media/checkmark.png)|![Marque de vérification.](../../media/checkmark.png)|
|**Stratégies anti-programme malveillant**||||
|Messages électroniques avec pièces jointes mis en quarantaine en tant que programmes malveillants.||||
|**Pièces jointes sécurisées dans Defender pour Office 365**||||
|Stratégies de pièces jointes fiables qui met en quarantaine les messages électroniques avec des pièces jointes malveillantes en tant que programmes malveillants.||||
|Pièces jointes fiables pour SharePoint, OneDrive et Microsoft Teams qui mettent en quarantaine les fichiers malveillants en tant que programmes malveillants.||||
|**Règles de flux de messagerie (règles de transport)**||||
|Règles de flux de messagerie qui met en quarantaine les messages électroniques.||||

_Les stratégies de quarantaine_ définissent ce que les utilisateurs sont autorisés à faire pour les messages mis en quarantaine en fonction de la raison pour laquelle le message a été mis en quarantaine dans [les fonctionnalités prises en charge](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features). Les stratégies de mise en quarantaine par défaut appliquent les fonctionnalités historiques comme décrit dans le tableau précédent. Les administrateurs peuvent créer et appliquer des stratégies de mise en quarantaine personnalisées qui définissent des fonctionnalités moins restrictives ou plus restrictives pour les utilisateurs dans les fonctionnalités prises en charge. Pour plus d’informations, voir [Stratégies de mise en quarantaine](quarantine-policies.md).

Vous pouvez afficher et gérer vos messages mis en quarantaine dans le Portail Microsoft 365 Defender ou (si un administrateur a utilisé cette configuration) dans les notifications de mise en quarantaine dans les stratégies de mise en quarantaine.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour ouvrir le Portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>. Pour accéder directement à la page de **mise en quarantaine**, utilisez <https://security.microsoft.com/quarantine>.

- Les administrateurs peuvent configurer la durée pendant laquelle les messages sont conservés dans la quarantaine avant d’être définitivement supprimés dans les stratégies anti-courrier indésirable. Les messages dont la mise en quarantaine est arrivée à expiration ne peuvent pas être récupérés. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

- Par défaut, les messages mis en quarantaine car considérés comme de l’hameçonnage à haute fiabilité, des programmes malveillants ou par règles de flux de messagerie ne sont disponibles que pour les administrateurs. Ils sont en revanche invisibles pour les utilisateurs. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

## <a name="view-your-quarantined-messages"></a>Afficher les messages mis en quarantaine

> [!NOTE]
> Votre capacité à afficher les messages mis en quarantaine est contrôlée par la [stratégie de mise en quarantaine](quarantine-policies.md) qui s’applique au type de message mis en quarantaine (qui peut être la [stratégie de mise en quarantaine par défaut pour la raison de mise en quarantaine](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)).

1. Dans le portail Microsoft 365 Defender à <https://security.microsoft.com>, accédez à **E-mail et collaboration**\>**Examiner**\>**Mise en quarantaine**. Pour accéder directement à la page de **mise en quarantaine**, utilisez <https://security.microsoft.com/quarantine>.

2. Sur la page Web **Quarantaine**, vous pouvez trier les résultats en cliquant sur un en-tête de colonne disponible. Cliquez sur **Personnaliser les colonnes** pour modifier les colonnes qui s'affichent. Les valeurs par défaut sont marquées d'un astérisque (<sup>\*</sup>) :

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

   Lorsque vous avez terminé, cliquez sur **Appliquer**.

3. Pour filtrer les résultats, cliquez sur **Filtrer**. Les filtres suivants sont disponibles dans le menu déroulant **Filtres** qui apparaît :
   - **ID du message** : l’identificateur global unique du message.
   - **Adresse de l’expéditeur**
   - **Adresse du destinataire**
   - **Sujet**
   - **Heure reçue** : Saisissez une **heure de début** et une **heure de fin** (date).
   - **Date d’expiration** : filtrer les messages par date d'expiration de la quarantaine :
     - **Aujourd’hui**
     - **Dans les 2 prochains jours**
     - **Dans les 7 prochains jours**
     - **Heure reçue** : Saisissez une **heure de début** et une **heure de fin** (date).
   - **Raison de la mise en quarantaine :**
     - **E-mail de masse**
     - **Courrier indésirable**
     - **Hameçonnage** : Le verdict du filtre anti-spam était **hameçonnant** ou la protection anti-phishing a mis le message en quarantaine ([paramètres d'usurpation](set-up-anti-phishing-policies.md#spoof-settings) ou [protection contre l'usurpation d'identité](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)).
     - **Hameçonnage à haute fiabilité**
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

   Lorsque vous avez terminé, cliquez sur **Appliquer**. Pour effacer les filtres, cliquez sur ![l'icône Effacer les filtres.](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

4. Utilisez le **champ de recherche** et une valeur correspondante pour trouver des messages spécifiques. Les caractères génériques ne sont pas pris en charge. Vous pouvez effectuer une recherche sur les valeurs suivantes :
   - Message ID
   - Adresse de messagerie de l’expéditeur
   - Adresse de messagerie du destinataire
   - Objet. Utiliser l'intégralité du sujet du message La recherche n’est pas sensible à la casse.
   - Nom de la stratégie Nom de la stratégie : utilisez le nom de stratégie complet indiqué dans le message. La recherche n’est pas sensible à la casse.

   Après avoir saisi les critères de recherche, appuyez sur ENTRÉE pour filtrer les résultats.

   > [!NOTE]
   > La zone **de recherche** de la page **de mise en quarantaine** principale recherche uniquement les éléments en quarantaine dans l’affichage actuel, et non la mise en quarantaine entière. Pour rechercher tous les éléments mis en quarantaine, utilisez l'option **Filtre** et le menu déroulant **Filtres** qui en résulte.

Une fois le message spécifique mis en quarantaine trouvé, sélectionnez-le pour afficher des détails à son sujet et pour prendre des mesures (par exemple, afficher, déplacer, télécharger ou supprimer le message).


### <a name="view-quarantined-message-details"></a>Afficher les détails des messages mis en quarantaine

Lorsque vous sélectionnez un message mis en quarantaine dans la liste, les informations suivantes sont disponibles dans le flyout de détails qui apparaît.

:::image type="content" source="../../media/quarantine-user-message-details.png" alt-text="Les détails du menu volant d'un message en quarantaine" lightbox="../../media/quarantine-user-message-details.png":::

Lorsque vous sélectionnez un message électronique dans la liste, les détails de message suivants s’affichent dans le volet déroulant **Détails** :

- **ID du message** : l’identificateur global unique pour le message.
- **Adresse de l’expéditeur**
- **Reçu** : Date et heure de réception du message.
- **Subject**
- **Raison de la mise en quarantaine**
- **Type de politique** : Le type de politique. Par exemple, **la politique anti-spam**.
- **Nombre de destinataires**
- **Destinataires** : si le message contient plusieurs destinataires, vous devez cliquer sur **Prévisualiser le message** ou **Afficher l’en-tête du message** pour afficher la liste complète des destinataires.
- **Expires** : Date et heure auxquelles le message sera automatiquement et définitivement supprimé de la quarantaine.

Pour donner suite au message, consultez la section suivante.

> [!NOTE]
> Pour rester dans le menu déroulant des détails, mais changer le message en quarantaine que vous regardez, utilisez les flèches haut et bas en haut du menu déroulant.
>
> :::image type="content" source="../../media/quarantine-message-details-flyout-up-down-arrows.png" alt-text="Les flèches vers le haut et les flèches vers le bas des détails du menu flottant d'un message en quarantaine" lightbox="../../media/quarantine-message-details-flyout-up-down-arrows.png":::

### <a name="take-action-on-quarantined-email"></a>Effectuer une action sur les messages mis en quarantaine

> [!NOTE]
> Votre capacité à prendre des mesures sur les messages mis en quarantaine est contrôlée par la [stratégie de mise en quarantaine](quarantine-policies.md) qui s’applique au type de message mis en quarantaine (qui peut être la [stratégie de quarantaine par défaut pour la raison de mise en quarantaine](quarantine-policies.md#step-2-assign-a-quarantine-policy-to-supported-features)). Cette section décrit toutes les actions disponibles.

Après avoir sélectionné un message en quarantaine dans la liste, les actions suivantes sont disponibles dans le flyout des détails :

:::image type="content" source="../../media/quarantine-user-message-details-flyout-actions.png" alt-text="Les actions disponibles dans les détails du menu flottant d'un message en quarantaine" lightbox="../../media/quarantine-user-message-details-flyout-actions.png":::

- ![Icône d’e-mail de version.](../../media/m365-cc-sc-check-mark-icon.png) **E-mail de version**<sup>\*</sup> : Transmet le message dans votre boîte de réception.

- ![Afficher l’icône des en-têtes de messages.](../../media/m365-cc-sc-eye-icon.png) **Afficher les en-têtes de message** : Sélectionnez ce lien pour voir le texte de l'en-tête du message. Le flyout de **l'en-tête de message** apparaît avec les liens suivants :
- **Copier l'en-tête du message** : Cliquez sur ce lien pour copier l'en-tête du message (tous les champs d'en-tête) dans votre presse-papiers.
- **Analyseur d'en-tête de message Microsoft Corporation** : Pour analyser en profondeur les champs et les valeurs de l'en-tête, cliquez sur ce lien pour accéder à l'analyseur d'en-tête de message. Collez l'en-tête du message dans la section **Insérez l'en-tête du message que vous souhaitez analyser** (CTRL+V ou cliquez avec le bouton droit de la souris et choisissez **Coller**), puis cliquez sur **Analyser les en-têtes**.

Les actions suivantes sont disponibles après avoir cliqué sur l'icône. ![Autres actions ](../../media/m365-cc-sc-more-actions-icon.png) **Autres actions** :

- ![Icône de prévisualisation de message ](../../media/m365-cc-sc-eye-icon.png) **Prévisualisation de message** : Dans le menu flottant qui apparaît, sélectionnez l'un des onglets suivants :
  - **Affichage Source** : affiche la version HTML du corps du message, dans laquelle tous les liens sont désactivés.
  - **Texte simple** : affiche le corps du message au format texte brut.

- ![Icône Supprimer de la quarantaine.](../../media/m365-cc-sc-delete-icon.png) **Supprimer de la quarantaine** : Après avoir cliqué sur **Oui** dans l'avertissement qui apparaît, le message est immédiatement supprimé sans être envoyé aux destinataires d'origine.

- ![Icône Télécharger l’e-mail.](../../media/m365-cc-sc-download-icon.png) **Télécharger l’e-mail** : dans le menu volant qui s’affiche, configurez les paramètres suivants :
  - **Motif du téléchargement du fichier** : entrez du texte descriptif.
  - **Créer un mot de passe** et **confirmer le mot de passe** : entrez un mot de passe requis pour ouvrir le fichier de message téléchargé.

  Lorsque vous avez terminé, cliquez sur **Télécharger**, puis **Terminé** pour enregistrer une copie locale du message. Le fichier de message .eml est enregistré dans un fichier compressé nommé Mise en quarantaine Messages.zip dans votre dossier **Téléchargements** . Si le fichier .zip existe déjà, un nombre est ajouté au nom de fichier (par exemple, Messages mis en quarantaine(1).zip).

- ![Icône de blocage de l’expéditeur.](../../media/m365-cc-sc-block-sender-icon.png) **Bloquer l'expéditeur** : Ajouter l'expéditeur à la liste des expéditeurs bloqués dans **votre** boîte aux lettres. Pour plus d'informations, consultez [Bloquer un expéditeur du courrier](https://support.microsoft.com/office/b29fd867-cac9-40d8-aed1-659e06a706e4).

<sup>\*</sup> Cette option n'est pas disponible pour les messages qui ont déjà été validés (la **valeur du statut** Validé est **publiée**).

Si vous ne libérez pas ou ne supprimez pas le message, il sera supprimé après l'expiration de la période de conservation en quarantaine par défaut (comme indiqué dans la **colonne Expiration**).

> [!NOTE]
> Sur un appareil mobile, le texte de description n'est pas disponible sur les icônes d'action.
>
> :::image type="content" source="../../media/quarantine-user-message-details-flyout-mobile-actions.png" alt-text="Les détails d'un message en quarantaine avec les actions disponibles mises en évidence" lightbox="../../media/quarantine-user-message-details-flyout-mobile-actions.png":::

>
> Les icônes dans l'ordre et leurs descriptions correspondantes sont résumées dans le tableau suivant :
>
> |Icône|Description|
> |---:|---|
> |![Icône de version d’e-mail](../../media/m365-cc-sc-check-mark-icon.png)|**Version d’e-mail**|
> |![Afficher l’icône des en-têtes de messages.](../../media/m365-cc-sc-eye-icon.png)|**Afficher les en-têtes de messages**|
> |![Afficher l’icône de prévisualisation du message.](../../media/m365-cc-sc-eye-icon.png)|**Afficher une prévisualisation du message**|
> |![Supprimer de l’icône de la quarantaine.](../../media/m365-cc-sc-delete-icon.png)|**Supprimer de la quarantaine**|
> |![Icône de blocage de l’expéditeur.](../../media/m365-cc-sc-block-sender-icon.png)|**Bloquer l’expéditeur**|

#### <a name="take-action-on-multiple-quarantined-email-messages"></a>Effectuer une action sur plusieurs courriers électroniques mis en quarantaine

Lorsque vous sélectionnez plusieurs messages mis en quarantaine dans la liste (jusqu'à 100) en cliquant dans la zone vide à gauche de la première colonne, la liste déroulante **Actions en vrac** s'affiche et vous permet d'effectuer les actions suivantes :

:::image type="content" source="../../media/quarantine-user-message-bulk-actions.png" alt-text="La liste déroulante d'actions groupées pour les messages en quarantaine" lightbox="../../media/quarantine-user-message-bulk-actions.png":::

- ![Icône des messages de publication](../../media/m365-cc-sc-check-mark-icon.png) **Libérer les messages** : Transférer les messages dans votre boîte de réception
- ![Icône Supprimer de la quarantaine](../../media/m365-cc-sc-delete-icon.png) **Supprimer les messages** :  Après avoir cliqué sur **Oui** dans l'avertissement qui apparaît, les messages sont immédiatement supprimés de la quarantaine sans être envoyés aux destinataires d'origine.
