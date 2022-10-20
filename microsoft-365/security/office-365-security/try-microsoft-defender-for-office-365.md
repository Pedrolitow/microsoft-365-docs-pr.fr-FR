---
title: Essayez d’évaluer Defender pour Office 365
description: Découvrez comment évaluer et essayer les fonctionnalités de Microsoft Defender pour Office 365 sans affecter votre flux de courrier existant.
keywords: Try, Evaluate, Trial, Evaluation, Defender pour Office 365
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- m365-security
ms.custom: ''
ms.subservice: mdo
ms.service: microsoft-365-security
ROBOTS: ''
ms.openlocfilehash: 297435fbea9e70ba0b23401a17bbb756b638ff4c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68621977"
---
# <a name="try-microsoft-defender-for-office-365"></a>Essayer Microsoft Defender pour Office 365

En tant que client Microsoft 365 existant, les pages **Essais** et **évaluation** du portail <https://security.microsoft.com> Microsoft 365 Defender vous permettent d’essayer les fonctionnalités de Microsoft Defender pour Office 365 Plan 2 avant d’acheter.

Avant d’essayer Defender pour Office 365 plan 2, vous devez vous poser certaines questions clés :

- Dois-je observer passivement ce que Defender pour Office 365 Plan 2 peut faire pour moi (*audit*), ou est-ce que je souhaite que Defender pour Office 365 Plan 2 prenne des mesures directes sur les problèmes qu’il trouve (*bloquer*) ?
- Dans les deux cas, comment puis-je savoir ce que Defender pour Office 365 Plan 2 fait pour moi?
- Combien de temps ai-je avant de prendre la décision de conserver Defender pour Office 365 plan 2 ?

Cet article vous aidera à répondre à ces questions afin de pouvoir essayer Defender pour Office 365 Plan 2 d’une manière qui répond le mieux aux besoins de votre organisation.

Pour obtenir un guide complémentaire sur l’utilisation de votre version d’évaluation, consultez [le playbook Trial : Microsoft Defender pour Office 365](trial-playbook-defender-for-office-365.md).

## <a name="overview-of-defender-for-office-365"></a>Vue d’ensemble de Defender pour Office 365

Defender pour Office 365 aide les organisations à sécuriser leur entreprise en offrant une gamme complète de fonctionnalités. Pour plus d’informations, consultez [Microsoft Defender pour Office 365](defender-for-office-365.md).

Vous pouvez également en savoir plus sur Defender pour Office 365 dans ce [guide interactif](https://aka.ms/MS365D.InteractiveGuide).

![Microsoft Defender pour Office 365 diagramme conceptuel.](../../media/microsoft-defender-for-office-365.png)

Regardez cette courte vidéo pour en savoir plus sur la façon dont vous pouvez faire plus en moins de temps avec Microsoft Defender pour Office 365.

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RWMmIe]

## <a name="how-trials-and-evaluations-work-for-defender-for-office-365"></a>Fonctionnement des essais et des évaluations pour Defender pour Office 365

### <a name="policies"></a>Politiques

Defender pour Office 365 inclut les fonctionnalités de Exchange Online Protection (EOP), qui sont présentes dans toutes les organisations Microsoft 365 avec des boîtes aux lettres Exchange Online et des fonctionnalités exclusives à Defender pour Office 365.

Les fonctionnalités de protection d’EOP et de Defender pour Office 365 sont implémentées à l’aide de stratégies. **Les stratégies qui sont exclusives à Defender pour Office 365 sont créées pour vous en fonction des besoins** :

- [Protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Pièces jointes sécurisées pour les messages électroniques](safe-attachments.md)
- [Liens sécurisés pour les e-mails et Microsoft Teams](safe-links.md)
  - Les liens sécurisés détonent les URL pendant le flux de messagerie. Pour empêcher le détonation d’URL spécifiques, utilisez des entrées d’autorisation pour les URL dans la liste d’autorisations/blocs du locataire. Pour plus d’informations, consultez [Gérer la liste verte/bloquée du locataire](manage-tenant-allow-block-list.md).
  - Les liens sécurisés n’encapsulent pas les liens d’URL dans les corps des messages électroniques.

Votre éligibilité à une évaluation ou à un essai signifie que vous disposez déjà d’EOP. **Aucune stratégie EOP nouvelle ou spéciale n’est créée pour l’évaluation ou la version d’évaluation de Defender pour Office 365 Plan 2**. Les stratégies EOP existantes dans votre organisation Microsoft 365 sont en mesure d’agir sur les messages (par exemple, envoyer des messages au dossier Junk Email ou mettre en quarantaine) :

- [Stratégies anti-programme malveillant](anti-malware-protection.md)
- [Protection anti-courrier indésirable entrante](anti-spam-protection.md)
- [Protection contre l’usurpation d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings)

Les stratégies par défaut pour ces fonctionnalités EOP sont toujours activées, s’appliquent à tous les destinataires et sont toujours appliquées en dernier après toutes les stratégies personnalisées.

### <a name="audit-mode-vs-blocking-mode-for-defender-for-office-365"></a>Mode audit et mode de blocage pour Defender pour Office 365

Voulez-vous que votre expérience Defender pour Office 365 soit active ou passive ? Voici les deux modes que vous pouvez sélectionner :

- **Mode d’audit** : des *stratégies d’évaluation* spéciales sont créées pour l’anti-hameçonnage (qui inclut la protection de l’emprunt d’identité), les pièces jointes sécurisées et les liens fiables. Ces stratégies d’évaluation sont configurées pour *détecter les* menaces uniquement. Defender pour Office 365 détecte les messages dangereux à signaler, mais les messages ne sont pas traités (par exemple, les messages détectés ne sont pas mis en quarantaine). Les paramètres de ces stratégies d’évaluation sont décrits dans la section [Stratégies en mode audit](#policies-in-audit-mode) plus loin dans cet article.

  Le mode Audit permet d’accéder aux rapports personnalisés pour les menaces détectées par Defender pour Office 365 sur la page **mode Évaluation** à l’adresse <https://security.microsoft.com/atpEvaluation>.

- **Mode de blocage** : le modèle Standard pour les [stratégies de sécurité prédéfinies](preset-security-policies.md) est activé et utilisé pour la version d’évaluation, et les utilisateurs que vous spécifiez inclure dans l’essai sont ajoutés à la stratégie de sécurité prédéfinies Standard. Defender pour Office 365 détecte et *prend des mesures sur* *les* messages dangereux (par exemple, les messages détectés sont mis en quarantaine).

  La sélection par défaut et recommandée consiste à étendre ces stratégies Defender pour Office 365 à tous les utilisateurs de l’organisation. Toutefois, pendant ou après la configuration de votre version d’évaluation, vous pouvez modifier l’attribution de stratégie à des utilisateurs, groupes ou domaines de messagerie spécifiques dans le portail Microsoft 365 Defender ou dans [Exchange Online PowerShell](#policy-settings-associated-with-defender-for-office-365-trials).

  Le mode de blocage ne fournit pas de rapports personnalisés pour les menaces détectées par Defender pour Office 365. Au lieu de cela, les informations sont disponibles dans les rapports réguliers et les fonctionnalités d’enquête de Defender pour Office 365 Plan 2.

Un facteur clé en mode audit et en mode de blocage est la façon dont le courrier électronique est remis à votre organisation Microsoft 365 :

- Les messages provenant d’Internet circulent directement dans Microsoft 365, mais votre abonnement actuel n’a que [Exchange Online Protection (EOP)](exchange-online-protection-overview.md) ou [Defender pour Office 365 Plan 1](overview.md#microsoft-defender-for-office-365-plan-1-vs-plan-2-cheat-sheet).

  ![Le courrier électronique transite à partir d’Internet vers Microsoft 365, avec protection contre EOP et/ou Defender pour Office 365 Plan 1.](../../media/mdo-trial-mail-flow.png)

  Dans ces environnements, vous pouvez sélectionner **le mode audit** ou **le mode de blocage**.

- Vous utilisez actuellement un service ou un appareil tiers pour la protection par e-mail de vos boîtes aux lettres Microsoft 365. Le courrier provenant d’Internet transite par le service de protection avant la remise dans votre organisation Microsoft 365. La protection Microsoft 365 est aussi faible que possible (elle n’est jamais complètement désactivée ; par exemple, la protection contre les programmes malveillants est toujours appliquée).

  ![Le courrier électronique circule à partir d’Internet via le service ou l’appareil de protection tiers avant la remise dans Microsoft 365.](../../media/mdo-migration-before.png)

  Dans ces environnements, vous pouvez sélectionner le **mode audit** uniquement. Vous n’avez pas besoin de modifier votre flux de messagerie (enregistrements MX).

### <a name="evaluation-vs-trial-for-defender-for-office-365"></a>Évaluation et essai pour Defender pour Office 365

Quelle est la différence entre une évaluation et une version d’évaluation de Defender pour Office 365 Plan 2 ? Ce n’est pas la même chose ? Eh bien, oui et non. Voici ce que vous devez savoir :

- Si vous n’avez pas encore de licences Defender pour Office 365 Plan 2 (par exemple, EOP autonome, Microsoft 365 E3, Microsoft 365 Business Premium ou Defender pour Office 365 Plan 1), vous pouvez commencer votre version d’évaluation à partir du **Page d’essais de Microsoft 365** ou <https://security.microsoft.com/trialHorizontalHub> page **mode Évaluation** dans <https://security.microsoft.com/atpEvaluation> le portail Microsoft 365 Defender. À l’un ou l’autre emplacement, vous pouvez sélectionner **le mode d’autorisation** (stratégie de sécurité prédéfinies standard) ou le **mode de blocage** (stratégies d’évaluation) comme décrit précédemment.

  Quel que soit l’emplacement que vous utilisez, nous approvisionnons automatiquement les licences d’essai Defender pour Office 365 Plan 2 nécessaires lors de votre inscription. Les étapes manuelles ou externes pour obtenir et attribuer des licences Plan 2 dans le Centre d'administration Microsoft 365 ne sont plus nécessaires. Les licences d’évaluation sont valables pendant 90 jours :

  - Pour les organisations sans Defender pour Office 365 (par exemple, EOP autonome ou Microsoft 365 E3), les fonctionnalités (en particulier les stratégies) de Defender pour Office 365 sont disponibles pendant la période d’essai.

  - Les organisations avec Defender pour Office 365 Plan 1 (par exemple, des abonnements Microsoft 365 Business Premium ou des modules complémentaires) ont exactement les mêmes stratégies que les organisations avec Defender pour Office 365  Plan 2 (protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage, stratégies de pièces jointes sécurisées et stratégies de liens fiables). Les stratégies de sécurité du **mode d’autorisation (stratégie** de sécurité prédéfinie standard) ou du **mode de blocage** (stratégies d’évaluation) n’expirent pas ou n’arrêtent pas de fonctionner après 90 jours. Ce qui se termine après 90 jours pour ces organisations sont les [fonctionnalités d’automatisation, d’investigation, de correction et d’éducation](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) du Plan 2 qui ne sont pas présentes dans le Plan 1.

- Si vous avez déjà Defender pour Office 365 Plan 2 (par exemple, dans le cadre d’un abonnement Microsoft 365 E5), vous ne verrez jamais **Defender pour Office 365** sur la page **d’essais de Microsoft 365** à l’adresse <https://security.microsoft.com/trialHorizontalHub>. Au lieu de cela, vous démarrez l’évaluation de Defender pour Office 365 Plan sur la page <https://security.microsoft.com/atpEvaluation> **Mode d’évaluation** en **mode d’autorisation (stratégie** de sécurité prédéfinies standard) ou **en mode de blocage** (stratégies d’évaluation).

  Par définition, ces organisations n’ont pas besoin de licences d’essai de Defender pour Office 365 Plan 2, de sorte que leurs évaluations sont illimitées dans la durée.

Les informations de la liste précédente sont résumées dans le tableau suivant :

|Organisation|Modes disponibles|S’inscrire à partir de la<br/>Page d’évaluation ?|S’inscrire à partir de la<br/>Page Essais ?|Évaluation<br/>point|
|---|---|:---:|:---:|---|
|EOP autonome<br/>(aucune boîte aux lettres Exchange Online) <br/><br/> Microsoft 365 E3|Mode Audit <br/> Mode blocage|Oui|Oui|90 jours|
|Microsoft Defender pour Office 365 Plan 1 <br/><br/> Microsoft 365 Business Premium|Mode Audit <br/> Mode blocage|Oui|Oui|Illimité<sup>\*</sup>|
|Microsoft 365 E5|Mode Audit <br/> Mode blocage|Oui|Non|Illimité|

<sup>\*</sup> Les stratégies de sécurité du **mode d’autorisation (stratégie** de sécurité prédéfinie standard) ou du **mode de blocage** (stratégies d’évaluation) n’expirent pas ou n’arrêtent pas de fonctionner après 90 jours. Seules les [fonctionnalités d’automatisation, d’investigation, de correction et d’éducation qui sont exclusives](defender-for-office-365.md#microsoft-defender-for-office-365-plan-1-and-plan-2) à Defender pour Office 365 Plan 2 cessent de fonctionner après 90 jours.

## <a name="set-up-an-evaluation-or-trial-in-audit-mode"></a>Configurer une évaluation ou une version d’évaluation en mode audit

N’oubliez pas que lorsque vous évaluez Defender pour Office 365 en mode audit, des stratégies d’évaluation spéciales sont créées pour Defender pour Office 365 pouvez détecter les menaces. Les paramètres de ces stratégies d’évaluation sont décrits dans la section [Stratégies en mode audit](#policies-in-audit-mode) plus loin dans cet article.

1. Démarrez l’évaluation dans l’un des emplacements disponibles dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>. Par exemple :
   - Dans la bannière en haut de n’importe quelle page de fonctionnalité Defender pour Office 365, cliquez sur **Démarrer l’essai gratuit**.
   - Dans la page **d’essais de Microsoft 365**, <https://security.microsoft.com/trialHorizontalHub>recherchez et sélectionnez **Defender pour Office 365**.
   - Dans la page **Mode d’évaluation** , <https://security.microsoft.com/atpEvaluation>cliquez sur **Démarrer l’évaluation**.

2. Dans la boîte de dialogue **Activer la protection** , sélectionnez **Non, je veux uniquement créer des rapports**, puis cliquez sur **Continuer**.

3. Dans la boîte de dialogue **Sélectionner les utilisateurs que vous souhaitez inclure** , configurez les paramètres suivants :

   - **Tous les utilisateurs** : il s’agit de l’option par défaut et recommandée.
   - **Sélectionner des utilisateurs** : si vous sélectionnez cette option, vous devez sélectionner les destinataires internes auxquels l’évaluation s’applique :
     - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
     - **Groupes** :
       - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
       - Groupes Microsoft 365 spécifiée
       - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

     Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

     For users or groups, you can use most identifiers (name, display name, alias, email address, account name, etc.), but the corresponding display name is shown in the results. For users, enter an asterisk (\*) by itself to see all available values.

   > [!NOTE]
   > Vous pouvez modifier ces sélections après avoir configuré la version d’évaluation, comme décrit dans la section [Gérer votre version d’évaluation](#manage-your-evaluation-or-trial-of-defender-for-office-365) .
   >
   > Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. L’évaluation ou la version d’évaluation est appliquée *uniquement* aux destinataires qui correspondent à *tous les* filtres de destinataires spécifiés. Par exemple, vous configurez une condition avec les valeurs suivantes :
   >
   > - **Utilisateurs** : romain@contoso.com
   > - **Groupes** : Cadres supérieurs
   >
   > L’évaluation ou l’essai est appliqué à romain@contoso.com *uniquement* s’il est également membre du groupe Exécutifs. S’il n’est pas membre du groupe, l’évaluation ou le procès ne lui est pas appliqué.
   >
   > De même, si vous utilisez le même filtre de destinataires comme exception, l’évaluation ou la version d’évaluation n’est pas appliquée à romain@contoso.com *uniquement* s’il est également membre du groupe Executives. S’il n’est pas membre du groupe, l’évaluation ou le procès s’applique toujours à lui.

   Lorsque vous avez terminé, cliquez sur **Continuer**.

4. Dans la boîte de **dialogue Aide-nous à comprendre votre flux de courrier** , configurez les options suivantes :

   - L’une des options suivantes est automatiquement sélectionnée en fonction de notre détection de l’enregistrement MX pour votre domaine :

     - **J’utilise un fournisseur de services tiers et/ou local** : l’enregistrement MX pour vos points de domaine ailleurs que Microsoft 365. Cette sélection nécessite les paramètres supplémentaires suivants après avoir cliqué sur **Suivant** :

       1. Dans la boîte **de dialogue Paramètres tiers ou locaux** , configurez les paramètres suivants :

          - **Sélectionnez un fournisseur de services tiers** : sélectionnez l’une des valeurs suivantes :
            - **Barracuda**
            - **Ironport**
            - **Mimecast**
            - **Proofpoint**
            - **Sophos**
            - **Symantec**
            - **Trend Micro**
            - **Other**

          - **Connecteur auquel appliquer cette évaluation** : Sélectionnez le connecteur utilisé pour le flux de messagerie dans Microsoft 365.

            [Le filtrage amélioré pour les connecteurs](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors) (également appelé *liste d’ignorer*) est automatiquement configuré sur le connecteur que vous spécifiez.

            Lorsqu’un service ou un appareil tiers se trouve devant le courrier électronique qui transite par Microsoft 365, le filtrage amélioré pour connecteurs identifie correctement la source des messages Internet et améliore considérablement la précision de la pile de filtrage Microsoft (en particulier [l’usurpation d’identité](anti-spoofing-protection.md), ainsi que les fonctionnalités de post-violation dans [l’Explorateur de menaces](threat-explorer.md) et la [réponse air & d’investigation automatisée](automated-investigation-response-office.md)).

          - **Répertoriez chaque adresse IP de passerelle transmise par vos messages** : ce paramètre n’est disponible que si vous avez sélectionné **Autre** pour **sélectionner un fournisseur de services tiers**. Entrez une liste séparée par des virgules des adresses IP utilisées par le service ou l’appareil de protection tiers pour envoyer des messages à Microsoft 365.

          Lorsque vous avez terminé, cliquez sur **Suivant**.

       2. Dans la boîte de dialogue **Règles de flux de messagerie Exchange**, déterminez si vous avez besoin d’une règle de flux de messagerie Exchange Online (également appelée règle de transport) qui ignore le filtrage du courrier indésirable pour les messages entrants provenant du service ou de l’appareil de protection tiers.

          Il est probable que vous ayez déjà une règle de flux de messagerie SCL=-1 dans Exchange Online qui permet à tous les messages entrants du service de protection de contourner (la plupart) le filtrage Microsoft 365. De nombreux services de protection encouragent cette méthode de règle de flux de courrier de niveau de confiance du courrier indésirable (SCL) pour les clients Microsoft 365 qui utilisent leurs services.

          Comme expliqué à l’étape précédente, le filtrage amélioré pour les connecteurs est automatiquement configuré sur le connecteur que vous spécifiez comme source de courrier du service de protection.

          L’activation du filtrage amélioré pour les connecteurs sans règle SCL=-1 pour les messages entrants du service de protection améliorera considérablement les fonctionnalités de détection des fonctionnalités de protection EOP, telles que [l’usurpation d’identité](anti-spoofing-protection.md), et pourrait avoir un impact sur la remise de ces messages nouvellement détectés (par exemple, passer au dossier Junk Email ou en quarantaine). Cet impact est limité aux stratégies EOP ; comme expliqué précédemment, Defender pour Office 365 stratégies sont créées en mode audit.

          Pour créer une règle de flux de messagerie SCL=-1 ou pour passer en revue vos règles existantes, cliquez sur le bouton **Accéder au centre d’administration Exchange** sur la page. Pour plus d’informations, consultez [Utiliser des règles de flux de courrier pour définir le niveau de confiance du courrier indésirable dans les messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

          Lorsque vous avez terminé, cliquez sur **Terminer**.

     - **J’utilise uniquement Microsoft Exchange Online** : les enregistrements MX de votre domaine pointent vers Microsoft 365. Il n’y a plus rien à configurer, alors cliquez sur **Terminer**.

   - **Partager des données avec Microsoft** : cette option n’est pas sélectionnée par défaut, mais vous pouvez cocher la case si vous le souhaitez.

5. Une boîte de dialogue de progression s’affiche lors de la configuration de votre évaluation. Une fois la configuration terminée, cliquez sur **Terminé**.

## <a name="set-up-an-evaluation-or-trial-in-blocking-mode"></a>Configurer une évaluation ou une version d’évaluation en mode de blocage

N’oubliez pas que lorsque vous essayez Defender pour Office 365 en mode de blocage, la sécurité prédéfinies Standard est activée et les utilisateurs spécifiés (certains ou tout le monde) sont inclus dans la stratégie de sécurité prédéfinies Standard. Pour plus d’informations sur la stratégie de sécurité prédéfinies Standard, consultez [Stratégies de sécurité prédéfinies](preset-security-policies.md).

1. Démarrez la version d’évaluation dans l’un des emplacements disponibles dans le portail Microsoft 365 Defender à l’adresse <https://security.microsoft.com>. Par exemple :
   - Dans la bannière en haut de n’importe quelle page de fonctionnalité Defender pour Office 365, cliquez sur **Démarrer l’essai gratuit**.
   - Dans la page **d’essais de Microsoft 365**, <https://security.microsoft.com/trialHorizontalHub>recherchez et sélectionnez **Defender pour Office 365**.
   - Dans la page **Mode d’évaluation** , <https://security.microsoft.com/atpEvaluation>cliquez sur **Démarrer l’évaluation**.

2. Dans la boîte de dialogue **Activer la protection** , sélectionnez **Oui, protégez mon organisation en bloquant les menaces**, puis cliquez sur **Continuer**.

3. Dans la boîte de dialogue **Sélectionner les utilisateurs que vous souhaitez inclure** , configurez les paramètres suivants :

   - **Tous les utilisateurs** : il s’agit de l’option par défaut et recommandée.
   - **Sélectionner des utilisateurs** : si vous sélectionnez cette option, vous devez sélectionner les destinataires internes auxquels s’applique la version d’évaluation :
     - **Utilisateurs** : boîtes aux lettres, utilisateurs de messagerie ou contacts de messagerie spécifiés.
     - **Groupes** :
       - Les membres des groupes de distribution ou des groupes de sécurité activés par courrier spécifiés.
       - Groupes Microsoft 365 spécifiée
     - **Domaines** : tous les destinataires des [domaines acceptés](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) spécifiés dans votre organisation.

     Cliquez dans la zone appropriée, commencez à taper une valeur et sélectionnez la valeur souhaitée dans les résultats. Répétez cette opération autant de fois que nécessaire. Pour supprimer une valeur existante, cliquez sur Supprimer ![Icône Supprimer.](../../media/m365-cc-sc-remove-selection-icon.png) en regard de la valeur.

     For users or groups, you can use most identifiers (name, display name, alias, email address, account name, etc.), but the corresponding display name is shown in the results. For users, enter an asterisk (\*) by itself to see all available values.

   > [!NOTE]
   > Vous pouvez modifier ces sélections après avoir configuré la version d’évaluation, comme décrit dans la section [Gérer votre version d’évaluation](#manage-your-evaluation-or-trial-of-defender-for-office-365) .
   >
   > Plusieurs types de conditions ou exceptions différentes ne sont pas cumulatives ; elles sont inclusives. L’évaluation ou la version d’évaluation est appliquée *uniquement* aux destinataires qui correspondent à *tous les* filtres de destinataires spécifiés. Par exemple, vous configurez une condition avec les valeurs suivantes :
   >
   > - **Utilisateurs** : romain@contoso.com
   > - **Groupes** : Cadres supérieurs
   >
   > L’évaluation ou l’essai est appliqué à romain@contoso.com *uniquement* s’il est également membre du groupe Exécutifs. S’il n’est pas membre du groupe, l’évaluation ou le procès ne lui est pas appliqué.
   >
   > De même, si vous utilisez le même filtre de destinataires comme exception, l’évaluation ou la version d’évaluation n’est pas appliquée à romain@contoso.com *uniquement* s’il est également membre du groupe Executives. S’il n’est pas membre du groupe, l’évaluation ou le procès s’applique toujours à lui.

   Lorsque vous avez terminé, cliquez sur **Continuer**.

4. Une boîte de dialogue de progression s’affiche lors de la configuration de votre évaluation. Une fois l’installation terminée, cliquez sur **Terminé**.

## <a name="manage-your-evaluation-or-trial-of-defender-for-office-365"></a>Gérer l’évaluation ou la version d’évaluation de Defender pour Office 365

Une fois que vous avez configuré votre évaluation ou votre version d’évaluation en mode audit ou en mode de blocage, la page **Du mode Évaluation** se trouve à <https://security.microsoft.com/atpEvaluation> l’emplacement central pour plus d’informations sur la tentative d’Defender pour Office 365 plan 2.

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & stratégies de **collaboration** \> **& règles Les stratégies** \> **de menace** \> sélectionnent **le mode Évaluation** dans la section **Autres**. Ou, pour accéder directement à la page **d’évaluation Microsoft Defender pour Office 365**, utilisez <https://security.microsoft.com/atpEvaluation>.

2. Dans la page **d’évaluation Microsoft Defender pour Office 365**, vous pouvez effectuer les tâches suivantes :

   - Cliquez sur **Acheter un abonnement payant** pour acheter Defender pour Office 365 Plan 2.

   - Cliquez sur **Gérer**. Dans le **menu volant d’évaluation Microsoft Defender pour Office 365** qui s’affiche, vous pouvez effectuer les tâches suivantes :

     - Modifiez à qui s’applique l’évaluation ou la version d’évaluation, comme décrit précédemment dans La [configuration d’une évaluation ou d’une version d’évaluation en mode audit](#set-up-an-evaluation-or-trial-in-audit-mode) , et [configurer une évaluation ou un essai en mode de blocage](#set-up-an-evaluation-or-trial-in-blocking-mode).

     - Pour passer du **mode d’audit (stratégies** d’évaluation) au mode de blocage (stratégie de sécurité prédéfinies standard), cliquez sur **Convertir en protection standard**, puis cliquez sur **Continuer** dans la boîte de dialogue qui semble être prise dans l’Assistant **Appliquer la protection standard** dans la page **Stratégies de sécurité prédéfinies** . Les destinataires inclus et exclus existants sont copiés. Pour plus d’informations, consultez [Utiliser le portail Microsoft 365 Defender pour affecter des stratégies de sécurité prédéfinies Standard et Strict aux utilisateurs](preset-security-policies.md#use-the-microsoft-365-defender-portal-to-assign-standard-and-strict-preset-security-policies-to-users).

       **Remarques** :

       - Les stratégies de la stratégie de sécurité prédéfinies Standard ont une priorité plus élevée que les stratégies d’évaluation, ce qui signifie que les stratégies de la sécurité prédéfinies Standard sont toujours appliquées *avant* les stratégies d’évaluation, même si elles sont présentes et activées. Pour désactiver les stratégies d’évaluation, utilisez le bouton **Désactiver** .
       - Il n’existe aucun moyen automatique de passer du **mode de blocage** au **mode audit**. Les étapes manuelles sont les suivantes :
         1. Désactivez la stratégie de sécurité prédéfinies Standard dans la page **Stratégies de sécurité prédéfinies** .
         2. Après avoir cliqué sur **Gérer** dans la page **d’évaluation Microsoft Defender pour Office 365**, vérifiez la présence du bouton **Désactiver**, qui indique que les stratégies d’évaluation sont activées. Si vous voyez le bouton **Activer** , cliquez dessus pour activer les stratégies d’évaluation.
         3. Vérifiez les utilisateurs auxquels l’évaluation s’applique.

     - Pour désactiver les stratégies d’évaluation, cliquez sur **Désactiver**. Pour les réactiver, cliquez sur **Activer**.

     Lorsque vous avez terminé dans le menu volant, cliquez sur **Enregistrer**.

## <a name="reports-for-your-evaluation-or-trial-of-defender-for-office-365"></a>Rapports d’évaluation ou d’essai de Defender pour Office 365

Cette section décrit les rapports disponibles en mode audit et en mode de blocage.

### <a name="reports-for-blocking-mode"></a>Rapports pour le mode de blocage

En **mode de blocage**, les rapports suivants montrent les détections par Defender pour Office 365 :

- Vue [Mailflow pour le rapport d’état mailflow](view-email-security-reports.md#mailflow-view-for-the-mailflow-status-report) :

  - Les messages détectés comme emprunt d’identité d’utilisateur ou emprunt d’identité de domaine par des stratégies anti-hameçonnage apparaissent dans le **bloc d’emprunt d’identité**.
  - Les messages détectés lors de la détonation de fichier ou d’URL par des stratégies de pièces jointes sécurisées ou des stratégies liens fiables apparaissent dans le **bloc de détonation**.

- Rapport [d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) :

  - [Afficher les données par vue d’ensemble](view-email-security-reports.md#view-data-by-overview) :

    Vous pouvez filtrer la plupart des vues par **MDO** **protégé par** valeur pour voir les effets de Defender pour Office 365.

  - [Afficher les données par Email \> phish et la répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--phish-and-chart-breakdown-by-detection-technology)

    - Les messages détectés par [les campagnes](campaigns.md) apparaissent dans **Campaign**.
    - Les messages détectés par les pièces jointes sécurisées apparaissent dans la **réputation de détonation** de fichier et **de détonation de fichier**.
    - Les messages détectés par la protection de l’emprunt d’identité de l’utilisateur dans les stratégies anti-hameçonnage apparaissent dans **le domaine d’emprunt** d’identité, **l’utilisateur d’emprunt d’identité** et l’emprunt d’identité **mailbox intelligence**.
    - Les messages détectés par les liens fiables apparaissent dans la **réputation de détonation d’URL** et **de détonation d’URL**.

  - [Afficher les données par Email \> les programmes malveillants et la répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--malware-and-chart-breakdown-by-detection-technology)

    - Les messages détectés par [les campagnes](campaigns.md) apparaissent dans **Campaign**.
    - Les messages détectés par les pièces jointes sécurisées apparaissent dans la **réputation de détonation** de fichier et **de détonation de fichier**.
    - Les messages détectés par les liens fiables apparaissent dans la **réputation de détonation d’URL** et **de détonation d’URL**.

  - [Afficher les données par Email \> le courrier indésirable et la répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--spam-and-chart-breakdown-by-detection-technology)

    Les messages détectés par les liens fiables apparaissent dans la **réputation malveillante de l’URL**.

  - [Répartition du graphique par type de stratégie](view-email-security-reports.md#chart-breakdown-by-policy-type)

    Les messages détectés par les pièces jointes sécurisées apparaissent dans **les pièces jointes sécurisées**

  - [Afficher les données par programme malveillant de contenu \>](view-email-security-reports.md#view-data-by-content--malware)

    Les fichiers [malveillants détectés par les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](turn-on-mdo-for-spo-odb-and-teams.md) apparaissent dans la **détonation MDO**.

  - Rapport [des principaux expéditeurs et destinataires](view-email-security-reports.md#top-senders-and-recipients-report)

    **Afficher les données des principaux destinataires de programmes malveillants (MDO)** et **afficher les données pour les destinataires de phish supérieurs (MDO).**

  - Rapport [de protection d’URL](view-reports-for-mdo.md#url-protection-report)

### <a name="reports-for-audit-mode"></a>Rapports pour le mode audit

En **mode audit**, les rapports suivants montrent les détections par Defender pour Office 365 :

- Le [rapport d’état de la protection contre les menaces](view-email-security-reports.md#threat-protection-status-report) présente **l’option Évaluation : Oui/Non** en tant que propriété filtrable dans les affichages suivants :
  - [Afficher les données par Email \> phish et la répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--phish-and-chart-breakdown-by-detection-technology)
  - [Afficher les données par Email \> les programmes malveillants et la répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--malware-and-chart-breakdown-by-detection-technology)
  - [Afficher les données par Email \> le courrier indésirable et la répartition des graphiques par technologie de détection](view-email-security-reports.md#view-data-by-email--spam-and-chart-breakdown-by-detection-technology)

- [L’Explorateur de menaces](threat-explorer.md) affiche la bannière suivante dans les détails de détection des messages sous l’onglet **Analyse** de la **pièce jointe incorrecte**, **url de courrier indésirable + programme malveillant**, **URL de hameçonnage** et messages d’emprunt d’identité détectés par l’évaluation Defender pour Office 365 afficher la bannière suivante dans les détails de l’entrée :

  ![Bannière de notification dans les détails du message indiquant que l’évaluation Defender pour Office 365 a détecté un message électronique malveillant.](../../media/evalv2-detection-banner.png)

La **page d’évaluation Microsoft Defender pour Office 365** à <https://security.microsoft.com/atpEvaluation> consolider les rapports pour les stratégies dans l’évaluation :

- Liens sûrs
- Pièces jointes fiables
- Protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage

Par défaut, les graphiques affichent les données des 30 derniers jours, mais vous pouvez filtrer la plage de dates en cliquant sur l’icône ![Calendrier.](../../media/m365-cc-sc-add-internal-icon.png) **30 jours** et sélection parmi les valeurs supplémentaires suivantes inférieures à 30 jours :

- 24 heures
- 7 jours
- 14 jours
- Plage de dates personnalisée

Vous pouvez cliquer sur l’icône ![Télécharger.](../../media/m365-cc-sc-download-icon.png) **Téléchargez** pour télécharger les données du graphique dans un fichier .csv.

## <a name="required-permissions"></a>Autorisations requises

Les autorisations suivantes sont requises dans **Azure AD** pour configurer une évaluation ou un essai de Defender pour Microsoft 365 :

- **Créez, modifiez ou supprimez une évaluation ou une version d’évaluation** : Administrateur de sécurité ou Administrateur général.
- **Affichez les stratégies d’évaluation et les rapports en mode audit** : Administrateur de sécurité ou Lecteur Sécurité.

Pour plus d’informations sur les autorisations Azure AD dans le portail Microsoft 365 Defender, consultez [les rôles Azure AD dans le portail Microsoft 365 Defender](permissions-microsoft-365-security-center.md#azure-ad-roles-in-the-microsoft-365-defender-portal)

## <a name="frequently-asked-questions"></a>Questions fréquemment posées

### <a name="q-do-i-need-to-manually-get-or-activate-trial-licenses"></a>Q : Dois-je obtenir ou activer manuellement des licences d’évaluation ?

R : Non. La version d’évaluation provisionne automatiquement Defender pour Office 365 licences Plan 2 si vous en avez besoin, comme décrit précédemment.

### <a name="q-how-do-i-extend-the-trial"></a>Q : Comment faire prolonger l’essai?

R : Consultez [Étendre votre version d’évaluation](/microsoft-365/commerce/try-or-buy-microsoft-365#extend-your-trial).

### <a name="q-what-happens-to-my-data-after-the-trial-expires"></a>Q : Qu’advient-il de mes données après l’expiration de la version d’évaluation ?

R : Une fois votre version d’évaluation expirée, vous aurez accès à vos données d’évaluation (données des fonctionnalités de Defender pour Office 365 que vous n’ayez pas précédemment) pendant 30 jours. Après cette période de 30 jours, toutes les stratégies et données associées à l’essai Defender pour Office 365 sont supprimées.

### <a name="q-how-many-times-can-i-use-the-defender-for-office-365-trial-in-my-organization"></a>Q : Combien de fois puis-je utiliser la version d’évaluation Defender pour Office 365 dans mon organisation ?

R : Un maximum de 2 fois. Si votre premier essai expire, vous devez attendre au moins 30 jours après la date d’expiration avant de pouvoir vous inscrire à nouveau à l’essai Defender pour Office 365. Après votre deuxième essai, vous ne pouvez pas vous inscrire à une autre version d’évaluation.

### <a name="q-in-audit-mode-are-there-scenarios-where-defender-for-office-365-will-act-on-messages"></a>Q : En mode audit, existe-t-il des scénarios où Defender pour Office 365 agira sur les messages ?

R : Oui. Personne dans un programme ou une référence SKU ne peut désactiver ou contourner l’action sur les messages classés comme programmes malveillants ou hameçonnage à haut niveau de confiance par le service.

En mode audit, la [protection contre l’usurpation d’identité dans EOP](set-up-anti-phishing-policies.md#spoof-settings) prend également des mesures sur les messages. Pour empêcher la protection contre l’usurpation d’identité d’agir sur les messages, créez une règle de flux de messagerie Exchange (également appelée règle de transport) où le courrier entrant contourne tous les types de filtrage qui peuvent être contournés (y compris la protection contre l’usurpation d’identité). Pour obtenir des instructions, consultez [Utiliser des règles de flux de courrier pour définir le niveau de confiance du courrier indésirable dans les messages dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl).

### <a name="q-in-what-order-are-policies-evaluated"></a>Q : Dans quel ordre les stratégies sont-ils évaluées ?

R : Consultez [l’ordre de priorité pour les stratégies de sécurité prédéfinies et d’autres stratégies](preset-security-policies.md#order-of-precedence-for-preset-security-policies-and-other-policies).

## <a name="reference"></a>Référence

### <a name="policy-settings-associated-with-defender-for-office-365-trials"></a>Paramètres de stratégie associés aux essais Defender pour Office 365

#### <a name="policies-in-audit-mode"></a>Stratégies en mode audit

> [!WARNING]
> N’essayez pas de créer, modifier ou supprimer les stratégies de sécurité individuelles associées à l’évaluation de Defender pour Office 365. La seule méthode prise en charge pour créer les stratégies de sécurité individuelles pour l’évaluation consiste à démarrer l’évaluation ou la version d’évaluation en mode audit dans le portail Microsoft 365 Defender pour la première fois.

[Comme décrit précédemment](#audit-mode-vs-blocking-mode-for-defender-for-office-365), lorsque vous choisissez le mode d’audit pour votre évaluation ou votre version d’évaluation, les stratégies d’évaluation avec les paramètres nécessaires pour observer les messages, mais pas pour y prendre des mesures, sont automatiquement créées.

Pour afficher ces stratégies et leurs paramètres, exécutez la commande suivante dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) :

```powershell
Write-Output -InputObject ("`r`n"*3),"Evaluation anti-phishing policy",("-"*79);Get-AntiPhishPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Evaluation"; Write-Output -InputObject ("`r`n"*3),"Evaluation Safe Attachments policy",("-"*79);Get-SafeAttachmentPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Evaluation"; Write-Output -InputObject ("`r`n"*3),"Evaluation Safe Links policy",("-"*79);Get-SafeLinksPolicy | Where-Object -Property RecommendedPolicyType -eq -Value "Evaluation"
```

Les paramètres sont également décrits dans les tableaux suivants.

##### <a name="anti-phishing-evaluation-policy-settings"></a>Paramètres de stratégie d’évaluation anti-hameçonnage

|Paramètre|Valeur|
|---|---|
|Nom|Stratégie d’évaluation|
|AdminDisplayName|Stratégie d’évaluation|
|AuthenticationFailAction|MoveToJmf|
|Activé|Vrai|
|EnableFirstContactSafetyTips|Faux|
|EnableMailboxIntelligence|Vrai|
|EnableMailboxIntelligenceProtection|Vrai|
|EnableOrganizationDomainsProtection|Faux|
|EnableSimilarDomainsSafetyTips|Faux|
|EnableSimilarUsersSafetyTips|Faux|
|EnableSpoofIntelligence|Vrai|
|EnableSuspiciousSafetyTip|Faux|
|EnableTargetedDomainsProtection|Faux|
|EnableTargetedUserProtection|Faux|
|EnableUnauthenticatedSender|Vrai|
|EnableUnusualCharactersSafetyTips|Faux|
|EnableViaTag|Vrai|
|ExcludedDomains|{}|
|ExcludedSenders|{}|
|ImpersonationProtectionState|Manual|
|IsDefault|Faux|
|MailboxIntelligenceProtectionAction|NoAction|
|MailboxIntelligenceProtectionActionRecipients|{}|
|MailboxIntelligenceQuarantineTag|DefaultFullAccessPolicy|
|PhishThresholdLevel|1|
|PolicyTag|Blanc|
|RecommendedPolicyType|Évaluation|
|SpoofQuarantineTag|DefaultFullAccessPolicy|
|TargetedDomainActionRecipients|{}|
|TargetedDomainProtectionAction|NoAction|
|TargetedDomainQuarantineTag|DefaultFullAccessPolicy|
|TargetedDomainsToProtect|{}|
|TargetedUserActionRecipients|{}|
|TargetedUserProtectionAction|NoAction|
|TargetedUserQuarantineTag|DefaultFullAccessPolicy|
|TargetedUsersToProtect|{}|

##### <a name="safe-attachments-evaluation-policy-settings"></a>Paramètres de stratégie d’évaluation des pièces jointes sécurisées

|Paramètre|Valeur|
|---|---|
|Nom|Stratégie d’évaluation|
|Action|Autoriser|
|ActionOnError|Vrai|
|AdminDisplayName|Stratégie d’évaluation|
|ConfidenceLevelThreshold|80|
|Activer|Vrai|
|EnableOrganizationBranding|Faux|
|IsBuiltInProtection|Faux|
|IsDefault|Faux|
|OperationMode|Delay|
|QuarantineTag|AdminOnlyAccessPolicy|
|RecommendedPolicyType|Évaluation|
|Rediriger|Faux|
|RedirectAddress|Blanc|
|ScanTimeout|30|

##### <a name="safe-links-evaluation-policy-settings"></a>Paramètres de stratégie d’évaluation des liens fiables

|Paramètre|Valeur|
|---|---|
|Nom|Stratégie d’évaluation|
|AdminDisplayName|Stratégie d’évaluation|
|AllowClickThrough|Vrai|
|CustomNotificationText|Blanc|
|DeliverMessageAfterScan|Vrai|
|DisableUrlRewrite|Vrai|
|DoNotRewriteUrls|{}|
|EnableForInternalSenders|Faux|
|EnableOrganizationBranding|Faux|
|EnableSafeLinksForEmail|Vrai|
|EnableSafeLinksForOffice|Faux|
|EnableSafeLinksForTeams|Faux|
|IsBuiltInProtection|Faux|
|LocalizedNotificationTextList|{}|
|RecommendedPolicyType|Évaluation|
|ScanUrls|Vrai|
|TrackClicks|Vrai|

##### <a name="use-powershell-to-configure-recipient-conditions-and-exceptions-to-the-evaluation-in-audit-mode"></a>Utiliser PowerShell pour configurer les conditions de destinataire et les exceptions à l’évaluation en mode audit

Une règle associée aux stratégies d’évaluation Defender pour Office 365 contrôle les conditions du destinataire et les exceptions à l’évaluation.

Pour afficher la règle associée à l’évaluation, exécutez la commande suivante dans Exchange Online PowerShell :

```powershell
Get-ATPEvaluationRule
```

Pour utiliser Exchange Online PowerShell pour modifier à qui l’évaluation s’applique, utilisez la syntaxe suivante :

```powershell
Set-ATPEvaluationRule -Identity "Evaluation Rule" -SentTo <"user1","user2",... | $null> -ExceptIfSentTo <"user1","user2",... | $null> -SentToMemberOf <"group1","group2",... | $null> -ExceptIfSentToMemberOf <"group1","group2",... | $null> -RecipientDomainIs <"domain1","domain2",... | $null> -ExceptIfRecipientDomainIs <"domain1","domain2",... | $null>
```

Cet exemple configure les exceptions de l’évaluation pour les boîtes aux lettres d’opérations de sécurité (SecOps) spécifiées.

```powershell
Set-ATPEvaluationRule -Identity "Evaluation Rule" -ExceptIfSentTo "SecOps1","SecOps2"
```

##### <a name="use-powershell-to-turn-on-or-turn-off-the-evaluation-in-audit-mode"></a>Utiliser PowerShell pour activer ou désactiver l’évaluation en mode audit

Pour activer ou désactiver l’évaluation en mode audit, vous activez ou désactivez la règle associée à l’évaluation. La valeur de propriété State de la règle d’évaluation indique si la règle est activée ou désactivée.

Exécutez la commande suivante pour déterminer si l’évaluation est actuellement activée ou désactivée :

```powershell
Get-ATPEvaluationRule -Identity "Evaluation Rule" | Format-Table Name,State
```

Exécutez la commande suivante pour désactiver l’évaluation si elle est activée :

```powershell
Disable-ATPEvaluationRule -Identity "Evaluation Rule"
```

Exécutez la commande suivante pour activer l’évaluation si elle est désactivée :

```powershell
Enable-ATPEvaluationRule -Identity "Evaluation Rule"
```

#### <a name="policies-and-rules-in-block-mode"></a>Stratégies et règles en mode bloc

[Comme décrit précédemment](#audit-mode-vs-blocking-mode-for-defender-for-office-365), lorsque vous choisissez le mode de blocage pour votre version d’évaluation, les stratégies sont créées à l’aide du modèle Standard pour les [stratégies de sécurité prédéfinies](preset-security-policies.md).

Pour utiliser Exchange Online PowerShell afin d’afficher les stratégies de sécurité individuelles associées à la stratégie de sécurité prédéfinies standard et d’utiliser Exchange Online PowerShell pour afficher et configurer les conditions de destinataire et les exceptions pour la stratégie de sécurité prédéfinies, consultez [Les stratégies de sécurité prédéfinies dans Exchange Online PowerShell](preset-security-policies.md#preset-security-policies-in-exchange-online-powershell).
