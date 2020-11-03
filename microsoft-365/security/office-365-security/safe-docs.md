---
title: Documents approuvés dans Microsoft Defender pour Office 365
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Découvrez les documents sûrs dans Microsoft 365 E5 ou Microsoft 365 E5 sécurité.
ms.openlocfilehash: 7fbee440298aea3609665b62a946ae3ce2857e37
ms.sourcegitcommit: 815229e39a0f905d9f06717f00dc82e2a028fa7c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2020
ms.locfileid: "48845479"
---
# <a name="safe-documents-in-microsoft-365-e5"></a>Documents sécurisés dans Microsoft 365 E5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


Documents approuvés est une fonctionnalité de Microsoft 365 E5 ou Microsoft 365 E5 sécurité qui utilise [Microsoft Defender pour le point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser des documents et des fichiers ouverts en [mode protégé](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Les documents approuvés sont disponibles uniquement pour les utilisateurs disposant de licences de sécurité Microsoft *365 E5* ou *Microsoft 365 E5* . Ces licences ne sont pas incluses dans les plans Microsoft Defender pour Office 365.

- Les documents approuvés sont pris en charge dans les applications Microsoft 365 pour entreprise (anciennement appelé Office 365 ProPlus) version 2004 ou ultérieure.

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com>. Pour accéder directement à la page **pièces jointes approuvées ATP** , ouvrez <https://protection.office.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous être attribuées avant de pouvoir effectuer les procédures de cette rubrique. Pour activer et configurer des documents approuvés, vous devez être membre des groupes de rôles gestion de l' **organisation** ou **administrateur de sécurité** . Pour des informations supplémentaires sur les groupes de rôles dans le Centre de sécurité et conformité, voir [Autorisations dans le Centre de sécurité et conformité](permissions-in-the-security-and-compliance-center.md).

### <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour rester protégé, les documents fiables envoient des fichiers au Cloud [Microsoft Defender pour les points de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyse. Vous trouverez ci-dessous des détails sur la façon dont Microsoft Defender pour les points de terminaison gère vos données : [Microsoft Defender pour le stockage et la confidentialité des données de point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Les fichiers envoyés par des documents approuvés ne sont pas conservés dans Defender au-delà du temps nécessaire à l’analyse (généralement, moins de 24 heures).

## <a name="use-the-security--compliance-center-to-configure-safe-documents"></a>Utiliser le centre de sécurité & conformité pour configurer des documents approuvés

1. Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** - \> **Policy** \> **pièces jointes ATP** , puis cliquez sur **paramètres globaux**.

2. Dans les **paramètres globaux** , effectuer un survol qui s’affiche, configurez les paramètres suivants :

   - **Activer les documents approuvés pour les clients Office** : déplacez le bouton bascule vers la droite pour activer la fonctionnalité : ![ activer/désactiver ](../../media/963dfcd0-1765-4306-bcce-c3008c4406b9.png) .

   - **Autoriser les utilisateurs à cliquer en mode protégé même si les documents approuvés identifient le fichier comme malveillant** : nous vous recommandons de laisser cette option désactivée (laissez le bouton bascule vers la gauche : ![ désactiver ](../../media/scc-toggle-off.png) ).

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres des documents approuvés après la sélection des paramètres globaux dans la page pièces jointes fiables.](../../media/safe-docs.png)

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell pour configurer des documents approuvés

Utilisez la syntaxe suivante :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
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

- Dans le centre de sécurité & conformité, accédez à la stratégie de **gestion des menaces** \> **Policy** \> **pièces jointes** de niveau de sécurité ATP, cliquez sur **paramètres globaux** , puis vérifiez que l’autorisation documents **sûrs pour les clients Office** et **autoriser les utilisateurs à cliquer via le mode protégé même si les documents approuvés identifie le fichier comme des paramètres malveillants** .

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs des propriétés :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Les fichiers suivants sont disponibles pour tester la protection des documents approuvés. Ces documents sont similaires au fichier EICAR.TXT pour le test de solutions anti-programme malveillant et anti-virus. Les fichiers ne sont pas nocifs, mais ils déclenchent la protection des documents approuvés.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
