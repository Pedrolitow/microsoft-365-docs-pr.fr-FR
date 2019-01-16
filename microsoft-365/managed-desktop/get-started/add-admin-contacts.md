---
title: Ajouter des contacts d’administration dans le portail d’administration d’ordinateur de bureau Microsoft
description: Indiquez les personnes à contacter pour chaque zone de focus.
keywords: Service Microsoft de bureau, Microsoft 365, documentation
ms.service: m365-md
author: trudyha
ms.localizationpriority: normal
ms.date: 09/24/2018
ms.openlocfilehash: 31984609681b6e3b1b6de9996eb8fb0fcf6f5624
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867018"
---
# <a name="add-admin-contacts-in-microsoft-managed-desktop-admin-portal"></a>Ajouter des contacts d’administration dans le portail d’administration de bureau géré Microsoft

Il existe plusieurs manières de service de l’ordinateur de bureau Microsoft communique avec les clients. Pour simplifier la communication et garantir que nous vérifions avec les contacts meilleures, vous devez fournir un ensemble de contacts d’administration. Les opérations informatiques de bureau géré Microsoft contacte ces personnes pour obtenir une assistance de résolution des problèmes pour votre client. 

## <a name="azure-active-directory-access-for-microsoft-managed-desktop-admin-portal"></a>Accès à Active Directory pour le portail d’administration de bureau géré Microsoft Azure

Portail d’administration de bureau géré Microsoft nécessite que personnes l’accès au portail un de ces rôles d’Azure Active Directory (AD) :
- Administrateur général
- Administrateur de Service Intune
- Administrateur de facturation
- Administrateur de service prise en charge

L’administrateur Global doit être celui pour inscrire le client de bureau Microsoft.  Les cinq rôles ont le même accès au sein du portail d’administration pour lancer et afficher les tâches.  Pour plus d’informations sur l’attribution de ces rôles dans Azure AD, voir [autorisations de rôle administrateur dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). 

## <a name="admin-contact-focus-areas"></a>Domaines contact d’administration

Contacts d’administration doivent être la meilleure personne ou un groupe qui peut répondre aux questions et prendre des décisions de différents domaines.  Opérations de bureau géré Microsoft contacte ces contacts d’administration pour toute question concernant les demandes de prise en charge par le client.  Ces contacts Admin reçoivent des notifications pour les mises à jour de demande de prise en charge et de nouveaux messages.  Ces domaines sont les suivantes :

Zone de focus | Pour toute question concernant
--- | ---
Applications | Résolution des problèmes d’empaquetage de l’application
 Appareils  | État de santé, résolution des problèmes avec les périphériques de bureau Microsoft
Sécurité | Résolution des problèmes de sécurité avec des périphériques de bureau Microsoft
Autre | Pour les problèmes non couverts par les autres domaines

Toute personne que vous choisissez pour ces contacts doit disposer de la base de connaissances et l’autorité de prendre des décisions pour votre environnement de bureau Microsoft. Lorsque vous intégrée de Microsoft géré environnement de bureau, vous êtes invité à ajouter des contacts de votre support technique et de sécurité locale. 

Contacts d’administration sont requis lorsque vous [soumettre une demande de prise en charge](../working-with-managed-desktop/support.md). Vous devez disposer d’un contact de l’administrateur de la zone de focus de la demande de prise en charge. 

**Pour ajouter des contacts d’administration**

1.  Connectez-vous au [portail d’administration d’ordinateur de bureau Microsoft](http://aka.ms/mwaasportal). 

2.  Sous **prise en charge**, sélectionnez **les contacts d’administration**. 

    ![Menu de prise en charge, les contacts d’administration](images/admincontacts.png)

3. Sélectionnez **Ajouter**.

    ![Bouton Ajouter un portail d’administration](images/adminadd.png)

4.  Sélectionnez une **zone du focus** , entrez les informations du contact. 

    ![la liste de domaines](images/areaoffocus.png)

5. Répétez pour chaque zone de focus. 

