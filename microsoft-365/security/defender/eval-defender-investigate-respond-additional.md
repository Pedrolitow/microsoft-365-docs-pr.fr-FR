---
title: Essayer Microsoft 365 Defender fonctionnalités de réponse aux incidents dans un environnement pilote
description: Essayez les fonctionnalités de réponse aux incidents Microsoft 365 Defender pour hiérarchiser et gérer les incidents, automatiser les enquêtes et utiliser le repérage avancé dans la détection des menaces.
keywords: Microsoft 365 Defender essai, essayez Microsoft 365 Defender, évaluez Microsoft 365 Defender, laboratoire d’évaluation Microsoft 365 Defender, pilote Microsoft 365 Defender, cybersécurité, menace avancée persistante, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
localization_priority: Normal
ms.author: josephd
author: JoeDavies-MSFT
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-overview
- m365solution-evalutatemtp
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 7338292b784cdad17548efc3dd148f3ea6a72b28
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58568263"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>Essayer Microsoft 365 Defender fonctionnalités de réponse aux incidents dans un environnement pilote

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-investigate-respond.md) dans le processus d’examen et de réponse d’un incident Microsoft 365 Defender l’aide d’un environnement pilote. Pour plus d’informations sur ce processus, consultez l’article [de](eval-defender-investigate-respond.md) présentation.

Une fois que vous avez effectué une réponse [aux incidents](eval-defender-investigate-respond-simulate-attack.md)pour une attaque simulée, voici quelques fonctionnalités Microsoft 365 Defender à explorer :

|Fonctionnalité |Description |
|:-------|:-----|
| [Hiérarchiser les incidents](#prioritize-incidents) | Utilisez le filtrage et le tri de la file d’attente des incidents pour déterminer les incidents à traiter par la suite. |
| [Gérer des incidents](#manage-incidents) | Modifier les propriétés d’incident pour garantir une affectation correcte, ajouter des balises et des commentaires et résoudre un incident. |
| [Examen et réponse automatisés](#examine-automated-investigation-and-response-with-the-action-center) | Fonctionnalités d’investigation et de réponse automatisées (AIR) qui peuvent aider votre équipe des opérations de sécurité à gérer les menaces plus efficacement. Le centre de mise en œuvre est une expérience de « volet unique » pour les tâches d’incident et d’alerte, telles que l’approbation des actions de correction en attente. |
| [Repérage avancé](#advanced-hunting) | Outil de recherche de menace basé sur une requête qui vous permet d’inspecter de manière proactive les événements de votre réseau et de localiser les indicateurs et entités de menace. Vous utilisez également la recherche avancée pendant l’examen et la correction d’un incident. |


## <a name="prioritize-incidents"></a>Hiérarchiser les incidents

Vous pouvez vous rendre dans la file d’attente des incidents à partir **d’incidents & alertes** > Incidents sur le lancement rapide du portail Microsoft 365 Defender ([security.microsoft.com](https://security.microsoft.com)). Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Exemple de file d’attente d’incident.":::

La section **Incidents et alertes** les plus récents présente un graphique du nombre d’alertes reçues et d’incidents créés au cours des dernières 24 heures.

Pour examiner la liste des incidents et hiérarchiser leur importance pour l’affectation et l’examen, vous pouvez : 

- Configurez des colonnes personnalisables **(sélectionnez** Sélectionner des colonnes) pour vous donner une visibilité sur les différentes caractéristiques de l’incident ou des entités impactées. Cela vous permet de prendre une décision éclairée concernant la hiérquage des incidents à analyser.

- Utilisez le filtrage pour vous concentrer sur un scénario ou une menace spécifique. L’application de filtres à la file d’attente d’incidents peut aider à déterminer les incidents qui nécessitent une attention immédiate. 

Dans la file d’attente des incidents par défaut, sélectionnez **Filtres** pour voir un volet **Filtres,** à partir duquel vous pouvez spécifier un ensemble spécifique d’incidents. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Exemple du volet filtres de la file d’attente des incidents.":::

Pour plus d’informations, voir [Hiérarchiser les incidents.](incident-queue.md)

## <a name="manage-incidents"></a>Gérer les incidents

Vous pouvez gérer les incidents à partir du **volet Gérer les incidents** pour un incident. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Exemple du volet Gérer les incidents d’un incident.":::

Vous pouvez afficher ce volet à partir du lien **Gérer l’incident** sur :

- Volet des propriétés d’un incident dans la file d’attente des incidents.
- **Page récapitulatif** d’un incident.

Voici comment gérer vos incidents :

- Modifier le nom de l’incident

  Modifiez le nom attribué de manière utomatically en fonction des meilleures pratiques de votre équipe de sécurité.
  
- Ajouter des balises d’incident

  Ajoutez des balises que votre équipe de sécurité utilise pour classer les incidents, qui peuvent être filtrés ultérieurement.
  
- Affectez l’incident à vous-même

  Affectez-le au nom de votre compte d’utilisateur, qui peut être filtré ultérieurement.
  
- Résoudre un incident

  Fermez l’incident une fois qu’il a été corrigé.
  
- Définir sa classification et sa détermination

  Classifiez et sélectionnez le type de menace lorsque vous résolvez un incident.
  
- Ajouter des commentaires

  Utilisez des commentaires pour l’avancement, des notes ou d’autres informations en fonction des meilleures pratiques de votre équipe de sécurité. L’historique complet des commentaires est disponible à partir de l’option **Commentaires** et historique dans la page de détails d’un incident.

Pour plus d’informations, [voir Gérer les incidents.](manage-incidents.md)

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>Examiner l’examen et la réponse automatisés avec le centre de gestion de l’action

Selon la façon dont les fonctionnalités d’examen et de réponse automatisées sont configurées pour votre organisation, des mesures correctives sont prises automatiquement ou uniquement après approbation par votre équipe des opérations de sécurité. Toutes les actions, qu’elles soient en [](m365d-action-center.md)attente ou terminées, sont répertoriées dans le centre de mise en œuvre, qui répertorie les actions de correction en attente et terminées pour vos appareils, le contenu de collaboration des & de messagerie électronique et les identités dans un seul emplacement.

Voici un exemple.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centre de l’action unifiée dans Microsoft 365 Defender.":::

Dans le centre de l’action, vous pouvez sélectionner les actions en attente, puis les approuver ou les rejeter dans le volet volant. Voici un exemple.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Approuver ou rejeter une action.":::

Approuver (ou rejeter) les actions en attente dès que possible afin que vos enquêtes automatisées se poursuivent et se terminent en temps voulu.

Pour plus d’informations, voir [Centre d’enquête](m365d-autoir.md) et de réponse [automatisé.](m365d-action-center.md)

## <a name="advanced-hunting"></a>Repérage avancé

> [!NOTE]
> Avant de vous suivre dans la simulation de recherche avancée, regardez la vidéo suivante pour comprendre les concepts de recherche avancés, voir où vous pouvez le trouver dans le portail et savoir comment cela peut vous aider dans vos opérations de sécurité.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


Si la simulation d’attaque [PowerShell](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) sans fichier facultative était une attaque réelle qui avait déjà atteint la phase d’accès aux informations d’identification, vous pouvez utiliser le recherche avancée à tout moment dans l’examen pour rechercher de manière proactive les événements et les enregistrements dans le réseau à l’aide de ce que vous connaissez déjà des alertes générées et des entités affectées. 

Par exemple, en fonction des informations de l’alerte de reconnaissance d’adresses IP et d’utilisateurs [(SMB),](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity) vous pouvez utiliser le tableau pour rechercher tous les événements d’éumération de session SMB ou rechercher d’autres activités de découverte dans différents autres protocoles dans Microsoft Defender pour les données d’identité à l’aide du `IdentityDirectoryEvents` `IdentityQueryEvents` tableau.


### <a name="hunting-environment-requirements"></a>Conditions requises pour l’environnement de recherche

Une seule boîte aux lettres et périphérique interne est requis pour cette simulation. Vous aurez également besoin d’un compte de messagerie externe pour envoyer le message de test.

1. Vérifiez que votre client a [activé Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Identifiez une boîte aux lettres cible à utiliser pour recevoir des messages électroniques.

   - Cette boîte aux lettres doit être surveillée par Microsoft Defender pour Office 365

   - L’appareil de la condition 3 doit accéder à cette boîte aux lettres

3. Configurez un périphérique de test :

    a. Assurez-vous que vous utilisez Windows 10 version 1903 ou ultérieure.

    b. Associez le périphérique de test au domaine de test.

    c. [Activer Antivirus Windows Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Si vous avez des difficultés à activer Antivirus Windows Defender, consultez [cette rubrique de résolution des problèmes.](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-windows-defender-antivirus-is-not-disabled-by-a-policy)

    d. [Intégration à Microsoft Defender pour point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)

### <a name="run-the-simulation"></a>Exécuter la simulation

1. À partir d’un compte de messagerie externe, envoyez un courrier électronique à la boîte aux lettres identifiée à l’étape 2 de la section des exigences de l’environnement de recherche. Inclure une pièce jointe qui sera autorisée par le biais de toutes les stratégies de filtrage de courrier électronique existantes. Ce fichier n’a pas besoin d’être malveillant ou exécutable. Les types de fichiers suggérés <i>sont.pdf, </i> <i>.exe</i> (si autorisé) ou un type Office de document tel qu’un fichier Word.

2. Ouvrez le courrier électronique envoyé à partir de l’appareil configuré comme défini à l’étape 3 de la section des conditions requises pour l’environnement de recherche. Ouvrez la pièce jointe ou enregistrez le fichier sur l’appareil.

#### <a name="go-hunting"></a>Aller au chasse

1. Ouvrez [le Microsoft 365 Defender.](https://security.microsoft.com/)

2. Dans le volet de navigation, sélectionnez **Hunting > Advanced hunting**.

3. Créez une requête qui commence par collecter des événements de courrier électronique.

   1. Select **Query > New**.

   1. Dans les **groupes de** messagerie sous **Recherche avancée,** double-cliquez **sur EmailEvents**. Vous devriez le voir dans la fenêtre de requête.

      ```console
      EmailEvents
      ```

   1. Modifiez la période de la requête sur les dernières 24 heures. En supposant que l’e-mail que vous avez envoyé lorsque vous avez lancé la simulation ci-dessus se trouvait au cours des dernières 24 heures, sinon, modifiez la période si nécessaire.

   1. Sélectionnez **Exécuter la requête**. Vous pouvez obtenir des résultats différents en fonction de votre environnement pilote.

      > [!NOTE]
      > Consultez l’étape suivante pour les options de filtrage pour limiter le retour de données.

      ![Exemple de résultats de requête de recherche avancée.](../../media/mtp/fig19.png)

        > [!NOTE]
        > Le recherche avancée affiche les résultats de la requête sous la mesure de données tabulaires. Vous pouvez également choisir d’afficher les données dans d’autres types de formats tels que les graphiques.

   1. Consultez les résultats et déterminez si vous pouvez identifier l’e-mail que vous avez ouvert. L’exposition du message dans un recherche avancée peut prendre jusqu’à deux heures. Pour affiner les résultats, vous pouvez ajouter la condition **where** à votre requête pour rechercher uniquement les e-mails dont le domaine SenderMailFromDomain est « yahoo.com ». Voici un exemple.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Cliquez sur les lignes résultantes de la requête pour pouvoir inspecter l’enregistrement.

      ![Exemple de panneau latéral d’inspection de l’enregistrement qui s’ouvre lorsqu’un résultat de recherche avancé est sélectionné.](../../media/mtp/fig21.png)

4. Maintenant que vous avez vérifié que vous pouvez voir le message électronique, ajoutez un filtre pour les pièces jointes. Concentrez-vous sur tous les e-mails avec pièces jointes dans l’environnement. Pour cette simulation, concentrez-vous sur les e-mails entrants, et non sur ceux envoyés à partir de votre environnement. Supprimez les filtres que vous avez ajoutés pour localiser votre message et ajoutez « | où **AttachmentCount > 0** et **EmailDirection**  ==  **« Entrant »**

   La requête suivante vous montre le résultat avec une liste plus courte que votre requête initiale pour tous les événements de courrier électronique :

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Ensuite, incluez les informations sur la pièce jointe (telles que : nom de fichier, hèses) à votre jeu de résultats. Pour ce faire, joignez la table **EmailAttachmentInfo.** Les champs communs à utiliser pour la jointage, dans ce cas sont **NetworkMessageId** et **RecipientObjectId**.

   La requête suivante inclut également une ligne supplémentaire « | **renommer par projet EmailTimestamp=Timestamp**« qui vous aidera à identifier l’intervalle d’heure qui était lié à l’e-mail par rapport aux timestamps liés aux actions de fichier que vous ajouterez à l’étape suivante.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Ensuite, utilisez la valeur **SHA256** de la table **EmailAttachmentInfo** pour rechercher **DeviceFileEvents** (actions de fichier qui se sont produites sur le point de terminaison) pour ce hachage. Le champ commun ici sera le hachage SHA256 pour la pièce jointe.

   Le tableau qui en résulte inclut désormais les détails du point de terminaison (Microsoft Defender pour endpoint) tels que le nom de l’appareil, l’action effectuée (dans ce cas, filtrée pour inclure uniquement les événements FileCreated) et l’endroit où le fichier a été stocké. Le nom de compte associé au processus sera également inclus.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Vous avez maintenant créé une requête qui identifiera tous les e-mails entrants dans lequel l’utilisateur a ouvert ou enregistré la pièce jointe. Vous pouvez également affiner cette requête pour filtrer des domaines d’expéditeur, des tailles de fichiers, des types de fichiers, etc. spécifiques.

7. Les fonctions sont un type spécial de jointage, qui vous permet d’en tirer plus de données TI sur un fichier comme sa prévalence, ses informations sur le signataire et l’émetteur, etc. Pour obtenir plus de détails sur le fichier, utilisez l’enrichissement de fonction **FileProfile()** :

    ```console
    EmailEvents
    | where AttachmentCount > 0 and EmailDirection == "Inbound"
    | project-rename EmailTimestamp=Timestamp
    | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
    | join DeviceFileEvents on SHA256
    | where ActionType == "FileCreated"
    | distinct SHA1
    | invoke FileProfile()
    ```

#### <a name="create-a-detection"></a>Créer une détection

Une fois que vous avez créé une requête qui  identifie les informations dont vous souhaitez être averti s’ils se produisent à l’avenir, vous pouvez créer une détection personnalisée à partir de la requête.

Les détections personnalisées exécutent la requête en fonction de la fréquence que vous avez définie, et les résultats des requêtes créent des alertes de sécurité, en fonction des ressources impactées que vous choisissez. Ces alertes sont corrélées aux incidents et peuvent être triées comme n’importe quelle autre alerte de sécurité générée par l’un des produits.

1. Dans la page de requête, supprimez les lignes 7 et 8 qui ont été ajoutées à l’étape 7 des instructions de repérage d’aller, puis cliquez sur Créer **une règle de détection.**

   ![Exemple d’endroit où vous pouvez cliquer sur créer une règle de détection dans la page de repérage avancé.](../../media/mtp/fig22.png)

   > [!NOTE]
   > Si vous cliquez **sur Créer une règle de détection** et que vous avez des erreurs de syntaxe dans votre requête, votre règle de détection ne sera pas enregistrée. Vérifiez votre requête pour vous assurer qu’il n’y a aucune erreur.

2. Remplissez les champs requis avec les informations qui permettront à l’équipe de sécurité de comprendre l’alerte, pourquoi elle a été générée et les actions que vous attendez qu’elle prenne.

   ![Exemple de page de création de règle de détection dans laquelle vous pouvez définir les détails de l’alerte.](../../media/mtp/fig23.png)

   Veillez à remplir les champs avec clarté pour aider l’utilisateur suivant à prendre une décision éclairée sur cette alerte de règle de détection.

3. Sélectionnez les entités qui sont impactées dans cette alerte. Dans ce cas, sélectionnez **Appareil** et boîte aux **lettres.**

   ![Exemple de page créer une règle de détection dans laquelle vous pouvez choisir les paramètres des entités impactées.](../../media/mtp/fig24.png)

4. Déterminez les actions à prendre si l’alerte est déclenchée. Dans ce cas, exécutez une analyse antivirus, même si d’autres actions peuvent être prises.

   ![Exemple de page créer une règle de détection dans laquelle vous pouvez exécuter une analyse antivirus lorsqu’une alerte est déclenchée pour aider à résoudre les menaces.](../../media/mtp/fig25.png)

5. Sélectionnez l’étendue de la règle d’alerte. Étant donné que cette requête implique des appareils, les groupes d’appareils sont pertinents dans cette détection personnalisée en fonction du contexte microsoft Defender pour point de terminaison. Lors de la création d’une détection personnalisée qui n’inclut pas les appareils en tant qu’entités touchées, l’étendue ne s’applique pas.

   ![Exemple de page de création de règle de détection dans laquelle vous pouvez définir l’étendue de la règle d’alerte gère vos attentes pour les résultats que vous verrez.](../../media/mtp/fig26.png)

   Pour ce projet pilote, vous pouvez limiter cette règle à un sous-ensemble d’appareils de test dans votre environnement de production.

6. Sélectionnez **Créer**. Sélectionnez ensuite **des règles de détection personnalisées** dans le panneau de navigation.

   ![Exemple d’option de règles de détection personnalisées dans le menu.](../../media/mtp/fig27a.png)

   ![Exemple de page de règles de détection qui affiche les détails de la règle et de l’exécution.](../../media/mtp/fig27b.png)

   À partir de cette page, vous pouvez sélectionner la règle de détection, qui ouvre une page de détails.

   ![Exemple de page de pièces jointes dans laquelle vous pouvez voir l’état de l’exécution de la règle, les alertes et actions déclenchées, modifier la détection, etc.](../../media/mtp/fig28.png)

<!--

### Advanced hunting walk-through exercises

To learn more about advanced hunting, the following webcasts will walk you through the capabilities of advanced hunting within Microsoft 365 Defender to create cross-pillar queries, pivot to entities, and create custom detections and remediation actions.

> [!NOTE]
> Be prepared with your own GitHub account to run the hunting queries in your pilot test lab environment.

|Title|Description|Download MP4|Watch on YouTube|CSL file to use|
|---|---|---|---|---|
|Episode 1: KQL fundamentals|We'll cover the basics of advanced hunting capabilities in Microsoft 365 Defender. Learn about available advanced hunting data and basic KQL syntax and operators.|[MP4](https://aka.ms/MTP15JUL20_MP4)|[YouTube](https://youtu.be/0D9TkGjeJwM)|[Episode 1: CSL file in Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%201%20-%20KQL%20Fundamentals.csl)|
|Episode 2: Joins|We'll continue learning about data in advanced hunting and how to join tables together. Learn about inner, outer, unique, and semi joins, and the nuances of the default Kusto innerunique join.|[MP4](https://aka.ms/MTP22JUL20_MP4)|[YouTube](https://youtu.be/LMrO6K5TWOU)|[Episode 2: CSL file in Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%202%20-%20Joins.csl)|
|Episode 3: Summarizing, pivoting, and visualizing data|Now that we're able to filter, manipulate, and join data, it's time to start summarizing, quantifying, pivoting, and visualizing. In this episode, we'll cover the summarize operator and some of the calculations you can perform while diving into additional tables in the advanced hunting schema. We turn our datasets into charts that can help improve analysis.|[MP4](https://aka.ms/MTP29JUL20_MP4)|[YouTube](https://youtu.be/UKnk9U1NH6Y)|[Episode 3: CSL file in Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%203%20-%20Summarizing%2C%20Pivoting%2C%20and%20Joining.csl)|
|Episode 4: Let's hunt! Applying KQL to incident tracking|Time to track some attacker activity! In this episode, we'll use our improved understanding of KQL and advanced hunting in Microsoft 365 Defender to track an attack. Learn some of the tips and tricks used in the field to track attacker activity, including the ABCs of cybersecurity and how to apply them to incident response.|[MP4](https://aka.ms/MTP5AUG20_MP4)|[YouTube](https://youtu.be/2EUxOc_LNd8)|[Episode 4: CSL file in Git](https://github.com/microsoft/Microsoft-threat-protection-Hunting-Queries/blob/master/Webcasts/TrackingTheAdversary/Episode%204%20-%20Lets%20Hunt.csl)|
|

--> 

### <a name="expert-training-on-advanced-hunting"></a>Formation experte sur le chasse avancée

**Le suivi de l’adversaire est** une série de webcasts pour les nouveaux analystes de sécurité et les observateurs de menaces. Il vous guide à travers les principes de base du recherche avancée tout au long de la création de vos propres requêtes sophistiquées. 

Pour [commencer, consultez](advanced-hunting-expert-training.md) Obtenir une formation spécialisée sur la recherche avancée.

### <a name="navigation-you-may-need"></a>Navigation dont vous aurez peut-être besoin

[Créer l’Microsoft 365 Defender d’évaluation de la sécurité](eval-create-eval-environment.md)
