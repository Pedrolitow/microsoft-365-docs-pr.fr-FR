---
title: Protection anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- m365-security
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les fonctionnalités de protection anti-hameçonnage dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: a1f5914d0687a437dfe7b026ea02c9c33b026a9d
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68090913"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Protection anti-hameçonnage dans Microsoft 365

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le *Hameçonnage* est une attaque par courrier électronique qui tente d’accéder à des informations sensibles par le biais de messages qui paraissent provenir d’expéditeurs légitimes ou approuvés. Il existe des catégories spécifiques de hameçonnage. Par exemple :

- **Le harponnage** utilise du contenu ciblé et personnalisé spécifiquement adapté aux destinataires ciblés (généralement, après reconnaissance sur les destinataires par l’attaquant).

- **Le harponnage de cadre** est dirigé vers les cadres ou d’autres cibles à valeur élevée au sein d’une organisation pour un effet maximal.

- **La compromission par e-mail d’entreprise (BEC)** utilise des expéditeurs de confiance falsifiés (agents financiers, clients, partenaires approuvés, etc.) pour inciter les destinataires à approuver les paiements, à transférer des fonds ou à révéler des données client. Pour en savoir plus, regardez [cette vidéo](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2).

- **Les ransomware** qui chiffrent vos données et exigent un paiement pour les déchiffrer commencent presque toujours par des messages de hameçonnage. La protection anti-hameçonnage ne peut pas vous aider à déchiffrer les fichiers chiffrés, mais elle peut vous aider à détecter les messages de hameçonnage initiaux associés à la campagne de rançongiciel. Pour plus d’informations sur la récupération à la suite d’une attaque par ransomware, consultez [Récupérer à partir d’une attaque par ransomware dans Microsoft 365](recover-from-ransomware.md).

Avec la complexité croissante des attaques, il est même difficile pour les utilisateurs formés d’identifier les messages de hameçonnage sophistiqués. Heureusement, Exchange Online Protection (EOP) et les fonctionnalités supplémentaires de Microsoft Defender pour Office 365 peuvent vous aider.

## <a name="anti-phishing-protection-in-eop"></a>Protection anti-hameçonnage dans EOP

EOP (autrement dit, les organisations Microsoft 365 sans Microsoft Defender pour Office 365) contient des fonctionnalités qui peuvent aider à protéger votre organisation contre les menaces de hameçonnage :

- **Intelligence par usurpation** d’identité : utilisez l’insight d’intelligence de l’usurpation d’identité pour examiner les expéditeurs usurpés détectés dans les messages provenant de domaines externes et internes, et autoriser ou bloquer manuellement ces expéditeurs détectés. Si vous souhaitez en savoir plus, consultez [Informations sur la veille contre l’usurpation d’identité dans EOP](learn-about-spoof-intelligence.md).

- **Stratégies anti-hameçonnage dans EOP** : activez ou désactivez l’intelligence d’usurpation d’identité, activez ou désactivez les indicateurs d’expéditeur non authentifiés dans Outlook et spécifiez l’action pour les expéditeurs usurpés bloqués. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-hameçonnage dans EOP](configure-anti-phishing-policies-eop.md).

- **Autoriser ou bloquer les expéditeurs usurpés dans la liste d’autorisation/de** blocage du locataire : lorsque vous remplacez le verdict dans l’insight d’intelligence de l’usurpation d’identité, l’expéditeur usurpé devient une entrée d’autorisation ou de blocage manuelle qui apparaît uniquement sous l’onglet **Expéditeurs usurpés** dans la liste d’autorisations/blocs du locataire. Vous pouvez également créer manuellement des entrées d'autorisation ou de blocage pour les faux expéditeurs avant qu'ils ne soient détectés par la veille contre l’usurpation d’identité. Pour plus d’informations, voir [Gérer liste rouge/verte du client dans EOP](manage-tenant-allow-block-list.md).

- **Authentification par e-mail implicite** : EOP améliore les vérifications d’authentification par e-mail standard pour les e-mails entrants ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md) et [DMARC](use-dmarc-to-validate-email.md) avec la réputation de l’expéditeur, l’historique de l’expéditeur, l’historique des destinataires, l’analyse comportementale et d’autres techniques avancées pour aider à identifier les expéditeurs falsifiés. Si vous souhaitez en savoir plus, consultez la page [Authentification de messagerie électronique dans Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Protection supplémentaire contre les attaques par phishing dans Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 contient des fonctionnalités supplémentaires et plus avancées de protection contre le phishing :

- **Stratégies anti-hameçonnage dans Microsoft Defender pour Office 365** : configurez les paramètres de protection d’emprunt d’identité pour des domaines d’expéditeur et d’expéditeur de messages spécifiques, des paramètres d’intelligence de boîte aux lettres et des seuils de hameçonnage avancés réglables. Pour plus d’informations, consultez [Paramètres exclusifs des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365](configure-mdo-anti-phishing-policies.md). Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage dans EOP et les stratégies anti-hameçonnage dans Defender pour Office 365, consultez [les stratégies anti-hameçonnage dans Microsoft 365](set-up-anti-phishing-policies.md).
- **Vues de campagne** : Le Machine Learning et d’autres heuristiques identifient et analysent les messages impliqués dans des attaques de hameçonnage coordonnées contre l’ensemble du service et de votre organisation. Pour plus d’informations, consultez [Affichages de campagne dans Microsoft Defender pour Office 365](campaigns.md).
- **Exercice de simulation d'attaque** : les administrateurs peuvent créer de faux messages de hameçonnage et les envoyer à des utilisateurs internes en tant qu’outil d’éducation. Pour plus d’informations, consultez [Simuler une attaque par hameçonnage](attack-simulation-training.md).

## <a name="other-anti-phishing-resources"></a>Autres ressources anti-hameçonnage

- Pour les utilisateurs finaux : [protégez-vous contre les schémas d’hameçonnage et d’autres formes de fraude en ligne](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593).

- [Comment Microsoft 365 valide l’adresse From pour empêcher le hameçonnage](how-office-365-validates-the-from-address.md).
