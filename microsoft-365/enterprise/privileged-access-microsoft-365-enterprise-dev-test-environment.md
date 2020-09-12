---
title: Gestion des accès privilégiés pour votre environnement de test Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Utilisez ce guide de laboratoire de test pour activer la gestion des accès privilégiés pour votre environnement de test Microsoft 365 pour les entreprises.
ms.openlocfilehash: d8d92aa86076e323e4b5bb5c8eb1385edcac420c
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47545941"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Gestion des accès privilégiés pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

Avec les instructions de cet article, vous configurez la gestion des accès privilégiés pour renforcer la sécurité dans votre environnement de test Microsoft 365 pour les entreprises.

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

>[!TIP]
>Cliquez [ici](../media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan visuel de tous les articles de l’ensemble des guides de laboratoire de test de Microsoft 365 pour entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez simplement configurer la gestion des accès privilégiés de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer la gestion des accès privilégiés dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Le test de la gestion des accès privilégiés ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt AD DS. Elle est fournie ici en tant qu’option qui vous permet de tester la gestion des accès privilégiés et de l’expérimenter dans un environnement qui représente une organisation typique. 

## <a name="phase-2-configure-privileged-access-management"></a>Phase 2 : configurer la gestion des accès privilégiés

Dans cette phase, vous allez configurer un groupe approbateurs et activer la gestion des accès privilégiés pour votre environnement de test Microsoft 365 pour les entreprises. Pour plus d’informations et pour obtenir une vue d’ensemble de la gestion des accès privilégiés, consultez la rubrique [gestion des accès privilégiés](../compliance/privileged-access-management-overview.md).

Procédez comme suit pour configurer et utiliser l’accès privilégié dans votre organisation :

- [Étape 1 : créer un groupe d’approbateurs](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

    Avant de commencer à utiliser l’accès aux privilèges, déterminez qui disposera de l’autorité d’approbation pour les demandes entrantes d’accès à des tâches élevées et privilégiées. Tout utilisateur qui fait partie du groupe approbateurs est en mesure d’approuver les demandes d’accès. Pour cela, vous créez un groupe de sécurité à extension messagerie dans Microsoft 365. Créez un groupe de sécurité nommé « approbateurs d’accès privilégié » dans votre environnement de test et ajoutez « User 3 » précédemment créé dans les étapes du Guide de laboratoire de test précédent.

- [Étape 2 : activer l’accès privilégié](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

    L’accès privilégié doit être activé de manière explicite dans Microsoft 365 avec le groupe d’approbateurs par défaut et inclure un ensemble de comptes système que vous souhaitez exclure du contrôle d’accès gestion des accès privilégiés. Veillez à activer l’accès privilégié dans votre organisation avant de commencer la phase 3 de ce guide.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Phase 3 : vérifier que l’approbation est requise pour les tâches avec privilèges élevés et privilégiées

Dans cette phase, vous vérifiez que la stratégie d’accès privilégié fonctionne et que les utilisateurs demandent une approbation pour exécuter des tâches élevées et privilégiées définies.

### <a name="test-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Tester la possibilité d’exécuter une tâche non définie dans une stratégie d’accès privilégié

Tout d’abord, connectez-vous à Exchange Management PowerShell avec les informations d’identification d’un utilisateur configuré en tant qu’administrateur général dans votre environnement de test et essayez de créer une nouvelle règle de journal. La tâche [New-JournalRule](https://docs.microsoft.com/powershell/module/exchange/new-journalrule) n’est actuellement pas définie dans une stratégie d’accès privilégié pour votre organisation.

1. Sur votre ordinateur local, ouvrez le module Exchange Online Remote PowerShell et connectez-vous au module **Microsoft**  >  **Exchange Online** PowerShell à l’aide du compte d’administrateur général pour votre environnement de test.

2. Dans Exchange Management PowerShell, créez une nouvelle règle de journal pour votre organisation :

```ExchangeManagementPowerShell
New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
```

4. Affichage de la création de la nouvelle règle de journal dans Exchange Management PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Créer une stratégie d’accès privilégié pour la tâche New-JournalRule

>[!NOTE]
>Si vous n’avez pas déjà effectué les étapes 1 et 2 de la phase 2 de ce guide, assurez-vous de suivre les étapes nécessaires pour créer un groupe d’approbateurs nommé « approbateurs d’accès aux privilèges » et pour activer l’accès privilégié dans votre environnement de test.

1. Connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) à l’aide des informations d’identification du compte d’administrateur global pour votre environnement de test.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **configurer les stratégies** et sélectionnez **Ajouter une stratégie**.

5. Dans les champs de liste déroulante, sélectionnez ou entrez les valeurs suivantes :

    **Type de stratégie**: tâche

    **Étendue de la stratégie** : Exchange

    **Nom**de la stratégie : nouvelle règle de journal

    **Type d’approbation**: Manuel

    **Groupe d’approbation**: approbateurs des accès privilégiés

6. Sélectionnez **créer** , puis **Fermer**. La configuration et l’activation de la stratégie peuvent prendre quelques minutes. Veillez à laisser le temps nécessaire pour que la stratégie soit entièrement activée avant de tester les conditions d’approbation à l’étape suivante.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Condition d’approbation de test pour la tâche New-JournalRule définie dans une stratégie d’accès privilégié

1. Sur votre ordinateur local, ouvrez le module Exchange Online Remote PowerShell et connectez-vous au module **Microsoft**  >  **Exchange Online** PowerShell à l’aide d’un compte d’administrateur général pour votre environnement de test.

2. Dans Exchange Management PowerShell, créez une nouvelle règle de journal pour votre organisation :

```ExchangeManagementPowerShell
New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
```

3. Afficher l’erreur « autorisations insuffisantes » dans Exchange Management PowerShell :

```ExchangeManagementPowerShell
Insufficient permissions. Please raise an elevated access request for this task.
    + CategoryInfo          : NotSpecified: (:) [], LocalizedException
    + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
    7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
    + PSComputerName        : outlook.office365.com
```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Demander l’accès pour créer une nouvelle règle de journal à l’aide de la tâche New-JournalRule

1. Connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) à l’aide du compte d’administrateur général pour votre environnement de test.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **nouvelle demande**. Dans les champs de liste déroulante, sélectionnez les valeurs appropriées pour votre organisation :

    **Type de demande**: tâche

    **Étendue de la demande** : Exchange

    **Demande**: nouvelle règle de journal

    **Durée (heures)**: 2

    **Commentaires**: demander l’autorisation de créer une nouvelle règle de journal

5. Sélectionnez **Enregistrer** , puis **Fermer**. Votre demande sera envoyée au groupe de l’approbateur par courrier électronique.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Approuver une demande d’accès privilégié pour la création d’une nouvelle règle de journal

1. Connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) à l’aide des informations d’identification de l’utilisateur 3 dans votre environnement de test (membre du groupe de sécurité « approbateurs avec accès privilégié » dans votre environnement de test).

2. Dans le centre d’administration, accédez à **paramètres**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez la demande en attente et sélectionnez **approuver** pour accorder l’accès au compte d’administrateur général afin de créer une nouvelle règle de journal. Un courrier électronique de notification confirmant que l’approbation a été accordée est envoyé au compte d’administrateur global (l’utilisateur qui effectue la demande).  

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Tester la création d’une nouvelle règle de journal avec un accès privilégié approuvé pour la tâche New-JournalRule

1. Sur votre ordinateur local, ouvrez le module Exchange Online Remote PowerShell et connectez-vous au module **Microsoft**  >  **Exchange Online** PowerShell à l’aide du compte d’administrateur général pour votre environnement de test.

2. Dans Exchange Management PowerShell, créez une nouvelle règle de journal pour votre organisation :

```ExchangeManagementPowerShell
New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
```

3. Affichage de la création de la nouvelle règle de journal dans Exchange Management PowerShell.

## <a name="next-step"></a>Étape suivante

Découvrez les fonctionnalités et les fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) supplémentaires dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
