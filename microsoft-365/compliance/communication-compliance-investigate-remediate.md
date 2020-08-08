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
ms.openlocfilehash: 566ee3645fbb5b753269f82f5a43b07e06c4878d
ms.sourcegitcommit: 9550298946f8accb90cd59be7b46b71d4bf4f8cc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/08/2020
ms.locfileid: "46597478"
---
# <a name="investigate-and-remediate-communication-compliance-alerts"></a>Examiner et corriger les alertes de conformité des communications

Une fois que vous avez configuré vos stratégies de conformité de communication, vous commencerez à recevoir des alertes dans le centre de conformité Microsoft 365 pour les problèmes de message qui correspondent à vos conditions de stratégie. Suivez les instructions de flux de travail ici pour examiner et résoudre les problèmes d’alerte.

## <a name="investigate-alerts"></a>Analyser les alertes

La première étape pour examiner les problèmes détectés par vos stratégies consiste à passer en revue les alertes de conformité des communications dans le centre de conformité Microsoft 365. Il existe plusieurs domaines dans la section relative à la solution de conformité des communications pour vous aider à examiner rapidement les alertes, en fonction de la manière dont vous préférez afficher le regroupement des alertes :

- **Page de stratégie de conformité des communications**: lorsque vous vous connectez à à [https://compliance.microsoft.com](https://compliance.microsoft.com) l’aide des informations d’identification d’un compte d’administrateur de votre organisation Microsoft 365, sélectionnez **communication Compliance** pour afficher la page **stratégie** de conformité des communications. Cette page affiche des stratégies de conformité de communication configurées pour votre organisation Microsoft 365 et des liens vers des modèles de stratégie recommandés. Chaque stratégie indiquée inclut le nombre d’alertes qui nécessitent une révision, le nombre d’éléments remontés et résolus, ainsi que l’état actuel de la stratégie. La sélection d’une stratégie affiche toutes les alertes en attente pour les correspondances à la stratégie, une alerte spécifique pour lancer la page de détails de la stratégie et démarrer les actions de correction.
- **Alertes**: accédez à **Communication compliance**  >  **alertes** de conformité des communications pour afficher les 30 derniers jours des alertes regroupées par correspondances de stratégie. Cet affichage vous permet de voir rapidement les stratégies de conformité des communications qui génèrent la plupart des alertes classées par gravité. Pour démarrer les actions de correction, sélectionnez la stratégie associée à l’alerte pour lancer la page Détails de la **stratégie** . À partir de la page Détails de la **stratégie** , vous pouvez consulter un résumé des activités dans la page **vue d’ensemble** , vérifier et agir sur les messages d’alerte sur la page **en attente** , ou consulter l’historique des alertes fermées sur la page **résolu** .
- **Rapports**: accédez à rapports de **conformité des communications**  >  **Reports** pour afficher les widgets de rapport de conformité de communication. Chaque widget fournit une vue d’ensemble des activités et des États de conformité de la communication, y compris l’accès à des informations plus approfondies sur les correspondances de stratégie et les actions de correction.

### <a name="using-filters"></a>Utilisation de filtres

L’étape suivante consiste à trier les messages de sorte qu’il soit plus facile de rechercher des alertes. À partir de la page Détails de la **stratégie** , la conformité des communications prend en charge le filtrage multiniveau de plusieurs champs de message pour vous aider à examiner et à examiner rapidement les messages avec des correspondances de stratégie. Le filtrage est disponible pour les éléments en attente et résolus pour chaque stratégie configurée. Vous pouvez configurer des requêtes de filtrage pour une stratégie ou configurer et enregistrer des requêtes de filtrage personnalisées et par défaut à utiliser dans chaque stratégie spécifique. Une fois que vous avez configuré les champs d’un filtre, les champs de filtre affichés en haut de la file d’attente de messages d’alerte peuvent être configurés pour des valeurs de filtre spécifiques.

Pour obtenir la liste complète des filtres et des détails sur les champs, voir [Filters](communication-compliance-feature-reference.md#filters) dans l’article de référence de la fonctionnalité.

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

### <a name="using-near-and-exact-duplicate-analysis"></a>Utilisation de l’analyse de doublons proche et exacte

Les stratégies de conformité des communications analysent et pré-groupent automatiquement les doublons de messages proches et exacts sans étapes de configuration supplémentaires. Cet affichage vous permet d’agir rapidement sur des messages similaires un par un ou en tant que groupe, ce qui réduit la charge d’enquête de message pour les relecteurs. Au fur et à mesure que des doublons sont détectés, les contrôles **Doublons proches** et/ou les contrôles **Doublons exacts** sont affichés dans la barre d’outils action de correction. Cet affichage n’est pas disponible si les doublons proches ou exacts sont introuvables.

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

Quel que soit l’endroit où vous commencez à réviser les alertes ou le filtrage que vous configurez, l’étape suivante consiste à prendre des mesures pour résoudre le problème. Commencez votre correction d’alerte à l’aide du flux de travail suivant sur les pages de **stratégie** ou d' **alertes** :

1. **Examiner les concepts de base des messages** : il peut arriver qu’il s’agisse de la source ou de l’objet qu’un message peut être résolu immédiatement. Il se peut que le message soit un parasite ou une correspondance incorrecte avec une stratégie et qu’il doive être résolu comme faux positif. Sélectionnez le contrôle **Faux positif** pour résoudre immédiatement l’alerte et supprimer de la file d’attente d’alertes en cours. À partir de la source ou de l’expéditeur, vous savez peut-être déjà comment le message doit être routé ou géré dans ces circonstances. Envisagez d’utiliser les contrôles **Baliser comme** ou **Réaffectation** afin d’affecter une balise aux messages applicables ou d’envoyer des messages à un réviseur désigné.

    ![Contrôles de correction de la conformité des communications](../media/communication-compliance-remediation-controls.png)

2. **Consultez les détails du message** : une fois que vous avez révisé les concepts de base des messages, il est temps d’ouvrir un message pour examiner les détails et déterminer d’autres actions correctives. Sélectionnez un message pour afficher l’ensemble des informations d’en-tête et de corps du message. Plusieurs affichages sont disponibles pour vous aider à déterminer la bonne marche à suivre :

    - **Mode Source** : cet mode est l’affichage des messages standard couramment consulté dans la plupart des plateformes de messagerie web. Les informations d’en-tête sont mises en forme dans le style normal et le corps du message prend en charge les fichiers graphiques incorporés et le texte renvoyé à la ligne.
    - **Mode texte** : le mode texte affiche un affichage de texte numéroté par une ligne uniquement du message et inclut une mise en surbrillance des mots clés pour les termes correspondants dans la stratégie de conformité des communications associée. La mise en surbrillance des mots clés vous permet d’analyser rapidement les longs messages pour le domaine qui vous intéresse. Les fichiers incorporés ne sont pas affichés et la numérotation des lignes de cet affichage est utile pour référencer des détails pertinents entre plusieurs relecteurs.
    - **Mode annoter** : cet mode permet aux réviseurs d’ajouter des annotations directement sur le message qui sont enregistrées dans l’affichage du message.
    - **Historique des utilisateurs** : le mode historique des utilisateurs affiche toutes les autres alertes générées par une stratégie de conformité des communications pour l’utilisateur qui envoie le message.
    - **Affichage détaillé des messages**: Affichage avancé des métadonnées et des informations de configuration des messages.
    - **Notification de modèle de notification (** préversion) : de nombreuses actions de harcèlement et de intimidation dans le temps et impliquent la récurrence d’instances du même comportement par un utilisateur. La notification de *modèle détecté* apparaît dans les détails de l’alerte et attire l’attention sur l’alerte. La détection des modèles est basée sur une stratégie et évalue le comportement au cours des 30 derniers jours lorsqu’au moins deux messages sont envoyés au même destinataire par un expéditeur. Les enquêteurs et les relecteurs peuvent utiliser cette notification pour identifier les comportements répétés afin d’évaluer l’alerte comme il convient.

    ![Contrôles d’affichage de message de conformité de communication](../media/communication-compliance-message-views.png)

3. **Choisir une action de correction**: à présent que vous avez examiné les détails du message pour l’alerte, vous pouvez choisir plusieurs actions de correction :

    - **Resolve**: la sélection du contrôle de **résolution** supprime immédiatement le message de la file d’attente des **alertes en attente** et aucune autre action ne peut être effectuée sur le message. En sélectionnant **résoudre**, vous avez essentiellement fermé l’alerte sans autre classification et elle ne peut pas être rouverte pour d’autres actions. Tous les messages résolus sont affichés sous l’onglet **résolu** .
    - **Faux positif**: vous pouvez toujours résoudre un message en tant que faux positif à tout moment pendant le flux de travail de révision des messages. Faux positif signifie que l’alerte n’était pas actionnable ou que l’alerte a été générée de manière incorrecte par le processus d’alerte. Le message ne peut pas être rouvert et tous les faux positifs sont affichés sous l’onglet **résolu** .
    - **Balise comme**: balise le message comme étant *conforme*, *non conforme*ou comme étant *question* en relation avec les stratégies et les normes de votre organisation. L’ajout de balises et de commentaires de marquage vous permet de microfiltrer les alertes de stratégie pour les escalades ou dans d’autres processus de révision interne. Une fois le marquage terminé, vous pouvez également choisir de résoudre le message pour le déplacer de la file d’attente de révision en attente.
    - **Notifier**: vous pouvez utiliser le contrôle **Notify** pour affecter un modèle d’avertissement personnalisé à l’alerte et envoyer un avertissement à l’utilisateur. Choisissez le modèle d’avertissement approprié configuré dans la zone **paramètres de conformité des communications** et sélectionnez Envoyer pour **Envoyer** un rappel à l’utilisateur qui a envoyé le message et résoudre le problème.
    - **Escalade**: à l’aide du contrôle d' **escalade** , vous pouvez choisir les autres personnes de votre organisation qui doivent consulter le message. Dans la liste des relecteurs configurés dans la stratégie de conformité des communications, effectuez une sélection dans une liste pour envoyer une notification par courrier électronique demandant une révision supplémentaire de l’alerte de message. Le réviseur sélectionné peut utiliser un lien figurant dans la notification par courrier électronique pour accéder directement aux éléments qui y sont réaffectés pour révision.
    - **Escalade pour l’enquête**: en utilisant le contrôle **d’enquête escalade** , vous pouvez créer un nouveau [cas eDiscovery avancé](overview-ediscovery-20.md) pour un ou plusieurs messages. Vous fournirez un nom et des remarques pour le nouvel incident, et l’utilisateur qui a envoyé le message correspondant à la stratégie est automatiquement affecté comme dépositaire de cas. Vous n’avez pas besoin d’autorisations supplémentaires pour gérer le cas. La création d’un cas ne permet pas de résoudre ou de créer une nouvelle balise pour le message. Vous pouvez sélectionner un total de 100 messages lors de la création d’un cas avancé eDiscovery lors du processus de correction. Les messages de tous les canaux de communication surveillés par la conformité des communications sont pris en charge. Par exemple, vous pouvez sélectionner 50 conversations Microsoft Teams, 25 messages électroniques Exchange Online et 25 messages Yammer lorsque vous ouvrez un nouveau cas de découverte électronique avancée pour un utilisateur.
    - **Supprimer un message dans Teams (aperçu)**: en utilisant le contrôle **supprimer le message dans teams** , vous pouvez bloquer les messages et le contenu inappropriés identifiés dans les alertes des canaux Microsoft teams et 1:1 et des conversations de groupe. Les messages supprimés et le contenu sont remplacés par un Conseil de stratégie qui explique qu’il est bloqué et la stratégie qui s’applique à sa suppression de l’affichage. Les destinataires disposent d’un lien dans le Conseil de stratégie pour en savoir plus sur la stratégie applicable et le processus de révision. L’expéditeur reçoit un Conseil de stratégie pour le message et le contenu bloqués, mais il peut consulter les détails du message et du contenu bloqués pour le contexte concernant la suppression.

    ![Supprimer un message de Microsoft teams](../media/communication-compliance-remove-teams-message.png)

4. **Déterminer si les détails des messages doivent être archivés en dehors de la conformité des communications**: les détails des messages peuvent être exportés ou téléchargés si vous avez besoin d’archiver les messages dans une solution de stockage distincte. La sélection du contrôle **Télécharger** ajoute automatiquement les messages sélectionnés à un fichier .ZIP qui peut être sauvegardé en dehors de Microsoft 365.
