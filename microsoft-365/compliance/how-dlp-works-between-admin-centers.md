---
title: Fonctionnement de la protection contre la perte de données avec le Centre de sécurité & conformité & centre d’administration Exchange
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
description: Découvrez comment DLP dans le Centre de sécurité & conformité fonctionne avec DLP et les règles de flux de messagerie (règles de transport) dans le Centre d’administration Exchange.
ms.custom:
- seo-marvel-apr2020
- admindeeplinkEXCHANGE
ms.openlocfilehash: fa77bf84ff8ef2b4f194f45b9a29b49f6b662a70
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66641403"
---
# <a name="how-dlp-works-between-the-compliance-center-and-exchange-admin-center"></a>Fonctionnement de DLP entre le Centre de conformité et le Centre d’administration Exchange

Dans Microsoft Purview, vous pouvez créer une stratégie de protection contre la perte de données (DLP) dans deux centres d’administration différents :
  
- Dans le **portail de conformité Microsoft Purview**, vous pouvez créer une stratégie DLP unique pour protéger le contenu dans SharePoint, OneDrive, Exchange, Teams et maintenant les appareils de point de terminaison. Nous vous recommandons de créer une stratégie DLP ici. Pour plus d’informations, consultez la [référence sur la protection contre la perte de données](data-loss-prevention-policies.md).
    
- Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, vous pouvez créer une stratégie DLP pour protéger le contenu uniquement dans Exchange. Cette stratégie peut utiliser des règles de flux de messagerie Exchange (également appelées règles de transport), de sorte qu’elle a plus d’options spécifiques à la gestion des e-mails. Pour plus d’informations, consultez [DLP dans le Centre d’administration Exchange](/exchange/security-and-compliance/data-loss-prevention/data-loss-prevention).
    
Les stratégies DLP créées dans ces centres d’administration fonctionnent côte à côte : cet article explique comment procéder.
 
  
## <a name="how-dlp-in-the-security--compliance-center-works-with-dlp-and-mail-flow-rules-in-the-exchange-admin-center"></a>Fonctionnement de DLP dans le Centre de sécurité & conformité avec les règles de flux de messagerie et DLP dans le Centre d’administration Exchange

Après avoir créé une stratégie DLP dans le Centre de sécurité & conformité, la stratégie est déployée sur tous les emplacements inclus dans la stratégie. Si la stratégie inclut Exchange Online, la stratégie y est synchronisée et appliquée exactement de la même façon qu’une stratégie DLP créée dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>. 
  
Si vous avez créé des stratégies DLP dans le Centre d’administration Exchange, ces stratégies continueront de fonctionner côte à côte avec toutes les stratégies de courrier que vous créez dans le Centre de sécurité & conformité. Toutefois, notez que les règles créées dans le Centre d’administration Exchange sont prioritaires. Toutes les règles de flux de messagerie Exchange sont traitées en premier, puis les règles DLP du Centre de sécurité & conformité sont traitées.
  
Cela signifie :
  
- Les messages bloqués par les règles de flux de messagerie Exchange ne sont pas analysés par les règles DLP créées dans le Centre de sécurité & conformité.
- Les messages mis en quarantaine par les règles de flux de messagerie Exchange ou tout autre filtre s’exécutent avant que DLP ne soit analysé par DLP. 
- Si une règle de flux de messagerie Exchange modifie un message d’une manière qui l’amène à correspondre à une stratégie DLP dans le Centre de sécurité & conformité, par exemple l’ajout d’utilisateurs externes, les règles DLP le détectent et appliquent la stratégie en fonction des besoins.
    
Notez également que les règles de flux de messagerie Exchange qui utilisent l’action « Arrêter le traitement » n’affectent pas le traitement des règles DLP dans le Centre de sécurité & conformité . Elles seront toujours traitées.
  
## <a name="policy-tips-in-the-security--compliance-center-vs-the-exchange-admin-center"></a>Conseils de stratégie dans le Centre de sécurité & conformité et le Centre d’administration Exchange

Les conseils de stratégie peuvent fonctionner avec des stratégies DLP et des règles de flux de messagerie créées dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange</a>, ou avec des stratégies DLP créées dans le Centre de sécurité & conformité, mais pas les deux. En fait, ces stratégies sont stockées à différents emplacements, mais les conseils de stratégie ne peuvent être utilisés qu’à partir d’un emplacement unique.
  
Si vous avez configuré des conseils de stratégie dans le Centre d’administration Exchange, les conseils de stratégie que vous configurez dans le Centre de sécurité & conformité n’apparaissent pas aux utilisateurs dans Outlook sur le web et Outlook 2013 et versions ultérieures tant que vous n’avez pas désactivé les conseils dans le Centre d’administration Exchange. Cela garantit que vos règles de flux de messagerie Exchange actuelles continueront de fonctionner jusqu’à ce que vous choisissiez de basculer vers le Centre de sécurité & conformité.
  
>[!Note]
>Bien que les conseils de stratégie ne puissent être utilisés qu’à partir d’un emplacement unique, les notifications par e-mail sont toujours envoyées, même si vous utilisez des stratégies DLP à la fois dans le Centre de sécurité & conformité et dans le Centre d’administration Exchange.
