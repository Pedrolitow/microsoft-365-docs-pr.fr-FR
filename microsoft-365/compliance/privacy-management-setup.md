---
title: Prise en charge de la gestion de la confidentialité Microsoft (prévisualisation)
f1.keywords:
- CSH
ms.author: v-jgriffee
author: jmgriffee
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- M365-privacy-management
search.appverid:
- MOE150
- MET150
description: Découvrez comment configurer la gestion de la confidentialité pour votre organisation, définir des rôles et des autorisations et configurer des paramètres importants.
ms.openlocfilehash: f6989de8e9a3926f5d9e43cf08240ce76c85a0c9
ms.sourcegitcommit: 60cc1b2828b1e191f30ca439b97e5a38f48c5169
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2021
ms.locfileid: "53541012"
---
# <a name="get-started-with-privacy-management-preview"></a>Prise en charge de la gestion de la confidentialité (aperçu)

Dans cet article : découvrez  comment configurer l’accès à  la gestion de la confidentialité pour votre organisation, comment commencer à évaluer vos données et comment gérer les **paramètres importants.**

## <a name="sign-up"></a>S’inscrire

La gestion de la confidentialité est disponible dans le Centre de conformité Microsoft 365. La prévisualisation publique de la gestion de la confidentialité est disponible pour les organisations ayant des licences E1, E3 et E5 Office 365 et Microsoft 365 licences d’entreprise. Lors de la disponibilité générale de la gestion de la confidentialité, les organisations doivent obtenir une nouvelle licence.

Notez que la prévisualisation publique de la gestion de la confidentialité n’est pas disponible pour les clients modérés, Cloud de la communauté du secteur public élevés ou du département de la Défense (DoD) du gouvernement américain Community (Cloud de la communauté du secteur public).

Pour commencer la prévisualisation publique, obtenez l’abonnement d’aperçu à partir du Centre d’administration. Si vous n’avez pas encore d’abonnement lorsque vous sélectionnez la gestion de la confidentialité pour la première fois dans le centre de conformité, vous êtes dirigé vers le Centre d’administration pour commencer. Il est recommandé que l’administrateur global se connecte et définisse les autorisations des utilisateurs comme indiqué ci-dessous lors de la première visite de la gestion de la confidentialité. Si vous ne devez pas détenir le rôle requis pour obtenir l’abonnement ou consentir aux conditions d’utilisation de la gestion de la confidentialité, vous serez invité à contacter votre administrateur global pour obtenir de l’aide.

Confirmer que vous souhaitez commencer à utiliser la gestion de la confidentialité indique que vous acceptez les termes et le processus d’évaluation des données personnelles. Vous pouvez consulter les liens fournis dans son intégralité avant de poursuivre.

## <a name="set-user-permissions-and-assign-roles"></a>Définir des autorisations utilisateur et attribuer des rôles

La gestion de la confidentialité utilise un modèle d’autorisation de contrôle d’accès basé sur un rôle (RBAC). Seuls les utilisateurs affectés à un rôle peuvent accéder à la gestion de la confidentialité, et les actions autorisées par chaque utilisateur sont limitées par type de rôle.

Les autorisations et les attributions de rôles pour la gestion de la confidentialité peuvent être gérées dans le Centre de conformité Microsoft 365, comme suit. Notez que les rôles spécifiques à la gestion de la confidentialité n’apparaissent pas dans Azure Active Directory.

### <a name="in-the-microsoft-365-compliance-center"></a>Dans la Centre de conformité Microsoft 365

- Sélectionnez Autorisations dans le navigation de gauche.
- Développez le Centre de conformité et sélectionnez Rôles. La liste complète des groupes de rôles s’affiche. 
- Faites défiler pour rechercher les groupes de gestion de la confidentialité, ou recherchez par mot clé, par exemple « confidentialité ».
- Sélectionnez le groupe de rôles approprié pour voir une description, les rôles attribués et une liste de membres.
- Utilisez le lien Modifier à côté de ces sections pour ajouter ou modifier des utilisateurs ou modifier les paramètres.

### <a name="learn-about-role-groups-and-roles"></a>En savoir plus sur les groupes de rôles et les rôles

Cette section décrit les groupes de rôles et les rôles pertinents pour la gestion de la confidentialité. Les membres doivent être affectés à des groupes de rôles par l’administrateur de niveau supérieur en fonction des tâches qu’ils doivent accomplir et du niveau d’accès approprié aux fichiers. Chaque groupe de rôles comprend un ou plusieurs rôles. Ces rôles peuvent concerner des tâches de gestion de la confidentialité spécifiques ou correspondre à des fonctions clés activées ou restreintes pour les membres de ce groupe.

Les groupes de rôles peuvent être personnalisés si nécessaire. Pour éviter toute perte accidentelle d’accès, nous vous recommandons de créer une copie du groupe de rôles existant que vous souhaitez personnaliser, d’attribuer à la copie un nom identifiable, d’apporter et de vérifier vos modifications au nouveau groupe et d’y affecter des personnes, le cas échéant.

**Gestion de la** confidentialité : ce groupe contient tous les rôles d’autorisation de gestion de la confidentialité dans un seul groupe. Il s’agit du moyen le plus simple de commencer rapidement la gestion de la confidentialité et de gérer le contrôle d’accès pour d’autres groupes qui utiliseront la gestion de la confidentialité. Il convient également aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts.

Administrateurs de la gestion de la confidentialité : les membres de ce groupe de **rôles** se concentrent sur les tâches de configuration et d’administration, et ont un large accès aux fonctions de gestion de la confidentialité, notamment la création, la lecture, la mise à jour et la suppression de stratégies de gestion de la confidentialité, les demandes de droits de l’objet, les autorisations de gestion de la confidentialité et les paramètres de gestion de la confidentialité.

**Analystes de gestion de la** confidentialité : les membres de ce groupe de rôles agissent en tant qu’analystes de cas de gestion de la confidentialité. Ils peuvent examiner les correspondances de stratégie, afficher les métadonnées des fichiers et prendre des mesures correctives. Ce groupe ne peut pas accéder aux fichiers complets via l’Explorateur de contenu.

**Enquêteurs de gestion de la confidentialité**: les membres de ce groupe agissent en tant qu’enquêteurs de données de gestion de la confidentialité. Ils peuvent examiner les correspondances de stratégie, afficher le contenu du fichier associé et prendre des mesures correctives. Ce groupe peut accéder aux fichiers via l’Explorateur de contenu.

**Visionneuse de la** gestion de la confidentialité : les membres de ce groupe peuvent afficher des informations analytiques dans la gestion de la confidentialité, telles que la vue d’ensemble, le profil de données et les rapports de demande d’objet.

**Administrateurs des demandes des droits de l’objet**: les membres de ce groupe ont un accès total pour administrer et créer des demandes de droits d’objet.

**Contributeurs à la gestion de la confidentialité**: les membres de ce groupe ont un accès collaborateur aux demandes de droits de l’objet.

Pour voir les rôles spécifiques inclus dans chaque groupe de rôles, consultez le tableau suivant.

|   Groupe de rôles        |   Rôles inclus                          |
|:-- |:--|
| Gestion de la confidentialité  | Gestion des cas                           |
|                     | Visionneuse de contenu de classification des données        |
|                     | Visionneuse de listes de classification des données           |
|                     | Administrateur de la gestion de la confidentialité                  |
|                     | Analyse de la gestion de la confidentialité               |
|                     | Examen de la gestion de la confidentialité          |
|                     | Contribution permanente à la gestion de la confidentialité |
|                     | Contribution temporaire à la gestion de la confidentialité |
|                     | Visionneuse de la gestion de la confidentialité                 |
|                     | Administrateur des demandes de droits de l’objet              |
|                     | View-Only Case                            |
| Administrateur de la gestion de la confidentialité | Gestion des cas                      |
|                          | Administrateur de la gestion de la confidentialité             |
|                          | View-Only Case                       |
| Analystes de la gestion de la confidentialité | Gestion des cas                   |
|                             | Visionneuse de listes de classification des données   |
|                             | Analyse de la gestion de la confidentialité       |
|                             | View-Only Case                    |
| Enquêteurs de la gestion de la confidentialité | Gestion des cas              |
|                                  | Visionneuse de contenu de classification des données |
|                                  | Visionneuse de listes de classification des données    |
|                                  | Examen de la gestion de la confidentialité   |
|                                  | View-Only Case                     |
| Visionneuse de la gestion de la confidentialité        | Visionneuse de la gestion de la confidentialité          |
| Administrateur des demandes de droits de l’objet | Administrateur des demandes de droits de l’objet   |
|Contributeurs à la gestion de la confidentialité       | Contribution temporaire à la gestion de la confidentialité |
|                                      | Contribution permanente à la gestion de la confidentialité |

## <a name="configure-settings"></a>Configurer les paramètres

La Paramètres page est accessible via la roulette d’engrenage dans le coin supérieur droit des pages principales de la gestion de la confidentialité. Il permet aux administrateurs de gestion de la confidentialité de configurer les propriétés essentielles dans la gestion de la confidentialité. Les options sont les suivantes:

### <a name="anonymization"></a>Anonymisation

Cette fonctionnalité vous permet d’afficher des versions rendues anonymes des noms d’utilisateur dans les fonctionnalités de gestion de la confidentialité aux utilisateurs de certains rôles. Cela remplacera les noms complets identifiables tels que « Grace Grace » par une étiquette générique telle que « AnonyIS8-988 » afin de masquer les identités de vos utilisateurs lors de l’examen des données sensibles. Cette option ne s’applique pas au module de demande de droits de l’objet.

### <a name="user-notification-emails"></a>E-mails de notification de l’utilisateur

Lorsque nous détectons une correspondance pour vos stratégies de gestion des données, la gestion de la confidentialité peut envoyer un courrier électronique aux utilisateurs concernés avec des actions correctives à prendre et un lien vers une formation sur la confidentialité. Dans Paramètres, vous pouvez activer ou désactiver la fonctionnalité de notification par courrier électronique de la gestion de la confidentialité dans son ensemble. Vous pouvez activer des notifications individuelles, définir la fréquence des e-mails et spécifier une URL de formation lorsque vous créez ou modifiez une stratégie. Si la fonctionnalité de notification est désactivée Paramètres, toute configuration au niveau de la stratégie pour des messages de notification spécifiques est désactivée. Pour en savoir plus sur les stratégies, voir [Créer et gérer des stratégies.](privacy-management-policies.md)

### <a name="teams-collaboration"></a>Collaboration des équipes

Intégrez Microsoft Teams fonctionnalités de gestion de la confidentialité pour améliorer la collaboration avec les parties prenantes. Chaque fois qu’une demande de droits d’objet est créée, une équipe associée est créée. Les utilisateurs peuvent être ajoutés à une équipe à partir de l’onglet Collaborateurs de la demande. Pour en savoir plus sur les demandes de droits d’objet, voir [Gérer les demandes de droits d’objet.](privacy-management-subject-rights-requests.md)

### <a name="power-automate-flows"></a>Power Automate flux

Utilisez Power Automate flux de travail pour gérer automatiquement les processus et les tâches liés à la confidentialité. Vous pouvez créer des flux dans la section Paramètres à l’aide de modèles de gestion de la confidentialité intégrés ou utiliser la console Power Automate pour créer des flux personnalisés. Pour en savoir plus sur Power Automate, consultez la documentation [Power Automate](/power-automate/) documentation.

### <a name="data-matching"></a>Correspondance de données

Utilisez cette section pour télécharger des schémas de données qui décrivent les attributs de vos sujets de données, ce qui permet d’identifier la sujet de données correcte lors de la recherche de données personnelles dans votre environnement Microsoft 365 données. Les schémas et les packages de règles sont créés et chargés au format XML. Sous téléchargement de données personnelles, vous pouvez également envoyer des données personnelles qui correspond à un schéma fourni. Vous pouvez créer et télécharger votre propre fichier ou choisir de télécharger des données personnelles à partir d’Azure. Pour en savoir plus sur les demandes de droits d’objet, voir [Gérer les demandes de droits d’objet.](privacy-management-subject-rights-requests.md)

### <a name="data-retention-periods"></a>Périodes de rétention des données

Pour les demandes de droits d’objet, choisissez la durée de rétention des données finales collectées et le rapport après la fermeture d’une demande. Vous pouvez sélectionner entre 30 et 90 jours. Pour en savoir plus sur les demandes de droits d’objet, voir [Gérer les demandes de droits d’objet.](privacy-management-subject-rights-requests.md)

### <a name="data-review-tags"></a>Balises de révision des données

Gérez les balises que vous utiliserez pour marquer les fichiers récupérés dans une demande de droits d’objet. Dans cette section, vous pouvez modifier les noms et les descriptions des balises personnalisées. Vous pouvez également modifier les descriptions des balises intégrées fournies par le système. Les noms des balises système ne peuvent pas être modifiés. Pour en savoir plus sur les demandes de droits d’objet, voir [Gérer les demandes de droits d’objet.](privacy-management-subject-rights-requests.md)

## <a name="get-initial-data-insights"></a>Obtenir des informations sur les données initiales

Une fois que vous êtes passé à la gestion de la confidentialité, vous arrivez à la page **Vue d’ensemble.** Cette page fournit des informations dynamiques sur les données personnelles stockées dans votre environnement Microsoft 365 afin de vous aider à identifier rapidement les problèmes, à identifier les indicateurs de risque et à prendre des mesures pour résoudre les problèmes. Votre vue d’ensemble doit être remplie avec les informations initiales dans les 24 premières heures de l’inscription. À mesure que vous continuez d’utiliser la gestion de la confidentialité, la page de vue d’ensemble s’actualise pour continuer à fournir des informations actuelles.

Pour obtenir des informations supplémentaires sur vos données au fil du temps, votre **page** de profil de données fournit davantage de visualisations et d’analyses et vous offre une vue d’ensemble des données de votre organisation par emplacement géographique et par service Microsoft 365.

Pour en savoir plus sur ces pages, voir [Rechercher et visualiser vos données.](privacy-management-data-profile.md)
