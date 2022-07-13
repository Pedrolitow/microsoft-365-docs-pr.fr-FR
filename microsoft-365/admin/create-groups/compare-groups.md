---
title: Comparer les groupes
ms.reviewer: arvaradh
f1.keywords: CSH
ms.author: mikeplum
author: MikePlumleyMSFT
manager: serdars
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: high
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
ms.custom:
- AdminSurgePortfolio
- okr_smb
- AdminTemplateSet
- admindeeplinkMAC
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 758759ad-63ee-4ea9-90a3-39f941897b7d
description: Les membres du groupe Microsoft 365 disposent d'une messagerie de groupe et d'un espace de travail partagé pour les conversations, les fichiers et les événements du calendrier, du flux et du planificateur.
ms.openlocfilehash: cf66d4b2b2aab903934a87f64f53fa485d82f572
ms.sourcegitcommit: c314e989202dc1c9c260fffd459d53bc1f08514e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/12/2022
ms.locfileid: "66717643"
---
# <a name="compare-groups"></a>Comparer des groupes

Dans la section <a href="https://go.microsoft.com/fwlink/p/?linkid=2052855" target="_blank">**Groups**</a> du Centre d’administration Microsoft 365, vous pouvez créer et gérer les types de groupes suivants : 

- Les **Groupes Microsoft 365** sont utilisés pour la collaboration entre utilisateurs, aussi bien à l’intérieur qu’à l’extérieur de votre entreprise. Ils incluent des services de collaboration tels que SharePoint et le Planificateur.
- **Les groupes de distribution** sont utilisés pour envoyer des notifications par courrier électronique à un groupe de personnes.
- Les **Groupes de sécurité** sont utilisés pour accorder l’accès aux ressources telles que les sites SharePoint.
- Les **Groupes de sécurité à extension courrier** sont utilisés pour accorder l’accès aux ressources telles que SharePoint et envoyer par e-mail des notifications à ces utilisateurs.
- Les **Boîtes aux lettres partagées** sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique.
- Les **groupes de distribution dynamiques** sont créés pour accélérer l’envoi en masse de messages électroniques et d’autres informations au sein d’une organisation.

Certains groupes autorisent l’appartenance ou l’e-mail dynamique.

||Groupes Microsoft 365|Groupes de distribution|Groupes de sécurité|Groupes de sécurité à extension messagerie|Boîtes aux lettres partagées|Groupes de distribution dynamique|
|:----|:----|:----|:----|:----|:----|:----|
|**Mail-enabled**|Oui|Oui|Non|Oui|Oui|Oui|
|**Appartenance dynamique à Azure AD**|Oui|Non|Oui|Non|Non|Non|

Tous ces types de groupes peuvent être utilisés avec Power Automate.

## <a name="microsoft-365-groups"></a>Groupes Microsoft 365

Les Groupes Microsoft 365 sont utilisés pour la collaboration entre utilisateurs, aussi bien à l’intérieur qu’à l’extérieur de votre entreprise. Pour chaque groupe Microsoft 365, les membres bénéficient d’un e-mail de groupe et d’un espace de travail partagé pour les conversations, les fichiers et les événements de calendrier, ainsi que d’un planificateur.

Vous pouvez ajouter des personnes externes à votre organisation dans le cadre d’un groupe, à partir du moment où cette fonction est [activée par l'administrateur](manage-guest-access-in-groups.md). Vous pouvez également permettre aux expéditeurs externes d’envoyer des e-mails vers l’adresse de messagerie du groupe.

Les groupes Microsoft 365 peuvent être [configurés pour l’appartenance dynamique à Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), ce qui permet aux membres d’un groupe d’être ajoutés ou supprimés automatiquement en fonction de leurs attributs, tels que le service, le lieu, le titre, etc.

Les groupes Microsoft 365 sont accessibles via des applications mobiles comme Outlook pour iOS et Android.

Les membres du groupe peuvent Envoyer en tant que ou Envoyer de la part de l’adresse e-mail du groupe si cette fonction a été [activée par l'administrateur](../../solutions/allow-members-to-send-as-or-send-on-behalf-of-group.md).

Les Groupes Microsoft 365 prennent en charge l’imbrication via [Groupes dynamiques dans Azure Active Directory](/azure/active-directory/enterprise-users/groups-dynamic-rule-member-of).

Groupes Microsoft 365 peut être ajouté à l’un des trois groupes SharePoint (propriétaires, membres ou visiteurs) pour accorder des autorisations aux personnes sur le site.

## <a name="distribution-groups"></a>Groupes de distribution

Les [Groupes de distribution](/exchange/recipients-in-exchange-online/manage-distribution-groups/manage-distribution-groups) sont utilisés pour envoyer des notifications à un groupe de personnes. Ils peuvent recevoir des e-mails externes s’ils sont activés par l’administrateur.

Les groupes de distribution conviennent aux situations dans lesquelles vous devez diffuser des informations à un groupe de personnes, tel que « Personnes dans le bâtiment A » ou « Tout le monde chez Contoso ».

Les groupes de distribution peuvent être [mis à niveau vers des groupes Microsoft 365](../manage/upgrade-distribution-lists.md).

Les groupes de distribution peuvent être ajoutés à une équipe dans Microsoft Teams, bien que seuls les membres soient ajoutés et non le groupe lui-même.

Les groupes Microsoft 365 ne peuvent pas être membres des groupes de distribution.

## <a name="dynamic-distribution-groups"></a>Groupes de distribution dynamique 

Les [groupes de distribution dynamiques](/exchange/recipients-in-exchange-online/manage-dynamic-distribution-groups/manage-dynamic-distribution-groups) sont des groupes à extension messagerie qui sont utilisés pour envoyer des messages aux personnes avec des attributs spécifiques, tels que le service ou l’emplacement. Ces attributs sont définis dans le Centre d’administration Exchange plutôt que dans Azure AD.

Contrairement aux groupes de distribution habituels qui contiennent un ensemble défini de membres, la liste des membres de ces groupes de distribution dynamiques est calculée chaque fois qu'un message leur est envoyé, en fonction des filtres et conditions que vous avez définis. Lorsqu'un courrier électronique est envoyé à un groupe de distribution dynamique, il est remis à tous les destinataires de l'organisation qui respectent les critères définis pour ce groupe.

## <a name="security-groups"></a>Groupes de sécurité

Les [Groupes de sécurité](../email/create-edit-or-delete-a-security-group.md) sont utilisés pour accorder l’accès aux ressources Microsoft 365 telles que SharePoint. Ils peuvent simplifier l’administration, car vous n’avez qu'à gérer le groupe qu’au lieu d’ajouter de manière individuelle des utilisateurs dans chaque ressource.

Les groupes de sécurité peuvent contenir des utilisateurs ou des appareils. La création d’un groupe de sécurité pour les appareils peut être utilisée avec des services de gestion des appareils mobiles, tels que Intune.

Les groupes de sécurité peuvent être [configurés pour l’appartenance dynamique à Azure Active Directory](/azure/active-directory/users-groups-roles/groups-change-type), ce qui permet aux membres d’un groupe ou à des appareils d’être ajoutés ou supprimés automatiquement en fonction de leurs attributs, tels que le service, le lieu ou le titre, ou les attributs d'appareils comme la version du système d'exploitation.

Les groupes de sécurité peuvent être ajoutés à une équipe.

Les groupes Microsoft 365 ne peuvent pas être membres des groupes de sécurité.

## <a name="mail-enabled-security-groups"></a>Groupes de sécurité à extension messagerie

Les groupes de sécurité à extension messagerie fonctionnent de la même façon que les groupes de sécurité classiques, sauf qu’ils ne peuvent pas être gérés de façon dynamique via Azure Active Directory et qu'ils ne peuvent pas comprendre des appareils.

Ils incluent la possibilité d’envoyer des e-mails à tous les membres du groupe.

Les groupes de sécurité à accès à la messagerie peuvent être ajoutés à une équipe.

## <a name="shared-mailboxes"></a>Boîtes aux lettres partagées

Les [Boîtes aux lettres partagées](../email/create-a-shared-mailbox.md) sont utilisées lorsque plusieurs personnes doivent accéder à la même boîte aux lettres, par exemple, une information d’entreprise ou une adresse de courrier du support technique, du bureau d'accueil, ou d'un autre poste pouvant être partagé par plusieurs personnes.

Les boîtes aux lettres partagées peuvent recevoir des e-mails externes si l’administrateur a activé cette option.

Les boîtes aux lettres partagées incluent un calendrier qui peut être utilisé pour la collaboration.

Les utilisateurs disposant d’autorisations sur la boîte aux lettres du groupe peuvent Envoyer en tant que ou Envoyer de la part pour le compte de l’adresse de messagerie de la boîte aux lettres si l’administrateur leur a accordé cette autorisation. Cette fonctionnalité est particulièrement utile pour les boîtes aux lettres d’aide et de support, car les utilisateurs peuvent envoyer des e-mails à partir du « Support technique de Contoso » ou du « Bureau d'accueil du bâtiment A ».

Il n'est pas possible de migrer une boîte aux lettres partagée vers un groupe Microsoft 365.

## <a name="related-content"></a>Contenu associé

[Apprendre sur les groupes Microsoft 365](https://support.microsoft.com/office/b565caa1-5c40-40ef-9915-60fdb2d97fa2)

[Améliorer les listes de distribution vers les groupes Microsoft 365 dans Outlook](/microsoft-365/admin/manage/upgrade-distribution-lists)

[Pourquoi vous devriez mettre à niveau vos listes de distribution vers des groupes dans Outlook](https://support.microsoft.com/office/7fb3d880-593b-4909-aafa-950dd50ce188)
