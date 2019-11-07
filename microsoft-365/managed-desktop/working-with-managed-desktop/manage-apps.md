---
title: Gérer les applications dans le bureau géré Microsoft
description: Informations sur la mise à jour des applications métiers déployées sur des appareils de bureau gérés par Microsoft
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: 425ba674ca9911e4c93bda4fc9ad61cec7fb85b7
ms.sourcegitcommit: 3d37043c0447359c952dc99026c219dd69f6fb8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2019
ms.locfileid: "38012409"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Gérer les applications métiers dans le bureau géré Microsoft

<!--Application management -->

Il existe deux façons de gérer les mises à jour de l’application pour les applications que vous avez intégrées à Microsoft Managed Desktop et déployées sur vos appareils de bureau gérés par Microsoft. Vous pouvez créer des mises à jour d’application dans le portail de bureau géré Microsoft ou dans Intune. 

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Mettre à jour les applications métiers dans le bureau géré Microsoft

**Pour mettre à jour vos applications métiers dans le portail de bureau géré Microsoft**
1. Connectez-vous au [portail d’administration de bureau géré Microsoft](https://aka.ms/mmdportal).
2. Sous **inventaire**, sélectionnez **applications**.  
3. Sélectionnez l’application que vous souhaitez mettre à jour, puis sélectionnez **modifier**.
4. Sous **gérer**, sélectionnez **Propriétés**. 
5. Cliquez sur **fichier de package d’application**, puis accédez à télécharger un nouveau fichier de package d’application.
6. Sélectionnez **fichier de package d’application**.
7. Sélectionnez l’icône de dossier et accédez à l’emplacement de votre fichier d’application mis à jour. Sélectionnez **Ouvrir**. Les informations de l’application sont mises à jour avec les informations du package.
8. Vérifiez que la version de l' **application** reflète le package d’application mis à jour. 

L’application mise à jour sera déployée sur les appareils de l’utilisateur.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>Mettre à jour les applications métiers dans Intune

**Pour mettre à jour vos applications métiers dans Intune**
1. Connectez-vous au [portail Azure](https://azure.portal.com).
2. Sélectionnez **tous les services** > **Intune**. Intune se trouve dans la section **surveillance + Management** .
3. Sélectionnez **applications clientes > applications**.
4. Recherchez et sélectionnez votre application dans la liste des applications.
5. Dans le panneau de **vue d’ensemble** , sélectionnez **Propriétés**.
6. Sélectionnez **fichier de package d’application**.
7. Sélectionnez l’icône de dossier et accédez à l’emplacement de votre fichier d’application mis à jour. Sélectionnez **Ouvrir**. Les informations de l’application sont mises à jour avec les informations du package.
8. Vérifiez que la version de l' **application** reflète le package d’application mis à jour.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>Restaurer une version antérieure d’une application

Si une erreur est détectée lors du déploiement d’une nouvelle version d’une application, vous pouvez revenir à une version antérieure. Le processus décrit ici est destiné aux applications où le type est répertorié en tant qu' **application métier Windows MSI** ou **application windows (Win 32)-Aperçu**

**Pour restaurer une application métier vers une version antérieure**

1. Connectez-vous au [portail d’administration de bureau géré Microsoft](https://aka.ms/mmdportal).
2. Sous **inventaire**, sélectionnez **applications**.  
3. Sélectionnez l’application que vous devez restaurer, puis sélectionnez **modifier**.
4. Sous **gérer**, sélectionnez **Propriétés**. 
    - Pour les applications d' **application sectorielle Windows MSI** , sélectionnez **informations sur l’application**, puis sous **ignorer la version**de l’application, sélectionnez **Oui**.
    - Pour **Windows App (Win 32)-Preview** Apps, SELECT **app information**, SELECT **Detection Rules**, puis **Add**. 
    S’il existe une règle MSI, vérifiez que la **case à cocher vérification de la version du produit MSI** est définie sur **non**.
5. [Téléchargez une version précédente du fichier source de l’application vers le](../get-started/deploy-apps.md) portail d’administration de bureau géré Microsoft.  

