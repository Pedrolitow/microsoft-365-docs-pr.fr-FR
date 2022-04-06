---
title: Sécuriser par défaut dans Office 365
f1.keywords:
- NOCSH
ms.author: dansimp
author: dansimp
manager: dansimp
ms.date: 06/28/2021
audience: ITPro
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
description: En savoir plus sur le paramètre sécurisé par défaut dans Exchange Online Protection (EOP)
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 09395775cc5ecbd420dc7197664401c01c24d6c3
ms.sourcegitcommit: 85ce5fd0698b6f00ea1ea189634588d00ea13508
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/06/2022
ms.locfileid: "64664213"
---
# <a name="secure-by-default-in-office-365"></a>Sécuriser par défaut dans Office 365

[!INCLUDE [Prerelease information](../includes/prerelease.md)]
[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]

**S’applique à**
- [Exchange Online Protection](exchange-online-protection-overview.md)
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)
- [Microsoft 365 Defender](../defender/microsoft-365-defender.md)

« Sécurisé par défaut » est un terme utilisé pour définir les paramètres par défaut les plus sécurisés possible.

Toutefois, la sécurité doit être équilibrée avec la productivité. Cela peut inclure l’équilibrage entre les éléments suivants :

- **Facilité d’utilisation** : Paramètres ne doit pas être un frein à la productivité des utilisateurs.
- **Risque** : la sécurité peut bloquer les activités importantes.
- **Paramètres hérités** : certaines configurations pour les produits et fonctionnalités plus anciens peuvent être conservées pour des raisons métier, même si de nouveaux paramètres modernes sont améliorés.

Microsoft 365 organisations avec des boîtes aux lettres dans Exchange Online sont protégées par Exchange Online Protection (EOP). Cette protection comprend les éléments suivants :

- Les e-mails avec des programmes malveillants suspects seront automatiquement mis en quarantaine. La stratégie de quarantaine et les paramètres de la stratégie anti-programme malveillant déterminent si les destinataires sont avertis des messages de programmes malveillants mis en quarantaine. Pour plus d’informations, consultez [Configurer des stratégies anti-programme malveillant dans EOP](configure-anti-malware-policies.md).
- Les e-mails identifiés comme hameçonnage à haut niveau de confiance seront gérés en fonction de l’action de stratégie anti-courrier indésirable. Consultez [Configurer les stratégies anti-courrier indésirable dans EOP](configure-your-spam-filter-policies.md).

Pour plus d’informations sur EOP, consultez [Exchange Online Protection vue d’ensemble](exchange-online-protection-overview.md).

Étant donné que Microsoft souhaite sécuriser nos clients par défaut, certains remplacements de locataires ne sont pas appliqués pour les programmes malveillants ou le hameçonnage à haut niveau de confiance. Ces remplacements sont les suivants :

- Listes d’expéditeurs autorisées ou listes de domaines autorisés (stratégies anti-courrier indésirable)
- expéditeurs Outlook Coffre
- Liste d’autorisations IP (filtrage de connexion)
- Exchange règles de flux de courrier (également appelées règles de transport)

Vous trouverez plus d’informations sur ces remplacements dans [Créer des listes d’expéditeurs sécurisés](create-safe-sender-lists-in-office-365.md).

> [!NOTE]
> Nous avons déprécié l’action **déplacer le message vers le dossier Courrier indésirable** pour un verdict d’e-mail **de hameçonnage à haut niveau de confiance** dans les stratégies anti-courrier indésirable EOP. Les stratégies anti-courrier indésirable qui utilisent cette action pour les messages de hameçonnage à haut niveau de confiance seront converties en **message de mise en quarantaine**. L’action **de redirection du message vers l’adresse e-mail** pour les messages de hameçonnage à haut niveau de confiance n’est pas affectée.

La sécurité par défaut n’est pas un paramètre qui peut être activé ou désactivé, mais c’est la façon dont notre filtrage fonctionne de manière à empêcher les messages potentiellement dangereux ou indésirables de vos boîtes aux lettres. Les programmes malveillants et les messages de hameçonnage à haut niveau de confiance doivent être mis en quarantaine. Par défaut, seuls les administrateurs peuvent gérer les messages mis en quarantaine en tant que programmes malveillants ou hameçonnage à haut niveau de confiance, et ils peuvent également signaler des faux positifs à Microsoft à partir de là. Si vous souhaitez en savoir plus, voir [Gérer les messages et les fichiers mis en quarantaine en tant qu'administrateur dans EOP](manage-quarantined-messages-and-files.md).

## <a name="more-on-why-were-doing-this"></a>En savoir plus sur la raison pour laquelle nous faisons cela

L’esprit de sécurité par défaut est le suivant : nous prenons la même action sur le message que vous feriez si vous saviez que le message était malveillant, même lorsqu’une exception configurée autoriserait autrement la remise du message. Il s’agit de la même approche que celle que nous avons toujours utilisée sur les programmes malveillants, et nous étendons maintenant ce même comportement aux messages de hameçonnage à haut niveau de confiance.

Nos données indiquent qu’un utilisateur est 30 fois plus susceptible de cliquer sur un lien malveillant dans les messages dans le dossier Courrier indésirable que sur Quarantaine. Nos données indiquent également que le taux de faux positifs (bons messages marqués comme mauvais) pour les messages de hameçonnage à haut niveau de confiance est très faible, et les administrateurs peuvent résoudre les faux positifs avec les soumissions d’administrateur.

Nous avons également déterminé que l’expéditeur autorisé et les listes de domaines autorisés dans les stratégies anti-courrier indésirable et les expéditeurs Coffre dans Outlook étaient trop larges et causaient plus de tort que de bien.

Autrement dit, en tant que service de sécurité, nous agissons en votre nom pour empêcher vos utilisateurs d’être compromis.

## <a name="exceptions"></a>Exceptions

Vous ne devez envisager d’utiliser des remplacements que dans les scénarios suivants :

- Simulations d’hameçonnage : les attaques simulées peuvent vous aider à identifier les utilisateurs vulnérables avant qu’une attaque réelle n’affecte votre organisation. Pour empêcher le filtrage des messages de simulation d’hameçonnage, consultez [Configurer des simulations de hameçonnage tierces dans la stratégie de remise avancée](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).
- Boîtes aux lettres Security/SecOps : boîtes aux lettres dédiées utilisées par les équipes de sécurité pour obtenir des messages non filtrés (bons et mauvais). Teams pouvez ensuite vérifier s’ils contiennent du contenu malveillant. Pour plus d’informations, consultez [Configurer les boîtes aux lettres SecOps dans la stratégie de remise avancée](/microsoft-365/security/office-365-security/configure-advanced-delivery#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy).
- Filtres tiers : Secure par défaut s’applique uniquement lorsque l’enregistrement MX de votre domaine est défini sur Exchange Online Protection (contoso.mail.protection.outlook.com). S’il est défini sur un autre service ou appareil, il est possible de remplacer Secure par défaut par une [règle de transport](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-set-scl) pour contourner tout filtrage du courrier indésirable. Lorsque Microsoft détecte les messages comme étant des phish à haut niveau de confiance avec cette règle en place, ils sont toujours livrés à la boîte de réception. 
- Faux positifs : vous souhaiterez peut-être autoriser temporairement certains messages qui sont toujours analysés par Microsoft [via des soumissions d’administrateur](admin-submission.md). Comme pour tous les remplacements, il est recommandé qu’ils soient temporaires.
