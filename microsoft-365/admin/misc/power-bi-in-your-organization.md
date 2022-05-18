---
title: Power BI dans votre organisation
f1.keywords:
- NOCSH
ms.author: cmcatee
author: cmcatee-MSFT
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- Adm_O365
- Adm_NonTOC
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- PWB150
ms.assetid: d7941332-8aec-4e5e-87e8-92073ce73dc5
ROBOTS: NOINDEX
description: Découvrez Power BI et comment les utilisateurs de votre organisation peuvent utiliser ce service d’analytique métier.
ms.openlocfilehash: b4e1fd299caa4045a68770adc3a2d53dd4b11ec0
ms.sourcegitcommit: da6b3cb3b2ccfcdcd5091efce8290b6c486547db
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/18/2022
ms.locfileid: "65469533"
---
# <a name="using-power-bi-data-in-your-organization"></a>Utilisation de données Power BI dans votre organisation

[] Cette page décrit la façon dont les membres de votre organisation peuvent utiliser Power BI et la façon dont vous pouvez contrôler l'acquisition de ce service par votre organisation.

## <a name="what-is-power-bi"></a>Qu'est-ce que Power BI ?

Microsoft Power BI permet aux utilisateurs de visualiser des données, de partager des découvertes et de collaborer de façon intuitive et inédite. Pour en savoir plus, consultez le [site web Power BI](https://powerbi.microsoft.com/en-us/).
  
## <a name="does-power-bi-meet-national-regional-and-industry-specific-compliance-requirements"></a>Les Power BI répondent-ils aux exigences de conformité nationales, régionales et sectorielles ?

Pour en savoir plus sur Power BI conformité, consultez le Centre de gestion de la [confidentialité Microsoft](https://go.microsoft.com/fwlink/?LinkId=785324).
  
## <a name="how-do-users-sign-up-for-power-bi"></a>Comment les utilisateurs peuvent-ils s'inscrire à Power BI ?

En tant qu'administrateur, vous pouvez vous inscrire à Power BI via le [site web Power BI](https://powerbi.microsoft.com/en-us/). Vous pouvez également vous inscrire via la page des services d’achat sur le Centre d'administration Microsoft 365. Lorsqu'un administrateur s'inscrit à Power BI, il peut affecter des licences d'abonnement aux utilisateurs qui doivent y accéder.
  
Par ailleurs, il est possible que les utilisateurs dans votre organisation puissent s'inscrire à Power BI via le [site web Power BI](https://powerbi.microsoft.com/en-us/). Lorsqu'un utilisateur de votre organisation s'inscrit à Power BI, cet utilisateur se voit affecter une licence Power BI automatiquement.
  
## <a name="how-do-individual-users-in-my-organization-sign-up"></a>Comment les utilisateurs individuels de mon organisation peuvent-ils s'inscrire ?

Trois scénarios peuvent s'appliquer aux utilisateurs de votre organisation :
  
### <a name="scenario-1-your-organization-already-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-already-has-a-microsoft-365-account"></a>Scénario 1 : Votre organisation dispose déjà d’un environnement Microsoft 365 et l’utilisateur qui s’inscrit à Power BI dispose déjà d’un compte Microsoft 365.

Dans ce scénario, si un utilisateur possède déjà un compte professionnel ou scolaire dans le client (par exemple, contoso.com) mais n'a pas encore Power BI, Microsoft activera simplement l'offre pour ce compte et l'utilisateur sera automatiquement informé en relation avec l'utilisation du service Power BI.
  
### <a name="scenario-2-your-organization-has-an-existing-microsoft-365-environment-and-the-user-signing-up-for-power-bi-doesnt-have-a-microsoft-365-account"></a>Scénario 2 : Votre organisation dispose d’un environnement Microsoft 365 existant et l’utilisateur qui s’inscrit à Power BI n’a pas de compte Microsoft 365.

Dans ce scénario, l’utilisateur a une adresse e-mail dans le domaine de votre organisation (par exemple, contoso.com), mais n’a pas encore de compte Microsoft 365. Il peut dès lors s'inscrire à Power BI afin de se voir automatiquement attribuer un compte. Cela permet à l'utilisateur d'accéder au service Power BI. Par exemple, si un employé nommé Nancy utilise son adresse e-mail professionnelle (par exemple, Nancy@contoso.com) pour s’inscrire, Microsoft ajoute automatiquement Nancy en tant qu’utilisateur dans l’environnement de Microsoft 365 Contoso et active Power BI pour ce compte.
  
### <a name="scenario-3-your-organization-does-not-have-a-microsoft-365-environment-connected-to-your-email-domain"></a>Scénario 3 : Votre organisation n’a pas d’environnement Microsoft 365 connecté à votre domaine de messagerie.

Aucune action administrative n’est nécessaire à votre organisation pour tirer parti de Power BI.
  
> [!IMPORTANT]
> Si votre organisation dispose de plusieurs domaines de messagerie et que vous préférez que toutes les extensions d’adresse e-mail soient dans le même locataire, avant que les utilisateurs ne créent votre locataire principal, ajoutez tous les domaines d’adresse e-mail à ce locataire avant que les utilisateurs ne créent votre locataire principal. Il n’existe aucun mécanisme automatisé pour déplacer les utilisateurs entre les locataires une fois qu’ils ont été créés. Pour plus d’informations sur ce processus, consultez [Si j’ai plusieurs domaines, puis-je contrôler le locataire auquel les utilisateurs sont ajoutés ?](#if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to) plus loin dans cet article et [ajouter un domaine à Office 365](../setup/add-domain.md) en ligne.
  
## <a name="how-will-this-change-the-way-i-manage-identities-for-users-in-my-organization-today"></a>Quelles seront les conséquences sur ma méthode actuelle de gestion des identités pour les utilisateurs de mon organisation ?

Si votre organisation dispose déjà d’un environnement Microsoft 365 et que tous les utilisateurs de votre organisation ont des comptes Microsoft 365, la gestion des identités ne changera pas.
  
Si votre organisation dispose déjà d’un environnement Microsoft 365 mais que tous les utilisateurs de votre organisation n’ont pas de comptes Microsoft 365, nous allons créer un utilisateur dans le locataire et attribuer des licences en fonction de l’adresse e-mail professionnelle ou scolaire de l’utilisateur. Cela signifie que le nombre d'utilisateurs que vous gérez à un moment donné augmente à mesure que les utilisateurs de votre organisation s'inscrivent au service.
  
Si vous gérez votre répertoire localement et utilisez Active Directory Federation Services (AD FS), Microsoft n'ajoute pas les utilisateurs à votre client. Les utilisateurs qui tentent de rejoindre votre client reçoivent un message leur indiquant de contacter l'administrateur de l'organisation.
  
Si votre organisation n’a pas d’environnement Microsoft 365 connecté à votre domaine de messagerie, il n’y aura aucun changement dans la façon dont vous gérez l’identité. Les utilisateurs seront ajoutés à un nouveau répertoire d’utilisateurs cloud uniquement, et vous aurez la possibilité de choisir de prendre le relais en tant qu’administrateur du locataire et de les gérer.
  
## <a name="what-is-the-process-to-manage-a-tenant-created-by-microsoft-for-my-users"></a>Quel est la procédure à suivre pour gérer un client créé par Microsoft pour mes utilisateurs ?

Si un client a été créé par Microsoft, vous pouvez le revendiquer et le gérer en procédant comme suit :
  
1. Rejoignez le client en [vous inscrivant à Power BI](https://go.microsoft.com/fwlink/?LinkId=522448) à l'aide d'un domaine d'adresse de messagerie correspondant au domaine du client que vous voulez gérer. Par exemple, si Microsoft a créé le client contoso.com, vous devez rejoindre le client avec une adresse de messagerie se terminant par @contoso.com.

1. Revendiquez le contrôle d'administrateur en vérifiant que vous êtes propriétaire du domaine : une fois dans le client, vous pouvez vous attribuer vous-même le rôle d'administrateur en vérifiant la propriété du domaine. Pour ce faire, procédez comme suit :

::: moniker range="o365-worldwide"

3. Accédez à <a href="https://admin.microsoft.com" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

3. Accédez à <a href="https://portal.partner.microsoftonline.cn" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end

4. Sélectionnez l’icône du lanceur d’applications située en haut à gauche et choisissez **Administrateur**.

    ![Lanceur d’applications avec l’application d’administration mise en surbrillance.](../../media/4eea9dbc-591b-48be-9916-322d41c6525b.png)
  
5. Lisez les instructions de la page **Devenir l’administrateur** , puis sélectionnez **Oui, je veux être l’administrateur**.

    > [!NOTE]
    >  Si cette option n’apparaît pas, un administrateur est déjà en place.
  
## <a name="if-i-have-multiple-domains-can-i-control-the-tenant-that-users-are-added-to"></a>Si j’ai plusieurs domaines, puis-je contrôler le locataire auquel les utilisateurs sont ajoutés ?

Si vous ne faites rien, un client est créé pour chaque domaine et sous-domaine de messagerie d'utilisateur.
  
Si vous voulez regrouper tous les utilisateurs dans un seul client quelle que soit leur extension d'adresse de messagerie :
  
- Créez un client cible au préalable, ou utilisez un client existant, et ajoutez tous les domaines et sous-domaines existants que vous voulez regrouper au sein de ce client. Tous les utilisateurs dont les adresses de messagerie se terminent par ces domaines et sous-domaines rejoindront ensuite automatiquement le client cible lors de leur inscription.

> [!IMPORTANT]
> Aucun mécanisme automatisé pris en charge n’est disponible pour déplacer les utilisateurs d’un locataire à un autre après leur création. Pour en savoir plus sur l’ajout de domaines à un seul locataire Microsoft 365, consultez [Ajouter un domaine à Office 365](../setup/add-domain.md).

> [!IMPORTANT]
> Pour plus d’informations et des conseils sur la gestion des locataires, consultez [Qu’est-ce que Power BI administration ?](/power-bi/service-admin-administering-power-bi-in-your-organization)
  
## <a name="how-can-i-prevent-users-from-joining-my-existing-tenant"></a>Comment empêcher les utilisateurs de rejoindre mon locataire existant ?

Il existe des étapes que vous pouvez suivre en tant qu’administrateur pour empêcher les utilisateurs de rejoindre votre locataire existant. Si vous empêchez les utilisateurs de rejoindre le locataire, les tentatives de connexion des utilisateurs échouent et ils sont invités à contacter l’administrateur de leur organisation. Vous n’avez pas besoin de répéter ce processus si vous avez déjà désactivé la distribution automatique de licences avant (par exemple, Office 365 Éducation pour les étudiants, les enseignants et le personnel).
  
Cette procédure requiert l'utilisation de Windows PowerShell. Pour prendre en main Windows PowerShell, voir le [guide de prise en main de PowerShell](/powershell/scripting/overview).
  
Pour effectuer les étapes suivantes, vous devez installer la dernière version 64 bits du [module PowerShell Azure Active Directory V2](https://www.powershellgallery.com/packages/AzureADPreview/2.0.2.5).
  
Après avoir cliqué sur le lien, sélectionnez **Exécuter** pour exécuter le package d’installation.
  
**Désactiver l'association automatique au client**: utilisez cette commande Windows PowerShell pour empêcher les nouveaux utilisateurs de rejoindre un client géré :
  
Pour désactiver l'association automatique au client des nouveaux utilisateurs :  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $false`
  
Pour activer l'association automatique au client des nouveaux utilisateurs :  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
> [!NOTE]
> Ce blocage empêche les nouveaux utilisateurs de votre organisation de s’inscrire à Power BI. Les utilisateurs qui s’inscrivent à Power BI avant de désactiver les nouvelles inscriptions pour votre organisation conservent toujours leurs licences. Consultez les [Comment faire supprimer Power BI pour les utilisateurs qui se sont déjà inscrits ?](#how-do-i-remove-power-bi-for-users-that-already-signed-up) pour obtenir des instructions sur la façon dont vous pouvez supprimer l’accès à Power BI pour les utilisateurs qui s’étaient déjà inscrits au service.
  
## <a name="how-can-i-allow-users-to-join-my-existing-tenant"></a>Comment autoriser les utilisateurs à rejoindre mon locataire existant ?

Pour autoriser les utilisateurs à rejoindre votre client, exécutez la commande inverse, comme décrit dans la question ci-dessus :  `Set-MsolCompanySettings -AllowEmailVerifiedUsers $true`
  
## <a name="how-do-i-verify-if-i-have-the-block-on-in-the-tenant"></a>Comment vérifier que le blocage est activé dans le locataire ?

Utilisez le script PowerShell suivant :  `Get-MsolCompanyInformation | fl allow*`
  
## <a name="how-can-i-prevent-my-existing-users-from-starting-to-use-power-bi"></a>Comment empêcher les utilisateurs existants d'utiliser Power BI ?

**Désactiver la distribution automatique de licences :** utilisez ce script Windows PowerShell pour désactiver la distribution automatique de licences pour les utilisateurs existants. Vous n’avez pas besoin de répéter ce processus si vous avez déjà désactivé la distribution automatique de licences avant (par exemple, Office 365 Éducation pour les étudiants, les enseignants et le personnel).
  
Pour désactiver la distribution automatique de licences pour les utilisateurs existants :  `Set-MsolCompanySettings -AllowAdHocSubscriptions $false`
  
Pour activer la distribution automatique de licences pour les utilisateurs existants :  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
> [!NOTE]
> L’indicateur *AllowAdHocSubscriptions* est utilisé pour contrôler plusieurs fonctionnalités utilisateur de votre organisation, notamment la possibilité pour les utilisateurs de s’inscrire au service Azure Rights Management. La modification de cet indicateur affecte toutes ces fonctionnalités.
  
## <a name="how-can-i-allow-my-existing-users-to-sign-up-for-power-bi"></a>Comment autoriser mes utilisateurs existants à s'inscrire à Power BI ?

Pour autoriser les utilisateurs existants à s'inscrire à Power BI, exécutez la commande inverse, comme décrit dans la question ci-dessus :  `Set-MsolCompanySettings -AllowAdHocSubscriptions $true`
  
## <a name="how-do-i-remove-power-bi-for-users-that-already-signed-up"></a>Comment supprimer Power BI pour les utilisateurs déjà inscrits ?

Si un utilisateur s’est inscrit à Power BI, mais que vous ne souhaitez plus qu’il ait accès à Power BI, vous pouvez supprimer la licence Power BI pour cet utilisateur.
  
::: moniker range="o365-worldwide"

1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834822" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

::: moniker range="o365-21vianet"

 1. Dans le Centre d’administration, accédez à la page **Utilisateurs** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=850628" target="_blank">Utilisateurs actifs</a>.

::: moniker-end

2. Recherchez l’utilisateur pour lequel vous souhaitez supprimer la licence, puis sélectionnez son nom.

3. Sous l’onglet **Licences et applications**, désactivez la case à cocher **Microsoft Power BI**.

4. Sélectionnez **Enregistrer les modifications**.

## <a name="how-do-i-know-when-new-users-have-joined-my-tenant"></a>Comment puis-je savoir si de nouveaux utilisateurs ont rejoint mon locataire ?

Les utilisateurs qui ont rejoint votre client dans le cadre de ce programme se voient attribuer une licence unique, que vous pouvez filtrer dans votre volet d'utilisateur actif dans le tableau de bord d'administration.
  
Pour créer cette nouvelle vue, dans le Centre d’administration, suivez les étapes de [création d’un affichage utilisateur personnalisé](../add-users/create-edit-or-delete-a-custom-user-view.md#create-a-custom-user-view). Sous **Licence de produit affectée**, sélectionnez **Microsoft Power BI**. Une fois la nouvelle vue créée, vous pourrez voir tous les utilisateurs de votre locataire qui se sont inscrits à ce programme.
  
## <a name="are-there-any-additional-things-i-should-be-prepared-for"></a>Quels sont les éventuels autres aspects auxquels je dois être préparé ?

Vous pouvez éventuellement faire face à une augmentation des demandes de réinitialisation de mot de passe. Pour plus d’informations sur ce processus, voir [Réinitialiser le mot de passe d’un utilisateur](../add-users/reset-passwords.md).
  
Vous pouvez supprimer un utilisateur de votre locataire via le processus standard dans le Centre d’administration. Cependant, si l'utilisateur a toujours une adresse de messagerie active de votre organisation, il pourra rejoindre le client, sauf si vous empêchez tous les utilisateurs de le faire.
  
## <a name="why-did-1-million-licenses-for-microsoft-power-bi-show-up-in-my-tenant"></a>Pourquoi 1 million de licences pour Microsoft Power BI s’affichent-ils dans mon locataire ?

En tant qu’organisation éligible, les utilisateurs de votre organisation peuvent utiliser microsoft service Power BI et ces licences représentent la capacité disponible pour les nouveaux utilisateurs Power BI dans votre locataire. Ces licences ne sont pas facturées. Si vous avez choisi d’autoriser les utilisateurs à s’inscrire à Power BI eux-mêmes, l’une de ces licences gratuites disponibles leur sera attribuée une fois le processus d’inscription terminé. Vous pouvez également choisir d’attribuer ces licences aux utilisateurs vous-même via le Centre d’administration.
  
## <a name="is-this-free-will-i-be-charged-for-these-licenses"></a>Est-ce gratuit ? Ces licences me seront-elles facturées ?

Ces licences s'appliquent à la version gratuite de Power BI. Si vous êtes intéressé par des fonctionnalités supplémentaires, jetez un coup d'œil à la version professionnelle de Power BI.
  
## <a name="why-1-million-licenses"></a>Pourquoi un million de licences ?

Nous avons choisi un nombre suffisamment important pour que la majorité des organisations disposent de licences suffisantes pour offrir cet avantage sans délai à leurs utilisateurs.
  
## <a name="what-if-i-need-more-than-1-million-licenses"></a>Comment faire pour bénéficier de plus d'un million de licences ?

Si vous prévoyez d'acquérir des licences supplémentaires, contactez votre représentant Microsoft.