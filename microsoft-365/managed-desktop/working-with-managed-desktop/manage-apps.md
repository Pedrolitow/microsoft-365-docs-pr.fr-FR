---
title: Gérer les applications dans Bureau géré Microsoft
description: Informations sur la mise à jour des applications métier déployées sur Bureau géré Microsoft appareils
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
f1.keywords:
- NOCSH
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.localizationpriority: normal
ms.date: 01/18/2019
ms.collection: M365-modern-desktop
ms.openlocfilehash: b016d8458b4b4cc9f6b684d3b8a3c0a1e1322fef
ms.sourcegitcommit: be929f79751c0c52dfa6bd98a854432a0c63faf0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/14/2021
ms.locfileid: "52925406"
---
# <a name="manage-line-of-business-apps-in-microsoft-managed-desktop"></a>Gérer les applications métier dans le bureau géré Microsoft

<!--Application management -->

Il existe deux façons de gérer les mises à jour d’application pour les applications que vous avez intégrés à Bureau géré Microsoft et déployés sur vos appareils Bureau géré Microsoft. Vous pouvez effectuer des mises à jour d’application dans Bureau géré Microsoft portail ou Intune. 

<span id="update-app-mmd" />

## <a name="update-line-of-business-apps-in-microsoft-managed-desktop"></a>Mettre à jour des applications métier dans Bureau géré Microsoft

**Pour mettre à jour vos applications métier dans Bureau géré Microsoft web**
1. Connectez-vous [Bureau géré Microsoft portail d’administration.](https://aka.ms/mmdportal)
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

Si une erreur est trouvée lors du déploiement d’une nouvelle version d’une application, vous pouvez revenir à une version précédente. Le processus décrit ici est pour les applications où le type est répertorié comme Windows application métier **MSI** ou **application Windows (Win 32) : prévisualisation**

**Pour revenir à une version antérieure d’une application métier**

1. Connectez-vous [Bureau géré Microsoft portail d’administration.](https://aka.ms/mmdportal)
2. Sous **Inventaire,** sélectionnez **Applications.**  
3. Sélectionnez l’application que vous devez revenir en arrière, puis sélectionnez **Modifier.**
4. Sous **Gérer,** sélectionnez **Propriétés.** 
    - Pour Windows applications **métier MSI,** sélectionnez Informations sur l’application, puis sous Ignorer la **version** de l’application, sélectionnez **Oui**.
    - For **Windows app (Win 32) - preview** apps, select App **information,** select **Detection rules,** and then select **Add**. 
    S’il existe une règle MSI, vérifiez que la vérification de la version du produit **MSI** est définie sur **Non**.
5. [Télécharger une version précédente du fichier source](../get-started/deploy-apps.md) de l’application sur Bureau géré Microsoft portail d’administration.  

