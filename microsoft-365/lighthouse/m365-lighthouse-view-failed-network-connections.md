---
title: Afficher une connexion réseau d’entreprise pc cloud ayant échoué dans Microsoft 365 Lighthouse
f1.keywords: NOCSH
ms.author: sharik
author: SKjerland
manager: scotv
audience: Admin
ms.topic: article
ms.prod: microsoft-365-lighthouse
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365
ms.custom:
- AdminSurgePortfolib
- M365-Lighthouse
search.appverid: MET150
description: Pour les fournisseurs de services gérés (MSP) qui utilisent Microsoft 365 Lighthouse, découvrez comment afficher un PC cloud d’entreprise ayant échoué à la connexion réseau.
ms.openlocfilehash: 68cae662da8af7ee536a3e0e304c2d46b4f52835
ms.sourcegitcommit: 349f0f54b0397cdd7d8fbb9ef07f1b6654a32d6e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/20/2022
ms.locfileid: "65623672"
---
# <a name="view-an-enterprise-cloud-pc-failed-network-connection-in-microsoft-365-lighthouse"></a>Afficher une connexion réseau d’entreprise pc cloud ayant échoué dans Microsoft 365 Lighthouse

Microsoft 365 Lighthouse fournit l’état de connexion entre vos locataires et Azure Active Directory. Lorsqu’un PC cloud a une connexion réseau ayant échoué, vous pouvez afficher des informations détaillées dans Microsoft Endpoint Manager centre d’administration.

## <a name="before-you-begin"></a>Avant de commencer

- Vous devez être administrateur général dans le locataire partenaire.
- Vous devez disposer d’un accès administrateur de PC cloud ou lecteur de PC cloud pour afficher les problèmes de connexion.

## <a name="view-a-failed-network-connection"></a>Afficher une connexion réseau ayant échoué

1. Dans le volet de navigation gauche de Lighthouse, sélectionnez **Windows 365**.

2. Sélectionnez l’onglet **Connexions réseau Azure** .

3. Dans la zone récapitulative de la connexion, sélectionnez **Connexions ayant échoué**.

4. Dans la liste filtrée, sélectionnez **Afficher les détails de la connexion dans Microsoft Endpoint Manager** en regard de la connexion à examiner.

5. Dans Microsoft Endpoint Manager centre d’administration, sélectionnez **Afficher les détails** pour en savoir plus sur l’erreur.

## <a name="next-steps"></a>Prochaines étapes

Pour résoudre les problèmes de connexion, consultez l’article [résoudre les problèmes de connexion réseau locale](/windows-365/enterprise/troubleshoot-on-premises-network-connection) .

## <a name="related-content"></a>Contenu connexe

[Contrôle d’accès en fonction du rôle pc cloud ](/windows-365/enterprise/role-based-access)(article)\
[Jonction de domaine Active Directory](/windows-365/enterprise/troubleshoot-on-premises-network-connection#active-directory-domain-join) (article)\
[Azure Active Directory device Sync](/windows-365/enterprise/troubleshoot-on-premises-network-connection#azure-active-directory-device-sync) (article)
