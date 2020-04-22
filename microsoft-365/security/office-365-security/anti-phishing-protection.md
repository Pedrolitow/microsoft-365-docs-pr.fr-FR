---
title: Protection anti-hameçonnage dans Microsoft 365
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
ms.custom: TopSMBIssues
ms.collection:
- M365-security-compliance
description: Microsoft 365 offre une large gamme de protection contre les attaques par hameçonnage par défaut, ainsi que par des fonctionnalités supplémentaires dans Office 365 Advanced Threat Protection (ATP). Cette rubrique présente les ressources en ligne que vous pouvez utiliser pour découvrir et mettre en œuvre des stratégies et des options anti-hameçonnage dans Microsoft 365.
ms.openlocfilehash: fd1aaee221254c3899c15d22850e95378436a392
ms.sourcegitcommit: 2614f8b81b332f8dab461f4f64f3adaa6703e0d6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/21/2020
ms.locfileid: "43634579"
---
# <a name="anti-phishing-protection-in-microsoft-365"></a>Protection anti-hameçonnage dans Microsoft 365

*Hameçonnage* attaque par courrier électronique qui tente de dérober des informations sensibles dans les messages semblant provenir d’expéditeurs légitimes ou approuvés. Il existe des catégories spécifiques de hameçonnage. Par exemple :

- Le **Spear Phishing** utilise du contenu ciblé et personnalisé, spécialement adapté aux destinataires ciblés (en général, après la reconnaissance des destinataires par l’agresseur).

- La **baleine** est dirigée vers des cadres ou d’autres objectifs de grande valeur au sein d’une organisation pour un maximum d’effets.

- La **compromission des messages professionnels (bec)** utilise des expéditeurs approuvés falsifiés (responsables financiers, clients, partenaires approuvés, etc.) pour inciter le destinataire à approuver les paiements, transférer des fonds ou divulguer des données client.

- **Ransomware** qui chiffre vos données et demande un paiement pour les déchiffrer presque toujours dans les messages de hameçonnage. La protection anti-hameçonnage ne peut pas vous aider à déchiffrer les fichiers chiffrés, mais elle peut vous aider à détecter les messages de hameçonnage initiaux associés à la campagne de ransomware. Pour plus d’informations sur la récupération d’une attaque par ransomware, consultez [la rubrique relative à la récupération à partir d’une attaque par ransomware dans Microsoft 365](recover-from-ransomware.md).

Avec la complexité croissante des attaques, il est même difficile pour les utilisateurs formés d’identifier les messages de hameçonnage sophistiqués. Heureusement, Exchange Online Protection (EOP) et les fonctionnalités supplémentaires de la protection avancée contre les menaces (ATP) de Microsoft 365 peuvent vous aider.

## <a name="anti-phishing-protection-in-eop"></a>Protection anti-hameçonnage dans EOP

EOP (les organisations Microsoft 365 sans ATP) contient des fonctionnalités qui peuvent vous aider à protéger votre organisation contre les menaces de hameçonnage :

- **Veille contre l’usurpation d’identité** : passez en revue les messages usurpant une identité provenant des expéditeurs dans les domaines internes et externes, et autorisez ou bloquez ces expéditeurs. Pour plus d’informations, consultez la rubrique [configure usurpation Intelligence in Microsoft 365](learn-about-spoof-intelligence.md).

- **Stratégie anti-hameçonnage par défaut**: activer ou désactiver l’Assistant usurpation d’identité, activer ou désactiver l’identification de l’expéditeur non authentifié dans Outlook, et spécifier l’action pour les expéditeurs usurpés bloqués (déplacer vers le dossier courrier indésirable ou mettre en quarantaine). Pour plus d’informations, consultez la rubrique [configure anti-phishing Policies in EOP](configure-anti-phishing-policies-eop.md).

- **Authentification de messagerie implicite**: EOP améliore les vérifications d’authentification de messagerie standard pour le courrier électronique entrant ([SPF](set-up-spf-in-office-365-to-help-prevent-spoofing.md), [DKIM](use-dkim-to-validate-outbound-email.md)et [DMARC](use-dmarc-to-validate-email.md)), avec la réputation de l’expéditeur, l’historique des destinataires, l’analyse comportementale et d’autres techniques avancées pour identifier les expéditeurs falsifiés. Pour plus d’informations, consultez la rubrique [authentification de messagerie dans Microsoft 365](email-validation-and-authentication.md).

## <a name="additional-anti-phishing-protection-in-office-365-atp"></a>Protection supplémentaire contre le hameçonnage dans Office 365 ATP

La protection avancée contre les menaces Office 365 contient des fonctionnalités anti-hameçonnage supplémentaires et plus avancées :

- **Stratégies anti-hameçonnage ATP**: créez de nouvelles stratégies personnalisées, configurez les paramètres d’emprunt d’identité (protéger les utilisateurs et les domaines de l’emprunt d’identité), les paramètres d’intelligence de boîte aux lettres et les seuils de phishing avancés ajustables. Pour plus d’informations, reportez-vous à la rubrique [configure ATP anti-phishing Policies in Microsoft 365](configure-atp-anti-phishing-policies.md). Pour plus d’informations sur les différences entre les stratégies anti-hameçonnage et les stratégies anti-hameçonnage ATP, consultez la rubrique [anti-phishing Policies in Microsoft 365](set-up-anti-phishing-policies.md).

- **Vues de campagne**: l’apprentissage automatique et d’autres heuristiques identifient et analysent les messages impliqués dans des attaques de hameçonnage coordonné contre l’ensemble du service et de votre organisation. Pour plus d’informations, voir [campagne views in Office 365 DAV](campaigns.md).

- **Simulateur d’attaque**: les administrateurs peuvent créer des messages d’hameçonnage factices et les envoyer à des utilisateurs internes en tant qu’outil d’éducation. Pour plus d’informations, reportez-vous à la rubrique [Attack Simulator in Office 365 ATP](attack-simulator.md).

## <a name="other-anti-phishing-resources"></a>Autres ressources anti-hameçonnage

- Pour les utilisateurs finaux : [Protégez-vous des schémas de hameçonnage et d’autres formes de fraude en ligne](https://support.office.com/article/f84750b4-2f2c-46c3-89f6-e65f7f8c3546).

- [Comment Microsoft 365 valide l’adresse de pour empêcher le hameçonnage](how-office-365-validates-the-from-address.md).