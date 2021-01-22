---
title: Configurer des fonctionnalités automatisées d’examen et de réponse dans Microsoft 365 Defender
description: Configurer l’examen et la réponse automatisés avec auto-ressource dans Microsoft 365 Defender
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: m365-security
localization_priority: Normal
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.custom: autoir
ms.reviewer: evaldm, isco
f1.keywords: CSH
ms.technology: m365d
ms.openlocfilehash: 123b3b5f8514e9b3914b98178191d60e78280991
ms.sourcegitcommit: 855719ee21017cf87dfa98cbe62806763bcb78ac
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/22/2021
ms.locfileid: "49930317"
---
# <a name="configure-automated-investigation-and-response-capabilities-in-microsoft-365-defender"></a>Configurer des fonctionnalités automatisées d’examen et de réponse dans Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


Microsoft 365 Defender inclut de puissantes fonctionnalités [d’investigation](mtp-autoir.md) et de réponse automatisées qui peuvent faire gagner beaucoup de temps et d’efforts à votre équipe en matière d’opérations de sécurité. Grâce à une autorésuration, ces fonctionnalités imitent les étapes qu’un analyste de sécurité prend pour examiner les menaces et y répondre, seulement plus rapidement et avec plus de possibilité d’échelle. Cet article explique comment configurer l’examen et la réponse automatisés dans Microsoft 365 Defender.

Pour configurer des fonctionnalités d’examen et de réponse automatisées, suivez les étapes suivantes :

1. [Examinez les conditions préalables.](#prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender)
2. [Examinez ou modifiez le niveau d’automatisation pour les groupes d’appareils.](#review-or-change-the-automation-level-for-device-groups)
3. [Examinez vos stratégies de sécurité et d’alerte dans Office 365.](#review-your-security-and-alert-policies-in-office-365)
4. [Assurez-vous que Microsoft 365 Defender est allumé.](#make-sure-microsoft-365-defender-is-turned-on)

Ensuite, une fois toutes les actions définies, examinez les actions en attente et terminées [dans le centre de actions.](#review-pending-and-completed-actions-in-the-action-center)

## <a name="prerequisites-for-automated-investigation-and-response-in-microsoft-365-defender"></a>Conditions préalables à l’examen et à la réponse automatisés dans Microsoft 365 Defender

|Conditions requises |Détails |
|--|--|
|Conditions d’abonnement |L’un des abonnements : <ul><li>Microsoft 365 E5</li><li>Microsoft 365 A5</li><li>Microsoft 365 E5 Sécurité</li><li>Sécurité Microsoft 365 A5</li><li>Office 365 E5 plus Enterprise Mobility + Security E5 plus Windows E5</li></ul><p> Consultez les conditions requises pour les [licences Microsoft 365 Defender.](https://docs.microsoft.com/microsoft-365/security/mtp/prerequisites?#licensing-requirements)|
|Configuration réseau requise |<ul><li>[Microsoft Defender pour l’identité](https://docs.microsoft.com/azure-advanced-threat-protection/what-is-atp) activé</li><li>[Microsoft Cloud App Security](https://docs.microsoft.com/cloud-app-security/what-is-cloud-app-security) configuré</li><li>[Intégration de Microsoft Defender pour l’identité](https://docs.microsoft.com/cloud-app-security/mdi-integration)</li></ul>|
|Configuration requise pour ordinateur Windows |Windows 10, version 1709 ou ultérieure installée (voir les informations de publication de [Windows 10)](https://docs.microsoft.com/windows/release-information/)avec les services de protection contre les menaces suivants configurés :<ul><li>[Microsoft Defender pour point de terminaison](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/configure-endpoints)</li><li>[Microsoft Defender Antivirus](https://docs.microsoft.com/windows/security/threat-protection/windows-defender-antivirus/configure-windows-defender-antivirus-features)</li></ul>|
|Protection du contenu du courrier électronique et des fichiers Office |[Microsoft Defender pour Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp#configure-atp-policies) configuré |
|Autorisations |<ul><li>Pour configurer des fonctionnalités d’examen et de réponse automatisées, vous devez avoir le rôle Administrateur général ou Administrateur de la sécurité attribué dans Azure Active Directory ( ) ou dans le Centre d’administration [https://portal.azure.com](https://portal.azure.com) Microsoft 365 ( [https://admin.microsoft.com](https://admin.microsoft.com) ).</li><p><li>Pour obtenir les autorisations nécessaires pour travailler avec des fonctionnalités d’examen et de réponse automatisées, telles que la révision, l’approbation ou le rejet des actions en attente, voir [Autorisations requises](mtp-action-center.md#required-permissions-for-action-center-tasks)pour les tâches du centre de gestion des actions.</li></ul>|

## <a name="review-or-change-the-automation-level-for-device-groups"></a>Examiner ou modifier le niveau d’automatisation pour les groupes d’appareils

L’application d’enquêtes automatisées et l’action de correction automatique ou seulement après approbation de vos appareils dépendent de certains paramètres, tels que les stratégies de groupe d’appareils de votre organisation. Examinez le niveau d’automatisation de vos stratégies de groupe d’appareils.

1. Go to the Microsoft Defender Security Center ( [https://securitycenter.windows.com](https://securitycenter.windows.com) ) and sign in.

2. Go to **Settings**  >  **Permissions**  >  **Device groups**.

3. Examinez vos stratégies de groupe d’appareils. En particulier, regardez la colonne **de niveau correction.** Nous vous recommandons **d’utiliser Full - corriger les menaces automatiquement**.  Vous devrez peut-être créer ou modifier vos groupes d’appareils pour obtenir le niveau d’automatisation voulu. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants :

   - [Comment les menaces sont corrigés](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/automated-investigations#how-threats-are-remediated)
   - [Créer et gérer des groupes d’appareils](https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/machine-groups)

## <a name="review-your-security-and-alert-policies-in-office-365"></a>Passer en revue vos stratégies de sécurité et d’alerte dans Office 365

Microsoft fournit des stratégies [d’alerte intégrées](https://docs.microsoft.com/microsoft-365/compliance/alert-policies) qui permettent d’identifier certains risques. Ces risques incluent l’abus des autorisations d’administrateur Exchange, l’activité des programmes malveillants, les menaces externes et internes potentielles, ainsi que les risques de gouvernance des informations. Certaines alertes peuvent déclencher une [enquête et une réponse automatisées dans Office 365.](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-air) Assurez-vous que vos fonctionnalités de Microsoft Defender pour [Office 365](https://docs.microsoft.com/microsoft-365/security/office-365-security/office-365-atp) sont configurées correctement.

Bien que certaines alertes et stratégies de sécurité peuvent déclencher des enquêtes automatisées, aucune action de correction n’est prise automatiquement pour le courrier électronique et le contenu. Au lieu de cela, toutes les actions de correction pour le courrier électronique et le contenu de courrier électronique attendent l’approbation de votre équipe des opérations de sécurité dans le centre [de actions.](mtp-action-center.md)

Les paramètres de sécurité dans Office 365 contribuent à protéger le courrier électronique et le contenu. Pour afficher ou modifier ces paramètres, suivez les instructions de [La protection contre les menaces.](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)

1. Dans le Centre de sécurité Microsoft 365 ( [https://security.microsoft.com/](https://security.microsoft.com/) ), allez à **Stratégies**  >  **de protection contre les menaces.**

2. Assurez-vous que toutes les stratégies suivantes sont configurées. Pour obtenir de l’aide et des recommandations, voir [Protéger contre les menaces.](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats)

   - [Anti-programme malveillant (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-1---anti-malware-protection)
   - [Anti-hameçonnage dans Defender pour Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-2---anti-phishing-protection)
   - [Pièces jointes sécurisées (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#atp-safe-attachments-policies)
   - [Liens sécurisés (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#atp-safe-links-policies)
   - [Anti-courrier indésirable (Office 365)](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-3---anti-spam-protection)

3. [Assurez-vous que Microsoft Defender pour Office 365 pour SharePoint, OneDrive](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#part-5---turn-on-atp-for-sharepoint-onedrive-and-microsoft-teams-workloads) et Microsoft Teams est allumé.

4. [Assurez-vous que la purge automatique d’heure zéro](https://docs.microsoft.com/microsoft-365/security/office-365-security/protect-against-threats#zero-hour-auto-purge-for-email-in-eop) pour la protection de la messagerie est en vigueur.

5. (Cette étape est facultative.) Examinez vos [stratégies d’alerte Office 365](https://docs.microsoft.com/microsoft-365/compliance/alert-policies) dans le Centre de conformité Microsoft 365 ( [https://compliance.microsoft.com/compliancepolicies](https://compliance.microsoft.com/compliancepolicies) ). Plusieurs stratégies d’alerte par défaut sont dans la catégorie Gestion des menaces. Certaines de ces alertes peuvent déclencher une enquête et une réponse automatisées. Pour en savoir plus, consultez [stratégies d’alerte par défaut.](https://docs.microsoft.com/microsoft-365/compliance/alert-policies?#default-alert-policies)

## <a name="make-sure-microsoft-365-defender-is-turned-on"></a>Assurez-vous que Microsoft 365 Defender est allumé

1. Go to the Microsoft 365 security center ( [https://security.microsoft.com](https://security.microsoft.com) ) and sign in.

2. Dans le volet de navigation, recherchez **Incidents,** Centre de action et **Recherche,** comme illustré dans l’image suivante :

   :::image type="content" source="../../media/mtp-enable/mtp-on.png" alt-text="MTP sur":::

   - Si vous voyez **incidents,** centre **de action** et **de** recherche , Microsoft 365 Defender est allumé. Consultez la procédure, [examinez ou modifiez le niveau d’automatisation pour les groupes d’appareils](#review-or-change-the-automation-level-for-device-groups) (dans cet article).

   - Si vous ne *voyez pas* **incidents,** centre **de** action ou de **recherche,** Microsoft 365 Defender n’est peut-être pas allumé. Dans ce cas, passer à l’étape suivante ([Passer en revue](#review-pending-and-completed-actions-in-the-action-center)les actions en attente et terminées, dans cet article).

3. Dans le volet de navigation, choisissez **Paramètres**  >  **Microsoft 365 Defender**. Confirmez que Microsoft 365 Defender est allumé.

   Besoin d'aide ? Voir [Activer Microsoft 365 Defender.](https://docs.microsoft.com/microsoft-365/security/mtp/mtp-enable)

## <a name="review-pending-and-completed-actions-in-the-action-center"></a>Passer en revue les actions en attente et terminées dans le centre de actions

Une fois que vous avez configuré l’examen et la réponse automatisés dans Microsoft 365 Defender, l’étape suivante consiste à visiter le centre de réponse ( [https://security.microsoft.com/action-center](https://security.microsoft.com/action-center) ). Vous pouvez y examiner et approuver les actions en attente, et voir les actions de correction qui ont été prises automatiquement ou manuellement.

[Visitez le centre de l’action.](mtp-action-center.md)
