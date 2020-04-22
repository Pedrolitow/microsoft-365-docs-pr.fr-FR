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
ms.openlocfilehash: b70c7013ce038a3934b7ea5e62d1d0530f12e4e6
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43634315"
---
# <a name="safe-documents-in-office-365-advanced-threat-protection"></a>Documents approuvés dans Office 365 protection avancée contre les menaces

Documents approuvés est une fonctionnalité d’Office 365 protection avancée contre les menaces qui utilise la [protection avancée contre les menaces de Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser les documents et les fichiers ouverts en [mode protégé](https://support.office.com/article/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Cette fonctionnalité est disponible uniquement pour les utilisateurs disposant de la licence de sécurité Microsoft 365 E5 ou Microsoft 365 E5.

- Les documents approuvés sont actuellement disponibles pour la préversion publique, disponibles pour les utilisateurs qui font partie du [programme Office Insider](https://insider.office.com/en-us/join) sur le canal mensuel (ciblé) avec Office version 2002 (12527,20092) ou supérieur. Cette fonctionnalité est désactivée par défaut et doit être activée par l’administrateur de la sécurité.

- Seule région américaine prise en charge pour le traitement de fichiers conformes (tous les fichiers sont acheminés vers la région américaine pour analyse). La prise en charge de la France/de la région de l’UE est prévue dans une prochaine mise à jour.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online/connect-to-exchange-online-powershell/connect-to-exchange-online-powershell). Pour vous connecter à Exchange Online Protection PowerShell, consultez la rubrique [Connect to Exchange Online Protection PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-eop/connect-to-exchange-online-protection-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir effectuer les procédures de cette rubrique. Pour activer et configurer des documents approuvés, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** . Pour plus d’informations sur les groupes de rôles dans le centre de sécurité & conformité, consultez [la rubrique autorisations dans le centre de sécurité & conformité](permissions-in-the-security-and-compliance-center.md).

## <a name="use-the-security--compliance-center-to-configure-safe-documents"></a>Utiliser le centre de sécurité & conformité pour configurer des documents approuvés

1. Ouvrez le centre de sécurité & conformité <https://protection.office.com>à l’adresse.

2. Accédez à la **stratégie** \> de **gestion** \> des menaces **pièces jointes sûres ATP**.

3. Dans la section **aider les utilisateurs à rester sûrs lors de l’approbation d’un fichier à ouvrir en dehors du mode protégé dans les applications Office** , configurez l’un des paramètres suivants :

   - **Activer les documents approuvés pour les clients Office (les fichiers seront également envoyés vers Microsoft Cloud pour les analyses en profondeur)**

   - **Autoriser les utilisateurs à cliquer en mode protégé même si les documents approuvés identifient le fichier comme malveillant**: nous vous recommandons de ne pas activer cette option.

4. Lorsque vous avez terminé, cliquez sur **Enregistrer**.

![Page pièces jointes approuvées ATP](../../media/safe-docs.png)

### <a name="use-exchange-online-powershell-or-exchange-online-protection-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell ou Exchange Online Protection PowerShell pour configurer des documents fiables

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

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez la rubrique [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/advanced-threat-protection/set-atppolicyforo365).

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez bien activé et configuré les documents approuvés, effectuez l’une des opérations suivantes :

- Dans le centre de sécurité & conformité, accédez à la **stratégie** \> de **gestion** \> des menaces **pièces jointes**au niveau de sécurité ATP et vérifiez que les sélections dans la section **aider les utilisateurs à rester sécurisés lors de l’ouverture d’un fichier pour ouvrir en dehors de la section applications Office** .

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs des propriétés :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```
