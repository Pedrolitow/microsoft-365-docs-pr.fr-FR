---
title: Transition d’un abonnement Fournisseur de solutions Cloud Microsoft365Business
description: Découvrez comment faire passer un abonnement CSP Microsoft 365 Entreprise de la prévisualisation à la disponibilité générale.
author: jasongroce
f1.keywords:
- NOCSH
ms.custom:
- seo-marvel-mar
- AdminSurgePortfolio
ms.author: jasongroce
ms.topic: article
manager: jasonh
ms.prod: microsoft-365-business
localization_priority: Normal
audience: microsoft-business
keywords: Microsoft 365 Business, Microsoft 365, SMB, transition d’un abonnement Fournisseur de solutions Cloud
ms.date: 11/01/2017
ms.openlocfilehash: c35cb3b78c4fe2cebc8308b34ceef3decd346b3db298ce5fb56abc8cf205e69d
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53867126"
---
# <a name="transition-a-microsoft-365-business-csp-subscription"></a>Transition d’un abonnement Fournisseur de solutions Cloud Microsoft365Business

Si vous avez un abonnement Fournisseur de solutions Cloud Microsoft365Business version d’évaluation , suivez ce guide pour découvrir comment vous pouvez passer votre abonnement existant à la version d’évaluation vers la version mise à disponibilité générale Microsoft 365Business.

**Comment faire passer un abonnement à la version d’évaluation vers la version mise à disponibilité générale**

1. Connectez-vous à l’<a href="https://partnercenter.microsoft.com" target="_blank">Espace partenaires</a>.
2. Dans le tableau de bord, sélectionnez **Clients**, puis recherchez et sélectionnez le nom de la société.

    Les abonnements pour la société seront affichés.

    ![Abonnements du client dans l’Espace partenaires](../../media/pc_customer_subscriptions_1.png)
    
3. Dans la page **Abonnements** de l’entreprise, sélectionnez **Ajouter un abonnement.**
4. Dans la page **Nouvel abonnement,** **sélectionnez** Petite entreprise, puis Microsoft 365 **Entreprise dans** la liste.
5. Ajoutez le nombre de licences, puis sélectionnez **Suivant: révision** pour passer en revue l’abonnement, puis sélectionnez **Soumettre**.

    ![Passez en revue le nouvel abonnement à Microsoft 365Business](../../media/pc_customer_reviewnewsubscription.png)

    Les **abonnements basés sur les licences** afficheront **Microsoft 365Business Preview** et **Microsoft 365Business**. Vous allez ensuite suspendre l’abonnement Preview.

6. Sélectionnez **Microsoft 365 Business Preview**.
7. Dans la page **Microsoft 365 aperçu commercial,** sélectionnez **Suspendu** pour suspendre l’abonnement d’aperçu.

    ![Suspendre l’abonnement à la version d’évaluation Microsoft 365Business](../../media/pc_customer_m365bpreview_suspend.png)

8. Sélectionnez **Soumettre** pour confirmer.

    Dans la page **Abonnements,** confirmez que **l’état Microsoft 365 l’aperçu** professionnel affiche **Suspendu.**

    ![Vérifier que l’état de l’abonnement à la version d’évaluation est suspendu](../../media/pc_customer_m365bpreview_suspend_confirm.png)

9. Si vous le souhaitez, vous pouvez également valider le contrat de licence. Pour cela, procédez comme suit:
    1. Sélectionnez **Utilisateurs et licences** dans la page **Abonnements** de la société.
    2. Dans la page **Utilisateurs et licences,** sélectionnez un utilisateur.
    3. Dans la page de l’utilisateur, consultez la section Attribuer des **licences** et vérifiez qu’elle affiche **Microsoft 365 Business**.

        ![Vérifier que la licence Microsoft 365Business est attribuée à l’utilisateur](../../media/pc_customer_userslicenses_m365b_validate.png)

## <a name="impact-to-customers-and-users-during-and-after-transition"></a>Impact sur les clients et les utilisateurs pendant et après la transition

Il n’y a aucun impact sur les clients et les utilisateurs pendant la transition et après la transition.

## <a name="impact-to-customers-who-dont-transition"></a>Impact sur les clients qui n’effectuent pas la transition

Le tableau suivant récapitule l’impact sur les clients qui ne font pas la transition d’un abonnement à la version d’évaluation Microsoft 365Business Preview vers un abonnement Microsoft 365Business.

|       | T-0 à T+30     | T+30 à T+60 | T+60 à T+120 | Au-delà de T+120  |
|-------|-----------------|--------------|---------------|---------------|
| **État** | En période de grâce | Expiré      | Désactivé      | Supprimé |
| **Impact sur les services**                                                        |
| **Centre d’administration Microsoft 365** | Aucun impact sur les fonctionnalités | Aucun impact sur les fonctionnalités | Possibilité d'ajouter/de supprimer des utilisateurs, d’acheter des abonnements.</br> Ne peut pas attribuer/révoquer des licences. | L’abonnement du client et toutes les données sont supprimés. L’administrateur peut gérer d’autres abonnements payants. |
| **Applications Office**                         | Aucun impact sur les utilisateurs finaux | Aucun impact sur les utilisateurs finaux | Office passe en mode de fonctionnalités réduites.</br> Les utilisateurs peuvent afficher uniquement les fichiers. | Office passe en mode de fonctionnalités réduites.</br> Les utilisateurs peuvent afficher uniquement les fichiers. |
| **Services cloud (SharePoint Online, Exchange Online, Skype, Teams, etc.)** | Aucun impact sur les utilisateurs finaux | Aucun impact sur les utilisateurs finaux | Les utilisateurs finaux et les administrateurs n’ont aucun accès aux données dans le cloud. | L’abonnement du client et toutes les données sont supprimés. |
| **Composants EM+S** | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | La fonctionnalité n’est plus appliquée.</br> Voir [Impacts sur les appareils mobiles à l’expiration de l’abonnement](#mobile-device-impacts-upon-subscription-expiration) et [Impact sur les PC Windows10à l’expiration de l’abonnement](#windows-10-pc-impacts-upon-subscription-expiration) pour plus d’informations. | La fonctionnalité n’est plus appliquée.</br> Voir [Impacts sur les appareils mobiles à l’expiration de l’abonnement](#mobile-device-impacts-upon-subscription-expiration) et [Impact sur les PC Windows10 à l’expiration de l’abonnement](#windows-10-pc-impacts-upon-subscription-expiration) pour plus d’informations. |
| **Windows 10 Business** | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | La fonctionnalité n’est plus appliquée.</br> Voir [Impacts sur les appareils mobiles à l’expiration de l’abonnement](#mobile-device-impacts-upon-subscription-expiration) et [Impact sur les PC Windows10à l’expiration de l’abonnement](#windows-10-pc-impacts-upon-subscription-expiration) pour plus d’informations. | La fonctionnalité n’est plus appliquée.</br> Voir [Impacts sur les appareils mobiles à l’expiration de l’abonnement](#mobile-device-impacts-upon-subscription-expiration) et [Impact sur les PC Windows10à l’expiration de l’abonnement](#windows-10-pc-impacts-upon-subscription-expiration) pour plus d’informations. |
| **Connexion Azure AD sur un PC Windows10** | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | Aucun impact sur les administrateurs</br> Aucun impact sur les utilisateurs finaux | Une fois le client supprimé, un utilisateur peut se connecter uniquement avec les informations d’identification locales. Réimager l’appareil s’il n’y a aucune information d’identification locale. |

## <a name="mobile-device-impacts-upon-subscription-expiration"></a>Impacts sur les appareils mobiles à l’expiration de l’abonnement

Le tableau suivant récapitule l’impact sur les stratégies de gestion des applications sur les appareils mobiles.

|                            | Expérience Licence complète                      | T+60jours après l’expiration          |
|----------------------------|------------------------------------------------|------------------------------------|
| **Supprimer les fichiers de travail à partir d’un appareil inactif** | Les fichiers de travail sont supprimés après le nombre de jours sélectionnés | Les fichiers de travail restent sur les appareils personnels de l’utilisateur |
| **Forcer les utilisateurs à enregistrer tous les fichiers de travail sur OneDrive Entreprise** | Les fichiers de travail peuvent uniquement être enregistrés sur OneDrive Entreprise | Les fichiers de travail peuvent être enregistrés en tout lieu |
| **Chiffrer les fichiers de travail** | Les fichiers de travail sont chiffrés | Les fichiers de travail ne sont plus chiffrés</br> Les stratégies de sécurité sont supprimées et les données Office sur les applications sont supprimées. |
| **Exiger le code confidentiel ou l’empreinte digitale pour accéder aux applications Office** | Accès restreint aux applications | Aucune restriction d’accès au niveau des applications |
| **Réinitialiser le code confidentiel en cas d’échec de connexion** | Accès restreint aux applications | Aucune restriction d’accès au niveau des applications |
| **Obliger les utilisateurs à se connecter à nouveau après que les applications Office sont restées inactives** | Connexion requise | Aucune sign-in requise |
| **Refuser l’accès aux fichiers de travail sur les appareils débridés ou rootés** | Les fichiers de travail ne sont pas accessibles sur les appareils jailbreakés/racines | Les fichiers de travail sont accessibles sur les appareils débridés/rootés |
| **Autoriser les utilisateurs à copier le contenu des applications Office vers les applications personnelles** | Copier/coller limité aux applications disponibles dans le cadre de l’abonnement Microsoft 365 abonnement | Copier/coller disponible pour toutes les applications |

## <a name="windows-10-pc-impacts-upon-subscription-expiration"></a>Impacts sur les PC Windows10 à l’expiration de l’abonnement

Le tableau suivant récapitule l’impact sur les stratégies de configuration d’appareils Windows10.

|                            | Expérience Licence complète                      | T+60jours après l’expiration          |
|----------------------------|------------------------------------------------|------------------------------------|
| **Aider à protéger les PC contre les menaces à l’aide de Windows Defender** | Activer/désactiver est hors du contrôle de l’utilisateur | L’utilisateur peut activer/désactiver Windows Defender sur le PC Windows 10 pc |
| **Protéger les PC contre les menaces basées sur le web dans MicrosoftEdge** | Protection du PC dans MicrosoftEdge | L’utilisateur peut activer/désactiver la protection pc dans Microsoft Edge |
| **Désactiver l’écran de l’appareil en cas d’inactivité** | L’administrateur définit la stratégie d’intervalle de délai d’expiration de l’écran | Le délai d’expiration de l’écran peut être configuré par l’utilisateur final |
| **Autoriser les utilisateurs à télécharger des applications à partir du MicrosoftStore** | L’administrateur définit si un utilisateur peut télécharger des applications à partir du MicrosoftStore | Les utilisateurs peuvent télécharger des applications du MicrosoftStore à tout moment |
| **Permettre aux utilisateurs d’accéder à Cortana** | L’administrateur définit la stratégie de l’accès utilisateur à Cortana | Les appareils de l’utilisateur peuvent activer/désactiver Cortana |
| **Permettre aux utilisateurs de recevoir des conseils et des publicités de Microsoft** | L’administrateur définit la stratégie utilisateur pour recevoir des conseils et des publicités de Microsoft | L’utilisateur peut activer/désactiver les conseils et les publicités de Microsoft |
| **Autoriser les utilisateurs à copier le contenu des applications Office vers les applications personnelles** | L’administrateur définit une stratégie pour maintenir Windows 10 à jour des appareils | Les utilisateurs peuvent décider quand mettre à jour Windows |
