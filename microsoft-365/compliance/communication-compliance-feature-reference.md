---
title: Référence de la fonctionnalité de conformité des communications
description: Référence de la fonctionnalité de conformité de la communication dans Microsoft 365. Découvrez les détails et les spécifications de chacun des composants fonctionnels.
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.SupervisoryReview
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 757b1fcdae69e98ec45bb29e669ceda8f8cb8f98
ms.sourcegitcommit: fdb5f9d865037c0ae23aae34a5c0f06b625b2f69
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2020
ms.locfileid: "48131634"
---
# <a name="communication-compliance-feature-reference"></a>Référence de la fonctionnalité de conformité des communications

## <a name="policies"></a>Stratégies

>[!Important]
>L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité de communication Microsoft 365](https://compliance.microsoft.com/supervisoryreview).

Vous créez des stratégies de conformité des communications pour les organisations Microsoft 365 dans le Centre de conformité Microsoft 365. Les stratégies de conformité des communications définissent les communications et les utilisateurs qui font l’objet d’un examen au sein de votre organisation, définissent les conditions personnalisées auxquelles doivent répondre les communications et indiquent qui doit effectuer des révisions. Les utilisateurs auxquels le rôle d' *administrateur de conformité de communication* est affecté peuvent définir des stratégies, et toute personne disposant de ce rôle peut accéder à la page conformité de la **communication** et aux paramètres globaux dans le centre de conformité Microsoft 365. Si nécessaire, vous pouvez exporter l’historique des modifications apportées à une stratégie dans un fichier. csv qui inclut également l’état des alertes en attente de révision, des éléments escaladés et des éléments résolus. Les stratégies ne peuvent pas être renommées et peuvent être supprimées lorsqu’elles ne sont plus nécessaires.

>[!NOTE]
>Les stratégies de surveillance créées dans le centre de sécurité & conformité pour les abonnements Office 365 ne peuvent pas migrer vers Microsoft 365. Si vous effectuez une migration à partir d’un abonnement Office 365 vers un abonnement Microsoft 365, vous devrez créer de nouvelles stratégies de conformité de communication pour remplacer les stratégies de surveillance existantes.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de stratégie sont des paramètres de stratégie prédéfinis que vous pouvez utiliser pour créer rapidement des stratégies pour répondre aux scénarios de conformité courants. Chacun de ces modèles présente des différences dans les conditions et l’étendue, et tous les modèles utilisent les mêmes types de signaux d’analyse. Vous pouvez choisir parmi les modèles de stratégie suivants :

|**Catégorie**|**Modèle de stratégie**|**Détails**|
|:-----|:-----|:-----|
| **Langage offensant et blocage du harcèlement** | Surveiller les communications pour un langage offensant | -Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype entreprise <br> -Direction : entrant, sortant, interne <br> -Pourcentage de révision : 100% <br> -Conditions : classifieur de langue offensant |
| **Informations sensibles** | Surveiller les communications pour les informations sensibles | -Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype entreprise <br> -Direction : entrant, sortant, interne <br> -Pourcentage de révision : 10% <br> -Conditions : informations sensibles, modèles de contenu prédéfinis et types, option de dictionnaire personnalisé, pièces jointes dont la taille est supérieure à 1 Mo |
| **Conformité réglementaire** | Surveiller les communications pour les informations relatives à la conformité réglementaire financière | -Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype entreprise <br> -Direction : entrant, sortant <br> -Pourcentage de révision : 10% <br> -Conditions : option de dictionnaire personnalisé, pièces jointes d’une taille supérieure à 1 Mo |

## <a name="permissions-preview"></a>Autorisations (aperçu)

>[!Important]
>Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les rôles attribués au cours de cette étape sont obligatoires avant toute accessibilité des fonctionnalités de conformité de la communication.

Cinq groupes de rôles sont utilisés pour configurer les autorisations de gestion des fonctionnalités de conformité des communications. Pour que la conformité de la **communication** soit disponible sous la forme d’une option de menu dans le centre de conformité Microsoft 365 et pour poursuivre ces étapes de configuration, vous devez être affecté aux groupes de rôles de *conformité* de communication ou d' *administrateur de conformité* de communication. Pour accéder aux fonctionnalités de conformité de communication et les gérer une fois la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de conformité de communication.

En fonction de la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques. Vous pouvez attribuer à des groupes de rôles spécifiques des utilisateurs ayant des responsabilités différentes en matière de gestion des fonctionnalités de conformité des communications. Ou vous pouvez décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, investigateurs et visionneuses désignés au groupe de rôles de *conformité de communication* . Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux aux besoins de gestion de la conformité.

Sélectionnez l’une des options de groupe de rôles suivantes lors de la configuration de la conformité des communications :

|**Rôle**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité de la communication** | Utilisez ce groupe de rôles pour gérer la conformité des communications de votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, investigateurs et visionneuses désignés, vous pouvez configurer des autorisations de conformité de la communication dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité de communication. Cette configuration est la méthode la plus simple pour démarrer rapidement la conformité de la communication et convient aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité de communication** | Utilisez ce groupe de rôles pour configurer initialement la conformité de la communication et par la suite pour séparer les administrateurs de conformité des communications en un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité de communication, des paramètres globaux et des affectations de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies pour lesquelles ils sont affectés en tant que relecteurs, afficher les métadonnées de message (et non le contenu des messages), faire remonter aux relecteurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Investigation de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’investigations de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des relecteurs supplémentaires, passer à un cas avancé eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité de la communication** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui géreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de la conformité de la communication et peuvent afficher tous les rapports de conformité des communications. |

### <a name="for-organizations-using-the-original-permissions-and-role-groups"></a>Pour les organisations qui utilisent les autorisations d’origine et les groupes de rôles

La nouvelle structure de groupe de rôles remplace la structure de groupe de rôles initiale pour la conformité de la communication. Pour les organisations qui utilisent déjà la conformité de communication, vous devez disposer du rôle d’administrateur examen de surveillance pour commencer à respecter la conformité des communications dans le centre de conformité Microsoft 365. En outre, vous deviez créer un nouveau groupe de rôles pour les relecteurs avec l’administrateur de révision de surveillance, la gestion des cas, l’administrateur de conformité et les rôles d’examen pour examiner et corriger les messages avec des correspondances de stratégie. En gros, tous les administrateurs et relecteurs se trouvaient dans un seul groupe de rôles et tous disposent des mêmes autorisations d’accès et de gestion. Avec les mises à jour les plus récentes de la conformité de la communication, vous devez planifier la migration de la structure de groupe de rôles précédente vers la nouvelle structure de groupe de rôles. La prise en charge de la structure de groupe de rôles précédente sera progressive.

Pour faciliter la planification de la migration, prenez en compte l’exemple suivant. Vous disposez actuellement de trois types d’utilisateurs dans votre organisation, les administrateurs informatiques, le triage et les relecteurs. Ces trois types d’utilisateurs appartiennent à la structure de groupes de rôles précédente et sont tous membres d’un groupe de rôles unique avec les rôles suivants attribués :

- Administrateur de la vérification de surveillance
- Gestion des cas
- Administrateur de conformité
- Révision

Pour mettre à jour les rôles de ces utilisateurs pour la nouvelle structure de groupe de rôles, et pour séparer les autorisations d’accès et de gestion des utilisateurs, vous pouvez considérer trois nouveaux groupes et les nouvelles affectations de groupe de rôles associées :

- **Administrateurs informatiques**: attribué au nouveau groupe de rôles d' *administrateur de conformité de communication* .
- **Triage**: affecté au groupe de rôles *analyste de conformité des communications* .
- **Relecteurs**: affectés au nouveau groupe de rôles contrôle de *conformité de communication* .

## <a name="supervised-users"></a>Utilisateurs supervisés

Avant de commencer à utiliser la conformité des communications, vous devez déterminer qui a besoin de ses communications. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou groupes de personnes à superviser. Les groupes Microsoft 365, les listes de distribution Exchange, les communautés Yammer et les canaux Microsoft teams sont des exemples de ces groupes. Vous pouvez également exclure des utilisateurs ou des groupes spécifiques de l’analyse d’un groupe d’exclusion spécifique ou d’une liste de groupes.

>[!IMPORTANT]
>Les utilisateurs couverts par les stratégies de conformité des communications doivent disposer d’une licence de conformité Microsoft 365 E5, d’une licence Office 365 entreprise E3 avec le complément de conformité avancé ou être inclus dans un abonnement Office 365 entreprise E5. Si vous ne disposez pas d’un plan entreprise E5 existant et que vous souhaitez essayer la conformité de la communication, vous pouvez vous [inscrire pour obtenir une version d’évaluation d’Office 365 entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

## <a name="reviewers"></a>Relecteurs

Lorsque vous créez une stratégie de conformité de communication, vous devez déterminer qui révise les messages des utilisateurs supervisés. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou les groupes de personnes qui doivent réviser les communications contrôlées. Tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online et doivent être affectés aux rôles d' *enquête* de conformité de communication ou d' *analyse* de conformité des communications. Les relecteurs (analystes ou investigateurs) doivent également avoir le rôle de *gestion des cas de conformité de communication* affecté. Lorsque les relecteurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.

## <a name="groups-for-supervised-users-and-reviewers"></a>Groupes pour les utilisateurs et les relecteurs surveillés

Pour simplifier votre configuration, créez des groupes pour les personnes qui ont besoin de leurs communications et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous voulez analyser des communications entre deux groupes distincts de personnes, ou si vous voulez spécifier un groupe qui n’est pas supervisé.

Lorsque vous affectez un groupe de distribution dans la stratégie, la stratégie surveille tous les messages électroniques provenant de chaque utilisateur dans le groupe de distribution. Lorsque vous affectez un groupe Microsoft 365 dans la stratégie, la stratégie surveille tous les messages électroniques envoyés à ce groupe, et non les messages électroniques individuels reçus par chaque membre du groupe.

L’ajout de groupes et de listes de distribution aux stratégies de conformité des communications fait partie des conditions générales et de l’ensemble de règles, de sorte que le nombre maximal de groupes et de listes de distribution pris en charge par une stratégie varie en fonction du nombre de conditions également ajoutées à la stratégie. Chaque stratégie doit prendre en charge environ 20 groupes ou listes de distribution, en fonction du nombre de conditions supplémentaires présentes dans la stratégie.

## <a name="supported-communication-types"></a>Types de communications pris en charge

Avec les stratégies de conformité de communication, vous pouvez choisir d’analyser les messages d’une ou plusieurs des plateformes de communication suivantes en tant que groupe ou en tant que sources autonomes. Les communications capturées sur ces plateformes sont conservées pendant sept ans pour chaque stratégie par défaut, même si les utilisateurs quittent votre organisation et que leurs boîtes aux lettres sont supprimées.

- **Microsoft teams**: les communications de conversation dans les canaux Microsoft teams publics et privés, ainsi que dans les conversations individuelles, peuvent être analysées. Lorsque des utilisateurs sont affectés à une stratégie de conformité de communication lorsque la couverture Microsoft teams est sélectionnée, les communications de conversation pour les utilisateurs sont automatiquement analysées sur toutes les équipes Microsoft teams dont les utilisateurs sont membres. La couverture Microsoft teams est automatiquement incluse pour les modèles de stratégie prédéfinis et est sélectionnée par défaut dans le modèle de stratégie personnalisé. Les conversations de teams correspondant à des conditions de stratégie de conformité de communication peuvent prendre jusqu’à 24 heures pour être traitées. Utilisez les configurations de gestion de groupe suivantes pour superviser les conversations des utilisateurs individuels et les communications de canal dans teams :

    - **Pour les communications de conversation de teams :** Affectez des utilisateurs individuels ou affectez un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.
    - **Pour les communications de canal teams :** Affectez à chaque canal Microsoft teams ou groupe Microsoft 365 que vous souhaitez analyser, qui contient un utilisateur spécifique à la stratégie de conformité de communication. Si vous ajoutez le même utilisateur à d’autres canaux Microsoft Teams ou à des groupes Microsoft 365, veillez à ajouter ces nouveaux canaux et groupes à la stratégie de conformité des communications.
    - **Pour les communications de conversation avec des environnements de messagerie hybrides**: la conformité des communications permet de surveiller les messages de conversation pour les utilisateurs des organisations disposant d’un déploiement local Exchange ou d’un fournisseur de messagerie externe ayant activé Microsoft Teams. Vous devez créer un groupe de distribution pour les utilisateurs disposant de boîtes aux lettres locales ou externes à surveiller. Lors de la création d’une stratégie de conformité de communication, vous affectez ce groupe de distribution à la sélection **utilisateurs et groupes surveillés** dans l’Assistant stratégie.

    >[!IMPORTANT]
    >Vous devez classer une demande auprès du support Microsoft pour permettre à votre organisation d’utiliser l’interface utilisateur graphique dans le centre de sécurité & conformité afin de rechercher des données de conversation teams pour les utilisateurs locaux. Pour plus d’informations, reportez-vous à la rubrique [recherche de boîtes aux lettres en nuage pour les utilisateurs locaux](search-cloud-based-mailboxes-for-on-premises-users.md).

Vous devez effectuer une demande auprès du Support Microsoft pour autoriser votre organisation à utiliser l’interface utilisateur graphique dans le centre de conformité et sécurité pour rechercher des équipes dans les boîtes aux lettres en ligne des utilisateurs locaux.

- **Messagerie Exchange**: les boîtes aux lettres hébergées sur Exchange Online dans le cadre de votre abonnement Microsoft 365 ou Office 365 sont toutes éligibles pour l’analyse des messages. Les messages électroniques et les pièces jointes Exchange correspondant à des conditions de stratégie de conformité de communication peuvent mettre jusqu’à 24 heures pour être traités. Les types de pièces jointes prises en charge pour la conformité des communications sont les mêmes que les [types de fichiers pris en charge pour les inspections du contenu des règles de flux de messagerie Exchange](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

- **Yammer**: les messages privés, les conversations publiques et les pièces jointes associées dans les communautés Yammer peuvent être analysés. Lorsqu’un utilisateur est ajouté à la stratégie de conformité de communication qui inclut Yammer comme canal défini, les communications entre toutes les communautés Yammer dont l’utilisateur est membre sont incluses dans le processus d’analyse. Les conversations et les pièces jointes Yammer correspondant à des conditions de stratégie de conformité de communication peuvent prendre jusqu’à 24 heures pour être traitées. Yammer doit être en [mode natif](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode) pour les stratégies de conformité de communication afin de surveiller les communications et les pièces jointes Yammer. En mode natif, tous les utilisateurs de Yammer se trouvent dans Azure Active Directory (AAD), tous les groupes sont des Groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online.

- **Skype Entreprise Online** :Les communications de conversation et les pièces jointes associées dans Skype Entreprise Online peuvent être supervisées. Les conversations Skype Entreprise Online correspondant aux conditions de la stratégie de conformité des communications peuvent prendre jusqu’à 24 heures. Les conversations de conversation surveillées proviennent de [conversations précédentes enregistrées dans Skype entreprise Online](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  Utilisez la configuration de gestion de groupe suivante pour superviser les communications de conversation des utilisateurs dans Skype entreprise Online :

    - **Pour les communications de conversation de Skype entreprise Online**: affectez des utilisateurs individuels ou affectez un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.

- **Sources tierces** : vous pouvez analyser les communications provenant de sources tierces pour les données importées dans les boîtes aux lettres de votre organisation Microsoft 365. Les connecteurs prennent en charge les ressources tierces suivantes :

    - [Instant Bloomberg](archive-instant-bloomberg-data.md)
    - [Message Bloomberg](archive-bloomberg-message-data.md)
    - [Conversation ICE](archive-icechat-data.md)

Vous devez configurer un connecteur tiers pour votre organisation Microsoft 365 avant de pouvoir attribuer le connecteur à une stratégie de conformité de communication. La section **sources tierces** de l’Assistant stratégie de conformité des communications affiche uniquement les connecteurs tiers actuellement configurés.

## <a name="transitioning-from-supervision-in-office-365"></a>Transition de la surveillance dans Office 365

Les organisations qui utilisent des stratégies de surveillance dans Office 365 et qui envisagent de passer aux stratégies de conformité des communications dans Microsoft 365 doivent comprendre les points importants suivants :

- Les deux solutions peuvent être utilisées côte à côte au sein de votre organisation, mais les stratégies utilisées dans chaque solution doivent avoir des noms de stratégie uniques. Les groupes et les dictionnaires de mots clés personnalisés peuvent être partagés entre les solutions pendant une période de transition.
- Les messages enregistrés en supervision dans Office 365 les correspondances de stratégie ne peuvent pas être déplacés ou partagés dans la conformité de communication dans Microsoft 365.
- La solution de supervision dans Office 365 sera entièrement remplacée par la solution de conformité de la communication dans Microsoft 365. Nous vous recommandons de créer de nouvelles stratégies dans la conformité de la communication avec les mêmes paramètres que les stratégies de surveillance existantes pour utiliser les améliorations apportées à l’enquête et aux corrections correctives. Lors de la transition vers la conformité des communications dans Microsoft 365, vous devez planifier l’exportation de données de rapport de supervision dans Office 365 si vous avez des exigences de stratégie de rétention de conformité internes.

Pour plus d’informations sur la retraite de la surveillance dans Office 365, consultez la feuille de [route de Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour plus de détails.

## <a name="policy-settings"></a>Paramètres de stratégie

### <a name="users"></a>Utilisateurs

Vous avez la possibilité de sélectionner **tous les utilisateurs** ou de définir des utilisateurs spécifiques dans une stratégie de conformité de communication. La sélection de **Tous les utilisateurs** applique la stratégie à tous les utilisateurs et les groupes auxquels n’importe quel utilisateur est inclus en tant que membre. La définition d’utilisateurs spécifiques applique la stratégie aux utilisateurs définis et aux groupes auxquels les utilisateurs définis sont inclus.

### <a name="direction"></a>Direction

Par défaut, la **direction est** la condition est affichée et ne peut pas être supprimée. Les paramètres de direction de communication d’une stratégie sont choisis individuellement ou ensemble :

- **Entrant**: vous pouvez choisir **entrant** pour examiner les communications envoyées **aux** personnes que vous avez choisies de superviser.
- **Sortant**: vous pouvez choisir **sortant** si vous souhaitez consulter les communications envoyées **par** les personnes que vous avez choisies de superviser.
- **Internal**: vous pouvez choisir **Internal** pour examiner les communications envoyées **entre** les personnes que vous avez identifiées dans la stratégie.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous pouvez inclure des types d’informations sensibles dans le cadre de votre stratégie de conformité de communication. Les types d’informations sensibles sont des types de données prédéfinis ou personnalisés qui peuvent vous aider à identifier et à protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, et bien plus encore. Dans le cadre de [protection contre la perte de données (DLP)](data-loss-prevention-policies.md), la configuration des informations sensibles peut utiliser les modèles, la proximité des caractères, les niveaux de confiance, et même les types de données personnalisés pour vous aider à identifier et signaler le contenu sensible. Les types d’informations sensibles par défaut sont les suivants :

- Financier
- Médecine et santé
- Confidentialité
- Type d’informations personnalisées

Pour en savoir plus sur les détails des informations sensibles et les modèles inclus dans les types par défaut, consultez la rubrique [informations sensibles](sensitive-information-type-entity-definitions.md)sur les définitions d’entités.

### <a name="custom-keyword-dictionaries"></a>Dictionnaires de mots clés personnalisés

Configurez des dictionnaires de mots clés personnalisés (ou des lexiques) pour fournir une gestion simple des mots clés propres à votre organisation ou votre secteur d’activité. Les dictionnaires de mots clés prennent en charge jusqu’à 100 Ko de termes (post-compression) dans le dictionnaire et prennent en charge n’importe quelle langue. La limite client est également de 100 Ko après la compression. Si nécessaire, vous pouvez appliquer plusieurs dictionnaires de mots clés personnalisés à une seule stratégie ou disposer d’un dictionnaire à Mots clés unique par stratégie. Ces dictionnaires sont affectés dans une stratégie de conformité de communication et peuvent être issus d’un fichier (par exemple, une liste. csv ou. txt) ou d’une liste que vous pouvez [importer dans le centre de conformité](create-a-keyword-dictionary.md). Utilisez des dictionnaires personnalisés lorsque vous devez prendre en charge des termes ou des langues propres à votre organisation et à vos stratégies.

### <a name="classifiers"></a>Classifieurs requêtes

Les classifieurs intégrés et globaux analysent les messages envoyés ou reçus sur tous les canaux de communication de votre organisation en fonction de différents types de problèmes de conformité. Les classifieurs utilisent une combinaison d'intelligence artificielle et de mots clés pour identifier le langage dans les messages susceptibles d'enfreindre les stratégies anti-harcèlement. Les classifieurs intégrés prennent actuellement en charge uniquement les mots clés anglais dans les messages.

Conformité des communications les classifieurs intégrés et les classifieurs globaux analysent les communications pour les termes, les images et les sentiments pour les types de langue et de contenu suivants :

- **Menace**: analyse les menaces pour valider la violence ou nuire physiquement à une personne ou à une propriété.
- **Harcèlement ciblé**: analyse les comportements offensants ciblant les personnes en matière de race, de couleur, de religion et d’origine nationale.
- **Blasphèmes**: analyse les expressions à inconvenances qui dépassent la plupart des gens.
- **Images pour adultes**: recherche des images sexuellement explicites.
- **Images Racy**: recherche des images sexuellement à l’esprit, mais qui contiennent moins de contenu explicite que les images considérées comme adultes.
- **Images Gory**: recherche les images qui décrivent la violence et Gore.

Les classifieurs d’image *adulte*, *Racy*et *Gory* analysent les fichiers dans. JPEG,. PNG,. GIF et. Formats BMP. La taille des fichiers image doit être inférieure à 4 méga-octets (Mo) et les dimensions des images doivent être supérieures à 50x50 pixels et supérieures à 50 kilo-octets (Ko) pour que l’image soit considérée comme étant à évaluer. L’identification de l’image est prise en charge pour les messages électroniques Exchange Online, ainsi que pour les canaux et conversations Microsoft Teams.

Les classifieurs intégrés et globaux ne fournissent pas une liste exhaustive des termes ou des images de ces zones. De plus, les normes linguistiques et culturelles changent en permanence, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour les classifieurs à sa discrétion. Alors que les classifieurs peuvent aider votre organisation à surveiller ces domaines, les classifieurs ne sont pas destinés à fournir les moyens exclusifs de surveillance ou d’adressage de cette langue ou de cette image. Votre organisation, et non Microsoft, reste responsable de toutes les décisions liées à l’analyse et au blocage de la langue et des images dans ces domaines.

Pour plus d’informations sur les classifieurs de formation dans Microsoft 365, voir [Getting Started with trainable Classifiers](classifier-get-started-with.md).

### <a name="conditional-settings"></a>Paramètres conditionnels
<a name="ConditionalSettings"> </a>

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications à partir de la messagerie et des sources tierces de votre organisation (par exemple, la notification instantanée ou la messagerie instantanée).

Le tableau suivant décrit plus en plus de chaque condition.
  
|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le contenu correspond à l’un de ces classifieurs** | S’appliquer à la stratégie lorsqu’un classifieur est inclus ou exclu d’un message. Certains classifieurs sont prédéfinis dans votre client et les classifieurs personnalisés doivent être configurés séparément avant d’être disponibles pour cette condition. Un seul classifieur peut être défini en tant que condition dans une stratégie. Pour plus d’informations sur la configuration des classifieurs, voir [en savoir plus sur les classifieurs de formation (aperçu)](classifier-learn-about.md). |
| **Le contenu contient l’un de ces types d’informations sensibles** | S’appliquent à la stratégie lorsque des types d’informations sensibles sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre client, et les classifieurs personnalisés peuvent être configurés séparément ou dans le cadre du processus d’attribution de la condition. Chaque type d’informations sensibles que vous choisissez est appliqué séparément et un seul de ces types d’informations sensibles doit s’appliquer pour la stratégie à appliquer au message. Pour plus d’informations sur les types d’informations sensibles personnalisés, consultez la rubrique [Custom sensitive types information](custom-sensitive-info-types.md). |
| **Un message est reçu à partir de l’un de ces domaines**  <br><br> **Le message n’est reçu à partir d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages reçus. Entrez chaque domaine ou adresse de messagerie et séparez les domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie entré est appliqué séparément, un seul domaine ou une seule adresse de messagerie doit s’appliquer pour la stratégie à appliquer au message. <br><br> Si vous souhaitez analyser tous les messages électroniques à partir d’un domaine spécifique, tout en excluant les messages qui n’ont pas besoin d’être réexaminés (bulletins d’information, annonces, etc.), vous devez configurer un **message n’est reçu à partir d’aucun de ces domaines** , qui exclut l’adresse de messagerie (par exemple « Newsletter@contoso.com »). |
| **Un message est envoyé à l’un de ces domaines**  <br><br> **Le message n’est pas envoyé à l’un de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages envoyés. Entrez chaque domaine ou adresse de messagerie et séparez les domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie est appliqué séparément, un seul domaine ou une seule adresse de messagerie doit s’appliquer pour la stratégie à appliquer au message. <br><br> Si vous souhaitez analyser tous les messages électroniques envoyés à un domaine spécifique, tout en excluant les messages envoyés qui n’ont pas besoin d’être examinés, vous devez configurer deux conditions : <br> -Un **message est envoyé à l’un de ces domaines** qui définit le domaine (« contoso.com »), et <br> -Un **message n’est pas envoyé à l’un de ces domaines** , qui exclut l’adresse de messagerie (« Subscriptions@contoso.com »). |
| **Le message est classé avec l’une de ces étiquettes**  <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Pour appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour la stratégie à appliquer au message). Pour plus d’informations sur les étiquettes de rétention, voir [en savoir plus sur les stratégies de rétention et les étiquettes de conservation](retention.md).|
| **Le message contient l’un de ces mots**  <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets pour encadrer l’expression. Chaque mot ou phrase que vous entrez est appliqué séparément (un seul mot doit obligatoirement s’appliquer à la stratégie à appliquer au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **La pièce jointe contient l’un de ces mots**  <br><br> **La pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans une pièce jointe (par exemple, un document Word), entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets pour encadrer l’expression. Chaque mot ou phrase que vous entrez est appliqué séparément (un seul mot doit obligatoirement s’appliquer à la stratégie à appliquer à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **La pièce jointe est l’un de ces types de fichiers**  <br><br> **Aucune de ces types de fichiers n’est associée à la pièce jointe** | Pour superviser les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichiers (par exemple,. exe ou. pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichiers, entrez-les sur des lignes distinctes. Une seule extension de pièce jointe doit correspondre pour que la stratégie s’applique.|
| **La taille du message est supérieure à**  <br><br> **La taille du message n’est pas supérieure à** | Pour examiner les messages en fonction d’une certaine taille, utilisez les conditions suivantes pour spécifier la taille maximale ou minimale qu’un message peut contenir avant d’être soumis à révision. Par exemple, si vous spécifiez une **taille de message supérieure à** \> **1,0 Mo**, tous les messages de 1,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La taille de la pièce jointe est supérieure à**  <br><br> **La pièce jointe n’est pas supérieure à** | Pour examiner les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale qu’une pièce jointe peut contenir avant que le message et ses pièces jointes soient soumis à révision. Par exemple, si vous spécifiez une **taille de pièce jointe supérieure** à \> **2,0 Mo**, tous les messages avec des pièces jointes 2,01 Mo et supérieures sont soumis à la révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
   
#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes
<a name="Matchwords"> </a>

Chaque mot que vous entrez et séparé par une virgule est appliqué séparément (un seul mot doit obligatoirement s’appliquer à la condition de stratégie à appliquer à la messagerie ou à la pièce jointe). Par exemple, nous utilisons la condition, le **message contient l’un de ces mots**, avec les mots-clés « Banker », « Confidential » et « Insider Insider » séparé par une virgule (Banker, Confidential, « negociation d’initié »). La stratégie s’applique aux messages qui incluent le mot « Banker », « Confidential » ou l’expression « negociation Insiders ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots contenus dans le message ou dans la pièce jointe doivent correspondre exactement à ce que vous entrez.

>[!IMPORTANT]
>Lors de l’importation d’un fichier de dictionnaire personnel, chaque mot ou expression doit être séparé par un retour chariot et sur une ligne distincte. <br> Par exemple : <br><br>
>*bancaire* <br>
>*Divulguer* <br>
>*commerce d’initié*

Pour analyser les messages électroniques et les pièces jointes des mêmes mots clés, créez une [stratégie de protection contre la perte de données](create-test-tune-dlp-policy.md) avec un dictionnaire de [Mots clés personnalisé](create-a-keyword-dictionary.md) pour les termes que vous souhaitez analyser dans les messages. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **ou** dans la pièce jointe du courrier électronique. L’utilisation des paramètres de stratégie conditionnelle standard (le*message contient l’un de ces mots* et la *pièce jointe contient l’un de ces mots*) pour identifier les termes dans les messages et dans les pièces jointes exige que les termes soient **présents dans le** message et la pièce jointe.
  
#### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer le moment auquel la stratégie de conformité des communications doit être appliquée aux éléments de communication. Lorsque vous configurez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « commercial » et qu’il est supérieur à 2 Mo. Toutefois, si le message contient également les mots « approuvé par Contoso Financial », la stratégie ne doit pas s’appliquer. Dans cet exemple, les trois conditions suivantes sont définies comme suit :
  
- Le **message contient l’un de ces mots**, avec le mot clé « Trade »
- La **taille du message est supérieure à**, avec la valeur 2 Mo
- Le **message ne contient aucun de ces mots**, avec les mots-clés « approuvé par l’équipe financière de contoso »

### <a name="review-percentage"></a>Vérifier le pourcentage

Si vous souhaitez réduire la quantité de contenu à réviser, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de conformité de communication. Un échantillon aléatoire de contenu est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les réviseurs examinent tous les éléments, vous pouvez configurer **100 %** dans une stratégie de conformité des communications.

## <a name="privacy-preview"></a>Confidentialité (préversion)

La protection de la confidentialité des utilisateurs qui ont des correspondances de stratégie est importante et peut contribuer à promouvoir l’objection en matière d’analyse des données et de révision des alertes de conformité des communications. Ce paramètre s’applique uniquement aux noms d’utilisateurs qui affichent la solution de conformité de communication. Elle n’affecte pas le mode d’affichage des noms dans les autres solutions de conformité ou le centre d’administration.

Pour les utilisateurs disposant d’une correspondance de conformité de communication, vous pouvez choisir l’un des paramètres suivants dans les **paramètres de conformité de communication**:

- **Afficher les versions anonymes des**noms d’utilisateur : les noms d’utilisateur sont rendus anonymes pour empêcher les administrateurs, les analystes, les enquêteurs de données et les relecteurs de voir qui est associé à des alertes de stratégie. Par exemple, un utilisateur « gracieuses Taylor » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans tous les domaines de l’expérience de conformité des communications. Le choix de ce paramètre permet d'anonymiser tous les utilisateurs ayant des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans les détails de l’alerte de conformité des communications ne seront pas disponibles lorsque cette option est sélectionnée. Toutefois, les noms d’utilisateur sont affichés lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateur sont affichés pour tous les utilisateurs qui ont des correspondances de stratégie actuelle ou passée.
- **Ne pas afficher les versions anonymes des**noms d’utilisateur : les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelle et passée pour les alertes de conformité de communication. Les informations de profil utilisateur (nom, titre, alias, organisation ou service) sont affichées pour l’utilisateur pour toutes les alertes de conformité de communication.

## <a name="notice-templates"></a>Modèles de notifications

Vous pouvez créer des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par courrier électronique pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse de messagerie de l’utilisateur associée à la correspondance de stratégie qui a généré l’alerte spécifique pour correction. Lors de la sélection d’un modèle d’avis à appliquer à une violation de stratégie dans le cadre du flux de travail de correction, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou de remplacer les champs selon vos besoins.

Les modèles de notifications sont des modèles de courrier électronique personnalisés dans lesquels vous pouvez définir les champs de message suivants dans la zone **paramètres de conformité** de la communication :

|**Field**|**Obligatoire**| **Détails** |
|:-----|:-----|:-----|
|**Nom du modèle** | Oui | Nom convivial du modèle d’avis que vous sélectionnerez dans le flux de travail de notification lors de la correction, prend en charge les caractères de texte. |
| **Adresse de l’expéditeur** | Oui | Adresse d’un ou de plusieurs utilisateurs ou groupes qui envoient le message à l’utilisateur avec une correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement. |
| **Adresses CC et CCI** | Non | Les utilisateurs ou groupes facultatifs devant être avertis de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement. |
| **Subject** | Oui | Informations qui s’affichent dans la ligne d’objet du message, prend en charge les caractères de texte. |
| **Corps du message** | Oui | Informations qui s’affichent dans le corps du message, prend en charge le texte ou les valeurs HTML. |

### <a name="html-for-notices"></a>HTML pour les notifications

Si vous souhaitez créer un message électronique en texte simple pour les notifications, vous pouvez créer un message plus détaillé à l’aide du code HTML dans le champ corps du message d’un modèle de notification. L’exemple suivant fournit le format du corps des messages pour un modèle de notification par courrier électronique HTML de base :

```HTML
<!DOCTYPE html>
<html>
    <body>
        <h2>Action Required: Contoso Employee Code of Conduct Policy Training</h2>
        <p>A recent message you've sent has generated a policy alert for the Contoso Employee <a href='https://www.contoso.com'>Code of Conduct Policy</a>.</p>
        <p>You are required to attend the Contoso Employee Code of Conduct <a href='https://www.contoso.com'>training</a> within the next 14 days. Please contact <a href='mailto:hr@contoso.com'>Human Resources</a> with any questions about this training request.</p>
        <p>Thank you,</p>
        <p><em>Human Resources</em></p>
    </body>
</html>
```

>[!NOTE]
>L’implémentation de l’attribut HTML href dans les modèles de notification de conformité des communications prend actuellement en charge uniquement les guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="filters"></a>Filtres

Les filtres de conformité de la communication vous permettent de filtrer et de trier les messages d’alerte pour des actions plus rapides d’enquête et de correction. Le filtrage est disponible sur les onglets **en attente** et **résolus** pour chaque stratégie. Pour enregistrer un filtre ou un jeu de filtres en tant que requête de filtre enregistrée, une ou plusieurs valeurs doivent être configurées en tant que sélections de filtre. Le tableau suivant présente les détails des filtres :

|**Filter**|**Détails**|
|:-----|:-----|
| **Date** | Date à laquelle le message a été envoyé ou reçu par un utilisateur au sein de votre organisation. |
| **Classe file** | Classe du message en fonction du type de message, qu’il *s’agisse d’un message ou* d’une *pièce jointe*. |
| **Avec pièce jointe** | Présence d’une pièce jointe dans le message. |
| **Classe d’élément** | Source du message en fonction du type de message, de la messagerie électronique, de la conversation Microsoft Team, Bloomberg, etc. Pour plus d’informations sur les types d’éléments communs et les classes de message, voir [Item Types and message classes](https://docs.microsoft.com/office/vba/outlook/concepts/forms/item-types-and-message-classes). |
| **Domaines de destinataires** | Domaine auquel le message a été envoyé. Ce domaine est normalement votre domaine d’abonnement Microsoft 365 par défaut. |
| **Destinataire** | Utilisateur auquel le message a été envoyé. |
| **Sender** | La personne qui a envoyé le message. |
| **Domaine de l’expéditeur** | Le domaine qui a envoyé le message. |
| **Taille** | Taille du message en Ko. |
| **Subject/title** | Objet du message ou titre de conversation. |
| **Tags** | Les balises affectées à un message, qu’elles soient *douteuses*, *conformes*ou *non conformes*. |
| **Transmis à** | Nom d’utilisateur de la personne incluse dans le cadre d’une action de réaffectation de message. |
| **Classifieurs requêtes** | Nom des classifieurs intégrés et personnalisés qui s’appliquent au message. Certains exemples incluent un *langage offensant*, un *harcèlement ciblé*, un *blasphème*, une *menace*, etc.

## <a name="alert-policies"></a>Stratégies d’alerte

Une fois que vous avez configuré une stratégie, une stratégie d’alerte correspondante est automatiquement créée et des alertes sont générées pour les messages qui répondent aux conditions définies dans la stratégie. Par défaut, toutes les stratégies correspondent aux déclencheurs d’alerte dont le niveau de gravité est moyen dans la stratégie d’alerte associée. Des alertes sont générées pour une stratégie de conformité des communications une fois que le niveau de seuil de déclenchement d’agrégation est atteint dans la stratégie d’alerte associée.

Pour les stratégies de conformité de communication, les valeurs de stratégie d’alerte suivantes sont configurées par défaut :

|**Déclencheur de stratégie d’alerte**|**Valeur par défaut**|
|:-----|:-----|
| Aggregat | Agrégation simple |
| Seuil | 4 activités |
| Fenêtre | 60 minutes |

>[!Note]
>Les paramètres de déclenchement de seuil de stratégie d’alerte pour les activités prennent en charge une valeur minimale de 3 ou supérieure pour les stratégies de conformité de communication.

Vous pouvez modifier les paramètres par défaut des déclencheurs sur le nombre d’activités, la période pour les activités et les utilisateurs spécifiques des stratégies d’alerte sur la page **stratégies d’alerte** dans le centre de sécurité & conformité.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Modifier le niveau de gravité pour une stratégie d’alerte

Si vous souhaitez modifier le niveau de gravité affecté dans une stratégie d’alerte pour une stratégie de conformité de communication spécifique, procédez comme suit :

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **stratégies**.

3. Sélectionnez **alerte Office 365** sur la page **stratégies** pour ouvrir la page **stratégies d’alerte** dans le centre de **sécurité & de sécurité Office 365**.

4. Cochez la case correspondant à la stratégie de conformité de communication que vous souhaitez mettre à jour, puis sélectionnez **modifier la stratégie**.

5. Sous l’onglet **Description** , sélectionnez la liste déroulante **gravité** pour configurer le niveau d’alerte de stratégie.

6. Sélectionnez **Enregistrer** pour appliquer le nouveau niveau de gravité à la stratégie.

7. Sélectionnez **Fermer** pour quitter la page Détails de la stratégie d’alerte.

## <a name="power-automate-flows-preview"></a>Flux d’automates d’alimentation (aperçu)

[Microsoft Power automate](https://docs.microsoft.com/power-automate/getting-started) est un service de flux de travail qui automatise les actions entre les applications et les services. En utilisant des flux provenant de modèles ou créés manuellement, vous pouvez automatiser les tâches courantes associées à ces applications et services. Lorsque vous activez la mise à l’arrêt automatique des flux pour la conformité de la communication, vous pouvez automatiser des tâches importantes pour les alertes et les utilisateurs. Vous pouvez configurer la gestion de l’alimentation automatique des flux pour avertir les responsables lorsque les utilisateurs ont des alertes de conformité et d’autres applications.

Les clients disposant d’abonnements Microsoft 365 qui incluent la conformité aux communications n’ont pas besoin de puissance automatique supplémentaire pour utiliser le modèle automate de conformité de la conformité recommandé par défaut. Le modèle par défaut peut être personnalisé pour prendre en charge votre organisation et les scénarios principaux de conformité de communication. Si vous choisissez d’utiliser les fonctionnalités de Power automate Premium dans ces modèles, créez un modèle personnalisé à l’aide du connecteur Microsoft 365 Compliance Connector ou utilisez Power automates pour d’autres zones de conformité dans Microsoft 365, vous aurez peut-être besoin d’une alimentation automatique supplémentaire.

![Mise en conformité de la communication automate](../media/communication-compliance-power-automate.png)

Le modèle automate d’alimentation suivant est fourni aux clients pour prendre en charge l’automatisation des processus pour les alertes de conformité de communication :

- **Avertir le gestionnaire lorsqu’un utilisateur a une alerte de conformité de communication**: il se peut que certaines organisations doivent avoir une notification de gestion immédiate lorsqu’un utilisateur a une alerte de conformité de communication. Lorsque ce flux est configuré et sélectionné, le responsable de l’utilisateur du cas reçoit un message électronique contenant les informations suivantes sur toutes les alertes :
    - Stratégie applicable pour l’alerte
    - Date/heure de l’alerte
    - Niveau de gravité de l’alerte

### <a name="create-a-power-automate-flow"></a>Création d’un flux automatique de puissance

Pour créer un flux Automated Power Up à partir d’un modèle recommandé par défaut, vous devez utiliser l’option **gérer les flux d’alimentation** automatique à partir du contrôle **automatiser** lorsque vous travaillez directement dans une alerte. Pour créer un flux automatique de puissance avec **gestion**de l’alimentation automatique, vous devez être membre d’au moins un groupe de rôles de conformité de communication.

Procédez comme suit pour créer un flux automatique d’alimentation à partir d’un modèle par défaut :

1. Dans le centre de conformité Microsoft 365, accédez à stratégies de **conformité des communications**  >  **Policies** et sélectionnez la stratégie avec l’alerte que vous souhaitez consulter.
2. Dans la stratégie, sélectionnez l’onglet **en attente** et sélectionnez une alerte en attente.
3. Sélectionnez **automate d’alimentation** dans le menu action d’alerte.
4. Sur la page **automatiser** , sélectionnez un modèle par défaut dans la section **modèles de conformité des communications** de la page.
5. Le flux répertorie les connexions incorporées nécessaires pour le flux et s’affiche si les États de connexion sont disponibles. Si nécessaire, mettez à jour toutes les connexions qui ne sont pas affichées comme disponibles. Sélectionnez **Continuer**.
6. Par défaut, les flux recommandés sont préconfigurés avec les champs de données de conformité de communication recommandés et de service Microsoft 365 requis pour effectuer la tâche attribuée au flux. Si nécessaire, personnalisez les composants de flux à l’aide du contrôle **afficher les options avancées** et en configurant les propriétés disponibles pour le composant de flux.
7. Si nécessaire, ajoutez des étapes supplémentaires au flux en sélectionnant le bouton **nouvelle étape** . Dans la plupart des cas, cette modification n’est pas nécessaire pour les modèles par défaut recommandés.
8. Sélectionnez **Enregistrer brouillon** pour enregistrer le flux pour une configuration ultérieure, ou sélectionnez **Enregistrer** pour terminer la configuration du flux.
9. Sélectionnez **Fermer** pour revenir à la page flux automatique de l’alimentation. Le nouveau modèle est affiché sous la forme d’un flux sous l’onglet **mes flux** et est automatiquement disponible à partir du contrôle Power automate de l’utilisateur qui a créé le flux lorsque vous travaillez avec des alertes de conformité de communication.

### <a name="share-a-power-automate-flow"></a>Partager un flux de puissance automatique

Par défaut, les flux d’alimentation automatique automatiques créés par un utilisateur sont uniquement disponibles pour cet utilisateur. Pour que d’autres utilisateurs de conformité de communication aient accès et utilisent un flux, le flux doit être partagé par le créateur du flux. Pour partager un flux, vous devez utiliser le contrôle **automate Power** lorsque vous travaillez directement dans une alerte.

Pour partager un flux d’alimentation automatique, vous devez être membre d’au moins un groupe de rôles de conformité de communication.
Procédez comme suit pour partager un flux automatique de puissance :

1. Dans le centre de conformité Microsoft 365, accédez à stratégies de **conformité des communications**  >  **Policies** et sélectionnez la stratégie avec l’alerte que vous souhaitez consulter.
2. Dans la stratégie, sélectionnez l’onglet **en attente** et sélectionnez une alerte en attente.
3. Sélectionnez **automate d’alimentation** dans le menu action d’alerte.
4. Sur la page flux automatique de l' **alimentation** , sélectionnez l’onglet **mes flux** ou flux d' **équipe** .
5. Sélectionnez le flux à partager, puis sélectionnez **partager** dans le menu options de flux.
6. Dans la page partage de flux, entrez le nom de l’utilisateur ou du groupe que vous souhaitez ajouter en tant que propriétaire pour le flux.
7. Dans la boîte de dialogue **connexion utilisée** , sélectionnez **OK** pour confirmer que l’utilisateur ou le groupe ajouté aura un accès total au flux.

### <a name="edit-a-power-automate-flow"></a>Modifier un flux d’alimentation automatique

Si vous avez besoin de modifier un flux, vous utiliserez le contrôle **automate Power** lorsque vous travaillerez directement dans une alerte. Pour modifier un flux d’automate de gestion de l’alimentation, vous devez être membre d’au moins un groupe de rôles de conformité de communication.

Pour modifier un flux automatique, procédez comme suit :

1. Dans le centre de conformité Microsoft 365, accédez à stratégies de **conformité des communications**  >  **Policies** et sélectionnez la stratégie avec l’alerte que vous souhaitez consulter.
2. Dans la stratégie, sélectionnez l’onglet **en attente** et sélectionnez une alerte en attente.
3. Sélectionnez **automate d’alimentation** dans le menu action d’alerte.
4. Sur la page flux automatique de l' **alimentation** , sélectionnez flux à modifier. Sélectionnez **modifier** dans le menu contrôle de flux.
5. Sélectionnez les **ellipsis**  >  **paramètres** de sélection pour modifier un paramètre de composant de flux ou supprimer des **points de suspension**  >  **Delete** pour supprimer un composant de flux.
6. Sélectionnez **Enregistrer** , puis **Fermer** pour terminer la modification du flux.

### <a name="delete-a-power-automate-flow"></a>Supprimer un flux d’alimentation automatique

Si vous devez supprimer un flux, vous devez utiliser le contrôle **automate Power** lorsque vous travaillez directement dans une alerte. Pour supprimer un flux d’alimentation automatique, vous devez être membre d’au moins un groupe de rôles de conformité de communication.

Procédez comme suit pour supprimer un flux automatique de puissance :

1. Dans le centre de conformité Microsoft 365, accédez à stratégies de **conformité des communications**  >  **Policies** et sélectionnez la stratégie avec l’alerte que vous souhaitez consulter.
2. Dans la stratégie, sélectionnez l’onglet **en attente** et sélectionnez une alerte en attente.
3. Sélectionnez **automate d’alimentation** dans le menu action d’alerte.
4. Sur la page flux automatique de l' **alimentation** , sélectionnez flux à supprimer. Sélectionnez **supprimer** dans le menu contrôle de flux.
5. Dans la boîte de dialogue de confirmation de suppression, sélectionnez **supprimer** pour supprimer le flux ou cliquez sur **Annuler** pour quitter l’action de suppression.

## <a name="reports-preview"></a>Rapports (aperçu)

Le nouveau tableau de bord **rapports** est l’emplacement central pour l’affichage de tous les rapports de conformité de communication. Les widgets de rapport fournissent un aperçu rapide des informations les plus souvent nécessaires pour une évaluation globale de l’état des activités de conformité des communications. Les informations contenues dans les widgets de rapport ne sont pas exportables. Les rapports détaillés fournissent des informations détaillées sur les zones de conformité de communication spécifiques et permettent de filtrer, regrouper, trier et exporter des informations lors de la révision.

Le **tableau de bord rapports** contient les liens des widgets de rapport et des rapports détaillés suivants :

- La **stratégie récente correspond à** widget : affiche le nombre de correspondances par stratégie active dans le temps.
- Widgets **résolus par la stratégie** : affiche le nombre d’alertes de correspondance de stratégie résolues par stratégie dans le temps.
- **Utilisateurs avec la plupart des stratégies** -widget match : affiche les utilisateurs (ou les noms d’utilisateur anonymes) et le nombre de correspondances de stratégie pour une période donnée.
- **Stratégie avec le plus de correspondances** , widget : affiche les stratégies et le nombre de correspondances pour une période donnée, classés le plus élevé pour les correspondances.
- **Escalades par le widget de stratégie** : affiche le nombre de remontées par stratégie sur un moment donné.
- **Paramètres de stratégie et** rapport détaillé d’État : fournit un aperçu détaillé de la configuration et des paramètres de stratégie, ainsi que de l’état général de chacune de la stratégie (correspondances et actions) sur les messages. Utilisez l’option *Exporter* pour créer un. Fichier CSV contenant les détails du rapport.
- **Éléments et actions par stratégie** rapport détaillé : Examinez et exportez les éléments correspondants et les actions de correction par stratégie. Utilisez l’option *Exporter* pour créer un. Fichier CSV contenant les détails du rapport.
- Rapport détaillé sur les éléments **et les actions par emplacement** : Examinez et exportez les éléments correspondants et les actions de correction par emplacement Microsoft 365. Utilisez l’option *Exporter* pour créer un. Fichier CSV contenant les détails du rapport.

## <a name="audit"></a>Audit

Dans certains cas, vous devez fournir des informations aux auditeurs de réglementation ou de conformité pour prouver le contrôle des activités et des communications des utilisateurs. Ces informations peuvent être un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque fois qu’une stratégie de conformité de communication est modifiée. Les stratégies de conformité des communications disposent de pistes d’audit intégrées pour une préparation complète des audits internes ou externes. Les historiques d’audit détaillés de chaque action de création, de modification et de suppression sont capturés par vos stratégies de communication afin de fournir des preuves de procédures de surveillance.

>[!Important]
>L’audit doit être activé pour votre organisation pour que les événements de conformité de la communication soient enregistrés. Pour activer l’audit, consultez [la rubrique activer le journal d’audit](communication-compliance-configure.md#step-2-required-enable-the-audit-log).

Pour afficher les activités de mise à jour des stratégies de conformité des communications, sélectionnez le contrôle d' **exportation des mises à jour des stratégies** sur la page principale de n’importe quelle stratégie. Vous devez disposer des rôles administrateur *général* ou *administrateur de conformité des communications* pour exporter des activités de mise à jour. Cette action génère un fichier d’audit au format. csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Date à laquelle l’activité de mise à jour a été effectuée dans une stratégie. |
| **UserIds** | Utilisateur qui a effectué l’activité de mise à jour dans une stratégie. |
| **Opérations** | Les opérations de mise à jour effectuées sur la stratégie. |
| **AuditData** | Ce champ est la source de données principale pour toutes les activités de mise à jour de stratégie. Toutes les activités de mise à jour sont enregistrées et séparées par des virgules. |

Pour afficher les activités de vérification de conformité de la communication pour une stratégie, sélectionnez le contrôle **Exporter les activités de révision** dans la page de vue d' **ensemble** pour une stratégie spécifique. Vous devez disposer des rôles administrateur *général* ou *administrateur de conformité des communications* pour exporter des activités de révision. Cette action génère un fichier d’audit au format. csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Date à laquelle l’activité de révision a été effectuée dans une stratégie. |
| **UserIds** | Utilisateur qui a effectué l’activité de révision dans une stratégie. |
| **Opérations** | Les opérations de révision effectuées sur la stratégie. |
| **AuditData** | Ce champ est la source de données principale pour toutes les activités de révision de stratégie. Toutes les activités de révision sont enregistrées et séparées par des virgules. |

Vous pouvez également afficher les activités d’audit dans le journal d’audit unifié ou avec l’applet de commande PowerShell [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog) .

Par exemple, l’exemple suivant renvoie les activités de toutes les activités de vérification de surveillance (stratégies et règles) :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

Cet exemple renvoie les activités de mise à jour pour vos stratégies de conformité de communication :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité de la communication pour votre organisation Microsoft 365, consultez la rubrique [configure communication Compliance for your microsoft 365 Organization](communication-compliance-configure.md).
