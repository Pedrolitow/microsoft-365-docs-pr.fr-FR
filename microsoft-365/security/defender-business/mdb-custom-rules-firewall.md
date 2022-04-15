---
title: Gérer des règles personnalisées pour les stratégies de pare-feu dans Microsoft Defender pour les PME
description: Les règles personnalisées fournissent des exceptions aux stratégies de pare-feu. Vous pouvez utiliser des règles personnalisées pour bloquer ou autoriser des connexions spécifiques dans Microsoft Defender pour les PME
search.appverid: MET150
author: denisebmsft
ms.author: deniseb
manager: dansimp
audience: Admin
ms.topic: overview
ms.date: 04/12/2022
ms.prod: m365-security
ms.technology: mdb
ms.localizationpriority: medium
ms.reviewer: inbadian, shlomiakirav
f1.keywords: NOCSH
ms.collection:
- SMB
- M365-security-compliance
ms.openlocfilehash: ae409f1196b01b774d9e73d45d16868bff1c904b
ms.sourcegitcommit: e3bc6563037bd2cce2abf108b3d1bcc2ccf538f6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/15/2022
ms.locfileid: "64861705"
---
# <a name="manage-your-custom-rules-for-firewall-policies-in-microsoft-defender-for-business"></a>Gérer vos règles personnalisées pour les stratégies de pare-feu dans Microsoft Defender pour les PME

> [!NOTE]
> Microsoft Defender pour les PME est désormais inclus dans [Microsoft 365 Business Premium](../../business-premium/index.md). 


Microsoft Defender pour les PME inclut des stratégies de pare-feu qui aident à protéger vos appareils contre le trafic réseau indésirable. Vous pouvez utiliser des règles personnalisées pour définir des exceptions pour vos stratégies de pare-feu. Autrement dit, vous pouvez utiliser des règles personnalisées pour bloquer ou autoriser des connexions spécifiques.

Pour en savoir plus sur les stratégies et les paramètres de [pare-feu, consultez Pare-feu dans Microsoft Defender pour les PME](mdb-firewall.md).

**Cet article explique comment** :

- [Créer une règle personnalisée pour une stratégie de pare-feu](#create-a-custom-rule-for-a-firewall-policy)
- [Modifier une règle personnalisée pour une stratégie de pare-feu](#edit-a-custom-rule-for-a-firewall-policy)
- [Supprimer une règle personnalisée](#delete-a-custom-rule)

>
> **Avez-vous un peu de temps ?**
> Veuillez prendre notre <a href="https://microsoft.qualtrics.com/jfe/form/SV_0JPjTPHGEWTQr4y" target="_blank">courte enquête sur la sécurité</a>. Vos commentaires sont les bienvenus.
>

## <a name="create-a-custom-rule-for-a-firewall-policy"></a>Créer une règle personnalisée pour une stratégie de pare-feu

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Accédez à **la configuration endpointsDevice** >  et passez en revue la liste des stratégies.

3. Dans la section **Pare-feu** , sélectionnez une stratégie existante ou ajoutez une nouvelle stratégie.

4. À l’étape **Paramètres de configuration** , passez en revue les paramètres. Apportez les modifications nécessaires au **réseau de domaine**, **au réseau public** et **au réseau privé**.

5. Pour créer une règle personnalisée, procédez comme suit : 

   1. Sous **Règles personnalisées**, choisissez **+ Ajouter une règle**. (Vous pouvez avoir jusqu’à 150 règles personnalisées.)
   2. Dans le menu volant **Créer une règle** , spécifiez un nom et une description pour la règle.
   3. Sélectionnez un profil. (Vos options incluent **le réseau de domaine**, **le réseau public** ou **le réseau privé**.)
   4. Dans la liste **des types d’adresses distantes** , sélectionnez le chemin d’accès du fichier **IP** ou **de l’application**.
   5. Dans la zone **Valeur** , spécifiez une valeur appropriée. Selon ce que vous avez sélectionné à l’étape 6d, vous pouvez spécifier une adresse IP, une plage d’adresses IP ou un chemin d’accès au fichier d’application. (Consultez [les paramètres du pare-feu](mdb-firewall.md).)
   6. Dans le menu volant **Créer une règle** , sélectionnez **Créer une règle**. 

6. Dans l’écran **Paramètres de configuration** , choisissez **Suivant**.

7. Dans l’écran **Vérifier votre stratégie** , passez en revue les modifications apportées aux paramètres de stratégie de pare-feu. Apportez les modifications nécessaires, puis **choisissez Créer une stratégie**.

## <a name="edit-a-custom-rule-for-a-firewall-policy"></a>Modifier une règle personnalisée pour une stratégie de pare-feu

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Accédez à **la configuration endpointsDevice** >  et passez en revue la liste des stratégies.

3. Dans la section **Pare-feu** , sélectionnez une stratégie existante ou ajoutez une nouvelle stratégie.

4. Sous **Règles personnalisées**, passez en revue la liste des règles.

5. Sélectionnez une règle, puis **choisissez Modifier**. Son menu volant s’ouvre.

6. Pour modifier votre règle personnalisée, procédez comme suit :

   1. Dans le menu volant **Modifier la règle** , passez en revue et modifiez le nom et la description de la règle.
   2. Examinez et, si nécessaire, modifiez le profil de la règle. (Vos options incluent **le réseau de domaine**, **le réseau public** ou **le réseau privé**.)
   3. Dans la liste **des types d’adresses distantes** , sélectionnez le chemin d’accès du fichier **IP** ou **de l’application**.
   4. Dans la zone **Valeur** , spécifiez une valeur appropriée. Selon ce que vous avez sélectionné à l’étape 6c, vous pouvez spécifier une adresse IP, une plage d’adresses IP ou un chemin d’accès au fichier d’application. (Consultez [les paramètres du pare-feu](mdb-firewall.md).)
   5. **Définissez Activer la règle** **sur Activé** pour activer la règle. Ou, pour désactiver la règle, définissez le commutateur sur **Désactivé**.
   6. Dans le menu volant **Modifier la règle** , sélectionnez **Mettre à jour la règle**. 

7. Dans l’écran **Paramètres de configuration** , choisissez **Suivant**.

8. Dans l’écran **Vérifier votre stratégie** , passez en revue les modifications apportées aux paramètres de stratégie de pare-feu. Apportez les modifications nécessaires, puis **choisissez Créer une stratégie**.

## <a name="delete-a-custom-rule"></a>Supprimer une règle personnalisée

1. Accédez au portail Microsoft 365 Defender ([https://security.microsoft.com](https://security.microsoft.com)) et connectez-vous.

2. Accédez à **la configuration endpointsDevice** >  et passez en revue la liste des stratégies.

3. Dans la section **Pare-feu** , sélectionnez une stratégie existante ou ajoutez une nouvelle stratégie.

4. Sous **Règles personnalisées**, passez en revue la liste des règles.

5. Sélectionnez une règle, puis **choisissez Supprimer**. Son menu volant s’ouvre.

6. Dans l’écran de confirmation, choisissez **Supprimer**. 

## <a name="next-steps"></a>Prochaines étapes

- [Afficher et gérer les incidents dans Microsoft Defender pour les PME](mdb-view-manage-incidents.md)
- [Répondre aux menaces et les atténuer dans Microsoft Defender pour les PME](mdb-respond-mitigate-threats.md)
- [Passer en revue les actions de correction dans le Centre d’actions](mdb-review-remediation-actions.md)