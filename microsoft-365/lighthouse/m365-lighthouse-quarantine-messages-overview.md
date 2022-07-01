---
title: Vue d’ensemble des messages mis en quarantaine dans Microsoft 365 Lighthouse
f1.keywords: CSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: shcallaw
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolio
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment gérer les messages mis en quarantaine.
ms.openlocfilehash: 3a295802ba806c48f01f6f64c8b148169fe28102
ms.sourcegitcommit: 85799f0efc06037c1ff309fe8e609bbd491f9b68
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/01/2022
ms.locfileid: "66574367"
---
# <a name="overview-of-quarantined-messages-in-microsoft-365-lighthouse"></a>Vue d’ensemble des messages mis en quarantaine dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse vous permet de voir des insights et des informations sur les e-mails mis en quarantaine sur tous vos locataires clients. À partir d’une seule vue, vous pouvez trier les e-mails mis en quarantaine et prendre les mesures appropriées. Les données sont disponibles si le locataire a implémenté Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 Plan 1 (MDO).

Vous pouvez accéder aux informations en sélectionnant **Protection des données** dans la navigation de gauche ou la page **d’accueil** .

## <a name="quarantined-messages-page"></a>Page Messages mis en quarantaine

À partir de cette page, vous pouvez afficher des statistiques consolidées sur vos locataires clients, des données de tendance pour le type et le volume de données de quarantaine, ainsi que des informations relatives aux files d’attente de mise en quarantaine dans des locataires clients individuels.

La section **État des messages** fournit une vue consolidée des locataires éligibles actuellement intégrés à Lighthouse. La vue inclut

- Nombre total de messages en quarantaine
- Nombre total de messages en attente de révision
- Messages qui approchent actuellement de la limite de mise en quarantaine par défaut de 30 jours et qui sont sur le point d’être supprimés automatiquement (expirer)
- Messages qui ont été libérés de la quarantaine
- Nombre total de boîtes aux lettres impactées sur tous vos locataires

Les données reflètent les 30 derniers jours ; toutefois, vous pouvez utiliser le filtre **d’intervalle de temps** pour modifier la vue.

Le **graphique raison** de la **quarantaine** contient une répartition des nombres de quarantaines par type de stratégie Exchange Online Protection (EOP) et Microsoft Defender pour Office 365 Plan 1 (MDO). Ces types incluent

- Programme malveillant
- Hameçonnage
- Hameçonnage à haut niveau de confiance
- Courrier indésirable
- Courrier électronique en bloc

La liste de quarantaine est une vue triable des informations de quarantaine par locataire. Dans cette vue, vous pouvez filtrer en fonction des informations suivantes :

- **Raison de la quarantaine :** Any, Malware, Phish, Phish haute confiance, Spam, Courrier électronique en bloc
- **Type de stratégie :** Any, Anti-malware, Anti-phishing, Anti-spam, Pièces jointes sécurisées, Règle de transport, Inconnu
- **Sur le point d’expirer :** Any, Today, within two days, within seven days

Vous pouvez également ajuster les colonnes et trier les données en fonction du locataire, de l’état du message et des dates d’expiration.

:::image type="content" source="../media/m365-lighthouse-data-protection/quarantine-email-page.png" alt-text="Page Messages de mise en quarantaine dans Microsoft 365 Lighthouse" lightbox="../media/m365-lighthouse-data-protection/quarantine-email-page.png":::

L’option **Copier le lien vers les messages dans Microsoft** **365 Defender** fournit un lien vers Microsoft 365 Defender portail où vous pouvez accéder et gérer la file d’attente de mise en quarantaine des e-mails de votre locataire. Vous devez vous authentifier avant de pouvoir effectuer une action.

## <a name="related-content"></a>Contenu connexe

[Messages électroniques mis en quarantaine](../security/office-365-security/quarantine-email-messages.md) (article)\
[Recommandations Microsoft pour EOP et Defender pour Office 365 paramètres de sécurité](../security/office-365-security/recommended-settings-for-eop-and-office365.md) (article)\
[vue d’ensemble de Exchange Online Protection (EOP)](../security/office-365-security/exchange-online-protection-overview.md) (article)
