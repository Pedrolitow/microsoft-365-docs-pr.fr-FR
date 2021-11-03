---
title: Nouveautés de Microsoft Defender pour Point de terminaison sur Android
description: Découvrez les principales modifications apportées aux versions précédentes de Microsoft Defender pour Endpoint sur Android.
keywords: microsoft, defender, Microsoft Defender pour point de terminaison, mac, installation, macos, whatsnew
ms.prod: m365-security
ms.mktglfcycl: security
ms.sitesec: library
ms.pagetype: security
ms.author: macapara
author: mjcaparas
ms.localizationpriority: medium
manager: dansimp
audience: ITPro
ms.collection:
- m365-security-compliance
- m365initiative-defender-endpoint
ms.topic: reference
ms.technology: mde
ms.openlocfilehash: 820c93804615e9aafcb34052d65f09bbd3e3d1c9
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/03/2021
ms.locfileid: "60717453"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Nouveautés de Microsoft Defender pour Point de terminaison sur Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later"></a>Modifications d’autorisation à venir pour Microsoft Defender pour le point de terminaison exécutant Android 11 ou version ultérieure

En novembre, Microsoft Defender pour le point de terminaison sera requis par [Google](https://developer.android.com/distribute/play-policies#APILevel30) pour passer à l’API Android 30. Ce déplacement demande une nouvelle autorisation [de stockage](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play) pour les appareils exécutant Android 11 ou version ultérieure. Les utilisateurs doivent accepter cette nouvelle autorisation de stockage une fois qu’ils ont mis à jour la version de novembre de Microsoft Defender for Endpoint. Cela permettra de poursuivre la fonctionnalité « Sécurité des applications » de Defender sur leurs appareils. Pour plus d’informations, voir les détails dans les sections suivantes.

**Quel sera l’impact sur votre organisation :**

Ces modifications ne vous affectent que si vous utilisez Microsoft Defender pour Endpoint sur les appareils exécutant Android 11 ou version ultérieure et mis à jour vers l’application de novembre. Ce paramètre n’est pas configurable via Microsoft Endpoint Manager; les utilisateurs devront prendre des mesures en raison des modifications apportées à l’API Google susmentionnées.

- **Expérience utilisateur :** Les utilisateurs recevront une notification indiquant qu’il manque une autorisation pour la sécurité de l’application. Si l’utilisateur refuse cette autorisation, la fonctionnalité « Sécurité de l’application » est désactivée sur l’appareil. Si votre utilisateur n’accepte pas ou ne refuse pas l’autorisation, il continue de recevoir l’invite lors du déverrouillage de son appareil ou de l’ouverture de l’application jusqu’à ce qu’elle ait été approuvée.

>[!NOTE] 
> Si votre organisation affiche un aperçu de la fonctionnalité « Protection contre la falsification » et si les nouvelles autorisations de stockage ne sont pas accordées par l’utilisateur dans les 7 jours suivant la mise à jour vers la dernière version, l’utilisateur risque de perdre l’accès aux ressources d’entreprise.

**Ce que vous devez faire pour préparer :**

Informez vos utilisateurs et le helpdesk (le cas échéant) que les utilisateurs devront accepter les nouvelles autorisations lorsqu’ils y seront invités après avoir mis à jour la version de novembre de l’application Microsoft Defender pour Endpoint. Pour accepter les autorisations, les utilisateurs doivent :

1. Appuyez sur la notification Defender dans l’application ou ouvrez l’application Microsoft Defender pour le point de terminaison. Les utilisateurs voient un écran répertoriant les autorisations nécessaires. Une coche verte est manquante en regard de l’autorisation Stockage défaut.

2. Appuyez **sur Commencer.**

3. Appuyez sur le basculement pour **autoriser l’accès afin de gérer tous les fichiers.** 

  >[!NOTE] 
  >Cette autorisation permet à Microsoft Defender for Endpoint d’accéder au stockage sur l’appareil de l’utilisateur, ce qui permet de détecter et de supprimer les applications malveillantes et indésirables. Microsoft Defender pour le point de terminaison accède uniquement au fichier de package d’application Android (.apk) et analyse uniquement les fichiers liés au travail sur les appareils ayant un profil de travail.

4. L’appareil est désormais protégé.





