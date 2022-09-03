---
title: Afficher une connexion réseau d’entreprise pc cloud ayant échoué dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
ms-reviewer: katmartin
audience: Admin
ms.topic: article
ms.service: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment afficher un PC cloud d’entreprise ayant échoué à la connexion réseau.
ms.openlocfilehash: 0d4c2c535da22199c2667b08e3a0f0c1c13928e3
ms.sourcegitcommit: 2b89bcff547e00be3d38dc8d1e6cbcf8f41eba42
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/03/2022
ms.locfileid: "67590697"
---
# <a name="view-an-enterprise-cloud-pc-failed-network-connection-in-microsoft-365-lighthouse"></a>Afficher une connexion réseau d’entreprise pc cloud ayant échoué dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse fournit l’état de connexion entre vos locataires clients et Azure Active Directory (Azure AD). Lorsqu’un PC cloud a une connexion réseau ayant échoué, vous pouvez afficher des informations détaillées dans le Centre d’administration Microsoft Endpoint Manager.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être administrateur général dans le locataire partenaire.
- Vous devez disposer d’un accès Administrateur de PC cloud ou Lecteur de PC cloud pour afficher les problèmes de connexion.

## <a name="view-a-failed-network-connection"></a>Afficher une connexion réseau ayant échoué

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Appareils** >  **Windows 365**.

2. Sélectionnez l’onglet **Connexions réseau Azure** .

3. Dans la barre de couleur count-annotation, sélectionnez **Connexions ayant échoué**.

4. Dans la liste filtrée, sélectionnez **Afficher les détails de la connexion dans Microsoft Endpoint Manager** en regard de la connexion à examiner.

5. Dans le Centre d’administration Microsoft Endpoint Manager, sélectionnez **Afficher les détails** pour en savoir plus sur l’erreur.

## <a name="next-steps"></a>Prochaines étapes

Pour résoudre les problèmes de connexion, consultez [Résolution des problèmes de connexion réseau locale](/windows-365/enterprise/troubleshoot-on-premises-network-connection).

## <a name="related-content"></a>Contenu associé

[Contrôle d’accès en fonction du rôle pc cloud ](/windows-365/enterprise/role-based-access)(article)\
[Jonction de domaine Active Directory](/windows-365/enterprise/troubleshoot-on-premises-network-connection#active-directory-domain-join) (article)\
[Azure Active Directory device Sync](/windows-365/enterprise/troubleshoot-on-premises-network-connection#azure-active-directory-device-sync) (article)
