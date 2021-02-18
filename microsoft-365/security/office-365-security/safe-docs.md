---
title: Documents sécurisés dans Microsoft Defender pour Office 365
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Découvrez la sécurité des documents sécurisés dans Microsoft 365 E5 ou Microsoft 365 E5 Security.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a3f4ed3535c7e53774b9b567b50f7c06e99cef9d
ms.sourcegitcommit: 786f90a163d34c02b8451d09aa1efb1e1d5f543c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/18/2021
ms.locfileid: "50288584"
---
# <a name="safe-documents-in-microsoft-365-e5"></a>Documents sécurisés dans Microsoft 365 E5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](office-365-atp.md)
- [Microsoft 365 Defender](../mtp/microsoft-threat-protection.md)

La fonctionnalité Documents sécurisés de Microsoft 365 E5 ou Sécurité Microsoft 365 E5 utilise [Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour le point de terminaison pour analyser les documents et les fichiers ouverts en affichage [protégé.](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653)

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Les documents sécurisés sont disponibles uniquement pour les utilisateurs titulaires de licences De sécurité *Microsoft 365 E5* ou *Microsoft 365 E5.* Ces licences ne sont pas incluses dans les plans Microsoft Defender pour Office 365.

- La sécurité des documents est prise en charge dans Microsoft 365 Apps for enterprise (anciennement Office 365 ProPlus) version 2004 ou ultérieure.

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com>. Pour aller directement à la page Pièces **jointes sécurisées ATP,** ouvrez <https://protection.office.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans le Centre de sécurité et de conformité pour que vous puissiez effectuer les procédures décrites dans cet article.
  - Pour configurer les paramètres des documents sécurisés,  vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur de** la sécurité.
  - Pour accéder en lecture seule aux paramètres des documents  sécurisés, vous devez être membre des groupes de rôles Lecteur global ou Lecteur **de** sécurité.

  Pour en savoir plus, consultez [Autorisations dans le Centre de sécurité et de conformité](permissions-in-the-security-and-compliance-center.md).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises dans le centre de sécurité et de conformité _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](https://docs.microsoft.com/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

### <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour vous protéger, les documents sécurisés envoient des fichiers au cloud [Microsoft Defender for Endpoint](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyse. Pour plus d’informations sur la façon dont Microsoft Defender pour le point de terminaison gère vos données, voir : Microsoft Defender pour le stockage et la confidentialité des données de [point de terminaison.](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)

Les fichiers envoyés par des documents sécurisés ne sont pas conservés dans Defender au-delà du temps nécessaire à l’analyse (généralement, moins de 24 heures).

## <a name="use-the-security--compliance-center-to-configure-safe-documents"></a>Utiliser le Centre de sécurité & conformité pour configurer des documents sécurisés

1. Dans le Centre de sécurité &  conformité, allez dans Stratégie de gestion des menaces - Pièces jointes sécurisées , puis cliquez sur \>  \>  **Paramètres globaux.**

2. Dans le **volant des paramètres globaux** qui s’affiche, configurez les paramètres suivants :

   - **Activer les documents sécurisés pour les clients Office**: déplacez le basculement vers la droite pour activer la fonctionnalité : ![ Activer/ ](../../media/scc-toggle-on.png) Activer.

   - Autoriser les utilisateurs à cliquer dans le affichage protégé même si les **documents sécurisés identifient** le fichier comme malveillant : nous vous recommandons de laisser cette option désactivée (laissez le bouton bascule vers la gauche : ![ basculez vers la ](../../media/scc-toggle-off.png) gauche).

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres de documents sécurisés après la sélection des paramètres globaux dans la page Pièces jointes sécurisées.](../../media/safe-docs.png)

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell pour configurer des documents sécurisés

Utilisez la syntaxe suivante :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Le _paramètre EnableSafeDocs_ active ou désactive les documents sécurisés pour l’ensemble de l’organisation.
- Le _paramètre AllowSafeDocsOpen_ permet ou empêche les utilisateurs de quitter le affichage protégé (c’est-à-dire, l’ouverture du document) si le document a été identifié comme malveillant.

Cet exemple active les documents sécurisés pour l’ensemble de l’organisation et empêche les utilisateurs d’ouvrir des documents qui ont été identifiés comme malveillants en affichage protégé.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AtpPolicyForO365](https://docs.microsoft.com/powershell/module/exchange/set-atppolicyforo365).

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez activé et configuré les documents sécurisés, faites l’une des étapes suivantes :

- Dans le Centre de sécurité &  conformité, consultez La stratégie de gestion des menaces pièces \>  \> **jointes sécurisées ATP,**  cliquez sur **Paramètres** globaux et vérifiez l’activer pour les clients Office et autoriser les utilisateurs à cliquer dans le affichage protégé, même si les **documents sécurisés identifient** le fichier comme des paramètres malveillants.

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs des propriétés :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Les fichiers suivants sont disponibles pour tester la protection des documents sécurisés. Ces documents sont similaires au fichier EICAR.TXT pour tester les solutions antivirus et anti-programme malveillant. Les fichiers ne sont pas dangereux, mais ils déclenchent la protection des documents sécurisés.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
