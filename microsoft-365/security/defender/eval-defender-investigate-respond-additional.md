---
title: Essayer Microsoft 365 Defender fonctionnalités de réponse aux incidents dans un environnement pilote
description: Essayez les fonctionnalités de réponse aux incidents dans Microsoft 365 Defender pour hiérarchiser et gérer les incidents, automatiser les investigations et utiliser la chasse avancée dans la détection des menaces.
keywords: Microsoft 365 Defender essai, essayez Microsoft 365 Defender, évaluez Microsoft 365 Defender, Microsoft 365 Defender laboratoire d’évaluation, Microsoft 365 Defender  pilote, cybersécurité, menace persistante avancée, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, investigation et correction automatisées, repérage avancé
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.localizationpriority: medium
ms.author: dansimp
author: dansimp
ms.date: 07/09/2021
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.openlocfilehash: 5dbda4df04d47d4069a60fd7925dde2390708aba
ms.sourcegitcommit: 10e6abe740e27000e223378eb17d657a47555fa8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/31/2022
ms.locfileid: "67473632"
---
# <a name="try-microsoft-365-defender-incident-response-capabilities-in-a-pilot-environment"></a>Essayer Microsoft 365 Defender fonctionnalités de réponse aux incidents dans un environnement pilote

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 2 sur 2](eval-defender-investigate-respond.md) dans le processus d’examen et de réponse d’un incident dans Microsoft 365 Defender à l’aide d’un environnement pilote. Pour plus d’informations sur ce processus, consultez l’article [de présentation](eval-defender-investigate-respond.md) .

Une fois que vous avez effectué une [réponse aux incidents pour une attaque simulée](eval-defender-investigate-respond-simulate-attack.md), voici quelques fonctionnalités Microsoft 365 Defender à explorer :

|Fonctionnalité |Description |
|:-------|:-----|
| [Hiérarchisation des incidents](#prioritize-incidents) | Utilisez le filtrage et le tri de la file d’attente d’incidents pour déterminer les incidents à traiter ensuite. |
| [Gestion des incidents](#manage-incidents) | Modifiez les propriétés d’incident pour garantir une affectation correcte, ajouter des balises et des commentaires et résoudre un incident. |
| [Examen et réponse automatisés](#examine-automated-investigation-and-response-with-the-action-center) | Utilisez des fonctionnalités d’investigation et de réponse automatisées (AIR) pour aider votre équipe chargée des opérations de sécurité à résoudre les menaces de manière plus efficace et efficace. Le centre d’action est une expérience « unique volet de verre » pour les tâches d’incident et d’alerte, telles que l’approbation des actions de correction en attente. |
| [Repérage avancé](#use-advanced-hunting) | Utilisez des requêtes pour inspecter de manière proactive les événements de votre réseau et localiser les indicateurs de menace et les entités. Vous utilisez également la chasse avancée pendant l’examen et la correction d’un incident. |


## <a name="prioritize-incidents"></a>Hiérarchiser les incidents

Vous accédez à la file d’attente des **incidents à partir des alertes & > incidents** lors du lancement rapide du <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents.png" alt-text="Section Incidents & alertes dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents.png":::


La section **Incidents et alertes les plus récents** affiche un graphique du nombre d’alertes reçues et d’incidents créés au cours des dernières 24 heures.

Pour examiner la liste des incidents et hiérarchiser leur importance pour l’affectation et l’investigation, vous pouvez : 

- Configurez des colonnes personnalisables ( **sélectionnez Choisir des colonnes**) pour vous donner une visibilité sur les différentes caractéristiques de l’incident ou des entités affectées. Cela vous aide à prendre une décision éclairée concernant la hiérarchisation des incidents à des fins d’analyse.

- Utilisez le filtrage pour vous concentrer sur un scénario ou une menace spécifique. L’application de filtres sur la file d’attente d’incidents peut aider à déterminer les incidents qui nécessitent une attention immédiate. 

Dans la file d’attente d’incidents par défaut, sélectionnez **Filtres** pour afficher un volet **Filtres** , à partir duquel vous pouvez spécifier un ensemble spécifique d’incidents. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-filters.png" alt-text="Volet Filtres de la section Incidents & alertes dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-filters.png":::

Pour plus d’informations, consultez [Hiérarchiser les incidents](incident-queue.md).

## <a name="manage-incidents"></a>Gérer les incidents

Vous pouvez gérer les incidents à partir du volet **Gérer les incidents** pour un incident. Voici un exemple.

:::image type="content" source="../../media/incidents-queue/incidents-ss-incidents-manage.png" alt-text="Volet Gérer les incidents de la section Incidents & alertes dans le portail Microsoft 365 Defender" lightbox="../../media/incidents-queue/incidents-ss-incidents-manage.png":::

Vous pouvez afficher ce volet à partir du lien **Gérer l’incident** sur les éléments suivants :

- Volet Propriétés d’un incident dans la file d’attente des incidents.
- **Page récapitulative** d’un incident.

Voici comment gérer vos incidents :

- Modifier le nom de l’incident

  Modifiez le nom attribué automatiquement en fonction des bonnes pratiques de votre équipe de sécurité.
  
- Ajouter des balises d’incident

  Ajoutez des balises utilisées par votre équipe de sécurité pour classifier les incidents, qui peuvent être filtrés ultérieurement.
  
- Affecter l’incident

  Affectez-le à un nom de compte d’utilisateur, qui peut être filtré ultérieurement.
  
- Résoudre un incident

  Fermez l’incident une fois qu’il a été corrigé.
  
- Définir sa classification et sa détermination

  Classifiez et sélectionnez le type de menace lorsque vous résolvez un incident.
  
- Ajouter des commentaires

  Utilisez des commentaires pour la progression, les notes ou d’autres informations basées sur les meilleures pratiques de votre équipe de sécurité. L’historique complet des commentaires est disponible à partir de l’option **Commentaires et historique** dans la page de détails d’un incident.

Pour plus d’informations, consultez [Gérer les incidents](manage-incidents.md).

## <a name="examine-automated-investigation-and-response-with-the-action-center"></a>Examiner l’investigation automatisée et la réponse avec le Centre d’actions

Selon la façon dont les fonctionnalités d’investigation et de réponse automatisées sont configurées pour votre organisation, les actions de correction sont effectuées automatiquement ou uniquement après approbation par votre équipe des opérations de sécurité. Toutes les actions, qu’elles soient en attente ou terminées, sont répertoriées dans le [Centre d’actions](m365d-action-center.md), qui répertorie les actions de correction en attente et terminées pour vos appareils, l’e-mail & le contenu de collaboration et les identités dans un emplacement unique.

Voici un exemple.

:::image type="content" source="../../media/m3d-action-center-unified.png" alt-text="Centre d’action unifiée dans le portail Microsoft 365 Defender" lightbox="../../media/m3d-action-center-unified.png":::

Dans le Centre d’actions, vous pouvez sélectionner les actions en attente, puis les approuver ou les rejeter dans le volet de menu volant. Voici un exemple.

:::image type="content" source="../../media/air-actioncenter-itemselected.png" alt-text="Volet affichant les options d’approbation ou de rejet d’une action dans le portail Microsoft 365 Defender" lightbox="../../media/air-actioncenter-itemselected.png":::


Approuvez (ou refusez) les actions en attente dès que possible afin que vos enquêtes automatisées puissent se poursuivre et se terminer en temps voulu.

Pour plus d’informations, consultez [Le Centre d’investigation et de réponse automatisée](m365d-autoir.md) et [le Centre d’action](m365d-action-center.md).

## <a name="use-advanced-hunting"></a>Utiliser la chasse avancée

> [!NOTE]
> Avant de vous guider dans la simulation de chasse avancée, regardez la vidéo suivante pour comprendre les concepts de chasse avancés, voir où vous pouvez le trouver dans le portail et savoir comment il peut vous aider dans vos opérations de sécurité.

<br>

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4Bp7O]


Si la [simulation d’attaque PowerShell sans fichier facultative](eval-defender-investigate-respond-simulate-attack.md#simulate-an-attack-with-an-isolated-domain-controller-and-client-device-optional) était une attaque réelle qui avait déjà atteint l’étape d’accès aux informations d’identification, vous pouvez utiliser la recherche avancée à tout moment de l’enquête pour effectuer une recherche proactive dans les événements et les enregistrements du réseau à l’aide de ce que vous savez déjà à partir des alertes générées et des entités affectées. 

Par exemple, en fonction des informations contenues dans l’alerte de [reconnaissance d’utilisateur et d’adresse IP (SMB](eval-defender-investigate-respond-simulate-attack.md#alert-user-and-ip-address-reconnaissance-smb-source-microsoft-defender-for-identity)), vous pouvez utiliser la `IdentityDirectoryEvents` table pour rechercher tous les événements d’énumération de session SMB ou rechercher d’autres activités de découverte dans différents autres protocoles dans Microsoft Defender pour Identity données à l’aide de la `IdentityQueryEvents` table.


### <a name="hunting-environment-requirements"></a>Conditions requises pour l’environnement de chasse

Une seule boîte aux lettres interne et un seul appareil sont requis pour cette simulation. Vous aurez également besoin d’un compte de messagerie externe pour envoyer le message de test.

1. Vérifiez que votre locataire a [activé Microsoft 365 Defender](m365d-enable.md#confirm-that-the-service-is-on).
2. Identifiez une boîte aux lettres cible à utiliser pour recevoir des e-mails.

   - Cette boîte aux lettres doit être surveillée par Microsoft Defender pour Office 365

   - L’appareil de l’exigence 3 doit accéder à cette boîte aux lettres

3. Configurer un appareil de test :

    a. Vérifiez que vous utilisez Windows 10 version 1903 ou ultérieure.

    b. Joignez l’appareil de test au domaine de test.

    c. [Activez l’antivirus Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features). Si vous rencontrez des problèmes d’activation de l’antivirus Microsoft Defender, consultez [cette rubrique de résolution des problèmes](/windows/security/threat-protection/microsoft-defender-atp/troubleshoot-onboarding#ensure-that-microsoft-defender-antivirus-is-not-disabled-by-a-policy).

    d. [Intégration à Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints).

### <a name="run-the-simulation"></a>Exécuter la simulation

1. À partir d’un compte de messagerie externe, envoyez un e-mail à la boîte aux lettres identifiée à l’étape 2 de la section relative aux exigences de l’environnement de chasse. Incluez une pièce jointe qui sera autorisée par le biais de toutes les stratégies de filtre de messagerie existantes. Ce fichier n’a pas besoin d’être malveillant ou exécutable. Les types de fichiers suggérés sont <i>.pdf</i>, <i>.exe</i> (si autorisé) ou un type de document Office tel qu’un fichier Word.

2. Ouvrez l’e-mail envoyé à partir de l’appareil configuré comme défini à l’étape 3 de la section relative aux exigences de l’environnement de chasse. Ouvrez la pièce jointe ou enregistrez le fichier sur l’appareil.

#### <a name="go-hunting"></a>Aller à la chasse

1. Ouvrez le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>.

2. Dans le volet de navigation, sélectionnez **Repérage > Repérage avancé**.

3. Créez une requête qui commence par collecter des événements de messagerie.

   1. Sélectionnez **Requête > Nouveau**.

   1. Dans le **Email** groupes sous **Repérage avancé**, double-cliquez sur **EmailEvents**. Vous devriez le voir dans la fenêtre de requête.

      ```console
      EmailEvents
      ```

   1. Remplacez l’intervalle de temps de la requête par les dernières 24 heures. En supposant que l’e-mail que vous avez envoyé lorsque vous avez exécuté la simulation ci-dessus était au cours des dernières 24 heures, sinon, modifiez l’intervalle de temps en fonction des besoins.

   1. Sélectionnez **Exécuter la requête**. Vous pouvez avoir des résultats différents en fonction de votre environnement pilote.

      > [!NOTE]
      > Consultez l’étape suivante pour connaître les options de filtrage permettant de limiter le retour de données.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-1.png" alt-text="Page Repérage avancé dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-1.png":::

        > [!NOTE]
        > La chasse avancée affiche les résultats de la requête sous forme de données tabulaires. Vous pouvez également choisir d’afficher les données dans d’autres types de format tels que des graphiques.

   1. Examinez les résultats et déterminez si vous pouvez identifier l’e-mail que vous avez ouvert. Jusqu’à deux heures peuvent être nécessaires pour que le message s’affiche en repérage avancé. Pour affiner les résultats, vous pouvez ajouter la condition **where** à votre requête pour rechercher uniquement les e-mails qui ont « yahoo.com » comme senderMailFromDomain. Voici un exemple.

      ```console
      EmailEvents
      | where SenderMailFromDomain == "yahoo.com"
      ```

   1. Cliquez sur les lignes résultantes de la requête pour pouvoir inspecter l’enregistrement.

      :::image type="content" source="../../media/advanced-hunting-incident-response-try-2.png" alt-text="Section Inspecter l’enregistrement de la page Repérage avancé dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-2.png":::

4. Maintenant que vous avez vérifié que vous pouvez voir l’e-mail, ajoutez un filtre pour les pièces jointes. Concentrez-vous sur tous les e-mails contenant des pièces jointes dans l’environnement. Pour cette simulation, concentrez-vous sur les e-mails entrants, et non sur ceux qui sont envoyés à partir de votre environnement. Supprimez les filtres que vous avez ajoutés pour localiser votre message et ajoutez « | where **AttachmentCount > 0** and **EmailDirection** == **"Inbound" »**

   La requête suivante affiche le résultat avec une liste plus courte que votre requête initiale pour tous les événements de messagerie :

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   ```

5. Ensuite, incluez les informations relatives à la pièce jointe (par exemple: nom de fichier, hachages) à votre jeu de résultats. Pour ce faire, joignez la table **EmailAttachmentInfo** . Les champs courants à utiliser pour la jointure, dans ce cas sont **NetworkMessageId** et **RecipientObjectId**.

   La requête suivante inclut également une ligne supplémentaire « | **project-rename EmailTimestamp=Timestamp** » qui vous aidera à identifier l’horodatage lié à l’e-mail et les horodatages liés aux actions de fichier que vous ajouterez à l’étape suivante.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   ```

6. Ensuite, utilisez la valeur **SHA256** de la table **EmailAttachmentInfo** pour rechercher **DeviceFileEvents** (actions de fichier qui se sont produites sur le point de terminaison) pour ce hachage. Le champ commun ici sera le hachage SHA256 pour la pièce jointe.

   La table résultante inclut désormais les détails du point de terminaison (Microsoft Defender pour point de terminaison) tels que le nom de l’appareil, l’action effectuée (dans ce cas, filtrée pour inclure uniquement les événements FileCreated) et l’emplacement où le fichier a été stocké. Le nom du compte associé au processus sera également inclus.

   ```console
   EmailEvents
   | where AttachmentCount > 0 and EmailDirection == "Inbound"
   | project-rename EmailTimestamp=Timestamp
   | join EmailAttachmentInfo on NetworkMessageId, RecipientObjectId
   | join DeviceFileEvents on SHA256
   | where ActionType == "FileCreated"
   ```

   Vous avez maintenant créé une requête qui identifie tous les e-mails entrants où l’utilisateur a ouvert ou enregistré la pièce jointe. Vous pouvez également affiner cette requête pour filtrer des domaines d’expéditeur spécifiques, des tailles de fichier, des types de fichiers, et ainsi de suite.

7. Les fonctions sont un type spécial de jointure, qui vous permet d’extraire plus de données TI sur un fichier comme sa prévalence, ses informations de signataire et d’émetteur, etc. Pour obtenir plus d’informations sur le fichier, utilisez l’enrichissement de la fonction **FileProfile()** :

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

Une fois que vous avez créé une requête qui identifie les informations dont vous souhaitez **être alerté** si elles se produisent à l’avenir, vous pouvez créer une détection personnalisée à partir de la requête.

Les détections personnalisées exécutent la requête en fonction de la fréquence que vous définissez, et les résultats des requêtes créent des alertes de sécurité, en fonction des ressources affectées que vous choisissez. Ces alertes sont corrélées aux incidents et peuvent être triées en tant qu’autres alertes de sécurité générées par l’un des produits.

1. Dans la page de requête, supprimez les lignes 7 et 8 ajoutées à l’étape 7 des instructions de repérage Go, puis cliquez sur **Créer une règle de détection**.

   :::image type="content" source="../../media/advanced-hunting-incident-response-try-3.png" alt-text="Section Modification de requête de la page Repérage avancé dans le portail Microsoft 365 Defender" lightbox="../../media/advanced-hunting-incident-response-try-3.png":::

   > [!NOTE]
   > Si vous cliquez sur **Créer une règle de détection** et que votre requête comporte des erreurs de syntaxe, votre règle de détection n’est pas enregistrée. Vérifiez votre requête pour vous assurer qu’il n’y a pas d’erreurs.

2. Renseignez les champs requis avec les informations qui permettront à l’équipe de sécurité de comprendre l’alerte, la raison pour laquelle elle a été générée et les actions que vous attendez d’elles.

   :::image type="content" source="../../media/mtp/fig23.png" alt-text="Page Détails de l’alerte dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig23.png":::

   Veillez à remplir les champs avec clarté pour aider l’utilisateur suivant à prendre une décision éclairée concernant cette alerte de règle de détection.

3. Sélectionnez les entités affectées dans cette alerte. Dans ce cas, sélectionnez **Appareil** et **boîte aux lettres**.

   :::image type="content" source="../../media/mtp/fig24.png" alt-text="Page détails des entités impactées dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig24.png":::

4. Déterminez les actions à effectuer si l’alerte est déclenchée. Dans ce cas, exécutez une analyse antivirus, bien que d’autres actions puissent être effectuées.

   :::image type="content" source="../../media/mtp/fig25.png" alt-text="Page Actions dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig25.png":::

5. Sélectionnez l’étendue de la règle d’alerte. Étant donné que cette requête implique des appareils, les groupes d’appareils sont pertinents dans cette détection personnalisée en fonction Microsoft Defender pour point de terminaison contexte. Lors de la création d’une détection personnalisée qui n’inclut pas les appareils en tant qu’entités affectées, l’étendue ne s’applique pas.

   :::image type="content" source="../../media/mtp/fig26.png" alt-text="Page Étendue dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig26.png":::


   Pour ce pilote, vous pouvez limiter cette règle à un sous-ensemble d’appareils de test dans votre environnement de production.

6. Sélectionnez **Créer**. Ensuite, sélectionnez **Règles de détection personnalisées** dans le panneau de navigation.

   :::image type="content" source="../../media/mtp/fig27a.png" alt-text="Option de règles de détection personnalisée dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig27a.png":::

   :::image type="content" source="../../media/mtp/fig27b.png" alt-text="Page affichant les règles de détection et les détails d’exécution dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig27b.png":::

   Dans cette page, vous pouvez sélectionner la règle de détection, qui ouvre une page de détails.

   :::image type="content" source="../../media/mtp/fig28.png" alt-text="Page affichant les détails des alertes déclenchées dans le portail Microsoft 365 Defender" lightbox="../../media/mtp/fig28.png":::


### <a name="expert-training-on-advanced-hunting"></a>Formation d’experts sur la chasse avancée

**Le suivi de l’adversaire** est une série web destinée aux nouveaux analystes de la sécurité et aux chasseurs de menaces chevronnés. Il vous guide tout au long des principes de base de la chasse avancée jusqu’à la création de vos propres requêtes sophistiquées. 

Voir [Obtenir une formation d’expert sur la chasse avancée](advanced-hunting-expert-training.md) pour commencer.

### <a name="navigation-you-may-need"></a>Navigation dont vous aurez peut-être besoin

[Créer l’environnement d’évaluation Microsoft 365 Defender](eval-create-eval-environment.md)
