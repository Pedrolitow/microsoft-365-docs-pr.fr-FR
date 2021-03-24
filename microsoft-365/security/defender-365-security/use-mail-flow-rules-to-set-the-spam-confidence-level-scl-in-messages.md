---
title: Utiliser des règles de flux de messagerie pour le SCL dans les messages
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 4ccab17a-6d49-4786-aa28-92fb28893e99
ms.collection:
- M365-security-compliance
description: Découvrez comment créer des règles de flux de messagerie (règles de transport) pour identifier les messages et définir le niveau de confiance du courrier indésirable (SCL) des messages dans Exchange Online Protection.
ms.custom: seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 795347046342ea17870e7758a6327facf51315a4
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51061894"
---
# <a name="use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages-in-eop"></a>Utiliser des règles de flux de messagerie pour définir le niveau de confiance du courrier indésirable (SCL) dans les messages dans EOP

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 Plan 1 et Plan 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Dans les organisations Microsoft 365 ayant des boîtes aux lettres dans Exchange Online ou des organisations Exchange Online Protection autonomes (EOP) sans boîtes aux lettres Exchange Online, EOP utilise des stratégies anti-courrier indésirable (également appelées stratégies de filtrage du courrier indésirable ou stratégies de filtrage de contenu) pour analyser les messages entrants à la recherche de courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Si vous souhaitez marquer des messages spécifiques comme courrier indésirable avant même d’être analysés par le filtrage du courrier indésirable, ou marquer des messages afin qu’ils ignorent le filtrage du courrier indésirable, vous pouvez créer des règles de flux de messagerie (également appelées règles de transport) pour identifier les messages et définir le niveau de confiance du courrier indésirable (SCL). Pour plus d’informations sur le SCL, voir Le niveau de confiance du courrier indésirable [(SCL) dans EOP.](spam-confidence-levels.md)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Des autorisations doivent vous être attribuées dans Exchange Online ou Exchange Online Protection avant de pouvoir suivre les procédures de cet article. Plus précisément, vous avez besoin du rôle Règles de **transport,** qui est  attribué par défaut aux groupes de rôles Gestion de l’organisation, Gestion de la conformité **(administrateurs** globaux) et Gestion des enregistrements.

  Pour plus d’informations, voir les rubriques suivantes :

  - [Autorisations dans Exchange Online](/exchange/permissions-exo/permissions-exo)
  - [Autorisations dans EOP autonome](feature-permissions-in-eop.md)
  - [Utiliser le EAC pour modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups)

- Pour ouvrir le Centre d’administration Exchange (EAC) dans Exchange Online, consultez le [Centre d’administration Exchange dans Exchange Online.](/Exchange/exchange-admin-center) Pour ouvrir le CAE dans EOP autonome, consultez le Centre [d’administration Exchange dans EOP autonome.](exchange-admin-center-in-exchange-online-protection-eop.md)

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Pour plus d’informations sur les règles de flux de messagerie dans Exchange Online et Exchange Online Protection, voir Règles de flux de messagerie [(règles de transport) dans Exchange Online](/Exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

## <a name="use-the-eac-to-create-a-mail-flow-rule-that-sets-the-scl-of-a-message"></a>Utiliser le EAC pour créer une règle de flux de messagerie qui définit le SCL d’un message

1. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

2. Cliquez **sur Ajouter** une icône ![ ](../../media/ITPro-EAC-AddIcon.png) Ajouter, puis **sélectionnez Créer une règle.**

3. Dans la page **Nouvelle règle** qui s'ouvre, configurez les paramètres suivants :

   - **Nom**: entrez un nom unique et descriptif pour la règle.

   - Cliquez sur **Autres options**.

   - **Appliquez cette règle si**: sélectionnez une ou plusieurs conditions pour identifier les messages. Pour plus d’informations, voir Conditions et exceptions de règle de flux de messagerie [(prédicats) dans Exchange Online.](/Exchange/security-and-compliance/mail-flow-rules/conditions-and-exceptions)

   - **Pour ce faire,** **sélectionnez Modifier les propriétés du message** pour définir le niveau de \> **confiance du courrier indésirable (SCL).** Dans la **boîte de dialogue Spécifier le SCL** qui s’affiche, configurez l’une des valeurs suivantes :

   - **Contourner le filtrage du courrier indésirable**: les messages ignorent le filtrage du courrier indésirable.

     > [!CAUTION]
     > Soyez très prudent lorsque vous autorisez les messages à ignorer le filtrage du courrier indésirable. Les attaquants peuvent utiliser cette vulnérabilité pour envoyer du hameçonnage et d’autres messages malveillants à votre organisation. Les règles de flux de messagerie ne nécessitent pas seulement l’adresse de messagerie ou le domaine de l’expéditeur. Pour plus d’informations, voir [Créer des listes d’expéditeurs sûrs dans EOP.](create-safe-sender-lists-in-office-365.md)

   - **0 à 4 :** le message est envoyé par le biais du filtrage du courrier indésirable pour traitement supplémentaire.

   - **5 ou 6 :** le message est marqué comme courrier **indésirable.** L’action que vous avez  configurée pour les verdicts de filtrage du courrier indésirable dans vos stratégies anti-courrier indésirable est appliquée au message (la valeur par défaut est Déplacer le message vers le dossier Courrier **indésirable).**

   - **7 à 9 :** le message est marqué comme courrier indésirable à **niveau de confiance élevé.** L’action que vous avez  configurée pour les verdicts de filtrage du courrier indésirable à niveau de confiance élevé dans vos stratégies anti-courrier indésirable est appliquée au message (la valeur par défaut est Déplacer le message vers le dossier Courrier **indésirable).**

4. Spécifiez les propriétés supplémentaires que vous souhaitez pour la règle. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

## <a name="how-do-you-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vous assurer que cette procédure fonctionne correctement, envoyez un message électronique à un membre de votre organisation et vérifiez que l'action effectuée sur le message correspond à celle prévue. Par exemple, si vous avez **défini le seuil de probabilité de courrier indésirable (SCL)** sur **Contourner le filtrage du courrier indésirable**, le message doit être envoyé vers la boîte de réception du destinataire spécifié. Toutefois, si vous définissez le niveau de confiance du courrier indésirable **sur** **9** et que l’action  de courrier indésirable à niveau de confiance élevé pour vos stratégies anti-courrier indésirable applicables consiste à déplacer le message vers le dossier Courrier indésirable, le message doit être envoyé vers le dossier Courrier indésirable du destinataire spécifié.