---
title: Afficher ou modifier les stratégies de protection des appareils
description: Afficher, modifier, créer et supprimer des stratégies de protection des appareils dans Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 03/14/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: high
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 816b425fbbd511b68d2c21f313b497bbd4b77f8a
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65087028"
---
# <a name="view-and-edit-your-device-protection-policies"></a>Afficher et modifier vos stratégies de protection des appareils

Dans Microsoft 365 Business Premium, les paramètres de sécurité des appareils gérés sont configurés par le biais de stratégies de protection des appareils. Pour simplifier votre expérience d’installation et de configuration, vous disposez de stratégies préconfigurées qui vous aident à protéger les appareils de votre organisation dès leur intégration. Utilisez les stratégies par défaut, modifiez les stratégies existantes ou créez vos propres stratégies.

**Ce guide décrit comment** :

- Obtenir une vue d’ensemble de vos stratégies par défaut
- Afficher vos stratégies existantes
- Modifier une stratégie existante
- Créer une stratégie

## <a name="default-device-protection-policies"></a>Stratégies de protection des appareils par défaut

Microsoft 365 Business Premium comprend deux principaux types de stratégies pour protéger les appareils de votre organisation :

- **Stratégies de protection nouvelle génération**, qui déterminent la configuration des Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces

- Les **Stratégies de pare-feu**, qui déterminent le trafic réseau autorisé à effectuer par les appareils de votre organisation

Ces stratégies font partie de Microsoft Defender Entreprise, qui est inclus dans votre abonnement Microsoft 365 Business Premium.

## <a name="view-your-existing-device-protection-policies"></a>Afficher vos stratégies de protection des appareils existantes

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (par exemple, **Client Windows**) et par type de stratégie (par exemple, **Protection nouvelle génération** et **Pare-feu**). 

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Page Configuration de l’appareil.":::

3. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies sous les catégories **Protection nouvelle génération** et **Pare-feu**. 

4. Pour afficher plus de détails sur une stratégie, sélectionnez son nom. Un volet latéral s’ouvre et fournit plus d’informations sur cette stratégie, telles que les appareils protégés par cette stratégie.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Capture d’écran d’une stratégie sélectionnée dans la page Configuration de l’appareil.":::

## <a name="edit-an-existing-device-protection-policy"></a>Modifier une stratégie de protection des appareils existante

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (par exemple, **Client Windows**) et par type de stratégie (par exemple, **Protection nouvelle génération** et **Pare-feu**). 

3. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies sous les catégories **Protection nouvelle génération** et **Pare-feu**. 

4. Pour modifier une stratégie, sélectionnez son nom, puis choisissez **Modifier**.

5. Sur l’onglet **Informations générales**, passez en revue les informations. Si nécessaire, vous pouvez modifier la description. Sélectionnez **Suivant**.

6. Sur l’onglet **Groupes d’appareils**, déterminez les groupes d’appareils qui doivent recevoir cette stratégie.  

   - Pour conserver le groupe d’appareils sélectionné tel qu’il est, choisissez **Suivant**.
   - Pour supprimer un groupe d’appareils de la stratégie, sélectionnez **Supprimer**.
   - Pour configurer un nouveau groupe d’appareils, sélectionnez **Créer un groupe**, puis configurez votre groupe d’appareils. (Pour obtenir de l’aide sur cette tâche, consultez [Groupes d’appareils dans Microsoft 365 Business Premium](m365bp-device-groups-mdb.md).)
   - Pour appliquer la stratégie à un autre groupe d’appareils, sélectionnez **Utiliser le groupe existant**.

   Une fois que vous avez spécifié quels groupes d’appareils doivent recevoir la stratégie, choisissez **Suivant**.

7. Sur l’onglet **Paramètres de configuration**, passez en revue les paramètres. Si nécessaire, vous pouvez modifier les paramètres de votre stratégie. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants : 

   - [Comprendre les paramètres de configuration de nouvelle génération](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Paramètres du pare-feu](../security/defender-business/mdb-firewall.md)

   Une fois que vous avez spécifié vos paramètres de protection de nouvelle génération, choisissez **Suivant**.

8. Sur l’onglet **Vérifier votre stratégie**, passez en revue les informations générales, les appareils ciblés et les paramètres de configuration. 

   - Apportez les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Mettre à jour la stratégie**.

## <a name="create-a-new-device-protection-policy"></a>Créer une stratégie de protection des appareils

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil**. Les stratégies sont organisées par système d’exploitation (par exemple, **Client Windows**) et par type de stratégie (par exemple, **Protection nouvelle génération** et **Pare-feu**). 

3. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies **Protection nouvelle génération**. 

4. Sous **Protection nouvelle génération** ou **Pare-feu**, sélectionnez **+ Ajouter**.

5. Sur l’onglet **Informations générales**, procédez comme suit :

   1. Spécifiez un nom et une description. Ces informations vous aideront, vous et votre équipe, à identifier la stratégie ultérieurement.
   2. Passez en revue l’ordre de stratégie et modifiez-le si nécessaire. (Pour plus d’informations, consultez [Ordre de stratégie](../security/defender-business/mdb-policy-order.md).)
   3. Cliquez sur **Suivant**. 

7. Sur l’onglet **Groupes d’appareils**, créez un groupe d’appareils ou utilisez un groupe existant. Les stratégies sont affectées aux appareils par le biais de groupes d’appareils. Voici quelques éléments à garder à l’esprit :

   - Au départ, vous ne disposez peut-être que de votre groupe d’appareils par défaut, qui inclut les appareils que les membres de votre organisation utilisent pour accéder aux données et à la messagerie de l’organisation. Vous pouvez conserver et utiliser votre groupe d’appareils par défaut.
   - Créez un groupe d’appareils pour appliquer une stratégie avec des paramètres spécifiques différents de la stratégie par défaut. 
   - Lorsque vous configurez votre groupe d’appareils, vous spécifiez certains critères, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez. 
   - Tous les groupes d’appareils, y compris les groupes d’appareils par défaut et personnalisés que vous définissez, sont stockés dans Azure Active Directory (Azure AD).

   Pour en savoir plus sur les groupes d’appareils, consultez [Groupes d’appareils dans Microsoft Defender Entreprise](../security/defender-business/mdb-create-edit-device-groups.md).

8. Sur l’onglet **Paramètres de configuration**, spécifiez les paramètres de votre stratégie, puis choisissez **Suivant**. Pour plus d’informations sur les paramètres individuels, consultez [Comprendre les paramètres de configuration de nouvelle génération dans Microsoft Defender Entreprise](../security/defender-business/mdb-next-gen-configuration-settings.md).

9. Sur l’onglet **Vérifier votre stratégie**, passez en revue les informations générales, les appareils ciblés et les paramètres de configuration. 

   - Apportez les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Créer une stratégie**.

## <a name="next-objective"></a>Objectif suivant

Configurez et gérez [groupes d’appareils](m365bp-device-groups-mdb.md).

