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
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom: admindeeplinkCOMPLIANCE
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: c4e28c91cc7e7fe441d000553e9099ad39420991
ms.sourcegitcommit: 7dc7e9fd76adf848f941919f86ca25eecc704015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/11/2022
ms.locfileid: "65317045"
---
# <a name="get-started-with-communication-compliance"></a>Prise en main de la conformité des communications

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Utilisez des stratégies de conformité des communications pour identifier les communications utilisateur à examiner par des réviseurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à surveiller les communications au sein de votre organisation, consultez [les stratégies de conformité des communications](communication-compliance.md). Si vous souhaitez examiner comment Contoso a rapidement configuré une stratégie de conformité des communications pour surveiller le contenu inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer, consultez cette [étude de cas](communication-compliance-case-study.md).

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

Avant de commencer à vous familiariser avec la conformité des communications, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la conformité des communications et l’utiliser, votre organisation doit disposer de l’un des abonnements ou modules complémentaires suivants :

- abonnement Microsoft 365 E5/A5/F5/G5 (version payante ou d’évaluation)
- Microsoft 365 E3/A3/F3/G5 + le module complémentaire conformité Microsoft 365 E5/A5/F5/G5
- Microsoft 365 E3/A3/F3/G5 + le module complémentaire de gestion des risques internes Microsoft 365 E5/A5/F5/G5
- Office 365 Entreprise abonnement E5 (version payante ou d’évaluation)
- abonnement Office 365 A5 (version payante ou d’évaluation)
- Office 365 Entreprise abonnement E3 + le module complémentaire Conformité avancée Office 365 (plus disponible pour les nouveaux abonnements, voir la note)

L’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de conformité des communications. Pour plus d’informations sur les abonnements et les licences, consultez [Microsoft 365 conseils sur la sécurité & la conformité](/office365/servicedescriptions/microsoft-365-service-descriptions/microsoft-365-tenantlevel-services-licensing-guidance/microsoft-365-security-compliance-licensing-guidance#communication-compliance).

> [!IMPORTANT]
> La conformité des communications est actuellement disponible dans les locataires hébergés dans des régions géographiques et des pays pris en charge par les dépendances du service Azure. Pour vérifier que la conformité des communications est prise en charge pour votre organisation, consultez [la disponibilité des dépendances Azure par pays/région](/troubleshoot/azure/general/dependency-availability-by-country).

Si vous n’avez pas de plan Office 365 Entreprise E5 existant et que vous souhaitez essayer la conformité des communications, vous pouvez [ajouter Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire à une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Office 365 Entreprise E5.

> [!NOTE]
> Conformité avancée Office 365 n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contiennent les mêmes fonctionnalités de conformité ou d’autres.

## <a name="recommended-actions-preview"></a>Actions recommandées (préversion)

Les actions recommandées peuvent aider votre organisation à prendre en main les fonctionnalités de conformité des communications et à tirer le meilleur parti de vos stratégies existantes. Incluses dans la page **Stratégies** , les actions recommandées fournissent des insights et résument les types d’informations sensibles et les activités de contenu inappropriées dans les communications de votre organisation. Informations sont prises en charge par la [classification des données](data-classification-overview.md) et l’application d’étiquettes de confidentialité, d’étiquettes de rétention et de classification des types d’informations sensibles. Ces informations n’incluent pas d’informations d’identification personnelle (PII) pour les utilisateurs de votre organisation.

![Actions recommandées pour la conformité des communications.](../media/communication-compliance-recommended-actions.png)

L’activité dans les messages contenant du contenu inapproprié est agrégée par [type de classifieur](/microsoft-365/compliance/communication-compliance-policies#classifiers) à partir de stratégies existantes qui utilisent le modèle de contenu inapproprié ou des stratégies personnalisées qui utilisent des classifieurs pour du contenu inapproprié. Examinez les alertes de ces messages dans le tableau de bord Des alertes pour vos stratégies.

L’activité impliquant des [types d’informations sensibles](/microsoft-365/compliance/communication-compliance-policies#sensitive-information-types) est détectée dans les messages couverts par les stratégies existantes et pour les messages qui ne sont pas couverts par les stratégies existantes. Informations sont agrégées pour tous les types d’informations sensibles, y compris ceux que votre organisation n’a pas encore définis dans une stratégie de conformité des communications existante. Utilisez ces informations pour créer une stratégie de conformité des communications ou mettre à jour des stratégies existantes.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Étape 1 (obligatoire) : activer les autorisations pour la conformité des communications

> [!IMPORTANT]
> Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs affectés au sein de votre organisation peut prendre jusqu’à 30 minutes.

Six groupes de rôles sont utilisés pour configurer les autorisations initiales pour gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des communications** disponible en tant qu’option de menu dans portail de conformité Microsoft Purview et pour poursuivre ces étapes de configuration, vous devez être affecté à l’un des rôles ou groupes de rôles suivants :

- Azure Active Directory rôle [*d’administrateur général*](/azure/active-directory/roles/permissions-reference#global-administrator)
- Azure Active Directory rôle [*d’administrateur de conformité*](/azure/active-directory/roles/permissions-reference#compliance-administrator)
- portail de conformité Microsoft Purview groupe [*de rôles Gestion de l’organisation*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center)
- groupe de [*rôles administrateur de conformité*](/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center) portail de conformité Microsoft Purview
- *Groupe de rôles Conformité des communications*
- *Groupe de rôles Administrateur de la conformité des communications*

Les membres des rôles suivants disposent des mêmes autorisations de solution incluses dans le groupe de *rôles Administrateur de conformité des communications* :

- *administrateur général* Azure Active Directory
- *administrateur de conformité* Azure Active Directory
- *gestion de l’organisation* portail de conformité Microsoft Purview
- *Administrateur de conformité* portail de conformité Microsoft Purview

> [!IMPORTANT]
> Assurez-vous d’avoir toujours au moins un utilisateur dans les groupes de rôles *Conformité* des communications ou Administration de la *conformité* des communications (en fonction de l’option que vous choisissez) afin que votre configuration de conformité des communications n’accède pas à un scénario « zéro administrateur » si des utilisateurs spécifiques quittent votre organisation.

Selon la façon dont vous souhaitez gérer les stratégies et les alertes de conformité des communications, vous devez affecter des utilisateurs à des groupes de rôles spécifiques pour gérer différents ensembles de fonctionnalités de conformité des communications. Vous avez la possibilité d’affecter des utilisateurs ayant des responsabilités de conformité différentes à des groupes de rôles spécifiques pour gérer différents domaines de fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés au groupe de rôles *Conformité des communications* . Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux à vos exigences de gestion de la conformité.

Choisissez parmi ces options de groupe de rôles de solution lors de la configuration et de la gestion de la conformité des communications :

| Rôle | Autorisations de rôle |
|:-----|:-----------------|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et observateurs désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité de communication. Cette configuration est le moyen le plus simple de prendre rapidement en main la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. Les utilisateurs qui créent des stratégies en tant qu’administrateur de conformité des communications doivent avoir leur boîte aux lettres hébergée sur Exchange Online.|
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications et, plus tard, pour séparer les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité de communication, des paramètres globaux et des attributions de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. Les utilisateurs qui créent des stratégies en tant qu’administrateur de conformité des communications doivent avoir leur boîte aux lettres hébergée sur Exchange Online.|
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui joueront le rôle d’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies à l’endroit où ils sont affectés en tant que réviseurs, afficher les métadonnées de message (et non le contenu du message), effectuer une escalade vers des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui joueront le rôle d’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à d’autres réviseurs, passer à un cas eDiscovery (Premium), envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Option 1 : Affecter tous les utilisateurs de conformité au groupe de rôles Conformité des communications

1. Connectez-vous à [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le Centre de conformité de sécurité &amp; , accédez à **Autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de *rôles Conformité des communications* , puis **modifiez le groupe de rôles**.

4. **Sélectionnez Choisir des membres** dans le volet de navigation gauche, puis sélectionnez **Modifier**.

5. Sélectionnez **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de *rôles Conformité des communications* .

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Option 2 : Affecter des utilisateurs à des groupes de rôles de conformité de communication spécifiques

Utilisez cette option pour affecter des utilisateurs à des groupes de rôles spécifiques afin de segmenter l’accès à la conformité des communications et les responsabilités entre les différents utilisateurs de votre organisation.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365, puis accédez aux **autorisations**</a>.

2. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez l’un des groupes de rôles de conformité des communications, puis sélectionnez **Modifier le groupe de rôles**.

4. **Sélectionnez Choisir des membres** dans le volet de navigation gauche, puis sélectionnez **Modifier**.

5. Sélectionnez **Ajouter** , puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles.

8. Sélectionnez le groupe de rôles de conformité de communication suivant, puis répétez les étapes 4 à 7 pour chaque groupe de rôles requis.

9. Sélectionnez **Fermer** pour effectuer les étapes.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [Autorisations dans le Centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie organisationnelle définie ou à chaque modification d’une stratégie de conformité des communications.

L'audit est activé par défaut pour les organisations Microsoft 365. Certaines organisations peuvent avoir désactivé l'audit pour des raisons spécifiques. Si l'audit est désactivé pour votre organisation, c'est peut-être parce qu'un autre administrateur l'a désactivé. Nous vous recommandons de confirmer que vous pouvez réactiver l'audit lorsque vous terminez cette étape.

Pour obtenir des instructions détaillées sur l'activation de l'audit, consultez [Activer ou désactiver la recherche dans le journal d'audit](turn-audit-log-search-on-or-off.md). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n'avez à faire cette action qu'une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [Rechercher dans le journal d’audit](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Étape 3 (facultatif) : Configurer des groupes pour la conformité des communications

 Lorsque vous créez une stratégie de conformité des communications, vous définissez qui a examiné ses communications et qui effectue des révisions. Dans la stratégie, vous allez utiliser des adresses e-mail pour identifier des personnes ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont la communication est examinée et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous en aurez peut-être besoin. Par exemple, si vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui ne sera pas supervisé.

Utilisez le graphique suivant pour vous aider à configurer des groupes dans votre organisation pour les stratégies de conformité des communications :

| **Membre de stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs exclus | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique <br> Groupes de distribution imbriqués <br> Groupes de sécurité à extension messagerie <br> Microsoft 365 groupes avec appartenance dynamique |
| Relecteurs | Aucune | Groupes de distribution <br> groupes de distribution dynamiques <br> Groupes de distribution imbriqués <br> Groupes de sécurité à extension messagerie |

Lorsque vous affectez un *groupe de distribution* dans la stratégie, la stratégie surveille tous les e-mails et Teams conversations de chaque utilisateur du *groupe de distribution*. Lorsque vous affectez un *groupe Microsoft 365* dans la stratégie, la stratégie surveille tous les e-mails et Teams conversations envoyées au *groupe Microsoft 365** et non les e-mails et conversations individuels reçus par chaque membre du groupe. L’utilisation de groupes de distribution dans les stratégies de conformité des communications est recommandée afin que les e-mails individuels et les conversations Teams de chaque utilisateur soient automatiquement surveillés.

Si vous êtes une organisation avec un déploiement local Exchange ou un fournisseur de courrier externe et que vous souhaitez surveiller Microsoft Teams conversations pour vos utilisateurs, vous devez créer un groupe de distribution pour les utilisateurs disposant de boîtes aux lettres locales ou externes à surveiller. Plus loin dans ces étapes, vous allez affecter ce groupe de distribution comme **sélection d’utilisateurs et de groupes supervisés** dans l’Assistant Stratégie. Pour plus d’informations sur les exigences et les limitations relatives à l’activation du stockage cloud et Teams la prise en charge des utilisateurs locaux, consultez [Rechercher des données de conversation Teams pour les utilisateurs locaux](search-cloud-based-mailboxes-for-on-premises-users.md).

Pour gérer les utilisateurs supervisés dans les grandes organisations d’entreprise, vous devrez peut-être surveiller tous les utilisateurs dans les grands groupes. Vous pouvez utiliser PowerShell pour configurer un groupe de distribution pour une stratégie de conformité de communication globale pour le groupe affecté. Cela vous permet de surveiller des milliers d’utilisateurs avec une stratégie unique et de mettre à jour la stratégie de conformité des communications à mesure que de nouveaux employés rejoignent votre organisation.

1. Créez un [groupe de distribution](/powershell/module/exchange/new-distributiongroup) dédié pour votre stratégie globale de conformité des communications avec les propriétés suivantes : assurez-vous que ce groupe de distribution n’est pas utilisé à d’autres fins ou à d’autres services Office 365.

    - **MemberDepartRestriction = Closed**. Garantit que les utilisateurs ne peuvent pas se supprimer du groupe de distribution.
    - **MemberJoinRestriction = Fermé**. Garantit que les utilisateurs ne peuvent pas s’ajouter au groupe de distribution.
    - **ModerationEnabled = True**. Garantit que tous les messages envoyés à ce groupe sont soumis à l’approbation et que le groupe n’est pas utilisé pour communiquer en dehors de la configuration de la stratégie de conformité des communications.

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

Pour plus d’informations sur la configuration de groupes, consultez :

- [Création et gestion de groupes de distribution](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Vue d’ensemble de Groupes Microsoft 365](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Étape 4 (facultatif) : vérifier que votre locataire Yammer est en mode natif

En mode natif, tous les utilisateurs Yammer sont en Azure Active Directory (Azure AD), tous les groupes sont des groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online. Votre locataire Yammer doit être en mode natif pour que les stratégies de conformité des communications analysent et identifient les conversations à risque dans les messages privés et les conversations de la communauté dans Yammer.

Pour plus d’informations sur la configuration de Yammer en mode natif, consultez :

- [Vue d’ensemble du mode natif Yammer dans Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Configurer votre réseau Yammer en mode natif pour Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Étape 5 (obligatoire) : Créer une stratégie de conformité des communications

>[!IMPORTANT]
>L’utilisation de PowerShell pour créer et gérer des stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité des communications](https://compliance.microsoft.com/supervisoryreview).

>[!TIP]  
>Vous souhaitez voir une procédure détaillée de configuration d’une nouvelle stratégie de conformité des communications et de correction d’une alerte ? Regardez [cette vidéo de 15 minutes](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) pour voir une démonstration de la façon dont les stratégies de conformité des communications peuvent vous aider à détecter les messages inappropriés, à examiner les violations potentielles et à corriger les problèmes de conformité.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le portail de conformité Microsoft Purview, sélectionnez **Conformité des communications**.

3. Cliquez sur l'onglet **Stratégies**.

4. Sélectionnez **Créer une stratégie** pour créer et configurer une nouvelle stratégie à partir d’un modèle ou pour créer et configurer une stratégie personnalisée.

    Si vous choisissez un modèle de stratégie pour créer une stratégie, vous allez :

    - Confirmez ou mettez à jour le nom de la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.

    - Choisissez les utilisateurs ou groupes à superviser, notamment les utilisateurs ou les groupes que vous souhaitez exclure. Lorsque vous utilisez le modèle de conflit d’intérêts, vous sélectionnez deux groupes ou deux utilisateurs à surveiller pour les communications internes.

    - Choisissez les réviseurs de la stratégie. Les réviseurs sont des utilisateurs individuels et tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Les réviseurs ajoutés ici sont les réviseurs parmi lesquels vous pouvez choisir lors de l’escalade d’une alerte dans le flux de travail d’investigation et de correction. Lorsque les réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les avertit de l’attribution à la stratégie et fournit des liens vers des informations sur le processus de révision.

    - Choisissez un champ de condition limitée, généralement un type d’informations sensibles ou un dictionnaire de mots clés à appliquer à la stratégie.

    > [!NOTE]
    > Si vous souhaitez activer la [reconnaissance optique de caractères (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) pour analyser les images incorporées ou jointes dans les messages pour rechercher du texte imprimé ou manuscrit qui correspond aux conditions de stratégie, sélectionnez **Personnaliser policyConditions** >  **et pourcentage**, puis **activez Extraire du texte imprimé ou manuscrit à partir d’images à des fins d’évaluation**.

    Si vous choisissez d’utiliser l’Assistant Stratégie pour créer une stratégie personnalisée, vous allez :

    - Donnez un nom et une description à la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.

    - Choisissez les utilisateurs ou groupes à superviser, y compris tous les utilisateurs de votre organisation, des utilisateurs et des groupes spécifiques, ou d’autres utilisateurs et groupes que vous souhaitez exclure.

    - Choisissez les réviseurs de la stratégie. Les réviseurs sont des utilisateurs individuels et tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Les réviseurs ajoutés ici sont les réviseurs parmi lesquels vous pouvez choisir lors de l’escalade d’une alerte dans le flux de travail d’investigation et de correction. Lorsque les réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un e-mail qui les avertit de l’attribution à la stratégie et fournit des liens vers des informations sur le processus de révision.

    - Choisissez les canaux de communication à analyser, notamment Exchange, Microsoft Teams, Yammer ou Skype Entreprise. Vous choisirez également d’analyser des sources tierces si vous avez configuré un connecteur dans Microsoft 365.

    - Choisissez la direction de communication à surveiller, y compris les communications entrantes, sortantes ou internes.

    - Définissez les [conditions](communication-compliance-policies.md#ConditionalSettings) de stratégie de conformité des communications. Vous pouvez choisir parmi les conditions de correspondance pour l'adresse du message, les mots-clés, les types de fichiers et la taille.

    - Choisissez si vous souhaitez inclure des types d’informations sensibles. Cette étape vous permet de sélectionner les types d’informations sensibles par défaut et personnalisés. Choisissez parmi les types d’informations sensibles personnalisés existants ou les dictionnaires de mots clés personnalisés dans l’Assistant Stratégie de conformité des communications. Vous pouvez créer ces éléments avant d’exécuter l’Assistant si nécessaire. Vous pouvez également créer de nouveaux types d’informations sensibles à partir de l’Assistant Stratégie de conformité des communications.

    - Choisissez si vous souhaitez activer les classifieurs. Les classifieurs peuvent détecter la langue et les images inappropriées envoyées ou reçues dans le corps des messages électroniques ou d’autres types de texte. Vous pouvez choisir les classifieurs intégrés suivants : *menaces*, *blasphèmes*, *harcèlement ciblé*, *images adultes*, *images racées* et *images Gory*.

    - Activez la [reconnaissance optique des caractères (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) pour analyser les images incorporées ou attachées dans les messages pour rechercher du texte imprimé ou manuscrit qui correspond aux conditions de stratégie. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés au texte, aux mots clés, aux classifieurs ou aux types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de l’analyse optique de la reconnaissance de caractères.

    - Définissez le Pourcentage de communications à réviser.

    - Passez en revue vos sélections de stratégie et créez-la.

5. Sélectionnez **Créer une stratégie** lors de l’utilisation des modèles ou **Envoyer** lors de l’utilisation de l’Assistant Stratégie personnalisée.

6. La page **Votre stratégie a été créée** s’affiche avec des instructions sur le moment où la stratégie sera activée et les communications qui seront capturées.

## <a name="step-6-optional-update-compliance-boundaries-for-communication-compliance-policies"></a>Étape 6 (facultatif) : Mettre à jour les limites de conformité pour les stratégies de conformité des communications

[Les limites de conformité](/microsoft-365/compliance/set-up-compliance-boundaries) créent des limites logiques au sein d’une organisation qui contrôlent les emplacements de contenu utilisateur (tels que les boîtes aux lettres, les comptes OneDrive et les sites SharePoint) que les gestionnaires eDiscovery peuvent rechercher.

Si vous avez configuré des limites de conformité dans votre organisation, vous devez mettre à jour les limites de conformité pour permettre à certains utilisateurs d’accéder aux boîtes aux lettres qui prennent en charge les stratégies de conformité des communications. Vous devez autoriser l’accès aux administrateurs de conformité des communications et aux réviseurs de conformité des communications pour que vos actions de gestion et d’investigation et de correction des stratégies fonctionnent correctement.

Pour autoriser l’accès aux administrateurs et réviseurs de conformité des communications, exécutez les commandes PowerShell suivantes. Vous n’avez besoin d’exécuter ces commandes qu’une seule fois, même si vous ajoutez de nouvelles stratégies de conformité des communications à l’avenir :

```powershell
Import-Module ExchangeOnlineManagement
$UserCredential = Get-Credential
Connect-IPPSSession -Credential $UserCredential
New-ComplianceSecurityFilter -FilterName "CC_mailbox" -Users <list your communication compliance admins and reviewers user alias or email address> -Filters "Mailbox_Name -like 'SupervisoryReview{*'" -Action All
```

Pour plus d’informations sur la syntaxe des applets de commande, consultez [New-ComplianceSecurityFilter](/powershell/module/exchange/new-compliancesecurityfilter).

## <a name="step-7-optional-create-notice-templates-and-configure-user-anonymization"></a>Étape 7 (facultatif) : créer des modèles d’avis et configurer l’anonymisation des utilisateurs

Si vous souhaitez avoir la possibilité de répondre à une alerte de stratégie en envoyant un avis de rappel à l’utilisateur associé, vous devez créer au moins un modèle d’avis dans votre organisation. Les champs de modèle d’avis sont modifiables avant d’être envoyés dans le cadre du processus de correction des alertes, et la création d’un modèle d’avis personnalisé pour chaque stratégie de conformité des communications est recommandée.

Vous pouvez également choisir d’activer l’anonymisation pour les noms d’utilisateur affichés lors de l’examen des correspondances de stratégie et de l’action sur les messages.

1. Connectez-vous au [portail de conformité Microsoft Purview](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le portail de conformité Microsoft Purview, accédez à **La conformité des communications**.

3. Pour configurer l’anonymisation des noms d’utilisateur, sélectionnez l’onglet **Confidentialité** .

4. Pour activer l’anonymisation, **sélectionnez Afficher les versions anonymes des noms d’utilisateur**.

5. Sélectionnez **Enregistrer**.

6. Accédez à l’onglet **Modèles d’avis** , puis **sélectionnez Créer un modèle d’avis**.

7. Dans la page **Modifier un modèle d’avis** , renseignez les champs suivants :

    - Nom du modèle (obligatoire)
    - Envoyer à partir de (obligatoire)
    - Cc et Cci (facultatif)
    - Objet (obligatoire)
    - Corps du message (obligatoire)

8. Sélectionnez **Enregistrer** pour créer et enregistrer le modèle d’avis.

## <a name="step-8-optional-test-your-communication-compliance-policy"></a>Étape 8 (facultatif) : Tester votre stratégie de conformité des communications

Une fois que vous avez créé une stratégie de conformité des communications, il est judicieux de la tester pour vous assurer que les conditions que vous avez définies sont correctement appliquées par la stratégie. Vous pouvez également [tester vos stratégies Protection contre la perte de données Microsoft Purview (DLP)](create-test-tune-dlp-policy.md) si vos stratégies de conformité des communications incluent des types d’informations sensibles. Veillez à laisser à vos stratégies le temps de s’activer afin que les communications que vous souhaitez tester soient capturées.

Procédez comme suit pour tester votre stratégie de conformité des communications :

1. Ouvrez un client de messagerie, Microsoft Teams ou Yammer lors de la connexion en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.

2. Envoyez un e-mail, une conversation Microsoft Teams ou Yammer message qui répond aux critères que vous avez définis dans la stratégie de conformité des communications. Ce test peut être un mot clé, une taille de pièce jointe, un domaine, etc. Veillez à déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop souples.

    > [!NOTE]
    > Le traitement complet des messages électroniques dans une stratégie peut prendre environ 24 heures. Les communications dans les plateformes Microsoft Teams, Yammer et tierces peuvent prendre environ 48 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité des communications. Accédez à **Communication** **complianceAlerts** >  pour afficher les alertes de vos stratégies.

4. Corrigez l’alerte à l’aide des contrôles de correction et vérifiez que l’alerte est correctement résolue.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez effectué ces étapes pour créer votre première stratégie de conformité des communications, vous commencerez à recevoir des alertes à partir d’indicateurs d’activité après 24 à 48 heures. Configurez des stratégies supplémentaires en fonction des besoins en suivant les instructions de l’étape 5 de cet article.

Pour en savoir plus sur l’examen des alertes de conformité des communications, consultez [Examiner et corriger les alertes de conformité des communications](communication-compliance-investigate-remediate.md).

Pour suivre les dernières mises à jour de conformité des communications, sélectionnez **Nouveautés** de la [conformité des communications](https://compliance.microsoft.com/) pour votre organisation.
