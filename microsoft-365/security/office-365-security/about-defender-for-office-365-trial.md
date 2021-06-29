---
title: À propos de la version d’Office 365 Microsoft Defender
f1.keywords: ''
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: ''
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- seo-marvel-apr2020
ROBOTS: NOINDEX
description: Les administrateurs peuvent en savoir plus sur le mode d’essai de Microsoft Defender Office 365
ms.openlocfilehash: 50060e36a0dd6d82ccbdf6d2bb8a00b2bf5e9d6d
ms.sourcegitcommit: 6749455c52b0f98a92f6fffbc2bb86caf3538bd8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/29/2021
ms.locfileid: "53195008"
---
# <a name="about-the-microsoft-defender-for-office-365-trial"></a>À propos de la version d’Office 365 Microsoft Defender

Microsoft Defender for Office 365 protège votre organisation contre les menaces malveillantes qui sont posées par les messages électroniques, les liens (URL) et les outils de collaboration. Defender pour Office 365 inclut :

- **Stratégies de protection contre les menaces** : définissez des stratégies de protection contre les menaces pour définir le niveau de protection approprié pour votre organisation.
- **Rapports**: affichez des rapports en temps réel pour surveiller Defender Office 365 performances au niveau de votre organisation.
- **Fonctionnalités de recherche et de réponse aux menaces** : utilisez des outils de pointe pour étudier, comprendre, simuler et prévenir les menaces.
- **Fonctionnalités automatisées d’investigation et de réponse** : gagnez du temps pour investiguer et atténuer les menaces.

Une version d’essai de Microsoft Defender pour Office 365 est le moyen le plus simple d’essayer les fonctionnalités de Defender pour Office 365, et sa configuration ne prend que quelques clics. Une fois la configuration de la version d’essai terminée, toutes les fonctionnalités de Defender for Office 365 Plan 1 et Plan 2 sont disponibles dans l’organisation pendant 90 jours au plus.

> [!NOTE]
> La configuration automatisée décrite dans cet article est actuellement en prévisualisation publique et peut ne pas être disponible à votre emplacement.

## <a name="terms-and-conditions"></a>Conditions générales

La version d’Office 365 Defender for Office 365 est disponible pendant 90 jours et peut être lancée pour tous vos utilisateurs. Pour plus d’informations, [consultez Microsoft Defender pour obtenir Office 365 conditions d'& conditions générales.](defender-for-office-365-trial-terms-and-conditions.md)

## <a name="set-up-a-defender-for-office-365-trial"></a>Configurer une version d’Office 365 Defender

Une version d’essai permet aux organisations de configurer et de configurer facilement Defender pour Office 365 fonctionnalités. Lors de l’installation, les stratégies qui sont exclusives à Defender pour Office 365 (en particulier, les pièces [jointes Coffre,](safe-attachments.md)les liens [Coffre](safe-links.md)et la protection contre l’emprunt d’identité dans les stratégies [anti-courrier](set-up-anti-phishing-policies.md#impersonation-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)indésirable) sont appliquées à l’aide du modèle Standard pour les stratégies de sécurité prédéfinie. [](preset-security-policies.md)

Par défaut, ces stratégies sont limitées à tous les utilisateurs de l’organisation, mais les administrateurs peuvent personnaliser les stratégies pendant ou après l’installation afin qu’elles s’appliquent uniquement à des utilisateurs spécifiques.

Lors de l’installation, la fonctionnalité de réponse de Defender Office 365 (dans Defender pour Office 365 P2 ou équivalent) est également configurée pour l’ensemble de l’organisation. Aucune portée de stratégie n’est requise.

## <a name="licensing"></a>Licence

Dans le cadre de la configuration de la version d’essai, les licences Defender pour Office 365 sont automatiquement appliquées à l’organisation. Les licences sont gratuites pour les 90 premiers jours.

## <a name="permissions"></a>Autorisations

Pour démarrer ou mettre fin à la version  d’essai, vous devez être membre des rôles Administrateur général ou Administrateur de sécurité dans Azure Active Directory.  Pour plus d’informations, voir [à propos des rôles d’administrateur.](../../admin/add-users/about-admin-roles.md)

## <a name="additional-information"></a>Informations supplémentaires

Une fois que vous êtes inscrit à la version d’essai, la mise à disposition des modifications et des mises à jour peut prendre jusqu’à 2 heures. En outre, les administrateurs doivent se déconnecter et se connecter pour voir les modifications.

Les administrateurs peuvent désactiver la version d’essai à tout moment en <> carte.

## <a name="availability"></a>Disponibilité

La version d’évaluation de Defender pour Office 365 est progressivement mise en place pour les clients existants qui répondent à des critères spécifiques (y compris la géographie) et qui n’ont pas de licences Defender pour Office 365 Plan 1 ou Plan 2 (incluses dans leur abonnement ou en tant que modules).

## <a name="learn-more-about-defender-for-office-365"></a>En savoir plus sur Defender pour Office 365

Defender for Office 365 aide les organisations à sécuriser leur entreprise en offrant une gamme complète de fonctionnalités.

Vous pouvez également en savoir plus sur Defender for Office 365 dans ce [guide interactif.](https://techcommunity.microsoft.com/t5/video-hub/protect-your-organization-with-microsoft-365-defender/m-p/1671189)

![Diagramme conceptuel De Microsoft Defender Office 365](../../media/microsoft-defender-for-office-365.png)

### <a name="prevention"></a>Prévention

Une pile de filtrage robuste empêche une grande variété d’attaques ciblées et basées sur le volume, y compris la compromission de la messagerie professionnelle, le hameçonnage des informations d’identification, les ransomware et les programmes malveillants avancés.

- [Stratégies anti-hameçonnage : paramètres exclusifs dans Defender pour Office 365](set-up-anti-phishing-policies.md#exclusive-settings-in-anti-phishing-policies-in-microsoft-defender-for-office-365)
- [Pièces jointes fiables](safe-attachments.md)
- [Liens fiables](safe-links.md)

### <a name="detection"></a>Détection

L’IA de pointe détecte les contenus malveillants et suspects et met en corrélation les modèles d’attaque pour identifier les campagnes conçues pour éviter la protection.

- [Affichages des campagnes dans Microsoft Defender pour Office 365](campaigns.md)

### <a name="investigation-and-hunting"></a>Investigation et recherche

Les expériences puissantes permettent d’identifier, de hiérarchiser et d’examiner les menaces, avec des fonctionnalités de recherche avancées pour suivre les attaques Office 365.

- [Détections en temps réel et de l’Explorateur de menaces](threat-explorer.md)
- [Rapports en temps réel dans Defender pour Office 365](view-reports-for-mdo.md)
- [Suivis des menaces : nouveautés et remarques](threat-trackers.md)
- Intégration à [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

### <a name="response-and-remediation"></a>Réponse et correction

Les fonctionnalités d’automatisation et de réponse aux incidents étendues renforcent l’efficacité et l’efficacité de votre équipe de sécurité.

- [Examen et réponse automatisés (AIR) dans Microsoft Defender pour Office 365](office-365-air.md)

### <a name="awareness-and-training"></a>Sensibilisation et formation

Des fonctionnalités de simulation et de formation enrichies, ainsi que des expériences intégrées au sein des applications clientes, renforcent la sensibilisation des utilisateurs.

- [Commencer à utiliser la formation à la simulation d’attaque](attack-simulation-training-get-started.md)

### <a name="secure-posture"></a>Posture sécurisée

Les modèles recommandés et les informations de configuration aident les clients à obtenir et à rester sécurisés.

- [Stratégies de sécurité prédéfini dans EOP et Microsoft Defender pour Office 365](preset-security-policies.md)
- [Analyseur de configuration des stratégies de protection dans EOP et Microsoft Defender pour Office 365](configuration-analyzer-for-security-policies.md).

## <a name="give-feedback"></a>Faire part de vos commentaires

Vos commentaires nous aident à mieux protéger votre environnement contre les attaques avancées. Partagez votre expérience et vos impressions sur les fonctionnalités du produit et les résultats de la version d’essai.
