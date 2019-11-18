---
title: Référence de la fonctionnalité de conformité de la communication (aperçu)
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
description: Référence de la fonctionnalité de conformité de la communication dans Microsoft 365. Découvrez les détails et les spécifications de chacun des composants fonctionnels.
ms.openlocfilehash: 42e47807743c74663effcb50d3c36156072e38cf
ms.sourcegitcommit: b424ea039c5915975f3efce8793bfc8dd2fdf906
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/07/2019
ms.locfileid: "38685796"
---
# <a name="communication-compliance-feature-reference-preview"></a>Référence de la fonctionnalité de conformité de la communication (aperçu)

## <a name="policies"></a>Stratégies

Vous créez des stratégies de conformité des communications pour les organisations Microsoft 365 dans le centre de conformité Microsoft 365. Si vous disposez d’une organisation Office 365, vous [configurerez des stratégies de surveillance](configure-supervision-policies.md) dans le centre de sécurité et conformité Office 365. Les stratégies de conformité des communications définissent les communications et les utilisateurs qui font l’objet d’une vérification dans votre organisation, définissent les conditions personnalisées que les communications doivent respecter et spécifie qui doit effectuer des révisions. Les utilisateurs inclus dans le groupe de rôles d' **administrateur de vérification de surveillance** peuvent configurer des stratégies et quiconque disposant de ce rôle peut accéder à la page conformité de la **communication** dans le centre de conformité Microsoft 365. Si nécessaire, vous pouvez exporter l’historique des modifications apportées à une stratégie dans un fichier. csv qui inclut également l’état des alertes en attente de révision, des éléments escaladés et des éléments résolus. Les stratégies ne peuvent pas être renommées et peuvent être supprimées lorsqu’elles ne sont plus nécessaires.

> [!NOTE]
> Les stratégies de surveillance créées dans le centre de sécurité et conformité Office 365 pour les abonnements Office 365 ne peuvent pas migrer vers Microsoft 365. Si vous effectuez une migration à partir d’un abonnement Office 365 vers un abonnement Microsoft 365, vous devrez créer de nouvelles stratégies de conformité de communication pour remplacer les stratégies de surveillance existantes.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de stratégie sont des paramètres de stratégie prédéfinis que vous pouvez utiliser pour créer rapidement des stratégies pour répondre aux scénarios de conformité courants. Chacun de ces modèles présente des différences dans les conditions et l’étendue, et tous les modèles utilisent les mêmes types de signaux d’analyse. Vous pouvez choisir parmi les modèles de stratégie suivants :

|**Catégorie**|**Modèle de stratégie**|**Détails**|
|:-----|:-----|:-----|
| **Langage offensant et blocage du harcèlement** | Surveiller les communications pour un langage offensant | -Emplacements : Exchange, teams, Skype entreprise <br> -Direction : entrant, sortant, interne <br> -Pourcentage de révision : 100% <br> -Conditions : classifieur de langue offensant |
| **Informations sensibles** | Surveiller les communications pour les informations sensibles | -Emplacements : Exchange, teams, Skype entreprise <br> -Direction : entrant, sortant, interne <br> -Pourcentage de révision : 10% <br> -Conditions : informations sensibles, modèles et types de contenu prédéfinis, option de dictionnaire personnalisé, pièces jointes dont la taille est supérieure à 1 Mo |
| **Conformité réglementaire** | Surveiller les communications pour les informations relatives à la conformité réglementaire financière | -Emplacements : Exchange, teams, Skype entreprise <br> -Direction : entrant, sortant <br> -Pourcentage de révision : 10% <br> -Conditions : option de dictionnaire personnalisé, pièces jointes d’une taille supérieure à 1 Mo |

## <a name="supervised-users"></a>Utilisateurs supervisés

Avant de commencer à utiliser la conformité de la communication, vous devez déterminer qui a besoin de ses communications. Dans la stratégie, les adresses de messagerie des utilisateurs identifient des individus ou des groupes de personnes à superviser. Les groupes Office 365, les listes de distribution Exchange et les canaux Microsoft teams sont des exemples de ces groupes. Vous pouvez également exclure des utilisateurs ou des groupes spécifiques de l’analyse à l’aide d’un groupe d’exclusion spécifique ou d’une liste de groupes.

> [!IMPORTANT]
> Les utilisateurs couverts par les stratégies de conformité des communications doivent disposer d’une licence de conformité Microsoft 365 E5, d’une licence Office 365 entreprise E3 avec le complément de conformité avancé ou être inclus dans un abonnement Office 365 entreprise E5. Si vous ne disposez pas d’un plan entreprise E5 existant et que vous souhaitez essayer la conformité de la communication, vous pouvez vous [inscrire pour obtenir une version d’évaluation d’Office 365 entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).

## <a name="reviewers"></a>Relecteurs

Lorsque vous créez une stratégie de conformité de communication, vous devez déterminer qui effectue des révisions des messages des utilisateurs supervisés. Dans la stratégie, les adresses de messagerie des utilisateurs identifient des personnes ou des groupes de personnes pour examiner les communications surveillées. Tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online et doivent disposer des rôles de **gestion des dossiers** et de **révision** .

## <a name="groups-for-supervised-users-and-reviewers"></a>Groupes pour les utilisateurs et les relecteurs surveillés

Pour simplifier votre configuration, créez des groupes pour les personnes qui ont besoin de leurs communications et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez analyser les communications entre deux groupes distincts de personnes, ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

Lorsque vous sélectionnez un groupe Office 365 pour les utilisateurs supervisés, la stratégie analyse le contenu de la boîte aux lettres Office 365 partagée et les canaux Microsoft teams associés au groupe. Lorsque vous sélectionnez une liste de distribution, la stratégie analyse les boîtes aux lettres des utilisateurs individuels.

## <a name="supported-communication-types"></a>Types de communication pris en charge

Avec les stratégies de conformité de communication, vous pouvez choisir d’analyser les messages d’une ou plusieurs des plateformes de communication suivantes en tant que groupe ou en tant que sources autonomes. Les communications capturées sur ces plateformes sont conservées pendant sept ans pour chaque stratégie par défaut, même si les utilisateurs quittent votre organisation et que leur boîte aux lettres est supprimée.

- **Microsoft teams**: les communications de conversation et les pièces jointes associées dans les canaux Microsoft teams publics et privés et dans des conversations individuelles peuvent être analysées. Les conversations de teams correspondant aux conditions de stratégie de conformité de communication sont traitées une fois toutes les 24 heures, puis disponibles dans les rapports de conformité des communications. Utilisez les configurations de gestion de groupe suivantes pour superviser les conversations des utilisateurs individuels et les communications de canal dans teams :

    - **Pour les communications de conversation de teams :** Affectez des utilisateurs individuels ou affectez un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Il s’agit des relations utilisateur/conversation 1-à-1 ou 1-n.
    - **Pour les communications de canal teams :** Affectez tous les groupes Microsoft Team Channel ou Office 365 que vous souhaitez analyser qui contiennent un utilisateur spécifique à la stratégie de conformité de communication. Si vous ajoutez le même utilisateur à d’autres canaux Microsoft teams ou à des groupes Office 365, veillez à ajouter ces nouveaux canaux et groupes à la stratégie de conformité des communications.

- **Messagerie Exchange**: les boîtes aux lettres hébergées sur Exchange Online dans le cadre de votre abonnement Microsoft 365 ou Office 365 sont toutes éligibles pour l’analyse des messages. Les e-mails et les pièces jointes correspondant à des conditions de stratégie de conformité de communication sont immédiatement disponibles dans les rapports de conformité de communication. Les types de pièces jointes prises en charge pour la conformité de la communication sont les mêmes que ceux [pris en charge pour les inspections de contenu de règle de flux de messagerie Exchange](https://docs.microsoft.com/exchange/security-and-compliance/mail-flow-rules/inspect-message-attachments#supported-file-types-for-mail-flow-rule-content-inspection).

- **Skype entreprise Online**: les communications de conversation et les pièces jointes associées dans Skype entreprise Online peuvent être surveillées. Les conversations Skype entreprise Online correspondant à des conditions de stratégie de conformité de communication sont traitées une fois toutes les 24 heures, puis disponibles dans les rapports de conformité des communications. Les conversations de conversation surveillées proviennent de [conversations précédentes enregistrées dans Skype entreprise Online](https://support.office.com/article/Find-a-previous-Skype-for-Business-conversation-18892eba-5f18-4281-8c87-fd48bd72e6a2).  Utilisez la configuration de gestion de groupe suivante pour superviser les communications de conversation des utilisateurs dans Skype entreprise Online :

    - **Pour les communications de conversation de Skype entreprise Online**: affectez des utilisateurs individuels ou affectez un [groupe de distribution](https://support.office.com/article/Distribution-groups-E8BA58A8-FAB2-4AAF-8AA1-2A304052D2DE) à la stratégie de conformité des communications. Il s’agit des relations utilisateur/conversation 1-à-1 ou 1-n.

- **Sources**tierces : vous pouvez analyser les communications à partir de sources tierces pour les données importées dans des boîtes aux lettres dans votre organisation Microsoft 365. Les connecteurs prennent en charge les ressources tierces suivantes :

    - [Instant Bloomberg](archive-instant-bloomberg-data.md)
    - [Facebook](archive-facebook-data-with-sample-connector.md)
    - [LinkedIn](archive-linkedin-data.md)
    - SAP SuccessFactors
    - [Twitter](archive-twitter-data-with-sample-connector.md)
    - [Connecteur de données personnalisé](archiving-third-party-data.md)

Vous devez configurer un connecteur tiers pour votre organisation Microsoft 365 avant de pouvoir attribuer le connecteur à une stratégie de conformité de communication. La section **sources** tierces de l’Assistant stratégie de conformité des communications affiche uniquement les connecteurs tiers actuellement configurés.

## <a name="policy-settings"></a>Paramètres de stratégie

### <a name="direction"></a>Direction

Par défaut, la **direction est** la condition est affichée et ne peut pas être supprimée. Les paramètres de direction de communication d’une stratégie sont choisis individuellement ou ensemble :

- **Entrant**: vous pouvez choisir **entrant** pour examiner les communications envoyées **aux** personnes que vous avez choisies de superviser **des** personnes qui ne sont pas incluses dans la stratégie.
- **Sortant**: vous pouvez choisir **sortant** si vous souhaitez consulter les communications envoyées **par** les personnes que vous avez choisies de superviser **aux** personnes qui ne sont pas incluses dans la stratégie.
- **Internal**: vous pouvez choisir **Internal** pour examiner les communications envoyées **entre** les personnes que vous avez identifiées dans la stratégie.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous pouvez inclure des types d’informations sensibles dans le cadre de votre stratégie de conformité de communication. Les types d’informations sensibles sont des types de données prédéfinis ou personnalisés qui peuvent vous aider à identifier et à protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, et bien plus encore. Dans le cadre de la [protection contre la perte de données (DLP)](data-loss-prevention-policies.md)d’Office 365, la configuration des informations sensibles peut utiliser des modèles, la proximité des caractères, les niveaux de confiance et même les types de données personnalisés pour identifier et marquer le contenu susceptible d’être sensible. Les types d’informations sensibles par défaut sont les suivants :

- Financier
- Médecine et santé
- Confidentialité
- Type d’informations personnalisées

Pour en savoir plus sur les détails des informations sensibles et les modèles inclus dans les types par défaut, consultez la rubrique [types d’informations sensibles](what-the-sensitive-information-types-look-for.md).

### <a name="custom-keyword-dictionaries"></a>Dictionnaires de mots clés personnalisés

Configurez des dictionnaires de mots clés personnalisés (ou des lexiques) pour fournir une gestion simple des mots clés propres à votre organisation ou votre secteur d’activité. Les dictionnaires de mots clés prennent en charge jusqu’à 100 000 termes par dictionnaire. Si nécessaire, vous pouvez appliquer plusieurs dictionnaires de mots clés personnalisés à une seule stratégie ou disposer d’un dictionnaire à Mots clés unique par stratégie. Ces dictionnaires sont affectés dans une stratégie de conformité de communication et peuvent être issus d’un fichier (par exemple, une liste. csv ou. txt) ou d’une liste que vous pouvez [importer dans le centre de conformité](create-a-keyword-dictionary.md).

### <a name="classifiers"></a>Classifieurs requêtes

Les classifieurs intégrés analysent les messages envoyés ou reçus sur tous les canaux de communication de votre organisation en fonction de différents types de problèmes de conformité. Les classifieurs utilisent une combinaison d’intelligence artificielle et de mots clés pour identifier la langue dans les messages susceptibles de violer les stratégies anti-harcèlement. Les classifieurs prennent actuellement en charge uniquement les mots clés anglais dans les messages.

Conformité de la communication analysez les communications pour les termes et les sentiments pour les types de langages suivants :

- **Menace**: analyse les menaces pour valider la violence ou nuire physiquement à une personne ou à une propriété.
- **Harcèlement**: analyse les comportements offensants ciblant les personnes en matière de race, couleur, religion, origine nationale
- **Blasphèmes**: analyse les expressions à inconvenances qui dépassent la plupart des gens.

Notez que les classifieurs intégrés ne fournissent pas une liste exhaustive de termes dans ces domaines. De plus, les normes linguistiques et culturelles changent en permanence, et en raison de ces réalités, Microsoft se réserve le droit de mettre à jour les classifieurs à sa discrétion. Alors que les classifieurs peuvent aider votre organisation à surveiller ces domaines, les classifieurs ne sont pas destinés à fournir les moyens uniques de surveillance ou d’adressage de cette langue pour votre organisation. Votre organisation, et non Microsoft, reste responsable de toutes les décisions liées à l’analyse et au blocage de la langue dans ces domaines.

Pour plus d’informations sur les classifieurs dans Microsoft 365, reportez-vous à [Classifiers](classifier-getting-started-with.md).

### <a name="conditional-settings"></a>Paramètres conditionnels
<a name="ConditionalSettings"> </a>

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications à partir de la messagerie et des sources tierces de votre organisation (par exemple, Facebook ou DropBox).

Le tableau suivant décrit plus en plus de chaque condition.
  
|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le contenu correspond à l’un de ces classifieurs** | S’appliquer à la stratégie lorsqu’un classifieur est inclus ou exclu d’un message. Certains classifieurs sont prédéfinis dans votre client et les classifieurs personnalisés doivent être configurés séparément avant d’être disponibles pour cette condition. Un seul classifieur peut être défini en tant que condition dans une stratégie. Pour plus d’informations sur la configuration des classifieurs, consultez la rubrique [Classifiers](classifier-getting-started-with.md). |
| **Le contenu contient l’un de ces types d’informations sensibles** | S’appliquent à la stratégie lorsque des types d’informations sensibles sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre client et les classifieurs personnalisés peuvent être configurés séparément ou dans le cadre du processus d’attribution de la condition. Chaque type d’informations sensibles que vous choisissez est appliqué séparément et un seul de ces types d’informations sensibles doit s’appliquer pour la stratégie à appliquer au message. Pour plus d’informations sur les types d’informations sensibles personnalisés, consultez la rubrique [Custom sensitive types information](custom-sensitive-info-types.md). |
| **Un message est reçu à partir de l’un de ces domaines**  <br><br> **Le message n’est reçu à partir d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages reçus. Entrez chaque domaine ou adresse de messagerie et séparez les domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie entré est appliqué séparément, un seul domaine ou une seule adresse de messagerie doit s’appliquer pour la stratégie à appliquer au message. <br><br> Si vous souhaitez analyser tous les messages électroniques à partir d’un domaine spécifique tout en excluant les messages qui n’ont pas besoin d’être réexaminés (bulletins d’information, annonces, etc.), vous devez configurer la condition qu’un **message n’est pas reçu de l’un de ces domaines** , qui exclut l’adresse de messagerie (par exemple « Newsletter@contoso.com »). |
| **Un message est envoyé à l’un de ces domaines**  <br><br> **Le message n’est pas envoyé à l’un de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages envoyés. Entrez chaque domaine ou adresse de messagerie et séparez les domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie est appliqué séparément, un seul domaine ou une seule adresse de messagerie doit s’appliquer pour la stratégie à appliquer au message. <br><br> Si vous souhaitez analyser tous les messages électroniques envoyés à un domaine spécifique mais exclure les messages envoyés qui n’ont pas besoin d’être réexaminés, vous devez configurer deux conditions : <br> -Un **message est envoyé à l’un de ces domaines** qui définit le domaine (« contoso.com »), et <br> -Un **message n’est pas envoyé à l’un de ces domaines** , qui exclut l’adresse de messagerie (« Subscriptions@contoso.com »). |
| **Le message est classé avec l’une de ces étiquettes**  <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Pour appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour la stratégie à appliquer au message). Pour plus d’informations sur la configuration des étiquettes de rétention, consultez la rubrique [vue d’ensemble des étiquettes de rétention](labels.md).|
| **Le message contient l’un de ces mots**  <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot ou expression sur une ligne distincte. Chaque ligne de mots que vous entrez est appliquée séparément (une seule de ces lignes doit s’appliquer à la stratégie à appliquer au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **La pièce jointe contient l’un de ces mots**  <br><br> **La pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans une pièce jointe (par exemple, un document Word), entrez chaque mot ou expression sur une ligne distincte. Chaque ligne de mots que vous entrez est appliquée séparément (une seule ligne doit s’appliquer à la stratégie à appliquer à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-feature-reference.md#Matchwords).|
| **La pièce jointe est l’un de ces types de fichiers**  <br><br> **Aucune de ces types de fichiers n’est associée à la pièce jointe** | Pour superviser les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichiers (par exemple,. exe ou. pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichiers, entrez-les sur des lignes distinctes. Une seule extension de pièce jointe doit correspondre pour que la stratégie s’applique.|
| **La taille du message est supérieure à**  <br><br> **La taille du message n’est pas supérieure à** | Pour examiner les messages en fonction d’une certaine taille, utilisez les conditions suivantes pour spécifier la taille maximale ou minimale qu’un message peut contenir avant d’être soumis à révision. Par exemple, si vous spécifiez une **taille de message supérieure à** \> **1,0 Mo**, tous les messages de 1,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La taille de la pièce jointe est supérieure à**  <br><br> **La pièce jointe n’est pas supérieure à** | Pour examiner les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale qu’une pièce jointe peut contenir avant que le message et ses pièces jointes soient soumis à révision. Par exemple, si vous spécifiez une **taille de pièce jointe supérieure** \> à **2,0 Mo**, tous les messages avec des pièces jointes 2,01 Mo et supérieures sont soumis à la révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
   
#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes
<a name="Matchwords"> </a>

Chaque ligne de mots que vous entrez est appliquée séparément (une seule ligne doit s’appliquer à la condition de stratégie à appliquer à l’e-mail ou à la pièce jointe). Par exemple, nous utilisons la condition, le **message contient l’un de ces mots**, avec les mots-clés « Banker » et « negociing Insider » sur des lignes distinctes. La stratégie s’applique aux messages qui incluent le mot « Banker » ou l’expression « negociation Insiders ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots contenus dans le message ou dans la pièce jointe doivent correspondre exactement à ce que vous entrez.

Pour analyser les messages électroniques et les pièces jointes des mêmes mots clés, créez une [stratégie de protection contre la perte de données](create-test-tune-dlp-policy.md) avec un dictionnaire de [Mots clés personnalisé](create-a-keyword-dictionary.md) pour les termes que vous souhaitez analyser dans les messages. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **ou** dans la pièce jointe du courrier électronique. L’utilisation des paramètres de stratégie conditionnelle standard (le*message contient l’un de ces mots* et la *pièce jointe contient l’un de ces mots*) pour identifier les termes dans les messages et dans les pièces jointes exige que les termes soient **présents dans le** message et la pièce jointe.
  
#### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer à quel moment appliquer la stratégie de surveillance aux éléments de communication. Lorsque vous configurez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « commercial » et qu’il est supérieur à 2 Mo. Toutefois, si le message contient également les mots « approuvé par Contoso Financial », la stratégie ne doit pas s’appliquer. Dans cet exemple, les trois conditions suivantes sont définies comme suit :
  
- Le **message contient l’un de ces mots**, avec les mots clés « Trade »
- La **taille du message est supérieure à**, avec la valeur 2 Mo
- Le **message ne contient aucun de ces mots**, avec les mots-clés « approuvé par l’équipe financière de contoso »

### <a name="review-percentage"></a>Vérifier le pourcentage

Si vous souhaitez réduire la quantité de contenu à réviser, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de surveillance. Un échantillon aléatoire de contenu en temps réel est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les relecteurs examinent tous les éléments, vous pouvez configurer **100%** dans une stratégie de conformité de communication.

## <a name="notices"></a>Constaté

Vous pouvez créer des modèles d’avis si vous souhaitez envoyer aux utilisateurs un avis de rappel par courrier électronique pour les correspondances de stratégie dans le cadre du processus de résolution des problèmes. Les notifications peuvent uniquement être envoyées à l’adresse de messagerie de l’employé associée à la correspondance de stratégie qui a généré l’alerte spécifique pour correction. Lors de la sélection d’un modèle d’avis à appliquer à une violation de stratégie dans le cadre du flux de travail de correction, vous pouvez choisir d’accepter les valeurs de champ définies dans le modèle ou de remplacer les champs selon vos besoins.

Les modèles de notifications sont des modèles de courrier électronique personnalisés dans lesquels vous pouvez définir les champs de message suivants :

|**Field**|**Obligatoire**| **Détails** |
|:-----|:-----|:-----|
|**Nom du modèle** | Oui | Nom convivial du modèle d’avis que vous sélectionnerez dans le flux de travail de notification lors de la correction, prend en charge les caractères de texte. |
| **Adresse de l’expéditeur** | Oui | Adresse d’un ou de plusieurs utilisateurs ou groupes qui envoie le message à l’employé avec une correspondance de stratégie, sélectionnée dans Active Directory pour votre abonnement. |
| **Adresses CC et CCI** | Non | Les utilisateurs ou groupes facultatifs devant être avertis de la correspondance de stratégie, sélectionnés dans Active Directory pour votre abonnement. |
| **Objet** | Oui | Informations qui s’affichent dans la ligne d’objet du message, prend en charge les caractères de texte. |
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

> [!NOTE]
> L’implémentation de l’attribut HTML href dans les modèles de notification de conformité des communications prend actuellement en charge uniquement les guillemets simples au lieu de guillemets doubles pour les références d’URL.

## <a name="filters"></a>Filtres

Les filtres de conformité de la communication vous permettent de filtrer et de trier les messages d’alerte pour des actions plus rapides d’enquête et de correction. Le filtrage est disponible sur les onglets **en attente** et **résolus** pour chaque stratégie. Pour enregistrer un filtre ou un jeu de filtres en tant que requête de filtre enregistrée, une ou plusieurs valeurs doivent être configurées en tant que sélections de filtre. Le tableau suivant présente les détails des filtres :

|**Filtre**|**Détails**|
|:-----|:-----|
| **Date** | Date à laquelle le message a été envoyé ou reçu par un utilisateur au sein de votre organisation. |
| **Classe file** | Classe du message en fonction du type de message, qu’il *s’agisse d’un message ou* d’une *pièce jointe*. |
| **Avec pièce jointe** | Présence d’une pièce jointe dans le message. |
| **Classe d’élément** | Source du message en fonction du type de message, de la messagerie électronique, de la conversation Microsoft Team, de Bloonmberg, etc. |
| **Domaines de destinataires** | Domaine auquel le message a été envoyé. Il s’agit normalement de votre domaine d’abonnement Microsoft 365 par défaut. |
| **Destinataire** | Utilisateur auquel le message a été envoyé. |
| **Sender** | La personne qui a envoyé le message. |
| **Domaine de l’expéditeur** | Le domaine qui a envoyé le message. |
| **Size** | Taille du message en Ko. |
| **Subject/title** | Objet du message ou titre de conversation. |
| **Tags** | Les balises affectées à un message, qu’elles soient *douteuses*, *conformes*ou *non conformes*. |
| **Transmis à** | Nom d’utilisateur de la personne incluse dans le cadre d’une action de réaffectation de message. |

## <a name="alert-policies"></a>Stratégies d’alerte

Après avoir configuré une stratégie, une stratégie d’alerte correspondante est automatiquement créée et des alertes sont générées pour les messages qui répondent aux conditions définies dans la stratégie. Par défaut, toutes les stratégies correspondent aux déclencheurs d’alerte dont le niveau de gravité est moyen dans la stratégie d’alerte associée. Des alertes sont générées pour une stratégie de conformité des communications une fois que le niveau de seuil de déclenchement d’agrégation est atteint dans la stratégie d’alerte Office 365 associée.

Pour les stratégies de conformité de communication, les valeurs de stratégie d’alerte suivantes sont configurées par défaut :

|**Déclencheur de stratégie d’alerte**|**Valeur par défaut**|
|:-----|:-----|
| Aggregat | Agrégation simple |
| Seuil | 4 activités |
| Fenêtre | 60 minutes |

> [!Note]
> Les paramètres de déclenchement de seuil de stratégie d’alerte pour les activités prennent en charge une valeur minimale de 3 ou supérieure pour les stratégies de conformité de communication.

Vous pouvez modifier les paramètres par défaut des déclencheurs sur le nombre d’activités, la période pour les activités et les utilisateurs spécifiques des stratégies d’alerte sur la page **stratégies d’alerte** dans le centre de conformité & Office 365 Security.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Modifier le niveau de gravité pour une stratégie d’alerte

Si vous souhaitez modifier le niveau de gravité affecté dans une stratégie d’alerte pour une stratégie de conformité de communication spécifique, procédez comme suit :

1. Connectez- [https://compliance.microsoft.com](https://compliance.microsoft.com) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **stratégies**.

3. Sélectionnez **alerte Office 365** sur la page **stratégies** pour ouvrir la page **stratégies d’alerte** dans le centre de **sécurité & de sécurité Office 365**.

4. Cochez la case correspondant à la stratégie de conformité de communication que vous souhaitez mettre à jour, puis sélectionnez **modifier la stratégie**.

5. Sous l’onglet **Description** , sélectionnez la liste déroulante **gravité** pour configurer le niveau d’alerte de stratégie.

6. Sélectionnez **Enregistrer** pour appliquer le nouveau niveau de gravité à la stratégie.

7. Sélectionnez **Fermer** pour quitter la page Détails de la stratégie d’alerte.

## <a name="audit"></a>Contrôlé

Dans certains cas, vous devez fournir des informations aux auditeurs de réglementation ou de conformité pour prouver le contrôle des activités et des communications des employés. Il peut s’agir d’un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque fois qu’une stratégie de conformité de communication est modifiée. Les stratégies de conformité des communications disposent de pistes d’audit intégrées pour une préparation complète des audits internes ou externes. Les historiques d’audit détaillés de chaque action de création, de modification et de suppression sont capturés par vos stratégies de communication afin de fournir des preuves de procédures de surveillance.

Pour afficher les activités de stratégie de conformité de communication, sélectionnez le contrôle **Exporter les activités de révision** dans la page principale pour n’importe quelle stratégie. Cela génère un fichier d’audit au format. csv qui contient les informations suivantes :

|**Field**|**Détails**|
|:-----|:-----|
| **CreationDate** | Lors de l’exécution de l’activité dans une stratégie. |
| **UserIds** | Utilisateur qui a exécuté l’activité dans une stratégie. |
| **Operations** | Les opérations effectuées sur la stratégie. |
| **AuditData** | Il s’agit du champ de source de données principal pour toutes les activités de stratégie. Toutes les activités sont enregistrées et séparées par des virgules. |

Vous pouvez également afficher les activités d’audit dans le journal d’audit unifié ou avec l’applet de commande PowerShell [Search-UnifiedAuditLog](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-audit/search-unifiedauditlog) .

Par exemple, l’exemple suivant montre comment renvoyer les activités de toutes les activités de vérification de surveillance (stratégies et règles) et répertorier les informations détaillées pour chacune d’elles :

```PowerShell
Search-UnifiedAuditLog -StartDate 3/1/2019 -EndDate ([System.DateTime]::Now) -RecordType DataGovernance -ResultSize 5000 | Where-Object {$_.Operations -like "*SupervisoryReview*"}  | fl CreationDate,Operations,UserIds,AuditData
```

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

Pour configurer la conformité de la communication pour votre organisation Microsoft 365, consultez la rubrique [configure communication Compliance for your microsoft 365 Organization (Preview)](communication-compliance-configure.md).
