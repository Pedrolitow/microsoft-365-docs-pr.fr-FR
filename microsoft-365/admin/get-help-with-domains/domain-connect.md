---
title: Utilisation de Domain Connect
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: ec6f4bd8-5996-4505-ba68-afaf8a141fb9
description: Découvrez comment utiliser les bureaux d’enregistrement compatibles avec Domain Connect et ajouter votre domaine à Microsoft 365.
ms.openlocfilehash: e20588181a5e9ca55d11844e2f31c3504a2bbfa0
ms.sourcegitcommit: c757f434da78bae71d4b476e14836fdf4da9f31e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/21/2022
ms.locfileid: "67884332"
---
# <a name="using-domain-connect-to-add-your-domain-to-microsoft-365"></a>Utilisation de Domain Connect pour ajouter votre domaine à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez.

[Domain Connect](https://www.domainconnect.org/) permet aux bureaux d’enregistrement activés d’ajouter votre domaine à Microsoft 365 dans un processus en trois étapes qui prend quelques minutes.

Dans l’Assistant, nous allons simplement confirmer que vous êtes le propriétaire du domaine, puis configurer automatiquement les enregistrements de votre domaine. Par conséquent, le courrier électronique est envoyé à Microsoft 365 et à d’autres services Microsoft 365, tels que Teams, qui utilisent votre domaine.

> [!NOTE]
> Veillez à désactiver les bloqueurs de fenêtres contextuelles dans votre navigateur avant de démarrer l'Assistant de configuration.

## <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Bureaux d’enregistrement Domain Connect s’intégrant à Microsoft 365

- [11&amp; IONOS](https://www.1and1.com/)
- [123Reg](https://www.123-reg.co.uk/)
- [GoDaddy](https://www.godaddy.com/)
- [Wordpress](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer ou WildGbDomains (revendeurs GoDaddy utilisant l’hébergement DNS SecureServer)
  - [Hébergement web MadDog](https://maddogwebhosting.com/domains/)
  - [CheapNames](https://www.cheapnames.com)

## <a name="what-happens-to-my-email-and-website"></a>Qu’advient-il de mon courrier et de mon site web ?

After you finish setup, the MX record for your domain is updated to point to Microsoft 365 and all email for your domain will start coming to Microsoft 365. Make sure you've added users and set up mailboxes in Microsoft 365 for everyone who gets email on your domain!

If you have a website that you use with your business, it will keep working where it is. The Domain Connect setup steps don't affect your website.
