---
title: Créer une notification de non-droit
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez l’outil Communications dans Advanced eDiscovery cas pour envoyer, collecter et suivre des notifications de mise en attente légale.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: cc9e8c424550c2be12711d7ef098c95230b0b1a4
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58574363"
---
# <a name="create-a-legal-hold-notice"></a>Créer une notification de non-droit

À l Advanced eDiscovery les communications des dépositaires, les organisations peuvent gérer leur flux de travail autour de la communication avec les dépositaires. Grâce à l’outil communications, les équipes juridiques peuvent systématiquement envoyer, collecter et suivre les notifications de mise en attente légale. Le processus de création flexible permet également aux équipes de personnaliser le flux de travail de notification de conservation et le contenu des notifications envoyées aux dépositaires.

![Page Communications.](../media/CommunicationPage.PNG)

Cet article décrit les étapes du flux de travail de notification de mise en attente.

## <a name="step-1-specify-communication-details"></a>Étape 1 : spécifier les détails de communication

La première étape consiste à spécifier les détails appropriés pour les notifications de conservation légale ou d’autres communications de dépositaire.

![Page Communication de nom.](../media/NameCommunication.PNG)

1. Dans la Centre de conformité Microsoft 365, go to **eDiscovery > Advanced** to display the list of cases in your organization.

2. Sélectionnez un cas, cliquez sur **l’onglet Communications,** puis sur **Nouvelle communication.**

3. Dans la page **Communication du** nom, spécifiez les détails de communication suivants (obligatoires).

    - **Nom**: il s’agit du nom de la communication.

    - **Responsable de l’émission**: la liste de listes listes affiche la liste des membres de cas. Pour plus d’informations sur l’ajout de nouveaux membres à un cas, voir [Créer un Advanced eDiscovery cas.](create-and-manage-advanced-ediscoveryv2-case.md#create-a-case) Chaque avis envoyé aux dépositaires sera envoyé au nom du responsable de l’émission spécifié.

> [!NOTE]
> Le responsable de l’émission doit avoir une boîte **aux lettres active** pour s’afficher dans la boîte aux lettres du responsable de l’émission.


4. Cliquez sur **Suivant**.

## <a name="step-2-define-the-portal-content"></a>Étape 2 : Définir le contenu du portail

Ensuite, vous pouvez créer et ajouter le contenu de l’avis de attente. Dans la page **Définir le contenu du portail** dans l’Assistant Créer une **communication,** spécifiez le contenu de l’avis de attente. Ce contenu est automatiquement intégré aux notifications d’émission, de ré émission, de rappel et d’escalade. En outre, ce contenu s’affiche dans le portail de conformité du dépositaire.

![Page de contenu du portail.](../media/PortalContent.PNG)

Pour créer le contenu du portail :

1. Tapez (ou coupez-collez à partir d’un autre document) votre avis de non-attente dans la boîte de texte du contenu du portail.

2. Insérez des variables de fusion dans votre avis pour personnaliser l’avis et partager le portail de conformité des dépositaires.

3. Cliquez sur **Suivant**.

  > [!TIP]
  > Pour en savoir plus sur la façon de personnaliser le contenu et le format du contenu du portail, voir [Utiliser l’éditeur de communications.](using-communications-editor.md)

## <a name="step-3-set-the-required-notifications"></a>Étape 3 : Définir les notifications requises

Une fois que vous avez défini le contenu de l’avis de mise en attente, vous pouvez configurer les flux de travail autour de l’envoi et de la gestion du processus de notification. Les notifications sont des messages électroniques envoyés pour avertir et suivre les dépositaires. Chaque dépositaire ajouté à la communication reçoit la même notification.

Pour configurer et envoyer un avis de mise en attente, vous devez inclure des notifications d’émission, de nouvelle émission et de publication.

### <a name="issuance-notification"></a>Notification d’émission

Une fois la communication créée, la **notification d’émission** est initiée par le responsable de l’émission spécifié. La notification d’émission est la première communication envoyée au dépositaire pour l’informer de ses obligations de conservation.

Pour créer une notification d’émission :

1. Dans la vignette **Émission,** cliquez sur **Modifier.**

2. Si nécessaire, ajoutez des membres de cas ou du personnel supplémentaires aux **champs Cc** et **Cci.** Pour ajouter plusieurs utilisateurs à ces champs, séparez les adresses de messagerie par un point-virgule.

3. Spécifiez **l’objet** de l’avis (obligatoire).

4. Spécifiez le contenu ou les instructions supplémentaires que vous souhaitez fournir au dépositaire (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis d’émission.

5. Cliquez sur **Enregistrer**.

### <a name="re-issuance-notification"></a>Re-Issuance notification

Au fur et à mesure de la progression du cas, les dépositaires peuvent être tenus de conserver des données supplémentaires ou inférieures aux instructions précédemment. Une fois que vous avez mis à jour le contenu du portail, la notification de nouvelle émission est envoyée et avertit les dépositaires des modifications apportées à leurs obligations de conservation.

Pour créer une notification de nouvelle émission :

1. Dans la **vignette Réédition,** cliquez sur **Modifier.**

2. Si nécessaire, ajoutez des membres de cas ou du personnel supplémentaires aux **champs Cc** et **Cci.** Pour ajouter plusieurs utilisateurs à ces champs, séparez les adresses de messagerie par un point-virgule.

3. Spécifiez **l’objet** de l’avis (obligatoire).

4. Spécifiez le contenu ou les instructions supplémentaires que vous souhaitez fournir au dépositaire (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis de nouvelle émission.

5. Cliquez sur **Enregistrer**.

> [!NOTE]
> Si le contenu du portail est modifié (dans la **page** Définir le contenu du portail dans l’Assistant Modifier la **communication),** la notification de rééd émission est automatiquement envoyée à tous les dépositaires affectés à l’avis. Une fois la notification envoyée, les dépositaires sont invités à ré-accusé de réception de leur notification de conservation. Si vous avez mis en place des flux de travail de rappel ou d’escalade, ceux-ci seront également ré-démarrer. Pour plus d’informations sur les autres événements de gestion de cas qui déclenchent des communications, voir [Événements qui déclenchent des notifications.](#events-that-trigger-notifications)

### <a name="release-notification"></a>Notification de publication

Une fois qu’un problème est résolu ou si un dépositaire n’est plus soumis à la conservation du contenu, vous pouvez libérer le dépositaire d’un cas. Si le dépositaire a déjà émis un avis de conservation, la notification de publication peut être utilisée pour avertir les dépositaires qu’ils ont été libérés de leur obligation.

Pour créer une notification de publication :

1. Dans la vignette **Release,** cliquez sur **Modifier.**

2. Si nécessaire, ajoutez des membres de cas ou du personnel supplémentaires aux **champs Cc** et **Cci.** Pour ajouter plusieurs utilisateurs à ces champs, séparez les adresses de messagerie par un point-virgule.

3. Spécifiez **l’objet** de l’avis (obligatoire).

4. Spécifiez le contenu ou les instructions supplémentaires que vous souhaitez fournir au dépositaire (obligatoire).

5. Cliquez **sur Enregistrer** et allez à l’étape suivante.

## <a name="optional-step-4-set-the-optional-notifications"></a>(Facultatif) Étape 4 : Définir les notifications facultatives

Si vous le souhaitez, vous pouvez simplifier le flux de travail pour le suivi des dépositaires qui ne répond pas en créant et en programmant des notifications de rappel et d’escalade automatisées.

![Page Rappel/Escalade.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Reminders

Une fois que vous avez envoyé une notification de conservation, vous pouvez suivre les dépositaires qui ne répond pas en définissant un flux de travail de rappel.

Pour planifier des rappels :

1. Dans la vignette **Rappel,** cliquez sur **Modifier.**

2. Activez le **flux de** travail Rappel en **activé** le basculement d’état (obligatoire).

3. Spécifiez **l’intervalle de rappel (en jours)** (obligatoire). Il s’agit du nombre de jours d’attente avant l’envoi de la première notification de rappel et du suivi. Par exemple, si vous définissez l’intervalle de rappel sur sept jours, le premier rappel sera envoyé sept jours après l’émission initiale de la notification de mise en attente. Tous les rappels suivants sont également envoyés tous les sept jours.

4. Spécifiez **le nombre de rappels** (obligatoire). Ce champ spécifie le nombre de rappels à envoyer aux dépositaires qui ne répond pas. Par exemple, si vous définissez le nombre de rappels sur 3, un dépositaire reçoit un maximum de trois rappels. Une fois qu’un dépositaire a reconnu la notification de conservation, les rappels ne sont plus envoyés à cet utilisateur.

5. Spécifiez **l’objet** de l’avis (obligatoire).

6. Spécifiez le contenu ou les instructions supplémentaires que vous souhaitez fournir au dépositaire (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis de rappel.

7. Cliquez **sur Enregistrer** et allez à l’étape suivante.

### <a name="escalations"></a>Escalades

Dans certains cas, vous aurez peut-être besoin de moyens supplémentaires pour suivre les dépositaires qui ne répondront pas. Si un dépositaire ne reconnaît pas une notification de conservation après avoir reçu le nombre spécifié de rappels, l’équipe juridique peut spécifier un flux de travail pour envoyer automatiquement une notification d’escalade au dépositaire et à son responsable.

Pour planifier des escalades :

1. Dans la vignette **Escalade,** cliquez sur **Modifier.**

2. Activez le flux **de** travail d’escalade en activé **le** basculement d’état.

3. Spécifiez **l’intervalle d’escalade (en jours)** (obligatoire).

4. Spécifiez **le nombre d’escalades** (obligatoire). Ce champ spécifie le nombre d’escalades à envoyer aux dépositaires qui ne répond pas. Par exemple, si vous définissez le nombre d’escalades sur 3, une notification d’escalade est envoyée au dépositaire et à son responsable au maximum trois fois. Une fois qu’un dépositaire a reconnu la notification de conservation, les escalades ne sont plus envoyées.

5. Spécifiez **l’objet** de l’avis (obligatoire).

6. Spécifiez le contenu ou les instructions supplémentaires que vous souhaitez fournir au dépositaire (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis d’escalade.

7. Cliquez **sur Enregistrer** et passer à l’étape suivante.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>Étape 5 : Affecter des dépositaires pour recevoir des notifications

Une fois que vous avez finalisé le contenu pour les notifications, sélectionnez les dépositaires à qui vous souhaitez envoyer des notifications.

![Page Sélectionner les dépositaires.](../media/SelectCustodians.PNG)

Pour ajouter des dépositaires :

1. Affectez des dépositaires à la communication en cliquant sur la case à cocher en regard de leur nom.

    Une fois la communication créée, le flux de travail de notification s’applique automatiquement aux dépositaires sélectionnés.

2. Cliquez **sur Suivant** pour passer en revue les paramètres et détails de communication.

> [!NOTE]
> Vous pouvez uniquement ajouter des dépositaires qui ont été ajoutés au cas et qui n’ont pas reçu de notification supplémentaire dans le cas.

## <a name="step-6-review-settings"></a>Étape 6 : Examiner les paramètres

Après avoir passé en  revue les paramètres et cliqué sur Envoyer pour terminer la communication, le système démarre automatiquement le flux de travail de communication en envoyant l’avis d’émission.

## <a name="events-that-trigger-notifications"></a>Événements qui déclenchent des notifications

Le tableau suivant décrit les événements dans le processus de gestion des cas qui se déclenchent lorsque les différents types de notifications sont envoyés aux dépositaires.

|Type de communication|Déclencher |
|:---------|:---------|
|Avis d’émission|Création initiale de la notification. Vous pouvez également renvoyer manuellement une notification de mise en attente. |
|Notifications de réé émission|Mise à jour du contenu du portail sur la page **Définir le contenu du** portail dans **l’Assistant Modifier la communication.**|
|Avis de publication|Le dépositaire est libéré du cas.|
|Reminders|Intervalle et nombre de rappels configurés pour le rappel.|
|Escalades|Intervalle et nombre de rappels configurés pour l’escalade.|
|||
