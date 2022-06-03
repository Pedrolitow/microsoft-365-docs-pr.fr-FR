---
title: Stratégies de conformité des communications
description: En savoir plus sur les stratégies de conformité des communications.
keywords: Microsoft 365, Microsoft Purview, conformité, conformité des communications
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
ms.openlocfilehash: 44b177d0215acaa2e637aacda22db3eb16ee7168
ms.sourcegitcommit: 5fe7f2954a89406245416fc1a218cf4bf19abb85
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/03/2022
ms.locfileid: "65864515"
---
# <a name="communication-compliance-policies"></a>Stratégies de conformité des communications

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

## <a name="policies"></a>Politiques

> [!IMPORTANT]
> L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité des communications](https://compliance.microsoft.com/supervisoryreview).

Vous créez des stratégies de conformité des communications pour Microsoft 365 organisations dans le portail de conformité Microsoft Purview. Les stratégies de conformité des communications définissent les communications et les utilisateurs susceptibles d’être examinés dans votre organisation, définissent les conditions personnalisées que les communications doivent respecter et spécifient qui doit effectuer des révisions. Les utilisateurs auxquels le rôle *Administration de conformité des communications* est attribué peuvent configurer des stratégies, et toute personne ayant ce rôle peut accéder à la page **de conformité des communications** et aux paramètres globaux dans le portail de conformité Microsoft Purview. Si nécessaire, vous pouvez exporter l’historique des modifications vers une stratégie vers un fichier .csv (valeurs séparées par des virgules) qui inclut également l’état des alertes en attente de révision, d’éléments réaffectés et d’éléments résolus. Les stratégies ne peuvent pas être renommées et peuvent être supprimées quand vous n’en avez plus besoin.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de stratégie sont des paramètres de stratégie prédéfinis que vous pouvez utiliser pour créer rapidement des stratégies pour répondre aux scénarios de conformité courants. Chacun de ces modèles présente des différences dans les conditions et l’étendue, et tous les modèles utilisent les mêmes types de signaux d’analyse. Vous pouvez choisir parmi les modèles de stratégie suivants :

|**Catégorie**|**Modèle de stratégie**|**Détails**|
|:-----|:-----|:-----|
| **Texte inapproprié** | Détecter le texte inapproprié | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage de révision : 100 % <br> - Conditions : classifieurs de menace, de discrimination et de harcèlement ciblé |
| **Images inappropriées** | Détecter les images inappropriées | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage de révision : 100 % <br> - Conditions : classifieurs d’images adultes et racy |
| **Informations sensibles** | Surveiller les informations sensibles | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant, interne <br> - Pourcentage de révision : 10 % <br> - Conditions : informations sensibles, modèles de contenu et types, option de dictionnaire personnalisé, pièces jointes de plus de 1 Mo |
| **Conformité réglementaire** | Surveiller la conformité réglementaire | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : entrant, sortant <br> - Pourcentage de révision : 10 % <br> - Conditions : option de dictionnaire personnalisé, pièces jointes supérieures à 1 Mo |
| **Conflit d’intérêts** | Surveiller les conflits d’intérêts | - Emplacements : Exchange Online, Microsoft Teams, Yammer, Skype Entreprise <br> - Direction : Interne <br> - Pourcentage de révision : 100 % <br> - Conditions : Aucune |

Les communications sont analysées toutes les 24 heures à partir de la création des stratégies. Par exemple, si vous créez une stratégie de contenu inappropriée à 11h00, la stratégie collecte les signaux de conformité des communications toutes les 24 heures à 11h00 tous les jours. La modification d’une stratégie ne change pas cette fois. Pour afficher la date et l’heure de la dernière analyse d’une stratégie, accédez à la colonne *Dernière analyse* de stratégie sur la page **Stratégie** . Après avoir créé une stratégie, l’affichage de la première date et heure de la première analyse de stratégie peut prendre jusqu’à 24 heures. La date et l’heure de la dernière analyse sont converties en fuseau horaire de votre système local.

## <a name="pause-a-policy-preview"></a>Suspendre une stratégie (préversion)

Une fois que vous avez créé une stratégie de conformité des communications, la stratégie peut être temporairement suspendue si nécessaire. La suspension d’une stratégie peut être utilisée pour tester ou dépanner les correspondances de stratégie, ou pour optimiser les conditions de stratégie. Au lieu de supprimer une stratégie dans ces circonstances, la suspension d’une stratégie conserve également les alertes et les messages de stratégie existants pour les examens et examens en cours. La suspension d’une stratégie empêche l’inspection et la génération d’alertes pour toutes les conditions de message utilisateur définies dans la stratégie pendant la pause de la stratégie. Pour suspendre ou redémarrer une stratégie, les utilisateurs doivent être membres du groupe de *rôles Conformité des communications Administration*.

Pour suspendre une stratégie, accédez à la page **Stratégie** , sélectionnez une stratégie, puis sélectionnez **Suspendre la stratégie** dans la barre d’outils Actions. Dans le volet **Suspendre** la stratégie, vérifiez que vous souhaitez suspendre la stratégie en sélectionnant **Suspendre**. Dans certains cas, l’interruption d’une stratégie peut prendre jusqu’à 24 heures. Une fois la stratégie suspendue, les alertes pour les messages correspondant à la stratégie ne sont pas créées. Toutefois, les messages associés aux alertes qui ont été créées avant la suspension de la stratégie restent disponibles pour l’examen, l’examen et la correction.

L’état de la stratégie pour les stratégies suspendues peut indiquer plusieurs états :

- **Actif** : la stratégie est active
- **Suspendu** : la stratégie est entièrement suspendue.
- **Suspension** : la stratégie est en cours de suspension.
- **Reprise** : Stratégie en cours de reprise.
- **Erreur lors de la reprise** : une erreur s’est produite lors de la reprise de la stratégie. Pour la trace de la pile d’erreurs, placez votre souris sur *l’erreur lors de la reprise de* l’état dans la colonne État de la page Stratégie.
- **Erreur de suspension** : une erreur s’est produite lors de la suspension de la stratégie. Pour la trace de la pile d’erreurs, pointez votre souris sur *l’erreur de suspension* de l’état dans la colonne État de la page Stratégie.

Pour reprendre une stratégie, accédez à la page **Stratégie** , sélectionnez une stratégie, puis sélectionnez **Reprendre la stratégie** dans la barre d’outils Actions. Dans le volet **Stratégie de reprise** , vérifiez que vous souhaitez reprendre la stratégie en sélectionnant **Reprendre**. Dans certains cas, la reprise d’une stratégie peut prendre jusqu’à 24 heures. Une fois la stratégie reprise, des alertes pour les messages correspondant à la stratégie seront créées et seront disponibles pour l’examen, l’examen et la correction.

## <a name="copy-a-policy-preview"></a>Copier une stratégie (préversion)

Pour les organisations avec des stratégies de conformité des communications existantes, il peut y avoir des scénarios lors de la création d’une stratégie à partir d’une stratégie existante. La copie d’une stratégie crée un doublon exact d’une stratégie existante, y compris tous les utilisateurs dans l’étendue, tous les réviseurs affectés et toutes les conditions de stratégie. Voici quelques scénarios :

- **Limite de stockage de stratégie atteinte** : les stratégies de conformité des communications actives ont des limites de stockage de messages. Lorsque la limite de stockage d’une stratégie est atteinte, la stratégie est automatiquement désactivée. Les organisations qui doivent continuer à détecter, capturer et agir sur des messages inappropriés couverts par la stratégie désactivée peuvent rapidement créer une nouvelle stratégie avec une configuration identique.
- **Détecter et examiner les messages inappropriés pour différents groupes d’utilisateurs** : certaines organisations peuvent préférer créer plusieurs stratégies avec la même configuration, mais incluent différents utilisateurs dans l’étendue et différents réviseurs pour chaque stratégie.
- **Stratégies similaires avec de petites modifications** : pour les stratégies avec des configurations ou des conditions complexes, il peut gagner du temps pour créer une stratégie à partir d’une stratégie similaire.

Pour copier une stratégie, les utilisateurs doivent être membres des groupes de *rôles Conformité des communications* ou *Conformité des communications Administration*. Une fois qu’une nouvelle stratégie a été créée à partir d’une stratégie existante, l’affichage des messages correspondant à la nouvelle configuration de stratégie peut prendre jusqu’à 24 heures.

Pour copier une stratégie et créer une stratégie, effectuez les étapes suivantes :

1. Sélectionnez la stratégie à copier.
2. Sélectionnez **le bouton Copier** la barre de commandes de stratégie dans la barre de commandes ou sélectionnez **Copier la stratégie** dans le menu d’action de la stratégie.
3. Dans le volet **Copier** la stratégie, vous pouvez accepter le nom par défaut de la stratégie dans le champ **Nom** de la stratégie ou renommer la stratégie. Le nom de stratégie de la nouvelle stratégie ne peut pas être le même qu’une stratégie active ou désactivée existante. Renseignez le champ **Description** en fonction des besoins.
4. Si vous n’avez pas besoin de personnalisation supplémentaire de la stratégie, sélectionnez **Copier la stratégie** pour terminer le processus. Si vous devez mettre à jour la configuration de la nouvelle stratégie, sélectionnez **Personnaliser la stratégie**. Cela démarre l’Assistant Stratégie pour vous aider à mettre à jour et à personnaliser la nouvelle stratégie.

## <a name="user-reported-messages-policy"></a>Stratégie de messages signalés par l’utilisateur

>[!NOTE]
>Les messages signalés par l’utilisateur commenceront à être disponibles pour les organisations sous licence pour [la conformité des communications](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) et les Microsoft Teams à compter de mai 2022. Cette fonctionnalité doit être disponible pour toutes les organisations sous licence d’ici le 31 août 2022.

Dans le cadre d’une défense en couches pour détecter et corriger les messages inappropriés dans votre organisation, vous pouvez compléter les stratégies de conformité des communications par des messages signalés par l’utilisateur dans Microsoft Teams. Cette fonctionnalité permet aux utilisateurs de votre organisation de signaler eux-mêmes des messages inappropriés, tels que le harcèlement ou la menace de langue, le partage de contenu pour adultes et le partage d’informations sensibles ou confidentielles, afin de favoriser un environnement de travail sûr et conforme.

Activé par défaut dans le [centre d’administration Teams](/microsoftteams/manage-teams-in-modern-portal), l’option *Signaler une préoccupation* dans Teams messages permet aux utilisateurs de votre organisation d’envoyer des messages inappropriés à réviser par les réviseurs de conformité des communications pour la stratégie. Ces messages sont pris en charge par une stratégie système par défaut qui prend en charge la création de rapports dans Teams canaux, les conversations de groupe et les conversations privées.

![La conformité des communications signale une préoccupation.](../media/communication-compliance-report-a-concern-full-menu.png)

Lorsqu’un utilisateur envoie un message de conversation Teams à réviser, le message est copié dans la stratégie de message signalée par l’utilisateur. Les messages signalés restent visibles initialement pour tous les membres de conversation et il n’existe aucune notification aux membres de conversation ou à l’expéditeur indiquant qu’un message a été signalé dans des conversations de canal, privées ou de groupe. Un utilisateur ne peut pas signaler le même message plusieurs fois et le message reste visible pour tous les utilisateurs inclus dans la session de conversation pendant le processus de révision de stratégie. 

Pendant le processus de révision, les réviseurs de conformité des communications peuvent effectuer toutes les [actions de correction](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) standard sur le message, y compris la suppression du message de la conversation Teams. Selon la façon dont les messages sont corrigés, l’expéditeur et les destinataires verront différents [messages de notification](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams) dans Teams conversations après la révision.

![Stratégie de messages signalés par l’utilisateur de conformité des communications.](../media/communication-compliance-user-reported-messages-policy.png)

Les messages signalés par l’utilisateur à partir de Teams conversations sont les seuls messages traités par la stratégie de message signalé par l’utilisateur et seuls les réviseurs affectés à la stratégie peuvent être modifiés. Toutes les autres propriétés de stratégie ne sont pas modifiables. Lorsque la stratégie est créée, les réviseurs initiaux affectés à la stratégie sont tous membres du groupe de *rôles Administrateurs* de conformité des communications (s’il est rempli avec au moins un utilisateur) ou tous les membres du groupe de rôles *Global Administration* de votre organisation. Le créateur de stratégie est un utilisateur sélectionné de manière aléatoire dans le groupe de *rôles Administrateurs de conformité des communications* (s’il est rempli avec au moins un utilisateur) ou un utilisateur sélectionné de manière aléatoire dans le groupe de rôles *Global Administration* de votre organisation.  

Les administrateurs doivent immédiatement affecter des réviseurs personnalisés à cette stratégie selon les besoins de votre organisation. Cela peut inclure des réviseurs tels que votre agent de conformité, l’agent des risques ou les membres de votre service des ressources humaines. Pour personnaliser les réviseurs des messages de conversation envoyés en tant que messages signalés par l’utilisateur, effectuez les étapes suivantes :

1. Connectez-vous [portail de conformité Microsoft Purview](https://compliance.microsoft.com/) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.
2. Dans le portail de conformité, accédez à **La conformité des communications**.
3. Sous l’onglet **Stratégie** , sélectionnez la stratégie *de messages signalés par l’utilisateur* , puis **sélectionnez Modifier**.
4. Dans le volet **Surveiller les messages signalés par l’utilisateur** , affectez des réviseurs pour la stratégie. Les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Lorsque les réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les avertit de l’attribution à la stratégie et fournit des liens vers des informations sur le processus de révision.
5. Sélectionnez **Enregistrer**.

L’option *Signaler une préoccupation* est activée par défaut et peut être contrôlée via Teams stratégies de messagerie dans le [centre de Teams Administration](/microsoftteams/manage-teams-in-modern-portal). Les utilisateurs de votre organisation recevront automatiquement la stratégie globale, sauf si vous créez et affectez une stratégie personnalisée. Modifiez les paramètres de la stratégie globale ou créez et affectez une ou plusieurs stratégies personnalisées pour activer ou désactiver l’option *Signaler un problème* . Pour en savoir plus, consultez [Gérer les stratégies de messagerie dans Teams](/microsoftteams/messaging-policies-in-teams).  

>[!IMPORTANT]
>Si vous utilisez PowerShell pour activer ou désactiver l’option de **création de rapports d’utilisateurs finaux** dans le centre Teams Administration, vous devez utiliser [Microsoft Teams module cmdlets version 4.2.0](/MicrosoftTeams/teams-powershell-release-notes) ou ultérieure.

## <a name="storage-limit-notification-preview"></a>Stockage notification de limite (préversion)

Chaque stratégie de conformité des communications a une taille limite de stockage de 100 Go ou 1 million de messages, selon ce qui est atteint en premier. À mesure que la stratégie approche de ces limites, les e-mails de notification sont automatiquement envoyés aux utilisateurs affectés aux groupes de *rôles Conformité des communications* ou *Conformité des communications Administration*. Les messages de notifications sont envoyés lorsque la taille de stockage ou le nombre de messages atteint 80, 90 et 95 % de la limite. Lorsque la limite de stratégie est atteinte, la stratégie est automatiquement désactivée et la stratégie cesse de traiter les messages pour les alertes.

>[!IMPORTANT]
>Si une stratégie est désactivée en raison de l’atteinte des limites de stockage et de message, veillez à évaluer comment gérer la stratégie désactivée. Si vous supprimez la stratégie, tous les messages, les pièces jointes associées et les alertes de message seront définitivement supprimés. Si vous devez conserver ces éléments pour une utilisation ultérieure, ne supprimez pas la stratégie désactivée.

Pour gérer les stratégies qui approchent des limites de stockage et de message, envisagez d’effectuer une copie de la stratégie pour maintenir la continuité de la couverture ou de prendre les mesures suivantes pour réduire la taille de stockage et le nombre de messages de stratégie actuels :

- Envisagez de réduire le nombre d’utilisateurs affectés à la stratégie. La suppression d’utilisateurs de la stratégie ou la création de stratégies différentes pour différents groupes d’utilisateurs peuvent aider à ralentir la croissance de la taille de la stratégie et du nombre total de messages.
- Examinez la stratégie pour rechercher des alertes excessives de faux positifs. Envisagez d’ajouter des exceptions ou des modifications aux conditions de stratégie pour ignorer les alertes de faux positifs courantes.
- Si une stratégie a atteint les limites de stockage ou de message et a été désactivée, effectuez une copie de la stratégie pour continuer à détecter et à prendre des mesures pour les mêmes conditions et utilisateurs.

## <a name="policy-settings"></a>Paramètres de stratégie

### <a name="users"></a>Utilisateurs

Vous pouvez choisir de sélectionner **Tous les utilisateurs** ou de définir des utilisateurs spécifiques dans une stratégie de conformité des communications. La sélection de **Tous les utilisateurs** applique la stratégie à tous les utilisateurs et les groupes auxquels n’importe quel utilisateur est inclus en tant que membre. La définition d’utilisateurs spécifiques applique la stratégie aux utilisateurs définis et aux groupes auxquels les utilisateurs définis sont inclus.

### <a name="direction"></a>Direction

Par défaut, la condition **Direction est** affichée et ne peut pas être supprimée. Les paramètres de direction de communication dans une stratégie sont choisis individuellement ou ensemble :

- **Entrant** : détecte les communications envoyées **aux** utilisateurs supervisés à partir d’expéditeurs externes et internes, y compris d’autres utilisateurs supervisés dans la stratégie.
- **Sortant** : détecte les communications envoyées **par** les utilisateurs supervisés à des destinataires externes et internes, y compris d’autres utilisateurs supervisés dans la stratégie.
- **Interne** : détecte les communications **entre** les utilisateurs ou groupes supervisés dans la stratégie.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous avez la possibilité d’inclure des types d’informations sensibles dans le cadre de votre stratégie de conformité des communications. Les types d’informations sensibles sont des types de données prédéfinis ou personnalisés qui peuvent aider à identifier et protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Dans le cadre de [Learn about Protection contre la perte de données Microsoft Purview](dlp-learn-about-dlp.md), la configuration des informations sensibles peut utiliser des modèles, la proximité des caractères, des niveaux de confiance et même des types de données personnalisés pour identifier et marquer le contenu qui peut être sensible. Les types d’informations sensibles par défaut sont les suivants :

- Financier
- Santé et médical
- Confidentialité
- Type d’informations personnalisées

> [!IMPORTANT]
> Les SIT ont deux façons différentes de définir les paramètres de nombre d’instances uniques max. Pour plus d’informations, consultez [Valeurs prises en charge par le nombre d’instances pour SIT](create-a-custom-sensitive-information-type.md#instance-count-supported-values-for-sit).

Pour en savoir plus sur les détails des informations sensibles et les modèles inclus dans les types par défaut, consultez [Définitions d’entités de type Informations sensibles](sensitive-information-type-entity-definitions.md).

### <a name="custom-keyword-dictionaries"></a>Dictionnaires de mots clés personnalisés

Configurez des dictionnaires de mots clés personnalisés (ou lexicons) pour fournir une gestion simple des mots clés spécifiques à votre organisation ou à votre secteur d’activité. Les dictionnaires de mots clés prennent en charge jusqu’à 100 Ko de termes (après compression) dans le dictionnaire et prennent en charge n’importe quelle langue. La limite de locataire est également de 100 Ko après compression. Si nécessaire, vous pouvez appliquer plusieurs dictionnaires de mots clés personnalisés à une stratégie unique ou avoir un dictionnaire de mots clés unique par stratégie. Ces dictionnaires sont affectés dans une stratégie de conformité des communications et peuvent provient d’un fichier (par exemple, une liste .csv ou .txt), ou d’une liste que vous pouvez [importer dans le Centre de conformité](create-a-keyword-dictionary.md). Utilisez des dictionnaires personnalisés lorsque vous devez prendre en charge des termes ou des langues spécifiques à votre organisation et stratégies.

### <a name="classifiers"></a>Classificateurs

[Les classifieurs intégrés et globaux pouvant être formés analysent les messages envoyés](/microsoft-365/compliance/classifier-learn-about) ou reçus sur tous les canaux de communication de votre organisation pour rechercher différents types de problèmes de conformité. Les classifieurs utilisent une combinaison d'intelligence artificielle et de mots clés pour identifier le langage dans les messages susceptibles d'enfreindre les stratégies anti-harcèlement. Les classifieurs intégrés prennent actuellement en charge l’identification des mots clés de message dans plusieurs langues :

- Arabe
- Chinois (simplifié)
- Chinois (traditionnel)
- Néerlandais
- Anglais
- Français
- Allemand
- Italien
- Korean
- Japanese
- Portugais
- Espagnol

Les classifieurs intégrés et globaux de conformité des communications analysent les communications à la recherche de termes, d’images et de sentiments pour les types de langage et de contenu suivants :

- **Images pour adultes** : analyse les images qui sont sexuellement explicites par nature.
- **Plaintes des clients** : recherche les commentaires et les plaintes concernant les produits ou services de votre organisation.
- **Discrimination** : recherche un langage discriminatoire explicite et est particulièrement sensible à la langue discriminatoire à l’égard des communautés afro-américaines/noires par rapport à d’autres communautés.
- **Images gory** : recherche des images qui décrivent la violence et le gore.
- **Harcèlement** : Analyses de comportements offensants ciblant des personnes concernant la race, la couleur, la religion, l’origine nationale.
- **Blasphème** : Recherche les expressions profanes qui gênent la plupart des gens.
- **Images racées** : recherche des images qui sont sexuellement suggestifs dans la nature, mais qui contiennent moins de contenu explicite que les images considérées comme adultes.
- **Menace** : recherche les menaces de violence ou de dommages physiques à une personne ou à des biens.

Les classifieurs d’images *Adult*, *Racy* et *Gory* analysent les fichiers aux formats .jpeg, .png, .gif et .bmp. La taille des fichiers image doit être inférieure à 4 mégaoctets (Mo) et les dimensions des images doivent être supérieures à 50 x 50 pixels et supérieures à 50 kilo-octets (Ko) pour que l’image puisse être évaluée. L’identification d’image est prise en charge pour Exchange Online messages électroniques et Microsoft Teams canaux et conversations.

Les classifieurs intégrés pouvant être formés et globaux ne fournissent pas de liste exhaustive de termes ou d’images dans ces domaines. De plus, les normes linguistiques et culturelles changent continuellement, et à la lumière de ces réalités, Microsoft se réserve le droit de mettre à jour les classifieurs à sa discrétion. Bien que les classifieurs puissent aider votre organisation à surveiller ces domaines, les classifieurs ne sont pas destinés à fournir le seul moyen de surveillance ou d’adressage de telles langues ou images de votre organisation. Votre organisation, et non Microsoft, reste responsable de toutes les décisions relatives à la surveillance, à l’analyse et au blocage de la langue et des images dans ces domaines, notamment le respect de la confidentialité locale et d’autres lois applicables. Microsoft encourage la consultation avec des conseillers juridiques avant le déploiement et l’utilisation.

> [!NOTE]
> Les stratégies utilisant des classifieurs inspectent et évaluent les messages dont le nombre de mots est égal ou supérieur à six. Les messages contenant moins de six mots ne sont pas évalués dans les stratégies à l’aide de classifieurs. Pour identifier et prendre des mesures sur les messages plus courts contenant du contenu inapproprié, nous vous recommandons d’inclure un dictionnaire de mots clés personnalisé pour la surveillance des stratégies de conformité des communications pour ce type de contenu.

### <a name="optical-character-recognition-ocr"></a>Reconnaissance optique des caractères

Configurez des stratégies de conformité de communication intégrées ou personnalisées pour analyser et identifier le texte imprimé ou manuscrit à partir d’images qui peuvent être inappropriées dans votre organisation. La [prise en charge intégrée d’Azure Cognitive Services et de l’analyse optique](/azure/cognitive-services/computer-vision/overview-ocr) pour l’identification du texte dans les images permet aux analystes et aux enquêteurs de détecter et d’agir sur des cas où des comportements inappropriés peuvent être manqués dans les communications qui sont principalement non textuelles.

Vous pouvez activer la reconnaissance optique de caractères (OCR) dans les nouvelles stratégies à partir de modèles, de stratégies personnalisées ou de mettre à jour des stratégies existantes pour étendre la prise en charge du traitement des images incorporées et des pièces jointes. Lorsqu’elle est activée dans une stratégie créée à partir d’un modèle de stratégie, l’analyse automatique est prise en charge pour les images incorporées ou jointes dans l’e-mail et les messages de conversation Microsoft Teams. Pour les images incorporées dans les fichiers de document, l’analyse OCR n’est pas prise en charge. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés à des mots clés, des classifieurs intégrés ou des types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de l’analyse OCR.

Les images de 50 Ko à 4 Mo dans les formats d’image suivants sont analysées et traitées :

- .jpg/.jpeg (groupe d’experts photographiques conjoint)
- .png (graphiques réseau portables)
- .bmp (bitmap)
- .tiff (format de fichier image de balise)
- .pdf (format de document portable)

> [!NOTE]
> L’analyse et l’extraction des images .pdf incorporées et jointes sont actuellement prises en charge uniquement pour les messages électroniques.

Lorsque vous examinez les alertes en attente pour les stratégies avec OCR activé, les images identifiées et mises en correspondance avec les conditions de stratégie sont affichées en tant qu’éléments enfants pour les alertes associées. Vous pouvez afficher l’image d’origine pour évaluer le texte identifié en contexte avec le message d’origine. La disponibilité des images détectées avec des alertes peut prendre jusqu’à 48 heures.

### <a name="conditional-settings"></a>Paramètres conditionnels
<a name="ConditionalSettings"> </a>

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications provenant de sources de messagerie et tierces de votre organisation (par exemple, à partir d’Instant Bloomberg).

Le tableau suivant explique plus en détail chaque condition.

|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le contenu correspond à l’un de ces classifieurs** | S’applique à la stratégie lorsque des classifieurs sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre locataire, et les classifieurs personnalisés doivent être configurés séparément avant d’être disponibles pour cette condition. Un seul classifieur peut être défini comme condition dans une stratégie. Pour plus d’informations sur la configuration des classifieurs, consultez [En savoir plus sur les classifieurs pouvant être formés (préversion).](classifier-learn-about.md) |
| **Le contenu contient l’un de ces types d’informations sensibles** | S’applique à la stratégie lorsque tous les types d’informations sensibles sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre locataire, et les classifieurs personnalisés peuvent être configurés séparément ou dans le cadre du processus d’attribution de condition. Chaque type d’informations sensibles que vous choisissez est appliqué séparément et un seul de ces types d’informations sensibles doit s’appliquer pour que la stratégie s’applique au message. Pour plus d’informations sur les types d’informations sensibles personnalisés, consultez [En savoir plus sur les types d’informations sensibles](sensitive-information-type-learn-about.md). |
| **Le message est reçu de l’un de ces domaines**  <br><br> **Le message n’est reçu d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines ou des adresses e-mail spécifiques dans les messages reçus. Entrez chaque domaine ou adresse e-mail et séparez plusieurs domaines ou adresses e-mail par une virgule. Chaque domaine ou adresse e-mail entré est appliqué séparément, une seule adresse de domaine ou de messagerie doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez analyser tous les e-mails d’un domaine spécifique, mais que vous souhaitez exclure les messages qui n’ont pas besoin d’être examinés (bulletins d’informations, annonces, et ainsi de suite), vous devez configurer un **message qui n’est reçu d’aucune de ces conditions de domaine** qui exclut l’adresse e-mail (exemple « newsletter@contoso.com »). |
| **Le message est envoyé à l’un de ces domaines**  <br><br> **Le message n’est envoyé à aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines spécifiques dans les messages envoyés. Entrez chaque domaine et séparez plusieurs domaines par une virgule. Chaque domaine est appliqué séparément, un seul domaine doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez exclure tous les e-mails envoyés à deux domaines spécifiques, vous devez configurer que le **message n’est envoyé à aucune de ces conditions de domaine** avec les deux domaines (exemple « contoso.com,wingtiptoys.com »). |
| **Le message est classé avec l’une de ces étiquettes**  <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Pour appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées sont choisies dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur les étiquettes de rétention, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](retention.md).|
| **Le message contient l’un de ces mots**  <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-policies.md#Matchwords).|
| **La pièce jointe contient l’un de ces mots**  <br><br> **La pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans une pièce jointe de message (par exemple, un document Word), entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](communication-compliance-policies.md#Matchwords).|
| **La pièce jointe est l’un de ces types de fichiers**  <br><br> **La pièce jointe n’est pas de ces types de fichiers** | Pour superviser les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichier (telles que .exe ou .pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichier, entrez des types de fichiers séparés par une virgule (exemple *.exe,.pdf,.zip*). Une seule extension de pièce jointe doit correspondre à la stratégie à appliquer.|
| **La taille du message est supérieure à**  <br><br> **La taille du message n’est pas supérieure à** | Pour passer en revue les messages en fonction d’une certaine taille, utilisez ces conditions pour spécifier la taille maximale ou minimale qu’un message peut être avant qu’il ne soit sujet à révision. Par exemple, si vous spécifiez que **la taille du message est supérieure** \> à **1,0 Mo**, tous les messages de 1,01 Mo et plus sont sujets à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La pièce jointe est supérieure à**  <br><br> **La pièce jointe n’est pas supérieure à** | Pour passer en revue les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale qu’une pièce jointe peut être avant que le message et ses pièces jointes soient soumis à révision. Par exemple, si vous spécifiez que la **pièce jointe est supérieure** \> à **2,0 Mo**, tous les messages avec des pièces jointes de 2,01 Mo et plus sont sujets à révision. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes
<a name="Matchwords"> </a>

Chaque mot que vous entrez et séparez par une virgule est appliqué séparément (un seul mot doit s’appliquer à la condition de stratégie à appliquer à l’e-mail ou à la pièce jointe). Par exemple, utilisons la condition, **Message contient l’un de ces mots**, avec les mots clés « banker », « confidential » et « insider trading » séparés par une virgule (banquier, confidentiel, « insider trading »). La stratégie s’applique à tous les messages qui incluent le mot « banquier », « confidentiel » ou l’expression « insider trading ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots du message ou de la pièce jointe doivent correspondre exactement à ce que vous entrez.

> [!IMPORTANT]
>
> Lors de l’importation d’un fichier de dictionnaire personnalisé, chaque mot ou expression doit être séparé par un retour chariot et sur une ligne distincte. Par exemple :
>
> *Banquier* <br>
> *Confidentiel* <br>
> *Initiés*

Pour rechercher les mêmes mots clés dans les messages électroniques et les pièces jointes, créez un [dictionnaire de mots clés personnalisé](create-a-keyword-dictionary.md) pour les termes que vous souhaitez analyser dans les messages. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **ou** dans la pièce jointe. L’utilisation des paramètres de stratégie conditionnelle standard (*message contient l’un de ces mots* et *pièce jointe contient l’un de ces mots*) pour identifier les termes dans les messages et dans les pièces jointes nécessite que les termes soient présents à la **fois** dans le message et dans la pièce jointe.

#### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer quand appliquer la stratégie de conformité des communications aux éléments de communication. Lorsque vous configurez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « trade » et est supérieur à 2 Mo. Toutefois, si le message contient également les mots « Approuvé par Contoso financial », la stratégie ne doit pas s’appliquer. Dans cet exemple, les trois conditions sont définies comme suit :

- **Le message contient l’un de ces mots**, avec le mot clé « trade »
- **La taille du message est supérieure** à, avec la valeur 2 Mo
- **Le message ne contient aucun de ces mots**, avec les mots clés « Approuvé par l’équipe financière de Contoso »

### <a name="review-percentage"></a>Pourcentage de révision

Si vous souhaitez réduire la quantité de contenu à examiner, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de conformité des communications. Un échantillon aléatoire de contenu est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les réviseurs examinent tous les éléments, vous pouvez configurer **100 %** dans une stratégie de conformité des communications.

## <a name="alert-policies"></a>Stratégies d’alerte

Après avoir configuré une stratégie, une stratégie d’alerte correspondante est automatiquement créée et des alertes sont générées pour les messages qui correspondent aux conditions définies dans la stratégie. La création d’une stratégie peut prendre jusqu’à 24 heures pour recevoir des alertes provenant d’indicateurs d’activité. Par défaut, tous les déclencheurs d’alerte correspondants à une stratégie se voient attribuer un niveau de gravité moyen dans la stratégie d’alerte associée. Les alertes sont générées pour une stratégie de conformité des communications une fois que le niveau de seuil du déclencheur d’agrégation est atteint dans la stratégie d’alerte associée. Une seule notification par e-mail est envoyée toutes les 24 heures pour toutes les alertes, quel que soit le nombre de messages individuels qui correspondent aux conditions de stratégie. Par exemple, Contoso a activé une stratégie de contenu inappropriée et, pour le 1er janvier, 100 correspondances de stratégie ont généré six alertes. Une notification par e-mail unique pour les six alertes est envoyée à la fin du 1er janvier.

Pour les stratégies de conformité des communications, les valeurs de stratégie d’alerte suivantes sont configurées par défaut :

|**Déclencheur de stratégie d’alerte**|**Valeur par défaut**|
|:-----|:-----|
| Agrégation | Agrégation simple |
| Seuil | Par défaut : 4 activités <br> Minimum : 3 activités <br> Maximum : 2 147 483 647 activités |
| Fenêtre | Valeur par défaut : 60 minutes <br> Minimum : 60 minutes <br> Maximum : 10 000 minutes |

> [!NOTE]
> Les paramètres de déclencheur de seuil de stratégie d’alerte pour les activités prennent en charge une valeur minimale de 3 ou une valeur supérieure pour les stratégies de conformité des communications.

Vous pouvez modifier les paramètres par défaut pour les déclencheurs sur le nombre d’activités, la période pour les activités et pour des utilisateurs spécifiques dans les stratégies d’alerte dans la page **Stratégies d’alerte** du portail de conformité Microsoft Purview.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Modifier le niveau de gravité d’une stratégie d’alerte

Si vous souhaitez modifier le niveau de gravité affecté dans une stratégie d’alerte pour une stratégie de conformité de communication spécifique, effectuez les étapes suivantes :

1. Connectez-vous [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le portail de conformité Microsoft Purview, accédez à **Stratégies**.

3. Sélectionnez **Office 365 alerte** dans la page **Stratégies** pour ouvrir la page **Stratégies d’alertes**.

4. Cochez la case de la stratégie de conformité des communications à mettre à jour, puis **sélectionnez Modifier la stratégie**.

5. Sous l’onglet **Description** , sélectionnez la liste déroulante **Gravité** pour configurer le niveau d’alerte de stratégie.

6. Sélectionnez **Enregistrer** pour appliquer le nouveau niveau de gravité à la stratégie.

7. Sélectionnez **Fermer** pour quitter la page de détails de la stratégie d’alerte.
