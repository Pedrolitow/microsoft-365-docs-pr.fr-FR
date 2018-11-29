---
title: 'Étape 4 : configurer le trafic de contournement'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 10/31/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
ms.custom: ''
description: Analysez et configurez des navigateurs web et des équipements de périmètre pour le trafic de contournement vers des emplacements Office 365 approuvés.
ms.openlocfilehash: f52921fdc0a5329e3fffae687855a653f7026df6
ms.sourcegitcommit: eb1a77e4cc4e8f564a1c78d2ef53d7245fe4517a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/28/2018
ms.locfileid: "26867236"
---
# <a name="step-4-configure-traffic-bypass"></a>Étape 4 : configurer le trafic de contournement

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/networking_icon-small.png)

Étant donné que le trafic Internet général peut être risqué, les réseaux d’organisation appliquent généralement la sécurité avec des équipements de périmètre tels que des serveurs proxy, le SSL Break and Inspect, des appareils d’inspection des paquets et des systèmes de protection contre la perte de données. Pour en savoir plus sur certains problèmes avec les périphériques d’interception réseau, reportez-vous à l’article relatif à l’utilisation de périphériques réseau tiers ou de solutions sur le trafic Office 365.

Toutefois, les noms de domaine DNS et les adresses IP utilisées par les services cloud Microsoft 365 sont connus. Par ailleurs, le trafic et les services eux-mêmes sont protégés avec de nombreuses fonctionnalités de sécurité. Étant donné que cette protection et cette sécurité sont déjà en place, vos équipements de périmètre n’ont pas besoin de les dupliquer. Les destinations intermédiaires et le traitement de la sécurité dupliqué pour le trafic Microsoft 365 peuvent réduire les performances de façon considérable.

La première chose à faire lorsque vous éliminez les destinations intermédiaires et le traitement de la sécurité dupliqué consiste à identifier le trafic Microsoft 365. Microsoft a défini les types de noms de domaine DNS et les plages d’adresses IP suivants, appelés points de terminaison :

- Optimiser : obligatoires pour la connectivité à tous les services Office 365 et représentent plus de 75 % de la bande passante, des connexions et du volume de données de Microsoft 365. Ces points de terminaison représentent les scénarios de Microsoft 365 les plus sensibles aux performances, à la latence et à la disponibilité du réseau.
- Autoriser : obligatoires pour la connectivité à des services et fonctionnalités Microsoft 365 spécifiques, mais ne sont pas sensibles aux performances et à la latence du réseau comme ceux de la catégorie Optimiser.
 - Par défaut : représentent des services et des dépendances Microsoft 365 qui n’exigent aucune optimisation. Vous pouvez considérer les points de terminaison de la catégorie Par défaut comme du trafic Internet normal.

Vous pouvez trouver les noms de domaine DNS et les plages d’adresses IP sur la page [https://aka.ms/o365endpoints](https://aka.ms/o365endpoints).

Microsoft vous recommande les points suivants :

- Utiliser des scripts PAC (Proxy Automatic Configuration) sur les navigateurs Internet de vos ordinateurs locaux pour contourner vos serveurs proxy pour les noms de domaine DNS des services cloud Microsoft 365. Pour le dernier script PAC de Microsoft 365, reportez-vous au script PowerShell Get-Pacfile.
- Analyser vos équipements de périmètre pour déterminer le traitement dupliqué, puis les configurer pour transférer le trafic vers les points de terminaison Optimiser et Autoriser sans traitement. Ceci s’appelle le trafic de contournement. 
- 
Les équipements de périmètre incluent les pare-feux, le SSL Break and Inspect, les appareils d’inspection des paquets et les systèmes de protection contre la perte de données. Pour configurer et mettre à jour les configurations des équipements de périmètre, vous pouvez utiliser un script ou un appel REST pour consommer une liste de points de terminaison structurée à partir du service web des points de terminaison Office 365. Pour plus d’informations, reportez-vous à l’article [Service web d’URL et d’adresse IP Office 365](https://docs.microsoft.com/office365/enterprise/office-365-ip-web-service).

Vous ne faites que contourner le traitement de sécurité réseau et de proxy normal pour le trafic vers les points de terminaison des catégories Optimiser et Autoriser de Microsoft 365. Tout autre trafic Internet général sera en proxy et soumis au traitement de sécurité de votre réseau existant.


Comme point de vérification intermédiaire, vous pouvez consulter les [critères de sortie](networking-exit-criteria.md#crit-networking-step4) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step5.png)|[Optimiser les performances du service Office 365 et du client](networking-optimize-tcp-performance.md) |



