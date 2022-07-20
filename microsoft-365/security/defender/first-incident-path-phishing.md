---
title: Exemple d’attaque par e-mail de hameçonnage
description: Parcourez un exemple d’analyse d’une attaque par hameçonnage.
keywords: incidents, alertes, enquêter, corrélation, attaque, machines, appareils, utilisateurs, identités, identité, boîte de réception, e-mail, 365, microsoft, m365
search.product: eADQiWindows 10XVcnh
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- M365-security-compliance
- m365solution-firstincident
ms.topic: conceptual
search.appverid:
- MOE150
- MET150
ms.technology: m365d
ms.openlocfilehash: dcf620cfaeb1d33665538d16d080e72745b96e42
ms.sourcegitcommit: c1eaea74c8ffce2f9f477c9469342e88e4a70c14
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/20/2022
ms.locfileid: "66892905"
---
# <a name="example-of-a-phishing-email-attack"></a>Exemple d’attaque par e-mail de hameçonnage

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender.md)]

**S’applique à :**
- Microsoft 365 Defender

Microsoft 365 Defender pouvez aider à détecter les pièces jointes malveillantes fournies par e-mail. Étant donné que le [Centre de sécurité et de conformité Office 365](https://protection.office.com/) s’intègre à Microsoft 365 Defender, les analystes de sécurité peuvent avoir une visibilité sur les menaces provenant de Office 365, telles que les pièces jointes.

Par exemple, un incident à plusieurs étapes a été attribué à un analyste.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-incident.png" alt-text="Un incident à plusieurs étapes" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-incident.png":::

Sous l’onglet **Alertes** de l’incident, les alertes de Defender pour Office 365 et de Microsoft Defender for Cloud Apps sont affichées. L’analyste peut explorer les alertes Defender pour Office 365 en sélectionnant les alertes de messages électroniques. Les détails de l’alerte sont affichés dans le volet latéral.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png" alt-text="Alerte par e-mail" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-alerts.png":::
 
En faisant défiler l’écran vers le bas, des informations supplémentaires s’affichent, montrant les fichiers malveillants et l’utilisateur qui ont été affectés.

:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-impact.png" alt-text="Impact sur l’utilisateur et le fichier d’une alerte par e-mail" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-impact.png":::
  
La sélection de la **page Ouvrir l’alerte** vous permet d’accéder à l’alerte spécifique où différentes informations peuvent être consultées plus en détail en sélectionnant le lien. Le message électronique réel peut être affiché en sélectionnant **Afficher les messages dans l’Explorateur en** bas du panneau.
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png" alt-text="Détails d’une alerte" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-event-explorer.png"::: 

Cela permet à l’analyste d’accéder à la page Gestion des menaces où l’objet de l’e-mail, le destinataire, l’expéditeur et d’autres informations sont affichés. **ZAP** sous **Actions spéciales** indique à l’analyste que la fonctionnalité de vidage automatique de zéro heure a été implémentée. ZAP détecte et supprime automatiquement les messages malveillants et indésirables des boîtes aux lettres au sein de l’organisation. Pour plus d’informations, consultez [le vidage automatique de zéro heure (ZAP) dans Exchange Online](../office-365-security/zero-hour-auto-purge.md).

D’autres actions peuvent être effectuées sur des messages spécifiques en sélectionnant **Actions**. 
 
:::image type="content" source="../../media/first-incident-path-phishing/first-incident-phishing-actions.png" alt-text="Autres actions qui peuvent être effectuées sur les e-mails" lightbox="../../media/first-incident-path-phishing/first-incident-phishing-actions.png"::: 

## <a name="next-step"></a>Étape suivante

Consultez le chemin d’accès à l’enquête [sur les attaques basées sur l’identité](first-incident-path-identity.md) .

## <a name="see-also"></a>Voir aussi

- [Vue d’ensemble des incidents](incidents-overview.md)
- [Enquêter sur des incidents](investigate-incidents.md)
- [Gérer les incidents](manage-incidents.md)
