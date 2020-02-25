---
title: Protection Microsoft contre les menaces
description: Microsoft Threat Protection est une solution coordonnée de protection contre les menaces conçue pour protéger les périphériques, l’identité, les données et les applications
keywords: Introduction à Microsoft Threat Protection, Cyber Security, Advanced persistent Threat, Enterprise Security, Devices, Device, Identity, Users, Data, applications, incidents, Automated Investigation and Remediation, recherche avancée
search.product: eADQiWindows 10XVcnh
search.appverid: met150
ms.prod: microsoft-365-enterprise
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: M365-security-compliance
ms.topic: conceptual
ms.openlocfilehash: ef68143d185b6b716b8b5c8213b1e4f3ea1a5abd
ms.sourcegitcommit: 74bf600424d0cb7b9d16b4f391aeda7875058be1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42235073"
---
# <a name="microsoft-threat-protection"></a>Protection Microsoft contre les menaces

**S’applique à :**
- Protection Microsoft contre les menaces



La protection de Microsoft contre les menaces est une suite de défense d’entreprise pré-et post-violation unifiée qui s’intègre de manière native sur les points de terminaison, les identités, les messages électroniques et les applications pour détecter, prévenir, examiner et répondre automatiquement aux attaques sophistiquées.  

Avec la solution de protection Microsoft contre les menaces intégrée, les professionnels de la sécurité peuvent combiner les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace ; la manière dont il entre dans l’environnement, ce qu’il est affecté et la façon dont il influe actuellement sur l’organisation. Microsoft Threat Protection effectue une action automatique pour empêcher ou bloquer les boîtes aux lettres, les points de terminaison et les identités utilisateur affectés autoréparation.  


La suite Microsoft Threat Protection protège les éléments suivants : 
- **Points de terminaison avec Microsoft Defender ATP** -Microsoft Defender ATP est une plateforme de point de terminaison unifiée pour la protection préventive, la détection après effraction, l’enquête automatisée et la réponse. 
- La **messagerie et la collaboration avec office 365 ATP** -Office 365 ATP protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. 
- Les **identités avec Azure ATP et Azure ad Identity Protection** -Azure ATP utilisent des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation. 
- **Applications avec Microsoft Cloud App Security** -la sécurité de l’application Cloud Microsoft est une solution complète de la visibilité complète, des contrôles de données renforcés et une protection améliorée contre les menaces pour vos applications Cloud. 

La couche de produit unique de protection contre les menaces Microsoft renforce les composants individuels de la suite :
- Aider à se protéger contre les attaques et coordonner les réponses de la suite via le partage de signaux et les actions automatisées
- Narration de l’histoire complète de l’attaque entre les alertes de produits, les comportements et le contexte des équipes de sécurité en joignant des données sur des alertes, des événements suspects et des ressources affectées à « incidents »
- Automatiser la réponse à une compromission en déclenchant l’auto-réparation des ressources affectées via la correction automatisée
- Permettre aux équipes de sécurité d’effectuer une mise à l’échelle des menaces d’un point de terminaison à l’autres

![Image de la page de présentation de l’incident](../../media/overview-incident.png) <br>
Incident entre produits (vue d’ensemble)

![Image de la file d’attente des alertes](../../media/incident-list.png)<br>
Toutes les alertes associées dans les produits de la suite corrélées en un seul incident (affichage alertes)

![Image de la file d’attente des incidents](../../media/advanced-hunting.png)<br>
Recherche basée sur les requêtes sur les données brutes de messagerie et de point de terminaison


Les fonctionnalités interproduits de la protection contre les menaces Microsoft sont les suivantes : 
- **Volet unique de l’ensemble des produits en verre** -centré toutes les informations sur les détections, les ressources affectées, les actions automatisées effectuées et les preuves associées dans une file d’attente unique et dans un volet unique dans [Security.Microsoft.com](https://security.microsoft.com). 
- **File d’attente d’incidents combinés** : pour aider les professionnels de la sécurité à se concentrer sur ce qui est essentiel en garantissant une étendue d’attaque complète, les ressources affectées et les actions de correction automatisées sont regroupées et mises en avant de manière opportune. 
- **Réponse automatique aux menaces** les informations sur les menaces critiques sont partagées en temps réel entre les produits de protection contre les menaces Microsoft pour arrêter la progression d’une attaque. Par exemple, si un fichier malveillant est détecté sur un point de terminaison protégé par Microsoft Defender ATP, il indiquera à Office 365 ATP d’analyser et de supprimer le fichier de tous les messages électroniques. Le fichier sera bloqué sur vue par l’ensemble de la suite de sécurité Microsoft 365.
- **Autoréparation des appareils compromis, des identités des utilisateurs et des boîtes aux lettres** : Microsoft Threat Protection utilise des autoformations et des règles automatiques pour reconvertir les ressources affectées à un état sécurisé. La protection contre les menaces Microsoft exploite les capacités de correction automatique des produits suite pour garantir que tous les biens affectés à un incident sont automatiquement corrigés dès que possible.
- **Menace sur les produits croisés** : les équipes de sécurité peuvent tirer parti de leurs connaissances organisationnelles uniques pour rechercher des signes de compromission en créant leurs propres requêtes personnalisées sur les données brutes collectées par les différents produits de protection. Microsoft Threat Protection offre un accès basé sur les requêtes aux 30 jours de signaux bruts et de données d’alerte sur les données de point de terminaison et Office 365 ATP. 

<center><h2>Services de protection contre les menaces Microsoft</center></h2>
<table><tr><td><center><b><a href="https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection"><b>Protection avancée contre les menaces Microsoft Defender</b></center></a></td>
<td><center><b><a href="https://docs.microsoft.com/office365/securitycompliance/office-365-atp"><b>Office 365 protection avancée contre les menaces</b></center></a></td>
<td><center><b><a href="https://docs.microsoft.com/azure-advanced-threat-protection/"><b>Azure protection avancée contre les menaces</b></a></center></td>
<td><center><b><a href="https://docs.microsoft.com/cloud-app-security/"><b>Sécurité des applications Cloud Microsoft</b></a></center></td>
</tr>
</table>
<br>


## <a name="get-started"></a>Prise en main
Les clients disposant d’une licence Microsoft 365 E5 ou équivalente peuvent utiliser la Protection Microsoft contre les menaces. Pour commencer, activez le service dans le centre de sécurité Microsoft 365 sur [Security.Microsoft.com](https://security.microsoft.com). Pour plus d’informations, consultez :
- [Conditions de licence](prerequisites.md#licensing-requirements)
- [Activer la Protection Microsoft contre les menaces](mtp-enable.md)
