---
title: Configurer votre service EOP autonome
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
ms.date: ''
audience: ITPro
ms.topic: how-to
ms.service: O365-seccomp
ms.custom:
- seo-marvel-apr2020
localization_priority: Normal
ms.assetid: d74c6ddf-11b0-43ee-b298-8bb0340895f0
description: Les administrateurs peuvent apprendre à configurer Exchange Online Protection (EOP) autonome pour protéger les environnements de messagerie locaux.
ms.openlocfilehash: cf49cf4b0784731c23c0c36de44d3b0b2cb78dc8
ms.sourcegitcommit: e12fa502bc216f6083ef5666f693a04bb727d4df
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/20/2020
ms.locfileid: "46827820"
---
# <a name="set-up-your-standalone-eop-service"></a>Configurer votre service EOP autonome

Cette rubrique explique comment configurer Exchange Online Protection (EOP) en mode autonome. Si vous avez été redirigé depuis l'Assistant Domaines Office 365, revenez à l'Assistant Domaines Office 365 si vous ne souhaitez pas utiliser Exchange Online Protection. Si vous recherchez plus d'informations sur la configuration des connecteurs, consultez la rubrique [Configure mail flow using connectors in Office 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/use-connectors-to-configure-mail-flow).

> [!NOTE]
> Elle suppose que vous disposez de boîtes aux lettres locales et que vous voulez les protéger avec EOP (scénario dit « autonome »). Si vous voulez héberger toutes vos boîtes aux lettres dans le nuage avec Exchange Online, il n'est pas nécessaire de réaliser toutes les étapes décrites dans cette rubrique. Consultez la [comparaison des plans Exchange Online](https://products.office.com/exchange/compare-microsoft-exchange-online-plans) pour vous inscrire et acheter des boîtes aux lettres Cloud. Si vous voulez héberger certaines de vos boîtes aux lettres localement et d'autres dans le nuage, il s'agit d'un scénario hybride. Des paramètres de flux de messagerie plus avancés sont requis. [Déploiements hybrides Exchange Server](https://docs.microsoft.com/exchange/exchange-hybrid) explique le flux de messagerie hybride et comporte des liens vers des ressources qui expliquent comment le configurer.

## <a name="what-do-you-need-to-know-before-you-begin"></a>Ce qu'il faut savoir avant de commencer

- Durée d'exécution estimée de cette tâche : 1 heure

- Des autorisations doivent vous être attribuées avant de pouvoir exécuter ces procédures. Plus précisément, vous avez besoin du rôle domaines approuvés et distants, qui est affecté aux groupes de rôles MailFlowAdministrator et OrganizationManagement (administrateurs globaux) par défaut. Pour plus d’informations, consultez la rubrique [autorisations dans EOP autonome](feature-permissions-in-eop.md) et utiliser le centre d’administration Exchange pour [modifier la liste des membres dans les groupes de rôles](manage-admin-role-group-permissions-in-eop.md#use-the-eac-modify-the-list-of-members-in-role-groups).

- Si vous ne vous êtes pas inscrit à EOP, consultez la page [Exchange Online Protection](https://products.office.com/exchange/exchange-email-security-spam-protection), et choisissez d'acheter ou d'essayer le service.

- Pour plus d’informations sur les raccourcis clavier applicables aux procédures de cette rubrique, voir [raccourcis clavier pour le centre d’administration Exchange dans Exchange Online](https://docs.microsoft.com/Exchange/accessibility/keyboard-shortcuts-in-admin-center).

> [!TIP]
> Vous rencontrez des difficultés ? Demandez de l’aide dans le Forum [Exchange Online Protection](https://go.microsoft.com/fwlink/p/?linkId=285351) .

## <a name="step-1-use-the-microsoft-365-admin-center-to-add-and-verify-your-domain"></a>Étape 1 : utiliser le centre d’administration Microsoft 365 pour ajouter et vérifier votre domaine

1. Dans le [Centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/admin-overview/about-the-admin-center), accédez à **configuration** pour ajouter votre domaine au service.

2. Suivez les étapes pour ajouter les enregistrements DNS applicables à votre fournisseur d'hébergement DNS afin de vérifier l'appartenance du domaine.

> [!TIP]
> L' [Ajout d’un domaine à office 365 et la](https://docs.microsoft.com/microsoft-365/admin/setup/add-domain) création d' [enregistrements DNS auprès d’un fournisseur d’hébergement dns pour Office 365](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider) sont des ressources utiles à référencer lorsque vous ajoutez votre domaine au service et configurez le DNS.

## <a name="step-2-add-recipients-and-optionally-enable-dbeb"></a>Étape 2 : Ajouter des destinataires et éventuellement activer DBEB

Avant de configurer votre flux de messagerie vers et depuis le service EOP, nous vous recommandons d'ajouter vos destinataires au service. Il existe plusieurs méthodes pour mener à bien cette opération, comme indiqué dans [Gestion des utilisateurs de messagerie dans EOP](manage-mail-users-in-eop.md). Aussi, si vous souhaitez activer le blocage du périmètre basé sur l'annuaire (DBEB) afin d'appliquer la vérification du destinataire dans le service après avoir ajouté vos destinataires, vous devez définir votre type de domaine sur Faisant autorité. Pour plus d'informations sur le DBEB, consultez la rubrique [Use Directory Based Edge Blocking to Reject Messages Sent to Invalid Recipients](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-directory-based-edge-blocking).

## <a name="step-3-use-the-eac-to-set-up-mail-flow"></a>Étape 3 : Utiliser le CAE pour configurer le flux de messagerie

Créez des connecteurs dans le Centre d'administration Exchange (CAE) qui activent le flux de messagerie entre EOP et vos serveurs de messagerie locaux. Pour obtenir des instructions détaillées, reportez-vous [à configurer des connecteurs pour router les messages entre Microsoft 365 et vos propres serveurs de messagerie](https://docs.microsoft.com/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail).

### <a name="how-do-you-know-this-task-worked"></a>Comment savoir si cette tâche a fonctionné ?

Vérifiez le flux de messagerie entre le service et votre environnement. Pour plus d’informations, consultez [la rubrique Test du flux de messagerie en validant vos connecteurs Microsoft 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/test-mail-flow).

## <a name="step-4-allow-inbound-port-25-smtp-access"></a>Étape 4 : Autoriser l’accès SMTP entrant sur le port 25

Une fois que vous avez configuré les connecteurs, attendez 72 heures pour autoriser la propagation de vos mises à jour des enregistrements DNS. Ensuite, limitez le trafic SMTP entrant sur le port 25 au niveau du pare-feu ou des serveurs de messagerie de façon à accepter uniquement le courrier électronique en provenance des centres de données EOP, en particulier des adresses IP répertoriées dans [Adresses IP d'Exchange Online Protection](https://docs.microsoft.com/office365/enterprise/urls-and-ip-address-ranges). Cela protège votre environnement local en limitant l'étendue des messages entrants. Si des paramètres définis sur votre serveur de messagerie contrôlent les adresses IP autorisées à se connecter pour le relais de messagerie, mettez-les à jour également.

> [!TIP]
> Configurez les paramètres du serveur SMTP en définissant l'expiration du délai de connexion sur 60 secondes. Ce paramètre est acceptable pour la plupart des situations, ce qui permet un certain délai dans le cas d’un message envoyé avec une pièce jointe de grande taille, par exemple.

## <a name="step-5-ensure-that-spam-is-routed-to-each-users-junk-email-folder"></a>Étape 5 : vérifier que le courrier indésirable est acheminé vers le dossier de courrier indésirable de chaque utilisateur

Pour vous assurer que le courrier indésirable est correctement routé vers le dossier Courrier indésirable de chaque utilisateur, vous pouvez effectuer quelques opérations de configuration. Les étapes sont fournies dans [configure standalone EOP pour envoyer du courrier indésirable dans le dossier courrier indésirable dans des environnements hybrides](ensure-that-spam-is-routed-to-each-user-s-junk-email-folder.md).

Si vous ne souhaitez pas déplacer les messages vers le dossier de courrier indésirable de chaque utilisateur, vous pouvez choisir une autre action en modifiant vos stratégies anti-courrier indésirable. Si vous souhaitez en savoir plus, consultez l’article [Configurer les stratégies anti-courrier indésirable dans Office 365](configure-your-spam-filter-policies.md).

## <a name="step-6-use-the-microsoft-365-admin-center-to-point-your-mx-record-to-eop"></a>Étape 6 : utiliser le centre d’administration Microsoft 365 pour faire pointer votre enregistrement MX vers EOP

Suivez les étapes de configuration du domaine pour mettre à jour votre enregistrement MX pour votre domaine, de sorte que votre courrier entrant passe par EOP. Veillez à pointer directement votre enregistrement MX vers EOP plutôt que de faire relayer votre courrier électronique vers EOP par un service de filtrage tiers. Pour plus d'informations, vous pouvez de nouveau vous reporter à la rubrique [Créer des enregistrements DNS pour Office 365 lorsque vous gérez vos enregistrements DNS](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/create-dns-records-at-any-dns-hosting-provider).

> [!NOTE]
> Si vous devez faire pointer votre enregistrement MX vers un autre serveur ou service qui se trouve devant EOP, reportez-vous à la rubrique [filtrage amélioré pour les connecteurs dans Exchange Online](https://docs.microsoft.com/Exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors).

### <a name="how-do-you-know-this-task-worked"></a>Comment savoir si cette tâche a fonctionné ?

À ce stade, vous avez vérifié la fourniture de service pour un connecteur local sortant correctement configuré et vous vous êtes assuré que votre enregistrement MX pointe vers EOP. Vous pouvez désormais exécuter les tests supplémentaires suivants afin de vérifier qu'un courrier électronique est bien remis par le service à votre environnement local :

- Vérifiez le flux de messagerie entre le service et votre environnement. Pour plus d’informations, consultez [la rubrique Test du flux de messagerie en validant vos connecteurs Microsoft 365](https://docs.microsoft.com/exchange/mail-flow-best-practices/test-mail-flow).

- Envoyez un message électronique à partir d'un compte de messagerie basé sur le web vers un destinataire de messagerie de votre organisation dont le domaine correspond au domaine ajouté au service. Vérifiez la remise du message à la boîte aux lettres locale à l'aide de Microsoft Outlook ou d'un autre client de messagerie.

- Si vous souhaitez effectuer un test de message sortant, vous pouvez envoyer un message électronique d'un utilisateur de votre organisation vers un compte de messagerie basé sur le web et confirmer sa réception.

> [!TIP]
> Une fois votre configuration terminée, aucune étape supplémentaire n'est requise pour activer la suppression du courrier indésirable et des programmes malveillants par EOP. Ces opérations sont effectuées automatiquement. Toutefois, vous pouvez affiner vos paramètres en fonction des besoins de votre entreprise. Pour plus d’informations, consultez la rubrique [protection contre le courrier indésirable et les programmes malveillants dans Office 365](anti-spam-and-anti-malware-protection.md) et [configure usurpation d’identité](learn-about-spoof-intelligence.md). <br/><br/> Maintenant que votre service est en cours d’exécution, nous vous recommandons de lire les [meilleures pratiques pour la configuration d’EOP](best-practices-for-configuring-eop.md), qui décrit les paramètres recommandés et les éléments à prendre en compte après avoir configuré EOP.
