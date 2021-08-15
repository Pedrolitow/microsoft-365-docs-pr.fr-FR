---
title: Automatiser la gestion des licences et l’appartenance à un Microsoft 365 pour l’environnement de test d’entreprise
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
description: Configurez la gestion des licences basée sur les groupes et l’appartenance à un groupe dynamique dans Microsoft 365 pour l’environnement de test d’entreprise.
ms.openlocfilehash: 8835498f0b56eeafbc86f49a0be2df840359afbfdeb5518ca6fe521b64c8c652
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53859082"
---
# <a name="automate-licensing-and-group-membership-for-your-microsoft-365-for-enterprise-test-environment"></a>Automatiser la gestion des licences et l’appartenance à un Microsoft 365 pour l’environnement de test d’entreprise

*Ce Guide de laboratoire de test ne peut être utilisé que pour Microsoft 365 pour les environnements de test d’entreprise.*

La gestion des licences basée sur les groupes attribue ou supprime automatiquement les licences d’un compte d’utilisateur en fonction de l’appartenance au groupe. L’appartenance à un groupe dynamique ajoute ou supprime des membres à un groupe en fonction des propriétés du compte d’utilisateur, telles que **Département** ou **Pays.** Cet article vous décrit les démonstrations de l’ajout et de la suppression de membres de groupe dans votre Microsoft 365 environnement de test d’entreprise.

La configuration de la gestion des licences automatiques et de l’appartenance à un groupe dynamique dans votre Microsoft 365 environnement de test d’entreprise implique deux phases :

- [Phase 1 : Créer votre environnement de test Microsoft 365 entreprise](#phase-1-build-out-your-microsoft-365-for-enterprise-test-environment)
- [Phase 2 : Configurer et tester l’appartenance à un groupe dynamique et la gestion automatique des licences](#phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing)

![Guides de laboratoire de test pour Microsoft Cloud](../media/m365-enterprise-test-lab-guides/cloud-tlg-icon.png) 
    
> [!TIP]
> Pour obtenir une carte visuelle de tous les articles de la pile Microsoft 365 guide de laboratoire de test pour entreprise, Microsoft 365 pour la pile de guides de laboratoire de [test d’entreprise.](../downloads/Microsoft365EnterpriseTLGStack.pdf)
  
## <a name="phase-1-build-out-your-microsoft-365-for-enterprise-test-environment"></a>Phase 1 : Créer votre environnement de test Microsoft 365 entreprise

Si vous souhaitez uniquement tester les licences automatisées et l’appartenance à un groupe de manière légère avec la configuration minimale requise, suivez les instructions de la [configuration de base légère.](lightweight-base-configuration-microsoft-365-enterprise.md)
  
Si vous souhaitez tester la gestion automatisée des licences et l’appartenance à un groupe dans une entreprise simulée, suivez les instructions de [l’authentification directe.](pass-through-auth-m365-ent-test-environment.md)
  
> [!NOTE]
> Le test de la gestion automatisée des licences et de l’appartenance à un groupe ne nécessite pas l’environnement de test d’entreprise simulé, qui inclut un intranet simulé connecté à Internet et la synchronisation d’annuaires pour une forêt AD DS (Active Directory Domain Services). Il est fourni ici en tant qu’option afin que vous pouvez tester la gestion automatisée des licences et l’appartenance à un groupe et l’expérimenter dans un environnement qui représente une organisation classique.
  
## <a name="phase-2-configure-and-test-dynamic-group-membership-and-automatic-licensing"></a>Phase 2 : Configurer et tester l’appartenance à un groupe dynamique et la gestion automatique des licences

Tout d’abord, créez un groupe nommé Ventes, puis ajoutez  une  règle d’appartenance au groupe dynamique afin que les comptes d’utilisateurs dont le service est le service des ventes rejoignent automatiquement le groupe Ventes.

1. Dans une instance privée de votre navigateur Internet, connectez-vous au [Centre d’administration Microsoft 365](https://admin.microsoft.com) avec le compte d’administrateur général de votre abonnement Microsoft 365 E5 de laboratoire de test.
2. Sous un onglet distinct de votre navigateur, allez sur le portail Azure à [https://portal.azure.com](https://portal.azure.com) l':.
3. Dans le portail Azure, entrez **des groupes** dans la zone de recherche, puis sélectionnez **Groupes.**
4. dans le **volet Tous les groupes,** sélectionnez **Nouveau groupe.**
5. Dans **le type de groupe,** **sélectionnez Microsoft 365**.
6. Dans **le nom du groupe,** entrez **Ventes**.
7. Dans **le type d’appartenance,** **sélectionnez Utilisateur dynamique.**
8. Sélectionnez **Membres utilisateur dynamiques.**
9. Dans le **volet Règles d’appartenance** dynamique : 
   - Sélectionnez la **propriété de** service.
   - Sélectionnez **l’opérateur Égal à.**
   - Dans la **zone Valeur,** entrez **Ventes**.
10. Sélectionnez **Enregistrer**.
11. Sélectionnez **Créer**.

Ensuite, configurez le groupe Ventes afin que les membres se voit attribuer automatiquement la Microsoft 365 E5 licence.

1. Sélectionnez **le groupe** Ventes, puis **sélectionnez Licences.**
2. Dans le **volet Mettre à jour les attributions** de licence, **sélectionnez Microsoft 365 E5,** puis sélectionnez **Enregistrer.**
3. Dans votre navigateur, fermez l’onglet du portail Azure.

Ensuite, testez l’appartenance au groupe dynamique et la gestion automatique des licences sur le compte Utilisateur 4 :

1. Dans **l’Microsoft Office Accueil** de votre navigateur, sélectionnez **Administrateur.**
2. Dans **l’Centre d’administration Microsoft 365,** sélectionnez **Utilisateurs actifs.**
3. Dans la page **Utilisateurs** actifs, sélectionnez **le compte Utilisateur 4.**
4. Dans le **volet Utilisateur 4,** **sélectionnez Modifier pour** les **licences de produit.**
5. Dans le **volet Licences de** produits, désactivez la **licence Microsoft 365 E5,** puis **sélectionnez Enregistrer**  >  **fermer.**
6. Dans les propriétés du compte Utilisateur 4, vérifiez qu’aucune licence de produit n’a été attribuée et qu’il n’y a pas d’appartenance à un groupe.
7. Pour **plus d’informations sur** le contact, **sélectionnez Modifier.**
8. Dans le **volet Modifier les informations de contact,** sélectionnez **Coordonnées.**
9. Dans la **zone Service,** entrez **Ventes,** puis **sélectionnez Enregistrer**  >  **la fermeture.**
10. Patientez quelques minutes, puis sélectionnez périodiquement l’icône Actualiser dans le coin supérieur droit du volet du compte Utilisateur 4. 

Dans le temps, vous devriez voir les :

- **Propriété d’appartenance au** groupe mise à jour avec **le groupe** Ventes.
- **Propriété des licences de** produit mise à jour **avec la Microsoft 365 E5** licence.

Consultez les articles suivants pour déployer l’appartenance à un groupe dynamique et la gestion automatique des licences en production :

- [Gestion des licences basée sur les groupes dans Azure Active Directory](/azure/active-directory/fundamentals/active-directory-licensing-whatis-azure-portal)
- [Groupes dynamiques dans Azure Active Directory](/azure/active-directory/users-groups-roles/groups-create-rule)

## <a name="next-step"></a>Étape suivante

Explorez les autres fonctionnalités liées aux [identités](m365-enterprise-test-lab-guides.md#identity) disponibles dans votre environnement de test.

## <a name="see-also"></a>Voir aussi

[Feuille de route des identités](identity-roadmap-microsoft-365.md)

[Microsoft 365 pour les entreprises Guides de laboratoire d'essai](m365-enterprise-test-lab-guides.md)

[Vue d’ensemble de Microsoft 365 pour entreprise](microsoft-365-overview.md)

[Documentation Microsoft 365 Entreprise](/microsoft-365-enterprise/)