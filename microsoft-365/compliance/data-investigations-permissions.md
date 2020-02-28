---
title: Affecter des autorisations pour les enquêtes sur les données (aperçu)
f1.keywords:
- NOCSH
ms.author: markjjo
author: markjjo
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.collection: M365-security-compliance
search.appverid:
- MOE150
- MET150
ms.assetid: ''
description: Cet article explique comment configurer les autorisations nécessaires pour utiliser l’outil des enquêtes de données dans Microsoft 365.
ms.openlocfilehash: 855d288c373bd2525afa3b8b7a3bbd894c4683a2
ms.sourcegitcommit: 7930fb8327bbd3594fde52f2dbf91e0f5d92f684
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/28/2020
ms.locfileid: "42328139"
---
# <a name="assign-permissions-for-data-investigations-preview"></a>Affecter des autorisations pour les enquêtes sur les données (aperçu)

Pour accéder à une enquête sur les données dans le centre de conformité Office 365 ou Microsoft 365, vous devez être membre du groupe de rôles Data investigation. Pour ajouter des membres à un groupe de rôles, vous devez être membre du groupe de rôles gestion de l’organisation ou disposer du rôle de gestion des rôles dans le centre de sécurité & conformité. Une fois qu’un utilisateur est membre du groupe de rôles Data investigation, il peut créer, consulter et mener des enquêtes dans les enquêtes de données dont vous êtes membre.

Pour attribuer des autorisations d’investigation de données :

1. Accédez à [https://protection.office.com](https://protection.office.com) et connectez-vous à l’aide des informations d’identification d’un compte d’administrateur de votre organisation.

2. Dans le centre de sécurité & conformité, cliquez sur **autorisations**.

3. Cliquez sur le groupe de rôles **Data investigation** , puis en regard de **membres** sur la page de menu volant, cliquez sur **modifier**.

4. Cliquez sur **choisir les membres** , puis sur **Ajouter**. Sélectionnez les utilisateurs que vous souhaitez ajouter en tant qu’utilisateurs de données, puis cliquez sur **Ajouter**.

5. Une fois que vous avez ajouté tous les utilisateurs, cliquez sur **Terminer** , puis sur **Enregistrer** pour enregistrer les modifications apportées au groupe de rôles.

> [!NOTE]
> Le rôle de gestion de l’accès aux données affecté au groupe de rôles Data investigation fournit les autorisations nécessaires pour accéder à l’outil d’investigation de données dans le centre de conformité Office 365 ou Microsoft 365. Par défaut, ce rôle n’est pas attribué au groupe de rôles gestion de l’organisation, ce qui signifie que les administrateurs globaux de votre organisation ne pourront peut-être pas accéder à l’outil d’examen des données par défaut. Pour résoudre ce problème, vous pouvez ajouter des administrateurs globaux au groupe de rôles Data investigation ou ajouter le rôle de gestion de l’enquête sur les données au groupe de rôles gestion de l’organisation. Une troisième option consiste à créer un groupe de rôles personnalisé et à attribuer le rôle de gestion de l’examen des données (et d’autres rôles), puis à ajouter les membres appropriés. Pour plus d’informations sur les groupes de rôles et les rôles, voir [Permissions in the Office 365 Security & Compliance Center](https://docs.microsoft.com/microsoft-365/security/office-365-security/permissions-in-the-security-and-compliance-center).
