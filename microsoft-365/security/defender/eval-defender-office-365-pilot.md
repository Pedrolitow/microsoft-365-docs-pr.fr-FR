---
title: Pilotez Microsoft Defender pour Office 365, utilisez l’évaluation dans votre environnement de production
description: Étapes de pilote de votre évaluation avec des groupes d’utilisateurs actifs et existants afin de tester correctement les fonctionnalités de Microsoft Defender pour Office 365.
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.service: microsoft-365-security
ms.subservice: m365d
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.date: 05/25/2021
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security
- m365solution-scenario
- m365solution-evalutatemtp
- zerotrust-solution
- highpri
- tier1
ms.custom: admindeeplinkEXCHANGE
ms.topic: how-to
ms.openlocfilehash: cb1f96b5882f1f0554200053c6032c2649c60e35
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68064341"
---
# <a name="pilot-microsoft-defender-for-office-365"></a>Microsoft Defender pour Office 365 pilote

**S’applique à :**
- Microsoft 365 Defender

Cet article est [l’étape 3 sur 3](eval-defender-office-365-overview.md) du processus de configuration de l’environnement d’évaluation pour Microsoft Defender pour Office 365. Pour plus d’informations sur ce processus, consultez [l’article de présentation](eval-defender-office-365-overview.md).

Utilisez les étapes suivantes pour configurer et configurer le pilote pour Microsoft Defender pour Office 365.

:::image type="content" source="../../media/defender/m365-defender-office-pilot.png" alt-text="Étapes de création du pilote dans le portail Microsoft Defender pour Office 365." lightbox="../../media/defender/m365-defender-office-pilot.png":::

- [Étape 1 : Créer des groupes pilotes](#step-1-create-pilot-groups)
- [Étape 2 : Configurer la protection](#step-2-configure-protection)
- [Étape 3 : Tester les fonctionnalités : familiarisez-vous avec la simulation, la surveillance et les métriques](#step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics)

Lorsque vous évaluez Microsoft Defender pour Office 365, vous pouvez choisir de piloter des utilisateurs spécifiques avant d’activer et d’appliquer des stratégies pour l’ensemble de votre organisation. La création de groupes de distribution peut aider à gérer les processus de déploiement. Par exemple, créez des groupes tels que *Defender pour Office 365 Utilisateurs - Protection standard*, *Defender pour Office 365 Utilisateurs - Protection stricte*, *utilisateurs Defender pour Office 365 - Protection personnalisée* ou *Defender pour Office 365 utilisateurs - Exceptions*.

Il n’est peut-être pas évident de savoir pourquoi « Standard » et « Strict » sont les termes utilisés pour ces groupes, mais cela deviendra évident lorsque vous explorerez plus en détail Defender pour Office 365 préréglages de sécurité. Les groupes d’affectation de noms « personnalisés » et « exceptions » parlent d’eux-mêmes, et même si la plupart de vos utilisateurs doivent être soumis à des groupes *standard* et *stricts*, personnalisés et d’exceptions collecteront des données précieuses pour vous concernant la gestion des risques.

## <a name="step-1-create-pilot-groups"></a>Étape 1 : Créer des groupes pilotes

Les groupes de distribution peuvent être créés et définis directement dans Exchange Online ou synchronisés à partir de Active Directory local.

1. Connectez-vous au Centre de Administration Exchange (EAC) à <https://admin.exchange.microsoft.com> l’aide d’un compte qui a reçu le rôle Administrateur du destinataire ou qui a reçu des autorisations de gestion de groupe déléguées.
2. Accédez aux **groupes** **de destinataires**\>.

   :::image type="content" source="../../media/mdo-eval/1_mdo-eval-pilot.png" alt-text=" Élément de menu Groupes à cliquer." lightbox="../../media/mdo-eval/1_mdo-eval-pilot.png":::

3. Dans la page **Groupes** , sélectionnez ![Ajouter une icône de groupe.](../../media/m365-cc-sc-add-internal-icon.png) **Ajoutez un groupe**.

   :::image type="content" source="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png" alt-text="Option Ajouter un groupe à cliquer." lightbox="../../media/mdo-eval/2_mdo-eval-pilot-add-group.png":::

4. Pour le type de groupe, sélectionnez **Distribution**, puis cliquez sur **Suivant**.

   :::image type="content" source="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png" alt-text=" Section Choisir un type de groupe." lightbox="../../media/mdo-eval/3-mdo-eval-pilot-group-type.png":::

5. Donnez au groupe un **nom** et une **description** facultative, puis cliquez sur Suivant.

   :::image type="content" source="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png" alt-text="Section Configurer les principes de base." lightbox="../../media/mdo-eval/4_mdo-eval-pilot-set-up-basics.png":::

6. Sur les pages restantes, affectez un propriétaire, ajoutez des membres au groupe, définissez l’adresse e-mail, les restrictions de départ et d’autres paramètres.

## <a name="step-2-configure-protection"></a>Étape 2 : Configurer la protection

Certaines fonctionnalités de Defender pour Office 365 sont configurées et activées par défaut, mais les opérations de sécurité peuvent vouloir augmenter le niveau de protection par rapport à la valeur par défaut.

Certaines fonctionnalités *ne sont pas encore* configurées. Vous disposez des options suivantes pour configurer la protection :

- **Affecter des utilisateurs à des stratégies de sécurité prédéfinies** : les [stratégies de sécurité prédéfinies](../office-365-security/preset-security-policies.md) sont fournies comme méthode pour affecter rapidement un niveau de protection uniforme à toutes les fonctionnalités. Vous pouvez choisir parmi **la protection Standard** ou **Strict** . L’avantage ici est que vous protégez des groupes d’utilisateurs le plus rapidement possible. Cet inconvénient est que vous ne pouvez pas personnaliser la plupart des paramètres dans les stratégies de sécurité prédéfinies (par exemple, vous ne pouvez pas modifier une action de **Remettre aux dossiers Junk Email des destinataires** en **quarantaine** ou inversement). Gardez également à l’esprit que les stratégies de sécurité prédéfinies sont *toujours* appliquées avant les stratégies personnalisées. Par conséquent, si vous souhaitez créer et utiliser des stratégies personnalisées, vous devez exclure les utilisateurs de ces stratégies personnalisées des stratégies de sécurité prédéfinies.

- **Configurer des stratégies de protection *personnalisées*** : si vous préférez configurer l’environnement vous-même, vous pouvez rapidement obtenir une *base de référence* de protection en suivant les instructions de [Protection contre les menaces](../office-365-security/protect-against-threats.md). Cette approche vous permet d’en savoir plus sur les paramètres configurables. Et vous pourrez affiner les stratégies ultérieurement.

  Vous pouvez également créer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation. Avant de commencer à personnaliser les stratégies, il est important de comprendre la priorité dans laquelle ces stratégies de protection sont appliquées et appliquées. Les opérations de sécurité doivent créer et/ou configurer certaines stratégies, même si la présélection est appliquée.

- **Attribuez automatiquement des stratégies de sécurité prédéfinies** : les [stratégies de sécurité prédéfinies sont fournies](../office-365-security/preset-security-policies.md) comme méthode pour affecter rapidement un niveau de protection uniforme à toutes les fonctionnalités. Vous pouvez choisir **_parmi Standard_*_ ou _*_Strict_**. Une bonne approche consiste à commencer par des stratégies de sécurité prédéfinies, puis à affiner les stratégies à mesure que vous en apprendrez davantage sur les fonctionnalités et votre propre environnement de menace unique. L’avantage ici est que vous protégez des groupes d’utilisateurs le plus rapidement possible, avec la possibilité d’ajuster la protection par la suite. (Cette méthode est recommandée.)
- **Configurer manuellement la protection de base** de référence : si vous préférez configurer l’environnement vous-même, vous pouvez rapidement obtenir une *base de référence* de protection en suivant les instructions de [Protection contre les menaces](../office-365-security/protect-against-threats.md). Cette approche vous permet d’en savoir plus sur les paramètres configurables. Et vous pourrez affiner les stratégies ultérieurement.
- **Configurer des stratégies de protection *personnalisées*** : vous pouvez également générer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation. Avant de commencer à personnaliser les stratégies, il est important de comprendre la priorité dans laquelle ces stratégies de protection sont appliquées et appliquées. Les opérations de sécurité doivent créer des stratégies même si la présélection est appliquée, en particulier pour définir des stratégies de sécurité pour les liens sécurisés et les pièces jointes sécurisées.

> [!IMPORTANT]
> **Si vous devez configurer des stratégies de protection personnalisées**, vous devez examiner les valeurs qui composent les définitions de sécurité **Standard** et **Strict** ici : [Paramètres recommandés pour EOP et Microsoft Defender pour Office 365 sécurité](../office-365-security/recommended-settings-for-eop-and-office365.md). Les valeurs par défaut, comme indiqué avant toute configuration, sont également répertoriées. Conservez une feuille de calcul de l’endroit où votre build personnalisée dévie.

### <a name="assign-preset-security-policies"></a>Affecter des stratégies de sécurité prédéfinies

Nous vous recommandons de commencer par les *stratégies de référence recommandées* lors de l’évaluation de MDO, puis de les affiner en fonction des besoins au cours de votre période d’évaluation.

Vous pouvez activer des stratégies de sécurité prédéfinies dans EOP et Defender pour Office 365 rapidement, et les affecter à des utilisateurs pilotes spécifiques ou à des groupes définis dans le cadre de votre évaluation. Les stratégies prédéfinies offrent un modèle de protection **Standard** de base ou un modèle de protection **strict** plus agressif, qui peut être attribué indépendamment.

Par exemple, une condition EOP pour les évaluations pilotes peut être appliquée si les destinataires sont *membres* d’un groupe *EOP Standard Protection* défini, puis gérés en ajoutant des comptes au groupe ou en supprimant le compte.

De même, une condition de Defender pour Office 365 pour les évaluations pilotes peut être appliquée si les destinataires sont *membres* d’un *groupe de protection standard Defender pour Office 365* défini, puis gérés en ajoutant/supprimant des comptes via le groupe.

Pour obtenir des instructions complètes, consultez [le portail Microsoft 365 Defender pour affecter des stratégies de sécurité prédéfinies Standard et Strict aux utilisateurs](../office-365-security/preset-security-policies.md#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

### <a name="configure-custom-protection-policies"></a>Configurer des stratégies de protection personnalisées

Les modèles de stratégie *Standard* ou *Strict* Defender pour Office 365 prédéfinis offrent à vos utilisateurs pilotes la protection de référence recommandée. Toutefois, vous pouvez également générer et affecter des stratégies de protection personnalisées dans le cadre de votre évaluation.

Il est *important* de connaître la priorité de ces stratégies de protection lorsqu’elles sont appliquées et appliquées, comme expliqué dans [l’ordre et la précédence de la protection par e-mail : Office 365](../office-365-security/how-policies-and-protections-are-combined.md) et [Ordre de priorité pour les stratégies de sécurité prédéfinies et d’autres stratégies](../office-365-security/preset-security-policies.md#order-of-precedence-for-preset-security-policies-and-other-policies).

Le tableau ci-dessous fournit des références et des conseils supplémentaires pour configurer et affecter des stratégies de protection personnalisées :

|Stratégie|Description|Inclus dans la présélection<br>stratégies de sécurité ?|Stratégie par défaut<br>Disponible?|Référence|
|---|---|:---:|:---:|---|
|Stratégies de filtre de connexion|Identifiez les serveurs de courrier source corrects ou incorrects par adresse IP.|Non|Oui|[Configurer la stratégie de filtre de connexion par défaut dans EOP](../office-365-security/configure-the-connection-filter-policy.md)|
|Stratégies de filtrage du courrier indésirable sortant|Spécifiez les limites de débit des messages sortants et contrôlez le transfert de courrier externe.|Non|Oui|[Configurer le filtrage du courrier indésirable sortant dans EOP](../office-365-security/configure-the-outbound-spam-policy.md)|
|Stratégies anti-programme malveillant|Protégez les utilisateurs contre les programmes malveillants par e-mail, notamment les actions à entreprendre et les personnes à notifier si des programmes malveillants sont détectés.|Oui|Oui|[Configurer des stratégies anti-programme malveillant dans EOP](../office-365-security/configure-anti-malware-policies.md)|
|Stratégies anti-courrier indésirable|Protégez les utilisateurs contre le courrier indésirable, y compris les actions à prendre si le courrier indésirable est détecté.|Oui|Oui|[Configurer des stratégies anti-courrier indésirable dans Defender pour Office 365](../office-365-security/configure-your-spam-filter-policies.md)|
|Protection contre l’usurpation d’identité|Protégez les utilisateurs contre les tentatives d’usurpation d’identité à l’aide d’informations d’usurpation d’identité et d’usurpation d’identité.|Oui|Oui|[Configurer l’intelligence par usurpation d’identité dans Defender pour Office 365](../office-365-security/learn-about-spoof-intelligence.md) <br><br> [Configurer des stratégies anti-hameçonnage dans EOP](../office-365-security/configure-anti-phishing-policies-eop.md)|
|Protection de l’emprunt d’identité|Protéger les utilisateurs contre les attaques par hameçonnage et configurer des conseils de sécurité sur les messages suspects|Oui, mais une certaine configuration est requise.|Oui, mais une certaine configuration est requise.|[Paramètres d’emprunt d’identité dans les stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](../office-365-security/set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365) <br><br> [Insight sur l’emprunt d’identité dans Defender pour Office 365](../office-365-security/impersonation-insight.md) <br><br> [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](../office-365-security/configure-mdo-anti-phishing-policies.md)|
|Stratégies de pièces jointes fiables|Protégez les utilisateurs contre les contenus malveillants dans les pièces jointes et les fichiers de messagerie dans SharePoint, OneDrive et Teams.|Oui|Efficacement, par le biais de la protection intégrée|[Configurer des stratégies de pièce jointe sécurisée dans Defender pour Office 365](../office-365-security/set-up-safe-attachments-policies.md)|
|Stratégies de liens fiables|Protégez les utilisateurs de l’ouverture et du partage de liens malveillants dans les messages électroniques ou les applications Office prises en charge.|Oui|Efficacement, par le biais de la protection intégrée|[Configurer les stratégies de la fonctionnalité Liens fiables dans Defender pour Office 365](../office-365-security/set-up-safe-links-policies.md)|

## <a name="step-3-try-out-capabilities-and-get-familiar-with-simulation-monitoring-and-metrics"></a>Étape 3 : Tester les fonctionnalités et se familiariser avec la simulation, la supervision et les métriques

Maintenant que votre pilote est configuré et configuré, il est utile de se familiariser avec les outils de création de rapports, de surveillance et de simulation d’attaque qui sont propres à Microsoft Defender pour Microsoft 365.

|Fonctionnalité|Description|Plus d’informations|
|---|---|---|
|Threat Explorer|L’Explorateur des menaces est un outil puissant en quasi-temps réel qui permet aux équipes des opérations de sécurité d’examiner et de répondre aux menaces et d’afficher des informations sur les programmes malveillants suspects et les hameçonnages dans les e-mails et les fichiers dans Office 365, ainsi que d’autres menaces et risques de sécurité pour votre organisation.|[Affichages dans l’Explorateur de menaces et détections en temps réel](../office-365-security/threat-explorer-views.md)|
|Formation à la simulation d'attaque|Vous pouvez utiliser Exercice de simulation d'attaque dans le portail Microsoft 365 Defender pour exécuter des scénarios d’attaque réalistes au sein de votre organisation, qui vous aident à identifier et à trouver des utilisateurs vulnérables avant qu’une attaque réelle n’affecte votre environnement.|[Commencer à utiliser la formation à la simulation d’attaque](../office-365-security/attack-simulation-training-get-started.md)|
|Tableau de bord rapports|Dans le menu de navigation de gauche, cliquez sur Rapports et développez l’en-tête Email & collaboration. Les rapports de collaboration Email & portent sur la détection des tendances de sécurité, dont certaines vous permettront d’agir (par le biais de boutons tels que « Accéder aux soumissions ») et d’autres qui afficheront des tendances. Ces métriques sont générées automatiquement.|[Afficher les rapports de sécurité par e-mail dans le portail Microsoft 365 Defender](../office-365-security/view-email-security-reports.md) <br><br> [Afficher les rapports Defender pour Office 365 dans le portail Microsoft 365 Defender](../office-365-security/view-reports-for-mdo.md)|

## <a name="next-steps"></a>Prochaines étapes

[Évaluer Microsoft Defender pour point de terminaison](eval-defender-endpoint-overview.md)

Revenir à la vue d’ensemble [d’Évaluer Microsoft Defender pour Office 365](eval-defender-office-365-overview.md)

Revenir à la vue d’ensemble de [Evaluate et pilot Microsoft 365 Defender](eval-overview.md)
