---
title: 'Étape 4 : Planifier des modifications d’adresse URL et d’adresse IP'
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 03/05/2018
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Strat_O365_Enterprise
ms.custom: ''
description: ''
ms.openlocfilehash: dacd2ad83bdeb106ae398e8223f457c66a12b598
ms.sourcegitcommit: 66bb5af851947078872a4d31d3246e69f7dd42bb
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/15/2019
ms.locfileid: "34073224"
---
# <a name="step-4-plan-for-url-and-ip-address-changes"></a>Étape 4 : Planifier des modifications d’adresse URL et d’adresse IP

*Cette étape est facultative et s’applique aux versions E3 et E5 de Microsoft 365 Entreprise*

![](./media/deploy-foundation-infrastructure/networking_icon-small.png)

>[!Note]
>Cette étape requiert l’[Étape 3](networking-configure-proxies-firewalls.md). Si vous n’avez pas suivi l’Étape 3, vous pouvez passer à l’[Étape 5](networking-optimize-tcp-performance.md).
>

Les URL et adresses IP utilisées par le réseau Microsoft 365 général changent au fil du temps, donc il est important de planifier des mises à jour de ces points de terminaison. Par exemple, vous devrez peut-être reconfigurer vos appareils de périmètre de sécurité avec les éléments suivants :

- de nouvelles URL pour les nouveaux services qui nécessiteront un traitement facile ;
- des URL supprimées pour les services qui ne sont plus disponibles ;
- de nouvelles plages d’adresses IP pour les nouveaux emplacements réseau Microsoft et serveurs sur Internet ; 
- des modifications des plages d’adresses IP pour les différents services.

Pour plus d’informations sur l’établissement d’un plan d’implémentation pour les modifications des points de terminaison, qui inclut les notifications de ces modifications, reportez-vous aux rubriques [Gestion des points de terminaison Office 365 - Intégration](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a?ui=en-US#ID0EABAAA=2._Proxies&ID0EAEAAA=3._Integration) et [Gestion des points de terminaison Office 365 - Proxys](https://support.office.com/article/Managing-Office-365-endpoints-99cab9d4-ef59-4207-9f2b-3728eb46bf9a#ID0EABAAA=2._Proxies&ID0EAEAAA=2._Proxies).

Comme point de vérification intermédiaire, vous pouvez consultez les [critères de sortie](networking-exit-criteria.md#crit-networking-step4) pour cette étape.

## <a name="next-step"></a>Étape suivante

|||
|:-------|:-----|
|![](./media/stepnumbers/Step5.png)|[Optimiser les performances du service Office 365 et du client](networking-optimize-tcp-performance.md)|
