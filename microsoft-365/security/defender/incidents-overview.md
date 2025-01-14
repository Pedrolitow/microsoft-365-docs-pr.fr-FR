---
title: Réponse aux incidents avec Microsoft 365 Defender
description: Examinez les incidents détectés sur les appareils, les utilisateurs et les boîtes aux lettres dans le portail Microsoft 365 Defender.
keywords: incidents, alertes, récit d’attaque, investigation, analyse, réponse, corrélation, attaque, ordinateurs, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365, réponse aux incidents, cyberattaque
search.product: eADQiWindows 10XVcnh
ms.service: microsoft-365-security
ms.subservice: m365d
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
- m365-security
- tier1
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.openlocfilehash: da8e2ea8c4f3c239324a2a15992a0bd831fca55d
ms.sourcegitcommit: e7dbe3b0d97cd8c64b5ae15f990d5e4b1dc9c464
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68688198"
---
# <a name="incident-response-with-microsoft-365-defender"></a>Réponse aux incidents avec Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

Un incident dans Microsoft 365 Defender est une collection d’alertes corrélées et de données associées qui composent l’histoire d’une attaque.

Les services et applications Microsoft 365 créent des alertes lorsqu’ils détectent un événement ou une activité suspect ou malveillant. Les alertes individuelles fournissent des indices précieux sur une attaque terminée ou en cours. Toutefois, les attaques utilisent généralement différentes techniques contre différents types d’entités, comme les appareils, les utilisateurs et les boîtes aux lettres. Le résultat est plusieurs alertes pour plusieurs entités dans votre client.

Étant donné que le regroupement des alertes individuelles pour obtenir des insights sur une attaque peut s’avérer difficile et fastidieux, Microsoft 365 Defender agrège automatiquement les alertes et leurs informations associées dans un incident.

:::image type="content" source="../../media/incidents-overview/incidents.png" alt-text="Comment Microsoft 365 Defender met en corrélation les événements des entités dans un incident." lightbox="../../media/incidents-overview/incidents.png":::

Le regroupement d’alertes associées dans un incident vous donne une vue complète d’une attaque. Par exemple, vous pouvez voir :

- Où l’attaque a démarré.
- Quelles tactiques ont été utilisées.
- Jusqu’où l’attaque est-elle passée dans votre locataire.
- L’étendue de l’attaque, par exemple le nombre d’appareils, d’utilisateurs et de boîtes aux lettres qui ont été affectés.
- Toutes les données associées à l’attaque.

Si [cette option est activée](m365d-enable.md), Microsoft 365 Defender pouvez [examiner et résoudre automatiquement](m365d-autoir.md) les alertes par le biais de l’automatisation et de l’intelligence artificielle. Vous pouvez également effectuer des étapes de correction supplémentaires pour résoudre l’attaque.

## <a name="incidents-and-alerts-in-the-microsoft-365-defender-portal"></a>Incidents et alertes dans le portail Microsoft 365 Defender

Vous gérez les incidents à partir **d’incidents & d’alertes > d’incidents** lors du lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target=" blank">portail Microsoft 365 Defender</a>. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Page Incidents dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::

La sélection d’un nom d’incident affiche l’intégralité de l’histoire de l’attaque de l’incident, notamment :

- Page d’alerte dans l’incident : étendue des alertes liées à l’incident et leurs informations sous le même onglet.
- Graphe : représentation visuelle de l’attaque qui connecte les différentes entités suspectes qui font partie de l’attaque à leurs ressources associées, telles que les utilisateurs, les appareils et les boîtes aux lettres. 

Vous pouvez afficher les détails de l’entité directement à partir du graphique et agir dessus avec des options de réponse telles que la suppression de fichiers ou l’isolation de l’appareil.

:::image type="content" source="../../media/incidents-overview/incidents-ss-incident-summary.png" alt-text="Capture d’écran montrant la page de récit d’attaque pour un incident dans le portail Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-ss-incident-summary.png":::

Les onglets supplémentaires pour un incident sont les suivants :

- Alertes

  Toutes les alertes liées à l’incident et à leurs informations.

- Appareils

  Tous les appareils qui ont été identifiés comme faisant partie de ou liés à l’incident.

- Utilisateurs

  Tous les utilisateurs qui ont été identifiés comme faisant partie ou liés à l’incident.

- Boîtes aux lettres

  Toutes les boîtes aux lettres qui ont été identifiées comme faisant partie ou liées à l’incident.

- Enquêtes

  Toutes les [investigations automatisées](m365d-autoir.md) déclenchées par les alertes dans l’incident.

- Preuve et réponse

  Tous les événements pris en charge et les entités suspectes dans les alertes de l’incident.

- Résumé

  Vue d’ensemble rapide des ressources affectées associées aux alertes.

> [!NOTE]
> Si vous voyez un état d’alerte *de type d’alerte non pris en charge* , cela signifie que les fonctionnalités d’investigation automatisée ne peuvent pas récupérer cette alerte pour exécuter une investigation automatisée. Toutefois, vous pouvez [examiner ces alertes manuellement](investigate-incidents.md#alerts).

## <a name="example-incident-response-workflow-for-microsoft-365-defender"></a>Exemple de workflow de réponse aux incidents pour Microsoft 365 Defender

Voici un exemple de flux de travail pour répondre aux incidents dans Microsoft 365 avec le portail Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-workflow.png" alt-text="Exemple de workflow de réponse aux incidents pour le portail Microsoft 365 Defender." lightbox="../../media/incidents-overview/incidents-example-workflow.png":::

En continu, identifiez les incidents les plus prioritaires pour l’analyse et la résolution dans la file d’attente des incidents et préparez-les pour la réponse. Il s’agit d’une combinaison de :

- [Triage](incident-queue.md) pour déterminer les incidents de priorité la plus élevée par le filtrage et le tri de la file d’attente des incidents.
- [Gestion des](manage-incidents.md) incidents en modifiant leur titre, en les affectant à un analyste et en ajoutant des balises et des commentaires.

Envisagez les étapes suivantes pour votre propre workflow de réponse aux incidents :

1. Pour chaque incident, commencez une [attaque et alertez l’investigation et l’analyse](investigate-incidents.md) :

   1. Affichez l’histoire de l’attaque de l’incident pour comprendre son étendue, sa gravité, sa source de détection et les entités affectées.

   1. Commencez à analyser les alertes pour comprendre leur origine, leur étendue et leur gravité avec l’histoire de l’alerte dans l’incident.

   1. Si nécessaire, collectez des informations sur les appareils, les utilisateurs et les boîtes aux lettres concernés à l’aide du graphique. Cliquez avec le bouton droit sur une entité pour ouvrir un menu volant avec tous les détails.

   1. Découvrez comment Microsoft 365 Defender a [résolu automatiquement certaines alertes](m365d-autoir.md) sous l’onglet **Investigations**.

   1. Si nécessaire, utilisez les informations du jeu de données pour l’incident pour plus d’informations avec l’onglet **Preuve et réponse** .

2. Après ou pendant votre analyse, effectuez l’endiguement pour réduire tout impact supplémentaire de l’attaque et l’élimination de la menace de sécurité.

3. Autant que possible, récupérez l’attaque en restaurant vos ressources de locataire à l’état dans lequel elles se trouvaient avant l’incident.

4. [Résolvez](manage-incidents.md#resolve-an-incident) l’incident et prenez le temps d’apprendre après l’incident pour :

   - Comprendre le type de l’attaque et son impact.
   - Recherchez une tendance d’attaque dans [Threat Analytics](threat-analytics.md) et la communauté de sécurité.
   - Rappelez-vous le flux de travail que vous avez utilisé pour résoudre l’incident et mettre à jour vos workflows, processus, stratégies et playbooks standard en fonction des besoins.
   - Déterminez si des modifications de votre configuration de sécurité sont nécessaires et implémentez-les.

Si vous débutez dans l’analyse de la sécurité, consultez la [présentation de la réponse à votre premier incident](incidents-overview.md) pour obtenir des informations supplémentaires et parcourir un exemple d’incident.

Pour plus d’informations sur la réponse aux incidents dans les produits Microsoft, consultez [cet article](/security/compass/incident-response-overview).

## <a name="example-security-operations-for-microsoft-365-defender"></a>Exemples d’opérations de sécurité pour Microsoft 365 Defender

Voici un exemple d’opérations de sécurité (SecOps) pour Microsoft 365 Defender.

:::image type="content" source="../../media/incidents-overview/incidents-example-operations.png" alt-text="Exemple d’opérations de sécurité pour Microsoft 365 Defender" lightbox="../../media/incidents-overview/incidents-example-operations.png":::

Les tâches quotidiennes peuvent inclure :

- [Gestion des](manage-incidents.md) incidents
- Examen des actions [d’investigation et de réponse automatisées (AIR)](m365d-action-center.md) dans le centre de notifications
- Examen de la dernière version [d’Analyse des menaces](threat-analytics.md)
- [Réponse aux](investigate-incidents.md) incidents

Les tâches mensuelles peuvent inclure :

- Examen des [paramètres AIR](m365d-configure-auto-investigation-response.md)
- Examen du [degré de sécurisation](microsoft-secure-score-improvement-actions.md) et [de la Gestion des vulnérabilités Microsoft Defender](../defender-endpoint/next-gen-threat-and-vuln-mgt.md)
- Rapports à votre chaîne de gestion de la sécurité informatique

Les tâches trimestrielles peuvent inclure un rapport et une séance d’information sur les résultats de la sécurité à l’intention du responsable de la sécurité de l’information (CISO).

Les tâches annuelles peuvent inclure la conduite d’un incident majeur ou d’un exercice de violation pour tester votre personnel, vos systèmes et vos processus.

Les tâches quotidiennes, mensuelles, trimestrielles et annuelles peuvent être utilisées pour mettre à jour ou affiner les processus, les stratégies et les configurations de sécurité.

Pour plus [d’informations, consultez Intégration de Microsoft 365 Defender dans vos opérations de sécurité](integrate-microsoft-365-defender-secops.md).

### <a name="secops-resources-across-microsoft-products"></a>Ressources SecOps dans les produits Microsoft

Pour plus d’informations sur SecOps sur les produits Microsoft, consultez les ressources suivantes :

- [Capabilities](/security/compass/security-operations-capabilities)
- [Meilleures pratiques](/security/compass/security-operations)
- [Vidéos et diapositives](/security/compass/security-operations-videos-and-decks)

## <a name="get-incident-notifications-by-email"></a>Recevoir des notifications d’incident par e-mail

Vous pouvez configurer Microsoft 365 Defender pour informer votre personnel par e-mail des nouveaux incidents ou des mises à jour des incidents existants. Vous pouvez choisir d’obtenir des notifications en fonction des points suivants :

- Gravité de l’alerte
- Sources d’alerte 
- Groupe d’appareils

**Choisissez de recevoir des notifications par e-mail uniquement pour une source de service spécifique** : vous pouvez facilement sélectionner des sources de service spécifiques pour lesquelles vous souhaitez recevoir des notifications par e-mail.
 
**Obtenir plus de granularité avec des sources de détection spécifiques** : vous pouvez recevoir des notifications uniquement pour une source de détection spécifique. 

**Définir la gravité par détection ou source de service** : vous pouvez choisir d’obtenir des notifications par e-mail uniquement sur des gravités spécifiques par source. Par exemple, vous pouvez recevoir une notification pour les alertes moyenne et élevée pour EDR et toutes les gravités pour Microsoft Defender Experts.  

La notification par e-mail contient des détails importants sur l’incident, comme le nom de l’incident, la gravité et les catégories, entre autres. Vous pouvez également accéder directement à l’incident et commencer votre analyse immédiatement. Pour plus d’informations, consultez [Examiner les incidents](investigate-incidents.md).

Vous pouvez ajouter ou supprimer des destinataires dans les notifications par e-mail. Les nouveaux destinataires sont avertis des incidents après leur ajout.

> [!NOTE]
> Vous avez besoin de l’autorisation **Gérer les paramètres de sécurité** pour configurer les paramètres de notification par e-mail. Si vous avez choisi d’utiliser la gestion des autorisations de base, les utilisateurs disposant des rôles Administrateur de la sécurité ou Administrateur général peuvent configurer des notifications par e-mail. <br> <br>
De même, si votre organisation utilise le contrôle d’accès en fonction du rôle (RBAC), vous pouvez uniquement créer, modifier, supprimer et recevoir des notifications basées sur des groupes d’appareils que vous êtes autorisé à gérer.

### <a name="create-a-rule-for-email-notifications"></a>Créer une règle pour les notifications par e-mail

Suivez ces étapes pour créer une règle et personnaliser les paramètres de notification par courrier électronique.

1. Accédez à [Microsoft 365 Defender](https://security.microsoft.com) dans le volet de navigation, sélectionnez **Paramètres > Microsoft 365 Defender > Notifications par e-mail d’incident**.
2. Sélectionnez **Ajouter un élément**.
3. Dans la page **Informations de base** , tapez le nom de la règle et une description, puis sélectionnez **Suivant**.
4. Dans la page **Paramètres de notification** , configurez :
    - **Gravité de l’alerte** : choisissez les gravités d’alerte qui déclencheront une notification d’incident. Par exemple, si vous souhaitez uniquement être informé des incidents de gravité élevée, sélectionnez **Élevé**.
    - **Étendue du groupe d’appareils** : vous pouvez spécifier tous les groupes d’appareils ou sélectionner dans la liste des groupes d’appareils de votre client.
    - **Envoyer une seule notification par incident** : sélectionnez si vous souhaitez une notification par incident.
    - **Inclure le nom de l’organisation dans l’e-mail** : sélectionnez si vous souhaitez que le nom de votre organisation apparaisse dans la notification par courrier électronique.
    - **Inclure un lien de portail propre au client** : sélectionnez si vous souhaitez ajouter un lien avec l’ID de client dans la notification par courrier électronique pour accéder à un client Microsoft 365 spécifique.

    :::image type="content" source="../../media/get-incident-notifications/incidents-email-notification-settings.png" alt-text="Capture d’écran de la page Paramètres de notification pour les notifications par e-mail d’incident dans le portail Microsoft 365 Defender." lightbox="../../media/get-incident-notifications/incidents-email-notification-settings.png":::

5. Sélectionnez **Suivant**. Dans la page **Destinataires** , ajoutez les adresses e-mail qui recevront les notifications d’incident. Sélectionnez **Ajouter** après avoir tapé chaque nouvelle adresse e-mail. Pour tester les notifications et vous assurer que les destinataires les reçoivent dans les boîtes de réception, sélectionnez **Envoyer un e-mail de test**.
6. Sélectionnez **Suivant**. Dans la page **Vérifier la règle** , passez en revue les paramètres de la règle, puis sélectionnez **Créer une règle**. Les destinataires commencent à recevoir des notifications d’incident par e-mail en fonction des paramètres.

Pour modifier une règle existante, sélectionnez-la dans la liste des règles. Dans le volet avec le nom de la règle, sélectionnez **Modifier la règle et apportez** vos modifications dans les pages **Informations de base**, **Paramètres de notification** et **Destinataires** .

Pour supprimer une règle, sélectionnez-la dans la liste des règles. Dans le volet avec le nom de la règle, sélectionnez **Supprimer**.

Une fois que vous recevez la notification, vous pouvez accéder directement à l’incident et commencer votre enquête immédiatement. Pour plus d’informations sur l’examen des incidents, consultez [Examiner les incidents dans Microsoft 365 Defender](investigate-incidents.md).

## <a name="training-for-security-analysts"></a>Formation pour les analystes de sécurité

Utilisez ce module d’apprentissage de Microsoft Learn pour comprendre comment utiliser Microsoft 365 Defender pour gérer les incidents et les alertes.

|Formation :|Examiner les incidents avec Microsoft 365 Defender|
|---|---|
|![Examiner les incidents avec Microsoft 365 Defender’icône de formation.](../../media/incidents-overview/m365-defender-address-security-investigation.svg)| Microsoft 365 Defender unifie les données sur les menaces de plusieurs services et utilise l’IA pour les combiner en incidents et alertes. Découvrez comment réduire le temps entre un incident et sa gestion pour sa prochaine réponse et résolution. <p> 27 min - 6 unités |

> [!div class="nextstepaction"]
> [Démarrer >](/training/modules/defender-investigate-incidents/)

## <a name="next-steps"></a>Prochaines étapes

Utilisez les étapes répertoriées en fonction de votre niveau d’expérience ou de votre rôle au sein de votre équipe de sécurité.

### <a name="experience-level"></a>Niveau d’expérience

Suivez ce tableau pour connaître votre niveau d’expérience en matière d’analyse de la sécurité et de réponse aux incidents.

| Niveau | Étapes |
|:-------|:-----|
| **New** | <ol><li> Consultez la [procédure pas à pas Répondre à votre premier incident](first-incident-overview.md) pour obtenir une visite guidée d’un processus classique d’analyse, de correction et de révision post-incident dans le portail Microsoft 365 Defender avec un exemple d’attaque. </li><li> Déterminez quels incidents doivent être [classés par ordre de priorité](incident-queue.md) en fonction de la gravité et d’autres facteurs. </li><li> [Gérez les incidents](manage-incidents.md), ce qui inclut le changement de nom, l’affectation, la classification et l’ajout d’étiquettes et de commentaires en fonction de votre workflow de gestion des incidents.</li></ol> |
| **Expérimenté** | <ol><li> Commencez à utiliser la file d’attente des incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. Vous pouvez alors effectuer les opérations suivantes : </li> <ul><li> Déterminez quels incidents doivent être [classés par ordre de priorité](incident-queue.md) en fonction de la gravité et d’autres facteurs. </li><li> [Gérez les incidents](manage-incidents.md), ce qui inclut le changement de nom, l’affectation, la classification et l’ajout d’étiquettes et de commentaires en fonction de votre workflow de gestion des incidents. </li><li> Effectuer [des enquêtes sur](investigate-incidents.md) les incidents. </li></ul> </li><li> Suivez et répondez aux menaces émergentes avec [l’analyse des menaces](threat-analytics.md). </li><li>  Chassez de manière proactive les menaces avec la [chasse avancée aux menaces](advanced-hunting-overview.md). </li><li> Consultez ces [playbooks de réponse aux incidents](/security/compass/incident-response-playbooks) pour obtenir des conseils détaillés sur le hameçonnage, la pulvérisation de mot de passe et les attaques d’octroi de consentement d’application. </li></ol> |

### <a name="security-team-role"></a>Rôle d’équipe de sécurité

Suivez ce tableau en fonction de votre rôle d’équipe de sécurité.

| Rôle | Étapes |
|---|---|
| Répondeur aux incidents (niveau 1) | Commencez à utiliser la file d’attente des incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. Vous pouvez alors effectuer les opérations suivantes : <ul><li> Déterminez quels incidents doivent être [classés par ordre de priorité](incident-queue.md) en fonction de la gravité et d’autres facteurs. </li><li> [Gérez les incidents](manage-incidents.md), ce qui inclut le changement de nom, l’affectation, la classification et l’ajout d’étiquettes et de commentaires en fonction de votre workflow de gestion des incidents. </li></ul> |
| Enquêteur ou analyste de sécurité (niveau 2) | <ol><li> Effectuez [des enquêtes sur](investigate-incidents.md) les incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. </li><li> Consultez ces [playbooks de réponse aux incidents](/security/compass/incident-response-playbooks) pour obtenir des conseils détaillés sur le hameçonnage, la pulvérisation de mot de passe et les attaques d’octroi de consentement d’application. </li></ol> |
| Analyste de sécurité avancé ou chasseur de menaces (niveau 3) | <ol><li>Effectuez [des enquêtes sur](investigate-incidents.md) les incidents à partir de la page **Incidents** du portail Microsoft 365 Defender. </li><li> Suivez et répondez aux menaces émergentes avec [l’analyse des menaces](threat-analytics.md). </li><li> Chassez de manière proactive les menaces avec la [chasse avancée aux menaces](advanced-hunting-overview.md). </li><li> Consultez ces [playbooks de réponse aux incidents](/security/compass/incident-response-playbooks) pour obtenir des conseils détaillés sur le hameçonnage, la pulvérisation de mot de passe et les attaques d’octroi de consentement d’application. |
| Responsable SOC | Découvrez comment [intégrer Microsoft 365 Defender à votre Centre des opérations de sécurité (SOC).](integrate-microsoft-365-defender-secops.md) |
