---
title: Score de productivité Microsoft-confidentialité
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: Sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
monikerRange: o365-worldwide
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ROBOTS: NOINDEX, NOFOLLOW
description: La protection de la confidentialité avec le score de productivité.
ms.openlocfilehash: 799d532ca1f0abd5fa6234052d4875a79d629601
ms.sourcegitcommit: 2160e7cf373f992dd4d11793a59cb8c44f8d587e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/26/2020
ms.locfileid: "48287245"
---
# <a name="privacy-controls-for-productivity-score"></a>Contrôles de confidentialité du score de productivité

Le score de productivité aide les organisations à transformer le travail réalisé grâce à des informations sur la façon dont les utilisateurs utilisent Microsoft 365 et les expériences technologiques qui les prennent en charge. Le score reflète les performances de votre organisation&#39;s par rapport aux mesures relatives aux employés et aux technologies et compare votre score avec des organisations comme les vôtres. Pour plus d’informations, consultez la rubrique [vue d’ensemble](productivity-score.md) de la note de productivité.

Votre confidentialité est importante pour nous et vous pouvez consulter la déclaration de confidentialité de Microsoft [ici](https://privacy.microsoft.com/privacystatement). Dans la note de productivité, il existe des informations importantes sur la façon dont les employés de votre organisation travaillent. Par conséquent, nous souhaitons également vous fournir des contrôles pour vous assurer que les informations sont exploitables d’une manière significative tout en ne compromettant pas l’approbation que vous placez dans nous.

Nous fournissons les contrôles suivants pour permettre une gestion plus sûre des données :

- Des rôles d’administrateur flexibles permettant de contrôler qui peut voir les informations dans le score de productivité.
- Anonymisation des mesures de niveau utilisateur.
- Possibilité de refuser l’expérience de l’employé.

## <a name="flexible-admin-roles-to-control-who-can-see-the-information-in-productivity-score"></a>Rôles d’administrateur flexibles permettant de contrôler qui peut voir les informations dans le score de productivité

Pour afficher l’intégralité de la fonction de score de productivité avec un rôle d’administrateur, y compris les informations de niveau client et les détails au niveau de chaque utilisateur, votre rôle doit être l’un des suivants :

- Administrateur global
- Administrateurs Exchange
- Administrateur SharePoint
- Administrateur pour Skype Entreprise
- Administrateur Teams
- Lecteur général
- Lecteur de rapports

Pour inviter des personnes responsables de la gestion et de l’adoption des modifications, mais qui ne sont pas des administrateurs informatiques dans l’expérience, tout en leur donnant accès à l’expérience complète, y compris les informations de niveau client et les détails au niveau de chaque utilisateur, vous pouvez leur donner le rôle de lecteur de rapport.

Dans l’expérience de l’employé, nous fournissons les détails de l’activité par utilisateur au format grille pour chaque page de détails de catégorie. Dans la mesure où ce niveau de détail n’est pas adapté à tous les visiteurs potentiels du score de productivité, nous avons créé un rôle personnalisé dans Azure AD – rôle de lecteur de rapports de synthèse de l’utilisation – pour permettre l’accès à un ensemble plus large de visiteurs au sein de votre organisation, uniquement aux métriques agrégées et aux détails par niveau au sein de l’expérience.

:::image type="content" source="../../media/communicationspage.jpg" alt-text="Page communications dans les rapports de productivité.":::

## <a name="anonymization-of-user-level-metrics"></a>Anonymisation des mesures de niveau utilisateur

Pour que les données collectées pour tous les rapports soient anonymes, vous devez être administrateur général. Cela masque les informations identifiables telles que les noms d’utilisateur, de groupe et de site dans tous les rapports, y compris la note de productivité et l’utilisation de Microsoft 365.

1. Dans le centre d’administration, accédez à **Settings**paramètres d'   >   **organisation** paramètres, puis, sous l’onglet **services** , choisissez **rapports**.
2. Sélectionnez  **rapports** , puis choisissez d'  **afficher les identificateurs anonymes pour les noms d’utilisateur, de groupe et de site dans score de productivité et rapports d’utilisation**. Ce paramètre est appliqué à la fois aux rapports d’utilisation ainsi qu’à l’application de modèle.
3. Sélectionnez  **enregistrer les modifications**.

:::image type="content" source="../../media/orgsettings_anonymous.jpg" alt-text="Rendez les informations utilisateur anonymes pour les rapports.":::

## <a name="capability-to-opt-out-of-employee-experience"></a>Possibilité de désactiver l’expérience de l’employé

Nous allons également permettre de désactiver la zone de productivité de l’employé du score de productivité à la disponibilité générale. Activer ce paramètre permet d’empêcher quiconque de votre organisation de voir ces mesures et de supprimer votre organisation des calculs impliquant des catégories de communication, de réunions, de travail d’équipe, de collaboration de contenu et de mobilité.

1. Dans le centre d’administration, accédez à **Settings**paramètres d'   >   **organisation** paramètres, puis, sous l’onglet **services** , choisissez **rapports**.
2. Sélectionnez  **rapports** , puis désactivez la case à cocher  **partager vos données org&#39;s avec le score de productivité Insights**. Pour comprendre comment modifier les paramètres de partage de données pour l’analyse des points de terminaison dans le gestionnaire de configuration Intune, cliquez sur **en savoir plus**.
3. Sélectionnez  **enregistrer les modifications**.

:::image type="content" source="../../media/orgsettingspageoptout.jpg" alt-text="Page Paramètres de l’organisation dans laquelle vous pouvez désactiver l’expérience de l’employé.":::