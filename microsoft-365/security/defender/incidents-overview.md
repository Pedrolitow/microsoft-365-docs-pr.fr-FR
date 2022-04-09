---
title: Réponse aux incidents avec Microsoft 365 Defender
description: Examinez les incidents rencontrés sur les appareils, les utilisateurs et les boîtes aux lettres dans le portail Microsoft 365 Defender.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: 70f75fd5986a5d837e33b3caf0b7cb23239ddce5
ms.sourcegitcommit: dd7e5b67ff4ae4e7f74490e437c1795933c74cc7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2022
ms.locfileid: "64731589"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Réponse aux incidents avec Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Un incident dans Microsoft 365 Defender est une collection d’alertes corrélées et de données associées qui composent l’histoire d’une attaque.

Les services et applications Microsoft 365 créent des alertes lorsqu’ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques contre différents types d’entités, comme les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client.

Étant donné que le regroupement des alertes individuelles pour obtenir des insights sur une attaque peut s’avérer difficile et fastidieux, Microsoft 365 Defender agrège automatiquement les alertes et leurs informations associées dans un incident.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Comment Microsoft 365 Defender met en corrélation les événements d’entités dans un incident." lightbox="../../media/incidents-overview/incidents.png":::

Regardez cette courte vue d’ensemble des incidents en Microsoft 365 Defender (4 minutes).

<br>

>[!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bzwz?]

Le regroupement d’alertes associées dans un incident vous donne une vue complète d’une attaque. Par exemple, vous pouvez voir :

- Où l’attaque a démarré.
- Quelles tactiques ont été utilisées.
- Jusqu’où l’attaque est-elle passée dans votre locataire.
- L’étendue de l’attaque, par exemple le nombre d’appareils, d’utilisateurs et de boîtes aux lettres qui ont été affectés.
- Toutes les données associées à l’attaque.

[S’il est activé](m365d-enable.md), Microsoft 365 Defender pouvez [examiner et résoudre automatiquement](m365d-autoir.md) les alertes par le biais de l’automatisation et de l’intelligence artificielle. Vous pouvez également effectuer des étapes de correction supplémentaires pour résoudre l’attaque.

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Incidents et alertes dans le portail Microsoft 365 Defender

Vous gérez les incidents à partir **d’incidents & alertes > incidents** lors du lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Page Incidents dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

La sélection d’un nom d’incident affiche un résumé de l’incident et fournit un accès aux onglets avec des informations supplémentaires. Voici un exemple.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Page Résumé d’un incident dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Les onglets supplémentaires d’un incident sont les suivants :

- Alertes

  Toutes les alertes liées à l’incident et leurs informations.

- Appareils

  Tous les appareils qui ont été identifiés comme faisant partie ou liés à l’incident.

- Utilisateurs

  Tous les utilisateurs identifiés comme faisant partie ou liés à l’incident.

- Boîtes aux lettres

  Toutes les boîtes aux lettres qui ont été identifiées comme faisant partie de l’incident ou associées à l’incident.

- Enquêtes

  Toutes les [investigations automatisées déclenchées](m365d-autoir.md) par les alertes dans l’incident.

- Preuve et réponse

  Tous les événements pris en charge et les entités suspectes dans les alertes de l’incident.

- Graph (préversion)

  Représentation visuelle de l’attaque qui connecte les différentes entités suspectes qui font partie de l’attaque avec leurs ressources associées, telles que les utilisateurs, les appareils et les boîtes aux lettres.

Voici la relation entre un incident et ses données et les onglets d’un incident dans le portail Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-security-center.png" alt-text="Relation d’un incident et de ses données aux onglets d’un incident dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-security-center.png":::

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Exemple de flux de travail de réponse aux incidents pour Microsoft 365 Defender

Voici un exemple de flux de travail pour répondre aux incidents dans Microsoft 365 avec le portail Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Exemple de flux de travail de réponse aux incidents pour le portail Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

En continu, identifiez les incidents les plus prioritaires pour l’analyse et la résolution dans la file d’attente des incidents et préparez-les pour la réponse. Il s’agit d’une combinaison de :

- [Tri pour](incident-queue.md) déterminer les incidents les plus prioritaires via le filtrage et le tri de la file d’attente d’incidents.
- [Gestion](manage-incidents.md) des incidents en modifiant leur titre, en les affectant à un analyste et en ajoutant des balises et des commentaires.

Tenez compte de ces étapes pour votre propre flux de travail de réponse aux incidents :

1. Pour chaque incident, commencez une [attaque et alertez l’investigation et l’analyse](investigate-incidents.md) :

   1. Affichez le résumé de l’incident pour comprendre son étendue et sa gravité, ainsi que les entités affectées par les onglets **Résumé** et **Graph** (préversion).

   1. Commencez à analyser les alertes pour comprendre leur origine, leur étendue et leur gravité avec l’onglet **Alertes** .

   1. Si nécessaire, collectez des informations sur les appareils, les utilisateurs et les boîtes aux lettres concernés avec les onglets **Appareils**, **Utilisateurs** et **Boîtes aux lettres** .

   1. Découvrez comment Microsoft 365 Defender a [automatiquement résolu certaines alertes](m365d-autoir.md) avec l’onglet **Investigations**.

   1. Si nécessaire, utilisez des informations dans le jeu de données pour l’incident pour plus d’informations sous l’onglet **Preuve et réponse** .

2. Après ou pendant votre analyse, effectuez l’endiguement pour réduire tout impact supplémentaire de l’attaque et l’élimination de la menace de sécurité.

3. Autant que possible, récupérez l’attaque en restaurant vos ressources de locataire à l’état dans lequel elles se trouvaient avant l’incident.

4. [Résolvez](manage-incidents.md#resolve-an-incident) l’incident et prenez le temps d’apprendre après l’incident à :

   - Comprendre le type de l’attaque et son impact.
   - Recherchez une tendance d’attaque de sécurité dans [Threat Analytics](threat-analytics.md) et la communauté de sécurité.
   - Rappelez-vous le flux de travail que vous avez utilisé pour résoudre l’incident et mettre à jour vos workflows, processus, stratégies et playbooks standard en fonction des besoins.
   - Déterminez si des modifications de votre configuration de sécurité sont nécessaires et implémentez-les.

Si vous débutez avec l’analyse de la sécurité, consultez [l’introduction à la réponse à votre premier incident](incidents-overview.md) pour plus d’informations et pour parcourir un exemple d’incident.

Pour plus d’informations sur la réponse aux incidents dans les produits Microsoft, consultez [cet article](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Exemples d’opérations de sécurité pour Microsoft 365 Defender

Voici un exemple d’opérations de sécurité (SecOps) pour Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Exemple d’opérations de sécurité pour Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Les tâches quotidiennes peuvent inclure :

- [Gestion des](manage-incidents.md) incidents
- Examen des actions AIR [(Automated Investigation and Response)](m365d-action-center.md) dans le Centre d’actions
- Examen de la dernière [analyse des menaces](threat-analytics.md)
- [Réponse aux](investigate-incidents.md) incidents

Les tâches mensuelles peuvent inclure :

- Examen [des paramètres AIR](m365d-configure-auto-investigation-response.md)
- Examen [du degré de sécurisation](microsoft-secure-score-improvement-actions.md) et de [la gestion des vulnérabilités & des menaces](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Création de rapports à votre chaîne de gestion de la sécurité informatique

Les tâches trimestrielles peuvent inclure un rapport et une séance d’information sur les résultats de la sécurité au directeur de la sécurité des informations (CISO).

Les tâches annuelles peuvent inclure la réalisation d’un incident majeur ou d’un exercice de violation pour tester votre personnel, vos systèmes et vos processus.

Les tâches quotidiennes, mensuelles, trimestrielles et annuelles peuvent être utilisées pour mettre à jour ou affiner les processus, les stratégies et les configurations de sécurité.

Pour plus [d’informations, consultez Intégration de Microsoft 365 Defender dans vos opérations de sécurité](integrate-microsoft-365-defender-secops.md).

### <a name="secops-resources-across-microsoft-products"></a>Ressources SecOps sur les produits Microsoft

Pour plus d’informations sur SecOps sur les produits Microsoft, consultez les ressources suivantes :

- [Capabilities](/security/compass/security-operations-capabilities)
- [Meilleures pratiques](/security/compass/security-operations)
- [Vidéos et diapositives](/security/compass/security-operations-videos-and-decks)

## <a name="get-incident-notifications-by-email"></a>Obtenir des notifications d’incident par e-mail

Vous pouvez configurer Microsoft 365 Defender pour informer votre personnel avec un e-mail concernant les nouveaux incidents ou les mises à jour des incidents existants. Vous pouvez choisir d’obtenir des notifications en fonction des facteurs suivants :

- Gravité de l’incident.
- Groupe d’appareils.
- Uniquement lors de la première mise à jour par incident.

La notification par e-mail contient des détails importants sur l’incident, comme le nom, la gravité et les catégories de l’incident, entre autres. Vous pouvez également accéder directement à l’incident et commencer votre analyse immédiatement. Pour plus d’informations, consultez [Examiner les incidents](investigate-incidents.md).

Vous pouvez ajouter ou supprimer des destinataires dans les notifications par e-mail. Les nouveaux destinataires sont avertis des incidents une fois qu’ils ont été ajoutés.

> [!NOTE]
> Vous avez besoin de l’autorisation **Gérer les paramètres de sécurité** pour configurer les paramètres de notification par e-mail. Si vous avez choisi d’utiliser la gestion des autorisations de base, les utilisateurs dotés de rôles Administrateur de sécurité ou Administrateur général peuvent configurer des notifications par e-mail. <br> <br>
De même, si votre organisation utilise le contrôle d’accès en fonction du rôle (RBAC), vous pouvez uniquement créer, modifier, supprimer et recevoir des notifications en fonction des groupes d’appareils que vous êtes autorisé à gérer.

### <a name="create-a-rule-for-email-notifications"></a>Créer une règle pour les notifications par e-mail

Suivez ces étapes pour créer une règle et personnaliser les paramètres de notification par courrier électronique.

1. Dans le volet de navigation, sélectionnez **Paramètres > Microsoft 365 Defender > notifications par e-mail d’incident**.
2. Sélectionnez **Ajouter un élément**.
3. Dans la page **De base** , tapez le nom de la règle et une description, puis sélectionnez **Suivant**.
4. Dans la page **Paramètres de** notification, configurez :
    - **Gravité de l’alerte** : choisissez les gravités d’alerte qui déclencheront une notification d’incident. Par exemple, si vous souhaitez uniquement être informé des incidents de gravité élevée, sélectionnez **Élevé**.
    - **Étendue du groupe d’appareils** : vous pouvez spécifier tous les groupes d’appareils ou sélectionner dans la liste des groupes d’appareils de votre client.
    - **Notifier uniquement lors de la première occurrence par incident** : sélectionnez si vous souhaitez recevoir une notification uniquement sur la première alerte qui correspond à vos autres sélections. Les mises à jour ou alertes ultérieures liées à l’incident n’envoient pas de notifications supplémentaires.
    - **Inclure le nom de l’organisation dans l’e-mail** : sélectionnez si vous souhaitez que le nom de votre organisation apparaisse dans la notification par courrier électronique.
    - **Inclure un lien de portail propre au client** : sélectionnez si vous souhaitez ajouter un lien avec l’ID de client dans la notification par courrier électronique pour accéder à un client Microsoft 365 spécifique.

    :::image type="content" source="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png" alt-text="Page Paramètres de notification pour les notifications par e-mail d’incident dans le portail Microsoft 365 Defender." lightbox="../../media/get-incident-notifications/incidents-ss-email-notification-settings.png":::

5. Sélectionnez **Suivant**. Dans la page **Destinataires** , ajoutez les adresses e-mail qui recevront les notifications d’incident. Sélectionnez **Ajouter** après avoir tapé chaque nouvelle adresse e-mail. Pour tester les notifications et vérifier que les destinataires les reçoivent dans les boîtes de réception, sélectionnez **Envoyer un e-mail de test**.
6. Sélectionnez **Suivant**. Dans la page **Vérifier la règle** , passez en revue les paramètres de la règle, puis sélectionnez **Créer une règle**. Les destinataires commenceront à recevoir des notifications d’incident par e-mail en fonction des paramètres.

Pour modifier une règle existante, sélectionnez-la dans la liste des règles. Dans le volet portant le nom de la règle, **sélectionnez Modifier la règle** et apportez vos modifications aux pages **Informations de base**, **Paramètres de** notification et **Destinataires** .

Pour supprimer une règle, sélectionnez-la dans la liste des règles. Dans le volet portant le nom de la règle, **sélectionnez Supprimer**.

## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Utilisez ce module d’apprentissage de Microsoft Learn pour comprendre comment utiliser Microsoft 365 Defender pour gérer les incidents et les alertes.

|Formation :|Examiner les incidents avec Microsoft 365 Defender|
|---|---|
|![Examinez les incidents avec Microsoft 365 Defender icône d’entraînement.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender unifie les données de menace de plusieurs services et utilise l’IA pour les combiner en incidents et alertes. Découvrez comment réduire le temps entre un incident et sa gestion pour sa prochaine réponse et résolution. <p> 27 min - 6 unités |

> [!div class="nextstepaction"]
> [Démarrer >](/learn/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Prochaines étapes

Utilisez les étapes répertoriées en fonction de votre niveau d’expérience ou de votre rôle au niveau de votre équipe de sécurité.

### <a name="experience-level"></a>Niveau d’expérience

Suivez ce tableau pour connaître votre niveau d’expérience en matière d’analyse de la sécurité et de réponse aux incidents.

| Niveau | Étapes |
|:-------|:-----|
| **New** | <ol><li> Consultez la [procédure pas à pas Répondre à votre premier incident](first-incident-overview.md) pour obtenir une visite guidée d’un processus classique d’analyse, de correction et de révision post-incident dans le portail Microsoft 365 Defender avec un exemple d’attaque. </li><li> Découvrez quels incidents doivent être [hiérarchisés](incident-queue.md) en fonction de la gravité et d’autres facteurs. </li><li> [Gérez les incidents](manage-incidents.md), ce qui inclut le renommage, l’affectation, la classification et l’ajout de balises et de commentaires en fonction de votre flux de travail de gestion des incidents.</li></ol> |
| **Expérimenté** | <ol><li> Démarrage avec la file d’attente des incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. Vous pouvez alors effectuer les opérations suivantes : </li> <ul><li> Découvrez quels incidents doivent être [hiérarchisés](incident-queue.md) en fonction de la gravité et d’autres facteurs. </li><li> [Gérez les incidents](manage-incidents.md), ce qui inclut le renommage, l’affectation, la classification et l’ajout de balises et de commentaires en fonction de votre flux de travail de gestion des incidents. </li><li> Effectuez [des investigations](investigate-incidents.md) sur les incidents. </li></ul> </li><li> Suivez et répondez aux menaces émergentes avec [l’analytique des menaces](threat-analytics.md). </li><li>  Recherche proactive des menaces avec [repérage avancé des menaces](advanced-hunting-overview.md). </li><li> Consultez ces [playbooks de réponse aux incidents pour obtenir des conseils détaillés](/security/compass/incident-response-playbooks) sur l’hameçonnage, la pulvérisation de mots de passe et les attaques d’octroi de consentement d’application. </li></ol> |

### <a name="security-team-role"></a>Rôle d’équipe de sécurité

Suivez ce tableau en fonction de votre rôle d’équipe de sécurité.

| Rôle | Étapes |
|---|---|
| Répondeur d’incident (niveau 1) | Démarrage avec la file d’attente des incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. Vous pouvez alors effectuer les opérations suivantes : <ul><li> Découvrez quels incidents doivent être [hiérarchisés](incident-queue.md) en fonction de la gravité et d’autres facteurs. </li><li> [Gérez les incidents](manage-incidents.md), ce qui inclut le renommage, l’affectation, la classification et l’ajout de balises et de commentaires en fonction de votre flux de travail de gestion des incidents. </li></ul> |
| Enquêteur ou analyste de sécurité (niveau 2) | <ol><li> Effectuez [des investigations sur les](investigate-incidents.md) incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. </li><li> Consultez ces [playbooks de réponse aux incidents pour obtenir des conseils détaillés](/security/compass/incident-response-playbooks) sur l’hameçonnage, la pulvérisation de mots de passe et les attaques d’octroi de consentement d’application. </li></ol> |
| Analyste de sécurité avancé ou chasseur de menaces (niveau 3) | <ol><li>Effectuez [des investigations sur les](investigate-incidents.md) incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. </li><li> Suivez et répondez aux menaces émergentes avec [l’analytique des menaces](threat-analytics.md). </li><li> Recherche proactive des menaces avec [repérage avancé des menaces](advanced-hunting-overview.md). </li><li> Consultez ces [playbooks de réponse aux incidents pour obtenir des conseils détaillés](/security/compass/incident-response-playbooks) sur l’hameçonnage, la pulvérisation de mots de passe et les attaques d’octroi de consentement d’application. |
| Gestionnaire SOC | Découvrez comment [intégrer Microsoft 365 Defender à votre Centre des opérations de sécurité (SOC).](integrate-microsoft-365-defender-secops.md) |
