---
title: Épingler des applications au lanceur d’applications de vos utilisateurs
f1.keywords:
- NOCSH
ms.author: kwekua
author: kwekua
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- M365-subscription-management
ms.service: o365-administration
localization_priority: Normal
description: En tant qu’administrateur général, vous pouvez épingler jusqu’à trois applications au lanceur d’applications de vos utilisateurs.
ms.openlocfilehash: 6569b05f29a2219c9d1d6c847e65cd29043d80fd82d5e499e2af57ba96af0da9
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53825009"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>Épingler des applications au lanceur d’applications de vos utilisateurs

Vous pouvez utiliser les contrôles du portail Azure Active Directory pour épingler jusqu’à trois applications à Office.com et au lanceur d’applications pour tous les utilisateurs de votre organisation. Vous pouvez également organiser des groupes d’applications. Toute application que vous ajoutez peut être désépinée ultérieurement par l’utilisateur à tout moment. Pour épingler une application pour vos utilisateurs, vous devez être administrateur d’application cloud, administrateur d’application dans Azure Active Directory ou administrateur général dans Office 365. Pour plus d’informations sur les rôles d’administrateur, voir rôles d’administrateur [dans Azure Active Directory](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) et [rôles d’administrateur dans Microsoft 365](../add-users/about-admin-roles.md). 

Pour plus d’informations sur le lanceur d’applications [](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) et Office.com, consultez l’article du lanceur d’applications et les mises à jour de office.com et du lanceur d’applications [Office 365.com.](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503)

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Utiliser le portail Azure Active Directory pour épingler des applications

1. Go to the Centre d’administration Microsoft 365 at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .
2. In the left nav, choose **Show all**, and under **Admin centers**, choose **Azure Active Directory**.
3. In **Azure Active Directory**, choose **Enterprise applications** User  >  **settings**.
4. Dans la **section Office 365 Paramètres,** choisissez **Ajouter une application.**
5. Choisissez les applications que vous souhaitez épingler au lanceur d’applications des utilisateurs, puis choisissez **Ajouter**.

:::image type="content" source="../../media/add-apps.png" alt-text="Microsoft 365 pour épingler des applications.":::

### <a name="pin-a-custom-app"></a>Épingler une application personnalisée

> [!NOTE]
> L’interface utilisateur indique si vous devez acheter des licences Azure AD supplémentaires pour utiliser cette fonctionnalité. Pour plus d’informations, [voir Azure Active Directory tarification.](https://azure.microsoft.com/pricing/details/active-directory/)

1. In **Azure Active Directory**, choose **Enterprise applications** New  >  **application** on the top of the All **applications** page.
2. Dans la page Ajouter une **application,** choisissez **application non galerie** ou Créez votre propre **application** si vous êtes dans la version d’aperçu de Azure Active Directory. 
3. Tapez un nom pour l’application, puis attribuez un utilisateur dans l’onglet **Utilisateurs et** groupes.
4. Utilisez **l’onglet Propriétés** pour télécharger une icône pour l’application.
5. Pour affecter une URL à l’application, sous l’onglet **Sign-on** unique, choisissez **Lié,** puis entrez une URL.
6. Cliquez sur **Enregistrer**.

## <a name="create-application-collections"></a>Créer des collections d’applications

Vous pouvez également créer des collections d’applications pour les utilisateurs de votre organisation. Pour obtenir des instructions, voir [créer des collections sur le portail Mes applications dans le portail Azure.](/azure/active-directory/manage-apps/access-panel-collections)