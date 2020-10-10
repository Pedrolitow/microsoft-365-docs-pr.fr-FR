---
title: Configurer les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection
description: Configurer une enquête et une réponse automatisées avec auto-réparation dans Microsoft Threat Protection
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365-initiative-m365-defender
ms.custom: autoir
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.openlocfilehash: 4b49436533855fc4c6a48a149fc23c433985bace
ms.sourcegitcommit: 5e1b8c959a081022826fb09358730096248507ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/09/2020
ms.locfileid: "48413829"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-threat-protection"></a>Configurer les fonctionnalités d’analyse et de réponse automatisées dans Microsoft Threat Protection

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


La protection de Microsoft contre les menaces comprend de puissantes fonctionnalités d’analyse [et de réponse automatisées](mtp-autoir.md) qui peuvent enregistrer les opérations de sécurité de votre équipe. Grâce à la réparation spontanée, ces fonctionnalités imitent les étapes qu’un analyste de la sécurité doit entreprendre pour examiner et répondre aux menaces, uniquement plus rapidement et avec plus de possibilités d’effectuer une montée en taille. Cet article explique comment configurer une enquête et une réponse automatisées dans Microsoft Threat Protection.

Pour configurer les fonctionnalités d’analyse et de réponse automatisées, procédez comme suit :

1. [Passez en revue les conditions préalables](#prerequisites-for-automated-investigation-and-response-in-microsoft-threat-protection).
2. [Vérifiez ou modifiez le niveau d’automatisation pour les groupes d’appareils](#review-or-change-the-automation-level-for-device-groups).
3. [Consultez vos stratégies de sécurité et d’alerte dans Office 365](#review-your-security-and-alert-policies-in-office-365).
4. Assurez-vous [que la protection contre les menaces Microsoft est activée](#make-sure-microsoft-threat-protection-is-turned-on).

Ensuite, une fois toutes les opérations configurées, [Vérifiez les actions en attente et terminées dans le centre de notifications](#review-pending-and-completed-actions-in-the-action-center). 


## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-threat-protection"></a>Conditions préalables à l’instruction et à la réponse automatisées dans Microsoft Threat Protection

|Conditions requises |Détails |
|--|--|
|Conditions d’abonnement |Un des abonnements : <br/>-Microsoft 365 E5 <br/>-Microsoft 365 a5 <br/>-Microsoft 365 E5 sécurité<br/>-Microsoft 365 a5 Security<br/>-Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5<br/><br/>Consultez la rubrique [licences de protection contre les menaces Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites?#licensing-requirements).|
|Configuration réseau requise |- [Azure ATP](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) activé<br/>- [Sécurité des applications Cloud Microsoft](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) configurée<br/>- [Sécurité des applications Cloud Microsoft intégrée à Azure ATP](https://docs.microsoft.com/cloud-app-security/aatp-integration) |
|Configuration requise pour ordinateur Windows |-Windows 10, version 1709 ou ultérieure installé (voir [informations sur la version Windows 10](https://docs.microsoft.com/windows/release-information/)) avec les services de protection contre les menaces suivants configurés :<br/>- [Microsoft Defender ATP](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints) <br/>- [Antivirus Microsoft Defender](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features) |
|Protection du contenu de messagerie et des fichiers Office |[Office 365 Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#configure-atp-policies) configurée |
|Autorisations |Pour configurer les fonctionnalités d’analyse et de réponse automatisées, vous devez disposer du rôle administrateur général ou administrateur de sécurité dans Azure Active Directory ( [https://portal.azure.com](https://portal.azure.com) ) ou dans le centre d’administration Microsoft 365 ( [https://admin.microsoft.com](https://admin.microsoft.com) ).<br/><br/>-Pour obtenir les autorisations nécessaires pour utiliser des fonctionnalités d’analyse et de réponse automatisées, telles que la révision, l’approbation ou le rejet des actions en attente, consultez la rubrique [Required Permissions for Action Center Tasks](mtp-action-center.md#required-permissions-for-action-center-tasks). |

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Vérifier ou modifier le niveau d’automatisation pour les groupes d’appareils

Si les analyses automatisées sont exécutées et si les actions de correction sont prises automatiquement ou uniquement à l’approbation de vos appareils, dépendent de certains paramètres, tels que les stratégies de groupe d’appareils de votre organisation. Examinez le niveau d’automatisation défini pour vos stratégies de groupes d’appareils.

1. Accédez au centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) et connectez-vous.

2. Accédez à **paramètres**  >  **autorisations**  >  **groupes de périphériques**. 

3. Passez en revue les stratégies de groupes d’appareils. Examinez en particulier la colonne **niveau de correction** . Nous vous recommandons d’utiliser **automatiquement les menaces de correction complète**.  Vous devrez peut-être créer ou modifier vos groupes d’appareils pour obtenir le niveau d’automatisation souhaité. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants :

   - [Comment les menaces sont corrigées](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   
   - [Créer et gérer des groupes d’appareils](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/machine-groups) 

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Consulter vos stratégies de sécurité et d’alerte dans Office 365

Microsoft fournit des stratégies d' [alerte](https://docs.microsoft.com/microsoft-365/compliance/alert-policies) intégrées qui permettent d’identifier certains risques. Ces risques incluent les autorisations d’administrateur Exchange en abus, l’activité de programmes malveillants, les menaces externes et internes potentielles, ainsi que les risques de gouvernance des informations. Certaines alertes peuvent déclencher une [enquête et une réponse automatisées dans Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air). Assurez-vous que vos fonctionnalités [Office 365 Advanced Threat Protection](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) sont correctement configurées.

Bien que certaines alertes et stratégies de sécurité puissent déclencher des enquêtes automatiques, aucune action de correction n’est effectuée automatiquement pour le courrier électronique et le contenu. Au lieu de cela, toutes les actions de correction pour le contenu du courrier électronique et de la messagerie attendent l’approbation de votre équipe des opérations de sécurité dans le [Centre de notifications](mtp-action-center.md).

Les paramètres de sécurité d’Office 365 aident à protéger la messagerie et le contenu. Pour afficher ou modifier ces paramètres, suivez les instructions de la section se [protéger contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats).

1. Dans le centre de sécurité Microsoft 365 ( [https://security.microsoft.com/](https://security.microsoft.com/) ), accédez à **stratégies**  >  **Threat Protection**.

2. Assurez-vous que toutes les stratégies suivantes sont configurées. Pour obtenir de l’aide et des recommandations, consultez la rubrique se [protéger contre les menaces](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats).

   - [Anti-programme malveillant (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-1---anti-malware-protection)
   - [Protection contre le hameçonnage (spyware) ATP (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-2---anti-phishing-protection)
   - [Pièces jointes fiables ATP (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#atp-safe-attachments-policies)
   - [Liens fiables ATP (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#atp-safe-links-policies)
   - [Blocage du courrier indésirable (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-3---anti-spam-protection) 

4. Assurez-vous que [Office 365 ATP pour SharePoint, OneDrive et Microsoft teams](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-5---turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams-workloads) est activé.

5. Assurez-vous que la [purge automatique pour](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#zero-hour-auto-purge-for-email-in-eop) la protection de la messagerie est activée. 

8. (Cette option est facultative.) Consultez vos [stratégies d’alerte Office 365](https://docs.microsoft.com/microsoft-365/compliance/alert-policies) dans le centre de conformité Microsoft 365 ( [https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies) ). Plusieurs stratégies d’alerte par défaut figurent dans la catégorie gestion des menaces. Certaines de ces alertes peuvent déclencher une enquête et une réponse automatisées. Pour en savoir plus, consultez la rubrique [stratégies d’alerte par défaut](https://docs.microsoft.com/microsoft-365/compliance/alert-policies?#default-alert-policies).
 
## <a name="make-sure-microsoft-threat-protection-is-turned-on"></a>Vérifier que la protection contre les menaces Microsoft est activée

1. Accédez au centre de sécurité Microsoft 365 ( [https://security.microsoft.com](https://security.microsoft.com) ) et connectez-vous.

2. Dans le volet de navigation, recherchez les **incidents**, le **Centre de notifications**et la **chasse**, comme illustré dans l’image suivante :

   :::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="MTP sur":::

   - Si vous constatez des **incidents**, le **Centre de notifications**et la **chasse**, la protection contre les menaces Microsoft est activée. Passez à la procédure suivante, [Vérifiez ou modifiez le niveau d’automatisation pour les groupes d’appareils](#review-or-change-the-automation-level-for-device-groups).

   - Si vous ne voyez *pas* les **incidents**, le **Centre de maintenance**ou la **chasse**, il se peut que la protection contre les menaces Microsoft ne soit pas activée. Dans ce cas, passez à l’étape suivante.

3. Dans le volet de navigation, choisissez **paramètres**  >  **Microsoft Threat Protection**. Vérifiez que la protection contre les menaces Microsoft est activée. 

   Besoin d’aide ? Voir [activer la protection contre les menaces Microsoft](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable).

## <a name="review-pending-and-completed-actions-in-the-action-center"></a>Vérifier les actions en attente et terminées dans le centre de notifications

Une fois que vous avez configuré l’analyse et la réponse automatisées dans Microsoft Threat Protection, l’étape suivante consiste à visiter le centre de notifications ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ). Vous pouvez ainsi passer en revue et approuver les actions en attente et consulter les actions correctives qui ont été effectuées automatiquement. 

[Visitez le centre de notifications](mtp-action-center.md).
