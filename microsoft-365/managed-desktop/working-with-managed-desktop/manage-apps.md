---
title: Gérer les applications dans Le Bureau géré Microsoft
description: Informations sur la mise à jour des applications métier déployées sur les appareils de bureau géré Microsoft
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
ms.localizationpriority: normal
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: 1a6b91ab5b4523f4b980dab0c25af41a9d614189
ms.sourcegitcommit: 1c91b7b24537d0e54d484c3379043db53c1aea65
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/29/2020
ms.locfileid: "41600681"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Gérer les applications métier dans le bureau géré Microsoft

<!--Application management -->

Il existe deux façons de gérer les mises à jour des applications pour les applications que vous avez intégrés au Bureau géré Microsoft et déployées sur vos appareils de bureau géré Microsoft. Vous pouvez effectuer des mises à jour d’application dans le portail Bureau géré Microsoft ou Intune. 

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Mettre à jour des applications métier dans le Bureau géré Microsoft

**Pour mettre à jour vos applications métier dans le portail Bureau géré Microsoft**
1. Connectez-vous au [portail d’administration du bureau géré Microsoft.](https://aka.ms/mmdportal)
2. Sous **Inventaire,** sélectionnez **Applications.**  
3. Sélectionnez l’application à mettre à jour, puis sélectionnez **Modifier.**
4. Sous **Gérer,** sélectionnez **Propriétés.** 
5. Cliquez **sur Fichier de package d’application,** puis recherchez un nouveau fichier de package d’application.
6. Sélectionnez **le fichier de package d’application.**
7. Sélectionnez l’icône du dossier et accédez à l’emplacement de votre fichier d’application mis à jour. Sélectionnez **Ouvrir**. Les informations de l’application sont mises à jour avec les informations de package.
8. Vérifiez que la **version de l’application** reflète le package d’application mis à jour. 

L’application mise à jour sera déployée sur les appareils de vos utilisateurs.

<span id="update-app-intune" />

## <a name="update-line-of-business-apps-in-intune"></a>Mettre à jour des applications métier dans Intune

**Pour mettre à jour vos applications métier dans Intune**
1. Connectez-vous au [portail Azure.](https://portal.azure.com)
2. Sélectionnez **Tous les services**  >  **Intune**. Intune se trouve dans la section **Analyse + Gestion.**
3. Sélectionnez **applications clientes > applications.**
4. Recherchez et sélectionnez votre application dans la liste des applications.
5. Dans le tableau **de** présentation, sélectionnez **Propriétés.**
6. Sélectionnez **le fichier de package d’application.**
7. Sélectionnez l’icône du dossier et accédez à l’emplacement de votre fichier d’application mis à jour. Sélectionnez **Ouvrir**. Les informations de l’application sont mises à jour avec les informations de package.
8. Vérifiez que la **version de l’application** reflète le package d’application mis à jour.

<span id="roll-back-app-mmd" />

## <a name="roll-back-an-app-to-a-previous-version"></a>Revenir à une version antérieure d’une application

Si une erreur est trouvée lors du déploiement d’une nouvelle version d’une application, vous pouvez revenir à une version précédente. Le processus décrit ici est pour les applications où le type est répertorié en tant qu’application métier **Windows MSI** ou application **Windows (Win 32) - aperçu**

**Pour revenir à une version antérieure d’une application métier**

1. Connectez-vous au [portail d’administration du bureau géré Microsoft.](https://aka.ms/mmdportal)
2. Sous **Inventaire,** sélectionnez **Applications.**  
3. Sélectionnez l’application que vous devez revenir en arrière, puis sélectionnez **Modifier.**
4. Sous **Gérer,** sélectionnez **Propriétés.** 
    - Pour les applications métier **Windows MSI,** sélectionnez Informations sur l’application, puis sous Ignorer la **version** de l’application, sélectionnez **Oui**.
    - Pour **l’application Windows (Win 32) : prévisualiser** les applications, sélectionner les informations sur **l’application,** sélectionner les règles de **détection,** puis sélectionner Ajouter . 
    S’il existe une règle MSI, vérifiez que la vérification de la version du produit **MSI** est définie sur **Non**.
5. [Téléchargez une version précédente du fichier source](../get-started/deploy-apps.md) de l’application sur le portail d’administration du bureau géré Microsoft.  

