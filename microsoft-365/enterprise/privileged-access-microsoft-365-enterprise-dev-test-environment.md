---
title: Gestion des accès privilégiés pour votre environnement de test Microsoft 365 entreprise
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
description: Utilisez ce guide de laboratoire de test pour activer la gestion des accès privilégiés de votre Microsoft 365 environnement de test d’entreprise.
ms.openlocfilehash: 334680092becee4d10784b1f48d5b39ec5b94405d9d8afb59d1e2060c218a017
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53904766"
---
# <a name="privileged-access-management-for-your-microsoft-365-for-enterprise-test-environment"></a>Gestion des accès privilégiés pour votre environnement de test Microsoft 365 entreprise

*Ce guide de laboratoire de test peut être utilisé pour les environnements Microsoft 365'entreprise et Office 365 Entreprise test.*

Cet article explique comment configurer la gestion des accès privilégiés pour renforcer la sécurité dans votre Microsoft 365 environnement de test d’entreprise.

La configuration de la gestion des accès privilégiés implique trois phases :

- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Configurer la gestion des accès privilégiés](#phase-2-configure-privileged-access-management)
- [Phase 3 : Vérifier que l’approbation est requise pour les tâches avec élévation de privilèges](#phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez configurer la gestion des accès privilégiés de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez configurer la gestion des accès privilégiés dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
>[!NOTE]
>Le test de la gestion des accès privilégiés ne nécessite pas l’environnement de test d’entreprise simulée, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory. Il est fourni ici en tant qu’option afin que vous pouvez tester la gestion des accès privilégiés et l’expérimenter dans un environnement qui représente une organisation classique.

## <a name="phase-2-configure-privileged-access-management"></a>Phase 2 : Configurer la gestion des accès privilégiés

Dans cette phase, configurez un groupe d’approbations et activez la gestion des accès privilégiés pour votre Microsoft 365 environnement de test d’entreprise. Pour plus d’informations et une vue d’ensemble de la gestion des accès privilégiés, voir [Privileged access management](../compliance/privileged-access-management-overview.md).

Pour configurer et utiliser l’accès privilégié dans votre organisation, effectuez les étapes suivantes.

#### <a name="step-1-create-an-approvers-group"></a>[Étape 1 : Créer un groupe d’approbation](../compliance/privileged-access-management-configuration.md#step-1-create-an-approvers-group)

Avant de commencer à utiliser l’accès privilégié, déterminez qui aura l’autorité d’approbation pour les demandes entrantes d’accès aux tâches élevées et privilégiées. Tous les utilisateurs qui font partie du groupe d’approbations peuvent approuver les demandes d’accès. Pour utiliser l’accès privilégié, vous devez créer un groupe de sécurité à messagerie dans Microsoft 365. Dans votre environnement de test, nommez le nouveau groupe de sécurité « Privileged Access Approvers » et ajoutez l'« Utilisateur 3 » précédemment créé lors des étapes précédentes du guide de laboratoire de test.

#### <a name="step-2-enable-privileged-access"></a>[Étape 2 : Activer l’accès privilégié](../compliance/privileged-access-management-configuration.md#step-2-enable-privileged-access)

L’accès privilégié doit être explicitement allumé dans Microsoft 365 avec le groupe d’approbation par défaut, et il doit inclure un ensemble de comptes système que vous souhaitez exclure du contrôle d’accès de gestion des accès privilégiés. Veillez à activer l’accès privilégié dans votre organisation avant de commencer la phase 3 de ce guide.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Phase 3 : Vérifier que l’approbation est requise pour les tâches avec élévation de privilèges

Dans cette phase, vérifiez que la stratégie d’accès privilégié fonctionne et que les utilisateurs ont besoin d’approbation pour exécuter des tâches définies avec élévation de privilèges.

### <a name="test-the-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Tester la possibilité d’exécuter une tâche NON définie dans une stratégie d’accès privilégié

Tout d’abord, connectez-vous à Exchange Management PowerShell avec les informations d’identification d’un utilisateur configuré avec le rôle de gestion des rôles Exchange dans votre environnement de test et essayez de créer une règle de journal. La [tâche New-JournalRule](/powershell/module/exchange/new-journalrule) n’est actuellement pas définie dans une stratégie d’accès privilégié pour votre organisation.

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell de **Microsoft Corporation** Microsoft Exchange Online  >  **Remote PowerShell Module** à l’aide des informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.
2. Dans Exchange PowerShell Gestion, créez une règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
   ```

3. Découvrez que la nouvelle règle de journal a été créée avec succès dans Exchange PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Créer une stratégie d’accès privilégié pour la New-JournalRule de travail

>[!NOTE]
>Si vous n’avez pas déjà effectué les étapes 1 et 2 de la phase 2 de ce guide, assurez-vous de suivre les étapes pour créer un groupe d’approbation nommé « Approvers d’accès privilégié » afin d’activer l’accès privilégié dans votre environnement de test.

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification avec Exchange rôle de gestion des rôles pour votre environnement de test.
2. Dans le Centre d’administration, accédez **à Paramètres**  >  **sécurité & confidentialité**  >  **privilégié.**
3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**
4. Sélectionnez **Configurer les stratégies,** puis **ajoutez une stratégie.**
5. Dans les champs de listes, sélectionnez ou entrez les valeurs suivantes :

    **Type de stratégie**: étendue **de stratégie de tâche**: Exchange stratégie **:** Nouveau type d’approbation de règle de **journal**: **Groupe** Approbation manuelle : Approbations d’accès privilégié  

6. Sélectionnez **Créer**, puis sélectionnez **Fermer**. La configuration et l’activé de la stratégie peuvent prendre quelques minutes. Veillez à laisser le temps à la stratégie d’être entièrement activée avant de tester l’exigence d’approbation à l’étape suivante.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Tester l’approbation requise pour la tâche New-JournalRule définie dans une stratégie d’accès privilégié

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell de **Microsoft Corporation** Microsoft Exchange Online  >  **Remote PowerShell Module** à l’aide des informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.

2. Dans Exchange PowerShell Gestion, créez une règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Affichez l’erreur « Autorisations insuffisantes » dans Exchange PowerShell de gestion :

   ```ExchangeManagementPowerShell
   Insufficient permissions. Please raise an elevated access request for this task.
       + CategoryInfo          : NotSpecified: (:) [], LocalizedException
       + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
       7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
       + PSComputerName        : outlook.office365.com
   ```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Demander l’accès pour créer une règle de journal à l’aide New-JournalRule tâche

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification avec Exchange rôle de gestion des rôles pour votre environnement de test.

2. Dans le Centre d’administration, accédez **à Paramètres**  >  **sécurité & confidentialité**  >  **privilégié.**

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez **Nouvelle requête**. Dans les champs de la baisse, sélectionnez les valeurs appropriées pour votre organisation :

    **Type de** requête : étendue **de** demande de tâche : Exchange **demande** pour : Nouvelle durée de règle de journal **(heures)**: **2** commentaires : demander l’autorisation de créer une règle de journal  

5. Sélectionnez **Enregistrer,** puis **Fermez.** Votre demande est envoyée au groupe de l’approuveur par courrier électronique.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Approuver une demande d’accès privilégié pour la création d’une nouvelle règle de journal

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification de l’utilisateur 3 dans votre environnement de test (membre du groupe de sécurité « Privileged Access Approvers » dans votre environnement de test).

2. Dans le Centre d’administration, accédez **à Paramètres**  >  **sécurité & confidentialité**  >  **privilégié.**

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez la demande en attente, puis **sélectionnez Approuver** pour accorder l’accès au compte d’utilisateur afin de créer une règle de journal. Le compte (l’utilisateur demandeur) reçoit une confirmation par courrier électronique pour confirmer que l’approbation a été accordée.

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Tester la création d’une règle de journal avec un accès privilégié approuvé pour la New-JournalRule tâche

1. Sur votre ordinateur local, ouvrez et connectez-vous au module Exchange Online Remote PowerShell de **Microsoft Corporation** Microsoft Exchange Online  >  **Remote PowerShell Module** à l’aide des informations d’identification avec le rôle de gestion des rôles Exchange pour votre environnement de test.

2. Dans Exchange PowerShell Gestion, créez une règle de journal pour votre organisation :

   ```ExchangeManagementPowerShell
   New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
   ```

3. Découvrez que la nouvelle règle de journal a été créée avec succès dans Exchange PowerShell.

## <a name="next-step"></a>Étape suivante

Explorez [d’autres fonctionnalités de protection](m365-enterprise-test-lab-guides.md#information-protection) des informations dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

- [Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)
- [Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)
- [Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)
