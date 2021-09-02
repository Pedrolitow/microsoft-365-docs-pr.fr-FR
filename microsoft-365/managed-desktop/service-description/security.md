---
title: Technologies de sécurité dans Microsoft Manged Desktop
description: Technologies utilisées pour la sécurité des appareils, la gestion des identités et des accès, la sécurité du réseau et la sécurité des informations
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 9f2e3b9d623f5f2b019296dc08c34c32ace2e9d6
ms.sourcegitcommit: ef9cd046c47b340686a4f7bb123ea3b0a269769a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/02/2021
ms.locfileid: "58863772"
---
# <a name="security-technologies-in-microsoft-managed-desktop"></a>Technologies de sécurité dans Microsoft Manged Desktop

<!--Security, also Onboarding doc: data handling/store, privileged account access -->

Microsoft Manged Desktop utilise plusieurs technologies Microsoft pour sécuriser les appareils gérés et les données. En outre, le centre Microsoft Manged Desktop des opérations de sécurité utilise différents [processus](security-operations.md) conjointement avec ces technologies.

Notamment :

- [Sécurité des appareils](#device-security) : sécurité et protection sur Microsoft Manged Desktop appareils
- [Gestion des identités et des accès :](#identity-and-access-management) gestion de l’utilisation sécurisée des appareils par Azure Active Directory services d’identité
- [Sécurité réseau](#network-security) : informations VPN et Microsoft Manged Desktop solution et paramètres recommandés
- [Sécurité des informations](#information-security) : services disponibles facultatifs pour protéger davantage les informations sensibles

Pour plus d’informations sur les pratiques de stockage, d’utilisation et de sécurité des données utilisées par Microsoft Manged Desktop données, consultez notre livre blanc sur [https://aka.ms/mmd-data](https://aka.ms/mmd-data) .


## <a name="device-security"></a>Sécurité de l’appareil

Microsoft Manged Desktop s’assure que tous les appareils gérés sont sécurisés et protégés, et détecte les menaces dès que possible à l’aide des services suivants :

Service | Description
--- | ---
Antivirus | Antivirus Microsoft Defender est installé et configuré<br>Antivirus Microsoft Defender définitions sont à jour
Chiffrement de volume complet | Windows BitLocker est la solution de chiffrement de volume pour Microsoft Manged Desktop périphériques.<br><br>Une fois qu’une organisation est intégrée au service, les appareils sont chiffrés à l’aide de Windows BitLocker avec le module de plateforme de gestion de la plateforme de confiance (TPM) intégré afin d’empêcher tout accès non autorisé aux données locales lorsque l’appareil est en mode veille ou hors service.
Analyse | Microsoft Defender pour le point de terminaison est utilisé pour la surveillance des menaces de sécurité sur tous Microsoft Manged Desktop appareils. Defender pour le point de terminaison permet aux clients d’entreprise de détecter, d’examiner et de répondre aux menaces avancées dans leur réseau d’entreprise. Pour plus d’informations, [voir Microsoft Defender pour le point de terminaison.](/windows/threat-protection/windows-defender-atp/windows-defender-advanced-threat-protection)
Mises à jour du système d’exploitation | Microsoft Manged Desktop appareils sont toujours sécurisés avec les dernières mises à jour de sécurité.
Configuration de l’appareil sécurisé | Microsoft Manged Desktop implémente la ligne de base de sécurité Microsoft. Pour plus d’informations, [voir Windows de sécurité.](/windows/security/threat-protection/windows-security-baselines)



## <a name="identity-and-access-management"></a>Gestion des identités et des accès

La gestion des identités et des accès protège les biens d’entreprise et les données stratégiques de l’entreprise. Microsoft Manged Desktop des appareils pour garantir une utilisation sécurisée avec Azure Active Directory (Azure AD) gérées. Il incombe au client de conserver des informations précises dans son client Azure AD.

Service | Description
--- | ---
Authentification biométrique | Windows Hello permet aux utilisateurs de se connecter à l’aide de leur visage ou d’un code confidentiel, ce qui rend les mots de passe plus difficiles à oublier ou à voler. Les clients sont chargés d’implémenter les conditions préalables nécessaires pour leur active directory local pour l’utilisation de ce service dans une configuration hybride. Pour plus d’informations, [voir Windows Hello.](/windows-hardware/design/device-experiences/windows-hello) 
Autorisation utilisateur standard | Pour protéger le système et le sécuriser, l’utilisateur se voit attribuer des autorisations d’utilisateur standard. Cette autorisation est attribuée dans le cadre de l’Windows d’autopilot out-of-box.



## <a name="network-security"></a>Sécurité réseau

Les clients sont responsables de la sécurité du réseau. 

Service | Description
--- | ---
VPN | Les clients possèdent leur infrastructure VPN, pour s’assurer que des ressources limitées de l’entreprise peuvent être exposées en dehors de l’intranet.<br><br>Exigence minimale : Microsoft Manged Desktop nécessite une solution VPN compatible Windows 10 prise en charge. Si votre organisation a besoin d’une solution VPN, elle doit prendre en charge Windows 10 et être empaqueté et déployable via Intune. Pour plus d’informations, contactez votre éditeur de logiciels.<br><br>Recommandation :<br>- Microsoft recommande une solution VPN moderne qui pourrait être facilement déployée via Intune pour pousser les profils VPN. Cette approche offre un moyen toujours continu, transparent, fiable et sécurisé d’accéder au réseau d’entreprise. Pour plus d’informations, [voir [Paramètres VPN dans Intune]](/intune/vpn-settings-configure).<br>- Les clients VPN épais, ou les clients VPN plus anciens, ne sont pas recommandés par Microsoft lors de l’utilisation de Microsoft Manged Desktop car cela peut avoir un impact sur l’environnement utilisateur.<br>- Microsoft recommande que le trafic web sortant soit directement vers Internet sans passer par le VPN afin d’éviter tout problème de performances.<br>- Dans l’idéal, Microsoft recommande d’utiliser Azure Active Directory proxy d’application au lieu d’un VPN.


## <a name="information-security"></a>Sécurité des informations

Vous pouvez configurer ces services facultatifs pour protéger les biens à valeur élevée de l’entreprise. 

Service | Description
--- | ---
Récupération des données  | Les informations stockées dans les dossiers clés de l’appareil sont enregistrées OneDrive Entreprise. Microsoft Manged Desktop n’est pas responsable des données qui ne sont pas synchronisées avec OneDrive Entreprise.
Protection des informations Windows | Pour les entreprises qui requièrent des niveaux élevés de sécurité des informations, nous vous [Windows protection](/windows/threat-protection/windows-information-protection/protect-enterprise-data-using-wip) des informations et Azure [Information Protection.](https://www.microsoft.com/cloud-platform/azure-information-protection)
