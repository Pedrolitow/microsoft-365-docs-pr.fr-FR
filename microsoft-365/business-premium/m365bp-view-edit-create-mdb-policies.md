---
title: Afficher ou modifier des stratégies de protection des appareils
description: Afficher, modifier, créer et supprimer des stratégies de protection des appareils dans Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/08/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
- m365-initiative-defender-business
ms.openlocfilehash: ba322493b3900c099ab5525f052604604ef0ac23
ms.sourcegitcommit: 3fb76db6b34e24569417f4c8a41b99f46a780389
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2022
ms.locfileid: "63525262"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Afficher et modifier vos stratégies de protection des appareils

Dans Microsoft 365 Business Premium, les paramètres de sécurité des appareils gérés sont configurés par le biais de stratégies de protection des appareils. Pour simplifier votre configuration, vous avez des stratégies préconfigurées qui peuvent vous aider à protéger les appareils de votre organisation dès qu’ils sont intégrés. Vous pouvez utiliser les stratégies par défaut, modifier des stratégies ou créer vos propres stratégies.

**Cet article décrit comment** :

- Obtenir une vue d’ensemble de vos stratégies par défaut
- Afficher vos stratégies existantes
- Modifier une stratégie existante
- Créer une stratégie

## <a name="default-device-protection-policies"></a>Stratégies de protection des appareils par défaut

Microsoft 365 Business Premium comprend deux principaux types de stratégies pour protéger les appareils de votre organisation :

- **Stratégies de protection nouvelle génération**, qui déterminent la façon dont Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces sont configurées

- **Stratégies de** pare-feu, qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils de votre organisation

Ces stratégies font partie de Microsoft Defender entreprise, qui est inclus dans votre abonnement Microsoft 365 Business Premium abonnement.

## <a name="view-your-existing-device-protection-policies"></a>Afficher vos stratégies de protection des appareils existantes

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (tel que **Windows client**) et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).  

3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients**), puis examinez la liste des stratégies sous les catégories Protection  nouvelle génération et **Pare-feu**. 

4. Pour afficher plus de détails sur une stratégie, sélectionnez son nom. Un volet latéral s’ouvre et fournit plus d’informations sur cette stratégie, par exemple sur les appareils protégés par cette stratégie.

## <a name="edit-an-existing-device-protection-policy"></a>Modifier une stratégie de protection des appareils existante

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (tel que **Windows client**) et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).  

3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients**), puis examinez la liste des stratégies sous les catégories Protection  nouvelle génération et **Pare-feu**. 

4. Pour modifier une stratégie, sélectionnez son nom, puis sélectionnez **Modifier**.

5. Sous **l’onglet Informations générales** , examinez les informations. Si nécessaire, vous pouvez modifier la description. Sélectionnez **Suivant**.

6. Sous **l’onglet Groupes d’appareils** , déterminez les groupes d’appareils qui doivent recevoir cette stratégie.  

   - Pour conserver le groupe d’appareils sélectionné tel quel, choisissez **Suivant**.
   - Pour supprimer un groupe d’appareils de la stratégie, sélectionnez **Supprimer**.
   - Pour configurer un nouveau groupe d’appareils, **sélectionnez** Créer un groupe, puis configurer votre groupe d’appareils. (Pour obtenir de l’aide sur cette tâche, consultez [Groupes d’appareils Microsoft 365 Business Premium](m365bp-device-groups-mdb.md).)
   - Pour appliquer la stratégie à un autre groupe d’appareils, **sélectionnez Utiliser un groupe existant**.

   Une fois que vous avez spécifié les groupes d’appareils qui doivent recevoir la stratégie, choisissez **Suivant**.

7. Sous **l’onglet Paramètres de configuration** , examinez les paramètres. Si nécessaire, vous pouvez modifier les paramètres de votre stratégie. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants : 

   - [Comprendre les paramètres de configuration nouvelle génération](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Paramètres du pare-feu](../security/defender-business/mdb-firewall.md)

   Après avoir spécifié vos paramètres de protection nouvelle génération, choisissez **Suivant**.

8. Sous **l’onglet Examiner votre stratégie** , examinez les informations générales, les appareils ciblés et les paramètres de configuration. 

   - A apporter les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, sélectionnez Mettre **à jour la stratégie**.

## <a name="create-a-new-device-protection-policy"></a>Créer une stratégie de protection des appareils

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (tel que **Windows client**) et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).  

3. Sélectionnez un onglet de système d’exploitation (**par exemple, Windows clients**), puis examinez la liste des stratégies **de protection nouvelle** génération. 

4. Sous **Protection nouvelle génération ou Pare-feu**, **sélectionnez + Ajouter**.

5. Sous **l’onglet Informations générales** , prenez les mesures suivantes :

   1. Spécifiez un nom et une description. Ces informations vous aideront, vous et votre équipe, à identifier la stratégie ultérieurement.
   2. Examinez l’ordre de stratégie et modifiez-le si nécessaire. (Pour plus d’informations, consultez [l’ordre des stratégies](../security/defender-business/mdb-policy-order.md).)
   3. Cliquez sur **Suivant**. 

7. Sous **l’onglet Groupes d’appareils** , créez un groupe d’appareils ou utilisez un groupe existant. Les stratégies sont affectées aux appareils par le biais de groupes d’appareils. Voici quelques éléments à garder à l’esprit :

   - Initialement, vous n’avez peut-être que votre groupe d’appareils par défaut, qui inclut les appareils que les membres de votre organisation utilisent pour accéder aux données et à la messagerie de l’organisation. Vous pouvez conserver et utiliser votre groupe d’appareils par défaut.
   - Créez un groupe d’appareils pour appliquer une stratégie avec des paramètres spécifiques qui sont différents de la stratégie par défaut. 
   - Lorsque vous définissez votre groupe d’appareils, vous spécifiez certains critères, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 
   - Tous les groupes d’appareils, y compris les groupes d’appareils par défaut et personnalisés que vous définissez, sont stockés dans Azure Active Directory (Azure AD).

   Pour en savoir plus sur les groupes d’appareils, voir [Groupes d’appareils dans Microsoft Defender pour Entreprises](../security/defender-business/mdb-create-edit-device-groups.md).

8. Sous **l’onglet Paramètres de configuration** , spécifiez les paramètres de votre stratégie, puis choisissez **Suivant**. Pour plus d’informations sur les paramètres individuels, voir [Comprendre les paramètres de configuration nouvelle génération dans Microsoft Defender pour les entreprises](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. Sous **l’onglet Examiner votre stratégie** , examinez les informations générales, les appareils ciblés et les paramètres de configuration. 

   - A apporter les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Créer une stratégie**.


## <a name="next-steps"></a>Prochaines étapes

[Groupes d’appareils dans Microsoft 365 Business Premium](m365bp-device-groups-mdb.md)