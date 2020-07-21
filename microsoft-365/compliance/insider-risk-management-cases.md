---
title: Dossiers de gestion des risques initiés
description: En savoir plus sur les cas de gestion des risques internes dans Microsoft 365
keywords: Microsoft 365, gestion des risques internes, gestion des risques, conformité
localization_priority: Normal
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 52b80c85fcd9ddb22330c1103e3df908a217e8f2
ms.sourcegitcommit: a08103bc120bdec7cfeaf67c1be4e221241e69ad
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/21/2020
ms.locfileid: "45199932"
---
# <a name="insider-risk-management-cases"></a>Dossiers de gestion des risques initiés

Les cas sont le cœur de la gestion des risques initiés et vous permettent d’examiner et de traiter en profondeur les problèmes générés par les indicateurs de risque définis dans vos stratégies. Les incidents sont créés manuellement à partir d’alertes dans les situations où une autre action est nécessaire pour résoudre un problème lié à la conformité pour un utilisateur. Chaque cas est limité à un seul utilisateur et plusieurs alertes peuvent être ajoutées à un cas existant ou à un autre cas. 

Après avoir examiné les détails d’un cas, vous pouvez prendre les mesures suivantes :

- envoi d’une notification à l’utilisateur
- résolution du cas comme bénigne
- partage du cas avec votre instance de ServiceNow ou avec un destinataire de courrier électronique
- escalade de la demande de devis pour une enquête eDiscovery avancée

## <a name="cases-dashboard"></a>Tableau de bord incidents

Le **tableau de bord des cas** de gestion des risques Insiders vous permet d’afficher et d’agir sur les incidents. Chaque widget de rapport du tableau de bord affiche des informations pour les 30 derniers jours.

- **Cas actifs**: nombre total de cas actifs en cours d’enquête.
- **Cas au cours des 30 derniers jours**: nombre total de cas créés, triés par état *actif* et *fermé* .
- **Statistics**: durée moyenne des cas actifs, indiquée en heures, jours ou mois.

La file d’attente de cas répertorie tous les dossiers actifs et fermés de votre organisation, ainsi que l’état actuel des attributs case suivants :

- **Nom**de la casse : nom de l’incident, défini lorsqu’une alerte est confirmée et que le cas est créé.  
- **Status**: état *actif* ou *fermé*.
- **User**: l’utilisateur pour le cas. Si l’anonymisation pour les noms d’utilisateur est activée, les informations anonymes s’affichent.
- **Date/heure d’ouverture**: temps écoulé depuis l’ouverture du cas.
- **Total des alertes de stratégie**: nombre de correspondances de stratégie incluses dans le cas. Ce nombre peut augmenter si de nouvelles alertes sont ajoutées au cas.
- **Dernière mise à jour**: le temps écoulé depuis qu’il y a eu une remarque de cas ajoutée ou modifié dans l’état du cas.
- **Dernière mise à jour par**: le nom de l’analyste ou de l’investigateur de gestion des risques Insiders qui a mis à jour le cas.

![Tableau de bord des cas de gestion des risques Insiders](../media/insider-risk-cases-dashboard.png)

Utilisez le contrôle de **recherche** pour rechercher des noms de cas spécifiques et utilisez le filtre de cas pour trier les cas par les attributs suivants :

- Statut
- Heure d'ouverture du cas, date de début et la date de fin
- Dernière mise à jour, date de début et la date de fin

## <a name="filter-cases"></a>Filtrer les cas

Selon le nombre et le type de stratégies de gestion des risques Insider actives au sein de votre organisation, il peut s’avérer difficile de vérifier une grande file d’attente de cas. L’utilisation de filtres case peut aider les analystes et les enquêteurs à trier les cas en plusieurs attributs. Pour filtrer les alertes dans le **tableau de bord incidents**, sélectionnez le contrôle de **filtre** . Vous pouvez filtrer les incidents par un ou plusieurs attributs :

- **État**: sélectionnez une ou plusieurs valeurs d’État pour filtrer la liste de cas. Les options sont *active* et *Closed*.
- **Time case ouverte**: sélectionnez les dates de début et de fin de l’ouverture du cas.
- **Dernière mise à jour**: sélectionnez les dates de début et de fin du moment où le cas a été mis à jour.

## <a name="investigate-a-case"></a>Examiner un cas

Une enquête approfondie sur les alertes de gestion des risques initiés est essentielle pour prendre des mesures correctives appropriées. Les cas d’Insider de gestion des risques constituent l’outil de gestion centralisée pour approfondir l’historique des activités de risque utilisateur et les détails des alertes, et pour explorer le contenu et les messages exposés aux risques. Les analystes et les enquêteurs de risques utilisent également des cas pour centraliser les commentaires et les notes et traiter la résolution des incidents.

La sélection d’un cas ouvre les outils de gestion des cas et permet aux analystes et aux enquêteurs d’approfondir les détails des cas.

### <a name="case-overview"></a>Présentation du cas

L’onglet **Vue d’ensemble de cas** résume l'activité d'alerte et l'historique du niveau de risque pour le cas. 

- Le widget **alertes** affiche la correspondance de stratégie pour le cas, y compris l’état de l’alerte, la gravité du risque d’alerte et le moment où l’alerte a été détectée. 
- Le graphique **Historique du niveau de risque** affiche le niveau de risque de l'utilisateur au cours des 30 derniers jours. Le graphique en courbes permet aux analystes et aux enquêteurs de voir rapidement la tendance des risques globaux des utilisateurs au fil du temps. 
- Le widget **Contenu de l’activité de risque** synthétise les types de données et le contenu des alertes ajoutées au cas. Cet exemple offre une vue d’ensemble de la totalité des données et contenus exposés en cas de risque.

Le volet de **Détails des cas** est disponible sur tous les onglets de gestion des dossiers et récapitule les détails de l’incident pour les analystes et les investigateurs de risque. Elle comprend les éléments suivants :

- **Nom**de la casse : nom de l’incident, préfixé avec un numéro de séquence de casse généré automatiquement et le nom du risque associé au modèle de stratégie correspondant à la première alerte confirmée. 
- **État**de la demande de devis : état *actif* ou *fermé*.
- **Note de risque de l’utilisateur**: niveau de risque calculé actuel de l’utilisateur pour le cas. Ce score est calculé toutes les 24 heures et utilise les scores de risque d’alerte de toutes les alertes actives associées à l’utilisateur.
- **Alertes confirmées**: liste des alertes pour l’utilisateur confirmée pour le cas.
- **Contenu connexe**: liste de contenu, triée par sources et types de contenu. Par exemple, pour le contenu d’une alerte de cas dans SharePoint Online, il est possible de voir la liste des noms de dossiers ou de fichiers qui sont associés à l'activité à risque pour les alertes dans le cas.

![Détails des cas d’Insider gestion des risques](../media/insider-risk-case-details.png)

### <a name="alerts"></a>Alertes

L’onglet **alertes** résume les alertes actuelles incluses dans le cas. De nouvelles alertes peuvent être ajoutées à un cas existant et elles seront ajoutées à la file d’attente d' **alerte** à mesure qu’elles sont affectées. Les attributs d’alerte suivants sont répertoriés dans la file d’attente :

- Statut
- Severity
- Heure de détection

Sélectionnez une alerte dans la file d’attente pour afficher la page Détails de l' **alerte** .

Utilisez le contrôle de recherche pour rechercher des noms d’alerte pour un texte spécifique et utilisez le filtre d’alerte pour trier les cas par les attributs suivants :

- Statut
- Severity
- Heure détectée, la date de début et la date de fin

Utilisez le contrôle de filtre pour filtrer les alertes par plusieurs attributs, notamment :

- **État**: sélectionnez une ou plusieurs valeurs d’État pour filtrer la liste des alertes. Les options sont *Confirmé*, *Fermé*, *Révision requise*et *Résolu*.
- **Gravité**: sélectionnez un ou plusieurs niveaux de gravité des risques d’alerte pour filtrer la liste des alertes. Les options disponibles sont *Élevée*, *Moyenne*et *Faible*.
- **Heure détectée**: sélectionnez les dates de début et de fin de la date de création de l’alerte.
- **Stratégie**: sélectionnez une ou plusieurs stratégies pour filtrer les alertes générées par les stratégies sélectionnées.

### <a name="user-activity"></a>Activité utilisateur

L’onglet **Activité des utilisateurs** est l’un des outils les plus performants pour l’analyse des risques internes et l’examen pour les cas de la solution de gestion des risques internes. Cet onglet est conçu pour permettre un examen rapide d’un incident, notamment une chronologie historique de toutes les alertes, les détails de toutes les alertes, le score de risque actuel de l’utilisateur dans le cas et des contrôles permettant d’appliquer les risques dans le cas.

![Activité des utilisateurs de gestion des risques Insiders](../media/insider-risk-user-activities.png)

1. **Filtres date et heure**de la fenêtre : par défaut, les six derniers mois d’alertes confirmées dans le cas s’affichent dans le graphique d’activité de l’utilisateur. Vous pouvez facilement filtrer l’affichage graphique avec les contrôles de curseur aux deux extrémités de la fenêtre de graphique ou en définissant des dates de début et de fin spécifiques dans le contrôle de filtre de graphique.
2. **Activité et détails de l’alerte de risque**: les activités de risque s’affichent visuellement sous forme de bulles colorées dans le graphique d’activité de l’utilisateur. Les bulles sont créées pour différentes catégories de risques et la taille des bulles est proportionnelle au nombre d’activités à risque pour la catégorie. Sélectionnez une bulle pour afficher les détails de chaque activité de risque. Les détails sont les suivants :
    - **Date** de l’activité de risque.
    - Catégorie de l' **activité de risque**. Par exemple, des *courriers électroniques avec des pièces jointes envoyées à l’extérieur de l’organisation* ou des *fichiers téléchargés à partir de SharePoint Online*.
    - **Score de risque** pour l’alerte. Ce score correspond au score numérique du niveau de gravité des risques d’alerte.
    - Nombre d’événements associés à l’alerte. Des liens vers chaque fichier ou message électronique associé à l’activité de risque sont également disponibles.
3. **Légende**de l’activité des risques : dans la partie inférieure du graphique d’activité de l’utilisateur, une légende de couleur vous permet de déterminer rapidement la catégorie de risque pour chaque alerte.
4. **Chronologie**de l’activité des risques : la chronologie complète de toutes les alertes de risque associées à l’incident est répertoriée, y compris tous les détails disponibles dans la bulle d’alerte correspondante.
5. **Actions de cas**: les options de résolution de l’incident figurent dans la barre d’outils action de l’incident. Vous pouvez résoudre un cas, envoyer une notification par courrier électronique à l’utilisateur ou escalader le cas à une enquête sur les données ou les utilisateurs.

### <a name="content-explorer"></a>Explorateur de contenu

L’onglet **Explorateur de contenu** permet aux analystes et aux enquêteurs de vérifier les copies de tous les fichiers et messages électroniques associés à des alertes de risque. Par exemple, si une alerte est créée lorsqu’un utilisateur télécharge des centaines de fichiers à partir de SharePoint Online et que l’activité déclenche une alerte de stratégie, tous les fichiers téléchargés pour l’alerte sont capturés et copiés dans le cas de la gestion des risques initiaux à partir des sources de stockage d’origine.

L’Explorateur de contenu est un outil puissant doté de fonctionnalités de recherche et de filtrage de base et avancées. Pour en savoir plus sur l’utilisation de l’Explorateur de contenu, reportez-vous à l' [Insider Risk Management content Explorer](insider-risk-management-content-explorer.md).

![Explorateur de contenu de cas de gestion des risques Insiders](../media/insider-risk-content-explorer.png)

### <a name="case-notes"></a>Notes de cas

L’onglet **Remarques** dans le cas correspond à l’endroit où les analystes et les investigateurs des risques partagent des commentaires, des commentaires et des informations sur leur travail pour le cas. Les notes sont des ajouts permanents à un cas et ne peuvent pas être modifiées ou supprimées une fois la note enregistrée. Lors de la création d’un cas à partir d’une alerte, les commentaires entrés dans la boîte de dialogue **Confirmer l’alerte et créer un cas de risque internes** sont automatiquement ajoutés comme note de cas.

Le tableau de bord des notes de cas affiche des notes par l’utilisateur qui a créé la note et le temps écoulé depuis l’enregistrement de la note. Pour rechercher un mot clé spécifique dans le champ de texte note de cas, utilisez le bouton **Rechercher** du tableau de bord de cas et entrez un mot clé spécifique.

Pour ajouter une note à un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez l’onglet **notes de cas** .
3. Sélectionnez **Ajouter une note de cas**.
4. Dans la boîte de dialogue **Ajouter une note de cas** , tapez votre remarque pour le cas. Sélectionnez **Enregistrer** pour ajouter la note au cas ou sélectionnez **Annuler** fermer sans enregistrer la note dans le cas.

### <a name="contributors"></a>Contributeurs

L’onglet **Contributeurs** dans le cas est l’endroit où les analystes et les enquêteurs peuvent ajouter d’autres réviseurs au cas. Par défaut, tous les utilisateurs auxquels sont affectés les rôles **analystes de gestion des risques Insider** et **inSided Management investigations** sont répertoriés en tant que contributeurs pour chaque cas actif et fermé.

Toutes les situations de gestion des risques internes doivent être gérées avec des contrôles d’accès appropriés en place pour assurer la confidentialité et l’intégrité de l’examen. Pour assurer le contrôle d’accès des cas, l’un des deux types d’accès est attribué aux utilisateurs :

- **Accès permanent**: l’accès permanent est automatiquement accordé aux utilisateurs avec les rôles des **analystes de gestion des risques internes** et des **investigateurs de gestion des risques Insiders** lorsque le cas est créé à partir d’une alerte. L'accès permanent permet un contrôle total du cas pendant toute sa durée de vie et donne la possibilité d'ajouter d'autres contributeurs au cas.
- **Accès temporaire**: l’accès temporaire est accordé uniquement aux utilisateurs par des collaborateurs qui disposent d’un accès permanent pour le cas. En règle générale, ce niveau d’accès est accordé à l’utilisateur qui doit ajouter des notes à un cas. Les collaborateurs disposant d’un accès temporaire ont accès à tous les contrôles de gestion des cas, sauf :
    - Autorisation de confirmer ou d’ignorer les alertes
    - Autorisation de modifier les contributeurs pour les cas
    - Autorisation d’afficher les fichiers et messages dans l’Explorateur de contenu

Pour ajouter un collaborateur à un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez l’onglet **collaborateurs** .
3. Sélectionnez **Ajouter un collaborateur**.
4. Dans la boîte de dialogue **Ajouter un collaborateur** , commencez à taper le nom de l’utilisateur que vous souhaitez ajouter, puis sélectionnez l’utilisateur dans la liste des utilisateurs suggérés. Cette liste est générée à partir de l’Azure Active Directory de votre abonnement client.
5. Dans la boîte de dialogue **Ajouter un collaborateur** , sélectionnez le niveau d’accès du collaborateur. Vous pouvez sélectionner **permanent** ou **temporaire**.
6. Sélectionnez **Ajouter** pour ajouter l’utilisateur en tant que collaborateur ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans ajouter l’utilisateur en tant que collaborateur.

## <a name="case-actions"></a>Actions de cas

Les analystes et les enquêteurs de risques peuvent agir sur un cas selon l’une des méthodes, selon la gravité du cas, l’historique des risques et les recommandations de votre organisation. Dans certains cas, il se peut que vous deviez transmettre un cas à un utilisateur ou à une enquête de données pour collaborer avec d’autres domaines de votre organisation et approfondir les activités à risque. La gestion des risques initiés est étroitement intégrée aux autres solutions de conformité Microsoft 365 pour vous aider à gérer la résolution de bout en bout.

### <a name="send-email-notice"></a>Envoyer une notification par courrier électronique

Dans la plupart des cas, les actions de l’utilisateur qui créent des alertes de risque involontaires sont involontaires ou accidentelles. Envoyer une notification de rappel à l’utilisateur par courrier électronique est une méthode efficace pour documenter l’examen et l’action des cas, ainsi qu’une méthode pour rappeler aux utilisateurs les stratégies d’entreprise ou pour les diriger vers la formation de réactualisation. Les notifications sont générées à partir de [modèles de notification que vous créez](insider-risk-management-notices.md) pour votre infrastructure de gestion des risques Insiders.

N’oubliez pas que l’envoi d’un message électronique à un utilisateur ***ne*** résout pas le cas comme étant *fermé*. Dans certains cas, vous souhaiterez peut-être laisser un cas ouvert après l’envoi d’une notification à un utilisateur pour rechercher des activités à risque supplémentaires sans ouvrir de nouveau cas. Si vous voulez résoudre un cas après l’envoi d’une notification, vous devez sélectionner le **Résoudre un cas** sous la forme d’une étape de suivi après l’envoi d’une notification.

Pour envoyer une notification à l’utilisateur affecté à un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez le bouton **Envoyer une notification par courrier électronique** sur la barre d’outils action de cas.
3. Dans la boîte de dialogue **Envoyer une notification par courrier électronique** , sélectionnez le modèle de liste déroulante **choisir un modèle d’avis** pour sélectionner le modèle d’avertissement de l’avis. Cette sélection pré-remplit les autres champs de l’avis.
4. Examinez les champs notice et mettez à jour le cas échéant. Les valeurs entrées ici remplaceront les valeurs du modèle.
5. Sélectionnez **Envoyer** pour envoyer l’avis à l’utilisateur ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans envoyer l’avis à l’utilisateur. Toutes les notifications envoyées sont ajoutées à la file d’attente de notes dans le tableau de bord **Notes** de cas.

### <a name="escalate-for-investigation"></a>Faire remonter le dossier pour enquête

Escaladez le cas à l’enquête utilisateur dans des situations où un examen juridique supplémentaire est nécessaire pour l’activité de risque de l’utilisateur. Cette remontée ouvre un nouveau dossier Advanced eDiscovery dans votre organisation Microsoft 365. Advanced eDiscovery offre un flux de travail de bout en bout pour conserver, collecter, réviser, analyser et exporter du contenu réactif aux examens juridiques internes et externes de votre organisation. Il permet également à votre équipe juridique de gérer l’ensemble du flux de travail de notification de conservation légale pour communiquer avec les conservateurs impliqués dans un cas. L’affectation d’un réviseur en tant que consignataire dans un cas Advanced eDiscovery créé à partir d’un cas de gestion des risques internes permet à votre équipe juridique de prendre les mesures appropriées et de gérer la conservation du contenu. Pour en savoir plus sur les cas Advanced eDiscovery, consultez [Présentation de Advanced eDiscovery dans Microsoft 365](overview-ediscovery-20.md).

Pour transmettre un incident à une enquête utilisateur :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez le bouton **escalader pour l’enquête** sur la barre d’outils action de cas.
3. Dans la boîte de dialogue **escalade de l’enquête** , entrez un nom pour la nouvelle enquête utilisateur. Si nécessaire, entrez des remarques sur le cas et sélectionnez **escalade**.
5. Sélectionnez **confirmer** pour créer le cas d’enquête utilisateur ou cliquez sur **Annuler** pour fermer la boîte de dialogue sans créer de cas d’enquête utilisateur.

Une fois que le cas de gestion des risques inSided a été remonté vers un nouveau cas d’enquête utilisateur, vous pouvez passer en revue le nouveau cas dans la zone avancé de **découverte électronique**  >  **Advanced** dans le centre de conformité Microsoft 365.

### <a name="share-a-case"></a>Partager un cas

Le partage d’un dossier de gestion des risques inSided permet aux investigateurs et examens de collaborer facilement avec les autres parties prenantes en matière de conformité de votre organisation. Vous pouvez rapidement partager un lien vers un cas d’Insider de gestion des risques avec des parties prenantes externes à partir du domaine de gestion des cas. Pour accéder au cas de gestion des risques inSided à partir du lien, les parties prenantes doivent être incluses dans n’importe quel groupe de rôles de gestion des risques Insiders.

Les options de partage suivantes sont disponibles : 

- **ServiceNow**: après avoir configuré le connecteur ServiceNow Microsoft 365 pour votre organisation Microsoft 365, vous pouvez facilement partager un lien vers le cas, ouvrir un incident ou demander une modification avec votre organisation ServiceNow. Pour partager le cas avec ServiceNow, sélectionnez **partager**  >  **ServiceNow** à partir de l’action case. L’intégration de ServiceNow avec les supports de gestion des risques initiaux inclut les informations et les actions suivantes :
    - **Nom**de la tâche : nom de la nouvelle tâche ServiceNow.
    - **Description**de la tâche : description de la nouvelle tâche ServiceNow. Ce champ de description modifiable inclut automatiquement un lien vers le cas d’Insider de gestion des risques.
    - **Type de tâche**: type de tâche pour la nouvelle tâche ServiceNow, qu’il s’agisse d’un *incident* ou d’une *demande de modification*.
    - **Priority**: priorité de la nouvelle tâche ServiceNow, à savoir *planification*, *faible*, *modérée*, *élevée*ou *critique*.
    - **Date d’échéance**: date demandée pour l’exécution de la tâche ServiceNow.

![Partage de la gestion des risques initiés avec ServiceNow](../media/insider-risk-share-servicenow.png)

- **Courrier électronique**: partage un lien vers le cas d’Insider de gestion des risques dans un message électronique. Vous pouvez choisir n’importe quel client de messagerie configuré localement avec cette option de partage. Pour partager le lien de cas avec le courrier, sélectionnez **partager**  >  le**courrier électronique** à partir de la barre d’outils action de cas.
- **Copier le lien**: copie un lien vers le cas d’Insider de gestion des risques dans votre presse-papiers. Pour copier le lien de cas dans votre presse-papiers, sélectionnez **partager**le  >  **lien de copie** à partir de la barre d’outils action de cas.

### <a name="resolve-the-case"></a>Résoudre le dossier

Une fois que les analystes et les enquêteurs ont terminé leur examen et leur enquête, un cas peut être résolu pour agir sur toutes les alertes actuellement incluses dans le cas. La résolution d’un cas ajoute une classification de résolution, le statut de la case à *fermeture*et les motifs d’action de résolution sont automatiquement ajoutés à la file d’attente de notes dans le tableau de bord **Notes** de cas. Les cas sont résolus comme suit :

- **Bénigne**: la classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme faible risque, non sérieux ou faux positif.
- **Violation de stratégie confirmée**: classification pour les cas où les alertes de correspondance de stratégie sont évaluées comme risquées, graves ou le résultat d’un but malveillant.

Pour résoudre un cas :

1. Dans le [Centre de conformité Microsoft 365](https://compliance.microsoft.com), accédez à **gestion des risques internes** et sélectionnez l’onglet **incidents** .
2. Sélectionnez un cas, puis sélectionnez le bouton **résoudre le cas** dans la barre d’outils action de cas.
3. Dans la boîte de dialogue **résoudre l’incident** , sélectionnez le contrôle **résoudre en tant que** liste déroulante pour sélectionner la classification de résolution pour le cas. Les options sont **inoffensives** ou une **violation de stratégie confirmée**.
4. Dans la boîte de dialogue **résoudre l’incident** , entrez les motifs de la classification de résolution dans le champ texte de l' **action effectuée** .
5. Sélectionnez **résoudre** pour fermer le cas ou sélectionnez **Annuler** pour fermer la boîte de dialogue sans résoudre le cas.
