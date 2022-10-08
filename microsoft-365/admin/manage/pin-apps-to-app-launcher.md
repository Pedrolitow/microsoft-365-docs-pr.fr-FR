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
- scotvorg
- Adm_O365
- M365-subscription-management
- Adm_TOC
ms.service: microsoft-365-business
ms.custom: admindeeplinkMAC
ms.localizationpriority: medium
description: En tant qu’administrateur général, vous pouvez épingler jusqu’à trois applications au lanceur d’applications de vos utilisateurs.
ms.openlocfilehash: 0d187c6dfb9bf9422465865033d1eb623d6b7c07
ms.sourcegitcommit: 0b7070ec119e00e0dafe030bbfbef0ae5c9afa19
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2022
ms.locfileid: "68187182"
---
# <a name="pin-apps-to-your-users-app-launcher"></a>Épingler des applications au lanceur d’applications de vos utilisateurs

Vous pouvez utiliser des contrôles dans le portail Azure Active Directory pour épingler jusqu’à trois applications à Office.com et le lanceur d’applications pour tous les utilisateurs de votre organisation. Vous pouvez également organiser des groupes d’applications. Toute application que vous ajoutez peut être désépinglée par l’utilisateur à tout moment. Pour épingler une application pour vos utilisateurs, vous devez être administrateur d’application cloud, administrateur d’application dans Azure Active Directory ou Administrateur général dans Microsoft 365. Pour plus d’informations sur les rôles d’administrateur, consultez [les rôles intégrés Azure AD](/azure/active-directory/roles/permissions-reference) et les [rôles d’administrateur dans Microsoft 365](../add-users/about-admin-roles.md). 

Pour plus d’informations sur le lanceur d’applications et les Office.com, consultez l’article de blog [sur le lanceur d’applications](https://support.microsoft.com/office/79f12104-6fed-442f-96a0-eb089a3f476a) et les [mises à jour de office.com et du lanceur d’applications Office 365](https://techcommunity.microsoft.com/t5/office-365-blog/updates-to-office-com-and-the-office-365-app-launcher/ba-p/1150503).

## <a name="use-the-azure-active-directory-portal-to-pin-apps"></a>Utiliser le portail Azure Active Directory pour épingler des applications

> [!NOTE]
> Les applications Microsoft 365 sont exclues de cette liste, car elles sont déjà affichées dans le lanceur d’applications.

1. Accédez au Centre d'administration Microsoft 365 sur <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.
2. Dans le volet de navigation de gauche, choisissez **Afficher tout** et, sous **Administration centres**, choisissez **Azure Active Directory**.
3. Dans **Azure Active Directory**, choisissez Paramètres utilisateur **des applications** > **d’entreprise**.
4. Dans la section **Paramètres Office 365**, choisissez **Ajouter une application**.
5. Choisissez les applications que vous souhaitez épingler au lanceur d’applications des utilisateurs, puis choisissez **Ajouter**.

:::image type="content" source="../../media/add-apps.png" alt-text="Paramètres Microsoft 365 pour épingler des applications.":::

### <a name="pin-a-custom-app"></a>Épingler une application personnalisée

> [!NOTE]
> L’interface utilisateur indique si vous devez acheter des licences Azure AD supplémentaires pour utiliser cette fonctionnalité. Pour plus d’informations, consultez [la tarification d’Azure Active Directory](https://azure.microsoft.com/pricing/details/active-directory/).

1. Dans **Azure Active Directory**, choisissez **Applications** >  d’entreprise **Nouvelle application** en haut de la page **Toutes les applications**.
2. Dans la page **Ajouter une application** , choisissez **Une application autre** que la galerie ou **Créez votre propre application** si vous êtes dans la préversion d’Azure Active Directory. 
3. Tapez un nom pour l’application, puis attribuez un utilisateur dans l’onglet **Utilisateurs et groupes** .
4. Utilisez l’onglet **Propriétés** pour charger une icône pour l’application.
5. Pour affecter une URL à l’application, sous l’onglet **Authentification unique** , choisissez **Lié** , puis entrez une URL.
6. Cliquez sur **Enregistrer**.

## <a name="create-application-collections"></a>Créer des collections d’applications

Vous pouvez également créer des collections d’applications pour les utilisateurs de votre organisation. Pour obtenir des instructions, consultez [créer des collections sur le portail Mes applications dans le Portail Azure](/azure/active-directory/manage-apps/access-panel-collections).