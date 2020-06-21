---
title: Planifier la gouvernance de groupes
ms.reviewer: johasand
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- BSA160
description: Découvrez comment planifier la gouvernance de groupes Microsoft 365.
ms.openlocfilehash: 37d243b56de363985ecb9463dfe5eb182d9e40b1
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780492"
---
# <a name="plan-for-governance-in-groups"></a>Planifier la gouvernance dans les groupes

Les groupes Microsoft 365 disposent d’un ensemble complet d’outils permettant d’implémenter les fonctionnalités de gouvernance dont votre organisation peut avoir besoin. Cet article guide les professionnels de l’informatique pour poser les bonnes questions afin de déterminer leurs besoins en matière de gouvernance et comment les répondre en fonction de leur profil organisationnel.

## <a name="why-microsoft-365-groups"></a>Pourquoi les groupes Microsoft 365 ?
![Description de l’image](../../media/01.png)

Nous connaissons que les organisations utilisent aujourd’hui un ensemble d’outils varié. Il existe une équipe de développeurs qui utilisent la conversation d’équipe, les cadres qui envoient du courrier électronique et l’ensemble de l’organisation qui se connecte via le réseau social de l’entreprise. Plusieurs outils de collaboration sont en cours d’utilisation, car chaque groupe est unique et possède ses propres besoins fonctionnels et sa propre pratique. Certains utiliseront uniquement le courrier électronique, tandis que d’autres seront principalement en conversation. 

Si les utilisateurs dispensent que les outils fournis par le service informatique ne répondent pas à leurs besoins, ils téléchargeront probablement leur application de consommateur favorite qui prend en charge leurs scénarios. Bien que ce processus permette aux utilisateurs de commencer rapidement, il se traduit par une expérience utilisateur frustrante au sein de l’organisation avec plusieurs connexions, des difficultés de partage et des emplacements uniques pour afficher du contenu. Ce concept est appelé « détourage » et représente un risque significatif pour les organisations. Elle réduit la possibilité de gérer uniformément l’accès utilisateur, de garantir la sécurité et les besoins en matière de conformité des services.

Les groupes Microsoft 365 autorisent les utilisateurs et réduisent le risque de clichés instantanés en fournissant une seule étape des outils nécessaires à la collaboration. Les groupes Microsoft 365 vous permettent de choisir un ensemble de personnes avec lesquelles vous souhaitez collaborer, et de configurer facilement une collection de ressources à partager pour ces personnes. L’attribution manuelle d’autorisations à des ressources est un élément du passé au-delà duquel l’ajout de membres au groupe accorde automatiquement les autorisations nécessaires à tous les biens fournis par le groupe.

## <a name="technical-architecture"></a>Architecture technique

Il existe trois méthodes de communication principales prises en charge par les groupes Microsoft 365. Il est possible de créer des groupes au sein de ces expériences et de les utiliser dans Microsoft 365 :
- Outlook : collaboration par courrier électronique avec une boîte aux lettres et un calendrier de groupe partagé
- Microsoft teams : un espace de travail de conversation permanente dans lequel vous pouvez avoir des conversations informelles, en temps réel, autour de plusieurs sujets, organisés par sous-groupes spécifiques
- Yammer : expérience sociale d’entreprise pour la collaboration

> [!NOTE]
> La création d’un groupe via d’autres applications d’équipe, telles que SharePoint, Planner ou Stream-, crée un groupe avec une boîte de réception Outlook et la possibilité de se connecter à Microsoft Teams.

En fonction de l’emplacement de création d’un groupe, certaines ressources sont configurées automatiquement, telles que :
- [Boîte de réception](https://support.microsoft.com/office/a0482e24-a769-4e39-a5ba-a7c56e828b22) -pour les conversations par courrier électronique entre les membres du groupe. Cette boîte de réception dispose d’une adresse de messagerie et peut être configurée pour accepter les messages provenant de personnes extérieures au groupe et même en dehors de votre organisation, comme une liste de distribution traditionnelle.
 - [Calendrier](https://support.microsoft.com/office/0cf1ad68-1034-4306-b367-d75e9818376a) : pour la planification des événements associés au groupe.
- [Site d’équipe SharePoint](https://support.microsoft.com/office/75545757-36c3-46a7-beed-0aaa74f0401e) : référentiel central d’informations, de liens et de contenu concernant votre groupe
- [Bibliothèque de documents SharePoint](https://support.microsoft.com/office/749bc73b-90c9-4760-9b6f-9aa1cf01b403) : emplacement central pour le groupe où stocker et partager des fichiers
- [Bloc-notes OneNote](https://support.microsoft.com/office/e768fafa-8f9b-4eac-8600-65aa10b2fe97) : pour rassembler des idées, des recherches et des informations
- [Planificateur](https://support.microsoft.com/office/4a9a13c6-3adf-4a60-a6fc-15c0b15e16fc) : pour l’affectation et la gestion des tâches de projet entre les membres de votre groupe
- [Groupe Yammer](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2) : un emplacement commun pour les conversations et les informations de partage
- Microsoft teams : un espace de travail de conversation dans Microsoft 365

Pour en savoir plus sur les ressources créées pour chaque groupe, consultez la [rubrique en savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2).

> [!NOTE]
> Lorsqu’un nouveau groupe Microsoft 365 est créé via Yammer ou Teams, le groupe n’est pas visible dans Outlook ou dans le carnet d’adresses, car la communication principale entre ces utilisateurs se produit dans leurs clients respectifs. Les groupes Yammer ne peuvent pas être connectés à Microsoft Teams.

## <a name="where-to-start-a-conversation"></a>Où démarrer une conversation
Il existe plusieurs emplacements de conversation dans Microsoft 365. La compréhension de l’emplacement de démarrage d’une conversation peut aider les organisations à définir une stratégie de communication.

![Description de l’image](../../media/03.png)

- Équipes : espace de travail de conversation (collaboration à haute vitesse) – boucle interne
   - Conçu pour la collaboration avec les personnes avec lesquelles vous travaillez tous les jours
  - Met des informations à portée de main sur les utilisateurs en une seule expérience
  - Ajouter des onglets, des connecteurs et des bots
  - Conversation en direct, conférence audio/vidéo, réunions enregistrées

- Yammer : se connecter à l’échelle de l’organisation (entreprise social) – boucle externe
  - Communautés de personnes : groupes interfonctionnels de personnes qui partagent un intérêt ou une expertise commune, mais qui ne travaillent pas nécessairement ensemble sur une base quotidienne
  - Connexion de leadership, formation de communautés, communautés basées sur des rôles

- Groupes Outlook : DL moderne (collaboration par messagerie électronique)
  - Omniprésent pour la communication ciblée
  - Mettre à niveau les listes de distribution vers les groupes Microsoft 365 : [Pourquoi devez-vous effectuer une mise à niveau ?](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)

- SharePoint : expérience de collaboration de contenu de base pour tous les groupes Microsoft 365
  - Chaque groupe obtient un site d’équipe SharePoint connecté.
  - Partager du contenu, créer des pages personnalisées et créer des actualités
  - [Connexion](https://docs.microsoft.com/sharepoint/dev/features/groupify/groupify-overview) de sites d’équipe SharePoint existants à de nouveaux groupes Microsoft 365

##  <a name="managing-and-governing-microsoft-365-at-scale"></a>Gestion et administration de Microsoft 365 à l’envergure

Les groupes Microsoft 365 disposent d’un ensemble complet d’outils permettant d’implémenter les fonctionnalités de gouvernance dont votre organisation peut avoir besoin. La section suivante décrit les fonctionnalités, recommande les meilleures pratiques et fournit des instructions pour poser les bonnes questions afin de déterminer les exigences de gouvernance et comment les répondre.

**Dans cette section**:
- [Contrôler qui peut créer des groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#control-who-can-create-office-365-groups)
- [Regrouper la suppression et la restauration logicielles](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#group-soft-delete-and-restore)
- [Stratégie de noms de groupes](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#group-naming-policy)
- [Stratégie d’expiration de groupe](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#group-expiration-policy)
- [Accès invité de groupe](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#group-guest-access)
- [Stratégies de groupe & protection des informations](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#group-policies--information-protection)
- [Mettre à niveau les outils de collaboration traditionnels](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#upgrade-traditional-collaboration-tools)
- [Création de rapports de groupes](https://docs.microsoft.com/office365/admin/create-groups/plan-for-groups-governance#groups-reporting)

### <a name="control-who-can-create-microsoft-365-groups"></a><a name="control-who-can-create-office-365-groups"></a>Contrôler qui peut créer des groupes Microsoft 365
Les utilisateurs finaux peuvent créer des groupes à partir de plusieurs points de terminaison, dont Outlook, SharePoint, teams et d’autres environnements.

![Description de l’image](../../media/04.png)
> [!Tip]
>- Envisagez d’utiliser en libre-service les propriétaires de groupe.
>- Documentez et communiquez comment demander un groupe.
>- Reportez-vous aux personnes qui peuvent créer des groupes lors de votre parcours sur le Cloud.
>- Envisagez d’utiliser l’appartenance dynamique pour configurer les membres du groupe de sécurité afin de contrôler la création de groupes.
>- Évaluez les groupes de scénarios pouvant être gérés via une appartenance dynamique et autorisez le reste.

Il existe trois modèles principaux de mise en service dans les groupes : Open, del et contrôlée. Le tableau suivant décrit les avantages de chaque modèle.

| Modèle          | Avantages                                                   |
| -------------- | ------------------------------------------------------------ |
| Open (par défaut) | Les utilisateurs peuvent créer leurs propres groupes en fonction de leurs besoins, sans avoir à patienter ou à vous en déranger. |
| A-del         | Les utilisateurs demandent un groupe à ce groupe. ELLE peut vous aider à sélectionner les meilleurs outils de collaboration pour leurs besoins. |
| Télécommandé     | Création de groupe restreinte à des personnes, des équipes ou des services spécifiques. Pour plus d’informations, consultez la rubrique [gérer les personnes autorisées à créer des groupes Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/create-groups/manage-creation-of-groups). |

Votre organisation peut avoir des exigences spécifiques pour implémenter des contrôles stricts sur les personnes autorisées à créer des groupes. Utilisez le tableau suivant pour prendre la décision concernant le modèle de mise en service adapté à votre organisation.

|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Quel modèle de mise en service répond aux besoins de votre organisation ?</li><li>Votre organisation a-t-elle besoin de limiter la création de groupes aux administrateurs ?</li><li>Votre organisation a-t-elle besoin de limiter la création de groupe aux membres du groupe de sécurité ?</li><li>Votre organisation a-t-elle besoin de créer des groupes de manière dynamique en fonction des attributs des utilisateurs, tels que service ?</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Documentez les besoins de votre organisation en matière de création de groupes et d’équipes.</li><li>Planifiez la mise en œuvre de ces exigences dans le cadre de votre déploiement de groupes.</li><li>Communiquer et publier vos stratégies pour informer les utilisateurs du comportement attendu</li><li>Planifier l’implémentation de l’appartenance dynamique, le cas échéant.</li></ul>|

> [!Important]
> La limitation de la création de groupes et d’équipes peut ralentir la productivité des utilisateurs, car de nombreux services Microsoft 365 nécessitent la création de groupes pour que le service fonctionne. Pour en savoir plus, consultez la rubrique [Pourquoi contrôler qui crée des groupes Microsoft 365 ?](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups?view=o365-worldwide%23why-control-who-creates-office-365-groups)

#### <a name="resources"></a>*Resources*
- [Gérer les personnes autorisées à créer des groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/manage-creation-of-groups?view=o365-worldwide)
- [Remplir des groupes de façon dynamique en fonction des attributs d’objets](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-groups-with-advanced-rules)
- [Comment faire pour modifier le paramètre par défaut des groupes Microsoft 365 pour Outlook, public ou privé](https://support.microsoft.com/office/36236e39-26d3-420b-b0ac-8072d2d2bedc)
- [Synchronisation des groupes de sécurité avec l’appartenance à une équipe](https://techcommunity.microsoft.com/t5/Microsoft-Teams-Blog/Syncing-Security-Groups-with-team-membership/ba-p/241959)

### <a name="group-soft-delete-and-restore"></a><a name="group-soft-delete-and-restore"></a>Regrouper la suppression et la restauration logicielles
Si vous avez supprimé un groupe Microsoft 365, par défaut, il est conservé pendant 30 jours. Cette période de 30 jours est appelée « suppression réversible », car vous avez encore la possibilité de le restaurer. Après cette période de 30 jours, le groupe et le contenu associé sont supprimés de manière définitive et ne peuvent plus être restaurés.

> [!Tip]
>- Communiquez le processus de restauration à vos utilisateurs.
>- Former votre équipe de support technique.
>- Effectuer le suivi des groupes à venir qui seront supprimés à l’aide du script PowerShell.

|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Avez-vous besoin que certains biens soient archivés pour le stockage à long terme ?</li><li>Existe-t-il des exigences en matière de rétention pour votre organisation ?</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Communiquer et publier les stratégies de suppression et de restauration pour informer les utilisateurs du comportement attendu </li><li> Consignez les besoins de votre organisation en matière de surveillance des groupes supprimés.</li><li>Prévoyez d’implémenter ces exigences dans le cadre de votre déploiement de groupes.</li></ul>|

> [!Important]
>During the "soft-delete" period if a user tries to access the site they will get a 403 forbidden message. After this period if the user tries to access the site they will get a 404 not found message.

#### <a name="resources"></a>*Resources*
- [Restaurer un groupe Microsoft 365 supprimé](https://docs.microsoft.com/microsoft-365/admin/create-groups/restore-deleted-group?ui=en-US&rs=en-001&ad=US)
- [Restaurer un groupe Microsoft 365 supprimé dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-restore-deleted)
- [Supprimer des groupes à l'aide de l'applet de commande Remove-UnifiedGroup](https://technet.microsoft.com/library/mt238270%28v=exchg.160%29.aspx)

### <a name="group-naming-policy"></a><a name="group-naming-policy"></a>Stratégie de noms de groupes
Une stratégie de noms peut vous aider, ainsi que vos utilisateurs, à identifier la fonction du groupe, de l’appartenance, de la région géographique ou de la personne qui a créé le groupe. La stratégie d’attribution de noms peut également aider à catégoriser les groupes dans le carnet d’adresses. Vous pouvez utiliser la stratégie pour empêcher l’utilisation de mots spécifiques dans les alias et les noms de groupes.

> [!Tip]
> - Utiliser des chaînes courtes comme suffixe.
> - Utilisez des attributs avec des valeurs.
> - Ne soyez pas trop créatif, la longueur totale du nom est de 264 caractères au maximum.
> - Charger les mots bloqués spécifiques de votre organisation pour restreindre l’utilisation.


|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Votre organisation a-t-elle besoin d’une convention d’affectation de noms spécifique pour les groupes ?</li><li>Votre organisation a-t-elle besoin de la Convention d’affectation de noms pour toutes les charges de travail ?</li><li>Votre organisation a-t-elle des mots spécifiques que vous souhaitez empêcher les utilisateurs d’utiliser ?</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Consignez les conditions requises de votre organisation pour les groupes d’affectation de noms. </li><li> Prévoyez d’implémenter ces exigences dans le cadre de votre déploiement de groupes.</li><li> Communiquez et publiez les stratégies et les normes d’appellation pour informer les utilisateurs.</li></ul>|

> [!Important]
>La stratégie de noms est appliquée aux groupes qui sont créés dans toutes les charges de travail de groupe (comme Outlook, Microsoft Teams, SharePoint, Planner, Yammer, etc.). Elle est appliquée à la fois au nom de groupe et à l’alias de groupe. Elle est appliquée lorsqu’un utilisateur crée un groupe et lorsque le nom ou l’alias du groupe est modifié pour un groupe existant.

#### <a name="resources"></a>*Resources*
- [Stratégie de noms de groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/groups-naming-policy)
- [Appliquer une stratégie d’attribution de noms pour les groupes Microsoft 365 dans Azure Active Directory](https://go.microsoft.com/fwlink/?linkid=868340)
- [Cmdlets Azure Active Directory pour la configuration de paramètres de groupe](https://go.microsoft.com/fwlink/?linkid=868341)
- [Fonctionnalités d’aperçu pour les noms de groupes](https://portal.azure.com/#blade/Microsoft_AAD_IAM/GroupsManagementMenuBlade/NamingPolicy)

### <a name="group-expiration-policy"></a><a name="group-expiration-policy"></a>Stratégie d’expiration de groupe
Les administrateurs peuvent spécifier une période d’expiration et n’importe quel groupe qui atteint la fin de cette période, et n’est pas renouvelé. La période d’expiration commence lorsque le groupe est créé, ou à la date à laquelle il a été renouvelé pour la dernière fois. Les propriétaires de groupe reçoivent automatiquement un courrier électronique avant l’expiration qui leur permet de renouveler le groupe pour un autre intervalle d’expiration. Les groupes actifs se renouvellent automatiquement.

Une fois que vous avez défini un groupe pour qu’il expire :
- Les propriétaires du groupe sont avertis de renouveler le groupe à mesure que l’expiration s’approche
- Tout groupe qui n’est pas renouvelé est supprimé.
- Tout groupe supprimé peut être restauré dans les 30 jours par les propriétaires du groupe ou l’administrateur

> [!Tip]
> - Au début du projet pilote des groupes spécifiques.
> - Choisissez groupes inactifs en fonction du rapport d’activité dans le centre d’administration Microsoft 365.
> - Communiquez le processus de renouvellement aux propriétaires de groupe.
> - Intégration de votre équipe de support technique.
> - Vérifiez que les groupes ont plusieurs propriétaires et configurez la messagerie pour les groupes orphelins.


|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Votre organisation souhaite-t-elle spécifier une date d’expiration pour les équipes ?</li><li>Déterminez la stratégie de traitement des groupes orphelins.</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Consignez les exigences de votre organisation concernant l’expiration, la rétention des données et l’archivage des groupes.</li><li>Prévoyez d’implémenter ces exigences dans le cadre de votre déploiement de groupes.</li><li>Planifier l’implémentation d’un travail personnalisé à des rapports sur des groupes qui ont des propriétaires uniques ou qui sont propriétaires. </li></ul>|

> [!Important]
>Lorsque vous modifiez la stratégie d’expiration, le service recalcule la date d’expiration pour chaque groupe. Il commence toujours à compter à partir de la date de création du groupe, puis applique la nouvelle stratégie d’expiration.

#### <a name="resources"></a>*Resources*
- [Stratégie d’expiration de groupe Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/create-groups/office-365-groups-expiration-policy)
- [Configurer la stratégie d’expiration pour les groupes Microsoft 365](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-lifecycle)

### <a name="group-guest-access"></a><a name="group-guest-access"></a>Accès invité de groupe
Les administrateurs peuvent contrôler s’il faut autoriser l’accès invité aux groupes Microsoft 365 pour l’ensemble de l’organisation ou pour des groupes Microsoft 365 individuels. Ils peuvent également déterminer qui peut autoriser l’ajout d’invités aux groupes.
>[!Tip]
>- Activer l’accès invité au niveau du client. Si nécessaire, bloquez des groupes spécifiques.
>- Déterminez l’utilisation des domaines invités autoriser/bloquer, du rôle d’invité invité, des révisions d’accès, des conditions d’utilisation.
>- Suivre l’activité des utilisateurs invités via des journaux d’audit.

|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Avez-vous besoin de limiter la possibilité d’ajouter des invités à teams par groupe ?</li><li> Votre organisation a-t-elle besoin de présenter des clauses d’exclusion de responsabilité pertinentes pour les besoins légaux ou de conformité ?</li><li>Votre organisation a-t-elle besoin de réduire la charge administrative de l’ajout et de la suppression d’utilisateurs ?</li><li>Votre organisation prévoit-elle des contrôles d’audit pour l’accès invité/externe ?</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Documentez les conditions requises pour l’accès invité/externe pour certains groupes classifiés, y compris la période de rétention et l’occurrence.</li><li>Les exigences de l’organisation de documents pour lesquelles les groupes doivent utiliser les conditions d’utilisation et la révision d’accès. </li><li>Effectuer des révisions pour gérer efficacement les appartenances aux groupes pour les utilisateurs internes et invités.</li></ul>|


#### <a name="resources"></a>*Resources*
- [Collaboration avec des personnes extérieures à votre organisation](https://docs.microsoft.com/microsoft-365/solutions/collaborate-with-people-outside-your-organization)
- [Gérer l’accès invité dans les groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/manage-guest-access-in-groups)
- [Accès invité dans les groupes Microsoft 365](https://support.microsoft.com/office/bfc7a840-868f-4fd6-a390-f347bf51aff6)
- [Access reviews Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-perform-access-review)
- [Conditions d’utilisation d’Azure Active Directory](https://docs.microsoft.com/azure/active-directory/active-directory-tou)
- [Google Federation](https://docs.microsoft.com/azure/active-directory/b2b/google-federation)

### <a name="group-policies--information-protection"></a><a name="group-policies--information-protection"></a>Stratégies de groupe & protection des informations
Les groupes Microsoft 365 sont basés sur les fonctionnalités avancées de sécurité et de conformité de Microsoft 365 et prennent en charge les classifications, l’audit et la création de rapports, la recherche de contenu de conformité, la découverte électronique, la conservation légale et les stratégies de rétention.
>[!Tip]
>- Configurez la classification, les instructions d’utilisation et les étiquettes alignées sur les besoins de votre organisation.
>- Les stratégies de rétention peuvent être définies indépendamment des étiquettes.
>- Activités de groupes d’audit : création, suppression, etc.
>- Gérer la confidentialité de groupe et l’accès invité en fonction de la classification.

|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Votre organisation a-t-elle des exigences d’utilisation spécifiques qui doivent être communiquées à tous les utilisateurs ?</li><li>Votre organisation a-t-elle besoin des classifications de tout le contenu ?</li><li>Votre organisation nécessite-t-elle la conservation du contenu pendant une période de temps spécifique ?</li><li>Votre organisation a-t-elle besoin d’appliquer des stratégies de rétention de données spécifiques à des groupes ?</li><li>Votre organisation a-t-elle besoin d’avoir la possibilité d’archiver des groupes inactifs pour conserver le contenu ?</li><li>Les créateurs de groupe doivent-ils pouvoir attribuer des classifications spécifiques de l’organisation à teams ?</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Documenter les instructions d’utilisation de votre organisation pour les groupes</li><li>Consignez les exigences de votre organisation en matière de classification.</li><li>Déterminez les stratégies à appliquer en fonction de la classification, par exemple, la sensibilité, la rétention et l’accès invité.</li><li>Définissez les étiquettes de confidentialité de votre organisation et les paramètres de protection que vous souhaitez associer.</li><li>Définir une stratégie d’étiquette pour contrôler les utilisateurs et les groupes qui voient ces étiquettes.</li><li>Configurez l' [étiquette de sensibilité des groupes](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels-teams-groups-sites) et commencez à classer les groupes dans votre organisation.</li><li>Planifiez la mise en œuvre de ces exigences dans le cadre de votre déploiement de groupes.</li></ul>|


#### <a name="resources"></a>*Resources*
- [Lien vers les instructions d’utilisation de vos groupes Microsoft 365](https://docs.microsoft.com/office365/enterprise/manage-office-365-groups-with-powershell#link-to-your-office-365-groups-usage-guidelines)
- [Créer des classifications pour les groupes Office dans votre organisation](https://docs.microsoft.com/office365/enterprise/manage-office-365-groups-with-powershell#create-classifications-for-office-groups-in-your-organization)
- [Configurer les paramètres de groupe](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-groups-settings-cmdlets)
- [Vue d’ensemble des stratégies de rétention](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)
- [Vue d’ensemble des étiquettes de confidentialité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels)
- [Vue d’ensemble des étiquettes](https://docs.microsoft.com/microsoft-365/compliance/labels)
- [Rechercher le journal d’audit](https://docs.microsoft.com/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance)
- [Création ou suppression d’une conservation légale inaltérable](https://docs.microsoft.com/exchange/security-and-compliance/create-or-remove-in-place-holds)
- [Créer une stratégie de conservation](https://docs.microsoft.com/microsoft-365/compliance/retention-policies)
- [Exécuter une recherche de contenu dans le centre de sécurité & conformité](https://docs.microsoft.com/microsoft-365/compliance/content-search)
- [Création et publication en bloc d’étiquettes de rétention à l’aide de PowerShell](https://docs.microsoft.com/microsoft-365/compliance/bulk-create-publish-labels-using-powershell)

### <a name="upgrade-traditional-collaboration-tools"></a><a name="upgrade-traditional-collaboration-tools"></a>Mettre à niveau les outils de collaboration traditionnels
Pour les années, les organisations s’appuyaient sur les groupes de distribution pour communiquer et collaborer avec des groupes de personnes à la fois à l’intérieur et à l’extérieur de l’entreprise. À présent, toutefois, les groupes Microsoft 365 dans Outlook offrent une solution plus puissante pour la collaboration. En outre, la possibilité de connecter un groupe Microsoft 365 à un site SharePoint existant est importante si vous souhaitez moderniser ce site.

>[!Tip]
>- Mettre à niveau facilement toutes vos listes de distribution éligibles, en quelques secondes, via le centre d’administration Exchange ou à l’aide d’applets de commande PowerShell.
>- Connecter des sites d’équipe SharePoint existants à de nouveaux groupes Microsoft 365.

|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Votre organisation a-t-elle des listes de distribution qui [ne sont pas éligibles](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists#how-do-i-check-which-dls-are-eligible-for-upgrade) pour la mise à niveau ?<li>Déterminez quel type de groupe est la liste de distribution la mieux migrée vers.</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Identifiez les listes de distribution qui seront candidates pour la mise à niveau vers les groupes Microsoft 365.</li><li>Analysez vos sites d’équipe SharePoint existants pour voir quels sites sont prêts à être connectés en groupe.</li><li>Informez les autres équipes de votre entreprise que vous avez mis à niveau votre groupe de distribution et les étapes que vous avez prises pour le réussir.</li></ul>|


#### <a name="resources"></a>*Resources*
- [Mettre à niveau les listes de distribution (DL) vers des groupes dans Outlook](https://aka.ms/whyupgradedls)
- Mise à niveau d’un seul clic via le centre d’administration Exchange ou via des [scripts PowerShell](https://docs.microsoft.com/microsoft-365/admin/manage/upgrade-distribution-lists)
- [Migrer des listes de distribution vers des groupes Microsoft 365-aide de l’administrateur](https://docs.microsoft.com/office365/admin/manage/upgrade-distribution-lists)
- [Connecter des sites SharePoint existants à des groupes Microsoft 365 :](https://docs.microsoft.com/sharepoint/dev/transform/modernize-connect-to-office365-group)
- [Étude et utilisation des données de l’analyseur](https://docs.microsoft.com/sharepoint/dev/transform/modernize-connect-to-office365-group-scanner)
- [Scanneur de modernisation SharePoint](https://github.com/SharePoint/sp-dev-modernization/tree/master/Tools/SharePoint.Modernization) (outil situé sur GitHub)

### <a name="groups-reporting"></a><a name="groups-reporting"></a>Création de rapports de groupes
Le tableau de bord rapports Microsoft 365 affiche une vue d’ensemble de l’activité sur les produits Microsoft de votre organisation. Il vous permet d'explorer les rapports au niveau de chaque produit afin d'offrir des informations plus précises sur les activités pour chaque produit.
> [!TIP]
>- Vous pouvez utiliser les rapports regroupements pour obtenir des informations sur l’activité des groupes Microsoft 365 dans votre organisation et connaître le nombre de groupes créés et utilisés.
>-Le rapport des groupes Microsoft 365 peut être consulté pour connaître les tendances des 7, 30, 90 ou 180 derniers jours.
>- Surveiller l’activité des groupes dans les conversations de boîte aux lettres de groupe, activité des sites de groupes et des fichiers, détails concernant l’appartenance au groupe, y compris les comptes des membres externes
>- Surveillez régulièrement pour contacter les propriétaires de groupe des groupes actifs afin de découvrir les cas d’utilisation et de les amplifier en interne.
>- Tirez parti des packs de contenu Power BI pour obtenir des informations supplémentaires.


|         |         |         |
|---------|---------|---------|
|![Description de l’image](../../media/decision_point.png)|Points de décision|<ul><li>Votre organisation a-t-elle besoin de rapports réguliers pour comprendre l’utilisation des groupes Microsoft 365 ?<li>Votre organisation a-t-elle besoin de rapports sur tous les groupes qui ont des membres externes ?</li></ul>|
|![Description de l’image](../../media/next_steps.png)|Étapes suivantes|<ul><li>Documentez les conditions requises de votre organisation pour examiner régulièrement les rapports d’activité des groupes.</li></ul>|


#### <a name="resources"></a>*Resources*
- [Rapports Microsoft 365 dans le centre d'administration](https://docs.microsoft.com/microsoft-365/admin/activity-reports/office-365-groups)
- [Pack de contenu adoption d’Office 365](https://docs.microsoft.com/microsoft-365/admin/usage-analytics/usage-analytics)
- [Pack de contenu Azure AD](https://docs.microsoft.com/azure/active-directory/active-directory-reporting-power-bi-content-pack-how-to)
- [API d’activité des groupes Microsoft Graph](https://developer.microsoft.com/graph/docs/api-reference/v1.0/resources/office_365_groups_activity_reports)
- [Rapport de groupes Microsoft 365 (groupes unifiés)](https://gallery.technet.microsoft.com/office/Office-365-Groups-Report-7e3e161b)
- [Rapports d’activité d’audit dans le portail Azure Active Directory](https://docs.microsoft.com/azure/active-directory/reports-monitoring/concept-audit-logs)
- [Microsoft Graph-utiliser la requête Delta pour effectuer le suivi des modifications](https://docs.microsoft.com/graph/delta-query-overview)

## <a name="getting-started-based-on-your-cloud-adoption-journey"></a>Prise en main basée sur le parcours de votre adoption sur le Cloud

Les groupes Microsoft 365 fournissent un ensemble complet de fonctionnalités de gouvernance dont votre organisation peut avoir besoin. Considérez les profils d’organisation suivants comme des conseils pour comprendre les meilleures pratiques, posez-vous les questions appropriées pour déterminer les exigences de gouvernance et comment les répondre.

**Considérez les profils d’organisation suivants :**
- Petite entreprise
- Moyennes entreprises
- Réglementé ou entreprise

### <a name="small-business"></a>Petite entreprise
Imaginez une organisation qui a déployé Microsoft 365 avec au moins des licences Exchange Online et SharePoint Online qui incluent les plans Business Essentials et Business Premium, ainsi que les plans entreprise E1, E3 et E5 sans licence Azure active Director Premium.

| Phase | Description |
| --------------- | ------------------------------------------------------------ |
| Aide |<ul><li>Envisagez un modèle de mise en service en libre service.</li><li> Les groupes dans Outlook & les sites SharePoint sont [privés par défaut](https://techcommunity.microsoft.com/t5/Office-365-Groups/Groups-in-Outlook-and-Group-connected-team-sites-are-now-private/m-p/186395).</li><li> Les groupes peuvent être créés en mettant à niveau des listes de distribution existantes (DL) un-par-un ou en bloc via PowerShell. Consultez la rubrique [mettre à niveau des listes de distribution vers des groupes Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/manage/upgrade-distribution-lists).</li><li> Activez l’accès invité mais en déterminant l’utilisation des domaines invités autoriser/bloquer.</li><li> Utilisez les rapports de groupe pour obtenir des informations sur la façon dont les utilisateurs utilisent des groupes.</li><li> Envisagez de créer une équipe Team teams de l’organisation à l’échelle de l’organisation afin que tous les utilisateurs fassent partie d’une équipe unique pour la collaboration. </li></ul>|
| Étapes suivantes      |<ul><li>Envisagez d’utiliser [des conceptions de site et des scripts de site](https://docs.microsoft.com/sharepoint/dev/declarative-customization/site-design-overview) pour définir la conception par défaut des contrôles à l’aide des actions définies dans la [référence de schéma JSON](https://docs.microsoft.com/sharepoint/dev/declarative-customization/site-design-json-schema).</li><li>Passez en revue les [rapports de groupes](https://docs.microsoft.com/microsoft-365/admin/activity-reports/office-365-groups).</li><li>Suivre le nombre total de groupes et de groupes inactifs/actifs.</li><li>Effectuez le suivi du stockage Exchange et SharePoint utilisé.</li><li>Afficher l’activité des groupes dans les conversations de boîte aux lettres de groupe, l’activité des sites de groupe/fichiers, etc.</li></ul> |

### <a name="medium-sized-business"></a>Moyennes entreprises
Outre les recommandations ci-dessus, considérez les points suivants pour les entreprises de taille moyenne qui ont déployé Microsoft 365 avec au moins une entreprise E3/E5 avec des licences Azure Active Directory Premium P1.

| Phase | Description |
| --------------- | ------------------------------------------------------------ |
| Aide |<ul><li>Déterminez un modèle de mise en service à l’ouverture ou à la décision de l’informatique.</li><li> Envisagez de créer certains groupes liés aux [règles d’appartenance dynamique](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-dynamic-membership) en fonction des attributs Azure ad, comme Department.</li><li> Définir les classifications au sein de votre organisation, par exemple, hautement confidentiel, confidentiel (par défaut), général.</li><li>  Définissez les stratégies en fonction de la classification, telle que la rétention et la sensibilité.</li><li> SharePoint est le service de contenu pour chaque groupe Microsoft 365. Envisagez [de concevoir et de déployer des sites SharePoint Online pour trois niveaux de protection (de](https://docs.microsoft.com/office365/enterprise/deploy-sharepoint-online-sites-for-three-tiers-of-protection) planification, sensibles et hautement confidentiels). Pour plus d’informations sur ces trois niveaux de protection, consultez [Sécuriser des sites et des fichiers SharePoint Online](https://docs.microsoft.com/office365/enterprise/secure-sharepoint-online-sites-and-files).</li><li> Par défaut, les groupes public et privé sont répertoriés dans la liste d’adresses globale. Déterminez les groupes que vous souhaitez voir apparaître dans la liste d’adresses globale créé en dehors de Microsoft Teams.  Utilisez l’applet de commande [Set-UnifiedGroup](https://technet.microsoft.com/library/mt238274(v=exchg.160).aspx) « HiddenFromAddressListsEnabled » ou « HidefromExchangeClients » pour masquer des groupes spécifiques.</li></ul> |
| Étapes suivantes      |<ul><li>Définir les [instructions d’utilisation](https://docs.microsoft.com/azure/active-directory/active-directory-accessmanagement-groups-settings-cmdlets) pour informer vos utilisateurs sur les meilleures pratiques qui permettent de conserver leurs groupes efficaces et de les informer sur les stratégies de contenu internes. Par exemple, comprendre les classifications, les stratégies et les procédures. </li><li>Définir la période de cycle de vie de groupe que les groupes doivent être renouvelés ou seront supprimés-stratégie d’expiration.</li><li>Envisagez de créer les travaux personnalisés suivants pour implémenter des stratégies basées sur les classifications.</li><li>Définir la confidentialité sur privé.</li><li>Désactivez l’appartenance/partage externe. </li><li>Messages électroniques pour avertir les membres du groupe pour les groupes sans [propriétaire](https://support.microsoft.com/office/86bb3db6-8857-45d1-95c8-f6d540e45732).</li><li>Appliquer la stratégie de propriété (propriétaires min. 2).</li><li> Définir des stratégies de rétention pour les groupes en fonction de la classification. </li><li>Vue d’ensemble des stratégies de rétention.</li><li>Utilisation de PowerShell pour identifier les groupes avec une classification et [Set-retentioncompliancepolicy permet](https://docs.microsoft.com/powershell/module/exchange/set-retentioncompliancepolicy?view=exchange-ps).</li><li>Envisagez d’utiliser des conceptions de site et des scripts de site pour définir les contrôles à l’aide des actions définies dans la [référence de schéma JSON](https://docs.microsoft.com/sharepoint/dev/declarative-customization/site-design-json-schema).</li><li>Envisagez [de créer un annuaire de sites simple à l’aide d’une conception de site](https://docs.microsoft.com/sharepoint/dev/declarative-customization/site-design-trigger-flow-tutorial) et de Microsoft Flow. Chaque fois qu’un site est créé à l’aide de cette conception de site, les informations du site sont capturées et inscrites dans une liste. </li></ul>|

### <a name="regulated-or-enterprise"></a>Réglementé ou entreprise
Outre les recommandations ci-dessus, vous devez tenir compte des points suivants pour les services hautement réglementés ou les plus grands, tels que le gouvernement, les services financiers ou les soins de santé qui ont déployé Office 365 avec au moins une entreprise E3/E5 avec des licences Azure Active Directory Premium P1/P2.

| Phase | Description |
| --------------- | ------------------------------------------------------------ |
| Aide |<ul><li> Définir des stratégies de gouvernance des données du site SharePoint associé au groupe en fonction de la classification.</li><li>[Protéger les fichiers SharePoint Online avec des étiquettes et des DLP](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-office-365-labels-and-dlp).</li><li>[Protégez les fichiers SharePoint Online avec Azure information protection](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-azure-information-protection).</li><li> Site de groupe configuré dans la région liée à l’emplacement des données par défaut de l’utilisateur ([multi-géo](https://docs.microsoft.com/office365/enterprise/multi-geo-capabilities-in-onedrive-and-sharepoint-online-in-office-365)).</li><li> Révisions d’appartenance pour les groupes avec des membres externes ([révisions d’accès](https://docs.microsoft.com/azure/active-directory/active-directory-azure-ad-controls-access-reviews-overview)).</li><li>S’assurer que les employés ou invités voient les clauses d’exclusion de responsabilité appropriées pour les besoins légaux ou de conformité avant d’obtenir l’accès. ([conditions d’utilisation](https://docs.microsoft.com/azure/active-directory/governance/active-directory-tou)).</li><li>Identifiez et signalez les groupes Microsoft 365 avec une [classification spécifique qui a également des utilisateurs externes](https://techcommunity.microsoft.com/t5/Office-365-Groups/Sample-Powershell-to-identify-groups-with-HBI-classification-and/m-p/215561).</li><li>Les groupes de clés secrètes dont les appartenances doivent être masquées doivent être créés à l’aide de la cmdlet [New-UnifiedGroup](https://technet.microsoft.com/library/mt219359(v=exchg.160).aspx) (à l’aide du commutateur HiddenGroup-MembershipEnabled) lors de la création de groupes.</li><li>Définissez les [étiquettes de sensibilité](https://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) pour l’organisation afin de [restreindre l’accès au contenu en utilisant le chiffrement](https://docs.microsoft.com/microsoft-365/compliance/encryption-sensitivity-labels) et de publier des groupes Microsoft 365 spécifiques.</li><li>Empêcher le contenu sensible de quitter votre organisation sur les appareils exécutant Windows à l’aide [d’étiquettes de confidentialité avec la protection des informations Windows](https://docs.microsoft.com/windows/security/information-protection/windows-information-protection/how-wip-works-with-labels?branch=vsts17546553). |
| Étapes suivantes      | <ul><li> Utilisez la conception de site et les scripts de site pour définir les [actions](https://developer.microsoft.com/office/blogs/site-scripts-site-designs-summer-2018-update/) par défaut qui se produisent lors de la création d’un nouveau site. Par exemple, [configure External Sharing Setting](https://github.com/SharePoint/sp-dev-site-scripts/tree/master/samples/site-apply-external-sharing-setting) or [Trigger a Microsoft Flow pour appeler une fonction Azure](https://github.com/SharePoint/sp-dev-site-scripts/tree/master/samples/site-azure-function) pour appliquer des configurations non prises en charge en mode natif. </li><li> Documentez les exigences relatives à la [protection des fichiers SharePoint Online avec des étiquettes et des DLP pour les](https://docs.microsoft.com/office365/enterprise/protect-sharepoint-online-files-with-office-365-labels-and-dlp) sites associés aux groupes Microsoft 365.</li><li>Documentez les besoins en matière d’organisation pour [sécuriser les sites et les fichiers SharePoint Online](https://docs.microsoft.com/microsoft-365/security/office-365-security/secure-sharepoint-online-sites-and-files) connectés aux groupes Microsoft 365. </li><li>Documentez les besoins de l’Organisation pour publier des [étiquettes de confidentialité](hhttps://docs.microsoft.com/microsoft-365/compliance/sensitivity-labels) sur des utilisateurs ou des groupes spécifiques afin de protéger le contenu.</li></ul> |

## <a name="groups-management-capability-planning-checklist"></a>Liste de vérification de la planification des capacités de gestion des groupes

Un certain nombre de contrôles liés aux groupes peuvent être administrés via Azure Active Directory. Pour en savoir plus sur la configuration des paramètres de groupe, reportez-vous à [applets de commande Azure Active Directory pour configurer les paramètres de groupe](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-settings-cmdlets).

Utilisez le tableau suivant pour déterminer les fonctionnalités dont vous aurez besoin pour déployer les besoins de votre organisation. Elle vous permettra de déterminer les licences dont vous avez besoin afin de pouvoir planifier à l’avance.

| **Fonctionnalité**      | **Détails**                                    | **Licence Azure AD Premium requise** | **Décision** |
| ------------------- | ---------------------------------------------- | ------------------------------------- | ------------ |
| Stratégie de noms de groupes | Utiliser des mots bloqués personnalisés à l’aide de suffixe-suffixe. | P1                                    |      À déterminer     |
| Classification de groupe | Affecter des classifications à Teams. | P1                                    |   À déterminer        |
| Accès invité de groupe | Autoriser ou empêcher l’ajout d’invités à des groupes. | Non                                    |  À déterminer        |
| Création de groupe | Limitez la création d’équipe aux administrateurs. | Non                                    |   À déterminer        |
| Création de groupe | Limitez la création d’équipe aux membres du groupe de sécurité. | P1                                    |     À déterminer      |
| Instructions relatives à l’utilisation des groupes | Définir un lien les instructions d’utilisation de groupe qui seront visibles sur tous les points de terminaison de création de groupe. | P1                                    |   À déterminer        |
| Appartenance masquée | Masquer les membres du groupe Microsoft 365 des utilisateurs qui ne sont pas membres du groupe | Non                                    |   À déterminer        |
| Stratégie d’expiration | Gérer le cycle de vie des groupes Microsoft 365 en définissant une stratégie d’expiration. | P1                                    |  À déterminer        |
| Rapports d’activité de groupe | Accédez à l’activité des groupes Microsoft 365 dans votre organisation et découvrez le nombre de groupes Microsoft 365 créés et utilisés. | Non                                    |    À déterminer       |
| Stratégie de rétention | Conserver ou supprimer des données pour une période spécifique en définissant des stratégies de rétention pour les groupes Microsoft 365 dans le centre de sécurité & conformité. **Remarque :** Pour utiliser cette fonctionnalité, vous devez disposer des licences d’Office 365 entreprise E3 ou version ultérieure. | Non                                    |    À déterminer       |
| Stratégie de protection contre la perte de données | Identifier les informations sensibles sur les sites connectés à un groupe Microsoft 365 et empêcher le partage accidentel. **Remarque :** Pour utiliser cette fonctionnalité, vous devez disposer des licences d’Office 365 entreprise E3 ou version ultérieure. | Non                                    |     À déterminer      |
| Archivage et restauration | Archivez une équipe lorsqu’elle n’est plus active, mais que vous souhaitez la conserver pour référence ou la réactiver ultérieurement. | Non                                    |   À déterminer        |
| Révisions d’accès | Effectuer des révisions pour gérer efficacement les appartenances aux groupes pour les utilisateurs internes et invités | P2                                    |   À déterminer       |
| Conditions d’utilisation | Méthode simple que les organisations peuvent utiliser pour présenter des informations aux utilisateurs finaux. Cette présentation permet aux utilisateurs de voir les clauses d’exclusion de responsabilité correspondant aux exigences légales ou de conformité. | P1                                    |         À déterminer  |

