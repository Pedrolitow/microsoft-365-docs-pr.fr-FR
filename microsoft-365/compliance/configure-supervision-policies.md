---
title: Configurer des stratégies de surveillance
description: Configurez des stratégies de surveillance des communications dans Office 365 pour capturer les communications des employés à des examens par des réviseurs internes ou externes.
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
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 74244b5288043a1d1bc62e0ae09ee8c25ff7d4e1
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47546776"
---
# <a name="configure-supervision-policies-in-office-365"></a>Configurer des stratégies de surveillance dans Office 365

>[!IMPORTANT]
>Suite à la publication de la conformité des communications dans la conformité Microsoft 365 en février 2020, la surveillance dans Office 365 est retirée. Les stratégies de surveillance ne seront plus disponibles pour la création et les stratégies seront finalement supprimées, après une période prolongée d’accès en lecture seule.
>
>Si vous utilisez la surveillance, sachez que :
>
>- À compter du 15 juin 2020, les locataires n’auront pas la possibilité de créer de nouvelles stratégies de surveillance.
>- À compter du 31 août 2020, les stratégies existantes arrêteront la capture de nouveaux messages.
>- À compter du 26 octobre 2020, les stratégies existantes seront supprimées.
>
>Nous encourageons activement les clients qui explorent ou utilisent actuellement la surveillance dans Office 365 à utiliser la nouvelle solution de conformité des [communications](communication-compliance.md) pour répondre à vos exigences réglementaires ou de surveillance des communications avec un ensemble beaucoup plus riche de fonctionnalités intelligentes.

Utilisez des stratégies de surveillance pour capturer les communications des employés à des examens par des réviseurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de surveillance peuvent vous aider à surveiller les communications dans votre organisation, voir stratégies de [surveillance dans Office 365](supervision-policies.md).

>[!NOTE]
>Les utilisateurs surveillés par des stratégies de surveillance doivent avoir une licence de conformité Microsoft 365 E5, une licence Office 365 Entreprise E3 avec le module de conformité avancée, être inclus dans un abonnement Office 365 Entreprise E5 ou être inclus dans un abonnement Microsoft 365 E5.
>Si vous n’avez pas d’offre Entreprise E5 existante et que vous souhaitez essayer la supervision, vous pouvez vous inscrire à une version d’essai [d’Office 365 Entreprise E5](https://go.microsoft.com/fwlink/p/?LinkID=698279).
  
Suivez ces étapes pour configurer et utiliser la surveillance dans votre organisation :
  
- **Étape 1 (facultative)**: [Configurer des groupes pour la supervision](#step-1-set-up-groups-for-supervision-optional)

    Avant de commencer à utiliser des stratégies de surveillance, déterminez qui a besoin de révision des communications et qui effectue les révisions. Si vous souhaitez commencer avec quelques utilisateurs seulement pour voir comment fonctionne la supervision, vous pouvez ignorer la configuration des groupes pour le moment.

- **Étape 2 (obligatoire)**: rendre [la surveillance disponible dans votre organisation](#step-2-make-supervision-available-in-your-organization-required)

    Ajoutez-vous au groupe de rôles De surveillance afin de pouvoir configurer des stratégies. Toute personne à qui ce rôle est attribué peut accéder à la page **supervision** dans le Centre de sécurité & conformité. Si les e-mails révisionnables sont hébergés sur Exchange Online, chaque réviseur doit avoir un accès PowerShell distant [à Exchange Online.](https://docs.microsoft.com/powershell/exchange/disable-access-to-exchange-online-powershell)

- **Étape 3 (facultative)**: créer des types d’informations sensibles personnalisés [et des dictionnaires de mots clés personnalisés](#step-3-create-custom-sensitive-information-types-and-custom-keyword-dictionaries-optional)

    Si vous avez besoin d’un type d’informations sensibles personnalisé ou d’un dictionnaire de mots clés personnalisé pour votre stratégie de surveillance, vous devez le créer avant de démarrer l’Assistant supervision.

- **Étape 4 (obligatoire)**: [configurer une stratégie de surveillance](#step-4-set-up-a-supervision-policy-required)

    Vous créez des stratégies de surveillance dans le Centre de sécurité & conformité. Ces stratégies définissent les communications qui sont sujettes à révision dans votre organisation et spécifient qui effectue les révisions. Les communications incluent la messagerie électronique et les communications Microsoft Teams, ainsi que les communications de plateforme tierce (par exemple, Facebook, Twitter, etc.). Les stratégies de surveillance créées dans les organisations ne sont pas pris en charge dans la surveillance des communications dans les abonnements Microsoft 365.

- **Étape 5 (facultative)**: [Tester votre stratégie de surveillance des communications](#step-5-test-your-supervision-policy-optional)

    Testez votre stratégie de surveillance pour vous assurer qu’elle fonctionne comme vous le souhaitez. Il est important de s’assurer que votre stratégie de conformité est conforme à vos normes.

## <a name="step-1-set-up-groups-for-supervision-optional"></a>Étape 1 : Configurer des groupes pour la surveillance (facultatif)

 Lorsque vous créez une stratégie de surveillance, vous définissez les personnes dont les communications sont analysées et celles qui effectuent des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont les communications sont analysées et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous en aurez peut-être besoin de plusieurs. Par exemple, vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui ne sera pas supervisé.

Utilisez le graphique suivant pour vous aider à configurer les groupes de votre organisation pour les stratégies de surveillance des communications :

| **Membre de la stratégie** | **Groupes pris en charge** | **Groupes non pris en place** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs non supervisés | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique |
| Relecteurs | Groupes de sécurité à extension messagerie  | Groupes de distribution <br> groupes de distribution dynamiques |
  
Lorsque vous sélectionnez un groupe Microsoft 365 pour les utilisateurs supervisés, la stratégie surveille le contenu de la boîte aux lettres partagée et les canaux Microsoft Teams associés au groupe. Lorsque vous sélectionnez une liste de distribution, la stratégie surveille les boîtes aux lettres utilisateur individuelles.

Pour gérer les utilisateurs supervisés dans les grandes entreprises, vous devrez peut-être surveiller tous les utilisateurs de grands groupes. Vous pouvez utiliser PowerShell pour configurer un groupe de distribution pour une stratégie de surveillance globale pour le groupe affecté. Cela vous permet de surveiller des milliers d’utilisateurs avec une stratégie unique et de maintenir la stratégie de surveillance à jour lorsque de nouveaux employés rejoignent votre organisation.

1. Créez un groupe de [distribution](https://docs.microsoft.com/powershell/module/exchange/new-distributiongroup) dédié pour votre stratégie de surveillance globale avec les propriétés suivantes : Assurez-vous que ce groupe de distribution n’est pas utilisé à d’autres fins ou à d’autres services Office 365.

    - **MemberDepartRestriction = Fermé**. Garantit que les utilisateurs ne peuvent pas se supprimer eux-mêmes du groupe de distribution.
    - **MemberJoinRestriction = Closed**. Garantit que les utilisateurs ne peuvent pas s’ajouter eux-mêmes au groupe de distribution.
    - **ModerationEnabled = True**. Garantit que tous les messages envoyés à ce groupe sont soumis à approbation et que le groupe n’est pas utilisé pour communiquer en dehors de la configuration de la stratégie de surveillance.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Sélectionnez un attribut personnalisé [Exchange inutilisé pour](https://docs.microsoft.com/Exchange/recipients/mailbox-custom-attributes?view=exchserver-2019&viewFallbackFrom=exchonline-ww) suivre les utilisateurs ajoutés à la stratégie de surveillance dans votre organisation.

3. Exécutez le script PowerShell suivant selon une planification périodique pour ajouter des utilisateurs à la stratégie de surveillance :

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

Pour plus d’informations sur la configuration des groupes, voir :

- [Création et gestion de groupes de distribution](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Gérer les groupes de sécurité à extension de messagerie](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups)
- [Vue d’ensemble des groupes Microsoft 365](https://docs.microsoft.com/office365/admin/create-groups/office-365-groups?view=o365-worldwide)

## <a name="step-2-make-supervision-available-in-your-organization-required"></a>Étape 2 : Rendre la surveillance disponible dans votre organisation (obligatoire)

Pour rendre **la surveillance** disponible en tant qu’option de menu dans le Centre de sécurité & conformité, vous devez avoir le rôle Administrateur de vérification de surveillance.
  
Pour ce faire, vous pouvez soit vous ajouter en tant que membre du groupe de rôles De surveillance, soit créer un groupe de rôles.
  
### <a name="add-members-to-the-supervisory-review-role-group"></a>Ajouter des membres au groupe de rôles Révision de surveillance

1. Connectez-vous [https://protection.office.com](https://protection.office.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre de sécurité & conformité, allez à **Autorisations.**

3. Sélectionnez le **groupe de rôles De surveillance,** puis cliquez sur l’icône Modifier.

4. Dans la section **Membres,** ajoutez les personnes qui vous souhaitez gérer la surveillance des communications pour votre organisation.

### <a name="create-a-new-role-group"></a>Créer un groupe de rôles

1. Connectez-vous [https://protection.office.com/permissions](https://protection.office.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre de sécurité & conformité, allez sur **Autorisations,** puis cliquez sur Ajouter ( **+** ).

3. Dans la section **Rôles,** cliquez sur Ajouter ( ) et faites défiler vers le bas **+** jusqu’à Administrateur de la révision de **surveillance.** Ajoutez ce rôle au groupe de rôles.

4. Dans la section **Membres,** ajoutez les personnes qui vous souhaitez gérer la surveillance des communications pour votre organisation.

Pour plus d’informations sur les groupes de rôles et les [autorisations, voir Autorisations dans le Centre de conformité.](../security/office-365-security/permissions-in-the-security-and-compliance-center.md)

### <a name="enable-remote-powershell-access-for-reviewers-if-email-is-hosted-on-exchange-online"></a>Activer l’accès PowerShell à distance pour les réviseurs (si le courrier électronique est hébergé sur Exchange Online)

1. Suivez les instructions dans [Activer ou désactiver l’accès à Exchange Online PowerShell.](https://docs.microsoft.com/powershell/exchange/disable-access-to-exchange-online-powershell)

## <a name="step-3-create-custom-sensitive-information-types-and-custom-keyword-dictionaries-optional"></a>Étape 3 : Créer des types d’informations sensibles personnalisés et des dictionnaires de mots clés personnalisés (facultatif)

Pour choisir parmi des types d’informations sensibles personnalisés existants ou des dictionnaires de mots clés personnalisés dans l’Assistant stratégie de surveillance, vous devez d’abord créer ces éléments si nécessaire.

### <a name="create-custom-keyword-dictionarylexicon-optional"></a>Créer un dictionnaire de mots clés/lexicon personnalisé (facultatif)

Utilisez un éditeur de texte (tel que le Bloc-notes) pour créer un fichier qui inclut les termes de mot clé que vous souhaitez surveiller dans une stratégie de surveillance. Assurez-vous que chaque terme se trouve sur une ligne distincte et enregistrez le fichier au format **Unicode/UTF-16 (Little Endian).**

### <a name="create-custom-sensitive-information-types"></a>Créer des types d’informations sensibles personnalisés

1. Créez un type d’informations sensibles et ajoutez votre dictionnaire personnalisé dans le Centre de sécurité & conformité. Accédez à **Classifications** Types d’informations sensibles et suivez les étapes de \>  l’Assistant **Nouveau type d’informations sensibles.** Ici, vous allez :

    - Définir un nom et une description pour le type d’informations sensibles
    - Définir les éléments de proximité, de niveau de confiance et de modèle principal
    - Importer votre dictionnaire personnalisé comme condition requise pour l’élément correspondant
    - Passer en revue vos sélections et créer le type d’informations sensibles

    Pour plus d’informations, voir [Créer un type d’informations sensibles](create-a-custom-sensitive-information-type.md) personnalisé et [Créer un dictionnaire de mots clés](create-a-keyword-dictionary.md)

    Une fois le dictionnaire/lexicon personnalisé créé, vous pouvez afficher les mots clés configurés avec la cmdlet [Get-DlpKeywordDictionary](https://docs.microsoft.com/powershell/module/exchange/get-dlpkeyworddictionary) ou ajouter et supprimer des termes à l’aide de la cmdlet [Set-DlpKeywordDictionary.](https://docs.microsoft.com/powershell/module/exchange/set-dlpkeyworddictionary)

## <a name="step-4-set-up-a-supervision-policy-required"></a>Étape 4 : Configurer une stratégie de surveillance (obligatoire)
  
1. Connectez-vous [https://protection.office.com](https://protection.office.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre de sécurité & conformité, sélectionnez **Supervision**.
  
3. Sélectionnez **Créer** et suivre l’Assistant pour configurer la configuration de la stratégie. À l’aide de l’Assistant, vous allez :

    - Donnez un nom et une description à la stratégie.
    - Choisissez les utilisateurs ou les groupes à superviser, y compris le choix des utilisateurs ou des groupes que vous souhaitez exclure.
    - Définissez les conditions de stratégie [de surveillance.](supervision-policies.md#ConditionalSettings) Vous pouvez choisir entre l’adresse du message, le mot clé, les types de fichiers et les conditions de correspondance de taille.
    - Choisissez si vous souhaitez inclure des types d’informations sensibles. C’est ici que vous pouvez sélectionner les types d’informations sensibles par défaut et personnalisés.
    - Choisissez si vous souhaitez activer le modèle de langage choquant. Cela détecte une langue inappropriée envoyée ou reçue dans le corps des messages électroniques.
    - Définissez le pourcentage de communications à réviser.
    - Choisissez les réviseurs pour la stratégie. Les réviseurs peuvent être des utilisateurs individuels ou des groupes de [sécurité à messagerie.](https://docs.microsoft.com/Exchange/recipients-in-exchange-online/manage-mail-enabled-security-groups#create-a-mail-enabled-security-group) Tous les réviseurs doivent avoir des boîtes aux lettres hébergées sur Exchange Online.
    - Examinez vos sélections de stratégie et créez la stratégie.

## <a name="step-5-test-your-supervision-policy-optional"></a>Étape 5 : Tester votre stratégie de surveillance (facultatif)

Après avoir créé une stratégie de surveillance des communications, il est bon de tester pour vous assurer que les conditions que vous avez définies sont correctement appliquées par la stratégie. Vous pouvez également tester vos stratégies de protection contre la perte de données [(DLP)](create-test-tune-dlp-policy.md) si vos stratégies de surveillance incluent des types d’informations sensibles. Suivez ces étapes pour tester votre stratégie de surveillance :

1. Ouvrez un client de messagerie ou Microsoft Teams connecté en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.
2. Envoyez un courrier électronique ou une conversation Microsoft Teams qui répond aux critères que vous avez définis dans la stratégie de surveillance. Il peut s’agit d’un mot clé, d’une taille de pièce jointe, d’un domaine, etc. Veillez à déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop peu restrictifs.

    >[!NOTE]
    >Les e-mails soumis à des stratégies définies sont traitées en temps quasi réel et peuvent être testés immédiatement après la configuration de la stratégie. Les conversations dans Microsoft Teams peuvent prendre jusqu’à 24 heures pour être entièrement traitées dans une stratégie. 

3. Connectez-vous à Microsoft 365 en tant que réviseur désigné dans la stratégie de surveillance des communications. Accédez à **Supervision**  >  *your Custom Policy*  >  **Open** to view the report for the policy.

