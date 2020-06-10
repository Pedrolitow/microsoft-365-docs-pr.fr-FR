---
title: Documents sécurisés dans Office 365 PACM
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Découvrez les documents sûrs dans Office 365 dav.
ms.openlocfilehash: e9b1fadd3e9e6dab337a0c3ded380c5c49f53bab
ms.sourcegitcommit: 584e2e9db8c541fe32624acdca5e12ee327fdb63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44678669"
---
# <a name="safe-documents-in-office-365-advanced-threat-protection"></a>Documents fiables dans Office 365 - Protection avancée contre les menaces

La fonctionnalité documents approuvés est une fonctionnalité d’Office 365 protection avancée contre les menaces (Office 365 ATP) qui utilise la [protection avancée contre les menaces de Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser les documents et les fichiers ouverts en [mode protégé](https://support.office.com/article/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Cette fonctionnalité est disponible uniquement pour les utilisateurs disposant de la licence de sécurité Microsoft 365 E5 ou Microsoft 365 E5.

- Les documents approuvés sont actuellement disponibles pour la préversion publique, disponibles pour les utilisateurs qui font partie du [programme Office Insider](https://insider.office.com/en-us/join) sur le canal actuel (aperçu) avec Office version 2002 (12527,20092) ou supérieur. Cette fonctionnalité est désactivée par défaut et doit être activée par l’administrateur de la sécurité.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell). Pour vous connecter à un service Exchange Online Protection PowerShell autonome, voir [Se connecter à Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir effectuer les procédures de cette rubrique. Pour activer et configurer des documents approuvés, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** . Pour des informations supplémentaires sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour rester protégé, les documents fiables envoient des fichiers au Cloud de [protection avancée contre les menaces Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyse.

- Vous trouverez [ici](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy) des informations détaillées sur la façon dont Microsoft Defender Advanced thread protection gère vos données.
- Outre les instructions ci-dessus, les fichiers envoyés par des documents approuvés ne sont pas conservés dans Defender au-delà du temps nécessaire à l’analyse, ce qui correspond généralement à moins de 24 heures.

## <a name="use-the-security--compliance-center-to-configure-safe-documents"></a>Utiliser le centre de sécurité & conformité pour configurer des documents approuvés

1. Ouvrez le centre de sécurité & conformité à l’adresse <https://protection.office.com> .

2. Accédez à la stratégie de **gestion des menaces** \> **Policy** \> **pièces jointes sûres ATP**.

3. Dans la section **aider les utilisateurs à rester sûrs lors de l’approbation d’un fichier à ouvrir en dehors du mode protégé dans les applications Office** , configurez l’un des paramètres suivants :

   - **Activer les documents approuvés pour les clients Office (les fichiers seront également envoyés vers Microsoft Cloud pour les analyses en profondeur)**

   - **Autoriser les utilisateurs à cliquer en mode protégé même si les documents approuvés identifient le fichier comme malveillant**: nous vous recommandons de ne pas activer cette option.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

![Page pièces jointes approuvées ATP](../../media/safe-docs.png)

### <a name="use-exchange-online-powershell-or-standalone-eop-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell ou le PowerShell autonome EOP pour configurer des documents fiables

Utilisez la syntaxe suivante :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true|$false> -AllowSafeDocsOpen <$true|$false>
```

- Le paramètre _EnableSafeDocs_ active ou désactive les documents approuvés pour l’ensemble de l’organisation.

- Le paramètre _AllowSafeDocsOpen_ autorise ou empêche les utilisateurs de quitter le mode protégé (c’est-à-dire, d’ouvrir le document) si le document a été identifié comme malveillant.

Cet exemple active les documents sécurisés pour l’ensemble de l’organisation et empêche les utilisateurs d’ouvrir des documents identifiés comme étant malveillants en mode protégé.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365).

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien activé et configuré les documents approuvés, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** \> **Policy** \> **pièces jointes**au niveau de sécurité ATP et vérifiez que les sélections dans la section **aider les utilisateurs à rester sécurisés lors de l’ouverture d’un fichier pour ouvrir en dehors de la section applications Office** .

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs des propriétés :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```
