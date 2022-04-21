---
title: 'Étape 3 : déployer la sécurité et la conformité pour les travailleurs hybrides'
f1.keywords:
- NOCSH
author: dansimp
ms.author: dansimp
manager: dansimp
audience: ITPro
ms.topic: article
ms.prod: microsoft-365-enterprise
ms.localizationpriority: high
ms.collection:
- M365-security-compliance
- Strat_O365_Enterprise
- remotework
- m365solution-remotework
- m365solution-scenario
ms.custom: ''
description: Utilisez les services de sécurité et de conformité Microsoft 365 pour protéger vos applications, données et appareils destinés aux travailleurs hybrides.
ms.openlocfilehash: 08771de0f9e833405da308fb645b5fb5c906c543
ms.sourcegitcommit: 52eea2b65c0598ba4a1b930c58b42dbe62cdaadc
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/19/2022
ms.locfileid: "64937782"
---
# <a name="step-3-deploy-security-and-compliance-for-hybrid-workers"></a>Étape 3 : déployer la sécurité et la conformité pour les travailleurs hybrides

Pour les travailleurs hybrides, dont certains ne sont jamais ou que très rarement au bureau, la sécurité et la conformité constituent un élément important de la solution globale. Toutes leurs communications se produisent sur Internet au lieu d’être limitées à un intranet d’organisation.

Vos employés et vous-même pouvez accomplir différentes tâches pour rester productifs tout en réduisant les risques en matière de cyber-sécurité et en respectant les réglementations internes ainsi que les réglementations relatives aux données.

Le travail à distance nécessite les éléments suivants en matière de sécurité et de conformité :

- Accès contrôlé aux applications de productivité utilisées par les travailleurs hybrides, par exemple Microsoft Teams
- Accès contrôlé et protection des données que les travailleurs hybrides créent et utilisent, telles que les conversations ou les fichiers partagés
- Protection des appareils Windows 11 ou 10 contre les programmes malveillants et d’autres types de cyberattaques
- Protection des courriers électroniques, des fichiers et des sites avec un étiquetage cohérent pour les niveaux de confidentialité et de protection
- Prévention des fuites d’informations
- Respect des réglementations régionales relatives aux données

Voici les fonctionnalités de Microsoft 365 qui fournissent des services de sécurité et de conformité aux travailleurs hybrides.

:::image type="content" source="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png" alt-text="Utilisez ces services Microsoft 365 pour maintenir votre sécurité et votre conformité" lightbox="../media/empower-people-to-work-remotely/remote-workers-security-compliance-grid.png":::

## <a name="security"></a>Sécurité

Protégez vos applications et données grâce aux fonctionnalités de sécurité de Microsoft 365.

|Fonctionnalité|Pourquoi en ai-je besoin ?|Licence|
|---|---|---|
|Microsoft Defender pour Office 365|Protégez vos applications et données Microsoft 365 (par exemple, messages électroniques, documents Office et outils de collaboration) contre les attaques. <p> Microsoft Defender pour Office 365 collecte et analyse les signaux de vos applications pour la détection, l’investigation et la correction des risques de sécurité, et protège votre organisation contre les menaces malveillantes posées par les courriers électroniques, les liens (URL) et les outils de collaboration. Il fournit également des outils automatisés d’évaluation et de configuration de la configuration des locataires pour des postures de sécurité standard et strictes.|Microsoft 365 E3 ou E5|
|Protection contre les programmes malveillants|‎Les antivirus Microsoft Defender et Device Guard fournissent une protection contre les programmes malveillants basée sur l’appareil. <p> SharePoint‎ Online analyse automatiquement les chargements de fichiers pour détecter les programmes malveillants connus. <p> Exchange Online Protection‎ (‎EOP‎) sécurise les boîtes aux lettres cloud.|Microsoft 365 E3 ou E5|
|Microsoft Defender pour point de terminaison|Protégez les appareils de votre organisation contre les cyber-menaces et les violations de données. Détectez, examinez et répondez aux menaces avancées.|Microsoft 365 E5|
|Defender for Cloud Apps|Protégez vos services cloud (Microsoft 365 et autres applications SaaS) contre les attaques.|Microsoft 365 E5 licences Defender for Cloud Apps individuelles ou individuelles|
|Azure AD Identity Protection|Automatisez la détection et la correction des risques basés sur l’identité. <p>Créez des stratégies d’accès conditionnel basées sur le risque qui requièrent l’authentification multifacteur (MFA) pour les connexions à risque.|Microsoft 365 E5 ou E3 avec les licences Azure AD Premium P2|
||||

La première étape consiste à apprendre à connaître et à utiliser [Niveau de sécurité Microsoft](/microsoft-365/security/defender/microsoft-secure-score).

Si vous souhaitez en savoir plus, consultez la rubrique [12 premières tâches pour les équipes de sécurité qui prennent en charge le télétravail](../security/top-security-tasks-for-remote-work.md).

Pour plus d’informations sur la sécurité dans Microsoft 365, consultez la [documentation de sécurité Microsoft 365](/microsoft-365/security).

## <a name="compliance"></a>Conformité

Respectez les stratégies internes ou les exigences réglementaires avec ces fonctionnalités de conformité de Microsoft 365.

|Fonctionnalité|Pourquoi en ai-je besoin ?|Licence|
|---|---|---|
|Étiquettes de confidentialité|Classifiez et protégez les données de votre organisation sans entraver la productivité des utilisateurs ni leur capacité à collaborer en plaçant des étiquettes avec différents niveaux de protection sur les messages électroniques, les fichiers et les sites.|Microsoft 365 E3 ou E5|
|Protection contre la perte de données (DLP)|Détectez, signalez et bloquez le partage risqué, accidentel ou inapproprié, tel que le partage de données contenant des informations personnelles, à la fois en interne et en externe.|Microsoft 365 E3 ou E5|
|Contrôle d’application d’accès conditionnel|Empêchez le téléchargement de données sensibles sur les appareils personnels des utilisateurs.|Microsoft 365 E3 ou E5|
|Étiquettes et stratégies de rétention des données|Mettez en place des contrôles de gouvernance des informations, tels que la durée de conservation des données ainsi que des exigences sur le stockage de données personnelles sur les clients, pour vous conformer aux stratégies de votre organisation ou aux réglementations relatives aux données.|Microsoft 365 E3 ou E5|
|Chiffrement des messages Microsoft Purview|Envoyez et recevez entre des personnes à l’intérieur et à l’extérieur de votre organisation des messages électroniques chiffrés qui contiennent des données réglementées, telles que des données personnelles relatives aux clients.|Microsoft 365 E3 ou E5|
|Gestionnaire de conformité|Gérez les activités de conformité réglementaire liées aux services cloud Microsoft avec cet outil d’évaluation des risques basé sur les flux de travail dans le portail d’approbation de services Microsoft.|Microsoft 365 E3 ou E5|
|Gestionnaire de conformité|Obtenez un score global concernant votre configuration de conformité actuelle avec des recommandations pour l’améliorer dans le portail de conformité Microsoft Purview.|Microsoft 365 E3 ou E5|
|Conformité des communications|Détectez, capturez et prenez des actions de correction pour les messages inappropriés au sein de votre organisation.|Microsoft 365 E5 ou Microsoft 365 E3 avec les modules complémentaires de conformité ou de gestion des risques internes|
|Gestion des risques internes|Détectez, examinez et agissez sur des risques malveillants et involontaires au sein de votre organisation. Microsoft 365 peut détecter ces types de risque, même lorsqu’un employé utilise un appareil non géré.|Microsoft 365 E5 ou Microsoft 365 E3 avec les modules complémentaires de conformité ou de gestion des risques internes|
||||

Consulter la rubrique [Tâches rapides pour démarrer avec la conformité Microsoft](../compliance/compliance-quick-tasks.md) pour plus d’informations.

## <a name="results-of-step-3"></a>Résultats de l’étape 3

Pour vos travailleurs hybrides, vous avez implémenté :

- Sécurité
  - Accès contrôlé aux applications et aux données utilisés par les travailleurs hybrides pour communiquer et collaborer
  - Protection contre les programmes malveillants pour les données de service cloud, la messagerie électronique et les appareils Windows 11 ou 10
- Conformité
  - Étiquetage cohérent pour les niveaux de confidentialité et de protection
  - Stratégies pour empêcher la fuite d’informations
  - Respect des réglementations régionales relatives aux données

## <a name="next-step"></a>Étape suivante

[![Étape 4: Gérer vos appareils, PC et autres points de terminaison.](../media/empower-people-to-work-remotely/remote-workers-step-grid-4.png)](empower-people-to-work-remotely-manage-endpoints.md)

Poursuivez avec l’[étape 4](empower-people-to-work-remotely-manage-endpoints.md) pour gérer vos appareils, PC et autres points de terminaison.
