---
title: Microsoft Defender pour point de terminaison dans Microsoft 365 Defender
description: En savoir plus sur les modifications apportées à la Centre de sécurité Microsoft Defender à Microsoft 365 Defender
keywords: Bien démarrer avec Microsoft 365 Defender, Microsoft Defender pour Office 365, Microsoft Defender pour point de terminaison, MDO, MDE, portail de sécurité, portail de sécurité Defender
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.localizationpriority: medium
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 04/21/2021
audience: ITPro
ms.topic: article
search.appverid:
- MOE150
- MET150
ms.collection:
- M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.openlocfilehash: 9669e0788197f59f6d46c0475a89c67310e32ec9
ms.sourcegitcommit: 217108c59be41b01963a393b4f16d137636fe6a8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/12/2022
ms.locfileid: "67328604"
---
# <a name="microsoft-defender-for-endpoint-in-microsoft-365-defender"></a>Microsoft Defender pour point de terminaison dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)

## <a name="quick-reference"></a>Référence rapide

L’image et le tableau ci-dessous répertorient les modifications apportées à la navigation entre les Centre de sécurité Microsoft Defender et les Microsoft 365 Defender.

> [!div class="mx-imgBorder"]
> :::image type="content" source="../../media/mde-m3d-security-center.png" alt-text="Nouveaux emplacements dans le portail Microsoft 365 Defender" lightbox="../../media/mde-m3d-security-center.png":::

| Centre de sécurité Microsoft Defender | Microsoft 365 Defender |
|---------|---------|
| Tableaux de bord <ul><li>Opérations de sécurité</li><li>Analyses de menaces</li></ul>  |Famille <ul><li>Analyses de menaces</li></ul>   |
| Incidents | Incidents et alertes |
| Inventaire des appareils | Inventaire des appareils |
| File d’attente des alertes | Incidents et alertes |
| Enquêtes automatisées | Centre de notifications |
| Recherche avancée de menaces | Repérage |
| Rapports | Rapports |
| API & partenaires | API & partenaires |
| Gestion des vulnérabilités de Microsoft Defender | Gestion des vulnérabilités |
| Évaluation et didacticiels | Didacticiels & d’évaluation |
| Gestion de la configuration | Gestion de la configuration |
| Paramètres | Paramètres | 

Le [Microsoft 365 Defender](microsoft-365-defender-portal.md) <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a> amélioré combine les fonctionnalités de sécurité qui protègent, détectent, examinent et répondent aux menaces de messagerie, de collaboration, d’identité et d’appareil. Cela regroupe les fonctionnalités des portails de sécurité Microsoft existants, notamment Centre de sécurité Microsoft Defender et le centre de conformité Office 365 Security &.

Si vous connaissez bien les Centre de sécurité Microsoft Defender, cet article décrit quelques-unes des modifications et améliorations apportées à Microsoft 365 Defender. Toutefois, certains éléments nouveaux et mis à jour doivent être pris en compte.

Historiquement, le [Centre de sécurité Microsoft Defender](/windows/security/threat-protection/microsoft-defender-atp/portal-overview) a été le foyer de Microsoft Defender pour point de terminaison. Les équipes de sécurité d’entreprise l’ont utilisée pour surveiller et aider à répondre aux alertes de menaces persistantes avancées potentielles ou de violations de données. Pour réduire le nombre de portails, Microsoft 365 Defender sera le point d’accueil de la surveillance et de la gestion de la sécurité sur vos identités, données, appareils, applications et infrastructure Microsoft.

Microsoft Defender pour point de terminaison dans Microsoft 365 Defender prend en charge [l’octroi de l’accès aux fournisseurs de services de sécurité gérés (MSSP)](/windows/security/threat-protection/microsoft-defender-atp/grant-mssp-access) de la même façon que [l’accès est accordé dans le Centre de sécurité Microsoft Defender](mssp-access.md).

> [!IMPORTANT]
> Ce que vous voyez dans Microsoft 365 Defender dépend de vos abonnements actuels. Par exemple, si vous n’avez pas de licence pour Microsoft Defender pour Office 365, la section Email & Collaboration ne s’affiche pas.

> [!Note]
> Microsoft 365 Defender n’est pas disponible pour :
>- Cloud de la communauté du gouvernement des États-Unis (GCC)
>- US Government Community Cloud High (GCC High)
>- Département de la Défense des États-Unis
>- Toutes les institutions gouvernementales américaines disposant de licences commerciales

Jetez un coup d’œil dans Microsoft 365 Defender à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">https://security.microsoft.com</a>.

En savoir plus sur les avantages : [Vue d’ensemble de Microsoft 365 Defender](microsoft-365-defender.md)

## <a name="whats-changed"></a>Fonctionnalités modifiées

Ce tableau est une référence rapide des modifications entre le Centre de sécurité Microsoft Defender et le Microsoft 365 Defender.

### <a name="alerts-and-actions"></a>Alertes et actions

| Zone | Description de la modification |
|---------|---------|
| [Incidents & alertes](incidents-overview.md)  | Dans Microsoft 365 Defender, vous pouvez gérer les incidents et les alertes sur tous vos points de terminaison, e-mails et identités. Nous avons convergé l’expérience pour vous aider à trouver des événements connexes plus facilement. Pour plus d’informations, consultez [La vue d’ensemble des incidents](incidents-overview.md).   |
| [Repérage](advanced-hunting-overview.md)  |  La modification des règles de détection personnalisées créées dans Microsoft Defender pour point de terminaison pour inclure les tables d’identité et de messagerie les déplace automatiquement vers Microsoft 365 Defender. Leurs alertes correspondantes s’affichent également dans Microsoft 365 Defender. Pour plus d’informations sur ces modifications, consultez [Migrer des règles de détection personnalisées](advanced-hunting-migrate-from-mde.md#migrate-custom-detection-rules). <br><br>La `DeviceAlertEvents` table pour la chasse avancée n’est pas disponible dans Microsoft 365 Defender. Pour interroger les informations d’alerte spécifiques à l’appareil dans Microsoft 365 Defender, vous pouvez utiliser les tables et `AlertEvidence` les `AlertInfo` tables pour prendre en charge davantage d’informations provenant d’un ensemble diversifié de sources. Créez votre prochaine requête liée à l’appareil en suivant [les requêtes d’écriture sans DeviceAlertEvents](advanced-hunting-migrate-from-mde.md#write-queries-without-devicealertevents).|
|[Centre d’action](m365d-action-center.md)    | Répertorie les actions en attente et terminées qui ont été effectuées à la suite d’enquêtes automatisées et d’actions de correction. Auparavant, le Centre d’actions de l’Centre de sécurité Microsoft Defender listé les actions en attente et terminées pour les actions de correction effectuées sur les appareils uniquement, tandis que les enquêtes automatisées répertoriaient les alertes et l’état. Dans le Microsoft 365 Defender amélioré, le Centre d’action regroupe les actions de correction et les investigations sur les e-mails, les appareils et les utilisateurs, le tout dans un même emplacement.  |
| [Analyses de menaces](threat-analytics.md) |  Déplacé vers le haut de la barre de navigation pour faciliter la découverte et l’utilisation. Inclut désormais des informations sur les menaces pour les points de terminaison et la messagerie et la collaboration.    |

### <a name="endpoints"></a>Points de terminaison

| Zone | Description de la modification |
|---------|---------|
|Rechercher   |  La barre de recherche se trouve en haut de la page. Des suggestions sont fournies à mesure que vous tapez. Vous pouvez rechercher parmi les entités suivantes dans Defender pour point de terminaison et Defender pour Identity : <br><br> - **Appareils** pris en charge pour Defender pour point de terminaison et Defender pour Identity. Vous pouvez même utiliser des opérateurs de recherche, par exemple, vous pouvez utiliser « contains » pour rechercher une partie d’un nom d’hôte. <br><br> - **Utilisateurs** : pris en charge à la fois pour Defender pour point de terminaison et Defender pour Identity. <br><br> - **Fichiers, adresses IP et URL** - mêmes fonctionnalités que dans Defender pour point de terminaison. <br> REMARQUE : *Les recherches d’ADRESSEs IP et d’URL correspondent exactement et n’apparaissent pas dans la page des résultats de la recherche : elles mènent directement à la page d’entité.  <br><br> - **MDVM** : mêmes fonctionnalités que dans Defender pour point de terminaison (vulnérabilités, logiciels et recommandations). <br><br>  La page des résultats de recherche améliorés centralise les résultats de toutes les entités.  |
|[Tableau de bord](/windows/security/threat-protection/microsoft-defender-atp/security-operations-dashboard)   |  Il s’agit de votre tableau de bord des opérations de sécurité. Consultez une vue d’ensemble du nombre d’alertes actives déclenchées, des appareils à risque, des utilisateurs à risque et du niveau de gravité pour les alertes, les appareils et les utilisateurs. Vous pouvez également voir si des appareils ont des problèmes de capteur, l’intégrité globale de votre service et comment des alertes non résolues ont été détectées. |
|Inventaire des appareils | Aucune modification. |
|[Gestion des vulnérabilités](/windows/security/threat-protection/microsoft-defender-atp/next-gen-threat-and-vuln-mgt)    |    Le nom a été raccourci pour tenir dans le volet de navigation. Il est identique à la section Gestion des vulnérabilités Microsoft Defender, avec toutes les pages en dessous.     |
| Partenaires et API | Aucune modification. |
| Didacticiels sur les évaluations &    |     Nouvelles fonctionnalités de test et d’apprentissage.     |
| Gestion de la configuration   |  Aucune modification.  |

> [!NOTE]
> **L’examen et la correction automatiques** font désormais partie des incidents. Vous pouvez voir les événements d’investigation et de correction automatisés dans l’onglet **Incident > Investigation** .

> [!TIP]
> La recherche d’appareils est effectuée à partir des points de terminaison > la recherche.

### <a name="access-and-reporting"></a>Accès et création de rapports

| Zone | Description de la modification |
|---------|---------|
| Rapports  | Consultez les rapports pour les points de terminaison et la collaboration par e-mail &, notamment la protection contre les menaces, l’intégrité et la conformité des appareils et les appareils vulnérables. |
| Intégrité  |  Il est actuellement lié à la page « État des services » du [Centre d'administration Microsoft 365](https://admin.microsoft.com/). |
| Paramètres |  Gérez vos paramètres pour les Microsoft 365 Defender, les points de terminaison, la collaboration Email &, les identités et la découverte d’appareils.   |

## <a name="microsoft-365-security-navigation-and-capabilities"></a>Navigation et fonctionnalités de sécurité Microsoft 365

La barre de navigation gauche, ou la barre de lancement rapide, vous semblera familière. Toutefois, il existe des éléments nouveaux et mis à jour dans Microsoft 365 Defender portail. 

### <a name="incidents-and-alerts"></a>Incidents et alertes

Réunit les incidents et la gestion des alertes de vos e-mail, appareils, et identités. La page d’alerte fournit un contexte complet à l’alerte en combinant les signaux d’attaque pour construire une histoire détaillée. Une nouvelle expérience unifiée réunit désormais un affichage cohérent des alertes des charges de travail. Vous pouvez rapidement trier, examiner et prendre des mesures efficaces.

- [En savoir plus sur les incidents](incidents-overview.md)
- [En savoir plus sur la gestion des alertes](investigate-alerts.md).

:::image type="content" source="../../media/converge-1-alerts-and-actions.png" alt-text="Barre de lancement rapide Alertes et actions dans le portail Microsoft 365 Defender" lightbox="../../media/converge-1-alerts-and-actions.png":::

### <a name="hunting"></a>Repérage

Recherchez de façon proactive les menaces, les programmes malveillants et des activités malveillantes sur vos points de terminaison, boîtes aux lettres Office 365, etc. à l’aide de [Requêtes de repérage avancé](advanced-hunting-overview.md). Ces requêtes puissantes peuvent être utilisées pour rechercher et examiner les indicateurs et entités de menaces pour les menaces connues et potentielles.

[Des règles de détection personnalisées](custom-detection-rules.md) peuvent être créées à partir de requêtes de repérage avancées pour vous aider à surveiller de manière proactive les événements qui peuvent indiquer une activité de violation et des appareils mal configurés.


### <a name="action-center"></a>Centre de notifications

Le centre d’action montre les enquêtes créées par les fonctionnalités automatisées d’enquête et de réponse. Ce système automatisé et self-healing dans Microsoft 365 Defender peut aider les équipes de sécurité en répondant automatiquement à des événements spécifiques.

[En savoir plus sur le Centre d’actions](m365d-action-center.md).

### <a name="threat-analytics"></a>Analyses de menaces

Obtenez des informations sur threat Intelligence auprès de chercheurs chevronnés de la sécurité Microsoft. Les analyses de menaces permettent aux équipes de sécurité d’être plus efficaces face aux menaces émergentes. L’analyse des menaces inclut :

- Détections et atténuations liées à la messagerie à partir de Microsoft Defender pour Office 365. Cela s’ajoute aux données de point de terminaison déjà disponibles auprès de Microsoft Defender pour les points de terminaison.
- Les affichages d’incidents liés aux menaces.
- Expérience améliorée pour identifier et utiliser rapidement les informations utilisables dans les rapports.

Vous pouvez accéder à l’analytique des menaces à partir de la barre de navigation supérieure gauche dans Microsoft 365 Defender, ou à partir d’une carte de tableau de bord dédiée qui affiche les principales menaces pour votre organisation.

En savoir plus sur le [suivi et la réponse aux menaces émergentes avec l’analytique des menaces](./threat-analytics.md).

### <a name="endpoints-section"></a>Section Points de terminaison

Affichez et gérez la sécurité des points de terminaison dans votre organisation. Si vous avez utilisé la Centre de sécurité Microsoft Defender, elle vous sera familière.

:::image type="content" source="../../media/converge-2-endpoints.png" alt-text="Barre de lancement rapide des points de terminaison dans le portail Microsoft 365 Defender" lightbox="../../media/converge-2-endpoints.png":::

### <a name="access-and-reports"></a>Accès et rapports

Afficher des rapports, modifier vos paramètres, et modifier les rôles d’un utilisateur.

:::image type="content" source="../../media/converge-4-access-and-reporting-new.png" alt-text="Barre de lancement rapide Accès et création de rapports dans le portail Microsoft 365 Defender" lightbox="../../media/converge-4-access-and-reporting-new.png":::

### <a name="siem-api-connections"></a>Connexions d’API SIEM

Si vous utilisez [l’API SIEM Defender pour](../defender-endpoint/enable-siem-integration.md) point de terminaison, vous pouvez continuer à le faire. Nous avons ajouté de nouveaux liens sur la charge utile de l’API qui pointent vers la page d’alerte ou la page d’incident dans le portail de sécurité Microsoft 365. Les nouveaux champs d’API incluent LinkToMTP et IncidentLinkToMTP. Pour plus d’informations, consultez [Redirection de comptes de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="email-alerts"></a>alertes Email

Vous pouvez continuer à utiliser des alertes par e-mail pour Defender pour point de terminaison. Nous avons ajouté de nouveaux liens dans les e-mails qui pointent vers la page d’alerte ou la page d’incident dans Microsoft 365 Defender. Pour plus d’informations, consultez [Redirection de comptes de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender](./microsoft-365-security-mde-redirection.md).

### <a name="managed-security-service-providers-mssp"></a>Fournisseurs de services de sécurité managé (MSSP)

La connexion à plusieurs locataires simultanément dans la même session de navigation n’est actuellement pas prise en charge dans le portail unifié. Vous pouvez désactiver la redirection automatique [en rétablissant l’ancien portail Microsoft Defender pour point de terminaison](microsoft-365-security-mde-redirection.md#can-i-go-back-to-using-the-former-portal) pour conserver cette fonctionnalité jusqu’à ce que le problème soit résolu.

## <a name="related-information"></a>Informations connexes

- [Microsoft 365 Defender](microsoft-365-defender.md)
- [Microsoft Defender pour point de terminaison dans Microsoft 365 Defender](microsoft-365-security-center-mde.md)
- [Redirection de comptes de Microsoft Defender pour point de terminaison vers Microsoft 365 Defender](microsoft-365-security-mde-redirection.md)
