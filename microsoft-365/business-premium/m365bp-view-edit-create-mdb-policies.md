---
title: Afficher ou modifier les stratégies de protection des appareils
description: Afficher, modifier, créer et supprimer des stratégies de protection des appareils dans Microsoft 365 Business Premium
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.service: microsoft-365-business
ms.subservice: business-premium
ms.localizationpriority: high
ms.date: 09/14/2022
ms.reviewer: shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 7956c330b2df483ae2459f2d4fc23a54e8387c4e
ms.sourcegitcommit: b1ed6470645455c2f1fcf467450debc622c40147
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/15/2022
ms.locfileid: "67710914"
---
# <a name="view-and-edit-device-protection-policies"></a>Afficher et modifier les stratégies de protection des appareils

Dans Microsoft 365 Business Premium, les paramètres de sécurité des appareils gérés sont configurés via des stratégies de protection des appareils dans le portail Microsoft 365 Defender ou dans le Centre d’administration Microsoft Endpoint Manager. Pour simplifier l’installation et la configuration, il existe des stratégies préconfigurées qui protègent les appareils de votre organisation dès leur intégration. Vous pouvez utiliser les stratégies par défaut, modifier des stratégies existantes ou créer vos propres stratégies.

**Ce guide décrit comment** :

- Obtenir une vue d’ensemble de vos stratégies par défaut
- Utilisez des stratégies d’appareil dans le portail Microsoft 365 Defender ou le Centre d’administration Microsoft Endpoint Manager (Intune).

## <a name="about-the-default-device-protection-policies"></a>À propos des stratégies de protection des appareils par défaut

Microsoft 365 Business Premium comprend deux principaux types de stratégies pour protéger les appareils de votre organisation :

- **Stratégies de protection de nouvelle génération**, qui déterminent comment les Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces sont configurées.

- Les **Stratégies de pare-feu**, qui déterminent le trafic réseau autorisé à effectuer par les appareils de votre organisation.

Ces stratégies font partie de Microsoft Defender entreprise, inclus dans votre abonnement Microsoft 365 Business Premium. Des informations sont fournies pour l’utilisation des stratégies dans le portail Microsoft 365 Defender ou dans le Centre d’administration Microsoft Endpoint Manager.

## <a name="working-with-device-polices-in-the-microsoft-365-defender-portal"></a>Utilisation des stratégies d’appareil dans le portail Microsoft 365 Defender

Les détails suivants s’appliquent à l’utilisation de vos stratégies dans le centre de sécurité.

### <a name="view-existing-device-protection-policies"></a>Afficher les stratégies de protection des appareils existantes

Pour afficher vos stratégies de protection des appareils existantes dans le portail Microsoft 365 Defender :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

1. Dans le volet de navigation, choisissez **Configuration du dispositif**. Les stratégies sont organisées par système d'exploitation (comme le **client Windows**) et par type de stratégie (comme la **protection de nouvelle génération** et le **pare-feu**).

    :::image type="content" source="../media/mdb-deviceconfiguration.png" lightbox="../media/mdb-deviceconfiguration.png" alt-text="Page Configuration de l’appareil.":::

1. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies sous les catégories **Protection nouvelle génération** et **Pare-feu**.

1. Pour afficher plus de détails sur une stratégie, sélectionnez son nom. Un volet latéral s’ouvre et fournit plus d’informations sur cette stratégie, telles que les appareils protégés par cette stratégie.

   :::image type="content" source="../media/mdb-deviceconfig-selectedpolicy.png" lightbox="../media/mdb-deviceconfig-selectedpolicy.png" alt-text="Capture d’écran d’une stratégie sélectionnée dans la page Configuration de l’appareil.":::

### <a name="edit-an-existing-device-protection-policy"></a>Modifier une stratégie de protection des appareils existante

Pour modifier une stratégie d’appareil :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

1. Dans le volet de navigation, choisissez **Configuration du dispositif**. Les stratégies sont organisées par système d'exploitation (comme le **client Windows**) et par type de stratégie (comme la **protection de nouvelle génération** et le **pare-feu**).

1. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies sous les catégories **Protection nouvelle génération** et **Pare-feu**.

1. Pour modifier une stratégie, sélectionnez son nom, puis choisissez **Modifier**.

1. Sur l’onglet **Informations générales**, passez en revue les informations. Si nécessaire, vous pouvez modifier la description. Sélectionnez **Suivant**.

1. Sur l’onglet **Groupes d’appareils**, déterminez les groupes d’appareils qui doivent recevoir cette stratégie.  

   - Pour conserver le groupe d’appareils sélectionné tel qu’il est, choisissez **Suivant**.
   - Pour supprimer un groupe d’appareils de la stratégie, sélectionnez **Supprimer**.
   - Pour configurer un nouveau groupe d’appareils, sélectionnez **Créer un groupe**, puis configurez votre groupe d’appareils. (Pour obtenir de l’aide sur cette tâche, consultez [Groupes d’appareils dans Microsoft 365 Business Premium](m365bp-device-groups-mdb.md).)
   - Pour appliquer la stratégie à un autre groupe d’appareils, sélectionnez **Utiliser le groupe existant**.

   Une fois que vous avez spécifié quels groupes d’appareils doivent recevoir la stratégie, choisissez **Suivant**.

1. Sur l’onglet **Paramètres de configuration**, passez en revue les paramètres. Si nécessaire, vous pouvez modifier les paramètres de votre stratégie. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants : 

   - [Comprendre les paramètres de configuration de nouvelle génération](../security/defender-business/mdb-next-gen-configuration-settings.md)   
   - [Paramètres du pare-feu](../security/defender-business/mdb-firewall.md)

   Une fois que vous avez spécifié vos paramètres de protection de nouvelle génération, choisissez **Suivant**.

1. Sur l’onglet **Vérifier votre stratégie**, passez en revue les informations générales, les appareils ciblés et les paramètres de configuration.

   - Apportez les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Mettre à jour la stratégie**.

### <a name="create-a-new-device-protection-policy"></a>Créer une stratégie de protection des appareils

Pour créer une stratégie de protection des appareils :

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)), puis connectez-vous.

1. Dans le volet de navigation, choisissez **Configuration du dispositif**. Les stratégies sont organisées par système d'exploitation (comme le **client Windows**) et par type de stratégie (comme la **protection de nouvelle génération** et le **pare-feu**).

1. Sélectionnez un onglet de système d’exploitation (par exemple, **Clients Windows**), puis passez en revue la liste des stratégies **Protection nouvelle génération**.

1. Sous **Protection nouvelle génération** ou **Pare-feu**, sélectionnez **+ Ajouter**.

1. Sur l’onglet **Informations générales**, procédez comme suit :

   1. Spécifiez un nom et une description. Ces informations vous aideront, vous et votre équipe, à identifier la stratégie ultérieurement.
   2. Passez en revue l’ordre de stratégie et modifiez-le si nécessaire. (Pour plus d’informations, consultez [Ordre de stratégie](../security/defender-business/mdb-policy-order.md).)
   3. Cliquez sur **Suivant**.

1. Sur l’onglet **Groupes d’appareils**, créez un groupe d’appareils ou utilisez un groupe existant. Les stratégies sont affectées aux appareils par le biais de groupes d’appareils. Voici quelques éléments à garder à l’esprit :

   - Au départ, vous ne disposez peut-être que de votre groupe d’appareils par défaut, qui inclut les appareils que les membres de votre organisation utilisent pour accéder aux données et à la messagerie de l’organisation. Vous pouvez conserver et utiliser votre groupe d’appareils par défaut.
   - Créez un groupe d’appareils pour appliquer une stratégie avec des paramètres spécifiques différents de la stratégie par défaut.
   - Lorsque vous configurez votre groupe d’appareils, vous spécifiez certains critères, tels que la version du système d’exploitation. Les appareils qui répondent aux critères sont inclus dans ce groupe d’appareils, sauf si vous les excluez.
   - Tous les groupes d’appareils, y compris les groupes d’appareils par défaut et personnalisés que vous définissez, sont stockés dans Azure Active Directory (Azure AD).

   Pour en savoir plus sur les groupes d’appareils, consultez [Groupes d’appareils dans Microsoft Defender Entreprise](../security/defender-business/mdb-create-edit-device-groups.md).

1. Sur l’onglet **Paramètres de configuration**, spécifiez les paramètres de votre stratégie, puis choisissez **Suivant**. Pour plus d’informations sur les paramètres individuels, consultez [Comprendre les paramètres de configuration de nouvelle génération dans Microsoft Defender Entreprise](../security/defender-business/mdb-next-gen-configuration-settings.md).

1. Sur l’onglet **Vérifier votre stratégie**, passez en revue les informations générales, les appareils ciblés et les paramètres de configuration.

   - Apportez les modifications nécessaires en sélectionnant **Modifier**.
   - Lorsque vous êtes prêt à continuer, choisissez **Créer une stratégie**.

## <a name="working-with-device-policies-in-the-microsoft-endpoint-manager-admin-center"></a>Utilisation des stratégies d’appareil dans le Centre d’administration Microsoft Endpoint Manager

Utilisez les informations suivantes pour créer et gérer des stratégies d’appareil dans Intune, via la sécurité des points de terminaison dans le Centre d’administration Microsoft Endpoint Manager.

### <a name="create-duplicate-and-edit-policies"></a>Créer, dupliquer et modifier des stratégies

Pour créer une stratégie dans Intune

1. Connectez-vous au Centre d’administration Microsoft Endpoint Manager.

1. Sélectionnez **Sécurité du point de terminaison** et le type de stratégie que vous souhaitez configurer, puis **Créer une stratégie**.

1. Choisissez parmi les types de stratégie suivants :

    - Antivirus
    - Chiffrement de disque
    - Pare-feu
    - Détection et réponse du point de terminaison
    - Réduction de la surface d'attaque
    - Protection de compte
    - Entrez les propriétés suivantes :

1. Plateforme : choisissez la plateforme pour laquelle vous créez la stratégie. Les options disponibles dépendent du type de stratégie que vous sélectionnez.

1. Profil : choisissez parmi les profils disponibles pour la plateforme que vous avez sélectionnée. Pour plus d’informations sur les profils, consultez la section dédiée de cet article pour le type de stratégie choisi.

1. Sélectionnez **Créer**.

1. Dans la page De base, entrez un nom et une description pour le profil, puis choisissez **Suivant**.

1. Dans la page Paramètres de configuration, développez chaque groupe de paramètres et configurez les paramètres que vous souhaitez gérer avec ce profil.

1. Quand vous avez terminé de configurer les paramètres, sélectionnez **Suivant**.

1. Dans la page Balises d’étendue, choisissez **Sélectionner des balises d’étendue** pour ouvrir le volet **Sélectionner des balises** pour affecter des balises d’étendue au profil.

1. Sélectionnez **Suivant** pour continuer.

1. Dans la page **Affectations**, sélectionnez les groupes qui recevront ce profil. Pour plus d’informations sur l’affectation de profils, consultez Attribuer des profils d’utilisateur et d’appareil.

1. Sélectionnez **Suivant**.

1. Dans la page Vérifier + créer, quand vous avez terminé, choisir **Créer**. Le profil que vous venez de créer apparaît dans la liste lorsque vous sélectionnez le type de stratégie pour le nouveau profil.

Pour dupliquer une stratégie dans Intune :

1. Connectez-vous au Centre d’administration Microsoft Endpoint Manager.

1. Sélectionnez la stratégie que vous souhaitez copier. Ensuite, sélectionnez **Dupliquer**, ou sélectionnez les points de suspension **(…)** à la droite de la stratégie et sélectionnez **Dupliquer**.
1. Indiquez un nouveau nom pour la stratégie, puis sélectionnez **Enregistrer**.

Pour modifier une stratégie :

1. Sélectionnez la nouvelle stratégie, puis **Propriétés**.

1. Sélectionnez **Paramètres** pour développer la liste des paramètres de configuration dans la stratégie. Vous ne pouvez pas modifier les paramètres à partir de cette vue, mais vous pouvez vérifier comment ils sont config.

1. Pour modifier la stratégie, sélectionnez **Modifier** pour chaque catégorie dans laquelle vous souhaitez apporter une modification :

    - Informations de base
    - Affectations
    - Balises d'étendue
    - les paramètres de configuration ;

1. Après avoir effectué les modifications, sélectionnez **Enregistrer** pour les enregistrer. Les modifications apportées à une catégorie doivent être enregistrées avant de pouvoir introduire des modifications à d’autres catégories.

## <a name="manage-conflicts"></a>Gérer les conflits

La plupart des paramètres d’appareil que vous pouvez gérer avec des stratégies de sécurité de point de terminaison sont également disponibles via d’autres types de stratégies dans Intune. Ces autres types de stratégie incluent les stratégies de configuration des appareils et les bases de référence de sécurité. Étant donné que les paramètres peuvent être gérés via plusieurs types de stratégies différentes ou par plusieurs instances du même type de stratégie, préparez-vous à identifier et résoudre les conflits de stratégie pour les appareils qui ne respectent pas les configurations attendues.

Les lignes de base de sécurité peuvent définir une valeur autre que la valeur par défaut pour un paramètre afin qu’il soit conforme à la configuration recommandée pour les adresses de base.

D’autres types de stratégies, y compris les stratégies de sécurité de point de terminaison, définissent la valeur Non configurée par défaut. Ces autres types de stratégie vous obligent à configurer explicitement les paramètres dans la stratégie.

Quelle que soit la méthode de stratégie, la gestion du même paramètre sur le même appareil par le biais de plusieurs types de stratégie ou de plusieurs instances du même type de stratégie peut entraîner des conflits qui doivent être évités.

## <a name="see-also"></a>Voir aussi

[Gérer la sécurité des points de terminaison dans Microsoft Intune](/mem/Intune/protect/endpoint-security)

[Meilleures pratiques pour sécuriser les plans Microsoft 365 pour les PME](../admin/security-and-compliance/secure-your-business-data.md)

## <a name="next-objective"></a>Objectif suivant

[Configurez et gérez des groupes d’appareils](m365bp-device-groups-mdb.md).