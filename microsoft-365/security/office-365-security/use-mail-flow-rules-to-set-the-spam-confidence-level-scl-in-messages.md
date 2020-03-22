---
title: Utiliser des règles de flux de messagerie pour le SCL dans les messages
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 4ccab17a-6d49-4786-aa28-92fb28893e99
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à définir la valeur SCL des messages dans Exchange Online Protection.
ms.openlocfilehash: b7ea9a0f046e5a48f0de8d4ac9ae6d53821f03c0
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42895094"
---
# <a name="use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages"></a>Utilisation des règles de flux de courrier pour définir le seuil de probabilité de courrier indésirable (SCL) dans les messages

Si vous êtes un client Office 365 avec des boîtes aux lettres dans Exchange Online ou un client Exchange Online Protection (EOP) autonome sans boîte aux lettres Exchange Online, EOP utilise des stratégies de blocage du courrier indésirable (également appelées stratégies de filtrage du courrier indésirable ou stratégies de filtrage de contenu) pour analyser messages entrants pour le courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

Si vous souhaitez marquer des messages spécifiques comme courrier indésirable avant qu’ils soient encore analysés par le filtrage du courrier indésirable, ou marquer les messages de sorte qu’ils ignorent le filtrage du courrier indésirable, vous pouvez créer des règles de flux de messagerie (également appelées règles de transport) pour identifier les messages et définir le seuil de probabilité de courrier indésirable. Pour plus d’informations sur la valeur SCL, consultez la rubrique [Spam Confidence Level (SCL) in Office 365](spam-confidence-levels.md).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour pouvoir effectuer ces procédures, vous devez disposer d’autorisations dans Exchange Online. Plus précisément, vous devez disposer du rôle **de règles de transport** , qui est affecté aux rôles de gestion de l' **organisation**, de gestion de **la conformité**et de **gestion des enregistrements** par défaut. Pour plus d’informations, voir [Gérer les groupes de rôles dans Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/role-groups).

- Pour ouvrir le centre d’administration Exchange dans Exchange Online, consultez la rubrique [Exchange Admin Center in Exchange Online](https://docs.microsoft.com/Exchange/exchange-admin-center).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online, consultez la rubrique [mail Flow Rules (règles de transport) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) .

## <a name="use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message"></a>Utiliser le centre d’administration Exchange pour créer une règle de flux de messagerie qui définit la valeur SCL d’un message

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez sur **Ajouter** ![une](../../media/ITPro-EAC-AddIcon.png) icône Ajouter, puis sélectionnez **créer une nouvelle règle**.

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle.

   - Cliquez sur **Autres options**.

   - **Appliquer cette règle si**: sélectionnez une ou plusieurs conditions pour identifier les messages. Pour plus d’informations, consultez la rubrique [mail Flow Rule conditions and exceptions (prédicats) dans Exchange Online](https://docs.microsoft.com/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions).

   - **Procédez comme suit**: sélectionnez **modifier les propriétés** \> du message **définir le seuil de probabilité de courrier indésirable (SCL)**. Dans la boîte de dialogue spécifier la valeur **SCL** qui s’affiche, configurez l’une des valeurs suivantes :

   - **Contournement du filtrage du courrier indésirable**: définit la valeur SCL sur-1, ce qui signifie que les messages ignorent le filtrage du courrier indésirable.

     > [!CAUTION]
     > Soyez très vigilant lorsque vous autorisez les messages à ignorer le filtrage du courrier indésirable. Les attaquants peuvent utiliser cette vulnérabilité pour envoyer du hameçonnage et d’autres messages malveillants dans votre organisation. Les règles de flux de messagerie nécessitent plus que l’adresse de messagerie ou le domaine de l’expéditeur. Pour plus d’informations, consultez la rubrique [créer des listes d’expéditeurs approuvés dans Office 365](create-safe-sender-lists-in-office-365.md).

   - **0 à 4**: le message est envoyé par le biais du filtrage du courrier indésirable pour un traitement supplémentaire.

   - **5 ou 6**: le message est marqué comme **courrier indésirable**. L’action que vous avez configurée pour le filtrage du **courrier indésirable** dans vos stratégies de blocage du courrier indésirable est appliquée au message (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**).

   - **7 à 9**: le message est marqué comme **courrier indésirable à niveau de confiance élevé**. L’action que vous avez configurée pour le filtrage du **courrier indésirable à niveau de confiance élevé** les valeurs de votre stratégie de blocage du courrier indésirable est appliquée au message (la valeur par défaut est **déplacer le message vers le dossier courrier indésirable**).

4. Spécifiez les propriétés supplémentaires souhaitées pour la règle. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vous assurer que cette procédure fonctionne correctement, envoyez un message électronique à un membre de votre organisation et vérifiez que l'action effectuée sur le message correspond à celle prévue. Par exemple, si vous avez **défini le seuil de probabilité de courrier indésirable (SCL)** sur **Contourner le filtrage du courrier indésirable**, le message doit être envoyé vers la boîte de réception du destinataire spécifié. Cependant, si vous avez **défini le seuil de probabilité de courrier indésirable (SCL)** sur **9** et que l'action **Probabilité élevée de courrier indésirable** pour les stratégies de filtre de contenu applicables consiste à déplacer le message vers le dossier Courrier indésirable, le message doit être envoyé vers le dossier Courrier indésirable du destinataire spécifié.
