---
title: Prise en main de la conformité des communications
description: Configurez des stratégies de conformité des communications pour configurer les communications utilisateur à réviser.
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
- highpri
- tier1
- purview-compliance
- m365solution-insiderrisk
- m365initiative-compliance
- highpri
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: c837bee4ccbab7f146c553b97a8d44bff8ae2949
ms.sourcegitcommit: a20d30f4e5027f90d8ea4cde95d1d5bacfdd2b5e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/28/2022
ms.locfileid: "68769972"
---
# <a name="get-started-with-communication-compliance"></a>Prise en main de la conformité des communications

> [!IMPORTANT]
> Conformité des communications Microsoft Purview fournit les outils pour aider les organisations à détecter les violations de conformité réglementaire (par exemple SEC ou FINRA), telles que des informations sensibles ou confidentielles, des propos harcelants ou menaçants, et le partage de contenu pour adultes. Conçu avec la confidentialité par défaut, les noms d’utilisateur sont pseudonymisés par défaut, les contrôles d’accès en fonction du rôle sont intégrés, les enquêteurs sont activés par un administrateur et les journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Utilisez des stratégies de conformité des communications pour identifier les communications utilisateur à des fins d’analyse par des réviseurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à détecter les communications dans votre organisation, consultez Stratégies de [conformité des communications](/microsoft-365/compliance/communication-compliance-policies). Si vous souhaitez voir comment Contoso a configuré rapidement une stratégie de conformité des communications pour détecter du contenu potentiellement inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer, consultez cette [étude de cas](/microsoft-365/compliance/communication-compliance-case-study).

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

Avant de commencer à utiliser la conformité des communications, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la conformité des communications et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

- Abonnement Microsoft 365 E5/A5/F5/G5 (version payante ou d’évaluation)
- Abonnement Microsoft 365 E3/A3/F3/G5 + le module complémentaire conformité Microsoft 365 E5/A5/F5/G5
- Abonnement Microsoft 365 E3/A3/F3/G5 + module complémentaire Microsoft 365 E5/A5/F5/G5 Insider Risk Management
- abonnement Office 365 Entreprise E5 (version payante ou d’évaluation)
- abonnement Office 365 A5 (version payante ou d’évaluation)
- Office 365 Entreprise abonnement E3 + le module complémentaire Conformité avancée Office 365 (plus disponible pour les nouveaux abonnements, voir remarque)

Les utilisateurs inclus dans les stratégies de conformité des communications doivent se voir attribuer l’une des licences ci-dessus. Pour plus d’informations sur les abonnements et les licences, consultez [Les conseils microsoft 365 pour la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> La conformité des communications est actuellement disponible pour les locataires hébergés dans des régions géographiques et des pays pris en charge par les dépendances de service Azure. Pour vérifier que la conformité des communications est prise en charge pour votre organisation, consultez [Disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas d’offre Office 365 Entreprise E5 existante et que vous souhaitez essayer la conformité des communications, vous pouvez [ajouter Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire à un essai](https://www.microsoft.com/microsoft-365/enterprise) de Office 365 Entreprise E5.

> [!NOTE]
> Conformité avancée Office 365 n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contiennent les fonctionnalités de conformité identiques ou supplémentaires.

## <a name="recommended-actions-preview"></a>Actions recommandées (préversion)

Les actions recommandées peuvent aider votre organisation à prendre rapidement en main la conformité des communications. Incluses dans la page **Vue d’ensemble** , les actions recommandées vous aideront à suivre les étapes de configuration et de déploiement des stratégies.

Les recommandations suivantes sont disponibles pour vous aider à démarrer et optimiser votre configuration de conformité des communications :

- **Apprenez à connaître la conformité des communications** : avant de terminer la configuration, consultez notre documentation officielle pour en savoir plus sur, planifier et déployer la conformité des communications dans votre organisation.
- **Attribuez des autorisations pour vous assurer que votre équipe peut accomplir son travail** : assurez-vous que seules les parties prenantes appropriées peuvent accéder à la solution en affectant des membres de l’équipe responsables de la gestion des fonctionnalités de conformité des communications et de l’examen et de l’examen des alertes.
- **Créer des groupes de distribution pour les utilisateurs dont vous souhaitez détecter les communications** : Créez des groupes de distribution contenant des utilisateurs qui seront inclus dans les stratégies de conformité des communications.
- **Créez votre première stratégie pour commencer à détecter les communications** : détectez et examinez les violations de conformité réglementaire potentielles en configurant d’abord une stratégie qui identifie les violations potentielles dans les communications internes et/ou externes de votre organisation.
- **Passez en revue les alertes pour examiner les messages détectés et prendre des mesures** : identifiez et analysez les messages qui correspondent aux conditions d’une stratégie pour déclencher des alertes qui fournissent un contexte autour d’une violation de stratégie, afin que vous puissiez examiner et prendre des mesures si nécessaire.
- **Passez en revue les rapports pour obtenir des informations rapides sur le fonctionnement des stratégies** : obtenez des informations rapides sur le fonctionnement de vos stratégies, affichez des rapports détaillés pour approfondir vos connaissances et exportez les résultats pour des analyses plus approfondies.

Chaque action dans la conformité des communications a trois attributs :

- **Action** : nom et description de l’action recommandée.
- **Recommandé, obligatoire ou facultatif** : indique si l’action recommandée est fortement recommandée, obligatoire ou facultative pour que les fonctionnalités de conformité des communications fonctionnent comme prévu.
- **Durée estimée de l’exécution** : durée estimée de l’exécution de l’action recommandée en minutes.

Sélectionnez des recommandations dans la liste pour commencer à configurer la conformité des communications. Chaque action recommandée vous guide à travers les activités requises pour la recommandation, y compris les exigences, à quoi s'attendre et l'impact de la configuration de la fonctionnalité dans votre organisation. Certaines actions recommandées sont automatiquement marquées comme terminées lors de la configuration. Si ce n’est pas le cas, vous devez sélectionner manuellement l’action comme terminée lors de la configuration.

Également inclus dans la page Stratégies, les insights sur les actions recommandées permettent de résumer les types d’informations sensibles actuels et les violations potentielles de conformité réglementaire dans les communications au sein de votre organisation. Les insights sont pris en charge par la [classification des données](/microsoft-365/compliance/data-classification-overview) et l’application d’étiquettes de confidentialité, d’étiquettes de rétention et de classification des types d’informations sensibles. Ces informations sont agrégées et n’incluent aucune information d’identification personnelle (PII) pour les utilisateurs de votre organisation.

![Actions recommandées pour la conformité des communications.](../media/communication-compliance-recommended-actions.png)

L’activité dans les messages est agrégée par [type de classifieur](/microsoft-365/compliance/communication-compliance-policies#classifiers) à partir de stratégies existantes qui utilisent le modèle *de stratégie Détecter le texte inapproprié* ou de stratégies personnalisées qui utilisent des classifieurs. Examinez les alertes pour ces messages dans le **tableau de bord Alerte** pour vos stratégies.

Une activité impliquant des [types d’informations sensibles](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) est détectée dans les messages couverts dans les stratégies existantes et pour les messages qui ne sont pas couverts par les stratégies existantes. Les messages d’insight qui ne sont pas couverts par les stratégies existantes ne peuvent pas être examinés et corrigés. Une nouvelle stratégie doit être créée pour détecter et corriger une activité similaire dans les messages futurs. Les insights sont agrégés pour tous les types d’informations sensibles, y compris ceux que votre organisation n’a pas définis précédemment dans une stratégie de conformité des communications existante. Utilisez ces insights pour créer une stratégie de conformité des communications ou mettre à jour les stratégies existantes. Après avoir créé une stratégie, les alertes de messages pour cette stratégie peuvent ou non correspondre à un nombre égal de messages identifiés dans un insight similaire. Votre stratégie peut avoir des conditions différentes, un nombre différent d’utilisateurs dans l’étendue et détecte uniquement l’activité des messages qui se produit une fois la stratégie active.

>[!TIP]
>Vous ne voulez pas voir les informations sur les actions recommandées ? Ouvrez une demande avec Support Microsoft pour désactiver l’affichage de ces widgets d’insight pour votre organisation.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Étape 1 (obligatoire) : Activer les autorisations pour la conformité des communications

> [!IMPORTANT]
> Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs attribués au sein de votre organisation peut prendre jusqu’à 30 minutes.

Six groupes de rôles sont utilisés pour configurer les autorisations initiales afin de gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des communications** disponible en tant qu’option de menu dans portail de conformité Microsoft Purview et poursuivre ces étapes de configuration, vous devez être affecté à l’un des rôles ou groupes de rôles suivants :

- Rôle [*Administrateur général*](/azure/active-directory/roles/permissions-reference#global-administrator) Azure Active Directory
- [*Rôle Administrateur de conformité*](/azure/active-directory/roles/permissions-reference#compliance-administrator) Azure Active Directory
- portail de conformité Microsoft Purview [*groupe de rôles Gestion de l’organisation*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- portail de conformité Microsoft Purview groupe de rôles [*Administrateur de conformité*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- *Groupe de rôles Conformité des communications*
- *Groupe de rôles Administrateurs de conformité des communications*

Les membres des rôles suivants ont les mêmes autorisations de solution que celles incluses dans le groupe de rôles *Administrateurs de conformité des communications* :

- *Administrateur général* Azure Active Directory
- *Administrateur de conformité* Azure Active Directory
- *gestion de l’organisation* portail de conformité Microsoft Purview
- *Administrateur de conformité* portail de conformité Microsoft Purview

> [!IMPORTANT]
> Assurez-vous que vous avez toujours au moins un utilisateur dans les groupes de rôles *Conformité des communications* ou *Administrateurs de conformité des communications* (en fonction de l’option que vous choisissez) afin que votre configuration de conformité des communications n’entre pas dans un scénario « administrateur zéro » si des utilisateurs spécifiques quittent votre organisation.

Selon la façon dont vous souhaitez gérer les alertes et les stratégies de conformité des communications, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de conformité des communications. Vous avez la possibilité d’attribuer des utilisateurs avec des responsabilités de conformité différentes à des groupes de rôles spécifiques pour gérer différents domaines des fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés au groupe de rôles *Conformité des communications* . Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux à vos exigences de gestion de la conformité.

Choisissez parmi ces options de groupe de rôles de solution lors de la configuration et de la gestion de la conformité des communications :

| Rôle | Autorisations de rôle |
|:-----|:-----------------|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration est le moyen le plus simple de démarrer rapidement avec la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. Les utilisateurs qui créent des stratégies en tant qu’administrateur de conformité des communications doivent avoir leur boîte aux lettres hébergée sur Exchange Online.|
| **Administrateurs de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis pour séparer les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. Les utilisateurs qui créent des stratégies en tant qu’administrateur de conformité des communications doivent avoir leur boîte aux lettres hébergée sur Exchange Online.|
| **Analystes de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies où ils sont affectés en tant que réviseurs, afficher les métadonnées de message (et non le contenu des messages), remonter à d’autres réviseurs ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteurs de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, les réaffecter à d’autres réviseurs, passer à un cas eDiscovery (Premium), envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuses de la conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui géreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de conformité des communications et afficher tous les rapports de conformité des communications. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Option 1 : Affecter tous les utilisateurs de conformité au groupe de rôles Conformité des communications

1. Connectez-vous à [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) l’aide des informations d’identification d’un compte administrateur dans votre organisation Microsoft 365.

2. Dans le Centre de conformité de la sécurité &amp; , accédez à **Autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles *Conformité des communications* , puis **sélectionnez Modifier le groupe de rôles**.

4. Sélectionnez **Choisir des membres** dans le volet de navigation gauche, puis sélectionnez **Modifier**.

5. Sélectionnez **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles *Conformité des communications* .

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes.

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Option 2 : Affecter des utilisateurs à des groupes de rôles de conformité des communications spécifiques

Utilisez cette option pour affecter des utilisateurs à des groupes de rôles spécifiques afin de segmenter l’accès et les responsabilités de conformité des communications entre les différents utilisateurs de votre organisation.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365, puis accédez à **Autorisations**</a>.

2. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez l’un des groupes de rôles de conformité des communications, puis **sélectionnez Modifier le groupe de rôles**.

4. Sélectionnez **Choisir des membres** dans le volet de navigation gauche, puis sélectionnez **Modifier**.

5. Sélectionnez **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles.

8. Sélectionnez le groupe de rôles de conformité des communications suivant, puis répétez les étapes 4 à 7 pour chaque groupe de rôles requis.

9. Sélectionnez **Fermer** pour effectuer les étapes.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [Autorisations dans le Centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Étape 2 (obligatoire) : Activer le journal d’audit

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie organisationnelle définie ou à chaque modification d’une stratégie de conformité des communications.

L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape.

Pour obtenir des instructions détaillées sur l'activation de l'audit, consultez [Activer ou désactiver la recherche dans le journal d'audit](/microsoft-365/compliance/turn-audit-log-search-on-or-off). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n'avez à faire cette action qu'une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [Rechercher dans le journal d’audit](/microsoft-365/compliance/search-the-audit-log-in-security-and-compliance).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Étape 3 (facultative) : Configurer des groupes pour la conformité des communications

 Lorsque vous créez une stratégie de conformité des communications, vous définissez qui a ses communications examinées et qui effectue des révisions. Dans la stratégie, vous allez utiliser des adresses e-mail pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont la communication est examinée et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous en aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez détecter les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui ne sera pas supervisé.

Utilisez le graphique suivant pour vous aider à configurer des groupes dans votre organisation pour les stratégies de conformité des communications :

| **Membre de stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs exclus | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique <br> Groupes de distribution imbriqués <br> Groupes de sécurité à extension messagerie <br> Groupes Microsoft 365 avec appartenance dynamique |
| Relecteurs | Aucun | Groupes de distribution <br> Groupes de distribution dynamique <br> Groupes de distribution imbriqués <br> Groupes de sécurité à extension messagerie |

Lorsque vous attribuez un *groupe de distribution* dans la stratégie, la stratégie détecte tous les e-mails et conversations Teams de chaque utilisateur du *groupe de distribution*. Lorsque vous affectez un *groupe Microsoft 365* dans la stratégie, la stratégie détecte tous les e-mails et conversations Teams envoyés au *groupe Microsoft 365**, et non les e-mails et conversations individuels reçus par chaque membre du groupe. Il est recommandé d’utiliser des groupes de distribution dans les stratégies de conformité des communications afin que les e-mails individuels et les conversations Teams de chaque utilisateur soient automatiquement détectés.

Si vous êtes une organisation disposant d’un déploiement Exchange local ou d’un fournisseur de messagerie externe et que vous souhaitez détecter les conversations Microsoft Teams pour vos utilisateurs, vous devez créer un groupe de distribution pour les utilisateurs avec des boîtes aux lettres locales ou externes. Plus loin dans ces étapes, vous affecterez ce groupe de distribution en tant que sélection **Utilisateurs et groupes supervisés** dans l’Assistant Stratégie. Pour plus d’informations sur les exigences et les limitations relatives à l’activation du stockage cloud et à la prise en charge de Teams pour les utilisateurs locaux, consultez [Rechercher des données de conversation Teams pour les utilisateurs locaux](/microsoft-365/compliance/search-cloud-based-mailboxes-for-on-premises-users).

Pour gérer les utilisateurs supervisés dans les grandes organisations d’entreprise, vous devrez peut-être détecter les messages pour tous les utilisateurs de grands groupes. Vous pouvez utiliser PowerShell pour configurer un groupe de distribution pour une stratégie de conformité des communications globale pour le groupe affecté. Cela vous permet de détecter les messages pour des milliers d’utilisateurs avec une seule stratégie et de maintenir la stratégie de conformité des communications à jour à mesure que de nouveaux employés rejoignent votre organisation.

1. Créez un [groupe de distribution](/powershell/module/exchange/new-distributiongroup) dédié pour votre stratégie de conformité de communication globale avec les propriétés suivantes : Assurez-vous que ce groupe de distribution n’est pas utilisé à d’autres fins ou à d’autres services Office 365.

    - **MemberDepartRestriction = Fermé**. Garantit que les utilisateurs ne peuvent pas se supprimer du groupe de distribution.
    - **MemberJoinRestriction = Closed**. Garantit que les utilisateurs ne peuvent pas s’ajouter au groupe de distribution.
    - **ModerationEnabled = True**. Garantit que tous les messages envoyés à ce groupe sont soumis à approbation et que le groupe n’est pas utilisé pour communiquer en dehors de la configuration de la stratégie de conformité des communications.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Sélectionnez un [attribut personnalisé Exchange](/Exchange/recipients/mailbox-custom-attributes) inutilisé pour suivre les utilisateurs ajoutés à la stratégie de conformité des communications dans votre organisation.

3. Exécutez le script PowerShell suivant selon une planification périodique pour ajouter des utilisateurs à la stratégie de conformité des communications :

    ```PowerShell
    $Mbx = (Get-Mailbox -RecipientTypeDetails UserMailbox -ResultSize Unlimited -Filter {CustomAttribute9 -eq $Null})
    $i = 0
    ForEach ($M in $Mbx)
    {
      Write-Host "Adding" $M.DisplayName
      Add-DistributionGroupMember -Identity <your group name> -Member $M.DistinguishedName -ErrorAction SilentlyContinue
      Set-Mailbox -Identity $M.Alias -<your custom attribute name> SRAdded
      $i++
    }
    Write-Host $i "Mailboxes added to supervisory review distribution group."
    ```

Pour plus d’informations sur la configuration des groupes, consultez :

- [Création et gestion de groupes de distribution](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Vue d’ensemble de Groupes Microsoft 365](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Étape 4 (facultative) : Vérifier que votre locataire Yammer est en mode natif

En mode natif, tous les utilisateurs yammer se trouvent dans Azure Active Directory (Azure AD), tous les groupes sont Office 365 groupes et tous les fichiers sont stockés dans SharePoint Online. Votre locataire Yammer doit être en mode natif pour que les stratégies de conformité des communications vérifient et identifient les conversations à risque dans les messages privés et les conversations de la communauté dans Yammer.

Pour plus d’informations sur la configuration de Yammer en mode natif, consultez :

- [Vue d’ensemble du mode natif Yammer dans Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Configurer votre réseau Yammer en mode natif pour Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Étape 5 (obligatoire) : Créer une stratégie de conformité des communications

> [!IMPORTANT]
> L’utilisation de PowerShell pour créer et gérer des stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité des communications](https://compliance.microsoft.com/supervisoryreview).

> [!TIP]
> Vous souhaitez voir une procédure pas à pas détaillée de la configuration d’une nouvelle stratégie de conformité des communications et de la correction d’une alerte ? Regardez [cette vidéo de 15 minutes](/microsoft-365/compliance/communication-compliance-plan#creating-a-communication-compliance-policy-walkthrough) pour voir une démonstration de la façon dont les stratégies de conformité des communications peuvent vous aider à détecter les messages potentiellement inappropriés, à examiner les violations potentielles et à corriger les problèmes de conformité.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte administrateur dans votre organisation Microsoft 365.

2. Dans la portail de conformité Microsoft Purview, sélectionnez **Conformité des communications**.

3. Cliquez sur l'onglet **Stratégies**.

4. Sélectionnez **Créer une stratégie** pour créer et configurer une stratégie à partir d’un modèle ou pour créer et configurer une stratégie personnalisée.

    Si vous choisissez un modèle de stratégie pour créer une stratégie, vous allez :

    - Confirmez ou mettez à jour le nom de la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.

    - Choisissez les utilisateurs ou les groupes à superviser, y compris les utilisateurs ou les groupes que vous souhaitez exclure. Lorsque vous utilisez le modèle de conflit d’intérêts, vous sélectionnez deux groupes ou deux utilisateurs pour détecter les communications internes.

    - Choisissez les réviseurs pour la stratégie. Les réviseurs sont des utilisateurs individuels et tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Les réviseurs ajoutés ici sont les réviseurs que vous pouvez choisir lors de l’escalade d’une alerte dans le flux de travail d’investigation et de correction. Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les informe de l’affectation à la stratégie et fournit des liens vers des informations sur le processus de révision.

    - Choisissez un champ de condition limité, généralement un type d’informations sensibles ou un dictionnaire de mots clés à appliquer à la stratégie.

    > [!NOTE]
    > Si vous souhaitez activer la [reconnaissance optique de caractères (OCR)](/microsoft-365/compliance/communication-compliance-policies#optical-character-recognition-ocr) pour identifier les images incorporées ou jointes dans les messages pour du texte imprimé ou manuscrit qui correspond aux conditions de stratégie, sélectionnez **Personnaliser les****conditions et le pourcentage** de stratégie  >  et activez **Extraire le texte imprimé ou manuscrit d’images à des fins d’évaluation**.

    Si vous choisissez d’utiliser l’Assistant Stratégie pour créer une stratégie personnalisée, vous allez :

    - Donnez un nom et une description à la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.

    - Choisissez les utilisateurs ou les groupes à superviser, y compris tous les utilisateurs de votre organisation, des utilisateurs et groupes spécifiques ou d’autres utilisateurs et groupes que vous souhaitez exclure.

    - Choisissez les réviseurs pour la stratégie. Les réviseurs sont des utilisateurs individuels et tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Les réviseurs ajoutés ici sont les réviseurs que vous pouvez choisir lors de l’escalade d’une alerte dans le flux de travail d’investigation et de correction. Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les informe de l’affectation à la stratégie et fournit des liens vers des informations sur le processus de révision.

    - Choisissez les canaux de communication à vérifier, notamment Exchange, Microsoft Teams ou Yammer. Vous choisirez également de vérifier les sources tierces si vous avez configuré un connecteur dans Microsoft 365.

    - Choisissez le sens de communication à détecter, y compris les communications entrantes, sortantes ou internes.

    - Définissez les [conditions](/microsoft-365/compliance/communication-compliance-policies#conditional-settings) de la stratégie de conformité des communications. Vous pouvez choisir parmi les conditions de correspondance pour l'adresse du message, les mots-clés, les types de fichiers et la taille.

    - Choisissez si vous souhaitez inclure des types d’informations sensibles. Cette étape vous permet de sélectionner les types d’informations sensibles par défaut et personnalisés. Choisissez parmi les types d’informations sensibles personnalisés ou les dictionnaires de mots clés personnalisés existants dans l’Assistant Stratégie de conformité des communications. Vous pouvez créer ces éléments avant d’exécuter l’Assistant si nécessaire. Vous pouvez également créer de nouveaux types d’informations sensibles à partir de l’Assistant Stratégie de conformité des communications.

    - Choisissez si vous souhaitez activer les classifieurs. Les classifieurs peuvent détecter la langue potentiellement inappropriée et les images envoyées ou reçues dans le corps des messages électroniques ou d’autres types de texte. Vous pouvez choisir les classifieurs intégrés suivants : *Menaces*, *Profanités*, *Harcèlement ciblé*, *Images adultes*, *Images Racy* et *Images Gory*.

    - Activez la [reconnaissance optique de caractères (OCR)](/microsoft-365/compliance/communication-compliance-policies#optical-character-recognition-ocr) pour identifier les images incorporées ou jointes dans les messages pour du texte imprimé ou manuscrit qui correspond aux conditions de stratégie. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés à du texte, des mots clés, des classifieurs ou des types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de documents de reconnaissance optique de caractères (OCR).

    - Définissez le Pourcentage de communications à réviser.

    - Passez en revue vos sélections de stratégie et créez la stratégie.

5. Sélectionnez **Créer une stratégie lors de** l’utilisation des modèles ou **Envoyer** lors de l’utilisation de l’Assistant Stratégie personnalisée.

6. La page **Votre stratégie a été créée** s’affiche avec des instructions sur le moment où la stratégie sera activée et les communications qui seront capturées.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>Étape 6 (facultative) : Mettre à jour les limites de conformité pour les stratégies de conformité des communications

[Les limites de conformité](/microsoft-365/compliance/set-up-compliance-boundaries) créent des limites logiques au sein d’une organisation qui contrôlent les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les comptes OneDrive et les sites SharePoint) que les gestionnaires eDiscovery peuvent rechercher.

Si vous avez configuré des limites de conformité dans votre organisation, vous devez mettre à jour les limites de conformité pour permettre à certains utilisateurs d’accéder aux boîtes aux lettres qui prennent en charge les stratégies de conformité des communications. Vous devez autoriser l’accès aux administrateurs de conformité des communications et aux réviseurs de conformité des communications pour que vos actions de gestion des stratégies et d’investigation et de correction fonctionnent correctement.

Pour autoriser l’accès des administrateurs et réviseurs de conformité des communications, exécutez les commandes PowerShell suivantes. Vous ne devez exécuter ces commandes qu’une seule fois, même si vous ajoutez de nouvelles stratégies de conformité des communications à l’avenir :

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Pour plus d’informations sur la syntaxe des applets de commande, consultez [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>Étape 7 (facultative) : Créer des modèles de notification et configurer l’anonymisation de l’utilisateur

Si vous souhaitez avoir la possibilité de répondre à une alerte de stratégie en envoyant une notification de rappel à l’utilisateur associé, vous devez créer au moins un modèle de notification dans votre organisation. Les champs de modèle d’avis sont modifiables avant d’être envoyés dans le cadre du processus de correction d’alerte, et il est recommandé de créer un modèle de notification personnalisé pour chaque stratégie de conformité des communications.

Vous pouvez également choisir d’activer l’anonymisation pour les noms d’utilisateur affichés lors de l’examen des correspondances de stratégie et de l’action sur les messages.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte administrateur dans votre organisation Microsoft 365.

2. Dans le portail de conformité Microsoft Purview, accédez à **Conformité des communications**.

3. Pour configurer l’anonymisation des noms d’utilisateur, sélectionnez l’onglet **Confidentialité** .

4. Pour activer l’anonymisation, sélectionnez **Afficher les versions anonymes des noms d’utilisateur**.

5. Sélectionnez **Enregistrer**.

6. Accédez à l’onglet **Modèles de** notification, puis sélectionnez **Créer un modèle d’avis**.

7. Dans la page **Modifier un modèle d’avis** , renseignez les champs suivants :

    - Nom du modèle (obligatoire)
    - Envoyer à partir de (obligatoire)
    - Cc et Cci (facultatif)
    - Objet (obligatoire)
    - Corps du message (obligatoire)

8. Sélectionnez **Enregistrer** pour créer et enregistrer le modèle d’avis.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>Étape 8 (facultative) : Tester votre stratégie de conformité des communications

Après avoir créé une stratégie de conformité des communications, il est judicieux de la tester pour vous assurer que les conditions que vous avez définies sont correctement appliquées par la stratégie. Vous pouvez également [tester vos stratégies de Protection contre la perte de données Microsoft Purview (DLP)](/microsoft-365/compliance/create-test-tune-dlp-policy) si vos stratégies de conformité des communications incluent des types d’informations sensibles. Veillez à laisser à vos stratégies le temps d’activer afin que les communications que vous souhaitez tester soient capturées.

Procédez comme suit pour tester votre stratégie de conformité des communications :

1. Ouvrez un client de messagerie, Microsoft Teams ou Yammer quand vous êtes connecté en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.

2. Envoyez un e-mail, une conversation Microsoft Teams ou un message Yammer qui répond aux critères que vous avez définis dans la stratégie de conformité des communications. Ce test peut être un mot clé, une taille de pièce jointe, un domaine, etc. Veillez à déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop indulgents.

    > [!NOTE]
    > Email messages peuvent prendre environ 24 heures pour être entièrement traité dans une stratégie. Les communications dans Microsoft Teams, Yammer et les plateformes tierces peuvent prendre environ 48 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité des communications. Accédez à **Alertes de conformité** >  des communications pour afficher les alertes de vos stratégies.

4. Corrigez l’alerte à l’aide des contrôles de correction et vérifiez que l’alerte est correctement résolue.

## <a name="next-steps"></a>Prochaines étapes

Une fois que vous avez effectué ces étapes pour créer votre première stratégie de conformité des communications, vous commencez à recevoir des alertes des indicateurs d’activité après 24 à 48 heures. Configurez des stratégies supplémentaires en fonction des besoins à l’aide des instructions de l’étape 5 de cet article.

Pour en savoir plus sur l’examen des alertes de conformité des communications, consultez [Examiner et corriger les alertes de conformité des communications](/microsoft-365/compliance/communication-compliance-investigate-remediate).

Pour suivre les dernières mises à jour de conformité des communications, sélectionnez **Nouveautés de la** [conformité des communications](https://compliance.microsoft.com/) pour votre organisation.
