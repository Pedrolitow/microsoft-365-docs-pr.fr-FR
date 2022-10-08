---
title: Pages de connexion dans l’entraînement de simulation d’attaque
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.service: microsoft-365-security
ms.localizationpriority: medium
ms.collection:
- m365-security
- m365initiative-defender-office365
description: Les administrateurs peuvent apprendre à créer et à gérer des pages de connexion pour les attaques par hameçonnage simulées dans Microsoft Defender pour Office 365 Plan 2.
ms.subservice: mdo
search.appverid: met150
ms.openlocfilehash: 315c33a58ffad266ae75e5ae8ccabb013255bdea
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68082866"
---
# <a name="login-pages-in-attack-simulation-training"></a>Pages de connexion dans l’entraînement de simulation d’attaque

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Dans Exercice de simulation d'attaque dans Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2, les pages de connexion sont affichées aux utilisateurs dans des simulations qui utilisent la **collecte des informations d’identification** et **le lien dans** les [techniques d’ingénierie sociale des pièces jointes](attack-simulation-training.md#select-a-social-engineering-technique).

Pour afficher les pages de connexion disponibles, ouvrez le portail Microsoft 365 Defender à <https://security.microsoft.com>l’adresse suivante : accédez à **Email & onglet Collaboration** \> **Exercice de simulation d'attaque** \> Bibliothèque \> de **contenu Simulation**, puis **sélectionnez Pages de** connexion. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** dans lequel vous pouvez sélectionner **des pages de** connexion, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.

**Les pages de connexion** comportent deux onglets :

- **Pages de connexion globales** : contient les pages de connexion intégrées et non modifiables. Il existe quatre pages de connexion intégrées localisées dans plus de 12 langues :
  - **Page de connexion GitHub**
  - **Page de connexion LinkedIn**
  - **Page de connexion Microsoft**
  - **Page de connexion non marquée**

- **Pages de connexion de locataire** : contient les pages de connexion personnalisées que vous avez créées.

Les informations suivantes s’affichent pour chaque page de connexion :

- **Name**
- **Language**
- **Source** : pour les pages de connexion intégrées, la valeur est **Global**. Pour les pages de connexion personnalisées, la valeur est **Locataire**.
- **État** : **Prêt** ou **Brouillon**.
- **Créé par** : Pour les pages de connexion intégrées, la valeur est **Microsoft**. Pour les pages de connexion personnalisées, la valeur est l’UPN de l’utilisateur qui a créé la page de connexion.
- **Dernière modification**

Pour rechercher une page de connexion dans la liste, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher le nom de la page de connexion.

Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer les pages de connexion par **langue** ou **état**.

Pour supprimer une ou plusieurs colonnes affichées, cliquez sur ![l’icône Personnaliser les colonnes.](../../media/m365-cc-sc-customize-icon.png) **Personnalisez les colonnes**.

Lorsque vous sélectionnez une page de connexion dans la liste, un menu volant de détails s’affiche avec les informations suivantes :

- ![Icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **La modification** est disponible uniquement dans les pages de connexion personnalisées sous l’onglet **Pages de connexion du locataire** .
- ![Marquer comme icône par défaut.](../../media/m365-cc-sc-set-as-default-icon.png) **Marquez comme valeur par défaut** pour faire de cette page de connexion la sélection par défaut dans la **collecte des informations d’identification** ou **lier dans** [les charges utiles de](attack-simulation-training-payloads.md) pièce jointe ou [les automatisations de charge utile](attack-simulation-training-payload-automations.md). Si la page de connexion est déjà la page par défaut, ![marquez l’icône par défaut.](../../media/m365-cc-sc-set-as-default-icon.png) **La marque par défaut** n’est pas disponible.
- **Onglet Aperçu** : affichez la page de connexion à mesure que les utilisateurs la verront. Les liens **page 1** et **page 2** sont disponibles en bas de la page pour les pages de connexion à deux pages.
- **Onglet Détails** : Afficher les détails de la page de connexion :
  - **Description**
  - **État** : **Prêt** ou **Brouillon**.
  - **Source de la page de connexion** : pour les pages de connexion intégrées, la valeur est **Global**. Pour les pages de connexion personnalisées, la valeur est **Locataire**.
  - **Modifié par**
  - **Language**
  - **Dernière modification**

## <a name="create-login-pages"></a>Créer des pages de connexion

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>**Email & onglet Collaboration** \> **Exercice de simulation d'attaque** \> Bibliothèque \> de **contenu Simulation**, puis sélectionnez **Pages de** connexion. Pour accéder directement à l’onglet **Bibliothèque de contenu simulation** dans lequel vous pouvez sélectionner **des pages de** connexion, utilisez <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>.
Vous pouvez créer des pages de connexion personnalisées aux emplacements suivants :

   Cliquez sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** pour démarrer l’Assistant Création d’une page de connexion de l’utilisateur final.

   > [!NOTE]
   > ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **La fonctionnalité Créer** est également disponible lors de l’étape de sélection de la charge utile lors de la création d’une automatisation de simulation ou de simulation. Pour plus d’informations, consultez [Créer une simulation : Sélectionner une charge utile et une page de connexion](attack-simulation-training.md#select-a-payload-and-login-page) , et [Créer une automatisation de simulation : Sélectionner une charge utile et une page de connexion](attack-simulation-training-simulation-automations.md#select-a-payload-and-login-page).
   >
   > À tout moment pendant l’Assistant création, vous pouvez cliquer sur **Enregistrer et fermer** pour enregistrer votre progression et continuer à configurer la page de connexion ultérieurement. Vous pouvez reprendre là où vous vous étiez arrêté en sélectionnant la page de connexion sous l’onglet **Pages de connexion du locataire** dans les **pages de** connexion, puis en ![cliquant sur l’icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**. La page de connexion partiellement terminée aura la valeur **d’état** **Draft**.

2. Dans la page **Définir les détails de la page de connexion** , configurez les paramètres suivants :
   - **Nom** : entrez un nom unique.
   - **Description** : entrez une description facultative.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

3. Dans la **page Configurer la page de connexion** , configurez les paramètres suivants :

   - **Sélectionnez une langue** : Les valeurs disponibles sont le **chinois (simplifié),** le **chinois (traditionnel),** **l’anglais**, **l’Français**, **l’allemand**, **l’italien**, **le japonais**, **le coréen**, **le portugais**, **le russe**, **l’espagnol** et le **néerlandais**.

   - **Faites de cette page la page de connexion par défaut** : si vous sélectionnez cette option, la page de connexion sera la sélection par défaut dans la **collecte des informations d’identification** ou **lier dans** [les charges utiles](attack-simulation-training-payloads.md) de pièce jointe ou [les automatisations de charge utile](attack-simulation-training-payload-automations.md).

   - **Créez une connexion à deux pages** : si vous ne sélectionnez pas cette option, la page de connexion est d’une page. Si vous sélectionnez cette option, les onglets **Page 1** et **Page 2** s’affichent pour vous permettre de configurer séparément.

     - Sous l’onglet **Texte** , un éditeur de texte enrichi est disponible pour vous permettre de créer votre page de connexion.

       - Utilisez le contrôle **de balise dynamique** pour personnaliser la page de connexion en insérant les balises disponibles :
         - **Insérer un nom d’utilisateur** : la valeur ajoutée dans le corps du message est `${userName}`.
         - **Insérer un e-mail** : la valeur ajoutée dans le corps du message est `${emailAddress}`.
         - **Date d’insertion** : la valeur ajoutée dans le corps du message est `${date|MM/dd/yyyy|offset}`.

       - Utilisez le contrôle **Utiliser à partir du contrôle par défaut** pour sélectionner une page de connexion intégrée pour commencer en tant que modèle.

       - Le contrôle **bouton Ajouter suivant** est disponible uniquement sur la **page 1** des connexions à deux pages. Le texte par défaut sur le bouton est **Suivant** , mais vous pouvez le modifier.

       - Le contrôle **bouton Ajouter une compromission** est disponible sur les connexions à une page ou sur la **page 2** des connexions à deux pages. Le texte par défaut sur le bouton est **Envoyer**, mais vous pouvez le modifier.

     - Sous l’onglet **Code** , vous pouvez afficher et modifier le code HTML directement. La mise en forme et d’autres contrôles tels que **balise dynamique** et **Utiliser à partir du bouton par défaut** ou **Ajouter une compromission** ne sont pas disponibles.

   - Utilisez le bouton Aperçu de la **page de connexion** en haut de la page pour passer en revue la page de connexion.

   Lorsque vous avez terminé, cliquez sur **Suivant**.

4. Dans la **page Vérifier la page de connexion** , vous pouvez consulter les détails de votre page de connexion.

   Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

   Lorsque vous avez terminé, cliquez sur **Envoyer**.

5. Dans la **page Nouvelle page \<Name\> de connexion créée** , vous pouvez utiliser les liens pour créer une page de connexion, lancer une simulation ou afficher toutes les pages de connexion.

   Lorsque vous avez terminé, cliquez sur **Terminé**.

De retour dans l’onglet **Pages de connexion du locataire** dans les **pages de** connexion, la page de connexion que vous avez créée est maintenant répertoriée.

## <a name="modify-login-pages"></a>Modifier les pages de connexion

Vous ne pouvez pas modifier les pages de connexion intégrées sous l’onglet **Pages de connexion globales** . Vous pouvez uniquement modifier les pages de connexion personnalisées sous l’onglet **Pages de connexion du locataire** .

Pour modifier une page de connexion personnalisée existante sous l’onglet **Pages de connexion du locataire** , effectuez l’une des étapes suivantes :

- Sélectionnez la page de connexion dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Icône Modifier** qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Nom** et **Langue** de la page de connexion dans la liste, puis sélectionnez ![l’icône Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**.
- Sélectionnez la page de connexion dans la liste en cliquant sur le nom. Dans le menu volant des détails qui s’ouvre, cliquez sur l’icône ![Modifier.](../../media/m365-cc-sc-edit-icon.png) **Édition**.

L’Assistant Page de connexion s’ouvre avec les paramètres et les valeurs de la page de connexion sélectionnée. Les étapes sont les mêmes que celles décrites dans la section [Créer des pages de connexion](#create-login-pages) .

## <a name="copy-login-pages"></a>Copier les pages de connexion

Pour copier une page de connexion existante dans les **onglets Pages de connexion du locataire** ou **Pages de connexion globales** , effectuez l’une des étapes suivantes :

- Sélectionnez la page de connexion dans la liste en cochant la case, puis cliquez sur l’icône ![Créer une copie.](../../media/m365-cc-sc-edit-icon.png) **Créez une** icône de copie qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Nom** et **Langue** de la page de connexion dans la liste, puis sélectionnez ![Créer une icône de copie.](../../media/m365-cc-sc-edit-icon.png) **Créez une copie**.

L’Assistant Page de connexion s’ouvre avec les paramètres et les valeurs de la page de connexion sélectionnée. Les étapes sont les mêmes que celles décrites dans la section [Créer des pages de connexion](#create-login-pages) .

> [!NOTE]
> Lorsque vous copiez une page de connexion intégrée sous l’onglet **Pages de connexion globales** , veillez à modifier la valeur **name** . Cette étape garantit que la copie est enregistrée en tant que page de connexion personnalisée sous l’onglet **Pages de connexion du locataire** .
>
> Le contrôle **Utiliser à partir du contrôle par défaut** sur la page **Configurer la page de connexion** dans l’Assistant Page de connexion vous permet de copier le contenu d’une page de connexion intégrée.

## <a name="remove-login-pages"></a>Supprimer les pages de connexion

Vous ne pouvez pas supprimer les pages de connexion intégrées de l’onglet **Pages de connexion globales** . Vous pouvez uniquement supprimer des pages de connexion personnalisées sous l’onglet **Pages de connexion du locataire** .

Pour supprimer une page de connexion personnalisée existante de l’onglet **Pages de connexion du locataire** , effectuez l’une des étapes suivantes :

- Sélectionnez la page de connexion dans la liste en cochant la case, puis cliquez sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Icône Supprimer** qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Nom** et **Langue** de la page de connexion dans la liste, puis sélectionnez ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**

## <a name="make-a-login-page-the-default"></a>Faire d’une page de connexion la page par défaut

La page de connexion par défaut est la sélection par défaut utilisée dans la **collecte des informations d’identification** ou le **lien dans** [les charges utiles de](attack-simulation-training-payloads.md) pièce jointe ou [les automatisations de charge utile](attack-simulation-training-payload-automations.md).

Pour faire d’une page de connexion la valeur par défaut dans les **onglets Pages de connexion** client ou **Pages de connexion globales** , effectuez l’une des étapes suivantes :

- Sélectionnez la page de connexion dans la liste en cliquant sur la case à cocher. Cliquez sur l’icône ![Marquer comme icône par défaut.](../../media/m365-cc-sc-set-as-default-icon.png) **Marquer comme icône par défaut** qui s’affiche.
- Cliquez sur **⋮** (**Actions**) entre les valeurs **Nom** et **Langue** de la page de connexion dans la liste, puis sélectionnez ![Marquer comme icône par défaut.](../../media/m365-cc-sc-set-as-default-icon.png) **Marquez comme valeur par défaut**.
- Sélectionnez la page de connexion dans la liste en cliquant sur le nom. Dans le menu volant des détails qui s’ouvre, cliquez sur ![Marquer comme icône par défaut.](../../media/m365-cc-sc-set-as-default-icon.png) **Marquez comme valeur par défaut**.
- Sélectionnez **Définir comme page de connexion par défaut** dans la page **Configurer la page de connexion** de l’Assistant lorsque vous [créez ou modifiez une page de connexion](#create-login-pages).

> [!NOTE]
> Les procédures précédentes ne sont pas disponibles si la page de connexion est déjà la valeur par défaut.
>
> La page de connexion par défaut est également marquée dans la liste, même si vous devrez peut-être élargir la colonne **Name** pour la voir :
>
> ![Page de connexion par défaut marquée dans la liste des pages de connexion dans Exercice de simulation d'attaque.](../../media/attack-sim-training-login-pages-default.png)

## <a name="related-links"></a>Liens associés

[Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

[Créer une simulation d’attaque par hameçonnage](attack-simulation-training.md)

[Automatisations de simulation pour Exercice de simulation d'attaque](attack-simulation-training-simulation-automations.md)
