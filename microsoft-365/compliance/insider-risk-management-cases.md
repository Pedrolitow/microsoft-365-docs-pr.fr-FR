---
title: Cas de gestion des risques internes
description: En savoir plus sur les cas de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 55373830a351bc3bad40a4a492101c5ac011d8b0
ms.sourcegitcommit: dd4214a309c71292490743752da728cec7bffe88
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/22/2021
ms.locfileid: "59479524"
---
# <a name="insider-risk-management-cases"></a>Cas de gestion des risques internes

Les cas sont au cœur de la gestion des risques internes et vous permettent d’examiner et d’agir en profondeur sur les problèmes générés par les indicateurs de risque définis dans vos stratégies. Les cas sont créés manuellement à partir d’alertes dans les situations où des mesures supplémentaires sont nécessaires pour résoudre un problème de conformité pour un utilisateur. Chaque cas est étendue à un seul utilisateur et plusieurs alertes de l’utilisateur peuvent être ajoutées à un cas existant ou à un nouveau cas.

Après avoir ouvert une enquête sur les détails d’un cas, vous pouvez prendre des mesures en :

- envoi d’un avis à l’utilisateur
- résolution du cas comme étant anodin
- partage du cas avec votre instance ServiceNow ou avec un destinataire de courrier électronique
- escalade du cas pour une enquête Advanced eDiscovery de recherche

Consultez la vidéo [Examen](https://www.youtube.com/watch?v=UONUSmkRC8s) et escalade de gestion des risques internes pour obtenir une vue d’ensemble de la façon dont les cas sont examinés et gérés dans la gestion des risques internes.

## <a name="cases-dashboard"></a>Tableau de bord Cas

Le tableau de bord Cas **de** gestion des risques internes vous permet d’afficher les cas et d’agir sur ces cas. Chaque widget de rapport sur le tableau de bord affiche des informations pour les 30 derniers jours.

- **Cas actifs**: nombre total de cas actifs en cours d’examen.
- **Cas au cours des 30 derniers** jours : nombre total de cas créés, triés par *état Actif* *et* Fermé.
- **Statistiques**: durée moyenne des cas actifs, répertoriée en heures, jours ou mois.

La file d’attente répertorie tous les cas actifs et fermés pour votre organisation, en plus de l’état actuel des attributs de cas suivants :

- **Nom de** cas : nom du cas, défini lorsqu’une alerte est confirmée et que le cas est créé.  
- **État**: l’état du cas, *actif* ou *fermé*.
- **Utilisateur**: utilisateur du cas. Si l’anonymisation des noms d’utilisateur est activée, les informations anonymisées s’affichent.
- **Cas d’heure ouvert**: temps écoulé depuis l’ouverture du cas.
- **Nombre total d’alertes de** stratégie : nombre de correspondances de stratégie incluses dans le cas. Ce nombre peut augmenter si de nouvelles alertes sont ajoutées au cas.
- **Dernière mise à jour du** cas : le temps écoulé depuis l’ajout d’une note de cas ou d’une modification dans l’état du cas.
- **Last updated by**: The name of the insider risk management analyst or investigator that last updated the case.

![Tableau de bord Cas de gestion des risques internes.](../media/insider-risk-cases-dashboard.png)

Utilisez le contrôle **de** recherche pour rechercher des noms de cas pour du texte spécifique et utiliser le filtre de cas pour trier les cas selon les attributs suivants :

- Statut
- Heure d'ouverture du cas, date de début et la date de fin
- Dernière mise à jour, date de début et la date de fin

## <a name="filter-cases"></a>Filtrer des cas

Selon le nombre et le type de stratégies actives de gestion des risques internes dans votre organisation, l’examen d’une file d’attente de cas importante peut être difficile. L’utilisation de filtres de cas permet aux analystes et aux enquêteurs de trier les cas par plusieurs attributs. Pour filtrer les alertes dans le tableau de bord **Cas,** sélectionnez **le contrôle** Filtre. Vous pouvez filtrer les cas par un ou plusieurs attributs :

- **État**: sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste des cas. Les options sont *Active* et *Closed*.
- **Cas d’heure ouvert**: sélectionnez les dates de début et de fin de l’ouverture du cas.
- **Dernière mise à jour**: sélectionnez les dates de début et de fin de la mise à jour du cas.

## <a name="investigate-a-case"></a>Examiner un cas

Un examen plus approfondi des alertes de gestion des risques internes est essentiel pour prendre des mesures correctives appropriées. Les cas de gestion des risques internes sont l’outil central de gestion permettant d’approfondir l’historique des activités des risques utilisateur, les détails des alertes, la séquence des événements de risque et d’explorer le contenu et les messages exposés aux risques. Les analystes et enquêteurs de risque utilisent également des cas pour centraliser les commentaires et les notes de révision et pour traiter la résolution des cas.

La sélection d’un cas ouvre les outils de gestion des cas et permet aux analystes et aux enquêteurs d’approfondir les détails des cas.

### <a name="case-overview"></a>Présentation du cas

**L’onglet Vue d’ensemble** des cas récapitule les détails des cas pour les analystes et enquêteurs de risque. Il inclut les informations suivantes dans la **zone à propos de ce** cas

- **État**: état actuel du cas, actif ou fermé.
- **Cas créé le :** date et heure de création du cas.
- **Score de risque de l’utilisateur**: niveau de risque calculé actuel de l’utilisateur pour le cas. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur.
- **Email**: alias de messagerie de l’utilisateur pour le cas.
- **Organisation ou service :** organisation ou service à qui l’utilisateur est affecté.
- **Nom du responsable**: nom du responsable de l’utilisateur.
- **E-mail du** responsable : alias de messagerie du responsable de l’utilisateur.

![Détails du cas de gestion des risques internes.](../media/insider-risk-case-details.png)

**L’onglet Vue d’ensemble** du cas inclut également une section Alertes qui inclut les informations **suivantes** sur les alertes de correspondance de stratégie associées au cas :

- **Correspondances de stratégie :** nom de la stratégie de gestion des risques internes associée aux alertes de correspondance pour l’activité de l’utilisateur.
- **État**: état de l’alerte.
- **Gravité :** gravité de l’alerte.
- **Heure détectée :** temps écoulé depuis la généré de l’alerte.

### <a name="alerts"></a>Alertes

**L’onglet** Alertes récapitule les alertes actuelles incluses dans le cas. De nouvelles alertes peuvent être ajoutées à un cas  existant et elles sont ajoutées à la file d’attente des alertes à mesure qu’elles sont affectées. Les attributs d’alerte suivants sont répertoriés dans la file d’attente :

- Statut
- Severity
- Heure détectée

Sélectionnez une alerte dans la file d’attente pour afficher la page **détails de l’alerte.**

Utilisez le contrôle de recherche pour rechercher des noms d’alertes pour un texte spécifique et utilisez le filtre d’alerte pour trier les cas selon les attributs suivants :

- Statut
- Severity
- Heure détectée, la date de début et la date de fin

Utilisez le contrôle de filtre pour filtrer les alertes par plusieurs attributs, notamment :

- **État**: sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste d’alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise* et *Résolu*.
- **Gravité : sélectionnez** un ou plusieurs niveaux de gravité des risques d’alerte pour filtrer la liste d’alertes. Les options disponibles sont *Élevée*, *Moyenne* et *Faible*.
- **Heure détectée :** sélectionnez les dates de début et de fin de la création de l’alerte.
- **Stratégie**: sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

### <a name="user-activity"></a>Activité utilisateur

L’onglet **Activité des utilisateurs** est l’un des outils les plus performants pour l’analyse des risques internes et l’examen pour les cas de la solution de gestion des risques internes. Cet onglet est structuré pour permettre un examen rapide d’un cas, y compris une chronologie historique de toutes les alertes, les détails de l’alerte, le score de risque actuel pour l’utilisateur dans le cas, la séquence d’événements de risque et les contrôles pour prendre des mesures efficaces pour contenir les risques dans le cas.

![Activité des utilisateurs de gestion des risques internes.](../media/insider-risk-user-activities.png)

1. **Filtres de** temps : par défaut, les six derniers mois d’alertes confirmées dans le cas sont affichés dans le graphique d’activité de l’utilisateur. Vous pouvez facilement filtrer l’affichage graphique en sélectionnant les onglets *6 mois,* *3* mois ou *1* mois sur le graphique en bulles.
2. **Activité et détails** des alertes de risque : les activités de risque sont affichées visuellement sous forme de bulles de couleur dans le graphique d’activité de l’utilisateur. Les bulles sont créées pour différentes catégories de risque et la taille des bulles est proportionnelle au nombre d’activités de risque pour la catégorie. Sélectionnez une bulle pour afficher les détails de chaque activité de risque. Les détails sont les suivants :
    - **Date** de l’activité de risque.
    - Catégorie **d’activité de risque.** Par exemple, *e-mail(s) avec* des pièces jointes envoyées à l’extérieur de l’organisation ou fichiers *téléchargés* à partir de SharePoint Online .
    - **Score de risque** pour l’alerte. Ce score correspond au score numérique du niveau de gravité des risques d’alerte.
    - Nombre d’événements associés à l’alerte. Des liens vers chaque fichier ou e-mail associé à l’activité de risque sont également disponibles.
3. **Séquence de risques (aperçu)**: l’ordre chronologique des activités risquées est un aspect important de l’examen des risques et l’identification de ces activités connexes est un élément important de l’évaluation du risque global pour votre organisation. Les activités d’alerte associées sont affichées avec des lignes de connexion pour souligner que ces activités sont associées à une zone de risque plus importante. Cette vue des activités peut aider les enquêteurs à « connecter les points » pour les activités à risque qui auraient pu être vues comme des événements isolés ou isolés. Sélectionnez n’importe quelle bulle dans l’ordre pour afficher les détails de toutes les activités de risque associées. Les détails sont les suivants :

    - **Nom** de la séquence.
    - **Plage de** **dates ou de** dates de la séquence.
    - **Score de risque** pour la séquence. Ce score est le score numérique pour la séquence des niveaux de gravité de risque d’alerte combinés pour chaque activité associée dans la séquence.
    - **Nombre d’événements associés à chaque alerte dans la séquence.** Des liens vers chaque fichier ou e-mail associé à chaque activité de risque sont également disponibles.
    - **Afficher les activités dans l’ordre.** Affiche la séquence sous la forme d’une ligne de surbrillon sur le graphique en bulles et développe les détails de l’alerte pour afficher toutes les alertes associées dans la séquence.

4. **Légende de l’activité de** risque : en bas du graphique d’activité de l’utilisateur, une légende codée en couleur vous permet de déterminer rapidement la catégorie de risque pour chaque alerte.
5. **Chronologie des** activités de risque : la chronologie complète de toutes les alertes de risque associées au cas sont répertoriées, y compris tous les détails disponibles dans la bulle d’alerte correspondante.
6. **Actions de cas**: les options de résolution du cas sont disponibles dans la barre d’outils de l’action de cas. Vous pouvez résoudre un cas, envoyer une notification par courrier électronique à l’utilisateur ou faire réamorcer le cas d’un examen de données ou d’un utilisateur.

### <a name="activity-explorer-preview"></a>Explorateur d’activités (aperçu)

> [!IMPORTANT]
> L’onglet Explorateur d’activités est disponible dans la zone de gestion des cas pour les utilisateurs ayant déclenché des événements une fois que cette fonctionnalité est disponible dans votre organisation.

**L’onglet Explorateur d’activités** permet aux analystes et aux enquêteurs de risques d’examiner les détails de l’activité associés aux alertes de risque. Par exemple, dans le cadre des actions de gestion des cas, les enquêteurs et les analystes peuvent avoir besoin de passer en revue toutes les activités de risque associées au cas pour plus de détails. Avec **l’Explorateur d’activités,** les réviseurs peuvent rapidement passer en revue une chronologie des activités à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes.

Pour plus d’informations sur l’Explorateur d’activités, consultez l’article sur les [alertes de gestion des risques internes.](insider-risk-management-activities.md#activity-explorer)

### <a name="content-explorer"></a>Explorateur de contenu

**L’onglet Explorateur de** contenu permet aux enquêteurs de risque d’examiner les copies de tous les fichiers et messages électroniques associés aux alertes de risque. Par exemple, si une alerte est créée lorsqu’un utilisateur télécharge des centaines de fichiers à partir de SharePoint Online et que l’activité déclenche une alerte de stratégie, tous les fichiers téléchargés pour l’alerte sont capturés et copiés dans le cas de gestion des risques internes à partir des sources de stockage d’origine.

L’Explorateur de contenu est un outil puissant avec des fonctionnalités de recherche et de filtrage de base et avancées. Pour en savoir plus sur l’utilisation de l’Explorateur de contenu, voir [l’Explorateur](insider-risk-management-content-explorer.md)de contenu de gestion des risques internes.

![Explorateur de contenu de cas de gestion des risques internes.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Notes sur le cas

**L’onglet Notes** de cas dans le cas où les analystes et enquêteurs de risque partagent des commentaires, des commentaires et des informations sur leur travail pour le cas. Les notes sont des ajouts permanents à un cas et ne peuvent pas être modifiées ou supprimées une fois la note enregistrée. Lors de la création d’un cas à partir d’une alerte, les commentaires entrés dans la boîte de dialogue **Confirmer l’alerte et créer un cas de risque internes** sont automatiquement ajoutés comme note de cas.

Le tableau de bord des notes de cas affiche les notes de l’utilisateur qui a créé la note et le temps écoulé depuis l’enregistré. Pour rechercher un mot clé spécifique dans  le champ de texte de note de cas, utilisez le bouton Rechercher dans le tableau de bord de cas et entrez un mot clé spécifique.

Pour ajouter une note à un cas :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **Gestion** des risques internes et sélectionnez **l’onglet Cas.**
2. Sélectionnez un cas, puis **l’onglet Notes** de cas.
3. Sélectionnez **Ajouter une note de cas.**
4. Dans la **boîte de dialogue Ajouter une note** de cas, tapez votre note pour le cas. Sélectionnez **Enregistrer** pour ajouter la note au cas ou **sélectionnez Annuler** fermer sans enregistrer la note dans le cas.

### <a name="contributors"></a>Contributeurs

L’onglet **Contributeurs** dans le cas est l’endroit où les analystes et les enquêteurs peuvent ajouter d’autres réviseurs au cas. Par défaut, tous  les utilisateurs affectés aux analystes de gestion des risques internes et aux enquêteurs de gestion des risques internes sont **répertoriés** en tant que contributeurs pour chaque cas actif et fermé. Seuls les **utilisateurs affectés au** rôle Enquêteurs de gestion des risques internes sont autorisés à afficher des fichiers et des messages dans l’Explorateur de contenu.

L’accès temporaire à un cas peut être accordé en ajoutant un utilisateur en tant que collaborateur. Les collaborateurs ont tout le contrôle de gestion des cas sur le cas spécifique, sauf :

- Autorisation de confirmer ou d’ignorer les alertes
- Autorisation de modifier les contributeurs pour les cas
- Autorisation d’afficher des fichiers et des messages dans l’Explorateur de contenu

Pour ajouter un collaborateur à un cas :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **Gestion** des risques internes et sélectionnez **l’onglet Cas.**
2. Sélectionnez un cas, puis **l’onglet Collaborateurs.**
3. Sélectionnez **Ajouter un collaborateur.**
4. Dans la **boîte de dialogue** Ajouter un collaborateur, commencez à taper le nom de l’utilisateur que vous souhaitez ajouter, puis sélectionnez l’utilisateur dans la liste d’utilisateurs suggérée. Cette liste est générée à partir de la Azure Active Directory de votre abonnement client.
5. Sélectionnez **Ajouter** pour ajouter l’utilisateur en tant que collaborateur ou sélectionnez **Annuler** fermer la boîte de dialogue sans ajouter l’utilisateur en tant que collaborateur.

## <a name="case-actions"></a>Actions de cas

Les enquêteurs des risques peuvent agir sur un cas dans l’une des méthodes suivantes, en fonction de la gravité du cas, de l’historique des risques de l’utilisateur et des recommandations en matière de risques de votre organisation. Dans certains cas, vous devrez peut-être transformer un cas en examen d’utilisateur ou de données pour collaborer avec d’autres zones de votre organisation et approfondir les activités à risque. La gestion des risques internes est étroitement intégrée aux autres solutions de conformité Microsoft 365 pour vous aider à gérer la résolution de bout en bout.

### <a name="send-email-notice"></a>Envoyer une notification par courrier électronique

Dans la plupart des cas, les actions de l’utilisateur qui créent des alertes de risque internes sont accidentelles ou accidentelles. L’envoi d’une notification de rappel à l’utilisateur par courrier électronique est une méthode efficace pour documenter la révision et l’action des cas, et permet de rappeler aux utilisateurs les stratégies d’entreprise ou de les faire pointer vers une formation d’actualisation. Les avis sont générés à partir de [modèles d’avis](insider-risk-management-notices.md) que vous créez pour votre infrastructure de gestion des risques internes.

Il est important de se souvenir que l’envoi d’une notification par courrier électronique à un utilisateur ***** ne résout pas le cas comme _Closed*. Dans certains cas, vous pouvez laisser un cas ouvert après avoir envoyé une notification à un utilisateur pour rechercher d’autres activités à risque sans ouvrir de nouveau cas. Si vous voulez résoudre un cas après l’envoi d’une notification, vous devez sélectionner le **Résoudre un cas** sous la forme d’une étape de suivi après l’envoi d’une notification.

Pour envoyer une notification à l’utilisateur affecté à un cas :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **Gestion** des risques internes et sélectionnez **l’onglet Cas.**
2. Sélectionnez un cas, puis sélectionnez le bouton Envoyer une notification par **courrier** électronique dans la barre d’outils de l’action de cas.
3. Dans la boîte de dialogue Envoyer  un **avis** par courrier électronique, sélectionnez le contrôle de liste de listes des modèles d’avis pour sélectionner le modèle d’avis pour l’avis. Cette sélection pré-remplit les autres champs de l’avis.
4. Examinez les champs d’avis et mettez à jour le cas échéant. Les valeurs entrées ici remplacent les valeurs du modèle.
5. Sélectionnez **Envoyer** pour envoyer l’avis à l’utilisateur ou **sélectionnez Annuler** fermer la boîte de dialogue sans envoyer l’avis à l’utilisateur. Toutes les notifications envoyées sont ajoutées à la file d’attente des notes de cas dans le tableau **de bord des notes de** cas.

### <a name="escalate-for-investigation"></a>Faire remonter le dossier pour enquête

Faire passer le cas pour l’examen de l’utilisateur dans les situations où un examen juridique supplémentaire est nécessaire pour l’activité de risque de l’utilisateur. Cette remontée ouvre un nouveau dossier Advanced eDiscovery dans votre organisation Microsoft 365. Advanced eDiscovery offre un flux de travail de bout en bout pour conserver, collecter, réviser, analyser et exporter du contenu réactif aux examens juridiques internes et externes de votre organisation. Il permet également à votre équipe juridique de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les conservateurs impliqués dans un cas. L’affectation d’un réviseur en tant que consignataire dans un cas Advanced eDiscovery créé à partir d’un cas de gestion des risques internes permet à votre équipe juridique de prendre les mesures appropriées et de gérer la conservation du contenu. Pour en savoir plus sur les cas Advanced eDiscovery, consultez [Présentation de Advanced eDiscovery dans Microsoft 365](overview-ediscovery-20.md).

Pour faire recaler un cas à un examen par un utilisateur :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **Gestion** des risques internes et sélectionnez **l’onglet Cas.**
2. Sélectionnez un cas, puis sélectionnez le bouton Escalader pour **l’examen** dans la barre d’outils d’action de cas.
3. Dans la **boîte de dialogue Escalader pour l’examen,** entrez un nom pour le nouvel examen utilisateur. Si nécessaire, entrez des notes sur le cas et sélectionnez **Escalate**.
4. Examinez les champs d’avis et mettez à jour le cas échéant. Les valeurs entrées ici remplacent les valeurs du modèle.
5. Sélectionnez **Confirmer** pour créer le cas d’enquête de l’utilisateur ou **sélectionnez Annuler** pour fermer la boîte de dialogue sans créer de nouveau cas d’enquête utilisateur.

Une fois que le cas de gestion des risques internes a été réamorcer vers un nouveau cas d’examen utilisateur, vous pouvez passer en revue le nouveau cas dans la zone **eDiscovery** avancée du  >   Centre de conformité Microsoft 365.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Exécuter des tâches automatisées avec Power Automate flux pour le cas

À l’aide des flux Power Automate recommandés, les enquêteurs de risque et les analystes peuvent rapidement prendre des mesures pour :

- Demander des informations rh ou professionnelles sur un utilisateur dans un cas de risque interne
- Avertir le responsable lorsqu’un utilisateur a une alerte de risque interne
- Créer un enregistrement pour un cas de gestion des risques internes dans ServiceNow
- Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne

Pour exécuter, gérer ou créer des flux Power Automate pour un cas de gestion des risques internes :

1. Sélectionnez **Automatiser dans la** barre d’outils de l’action de cas. 
2. Choisissez le flux Power Automate à exécuter, puis sélectionnez **Exécuter le flux.** 
3. Une fois le flux terminé, sélectionnez **Terminé.**

Pour en savoir plus sur les Power Automate pour la gestion des risques internes, voir Prise en charge des paramètres de [gestion des risques internes.](insider-risk-management-settings.md#power-automate-flows-preview)

### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Afficher ou créer une équipe Microsoft Teams pour le cas

Lorsque Microsoft Teams pour la gestion des risques internes est activée dans les paramètres, une équipe Microsoft Teams est automatiquement créée chaque fois qu’une alerte est confirmée et qu’un cas est créé. Les enquêteurs des risques et les analystes peuvent rapidement ouvrir Microsoft Teams et accéder directement à l’équipe pour un cas en sélectionnant Afficher l’équipe **Microsoft Teams** dans la barre d’outils d’action du cas.

Pour les cas ouverts avant d’activer l’intégration de Microsoft Team, les enquêteurs de risque et les analystes peuvent créer une équipe Microsoft Teams pour un cas en sélectionnant Créer une équipe **Microsoft Teams** dans la barre d’outils de l’action de cas.

Lorsqu’un cas est résolu, l’équipe Microsoft associée est automatiquement archivée (masquée et en lecture seule).

Pour en savoir plus sur les Microsoft Teams gestion des risques internes, voir Prise en charge des paramètres de [gestion des risques internes.](insider-risk-management-settings.md#microsoft-teams-preview)

### <a name="resolve-the-case"></a>Résoudre le dossier

Une fois que les analystes et enquêteurs de risque ont terminé leur examen et leur examen, un cas peut être résolu pour agir sur toutes les alertes actuellement incluses dans le cas. La résolution d’un cas ajoute une classification de résolution, modifie l’état du cas sur *Fermé* et les raisons de l’action de résolution sont automatiquement ajoutées à la file d’attente des notes de cas dans le tableau de bord des **notes** de cas. Les cas sont résolus comme suit :

- **Non** anodin : classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme étant à faible risque, non graves ou faux positifs.
- **Violation de stratégie** confirmée : classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme risquées, graves ou le résultat d’une intention malveillante.

Pour résoudre un cas :

1. Dans la [Centre de conformité Microsoft 365,](https://compliance.microsoft.com)allez à **Gestion** des risques internes et sélectionnez **l’onglet Cas.**
2. Sélectionnez un cas, puis sélectionnez le **bouton Résoudre** le cas dans la barre d’outils d’action de cas.
3. Dans la **boîte de dialogue Résoudre le cas,** sélectionnez **résoudre** en tant que contrôle de la boîte de dialogue pour sélectionner la classification de résolution pour le cas. Les options possibles sont une violation **de** la stratégie anodin **ou confirmée.**
4. Dans la **boîte de dialogue Résoudre le cas,** entrez les raisons de la classification de résolution dans le champ de texte **Action** prise.
5. Sélectionnez **Résoudre** pour fermer le cas ou **annuler** la boîte de dialogue sans résoudre le cas.
