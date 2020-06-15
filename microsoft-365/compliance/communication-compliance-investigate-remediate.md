---
title: Examiner et corriger les alertes de conformité des communications
description: Examinez et corrigez les alertes de conformité des communications dans Microsoft 365.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 5bda1556b5726c6e94a6860c7c57f3f7082f2f5e
ms.sourcegitcommit: f80c6c52e5b08290f74baec1d64c4070046c32e4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/12/2020
ms.locfileid: "44717315"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Examiner et corriger les alertes de conformité des communications

Une fois que vous avez configuré vos stratégies de conformité de communication, vous commencerez à recevoir des alertes dans le centre de conformité Microsoft 365 pour les problèmes de message qui correspondent à vos conditions de stratégie. Suivez les instructions de flux de travail ici pour examiner et résoudre les problèmes d’alerte.

## <a name="investigate-alerts"></a>Analyser les alertes

La première étape pour examiner les problèmes détectés par vos stratégies consiste à passer en revue les alertes générées dans le centre de conformité Microsoft 365. Il existe plusieurs domaines dans le centre de conformité pour vous aider à examiner rapidement les alertes, en fonction de la manière dont vous préférez afficher le regroupement des alertes :

- **Page d’accueil de la communication**: lorsque vous vous connectez à à [https://compliance.microsoft.com](https://compliance.microsoft.com) l’aide des informations d’identification d’un compte d’administrateur de votre organisation Microsoft 365, sélectionnez **communication Compliance**  >  **Overview** pour afficher la page d’accueil de la communication. Vous verrez ici :
    - Alertes nécessitant une révision dont la gravité est élevée à faible. Sélectionnez une alerte pour lancer la page Détails de l’alerte et démarrer les actions de correction.
    - Les stratégies récentes correspondent à celles indiquées par nom de stratégie.
    - Éléments résolus affichés par nom de stratégie.
    - Escalades indiquées par nom de stratégie.
    - Utilisateurs avec le plus grand nombre de correspondances de stratégie, classés par ordre décroissant de correspondance.
- **Onglet Alertes**: accédez à **Communication compliance**  >  **alertes** de conformité des communications pour afficher les 30 derniers jours des alertes regroupées par correspondances de stratégie. Cet affichage vous permet de voir rapidement les stratégies de conformité des communications qui génèrent le plus d’alertes classées par gravité.  Pour démarrer les actions de correction, développez une stratégie pour sélectionner une alerte spécifique et pour lancer la page Détails de l’alerte.
- **Onglet stratégies**: accédez à **Communication compliance**  >  **stratégies** de conformité des communications pour afficher les stratégies de conformité de communication configurées pour votre organisation Microsoft 365. Chaque stratégie indiquée inclut le nombre d’alertes qui doivent être réexaminées. La sélection d’une stratégie affiche toutes les alertes en attente concernant la stratégie, la sélection d’une alerte spécifique pour le lancement de la page de détails de stratégie et le démarrage des actions de correction.

### <a name="using-filters"></a>Utilisation de filtres

L’étape suivante consiste à trier les messages de sorte qu’il soit plus facile d’examiner les alertes. La conformité de la communication prend en charge le filtrage multiniveau pour plusieurs champs de message afin de vous aider à examiner et à examiner rapidement les messages avec des correspondances de stratégie. Le filtrage est disponible pour les éléments en attente et résolus pour chaque stratégie configurée. Vous pouvez configurer des requêtes de filtre pour une stratégie ou configurer et enregistrer des requêtes de filtre personnalisées et par défaut à utiliser dans chaque stratégie spécifique. Après avoir configuré les champs d’un filtre, vous verrez les champs de filtre affichés en haut de la file d’attente de messages d’alerte que vous pouvez configurer pour des valeurs de filtre spécifiques.

Pour obtenir la liste complète des filtres et des détails sur les champs, voir [filtres](communication-compliance-feature-reference.md#filters) dans la rubrique référence de la fonctionnalité.

#### <a name="to-configure-a-filter"></a>Pour configurer un filtre

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **conformité des communications**.

3. Sélectionnez l’onglet **stratégies** , puis sélectionnez une stratégie d’enquête, double-cliquez pour ouvrir la page **stratégie** .

4. Sur la page **stratégie** , sélectionnez l’onglet **en attente** ou **résolu** pour afficher les éléments à filtrer.

5. Sélectionnez le contrôle **filtres** pour ouvrir la page Détails du **filtre** .

6. Activez une ou plusieurs cases à cocher pour activer les filtres pour ces alertes. Vous pouvez choisir parmi de nombreux filtres, dont *Date*, *expéditeur*, *objet/titre*, *classifieurs*, etc.

7. Si vous souhaitez enregistrer le filtre sélectionné comme filtre par défaut, sélectionnez Enregistrer par **défaut**. Si vous souhaitez utiliser ce filtre en tant que filtre enregistré, sélectionnez **Terminer**.

8. Si vous souhaitez enregistrer les filtres sélectionnés en tant que requête de filtre, sélectionnez **enregistrer le contrôle de requête** après avoir configuré au moins une valeur de filtre. Entrez un nom pour la requête de filtre et sélectionnez **Enregistrer**. Ce filtre peut être utilisé uniquement pour cette stratégie et est mentionné dans la section **requêtes de filtrage enregistrées** de la page Détails des **filtres** .

    ![Contrôles des détails de filtrage de conformité des communications](../media/communication-compliance-filter-detail-controls.png)

### <a name="using-near-and-exact-duplicate-analysis"></a>Utilisation de l’analyse near et de la copie exacte

Les stratégies de conformité des communications analysent et regroupent automatiquement les doublons de messages proches et exactes sans aucune étape de configuration supplémentaire. Cet affichage vous permet de corriger rapidement les messages similaires, un par un ou en tant que groupe, réduisant ainsi la charge d’enquête de message pour les relecteurs. Lorsque des doublons sont détectés, les contrôles **des doublons et/** ou des doublons **exactes** s’affichent dans la barre d’outils action de correction. Cet affichage n’est pas disponible si les doublons proches ou exacts sont introuvables.

#### <a name="to-remediate-duplicates"></a>Pour corriger les doublons

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **conformité des communications**.

3. Sélectionnez l’onglet **stratégies** , puis sélectionnez une stratégie d’enquête, double-cliquez pour ouvrir la page **stratégie** .

4. Sur la page **stratégie** , sélectionnez l’onglet **en attente** ou **résolu** pour afficher les messages en double.

5. Sélectionnez les contrôles **proches des doublons** ou **copies exactes** pour ouvrir la page des détails des doublons.

6. Sélectionnez un ou plusieurs messages pour les contrôles d’action de correction pour ces messages.

7. Sélectionnez **résoudre**, **avertir**, **escalader**ou **Télécharger** pour appliquer l’action aux messages dupliqués sélectionnés comme filtre par défaut.

8. Sélectionnez **Fermer** après avoir terminé les actions de correction sur les messages.

    ![Contrôle des doublons exacts de la communication](../media/communication-compliance-duplicates-controls.png)

## <a name="remediate-alerts"></a>Correction des alertes

Quelle que soit l’endroit où vous commencez à examiner les alertes ou le filtrage que vous configurez, l’étape suivante consiste à prendre des mesures pour corriger l’alerte. Commencez votre correction d’alerte à l’aide du flux de travail suivant sur les pages de **stratégie** ou d' **alertes** :

1. **Examinez les notions de base sur les messages**: parfois, il est évident de la source ou de l’objet qu’un message peut être résolu immédiatement. Il se peut que le message soit un parasite ou une correspondance incorrecte avec une stratégie et qu’il doive être résolu comme faux positif. Sélectionnez le contrôle **faux positif** pour résoudre immédiatement l’alerte et supprimer de la file d’attente des alertes en attente. À partir de l’information source ou de l’expéditeur, vous savez peut-être déjà comment le message doit être routé ou géré dans ces circonstances. Envisagez d’utiliser la **balise** ou les contrôles pour affecter une balise aux messages **applicables ou pour** envoyer des messages à un réviseur désigné.

    ![Contrôles de correction de la conformité des communications](../media/communication-compliance-remediation-controls.png)

2. **Examinez les détails du message**: après avoir examiné les notions de base du message, il est temps d’ouvrir un message pour examiner les détails et pour déterminer d’autres actions de correction. Sélectionnez un message pour afficher l’en-tête et les informations de corps de message complètes. Plusieurs vues différentes sont disponibles pour vous aider à déterminer la bonne marche à suivre :

    - **Mode Source**: cet affichage est l’affichage de message standard généralement visible dans la plupart des plateformes de messagerie Web. Les informations d’en-tête sont mises en forme dans le style normal et le corps du message prend en charge les fichiers graphiques incorporés et le texte renvoyé à la ligne.
    - **Affichage**de texte : la vue de texte affiche un affichage de texte uniquement du message et inclut une mise en surbrillance de mots clés pour les termes correspondant à la stratégie de conformité de communication associée. La mise en surbrillance des mots clés peut vous aider à analyser rapidement les messages longs pour le domaine qui vous intéresse. Les fichiers incorporés ne sont pas affichés et la numérotation des lignes de cet affichage est utile pour référencer des détails pertinents entre plusieurs relecteurs.
    - **Annoted View**: cette vue permet aux relecteurs d’ajouter des annotations directement sur le message qui est enregistré dans l’affichage du message.
    - **Historique des utilisateurs**: affichage historique des utilisateurs affiche toutes les autres alertes générées par une stratégie de conformité de la communication pour l’utilisateur qui envoie le message.

    ![Contrôles d’affichage de message de conformité de communication](../media/communication-compliance-message-views.png)

3. **Choisir une action de correction**: à présent que vous avez examiné les détails du message pour l’alerte, vous pouvez choisir plusieurs actions de correction :

    - **Resolve**: la sélection du contrôle de **résolution** supprime immédiatement le message de la file d’attente des **alertes en attente** et aucune autre action ne peut être effectuée sur le message. En sélectionnant **résoudre**, vous avez essentiellement fermé l’alerte sans autre classification et elle ne peut pas être rouverte pour d’autres actions. Tous les messages résolus sont affichés sous l’onglet **résolu** .
    - **Faux positif**: vous pouvez toujours résoudre un message en tant que faux positif à tout moment pendant le flux de travail de révision des messages. Le message ne peut pas être rouvert et tous les faux positifs sont affichés sous l’onglet **résolu** .
    - **Balise comme**: balise le message comme étant *conforme*, *non conforme*ou comme étant *question* en relation avec les stratégies et les normes de votre organisation. L’ajout de balises et de commentaires de marquage peut vous aider à filtrer les alertes de stratégie pour les escalades ou dans d’autres processus de révision interne. Une fois le marquage terminé, vous pouvez également choisir de résoudre le message pour le déplacer de la file d’attente de révision en attente.
    - **Notifier**: vous pouvez utiliser le contrôle **Notify** pour affecter un modèle d’avertissement personnalisé à l’alerte et envoyer un avertissement à l’utilisateur. Choisissez le modèle d’avertissement approprié, puis sélectionnez **Envoyer pour envoyer** un rappel à l’employé qui a envoyé le message et résoudre le problème.
    - **Escalade**: à l’aide du contrôle d' **escalade** , vous pouvez choisir les autres personnes de votre organisation qui doivent consulter le message. Dans la liste des relecteurs configurés dans la stratégie de conformité des communications, effectuez une sélection dans une liste pour envoyer une notification par courrier électronique demandant une révision supplémentaire de l’alerte de message. Le réviseur sélectionné peut utiliser un lien dans la notification par courrier électronique pour accéder directement aux éléments qui y sont réaffectés à des fins de révision.
    - **Créer un cas**: à l’aide du contrôle **créer un cas** , vous pouvez créer un nouveau [cas eDiscovery avancé](overview-ediscovery-20.md) pour un ou plusieurs messages. Vous fournirez un nom et des remarques pour le nouvel incident, et l’utilisateur qui a envoyé le message correspondant à la stratégie est automatiquement affecté comme dépositaire de cas. Vous n’avez pas besoin d’autorisations supplémentaires pour gérer le cas. La création d’un cas ne permet pas de résoudre ou de créer une nouvelle balise pour le message.

4. **Déterminez si les détails du message doivent être archivés en dehors de la conformité de la communication**: les détails du message peuvent être exportés ou téléchargés si vous devez archiver les messages dans une solution de stockage distincte. La sélection du contrôle de **Téléchargement** ajoute automatiquement les messages sélectionnés à un. Fichier ZIP qui peut être enregistré en dehors de Microsoft 365.
