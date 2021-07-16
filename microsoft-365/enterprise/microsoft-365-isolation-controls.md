---
title: Contrôles d'isolation Microsoft 365
ms.author: robmazz
author: robmazz
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.collection:
- Strat_O365_IP
- M365-security-compliance
f1.keywords:
- NOCSH
description: Découvrez comment fonctionnent les contrôles d’isolation Microsoft 365, ce qui permet aux services d’inter-fonctionner ou de rester autonomes selon les besoins.
ms.custom: seo-marvel-apr2020
ms.openlocfilehash: 514b12e44d9e81a18b691ebf3196a3d21157e71b
ms.sourcegitcommit: 27addd4dac07926528b788215d2dcd0e46301eb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/16/2021
ms.locfileid: "53464098"
---
# <a name="microsoft-365-isolation-controls"></a>Contrôles d'isolation Microsoft 365 

Microsoft s’assure en permanence que l’architecture multi-clients de Microsoft 365 prend en charge la sécurité, la confidentialité, la confidentialité, l’intégrité, les normes locales, internationales et de disponibilité au niveau de [l’entreprise.](https://www.microsoft.com/TrustCenter/Compliance?service=Office#Icons) L’échelle et l’étendue des services fournis par Microsoft rendent difficile et non économique la gestion des Microsoft 365 avec une interaction humaine significative. Microsoft 365 services sont fournis via plusieurs centres de données distribués globalement, chacun hautement automatisé avec peu d’opérations nécessitant une intervention humaine ou tout accès au contenu client. Notre personnel prend en charge ces services et centres de données à l’aide d’outils automatisés et d’un accès à distance hautement sécurisé. 

Microsoft 365 se compose de plusieurs services qui fournissent des fonctionnalités métiers importantes et contribuent à l’ensemble Microsoft 365 expérience utilisateur. Chacun de ces services est autonome et conçu pour s’intégrer les uns aux autres.

Microsoft 365 est conçu avec les principes suivants :

 - **[Architecture orientée service](/previous-versions/aa480021(v=msdn.10))** : conception et développement de logiciels sous la forme de services interopérables fournissant des fonctionnalités métiers bien définies.
 - **[Operational Security Assurance](https://www.microsoft.com/download/details.aspx?id=40872)** : infrastructure qui intègre les connaissances acquises grâce à différentes fonctionnalités propres à Microsoft, notamment le cycle de vie du développement de la sécurité Microsoft, le Centre de réponse de sécurité [Microsoft](https://technet.microsoft.com/library/dn440717.aspx)et la connaissance approfondie du paysage des menaces de cybersécurité. [](https://www.microsoft.com/sdl/default.aspx)

Microsoft 365 services inter-opèrent les uns avec les autres, mais sont conçus et implémentés pour pouvoir être déployés et gérés en tant que services autonomes, indépendamment les uns des autres. Microsoft sépare les tâches et les domaines de responsabilité des Microsoft 365 afin de réduire les possibilités de modification non autorisée ou involontaire ou d’utilisation abusive des biens de l’organisation. Microsoft 365 équipes ont défini des rôles dans le cadre d’un mécanisme complet de contrôle d’accès basé sur les rôles.

## <a name="customer-content-isolation"></a>Isolation du contenu client

Tout le contenu client d’un client est isolé des autres clients et des données des opérations et des systèmes utilisées dans la gestion des Microsoft 365. Plusieurs formes de protection sont implémentées dans Microsoft 365 pour minimiser le risque de compromission d'un service ou d'une application Microsoft 365. Plusieurs formes de protection empêchent également l’accès non autorisé aux informations des locataires ou du Microsoft 365 lui-même.

Pour plus d’informations sur la façon dont Microsoft implémente l’isolation logique des données client au sein Microsoft 365, voir Isolation du client [dans Microsoft 365](microsoft-365-tenant-isolation-overview.md).