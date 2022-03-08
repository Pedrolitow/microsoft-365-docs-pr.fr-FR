---
title: Filtrage du contenu web
description: Utilisez le filtrage de contenu web dans Microsoft Defender pour point de terminaison pour suivre et contrôler l’accès aux sites web en fonction de leurs catégories de contenu.
keywords: protection web, protection contre les menaces web, navigation web, surveillance, rapports, cartes, liste de domaines, sécurité, hameçonnage, programme malveillant, attaque, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.technology: mde
ms.openlocfilehash: 14d45f4ac22a9707b380d817cb89da1bbee562e2
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63326508"
---
# <a name="web-content-filtering"></a>Filtrage du contenu web

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)

Le filtrage de contenu Web fait partie des fonctionnalités de [protection Web](web-protection-overview.md) de Microsoft Defender pour point de terminaison. Il permet à votre organisation de suivre et de contrôler l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites web, bien qu’ils ne soient pas malveillants, peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

Configurez des stratégies sur vos groupes d’appareils pour bloquer certaines catégories. Le blocage d’une catégorie empêche les utilisateurs au sein de groupes d’appareils spécifiés d’accéder aux URL associées à la catégorie. Pour toute catégorie qui n’est pas bloquée, les URL sont automatiquement auditées. Vos utilisateurs peuvent accéder aux URL sans interruption, et vous allez collecter des statistiques d’accès pour vous aider à créer une décision de stratégie plus personnalisée. Vos utilisateurs voient une notification de blocage si un élément de la page qu’ils voient appelle une ressource bloquée.

Le filtrage de contenu Web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et la Protection du réseau (Chrome, Firefox, Firefox et Opera). Pour plus d’informations sur la prise en charge du navigateur, consultez la section des conditions préalables.

## <a name="benefits-of-web-content-filtering"></a>Avantages du filtrage de contenu web

- Les utilisateurs ne peuvent pas accéder aux sites web dans des catégories bloquées, qu’ils naviguent en local ou en de suite.

- Votre équipe de sécurité peut déployer facilement des stratégies pour des groupes d’utilisateurs à l’aide de groupes d’appareils définis dans les paramètres de contrôle d’accès basés sur les [rôles Microsoft Defender for Endpoint](/microsoft-365/security/defender-endpoint/rbac).

- Votre équipe de sécurité peut accéder aux rapports web dans le même emplacement central, avec une visibilité sur les blocs réels et l’utilisation du web.

## <a name="prerequisites"></a>Prerequisites

Avant d’essayer cette fonctionnalité, assurez-vous que vous disposez des conditions suivantes :

- Votre abonnement inclut l’une des Windows 10 Entreprise suivantes : Windows 10 Entreprise E5, Microsoft 365 E5, Microsoft 365 E5 Sécurité, Microsoft 365 E3 + Microsoft 365 E5 Sécurité  module ou licence autonome Microsoft Defender pour point de terminaison. 

- Vous avez accès à <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender portail.</a>

- Les appareils de votre organisation exécutent la mise à jour anniversaire Windows 10 (version 1607) ou une version ultérieure, ou Windows 11 avec les dernières mises à jour [antivirus/anti-programme malveillant](manage-updates-baselines-microsoft-defender-antivirus.md).

- Windows Defender SmartScreen et la Protection du réseau sont activés sur les appareils de votre organisation.

## <a name="data-handling"></a>Traitement des données

Les données sont stockées dans la région sélectionnée dans le cadre de vos paramètres de gestion des données [de Microsoft Defender for Endpoint](data-storage-privacy.md). Vos données ne quitteront pas le centre de données dans cette région. En outre, vos données ne seront pas partagées avec des tiers, y compris nos fournisseurs de données.

## <a name="turn-on-web-content-filtering"></a>Activer le filtrage de contenu web

Dans le portail de navigation de gauche <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a>,  \> sélectionnez Paramètres **fonctionnalités avancées générales** \>  \> des points de **terminaison**. Faites défiler vers le bas jusqu’à ce que l’entrée du filtrage **de contenu Web s’y voie.** Basculez sur Les préférences **d’on** et **d’enregistrer**.

### <a name="configure-web-content-filtering-policies"></a>Configurer des stratégies de filtrage de contenu web

Les stratégies de filtrage de contenu Web spécifient les catégories de site bloquées sur les groupes d’appareils. Pour gérer les stratégies, go to **Paramètres** \> **Endpoints** \> **Web content filtering** (under **Rules**).

Les stratégies peuvent être déployées pour bloquer l’une des catégories parent ou enfant suivantes :

<details>
<summary>Contenu pour adultes</summary>

**Domaines :** sites liés à des groupes ou des mouvements dont les membres font preuve d’une enthousiasme pour un système qui est différent de ceux qui sont socialement acceptés. 

**Jeux :** jeux en ligne et sites qui favorisent les compétences et la pratique en matière de jeux.

**Nudity** : sites qui fournissent des images ou des vidéos pleines frontales et semi-intégrales, généralement sous forme d’illustrations, et qui peuvent autoriser le téléchargement ou la vente de ces documents.

**Forcément explicite :** sites contenant du contenu explicitement explicite sous forme d’image ou de texte. Toute forme de contenu à orientation sexuelle est également répertoriée ici.

Éducation sexuelle : sites qui traitent de la violence et de la violence d’une manière informative et non-toristique, y compris les sites qui fournissent une éducation sur la reproduction humaine et la santé humaine, les sites qui fournissent des conseils sur la prévention des infections sexuelles et les sites qui fournissent des conseils sur les sujets de santé sexuelle.

**N’a** pas de valeur : sites orientés vers du contenu qui n’est pas adapté aux enfants de l’école à afficher ou qu’un employeur ne serait pas en conflit avec l’accès de son personnel, mais pas nécessairement violent ou concis.

**Violence** : sites qui affichent ou promeuvent du contenu lié à la violence contre les humains ou les animaux.

</details>

<details>
<summary>Bande passante élevée</summary>

**Sites de téléchargement** : sites dont la fonction principale est de permettre aux utilisateurs de télécharger du contenu multimédia ou des programmes, tels que des programmes informatiques.

**Partage d’image** : sites principalement utilisés pour la recherche ou le partage de photos, y compris ceux qui ont des aspects sociaux.

**Pair à pair** : sites qui hébergent des logiciels P2P (peer-to-peer) ou facilitent le partage de fichiers à l’aide de logiciels P2P.

**Téléchargements de &** en continu : sites dont la fonction principale est la distribution de médias de diffusion en continu, ou sites qui permettent aux utilisateurs de rechercher, de regarder ou d’écouter du contenu multimédia en continu.
  
</details>

<details>
<summary>Responsabilité légale</summary>

**Images d’abus enfants** : sites qui incluent des images d’abus ou des images d’abus enfants. 

**Activités pénales** : sites qui donnent des instructions sur, des conseils ou la promotion d’activités illégales.

**Piratage :** sites qui fournissent des ressources pour une utilisation illégale ou discutable de logiciels informatiques ou de matériel, y compris les sites qui distribuent des documents protégés par des droits d’auteur qui ont été déchiffrés.

**&** de violence : sites qui promeuvent des opinions agressives, dégradées ou abusives sur n’importe quelle section de la population qui peuvent être identifiées par la course, le genre, l’âge, la nationalité, le handicap physique, la situation économique, les préférences sexuelles ou tout autre choix de style de vie.

**Consommation illégale :** sites qui vendent des produits illicites/contrôlés, promeuvent des abus ou vendent des accessoires connexes.

**Logiciels non** fiables : sites qui contiennent ou promeuvent l’utilisation de programmes malveillants, de logiciels espions, de botnets, d’tentatives de hameçonnage ou de piratage & de droits d’auteur.

**Enseignement scolaire :** sites liés au plagiarisme ou à la politique scolaire. 

**Auto-nuire :** sites qui promeuvent les auto-dommages, y compris les sites de cyberintimidation qui contiennent des messages abusifs et/ou offensants à l’égard des utilisateurs.

**Armes :** tout site qui vend des airs ou qui fait la défense de l’utilisation d’armes, y compris, mais sans s’y limiter, à l’histoire, à la chasse et à la défense.

</details>

<details>
<summary>Resoe</summary>

**Conversation** : sites qui sont principalement des salles de conversation web.

**Jeux :** sites relatifs aux jeux vidéo ou informatiques, y compris les sites qui promeuvent les jeux par le biais de l’hébergement de services en ligne ou d’informations relatives aux jeux.

**Messagerie instantanée :** sites qui peuvent être utilisés pour télécharger un logiciel de messagerie instantanée ou une messagerie instantanée client.

**Professional réseau :** sites qui fournissent des services de mise en réseau professionnels.

**Réseau social :** sites qui fournissent des services de réseau social.

**Messagerie web :** sites offrant des services de messagerie web.
  
</details>

<details>
<summary>Non catégorisé</summary>

**Domaines nouvellement inscrits** : sites qui ont été récemment inscrits au cours des 30 derniers jours et qui n’ont pas encore été déplacés vers une autre catégorie.

**Domaines parés :** sites qui n’ont pas de contenu ou qui sont parés pour une utilisation ultérieure.
  
**REMARQUE** : Uncategorized contient uniquement les domaines nouvellement inscrits et les domaines parqués, et n’inclut pas tous les autres sites en dehors de ces catégories.
  
</details>

### <a name="create-a-policy"></a>Créer une stratégie

Pour ajouter une nouvelle stratégie, suivez les étapes suivantes :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender, choisissez</a> **Paramètres** >  **de contenu Web** > **+ Ajouter une stratégie**.

2. Spécifiez un nom.

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer entièrement chaque catégorie parent et sélectionner des catégories de contenu web spécifiques.

4. Spécifiez l’étendue de la stratégie. Sélectionnez les groupes d’appareils pour spécifier où appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne pourront pas accéder aux sites web dans les catégories sélectionnées.

5. Examinez le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à 2 heures pour s’appliquer à vos appareils sélectionnés.

> [!NOTE]
>
> - Vous pouvez déployer une stratégie sans sélectionner de catégorie sur un groupe d’appareils. Cette action crée une stratégie d’audit uniquement pour vous aider à comprendre le comportement des utilisateurs avant de créer une stratégie de blocage.
> - Si vous supprimez une stratégie ou modifiez des groupes d’appareils en même temps, cela peut entraîner un retard dans le déploiement de la stratégie.
> - Le blocage de la catégorie « Non catégorisé » peut entraîner des résultats inattendus et inattendus.

## <a name="end-user-experience"></a>Expérience de l’utilisateur final

L’expérience de blocage pour les navigateurs tiers pris en charge est fournie par la Protection du réseau, qui fournit un message au niveau du système pour avertir l’utilisateur d’une connexion bloquée. Pour une expérience plus conviviale dans le navigateur, envisagez d’utiliser Microsoft Edge.

### <a name="allow-specific-websites"></a>Autoriser des sites web spécifiques

Il est possible de remplacer la catégorie bloquée dans le filtrage de contenu web pour autoriser un site unique en créant une stratégie d’indicateur personnalisée. La stratégie d’indicateur personnalisé va prendre le pas sur la stratégie de filtrage de contenu web lorsqu’elle est appliquée au groupe d’appareils en question.

Pour définir un indicateur personnalisé, suivez les étapes suivantes :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, Paramètres  \>  \> URL des indicateurs **de** \> point de terminaison **/Ajouter** \> **un élément de domaine**.

2. Entrez le domaine du site.

3. Définissez l’action de stratégie sur **Autoriser**.

### <a name="dispute-categories"></a>Catégories de litige

Si vous rencontrez un domaine qui a été classé de manière incorrecte, vous pouvez la disputer directement à partir du portail.

Pour litiger la catégorie d’un domaine, accédez à **Reports** \> **Web Protection** \> **Web Content Filtering Details** \> **Domains**. Sous l’onglet Domaines des rapports de filtrage de contenu Web, vous verrez des ellipses à côté de chacun des domaines. Pointez sur ces ellipses et sélectionnez **Catégorie litige**.

Un panneau s’ouvre où vous pouvez sélectionner la priorité et ajouter des détails, tels que la catégorie suggérée pour la catégorisation. Une fois que vous avez terminé le formulaire, sélectionnez **Envoyer**. Notre équipe examine la demande dans un jour ou deux. Pour un déblocage immédiat, créez [un indicateur d’autoriser personnalisé](indicator-ip-domain.md).

### <a name="url-category-lookup"></a>Recherche de catégorie d’URL

Pour déterminer la catégorie d’un site web, vous pouvez utiliser la fonction de recherche d’URL disponible sur le portail Microsoft 365 Defender (<https://security.microsoft.com>) sous **Recherche de points de** \> **terminaison**. Dans les résultats de recherche d’URL, la catégorie de filtrage de contenu web apparaît sous **URL/Détails du domaine**. Les administrateurs peuvent également en litige la catégorie du domaine directement à partir de cette page, comme illustré dans l’image suivante. Si le résultat de catégorie n’est pas affiché, l’URL n’est pas actuellement affectée à une catégorie de filtrage de contenu web existante.

![Image des résultats de recherche de catégorie de filtrage de contenu web.](../../media/web-content-filtering-category-lookup.png)

## <a name="web-content-filtering-cards-and-details"></a>Cartes et détails de filtrage de contenu Web

Sélectionnez **Reports** \> **Web Protection pour** afficher les cartes avec des informations sur le filtrage de contenu web et la protection contre les menaces web. Les cartes suivantes fournissent des informations récapitulatifs sur le filtrage de contenu web.

### <a name="web-activity-by-category"></a>Activité web par catégorie

Cette carte répertorie les catégories de contenu web parent avec la plus grande augmentation ou diminution du nombre de tentatives d’accès. Comprendre les changements majeurs dans les modèles d’activité web dans votre organisation depuis les 30 derniers jours, 3 mois ou 6 derniers mois. Sélectionnez un nom de catégorie pour afficher plus d’informations.

Au cours des 30 premiers jours d’utilisation de cette fonctionnalité, il se peut que votre organisation ne dispose pas de suffisamment de données pour afficher ces informations.

![Image de l’activité web par carte de catégorie.](images/web-activity-by-category600.png)

### <a name="web-content-filtering--summary-card"></a>Fiche récapitulatif du filtrage du contenu Web

Cette carte affiche la distribution des tentatives d’accès bloqué entre les différentes catégories de contenu web parent. Sélectionnez l’une des barres de couleur pour afficher plus d’informations sur une catégorie web parente spécifique.

![Image de la carte récapitulatif du filtrage du contenu web.](images/web-content-filtering-summary.png)

### <a name="web-activity-summary-card"></a>Carte récapitulatif des activités web

Cette carte affiche le nombre total de demandes de contenu web dans toutes les URL.

![Image de la carte récapitulatif des activités web.](images/web-activity-summary.png)

### <a name="view-card-details"></a>Afficher les détails de la carte

Vous pouvez accéder aux **détails du rapport** pour chaque carte en sélectionnant une ligne de tableau ou une barre de couleur dans le graphique de la carte. La page de détails du rapport pour chaque carte contient des données statistiques complètes sur les catégories de contenu web, les domaines de site web et les groupes d’appareils.

![Image des détails du rapport de protection web.](images/web-protection-report-details.png)

- **Catégories Web :** répertorie les catégories de contenu web qui ont connu des tentatives d’accès dans votre organisation. Sélectionnez une catégorie spécifique pour ouvrir un volant de synthèse.

- **Domaines :** répertorie les domaines web qui ont été accédés ou bloqués dans votre organisation. Sélectionnez un domaine spécifique pour afficher des informations détaillées sur ce domaine.

- **Groupes d’appareils** : répertorie tous les groupes d’appareils qui ont généré une activité web dans votre organisation

Utilisez le filtre de plage de temps en haut à gauche de la page pour sélectionner une période. Vous pouvez également filtrer les informations ou personnaliser les colonnes. Sélectionnez une ligne pour ouvrir un volet volant avec encore plus d’informations sur l’élément sélectionné.

### <a name="known-issues-and-limitations"></a>Problèmes connus et conseils

Seul Microsoft Edge est pris en charge si la configuration du système d’exploitation de votre appareil est Server (**cmd** \> **Systeminfo** \> **OS Configuration**). La protection du réseau est uniquement prise en charge en mode Inspect sur les appareils serveur, qui est responsable de la sécurisation du trafic sur les navigateurs tiers pris en charge.

Seul le Microsoft Edge est pris en charge et la Protection du réseau n’est pas prise en charge sur Windows 10 hôtes multisession Azure Virtual Desktop.

La Protection du réseau ne prend actuellement pas en charge l’inspection SSL, ce qui peut entraîner le blocage normal de certains sites par le filtrage de contenu Web. Les sites seraient autorisés en raison d’un manque de visibilité sur le trafic chiffré une fois que l’accord TLS a eu lieu et parce qu’il n’est pas en mesure d’en savoir plus sur certaines redirections.  Cela inclut les redirections de certaines pages de connexion de messagerie web vers la page de boîte aux lettres. En tant que solution de contournement acceptée, vous pouvez créer un indicateur de blocage personnalisé pour la page de connexion afin de vous assurer qu’aucun utilisateur n’est en mesure d’accéder au site. Gardez à l’esprit que cela peut bloquer leur accès à d’autres services associés au même site web. 

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
- [Répondre aux menaces web](web-protection-response.md)
- [Conditions requises pour la protection du réseau](web-content-filtering.md)
