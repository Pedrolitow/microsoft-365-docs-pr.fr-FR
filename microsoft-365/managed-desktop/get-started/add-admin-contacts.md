---
title: Ajouter et vérifier des contacts d’administrateur dans le portail d’administration
description: Dites-nous qui contacter pour chaque zone de focus.
keywords: Microsoft Managed Desktop, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.openlocfilehash: 5a980c1e15a6cbc098647139caf48f813b36b040
ms.sourcegitcommit: 3dd9944a6070a7f35c4bc2b57df397f844c3fe79
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2020
ms.locfileid: "42085892"
---
# <a name="add-and-verify-admin-contacts-in-the-admin-portal"></a>Ajouter et vérifier des contacts d’administrateur dans le portail d’administration

Le service de bureau géré Microsoft communique de plusieurs façons avec les clients. Pour simplifier la communication et vérifier que nous vérifions les personnes appropriées, vous devez fournir un ensemble de contacts d’administration. Les opérations informatiques de bureau gérées par Microsoft contacteront ces personnes pour résoudre les problèmes de résolution des problèmes pour votre client.

> [!IMPORTANT]
> Vous avez peut-être déjà ajouté ces contacts dans le portail d’administration. Si c’est le cas, prenez le temps de vérifier que la liste des contacts est exacte, car Microsoft Managed Desktop **doit** être en mesure de les joindre en cas d’incident grave.

## <a name="azure-active-directory-access-for-microsoft-managed-desktop-admin-portal"></a>Accès Azure Active Directory pour le portail d’administration de bureau géré Microsoft

Le portail d’administration de bureau géré Microsoft exige que les utilisateurs qui accèdent au portail disposent de l’un de ces rôles Azure Active Directory (AD) :
- Administrateur général
- Administrateur du service Intune
- Lecteur général
- Administrateur de support de service

L’administrateur général doit être celui pour inscrire votre organisation dans le bureau géré Microsoft. Les cinq rôles ont le même accès dans le portail d’administration pour lancer et afficher les tâches. Pour plus d’informations sur l’affectation de ces rôles dans Azure AD, reportez-vous à la rubrique [Administrator Role Permissions in Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/directory-assign-admin-roles). 

## <a name="admin-contact-areas-of-focus"></a>Zones de contact de l’administrateur

Les contacts d’administration doivent être la personne ou le groupe le mieux adapté pour répondre aux questions et prendre des décisions pour différentes zones de focus. **Les opérations de bureau géré Microsoft contacteront ces contacts d’administration pour les questions portant sur les demandes de support déposées par le client.** Ces contacts d’administration recevront des notifications pour les mises à jour des demandes de support et les nouveaux messages. Ces domaines sont les suivants :

Zone de focus | Pour obtenir des questions sur
--- | ---
Empaquetage d’applications | Résolution des problèmes d’empaquetage d’applications
Appareils | Intégrité de l’appareil, résolution des problèmes avec les appareils de bureau gérés Microsoft
Sécurité | Résolution des problèmes de sécurité avec les appareils de bureau gérés Microsoft
Support technique informatique | dans les cas où notre équipe de support technique effectue des tickets d’utilisateur final en dehors des zones de support de bureau géré Microsoft 
Autres | Pour les problèmes non couverts par d’autres domaines

**Les personnes que vous choisissez pour ces contacts doivent disposer des connaissances et des pouvoirs nécessaires pour prendre des décisions concernant votre environnement de bureau géré Microsoft.** Lorsque vous intégrez votre environnement de bureau géré Microsoft, vous êtes invité à ajouter des contacts pour votre service d’assistance et sécurité locaux. 

Les contacts d’administration sont requis lorsque vous [envoyez une demande de support](../service-description/support.md). Vous devez disposer d’un contact administrateur pour la zone de sélection de la demande de support. 

**Pour ajouter des contacts d’administration**

1.  Connectez-vous au [portail d’administration de bureau géré Microsoft](https://aka.ms/mwaasportal). 

2.  Sous **support**, sélectionnez **contacts d’administration**. 

    ![Menu support, contacts administrateur dans la partie supérieure sélectionnée](../../media/admincontacts.png)

3. Sélectionnez **Ajouter**.

    ![Portail d’administration, bouton Ajouter, à gauche de l’option Exporter et actualiser](../../media/adminadd.png)

4.  Sélectionnez une **zone de** sélection, puis entrez les informations du contact. 

    ![Liste des domaines ciblés, tels que les autres, les applications et la sécurité](../../media/areaoffocus.png)

5. Répétez l’opération pour chaque zone de focus. 

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de prise en main de Microsoft Managed Desktop

1. Ajouter et vérifier des contacts d’administration dans le portail d’administration (cette rubrique)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. [Installer le portail d’entreprise Intune sur sur les appareils](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer des appareils de bureau géré Microsoft](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation des appareils](get-started-devices.md)
8. [Déployer des applications sur des appareils](deploy-apps.md)
