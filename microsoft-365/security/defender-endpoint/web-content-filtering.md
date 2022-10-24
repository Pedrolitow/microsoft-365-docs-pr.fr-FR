---
title: Filtrage du contenu web
description: Utilisez le filtrage de contenu web dans Microsoft Defender pour point de terminaison pour suivre et réglementer l’accès aux sites web en fonction de leurs catégories de contenu.
keywords: protection web, protection contre les menaces web, navigation web, surveillance, rapports, cartes, liste de domaines, sécurité, hameçonnage, programmes malveillants, exploit, sites web, protection réseau, Edge, Internet Explorer, Chrome, Firefox, navigateur web
ms.service: microsoft-365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
ms.author: deniseb
author: denisebmsft
ms.localizationpriority: medium
ms.date: 10/24/2022
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- tier2
ms.custom: admindeeplinkDEFENDER
ms.topic: conceptual
ms.subservice: mde
search.appverid: met150
ms.openlocfilehash: 60a92ef217e572ec8ea9554c2870191f581dfa70
ms.sourcegitcommit: 0ca3ab2abe07810e9b2cc2d806e3c6b9f35b146c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2022
ms.locfileid: "68684986"
---
# <a name="web-content-filtering"></a>Filtrage du contenu web

**S’applique à :**
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)
- [Microsoft Defender pour point de terminaison Plan 1](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour point de terminaison Plan 2](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft Defender pour les PME](../defender-business/mdb-overview.md)

> [!TIP]
> Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-main-abovefoldlink&rtc=1)


## <a name="what-is-web-content-filtering"></a>Qu’est-ce que le filtrage de contenu web ?

Le filtrage de contenu web fait partie des fonctionnalités de [protection web](web-protection-overview.md) dans Microsoft Defender pour point de terminaison et Microsoft Defender pour entreprises. Le filtrage de contenu web permet à votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites web (même s’ils ne sont pas malveillants) peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

Configurez des stratégies sur vos groupes d’appareils pour bloquer certaines catégories. Le blocage d’une catégorie empêche les utilisateurs au sein de groupes d’appareils spécifiés d’accéder aux URL associées à la catégorie. Pour toute catégorie qui n’est pas bloquée, les URL sont automatiquement auditées. Vos utilisateurs peuvent accéder aux URL sans interruption, et vous allez collecter des statistiques d’accès pour vous aider à créer une décision de stratégie plus personnalisée. Vos utilisateurs verront une notification de blocage si un élément de la page qu’ils consultent effectuent des appels à une ressource bloquée.

> [!NOTE]
> La création de groupes d’appareils est prise en charge dans Defender pour point de terminaison Plan 1 et Plan 2.

Le filtrage de contenu web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et la protection réseau (Chrome, Firefox, Brave et Opera). Pour plus d’informations sur la prise en charge des [navigateurs](#prerequisites) , consultez la section Prérequis.

## <a name="benefits-of-web-content-filtering"></a>Avantages du filtrage de contenu web

- Les utilisateurs ne peuvent pas accéder aux sites web dans des catégories bloquées, qu’ils naviguent localement ou non.
- Votre équipe de sécurité peut accéder aux rapports web dans le même emplacement central, avec une visibilité sur les blocs réels et l’utilisation du web.
- Si vous utilisez Defender pour point de terminaison, votre équipe de sécurité peut déployer facilement des stratégies sur des groupes d’utilisateurs à l’aide de groupes d’appareils définis dans [Microsoft Defender pour point de terminaison paramètres de contrôle d’accès en fonction du rôle](/microsoft-365/security/defender-endpoint/rbac).
- Si vous utilisez Defender for Business, vous pouvez définir une stratégie de filtrage de contenu web qui sera appliquée à tous les utilisateurs. 

## <a name="prerequisites"></a>Configuration requise

Avant d’essayer cette fonctionnalité, vérifiez que vous répondez aux exigences décrites dans le tableau suivant :

| Conditions requises | Description |
|:---|:---|
| Abonnement | Votre abonnement doit inclure l’un des éléments suivants :<br/>- [Windows 10/11 Entreprise E5](/windows/deployment/deploy-enterprise-licenses)<br/>- [Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise/e5?activetab=pivot%3aoverviewtab)<br/>- Microsoft 365 E5 Sécurité<br/>- [Microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise/e3?activetab=pivot%3aoverviewtab)<br/>- [Microsoft Defender pour point de terminaison Plan 1 ou Plan 2](../defender/eval-defender-endpoint-overview.md)<br/>- [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md)<br/>- [Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium)|
| Accès au portail | Vous devez avoir accès au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. |
| Système d’exploitation | Les appareils de votre organisation doivent exécuter l’un des systèmes d’exploitation suivants avec les [dernières mises à jour antivirus/anti-programme malveillant](manage-updates-baselines-microsoft-defender-antivirus.md) : <br/>- Windows 11<br/>- mise à jour anniversaire Windows 10 (version 1607) ou ultérieure |
| Protection associée | [Windows Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) et la [protection réseau](network-protection.md) doivent être activés sur les appareils de votre organisation. |

## <a name="data-handling"></a>Traitement des données

Les données sont stockées dans la région sélectionnée dans le cadre de vos [paramètres de gestion des données Microsoft Defender pour point de terminaison](data-storage-privacy.md). Vos données ne quitteront pas le centre de données dans cette région. En outre, vos données ne seront pas partagées avec des tiers, y compris nos fournisseurs de données.

## <a name="precedence-for-multiple-active-policies"></a>Priorité pour plusieurs stratégies actives

L’application de plusieurs stratégies de filtrage de contenu web différentes sur le même appareil entraîne l’application de la stratégie plus restrictive pour chaque catégorie. Prenons l’exemple du scénario suivant :

- **Stratégie 1** : bloque les catégories 1 et 2 et audite le reste
- **Stratégie 2** : bloque les catégories 3 et 4 et audite le reste

Le résultat est que les catégories 1 à 4 sont toutes bloquées.  Cela est illustré dans l’image suivante.

:::image type="content" source="images/web-content-filtering-policies-mode-precedence.png" alt-text="Illustre la priorité du mode de blocage de stratégie de filtrage de contenu web par rapport au mode audit":::

## <a name="turn-on-web-content-filtering"></a>Activer le filtrage de contenu web

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portail Microsoft 365 Defender</a> et connectez-vous.

2. Dans le volet de navigation, sélectionnez **Paramètres Points** \> **de terminaison** **Fonctionnalités avancées**\> **générales**\>. 

3. Faites défiler vers le bas jusqu’à ce que le **filtrage de contenu web s’affiche**. 

4. Basculez sur **Activé**, puis sélectionnez **Enregistrer les préférences**.

### <a name="configure-web-content-filtering-policies"></a>Configurer des stratégies de filtrage de contenu web

Les stratégies de filtrage de contenu web spécifient les catégories de sites qui sont bloquées sur les groupes d’appareils. Pour gérer les stratégies, accédez à **Paramètres Points** \> **de terminaison** \> **Filtrage du contenu web** (sous **Règles**).

Les stratégies peuvent être déployées pour bloquer l’une des catégories parentes ou enfants suivantes :

<details>
<summary>Contenu pour adultes</summary>

**Cultes** : Sites liés à des groupes ou des mouvements dont les membres démontrent la passion pour un système de croyance différent de ceux qui sont socialement acceptés. 

**Jeux d’argent** : jeux d’argent en ligne et sites qui font la promotion des compétences et de la pratique du jeu.

**Nudité** : sites qui fournissent des images ou des vidéos entièrement frontales et semi-nues, généralement sous forme artistique, et qui peuvent permettre le téléchargement ou la vente de tels documents.

**Pornographie / Sexuellement explicite** : Sites contenant du contenu sexuellement explicite sous forme d’image ou de texte. Toute forme de matériel sexuellement orienté est également listé ici.

**Éducation sexuelle** : Sites qui traitent du sexe et de la sexualité d’une manière informative et non voyeuriste, y compris des sites qui fournissent de l’éducation sur la reproduction humaine et la contraception, des sites qui offrent des conseils sur la prévention de l’infection par des maladies sexuelles et des sites qui offrent des conseils sur des questions de santé sexuelle.

**Sans goût** : sites orientés vers du contenu inadapté pour les écoliers ou qu’un employeur serait mal à l’aise avec l’accès de son personnel, mais pas nécessairement violent ou pornographique.

**Violence** : Sites qui affichent ou font la promotion de contenu lié à la violence contre les humains ou les animaux.

</details>

<details>
<summary>Bande passante élevée</summary>

**Sites de téléchargement** : sites dont la fonction principale est de permettre aux utilisateurs de télécharger du contenu multimédia ou des programmes, tels que des programmes informatiques.

**Partage d’images** : sites utilisés principalement pour la recherche ou le partage de photos, y compris ceux qui ont des aspects sociaux.

**Pair à pair** : sites qui hébergent des logiciels P2P (peer-to-peer) ou facilitent le partage de fichiers à l’aide d’un logiciel P2P.

**Streaming multimédia & téléchargements** : sites dont la fonction principale est la distribution de médias de streaming, ou sites qui permettent aux utilisateurs de rechercher, regarder ou écouter des médias en streaming.
  
</details>

<details>
<summary>Responsabilité légale</summary>

**Images d’abus d’enfants** : sites qui incluent des images de pédopornographie ou de pornographie. 

**Activités criminelles** : sites qui donnent des instructions, des conseils ou la promotion d’activités illégales.

**Piratage** : sites qui fournissent des ressources pour une utilisation illégale ou douteuse de logiciels ou de matériel informatique, y compris les sites qui distribuent du matériel protégé par des droits d’auteur qui ont été piratés.

**Haine & l’intolérance** : sites faisant la promotion d’opinions agressives, dégradantes ou abusives à l’égard de toute partie de la population qui pourrait être identifiée par la race, la religion, le sexe, l’âge, la nationalité, le handicap physique, la situation économique, les préférences sexuelles ou tout autre choix de mode de vie.

**Drogues illicites** : Sites qui vendent des substances illégales ou contrôlées, favorisent l’abus de substances ou vendent des accessoires connexes.

**Logiciels illégaux** : sites qui contiennent ou favorisent l’utilisation de logiciels malveillants, de logiciels espions, de botnets, d’escroqueries par hameçonnage ou de piratage & le vol de droits d’auteur.

**Tricherie scolaire** : sites liés au plagiat ou à la tricherie scolaire. 

**Automutilation** : sites qui favorisent l’automutilation, y compris les sites de cyberintimidation qui contiennent des messages abusifs et/ou menaçants envers les utilisateurs.

**Armes** : Tout site qui vend des armes ou préconise l’utilisation d’armes, y compris, mais sans s’y limiter, les armes, les couteaux et les munitions.

</details>

<details>
<summary>Loisirs</summary>

**Conversation** : sites qui sont principalement des salles de conversation web.

**Jeux** : Sites relatifs aux jeux vidéo ou informatiques, y compris les sites qui font la promotion des jeux en hébergeant des services en ligne ou des informations relatives aux jeux.

**Messagerie instantanée** : sites qui peuvent être utilisés pour télécharger un logiciel de messagerie instantanée ou une messagerie instantanée basée sur le client.

**Réseau professionnel** : sites qui fournissent des services de mise en réseau professionnels.

**Réseaux sociaux** : sites qui fournissent des services de réseautage social.

**E-mail web** : sites offrant des services de messagerie web.
  
</details>

<details>
<summary>Uncategorized</summary>

**Domaines nouvellement enregistrés** : sites qui ont été récemment inscrits au cours des 30 derniers jours et qui n’ont pas encore été déplacés vers une autre catégorie.

**Domaines parqués** : sites qui n’ont pas de contenu ou qui sont parqués pour une utilisation ultérieure.
  
**REMARQUE** : Uncategorized contient uniquement les domaines nouvellement inscrits et les domaines parqués, et n’inclut pas tous les autres sites en dehors de ces catégories.
  
</details>

### <a name="create-a-policy"></a>Créer une stratégie

Pour ajouter une nouvelle stratégie, procédez comme suit :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, choisissez **Paramètres Points** > **de terminaison** > **Filtrage du** >  contenu web **+ Ajouter une stratégie**.

2. Spécifiez un nom.

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer entièrement chaque catégorie parente et sélectionner des catégories de contenu web spécifiques.

4. Spécifiez l’étendue de la stratégie. Sélectionnez les groupes d’appareils pour spécifier où appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne pourront pas accéder aux sites web dans les catégories sélectionnées.

   > [!IMPORTANT]
   > Si vous utilisez Microsoft 365 Business Premium ou Defender for Business, votre stratégie de filtrage de contenu web est appliquée à tous les utilisateurs par défaut. L’étendue ne s’applique pas.

5. Passez en revue le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à 2 heures pour s’appliquer à vos appareils sélectionnés.

> [!NOTE]
> - Vous pouvez déployer une stratégie sans sélectionner de catégorie sur un groupe d’appareils. Cette action crée une stratégie d’audit uniquement pour vous aider à comprendre le comportement de l’utilisateur avant de créer une stratégie de bloc.
> - Si vous supprimez une stratégie ou modifiez des groupes d’appareils en même temps, cela peut entraîner un retard dans le déploiement de la stratégie.
> - Le blocage de la catégorie « Non catégorisé » peut entraîner des résultats inattendus et indésirables.

## <a name="end-user-experience"></a>Expérience de l’utilisateur final

L’expérience de blocage pour les navigateurs tiers pris en charge est fournie par la protection réseau, qui fournit un message au niveau du système informant l’utilisateur d’une connexion bloquée. Pour une expérience dans le navigateur plus conviviale, envisagez d’utiliser Microsoft Edge.

### <a name="allow-specific-websites"></a>Autoriser des sites web spécifiques

Il est possible de remplacer la catégorie bloquée dans le filtrage de contenu web pour autoriser un seul site en créant une stratégie d’indicateur personnalisée. La stratégie d’indicateur personnalisé remplace la stratégie de filtrage de contenu web lorsqu’elle est appliquée au groupe d’appareils en question.

Pour définir un indicateur personnalisé, procédez comme suit :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, accédez à **Paramètres Indicateurs** \> de **point de terminaison** \>  \> **URL/Domaine** \> **Ajouter un élément**.

2. Entrez le domaine du site.

3. Définissez l’action de stratégie sur **Autoriser**.

### <a name="dispute-categories"></a>Catégories de litiges

Si vous rencontrez un domaine qui a été classé de manière incorrecte, vous pouvez contester la catégorie directement à partir du portail Microsoft 365 Defender.

Pour contester la catégorie d’un domaine, accédez à **Rapports Protection** \> \> **Web** Web **Filtrage des détails** \> **Domaines**. Sous l’onglet Domaines des rapports de filtrage de contenu web, vous verrez des points de suspension en regard de chacun des domaines. Pointez sur ces points de suspension et sélectionnez **Catégorie de litige**.

Un panneau s’ouvre dans lequel vous pouvez sélectionner la priorité et ajouter des détails supplémentaires, tels que la catégorie suggérée pour la reclassement. Une fois que vous avez terminé le formulaire, sélectionnez **Envoyer**. Notre équipe examinera la demande dans un délai d’un jour ouvrable. Pour un déblocage immédiat, créez un [indicateur d’autorisation personnalisé](indicator-ip-domain.md).

## <a name="web-content-filtering-cards-and-details"></a>Cartes de filtrage de contenu web et détails

Sélectionnez **Rapports** \> **Protection web** pour afficher les cartes contenant des informations sur le filtrage de contenu web et la protection contre les menaces web. Les cartes suivantes fournissent des informations récapitulatives sur le filtrage de contenu web.

### <a name="web-activity-by-category"></a>Activité web par catégorie

Cette carte répertorie les catégories de contenu web parent avec l’augmentation ou la diminution la plus importante du nombre de tentatives d’accès. Comprendre les changements radicaux dans les modèles d’activité web dans votre organisation depuis les 30 derniers jours, 3 mois ou 6 mois. Sélectionnez un nom de catégorie pour afficher plus d’informations.

Au cours des 30 premiers jours de l’utilisation de cette fonctionnalité, votre organisation peut ne pas disposer de suffisamment de données pour afficher ces informations.

:::image type="content" source="images/web-activity-by-category600.png" alt-text="Carte activité web par catégorie" lightbox="images/web-activity-by-category600.png":::

### <a name="web-content-filtering--summary-card"></a>Carte de résumé du filtrage de contenu web

Cette carte affiche la distribution des tentatives d’accès bloqué entre les différentes catégories de contenu web parent. Sélectionnez l’une des barres colorées pour afficher plus d’informations sur une catégorie web parente spécifique.

:::image type="content" source="images/web-content-filtering-summary.png" alt-text="Carte récapitulative du filtrage de contenu web" lightbox="images/web-content-filtering-summary.png":::

### <a name="web-activity-summary-card"></a>Carte récapitulative de l’activité web

Cette carte affiche le nombre total de demandes de contenu web dans toutes les URL.

:::image type="content" source="images/web-activity-summary.png" alt-text="Carte récapitulative de l’activité web" lightbox="images/web-activity-summary.png":::

### <a name="view-card-details"></a>Afficher les détails de la carte

Vous pouvez accéder aux **détails du rapport** pour chaque carte en sélectionnant une ligne de tableau ou une barre de couleur dans le graphique de la carte. La page de détails du rapport pour chaque carte contient des données statistiques détaillées sur les catégories de contenu web, les domaines de site web et les groupes d’appareils.

:::image type="content" source="images/web-protection-report-details.png" alt-text="Détails du rapport de protection web" lightbox="images/web-protection-report-details.png":::

- **Catégories web** : répertorie les catégories de contenu web qui ont eu des tentatives d’accès dans votre organisation. Sélectionnez une catégorie spécifique pour ouvrir un menu volant résumé.

- **Domaines** : répertorie les domaines web qui ont été consultés ou bloqués dans votre organisation. Sélectionnez un domaine spécifique pour afficher des informations détaillées sur ce domaine.

- **Groupes d’appareils** : répertorie tous les groupes d’appareils qui ont généré une activité web dans votre organisation

Utilisez le filtre d’intervalle de temps en haut à gauche de la page pour sélectionner une période. Vous pouvez également filtrer les informations ou personnaliser les colonnes. Sélectionnez une ligne pour ouvrir un volet volant avec encore plus d’informations sur l’élément sélectionné.

### <a name="known-issues-and-limitations"></a>Problèmes connus et conseils

Seul Microsoft Edge est pris en charge si la configuration du système d’exploitation de votre appareil est Server (**cmd** \> **Systeminfo** \> **OS Configuration**). La protection réseau n’est prise en charge qu’en mode Inspect sur les appareils serveur, qui est responsable de la sécurisation du trafic entre les navigateurs tiers pris en charge.

Seul Microsoft Edge est pris en charge et la protection réseau n’est pas prise en charge sur Windows 10 hôtes azure Virtual Desktop multisession.

Actuellement, la protection réseau ne prend pas en charge l’inspection SSL, ce qui peut entraîner l’autorisation de certains sites par le filtrage de contenu web qui serait normalement bloqué. Les sites seraient autorisés en raison d’un manque de visibilité du trafic chiffré après la négociation TLS et d’une incapacité à analyser certaines redirections.  Cela inclut les redirections de certaines pages de connexion de messagerie web vers la page de boîte aux lettres. Comme solution de contournement acceptée, vous pouvez créer un indicateur de blocage personnalisé pour la page de connexion afin de vous assurer qu’aucun utilisateur n’est en mesure d’accéder au site. Gardez à l’esprit que cela peut bloquer leur accès à d’autres services associés au même site web. 

Si vous utilisez Microsoft 365 Business Premium ou Microsoft Defender pour entreprises, vous pouvez définir une stratégie de filtrage de contenu web pour votre environnement. Cette stratégie s’applique par défaut à tous les utilisateurs.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
- [Répondre aux menaces web](web-protection-response.md)
- [Configuration requise pour la protection réseau](web-content-filtering.md)
