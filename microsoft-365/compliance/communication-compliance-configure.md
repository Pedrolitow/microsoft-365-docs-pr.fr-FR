---
title: Configurer la conformité de la communication pour Microsoft 365 (version d’évaluation)
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
description: Configurez les stratégies de conformité des communications pour configurer les communications des employés pour révision.
ms.openlocfilehash: 0a830914a22968119d836e2190a6f133d91fd305
ms.sourcegitcommit: 5f96fa472cbdca30c2cfe24d66c9c6fcaedb1a6b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "38755602"
---
# <a name="configure-communication-compliance-for-microsoft-365-preview"></a>Configurer la conformité de la communication pour Microsoft 365 (version d’évaluation)

> [!IMPORTANT]
> Cette rubrique s’applique à la configuration de la conformité de la communication dans un abonnement Microsoft 365. Si vous souhaitez configurer des stratégies de surveillance pour un abonnement Office 365, consultez la rubrique [configure supervision for office 365](supervision-policies.md).

Utilisez des stratégies de conformité des communications pour capturer les communications des employés à des fins d’examen par des relecteurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à surveiller les communications au sein de votre organisation, consultez la rubrique [communications Compliance Policies in Microsoft 365](communication-compliance.md).

> [!NOTE]
> Les utilisateurs surveillés par les stratégies de conformité des communications doivent disposer d’une licence de conformité Microsoft 365 E5, d’une licence Office 365 entreprise E3 avec le complément de conformité avancé ou être inclus dans un abonnement Office 365 entreprise E5.
> Si vous ne disposez pas d’un plan entreprise E5 existant et que vous souhaitez essayer la conformité de la communication, vous pouvez vous [inscrire pour obtenir une version d’évaluation d’Office 365 entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).
  
Procédez comme suit pour configurer et utiliser la conformité des communications dans votre organisation Microsoft 365 :
  
- **Étape 1 (facultatif)**: [configurer des groupes pour la conformité de la communication](#step-1-set-up-groups-for-communication-compliance-optional) 

    Avant de commencer à utiliser la conformité de la communication, déterminez qui a besoin des communications vérifiées et qui effectue des révisions. Si vous souhaitez commencer avec quelques utilisateurs seulement pour voir le fonctionnement de la conformité de la communication, vous pouvez ignorer la configuration des groupes pour le moment.

- **Étape 2 (obligatoire)**: [mise à disposition de la conformité de la communication au sein de votre organisation](#step-2-make-communication-compliance-available-in-your-organization-required)

    Ajoutez-vous au rôle d' **administrateur examen de surveillance** afin de pouvoir configurer des stratégies. Vous devrez également créer un groupe avec les rôles **administrateur de révision de surveillance**, **gestion des cas** et **révision** pour les personnes ou les groupes qui adopteront des actions d’enquête et de correction sur les messages avec des correspondances de stratégie. Toute personne disposant de ces rôles peut accéder à la page conformité de la **communication** dans le centre de conformité Microsoft 365. Si la messagerie Reviewable est hébergée sur Exchange Online, chaque réviseur doit disposer [d’un accès à PowerShell à distance à Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/disable-access-to-exchange-online-powershell).

- **Étape 3 (obligatoire)**: [configurer une stratégie de conformité de communication](#step-3-create-a-communication-compliance-policy-required)

    Vous créez des stratégies de conformité de communication dans le centre de conformité Microsoft 365. Ces stratégies définissent les communications qui font l’objet d’un examen dans votre organisation et spécifie qui effectue des révisions. Les communications incluent le courrier électronique, Microsoft Teams, Skype entreprise et les communications de plateformes tierces (par exemple, Facebook, Twitter, etc.).

- **Étape 4 (facultative)**: [créer des modèles de notification d’employé](#step-4-create-employee-notice-templates-optional)

    Créez des modèles d’avis personnalisés pour envoyer des notifications par courrier électronique aux employés sous forme d’option de correction pour les correspondances de stratégie.

- **Étape 5 (facultatif)**: [tester votre stratégie de conformité de communication](#step-5-test-your-communication-compliance-policy-optional)

    Testez votre stratégie de conformité de communication pour vous assurer qu’elle fonctionne comme vous le souhaitez. Il est important de s’assurer que la stratégie de conformité répond à vos normes.

## <a name="step-1-set-up-groups-for-communication-compliance-optional"></a>Étape 1 : configurer des groupes pour la conformité des communications (facultatif)

 Lorsque vous créez une stratégie de conformité de communication, vous définissez les personnes qui ont consulté leurs communications et qui effectue des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont la communication est vérifiée et les groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

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

## <a name="step-2-make-communication-compliance-available-in-your-organization-required"></a>Étape 2 : mise à disposition de la conformité de la communication dans votre organisation (obligatoire)

Pour que la conformité de la **communication** soit disponible sous la forme d’une option de menu dans le centre de conformité Microsoft 365, vous devez disposer du rôle d' **administrateur examen de surveillance** . De plus, pour examiner et corriger les messages avec des correspondances de stratégie, vous devez créer un groupe pour les relecteurs avec les rôles **administrateur de révision de surveillance**, gestion des **cas** et **révision** .

### <a name="create-a-new-role-group"></a>Créer un groupe de rôles

1. Connectez- [https://compliance.microsoft.com](https://compliance.microsoft.com) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Office 365.

2. Dans le centre de conformité Microsoft 365, accédez à **autorisations**. Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez **Créer**.

4. Dans le champ **nom** , attribuez un nom convivial au nouveau groupe de rôles. Sélectionnez **Suivant**.

5. Sélectionnez **choisir les rôles** , puis **Ajouter**. Activez la case à cocher **administrateur de révision de surveillance**, gestion **des** **cas**, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

6. Sélectionnez **choisir les membres** , puis **Ajouter**. Activez la case à cocher de tous les utilisateurs et groupes pour lesquels vous souhaitez créer des stratégies et gérer les messages avec des correspondances de stratégie, puis sélectionnez **Ajouter** et **Terminer**. Sélectionnez **Suivant**.

7. Sélectionnez **créer un groupe de rôles** à terminer.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité](../security/office-365-security/protect-against-threats.md).

## <a name="step-3-create-a-communication-compliance-policy-required"></a>Étape 3 : créer une stratégie de conformité de communication (obligatoire)
  
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
    - Choisissez les utilisateurs ou les groupes à superviser, notamment le choix de tous les utilisateurs de votre organisation, des utilisateurs et des groupes spécifiques, ou d’autres utilisateurs et groupes que vous souhaitez exclure. -
    - Choisissez les relecteurs de la stratégie. Les relecteurs peuvent être des utilisateurs individuels ou des [groupes de sécurité à extension messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#create-a-mail-enabled-security-group). Tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online.
    - Choisissez les canaux de communication à analyser, y compris Exchange, Microsoft teams ou Skype entreprise. Vous choisirez également d’analyser les sources tierces si vous avez configuré un connecteur dans Microsoft 365.
    - Choisissez la direction de communication à surveiller, y compris les communications entrantes, sortantes ou internes.
    - Définir les [conditions](communication-compliance-feature-reference.md#ConditionalSettings)de la stratégie de conformité de communication. Vous pouvez choisir entre une adresse de message, un mot clé, un type de fichier et une condition de correspondance de taille.
    - Choisissez si vous souhaitez inclure des types d’informations sensibles. C’est ici que vous pouvez sélectionner les types d’informations sensibles par défaut et personnalisés. Choisir parmi des types d’informations sensibles personnalisés ou des dictionnaires de mots clés personnalisés existants dans l’Assistant stratégie de conformité des communications, vous pouvez créer ces éléments avant d’exécuter l’Assistant si nécessaire. Si vous le souhaitez, vous pouvez également créer de nouveaux types d’informations sensibles à partir de l’Assistant stratégie de conformité des communications.
    - Choisissez si vous souhaitez activer le modèle de langage offensant. Cette fonctionnalité détecte les langues inappropriées envoyées ou reçues dans le corps des messages électroniques.
    - Définir le pourcentage de communications à réviser.
    - Examinez vos sélections de stratégie et créez la stratégie.

5. Sélectionnez **créer une stratégie** lors de l’utilisation des modèles ou de l' **envoi** lors de l’utilisation de l’Assistant stratégie personnalisée.

6. La page **votre stratégie a été créée** s’affiche avec des instructions sur l’activation de la stratégie et la capture des communications.

## <a name="step-4-create-employee-notice-templates-optional"></a>Étape 4 : créer des modèles de notification d’employé (facultatif)

Si vous souhaitez pouvoir répondre à une alerte de stratégie en envoyant un rappel à l’employé associé, vous devez créer au moins un modèle d’avis dans votre organisation. Les champs de modèle d’avis sont modifiables avant l’envoi dans le cadre du processus de correction des alertes et la création d’un modèle d’avertissement personnalisé pour chaque stratégie de conformité des communications est recommandée.

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

## <a name="step-5-test-your-communication-compliance-policy-optional"></a>Étape 5 : test de votre stratégie de conformité des communications (facultatif)

Une fois que vous avez créé une stratégie de conformité de communication, il est recommandé de tester les conditions que vous avez définies correctement appliquées par la stratégie. Vous pouvez également [tester vos stratégies de protection contre la perte de données (DLP)](create-test-tune-dlp-policy.md) si vos stratégies de conformité de communication incluent des types d’informations sensibles. Assurez-vous que vous laissez vos stratégies s’activer afin que les communications que vous souhaitez tester soient capturées.

Procédez comme suit pour tester votre stratégie de conformité de communication :

1. Ouvrez un client de messagerie ou Microsoft teams connecté en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.
2. Envoyez un message électronique ou une conversation Microsoft teams qui répond aux critères que vous avez définis dans la stratégie de conformité de communication. Il peut s’agir d’un mot clé, d’une taille de pièce jointe, d’un domaine, etc. Assurez-vous que vous déterminez si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop stricts.

    > [!NOTE]
    > Les communications de tous les canaux sources peuvent prendre jusqu’à 24 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité des communications. Accédez à **** > **alertes** de conformité des communications pour afficher les alertes correspondant à vos stratégies.

4. Corrigez l’alerte à l’aide des contrôles de correction et assurez-vous que l’alerte est correctement résolue.
