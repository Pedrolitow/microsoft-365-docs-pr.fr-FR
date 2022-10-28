---
title: Créer et gérer des stratégies de conformité des communications
description: En savoir plus sur la création et la gestion des stratégies de conformité des communications.
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
- tier1
- purview-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 783d2143fcc88bd813a44822572903640fe08fc9
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68768960"
---
# <a name="create-and-manage-communication-compliance-policies"></a>Créer et gérer des stratégies de conformité des communications

> [!IMPORTANT]
> Conformité des communications Microsoft Purview fournit les outils pour aider les organisations à détecter les violations de conformité réglementaire (par exemple SEC ou FINRA), telles que des informations sensibles ou confidentielles, des propos harcelants ou menaçants, et le partage de contenu pour adultes. Créés avec la confidentialité par défaut, les noms d’utilisateur sont pseudonymisés par défaut, les contrôles d’accès en fonction du rôle sont intégrés, les enquêteurs sont activés par un administrateur et les journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="policies"></a>Politiques

> [!IMPORTANT]
> L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité des communications](https://compliance.microsoft.com/supervisoryreview).

Vous créez des stratégies de conformité des communications pour Microsoft 365 organisations dans le portail de conformité Microsoft Purview. Les stratégies de conformité des communications définissent les communications et les utilisateurs qui sont soumis à révision dans votre organisation, définissent les conditions personnalisées auxquelles les communications doivent répondre et spécifient qui doit effectuer des révisions. Les utilisateurs auxquels est attribué le rôle *Administrateurs de conformité* des communications peuvent configurer des stratégies, et toute personne disposant de ce rôle peut accéder à la page **Conformité des communications** et aux paramètres globaux dans le portail de conformité Microsoft Purview. Si nécessaire, vous pouvez exporter l’historique des modifications apportées à une stratégie vers un fichier .csv (valeurs séparées par des virgules) qui inclut également l’état des alertes en attente de révision, des éléments réaffectés et des éléments résolus. Les stratégies ne peuvent pas être renommées et peuvent être supprimées lorsqu’elles ne sont plus nécessaires.

## <a name="policy-templates"></a>Modèles de stratégie

Les modèles de stratégie sont des paramètres de stratégie prédéfinis que vous pouvez utiliser pour créer rapidement des stratégies afin de traiter les scénarios de conformité courants. Chacun de ces modèles présente des différences de conditions et d’étendue, et tous les modèles utilisent les mêmes types de signaux d’analyse. Vous pouvez choisir parmi les modèles de stratégie suivants :

|**Catégorie**|**Modèle de stratégie**|**Détails**|
|:-----|:-----|:-----|
| **Texte inapproprié** | Détecter le texte inapproprié | - Emplacements : Exchange Online, Microsoft Teams, Yammer <br> - Direction : entrant, sortant, interne <br> - Pourcentage de révision : 100 % <br> - Conditions : classifieurs de menaces, de discrimination et de harcèlement ciblé |
| **Images inappropriées** | Détecter les images inappropriées | - Emplacements : Exchange Online, Microsoft Teams, Yammer <br> - Direction : entrant, sortant, interne <br> - Pourcentage de révision : 100 % <br> - Conditions : classifieurs d’images adultes et racé |
| **Informations sensibles** | Surveiller les informations sensibles | - Emplacements : Exchange Online, Microsoft Teams, Yammer <br> - Direction : entrant, sortant, interne <br> - Pourcentage de révision : 10 % <br> - Conditions : informations sensibles, modèles de contenu et types prêtes à l’emploi, option de dictionnaire personnalisé, pièces jointes d’une taille supérieure à 1 Mo |
| **Conformité réglementaire** | Surveiller la conformité réglementaire | - Emplacements : Exchange Online, Microsoft Teams, Yammer <br> - Direction : entrant, sortant <br> - Pourcentage de révision : 10 % <br> - Conditions : option dictionnaire personnalisé, pièces jointes supérieures à 1 Mo |
| **Conflit d’intérêts** | Surveiller les conflits d’intérêts | - Emplacements : Exchange Online, Microsoft Teams, Yammer <br> - Direction : Interne <br> - Pourcentage de révision : 100 % <br> - Conditions : Aucune |

Les communications sont analysées toutes les 24 heures à compter de la création des stratégies. Par exemple, si vous créez une stratégie de contenu inappropriée à 11h00, la stratégie collecte les signaux de conformité des communications toutes les 24 heures à 11h00 tous les jours. La modification d’une stratégie ne change pas cette fois. Pour afficher la date et l’heure de la dernière analyse d’une stratégie, accédez à la colonne *Dernière analyse de stratégie* dans la page **Stratégie** . Après avoir créé une stratégie, l’affichage de la date et de l’heure de la première analyse de stratégie peut prendre jusqu’à 24 heures. La date et l’heure de la dernière analyse sont converties en fuseau horaire de votre système local.

## <a name="user-reported-messages-policy"></a>Stratégie de messages signalés par l’utilisateur

>[!NOTE]
>La disponibilité des messages signalés par l’utilisateur pour les organisations disposant d’une licence et utilisant [la conformité des communications](/microsoft-365/compliance/communication-compliance-configure#subscriptions-and-licensing) et Microsoft Teams a commencé en mai 2022. Cette fonctionnalité sera disponible d’après le 31 août 2022 pour toutes les organisations disposant d’une licence et utilisant la conformité des communications jusqu’en juillet 2022. Pour les organisations qui commencent à utiliser la conformité des communications après juillet 2022, la disponibilité de la stratégie de messages signalés par l’utilisateur peut prendre jusqu’à 30 jours à compter de la date de votre licence et de la première utilisation de la conformité des communications.

Dans le cadre d’une défense en couches pour détecter et corriger les messages inappropriés dans votre organisation, vous pouvez compléter les stratégies de conformité des communications par des messages signalés par l’utilisateur dans Microsoft Teams. Cette fonctionnalité permet aux utilisateurs de votre organisation de signaler eux-mêmes les messages de conversation internes et de groupe inappropriés, tels que le harcèlement ou le langage menaçant, le partage de contenu pour adultes et le partage d’informations sensibles ou confidentielles, afin de favoriser un environnement de travail sûr et conforme.

Activée par défaut dans le [Centre d’administration Teams](/microsoftteams/manage-teams-in-modern-portal), l’option *Signaler un problème* dans les messages Teams permet aux utilisateurs de votre organisation d’envoyer des messages de conversation de groupe et personnels internes inappropriés pour examen par les réviseurs de conformité des communications pour la stratégie. Ces messages sont pris en charge par une stratégie système par défaut qui prend en charge la création de rapports de messages dans les conversations privées et de groupe Teams.

![Signaler un problème de conformité des communications](../media/communication-compliance-report-a-concern-full-menu.png)

Lorsqu’un utilisateur envoie un message de conversation Teams pour révision, le message est copié dans la stratégie de message signalé par l’utilisateur. Les messages signalés restent initialement visibles par tous les membres de la conversation et aucune notification n’est envoyée aux membres de la conversation ou à l’émetteur indiquant qu’un message a été signalé dans des conversations de canal, privées ou de groupe. Un utilisateur ne peut pas signaler le même message plusieurs fois et le message reste visible par tous les utilisateurs inclus dans la session de conversation pendant le processus de révision de stratégie.

Pendant le processus de révision, les réviseurs de conformité des communications peuvent effectuer toutes les [actions de correction](/microsoft-365/compliance/communication-compliance-investigate-remediate#step-3-decide-on-a-remediation-action) standard sur le message, y compris la suppression du message de la conversation Teams. Selon la façon dont les messages sont corrigés, l’expéditeur et les destinataires du message voient différents [messages de notification](/microsoftteams/communication-compliance#act-on-inappropriate-messages-in-microsoft-teams) dans les conversations Teams après la révision.

![Stratégie de messages signalés par l’utilisateur de conformité des communications](../media/communication-compliance-user-reported-messages-policy.png)

Les messages signalés par l’utilisateur à partir de conversations Teams sont les seuls messages traités par la stratégie de message signalé par l’utilisateur et seuls les réviseurs attribués pour la stratégie peuvent être modifiés. Toutes les autres propriétés de stratégie ne sont pas modifiables. Lorsque la stratégie est créée, les réviseurs initiaux affectés à la stratégie sont tous membres du groupe de rôles *Administrateurs de conformité des communications* (s’il est rempli avec au moins un utilisateur) ou tous les membres du groupe de rôles *Global Administration* de votre organisation. Le créateur de la stratégie est un utilisateur sélectionné de manière aléatoire dans le groupe de rôles *Administrateurs de conformité des communications* (s’il est rempli avec au moins un utilisateur) ou un utilisateur sélectionné de manière aléatoire dans le groupe de rôles *Global Administration* de votre organisation.

Les administrateurs doivent immédiatement affecter des réviseurs personnalisés à cette stratégie en fonction de votre organisation. Cela peut inclure des réviseurs tels que votre agent de conformité, votre responsable des risques ou des membres de votre service des ressources humaines. Pour personnaliser les réviseurs pour les messages de conversation envoyés en tant que messages signalés par l’utilisateur, procédez comme suit :

1. Connectez-vous [à portail de conformité Microsoft Purview](https://compliance.microsoft.com/) à l’aide des informations d’identification d’un compte administrateur dans votre organisation Microsoft 365.
2. Dans le portail de conformité, accédez à **Conformité des communications**.
3. Sous l’onglet **Stratégie** , sélectionnez la stratégie *Messages signalés par l’utilisateur* , puis sélectionnez **Modifier**.
4. Dans le volet **Surveiller les messages signalés par l’utilisateur** , affectez des réviseurs pour la stratégie. Les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les informe de l’affectation à la stratégie et fournit des liens vers des informations sur le processus de révision.
5. Sélectionnez **Enregistrer**.

L’option *Signaler un problème* est activée par défaut et peut être contrôlée via des stratégies de messagerie Teams dans le [Centre Administration Teams](/microsoftteams/manage-teams-in-modern-portal). Les utilisateurs de votre organisation obtiennent automatiquement la stratégie globale, sauf si vous créez et affectez une stratégie personnalisée. Modifiez les paramètres de la stratégie globale ou créez et affectez une ou plusieurs stratégies personnalisées pour activer ou désactiver l’option *Signaler un problème* . Pour en savoir plus, consultez [Gérer les stratégies de messagerie dans Teams](/microsoftteams/messaging-policies-in-teams).

>[!IMPORTANT]
>Si vous utilisez PowerShell pour activer ou désactiver l’option **Rapports des utilisateurs** finaux dans le Centre Administration Teams, vous devez utiliser le [module d’applets de commande Microsoft Teams version 4.2.0](/MicrosoftTeams/teams-powershell-release-notes) ou ultérieure.

## <a name="policy-for-insider-risk-management-integration-preview"></a>Stratégie pour l’intégration de la gestion des risques internes (préversion)

Lorsque les utilisateurs rencontrent des facteurs de stress pour l’emploi, ils peuvent devenir mécontents. Ce sentiment peut entraîner un comportement non caractéristique ou malveillant de la part de certains utilisateurs qui pourrait apparaître comme un comportement potentiellement inapproprié sur les systèmes de messagerie de votre organisation. La conformité des communications peut fournir des signaux de mécontentement détectés dans les messages applicables aux stratégies de désintégancement [de la gestion des risques internes](/microsoft-365/compliance/insider-risk-management) à l’aide d’une stratégie [de détection de texte inappropriée](#policy-templates) dédiée. Cette stratégie est créée automatiquement (si elle est sélectionnée en tant qu’option) lors de la configuration d’une [stratégie de fuites de données par des employés mécontents](/microsoft-365/compliance/insider-risk-management-policies#data-leaks-by-disgruntled-users-preview) ou [de violations de stratégie de sécurité par des employés mécontents](/microsoft-365/compliance/insider-risk-management-policies#security-policy-violations-by-disgruntled-users-preview) dans la gestion des risques internes.

Lorsqu’elle est configurée pour une stratégie de non-conformité de gestion des risques internes, une stratégie dédiée nommée *Disgruntlement dans les messages ( date de création)* est créée dans la conformité des communications et inclut automatiquement tous les utilisateurs de l’organisation dans la stratégie. Cette stratégie commence à détecter les comportements mécontents dans les messages en utilisant les [classifieurs de menaces, de harcèlement et de discrimination intégrés et](#classifiers) envoie automatiquement ces signaux à la gestion des risques internes. Si nécessaire, cette stratégie peut être modifiée pour mettre à jour l’étendue des utilisateurs inclus, ainsi que les conditions de stratégie et les classifieurs.

Les utilisateurs qui envoient 5 messages ou plus classés comme mécontents dans les 24 heures sont automatiquement placés dans le cadre des stratégies de gestion des risques internes qui incluent cette option. Une fois dans l’étendue, la gestion des risques internes détecte les activités à risque configurées dans la stratégie et génère des alertes le cas échéant. Cela peut prendre jusqu’à 48 heures entre le moment où les messages de mécontentement sont envoyés et le moment où un utilisateur est placé dans l’étendue d’une stratégie de gestion des risques internes. Si une alerte est générée pour une activité à risque détectée par la stratégie de gestion des risques internes, l’événement déclencheur de l’alerte est identifié comme provenant de l’activité de non-conformité de la communication.

Tous les utilisateurs affectés au groupe de rôles [Enquêteurs de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-plan#plan-for-the-review-and-investigation-workflow) sont automatiquement affectés en tant que réviseurs dans la stratégie de conformité des communications dédiée. Si les enquêteurs internes à la gestion des risques doivent examiner l’alerte de mécontentement associée directement dans la page des alertes de conformité des communications (liée à partir des détails de l’alerte de gestion des risques internes), ils doivent être ajoutés manuellement au groupe de rôles *Enquêteurs de conformité des communications* .

Avant d’intégrer la conformité des communications à la gestion des risques internes, vous devez également prendre en compte les conseils suivants lors de la détection des messages contenant du texte potentiellement inapproprié :

- **Pour les organisations sans stratégie *Détecter le texte inapproprié* existante**. La nouvelle stratégie *Disgruntlement dans les messages - (date de création)* sera automatiquement créée par l’Assistant Stratégie de gestion des risques internes. Dans la plupart des cas, aucune action supplémentaire n’est nécessaire.
- **Pour les organisations disposant d’une stratégie *Détecter le texte inapproprié* existante**. La nouvelle stratégie *Disgruntlement dans les messages - (date de création)* sera automatiquement créée par l’Assistant Stratégie de gestion des risques internes. Bien que vous ayez deux stratégies de conformité des communications pour le texte potentiellement inapproprié dans les messages, les enquêteurs ne verront pas les alertes en double pour la même activité. Les enquêteurs de gestion des risques internes voient uniquement les alertes pour la stratégie d’intégration dédiée et les enquêteurs de conformité des communications voient uniquement les alertes pour la stratégie existante. Si nécessaire, vous pouvez modifier la stratégie dédiée pour modifier les utilisateurs dans l’étendue ou les conditions de stratégie individuelles, le cas échéant.

## <a name="pause-a-policy"></a>Suspendre une stratégie

Une fois que vous avez créé une stratégie de conformité des communications, la stratégie peut être temporairement suspendue si nécessaire. La suspension d’une stratégie peut être utilisée pour tester ou résoudre les problèmes de correspondances de stratégie, ou pour optimiser les conditions de stratégie. Au lieu de supprimer une stratégie dans ces circonstances, la suspension d’une stratégie conserve également les alertes et les messages de stratégie existants pour les enquêtes et les révisions en cours. La suspension d’une stratégie empêche l’inspection et la génération d’alertes pour toutes les conditions de message utilisateur définies dans la stratégie au moment où la stratégie est suspendue. Pour suspendre ou redémarrer une stratégie, les utilisateurs doivent être membres du groupe de rôles *Administrateurs de conformité des communications* .

Pour suspendre une stratégie, accédez à la page **Stratégie** , sélectionnez une stratégie, puis sélectionnez **Suspendre la stratégie** dans la barre d’outils Actions. Dans le volet **Suspendre la stratégie** , vérifiez que vous souhaitez suspendre la stratégie en sélectionnant **Suspendre**. Dans certains cas, la suspension d’une stratégie peut prendre jusqu’à 24 heures. Une fois la stratégie suspendue, les alertes pour les messages correspondant à la stratégie ne sont pas créées. Toutefois, les messages associés aux alertes créées avant la suspension de la stratégie restent disponibles pour examen, examen et correction.

L’état de la stratégie pour les stratégies suspendues peut indiquer plusieurs états :

- **Actif** : la stratégie est active
- **Suspendu** : la stratégie est entièrement suspendue.
- **Suspension** : la stratégie est en cours de suspension.
- **Reprise** : stratégie en cours de reprise.
- **Erreur lors de la reprise** : une erreur s’est produite lors de la reprise de la stratégie. Pour le suivi de la pile d’erreurs, placez votre souris sur *l’état Erreur lors de la reprise* de l’état dans la colonne État de la page Stratégie.
- **Erreur lors de la suspension** : une erreur s’est produite lors de la suspension de la stratégie. Pour la trace de la pile d’erreurs, pointez votre souris sur l’état *Erreur dans* l’état de suspension dans la colonne État de la page Stratégie.

Pour reprendre une stratégie, accédez à la page **Stratégie** , sélectionnez une stratégie, puis sélectionnez **Reprendre la stratégie** dans la barre d’outils Actions. Dans le volet **Reprendre la stratégie** , confirmez que vous souhaitez reprendre la stratégie en sélectionnant **Reprendre**. Dans certains cas, la reprise d’une stratégie peut prendre jusqu’à 24 heures. Une fois la stratégie reprise, des alertes pour les messages correspondant à la stratégie sont créées et disponibles pour investigation, révision et correction.

## <a name="copy-a-policy"></a>Copier une stratégie

Pour les organisations disposant de stratégies de conformité des communications existantes, il peut s’avérer utile de créer une stratégie à partir d’une stratégie existante. La copie d’une stratégie crée un doublon exact d’une stratégie existante, y compris tous les utilisateurs dans l’étendue, tous les réviseurs affectés et toutes les conditions de stratégie. Voici quelques scénarios :

- **Limite de stockage de stratégie atteinte** : les stratégies de conformité des communications actives ont des limites de stockage de messages. Lorsque la limite de stockage d’une stratégie est atteinte, la stratégie est automatiquement désactivée. Les organisations qui doivent continuer à détecter, capturer et agir sur les messages inappropriés couverts par la stratégie désactivée peuvent rapidement créer une nouvelle stratégie avec une configuration identique.
- **Détecter et examiner les messages inappropriés pour différents groupes d’utilisateurs** : certaines organisations peuvent préférer créer plusieurs stratégies avec la même configuration, mais inclure différents utilisateurs dans l’étendue et différents réviseurs pour chaque stratégie.
- **Stratégies similaires avec de petites modifications** : pour les stratégies avec des configurations ou des conditions complexes, la création d’une stratégie à partir d’une stratégie similaire peut gagner du temps.

Pour copier une stratégie, les utilisateurs doivent être membres des groupes de rôles *Conformité des communications* ou *Administrateurs de conformité des* communications. Une fois qu’une nouvelle stratégie est créée à partir d’une stratégie existante, l’affichage des messages correspondant à la nouvelle configuration de stratégie peut prendre jusqu’à 24 heures.

Pour copier une stratégie et créer une stratégie, procédez comme suit :

1. Sélectionnez la stratégie que vous souhaitez copier.
2. Sélectionnez le bouton Copier la barre **de commandes** de la stratégie dans la barre de commandes ou sélectionnez **Copier la stratégie** dans le menu Action de la stratégie.
3. Dans le volet **Copier la stratégie** , vous pouvez accepter le nom par défaut de la stratégie dans le champ **Nom de** la stratégie ou renommer la stratégie. Le nom de la stratégie pour la nouvelle stratégie ne peut pas être identique à une stratégie active ou désactivée existante. Renseignez le champ **Description** si nécessaire.
4. Si vous n’avez pas besoin d’une personnalisation supplémentaire de la stratégie, sélectionnez **Copier la stratégie** pour terminer le processus. Si vous devez mettre à jour la configuration de la nouvelle stratégie, sélectionnez **Personnaliser la stratégie**. Cela démarre l’Assistant Stratégie pour vous aider à mettre à jour et personnaliser la nouvelle stratégie.

## <a name="policy-activity-detection"></a>Détection de l’activité de stratégie

Les communications sont analysées toutes les heures à partir de la création des stratégies. Par exemple, si vous créez une stratégie de contenu inapproprié à 11h00, la stratégie collecte les signaux de conformité des communications toutes les heures à partir de la date de création de la stratégie. La modification d’une stratégie ne change pas cette fois. Pour afficher la date et l’heure de la dernière analyse d’une stratégie, accédez à la colonne *Dernière analyse de stratégie* dans la page **Stratégie** . Après avoir créé une stratégie, l’affichage de la date et de l’heure de la première analyse de stratégie peut prendre jusqu’à une heure. La date et l’heure de la dernière analyse sont converties en fuseau horaire de votre système local.

Le tableau suivant décrit le délai de détection des types de contenu pris en charge :

|**Type de contenu**|**Délai de détection**|
|:---------------|:--------------------|
| Email contenu du corps | 1 heure |
| Contenu du corps teams | 1 heure |
| Contenu du corps yammer | 13 heures |
| Email OCR | 13 heures |
| Teams OCR | 13 heures |
| pièce jointe Email | 13 heures |
| Pièce jointe d’équipe | 13 heures |
| Pièce jointe moderne Teams | 13 heures |
| Métadonnées Teams | 1 heure |
| métadonnées Email | 1 heure |
| Canaux partagés Teams | 13 heures |

Pour les stratégies existantes créées avant le 31 juillet 2022, la détection des messages et la révision des alertes correspondant à ces stratégies peuvent prendre jusqu’à 24 heures. Pour réduire la latence de ces stratégies, [copiez la stratégie existante](/microsoft-365/compliance/communication-compliance-policies#copy-a-policy) et créez une stratégie à partir de la copie. Si vous n’avez pas besoin de conserver les données de l’ancienne stratégie, vous pouvez les suspendre ou les supprimer.

Pour identifier une stratégie plus ancienne, consultez *la colonne Dernière analyse de stratégie* dans la page **Stratégie** . Les stratégies plus anciennes affichent une date complète pour l’analyse, tandis que les stratégies créées après le 31 juillet 2022 s’affichent *il y a 1 heure* pour l’analyse. Une autre option pour réduire la latence consiste à attendre le 31 décembre 2022 pour que vos stratégies existantes soient automatiquement migrées vers les nouveaux critères de détection.

## <a name="storage-limit-notification-preview"></a>Notification de limite de stockage (préversion)

Chaque stratégie de conformité des communications a une taille de limite de stockage de 100 Go ou 1 million de messages, selon la valeur atteinte en premier. À mesure que la stratégie approche de ces limites, des e-mails de notification sont automatiquement envoyés aux utilisateurs affectés aux groupes de rôles *Conformité des communications* ou *Administrateurs de conformité des communications* . Les messages de notification sont envoyés lorsque la taille de stockage ou le nombre de messages atteint 80, 90 et 95 % de la limite. Lorsque la limite de stratégie est atteinte, la stratégie est automatiquement désactivée et la stratégie cesse de traiter les messages pour les alertes.

> [!IMPORTANT]
> Si une stratégie est désactivée en raison de l’atteinte des limites de stockage et de message, veillez à évaluer comment gérer la stratégie désactivée. Si vous supprimez la stratégie, tous les messages, pièces jointes associées et alertes de message sont supprimés définitivement. Si vous devez conserver ces éléments pour une utilisation ultérieure, ne supprimez pas la stratégie désactivée.

Pour gérer les stratégies qui approchent des limites de stockage et de messages, envisagez de créer une copie de la stratégie pour maintenir la continuité de la couverture ou d’effectuer les actions suivantes pour réduire la taille de stockage et le nombre de messages de stratégie actuels :

- Envisagez de réduire le nombre d’utilisateurs affectés à la stratégie. La suppression d’utilisateurs de la stratégie ou la création de stratégies différentes pour différents groupes d’utilisateurs peut aider à ralentir la croissance de la taille de la stratégie et du nombre total de messages.
- Examinez la stratégie pour les alertes de faux positifs excessifs. Envisagez d’ajouter des exceptions ou des modifications aux conditions de stratégie pour ignorer les alertes de faux positifs courants.
- Si une stratégie a atteint les limites de stockage ou de message et a été désactivée, effectuez une copie de la stratégie pour continuer à détecter et à prendre des mesures pour les mêmes conditions et utilisateurs.

## <a name="policy-settings"></a>Paramètres de stratégie

### <a name="users"></a>Utilisateurs

Vous pouvez choisir de sélectionner **Tous les utilisateurs** ou de définir des utilisateurs spécifiques dans une stratégie de conformité des communications. La sélection de **Tous les utilisateurs** applique la stratégie à tous les utilisateurs et les groupes auxquels n’importe quel utilisateur est inclus en tant que membre. La définition d’utilisateurs spécifiques applique la stratégie aux utilisateurs définis et aux groupes auxquels les utilisateurs définis sont inclus.

### <a name="direction"></a>Direction

Par défaut, la condition **Direction is** s’affiche et ne peut pas être supprimée. Les paramètres de direction de la communication dans une stratégie sont choisis individuellement ou ensemble :

- **Entrant** : détecte les communications envoyées **aux** utilisateurs supervisés à partir d’expéditeurs externes et internes, y compris d’autres utilisateurs supervisés dans la stratégie.
- **Sortant** : détecte les communications envoyées **des** utilisateurs supervisés à des destinataires externes et internes, y compris d’autres utilisateurs supervisés dans la stratégie.
- **Interne** : détecte les communications **entre** les utilisateurs ou groupes supervisés dans la stratégie.

### <a name="sensitive-information-types"></a>Types d’informations sensibles

Vous avez la possibilité d’inclure des types d’informations sensibles dans le cadre de votre stratégie de conformité des communications. Les types d’informations sensibles sont des types de données prédéfinis ou personnalisés qui peuvent aider à identifier et à protéger les numéros de carte de crédit, les numéros de compte bancaire, les numéros de passeport, etc. Dans le cadre [d’En savoir plus sur les Protection contre la perte de données Microsoft Purview](/microsoft-365/compliance/dlp-learn-about-dlp), la configuration des informations sensibles peut utiliser des modèles, la proximité des caractères, des niveaux de confiance et même des types de données personnalisés pour aider à identifier et à marquer le contenu susceptible d’être sensible. Les types d’informations sensibles par défaut sont les suivants :

- Financier
- Santé et médical
- Confidentialité
- Type d’informations personnalisées

> [!IMPORTANT]
> Les SIT ont deux façons différentes de définir les paramètres du nombre maximal d’instances uniques. Pour plus d’informations, consultez [Valeurs prises en charge par le nombre d’instances pour SIT](/microsoft-365/compliance/create-a-custom-sensitive-information-type#instance-count-supported-values-for-sit).

Pour en savoir plus sur les détails des informations sensibles et les modèles inclus dans les types par défaut, consultez [Définitions d’entité de type d’informations sensibles](/microsoft-365/compliance/sensitive-information-type-entity-definitions).

### <a name="custom-keyword-dictionaries"></a>Dictionnaires de mots clés personnalisés

Configurez des dictionnaires de mots clés personnalisés (ou lexiques) pour fournir une gestion simple des mots clés spécifiques à votre organisation ou secteur d’activité. Les dictionnaires de mots clés prennent en charge jusqu’à 100 Ko de termes (post-compression) dans le dictionnaire et prennent en charge n’importe quelle langue. La limite de locataire est également de 100 Ko après la compression. Si nécessaire, vous pouvez appliquer plusieurs dictionnaires de mots clés personnalisés à une seule stratégie ou avoir un seul dictionnaire de mots clés par stratégie. Ces dictionnaires sont attribués dans une stratégie de conformité des communications et peuvent provenir d’un fichier (tel qu’une liste .csv ou .txt), ou d’une liste que vous pouvez [importer dans le portail de conformité](/microsoft-365/compliance/create-a-keyword-dictionary). Utilisez des dictionnaires personnalisés lorsque vous devez prendre en charge des termes ou des langues spécifiques à votre organisation et à vos stratégies.

### <a name="classifiers"></a>Classificateurs

[Les classifieurs globaux et entraînables](/microsoft-365/compliance/classifier-learn-about) intégrés inspectent les messages envoyés ou reçus sur tous les canaux de communication de votre organisation pour détecter différents types de problèmes de conformité. Les classifieurs utilisent une combinaison d'intelligence artificielle et de mots clés pour identifier le langage dans les messages susceptibles d'enfreindre les stratégies anti-harcèlement.

Les stratégies utilisant des classifieurs inspectent et évaluent les messages dont le nombre de mots est supérieur ou égal à six. Les messages contenant moins de six mots ne sont pas évalués dans les stratégies à l’aide de classifieurs. Pour identifier et prendre des mesures sur les messages plus courts contenant du contenu inapproprié, nous vous recommandons d’inclure un dictionnaire de mots clés personnalisé aux stratégies de conformité de communication détectant ce type de contenu.

La conformité des communications peut utiliser des classifieurs intégrés et globaux spécifiques pour inspecter les communications pour les types de langage et de contenu suivants :

|**Classifieur**|**Description**|
|:-------------|:--------------|
| **Images pour adultes** | Détecte les images potentiellement sexuellement explicites par nature. |
| **Sabotage d’entreprise (préversion)** | Détecte les messages qui peuvent mentionner des actes pour endommager ou détruire des biens ou des biens de l’entreprise. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire, telles que les normes de protection de l’infrastructure critique de la NERC ou les réglementations par état comme le chapitre 9.05 RCW dans l’état de Washington. |
| **Plaintes des clients (préversion)** | Détecte les messages qui peuvent suggérer des plaintes des clients concernant les produits ou services de votre organisation, comme l’exige la loi pour les secteurs réglementés. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la Règle 4530 de la FINRA, la FINRA 4513, la FINRA 2111, le Consumer Financial Protection Bureau, le Code of Federal Regulations Title 21: Food and Drugs et la Loi sur la Federal Trade Commission. |
| **Discrimination** | Détecte une langue discriminatoire potentiellement explicite et est particulièrement sensible à la langue discriminatoire à l’égard des communautés afro-américaines/noires par rapport à d’autres communautés. |
| **Cadeaux & divertissement (préversion)** | Détecte les messages qui peuvent suggérer l’échange de cadeaux ou de divertissements en échange d’un service, ce qui enfreint les réglementations liées à la corruption. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la Loi sur les pratiques corrompues étrangères (FCPA), la loi britannique sur la corruption et la règle 2320 de la FINRA. |
| **Images gory** | Détecte les images qui représentent potentiellement la violence et le gore. |
| **Harcèlement** | Détecte les comportements potentiellement offensants ciblant des personnes concernant la race, la couleur, la religion, l’origine nationale. |
| **Blanchiment d’argent (préversion)** | Détecte les signes qui peuvent suggérer le blanchiment d’argent ou la participation à des actes de dissimulation ou de déguisement de l’origine ou de la destination du produit. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la Bank Secrecy Act, l’USA Patriot Act, la règle 3310 de la FINRA et la loi anti-blanchiment de 2020. |
| **Vulgarité** | Détecte les expressions potentiellement profanes qui embarrassent la plupart des gens. |
| **Images racé** | Détecte les images potentiellement suggestives à caractère sexuel, mais qui contiennent moins de contenu explicite que les images considérées comme adultes. |
| **Collusion réglementaire (préversion)** | Détecte les messages susceptibles d’enfreindre les exigences réglementaires en matière de collusion, comme une tentative de dissimulation d’informations sensibles. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que le Sherman Antitrust Act, la Securities Exchange Act 1933, la Securities Exchange Act de 1934, la Loi sur les conseillers en placement de 1940, la Loi sur la Commission fédérale et la Loi sur la Robinson-Patman. |
| **Manipulation de stock (préversion)** | Détecte les signes d’une possible manipulation des actions, comme des recommandations d’achat, de vente ou de conservation d’actions qui peuvent suggérer une tentative de manipulation du cours des actions. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la Loi sur la bourse de valeurs mobilières de 1934, la règle 2372 de la FINRA et la règle 5270 de la FINRA. |
| **Menace** | Détecte les menaces potentielles de violence ou de préjudice physique à une personne ou à un bien. |
| **Divulgation non autorisée (préversion)** | Détecte le partage d’informations contenant du contenu qui est explicitement désigné comme confidentiel ou interne à des personnes non autorisées. Ce classifieur peut aider les clients à gérer les obligations de conformité réglementaire telles que la règle FINRA 2010 et la règle SEC 10b-5. |

> [!IMPORTANT]
> Les classifieurs en préversion peuvent détecter un grand volume de contenu d’expéditeur/bulletin d’informations en bloc en raison d’un problème connu. Bien que ces classifieurs soient en préversion, vous pouvez atténuer la détection de grands volumes de contenu de l’expéditeur en bloc/bulletin d’informations en ajoutant la [condition *Message n’est envoyé à aucun de ces domaines*](/microsoft-365/compliance/communication-compliance-policies#conditional-settings) à vos stratégies avec une liste de domaines à exclure.

> [!NOTE]
> Les stratégies utilisant des classifieurs de menaces, de harcèlement et de grossièretés en anglais inspectent et évaluent les messages dont le nombre de mots est supérieur ou égal à trois. Les messages contenant moins de trois mots ne sont pas évalués dans les stratégies utilisant ces types de classifieurs. Pour identifier et prendre des mesures sur les messages plus courts contenant du contenu inapproprié, nous vous recommandons d’inclure un dictionnaire de mots clés personnalisé aux stratégies de conformité de communication détectant ce type de contenu.

### <a name="optical-character-recognition-ocr"></a>Reconnaissance optique des caractères

Configurez des stratégies de conformité de communication intégrées ou personnalisées pour analyser et identifier le texte imprimé ou manuscrit à partir d’images qui peuvent être inappropriés dans votre organisation. Azure [Cognitive Services intégré et la prise en charge de la numérisation optique](/azure/cognitive-services/computer-vision/overview-ocr) pour l’identification du texte dans les images aident les analystes et les enquêteurs à détecter et à agir sur les cas où un comportement inapproprié peut être manqué dans des communications qui sont principalement non textuelles.

Vous pouvez activer la reconnaissance optique de caractères (OCR) dans de nouvelles stratégies à partir de modèles ou de stratégies personnalisées, ou mettre à jour les stratégies existantes pour étendre la prise en charge du traitement des images incorporées et des pièces jointes. Lorsqu’elle est activée dans une stratégie créée à partir d’un modèle de stratégie, l’analyse automatique est prise en charge pour les images incorporées ou jointes dans les e-mails et les messages de conversation Microsoft Teams. Pour les images incorporées dans des fichiers de document, l’analyse OCR n’est pas prise en charge. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés à des mots clés, des classifieurs intégrés ou des types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de l’analyse OCR.

Les images de 50 Ko à 4 Mo dans les formats d’image suivants sont analysées et traitées :

- .jpg/.jpeg (groupe conjoint d’experts photographiques)
- .png (graphiques réseau portables)
- .bmp (bitmap)
- .tiff (format de fichier image de balise)
- .pdf (format de document portable)

> [!NOTE]
> L’analyse et l’extraction des images .pdf incorporées et jointes sont actuellement prises en charge uniquement pour les messages électroniques.

Lors de l’examen des alertes en attente pour les stratégies avec la reconnaissance optique de caractères activée, les images identifiées et mises en correspondance avec les conditions de stratégie sont affichées en tant qu’éléments enfants pour les alertes associées. Vous pouvez afficher l’image d’origine pour évaluer le texte identifié en contexte avec le message d’origine. La disponibilité des images détectées avec des alertes peut prendre jusqu’à 48 heures.

### <a name="conditional-settings"></a>Paramètres conditionnels

Les conditions que vous choisissez pour la stratégie s’appliquent aux communications provenant à la fois de la messagerie électronique et de sources tierces de votre organisation (par exemple, à partir d’Instant Bloomberg).

Le tableau suivant explique plus en détail chaque condition.

|**Condition**|**Comment utiliser cette condition ?**|
|:-----|:-----|
| **Le contenu correspond à l’un de ces classifieurs** | Appliquez à la stratégie quand des classifieurs sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre organisation, et les classifieurs personnalisés doivent être configurés séparément avant d’être disponibles pour cette condition. Un seul classifieur peut être défini comme condition dans une stratégie. Pour plus d’informations sur la configuration des classifieurs, consultez [En savoir plus sur les classifieurs pouvant être formés (préversion)](/microsoft-365/compliance/classifier-learn-about) . |
| **Le contenu contient l’un de ces types d’informations sensibles** | Appliquer à la stratégie lorsque des types d’informations sensibles sont inclus ou exclus dans un message. Certains classifieurs sont prédéfinis dans votre locataire, et les classifieurs personnalisés peuvent être configurés séparément ou dans le cadre du processus d’attribution de condition. Chaque type d’informations sensibles que vous choisissez est appliqué séparément et un seul de ces types d’informations sensibles doit s’appliquer pour que la stratégie s’applique au message. Pour plus d’informations sur les types d’informations sensibles personnalisés, consultez [En savoir plus sur les types d’informations sensibles](/microsoft-365/compliance/sensitive-information-type-learn-about). |
| **Un message est reçu de l’un de ces domaines** <br><br> **Le message n’est reçu d’aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines spécifiques dans les messages reçus. Entrez chaque domaine et séparez plusieurs domaines par une virgule. Chaque domaine entré est appliqué séparément, un seul domaine doit s’appliquer pour que la stratégie s’applique au message. Si vous souhaitez utiliser **Message reçu à partir de l’un de ces domaines** pour rechercher des messages provenant d’une adresse e-mail spécifique, vous devez combiner cette condition avec une autre condition telle que **Message contient l’un de ces mots** ou **Le contenu correspond à l’un de ces classifieurs** , ou vous pouvez obtenir des résultats inattendus. <br><br> Si vous souhaitez analyser tous les e-mails d’un domaine spécifique, mais que vous souhaitez exclure les messages qui n’ont pas besoin d’être examinés (bulletins d’informations, annonces, etc.), vous devez configurer que le **message n’est reçu d’aucune de ces conditions de domaines** qui exclut l’adresse e-mail (par exemple, newsletter@contoso.com). |
| **Le message est envoyé à l’un de ces domaines** <br><br> **Le message n’est envoyé à aucun de ces domaines** | Appliquez la stratégie pour inclure ou exclure des domaines spécifiques dans les messages envoyés. Entrez chaque domaine et séparez plusieurs domaines par une virgule. Chaque domaine est appliqué séparément, un seul domaine doit s’appliquer pour que la stratégie s’applique au message. <br><br> Si vous souhaitez exclure tous les e-mails envoyés à deux domaines spécifiques, vous devez configurer la condition **Message n’est envoyé à aucun de ces domaines** avec les deux domaines (exemple « contoso.com,wingtiptoys.com »). |
| **Le message est classé avec l’une de ces étiquettes** <br><br> **Le message n’est classé avec aucune de ces étiquettes** | Pour appliquer la stratégie lorsque certaines étiquettes de rétention sont incluses ou exclues dans un message. Les étiquettes de rétention doivent être configurées séparément et les étiquettes configurées sont choisies dans le cadre de cette condition. Chaque étiquette que vous choisissez est appliquée séparément (une seule de ces étiquettes doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur les étiquettes de rétention, consultez [En savoir plus sur les stratégies de rétention et les étiquettes de rétention](/microsoft-365/compliance/retention).|
| **Le message contient l’un de ces mots** <br><br> **Le message ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans un message, entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique au message). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](#matching-words-and-phrases-to-emails-or-attachments).|
| **La pièce jointe contient l’un de ces mots** <br><br> **Pièce jointe ne contient aucun de ces mots** | Pour appliquer la stratégie lorsque certains mots ou expressions sont inclus ou exclus dans une pièce jointe de message (tel qu’un document Word), entrez chaque mot séparé par une virgule. Pour les expressions de deux mots ou plus, utilisez des guillemets autour de l’expression. Chaque mot ou expression que vous entrez est appliqué séparément (un seul mot doit s’appliquer pour que la stratégie s’applique à la pièce jointe). Pour plus d’informations sur la saisie des mots ou des expressions, voir la section suivante [Matching words and phrases to emails or attachments](#matching-words-and-phrases-to-emails-or-attachments).|
| **La pièce jointe est l’un de ces types de fichiers** <br><br> **Pièce jointe ne correspond à aucun de ces types de fichiers** | Pour superviser les communications qui incluent ou excluent des types spécifiques de pièces jointes, entrez les extensions de fichier (telles que .exe ou .pdf). Si vous souhaitez inclure ou exclure plusieurs extensions de fichier, entrez les types de fichiers séparés par une virgule (exemple *.exe,.pdf,.zip*). Une seule extension de pièce jointe doit correspondre pour que la stratégie s’applique.|
| **La taille du message est supérieure à** <br><br> **La taille du message n’est pas supérieure à** | Pour passer en revue les messages en fonction d’une certaine taille, utilisez ces conditions pour spécifier la taille maximale ou minimale d’un message avant d’être soumis à révision. Par exemple, si vous spécifiez **que la taille du message est supérieure** \> à **1 Mo**, tous les messages de 1,01 Mo et plus sont susceptibles d’être examinés. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|
| **La pièce jointe est plus grande que** <br><br> **La pièce jointe n’est pas supérieure à** | Pour passer en revue les messages en fonction de la taille de leurs pièces jointes, spécifiez la taille maximale ou minimale d’une pièce jointe avant que le message et ses pièces jointes soient soumis à révision. Par exemple, si vous spécifiez **Pièce jointe supérieure** \> à **2 Mo**, tous les messages avec des pièces jointes de 2,01 Mo et plus sont susceptibles d’être examinés. Vous pouvez choisir des octets, kilo-octets, mégaoctets ou gigaoctets pour cette condition.|

#### <a name="matching-words-and-phrases-to-emails-or-attachments"></a>Correspondance de mots et expressions avec des courriers électroniques ou des pièces jointes

Chaque mot que vous entrez et séparez par une virgule est appliqué séparément (un seul mot doit s’appliquer pour que la condition de stratégie s’applique à l’e-mail ou à la pièce jointe). Par exemple, utilisons la condition **, Message contient l’un de ces mots**, avec les mots clés « banquier », « confidentiel » et « délit d’initié » séparés par une virgule (banquier, confidentiel, « délit d’initié »). La politique s’applique à tous les messages qui incluent le mot « banquier », « confidentiel » ou l’expression « délit d’initié ». Un seul de ces mots ou expression doit être présent pour que cette condition de stratégie s’applique. Les mots du message ou de la pièce jointe doivent correspondre exactement à ce que vous entrez.

> [!IMPORTANT]
>
> Lors de l’importation d’un fichier de dictionnaire personnalisé, chaque mot ou expression doit être séparé par un retour chariot et sur une ligne distincte. Par exemple :
>
> *Banquier* <br>
> *Confidentiel* <br>
> *Initiés*

Pour analyser les mêmes mots clés dans les messages électroniques et les pièces jointes, créez un [dictionnaire de mots clés personnalisé](/microsoft-365/compliance/create-a-keyword-dictionary) pour les termes que vous souhaitez analyser dans les messages. Cette configuration de stratégie identifie les mots clés définis qui apparaissent dans le message électronique **OU** dans la pièce jointe de l’e-mail. L’utilisation des paramètres de stratégie conditionnelle standard (*Message contient l’un de ces mots* et *Pièce jointe contient l’un de ces mots*) pour identifier les termes dans les messages et dans les pièces jointes nécessite que les termes soient présents à la **fois** dans le message et la pièce jointe.

#### <a name="enter-multiple-conditions"></a>Entrer plusieurs conditions

Si vous entrez plusieurs conditions, Microsoft 365 utilise toutes les conditions ensemble pour déterminer quand appliquer la stratégie de conformité des communications aux éléments de communication. Lorsque vous configurez plusieurs conditions, toutes les conditions doivent être remplies pour que la stratégie s’applique, sauf si vous entrez une exception. Par exemple, vous avez besoin d’une stratégie qui s’applique si un message contient le mot « trade » et est supérieur à 2 Mo. Toutefois, si le message contient également les mots « Approuvé par Contoso financial », la stratégie ne doit pas s’appliquer. Dans cet exemple, les trois conditions sont définies comme suit :

- **Le message contient l’un de ces mots**, avec le mot clé « trade »
- **La taille du message est supérieure** à, avec la valeur 2 Mo
- **Le message ne contient aucun de ces mots**, avec les mots clés « Approuvé par l’équipe financière de Contoso »

### <a name="review-percentage"></a>Pourcentage de révision

Si vous souhaitez réduire la quantité de contenu à réviser, vous pouvez spécifier un pourcentage de toutes les communications régies par une stratégie de conformité des communications. Un échantillon aléatoire de contenu est sélectionné à partir du pourcentage total de contenu qui correspond aux conditions de stratégie choisies. Si vous souhaitez que les réviseurs examinent tous les éléments, vous pouvez configurer **100 %** dans une stratégie de conformité des communications.

## <a name="alert-policies"></a>Stratégies d’alerte

Après avoir configuré une stratégie, une stratégie d’alerte correspondante est automatiquement créée et des alertes sont générées pour les messages qui correspondent aux conditions définies dans la stratégie. La création d’une stratégie peut prendre jusqu’à 24 heures pour recevoir des alertes à partir d’indicateurs d’activité. Par défaut, tous les déclencheurs d’alerte correspondant à une stratégie se voient attribuer un niveau de gravité moyen dans la stratégie d’alerte associée. Des alertes sont générées pour une stratégie de conformité des communications une fois que le niveau de seuil du déclencheur d’agrégation est atteint dans la stratégie d’alerte associée. Une notification par e-mail unique est envoyée toutes les 24 heures pour toutes les alertes, quel que soit le nombre de messages individuels qui correspondent aux conditions de stratégie. Par exemple, Contoso a une stratégie de contenu inappropriée activée et pour le 1er janvier, 100 correspondances de stratégie ont généré six alertes. Une seule notification par e-mail pour les six alertes est envoyée à la fin du 1er janvier.

Pour les stratégies de conformité des communications, les valeurs de stratégie d’alerte suivantes sont configurées par défaut :

|**Déclencheur de stratégie d’alerte**|**Valeur par défaut**|
|:-----|:-----|
| Agrégation | Agrégation simple |
| Seuil | Par défaut : 4 activités <br> Minimum : 3 activités <br> Maximum : 2 147 483 647 activités |
| Fenêtre | Valeur par défaut : 60 minutes <br> Minimum : 60 minutes <br> Maximum : 10 000 minutes |

> [!NOTE]
> Les paramètres de déclencheur de seuil de stratégie d’alerte pour les activités prennent en charge une valeur minimale de 3 ou plus pour les stratégies de conformité des communications.

Vous pouvez modifier les paramètres par défaut des déclencheurs sur le nombre d’activités, la période des activités et pour des utilisateurs spécifiques dans les stratégies d’alerte sur la page **Stratégies d’alerte** dans le portail de conformité Microsoft Purview.

### <a name="change-the-severity-level-for-an-alert-policy"></a>Modifier le niveau de gravité d’une stratégie d’alerte

Si vous souhaitez modifier le niveau de gravité affecté dans une stratégie d’alerte pour une stratégie de conformité des communications spécifique, procédez comme suit :

1. Connectez-vous [à portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte administrateur dans votre organisation Microsoft 365.

2. Dans la portail de conformité Microsoft Purview, accédez à **Stratégies**.

3. Sélectionnez **Office 365 alerte** dans la page **Stratégies** pour ouvrir la page **Stratégies d’alertes**.

4. Cochez la case pour la stratégie de conformité des communications que vous souhaitez mettre à jour, puis sélectionnez **Modifier la stratégie**.

5. Sous l’onglet **Description** , sélectionnez la liste déroulante **Gravité** pour configurer le niveau d’alerte de stratégie.

6. Sélectionnez **Enregistrer** pour appliquer le nouveau niveau de gravité à la stratégie.

7. Sélectionnez **Fermer** pour quitter la page des détails de la stratégie d’alerte.
