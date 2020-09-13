---
title: Prise en main de la gestion des accès privilégiés
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: ''
description: Utilisez cet article pour en savoir plus sur l’activation et la configuration de la gestion des accès privilégiés dans Office 365.
ms.openlocfilehash: 7b3ac9dbc065bcbbdf48e805a3975886a894c645
ms.sourcegitcommit: 27daadad9ca0f02a833ff3cff8a574551b9581da
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2020
ms.locfileid: "47545994"
---
# <a name="get-started-with-privileged-access-management"></a>Prise en main de la gestion des accès privilégiés

Cette rubrique vous guide tout au long de l’activation et de la configuration de la gestion des accès privilégiés dans votre organisation. Vous pouvez utiliser le centre d’administration Microsoft 365 ou Exchange Management PowerShell pour gérer et utiliser l’accès privilégié.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer à utiliser la gestion des accès privilégiés, vous devez confirmer votre [abonnement Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et tous les modules complémentaires. Pour accéder à la gestion des accès privilégiés et l’utiliser, votre organisation doit disposer de l’un des abonnements ou des modules complémentaires suivants :

- Abonnement Microsoft 365 E5 (payant ou version d’évaluation)
- Microsoft 365 E3 Subscription (ou Office 365 E3 subscription + Enterprise Mobility and Security E3 subscription) + The Microsoft 365 E5 Compliance Add-on
- Tout abonnement Microsoft 365, Office 365, Exchange, SharePoint ou OneDrive entreprise + le module complémentaire de gestion des risques de l’Insider de Microsoft 365 E5  
- Abonnement Microsoft 365 a5 (payant ou version d’évaluation)
- Abonnement Microsoft 365 a3 (ou abonnement Office 365 a3 + abonnement Enterprise Mobility and Security a3) + le complément Microsoft a5 Compliance
- Tout abonnement Microsoft 365, Office 365, Exchange, SharePoint ou OneDrive éducation + le complément de gestion des risques Microsoft 365 a5 Insider
- Office 365 entreprise E5 abonnement (payant ou version d’évaluation)
- Office 365 entreprise E3 abonnement + le complément Office 365 Advanced Compliance (qui n’est plus disponible pour les nouveaux abonnements, reportez-vous à la rubrique note)

Les utilisateurs qui envoient et répondent aux demandes de gestion des accès privilégiés doivent disposer de l’une des licences ci-dessus.

>[!IMPORTANT]
>Office 365 Advanced Compliance n’est plus vendu en tant qu’abonnement autonome. Lorsque les abonnements actuels arrivent à expiration, les clients doivent effectuer une transition vers l’un des abonnements ci-dessus, qui contiennent les mêmes fonctionnalités de conformité ou des fonctionnalités de conformité supplémentaires.

Si vous ne disposez pas d’un plan Office 365 entreprise E5 existant et que vous souhaitez essayer la gestion des accès privilégiés, vous pouvez [Ajouter microsoft 365](https://docs.microsoft.com/office365/admin/try-or-buy-microsoft-365) à votre abonnement Office 365 existant ou [vous inscrire pour obtenir une version d’évaluation](https://www.microsoft.com/microsoft-365/enterprise) de Microsoft 365 entreprise E5.

## <a name="enable-and-configure-privileged-access-management"></a>Activer et configurer la gestion des accès privilégiés

Procédez comme suit pour configurer et utiliser l’accès privilégié dans votre organisation :

- [Étape 1 : créer un groupe d’approbateurs](privileged-access-management-configuration.md#step1)

    Avant de commencer à utiliser l’accès privilégié, déterminez qui a besoin de l’autorité d’approbation pour les demandes entrantes permettant d’accéder à des tâches avec élévation de privilèges. Tout utilisateur faisant partie du groupe d’approbateurs peut approuver les demandes d’accès. Ce groupe est activé par la création d’un groupe de sécurité à extension messagerie dans Office 365.

- [Étape 2 : activer l’accès privilégié](privileged-access-management-configuration.md#step2)

    Les accès privilégiés doivent être activés de manière explicite dans Office 365 avec le groupe d’approbateurs par défaut, y compris un ensemble de comptes système que vous souhaitez exclure du contrôle d’accès par gestion des accès privilégiés.

- [Étape 3 : créer une stratégie d’accès](privileged-access-management-configuration.md#step3)

    La création d’une stratégie d’approbation vous permet de définir les exigences d’approbation spécifiques d’une tâche spécifique. Les options type d’approbation sont **Automatiques** ou **Manuelles**.

- [Étape 4 : soumettre/approuver des demandes d’accès privilégié](privileged-access-management-configuration.md#step4)

    Une fois activé, l’accès privilégié nécessite des approbations pour toutes les tâches auxquelles une stratégie d’approbation associée est définie. Pour les tâches incluses dans une stratégie d’approbation, les utilisateurs doivent demander et se voir autoriser d’accès afin d’obtenir les autorisations nécessaires pour exécuter la tâche.

Une fois l’approbation accordée, l’utilisateur demandeur peut exécuter la tâche prévue et l’accès privilégié autorise et exécute la tâche au nom de l’utilisateur. L’approbation reste valide pendant la durée demandée (la durée par défaut est de 4 heures), période durant laquelle le demandeur peut effectuer la tâche prévue plusieurs fois. Toutes ces réalisations sont enregistrées et mises à disposition pour l’audit sur la sécurité et la conformité. 

>[!NOTE]
>Si vous souhaitez utiliser Exchange Management PowerShell pour activer et configurer l’accès privilégié, suivez les étapes de la [page connexion à Exchange Online PowerShell à l’aide de l’authentification multifacteur](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) pour vous connecter à Exchange Online PowerShell avec vos informations d’identification Office 365. Vous n’avez pas besoin d’activer l’authentification multifacteur pour votre organisation afin d’utiliser les étapes d’activation de l’accès privilégié lors de la connexion à Exchange Online PowerShell. La connexion avec l’authentification multifacteur crée un jeton OAuth qui est utilisé par un accès privilégié pour signer vos demandes.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>Étape 1 : créer un groupe d’approbateurs

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le centre d’administration, accédez à **groupes**  >  **Ajouter un groupe**.

3. Sélectionnez **groupe de sécurité à extension messagerie** , puis renseignez les champs **nom**, **adresse de messagerie du groupe**et **Description** pour le nouveau groupe.

4. Enregistrez le groupe.  La configuration totale du groupe peut prendre quelques minutes et s’affiche dans le Centre d’administration Microsoft 365.

5. Sélectionnez le nouveau groupe approbateur et sélectionnez **modifier** pour ajouter des utilisateurs au groupe.

6. Enregistrez le groupe.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>Étape 2 : activer l’accès privilégié

### <a name="in-the-microsoft-365-admin-center"></a>Dans le centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Activez le contrôle **exiger des approbations pour les tâches privilégiées** .

4. Affectez le groupe d’approbateurs que vous avez créé à l’étape 1 comme **groupe d’approbateurs par défaut**.

5. **Enregistrer** et **Fermer**.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour activer l’accès privilégié et attribuer le groupe de l’approbateur, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Exemple :

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', sys2@fabrikamorg.onmicrosoft.com')
```

>[!NOTE]
>La fonctionnalité comptes système est mise à disposition pour garantir que certaines automations au sein de vos organisations peuvent fonctionner sans dépendance sur l’accès privilégié, mais il est recommandé que ces exclusions soient exceptionnelles et que celles autorisées soient approuvées et auditées régulièrement.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>Étape 3 : créer une stratégie d’accès

Vous pouvez créer et configurer jusqu’à 30 stratégies d’accès privilégié pour votre organisation.

### <a name="in-the-microsoft-365-admin-center"></a>Dans le centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **configurer les stratégies** et sélectionnez **Ajouter une stratégie**.

5. Dans les champs de liste déroulante, sélectionnez les valeurs appropriées pour votre organisation :
    
    **Type de stratégie** : tâche, rôle ou groupe de rôles

    **Étendue de la stratégie** : Exchange

    **Nom de la stratégie** : sélection parmi les stratégies disponibles

    **Type d’approbation** : manuel ou automatique

    **Groupe d’approbation** : sélection du groupe d’approbateurs créé à l’Étape 1.

6. Sélectionnez **créer** , puis **Fermer**. La configuration et l’activation de la stratégie peuvent prendre quelques minutes.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour créer et définir une stratégie d’approbation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Exemple :

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>Étape 4 : soumettre/approuver des demandes d’accès privilégié

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Demander une autorisation d’élévation pour l’exécution de tâches privilégiées

Les demandes d’accès privilégié sont valables pendant 24 heures après l’envoi de la demande. En cas de rejet ou de refus, les demandes expirent et l’accès n’est pas approuvé.

#### <a name="in-the-microsoft-365-admin-center"></a>Dans le centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **nouvelle demande**. Dans les champs de liste déroulante, sélectionnez les valeurs appropriées pour votre organisation :

    **Type de demande** : tâche, rôle ou groupe de rôles

    **Étendue de la demande** : Exchange

    **Demande pour** : sélection parmi les stratégies disponibles

    **Durée (heures)**  : nombre d’heures d’accès demandé. Il n’y a pas de limite sur le nombre d’heures qui peuvent être demandées.

    **Commentaires**: champ de texte pour les commentaires liés à votre demande d’accès

5. Sélectionnez **Enregistrer** , puis **Fermer**. Votre demande sera envoyée au groupe de l’approbateur par courrier électronique.

#### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Exécutez la commande suivante dans Exchange Online PowerShell pour créer et soumettre une demande d’approbation au groupe de l’approbateur :

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Exemple :

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Afficher le statut des demandes d’élévation

Après la création d’une demande d’approbation, l’état de la demande d’élévation peut être révisé dans le centre d’administration ou dans Exchange Management PowerShell à l’aide de l’ID de demande associé.

#### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec vos informations d’identification.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **affichage** pour filtrer les demandes soumises par état **en attente**, **approuvé**, **refusé**ou **référentiel sécurisé du client** .

#### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher l’état d’une demande d’approbation pour un ID de demande spécifique :

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Exemple :

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Approbation d’une demande d’autorisation d’élévation

Lorsqu’une demande d’approbation est créée, les membres du groupe d’approbateur approprié reçoivent une notification par courrier électronique et peuvent approuver la demande associée à l’ID de demande. Le demandeur est informé de l’approbation ou du refus par message électronique.

#### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec vos informations d’identification.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez une demande répertoriée pour afficher les détails et agir sur la demande.

5. Sélectionnez **approuver** pour approuver la demande ou **refuser** pour la refuser. Les demandes précédemment approuvées peuvent avoir un accès révoqué en sélectionnant **Revoke**.

#### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour approuver une demande d’autorisation d’élévation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Exemple :

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Pour refuser une demande d’autorisation d’élévation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Deny-ElevatedAccessRequest -RequestId <request id> -Comment '<denial comment>'
```

Exemple :

```PowerShell
Deny-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<denial comment>'
```

## <a name="delete-a-privileged-access-policy-in-office-365"></a>Supprimer une stratégie d’accès privilégié dans Office 365

Si elle n’est plus nécessaire dans votre organisation, vous pouvez supprimer une stratégie d’accès privilégié.

### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Sélectionnez **gérer les stratégies d’accès et les demandes**.

4. Sélectionnez **configurer les stratégies**.

5. Sélectionnez la stratégie à supprimer, puis **Supprimer la stratégie**.

6. Sélectionnez **Fermer**.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour supprimer une stratégie d’accès privilégié, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Désactivation de l’accès privilégié dans Office 365

Si nécessaire, vous pouvez désactiver la gestion des accès privilégiés pour votre organisation. La désactivation de l’accès privilégié ne supprime pas les stratégies d’approbation ou les groupes d’approbateurs associés.

### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec des informations d’identification pour un compte d’administrateur de votre organisation.

2. Dans le centre d’administration, accédez à **paramètres**  >  **Organisation des paramètres d’organisation**  >  **sécurité & confidentialité**des  >  **accès privilégiés**.

3. Activez l' **autorisation exiger des approbations pour le contrôle d’accès privilégié** .

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour désactiver l’accès privilégié, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Disable-ElevatedAccessControl
```
