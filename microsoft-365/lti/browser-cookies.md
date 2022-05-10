---
title: Autoriser les cookies pour les URL LMS dans votre navigateur
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: o365-administration
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Découvrez comment autoriser les cookies pour les URL LMS dans les navigateurs Edge, Chrome et Firefox et Safari.
ms.openlocfilehash: 1dabe2d16dc2d559ec1576a2140c48b63c8e2ccd
ms.sourcegitcommit: 5c64002236561000c5bd63c71423e8099e803c2d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/09/2022
ms.locfileid: "65285623"
---
# <a name="allow-cookies-for-lms-urls-in-your-browser"></a>Autoriser les cookies pour les URL LMS dans votre navigateur

Des cookies de navigateur tiers sont nécessaires pour terminer l’établissement de la liaison LTI 1.3 conformément aux normes ims globales. Par conséquent, lors du lancement de l’outil LTI à partir d’un Learning Management System (LMS), le paramètre de navigateur doit autoriser les cookies tiers pour l’URL LMS.

Voici les étapes à suivre pour autoriser les cookies dans votre navigateur.

# <a name="microsoft-edge"></a>[Microsoft Edge](#tab/edge)

## <a name="allow-cookies-for-lms-urls-in-microsoft-edge"></a>Autoriser les cookies pour les URL LMS dans Microsoft Edge

1. Dans edge  **Paramètres**  window,  **selectCookies et les autorisations** > de  **siteCookies et data storedManage** > **, puis supprimez les cookies et les données de site**.
2. Activez les  **sites OnAllow pour enregistrer et lire les données de cookie (recommandé)** et  **assurez-vous** que les cookies  tiersblock sont désactivés.

Si vous devez bloquer les cookies tiers :

1. Dans edge  **Paramètres**  window,  **selectCookies et les autorisations** > de  **siteCookies et data storedManage** > **, puis supprimez les cookies et les données de site**.
2.  **UnderAllow**,  **selectAddto**  add the domain URL of the LMS platform.
   1. Par exemple, si la plateforme LMS est hébergée sur `https://contoso.com`, cette URL doit être ajoutée sous **Autoriser**.

![Capture d’écran de Microsoft Edge page paramètres de cookie](media/edge-cookies.png)

# <a name="google-chrome"></a>[Google Chrome](#tab/chrome)

## <a name="allow-cookies-for-lms-urls-in-google-chrome"></a>Autoriser les cookies pour les URL LMS dans Google Chrome

1. Dans Chrome  **Paramètres**  window, sur  **thePrivacy et securitytab** ,  **selectCookies et d’autres données de site**.

2.  **Sous-sites qui peuvent toujours utiliser des cookies**,  **selectAdd**, puis sélectionnez les  **cookies tiersIncluding sur cette case** à cocher de site .

3. Ajoutez l’URL de domaine de la plateforme LMS.
   1. Par exemple, si la plateforme LMS est hébergée sur `https://contoso.com`, cette URL doit être utilisée.

![Capture d’écran de la page paramètres des cookies Google Chrome](media/chrome-cookies.png)

# <a name="mozilla-firefox"></a>[Mozilla Firefox](#tab/firefox)

## <a name="allow-cookies-for-lms-urls-in-mozilla-firefox"></a>Autoriser les cookies pour les URL LMS dans Mozilla Firefox

1. Dans Firefox  **Paramètres**  window, sélectionnez &  **Securitytab** .

2.  **UnderCookies et Données de site**,  **selectManage Exceptions**.

3. Dans la  **zoneAddress de websitetext** , entrez l’URL de la plateforme LMS.
   1. Par exemple, si la plateforme LMS est hébergée sur `https://contoso.com`, cette URL doit être utilisée.

4. Sélectionnez **Autoriser** pour autoriser les cookies pour le site web entré.

5. Sélectionner  **les modifications**.

![Capture d’écran de la page paramètres des cookies Mozilla Firefox](media/firefox-cookies.png)

# <a name="safari"></a>[Safari](#tab/safari)

## <a name="allow-cookies-for-lms-urls-in-safari"></a>Autoriser les cookies pour les URL LMS dans Safari

1.  **SelectPreferencesPrivacy** >. ****

2. Désactivez la case  **à cocher de**  suivi intersitePrevent.

---

> [!NOTE]
> Vous ne pouvez pas modifier les paramètres vous-même (votre navigateur est géré par votre organisation), contactez votre service informatique.
