---
title: Protéger les boîtes aux lettres locales en Chine avec EOP autonome
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
localization_priority: Normal
search.appverid:
- GEU150
- GMA150
- GPA150
- MET150
ms.assetid: c5e95951-da67-4ec7-92c5-982abd477e69
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs en Chine qui utilisent Office 365 géré par 21Vianet peuvent apprendre à utiliser Exchange Online Protection (EOP) autonome pour protéger leurs boîtes aux lettres sur site.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 4258d64721fc2042297bb15eaeecafa90dcf4bc1
ms.sourcegitcommit: 27b2b2e5c41934b918cac2c171556c45e36661bf
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/19/2021
ms.locfileid: "50929287"
---
# <a name="protect-on-premises-mailboxes-in-china-with-standalone-eop"></a>Protéger les boîtes aux lettres locales en Chine avec EOP autonome

[!INCLUDE [Microsoft 365 Defender rebranding](../includes/microsoft-defender-for-office.md)]


> [!NOTE]
> Cet article s’applique uniquement à Office 365 géré par 21Vianet en Chine.

Même si vous prévoyez d’héberger une partie ou la plupart de vos boîtes aux lettres en local, vous pouvez toujours protéger les boîtes aux lettres avec Exchange Online Protection (EOP). Pour configurer des connecteurs, votre compte doit être un administrateur général ou un administrateur d’entreprise Exchange (groupe de rôles Gestion de l’organisation). Pour plus d’informations sur la relation entre les autorisations Office 365 et les autorisations Exchange, voir Attribuer des rôles d’administrateur dans [Office 365 géré par 21Vianet.](../../admin/add-users/assign-admin-roles.md?preserve-view=true&view=o365-21vianet) Si toutes vos boîtes aux lettres Exchange sont en local, suivez ces étapes pour configurer votre service EOP.

## <a name="step-1-use-the-microsoft-365-admin-center-to-add-and-verify-your-domain"></a>Étape 1 : Utiliser le Centre d’administration Microsoft 365 pour ajouter et vérifier votre domaine

1. Dans le Centre d’administration Microsoft 365, accédez au programme d’installation pour ajouter votre domaine au service.

2. Suivez les étapes du portail pour ajouter les enregistrements DNS applicables à votre fournisseur d’hébergement DNS afin de vérifier la propriété du domaine.

> [!TIP]
> Ajouter votre domaine et vos utilisateurs à Office 365 géré par [21Vianet](../../admin/setup/add-domain.md?preserve-view=true&view=o365-21vianet) et créer des enregistrements [DNS pour Office 365](../../admin/services-in-china/create-dns-records-when-you-manage-your-dns-records.md?preserve-view=true&view=o365-21vianet) lorsque vous gérez vos enregistrements DNS sont des ressources utiles à référencer lorsque vous ajoutez votre domaine au service et configurez DNS.

### <a name="step-2-add-recipients-and-configure-the-domain-type"></a>Étape 2 : Ajouter des destinataires et configurer le type de domaine

Avant de configurer votre flux de messagerie vers et depuis le service EOP, nous vous recommandons d'ajouter vos destinataires au service. Il existe plusieurs méthodes pour mener à bien cette opération, comme indiqué dans [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md). Aussi, si vous souhaitez activer le blocage du périmètre basé sur l'annuaire (DBEB) afin d'appliquer la vérification du destinataire dans le service après avoir ajouté vos destinataires, vous devez définir votre type de domaine sur Faisant autorité. Pour plus d’informations sur DBEB, voir Utiliser le blocage du périphérie basé sur l’annuaire pour rejeter les [messages envoyés à des destinataires non valides.](/exchange/mail-flow-best-practices/use-directory-based-edge-blocking)

## <a name="step-3-use-the-eac-to-set-up-mail-flow"></a>Étape 3 : Utiliser le CAE pour configurer le flux de messagerie

Créez des connecteurs dans le Centre d'administration Exchange (CAE) qui activent le flux de messagerie entre EOP et vos serveurs de messagerie locaux. Pour obtenir des instructions détaillées, voir Configurer le flux [de messagerie à l’aide de connecteurs dans Office 365.](/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow)

 Comment savoir si cette tâche a fonctionné ?

 Voir [Flux de messagerie test en validant vos connecteurs Office 365.](/exchange/mail-flow-best-practices/test-mail-flow)

## <a name="step-4-allow-inbound-port-25-smtp-access"></a>Étape 4 : Autoriser l’accès SMTP entrant sur le port 25

Après avoir configuré les connecteurs, attendez 72 heures avant d’autoriser la propagation de vos mises à jour d’enregistrement DNS. Ensuite, limitez le trafic SMTP du port 25 entrant sur votre pare-feu ou vos serveurs de messagerie pour qu’il accepte uniquement les messages provenant des centres de données EOP, en particulier à partir des adresses IP répertoriées dans les URL et les plages d’adresses IP pour [Office 365.](../../enterprise/managing-office-365-endpoints.md) Cela protège votre environnement local en limitant l'étendue des messages entrants. Si des paramètres définis sur votre serveur de messagerie contrôlent les adresses IP autorisées à se connecter pour le relais de messagerie, mettez-les à jour également.

> [!TIP]
> Configurez les paramètres du serveur SMTP en définissant l'expiration du délai de connexion sur 60 secondes. Ce paramétrage est acceptable dans la plupart des cas, et autorise un certain délai, par exemple, si le message envoyé contient une pièce jointe volumineuse.

## <a name="step-5-ensure-that-spam-is-routed-to-each-users-junk-email-folder"></a>Étape 5 : s’assurer que le courrier indésirable est acheminé vers le dossier Courrier indésirable de chaque utilisateur

Pour vous assurer que le courrier indésirable est correctement routé vers le dossier Courrier indésirable de chaque utilisateur, vous pouvez effectuer quelques opérations de configuration. Les étapes sont fournies dans [Configure standalone EOP to deliver spam to the Junk Email folder in hybrid environments](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md). Si vous ne souhaitez pas déplacer des messages vers le dossier Courrier indésirable de chaque utilisateur, vous pouvez choisir une autre action en éditant vos stratégies anti-courrier indésirable (également appelées stratégies de filtrage de contenu). Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

## <a name="step-6-use-the-microsoft-365-admin-center-to-point-your-mx-record-to-eop"></a>Étape 6 : Utiliser le Centre d’administration Microsoft 365 pour faire pointer votre enregistrement MX vers EOP

Suivez les étapes de configuration de domaine Office 365 pour mettre à jour votre enregistrement MX pour votre domaine, de sorte que votre courrier entrant circule dans EOP. Pour plus d’informations, vous pouvez de nouveau référencer Créer des enregistrements [DNS pour Office 365](../../admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md?preserve-view=true&view=o365-21vianet)lorsque vous gérez vos enregistrements DNS.

Comment savoir si cette tâche a fonctionné ?

 Voir [Flux de messagerie test en validant vos connecteurs Office 365.](/exchange/mail-flow-best-practices/test-mail-flow)

À ce stade, vous avez vérifié la fourniture de service pour un connecteur local sortant correctement configuré et vous vous êtes assuré que votre enregistrement MX pointe vers EOP. Vous pouvez désormais exécuter les tests supplémentaires suivants afin de vérifier qu'un courrier électronique est bien remis par le service à votre environnement local :

- Dans l'Analyseur de connectivité à distance, cliquez sur l'onglet **Office 365**, puis exécutez le test **Courrier SMTP entrant** situé sous **Tests E-mail sur Internet**.

- Envoyez un message électronique à partir d'un compte de messagerie basé sur le web vers un destinataire de messagerie de votre organisation dont le domaine correspond au domaine ajouté au service. Vérifiez la remise du message à la boîte aux lettres locale à l'aide de Microsoft Outlook ou d'un autre client de messagerie.

- Si vous souhaitez effectuer un test de message sortant, vous pouvez envoyer un message électronique d'un utilisateur de votre organisation vers un compte de messagerie basé sur le web et confirmer sa réception.

## <a name="less-common-a-hybrid-setup-with-mailboxes-on-premises-and-in-the-cloud"></a>Moins courant : configuration hybride avec des boîtes aux lettres en local et dans le cloud

Si vous avez des boîtes aux lettres Exchange en local et une ou plusieurs boîtes aux lettres dans le cloud dans Exchange Online, vous avez une *configuration* hybride. Dans une configuration hybride, des fonctionnalités telles que le partage de calendrier de libre/occupé et le routage du courrier fonctionnent ensemble dans vos environnements locaux et cloud. Vous pouvez avoir une configuration hybride en place pendant la transition des boîtes aux lettres vers Exchange Online. Un environnement hybride est installé différemment de la protection autonome EOP.

Vous pouvez choisir un scénario hybride pour tirer parti de la messagerie en nuage pour la plupart de vos employés. Vous pouvez le faire tout en hébergeant certaines boîtes aux lettres en local . par exemple, pour votre service juridique.

Une configuration hybride peut être complexe, mais elle présente de nombreux avantages. Pour en savoir plus sur la configuration de scénarios hybrides avec Exchange, [voir Exchange Server déploiements hybrides.](/Exchange/exchange-hybrid)