---
title: Afficher et modifier vos paramètres de sécurité dans Microsoft Defender pour entreprises
description: Afficher et modifier les stratégies et paramètres de sécurité dans Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365solution-mdb-setup
- highpri
ms.openlocfilehash: 189cfb05ad41e967ac61c1ca73c5f8feeab1f411
ms.sourcegitcommit: 511d15831b97d02e5a0f5e11834ad52617abd0f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67600288"
---
# <a name="view-and-edit-security-policies-and-settings-in-microsoft-defender-for-business"></a>Afficher et modifier les stratégies et paramètres de sécurité dans Microsoft Defender pour entreprises

Une fois que vous avez intégré les appareils de votre entreprise à Defender entreprise, l’étape suivante consiste à passer en revue vos stratégies de sécurité. 

> [!TIP]
> Defender entreprise inclut des stratégies de sécurité préconfigurées avec les paramètres recommandés. Vous pouvez modifier ces paramètres en fonction des besoins de votre entreprise.

Les stratégies de sécurité à examiner et à configurer sont les suivantes :

- **[Stratégies de protection de nouvelle génération](#view-or-edit-your-next-generation-protection-policies)**, qui déterminent la protection antivirus et anti-programme malveillant pour les appareils de votre entreprise
- **[Protection et règles de pare-feu](#view-or-edit-your-firewall-policies-and-custom-rules)**, qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils de votre entreprise
- **[Filtrage du contenu web](#set-up-web-content-filtering)**, qui empêche les utilisateurs de visiter certains sites web (URL) en fonction de catégories, telles que le contenu pour adultes ou la responsabilité légale
- **[Fonctionnalités avancées](#review-settings-for-advanced-features)**, telles que l’investigation automatisée et la réponse et la détection et la réponse de point de terminaison (EDR) en mode bloc

Dans Defender entreprise, les stratégies de sécurité sont appliquées aux appareils par le biais [de groupes d’appareils](mdb-create-edit-device-groups.md#what-is-a-device-group). 

En plus de vos stratégies de sécurité, vous pouvez [afficher et modifier les paramètres](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal), tels que le fuseau horaire à utiliser dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et s’il faut recevoir des fonctionnalités en préversion à mesure qu’elles deviennent disponibles.

Utilisez cet article comme guide pour gérer vos stratégies et paramètres de sécurité.

## <a name="what-to-do"></a>Procédure

1. [Choisissez où gérer vos stratégies et appareils de sécurité](#choose-where-to-manage-security-policies-and-devices).
2. [Passez en revue vos stratégies de protection de nouvelle génération](#view-or-edit-your-next-generation-protection-policies).
3. [Passez en revue vos stratégies de pare-feu et vos règles personnalisées](#view-or-edit-your-firewall-policies-and-custom-rules).
4. [Configurer le filtrage du contenu Web](#set-up-web-content-filtering).
5. [Examiner les paramètres des fonctions avancées](#review-settings-for-advanced-features).
6. [Affichez d’autres paramètres dans le portail Microsoft 365 Defender](#view-and-edit-other-settings-in-the-microsoft-365-defender-portal). 
7. [Passez à vos étapes suivantes](#next-steps).


## <a name="choose-where-to-manage-security-policies-and-devices"></a>Choisir l’emplacement de gestion des stratégies de sécurité et des appareils

Defender pour Entreprise propose un [processus de configuration simplifié](mdb-simplified-configuration.md) qui permet de simplifier le processus d’installation et de configuration. Si vous sélectionnez le processus de configuration simplifié, vous pouvez afficher et gérer vos stratégies de sécurité dans le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)). Toutefois, vous n’êtes pas limité à cette option. Si vous avez utilisé Microsoft Intune, vous pouvez continuer à utiliser le Centre d’administration Microsoft Endpoint Manager.

Le tableau suivant peut vous aider à choisir où gérer vos stratégies et appareils de sécurité.

| Option | Description |
|:---|:---|
| **Utiliser le portail Microsoft 365 Defender** (*recommandé*) | Le portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)) est un guichet unique pour la gestion des appareils, des stratégies de sécurité et des paramètres de sécurité de votre entreprise. Vous pouvez accéder à vos stratégies et paramètres de sécurité, utiliser le [tableau de bord Gestion des vulnérabilités Microsoft Defender](mdb-view-tvm-dashboard.md) et [afficher et gérer les incidents](mdb-view-manage-incidents.md) au même endroit. <p>Si vous utilisez Intune, les appareils que vous intègrez à Defender Entreprise et vos stratégies de sécurité sont visibles dans le centre d’administration Endpoint Manager. Pour en savoir plus, consultez les articles suivants :<ul><li>[Paramètres et Microsoft Intune par défaut de Defender entreprise](mdb-next-gen-configuration-settings.md#defender-for-business-default-settings-and-microsoft-intune)</li><li>[Pare-feu dans Defender pour Entreprises](mdb-firewall.md)</li></ul>   |
| **Utiliser le Centre d’administration Microsoft Endpoint Manager** | Si votre entreprise utilise déjà Intune pour gérer les stratégies de sécurité, vous pouvez continuer à utiliser le centre d’administration Endpoint Manager pour gérer vos appareils et stratégies de sécurité. Pour en savoir plus, consultez [Gérer la sécurité des appareils avec les stratégies de sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security-policy). <p>Si vous décidez de basculer vers le [processus de configuration simplifié dans Defender entreprise](mdb-simplified-configuration.md), vous serez invité à supprimer les stratégies de sécurité existantes dans Intune pour éviter [les conflits](mdb-troubleshooting.yml) de stratégie ultérieurement. |

> [!IMPORTANT]
> Si vous gérez des stratégies de sécurité dans le portail Microsoft 365 Defender, vous pouvez *afficher* ces stratégies dans le centre d’administration Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)), où elles sont répertoriées en tant que stratégies **antivirus** ou **pare-feu**. Lorsque vous affichez vos stratégies de pare-feu dans le Centre d’administration, deux stratégies sont répertoriées : une pour la protection pare-feu et une autre pour les règles personnalisées.

## <a name="view-or-edit-your-next-generation-protection-policies"></a>Afficher ou modifier vos stratégies de protection de nouvelle génération

Selon que vous utilisez le portail Microsoft 365 Defender ou le Centre d’administration Microsoft Endpoint Manager pour gérer vos stratégies de protection de nouvelle génération, utilisez l’une des procédures suivantes :

| Portail | Procedure |
|:---|:---|
| portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) |<ol><li>Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.</li><li>Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.</li><li>Sélectionnez un onglet de système d’exploitation (par exemple, **clients Windows**).</li><li>Développez la **protection nouvelle génération** pour afficher votre liste de stratégies.</li><li>Sélectionnez une stratégie pour afficher plus de détails sur la stratégie.</li><li>Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants : <ul><li>[Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)</li><li>[Comprendre les paramètres de configuration de nouvelle génération](mdb-next-gen-configuration-settings.md)</li></ul></li><ol>  |
| Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) |Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Intune, [commencez par Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). <ol><li>Accédez à [https://endpoint.microsoft.com](https://endpoint.microsoft.com) et connectez-vous. Vous êtes maintenant dans le centre d’administration Endpoint Manager.</li><li>Sélectionnez **Sécurité des points de terminaison**.</li><li>Sélectionnez **Antivirus** pour afficher vos stratégies dans cette catégorie.</li></ol>|

## <a name="view-or-edit-your-firewall-policies-and-custom-rules"></a>Afficher ou modifier vos stratégies de pare-feu et vos règles personnalisées

Selon que vous utilisez le portail Microsoft 365 Defender ou le Centre d’administration Microsoft Endpoint Manager pour gérer la protection de votre pare-feu, utilisez l’une des procédures suivantes.

| Portail | Procedure |
|:---|:---|
| portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) |<ol><li>Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.</li><li>Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation et type de stratégie.</li><li>Sélectionnez un onglet de système d’exploitation (par exemple, **clients Windows**).</li><li>Développez **le Pare-feu** pour afficher votre liste de stratégies.</li><li>Sélectionnez une stratégie pour afficher les détails. </li><li>Pour apporter des modifications ou en savoir plus sur les paramètres de stratégie, consultez les articles suivants :<ul><li>[Afficher ou modifier des stratégies d’appareil](mdb-view-edit-policies.md)</li><li>[Paramètres du pare-feu](mdb-firewall.md)</li><li>[Gérer vos règles personnalisées pour les stratégies de pare-feu](mdb-custom-rules-firewall.md)</li><ul></li><ol>  |
| Centre d’administration Microsoft Endpoint Manager ([https://endpoint.microsoft.com](https://endpoint.microsoft.com)) |Pour obtenir de l’aide sur la gestion de vos paramètres de sécurité dans Intune, [commencez par Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security). <ol><li>Accédez à [https://endpoint.microsoft.com](https://endpoint.microsoft.com) et connectez-vous. Vous êtes maintenant dans le centre d’administration Endpoint Manager.</li><li>Sélectionnez **Sécurité des points de terminaison**.</li><li>Sélectionnez **Pare-feu** pour afficher vos stratégies dans cette catégorie. Les règles personnalisées définies pour la protection pare-feu sont répertoriées en tant que stratégies distinctes.</li></ol>|

## <a name="set-up-web-content-filtering"></a>Configurer le filtrage de contenu web

Le filtrage de contenu web permet à votre équipe de sécurité de suivre et de réglementer l’accès aux sites web en fonction des catégories de contenu, par exemple :

- Contenu pour adultes : sites liés aux cultes, au jeu, à la nudité, à la pornographie, au matériel sexuellement explicite ou à la violence
- Bande passante élevée : télécharger des sites, des sites de partage d’images ou des hôtes pair à pair
- Responsabilité légale : sites qui incluent des images d’abus d’enfants, favorisent des activités illégales, favorisent le plagiat ou la tricherie scolaire, ou qui favorisent des activités dangereuses
- Loisirs : sites qui fournissent des salles de conversation web, des jeux en ligne, des e-mails web ou des réseaux sociaux
- Non catégorisé : sites qui n’ont pas de contenu ou qui viennent d’être inscrits

Tous les sites web de ces catégories ne sont pas malveillants, mais ils peuvent être problématiques pour votre entreprise en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes. Vous pouvez créer une stratégie d’audit uniquement pour mieux comprendre si votre équipe de sécurité doit bloquer des catégories de sites web.

Le filtrage de contenu web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et Network Protection (Chrome, Firefox, Brave et Opera). Pour plus d’informations, consultez [Prérequis pour le filtrage de contenu web](../defender-endpoint/web-content-filtering.md#prerequisites).

### <a name="to-set-up-web-content-filtering"></a>Pour configurer le filtrage de contenu web

1. Dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), choisissez **Paramètres** >  de **filtrage de** >  contenu Web **+ Ajouter une stratégie**.

2. Spécifiez un nom et une description pour votre stratégie.

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer entièrement chaque catégorie parente, puis sélectionnez des catégories de contenu web spécifiques. Pour configurer une stratégie d’audit uniquement qui ne bloque aucun site web, ne sélectionnez aucune catégorie.

   Ne sélectionnez pas **Non catégorisé**.

4. Spécifiez l’étendue de la stratégie en sélectionnant les groupes d’appareils auxquels appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne peuvent pas accéder aux sites web dans les catégories sélectionnées.

5. Passez en revue le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à deux heures pour s’appliquer à vos appareils sélectionnés.

> [!TIP]
> Pour en savoir plus sur le filtrage de contenu web, consultez filtrage [de contenu web](../defender-endpoint/web-content-filtering.md).

## <a name="review-settings-for-advanced-features"></a>Passer en revue les paramètres des fonctionnalités avancées

Outre les stratégies de protection, de pare-feu et de filtrage de contenu web de nouvelle génération, Defender entreprise inclut des fonctionnalités de sécurité avancées. Ces fonctionnalités sont préconfigurées pour les paramètres recommandés. Vous pouvez revoir et modifier les paramètres en fonction des besoins de votre entreprise.

Pour accéder aux paramètres des fonctionnalités avancées dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), accédez à **Paramètres des** points de terminaison Fonctionnalités  > **avancées générales** >  > .

Le tableau suivant décrit les paramètres de fonctionnalité avancés.

| Setting | Description |
|:---|:---|
| **Examen automatisé** <br/>(activé par défaut) | À mesure que des alertes sont générées, des investigations automatisées peuvent se produire. Chaque investigation automatisée détermine si une menace détectée nécessite une action, puis prend ou recommande des actions de correction, telles que l’envoi d’un fichier en quarantaine, l’arrêt d’un processus, l’isolation d’un appareil ou le blocage d’une URL. Pendant l’exécution d’un examen, les autres alertes associées qui apparaissent sont ajoutées à l’examen jusqu’à la fin de l’opération. Si une entité affectée est vue ailleurs, l’enquête automatisée étend son étendue pour inclure cette entité, et le processus d’examen se répète.<p>Vous pouvez afficher les enquêtes sur la page **Incidents** . Sélectionnez un incident, puis sélectionnez l’onglet **Investigations** .<p>Par défaut, les fonctionnalités d’investigation et de réponse automatisées sont activées à l’échelle du locataire. **Nous vous recommandons de maintenir l’investigation automatisée activée**. Si vous la désactivez, la protection en temps réel dans l’Antivirus Microsoft Defender sera affectée et votre niveau de protection global sera réduit. <p>[En savoir plus sur les enquêtes automatisées](../defender-endpoint/automated-investigations.md).   |
| **Réponse en direct**  | Defender entreprise inclut les types d’actions de réponse manuelle suivants : <ul><li>Exécuter une analyse antivirus</li><li>Isoler l’appareil</li><li>Arrêter et mettre en quarantaine un fichier</li><li>Ajouter un indicateur pour bloquer ou autoriser un fichier</li></ul> <p>[En savoir plus sur les actions de réponse](../defender-endpoint/respond-machine-alerts.md). |
| **Réponse en direct pour les serveurs** | (Ce paramètre n’est actuellement pas disponible dans Defender entreprise.)   |
| **Exécution de scripts non signés live Response** | (Ce paramètre n’est actuellement pas disponible dans Defender entreprise.)  | 
| **Activer EDR en mode bloc**<br/>(activé par défaut) | Fournit une protection supplémentaire contre les artefacts malveillants lorsque l’Antivirus Microsoft Defender n’est pas le produit antivirus principal et s’exécute en mode passif sur un appareil. La détection et la réponse des points de terminaison (EDR) en mode bloc fonctionnent en arrière-plan pour corriger les artefacts malveillants détectés par les fonctionnalités EDR. De tels artefacts peuvent avoir été manqués par le produit antivirus principal non-Microsoft.<p>[En savoir plus sur EDR en mode bloc](../defender-endpoint/edr-in-block-mode.md). |
| **Autoriser ou bloquer un fichier** <br/>(activé par défaut) | Vous permet d’autoriser ou de bloquer un fichier à l’aide [d’indicateurs](../defender-endpoint/indicator-file.md). Cette fonctionnalité nécessite que l’Antivirus Microsoft Defender soit en mode actif et [que la protection cloud](../defender-endpoint/cloud-protection-microsoft-defender-antivirus.md) soit activée.<p>Le blocage d’un fichier empêche sa lecture, son écriture ou son exécution sur les appareils de votre organisation. <p>[En savoir plus sur les indicateurs pour les fichiers](../defender-endpoint/indicator-file.md).  |
| **Indicateurs réseau personnalisés**<br/>(activé par défaut) | Vous permet d’autoriser ou de bloquer une adresse IP, une URL ou un domaine à l’aide [d’indicateurs réseau](../defender-endpoint/indicator-ip-domain.md). Cette fonctionnalité nécessite que l’Antivirus Microsoft Defender soit en mode actif et [que la protection réseau](../defender-endpoint/enable-network-protection.md) soit activée.<p>Vous pouvez autoriser ou bloquer des adresses IP, des URL ou des domaines en fonction de votre renseignement sur les menaces. Vous pouvez également inviter les utilisateurs s’ils ouvrent une application risquée, mais l’invite ne les empêchera pas d’utiliser l’application.<p>[En savoir plus sur la protection réseau](../defender-endpoint/network-protection.md). |
| **Protection contre les falsifications**<br/>(nous vous recommandons d’activer ce paramètre) | La protection contre les falsifications empêche les applications malveillantes d’effectuer des actions telles que :<ul><li>Désactiver la protection contre les virus et les menaces</li><li>Désactiver la protection en temps réel</li><li>Désactiver la surveillance du comportement</li><li>Désactiver la protection cloud</li><li>Supprimer les mises à jour du renseignement de sécurité</li><li>Désactiver les actions automatiques sur les menaces détectées</li></ul><p>La protection contre les falsifications verrouille essentiellement l’Antivirus Microsoft Defender sur ses valeurs par défaut sécurisées et empêche la modification de vos paramètres de sécurité par les applications et les méthodes non autorisées. <p>[En savoir plus sur la protection contre les falsifications](../defender-endpoint/prevent-changes-to-security-settings-with-tamper-protection.md).  |
| **Afficher les détails de l’utilisateur**<br/>(activé par défaut) | Permet aux membres de votre organisation de voir des détails, tels que les images, les noms, les titres et les services des employés. Ces détails sont stockés dans Azure Active Directory (Azure AD).<p>[En savoir plus sur les profils utilisateur dans Azure AD](/azure/active-directory/fundamentals/active-directory-users-profile-azure-portal).  |
| **intégration Skype Entreprise**<br/>(activé par défaut) | Skype Entreprise a pris sa retraite en juillet 2021. Si vous n’avez pas encore migré vers Microsoft Teams, consultez [Configurer Microsoft Teams dans votre petite entreprise](/microsoftteams/deploy-small-business). <p>L’intégration à Microsoft Teams (ou à l’ancien Skype Entreprise) permet une communication en un clic entre les personnes de votre entreprise.   |
| **Filtrage du contenu web**<br/>(activé par défaut) | Bloque l’accès aux sites web qui contiennent du contenu indésirable et effectue le suivi de l’activité web dans tous les domaines. Consultez [Configurer le filtrage de contenu web](#set-up-web-content-filtering). |
| **connexion Microsoft Intune**<br/>(Nous vous recommandons d’activer ce paramètre si vous avez Intune) | Si l’abonnement de votre organisation inclut des Microsoft Intune (inclus dans [Microsoft 365 Business Premium](../../business/index.yml)), ce paramètre permet à Defender Entreprise de partager des informations sur les appareils avec Intune.  |
| **Découverte d’appareils**<br/>(activé par défaut) | Permet à votre équipe de sécurité de rechercher des appareils non gérés qui sont connectés à votre réseau d’entreprise. Les appareils inconnus et non gérés présentent des risques significatifs pour votre réseau, qu’il s’agisse d’une imprimante non modifiée, d’un appareil réseau avec une configuration de sécurité faible ou d’un serveur sans contrôle de sécurité.<p>La découverte d’appareils utilise des appareils intégrés pour détecter les appareils non gérés, afin que votre équipe de sécurité puisse intégrer les appareils non gérés et réduire votre vulnérabilité. <p>[En savoir plus sur la découverte d’appareils](../defender-endpoint/device-discovery.md).    |
| **Fonctionnalités en préversion** | Microsoft met continuellement à jour des services tels que Defender Entreprise pour inclure de nouvelles fonctionnalités et améliorations. Si vous choisissez de recevoir des fonctionnalités en préversion, vous serez parmi les premiers à essayer les fonctionnalités à venir dans l’expérience de préversion. <p>[En savoir plus sur les fonctionnalités en préversion](../defender-endpoint/preview.md).  |

## <a name="view-and-edit-other-settings-in-the-microsoft-365-defender-portal"></a>Afficher et modifier d’autres paramètres dans le portail Microsoft 365 Defender

Outre les stratégies de sécurité appliquées aux appareils, vous pouvez afficher et modifier d’autres paramètres dans Defender entreprise. Par exemple, vous spécifiez le fuseau horaire à utiliser, et vous pouvez embarquer (ou débarquer) des appareils. 

> [!NOTE]
> Vous pouvez voir plus de paramètres dans votre locataire que ce qui est répertorié dans cet article. Cet article met en évidence les paramètres les plus importants que vous devez examiner dans Defender entreprise.

### <a name="settings-to-review-for-defender-for-business"></a>Paramètres à examiner pour Defender Entreprise

Le tableau suivant décrit les paramètres que vous pouvez afficher et modifier dans Defender entreprise :

| Catégorie | Setting | Description |
|:---|:---|:---|
| **Centre de sécurité** | **Fuseau horaire** | Sélectionnez le fuseau horaire à utiliser pour les dates et heures affichées dans les incidents, les menaces détectées et l’examen et la correction automatisés. Vous pouvez utiliser UTC ou votre fuseau horaire local (*recommandé*).  |
| **Microsoft 365 Defender** | **Account** | Affichez les détails tels que l’emplacement de stockage de vos données, votre ID de locataire et votre ID d’organisation (organisation). |
| **Microsoft 365 Defender**  | **Fonctionnalités en préversion**  | Activez les fonctionnalités en préversion pour essayer les fonctionnalités à venir et les nouvelles fonctionnalités. Vous pouvez être parmi les premiers à afficher un aperçu des nouvelles fonctionnalités et à fournir des commentaires. |
| **Points de terminaison**  | **Notifications par e-mail** | Configurez ou modifiez vos règles de notification par e-mail. Lorsque des vulnérabilités sont détectées ou qu’une alerte est créée, les destinataires spécifiés dans vos règles de notification par e-mail reçoivent un e-mail. [En savoir plus sur les notifications par e-mail](mdb-email-notifications.md). |
| **Points de terminaison**   | **Gestion des** >  appareils **Intégration** | Intégrer des appareils à Defender entreprise à l’aide d’un script téléchargeable. Pour plus d’informations, consultez [Intégrer des appareils à Defender entreprise](mdb-onboard-devices.md).   |  
| **Points de terminaison**  |  **Gestion des** >  appareils **Désintégrage** | Désintégrez (supprimez) les appareils de Defender pour Entreprises. Lorsque vous déconnectez un appareil, il n’envoie plus de données à Defender entreprise, mais les données reçues avant la désintégrage sont conservées. Pour plus d’informations, consultez [Désintégrage d’un appareil](mdb-offboard-devices.md).  |

### <a name="access-your-settings-in-the-microsoft-365-defender-portal"></a>Accéder à vos paramètres dans le portail Microsoft 365 Defender

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com/](https://security.microsoft.com/)), puis connectez-vous.

2. Sélectionnez **Paramètres**, puis sélectionnez une catégorie (par exemple, **Centre de sécurité**, **Microsoft 365 Defender** ou Points de **terminaison**).

3. Dans la liste des paramètres, sélectionnez un élément à afficher ou à modifier.

## <a name="next-steps"></a>Prochaines étapes

- [Prise en main de Defender entreprise](mdb-get-started.md)
- [Gérer les appareils dans Defender entreprise](mdb-manage-devices.md)
- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
- [Afficher ou modifier des stratégies dans Defender entreprise](mdb-view-edit-policies.md)
