---
title: Vue d’ensemble des messages mis en quarantaine dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms.reviewer: shcallaw
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services managés (MSP) utilisant Microsoft 365 Lighthouse, découvrez comment gérer les messages mis en quarantaine.
ms.openlocfilehash: 23324b382a58fafd01c639a36672c9e3f3b71329
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68659804"
---
# <a name="overview-of-quarantined-messages-in-microsoft-365-lighthouse"></a>Vue d’ensemble des messages mis en quarantaine dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse vous permet de voir des insights et des informations sur les e-mails mis en quarantaine dans tous vos locataires clients. À partir d’une vue unique, vous pouvez trier les e-mails mis en quarantaine et prendre les mesures appropriées. Les données sont disponibles si le locataire a implémenté Exchange Online Protection (EOP) et Microsoft Defender pour Office365 Plan 1 (MDO).

Vous pouvez accéder aux informations en sélectionnant **Accueil** dans le volet de navigation gauche ou en sélectionnant **Protection des données** dans le volet de navigation gauche pour ouvrir la page Messages mis en quarantaine.

## <a name="quarantined-messages-page"></a>Page messages mis en quarantaine

À partir de cette page, vous pouvez afficher des statistiques consolidées sur vos locataires clients, des données de tendance pour le type et le volume des données de quarantaine, ainsi que des informations relatives aux files d’attente de mise en quarantaine dans des locataires clients individuels.

La section **État des messages** fournit une vue consolidée des locataires éligibles actuellement intégrés à Lighthouse. La vue inclut

- Nombre total de messages en quarantaine
- Nombre total de messages en attente de révision
- Messages qui approchent actuellement de la limite de quarantaine par défaut de 30 jours et qui sont sur le point d’être automatiquement supprimés (expirent)
- Messages qui ont été libérés de la quarantaine
- Nombre total de boîtes aux lettres impactées sur tous vos locataires

Les données reflètent les 30 derniers jours; Toutefois, vous pouvez utiliser le filtre **Intervalle de temps** pour modifier la vue.

La section **Raison** de la quarantaine contient une répartition des nombres de quarantaines par Exchange Online Protection (EOP) et Microsoft Defender pour le type de stratégie Office365 Plan 1 (MDO). Ces types incluent

- Programme malveillant
- Hameçonnage
- Hameçonnage à haute confiance
- Courrier indésirable
- Email en bloc

La liste de quarantaine est une vue triable des informations de quarantaine par locataire. Dans cette vue, vous pouvez filtrer selon les informations suivantes :

- **Raison de la quarantaine :** Any, Malware, Phish, High confidence phish, Spam, Bulk Email
- **Type de stratégie :** Tout, Anti-programme malveillant, Anti-hameçonnage, Anti-courrier indésirable, Pièces jointes sécurisées, Règle de transport, Inconnu
- **Sur le point d’expirer :** Any, Aujourd’hui, dans les deux jours, dans les sept jours

Vous pouvez également ajuster les colonnes et trier les données en fonction du locataire, de l’état des messages et des dates d’expiration.

:::image type="content" source="../media/m365-lighthouse-data-protection/quarantine-email-page.png" alt-text="Page messages de mise en quarantaine dans Microsoft 365 Lighthouse" lightbox="../media/m365-lighthouse-data-protection/quarantine-email-page.png":::

L’option **Copier le lien vers les messages dans Microsoft** **365 Defender** fournit un lien vers Microsoft 365 Defender portail où vous pouvez accéder et gérer la file d’attente de mise en quarantaine des e-mails de votre locataire. Vous devez vous authentifier avant de pouvoir effectuer une action.

## <a name="related-content"></a>Contenu associé

[Messages électroniques mis en quarantaine](../security/office-365-security/quarantine-email-messages.md) (article)\
[Recommandations Microsoft pour les paramètres de sécurité EOP et Defender pour Office 365](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (article)\
[vue d’ensemble de Exchange Online Protection (EOP)](../security/office-365-security/exchange-online-protection-overview.md) (article)
