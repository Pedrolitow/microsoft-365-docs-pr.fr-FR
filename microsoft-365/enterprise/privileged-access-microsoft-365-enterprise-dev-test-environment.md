---
title: Gestion des accès privilégiés pour votre environnement de test Microsoft 365 Entreprise
ms.author: robmazz
author: robmazz
manager: laurawi
ms.date: 09/21/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom: Ent_TLGs
description: Utilisez ce Guide de laboratoire de Test pour permettre la gestion de l’accès privilégié de votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 5f1a416a12171504af110ec62b9a7882143263e6
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26866847"
---
# <a name="privileged-access-management-for-your-microsoft-365-enterprise-test-environment"></a>Gestion des accès privilégiés pour votre environnement de test Microsoft 365 Entreprise

Avec les instructions de cet article, vous configurez la gestion des accès privilégié pour renforcer la sécurité dans votre environnement de test Microsoft 365 pour entreprises.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png)

> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez simplement configurer la gestion de l’accès privilégié de manière léger avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez configurer la gestion de l’accès privilégié dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test de gestion de l’accès privilégié ne nécessite pas l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option pour que vous puissiez tester privilégié accéder à la gestion et tester dans un environnement qui représente une organisation classique. 

## <a name="phase-2-configure-privileged-access-management"></a>Phase 2 : Configurer la gestion des accès privilégié

Durant cette phase, vous configurez un groupe approbateurs et activez la gestion de l’accès privilégié pour votre environnement de test Microsoft 365 pour entreprises. Pour plus d’informations et une vue d’ensemble des privilèges accéder à la gestion, voir [gestion de l’accès privilégié dans Office 365](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-overview).

Suivez ces étapes pour configurer et utiliser un accès privilégié dans votre organisation Office 365 :

- [Étape 1 : Créer le groupe d’approbateur](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration#step-1---create-an-approvers-group)

    Avant de commencer à l’aide de privilège d’accès, déterminer ayant autorité d’approbation pour les demandes entrantes pour l’accès aux tâches avec des privilèges élevés et privilégiés. Tout utilisateur qui fait partie du groupe des approbateurs sera en mesure d’approuver les demandes d’accès. Cette option est activée en créant un groupe de sécurité à extension messagerie dans Office 365. Créer un nouveau groupe de sécurité nommé « Approbateurs d’accès privilégié » dans votre environnement de test et ajouter le « utilisateur 3 », précédemment créé dans les étapes de guide de laboratoire de test préalable.

- [Étape 2 : Activer l’accès privilégié](https://docs.microsoft.com/office365/securitycompliance/privileged-access-management-configuration#step-2---enable-privileged-access)

    Accès privilégié doit être activé explicitement dans Office 365 avec le groupe d’approbateur par défaut et y compris un ensemble de comptes système que vous souhaitez exclure le contrôle d’accès de gestion des accès privilégié. Veillez à activer l’accès privilégié dans votre organisation Office 365 avant de commencer la Phase 3 de ce guide.

## <a name="phase-3-verify-that-approval-is-required-for-elevated-and-privileged-tasks"></a>Phase 3 : Vérifiez que l’approbation est nécessaire pour les tâches avec des privilèges élevés et privilégiés
Dans cette phase, vous vérifiez que la stratégie d’accès privilégié fonctionne et que les utilisateurs ont besoin d’approbation pour exécuter des tâches avec des privilèges élevés et privilégiés définies.

### <a name="test-ability-to-execute-a-task-not-defined-in-a-privileged-access-policy"></a>Tester la capacité à exécuter une tâche non définie dans une stratégie d’accès privilégié

Tout d’abord, connectez-vous à Exchange Management PowerShell avec les informations d’identification d’un utilisateur configuré comme un administrateur Global dans votre environnement de test et essayez de créer une nouvelle règle de Journal. La tâche [New-JournalRule](https://docs.microsoft.com/powershell/module/exchange/policy-and-compliance/new-journalrule?view=exchange-ps) n’est pas actuellement définie dans une stratégie d’accès privilégié pour votre organisation.

1. Sur votre ordinateur local, ouvrez et connectez-vous à la le Exchange Online PowerShell Module distant **Microsoft**Corporation > **Exchange distant PowerShell Module Microsoft Online** à l’aide de l’administrateur Global de compte pour votre environnement de test.

2. Dans Exchange Management Powershell, créez une nouvelle règle de Journal pour votre organisation :

```
New-JournalRule -Name "JournalRule1" -Recipient joe@contoso.onmicrosoft.com -JournalEmailAddress barbara@adatum.com -Scope Global -Enabled $true
```
4. Affichage que la nouvelle règle de Journal a été créée dans Exchange Management PowerShell.

### <a name="create-a-new-privileged-access-policy-for-the-new-journalrule-task"></a>Créer une nouvelle stratégie d’accès privilégié pour la tâche New-JournalRule

> [!NOTE]
> Si vous n’avez pas déjà effectué les étapes 1 et 2 à partir de la Phase 2 de ce guide, vous pouvez être que suivre les étapes pour créer groupe d’un approbateur nommé « Privilège accès approbateurs » et permettre l’accès privilégié dans votre environnement de test.

1. Se connecter au [Centre d’administration de Microsoft 365](https://portal.office.com) à l’aide des informations d’identification pour votre environnement de test, le compte d’administrateur Global.

2. Dans le centre d’administration, cliquez sur **paramètres** > **sécurité et confidentialité** > **accès privilégié**.

3. Sélectionnez **Gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **configurer les stratégies** et sélectionnez **Ajouter une stratégie**.

5. Dans les champs de liste déroulante, sélectionnez ou entrez les valeurs suivantes :
    
    **Type de stratégie**: tâche

    **Étendue de la stratégie**: Exchange

    **Nom de la stratégie**: nouvelle règle de Journal

    **Type d’approbation**: manuel

    **Groupe d’approbation**: privilégié approbateurs Access

6. Sélectionnez **créer** , puis sur **Fermer**. Il peut prendre quelques minutes pour la stratégie soit entièrement configuré et activé. Veillez à laisser le temps à la stratégie à activer entièrement avant de tester l’obligation d’approbation à l’étape suivante.

### <a name="test-approval-requirement-for-the-new-journalrule-task-defined-in-a-privileged-access-policy"></a>Demande d’approbation de test pour la tâche New-JournalRule définie dans une stratégie d’accès privilégié

1. Sur votre ordinateur local, ouvrez et connectez-vous à la le Exchange Online PowerShell Module distant **Microsoft**Corporation > compte**Exchange à distance PowerShell Module Microsoft Online** à l’aide d’un à l’aide de l’administrateur Global de test environnement.

2. Dans Exchange Management Powershell, créez une nouvelle règle de Journal pour votre organisation :

```
New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
```
3. Afficher l’erreur « Autorisations insuffisant » dans Exchange Management PowerShell :

```
Insufficient permissions. Please raise an elevated access request for this task.
    + CategoryInfo          : NotSpecified: (:) [], LocalizedException
    + FullyQualifiedErrorId : [Server=CY1PR00MB0220,RequestId=7b8c7470-ddd0-4528-a01e-5e20ecc9bd54,TimeStamp=9/19/2018
    7:38:34 PM] [FailureCategory=Cmdlet-LocalizedException] 882BD051
    + PSComputerName        : outlook.office365.com
```

### <a name="request-access-to-create-a-new-journal-rule-using-the-new-journalrule-task"></a>Pour créer une nouvelle règle de Journal à l’aide de la tâche New-JournalRule pour demander l’accès

1. Connectez-vous au [Centre d’administration de Microsoft 365](https://portal.office.com) utilisant le compte d’administrateur Global de votre environnement de test.

2. Dans le centre d’administration, cliquez sur **paramètres** > **sécurité et confidentialité** > **accès privilégié**.

3. Sélectionnez **Gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **nouvelle demande**. Dans les champs de liste déroulante, sélectionnez les valeurs appropriées pour votre organisation :

    **Type de demande**: tâche

    **Étendue de demande**: Exchange

    **Demande de**: nouvelle règle de Journal

    **Durée (en heures)**: 2

    **Commentaires**: demander l’autorisation de créer une nouvelle règle de Journal

5. Sélectionnez **Enregistrer** , puis sur **Fermer**. Votre demande sera envoyée au groupe de l’approbateur par courrier électronique.

### <a name="approve-privileged-access-request-for-the-creation-of-a-new-journal-rule"></a>Approuver les demandes d’accès privilégié de la création d’une nouvelle règle de Journal

1. Connectez-vous au [Centre d’administration de Microsoft 365](https://portal.office.com) par les informations d’identification utilisateur 3 dans votre environnement de test (membre du groupe de sécurité « Approbateurs d’accès privilégié » dans votre environnement de test).

2. Dans le centre d’administration, cliquez sur **paramètres** > **sécurité et confidentialité** > **accès privilégié**.

3. Sélectionnez **Gérer les stratégies d’accès et les demandes**.

4. Sélectionnez la demande en attente, sélectionnez **Approuver** pour accorder l’accès au compte d’administrateur Global pour créer une nouvelle règle de Journal. Une notification électronique vous demandant de confirmer que la réception a été accordée sera envoyé au compte d’administrateur Global (l’utilisateur).  

### <a name="test-creating-a-new-journal-rule-with-privileged-access-approved-for-the-new-journalrule-task"></a>Création d’une nouvelle règle de Journal avec un accès privilégié approuvé pour la tâche New-JournalRule de test

1. Sur votre ordinateur local, ouvrez et connectez-vous à la le Exchange Online PowerShell Module distant **Microsoft**Corporation > **Exchange distant PowerShell Module Microsoft Online** à l’aide de l’administrateur Global de compte pour votre environnement de test.

2. Dans Exchange Management Powershell, créez une nouvelle règle de Journal pour votre organisation :

```
New-JournalRule -Name "JournalRule2" -Recipient user1@<your subscription domain> -JournalEmailAddress user1@<your subscription domain> -Scope Global -Enabled $true
```
3. Affichage que la nouvelle règle de Journal a été créée dans Exchange Management PowerShell.

## <a name="next-step"></a>Étape suivante

Explorez les fonctionnalités supplémentaires de [protection des informations](m365-enterprise-test-lab-guides.md#information-protection) et fonctionnalités dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déployer Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)