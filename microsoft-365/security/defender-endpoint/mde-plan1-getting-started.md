---
title: Démarrage avec Microsoft Defender pour point de terminaison Plan 1
description: Démarrage à l’aide de Defender pour point de terminaison Plan 1. Découvrez comment utiliser le Defender pour le cloud, gérer les alertes et les appareils et afficher des rapports.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: overview
ms.date: 01/03/2022
ms.prod: m365-security
ms.technology: mdep1
ms.localizationpriority: medium
ms.reviewer: inbadian
f1.keywords: NOCSH
ms.collection:
- M365-security-compliance
- m365initiative-defender-endpoint
ms.custom: intro-get-started
ms.openlocfilehash: d332cbf32f5423fb16abb158f9a30a18c2391a22
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64939342"
---
# <a name="get-started-with-microsoft-defender-for-endpoint-plan-1"></a>Démarrage avec Microsoft Defender pour point de terminaison Plan 1

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) vous permet d’afficher des informations sur les menaces détectées, de gérer vos alertes et incidents, d’effectuer les actions nécessaires sur les menaces détectées et de gérer les appareils. Le portail Microsoft 365 Defender vous permet de commencer à interagir avec les fonctionnalités de protection contre les menaces que vous obtenez avec Defender pour point de terminaison Plan 1. Les sections suivantes décrivent comment commencer :

- [Portail Microsoft 365 Defender](#the-microsoft-365-defender-portal)
- [Affichage et gestion des incidents & alertes](#view-and-manage-incidents--alerts)
- [Gestion des appareils](#manage-devices)
- [Affichage des rapports](#view-reports)

## <a name="the-microsoft-365-defender-portal"></a>Portail Microsoft 365 Defender

Le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) vous permet d’afficher les alertes, de gérer les appareils et d’afficher des rapports. Lorsque vous vous connectez au portail Microsoft 365 Defender, vous commencez par la page d’accueil, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/m365-defender-portal.png" alt-text="Le portail de Microsoft 365 Defender" lightbox="../../media/mde-p1/m365-defender-portal.png":::

La page d’accueil fournit à votre équipe de sécurité une vue agrégée d’instantanés des alertes, de l’état de l’appareil et des menaces détectées. La Defender pour le cloud est configurée pour que votre équipe des opérations de sécurité puisse trouver rapidement et facilement les informations qu’elle recherche.

> [!NOTE]
> Nos exemples présentés dans cet article peuvent différer de ce que vous voyez dans votre portail Microsoft 365 Defender. Ce que vous voyez dans votre portail dépend de vos licences et autorisations. En outre, votre équipe de sécurité peut personnaliser le portail de votre organisation en ajoutant, en supprimant et en réorganisant des cartes.

### <a name="cards-highlight-key-information-and-include-recommendations"></a>Les cartes mettent en évidence les informations clés et incluent des recommandations

La page d’accueil inclut des cartes, telles que la carte Incidents actifs affichée dans l’image suivante :

:::image type="content" source="../../media/mde-p1/active-incidents-card.png" alt-text="Carte Incidents actifs" lightbox="../../media/mde-p1/active-incidents-card.png":::

La carte vous fournit des informations en un clin d’œil, ainsi qu’un lien ou un bouton que vous pouvez sélectionner pour afficher des informations plus détaillées. En faisant référence à notre exemple de carte d’incidents actifs, nous pouvons sélectionner **Afficher tous les incidents** pour accéder à notre liste d’incidents.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Liste des incidents" lightbox="../../media/mde-p1/incidents.png":::

### <a name="navigation-bar-makes-it-easy-to-find-alerts-the-action-center-and-more"></a>La barre de navigation facilite la recherche d’alertes, le centre d’actions et bien plus encore

La barre de navigation sur le côté gauche de l’écran vous permet de vous déplacer facilement entre les incidents, les alertes, le centre d’action, les rapports et les paramètres. Le tableau suivant décrit la barre de navigation.<br/><br/>

| Élément de barre de navigation | Description |
|:---|:---|
| **Accueil** | Accède à la page d’accueil du [portail Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md). |
| **Incidents & alertes** | S’étend pour afficher **les incidents** et **les alertes**. |
| **Incidents & alertes** >  **Incidents** | Accède à la liste **des incidents** . Des incidents sont créés lorsque des alertes sont déclenchées et/ou des menaces sont détectées. Par défaut, la liste **des incidents affiche les** données des 30 derniers jours, avec l’incident le plus récent répertorié en premier. <br/><br/> Pour en savoir plus, consultez [Incidents](view-incidents-queue.md). |
| **Incidents & alertes** >  **Alertes** | Accède à la liste **des alertes** (également appelée file **d’attente d’alertes**). Les alertes sont déclenchées lorsqu’un fichier, un processus ou un comportement suspect ou malveillant est détecté. Par défaut, la liste **Des alertes affiche les** données des 30 derniers jours, avec la dernière alerte répertoriée en premier. <br/><br/> Pour en savoir plus, consultez [Alertes](alerts-queue.md). |
| **Centre de notifications** | Accède au Centre d’actions, qui effectue le suivi des actions de correction et de réponse manuelle. Le Centre d’action effectue le suivi des activités comme suit : <br/>- Antivirus Microsoft Defender rencontre un fichier malveillant, puis bloque/supprime ce fichier. <br/>- Votre équipe de sécurité isole un appareil.<br/>- Defender pour point de terminaison détecte et met en quarantaine un fichier. <br/><br/> Pour en savoir plus, consultez [le Centre d’actions](auto-investigation-action-center.md). |
| **Degré de sécurisation** | Affiche une représentation de la posture de sécurité de votre organisation, ainsi qu’une liste d’actions d’amélioration et de métriques. <br/><br/> Pour plus d’informations, consultez [Microsoft Secure Score](../defender/microsoft-secure-score.md). |
| **hub Learning** | Accédez à la liste des parcours d’apprentissage auxquels vous pouvez accéder pour en savoir plus sur Microsoft 365 fonctionnalités de sécurité.  |
| **Terminaison** >  **Rechercher** | Accède à une page dans laquelle vous pouvez rechercher des appareils spécifiques par nom d’appareil. Dans la liste des résultats, vous pouvez voir des détails, tels que le niveau de risque et l’état d’intégrité, en un clin d’œil. |
|  **Terminaison** >  **Inventaire des appareils** | Accède à votre liste d’appareils intégrés à Defender pour point de terminaison. Fournit des informations sur les appareils, telles que leur niveau d’exposition et de risque. <br/><br/> Pour plus d’informations, consultez [l’inventaire des appareils](machines-view-overview.md). |
|  **Terminaison** >  **Lignes de base de & de configuration** | S’étend pour afficher **les bases de référence de sécurité** et **la gestion de la configuration**. |
|  **Terminaison** >  Lignes  >  **de base de & de configuration** **Bases de référence de sécurité** | Les bases de référence de sécurité sont des stratégies préconfigurées et des groupes de paramètres qui peuvent vous aider à appliquer les paramètres de sécurité recommandés de manière efficace et efficace. Les lignes de base incluent des paramètres basés sur les meilleures pratiques de l’industrie. Vous pouvez conserver les paramètres par défaut ou personnaliser vos bases de référence en fonction des besoins de votre organisation. <br/><br/> Pour plus d’informations, consultez [Utiliser les bases de référence de sécurité pour configurer Windows 10 appareils dans Intune](/mem/intune/protect/security-baselines). |
|  **Terminaison** >  Lignes  >  **de base de & de configuration** **Gestion de la configuration** | Accède à la page **gestion de la configuration** des appareils, où vous pouvez afficher des informations sur les appareils intégrés et prendre des mesures pour intégrer davantage d’appareils. |
| **Rapports** | Accède à vos rapports, tels que votre [rapport de protection contre les menaces](threat-protection-reports.md), le [rapport d’intégrité et de conformité](machine-reports.md) des appareils et votre [rapport de protection web](web-protection-overview.md). |
| **État d'intégrité** | Inclut des liens vers le **État des services** et le **centre de messages**.  |
| **Santé** >  **État des services** | Accède à la page État des services dans le Centre d'administration Microsoft 365. Cette page vous permet d’afficher l’état d’intégrité de tous les services disponibles avec les abonnements de votre organisation.   |
| **Santé** >  **Centre de messages** | Accède au centre de messages dans le Centre d'administration Microsoft 365. Le centre de messages fournit des informations sur les modifications planifiées. Chaque message décrit ce qui s’en vient, comment il peut affecter les utilisateurs et comment gérer les modifications. |  
| **Autorisations & rôles** | Vous permet d’accorder des autorisations pour utiliser le portail Microsoft 365 Defender. Les autorisations sont accordées par le biais de rôles dans Azure Active Directory (Azure AD). Sélectionnez un rôle et un volet volant s’affiche. Le menu volant contient un lien vers Azure AD où vous pouvez ajouter ou supprimer des membres dans un groupe de rôles. <br/><br/> Pour plus d’informations, consultez [Gérer l’accès au portail à l’aide du contrôle d’accès en fonction du rôle](rbac.md).  |
| **Paramètres** | Accède aux paramètres généraux de votre portail Microsoft 365 Defender (listé en tant que **Centre de sécurité**) et Defender pour point de terminaison (répertoriés en tant que points de **terminaison**). <br/><br/> Pour en savoir plus, consultez [Paramètres](../defender/microsoft-365-defender.md#the-microsoft-365-defender-portal). |
| **Autres ressources** | Affiche une liste d’autres portails et centres, tels que Azure Active Directory et le portail de conformité Microsoft Purview. <br/><br/> Pour plus d’informations, consultez [les portails de sécurité et les centres d’administration Microsoft](../defender/portals.md). |

> [!TIP]
> Pour en savoir plus, consultez la [vue d’ensemble du portail Microsoft 365 Defender](../defender/microsoft-365-security-center-mde.md).

## <a name="view-and-manage-incidents--alerts"></a>Afficher et gérer les incidents & les alertes

Lorsque vous vous connectez au portail Microsoft 365 Defender, veillez à afficher et à gérer vos incidents et alertes. Commencez par votre liste **d’incidents** . L’image suivante montre une liste d’incidents, dont un avec une gravité élevée et un autre avec une gravité moyenne.

:::image type="content" source="../../media/mde-p1/incidents.png" alt-text="Liste des incidents":::

Sélectionnez un incident pour afficher les détails de l’incident. Les détails incluent les alertes qui ont été déclenchées, le nombre d’appareils et d’utilisateurs affectés, ainsi que d’autres détails. L’image suivante montre un exemple de détails de l’incident.

:::image type="content" source="../../media/mde-p1/single-incident.png" alt-text="Détails d’un incident" lightbox="../../media/mde-p1/single-incident.png":::

Utilisez les **onglets Alertes**, **Appareils** et **Utilisateurs** pour afficher plus d’informations, telles que les alertes déclenchées, les appareils affectés et les comptes d’utilisateurs affectés. À partir de là, vous pouvez effectuer des actions de réponse manuelles, telles que l’isolation d’un appareil, l’arrêt et la mise en quarantaine d’un fichier, etc.

> [!TIP]
> Pour en savoir plus sur l’utilisation de la vue **Incident** , consultez [Gérer les incidents](manage-incidents.md).

## <a name="manage-devices"></a>Gestion des appareils

Pour afficher et gérer les appareils de votre organisation, dans la barre de navigation, sous **Points de terminaison**, sélectionnez **Inventaire** des appareils. Vous verrez une liste d’appareils, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/device-inventory.png" alt-text="Inventaire des appareils" lightbox="../../media/mde-p1/device-inventory.png":::

La liste inclut les appareils pour lesquels des alertes ont été générées. Par défaut, les données affichées sont pour les 30 derniers jours, avec les éléments les plus récents répertoriés en premier. Sélectionnez un appareil pour afficher plus d’informations à son sujet. Un volet volant s’ouvre, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/device-inventory-selecteddevice.png" alt-text="Détails de l’appareil sélectionné" lightbox="../../media/mde-p1/device-inventory-selecteddevice.png":::

Le volet de menu volant affiche des détails, tels que toutes les alertes actives pour l’appareil, et inclut des liens pour prendre des mesures, telles que l’isolation d’un appareil.

S’il existe des alertes actives sur l’appareil, vous pouvez les afficher dans le volet volant. Sélectionnez une alerte individuelle pour afficher plus de détails à son sujet. Vous pouvez également effectuer une action, telle que **Isoler l’appareil**, afin que vous puissiez examiner l’appareil plus en détail tout en réduisant le risque d’infecter d’autres appareils.

> [!TIP]
> Pour plus d’informations, consultez [Examiner les appareils dans la liste des appareils Defender pour point de terminaison](investigate-machines.md).

## <a name="view-reports"></a>Affichage des rapports

Dans Defender pour point de terminaison Plan 1, plusieurs rapports sont disponibles dans le portail Microsoft 365 Defender. Pour accéder à vos rapports, procédez comme suit :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Dans la barre de navigation, choisissez **Rapports**.

3. Sélectionnez un rapport dans la liste. Vous verrez les trois rapports suivants :

   - Rapport de protection contre les menaces
   - Rapport d’intégrité de l’appareil
   - Rapport de protection web

> [!TIP]
> Pour plus d’informations, consultez [les rapports de protection contre les menaces](threat-protection-reports.md).

### <a name="threat-protection-report"></a>Rapport de protection contre les menaces

Pour accéder à votre rapport de protection contre les menaces, dans le portail Microsoft 365 Defender, choisissez **Rapports**, puis la **protection contre les menaces**. Le rapport Protection contre les menaces affiche les tendances, l’état, les catégories et bien plus encore des alertes. Les vues sont organisées en deux colonnes : **Tendances des alertes** et **état de l’alerte**, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/threat-protection-report.png" alt-text="Rapport de protection contre les menaces" lightbox="../../media/mde-p1/threat-protection-report.png":::

Faites défiler vers le bas pour afficher toutes les vues de chaque liste.

- Par défaut, les vues de la colonne **Tendances d’alerte** affichent les données des 30 derniers jours, mais vous pouvez définir une vue pour afficher les données des trois derniers mois, des six derniers mois ou une plage de temps personnalisée (jusqu’à 180 jours).
- Les vues de la colonne **État d’alerte** sont un instantané du jour ouvré précédent.

> [!TIP]
> Pour en savoir plus, consultez le [rapport de protection contre les menaces dans Defender pour point de terminaison](threat-protection-reports.md).

### <a name="device-health-report"></a>Rapport d’intégrité de l’appareil

Pour accéder à votre rapport d’intégrité de l’appareil, dans le portail Microsoft 365 Defender, choisissez **Rapports**, puis **l’intégrité de l’appareil**. Le rapport d’intégrité de l’appareil affiche l’état d’intégrité et l’antivirus sur les appareils de votre organisation. À l’instar du [rapport sur la protection contre les menaces](#threat-protection-report), les affichages sont organisés en deux colonnes : **Tendances des appareils** et résumé de l’appareil, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/device-health-report.png" alt-text="Rapport d’intégrité de l’appareil" lightbox="../../media/mde-p1/device-health-report.png":::

Faites défiler vers le bas pour afficher toutes les vues de chaque liste. Par défaut, les vues de la colonne **Tendances de l’appareil** affichent les données des 30 derniers jours, mais vous pouvez modifier une vue pour afficher les données des trois derniers mois, des six derniers mois ou une plage de temps personnalisée (jusqu’à 180 jours). Les vues **récapitulatives de l’appareil** sont des instantanés du jour ouvré précédent.

> [!TIP]
> Pour en savoir plus, consultez [Intégrité de l’appareil](machine-reports.md).

### <a name="web-protection-report"></a>Rapport de protection web

Pour accéder à votre rapport d’intégrité de l’appareil, dans le portail Microsoft 365 Defender, choisissez **Rapports**, puis la **protection web**. Le rapport de protection web affiche les détections au fil du temps, telles que les URL malveillantes et les tentatives d’accès aux URL bloquées, comme illustré dans l’image suivante :

:::image type="content" source="../../media/mde-p1/web-protection-report.png" alt-text="Rapport de protection web" lightbox="../../media/mde-p1/web-protection-report.png":::

Faites défiler vers le bas pour afficher toutes les vues dans le rapport de protection web. Certaines vues incluent des liens qui vous permettent d’afficher plus de détails, de configurer vos fonctionnalités de protection contre les menaces et même de gérer les indicateurs qui servent d’exceptions dans Defender pour point de terminaison.

> [!TIP]
> Pour plus d’informations, consultez [La protection web](web-protection-overview.md).

## <a name="next-steps"></a>Étapes suivantes

- [Gérer Microsoft Defender pour point de terminaison plan 1](mde-p1-maintenance-operations.md)
- [Microsoft Defender pour point de terminaison](microsoft-defender-endpoint.md)
