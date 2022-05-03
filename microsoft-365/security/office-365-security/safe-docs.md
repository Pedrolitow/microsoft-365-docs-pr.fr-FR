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
description: Découvrez Coffre documents dans Microsoft 365 E5/A5 ou Microsoft 365 E5/A5 Security.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 3fa1c7e07c1e1cd117ee20f4712dbbadad3c2b5c
ms.sourcegitcommit: f30616b90b382409f53a056b7a6c8be078e6866f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2022
ms.locfileid: "65174138"
---
# <a name="safe-documents-in-microsoft-365-e5a5"></a>documents Coffre dans Microsoft 365 E5/A5

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Coffre Documents est une fonctionnalité premium qui utilise le backend cloud de [Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) pour analyser les documents ouverts Office en [mode protégé](https://support.microsoft.com/office/d6f09ac7-e6b9-4495-8e43-2bbcdbcb6653) ou [Application Guard pour Office](https://support.microsoft.com/topic/9e0fb9c2-ffad-43bf-8ba3-78f785fdba46).

Les utilisateurs n’ont pas besoin que Defender pour point de terminaison soit installé sur leurs appareils locaux pour obtenir Coffre protection des documents. Les utilisateurs obtiennent Coffre protection des documents si toutes les exigences suivantes sont remplies :

- Coffre Documents est activé dans l’organisation, comme décrit dans cet article.
- Les licences d’un plan de licences requis sont attribuées aux utilisateurs. Coffre Documents est contrôlé par le plan de service **Office 365 SafeDocs** (ou **SAFEDOCS** ou **bf6f5520-59e3-4f82-974b-7dbbc4fd27c7**) (également appelé service). Ce plan de service est disponible dans les plans de licence suivants (également appelés plans de licence, plans Microsoft 365 ou produits) :
  - Microsoft 365 A5 pour les enseignants
  - Microsoft 365 A5 pour les étudiants
  - Microsoft 365 E5 Sécurité

  Coffre Documents n’est pas inclus dans Microsoft Defender pour Office 365 plans de licence.

  Pour plus d’informations, consultez [Les noms de produits et les identificateurs de plan de service pour les licences](/azure/active-directory/enterprise-users/licensing-service-plan-reference).

- Ils utilisent Applications Microsoft 365 pour les grandes entreprises (anciennement Office 365 ProPlus) version 2004 ou ultérieure.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Vous ouvrez le Portail Microsoft 365 Defender sur <https://security.microsoft.com>. Pour accéder directement à la page **Coffre Pièces jointes**, utilisez <https://security.microsoft.com/safeattachmentv2>.

- Pour vous connecter à Exchange Online PowerShell, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

- Vous avez besoin d’autorisations dans **Exchange Online** avant de pouvoir effectuer les procédures décrites dans cet article :
  - Pour configurer Coffre paramètres documents, vous devez être membre des groupes de **rôles Gestion de l’organisation** ou **Administrateur de la sécurité**.
  - Pour accéder en lecture seule aux paramètres Coffre Documents, vous devez être membre des groupes de **rôles Lecteur général** ou **Lecteur de sécurité**.

  Pour plus d'informations, voir [Permissions en échange en ligne](/exchange/permissions-exo/permissions-exo).

  > [!NOTE]
  >
  > - L’ajout d’utilisateurs au rôle Azure Active Directory correspondant dans le Centre d’administration Microsoft 365 donne aux utilisateurs les autorisations requises _et_ les autorisations pour les autres fonctionnalités de [Microsoft 365](../../admin/add-users/about-admin-roles.md).
  >
  > - Le groupe de rôles **Gestion de l’organisation en affichage seul** dans [Exchange Online](/Exchange/permissions-exo/permissions-exo#role-groups) permet également d’accéder en lecture seule à la fonctionnalité.

### <a name="how-does-microsoft-handle-your-data"></a>Comment Microsoft gère-t-il vos données ?

Pour vous protéger, Coffre Documents envoie des fichiers au [cloud Microsoft Defender pour point de terminaison](/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection) à des fins d’analyse. Vous trouverez des détails sur la façon dont Microsoft Defender pour point de terminaison gère vos données ici : [Microsoft Defender pour point de terminaison le stockage et la confidentialité des données](/windows/security/threat-protection/microsoft-defender-atp/data-storage-privacy).

Les fichiers envoyés par Coffre Documents ne sont pas conservés dans Defender pour point de terminaison au-delà du temps nécessaire à l’analyse (généralement, moins de 24 heures).

## <a name="use-the-microsoft-365-defender-portal-to-configure-safe-documents"></a>Utiliser le portail Microsoft 365 Defender pour configurer Coffre Documents

1. Dans le portail <https://security.microsoft.com>Microsoft 365 Defender, accédez à **Email & Collaboration** \> **Policies & Rules** \> **Threat policies** \> **Coffre Attachments** dans la section **Stratégies**. Pour accéder directement à la page **Coffre Pièces jointes**, utilisez <https://security.microsoft.com/safeattachmentv2>.

2. Dans la page **Coffre Pièces jointes**, cliquez sur **Paramètres globaux**.

3. Dans les **paramètres globaux** qui s’affichent, configurez les paramètres suivants :
   - **Activez Coffre Documents pour les clients Office** : déplacez le bouton bascule vers la droite pour activer la fonctionnalité : ![Activer/désactiver.](../../media/scc-toggle-on.png)
   - **Autoriser les utilisateurs à cliquer via la vue protégée même si Coffre documents ont identifié le fichier comme malveillant** : nous vous recommandons de laisser cette option désactivée (laissez le bouton bascule à gauche : ![Désactiver la touche Bascule).](../../media/scc-toggle-off.png)

   Lorsque vous avez terminé, cliquez sur **Enregistrer**.

   :::image type="content" source="../../media/safe-docs-global-settings.png" alt-text="Paramètres Coffre Documents après avoir sélectionné les paramètres globaux dans la page Coffre Pièces jointes" lightbox="../../media/safe-docs-global-settings.png":::

### <a name="use-exchange-online-powershell-to-configure-safe-documents"></a>Utiliser Exchange Online PowerShell pour configurer des documents Coffre

Si vous préférez utiliser PowerShell pour configurer Coffre Documents, utilisez la syntaxe suivante dans Exchange Online PowerShell :

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs <$true | $false> -AllowSafeDocsOpen <$true | $false>
```

- Le paramètre _EnableSafeDocs_ active ou désactive Coffre Documents pour l’ensemble de l’organisation.
- Le paramètre _AllowSafeDocsOpen_ autorise ou empêche les utilisateurs de quitter la vue protégée (autrement dit, l’ouverture du document) si le document a été identifié comme malveillant.

Cet exemple active Coffre Documents pour l’ensemble de l’organisation et empêche les utilisateurs d’ouvrir des documents identifiés comme malveillants à partir de la vue protégée.

```powershell
Set-AtpPolicyForO365 -EnableSafeDocs $true -AllowSafeDocsOpen $false
```

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, consultez [Set-AtpPolicyForO365](/powershell/module/exchange/set-atppolicyforo365).

### <a name="configure-individual-access-to-safe-documents"></a>Configurer l’accès individuel aux documents Coffre

Si vous souhaitez autoriser ou bloquer de manière sélective l’accès à la fonctionnalité Coffre Documents, procédez comme suit :

1. Activez Coffre Documents dans le portail Microsoft 365 Defender ou Exchange Online PowerShell, comme décrit précédemment dans cet article.
2. Utilisez Azure AD PowerShell pour désactiver Coffre Documents pour des utilisateurs spécifiques, comme décrit dans [Désactiver des services Microsoft 365 spécifiques pour des utilisateurs spécifiques pour un plan de licence spécifique](/microsoft-365/enterprise/disable-access-to-services-with-microsoft-365-powershell#disable-specific-microsoft-365-services-for-specific-users-for-a-specific-licensing-plan).

  Le nom du plan de service à désactiver dans PowerShell est **SAFEDOCS**.

Pour plus d’informations, voir les rubriques suivantes :

- [Afficher Microsoft 365 licences et services avec PowerShell](/microsoft-365/enterprise/view-licenses-and-services-with-microsoft-365-powershell)
- [Afficher Microsoft 365 licence de compte et les détails du service avec PowerShell](/microsoft-365/enterprise/view-account-license-and-service-details-with-microsoft-365-powershell)
- [Noms de produits et identificateurs de plans de service pour la gestion des licences](/azure/active-directory/enterprise-users/licensing-service-plan-reference)

### <a name="onboard-to-the-microsoft-defender-for-endpoint-service-to-enable-auditing-capabilities"></a>Intégration au service Microsoft Defender pour point de terminaison pour activer les fonctionnalités d’audit

Pour activer les fonctionnalités d’audit, l’appareil local doit avoir Microsoft Defender pour point de terminaison installé. Pour déployer Microsoft Defender pour point de terminaison, vous devez passer par les différentes phases de déploiement. Après l’intégration, vous pouvez configurer les fonctionnalités d’audit dans le portail Microsoft 365 Defender.

Pour plus d’informations, consultez [Intégrer au service Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/onboarding). Si vous avez besoin d’aide supplémentaire, [reportez-vous à La résolution des problèmes d’intégration Microsoft Defender pour point de terminaison](/microsoft-365/security/defender-endpoint/troubleshoot-onboarding).

### <a name="how-do-i-know-this-worked"></a>Comment savoir si cela a fonctionné ?

Pour vérifier que vous avez activé et configuré Coffre Documents, effectuez l’une des étapes suivantes :

- Dans le portail Microsoft 365 Defender, accédez aux stratégies de **& de collaboration** \> par e-mail **& les stratégies** de **menace** \> des règles \> **Coffre les pièces jointes** dans la section **Paramètres globaux** de la section \> **Stratégies**, puis vérifiez **l’activation des documents Coffre pour les clients Office** et **Autoriser les utilisateurs à cliquer via la vue protégée même si Coffre Documents identifie le fichier comme paramètres malveillants**.

- Exécutez la commande suivante dans Exchange Online PowerShell et vérifiez les valeurs de propriété :

  ```powershell
  Get-AtpPolicyForO365 | Format-List *SafeDocs*
  ```

- Les fichiers suivants sont disponibles pour tester Coffre protection des documents. Ces fichiers sont similaires au fichier EICAR.TXT pour tester les solutions antivirus et anti-programme malveillant. Les fichiers ne sont pas dangereux, mais ils déclenchent Coffre protection des documents.

  - [SafeDocsDemo.docx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.docx)
  - [SafeDocsDemo.pptx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.pptx)
  - [SafeDocsDemo.xlsx](https://github.com/MicrosoftDocs/microsoft-365-docs/raw/public/microsoft-365/downloads/SafeDocsDemo.xlsx)
