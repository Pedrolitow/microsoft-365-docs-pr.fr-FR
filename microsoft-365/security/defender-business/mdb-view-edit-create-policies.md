---
title: Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises
description: Découvrez comment afficher, modifier, créer et supprimer des stratégies de cybersécurité dans Defender entreprise. Protégez vos appareils avec des stratégies de sécurité.
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-security
ms.subservice: mdb
ms.localizationpriority: medium
ms.date: 08/11/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- m365-security
- m365-initiative-defender-business
- tier1
ms.openlocfilehash: 626287dcd8c1bed6dac91d55f020d9f5a5780cff
ms.sourcegitcommit: 0283c436f3ba61a708b52b57a1955f5ea74376a3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/28/2022
ms.locfileid: "68097750"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business"></a>Afficher ou modifier des stratégies dans Microsoft Defender pour entreprises

Dans Defender pour entreprise, les paramètres de sécurité sont configurés par le biais de stratégies qui sont appliquées aux appareils. Pour simplifier votre expérience d’installation et de configuration, Defender entreprise inclut des stratégies préconfigurées pour protéger les appareils de votre entreprise dès qu’ils sont intégrés. Vous pouvez utiliser les stratégies par défaut, modifier des stratégies ou créer vos propres stratégies.

**Cet article explique comment** :

- [Obtenir une vue d’ensemble de vos stratégies par défaut](#default-policies-in-defender-for-business)
- [Afficher vos stratégies existantes](#view-your-existing-policies)
- [Modifier une stratégie existante](#edit-an-existing-policy)
- [Créer une stratégie](#create-a-new-policy)

> [!NOTE]
> Les procédures décrites dans cet article décrivent comment afficher, modifier et créer des stratégies de sécurité dans le portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)). Si vous utilisez Microsoft Intune, consultez [Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/intune/protect/endpoint-security).

## <a name="default-policies-in-defender-for-business"></a>Stratégies par défaut dans Defender entreprise

Dans Defender Entreprise, il existe deux principaux types de stratégies pour protéger les appareils de votre entreprise :

- **Stratégies de protection nouvelle génération**, qui déterminent la configuration des Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces
- **Stratégies de pare-feu**, qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils de votre entreprise

## <a name="view-your-existing-policies"></a>Afficher vos stratégies existantes

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. In the navigation pane, choose **Device configuration**. Policies are organized by operating system (such as **Windows client**) and policy type (such as **Next-generation protection** and **Firewall**). 

3. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies sous les catégories **Protection nouvelle génération** et **Pare-feu**. 

4. Pour afficher plus de détails sur une stratégie, sélectionnez son nom. Un volet latéral s’ouvre et fournit plus d’informations sur cette stratégie, telles que les appareils protégés par cette stratégie.

## <a name="edit-an-existing-policy"></a>Modifier une stratégie existante

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. In the navigation pane, choose **Device configuration**. Policies are organized by operating system (such as **Windows client**) and policy type (such as **Next-generation protection** and **Firewall**). 

3. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies sous les catégories **Protection nouvelle génération** et **Pare-feu**. 

4. Pour modifier une stratégie, sélectionnez son nom, puis choisissez **Modifier**.

5. Sur l’onglet **Informations générales**, passez en revue les informations. Si nécessaire, vous pouvez modifier la description. Sélectionnez **Suivant**.

6. Sur l’onglet **Groupes d’appareils**, déterminez les groupes d’appareils qui doivent recevoir cette stratégie.  

   - Pour conserver le groupe d’appareils sélectionné tel qu’il est, choisissez **Suivant**.
   - Pour supprimer un groupe d’appareils de la stratégie, sélectionnez **Supprimer**.
   - Pour configurer un nouveau groupe d’appareils, sélectionnez **Créer un groupe**, puis configurez votre groupe d’appareils. (Pour obtenir de l’aide sur cette tâche, consultez [Groupes d’appareils dans Defender entreprise](mdb-create-edit-device-groups.md).)
   - Pour appliquer la stratégie à un autre groupe d’appareils, sélectionnez **Utiliser le groupe existant**.

   Une fois que vous avez spécifié quels groupes d’appareils doivent recevoir la stratégie, choisissez **Suivant**.

7. Sur l’onglet **Paramètres de configuration**, passez en revue les paramètres. Si nécessaire, vous pouvez modifier les paramètres de votre stratégie. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants : 

   - [Comprendre les paramètres de configuration de nouvelle génération](mdb-next-gen-configuration-settings.md)   
   - [Paramètres du pare-feu](mdb-firewall.md)

   Une fois que vous avez spécifié vos paramètres de protection de nouvelle génération, choisissez **Suivant**.

8. Sur l’onglet **Vérifier votre stratégie**, passez en revue les informations générales, les appareils ciblés et les paramètres de configuration. 

   - Apportez les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Mettre à jour la stratégie**.

## <a name="create-a-new-policy"></a>Créer une stratégie

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. In the navigation pane, choose **Device configuration**. Policies are organized by operating system (such as **Windows client**) and policy type (such as **Next-generation protection** and **Firewall**). 

3. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies **Protection nouvelle génération**. 

4. Sous **Protection nouvelle génération** ou **Pare-feu**, sélectionnez **+ Ajouter**.

5. Sur l’onglet **Informations générales**, procédez comme suit :

   1. Spécifiez un nom et une description. Ces informations vous aideront, vous et votre équipe, à identifier la stratégie ultérieurement.
   2. Passez en revue l’ordre de stratégie et modifiez-le si nécessaire. (Pour plus d’informations, consultez [Ordre de stratégie](mdb-policy-order.md).)
   3. Cliquez sur **Suivant**. 

7. Sur l’onglet **Groupes d’appareils**, créez un groupe d’appareils ou utilisez un groupe existant. Les stratégies sont affectées aux appareils par le biais de groupes d’appareils. Voici quelques éléments à garder à l’esprit :

   - Initialement, vous pouvez uniquement disposer de votre groupe d’appareils par défaut, qui inclut les appareils utilisés par les membres de votre entreprise pour accéder aux données et aux e-mails de l’entreprise. Vous pouvez conserver et utiliser votre groupe d’appareils par défaut.
   - Créez un groupe d’appareils pour appliquer une stratégie avec des paramètres spécifiques différents de la stratégie par défaut. 
   - Lorsque vous configurez votre groupe d’appareils, vous spécifiez certains critères, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 
   - Tous les groupes d’appareils, y compris les groupes d’appareils par défaut et personnalisés que vous définissez, sont stockés dans Azure Active Directory (Azure AD).

   Pour en savoir plus sur les groupes d’appareils, consultez [Groupes d’appareils dans Defender pour Entreprises](mdb-create-edit-device-groups.md).

8. Sur l’onglet **Paramètres de configuration**, spécifiez les paramètres de votre stratégie, puis choisissez **Suivant**. Pour plus d’informations sur les paramètres individuels, consultez [Paramètres de configuration pour Defender entreprise](mdb-next-gen-configuration-settings.md).

9. Sur l’onglet **Vérifier votre stratégie**, passez en revue les informations générales, les appareils ciblés et les paramètres de configuration. 

   - Apportez les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Créer une stratégie**.


## <a name="next-steps"></a>Prochaines étapes

Choisissez une ou plusieurs des tâches suivantes :

- [Gérer les appareils](mdb-manage-devices.md)
- [Créer une stratégie dans Defender entreprise](mdb-create-new-policy.md)
- [Afficher et gérer les incidents dans Defender entreprise](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Defender entreprise](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)