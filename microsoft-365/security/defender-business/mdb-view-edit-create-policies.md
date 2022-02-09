---
title: Afficher ou modifier des stratégies dans Microsoft Defender entreprise (prévisualisation)
description: Découvrez comment afficher, modifier, créer et supprimer des stratégies de protection nouvelle génération dans Microsoft Defender pour Entreprises (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/03/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: 81cd2774115478f4d85fa1878d7ce8a598600e7f
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62465420"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business-preview"></a>Afficher ou modifier des stratégies dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 

Dans Microsoft Defender pour Entreprises (prévisualisation), les paramètres de sécurité sont configurés par le biais de stratégies appliquées aux appareils. Pour simplifier votre configuration, Defender pour entreprise (prévisualisation) inclut des stratégies préconfigurées pour vous aider à protéger les appareils de votre organisation dès qu’ils sont intégrés. Vous pouvez utiliser les stratégies par défaut, modifier des stratégies ou créer vos propres stratégies.

**Cet article décrit comment** :

- [Obtenir une vue d’ensemble de vos stratégies par défaut](#default-policies-in-defender-for-business)
- [Afficher vos stratégies existantes](#view-your-existing-policies)
- [Modifier une stratégie existante](#edit-an-existing-policy)
- [Créer une stratégie](#create-a-new-policy)

>
> **Avez-vous un peu de temps ?**
> Veuillez consulter notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur Microsoft Defender entreprise</a>. Vos commentaires sont les bienvenus.
>

## <a name="default-policies-in-defender-for-business"></a>Stratégies par défaut dans Defender for Business

Dans Defender for Business (prévisualisation), il existe deux principaux types de stratégies pour protéger les appareils de votre organisation :

- **Stratégies de protection nouvelle génération**, qui déterminent la configuration Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces
- **Stratégies de** pare-feu, qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils de votre organisation


## <a name="view-your-existing-policies"></a>Afficher vos stratégies existantes

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (tel que **Windows client**) et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).  

3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients**), puis examinez la liste des stratégies sous les catégories Protection  nouvelle génération et **Pare-feu**. 

4. Pour afficher plus de détails sur une stratégie, sélectionnez son nom. Un volet latéral s’ouvre et fournit plus d’informations sur cette stratégie, par exemple sur les appareils protégés par cette stratégie.

## <a name="edit-an-existing-policy"></a>Modifier une stratégie existante

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (tel que **Windows client**) et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).  

3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients**), puis examinez la liste des stratégies sous les catégories Protection  nouvelle génération et **Pare-feu**. 

4. Pour modifier une stratégie, sélectionnez son nom, puis sélectionnez **Modifier**.

5. Sous **l’onglet Informations générales** , examinez les informations. Si nécessaire, vous pouvez modifier la description. Sélectionnez **Suivant**.

6. Sous **l’onglet Groupes d’appareils** , déterminez les groupes d’appareils qui doivent recevoir cette stratégie.  

   - Pour conserver le groupe d’appareils sélectionné tel quel, choisissez **Suivant**.
   - Pour supprimer un groupe d’appareils de la stratégie, sélectionnez **Supprimer**.
   - Pour configurer un nouveau groupe d’appareils, **sélectionnez** Créer un groupe, puis configurer votre groupe d’appareils. (Pour obtenir de l’aide sur cette tâche, voir [Groupes d’appareils dans Microsoft Defender entreprise (prévisualisation)](mdb-create-edit-device-groups.md).)
   - Pour appliquer la stratégie à un autre groupe d’appareils, **sélectionnez Utiliser un groupe existant**.

   Une fois que vous avez spécifié les groupes d’appareils qui doivent recevoir la stratégie, choisissez **Suivant**.

7. Sous **l’onglet Paramètres de configuration** , examinez les paramètres. Si nécessaire, vous pouvez modifier les paramètres de votre stratégie. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants : 

   - [Comprendre les paramètres de configuration nouvelle génération](mdb-next-gen-configuration-settings.md)   
   - [Paramètres du pare-feu](mdb-firewall.md)

   Après avoir spécifié vos paramètres de protection nouvelle génération, choisissez **Suivant**.

8. Sous **l’onglet Examiner votre stratégie** , examinez les informations générales, les appareils ciblés et les paramètres de configuration. 

   - A apporter les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, sélectionnez Mettre **à jour la stratégie**.

## <a name="create-a-new-policy"></a>Créer une stratégie

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (tel que **Windows client**) et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).  

3. Sélectionnez un onglet de système d’exploitation (**par exemple, Windows clients**), puis examinez la liste des stratégies **de protection nouvelle** génération. 

4. Sous **Protection nouvelle génération ou Pare-feu**, **sélectionnez + Ajouter**.

5. Sous **l’onglet Informations générales** , prenez les mesures suivantes :

   1. Spécifiez un nom et une description. Ces informations vous aideront, vous et votre équipe, à identifier la stratégie ultérieurement.
   2. Examinez l’ordre de stratégie et modifiez-le si nécessaire. (Pour plus d’informations, consultez [l’ordre des stratégies](mdb-policy-order.md).)
   3. Cliquez sur **Suivant**. 

7. Sous **l’onglet Groupes d’appareils** , créez un groupe d’appareils ou utilisez un groupe existant. Les stratégies sont affectées aux appareils par le biais de groupes d’appareils. Voici quelques éléments à garder à l’esprit :

   - Initialement, vous n’avez peut-être que votre groupe d’appareils par défaut, qui inclut les appareils que les membres de votre organisation utilisent pour accéder aux données et à la messagerie de l’organisation. Vous pouvez conserver et utiliser votre groupe d’appareils par défaut.
   - Créez un groupe d’appareils pour appliquer une stratégie avec des paramètres spécifiques qui sont différents de la stratégie par défaut. 
   - Lorsque vous définissez votre groupe d’appareils, vous spécifiez certains critères, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 
   - Tous les groupes d’appareils, y compris les groupes d’appareils par défaut et personnalisés que vous définissez, sont stockés dans Azure Active Directory (Azure AD).

   Pour en savoir plus sur les groupes d’appareils, voir [Groupes d’appareils dans Defender pour Entreprises (prévisualisation).](mdb-create-edit-device-groups.md)

8. Sous **l’onglet Paramètres de configuration** , spécifiez les paramètres de votre stratégie, puis choisissez **Suivant**. Pour plus d’informations sur les paramètres individuels, voir [Paramètres de configuration de Microsoft Defender pour Entreprise (prévisualisation).](mdb-next-gen-configuration-settings.md)

9. Sous **l’onglet Examiner votre stratégie** , examinez les informations générales, les appareils ciblés et les paramètres de configuration. 

   - A apporter les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Créer une stratégie**.


## <a name="next-steps"></a>Prochaines étapes

Choisissez une ou plusieurs des tâches suivantes :

- [Gérer les appareils](mdb-manage-devices.md)

- [Créer une stratégie dans Microsoft Defender entreprise (prévisualisation)](mdb-create-new-policy.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)