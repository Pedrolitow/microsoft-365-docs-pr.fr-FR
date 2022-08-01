---
title: Protéger votre suite C avec la protection de compte Priority dans Microsoft Defender pour Office 365 Plan 2
description: Étapes de protection de votre suite C avec une protection de compte prioritaire. L’étiquetage d’un compte en tant que compte prioritaire permet d’optimiser la protection supplémentaire pour les modèles de flux de messagerie ciblant les cadres de l’entreprise, ainsi qu’une visibilité supplémentaire dans les rapports, les alertes et les enquêtes.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: de0de8b418036d6b8e73b9cf5ec8deafc24af6a9
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67106490"
---
# <a name="protect-your-c-suite-with-priority-account-protection"></a>Protégez votre suite C avec une protection de compte prioritaire

La protection prioritaire des comptes permet aux équipes informatiques et de sécurité de garantir une haute qualité de service et de protection pour les personnes critiques au sein de votre organisation. L’étiquetage d’un compte en tant que compte prioritaire permet d’optimiser la protection supplémentaire pour les modèles de flux de messagerie ciblant les cadres de l’entreprise, ainsi qu’une visibilité supplémentaire dans les rapports, les alertes et les enquêtes.

## <a name="what-youll-need"></a>Ce dont vous aurez besoin
- Microsoft Defender pour Office 365 plan 2 (inclus dans les plans E5)
- Autorisations suffisantes (rôle Administrateur de sécurité)
- 5 minutes pour effectuer les étapes ci-dessous.

## <a name="tag-priority-users"></a>Marquer les utilisateurs prioritaires
1. Identifiez les utilisateurs, groupes ou domaines que vous souhaitez marquer comme comptes prioritaires.
1. Connectez-vous au [portail de sécurité Microsoft](https://security.microsoft.com/) et accédez à Paramètres dans la barre de navigation de gauche.
1. Sélectionnez Email & collaboration sur la page qui se charge, puis cliquez sur Balises utilisateur
1. Dans la page Balises utilisateur, sélectionnez la balise de compte Priorité, puis appuyez sur Modifier la balise
1. Dans le menu volant qui s’affiche, sélectionnez Ajouter des membres
1. Recherchez les utilisateurs que vous souhaitez étiqueter, sélectionnez un ou plusieurs utilisateurs et appuyez sur Ajouter
1. Passez en revue les membres que vous avez sélectionnés, puis appuyez sur Suivant
1. Appuyez sur Envoyer pour confirmer les modifications

Pour savoir quelles sont les balises de compte de priorité, consultez [Gérer et surveiller les comptes de priorité - Administrateur Microsoft 365 | Microsoft Docs](../../../admin/setup/priority-accounts.md).

## <a name="next-steps"></a>Étapes suivantes
[Passez en revue la protection différenciée pour les utilisateurs marqués comme comptes prioritaires](../../office-365-security/configure-review-priority-account.md).

## <a name="powershell-configuration"></a>Configuration de PowerShell
Si vous souhaitez effectuer ces étapes via [PowerShell](/powershell/exchange/connect-to-exchange-online-powershell), vous pouvez le faire à l’aide des applets de commande suivantes :
1. Afficher la liste des comptes prioritaires : **Get-User -IsVIP | sélectionner Identity**
1. Ajouter un utilisateur à la liste des comptes prioritaires : **Set-User -VIP:$true -Identity \<Identity\>**
1. Supprimer un utilisateur de la liste des comptes prioritaires : **Set-User -VIP:$false -Identity \<Identity\>**
