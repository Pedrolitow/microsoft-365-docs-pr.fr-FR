---
title: Transférer un domaine de Microsoft vers un autre hôte
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
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
- okr_smb
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
description: 'Recherchez les étapes à suivre pour transférer un domaine de Microsoft vers un autre serveur d’inscriptions. '
ms.openlocfilehash: 7e00f5ae2c36a06803a3f7a8acd825dcab90805c
ms.sourcegitcommit: 6fb2a1c404ea3c3573b0f7803bf17459a9387891
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "46788979"
---
# <a name="transfer-a-domain-from-microsoft-to-another-host"></a>Transférer un domaine de Microsoft vers un autre hôte

Vous ne pouvez pas transférer un domaine Microsoft 365 vers un autre bureau d’enregistrement pendant 60 jours après avoir acheté le domaine auprès de Microsoft.

> [!NOTE]
> Une requête _Whois_   affiche un bureau d’enregistrement de domaines Microsoft acheté comme sauvage (plain West Domains). Toutefois, seul Microsoft doit être contacté concernant votre domaine acheté Microsoft 365.

Suivez les étapes ci-dessous pour obtenir un code auprès de Microsoft 365, puis accédez au site Web du Bureau d’enregistrement de domaine pour configurer le transfert de votre nom de domaine vers le nouveau serveur d’inscriptions.

## <a name="transfer-a-domain"></a>Transférer un domaine

1. Dans le centre d’administration, accédez à  **paramètres**   >  **Domains**.

2. <sur la page **domaines** , sélectionnez le domaine Microsoft 365 que vous souhaitez transférer vers un autre bureau d’enregistrement de domaines, puis sélectionnez **vérifier l’intégrité**.

3. En haut de la page, sélectionnez **transférer un domaine**.

4. Sur la page **choisir l’emplacement de transfert de votre domaine** , sélectionnez **un autre bureau**d’enregistrement, puis cliquez sur **suivant**.

5. Sur la page **déverrouiller le transfert de domaine** , sélectionnez **déverrouiller le transfert pour les <_votre domaine_ > **, puis cliquez sur **suivant**.

6. Vérifiez votre domaine transférer les informations de contact, puis cliquez sur **suivant**.

7. Copiez le code d’autorisation et patientez 30 minutes avant que l’état de transfert de votre domaine passe à **déverrouillé pour le transfert** sous l’onglet **enregistrement** avant de passer aux étapes suivantes.

8. Accédez au site Web du Bureau d’enregistrement de domaines dont vous souhaitez gérer le nom de votre domaine. Suivez les instructions pour le transfert d’un domaine (recherchez de l’aide sur son site Web).

L’onglet **enregistrement** du code d’autorisation se trouve sur la page  **domaines** dans Microsoft 365.

9. Une fois le transfert terminé, vous allez renouveler votre domaine au niveau du nouveau bureau d’enregistrement de domaines.

10. Pour terminer le processus, revenez à la page **domaines** dans le centre d’administration, puis sélectionnez  **transfert de domaine complet**.

> [!NOTE]
> Les domaines achetés par Microsoft 365 ne sont pas éligibles pour les modifications de serveur de noms ou le transfert de domaine entre les organisations Microsoft 365. Si l’une de ces valeurs est requise, l’inscription du domaine doit être transférée vers un autre serveur d’inscriptions.
