---
title: Fonctionnement de DLP avec le Centre de sécurité & conformité & Exchange’administration
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
localization_priority: Normal
search.appverid:
- MOE150
- MET150
ms.assetid: a7e4342a-a0a1-4b43-b166-3d7eecf5d2fd
description: Découvrez comment DLP dans le Centre de sécurité & conformité fonctionne avec DLP et les règles de flux de messagerie (règles de transport) dans le Centre d Exchange’administration.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 37d1c4a5900fb9a6d42934246cbed6666e0609eb
ms.sourcegitcommit: d08fe0282be75483608e96df4e6986d346e97180
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/12/2021
ms.locfileid: "59182288"
---
# <a name="how-dlp-works-between-the-microsoft-365-compliance-center-and-exchange-admin-center"></a>Fonctionnement de la DLP entre le Centre Microsoft 365 conformité et Exchange’administration centrale

Dans Microsoft 365, vous pouvez créer une stratégie de protection contre la perte de données (DLP) dans deux centres d’administration différents :
  
- Dans le Centre de conformité **Microsoft 365,** vous pouvez créer une stratégie DLP unique pour protéger le contenu dans les appareils SharePoint, OneDrive, Exchange, Teams et désormais les points de terminaison. Nous vous recommandons de créer une stratégie DLP ici. Pour plus d’informations, [voir la référence sur la protection contre la perte de données.](data-loss-prevention-policies.md)
    
- Dans le **Exchange d’administration,** vous pouvez créer une stratégie DLP pour protéger le contenu uniquement dans Exchange. Cette stratégie peut utiliser des Exchange de flux de messagerie (également appelées règles de transport), de sorte qu’elle dispose d’autres options spécifiques à la gestion du courrier électronique. Pour plus d’informations, voir [DLP dans le centre Exchange’administration.](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention)
    
Les polices DLP créées dans ces centres d’administration fonctionnent côte à côte : cette rubrique explique comment.
  
![Pages DLP dans le Centre de sécurité et conformité Exchange centre d’administration.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Fonctionnement de la protection contre la protection contre la protection contre la & dans le Centre de sécurité et conformité avec les règles de flux de messagerie et DLP dans le Centre d’administration Exchange de sécurité

Après avoir créé une stratégie DLP dans le Centre de sécurité & conformité, la stratégie est déployée sur tous les emplacements inclus dans la stratégie. Si la stratégie inclut Exchange Online, la stratégie y est synchronisée et appliquée exactement de la même manière qu’une stratégie DLP créée dans le centre d’administration Exchange. 
  
Si vous avez créé des stratégies DLP dans le Centre d’administration Exchange, ces stratégies continueront à fonctionner côte à côte avec les stratégies de courrier électronique que vous créez dans le Centre de sécurité et conformité &. Toutefois, notez que les règles créées dans Exchange’administration centrale sont prioritaire. Toutes Exchange de flux de messagerie sont traitées en premier, puis les règles DLP du Centre de sécurité & conformité sont traitées.
  
Cela signifie que :
  
- Les messages bloqués par Exchange règles de flux de messagerie ne sont pas analysés par les règles DLP créées dans le Centre de sécurité & conformité.

- Les messages mis en quarantaine par Exchange règles de flux de messagerie ou tout autre filtre exécuté avant la DLP ne seront pas analysés par DLP.
    
- Si une règle de flux de messagerie Exchange modifie un message de manière à ce qu’il corresponde à une stratégie DLP dans le Centre de sécurité & conformité (par exemple, l’ajout d’utilisateurs externes), les règles DLP le détectent et appliquent la stratégie selon les besoins.
    
Notez également que Exchange règles de flux de messagerie qui utilisent l’action « Arrêter le traitement » n’affectent pas le traitement des règles DLP dans le Centre de sécurité & conformité . Elles seront toujours traitées.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Conseils de stratégie dans le Centre de sécurité & conformité et le Centre d’administration Exchange de sécurité

Les conseils de stratégie peuvent fonctionner avec les stratégies DLP et les règles de flux de messagerie créées dans le Centre d’administration Exchange, ou avec les stratégies DLP créées dans le Centre de sécurité & conformité, mais pas les deux. En effet, ces stratégies sont stockées à différents emplacements, mais les conseils de stratégie ne peuvent dessiner qu’à partir d’un seul emplacement.
  
Si vous avez configuré des conseils de stratégie dans le Centre d’administration Exchange, les conseils de stratégie que vous configurez dans le Centre de sécurité & conformité n’apparaissent pas pour les utilisateurs dans Outlook sur le web et Outlook 2013 et ultérieurs tant que vous n’avez pas éteint les conseils dans le Centre d’administration Exchange. Cela garantit que vos règles de flux Exchange de messagerie continueront de fonctionner jusqu’à ce que vous choisissiez de basculer vers le Centre de sécurité & conformité.
  
Notez que bien que les conseils de stratégie ne peuvent dessiner qu’à partir d’un seul emplacement, les notifications par courrier électronique sont toujours envoyées, même si vous utilisez des stratégies DLP dans le Centre de sécurité & conformité et le Centre d’administration Exchange.
