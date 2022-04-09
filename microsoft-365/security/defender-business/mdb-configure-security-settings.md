---
title: Afficher et modifier vos paramètres de sécurité dans Microsoft Defender pour les PME
description: Configurer vos stratégies de sécurité dans Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/15/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 3d6ef3a7bc3ae9b7556041cedc88df354421f885
ms.sourcegitcommit: dd5fc139affb4cba4089cbdb2c478968b680699a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2022
ms.locfileid: "64746489"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Afficher et modifier vos stratégies et paramètres de sécurité dans Microsoft Defender pour les PME

> [!IMPORTANT]
> Microsoft Defender pour les PME est déployée pour [Microsoft 365 Business Premium](../../business-premium/index.md) clients, à compter du 1er mars 2022. Defender entreprise en tant qu’abonnement autonome est en préversion et sera déployé progressivement pour les clients et les partenaires informatiques qui [s’inscrivent ici](https://aka.ms/mdb-preview) pour le demander. La préversion inclut un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios), et nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations contenues dans cet article concernent des produits/services prédéfinis qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expresse ou implicite, pour les informations fournies ici. 

## <a name="overview"></a>Vue d’ensemble

Une fois que vous avez intégré les appareils de votre entreprise à Microsoft Defender pour les PME, l’étape suivante consiste à afficher et, si nécessaire, à modifier vos stratégies et paramètres de sécurité. Les stratégies de sécurité à configurer sont les suivantes :

- **[Stratégies de protection de nouvelle génération](#view-or-edit-your-next-generation-protection-policies)**, qui déterminent la protection antivirus et anti-programme malveillant pour les appareils de votre entreprise
- **[Protection et règles de pare-feu](#view-or-edit-your-firewall-policies-and-custom-rules)**, qui déterminent le trafic réseau autorisé à circuler vers ou depuis les appareils de votre entreprise
- **[Filtrage du contenu web](#set-up-web-content-filtering)**, qui empêche les utilisateurs de visiter certains sites web (URL) en fonction de catégories, telles que le contenu pour adultes ou la responsabilité légale.

Dans Defender entreprise, les stratégies de sécurité sont appliquées aux appareils par le biais [de groupes d’appareils](mdb-create-edit-device-groups.md#what-is-a-device-group). 

En plus de vos stratégies de sécurité, vous pouvez [afficher et modifier les paramètres](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), tels que le fuseau horaire à utiliser dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et s’il faut recevoir des fonctionnalités en préversion à mesure qu’elles deviennent disponibles.

Utilisez cet article comme guide pour gérer vos stratégies et paramètres de sécurité.

## <a name="what-to-do"></a>Procédure

1. [Choisissez où gérer vos stratégies et appareils de sécurité](#choose-where-to-manage-security-policies-and-devices).

2. [Affichez ou modifiez vos stratégies de protection de nouvelle génération](#view-or-edit-your-next-generation-protection-policies).

3. [Affichez ou modifiez vos stratégies de pare-feu et vos règles personnalisées](#view-or-edit-your-firewall-policies-and-custom-rules).

4. [Configurez le filtrage de contenu web](#set-up-web-content-filtering).

5. [Affichez et modifiez d’autres paramètres dans le portail Microsoft 365 Defender](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 

6. [Passez à vos étapes suivantes](#next-steps).

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">court sondage sur Microsoft Defender pour les PME</a>. Vos commentaires sont les bienvenus.
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Choisir l’emplacement de gestion des stratégies de sécurité et des appareils

Defender pour Entreprise propose un [processus de configuration simplifié](mdb-simplified-configuration.md) qui permet de simplifier le processus d’installation et de configuration. Si vous sélectionnez le processus de configuration simplifié, vous pouvez afficher et gérer vos stratégies de sécurité dans le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Toutefois, vous n’êtes pas limité à cette option. Si vous avez utilisé Microsoft Endpoint Manager (ce qui inclut Microsoft Intune), vous pouvez continuer à utiliser votre Endpoint Manager.

Le tableau suivant peut vous aider à choisir où gérer vos stratégies et appareils de sécurité. <br/><br/>

| Option | Description |
|:---|:---|
| **Utiliser le portail Microsoft 365 Defender** (*recommandé*) | Le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) peut être votre guichet unique pour gérer les appareils, les stratégies de sécurité et les paramètres de sécurité de votre entreprise. Vous pouvez accéder à vos stratégies et paramètres de sécurité, utiliser votre [tableau de bord Threat & Vulnerability Management](mdb-view-tvm-dashboard.md) et [afficher et gérer les incidents](mdb-view-manage-incidents.md) au même endroit. <br/><br/>Si vous utilisez Microsoft Endpoint Manager, les appareils que vous intègrez à Defender Entreprise et vos stratégies de sécurité sont visibles dans Endpoint Manager. Pour en savoir plus, consultez les articles suivants :<br/><br/>- [Paramètres et Microsoft Endpoint Manager par défaut de Defender entreprise](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-endpoint-manager)<br/><br/>- [Pare-feu dans Microsoft Defender pour les PME](mdb-firewall.md)   |
| **Utiliser Microsoft Endpoint Manager** | Si votre entreprise utilise déjà Endpoint Manager (ce qui inclut Microsoft Intune) pour gérer les stratégies de sécurité, vous pouvez continuer à utiliser Endpoint Manager pour gérer les appareils et les stratégies de sécurité. Pour en savoir plus, consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Si vous décidez de basculer vers le [processus de configuration simplifié dans Defender entreprise](mdb-simplified-configuration.md), vous serez invité à supprimer les stratégies de sécurité existantes dans Endpoint Manager pour éviter [les conflits](mdb-troubleshooting.yml) de stratégie ultérieurement. |

> [!IMPORTANT]
> Si vous gérez des stratégies de sécurité dans le portail Microsoft 365 Defender, vous pouvez *afficher* ces stratégies dans Endpoint Manager, répertoriées en tant que stratégies antivirus ou pare-feu. Lorsque vous affichez vos stratégies de pare-feu dans Endpoint Manager, deux stratégies sont répertoriées : une pour la protection de votre pare-feu et une autre pour les règles personnalisées.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Afficher ou modifier vos stratégies de protection de nouvelle génération

Selon que vous utilisez le portail Microsoft 365 Defender ou Microsoft Endpoint Manager pour gérer vos stratégies de protection de nouvelle génération, utilisez l’une des procédures du tableau suivant : <br/><br/>

| Portail | Procedure |
|:---|:---|
| portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par exemple **, Windows clients**).<br/><br/>4. Développez la **protection nouvelle génération** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Comprendre les paramètres de configuration de nouvelle génération](mdb-next-gen-configuration-settings.md)  |
| centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Accédez à [https://endpoint.microsoft.com](https://endpoint.microsoft.com) et connectez-vous. Vous êtes maintenant dans le centre d’administration Microsoft Endpoint Manager.<br/><br/>2. Sélectionnez **Sécurité du point de terminaison**.<br/><br/>3. Sélectionnez **Antivirus** pour afficher vos stratégies dans cette catégorie. <br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Microsoft Endpoint Manager, [commencez par Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Afficher ou modifier vos stratégies de pare-feu et vos règles personnalisées

Selon que vous utilisez le portail Microsoft 365 Defender ou Microsoft Endpoint Manager pour gérer la protection de votre pare-feu, utilisez l’une des procédures du tableau suivant : <br/><br/>

| Portail | Procedure |
|:---|:---|
| portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par exemple **, Windows clients**).<br/><br/>4. Développez **le pare-feu** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Paramètres de pare-feu](mdb-firewall.md)<br/>- [Gérer vos règles personnalisées pour les stratégies de pare-feu](mdb-custom-rules-firewall.md)  |
| centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Accédez à [https://endpoint.microsoft.com](https://endpoint.microsoft.com) et connectez-vous. Vous êtes maintenant dans le centre d’administration Microsoft Endpoint Manager.<br/><br/>2. Sélectionnez **Sécurité du point de terminaison**.<br/><br/>3. Sélectionnez **Pare-feu** pour afficher vos stratégies dans cette catégorie. Les règles personnalisées définies pour la protection pare-feu sont répertoriées en tant que stratégies distinctes.<br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Microsoft Endpoint Manager, [commencez par Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="set-up-web-content-filtering"></a>Configurer le filtrage de contenu web

Le filtrage de contenu web permet à votre équipe de sécurité de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu, par exemple :

- Contenu pour adultes : sites liés aux cultes, au jeu, à la nudité, à la pornographie, au matériel sexuellement explicite ou à la violence

- Bande passante élevée : télécharger des sites, des sites de partage d’images ou des hôtes pair à pair

- Responsabilité légale : sites qui incluent des images d’abus d’enfants, favorisent des activités illégales, favorisent le plagiat ou la tricherie scolaire, ou qui favorisent des activités dangereuses

- Loisirs : sites qui fournissent des salles de conversation web, des jeux en ligne, des e-mails web ou des réseaux sociaux

- Non catégorisé : sites qui n’ont pas de contenu ou qui viennent d’être inscrits

Tous les sites web de ces catégories ne sont pas malveillants, mais ils peuvent être problématiques pour votre entreprise en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes. En outre, vous pouvez créer une stratégie d’audit uniquement pour mieux comprendre si votre équipe de sécurité doit bloquer les catégories de sites web.

Le filtrage de contenu web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et Network Protection (Chrome, Firefox, Brave et Opera). Pour plus d’informations, consultez [Prérequis pour le filtrage de contenu web](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Pour configurer le filtrage de contenu web

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Paramètres** >  **Web content filtering** > **+ Add policy**.

2. Spécifiez un nom et une description pour votre stratégie.

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer complètement chaque catégorie parente et sélectionner des catégories de contenu web spécifiques.

   Pour configurer une stratégie d’audit uniquement qui ne bloque aucun site web, ne sélectionnez aucune catégorie.

   Ne sélectionnez pas **Non catégorisé**.

4. Spécifiez l’étendue de la stratégie en sélectionnant des groupes d’appareils pour appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne peuvent pas accéder aux sites web dans les catégories sélectionnées.

5. Passez en revue le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à 2 heures pour s’appliquer à vos appareils sélectionnés.

> [!TIP]
> Pour en savoir plus sur le filtrage de contenu web, consultez filtrage [de contenu web](../defender-endpoint/web-content-filtering.md).

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Afficher et modifier d’autres paramètres dans le portail Microsoft 365 Defender

Outre les stratégies de sécurité appliquées aux appareils, vous pouvez afficher et modifier d’autres paramètres dans Defender entreprise. Par exemple, vous spécifiez le fuseau horaire à utiliser et vous pouvez intégrer (ou déconnecter) des appareils. 

> [!NOTE]
> Vous pouvez voir plus de paramètres dans votre locataire que ce qui est répertorié dans cet article. Cet article met en évidence les paramètres les plus importants que vous devez examiner dans Defender entreprise.

### <a name="settings-to-review-for-defender-for-business"></a>Paramètres à examiner pour Defender Entreprise

Le tableau suivant décrit les paramètres à afficher (et si nécessaire, modifier) dans Defender entreprise.

<br/><br/>

| Catégorie | Paramètre | Description |
|:---|:---|:---|
| **Centre de sécurité** | **Fuseau horaire** | Sélectionnez le fuseau horaire à utiliser pour les dates et heures affichées dans les incidents, les menaces détectées et l’examen automatisé & correction. Vous pouvez utiliser UTC ou votre fuseau horaire local (*recommandé*).  |
| **Microsoft 365 Defender** | **Account** | Affichez les détails, tels que l’emplacement où vos données sont stockées, votre ID de locataire et votre ID d’organisation (organisation). |
| **Microsoft 365 Defender**  | **Fonctionnalités en préversion**  | Activez les fonctionnalités en préversion pour essayer les fonctionnalités à venir et les nouvelles fonctionnalités. Vous pouvez être parmi les premiers à afficher un aperçu des nouvelles fonctionnalités et à fournir des commentaires. |
| **Points de terminaison**  | **Notifications par e-mail** | Configurez ou modifiez vos règles de notification par e-mail. Lorsque des vulnérabilités sont détectées ou qu’une alerte est créée, les destinataires spécifiés dans vos règles de notification par e-mail reçoivent un e-mail. [En savoir plus sur les notifications par e-mail](mdb-email-notifications.md). |
| **Points de terminaison**   | **Gestion des** >  appareils **Intégration** | Intégrer des appareils à Defender entreprise à l’aide d’un script téléchargeable. Pour en savoir plus, consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).   |  
| **Points de terminaison**  |  **Gestion des** >  appareils **Désintégrage** | Désintégrez (supprimez) les appareils de Defender pour Entreprises. Lorsque vous déconnectez un appareil, il n’envoie plus de données à Defender entreprise, mais les données reçues avant la désintégrage sont conservées. Pour plus d’informations, consultez [Désintégrage d’un appareil](mdb-onboard-devices.md#offboarding-a-device).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Accéder à vos paramètres dans le portail Microsoft 365 Defender

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) et connectez-vous.

2. Sélectionnez **Paramètres**, puis sélectionnez une catégorie (par exemple, **Centre de sécurité**, **Microsoft 365 Defender** ou **points de terminaison**).

3. Dans la liste des paramètres, sélectionnez un élément à afficher ou à modifier.


## <a name="next-steps"></a>Prochaines étapes

Passez à une ou plusieurs des tâches suivantes :

- [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md)
- [Gérer les appareils dans Microsoft Defender pour les PME](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](mdb-view-edit-policies.md)
