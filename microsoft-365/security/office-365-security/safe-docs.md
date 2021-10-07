---
title: Documents sécurisés dans Microsoft Defender pour Office 365
ms.author: chrisda
author: chrisda
manager: dansimp
ms.reviewer: kshi
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
description: Découvrez comment Coffre documents dans Microsoft 365 E5 ou Microsoft 365 E5 Sécurité.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: cd1bb71bee6a123ae698f1178e62a521409d4103
ms.sourcegitcommit: d4b867e37bf741528ded7fb289e4f6847228d2c5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/06/2021
ms.locfileid: "60180705"
---
# <a name="safe-documents-in-microsoft-365-e5"></a>Documents sécurisés dans Microsoft 365 E5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Coffre Les documents sont une fonctionnalité premium qui utilise le système principal cloud de [](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser les documents Office ouverts en affichage protégé ou Application Guard [pour Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

Les utilisateurs n’ont pas besoin que Defender for Endpoint soit installé sur leurs appareils locaux pour obtenir la protection Coffre Documents. Les utilisateurs Coffre protection des documents si toutes les conditions suivantes sont remplies :

- Coffre Les documents sont activés dans l’organisation comme décrit dans cet article.
- Les licences d’un plan de gestion des licences requis sont attribuées aux utilisateurs. Coffre Les documents sont contrôlés par le plan de service **Office 365 SafeDocs** (ou **SAFEDOCS** ou **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (également appelé service). Ce plan de service est disponible dans les plans de gestion des licences suivants (également appelés plans de licence, plans Microsoft 365 ou produits) :
  - Microsoft 365 A5 pour les enseignants
  - Microsoft 365 A5 pour les étudiants
  - Microsoft 365 E5
  - Microsoft 365 E5 Sécurité

  Coffre Les documents ne sont pas inclus dans les plans de gestion des Office 365 Microsoft Defender.

  Pour plus d’informations, voir Noms de produits [et identificateurs de plan de service pour la gestion des licences.](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

- Ils utilisent Applications Microsoft 365 pour les grandes entreprises (anciennement Office 365 ProPlus) version 2004 ou ultérieure.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour aller directement à la page **Coffre pièces jointes,** utilisez <https://security.microsoft.com/safeattachmentv2> .

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous avez besoin d’autorisations **Exchange Online** pour pouvoir suivre les procédures de cet article :
  - Pour configurer les Coffre Documents, vous devez être membre  des groupes de rôles Gestion de l’organisation ou **Administrateur** de la sécurité.
  - Pour accéder en lecture seule aux paramètres Coffre Documents, vous  devez être membre des groupes de rôles Lecteur global ou Lecteur **de** sécurité.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de Microsoft 365. Pour plus d’informations, consultez [À propos des rôles d’administrateur](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

### <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour vous protéger, Coffre Documents envoie des fichiers au cloud [Microsoft Defender for Endpoint](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyse. Pour plus d’informations sur la façon dont Microsoft Defender pour le point de terminaison gère vos données, voir : Microsoft Defender pour le stockage et la confidentialité des données de [point de terminaison.](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy)

Les fichiers envoyés par Coffre Documents ne sont pas conservés dans Defender au-delà du temps nécessaire à l’analyse (généralement, moins de 24 heures).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Utiliser le portail Microsoft 365 Defender pour configurer les documents Coffre documents

1. Ouvrez le portail Microsoft 365 Defender de messagerie et & stratégies de **collaboration** & règles de menace Coffre pièces jointes dans la \>  \>  \> section **Stratégies.** 

2. Dans la page **Coffre pièces jointes,** cliquez **sur Paramètres globaux.**

3. Dans le **volant des paramètres globaux** qui s’affiche, configurez les paramètres suivants :
   - **Activer Coffre documents** pour Office clients : déplacez le basculement vers la droite pour activer la fonctionnalité : ![ Activer/ Activer. ](../../media/scc-toggle-on.png)
   - Autoriser les utilisateurs à cliquer dans le affichage protégé même si **Coffre Documents a** identifié le fichier comme malveillant : nous vous recommandons de laisser cette option désactivée (laissez le bouton bascule vers la gauche : ![ Basculez. ](../../media/scc-toggle-off.png) ).

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   ![Coffre Documents settings after selecting Global settings on the Coffre Attachments page.](../../media/safe-docs-global-settings.png)

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell pour configurer Coffre Documents

Si vous préférez utiliser PowerShell pour configurer Coffre Documents, utilisez la syntaxe suivante dans Exchange Online PowerShell :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Le _paramètre EnableSafeDocs_ active ou désactive Coffre documents pour l’ensemble de l’organisation.
- Le _paramètre AllowSafeDocsOpen_ permet ou empêche les utilisateurs de quitter le affichage protégé (c’est-à-dire, l’ouverture du document) si le document a été identifié comme malveillant.

Cet exemple active Coffre documents pour l’ensemble de l’organisation et empêche les utilisateurs d’ouvrir des documents qui ont été identifiés comme malveillants en affichage protégé.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Configurer l’accès individuel aux Coffre documents

Si vous souhaitez autoriser ou bloquer l’accès à la fonctionnalité Documents Coffre de manière sélective, suivez les étapes suivantes :

1. Activer Coffre documents dans le portail Microsoft 365 Defender ou Exchange Online PowerShell, comme décrit précédemment dans cet article.
2. Utilisez Azure AD PowerShell pour désactiver les documents Coffre pour des utilisateurs spécifiques, comme décrit dans Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de gestion [des licences spécifique.](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan)

  Le nom du plan de service à désactiver dans PowerShell est **SAFEDOCS**.

Pour plus d’informations, voir les rubriques suivantes :

- [Afficher Microsoft 365 licences et services avec PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Afficher Microsoft 365 licence de compte et les détails du service avec PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Noms de produits et identificateurs de plans de service pour la gestion des licences](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Intégration au service Microsoft Defender for Endpoint pour activer les fonctionnalités d’audit

Pour activer les fonctionnalités d’audit, Microsoft Defender pour point de terminaison doit être installé sur l’appareil local. Pour déployer Microsoft Defender pour endpoint, vous devez passer par les différentes phases de déploiement. Après l’intégration, vous pouvez configurer les fonctionnalités d’audit dans Microsoft 365 Defender portail.

Pour plus d’informations, [voir Intégrer au service Microsoft Defender for Endpoint.](/microsoft-365/security/defender-endpoint/onboarding) Si vous avez besoin d’aide supplémentaire, reportez-vous à Résoudre les problèmes d’intégration de Microsoft Defender pour les points [de terminaison.](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding)

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez activé et configuré Coffre Documents, faites l’une des étapes suivantes :

- Dans le portail Microsoft 365 Defender, go to **Email & Collaboration** Policies & \> **Rules** Threat \> **policies** \> **Coffre Attachments** in the **Policies** section \> **Global settings**, and verify the **Turn on Coffre Documents for Office clients** and Allow people to **click through Affichage protégé même si Coffre Documents identifie le fichier comme paramètres** malveillants.

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs des propriétés :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Les fichiers suivants sont disponibles pour tester la protection Coffre documents. Ces fichiers sont similaires au fichier EICAR.TXT pour tester les solutions antivirus et anti-programme malveillant. Les fichiers ne sont pas dangereux, mais ils déclenchent la protection Coffre documents.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
