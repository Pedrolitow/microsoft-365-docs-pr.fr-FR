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
description: Découvrez les documents sécurisés dans Microsoft 365 E5 ou Microsoft 365 E5 Sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 1186c7856d0b979c483cf6dd1c0a010ab582e2ce
ms.sourcegitcommit: 437bdbf3f99610869811e80432a59b5f244f7a87
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/08/2021
ms.locfileid: "51644751"
---
# <a name="safe-documents-in-microsoft-365-e5"></a>Documents sécurisés dans Microsoft 365 E5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Les documents sécurisés sont une fonctionnalité de Microsoft 365 E5 ou de Microsoft 365 E5 Sécurité qui utilise Microsoft Defender [](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) [pour](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) le point de terminaison pour analyser les documents et les fichiers ouverts en affichage protégé ou Application Guard pour [Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Les documents sécurisés sont disponibles uniquement pour les utilisateurs *Microsoft 365 E5* ou *Microsoft 365 E5 Sécurité* licences. Ces licences ne sont pas incluses dans Microsoft Defender pour Office 365 plans.

- La sécurité des documents est prise en charge Applications Microsoft 365 pour les grandes entreprises (anciennement Office 365 ProPlus) version 2004 ou ultérieure.

- Vous ouvrez le Centre de conformité et sécurité sur <https://protection.office.com>. Pour aller directement à la page Pièces **jointes sécurisées ATP,** ouvrez <https://protection.office.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Des autorisations doivent vous avoir été attribuées dans **Exchange Online** pour que vous puissiez effectuer les procédures décrites dans cette rubrique.
  - Pour configurer les paramètres des documents sécurisés,  vous devez être membre des groupes de rôles Gestion de l’organisation ou **Administrateur de** la sécurité.
  - Pour accéder en lecture seule aux paramètres des documents  sécurisés,  vous devez être membre des groupes de rôles Lecteur global ou Lecteur de sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

### <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour vous protéger, les documents sécurisés envoient des fichiers au cloud [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyse. Pour plus d’informations sur la façon dont Microsoft Defender pour le point de terminaison gère vos données, voir : Microsoft Defender pour le stockage et la confidentialité des données de [point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)

Les fichiers envoyés par des documents sécurisés ne sont pas conservés dans Defender au-delà du temps nécessaire à l’analyse (généralement, moins de 24 heures).

## <a name="use-the-security--compliance-center-to-configure-safe-documents"></a>Utiliser le Centre de sécurité & conformité pour configurer des documents sécurisés

1. Dans le Centre de sécurité &  conformité, allez dans Stratégie de gestion des menaces - Pièces jointes sécurisées , puis cliquez sur \>  \>  **Paramètres globaux.**

2. Dans le **volant des paramètres globaux** qui s’affiche, configurez les paramètres suivants :

   - **Activer les documents sécurisés pour Office clients**: déplacez le basculement vers la droite pour activer la fonctionnalité : ![ Activer/ ](../../media/scc-toggle-on.png) Activer.

   - Autoriser les utilisateurs à cliquer dans le affichage protégé même si les **documents sécurisés identifient** le fichier comme malveillant : nous vous recommandons de laisser cette option désactivée (laissez le bouton bascule vers la gauche : ![ basculez vers la ](../../media/scc-toggle-off.png) gauche).

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Paramètres des documents sécurisés après la sélection des paramètres globaux dans la page Pièces jointes sécurisées.](../../media/safe-docs.png)

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell pour configurer des documents sécurisés

Utilisez la syntaxe suivante :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Le _paramètre EnableSafeDocs_ active ou désactive les documents sécurisés pour l’ensemble de l’organisation.
- Le _paramètre AllowSafeDocsOpen_ permet ou empêche les utilisateurs de quitter le affichage protégé (c’est-à-dire, l’ouverture du document) si le document a été identifié comme malveillant.

Cet exemple active les documents sécurisés pour l’ensemble de l’organisation et empêche les utilisateurs d’ouvrir des documents qui ont été identifiés comme malveillants en affichage protégé.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Intégration au service Microsoft Defender for Endpoint pour activer les fonctionnalités d’audit

Pour déployer Microsoft Defender pour le point de terminaison, vous devez passer par les différentes phases de déploiement. Après l’intégration, vous pouvez configurer les fonctionnalités d’audit dans le Centre de sécurité & conformité.

Pour plus d’informations, [voir Intégrer au service Microsoft Defender for Endpoint.](/microsoft-365/security/defender-endpoint/onboarding) Si vous avez besoin d’aide supplémentaire, reportez-vous à La résolution des problèmes d’intégration de Microsoft Defender pour les points [de terminaison.](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez activé et configuré les documents sécurisés, faites l’une des étapes suivantes :

- Dans le Centre de sécurité &  conformité, consultez La stratégie de gestion des menaces - Pièces jointes sécurisées , cliquez sur Paramètres globaux et vérifiez l’activer pour les clients Office et autoriser les utilisateurs à cliquer en affichage protégé, même si les documents sécurisés identifient le fichier comme des \>  \> paramètres malveillants.   

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs des propriétés :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Les fichiers suivants sont disponibles pour tester la protection des documents sécurisés. Ces documents sont similaires au fichier EICAR.TXT pour tester les solutions antivirus et anti-programme malveillant. Les fichiers ne sont pas dangereux, mais ils déclenchent la protection des documents sécurisés.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
