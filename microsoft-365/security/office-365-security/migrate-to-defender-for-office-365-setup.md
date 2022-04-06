---
title: 'Migrer vers Microsoft Defender pour Office 365 Phase 2 : Installation'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Prenez les mesures nécessaires pour commencer la migration d’un service ou d’un appareil de protection tiers vers Microsoft Defender pour Office 365 protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f4f6e1d557915fe40dc570cd58374371e0e9b6a3
ms.sourcegitcommit: b0c3ffd7ddee9b30fab85047a71a31483b5c649b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2022
ms.locfileid: "64474924"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Migrer vers Microsoft Defender pour Office 365 - Phase 2 : Installation

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

<br>

|[![Phase 1 : Préparer.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Phase 1 : préparation](migrate-to-defender-for-office-365-prepare.md)|![Phase 2 : Configurer.](../../media/phase-diagrams/setup.png) <br> Phase 2 : configuration|[![Phase 3 : Intégration.](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Phase 3 : intégration](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Vous êtes là !*||

Bienvenue dans **la phase 2 : configuration** de **[votre migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process)** ! Cette phase de migration comprend les étapes suivantes :

1. [Créer des groupes de distribution pour les utilisateurs pilotes](#step-1-create-distribution-groups-for-pilot-users)
2. [Configurer l’envoi d’utilisateurs pour les rapports de messages utilisateur](#step-2-configure-user-submission-for-user-message-reporting)
3. [Gérer ou créer la règle de flux de messagerie SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Configurer le filtrage amélioré pour les connecteurs](#step-4-configure-enhanced-filtering-for-connectors)
5. [Créer des stratégies de protection pilote](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>Étape 1 : Créer des groupes de distribution pour les utilisateurs pilotes

Les groupes de distribution sont requis Microsoft 365 pour les aspects suivants de votre migration :

- Exceptions à la règle de flux de messagerie **SCL=-1** : vous souhaitez que les utilisateurs pilotes obtiennent l’effet complet de Defender pour la protection Office 365, de sorte que vous avez besoin que leurs messages entrants soient analysés par Defender pour Office 365. Pour ce faire, définissez vos utilisateurs pilotes dans les groupes de distribution appropriés dans Microsoft 365 et configurez ces groupes en tant qu’exceptions à la règle de flux de messagerie SCL=-1.

  Comme nous l’avons décrit à l’étape 2 de l’intégration [: (facultatif)](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service) exemptez les utilisateurs pilotes du filtrage par votre service de protection existant, vous devez envisager d’exempter ces mêmes utilisateurs pilotes de l’analyse par votre service de protection existant. L’élimination de la possibilité de filtrage par votre service de protection existant et de s’appuyer exclusivement sur Defender pour Office 365 est la représentation la plus proche et la plus proche de ce qui se passe une fois la migration terminée.

- **Test des fonctionnalités de protection** de Office 365 Defender spécifiques : même pour les utilisateurs pilotes, vous ne souhaitez pas activer tous les éléments en même temps. L’utilisation d’une approche par étapes pour les fonctionnalités de protection qui sont en vigueur pour vos utilisateurs pilotes facilite la résolution des problèmes et l’ajustement. Dans cette approche, nous vous recommandons les groupes de distribution suivants :
  - **Un Coffre de pièces jointes** : par exemple, **MDOPilotSafeAttachments\_**
  - **Groupe pilote Coffre liens** : par exemple, **MDOPilotSafeLinks\_**
  - **Un groupe pilote pour les paramètres de stratégie anti-courrier indésirable et anti-hameçonnage** standard : par exemple, **MDOPilotSpamPhishStandard\_\_**
  - **Un groupe pilote pour les paramètres stricts de stratégie anti-courrier indésirable et anti-hameçonnage** : par exemple, **MDOPilotSpamPhishStrict\_\_**

Pour plus de clarté, nous allons utiliser ces noms de groupes spécifiques tout au long de cet article, mais vous êtes libre d’utiliser votre propre convention d’attribution de noms.

Lorsque vous êtes prêt à commencer le test, ajoutez ces groupes en tant qu’exceptions à la règle de flux de messagerie [SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Lorsque vous créez des stratégies pour les différentes fonctionnalités de protection dans Defender pour Office 365, vous utilisez ces groupes comme conditions qui définissent à qui s’applique la stratégie.

**Remarques** :

- Les termes Standard et Strict proviennent de nos [paramètres de sécurité recommandés](recommended-settings-for-eop-and-office365.md), qui sont également utilisés dans les stratégies [de sécurité prédéfinées](preset-security-policies.md). Dans l’idéal, nous vous indiquerons de définir vos utilisateurs pilotes dans les stratégies de sécurité standard et stricte, mais nous ne pouvons pas le faire. Pourquoi ? Étant donné que vous ne pouvez pas personnaliser les paramètres dans les stratégies de sécurité prédéfinie (en particulier, les actions entreprises sur les messages ou l’ajustement des paramètres de protection contre l’emprunt d’identité). Au cours de vos tests de migration, vous voudrez voir ce que Defender pour Office 365 ferait pour les messages, vérifier que c’est ce que vous voulez faire et éventuellement ajuster les configurations de stratégie pour autoriser ou empêcher ces résultats.

  Par conséquent, au lieu d’utiliser des stratégies de sécurité prédéfines, vous allez créer manuellement des stratégies personnalisées avec des paramètres très similaires aux paramètres des stratégies de sécurité standard et stricte, mais dans certains cas sont différents.

- Si vous souhaitez expérimenter des paramètres qui  diffèrent considérablement de nos valeurs standard ou stricte recommandées, vous devez envisager de créer et d’utiliser des groupes de distribution supplémentaires et spécifiques pour les utilisateurs pilotes dans ces scénarios. Vous pouvez utiliser l’Analyseur de configuration pour voir si vos paramètres sont sécurisés. Pour obtenir des instructions, [consultez l’analyseur de configuration pour les stratégies de protection dans EOP et Microsoft Defender pour Office 365](configuration-analyzer-for-security-policies.md).

  Pour la plupart des organisations, la meilleure approche consiste à commencer par des stratégies qui s’alignent étroitement avec nos paramètres Standard recommandés. Après autant d’observations et de commentaires que vous pouvez le faire dans votre période disponible, vous pouvez passer à des paramètres plus agressifs ultérieurement. La protection et la remise de l’emprunt d’identité au dossier Courrier indésirable et la remise en quarantaine peuvent nécessiter une personnalisation.

  Si vous utilisez des stratégies personnalisées, assurez-vous simplement qu’elles sont appliquées avant les stratégies qui contiennent nos paramètres recommandés pour la migration. Si un utilisateur est identifié dans plusieurs stratégies du même type (par exemple, anti-hameçonnage), une seule stratégie de ce type est appliquée à l’utilisateur (en fonction de la valeur de priorité de la stratégie). Pour plus d’informations, voir [Ordre et priorité de la protection de la messagerie](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>Étape 2 : Configurer l’envoi d’utilisateurs pour les rapports de messages utilisateur

La possibilité pour les utilisateurs d’identifier les faux positifs ou les faux négatifs de Defender pour Office 365 est une partie importante de la migration.

Vous pouvez spécifier une boîte Exchange Online pour recevoir des messages que les utilisateurs signalent comme malveillants ou non malveillants. Pour plus d’instructions, voir [Paramètres des messages signalés par l’utilisateur](user-submission.md). Cette boîte aux lettres peut recevoir des copies des messages que vos utilisateurs ont envoyés à Microsoft, ou la boîte aux lettres peut intercepter les messages sans les signaler à Microsoft (votre équipe de sécurité peut analyser et envoyer manuellement les messages). Toutefois, cette approche d’interception ne permet pas au service d’affiner et d’apprendre automatiquement.

Vous devez également vérifier que tous les utilisateurs du projet pilote ont installé une application de rapport de messages prise en charge dans Outlook compatible avec la soumission d’utilisateurs. Ces applications sont les suivantes :

- [Le add-in Message de rapport](enable-the-report-message-add-in.md)
- [Le module de signalement du hameçonnage](enable-the-report-phish-add-in.md)
- Outils de rapport tiers pris en charge, comme décrit [ici](user-submission.md#third-party-reporting-tools).

Ne sous-estimez pas l’importance de cette étape. Les données issues des soumissions d’utilisateurs vous donnent la boucle de commentaires dont vous avez besoin pour vérifier une bonne expérience cohérente de l’utilisateur final avant et après la migration. Ces commentaires vous aident à prendre des décisions de configuration de stratégie éclairées, ainsi qu’à fournir à votre direction des rapports sur la bonne déroulement de la migration.

Au lieu de s’appuyer sur des données reposant sur l’expérience de l’ensemble de l’organisation, plusieurs migrations ont donné lieu à des émo gations d’émulation basées sur une expérience utilisateur négative unique. En outre, si vous exécutez des simulations de hameçonnage, vous pouvez utiliser les commentaires de vos utilisateurs pour vous informer lorsqu’ils voient un risque qui peut nécessiter une enquête.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>Étape 3 : Gérer ou créer la règle de flux de messagerie SCL=-1

Étant donné que votre courrier entrant est acheminé via un autre service de protection qui se trouve devant Microsoft 365, il est très probable que vous avez déjà une règle de flux de messagerie (également appelée règle de transport) dans Exchange Online qui définit le niveau de confiance du courrier indésirable (SCL) de tous les messages entrants sur la valeur -1 (contourner le filtrage du courrier indésirable). La plupart des services de protection tiers encouragent cette règle de flux de messagerie SCL=-1 pour Microsoft 365 clients qui souhaitent utiliser leurs services.

Si vous utilisez un autre mécanisme pour remplacer la pile de filtrage Microsoft (par exemple, une liste d’adresses IP permises), nous vous recommandons d’utiliser une règle de flux de messagerie SCL=-1 tant que tous les messages Internet entrants entrants dans Microsoft 365 proviennent du service de protection tiers (aucun flux de courrier provenant directement d’Internet vers Microsoft 365).

La règle de flux de messagerie SCL=-1 est importante pendant la migration pour les raisons suivantes :

- Vous pouvez utiliser [l’Explorateur](email-security-in-microsoft-defender.md) de menaces pour voir quelles  fonctionnalités de la pile Microsoft auraient eu lieu sur les messages sans affecter les résultats de votre service de protection existant.
- Vous pouvez ajuster progressivement les personnes protégées par la pile de filtrage Microsoft 365 en configurant des exceptions à la règle de flux de messagerie SCL=-1. Les exceptions seront les membres des groupes de distribution pilotes que nous vous recommandons plus loin dans cet article.

  Avant ou pendant le passage de votre enregistrement MX à Microsoft 365, vous désactivez cette règle pour activer la protection complète de la pile de protection Microsoft 365 pour tous les destinataires de votre organisation.

Pour plus d’informations, voir Utiliser des règles de flux de messagerie pour définir le niveau de confiance du courrier indésirable [(SCL) dans les messages Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Remarques** :

- Si vous prévoyez d’autoriser le flux de messagerie Internet via **votre service de** protection existant et directement dans Microsoft 365 en même temps, vous devez limiter la règle de flux de messagerie SCL=-1 (courrier qui contourne le filtrage du courrier indésirable) aux messages qui ont été envoyés via votre service de protection existant uniquement. Vous ne souhaitez pas que le courrier Internet non filtré soit envoyé dans les boîtes aux lettres des utilisateurs Microsoft 365.

  Pour identifier correctement les messages qui ont déjà été analysés par votre service de protection existant, vous pouvez ajouter une condition à la règle de flux de messagerie SCL=-1. Par exemple :

  - **Pour les services de protection en nuage** : vous pouvez utiliser une valeur d’en-tête et d’en-tête propre à votre organisation. Les messages qui ont l’en-tête ne sont pas analysés Microsoft 365. Les messages sans l’en-tête sont analysés par Microsoft 365
  - **Pour les services ou appareils de protection** locaux : vous pouvez utiliser les adresses IP sources. Les messages provenant des adresses IP sources ne sont pas analysés par Microsoft 365. Les messages qui ne sont pas issus des adresses IP sources sont analysés par Microsoft 365.

- Ne comptez pas exclusivement sur les enregistrements MX pour contrôler si le courrier est filtré. Les expéditeurs peuvent facilement ignorer l’enregistrement MX et envoyer des messages électroniques directement Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>Étape 4 : Configurer le filtrage amélioré pour les connecteurs

La première chose à faire est de configurer le filtrage amélioré pour les [connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (également appelé ignorer la *liste) sur* le connecteur utilisé pour le flux de messagerie de votre service de protection existant vers Microsoft 365. Vous pouvez utiliser le rapport [des messages entrants pour](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) identifier le connecteur.

Le filtrage amélioré pour les connecteurs est requis par Defender Office 365 pour voir d’où les messages Internet sont réellement issus. Le filtrage amélioré pour les connecteurs améliore considérablement la précision de la pile de filtrage Microsoft (en particulier la veille contre l’usurpation d’informations[, ainsi](anti-spoofing-protection.md) que les [](threat-explorer.md) fonctionnalités post-violation dans l’Explorateur de menaces et la réponse & d’investigation [automatisée (AIR)](automated-investigation-response-office.md).

Pour activer correctement le filtrage amélioré pour les connecteurs, vous devez ajouter les adresses **IP** publiques \***\*\***\* de tous les services tiers et/ou hôtes du système de messagerie local qui routent le courrier entrant vers Microsoft 365.

Pour vérifier que le filtrage amélioré des connecteurs fonctionne, vérifiez que les messages entrants contiennent l’un des en-têtes suivants ou les deux :

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>Étape 5 : Créer des stratégies de protection pilote

En créant des stratégies de production, même si elles ne sont pas appliquées à tous les utilisateurs, vous pouvez [](threat-explorer.md) tester les fonctionnalités post-violation telles que l’Explorateur de menaces et tester l’intégration de Defender pour Office 365 dans les processus de votre équipe de réponse à la sécurité.

> [!IMPORTANT]
> Les stratégies peuvent être limitées aux utilisateurs, groupes ou domaines. Nous vous déconseillons de combiner les trois dans une stratégie, car seuls les utilisateurs qui correspondent à ces trois stratégies entreront dans le cadre de la stratégie. Pour les stratégies pilotes, nous vous recommandons d’utiliser des groupes ou des utilisateurs. Pour les stratégies de production, nous vous recommandons d’utiliser des domaines. Il est extrêmement important de comprendre que seul le  domaine de messagerie principal de l’utilisateur détermine si l’utilisateur entre dans l’étendue de la stratégie. Ainsi, si vous basculez l’enregistrement MX pour le domaine secondaire d’un utilisateur, assurez-vous que son domaine principal est également couvert par une stratégie.

### <a name="create-pilot-safe-attachments-policies"></a>Créer des stratégies Coffre pièces jointes pilotes

[Coffre pièces jointes](safe-attachments.md) est la fonctionnalité Defender pour Office 365 la plus simple à activer et à tester avant de changer d’enregistrement MX. Coffre pièces jointes présente les avantages suivants :

- Configuration minimale.
- Probabilité extrêmement faible de faux positifs.
- Comportement similaire à la protection contre les programmes malveillants, qui est toujours en cours et n’est pas affectée par la règle de flux de messagerie SCL=-1.

Créez une stratégie Coffre pièces jointes pour vos utilisateurs pilotes.

Pour les paramètres recommandés, voir [Recommandations Coffre stratégie pièces jointes](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Notez que les recommandations Standard et Strict sont les mêmes. Pour créer la stratégie, voir [Configurer les stratégies Coffre pièces jointes](set-up-safe-attachments-policies.md). N’oubliez pas d’utiliser le groupe **MDOPilotSafeAttachments\_** comme condition de la stratégie (à qui s’applique la stratégie).

> [!IMPORTANT]
> Aujourd’hui, il n’existe aucune stratégie Coffre pièces jointes par défaut. Avant de changer d’enregistrement MX, nous vous recommandons d’avoir une stratégie Coffre pièces jointes qui protège l’ensemble de l’organisation.

### <a name="create-pilot-safe-links-policies"></a>Créer des stratégies de liens Coffre pilote

> [!NOTE]
> Nous ne  prisons pas en charge l’habillage ou la réécriture de liens déjà wrapped ou rewritten. Si votre service de protection actuel encapsule ou réécrit déjà les liens dans les messages électroniques, vous devez désactiver cette fonctionnalité pour vos utilisateurs pilotes. Une façon de s’assurer que cela ne se produit pas consiste à exclure le domaine d’URL de l’autre service dans la stratégie Coffre liens.
>
> Coffre de liens pour les applications Office pris en charge est un paramètre global qui s’applique à tous les utilisateurs sous licence. Vous pouvez l’activer ou le désactiver globalement, et non pour des utilisateurs spécifiques. Pour plus d’informations, voir [Configure Coffre Links protection for Office 365 apps](configure-global-settings-for-safe-links.md#configure-safe-links-protection-for-office-365-apps-in-the-microsoft-365-defender-portal).

Créez une stratégie Coffre liens pour vos utilisateurs pilotes. Les probabilités de faux positifs dans Coffre Liens sont également assez faibles, mais vous devez envisager de tester la fonctionnalité sur un nombre d’utilisateurs pilotes inférieur à celui Coffre pièces jointes. Étant donné que la fonctionnalité a une incidence sur l’expérience utilisateur, vous devez envisager un plan pour former les utilisateurs.

Pour les paramètres recommandés, voir [Paramètres de stratégie Coffre liens recommandés](recommended-settings-for-eop-and-office365.md#safe-links-settings). Notez que les recommandations Standard et Strict sont les mêmes. Pour créer la stratégie, voir [Configurer Coffre de liens](set-up-safe-links-policies.md). N’oubliez pas d’utiliser le groupe **MDOPilotSafeLinks\_** comme condition de la stratégie (à qui s’applique la stratégie).

> [!IMPORTANT]
> Aujourd’hui, il n’existe aucune stratégie Coffre liens par défaut. Avant de changer d’enregistrement MX, nous vous recommandons d’avoir une stratégie Coffre liens qui protège l’ensemble de l’organisation.

### <a name="create-pilot-anti-spam-policies"></a>Créer des stratégies anti-courrier indésirable pilotes

Créez deux stratégies anti-courrier indésirable pour les utilisateurs pilotes :

- Stratégie qui utilise les paramètres Standard. Utilisez le groupe **MDOPilotSpamPhishStandard\_\_** comme condition de la stratégie (à qui s’applique la stratégie).
- Stratégie qui utilise les paramètres Strict. Utilisez le groupe **MDOPilotSpamPhishStrict\_\_** comme condition de la stratégie (à qui s’applique la stratégie). Cette stratégie doit avoir une priorité plus élevée (nombre inférieur) que la stratégie avec les paramètres Standard.

Pour les paramètres standard et strict recommandés, voir [Paramètres de stratégie anti-courrier indésirable recommandés](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). Pour créer les stratégies, voir [Configurer des stratégies anti-courrier indésirable](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Créer des stratégies anti-hameçonnage pilotes

Créez deux stratégies anti-hameçonnage pour les utilisateurs pilotes :

- Stratégie qui utilise les paramètres Standard, à l’exception des actions de détection d’emprunt d’identité comme décrit ci-dessous. Utilisez le groupe **MDOPilotSpamPhishStandard\_\_** comme condition de la stratégie (à qui s’applique la stratégie).
- Stratégie qui utilise les paramètres Strict, à l’exception des actions de détection d’emprunt d’identité comme décrit ci-dessous. Utilisez le groupe **MDOPilotSpamPhishStrict\_\_** comme condition de la stratégie (à qui s’applique la stratégie). Cette stratégie doit avoir une priorité plus élevée (nombre inférieur) que la stratégie avec les paramètres Standard.

Pour les détections d’usurpation d’adresses, l’action standard recommandée est Déplacer le message vers les dossiers Courrier indésirable des **destinataires** et l’action stricte recommandée consiste à mettre le **message en quarantaine**. Utilisez la veille contre l’usurpation d’informations pour observer les résultats. Les remplacements sont expliqués dans la section suivante. Si vous souhaitez en savoir plus, consultez [Informations sur la veille contre l’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md).

Pour les détections d’emprunt d’identité, ignorez les actions standard et stricte recommandées pour les stratégies pilotes. Utilisez plutôt la valeur **Ne pas appliquer d’action** pour les paramètres suivants :

- **Si le message est détecté comme un utilisateur dont l’identité est usurpée**
- **Si le message est détecté comme domaine dont l’identité est usurpée**
- **Si l’intelligence de boîte aux lettres détecte un utilisateur dont l’identité est usurpée**

Utilisez l’aperçu de l’emprunt d’identité pour observer les résultats. Pour plus d’informations, [voir l’aperçu de l’emprunt d’identité dans Defender pour Office 365](impersonation-insight.md).

Vous allez régler la protection contre l’usurpation d’identité (ajuster les autoriser et les blocs) et activer chaque action de protection contre l’usurpation d’identité pour mettre en quarantaine ou déplacer les messages vers le dossier Courrier indésirable (en fonction des recommandations standard ou stricte). Vous pouvez observer les résultats et ajuster leurs paramètres si nécessaire.

Pour plus d’informations, voir les rubriques suivantes :

- [Protection contre l’usurpation d’identité](anti-spoofing-protection.md)
- [Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Configurez des stratégies anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Étape suivante

**Félicitations** ! Vous avez terminé la phase **d’installation** de [votre migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process) !

- Passer à [la phase 3 : Intégration](migrate-to-defender-for-office-365-onboard.md).
