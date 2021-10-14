---
title: Gérer vos autoriser dans la liste d’attente des locataires
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à configurer les autoriser dans la liste d’adresses client autoriser/bloquer dans le portail de sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 98ae7b53ce793809ae93cf32d574d979e5b7c6e5
ms.sourcegitcommit: be074f57e33c811bb3857043152825209bc8af07
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/13/2021
ms.locfileid: "60335561"
---
# <a name="add-allows-in-the-tenant-allowblock-list"></a>Ajouter des autorisations dans la liste verte/rouge du client

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les administrateurs ne peuvent pas ajouter d’autoriser directement à la liste d’adresses client autoriser/bloquer. Au lieu de cela, vous utilisez le processus de soumission de l’administrateur pour envoyer le message qui a été bloqué afin que l’URL, le fichier et/ou les expéditeurs correspondants soient ajoutés à la liste d’adresses client autoriser/bloquer. Dans la plupart des cas où le message a été déterminé comme faux positif qui a été incorrectement bloqué, les autorise sont conservées aussi longtemps que nécessaire pour donner au système le temps de l’autoriser naturellement.

> [!IMPORTANT]
>
> Étant donné que Microsoft gère les allows pour vous, l’expéditeur, l’URL ou le fichier permet qui ne sont pas nécessaires ou considérés comme étant mauvais sera supprimé. Il s’agit de protéger votre environnement et d’éviter une mauvaise configuration des autoriser. Dans les cas où vous n’êtes pas d’accord, un dossier de support peut être nécessaire pour vous aider à déterminer pourquoi un message est toujours considéré comme mauvais.

## <a name="add-allows-using-the-submissions-portal"></a>Ajouter des autoriser à l’aide du portail soumissions 

Autorisez les fichiers, les URL et les expéditeurs dans la section Soumissions de Microsoft 365 Defender. 

1. Dans le portail Microsoft 365 Defender, go to **Email & collaboration** \> **Submissions**.

2. Dans la page **Soumissions,** vérifiez que l’onglet Soumis pour analyse est sélectionné, puis cliquez sur  ![ l’icône Ad.](../../media/m365-cc-sc-create-icon.png) **Envoyer à Microsoft pour analyse.**

3. Utilisez le **volant Envoyer à Microsoft** pour révision pour envoyer un message, soit en ajoutant l’ID de message réseau, soit en téléchargeant le fichier de courrier électronique. 

4. Dans la section **Sélectionner une raison pour l’envoi à Microsoft,** sélectionnez Ne pas avoir été bloqué **(faux positif).** 

5. Activer **l’option Autoriser les messages comme celle-ci.** 

6. Dans la **liste supprimée après** la liste, spécifiez la durée de fonctionnement de l’option d’option d’autoriser.

7. Lorsque vous avez terminé, cliquez sur le **bouton** Envoyer.

> [!div class="mx-imgBorder"]
> ![Exemple d’envoi de faux positif.](../../media/admin-submission-allow-messages.png)

## <a name="create-spoofed-sender-allow-entries-using-microsoft-365-defender"></a>Créer des entrées d’expéditeurs usurpées à l’aide Microsoft 365 Defender

> [!NOTE]
> 
> - Seule la _combinaison_ de l’utilisateur usurpé et de l’infrastructure d’envoi, telle que définie dans la paire de domaines, est spécifiquement autorisée ou bloquée à l’usurpation. 
> - Lorsque vous configurez une entrée d’autoriser ou de bloquer une paire de domaines, les messages de cette paire de domaines n’apparaissent plus dans l’aperçu de l’usurpation d’intelligence.
> - Les entrées des expéditeurs usurpés n’expirent jamais.
> - L’usurpation prend en charge à la fois autoriser et bloquer. L’URL prend uniquement en charge l’autoriser.

1. Dans le portail Microsoft 365 Defender, go to **Policies &** \> **Threat Policies** \> **Rules** section \> **Tenant Allow/Block Lists**.

2. Dans la page **Liste d’attente des** locataires, sélectionnez l’onglet **Usurpation** d’informations, puis cliquez sur Icône ![ Bloquer.](../../media/m365-cc-sc-create-icon.png) **Ajouter**.

3. Dans le **volant Ajouter de nouvelles paires de domaines** qui s’affiche, configurez les paramètres suivants :
   - **Ajoutez de nouvelles paires de domaines avec des caractères génériques**: entrez une paire de domaines par ligne, jusqu’à un maximum de 20. Pour plus d’informations sur la syntaxe des entrées d’expéditeur usurpées, voir Gérer la liste d’adresses client [autoriser/bloquer.](tenant-allow-block-list.md)
   - **Type d’usurpation**: sélectionnez l’une des valeurs suivantes :
     - **Interne**: l’expéditeur usurpé se trouve dans un domaine appartenant à votre organisation [(un domaine accepté).](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains)
     - **Externe**: l’expéditeur usurpé se trouve dans un domaine externe.
   - **Action**: **sélectionnez Autoriser** ou **Bloquer**.

4. Lorsque vous avez terminé, cliquez sur **Ajouter**.

## <a name="add-spoofed-sender-allow-entries-using-powershell"></a>Ajouter des entrées d’expéditeur usurpées à l’aide de PowerShell

Pour ajouter des entrées d’expéditeur usurpées dans la liste d’adresses client autoriser/bloquer, utilisez la syntaxe suivante :

```powershell
New-TenantAllowBlockListSpoofItems -SpoofedUser <Domain | EmailAddress | *> -SendingInfrastructure <Domain | IPAddress/24> -SpoofType <External | Internal> -Action <Allow | Block>
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TenantAllowBlockListSpoofItems](/powershell/module/exchange/new-tenantallowblocklistspoofitems).

## <a name="related-articles"></a>Articles connexes

- [Envois par l’administrateur](admin-submission.md)
- [Signaler les faux positifs et les faux négatifs](report-false-positives-and-false-negatives.md)
