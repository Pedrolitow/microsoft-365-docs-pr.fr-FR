---
title: Créer une stratégie dans Microsoft Defender pour les entreprises
description: Découvrez comment créer une stratégie de sécurité dans Microsoft Defender pour les entreprises
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/13/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: aaeb816b833a15e5ea7bf5d7577b062f8b5dbc6b
ms.sourcegitcommit: 74f79aacb4ffcc6cb0e315239b1493324eabb449
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/14/2021
ms.locfileid: "61508274"
---
# <a name="create-a-new-policy-in-microsoft-defender-for-business-preview"></a>Créer une stratégie dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et [](https://aka.ms/mdb-preview) sera progressivement mis en place pour les clients et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un ensemble initial de [scénarios](mdb-tutorials.md#try-these-preview-scenarios)et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 


Microsoft Defender pour Entreprise (prévisualisation) inclut des stratégies par défaut qui utilisent les paramètres recommandés pour protéger les appareils de votre entreprise dès le premier jour. Par exemple, vous avez des  stratégies de protection nouvelle génération et des stratégies de **pare-feu** intégrées à l’aide des paramètres de sécurité recommandés. Mais vous n’êtes pas limité à vos stratégies par défaut. Vous pouvez également créer de nouvelles stratégies, comme décrit dans cet article.

> [!TIP]
> Si vous souhaitez modifier une stratégie existante, voir Afficher ou modifier des stratégies [dans Microsoft Defender entreprise (prévisualisation).](mdb-view-edit-policies.md)

## <a name="create-a-new-policy"></a>Créer une stratégie

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil.** Les stratégies sont organisées par système d’exploitation (tel que **Windows client)** et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).   

3. Sélectionnez un onglet de système d’exploitation **(par exemple, Windows clients),** puis examinez la liste des **stratégies de protection nouvelle** génération. 

4. Sous **Protection nouvelle génération ou Pare-feu,** **sélectionnez + Ajouter.** 

5. Sous **l’onglet Informations générales,** prenez les mesures suivantes :

   1. Spécifiez un nom et une description. Ces informations vous aideront, vous et votre équipe, à identifier la stratégie ultérieurement.
   2. Examinez l’ordre de stratégie et modifiez-le si nécessaire. (Pour plus d’informations, consultez [l’ordre des stratégies.)](mdb-policy-order.md)
   3. Cliquez sur **Suivant**. 

7. Sous **l’onglet Groupes** d’appareils, créez un groupe d’appareils ou utilisez un groupe existant. Les stratégies sont affectées aux appareils par le biais de groupes d’appareils. Voici quelques éléments à garder à l’esprit :

   - Initialement, vous n’avez peut-être que votre groupe d’appareils par défaut, qui inclut les appareils que les membres de votre entreprise utilisent pour accéder aux données et à la messagerie de l’entreprise. Vous pouvez conserver et utiliser votre groupe d’appareils par défaut.
   - Créez un groupe d’appareils pour appliquer une stratégie avec des paramètres spécifiques qui sont différents de la stratégie par défaut. 
   - Lorsque vous définissez votre groupe d’appareils, vous spécifiez certains critères, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 
   - Tous les groupes d’appareils, y compris les groupes d’appareils par défaut et personnalisés que vous définissez, sont stockés dans Azure Active Directory (Azure AD).

   Pour en savoir plus sur les groupes d’appareils, voir . 

8. Sous **l’onglet Paramètres de configuration,** spécifiez les paramètres de votre stratégie, puis choisissez **Suivant**. Pour plus d’informations sur les paramètres individuels, voir Paramètres de configuration de [Microsoft Defender pour Entreprise (prévisualisation).](mdb-next-gen-configuration-settings.md)

9. Sous **l’onglet Examiner votre stratégie,** examinez les informations générales, les appareils ciblés et les paramètres de configuration. 

   - A apporter les modifications nécessaires en sélectionnant **Modifier.**
   - Lorsque vous êtes prêt à continuer, choisissez **Créer une stratégie.**

## <a name="next-steps"></a>Étapes suivantes

Choisissez une ou plusieurs des tâches suivantes :

- [Commencer à utiliser Defender pour les entreprises (prévisualisation)](mdb-get-started.md)

- [Afficher ou modifier des stratégies](mdb-view-edit-policies.md)

- [Gérer les appareils](mdb-manage-devices.md)

- [Afficher et gérer les incidents](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)