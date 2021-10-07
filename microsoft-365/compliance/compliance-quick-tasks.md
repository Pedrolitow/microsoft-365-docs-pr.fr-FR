---
title: Tâches rapides pour démarrer avec la conformité Microsoft 365
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.collection:
- m365-security-compliance
- m365initiative-compliance
ms.localizationpriority: medium
description: Découvrez les tâches qui vous aideront à prendre rapidement en charge la conformité dans Microsoft 365.
ms.openlocfilehash: d60a9f589b6dc0c29d60c96fac9a8e30fbc4a3e0
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60156545"
---
# <a name="quick-tasks-for-getting-started-with-microsoft-365-compliance"></a>Tâches rapides pour démarrer avec la conformité Microsoft 365

Si vous débutez avec Microsoft 365 conformité et que vous vous demandez où commencer, cet article fournit des instructions sur les bases et hiérarchise les tâches de conformité importantes. Cet article vous aidera à prendre rapidement en charge la gestion et la surveillance de vos données, la protection des informations et la réduction des risques internes.

Cet article est également utile si vous savez comment gérer au mieux les risques, protéger vos données et rester conforme aux réglementations et normes avec un personnel nouvellement distant. Les employés collaborent et se connectent désormais les uns avec les autres de nouvelles façons, ce qui signifie que vos processus et contrôles de conformité existants devront peut-être s’adapter. L’identification et la gestion de ces nouveaux risques de conformité au sein de votre organisation sont essentiels à la protection de vos données et à la réduction des menaces et des risques.

Une fois ces tâches de conformité de base terminées, envisagez d’étendre la couverture de conformité dans votre organisation en implémentant des solutions Microsoft 365 conformité supplémentaires.

## <a name="task-1-configure-compliance-permissions"></a>Tâche 1 : Configurer les autorisations de conformité

Il est important de gérer les personnes de votre organisation qui ont accès au Centre de conformité Microsoft 365 pour afficher du contenu et effectuer des tâches de gestion. Microsoft 365 rôles d’administration spécifiques à la conformité et à l’utilisation des outils inclus dans le Centre de conformité Microsoft 365.

Commencez par attribuer des autorisations de conformité aux membres de votre organisation afin qu’ils peuvent effectuer ces tâches et empêcher les personnes non autorisées d’avoir accès à des zones en dehors de leurs responsabilités. Vous devez vous assurer que vous avez affecté les  bonnes personnes  aux rôles d’administrateur des données de conformité et d’administrateur de conformité avant de commencer à configurer et implémenter des solutions de conformité incluses dans Microsoft 365. Vous devez également affecter des utilisateurs au Azure Active Directory de lecture global pour afficher les données dans le Gestionnaire de conformité.

Pour obtenir des instructions pas à pas sur la configuration des autorisations et l’affectation de personnes à des rôles d’administrateur, voir Autorisations dans le Centre de sécurité [& conformité.](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)

## <a name="task-2-know-your-state-of-compliance"></a>Tâche 2 : Connaître votre état de conformité

Il est difficile de savoir où aller si vous ne savez pas où vous vous trouvez. Pour répondre à vos besoins en matière de conformité, vous pouvez comprendre votre niveau actuel de risque et les mises à jour qui peuvent être nécessaires dans ces temps en constante évolution. Que votre organisation soit nouvelle en matière de conformité ou qu’elle ait une expérience approfondie des normes et réglementations qui régissent votre secteur d’activité, la meilleure chose que vous pouvez faire pour améliorer la conformité consiste à comprendre où en est votre organisation.

[Le Gestionnaire de conformité Microsoft peut](compliance-manager.md) vous aider à comprendre la posture de conformité de votre organisation et à mettre en évidence les domaines qui peuvent avoir besoin d’être améliorés. Le Gestionnaire de conformité utilise un tableau de bord centralisé pour calculer un score basé sur les risques, mesurant votre progression dans l’exécution des actions qui permettent de réduire les risques liés à la protection des données et aux normes réglementaires. Vous pouvez également utiliser le Gestionnaire de conformité comme outil pour suivre toutes vos évaluations des risques. Il fournit des fonctionnalités de flux de travail pour vous aider à évaluer efficacement vos risques à l’aide d’un outil commun.

Pour obtenir des instructions pas à pas pour commencer avec le Gestionnaire de conformité, consultez La mise en [place du Gestionnaire de conformité.](compliance-manager-setup.md)

> [!IMPORTANT]
> La sécurité et la conformité sont étroitement intégrées pour la plupart des organisations. Il est important que votre organisation aborde les domaines de sécurité de base, de protection contre les menaces et de gestion des identités et des accès pour fournir une approche de défense en profondeur à la sécurité et à la conformité.
>
> Vérifiez votre [niveau Microsoft 365 sécurisé dans](../security/defender/microsoft-secure-score.md) le centre Microsoft 365 sécurité et terminez les tâches décrites dans les articles suivants :
>
> - [Feuille de route de sécurité : principales priorités pour les 30 premiers jours, 90 jours et au-delà](../security/office-365-security/security-roadmap.md)
> - [12 tâches principales pour les équipes de sécurité pour prendre en charge le travail à domicile](../security/top-security-tasks-for-remote-work.md)

## <a name="task-3-enable-auditing-for-your-organization"></a>Tâche 3 : activer l’audit pour votre organisation

Maintenant que vous avez déterminé l’état actuel de votre organisation et qui peut gérer les fonctions de conformité, l’étape suivante consiste à vous assurer que vous avez les données pour mener des enquêtes de conformité et générer des rapports sur les activités du réseau et des utilisateurs dans votre organisation. L’activation de l’audit est également une condition préalable importante pour les solutions de conformité couvertes plus loin dans cet article.

Informations données fournies par le journal d’audit sont un outil précieux pour vous aider à faire correspondre vos exigences de conformité aux solutions qui peuvent vous aider à gérer et surveiller les domaines de conformité qui ont besoin d’être améliorés. L’enregistrement d’audit doit être activé avant l’enregistrement des activités et avant de pouvoir effectuer une recherche dans le journal d’audit. Lorsqu’elle est activée, l’activité des utilisateurs et des administrateurs de votre organisation est enregistrée dans le journal d’audit et conservée pendant 90 jours, et jusqu’à un an en fonction de la licence attribuée aux utilisateurs.

Pour obtenir des instructions détaillées sur l’activer, voir Activer ou désactiver la recherche dans le journal [d’audit.](turn-audit-log-search-on-or-off.md)

## <a name="task-4-create-policies-to-alert-you-about-potential-compliance-issues"></a>Tâche 4 : créer des stratégies pour vous alerter sur les problèmes de conformité potentiels

Microsoft fournit plusieurs stratégies d’alerte intégrées qui permettent d’identifier les abus des autorisations d’administrateur, l’activité des programmes malveillants, les menaces externes et internes potentielles, ainsi que les risques de gouvernance des informations. Ces stratégies sont désactivées par défaut, mais vous devrez peut-être configurer des alertes personnalisées pour vous aider à gérer les exigences de conformité propres à votre organisation.

Utilisez la stratégie d’alerte et les outils de tableau de bord d’alerte pour créer des stratégies d’alerte personnalisées et afficher les alertes générées lorsque les utilisateurs effectuent des activités qui correspondent aux conditions de stratégie. Par exemple, vous pouvez utiliser des stratégies d’alerte pour suivre les activités des utilisateurs et des administrateurs qui affectent les exigences de conformité, les autorisations et les incidents de perte de données dans votre organisation.

Pour obtenir des instructions pas à pas sur la création de stratégies d’alerte personnalisées, voir stratégies d’alerte dans le centre de sécurité [et conformité.](alert-policies.md)

## <a name="task-5-classify-and-protect-sensitive-data"></a>Tâche 5 : classifier et protéger les données sensibles

Pour mener à bien leur travail, les membres de votre organisation collaborent avec d’autres personnes internes ou externes à votre organisation. Cela signifie que le contenu n’est plus protégé par un pare-feu : il peut se déplacer partout, sur les appareils, applications et services. Dans ce cas, vous devez sécuriser et protéger l’itinérance, tout en respectant les stratégies métier et de conformité de votre organisation.

[Les étiquettes de sensibilité](sensitivity-labels.md) vous permet de classifier et de protéger les données de votre organisation, tout en vous assurez que la productivité des utilisateurs et leur capacité à collaborer ne sont pas ralenties. Utilisez les étiquettes de niveau de sensibilité pour appliquer des restrictions de chiffrement et d’utilisation en appliquant des marquages visuels et protéger les informations sur les plateformes et les appareils, en local et dans le cloud.

Pour obtenir des instructions pas à pas sur la configuration et l’utilisation des étiquettes de sensibilité, consultez La mise en place [des étiquettes de sensibilité.](get-started-with-sensitivity-labels.md) Pour plus d’informations sur les licences d’étiquettes de niveau de Microsoft 365, consultez les recommandations en matière de [licences pour la sécurité & conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#information-protection)

## <a name="task-6-configure-a-retention-policy"></a>Tâche 6 : Configurer une stratégie de rétention

Une [stratégie de](retention.md) rétention vous permet de décider de manière proactive s’il faut conserver du contenu, supprimer du contenu ou les deux, conserver puis supprimer le contenu à la fin d’une période de rétention spécifiée. Ces actions peuvent être nécessaires pour se conformer aux réglementations du secteur et aux stratégies internes, et réduire les risques en cas de litige ou de violation de la sécurité.

Lorsque le contenu est soumis à une stratégie de rétention, les utilisateurs peuvent continuer à modifier le contenu et à l’utiliser comme si rien n’était modifié. Le contenu est conservé en place, à son emplacement d’origine. Toutefois, si quelqu’un modifie ou supprime le contenu soumis à la stratégie de rétention, une copie du contenu d’origine est enregistrée dans un emplacement sécurisé où il est conservé pendant que la stratégie de rétention de ce contenu est en vigueur.

Vous pouvez rapidement mettre en place une stratégie de rétention pour plusieurs emplacements de votre environnement Microsoft 365 tels que la messagerie Exchange, les sites SharePoint, les comptes OneDrive et les groupes Microsoft 365 de rétention. Il n’existe aucune limite au nombre de boîtes aux lettres ou de sites que cette stratégie peut inclure automatiquement. Toutefois, si vous devez être plus sélectif, vous pouvez le faire en configurant une stratégie de rétention pour des emplacements spécifiques et inclure ou exclure des sites ou des utilisateurs.

Pour obtenir des instructions pas à pas pour configurer une stratégie de rétention, voir [Créer et configurer des stratégies de rétention.](create-retention-policies.md) Si vous n’avez jamais configurer la rétention dans Microsoft 365, voir [Prise en main des stratégies et des étiquettes de rétention](get-started-with-retention.md).

## <a name="task-7-configure-sensitive-information-and-offensive-language-policies"></a>Tâche 7 : Configurer des informations sensibles et des stratégies de langage choquant

La protection des informations sensibles et la détection et l’action sur les incidents de harcèlement sur le lieu de travail est un élément important de la conformité avec les stratégies et normes internes. [La conformité des](communication-compliance-feature-reference.md) communications Microsoft 365 réduire ces risques en vous aidant à détecter, capturer et prendre rapidement des mesures correctives pour les communications électroniques et Microsoft Teams messagerie. Il s’agit notamment de communications inappropriées contenant du blasphémité, des menaces, du harcèlement et des communications qui partagent des informations sensibles à l’intérieur et à l’extérieur de votre organisation.

Un modèle de stratégie *anti-harcèlement* et de langage choquant prédéfini vous permet d’analyser les communications internes et externes pour les correspondances de stratégie afin qu’elles soient examinées par des réviseurs désignés. Les réviseurs peuvent examiner les communications analysées par e-mail, Microsoft Teams, Yammer ou tierces dans votre organisation et prendre les mesures correctives appropriées pour s’assurer qu’elles sont conformes aux normes de votre organisation.

Le modèle  de stratégie d’informations sensibles prédéfini vous permet de créer rapidement une stratégie pour analyser les communications par courrier électronique et Microsoft Teams contenant des mots clés ou des types d’informations sensibles définis pour vous assurer que les données importantes ne sont pas partagées avec des personnes qui ne devraient pas y avoir accès. Ces activités peuvent inclure des communications non autorisées sur des projets confidentiels ou des règles propres au secteur sur le délit d’initié ou d’autres activités d’initié.

Pour obtenir des instructions pas à pas pour planifier et configurer la conformité des communications, voir [Plan for communication compliance](communication-compliance-plan.md) and Get started with communication [compliance](communication-compliance-configure.md). Pour plus d’informations sur les licences de conformité des communications, [voir Microsoft 365 licences pour la sécurité et & conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance)

## <a name="task-8-see-whats-happening-with-your-sensitive-items"></a>Tâche 8 : voir ce qui se passe avec vos éléments sensibles

Les étiquettes de confidentialité, les types d’informations sensibles, les étiquettes et stratégies de rétention et les classifieurs entraidables peuvent être utilisés pour classer et étiqueter des éléments sensibles sur Exchange, SharePoint et OneDrive comme vous l’avez vu dans les tâches précédentes. La dernière étape de votre parcours de tâche rapide consiste à voir quels éléments ont été étiquetés et quelles actions vos utilisateurs prennent sur ces éléments sensibles. [L’Explorateur de](data-classification-content-explorer.md) contenu [et l’Explorateur d’activités](data-classification-activity-explorer.md) fournissent cette visibilité.

### <a name="content-explorer"></a>Explorateur de contenu
 L’Explorateur de contenu vous permet d’afficher, dans leur format natif, tous les éléments qui ont été classés en tant que type d’informations sensibles ou appartenant à une certaine classification par un classifieur entraisable, ainsi que tous les éléments qui ont une étiquette de sensibilité ou de rétention appliquée.

Pour obtenir des instructions pas à pas sur l’utilisation de l’Explorateur de contenu, voir Connaître vos données - vue d’ensemble de la [classification](data-classification-overview.md)des données et commencer à [utiliser l’Explorateur de contenu.](data-classification-content-explorer.md)

### <a name="activity-explorer"></a>Explorateur d’activités
L’Explorateur d’activités vous permet de surveiller ce qui est fait avec vos éléments sensibles classés et étiquetés dans :
- SharePoint
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

Pour obtenir des instructions pas à pas sur l’utilisation de l’Explorateur d’activités, voir Commencer [avec l’Explorateur d’activités.](data-classification-activity-explorer.md)

## <a name="next-steps"></a>Étapes suivantes

Maintenant que vous avez configuré les bases de la gestion de la conformité pour votre organisation, envisagez les solutions de conformité suivantes dans Microsoft 365 pour vous aider à protéger les informations sensibles, à détecter et à agir sur les risques internes supplémentaires.

### <a name="configure-retention-labels"></a>Configurer des étiquettes de rétention

Alors que les stratégies de rétention s’appliquent au niveau du conteneur à des emplacements tels que des sites SharePoint et des boîtes aux lettres [Exchange,](retention.md#retention-labels) les étiquettes de rétention permettent un ciblage plus spécifique pour vos stratégies de rétention et de suppression. Par exemple, au niveau du document ou du message électronique, que les utilisateurs finaux peuvent appliquer manuellement en plus de l’application automatique par les administrateurs. Vous pouvez également appliquer une étiquette de rétention à une bibliothèque de documents, un dossier ou un ensemble de documents dans SharePoint, afin que tous les documents stockés à cet emplacement héritent de l’étiquette de rétention par défaut.

En outre, les étiquettes de rétention prise [en charge la gestion des](records-management.md) enregistrements pour marquer le contenu en tant qu’enregistrement. Lorsque cela se produit, l’étiquette impose des restrictions supplémentaires sur le contenu qui peut être nécessaire pour aider votre organisation à se conformer aux exigences réglementaires.

Pour obtenir des instructions pas à pas pour créer et publier des étiquettes de rétention, consultez les instructions suivantes :
- [Créer des étiquettes de rétention et les appliquer dans les applications](create-apply-retention-labels.md)
- [Appliquer automatiquement une étiquette de rétention au contenu](apply-retention-labels-automatically.md)

Pour commencer à gérer les enregistrements, voir [Prise en charge de la gestion des enregistrements.](get-started-with-records-management.md)

### <a name="identify-and-define-sensitive-information-types"></a>Identifier et définir des types d’informations sensibles

Définir des types d’informations sensibles en fonction du modèle contenu dans les informations contenues dans les données de votre organisation. Les [types d’informations sensibles](./sensitive-information-type-entity-definitions.md) intégrés permettent d’identifier et de protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Vous pouvez également créer vos [propres types d’informations de sensibilité](create-a-custom-sensitive-information-type.md) personnalisés propres à votre organisation.

Pour obtenir des instructions pas à pas pour définir des types d’informations sensibles personnalisés, voir Créer un type d’informations sensibles personnalisé dans le Centre de sécurité [& conformité.](./create-a-custom-sensitive-information-type.md)

### <a name="prevent-data-loss"></a>Éviter les pertes de données

Les stratégies de protection contre la perte de données [(DLP)](dlp-learn-about-dlp.md) vous permettent d’identifier, de surveiller et de protéger automatiquement les informations sensibles au sein Microsoft 365 organisation. Utilisez les stratégies DLP pour identifier les éléments sensibles dans services Microsoft, empêcher le partage accidentel d’éléments sensibles et aider les utilisateurs à rester conformes sans interrompre leur flux de travail.

Pour obtenir des instructions pas à pas pour configurer des stratégies DLP, [créez, testez et régler une stratégie DLP.](create-test-tune-dlp-policy.md) Pour plus d’informations sur les licences de gestion des pertes de données, voir Microsoft 365 de gestion des [licences pour la sécurité & conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#office-365-data-loss-prevention-for-exchange-online-sharepoint-online-and-onedrive-for-business)

### <a name="detect-and-act-on-insider-risks"></a>Détecter les risques internes et agir sur ces risques

De plus en plus, les employés ont un accès croissant pour créer, gérer et partager des données sur un large éventail de plateformes et de services. Dans la plupart des cas, les organisations disposent de ressources et d’outils limités pour identifier et atténuer les risques à l’échelle de l’organisation, tout en respectant les exigences de conformité et les normes de confidentialité des employés. Ces risques peuvent inclure le vol de données par les employés qui quittent l’organisation et les fuites de données d’informations en dehors de votre organisation par un partage accidentel ou une intention malveillante.

[La gestion des](insider-risk-management-policies.md) risques internes dans Microsoft 365 utilise l’ensemble des indicateurs de service et tiers pour vous aider à identifier, trier et agir rapidement sur l’activité des utilisateurs à risque. À l’aide des journaux de Microsoft 365 et de Microsoft Graph, la gestion des risques internes vous permet de définir des stratégies spécifiques pour identifier les indicateurs de risque et prendre des mesures pour atténuer ces risques.

Pour obtenir des instructions pas à pas pour planifier et configurer des stratégies de gestion des risques internes, voir [Planifier](insider-risk-management-plan.md) la gestion des risques internes et prendre en charge la gestion [des risques internes.](insider-risk-management-configure.md) Pour plus d’informations sur les licences de gestion des risques internes, voir [Microsoft 365 licences pour la sécurité et & conformité.](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#insider-risk-management)