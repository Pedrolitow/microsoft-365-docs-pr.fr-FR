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
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.custom: admindeeplinkDEFENDER
ms.topic: article
ms.subservice: mde
ms.openlocfilehash: 294549d49c37024d0f1c9ed94a325990aacbf572
ms.sourcegitcommit: d3ef9391f621e8f4ca70661184b3bb82c6cbda94
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2022
ms.locfileid: "67585859"
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

Le filtrage de contenu web fait partie des fonctionnalités de [protection web](web-protection-overview.md) dans Microsoft Defender pour point de terminaison et Microsoft Defender pour entreprises. Le filtrage de contenu web permet à votre organisation de suivre et de réglementer l’accès aux sites web en fonction de leurs catégories de contenu. La plupart de ces sites Web (même s’ils ne sont pas malveillants) peuvent être problématiques en raison des réglementations de conformité, de l’utilisation de la bande passante ou d’autres problèmes.

Configurez des stratégies entre vos groupes d’appareils pour bloquer certaines catégories. Le blocage d’une catégorie empêche les utilisateurs des groupes d’appareils spécifiés d’accéder aux URL associées à la catégorie. Pour toute catégorie qui n’est pas bloquée, les URL sont automatiquement auditées. Vos utilisateurs peuvent accéder aux URL sans interruption, et vous collectez des statistiques d’accès pour vous aider à créer une décision de stratégie plus personnalisée. Vos utilisateurs verront une notification de blocage si un élément de la page qu’ils consultent effectue des appels à une ressource bloquée.

Le filtrage de contenu web est disponible sur les principaux navigateurs web, avec des blocs exécutés par Windows Defender SmartScreen (Microsoft Edge) et Network Protection (Chrome, Firefox, Brave et Opera). Pour plus d’informations sur la prise en charge des navigateurs, consultez la section [des prérequis](#prerequisites) .

## <a name="benefits-of-web-content-filtering"></a>Avantages du filtrage de contenu web

- Les utilisateurs ne peuvent pas accéder aux sites web dans des catégories bloquées, qu’ils naviguent localement ou en déplacement.
- Votre équipe de sécurité peut accéder aux rapports web dans le même emplacement central, avec une visibilité sur les blocs réels et l’utilisation du web.
- Si vous utilisez Defender pour point de terminaison, votre équipe de sécurité peut facilement déployer des stratégies sur des groupes d’utilisateurs à l’aide de groupes d’appareils définis dans [Microsoft Defender pour point de terminaison paramètres de contrôle d’accès en fonction du rôle](/microsoft-365/security/defender-endpoint/rbac).
- Si vous utilisez Defender entreprise, vous pouvez définir une stratégie de filtrage de contenu web qui sera appliquée à tous les utilisateurs. 

## <a name="prerequisites"></a>Prerequisites

Avant d’essayer cette fonctionnalité, veillez à respecter les exigences décrites dans le tableau suivant :

| Conditions requises | Description |
|:---|:---|
| Abonnement | Votre abonnement doit inclure l’un des éléments suivants :<br/>- [Windows 10/11 Entreprise E5](/windows/deployment/deploy-enterprise-licenses)<br/>- [Microsoft 365 E5](https://www.microsoft.com/microsoft-365/enterprise/e5?activetab=pivot%3aoverviewtab)<br/>- Microsoft 365 E5 Sécurité<br/>- [Microsoft 365 E3](https://www.microsoft.com/microsoft-365/enterprise/e3?activetab=pivot%3aoverviewtab)<br/>- [Microsoft Defender pour point de terminaison plan 1 ou plan 2](../defender/eval-defender-endpoint-overview.md)<br/>- [Microsoft Defender pour entreprises](../defender-business/mdb-overview.md)<br/>- [Microsoft 365 Business Premium](https://www.microsoft.com/microsoft-365/business/microsoft-365-business-premium)|
| Accès au portail | Vous devez avoir accès au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>. |
| Système d’exploitation | Les appareils de votre organisation doivent exécuter l’un des systèmes d’exploitation suivants avec les [dernières mises à jour antivirus/anti-programme malveillant](manage-updates-baselines-microsoft-defender-antivirus.md) : <br/>- Windows 11<br/>- mise à jour anniversaire Windows 10 (version 1607) ou ultérieure |
| Protection associée | [Windows Defender SmartScreen](/windows/security/threat-protection/microsoft-defender-smartscreen/microsoft-defender-smartscreen-overview) et [la protection réseau](network-protection.md) doivent être activées sur les appareils de votre organisation. |

## <a name="data-handling"></a>Traitement des données

Les données sont stockées dans la région sélectionnée dans le cadre de vos [paramètres de gestion des données Microsoft Defender pour point de terminaison](data-storage-privacy.md). Vos données ne quittent pas le centre de données de cette région. En outre, vos données ne seront partagées avec aucun tiers, y compris nos fournisseurs de données.

## <a name="precedence-for-multiple-active-policies"></a>Priorité pour plusieurs stratégies actives

L’application de plusieurs stratégies de filtrage de contenu web différentes sur le même appareil entraîne l’application d’une stratégie plus restrictive pour chaque catégorie. Prenons l’exemple du scénario suivant :

- **Stratégie 1** : bloque les catégories 1 et 2 et audite le reste
- **Stratégie 2** : bloque les catégories 3 et 4 et audite le reste

Le résultat est que les catégories 1 à 4 sont toutes bloquées.  Ceci est illustré dans l’image suivante.

:::image type="content" source="images/web-content-filtering-policies-mode-precedence.png" alt-text="Illustre la précédence du mode de blocage de stratégie de filtrage de contenu web sur le mode audit":::

## <a name="turn-on-web-content-filtering"></a>Activer le filtrage de contenu web

1. Accédez au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Portail Microsoft 365 Defender</a> et connectez-vous.

2. Dans le volet de navigation, sélectionnez **Paramètres des** \> **points de terminaison Fonctionnalités avancées** \> **générales**\>. 

3. Faites défiler vers le bas jusqu’à ce que vous voyiez **le filtrage de contenu Web**. 

4. Basculez sur **Activé**, puis **sélectionnez Enregistrer les préférences**.

### <a name="configure-web-content-filtering-policies"></a>Configurer des stratégies de filtrage de contenu web

Les stratégies de filtrage de contenu web spécifient les catégories de sites bloquées sur quels groupes d’appareils. Pour gérer les stratégies, accédez au **filtrage de contenu Web** **Paramètres** \> **des** \> points de terminaison (sous **Règles**).

Les stratégies peuvent être déployées pour bloquer l’une des catégories parent ou enfant suivantes :

<details>
<summary>Contenu pour adultes</summary>

**Cultes** : Sites liés à des groupes ou des mouvements dont les membres démontrent leur passion pour un système de croyances différent de ceux qui sont socialement acceptés. 

**Jeux d’argent** : jeux en ligne et sites qui favorisent les compétences et la pratique du jeu.

**Nudité** : sites qui fournissent des images ou vidéos pleines frontales et semi-nues, généralement sous forme artistique, et qui peuvent autoriser le téléchargement ou la vente de tels matériaux.

**Pornographie / Sexuellement explicite** : sites contenant du contenu sexuellement explicite sous forme d’image ou de texte. Toute forme de matériel sexuellement orienté est également répertorié ici.

**Éducation sexuelle** : sites qui traitent du sexe et de la sexualité de manière informative et non-chroniste, y compris les sites qui fournissent une éducation sur la reproduction et la contraception humaines, les sites qui offrent des conseils sur la prévention de l’infection par les maladies sexuelles, et les sites qui offrent des conseils sur les questions de santé sexuelle.

**Insipide** : sites orientés vers du contenu qui ne convient pas aux enfants des écoles ou qu’un employeur serait mal à l’aise avec l’accès de son personnel, mais pas nécessairement violent ou pornographique.

**Violence** : sites qui affichent ou promeuvent du contenu lié à la violence envers les humains ou les animaux.

</details>

<details>
<summary>Bande passante élevée</summary>

**Sites de téléchargement** : sites dont la fonction principale est de permettre aux utilisateurs de télécharger du contenu multimédia ou des programmes, tels que des programmes informatiques.

**Partage d’images** : sites utilisés principalement pour la recherche ou le partage de photos, y compris ceux qui ont des aspects sociaux.

**P2P** : sites qui hébergent des logiciels P2P ou facilitent le partage de fichiers à l’aide du logiciel P2P.

**Médias de diffusion en continu & téléchargements** : sites dont la fonction principale est la distribution de médias de diffusion en continu, ou sites qui permettent aux utilisateurs de rechercher, de regarder ou d’écouter du contenu multimédia en streaming.
  
</details>

<details>
<summary>Responsabilité légale</summary>

**Images de mauvais traitements** envers les enfants : sites qui incluent des images de violence envers les enfants ou de la pornographie. 

**Activité criminelle** : sites qui donnent des instructions, des conseils sur ou la promotion d’activités illégales.

**Piratage** : sites qui fournissent des ressources pour l’utilisation illégale ou douteuse de logiciels ou de matériel informatique, y compris les sites qui distribuent du matériel protégé par le droit d’auteur qui a été craqué.

**Haine & l’intolérance** : sites favorisant des opinions agressives, dégradantes ou abusives sur toute partie de la population pouvant être identifiée par la race, la religion, le sexe, l’âge, la nationalité, l’incapacité physique, la situation économique, les préférences sexuelles ou tout autre choix de style de vie.

**Drogues illégales** : sites qui vendent des substances illégales/contrôlées, favorisent l’abus de substances ou vendent des accessoires connexes.

**Logiciels illégaux** : sites qui contiennent ou favorisent l’utilisation de logiciels malveillants, de logiciels espions, de botnets, d’escroqueries par hameçonnage ou de piratage & le vol de droits d’auteur.

**Triche à l’école**: Sites liés au plagiat ou à la tricherie scolaire. 

**Automutilation** : sites qui favorisent l’automutilation, y compris les sites de cyberintimidation qui contiennent des messages abusifs et/ou menaçants envers les utilisateurs.

**Armes** : tout site qui vend des armes ou préconise l’utilisation d’armes, y compris, mais sans s’y limiter, des armes à feu, des couteaux et des munitions.

</details>

<details>
<summary>Loisirs</summary>

**Conversation** : sites qui sont principalement des salles de conversation web.

**Jeux** : sites relatifs aux jeux vidéo ou informatiques, y compris les sites qui favorisent les jeux par le biais de l’hébergement de services en ligne ou d’informations relatives aux jeux.

**Messagerie instantanée** : sites qui peuvent être utilisés pour télécharger un logiciel de messagerie instantanée ou une messagerie instantanée basée sur le client.

**Réseau professionnel** : sites qui fournissent des services de mise en réseau professionnels.

**Réseaux sociaux** : sites qui fournissent des services de réseaux sociaux.

**E-mail web** : sites proposant des services de messagerie web.
  
</details>

<details>
<summary>Uncategorized</summary>

**Domaines nouvellement inscrits** : sites qui ont été récemment inscrits au cours des 30 derniers jours et qui n’ont pas encore été déplacés vers une autre catégorie.

**Domaines parqués** : sites qui n’ont pas de contenu ou qui sont garés pour une utilisation ultérieure.
  
**REMARQUE** : Uncategorized contient uniquement les domaines nouvellement inscrits et les domaines parqués, et n’inclut pas tous les autres sites en dehors de ces catégories.
  
</details>

### <a name="create-a-policy"></a>Créer une stratégie

Pour ajouter une nouvelle stratégie, procédez comme suit :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, choisissez **Paramètres** >  de **filtrage de** >  contenu Web **+ Ajouter une stratégie**.

2. Spécifiez un nom.

3. Sélectionnez les catégories à bloquer. Utilisez l’icône développer pour développer complètement chaque catégorie parente et sélectionner des catégories de contenu web spécifiques.

4. Spécifiez l’étendue de la stratégie. Sélectionnez les groupes d’appareils pour spécifier où appliquer la stratégie. Seuls les appareils des groupes d’appareils sélectionnés ne peuvent pas accéder aux sites web dans les catégories sélectionnées.

   > [!IMPORTANT]
   > Si vous utilisez Microsoft 365 Business Premium ou Defender entreprise, votre stratégie de filtrage de contenu web est appliquée par défaut à tous les utilisateurs. L’étendue ne s’applique pas.

5. Passez en revue le résumé et enregistrez la stratégie. L’actualisation de la stratégie peut prendre jusqu’à 2 heures pour s’appliquer à vos appareils sélectionnés.

> [!NOTE]
> - Vous pouvez déployer une stratégie sans sélectionner de catégorie sur un groupe d’appareils. Cette action crée une stratégie d’audit uniquement pour vous aider à comprendre le comportement de l’utilisateur avant de créer une stratégie de blocage.
> - Si vous supprimez une stratégie ou modifiez des groupes d’appareils en même temps, cela peut entraîner un retard dans le déploiement de la stratégie.
> - Le blocage de la catégorie « Uncategorized » peut entraîner des résultats inattendus et indésirables.

## <a name="end-user-experience"></a>Expérience de l’utilisateur final

L’expérience de blocage pour les navigateurs tiers pris en charge est fournie par la protection réseau, qui fournit un message au niveau du système informant l’utilisateur d’une connexion bloquée. Pour une expérience plus conviviale dans le navigateur, envisagez d’utiliser Microsoft Edge.

### <a name="allow-specific-websites"></a>Autoriser des sites web spécifiques

Il est possible de remplacer la catégorie bloquée dans le filtrage de contenu web pour autoriser un site unique en créant une stratégie d’indicateur personnalisée. La stratégie d’indicateur personnalisé remplace la stratégie de filtrage de contenu web lorsqu’elle est appliquée au groupe d’appareils en question.

Pour définir un indicateur personnalisé, procédez comme suit :

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, accédez à **l’URL des indicateurs de paramètres** \>  \> \> des **points** de terminaison/élément **d’ajout** **de domaine**\>.

2. Entrez le domaine du site.

3. Définissez l’action de stratégie sur **Autoriser**.

### <a name="dispute-categories"></a>Catégories de litiges

Si vous rencontrez un domaine qui a été classé de manière incorrecte, vous pouvez contester la catégorie directement à partir du portail Microsoft 365 Defender.

Pour contester la catégorie d’un domaine, accédez à **Reports** \> **Web Protection** \> **Web Content Filtering Details** \> **Domains**. Sous l’onglet Domaines des rapports de filtrage de contenu web, vous verrez des points de suspension à côté de chacun des domaines. Pointez sur ces points de suspension et sélectionnez **Catégorie de litige**.

Un panneau s’ouvre dans lequel vous pouvez sélectionner la priorité et ajouter d’autres détails, tels que la catégorie suggérée pour la recategorisation. Une fois le formulaire terminé, **sélectionnez Envoyer**. Notre équipe examinera la demande dans un délai d’un jour ouvrable. Pour le déblocage immédiat, créez un [indicateur d’autorisation personnalisé](indicator-ip-domain.md).

## <a name="web-content-filtering-cards-and-details"></a>Cartes et détails de filtrage de contenu web

Sélectionnez **Rapports** \> **protection web** pour afficher les cartes contenant des informations sur le filtrage de contenu web et la protection contre les menaces web. Les cartes suivantes fournissent des informations récapitulatives sur le filtrage de contenu web.

### <a name="web-activity-by-category"></a>Activité web par catégorie

Cette carte répertorie les catégories de contenu web parent avec la plus grande augmentation ou diminution du nombre de tentatives d’accès. Comprendre les changements radicals dans les modèles d’activité web dans votre organisation à partir des 30 derniers jours, 3 mois ou 6 mois. Sélectionnez un nom de catégorie pour afficher plus d’informations.

Dans les 30 premiers jours d’utilisation de cette fonctionnalité, votre organisation peut ne pas avoir suffisamment de données pour afficher ces informations.

:::image type="content" source="images/web-activity-by-category600.png" alt-text="Activité web par carte de catégorie" lightbox="images/web-activity-by-category600.png":::

### <a name="web-content-filtering--summary-card"></a>Carte récapitulative de filtrage de contenu web

Cette carte affiche la distribution des tentatives d’accès bloqué dans les différentes catégories de contenu web parent. Sélectionnez l’une des barres colorées pour afficher plus d’informations sur une catégorie web parente spécifique.

:::image type="content" source="images/web-content-filtering-summary.png" alt-text="Carte récapitulative de filtrage de contenu web" lightbox="images/web-content-filtering-summary.png":::

### <a name="web-activity-summary-card"></a>Carte récapitulative de l’activité web

Cette carte affiche le nombre total de demandes de contenu web dans toutes les URL.

:::image type="content" source="images/web-activity-summary.png" alt-text="Carte récapitulative de l’activité web" lightbox="images/web-activity-summary.png":::

### <a name="view-card-details"></a>Afficher les détails de la carte

Vous pouvez accéder aux **détails du rapport** pour chaque carte en sélectionnant une ligne de tableau ou une barre de couleur dans le graphique de la carte. La page de détails du rapport pour chaque carte contient des données statistiques détaillées sur les catégories de contenu web, les domaines de site web et les groupes d’appareils.

:::image type="content" source="images/web-protection-report-details.png" alt-text="Détails du rapport de protection web" lightbox="images/web-protection-report-details.png":::

- **Catégories web** : répertorie les catégories de contenu web qui ont eu des tentatives d’accès dans votre organisation. Sélectionnez une catégorie spécifique pour ouvrir un menu volant récapitulatif.

- **Domaines** : répertorie les domaines web qui ont été consultés ou bloqués dans votre organisation. Sélectionnez un domaine spécifique pour afficher des informations détaillées sur ce domaine.

- **Groupes d’appareils** : répertorie tous les groupes d’appareils qui ont généré une activité web dans votre organisation

Utilisez le filtre d’intervalle de temps en haut à gauche de la page pour sélectionner une période. Vous pouvez également filtrer les informations ou personnaliser les colonnes. Sélectionnez une ligne pour ouvrir un volet volant avec encore plus d’informations sur l’élément sélectionné.

### <a name="known-issues-and-limitations"></a>Problèmes connus et conseils

Seul Microsoft Edge est pris en charge si la configuration du système d’exploitation de votre appareil est Server (**cmd** \> **Systeminfo** \> **OS Configuration**). La protection réseau est uniquement prise en charge en mode Inspecter sur les appareils serveur, qui est responsable de la sécurisation du trafic entre les navigateurs tiers pris en charge.

Seul Microsoft Edge est pris en charge et la protection réseau n’est pas prise en charge sur Windows 10 hôtes multisession Azure Virtual Desktop.

La protection réseau ne prend actuellement pas en charge l’inspection SSL, ce qui peut entraîner l’autorisation de certains sites par le filtrage de contenu web qui serait normalement bloqué. Les sites seraient autorisés en raison d’un manque de visibilité du trafic chiffré après l’établissement de l’établissement d’une liaison TLS et d’une incapacité à analyser certaines redirections.  Cela inclut les redirections de certaines pages de connexion de messagerie web vers la page de boîte aux lettres. Comme solution de contournement acceptée, vous pouvez créer un indicateur de bloc personnalisé pour la page de connexion afin de vous assurer qu’aucun utilisateur n’est en mesure d’accéder au site. Gardez à l’esprit que cela peut bloquer leur accès à d’autres services associés au même site web. 

Si vous utilisez Microsoft 365 Business Premium ou Microsoft Defender pour entreprises, vous pouvez définir une stratégie de filtrage de contenu web pour votre environnement. Cette stratégie s’applique par défaut à tous les utilisateurs.

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble de la protection web](web-protection-overview.md)
- [Protection contre les menaces web](web-threat-protection.md)
- [Surveiller la sécurité web](web-protection-monitoring.md)
- [Répondre aux menaces web](web-protection-response.md)
- [Configuration requise pour la protection réseau](web-content-filtering.md)
