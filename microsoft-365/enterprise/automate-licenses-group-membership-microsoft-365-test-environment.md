---
title: Automatiser les licences et l’appartenance aux groupes pour votre environnement de test Microsoft 365 pour les entreprises
f1.keywords:
- NOCSH
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/09/2019
audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: M365-identity-device-management
ms.custom:
- TLG
- Ent_TLGs
description: Configurez la gestion des licences basée sur un groupe et l’appartenance à un groupe dynamique dans votre environnement de test Microsoft 365.
ms.openlocfilehash: d770e7be3b0b55855f1fee26a45d55260c3074cb
ms.sourcegitcommit: 53ff1fe6d6143b0bf011031eea9b85dc01ae4f74
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/16/2020
ms.locfileid: "48487575"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatiser les licences et l’appartenance aux groupes pour votre environnement de test Microsoft 365 pour les entreprises

*Ce guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

Les licences basées sur des groupes attribuent ou suppriment automatiquement des licences pour un compte d’utilisateur en fonction de l’appartenance à un groupe. L’appartenance à un groupe dynamique ajoute ou supprime des membres d’un groupe en fonction des propriétés du compte d’utilisateur, telles que **service** ou **pays**. Cet article vous guide à travers les démonstrations de l’ajout et de la suppression des membres du groupe dans votre environnement de test Microsoft 365 pour les entreprises.

La configuration des licences automatiques et l’appartenance au groupe dynamique dans votre environnement de test Microsoft 365 pour entreprise implique deux phases :

- [Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : configurer et tester l’appartenance au groupe dynamique et les licences automatiques](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir un plan de tous les Articles de la pile de guide de laboratoire de test Microsoft 365 pour Enterprise, accédez à [Microsoft 365 pour la pile de guide de laboratoire de test d’entreprise](../downloads/Microsoft365EnterpriseTLGStack.pdf).
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : créer votre environnement de test Microsoft 365 pour les entreprises

Si vous souhaitez tester uniquement les licences automatisées et l’appartenance aux groupes de façon légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester les licences automatisées et l’appartenance aux groupes dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Phase 2 : configurer et tester l’appartenance au groupe dynamique et les licences automatiques

Tout d’abord, créez un groupe nommé Sales et ajoutez une règle d’appartenance au groupe dynamique de sorte que les comptes d’utilisateur dont le **service** est défini sur **Sales** rejoignent automatiquement le groupe Sales.

1. Dans une instance privée de votre navigateur Internet, connectez-vous au [Centre d’administration de microsoft 365](https://admin.microsoft.com) avec le compte d’administrateur général de votre abonnement de laboratoire de test Microsoft 365 E5.
2. Dans un onglet distinct de votre navigateur, accédez au portail Azure à l’adresse [https://portal.azure.com](https://portal.azure.com) .
3. Dans le portail Azure, entrez des **groupes** dans la zone de recherche, puis sélectionnez **groupes**.
4. dans le volet **tous les groupes** , sélectionnez **nouveau groupe**.
5. Dans **type de groupe**, sélectionnez **Microsoft 365**.
6. Dans **nom du groupe**, entrez **ventes**.
7. Dans **type d’appartenance**, sélectionnez **utilisateur dynamique**.
8. Sélectionnez **utilisateurs dynamiques**.
9. Dans le volet **règles d’appartenance dynamiques** : 
   - Sélectionnez la propriété **Department (service** ).
   - Sélectionnez l’opérateur **est égal** à.
   - Dans la zone **valeur** , entrez **ventes**.
10. Sélectionnez **Enregistrer**.
11. Sélectionnez **Créer**.

Ensuite, configurez le groupe ventes de sorte que les membres reçoivent automatiquement la licence Microsoft 365 E5.

1. Sélectionnez le groupe **ventes** , puis sélectionnez **licences**.
2. Dans le volet **mettre à jour les affectations de licence** , sélectionnez **Microsoft 365 E5**, puis **Enregistrer**.
3. Dans votre navigateur, fermez l’onglet portail Azure.

Ensuite, testez l’appartenance au groupe dynamique et les licences automatiques sur le compte utilisateur 4 :

1. Dans l’onglet **Accueil Microsoft Office** de votre navigateur, sélectionnez **administrateur**.
2. À partir de l’onglet **Centre d’administration 365 de Microsoft** , sélectionnez **utilisateurs actifs**.
3. Sur la page **utilisateurs actifs** , sélectionnez le compte **utilisateur 4** .
4. Dans le volet **utilisateur 4** , sélectionnez **modifier** pour **licences de produits**.
5. Dans le volet **licences de produits** , désactivez la licence **Microsoft 365 E5** , puis sélectionnez **Enregistrer**  >  **Fermer**.
6. Dans les propriétés du compte utilisateur 4, vérifiez qu’aucune licence de produit n’a été affectée et qu’il n’y a pas d’appartenance à un groupe.
7. Pour les **informations de contact**, sélectionnez **modifier**.
8. Dans le volet **modifier les informations** de contact **, sélectionnez coordonnées**.
9. Dans la zone **service** , entrez **ventes**, puis sélectionnez **Enregistrer**  >  **Fermer**.
10. Patientez quelques minutes, puis sélectionnez régulièrement l’icône d' **actualisation** dans le coin supérieur droit du volet de comptes utilisateur 4.

Dans le temps, vous devriez voir les éléments suivants :

- Propriété d' **appartenance au groupe** mise à jour avec le groupe **ventes** .
- Propriété de **licences de produit** mise à jour avec la licence **Microsoft 365 E5** .

Consultez les articles suivants pour déployer l’appartenance à un groupe dynamique et les licences automatiques en production :

- [Gestion des licences par groupe dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Groupes dynamiques dans Azure Active Directory](https://docs.microsoft.com/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Feuille de route d’identité](identity-roadmap-microsoft-365.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 pour entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
