---
title: Power BI dans votre organisation
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- Adm_O365
- Adm_NonTOC
search.appverid:
- MET150
- PWB150
ms.assetid: d7941332-8aec-4e5e-87e8-92073ce73dc5
ROBOTS: NOINDEX
description: Découvrez Power BI et comment les utilisateurs de votre organisation peuvent utiliser ce service Business Analytics.
ms.openlocfilehash: 56a6dd1c90b8dcb810e74c36b5e7f93ab6a0eb2c
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42254271"
---
# <a name="power-bi-in-your-organization"></a>Power BI dans votre organisation

[] Cette page décrit la façon dont les membres de votre organisation peuvent utiliser Power BI et la façon dont vous pouvez contrôler l'acquisition de ce service par votre organisation.
    
## <a name="what-is-power-bi"></a>Qu'est-ce que Power BI ?

Microsoft Power BI permet aux utilisateurs de visualiser des données, de partager des découvertes et de collaborer de façon intuitive et inédite. Pour en savoir plus, consultez le [site web Power BI](https://powerbi.microsoft.com/en-us/).
  
## <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Est-ce que Power BI répond aux exigences de conformité nationales, régionales et industrielles ?

Pour en savoir plus sur la conformité Power BI, consultez le centre de gestion de la [confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=785324).
  
## <a name="how-do-users-sign-up-for-power-bi"></a>Comment les utilisateurs peuvent-ils s'inscrire à Power BI ?

En tant qu'administrateur, vous pouvez vous inscrire à Power BI via le [site web Power BI](https://powerbi.microsoft.com/en-us/). Vous pouvez également vous inscrire via la page acheter des services dans le centre d’administration Microsoft 365. Lorsqu'un administrateur s'inscrit à Power BI, il peut affecter des licences d'abonnement aux utilisateurs qui doivent y accéder.
  
Par ailleurs, il est possible que les utilisateurs dans votre organisation puissent s'inscrire à Power BI via le [site web Power BI](https://powerbi.microsoft.com/en-us/). Lorsqu'un utilisateur de votre organisation s'inscrit à Power BI, cet utilisateur se voit affecter une licence Power BI automatiquement.
  
## <a name="how-do-individual-users-in-my-organization-sign-up"></a>Comment les utilisateurs individuels de mon organisation peuvent-ils s'inscrire ?

Trois scénarios peuvent s'appliquer aux utilisateurs de votre organisation :
  
### <a name="scenario-1-your-organization-already-has-an-existing-office-365-environment-and-the-user-signing-up-for-power-bi-already-has-an-office-365-account"></a>Scénario 1 : votre organisation possède déjà un environnement Office 365 et l'utilisateur qui s'inscrit à Power BI a déjà un compte Office 365.

Dans ce scénario, si un utilisateur possède déjà un compte professionnel ou scolaire dans le client (par exemple, contoso.com) mais n'a pas encore Power BI, Microsoft activera simplement l'offre pour ce compte et l'utilisateur sera automatiquement informé en relation avec l'utilisation du service Power BI.
  
### <a name="scenario-2-your-organization-has-an-existing-office-365-environment-and-the-user-signing-up-for-power-bi-doesnt-have-an-office-365-account"></a>Scénario 2 : votre organisation possède un environnement Office 365 et l'utilisateur qui s'inscrit à Power BI n'a pas de compte Office 365.

Dans ce scénario, l'utilisateur a une adresse de messagerie dans le domaine de votre organisation (par exemple, contoso.com), mais n'a pas encore de compte Office 365. Il peut dès lors s'inscrire à Power BI afin de se voir automatiquement attribuer un compte. Cela permet à l'utilisateur d'accéder au service Power BI. Par exemple, si une employé nommée Marie utilise son adresse de messagerie professionnelle (par exemple, marie@contoso.com) pour s'inscrire, Microsoft ajoutera automatiquement Nancy en tant qu'utilisateur dans l'environnement Office 365 de Contoso et activera Power BI pour ce compte.
  
### <a name="scenario-3-your-organization-does-not-have-an-office-365-environment-connected-to-your-email-domain"></a>Scénario 3 : votre organisation n'a pas d'environnement Office 365 connecté à votre domaine de messagerie.

Il n'est pas nécessaire que votre organisation prenne une action administrative pour utiliser Power BI.
  
> [!IMPORTANT]
> Si votre organisation dispose de plusieurs domaines de messagerie et que vous préférez que toutes les extensions d’adresse de messagerie se trouvent dans le même client, avant que tous les utilisateurs créent votre client principal, ajoutez tous les domaines d’adresse de messagerie à ce client avant que les utilisateurs ne créent votre client principal. Il n’existe pas de mécanisme automatisé pour déplacer des utilisateurs entre les clients une fois qu’ils ont été créés. Pour plus d’informations sur ce processus, voir [si j’ai plusieurs domaines, puis-je contrôler le client Office 365 auquel les utilisateurs sont ajoutés ?](#if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to) plus loin dans cet article, puis [Ajouter un domaine à Office 365](../setup/add-domain.md) online. 
  
## <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Quelles seront les conséquences sur ma méthode actuelle de gestion des identités pour les utilisateurs de mon organisation ?

Si votre organisation possède déjà un environnement Office 365 et que tous les utilisateurs de votre organisation ont des comptes Office 365, la gestion des identités ne change pas.
  
Si votre organisation possède déjà un environnement Office 365 mais que tous les utilisateurs n'ont pas de compte Office 365, Microsoft crée un utilisateur dans le client et attribue des licences en fonction de l'adresse de messagerie professionnelle ou scolaire de l'utilisateur. Cela signifie que le nombre d'utilisateurs que vous gérez à un moment donné augmente à mesure que les utilisateurs de votre organisation s'inscrivent au service.
  
Si vous gérez votre répertoire localement et utilisez Active Directory Federation Services (AD FS), Microsoft n'ajoute pas les utilisateurs à votre client. Les utilisateurs qui tentent de rejoindre votre client reçoivent un message leur indiquant de contacter l'administrateur de l'organisation.
  
Si votre organisation n'a pas d'environnement Office 365 connecté à votre domaine de messagerie, votre méthode de gestion des identités reste inchangée. Les utilisateurs sont ajoutés à un nouveau répertoire d'utilisateurs situé exclusivement sur le cloud. Vous avez en outre la possibilité de choisir de prendre la main en tant qu'administrateur du client afin de les gérer.
  
## <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Quel est la procédure à suivre pour gérer un client créé par Microsoft pour mes utilisateurs ?

Si un client a été créé par Microsoft, vous pouvez le revendiquer et le gérer en procédant comme suit :
  
1. Rejoignez le client en [vous inscrivant à Power BI](https://go.microsoft.com/fwlink/?LinkId=522448) à l'aide d'un domaine d'adresse de messagerie correspondant au domaine du client que vous voulez gérer. Par exemple, si Microsoft a créé le client contoso.com, vous devez rejoindre le client avec une adresse de messagerie se terminant par @contoso.com. 
    
2. Revendiquez le contrôle d'administrateur en vérifiant que vous êtes propriétaire du domaine : une fois dans le client, vous pouvez vous attribuer vous-même le rôle d'administrateur en vérifiant la propriété du domaine. Pour ce faire, procédez comme suit :
 
::: moniker range="o365-worldwide"
   
3. Accédez à [https://admin.microsoft.com](https://admin.microsoft.com).
 

::: moniker-end

::: moniker range="o365-germany"

3. Accédez à [https://portal.office.de](https://portal.office.de).

::: moniker-end

::: moniker range="o365-21vianet"

3. Accédez à [https://portal.partner.microsoftonline.cn](https://portal.partner.microsoftonline.cn).

::: moniker-end

    
4. Sélectionnez l’icône du lanceur d’applications située en haut à gauche et choisissez **Administrateur**.
    
    ![The Office 365 app launcher with the Admin app highlighted](../media/4eea9dbc-591b-48be-9916-322d41c6525b.png)
  
5. Lisez les instructions de la page **devenir administrateur** , puis sélectionnez **Oui, je veux être administrateur**.
    
    > [!NOTE]
    >  Si cette option ne s’affiche pas, cela signifie qu’un administrateur est déjà en place. 
  
## <a name="if-i-have-multiple-domains-can-i-control-the-office-365-tenant-that-users-are-added-to"></a>Si j'utilise plusieurs domaines, puis-je contrôler le client Office 365 auquel sont ajoutés les utilisateurs ?

Si vous ne faites rien, un client est créé pour chaque domaine et sous-domaine de messagerie d'utilisateur.
  
Si vous voulez regrouper tous les utilisateurs dans un seul client quelle que soit leur extension d'adresse de messagerie :
  
- Créez un client cible au préalable, ou utilisez un client existant, et ajoutez tous les domaines et sous-domaines existants que vous voulez regrouper au sein de ce client. Tous les utilisateurs dont les adresses de messagerie se terminent par ces domaines et sous-domaines rejoindront ensuite automatiquement le client cible lors de leur inscription.
    
> [!IMPORTANT]
> Il n'existe aucun mécanisme automatisé pris en charge pour déplacer les utilisateurs d'un client à l'autre une fois créés. Pour en savoir plus sur l’ajout de domaines à un seul client Office 365, consultez [la rubrique ajouter un domaine à office 365](../setup/add-domain.md). 
  
> [!IMPORTANT]
> Pour plus d’informations et de conseils sur la gestion des clients, voir [qu’est-ce que Power bi administration ?](https://docs.microsoft.com/power-bi/service-admin-administering-power-bi-in-your-organization). 
  
## <a name="how-can-i-prevent-users-from-joining-my-existing-office-365-tenant"></a>Comment empêcher les utilisateurs de rejoindre mon client Office 365 existant ?

Il existe des étapes que vous pouvez prendre en tant qu’administrateur pour empêcher les utilisateurs de rejoindre votre client Office 365 existant. Si vous bloquez cette opération, les tentatives de connexion des utilisateurs échoueront et seront dirigées pour contacter l’administrateur de leur organisation. Vous n’avez pas besoin de répéter ce processus si vous avez déjà désactivé la distribution automatique des licences (par exemple, Office 365 éducation pour les étudiants, le corps enseignant et le personnel).
  
Cette procédure requiert l'utilisation de Windows PowerShell. Pour prendre en main Windows PowerShell, voir le [guide de prise en main de PowerShell](https://go.microsoft.com/fwlink/p/?LinkID=286814).
  
Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module Azure Active Directory pour Windows PowerShell](https://www.powershellgallery.com/packages/AzureADPreview/2.0.2.5).
  
Après avoir sélectionné le lien, sélectionnez **exécuter** pour exécuter le package d’installation. 
  
 **Désactiver l'association automatique au client**: utilisez cette commande Windows PowerShell pour empêcher les nouveaux utilisateurs de rejoindre un client géré :
  
Pour désactiver l'association automatique au client des nouveaux utilisateurs :  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $false`
  
Pour activer l'association automatique au client des nouveaux utilisateurs :  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
> [!NOTE]
> Ce blocage empêche les nouveaux utilisateurs de votre organisation de s’inscrire à Power BI. Les utilisateurs qui s’inscrivent à Power BI avant de désactiver les nouveaux abonnements pour votre organisation conserveront toujours leurs licences. Voir la [procédure de suppression de Power bi pour les utilisateurs qui se sont déjà inscrits ?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) pour obtenir des instructions sur la manière dont vous pouvez supprimer l’accès à Power bi pour les utilisateurs qui se sont déjà inscrit au service. 
  
## <a name="how-can-i-allow-users-to-join-my-existing-office-365-tenant"></a>Comment autoriser les utilisateurs à rejoindre mon client Office 365 existant ?

Pour autoriser les utilisateurs à rejoindre votre client, exécutez la commande inverse, comme décrit dans la question ci-dessus :  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
## <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Comment vérifier que le blocage est activé dans le client ?

Utilisez le script PowerShell suivant :  `Get-MsolCompanyInformation | fl allow*`
  
## <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Comment empêcher les utilisateurs existants d'utiliser Power BI ?

 **Désactiver la distribution automatique de licences :** utilisez ce script Windows PowerShell pour désactiver la distribution automatique de licences pour les utilisateurs existants. Vous n’avez pas besoin de répéter ce processus si vous avez déjà désactivé la distribution automatique des licences (par exemple, Office 365 éducation pour les étudiants, le corps enseignant et le personnel). 
  
Pour désactiver la distribution automatique de licences pour les utilisateurs existants :  `Set-MsolCompanySettings -AllowAdHocSubscriptions $false`
  
Pour activer la distribution automatique de licences pour les utilisateurs existants :  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
> [!NOTE]
> L’indicateur *AllowAdHocSubscriptions* est utilisé pour contrôler plusieurs fonctionnalités utilisateur au sein de votre organisation, y compris la possibilité pour les utilisateurs de s’inscrire au service Azure Rights Management. La modification de cet indicateur affecte toutes ces fonctionnalités. 
  
## <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Comment autoriser mes utilisateurs existants à s'inscrire à Power BI ?

Pour autoriser les utilisateurs existants à s'inscrire à Power BI, exécutez la commande inverse, comme décrit dans la question ci-dessus :  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
## <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Comment supprimer Power BI pour les utilisateurs déjà inscrits ?

Si un utilisateur s'est inscrit à Power BI mais que vous ne souhaitez plus qu'il accède à Power BI, vous pouvez supprimer la licence Power BI pour cet utilisateur.

::: moniker range="o365-worldwide"

> [!NOTE]
> Si le nouveau Centre d’administration Microsoft 365 n’est pas celui que vous utilisez, vous pouvez l’activer en sélectionnant le bouton bascule **Essayer le nouveau Centre d’administration** situé en haut de la page d’accueil.
  
1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.
    
2. Recherchez l’utilisateur dont vous souhaitez supprimer la licence, puis sélectionnez son nom.
    
3. Sous l’onglet **licences et applications** , désactivez la case à cocher **Microsoft Power bi** .
    
4. Sélectionnez **enregistrer les modifications**.

::: moniker-end

  
::: moniker range="o365-germany"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=847686" target="_blank">Utilisateurs actifs</a>.

2. Recherchez l’utilisateur dont vous souhaitez supprimer la licence, puis sélectionnez son nom.
    
3. En regard de **licences de produit**, sélectionnez **modifier**. 
    
4. Désactivez l’option **Microsoft Power bi** .
    
5. Cliquez sur **Enregistrer**.

::: moniker-end

::: moniker range="o365-21vianet"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

2. Recherchez l’utilisateur dont vous souhaitez supprimer la licence, puis sélectionnez son nom.
    
3. En regard de **licences de produit**, sélectionnez **modifier**. 
    
4. Désactivez l’option **Microsoft Power bi** .
    
5. Cliquez sur **Enregistrer**.

::: moniker-end 


## <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Comment connaître la date à laquelle les nouveaux utilisateurs ont rejoint mon client ?

Les utilisateurs qui ont rejoint votre client dans le cadre de ce programme se voient attribuer une licence unique, que vous pouvez filtrer dans votre volet d'utilisateur actif dans le tableau de bord d'administration.
  
Pour créer cette nouvelle vue, dans le centre d’administration, suivez les étapes décrites dans la procédure [créer un affichage utilisateur personnalisé](../add-users/create-edit-or-delete-a-custom-user-view.md#create-a-custom-user-view). Sous **licence de produit attribuée**, sélectionnez **Microsoft Power bi**. Une fois que le nouvel affichage a été créé, vous pourrez voir tous les utilisateurs de votre client qui ont inscrit dans ce programme.
  
## <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Quels sont les éventuels autres aspects auxquels je dois être préparé ?

Vous pouvez éventuellement faire face à une augmentation des demandes de réinitialisation de mot de passe. Pour plus d'informations sur ce processus, voir [Réinitialiser le mot de passe d'un utilisateur](../add-users/reset-passwords.md).
  
Vous pouvez supprimer un utilisateur de votre client via le processus standard dans le centre d’administration. Cependant, si l'utilisateur a toujours une adresse de messagerie active de votre organisation, il pourra rejoindre le client, sauf si vous empêchez tous les utilisateurs de le faire.
  
## <a name="why-did-1-million-licenses-for-microsoft-power-bi-show-up-in-my-office-365-tenant"></a>Pourquoi un million de licences pour Microsoft Power BI apparaissent-elles dans mon client Office 365 ?

En tant qu’organisation éligible, les utilisateurs de votre organisation peuvent utiliser le service Microsoft Power BI et ces licences représentent la capacité disponible pour les nouveaux utilisateurs de Power BI de votre client. Ces licences ne sont pas facturées. Si vous avez choisi d’autoriser les utilisateurs à s’inscrire à Power BI, ils se verront attribuer l’une de ces licences gratuites disponibles une fois le processus d’inscription terminé. Vous pouvez également choisir d’affecter ces licences aux utilisateurs vous-même via le centre d’administration.
  
## <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Est-ce gratuit ? Ces licences me seront-elles facturées ?

Ces licences s'appliquent à la version gratuite de Power BI. Si vous êtes intéressé par des fonctionnalités supplémentaires, jetez un coup d'œil à la version professionnelle de Power BI.
  
## <a name="why-1-million-licenses"></a>Pourquoi un million de licences ?

Nous avons choisi un nombre suffisamment élevé pour que la majorité des organisations aient des licences suffisantes pour fournir ce bénéfice sans retard à leurs utilisateurs.
  
## <a name="what-if-i-need-more-than-1-million-licenses"></a>Comment faire pour bénéficier de plus d'un million de licences ?

Si vous prévoyez d'acquérir des licences supplémentaires, contactez votre représentant Microsoft.