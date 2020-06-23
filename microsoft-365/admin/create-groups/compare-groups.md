---
title: Comparer les groupes
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: pamgreen
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Priority
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 758759ad-63ee-4ea9-90a3-39f941897b7d
description: Découvrez les types de groupes que vous pouvez utiliser.
ms.openlocfilehash: 333d929e72647421951eefa50508c23dddc196ac
ms.sourcegitcommit: 659adf65d88ee44f643c471e6202396f1ffb6576
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/17/2020
ms.locfileid: "44780456"
---
# <a name="compare-groups"></a>Comparer des groupes

Dans la section **Groupes** du Centre d’administration Microsoft 365, vous pouvez créer et gérer les types de groupes suivants : 

- **Microsoft 365 Groups** (anciennement groupes Office 365) est utilisé pour la collaboration entre les utilisateurs, à l’intérieur et à l’extérieur de votre entreprise.
- Les **Groupes de distribution** sont utilisés pour envoyer des notifications à un groupe de personnes.
- Les **Groupes de sécurité** sont utilisés pour accorder l’accès aux ressources telles que les sites SharePoint.
- Les **Groupes de sécurité à extension courrier** sont utilisés pour accorder l’accès aux ressources telles que SharePoint et envoyer par e-mail des notifications à ces utilisateurs.
- Les **Boîtes aux lettres partagées** sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique.

## <a name="microsoft-365-groups"></a>Groupes Microsoft 365

Les Groupes Microsoft 365 sont utilisés pour la collaboration entre utilisateurs, aussi bien à l’intérieur qu’à l’extérieur de votre entreprise. Pour chaque groupe Microsoft 365, les membres bénéficient d’un e-mail de groupe et d’un espace de travail partagé pour les conversations, les fichiers et les événements de calendrier, ainsi que d’un Planificateur.

Vous pouvez ajouter des personnes externes à votre organisation dans le cadre d’un groupe, à partir du moment où cette fonction est [activée par l'administrateur](manage-guest-access-in-groups.md). Vous pouvez également permettre aux expéditeurs externes d’envoyer des e-mails vers l’adresse de messagerie du groupe.

Les groupes Microsoft 365 peuvent être [configurés pour l’appartenance dynamique à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type), ce qui permet aux membres d’un groupe d’être ajoutés ou supprimés automatiquement en fonction de leurs attributs, tels que le service, le lieu, le titre, etc.

Les groupes Microsoft 365 sont accessibles via des applications mobiles comme Outlook pour iOS et Android.

Les membres du groupe peuvent Envoyer en tant que ou Envoyer de la part de l’adresse e-mail du groupe si cette fonction a été [activée par l'administrateur](allow-members-to-send-as-or-send-on-behalf-of-group.md).

## <a name="distribution-groups"></a>Groupes de distribution

Les [Groupes de distribution](https://docs.microsoft.com/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) sont utilisés pour envoyer des notifications à un groupe de personnes. Ils peuvent recevoir des e-mails externes s’ils sont activés par l’administrateur.

Les groupes de distribution conviennent aux situations dans lesquelles vous devez diffuser des informations à un groupe de personnes, tel que « Personnes dans le bâtiment A » ou « Tout le monde chez Contoso ».

## <a name="security-groups"></a>Groupes de sécurité

Les [Groupes de sécurité](../email/create-edit-or-delete-a-security-group.md) sont utilisés pour accorder l’accès aux ressources Microsoft 365 telles que SharePoint. Ils peuvent simplifier l’administration, car vous n’avez qu'à gérer le groupe qu’au lieu d’ajouter de manière individuelle des utilisateurs dans chaque ressource.

Les groupes de sécurité peuvent inclure des utilisateurs ou des appareils. La création d’un groupe de sécurité pour des appareils peut être utilisée avec des services de gestion d'appareils mobiles, tels que Intune.

Les groupes de sécurité peuvent être [configurés pour l’appartenance dynamique à Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-change-type), ce qui permet aux membres d’un groupe ou à des appareils d’être ajoutés ou supprimés automatiquement en fonction de leurs attributs, tels que le service, le lieu ou le titre, ou les attributs d'appareils comme la version du système d'exploitation.

## <a name="mail-enabled-security-groups"></a>Groupes de sécurité à extension messagerie

Les groupes de sécurité à extension messagerie fonctionnent de la même façon que les groupes de sécurité classiques, sauf qu’ils ne peuvent pas être gérés de façon dynamique via Azure Active Directory et qu'ils ne peuvent pas comprendre des appareils.

Ils incluent la possibilité d’envoyer des e-mails à tous les membres du groupe.

## <a name="shared-mailboxes"></a>Boîtes aux lettres partagées

Les [Boîtes aux lettres partagées](../email/create-a-shared-mailbox.md) sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique, du bureau d'accueil, ou d'un autre poste pouvant être partagé par plusieurs personnes.

Les boîtes aux lettres partagées peuvent recevoir des e-mails externes si l’administrateur a activé cette option.

Les utilisateurs disposant d’autorisations sur la boîte aux lettres du groupe peuvent Envoyer en tant que ou Envoyer de la part pour le compte de l’adresse de messagerie de la boîte aux lettres si l’administrateur leur a accordé cette autorisation. Cette fonctionnalité est particulièrement utile pour les boîtes aux lettres d’aide et de support, car les utilisateurs peuvent envoyer des e-mails à partir du « Support technique de Contoso » ou du « Bureau d'accueil du bâtiment A ».

Pour le moment, il n'est pas possible de migrer une boîte aux lettres partagée vers un groupe Microsoft 365. Est-ce une fonction que vous souhaitez avoir ? Faites-le nous savoir. **[Votez ici](https://go.microsoft.com/fwlink/?linkid=871518)**.

## <a name="related-articles"></a>Articles connexes

[En savoir plus sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)
