---
title: Cas de gestion des risques internes
description: En savoir plus sur les cas de gestion des risques internes dans Microsoft Purview
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- tier1
- purview-compliance
ms.custom: admindeeplinkCOMPLIANCE
ms.openlocfilehash: 77fab460187f1935c016e691937af91d014929a2
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68734844"
---
# <a name="insider-risk-management-cases"></a>Cas de gestion des risques internes

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Les cas sont au cœur de la gestion des risques internes et vous permettent d’examiner et d’agir en profondeur sur les problèmes générés par les indicateurs de risque définis dans vos stratégies. Les cas sont créés manuellement à partir d’alertes dans les situations où une action supplémentaire est nécessaire pour résoudre un problème lié à la conformité pour un utilisateur. Chaque cas est limité à un seul utilisateur et plusieurs alertes pour l’utilisateur peuvent être ajoutées à un cas existant ou à un nouveau cas.

Après avoir examiné les détails d’un cas, vous pouvez prendre les mesures suivantes :

- Envoi d’une notification à l’utilisateur
- Résolution du cas comme étant sans gravité
- Partage du cas avec votre instance ServiceNow ou avec un destinataire de l’e-mail
- Escalade du cas pour une enquête eDiscovery (Premium)

Regardez la [vidéo Investigation et escalade des risques internes](https://www.youtube.com/watch?v=UONUSmkRC8s) pour une vue d’ensemble de la façon dont les cas sont examinés et gérés dans la gestion des risques internes.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="cases-dashboard"></a>Tableau de bord des cas

Le **tableau de bord Cas** de gestion des risques internes vous permet d’afficher et d’agir sur les cas. Chaque widget de rapport sur le tableau de bord affiche des informations pour les 30 derniers jours.

- **Cas actifs** : nombre total de cas actifs en cours d’investigation.
- **Cas au cours des 30 derniers jours** : nombre total de cas créés, triés par état *Actif* et *Fermé* .
- **Statistiques** : durée moyenne des cas actifs, exprimée en heures, en jours ou en mois.

La file d’attente des cas répertorie tous les cas actifs et fermés pour votre organisation, en plus de l’état actuel des attributs de cas suivants :

- **Nom** du cas : nom du cas, défini lorsqu’une alerte est confirmée et que le cas est créé.  
- **État** : état du cas, *Actif* ou *Fermé*.
- **Utilisateur** : l’utilisateur pour le cas. Si l’anonymisation des noms d’utilisateur est activée, les informations anonymisées s’affichent.
- **Heure d’ouverture** : délai écoulé depuis l’ouverture de l’affaire.
- **Nombre total d’alertes de stratégie** : nombre de correspondances de stratégie incluses dans le cas. Ce nombre peut augmenter si de nouvelles alertes sont ajoutées au cas.
- **Dernière mise à jour du cas** : le temps écoulé depuis l’ajout d’une note de cas ou d’une modification dans l’état du cas.
- **Dernière mise à jour par** : nom de l’analyste ou de l’enquêteur en gestion des risques internes qui a mis à jour le cas pour la dernière fois.

![Tableau de bord des cas de gestion des risques internes.](../media/insider-risk-cases-dashboard.png)

Utilisez le contrôle **De recherche** pour rechercher des noms de cas pour un texte spécifique et utilisez le filtre de cas pour trier les cas selon les attributs suivants :

- État
- Heure d'ouverture du cas, date de début et la date de fin
- Dernière mise à jour, date de début et la date de fin

## <a name="filter-cases"></a>Filtrer les cas

Selon le nombre et le type de stratégies de gestion des risques internes actives dans votre organisation, l’examen d’une file d’attente importante de cas peut être difficile. L’utilisation de filtres de cas peut aider les analystes et les enquêteurs à trier les cas selon plusieurs attributs. Pour filtrer les alertes dans le **tableau de bord Cas**, sélectionnez le contrôle **Filtrer** . Vous pouvez filtrer les cas par un ou plusieurs attributs :

- **État** : sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste des cas. Les options sont *Actif* et *Fermé*.
- **Heure d’ouverture du cas** : sélectionnez les dates de début et de fin de l’ouverture du cas.
- **Dernière mise à jour** : sélectionnez les dates de début et de fin de la mise à jour du cas.

## <a name="investigate-a-case"></a>Examiner un cas

Une investigation plus approfondie des alertes de gestion des risques internes est essentielle pour prendre les mesures correctives appropriées. Les cas de gestion des risques internes sont l’outil de gestion central qui permet d’approfondir l’historique des activités à risque des utilisateurs, les détails des alertes, la séquence des événements à risque et d’explorer le contenu et les messages exposés aux risques. Les analystes des risques et les enquêteurs utilisent également des cas pour centraliser les commentaires et les notes de révision et pour traiter la résolution des cas.

La sélection d’un cas ouvre les outils de gestion des cas et permet aux analystes et aux enquêteurs d’approfondir les détails des cas.

### <a name="case-overview"></a>Présentation du cas

L’onglet **Vue d’ensemble** des cas résume les détails du cas pour les analystes des risques et les enquêteurs. Il inclut les informations suivantes dans la zone **À propos de ce cas**

- **État** : état actuel du cas, Actif ou Fermé.
- **Case created on** : date et heure de création du cas.
- **Score de risque de l’utilisateur** : niveau de risque calculé actuel de l’utilisateur pour le cas. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur.
- **Email** : alias d’e-mail de l’utilisateur pour le cas.
- **Organisation ou service** : organisation ou service auquel l’utilisateur est affecté.
- **Nom du gestionnaire** : nom du responsable de l’utilisateur.
- **Adresse e-mail du responsable** : alias d’e-mail du responsable de l’utilisateur.

![Détails du cas de gestion des risques internes](../media/insider-risk-case-details.png)

L’onglet **Vue d’ensemble** des cas inclut également une section **Alertes** qui inclut les informations suivantes sur les alertes de correspondance de stratégie associées au cas :

- **Correspondances de** stratégie : nom de la stratégie de gestion des risques internes associée aux alertes de correspondance pour les activités potentiellement risquées des utilisateurs susceptibles d’entraîner un incident de sécurité.
- **État** : état de l’alerte.
- **Gravité** : gravité de l’alerte.
- **Heure détectée** : temps écoulé depuis la génération de l’alerte.

### <a name="alerts"></a>Alertes

L’onglet **Alertes** récapitule les alertes actuelles incluses dans le cas. De nouvelles alertes peuvent être ajoutées à un cas existant et elles seront ajoutées à la file d’attente **d’alerte** au fur et à mesure qu’elles sont affectées. Les attributs d’alerte suivants sont répertoriés dans la file d’attente :

- État
- Severity
- Heure détectée

Sélectionnez une alerte dans la file d’attente pour afficher la page **de détails de l’alerte** .

Utilisez le contrôle de recherche pour rechercher du texte spécifique dans les noms d’alerte et utilisez le filtre d’alerte pour trier les cas selon les attributs suivants :

- État
- Severity
- Heure détectée, la date de début et la date de fin

Utilisez le contrôle de filtre pour filtrer les alertes selon plusieurs attributs, notamment :


- **État** : sélectionnez une ou plusieurs valeurs d’état pour filtrer la liste des alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise* et *Résolu*.
- **Gravité** : sélectionnez un ou plusieurs niveaux de gravité de risque d’alerte pour filtrer la liste des alertes. Les options disponibles sont *Élevée*, *Moyenne* et *Faible*.
- **Heure détectée** : sélectionnez les dates de début et de fin de la création de l’alerte.
- **Stratégie** : sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

### <a name="user-activity"></a>Activité utilisateur

**L’onglet Activité de** l’utilisateur permet aux analystes des risques et aux enquêteurs d’examiner les détails de l’activité des utilisateurs et d’utiliser une représentation visuelle de toutes les activités potentiellement à risque associées aux alertes et aux cas à risque pour déterminer si ces activités à risque peuvent entraîner un incident de sécurité. Par exemple, dans le cadre du processus de triage des alertes, les analystes peuvent avoir besoin d’examiner toutes les activités à risque associées au cas pour plus de détails. Dans les cas, les enquêteurs sur les risques peuvent consulter les détails de l’activité des utilisateurs et le graphique en bulles pour mieux comprendre l’étendue globale des activités à risque associées au cas. Pour plus d’informations sur le graphique d’activité utilisateur, consultez l’article [Activités de gestion des risques internes](insider-risk-management-activities.md#user-activity) .

### <a name="activity-explorer-preview"></a>Explorateur d’activités (préversion)

**L’onglet Explorateur d’activités** permet aux analystes des risques et aux enquêteurs d’examiner les détails de l’activité de cas associées aux alertes à risque. Par exemple, dans le cadre des mesures de gestion de cas, les enquêteurs et les analystes devront peut-être examiner toutes les activités à risque associées au cas pour obtenir plus de détails. Avec **l’Explorateur d’activités**, les réviseurs peuvent rapidement examiner une chronologie des activités potentiellement à risque détectées et identifier et filtrer toutes les activités à risque associées aux alertes.

Pour plus d’informations sur l’Explorateur d’activités, consultez l’article [Activités de gestion des risques internes](insider-risk-management-activities.md#activity-explorer) .

## <a name="forensic-evidence-preview"></a>Preuve d’investigation (préversion)

L’onglet **Preuves forensiques (préversion)** permet aux enquêteurs sur les risques d’examiner les captures visuelles associées aux activités à risque incluses dans les cas. Par exemple, dans le cadre des actions de gestion de cas, les enquêteurs peuvent avoir besoin d’aider à clarifier le contexte de l’activité des utilisateurs en cours d’examen. L’affichage des clips réels de l’activité peut aider l’enquêteur à déterminer si l’activité de l’utilisateur est potentiellement risquée et peut entraîner un incident de sécurité.

Pour plus d’informations sur les preuves d’investigation, consultez l’article [En savoir plus sur les preuves forensiques de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-forensic-evidence) .

### <a name="content-explorer"></a>Explorateur de contenu

**L’onglet Explorateur** de contenu permet aux enquêteurs des risques d’examiner des copies de tous les fichiers individuels et messages électroniques associés aux alertes à risque. Par exemple, si une alerte est créée lorsqu’un utilisateur télécharge des centaines de fichiers à partir de SharePoint Online et que l’activité déclenche une alerte de stratégie, tous les fichiers téléchargés pour l’alerte sont capturés et copiés dans le cas de gestion des risques internes à partir de sources de stockage d’origine.

L’Explorateur de contenu est un outil puissant avec des fonctionnalités de recherche et de filtrage de base et avancées. Pour en savoir plus sur l’utilisation de l’Explorateur de contenu, consultez Explorateur [de contenu gestion des risques internes](insider-risk-management-content-explorer.md).

![Cas de gestion des risques internes Explorateur de contenu.](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Notes sur le cas

L’onglet **Notes** sur le cas dans le cas est l’endroit où les analystes des risques et les enquêteurs partagent des commentaires, des commentaires et des insights sur leur travail pour le cas. Les notes sont des ajouts permanents à un cas et ne peuvent pas être modifiées ou supprimées après l’enregistrement de la note. Lors de la création d’un cas à partir d’une alerte, les commentaires entrés dans la boîte de dialogue **Confirmer l’alerte et créer un cas de risque internes** sont automatiquement ajoutés comme note de cas.

Le tableau de bord des notes de cas affiche les notes de l’utilisateur qui a créé la note et le temps écoulé depuis l’enregistrement de la note. Pour rechercher un mot clé spécifique dans le champ de texte de note de cas, utilisez le bouton **Rechercher** dans le tableau de bord de cas et entrez un mot clé spécifique.

Pour ajouter une note à un cas :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Cas**.
2. Sélectionnez un cas, puis sélectionnez l’onglet **Notes de cas** .
3. Sélectionnez **Ajouter une note de casse**.
4. Dans la boîte de dialogue **Ajouter une note de casse** , tapez votre note pour le cas. Sélectionnez **Enregistrer** pour ajouter la note au cas ou **sélectionnez Annuler** la fermeture sans enregistrer la note dans le cas.

### <a name="contributors"></a>Contributeurs

L’onglet **Contributeurs** dans le cas est l’endroit où les analystes et les enquêteurs peuvent ajouter d’autres réviseurs au cas. Par défaut, tous les utilisateurs **auxquels sont attribués les rôles Analystes de gestion des risques** **internes et Enquêteurs en gestion des risques internes** sont répertoriés en tant que contributeurs pour chaque cas actif et fermé. Seuls les utilisateurs auxquels est attribué le rôle **Enquêteur de gestion des risques internes sont autorisés** à afficher les fichiers et les messages dans l’Explorateur de contenu.

L’accès temporaire à un cas peut être accordé en ajoutant un utilisateur en tant que contributeur. Les contributeurs disposent de tous les contrôles de gestion de cas sur le cas spécifique, à l’exception des éléments suivants :

- Autorisation de confirmer ou d’ignorer les alertes
- Autorisation de modifier les contributeurs pour les cas
- Autorisation d’afficher des fichiers et des messages dans l’Explorateur de contenu

Pour ajouter un contributeur à un cas :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Cas**.
2. Sélectionnez un cas, puis sélectionnez l’onglet **Contributeurs** .
3. Sélectionnez **Ajouter un contributeur**.
4. Dans la boîte de dialogue **Ajouter un contributeur** , commencez à taper le nom de l’utilisateur que vous souhaitez ajouter, puis sélectionnez l’utilisateur dans la liste des utilisateurs suggérés. Cette liste est générée à partir d’Azure Active Directory de votre abonnement client.
5. Sélectionnez **Ajouter** pour ajouter l’utilisateur en tant que contributeur ou sélectionnez **Annuler** fermer la boîte de dialogue sans ajouter l’utilisateur en tant que contributeur.

## <a name="case-actions"></a>Actions de cas

Les enquêteurs sur les risques peuvent prendre des mesures sur un cas selon l’une des méthodes suivantes, en fonction de la gravité du cas, de l’historique des risques de l’utilisateur et des directives relatives aux risques de votre organisation. Dans certains cas, vous devrez peut-être faire remonter un cas à un utilisateur ou à une enquête sur les données pour collaborer avec d’autres domaines de votre organisation et approfondir les activités à risque. La gestion des risques internes est étroitement intégrée à d’autres solutions Microsoft Purview pour vous aider à gérer la résolution de bout en bout.

### <a name="send-email-notice"></a>Envoyer une notification par e-mail

Dans la plupart des cas, les actions utilisateur qui créent des alertes à risque interne sont accidentelles ou accidentelles. L’envoi d’un avis de rappel à l’utilisateur par e-mail est une méthode efficace pour documenter l’examen et l’action de cas. Il s’agit d’une méthode permettant de rappeler aux utilisateurs des stratégies d’entreprise ou de les diriger vers une formation de mise à jour. Les avis sont générés à partir de [modèles de notification que vous créez](insider-risk-management-notices.md) pour votre infrastructure de gestion des risques internes.

Il est important de se rappeler que l’envoi d’un e-mail d’avis à un utilisateur ***ne résout pas** le cas comme _Closed*. Dans certains cas, vous pouvez laisser un cas ouvert après avoir envoyé un avis à un utilisateur pour rechercher d’autres activités à risque sans ouvrir de nouveau cas. Si vous voulez résoudre un cas après l’envoi d’une notification, vous devez sélectionner le **Résoudre un cas** sous la forme d’une étape de suivi après l’envoi d’une notification.

Pour envoyer une notification à l’utilisateur affecté à un cas :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Cas**.
2. Sélectionnez un cas, puis sélectionnez le bouton **Envoyer un avis par e-mail** dans la barre d’outils de l’action de cas.
3. Dans la boîte de dialogue **Envoyer une notification par e-mail** , sélectionnez le contrôle de liste déroulante **Choisir un modèle d’avis** pour sélectionner le modèle d’avis pour l’avis. Cette sélection préremplit les autres champs de l’avis.
4. Passez en revue les champs d’avis et mettez à jour le cas échéant. Les valeurs entrées ici remplacent les valeurs du modèle.
5. Sélectionnez **Envoyer** pour envoyer l’avis à l’utilisateur ou sélectionnez **Annuler** fermer la boîte de dialogue sans envoyer l’avis à l’utilisateur. Tous les avis envoyés sont ajoutés à la file d’attente des notes de cas dans le tableau de bord **Notes** de cas.

### <a name="escalate-for-investigation"></a>Réaffecter pour examen

Augmentez le cas pour l’enquête de l’utilisateur dans les situations où un examen juridique supplémentaire est nécessaire pour l’activité à risque de l’utilisateur. Cette escalade ouvre un nouveau cas Microsoft Purview eDiscovery (Premium) dans votre organisation Microsoft 365. La découverte électronique (Premium) fournit un flux de travail de bout en bout pour préserver, collecter, examiner, analyser et exporter le contenu qui répond aux enquêtes juridiques internes et externes de votre organisation. Il permet également à votre équipe juridique de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les conservateurs impliqués dans un cas. L’escalade à un cas eDiscovery (Premium) à partir d’une affaire de gestion des risques internes aide votre équipe juridique à prendre les mesures appropriées et à gérer la conservation du contenu. Pour en savoir plus sur les cas eDiscovery (Premium), consultez [Vue d’ensemble de Microsoft Purview eDiscovery (Premium)](overview-ediscovery-20.md).

Pour faire remonter un cas à une investigation utilisateur :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Cas**.
2. Sélectionnez un cas, puis sélectionnez le bouton **Escalader pour investigation** dans la barre d’outils action de cas.
3. Dans la boîte de dialogue **Escalader pour investigation** , entrez un nom pour la nouvelle investigation utilisateur. Si nécessaire, entrez des notes sur le cas, puis sélectionnez **Escalader**.
4. Passez en revue les champs d’avis et mettez à jour le cas échéant. Les valeurs entrées ici remplacent les valeurs du modèle.
5. Sélectionnez **Confirmer** pour créer le cas d’investigation utilisateur ou **sélectionnez Annuler** pour fermer la boîte de dialogue sans créer de cas d’investigation utilisateur.

Une fois que le cas de gestion des risques internes a été remonté à un nouveau cas d’enquête utilisateur, vous pouvez examiner le nouveau cas dans la zone **eDiscovery** > **Advanced** dans le portail de conformité Microsoft Purview.

### <a name="run-automated-tasks-with-power-automate-flows-for-the-case"></a>Exécuter des tâches automatisées avec des flux Power Automate pour le cas

À l’aide des flux Power Automate recommandés, les enquêteurs et les analystes des risques peuvent rapidement prendre des mesures pour :

- Demander des informations aux RH ou à l’entreprise sur un utilisateur dans un cas de risque interne.
- Avertir le responsable lorsqu’un utilisateur a une alerte de risque interne.
- Créez un enregistrement pour un cas de gestion des risques internes dans ServiceNow.
- Avertir les utilisateurs lorsqu’ils sont ajoutés à une stratégie de risque interne.

Pour exécuter, gérer ou créer des flux Power Automate pour un cas de gestion des risques internes :

1. Sélectionnez **Automatiser** dans la barre d’outils de l’action de cas.
2. Choisissez le flux Power Automate à exécuter, puis sélectionnez **Exécuter le flux**.
3. Une fois le flux terminé, sélectionnez **Terminé**.

Pour en savoir plus sur les flux Power Automate pour la gestion des risques internes, consultez [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#power-automate-flows-preview).

 ### <a name="view-or-create-a-microsoft-teams-team-for-the-case"></a>Afficher ou créer une équipe Microsoft Teams pour le cas

Lorsque l’intégration de Microsoft Teams pour la gestion des risques internes est activée dans les paramètres, une équipe Microsoft Teams est automatiquement créée chaque fois qu’une alerte est confirmée et qu’un cas est créé. Les enquêteurs et les analystes des risques peuvent rapidement ouvrir Microsoft Teams et accéder directement à l’équipe pour un cas en sélectionnant **Afficher l’équipe Microsoft Teams** dans la barre d’outils d’action de cas.

Pour les cas ouverts avant l’activation de l’intégration de l’équipe Microsoft, les enquêteurs et les analystes des risques peuvent créer une équipe Microsoft Teams pour un cas en sélectionnant **Créer une équipe Microsoft Teams** dans la barre d’outils de l’action de cas.

Lorsqu’un cas est résolu, l’équipe Microsoft associée est automatiquement archivée (masquée et en lecture seule).

Pour en savoir plus sur Microsoft Teams pour la gestion des risques internes, consultez [Prise en main des paramètres de gestion des risques internes](insider-risk-management-settings.md#microsoft-teams-preview).

### <a name="resolve-the-case"></a>Résoudre le cas

Une fois que les analystes des risques et les enquêteurs ont terminé leur examen et leur enquête, un cas peut être résolu pour agir sur toutes les alertes actuellement incluses dans le cas. La résolution d’un cas ajoute une classification de résolution, modifie l’état du cas sur *Fermé*, et les raisons de l’action de résolution sont automatiquement ajoutées à la file d’attente des notes de cas dans le tableau de bord **Notes** de cas. Les cas sont résolus comme suit :

- **Inoffensif** : classification des cas où les alertes de correspondance de stratégie sont évaluées comme étant à faible risque, non graves ou faux positifs.
- **Violation de stratégie confirmée** : classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme risquées, graves ou le résultat d’une intention malveillante.

Pour résoudre un cas :

1. Dans la [portail de conformité Microsoft Purview](https://compliance.microsoft.com), accédez à **Gestion des risques internes** et sélectionnez l’onglet **Cas**.
2. Sélectionnez un cas, puis sélectionnez le bouton **Résoudre le cas** dans la barre d’outils d’action de cas.
3. Dans la boîte de dialogue **Résoudre le cas** , sélectionnez le contrôle de liste déroulante **Résoudre en tant que** pour sélectionner la classification de résolution du cas. Les options sont **Une violation de stratégie sans gravité** ou **Une violation de stratégie confirmée**.
4. Dans la boîte de dialogue **Résoudre le cas** , entrez les raisons de la classification de résolution dans le champ **de texte Action effectuée** .
5. Sélectionnez **Résoudre** pour fermer le cas ou **sélectionnez Annuler** fermer la boîte de dialogue sans résoudre le cas.
