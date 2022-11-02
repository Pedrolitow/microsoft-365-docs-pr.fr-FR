---
title: En savoir plus sur les preuves forensiques de gestion des risques internes (préversion)
description: Découvrez les preuves forensiques de gestion des risques internes dans Microsoft Purview. La preuve forensique est un outil d’investigation qui permet d’afficher l’activité des utilisateurs capturés afin de déterminer si les actions de l’utilisateur posent un risque et peuvent entraîner un incident de sécurité.
keywords: Microsoft 365, Microsoft Purview, risque interne, gestion des risques, conformité
ms.localizationpriority: medium
ms.service: O365-seccomp
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection: m365-security-compliance
ms.openlocfilehash: 5bc3f1863fa2e49bc6cc98aca1c9be38b07ec582
ms.sourcegitcommit: ab45f2963e0635ff2cb9670f6f7b4c784f6a250e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68815218"
---
# <a name="learn-about-insider-risk-management-forensic-evidence-preview"></a>En savoir plus sur les preuves forensiques de gestion des risques internes (préversion)

>[!IMPORTANT]
>Gestion des risques internes Microsoft Purview met en corrélation différents signaux pour identifier les risques internes potentiels malveillants ou par inadvertance, tels que le vol d’adresses IP, les fuites de données et les violations de sécurité. La gestion des risques internes permet aux clients de créer des stratégies pour gérer la sécurité et la conformité. Conçu avec la confidentialité par défaut, les utilisateurs sont pseudonymisés par défaut, et des contrôles d’accès en fonction du rôle et des journaux d’audit sont en place pour garantir la confidentialité au niveau de l’utilisateur.

Disposer d’un contexte visuel est essentiel pour les équipes de sécurité pendant les enquêtes judiciaires afin d’obtenir de meilleures informations sur les activités potentiellement risquées des utilisateurs liées à la sécurité. Avec des déclencheurs d’événements personnalisables et des contrôles intégrés de protection de la confidentialité des utilisateurs, les preuves forensiques permettent la capture d’activités visuelles personnalisables sur les appareils pour aider votre organisation à mieux atténuer, comprendre et répondre aux risques potentiels liés aux données, comme l’exfiltration de données sensibles non autorisées. Vous définissez les stratégies appropriées pour votre organisation, notamment les événements à risque qui sont la priorité la plus élevée pour la capture des preuves d’investigation, les données les plus sensibles et si les utilisateurs sont avertis quand la capture d’investigation est activée. La capture des preuves forensiques est désactivée par défaut et la création de stratégie nécessite une double autorisation.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="feature-capabilities"></a>Fonctionnalités des fonctionnalités

- **La capture visuelle** permet aux organisations de capturer des extraits des principales activités des utilisateurs liées à la sécurité, ce qui permet une visibilité plus sécurisée ou conforme et de répondre aux besoins de l’organisation.
- **Protection de la confidentialité des utilisateurs** via plusieurs niveaux d’approbation pour l’activation de la fonctionnalité de capture.
- **Les déclencheurs personnalisables et les options de capture signifient** que les équipes de sécurité peuvent configurer des preuves forensiques pour répondre à leurs besoins, *qu’il s’agisse d’incidents (par exemple, capture 5 minutes avant et 10 minutes après le téléchargement de « SecretResearchPlans.docx » par un utilisateur*) ou en fonction des besoins de capture continue.
- **Le ciblage de stratégie centré sur l’utilisateur** signifie que les équipes de sécurité et de conformité peuvent se concentrer sur l’activité par utilisateur, et non sur l’appareil, pour obtenir de meilleures informations contextuelles.
- **Les contrôles d’accès en fonction du rôle (RBAC) forts** signifient que la possibilité de configurer et d’examiner des clips d’investigation est étroitement contrôlée et disponible uniquement pour les personnes de l’organisation disposant des autorisations appropriées.
- **Intégration approfondie avec les fonctionnalités actuelles de gestion des risques internes**, ce qui facilite l’intégration et les flux de travail plus familiers pour les administrateurs de gestion des risques internes et une approche de plateforme unique approuvée.

## <a name="device-and-configuration-requirements"></a>Configuration requise pour l’appareil et la configuration

Les tableaux suivants incluent les exigences minimales prises en charge pour l’utilisation des preuves forensiques de gestion des risques internes.

### <a name="supported-platforms"></a>Plateformes prises en charge

|**Système d’exploitation**|**RÉFÉRENCE SKU**|**Processeur**|
|:----------|:-------|:-------------------|
| Windows 10 | Entreprise | 64 bits (Intel ou AMD) |
| Windows 11 | Entreprise | 64 bits (Intel ou AMD) |

### <a name="physical-devices"></a>Appareils physiques

|**Matériel**|**Configuration minimale**|
|:----------|:-------------------------------|
| Mémoire RAM | Minimum de 8 Go (au moins 2 Go doivent être disponibles pour l’utilisation du client |
| Processeur de processeur | Intel i5 ou version ultérieure et AMD Ryzen 5 ou version ultérieure |
| Carte graphique | Compatible avec DirectX 11 ou version ultérieure, avec un pilote WDDM 1.0 ou version ultérieure (actuellement, seules les cartes graphiques intégrées sont prises en charge)|
| Espace disque | Minimum de 10 Go de stockage sur disque |
| Afficher | Résolution d’écran minimale de 1920 x 1080 | 

### <a name="hyper-v-and-virtual-machines"></a>Hyper-V et machines virtuelles

|**Matériel**|**Configuration minimale**|
|:----------|:-------------------------------|
| Mémoire RAM | Minimum de 16 Go (au moins 2 Go doivent être disponibles pour l’utilisation du client) |
| Processeur de processeur | Au moins deux processeurs virtuels et au moins quatre cœurs pour chaque processeur virtuel |
| Espace disque | Minimum de 10 Go de stockage sur disque |
| Afficher | Résolution d’écran minimale de 1920 x 1080 | 

> [!IMPORTANT]
> Si la configuration minimale requise n’est pas remplie, les utilisateurs sont susceptibles de rencontrer des problèmes de client Microsoft Purview et la qualité des enregistrements d’investigation peut ne pas être fiable.

## <a name="capturing-options"></a>Options de capture

[Le déclenchement d’événements, d’indicateurs globaux et d’indicateurs de stratégie](/microsoft-365/compliance/insider-risk-management-settings#indicators) jouent un rôle important dans toutes les stratégies de gestion des risques internes, y compris les stratégies de preuve d’investigation. Les événements de déclenchement sont des actions de l’utilisateur qui déterminent si les utilisateurs sont placés dans l’étendue de l’évaluation dans les stratégies de gestion des risques internes. Les indicateurs de paramètres globaux sont utilisés pour déterminer les activités collectées par la gestion des risques internes. Les indicateurs de stratégie sont utilisés pour déterminer un score de risque pour un utilisateur dans l’étendue.

Selon la façon dont votre organisation décide de configurer les preuves d’investigation, il existe deux options de capture :

- **Activités spécifiques** : cette option de stratégie capture l’activité uniquement lorsqu’un événement déclencheur a placé un utilisateur approuvé dans l’étendue de la stratégie de preuve d’investigation et lorsque les conditions d’un indicateur de stratégie sont détectées pour l’utilisateur. Par exemple, un utilisateur approuvé pour la capture de preuves forensiques est intégré à la stratégie de preuve forensique et l’utilisateur copie les données vers des services de stockage cloud personnels ou des appareils de stockage portables. La capture est limitée uniquement à la période configurée lorsque l’utilisateur copie les données vers le service de stockage cloud personnel ou l’appareil de stockage portable. Les captures de cette option peuvent être examinées sous l’onglet **Preuves forensiques (préversion)** du tableau de bord **Alertes** .
- **Toutes les activités** : cette option de stratégie capture toute activité effectuée par les utilisateurs. Cela inclut le déplacement de la souris, les séquences de touches et toutes les activités définies par les indicateurs de risque interne. Par exemple, votre organisation a un besoin urgent de capturer des activités pour un utilisateur approuvé qui est activement impliqué dans des activités potentiellement risquées susceptibles d’entraîner un incident de sécurité. Les indicateurs de stratégie n’ont peut-être pas atteint le seuil pour qu’une alerte soit générée par la stratégie et l’activité potentiellement risquée peut ne pas être documentée. L’aide à la capture continue empêche l’activité potentiellement risquée d’être manquée ou de ne pas être détectée. Les captures de cette option seront disponibles pour révision sous l’onglet **Preuves d’investigation (préversion)** du tableau de bord **Rapports d’activité utilisateur (préversion).**

>[!IMPORTANT]
>Les clips de preuve d’investigation sont supprimés 120 jours après leur capture ou à la fin de la période de préversion, selon la date la plus précoce. Vous pouvez télécharger ou transférer des extraits de preuve d’investigation avant qu’ils ne soient supprimés.

## <a name="workflow"></a>Flux de travail

Le flux de travail global pour la détection, l’examen et la correction des alertes qui contiennent la capture de clip suit les [mêmes étapes de base](/microsoft-365/compliance/insider-risk-management#workflow) que les autres stratégies de gestion des risques internes. Toutefois, il existe des différences notables pour les preuves d’investigation lorsqu’elles sont configurées dans votre organisation :

- **Les utilisateurs soumis à la capture doivent avoir des demandes et des approbations de capture explicites** : il s’agit d’un processus supplémentaire non inclus dans le cadre de la configuration d’autres stratégies de gestion des risques internes. Les utilisateurs affectés aux groupes de rôles *Gestion des risques internes* ou *Administrateurs de gestion des risques internes* doivent envoyer une demande aux utilisateurs affectés au groupe de rôles *Approbateurs de gestion des risques internes* avant qu’un utilisateur de votre organisation ne soit éligible aux options de capture de clip. Par exemple, cette exigence permet de prendre en charge les scénarios organisationnels dans lesquels vos administrateurs de gestion des risques internes doivent obtenir l’approbation explicite de votre personnel juridique ou des ressources humaines désigné avant que la capture pour n’importe quel utilisateur soit activée.
- **Les appareils doivent être intégrés et le client Microsoft Purview doit être installé** : avant que des preuves d’investigation puissent collecter et stocker des clips capturés pour les utilisateurs éligibles, leurs appareils doivent être intégrés au portail de conformité Microsoft Purview. En outre, le client Microsoft Purview doit être installé sur chaque appareil. Ces prérequis permettent la prise en charge de la capture d’appareils en ligne et hors connexion.

## <a name="ready-to-get-started"></a>Vous êtes prêt ?

- Consultez [Prise en main des preuves forensiques de gestion des risques internes](/microsoft-365/compliance/insider-risk-management-forensic-evidence-configure) pour obtenir des instructions détaillées sur la configuration de la capture des preuves forensiques dans votre organisation.
- Consultez [Prise en main de la gestion des risques internes](/microsoft-365/compliance/insider-risk-management-configure) pour configurer les prérequis, créer des stratégies et commencer à recevoir des alertes.
