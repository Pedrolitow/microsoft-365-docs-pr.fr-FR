---
title: Microsoft 365 Defender
description: Microsoft 365 Defender est une solution de protection contre les menaces coordonnée conçue pour protéger les appareils, l’identité, les données et les applications
keywords: introduction à MMicrosoft 365 Defender, cybersécurité, menace persistante avancée, sécurité d’entreprise, appareils, appareil, identité, utilisateurs, données, applications, incidents, examen et correction automatisés, recherche avancée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
localization_priority: Normal
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.technology: m365d
ms.openlocfilehash: 1e8b5745e67741535f0c521fc6c6dc1f83868b3c
ms.sourcegitcommit: c2d752718aedf958db6b403cc12b972ed1215c00
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2021
ms.locfileid: "58568791"
---
# <a name="microsoft-365-defender"></a>Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous voulez essayer Microsoft 365 Defender ? Vous pouvez [l’évaluer dans un environnement de laboratoire](m365d-evaluation.md?ocid=cx-docs-MTPtriallab) ou [exécuter votre projet pilote en production](m365d-pilot.md?ocid=cx-evalpilot).
>

Microsoft 365 Defender est une suite de défense d’entreprise pré-et post-violation unifiée qui coordonne en natif la détection, la prévention, les examens et la réponse sur les points de terminaison, les identités, les messages électroniques et les applications pour fournir une protection intégrée contre les attaques sophistiquées.

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent assembler les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace . comment il est entré dans l’environnement, ce qu’il a affecté et comment il a actuellement un impact sur l’organisation. Microsoft 365 Defender prend des mesures automatiques pour empêcher ou arrêter l’attaque et auto-panser les boîtes aux lettres, les points de terminaison et les identités des utilisateurs affectés.  


<center><h2>Microsoft 365 Defender services</center></h2>
<table><tr><td><center><b><a href="/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection"><b>Microsoft Defender pour le point de terminaison</b></center></a></td>
<td><center><b><a href="/office365/securitycompliance/office-365-atp"><b>Microsoft Defender pour Office 365</b></center></a></td>
<td><center><b><a href="/azure-advanced-threat-protection/"><b>Microsoft Defender pour l’identité</b></a></center></td>
<td><center><b><a href="/cloud-app-security/"><b>Microsoft Cloud App Security</b></a></center></td>
</tr>
</table>
<br>

## <a name="microsoft-365-defender-interactive-guide"></a>Microsoft 365 Defender interactif

Dans ce guide interactif, vous allez découvrir comment protéger votre organisation à l’Microsoft 365 Defender. Vous verrez comment les Microsoft 365 Defender peuvent vous aider à détecter les risques de sécurité, à examiner les attaques de votre organisation et à prévenir automatiquement les activités dangereuses.

[Consulter le guide interactif](https://aka.ms/M365Defender-InteractiveGuide)



La suite Microsoft 365 Defender protège : 
- **Points de** terminaison avec Microsoft Defender pour point de terminaison - Microsoft Defender pour point de terminaison est une plateforme de point de terminaison unifiée pour la protection préventive, la détection post-violation, l’examen automatisé et la réponse. 
- **E-mail** et collaboration avec Microsoft Defender pour Office 365 - Defender pour Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. 
- Identités avec Microsoft Defender pour l’identité et **Azure AD Identity Protection** - Microsoft Defender pour l’identité utilise les signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions internes malveillantes dirigées contre votre organisation. 
- **Applications** avec sécurité Microsoft Cloud App : la sécurité de Microsoft Cloud App est une solution saaS complète qui apporte une visibilité approfondie, des contrôles de données forts et une protection renforcée contre les menaces à vos applications cloud. 

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww] 

Microsoft 365 Defender’une couche unique entre produits complète les composants de suite individuels pour :
- Protéger contre les attaques et coordonner les réponses coordonnées dans la suite par le biais du partage de signal et des actions automatisées
- Narratez l’intégralité de l’attaque sur les alertes, les comportements et le contexte des produits pour les équipes de sécurité en joignant les données sur les alertes, les événements suspects et les ressources impactées aux « incidents »
- Automatiser la réponse à la compromission en déclenchant la réparation automatique des biens touchés via une correction automatisée
- Permettre aux équipes de sécurité d’effectuer une recherche détaillée et efficace des menaces sur les points de terminaison et Office données

![Image de la page vue d’ensemble de l’incident.](../../media/overview-incident.png) <br>
Incident entre produits (vue d’ensemble)

![Image de la file d’attente des alertes.](../../media/incident-list.png)<br>
Toutes les alertes associées dans les produits de suite corrélées en un seul incident (affichage des alertes)

![Image de la file d’attente des incidents.](../../media/advanced-hunting.png)<br>
Recherche basée sur une requête sur les données brutes du point de terminaison et du courrier électronique


Microsoft 365 Defender fonctionnalités entre produits sont les suivantes : 
- **Volet** unique produit - Affichage central de toutes les informations relatives aux détections, aux biens touchés, aux actions automatisées prises et aux preuves associées dans une seule file d’attente et un seul volet dans [security.microsoft.com](https://security.microsoft.com). 
- File d’attente **d’incidents combinés** : pour aider les professionnels de la sécurité à se concentrer sur ce qui est critique en garantissant l’étendue d’attaque complète, les ressources impactées et les actions de correction automatisées sont regroupées et mises en avant en temps voulu. 
- **Réponse automatique aux menaces** : les informations sur les menaces critiques sont partagées en temps réel entre les produits Microsoft 365 Defender pour aider à arrêter la progression d’une attaque. Par exemple, si un fichier malveillant est détecté sur un point de terminaison protégé par Microsoft Defender pour endpoint, il demande à Defender pour Office 365 d’analyser et de supprimer le fichier de tous les messages électroniques. Le fichier sera bloqué à la vue par l’ensemble Microsoft 365 suite de sécurité.
- **Auto-réparation** pour les appareils compromis, les identités des utilisateurs et les boîtes aux lettres : Microsoft 365 Defender utilise des actions automatiques et des playbooks optimisés par l’IA pour corriger les biens touchés à un état sécurisé. Microsoft 365 Defender utilise les fonctionnalités de correction automatique des produits de la suite pour s’assurer que tous les biens touchés liés à un incident sont automatiquement corrigés lorsque cela est possible.
- **Recherche de** menaces entre produits : les équipes de sécurité peuvent tirer parti de leurs connaissances organisationnelles uniques pour chercher des signes de compromission en créant leurs propres requêtes personnalisées sur les données brutes collectées par les différents produits de protection. Microsoft 365 Defender fournit un accès basé sur une requête à 30 jours de signaux bruts historiques et de données d’alerte sur le point de terminaison et Microsoft Defender pour Office 365 données. 


## <a name="get-started"></a>Prise en main
Microsoft 365 Defender licences doivent être remplies avant de pouvoir activer le service dans le portail Microsoft 365 Defender à [l’security.microsoft.com](https://security.microsoft.com). Pour plus d’informations, voir :
- [Conditions de licence](prerequisites.md#licensing-requirements)
- [Activer Microsoft 365 Defender](m365d-enable.md)


## <a name="see-also"></a>Voir aussi
- [Déployer des fonctionnalités de protection contre les menaces dans Microsoft 365 E5](/microsoft-365/solutions/deploy-threat-protection)
