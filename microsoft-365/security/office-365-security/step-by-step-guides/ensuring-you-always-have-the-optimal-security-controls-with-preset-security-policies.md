---
title: Garantir que vous disposez toujours des contrôles de sécurité optimaux avec des stratégies de sécurité prédéfinies
description: Étapes permettant de garantir que vous disposez toujours des meilleurs contrôles de sécurité avec des stratégies de sécurité prédéfinies. Les stratégies prédéfinies vous permettent de sélectionner un profil de sécurité standard ou strict. Microsoft gère et gère les contrôles de sécurité dans Microsoft Defender pour Office 365 pour vous.
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
ms.openlocfilehash: 383023ea03e9b1634664b3311e7f698ce946608b
ms.sourcegitcommit: 7e551fa4e9b8b25ed62b5f406143b6b1dae08cbf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/01/2022
ms.locfileid: "67107346"
---
# <a name="ensuring-you-always-have-the-optimal-security-controls-with-preset-security-policies"></a>Garantir que vous disposez toujours des contrôles de sécurité optimaux avec des stratégies de sécurité prédéfinies

Les stratégies de sécurité prédéfinies vous permettent de sélectionner un profil de sécurité standard ou strict, et microsoft gère et gère les contrôles de sécurité dans Microsoft Defender pour Office 365 pour vous.

À mesure que de nouveaux contrôles sont ajoutés ou si le paramètre de meilleure pratique pour un contrôle de sécurité change avec l’évolution du paysage des menaces, Microsoft met automatiquement à jour les paramètres de contrôle de sécurité pour les utilisateurs affectés à une stratégie de sécurité prédéfinies Standard ou Strict. À l’aide de stratégies de préréglage de sécurité, vous disposerez toujours de la configuration recommandée et recommandée par Microsoft pour vos utilisateurs.

## <a name="what-you-will-need"></a>Ce dont vous aurez besoin
- Microsoft Defender pour Office 365 plan 1 ou supérieur (inclus dans E5)
- Autorisations suffisantes (rôle Administrateur de sécurité)
- 5 minutes pour effectuer les étapes ci-dessous.

## <a name="choosing-between-standard-and-strict-policies"></a>Choix entre les stratégies Standard et Strict

Notre stratégie de sécurité prédéfinies stricte a des limites et des paramètres plus agressifs pour les contrôles de sécurité, ce qui entraîne des détections plus agressives et implique l’administrateur dans la prise de décisions sur les e-mails bloqués qui sont publiés aux utilisateurs finaux.

- Collectez la liste de vos utilisateurs qui nécessitent des détections plus agressives, même si cela signifie que plus de messages sont signalés comme suspects. Il s’agit généralement de votre personnel exécutif, du personnel de support exécutif et d’utilisateurs historiquement très ciblés.

- Assurez-vous que les utilisateurs sélectionnés disposent d’une couverture administrateur pour passer en revue et publier des e-mails si l’utilisateur final pense que le courrier peut être correct et demande que le message leur soit remis.

- Si les critères ci-dessus sont remplis, l’utilisateur doit être placé dans la stratégie de sécurité prédéfinies strict. Sinon, l’utilisateur doit être placé dans la stratégie de sécurité prédéfinies Standard.

> [!TIP]
> Pour plus d’informations sur les polices de sécurité Standard et Strict, consultez cet [article](../../office-365-security/recommended-settings-for-eop-and-office365.md).

## <a name="enable-security-presets"></a>Activer les présélections de sécurité

Une fois que vous avez choisi entre les stratégies de préréglage de sécurité Standard et Strict pour vos utilisateurs, il faut quelques étapes supplémentaires pour affecter des utilisateurs à chaque présélection.

1. Identifiez les utilisateurs, groupes ou domaines que vous souhaitez inclure dans les présélections de sécurité Standard et Strict.
1. Connectez-vous au portail Microsoft Security à l’adresse https://security.microsoft.com.
1. Dans le volet de navigation gauche, sous **Email & collaboration**, sélectionnez **Stratégies & règles**.
1. Sélectionnez **Stratégies de menace**.
1. Sélectionnez **Stratégies de sécurité prédéfinies** sous le titre **Stratégies modèles**
1. Sélectionnez **Gérer** sous la présélection de protection Standard.
1. Sélectionnez **Tous les destinataires** à appliquer Exchange Online Protection à l’échelle du locataire, ou sélectionnez **Destinataires spécifiques** pour ajouter manuellement des utilisateurs, des groupes ou des domaines auxquels vous souhaitez appliquer la stratégie de protection. Cliquez sur le bouton **Suivant** .
1. Sélectionnez **Tous les destinataires** pour appliquer Defender pour Office 365 protection à l’échelle du locataire, ou sélectionnez **Destinataires spécifiques** pour ajouter manuellement des utilisateurs, des groupes ou des domaines auxquels vous souhaitez appliquer la stratégie de protection. Cliquez sur le bouton **Suivant** .
1. Dans la section **Protection** de l’emprunt d’identité, ajoutez des adresses e-mail & domaines pour vous protéger contre les attaques d’emprunt d’identité, puis ajoutez les expéditeurs et domaines approuvés auxquelles vous ne souhaitez pas appliquer la protection d’emprunt d’identité, puis appuyez sur **Suivant**.
3. Cliquez sur le bouton **Confirmer** .
4. Sélectionnez le lien **Gérer** dans la présélection De protection stricte.
5. Répétez les étapes 7 à 10, mais pour les utilisateurs, une protection stricte doit être appliquée. (le cas échéant)
7. Cliquez sur le bouton **Confirmer** .

> [!TIP]
> Pour en savoir plus sur les polcies prédéfinies, cliquez [ici](../../office-365-security/preset-security-policies.md)

## <a name="next-steps"></a>Étapes suivantes

Utilisez l’analyseur de configuration pour déterminer si vos utilisateurs sont configurés conformément aux meilleures pratiques de Microsoft.

> [!TIP]
> L’analyseur de configuration permet aux administrateurs de rechercher et de corriger les stratégies de sécurité où les paramètres sont inférieurs aux paramètres de profil de protection standard ou strict dans les stratégies de sécurité prédéfinies. En savoir plus sur l’analyseur de configuration [ici](../../office-365-security/configuration-analyzer-for-security-policies.md).

Les présélections sécurisées sont toujours suggérées, car elles garantissent que vous appliquez toujours les meilleures pratiques de Microsoft. Toutefois, dans certains cas, des configurations personnalisées sont requises. Découvrez les stratégies personnalisées [ici](../../office-365-security/tenant-wide-setup-for-increased-security.md).

