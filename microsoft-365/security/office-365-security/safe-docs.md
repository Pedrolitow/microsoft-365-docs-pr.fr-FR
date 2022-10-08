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
- m365-security
description: Découvrez les documents sécurisés dans Microsoft 365 A5 ou la sécurité E5.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 05f337652b0cd08ac930b1439b3f2415bb697e1e
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68060425"
---
# <a name="safe-documents-in-microsoft-365-a5-or-e5-security"></a>Documents sécurisés dans Microsoft 365 A5 ou sécurité E5

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Documents sécurisés est une fonctionnalité premium qui utilise le backend cloud de [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser les documents Office ouverts en [mode protégé](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) ou [Protection d'application pour Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

Les utilisateurs n’ont pas besoin que Defender pour point de terminaison soit installé sur leurs appareils locaux pour bénéficier de la protection des documents sécurisés. Les utilisateurs bénéficient d’une protection des documents sécurisés si toutes les exigences suivantes sont remplies :

- Les documents sécurisés sont activés dans l’organisation, comme décrit dans cet article.
- Les licences d’un plan de licences requis sont attribuées aux utilisateurs. Les documents sécurisés sont contrôlés par le plan de service **Office 365 SafeDocs** (ou **SAFEDOCS** ou **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (également appelé service). Ce plan de service est disponible dans les plans de licence suivants (également appelés plans de licence, plans Microsoft 365 ou produits) :
  - Microsoft 365 A5 pour les enseignants
  - Microsoft 365 A5 pour les étudiants
  - Microsoft 365 E5 Sécurité

  Les documents approuvés ne sont pas inclus dans Microsoft Defender pour Office 365 plans de licence.

  Pour plus d’informations, consultez [Les noms de produits et les identificateurs de plan de service pour les licences](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- Ils utilisent Applications Microsoft 365 pour les grandes entreprises (anciennement Office 365 ProPlus) version 2004 ou ultérieure.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Pièces jointes sécurisées** , utilisez <https://security.microsoft.com/safeattachmentv2>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous avez besoin d’autorisations dans **Exchange Online** avant de pouvoir effectuer les procédures décrites dans cet article :
  - Pour configurer les paramètres documents sécurisés, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité** .
  - Pour accéder en lecture seule aux paramètres Documents sécurisés, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité** .

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - Adding users to the corresponding Azure Active Directory role in the Microsoft 365 admin center gives users the required permissions _and_ permissions for other features in Microsoft 365. For more information, see [About admin roles](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

### <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour vous protéger, les documents sécurisés envoient des fichiers au [cloud Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) à des fins d’analyse. Vous trouverez des détails sur la façon dont Microsoft Defender pour point de terminaison gère vos données ici : [Microsoft Defender pour point de terminaison le stockage et la confidentialité des données](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Les fichiers envoyés par les documents sécurisés ne sont pas conservés dans Defender pour point de terminaison au-delà du temps nécessaire à l’analyse (généralement, moins de 24 heures).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Utiliser le portail Microsoft 365 Defender pour configurer des documents sécurisés

1. Dans le portail Microsoft 365 Defender, accédez à <https://security.microsoft.com>Email & Stratégies de **collaboration** \> **& les** **pièces jointes sécurisées des** stratégies de **menace** \> des règles \> dans la section **Stratégies**. Pour accéder directement à la page **Pièces jointes sécurisées** , utilisez <https://security.microsoft.com/safeattachmentv2>.

2. Dans la page **Pièces jointes sécurisées** , cliquez sur **Paramètres globaux**.

3. Dans les **paramètres globaux** qui s’affichent, configurez les paramètres suivants :
   - **Activer les documents sécurisés pour les clients Office** : déplacez le bouton bascule vers la droite pour activer la fonctionnalité : ![Activer/désactiver.](../../media/scc-toggle-on.png)
   - **Autoriser les utilisateurs à cliquer sur La vue protégée même si les documents sécurisés ont identifié le fichier comme malveillant** : nous vous recommandons de laisser cette option désactivée (laissez le bouton bascule à gauche : ![Désactiver).](../../media/scc-toggle-off.png))

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Paramètres documents sécurisés après avoir sélectionné les paramètres globaux dans la page Pièces jointes sécurisées" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell pour configurer des documents sécurisés

Si vous préférez utiliser PowerShell pour configurer des documents sécurisés, utilisez la syntaxe suivante dans Exchange Online PowerShell :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Le paramètre _EnableSafeDocs_ active ou désactive les documents sécurisés pour l’ensemble de l’organisation.
- Le paramètre _AllowSafeDocsOpen_ autorise ou empêche les utilisateurs de quitter la vue protégée (autrement dit, l’ouverture du document) si le document a été identifié comme malveillant.

Cet exemple active les documents sécurisés pour l’ensemble de l’organisation et empêche les utilisateurs d’ouvrir des documents identifiés comme malveillants à partir de la vue protégée.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Configurer l’accès individuel aux documents sécurisés

Si vous souhaitez autoriser ou bloquer de manière sélective l’accès à la fonctionnalité Documents sécurisés, procédez comme suit :

1. Activez documents sécurisés dans le portail Microsoft 365 Defender ou Exchange Online PowerShell comme décrit précédemment dans cet article.
2. Utilisez Azure AD PowerShell pour désactiver les documents sécurisés pour des utilisateurs spécifiques, comme décrit dans [Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de licence spécifique](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  Le nom du plan de service à désactiver dans PowerShell est **SAFEDOCS**.

Pour plus d’informations, voir les rubriques suivantes :

- [Afficher les licences et services Microsoft 365 avec PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Afficher les détails du service et de la licence de compte Microsoft 365 avec PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Noms de produits et identificateurs de plans de service pour la gestion des licences](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Intégration au service Microsoft Defender pour point de terminaison pour activer les fonctionnalités d’audit

Pour activer les fonctionnalités d’audit, l’appareil local doit avoir Microsoft Defender pour point de terminaison installé. Pour déployer Microsoft Defender pour point de terminaison, vous devez passer par les différentes phases de déploiement. Après l’intégration, vous pouvez configurer les fonctionnalités d’audit dans le portail Microsoft 365 Defender.

Pour plus d’informations, consultez [Intégrer au service Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboarding). Si vous avez besoin d’aide supplémentaire, [reportez-vous à La résolution des problèmes d’intégration Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez activé et configuré des documents sécurisés, effectuez l’une des étapes suivantes :

- Dans le  portail Microsoft 365 Defender, accédez à Email & Stratégies de **collaboration** \> **& règles** \> \> - **Pièces jointes sécurisées** dans les **paramètres globaux** de la section  \> Stratégies, puis vérifiez l’activation des **documents sécurisés pour les clients Office** et **Autoriser les utilisateurs à cliquer via la vue protégée même si les documents sécurisés identifient le fichier comme** des paramètres malveillants.

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs de propriété :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Les fichiers suivants sont disponibles pour tester la protection des documents sécurisés. Ces fichiers sont similaires au fichier EICAR.TXT pour tester les solutions antivirus et anti-programme malveillant. Les fichiers ne sont pas dangereux, mais ils déclenchent la protection des documents sécurisés.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
