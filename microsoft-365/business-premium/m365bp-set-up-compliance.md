---
title: Configurer les fonctionnalités de conformité
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: dansimp
audience: Admin
ms.topic: how-to
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: high
ms.date: 07/19/2022
ms.custom:
- MiniMaven
search.appverid:
- BCS160
- MET150
description: Configurez des fonctionnalités de conformité pour éviter la perte de données et sécuriser les informations sensibles de vos clients et de vos clients.
ms.openlocfilehash: 996976f0f003cbb2f145d1c450273bec003d08ab
ms.sourcegitcommit: 651610ca73bfd1d008d97311b59782790df664fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2022
ms.locfileid: "67613843"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité


Consultez l’[aide de Microsoft 365 Petite Entreprise](https://go.microsoft.com/fwlink/?linkid=2197659) sur YouTube.

Votre abonnement Microsoft 365 Business Premium inclut des fonctionnalités de conformité et de confidentialité. Ces fonctionnalités permettent de protéger les données de votre entreprise et de sécuriser vos informations sensibles et celles de vos clients. Cet article est conçu pour vous aider à bien démarrer avec vos fonctionnalités de conformité.


## <a name="before-you-begin"></a>Avant de commencer

Vérifiez que l’un des rôles suivants est attribué dans Azure Active Directory :

- Administrateur général
- Administrateur de conformité

Pour en savoir plus, consultez [Démarrage avec la page rôles](../admin/add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>Utiliser le Gestionnaire de conformité pour commencer

:::image type="content" source="./media/m365bp-compliancemanager.png" alt-text="Capture d’écran du Gestionnaire de conformité dans Microsoft 365 Business Premium.":::

Microsoft 365 Business Premium inclut le Gestionnaire de conformité, qui peut vous aider à commencer à configurer vos fonctionnalités de conformité. Ces fonctionnalités incluent la protection contre la perte de données, la gestion du cycle de vie des données et la gestion des risques internes, pour n’en citer que quelques-uns. Le Gestionnaire de conformité peut vous faire gagner du temps en mettant en évidence des recommandations, un score de conformité et des moyens d’améliorer votre score.

Voici comment procéder :

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous.

2. Dans le volet de navigation, choisissez **Gestionnaire de conformité**.

3. Sous l’onglet **Vue d’ensemble** , passez en revue les informations. Sélectionnez un élément ou un lien pour afficher plus d’informations ou pour prendre des mesures, telles que la configuration d’une stratégie de protection contre la perte de données (DLP). Par exemple, dans la section **Solutions qui affectent votre score**, vous pouvez sélectionner le lien dans la colonne **Actions restantes** .

   :::image type="content" source="./media/m365bp-compliancesolutions.png" alt-text="capture d’écran des solutions qui affectent votre volet Score.":::

   Cette action vous permet d’accéder à l’onglet **Actions d’amélioration**, qui est filtré pour l’élément que vous avez sélectionné. Dans cet exemple, nous examinons les stratégies DLP à configurer.

   :::image type="content" source="./media/m365bp-dlppoliciestoconfigure.png" alt-text="Capture d’écran des stratégies DLP à configurer.":::

4. Sous l’onglet **Actions d’amélioration**, sélectionnez un élément. Dans notre exemple, nous avons sélectionné **Créer des stratégies DLP personnalisées ou des informations d’identification personnelle**. Une page charge qui fournit plus d’informations sur la stratégie à configurer.

   :::image type="content" source="./media/m365bp-dlppolicyinfo.png" alt-text="Capture d’écran des informations sur la stratégie DLP pour le contenu client.":::

   Suivez les informations à l’écran pour configurer votre stratégie DLP.

Pour plus d’informations sur les fonctionnalités de conformité dans Microsoft 365 pour les entreprises, consultez la[documentation Microsoft Purview](../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>Utiliser des étiquettes de confidentialité

Regardez cette vidéo et d’autres sur notre [Chaîne YouTube](https://go.microsoft.com/fwlink/?linkid=2198022).

Les étiquettes de confidentialité sont disponibles dans les applications Office (comme Outlook, Word, Excel et PowerPoint). Voici quelques exemples d’étiquettes :

- Normal
- Personnel
- Private
- Confidentiel

Toutefois, vous pouvez également définir d’autres étiquettes pour votre entreprise.

Utilisez les articles suivants pour bien démarrer avec les étiquettes de confidentialité :

1. [En savoir plus sur les étiquettes de confidentialité](../compliance/sensitivity-labels.md).

2. [Démarrage avec des étiquettes de confidentialité](../compliance/get-started-with-sensitivity-labels.md).

3. [Créer et configurer des étiquettes de confidentialité et leurs stratégies](../compliance/create-sensitivity-labels.md).

4. [Montrer aux membres de votre entreprise comment utiliser des étiquettes de confidentialité](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)