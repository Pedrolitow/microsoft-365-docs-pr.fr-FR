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
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les fonctionnalités de protection anti-hameçonnage dans Exchange Online Protection (EOP) et Microsoft Defender pour Office 365.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a100e28ddee1629b2fe35e28742a43b891d13e57
ms.sourcegitcommit: 6e5c00f84b5201422aed094f2697016407df8fc2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/02/2021
ms.locfileid: "51570611"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Protection anti-hameçonnage dans Microsoft 365

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

Le *Hameçonnage* est une attaque par courrier électronique qui tente d’accéder à des informations sensibles par le biais de messages qui paraissent provenir d’expéditeurs légitimes ou approuvés. Il existe des catégories spécifiques de hameçonnage. Par exemple :

- **Le harponnage** utilise du contenu ciblé et personnalisé qui est spécifiquement adapté aux destinataires ciblés (généralement, après la reconnaissance des destinataires par l’attaquant).

- **La whaling** est dirigée vers les cadres ou d’autres cibles à valeur élevée au sein d’une organisation pour un effet maximal.

- La compromission de messagerie professionnelle **(BEC)** utilise des expéditeurs de confiance falsifiés (responsables financiers, clients, partenaires de confiance, etc.) pour duplicher les destinataires dans l’approbation des paiements, le transfert de fonds ou la découverte de données client. Pour en savoir plus, regardez [cette vidéo.](https://www.youtube.com/watch?v=8Kn31h9HwIQ&list=PL3ZTgFEc7LystRja2GnDeUFqk44k7-KXf&index=2)

- **Les ransomware** qui chiffrent vos données et exigent un paiement pour les déchiffrer démarrent presque toujours dans les messages d’hameçonnage. La protection anti-hameçonnage ne peut pas vous aider à déchiffrer les fichiers chiffrés, mais elle peut vous aider à détecter les messages de hameçonnage initiaux associés à la campagne de ransomware. Pour plus d’informations sur la récupération suite à une attaque par ransomware, voir Récupérer à partir d’une attaque par ransomware dans [Microsoft 365.](recover-from-ransomware.md)

Avec la complexité croissante des attaques, il est même difficile pour les utilisateurs formés d’identifier les messages de hameçonnage sophistiqués. Heureusement, Exchange Online Protection (EOP) et les fonctionnalités supplémentaires de Microsoft Defender pour Office 365 peuvent vous aider.

## <a name="anti-phishing-protection-in-eop"></a>Protection anti-hameçonnage dans EOP

EOP (autrement dit, les organisations Microsoft 365 sans Microsoft Defender pour Office 365) contient des fonctionnalités qui peuvent aider à protéger votre organisation contre les menaces de hameçonnage :

- **Veille contre l’usurpation d’identité** : passez en revue les messages usurpant une identité provenant des expéditeurs dans les domaines internes et externes, et autorisez ou bloquez ces expéditeurs. Pour plus d’informations, voir [Configurer la veille contre l’usurpation d’adresse dans EOP.](learn-about-spoof-intelligence.md)

- Stratégies **anti-hameçonnage** dans EOP : activer ou désactiver la veille contre l’usurpation d’identité, activer ou désactiver l’identification des expéditeurs non authentifiés dans Outlook et spécifier l’action pour les expéditeurs usurpés bloqués (déplacer vers le dossier Courrier indésirable ou la mise en quarantaine). Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans EOP.](configure-anti-phishing-policies-eop.md)

- Authentification de messagerie implicite : EOP améliore les vérifications standard de l’authentification du courrier électronique pour le courrier entrant ([SPF,](set-up-spf-in-office-365-to-help-prevent-spoofing.md) [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC)](use-dmarc-to-validate-email.md)avec la réputation de l’expéditeur, l’historique des expéditeurs, l’historique des destinataires, l’analyse comportementale et d’autres techniques avancées pour vous aider à identifier les expéditeurs falsifiés. Si vous souhaitez en savoir plus, consultez la page [Authentification de messagerie électronique dans Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-microsoft-defender-for-office-365"></a>Protection supplémentaire contre les attaques par phishing dans Microsoft Defender pour Office 365

Microsoft Defender pour Office 365 contient des fonctionnalités supplémentaires et plus avancées de protection contre le phishing :

- Stratégies anti-hameçonnage dans Microsoft Defender pour **Office 365**: créez des stratégies personnalisées, configurez les paramètres de protection contre l’emprunt d’identité (protégez les utilisateurs et les domaines contre l’emprunt d’identité), les paramètres d’intelligence des boîtes aux lettres et les seuils d’hameçonnage avancés ajustables. Pour plus d’informations, voir [Configurer des stratégies anti-hameçonnage dans Microsoft Defender pour Office 365.](configure-atp-anti-phishing-policies.md) Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage dans EOP et les stratégies anti-hameçonnage dans Defender pour Office 365, voir stratégies anti-hameçonnage dans [Microsoft 365.](set-up-anti-phishing-policies.md)

- **Affichages campagne**: l’apprentissage automatique et d’autres heuristiques identifient et analysent les messages impliqués dans des attaques par hameçonnage coordonnées contre l’ensemble du service et de votre organisation. Pour plus d’informations, [voir Affichages des campagnes dans Microsoft Defender pour Office 365.](campaigns.md)

- **Simulateur d’attaques**: les administrateurs peuvent créer des messages de hameçonnage factices et les envoyer à des utilisateurs internes en tant qu’outil d’éducation. Pour plus d’informations, [voir Simulateur d’attaques dans Microsoft Defender pour Office 365.](attack-simulator.md)

## <a name="other-anti-phishing-resources"></a>Autres ressources anti-hameçonnage

- Pour les utilisateurs finaux : [protégez-vous contre les schémas de hameçonnage et d’autres formes de fraude en ligne.](https://support.microsoft.com/office/be0de46a-29cd-4c59-aaaf-136cf177d593)

- [Comment Microsoft 365 valide l’adresse De pour empêcher le hameçonnage.](how-office-365-validates-the-from-address.md)
