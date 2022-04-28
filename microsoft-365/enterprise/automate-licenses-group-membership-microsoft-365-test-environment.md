---
title: Automatiser l’appartenance aux licences et aux groupes pour votre Microsoft 365 pour l’environnement de test d’entreprise
f1.keywords:
- NOCSH
ms.author: kvice
author: kelleyvice-msft
manager: scotv
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
ms.localizationpriority: medium
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Configurez les licences basées sur les groupes et l’appartenance dynamique aux groupes dans votre Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: 1d471076ac07acb023cdf785233ea2222690b596
ms.sourcegitcommit: e50c13d9be3ed05ecb156d497551acf2c9da9015
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/27/2022
ms.locfileid: "65097533"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatiser l’appartenance aux licences et aux groupes pour votre Microsoft 365 pour l’environnement de test d’entreprise

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Les licences basées sur un groupe attribuent ou suppriment automatiquement des licences pour un compte d’utilisateur en fonction de l’appartenance au groupe. L’appartenance dynamique à un groupe ajoute ou supprime des membres à un groupe en fonction des propriétés du compte d’utilisateur, telles que **Department** ou **Country**. Cet article vous explique comment ajouter et supprimer des membres de groupe dans votre Microsoft 365 pour l’environnement de test d’entreprise.

La configuration des licences automatiques et de l’appartenance à un groupe dynamique dans votre Microsoft 365 pour l’environnement de test d’entreprise implique deux phases :

- [Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Configurer et tester l’appartenance à un groupe dynamique et la gestion automatique des licences](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Guides de laboratoire de test pour le cloud Microsoft.](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles du Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise, accédez à [Microsoft 365 pour la pile des guides de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre Microsoft 365 pour l’environnement de test d’entreprise

Si vous souhaitez tester uniquement l’appartenance automatisée aux licences et aux groupes d’une manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester la licence automatisée et l’appartenance à un groupe dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et de l’appartenance aux groupes ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt services de domaine Active Directory (AD DS). Il est fourni ici en tant qu’option afin que vous puissiez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Phase 2 : Configurer et tester l’appartenance à un groupe dynamique et la gestion automatique des licences

Tout d’abord, créez un groupe nommé Sales et ajoutez une règle d’appartenance au groupe dynamique afin que les comptes d’utilisateur avec le **service** défini sur **Ventes** rejoignent automatiquement le groupe Ventes.

1. Dans une instance privée de votre navigateur Internet, connectez-vous au [Centre d'administration Microsoft 365](https://admin.microsoft.com) avec le compte d’administrateur général de votre abonnement de laboratoire de test Microsoft 365 E5.
2. Sous un onglet distinct de votre navigateur, accédez à la Portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com).
3. Dans le Portail Azure, entrez **des groupes** dans la zone de recherche, puis sélectionnez **Groupes**.
4. Dans le volet **Tous les groupes** , sélectionnez **Nouveau groupe**.
5. Dans **Type de groupe**, sélectionnez **Microsoft 365**.
6. Dans **le nom du groupe**, entrez **Ventes**.
7. Dans **Type d’appartenance**, sélectionnez **Utilisateur dynamique**.
8. Sélectionnez **les membres de l’utilisateur dynamique**.
9. Dans le volet **Règles d’appartenance dynamique** : 
   - Sélectionnez la propriété **department** .
   - Sélectionnez l’opérateur **Equals** .
   - Dans la zone **Valeur** , entrez **Sales**.
10. Sélectionnez **Enregistrer**.
11. Sélectionnez **Créer**.

Ensuite, configurez le groupe Ventes afin que les membres reçoivent automatiquement la licence Microsoft 365 E5.

1. Sélectionnez le groupe **Ventes** , puis sélectionnez **Licences**.
2. Dans le volet **Mettre à jour les attributions de licences**, sélectionnez **Microsoft 365 E5**, puis **sélectionnez Enregistrer**.
3. Dans votre navigateur, fermez l’onglet Portail Azure.

Ensuite, testez l’appartenance au groupe dynamique et les licences automatiques sur le compte Utilisateur 4 :

1. Sous l’onglet **Microsoft Office Accueil** de votre navigateur, sélectionnez **Administrateur**.
2. Sous l’onglet **Centre d'administration Microsoft 365**, sélectionnez **Utilisateurs actifs**.
3. Dans la page **Utilisateurs actifs** , sélectionnez le compte **Utilisateur 4** .
4. Dans le volet **Utilisateur 4** , **sélectionnez Modifier** pour **les licences de produit**.
5. Dans le volet **Licences du produit**, désactivez la licence **Microsoft 365 E5**, puis sélectionnez **SaveClose** > .
6. Dans les propriétés du compte Utilisateur 4, vérifiez qu’aucune licence de produit n’a été attribuée et qu’il n’existe aucune appartenance à un groupe.
7. Pour **les informations de contact**, **sélectionnez Modifier**.
8. Dans le volet **Modifier les informations de contact** , sélectionnez **Informations de contact**.
9. Dans la zone **Département**, entrez **Ventes**, puis sélectionnez **SaveClose** > .
10. Patientez quelques minutes, puis sélectionnez régulièrement l’icône **Actualiser** dans le coin supérieur droit du volet compte Utilisateur 4.

Dans le temps, vous devriez voir les éléments :

- **Propriété d’appartenances aux groupes** mise à jour avec le groupe **Sales** .
- **Propriété des licences de produit** mise à jour avec la licence **Microsoft 365 E5**.

Consultez les articles suivants pour déployer l’appartenance à un groupe dynamique et la gestion automatique des licences en production :

- [Licences basées sur des groupes dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Groupes dynamiques dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Déployer une identité](deploy-identity-solution-overview.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)