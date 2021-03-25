---
title: Sécurisé par défaut dans Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: conceptual
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: En savoir plus sur le paramètre sécurisé par défaut dans Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: f1b495a9c985077dfc88d1da7a221bb60ca10df9
ms.sourcegitcommit: dcb97fbfdae52960ae62b6faa707a05358193ed5
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/25/2021
ms.locfileid: "51204303"
---
# <a name="secure-by-default-in-office-365"></a>Sécurisé par défaut dans Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

« Sécurisé par défaut » est un terme utilisé pour définir les paramètres par défaut les plus sécurisés possible.

Toutefois, la sécurité doit être équilibrée avec la productivité. Cela peut inclure l’équilibrage entre :

- **Convivialité :** les paramètres ne doivent pas être contre la productivité des utilisateurs.
- **Risque :** la sécurité peut bloquer les activités importantes.
- **Paramètres hérités**: certaines configurations pour les anciens produits et fonctionnalités peuvent avoir besoin d’être conservées pour des raisons professionnelles, même si les nouveaux paramètres modernes sont améliorés.

Les organisations Microsoft 365 avec boîtes aux lettres dans Exchange Online sont protégées par Exchange Online Protection (EOP). Cette protection inclut :

- Les messages électroniques avec des programmes malveillants suspectés sont automatiquement mis en quarantaine et les destinataires sont avertis. Voir [Configurer des stratégies anti-programme malveillant dans EOP.](configure-anti-malware-policies.md)
- Les messages électroniques identifiés comme étant du hameçonnage à haut niveau de confiance seront gérés en fonction de l’action de stratégie anti-courrier indésirable. Voir [Configurer des stratégies anti-courrier indésirable dans EOP.](configure-your-spam-filter-policies.md)

Pour plus d’informations sur EOP, voir [vue d’ensemble d’Exchange Online Protection.](exchange-online-protection-overview.md)

Étant donné que Microsoft souhaite sécuriser nos clients par défaut, certaines substitutions de clients ne sont pas appliquées pour les programmes malveillants ou le hameçonnage à haut niveau de confiance. Ces substitutions sont les suivantes :

- Listes d’expéditeurs autorisés ou listes de domaines autorisés (stratégies anti-courrier indésirable)
- Expéditeurs sécurisés Outlook
- Liste d’adresses IP permises (filtrage des connexions)

Pour plus d’informations sur ces remplacements, voir [Créer des listes d’expéditeurs sûrs.](create-safe-sender-lists-in-office-365.md)

> [!NOTE]
> Nous sommes en train de déprécier l’action Déplacer le **message** vers le dossier Courrier indésirable pour un **verdict** de courrier de hameçonnage à haut niveau de confiance dans les stratégies EOP anti-courrier indésirable. Les stratégies anti-courrier indésirable qui utilisent cette action pour les messages de hameçonnage à haut niveau de confiance seront converties en message de mise **en quarantaine.** **L’action de redirection vers l’adresse e-mail** pour les messages de hameçonnage à haut niveau de confiance n’est pas affectée.

La sécurité par défaut n’est pas un paramètre qui peut être allumé ou désactivé, mais la façon dont notre filtrage est prêt à l’emploi pour empêcher les messages potentiellement dangereux ou indésirables de sortir de vos boîtes aux lettres. Les programmes malveillants et les messages de hameçonnage à haut niveau de confiance doivent être mis en quarantaine. Seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants ou hameçonnage à haut niveau de confiance, et ils peuvent également signaler des faux positifs à Microsoft à partir de là. Pour plus d’informations, voir Gérer les fichiers et les messages mis en quarantaine en tant [qu’administrateur dans EOP](manage-quarantined-messages-and-files.md)

## <a name="more-on-why-were-doing-this"></a>En savoir plus sur la raison de cette situation

L’objectif de la sécurité par défaut est le suivant : nous prenons la même action sur le message que si vous connaissiez le message malveillant, même lorsqu’une exception configurée autoriserait sinon la livraison du message. Il s’agit de la même approche que nous avons toujours utilisée sur les programmes malveillants, et maintenant, nous étendons ce comportement aux messages de hameçonnage à haut niveau de confiance.

Nos données indiquent qu’un utilisateur a 30 fois plus de chances de cliquer sur un lien malveillant dans les messages du dossier Courrier indésirable que de mettre en quarantaine. Nos données indiquent également que le taux de faux positifs (messages positifs marqués comme faux) pour les messages de hameçonnage à niveau de confiance élevé est très faible, et que les administrateurs peuvent résoudre les faux positifs avec des envois d’administrateur.

Nous avons également déterminé que les listes d’expéditeurs et de domaines autorisés dans les stratégies anti-courrier indésirable et les expéditeurs autorisés dans Outlook étaient trop larges et causaient plus de dommages que de bien.

Autrement dit : en tant que service de sécurité, nous agissant en votre nom pour empêcher la compromissions vos utilisateurs. 

## <a name="exceptions"></a>Exceptions

La seule substitution permettant aux messages de hameçonnage à haut niveau de confiance de contourner le filtrage est les règles de flux de messagerie Exchange (également appelées règles de transport). Pour utiliser des règles de flux de messagerie pour contourner le filtrage, voir Utiliser des règles de flux de messagerie pour définir le [SCL dans les messages.](use-mail-flow-rules-to-set-the-spam-confidence-level-scl-in-messages.md)

Vous ne devez envisager d’utiliser des substitutions que dans les scénarios suivants :

- Simulations de hameçonnage : les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’impacte votre organisation.
- Boîtes aux lettres De sécurité/SecOps : boîtes aux lettres dédiées utilisées par les équipes de sécurité pour obtenir des messages non filtrés (bonnes et mauvaises). Les équipes peuvent ensuite examiner s’ils contiennent du contenu malveillant.
- Filtres tiers : la sécurité par défaut ne s’applique pas lorsque l’enregistrement MX du domaine ne pointe pas vers Office 365.
- Faux positifs : vous souhaitez peut-être autoriser temporairement certains messages en cours d’analyse par Microsoft [via des envois d’administrateurs.](admin-submission.md) Comme pour toutes les substitutions, il est recommandé qu’elles soient temporaires.
