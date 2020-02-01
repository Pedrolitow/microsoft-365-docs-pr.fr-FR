---
title: Configurer les stratégies de surveillance
description: Configurer la surveillance de la communication pour Office 365
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
titleSuffix: Office 365 Compliance
ms.openlocfilehash: d0bd5411e99471ff326906f65747ec7a6f841545
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41596201"
---
# <a name="configure-supervision-policies-in-office-365"></a>Configurer des stratégies de surveillance dans Office 365

>[!IMPORTANT]
>Cette rubrique s’applique à la configuration des stratégies de surveillance dans un abonnement Office 365. Si vous souhaitez configurer la conformité des communications pour un abonnement Microsoft 365, consultez [la rubrique Configure communications compliance in microsoft 365 (Preview)](communication-compliance-configure.md).

Utilisez des stratégies de surveillance pour capturer les communications des employés à des fins d’examen par des relecteurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de surveillance peuvent vous aider à surveiller les communications au sein de votre organisation, consultez la rubrique [surveillance des stratégies dans Office 365](supervision-policies.md).

>[!NOTE]
>Les utilisateurs surveillés par des stratégies de surveillance doivent disposer d’une licence de conformité Microsoft 365 E5, d’une licence Office 365 entreprise E3 avec le complément de conformité avancé ou être inclus dans un abonnement Office 365 entreprise E5.
>Si vous ne disposez pas d’un plan entreprise E5 existant et que vous souhaitez essayer de contrôler, vous pouvez vous [inscrire pour obtenir une version d’évaluation d’Office 365 entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).
  
Procédez comme suit pour configurer et utiliser la surveillance dans votre organisation Office 365 :
  
- **Étape 1 (facultatif)**: [configurer des groupes pour la surveillance](#step-1-set-up-groups-for-supervision-optional)

    Avant de commencer à utiliser les stratégies de surveillance, déterminez qui a besoin des communications vérifiées et qui effectue des révisions. Si vous souhaitez commencer avec quelques utilisateurs seulement pour voir le fonctionnement de la surveillance, vous pouvez ignorer la configuration des groupes pour le moment.

- **Étape 2 (obligatoire)**: [rendez la surveillance disponible dans votre organisation](#step-2-make-supervision-available-in-your-organization-required)

    Ajoutez-vous au groupe de rôles examen de surveillance afin de pouvoir configurer des stratégies. Tous les utilisateurs auxquels ce rôle est attribué peuvent accéder à la page **surveillance** dans le centre de sécurité et conformité Office 365. Si la messagerie Reviewable est hébergée sur Exchange Online, chaque réviseur doit disposer [d’un accès à PowerShell à distance à Exchange Online](https://docs.microsoft.com/powershell/exchange/exchange-online/disable-access-to-exchange-online-powershell).

- **Étape 3 (facultative)**: [créer des types d’informations sensibles personnalisés et des dictionnaires de mots clés personnalisés](#step-3-create-custom-sensitive-information-types-and-custom-keyword-dictionaries-optional)

    Si vous avez besoin d’un type d’informations sensibles personnalisé ou d’un dictionnaire de mots clés personnalisé pour votre stratégie de surveillance, vous devez le créer avant de démarrer l’Assistant surveillance.

- **Étape 4 (obligatoire)**: [configurer une stratégie de surveillance](#step-4-set-up-a-supervision-policy-required)

    Vous créez des stratégies de surveillance dans le centre de sécurité et conformité Office 365. Ces stratégies définissent les communications qui font l’objet d’un examen dans votre organisation et spécifie qui effectue des révisions. Les communications incluent le courrier électronique et les communications Microsoft Teams, ainsi que les communications de plateformes tierces (par exemple, Facebook, Twitter, etc.). Les stratégies de surveillance créées dans les organisations Office 365 ne sont pas prises en charge dans les abonnements Microsoft 365.

- **Étape 5 (facultatif)**: [test de votre stratégie de supervision de communication](#step-5-test-your-supervision-policy-optional)

    Testez votre stratégie de surveillance pour vous assurer qu’elle fonctionne comme vous le souhaitez. Il est important de s’assurer que la stratégie de conformité répond à vos normes.

## <a name="step-1-set-up-groups-for-supervision-optional"></a>Étape 1 : configurer des groupes pour la surveillance (facultatif)

 Lorsque vous créez une stratégie de surveillance, vous définissez les personnes dont les communications sont analysées et celles qui effectuent des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont les communications sont analysées et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous aurez peut-être besoin de plusieurs. Par exemple, vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui n’est pas supervisé.

Utilisez le tableau suivant pour vous aider à configurer les groupes au sein de votre organisation pour les stratégies de surveillance des communications :

| **Membre de la stratégie** | **Groupes pris en charge** | **Groupes non pris en charge** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs non supervisés | Groupes de distribution <br> Groupes Office 365 | Groupes de distribution dynamique |
| Relecteurs | Groupes de sécurité à extension messagerie  | Groupes de distribution <br> groupes de distribution dynamiques |
  
Lorsque vous sélectionnez un groupe Office 365 pour les utilisateurs supervisés, la stratégie surveille le contenu de la boîte aux lettres Office 365 partagée et les canaux Microsoft teams associés au groupe. Lorsque vous sélectionnez une liste de distribution, la stratégie analyse les boîtes aux lettres des utilisateurs individuels.

Pour gérer les utilisateurs supervisés dans les grandes organisations d’entreprise, il se peut que vous deviez surveiller tous les utilisateurs entre les grands groupes. Vous pouvez utiliser PowerShell pour configurer un groupe de distribution pour une stratégie de surveillance globale pour le groupe affecté. Cela vous permet de surveiller des milliers d’utilisateurs à l’aide d’une seule stratégie et de mettre à jour la stratégie de supervision lorsque de nouveaux employés rejoignent votre organisation.

1. Créez un [groupe de distribution](https://docs.microsoft.com/powershell/module/exchange/users-and-groups/new-distributiongroup?view=exchange-ps) dédié pour votre stratégie de surveillance globale avec les propriétés suivantes : Assurez-vous que ce groupe de distribution n’est pas utilisé à d’autres fins ou d’autres services Office 365.

    - **MemberDepartRestriction = fermé**. Garantit que les utilisateurs ne peuvent pas se supprimer eux-mêmes du groupe de distribution.
    - **MemberJoinRestriction = fermé**. Garantit que les utilisateurs ne peuvent pas s’ajouter eux-mêmes au groupe de distribution.
    - **ModerationEnabled = true**. Garantit que tous les messages envoyés à ce groupe sont soumis à approbation et que le groupe n’est pas utilisé pour communiquer en dehors de la configuration de la stratégie de supervision.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Sélectionnez un [attribut personnalisé Exchange](https://docs.microsoft.com/Exchange/recipients/mailbox-custom-attributes?view=exchserver-2019&viewFallbackFrom=exchonline-ww) inutilisé pour suivre les utilisateurs ajoutés à la stratégie de surveillance dans votre organisation.

3. Exécutez le script PowerShell suivant sur une planification périodique pour ajouter des utilisateurs à la stratégie de surveillance :

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

Pour plus d’informations sur la configuration des groupes, voir :

- [Création et gestion de groupes de distribution](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Gérer les groupes de sécurité à extension de messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups)
- [Vue d’ensemble des groupes Office 365](https://docs.microsoft.com/office365/admin/create-groups/office-365-groups?view=o365-worldwide)

## <a name="step-2-make-supervision-available-in-your-organization-required"></a>Étape 2 : rendez la surveillance disponible dans votre organisation (obligatoire)

Pour que la **surveillance** soit disponible sous la forme d’une option de menu dans le centre de sécurité et de conformité Office 365, vous devez disposer du rôle d’administrateur examen de surveillance.
  
Pour ce faire, vous pouvez vous ajouter en tant que membre du groupe de rôles examen de surveillance, ou vous pouvez créer un groupe de rôles.
  
### <a name="add-members-to-the-supervisory-review-role-group"></a>Ajouter des membres au groupe de rôles examen de surveillance

1. Connectez- [https://protection.office.com](https://protection.office.com) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Office 365.

2. Dans le centre de sécurité et conformité Office 365, accédez à **autorisations**.

3. Sélectionnez le groupe de rôles **examen de surveillance** , puis cliquez sur l’icône modifier.

4. Dans la section **membres** , ajoutez les personnes dont vous souhaitez gérer la surveillance des communications pour votre organisation.

### <a name="create-a-new-role-group"></a>Créer un groupe de rôles

1. Connectez- [https://protection.office.com/permissions](https://protection.office.com/permissions) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Office 365.

2. Dans le centre de sécurité et conformité Office 365, accédez à **autorisations** , puis cliquez sur**+** ajouter ().

3. Dans la section **rôles** , cliquez sur Ajouter**+**() et faites défiler vers le bas jusqu’à administrateur de la **vérification de surveillance**. Ajoutez ce rôle au groupe de rôles.

4. Dans la section **membres** , ajoutez les personnes dont vous souhaitez gérer la surveillance des communications pour votre organisation.

Pour plus d’informations sur les groupes de rôles et les autorisations, consultez [la rubrique autorisations dans le centre de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md).

### <a name="enable-remote-powershell-access-for-reviewers-if-email-is-hosted-on-exchange-online"></a>Activer l’accès à PowerShell à distance pour les relecteurs (si le courrier électronique est hébergé sur Exchange Online)

1. Suivez les instructions [pour activer ou désactiver l’accès à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/disable-access-to-exchange-online-powershell).

## <a name="step-3-create-custom-sensitive-information-types-and-custom-keyword-dictionaries-optional"></a>Étape 3 : créer des types d’informations sensibles personnalisés et des dictionnaires personnels de mots clés personnalisés (facultatif)

Pour sélectionner des types d’informations sensibles personnalisés ou des dictionnaires personnels de mots clés personnalisés dans l’Assistant stratégie de surveillance, vous devez d’abord créer ces éléments si nécessaire.

### <a name="create-custom-keyword-dictionarylexicon-optional"></a>Créer un dictionnaire/Lexique de mots clés personnalisé (facultatif)

Utilisez un éditeur de texte (comme le bloc-notes) pour créer un fichier qui inclut les termes de mots clés que vous souhaitez surveiller dans une stratégie de surveillance. Assurez-vous que chaque terme se trouve sur une ligne distincte et enregistrez le fichier au format **Unicode/UTF-16 (Little endian)** .

### <a name="create-custom-sensitive-information-types"></a>Créer des types d’informations sensibles personnalisés

1. Créez un nouveau type d’informations sensibles et ajoutez votre dictionnaire personnalisé dans le centre de conformité Office 365 Security &. Naviguez jusqu’à **types d’informations sensibles** sur les **classifications** \> et suivez les étapes de l' **Assistant Nouveau type d’informations sensibles**. Ici, vous allez :

    - Définir un nom et une description pour le type d’informations sensibles
    - Définir les éléments de proximité, de niveau de confiance et de modèle principal
    - Importer votre dictionnaire personnalisé en tant que condition requise pour l’élément correspondant
    - Vérifier vos sélections et créer le type d’informations sensibles

    Pour plus d’informations, consultez [la rubrique créer un type d’informations sensibles personnalisé](create-a-custom-sensitive-information-type.md) et [créer un dictionnaire de mots clés](create-a-keyword-dictionary.md)

    Une fois le dictionnaire/lexique personnalisé créé, vous pouvez afficher les mots clés configurés à l’aide de la cmdlet [Get-dlpkeyworddictionary permet](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-dlp/get-dlpkeyworddictionary) ou ajouter et supprimer des termes à l’aide de la cmdlet [Set-dlpkeyworddictionary permet](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance-dlp/set-dlpkeyworddictionary) .

## <a name="step-4-set-up-a-supervision-policy-required"></a>Étape 4 : configurer une stratégie de surveillance (obligatoire)
  
1. Connectez- [https://protection.office.com](https://protection.office.com) vous à l’aide des informations d’identification d’un compte d’administrateur dans votre organisation Office 365.

2. Dans le centre de sécurité et conformité Office 365, sélectionnez **surveillance**.
  
3. Sélectionnez **créer** et suivez l’Assistant pour configurer la configuration de la stratégie. À l’aide de l’Assistant, vous allez :

    - Donnez un nom et une description à la stratégie.
    - Choisissez les utilisateurs ou les groupes à superviser, y compris le choix des utilisateurs ou des groupes que vous souhaitez exclure.
    - Définir les [conditions](supervision-policies.md#ConditionalSettings)de la stratégie de surveillance. Vous pouvez choisir entre une adresse de message, un mot clé, un type de fichier et une condition de correspondance de taille.
    - Choisissez si vous souhaitez inclure des types d’informations sensibles. C’est ici que vous pouvez sélectionner les types d’informations sensibles par défaut et personnalisés.
    - Choisissez si vous souhaitez activer le modèle de langage offensant. Cette fonctionnalité détecte les langues inappropriées envoyées ou reçues dans le corps des messages électroniques.
    - Définir le pourcentage de communications à réviser.
    - Choisissez les relecteurs de la stratégie. Les relecteurs peuvent être des utilisateurs individuels ou des [groupes de sécurité à extension messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#create-a-mail-enabled-security-group). Tous les relecteurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online.
    - Examinez vos sélections de stratégie et créez la stratégie.

## <a name="step-5-test-your-supervision-policy-optional"></a>Étape 5 : test de votre stratégie de supervision (facultatif)

Une fois que vous avez créé une stratégie de supervision de communication, il est recommandé de tester les conditions que vous avez définies correctement appliquées par la stratégie. Vous pouvez également [tester vos stratégies de protection contre la perte de données (DLP)](create-test-tune-dlp-policy.md) si vos stratégies de surveillance incluent des types d’informations sensibles. Suivez les étapes ci-dessous pour tester votre stratégie de supervision :

1. Ouvrez un client de messagerie ou Microsoft teams connecté en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.
2. Envoyez un message électronique ou une conversation Microsoft teams qui répond aux critères que vous avez définis dans la stratégie de supervision. Il peut s’agir d’un mot clé, d’une taille de pièce jointe, d’un domaine, etc. Assurez-vous que vous déterminez si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop stricts.

    >[!NOTE]
    >Les e-mails soumis à des stratégies définies sont traités en temps réel et peuvent être testés immédiatement après la configuration de la stratégie. Les conversations dans Microsoft teams peuvent prendre jusqu’à 24 heures pour être entièrement traitées dans une stratégie. 

3. Connectez-vous à votre client Office 365 en tant que réviseur désigné dans la stratégie de surveillance des communications. Accédez à **surveillance** > de*votre stratégie* > personnalisée pour afficher le rapport de**la stratégie.**

