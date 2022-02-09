---
title: Gérer des règles personnalisées pour les stratégies de pare-feu dans Microsoft Defender entreprise
description: Les règles personnalisées fournissent des exceptions aux stratégies de pare-feu. Vous pouvez utiliser des règles personnalisées pour bloquer ou autoriser des connexions spécifiques dans Microsoft Defender entreprise
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 02/07/2022
ms.prod: m365-security
ms.technology: mdb
localization_priority: Normal
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: 2200c32d910a5afd20a8ff01c6e24625d72ae21c
ms.sourcegitcommit: 4c207a9bdbb6c8ba372ae37907ccefca031a49f8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/09/2022
ms.locfileid: "62464589"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business-preview"></a>Gérer vos règles personnalisées pour les stratégies de pare-feu dans Microsoft Defender entreprise (aperçu)

> [!IMPORTANT]
> Microsoft Defender pour Entreprise est désormais en prévisualisation et sera progressivement mis en place pour les clients [](https://aka.ms/mdb-preview) et les partenaires qui s’y connectent pour le demander. Nous intégrerons un ensemble initial de clients et de partenaires dans les prochaines semaines et développerons la prévisualisation jusqu’à la disponibilité générale. Notez que la prévisualisation sera lancée avec un [ensemble initial de scénarios](mdb-tutorials.md#try-these-preview-scenarios) et que nous ajouterons régulièrement des fonctionnalités.
> 
> Certaines informations de cet article concernent les produits/services pré-publiés qui peuvent être considérablement modifiés avant leur publication commerciale. Microsoft n’offre aucune garantie, expressément ou implicite, pour les informations fournies ici. 


Microsoft Defender pour Entreprise (prévisualisation) inclut des stratégies de pare-feu qui aident à protéger vos appareils contre le trafic réseau indésirable. Vous pouvez utiliser des règles personnalisées pour définir des exceptions pour vos stratégies de pare-feu. Autrement dit, vous pouvez utiliser des règles personnalisées pour bloquer ou autoriser des connexions spécifiques.

Pour en savoir plus sur les stratégies et paramètres de pare-feu, voir [Pare-feu dans Microsoft Defender pour Entreprises (prévisualisation).](mdb-firewall.md)

**Cet article décrit comment** :

- [Créer une règle personnalisée pour une stratégie de pare-feu](#create-a-custom-rule-for-a-firewall-policy)
- [Modifier une règle personnalisée pour une stratégie de pare-feu](#edit-a-custom-rule-for-a-firewall-policy)
- [Supprimer une règle personnalisée](#delete-a-custom-rule)

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Créer une règle personnalisée pour une stratégie de pare-feu

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Go to **EndpointsDevice** >  **configuration**, and review the list of policies.

3. Dans la section **Pare-feu** , sélectionnez une stratégie existante ou ajoutez une nouvelle stratégie.

4. À **l’étape Paramètres de configuration** , examinez les paramètres. A apporter les modifications nécessaires au **réseau de domaine**, **au réseau public** et **au réseau privé**.

5. Pour créer une règle personnalisée, suivez les étapes suivantes : 

   1. Sous **Règles personnalisées**, **choisissez + Ajouter une règle**. (Vous pouvez avoir jusqu’à 150 règles personnalisées.)
   2. Dans le **volant Créer une règle** , spécifiez un nom et une description pour la règle.
   3. Sélectionnez un profil. (Vos options incluent **le réseau de domaine**, **le réseau public** ou **le réseau privé**.)
   4. Dans la liste **des types d’adresses** distantes, sélectionnez le chemin **d’accès au** **fichier IP ou Application**.
   5. Dans la **zone** Valeur, spécifiez une valeur appropriée. Selon ce que vous avez sélectionné à l’étape 6d, vous pouvez spécifier une adresse IP, une plage d’adresses IP ou un chemin d’accès au fichier d’application. (Voir [paramètres du pare-feu](mdb-firewall.md).)
   6. Dans le **volant Créer une règle** , **sélectionnez Créer une règle**. 

6. Dans **l’écran Paramètres de configuration** , choisissez **Suivant**.

7. Dans **l’écran Examiner votre stratégie** , examinez les modifications apportées aux paramètres de stratégie de pare-feu. A effectuer les modifications nécessaires, puis **sélectionnez Créer une stratégie**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Modifier une règle personnalisée pour une stratégie de pare-feu

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Go to **EndpointsDevice** >  **configuration**, and review the list of policies.

3. Dans la section **Pare-feu** , sélectionnez une stratégie existante ou ajoutez une nouvelle stratégie.

4. Sous **Règles personnalisées**, examinez la liste des règles.

5. Sélectionnez une règle, puis sélectionnez **Modifier**. Son volant s’ouvre.

6. Pour modifier votre règle personnalisée, suivez les étapes suivantes :

   1. Dans le **volant modifier la règle** , examinez et modifiez le nom et la description de la règle.
   2. Examinez et, si nécessaire, modifiez le profil de la règle. (Vos options incluent **le réseau de domaine**, **le réseau public** ou **le réseau privé**.)
   3. Dans la liste **des types d’adresses** distantes, sélectionnez le chemin **d’accès au** **fichier IP ou Application**.
   4. Dans la **zone** Valeur, spécifiez une valeur appropriée. Selon ce que vous avez sélectionné à l’étape 6c, vous pouvez spécifier une adresse IP, une plage d’adresses IP ou un chemin d’accès au fichier d’application. (Voir [paramètres du pare-feu](mdb-firewall.md).)
   5. **Définissez Activer la** règle **pour** activer la règle. Ou, pour désactiver la règle, définissez le commutateur sur **Désactivé**.
   6. Dans le volant **de la règle de** modification, sélectionnez **Mettre à jour la règle**. 

7. Dans **l’écran Paramètres de configuration** , choisissez **Suivant**.

8. Dans **l’écran Examiner votre stratégie** , examinez les modifications apportées aux paramètres de stratégie de pare-feu. A effectuer les modifications nécessaires, puis **sélectionnez Créer une stratégie**.

## <a name="delete-a-custom-rule"></a>Supprimer une règle personnalisée

1. Go to the Microsoft 365 Defender portal ([https://security.microsoft.com](https://security.microsoft.com)) and sign in.

2. Go to **EndpointsDevice** >  **configuration**, and review the list of policies.

3. Dans la section **Pare-feu** , sélectionnez une stratégie existante ou ajoutez une nouvelle stratégie.

4. Sous **Règles personnalisées**, examinez la liste des règles.

5. Sélectionnez une règle, puis choisissez **Supprimer**. Son volant s’ouvre.

6. Dans l’écran de confirmation, sélectionnez **Supprimer**. 

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender entreprise (prévisualisation)](mdb-view-manage-incidents.md)

- [Répondre aux menaces et les atténuer dans Microsoft Defender entreprise (prévisualisation)](mdb-respond-mitigate-threats.md)

- [Passer en revue les actions de correction dans le centre de mise à jour](mdb-review-remediation-actions.md)