---
title: Mise en place de Microsoft Defender pour Endpoint Plan 1 (prévisualisation)
description: Commencer à utiliser Defender pour Endpoint Plan 1. Découvrez comment utiliser Defender pour le cloud, gérer les alertes et les appareils, et afficher des rapports.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 10/01/2021
ms.prod: m365-security
ms.technology: mde
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection: M365-security-compliance
ms.openlocfilehash: e361c8a93d35a9e0cc589b8d47adadfe54ef141b
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111134"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1-preview"></a>Mise en place de Microsoft Defender pour Endpoint Plan 1 (prévisualisation)

> [!TIP]
> Si vous avez Microsoft 365 E3 ou A3, mais pas Microsoft 365 E5 ou A5, visitez le site pour vous inscrire [https://aka.ms/mdep1trial](https://aka.ms/mdep1trial) au programme d’aperçu !

Le portail Microsoft 365 Defender ( ) vous permet d’afficher des informations sur les menaces détectées, de gérer vos alertes et incidents, d’agir sur les menaces détectées et de gérer les [https://security.microsoft.com](https://security.microsoft.com) appareils. Le portail Microsoft 365 Defender est l’endroit où vous pouvez commencer à interagir avec les fonctionnalités de protection contre les menaces que vous obtenez avec Defender for Endpoint Plan 1 (prévisualisation). Les sections suivantes décrivent comment commencer :

- [Portail Microsoft 365 Defender](#the-microsoft-365-defender-portal)
- [Affichage et gestion des incidents & alertes](#view-and-manage-incidents--alerts)
- [Gestion des appareils](#manage-devices)
- [Affichage des rapports](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Portail Microsoft 365 Defender

Le Microsoft 365 Defender ( ) vous permet d’afficher les alertes, de gérer les appareils [https://security.microsoft.com](https://security.microsoft.com) et d’afficher les rapports. Lorsque vous vous connectez au portail Microsoft 365 Defender, vous commencez par la page d’accueil, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Portail Microsoft 365 Defender":::

La page d’accueil fournit à votre équipe de sécurité une vue d’ensemble des alertes, de l’état de l’appareil et des menaces détectées. Defender pour le cloud est installé afin que votre équipe en matière d’opérations de sécurité puisse trouver rapidement et facilement les informations qu’elle recherche.

> [!NOTE]
> Nos exemples présentés dans cet article peuvent différer de ce que vous voyez sur votre portail Microsoft 365 Defender web. Ce que vous voyez dans votre portail dépend de vos licences et autorisations. En outre, votre équipe de sécurité peut personnaliser le portail de votre organisation en ajoutant, supprimant et réorganiser des cartes.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Les cartes mettent en évidence les informations clés et incluent des recommandations

La page d’accueil inclut des cartes, telles que la carte Incidents actifs affichée dans l’image suivante :

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Carte Incidents actifs":::

La carte vous fournit des informations en un coup d’œil, ainsi qu’un lien ou un bouton que vous pouvez sélectionner pour afficher des informations plus détaillées. En faisant référence à notre exemple de carte Incidents actifs, nous pouvons sélectionner Afficher tous les **incidents** pour accéder à notre liste d’incidents.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Liste des incidents":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>La barre de navigation facilite la recherche des alertes, du centre de données, et bien plus encore

La barre de navigation sur le côté gauche de l’écran vous permet de vous déplacer facilement entre les incidents, les alertes, le centre de mise en œuvre, les rapports et les paramètres. Le tableau suivant décrit la barre de navigation.<br/><br/>

| Élément de barre de navigation | Description |
|:---|:---|
| **Accueil** | Accédez à la page d’accueil du [portail Microsoft 365 Defender.](../defender/microsoft-365-security-center-mde.md) |
| **Incidents & alertes** | Se développe pour afficher **les incidents** et **les alertes.** |
| **Incidents & alertes**  >  **Incidents** | Permet d’accéder à **la liste Incidents.** Les incidents sont créés lorsque des alertes sont déclenchées et/ou que des menaces sont détectées. Par défaut, la liste **Incidents** affiche les données des 30 derniers jours, avec le dernier incident répertorié en premier. <br/><br/> Pour en savoir plus, consultez [Incidents.](view-incidents-queue.md) |
| **Incidents & alertes**  >  **Alertes** | Navigue vers la liste **Alertes** (également appelée file **d’attente des alertes).** Les alertes sont déclenchées lorsqu’un fichier, un processus ou un comportement suspect ou malveillant est détecté. Par défaut, la liste **Alertes** affiche les données des 30 derniers jours, la dernière alerte répertoriée en premier. <br/><br/> Pour plus d’informations, voir [Alertes.](alerts-queue.md) |
| **Centre de actions** | Navigue vers le centre de mise en œuvre, qui suit les actions de correction et de réponse manuelle. Le centre de suivi des activités comme celles-ci : <br/>- Antivirus Microsoft Defender un fichier malveillant, puis bloque/supprime ce fichier. <br/>- Votre équipe de sécurité isole un appareil.<br/>- Defender pour le point de terminaison détecte et met en quarantaine un fichier. <br/><br/> Pour en savoir plus, consultez le [Centre de l’action.](auto-investigation-action-center.md) |
| **Degré de sécurisation** | Affiche une représentation de la posture de sécurité de votre organisation, ainsi qu’une liste d’actions et de mesures d’amélioration. <br/><br/> Pour en savoir plus, [consultez Le Score de sécurité Microsoft.](../defender/microsoft-secure-score.md) |
| **Learning hub** | Accédez à la liste des parcours d’apprentissage accessibles pour en savoir plus sur Microsoft 365 fonctionnalités de sécurité.  |
| **Points de terminaison**  >  **Recherche** | Navigue vers une page où vous pouvez rechercher des appareils spécifiques par nom d’appareil. Dans la liste des résultats, vous pouvez voir les détails, tels que le niveau de risque et l’état de santé, en un coup d’œil. |
|  **Points de terminaison**  >  **Inventaire des appareils** | Permet d’accéder à la liste des appareils intégrés à Defender for Endpoint. Fournit des informations sur les appareils, telles que leur exposition et leurs niveaux de risque. <br/><br/> Pour en savoir plus, consultez [l’inventaire des appareils.](machines-view-overview.md) |
|  **Points de terminaison**  >  **Configuration & de référence** | Se développe pour afficher les **lignes de base de sécurité et** la gestion de la **configuration.** |
|  **Points de terminaison**  >  **Configuration et & base de référence**  >  **Bases de référence de sécurité** | Les lignes de base de sécurité sont des stratégies pré-configurées et des groupes de paramètres qui peuvent vous aider à appliquer efficacement et efficacement les paramètres de sécurité recommandés. Les lignes de base incluent des paramètres basés sur les meilleures pratiques du secteur. Vous pouvez conserver les paramètres par défaut ou personnaliser vos lignes de base en fonction des besoins de votre organisation. <br/><br/> Pour plus d’informations, voir Utiliser les lignes de base de sécurité pour [configurer les Windows 10 dans Intune.](/mem/intune/protect/security-baselines) |
|  **Points de terminaison**  >  **Configuration et & base de référence**  >  **Gestion de la configuration** | Accédez à la page Gestion de **la configuration** des appareils, où vous pouvez afficher des informations sur les appareils intégrés et prendre des mesures pour intégrer d’autres appareils. |
| **Rapports** | Accédez à vos rapports, tels que votre rapport sur la [protection](threat-protection-reports.md)contre les menaces, [](machine-reports.md)le rapport d’état et de conformité de l’appareil et votre rapport de protection [Web.](web-protection-overview.md) |
| **État d'intégrité** | Inclut des liens vers **l’état du service et** le centre de **messages.**  |
| **Santé**  >  **État du service** | Accédez à la page État du service dans le Centre d'administration Microsoft 365. Cette page vous permet d’afficher l’état d’état d’état dans tous les services disponibles avec les abonnements de votre organisation.   |
| **Santé**  >  **Centre de messages** | Navigue vers le centre de messages dans le Centre d'administration Microsoft 365. Le centre de messages fournit des informations sur les modifications planifiées. Chaque message décrit ce qui arrive, comment il peut affecter les utilisateurs et comment gérer les modifications. |  
| **Autorisations & rôles** | Vous permet d’accorder des autorisations d’utilisation du Microsoft 365 Defender web. Les autorisations sont accordées par le biais de rôles Azure Active Directory (Azure AD). Sélectionnez un rôle et un volet volant s’affiche. Le flyout contient un lien vers Azure AD où vous pouvez ajouter ou supprimer des membres dans un groupe de rôles. <br/><br/> Pour plus d’informations, voir [Gérer l’accès au portail à l’aide du contrôle d’accès basé sur les rôles.](rbac.md)  |
| **Paramètres** | Permet d’accéder aux paramètres généraux de votre portail Microsoft 365 Defender (répertorié en tant que centre de **sécurité)** et de Defender pour les points de terminaison (répertoriés en tant que points **de terminaison).** <br/><br/> Pour en savoir plus, [voir Paramètres](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Autres ressources** | Affiche une liste d’autres portails et centres, tels que les Azure Active Directory et les Centre de conformité Microsoft 365. <br/><br/> Pour en savoir plus, consultez [les portails de sécurité Microsoft et les centres d’administration.](../defender/portals.md) |

> [!TIP]
> Pour en savoir plus, consultez la [vue d’Microsoft 365 Defender portail d’entreprise.](../defender/microsoft-365-security-center-mde.md)

## <a name="view-and-manage-incidents--alerts"></a>Afficher et gérer les incidents & alertes

Lorsque vous vous connectez au portail Microsoft 365 Defender, veillez à afficher et à gérer vos incidents et alertes. Commencez par votre **liste Incidents.** L’image suivante montre une liste d’incidents, dont un avec une gravité élevée et un autre avec une gravité moyenne.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Liste des incidents":::

Sélectionnez un incident pour afficher les détails de l’incident. Les détails incluent les alertes déclenchées, le nombre d’appareils et d’utilisateurs affectés, ainsi que d’autres détails. L’image suivante montre un exemple de détails de l’incident.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Détails de l’incident":::

Utilisez les **onglets Alertes,** Périphériques et Utilisateurs pour afficher plus d’informations, telles que les alertes déclenchées, les appareils qui ont été affectés et les comptes d’utilisateur qui ont été affectés.   À partir de là, vous pouvez prendre des mesures de réponse manuelles, telles que l’isolation d’un appareil, l’arrêt et la mise en quarantaine d’un fichier, etc.

> [!TIP]
> Pour en savoir plus sur l’utilisation de **l’affichage Incident,** voir [Gérer les incidents.](manage-incidents.md)

## <a name="manage-devices"></a>Gestion des appareils

Pour afficher et gérer les appareils de votre organisation, dans la barre de navigation, sous Points de terminaison, sélectionnez **Inventaire des appareils.** Une liste d’appareils s’affiche, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Inventaire des appareils":::

La liste inclut les appareils pour lesquels des alertes ont été générées. Par défaut, les données affichées datent des 30 derniers jours, les éléments les plus récents sont répertoriés en premier. Sélectionnez un appareil pour afficher plus d’informations à son sujet. Un volet volant s’ouvre, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Détails de l’appareil sélectionné":::

Le volet volant affiche des détails, tels que les alertes actives de l’appareil, et inclut des liens pour prendre des mesures, comme l’isolation d’un appareil.

S’il existe des alertes actives sur l’appareil, vous pouvez les afficher dans le volet volant. Sélectionnez une alerte individuelle pour afficher plus de détails à son sujet. Vous pouvez également prendre une action, par exemple isoler l’appareil, afin de pouvoir examiner l’appareil plus en détail tout en réduisant le risque d’infecter d’autres appareils.

> [!TIP]
> Pour plus d’informations, voir Examiner les appareils dans la liste Des appareils [Defender pour les points de terminaison.](investigate-machines.md)

## <a name="view-reports"></a>Affichage des rapports

Dans Defender for Endpoint Plan 1, plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender endpoint. Pour accéder à vos rapports, suivez les étapes suivantes :

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Dans la barre de navigation, choisissez **Rapports.**

3. Sélectionnez un rapport dans la liste. Vous verrez les trois rapports suivants :

   - Rapport de protection contre les menaces
   - Rapport d’état de l’appareil
   - Rapport sur la protection web

> [!TIP]
> Pour plus d’informations, voir [rapports sur la protection contre les menaces.](threat-protection-reports.md)

### <a name="threat-protection-report"></a>Rapport de protection contre les menaces

Pour accéder à votre rapport sur la protection contre les menaces, dans le portail Microsoft 365 Defender, choisissez **Rapports,** puis **choisissez Protection contre les menaces.** Le rapport sur la protection contre les menaces affiche les tendances, l’état, les catégories et bien plus encore des alertes. Les affichages sont organisés en deux colonnes : tendances **d’alerte** et état de l’alerte, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Rapport de protection contre les menaces":::

Faites défiler vers le bas pour voir tous les affichages de chaque liste.

- Par défaut, les  affichages de la colonne Tendances d’alerte affichent les données des 30 derniers jours, mais vous pouvez définir un affichage pour afficher les données des trois derniers mois, des six derniers mois ou d’une plage de temps personnalisée (jusqu’à 180 jours).
- Les affichages dans la colonne **État de l’alerte** sont un instantané de la journée d’activité précédente.

> [!TIP]
> Pour en savoir plus, consultez le rapport [sur la protection contre les menaces dans Defender for Endpoint.](threat-protection-reports.md)

### <a name="device-health-report"></a>Rapport d’état de l’appareil

Pour accéder à votre rapport d’état de l’appareil, dans le portail Microsoft 365 Defender, choisissez **Rapports,** puis sélectionnez État **de l’appareil.** Le rapport d’état de l’appareil affiche l’état d’état d’état et l’antivirus sur tous les appareils de votre organisation. À l’image du rapport [sur la](#threat-protection-report)  protection contre les menaces, les affichages sont organisés en deux colonnes : Tendances des appareils et Résumé des **appareils,** comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Rapport d’état de l’appareil":::

Faites défiler vers le bas pour voir tous les affichages de chaque liste. Par défaut, les  affichages de la colonne Tendances de l’appareil affichent les données des 30 derniers jours, mais vous pouvez modifier un affichage pour afficher les données des trois derniers mois, des six derniers mois ou d’une plage de temps personnalisée (jusqu’à 180 jours). Les **vues récapitulatifs de l’appareil** sont des captures instantanées du jour oué précédent.

> [!TIP]
> Pour en savoir plus, consultez [l’état de l’appareil.](machine-reports.md)

### <a name="web-protection-report"></a>Rapport sur la protection web

Pour accéder à votre rapport d’état de l’appareil, dans le portail Microsoft 365 Defender, choisissez **Rapports,** puis **choisissez Protection Web.** Le rapport de protection Web affiche les détections au fil du temps, telles que les URL malveillantes et les tentatives d’accès aux URL bloquées, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Rapport sur la protection web":::

Faites défiler vers le bas pour voir tous les affichages dans le rapport de protection Web. Certains affichages incluent des liens qui vous permettent d’afficher plus de détails, de configurer vos fonctionnalités de protection contre les menaces et même de gérer les indicateurs qui font office d’exceptions dans Defender for Endpoint.

> [!TIP]
> Pour en savoir plus, consultez [La protection Web.](web-protection-overview.md)

## <a name="next-steps"></a>Prochaines étapes

- [Gérer Microsoft Defender pour Endpoint Plan 1 (prévisualisation)](mde-p1-maintenance-operations.md)
- [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md)
