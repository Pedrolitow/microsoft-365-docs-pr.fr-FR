---
title: Configurer des fonctionnalités d’enquête et de réponse automatisées dans Microsoft 365 Defender
description: Configurer l’investigation et la réponse automatisées avec l’auto-guérison dans Microsoft 365 Defender
search.appverid: MET150
ms.author: dansimp
author: dansimp
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.service: microsoft-365-security
ms.subservice: m365d
ms.localizationpriority: medium
ms.collection:
- m365-security
- tier2
ms.custom:
- autoir
- admindeeplinkDEFENDER
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.openlocfilehash: ed6437e990ca62934e1647bbfa113f3b163d8aef
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68051319"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Configurer des fonctionnalités d’enquête et de réponse automatisées dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender inclut de [puissantes fonctionnalités d’investigation et de réponse automatisées](m365d-autoir.md) qui peuvent faire gagner beaucoup de temps et d’efforts à votre équipe chargée des opérations de sécurité. Avec [l’auto-réparation](m365d-autoir.md#how-automated-investigation-and-self-healing-works), ces fonctionnalités imitent les étapes qu’un analyste de sécurité doit suivre pour examiner et répondre aux menaces, seulement plus rapidement et avec plus de capacité de mise à l’échelle.

Cet article explique comment configurer l’investigation et la réponse automatisées dans <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">Microsoft 365 Defender</a> en procédant comme suit :

1. [Passez en revue les prérequis](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender).
2. [Passez en revue ou modifiez le niveau d’automatisation pour les groupes d’appareils](#review-or-change-the-automation-level-for-device-groups).
3. [Passez en revue vos stratégies de sécurité et d’alerte dans Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Assurez-vous que Microsoft 365 Defender est activé](#make-sure-microsoft-365-defender-is-turned-on).

Ensuite, une fois que vous avez tous été configurés, vous pouvez [afficher et gérer les actions de correction dans le Centre d’actions](m365d-autoir-actions.md).

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Conditions préalables à l’examen et à la réponse automatisés dans Microsoft 365 Defender

<br>

****

|Conditions requises|Détails|
|---|---|
|Conditions d’abonnement|L’un de ces abonnements : <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 avec le module complémentaire Microsoft 365 E5 Sécurité</li><li>Microsoft 365 A3 avec le module complémentaire sécurité Microsoft 365 A5</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5</li></ul> <p> Consultez [Microsoft 365 Defender exigences en matière de licences](./prerequisites.md#licensing-requirements).|
|Configuration requise pour le réseau|<ul><li>[Microsoft Defender pour Identity](/azure-advanced-threat-protection/what-is-atp) activé</li><li>[Microsoft Defender for Cloud Apps](/cloud-app-security/what-is-cloud-app-security) configuré</li><li>[intégration Microsoft Defender pour Identity](/cloud-app-security/mdi-integration)</li></ul>|
|Configuration requise pour les appareils Windows|<ul><li>Windows 11</li><li>Windows 10, version 1709 ou ultérieure installée (voir [les informations de publication windows](/windows/release-information/))</li><li>Les services de protection contre les menaces suivants ont été configurés :<ul><li>[Microsoft Defender pour point de terminaison](../defender-endpoint/configure-endpoints.md)</li><li>[Antivirus Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|Protection du contenu des e-mails et des fichiers Office|[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) configuré|
|Autorisations|Pour configurer les fonctionnalités d’investigation et de réponse automatisées, le rôle Administrateur général ou Administrateur de sécurité doit être attribué dans Azure Active Directory (<https://portal.azure.com>) ou dans le Centre d'administration Microsoft 365 (<https://admin.microsoft.com>). <p> Pour obtenir les autorisations nécessaires pour utiliser des fonctionnalités d’investigation et de réponse automatisées, telles que l’examen, l’approbation ou le rejet d’actions en attente, consultez [Autorisations requises pour les tâches du Centre d’actions](m365d-action-center.md#required-permissions-for-action-center-tasks).|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Examiner ou modifier le niveau d’automatisation pour les groupes d’appareils

Que les enquêtes automatisées s’exécutent et que des actions de correction soient effectuées automatiquement ou uniquement après approbation de vos appareils dépendent de certains paramètres, tels que les stratégies de groupe d’appareils de votre organisation. Passez en revue le niveau d’automatisation configuré pour vos stratégies de groupe d’appareils.

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

2. Accédez aux **groupes d’appareils** **Paramètres** >  des **points de terminaison** >  sous **Autorisations**.

3. Passez en revue vos stratégies de groupe d’appareils. En particulier, examinez la colonne de **niveau Automation** . Nous vous recommandons d’utiliser **full - corriger automatiquement les menaces**.  Vous devrez peut-être créer ou modifier vos groupes d’appareils pour obtenir le niveau d’automatisation souhaité. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants :
   - [Comment les menaces sont corrigées](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Créer et gérer des groupes d’appareils](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Passez en revue vos stratégies de sécurité et d’alerte dans Office 365

Microsoft fournit des [stratégies d’alerte intégrées](../../compliance/alert-policies.md) qui permettent d’identifier certains risques. Ces risques incluent l’abus des autorisations d’administrateur Exchange, l’activité de programmes malveillants, les menaces externes et internes potentielles et les risques de gouvernance des informations. Certaines alertes peuvent déclencher une [investigation et une réponse automatisées dans Office 365](../office-365-security/office-365-air.md). Assurez-vous que vos fonctionnalités [Defender pour Office 365](../office-365-security/defender-for-office-365.md) sont correctement configurées.

Bien que certaines alertes et stratégies de sécurité puissent déclencher des investigations automatisées, *aucune action de correction n’est effectuée automatiquement pour les e-mails et le contenu*. Au lieu de cela, toutes les actions de correction pour le contenu des e-mails et des e-mails attendent l’approbation de votre équipe des opérations de sécurité dans le [Centre d’actions](m365d-action-center.md).

Les paramètres de sécurité dans Office 365 aident à protéger les e-mails et le contenu. Pour afficher ou modifier ces paramètres, suivez les instructions fournies dans [Protéger contre les menaces](../office-365-security/protect-against-threats.md).

1. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>, accédez à **Stratégies & stratégies de menace des règles**\>.

2. Vérifiez que toutes les stratégies suivantes sont configurées. Pour obtenir de l’aide et des recommandations, consultez [Protéger contre les menaces](/microsoft-365/security/office-365-security/protect-against-threats).
   - [Anti-programme malveillant](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Anti-hameçonnage](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Pièces jointes fiables](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Liens fiables](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Anti-spam](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)

3. Assurez-vous que [les pièces jointes sécurisées pour SharePoint, OneDrive et Microsoft Teams](../office-365-security/mdo-for-spo-odb-and-teams.md) sont activées.

4. Vérifiez que le [vidage automatique de zéro heure (ZAP) dans Exchange Online](../office-365-security/zero-hour-auto-purge.md) est en vigueur.

5. (Cette étape est facultative.) Passez en revue vos [stratégies d’alerte Office 365](../../compliance/alert-policies.md) dans le portail de conformité Microsoft Purview ([https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies)). Plusieurs stratégies d’alerte par défaut se trouvent dans la catégorie Gestion des menaces. Certaines de ces alertes peuvent déclencher une investigation et une réponse automatisées. Pour en savoir plus, consultez [Stratégies d’alerte par défaut](../../compliance/alert-policies.md#default-alert-policies).

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Vérifiez que Microsoft 365 Defender est activé

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="Volet de navigation gauche dans le portail Microsoft 365 Defender lorsque Microsoft 365 Defender est activé" lightbox="../../media/mtp-enable/mtp-on.png":::

1. Se connecter au <a href="https://go.microsoft.com/fwlink/p/?linkid=2077139" target="_blank">portail Microsoft 365 Defender</a>

2. Dans le volet de navigation, recherchez **incidents & centre d’alertes**, **de chasse** et **d’action** , comme illustré dans l’image précédente.
   - Si vous voyez **des incidents & le centre d’alertes**, **de chasse** et **d’action**, Microsoft 365 Defender est activé. Consultez la section [Révision ou modification du niveau d’automatisation pour les groupes d’appareils](#review-or-change-the-automation-level-for-device-groups) de cet article.
   - Si vous ne voyez *pas* **incidents**, **centre d’actions** ou **chasse**, Microsoft 365 Defender risque de ne pas être activé. Dans ce cas, [visitez le Centre d’action](m365d-action-center.md).

> [!TIP]
> Besoin d’aide ? Voir [Activer Microsoft 365 Defender](m365d-enable.md).

## <a name="next-steps"></a>Prochaines étapes

- [Actions de correction dans Microsoft 365 Defender](m365d-remediation-actions.md)
- [Visiter le Centre de notifications](m365d-action-center.md)
