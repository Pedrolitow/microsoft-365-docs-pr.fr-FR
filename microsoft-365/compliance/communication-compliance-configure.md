---
title: Prise en main de la conformité des communications
description: Configurez les stratégies de conformité des communications pour configurer les communications des utilisateurs à des fins de révision.
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
localization_priority: Normal
ms.collection:
- Strat_O365_IP
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: 262cb34bbe7f2923ecf8dce88208c70ba0b5b7f7
ms.sourcegitcommit: 79a21583a52aedd06317bbcabd8be40663379dec
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/02/2020
ms.locfileid: "48341410"
---
# <a name="get-started-with-communication-compliance"></a>Prise en main de la conformité des communications

Utilisez des stratégies de conformité des communications pour identifier les communications des utilisateurs à des fins d’examen par des relecteurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à surveiller les communications au sein de votre organisation, consultez la rubrique [communications Compliance Policies in Microsoft 365](communication-compliance.md). Si vous souhaitez passer en revue la manière dont Contoso a configuré rapidement une stratégie de conformité de communication pour surveiller le langage choquant dans Microsoft Teams, Exchange Online et les communications Yammer, consultez cette [étude de cas](communication-compliance-case-study.md).

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer la mise en route de la conformité de la communication, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la conformité de la communication et l’utiliser, votre organisation doit disposer de l’un des abonnements ou des modules complémentaires suivants :

- Abonnement Microsoft 365 E5 (payant ou version d’évaluation)
- Microsoft 365 E3 subscription + le complément de conformité Microsoft 365 E5
- Microsoft 365 E3 subscription + le complément de gestion des risques de Microsoft 365 E5 Insider
- Abonnement Microsoft 365 a5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 a3 + complément Microsoft 365 a5 Compliance
- Abonnement Microsoft 365 a3 + complément de gestion des risques Microsoft 365 a5 Insider
- Abonnement Microsoft 365 G5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 G5 + le complément de conformité Microsoft 365 G5
- Abonnement Microsoft 365 G5 + le complément de gestion des risques Microsoft 365 G5 Insider
- Office 365 entreprise E5 abonnement (payant ou version d’évaluation)
- Office 365 entreprise E3 abonnement + le complément Office 365 Advanced Compliance (qui n’est plus disponible pour les nouveaux abonnements, reportez-vous à la rubrique note)

Les utilisateurs inclus dans les stratégies de conformité des communications doivent disposer de l’une des licences ci-dessus.

>[!IMPORTANT]
>Office 365 Advanced Compliance n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels arrivent à expiration, les clients doivent effectuer une transition vers l’un des abonnements ci-dessus, qui contiennent les mêmes fonctionnalités de conformité ou des fonctionnalités de conformité supplémentaires.

Si vous ne disposez pas d’un plan Office 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [ajouter Microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) d’Office 365 entreprise E5.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Étape 1 (obligatoire) : activer les autorisations pour la conformité de la communication

>[!Important]
>Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les rôles attribués au cours de cette étape sont obligatoires avant toute accessibilité des fonctionnalités de conformité de la communication.

Cinq groupes de rôles sont utilisés pour configurer les autorisations de gestion des fonctionnalités de conformité des communications. Pour que la conformité de la **communication** soit disponible sous la forme d’une option de menu dans le centre de conformité Microsoft 365 et pour poursuivre ces étapes de configuration, vous devez être affecté aux groupes de rôles de *conformité* de communication ou d' *administrateur de conformité* de communication. Pour accéder aux fonctionnalités de conformité de communication et les gérer une fois la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de conformité de communication.

En fonction de la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques. Vous pouvez attribuer à des groupes de rôles spécifiques des utilisateurs ayant des responsabilités différentes en matière de gestion des fonctionnalités de conformité des communications. Ou vous pouvez décider d’affecter tous les comptes d’utilisateur pour les administrateurs, analystes, investigateurs et visionneuses désignés au groupe de rôles de *conformité de communication* . Utilisez un seul groupe de rôles ou plusieurs groupes de rôles pour répondre au mieux aux besoins de gestion de la conformité.

Sélectionnez l’une des options de groupe de rôles suivantes lors de la configuration de la conformité des communications :

|**Role**|**Autorisations de rôle**|
|:-----|:-----|
| **Conformité de la communication** | Utilisez ce groupe de rôles pour gérer la conformité des communications de votre organisation dans un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, investigateurs et visionneuses désignés, vous pouvez configurer des autorisations de conformité de la communication dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité de communication. Cette configuration est la méthode la plus simple pour démarrer rapidement la conformité de la communication et convient aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité de communication** | Utilisez ce groupe de rôles pour configurer initialement la conformité de la communication et par la suite pour séparer les administrateurs de conformité des communications en un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité de communication, des paramètres globaux et des affectations de groupes de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies pour lesquelles ils sont affectés en tant que relecteurs, afficher les métadonnées de message (et non le contenu des messages), faire remonter aux relecteurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Investigation de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agiront en tant qu’investigations de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des relecteurs supplémentaires, passer à un cas avancé eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité de la communication** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui géreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de création de rapports sur la page d’accueil de la conformité de la communication et peuvent afficher tous les rapports de conformité des communications. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Option 1 : assigner tous les utilisateurs de conformité au groupe de rôles de conformité de communication

1. Connectez-vous [https://protection.office.com/permissions](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité &amp; conformité, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le groupe de rôles *conformité des communications* , puis sélectionnez Modifier le **groupe de rôles**.

4. Sélectionnez **choisir les membres** dans le volet de navigation de gauche, puis sélectionnez **modifier**.

5. Sélectionnez **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles de *conformité de communication* .

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Option 2 : affecter des utilisateurs à des groupes de rôles de conformité de communication spécifiques

Utilisez cette option pour affecter des utilisateurs à des groupes de rôles spécifiques afin de segmenter les responsabilités et l’accès à la conformité aux communications entre différents utilisateurs de votre organisation.

1. Connectez-vous [https://protection.office.com/permissions](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité &amp; conformité, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez l’un des groupes de rôles de conformité de communication, puis sélectionnez **modifier le groupe de rôles**.

4. Sélectionnez **choisir les membres** dans le volet de navigation de gauche, puis sélectionnez **modifier**.

5. Sélectionnez **Ajouter** , puis activez la case à cocher de tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles.

8. Sélectionnez le groupe de rôles de conformité de communication suivant, puis répétez les étapes 4-7 pour chaque groupe de rôles requis.

9. Sélectionnez **Fermer** pour effectuer les étapes.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque fois qu’une stratégie de conformité de communication est modifiée.

Pour obtenir des instructions détaillées sur l’activation de l’audit, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md). Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous n’avez besoin d’effectuer cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [la rubrique Search the audit log](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Étape 3 (facultative) : configurer des groupes pour la conformité de la communication

 Lorsque vous créez une stratégie de conformité de communication, vous définissez les personnes qui ont consulté leurs communications et qui effectue des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont la communication est vérifiée et les groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

Utilisez le tableau suivant pour vous aider à configurer les groupes au sein de votre organisation pour les stratégies de conformité de communication :

| **Membre de la stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs non supervisés | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique |
| Relecteurs | Aucun | Groupes de distribution <br> groupes de distribution dynamiques <br> Groupes de sécurité à extension messagerie |
  
Lorsque vous affectez un groupe de distribution dans la stratégie, la stratégie surveille tous les messages électroniques provenant de chaque utilisateur dans le groupe de distribution. Lorsque vous affectez un groupe Microsoft 365 dans la stratégie, la stratégie surveille tous les messages électroniques envoyés à ce groupe, et non les messages électroniques individuels reçus par chaque membre du groupe.

Si vous êtes une organisation disposant d’un déploiement Exchange sur site ou d’un fournisseur de messagerie externe et que vous souhaitez surveiller les conversations de Microsoft teams pour vos utilisateurs, vous devez créer un groupe de distribution pour les utilisateurs disposant de boîtes aux lettres locales ou externes à surveiller. Plus loin dans cette procédure, vous affecterez ce groupe de distribution en tant qu' **utilisateurs et groupes contrôlés** dans l’Assistant stratégie.

>[!IMPORTANT]
>Vous devez effectuer une demande auprès du Support Microsoft pour autoriser votre organisation à utiliser l’interface utilisateur graphique dans le centre de conformité et sécurité pour rechercher des données de conversations Teams pour des utilisateurs locaux. Pour plus d’informations, reportez-vous à la rubrique [recherche de boîtes aux lettres en nuage pour les utilisateurs locaux](search-cloud-based-mailboxes-for-on-premises-users.md).

Pour plus d’informations sur la configuration des groupes, voir :

- [Création et gestion de groupes de distribution](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Vue d’ensemble des groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/office-365-groups?view=o365-worldwide)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Étape 4 (facultatif) : Vérifiez que votre client Yammer est en mode natif

En mode natif, tous les utilisateurs de Yammer se trouvent dans Azure Active Directory (AAD), tous les groupes sont des Groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online. Votre client Yammer doit être en mode natif pour que les stratégies de conformité de communication analysent et identifient les conversations dangereuses dans les messages privés et les conversations communautaires dans Yammer.

Pour plus d’informations sur la configuration de yammer en mode natif, voir :

- [Vue d’ensemble du mode natif Yammer dans Microsoft 365](https://docs.microsoft.com/yammer/configure-your-yammer-network/overview-native-mode)
- [Configurer votre réseau Yammer en mode natif pour Microsoft 365](https://docs.microsoft.com/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Étape 5 (obligatoire) : créer une stratégie de conformité de communication
  
>[!Important]
>L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité de communication Microsoft 365](https://compliance.microsoft.com/supervisoryreview).

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, sélectionnez **conformité des communications**.
  
3. Sélectionnez l’onglet **stratégies** .

4. Sélectionnez **créer une stratégie** pour créer et configurer une nouvelle stratégie à partir d’un modèle ou pour créer et configurer une stratégie personnalisée.

    Si vous choisissez un modèle de stratégie pour créer une stratégie, vous devez :

    - Vérifiez ou mettez à jour le nom de la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.
    - Choisissez les utilisateurs ou les groupes à superviser, y compris le choix des utilisateurs ou des groupes que vous souhaitez exclure.
    - Choisissez les relecteurs de la stratégie. Les relecteurs sont des utilisateurs individuels et tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Les relecteurs ajoutés ici sont les relecteurs que vous pouvez choisir lors de la réaffectation d’une alerte dans le flux de travail d’enquête et de correction. Lorsque les relecteurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.
    - Choisissez un champ de condition limité, généralement un type d’informations sensibles ou un dictionnaire de mots clés à appliquer à la stratégie.

    Si vous choisissez d’utiliser l’Assistant stratégie pour créer une stratégie personnalisée, vous devez :

    - Donnez un nom et une description à la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.
    - Choisissez les utilisateurs ou les groupes à superviser, y compris tous les utilisateurs de votre organisation, des utilisateurs et des groupes spécifiques, ou d’autres utilisateurs et groupes que vous souhaitez exclure.
    - Choisissez les relecteurs de la stratégie. Les relecteurs sont des utilisateurs individuels et tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online. Les relecteurs ajoutés ici sont les relecteurs que vous pouvez choisir lors de la réaffectation d’une alerte dans le flux de travail d’enquête et de correction. Lorsque les relecteurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.
    - Choisissez les canaux de communication à analyser, y compris Exchange, Microsoft Teams, Yammer ou Skype entreprise. Vous choisirez également d’analyser les sources tierces si vous avez configuré un connecteur dans Microsoft 365.
    - Choisissez la direction de communication à surveiller, y compris les communications entrantes, sortantes ou internes.
    - Définir les [conditions](communication-compliance-feature-reference.md#ConditionalSettings)de la stratégie de conformité de communication. Vous pouvez choisir entre une adresse de message, un mot clé, un type de fichier et une condition de correspondance de taille.
    - Choisissez si vous souhaitez inclure des types d’informations sensibles. Cette étape vous permet de sélectionner les types d’informations sensibles par défaut et personnalisés. Sélectionnez des types d’informations sensibles personnalisés ou des dictionnaires de mots clés personnalisés existants dans l’Assistant stratégie de conformité des communications. Si nécessaire, vous pouvez créer ces éléments avant d’exécuter l’Assistant. Vous pouvez également créer des types d’informations sensibles à partir de l’Assistant stratégie de conformité des communications.
    - Choisissez si vous souhaitez activer les classifieurs. Les classifieurs peuvent détecter une langue et des images inappropriées envoyées ou reçues dans le corps de messages électroniques ou d’autres types de texte. Vous pouvez choisir les classifieurs intégrés suivants : *menace*, *blasphèmes*, *harcèlement ciblé*, *images adultes*, *images Racy*et *images Gory*.

    >[!CAUTION]
    >Nous déprécions le **langage inconvenant** classifieur intégré, car il génère un grand nombre de faux positifs. Ne l’utilisez pas et, si vous l’utilisez, vous devez déconnecter vos processus d’entreprise. Nous vous recommandons d’utiliser à la place les classifieurs intégrés de **menace**, de **blasphème**et de **harcèlement ciblé** .

    - Définir le pourcentage de communications à réviser.
    - Examinez vos sélections de stratégie et créez la stratégie.

5. Sélectionnez **créer une stratégie** lors de l’utilisation des modèles ou de l' **envoi** lors de l’utilisation de l’Assistant stratégie personnalisée.

6. La page **votre stratégie a été créée** s’affiche avec des instructions sur le moment où la stratégie sera activée et les communications qui seront capturées.

## <a name="step-6-optional-create-notice-templates-and-configure-user-anonymization"></a>Étape 6 (facultative) : créer des modèles d’avis et configurer l’anonymisation des utilisateurs

Si vous souhaitez pouvoir répondre à une alerte de stratégie en envoyant un rappel à l’utilisateur associé, vous devez créer au moins un modèle d’avertissement dans votre organisation. Les champs du modèle d’avertissement sont modifiables avant d’être envoyés dans le cadre du processus de correction des alertes et la création d’un modèle d’avertissement personnalisé pour chaque stratégie de conformité des communications est recommandée.

Vous pouvez également choisir d’activer l’anonymisation pour les noms d’utilisateurs affichés lors de l’étude des correspondances de stratégie et de l’exécution d’actions sur les messages.

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **conformité des communications**.

3. Pour configurer l’anonymat pour les noms d’utilisateur, sélectionnez l’onglet **confidentialité** .

4. Pour activer l’anonymisation, sélectionnez **afficher les versions anonymes des noms d’utilisateur**.

5. Sélectionnez **Enregistrer**.

6. Accédez à l’onglet **modèles de notification** , puis sélectionnez créer un modèle d' **avis**.

7. Dans la page **modifier un modèle d’avis** , renseignez les champs suivants :

    - Nom du modèle (obligatoire)
    - Envoyer de (obligatoire)
    - CC et CCI (facultatif)
    - Subject (obligatoire)
    - Corps du message (obligatoire)

8. Sélectionnez **Enregistrer** pour créer et enregistrer le modèle d’avis.

## <a name="step-7-optional-test-your-communication-compliance-policy"></a>Étape 7 (facultative) : tester votre stratégie de conformité de communication

Une fois que vous avez créé une stratégie de conformité de communication, il est recommandé de la tester pour vous assurer que les conditions que vous avez définies sont appliquées correctement par la stratégie. Vous pouvez également [tester vos stratégies de protection contre la perte de données (DLP)](create-test-tune-dlp-policy.md) si vos stratégies de conformité de communication incluent des types d’informations sensibles. Assurez-vous que vous laissez vos stratégies s’activer afin que les communications que vous souhaitez tester soient capturées.

Procédez comme suit pour tester votre stratégie de conformité de communication :

1. Ouvrez un client de messagerie, Microsoft teams ou Yammer lors de la connexion en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.
2. Envoyez un message électronique, une conversation Microsoft teams ou un message Yammer correspondant aux critères que vous avez définis dans la stratégie de conformité de communication. Ce test peut être un mot clé, une taille de pièce jointe, un domaine, etc. Assurez-vous de déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop stricts.

    > [!NOTE]
    > Les communications de tous les canaux sources peuvent prendre jusqu’à 24 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité de communication. Accédez à **Communication compliance**  >  **alertes** de conformité des communications pour afficher les alertes correspondant à vos stratégies.

4. Corrigez l’alerte à l’aide des contrôles de correction et assurez-vous que l’alerte est correctement résolue.

## <a name="next-steps"></a>Étapes suivantes

Une fois que vous avez terminé ces étapes pour créer votre première stratégie de conformité de communication, vous commencerez à recevoir des alertes des indicateurs d’activité après environ 24 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 5 de cet article.

Pour en savoir plus sur l’examen des alertes de conformité des communications, consultez la rubrique [examiner et corriger les alertes de conformité des communications](communication-compliance-investigate-remediate.md).
