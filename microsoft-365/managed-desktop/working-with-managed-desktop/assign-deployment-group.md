---
title: Affecter des appareils à un groupe de déploiement
description: Comment spécifier le groupe de déploiement dans lequel vous souhaitez que les appareils soient connectés
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
ms.localizationpriority: medium
ms.collection: M365-modern-desktop
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.openlocfilehash: 6f3d2c79c23a37e1e1a965f9a3f416052a49fa76
ms.sourcegitcommit: af73b93a904ce8604be319e8dc7cadaf65d50534
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/31/2022
ms.locfileid: "62281422"
---
# <a name="assign-devices-to-a-deployment-group"></a>Affecter des appareils à un groupe de déploiement

Microsoft Manged Desktop affectera des appareils aux différents groupes de déploiement. Vous pouvez spécifier ou modifier le groupe affecté à un appareil à l’aide du portail d’administration. Vous modifiez l’affectation après l’inscription d’un appareil ou après l’inscription d’un utilisateur.

> [!IMPORTANT]
> Si vous modifiez l’affectation, les stratégies spécifiques à ce groupe seront appliquées à l’appareil. La modification peut installer la dernière version de Windows 10 (y compris les nouvelles mises à jour de fonctionnalité ou de qualité). Il est préférable de déplacer quelques appareils au début, puis de vérifier l’expérience utilisateur résultante. N’ignorez pas que certaines mises à jour redémarreront l’appareil. Vérifiez que vous avez sélectionné les appareils à affecter. L’affectation peut prendre effet jusqu’à 24 heures.

**Pour affecter des appareils à un groupe de déploiement :**

Si vous souhaitez déplacer des appareils distincts vers différents groupes, répétez ces étapes pour chaque groupe.

1. Dans Microsoft Endpoint Manager, sélectionnez **Appareils** dans le volet gauche.
1. Dans la **section Microsoft Manged Desktop**, sélectionnez **Appareils**.
1. Sélectionnez les appareils que vous souhaitez affecter. Tous les appareils sélectionnés sont affectés au groupe que vous spécifiez.
1. Sélectionnez **les actions de** l’appareil dans le menu.
1. **Sélectionnez Affecter l’appareil au groupe**. Un volant s’ouvre.
1. Utilisez le menu déroulant pour sélectionner le groupe vers qui déplacer les appareils, puis sélectionnez **Enregistrer**. Le **groupe affecté par** colonne est alors **en attente**.

Une fois l’affectation **terminée, le** groupe affecté par colonne est nommé **Administrateur** (indique que vous avez effectué la modification) et  la colonne Groupe affiche la nouvelle affectation de groupe.

> [!NOTE]
> Vous ne pouvez pas déplacer d’appareils vers d’autres groupes s’ils sont dans l’état d’inscription « erreur » ou « en attente ».
>
>Si un appareil n’a pas été correctement supprimé, il peut afficher l’état « prêt ». Si vous déplacez un tel appareil, il est possible que le déplacement ne se termine pas. Si le groupe n’est  pas affecté par la modification de colonne à **En** attente à l’étape 5, vérifiez que l’appareil est disponible en le recherchant dans Intune. Pour plus d’informations, consultez [Afficher les détails de l’appareil dans Intune](/mem/intune/remote-actions/device-inventory).
