---
title: 'Migrer vers Microsoft Defender pour Office 365 phase 2 : Configuration'
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
- m365solution-mdo-migration
ms.custom: migrationguides
description: Effectuez les étapes nécessaires pour commencer la migration d’un service ou d’un appareil de protection tiers vers Microsoft Defender pour Office 365 protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 69af51bbd39339b07af8f0832a113184afaf725b
ms.sourcegitcommit: e8dd5cd434d17af7096d28d467a2b3b021cbb233
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2022
ms.locfileid: "67051687"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-2-setup"></a>Migrer vers Microsoft Defender pour Office 365 - Phase 2 : Configuration

**S’applique à :**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

<br>

|[![Phase 1 : Préparer.](../../media/phase-diagrams/prepare.png#lightbox)](migrate-to-defender-for-office-365-prepare.md) <br> [Phase 1 : préparation](migrate-to-defender-for-office-365-prepare.md)|![Phase 2 : Configurer.](../../media/phase-diagrams/setup.png) <br> Phase 2 : configuration|[![Phase 3 : Intégration.](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Phase 3 : intégration](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
||*Vous êtes là !*||

Bienvenue dans **la phase 2 : Configuration** de votre **[migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process)** ! Cette phase de migration comprend les étapes suivantes :

1. [Créer des groupes de distribution pour les utilisateurs pilotes](#step-1-create-distribution-groups-for-pilot-users)
2. [Configurer la soumission d’utilisateurs pour la création de rapports de messages utilisateur](#step-2-configure-user-submission-for-user-message-reporting)
3. [Gérer ou créer la règle de flux de messagerie SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule)
4. [Configurer le filtrage amélioré pour les connecteurs](#step-4-configure-enhanced-filtering-for-connectors)
5. [Créer des stratégies de protection pilote](#step-5-create-pilot-protection-policies)

## <a name="step-1-create-distribution-groups-for-pilot-users"></a>Étape 1 : Créer des groupes de distribution pour les utilisateurs pilotes

Les groupes de distribution sont requis dans Microsoft 365 pour les aspects suivants de votre migration :

- **Exceptions pour la règle de flux de messagerie SCL=-1** : vous souhaitez que les utilisateurs pilotes obtiennent l’effet complet de la protection Defender pour Office 365. Vous avez donc besoin que leurs messages entrants soient analysés par Defender pour Office 365. Pour ce faire, vous définissez vos utilisateurs pilotes dans les groupes de distribution appropriés dans Microsoft 365 et configurez ces groupes en tant qu’exceptions à la règle de flux de messagerie SCL=-1.

  Comme nous l’avons décrit à [l’étape 2 d’intégration : (facultatif) Exemptez les utilisateurs pilotes du filtrage par votre service de protection existant](migrate-to-defender-for-office-365-onboard.md#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service), vous devez envisager d’exempter ces mêmes utilisateurs pilotes de l’analyse par votre service de protection existant. Éliminer la possibilité de filtrage par votre service de protection existant et de s’appuyer exclusivement sur Defender pour Office 365 est la meilleure et la plus proche représentation de ce qui va se passer une fois votre migration terminée.

- **Test de fonctionnalités de protection Defender pour Office 365 spécifiques** : même pour les utilisateurs pilotes, vous ne souhaitez pas tout activer en même temps. L’utilisation d’une approche intermédiaire pour les fonctionnalités de protection qui sont en vigueur pour vos utilisateurs pilotes facilitera considérablement la résolution des problèmes et l’ajustement. Avec cette approche à l’esprit, nous recommandons les groupes de distribution suivants :
  - **Groupe pilote Pièces jointes sécurisées** : Par exemple, **MDOPilot\_SafeAttachments**
  - **Un groupe pilote Safe Links** : Par exemple, **MDOPilot\_SafeLinks**
  - **Groupe pilote pour les paramètres de stratégie anti-courrier indésirable et anti-hameçonnage Standard** : Par exemple, **MDOPilot\_SpamPhish\_Standard**
  - **Groupe pilote pour les paramètres de stratégie anti-courrier indésirable et anti-hameçonnage stricts** : Par exemple, **MDOPilot\_SpamPhish\_Strict**

Pour plus de clarté, nous allons utiliser ces noms de groupes spécifiques tout au long de cet article, mais vous êtes libre d’utiliser votre propre convention d’affectation de noms.

Lorsque vous êtes prêt à commencer le test, ajoutez ces groupes en tant qu’exceptions à [la règle de flux de messagerie SCL=-1](#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Lorsque vous créez des stratégies pour les différentes fonctionnalités de protection dans Defender pour Office 365, vous allez utiliser ces groupes comme conditions qui définissent à qui la stratégie s’applique.

**Remarques** :

- Les termes Standard et Strict proviennent de nos [paramètres de sécurité recommandés](recommended-settings-for-eop-and-office365.md), qui sont également utilisés dans les [stratégies de sécurité prédéfinies](preset-security-policies.md). Dans l’idéal, nous vous conseillons de définir vos utilisateurs pilotes dans les stratégies de sécurité prédéfinies Standard et Strict, mais nous ne pouvons pas le faire. Pourquoi ? Étant donné que vous ne pouvez pas personnaliser les paramètres dans les stratégies de sécurité prédéfinies (en particulier, les actions effectuées sur les messages). Lors de vos tests de migration, vous souhaiterez voir ce que Defender pour Office 365 ferait aux messages, vérifier que c’est ce que vous voulez faire et éventuellement ajuster les configurations de stratégie pour autoriser ou empêcher ces résultats.

  Par conséquent, au lieu d’utiliser des stratégies de sécurité prédéfinies, vous allez créer manuellement des stratégies personnalisées avec des paramètres très similaires, mais dans certains cas différents des paramètres des stratégies de sécurité prédéfinies Standard et Strict.

- Si vous souhaitez expérimenter des paramètres qui diffèrent **considérablement** de nos valeurs recommandées Standard ou Strict, vous devez envisager de créer et d’utiliser des groupes de distribution supplémentaires et spécifiques pour les utilisateurs pilotes dans ces scénarios. Vous pouvez utiliser l’analyseur de configuration pour voir à quel point vos paramètres sont sécurisés. Pour obtenir des instructions, consultez [l’analyseur de configuration pour connaître les stratégies de protection dans EOP et Microsoft Defender pour Office 365](configuration-analyzer-for-security-policies.md).

  Pour la plupart des organisations, la meilleure approche consiste à commencer par des stratégies qui s’alignent étroitement avec nos paramètres Standard recommandés. Après avoir reçu autant d’observations et de commentaires que vous pouvez le faire dans votre intervalle de temps disponible, vous pouvez passer à des paramètres plus agressifs ultérieurement. La protection et la remise de l’emprunt d’identité au dossier Junk Email et la remise en quarantaine peuvent nécessiter une personnalisation.

  Si vous utilisez des stratégies personnalisées, assurez-vous qu’elles sont appliquées _avant_ les stratégies qui contiennent nos paramètres recommandés pour la migration. Si un utilisateur est identifié dans plusieurs stratégies du même type (par exemple, anti-hameçonnage), une seule stratégie de ce type est appliquée à l’utilisateur (en fonction de la valeur de priorité de la stratégie). Pour plus d’informations, consultez [Ordre et priorité de la protection par e-mail](how-policies-and-protections-are-combined.md).

## <a name="step-2-configure-user-submission-for-user-message-reporting"></a>Étape 2 : Configurer la soumission d’utilisateurs pour la création de rapports de messages utilisateur

La possibilité pour les utilisateurs d’identifier les faux positifs ou les faux négatifs à partir de Defender pour Office 365 est une partie importante de la migration.

Vous pouvez spécifier une boîte aux lettres Exchange Online pour recevoir des messages que les utilisateurs signalent comme malveillants ou non malveillants. Pour plus d’instructions, consultez [paramètres de message signalés par l’utilisateur](user-submission.md). Cette boîte aux lettres peut recevoir des copies des messages que vos utilisateurs ont envoyés à Microsoft, ou la boîte aux lettres peut intercepter les messages sans les signaler à Microsoft (vous êtes l’équipe de sécurité qui peut analyser et envoyer manuellement les messages). Toutefois, cette approche d’interception ne permet pas au service de régler et d’apprendre automatiquement.

Vous devez également confirmer que tous les utilisateurs du pilote disposent d’une application de création de rapports de messages prise en charge dans Outlook compatible avec la soumission d’utilisateurs. Ces applications sont les suivantes :

- [Complément Message de rapport](enable-the-report-message-add-in.md)
- [Complément Report Phishing](enable-the-report-phish-add-in.md)
- Outils de création de rapports tiers pris en charge, comme décrit [ici](user-submission.md#third-party-reporting-tools-options).

Ne sous-estimez pas l’importance de cette étape. Les données des soumissions d’utilisateurs vous donnent la boucle de commentaires dont vous avez besoin pour vérifier une bonne expérience cohérente de l’utilisateur final avant et après la migration. Ces commentaires vous aident à prendre des décisions éclairées en matière de configuration de stratégie, ainsi qu’à fournir à votre gestion des rapports soutenus par des données indiquant que la migration s’est déroulée sans problème.

Au lieu de s’appuyer sur des données qui sont soutenues par l’expérience de l’ensemble de l’organisation, plusieurs migrations ont entraîné des spéculations émotionnelles basées sur une expérience utilisateur négative unique. En outre, si vous avez exécuté des simulations de hameçonnage, vous pouvez utiliser les commentaires de vos utilisateurs pour vous informer lorsqu’ils voient quelque chose de risqué qui peut nécessiter une enquête.

## <a name="step-3-maintain-or-create-the-scl-1-mail-flow-rule"></a>Étape 3 : Gérer ou créer la règle de flux de messagerie SCL=-1

Étant donné que votre e-mail entrant est acheminé via un autre service de protection qui se trouve devant Microsoft 365, il est très probable que vous ayez déjà une règle de flux de courrier (également appelée règle de transport) dans Exchange Online qui définit le niveau de confiance du courrier indésirable (SCL) de tous les messages entrants sur la valeur -1 (ignorer le filtrage du courrier indésirable). La plupart des services de protection tiers encouragent cette règle de flux de messagerie SCL=-1 pour les clients Microsoft 365 qui souhaitent utiliser leurs services.

Si vous utilisez un autre mécanisme pour remplacer la pile de filtrage Microsoft (par exemple, une liste d’adresses IP autorisées), nous vous recommandons de passer à l’utilisation d’une règle de flux de messagerie SCL=-1 **tant que** tous les messages Internet entrants dans Microsoft 365 proviennent du service de protection tiers (aucun flux de courrier directement à partir d’Internet vers Microsoft 365).

La règle de flux de messagerie SCL=-1 est importante pendant la migration pour les raisons suivantes :

- Vous pouvez utiliser [l’Explorateur de menaces](email-security-in-microsoft-defender.md) pour voir quelles fonctionnalités de la pile Microsoft *auraient* agi sur les messages sans affecter les résultats de votre service de protection existant.
- Vous pouvez ajuster progressivement qui est protégé par la pile de filtrage Microsoft 365 en configurant des exceptions à la règle de flux de messagerie SCL=-1. Les exceptions seront les membres des groupes de distribution pilotes que nous recommandons plus loin dans cet article.

  Avant ou pendant le basculement de votre enregistrement MX vers Microsoft 365, vous désactivez cette règle pour activer la protection complète de la pile de protection Microsoft 365 pour tous les destinataires de votre organisation.

Pour plus d’informations, consultez [Utiliser des règles de flux de courrier pour définir le niveau de confiance du courrier indésirable dans les messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

**Remarques** :

- Si vous envisagez d’autoriser la messagerie Internet à transiter par votre service de protection existant **et** directement dans Microsoft 365 en même temps, vous devez restreindre la règle de flux de courrier SCL=-1 (courrier qui contourne le filtrage du courrier indésirable) aux messages qui sont passés par votre service de protection existant uniquement. Vous ne souhaitez pas que les messages Internet non filtrés arrivent dans les boîtes aux lettres des utilisateurs dans Microsoft 365.

  Pour identifier correctement le courrier qui a déjà été analysé par votre service de protection existant, vous pouvez ajouter une condition à la règle de flux de messagerie SCL=-1. Par exemple :

  - **Pour les services de protection basés sur le cloud** : vous pouvez utiliser un en-tête et une valeur d’en-tête propres à votre organisation. Les messages qui ont l’en-tête ne sont pas analysés par Microsoft 365. Les messages sans en-tête sont analysés par Microsoft 365
  - **Pour les appareils ou services de protection locaux** : vous pouvez utiliser des adresses IP sources. Les messages des adresses IP sources ne sont pas analysés par Microsoft 365. Les messages qui ne proviennent pas des adresses IP sources sont analysés par Microsoft 365.

- Ne vous fiez pas exclusivement aux enregistrements MX pour contrôler si le courrier est filtré. Les expéditeurs peuvent facilement ignorer l’enregistrement MX et envoyer des e-mails directement dans Microsoft 365.

## <a name="step-4-configure-enhanced-filtering-for-connectors"></a>Étape 4 : Configurer le filtrage amélioré pour les connecteurs

La première chose à faire est de configurer le [filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (également appelé *liste d’ignorer*) sur le connecteur utilisé pour le flux de messagerie de votre service de protection existant vers Microsoft 365. Vous pouvez utiliser le [rapport des messages entrants](/exchange/monitoring/mail-flow-reports/mfr-inbound-messages-and-outbound-messages-reports) pour identifier le connecteur.

Un filtrage amélioré pour les connecteurs est requis par Defender pour Office 365 pour voir d’où proviennent réellement les messages Internet. Le filtrage amélioré pour les connecteurs améliore considérablement la précision de la pile de filtrage Microsoft (en particulier le [renseignement sur l’usurpation d’identité](anti-spoofing-protection.md), ainsi que les fonctionnalités de post-violation dans [l’Explorateur de menaces](threat-explorer.md) et la [réponse & d’investigation automatisée (AIR).](automated-investigation-response-office.md)

Pour activer correctement le filtrage amélioré pour les connecteurs, vous devez ajouter les adresses IP **publiques** de \*\***tous les\*\*** services tiers et/ou hôtes de système de messagerie locaux qui routent le courrier entrant vers Microsoft 365.

Pour vérifier que le filtrage amélioré pour les connecteurs fonctionne, vérifiez que les messages entrants contiennent un ou les deux en-têtes suivants :

- `X-MS-Exchange-SkipListedInternetSender`
- `X-MS-Exchange-ExternalOriginalInternetSender`

## <a name="step-5-create-pilot-protection-policies"></a>Étape 5 : Créer des stratégies de protection pilote

En créant des stratégies de production, même si elles ne sont pas appliquées à tous les utilisateurs, vous pouvez tester des fonctionnalités post-violation comme [l’Explorateur de menaces](threat-explorer.md) et tester l’intégration de Defender pour Office 365 dans les processus de votre équipe de réponse de sécurité.

> [!IMPORTANT]
> Les stratégies peuvent être étendues aux utilisateurs, aux groupes ou aux domaines. Nous ne recommandons pas de mélanger les trois dans une stratégie, car seuls les utilisateurs qui correspondent aux trois seront inclus dans l’étendue de la stratégie. Pour les stratégies pilotes, nous vous recommandons d’utiliser des groupes ou des utilisateurs. Pour les stratégies de production, nous vous recommandons d’utiliser des domaines. Il est extrêmement important de comprendre que **seul** le domaine de messagerie principal de l’utilisateur détermine si l’utilisateur entre dans l’étendue de la stratégie. Par conséquent, si vous basculez l’enregistrement MX pour le domaine secondaire d’un utilisateur, assurez-vous que son domaine principal est également couvert par une stratégie.

### <a name="create-pilot-safe-attachments-policies"></a>Créer des stratégies de pièces jointes fiables pour le pilote

[Les pièces jointes sécurisées](safe-attachments.md) sont la fonctionnalité de Defender pour Office 365 la plus simple à activer et à tester avant de changer d’enregistrement MX. Les pièces jointes sécurisées offrent les avantages suivants :

- Configuration minimale.
- Très faible probabilité de faux positifs.
- Comportement similaire à la protection anti-programme malveillant, qui est toujours activée et non affectée par la règle de flux de messagerie SCL=-1.

Créez une stratégie de pièces jointes sécurisées pour vos utilisateurs pilotes.

Pour connaître les paramètres recommandés, consultez les [paramètres de stratégie Pièces jointes fiables recommandés](recommended-settings-for-eop-and-office365.md#safe-attachments-policy-settings). Notez que les recommandations Standard et Strict sont les mêmes. Pour créer la stratégie, consultez [Configurer des stratégies de pièces jointes sécurisées](set-up-safe-attachments-policies.md). Veillez à utiliser le groupe **MDOPilot\_SafeAttachments** comme condition de la stratégie (à qui la stratégie s’applique).

> [!NOTE]
> La stratégie de sécurité prédéfinie de **protection intégrée** offre une protection des pièces jointes sécurisées à tous les destinataires qui ne sont pas définis dans les stratégies pièces jointes sécurisées. Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

### <a name="create-pilot-safe-links-policies"></a>Créer des stratégies de liens fiables pilotes

> [!NOTE]
> Nous ne prenons pas en charge l’habillage ou la réécriture de liens déjà encapsulés ou réécrits. Si votre service de protection actuel encapsule ou réécrit déjà des liens dans des messages électroniques, vous devez désactiver cette fonctionnalité pour vos utilisateurs pilotes. Une façon de s’assurer que cela ne se produit pas consiste à exclure le domaine d’URL de l’autre service dans la stratégie Liens fiables.

Créez une stratégie de liens fiables pour vos utilisateurs pilotes. Les chances de faux positifs dans les liens sécurisés sont également assez faibles, mais vous devez envisager de tester la fonctionnalité sur un plus petit nombre d’utilisateurs pilotes que les pièces jointes sécurisées. Étant donné que la fonctionnalité a un impact sur l’expérience utilisateur, vous devez envisager un plan d’éducation des utilisateurs.

Pour connaître les paramètres recommandés, consultez les [paramètres de stratégie Liens fiables recommandés](recommended-settings-for-eop-and-office365.md#safe-links-settings). Notez que les recommandations Standard et Strict sont les mêmes. Pour créer la stratégie, consultez [Configurer des stratégies liens sécurisés](set-up-safe-links-policies.md). Veillez à utiliser le groupe **MDOPilot\_SafeLinks** comme condition de la stratégie (à qui la stratégie s’applique).

> [!NOTE]
> La **stratégie de sécurité** prédéfinie de protection intégrée offre une protection des liens sécurisés à tous les destinataires qui ne sont pas définis dans les stratégies liens sécurisés. Pour plus d’informations, consultez [Stratégies de sécurité prédéfinies dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md).

### <a name="create-pilot-anti-spam-policies"></a>Créer des stratégies pilotes anti-courrier indésirable

Créez deux stratégies anti-courrier indésirable pour les utilisateurs pilotes :

- Stratégie qui utilise les paramètres Standard. Utilisez le groupe **MDOPilot\_SpamPhish\_Standard** comme condition de la stratégie (à qui la stratégie s’applique).
- Stratégie qui utilise les paramètres stricts. Utilisez le groupe **MDOPilot\_SpamPhish\_Strict** comme condition de la stratégie (à qui la stratégie s’applique). Cette stratégie doit avoir une priorité plus élevée (nombre inférieur) que la stratégie avec les paramètres Standard.

Pour connaître les paramètres Standard et Strict recommandés, consultez [les paramètres de stratégie anti-courrier indésirable recommandés](recommended-settings-for-eop-and-office365.md#eop-anti-spam-policy-settings). Pour créer les stratégies, consultez Configurer les stratégies [anti-courrier indésirable](configure-your-spam-filter-policies.md).

### <a name="create-pilot-anti-phishing-policies"></a>Créer des stratégies pilotes anti-hameçonnage

Créez deux stratégies anti-hameçonnage pour les utilisateurs pilotes :

- Stratégie qui utilise les paramètres Standard, à l’exception des actions de détection d’emprunt d’identité, comme décrit ci-dessous. Utilisez le groupe **MDOPilot\_SpamPhish\_Standard** comme condition de la stratégie (à qui la stratégie s’applique).
- Stratégie qui utilise les paramètres Strict, à l’exception des actions de détection d’emprunt d’identité comme décrit ci-dessous. Utilisez le groupe **MDOPilot\_SpamPhish\_Strict** comme condition de la stratégie (à qui la stratégie s’applique). Cette stratégie doit avoir une priorité plus élevée (nombre inférieur) que la stratégie avec les paramètres Standard.

Pour les détections d’usurpation d’identité, l’action Standard recommandée est **Déplacer le message vers les dossiers Junk Email des destinataires**, et l’action stricte recommandée est **Mettre le message en quarantaine**. Utilisez l’insight d’intelligence de l’usurpation d’identité pour observer les résultats. Les remplacements sont expliqués dans la section suivante. Si vous souhaitez en savoir plus, consultez [Informations sur la veille contre l’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md).

Pour les détections d’emprunt d’identité, ignorez les actions standard et strictes recommandées pour les stratégies pilotes. Utilisez plutôt la valeur **Ne pas appliquer d’action** pour les paramètres suivants :

- **Si le message est détecté en tant qu’utilisateur emprunt d’identité**
- **Si le message est détecté comme domaine emprunté**
- **Si l’intelligence de boîte aux lettres détecte un utilisateur emprunt d’identité**

Utilisez l’insight d’emprunt d’identité pour observer les résultats. Pour plus d’informations, consultez [l’insight sur l’emprunt d’identité dans Defender pour Office 365](impersonation-insight.md).

Vous allez paramétrer la protection contre l’usurpation d’identité (ajuster les autorisations et les blocs) et activer chaque action de protection d’emprunt d’identité pour mettre en quarantaine ou déplacer les messages vers le dossier Junk Email (en fonction des recommandations Standard ou Strict). Vous pouvez observer les résultats et ajuster leurs paramètres si nécessaire.

Pour plus d’informations, voir les rubriques suivantes :

- [Protection contre l’usurpation d’identité](anti-spoofing-protection.md)
- [Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Configurez des stratégies anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase **d’installation** de votre [migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process) !

- Passez à la [phase 3 : Intégration](migrate-to-defender-for-office-365-onboard.md).
