---
title: Transférer un domaine de Microsoft vers un autre hôte
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
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
description: 'Recherchez les étapes ici pour transférer un domaine de Microsoft vers un autre bureau d’enregistrement. '
ms.openlocfilehash: ae4c261cacd12e99bac8e18d6fc55a8db452e03b
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68727408"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Transférer un domaine de Microsoft vers un autre hôte

Vous ne pouvez pas transférer un domaine Microsoft 365 vers un autre bureau d’enregistrement pendant 60 jours après l’achat du domaine auprès de Microsoft.

> [!NOTE]
> Une requête _Whois_ montre un bureau d’enregistrement de domaines acheté par Microsoft en tant que Wild West Domains LLC. Toutefois, seul Microsoft doit être contacté concernant votre domaine microsoft 365 acheté.

Connectez-vous en tant qu’administrateur général, suivez ces étapes pour obtenir un code sur Microsoft 365, puis accédez au site web de l’autre bureau d’enregistrement de domaines pour configurer le transfert de votre nom de domaine vers le nouveau bureau d’enregistrement.

## <a name="transfer-a-domain"></a>Transférer un domaine

1. Dans le Centre d’administration, accédez à **Paramètres** \> **Domaines**.

2. Dans la page **Domaines** , sélectionnez le domaine Microsoft 365 que vous souhaitez transférer vers un autre bureau d’enregistrement de domaines, puis sélectionnez **Vérifier l’intégrité**.

3. En haut de la page, sélectionnez **Transférer le domaine**.

4. Dans la page **Choisir l’emplacement de transfert de votre domaine** , sélectionnez **Un autre bureau d’enregistrement**, puis cliquez sur **Suivant**.

5. Dans la page **Déverrouiller le transfert de domaine** , sélectionnez Déverrouiller le **transfert pour <_votre domaine_>**, puis sélectionnez **Suivant**.

6. Vérifiez vos informations de contact de transfert de domaine, puis sélectionnez **Suivant**.

7. Copiez le code d’autorisation et attendez environ 30 minutes que l’état de transfert de votre domaine passe à **Déverrouillé pour transfert** sous l’onglet **Inscription** avant de passer aux étapes suivantes.

8. Accédez au site web du bureau d’enregistrement de domaines que vous souhaitez gérer votre nom de domaine à l’avenir. Suivez les instructions pour transférer un domaine (recherchez de l’aide sur leur site web). Cela signifie généralement payer des frais de transfert et donner l’authentification au nouveau bureau d’enregistrement afin qu’il puisse lancer le transfert. Microsoft vous adressera un e-mail pour confirmer que nous avons reçu la demande de transfert, et le domaine effectuera le transfert dans un délai de 5 jours.

    Vous trouverez l’onglet **Inscription** du code d’autorisation dans la page **Domaines** de Microsoft 365.

    > [!TIP]
    > Les domaines .uk nécessitent une procédure différente. Contactez Support Microsoft et demandez une modification de **balise IPS** pour qu’elle corresponde au bureau d’enregistrement que vous souhaitez gérer votre domaine à l’avenir. Une fois la balise modifiée, le domaine est immédiatement transféré au nouveau bureau d’enregistrement. Vous devrez ensuite travailler avec le nouveau bureau d’enregistrement pour terminer le transfert, en payant probablement des frais de transfert et en ajoutant le domaine transféré à votre compte avec votre nouveau bureau d’enregistrement.

9. Une fois le transfert terminé, vous renouvelez votre domaine auprès du nouveau bureau d’enregistrement de domaines.

10. Pour terminer le processus, revenez à la page **Domaines** dans le Centre d’administration, puis sélectionnez **Terminer le transfert de domaine**. Cela marque le domaine comme n’étant plus acheté auprès de Microsoft 365 et désactive l’abonnement au domaine. Il ne supprime pas le domaine du locataire et n’affecte pas les utilisateurs et les boîtes aux lettres existants sur le domaine.

> [!NOTE]
> Les domaines achetés par Microsoft 365 ne sont pas éligibles pour les modifications de serveur de noms ou le transfert du domaine entre les organisations Microsoft 365. Si l’un de ces éléments est requis, l’inscription de domaine doit être transférée à un autre bureau d’enregistrement.
