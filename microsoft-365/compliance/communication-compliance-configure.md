---
title: Prise en main de la conformité des communications
description: Configurez les stratégies de conformité des communications pour configurer les communications des employés pour révision.
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
- M365-security-compliance
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: b1ce2de627e7068124a1dfd15b84d40a2063d3a2
ms.sourcegitcommit: ab0a944159d9349fbc7adc2f51c7f881254d7782
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44210560"
---
# <a name="get-started-with-communication-compliance"></a>Prise en main de la conformité des communications

Utilisez des stratégies de conformité des communications pour capturer les communications des employés à des fins d’examen par des relecteurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à surveiller les communications au sein de votre organisation, consultez la rubrique [communications Compliance Policies in Microsoft 365](communication-compliance.md). Si vous souhaitez passer en revue la manière dont Contoso a configuré rapidement une stratégie de conformité de communication pour surveiller le langage choquant dans Microsoft Teams, Exchange Online et les communications Yammer, consultez cette [étude de cas](communication-compliance-case-study.md).

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

Pour que la conformité de la **communication** soit disponible sous la forme d’une option de menu dans le centre de conformité Microsoft 365, vous devez disposer du rôle d' **administrateur examen de surveillance** . Vous devez créer un nouveau groupe de rôles pour les relecteurs avec l' **administrateur de vérification de surveillance**, la gestion des **cas**, l' **administrateur de conformité**et les rôles de **révision** pour examiner et corriger les messages avec des correspondances de stratégie.

### <a name="create-a-new-role-group"></a>Créer un groupe de rôles

1. Connectez-vous [https://protection.office.com/permissions](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité &amp; conformité, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez **Créer**.

4. Dans le champ **nom** , attribuez un nom convivial au nouveau groupe de rôles. Sélectionnez **Suivant**.

5. Sélectionnez **choisir les rôles** , puis **Ajouter**. Activez la case à cocher **administrateur de vérification de surveillance**, gestion des **cas**, **administrateur de conformité**et **révision**, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

    ![Groupes de rôles obligatoires de conformité de la communication](../media/communication-compliance-role-groups-1.png)

6. Sélectionnez **choisir les membres** , puis **Ajouter**. Activez la case à cocher de tous les utilisateurs et groupes pour lesquels vous souhaitez créer des stratégies et gérer les messages avec des correspondances de stratégie, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

7. Sélectionnez **créer un groupe de rôles** à terminer.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les actions de correction effectuées par les relecteurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque fois qu’une stratégie de conformité de communication est modifiée.

Pour obtenir des instructions détaillées sur l’activation de l’audit, consultez la rubrique [activer ou désactiver la recherche dans le journal d’audit](turn-audit-log-search-on-or-off.md). Une fois que vous avez activé l’audit, un message s’affiche indiquant que le journal d’audit est en cours de préparation et que vous pouvez exécuter une recherche dans quelques heures après la fin de la préparation. Vous n’avez besoin d’effectuer cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [la rubrique Search the audit log](search-the-audit-log-in-security-and-compliance.md).

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Étape 3 (facultative) : configurer des groupes pour la conformité de la communication

 Lorsque vous créez une stratégie de conformité de communication, vous définissez les personnes qui ont consulté leurs communications et qui effectue des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont la communication est vérifiée et les groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

Utilisez le tableau suivant pour vous aider à configurer les groupes au sein de votre organisation pour les stratégies de conformité de communication :

| **Membre de la stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs non supervisés | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique |
| Relecteurs | Aucune | Groupes de distribution <br> groupes de distribution dynamiques <br> Groupes de sécurité à extension messagerie |
  
Lorsque vous sélectionnez un groupe Microsoft 365 pour les utilisateurs supervisés, la stratégie surveille le contenu de la boîte aux lettres partagée et des canaux Microsoft teams associés au groupe. Lorsque vous sélectionnez une liste de distribution, la stratégie analyse les boîtes aux lettres des utilisateurs individuels.

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
>L’utilisation de PowerShell pour créer et gérer des stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution de conformité de communication Microsoft 365](https://compliance.microsoft.com/supervisoryreview).

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
    - Choisissez si vous souhaitez activer les classifieurs. Les classifieurs peuvent détecter les langues inappropriées envoyées ou reçues dans le corps des messages électroniques ou dans d’autres types de texte.

    >[!CAUTION]
    >Nous détenons le classificateur intégré en **langage offensant** , car il a généré un nombre élevé de faux positifs. Ne l’utilisez pas et, si vous l’utilisez, vous devez déconnecter vos processus d’entreprise. Nous vous recommandons d’utiliser à la place les classifieurs intégrés de **menace**, de **blasphème**et de **harcèlement** .

    - Définir le pourcentage de communications à réviser.
    - Examinez vos sélections de stratégie et créez la stratégie.

5. Sélectionnez **créer une stratégie** lors de l’utilisation des modèles ou de l' **envoi** lors de l’utilisation de l’Assistant stratégie personnalisée.

6. La page **votre stratégie a été créée** s’affiche avec des instructions sur le moment où la stratégie sera activée et les communications qui seront capturées.

## <a name="step-6-optional-create-employee-notice-templates"></a>Étape 6 (facultative) : créer des modèles de notification d’employé

Si vous souhaitez pouvoir répondre à une alerte de stratégie en envoyant un rappel à l’employé associé, vous devez créer au moins un modèle d’avis dans votre organisation. Les champs du modèle d’avertissement sont modifiables avant d’être envoyés dans le cadre du processus de correction des alertes et la création d’un modèle d’avertissement personnalisé pour chaque stratégie de conformité des communications est recommandée.

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **conformité des communications**.

3. Sélectionnez l’onglet **modèles de notification** , puis sélectionnez créer un modèle d' **avis**.

4. Dans la page **modifier un modèle d’avis** , renseignez les champs suivants :

    - Nom du modèle d’avis (obligatoire)
    - Envoyer de (obligatoire)
    - CC et CCI (facultatif)
    - Subject (obligatoire)
    - Corps du message (obligatoire)

5. Sélectionnez **Enregistrer** pour créer et enregistrer le modèle d’avis.

## <a name="step-7-optional-test-your-communication-compliance-policy"></a>Étape 7 (facultative) : tester votre stratégie de conformité de communication

Une fois que vous avez créé une stratégie de conformité de communication, il est recommandé de la tester pour vous assurer que les conditions que vous avez définies sont appliquées correctement par la stratégie. Vous pouvez également [tester vos stratégies de protection contre la perte de données (DLP)](create-test-tune-dlp-policy.md) si vos stratégies de conformité de communication incluent des types d’informations sensibles. Assurez-vous que vous laissez vos stratégies s’activer afin que les communications que vous souhaitez tester soient capturées.

Procédez comme suit pour tester votre stratégie de conformité de communication :

1. Ouvrez un client de messagerie, Microsoft teams ou Yammer lors de la connexion en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.
2. Envoyez un message électronique, une conversation Microsoft teams ou un message Yammer correspondant aux critères que vous avez définis dans la stratégie de conformité de communication. Ce test peut être un mot clé, une taille de pièce jointe, un domaine, etc. Assurez-vous de déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop stricts.

    > [!NOTE]
    > Les communications de tous les canaux sources peuvent prendre jusqu’à 24 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité de communication. Accédez à **Communication compliance**  >  **alertes** de conformité des communications pour afficher les alertes correspondant à vos stratégies.

4. Corrigez l’alerte à l’aide des contrôles de correction et assurez-vous que l’alerte est correctement résolue.
