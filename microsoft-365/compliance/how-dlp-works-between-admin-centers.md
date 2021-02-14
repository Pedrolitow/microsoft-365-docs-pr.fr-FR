---
title: Fonctionnement de DLP avec le Centre de sécurité & conformité & centre d’administration Exchange
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 04/19/2019
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
description: Découvrez comment DLP dans le Centre de sécurité & conformité fonctionne avec DLP et les règles de flux de messagerie (règles de transport) dans le Centre d’administration Exchange.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 05e3c6342ab6d57c1f22de96e64a01df5fd15131
ms.sourcegitcommit: a45cf8b887587a1810caf9afa354638e68ec5243
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/05/2020
ms.locfileid: "44036195"
---
# <a name="how-dlp-works-between-the-security--compliance-center-and-exchange-admin-center"></a>Fonctionnement du DLP entre le Centre de sécurité et conformité et le Centre d’administration Exchange

Dans Office 365, vous pouvez créer une stratégie de protection contre la perte de données (DLP) dans deux centres d’administration différents :
  
- Dans le **Centre de sécurité &** conformité, vous pouvez créer une stratégie DLP unique pour protéger le contenu dans SharePoint, OneDrive, Exchange et désormais Microsoft Teams. Dans la mesure du possible, nous vous recommandons de créer une stratégie DLP ici. Pour plus d’informations, voir [DLP dans le Centre de sécurité & conformité.](data-loss-prevention-policies.md)
    
- Dans le **Centre d’administration Exchange,** vous pouvez créer une stratégie DLP pour protéger le contenu uniquement dans Exchange. Cette stratégie peut utiliser des règles de flux de messagerie Exchange (également appelées règles de transport), de sorte qu’elle dispose d’autres options spécifiques à la gestion du courrier électronique. Pour plus d’informations, voir [DLP dans le Centre d’administration Exchange.](https://go.microsoft.com/fwlink/?linkid=852311)
    
Les polices DLP créées dans ces centres d’administration fonctionnent côte à côte : cette rubrique explique comment.
  
![Pages DLP dans le Centre de sécurité et conformité et le Centre d’administration Exchange](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Fonctionnement de la protection contre la protection contre la protection contre la & dans le Centre de sécurité et conformité avec les règles de flux de messagerie et DLP dans le Centre d’administration Exchange

Après avoir créé une stratégie DLP dans le Centre de sécurité & conformité, la stratégie est déployée sur tous les emplacements inclus dans la stratégie. Si la stratégie inclut Exchange Online, la stratégie y est synchronisée et appliquée exactement de la même manière qu’une stratégie DLP créée dans le Centre d’administration Exchange. 
  
Si vous avez créé des stratégies DLP dans le Centre d’administration Exchange, ces stratégies continueront à fonctionner côte à côte avec les stratégies de courrier électronique que vous créez dans le Centre de sécurité & conformité. Toutefois, notez que les règles créées dans le Centre d’administration Exchange sont prioritaire. Toutes les règles de flux de messagerie Exchange sont traitées en premier, puis les règles DLP du Centre de sécurité & conformité sont traitées.
  
Cela signifie que :
  
- Les messages bloqués par les règles de flux de messagerie Exchange ne seront pas analysés par les règles DLP créées dans le Centre de sécurité & conformité.
    
- Si une règle de flux de messagerie Exchange modifie un message d’une manière qui le fait correspondre à une stratégie DLP dans le Centre de sécurité & conformité (par exemple, l’ajout d’utilisateurs externes), les règles DLP le détectent et appliquent la stratégie selon les besoins.
    
Notez également que les règles de flux de messagerie Exchange qui utilisent l’action « Arrêter le traitement » n’affectent pas le traitement des règles DLP dans le Centre de sécurité & conformité . Elles seront toujours traitées.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Conseils de stratégie dans le Centre de sécurité & conformité et le Centre d’administration Exchange

Les conseils de stratégie peuvent fonctionner avec les stratégies DLP et les règles de flux de messagerie créées dans le Centre d’administration Exchange, ou avec les stratégies DLP créées dans le Centre de sécurité & conformité, mais pas les deux. En effet, ces stratégies sont stockées à différents emplacements, mais les conseils de stratégie ne peuvent dessiner qu’à partir d’un seul emplacement.
  
Si vous avez configuré des conseils de stratégie dans le Centre d’administration Exchange, les conseils de stratégie que vous configurez dans le Centre de sécurité & conformité n’apparaîtront pas pour les utilisateurs dans Outlook sur le web et Outlook 2013 et les ultérieures tant que vous n’avez pas éteint les conseils dans le Centre d’administration Exchange. Cela garantit que vos règles de flux de messagerie Exchange actuelles continueront de fonctionner jusqu’à ce que vous choisissiez de basculer vers le Centre de sécurité & conformité.
  
Notez que bien que les conseils de stratégie ne peuvent dessiner qu’à partir d’un seul emplacement, les notifications par courrier électronique sont toujours envoyées, même si vous utilisez des stratégies DLP dans le Centre de sécurité & conformité et le Centre d’administration Exchange.
  

