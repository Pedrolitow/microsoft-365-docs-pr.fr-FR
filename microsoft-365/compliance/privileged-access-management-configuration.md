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
- m365-security-compliance
- m365solution-insiderrisk
- m365initiative-compliance
ms.custom:
- Ent_Solutions
- seo-marvel-apr2020
ms.assetid: ''
description: Utilisez cet article pour en savoir plus sur l’activation et la configuration de la gestion des accès privilégiés dans Office 365.
ms.openlocfilehash: 0b8d79c3012ecd321d7b00c1566aa557077d55f1
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126531"
---
# <a name="get-started-with-privileged-access-management"></a>Prise en main de la gestion des accès privilégiés

Cette rubrique vous guide tout au long de l’activation et de la configuration de la gestion des accès privilégiés dans votre organisation. Vous pouvez utiliser le Centre d’administration Microsoft 365 ou Exchange Management PowerShell pour gérer et utiliser l’accès privilégié.

## <a name="before-you-begin"></a>Avant de commencer

Avant de commencer à gérer les accès privilégiés, vous devez confirmer votre abonnement [Microsoft 365](https://www.microsoft.com/microsoft-365/compare-all-microsoft-365-plans) et les modules. Pour accéder à la gestion des accès privilégiés et l’utiliser, votre organisation doit avoir l’un des abonnements ou modules suivants :

- Abonnement Microsoft 365 E5 (version payante ou d’essai)
- Abonnement Microsoft 365 E3 (ou abonnement Office 365 E3 + Abonnement Enterprise Mobility and Security E3) + module de conformité Microsoft 365 E5
- Tout abonnement Microsoft 365, Office 365, Exchange, SharePoint ou OneDrive Entreprise + le module de gestion des risques internes Microsoft 365 E5  
- Abonnement Microsoft 365 A5 (version payante ou d’essai)
- Abonnement Microsoft 365 A3 (ou abonnement Office 365 A3 + abonnement Enterprise Mobility and Security A3) + module de conformité Microsoft A5
- Tout abonnement Microsoft 365, Office 365, Exchange, SharePoint ou OneDrive Éducation + le module de gestion des risques internes Microsoft 365 A5
- Abonnement Office 365 Entreprise E5 (version payante ou d’essai)
- Abonnement Office 365 Entreprise E3 + module de conformité avancée Office 365 (non disponible pour les nouveaux abonnements, voir la remarque)

Les utilisateurs qui envoient des demandes de gestion des accès privilégiés et y répondent doivent se voir attribuer l’une des licences ci-dessus.

>[!IMPORTANT]
>La conformité avancée Office 365 n’est plus vendue en tant qu’abonnement autonome. Lorsque les abonnements actuels expirent, les clients doivent passer à l’un des abonnements ci-dessus, qui contient les mêmes fonctionnalités de conformité ou des fonctionnalités supplémentaires.

Si vous n’avez pas de plan Office 365 Entreprise E5 existant et que vous souhaitez essayer la gestion des accès [](https://www.microsoft.com/microsoft-365/enterprise) privilégiés, vous pouvez ajouter [Microsoft 365](/office365/admin/try-or-buy-microsoft-365) à votre abonnement Office 365 existant ou vous inscrire à une version d’essai de Microsoft 365 Entreprise E5.

## <a name="enable-and-configure-privileged-access-management"></a>Activer et configurer la gestion des accès privilégiés

Suivez ces étapes pour configurer et utiliser l’accès privilégié dans votre organisation :

- [Étape 1 : Créer un groupe d’approbation](privileged-access-management-configuration.md#step1)

    Avant de commencer à utiliser l’accès privilégié, déterminez qui a besoin de l’autorité d’approbation pour les demandes entrantes permettant d’accéder à des tâches avec élévation de privilèges. Tout utilisateur faisant partie du groupe d’approbateurs peut approuver les demandes d’accès. Ce groupe est activé en créant un groupe de sécurité à messagerie dans Office 365.

- [Étape 2 : Activer l’accès privilégié](privileged-access-management-configuration.md#step2)

    Les accès privilégiés doivent être activés de manière explicite dans Office 365 avec le groupe d’approbateurs par défaut, y compris un ensemble de comptes système que vous souhaitez exclure du contrôle d’accès par gestion des accès privilégiés.

- [Étape 3 : Créer une stratégie d’accès](privileged-access-management-configuration.md#step3)

    La création d’une stratégie d’approbation vous permet de définir les exigences d’approbation spécifiques d’une tâche spécifique. Les options type d’approbation sont **Automatiques** ou **Manuelles**.

- [Étape 4 : Envoyer/approuver des demandes d’accès privilégié](privileged-access-management-configuration.md#step4)

    Une fois activé, l’accès privilégié nécessite des approbations pour toutes les tâches auxquelles une stratégie d’approbation associée est définie. Pour les tâches incluses dans une stratégie d’approbation, les utilisateurs doivent demander et se voir autoriser d’accès afin d’obtenir les autorisations nécessaires pour exécuter la tâche.

Une fois l’approbation accordée, l’utilisateur demandeur peut exécuter la tâche prévue et l’accès privilégié autorise et exécute la tâche au nom de l’utilisateur. L’approbation reste valide pendant la durée demandée (la durée par défaut est de 4 heures), période durant laquelle le demandeur peut effectuer la tâche prévue plusieurs fois. Toutes ces réalisations sont enregistrées et mises à disposition pour l’audit sur la sécurité et la conformité. 

>[!NOTE]
>Si vous souhaitez utiliser Exchange Management PowerShell pour activer et configurer l’accès privilégié, suivez les étapes de la procédure de connexion à Exchange Online PowerShell à l’aide de l’authentification [multifacteur](/powershell/exchange/connect-to-exchange-online-powershell#connect-to-exchange-online-powershell-using-mfa) pour vous connecter à Exchange Online PowerShell avec vos informations d’identification Office 365. Il n’est pas nécessaire d’activer l’authentification multifacteur pour que votre organisation utilise les étapes permettant d’activer l’accès privilégié lors de la connexion à Exchange Online PowerShell. La connexion avec l’authentification multifacteur crée un jeton OAuth qui est utilisé par l’accès privilégié pour la signature de vos demandes.

<a name="step1"> </a>

## <a name="step-1-create-an-approvers-group"></a>Étape 1 : Créer un groupe d’approbation

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre d’administration, allez à **Groupes**  >  **Ajouter un groupe.**

3. Sélectionnez **le groupe de** sécurité à messagerie, puis complétez les champs Nom, Adresse de **messagerie** du groupe et **Description** du nouveau groupe. 

4. Enregistrez le groupe.  La configuration totale du groupe peut prendre quelques minutes et s’affiche dans le Centre d’administration Microsoft 365.

5. Sélectionnez le groupe du nouvel approuveur et sélectionnez **Modifier** pour ajouter des utilisateurs au groupe.

6. Enregistrez le groupe.

<a name="step2"> </a>

## <a name="step-2-enable-privileged-access"></a>Étape 2 : Activer l’accès privilégié

### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre d’administration, accédez à   >  **Paramètres Org Settings**  >  **Security & Privacy**  >  **Privileged Access**.

3. Activez **le contrôle Exiger des approbations pour les tâches privilégiées.**

4. Affectez le groupe de l’approuveur que vous avez créé à l’étape 1 en tant que groupe **d’approbations par défaut.**

5. **Enregistrer** et **fermer**.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour activer l’accès privilégié et affecter le groupe de l’approuveur, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Enable-ElevatedAccessControl -AdminGroup '<default approver group>' -SystemAccounts @('<systemAccountUPN1>','<systemAccountUPN2>')
```

Exemple :

```PowerShell
Enable-ElevatedAccessControl -AdminGroup 'pamapprovers@fabrikam.onmicrosoft.com' -SystemAccounts @('sys1@fabrikamorg.onmicrosoft.com', 'sys2@fabrikamorg.onmicrosoft.com')
```

>[!NOTE]
>La fonctionnalité comptes système est mise à disposition pour garantir que certaines automatisations au sein de vos organisations peuvent fonctionner sans dépendance sur l’accès privilégié. Toutefois, il est recommandé que ces exclusions soient exceptionnelles et que celles autorisées doivent être approuvées et auditées régulièrement.

<a name="step3"> </a>

## <a name="step-3-create-an-access-policy"></a>Étape 3 : Créer une stratégie d’accès

Vous pouvez créer et configurer jusqu’à 30 stratégies d’accès privilégié pour votre organisation.

### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre d’administration, accédez à   >  **Paramètres Org Settings**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez **Configurer des stratégies** et **ajouter une stratégie.**

5. Dans les champs de la baisse, sélectionnez les valeurs appropriées pour votre organisation :
    
    **Type de stratégie** : tâche, rôle ou groupe de rôles

    **Étendue de la stratégie** : Exchange

    **Nom de la stratégie** : sélection parmi les stratégies disponibles

    **Type d’approbation** : manuel ou automatique

    **Groupe d’approbation** : sélection du groupe d’approbateurs créé à l’Étape 1.

6. Sélectionnez **Créer,** puis **Fermer.** La configuration et l’activé de la stratégie peuvent prendre quelques minutes.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour créer et définir une stratégie d’approbation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\<exchange management cmdlet name>' -ApprovalType <Manual, Auto> -ApproverGroup '<default/custom approver group>'
```

Exemple :

```PowerShell
New-ElevatedAccessApprovalPolicy -Task 'Exchange\New-MoveRequest' -ApprovalType Manual -ApproverGroup 'mbmanagers@fabrikamorg.onmicrosoft.com'
```

<a name="step4"> </a>

## <a name="step-4-submitapprove-privileged-access-requests"></a>Étape 4 : Envoyer/approuver des demandes d’accès privilégié

### <a name="requesting-elevation-authorization-to-execute-privileged-tasks"></a>Demander une autorisation d’élévation pour l’exécution de tâches privilégiées

Les demandes d’accès privilégié sont valables pendant 24 heures après l’envoi de la demande. En cas de rejet ou de refus, les demandes expirent et l’accès n’est pas approuvé.

#### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) à l’aide de vos informations d’identification.

2. Dans le Centre d’administration, accédez à   >  **Paramètres Org Settings**  >  **Security & Privacy**  >  **Privileged Access**.

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez **Nouvelle requête**. Dans les champs de la baisse, sélectionnez les valeurs appropriées pour votre organisation :

    **Type de demande** : tâche, rôle ou groupe de rôles

    **Étendue de la demande** : Exchange

    **Demande pour** : sélection parmi les stratégies disponibles

    **Durée (heures)**  : nombre d’heures d’accès demandé. Le nombre d’heures qui peuvent être demandées n’est pas limité.

    **Commentaires :** champ texte pour les commentaires liés à votre demande d’accès

5. Sélectionnez **Enregistrer,** puis **Fermer.** Votre demande est envoyée au groupe de l’approuveur par courrier électronique.

#### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Exécutez la commande suivante dans Exchange Online PowerShell pour créer et envoyer une demande d’approbation au groupe de l’approuveur :

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\<exchange management cmdlet name>' -Reason '<appropriate reason>' -DurationHours <duration in hours>
```

Exemple :

```PowerShell
New-ElevatedAccessRequest -Task 'Exchange\New-MoveRequest' -Reason 'Attempting to fix the user mailbox error' -DurationHours 4
```

### <a name="view-status-of-elevation-requests"></a>Afficher le statut des demandes d’élévation

Une fois qu’une demande d’approbation est créée, l’état de la demande d’élévation peut être examiné dans le Centre d’administration ou dans Exchange Management PowerShell à l’aide de l’ID de demande associé.

#### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous [au Centre d’administration Microsoft 365](https://admin.microsoft.com) avec vos informations d’identification.

2. Dans le Centre d’administration, accédez à **Paramètres** De l’organisation  >  **Paramètres** Sécurité  >  **& Accès**  >  **privilégié à la confidentialité.**

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez **Affichage** pour filtrer les demandes envoyées par **état En attente,** **Approuvé,** Refusé **ou** **Customer Lockbox.**

#### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Exécutez la commande suivante dans Exchange Online PowerShell pour afficher l’état d’une demande d’approbation pour un ID de demande spécifique :

```PowerShell
Get-ElevatedAccessRequest -Identity <request ID> | select RequestStatus
```

Exemple :

```PowerShell
Get-ElevatedAccessRequest -Identity 28560ed0-419d-4cc3-8f5b-603911cbd450 | select RequestStatus
```

### <a name="approving-an-elevation-authorization-request"></a>Approbation d’une demande d’autorisation d’élévation

Lorsqu’une demande d’approbation est créée, les membres du groupe d’approbation approprié reçoivent une notification par courrier électronique et peuvent approuver la demande associée à l’ID de demande. Le demandeur est informé de l’approbation ou du refus par message électronique.

#### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous [au Centre d’administration Microsoft 365](https://admin.microsoft.com) avec vos informations d’identification.

2. Dans le Centre d’administration, accédez à **Paramètres** De l’organisation  >  **Paramètres** Sécurité  >  **& Accès**  >  **privilégié à la confidentialité.**

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez une demande répertoriée pour afficher les détails et prendre des mesures sur la demande.

5. Sélectionnez **Approuver** pour approuver la demande ou **Refuser** pour refuser la demande. Les demandes précédemment approuvées peuvent être révoquées en sélectionnant **Révoquer.**

#### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour approuver une demande d’autorisation d’élévation, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Approve-ElevatedAccessRequest -RequestId <request id> -Comment '<approval comment>'
```

Exemple :

```PowerShell
Approve-ElevatedAccessRequest -RequestId a4bc1bdf-00a1-42b4-be65-b6c63d6be279 -Comment '<approval comment>'
```

Pour refuser une demande d’autorisation d’élévation, exécutez la commande suivante dans Exchange Online PowerShell :

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

2. Dans le Centre d’administration, accédez à **Paramètres** De l’organisation Paramètres Sécurité & Accès privilégié à  >    >    >  **la confidentialité.**

3. Sélectionnez **Gérer les stratégies et les demandes d’accès.**

4. Sélectionnez **Configurer les stratégies.**

5. Sélectionnez la stratégie à supprimer, puis **sélectionnez Supprimer la stratégie.**

6. Sélectionnez **Fermer**.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour supprimer une stratégie d’accès privilégié, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Remove-ElevatedAccessApprovalPolicy -Identity <identity GUID of the policy you want to delete>
```

## <a name="disable-privileged-access-in-office-365"></a>Désactiver l’accès privilégié dans Office 365

Si nécessaire, vous pouvez désactiver la gestion des accès privilégiés pour votre organisation. La désactivation de l’accès privilégié ne supprime pas les stratégies d’approbation ou les groupes d’approbation associés.

### <a name="in-the-microsoft-365-admin-center"></a>Dans le Centre d’administration Microsoft 365

1. Connectez-vous [au Centre d’administration Microsoft 365](https://admin.microsoft.com) avec les informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le Centre d’administration, accédez à   >  **Paramètres Org Settings**  >  **Security & Privacy**  >  **Privileged Access**.

3. Activez **la commande Exiger des approbations pour le contrôle d’accès** privilégié.

### <a name="in-exchange-management-powershell"></a>Dans Exchange Management PowerShell

Pour désactiver l’accès privilégié, exécutez la commande suivante dans Exchange Online PowerShell :

```PowerShell
Disable-ElevatedAccessControl
```
