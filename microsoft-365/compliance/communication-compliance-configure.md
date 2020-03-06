---
title: Configurer la conformité de la communication
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
ms.openlocfilehash: 3e3f16339d25c8cc592e937e30a446ed7e7cd333
ms.sourcegitcommit: 0d7f27982fe9e18a4df423da23b86e0b15e77c65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2020
ms.locfileid: "42542538"
---
# <a name="configure-communication-compliance-in-microsoft-365"></a>Configurer la conformité de la communication dans Microsoft 365

>[!IMPORTANT]
>Cette rubrique s’applique à la configuration de la conformité de la communication dans un abonnement Microsoft 365. Si vous souhaitez configurer des stratégies de surveillance pour un abonnement Office 365, consultez la rubrique [configure supervision for office 365](supervision-policies.md).

Utilisez des stratégies de conformité des communications pour capturer les communications des employés à des fins d’examen par des relecteurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à surveiller les communications au sein de votre organisation, consultez la rubrique [communications Compliance Policies in Microsoft 365](communication-compliance.md).

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer la mise en route de la conformité de la communication, vous devez confirmer votre abonnement Microsoft 365. Les utilisateurs inclus dans les stratégies de conformité des communications doivent disposer d’une licence de conformité Microsoft 365 E5, d’une licence Office 365 entreprise E3 avec le complément de conformité avancé ou être inclus dans un abonnement Microsoft 365 E5.

Si vous ne disposez pas d’un plan Microsoft 365 entreprise E5 existant et que vous souhaitez essayer de gérer les risques internes, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement Office 365 existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.
  
Procédez comme suit pour configurer et utiliser la conformité des communications dans votre organisation Microsoft 365 :

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Étape 1 (obligatoire) : activer les autorisations pour la conformité de la communication

>[!Important]
>Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les rôles attribués au cours de cette étape sont obligatoires avant toute accessibilité des fonctionnalités de conformité de la communication.

Pour que la conformité de la **communication** soit disponible sous la forme d’une option de menu dans le centre de conformité Microsoft 365, vous devez disposer du rôle d' **administrateur examen de surveillance** . Vous devez créer un nouveau groupe de rôles pour les relecteurs avec l' **administrateur de vérification de surveillance**, la gestion des **cas**, l' **administrateur de conformité**et les rôles de **révision** pour examiner et corriger les messages avec des correspondances de stratégie.

### <a name="create-a-new-role-group"></a>Créer un groupe de rôles

1. Connectez- [https://protection.office.com/permissions](https://protection.office.com/permissions) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de sécurité et conformité Microsoft Office 365, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez **Créer**.

4. Dans le champ **nom** , attribuez un nom convivial au nouveau groupe de rôles. Sélectionnez **Suivant**.

5. Sélectionnez **choisir les rôles** , puis **Ajouter**. Activez la case à cocher **administrateur de vérification de surveillance**, gestion des **cas**, **administrateur de conformité**et **révision**, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

    ![Groupes de rôles obligatoires de conformité de la communication](../media/communication-compliance-role-groups-1.png)

6. Sélectionnez **choisir les membres** , puis **Ajouter**. Activez la case à cocher de tous les utilisateurs et groupes pour lesquels vous souhaitez créer des stratégies et gérer les messages avec des correspondances de stratégie, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

7. Sélectionnez **créer un groupe de rôles** à terminer.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-2-required-enable-the-office-365-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit Office 365

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les actions de correction effectuées par les relecteurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie d’organisation définie ou à chaque fois qu’une stratégie de conformité de communication est modifiée.

Pour obtenir des instructions détaillées sur l’activation de l’audit, voir [activer ou désactiver la recherche dans le journal d’audit Office 365](turn-audit-log-search-on-or-off.md). Une fois que vous avez activé l’audit, un message s’affiche indiquant que le journal d’audit est en cours de préparation et que vous pouvez exécuter une recherche dans quelques heures après la fin de la préparation. Vous n’avez besoin d’effectuer cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, consultez [la rubrique Search the audit log](search-the-audit-log-in-security-and-compliance.md).


## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Étape 3 (facultative) : configurer des groupes pour la conformité de la communication

 Lorsque vous créez une stratégie de conformité de communication, vous définissez les personnes qui ont consulté leurs communications et qui effectue des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont la communication est vérifiée et les groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

Utilisez le tableau suivant pour vous aider à configurer les groupes au sein de votre organisation pour les stratégies de conformité de communication :

| **Membre de la stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs non supervisés | Groupes de distribution <br> Groupes Office 365 | Groupes de distribution dynamique |
| Relecteurs | Groupes de sécurité à extension messagerie  | Groupes de distribution <br> groupes de distribution dynamiques |
  
Lorsque vous sélectionnez un groupe Office 365 pour les utilisateurs supervisés, la stratégie surveille le contenu de la boîte aux lettres Office 365 partagée et les canaux Microsoft teams associés au groupe. Lorsque vous sélectionnez une liste de distribution, la stratégie analyse les boîtes aux lettres des utilisateurs individuels.

Pour plus d’informations sur la configuration des groupes, voir :

- [Création et gestion de groupes de distribution](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Gérer les groupes de sécurité à extension de messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups)
- [Vue d’ensemble des groupes Office 365](https://docs.microsoft.com/office365/admin/create-groups/office-365-groups?view=o365-worldwide)

## <a name="step-4-required-create-a-communication-compliance-policy"></a>Étape 4 (obligatoire) : créer une stratégie de conformité de communication
  
1. Connectez- [https://compliance.microsoft.com](https://compliance.microsoft.com) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, sélectionnez **conformité des communications**.
  
3. Sélectionnez l’onglet **stratégies** .

4. Sélectionnez **créer une stratégie** pour créer et configurer une nouvelle stratégie à partir d’un modèle ou pour créer et configurer une stratégie personnalisée.

    Si vous choisissez un modèle de stratégie pour créer une stratégie, vous devez :

    - Vérifiez ou mettez à jour le nom de la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.
    - Choisissez les utilisateurs ou les groupes à superviser, y compris le choix des utilisateurs ou des groupes que vous souhaitez exclure.
    - Choisissez les relecteurs de la stratégie. Les relecteurs peuvent être des utilisateurs individuels ou des [groupes de sécurité à extension messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#create-a-mail-enabled-security-group). Tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online.
    - Choisissez un champ de condition limité, généralement un type d’informations sensibles ou un dictionnaire de mots clés à appliquer à la stratégie.

    Si vous choisissez d’utiliser l’Assistant stratégie pour créer une stratégie personnalisée, vous devez :

    - Donnez un nom et une description à la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.
    - Choisissez les utilisateurs ou les groupes à superviser, y compris tous les utilisateurs de votre organisation, des utilisateurs et des groupes spécifiques, ou d’autres utilisateurs et groupes que vous souhaitez exclure.
    - Choisissez les relecteurs de la stratégie. Les relecteurs peuvent être des utilisateurs individuels ou des [groupes de sécurité à extension messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#create-a-mail-enabled-security-group). Tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online.
    - Choisissez les canaux de communication à analyser, y compris Exchange, Microsoft teams ou Skype entreprise. Vous choisirez également d’analyser les sources tierces si vous avez configuré un connecteur dans Microsoft 365.
    - Choisissez la direction de communication à surveiller, y compris les communications entrantes, sortantes ou internes.
    - Définir les [conditions](communication-compliance-feature-reference.md#ConditionalSettings)de la stratégie de conformité de communication. Vous pouvez choisir entre une adresse de message, un mot clé, un type de fichier et une condition de correspondance de taille.
    - Choisissez si vous souhaitez inclure des types d’informations sensibles. Cette étape vous permet de sélectionner les types d’informations sensibles par défaut et personnalisés. Sélectionnez des types d’informations sensibles personnalisés ou des dictionnaires de mots clés personnalisés existants dans l’Assistant stratégie de conformité des communications. Si nécessaire, vous pouvez créer ces éléments avant d’exécuter l’Assistant. Vous pouvez également créer des types d’informations sensibles à partir de l’Assistant stratégie de conformité des communications.
    - Choisissez si vous souhaitez activer le classificateur de langue offensant. Ce classifieur détecte une langue inappropriée envoyée ou reçue dans le corps des messages électroniques.
    - Définir le pourcentage de communications à réviser.
    - Examinez vos sélections de stratégie et créez la stratégie.

5. Sélectionnez **créer une stratégie** lors de l’utilisation des modèles ou de l' **envoi** lors de l’utilisation de l’Assistant stratégie personnalisée.

6. La page **votre stratégie a été créée** s’affiche avec des instructions sur le moment où la stratégie sera activée et les communications qui seront capturées.

## <a name="step-5-optional-create-employee-notice-templates"></a>Étape 5 (facultatif) : créer des modèles de notification d’employé

Si vous souhaitez pouvoir répondre à une alerte de stratégie en envoyant un rappel à l’employé associé, vous devez créer au moins un modèle d’avis dans votre organisation. Les champs du modèle d’avertissement sont modifiables avant d’être envoyés dans le cadre du processus de correction des alertes et la création d’un modèle d’avertissement personnalisé pour chaque stratégie de conformité des communications est recommandée.

1. Connectez- [https://compliance.microsoft.com](https://compliance.microsoft.com) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Microsoft 365.

2. Dans le centre de conformité Microsoft 365, accédez à **conformité des communications**.

3. Sélectionnez l’onglet **modèles de notification** , puis sélectionnez créer un modèle d' **avis**.

4. Dans la page **modifier un modèle d’avis** , renseignez les champs suivants :

    - Nom du modèle d’avis (obligatoire)
    - Envoyer de (obligatoire)
    - CC et CCI (facultatif)
    - Subject (obligatoire)
    - Corps du message (obligatoire)

5. Sélectionnez **Enregistrer** pour créer et enregistrer le modèle d’avis.

## <a name="step-6-optional-test-your-communication-compliance-policy"></a>Étape 6 (facultative) : tester votre stratégie de conformité de communication

Une fois que vous avez créé une stratégie de conformité de communication, il est recommandé de la tester pour vous assurer que les conditions que vous avez définies sont appliquées correctement par la stratégie. Vous pouvez également [tester vos stratégies de protection contre la perte de données (DLP)](create-test-tune-dlp-policy.md) si vos stratégies de conformité de communication incluent des types d’informations sensibles. Assurez-vous que vous laissez vos stratégies s’activer afin que les communications que vous souhaitez tester soient capturées.

Procédez comme suit pour tester votre stratégie de conformité de communication :

1. Ouvrez un client de messagerie ou Microsoft teams lors de la connexion en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.
2. Envoyez un message électronique ou une conversation Microsoft teams qui répond aux critères que vous avez définis dans la stratégie de conformité de communication. Ce test peut être un mot clé, une taille de pièce jointe, un domaine, etc. Assurez-vous de déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop stricts.

    > [!NOTE]
    > Les communications de tous les canaux sources peuvent prendre jusqu’à 24 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité de communication. Accédez à **** > **alertes** de conformité des communications pour afficher les alertes correspondant à vos stratégies.

4. Corrigez l’alerte à l’aide des contrôles de correction et assurez-vous que l’alerte est correctement résolue.
