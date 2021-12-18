---
title: Notifications à l’utilisateur final pour la formation à la simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à créer des messages électroniques de notification à l’utilisateur final pour une formation sur la simulation d’attaque dans Microsoft Defender Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: bddd0b587e8fbf3007009a070cbd3e7616faac04
ms.sourcegitcommit: 282f3a58b8e11615b3e53328e6b89a6ac52008e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/17/2021
ms.locfileid: "61561102"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Notifications à l’utilisateur final pour la formation à la simulation d’attaque

Dans la formation à la simulation d’attaques dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les notifications à l’utilisateur final sont des messages électroniques envoyés aux utilisateurs Il existe deux types de notifications de base :

- **Notifications de simulation**: ces messages sont envoyés lorsque les utilisateurs sont inscrits à des formations et en tant que rappels pour les formations requises.
- **Notifications positives :** ces messages sont envoyés lorsque les utilisateurs signalent un message de hameçonnage simulé.

Pour voir la notification de l’utilisateur final disponible, ouvrez le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com> **e-mail,** puis \>  \> **rendez-vous** sur l’onglet Notifications de l’utilisateur final de la formation sur la simulation d’attaques & collaboration. Pour aller directement à l’onglet **Notifications** de l’utilisateur final, utilisez <https://security.microsoft.com/attacksimulator?viewid=endUserNotification> .

**L’onglet Notifications de l’utilisateur** final possède deux onglets :

- **Notifications globales**: contient les notifications intégrées et non modifiables.
- **Notifications client**: contient les notifications personnalisées que vous avez créées.

Les informations suivantes sont affichées pour chaque notification :

- **Notifications**: nom de la notification.
- **Langue**: si la notification contient plusieurs traductions, les deux premières langues sont affichées directement. Pour voir les langues restantes, pointez sur l’icône numérique (par exemple, **+10**).
- **Type :** la valeur est **notification de simulation ou notification** de réception **positive.**
- **Source**: pour les notifications intégrées, la valeur est **Global**. Pour les notifications personnalisées, la valeur est **Client**.
- **État**
- **Simulations liées**
- **Créé par**: Pour les notifications intégrées, la valeur est **Microsoft**. Pour les notifications personnalisées, la valeur est l’UPN de l’utilisateur qui a créé la notification.
- **Heure de création**
- **Modifié par**
- **Heure de la dernière modification**

Pour rechercher une notification dans la liste, utilisez ![ l’icône Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de** recherche pour trouver le nom de la notification.

Pour grouper les notifications par type, cliquez sur ![ Icône Groupe.](../../media/m365-cc-sc-group-icon.png) **Groupez,** puis sélectionnez **Type de notification.** Pour regrouper les notifications, sélectionnez **Aucun**.

Sous **l’onglet Notifications du** client uniquement, cliquez sur ![ Icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) pour filtrer les notifications dans une ou plusieurs langues.

Pour supprimer une ou plusieurs colonnes affichées, cliquez sur Personnaliser ![ l’icône de colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnaliser les colonnes**.

Lorsque vous sélectionnez une notification dans la liste, un volant de détails s’affiche avec les informations suivantes :

- **Onglet Aperçu** : afficher le message de notification. Pour afficher le message dans différentes langues, utilisez la **zone Sélectionner la langue.**
- **Onglet Détails** : afficher les détails de la notification :
  - **Description de la notification**
  - **Source**: pour les notifications intégrées, la valeur est **Global**. Pour les notifications personnalisées, la valeur est **Client**.
  - **Type de notification**
  - **Modifié par**
  - **Dernière modification**

## <a name="create-end-user-notifications"></a>Créer des notifications à l’utilisateur final

Sous **l’onglet Notifications du** client, vous pouvez cliquer sur ![ Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en** une pour démarrer l’Assistant notification de l’utilisateur final.

1. Dans la page **Définir les détails**,** configurez les paramètres suivants :
   - **Sélectionnez le type de notification**: une notification de notification de réception **positive** ou une notification **de simulation** sont disponibles.
   - **Nom**: entrez un nom unique.
   - **Description**: entrez une description facultative.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

2. Dans la page **Définir le** contenu, le seul paramètre disponible est le bouton Ajouter du contenu en **langue métier.** Lorsque vous cliquez dessus, un volant **Ajouter du contenu dans** la langue par défaut s’affiche et contient les paramètres suivants :
   - **À partir du nom complet**
   - **À partir de l’adresse e-mail**
   - **Sélectionnez la langue de l’e-mail**: sélectionnez une langue dans la liste.
   - **Marquez-le comme** langue par défaut : comme il s’agit de la première et unique langue de la notification, cette valeur est sélectionnée et vous ne pouvez pas la modifier.
   - **Objet**: la valeur par défaut est **Merci d’avoir signalé** le hameçonnage, mais vous pouvez la modifier.
   - **Importer le** courrier électronique : vous pouvez éventuellement cliquer sur ce bouton, puis cliquer sur **Choisir** un fichier pour importer un fichier de message en texte simple existant.
   - Zone de contenu de messagerie électronique : deux onglets sont disponibles :
     - **Onglet Texte** : un éditeur de texte enrichi est disponible pour créer votre courrier électronique de notification. Outre les paramètres de police et de mise en forme classiques, les paramètres suivants sont disponibles :
       - **Balise dynamique**: sélectionnez l’une des balises suivantes :
         - **Insérer le prénom**
         - **Insérer le nom**
         - **Insérer un UPN**
         - **Insérer une adresse de messagerie**
         - **Insérer une charge utile**
     - **Onglet Code** : vous pouvez afficher et modifier directement le code HTML.

   Vous pouvez afficher un aperçu des résultats en cliquant sur le bouton Aperçu **du courrier** électronique en haut de la page.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   Vous êtes revenir à la **page** Définir le contenu dans laquelle la notification que vous vient de créer est résumée avec les informations suivantes :

   - **Language**
   - **Sujet**
   - **Catégorie**
   - **Actions**: les icônes suivantes sont disponibles :
     - ![Icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **Edit**
     - ![Icône Afficher.](../../media/m365-cc-sc-view-icon.png) **View**
     - ![Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**: s’il n’existe que la version linguistique de la notification, vous ne pouvez pas la supprimer.

   Pour ajouter une version de la notification dans une autre langue, cliquez sur ![ Ajouter une icône de traduction. ](../../media/m365-cc-sc-create-icon.png) Dans le **volant Ajouter** une traduction qui s’affiche,  les mêmes paramètres sont disponibles que dans le flyout de langue Ajouter du contenu dans la langue par défaut précédemment décrit. La seule différence est que vous pouvez sélectionner Marquer comme langue **par défaut** dans les traductions supplémentaires.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

   Vous pouvez répéter cette procédure autant de fois que nécessaire pour créer des versions traduites de la notification dans les 12 langues prises en charge.

   Lorsque vous avez terminé, cliquez sur **Suivant**

3. Dans la page **de notification** de révision, vous pouvez consulter les détails de votre notification.

   Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

   Dans la page **Nouvelle notification de simulation** créée, vous pouvez utiliser les liens pour créer une notification, lancer une simulation ou afficher toutes les notifications.

   Lorsque vous avez terminé, cliquez sur **Terminé**.

De retour sous **l’onglet Notifications du** client, la notification que vous avez créée est désormais répertoriée.

Lorsque vous sélectionnez une notification, les options supplémentaires suivantes sont disponibles :

Vous êtes revenir à la page de notification de **réception positive** dans laquelle la notification que vous venons de créer apparaît dans la liste Sélectionner une **notification** positive.

- Pour modifier la notification ou ajouter des traductions supplémentaires, sélectionnez la notification, puis cliquez sur ![ Icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **Modifiez la notification** pour démarrer l’Assistant notification comme décrit précédemment (avec la plupart des valeurs déjà remplies). Si la notification a déjà des traductions pour les 12 langues prise en charge, vous ne pouvez pas ajouter de traductions.

- Pour créer une copie d’une notification, sélectionnez-la, puis cliquez sur ![Créez une icône de copie.](../../media/m365-cc-sc-copy-icon.png).

- Pour supprimer une notification, sélectionnez-la, puis cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png).

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Automatisations de simulation pour la formation à la simulation d’attaques](attack-simulation-training-simulation-automations.md)
