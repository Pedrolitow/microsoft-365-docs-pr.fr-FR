---
title: Configurer des fonctionnalités d’examen et de réponse automatisées dans Microsoft 365 Defender
description: Configurer l’examen et la réponse automatisés avec auto-ressource dans Microsoft 365 Defender
search.appverid: MET150
ms.author: josephd
author: JoeDavies-MSFT
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: autoir
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.technology: m365d
ms.openlocfilehash: e25fab99718c791c64b583283237815736c450ae
ms.sourcegitcommit: f3d1009840513703c38bab99a6e13a3656eae5ee
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2021
ms.locfileid: "52793183"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Configurer des fonctionnalités d’examen et de réponse automatisées dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

Microsoft 365 Defender inclut de [puissantes fonctionnalités d’investigation](m365d-autoir.md) et de réponse automatisées qui peuvent faire gagner beaucoup de temps et d’efforts à votre équipe en matière d’opérations de sécurité. Grâce [à une auto-ressource,](m365d-autoir.md#how-automated-investigation-and-self-healing-works)ces fonctionnalités imitent les étapes qu’un analyste de sécurité prend pour examiner les menaces et y répondre, uniquement plus rapidement et avec plus de possibilité d’échelle.

Cet article explique comment configurer l’examen et la réponse automatisés dans Microsoft 365 Defender en suivant les étapes ci-après :

1. [Examinez les conditions préalables.](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
2. [Examinez ou modifiez le niveau d’automatisation pour les groupes d’appareils.](#review-or-change-the-automation-level-for-device-groups)
3. [Examinez vos stratégies de sécurité et d’alerte dans Office 365](#review-your-security-and-alert-policies-in-office-365).
4. [Assurez-vous Microsoft 365 Defender est allumé.](#make-sure-microsoft-365-defender-is-turned-on)

Ensuite, une fois que vous avez tous été mis en place, vous pouvez afficher et gérer les actions de correction [dans le centre de actions.](m365d-autoir-actions.md)

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Conditions préalables à l’examen et à la réponse automatisés dans Microsoft 365 Defender

<br>

****

|Conditions requises|Détails|
|---|---|
|Conditions d’abonnement|L’un de ces abonnements : <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E3 l’Microsoft 365 E5 Sécurité de module</li><li>Microsoft 365 A3 avec le module Microsoft 365 sécurité A5</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5</li></ul> <p> Voir [Microsoft 365 licences Requises pour Defender.](./prerequisites.md#licensing-requirements)|
|Configuration réseau requise|<ul><li>[Microsoft Defender pour l’identité](/azure-advanced-threat-protection/what-is-atp) activé</li><li>[Microsoft Cloud App Security](/cloud-app-security/what-is-cloud-app-security) configuré</li><li>[Intégration de Microsoft Defender pour l’identité](/cloud-app-security/mdi-integration)</li></ul>|
|Configuration requise pour ordinateur Windows|<ul><li>Windows 10, version 1709 ou ultérieure installée (voir Windows 10 [de publication)](/windows/release-information/)</li><li>Les services de protection contre les menaces suivants sont configurés :<ul><li>[Microsoft Defender pour point de terminaison](../defender-endpoint/configure-endpoints.md)</li><li>[Antivirus Microsoft Defender](/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul></li></ul>|
|Protection du contenu des e-mails et des Office de messagerie|[Microsoft Defender pour Office 365](/microsoft-365/security/office-365-security/defender-for-office-365#configure-atp-policies) configuré|
|Autorisations|Pour configurer des fonctionnalités d’examen et de réponse automatisées, vous devez avoir le rôle Administrateur général ou Administrateur de la sécurité attribué dans Azure Active Directory ( ) ou dans le Centre d’administration <https://portal.azure.com> Microsoft 365 ( <https://admin.microsoft.com> ). <p> Pour obtenir les autorisations nécessaires pour travailler avec des fonctionnalités d’examen et de réponse automatisées, telles que la révision, l’approbation ou le rejet des actions en attente, voir [Autorisations requises](m365d-action-center.md#required-permissions-for-action-center-tasks)pour les tâches du centre de gestion des actions.|
|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Examiner ou modifier le niveau d’automatisation pour les groupes d’appareils

L’application d’enquêtes automatisées et l’action de correction automatique ou seulement après approbation de vos appareils dépendent de certains paramètres, tels que les stratégies de groupe d’appareils de votre organisation. Examinez le niveau d’automatisation configuré pour vos stratégies de groupe d’appareils.

1. Go to the Centre de sécurité Microsoft Defender ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) and sign in.
2. Go to **Paramètres**  >  **Permissions**  >  **Device groups**.
3. Examinez vos stratégies de groupe d’appareils. En particulier, regardez la colonne **de niveau correction.** Nous vous recommandons **d’utiliser Full - corriger les menaces automatiquement**.  Vous devrez peut-être créer ou modifier vos groupes d’appareils pour obtenir le niveau d’automatisation voulu. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants :
   - [Comment les menaces sont corrigés](/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Créer et gérer des groupes d’appareils](/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Passer en revue vos stratégies de sécurité et d’alerte dans Office 365

Microsoft fournit des stratégies [d’alerte intégrées](../../compliance/alert-policies.md) qui permettent d’identifier certains risques. Ces risques incluent les abus Exchange autorisations d’administrateur, l’activité des programmes malveillants, les menaces externes et internes potentielles, ainsi que les risques de gouvernance des informations. Certaines alertes peuvent déclencher une [enquête et une réponse automatisées dans Office 365](../office-365-security/office-365-air.md). Assurez-vous [que vos fonctionnalités defender pour Office 365](../office-365-security/defender-for-office-365.md) sont configurées correctement.

Bien que certaines alertes et stratégies de sécurité peuvent déclencher des enquêtes automatisées, aucune action de correction n’est prise automatiquement pour le courrier *électronique et le contenu.* Au lieu de cela, toutes les actions de correction pour le courrier électronique et le contenu de courrier électronique attendent l’approbation de votre équipe des opérations de sécurité dans le centre [de gestion de l’action.](m365d-action-center.md)

Les paramètres de sécurité Office 365 protéger le courrier électronique et le contenu. Pour afficher ou modifier ces paramètres, suivez les instructions de [La protection contre les menaces.](../office-365-security/protect-against-threats.md)

1. Dans le centre Microsoft 365 de sécurité ( [https://security.microsoft.com](https://security.microsoft.com) ), go to Policies & **Rules** \> **Threat policies**.
2. Assurez-vous que toutes les stratégies suivantes sont configurées. Pour obtenir de l’aide et des recommandations, voir [Protéger contre les menaces.](/microsoft-365/security/office-365-security/protect-against-threats)
   - [Anti-programme malveillant](../office-365-security/protect-against-threats.md#part-1---anti-malware-protection-in-eop)
   - [Anti-hameçonnage](../office-365-security/protect-against-threats.md#part-2---anti-phishing-protection-in-eop-and-defender-for-office-365)
   - [Pièces jointes fiables](../office-365-security/protect-against-threats.md#safe-attachments-policies-in-microsoft-defender-for-office-365)
   - [Liens fiables](../office-365-security/protect-against-threats.md#safe-links-policies-in-microsoft-defender-for-office-365)
   - [Anti-courrier indésirable](../office-365-security/protect-against-threats.md#part-3---anti-spam-protection-in-eop)
3. [Assurez-vous que Microsoft Defender for Office 365 for SharePoint, OneDrive, and Microsoft Teams](../office-365-security/protect-against-threats.md#part-5---verify-safe-attachments-for-sharepoint-onedrive-and-microsoft-teams-is-turned-on) is turned on.
4. [Assurez-vous que la purge automatique d’heure zéro](../office-365-security/protect-against-threats.md#zero-hour-auto-purge-for-email-in-eop) pour la protection de la messagerie est en vigueur.
5. (Cette étape est facultative.) Examinez vos [stratégies Office 365 d’alerte](../../compliance/alert-policies.md) dans le centre Microsoft 365 conformité ( [https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies) ). Plusieurs stratégies d’alerte par défaut sont dans la catégorie Gestion des menaces. Certaines de ces alertes peuvent déclencher une enquête et une réponse automatisées. Pour en savoir plus, consultez [stratégies d’alerte par défaut.](../../compliance/alert-policies.md#default-alert-policies)

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Assurez-vous Microsoft 365 Defender est allumé

:::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="MTP sur":::

1. Connectez-vous au centre Microsoft 365 de sécurité ( [https://security.microsoft.com](https://security.microsoft.com) ).
2. Dans le volet de navigation, recherchez **Incidents,** Centre de action et **Recherche,** comme illustré dans l’image précédente.
   - Si vous voyez **incidents,** centre **de l’action** et **de** recherche , Microsoft 365 Defender est allumé. Consultez la section [Examiner ou modifier le niveau d’automatisation pour les groupes d’appareils](#review-or-change-the-automation-level-for-device-groups) de cet article.
   - Si vous ne *voyez pas* **incidents,** centre de l’action ou de **recherche,** Microsoft 365 Defender n’est peut-être pas allumé.  Dans ce cas, [visitez le centre de l’action.](m365d-action-center.md)
3. Dans le volet de navigation, choisissez **Paramètres**  >  **Microsoft 365 Defender.** Confirmez Microsoft 365 Defender est allumé.

> [!TIP]
> Besoin d’aide ? Voir [Activer Microsoft 365 Defender.](m365d-enable.md)

## <a name="next-steps"></a>Étapes suivantes

- [Actions de correction dans Microsoft 365 Defender](m365d-remediation-actions.md)
- [Visiter le Centre de notifications](m365d-action-center.md)
