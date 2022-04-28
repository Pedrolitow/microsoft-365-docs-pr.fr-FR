---
title: Créer un avis de conservation légale
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Utilisez l’outil Communications dans un cas eDiscovery (Premium) pour envoyer, collecter et suivre les notifications de conservation légale.
ms.custom: seo-marvel-mar2020
ms.openlocfilehash: 21090274f385d6a3354852134764a1f53a311f10
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65094987"
---
# <a name="create-a-legal-hold-notice"></a>Créer un avis de conservation légale

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

À l’aide des communications de consignation eDiscovery (Premium), les organisations peuvent gérer leur flux de travail autour de la communication avec les consignatateurs. Grâce à l’outil Communications, les équipes juridiques peuvent systématiquement envoyer, collecter et suivre les notifications de conservation légale. Le processus de création flexible permet également aux équipes de personnaliser le flux de travail de notification de conservation et le contenu des avis envoyés aux consignatateurs.

![Page Communications.](../media/CommunicationPage.PNG)

L’article décrit les étapes du flux de travail de notification de conservation.

## <a name="step-1-specify-communication-details"></a>Étape 1 : Spécifier les détails de la communication

La première étape consiste à spécifier les détails appropriés pour les avis de conservation légale ou d’autres communications des consignatateurs.

![Page Communication du nom.](../media/NameCommunication.PNG)

1. Dans le portail de conformité Microsoft Purview, accédez à **eDiscovery > Avancé** pour afficher la liste des cas dans votre organisation.

2. Sélectionnez un cas, cliquez sur l’onglet **Communications** , puis sur **Nouvelle communication**.

3. Dans la page **De communication du nom** , spécifiez les paramètres de communication suivants.

    - **Nom** : il s’agit du nom de la communication.

    - **Agent d’émission** : la liste déroulante affiche les utilisateurs de votre organisation qui peuvent être sélectionnés en tant qu’agent émetteur pour la communication. Chaque communication envoyée aux consignats sera envoyée au nom de l’agent d’émission sélectionné. La liste des utilisateurs dans la liste déroulante se compose des membres du cas et des agents d’émission à l’échelle de l’organisation. Ces agents d’émission sont ajoutés par un administrateur eDiscovery et sont disponibles dans tous les cas eDiscovery (Premium) dans votre organisation. Pour plus d’informations, consultez [Gérer les agents d’émission](advanced-ediscovery-issuing-officers.md).

    - **Sélectionner un modèle de communication** : la liste déroulante affiche les modèles de la bibliothèque communications dans la page des paramètres eDiscovery (Premium). Si vous sélectionnez un modèle, il s’affiche sur le **contenu définir le portail** comme point de départ pour le texte de la notification que vous créez. Si vous ne sélectionnez pas de modèle, vous devrez créer l’avis vous-même à partir de zéro. Pour plus d’informations sur les modèles de communication, consultez [Gérer les modèles de communication des consignatateurs](advanced-ediscovery-communications-library.md).

4. Cliquez sur **Suivant**.

## <a name="step-2-define-the-portal-content"></a>Étape 2 : Définir le contenu du portail

Ensuite, vous pouvez créer et ajouter le contenu de l’avis de suspension. Dans la page **Définir le contenu du portail** dans l’Assistant Création d’une **communication** , spécifiez le contenu de l’avis de suspension. Ce contenu est automatiquement ajouté aux avis d’émission, de ré-émission, de rappel et d’escalade. En outre, ce contenu s’affiche dans le portail de conformité du consignateur. Si vous avez sélectionné un modèle dans la bibliothèque communications, il s’affiche et fournit un point de départ pour l’avis que vous créez.

![Page Contenu du portail.](../media/PortalContent.PNG)

Pour créer le contenu du portail :

1. Tapez (ou coupez et collez à partir d’un autre document) votre avis de conservation dans la zone de texte pour le contenu du portail. Si vous avez sélectionné un modèle de communication dans la page précédente de l’Assistant, le modèle s’affiche. Vous pouvez modifier le contenu du modèle si nécessaire.

2. Insérez des variables de fusion dans votre avis pour personnaliser l’avis et partager le portail de conformité du gardien.

3. Cliquez sur **Suivant**.

  > [!TIP]
  > Pour en savoir plus sur la façon de personnaliser le contenu et le format du contenu du portail, consultez [Utiliser l’éditeur de communications](using-communications-editor.md).

## <a name="step-3-set-the-required-notifications"></a>Étape 3 : Définir les notifications requises

Une fois que vous avez défini le contenu de l’avis de suspension, vous pouvez configurer les flux de travail autour de l’envoi et de la gestion du processus de notification. Les notifications sont des messages électroniques qui sont envoyés pour notifier et effectuer un suivi auprès des consignatateurs. Chaque consigna ateur ajouté à la communication recevra la même notification.

Pour configurer et envoyer un avis de suspension, vous devez inclure les notifications d’émission, de ré-émission et de mise en production.

### <a name="issuance-notification"></a>Notification d’émission

Une fois la communication créée, la **notification d’émission** est lancée par l’agent d’émission spécifié. La notification d’émission est la première communication envoyée au consignateur pour l’informer de ses obligations de conservation.

Pour créer une notification d’émission :

1. Dans la vignette **Émission** , cliquez sur **Modifier**.

2. Si nécessaire, ajoutez des membres de cas ou du personnel supplémentaires aux champs **Cc** et **Cci** . Pour ajouter plusieurs utilisateurs à ces champs, séparez les adresses e-mail avec un point-virgule.

3. Spécifiez **l’objet** de l’avis (obligatoire).

4. Spécifiez le contenu ou des instructions supplémentaires que vous souhaitez fournir au consignateur (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis d’émission.

5. Cliquez sur **Enregistrer**.

### <a name="re-issuance-notification"></a>notification Re-Issuance

À mesure que le cas progresse, les consignataires peuvent être tenus de conserver des données supplémentaires ou inférieures à celles qui ont été demandées précédemment. Une fois que vous avez mis à jour le contenu du portail, la notification de rééditation est envoyée et avertit les consignatateurs des modifications apportées à leurs obligations de conservation.

Pour créer une notification de rééditance :

1. Dans la vignette **Réissue** , cliquez sur **Modifier**.

2. Si nécessaire, ajoutez des membres de cas ou du personnel supplémentaires aux champs **Cc** et **Cci** . Pour ajouter plusieurs utilisateurs à ces champs, séparez les adresses e-mail avec un point-virgule.

3. Spécifiez **l’objet** de l’avis (obligatoire).

4. Spécifiez le contenu ou des instructions supplémentaires que vous souhaitez fournir au consignateur (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis de rééditation.

5. Cliquez sur **Enregistrer**.

> [!NOTE]
> Si le contenu du portail est modifié (dans la page Définir le contenu du **portail** dans l’Assistant **Modification de la communication** ), la notification de réélation est automatiquement envoyée à tous les consignatateurs affectés à l’avis. Une fois la notification envoyée, les consignatateurs sont invités à confirmer à nouveau leur avis de suspension. Si vous avez configuré des flux de travail de rappel ou d’escalade, ceux-ci redémarrent également. Pour plus d’informations sur les autres événements de gestion de cas qui déclenchent des communications, consultez [Événements qui déclenchent des notifications](#events-that-trigger-notifications).

### <a name="release-notification"></a>Notification de publication

Une fois qu’une question est résolue ou si un consignaculateur n’est plus soumis à la conservation du contenu, vous pouvez libérer le consignateur d’un cas. Si le consignateur a déjà reçu un avis de suspension, la notification de mise en production peut être utilisée pour avertir les consignatateurs qu’ils ont été libérés de leur obligation.

Pour créer une notification de mise en production :

1. Dans la vignette **Release** , cliquez sur **Modifier**.

2. Si nécessaire, ajoutez des membres de cas ou du personnel supplémentaires aux champs **Cc** et **Cci** . Pour ajouter plusieurs utilisateurs à ces champs, séparez les adresses e-mail avec un point-virgule.

3. Spécifiez **l’objet** de l’avis (obligatoire).

4. Spécifiez le contenu ou des instructions supplémentaires que vous souhaitez fournir au consignateur (obligatoire).

5. Cliquez sur **Enregistrer** et passez à l’étape suivante.

## <a name="optional-step-4-set-the-optional-notifications"></a>(Facultatif) Étape 4 : Définir les notifications facultatives

Si vous le souhaitez, vous pouvez simplifier le flux de travail pour effectuer un suivi avec des consignatateurs qui ne répondent pas en créant et en planifiant des notifications de rappel et d’escalade automatisées.

![Page Rappel/Escalade.](../media/ReminderEscalations.PNG)

### <a name="reminders"></a>Reminders

Une fois que vous avez envoyé une notification d’attente, vous pouvez effectuer un suivi avec les consignatateurs qui ne répondent pas en définissant un flux de travail de rappel.

Pour planifier des rappels :

1. Dans la vignette **Rappel** , cliquez sur **Modifier**.

2. Activez le flux de travail **De rappel** en activant le bouton bascule **État** (obligatoire).

3. Spécifiez **l’intervalle de rappel (en jours)** (obligatoire). Il s’agit du nombre de jours d’attente avant d’envoyer les premières notifications de rappel et de suivi. Par exemple, si vous définissez l’intervalle de rappel sur sept jours, le premier rappel est envoyé sept jours après l’émission initiale de la notification de suspension. Tous les rappels suivants seraient également envoyés tous les sept jours.

4. Spécifiez le **nombre de rappels** (obligatoire). Ce champ spécifie le nombre de rappels à envoyer aux consignatateurs qui ne répondent pas. Par exemple, si vous définissez le nombre de rappels sur 3, un gardien reçoit un maximum de trois rappels. Une fois qu’un consigna ateur a reconnu la notification de suspension, les rappels ne seront plus envoyés à cet utilisateur.

5. Spécifiez **l’objet** de l’avis (obligatoire).

6. Spécifiez le contenu ou des instructions supplémentaires que vous souhaitez fournir au consignateur (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis de rappel.

7. Cliquez sur **Enregistrer** et passez à l’étape suivante.

### <a name="escalations"></a>Escalades

Dans certains cas, vous aurez peut-être besoin de moyens supplémentaires de suivre les consignatateurs qui ne répondront pas. Si un dépositaire ne reconnaît pas une notification de suspension après avoir reçu le nombre spécifié de rappels, l’équipe juridique peut spécifier un flux de travail pour envoyer automatiquement une notification d’escalade au consignatien et à son responsable.

Pour planifier des escalades :

1. Dans la vignette **Escalade** , cliquez sur **Modifier**.

2. Activez le flux de travail **d’escalade** en activant le bouton bascule **État** .

3. Spécifiez **l’intervalle d’escalade (en jours)** (obligatoire).

4. Spécifiez le **nombre d’escalades** (obligatoire). Ce champ spécifie le nombre d’escalades à envoyer aux consignatateurs qui ne répondent pas. Par exemple, si vous définissez le nombre d’escalades sur 3, un avis d’escalade est envoyé au responsable et au responsable au maximum trois fois. Une fois qu’un consigna ateur a reconnu la notification de suspension, les escalades ne seront plus envoyées.

5. Spécifiez **l’objet** de l’avis (obligatoire).

6. Spécifiez le contenu ou des instructions supplémentaires que vous souhaitez fournir au consignateur (obligatoire). Le contenu du portail que vous avez défini à l’étape 2 est ajouté à la fin de l’avis d’escalade.

7. Cliquez sur **Enregistrer** et passez à l’étape suivante.

## <a name="step-5-assign-custodians-to-receive-notifications"></a>Étape 5 : Affecter des consignatateurs pour recevoir des notifications

Une fois que vous avez finalisé le contenu des notifications, sélectionnez les consignatateurs auxquels vous souhaitez envoyer des notifications.

![Page Sélectionner les consignatateurs.](../media/SelectCustodians.PNG)

Pour ajouter des consignatateurs :

1. Affectez les consignats à la communication en cliquant sur la case à cocher en regard de leur nom.

    Une fois la communication créée, le flux de travail de notification s’applique automatiquement aux consignatateurs sélectionnés.

2. Cliquez sur **Suivant** pour passer en revue les paramètres de communication et les détails.

> [!NOTE]
> Vous pouvez uniquement ajouter des consignatateurs qui ont été ajoutés au cas et qui n’ont pas reçu une autre notification dans le cas.

## <a name="step-6-review-settings"></a>Étape 6 : Vérifier les paramètres

Une fois que vous avez examiné les paramètres et que vous avez cliqué sur **Envoyer** pour terminer la communication, le système démarre automatiquement le flux de travail de communication en envoyant l’avis d’émission.

## <a name="events-that-trigger-notifications"></a>Événements qui déclenchent des notifications

Le tableau suivant décrit les événements du processus de gestion de cas qui se déclenchent lorsque les différents types de notifications sont envoyés aux consignataires.

|Type de communication|Déclencher |
|:---------|:---------|
|Avis d’émission|Création initiale de la notification. Vous pouvez également renvoyer manuellement une notification de suspension. |
|Avis de rééditance|Mise à jour du contenu du portail dans la page **Définir le contenu du portail** dans l’Assistant **Modification de la communication** .|
|Avis de publication|Le gardien est libéré de l’affaire.|
|Reminders|Intervalle et nombre de rappels configurés pour le rappel.|
|Escalades|Intervalle et nombre de rappels configurés pour l’escalade.|
|||
