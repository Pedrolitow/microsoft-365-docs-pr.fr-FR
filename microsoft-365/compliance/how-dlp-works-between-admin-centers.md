---
title: Fonctionnement de DLP avec le Centre de sécurité & conformité & Exchange centre d’administration
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
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.assetid: a7e4342a-a0a1-4b43-b166-3d7eecf5d2fd
description: Découvrez comment DLP dans le Centre de sécurité & conformité fonctionne avec DLP et les règles de flux de messagerie (règles de transport) dans le centre d’administration Exchange.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: 0c5c6288ed9e3c1f536e7a221a270bad9663cf6b
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753405"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>Fonctionnement de DLP entre le Centre de conformité et le centre d’administration Exchange

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Dans Microsoft Purview, vous pouvez créer une stratégie de protection contre la perte de données (DLP) dans deux centres d’administration différents :
  
- Dans le **portail de conformité Microsoft Purview**, vous pouvez créer une stratégie DLP unique pour protéger le contenu dans SharePoint, OneDrive, Exchange, Teams et maintenant les appareils de point de terminaison. Nous vous recommandons de créer une stratégie DLP ici. Pour plus d’informations, consultez la [référence sur la protection contre la perte de données](data-loss-prevention-policies.md).
    
- Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>, vous pouvez créer une stratégie DLP pour protéger le contenu uniquement dans Exchange. Cette stratégie peut utiliser Exchange règles de flux de messagerie (également appelées règles de transport), de sorte qu’elle a plus d’options spécifiques à la gestion des e-mails. Pour plus d’informations, consultez [DLP dans le centre d’administration Exchange](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
Les stratégies DLP créées dans ces centres d’administration fonctionnent côte à côte : cet article explique comment procéder.
  
![Pages DLP dans le Centre de sécurité et de conformité et Exchange centre d’administration.](../media/d3eaa7e7-3b16-457b-bd9c-26707f7b584f.png)
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Fonctionnement de DLP dans le Centre de sécurité & conformité avec les règles de flux de messagerie et DLP dans le centre d’administration Exchange

Après avoir créé une stratégie DLP dans le Centre de sécurité & conformité, la stratégie est déployée sur tous les emplacements inclus dans la stratégie. Si la stratégie inclut Exchange Online, la stratégie est synchronisée et appliquée exactement de la même façon qu’une stratégie DLP créée dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>. 
  
Si vous avez créé des stratégies DLP dans le centre d’administration Exchange, ces stratégies continueront de fonctionner côte à côte avec les stratégies de courrier que vous créez dans le Centre de sécurité & conformité. Toutefois, notez que les règles créées dans le centre d’administration Exchange sont prioritaires. Toutes les règles de flux de courrier Exchange sont traitées en premier, puis les règles DLP du Centre de sécurité & conformité sont traitées.
  
Cela signifie :
  
- Les messages bloqués par Exchange règles de flux de courrier ne sont pas analysés par les règles DLP créées dans le Centre de sécurité & conformité.
- Les messages mis en quarantaine par Exchange règles de flux de messagerie ou tout autre filtre s’exécutent avant que DLP ne soit analysé par DLP. 
- Si une règle de flux de messagerie Exchange modifie un message d’une manière qui l’amène à correspondre à une stratégie DLP dans le Centre de sécurité & conformité, par exemple l’ajout d’utilisateurs externes, les règles DLP le détectent et appliquent la stratégie en fonction des besoins.
    
Notez également que Exchange règles de flux de messagerie qui utilisent l’action « Arrêter le traitement » n’affectent pas le traitement des règles DLP dans le Centre de sécurité & conformité . Elles seront toujours traitées.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Conseils de stratégie dans le Centre de sécurité & conformité par rapport au Centre d’administration Exchange

Les conseils de stratégie peuvent fonctionner avec des stratégies DLP et des règles de flux de messagerie créées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">centre d’administration Exchange</a>, ou avec des stratégies DLP créées dans le Centre de sécurité & conformité, mais pas les deux. En fait, ces stratégies sont stockées à différents emplacements, mais les conseils de stratégie ne peuvent être utilisés qu’à partir d’un emplacement unique.
  
Si vous avez configuré des conseils de stratégie dans le centre d’administration Exchange, les conseils de stratégie que vous configurez dans le Centre de sécurité & conformité n’apparaîtront pas aux utilisateurs dans Outlook sur le web et Outlook 2013 et versions ultérieures jusqu’à ce que vous désactiviez les conseils dans le centre d’administration Exchange. Cela garantit que vos règles de flux de courrier Exchange actuelles continueront de fonctionner jusqu’à ce que vous choisissiez de basculer vers le Centre de sécurité & conformité.
  
>[!Note]
>Bien que les conseils de stratégie ne puissent être utilisés qu’à partir d’un seul emplacement, les notifications par e-mail sont toujours envoyées, même si vous utilisez des stratégies DLP à la fois dans le Centre de sécurité & conformité et dans le centre d’administration Exchange.
