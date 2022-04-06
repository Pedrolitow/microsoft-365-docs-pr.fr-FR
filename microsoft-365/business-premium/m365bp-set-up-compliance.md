---
title: Renforcer la protection contre les menaces pour les Microsoft 365 Business Premium
f1.keywords:
- NOCSH
ms.author: deniseb
author: denisebmsft
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- M365-identity-device-management
- Adm_TOC
ms.custom:
- MiniMaven
- MSB365
- OKR_SMB_M365
- seo-marvel-mar
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
description: Configurer des fonctionnalités de conformité pour éviter la perte de données et sécuriser les informations sensibles de vos clients et de vos clients.
ms.openlocfilehash: 245a27c53951940f340dbb56c1b05a74d5dce249
ms.sourcegitcommit: adea59259a5900cad5de29ddf46d1ca9e9e1c82f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/04/2022
ms.locfileid: "64635342"
---
# <a name="set-up-compliance-features"></a>Configurer les fonctionnalités de conformité

Votre abonnement Microsoft 365 Business Premium inclut des fonctionnalités de conformité et de confidentialité. Ces fonctionnalités contribuent à protéger les données de votre entreprise et à sécuriser vos informations sensibles et celles de vos clients. Cet article est conçu pour vous aider à commencer avec vos fonctionnalités de conformité.

## <a name="before-you-begin"></a>Avant de commencer

Assurez-vous que l’un des rôles suivants est attribué dans Azure Active Directory :

- Administrateur général
- Administrateur de conformité

Pour plus d’informations, [voir Démarrage la page rôles](../admin/add-users/admin-roles-page.md).

## <a name="use-compliance-manager-to-get-started"></a>Utiliser le Gestionnaire de conformité pour commencer

:::image type="content" source="./media/m365bp-compliancemanager.png" alt-text="Capture d’écran du Gestionnaire de conformité dans Microsoft 365 Business Premium.":::

Microsoft 365 Business Premium inclut le Gestionnaire de conformité, qui peut vous aider à commencer la configuration de vos fonctionnalités de conformité. Ces fonctionnalités incluent la protection contre la perte de données, la gouvernance des informations et la gestion des risques internes, pour n’en citer que quelques-unes. Le Gestionnaire de conformité peut vous faire gagner du temps en mettant en évidence des recommandations, un score de conformité et des méthodes pour améliorer votre score.

Voici comment commencer :

1. Accédez à [https://compliance.microsoft.com](https://compliance.microsoft.com) et connectez-vous.

2. Dans le volet de navigation, choisissez **Gestionnaire de conformité**.

3. Sous **l’onglet Vue d’ensemble** , examinez les informations. Sélectionnez un élément ou un lien pour afficher plus d’informations ou pour prendre des mesures, telles que la configuration d’une stratégie de protection contre la perte de données (DLP). Par exemple, dans la section **Solutions qui affectent votre score** , vous pouvez sélectionner le lien dans la **colonne Actions restantes** .

   :::image type="content" source="./media/m365bp-compliancesolutions.png" alt-text="Capture d’écran des solutions qui affectent votre volet Score.":::

   Cette action vous permet d’obtenir l’onglet **Actions** d’amélioration, qui est filtré pour l’élément que vous avez sélectionné. Dans cet exemple, nous allons voir les stratégies DLP à configurer.

   :::image type="content" source="./media/m365bp-dlppoliciestoconfigure.png" alt-text="Capture d’écran des stratégies DLP à configurer.":::

4. Sous **l’onglet Actions d’amélioration** , sélectionnez un élément. Dans notre exemple, nous avons sélectionné Créer des stratégies DLP personnalisées ou **des informations d’identification personnelle**. Une page se charge et fournit plus d’informations sur la stratégie à configurer.

   :::image type="content" source="./media/m365bp-dlppolicyinfo.png" alt-text="Capture d’écran d’informations sur la stratégie DLP pour le contenu client.":::

   Suivez les informations à l’écran pour configurer votre stratégie DLP.

Pour plus d’informations sur les fonctionnalités de conformité Microsoft 365 pour les entreprises, voir [Microsoft 365 documentation de conformité](../compliance/index.yml).

## <a name="use-sensitivity-labels"></a>Utiliser des étiquettes de niveau de sensibilité

Les étiquettes de niveau de Office sont disponibles dans Office applications (telles que Outlook, Word, Excel et PowerPoint). Voici quelques exemples d’étiquettes :

- Normal
- Personnel
- Private
- Confidentiel

Toutefois, vous pouvez également définir d’autres étiquettes pour votre entreprise.

Utilisez les articles suivants pour commencer à utiliser les étiquettes de niveau de sensibilité :

1. [En savoir plus sur les étiquettes de niveau de sensibilité](../compliance/sensitivity-labels.md).

2. [Démarrage étiquettes de sensibilité](../compliance/get-started-with-sensitivity-labels.md).

3. [Créer et configurer des étiquettes de confidentialité et leurs stratégies](../compliance/create-sensitivity-labels.md).

4. [Montrer aux personnes de votre entreprise comment utiliser des étiquettes de sensibilité](https://support.microsoft.com/office/apply-sensitivity-labels-to-your-files-and-email-in-office-2f96e7cd-d5a4-403b-8bd7-4cc636bae0f9)