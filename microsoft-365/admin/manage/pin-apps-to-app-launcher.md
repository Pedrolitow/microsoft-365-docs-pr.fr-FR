---
title: Épingler des applications au lanceur d’applications de vos utilisateurs
f1.keywords:
- NOCSH
ms.author: sirkkuw
author: sirkkuw
manager: scotv
audience: Admin
ms.topic: article
ms.collection:
- Adm_O365
- M365-subscription-management
ms.service: o365-administration
localization_priority: Normal
description: En tant qu’administrateur général, vous pouvez épingler jusqu’à trois applications au lanceur d’applications de vos utilisateurs.
ms.openlocfilehash: d9b95a20f332a9b1f2f6b0ebba28a70c58677b58
ms.sourcegitcommit: 87449335d9a1124ee82fa2e95e4745155a95a62f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2020
ms.locfileid: "47310874"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>Épingler des applications au lanceur d’applications de vos utilisateurs

Vous pouvez utiliser des contrôles dans le portail Azure Active Directory pour épingler jusqu’à trois applications à Office.com et le lanceur d’applications pour tous les utilisateurs de votre organisation. Vous pouvez également organiser des groupes d’applications. Toute application que vous ajoutez peut être désépinée ultérieurement par l’utilisateur à tout moment. Pour épingler une application pour vos utilisateurs, vous devez être administrateur d’application cloud, administrateur d’application dans Azure Active Directory ou administrateur général dans Office 365. Pour plus d’informations sur les rôles d’administrateur, voir rôles d’administrateur [dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) et rôles d’administrateur [dans Microsoft 365.](../add-users/about-admin-roles.md) 

Pour plus d’informations sur le lanceur d’applications et les Office.com, consultez l’article du lanceur d’applications et les mises à jour de office.com et de l’article de blog du lanceur d’applications [Office 365.](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503) [](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a)

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Utiliser le portail Azure Active Directory pour épingler des applications

1. Go to the Microsoft 365 admin center at <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .
2. In the left nav, choose **Show all**, and under **Admin centers**, choose Azure **Active Directory**.
3. Dans **Azure Active Directory**, choisissez les **paramètres** utilisateur des applications  >  **d’entreprise.**
4. Dans la section **Paramètres Office 365,** choisissez **Ajouter une application.**
5. Choisissez les applications que vous souhaitez épingler au lanceur d’applications des utilisateurs, puis choisissez **Ajouter**.

:::image type="content" source="../../media/add-apps.png" alt-text="Paramètres Microsoft 365 pour épingler des applications.":::

### <a name="pin-a-custom-app"></a>Épingler une application personnalisée

> [!NOTE]
> L’interface utilisateur indique si vous devez acheter des licences Azure AD supplémentaires pour utiliser cette fonctionnalité. Pour plus d’informations, [voir tarification Azure Active Directory.](https://azure.microsoft.com/pricing/details/active-directory/)

1. Dans **Azure Active Directory, choisissez** Applications **d’entreprise** Nouvelle application en  >   haut de la page Toutes **les applications.**
2. Dans la page **Ajouter une application,** choisissez **Application non** galerie ou Créez votre propre **application** si vous êtes dans la version d’aperçu d’Azure Active Directory. 
3. Tapez un nom pour l’application, puis attribuez un utilisateur dans l’onglet **Utilisateurs et** groupes.
4. Utilisez **l’onglet Propriétés** pour télécharger une icône pour l’application.
5. Pour affecter une URL à l’application, sous l’onglet **Sign-on** unique, choisissez **Lié,** puis entrez une URL.
6. Cliquez sur **Enregistrer**.

## <a name="create-application-collections"></a>Créer des collections d’applications

Vous pouvez également créer des collections d’applications pour les utilisateurs de votre organisation. Pour obtenir des instructions, voir [créer des collections sur le portail Mes applications dans le portail Azure.](https://docs.microsoft.com/azure/active-directory/manage-apps/access-panel-collections)