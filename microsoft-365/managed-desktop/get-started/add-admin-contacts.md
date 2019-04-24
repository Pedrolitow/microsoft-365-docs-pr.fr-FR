---
title: Ajouter des contacts d'administration dans le portail d'administration de bureau géré Microsoft
description: Dites-nous qui contacter pour chaque zone de focus.
keywords: Microsoft maNaged Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.collection: M365-modern-desktop
ms.openlocfilehash: 014404ab38ff5871289be186dec150115c3be6ec
ms.sourcegitcommit: 81273a9df49647286235b187fa2213c5ec7e8b62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "32277533"
---
# <a name="add-admin-contacts-in-microsoft-managed-desktop-admin-portal"></a>Ajouter des contacts d'administration dans le portail d'administration de bureau géré Microsoft

Le service de bureau géré Microsoft communique de plusieurs façons avec les clients. Pour simplifier la communication et vérifier que nous vérifions les meilleurs contacts, vous devez fournir un ensemble de contacts d'administration. Les opérations informatiques de bureau gérées par Microsoft contacteront ces personnes pour résoudre les problèmes de résolution des problèmes pour votre client. 

## <a name="azure-active-directory-access-for-microsoft-managed-desktop-admin-portal"></a>Accès Azure Active Directory pour le portail d'administration de bureau géré Microsoft

Le portail d'administration de bureau géré Microsoft exige que les utilisateurs qui accèdent au portail disposent de l'un de ces rôles Azure Active Directory (AD):
- Administrateur général
- Administrateur du service Intune
- Administrateur de facturation
- Administrateur de support de service

L'administrateur général doit être celui pour inscrire le client dans le bureau géré Microsoft.  Les cinq rôles ont le même accès dans le portail d'administration pour lancer et afficher les tâches.  Pour plus d'informations sur l'affectation de ces rôles dans Azure AD, reportez-vous à la rubrique [Administrator Role Permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). 

## <a name="admin-contact-focus-areas"></a>Zones ciblées des contacts administratifs

Les contacts d'administration doivent être la personne ou le groupe le mieux adapté pour répondre aux questions et prendre des décisions concernant différentes priorités.  Les opérations de bureau géré Microsoft contacteront ces contacts d'administration pour les questions portant sur les demandes de support déposées par le client.  Ces contacts d'administration recevront des notifications pour les mises à jour des demandes de support et les nouveaux messages.  Ces domaines sont les suivants:

Zone de focus | Pour obtenir des questions sur
--- | ---
Applications | Résolution des problèmes d'emPaquetage d'applications
Appareils | Intégrité de l'appareil, résolution des problèmes avec les appareils de bureau gérés Microsoft
Sécurité | Résolution des problèmes de sécurité avec les appareils de bureau gérés Microsoft
Autre | Pour les problèmes non couverts par d'autres domaines

Les personnes que vous choisissez pour ces contacts doivent disposer des connaissances et des pouvoirs nécessaires pour prendre des décisions concernant votre environnement de bureau géré Microsoft. Lorsque vous intégrez votre environnement de bureau géré Microsoft, vous êtes invité à ajouter des contacts pour votre service d'assistance et sécurité locaux. 

Les contacts d'administration sont requis lorsque vous [envoyez une demande de support](../working-with-managed-desktop/support.md). Vous devez disposer d'un contact administrateur pour la zone de sélection de la demande de support. 

**Pour ajouter des contacts d'administration**

1.  Connectez-vous au [portail d'administration de bureau géré Microsoft](http://aka.ms/mwaasportal). 

2.  Sous **support**, sélectionnez **contacts d'administration**. 

    ![Menu support, contacts administrateur](images/admincontacts.png)

3. Cliquez sur **Ajouter**.

    ![Bouton Ajouter du portail d'administration](images/adminadd.png)

4.  Sélectionnez une **zone de** sélection, puis entrez les informations du contact. 

    ![Liste des zones ciblées](images/areaoffocus.png)

5. Répétez l'opération pour chaque zone de focus. 

