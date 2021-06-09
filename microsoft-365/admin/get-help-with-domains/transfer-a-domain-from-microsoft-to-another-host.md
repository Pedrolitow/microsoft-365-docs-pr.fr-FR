---
title: Transférer un domaine de Microsoft vers un autre hôte
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
ms.custom:
- AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: 'Pour transférer un domaine de Microsoft vers un autre bureau d’enregistrement, recherchez les étapes ci-après. '
ms.openlocfilehash: f34e9733ab53c8bdc6f4432c96e6232ecc26ee06
ms.sourcegitcommit: eac5d9f759f290d3c51cafaf335a1a1c43ded927
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/06/2021
ms.locfileid: "50126346"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Transférer un domaine de Microsoft vers un autre hôte

Vous ne pouvez pas transférer un domaine Microsoft 365 un autre bureau d’enregistrement pendant 60 jours après avoir acheté le domaine auprès de Microsoft.

> [!NOTE]
> Une _requête Whois_ affiche un bureau d’enregistrement de domaines acheté par   Microsoft en tant que Wild West Domains LLC. Toutefois, seul Microsoft doit être contacté concernant votre domaine Microsoft 365 acheté.

Suivez ces étapes pour obtenir un code sur Microsoft 365, puis allez sur l’autre site web du bureau d’enregistrement de domaines pour configurer le transfert de votre nom de domaine vers le nouveau bureau d’enregistrement.

## <a name="transfer-a-domain"></a>Transférer un domaine

1. Dans le Centre d’administration, Paramètres   ****   >  **Domaines**.

2. Dans la page **Domaines,** sélectionnez le domaine Microsoft 365 que vous souhaitez transférer vers un autre bureau d’enregistrement de domaines, puis sélectionnez Vérifier **l’état d’état.**

3. En haut de la page, sélectionnez **Transférer le domaine.**

4. Dans la page **Choisir où transférer** votre domaine, sélectionnez Un **autre** bureau d’enregistrement, puis cliquez sur **Suivant**.

5. Dans la page **Déverrouiller le** transfert de domaine, sélectionnez **Déverrouiller le transfert <_votre_ >** domaine, puis sélectionnez **Suivant**.

6. Vérifiez les informations de contact de transfert de votre domaine, puis sélectionnez **Suivant.**

7. Copiez le code d’autorisation et attendez environ 30 minutes que  l’état de transfert de votre domaine passe à Déverrouillé pour transfert sous l’onglet Inscription avant de passer aux étapes suivantes. 

8. Go to the website of the domain registrar you want to manage your domain name going forward. Suivez les instructions pour transférer un domaine (recherchez de l’aide sur son site web). Cela implique généralement de payer des frais de transfert et de donner l’authcode au nouveau bureau d’enregistrement afin qu’il puisse lancer le transfert. Microsoft vous adresse un e-mail pour confirmer que nous avons reçu la demande de transfert, et le domaine transférera dans un délai de 5 jours.

    L’onglet Inscription du **code** d’autorisation se trouve  **dans** la page Domaines Microsoft 365.
    
    > [!TIP]
    > Les domaines .uk nécessitent une procédure différente. Contactez le Support Microsoft et demandez une modification de balise **IPS** pour correspondre au bureau d’enregistrement que vous souhaitez gérer à l’avenir. Une fois la balise changée, le domaine transfère immédiatement vers le nouveau bureau d’enregistrement. Vous devrez ensuite travailler avec le nouveau bureau d’enregistrement pour effectuer le transfert, en payant probablement des frais de transfert et en ajoutant le domaine transféré à votre compte avec votre nouveau bureau d’enregistrement.

9. Une fois le transfert terminé, vous renouvelez votre domaine auprès du nouveau bureau d’enregistrement de domaines.

10. Pour terminer le processus, revenir à la page **Domaines** dans le Centre d’administration, puis sélectionnez   **Transférer le domaine complet.** Cela marque le domaine comme n’étant plus acheté auprès Microsoft 365 et désactive l’abonnement au domaine. Il ne supprime pas le domaine du client et n’affecte pas les utilisateurs et boîtes aux lettres existants sur le domaine.

> [!NOTE]
> Microsoft 365 domaines achetés ne sont pas éligibles pour les modifications de nameserver ou le transfert du domaine entre Microsoft 365 organisations. Si l’une d’elles est requise, l’enregistrement de domaine doit être transféré vers un autre bureau d’enregistrement.
