---
title: Comment configurer des autorisations et des stratégies de quarantaine
description: Étapes de configuration des stratégies de quarantaine et des autorisations entre différents groupes, notamment AdminOnlyPolicy, accès limité, accès complet et fourniture aux administrateurs de sécurité et aux utilisateurs d’un moyen simple de gérer les dossiers faux positifs.
search.product: ''
search.appverid: ''
ms.prod: m365-security
ms.mktglfcycl: deploy
ms.sitesec: library
ms.pagetype: security
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection: m365-guidance-templates
ms.topic: how-to
ms.technology: mdo
ms.openlocfilehash: 709656cafc15333559ac8abe50e21ccde690d09a
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67106950"
---
# <a name="how-to-configure-quarantine-permissions-and-policies"></a>Comment configurer des autorisations et des stratégies de quarantaine

Il est essentiel de fournir aux administrateurs de sécurité et aux utilisateurs un moyen très simple de gérer les dossiers faux positifs, compte tenu de la demande accrue d’une posture de sécurité plus agressive avec l’évolution du travail hybride. En adoptant une approche normative, les administrateurs et les utilisateurs peuvent y parvenir avec les conseils ci-dessous.

> [!TIP]
> Pour une courte vidéo destinée aux administrateurs qui tentent de définir des autorisations et des stratégies de quarantaine, [consultez ce lien](https://www.youtube.com/watch?v=vnar4HowfpY). Si vous êtes un utilisateur final, choisissez cette [vue d’ensemble de 1 minute](https://www.youtube.com/watch?v=s-vozLO43rI) du processus.

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin
- Autorisations suffisantes (rôle Administrateur de sécurité)
- 5 minutes pour effectuer les étapes ci-dessous.

## <a name="creating-custom-quarantine-policies-with-request-release-flow"></a>Création de stratégies de quarantaine personnalisées avec le flux de mise en production de la demande

Nos stratégies personnalisées permettent aux administrateurs de décider quels éléments leurs utilisateurs peuvent trier dans le dossier ***Faux positif** _ avec une possibilité étendue de permettre à l’utilisateur de demander la _release* de ces éléments à partir du dossier.

1. Déterminez la catégorie de verdicts (en bloc, spam, hameçonnage, hameçonnage ou programme malveillant) des éléments que vous souhaitez que votre utilisateur trie et non trie.
1. Pour les catégories que vous ne souhaitez pas que les utilisateurs trient, affectez les éléments à **AdminOnlyPolicy**. Quant à la catégorie que vous souhaitez que les utilisateurs trient avec un accès limité, vous pouvez *créer une stratégie personnalisée* avec un accès de mise en production de demande et affecter des utilisateurs à cette catégorie.
1. Il est **fortement recommandé** d’affecter des programmes malveillants et des éléments de hameçonnage à haute confiance à **AdminOnlyPolicy, d’accorder** aux éléments de hameçonnage de confiance régulière un *accès limité avec la mise en production des demandes*, tandis que le courrier indésirable et le courrier indésirable peuvent être laissés en tant qu’accès complet pour les utilisateurs.

> [!IMPORTANT]
> Pour plus d’informations sur la façon dont des stratégies personnalisées granulaires peuvent être créées, consultez [Stratégies de quarantaine - Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md).

## <a name="assigning-quarantine-policies-and-enabling-notification-with-organization-branding"></a>Affectation de stratégies de quarantaine et activation de la notification avec la personnalisation de l’organisation

Une fois qu’il a été décidé que les catégories d’éléments que les utilisateurs peuvent trier ou ne pas trier, et créé les stratégies de quarantaine correspondantes, les administrateurs doivent affecter ces stratégies aux utilisateurs respectifs et activer les notifications.

1. Identifiez les utilisateurs, les groupes ou les domaines que vous souhaitez inclure dans la catégorie *d’accès complet* par rapport à la catégorie d’accès *limité* ou à la catégorie *Administration uniquement*.
1. Connectez-vous au [portail de sécurité Microsoft](https://security.microsoft.com).
1. Sélectionnez **Email &** stratégies de collaboration  > **& règles**.
1. Sélectionnez **Stratégies de menace**.
1. Sélectionnez chacune des options **suivantes : stratégies anti-courrier indésirable**, **stratégie anti-hameçonnage**, **stratégie anti-programme malveillant**.
1. Sélectionnez **Créer une stratégie** , puis choisissez **Entrant**.
1. Ajoutez le nom de la stratégie, les utilisateurs, les groupes ou les domaines auxquels appliquer la stratégie et **Suivant**.
1. Sous l’onglet **Actions** , sélectionnez **Message de quarantaine** pour les catégories. Vous remarquerez un panneau supplémentaire pour *sélectionner la stratégie de quarantaine*. Utilisez cette liste déroulante pour sélectionner la stratégie de quarantaine que vous avez créée précédemment.
1. Passez à la section **Révision** , puis cliquez sur le bouton **Confirmer** pour créer la nouvelle stratégie.
1. Répétez les mêmes étapes pour les autres stratégies : **stratégie anti-hameçonnage**, stratégie **anti-programme malveillant** et **stratégie de pièce jointe sécurisée**.

> [!TIP]
> Pour plus d’informations sur ce que vous avez appris jusqu’à présent, consultez [Configurer les stratégies de filtrage du courrier indésirable - Office 365 | ](../../office-365-security/configure-your-spam-filter-policies.md)|  Microsoft Docs [Configurer des stratégies anti-hameçonnage dans EOP - Office 365 | ](../../office-365-security/configure-anti-phishing-policies-eop.md) |  Microsoft Docs [Configurer les stratégies anti-programme malveillant - Office 365 | ](../../office-365-security/configure-anti-malware-policies.md)|  Microsoft Docs [Set up Safe Attachments policies in Microsoft Defender pour Office 365 - Office 365 | Microsoft Docs](../../office-365-security/set-up-safe-attachments-policies.md)

## <a name="next-steps"></a>Étapes suivantes

- Utilisez **la stratégie globale** disponible dans la stratégie de quarantaine pour activer le logo, le nom complet et la clause d’exclusion de responsabilité de votre organisation.
- Définissez également la **fréquence utilisateur sur 1 jour** pour la notification de mise en quarantaine.

## <a name="more-information"></a>Plus d’informations

En savoir plus sur les paramètres de personnalisation et de notification de l’organisation ici [Stratégies de quarantaine - Office 365 | Microsoft Docs](../../office-365-security/quarantine-policies.md)
