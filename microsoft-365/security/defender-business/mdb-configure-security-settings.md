---
title: Afficher et modifier vos paramètres de sécurité dans Microsoft Defender entreprise
description: Configurer vos stratégies de sécurité dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/24/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 4fbc4dc4b5b8628b075d5e6d5a91f760e322a6cf
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63329808"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Afficher et modifier vos stratégies et paramètres de sécurité dans Microsoft Defender entreprise

> [!IMPORTANT]
> Microsoft Defender for Business est en déploiement Microsoft 365 Business Premium clients, à partir du 1er mars 2022. Defender for Business as a standalone subscription is in preview, and will roll out gradually to customers and IT Partners who [sign-up here](https://aka.ms/mdb-preview) to request it. La [prévisualisation inclut un ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

## <a name="overview"></a>Vue d’ensemble

Une fois que vous avez intégré les appareils de votre organisation à Microsoft Defender pour Entreprises, l’étape suivante consiste à afficher et, si nécessaire, à modifier vos stratégies et paramètres de sécurité. Les stratégies de sécurité sont les suivantes :

- **[Stratégies de protection nouvelle génération](#view-or-edit-your-next-generation-protection-policies)**, qui déterminent la protection antivirus et anti-programme malveillant pour les appareils de votre organisation
- **[Protection et règles de pare-feu](#view-or-edit-your-firewall-policies-and-custom-rules)**, qui déterminent le trafic réseau autorisé à circuler vers ou depuis les appareils de votre organisation
- **[Filtrage de contenu Web](#set-up-web-content-filtering)**, qui empêche les utilisateurs de visiter certains sites web (URL) en fonction de catégories, telles que le contenu pour adultes ou la responsabilité légale.

Dans Defender entreprise, les stratégies de sécurité sont appliquées aux appareils via des groupes [d’appareils](mdb-create-edit-device-groups.md#what-is-a-device-group). 

Outre vos stratégies de sécurité, vous pouvez afficher et modifier des [paramètres](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), tels que le fuseau horaire à utiliser dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et s’il faut recevoir les fonctionnalités d’aperçu dès qu’elles sont disponibles.

Utilisez cet article comme guide pour gérer vos stratégies et paramètres de sécurité.

## <a name="what-to-do"></a>Procédure

1. [Choisissez où gérer vos stratégies et appareils de sécurité](#choose-where-to-manage-security-policies-and-devices).

2. [Afficher ou modifier vos stratégies de protection nouvelle génération](#view-or-edit-your-next-generation-protection-policies).

3. [Afficher ou modifier vos stratégies de pare-feu et règles personnalisées](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Configurer le filtrage de contenu web](#set-up-web-content-filtering).

5. [Afficher et modifier d’autres paramètres dans Microsoft 365 Defender portail.](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal) 

6. [Procédez comme vous le faire pour les étapes suivantes](#next-steps).

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Choisir où gérer les stratégies et les appareils de sécurité

Defender for Business propose un [processus de configuration simplifié](mdb-simplified-configuration.md) qui simplifie le processus d’installation et de configuration. Si vous sélectionnez le processus de configuration simplifié, vous pouvez afficher et gérer vos stratégies de sécurité dans le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Toutefois, vous n’êtes pas limité à cette option. Si vous avez utilisé Microsoft Endpoint Manager (Microsoft Intune), vous pouvez continuer à utiliser votre Endpoint Manager.

Le tableau suivant peut vous aider à choisir l’endroit où gérer vos stratégies et appareils de sécurité. <br/><br/>

| Option | Description |
|:---|:---|
| **Utiliser le Microsoft 365 Defender web** (*recommandé*) | Le Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) peut être votre magasin unique pour la gestion des appareils, des stratégies de sécurité et des paramètres de sécurité de votre organisation. Vous pouvez accéder à vos stratégies et paramètres de sécurité, utiliser votre tableau de bord gestion des menaces [&](mdb-view-tvm-dashboard.md) vulnérabilités, et afficher et gérer les [incidents](mdb-view-manage-incidents.md) au même endroit.  |
| **Utiliser Microsoft Endpoint Manager** | Si votre organisation utilise déjà Endpoint Manager (qui inclut Microsoft Intune) pour gérer les stratégies de sécurité, vous pouvez continuer à utiliser Endpoint Manager pour gérer les appareils et les stratégies de sécurité. Pour plus d’informations, voir [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Si vous décidez de basculer vers le processus de configuration simplifiée dans [Defender for Business](mdb-simplified-configuration.md) pour utiliser le portail Microsoft 365 Defender à la place, vous serez invité à supprimer les stratégies de sécurité existantes dans Endpoint Manager afin d’éviter les conflits [](mdb-troubleshooting.yml) de stratégie ultérieurement. |

> [!NOTE]
> Si vous gérez nos stratégies de sécurité dans le portail Microsoft 365 Defender, vous pouvez  afficher ces stratégies dans Endpoint Manager, répertoriées en tant que stratégies antivirus ou pare-feu. Lorsque vous affichez vos stratégies de pare-feu dans Endpoint Manager, deux stratégies sont répertoriées : une stratégie pour la protection de votre pare-feu et une autre pour les règles personnalisées.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Afficher ou modifier vos stratégies de protection nouvelle génération

Selon que vous utilisez le portail Microsoft 365 Defender ou Microsoft Endpoint Manager pour gérer vos stratégies de protection nouvelle génération, utilisez l’une des procédures du tableau suivant : <br/><br/>

| Portail | Procedure |
|:---|:---|
| Microsoft 365 Defender portail ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par exemple **, Windows clients**).<br/><br/>4. Développez **la protection nouvelle génération** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Comprendre les paramètres de configuration nouvelle génération](mdb-next-gen-configuration-settings.md)  |
| Microsoft Endpoint Manager admin center ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Go to [https://endpoint.microsoft.com](https://endpoint.microsoft.com) and sign in. Vous êtes maintenant dans le centre d Microsoft Endpoint Manager’administration.<br/><br/>2. Sélectionnez **Sécurité des points de terminaison**.<br/><br/>3. Sélectionnez **Antivirus** pour afficher vos stratégies dans cette catégorie. <br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Microsoft Endpoint Manager, commencez par gérer la sécurité des points de [terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Afficher ou modifier vos stratégies de pare-feu et règles personnalisées

Selon que vous utilisez le portail Microsoft 365 Defender ou Microsoft Endpoint Manager pour gérer la protection de votre pare-feu, utilisez l’une des procédures du tableau suivant : <br/><br/>

| Portail | Procedure |
|:---|:---|
| Microsoft 365 Defender portail ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par exemple **, Windows clients**).<br/><br/>4. Développez le **Pare-feu** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Paramètres du pare-feu](mdb-firewall.md)<br/>- [Gérer vos règles personnalisées pour les stratégies de pare-feu](mdb-custom-rules-firewall.md)  |
| Microsoft Endpoint Manager admin center ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Go to [https://endpoint.microsoft.com](https://endpoint.microsoft.com) and sign in. Vous êtes maintenant dans le centre d Microsoft Endpoint Manager’administration.<br/><br/>2. Sélectionnez **Sécurité des points de terminaison**.<br/><br/>3. Sélectionnez **Pare-feu** pour afficher vos stratégies dans cette catégorie. Les règles personnalisées définies pour la protection pare-feu sont répertoriées en tant que stratégies distinctes.<br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Microsoft Endpoint Manager, commencez par gérer la sécurité des points de [terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Configurer le filtrage de contenu web

Le filtrage de contenu Web permet à votre équipe de sécurité de suivre et de contrôler l’accès aux sites web en fonction de leurs catégories de contenu, telles que :

- Contenu pour adultes : sites liés à des activités sexuelles, à des jeux d’argent, à la nudité, à la créativité, à du matériel explicite ou à la violence
- Bande passante élevée : télécharger des sites, des sites de partage d’images ou des hôtes d’égal à égal
- Responsabilité légale : sites qui incluent des images d’abus enfants, promeuvent des activités illégales, encouragent le plagiarisme ou la violence scolaire, ou qui promeuvent des activités dangereuses
- Événement : sites qui fournissent des salles de conversation web, des jeux en ligne, des e-mails web ou des réseaux sociaux
- Non catégorisé : sites qui n’ont pas de contenu ou qui sont nouvellement inscrits

Tous les sites web de ces catégories ne sont pas malveillants, mais ils peuvent être problématiques pour votre organisation en raison de réglementations de conformité, d’utilisation de la bande passante ou d’autres problèmes. En outre, vous pouvez créer une stratégie d’audit uniquement pour mieux comprendre si votre équipe de sécurité doit bloquer les catégories de sites web.

Le filtrage de contenu Web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et la Protection du réseau (Chrome, Firefox, Firefox et Opera). Pour plus d’informations, [voir Conditions préalables pour le filtrage de contenu web](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Pour configurer le filtrage de contenu web

1. Dans le portail Microsoft 365 Defender web ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Paramètres** >  **de contenu Web** > **+ Ajouter une stratégie**.

2. Spécifiez un nom et une description pour votre stratégie.

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer entièrement chaque catégorie parent et sélectionner des catégories de contenu web spécifiques.

   Pour configurer une stratégie d’audit uniquement qui ne bloque aucun site web, ne sélectionnez aucune catégorie.

   Ne sélectionnez **pas Uncategorized**.

4. Spécifiez l’étendue de la stratégie en sélectionnant des groupes d’appareils pour appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne pourront pas accéder aux sites web dans les catégories sélectionnées.

5. Examinez le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à 2 heures pour s’appliquer à vos appareils sélectionnés.

> [!TIP]
> Pour en savoir plus sur le filtrage de contenu web, voir [Filtrage de contenu Web](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Afficher et modifier d’autres paramètres dans le portail Microsoft 365 Defender web

Outre les stratégies de sécurité appliquées aux appareils, vous pouvez afficher et modifier d’autres paramètres dans Defender for Business. Par exemple, vous spécifiez le fuseau horaire à utiliser, et vous pouvez intégrer (ou horsboard) des appareils. 

> [!NOTE]
> Vous pouvez voir plus de paramètres dans votre client que ceux répertoriés dans cet article. Cet article met en évidence les paramètres les plus importants que vous devez examiner dans Defender for Business.

### <a name="settings-to-review-for-defender-for-business"></a>Paramètres à réviser pour Defender for Business

Le tableau suivant décrit les paramètres à afficher (et, si nécessaire, modifier) dans Defender for Business.

<br/><br/>

| Catégorie | Setting | Description |
|:---|:---|:---|
| **Centre de sécurité** | **Fuseau horaire** | Sélectionnez le fuseau horaire à utiliser pour les dates et heures affichées dans les incidents, les menaces détectées et les examens automatisés & correction. Vous pouvez utiliser l’heure UTC ou votre fuseau horaire local (*recommandé*).  |
| **Microsoft 365 Defender** | **Account** | Afficher des détails, tels que l’endroit où vos données sont stockées, votre ID de client et l’ID de votre organisation (organisation). |
| **Microsoft 365 Defender**  | **Fonctionnalités en préversion**  | Activer les fonctionnalités d’aperçu pour essayer les fonctionnalités à venir et les nouvelles fonctionnalités. Vous pouvez être parmi les premiers à afficher un aperçu des nouvelles fonctionnalités et à fournir des commentaires. |
| **Points de terminaison**  | **Notifications par courrier électronique** | Configurer ou modifier vos règles de notification par courrier électronique. Lorsque des vulnérabilités sont détectées ou qu’une alerte est créée, les destinataires spécifiés dans vos règles de notification par courrier électronique reçoivent un e-mail. [En savoir plus sur les notifications par courrier électronique](mdb-email-notifications.md). |
| **Points de terminaison**   | **Gestion des appareils** >  **Intégration** | Intégrer des appareils à Defender for Business à l’aide d’un script téléchargeable. Pour en savoir plus, [consultez Intégrer des appareils à Microsoft Defender pour Entreprises](mdb-onboard-devices.md).   |  
| **Points de terminaison**  |  **Gestion des appareils** >  **Offboarding** | Déboardez (supprimez) les appareils de Defender for Business. Lorsque vousboardez un appareil, il n’envoie plus de données à Defender for Business, mais les données reçues avant laboarding sont conservées. Pour en savoir plus, consultez [Laboarding d’un appareil](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Accéder à vos paramètres dans le portail Microsoft 365 Defender web

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com/](https://security.microsoft.com/)), and sign in.

2. **Sélectionnez Paramètres**, puis sélectionnez une catégorie (par **exemple, centre** de sécurité, **Microsoft 365 Defender** ou points **de terminaison**).

3. Dans la liste des paramètres, sélectionnez un élément à afficher ou à modifier.


## <a name="next-steps"></a>Étapes suivantes

Procédez à une ou plusieurs des tâches suivantes :

- [Commencer à utiliser Microsoft Defender pour les entreprises](mdb-get-started.md)

- [Gérer les appareils dans Microsoft Defender pour les entreprises](mdb-manage-devices.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise](mdb-view-manage-incidents.md)

- [Afficher ou modifier des stratégies dans Microsoft Defender entreprise](mdb-view-edit-policies.md)
