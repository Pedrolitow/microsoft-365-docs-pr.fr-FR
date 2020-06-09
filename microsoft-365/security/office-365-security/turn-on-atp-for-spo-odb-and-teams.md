---
title: Activer l’ATP Office 365-SharePoint, OneDrive & teams
f1.keywords:
- NOCSH
ms.author: tracyp
author: msfttracyp
manager: dansimp
audience: ITPro
ms.topic: article
ms.date: 02/06/2019
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 07e76024-0c80-40dc-8c48-1dd0d0f863cb
ms.collection:
- M365-security-compliance
- SPO_Content
description: Découvrez comment activer la protection avancée contre les menaces pour SharePoint, OneDrive et Teams, y compris comment définir des alertes pour les fichiers détectés.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 1276faf9883fda9bb73674b27f3e5fb1a648d5d3
ms.sourcegitcommit: 73b2426001dc5a3f4b857366ef51e877db549098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/09/2020
ms.locfileid: "44613395"
---
# <a name="turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Activer PACM pour SharePoint, OneDrive et Microsoft Teams.

> [!IMPORTANT]
> Cet article est destiné aux entreprises qui ont [Office 365 – Protection avancée contre les menaces](office-365-atp.md). Si vous êtes un utilisateur à domicile et que vous recherchez des informations sur les liens fiables dans Outlook, consultez la rubrique [Advanced Outlook.com Security](https://support.microsoft.com/office/882d2243-eab9-4545-a58a-b36fee4a46e2).

[Office 365 ATP pour SharePoint, OneDrive et Microsoft teams](atp-for-spo-odb-and-teams.md) protège votre organisation contre le partage accidentel de fichiers malveillants. Lorsqu’un fichier malveillant est détecté, ce fichier est bloqué afin que personne ne puisse l’ouvrir, le copier, le déplacer ou le partager tant que d’autres actions ne sont pas effectuées par l’équipe de sécurité de l’organisation. Lisez cet article pour activer la protection avancée contre les menaces pour SharePoint, OneDrive et Teams, configurer des alertes pour être averti des fichiers détectés et suivre les étapes suivantes.

Pour définir (ou modifier) des stratégies ATP, vous devez disposer d’un rôle approprié. Certains exemples sont décrits dans le tableau suivant :

|Role|WHERE/How Assigned|
|---------|---------|
|administrateur général|La personne qui s’inscrit pour acheter Microsoft 365 est un administrateur global par défaut. (Pour en savoir plus, consultez la rubrique [à propos des rôles d’administrateur Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/add-users/about-admin-roles) .)|
|Administrateur de sécurité|Centre d’administration Azure Active Directory ( [https://aad.portal.azure.com](https://aad.portal.azure.com) )|
|Gestion d’Organisation Exchange Online|Centre d’administration Exchange ( [https://outlook.office365.com/ecp](https://outlook.office365.com/ecp) ) <br>ou <br>  Applets de commande PowerShell (consultez la rubrique [Exchange Online PowerShell](https://docs.microsoft.com/powershell/exchange/exchange-online-powershell))|

## <a name="turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams"></a>Activer PACM pour SharePoint, OneDrive et Microsoft Teams.

**Avant de commencer cette procédure, assurez-vous que la journalisation d’audit est déjà activée pour votre environnement Microsoft 365**. Cette opération est généralement réalisée par une personne disposant du rôle journaux d’audit dans Exchange Online. Pour plus d’informations, voir [Activer ou désactiver la recherche dans le journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

1. Accédez à [https://protection.office.com](https://protection.office.com) , puis connectez-vous à l’aide de votre compte professionnel ou scolaire.

2. Dans le centre de sécurité & Security Center, dans le volet de navigation de gauche, sous **gestion des menaces**, sélectionnez **stratégie** de \> **pièces jointes approuvées**par la stratégie.

   ![Dans le centre de sécurité & conformité, sélectionnez stratégie de gestion des menaces. \>](../../media/08849c91-f043-4cd1-a55e-d440c86442f2.png)

3. Sélectionnez Activer la protection avancée contre **les menaces pour SharePoint, OneDrive et Microsoft teams**.

   ![Activer la protection avancée contre les menaces pour SharePoint Online, OneDrive entreprise et Microsoft teams](../../media/48cfaace-59cc-4e60-bf86-05ff6b99bdbf.png)

4. Cliquez sur **Enregistrer**.

5. Vérifiez (et, le cas échéant, modifiez) les stratégies de [pièces jointes](set-up-atp-safe-attachments-policies.md) approuvées et les [stratégies de liens fiables](set-up-atp-safe-links-policies.md)de votre organisation.

6. Recommandation En tant qu’administrateur général ou administrateur SharePoint Online, exécutez la cmdlet **[Set-SPOTenant](https://docs.microsoft.com/powershell/module/sharepoint-online/Set-SPOTenant)** avec le paramètre _DisallowInfectedFileDownload_ défini sur *true*.

   - La définition du paramètre sur *true* bloque toutes les actions (à l’exception de la suppression) des fichiers détectés. Les utilisateurs ne peuvent pas ouvrir, déplacer, copier ou partager des fichiers détectés.

   - La définition du paramètre sur *false* bloque toutes les actions à l’exception de Delete et download. Les utilisateurs peuvent choisir d’accepter le risque et de télécharger un fichier détecté.

7. Autorisez jusqu’à 30 minutes pour que vos modifications soient diffusées sur tous les centres de calcul Microsoft 365.

8. Recommandation Passez à la configuration des alertes pour les fichiers détectés.

Pour en savoir plus sur l’utilisation de PowerShell avec Microsoft 365, consultez la rubrique [Manage Microsoft 365 with PowerShell](https://docs.microsoft.com/office365/enterprise/powershell/manage-office-365-with-office-365-powershell).

Pour en savoir plus sur l’expérience utilisateur lorsqu’un fichier a été détecté comme malveillant, consultez la rubrique [que faire lorsqu’un fichier malveillant est trouvé dans SharePoint Online, OneDrive ou Microsoft teams](https://support.microsoft.com/en-us/office/what-to-do-when-a-malicious-file-is-found-in-sharepoint-online-onedrive-or-microsoft-teams-01e902ad-a903-4e0f-b093-1e1ac0c37ad2).

## <a name="set-up-alerts-for-detected-files"></a>Configurer des alertes pour les fichiers détectés

Pour recevoir une notification lorsqu’un fichier dans SharePoint Online, OneDrive entreprise ou Microsoft teams a été identifié comme malveillant, vous pouvez configurer une alerte.

1. Dans le [Centre de sécurité & conformité](https://protection.office.com), sélectionnez **alertes** \> **gérer les alertes**.

2. Choisissez **nouvelle stratégie d’alerte**.

3. Spécifiez un nom pour l’alerte. Par exemple, vous pouvez taper des fichiers malveillants dans les bibliothèques.

4. Tapez une description pour l’alerte. Par exemple, vous pouvez taper avertir les administrateurs lorsque des fichiers malveillants sont détectés dans SharePoint Online, OneDrive ou Microsoft Teams.

5. Dans la section **Envoyer cette alerte quand...** , procédez comme suit :

   a. Dans la liste **activités** , sélectionnez **programmes malveillants détectés dans le fichier**.

   b. Laissez le champ **utilisateurs** vide.

6. Dans la section **Envoyer cette alerte à...** , sélectionnez un ou plusieurs administrateurs globaux, administrateurs de sécurité ou lecteurs de sécurité qui doivent recevoir une notification lorsqu’un fichier malveillant est détecté.

7. Cliquez sur **Enregistrer**.

Pour en savoir plus sur les alertes, voir [créer des alertes d’activité dans le centre de sécurité & conformité](../../compliance/create-activity-alerts.md).

## <a name="next-steps"></a>Étapes suivantes

1. [Afficher des informations sur les fichiers malveillants détectés dans SharePoint, OneDrive ou Microsoft teams](malicious-files-detected-in-spo-odb-or-teams.md)

2. [Gérer les messages et les fichiers mis en quarantaine en tant qu’administrateur dans Microsoft 365](manage-quarantined-messages-and-files.md)
