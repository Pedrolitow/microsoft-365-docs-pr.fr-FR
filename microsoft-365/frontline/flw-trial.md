---
title: Gérer la version d’évaluation en première ligne dans Teams
author: daisyfell
ms.author: daisyfeller
ms.reviewer: samanro
manager: pamgreen
ms.topic: article
audience: admin
ms.service: microsoft-365-frontline
search.appverid: MET150
description: Découvrez comment configurer une version d’évaluation teams de 90 jours pour les employés de première ligne pour votre organisation.
ms.localizationpriority: high
ms.collection:
- m365-frontline
- highpri
appliesto:
- Microsoft Teams
- Microsoft 365 for frontline workers
ms.openlocfilehash: 464215390de3f045499fba8d332fe75f9bfe610d
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68051121"
---
# <a name="manage-the-frontline-trial-in-teams"></a>Gérer la version d’évaluation en première ligne dans Teams

> [!NOTE]
> Cette expérience d’essai sera bientôt disponible. Vous pouvez vérifier si cela est disponible pour votre organisation en recherchant un message dans le [Centre de messages](https://go.microsoft.com/fwlink/p/?linkid=2070717)  de votre centre d’administration Microsoft 365.

L’expérience d’évaluation en ligne de Microsoft Teams permet aux utilisateurs de votre organisation qui sont dans Teams de lancer une expérience Teams pour toute leur équipe de première ligne, tant que les autres membres sont dans Azure Active Directory (Azure AD). Vous pouvez désactiver cette fonctionnalité pour les utilisateurs de votre organisation à l’aide du [module PowerShell AllowSelfServicePurchase](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

## <a name="what-services-are-included"></a>Quels services sont inclus

La version d’évaluation inclut tous les éléments de la [licence Microsoft 365 F3](https://www.microsoft.com/microsoft-365/enterprise/f3) avec les exceptions suivantes :

- La version d’évaluation en première ligne inclut Exchange Foundation plutôt qu’Exchange Kiosk. D’autres fonctionnalités Teams peuvent être manquantes pour les utilisateurs en raison de cette modification.

## <a name="eligibility"></a>Éligibilité

> [!NOTE]
> Vous pouvez vérifier si votre organisation fait partie du pilote d’évaluation en recherchant une annonce dans le [Centre de messages](https://go.microsoft.com/fwlink/p/?linkid=2070717) de votre centre d’administration Microsoft 365. Votre organisation doit faire partie du pilote d’essai pour que les utilisateurs puissent lancer ou participer à une version d’évaluation. Cette offre n’est pas valable pour les clients GCC, GCC HIGH, DoD ou EDU.

La version d’évaluation en ligne peut accueillir un maximum de 300 utilisateurs par version d’évaluation.

Les utilisateurs peuvent démarrer une version d’évaluation de première ligne pour leur équipe s’ils :

- Disposer d’une licence active qui leur donne accès à Teams.
- N’avez pas encore commencé une version d’évaluation de personnel de première ligne.

> [!IMPORTANT]
> Si l’utilisateur qui a lancé la version d’évaluation quitte votre organisation avant la fin de l’essai, vous, en tant qu’administrateur, devez surveiller la version d’évaluation, consulter l’équipe pour voir qui tire parti de ces fonctionnalités et décider quels utilisateurs vous devrez mettre à niveau vers une licence payante.

Les utilisateurs peuvent participer à une version d’évaluation de personnel de première ligne s’ils disposent d’une adresse e-mail de domaine Azure Active Directory gérée.

Les utilisateurs peuvent participer s’ils ont déjà commencé une version d’évaluation, mais ne peuvent pas lancer une autre version d’évaluation.

> [!NOTE]
> Les utilisateurs sans accès existant à Teams peuvent uniquement être ajoutés à l’équipe d’évaluation au moment de la création de l’équipe. Les utilisateurs Teams existants peuvent toujours être ajoutés à la version d’évaluation après la création de l’équipe.

## <a name="set-up-the-trial"></a>Configurer la version d’évaluation

Les utilisateurs éligibles peuvent démarrer une version d’évaluation en ligne en se connectant à l’application Tâches dans Teams à partir de [l’application web](https://teams.microsoft.com/_#/apps/com.microsoft.teamspace.tab.planner/sections/mytasks) ou de bureau. Pour l’instant, le démarrage d’une version d’évaluation de première ligne via un appareil mobile n’est pas pris en charge. Lorsqu’une version d’évaluation est lancée, l’équipe entière reçoit automatiquement la licence d’évaluation de première ligne. Les utilisateurs disposant de licences payantes existantes qui leur donnent accès à Teams se verront également attribuer des licences d’évaluation, mais conserveront les fonctionnalités de leurs licences existantes tout au long de la période d’essai et conserveront leurs licences payantes existantes après la fin de l’essai. L’utilisateur qui a démarré la version d’évaluation recevra des notifications par e-mail tout au long de l’essai.

## <a name="manage-the-frontline-trials-experience"></a>Gérer l’expérience d’essais en première ligne

Les administrateurs peuvent empêcher les utilisateurs finaux de démarrer la version d’évaluation en ligne au sein de leur organisation à l’aide du module PowerShell **AllowSelfServicePurchase** . Cela concerne uniquement les licences d’évaluation. [Découvrez comment utiliser le module PowerShell AllowSelfServicePurchase](/microsoft-365/commerce/subscriptions/allowselfservicepurchase-powershell).

### <a name="manage-teams-for-users-who-have-the-frontline-trial-license"></a>Gérer Teams pour les utilisateurs disposant de la licence d’évaluation de première ligne

Vous pouvez gérer les utilisateurs qui disposent de la licence d’évaluation de première ligne, tout comme vous gérez les utilisateurs qui disposent d’une licence payante standard. Pour plus d’informations[Gérer les paramètres de Teams pour votre organisation](/microsoftteams/manage-teams-overview).

### <a name="remove-a-trial-license"></a>Supprimer une licence d’évaluation

Vous pouvez supprimer la licence d’évaluation de première ligne via PowerShell ou votre Centre d'administration Microsoft 365.

[Découvrez comment supprimer avec PowerShell](/office365/enterprise/powershell/remove-licenses-from-user-accounts-with-office-365-powershell).

[Découvrez comment supprimer dans le Centre d’administration](/microsoft-365/admin/add-users/delete-a-user).

## <a name="upgrade-users-from-frontline-trial"></a>Mettre à niveau des utilisateurs à partir d’une version d’évaluation de première ligne

Les utilisateurs peuvent vous contacter pour demander des licences à la fin de l’essai. Vous aurez besoin de privilèges d’administrateur pour mettre à niveau vos utilisateurs.

### <a name="when-to-upgrade"></a>Quand mettre à niveau

Vers la fin de la période d’essai de 90 jours, vous devez vérifier auprès de vos utilisateurs qui doivent continuer avec une licence payante. Veillez à le faire avant l’expiration de l’abonnement d’évaluation de première ligne pour éviter toute interruption de l’expérience des utilisateurs.

> [!IMPORTANT]
> Si la licence d’évaluation de première ligne se termine et qu’un utilisateur ne reçoit pas immédiatement une licence qui inclut Teams, il perd l’accès à Teams. Au bout de 30 jours, leurs données (fichiers, messages, etc.) sont supprimées. L’utilisateur demeure dans Azure Active Directory. Si une nouvelle licence est attribuée à l’utilisateur pour activer la fonctionnalité Teams au cours de la période de 30 jours, tout son contenu dans Teams existera toujours.

### <a name="choose-an-upgrade-path"></a>Choisir un chemin de mise à niveau

> [!TIP]
> La version d’évaluation de première ligne est basée sur la [licence Microsoft 365 F3](https://www.microsoft.com/microsoft-365/enterprise/f3).

En fonction des abonnements dont votre organisation dispose actuellement, il existe trois façons de passer d’une version d’évaluation de première ligne à une licence payante :

- **Mettez à niveau un abonnement Microsoft 365 existant.** Utilisez cette option si votre organisation dispose d’abonnements à d’autres produits Office qui n’incluent pas Teams. Pour plus d’informations, consultez [Mettre à niveau vers un autre plan](/microsoft-365/commerce/subscriptions/upgrade-to-different-plan). Pour afficher les utilisateurs actifs d’un abonnement existant, accédez à **Utilisateurs >** [Utilisateurs actifs](https://go.microsoft.com/fwlink/p/?linkid=834822) dans le centre d’administration Microsoft 365.

- **Ajoutez des utilisateurs à un abonnement Microsoft 365 existant.** Utilisez cette option si votre organisation ne dispose pas de suffisamment de licences Teams payantes pour couvrir votre équipe de première ligne. Pour plus d’informations, consultez [Acheter ou supprimer des licences](/microsoft-365/commerce/licenses/buy-licenses). Pour ajouter des utilisateurs à un abonnement existant qui dispose déjà de suffisamment de licences disponibles, consultez [Déplacer les utilisateurs vers un autre abonnement](/microsoft-365/commerce/subscriptions/move-users-different-subscription). Pour afficher les utilisateurs actifs d’un abonnement existant, accédez à **Utilisateurs >** [Utilisateurs actifs](https://go.microsoft.com/fwlink/p/?linkid=834822) dans le centre d’administration Microsoft 365.

- **Acheter un nouvel abonnement Microsoft 365.** Utilisez cette option si votre organisation n’a pas d’abonnements existants aux produits Office ou si votre organisation souhaite acheter un abonnement différent de son abonnement existant pour couvrir les utilisateurs de première ligne. Pour plus d’informations, consultez [Microsoft 365 pour les employés de première ligne](https://www.microsoft.com/microsoft-365/enterprise/frontline).

Si vous ne savez pas vers quel abonnement Microsoft 365 effectuer la mise à niveau, consultez [Microsoft 365 pour les employés de première ligne](https://www.microsoft.com/microsoft-365/enterprise/frontline). Si vous avez besoin d’aide supplémentaire pour choisir un abonnement ou si votre organisation a besoin de plus de 300 licences, contactez votre [partenaire Microsoft](https://www.microsoft.com/solution-providers/home) ou compte Microsoft représentant.

### <a name="assign-paid-licenses"></a>Attribuer des licences payantes

Pour attribuer vos licences nouvellement acquises, consultez [Attribuer des licences aux utilisateurs](/microsoft-365/admin/manage/assign-licenses-to-users).  

Après avoir attribué les nouvelles licences, retirez les licences exploratoires Teams. Pour plus d’informations, consultez [Retirer des licences aux utilisateurs](/microsoft-365/admin/manage/remove-licenses-from-users).

## <a name="faq"></a>FAQ

**Durée de la version d’évaluation** <br>
La version d’évaluation de première ligne dure 90 jours.

**Que doivent faire les administrateurs à la fin de l’expérience d’essai de première ligne de 90 jours ?** <br>
À la fin de la version d’évaluation de 90 jours, vous devez vérifier auprès de vos utilisateurs qui doivent continuer avec une licence payante. Vous devrez ensuite [Mettre à niveau vos utilisateurs](#upgrade-users-from-frontline-trial).

**Que se passe-t-il si l’utilisateur qui a démarré l’essai quitte votre organisation ?** <br>
En tant qu’administrateur, vous devrez surveiller l’essai pour le reste de la période de 90 jours et effectuer une mise à niveau vers des licences payantes pour les utilisateurs qui en ont besoin à la fin de l’essai.

**Qu’est-ce que la stratégie de rétention des données ?** <br>
Vous pouvez en savoir plus sur la rétention des données à partir des [informations d’abonnement Microsoft 365](/microsoft-365/commerce/subscriptions/what-if-my-subscription-expires?).

**Que se passe-t-il si un utilisateur rencontre une erreur lors du démarrage de la version d’évaluation de première ligne ?** <br>
Assurez-vous que votre organisation, l’utilisateur qui démarre la version d’évaluation et les utilisateurs ajoutés à la version d’évaluation répondent aux [critères d’éligibilité](#eligibility).