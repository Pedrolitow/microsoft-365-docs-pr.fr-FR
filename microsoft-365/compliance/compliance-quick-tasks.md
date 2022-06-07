---
title: Tâches rapides pour bien démarrer avec la conformité dans Microsoft Purview
description: Découvrez les tâches qui vous aideront à démarrer rapidement avec la conformité dans Microsoft Purview.
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
f1.keywords:
- NOCSH
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.custom:
- admindeeplinkDEFENDER
- intro-get-started
ms.localizationpriority: medium
ms.openlocfilehash: cb8471ffea418ac47921777a0ee9594fa73fe4ac
ms.sourcegitcommit: a5e75d7f7651313818bd2de292d5c38b290d8975
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2022
ms.locfileid: "65930216"
---
# <a name="quick-tasks-for-getting-started-with-compliance-in-microsoft-purview"></a>Tâches rapides pour bien démarrer avec la conformité dans Microsoft Purview

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Si vous débutez avec Microsoft Purview et que vous vous demandez par où commencer, cet article fournit des conseils sur les principes de base et hiérarchise les tâches de conformité importantes. Cet article vous aidera à prendre rapidement en main la gestion et la surveillance de vos données, la protection des informations et la réduction des risques internes.

Cet article est également utile si vous déterminez la meilleure façon de gérer les risques, de protéger vos données et de rester conforme aux réglementations et aux normes d’une main-d’œuvre nouvellement distante. Les employés collaborent et se connectent désormais de nouvelles façons, ce qui signifie que vos processus et contrôles de conformité existants devront peut-être s’adapter. L’identification et la gestion de ces nouveaux risques de conformité au sein de votre organisation sont essentielles à la protection de vos données et à la réduction des menaces et des risques.

Une fois que vous avez effectué ces tâches de conformité de base, envisagez d’étendre la couverture de conformité dans votre organisation en implémentant des solutions Microsoft Purview supplémentaires.

## <a name="task-1-configure-compliance-permissions"></a>Tâche 1 : Configurer les autorisations de conformité

Il est important de gérer les membres de votre organisation qui ont accès au portail de conformité Microsoft Purview pour afficher le contenu et effectuer des tâches de gestion. Microsoft 365 fournit des rôles d’administration spécifiques à la conformité et à l’utilisation des outils inclus dans le portail de conformité Microsoft Purview.

Commencez par attribuer des autorisations de conformité aux personnes de votre organisation afin qu’elles puissent effectuer ces tâches et empêcher les personnes non autorisées d’accéder à des zones en dehors de leurs responsabilités. Avant de commencer à configurer et à implémenter des solutions de conformité incluses dans Microsoft 365, vous devez vous assurer que vous avez affecté les personnes appropriées à **l’administrateur des données de conformité** et aux rôles d’administrateur de conformité. Vous devez également affecter des utilisateurs au rôle de lecteur général Azure Active Directory pour afficher les données dans le Gestionnaire de conformité.

Pour obtenir des instructions détaillées sur la configuration des autorisations et l’attribution de personnes à des rôles d’administrateur, consultez [Autorisations dans le Centre de sécurité & conformité](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).

## <a name="task-2-know-your-state-of-compliance"></a>Tâche 2 : Connaître votre état de conformité

Il est difficile de savoir où aller si vous ne savez pas où vous êtes. Répondre à vos besoins de conformité inclut la compréhension de votre niveau de risque actuel et des mises à jour qui peuvent être nécessaires en ces temps en constante évolution. Que votre organisation soit novice en matière de conformité ou qu’elle dispose d’une expérience approfondie des normes et réglementations qui régissent votre secteur d’activité, la meilleure chose à faire pour améliorer la conformité consiste à comprendre où se trouve votre organisation.

[Le Gestionnaire de conformité Microsoft Purview](/microsoft-365/compliance/compliance-manager) peut vous aider à comprendre la posture de conformité de votre organisation et à mettre en évidence les domaines qui peuvent nécessiter une amélioration. Le Gestionnaire de conformité utilise un tableau de bord centralisé pour calculer un score basé sur les risques, en mesurant votre progression dans l’exécution des actions qui contribuent à réduire les risques liés à la protection des données et aux normes réglementaires. Vous pouvez également utiliser le Gestionnaire de conformité comme outil pour suivre toutes vos évaluations des risques. Il fournit des fonctionnalités de flux de travail pour vous aider à évaluer efficacement vos risques à l’aide d’un outil commun.

Pour obtenir des conseils pas à pas sur la prise en main du Gestionnaire de conformité, consultez [Prise en main du Gestionnaire de conformité](/microsoft-365/compliance/compliance-manager-setup).

> [!IMPORTANT]
> La sécurité et la conformité sont étroitement intégrées pour la plupart des organisations. Il est important que votre organisation s’attaque aux domaines de base de la sécurité, de la protection contre les menaces et de la gestion des identités et des accès pour fournir une approche de défense approfondie à la fois en matière de sécurité et de conformité.
>
> Vérifiez votre [degré de sécurisation Microsoft 365](/microsoft-365/security/defender/microsoft-secure-score) dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a> et effectuez les tâches décrites dans les articles suivants :
>
> - [Feuille de route de sécurité - Principales priorités pour les 30 premiers jours, 90 jours et au-delà](/microsoft-365/security/office-365-security/security-roadmap)
> - [12 tâches principales pour les équipes de sécurité afin de prendre en charge le travail à domicile](/microsoft-365/security/top-security-tasks-for-remote-work)

## <a name="task-3-enable-auditing-for-your-organization"></a>Tâche 3 : Activer l’audit pour votre organisation

Maintenant que vous avez déterminé l’état actuel de votre organisation et qui peut gérer les fonctions de conformité, l’étape suivante consiste à vous assurer que vous disposez des données pour effectuer des enquêtes de conformité et générer des rapports pour les activités réseau et utilisateur dans votre organisation. L’activation de l’audit est également un prérequis important pour les solutions de conformité décrites plus loin dans cet article.

Les insights fournis par le journal d’audit sont un outil précieux pour vous aider à faire correspondre vos exigences de conformité à des solutions qui peuvent vous aider à gérer et à surveiller les domaines de conformité nécessitant une amélioration. La journalisation d’audit doit être activée avant l’enregistrement des activités et avant de pouvoir effectuer une recherche dans le journal d’audit. Lorsque cette option est activée, l’activité de l’utilisateur et de l’administrateur de votre organisation est enregistrée dans le journal d’audit et conservée pendant 90 jours, et jusqu’à un an en fonction de la licence attribuée aux utilisateurs.

Pour obtenir des instructions détaillées sur l'activation de l'audit, consultez [Activer ou désactiver la recherche dans le journal d'audit](/microsoft-365/compliance/turn-audit-log-search-on-or-off).

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Tâche 4 : Créer des stratégies pour vous avertir des problèmes de conformité potentiels

Microsoft fournit plusieurs stratégies d’alerte intégrées qui permettent d’identifier les abus d’autorisations d’administrateur, l’activité des programmes malveillants, les menaces externes et internes potentielles et les risques de gestion du cycle de vie des données. Ces stratégies sont activées par défaut, mais vous devrez peut-être configurer des alertes personnalisées pour faciliter la gestion des exigences de conformité propres à votre organisation.

Utilisez des outils de stratégie d’alerte et de tableau de bord d’alerte pour créer des stratégies d’alerte personnalisées et afficher les alertes générées lorsque les utilisateurs effectuent des activités qui correspondent aux conditions de stratégie. Il peut s’agir, par exemple, d’utiliser des stratégies d’alerte pour suivre les activités des utilisateurs et des administrateurs qui affectent les exigences de conformité, les autorisations et les incidents de perte de données dans votre organisation.

Pour obtenir des instructions pas à pas pour créer des stratégies d’alerte personnalisées, consultez [Stratégies d’alerte dans le Centre de sécurité et de conformité](/microsoft-365/compliance/alert-policies).

## <a name="task-5-classify-and-protect-sensitive-data"></a>Tâche 5 : Classifier et protéger les données sensibles

Pour mener à bien leur travail, les membres de votre organisation collaborent avec d’autres personnes internes ou externes à votre organisation. Cela signifie que le contenu n’est plus protégé par un pare-feu : il peut se déplacer partout, sur les appareils, applications et services. Dans ce cas, vous devez sécuriser et protéger l’itinérance, tout en respectant les stratégies métier et de conformité de votre organisation.

[Les étiquettes de confidentialité](/microsoft-365/compliance/sensitivity-labels) vous permettent de classifier et de protéger les données de votre organisation, tout en veillant à ce que la productivité des utilisateurs et leur capacité à collaborer ne soient pas entravées. Utilisez des étiquettes de confidentialité pour appliquer des restrictions de chiffrement et d’utilisation, appliquer des marquages visuels et protéger les informations sur les plateformes et les appareils, en local et dans le cloud.

Pour obtenir des conseils pas à pas sur la configuration et l’utilisation d’étiquettes de confidentialité, consultez [Prise en main des étiquettes de confidentialité](/microsoft-365/compliance/get-started-with-sensitivity-labels).

## <a name="task-6-configure-retention-policies"></a>Tâche 6 : Configurer des stratégies de rétention

Une [stratégie de rétention](/microsoft-365/compliance/retention) vous permet de décider de manière proactive s’il faut conserver du contenu, supprimer du contenu ou les deux : conserver et supprimer le contenu à la fin d’une période de rétention spécifiée. Ces actions peuvent être nécessaires pour se conformer aux réglementations et aux politiques internes du secteur et réduire vos risques en cas de litige ou de violation de la sécurité.

Lorsque le contenu est soumis à une stratégie de rétention, les utilisateurs peuvent continuer à modifier et à utiliser le contenu comme si rien n’avait changé. Le contenu est conservé en place, dans son emplacement d’origine. Toutefois, si une personne modifie ou supprime du contenu soumis à la stratégie de rétention, une copie du contenu d’origine est enregistrée dans un emplacement sécurisé où elle est conservée pendant que la stratégie de rétention de ce contenu est en vigueur.

Vous pouvez rapidement mettre en place des stratégies de rétention pour plusieurs services dans votre environnement Microsoft 365, notamment les messages Teams et Yammer, la messagerie Exchange, les sites SharePoint et les comptes OneDrive. Il n’existe aucune limite au nombre d’utilisateurs, de boîtes aux lettres ou de sites qu’une stratégie de rétention peut inclure automatiquement. Toutefois, si vous devez être plus sélectif, vous pouvez le faire en configurant une étendue adaptative basée sur une requête pour cibler dynamiquement des instances spécifiques, ou une étendue statique qui spécifie des instances spécifiques à inclure ou à exclure toujours.

Pour obtenir des instructions pas à pas pour configurer des stratégies de rétention, consultez [Créer et configurer des stratégies de rétention](/microsoft-365/compliance/create-retention-policies). Étant donné que les stratégies de rétention constituent la pierre angulaire d’une stratégie de gestion du cycle de vie des données pour les applications et services Microsoft 365, consultez également [Prise en main de la gestion du cycle de vie des données](/microsoft-365/compliance/get-started-with-data-lifecycle-management).

## <a name="task-7-configure-sensitive-information-and-inappropriate-language-policies"></a>Tâche 7 : Configurer des informations sensibles et des stratégies de langue inappropriées

La protection des informations sensibles et la détection et l’action en cas d’incidents de harcèlement au travail sont un élément important du respect des politiques et des normes internes. [La conformité des communications](/microsoft-365/compliance/communication-compliance) dans Microsoft Purview permet de réduire ces risques en vous aidant à détecter, capturer et prendre rapidement des mesures de correction pour les communications par e-mail et Microsoft Teams. Il s’agit notamment de communications inappropriées contenant des blasphèmes, des menaces, du harcèlement et des communications qui partagent des informations sensibles à l’intérieur et à l’extérieur de votre organisation.

Un modèle de stratégie *de texte* de détection prédéfini vous permet d’analyser les communications internes et externes à la recherche de correspondances de stratégie afin qu’elles puissent être examinées par des réviseurs désignés. Les réviseurs peuvent examiner les e-mails analysés, Microsoft Teams, Yammer ou les communications tierces de votre organisation et prendre les mesures de correction appropriées pour s’assurer qu’ils sont conformes aux normes de votre organisation.

Le modèle de stratégie *détecter les informations sensibles* prédéfini vous permet de créer rapidement une stratégie pour analyser les e-mails et les communications Microsoft Teams contenant des types ou mots clés d’informations sensibles définis pour vous assurer que les données importantes ne sont pas partagées avec des personnes qui ne doivent pas avoir accès. Ces activités peuvent inclure des communications non autorisées sur des projets confidentiels ou des règles spécifiques à l’industrie sur les opérations internes ou d’autres activités de connivence.

Pour obtenir des conseils pas à pas sur la planification et la configuration de la conformité des communications, consultez [Planifier la conformité des communications](/microsoft-365/compliance/communication-compliance-plan) et [Bien démarrer avec la conformité des communications](/microsoft-365/compliance/communication-compliance-configure). Pour plus d’informations sur les licences de conformité des communications, consultez les [conseils de licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>Tâche 8 : Voir ce qui se passe avec vos éléments sensibles

Les étiquettes de confidentialité, les types d’informations sensibles, les étiquettes de rétention et les stratégies ainsi que les classifieurs pouvant être formés peuvent être utilisés pour classifier et étiqueter des éléments sensibles dans Exchange, SharePoint et OneDrive, comme vous l’avez vu dans les tâches précédentes. La dernière étape de votre parcours de tâche rapide consiste à voir quels éléments ont été étiquetés et quelles actions vos utilisateurs effectuent sur ces éléments sensibles. [l’Explorateur de contenu](/microsoft-365/compliance/data-classification-content-explorer) et [l’Explorateur d’activités](/microsoft-365/compliance/data-classification-activity-explorer) offrent cette visibilité.

### <a name="content-explorer"></a>Explorateur de contenu

L’Explorateur de contenu vous permet d’afficher, dans leur format natif, tous les éléments qui ont été classés comme un type d’informations sensibles ou appartenant à une certaine classification par un classifieur pouvant être formé, et tous les éléments auxquels une étiquette de confidentialité ou de rétention est appliquée.

Pour obtenir des conseils pas à pas sur l’utilisation de l’Explorateur de contenu, consultez [Connaître vos données - Vue d’ensemble de la classification des données](/microsoft-365/compliance/data-classification-overview) et [Bien démarrer avec l’Explorateur de contenu](/microsoft-365/compliance/data-classification-content-explorer).

### <a name="activity-explorer"></a>Explorateur d’activités

L’Explorateur d’activités vous aide à surveiller ce qui est fait avec vos éléments sensibles classifiés et étiquetés dans :

- Microsoft Office SharePoint Online
- Exchange
- OneDrive

Plus de 30 filtres différents sont à votre disposition. Parmi ceux-ci, figurent :

- plage de dates
- type d’activité
- emplacement
- utilisateur
- étiquette de confidentialité
- étiquette de rétention
- chemin d’accès du fichier
- Stratégie DLP

Pour obtenir des conseils pas à pas sur l’utilisation de l’Explorateur d’activités, consultez [Prise en main de l’Explorateur d’activités](/microsoft-365/compliance/data-classification-activity-explorer).

## <a name="next-steps"></a>Prochaines étapes

Maintenant que vous avez configuré les principes de base de la gestion de la conformité pour votre organisation, envisagez les solutions de conformité suivantes dans Microsoft Purview pour vous aider à protéger les informations sensibles et à détecter et agir sur les risques internes supplémentaires.

### <a name="configure-retention-labels"></a>Configurer des étiquettes de rétention

Alors que les stratégies de rétention s’appliquent automatiquement à tous les éléments au niveau du conteneur (tels que les sites SharePoint, les boîtes aux lettres utilisateur, etc.), [les étiquettes de rétention](/microsoft-365/compliance/retention#retention-labels) s’appliquent à des éléments individuels, tels qu’un document SharePoint ou un e-mail. Vous pouvez appliquer ces étiquettes manuellement ou automatiquement.

Les étiquettes de rétention peuvent être utilisées dans le cadre de votre stratégie de gouvernance des données pour conserver ce dont vous avez besoin et supprimer ce que vous n’avez pas. Utilisez ces étiquettes lorsque vous avez besoin d’exceptions à vos stratégies de rétention lorsque des documents ou e-mails spécifiques ont besoin de paramètres de rétention ou de suppression différents. Par exemple, votre stratégie SharePoint conserve tous les documents pendant trois ans, mais des documents métier spécifiques doivent être conservés pendant cinq ans. Pour plus d’informations, consultez [Créer des étiquettes de rétention pour les exceptions à vos stratégies de rétention](/microsoft-365/compliance/create-retention-labels-data-lifecycle-management).

Toutefois, les étiquettes de rétention, lorsqu’elles sont [utilisées avec la gestion des enregistrements](/microsoft-365/compliance/records-management), fournissent de nombreuses autres options de gestion pour prendre en charge les documents et les e-mails au niveau de l’élément. Ce niveau de gestion des données est bien adapté aux éléments de grande valeur pour les exigences commerciales, légales ou réglementaires en matière de conservation des enregistrements. Pour plus d’informations, consultez [Prise en main de la gestion des enregistrements](/microsoft-365/compliance/get-started-with-records-management).

### <a name="identify-and-define-sensitive-information-types"></a>Identifier et définir des types d’informations sensibles

Définissez des types d’informations sensibles en fonction du modèle contenu dans les informations contenues dans les données de votre organisation. Utilisez des [types d’informations sensibles intégrés](./sensitive-information-type-entity-definitions.md) pour identifier et protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Vous pouvez également créer vos propres [types d’informations de confidentialité personnalisés](/microsoft-365/compliance/create-a-custom-sensitive-information-type) spécifiques à votre organisation.

Pour obtenir des instructions pas à pas pour définir des types d’informations sensibles personnalisés, consultez [Créer un type d’informations sensibles personnalisé dans le Centre de sécurité & conformité](./create-a-custom-sensitive-information-type.md).

### <a name="prevent-data-loss"></a>Évitez les pertes de données

Les [stratégies de protection contre la perte de données (DLP) Microsoft Purview](/microsoft-365/compliance/dlp-learn-about-dlp) vous permettent d’identifier, de surveiller et de protéger automatiquement les informations sensibles au sein de votre organisation Microsoft 365. Utilisez des stratégies DLP pour identifier les éléments sensibles dans les services Microsoft, empêcher le partage accidentel d’éléments sensibles et aider les utilisateurs à apprendre à rester conformes sans interrompre leur flux de travail.

Pour obtenir des instructions pas à pas pour configurer des stratégies DLP, [créez, testez et paramétrez une stratégie DLP](/microsoft-365/compliance/create-test-tune-dlp-policy). Pour plus d’informations sur les licences de gestion des pertes de données, consultez les [conseils de gestion des licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business).

### <a name="detect-and-act-on-insider-risks"></a>Détecter et agir sur les risques internes

De plus en plus, les employés ont un accès croissant à la création, à la gestion et au partage de données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation tout en répondant aux exigences de conformité et aux normes de confidentialité des employés. Ces risques peuvent inclure le vol de données en quittant les employés et les fuites de données d’informations en dehors de votre organisation par le surpartage accidentel ou une intention malveillante.

[La gestion des risques internes](/microsoft-365/compliance/insider-risk-management-policies) utilise l’étendue complète du service et des indicateurs tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. À l’aide des journaux de Microsoft 365 et de Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque et prendre des mesures pour atténuer ces risques.

Pour obtenir des conseils pas à pas sur la planification et la configuration des stratégies de gestion des risques internes, consultez [Planifier la gestion des risques internes](/microsoft-365/compliance/insider-risk-management-plan) et [Bien démarrer avec la gestion des risques internes](/microsoft-365/compliance/insider-risk-management-configure). Pour plus d’informations sur les licences de gestion des risques internes, consultez les [instructions relatives aux licences Microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management).
