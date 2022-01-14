---
title: Stratégies de conformité des communications
description: En savoir plus sur les stratégies de conformité des communications.
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
ms.localizationpriority: medium
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 5078943e9b2bf158a457d263b2db65e9bfca7659
ms.sourcegitcommit: a6651b841f111ea2776cab88bf2c80f805fa8e09
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/13/2022
ms.locfileid: "62034991"
---
# <a name="communication-compliance-policies"></a>Stratégies de conformité des communications

## <a name="policies"></a>Stratégies

> [!IMPORTANT]
> L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution Microsoft 365 conformité des communications.](https://compliance.microsoft.com/supervisoryreview)

Vous créez des stratégies de conformité des communications pour les organisations Microsoft 365 dans le Centre de conformité Microsoft 365. Les stratégies de conformité des communications définissent les communications et les utilisateurs qui sont soumis à révision dans votre organisation, définissent les conditions personnalisées que les communications doivent respecter et spécifient qui doit passer en revue. Les utilisateurs affectés au rôle d’administrateur de conformité des communications peuvent configurer des stratégies, et toute personne à qui ce rôle est attribué peut accéder à la **page** conformité des communications et aux paramètres globaux du Centre de conformité Microsoft 365.  Si nécessaire, vous pouvez exporter l’historique des modifications apportées à une stratégie vers un fichier .csv (valeurs séparées par des virgules) qui inclut également l’état des alertes en attente de révision, des éléments réexportés et des éléments résolus. Les stratégies ne peuvent pas être renommées et supprimées lorsqu’elles ne sont plus nécessaires.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de stratégie sont des paramètres de stratégie prédéfincés que vous pouvez utiliser pour créer rapidement des stratégies pour répondre aux scénarios de conformité courants. Chacun de ces modèles présente des différences dans les conditions et l’étendue, et tous les modèles utilisent les mêmes types de signaux d’analyse. Vous pouvez choisir parmi les modèles de stratégie suivants :

|**Catégorie**|**Modèle de stratégie**|**Détails**|
|:-----|:-----|:-----|
| **Texte inapproprié** | Détecter le texte inapproprié | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage d’avis : 100 % <br> - Conditions : classifieurs de menace, de discrimination (prévisualisation) et de harcèlement ciblé |
| **Images inappropriées** | Détecter les images inappropriées | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage d’avis : 100 % <br> - Conditions : classifieurs d’image pour adultes et racy |
| **Informations sensibles** | Surveiller les informations sensibles | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage d’avis : 10 % <br> - Conditions : informations sensibles, modèles de contenu pré-personnalisés et types, option de dictionnaire personnalisé, pièces jointes dont la taille est supérieure à 1 Mo |
| **Conformité réglementaire** | Surveiller la conformité réglementaire | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant <br> - Pourcentage d’avis : 10 % <br> - Conditions : option de dictionnaire personnalisé, pièces jointes dont la taille est supérieure à 1 Mo |
| **Conflit d’intérêt** | Surveiller les conflits d’intérêts | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : interne <br> - Pourcentage d’avis : 100 % <br> - Conditions : Aucune |

Les communications sont analysées toutes les 24 heures à partir de la création des stratégies. Par exemple, si vous créez une stratégie de contenu inappropriée à 11 h 00, la stratégie recueille tous les 24 heures des signaux de conformité des communications à 11 h 00 tous les jours. La modification d’une stratégie ne change pas cette fois. Pour afficher la date et l’heure de  la dernière analyse d’une stratégie, accédez à la colonne Dernière analyse de stratégie dans la page **Stratégie.** Après la création d’une stratégie, l’affichage de la date et de l’heure de la première analyse de stratégie peut prendre jusqu’à 24 heures. La date et l’heure de la dernière analyse sont converties en fuseau horaire de votre système local.

## <a name="pause-a-policy-preview"></a>Suspendre une stratégie (aperçu)

Une fois que vous avez créé une stratégie de conformité des communications, la stratégie peut être temporairement suspendue si nécessaire. La suspension d’une stratégie peut être utilisée pour tester ou dépanner les correspondances de stratégie, ou pour optimiser les conditions de stratégie. Au lieu de supprimer une stratégie dans ces circonstances, la suspension d’une stratégie conserve également les alertes et messages de stratégie existants pour les examens et examens en cours. La suspension d’une stratégie empêche l’inspection et la génération d’alertes pour toutes les conditions de message utilisateur définies dans la stratégie au moment où la stratégie est suspendue. Pour suspendre ou redémarrer une stratégie, les utilisateurs doivent être membres du groupe de rôles Administrateur de conformité *des* communications.

Pour suspendre une stratégie, accédez à la page **Stratégie,** sélectionnez une stratégie, puis sélectionnez **Stratégie** de pause dans la barre d’outils Actions. Dans le **volet Stratégie** de pause, confirmez que vous souhaitez suspendre la stratégie en sélectionnant **Pause**. Dans certains cas, l’interruption d’une stratégie peut prendre jusqu’à 24 heures. Une fois la stratégie suspendue, les alertes pour les messages correspondant à la stratégie ne sont pas créées. Toutefois, les messages associés aux alertes qui ont été créés avant la suspension de la stratégie restent disponibles pour examen, révision et correction.

L’état de la stratégie pour les stratégies suspendues peut indiquer plusieurs états :

- **Active**: la stratégie est active
- **Suspendu :** la stratégie est entièrement suspendue.
- **Mise en pause**: la stratégie est en cours d’interruption.
- **Reprise :** stratégie en cours de reprise.
- **Erreur lors de la reprise :** une erreur s’est produite lors de la reprise de la stratégie. Pour la trace de la pile  d’erreurs, pointez votre souris sur l’erreur lors de la reprise de l’état dans la colonne État de la page Stratégie.
- **Erreur lors de la mise en pause**: une erreur s’est produite lors de la suspension de la stratégie. Pour la trace de la pile  d’erreurs, pointez votre souris sur l’état Erreur en pause dans la colonne État de la page Stratégie.

Pour reprendre une stratégie, accédez à la page  **Stratégie,** sélectionnez une stratégie, puis sélectionnez Reprendre la stratégie dans la barre d’outils Actions. Dans le **volet De la** stratégie de reprise, confirmez que vous souhaitez reprendre la stratégie en sélectionnant **Resume**. Dans certains cas, la reprise d’une stratégie peut prendre jusqu’à 24 heures. Une fois la stratégie reprise, des alertes pour les messages correspondant à la stratégie sont créées et disponibles pour examen, révision et correction.

## <a name="copy-a-policy-preview"></a>Copier une stratégie (aperçu)

Pour les organisations ayant des stratégies de conformité des communications existantes, la création d’une stratégie à partir d’une stratégie existante peut être utile dans certains scénarios. La copie d’une stratégie crée un doublon exact d’une stratégie existante, y compris tous les utilisateurs dans l’étendue, tous les réviseurs affectés et toutes les conditions de stratégie. Certains scénarios peuvent inclure les suivants :

- **Limite de stockage de stratégie atteinte**: les stratégies de conformité des communications actives ont des limites de stockage des messages. Lorsque la limite de stockage d’une stratégie est atteinte, la stratégie est automatiquement désactivée. Les organisations qui doivent continuer à détecter, capturer et agir sur des messages inappropriés couverts par la stratégie désactivée peuvent rapidement créer une stratégie avec une configuration identique.
- **Détectez** et examinez les messages inappropriés pour différents groupes d’utilisateurs : certaines organisations peuvent préférer créer plusieurs stratégies avec la même configuration, mais inclure différents utilisateurs dans l’étendue et différents réviseurs pour chaque stratégie.
- **Stratégies similaires avec de petites modifications**: pour les stratégies avec des configurations ou des conditions complexes, la création d’une stratégie à partir d’une stratégie similaire peut gagner du temps.

Pour copier une stratégie, les utilisateurs doivent être membres des groupes de rôles Conformité des *communications* ou Administrateur de la conformité *des* communications. Une fois qu’une nouvelle stratégie est créée à partir d’une stratégie existante, l’affichage des messages qui correspondent à la nouvelle configuration de stratégie peut prendre jusqu’à 24 heures.

Pour copier une stratégie et en créer une, complétez les étapes suivantes :

1. Sélectionnez la stratégie à copier.
2. Sélectionnez **le bouton Copier** la barre de commandes de stratégie dans la barre de commandes ou sélectionnez Copier **la** stratégie dans le menu d’action de la stratégie.
3. Dans le **volet Copier la** stratégie, vous pouvez accepter  le nom par défaut de la stratégie dans le champ Nom de la stratégie ou renommer la stratégie. Le nom de la nouvelle stratégie ne peut pas être identique à une stratégie active ou désactivée existante. Remplissez le **champ Description** selon les besoins.
4. Si vous n’avez pas besoin d’une personnalisation supplémentaire de la stratégie, **sélectionnez Copier la** stratégie pour terminer le processus. Si vous devez mettre à jour la configuration de la nouvelle stratégie, sélectionnez **Personnaliser la stratégie.** L’Assistant Stratégie démarre pour vous aider à mettre à jour et personnaliser la nouvelle stratégie.

## <a name="storage-limit-notification-preview"></a>Stockage limite de notification (prévisualisation)

Chaque stratégie de conformité des communications a une taille limite de stockage de 100 Go ou 1 million de messages, selon la première limite atteinte. À mesure que la stratégie approche de ces limites, les  e-mails de notification sont automatiquement envoyés aux utilisateurs affectés aux groupes de rôles Conformité des communications ou *Administrateur* de la conformité des communications. Les messages de notification sont envoyés lorsque la taille de stockage ou le nombre de messages atteint 80, 90 et 95 % de la limite. Lorsque la limite de stratégie est atteinte, la stratégie est automatiquement désactivée et la stratégie cesse de traiter les messages pour les alertes.

>[!IMPORTANT]
>Si une stratégie est désactivée en raison de l’atteinte des limites de stockage et de message, n’oubliez pas d’évaluer comment gérer la stratégie désactivée. Si vous supprimez la stratégie, tous les messages, pièces jointes associées et alertes de message sont supprimés définitivement. Si vous devez conserver ces éléments pour une utilisation future, ne supprimez pas la stratégie désactivée.

Pour gérer les stratégies à l’approche des limites de stockage et de message, envisagez d’effectuer une copie de la stratégie pour maintenir la continuité de la couverture ou d’effectuer les actions suivantes pour réduire la taille actuelle du stockage et le nombre de messages de la stratégie :

- Envisagez de réduire le nombre d’utilisateurs affectés à la stratégie. La suppression d’utilisateurs de la stratégie ou la création de stratégies différentes pour différents groupes d’utilisateurs peuvent aider à ralentir la croissance de la taille de la stratégie et du nombre total de messages.
- Examinez la stratégie pour les alertes de faux positifs excessifs. Envisagez d’ajouter des exceptions ou des modifications aux conditions de stratégie pour ignorer les alertes fausses positives courantes.
- Si une stratégie a atteint les limites de stockage ou de message et a été désactivée, copiez-la pour continuer à détecter et à prendre des mesures pour les mêmes conditions et utilisateurs.

## <a name="policy-settings"></a>Paramètres de stratégie

### <a name="users"></a>Utilisateurs

Vous pouvez choisir de sélectionner Tous **les** utilisateurs ou de définir des utilisateurs spécifiques dans une stratégie de conformité des communications. La sélection de **Tous les utilisateurs** applique la stratégie à tous les utilisateurs et les groupes auxquels n’importe quel utilisateur est inclus en tant que membre. La définition d’utilisateurs spécifiques applique la stratégie aux utilisateurs définis et aux groupes auxquels les utilisateurs définis sont inclus.

### <a name="direction"></a>Direction

Par défaut, la **condition Direction** est affichée et ne peut pas être supprimée. Les paramètres d’orientation de communication dans une stratégie sont choisis individuellement ou ensemble :

- **Entrant :** détecte les  communications envoyées aux utilisateurs supervisés à partir d’expéditeurs externes et internes, y compris d’autres utilisateurs supervisés dans la stratégie.
- **Sortant :** détecte les communications envoyées par des utilisateurs **supervisés** à des destinataires externes et internes, y compris d’autres utilisateurs supervisés dans la stratégie.
- **Interne**: détecte les communications **entre** les utilisateurs ou les groupes supervisés dans la stratégie.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous avez la possibilité d’inclure des types d’informations sensibles dans le cadre de votre stratégie de conformité des communications. Les types d’informations sensibles sont des types de données prédéfin définis ou personnalisés qui permettent d’identifier et de protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Dans le cadre de la protection contre la perte de [données,](dlp-learn-about-dlp.md)la configuration des informations sensibles peut utiliser des modèles, la proximité des caractères, des niveaux de confiance et même des types de données personnalisés pour vous aider à identifier et à indiquer le contenu qui peut être sensible. Les types d’informations sensibles par défaut sont :

- Financier
- Santé et médical
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

- **Images pour adultes**: recherche les images qui sont explicites de manière sexuelle.
- **Discrimination (prévisualisation)**: recherche les propos explicites de discrimination et est particulièrement sensible au langage de discrimination à l’égard des communautés américaines/noires d’Afrique par rapport aux autres communautés.
- **Images de requête**: recherche les images qui décrivent la violence et les violences.
- **Blasphémité**: recherche les expressions expressions expressions qui insérons la plupart des personnes.
- **Images racées**: recherche les images qui sont sexuellement sexuellement en nature, mais qui contiennent un contenu moins explicite que les images considérées comme adulte.
- **Harcèlement ciblé :** recherche les conduites choquantes ciblant des personnes en ce qui concerne la course, la couleur, l’origine nationale.
- **Menace :** recherche les menaces de violence ou de dommages physiques à une personne ou à une propriété.

Les *classifieurs* d’image pour adultes, *racy* et *gory* analysent les fichiers au format .jpeg, .png, .gif et .bmp formats. La taille des fichiers image doit être inférieure à 4 mégaoctets (Mo) et les dimensions des images doivent être supérieures à 50 x 50 pixels et supérieures à 50 kilo-octets (Ko) pour que l’image soit éligible pour évaluation. L’identification d’image est prise en charge Exchange Online messages électroniques et Microsoft Teams canaux et conversations.

Les classifieurs intégrés entraçables et globaux ne fournissent pas une liste exhaustive de termes ou d’images dans ces domaines. En outre, les normes linguistiques et culturelles changent continuellement et, à la lumière de ces exigences, Microsoft se réserve le droit de mettre à jour les classifieurs à sa discrétion. Bien que les classifieurs peuvent aider votre organisation à surveiller ces domaines, les classifieurs ne sont pas destinés à fournir l’unique moyen de surveillance ou d’adressant ces langages ou images. Votre organisation, et non Microsoft, reste responsable de toutes les décisions relatives à la surveillance, l’analyse et le blocage de la langue et des images dans ces domaines, y compris la conformité avec la confidentialité locale et les autres lois applicables. Microsoft encourage les conseils juridiques avant le déploiement et l’utilisation.

> [!NOTE]
> Les stratégies utilisant des classifieurs examinent et évaluent les messages avec un nombre de mots supérieur ou six. Les messages contenant moins de six mots ne sont pas évalués dans les stratégies à l’aide de classifieurs. Pour identifier et prendre des mesures sur les messages plus courts contenant du contenu inapproprié, nous vous recommandons d’inclure un dictionnaire de mots clés personnalisé pour surveiller les stratégies de conformité des communications pour ce type de contenu.

Pour plus d’informations sur les classifieurs entraidables dans Microsoft 365, voir Getting [started with trainable classifiers](classifier-get-started-with.md).

### <a name="optical-character-recognition-ocr"></a>Reconnaissance optique des caractères

Configurez des stratégies de conformité des communications intégrées ou personnalisées pour analyser et identifier le texte imprimé ou manuscrit à partir d’images qui peuvent être inappropriées dans votre organisation. La prise en charge intégrée des [services cognitives Azure](/azure/cognitive-services/computer-vision/overview-ocr) et de l’analyse optique pour l’identification du texte dans les images permet aux analystes et aux enquêteurs de détecter et d’agir sur des cas où une conduite inappropriée peut être manquée dans des communications principalement non textuelles.

Vous pouvez activer la reconnaissance optique de caractères (OCR) dans de nouvelles stratégies à partir de modèles, de stratégies personnalisées ou mettre à jour des stratégies existantes pour développer la prise en charge du traitement des images incorporées et des pièces jointes. Lorsqu’elle est activée dans une stratégie créée à partir d’un modèle de stratégie, l’analyse automatique est prise en charge pour les images incorporées ou jointes dans les messages électroniques et Microsoft Teams messages de conversation. Pour les images incorporées dans des fichiers de documents, l’analyse ocr n’est pas prise en charge. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés à des mots clés, classifieurs intégrés ou types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de l’analyse ocr.

Les images de 50 Ko à 4 Mo dans les formats d’image suivants sont analysées et traitées :

- .jpg/.jpeg (groupe d’experts conjoint)
- .png (graphiques réseau portables)
- .bmp (bitmap)
- .tiff (format de fichier d’image de balise)
- .pdf (format de document portable)

> [!NOTE]
> L’analyse et l’extraction des images .pdf incorporées et jointes sont actuellement prises en charge uniquement pour les messages électroniques.

Lors de l’examen des alertes en attente pour les stratégies avec ocr activé, les images identifiées et associées aux conditions de stratégie sont affichées en tant qu’éléments enfants pour les alertes associées. Vous pouvez afficher l’image d’origine pour évaluer le texte identifié en contexte avec le message d’origine. La présence d’images détectées avec des alertes peut prendre jusqu’à 48 heures.

### <a name="conditional-settings"></a>Paramètres conditionnels
<a name="ConditionalSettings"> </a>

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications provenant de la messagerie électronique et de sources tierces de votre organisation (par exemple, d’Instant Bloomberg).

Le tableau suivant en explique plus sur chaque condition.

|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le contenu correspond à l’un de ces classifieurs** | S’applique à la stratégie lorsque des classifieurs sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre client et les classifieurs personnalisés doivent être configurés séparément avant d’être disponibles pour cette condition. Un seul classificateur peut être défini comme condition dans une stratégie. Pour plus d’informations sur la configuration des classifieurs, voir En savoir plus sur les [classifieurs entraisables (prévisualisation).](classifier-learn-about.md) |
| **Le contenu contient l’un de ces types d’informations sensibles** | S’applique à la stratégie lorsque des types d’informations sensibles sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre client, et les classifieurs personnalisés peuvent être configurés séparément ou dans le cadre du processus d’attribution de condition. Chaque type d’informations sensibles que vous choisissez est appliqué séparément et un seul de ces types d’informations sensibles doit s’appliquer pour que la stratégie s’applique au message. Pour plus d’informations sur les types d’informations sensibles personnalisés, voir [En savoir plus sur les types d’informations sensibles.](sensitive-information-type-learn-about.md) |
| **Le message est reçu de l’un de ces domaines**  <br><br> **Le message n’est reçu d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages reçus. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse e-mail entré est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez analyser tous les messages électroniques d’un domaine spécifique, mais que vous souhaitez exclure les messages qui n’ont pas besoin d’être réexpédés (bulletins d’informations, annonces, et ainsi de suite), vous devez configurer un **message** qui n’est reçu d’aucune condition de ces domaines qui exclut l’adresse e-mail (exemple « newsletter@contoso.com »). |
| **Le message est envoyé à l’un de ces domaines**  <br><br> **Le message n’est envoyé à aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses de messagerie spécifiques dans les messages envoyés. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses de messagerie par une virgule. Chaque domaine ou adresse de messagerie est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez analyser tous les messages envoyés à un domaine spécifique, mais que vous souhaitez exclure les messages envoyés qui n’ont pas besoin d’être revue, vous devez configurer deux conditions : <br> - Un **message est envoyé à l’une de ces** conditions de domaine qui définit le domaine (« contoso.com ») ET <br> - Un **message n’est envoyé à aucune** condition de ces domaines qui exclut l’adresse de messagerie « subscriptions@contoso.com »). |
| **Le message est classé avec l’une de ces étiquettes**  <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées sont choisies dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur les étiquettes de rétention, voir [En savoir plus sur les stratégies de rétention et les étiquettes de rétention.](retention.md)|
| **Le message contient l’un de ces mots**  <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-policies.md#Matchwords).|
| **La pièce jointe contient l’un de ces mots**  <br><br> **La pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus d’une pièce jointe de message (par exemple, un document Word), entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-policies.md#Matchwords).|
| **La pièce jointe est l’un de ces types de fichiers**  <br><br> **La pièce jointe n’est pas de ces types de fichiers** | Pour contrôler les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichier (par exemple, .exe ou .pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichier, entrez-les sur des lignes distinctes. Une seule extension de pièce jointe doit correspondre pour que la stratégie s’applique.|
| **La taille du message est supérieure à**  <br><br> **La taille du message n’est pas supérieure à** | Pour passer en revue les messages en fonction d’une certaine taille, utilisez ces conditions pour spécifier la taille maximale ou minimale d’un message avant d’être soumis à révision. Par exemple, si vous spécifiez que la taille du **message** est supérieure à \> **1,0 Mo,** tous les messages de 1,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La pièce jointe est supérieure à**  <br><br> **La pièce jointe n’est pas supérieure à** | Pour passer en revue les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale d’une pièce jointe avant que le message et ses pièces jointes soient sujettes à révision. Par exemple, si  vous spécifiez que la pièce jointe est supérieure à \> **2,0 Mo,** tous les messages avec des pièces jointes de 2,01 Mo et plus sont soumis à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes
<a name="Matchwords"> </a>

Chaque mot que vous entrez et séparez par une virgule est appliqué séparément (un seul mot doit s’appliquer à la condition de stratégie à appliquer au message électronique ou à la pièce jointe). Par exemple, nous allons utiliser la condition « **Message**» contient l’un de ces mots, avec les mots clés « banker », « confidential » et « insider trading » séparés par une virgule (bancaire, confidentiel, « délit d’initié »). La stratégie s’applique à tous les messages qui incluent le mot « banker », « confidential » ou l’expression « insider trading ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots du message ou de la pièce jointe doivent correspondre exactement à ce que vous entrez.

> [!IMPORTANT]
>
> Lors de l’importation d’un fichier de dictionnaire personnel, chaque mot ou expression doit être séparé par un retour chariot et sur une ligne distincte. Par exemple :
>
> *banker* <br>
> *confidentiel* <br>
> *délit d’initié*

Pour analyser les messages électroniques et les pièces [](create-a-keyword-dictionary.md) jointes pour les mêmes mots clés, créez un dictionnaire de mots clés personnalisé pour les termes que vous souhaitez analyser dans les messages. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **ou** dans la pièce jointe de l’e-mail. L’utilisation des paramètres de stratégie conditionnelle standard ( Le *message* contient l’un de ces mots et la  pièce jointe contient l’un de ces *mots)* pour identifier les termes dans les messages et dans les pièces jointes, les termes doivent être présents dans le message et la pièce jointe.

#### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer quand appliquer la stratégie de conformité des communications aux éléments de communication. Lorsque vous définissez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « commerce » et est supérieur à 2 Mo. Toutefois, si le message contient également les mots « Approuvé par Contoso financial », la stratégie ne doit pas s’appliquer. Dans cet exemple, les trois conditions seraient définies comme suit :

- **Le message contient l’un de ces mots,** avec le mot clé « trade »
- **La taille du message est supérieure** à , avec la valeur 2 Mo
- **Le message ne contient aucun de ces mots,** avec les mots clés « Approuvé par l’équipe financière de Contoso »

### <a name="review-percentage"></a>Pourcentage de révision

Si vous souhaitez réduire la quantité de contenu à réviser, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de conformité des communications. Un échantillon aléatoire de contenu est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les réviseurs examinent tous les éléments, vous pouvez configurer **100 %** dans une stratégie de conformité des communications.

## <a name="alert-policies"></a>Stratégies d’alerte

Après avoir configuré une stratégie, une stratégie d’alerte correspondante est automatiquement créée et des alertes sont générées pour les messages qui correspondent aux conditions définies dans la stratégie. La réception des alertes des indicateurs d’activité peut prendre jusqu’à 24 heures après le démarrage de la création d’une stratégie. Par défaut, tous les déclencheurs d’alerte de correspondance de stratégie se voit attribuer un niveau de gravité moyen dans la stratégie d’alerte associée. Les alertes sont générées pour une stratégie de conformité des communications une fois que le niveau de seuil du déclencheur d’agrégation est atteint dans la stratégie d’alerte associée. Une seule notification par courrier électronique est envoyée toutes les 24 heures pour toutes les alertes, quel que soit le nombre de messages individuels qui correspondent aux conditions de stratégie. Par exemple, contoso a activé une stratégie de contenu inappropriée et, pour le 1er janvier, 100 correspondances de stratégie ont généré 6 alertes. Une notification par courrier électronique unique pour les 6 alertes est envoyée à la fin du 1er janvier.

Pour les stratégies de conformité des communications, les valeurs de stratégie d’alerte suivantes sont configurées par défaut :

|**Déclencheur de stratégie d’alerte**|**Valeur par défaut**|
|:-----|:-----|
| Agrégation | Agrégation simple |
| Seuil | Par défaut : 4 activités <br> Minimum : 3 activités <br> Maximum : 2 147 483 647 activités |
| Fenêtre | Par défaut : 60 minutes <br> Minimum : 60 minutes <br> Maximum : 10 000 minutes |

> [!NOTE]
> Les paramètres de déclencheur de seuil de stratégie d’alerte pour les activités prend en charge une valeur minimale de 3 ou supérieure pour les stratégies de conformité des communications.

Vous pouvez modifier les paramètres par défaut des déclencheurs sur le nombre d’activités, la période des activités et pour des utilisateurs spécifiques dans les stratégies d’alerte sur la **page** Stratégies d’alerte dans la Centre de conformité Microsoft 365.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Modifier le niveau de gravité d’une stratégie d’alerte

Si vous souhaitez modifier le niveau de gravité affecté dans une stratégie d’alerte pour une stratégie de conformité des communications spécifique, complétez les étapes suivantes :

1. Connectez-vous [Centre de conformité Microsoft 365](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, allez à **Stratégies.**

3. Sélectionnez **Office 365 sur la** page **Stratégies** pour ouvrir la page **Stratégies d’alertes.**

4. Cochez la case de la stratégie de conformité des communications que vous souhaitez mettre à jour, puis **sélectionnez Modifier la stratégie.**

5. Sous **l’onglet Description,** sélectionnez la zone de dépôt **Gravité** pour configurer le niveau d’alerte de stratégie.

6. Sélectionnez **Enregistrer** pour appliquer le nouveau niveau de gravité à la stratégie.

7. Sélectionnez **Fermer** pour quitter la page des détails de la stratégie d’alerte.
