---
title: Tâches rapides pour la mise en route de la conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: Normal
description: Découvrez les tâches qui vous aideront à commencer rapidement à prendre en main la conformité dans Microsoft 365.
ms.openlocfilehash: 87dfa73c52473b0695c496826572ab9b5180dfca
ms.sourcegitcommit: 92bd1631a2bb6df8683aa6da45a116090b338bb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/15/2020
ms.locfileid: "44732482"
---
# <a name="quick-tasks-for-getting-started-with-microsoft-365-compliance"></a>Tâches rapides pour la mise en route de la conformité Microsoft 365

Si vous débutez avec la conformité Microsoft 365 et que vous vous demandez où commencer, cet article fournit des conseils sur les notions de base et hiérarchise les tâches de conformité importantes. Cet article vous aidera à démarrer rapidement la gestion et la surveillance de vos données, en protégeant les informations et en minimisant les risques des Insiders.

Cet article s’avère également utile si vous souhaitez mieux gérer les risques, protéger vos données et rester conformes aux réglementations et aux normes avec un nouveau personnel à distance. Les employés collaborent et se connectent les uns avec les autres de nouvelles façons, ce qui signifie que vos processus et contrôles de conformité existants peuvent nécessiter une adaptation. L’identification et la gestion de ces nouveaux risques de conformité au sein de votre organisation sont essentielles à la protection de vos données et à la minimisation des menaces et des risques.

Une fois ces tâches de conformité de base terminées, envisagez de développer la couverture de conformité dans votre organisation en implémentant des solutions de conformité Microsoft 365 supplémentaires.

## <a name="task-1-configure-compliance-permissions"></a>Tâche 1 : configurer les autorisations de conformité

Il est important de gérer les personnes de votre organisation qui ont accès au centre de conformité Microsoft 365 pour afficher le contenu et effectuer des tâches de gestion. Microsoft 365 fournit des rôles d’administrateur spécifiques à la conformité et à l’utilisation des outils inclus dans le centre de conformité Microsoft 365.

Commencez par attribuer des autorisations de conformité aux personnes de votre organisation pour qu’elles puissent effectuer ces tâches et empêcher des personnes non autorisées d’accéder à des zones en dehors de leurs responsabilités. Vous devez vous assurer que vous avez affecté les personnes appropriées aux rôles d’administrateur des **données de conformité** et d’administrateur de **conformité** avant de commencer à configurer et à implémenter des solutions de conformité incluses dans Microsoft 365. Vous devrez également affecter des utilisateurs au rôle de lecteur global Azure Active Directory pour afficher les données dans le score de conformité.

Pour obtenir des conseils détaillés sur la configuration des autorisations et l’affectation de personnes aux rôles d’administrateur, consultez [la rubrique autorisations dans le centre de sécurité & conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

## <a name="task-2-know-your-state-of-compliance"></a>Tâche 2 : déterminer votre état de conformité

Il est difficile de déterminer où aller si vous ne le Sachez pas. Répondre à vos besoins en matière de conformité inclut la compréhension de votre niveau de risque actuel et des mises à jour nécessaires à ces changements. Que votre organisation soit une nouveauté aux exigences de conformité ou qu’elle ait une expérience approfondie en matière de standards et de réglementations qui régissent votre secteur d’activité, la meilleure solution pour améliorer la conformité consiste à comprendre l’emplacement de votre organisation.

Le [score de conformité Microsoft](compliance-score.md) peut vous aider à comprendre la position de la conformité de votre organisation et à mettre en évidence les zones susceptibles de nécessiter une amélioration. Le score de conformité utilise un tableau de bord centralisé pour calculer un score basé sur les risques, ce qui mesure votre progression dans la réalisation d’actions qui permettent de réduire les risques liés à la protection des données et aux normes réglementaires. Vous pouvez également utiliser le score de conformité en tant qu’outil pour suivre toutes vos évaluations de risques. Il fournit des fonctionnalités de flux de travail pour vous aider à effectuer efficacement les évaluations des risques par le biais d’un outil courant.

Pour obtenir des conseils détaillés sur la prise en main du score de conformité, consultez [la rubrique Set up Compliance score](compliance-score-setup.md).

>[!IMPORTANT]
>La sécurité et la conformité sont étroitement intégrées pour la plupart des organisations. Il est important que votre organisation gère la sécurité de base, la protection contre les menaces et les zones de gestion des identités et des accès afin de fournir une approche de défense approfondie à la sécurité et à la conformité.
>
>Vérifiez votre [score de sécurité microsoft 365](../security/mtp/microsoft-secure-score.md) dans le centre de sécurité Microsoft 365 et effectuez les tâches décrites dans les articles suivants :
>
> - [Feuille de route de sécurité-priorités principales des 30 premiers jours, 90 jours, et au-delà](../security/office-365-security/security-roadmap.md)
> - [12 premières tâches pour les équipes de sécurité qui prennent en charge le travail à domicile](../security/top-security-tasks-for-remote-work.md)

## <a name="task-3-enable-auditing-for-your-organization"></a>Tâche 3 : activer l’audit pour votre organisation

À présent que vous avez déterminé l’état actuel de votre organisation et que vous pouvez gérer les fonctions de conformité, l’étape suivante consiste à s’assurer que vous disposez des données pour effectuer des enquêtes de conformité et générer des rapports pour les activités réseau et utilisateur dans votre organisation. L’activation de l’audit est également une condition préalable importante pour les solutions de conformité abordées plus loin dans cet article.

Les informations fournies par le journal d’audit sont un outil précieux pour vous aider à répondre à vos exigences de conformité aux solutions susceptibles de vous aider à gérer et à surveiller les zones de conformité nécessitant des améliorations. La journalisation d’audit doit être activée avant que les activités soient enregistrées et avant de pouvoir effectuer des recherches dans le journal d’audit. Lorsque ce paramètre est activé, l’activité de l’utilisateur et de l’administrateur de votre organisation est enregistrée dans le journal d’audit et conservée pendant 90 jours, et jusqu’à un an en fonction de la licence attribuée aux utilisateurs.

Pour obtenir des instructions détaillées sur l’activation de l’audit, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Tâche 4 : créer des stratégies pour vous informer des éventuels problèmes de conformité

Microsoft fournit plusieurs stratégies d’alerte intégrées qui permettent d’identifier les autorisations d’administrateur abus, l’activité de programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Ces stratégies sont activées par défaut, mais vous devrez peut-être configurer des alertes personnalisées pour faciliter la gestion des exigences de conformité propres à votre organisation.

Utilisez les outils de tableau de bord de stratégie et d’alerte pour créer des stratégies d’alerte personnalisées et afficher les alertes générées lorsque les utilisateurs effectuent des activités qui correspondent aux conditions de la stratégie. Voici quelques exemples d’utilisation des stratégies d’alerte pour suivre les activités de l’utilisateur et de l’administrateur affectant les exigences de conformité, les autorisations et les incidents de perte de données au sein de votre organisation.

Pour obtenir des conseils détaillés sur la création de stratégies d’alerte personnalisées, consultez [la rubrique Alert Policies in the Security and Compliance Center](alert-policies.md).

## <a name="task-5-configure-just-in-time-access-for-your-administrators"></a>Tâche 5 : configurer l’accès juste-à-temps pour vos administrateurs

L’accès permanent de certains utilisateurs à des informations sensibles ou à des paramètres de configuration réseau critiques constitue une voie potentielle pour les comptes compromis ou les activités de menace interne. La [gestion des accès privilégiés](privileged-access-management-overview.md) permet de protéger votre organisation contre les violations et de respecter les meilleures pratiques en matière de conformité en limitant l’accès permanent aux données sensibles ou l’accès aux paramètres de configuration critiques. Au lieu que les administrateurs disposent d’un accès constant, les règles d’accès juste-à-temps sont implémentées pour les tâches qui nécessitent des autorisations élevées. L’activation de la gestion des accès privilégiés dans Microsoft 365 permet à votre organisation de fonctionner avec des privilèges permanents et de fournir une couche de défense contre les vulnérabilités d’accès administratif permanentes.

Pour obtenir des conseils détaillés sur la configuration de la gestion des accès privilégiés, consultez la rubrique [prise en main de la gestion des accès privilégiés](privileged-access-management-configuration.md). Pour obtenir des informations sur les licences de gestion des accès privilégiés, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#privileged-access-management-in-office-365).

## <a name="task-6-classify-and-protect-sensitive-data"></a>Tâche 6 : classer et protéger les données sensibles

To get their work done, people in your organization collaborate with others both inside and outside the organization. This means that content no longer stays behind a firewall—it can roam everywhere, across devices, apps, and services. And when it roams, you want it to do so in a secure, protected way that meets your organization's business and compliance policies.

Les [étiquettes de sensibilité](sensitivity-labels.md) vous permettent de classer et de protéger les données de votre organisation, tout en veillant à ce que la productivité des utilisateurs et leur capacité à collaborer ne soient pas entravées. Utiliser les étiquettes de sensibilité pour appliquer le chiffrement et les restrictions d’utilisation appliquer des marquages visuels et protéger les informations sur les plateformes et les appareils, sur site et dans le Cloud.

Pour obtenir des conseils détaillés sur la configuration et l’utilisation des étiquettes de confidentialité, consultez la rubrique [prise en main des étiquettes de confidentialité](get-started-with-sensitivity-labels.md). Pour obtenir des informations sur les licences d’étiquette de sensibilité, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection).

## <a name="task-7-configure-a-retention-policy"></a>Tâche 7 : configurer une stratégie de rétention

Une [stratégie de rétention](retention-policies.md) vous permet de décider de manière proactive de conserver le contenu, de supprimer du contenu, ou les deux, de conserver, puis de supprimer le contenu à la fin d’une période de rétention spécifiée. Ces actions peuvent être nécessaires pour se conformer aux réglementations sectorielles et aux politiques internes, ainsi que réduire le risque en cas de litige ou de violation de la sécurité.

Lorsque le contenu est soumis à une stratégie de rétention, les utilisateurs peuvent continuer à modifier et à travailler avec le contenu comme s’ils ne l’ont pas changé. Le contenu est conservé en place, à son emplacement d’origine. Toutefois, si un utilisateur modifie ou supprime le contenu qui est soumis à la stratégie de rétention, une copie du contenu d’origine est enregistrée à un emplacement sécurisé où il est conservé, tandis que la stratégie de rétention pour ce contenu est en vigueur.

Vous pouvez rapidement mettre une stratégie de rétention en place pour plusieurs emplacements dans votre environnement Microsoft 365 : le courrier Exchange et les dossiers publics, les sites SharePoint, les comptes OneDrive et les groupes Microsoft 365. Appelée « stratégie de rétention à l’échelle de l’organisation », il n’existe pas de limite au nombre de boîtes aux lettres ou de sites que la stratégie peut inclure. Toutefois, si vous devez obtenir plus de détails, vous pouvez le faire en configurant une stratégie de rétention pour des emplacements spécifiques, puis en incluant ou en excluant des sites ou des utilisateurs.

Pour obtenir des conseils détaillés sur la configuration d’une stratégie de rétention, voir [Create and configure Retention Policies](create-retention-policies.md). Pour plus d’informations sur les licences de gestion des enregistrements, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management).

## <a name="task-8-configure-sensitive-information-and-offensive-language-policies"></a>Tâche 8 : configurer des informations sensibles et des stratégies de langue offensante

La protection des informations sensibles et la détection et l’action des incidents de harcèlement sur le lieu de travail constituent un élément important de la conformité aux stratégies et normes internes. [La conformité de la communication](communication-compliance-feature-reference.md) dans Microsoft 365 contribue à réduire ces risques en vous aidant à détecter, capturer et prendre rapidement des mesures correctives pour les communications par E-mail et Microsoft Teams. Il s’agit notamment de communications inappropriées contenant des blasphèmes, des menaces et des communications qui partagent des informations sensibles à l’intérieur et à l’extérieur de votre organisation.

Un modèle de stratégie *anti-harcèlement et injurieux* prédéfini vous permet d’analyser les communications internes et externes des correspondances de stratégie pour qu’elles puissent être examinées par les relecteurs désignés. Les relecteurs peuvent analyser les e-mails analysés, Microsoft Teams, Yammer ou des communications tierces de votre organisation et prendre les mesures correctives appropriées pour s’assurer qu’elles sont conformes aux normes de votre organisation.

Le modèle de stratégie d' *informations sensibles* prédéfini vous permet de créer rapidement une stratégie pour analyser le courrier électronique et les communications Microsoft teams contenant des types d’informations sensibles ou des mots clés pour vous assurer que les données importantes ne sont pas partagées avec des personnes qui n’ont pas accès. Ces activités peuvent inclure des communications non autorisées concernant des projets confidentiels ou des règles sectorielles sur les opérations d’initié ou d’autres activités de collusion.

Pour obtenir des conseils détaillés sur la planification et la configuration de la conformité des communications, voir [plan for communication Compliance](communication-compliance-plan.md) et [Get Started with communication Compliance](communication-compliance-configure.md). Pour plus d’informations sur les licences de conformité des communications, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="next-steps"></a>Étapes suivantes

À présent que vous avez configuré les bases de la gestion de la conformité pour votre organisation, envisagez les solutions de conformité suivantes dans Microsoft 365 pour vous aider à protéger les informations sensibles et à détecter et agir sur des risques Insiders supplémentaires.

### <a name="configure-retention-labels"></a>Configurer des étiquettes de rétention

Tandis que les stratégies de rétention s’appliquent au niveau du conteneur aux emplacements comme les sites SharePoint et les boîtes aux lettres Exchange, les [étiquettes de rétention](labels.md) permettent un ciblage plus spécifique pour vos stratégies de rétention et de suppression. Par exemple, au niveau du document ou du message électronique que les utilisateurs finaux peuvent appliquer manuellement en plus de l’application automatique par les administrateurs. Vous pouvez également appliquer une étiquette de rétention à une bibliothèque de documents, un dossier ou un ensemble de documents dans SharePoint, afin que tous les documents stockés à cet emplacement héritent de l’étiquette de rétention par défaut.

En outre, les étiquettes de rétention prennent en charge la [gestion des enregistrements](records-management.md) pour marquer le contenu comme un enregistrement. Dans ce cas, l’étiquette ne peut pas être modifiée ou retirée, et le contenu ne peut pas être modifié ou supprimé. Ces restrictions peuvent être nécessaires pour aider votre organisation à respecter les exigences réglementaires.

Pour obtenir des conseils détaillés sur la création et la publication des étiquettes de rétention, consultez la rubrique [créer, publier et appliquer automatiquement des étiquettes de rétention](create-retention-labels.md). Pour plus d’informations sur les licences de gestion des enregistrements, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#records-management).

### <a name="identify-and-define-sensitive-information-types"></a>Identifier et définir des types d’informations sensibles

Définir des types d’informations sensibles en fonction du modèle contenu dans les informations des données de votre organisation. Utilisez des [types d’informations sensibles intégrés pour](what-the-sensitive-information-types-look-for.md) identifier et protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Vous pouvez créer vos propres [types d’informations de sensibilité personnalisés](custom-sensitive-info-types.md) propres à votre organisation.

Pour obtenir des conseils détaillés sur la définition des types d’informations sensibles personnalisés, voir [créer un type d’informations sensibles personnalisé dans le centre de conformité & Compliance Center](https://docs.microsoft.com/microsoft-365/compliance/create-a-custom-sensitive-information-type).

### <a name="prevent-data-loss"></a>Éviter les pertes de données

Les [stratégies de protection contre la perte de données (DLP)](data-loss-prevention-policies.md) vous permettent d’identifier, de surveiller et de protéger automatiquement les informations sensibles dans votre organisation Microsoft 365. Utiliser des stratégies DLP pour identifier des informations sensibles dans les services Microsoft, empêcher le partage accidentel d’informations sensibles et aider les utilisateurs à se conformer à la conformité sans interrompre leur flux de travail.

Pour obtenir des conseils détaillés sur la configuration des stratégies DLP, consultez la rubrique [prise en main des recommandations de stratégie DLP](get-started-with-dlp-policy-recommendations.md) et [prise en main de la stratégie DLP par défaut](get-started-with-the-default-dlp-policy.md). Pour plus d’informations sur les licences de gestion des pertes de données, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Détecter et agir sur les risques des Insiders

De plus en plus, les employés disposent d’un accès croissant pour créer, gérer et partager des données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation, tout en respectant les exigences de conformité et les normes de confidentialité des employés. Ces risques peuvent inclure le vol de données en faisant sortir les employés et les fuites de données d’informations en dehors de votre organisation par un surPartage accidentel ou intentionnellement involontaire.

La [gestion des risques initiés](insider-risk-management-policies.md) dans Microsoft 365 utilise l’ensemble complet des indicateurs de service et tiers pour vous aider à identifier, à trier et à traiter rapidement les activités des utilisateurs à risque. À l’aide des journaux Microsoft 365 et Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque et de prendre des mesures pour atténuer ces risques.

Pour obtenir des conseils détaillés sur la planification et la configuration des stratégies de gestion des risques initiés, voir [plan for Insider Management Risk](insider-risk-management-plan.md) Management and [Start with Insider Risk Management](insider-risk-management-configure.md). Pour plus d’informations sur les licences de gestion des risques des Insiders, consultez [la rubrique Microsoft 365 Licensing Guidance for security & Compliance](https://docs.microsoft.com/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
