---
title: Journal d’activités du portail des messages chiffrés
f1.keywords:
- NOCSH
ms.author: v-tophillips
author: v-tophillips
manager: laurawi
audience: Admin
ms.topic: conceptual
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 05/12/2022
ms.collection:
- Strat_O365_IP
- M365-security-compliance
search.appverid:
- MET150
description: Les journaux d’accès sont disponibles pour les messages chiffrés récupérés via le portail des messages chiffrés.
ms.openlocfilehash: 50656d1695d8fc3d6e81de6afc03b3f4e3c5ccee
ms.sourcegitcommit: 54bc063818779e351ca24f04ba571f762d85751d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/13/2022
ms.locfileid: "65393223"
---
# <a name="encrypted-message-portal-activity-log-by-microsoft-purview-advanced-message-encryption-preview"></a>Journal d’activité du portail de messages chiffré par Microsoft Purview Advanced Message Encryption (préversion)

Les journaux d’accès sont disponibles pour les messages chiffrés via le portail des messages chiffrés qui permet à votre organisation de déterminer quand les messages sont lus et transférés par vos destinataires externes. Pour vous assurer que les journaux sont disponibles pour tous les destinataires externes, vous devez appliquer un modèle de personnalisation personnalisé aux e-mails protégés envoyés par votre organisation aux destinataires externes qui appliquent une expérience de portail. Voir [Ajouter la marque de votre organisation à vos messages chiffrés](add-your-organization-brand-to-encrypted-messages.md).

## <a name="enabling-message-access-audit-logs-in-powershell"></a>Activation des journaux d’audit d’accès aux messages dans PowerShell

Le journal d’accès peut être activé à l’aide de Exchange Online PowerShell. Le paramètre *-EnablePortalTrackingLogs* de Set-IrmConfiguration spécifie s’il faut activer les journaux d’audit pour accéder au portail de messages chiffrés. Les valeurs valides sont les suivantes :

- $true : activez la fonctionnalité d’audit.
- $false : désactiver la fonctionnalité d’audit

Exemple : Set-IrmConfiguration -EnablePortalTrackingLogs $true

Pour plus d’informations, consultez [Set-IRMConfiguration (ExchangePowerShell).](/powershell/module/exchange/set-irmconfiguration)

## <a name="message-access-audit-information"></a>Informations d’audit d’accès aux messages

Le journal d’accès contient des entrées pour les messages envoyés via le portail de messages chiffrés pour les types d’activité suivants :

- Horodatage de connexion et méthode d’authentification des utilisateurs externes
- L’utilisateur externe lit des messages ou des pièces jointes
- Téléchargement de pièces jointes
- réponses de messagerie et transfert

Pour plus d’informations sur le schéma du journal d’accès aux messages, consultez [Rechercher dans le journal d’audit dans le portail de conformité](search-the-audit-log-in-security-and-compliance.md#encrypted-message-portal-activities).

## <a name="search-for-events-in-the-message-access-logs"></a>Rechercher des événements dans les journaux d’accès aux messages

Pour afficher les événements capturés dans les journaux d’accès aux messages :

1. Dans le portail de conformité Microsoft Purview, sous **Solutions**, sélectionnez **Audit**.
1. Sous **Rechercher**, cliquez sur la liste **déroulante des activités** et tapez les activités du portail de messages chiffrées.
1. Sous activités du portail de messages chiffrés, sélectionnez les types d’événements à utiliser dans la recherche. Définissez la plage de dates pour la recherche (la semaine précédente est la semaine par défaut), vous pouvez également ajouter un utilisateur particulier dans votre organisation pour la recherche. Lorsque vous êtes prêt, sélectionnez **Rechercher**.
1. Sélectionnez un événement dans la liste pour afficher les propriétés d’audit.
