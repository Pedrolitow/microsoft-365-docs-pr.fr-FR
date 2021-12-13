---
title: Afficher ou modifier des stratégies dans Microsoft Defender entreprise (prévisualisation)
description: Découvrez comment afficher, modifier, créer et supprimer des stratégies de protection nouvelle génération dans Microsoft Defender pour Entreprises (prévisualisation)
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 12/10/2021
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 482d29f84675c7e2c4213498ff2e513280b84cb6
ms.sourcegitcommit: b1066b2a798568afdea9c09401d52fa38fe93546
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/13/2021
ms.locfileid: "61421089"
---
# <a name="view-or-edit-policies-in-microsoft-defender-for-business-preview"></a>Afficher ou modifier des stratégies dans Microsoft Defender entreprise (prévisualisation)

> [!IMPORTANT]
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. Cet article inclut des liens vers du contenu en ligne qui peut décrire certaines fonctionnalités qui ne sont pas incluses dans Microsoft Defender pour Entreprises (prévisualisation).

Dans Microsoft Defender entreprise (prévisualisation), les paramètres de sécurité sont configurés par le biais de stratégies. Il existe deux principaux types de stratégies dans Defender for Business (prévisualisation) :

- **Stratégies de protection nouvelle génération,** qui déterminent Antivirus Microsoft Defender et d’autres fonctionnalités de protection contre les menaces sont configurées
- **Stratégies de** pare-feu, qui déterminent le trafic réseau autorisé à circuler vers et depuis les appareils de votre entreprise

**Cet article décrit comment**:

- [Afficher vos stratégies existantes](#view-your-existing-policies)
- [Modifier une stratégie existante](#edit-an-existing-policy)

> [!TIP]
> Si vous souhaitez ajouter une nouvelle stratégie, voir [Créer une stratégie.](mdb-create-new-policy.md)

## <a name="view-your-existing-policies"></a>Afficher vos stratégies existantes

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil.** Les stratégies sont organisées par système d’exploitation (tel que **Windows client)** et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).   

3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients),** puis examinez la liste des stratégies sous les catégories Protection nouvelle génération et  Pare-feu.  

4. Pour afficher plus de détails sur une stratégie, sélectionnez son nom. Un volet latéral s’ouvre et fournit plus d’informations sur cette stratégie, par exemple sur les appareils protégés par cette stratégie.

## <a name="edit-an-existing-policy"></a>Modifier une stratégie existante

1. Go to the Microsoft 365 Defender portal ( [https://security.microsoft.com](https://security.microsoft.com) ), and sign in. 

2. Dans le volet de navigation, choisissez **Configuration de l’appareil.** Les stratégies sont organisées par système d’exploitation (tel que **Windows client)** et par type de stratégie (par exemple, protection nouvelle génération et pare-feu).   

3. Sélectionnez un onglet de système d’exploitation (par **exemple, Windows clients),** puis examinez la liste des stratégies sous les catégories Protection nouvelle génération et  Pare-feu.  

4. Pour modifier une stratégie, sélectionnez son nom, puis choisissez **Modifier.**

5. Sous **l’onglet Informations générales,** examinez les informations. Si nécessaire, vous pouvez modifier la description. Sélectionnez **Suivant**.

6. Sous **l’onglet Groupes d’appareils,** déterminez les groupes d’appareils qui doivent recevoir cette stratégie.  

   - Pour conserver le groupe d’appareils sélectionné tel quel, choisissez **Suivant.**
   - Pour supprimer un groupe d’appareils de la stratégie, sélectionnez **Supprimer.**
   - Pour configurer un nouveau groupe d’appareils, **sélectionnez** Créer un groupe, puis configurer votre groupe d’appareils. (Pour obtenir de l’aide sur cette tâche, consultez [Groupes d’appareils dans Microsoft Defender entreprise (prévisualisation).](mdb-create-edit-device-groups.md)
   - Pour appliquer la stratégie à un autre groupe d’appareils, **sélectionnez Utiliser un groupe existant.**

   Une fois que vous avez spécifié les groupes d’appareils qui doivent recevoir la stratégie, choisissez **Suivant**.

7. Sous **l’onglet Paramètres de configuration,** examinez les paramètres. Si nécessaire, vous pouvez modifier les paramètres de votre stratégie. Pour obtenir de l’aide sur cette tâche, consultez les articles suivants : 

   - [Comprendre les paramètres de configuration nouvelle génération](mdb-next-gen-configuration-settings.md)   
   - [Paramètres du pare-feu](mdb-firewall.md)

   Une fois que vous avez spécifié vos paramètres de protection nouvelle génération, choisissez **Suivant**.

8. Sous **l’onglet Examiner votre stratégie,** examinez les informations générales, les appareils ciblés et les paramètres de configuration. 

   - A apporter les modifications nécessaires en sélectionnant **Modifier.**
   - Lorsque vous êtes prêt à continuer, sélectionnez Mettre **à jour la stratégie.**


## <a name="next-steps"></a>Prochaines étapes

Choisissez une ou plusieurs des tâches suivantes :

- [Gérer les appareils](mdb-manage-devices.md)

- [Créer une stratégie dans Microsoft Defender entreprise (prévisualisation)](mdb-create-new-policy.md)

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)