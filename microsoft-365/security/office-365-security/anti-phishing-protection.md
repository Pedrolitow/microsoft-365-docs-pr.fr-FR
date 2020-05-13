---
title: Protection anti-hameçonnage
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
ms.assetid: 75af74b2-c7ea-4556-a912-8c48e07271d3
ms.collection:
- M365-security-compliance
ms.custom:
- TopSMBIssues
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les fonctionnalités de protection anti-hameçonnage dans Exchange Online Protection (EOP) et Office 365 Advanced Threat Protection (Office 365 ATP).
ms.openlocfilehash: c1b9332fc35997dfe1cbfdfbef79e2d7beed736f
ms.sourcegitcommit: 93c0088d272cd45f1632a1dcaf04159f234abccd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/12/2020
ms.locfileid: "44208970"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Protection anti-hameçonnage dans Microsoft 365

*Hameçonnage* attaque par courrier électronique qui tente de dérober des informations sensibles dans les messages semblant provenir d’expéditeurs légitimes ou approuvés. Il existe des catégories spécifiques de hameçonnage. Par exemple :

- Le **Spear Phishing** utilise du contenu ciblé et personnalisé, spécialement adapté aux destinataires ciblés (en général, après la reconnaissance des destinataires par l’agresseur).

- La **baleine** est dirigée vers des cadres ou d’autres objectifs de grande valeur au sein d’une organisation pour un maximum d’effets.

- La **compromission des messages professionnels (bec)** utilise des expéditeurs approuvés falsifiés (responsables financiers, clients, partenaires approuvés, etc.) pour inciter le destinataire à approuver les paiements, transférer des fonds ou divulguer des données client.

- **Ransomware** qui chiffre vos données et demande un paiement pour les déchiffrer presque toujours dans les messages de hameçonnage. La protection anti-hameçonnage ne peut pas vous aider à déchiffrer les fichiers chiffrés, mais elle peut vous aider à détecter les messages de hameçonnage initiaux associés à la campagne de ransomware. Pour plus d’informations sur la récupération d’une attaque par ransomware, consultez [la rubrique relative à la récupération à partir d’une attaque par ransomware dans Microsoft 365](recover-from-ransomware.md).

Avec la complexité croissante des attaques, il est même difficile pour les utilisateurs formés d’identifier les messages de hameçonnage sophistiqués. Heureusement, Exchange Online Protection (EOP) et les fonctionnalités supplémentaires d’Office 365 Advanced Threat Protection (Office 365 ATP) peuvent vous aider.

## <a name="anti-phishing-protection-in-eop"></a>Protection anti-hameçonnage dans EOP

EOP (les organisations Microsoft 365 sans ATP) contient des fonctionnalités qui peuvent vous aider à protéger votre organisation contre les menaces de hameçonnage :

- **Veille contre l’usurpation d’identité** : passez en revue les messages usurpant une identité provenant des expéditeurs dans les domaines internes et externes, et autorisez ou bloquez ces expéditeurs. Pour plus d’informations, consultez la rubrique [configure usurpation Intelligence in EOP](learn-about-spoof-intelligence.md).

- **Stratégies de détection d’hameçonnage dans EOP**: activation ou désactivation de l’intelligence des usurpations, activation ou désactivation de l’identification des expéditeurs non authentifiés dans Outlook, et spécification de l’action pour les expéditeurs usurpés bloqués (déplacer vers le dossier courrier indésirable ou mise en quarantaine). Pour plus d’informations, consultez la rubrique [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md).

- **Authentification de messagerie implicite**: EOP améliore les vérifications d’authentification de messagerie standard pour le courrier électronique entrant ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md)), avec la réputation de l’expéditeur, l’historique des destinataires, l’analyse comportementale et d’autres techniques avancées pour identifier les expéditeurs falsifiés. Si vous souhaitez en savoir plus, consultez la page [Authentification de messagerie électronique dans Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-office-365-atp"></a>Protection supplémentaire contre le hameçonnage dans Office 365 ATP

La protection avancée contre les menaces Office 365 contient des fonctionnalités anti-hameçonnage supplémentaires et plus avancées :

- **Stratégies anti-hameçonnage ATP**: créez de nouvelles stratégies personnalisées, configurez les paramètres d’emprunt d’identité (protéger les utilisateurs et les domaines de l’emprunt d’identité), les paramètres d’intelligence de boîte aux lettres et les seuils de phishing avancés ajustables. Pour plus d’informations, reportez-vous à la rubrique [configure ATP anti-phishing Policies in Microsoft 365](configure-atp-anti-phishing-policies.md). Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage et les stratégies anti-hameçonnage ATP, consultez la rubrique [anti-phishing Policies in Microsoft 365](set-up-anti-phishing-policies.md).

- **Vues de campagne**: l’apprentissage automatique et d’autres heuristiques identifient et analysent les messages impliqués dans des attaques de hameçonnage coordonné contre l’ensemble du service et de votre organisation. Pour plus d’informations, voir [campagne views in Office 365 DAV](campaigns.md).

- **Simulateur d’attaque**: les administrateurs peuvent créer des messages d’hameçonnage factices et les envoyer à des utilisateurs internes en tant qu’outil d’éducation. Pour plus d’informations, reportez-vous à la rubrique [Attack Simulator in Office 365 ATP](attack-simulator.md).

## <a name="other-anti-phishing-resources"></a>Autres ressources anti-hameçonnage

- Pour les utilisateurs finaux : [Protégez-vous des schémas de hameçonnage et d’autres formes de fraude en ligne](https://support.office.com/article/f84750b4-2f2c-46c3-89f6-e65f7f8c3546).

- [Comment Microsoft 365 valide l’adresse de pour empêcher le hameçonnage](how-office-365-validates-the-from-address.md).
