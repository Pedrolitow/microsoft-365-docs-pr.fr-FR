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
ms.openlocfilehash: 66e3e029e8da203b35285080caa91dca3a51e5c7
ms.sourcegitcommit: 872ab0b6a225c20274916e07ed4cc4944be9509a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/25/2022
ms.locfileid: "65678836"
---
# <a name="end-user-notifications-for-attack-simulation-training"></a>Automatisations de charge utile pour la formation à la simulation d’attaque

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Dans la formation de simulation d’attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les notifications de l’utilisateur final sont des messages électroniques envoyés aux utilisateurs. Il existe deux types de notifications de base :

- **Notifications de simulation** : ces messages sont envoyés lorsque les utilisateurs sont inscrits à des formations et en tant que rappels pour les formations requises.
- **Notifications de renforcement positif :** ces messages sont envoyés lorsque les utilisateurs signalent un message de hameçonnage simulé.

Pour afficher la notification de l’utilisateur final disponible, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse **e-mail &** onglet **Simulation de simulation** \> d’attaque de collaboration  \> \>, puis sélectionnez **Notifications de l’utilisateur final**. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** , utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Les notifications de l’utilisateur final** comportent deux onglets :

- **Notifications globales** : contient les notifications intégrées et non modifiables.
- **Notifications de locataire** : contient les notifications personnalisées que vous avez créées.

Les informations suivantes s’affichent pour chaque notification :

- **Notifications** : nom de la notification.
- **Langue** : si la notification contient plusieurs traductions, les deux premières langues sont affichées directement. Pour afficher les langues restantes, pointez sur l’icône numérique (par exemple, **+10**).
- **Type** : la valeur est **notification de simulation** ou **notification de renforcement positif**.
- **Source** : pour les notifications intégrées, la valeur est **Global**. Pour les notifications personnalisées, la valeur est **Locataire**.
- **État**
- **Simulations liées**
- **Créé par** : Pour les notifications intégrées, la valeur est **Microsoft**. Pour les notifications personnalisées, la valeur est l’UPN de l’utilisateur qui a créé la notification.
- **Heure de création**
- **Modifié par**
- **Heure de la dernière modification**

Pour rechercher une notification dans la liste, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour trouver le nom de la notification.

Pour regrouper les notifications par type, cliquez sur l’icône ![Groupe.](../../media/m365-cc-sc-group-icon.png) **Regroupez** , puis sélectionnez **Type de notification**. Pour dissocier les notifications, sélectionnez **Aucune**.

Sous l’onglet **Notifications du locataire** uniquement, cliquez sur ![l’icône Filtrer.](../../media/m365-cc-sc-filter-icon.png) pour filtrer les notifications par une ou plusieurs langues.

Pour supprimer une ou plusieurs colonnes affichées, cliquez sur ![l’icône Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes**.

Lorsque vous sélectionnez une notification dans la liste, un menu volant de détails s’affiche avec les informations suivantes :

- **Onglet Aperçu** : afficher le message de notification. Pour afficher le message dans différentes langues, utilisez la zone **Sélectionner une langue** .
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

Sous l’onglet **Notifications du locataire** , vous pouvez cliquer sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** pour démarrer l’Assistant Notification de l’utilisateur final.

1. Dans la page **Définir les détails** **, configurez les paramètres suivants :
   - **Sélectionnez le type de notification** : sélectionnez l’une des valeurs suivantes :
     - **Notification de renforcement positif**
     - **Notification de simulation**
     - **Notification d’affectation de formation**
     - **Notification de rappel de formation**
   - **Nom** : entrez un nom unique.
   - **Description** : entrez une description facultative.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

2. Dans la page **Définir le contenu** , le seul paramètre disponible est le bouton **Ajouter du contenu dans le langage métier** . Lorsque vous cliquez dessus, un menu volant **Ajouter du contenu dans la langue par défaut** s’affiche et contient les paramètres suivants :
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

3. Dans la page **De notification de révision** , vous pouvez consulter les détails de votre notification.

   Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

   Dans la page **Nouvelle notification de simulation créée** , vous pouvez utiliser les liens pour créer une notification, lancer une simulation ou afficher toutes les notifications.

   Lorsque vous avez terminé, cliquez sur **Terminé**.

De retour sous l’onglet **Notifications du locataire** , la notification que vous avez créée est maintenant répertoriée.

Lorsque vous sélectionnez une notification, les options supplémentaires suivantes sont disponibles :

Vous revenez à la page de **notification de renforcement positif** , où la notification que vous venez de créer apparaît maintenant dans la liste **Sélectionner une notification de renforcement positif** .

- Pour modifier la notification ou ajouter des traductions supplémentaires, sélectionnez la notification, puis cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Modifiez la notification** pour démarrer l’Assistant notification comme décrit précédemment (avec la plupart des valeurs déjà renseignées). Si la notification contient déjà des traductions pour les 12 langues prises en charge, vous ne pouvez pas ajouter d’autres traductions.

- Pour créer une copie d’une notification, sélectionnez-la, puis cliquez sur ![Créer une icône de copie.](../../media/m365-cc-sc-copy-icon.png).

- Pour supprimer une notification, sélectionnez-la, puis cliquez sur ![Icône Supprimer.](../../media/m365-cc-sc-delete-icon.png).

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Automatisations de simulation pour l’entraînement de simulation d’attaque](attack-simulation-training-simulation-automations.md)
