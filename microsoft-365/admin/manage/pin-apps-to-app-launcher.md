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

Vous pouvez utiliser des contrôles dans le portail Azure Active Directory pour épingler jusqu’à trois applications à Office.com et le lanceur d’applications pour tous les utilisateurs de votre organisation. Vous pouvez également organiser des groupes d’applications. Toute application que vous ajoutez peut être désépinglée ultérieurement par l’utilisateur à tout moment. Pour épingler une application pour vos utilisateurs, vous devez être un administrateur d’application Cloud ou un administrateur d’application dans Azure Active Directory, ou un administrateur global dans Office 365. Pour plus d’informations sur les rôles d’administrateur, consultez la rubrique [rôles d’administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles) et [rôles d’administrateur dans Microsoft 365](../add-users/about-admin-roles.md). 

Pour plus d’informations sur le lanceur d’applications et Office.com, consultez l’article relatif [au lanceur d’applications](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) et [aux mises à jour vers Office.com et à l’article du blog du lanceur d’applications Office 365](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503) .

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Utiliser le portail Azure Active Directory pour épingler des applications

1. Accédez au centre d’administration Microsoft 365 à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .
2. Dans le volet de navigation de gauche, choisissez **Afficher tout**, puis sous **centres d’administration**, sélectionnez **Azure Active Directory**.
3. Dans **Azure Active Directory**, choisissez **Enterprise applications**  >  **paramètres utilisateur**des applications d’entreprise.
4. Dans la section **paramètres Office 365** , sélectionnez **Ajouter une application**.
5. Choisissez les applications que vous souhaitez épingler au lanceur d’applications des utilisateurs, puis choisissez **Ajouter**.

:::image type="content" source="../../media/add-apps.png" alt-text="Paramètres Microsoft 365 pour épingler des applications.":::

### <a name="pin-a-custom-app"></a>Épingler une application personnalisée

> [!NOTE]
> L’interface utilisateur indiquera si vous avez besoin d’acheter des licences Azure AD supplémentaires pour utiliser cette fonctionnalité. Pour plus d’informations, consultez la rubrique [tarification Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

1. Dans **Azure Active Directory**, sélectionnez **applications d’entreprise**  >  **nouvelle application** en haut de la page **toutes les applications** .
2. Sur la page **Ajouter une application** , choisissez **application non-Galerie** ou **créer votre propre application** si vous êtes dans la version préliminaire d’Azure Active Directory. 
3. Tapez un nom pour l’application, puis attribuez un utilisateur sous l’onglet **utilisateurs et groupes** .
4. Utilisez l’onglet **Propriétés** pour charger une icône pour l’application.
5. Pour affecter une URL à l’application, dans l’onglet **authentification unique** , choisissez **lié** , puis entrez une URL.
6. Cliquez sur **Enregistrer**.

## <a name="create-application-collections"></a>Créer des collections d’applications

Vous pouvez également créer des collections d’applications pour les utilisateurs de votre organisation. Pour obtenir des instructions, consultez la rubrique [créer des collections dans le portail mes applications dans le portail Azure](https://docs.microsoft.com/azure/active-directory/manage-apps/access-panel-collections).