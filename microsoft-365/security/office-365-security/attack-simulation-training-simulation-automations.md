---
title: Automatisations de simulation pour Exercice de simulation d'attaque
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
description: Les administrateurs peuvent apprendre à créer des simulations automatisées qui contiennent des techniques et charges utiles spécifiques qui sont lancées lorsque les conditions spécifiées sont remplies dans Microsoft Defender pour Office 365 plan 2.
ms.technology: mdo
ms.openlocfilehash: 0b2a177947384d456b2e9a93f6252a98c879458f
ms.sourcegitcommit: 7374c7b013890744d74e5214f7f8d69ca7874466
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/23/2022
ms.locfileid: "67409133"
---
# <a name="simulation-automations-for-attack-simulation-training"></a>Automatisations de simulation pour Exercice de simulation d'attaque

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à** [Microsoft Defender pour Office 365 plan 2](defender-for-office-365.md)

Pour obtenir des informations de prise en main sur Exercice de simulation d'attaque, consultez [Prise en main de Exercice de simulation d'attaque](attack-simulation-training-get-started.md).

Pour créer une automatisation de simulation, procédez comme suit :

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com/>**Email & collaboration** \> **Exercice de simulation d'attaque** \> l’onglet  \> **Automations Simulation automations**.

   Pour accéder directement à l’onglet **Automations** où vous pouvez sélectionner **Automations de simulation**, utilisez <https://security.microsoft.com/attacksimulator?viewid=automations>.

2. Dans **Les automatisations de simulation**, sélectionnez ![l’icône Créer une automatisation.](../../media/m365-cc-sc-create-icon.png) **Créez l’automatisation**.

   :::image type="content" source="../../media/attack-sim-training-sim-automations-create.png" alt-text="Bouton Créer une simulation sous l’onglet Automatisations de simulation dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-sim-automations-create.png":::

3. L’Assistant Création s’ouvre. Le reste de cet article décrit les pages et les paramètres qu’elles contiennent.

> [!NOTE]
> À tout moment pendant l’Assistant Création de simulation, vous pouvez cliquer sur **Enregistrer et fermer** pour enregistrer votre progression et continuer à configurer la simulation ultérieurement. La simulation incomplète comporte le **brouillon** de valeur **d’état** sous l’onglet **Simulations**. Vous pouvez reprendre là où vous vous étiez arrêté en sélectionnant la simulation et en cliquant sur l’icône ![Modifier la simulation.](../../media/m365-cc-sc-edit-icon.png) **Modifiez** la simulation.## Nom et décrivez la simulation.

## <a name="name-and-describe-the-simulation-automation"></a>Nommer et décrire l’automatisation de simulation

Dans la page **de noms Automation** , configurez les paramètres suivants :

- **Nom** : entrez un nom unique et descriptif pour la simulation.
- **Description** : Entrez une description détaillée facultative pour la simulation.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="select-one-or-more-social-engineering-techniques"></a>Sélectionner une ou plusieurs techniques d’ingénierie sociale

Dans la page **Sélectionner les techniques d’ingénierie sociale** , sélectionnez une ou plusieurs des techniques d’ingénierie sociale disponibles, organisées à partir de [MITRE ATT&framework CK®](https://attack.mitre.org/techniques/enterprise/). Différentes charges utiles sont disponibles pour différentes techniques. Les techniques d’ingénierie sociale suivantes sont disponibles :

- **Collecte des informations d’identification** : tente de collecter des informations d’identification en emmenant les utilisateurs vers un site web connu avec des zones d’entrée pour envoyer un nom d’utilisateur et un mot de passe.
- **Pièce jointe de programme malveillant** : ajoute une pièce jointe malveillante à un message. Lorsque l’utilisateur ouvre la pièce jointe, du code arbitraire est exécuté pour aider l’attaquant à compromettre l’appareil de la cible.
- **Lien dans la pièce jointe** : type d’hybride de collecte des informations d’identification. Un attaquant insère une URL dans une pièce jointe. L’URL dans la pièce jointe suit la même technique que la collecte des informations d’identification.
- **Lien vers des programmes malveillants** : exécute du code arbitraire à partir d’un fichier hébergé sur un service de partage de fichiers connu. Le message envoyé à l’utilisateur contient un lien vers ce fichier malveillant. Ouverture du fichier et aide l’attaquant à compromettre l’appareil de la cible.
- **URL de lecteur :** l’URL malveillante dans le message dirige l’utilisateur vers un site web familier qui s’exécute en mode silencieux et/ou installe le code sur l’appareil de l’utilisateur.
- **Octroi de consentement OAuth** : l’URL malveillante demande aux utilisateurs d’accorder des autorisations aux données pour une Azure Application malveillante.

Si vous cliquez sur le lien **Afficher les détails** dans la description, un menu volant de détails s’ouvre qui décrit la technique et les étapes de simulation qui résultent de la technique.

:::image type="content" source="../../media/attack-sim-training-simulations-select-technique-sim-steps.png" alt-text="Menu volant Détails de la technique de collecte des informations d’identification dans la page Sélectionner des techniques d’ingénierie sociale" lightbox="../../media/attack-sim-training-simulations-select-technique-sim-steps.png":::

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="select-a-payload-and-login-page"></a>Sélectionner une charge utile et une page de connexion

Dans la page **Sélectionner la charge utile et la** connexion, vous devez sélectionner une charge utile existante dans la liste ou créer une charge utile.

Vous pouvez également afficher la page de connexion utilisée dans la charge utile, sélectionner une autre page de connexion à utiliser ou créer une page de connexion à utiliser.

### <a name="payload"></a>Charge

Dans la page **Sélectionner des charges utiles** , sélectionnez l’une des options suivantes :

- **Sélectionner manuellement**
- **Randomize**

Si vous sélectionnez **Randomiser**, il n’y a rien à configurer sur cette page. Cliquez donc sur **Suivant** pour continuer.

Si vous **sélectionnez Manuellement**, vous devez sélectionner une ou plusieurs charges utiles dans la liste. Les détails suivants s’affichent pour chaque charge utile :

- **Nom de la charge utile**
- **Technique** : vous devez sélectionner au moins une charge utile par technique que vous avez sélectionnée sur la page précédente.
- **Langue** : Les valeurs disponibles sont : **anglais**, **espagnol**, **allemand**, **japonais**, **Français**, **portugais**, **néerlandais**, **italien**, **suédois**, **chinois (simplifié),****norvégien bokmål**, **polonais**, **russe**, **finnois**, **coréen**, **turc**, **hongrois**, **hébreu**, **thaï**, **arabe**, **vietnamien**, **slovaque**, **grec**, **indonésien**, **roumain**, **slovène**, **croate**, **catalan** ou **autre**.
- **Taux de clic** : nombre de personnes ayant cliqué sur cette charge utile.
- **Taux de compromission prédit** : données historiques de la charge utile dans Microsoft 365 qui prédit le pourcentage de personnes qui seront compromises par cette charge utile.
- **Les simulations lancées** comptent le nombre de fois où cette charge utile a été utilisée dans d’autres simulations.

Dans l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Dans** la zone de recherche, vous pouvez taper une partie du nom de la charge utile et appuyer sur Entrée pour filtrer les résultats.

Si vous cliquez sur **Filtrer**, les filtres suivants sont disponibles :

- **Complexité** : calculée en fonction du nombre d’indicateurs dans la charge utile qui indiquent une attaque possible (fautes d’orthographe, urgence, etc.). D’autres indicateurs sont plus faciles à identifier en tant qu’attaque et indiquent une complexité plus faible. Les valeurs disponibles sont :
  - **High**
  - **Medium**
  - **Faible**

- **Language**

- **Ajouter des balises**

- **Filtrez par thème** : Les valeurs disponibles sont : **Activation** du **compte, vérification du compte**, **Facturation**, **Nettoyage du courrier**, **Document reçu**, **Dépenses**, **Télécopie**, **Rapport financier**, **Messages entrants**, **Facture**, **Éléments reçus**, **Alerte de connexion**, **Courrier reçu**, **Mot de passe**, **Paiement**, **Paie**, **Offre personnalisée**, **Quarantaine**, **Travail à distance**, **passer en revue le message**, **mise à jour de sécurité**, **service suspendu**, **signature requise**, **boîte aux lettres de vérification du stockage de boîte aux lettres de mise à niveau**, **messagerie vocale** et **autres**.

- **Filtrer par marque** : Les valeurs disponibles sont **: American Express**, **Capital One**, **DHL**, **DocuSign**, **Dropbox**, **Facebook**, **First American**, **Microsoft**, **Netflix**, **Scotiabank**, **SendGrid**, **Stewart Title**, **Tesco**, **Wells Fargo**, **Syrinx Cloud** et **Other**.

- **Filtrer par secteur d’activité** : Les valeurs disponibles sont les suivantes : **Services bancaires**, **Services aux entreprises**, **Services à la consommation**, **Éducation**, **Énergie**, **Construction**, **Conseil**, **Services financiers**, **Gouvernement**, **Hôtellerie**, **Assurance**, **Juridique**, **Services Courrier**, **Informatique**, **Santé**, **Fabrication**, **Vente au détail**, **Télécommunications**, **Immobilier**, et **Autres**.

- **Événement actuel** : Les valeurs disponibles sont **Oui** ou **Non**.

- **Controversé** : Les valeurs disponibles sont **Oui** ou **Non**.

Lorsque vous avez terminé de configurer les filtres, cliquez sur **Appliquer**, **Annuler** ou ![Effacer les filtres icône](../../media/m365-cc-sc-clear-filters-icon.png) **Effacer les filtres**.

Si vous sélectionnez une charge utile dans la liste en cliquant n’importe où dans la ligne autre que la case à cocher, les détails sur la charge utile sont affichés dans un menu volant :

- L’onglet **Charge utile** contient un exemple et d’autres détails sur la charge utile.
- L’onglet **Page de connexion** est disponible uniquement dans **Credential Harvest** ou Link dans les charges utiles de **pièce jointe** et est décrit dans la section suivante.
- **L’onglet Simulations lancé** contient le **nom** de la simulation, le **taux de clics**, le **taux compromis** et **l’action**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details-payload-tab.png" alt-text="L’onglet Charge utile dans le menu volant détails de la charge utile dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload-details-payload-tab.png":::

### <a name="login-page"></a>Page de connexion

> [!NOTE]
> L’onglet **Page de connexion** est disponible uniquement dans **la collecte des informations d’identification** ou **lier dans** les charges utiles de pièce jointe.

Sélectionnez la charge utile dans la liste en cliquant n’importe où dans la ligne autre que la case à cocher pour ouvrir le menu volant des détails.

L’onglet **Page de connexion** dans le menu volant détails de la charge utile affiche la page de connexion actuellement sélectionnée pour la charge utile.

Pour afficher la page de connexion complète, utilisez les liens **Page 1** et **Page 2** en bas de la page pour les pages de connexion à deux pages.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-details-login-page-tab.png" alt-text="Onglet Page de connexion dans le menu volant détails de la charge utile dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload-details-login-page-tab.png":::

Pour modifier la page de connexion utilisée dans la charge utile, cliquez sur l’icône ![Modifier la page de connexion.](../../media/m365-cc-sc-edit-icon.png) **Modifier la page de connexion**.

Dans le menu volant **Sélectionner la page de connexion** qui s’affiche, les informations suivantes s’affichent pour chaque page de connexion :

- **Name**
- **Language**
- **Source** : pour les pages de connexion intégrées, la valeur est **Global**. Pour les pages de connexion personnalisées, la valeur est **Locataire**.
- **État** : **Prêt** ou **Brouillon**.
- **Créé par** : Pour les pages de connexion intégrées, la valeur est **Microsoft**. Pour les pages de connexion personnalisées, la valeur est l’UPN de l’utilisateur qui a créé la page de connexion.
- **Dernière modification**
- **Actions** : cliquez sur l’icône ![Aperçu.](../../media/m365-cc-sc-eye-icon.png) **Aperçu** pour afficher un aperçu de la page de connexion.

Pour rechercher une page de connexion dans la liste, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher le nom de la page de connexion.

Cliquez sur l’icône ![Filtrer.](../../media/m365-cc-sc-filter-icon.png) **Filtrez** pour filtrer les pages de connexion par **source** ou **langue**.

:::image type="content" source="../../media/attack-sim-training-simulations-select-payload-select-login-page.png" alt-text="Page Sélectionner la connexion dans l’onglet Page de connexion dans le menu volant détails de la charge utile dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-select-payload-select-login-page.png":::

Pour créer une page de connexion, cliquez sur [Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** pour démarrer l’Assistant Création d’une page de connexion de l’utilisateur final. Les étapes sont les mêmes que dans les **pages de connexion** sous **Exercice de simulation d'attaque’onglet** \> **Bibliothèque de contenu simulé**. Pour obtenir des instructions, consultez [Créer des pages de connexion](attack-simulation-training-login-pages.md#create-login-pages).

De retour sur la **page Sélectionner la connexion**, vérifiez que la nouvelle page de connexion que vous avez créée est sélectionnée, puis cliquez sur **Enregistrer**.

Dans le menu volant détails de la charge utile, cliquez sur [l’icône Fermer.](../../media/m365-cc-sc-close-icon.png) **Fermez**.

Lorsque vous avez terminé sur la **page Sélectionner une charge utile et connexion**, cliquez sur **Suivant**.

## <a name="configure-oauth-payload"></a>Configurer la charge utile OAuth

> [!NOTE]
> Cette page est disponible uniquement si vous avez sélectionné **l’octroi de consentement OAuth** dans la page [Sélectionner des techniques d’ingénierie sociale](#select-one-or-more-social-engineering-techniques) . Sinon, vous accédez à la page **Utilisateurs cibles** .

Dans la page **Configurer la charge utile OAuth** , configurez les paramètres suivants :

- **Nom de l'application**

- **Logo de l’application** : cliquez sur **Parcourir** pour sélectionner un fichier .png, .jpeg ou .gif à utiliser. Pour supprimer un fichier après l’avoir sélectionné, cliquez sur **Supprimer**.

- **Sélectionner l’étendue de l’application** : choisissez l’une des valeurs suivantes :
  - **Accéder en lecture aux calendriers utilisateur**
  - **Accéder en lecture aux contacts utilisateur**
  - **Accéder en lecture aux courriers électroniques utilisateur**
  - **Lire tous les messages de conversations.**
  - **Accéder en lecture à tous les fichiers auxquels cet utilisateur peut accéder**
  - **Accéder en lecture et en écriture aux courriers électroniques utilisateur**
  - **Envoyer un courrier électronique en tant qu’utilisateur**

Lorsque vous avez terminé sur la page **Configurer la charge utile OAuth** , cliquez sur **Suivant**.

## <a name="target-users"></a>Utilisateurs ciblés

Dans la page **Utilisateurs cibles** , sélectionnez qui recevra la simulation. Configurez l’un des paramètres suivants :

- **Incluez tous les utilisateurs de votre organisation** : les utilisateurs concernés sont affichés dans les listes de 10. Vous pouvez utiliser les boutons **Suivant** et **Précédent** directement sous la liste des utilisateurs pour faire défiler la liste. Vous pouvez également utiliser l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Icône De recherche** sur la page pour rechercher les utilisateurs concernés.
- **Inclure uniquement des utilisateurs et des groupes spécifiques** : choisissez l’une des options suivantes :
  - ![Icône Ajouter des utilisateurs.](../../media/m365-cc-sc-create-icon.png) **Ajouter des utilisateurs** : dans le menu volant **Ajouter des utilisateurs** qui s’affiche, vous pouvez trouver des utilisateurs et des groupes en fonction des critères suivants :
    - **Utilisateurs ou groupes** : dans l’icône ![Rechercher des utilisateurs et des groupes.](../../media/m365-cc-sc-search-icon.png) **Recherchez des utilisateurs et des groupes**, vous pouvez taper une partie du **nom** ou **de l’adresse Email** de l’utilisateur ou du groupe, puis appuyer sur Entrée. Vous pouvez sélectionner une partie ou la totalité des résultats. Lorsque vous avez terminé, cliquez sur **Ajouter des utilisateurs x**.

      > [!NOTE]
      > Cliquez sur le bouton **Ajouter des filtres** pour revenir aux **options Filtrer les utilisateurs par catégories** pour effacer tous les utilisateurs ou groupes que vous avez sélectionnés dans les résultats de la recherche.

    - **Filtrer les utilisateurs par catégories** : Sélectionnez parmi aucune, une partie ou l’ensemble des options suivantes :
      - **Groupes d’utilisateurs suggérés** : Sélectionnez parmi les valeurs suivantes :
        - **Tous les groupes d’utilisateurs suggérés**
        - **Utilisateurs non ciblés par une simulation au cours des trois derniers mois**
        - **Récidivistes**
      - **Service** : Utilisez les options suivantes :
        - **Recherche** : dans l’icône ![Rechercher par département.](../../media/m365-cc-sc-search-icon.png) **Recherchez par zone Département** , vous pouvez taper une partie de la valeur Department, puis appuyer sur Entrée. Vous pouvez sélectionner une partie ou la totalité des résultats.
        - Sélectionner **tous les services**
        - Sélectionnez les valeurs Department existantes.
      - **Titre** : Utilisez les options suivantes :
        - **Recherche** : dans l’icône ![Rechercher par titre.](../../media/m365-cc-sc-search-icon.png) **Recherchez par zone Titre** , vous pouvez taper une partie de la valeur Titre, puis appuyer sur Entrée. Vous pouvez sélectionner une partie ou la totalité des résultats.
        - Sélectionner **tout le titre**
        - Sélectionnez les valeurs de titre existantes.

      :::image type="content" source="../../media/attack-sim-training-simulations-target-users-filter-by-category.png" alt-text="Filtrage des utilisateurs sur la page Utilisateurs cibles dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-target-users-filter-by-category.png":::

      Une fois que vous avez identifié vos critères, les utilisateurs affectés s’affichent dans la section **Liste** d’utilisateurs qui s’affiche, où vous pouvez sélectionner certains destinataires ou tous les destinataires découverts.

      Lorsque vous avez terminé, cliquez sur **Appliquer(x),** puis sur **Ajouter des utilisateurs x**.

  De retour sur la page **principale des utilisateurs cibles** , vous pouvez utiliser l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher les utilisateurs affectés. Vous pouvez également cliquer sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer** pour supprimer des utilisateurs spécifiques.

- ![Icône Importer.](../../media/m365-cc-sc-create-icon.png) **Importation** : dans la boîte de dialogue qui s’ouvre, spécifiez un fichier CSV qui contient une adresse e-mail par ligne.

  Une fois que vous avez trouvé un fichier CSV sélectionné, la liste des utilisateurs est importée et affichée sur la page **Utilisateurs ciblés** . Vous pouvez utiliser l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher les utilisateurs affectés. Vous pouvez également cliquer sur l’icône ![Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer** pour supprimer des utilisateurs spécifiques.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="assign-training"></a>Affecter une formation

Dans la page **Affecter une formation** , vous pouvez affecter des formations pour la simulation. Nous vous recommandons d’attribuer une formation pour chaque simulation, car les employés qui suivent la formation sont moins sensibles aux attaques similaires. Les paramètres suivants sont disponibles :

- **Sélectionnez la préférence de contenu d’entraînement** : choisissez l’une des options suivantes :
  - **Expérience de formation Microsoft** : il s’agit de la valeur par défaut avec les options associées suivantes à configurer :
    - Sélectionnez l’une des options suivantes :
      - **Affecter une formation pour moi** : il s’agit de la valeur par défaut et recommandée. Nous affectons l’entraînement en fonction des résultats de simulation et d’entraînement précédents d’un utilisateur, et vous pouvez passer en revue les sélections dans les étapes suivantes de l’Assistant.
      - **Sélectionnez moi-même les cours et modules de formation** : si vous sélectionnez cette valeur, vous pourrez toujours voir le contenu recommandé, ainsi que tous les cours et modules disponibles à l’étape suivante de l’Assistant.
    - **Date d’échéance** : choisissez l’une des valeurs suivantes :
      - **30 jours après la fin** de la simulation : il s’agit de la valeur par défaut.
      - **15 jours après la fin de la simulation**
      - **7 jours après la fin de la simulation**
  - **Redirection vers une URL personnalisée** : cette valeur comporte les options suivantes pour configurer :
    - **URL d’entraînement personnalisée** (obligatoire)
    - **Nom de formation personnalisé** (obligatoire)
    - **Description de l’entraînement personnalisé**
    - **Durée d’apprentissage personnalisée (en minutes)** : la valeur par défaut est 0, ce qui signifie qu’il n’y a pas de durée spécifiée pour l’entraînement.
    - **Date d’échéance** : choisissez l’une des valeurs suivantes :
      - **30 jours après la fin** de la simulation : il s’agit de la valeur par défaut.
      - **15 jours après la fin de la simulation**
      - **7 jours après la fin de la simulation**
  - **Aucune formation** : si vous sélectionnez cette valeur, la seule option sur la page est le bouton **Suivant** qui vous dirige vers la [**page d’accueil**](#landing-page) .

:::image type="content" source="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png" alt-text="Option permettant d’ajouter la formation recommandée sur la page Affectation de formation dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-simulations-assign-training-add-recommended-training.png":::

### <a name="training-assignment"></a>Affectation de formation

> [!NOTE]
> La page **Affectation** de formation n’est disponible que si vous avez sélectionné **l’expérience** \> de formation Microsoft **Sélectionner moi-même les cours et modules de formation** sur la page précédente.

Dans la page **Affectation** de formation, sélectionnez les formations que vous souhaitez ajouter à la simulation en cliquant sur l’icône ![Ajouter des entraînements.](../../media/m365-cc-sc-create-icon.png) **Ajoutez des formations**.

Dans le menu volant **Ajouter une formation** qui s’affiche, vous pouvez sélectionner les formations à utiliser sous les onglets suivants disponibles :

- **Onglet Recommandé** : affiche les formations intégrées recommandées en fonction de la configuration de simulation. Il s’agit des mêmes formations que celles qui auraient été attribuées si vous aviez sélectionné **Affecter une formation pour moi** sur la page précédente.
- **Onglet Tous les entraînements** : affiche toutes les formations intégrées disponibles.

  Les informations suivantes s’affichent pour chaque formation :

  - **Nom de l’entraînement**
  - **Source** : la valeur est **Global**.
  - **Durée (mins)**
  - **Aperçu** : cliquez sur le bouton **Aperçu** pour afficher l’entraînement.

  Dans l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) Dans la zone **de recherche**, vous pouvez taper une partie du nom de l’entraînement et appuyer sur Entrée pour filtrer les résultats sous l’onglet actif.

  Sélectionnez toutes les formations que vous souhaitez inclure dans l’onglet actif, puis cliquez sur **Ajouter**.

De retour sur la page principale **de l’affectation** de formation, les formations que vous avez sélectionnées sont affichées. Les informations suivantes s’affichent pour chaque formation :

- **Nom de l’entraînement**
- **Source**
- **Durée (mins)**

Pour chaque formation de la liste, sélectionnez une ou plusieurs des valeurs suivantes dans la colonne **Affecter à** pour configurer qui obtient l’entraînement :

- **Tous les utilisateurs**
- **Charge utile cliqué**
- **Compromis**

Si vous ne souhaitez pas utiliser une formation affichée, cliquez sur ![l’icône Supprimer.](../../media/m365-cc-sc-delete-icon.png) **Supprimer**

:::image type="content" source="../../media/attack-sim-training-training-assignment.png" alt-text="Page Affectation de formation dans Exercice de simulation d'attaque dans le portail Microsoft 365 Defender" lightbox="../../media/attack-sim-training-training-assignment.png":::

Lorsque vous avez terminé, cliquez sur **Suivant**.

### <a name="landing-page"></a>Page d’accueil

Dans la **page d’accueil** , vous configurez la page web vers laquelle l’utilisateur est amené s’il ouvre la charge utile dans la simulation.

- **Sélectionner la préférence de page d’accueil** : les valeurs disponibles dépendent de vos sélections de charge utile précédentes sur la page [Sélectionner une charge utile et la page de connexion](#select-a-payload-and-login-page) , comme décrit dans le tableau suivant :

  |Sélection de la charge utile|Valeurs disponibles pour sélectionner la préférence de page d’accueil|
  |---|---|
  |Sélectionner manuellement|Utiliser la page d’accueil par défaut de Microsoft <br><br> Créer votre propre page d’accueil <p> Utiliser une URL personnalisée <p> **Remarque** : L’option **Utiliser une valeur d’URL personnalisée** n’est pas disponible si vous avez précédemment sélectionné **La pièce jointe** ou **Lien vers un programme malveillant** dans la page [Sélectionner des techniques d’ingénierie sociale](#select-one-or-more-social-engineering-techniques) .|
  |Randomize|Utiliser la page d’accueil par défaut de Microsoft|

  Les valeurs de **préférence de page d’accueil Select** disponibles et leurs paramètres associés sont décrits dans la liste suivante :

  - **Utilisez la page d’accueil par défaut de Microsoft**. Il s’agit de la valeur par défaut et entraîne une action d’indicateur de modèle, de logo et de charge utile par défaut Microsoft applicable à toutes les charges utiles.

    Vous devez configurer les paramètres supplémentaires suivants sur la **page d’accueil** :

    - **Sélectionnez la mise en page d’accueil** : sélectionnez l’un des 5 modèles de page d’accueil disponibles.
    - **Ajouter un logo** : cliquez sur **Parcourir** pour rechercher et sélectionner un fichier .png, .jpeg ou .gif à ajouter à toutes les charges utiles sélectionnées par Microsoft. La taille du logo doit être de 210 x 70 au maximum pour éviter toute distorsion. Pour supprimer le logo, cliquez sur **Supprimer**.
    - **Indicateurs de charge utile** : ce paramètre n’est pas disponible si vous avez précédemment sélectionné **La pièce jointe** ou **lier aux programmes malveillants** dans la page [Sélectionner des techniques d’ingénierie sociale](#select-one-or-more-social-engineering-techniques) .

      Sélectionnez **Ajouter des indicateurs de charge utile à l’e-mail** pour aider les utilisateurs à identifier les messages de hameçonnage.

    Vous pouvez afficher un aperçu des résultats en cliquant sur le bouton **Ouvrir l’aperçu** au milieu de la page. Dans le menu volant d’aperçu qui s’affiche, vous pouvez utiliser **la charge utile Select pour afficher un aperçu** pour voir à quoi ressemble chaque charge utile.

  - **Créez votre propre page d’accueil** : cette valeur génère une action d’indicateur de charge utile unique appliquée aux charges utiles sélectionnées.

    Vous devez configurer les paramètres supplémentaires suivants sur la **page d’accueil** :

    - **Ajouter des indicateurs de charge utile à l’e-mail** : ce paramètre est disponible pour être sélectionné uniquement si les deux instructions suivantes sont vraies :
      - Vous avez sélectionné **La récolte des informations d’identification**, **lier en pièce jointe**, **URL drive-by** ou **octroi de consentement OAuth** dans la page [Sélectionner des techniques d’ingénierie sociale](#select-one-or-more-social-engineering-techniques) .
      - Vous avez ajouté la **balise dynamique** nommée **Insérer du contenu de charge utile** dans le contenu de la page d’accueil de cette page.

    - Contenu de la page d’accueil : deux onglets sont disponibles :

      - **Texte** : un éditeur de texte enrichi est disponible pour créer votre page d’accueil. Outre les paramètres de police et de mise en forme classiques, les paramètres suivants sont disponibles :
        - **Balise dynamique** : sélectionnez parmi les balises suivantes :

          |Nom de balise|Valeur de balise|
          |---|---|
          |**Insérer un nom d’utilisateur**|`${userName}`|
          |**Insérer un prénom**|`${firstName}`|
          |**Insérer le nom**|`${lastName}`|
          |**Insérer un UPN**|`${upn}`|
          |**Insérer Email**|`${emailAddress}`|
          |**Insérer un service**|`${department}`|
          |**Gestionnaire d’insertion**|`${manager}`|
          |**Insérer un téléphone mobile**|`${mobilePhone}`|
          |**Insérer une ville**|`${city}`|
          |**Insérer le nom de l’expéditeur**|`${FromName}`|
          |**Insérer un e-mail d’expéditeur**|`${FromEmail}`|
          |**Insérer un sujet de charge utile**|`${EmailSubject}`|
          |**Insérer du contenu de charge utile**|`${EmailContent}`|
          |**Insérer une date**|`${date|MM/dd/yyyy|offset}`|

        - **Utiliser par défaut** : sélectionnez l’un des 5 modèles de page d’accueil disponibles pour commencer. Vous pouvez modifier le texte et la disposition dans la zone d’édition. Pour réinitialiser la page d’accueil au texte et à la disposition par défaut du modèle, cliquez sur **Rétablir la valeur par défaut**.
        - **Lien d’entraînement** : dans la boîte de dialogue **Nom de l’URL de formation** qui s’affiche, entrez un titre de lien pour le lien d’entraînement, puis cliquez sur **Confirmer** pour ajouter le lien à la page d’accueil.
      - **Code** : vous pouvez afficher et modifier le code HTML directement.

      Vous pouvez afficher un aperçu des résultats en cliquant sur le bouton **Ouvrir l’aperçu** au milieu de la page. Dans le menu volant d’aperçu qui s’affiche, vous pouvez utiliser **la charge utile Select pour afficher un aperçu** pour voir à quoi ressemble chaque charge utile.

  - **Utilisez une URL personnalisée** : ajoutez l’URL dans la zone **d’URL entrée de la page d’accueil personnalisée** qui s’affiche. Aucune autre option n’est disponible sur la page.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="select-end-user-notification"></a>Sélectionner la notification de l’utilisateur final

Dans la page **Sélectionner la notification de l’utilisateur final** , sélectionnez parmi les options de notification suivantes :

- **Ne pas remettre de notifications** : cliquez sur **Continuer** dans la boîte de dialogue d’alerte qui s’affiche. Si vous sélectionnez cette option, vous accédez à la page [Planification](#simulation-schedule) de simulation lorsque vous cliquez sur **Suivant**.

- **Notification microsoft par défaut (recommandée)** : les paramètres supplémentaires suivants sont disponibles sur la page :

  - **Sélectionnez la langue par défaut** : Les valeurs disponibles sont le **chinois (simplifié),** le **chinois (traditionnel),****l’anglais**, **l’Français**, **l’allemand**, **l’italien**, **le japonais**, **le coréen**, **le portugais**, **le russe**, **l’espagnol** et le **néerlandais**.

  - Par défaut, les notifications suivantes sont incluses :
    - **Notification de renforcement positif Microsoft**
    - **Notification d’affectation de formation par défaut Microsoft**
    - **Notification de rappel d’entraînement par défaut de Microsoft**

    Pour chaque notification, les informations suivantes sont disponibles :
    - **Notifications** : nom de la notification.
    - **Langue** : si la notification contient plusieurs traductions, les deux premières langues sont affichées directement. Pour afficher les langues restantes, pointez sur l’icône numérique (par exemple, **+10**).
    - **Type** : une des valeurs suivantes :
      - **Notification de renforcement positif**
      - **Notification d’affectation de formation**
      - **Notification de rappel de formation**
    - **Préférences de remise** : pour les types de **notification de renforcement positif** et de **rappel d’entraînement** , les valeurs suivantes sont disponibles
      - **Ne pas remettre**
      - **Livrer après la fin de la campagne**
      - **Livrer pendant la campagne**
    - **Actions** : si vous cliquez sur l’icône ![Affichage.](../../media/m365-cc-sc-view-icon.png) **Icône Afficher** , la page **de notification Révision** s’affiche avec les informations suivantes :
      - **Onglet Aperçu** : affichez le message de notification comme les utilisateurs le verront.
        - Pour afficher le message dans différentes langues, utilisez la zone **Sélectionner une langue** .
        - Utilisez la **charge utile Sélectionner pour afficher un aperçu** afin de sélectionner le message de notification pour les simulations qui contiennent plusieurs charges utiles.
      - **Onglet Détails** : Afficher les détails de la notification :
        - **Description de la notification**
        - **Source** : pour les notifications intégrées, la valeur est **Global**. Pour les notifications personnalisées, la valeur est **Locataire**.
        - **Type de notification** : l’un des types suivants se base sur la notification que vous avez sélectionnée à l’origine :
          - **Notification de renforcement positif**
          - **Notification d’affectation de formation**
          - **Notification de rappel de formation**
        - **Modifié par**
        - **Dernière modification**

        Lorsque vous avez terminé, cliquez sur **Fermer**.

  Vous accédez à la page [Planification](#simulation-schedule) de simulation lorsque vous cliquez sur **Suivant**.

- **Notifications personnalisées de l’utilisateur final** : lorsque vous cliquez sur **Suivant**, vous accédez à la page de **notification d’affectation** de formation, comme décrit dans les sections suivantes.

### <a name="training-assignment-notification"></a>Notification d’affectation de formation

La page de **notification d’affectation** de formation n’est disponible que si vous avez sélectionné **les notifications personnalisées de l’utilisateur final** dans la page **[Sélectionner la notification de l’utilisateur final](#select-end-user-notification)** .

Cette page affiche les notifications suivantes et leurs langues configurées :

- **Notification d’affectation de formation par défaut Microsoft**
- Toutes les notifications d’affectation de formation personnalisées que vous avez créées précédemment.

  Ces notifications sont également disponibles dans **les notifications de l’utilisateur final** sous l’onglet **Bibliothèque de contenu Simulation** de Exercice de simulation d'attaque à l’adresse <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. La **notification d’affectation d’entraînement par défaut de Microsoft** est disponible sous l’onglet **Notifications globales**. Les notifications d’affectation de formation personnalisées sont disponibles sous l’onglet **Notifications du locataire**. Pour plus d’informations, consultez [les notifications de l’utilisateur final pour Exercice de simulation d'attaque](attack-simulation-training-end-user-notifications.md).

Vous pouvez sélectionner une notification d’affectation de formation existante ou créer une notification à utiliser :

- Pour sélectionner une notification existante, cliquez dans la zone vide en regard du nom de la notification. Si vous cliquez sur le nom de la notification, la notification est sélectionnée et un menu volant d’aperçu s’affiche. Pour désélectionner la notification, décochez la case en regard de la notification.
- Pour rechercher une notification existante, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher le nom.

  Sélectionnez la notification que vous souhaitez utiliser, puis cliquez sur **Suivant**.

- Pour créer et utiliser une nouvelle notification, cliquez sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** nouveau.

#### <a name="create-new-training-assignment-notification-wizard"></a>Assistant Création d’une notification d’affectation d’apprentissage

Si vous avez cliqué ![sur Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en une nouvelle** sur la page **de notification d’affectation** de formation, un Assistant création de notification s’ouvre.

Les étapes de création sont identiques à celles [décrites dans créer des notifications d’utilisateur final](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Dans la page **Définir les détails** , veillez à sélectionner la **notification d’affectation d’apprentissage** de valeur pour **le type de notification Select**.

Lorsque vous avez terminé, vous revenez à la page de **notification d’affectation** de formation où la notification que vous venez de créer apparaît maintenant dans la liste.

Sélectionnez la notification que vous souhaitez utiliser, puis cliquez sur **Suivant**.

### <a name="training-reminder-notification"></a>Notification de rappel de formation

La page de **notification de rappel** de formation n’est disponible que si vous avez sélectionné **les notifications personnalisées de l’utilisateur final** dans la page **[Sélectionner la notification de l’utilisateur final](#select-end-user-notification)** .

- **Définir la fréquence de notification de rappel** : Sélectionnez **Hebdomadaire** (par défaut) ou **Deux fois par semaine**.

- **Sélectionnez une notification de rappel** : cette section affiche les notifications suivantes et leurs langues configurées :

  - **Notification de rappel d’entraînement par défaut de Microsoft**
  - Toutes les notifications de rappel d’entraînement personnalisées que vous avez créées précédemment.

    Ces notifications sont également disponibles dans **les notifications de l’utilisateur final** sous l’onglet **Bibliothèque de contenu Simulation** de Exercice de simulation d'attaque à l’adresse <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. La **notification de rappel d’entraînement par défaut de Microsoft** est disponible sous l’onglet **Notifications globales**. Des notifications de rappel d’entraînement personnalisées sont disponibles sous l’onglet **Notifications du locataire**. Pour plus d’informations, consultez [les notifications de l’utilisateur final pour Exercice de simulation d'attaque](attack-simulation-training-end-user-notifications.md).

  Vous pouvez sélectionner une notification de rappel de formation existante ou créer une notification à utiliser :

  - Pour sélectionner une notification existante, cliquez dans la zone vide en regard du nom de la notification. Si vous cliquez sur le nom de la notification, la notification est sélectionnée et un menu volant d’aperçu s’affiche. Pour désélectionner la notification, décochez la case en regard de la notification.
  - Pour rechercher une notification existante, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher le nom.

    Sélectionnez la notification que vous souhaitez utiliser, puis cliquez sur **Suivant**.

  - Pour créer et utiliser une nouvelle notification, cliquez sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** nouveau.

#### <a name="create-new-training-reminder-notification-wizard"></a>Assistant Création d’une notification de rappel d’entraînement

Si vous avez cliqué ![sur Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en une nouvelle** sur la page de **notification de rappel de** formation, et un Assistant création de notification s’ouvre.

Les étapes de création sont identiques à celles [décrites dans créer des notifications d’utilisateur final](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Dans la page **Définir les détails** , veillez à sélectionner la **notification de rappel d’entraînement** de valeur pour **le type de notification Select**.

Lorsque vous avez terminé, vous revenez à la page de **notification de rappel** de formation où la notification que vous venez de créer apparaît maintenant dans la liste.

Sélectionnez la notification que vous souhaitez utiliser, puis cliquez sur **Suivant**.

### <a name="positive-reinforcement-notification"></a>Notification de renforcement positif

La page **de notification de renforcement positif** est disponible uniquement si vous avez sélectionné **les notifications personnalisées de l’utilisateur final** dans la page **[Sélectionner la notification de l’utilisateur final](#select-end-user-notification)** .

- **Préférences de remise** : sélectionnez l’une des valeurs suivantes :

  - **Ne pas remettre** : si vous sélectionnez cette option, vous êtes redépilé dans la page [Planification](#simulation-schedule) de simulation lorsque vous cliquez sur **Suivant**.

  - **Remettre une fois que l’utilisateur a signalé un hameçonnage et que la campagne se termine** ou **remettre immédiatement après que l’utilisateur a signalé un hameçonnage** : ces sections affichent les notifications suivantes et leurs langues configurées dans la section **Sélectionner une notification de renforcement positif** qui s’affiche :

  - **Notification de renforcement positif par défaut de Microsoft**
  - Toutes les notifications de renforcement positif personnalisées que vous avez créées précédemment.

    Ces notifications sont également disponibles dans **les notifications de l’utilisateur final** sous l’onglet **Bibliothèque de contenu Simulation** de Exercice de simulation d'attaque à l’adresse <https://security.microsoft.com/attacksimulator?viewid=simulationcontentlibrary>. La **notification de renforcement positif par défaut de Microsoft** est disponible sous l’onglet **Notifications globales**. Des notifications de renforcement positif personnalisées sont disponibles sous l’onglet **Notifications du locataire**. Pour plus d’informations, consultez [les notifications de l’utilisateur final pour Exercice de simulation d'attaque](attack-simulation-training-end-user-notifications.md).

  Vous pouvez sélectionner une notification de renforcement positif existante ou créer une notification à utiliser :

  - Pour sélectionner une notification existante, cliquez dans la zone vide en regard du nom de la notification. Si vous cliquez sur le nom de la notification, la notification est sélectionnée et un menu volant d’aperçu s’affiche. Pour désélectionner la notification, décochez la case en regard de la notification.
  - Pour rechercher une notification existante, utilisez l’icône ![Rechercher.](../../media/m365-cc-sc-search-icon.png) **Zone de recherche** pour rechercher le nom.

    Sélectionnez la notification que vous souhaitez utiliser, puis cliquez sur **Suivant**.

  - Pour créer et utiliser une nouvelle notification, cliquez sur ![Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en un** nouveau.

#### <a name="create-new-positive-reinforcement-notification-wizard"></a>Assistant Création d’une notification de renforcement positif

Si vous avez cliqué ![sur Créer une icône.](../../media/m365-cc-sc-create-icon.png) **Créez-en une nouvelle** sur la page **de notification de renforcement positif** . Un Assistant création de notification s’ouvre.

Les étapes de création sont identiques à celles [décrites dans créer des notifications d’utilisateur final](attack-simulation-training-end-user-notifications.md#create-end-user-notifications).

> [!NOTE]
> Dans la page **Définir les détails** , veillez à sélectionner la **valeur Notification de renforcement positif** pour **le type de notification Select**.

Lorsque vous avez terminé, vous revenez à la page de **notification de renforcement positif** où la notification que vous venez de créer apparaît maintenant dans la liste.

Sélectionnez la notification que vous souhaitez utiliser, puis cliquez sur **Suivant**.

## <a name="simulation-schedule"></a>Planification de la simulation

Dans la page Planification de la **simulation** , sélectionnez l’une des valeurs suivantes :

- **Aléatoire** : vous devez toujours sélectionner la planification sur la page suivante, mais les simulations seront lancées à des moments aléatoires avec la planification.
- **Fixe**

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="schedule-details"></a>Détails de la planification

Ce que vous voyez sur la page **Détails** de la planification varie selon que vous avez sélectionné **Randomd** ou **Fixed** sur la page précédente.

- **Aléatoire** : les paramètres suivants sont disponibles :
  - **Section De démarrage** de la simulation : Configurez le paramètre suivant :
    - **Sélectionnez la date à partir de laquelle vous souhaitez que les simulations commencent**
  - **Section Étendue de simulation** : Configurez les paramètres suivants :
    - **Sélectionnez les jours de la semaine sur lesquels les simulations sont autorisées à démarrer** : sélectionnez un ou plusieurs jours de la semaine.
    - **Entrez le nombre maximal de simulations qui peuvent être démarrées entre les dates de début et de fin** : entrez une valeur comprise entre 1 et 10.
    - **Durées d’envoi aléatoires** : sélectionnez ce paramètre pour aléatoirer les heures d’envoi.
  - **Section De fin** de la simulation : Configurez le paramètre suivant :
    - **Sélectionnez la date à laquelle vous souhaitez que les simulations se terminent**

- **Résolu** : les paramètres suivants sont disponibles :
  - **Section De démarrage** de la simulation : Configurez le paramètre suivant :
    - **Sélectionnez la date à partir de laquelle vous souhaitez que les simulations commencent**
  - **Section Périodicité** de simulation : Configurez les paramètres suivants :
    - **Sélectionnez si vous souhaitez lancer des simulations hebdomadaires ou mensuelles** : sélectionnez l’une des valeurs suivantes :
      - **Hebdomadaire** : il s’agit de la valeur par défaut.
      - **Mensuelle**
    - **Entrez la fréquence en semaines pendant laquelle vous souhaitez que les simulations se reproduisent** : entrez une valeur comprise entre 1 et 99 semaines.
    - **Sélectionnez le jour de la semaine à partir duquel vous souhaitez que les simulations commencent**
  - **Section de fin de simulation** : Sélectionnez l’une des valeurs suivantes :
    - **Sélectionnez la date à laquelle vous souhaitez que les simulations se terminent**
    - **Entrez le nombre d’occurrences des simulations à exécuter avant la fin** : entrez une valeur comprise entre 1 et 10.

Lorsque vous avez terminé, cliquez sur **Suivant**.

## <a name="launch-details"></a>Détails du lancement

Dans la page **Détails du lancement** , configurez les paramètres supplémentaires suivants pour l’automatisation :

- **Utilisez des charges utiles uniques dans les simulations au sein d’une automatisation** : par défaut, ce paramètre n’est pas sélectionné.
- **Ciblez tous les utilisateurs sélectionnés à chaque exécution de simulation** : par défaut, ce paramètre n’est pas sélectionné.
- **Cibler les récidivistes** : par défaut, ce paramètre n’est pas sélectionné. Si vous le sélectionnez, configurez le paramètre suivant qui s’affiche :
  - **Entrez le nombre maximal de fois qu’un utilisateur peut être ciblé dans cette automatisation** : entrez une valeur comprise entre 1 et 10.
- **Envoyer un e-mail de simulation en fonction du paramètre de fuseau horaire actuel de l’utilisateur à partir de l’application web Outlook** : par défaut, ce paramètre n’est pas sélectionné.

- **Afficher la page de collecte des données interstitielles de la technique drive-by** : ce paramètre n’est disponible que si vous avez sélectionné **l’URL Drive-by** dans la page **[Sélectionner des techniques d’ingénierie sociale](#select-one-or-more-social-engineering-techniques)** .  Vous pouvez afficher la superposition qui s’affiche pour les attaques par technique d’URL drive-by. Par défaut, le paramètre est activé sur ![l’icône Bascule.](../../media/scc-toggle-on.png) Pour masquer la superposition et accéder directement à la page d’accueil, désactivez ![ce paramètre pour désactiver l’icône.](../../media/scc-toggle-off.png)

## <a name="review-simulation-automation"></a>Passer en revue l’automatisation de simulation

Dans la page **Vérifier l’automatisation de la simulation** , vous pouvez consulter les détails de votre automatisation de simulation.

Vous pouvez sélectionner **Modifier** dans chaque section pour modifier les paramètres de la section. Vous pouvez également cliquer sur **Précédent** ou sélectionner la page spécifique dans l’Assistant.

Lorsque vous avez terminé, cliquez sur **Envoyer**.
