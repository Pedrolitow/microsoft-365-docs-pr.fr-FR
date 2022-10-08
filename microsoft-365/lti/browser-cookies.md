---
title: Autoriser les cookies pour les URL LMS dans votre navigateur
ms.author: danismith
author: DaniEASmith
manager: serdars
ms.reviewer: amitman
audience: admin
ms.topic: article
ms.service: microsoft-365-business
f1.keywords:
- CSH
ms.collection: M365-modern-desktop
ms.localizationpriority: medium
description: Découvrez comment autoriser les cookies pour les URL LMS dans les navigateurs Edge, Chrome et Firefox et Safari.
ms.openlocfilehash: fcaae51c9cdbab3a052a3c29d24e5386f4f852ee
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68167360"
---
# <a name="allow-cookies-for-lms-urls-in-your-browser"></a>Autoriser les cookies pour les URL LMS dans votre navigateur

Des cookies de navigateur tiers sont nécessaires pour terminer l’établissement de la liaison LTI 1.3 conformément aux normes ims globales. Par conséquent, lors du lancement de l’outil LTI à partir d’un système de gestion de l’apprentissage (LMS), le paramètre de navigateur doit autoriser les cookies tiers pour l’URL LMS.

Voici les étapes à suivre pour autoriser les cookies dans votre navigateur.

# <a name="microsoft-edge"></a>[Microsoft Edge](#tab/edge)

## <a name="allow-cookies-for-lms-urls-in-microsoft-edge"></a>Autoriser les cookies pour les URL LMS dans Microsoft Edge

1. Dans la fenêtre **Paramètres** dʼEdge, sélectionnez **Cookies et autorisations de site** > **Cookies et données stockés** > **Gérer et supprimer les cookies et les données du site**.
2. Activez l’option **Autoriser les sites à enregistrer et à lire les données des cookies (recommandé)** et assurez-vous que l’option **Bloquer les cookies tiers** est désactivée.

Si vous devez bloquer les cookies tiers :

1. Dans la fenêtre **Paramètres** dʼEdge, sélectionnez **Cookies et autorisations de site** > **Cookies et données stockés** > **Gérer et supprimer les cookies et les données du site**.
2. Sous **Autoriser**, **sélectionnez Ajouter** pour ajouter l’URL de domaine de la plateforme LMS.
   1. Par exemple, si la plateforme LMS est hébergée sur `https://contoso.com`, cette URL doit être ajoutée sous **Autoriser**.

![Capture d’écran de la page paramètres des cookies Microsoft Edge](media/edge-cookies.png)

# <a name="google-chrome"></a>[Google Chrome](#tab/chrome)

## <a name="allow-cookies-for-lms-urls-in-google-chrome"></a>Autoriser les cookies pour les URL LMS dans Google Chrome

1. Dans la fenêtre **Paramètres** de Chrome, sous l’onglet **Confidentialité et sécurité**, sélectionnez **Cookies et autres données de site**.

2. Sous **Sites autorisés à utiliser des cookies**, sélectionnez **Ajouter**, puis activez la case **Inclure les cookies tiers de ce site**.

3. Ajoutez l’URL de domaine de la plateforme LMS.
   1. Par exemple, si la plateforme LMS est hébergée sur `https://contoso.com`, cette URL doit être utilisée.

![Capture d’écran de la page paramètres des cookies Google Chrome](media/chrome-cookies.png)

# <a name="mozilla-firefox"></a>[Mozilla Firefox](#tab/firefox)

## <a name="allow-cookies-for-lms-urls-in-mozilla-firefox"></a>Autoriser les cookies pour les URL LMS dans Mozilla Firefox

1. Dans la fenêtre **Paramètres** de Firefox, sélectionnez lʼonglet **Vie privée et sécurité**.

2. Sous **Cookies et données de sites**, sélectionnez **Gérer les exceptions**.

3. Dans la zone **de texte Adresse du site web** , entrez l’URL de la plateforme LMS.
   1. Par exemple, si la plateforme LMS est hébergée sur `https://contoso.com`, cette URL doit être utilisée.

4. Sélectionnez **Autoriser** pour autoriser les cookies pour le site web entré.

5. Sélectionnez **Enregistrer les modifications**.

![Capture d’écran de la page paramètres des cookies Mozilla Firefox](media/firefox-cookies.png)

# <a name="safari"></a>[Safari](#tab/safari)

## <a name="allow-cookies-for-lms-urls-in-safari"></a>Autoriser les cookies pour les URL LMS dans Safari

1. Sélectionnez **Préférences** > **Confidentialité**.

2. Désactivez la case **Empêcher le suivi intersite**.

---

> [!NOTE]
> Vous ne pouvez pas modifier les paramètres vous-même (votre navigateur est géré par votre organisation), contactez votre service informatique.
