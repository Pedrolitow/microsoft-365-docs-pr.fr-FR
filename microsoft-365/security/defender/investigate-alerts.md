---
title: Examiner les alertes dans Microsoft 365 Defender
description: Examinez les alertes vues sur les appareils, les utilisateurs et les boîtes aux lettres.
keywords: incidents, alertes, examiner, analyser, réponse, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte aux lettres, e-mail, 365, microsoft, m365
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
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
search.appverid:
- MOE150
ms.openlocfilehash: 18010826e9db2d325205d255395a4eb4df6d417e
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67474597"
---
# <a name="investigate-alerts-in-microsoft-365-defender"></a>Examiner les alertes dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- Microsoft 365 Defender

>[!Note]
>Cet article décrit les alertes de sécurité dans Microsoft 365 Defender. Toutefois, vous pouvez utiliser des alertes d’activité pour envoyer des notifications par e-mail à vous-même ou à d’autres administrateurs lorsque les utilisateurs effectuent des activités spécifiques dans Microsoft 365. Pour plus d’informations, consultez [Créer des alertes d’activité - Microsoft Purview | Microsoft Docs](../../compliance/create-activity-alerts.md).

Les alertes sont la base de tous les incidents et indiquent l’occurrence d’événements malveillants ou suspects dans votre environnement. Les alertes font généralement partie d’une attaque plus large et fournissent des indices sur un incident.

Dans Microsoft 365 Defender, les alertes associées sont agrégées pour former [des incidents](incidents-overview.md). Les incidents fournissent toujours le contexte plus large d’une attaque. Toutefois, l’analyse des alertes peut être utile lorsque des analyses plus approfondies sont nécessaires.

La **file d’attente Alertes** affiche l’ensemble actuel d’alertes. Vous accédez à la file d’attente d’alertes à partir **des incidents & alertes > alertes** lors du lancement rapide du [portail Microsoft 365 Defender](https://go.microsoft.com/fwlink/p/?linkid=2077139).

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-queue.png" alt-text="Section Alertes dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-queue.png":::

Les alertes provenant de différentes solutions de sécurité Microsoft telles que Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365 et Microsoft 365 Defender apparaissent ici.

Par défaut, la file d’attente d’alertes dans le portail Microsoft 365 Defender affiche les alertes nouvelles et en cours des 30 derniers jours. L’alerte la plus récente se trouve en haut de la liste pour que vous puissiez la voir en premier. 

Dans la file d’attente d’alertes par défaut, vous pouvez sélectionner **Filtrer** pour afficher un volet **Filtre** , à partir duquel vous pouvez spécifier un sous-ensemble des alertes. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-filter.png" alt-text="Section Filtres dans le portail Microsoft 365 Defender." lightbox="../../media/investigate-alerts/alerts-ss-alerts-filter.png":::

Vous pouvez filtrer les alertes en fonction des critères suivants :

- Severity
- État
- Sources de service
- Entités (ressources impactées)
- État d’investigation automatisé

## <a name="required-roles-for-defender-for-office-365-alerts"></a>Rôles requis pour les alertes Defender pour Office 365

Vous devez avoir l’un des rôles suivants pour accéder à Microsoft Defender pour Office 365 alertes :

- Pour les rôles globaux Azure Active Directory (Azure AD) :

   - Administrateur général

   - Administrateur de sécurité

   - Opérateur de sécurité

   - Lecteur général

   - Lecteur de sécurité

- Office 365 groupes de rôles de conformité & de sécurité

   - Administrateur de conformité

   - Gestion de l’organisation 

- Un [rôle personnalisé](custom-roles.md)

## <a name="analyze-an-alert"></a>Analyser une alerte

Pour afficher la page d’alerte principale, sélectionnez le nom de l’alerte. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-main.png" alt-text="Détails d’une alerte dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-main.png":::

Vous pouvez également sélectionner l’action **Ouvrir la page d’alerte principale** dans le volet **Gérer les alertes** .

Une page d’alerte est composée des sections suivantes : 

- Histoire d’alerte, qui est la chaîne d’événements et d’alertes liés à cette alerte dans l’ordre chronologique
- Détails du résumé

Dans une page d’alerte, vous pouvez sélectionner les points de suspension (**...**) en regard de n’importe quelle entité pour afficher les actions disponibles, telles que la liaison de l’alerte à un autre incident. La liste des actions disponibles dépend du type d’alerte.

### <a name="alert-sources"></a>Sources d’alerte

Microsoft 365 Defender alertes peuvent provenir de solutions telles que Microsoft Defender pour point de terminaison, Microsoft Defender pour Office 365, Microsoft Defender for Cloud Apps et le module complémentaire de gouvernance des applications pour Microsoft Defender for Cloud Apps. Vous remarquerez peut-être des alertes avec des caractères ajoutés dans l’alerte. Le tableau suivant fournit des conseils pour vous aider à comprendre le mappage des sources d’alerte en fonction du caractère ajouté sur l’alerte.

> [!NOTE]
> - Les GUID ajoutés sont spécifiques uniquement aux expériences unifiées telles que la file d’attente des alertes unifiées, la page des alertes unifiées, l’investigation unifiée et l’incident unifié.
> - Le caractère ajouté ne modifie pas le GUID de l’alerte. La seule modification apportée au GUID est le composant ajouté.

| Source de l’alerte | Caractère ajouté |
| :---|:--- |
| Microsoft Defender pour Office 365 | `fa{GUID}` <br> Exemple : `fa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender pour point de terminaison | `da` ou `ed` pour les alertes de détection personnalisées <br> |
| Microsoft Defender pour l’identité | `aa{GUID}` <br> Exemple : `aa123a456b-c789-1d2e-12f1g33h445h6i` |
| Microsoft Defender for Cloud Apps |`ca{GUID}` <br> Exemple : `ca123a456b-c789-1d2e-12f1g33h445h6i` |

### <a name="analyze-affected-assets"></a>Analyser les ressources affectées

La section **Actions effectuées** contient une liste des ressources affectées, telles que les boîtes aux lettres, les appareils et les utilisateurs affectés par cette alerte. 

Vous pouvez également sélectionner **Afficher dans le centre d’actions** pour afficher l’onglet **Historique** du **centre d’actions** dans le portail Microsoft 365 Defender.

### <a name="trace-an-alerts-role-in-the-alert-story"></a>Suivre le rôle d’une alerte dans l’histoire de l’alerte

L’article d’alerte affiche toutes les ressources ou entités associées à l’alerte dans une arborescence de processus. L’alerte dans le titre est celle en question lorsque vous accédez pour la première fois à la page de l’alerte sélectionnée. Les ressources de l’article d’alerte sont extensibles et accessibles en un clic. Ils fournissent des informations supplémentaires et accélèrent votre réponse en vous permettant d’agir correctement dans le contexte de la page d’alerte. 

> [!NOTE]
> La section d’histoire des alertes peut contenir plusieurs alertes, avec des alertes supplémentaires liées à l’arborescence d’exécution qui s’affiche avant ou après l’alerte que vous avez sélectionnée.

### <a name="view-more-alert-information-on-the-details-page"></a>Afficher plus d’informations sur les alertes sur la page de détails

La page de détails affiche les détails de l’alerte sélectionnée, avec les détails et les actions qui y sont associés. Si vous sélectionnez l’une des ressources ou entités affectées dans l’article d’alerte, la page de détails change pour fournir des informations contextuelles et des actions pour l’objet sélectionné.

Une fois que vous avez sélectionné une entité d’intérêt, la page de détails change pour afficher des informations sur le type d’entité sélectionné, des informations historiques lorsqu’elle est disponible et des options d’action sur cette entité directement à partir de la page d’alerte.

## <a name="manage-alerts"></a>Gérer des alertes

Pour gérer une alerte, sélectionnez **Gérer l’alerte** dans la section Résumé des détails de la page d’alerte. Pour une seule alerte, voici un exemple du volet **Gérer l’alerte** .

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage.png" alt-text="Section Gérer les alertes dans le portail Microsoft 365 Defender" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage.png":::

Le volet **Gérer les alertes** vous permet d’afficher ou de spécifier :

- État de l’alerte (Nouveau, Résolu, En cours).
- Compte d’utilisateur auquel l’alerte a été attribuée.
- Classification de l’alerte :
     - **Non défini** (valeur par défaut).
     - **Vrai positif** avec un type de menace. Utilisez cette classification pour les alertes qui indiquent avec précision une menace réelle. Si vous spécifiez ce type de menace, votre équipe de sécurité voit les modèles de menaces et agit pour défendre votre organisation contre elles.
     - **Activité informationnelle attendue** avec un type d’activité. Utilisez cette option pour les alertes qui sont techniquement précises, mais qui représentent un comportement normal ou une activité de menace simulée. Vous souhaitez généralement ignorer ces alertes, mais attendez-vous à ce qu’elles soient similaires à l’avenir, où les activités sont déclenchées par des attaquants ou des programmes malveillants réels. Utilisez les options de cette catégorie pour classer les alertes pour les tests de sécurité, l’activité de l’équipe rouge et le comportement inhabituel attendu des applications et des utilisateurs approuvés.
     - **Faux positif** pour les types d’alertes qui ont été créés même en l’absence d’activité malveillante ou pour une fausse alerte. Utilisez les options de cette catégorie pour classer les alertes identifiées par erreur comme des événements ou des activités normaux comme malveillants ou suspects. Contrairement aux alertes pour l'« activité informationnelle et attendue », qui peuvent également être utiles pour intercepter les menaces réelles, vous ne souhaitez généralement pas voir ces alertes à nouveau. La classification des alertes en tant que faux positifs permet Microsoft 365 Defender d’améliorer sa qualité de détection.
- Commentaire sur l’alerte.

>[!NOTE]
> Vers le 29 août 2022, les valeurs de détermination d’alerte précédemment prises en charge (« Apt » et « SecurityPersonnel ») seront déconseillées et ne seront plus disponibles via l’API.

> [!NOTE]
> Une façon de gérer les alertes via l’utilisation de balises. La fonctionnalité d’étiquetage pour Microsoft Defender pour Office 365 est déployée de façon incrémentielle et est actuellement en préversion. <br>
> Actuellement, les noms de balise modifiés sont appliqués uniquement aux alertes créées *après* la mise à jour. Les alertes qui ont été générées avant la modification ne reflètent pas le nom de balise mis à jour. 

Pour gérer un *ensemble d’alertes similaire à une alerte spécifique*, sélectionnez **Afficher des alertes similaires** dans la zone **Insight** dans la section Détails du résumé de la page d’alerte.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-manage-select.png" alt-text="Gérer une alerte dans le portail Microsoft 365 Defender":::

Dans le volet **Gérer les alertes** , vous pouvez ensuite classer toutes les alertes associées en même temps. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-select-related.png" alt-text="Gestion des alertes associées dans le portail Microsoft 365 Defender":::

Si des alertes similaires ont déjà été classifiées dans le passé, vous pouvez gagner du temps en utilisant Microsoft 365 Defender recommandations pour découvrir comment les autres alertes ont été résolues. Dans la section Détails du résumé, sélectionnez **Recommandations**.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations.png" alt-text="Exemple de sélection de recommandations pour une alerte":::

**L’onglet Recommandations** fournit les actions et conseils suivants pour l’examen, la correction et la prévention. Voici un exemple.

:::image type="content" source="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" lightbox="../../media/investigate-alerts/alerts-ss-alerts-recommendations-example.png" alt-text="Exemple de recommandations d’alerte":::

 
## <a name="suppress-an-alert"></a>Supprimer une alerte

En tant qu’analyste soc (Security Operations Center), l’un des principaux problèmes consiste à trier le nombre d’alertes déclenchées quotidiennement. Pour les alertes de priorité inférieure, un analyste est toujours requis pour trier et résoudre l’alerte qui tend à être un processus manuel. Le temps d’un analyste SOC est précieux, car il souhaite se concentrer uniquement sur les alertes de gravité élevée et de priorité élevée.

La suppression des alertes permet d’ajuster et de gérer les alertes à l’avance. Cela simplifie la file d’attente des alertes et permet de gagner du temps en masquant ou en résolvant automatiquement les alertes, chaque fois qu’un comportement organisationnel attendu se produit et que les conditions de règle sont remplies. 

Vous pouvez créer des conditions de règle basées sur des « types de preuves » tels que des fichiers, des processus, des tâches planifiées et de nombreux autres types de preuves qui déclenchent l’alerte. Après avoir créé la règle, l’utilisateur peut appliquer la règle sur l’alerte sélectionnée ou sur tout type d’alerte qui remplit les conditions de règle pour supprimer l’alerte. 

> [!NOTE]
> La suppression des alertes n’est pas recommandée. Toutefois, dans certaines situations, une application métier interne connue ou des tests de sécurité déclenchent une activité attendue et vous ne souhaitez pas voir ces alertes. Vous pouvez donc créer une règle de suppression pour l’alerte. 

### <a name="create-rule-conditions-to-suppress-alerts"></a>Créer des conditions de règle pour supprimer des alertes

Pour créer une règle de suppression pour les alertes :

1. Sélectionnez l’alerte examinée. Dans la page d’alerte principale, sélectionnez **Créer une règle de suppression** dans la section Détails du résumé de la page d’alerte. 

    :::image type="content" source="../../media/investigate-alerts/suppression-click.png" lightbox="../../media/investigate-alerts/suppression-click.png" alt-text="Capture d’écran de l’action Créer une règle de séparation.":::

2. Dans le volet **Créer une règle de suppression** , sélectionnez **uniquement ce type d’alerte** pour appliquer la règle à l’alerte sélectionnée.

    Toutefois, pour appliquer la règle sur n’importe quel type d’alerte qui répond aux conditions de règle, sélectionnez **N’importe quel type d’alerte en fonction des conditions IOC**.
 
    Les EIC sont des indicateurs tels que des fichiers, des processus, des tâches planifiées et d’autres types de preuves qui déclenchent l’alerte.
    
    > [!NOTE]
    > Vous ne pouvez plus supprimer une alerte déclenchée par la source de « détection personnalisée ». Vous ne pouvez pas créer de règle de suppression pour cette alerte.
     
3. Dans la section **IOCs** , sélectionnez **N’importe quel IOC** pour supprimer l’alerte, quelle que soit la « preuve » à l’origine de l’alerte. 

    Pour définir plusieurs conditions de règle, **sélectionnez Choisir les E/S**. Utilisez **AND**, **OU** et les options de regroupement pour créer une relation entre ces plusieurs « types de preuves » à l’origine de l’alerte.
 
    1. Par exemple, dans la section **Conditions** , sélectionnez le **rôle d’entité** de preuve de déclenchement : Déclencheur, **Égal à** , puis sélectionnez le type de preuve dans la liste déroulante. 

    :::image type="content" source="../../media/investigate-alerts/evidence-types-drop-down-list.png" alt-text="Capture d’écran de la liste déroulante des types de preuves." lightbox="../../media/investigate-alerts/evidence-types-drop-down-list.png":::

    2. Toutes les propriétés de cette « preuve » sont automatiquement renseignées en tant que nouveau sous-groupe dans les champs respectifs ci-dessous.
    :::image type="content" source="../../media/investigate-alerts/properties-evidence.png" alt-text="Capture d’écran des propriétés du remplissage automatique des preuves." lightbox="../../media/investigate-alerts/properties-evidence.png" :::

    > [!NOTE]
    > Les valeurs de condition ne respectent pas la casse. 

    3. Vous pouvez modifier et/ou supprimer les propriétés de cette « preuve » en fonction de vos besoins (à l’aide de caractères génériques, quand cela est pris en charge).

    4. Outre les fichiers et les processus, le script AMSI (AntiMalware Scan Interface), l’événement WMI (Windows Management Instrumentation) et les tâches planifiées sont quelques-uns des types de preuves que vous pouvez sélectionner dans la liste déroulante des types de preuves.
    :::image type="content" source="../../media/investigate-alerts/other-evidence-types.png" alt-text="Capture d’écran d’autres types de preuves." lightbox="../../media/investigate-alerts/other-evidence-types.png":::
    
    5. Pour ajouter un autre IOC, cliquez sur **Ajouter un filtre**. 
    > [!NOTE]
    > L’ajout d’au moins un IOC à la condition de règle est nécessaire pour supprimer tout type d’alerte.
    
4. Vous pouvez également sélectionner **Remplir automatiquement toutes les E/S associées à l’alerte 7** dans la section **IOC** pour ajouter tous les types de preuves liés à l’alerte et leurs propriétés à la fois dans la section **Conditions** .
    :::image type="content" source="../../media/investigate-alerts/autofill-iocs.png" alt-text="Capture d’écran du remplissage automatique de toutes les E/S liées aux alertes." lightbox="../../media/investigate-alerts/autofill-iocs.png":::

5. Dans la section **Étendue** , définissez l’étendue dans la sous-section **Conditions** en sélectionnant un appareil spécifique, plusieurs appareils, groupes d’appareils, l’ensemble de l’organisation ou par utilisateur.
    > [!NOTE]
    > Vous devez avoir Administration autorisation lorsque **l’étendue** est définie uniquement pour **l’utilisateur**. Administration autorisation n’est pas requise lorsque **l’étendue** est définie pour **l’utilisateur** avec **l’appareil**, les **groupes d’appareils**.

:::image type="content" source="../../media/investigate-alerts/suppression-choose-scope.png" lightbox="../../media/investigate-alerts/suppression-choose-scope.png" alt-text="Capture d’écran du volet Créer une règle de suppression : Conditions, Étendue, Action.":::
 
6. Dans la section **Action** , effectuez l’action appropriée : **Masquer l’alerte** ou **Résoudre l’alerte**.
    Entrez **Nom**, **Commentaire**, puis cliquez sur **Enregistrer**.

7. **Empêchez le blocage des E/S par la suite :**<br>
Une fois que vous avez enregistré la règle de suppression, dans la page de **création de la règle de suppression réussie** qui s’affiche, vous pouvez ajouter les IOC sélectionnés en tant qu’indicateurs à la « liste verte » et les empêcher d’être bloqués à l’avenir. <br>
Toutes les E/S liées aux alertes s’affichent dans la liste. <br>
Les E/S sélectionnées dans les conditions de suppression sont sélectionnées par défaut.
      1. Par exemple, vous pouvez ajouter des fichiers à autoriser à la **preuve Select (IOC) à autoriser**. Par défaut, le fichier qui a déclenché l’alerte est sélectionné.
      1. Entrez l’étendue de **l’étendue Select à appliquer**. Par défaut, l’étendue de l’alerte associée est sélectionnée.
      1. Cliquez sur **Enregistrer**. À présent, le fichier n’est pas bloqué, car il figure dans la liste verte.

    :::image type="content" source="../../media/investigate-alerts/suppression-2-choose-iocs.png" lightbox="../../media/investigate-alerts/suppression-2-choose-iocs.png" alt-text="Capture d’écran de la création d’une règle de suppression réussie. ":::

8.  La nouvelle fonctionnalité d’alerte de suppression est disponible par défaut. <br> Toutefois, vous pouvez revenir à l’expérience précédente dans Microsoft 365 Defender portail en accédant à **Paramètres > points de terminaison > suppression d’alerte**, puis désactiver la **création de nouvelles règles de suppression activée** pour activer le basculement. 

 
    :::image type="content" source="../../media/investigate-alerts/suppression-toggle.png" lightbox="../../media/investigate-alerts/suppression-toggle.png" alt-text="Capture d’écran du bouton bascule pour activer/désactiver la fonctionnalité de création de règles de suppression.":::
    > [!NOTE]
    > Bientôt, seule la nouvelle expérience de suppression d’alerte sera disponible. Vous ne pourrez pas revenir à l’expérience précédente.

9.  **Modifiez les règles existantes :** <br> Vous pouvez toujours ajouter ou modifier les conditions de règle et l’étendue des règles nouvelles ou existantes dans le portail Microsoft Defender, en sélectionnant la règle appropriée et en cliquant sur **Modifier la règle**.    
    Pour modifier des règles existantes, **assurez-vous que la création de nouvelles règles de suppression activée** bascule est activée.         

    :::image type="content" source="../../media/investigate-alerts/suppression-toggle-on-edit.png" lightbox="../../media/investigate-alerts/suppression-toggle-on-edit.png" alt-text="Capture d’écran de la règle de suppression de modification.":::
  
## <a name="resolve-an-alert"></a>Résoudre une alerte

Une fois que vous avez terminé l’analyse d’une alerte et qu’elle peut être résolue, accédez au volet **Gérer les alertes** pour l’alerte ou des alertes similaires et marquez l’état **comme Résolu** , puis classifiez-le comme **vrai positif** avec un type de menace, une **activité informationnelle, attendue** avec un type d’activité ou un **Faux positif**.

La classification des alertes permet Microsoft 365 Defender améliorer sa qualité de détection.

## <a name="use-power-automate-to-triage-alerts"></a>Utiliser Power Automate pour trier les alertes

Les équipes d’opérations de sécurité modernes (SecOps) ont besoin d’automatisation pour fonctionner efficacement. Pour se concentrer sur la chasse et l’examen des menaces réelles, les équipes SecOps utilisent Power Automate pour trier la liste des alertes et éliminer celles qui ne sont pas des menaces.  

### <a name="criteria-for-resolving-alerts"></a>Critères de résolution des alertes

- Un message d’absence du bureau est activé

- L’utilisateur n’est pas marqué comme étant à risque élevé

Si les deux sont vraies, SecOps marque l’alerte comme voyage légitime et la résout. Une notification est publiée dans Microsoft Teams une fois l’alerte résolue.

### <a name="connect-power-automate-to-microsoft-defender-for-cloud-apps"></a>Connecter Power Automate à Microsoft Defender for Cloud Apps

Pour créer l’automatisation, vous aurez besoin d’un jeton d’API avant de pouvoir connecter Power Automate à Microsoft Defender for Cloud Apps.

1. Cliquez sur **Paramètres**, sélectionnez **Extensions de sécurité**, puis cliquez sur **Ajouter un jeton** dans l’onglet **Jetons d’API** .

2. Indiquez un nom pour votre jeton, puis cliquez sur **Générer**. Enregistrez le jeton car vous en aurez besoin ultérieurement.

### <a name="create-an-automated-flow"></a>Créer un flux automatisé

Regardez cette courte vidéo pour découvrir comment l’automatisation fonctionne efficacement pour créer un flux de travail fluide et comment connecter Power Automate à Defender pour Cloud Apps. 
> [!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RWFIRn]

## <a name="next-steps"></a>Prochaines étapes

Si nécessaire pour les incidents in-process, poursuivez votre [enquête](investigate-incidents.md).

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Gérer des incidents](manage-incidents.md)
- [Examiner des incidents](investigate-incidents.md)
- [Examiner les incidents de perte de données](investigate-dlp.md)