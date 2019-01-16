---
title: Automatiser l’appartenance de groupe et de licence pour votre environnement de test Microsoft 365 pour entreprises
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 08/21/2018
ms.audience: ITPro
ms.topic: article
ms.service: o365-solutions
localization_priority: Normal
ms.collection: Ent_O365
ms.custom:
- TLG
- Ent_TLGs
description: Configurer basée sur le groupe gestion des licences et l’appartenance au groupe dynamique dans votre environnement de test Microsoft 365 pour entreprises.
ms.openlocfilehash: 45a78af202f2d9ab029683aae4d95ed9a3370b08
ms.sourcegitcommit: e491c4713115610cbe13d2fbd0d65e1a41c34d62
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 01/16/2019
ms.locfileid: "26867227"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-enterprise-test-environment"></a>Automatiser l’appartenance de groupe et de licence pour votre environnement de test Microsoft 365 pour entreprises

Basée sur le groupe gestion des licences automatiquement assigne ou supprime des licences pour un compte d’utilisateur en fonction de l’appartenance au groupe. L’appartenance au groupe dynamique ajoute ou supprime des membres à un groupe en fonction de propriétés de compte d’utilisateur, telles que le service ou un pays. Cet article vous guide tout au long une démonstration des deux dans votre environnement de test Microsoft 365 pour entreprises.

Il existe deux phases à définir l’appartenance à un groupe de licences automatique et dynamique dans votre environnement de test Microsoft 365 pour entreprises :

1. Créer l’environnement de test Microsoft 365 pour entreprises.
2. Configurer et tester l’appartenance au groupe dynamique et la gestion des licences automatique.

![Guides de Laboratoire de Test pour Microsoft Cloud](media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Cliquez [ici](https://aka.ms/m365etlgstack) pour afficher le plan de tous les articles de l’ensemble de guides de laboratoire de test de Microsoft 365 Entreprise.
  
## <a name="phase-1-build-out-your-microsoft-365-enterprise-test-environment"></a>Phase 1 : Création de votre environnement de test Microsoft 365 pour entreprises

Si vous souhaitez uniquement tester les licences automatisé et l’appartenance au groupe de manière léger avec la configuration minimale requise, suivez les instructions de [configuration de base léger](lightweight-base-configuration-microsoft-365-enterprise.md).
  
Si vous souhaitez tester les licences automatisé et l’appartenance au groupe dans une entreprise simulée, suivez les instructions de [l’authentification directe](pass-through-auth-m365-ent-test-environment.md).
  
> [!NOTE]
> Test automatisé de gestion des licences et l’appartenance au groupe ne nécessite pas de l’environnement de test simulé entreprise, qui comprend un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt Windows Server Active Directory. Il est fourni ici en tant qu’option afin que vous puissiez licences automatisé et l’appartenance au groupe de test et tester dans un environnement qui représente une organisation classique. 
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Phase 2 : Configurer et tester l’appartenance au groupe dynamique et la gestion des licences automatique

Tout d’abord, vous créez un nouveau groupe de ventes et ajoutez une règle d’appartenance au groupe dynamique afin que les comptes d’utilisateurs avec le service des ventes la valeur sont automatiquement ajoutés au groupe de ventes.

1. À l’aide d’une instance privée de votre navigateur Internet, connectez-vous au portail Office à [https://office.com](https://office.com) avec le compte d’administrateur global de votre abonnement d’évaluation Office 365 E5.
2. Sur un onglet séparé de votre navigateur, accédez au portail Azure à [https://portal.azure.com](https://portal.azure.com).
3. Dans le portail Azure, cliquez sur **Azure Active Directory > Utilisateurs et groupes > Tous les groupes**.
4. Sur le serveur lame **tous les groupes** , cliquez sur **Nouveau groupe**.
5. Dans **type de groupe**, sélectionnez **Office 365**.
6. Dans **nom du groupe**, tapez **ventes**.
7. Dans **type d’appartenance**, sélectionnez **utilisateur dynamique** .
8. Cliquez sur **Ajouter une requête dynamique**.
9. Dans **Ajouter des utilisateurs où**, sélectionnez **Service**.
10. Dans le champ suivant, sélectionnez **Est égal à**.
11. Dans le champ suivant, tapez **ventes**.
12. Cliquez sur **Ajouter une requête**, puis cliquez sur **Créer**.
13. Fermez les cartes de **groupe** et les **groupes de groupes** .

Ensuite, vous configurez le groupe de ventes afin que les membres sont affectés automatiquement Office 365 E5 et mobilité d’entreprise + licences E5 de la sécurité.

1. Dans la **vue d’ensemble** lame pour Azure Active Directory, cliquez sur **licences > tous les produits**.
2. Dans la liste, sélectionnez **Enterprise Mobility + Security E5** et **Office 365 Entreprise E5**, puis cliquez sur **Affecter**.
3. Sur le serveur lame **attribuer des licences** , cliquez sur **utilisateurs et groupes**.
4. Dans la liste des groupes, sélectionnez le groupe de **ventes** .
5. Cliquez sur **Sélectionner**, puis sur **Affecter**.
6. Fermez l’onglet du portail Azure dans votre navigateur.

Ensuite, vous testez l’appartenance au groupe dynamique et la gestion des licences automatique sur le compte d’utilisateur 4. 

1. Sous l’onglet **Accueil de Microsoft Office** dans votre navigateur, cliquez sur **Admin**.
2. Sous l’onglet **Centre d’administration d’Office** , cliquez sur **utilisateurs actifs**.
3. Dans la page **utilisateurs actifs** , cliquez sur le compte **d’utilisateur 4** .
4. Dans le volet **4 de l’utilisateur** , cliquez sur **Modifier** pour les **licences de produit**.
5. Dans le volet de **licences de produits** , activer la **mobilité d’entreprise + sécurité E5** et licences **Office 365 entreprise E5** désactivé, puis cliquez sur **Enregistrer > Fermer**.
6. Dans les propriétés du compte d’utilisateur 4, vérifiez qu’aucune licence de produit n’ont été attribués et qu’il n’existe aucun appartenances aux groupes.
7. Pour plus **d’informations de Contact**, cliquez sur **Modifier** .
8. Dans le volet **Modifier le Contact** , cliquez sur **informations de Contact**.
9. Dans le champ **département** , tapez **ventes**, puis cliquez sur **Enregistrer > Fermer**.
10. Patientez quelques minutes, puis cliquez périodiquement sur l’icône Actualiser dans l’angle supérieur droit du volet de compte d’utilisateur 4. 

Dans le temps, vous devez voir les :

- Propriété **appartenances de groupe** mis à jour avec le groupe de **ventes** .
- Propriété **licences des produits** mis à jour avec les licences de **mobilité d’entreprise + sécurité E5** et **Office 365 entreprise E5** .

Dans la phase d’identité pour des informations et des liens pour déployer l’appartenance au groupe dynamique et la gestion des licences automatique en production, consultez la rubrique comme suit :

- [Configurez la gestion des licences automatique](identity-group-based-licensing.md)
- [Configurez l’appartenance à un groupe dynamique](identity-automatic-group-membership.md)

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Phase 2 : Identité](identity-infrastructure.md)

[Guides de laboratoire de test Microsoft 365 Entreprise](m365-enterprise-test-lab-guides.md)

[Déploiement de Microsoft 365 pour entreprises](deploy-microsoft-365-enterprise.md)

[Documentation Microsoft 365 Entreprise](https://docs.microsoft.com/microsoft-365-enterprise/)
