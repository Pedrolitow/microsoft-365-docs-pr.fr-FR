---
title: Utilisation de Domain Connect
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ec6f4bd8-5996-4505-ba68-afaf8a141fb9
description: Découvrez comment travailler avec des bureaux d’enregistrement activés pour Domain Connect et ajouter votre domaine à Microsoft 365.
ms.openlocfilehash: 109255d82100e636e3472242866a519ff64a9e54
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49655611"
---
# <a name="using-domain-connect"></a>Utilisation de Domain Connect

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.
  
[Les bureaux ](https://www.domainconnect.org/) d’enregistrement activés pour Domain Connect vous permettent d’ajouter votre domaine à Microsoft 365 au cours d’un processus en trois étapes qui prend quelques minutes. 
  
Dans l’Assistant, nous allons simplement confirmer que vous êtes propriétaire du domaine, puis configurer automatiquement les enregistrements de votre domaine, afin que le courrier électronique soit envoyé à Microsoft 365 et à d’autres services Microsoft 365, tels que Teams, fonctionnent avec votre domaine.
  
> [!NOTE]
> Veillez à désactiver les bloqueurs de fenêtres contextuelles dans votre navigateur avant de démarrer l'Assistant de configuration.
  
## <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Intégration des bureaux d’enregistrement Domain Connect à Microsoft 365

- [1 &amp; 1 IONOS](https://www.1and1.com/)
- [123Reg](https://www.123-reg.co.uk/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress](https://wordpress.com/)
- [Iquésk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer ou WildWestDomains (revendeurs GoDaddy utilisant l’hébergement DNS SecureServer)
    - [Domaines MadDog](https://www.maddogdomains.com/)
    - [SondesNames](https://www.cheapnames.com)

## <a name="what-happens-to-my-email-and-website"></a>Qu’arrive-t-il à mon courrier électronique et mon site web ?

Une fois que vous avez terminé l’installation, l’enregistrement MX de votre domaine est mis à jour pour pointer vers Microsoft 365 et tous les messages électroniques de votre domaine commenceront à arriver vers Microsoft 365. Assurez-vous d’avoir ajouté des utilisateurs et de configurer des boîtes aux lettres dans Microsoft 365 pour toute personne qui reçoit du courrier électronique sur votre domaine !
  
Si vous avez un site web que vous utilisez dans le cadre de votre activité, il continuera à fonctionner là où il se trouve. Les étapes de configuration de Domain Connect n’affectent pas votre site web.
