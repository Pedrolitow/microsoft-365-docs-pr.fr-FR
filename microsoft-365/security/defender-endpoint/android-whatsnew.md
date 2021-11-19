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
ms.openlocfilehash: 94f679599ada05ea7c012a34d5b189fd7b3b3fb9
ms.sourcegitcommit: 1ef176c79a0e6dbb51834fe30807409d4e94847c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/19/2021
ms.locfileid: "61111386"
---
# <a name="whats-new-in-microsoft-defender-for-endpoint-on-android"></a>Nouveautés de Microsoft Defender pour Point de terminaison sur Android

[!INCLUDE [Microsoft 365 Defender rebranding](../../includes/microsoft-defender.md)]

**S’applique à :**
- [Microsoft Defender pour point de terminaison](https://go.microsoft.com/fwlink/p/?linkid=2154037)
- [Microsoft 365 Defender](https://go.microsoft.com/fwlink/?linkid=2118804)

Vous voulez découvrir Microsoft Defender pour point de terminaison ? [Inscrivez-vous pour bénéficier d’un essai gratuit.](https://signup.microsoft.com/create-account/signup?products=7f379fee-c4f9-4278-b0a1-e4c8c2fcdf7e&ru=https://aka.ms/MDEp2OpenTrial?ocid=docs-wdatp-exposedapis-abovefoldlink)

## <a name="upcoming-permission-changes-for-microsoft-defender-for-endpoint-running-android-11-or-later-nov-2021"></a>Modifications des autorisations à venir pour Microsoft Defender pour le point de terminaison exécutant Android 11 ou version ultérieure (novembre 2021)

Release Build: 1.0.3501.0301 Release month: Nov 2021 Microsoft Defender for Endpoint has released this update required by [Google](https://developer.android.com/distribute/play-policies#APILevel30) to upgrade to Android API 30. Cette modification invite les utilisateurs à accéder à une nouvelle autorisation [de stockage,](https://developer.android.com/training/data-storage/manage-all-files#all-files-access-google-play)pour les appareils exécutant Android 11 ou version ultérieure. Les utilisateurs doivent accepter cette nouvelle autorisation de stockage une fois qu’ils ont mis à jour l’application Defender avec la version 1.0.3501.0301 ou ultérieure. Cela garantit que la fonctionnalité de sécurité de l’application defender pour point de terminaison fonctionne sans interruption. Pour plus d’informations, examinez les sections suivantes.

**Quel sera l’impact sur votre organisation :** Ces modifications auront une incidence si vous utilisez Microsoft Defender pour Endpoint sur les appareils exécutant Android 11 ou version ultérieure et que Vous avez mis à jour Defender pour Endpoint pour publier la build 1.0.3501.0301 ou ultérieure.

> [!NOTE]
> Les nouvelles autorisations de stockage ne peuvent pas être configurées par l’administrateur pour « Approuver automatiquement » via Microsoft Endpoint Manager. L’utilisateur doit prendre des mesures pour fournir l’accès à cette autorisation.

- **Expérience utilisateur :** Les utilisateurs recevront une notification indiquant qu’il manque une autorisation pour la sécurité de l’application. Si l’utilisateur refuse cette autorisation, la fonctionnalité « Sécurité de l’application » est désactivée sur l’appareil. Si l’utilisateur n’accepte pas ou ne refuse pas l’autorisation, il continue de recevoir l’invite lors du déverrouillage de son appareil ou de l’ouverture de l’application, jusqu’à ce qu’elle ait été approuvée.

> [!NOTE]
> Si votre organisation affiche un aperçu de la fonctionnalité « Protection contre la falsification » et si les nouvelles autorisations de stockage ne sont pas accordées par l’utilisateur dans les 7 jours suivant la mise à jour vers la dernière version, l’utilisateur risque de perdre l’accès aux ressources d’entreprise.

**Consignes de préparation :**

Informez vos utilisateurs et le helpdesk (le cas échéant) que les utilisateurs devront accepter les nouvelles autorisations lorsqu’ils y seront invités après avoir mis à jour Defender for Endpoint pour créer la version 1.0.3501.0301 ou ultérieure. Pour accepter les autorisations, les utilisateurs doivent :

1. Appuyez sur la notification Du point de terminaison dans l’application ou ouvrez l’application Defender pour le point de terminaison. Les utilisateurs voient un écran répertoriant les autorisations nécessaires. Une coche verte est manquante en regard de l’autorisation Stockage défaut.

2. Appuyez **sur Commencer.**

3. Appuyez sur le basculement pour **autoriser l’accès afin de gérer tous les fichiers.**

4. L’appareil est désormais protégé.

  > [!NOTE]
  > Cette autorisation permet à Microsoft Defender for Endpoint d’accéder au stockage sur l’appareil de l’utilisateur, ce qui permet de détecter et de supprimer les applications malveillantes et indésirables. Microsoft Defender pour le point de terminaison accède/analyse uniquement le fichier de package d’application Android (.apk). Sur les appareils avec un profil de travail, Defender pour le point de terminaison analyse uniquement les fichiers liés au travail.
