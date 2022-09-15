---
title: Utiliser la protection des identités, des appareils et des menaces pour la réglementation de la confidentialité des données
ms.author: bcarter
author: brendacarter
f1.keywords:
- NOCSH
manager: laurawi
ms.date: 06/09/2020
audience: ITPro
ms.topic: article
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
ms.collection:
- highpri
- M365-security-compliance
- Strat_O365_Enterprise
- m365solution-infoprotection
- m365solution-scenario
- zerotrust-solution
ms.custom: ''
description: Empêchez les violations de données personnelles avec les services d’identité, d’appareil et de protection contre les menaces de Microsoft 365.
ms.openlocfilehash: 1769f67d9815a1a7a3e556e9078aace6366fbf4c
ms.sourcegitcommit: 0af064e8b6778060f1bd365378d69b16fc9949b5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67731549"
---
# <a name="use-identity-device-and-threat-protection-for-data-privacy-regulation"></a>Utiliser la protection des identités, des appareils et des menaces pour la réglementation de la confidentialité des données

Microsoft 365 fournit un certain nombre de fonctionnalités de protection des identités, des appareils et des menaces que les organisations peuvent utiliser pour se conformer aux réglementations de conformité relatives à la confidentialité des données. Cet article décrit ce que les réglementations de confidentialité des données exigent dans ces domaines et fournit une liste des fonctionnalités et services Microsoft 365 associés avec des liens vers plus d’informations pour vous aider à répondre aux exigences d’implémentation.

## <a name="how-identity-device-and-threat-protection-relate-to-data-privacy-regulation"></a>Lien entre la protection des identités, des appareils et des menaces avec la réglementation sur la confidentialité des données

Bien que les réglementations sur la confidentialité des données varient en fonction de leur spécificité, l’essence de ce qu’elles appellent est incorporée dans l’article 5(1)(f) du RGPD, qui stipule que :

- Les données personnelles doivent être traitées de manière à garantir une sécurité appropriée des données personnelles, notamment la protection contre le traitement non autorisé ou illégal et contre les pertes, destructions ou dommages accidentels, à l’aide de mesures techniques ou organisationnelles appropriées (« intégrité et confidentialité »).

Étant donné que les violations de données personnelles sont souvent causées par une compromission de compte d’administrateur ou d’utilisateur final et un accès système malveillant. Par exemple, un piratage de compte d’administrateur peut entraîner l’exfiltration de numéros de carte de crédit client ou d’autres informations personnelles. Toutes les protections d’identité, d’appareil et de menace généralement recommandées disponibles avec Microsoft 365 doivent éventuellement être implémentées, ce qui sera reflété dans votre score de conformité, disponible dans le Gestionnaire de conformité.

## <a name="using-the-results-of-your-assessment-work-and-compliance-manager"></a>Utilisation des résultats de votre travail d’évaluation et du Gestionnaire de conformité

Le Gestionnaire de conformité inclut la protection des identités, des appareils et des menaces à l’aide des catégories suivantes :

- L’identité correspond à la catégorie **Contrôle d’accès**
- L’appareil correspond à la catégorie **Gérer les appareils**
- La protection contre les menaces correspond à la catégorie **Protéger contre les menaces**
 
Si elles sont sélectionnées dans notre échantillon de quatre réglementations majeures sur la confidentialité des données, le Gestionnaire de conformité spécifie 90 actions d’amélioration, dont la plupart sont notées « 27 ». Étant donné qu’un tel nombre est appelé par le Gestionnaire de conformité pour ces catégories, certaines des catégories les plus courantes sont répertoriées ici, à des fins de référence.

Utilisez [Azure Active Directory (Azure AD)](https://azure.microsoft.com/services/active-directory/) pour l’identité et la catégorie **Contrôle d’accès** , avec laquelle vous pouvez :

- Implémenter une authentification relecture (pour empêcher les attaques « Man in the middle »)
- Bloquer l’authentification héritée.
- Configurez les stratégies de risque de connexion et de risque de connexion utilisateur.
- Activez l’accès conditionnel et l’authentification multifacteur (MFA) pour les administrateurs et les non-administrateurs.
- Configurez et appliquez des stratégies de mot de passe.
- Limitez l’accès aux comptes privilégiés avec Azure AD Privileged Identity Management.
- Désactivez l’accès lors de l’arrêt.
- Auditer les comptes d’utilisateur et les modifications d’état.
- Passez en revue les modifications apportées au groupe de rôles et à l’administration.

Utilisez [Microsoft Endpoint Manager](https://www.microsoft.com/microsoft-365/microsoft-endpoint-manager) pour les appareils et la catégorie **Gérer les appareils**, avec laquelle vous pouvez :

- Bloquer les appareils mobiles endommagés et rootés.
- Configurez Intune pour la gestion des appareils mobiles.
- Créez des stratégies de conformité pour les appareils Android, iOS, macOS et Windows.
- Créez un profil de configuration d’appareil pour les appareils Android, iOS, macOS et Windows.
- Créez des stratégies de protection des applications pour iOS et Windows.
- Masquez les informations à l’aide de l’écran de verrouillage.
- Implémentez des stratégies de mot de passe pour les appareils mobiles.
- Exiger que les appareils mobiles se verrouillent en cas d’inactivité.
- Exiger que les appareils mobiles réinitialisent en cas d’échecs de connexion multiples.

Utilisez [Exchange Online Protection et Microsoft Defender pour Office 365](../security/office-365-security/defender-for-office-365.md) pour la catégorie **Protéger contre les menaces**, avec laquelle vous pouvez :

- Activez l’authentification de l’expéditeur (SPF, DMARC et DKIM).
- Configurez Microsoft Defender pour Office 365 stratégies anti-hameçonnage.
- Implémentez des pièces jointes sécurisées.
- Implémentez des liens sécurisés.
- Implémenter des stratégies de détection et de réponse des programmes malveillants.
- Implémentez des stratégies de courrier indésirable sortant et entrant.

### <a name="references"></a>Références:

- [Stratégies communes pour les identités et l’accès aux appareils](../security/office-365-security/identity-access-policies.md)
- [Protection contre les menaces dans Office 365](https://support.office.com/article/protect-against-threats-in-office-365-b10023f6-f30f-45d3-b3ad-b71aa4aa0d58)
- [Pièces jointes fiables](../security/office-365-security/safe-attachments.md)
- [Liens fiables](../security/office-365-security/safe-links.md)
- [Documents sécurisés](../security/office-365-security/safe-docs.md)
