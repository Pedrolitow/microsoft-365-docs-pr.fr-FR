---
title: Stratégies de surveillance
description: Découvrez comment utiliser des stratégies de surveillance dans Microsoft 365 pour capturer les communications des employés à des examens par des réviseurs désignés.
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
ms.custom: seo-marvel-apr2020
titleSuffix: Microsoft 365 Compliance
ms.openlocfilehash: 27c4d4603396089cb58cfed192f09d0db70cac5a
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47547584"
---
# <a name="supervision-policies"></a>Stratégies de surveillance

>[!IMPORTANT]
>Suite à la publication de la conformité des communications dans la conformité Microsoft 365 en février 2020, la surveillance dans Office 365 est retirée. Les stratégies de surveillance ne seront plus disponibles pour la création et les stratégies seront finalement supprimées, après une période prolongée d’accès en lecture seule.
>
>Si vous utilisez la surveillance, sachez que :
>
>- À compter du 15 juin 2020, les locataires n’auront pas la possibilité de créer de nouvelles stratégies de surveillance.
>- À compter du 31 août 2020, les stratégies existantes arrêteront la capture de nouveaux messages.
>- À compter du 26 octobre 2020, les stratégies existantes seront supprimées.
>
>Nous encourageons activement les clients qui explorent ou utilisent actuellement la surveillance dans Office 365 à utiliser la nouvelle solution de conformité des [communications](communication-compliance.md) pour répondre à vos exigences réglementaires ou de surveillance des communications avec un ensemble beaucoup plus riche de fonctionnalités intelligentes.

Les stratégies de surveillance dans Microsoft 365 vous permettent de capturer les communications des employés à des examens par des réviseurs désignés. Vous pouvez définir des stratégies spécifiques qui capturent le courrier électronique interne et externe, Microsoft Teams ou des communications tierces dans votre organisation. Les réviseurs peuvent ensuite examiner les messages pour s’assurer qu’ils sont conformes aux normes de message de votre organisation et les résoudre avec le type de classification.

Ces stratégies peuvent également vous aider à surmonter de nombreux défis de conformité modernes, notamment :

- Surveillance de l’augmentation des types de canaux de communication
- Volume croissant de données de message
- L’application & le risque d’amendes

Dans certaines organisations, il peut y avoir une séparation des tâches entre le support technique et le groupe de gestion de la conformité. Microsoft 365 prend en charge la séparation entre la configuration des fonctionnalités de stratégie de surveillance et la configuration des stratégies pour les communications capturées. Par exemple, le groupe it pour une organisation peut être responsable de la configuration des autorisations de rôle et des groupes pour prendre en charge les stratégies de surveillance qui sont configurées et gérées par l’équipe de conformité de l’organisation.

Pour obtenir une vue d’ensemble rapide des stratégies de surveillance, voir la vidéo de stratégie [de surveillance](https://youtu.be/C3Y8WZ7o_dI) sur le [canal Microsoft Mechanics](https://www.youtube.com/user/OfficeGarageSeries).

## <a name="transitioning-from-supervision"></a>Transition à partir de la surveillance

Les organisations qui utilisent des stratégies de surveillance et qui prévoient de passer aux stratégies de conformité des communications dans [Microsoft 365](communication-compliance.md) doivent comprendre les points importants ci-après :

- La solution de surveillance dans Microsoft 365 sera entièrement remplacée par la solution de conformité des communications dans Microsoft 365. Pour les organisations qui transitionnt vers la conformité des communications à partir des stratégies de surveillance, nous vous recommandons de créer de nouvelles stratégies de conformité des communications qui ont les mêmes *conditions* que les stratégies de surveillance existantes pour permettre de nouvelles améliorations d’examen et de correction. Lors de la transition vers la conformité des communications dans Microsoft 365, vous devez planifier l’exportation des données de rapports à partir de la supervision si vous avez des exigences de stratégie de rétention de conformité interne.
- En attendant, les organisations peuvent utiliser les deux solutions côte à côte jusqu’à la migration complète, mais les stratégies utilisées dans chaque solution doivent avoir des noms de *stratégie uniques.* Les groupes et les dictionnaires de mots clés personnalisés peuvent être partagés entre les solutions pendant la période de transition.
- Les messages enregistrés sous surveillance dans les correspondances de stratégie Microsoft 365 ne peuvent pas être déplacés ou partagés dans la conformité des communications dans Microsoft 365.

Pour plus d’informations sur la surveillance dans Office 365, consultez la feuille de [route Microsoft 365](https://www.microsoft.com/microsoft-365/roadmap) pour plus d’informations.

## <a name="scenarios-for-supervision-policies"></a>Scénarios de stratégies de surveillance

Les stratégies de surveillance peuvent aider à surveiller les communications dans votre organisation dans plusieurs domaines :

- **Stratégies d’entreprise**

    Les employés doivent se conformer à une utilisation acceptable, à des normes déontologiques et à d’autres stratégies d’entreprise dans toutes leurs communications professionnelles. Les stratégies de surveillance peuvent détecter les violations de stratégie et vous aider à prendre des mesures correctives pour atténuer ces types d’incidents. Par exemple, vous pouvez surveiller les violations potentielles des ressources humaines telles que le harcèlement ou l’utilisation d’un langage inapproprié ou choquant dans les communications des employés.

- **Gestion des risques**

    Les organisations sont responsables de toutes les communications distribuées dans l’ensemble de leur infrastructure et de leurs systèmes réseau d’entreprise. L’utilisation de stratégies de surveillance pour identifier et gérer l’exposition et les risques juridiques potentiels peut contribuer à réduire les risques avant qu’ils ne endommagent les opérations de l’entreprise. Par exemple, vous pouvez surveiller les communications non autorisées de votre organisation pour les projets confidentiels, tels que les acquisitions à venir, les fusions, les divulgations de revenus, les réorganisations ou les changements d’équipe de direction.

- **Conformité réglementaire**

    La plupart des organisations doivent se conformer à certains types de normes de conformité réglementaire dans le cadre de leurs procédures normales d’exploitation. Ces réglementations obligent souvent les organisations à implémenter un type de processus de surveillance ou de supervision pour la messagerie adaptée à leur secteur d’activité. La règle 3110 de l’Autorité de régulation financière (FINRA) est un bon exemple d’obligation pour les organisations de mettre en place des procédures de surveillance pour surveiller les activités de leurs employés et les types d’entreprises dans lesquelles elles s’engagent. Un autre exemple peut être la nécessité de surveiller les courtiers de votre organisation afin de se protéger contre les activités potentielles de corruption d’argent, de délit d’initié, de secret ou d’infraction. Les stratégies de surveillance peuvent aider votre organisation à répondre à ces exigences en fournissant un processus de surveillance et de création de rapports sur les communications d’entreprise.

## <a name="components"></a>Composants

### <a name="supervision-policy"></a>Stratégie de surveillance

Vous créez des stratégies de surveillance dans le Centre de conformité. Ces stratégies définissent les communications et les utilisateurs qui sont soumis à révision dans votre organisation, définissent des conditions personnalisées que les communications doivent respecter et spécifient qui doit effectuer les révisions. Les utilisateurs inclus dans le groupe de rôles Vérification de surveillance peuvent configurer des stratégies et toute personne à qui ce rôle est attribué peut accéder à la page Surveillance dans le Centre de conformité.

### <a name="supervised-users"></a>Utilisateurs supervisés

Avant de commencer à utiliser la surveillance, vous devez déterminer qui a besoin de revoir ses communications. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou groupes de personnes à superviser. Les groupes Microsoft 365, les listes de distribution basées sur Exchange et les canaux Microsoft Teams sont quelques exemples. Vous pouvez également exclure des utilisateurs ou des groupes spécifiques de la surveillance avec un groupe supervisé ou une liste de groupes.

>[!IMPORTANT]
>Les utilisateurs surveillés par des stratégies de surveillance doivent avoir une licence de conformité Microsoft 365 E5, une licence Office 365 Entreprise E3 avec le module de conformité avancée, être inclus dans un abonnement Office 365 Entreprise E5 ou être inclus dans un abonnement Microsoft 365 E5. Si vous n’avez pas d’offre Entreprise E5 existante et que vous souhaitez essayer la supervision, vous pouvez vous inscrire à une version d’essai [d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

### <a name="reviewers"></a>Relecteurs

Lorsque vous créez une stratégie de surveillance, vous devez déterminer qui effectuera les révisions des messages des utilisateurs supervisés. Dans la stratégie, les adresses de messagerie des utilisateurs identifient les individus ou les groupes de personnes qui doivent réviser les communications contrôlées. Tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online.

### <a name="groups-for-supervised-users-and-reviewers"></a>Groupes pour les utilisateurs et les relecteurs supervisés

Pour simplifier votre configuration, créez des groupes pour les personnes qui ont besoin de réviser leurs communications et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez surveiller les communications entre deux groupes distincts de personnes, ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

Lorsque vous sélectionnez un groupe Microsoft 365 pour les utilisateurs supervisés, la stratégie surveille le contenu de la boîte aux lettres partagée et les canaux Microsoft Teams associés au groupe. Lorsque vous sélectionnez une liste de distribution, la stratégie surveille les boîtes aux lettres utilisateur individuelles.

### <a name="supported-communication-types"></a>Types de communications pris en charge

Avec les stratégies de surveillance, vous pouvez choisir de surveiller les messages dans une ou plusieurs des plateformes de communication suivantes :

- **E-mail Exchange :** Les boîtes aux lettres hébergées sur Exchange Online dans le cadre de votre abonnement Microsoft 365 sont toutes éligibles pour la surveillance des messages. Les messages électroniques et pièces jointes correspondant aux conditions de stratégie de surveillance sont immédiatement disponibles pour la surveillance et dans les rapports de surveillance. Les types de pièces jointes pris en charge pour la supervision sont les mêmes que les types de fichiers pris en charge pour les inspections de contenu de règle de flux [de messagerie Exchange.](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection)

- **Microsoft Teams :** Les communications de conversation et les pièces jointes associées dans les canaux Microsoft Teams publics et privés et les conversations individuelles peuvent être supervisées. Les conversations Teams correspondant aux conditions de stratégie de surveillance sont traitées une fois toutes les 24 heures, puis sont disponibles pour la surveillance et dans les rapports de surveillance. Utilisez les configurations de gestion de groupe suivantes pour superviser les conversations des utilisateurs individuels et les communications de canal dans Teams :

    - **Pour la surveillance des conversation Teams :** Affecter des utilisateurs individuels ou affecter un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de surveillance. Cette configuration est pour les relations utilisateur/conversation 1-à-1 ou 1-à-plusieurs.
    - **Pour les communications de canal Teams :** Affectez à la stratégie de surveillance chaque canal Microsoft Team ou groupe Microsoft 365 que vous souhaitez surveiller et qui contient un utilisateur spécifique. Si vous ajoutez le même utilisateur à d’autres canaux Microsoft Teams ou groupes Microsoft 365, n’oubliez pas d’ajouter ces nouveaux canaux et groupes à la stratégie de surveillance.

- **Skype Entreprise Online :** Les communications de conversation et les pièces jointes associées dans Skype Entreprise Online peuvent être supervisées. Les conversations Skype Entreprise Online correspondant aux conditions de la stratégie de surveillance sont traitées une fois toutes les 24 heures, puis sont disponibles pour la surveillance et dans les rapports de surveillance. Les conversations supervisées sont provenant de [conversations précédentes enregistrées dans Skype Entreprise Online.](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2)  Utilisez la configuration de gestion de groupe suivante pour superviser les communications de conversation utilisateur dans Skype Entreprise Online :

    - **Pour la surveillance des conversation Skype Entreprise Online :** Affecter des utilisateurs individuels ou affecter un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de surveillance. Cette configuration est pour les relations utilisateur/conversation 1-à-1 ou 1-à-plusieurs.

- **Sources tierces :** Vous pouvez contrôler les communications à partir de sources tierces (par exemple, à partir de Facebook ou DropBox) pour les données importées dans les boîtes aux lettres de votre organisation. [Découvrez comment importer des données tierces.](archiving-third-party-data.md)

Par défaut, les communications capturées sur ces plateformes sont conservées pendant sept ans pour chaque stratégie, même si les utilisateurs quittent votre organisation et que leur boîte aux lettres est supprimée.

### <a name="policy-settings"></a>Paramètres de stratégie

#### <a name="direction"></a>Direction

Par défaut, la **condition Direction** est affichée et ne peut pas être supprimée. Les paramètres de direction de communication dans une stratégie sont choisis individuellement ou ensemble :

- **Entrant :** vous  pouvez choisir Entrant  pour passer en revue les communications envoyées aux personnes que vous avez choisi de superviser à partir de **personnes** non incluses dans la stratégie.
- **Sortant :** vous pouvez choisir Sortant si vous  souhaitez passer en  revue les communications envoyées par les personnes que vous avez choisi de superviser aux personnes qui ne sont pas incluses dans la stratégie. 
- **Interne**: vous pouvez choisir **Interne** pour passer en revue les communications envoyées **entre** les personnes que vous avez identifiées dans la stratégie.

#### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous avez la possibilité d’inclure des types d’informations sensibles dans le cadre de votre stratégie de surveillance. Les types d’informations sensibles sont des types de données prédéfin définis ou personnalisés qui permettent d’identifier et de protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Dans le cadre de la protection contre la perte de données [(DLP),](data-loss-prevention-policies.md)la configuration des informations sensibles peut utiliser des modèles, la proximité des caractères, des niveaux de confiance et même des types de données personnalisés pour vous aider à identifier et à indiquer le contenu qui peut être sensible. Les types d’informations sensibles par défaut sont :

- Financier
- Santé et santé
- Confidentialité
- Type d’informations personnalisé

Pour en savoir plus sur les détails des informations sensibles et les modèles inclus dans les types par défaut, voir Définitions d’entités de [type d’informations sensibles.](sensitive-information-type-entity-definitions.md)

#### <a name="custom-keyword-dictionaries"></a>Dictionnaires de mots clés personnalisés

Configurez des dictionnaires de mots clés personnalisés (ou lexicons) pour fournir une gestion simple des mots clés propres à votre organisation ou à votre secteur d’activité. Les dictionnaires de mots clés prendre en charge jusqu’à 100 000 To de termes (post-compression) dans le dictionnaire et ne prendre en charge que n’importe quelle langue. La limite du client est également de 100 Ko après compression. Si nécessaire, vous pouvez appliquer plusieurs dictionnaires de mots clés personnalisés à une stratégie unique ou avoir un seul dictionnaire de mots clés par stratégie. Ces dictionnaires sont affectés dans une stratégie de surveillance et peuvent être issus d’un fichier (par exemple, une liste .csv ou .txt) ou d’une liste que vous pouvez importer dans le Centre de [conformité.](create-a-keyword-dictionary.md)

#### <a name="offensive-language"></a>Langage choquant

Surveillez les messages électroniques envoyés ou reçus dans votre organisation pour les langages choquants. Le modèle utilise une combinaison d’apprentissage automatique, d’intelligence artificielle et de mots clés pour identifier le langage dans les messages électroniques susceptibles de violer les stratégies de lutte contre le harcèlement et les agresseurs. Le modèle de langage choquant prend actuellement en charge les mots clés anglais et surveille le corps des messages électroniques.

>[!NOTE]
>Créez une [stratégie de protection contre la perte de](create-test-tune-dlp-policy.md) données avec un dictionnaire de mots clés [personnalisé](create-a-keyword-dictionary.md) de termes bloqués si vous devez :
>
>- surveiller les communications De Microsoft Teams dans votre organisation pour un langage choquant
>- empêcher ou bloquer le langage choquant dans les communications de votre organisation ;

Le modèle ne fournit pas une liste exhaustive des langages choquants. En outre, les normes linguistiques et culturelles changent continuellement et, à la lumière de ces exigences, Microsoft se réserve le droit de mettre à jour le modèle à sa discrétion. Bien que le modèle puisse aider votre organisation à surveiller un langage choquant, il n’est pas destiné à fournir l’unique moyen de votre organisation de surveiller ou de traiter ce langage. Votre organisation, et non Microsoft, reste responsable de toutes les décisions relatives à la surveillance et au blocage du langage choquant.

Le modèle de langage choquant surveille les messages électroniques pour les sentiments associés aux types de langage suivants :

|**Type (Type)**|**Description**|
|:-----|:-----|
| **Blasphémités** | Expressions qui resserrent la plupart des personnes. |
| **Slurs** | Expressions qui expriment des préjudices envers des groupes particuliers (par exemple, la course, l’ancienneté, l’orientation sexuelle, le handicap). |
| **Nts** | Expressions qui peuvent provoquer des violences ou des violences, ou qui peuvent être à l’origine d’une violence ou d’une violence. |
| **Expressions masquées** | Expressions pour lesquelles la signification ou la prononciation est identique à un autre terme plus choquant. |

#### <a name="conditional-settings"></a>Paramètres conditionnels
<a name="ConditionalSettings"> </a>

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications à partir de la messagerie électronique et de sources tierces de votre organisation (par exemple, à partir de Facebook ou DropBox).

Le tableau suivant en explique plus sur chaque condition.
  
|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le message est reçu de l’un de ces domaines** <br><br> **Le message n’est reçu d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages reçus. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse e-mail entré est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez surveiller tous les messages électroniques provenant d’un domaine spécifique, mais que vous souhaitez exclure les messages qui n’ont pas besoin d’être contrôlés (bulletins d’informations, annonces, etc.), vous devez configurer la condition selon qu’un **message** n’est reçu d’aucune de ces conditions de domaine qui exclut l’adresse e-mail (exemple « newsletter@contoso.com »). |
| **Le message est envoyé à l’un de ces domaines** <br><br> **Le message n’est envoyé à aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages envoyés. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez surveiller tous les messages envoyés à un domaine spécifique, mais que vous souhaitez exclure les messages envoyés qui ne doivent pas être contrôlés, vous devez configurer deux conditions : <br> - Un **message est envoyé à l’une de** ces conditions de domaine qui définit le domaine (« contoso.com ») ET <br> - Un **message n’est envoyé à** aucune condition de ces domaines qui exclut l’adresse de messagerie « subscriptions@contoso.com »). |
| **Le message est classé avec l’une de ces étiquettes** <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Pour appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées sont choisies dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur les étiquettes de rétention, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)|
| **Le message contient l’un de ces mots** <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot ou expression et séparez-les par une virgule. Chaque mot que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](supervision-policies.md#Matchwords).|
| **La pièce jointe contient l’un de ces mots** <br><br> **La pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus d’une pièce jointe de message (par exemple, un document Word), entrez chaque mot ou expression et séparez-les par une virgule. Chaque mot que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](supervision-policies.md#Matchwords).|
| **La pièce jointe est l’un de ces types de fichiers** <br><br> **La pièce jointe n’est pas de ces types de fichiers** | Pour contrôler les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichier (telles que .exe ou .pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichier, entrez-les sur des lignes distinctes. Une seule extension de pièce jointe doit correspondre pour que la stratégie s’applique.|
| **La taille du message est supérieure à** <br><br> **La taille du message n’est pas supérieure à** | Pour passer en revue les messages en fonction d’une certaine taille, utilisez ces conditions pour spécifier la taille maximale ou minimale d’un message avant qu’il ne soit soumis à révision. Par exemple, si  vous spécifiez que la taille du message est supérieure à \> **1,0 Mo,** tous les messages de 1,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La pièce jointe est supérieure à** <br><br> **La pièce jointe n’est pas supérieure à** | Pour passer en revue les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale d’une pièce jointe avant que le message et ses pièces jointes soient soumis à révision. Par exemple, si  vous spécifiez que la pièce jointe est supérieure à \> **2,0 Mo,** tous les messages avec des pièces jointes de 2,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
   
##### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes
<a name="Matchwords"></a> Chaque mot que vous entrez et séparez par une virgule est appliqué séparément (un seul mot doit s’appliquer à la condition de stratégie à appliquer au message électronique ou à la pièce jointe). Par exemple, nous allons utiliser la condition « **Message**» contient l’un de ces mots, avec les mots clés « banker » et « insider trading » séparés par une virgule (bancaire, délit d’initié). La stratégie s’applique à tous les messages qui incluent le mot « banker » ou l’expression « insider trading ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots dans le message ou la pièce jointe doivent correspondre exactement à ce que vous entrez.

Pour analyser les messages électroniques et les pièces [](create-test-tune-dlp-policy.md) jointes pour les [](create-a-keyword-dictionary.md) mêmes mots clés, créez une stratégie de protection contre la perte de données avec un dictionnaire de mots clés personnalisé pour les termes que vous souhaitez surveiller. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **ou** dans la pièce jointe de l’e-mail. L’utilisation des paramètres de stratégie conditionnelle standard ( Le *message* contient l’un de ces mots et  *la* pièce jointe contient l’un de ces mots ) pour identifier les termes dans les messages et dans les pièces jointes, les termes sont présents dans le message et la pièce jointe.
  
##### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer quand appliquer la stratégie aux éléments de communication. Lorsque vous définissez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « commerce » et est supérieur à 2 Mo. Toutefois, si le message contient également les mots « Approuvé par Contoso financial », la stratégie ne doit pas s’appliquer. Par conséquent, dans ce cas, les trois conditions seraient les suivantes :
  
- **Le message contient l’un de ces mots,** avec le mot clé « trade »

- **La taille du message est supérieure** à , avec la valeur 2 Mo

- **Le message ne contient aucun de ces mots,** avec les mots clés « Approuvé par l’équipe financière de Contoso »

#### <a name="review-percentage"></a>Pourcentage de révision

Si vous voulez réduire la quantité de contenu à réviser, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de supervision. Un échantillon aléatoire de contenu est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les réviseurs examinent tous les éléments, vous pouvez entrer **100 %** dans une stratégie de surveillance.

## <a name="monitor--manage"></a>Surveiller & gérer

Il est facile de surveiller les résultats de vos stratégies de surveillance et d’appliquer une balise de résolution. Vous pouvez voir rapidement :

- État des éléments révisés
- Utilisateurs et groupes sous surveillance
- Utilisateurs et groupes désignés comme réviseurs

### <a name="supervision-policy-dashboard"></a>Tableau de bord de stratégie de surveillance

Utilisez le tableau de bord de stratégie de surveillance pour gérer les résultats de la stratégie de surveillance et résoudre les éléments en suspens. Ce tableau de bord permet aux réviseurs d’afficher les éléments qui doivent être examinés, d’agir sur un élément et de passer en revue les résultats des éléments précédemment révisés et résolus pour chaque stratégie de surveillance. Vous pouvez accéder au tableau de bord de la stratégie de surveillance dans le Centre de conformité **à l’ouverture** de la surveillance  >  *de votre stratégie*  >  **personnalisée.**

#### <a name="dashboard-home"></a>Accueil du tableau de bord

La page **d’accueil** du tableau de bord contient plusieurs sections pour vous aider à agir rapidement sur vos stratégies de surveillance. Vous pouvez :

- Passer rapidement en revue les points forts en attente et résolus pour la semaine
- Voir la liste des utilisateurs supervisés et des groupes supervisés pour la stratégie sélectionnée
- Consultez la liste des réviseurs et des équipes de révision pour la stratégie sélectionnée
- Voir les plateformes de communication dont le contenu est surveillé pour la stratégie

#### <a name="review-tab"></a>Onglet Révision

**L’onglet** Révision permet aux réviseurs de classifier et de résoudre les éléments identifiés par la stratégie sélectionnée. Vous pouvez :

- Filtrez les éléments en attente, conformes, non conformes et discutables.
- Marquer un élément comme conforme, non conforme ou discutable. Vous pouvez également enregistrer un commentaire avec l’élément pour clarifier l’action de marquage prise.
- Baliser plusieurs éléments en bloc comme étant conformes, non conformes ou discutables. Vous pouvez également enregistrer un commentaire avec plusieurs éléments pour clarifier l’action de marquage prise.
- Afficher l’historique du marquage pour un seul élément. Inclut qui a résolu l’élément, la date et l’heure de l’action, la balise de résolution et tous les commentaires inclus.
- Reclassez les éléments précédemment examinés comme conformes, non conformes ou discutables. Vous pouvez également enregistrer un commentaire avec un ou plusieurs éléments pour clarifier l’action de reclassement prise.

#### <a name="resolved-items-tab"></a>Onglet Éléments résolus

**L’onglet Éléments résolus** permet aux réviseurs d’afficher tous les éléments précédemment résolus pour la stratégie sélectionnée. Vous pouvez :

- Afficher et trier rapidement l’objet, l’expéditeur et la date des éléments résolus
- Afficher la classification et l’historique des commentaires d’un élément sélectionné

## <a name="reports"></a>Rapports

Utilisez les rapports de surveillance pour voir l’activité de révision au niveau de la stratégie et du réviseur. Pour chaque stratégie, vous pouvez également afficher des statistiques en direct sur l’état actuel de l’activité de révision. Vous pouvez utiliser les rapports de surveillance pour :
  
- Vérifiez que vos stratégies fonctionnent comme prévu.
- Découvrez le nombre de communications qui doivent être revue.
- Découvrez le nombre de communications non conformes et les communications qui passent l’examen. Ces informations peuvent vous aider à décider s’il faut affiner vos stratégies ou modifier le nombre de réviseurs.

### <a name="view-the-supervision-report"></a>Afficher le rapport de surveillance

1. Connectez-vous au [Centre de conformité avec](https://compliance.microsoft.com) les informations d’identification d’un compte administrateur avec les autorisations d’affichage des rapports de surveillance.
2. Go to either **Reports** \> **Dashboard** or **Supervision** to view the supervision reporting widget for a summary of current supervision policy activity.
3. Sélectionnez le widget **de** surveillance pour ouvrir la page de rapport détaillée.

>[!NOTE]
>Si vous n’êtes pas en mesure d’accéder à la **page** Rapports, vérifiez que vous êtes membre du groupe de rôles Vérification de surveillance, comme décrit dans Rendre la surveillance disponible dans [votre organisation.](configure-supervision-policies.md) L’inclusion dans ce groupe de rôles vous permet de créer et de gérer des polices de surveillance et d’exécuter le rapport.
  
### <a name="how-to-use-the-report"></a>Utilisation du rapport

Ce rapport répertorie chaque stratégie et le nombre de communications à chaque étape du processus de révision. Utilisez le rapport pour :
  
- Afficher les données pour toutes les stratégies ou des stratégies spécifiques.
- Afficher les données regroupées par type de balise, relecteur ou type de message.
- Exporter des données vers un fichier CSV en fonction de la date d’activité, de la stratégie et de l’activité du réviseur.
- Filtrer les données en fonction de la date d’activité, du type de balise, du réviseur et du type de message.

Voici une répartition des valeurs affichées dans la colonne **Type de** balise.
  
|**Type de balise**|**Ce que cela signifie**|
|:-----|:-----|
| **Non révisé** | Nombre d’e-mails non vérifiés pour le moment. Ces e-mails sont en attente de révision dans le tableau de bord de surveillance Microsoft 365.
| **Compliant** | Nombre d’e-mails révisés et marqués comme conformes. Ces messages doivent encore être résolus. |
| **Questionnable** | Nombre d’e-mails révisés et marqués comme discutables. Sert d’indicateur à d’autres réviseurs pour vérifier si un e-mail doit faire l’objet d’un examen de conformité. Ces messages doivent encore être résolus. |
| **Non conforme (actif)** | Nombre d’e-mails non conformes que les réviseurs examinent actuellement. |
| **Non conforme (résolu)** | Nombre d’e-mails non conformes que les réviseurs ont examinés et résolus. |
| **Stratégie de hit** | Nombre total (quotidien) de messages provenant de sources de données Exchange, Teams et tierces qui correspondent à une ou plusieurs conditions définies dans une stratégie de surveillance |
| **Dans Purview** | Nombre total (quotidien) de messages provenant d’Exchange, de Teams et de sources de données tierces analysés par une stratégie de surveillance |
| **Resolved** | Nombre total de messages provenant d’Exchange, Teams et de sources de données tierces classés **comme résolus**|

>[!NOTE]
>Les stratégies de surveillance doivent être provisionées avant qu’elles n’apparaissent dans les rapports. Si les stratégies sont supprimées, les données historiques sont toujours affichées. Toutefois, ils sont indiqués comme une « stratégie inexistante » et la fonction **Export** n’est pas disponible.

## <a name="audit"></a>Audit

Dans certains cas, vous devez fournir des informations aux auditeurs de réglementation ou de conformité pour prouver la surveillance des activités et des communications des employés. Ces informations peuvent être un résumé de toutes les activités de surveillance associées à une stratégie définie ou à chaque modification d’une stratégie de surveillance. Les stratégies de surveillance ont des pistes d’audit intégrées pour une préparation complète aux audits internes ou externes. Les historiques d’audit détaillés de chaque action surveillée par vos stratégies de surveillance fournissent une preuve des procédures de surveillance.

Afficher les activités d’audit dans le journal d’audit unifié ou avec l’cmdlet [PowerShell Search-UnifiedAuditLog.](https://docs.microsoft.com/powershell/module/exchange/search-unifiedauditlog)

Par exemple, l’exemple suivant renvoie les activités de toutes les activités de révision de surveillance (stratégies et règles) et répertorie des informations détaillées pour chacune d’elles :

```PowerShell
Search-UnifiedAuditLog -StartDate 3/1/2019 -EndDate ([System.DateTime]::Now) -RecordType DataGovernance -ResultSize 5000 | Where-Object {$_.Operations -like "*SupervisoryReview*"}  | fl CreationDate,Operations,UserIds,AuditData
```

Cet exemple renvoie les activités de mise à jour de vos stratégies de conformité des communications :

```PowerShell
Search-UnifiedAuditLog -StartDate $startDate -EndDate $endDate -Operations SupervisionPolicyCreated,SupervisionPolicyUpdated,SupervisionPolicyDeletedAuditData
```

Outre les informations fournies dans les rapports et les journaux de surveillance, vous pouvez également utiliser l’cmdlet [PowerShell Get-SupervisoryReviewActivity](https://docs.microsoft.com/powershell/module/exchange/get-supervisoryreviewactivity) pour renvoyer une liste détaillée complète de toutes les activités de stratégie de surveillance.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer des stratégies de surveillance pour votre organisation, voir [Configurer des stratégies de surveillance.](configure-supervision-policies.md)
