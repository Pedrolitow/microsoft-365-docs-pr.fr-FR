---
title: Gérer les applications dans Microsoft Manged Desktop
description: Informations sur la mise à jour des applications métier déployées sur Microsoft Manged Desktop appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: tiaraquan
f1.keywords:
- NOCSH
ms.author: tiaraquan
manager: dougeby
ms.topic: article
ms.localizationpriority: medium
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: a51be2521924164a8c90a51fcf99328ecf511877
ms.sourcegitcommit: bae72428d229827cba4c807d9cd362417afbcccb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/02/2022
ms.locfileid: "62322553"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Gérer les applications métier dans le bureau géré Microsoft

<!--Application management -->

Il existe deux façons de gérer les mises à jour d’application et de les déployer sur vos appareils Microsoft Manged Desktop mobiles. Vous pouvez effectuer des mises à jour d’application dans Microsoft Manged Desktop portail ou Intune.

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Mettre à jour des applications métier dans Microsoft Manged Desktop

**Pour mettre à jour vos applications métier dans Microsoft Manged Desktop portail :**

1. Connectez-vous [Microsoft Manged Desktop portail d’administration.](https://aka.ms/mmdportal)
1. Sous **Inventaire**, sélectionnez **Applications**.  
1. Sélectionnez l’application à mettre à jour, puis sélectionnez **Modifier**.
1. Sous **Gérer**, sélectionnez **Propriétés**.
1. **Sélectionnez le fichier de package d’application**, puis recherchez un nouveau fichier de package d’application.
1. Sélectionnez **le fichier de package d’application**.
1. Sélectionnez l’icône du dossier et accédez à l’emplacement de votre fichier d’application mis à jour. Sélectionnez **Ouvrir**. Les informations de l’application sont mises à jour avec les informations de package.
1. Vérifiez que la **version de l’application** reflète le package d’application mis à jour.

L’application mise à jour sera déployée sur les appareils de vos utilisateurs.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>Mettre à jour des applications métier dans Intune

**Pour mettre à jour vos applications métier dans Intune :**

1. Connectez-vous au [portail Azure](https://portal.azure.com).
2. **Sélectionnez Tous les** **ServicesIntune** > . Intune se trouve dans la section **Analyse + Gestion** .
3. **Sélectionnez Applications clientes > applications**.
4. Recherchez et sélectionnez votre application dans la liste des applications.
5. Dans la section **Vue d’ensemble** , sélectionnez **Propriétés**.
6. Sélectionnez **le fichier de package d’application**.
7. Sélectionnez l’icône du dossier et accédez à l’emplacement de votre fichier d’application mis à jour. Sélectionnez **Ouvrir**. Les informations de l’application sont mises à jour avec les informations de package.
8. Vérifiez que la **version de l’application** reflète le package d’application mis à jour.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>Roll back an app to a previous version

Lorsqu’une nouvelle version d’une application est déployée et qu’une erreur est trouvée, vous pouvez revenir à une version précédente. Le processus décrit ci-dessous est pour les applications dont le type est répertorié en tant qu’application métier **Windows MSI** ou **application Windows (Win 32) : prévisualisation**

**Pour revenir à une version antérieure d’une application métier :**

1. Connectez-vous [Microsoft Manged Desktop portail d’administration.](https://aka.ms/mmdportal)
2. Sous **Inventaire**, sélectionnez **Applications**.  
3. Sélectionnez l’application à revenir en arrière, puis sélectionnez **Modifier**.
4. Sous **Gérer**, sélectionnez **Propriétés**.
    - Pour **Windows applications métier MSI**, sélectionnez Informations sur l’application **, puis** sous Ignorer la **version** de l’application, sélectionnez **Oui**.
    - For **Windows app (Win 32) - preview** apps, select **App information**, select **Detection rules**, and then select **Add**.
    S’il existe une règle MSI, vérifiez que la vérification de version du produit **MSI** est définie sur **Non**.
5. [Télécharger une version précédente du fichier source de l’application](../get-started/deploy-apps.md) pour Microsoft Manged Desktop portail d’administration.  
