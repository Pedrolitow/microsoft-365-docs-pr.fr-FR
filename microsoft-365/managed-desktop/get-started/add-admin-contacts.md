---
title: Ajouter et vérifier des contacts d’administrateur dans le portail d’administration
description: Indiquez-nous qui contacter pour chaque domaine de travail.
keywords: Bureau géré Microsoft, Microsoft 365, service, documentation
ms.service: m365-md
author: jaimeo
ms.localizationpriority: normal
ms.collection: M365-modern-desktop
ms.author: jaimeo
manager: laurawi
ms.topic: article
ms.openlocfilehash: 18823db8ca8d4bfa82b8ab6265ee8a0902a13e79
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50925891"
---
# <a name="add-and-verify-admin-contacts-in-the-admin-portal"></a>Ajouter et vérifier des contacts d’administrateur dans le portail d’administration

Il existe plusieurs façons dont le service Bureau géré Microsoft communique avec les clients. Pour simplifier la communication et nous assurer que nous vérifions avec les bonnes personnes, vous devez fournir un ensemble de contacts d’administrateur. Les opérations informatiques du bureau géré Microsoft contacteront ces personnes pour obtenir de l’aide pour résoudre les problèmes de votre client.

> [!IMPORTANT]
> Vous avez peut-être déjà ajouté ces contacts dans le portail d’administration. Si c’est le cas, prenez le temps de vérifier que  la liste des contacts est exacte, car bureau géré Microsoft doit pouvoir les joindre en cas d’incident grave.

## <a name="azure-active-directory-access-for-microsoft-managed-desktop-admin-portal"></a>Accès à Azure Active Directory pour le portail d’administration du bureau géré Microsoft

Le portail d’administration du bureau géré Microsoft exige que les personnes accédant au portail ont l’un des rôles Azure Active Directory (AD) ci-après :
- Administrateur général
- Administrateur de service Intune
- Lecteur général
- Administrateur du support technique

L’administrateur général doit être celui qui inscrit votre organisation dans Bureau géré Microsoft. Les cinq rôles ont le même accès au sein du portail d’administration pour lancer et afficher les tâches. Pour plus d’informations sur l’attribution de ces rôles dans Azure AD, voir Autorisations de rôle [d’administrateur dans Azure Active Directory.](/azure/active-directory/users-groups-roles/directory-assign-admin-roles) 

## <a name="admin-contact-areas-of-focus"></a>Domaines de contact de l’administrateur

Les contacts d’administrateur doivent être la meilleure personne ou le meilleur groupe qui puisse répondre aux questions et prendre des décisions pour différents domaines de travail. **Microsoft Managed Desktop Operations contactera ces contacts d’administrateur pour toute question concernant les demandes de support déposées par le client.** Ces contacts d’administrateur recevront des notifications pour les mises à jour de demande de support et les nouveaux messages. Ces domaines sont les suivants :

Zone de mise au point | Pour des questions sur
--- | ---
Empaquetage d’application | Résolution des problèmes d’empaquetage d’application
Appareils | État de l’appareil, résolution des problèmes avec les appareils de bureau géré Microsoft
Sécurité | Résolution des problèmes de sécurité avec les appareils bureau géré Microsoft
Service d’aide à l’information | dans les cas où notre personnel de support remet des tickets d’utilisateur en dehors des zones de support Microsoft Managed Desktop 
Autre | Pour les problèmes non couverts par d’autres domaines

**Toute personne que vous choisissez pour ces contacts doit avoir les connaissances et l’autorité nécessaires pour prendre des décisions pour votre environnement Bureau géré Microsoft.** Lorsque vous intégrerez votre environnement Bureau géré Microsoft, vous êtes invité à ajouter des contacts pour votre aide et sécurité locales. 

Les contacts d’administrateur sont requis lorsque vous [envoyez une demande de support.](../service-description/support.md) Vous devez avoir un contact d’administrateur pour la zone de focus de la demande de support. 

**Pour ajouter des contacts d’administrateur**

1.  Connectez-vous au [portail d’administration bureau géré Microsoft.](https://aka.ms/mwaasportal) 

2.  Sous **Support,** sélectionnez **Contacts d’administration.** 

    ![Menu Support, Contacts d’administration dans la partie supérieure sélectionnée](../../media/admincontacts.png)

3. Sélectionnez **Ajouter**.

    ![Portail d’administration, bouton Ajouter, à gauche de l’exportation et de l’actualisation](../../media/adminadd.png)

4.  Sélectionnez **une zone de focus** et entrez les informations du contact. 

    ![liste des domaines de mise au point, tels que Autres, Applications et Sécurité](../../media/areaoffocus.png)

5. Répétez l’étape pour chaque zone de mise au point. 

## <a name="steps-to-get-started-with-microsoft-managed-desktop"></a>Étapes de mise en place du Bureau géré Microsoft

1. Ajouter et vérifier des contacts d’administrateur dans le portail d’administration (cette rubrique)
2. [Ajuster l’accès conditionnel](conditional-access.md)
3. [Affecter des licences](assign-licenses.md)
4. [Installer l’application Portail d’entreprise Intune sur les appareils](company-portal.md)
5. [Activer Enterprise State Roaming](enterprise-state-roaming.md)
6. [Configurer les appareils Bureau géré Microsoft](set-up-devices.md)
7. [Préparer vos utilisateurs à l’utilisation les appareils](get-started-devices.md)
8. [Déployer les applications sur les appareils](deploy-apps.md)