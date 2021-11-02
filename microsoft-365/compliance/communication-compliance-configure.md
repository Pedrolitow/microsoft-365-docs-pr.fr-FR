---
title: Prise en main de la conformité des communications
description: Configurez des stratégies de conformité des communications pour configurer les communications des utilisateurs en vue de leur révision.
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
search.appverid:
- MET150
- MOE150
ms.openlocfilehash: c58df514c136c6df2db5d1392a57db1ee6c34bb3
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60647430"
---
# <a name="get-started-with-communication-compliance"></a>Prise en main de la conformité des communications

Utiliser des stratégies de conformité des communications pour identifier les communications des utilisateurs à des examens par des réviseurs internes ou externes. Pour plus d’informations sur la façon dont les stratégies de conformité des communications peuvent vous aider à surveiller les communications dans votre organisation, consultez les stratégies de conformité des [communications dans Microsoft 365](communication-compliance.md). Si vous souhaitez examiner comment Contoso a configuré rapidement une stratégie de conformité des communications pour surveiller le contenu inapproprié dans les communications Microsoft Teams, Exchange Online et Yammer, consultez cette étude de [cas.](communication-compliance-case-study.md)

## <a name="subscriptions-and-licensing"></a>Abonnements et licences

Avant de commencer à vous conformer à la conformité des communications, vous devez confirmer votre abonnement [Microsoft 365 et](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) les modules. Pour accéder à la conformité des communications et l’utiliser, votre organisation doit avoir l’un des abonnements ou modules suivants :

- Microsoft 365 E5 abonnement (version payante ou d’essai)
- Microsoft 365 E3 abonnement + le module Microsoft 365 E5 Conformité’abonnement
- Microsoft 365 E3 abonnement + le module Microsoft 365 E5 gestion des risques internes
- Microsoft 365 A5 abonnement (version payante ou d’essai)
- Microsoft 365 A3 abonnement + le module Microsoft 365 A5 conformité de l’application
- Microsoft 365 A3 abonnement + le module Microsoft 365 A5 gestion des risques internes
- Abonnement Microsoft 365 G5 (version payante ou d’essai)
- Microsoft 365 Abonnement G5 + module Microsoft 365 conformité G5
- Microsoft 365 Abonnement G5 + module Microsoft 365 G5 Gestion des risques internes
- Office 365 Entreprise Abonnement E5 (version payante ou d’essai)
- Office 365 A5 abonnement (version payante ou d’essai)
- Office 365 Entreprise Abonnement E3 + module Conformité avancée Office 365 de service (non disponible pour les nouveaux abonnements, voir la remarque)

L’une des licences ci-dessus doit être attribuée aux utilisateurs inclus dans les stratégies de conformité des communications.

> [!IMPORTANT]
> Conformité avancée Office 365 n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contient les mêmes fonctionnalités de conformité ou des fonctionnalités supplémentaires.

Si vous n’avez pas de plan Office 365 Entreprise E5 et que vous souhaitez essayer la conformité des [](https://www.microsoft.com/microsoft-365/enterprise) communications, vous pouvez ajouter des [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement existant ou vous inscrire à une version d’essai de Office 365 Entreprise E5.

## <a name="recommended-actions-preview"></a>Actions recommandées (aperçu)

Les actions recommandées peuvent aider votre organisation à utiliser au mieux les fonctionnalités de conformité des communications et vos stratégies existantes. Incluses dans la page **Vue** d’ensemble, les actions recommandées fournissent des informations et résument les types d’informations sensibles et les activités de contenu inappropriées dans les communications de votre organisation.

![Actions recommandées pour la conformité des communications.](../media/communication-compliance-recommended-actions.png)

L’activité dans les messages contenant du contenu inapproprié est éumée par type de classifieur à partir de stratégies existantes qui utilisent le modèle de contenu inapproprié ou des stratégies personnalisées qui utilisent des classifieurs pour du contenu inapproprié. Examinez les alertes pour ces messages dans le tableau de bord d’alerte pour vos stratégies.

L’activité impliquant des types d’informations sensibles est détectée dans les messages couverts par les stratégies existantes et pour les messages qui ne sont pas couverts par les stratégies existantes. Informations sont fournis pour tous les types d’informations sensibles, y compris ceux que votre organisation n’a pas précédemment définis dans une stratégie de conformité des communications existante. Utilisez ces informations pour créer une stratégie de conformité des communications ou pour mettre à jour les stratégies existantes.

## <a name="step-1-required-enable-permissions-for-communication-compliance"></a>Étape 1 (obligatoire) : activer les autorisations pour la conformité des communications

> [!IMPORTANT]
> Par défaut, les administrateurs globaux n’ont pas accès aux fonctionnalités de conformité des communications. Les rôles attribués au cours de cette étape sont requis pour que les fonctionnalités de conformité des communications soient accessibles. Après avoir configuré vos groupes de rôles, l’application des autorisations de groupe de rôles aux utilisateurs affectés au sein de votre organisation peut prendre jusqu’à 30 minutes.

Il existe cinq groupes de rôles utilisés pour configurer les autorisations pour gérer les fonctionnalités de conformité des communications. Pour rendre **la conformité des** communications disponible en tant qu’option de menu dans  Centre de conformité Microsoft 365  et pour poursuivre ces étapes de configuration, vous devez être affecté aux groupes de rôles Conformité des communications ou Administrateur de la conformité des communications. Pour accéder aux fonctionnalités de conformité des communications et les gérer après la configuration initiale, les utilisateurs doivent être membres d’au moins un groupe de rôles de conformité des communications.

Selon la façon dont vous souhaitez gérer les stratégies de communication et les alertes, vous devez affecter des utilisateurs à des groupes de rôles spécifiques. Vous avez la possibilité d’affecter des utilisateurs ayant différentes responsabilités de conformité à des groupes de rôles spécifiques pour gérer différents domaines des fonctionnalités de conformité des communications. Vous pouvez également décider d’affecter tous les comptes d’utilisateur pour les  administrateurs, analystes, enquêteurs et visionneuses désignés au groupe de rôles Conformité des communications. Utilisez un ou plusieurs groupes de rôles pour mieux vous adapter à vos exigences de gestion de la conformité.

Choisissez parmi ces options de groupe de rôles lors de la configuration de la conformité des communications :

| Rôle | Autorisations de rôle |
|:-----|:-----|
| **Conformité des communications** | Utilisez ce groupe de rôles pour gérer la conformité des communications pour votre organisation au sein d’un seul groupe. En ajoutant tous les comptes d’utilisateur pour les administrateurs, analystes, enquêteurs et visionneuses désignés, vous pouvez configurer les autorisations de conformité des communications dans un seul groupe. Ce groupe de rôles contient tous les rôles d’autorisation de conformité des communications. Cette configuration est le moyen le plus simple de se lancer rapidement dans la conformité des communications et convient parfaitement aux organisations qui n’ont pas besoin d’autorisations distinctes définies pour des groupes d’utilisateurs distincts. |
| **Administrateur de conformité des communications** | Utilisez ce groupe de rôles pour configurer initialement la conformité des communications, puis séparez les administrateurs de conformité des communications dans un groupe défini. Les utilisateurs affectés à ce groupe de rôles peuvent créer, lire, mettre à jour et supprimer des stratégies de conformité des communications, des paramètres globaux et des attributions de groupe de rôles. Les utilisateurs affectés à ce groupe de rôles ne peuvent pas afficher les alertes de message. |
| **Analyste de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’analystes de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les stratégies où ils sont affectés en tant que réviseurs, afficher les métadonnées des messages (et non le contenu du message), passer à des réviseurs supplémentaires ou envoyer des notifications aux utilisateurs. Les analystes ne peuvent pas résoudre les alertes en attente. |
| **Enquêteur de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui agira en tant qu’enquêteurs de conformité des communications. Les utilisateurs affectés à ce groupe de rôles peuvent afficher les métadonnées et le contenu des messages, passer à des réviseurs supplémentaires, passer à un cas Advanced eDiscovery, envoyer des notifications aux utilisateurs et résoudre l’alerte. |
| **Visionneuse de conformité des communications** | Utilisez ce groupe pour attribuer des autorisations aux utilisateurs qui gèreront les rapports de communication. Les utilisateurs affectés à ce groupe de rôles peuvent accéder à tous les widgets de rapports sur la page d’accueil de conformité des communications et peuvent afficher tous les rapports de conformité des communications. |

### <a name="option-1-assign-all-compliance-users-to-the-communication-compliance-role-group"></a>Option 1 : Affecter tous les utilisateurs de conformité au groupe de rôles Conformité des communications

1. Connectez-vous [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans le Centre &amp; de conformité de sécurité, allez à **Autorisations.** Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez le *groupe de rôles Conformité* des communications, puis **Modifiez le groupe de rôles.**

4. Sélectionnez **Choisir des membres** dans le volet de navigation de gauche, puis sélectionnez **Modifier.**

5. Sélectionnez **Ajouter,** puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de *rôles* Conformité des communications.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles. Sélectionnez **Fermer** pour effectuer les étapes

### <a name="option-2-assign-users-to-specific-communication-compliance-role-groups"></a>Option 2 : Affecter des utilisateurs à des groupes de rôles de conformité des communications spécifiques

Utilisez cette option pour affecter des utilisateurs à des groupes de rôles spécifiques afin de segmenter l’accès à la conformité des communications et les responsabilités entre les différents utilisateurs de votre organisation.

1. Connectez-vous [https://compliance.microsoft.com/permissions](https://compliance.microsoft.com/permissions) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans le Centre &amp; de conformité de sécurité, allez à **Autorisations.** Sélectionnez le lien pour afficher et gérer les rôles dans Office 365.

3. Sélectionnez l’un des groupes de rôles de conformité des communications, puis **sélectionnez Modifier le groupe de rôles.**

4. Sélectionnez **Choisir des membres** dans le volet de navigation de gauche, puis sélectionnez **Modifier.**

5. Sélectionnez **Ajouter,** puis cochez la case pour tous les utilisateurs que vous souhaitez ajouter au groupe de rôles.

6. Sélectionnez **Ajouter**, puis **Terminé**.

7. Sélectionnez **Enregistrer** pour ajouter les utilisateurs au groupe de rôles.

8. Sélectionnez le groupe de rôles de conformité des communications suivant, puis répétez les étapes 4 à 7 pour chaque groupe de rôles requis.

9. Sélectionnez **Fermer** pour effectuer les étapes.

Pour plus d’informations sur les groupes de rôles et les [autorisations, voir Autorisations dans le Centre de conformité.](../security/office-365-security/protect-against-threats.md)

## <a name="step-2-required-enable-the-audit-log"></a>Étape 2 (obligatoire) : activer le journal d’audit

La conformité des communications nécessite des journaux d’audit pour afficher les alertes et suivre les mesures correctives prises par les réviseurs. Les journaux d’audit sont un résumé de toutes les activités associées à une stratégie organisationnelle définie ou à chaque modification d’une stratégie de conformité des communications.

L’audit est activé pour les Microsoft 365 par défaut. Certaines organisations peuvent avoir désactivé l’audit pour des raisons spécifiques. Si l’audit est désactivé pour votre organisation, c’est peut-être parce qu’un autre administrateur l’a désactivé. Nous vous recommandons de confirmer qu’il est acceptable de remettre l’audit en marche lorsque vous terminez cette étape.

Pour obtenir des instructions détaillées sur l’activer, voir Activer ou désactiver la recherche dans le journal [d’audit.](turn-audit-log-search-on-or-off.md) Une fois l’audit activé, le message qui apparaît indique que le journal d’audit est en cours de préparation et que vous pourrez effectuer une recherche environ deux heures après la fin de la préparation. Vous ne devez faire cette action qu’une seule fois. Pour plus d’informations sur l’utilisation du journal d’audit, voir [Rechercher dans le journal d’audit.](search-the-audit-log-in-security-and-compliance.md)

## <a name="step-3-optional-set-up-groups-for-communication-compliance"></a>Étape 3 (facultative) : configurer des groupes pour la conformité des communications

 Lorsque vous créez une stratégie de conformité des communications, vous définissez les personnes dont les communications sont examinées et celles qui effectuent des révisions. Dans la stratégie, vous utiliserez des adresses de messagerie pour identifier des individus ou des groupes de personnes. Pour simplifier votre configuration, vous pouvez créer des groupes pour les personnes dont les communications sont examinées et des groupes pour les personnes qui examinent ces communications. Si vous utilisez des groupes, vous en aurez peut-être besoin de plusieurs. Par exemple, si vous souhaitez surveiller les communications entre deux groupes distincts de personnes ou si vous souhaitez spécifier un groupe qui ne sera pas supervisé.

Utilisez le graphique suivant pour vous aider à configurer les groupes de votre organisation pour les stratégies de conformité des communications :

| **Membre de la stratégie** | **Groupes pris en charge** | **Groupes non pris en place** |
|:-----|:-----|:-----|
|Utilisateurs supervisés <br> Utilisateurs exclus | Groupes de distribution <br> Groupes Microsoft 365 | Groupes de distribution dynamique <br> Groupes de distribution imbrmbrés <br> Groupes de sécurité à extension messagerie <br> Microsoft 365 groupes avec appartenance dynamique |
| Relecteurs | Aucun changement | Groupes de distribution <br> groupes de distribution dynamiques <br> Groupes de distribution imbrmbrés <br> Groupes de sécurité à extension messagerie |

Lorsque vous affectez un groupe de distribution dans la stratégie, la stratégie surveille tous les messages électroniques et Teams conversations de chaque utilisateur dans le groupe de distribution. Lorsque vous affectez un groupe Microsoft 365 dans la stratégie, la stratégie surveille tous les messages électroniques et les conversations Teams envoyées à ce groupe, et non les messages électroniques et conversations individuels reçus par chaque membre du groupe.

Si vous êtes une organisation avec un déploiement Exchange local ou un fournisseur de messagerie externe et que vous souhaitez surveiller les conversations Microsoft Teams pour vos utilisateurs, vous devez créer un groupe de distribution pour les utilisateurs avec des boîtes aux lettres externes ou sur site à surveiller. Plus loin dans ces étapes, vous  allez affecter ce groupe de distribution en tant que sélection d’utilisateurs et de groupes Supervisés dans l’Assistant Stratégie. Pour plus d’informations sur les exigences et les limitations relatives à l’activation de la prise en charge du stockage en nuage et de la Teams pour les utilisateurs locaux, voir Rechercher des données de conversation Teams pour les [utilisateurs](search-cloud-based-mailboxes-for-on-premises-users.md)locaux.

Pour gérer les utilisateurs supervisés dans les grandes entreprises, vous devrez peut-être surveiller tous les utilisateurs de grands groupes. Vous pouvez utiliser PowerShell pour configurer un groupe de distribution pour une stratégie de conformité des communications globale pour le groupe affecté. Cela vous permet de surveiller des milliers d’utilisateurs avec une stratégie unique et de maintenir la stratégie de conformité des communications à jour lorsque de nouveaux employés rejoignent votre organisation.

1. Créez un groupe de distribution dédié pour votre stratégie de conformité des communications globales avec les propriétés suivantes : Assurez-vous que ce groupe de [distribution](/powershell/module/exchange/new-distributiongroup) n’est pas utilisé à d’autres fins ou à d’autres Office 365 services.

    - **MemberDepartRestriction = Fermé**. Garantit que les utilisateurs ne peuvent pas se supprimer eux-mêmes du groupe de distribution.
    - **MemberJoinRestriction = Closed**. Garantit que les utilisateurs ne peuvent pas s’ajouter eux-mêmes au groupe de distribution.
    - **ModerationEnabled = True**. Garantit que tous les messages envoyés à ce groupe sont soumis à approbation et que le groupe n’est pas utilisé pour communiquer en dehors de la configuration de la stratégie de conformité des communications.

    ```PowerShell
    New-DistributionGroup -Name <your group name> -Alias <your group alias> -MemberDepartRestriction 'Closed' -MemberJoinRestriction 'Closed' -ModerationEnabled $true
    ```

2. Sélectionnez un attribut personnalisé Exchange [inutilisé](/Exchange/recipients/mailbox-custom-attributes) pour suivre les utilisateurs ajoutés à la stratégie de conformité des communications dans votre organisation.

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

Pour plus d’informations sur la configuration des groupes, voir :

- [Création et gestion de groupes de distribution](/Exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups)
- [Vue d’ensemble Microsoft 365 groupes](/office365/admin/create-groups/office-365-groups)

## <a name="step-4-optional-verify-your-yammer-tenant-is-in-native-mode"></a>Étape 4 (facultative) : vérifiez que votre client Yammer est en mode natif

En mode natif, tous les Yammer utilisateurs sont en Azure Active Directory (Azure AD), tous les groupes sont des groupes Office 365 et tous les fichiers sont stockés dans SharePoint Online. Votre client Yammer doit être en mode natif pour les stratégies de conformité des communications afin d’analyser et d’identifier les conversations à risque dans les messages privés et les conversations de la communauté Yammer.

Pour plus d’informations sur la configuration Yammer en mode natif, voir :

- [Vue d’Yammer mode natif dans Microsoft 365](/yammer/configure-your-yammer-network/overview-native-mode)
- [Configurer votre réseau Yammer en mode natif pour Microsoft 365](/yammer/configure-your-yammer-network/native-mode)

## <a name="step-5-required-create-a-communication-compliance-policy"></a>Étape 5 (obligatoire) : créer une stratégie de conformité des communications

>[!IMPORTANT]
>L’utilisation de PowerShell pour créer et gérer les stratégies de conformité des communications n’est pas prise en charge. Pour créer et gérer ces stratégies, vous devez utiliser les contrôles de gestion des stratégies dans la [solution Microsoft 365 conformité des communications.](https://compliance.microsoft.com/supervisoryreview)

>[!TIP]  
>Vous souhaitez consulter une walkthrough détaillée de la configuration d’une nouvelle stratégie de conformité des communications et de la correction d’une alerte ? Regardez cette vidéo de [15 minutes](communication-compliance-plan.md#creating-a-communication-compliance-policy-walkthrough) pour voir une démonstration de la façon dont les stratégies de conformité des communications peuvent vous aider à détecter les messages inappropriés, à examiner les violations potentielles et à résoudre les problèmes de conformité.

1. Connectez-vous <https://compliance.microsoft.com> à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, sélectionnez **Conformité des communications.**

3. Cliquez sur l'onglet **Stratégies**.

4. Sélectionnez **Créer une** stratégie pour créer et configurer une nouvelle stratégie à partir d’un modèle ou pour créer et configurer une stratégie personnalisée.

    Si vous choisissez un modèle de stratégie pour créer une stratégie, vous devez :

    - Confirmez ou mettez à jour le nom de la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.

    - Choisissez les utilisateurs ou les groupes à superviser, y compris le choix des utilisateurs ou des groupes que vous souhaitez exclure. Lorsque vous utilisez le modèle de conflit d’intérêts, vous sélectionnez deux groupes ou deux utilisateurs à surveiller pour les communications internes.

    - Choisissez les réviseurs pour la stratégie. Les réviseurs sont des utilisateurs individuels et tous les réviseurs doivent avoir des boîtes aux lettres hébergées Exchange Online. Les réviseurs ajoutés ici sont les relecteurs parmi qui vous pouvez choisir lors de l’escalade d’une alerte dans le flux de travail d’examen et de correction. Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.

    - Choisissez un champ de condition limité, généralement un type d’informations sensibles ou un dictionnaire de mots clés à appliquer à la stratégie.

    > [!NOTE]
    > Si vous souhaitez activer la reconnaissance optique de caractères [(OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) pour analyser les images incorporées ou jointes dans les messages pour le texte imprimé ou manuscrit qui correspond aux conditions de stratégie, sélectionnez Personnaliser les conditions de stratégie et le pourcentage et activer l’extraction du texte imprimé ou manuscrit à partir d’images pour l’évaluation.  >   

    Si vous choisissez d’utiliser l’Assistant Stratégie pour créer une stratégie personnalisée, vous devez :

    - Donnez un nom et une description à la stratégie. Les noms de stratégie ne peuvent pas être modifiés une fois la stratégie créée.

    - Choisissez les utilisateurs ou les groupes à superviser, y compris tous les utilisateurs de votre organisation, des utilisateurs et des groupes spécifiques, ou d’autres utilisateurs et groupes que vous souhaitez exclure.

    - Choisissez les réviseurs pour la stratégie. Les réviseurs sont des utilisateurs individuels et tous les réviseurs doivent avoir des boîtes aux lettres hébergées Exchange Online. Les réviseurs ajoutés ici sont les relecteurs parmi qui vous pouvez choisir lors de l’escalade d’une alerte dans le flux de travail d’examen et de correction. Lorsque des réviseurs sont ajoutés à une stratégie, ils reçoivent automatiquement un message électronique les avertissant de l’affectation à la stratégie et fournissent des liens vers des informations sur le processus de révision.

    - Choisissez les canaux de communication à analyser, notamment Exchange, Microsoft Teams, Yammer ou Skype Entreprise. Vous choisirez également d’analyser des sources tierces si vous avez configuré un connecteur dans Microsoft 365.

    - Choisissez le sens des communications à surveiller, y compris les communications entrantes, sortantes ou internes.

    - Définissez les conditions de stratégie de conformité [des communications.](communication-compliance-policies.md#ConditionalSettings) Vous pouvez choisir parmi les conditions de correspondance pour l'adresse du message, les mots-clés, les types de fichiers et la taille.

    - Choisissez si vous souhaitez inclure des types d’informations sensibles. Cette étape vous permet de sélectionner les types d’informations sensibles par défaut et personnalisés. Choisissez parmi les types d’informations sensibles ou les dictionnaires de mots clés personnalisés existants dans l’Assistant Stratégie de conformité des communications. Vous pouvez créer ces éléments avant d’utiliser l’Assistant si nécessaire. Vous pouvez également créer de nouveaux types d’informations sensibles à partir de l’Assistant Stratégie de conformité des communications.

    - Choisissez si vous souhaitez activer les classifieurs. Les classifieurs peuvent détecter un langage inapproprié et des images envoyées ou reçues dans le corps des messages électroniques ou d’autres types de texte. Vous pouvez choisir les classifieurs intégrés suivants : *menace,* blasphémité, harcèlement *ciblé,* *images* pour adultes, *images racy* et *images de requête.*

    - Activez la reconnaissance optique de [caractères (OCR)](communication-compliance-policies.md#optical-character-recognition-ocr) pour analyser les images incorporées ou jointes dans les messages pour le texte imprimé ou manuscrit qui correspond aux conditions de stratégie. Pour les stratégies personnalisées, un ou plusieurs paramètres conditionnels associés à du texte, des mots clés, des classifieurs ou des types d’informations sensibles doivent être configurés dans la stratégie pour permettre la sélection de l’analyse optique de la reconnaissance de caractères.

    - Définissez le Pourcentage de communications à réviser.

    - Examinez vos sélections de stratégie et créez la stratégie.

5. Sélectionnez **Créer une stratégie** lors de l’utilisation des modèles ou **Envoyer** lors de l’utilisation de l’Assistant Stratégie personnalisée.

6. La page **Votre stratégie a été créée** s’affiche avec des instructions sur le moment où la stratégie sera activée et les communications qui seront capturées.

## <a name="step-6-optional-create-notice-templates-and-configure-user-anonymization"></a>Étape 6 (facultative) : créer des modèles d’avis et configurer l’anonymisation des utilisateurs

Si vous souhaitez avoir la possibilité de répondre à une alerte de stratégie en envoyant une notification de rappel à l’utilisateur associé, vous devez créer au moins un modèle de notification dans votre organisation. Les champs du modèle d’avis sont modifiables avant d’être envoyés dans le cadre du processus de correction des alertes, et la création d’un modèle de notification personnalisé pour chaque stratégie de conformité des communications est recommandée.

Vous pouvez également choisir d’activer l’anonymisation pour les noms d’utilisateur affichés lors de l’étude des correspondances de stratégie et de l’action sur les messages.

1. Connectez-vous [https://compliance.microsoft.com](https://compliance.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur dans Microsoft 365 organisation.

2. Dans la Centre de conformité Microsoft 365, allez à **Conformité des communications.**

3. Pour configurer l’anonymisation des noms d’utilisateur, sélectionnez **l’onglet** Confidentialité.

4. Pour activer l’anonymisation, **sélectionnez Afficher les versions anonymisées des noms d’utilisateur.**

5. Sélectionnez **Enregistrer**.

6. Accédez à **l’onglet Modèles d’avis,** puis **sélectionnez Créer un modèle de notification.**

7. Dans la page **Modifier un modèle d’avis,** complétez les champs suivants :

    - Nom du modèle (obligatoire)
    - Envoyer à partir de (obligatoire)
    - Cc et Cci (facultatif)
    - Objet (obligatoire)
    - Corps du message (obligatoire)

8. Sélectionnez **Enregistrer** pour créer et enregistrer le modèle d’avis.

## <a name="step-7-optional-test-your-communication-compliance-policy"></a>Étape 7 (facultative) : tester votre stratégie de conformité des communications

Après avoir créé une stratégie de conformité des communications, il est bon de la tester pour vous assurer que les conditions que vous avez définies sont correctement appliquées par la stratégie. Vous pouvez également tester vos stratégies de protection contre la perte de données [(DLP)](create-test-tune-dlp-policy.md) si vos stratégies de conformité des communications incluent des types d’informations sensibles. Veillez à laisser à vos stratégies le temps de s’activer afin que les communications que vous souhaitez tester soient capturées.

Suivez ces étapes pour tester votre stratégie de conformité des communications :

1. Ouvrez un client de messagerie, un Microsoft Teams ou un Yammer lors de la signature en tant qu’utilisateur supervisé défini dans la stratégie que vous souhaitez tester.

2. Envoyez un courrier électronique, Microsoft Teams conversation ou un message Yammer qui répond aux critères que vous avez définis dans la stratégie de conformité des communications. Ce test peut être un mot clé, une taille de pièce jointe, un domaine, etc. Veillez à déterminer si vos paramètres conditionnels configurés dans la stratégie sont trop restrictifs ou trop peu restrictifs.

    > [!NOTE]
    > Le traitement complet des messages électroniques dans une stratégie peut prendre jusqu’à 24 heures. Les communications Microsoft Teams, Yammer et les plateformes tierces peuvent prendre jusqu’à 48 heures pour être entièrement traitées dans une stratégie.

3. Connectez-vous Microsoft 365 en tant que réviseur désigné dans la stratégie de conformité des communications. Accédez aux **alertes de conformité**  >  **des communications** pour afficher les alertes de vos stratégies.

4. Corriger l’alerte à l’aide des contrôles de correction et vérifier que l’alerte est correctement résolue.

## <a name="next-steps"></a>Prochaines étapes

Après avoir effectué ces étapes pour créer votre première stratégie de conformité des communications, vous commencerez à recevoir des alertes d’indicateurs d’activité après 24 à 48 heures. Configurez des stratégies supplémentaires selon vos besoins à l’aide des instructions de l’étape 5 de cet article.

Pour en savoir plus sur l’examen des alertes de conformité des communications, voir Examiner et corriger [les alertes de conformité des communications.](communication-compliance-investigate-remediate.md)
