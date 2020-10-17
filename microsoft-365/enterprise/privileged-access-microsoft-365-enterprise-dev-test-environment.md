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
ms.openlocfilehash: 24ca7a6408a4290c54dd2bcd7c3f6061eb8f6c05
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487587"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Gestion des accès privilégiés pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test peut être utilisé pour les environnements de test Microsoft 365 pour les environnements de test d’entreprise et Office 365.*

Cet article explique comment configurer la gestion des accès privilégiés pour renforcer la sécurité dans votre environnement de test Microsoft 365 pour les entreprises.

La configuration de la gestion des accès privilégiés comprend trois phases :
- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : configurer la gestion des accès privilégiés](#phase-2-configure-privileged-access-management)
- [Phase 3 : vérifier que l’approbation est requise pour les tâches avec privilèges élevés et privilégiées](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez configurer la gestion des accès privilégiés de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer la gestion des accès privilégiés dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Le test de la gestion des accès privilégiés ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory. Elle est fournie ici en tant qu’option qui vous permet de tester la gestion des accès privilégiés et de l’expérimenter dans un environnement qui représente une organisation type.

## <a name="phase-2-configure-privileged-access-management"></a>Phase 2 : configurer la gestion des accès privilégiés

Dans cette phase, configurez un groupe approbateurs et activez la gestion des accès privilégiés pour votre environnement de test Microsoft 365 pour les entreprises. Pour plus d’informations et pour obtenir une vue d’ensemble de la gestion des accès privilégiés, consultez la rubrique [gestion des accès privilégiés](../compliance/privileged-access-management-overview.md).

Pour configurer et utiliser l’accès privilégié dans votre organisation, procédez comme suit.

#### <a name="step-1-create-an-approvers-group"></a>[Étape 1 : créer un groupe d’approbateurs](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Avant de commencer à utiliser l’accès privilégié, déterminez qui disposera de l’autorité d’approbation pour les demandes entrantes d’accès à des tâches élevées et privilégiées. Tous les utilisateurs qui font partie du groupe approbateurs peuvent approuver les demandes d’accès. Pour utiliser l’accès privilégié, vous devez créer un groupe de sécurité à extension messagerie dans Microsoft 365. Dans votre environnement de test, nommez le nouveau groupe de sécurité « approbateurs d’accès privilégié » et ajoutez « User 3 » précédemment créé dans les étapes précédentes du Guide de laboratoire de test.

#### <a name="step-2-enable-privileged-access"></a>[Étape 2 : activer l’accès privilégié](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

L’accès privilégié doit être activé de manière explicite dans Microsoft 365 avec le groupe d’approbateurs par défaut, et il doit inclure un ensemble de comptes système que vous souhaitez exclure du contrôle d’accès gestion des accès privilégiés. Veillez à activer l’accès privilégié dans votre organisation avant de commencer la phase 3 de ce guide.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Phase 3 : vérifier que l’approbation est requise pour les tâches avec privilèges élevés et privilégiées

Dans cette phase, vérifiez que la stratégie d’accès privilégié fonctionne et que les utilisateurs ont besoin d’une approbation pour exécuter des tâches élevées et privilégiées définies.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Tester la possibilité d’exécuter une tâche non définie dans une stratégie d’accès privilégié

Tout d’abord, connectez-vous à Exchange Management PowerShell avec les informations d’identification d’un utilisateur configuré en tant qu’administrateur général dans votre environnement de test et essayez de créer une nouvelle règle de journal. La tâche [New-JournalRule](https://docs.microsoft.com/powershell/module/exchange/new-journalrule) n’est actuellement pas définie dans une stratégie d’accès privilégié pour votre organisation.

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell du **Microsoft Corporation**  >  **module Microsoft Exchange Online PowerShell** à l’aide du compte d’administrateur général pour votre environnement de test.

1. Dans Exchange Management PowerShell, créez une nouvelle règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

1. Affichage de la création de la nouvelle règle de journal dans Exchange Management PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Créer une stratégie d’accès privilégié pour la tâche New-JournalRule

>[!NOTE]
>Si vous n’avez pas encore effectué les étapes 1 et 2 de la phase 2 de ce guide, assurez-vous de suivre les étapes nécessaires pour créer un groupe d’approbateurs nommé « approbateurs d’accès aux privilèges » afin d’activer l’accès privilégié dans votre environnement de test.

1. Connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) à l’aide des informations d’identification du compte d’administrateur global pour votre environnement de test.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **configurer les stratégies**, puis **Ajouter une stratégie**.

5. Dans les champs de liste déroulante, sélectionnez ou entrez les valeurs suivantes :

    **Type de stratégie**: tâche

    **Étendue de la stratégie** : Exchange

    **Nom**de la stratégie : nouvelle règle de journal

    **Type d’approbation**: Manuel

    **Groupe d’approbation**: approbateurs des accès privilégiés

6. Sélectionnez **créer**, puis **Fermer**. La configuration et l’activation de la stratégie peuvent prendre quelques minutes. Veillez à laisser le temps nécessaire pour que la stratégie soit entièrement activée avant de tester les conditions d’approbation à l’étape suivante.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Conditions requises en matière d’approbation de test pour la tâche New-JournalRule définie dans une stratégie d’accès privilégié

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell du module **Microsoft**  >  **Exchange Online PowerShell** à l’aide d’un compte d’administrateur général pour votre environnement de test.

2. Dans Exchange Management PowerShell, créez une nouvelle règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Affichez l’erreur « autorisations insuffisantes » dans Exchange Management PowerShell :

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

5. Sélectionnez **Enregistrer**, puis **Fermer**. Votre demande sera envoyée au groupe de l’approbateur par courrier électronique.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Approuver une demande d’accès privilégié pour la création d’une nouvelle règle de journal

1. Connectez-vous au [Centre d’administration 365 de Microsoft](https://admin.microsoft.com) à l’aide des informations d’identification de l’utilisateur 3 dans votre environnement de test (membre du groupe de sécurité « approbateurs avec accès privilégié » dans votre environnement de test).

2. Dans le centre d’administration, accédez à **paramètres**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez la demande en attente, puis sélectionnez **approuver** pour accorder l’accès au compte d’administrateur général afin de créer une nouvelle règle de journal. Le compte d’administrateur global (l’utilisateur qui effectue la demande) reçoit un message confirmant que l’approbation a été accordée.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Tester la création d’une nouvelle règle de journal avec un accès privilégié approuvé pour la tâche New-JournalRule

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell du **Microsoft Corporation**  >  **module Microsoft Exchange Online PowerShell** à l’aide du compte d’administrateur général pour votre environnement de test.

1. Dans Exchange Management PowerShell, créez une nouvelle règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

1. Affichage de la création de la nouvelle règle de journal dans Exchange Management PowerShell.

## <a name="next-step"></a>Étape suivante

Découvrez les fonctionnalités et les fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) supplémentaires dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
