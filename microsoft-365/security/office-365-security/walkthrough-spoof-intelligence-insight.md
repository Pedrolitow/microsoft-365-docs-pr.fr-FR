---
title: Gérer les expéditeurs usurpés à l’aide de la stratégie de renseignement sur l’usurpation d’identité et de l’information sur l’usurpation d’identité
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: overview
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 59a3ecaf-15ed-483b-b824-d98961d88bdd
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à utiliser la stratégie de renseignement sur l’usurpation d’identité et l’information sur l’usurpation d’identité pour autoriser ou bloquer les expéditeurs détectés d’usurpation d’identité.
ms.custom:
- seo-marvel-apr2020
ms.technology: mdo
ms.prod: m365-security
ROBOTS: NOINDEX, NOFOLLOW
ms.openlocfilehash: f827046dc9a103e73eb6fb79ba161e523e2b2690
ms.sourcegitcommit: 725a92b0b1555572b306b285a0e7a7614d34e5e5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/24/2022
ms.locfileid: "65649350"
---
# <a name="manage-spoofed-senders-using-the-spoof-intelligence-policy-and-spoof-intelligence-insight-in-eop"></a>Gérer les expéditeurs usurpés à l’aide de la stratégie de renseignement sur l’usurpation d’identité et de l’information sur l’usurpation d’identité dans EOP

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

> [!IMPORTANT]
> La gestion des expéditeurs usurpés dans le portail Microsoft 365 Defender est désormais disponible uniquement sous l’onglet **Usurpation** d’identité dans la liste d’autorisation/de blocage du locataire. Pour connaître les procédures actuelles dans le portail Microsoft 365 Defender, consultez [Spoof Intelligence Insight dans EOP](learn-about-spoof-intelligence.md).
>
> La gestion des expéditeurs usurpés dans Exchange Online PowerShell ou EOP Autonome PowerShell est en cours de migration exclusivement vers les applets de commande **-TenantAllowBlockListSpoofItems, Get-SpoofIntelligenceInsight et Get-SpoofMailReport associées\***.  Pour connaître les procédures utilisant ces applets de commande, consultez les articles suivants :
>
> - [Afficher les entrées d’expéditeur usurpées à l’aide de PowerShell](tenant-allow-block-list.md#view-spoofed-sender-entries)
> - [Ajouter des entrées d’autorisation d’expéditeur usurpées à l’aide de PowerShell](manage-tenant-allows.md#add-spoofed-sender-allow-entries-using-powershell)
> - [Ajouter des entrées de bloc d’expéditeur usurpées à l’aide de PowerShell](manage-tenant-blocks.md#add-spoofed-sender-block-entries)
> - [Modifier des entrées d’expéditeur usurpées à l’aide de PowerShell](modify-remove-entries-tenant-allow-block.md#modify-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
> - [Supprimer les entrées d’expéditeur usurpées à l’aide de PowerShell](modify-remove-entries-tenant-allow-block.md#remove-allow-or-block-spoofed-sender-entries-from-the-tenant-allowblock-list)
>
> L’ancienne expérience de gestion des expéditeurs usurpés utilisant les applets de commande **Get-PhishFilterPolicy** et **Set-PhishFilterPolicy** est en cours de dépréciation, mais elle est toujours présentée dans cet article pour plus d’exhaustivité jusqu’à ce que les applets de commande soient supprimées partout.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cet article :
  - Pour modifier la stratégie d’usurpation d’identité ou activer ou désactiver l’usurpation d’identité, vous devez être membre de :
    - **Gestion de l'organisation**
    - **Administrateur de sécurité** <u>et</u> **configuration en mode seul** ou gestion de l’organisation **en mode affichage uniquement**.
  - Pour accéder en lecture seule à la stratégie de renseignement sur l’usurpation d’identité, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  **Remarques** :

  - L'ajout d'utilisateurs au rôle Azure Active Directory Domain Services correspondant dans le centre d'administration Microsoft 365 donne aux utilisateurs les autorisations _et_ autorisations requises pour d'autres fonctionnalités dans Microsoft 365. Pour plus d'informations, consultez [À propos des rôles d'administrateur](../../admin/add-users/about-admin-roles.md).
  - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

- Les options d’intelligence par usurpation d’identité sont [décrites dans les paramètres d’usurpation d’identité dans les stratégies anti-hameçonnage](set-up-anti-phishing-policies.md#spoof-settings).

- Vous pouvez activer, désactiver et configurer les paramètres d’intelligence d’usurpation d’identité dans les stratégies anti-hameçonnage. Pour obtenir des instructions basées sur votre abonnement, consultez l’une des rubriques suivantes :

  - [Configurez des stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).
  - [Configurez des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

- Pour connaître les paramètres recommandés pour l’intelligence par usurpation d’identité, consultez [les paramètres de stratégie anti-hameçonnage EOP](recommended-settings-for-eop-and-office365.md#eop-anti-phishing-policy-settings).

## <a name="use-powershell-to-manage-spoofed-senders"></a>Utiliser PowerShell pour gérer les expéditeurs usurpés

Pour afficher les expéditeurs autorisés et bloqués dans l’intelligence d’usurpation d’identité, utilisez la syntaxe suivante :

```powershell
Get-PhishFilterPolicy [-AllowedToSpoof <Yes | No | Partial>] [-ConfidenceLevel <Low | High>] [-DecisionBy <Admin | SpoofProtection>] [-Detailed] [-SpoofType <Internal | External>]
```

Cet exemple retourne des informations détaillées sur tous les expéditeurs autorisés à usurper des utilisateurs dans vos domaines.

```powershell
Get-PhishFilterPolicy -AllowedToSpoof Yes -Detailed -SpoofType Internal
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Get-PhishFilterPolicy](/powershell/module/exchange/get-phishfilterpolicy).

Pour configurer les expéditeurs autorisés et bloqués dans l’intelligence d’usurpation d’identité, procédez comme suit :

1. Capturez la liste actuelle des expéditeurs usurpés détectés en écrivant la sortie de l’applet de commande **Get-PhishFilterPolicy** dans un fichier CSV en exécutant la commande suivante :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```

2. Modifiez le fichier CSV pour ajouter ou modifier les valeurs suivantes :
   - **Expéditeur** (domaine dans l’enregistrement PTR du serveur source ou l’adresse IP/24)
   - **SpoofedUser** : l’une des valeurs suivantes :
     - Adresse e-mail de l’utilisateur interne.
     - Domaine de messagerie de l’utilisateur externe.
     - Valeur vide qui indique que vous souhaitez bloquer ou autoriser tous les messages usurpés de **l’expéditeur** spécifié, quelle que soit l’adresse e-mail usurpée.
   - **AllowedToSpoof** (Oui ou Non)
   - **SpoofType** (interne ou externe)

   Enregistrez le fichier, lisez le fichier et stockez le contenu sous la forme d’une variable nommée `$UpdateSpoofedSenders` en exécutant la commande suivante :

   ```powershell
   $UpdateSpoofedSenders = Get-Content -Raw "C:\My Documents\Spoofed Senders.csv"
   ```

3. Utilisez la `$UpdateSpoofedSenders` variable pour configurer la stratégie de renseignement sur l’usurpation d’identité en exécutant la commande suivante :

   ```powershell
   Set-PhishFilterPolicy -Identity Default -SpoofAllowBlockList $UpdateSpoofedSenders
   ```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-PhishFilterPolicy](/powershell/module/exchange/set-phishfilterpolicy).

## <a name="how-do-you-know-these-procedures-worked"></a>Comment savoir si ces procédures ont fonctionné ?

Pour vérifier que vous avez configuré l’intelligence par usurpation d’identité avec les expéditeurs autorisés et non autorisés à usurper d’identité, exécutez les commandes suivantes dans PowerShell pour afficher les expéditeurs autorisés et non autorisés à usurper :

  ```powershell
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType Internal
  Get-PhishFilterPolicy -AllowedToSpoof Yes -SpoofType External
  Get-PhishFilterPolicy -AllowedToSpoof No -SpoofType External
  ```

- Dans PowerShell, exécutez la commande suivante pour exporter la liste de tous les expéditeurs usurpés dans un fichier CSV :

   ```powershell
   Get-PhishFilterPolicy -Detailed | Export-CSV "C:\My Documents\Spoofed Senders.csv"
   ```
