---
title: Configurer Teams avec trois niveaux de protection de partage de fichier
f1.keywords: NOCSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: ITPro
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: high
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
- m365solution-securecollab
- m365solution-scenario
ms.custom:
- Ent_Architecture
- seo-marvel-jun2020
ms.assetid: 1d51bd87-17bf-457c-b698-61821de3afa0
recommendations: false
description: Découvrez comment configurer Teams pour améliorer la sécurité du partage de fichiers à l’aide de trois niveaux de protection, en équilibrant la sécurité grâce à la facilité de collaboration.
ms.openlocfilehash: 4d287d342371a8182a4c9de5742d2d45ca01a1c6
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66012470"
---
# <a name="configure-teams-with-three-tiers-of-protection"></a>Configurer Teams avec trois niveaux de protection

Les articles de cette série fournissent des recommandations pour la configuration de Microsoft Teams et de leur sites associés SharePoint pour la protection des fichiers qui équilibre la sécurité et la simplicité de la collaboration.

Cet article définit quatre configurations différentes, en commençant par une équipe publique avec les stratégies de partage les plus ouvertes. Chaque configuration supplémentaire représente une élévation significative de la protection, la possibilité d’accéder et de collaborer sur des ressources étant dès lors réduite à l’ensemble approprié des utilisateurs. 

Les configurations décrites dans cet article respectent les recommandations de Microsoft quant aux trois niveaux de protection des données, des identités et des appareils :

- Protection Base de référence

- protection sensible

- Protection hautement sensible

Pour plus d’informations sur ces niveaux et les fonctionnalités recommandées pour chacun d’eux, consultez [Illustrations de documents sur le cloud Microsoft pour les architectes d’entreprise](./cloud-architecture-models.md)

## <a name="three-tiers-at-a-glance"></a>Trois niveaux en un coup d’œil

Le tableau suivant récapitule les configurations pour chaque niveau. Utilisez ces recommandations comme point de départ et ajustez les configurations pour répondre aux besoins de votre organisation. Il est possible que vous n’ayez pas besoin de chaque niveau.

|&nbsp;|Base de référence (public)|Base de référence (privé)|Sensible|Hautement sensible|
|:-----|:-----|:-----|:-----|:-----|
|Équipe privé ou publique|Public|Private|Private|Private|
|Qui a accès ?|Tous les membres de l’organisation, y compris les utilisateurs B2B.|Uniquement les membres de l’équipe. D’autres personnes peuvent demander l’accès au site associé.|Uniquement les membres de l’équipe.|Uniquement les membres de l’équipe.|
|Canaux privés|Les propriétaires et les membres peuvent créer des canaux privés|Les propriétaires et les membres peuvent créer des canaux privés|Seuls les propriétaires peuvent créer des canaux privés.|Seuls les propriétaires peuvent créer des canaux privés.|
|Canaux partagés|Les propriétaires et les membres peuvent créer des canaux partagés|Les propriétaires et les membres peuvent créer des canaux partagés|Seuls les propriétaires peuvent créer des canaux partagés|Seuls les propriétaires peuvent créer des canaux partagés|
|Accès invité au niveau du site|**Nouveaux invités et invités existants** (par défaut).|**Nouveaux invités et invités existants** (par défaut).|**Invités nouveaux et existants** ou **Uniquement les membres de votre organisation** en fonction des besoins de votre équipe.|**Invités nouveaux et existants** ou **Uniquement les membres de votre organisation** en fonction des besoins de votre équipe.|
|Paramètres de partage de site|**Sélectionnez les propriétaires et membres du site, et les personnes disposant des autorisations de modification peuvent partager des fichiers et des dossiers, mais seuls les propriétaires de site peuvent partager le site**.|**Sélectionnez les propriétaires et membres du site, et les personnes disposant des autorisations de modification peuvent partager des fichiers et des dossiers, mais seuls les propriétaires de site peuvent partager le site**.|**Sélectionnez les propriétaires et membres du site, et les personnes disposant des autorisations de modification peuvent partager des fichiers et des dossiers, mais seuls les propriétaires de site peuvent partager le site**.|**Seuls les propriétaires du site peuvent partager des fichiers, des dossiers et le site**.<br>Demandes d’accès **Désactivées**.|
|Accès à un appareil non géré au niveau du site|**Accès complet à partir des applications de bureau, des applications mobiles et du web** (par défaut).|**Accès complet à partir des applications de bureau, des applications mobiles et du web** (par défaut).|**Autoriser un accès limité, web uniquement**.|**Bloquer l’accès**.|
|Type de lien de partage par défaut|**Uniquement les personnes de votre organisation**|**Uniquement les personnes de votre organisation**|**Personnes spécifiques**|**Utilisateurs ayant un accès existant**|
|Étiquettes de confidentialité|Aucun|Aucun|Étiquette de confidentialité permet de classifier l’équipe et de contrôler l’accès des appareils non gérés.|Étiquette de confidentialité permet de classifier l’équipe et de contrôler l’accès des appareils non gérés. Une étiquette peut également être utilisée sur des fichiers pour chiffrer des fichiers.|

Une variante de l’option très sensible, [Équipes avec isolement de sécurité](secure-teams-security-isolation.md) utilise une étiquette de confidentialité unique pour une équipe, ce qui renforce la sécurité. Vous pouvez utiliser cette étiquette pour chiffrer des fichiers. Seuls les membres de cette équipe pourront les lire.

La protection Base de référence inclut les équipes publiques et privées. Les équipes publiques peuvent être découvertes et sont accessibles par toute personne de l’organisation. Les équipes privées peuvent être détectées et sont accessibles seulement par les membres de l’équipe. Ces deux configurations limitent le partage du site SharePoint associé aux propriétaires d’équipes afin d’aider à la gestion des autorisations.

Les équipes pour une protection sensible et hautement sensible sont des équipes privées dans lesquelles le partage et la demande d’accès pour le site associé sont limités et les étiquettes de confidentialité sont utilisées pour créer des stratégies relatives au partage invité, à l’accès aux appareils et au chiffrement de contenu.

## <a name="sensitivity-labels"></a>Étiquettes de confidentialité

Les niveaux sensitives et hautement sensitives utilisent des étiquettes de confidentialité pour renforcer la sécurisation de l’équipe et de ses fichiers. Pour mettre en œuvre ces niveaux, vous devez activer [les étiquettes de sensibilité pour protéger le contenu dans Microsoft Teams, Office 365 Groups et les sites SharePoint](../compliance/sensitivity-labels-teams-groups-sites.md).

Bien que le niveau de ligne de base ne nécessite aucune étiquette de confidentialité, vous pouvez créer une étiquette « général » et exiger que toutes les équipes soient étiquetées. Cela permettra de s'assurer que les utilisateurs font un choix conscient en matière de sensibilité lorsqu'ils créent une équipe. Si vous prévoyez de déployer les niveaux sensibles ou hautement sensibles, nous vous recommandons de créer une étiquette « général » que vous pouvez utiliser pour les équipes de référence et pour les fichiers qui ne sont pas sensibles.

Si vous êtes novice dans l'utilisation des étiquettes de confidentialité, nous vous recommandons de lire l’article [Prise en main des étiquettes de confidentialité](../compliance/get-started-with-sensitivity-labels.md) pour commencer. 

Si vous avez déjà déployé des étiquettes de confidentialité au sein de votre organisation, réfléchissez à la façon dont les étiquettes utilisées dans les niveaux sensibles et hautement sensibles s’adaptent à votre stratégie d’étiquette globale. 

## <a name="sharing-the-sharepoint-site"></a>Partage du site SharePoint

Chaque équipe a un site SharePoint associé dans lequel les documents sont stockés. (Il s’agit de l’onglet **Fichiers** dans un canal d’équipe). Le site SharePoint conserve sa propre gestion des autorisations, mais il est lié aux autorisations d’équipe. Les propriétaires d’équipe sont inclus comme propriétaires de site et les membres d’équipe sont inclus en tant que membres du site sur le site associé.

Les autorisations obtenues permettent :

- Aux propriétaires d’équipe de gérer le site et de disposer d’un contrôle total sur son contenu.
- Aux membres d’une équipe de créer et modifier des fichiers sur le site. 

Par défaut, les propriétaires et les membres de l'équipe peuvent partager le site lui-même avec les personnes extérieures à l’équipe, sans les ajouter réellement à l’équipe. Nous vous recommandons de le faire, car cela complique la gestion des utilisateurs et peut entraîner des personnes qui ne sont pas des membres de l’équipe ayant accès à des fichiers d’équipe qui ne sont pas en mesure de les regrouper. Pour éviter cela, à partir du niveau de la ligne de base de la protection, nous recommandons aux seuls propriétaires de partager le site directement.

Les équipes n’ont pas d’option d’autorisation en lecture seule, le site SharePoint. Si vous avez des participants à des groupes de partenaires qui doivent pouvoir afficher les fichiers d’équipe, mais pas les modifier, songez à les ajouter directement au site SharePoint avec des autorisations de lecture.

## <a name="sharing-files-and-folders"></a>Partager des fichiers et des dossiers

Par défaut, les propriétaires et les membres de l’équipe peuvent partager des fichiers et des dossiers avec des personnes externes à l’équipe. Cela peut inclure des personnes extérieures à votre organisation, si vous avez autorisé le partage d’invités. Dans les trois niveaux, nous mettons à jour le type de lien de partage par défaut afin d'éviter les surpartages accidentels. Dans le niveau hautement sensible, nous limitons ce partage uniquement aux propriétaires d’équipe.

## <a name="sharing-with-people-outside-your-organization"></a>Partage avec des personnes extérieures à votre organisation

Si vous devez partager le contenu de Teams avec des personnes extérieures à votre organisation, deux options s'offrent à vous :

- **Partage d'invité** - Le partage d'invité utilise la collaboration Azure AD B2B qui permet aux utilisateurs de partager des fichiers, des dossiers, des sites, des groupes et des équipes avec des personnes extérieures à votre organisation. Ces personnes accèdent aux ressources partagées en utilisant des comptes invités dans votre répertoire.
- **Canaux partagés** - Les canaux partagés utilisent la connexion directe Azure AD B2B qui permet aux utilisateurs de partager des ressources dans votre organisation avec des personnes d'autres organisations Azure AD. Ces personnes accèdent aux canaux partagés dans Teams à l’aide de leur propre compte professionnel ou scolaire. Aucun compte invité n’est créé dans votre organisation.

Le partage invité et les canaux partagés sont utiles en fonction de la situation. Voir [Planifier la collaboration externe](plan-external-collaboration.md) pour plus d’informations sur chacun d’eux et sur la façon de choisir les scénarios à utiliser pour un scénario donné.

Si vous prévoyez d'utiliser le partage entre invités, nous vous recommandons de configurer [l'intégration de SharePoint et de OneDrive avec Azure AD B2B](/sharepoint/sharepoint-azureb2b-integration-preview) pour une expérience de partage et d'administration optimale.

Le partage d’invités Teams est activé par défaut, mais vous pouvez le désactiver si nécessaire dans les niveaux sensibles et hautement sensibles à l’aide d’une étiquette de confidentialité. Les canaux partagés sont activés par défaut, mais nécessitent la mise en place de relations inter-organisationnelles pour chaque organisation avec laquelle vous souhaitez collaborer. Voir [Collaborer avec des participants externes dans un canal](collaborate-teams-direct-connect.md) pour plus de détails.

Dans le niveau hautement sensible, nous configurons l’étiquette de confidentialité pour chiffrer les fichiers auxquels elle est appliquée. Si vous voulez que les invités aient accès à ces fichiers, vous devez leur attribuer des autorisations lors de la création de l’étiquette. Les participants externes aux canaux partagés ne peuvent pas recevoir d'autorisations pour les étiquettes de sensibilité et ne peuvent pas accéder au contenu crypté par une étiquette de sensibilité.

Nous vous recommandons vivement de laisser le partage des invités activé pour le niveau de référence et pour les niveaux sensibles ou hautement sensibles si vous avez besoin de collaborer avec des personnes extérieures à votre organisation. Les fonctionnalités de partage d’invités de Microsoft 365 fournissent une expérience de partage bien plus sécurisée et régie que l’envoi de fichiers sous forme de pièces jointes dans des messages électroniques. Elle réduit également le risque d'informatique parallèle lorsque les utilisateurs utilisent des produits de consommation non réglementés pour les partager avec des collaborateurs externes légitimes.

Si vous collaborez régulièrement avec d’autres organisations qui utilisent Azure AD, les canaux partagés peuvent être une bonne option. Les canaux partagés apparaissent de manière transparente dans le client Teams de l'autre organisation et permettent aux participants externes d'utiliser leur compte utilisateur habituel pour leur organisation plutôt que de devoir se connecter séparément en utilisant un compte invité.

Reportez-vous aux références suivantes pour créer un environnement de partage d’invités sécurisé et productif pour votre organisation :

- [Meilleures pratiques relatives au partage de fichiers et de dossiers avec des utilisateurs non authentifiés](best-practices-anonymous-sharing.md)
- [Limiter l’exposition accidentelle de fichiers lors de partages avec des personnes extérieures à votre organisation](share-limit-accidental-exposure.md)
- [Créer un environnement de partage sécurisé avec des invités](create-secure-guest-sharing-environment.md)

## <a name="access-from-unmanaged-devices"></a>Accès à partir d’appareils enregistrés

Pour les niveaux sensibles et hautement sensibles, nous limitons l’accès au contenu SharePoint avec des étiquettes de confidentialité. L’accès conditionnel Azure AD offre de nombreuses options permettant de déterminer la manière dont les utilisateurs accèdent à Microsoft 365, y compris les limitations en fonction de l’emplacement, du risque, de la conformité des appareils et d’autres facteurs. Nous vous recommandons de lire l’article [Qu’est-ce que l’accès conditionnel ?](/azure/active-directory/conditional-access/overview) et d’envisager les stratégies supplémentaires qui peuvent être appropriées pour votre organisation.

Notez que les invités n’ont souvent pas d’appareils gérés par votre organisation. Si vous autorisez des invités de l’un des niveaux, pensez aux types d’appareils qu’ils utiliseront pour accéder aux équipes et aux sites, et définissez en conséquence vos stratégies d’appareil non gérés.

### <a name="control-device-access-across-microsoft-365"></a>Contrôle de l’accès à un appareil sur Microsoft 365

Le paramètre des appareils non gérés dans les étiquettes de confidentialité affecte uniquement l’accès à SharePoint. Si vous souhaitez étendre le contrôle des appareils non gérés au-delà de SharePoint, vous pouvez [Créer une stratégie d’accès conditionnel Azure Active Directory pour toutes les applications et les services de votre organisation](/azure/active-directory/conditional-access/howto-conditional-access-policy-compliant-device) en lieu et place. Pour configurer cette stratégie spécialement pour les [services Microsoft 365](/azure/active-directory/conditional-access/concept-conditional-access-cloud-apps#office-365), sélectionnez l’application cloud **Office 365** sous **Applications ou actions cloud**.

![Capture d’écran de l’application cloud Office 365 dans une stratégie d’accès conditionnel Azure Active Directory](/sharepoint/sharepointonline/media/azure-ca-office365-policy.png)

L'utilisation d'une stratégie qui affecte tous les services Microsoft 365 peut conduire à une meilleure sécurité et à une meilleure expérience pour vos utilisateurs. Par exemple, lorsque vous bloquez l'accès aux appareils non gérés dans SharePoint uniquement, les utilisateurs peuvent accéder à la conversation dans une équipe avec un appareil non géré, mais perdront l'accès lorsqu'ils essaieront d'accéder à l'onglet **Fichiers**. L'utilisation de l'application en nuage Office 365 permet d'éviter les problèmes liés aux [dépendances de services](/azure/active-directory/conditional-access/service-dependencies).

## <a name="next-step"></a>Étape suivante

Commencez par [configurer le niveau de base de la protection](configure-teams-baseline-protection.md). Si nécessaire, vous pouvez ajouter [Protection sensible](configure-teams-sensitive-protection.md) et [Protection hautement sensible](configure-teams-highly-sensitive-protection.md) au-dessus de la ligne de base.

## <a name="see-also"></a>Voir aussi

[Sécurité et de la conformité dans Microsoft Teams](/microsoftteams/security-compliance-overview)

[Stratégies d’alerte](../compliance/alert-policies.md)
