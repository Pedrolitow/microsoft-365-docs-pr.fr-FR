---
title: Référence des fonctionnalités de conformité des communications
description: Référence des fonctionnalités pour la conformité des communications dans Microsoft 365. Découvrez les détails et les spécifications de chacun des composants de fonctionnalité.
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
ms.openlocfilehash: e2d0f4f4abbe538d11d61869f52285f19c23a253
ms.sourcegitcommit: a7d1b29a024b942c7d0d8f5fb9b5bb98a0036b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2021
ms.locfileid: "50461805"
---
# <a name="communication-compliance-feature-reference"></a>Référence des fonctionnalités de conformité des communications

## <a name="policies"></a>Stratégies

>[!Important]
>L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la solution de conformité des [communications Microsoft 365.](https://compliance.microsoft.com/supervisoryreview)

Vous créez des stratégies de conformité des communications pour les organisations Microsoft 365 dans le Centre de conformité Microsoft 365. Les stratégies de conformité des communications définissent les communications et les utilisateurs qui sont soumis à révision dans votre organisation, définissent les conditions personnalisées que les communications doivent respecter et spécifient qui doit passer en revue. Les utilisateurs affectés au rôle d’administrateur de conformité des communications peuvent configurer des stratégies, et toute personne à qui ce rôle est attribué peut accéder à la **page** conformité des communications et aux paramètres globaux dans le Centre de conformité Microsoft 365.  Si nécessaire, vous pouvez exporter l’historique des modifications apportées à une stratégie vers un fichier .csv (valeurs séparées par des virgules) qui inclut également l’état des alertes en attente de révision, des éléments résordés et des éléments résolus. Les stratégies ne peuvent pas être renommées et supprimées lorsqu’elles ne sont plus nécessaires.

>[!NOTE]
>Les stratégies de surveillance créées dans le Centre de sécurité & conformité pour les abonnements Office 365 ne peuvent pas migrer vers Microsoft 365. Si vous migrez d’un abonnement Office 365 vers un abonnement Microsoft 365, vous devez créer de nouvelles stratégies de conformité des communications pour remplacer les stratégies de surveillance existantes.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de stratégie sont des paramètres de stratégie prédéfincés que vous pouvez utiliser pour créer rapidement des stratégies pour répondre aux scénarios de conformité courants. Chacun de ces modèles présente des différences dans les conditions et l’étendue, et tous les modèles utilisent les mêmes types de signaux d’analyse. Vous pouvez choisir parmi les modèles de stratégie suivants :

|**Catégorie**|**Modèle de stratégie**|**Détails**|
|:-----|:-----|:-----|
| **Langage choquant et anti-harcèlement** | Surveiller les communications en cas de langage choquant | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage d’avis : 100 % <br> - Conditions : classifieur de langage choquant |
| **Informations sensibles** | Surveiller les communications pour les informations sensibles | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage d’avis : 10 % <br> - Conditions : informations sensibles, modèles de contenu pré-personnalisés et types, option de dictionnaire personnalisé, pièces jointes dont la taille est supérieure à 1 Mo |
| **Conformité réglementaire** | Surveiller les communications pour les informations relatives à la conformité réglementaire financière | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant <br> - Pourcentage d’avis : 10 % <br> - Conditions : option de dictionnaire personnalisé, pièces jointes dont la taille est supérieure à 1 Mo |
| **Conflit d’intérêt** | Surveiller les communications entre deux groupes ou deux utilisateurs pour éviter les conflits d’intérêts | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : interne <br> - Pourcentage d’avis : 100 % <br> - Conditions : Aucune |

Les communications sont analysées toutes les 24 heures à partir de la création des stratégies. Par exemple, si vous créez une stratégie de langage choquant à 11 h 00, la stratégie recueille tous les 24 heures des signaux de conformité des communications à 11 h 00 tous les jours. La modification d’une stratégie ne change pas cette fois. Pour afficher la date et l’heure de  la dernière analyse d’une stratégie, accédez à la colonne Dernière analyse de stratégie dans la page **Stratégie.** Après la création d’une stratégie, l’affichage de la date et de l’heure de la première analyse de stratégie peut prendre jusqu’à 24 heures. La date et l’heure de la dernière analyse seront converties en fuseau horaire de votre système local.

## <a name="permissions"></a>Autorisations

>[!Important]
>Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les rôles attribués au cours de cette étape sont requis pour que les fonctionnalités de conformité des communications soient accessibles.

Il existe cinq groupes de rôles utilisés pour configurer les autorisations pour gérer les fonctionnalités de conformité des communications. Pour rendre la conformité des communications disponible en tant qu’option de menu dans le Centre  de  conformité Microsoft 365 et pour poursuivre ces étapes de configuration, vous devez être affecté aux groupes de rôles Conformité des communications ou Administrateur de la conformité des communications.  Pour accéder aux fonctionnalités de conformité des communications et les gérer après la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de conformité des communications.

Selon la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques. Vous avez la possibilité d’affecter des utilisateurs ayant différentes responsabilités de conformité à des groupes de rôles spécifiques pour gérer différents domaines des fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les  administrateurs, analystes, enquêteurs et visionneuses désignés au groupe de rôles Conformité des communications. Utilisez un ou plusieurs groupes de rôles pour mieux vous adapter à vos exigences de gestion de la conformité.

Choisissez parmi ces options de groupe de rôles lors de la configuration de la conformité des communications :

|**Groupe de rôles**|**Autorisations de groupe de rôles**|
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration est le moyen le plus simple de se lancer rapidement dans la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis séparez les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupe de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies dans laquelle ils sont affectés en tant que réviseurs, afficher les métadonnées des messages (et non le contenu du message), faire une escalade vers d’autres réviseurs ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, s’adresser à d’autres réviseurs, passer à un cas Advanced eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

### <a name="for-organizations-using-the-original-permissions-and-role-groups"></a>Pour les organisations utilisant les autorisations d’origine et les groupes de rôles

La nouvelle structure de groupe de rôles remplace la structure initiale du groupe de rôles pour la conformité des communications. Pour les organisations qui utilisent déjà la conformité des communications, vous devez avoir le rôle Administrateur de vérification de surveillance pour commencer à respecter la conformité des communications dans le Centre de conformité Microsoft 365. En outre, vous deviez créer un groupe de rôles pour les réviseurs avec les rôles Administrateur de vérification de surveillance, Gestion des cas, Administrateur de conformité et Révision pour examiner et corriger les messages avec des correspondances de stratégie. En fait, tous les administrateurs et les réviseurs faisaient partie d’un seul groupe de rôles et tout le monde avait les mêmes autorisations d’accès et de gestion. Avec les dernières mises à jour de la conformité des communications, vous devez planifier la migration de la structure de groupe de rôles précédente vers la nouvelle structure de groupe de rôles. La prise en charge de la structure de groupe de rôles précédente sera progressivement mise hors d’œuvre.

Pour faciliter la planification de la migration, prenons l’exemple suivant. Vous avez actuellement trois types d’utilisateurs dans votre organisation, les administrateurs informatiques, le triage et les réviseurs. Ces trois types d’utilisateurs font partie de la structure de groupe de rôles précédente et sont tous membres d’un groupe de rôles unique avec les rôles suivants attribués :

- Administrateur de la révision de surveillance
- Gestion des cas
- Administrateur de conformité
- Révision

Pour mettre à jour les rôles de ces utilisateurs pour la nouvelle structure de groupe de rôles et séparer les autorisations d’accès et de gestion pour les utilisateurs, vous pouvez envisager trois nouveaux groupes et les nouvelles attributions de groupe de rôles associées :

- **Administrateurs informatiques**: affectés au nouveau groupe de rôles Administrateur de conformité *des* communications.
- **Triage**: affecté au groupe de *rôles Analyste de conformité des* communications.
- **Réviseurs**: affecté au nouveau groupe de rôles Enquêteur de conformité *des* communications.

## <a name="supervised-users"></a>Utilisateurs supervisés

Avant de commencer à utiliser la conformité des communications, vous devez déterminer qui a besoin de ses communications. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou groupes de personnes à superviser. Ces groupes sont, par exemple, des groupes Microsoft 365, des listes de distribution Basées sur Exchange, des Yammer et des canaux Microsoft Teams. Vous pouvez également exclure des utilisateurs ou des groupes spécifiques de l’analyse d’un groupe d’exclusion spécifique ou d’une liste de groupes.

>[!IMPORTANT]
>Les utilisateurs couverts par les stratégies de conformité des communications doivent avoir une licence de conformité Microsoft 365 E5, une licence Office 365 Entreprise E3 avec le module de conformité avancée, ou être inclus dans un abonnement Office 365 Entreprise E5. Si vous n’avez pas de plan Entreprise E5 existant et que vous souhaitez essayer la conformité des communications, vous pouvez vous inscrire à une version d’essai [d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

## <a name="reviewers"></a>Relecteurs

Lorsque vous créez une stratégie de conformité des communications, vous devez déterminer qui examine les messages des utilisateurs supervisés. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou les groupes de personnes qui doivent réviser les communications contrôlées. Tous les réviseurs doivent avoir des boîtes aux  lettres hébergées sur Exchange Online et doivent être affectés aux rôles Analyse de conformité des communications ou Examen de la conformité *des* communications. Le rôle Gestion des cas de conformité  des communications doit également être attribué aux réviseurs (analystes ou enquêteurs). Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.

## <a name="groups-for-supervised-users-and-reviewers"></a>Groupes pour les utilisateurs et les relecteurs supervisés

Pour simplifier votre configuration, créez des groupes pour les personnes qui ont besoin de réviser leurs communications et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous voulez analyser des communications entre deux groupes distincts de personnes, ou si vous voulez spécifier un groupe qui n’est pas supervisé.

Lorsque vous affectez un groupe de distribution dans la stratégie, la stratégie surveille tous les messages électroniques de chaque utilisateur du groupe de distribution. Lorsque vous affectez un groupe Microsoft 365 dans la stratégie, la stratégie surveille tous les messages électroniques envoyés à ce groupe, pas les messages électroniques individuels reçus par chaque membre du groupe.

L’ajout de groupes et de listes de distribution à des stratégies de conformité des communications fait partie des conditions globales et des règles définies, de sorte que le nombre maximal de groupes et de listes de distribution pris en charge par une stratégie varie en fonction du nombre de conditions également ajoutées à la stratégie. Chaque stratégie doit prendre en charge environ 20 groupes ou listes de distribution, selon le nombre de conditions supplémentaires présentes dans la stratégie.

## <a name="supported-communication-types"></a>Types de communications pris en charge

Avec les stratégies de conformité des communications, vous pouvez choisir d’analyser les messages dans une ou plusieurs des plateformes de communication suivantes en tant que groupe ou en tant que sources autonomes. Par défaut, les communications capturées sur ces plateformes sont conservées pendant sept ans pour chaque stratégie, même si les utilisateurs quittent votre organisation et que leurs boîtes aux lettres sont supprimées.

- **Microsoft Teams :** les communications de conversation dans les canaux Microsoft Teams publics et privés et les conversations individuelles peuvent être analysées. Lorsque les utilisateurs sont affectés à une stratégie de conformité des communications dont la couverture Microsoft Teams est sélectionnée, les communications de conversation des utilisateurs sont automatiquement surveillées dans toutes les équipes Microsoft Teams dont les utilisateurs sont membres. La couverture Microsoft Teams est automatiquement incluse pour les modèles de stratégie prédéfin définis et est sélectionnée par défaut dans le modèle de stratégie personnalisé. Le traitement des conversations Teams correspondant aux conditions de stratégie de conformité des communications peut prendre jusqu’à 48 heures. Utilisez les configurations de gestion de groupe suivantes pour superviser les conversations des utilisateurs individuels et les communications de canal dans Teams :

    - **Pour les communications de conversation Teams :** Affecter des utilisateurs individuels ou affecter un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.
    - **Pour les communications de canal Teams :** Affectez à chaque canal Microsoft Teams ou groupe Microsoft 365 que vous souhaitez analyser un utilisateur spécifique à la stratégie de conformité des communications. Si vous ajoutez le même utilisateur à d’autres canaux Microsoft Teams ou à des groupes Microsoft 365, veillez à ajouter ces nouveaux canaux et groupes à la stratégie de conformité des communications.
    - Pour les communications de conversation Teams avec des **environnements** de messagerie hybride : la conformité des communications peut surveiller les messages de conversation pour les utilisateurs des organisations avec un déploiement Exchange local ou un fournisseur de messagerie externe ayant activé Microsoft Teams. Vous devez créer un groupe de distribution pour les utilisateurs avec des boîtes aux lettres externes ou sur site à surveiller. Lorsque vous créez une stratégie de conformité des  communications, vous affectez ce groupe de distribution en tant que sélection d’utilisateurs et de groupes Supervisés dans l’Assistant Stratégie.

    >[!IMPORTANT]
    >Vous devez effectuer une demande auprès du Support Microsoft pour autoriser votre organisation à utiliser l’interface utilisateur graphique dans le centre de conformité et sécurité pour rechercher des données de conversations Teams pour des utilisateurs locaux. Pour plus d’informations, voir Recherche de boîtes aux lettres dans le [cloud pour les utilisateurs locaux.](search-cloud-based-mailboxes-for-on-premises-users.md)

Vous devez effectuer une demande auprès du Support Microsoft pour autoriser votre organisation à utiliser l’interface utilisateur graphique dans le centre de conformité et sécurité pour rechercher des équipes dans les boîtes aux lettres en ligne des utilisateurs locaux.

- **Messagerie Exchange**: les boîtes aux lettres hébergées sur Exchange Online dans le cadre de votre abonnement Microsoft 365 ou Office 365 sont toutes éligibles pour l’analyse des messages. Le traitement des messages électroniques Exchange et des pièces jointes correspondant aux conditions de stratégie de conformité des communications peut prendre jusqu’à 24 heures. Les types de pièces jointes prises en charge pour la conformité des communications sont les mêmes que les [types de fichiers pris en charge pour les inspections du contenu des règles de flux de messagerie Exchange](/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

- **Yammer**: les messages privés et les conversations publiques et les pièces jointes associées dans Yammer communautés peuvent être analysées. Lorsqu’un utilisateur est ajouté à la stratégie de conformité des communications qui inclut Yammer en tant que canal défini, les communications entre toutes les communautés Yammer dont l’utilisateur est membre sont incluses dans le processus d’analyse. Yammer conversations et pièces jointes correspondant aux conditions de stratégie de conformité des communications peuvent prendre jusqu’à 24 heures. Yammer doit être en [mode natif pour](/yammer/configure-your-yammer-network/overview-native-mode) que les stratégies de conformité des communications surveillent Yammer communications et les pièces jointes. En mode natif, tous les utilisateurs de Yammer se trouvent dans Azure Active Directory (AAD), tous les groupes sont des Groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online.

- **Skype Entreprise Online** :Les communications de conversation et les pièces jointes associées dans Skype Entreprise Online peuvent être supervisées. Les conversations Skype Entreprise Online correspondant aux conditions de la stratégie de conformité des communications peuvent prendre jusqu’à 24 heures. Les conversations supervisées sont provenant de [conversations précédentes enregistrées dans Skype Entreprise Online.](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2)  Utilisez la configuration de gestion de groupe suivante pour superviser les communications de conversation utilisateur dans Skype Entreprise Online :

    - **Pour les communications de** conversation Skype Entreprise Online : affectez des utilisateurs individuels ou attribuez un groupe [de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Ce paramètre s'applique aux relations d'utilisateur/chat en tête à tête ou à plusieurs.

- Sources tierces : vous pouvez analyser les communications pour les données importées dans les boîtes aux lettres de votre organisation Microsoft 365 à partir de sources tierces telles que [Instant Bloomberg,](archive-instant-bloomberg-data.md) [Slack,](archive-slack-data.md) [Zoom,](archive-zoommeetings-data.md)SMS et bien d’autres. Pour obtenir la liste complète des connecteurs pris en charge dans la conformité des communications, voir [Archiver des données tierces.](archiving-third-party-data.md)

    Vous devez configurer un connecteur tiers pour votre organisation Microsoft 365 avant de pouvoir affecter le connecteur à une stratégie de conformité des communications. La section **Sources tierces** de l’Assistant Stratégie de conformité des communications affiche uniquement les connecteurs tiers actuellement configurés.

## <a name="policy-settings"></a>Paramètres de stratégie

### <a name="users"></a>Utilisateurs

Vous avez la possibilité de sélectionner Tous **les** utilisateurs ou de définir des utilisateurs spécifiques dans une stratégie de conformité des communications. La sélection de **Tous les utilisateurs** applique la stratégie à tous les utilisateurs et les groupes auxquels n’importe quel utilisateur est inclus en tant que membre. La définition d’utilisateurs spécifiques applique la stratégie aux utilisateurs définis et aux groupes auxquels les utilisateurs définis sont inclus.

### <a name="direction"></a>Direction

Par défaut, la **condition Direction** est affichée et ne peut pas être supprimée. Les paramètres d’orientation de communication dans une stratégie sont choisis individuellement ou ensemble :

- **Entrant :** vous pouvez choisir **Le** trafic entrant pour passer en revue les communications envoyées **aux** personnes que vous avez choisi de superviser.
- **Sortant :** vous pouvez choisir **Sortant** si vous souhaitez passer en revue les communications envoyées par **les** personnes que vous avez choisi de superviser.
- **Interne**: vous pouvez choisir **Interne** pour passer en revue les communications envoyées **entre** les personnes que vous avez identifiées dans la stratégie.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous avez la possibilité d’inclure des types d’informations sensibles dans le cadre de votre stratégie de conformité des communications. Les types d’informations sensibles sont des types de données prédéfin définis ou personnalisés qui permettent d’identifier et de protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Dans le cadre de [protection contre la perte de données (DLP)](data-loss-prevention-policies.md), la configuration des informations sensibles peut utiliser les modèles, la proximité des caractères, les niveaux de confiance, et même les types de données personnalisés pour vous aider à identifier et signaler le contenu sensible. Les types d’informations sensibles par défaut sont :

- Financier
- Santé et santé
- Confidentialité
- Type d’informations personnalisé

Pour en savoir plus sur les détails des informations sensibles et les modèles inclus dans les types par défaut, voir Définitions d’entités de [type d’informations sensibles.](sensitive-information-type-entity-definitions.md)

### <a name="custom-keyword-dictionaries"></a>Dictionnaires de mots clés personnalisés

Configurez des dictionnaires de mots clés personnalisés (ou lexicons) pour fournir une gestion simple des mots clés propres à votre organisation ou à votre secteur d’activité. Les dictionnaires de mots clés prendre en charge jusqu’à 100 Ko de termes (post-compression) dans le dictionnaire et n’importe quelle langue. La limite du client est également de 100 Ko après compression. Si nécessaire, vous pouvez appliquer plusieurs dictionnaires de mots clés personnalisés à une stratégie unique ou avoir un seul dictionnaire de mots clés par stratégie. Ces dictionnaires sont affectés dans une stratégie de conformité des communications et peuvent être issus d’un fichier (par exemple, une liste .csv ou .txt), ou d’une liste que vous pouvez importer dans le Centre de [conformité.](create-a-keyword-dictionary.md) Utilisez des dictionnaires personnalisés lorsque vous devez prendre en charge des termes ou des langues spécifiques à votre organisation et à vos stratégies.

### <a name="classifiers"></a>Classifieurs

Les classifieurs intégrés et globaux analysent les messages envoyés ou reçus sur tous les canaux de communication de votre organisation pour les différents types de problèmes de conformité. Les classifieurs utilisent une combinaison d'intelligence artificielle et de mots clés pour identifier le langage dans les messages susceptibles d'enfreindre les stratégies anti-harcèlement. Les classifieurs intégrés actuellement en charge l’identification des mots clés de message dans plusieurs langues :

- Chinois (simplifié)
- Anglais
- Français
- Allemand
- Italien
- Japonais
- Portugais
- Espagnol

Les classifieurs intégrés et globaux entraisables de conformité des communications analysent les communications pour les termes, les images et les sentiments pour les types de langage et de contenu suivants :

- **Menace :** recherche les menaces de violence ou de dommages physiques à une personne ou à une propriété.
- **Harcèlement ciblé**: recherche les conduites choquantes ciblant des personnes en ce qui concerne la course, la couleur, l’origine nationale, la couleur et l’origine nationale.
- **Blasphémité**: recherche les expressions insoignées qui insérancent la plupart des personnes.
- **Images pour adultes**: recherche les images qui sont explicites de manière sexuelle.
- **Images racées**: recherche les images qui sont sexuellement sexuellement en nature, mais qui contiennent un contenu moins explicite que les images considérées comme adulte.
- **Images de requête**: recherche les images qui décrivent la violence et les violences.

Les *classifieurs* d’image Pour adultes, *Racy* et *Gory* analysent les fichiers aux formats .jpeg, .png, .gif et .bmp. La taille des fichiers image doit être inférieure à 4 mégaoctets (Mo) et les dimensions des images doivent être supérieures à 50 x 50 pixels et supérieures à 50 kilo-octets (Ko) pour que l’image soit éligible pour évaluation. L’identification d’image est prise en charge pour les messages électroniques Exchange Online et les canaux et conversations Microsoft Teams.

Les classifieurs intégrés entraçables et globaux ne fournissent pas une liste exhaustive de termes ou d’images dans ces domaines. En outre, les normes linguistiques et culturelles changent continuellement et, à la lumière de ces exigences, Microsoft se réserve le droit de mettre à jour les classifieurs à sa discrétion. Bien que les classifieurs peuvent aider votre organisation à surveiller ces domaines, les classifieurs ne sont pas destinés à fournir l’unique moyen de votre organisation de surveiller ou d’adresser ces langages ou images. Votre organisation, et non Microsoft, reste responsable de toutes les décisions relatives à la surveillance, l’analyse et le blocage de la langue et des images dans ces domaines, y compris la conformité avec la confidentialité locale et les autres lois applicables. Microsoft encourage les conseils juridiques avant le déploiement et l’utilisation.

>[!NOTE]
>Les stratégies utilisant des classifieurs examinent et évaluent les messages avec un nombre de mots supérieur ou six. Les messages contenant moins de six mots ne sont pas évalués dans les stratégies à l’aide de classifieurs. Pour identifier et prendre des mesures sur les messages plus courts contenant du contenu inapproprié, nous vous recommandons d’inclure un dictionnaire de mots clés personnalisé pour surveiller les stratégies de conformité des communications pour ce type de contenu.

Pour plus d’informations sur les classifieurs entraisables dans Microsoft 365, voir La mise en place des [classifieurs entraisables.](classifier-get-started-with.md)

### <a name="optical-character-recognition-ocr-preview"></a>Reconnaissance optique de caractères (OCR) (aperçu)

Configurez des stratégies de conformité des communications intégrées ou personnalisées pour analyser et identifier le texte imprimé ou manuscrit à partir d’images qui peuvent être inappropriées dans votre organisation. La prise en charge intégrée des services cognitives Azure et de l’analyse optique pour l’identification du texte dans les images permet aux analystes et aux enquêteurs de détecter et d’agir sur des cas où une conduite inappropriée peut être manquée dans des communications principalement non textuelles.

Vous pouvez activer la reconnaissance optique de caractères (OCR) dans de nouvelles stratégies à partir de modèles, de stratégies personnalisées ou mettre à jour des stratégies existantes pour développer la prise en charge du traitement des images incorporées et des pièces jointes. Lorsqu’elle est activée dans une stratégie créée à partir d’un modèle de stratégie, l’analyse automatique est prise en charge pour les images incorporées ou jointes dans les messages électroniques et les messages de conversation Microsoft Teams. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés à des mots clés, classifieurs intégrés ou types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de l’analyse ocr.

Les images de 50 Ko à 4 Mo dans les formats d’image suivants sont analysées et traitées :

- .jpg/.jpeg (groupe d’experts en exercice commun)
- .png (graphiques réseau portables)
- .bmp (bitmap)
- .tiff (format de fichier d’image de balise)
- .pdf (format de document portable)

>[!NOTE]
>L’analyse et l’extraction des images .pdf incorporées et jointes sont actuellement prises en charge uniquement pour les messages électroniques.

Lors de la révision des alertes en attente pour les stratégies avec ocr activé, les images identifiées et associées aux conditions de stratégie sont affichées en tant qu’éléments enfants pour les alertes associées. Vous pouvez afficher l’image d’origine pour évaluer le texte identifié en contexte avec le message d’origine. La présence d’images détectées avec des alertes peut prendre jusqu’à 48 heures.

### <a name="conditional-settings"></a>Paramètres conditionnels
<a name="ConditionalSettings"> </a>

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications provenant de la messagerie électronique et de sources tierces de votre organisation (par exemple, d’Instant Bloomberg).

Le tableau suivant en explique plus sur chaque condition.
  
|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le contenu correspond à l’un de ces classifieurs** | S’applique à la stratégie lorsque des classifieurs sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre client et les classifieurs personnalisés doivent être configurés séparément avant d’être disponibles pour cette condition. Un seul classificateur peut être défini comme condition dans une stratégie. Pour plus d’informations sur la configuration des classifieurs, voir [Learn about trainable classifiers (preview).](classifier-learn-about.md) |
| **Le contenu contient l’un de ces types d’informations sensibles** | S’applique à la stratégie lorsque des types d’informations sensibles sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre client, et les classifieurs personnalisés peuvent être configurés séparément ou dans le cadre du processus d’attribution de condition. Chaque type d’informations sensibles que vous choisissez est appliqué séparément et un seul de ces types d’informations sensibles doit s’appliquer pour que la stratégie s’applique au message. Pour plus d’informations sur les types d’informations sensibles personnalisés, voir [En savoir plus sur les types d’informations sensibles.](sensitive-information-type-learn-about.md) |
| **Le message est reçu de l’un de ces domaines**  <br><br> **Le message n’est reçu d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages reçus. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse e-mail entré est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez analyser tous les messages électroniques d’un domaine spécifique, mais que vous souhaitez exclure les messages qui n’ont pas besoin d’être réexpédés (bulletins d’informations, annonces, et ainsi de suite), vous devez configurer un **message** qui n’est reçu d’aucune condition de ces domaines qui exclut l’adresse e-mail (exemple « newsletter@contoso.com »). |
| **Le message est envoyé à l’un de ces domaines**  <br><br> **Le message n’est envoyé à aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages envoyés. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez analyser tous les messages envoyés à un domaine spécifique, mais que vous souhaitez exclure les messages envoyés qui ne doivent pas être réviser, vous devez configurer deux conditions : <br> - Un **message est envoyé à l’une de ces** conditions de domaine qui définit le domaine (« contoso.com ») ET <br> - Un **message n’est envoyé à aucune** condition de ces domaines qui exclut l’adresse de messagerie « subscriptions@contoso.com »). |
| **Le message est classé avec l’une de ces étiquettes**  <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Pour appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées sont choisies dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur les étiquettes de rétention, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)|
| **Le message contient l’un de ces mots**  <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **La pièce jointe contient l’un de ces mots**  <br><br> **La pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus d’une pièce jointe de message (par exemple, un document Word), entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **La pièce jointe est l’un de ces types de fichiers**  <br><br> **La pièce jointe n’est pas de ces types de fichiers** | Pour contrôler les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichier (telles que .exe ou .pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichier, entrez-les sur des lignes distinctes. Une seule extension de pièce jointe doit correspondre pour que la stratégie s’applique.|
| **La taille du message est supérieure à**  <br><br> **La taille du message n’est pas supérieure à** | Pour examiner les messages en fonction d’une certaine taille, utilisez ces conditions pour spécifier la taille maximale ou minimale d’un message avant d’être soumis à révision. Par exemple, si vous spécifiez que la taille du **message** est supérieure à \> **1,0 Mo,** tous les messages de 1,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La pièce jointe est supérieure à**  <br><br> **La pièce jointe n’est pas supérieure à** | Pour passer en revue les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale d’une pièce jointe avant que le message et ses pièces jointes soient sujettes à révision. Par exemple, si  vous spécifiez que la pièce jointe est supérieure à \> **2,0 Mo,** tous les messages avec des pièces jointes de 2,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
   
#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes
<a name="Matchwords"> </a>

Chaque mot que vous entrez et séparez par une virgule est appliqué séparément (un seul mot doit s’appliquer à la condition de stratégie à appliquer au message électronique ou à la pièce jointe). Par exemple, nous allons utiliser la condition « **Message**» contient l’un de ces mots, avec les mots clés « banker », « confidential » et « insider trading » séparés par une virgule (bancaire, confidentiel, « délit d’initié »). La stratégie s’applique à tous les messages qui incluent le mot « banker », « confidential » ou l’expression « insider trading ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots dans le message ou la pièce jointe doivent correspondre exactement à ce que vous entrez.

>[!IMPORTANT]
>Lors de l’importation d’un fichier de dictionnaire personnel, chaque mot ou expression doit être séparé par un retour chariot et sur une ligne distincte. <br> Par exemple : <br><br>
>*banker* <br>
>*confidentiel* <br>
>*délit d’initié*

Pour analyser les messages électroniques et les pièces [](create-test-tune-dlp-policy.md) jointes pour les [](create-a-keyword-dictionary.md) mêmes mots clés, créez une stratégie de protection contre la perte de données avec un dictionnaire de mots clés personnalisé pour les termes que vous souhaitez analyser dans les messages. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **ou** dans la pièce jointe de l’e-mail. L’utilisation des paramètres de stratégie conditionnelle standard ( Le *message* contient l’un de ces mots et *la* pièce jointe contient l’un de ces mots) pour identifier les termes dans les messages et dans les pièces jointes, les termes doivent être présents dans le message et la pièce jointe. 
  
#### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer quand appliquer la stratégie de conformité des communications aux éléments de communication. Lorsque vous définissez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « commerce » et est supérieur à 2 Mo. Toutefois, si le message contient également les mots « Approuvé par Contoso financial », la stratégie ne doit pas s’appliquer. Dans cet exemple, les trois conditions seraient définies comme suit :
  
- **Le message contient l’un de ces mots,** avec le mot clé « trade »
- **La taille du message est supérieure** à , avec la valeur 2 Mo
- **Le message ne contient aucun de ces mots,** avec les mots clés « Approuvé par l’équipe financière de Contoso »

### <a name="review-percentage"></a>Pourcentage de révision

Si vous souhaitez réduire la quantité de contenu à réviser, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de conformité des communications. Un échantillon aléatoire de contenu est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les réviseurs examinent tous les éléments, vous pouvez configurer **100 %** dans une stratégie de conformité des communications.

## <a name="privacy"></a>Confidentialité

La protection de la confidentialité des utilisateurs qui ont des correspondances de stratégie est importante et peut contribuer à promouvoir la fiabilité dans les examens d’analyse et d’examen des données pour les alertes de conformité des communications. Ce paramètre s’applique uniquement aux noms d’utilisateurs affichant la solution de conformité des communications. Cela n’affecte pas la façon dont les noms sont affichés dans d’autres solutions de conformité ou centre d’administration.

Pour les utilisateurs ayant une correspondance de conformité des communications, vous pouvez choisir l’un des paramètres suivants dans les **paramètres** de conformité des communications :

- **Afficher les versions anonymisées** des noms d’utilisateur  : les noms d’utilisateur sont rendus anonymes pour empêcher les utilisateurs du groupe de rôles Analyste de conformité des communications de voir qui est associé aux alertes de stratégie. Les utilisateurs du groupe de rôles *Enquêteur de* conformité des communications voient toujours les noms d’utilisateur, et non les versions rendues anonymes. Par exemple, un utilisateur « Grace Grace » apparaît avec un pseudonyme aléatoire tel que « AnonIS8-988 » dans tous les domaines de l’expérience de conformité des communications. Le choix de ce paramètre permet d'anonymiser tous les utilisateurs ayant des correspondances de stratégie actuelle et passée et s’applique à toutes les stratégies. Les informations de profil utilisateur dans les détails de l’alerte de conformité des communications ne seront pas disponibles lorsque cette option sera choisie. Toutefois, les noms d’utilisateurs s’affichent lors de l’ajout de nouveaux utilisateurs à des stratégies existantes ou lors de l’affectation d’utilisateurs à de nouvelles stratégies. Si vous choisissez de désactiver ce paramètre, les noms d’utilisateur s’affichent pour tous les utilisateurs qui ont des correspondances de stratégie actuelles ou passées.
- **N’affichez pas les versions rendues anonymes** des noms d’utilisateur : les noms d’utilisateur sont affichés pour toutes les correspondances de stratégie actuelles et passées pour les alertes de conformité des communications. Les informations de profil utilisateur (nom, titre, alias et organisation ou service) s’affichent pour l’utilisateur pour toutes les alertes de conformité des communications.

## <a name="notice-templates"></a>Modèles de notifications

Vous pouvez créer des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par courrier électronique pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse de messagerie de l’utilisateur associée à la correspondance de stratégie qui a généré l’alerte spécifique pour la correction. Lorsque vous sélectionnez un modèle d’avis à appliquer à une violation de stratégie dans le cadre du flux de travail de correction, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou d’en faire le choix.

Les modèles d’avis sont des modèles de courrier personnalisés dans lequel vous pouvez définir les champs de message suivants dans la **zone Paramètres de conformité des communications** :

|**Field**|**Obligatoire**| **Détails** |
|:-----|:-----|:-----|
|**Nom du modèle** | Oui | Le nom convivial du modèle d’avis que vous sélectionnerez dans le flux de travail d’notification lors de la correction prend en charge les caractères de texte. |
| **Adresse de l’expéditeur** | Oui | Adresse d’un ou de plusieurs utilisateurs ou groupes qui envoient le message à l’utilisateur avec une correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement. |
| **Adresses CC et Cci** | Non | Utilisateurs ou groupes facultatifs à notifiés de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement. |
| **Subject** | Oui | Les informations qui apparaissent dans la ligne d’objet du message, prend en charge les caractères de texte. |
| **Corps du message** | Oui | Les informations qui apparaissent dans le corps du message, prend en charge les valeurs texte ou HTML. |

### <a name="html-for-notices"></a>HTML pour les notifications

Si vous souhaitez créer plus qu’un simple message électronique texte pour les notifications, vous pouvez créer un message plus détaillé à l’aide du code HTML dans le champ corps du message d’un modèle d’avis. L’exemple suivant fournit le format du corps du message pour un modèle de notification par courrier électronique html de base :

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
>L’implémentation d’attribut href HTML dans les modèles de notification de conformité des communications ne permet actuellement de ne pas utiliser de guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="filters"></a>Filtres

Les filtres de conformité des communications vous permettent de filtrer et de trier les messages d’alerte pour des actions d’investigation et de correction plus rapides. Le filtrage est disponible sous les **onglets En** **attente** et Résolu pour chaque stratégie. Pour enregistrer un filtre ou un ensemble de filtres en tant que requête de filtre enregistrée, une ou plusieurs valeurs doivent être configurées en tant que sélections de filtre. Le tableau suivant présente les détails du filtre :

|**Filtre**|**Détails**|
|:-----|:-----|
| **Date** | Date à laquelle le message a été envoyé ou reçu par un utilisateur de votre organisation. Pour filtrer un jour unique, sélectionnez une plage de dates qui commence par le jour où vous souhaitez obtenir des résultats et se termine par le jour suivant. Par exemple, si vous souhaitez filtrer les résultats pour le 20/09/2020, vous choisissez une plage de dates de filtre du 20/09/2020 au 21/09/2020.|
| **Classe de fichier** | La classe du message en fonction du type de message, *message ou* *pièce jointe*. |
| **A une pièce jointe** | Présence de la pièce jointe dans le message. |
| **Classe d’élément** | Source du message en fonction du type de message, du courrier électronique, de la conversation de Microsoft Team, de Bloomberg, etc. Pour plus d’informations sur les types d’éléments courants et les classes de messages, voir [Types d’éléments et Classes de messages.](/office/vba/outlook/concepts/forms/item-types-and-message-classes) |
| **Domaines des destinataires** | Domaine vers lequel le message a été envoyé. Ce domaine est normalement votre domaine d’abonnement Microsoft 365 par défaut. |
| **Destinataire** | Utilisateur auquel le message a été envoyé. |
| **Sender** | La personne qui a envoyé le message. |
| **Domaine de l’expéditeur** | Domaine qui a envoyé le message. |
| **Taille** | Taille du message en Ko. |
| **Objet/Titre** | Objet du message ou titre de conversation. |
| **Tags** | Balises affectées à un message, soit *discutables,* *conformes,* *soit non conformes.* |
| **Escalated To** | Nom d’utilisateur de la personne incluse dans le cadre d’une action d’escalade de message. |
| **Classifieurs** | Nom des classifieurs intégrés et personnalisés qui s’appliquent au message. Voici quelques exemples *: langage choquant,* *harcèlement ciblé,* *blasphémité,* *menace,* etc.

## <a name="alert-policies"></a>Stratégies d’alerte

Après avoir configuré une stratégie, une stratégie d’alerte correspondante est automatiquement créée et des alertes sont générées pour les messages qui correspondent aux conditions définies dans la stratégie. Par défaut, tous les déclencheurs d’alerte de correspondance de stratégie se voit attribuer un niveau de gravité moyen dans la stratégie d’alerte associée. Les alertes sont générées pour une stratégie de conformité des communications une fois que le niveau de seuil du déclencheur d’agrégation est atteint dans la stratégie d’alerte associée.

Pour les stratégies de conformité des communications, les valeurs de stratégie d’alerte suivantes sont configurées par défaut :

|**Déclencheur de stratégie d’alerte**|**Valeur par défaut**|
|:-----|:-----|
| Agrégation | Agrégation simple |
| Seuil | 4 activités |
| Fenêtre | 60 minutes |

>[!Note]
>Les paramètres de déclencheur de seuil de stratégie d’alerte pour les activités prend en charge une valeur minimale de 3 ou supérieure pour les stratégies de conformité des communications.

Vous pouvez modifier les paramètres par défaut des déclencheurs sur le nombre d’activités, la période des activités et pour des utilisateurs spécifiques dans les stratégies d’alerte dans la **page** Stratégies d’alerte dans le Centre de sécurité & conformité.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Modifier le niveau de gravité d’une stratégie d’alerte

Si vous souhaitez modifier le niveau de gravité affecté dans une stratégie d’alerte pour une stratégie de conformité des communications spécifique, complétez les étapes suivantes :

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le Centre de conformité Microsoft 365, allez à **Stratégies.**

3. Sélectionnez **l’alerte Office 365** sur la **page** Stratégies pour ouvrir la page **Stratégies** d’alertes dans le Centre de sécurité et conformité **Office 365 &.**

4. Cochez la case de la stratégie de conformité des communications que vous souhaitez mettre à jour, puis **sélectionnez Modifier la stratégie.**

5. Sous **l’onglet Description,** sélectionnez la zone de dépôt **Gravité** pour configurer le niveau d’alerte de stratégie.

6. Sélectionnez **Enregistrer** pour appliquer le nouveau niveau de gravité à la stratégie.

7. Sélectionnez **Fermer** pour quitter la page des détails de la stratégie d’alerte.

## <a name="power-automate-flows"></a>Flux Power Automate

[Microsoft Power Automate est un](/power-automate/getting-started) service de flux de travail qui automatise les actions entre les applications et les services. En utilisant des flux à partir de modèles ou créés manuellement, vous pouvez automatiser les tâches courantes associées à ces applications et services. Lorsque vous activez les flux Power Automate pour la conformité des communications, vous pouvez automatiser des tâches importantes pour les alertes et les utilisateurs. Vous pouvez configurer les flux Power Automate pour avertir les responsables lorsque les utilisateurs ont des alertes de conformité des communications et d’autres applications.

Les clients titulaires d’abonnements Microsoft 365 qui incluent la conformité des communications n’ont pas besoin de licences Power Automate supplémentaires pour utiliser le modèle power automate de conformité des communications par défaut recommandé. Le modèle par défaut peut être personnalisé pour prendre en charge votre organisation et couvrir les principaux scénarios de conformité des communications. Si vous choisissez d’utiliser des fonctionnalités Power Automate premium dans ces modèles, créez un modèle personnalisé à l’aide du connecteur de conformité Microsoft 365 ou utilisez des modèles Power Automate pour d’autres domaines de conformité dans Microsoft 365, vous aurez peut-être besoin de licences Power Automate supplémentaires.

>[!IMPORTANT]
>Recevez-vous des invites pour une validation de licence supplémentaire lors du test des flux Power Automate ? Votre organisation n’a peut-être pas encore reçu de mises à jour de service pour cette fonctionnalité d’aperçu. Des mises à jour sont déployées et toutes les organisations avec abonnement Microsoft 365 qui incluent la conformité des communications doivent avoir une prise en charge des licences pour les flux créés à partir des modèles Power Automate recommandés d’ici le 30 octobre 2020.

![Power Automate de conformité des communications](../media/communication-compliance-power-automate.png)

Le modèle Power Automate suivant est fourni aux clients pour prendre en charge l’automatisation des processus pour les alertes de conformité des communications :

- **Avertir le responsable lorsqu’un utilisateur a** une alerte de conformité des communications : certaines organisations peuvent avoir besoin d’une notification de gestion immédiate lorsqu’un utilisateur a une alerte de conformité des communications. Lorsque ce flux est configuré et sélectionné, le responsable de l’utilisateur du cas est envoyé un message électronique avec les informations suivantes sur toutes les alertes :
    - Stratégie applicable pour l’alerte
    - Date/heure de l’alerte
    - Niveau de gravité de l’alerte

### <a name="create-a-power-automate-flow"></a>Créer un flux Power Automate

Pour créer un flux Power Automate à partir d’un modèle par défaut recommandé, vous devez utiliser l’option Gérer les flux **Power Automate** à partir du contrôle **Automatiser** lorsque vous travaillez directement dans une alerte. Pour créer un flux Power Automate avec gérer les flux **Power Automate,** vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Pour créer un flux Power Automate à partir d’un modèle par défaut, vous pouvez effectuer les étapes suivantes :

1. Dans le Centre de conformité Microsoft 365, sélectionnez stratégies de conformité des communications et sélectionnez la stratégie avec l’alerte  >   à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate dans** le menu d’action d’alerte.
4. Dans la page **Power Automate,** sélectionnez un modèle par défaut dans les **modèles** de conformité des communications que vous souhaitez peut-être voir dans la section de la page.
5. Le flux affiche la liste des connexions incorporées nécessaires pour le flux et s’affiche si les états de connexion sont disponibles. Si nécessaire, mettez à jour les connexions qui ne sont pas affichées comme disponibles. Sélectionnez **Continuer**.
6. Par défaut, les flux recommandés sont pré-configurés avec la conformité de communication recommandée et les champs de données du service Microsoft 365 requis pour effectuer la tâche affectée pour le flux. Si nécessaire, personnalisez les composants de flux à l’aide du contrôle Afficher les **options** avancées et en configurant les propriétés disponibles pour le composant de flux.
7. Si nécessaire, ajoutez des étapes supplémentaires au flux en sélectionnant le **bouton Nouvelle étape.** Dans la plupart des cas, cette modification ne doit pas être nécessaire pour les modèles par défaut recommandés.
8. Sélectionnez **Enregistrer le** brouillon pour enregistrer le flux pour une configuration ultérieure, ou sélectionnez **Enregistrer** pour terminer la configuration du flux.
9. Sélectionnez **Fermer** pour revenir à la page de flux Power Automate. Le nouveau modèle est répertorié sous  la forme d’un flux sous l’onglet Mes flux et est automatiquement disponible à partir du contrôle Power Automate pour l’utilisateur qui a créé le flux lors de l’utilisation des alertes de conformité des communications.

### <a name="share-a-power-automate-flow"></a>Partager un flux Power Automate

Par défaut, les flux Power Automate créés par un utilisateur sont uniquement disponibles pour cet utilisateur. Pour que d’autres utilisateurs de conformité des communications ont accès et utilisent un flux, le flux doit être partagé par le créateur du flux. Pour partager un flux, vous devez utiliser le contrôle **Power Automate** lorsque vous travaillez directement dans une alerte.

Pour partager un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.
Pour partager un flux Power Automate, complétez les étapes suivantes :

1. Dans le Centre de conformité Microsoft 365, sélectionnez stratégies de conformité des communications et sélectionnez la stratégie avec l’alerte  >   à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate dans** le menu d’action d’alerte.
4. Dans la page **Flux Power Automate,** sélectionnez **l’onglet Mes flux ou** Flux **d’équipe.**
5. Sélectionnez le flux à partager, puis **sélectionnez Partager dans** le menu options de flux.
6. Sur la page de partage de flux, entrez le nom de l’utilisateur ou du groupe que vous souhaitez ajouter en tant que propriétaire du flux.
7. Dans la **boîte de dialogue Connexion utilisée,** sélectionnez **OK** pour reconnaître que l’utilisateur ou le groupe ajouté aura un accès total au flux.

### <a name="edit-a-power-automate-flow"></a>Modifier un flux Power Automate

Si vous devez modifier un flux, vous utiliserez le contrôle **Power Automate** lorsque vous travaillerez directement dans une alerte. Pour modifier un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Pour modifier un flux Power Automate, vous pouvez effectuer les étapes suivantes :

1. Dans le Centre de conformité Microsoft 365, sélectionnez stratégies de conformité des communications et sélectionnez la stratégie avec l’alerte  >   à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate dans** le menu d’action d’alerte.
4. Dans la page **Flux Power Automate,** sélectionnez flux à modifier. Sélectionnez **Modifier** dans le menu du contrôle de flux.
5. Sélectionnez **les paramètres de sélection** pour modifier un paramètre de composant de flux ou supprimer des  >   **ellipses**  >   pour supprimer un composant de flux.
6. Sélectionnez **Enregistrer,** **puis Fermez** pour terminer la modification du flux.

### <a name="delete-a-power-automate-flow"></a>Supprimer un flux Power Automate

Si vous devez supprimer un flux, vous utiliserez le contrôle **Power Automate** lorsque vous travaillerez directement dans une alerte. Pour supprimer un flux Power Automate, vous devez être membre d’au moins un groupe de rôles de conformité des communications.

Pour supprimer un flux Power Automate, vous devez effectuer les étapes suivantes :

1. Dans le Centre de conformité Microsoft 365, sélectionnez stratégies de conformité des communications et sélectionnez la stratégie avec l’alerte  >   à réviser.
2. Dans la stratégie, sélectionnez **l’onglet En attente** et sélectionnez une alerte en attente.
3. Sélectionnez **Power Automate dans** le menu d’action d’alerte.
4. Dans la page **Flux Power Automate,** sélectionnez flux à supprimer. Sélectionnez **Supprimer** dans le menu du contrôle de flux.
5. Dans la boîte de dialogue de confirmation de suppression, sélectionnez **Supprimer** pour supprimer le flux ou sélectionnez **Annuler** pour quitter l’action de suppression.

## <a name="reports-preview"></a>Rapports (aperçu)

Le nouveau tableau **de bord Rapports** est l’emplacement central pour afficher tous les rapports de conformité des communications. Les widgets de rapport fournissent un aperçu rapide des informations les plus couramment nécessaires pour une évaluation globale de l’état des activités de conformité des communications. Les informations contenues dans les widgets de rapport ne peuvent pas être exportées. Les rapports détaillés fournissent des informations détaillées sur des domaines spécifiques de conformité des communications et offrent la possibilité de filtrer, de grouper, de trier et d’exporter des informations lors de la révision.

![Tableau de bord des rapports de conformité des communications](../media/communication-compliance-reports-dashboard.png)

Le tableau **de bord Rapports contient** les widgets de rapport et les liens de rapports détaillés suivants :

- **Widget de correspondances de stratégie récente** : affiche le nombre de correspondances par stratégie active au fil du temps.
- **Éléments résolus par** widget de stratégie : affiche le nombre d’alertes de correspondance de stratégie résolues par stratégie au fil du temps.
- **Utilisateurs avec la plupart des** widgets de correspondance de stratégie : affiche les utilisateurs (ou les noms d’utilisateur anonymisés) et le nombre de correspondances de stratégie pour une période donnée.
- **Stratégie avec la plupart des widgets** de correspondances : affiche les stratégies et le nombre de correspondances pour une période donnée, classées de la plus haute à la plus faible pour les correspondances.
- **Escalades par** widget de stratégie : affiche le nombre d’escalades par stratégie sur une période donnée.
- **Paramètres** de stratégie et rapport détaillé sur l’état : fournit une analyse détaillée de la configuration et des paramètres de stratégie, ainsi que de l’état général de chacune des stratégies (correspondances et actions) sur les messages. Inclut les informations de stratégie et la façon dont les stratégies sont associées aux utilisateurs et groupes, aux emplacements, aux pourcentages d’avis, aux réviseurs, à l’état et à la dernière modification de la stratégie. Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.
- **Éléments et actions par rapport détaillé de stratégie** : examiner et exporter les éléments correspondants et les actions de correction par stratégie. Inclut les informations de stratégie et la façon dont les stratégies sont associées à :

    - Éléments en correspondance
    - Éléments escalades
    - Éléments résolus
    - Marqué comme conforme
    - Marqué comme non conforme
    - Marqué comme discutable
    - Éléments en attente de révision
    - Notification de l’utilisateur
    - Cas créé
    
    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.
- **Rapport détaillé sur l’élément** et les actions par emplacement : examiner et exporter les éléments correspondants et les actions de correction par emplacement Microsoft 365. Inclut des informations sur la façon dont les plateformes de charge de travail sont associées à :

    - Éléments en correspondance
    - Éléments escalades
    - Éléments résolus
    - Marqué comme conforme
    - Marqué comme non conforme
    - Marqué comme discutable
    - Éléments en attente de révision
    - Notification de l’utilisateur
    - Cas créé

    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.
- **Activité par rapport détaillé de l’utilisateur** : examiner et exporter les éléments correspondants et les actions de correction par utilisateur. Inclut des informations sur la façon dont les utilisateurs sont associés à :

    - Éléments en correspondance
    - Éléments escalades
    - Éléments résolus
    - Marqué comme conforme
    - Marqué comme non conforme
    - Marqué comme discutable
    - Éléments en attente de révision
    - Notification de l’utilisateur
    - Cas créé

    Utilisez *l’option* Exporter pour créer un fichier .csv contenant les détails du rapport.

## <a name="audit"></a>Audit

Dans certains cas, vous devez fournir des informations aux auditeurs de réglementation ou de conformité pour prouver la surveillance des activités et des communications des utilisateurs. Ces informations peuvent être un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque modification d’une stratégie de conformité des communications. Les stratégies de conformité des communications ont des pistes d’audit intégrées pour une préparation complète aux audits internes ou externes. Les historiques d’audit détaillés de chaque action de création, de modification et de suppression sont capturés par vos stratégies de communication pour fournir une preuve des procédures de surveillance.

>[!Important]
>L’audit doit être activé pour votre organisation avant que les événements de conformité des communications soient enregistrés. Pour activer l’audit, voir [Activer le journal d’audit.](communication-compliance-configure.md#step-2-required-enable-the-audit-log)

Pour afficher les activités de mise à jour des **stratégies** de conformité des communications, sélectionnez le contrôle Exporter les mises à jour de stratégie sur la page principale de n’importe quelle stratégie. Les rôles Administrateur *global* ou Administrateur de conformité des *communications* doivent vous être attribués pour exporter les activités de mise à jour. Cette action génère un fichier d’audit au format .csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Date à laquelle l’activité de mise à jour a été effectuée dans une stratégie. |
| **UserIds** | Utilisateur qui a effectué l’activité de mise à jour dans une stratégie. |
| **Operations** | Opérations de mise à jour effectuées sur la stratégie. |
| **AuditData** | Ce champ est la source de données principale pour toutes les activités de mise à jour de stratégie. Toutes les activités de mise à jour sont enregistrées et séparées par des délimiteur de virgule. |

Pour afficher les activités de révision de  la conformité des communications pour une stratégie, sélectionnez le contrôle Des activités de révision de l’exportation dans la **page** Vue d’ensemble d’une stratégie spécifique. Les rôles Administrateur *global* ou Administrateur de conformité des *communications* doivent vous être attribués pour exporter les activités de révision. Cette action génère un fichier d’audit au format .csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Date à laquelle l’activité de révision a été effectuée dans une stratégie. |
| **UserIds** | Utilisateur qui a effectué l’activité de révision dans une stratégie. |
| **Operations** | Les opérations de révision effectuées sur la stratégie. |
| **AuditData** | Ce champ est la source de données principale pour toutes les activités de révision de stratégie. Toutes les activités de révision sont enregistrées et séparées par des délimiteur de virgule. |

Vous pouvez également afficher les activités d’audit dans le journal d’audit unifié ou avec l’cmdlet [PowerShell Search-UnifiedAuditLog.](/powershell/module/exchange/search-unifiedauditlog)

Par exemple, l’exemple suivant renvoie les activités de toutes les activités de révision de surveillance (stratégies et règles) :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType AeD -Operations SupervisoryReviewTag
```

Cet exemple renvoie les activités de mise à jour de vos stratégies de conformité des communications :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -RecordType Discovery -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeleted
```

## <a name="transitioning-from-supervision-in-office-365"></a>Transition à partir de la surveillance dans Office 365

Les organisations qui utilisent des stratégies de surveillance dans Office 365 doivent immédiatement planifier la transition vers les stratégies de conformité des communications dans Microsoft 365 et doivent comprendre les points importants ci-après :

- La solution de surveillance dans Office 365 a été entièrement remplacée par la solution de conformité des communications dans Microsoft 365. Nous vous recommandons de créer de nouvelles stratégies de conformité des communications qui ont les mêmes paramètres que les stratégies de surveillance existantes pour utiliser les nouvelles améliorations d’examen et de correction. Lors de la transition vers la conformité des communications dans Microsoft 365, vous devez planifier l’exportation de données de rapport de supervision dans Office 365 si vous avez des exigences de stratégie de rétention de conformité internes.
- Les messages enregistrés sous surveillance dans les correspondances de stratégie Office 365 ne peuvent pas être déplacés ou partagés dans la conformité des communications dans Microsoft 365.
- Pour les organisations avec les deux solutions utilisées côte à côte pendant le processus de transition, les stratégies utilisées dans chaque solution doivent avoir des noms de stratégie uniques. Les groupes et les dictionnaires de mots clés personnalisés peuvent être partagés entre les solutions pendant une période de transition.

Pour plus d’informations sur la surveillance dans Office 365, consultez la feuille de route [Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour plus d’informations.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité des communications pour votre organisation Microsoft 365, voir Configurer la conformité des communications pour votre [organisation Microsoft 365.](communication-compliance-configure.md)
