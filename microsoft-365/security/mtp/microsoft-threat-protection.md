---
title: Microsoft 365 Defender
description: Microsoft 365 Defender est une solution coordonnée de protection contre les menaces conçue pour protéger les périphériques, l’identité, les données et les applications
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
ms.collection:
- M365-security-compliance
- m365initiative-m365-defender
ms.topic: conceptual
ms.openlocfilehash: 573f30dc3d8a43a337a4333dbaf05baf916857fa
ms.sourcegitcommit: 474bd6a86c3692d11fb2c454591c89029ac5bbd5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2020
ms.locfileid: "49357898"
---
# <a name="microsoft-365-defender"></a>Microsoft 365 Defender

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]


**S’applique à :**
- Microsoft 365 Defender

> Vous souhaitez découvrir Microsoft 365 Defender ? Vous pouvez l' [évaluer dans un environnement de laboratoire](https://aka.ms/mtp-trial-lab) ou [exécuter votre projet pilote en production](https://aka.ms/m365d-pilotplaybook).
>

Microsoft 365 Defender est une suite de défense d’entreprise pré-et post-violation de manière native qui coordonne la détection, la prévention, l’enquête et la réponse au-delà des points de terminaison, des identités, de la messagerie et des applications afin de fournir une protection intégrée contre les attaques sophistiquées.

Avec la solution Microsoft 365 Defender intégrée, les professionnels de la sécurité peuvent associer les signaux de menace que chacun de ces produits reçoit et déterminer l’étendue et l’impact complets de la menace ; la manière dont il entre dans l’environnement, ce qu’il est affecté et la façon dont il influe actuellement sur l’organisation. Microsoft 365 Defender effectue une action automatique pour empêcher ou bloquer les boîtes aux lettres affectées, les points de terminaison et les identités des utilisateurs concernés.  


<center><h2>Microsoft 365 Defender services</center></h2>
<table><tr><td><center><b><a href="https://docs.microsoft.com/windows/security/threat-protection/microsoft-defender-atp/microsoft-defender-advanced-threat-protection"><b>Microsoft Defender pour le point de terminaison</b></center></a></td>
<td><center><b><a href="https://docs.microsoft.com/office365/securitycompliance/office-365-atp"><b>Microsoft Defender pour Office 365</b></center></a></td>
<td><center><b><a href="https://docs.microsoft.com/azure-advanced-threat-protection/"><b>Microsoft Defender pour l’identité</b></a></center></td>
<td><center><b><a href="https://docs.microsoft.com/cloud-app-security/"><b>Sécurité des applications Cloud Microsoft</b></a></center></td>
</tr>
</table>
<br>


>[!TIP]
>Consultez ce [Guide interactif Microsoft 365 Defender](https://aka.ms/MTP-Interactive-Guide).


Microsoft 365 Defender suite protège les éléments suivants : 
- Les **points de terminaison avec Microsoft Defender for Endpoint** -Microsoft Defender for Endpoint sont une plateforme de point de terminaison unifiée pour la protection préventive, la détection après effraction, l’enquête automatisée et la réponse. 
- **Email and collaboration with Microsoft Defender for office 365** -Defender for Office 365 protège votre organisation contre les menaces malveillantes posées par les messages électroniques, les liens (URL) et les outils de collaboration. 
- **Identités avec Microsoft Defender for Identity and Azure ad Identity Protection** -Microsoft Defender for Identity utilise des signaux Active Directory pour identifier, détecter et examiner les menaces avancées, les identités compromises et les actions malveillantes dirigées vers votre organisation. 
- **Applications avec Microsoft Cloud App Security** -la sécurité de l’application Cloud Microsoft est une solution complète de la visibilité complète, des contrôles de données renforcés et une protection améliorée contre les menaces pour vos applications Cloud. 

>[!VIDEO https://www.microsoft.com/en-us/videoplayer/embed/RE4Bzww] 

La couche interproduit unique de Microsoft 365 Defender augmente les composants de suite individuels pour :
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


Les fonctionnalités multiproduits de Microsoft 365 Defender sont les suivantes : 
- **Volet unique de l’ensemble des produits en verre** -centré toutes les informations sur les détections, les ressources affectées, les actions automatisées effectuées et les preuves associées dans une file d’attente unique et dans un volet unique dans [Security.Microsoft.com](https://security.microsoft.com). 
- **File d’attente d’incidents combinés** : pour aider les professionnels de la sécurité à se concentrer sur ce qui est essentiel en garantissant une étendue d’attaque complète, les ressources affectées et les actions de correction automatisées sont regroupées et mises en avant de manière opportune. 
- **Réponse automatique aux menaces** les informations sur les menaces critiques sont partagées en temps réel entre les produits Microsoft 365 Defender pour vous aider à arrêter la progression d’une attaque. Par exemple, si un fichier malveillant est détecté sur un point de terminaison protégé par Microsoft Defender pour le point de terminaison, il indiquera à Defender pour Office 365 d’analyser et de supprimer le fichier de tous les messages électroniques. Le fichier sera bloqué sur vue par l’ensemble de la suite de sécurité Microsoft 365.
- **Autoréparation des appareils compromis, des identités des utilisateurs et des boîtes aux lettres** : Microsoft 365 Defender utilise des autoformations et des règles automatiques pour reconvertir les ressources affectées à un état sécurisé. Microsoft 365 Defender exploite les capacités de correction automatique des produits de la suite afin de garantir que tous les biens affectés à un incident sont automatiquement corrigés dès que possible.
- **Menace sur les produits croisés** : les équipes de sécurité peuvent tirer parti de leurs connaissances organisationnelles uniques pour rechercher des signes de compromission en créant leurs propres requêtes personnalisées sur les données brutes collectées par les différents produits de protection. Microsoft 365 Defender offre un accès basé sur les requêtes à 30 jours de signaux bruts historiques et de données d’alerte via le point de terminaison et les données Microsoft Defender pour Office 365. 


## <a name="get-started"></a>Prise en main
Les conditions de licence de Microsoft 365 Defender doivent être remplies pour pouvoir activer le service dans le centre de sécurité Microsoft 365 sur [Security.Microsoft.com](https://security.microsoft.com). Pour plus d’informations, consultez :
- [Conditions de licence](prerequisites.md#licensing-requirements)
- [Activer Microsoft 365 Defender](mtp-enable.md)
