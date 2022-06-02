---
title: Automatisations de charge utile pour la formation à la simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
ms.localizationpriority: medium
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à créer des e-mails de notification de l’utilisateur final pour la formation de simulation d’attaque dans Microsoft Defender pour Office 365 Plan 2.
ms.technology: mdo
ms.openlocfilehash: b26c8060fb869ea9e02ab06396a5a91281bcf3f0
ms.sourcegitcommit: a7cd723fd62b4b0aae9c2c2df04ead3c28180084
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/02/2022
ms.locfileid: "65839266"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Automatisations de charge utile pour la formation à la simulation d’attaque

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Dans l’entraînement de simulation d’attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les notifications de l’utilisateur final sont des messages électroniques envoyés aux [utilisateurs](attack-simulation-training.md) à la suite de simulations ou [d’automatisations de simulation](attack-simulation-training-simulation-automations.md). Les types de notifications d’utilisateur final suivants sont disponibles :

- **Notification de renforcement positif** : envoyée lorsque les utilisateurs signalent un message de hameçonnage simulé.
- **Notification de simulation** : envoyée lorsque les utilisateurs sont inclus dans une automatisation de simulation ou de simulation, mais qu’aucune formation n’est sélectionnée.
- **Notification d’affectation** de formation : envoyée lorsque des formations requises sont attribuées aux utilisateurs à la suite d’une simulation ou d’automatisations de simulation.
- **Notification de rappel de formation** : envoyée en tant que rappels pour les formations requises.

Pour afficher les notifications disponibles de l’utilisateur final, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse \> **e-mail &** onglet **Simulation** de **simulation** \> d’attaque de collaboration\>, puis sélectionnez **Notifications de l’utilisateur final**. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** dans lequel vous pouvez sélectionner **les notifications de l’utilisateur final**, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Les notifications de l’utilisateur final** comportent deux onglets :

- **Notifications globales** : contient les notifications intégrées et non modifiables.
- **Notifications de locataire** : contient les notifications personnalisées que vous avez créées.

Les informations suivantes s’affichent pour chaque notification :

- **Notifications** : nom de la notification.
- **Langue** : si la notification contient plusieurs traductions, les deux premières langues sont affichées directement. Pour afficher les langues restantes, pointez sur l’icône numérique (par exemple, **+10**).
- **Type** : la valeur est **notification de renforcement positif**, **notification de simulation**, **notification d’affectation** de formation ou **notification de rappel de formation**.
- **Source** : pour les notifications intégrées, la valeur est **Global**. Pour les notifications personnalisées, la valeur est **Locataire**.
- **État** : la valeur est **Ready** ou **Draft**. Sous l’onglet **Notifications globales** , la valeur est toujours **Prête**.
- **Simulations liées** : nombre total de [simulations](attack-simulation-training.md) ou [d’automatisations de simulation](attack-simulation-training-simulation-automations.md) qui utilisent la notification.
- **Créé par** : Pour les notifications intégrées, la valeur est **Microsoft**. Pour les notifications personnalisées, la valeur est l’UPN de l’utilisateur qui a créé la notification.
- **Heure de création**
- **Modifié par**
- **Heure de la dernière modification**

Pour rechercher une notification dans la liste, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour trouver le nom de la notification.

Pour regrouper les notifications par type, cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** , puis sélectionnez **Type de notification**. Pour dissocier les notifications, sélectionnez **Aucune**.

Sous l’onglet **Notifications du locataire** uniquement, cliquez sur ![l’icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) pour filtrer les notifications par une ou plusieurs langues.

Pour supprimer une ou plusieurs colonnes affichées, cliquez sur ![l’icône Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes**.

Lorsque vous sélectionnez une notification dans la liste, un menu volant de détails s’affiche avec les informations suivantes :

- **Onglet Aperçu** : affichez le message de notification comme les utilisateurs le verront. Pour afficher le message dans différentes langues, utilisez la zone **Sélectionner une langue** .
- **Onglet Détails** : Afficher les détails de la notification :
  - **Description de la notification**
  - **Source** : pour les notifications intégrées, la valeur est **Global**. Pour les notifications personnalisées, la valeur est **Locataire**.
  - **Type de notification**
  - **Modifié par**
  - **Dernière modification**
  - **Simulations**
    - **Noms de simulation**
    - **État de la simulation**
    - **Fin le**

Dans le menu volant des détails de l’onglet **Notifications du locataire** uniquement, cliquez sur **Modifier la notification** pour modifier la notification.

## <a name="create-end-user-notifications"></a>Créer des notifications d’utilisateur final

1. Dans le portail Microsoft 365 Defender, <https://security.microsoft.com>accédez à l’onglet \> **e-mail & bibliothèque** de **contenu simulation** de **simulation** \> d’attaque de collaboration\>, puis sélectionnez **notifications de l’utilisateur final**. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** dans lequel vous pouvez sélectionner **les notifications de l’utilisateur final**, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

2. Sous l’onglet **Notifications du locataire** , cliquez sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** pour démarrer l’Assistant notification de l’utilisateur final.

   > [!NOTE]
   > À tout moment pendant l’Assistant Création, vous pouvez cliquer sur **Enregistrer et fermer** pour enregistrer votre progression et continuer à configurer la notification ultérieurement. Vous pouvez reprendre là où vous vous étiez arrêté en sélectionnant la notification sous l’onglet **Notifications du locataire** dans **les notifications de l’utilisateur final**, puis en cliquant sur ![l’icône Modifier l’automatisation.](../../media/m365-cc-sc-edit-icon.png) **Modifier l’automatisation**. La notification partiellement terminée aura la valeur **d’état** **Draft**.

3. Dans la page **Définir les détails** **, configurez les paramètres suivants :
   - **Sélectionnez le type de notification** : sélectionnez l’une des valeurs suivantes :
     - **Notification de renforcement positif**
     - **Notification de simulation**
     - **Notification d’affectation de formation**
     - **Notification de rappel de formation**
   - **Nom** : entrez un nom unique.
   - **Description** : entrez une description facultative.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la page **Définir le contenu** , le seul paramètre disponible est le bouton **Ajouter du contenu dans le langage métier** . Lorsque vous cliquez dessus, un menu volant **Ajouter du contenu dans la langue par défaut** s’affiche et contient les paramètres suivants :
   - **À partir du nom d’affichage**
   - **À partir de l’adresse e-mail**
   - **Sélectionnez la langue de l’e-mail** : sélectionnez une langue dans la liste.
   - **Marquez-la comme langue par défaut** : étant donné qu’il s’agit de la première langue et de la seule langue de la notification, cette valeur est sélectionnée et vous ne pouvez pas la modifier.
   - **Objet** : La valeur par défaut est **Merci pour la création de rapports de hameçonnage**, mais vous pouvez la modifier.
   - **Importer un e-mail** : vous pouvez éventuellement cliquer sur ce bouton, puis cliquer sur **Choisir un fichier** pour importer un fichier de message en texte brut existant.
   - Zone de contenu de l’e-mail : deux onglets sont disponibles :
     - **Onglet Texte** : un éditeur de texte enrichi est disponible pour créer votre e-mail de notification. Outre les paramètres de police et de mise en forme classiques, les paramètres suivants sont disponibles :
       - **Balise dynamique** : sélectionnez parmi les balises suivantes :
         - **Insérer un prénom**
         - **Insérer le nom**
         - **Insérer un UPN**
         - **Insérer une adresse e-mail**
         - **Insérer une charge utile**
     - **Onglet Code** : vous pouvez afficher et modifier le code HTML directement.

   Vous pouvez afficher un aperçu des résultats en cliquant sur le bouton **Aperçu de l’e-mail** en haut de la page.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   Vous revenez à la page **Définir le contenu** , où la notification que vous venez de créer est résumée avec les informations suivantes :

   - **Language**
   - **Sujet**
   - **Catégorie**
   - **Actions** : Les icônes suivantes sont disponibles :
     - ![Icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **Edit**
     - ![Icône d’affichage.](../../media/m365-cc-sc-view-icon.png) **View**
     - ![Icône Effacer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer** : s’il n’existe que la version linguistique de la notification, vous ne pouvez pas la supprimer.

   Pour ajouter une version de la notification dans une autre langue, cliquez sur ![l’icône Ajouter une traduction.](../../media/m365-cc-sc-create-icon.png) Dans le menu volant **Ajouter une traduction** qui s’affiche, les mêmes paramètres sont disponibles que dans le **menu volant Ajouter du contenu dans la langue par défaut** qui a été décrit précédemment. La seule différence est que vous pouvez sélectionner **Marquer comme langue par défaut** dans les traductions supplémentaires.

   Lorsque vous avez terminé, cliquez sur **Enregistrer**

   Vous pouvez répéter ces étapes autant de fois que nécessaire pour créer des versions traduites de la notification dans les 12 langues prises en charge.

   Lorsque vous avez terminé, cliquez sur **Suivant**

5. Dans la page **De notification de révision** , vous pouvez consulter les détails de votre notification.

   Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

   Dans la page **Nouvelle notification de simulation créée** , vous pouvez utiliser les liens pour créer une notification, lancer une simulation ou afficher toutes les notifications.

   Lorsque vous avez terminé, cliquez sur **Terminé**.

De retour sous l’onglet **Notifications du locataire** dans **les notifications de l’utilisateur final**, la notification que vous avez créée est désormais répertoriée.

## <a name="modify-end-user-notifications"></a>Modifier les notifications de l’utilisateur final

Vous ne pouvez pas modifier les notifications intégrées sous l’onglet **Notifications globales** . Vous pouvez uniquement modifier les notifications personnalisées sous l’onglet **Notifications du locataire** .

Pour modifier une notification personnalisée existante sous l’onglet Notifications du locataire, effectuez l’une des **étapes suivantes** :

- Sélectionnez la notification dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Icône Modifier** qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Notifications** et **Langue** de la notification dans la liste, puis sélectionnez ![l’icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**.
- Sélectionnez la notification dans la liste en cliquant n’importe où dans la ligne, à l’exception de la case à cocher. Dans le menu volant d’informations qui s’ouvre, cliquez sur **Modifier la notification**.

L’Assistant Notification de l’utilisateur final s’ouvre avec les paramètres et les valeurs de la notification sélectionnée. Les étapes sont les mêmes que celles décrites dans la section [Créer des notifications de l’utilisateur final](#create-end-user-notifications) .

## <a name="copy-end-user-notifications"></a>Copier les notifications de l’utilisateur final

Pour copier une notification existante sous les **onglets Notifications client** ou **Notifications globales** , effectuez l’une des étapes suivantes :

- Sélectionnez la notification dans la liste en cochant la case, puis cliquez sur l’icône ![Créer une copie.](../../media/m365-cc-sc-edit-icon.png) **Créez une** icône de copie qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Notifications** et **Langue** de la notification dans la liste, puis sélectionnez ![Créer une icône de copie.](../../media/m365-cc-sc-edit-icon.png) **Créez une copie**.

Lorsque vous copiez une notification personnalisée sous l’onglet **Notifications du locataire** , une copie de la notification nommée «\<OriginalName\> - Copier » est disponible dans la liste.

Lorsque vous copiez une notification intégrée sous l’onglet **Notifications globales** , une boîte de **dialogue Créer une copie** s’affiche. La boîte de dialogue confirme qu’une copie de la notification a été créée et qu’elle est disponible sous l’onglet **Notifications du locataire** . Si vous cliquez sur **Accéder à la notification de locataire** , vous accédez à l’onglet **Notifications du locataire** , où la notification intégrée copiée est nommée «\<OriginalName\> - Copier » est disponible dans la liste. Si vous cliquez sur **Rester ici** dans la boîte de dialogue, vous revenez à l’onglet **Notifications globales** .

Une fois la copie créée, vous pouvez la modifier comme [décrit précédemment](#modify-end-user-notifications).

> [!NOTE]
> **L’option Utiliser à partir du contrôle par défaut** sur le **menu volant Ajouter du contenu dans la langue par défaut** dans l’Assistant Notification vous permet de copier le contenu d’une notification intégrée.

## <a name="remove-notifications"></a>Supprimer les notifications

Vous ne pouvez pas supprimer les notifications intégrées de l’onglet **Notifications globales** . Vous pouvez uniquement supprimer les notifications personnalisées sous l’onglet **Notifications du locataire** .

Pour supprimer une notification personnalisée existante de l’onglet Notifications du locataire, effectuez l’une des **étapes suivantes** :

- Sélectionnez la notification dans la liste en cochant la case, puis cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Notifications** et **Langue** de la notification dans la liste, puis sélectionnez ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**.

## <a name="related-links"></a>Liens connexes

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Automatisations de simulation pour l’entraînement de simulation d’attaque](attack-simulation-training-simulation-automations.md)
