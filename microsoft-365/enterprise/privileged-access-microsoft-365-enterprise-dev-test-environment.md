---
title: Gestion des accès privilégiés pour votre Microsoft 365 pour l’environnement de test d’entreprise
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: scotv
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
- M365-security-compliance
ms.custom: Ent_TLGs
description: Utilisez ce guide de laboratoire de test pour activer la gestion des accès privilégiés de votre Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: 0c92cbd398e4c388fe3c5999c5e0aa9973c4ee06
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65092092"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Gestion des accès privilégiés pour votre Microsoft 365 pour l’environnement de test d’entreprise

*Ce guide de laboratoire de test peut être utilisé pour les Microsoft 365 pour les environnements de test d’entreprise et Office 365 Entreprise.*

Cet article explique comment configurer la gestion des accès privilégiés pour renforcer la sécurité dans votre Microsoft 365 pour l’environnement de test d’entreprise.

La configuration de la gestion des accès privilégiés implique trois phases :

- [Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Configurer la gestion des accès privilégiés](#phase-2-configure-privileged-access-management)
- [Phase 3 : Vérifier que l’approbation est requise pour les tâches avec élévation de privilèges](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir une carte visuelle de tous les articles du Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise, accédez à [Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise

Si vous souhaitez configurer la gestion des accès privilégiés de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer la gestion des accès privilégiés dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
>[!NOTE]
>Le test de la gestion des accès privilégiés ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory. Il est fourni ici en tant qu’option pour vous permettre de tester la gestion des accès privilégiés et de l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-configure-privileged-access-management"></a>Phase 2 : Configurer la gestion des accès privilégiés

Dans cette phase, configurez un groupe d’approbateurs et activez la gestion des accès privilégiés pour votre Microsoft 365 pour l’environnement de test d’entreprise. Pour plus d’informations et une vue d’ensemble de la gestion des accès privilégiés, consultez [Privileged Access Management](../compliance/privileged-access-management-overview.md).

Pour configurer et utiliser l’accès privilégié dans votre organisation, effectuez les étapes suivantes.

#### <a name="step-1-create-an-approvers-group"></a>[Étape 1 : Créer un groupe d’approbateurs](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Avant de commencer à utiliser l’accès privilégié, déterminez qui aura l’autorité d’approbation pour les demandes entrantes d’accès aux tâches élevées et privilégiées. Tous les utilisateurs qui font partie du groupe Approbateurs peuvent approuver les demandes d’accès. Pour utiliser l’accès privilégié, vous devez créer un groupe de sécurité à extension messagerie dans Microsoft 365. Dans votre environnement de test, nommez le nouveau groupe de sécurité « Approbateurs d’accès privilégié » et ajoutez l'« utilisateur 3 » précédemment créé dans les étapes précédentes du guide de laboratoire de test.

#### <a name="step-2-enable-privileged-access"></a>[Étape 2 : Activer l’accès privilégié](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

L’accès privilégié doit être explicitement activé dans Microsoft 365 avec le groupe approbateur par défaut, et il doit inclure un ensemble de comptes système que vous souhaitez exclure du contrôle d’accès de gestion des accès privilégiés. Veillez à activer l’accès privilégié dans votre organisation avant de commencer la phase 3 de ce guide.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Phase 3 : Vérifier que l’approbation est requise pour les tâches avec élévation de privilèges

Dans cette phase, vérifiez que la stratégie d’accès privilégié fonctionne et que les utilisateurs ont besoin d’une approbation pour exécuter des tâches avec élévation de privilèges définies.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Tester la possibilité d’exécuter une tâche NON définie dans une stratégie d’accès privilégié

Tout d’abord, connectez-vous à Exchange Management PowerShell avec les informations d’identification d’un utilisateur configuré avec le rôle de gestion des rôles Exchange dans votre environnement de test et essayez de créer une règle journal. La tâche [New-JournalRule](/powershell/module/exchange/new-journalrule) n’est actuellement pas définie dans une stratégie d’accès privilégié pour votre organisation.

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell de **Microsoft Corporation** >  **Microsoft Exchange Online module PowerShell à distance** à l’aide d’informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.
2. Dans Exchange Gestion PowerShell, créez une règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Vérifiez que la nouvelle règle de journal a été créée avec succès dans Exchange Management PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Créer une stratégie d’accès privilégié pour la tâche New-JournalRule

>[!NOTE]
>Si vous n’avez pas encore effectué les étapes 1 et 2 de la phase 2 de ce guide, veillez à suivre les étapes pour créer un groupe d’approbateurs nommé « Approbateurs d’accès privilégié » pour activer l’accès privilégié dans votre environnement de test.

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) à l’aide d’informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.
2. Dans le Centre d’administration, accédez à **Paramètres** >  **Security & l’accès** **PrivacyPrivileged** > .
3. Sélectionnez **Gérer les stratégies d’accès et les demandes**.
4. Sélectionnez **Configurer les stratégies**, puis **sélectionnez Ajouter une stratégie**.
5. Dans les champs déroulants, sélectionnez ou entrez les valeurs suivantes :

    **Type de stratégie** : **Étendue de la stratégie** de tâche : nom Exchange **Policy** : Nouveau **type d’approbation** de règle de journal : **Groupe d’approbation** manuelle : Approbateurs d’accès privilégié  

6. Sélectionnez **Créer**, puis sélectionnez **Fermer**. La configuration et l’activation complètes de la stratégie peuvent prendre quelques minutes. Veillez à laisser le temps à la stratégie d’être entièrement activée avant de tester l’exigence d’approbation à l’étape suivante.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Condition d’approbation de test pour la tâche New-JournalRule définie dans une stratégie d’accès privilégié

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell de **Microsoft Corporation** >  **Microsoft Exchange Online module PowerShell à distance** à l’aide d’informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.

2. Dans Exchange Gestion PowerShell, créez une règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Affichez l’erreur « Autorisations insuffisantes » dans Exchange Management PowerShell :

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Demander l’accès pour créer une règle de journal à l’aide de la tâche New-JournalRule

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) à l’aide d’informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.

2. Dans le Centre d’administration, accédez à **Paramètres** >  **Security & l’accès** **PrivacyPrivileged** > .

3. Sélectionnez **Gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **Nouvelle requête**. Dans les champs déroulants, sélectionnez les valeurs appropriées pour votre organisation :

    **Type de demande** : **Étendue de la demande** de tâche : Exchange **Request pour** : Durée de la nouvelle règle de journal **(heures)** : 2 **Commentaires** : Demander l’autorisation de créer une règle de journal  

5. Sélectionnez **Enregistrer**, puis **Fermer**. Votre demande sera envoyée au groupe de l’approbateur par e-mail.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Approuver une demande d’accès privilégié pour la création d’une règle de journal

1. Connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification de l’utilisateur 3 dans votre environnement de test (membre du groupe de sécurité « Approbateurs d’accès privilégié » dans votre environnement de test).

2. Dans le Centre d’administration, accédez à **Paramètres** >  **Security & l’accès** **PrivacyPrivileged** > .

3. Sélectionnez **Gérer les stratégies d’accès et les demandes**.

4. Sélectionnez la demande en attente, puis **sélectionnez Approuver** pour accorder l’accès au compte d’utilisateur pour créer une règle de journal. Le compte (l’utilisateur demandeur) recevra une confirmation par e-mail indiquant que l’approbation a été accordée.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Tester la création d’une règle de journal avec un accès privilégié approuvé pour la tâche New-JournalRule

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell de **Microsoft Corporation** >  **Microsoft Exchange Online module PowerShell à distance** à l’aide d’informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.

2. Dans Exchange Gestion PowerShell, créez une règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Vérifiez que la nouvelle règle de journal a été créée avec succès dans Exchange Management PowerShell.

## <a name="next-step"></a>Étape suivante

Explorez d’autres fonctionnalités et fonctionnalités de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

- [Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
- [Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)
- [Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
