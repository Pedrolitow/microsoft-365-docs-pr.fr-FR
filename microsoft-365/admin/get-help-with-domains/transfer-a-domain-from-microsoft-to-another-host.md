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
description: 'Recherchez les étapes ci-dessous pour transférer un domaine de Microsoft vers un autre bureau d’enregistrement. '
ms.openlocfilehash: 7209d17caf8e89760a3abe9543f78c3c86c39bc4
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68193914"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Transférer un domaine de Microsoft vers un autre hôte

Vous ne pouvez pas transférer un domaine Microsoft 365 vers un autre bureau d’enregistrement pendant 60 jours après avoir acheté le domaine auprès de Microsoft.

> [!NOTE]
> Une requête _Whois_ montre un bureau d’enregistrement de domaines acheté par Microsoft en tant que Wild West Domains LLC. Toutefois, seul Microsoft doit être contacté concernant votre domaine acheté par Microsoft 365.

Suivez ces étapes pour obtenir un code sur Microsoft 365, puis accédez à l’autre site web du bureau d’enregistrement de domaines pour configurer le transfert de votre nom de domaine vers le nouveau bureau d’enregistrement.

## <a name="transfer-a-domain"></a>Transférer un domaine

1. Dans le centre d’administration, accédez à **Domaines de** \> **paramètres**.

2. Dans la page **Domaines** , sélectionnez le domaine Microsoft 365 que vous souhaitez transférer vers un autre bureau d’enregistrement de domaines, puis **sélectionnez Vérifier l’intégrité**.

3. En haut de la page, sélectionnez **Transférer le domaine**.

4. Dans la page **Choisir où transférer votre domaine** , sélectionnez **Un autre bureau d’enregistrement**, puis cliquez sur **Suivant**.

5. Dans la page **Déverrouiller le transfert de domaine** , sélectionnez **Déverrouiller le transfert pour <_votre domaine_>**, puis sélectionnez **Suivant**.

6. Vérifiez vos informations de contact de transfert de domaine, puis sélectionnez **Suivant**.

7. Copiez le code d’autorisation et attendez environ 30 minutes que votre état de transfert de domaine passe à **Déverrouillé pour transfert** sous **l’onglet Inscription** avant de passer aux étapes suivantes.

8. Accédez au site web du bureau d’enregistrement de domaines que vous souhaitez gérer votre nom de domaine à l’avenir. Suivez les instructions pour transférer un domaine (recherchez de l’aide sur son site web). Cela implique généralement de payer des frais de transfert et de donner l’Authcode au nouveau bureau d’enregistrement afin qu’il puisse lancer le transfert. Microsoft vous enverra un e-mail pour confirmer que nous avons reçu la demande de transfert et que le domaine sera transféré dans les 5 jours.

    Vous trouverez l’onglet Inscription du code **d’autorisation** dans la page **Domaines** de Microsoft 365.

    > [!TIP]
    > Les domaines .uk nécessitent une procédure différente. Contactez Support Microsoft et demandez un changement de **balise IPS** pour qu’il corresponde au bureau d’enregistrement que vous souhaitez gérer à l’avenir. Une fois la balise modifiée, le domaine est immédiatement transféré vers le nouveau bureau d’enregistrement. Vous devrez ensuite travailler avec le nouveau bureau d’enregistrement pour effectuer le transfert, en payant probablement des frais de transfert et en ajoutant le domaine transféré à votre compte avec votre nouveau bureau d’enregistrement.

9. Une fois le transfert terminé, vous allez renouveler votre domaine auprès du nouveau bureau d’enregistrement de domaines.

10. Pour terminer le processus, revenez à la page **Domaines** dans le centre d’administration, puis sélectionnez **Terminer le transfert de domaine**. Cela marquera le domaine comme n’étant plus acheté auprès de Microsoft 365 et désactivera l’abonnement au domaine. Il ne supprime pas le domaine du locataire et n’affecte pas les utilisateurs et boîtes aux lettres existants sur le domaine.

> [!NOTE]
> Les domaines achetés par Microsoft 365 ne sont pas éligibles aux modifications du serveur de noms ou au transfert du domaine entre les organisations Microsoft 365. Si l’une de ces opérations est requise, l’inscription de domaine doit être transférée à un autre bureau d’enregistrement.
