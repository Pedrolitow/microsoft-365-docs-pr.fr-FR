---
title: Afficher et modifier vos paramètres de sécurité dans Microsoft Defender pour les PME
description: Afficher et modifier les stratégies et paramètres de sécurité dans Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 9d401c5be4fc0454ce1d895fe5ea49267e5c5f70
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469170"
---
# <a name="view-and-edit-your-security-policies-and-settings-in-microsoft-defender-for-business"></a>Afficher et modifier vos stratégies et paramètres de sécurité dans Microsoft Defender pour les PME

Une fois que vous avez intégré les appareils de votre entreprise à Microsoft Defender pour les PME, l’étape suivante consiste à passer en revue vos stratégies de sécurité. Si nécessaire, vous pouvez modifier vos stratégies et paramètres de sécurité. 

> [!TIP]
> Defender entreprise inclut des stratégies de sécurité préconfigurées qui utilisent les paramètres recommandés. Toutefois, vous pouvez modifier vos paramètres en fonction des besoins de votre entreprise.

Les stratégies de sécurité à examiner et à configurer sont les suivantes :

- **[Stratégies de protection de nouvelle génération](#view-or-edit-your-next-generation-protection-policies)**, qui déterminent la protection antivirus et anti-programme malveillant pour les appareils de votre entreprise
- **[Protection et règles de pare-feu](#view-or-edit-your-firewall-policies-and-custom-rules)**, qui déterminent le trafic réseau autorisé à circuler vers ou depuis les appareils de votre entreprise
- **[Filtrage du contenu web](#set-up-web-content-filtering)**, qui empêche les utilisateurs de visiter certains sites web (URL) en fonction de catégories, telles que le contenu pour adultes ou la responsabilité légale.
- **[Fonctionnalités avancées](#review-settings-for-advanced-features)**, telles que l’investigation et la réponse automatisées, et protection évolutive des points de terminaison (PEPT) en mode bloc.

Dans Defender entreprise, les stratégies de sécurité sont appliquées aux appareils par le biais [de groupes d’appareils](mdb-create-edit-device-groups.md#what-is-a-device-group). 

En plus de vos stratégies de sécurité, vous pouvez [afficher et modifier les paramètres](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), tels que le fuseau horaire à utiliser dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et s’il faut recevoir des fonctionnalités en préversion à mesure qu’elles deviennent disponibles.

Utilisez cet article comme guide pour gérer vos stratégies et paramètres de sécurité.

## <a name="what-to-do"></a>Procédure

1. [Choisissez où gérer vos stratégies et appareils de sécurité](#choose-where-to-manage-security-policies-and-devices).
2. [Passez en revue vos stratégies de protection de nouvelle génération](#view-or-edit-your-next-generation-protection-policies).
3. [Passez en revue vos stratégies de pare-feu et vos règles personnalisées](#view-or-edit-your-firewall-policies-and-custom-rules).
4. [Configurez le filtrage de contenu web](#set-up-web-content-filtering).
5. [Passez en revue les paramètres des fonctionnalités avancées](#review-settings-for-advanced-features).
6. [Affichez d’autres paramètres dans le portail Microsoft 365 Defender](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 
7. [Passez à vos étapes suivantes](#next-steps).

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="choose-where-to-manage-security-policies-and-devices"></a>Choisir l’emplacement de gestion des stratégies de sécurité et des appareils

Defender pour Entreprise propose un [processus de configuration simplifié](mdb-simplified-configuration.md) qui permet de simplifier le processus d’installation et de configuration. Si vous sélectionnez le processus de configuration simplifié, vous pouvez afficher et gérer vos stratégies de sécurité dans le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Toutefois, vous n’êtes pas limité à cette option. Si vous avez utilisé Microsoft Intune, vous pouvez continuer à utiliser le centre d’administration Microsoft Endpoint Manager.

Le tableau suivant peut vous aider à choisir où gérer vos stratégies et appareils de sécurité. <br/><br/>

| Option | Description |
|:---|:---|
| **Utiliser le portail Microsoft 365 Defender** (*recommandé*) | Le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) peut être votre guichet unique pour gérer les appareils, les stratégies de sécurité et les paramètres de sécurité de votre entreprise. Vous pouvez accéder à vos stratégies et paramètres de sécurité, utiliser votre [tableau de bord Threat & Vulnerability Management](mdb-view-tvm-dashboard.md) et [afficher et gérer les incidents](mdb-view-manage-incidents.md) au même endroit. <br/><br/>Si vous utilisez Intune, les appareils que vous intègrez à Defender Entreprise et vos stratégies de sécurité sont visibles dans le centre d’administration Endpoint Manager. Pour en savoir plus, consultez les articles suivants :<br/>- [Paramètres et Microsoft Intune par défaut de Defender entreprise](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-intune) <br/>- [Pare-feu dans Microsoft Defender pour les PME](mdb-firewall.md)   |
| **Utiliser le centre d’administration Microsoft Endpoint Manager** | Si votre entreprise utilise déjà Intune pour gérer les stratégies de sécurité, vous pouvez continuer à utiliser le centre d’administration Endpoint Manager pour gérer vos appareils et stratégies de sécurité. Pour en savoir plus, consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <br/><br/>Si vous décidez de basculer vers le [processus de configuration simplifié dans Defender entreprise](mdb-simplified-configuration.md), vous serez invité à supprimer les stratégies de sécurité existantes dans Intune pour éviter [les conflits](mdb-troubleshooting.yml) de stratégie ultérieurement. |

> [!IMPORTANT]
> Si vous gérez des stratégies de sécurité dans le portail Microsoft 365 Defender, vous pouvez *afficher* ces stratégies dans le centre d’administration Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), répertoriés en tant que stratégies **antivirus** ou **pare-feu**. Lorsque vous affichez vos stratégies de pare-feu dans le centre d’administration Endpoint Manager, deux stratégies sont répertoriées : une stratégie pour la protection de votre pare-feu et une autre pour les règles personnalisées.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Afficher ou modifier vos stratégies de protection de nouvelle génération

Selon que vous utilisez le portail Microsoft 365 Defender ou le centre d’administration Microsoft Endpoint Manager pour gérer vos stratégies de protection de nouvelle génération, utilisez l’une des procédures du tableau suivant :

| Portail | Procedure |
|:---|:---|
| portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par exemple **, Windows clients**).<br/><br/>4. Développez la **protection nouvelle génération** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Comprendre les paramètres de configuration de nouvelle génération](mdb-next-gen-configuration-settings.md)  |
| centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Accédez à [https://endpoint.microsoft.com](https://endpoint.microsoft.com) et connectez-vous. Vous êtes maintenant dans le centre d’administration Endpoint Manager.<br/><br/>2. Sélectionnez **Sécurité du point de terminaison**.<br/><br/>3. Sélectionnez **Antivirus** pour afficher vos stratégies dans cette catégorie. <br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Intune, [commencez par Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Afficher ou modifier vos stratégies de pare-feu et vos règles personnalisées

Selon que vous utilisez le portail Microsoft 365 Defender ou le centre d’administration Microsoft Endpoint Manager pour gérer la protection de votre pare-feu, utilisez l’une des procédures du tableau suivant :

| Portail | Procedure |
|:---|:---|
| portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) | 1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous. <br/><br/>2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.<br/><br/>3. Sélectionnez un onglet de système d’exploitation (par exemple **, Windows clients**).<br/><br/>4. Développez **le pare-feu** pour afficher votre liste de stratégies.<br/><br/>5. Sélectionnez une stratégie pour afficher plus de détails sur la stratégie. Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <br/>- [Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)<br/>- [Paramètres de pare-feu](mdb-firewall.md)<br/>- [Gérer vos règles personnalisées pour les stratégies de pare-feu](mdb-custom-rules-firewall.md)  |
| centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) | 1. Accédez à [https://endpoint.microsoft.com](https://endpoint.microsoft.com) et connectez-vous. Vous êtes maintenant dans le centre d’administration Endpoint Manager.<br/><br/>2. Sélectionnez **Sécurité du point de terminaison**.<br/><br/>3. Sélectionnez **Pare-feu** pour afficher vos stratégies dans cette catégorie. Les règles personnalisées définies pour la protection pare-feu sont répertoriées en tant que stratégies distinctes.<br/><br/>Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Intune, [commencez par Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). |

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

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer complètement chaque catégorie parente et sélectionner des catégories de contenu web spécifiques. Pour configurer une stratégie d’audit uniquement qui ne bloque aucun site web, ne sélectionnez aucune catégorie.

   Ne sélectionnez pas **Non catégorisé**.

4. Spécifiez l’étendue de la stratégie en sélectionnant des groupes d’appareils pour appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne peuvent pas accéder aux sites web dans les catégories sélectionnées.

5. Passez en revue le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à 2 heures pour s’appliquer à vos appareils sélectionnés.

> [!TIP]
> Pour en savoir plus sur le filtrage de contenu web, consultez filtrage [de contenu web](../defender-endpoint/web-content-filtering.md).

## <a name="review-settings-for-advanced-features"></a>Passer en revue les paramètres des fonctionnalités avancées

Outre les stratégies de protection, de pare-feu et de filtrage de contenu web de nouvelle génération, Defender entreprise inclut des fonctionnalités de sécurité avancées. Ces fonctionnalités sont préconfigurées à l’aide des paramètres recommandés ; toutefois, vous pouvez les examiner et, si nécessaire, modifier les paramètres en fonction des besoins de votre entreprise.

Pour accéder aux paramètres des fonctionnalités avancées, dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), accédez à **Paramètres** >  **FonctionnalitésEndpointsGeneralAdvanced** >  > .

Le tableau suivant décrit les paramètres des fonctionnalités avancées :

| Paramètre | Description |
|:---|:---|
| **Examen automatisé** <br/>(activé par défaut) | À mesure que des alertes sont générées, des investigations automatisées peuvent se produire. Chaque investigation automatisée détermine si une menace détectée nécessite une action, puis prend (ou recommande) des actions de correction (comme l’envoi d’un fichier en quarantaine, l’arrêt d’un processus, l’isolation d’un appareil ou le blocage d’une URL). Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité affectée est vue ailleurs, l’enquête automatisée étend son étendue pour inclure cette entité, et le processus d’examen se répète.<br/><br/>Vous pouvez afficher les enquêtes sur la page **Incidents** . Sélectionnez un incident, puis sélectionnez l’onglet **Investigations** .<br/><br/>Par défaut, les fonctionnalités d’investigation et de réponse automatisées sont activées à l’échelle du locataire. **Nous vous recommandons de maintenir l’investigation automatisée activée**. Si vous la désactivez, la protection en temps réel dans Antivirus Microsoft Defender sera affectée et votre niveau de protection global sera réduit. <br/><br/>[En savoir plus sur les enquêtes automatisées](../defender-endpoint/automated-investigations.md).   |
| **Réponse en direct**  | Defender entreprise inclut les types d’actions de réponse manuelle suivants : <br/>- Exécuter une analyse antivirus<br/>- Isoler l’appareil<br/>- Arrêter et mettre en quarantaine un fichier<br/>- Ajoutez des indicateurs pour bloquer ou autoriser un fichier. <br/><br/>[En savoir plus sur les actions de réponse](../defender-endpoint/respond-machine-alerts.md). |
| **Réponse en direct pour les serveurs** | (Ce paramètre n’est actuellement pas disponible dans Defender entreprise)   |
| **Exécution de scripts non signés live Response** | (Ce paramètre n’est actuellement pas disponible dans Defender entreprise)  | 
| **Activer PEPT en mode bloc**<br/>(activé par défaut) | Fournit une protection supplémentaire contre les artefacts malveillants lorsque Antivirus Microsoft Defender n’est pas le produit antivirus principal et s’exécute en mode passif sur un appareil. La détection et la réponse des points de terminaison (PEPT) en mode bloc fonctionnent en arrière-plan pour corriger les artefacts malveillants détectés par PEPT fonctionnalités. De tels artefacts peuvent avoir été manqués par le produit antivirus principal non-Microsoft.<br/><br/>[En savoir plus sur PEPT en mode bloc](../defender-endpoint/edr-in-block-mode.md). |
| **Autoriser ou bloquer un fichier** <br/>(activé par défaut) | Vous permet d’autoriser ou de bloquer un fichier à l’aide [d’indicateurs](../defender-endpoint/indicator-file.md). Cette fonctionnalité nécessite Antivirus Microsoft Defender être en mode actif et la [protection cloud](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md) doit être activée.<br/><br/>Le blocage d’un fichier empêche sa lecture, son écriture ou son exécution sur les appareils de votre organisation. <br/><br/>[En savoir plus sur les indicateurs pour les fichiers](../defender-endpoint/indicator-file.md).  |
| **Indicateurs réseau personnalisés**<br/>(activé par défaut) | Vous permet d’autoriser ou de bloquer une adresse IP, une URL ou un domaine à l’aide [d’indicateurs réseau](../defender-endpoint/indicator-ip-domain.md). Cette fonctionnalité nécessite Antivirus Microsoft Defender être en mode actif et la [protection réseau](../defender-endpoint/enable-network-protection.md) doit être activée.<br/><br/>Vous pouvez autoriser ou bloquer des adresses IP, des URL ou des domaines en fonction de votre propre renseignement sur les menaces. Vous pouvez également avertir les utilisateurs avec une invite s’ils ouvrent une application à risque. L’invite ne les empêchera pas d’utiliser l’application, mais vous pouvez fournir un avertissement aux utilisateurs.<br/><br/>[En savoir plus sur la protection réseau](../defender-endpoint/network-protection.md). |
| **Protection contre les falsifications**<br/>(nous vous recommandons d’activer ce paramètre) | La protection contre les falsifications empêche les applications malveillantes d’effectuer des actions telles que :<br/>- Désactivation de la protection contre les virus et les menaces<br/>- Désactivation de la protection en temps réel<br/>- Désactivation de la surveillance du comportement<br/>- Désactivation de la protection cloud<br/>- Suppression des mises à jour du renseignement de sécurité<br/>- Désactivation des actions automatiques sur les menaces détectées<br/><br/>La protection contre les falsifications verrouille essentiellement Antivirus Microsoft Defender à ses valeurs sécurisées par défaut et empêche la modification de vos paramètres de sécurité par les applications et les méthodes non autorisées. <br/><br/>[En savoir plus sur la protection contre les falsifications](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md).  |
| **Afficher les détails de l’utilisateur**<br/>(activé par défaut) | Permet aux membres de votre organisation de voir des détails, tels que l’image, le nom, le titre et le service des employés. Ces détails sont stockés dans Azure Active Directory (Azure AD).<br/><br/>[En savoir plus sur les profils utilisateur dans Azure AD](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).  |
| **intégration Skype Entreprise**<br/>(activé par défaut) | Skype Entreprise a pris sa retraite en juillet 2021. Si vous n’avez pas encore déménagé à Microsoft Teams, consultez [Configurer Microsoft Teams dans votre petite entreprise](/microsoftteams/deploy-small-business). <br/><br/>L’intégration à Microsoft Teams (ou à l’ancien Skype Entreprise) permet une communication en un clic entre les personnes de votre entreprise.   |
| **Filtrage du contenu web**<br/>(activé par défaut) | Bloquez l’accès aux sites web contenant du contenu indésirable et suivez l’activité web dans tous les domaines. Consultez [Configurer le filtrage de contenu web](#set-up-web-content-filtering). |
| **connexion Microsoft Intune**<br/>(Nous vous recommandons d’activer ce paramètre si vous avez Intune) | Si l’abonnement de votre organisation inclut des Microsoft Intune (inclus dans [Microsoft 365 Business Premium](../../business/index.yml)), ce paramètre permet à Defender Entreprise de partager des informations sur les appareils avec Intune.  |
| **Découverte d’appareils**<br/>(activé par défaut) | Permet à votre équipe de sécurité de rechercher des appareils non gérés qui sont connectés à votre réseau d’entreprise. Les appareils inconnus et non gérés présentent des risques significatifs pour votre réseau, qu’il s’agisse d’une imprimante non modifiée, d’appareils réseau avec des configurations de sécurité faibles ou d’un serveur sans contrôle de sécurité. <br/><br/>La découverte d’appareils utilise des appareils intégrés pour détecter les appareils non gérés, afin que votre équipe de sécurité puisse intégrer les appareils non gérés et réduire votre vulnérabilité. <br/><br/>[En savoir plus sur la découverte d’appareils](../defender-endpoint/device-discovery.md).    |
| **Fonctionnalités en préversion** | Microsoft met continuellement à jour des services, tels que Defender Entreprise, pour inclure de nouvelles fonctionnalités et améliorations. Si vous choisissez de recevoir des fonctionnalités en préversion, vous serez parmi les premiers à essayer les fonctionnalités à venir dans l’expérience de préversion. <br/><br/>[En savoir plus sur les fonctionnalités en préversion](../defender-endpoint/preview.md).  |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Afficher et modifier d’autres paramètres dans le portail Microsoft 365 Defender

Outre les stratégies de sécurité appliquées aux appareils, vous pouvez afficher et modifier d’autres paramètres dans Defender entreprise. Par exemple, vous spécifiez le fuseau horaire à utiliser et vous pouvez intégrer (ou déconnecter) des appareils. 

> [!NOTE]
> Vous pouvez voir plus de paramètres dans votre locataire que ce qui est répertorié dans cet article. Cet article met en évidence les paramètres les plus importants que vous devez examiner dans Defender entreprise.

### <a name="settings-to-review-for-defender-for-business"></a>Paramètres à examiner pour Defender Entreprise

Le tableau suivant décrit les paramètres à afficher (et si nécessaire, modifier) dans Defender entreprise :

| Catégorie | Paramètre | Description |
|:---|:---|:---|
| **Centre de sécurité** | **Fuseau horaire** | Sélectionnez le fuseau horaire à utiliser pour les dates et heures affichées dans les incidents, les menaces détectées et l’examen automatisé & correction. Vous pouvez utiliser UTC ou votre fuseau horaire local (*recommandé*).  |
| **Microsoft 365 Defender** | **Account** | Affichez les détails, tels que l’emplacement où vos données sont stockées, votre ID de locataire et votre ID d’organisation (organisation). |
| **Microsoft 365 Defender**  | **Fonctionnalités en préversion**  | Activez les fonctionnalités en préversion pour essayer les fonctionnalités à venir et les nouvelles fonctionnalités. Vous pouvez être parmi les premiers à afficher un aperçu des nouvelles fonctionnalités et à fournir des commentaires. |
| **Points de terminaison**  | **Notifications par e-mail** | Configurez ou modifiez vos règles de notification par e-mail. Lorsque des vulnérabilités sont détectées ou qu’une alerte est créée, les destinataires spécifiés dans vos règles de notification par e-mail reçoivent un e-mail. [En savoir plus sur les notifications par e-mail](mdb-email-notifications.md). |
| **Points de terminaison**   | **Gestion des** >  appareils **Intégration** | Intégrer des appareils à Defender entreprise à l’aide d’un script téléchargeable. Pour en savoir plus, consultez [Intégrer des appareils à Microsoft Defender pour les PME](mdb-onboard-devices.md).   |  
| **Points de terminaison**  |  **Gestion des** >  appareils **Désintégrage** | Désintégrez (supprimez) les appareils de Defender pour Entreprises. Lorsque vous déconnectez un appareil, il n’envoie plus de données à Defender entreprise, mais les données reçues avant la désintégrage sont conservées. Pour plus d’informations, consultez [Désintégrage d’un appareil](mdb-offboard-devices.md).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Accéder à vos paramètres dans le portail Microsoft 365 Defender

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)), puis connectez-vous.

2. Sélectionnez **Paramètres**, puis sélectionnez une catégorie (par exemple, **Centre de sécurité**, **Microsoft 365 Defender** ou **points de terminaison**).

3. Dans la liste des paramètres, sélectionnez un élément à afficher ou à modifier.

## <a name="next-steps"></a>Prochaines étapes

Passez à une ou plusieurs des tâches suivantes :

- [Démarrage à l’aide de Microsoft Defender pour les PME](mdb-get-started.md)
- [Gérer les appareils dans Microsoft Defender pour les PME](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Afficher ou modifier des stratégies dans Microsoft Defender pour les PME](mdb-view-edit-policies.md)
