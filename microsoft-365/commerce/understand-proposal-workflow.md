---
title: Comprendre le flux de travail de la proposition
f1.keywords:
- CSH
author: cmcatee-MSFT
ms.author: cmcatee
manager: scotv
ms.reviewer: presharm, jmueller
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier1
- scotvorg
- M365-subscription-management
- Adm_O365
ms.custom:
- commerce_purchase
- AdminSurgePortfolio
search.appverid: MET150
description: Découvrez les propositions pour vous aider à acheter des produits et services Microsoft.
ROBOTS: NOINDEX
ms.date: 07/11/2022
ms.openlocfilehash: 154691dea57c7ee95583f9a8903278e012e7d9d6
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68733179"
---
# <a name="understand-the-microsoft-proposal-workflow"></a>Comprendre le flux de travail de la proposition Microsoft

Une proposition est une offre officielle de Microsoft pour que votre organisation achète des produits et services Microsoft. Les propositions représentent des commandes importantes que le service d’approvisionnement ou le service informatique de votre organisation passent auprès de Microsoft.

Avant le début du flux de travail de la proposition, votre service approvisionnement travaille directement avec un représentant Microsoft désigné pour déterminer les produits et services spécifiques dont votre organisation a besoin. Ensuite, votre représentant Microsoft rédige une proposition et envoie à votre service d’approvisionnement un e-mail avec un lien pour accepter la proposition dans le portail de la Place de marché Azure. Le site contient la proposition préparée spécifiquement pour vous et votre organisation.

Une fois que vous avez suivi le lien et que vous vous êtes connecté au site de proposition, vous pouvez démarrer le processus de révision de la proposition. Une fois que vous avez terminé l’examen et l’extraction de la proposition, vous recevez une facture pour les produits achetés conformément au plan de facturation que vous avez sélectionné. Pour savoir comment la facturation fonctionne pour les propositions, consultez [Comprendre la facturation](#understand-invoicing) ci-dessous.

## <a name="prerequisites-for-buying-items-with-a-proposal"></a>Conditions préalables pour l’achat d’articles avec une proposition

Avant de pouvoir acheter des articles pour une proposition, vous devez disposer d’un compte de facturation et d’un contrat avec Microsoft.

### <a name="billing-account"></a>Compte de facturation

Vous utilisez un compte de facturation pour gérer vos paramètres de compte, factures, profils de facturation et produits et services. Si vous n’avez pas encore de compte de facturation, votre représentant Microsoft en crée un pour vous. Sinon, ils utilisent un compte de facturation existant pour votre organisation, à condition que vous ayez l’autorisation d’utiliser ce compte de facturation.

Les autorisations de compte de facturation sont gérées par le propriétaire du compte de facturation. Les administrateurs généraux peuvent s’attribuer le rôle de propriétaire du compte de facturation, puis rendre d’autres personnes propriétaires de compte de facturation.

Pour plus d’informations sur les comptes de facturation, consultez [Gérer les comptes de facturation](manage-billing-accounts.md).

### <a name="microsoft-customer-agreement"></a>Contrat client Microsoft

Le Contrat client Microsoft (MCA) permet à une organisation d’acheter des produits et services Microsoft. Pour plus d’informations, consultez [Contrat client Microsoft](https://www.microsoft.com/Licensing/how-to-buy/microsoft-customer-agreement).

## <a name="permissions-needed-to-sign-an-agreement-or-pay-for-items"></a>Autorisations nécessaires pour signer un contrat ou payer des articles

Vous devez être propriétaire du compte de facturation ou contributeur de compte de facturation pour signer un contrat ou acheter des produits et services. Si vous êtes administrateur général mais que vous n’avez pas l’un de ces rôles, vous pouvez vous attribuer les rôles. Si vous n’êtes pas administrateur général, demandez à votre administrateur général ou au propriétaire du compte de facturation de vous attribuer l’un des rôles.

Les rôles propriétaire du compte de facturation et contributeur de compte de facturation sont attribués à l’aide de l’une des méthodes suivantes.

### <a name="assign-roles-in-the-microsoft-365-admin-center"></a>Attribuer des rôles dans le Centre d'administration Microsoft 365

1. Dans la Centre d'administration Microsoft 365, accédez à la page **Comptes de** > <a href="https://go.microsoft.com/fwlink/p/?linkid=2084771" target="_blank">facturation</a>.
2. Dans la page **Comptes de facturation** , dans la section **Rôles de compte de facturation** , sélectionnez **Attribuer des rôles**.
3. Dans le volet **Attribuer des rôles** , recherchez le nom de la personne à laquelle vous souhaitez attribuer un rôle.
4. Cochez la case correspondant au nom de rôle que vous souhaitez que la personne ait, puis sélectionnez **Attribuer**.

### <a name="assign-roles-in-the-azure-portal"></a>Attribuer des rôles dans le Portail Azure

1. Dans le Portail Azure, accédez à la page <a href="https://portal.azure.com/#blade/Microsoft_Azure_GTM/ModernBillingMenuBlade/Overview" target="_blank">Contrôle d’accès (IAM).</a>
2. Dans la page **Contrôle d’accès (IAM),** sélectionnez **Ajouter**.
3. Dans le volet **Ajouter une autorisation** , sélectionnez le **rôle** à attribuer à l’utilisateur.
4. Sélectionnez l’utilisateur, puis **enregistrer**.

Pour plus d’informations sur les rôles de compte de facturation, consultez [Comprendre l’accès aux comptes de facturation](manage-billing-accounts.md#understand-access-to-billing-accounts).

S’il s’agit d’un nouveau compte de facturation et que personne n’a accepté de contrat, vous devenez automatiquement le propriétaire du compte de facturation, à condition que vous :

- La personne nommée dans la proposition ou
- Vous êtes déjà [administrateur général Azure Active Directory](/azure/active-directory/roles/permissions-reference#global-administrator) pour votre organisation

## <a name="what-is-the-overall-workflow"></a>Quel est le workflow global ?

Le flux de travail de proposition global se présente comme suit :

- Votre représentant Microsoft crée une proposition et vous envoie un lien dans un e-mail.
- Vous utilisez le lien pour accéder à la page de connexion de la proposition.
- Vous passez en revue les informations de votre organisation.
- Vous passez en revue la proposition, acceptez le MCA si nécessaire et terminez le processus de validation.
  > [!IMPORTANT]
  > Vous devez avoir l’autorité nécessaire pour signer un contrat MCA au nom de votre organisation. Si vous n’avez pas cette autorité, une personne qui le fait doit effectuer cette étape.
- Une fois l’extraction terminée, vous recevez d’autres liens pour configurer vos produits et services.

## <a name="proposal-terms"></a>Conditions de la proposition

Le tableau suivant contient les termes et définitions qui apparaissent dans votre proposition et sur le site de la proposition.

| Terme | Définition |
|---|---|
| Compte de facturation | Un compte utilisé pour gérer les paramètres, les factures, les modes de paiement et les produits de votre compte. |
| Profil de facturation | Informations sur votre organisation qui vous permettent de personnaliser les éléments inclus dans votre facture et la façon dont vous payez vos factures. Le profil de facturation inclut le nom du compte de facturation, les modes de paiement utilisés pour le profil de facturation spécifique, les informations de contact, les paramètres de facture et les autorisations qui vous permettent de modifier le profil de facturation, de payer les factures et d’acheter des produits et services. |
| Accords existants | Tout contrat que votre organisation a déjà conclu avec Microsoft. Les contrats peuvent inclure, sans s’y limiter, un Accord Entreprise, un Contrat de services de produit & Microsoft ou Contrat client Microsoft. |
| Contrat client Microsoft (MCA) | Un contrat qui décrit les conditions générales du compte détenu par votre organisation avec Microsoft. |
| Représentant Microsoft | Un représentant Microsoft autorisé qui prépare une proposition pour vous et votre organisation. |
| Organisation | Une entité juridique qui utilise des produits, technologies ou services Microsoft. |
| Préparé par | Adresse e-mail du représentant Microsoft qui a préparé la proposition. |
| Conditions supplémentaires | Modifications apportées au MCA qui contiennent des termes spécifiques à votre organisation. Pour accepter des conditions supplémentaires, vous devez utiliser DocuSign pour enregistrer une signature électronique. |

## <a name="step-1-review-organization-information"></a>Étape 1 : Passer en revue les informations de l’organisation

Une fois connecté, la première chose à faire est de passer en revue les informations de votre organisation.

### <a name="your-organization"></a>Votre organisation

La section **Votre organisation** affiche le compte de facturation qui lui est associé. Les informations de compte de facturation sont extraites d’un compte de facturation existant ou créées pour vous par le représentant Microsoft. Si votre organisation est une filiale d’une autre organisation, vous voyez également une section **Organisation responsable** avec le nom et l’adresse de cette organisation.

Si cette commande est la première fois que votre organisation établit une relation commerciale avec Microsoft et que vous n’avez pas encore signé de contrat MCA, si les informations sous **Votre organisation** ou **organisation responsable** sont incorrectes, contactez le représentant pour apporter des modifications pour vous. Une fois que vous avez accepté un contrat MCA, vous pouvez consulter et modifier l’adresse et les informations de contact de votre organisation sur la page [Comptes de facturation](https://go.microsoft.com/fwlink/p/?linkid=2084771) dans le Centre d'administration Microsoft 365. Si le nom de votre organisation change, ouvrez une demande de support pour la mettre à jour. [Découvrez comment ouvrir une demande de support](../admin/get-help-support.md).

### <a name="your-information"></a>Vos informations

Si vous êtes un nouveau client, entrez votre nom, votre adresse e-mail et votre numéro de téléphone sous **Vos informations**, puis sélectionnez **Enregistrer**. Si vous êtes un client existant, vérifiez que vos informations sont correctes. Pour apporter des corrections, sélectionnez **Modifier**, apportez les modifications nécessaires, puis **sélectionnez Enregistrer**.

Lorsque vous êtes prêt, sélectionnez **Continuer** pour passer à l’étape suivante.

## <a name="step-2-review-proposal"></a>Étape 2 : Examiner la proposition

La proposition contient les détails des éléments que vous avez discutés avec votre représentant Microsoft. Vous pouvez transférer l’e-mail avec le lien de proposition pour le partager avec d’autres parties prenantes de votre organisation. Toute autre personne qui utilise le lien a une vue en lecture seule de la proposition.

Si vous souhaitez apporter des modifications à la proposition après examen, contactez votre représentant Microsoft.

### <a name="proposal-contents"></a>Contenu de la proposition

La proposition contient les informations suivantes :

| Section | Description |
|---|---|
| Nom de l’organisation | Nom de l’organisation pour laquelle la proposition a été préparée. |
| Valide jusqu’à la date | Date à laquelle l’offre de proposition expire. Si vous manquez cette date d’expiration, contactez votre représentant Microsoft pour lui faire savoir que la proposition vous intéresse toujours. |
| Devise | Devise utilisée pour calculer le coût des éléments de la proposition. |
| Préparé pour | Le nom du compte de facturation, l’adresse, l’adresse e-mail du contact et le numéro de téléphone de la personne qui a demandé la proposition. |
| Préparé par | Adresse e-mail du représentant Microsoft qui a préparé la proposition. |
| Résumé | Affiche le sous-total associé à la proposition. Si nécessaire, il affichera également le taux de change (FX) utilisé pour calculer les coûts. |
| Éléments de ligne de la proposition | Cette section contient la quantité, le prix unitaire et le sous-total de tous les éléments inclus dans la proposition. |
| Étape suivante | Cette section indique l’action nécessaire que vous devez effectuer. |

Pour signer un MCA, sélectionnez le bouton sous **Étape suivante**. Si vous devez signer des conditions supplémentaires, un lien vous dirige vers le site DocuSign, où vous suivez les étapes pour signer le document.

Une fois que vous avez signé les contrats ou conditions supplémentaires nécessaires, sélectionnez **Accéder à la validation**.

## <a name="step-3-checkout"></a>Étape 3 : Extraction

La page d’extraction contient les sections suivantes :

### <a name="sold-to"></a>Vendu à

Cette section présente le compte de facturation utilisé pour la proposition. Si vous avez besoin de modifier des informations, sélectionnez le lien **Modifier** . Vous pouvez également utiliser le lien **Modifier** pour ajouter l’ID fiscal de votre organisation. L’ID de taxe doit être lié au pays répertorié dans la section **Vendu à** . Si vous disposez d’une exonération fiscale, vous devez ouvrir un ticket de support pour demander le statut d’exonération fiscale.

Pour en savoir plus sur les ID de taxe et sur la façon de demander le statut d’exonération fiscale, consultez [Informations fiscales Microsoft 365](billing-and-payments/tax-information.md).

### <a name="billed-to"></a>Facturé à

Cette section présente le profil de facturation utilisé pour déterminer quels éléments sont inclus sur votre facture et comment vous payez vos factures. Chaque cycle de facturation, vous recevez une facture distincte pour chaque profil de facturation. Vous payez les factures à l’aide d’un chèque ou d’un virement bancaire, ou d’un prépaiement Azure. Si vous n’avez pas encore de profil de facturation, votre représentant Microsoft en crée un pour vous. Lors de l’extraction, vous pouvez sélectionner un autre profil de facturation, le cas échéant, modifier le nom du profil de facturation ou ajouter un P.O. Nombre. Vous pouvez également créer un profil de facturation.

Pour plus d’informations sur les profils de facturation, consultez [Gérer les profils de facturation](billing-and-payments/manage-billing-profiles.md).

### <a name="proposal-items-in-this-order"></a>Éléments de proposition dans cet ordre

Cette section présente la liste de tous les éléments inclus dans la proposition, qui peuvent inclure une ou plusieurs des catégories suivantes :

- **Conditions supplémentaires** Liste des modifications apportées au MCA qui contiennent les termes de votre organisation. Par exemple, cette liste peut inclure des termes HIPAA ou RGPD.
- **Acheter maintenant** Liste des articles que vous payez lors de la validation à la fin du flux de travail d’acceptation de la proposition.
- **Remises (appliquées aux frais futurs)** Liste des remises que vous recevez dans le cadre de la proposition.
- **Inclus** Liste des articles inclus dans le cadre du package de proposition sans frais supplémentaires. Certains de ces éléments peuvent avoir un coût associé à l’avenir.

> [!NOTE]
> Votre proposition peut inclure des abonnements avec une date de début future. Pour plus d’informations, consultez [Comprendre la facturation pour les dates de début futures](billing-and-payments/future-start-date.md).

### <a name="summary"></a>Résumé

Cette section indique le nombre d’articles payés, le sous-total, les taxes estimées et le montant total de la commande.

Pour passer la commande, sélectionnez **Passer une commande** ou **Accepter la commande du contrat&amp;**.

Après avoir passé la commande, vous recevez une confirmation avec les étapes suivantes à suivre. Si vous avez acheté un plan Azure, l’étape suivante consiste à configurer votre compte de facturation dans le Portail Azure.

## <a name="step-4-set-up-your-new-billing-account-azure-customers-only"></a>Étape 4 : Configurer votre nouveau compte de facturation (clients Azure uniquement)

Si vous êtes un nouveau client et que vous avez acheté des produits Azure dans le cadre de la proposition, l’étape suivante consiste à configurer votre nouveau compte de facturation. Pour savoir comment procéder, consultez [Configurer votre compte de facturation pour un Contrat client Microsoft](/azure/cost-management-billing/manage/mca-setup-account).

Si vous êtes un client Azure existant avec un Accord Entreprise et que vous signez un contrat MCA pour la première fois, l’étape suivante consiste à découvrir les modifications entre les contrats et à effectuer des tâches avec votre nouveau compte de facturation. Pour plus d’informations, consultez [Effectuer Accord Entreprise tâches dans votre compte de facturation pour un Contrat client Microsoft](/azure/cost-management-billing/manage/mca-enterprise-operations).

## <a name="understand-invoicing"></a>Comprendre la facturation

Une fois que vous avez vérifié et terminé votre commande, une facture initiale est envoyée dans les 24 à 48 heures. Après cela, vous recevez des factures environ le cinquième de chaque mois. La facture mensuelle contient les frais du mois précédent. Si vous avez des crédits pour votre compte, ils sont déduits des crédits monétaires de votre profil de facturation et appliqués au solde de votre facture. Le solde restant après l’application des crédits est le solde dû. Vous avez 30 jours à compter de la date de facturation pour payer la facture.

Les instructions de paiement pour l’envoi de chèques ou de virements bancaires sont incluses dans la copie PDF de votre facture. Pour afficher ou télécharger votre facture, consultez [Afficher votre facture.](billing-and-payments/view-your-bill-or-invoice.md)
