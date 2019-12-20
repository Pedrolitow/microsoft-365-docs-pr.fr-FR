---
title: Automatiser les licences et l’appartenance aux groupes pour votre environnement de test Microsoft 365 Enterprise
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
description: Configurez la gestion des licences basée sur un groupe et l’appartenance à un groupe dynamique dans votre environnement de test Microsoft 365 Enterprise.
ms.openlocfilehash: facff7eb556299c0312fa7488a35a96151bb1882
ms.sourcegitcommit: 0ad0092d9c5cb2d69fc70c990a9b7cc03140611b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/19/2019
ms.locfileid: "40802119"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-enterprise-test-environment"></a>Automatiser les licences et l’appartenance aux groupes pour votre environnement de test Microsoft 365 Enterprise

*Ce Guide de Laboratoire Test peut uniquement être utilisé pour les environnements de test Microsoft 365 Entreprise*.

Les licences basées sur des groupes attribuent ou suppriment automatiquement des licences pour un compte d’utilisateur en fonction de l’appartenance à un groupe. L’appartenance à un groupe dynamique ajoute ou supprime des membres d’un groupe en fonction des propriétés du compte d’utilisateur, telles que service ou pays. Cet article décrit les deux dans votre environnement de test Microsoft 365 Enterprise.

Il existe deux phases de configuration de la gestion des licences automatiques et de l’appartenance à un groupe dynamique dans votre environnement de test Microsoft 365 entreprise :

1. Créer l’environnement de test Microsoft 365 Entreprise.
2. Configurez et testez l’appartenance au groupe dynamique et les licences automatiques.

![Guides de laboratoire de test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](media/m365-enterprise-test-lab-guides/Microsoft365EnterpriseTLGStack.pdf) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Créer l’environnement de test Microsoft 365 Entreprise.

Si vous souhaitez simplement tester les licences automatisées et l’appartenance au groupe de façon légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester les licences automatisées et l’appartenance aux groupes dans une entreprise simulée, suivez les instructions de l' [authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Le test des licences automatisées et l’appartenance aux groupes ne nécessitent pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt des services de domaine Active Directory (AD DS). Elle est fournie ici en tant qu’option pour vous permettre de tester les licences automatiques et les appartenances aux groupes et de les tester dans un environnement qui représente une organisation typique. 
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Phase 2 : configurer et tester l’appartenance au groupe dynamique et les licences automatiques

Tout d’abord, vous créez un nouveau groupe de ventes et ajoutez une règle d’appartenance au groupe dynamique de sorte que les comptes d’utilisateur dont le service est défini sur ventes soient automatiquement ajoutés au groupe ventes.

1. À l’aide d’une instance privée de votre navigateur Internet, connectez-vous au portail [https://portal.office.com](https://portal.office.com) Office 365 à l’aide du compte d’administrateur général de votre abonnement de laboratoire de test Microsoft 365 E5.
2. Dans un onglet distinct de votre navigateur, accédez au portail Azure à l' [https://portal.azure.com](https://portal.azure.com)adresse.
3. Dans le portail Azure, tapez **groupes** dans la zone de recherche, puis cliquez sur **groupes**.
4. dans le volet **tous les groupes** , cliquez sur **nouveau groupe**.
5. Dans **type de groupe**, sélectionnez **Office 365**.
6. Dans **nom du groupe**, tapez **ventes**.
7. Dans **type d’appartenance**, sélectionnez **utilisateur dynamique**.
8. Cliquez sur **utilisateurs dynamiques**.
9. Dans le volet **règles d’appartenance dynamiques** : 
   - Sélectionnez la propriété **Department (service** ).
   - Sélectionnez l’opérateur **est égal** à.
   - Tapez **ventes** dans **valeur**.
10. Cliquez sur **Enregistrer**.
11. Cliquez sur **Créer**.

Ensuite, configurez le groupe ventes de sorte que les membres reçoivent automatiquement la licence Microsoft 365 E5.

1. Cliquez sur le groupe **ventes** , puis sur **licences**.
2. Dans le volet **mettre à jour les attributions de licence** , sélectionnez **Microsoft 365 E5**, puis cliquez sur **Enregistrer**.
3. Fermez l’onglet du portail Azure dans votre navigateur.

Ensuite, testez l’appartenance au groupe dynamique et les licences automatiques sur le compte utilisateur 4. 

1. Dans l’onglet **Accueil Microsoft Office** de votre navigateur, cliquez sur **administrateur**.
2. À partir de l’onglet **Centre d’administration 365 de Microsoft** , cliquez sur **utilisateurs actifs**.
3. Sur la page **utilisateurs actifs** , cliquez sur le compte **utilisateur 4** .
4. Dans le volet **utilisateur 4** , cliquez sur **modifier** pour **licences de produits**.
5. Dans le volet **licences de produits** , désactivez la licence **Microsoft 365 E5** , puis cliquez sur **Enregistrer > fermer**.
6. Dans les propriétés du compte utilisateur 4, vérifiez qu’aucune licence de produit n’a été affectée et qu’il n’y a pas d’appartenance à un groupe.
7. Cliquez sur **modifier** pour obtenir des **informations de contact**.
8. Dans le volet **modifier les informations de contact** , cliquez sur informations sur le **contact**.
9. Dans le champ **service** , tapez **ventes**, puis cliquez sur **Enregistrer > fermer**.
10. Patientez quelques minutes, puis cliquez régulièrement sur l’icône Actualiser dans le coin supérieur droit du volet compte utilisateur 4. 

À temps, vous devriez voir les éléments suivants :

- Propriété d' **appartenance au groupe** mise à jour avec le groupe **ventes** .
- Propriété de **licences de produit** mise à jour avec la licence **Microsoft 365 E5** .

Consultez ces étapes dans la phase d’identité pour obtenir des informations et des liens sur le déploiement de l’appartenance au groupe dynamique et des licences automatiques en production :

- [Configurez la gestion des licences automatique](identity-use-group-management.md#identity-group-license)
- [Configurer l’appartenance à un groupe dynamique](identity-use-group-management.md#identity-dyn-groups)

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Étape 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 Entreprise](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
