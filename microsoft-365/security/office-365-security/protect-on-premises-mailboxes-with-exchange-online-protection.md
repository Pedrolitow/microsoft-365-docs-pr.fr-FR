---
title: Protéger les boîtes aux lettres locales avec Exchange Online Protection
f1.keywords:
- NOCSH
ms.author: tracyp
author: MSFTTracyP
manager: dansimp
ms.date: 6/1/2017
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- GEU150
- GMA150
- GPA150
- MET150
ms.assetid: c5e95951-da67-4ec7-92c5-982abd477e69
ms.collection:
- M365-security-compliance
description: Même si vous envisagez d’héberger une partie ou l’ensemble de vos boîtes aux lettres en local, vous pouvez toujours protéger les boîtes aux lettres à l’aide d’Exchange Online Protection (EOP). Pour configurer les connecteurs, vous devez disposer d'un compte d'administrateur global Office 365 ou d'administrateur d'entreprise Exchange (groupe de rôles Gestion de l'organisation). Pour plus d’informations sur la relation entre les autorisations Office 365 et les autorisations Exchange, consultez la rubrique attribution de rôles d’administrateur dans Office 365 géré par 21Vianet. Si toutes vos boîtes aux lettres Exchange sont en local, procédez comme suit pour configurer votre service EOP.
ms.openlocfilehash: 8ff2e28100a748e34b8f079292d937cc9b3857e8
ms.sourcegitcommit: fce0d5cad32ea60a08ff001b228223284710e2ed
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/21/2020
ms.locfileid: "42895286"
---
# <a name="protect-on-premises-mailboxes-with-exchange-online-protection"></a>Protéger les boîtes aux lettres locales avec Exchange Online Protection

> [!NOTE]
> Cet article s’applique uniquement à Office 365 géré par 21Vianet en Chine.

Même si vous envisagez d’héberger une partie ou l’ensemble de vos boîtes aux lettres en local, vous pouvez toujours protéger les boîtes aux lettres à l’aide d’Exchange Online Protection (EOP). Pour configurer les connecteurs, vous devez disposer d'un compte d'administrateur global Office 365 ou d'administrateur d'entreprise Exchange (groupe de rôles Gestion de l'organisation). Pour plus d’informations sur la relation entre les autorisations Office 365 et les autorisations Exchange, consultez la rubrique [attribution de rôles d’administrateur dans Office 365 géré par 21ViaNet](https://docs.microsoft.com/office365/admin/add-users/assign-admin-roles?&view=o365-21vianet). Si toutes vos boîtes aux lettres Exchange sont en local, procédez comme suit pour configurer votre service EOP.

## <a name="step-1-use-the-microsoft-365-admin-center-to-add-and-verify-your-domain"></a>Étape 1 : utiliser le centre d’administration Microsoft 365 pour ajouter et vérifier votre domaine

1. Dans le centre d’administration Microsoft 365, accédez à configuration pour ajouter votre domaine au service.

2. Suivez les étapes indiquées dans le portail pour ajouter les enregistrements DNS applicables à votre fournisseur d’hébergement DNS afin de vérifier la propriété du domaine.

> [!TIP]
> [Ajoutez votre domaine et vos utilisateurs à office 365 géré par 21ViaNet](https://docs.microsoft.com/office365/admin/setup/add-domain?&view=o365-21vianet) et [créez des enregistrements dns pour Office 365 lorsque vous gérez vos enregistrements DNS](https://docs.microsoft.com/office365/admin/services-in-china/create-dns-records-when-you-manage-your-dns-records?&view=o365-21vianet) sont des ressources utiles à référencer lorsque vous ajoutez votre domaine au service et configurez le DNS.

### <a name="step-2-add-recipients-and-configure-the-domain-type"></a>Étape 2 : ajouter des destinataires et configurer le type de domaine

Avant de configurer votre flux de messagerie vers et depuis le service EOP, nous vous recommandons d'ajouter vos destinataires au service. Il existe plusieurs méthodes pour mener à bien cette opération, comme indiqué dans [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md). Aussi, si vous souhaitez activer le blocage du périmètre basé sur l'annuaire (DBEB) afin d'appliquer la vérification du destinataire dans le service après avoir ajouté vos destinataires, vous devez définir votre type de domaine sur Faisant autorité. Pour plus d’informations sur DBEB, consultez la rubrique [use Directory based Edge Blocking to Reject messages sent to Invalid Recipients](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

## <a name="step-3-use-the-eac-to-set-up-mail-flow"></a>Étape 3 : Utiliser le CAE pour configurer le flux de messagerie

Créez des connecteurs dans le Centre d'administration Exchange (CAE) qui activent le flux de messagerie entre EOP et vos serveurs de messagerie locaux. Pour obtenir des instructions détaillées, consultez la rubrique [configure mail Flow using Connectors in Office 365](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

 Comment savoir si cette tâche a fonctionné ?

 Consultez [tester le flux de messagerie en validant vos connecteurs Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/test-mail-flow).

## <a name="step-4-allow-inbound-port-25-smtp-access"></a>Étape 4 : Autoriser l’accès SMTP entrant sur le port 25

Après avoir configuré les connecteurs, attendez 72 heures avant d’autoriser la propagation de vos mises à jour d’enregistrement DNS. De cette manière, limitez le trafic SMTP entrant-25 sur votre pare-feu ou vos serveurs de messagerie pour qu’ils acceptent uniquement les messages provenant des centres de distribution EOP, en particulier ceux des adresses IP indiquées au niveau [des URL et des plages d’adresses IP pour Office 365](https://docs.microsoft.com/office365/enterprise/managing-office-365-endpoints). Cela protège votre environnement local en limitant l'étendue des messages entrants. Si des paramètres définis sur votre serveur de messagerie contrôlent les adresses IP autorisées à se connecter pour le relais de messagerie, mettez-les à jour également.

> [!TIP]
> Configurez les paramètres du serveur SMTP en définissant l'expiration du délai de connexion sur 60 secondes. Ce paramétrage est acceptable dans la plupart des cas, et autorise un certain délai, par exemple, si le message envoyé contient une pièce jointe volumineuse.

## <a name="step-5-ensure-that-spam-is-routed-to-each-users-junk-email-folder"></a>Étape 5 : vérifier que le courrier indésirable est acheminé vers le dossier de courrier indésirable de chaque utilisateur

Pour vous assurer que le courrier indésirable est correctement routé vers le dossier Courrier indésirable de chaque utilisateur, vous pouvez effectuer quelques opérations de configuration. Les étapes sont fournies dans [configure standalone EOP pour envoyer du courrier indésirable dans le dossier courrier indésirable dans des environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md). Si vous ne souhaitez pas déplacer les messages vers le dossier Courrier indésirable de chaque utilisateur, vous pouvez choisir une autre action en modifiant vos stratégies de filtrage de contenu dans le Centre d'administration Exchange. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

## <a name="step-6-use-the-microsoft-365-admin-center-to-point-your-mx-record-to-eop"></a>Étape 6 : utiliser le centre d’administration Microsoft 365 pour faire pointer votre enregistrement MX vers EOP

Suivez les étapes de configuration de domaine Office 365 pour mettre à jour votre enregistrement MX pour votre domaine, de sorte que votre courrier entrant circule dans EOP. Pour plus d’informations, vous pouvez à nouveau référencer [créer des enregistrements DNS pour Office 365 lorsque vous gérez vos enregistrements DNS](https://docs.microsoft.com/office365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).

Comment savoir si cette tâche a fonctionné ?

 Consultez [tester le flux de messagerie en validant vos connecteurs Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/test-mail-flow).

À ce stade, vous avez vérifié la fourniture de service pour un connecteur local sortant correctement configuré et vous vous êtes assuré que votre enregistrement MX pointe vers EOP. Vous pouvez désormais exécuter les tests supplémentaires suivants afin de vérifier qu'un courrier électronique est bien remis par le service à votre environnement local :

- Dans l'Analyseur de connectivité à distance, cliquez sur l'onglet **Office 365**, puis exécutez le test **Courrier SMTP entrant** situé sous **Tests E-mail sur Internet**.

- Envoyez un message électronique à partir d'un compte de messagerie basé sur le web vers un destinataire de messagerie de votre organisation dont le domaine correspond au domaine ajouté au service. Vérifiez la remise du message à la boîte aux lettres locale à l'aide de Microsoft Outlook ou d'un autre client de messagerie.

- Si vous souhaitez effectuer un test de message sortant, vous pouvez envoyer un message électronique d'un utilisateur de votre organisation vers un compte de messagerie basé sur le web et confirmer sa réception.

## <a name="less-common-a-hybrid-setup-with-mailboxes-on-premises-and-in-the-cloud"></a>Moins courants : configuration hybride avec des boîtes aux lettres locales et dans le Cloud

Si vous disposez de boîtes aux lettres Exchange sur site et d’une ou de plusieurs boîtes aux lettres dans le Cloud dans Exchange Online, vous disposez d’une configuration *hybride* . Dans une configuration hybride, des fonctionnalités telles que le partage du calendrier de disponibilité et le routage du courrier fonctionnent ensemble dans vos environnements locaux et Cloud. Vous disposez peut-être d’une configuration hybride en place lorsque vous migrez des boîtes aux lettres vers Exchange Online. Un environnement hybride est configuré différemment de la protection autonome EOP.

Vous pouvez choisir un scénario hybride pour tirer parti de la messagerie en nuage pour la plupart de vos employés. Vous pouvez effectuer cette opération tout en hébergeant des boîtes aux lettres locales ; par exemple, pour votre service juridique.

Une configuration hybride peut être complexe, mais elle offre de nombreux avantages. Pour en savoir plus sur la configuration des scénarios hybrides avec Exchange, consultez la rubrique [déploiements hybrides Exchange Server](https://docs.microsoft.com/Exchange/exchange-hybrid).
