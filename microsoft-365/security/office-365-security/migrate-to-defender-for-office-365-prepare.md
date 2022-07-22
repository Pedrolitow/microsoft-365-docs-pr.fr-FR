---
title: 'Migrer vers Microsoft Defender pour Office 365 phase 1 : Préparer'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365solution-mdo-migration
ms.custom: migrationguides
description: Étapes préalables à la migration d’un service ou d’un appareil de protection tiers vers Microsoft Defender pour Office 365 protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: 7134d1e306de99b3af70a934ec9e9880ea98d268
ms.sourcegitcommit: 00948161a72d8cea8c2baba873743fc4a0e19f90
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/22/2022
ms.locfileid: "66969833"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-1-prepare"></a>Migrer vers Microsoft Defender pour Office 365 - Phase 1 : Préparer

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

<br>

|![Phase 1 : Préparer.](../../media/phase-diagrams/prepare.png) <br> Phase 1 : préparation|[![Phase 2 : configuration](../../media/phase-diagrams/setup.png#lightbox)](migrate-to-defender-for-office-365-setup.md) <br> [Phase 2 : configuration](migrate-to-defender-for-office-365-setup.md)|[![Phase 3 : intégration](../../media/phase-diagrams/onboard.png#lightbox)](migrate-to-defender-for-office-365-onboard.md) <br> [Phase 3 : intégration](migrate-to-defender-for-office-365-onboard.md)|
|---|---|---|
|*Vous êtes là !*|||

Bienvenue dans **la phase 1 : Préparez** votre **[migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process)** ! Cette phase de migration comprend les étapes suivantes. Vous devez d’abord inventorier les paramètres de votre service de protection existant avant d’apporter des modifications. Sinon, vous pouvez effectuer les étapes restantes dans n’importe quel ordre :

1. [Inventaire des paramètres de votre service de protection existant](#inventory-the-settings-at-your-existing-protection-service)
2. [Vérifier votre configuration de protection existante dans Microsoft 365](#check-your-existing-protection-configuration-in-microsoft-365)
3. [Vérifier la configuration de votre routage de messagerie](#check-your-mail-routing-configuration)
4. [Déplacer des fonctionnalités qui modifient des messages dans Microsoft 365](#move-features-that-modify-messages-into-microsoft-365)
5. [Définir le courrier indésirable et les expériences utilisateur en bloc](#define-spam-and-bulk-user-experiences)
6. [Identifier et désigner des comptes prioritaires](#identify-and-designate-priority-accounts)

## <a name="inventory-the-settings-at-your-existing-protection-service"></a>Inventaire des paramètres de votre service de protection existant

Un inventaire complet des paramètres, règles, exceptions, etc. de votre service de protection existant est une bonne idée, car vous n’aurez probablement pas accès aux informations après avoir annulé votre abonnement.

**Toutefois, il est très important de ne pas recréer automatiquement ou arbitrairement toutes vos personnalisations existantes dans Defender pour Office 365.** Au mieux, vous pouvez introduire des paramètres qui ne sont plus obligatoires, pertinents ou fonctionnels. Pire encore, certaines de vos personnalisations précédentes peuvent créer des problèmes de sécurité dans Defender pour Office 365.

Vos tests et votre observation des fonctionnalités natives et du comportement de Defender pour Office 365 détermineront en fin de compte les remplacements et les paramètres dont vous avez besoin. Vous pouvez trouver utile de classer les paramètres de votre service de protection existant dans les catégories suivantes :

- **Filtrage de connexion ou de contenu** : vous constaterez probablement que vous n’avez pas besoin de la plupart de ces personnalisations dans Defender pour Office 365.
- **Routage d’entreprise** : la majorité des personnalisations que vous devez recréer entreront probablement dans cette catégorie. Par exemple, vous pouvez recréer ces paramètres dans Microsoft 365 en tant que règles de flux de messagerie Exchange (également appelées règles de transport), connecteurs et exceptions à l’usurpation d’identité.

Au lieu de déplacer les anciens paramètres à l’aveugle dans Microsoft 365, nous vous recommandons une approche en cascade qui implique une phase pilote avec un nombre croissant d’utilisateurs et un réglage basé sur l’observation en fonction de l’équilibrage des considérations de sécurité avec les besoins de l’entreprise.

## <a name="check-your-existing-protection-configuration-in-microsoft-365"></a>Vérifier votre configuration de protection existante dans Microsoft 365

Comme nous l’avons indiqué précédemment, il est impossible de désactiver complètement toutes les fonctionnalités de protection pour les messages remis dans Microsoft 365, même lorsque vous utilisez un service de protection tiers. Par conséquent, il n’est pas rare qu’une organisation Microsoft 365 ait au moins certaines fonctionnalités de protection par e-mail configurées. Par exemple :

- Dans le passé, vous n’utilisiez pas le service de protection tiers avec Microsoft 365. Vous avez peut-être utilisé et configuré certaines fonctionnalités de protection dans Microsoft 365 qui sont actuellement ignorées. Toutefois, ces paramètres peuvent prendre effet lorsque vous « activez la numérotation » pour activer les fonctionnalités de protection dans Microsoft 365.
- Vous pouvez avoir des mesures d’adaptation dans la protection Microsoft 365 pour les faux positifs (bon courrier marqué comme mauvais) ou les faux négatifs (courrier incorrect autorisé) qui l’ont fait par le biais de votre service de protection existant.

Passez en revue vos fonctionnalités de protection existantes dans Microsoft 365 et envisagez de supprimer ou de simplifier les paramètres qui ne sont plus nécessaires. Un paramètre de règle ou de stratégie requis il y a des années pourrait mettre l’organisation en danger et créer des lacunes involontaires en matière de protection.

## <a name="check-your-mail-routing-configuration"></a>Vérifier la configuration de votre routage de messagerie

- Si vous utilisez une sorte de routage complexe (par exemple, [le transport de courrier centralisé](/exchange/transport-options)), vous devez envisager de simplifier votre routage et de le documenter minutieusement. Les tronçons externes, en particulier une fois que Microsoft 365 a déjà reçu le message, peuvent compliquer la configuration et la résolution des problèmes.

- Le flux de courrier sortant et de relais n’est pas inclus dans cet article. Toutefois, sachez que vous devrez peut-être effectuer une ou plusieurs des étapes suivantes :
  - Vérifiez que tous les domaines que vous utilisez pour envoyer des e-mails ont les enregistrements SPF appropriés. Pour plus d’informations, consultez [Configurer SPF pour prévenir l’usurpation d’identité](set-up-spf-in-office-365-to-help-prevent-spoofing.md).
  - Nous vous recommandons vivement de configurer la connexion DKIM dans Microsoft 365. Pour plus d’informations, consultez [Utiliser DKIM pour valider les e-mails sortants](use-dkim-to-validate-outbound-email.md).
  - Si vous ne routagez pas le courrier directement à partir de Microsoft 365, vous devez modifier ce routage en supprimant ou en modifiant le connecteur sortant.

- L’utilisation de Microsoft 365 pour relayer des messages électroniques à partir de vos serveurs de messagerie locaux peut être un projet complexe en soi. Un exemple simple est un petit nombre d’applications ou d’appareils qui envoient la plupart de leurs messages à des destinataires internes et ne sont pas utilisés pour les envois en masse. Pour plus [d’informations, consultez ce guide](/exchange/mail-flow-best-practices/how-to-set-up-a-multifunction-device-or-application-to-send-email-using-microsoft-365-or-office-365) . Des environnements plus étendus devront être plus réfléchis. Les courriers électroniques et les messages marketing qui peuvent être considérés comme du courrier indésirable par les destinataires ne sont pas autorisés.

- Defender pour Office 365 n’a pas de fonctionnalité pour l’agrégation des rapports DMARC. Visitez le [catalogue MISA (Microsoft Intelligent Security Association)](https://www.microsoft.com/misapartnercatalog) pour voir les fournisseurs tiers qui proposent des rapports DMARC pour Microsoft 365.

## <a name="move-features-that-modify-messages-into-microsoft-365"></a>Déplacer des fonctionnalités qui modifient des messages dans Microsoft 365

Vous devez transférer toutes les personnalisations ou fonctionnalités qui modifient les messages de quelque manière que ce soit dans Microsoft 365. Par exemple, votre service de protection existant ajoute une balise **externe** à l’objet ou au corps des messages des expéditeurs externes. Toute fonctionnalité d’habillage de liens entraîne également des problèmes avec certains messages. Si vous utilisez une telle fonctionnalité aujourd’hui, vous devez hiérarchiser le déploiement des liens fiables comme alternative pour réduire les problèmes.

Si vous ne désactivez pas les fonctionnalités de modification de message dans votre service de protection existant, vous pouvez vous attendre à obtenir les résultats négatifs suivants dans Microsoft 365 :

- DKIM s’arrête. Tous les expéditeurs ne s’appuient pas sur DKIM, mais ceux qui le font échouent.
- [L’intelligence par usurpation d’identité](anti-spoofing-protection.md) et l’étape de paramétrage plus loin dans ce guide ne fonctionnent pas correctement.
- Vous obtiendrez probablement un grand nombre de faux positifs (bon courrier marqué comme mauvais).

Pour recréer l’identification de l’expéditeur externe dans Microsoft 365, vous disposez des options suivantes :

- La [fonctionnalité d’appel de l’expéditeur externe Outlook](https://techcommunity.microsoft.com/t5/exchange-team-blog/native-external-sender-callouts-on-email-in-outlook/ba-p/2250098), ainsi que les [premiers conseils de sécurité des contacts](set-up-anti-phishing-policies.md#first-contact-safety-tip).
- Règles de flux de messagerie (également appelées règles de transport). Pour plus d’informations, consultez les [exclusions de responsabilité, les signatures, les pieds de page ou les en-têtes des messages à l’échelle de l’organisation dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/disclaimers-signatures-footers-or-headers).

Microsoft travaille avec le secteur pour prendre en charge la norme ARC (Authenticated Received Chain) dans un avenir proche. Si vous souhaitez laisser les fonctionnalités de modification de message activées sur votre fournisseur de passerelle de messagerie actuel, nous vous recommandons de les contacter pour connaître leurs plans de prise en charge de cette norme.

## <a name="account-for-any-active-phishing-simulations"></a>Compte pour toutes les simulations de hameçonnage actives

Si vous avez des simulations de hameçonnage tierces actives, vous devez empêcher les messages, les liens et les pièces jointes d’être identifiés comme hameçonnage par Defender pour Office 365. Pour plus d’informations, consultez [Configurer des simulations d’hameçonnage tierces dans la stratégie de remise avancée](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-third-party-phishing-simulations-in-the-advanced-delivery-policy).

## <a name="define-spam-and-bulk-user-experiences"></a>Définir le courrier indésirable et les expériences utilisateur en bloc

- **Mise en quarantaine et remise au dossier Junk Email** : la réponse naturelle et recommandée pour les messages malveillants et certainement risqués consiste à mettre en quarantaine les messages. Mais, comment voulez-vous que vos utilisateurs gèrent les messages moins dangereux, tels que le courrier indésirable et le courrier en bloc (également appelé *courrier gris*). Ces types de messages doivent-ils être remis aux dossiers de Email de courrier indésirable de l’utilisateur ?

  Avec nos paramètres de sécurité Standard, nous livrons généralement ces types de messages moins risqués dans le dossier Junk Email. Ce comportement est similaire à de nombreuses offres de messagerie grand public, où les utilisateurs peuvent vérifier dans leur dossier Junk Email les messages manquants et les sauver eux-mêmes. Ou, si l’utilisateur s’est volontairement inscrit à un bulletin d’informations ou à un courrier marketing, il peut choisir de se désabonner ou de bloquer l’expéditeur pour sa propre boîte aux lettres.

  Toutefois, de nombreux utilisateurs d’entreprise sont habitués à peu (le cas échéant) de courrier dans leur dossier Junk Email. Au lieu de cela, ces utilisateurs d’entreprise sont utilisés pour vérifier la mise en quarantaine de leurs messages manquants. La quarantaine introduit des problèmes liés aux notifications de quarantaine, à la fréquence des notifications et aux autorisations requises pour afficher et libérer des messages.

  - Le message DKIM (Domain Keys Identified Mail) s’arrête.
  - [L’intelligence par usurpation d’identité](anti-spoofing-protection.md) ne fonctionnera pas correctement.
  - Vous obtiendrez probablement un grand nombre de faux positifs (bon courrier marqué comme mauvais).

  En fin de compte, c’est votre décision si vous souhaitez empêcher la remise de courrier électronique au dossier Junk Email en faveur de la remise en quarantaine. Mais une chose est certaine : si l’expérience dans Defender pour Office 365 est différente de ce à quoi vos utilisateurs sont habitués, vous devez les notifier et fournir une formation de base. Incorporez les apprentissages du pilote et assurez-vous que les utilisateurs sont préparés à tout nouveau comportement pour la remise des e-mails.

- **Courrier en bloc recherché ou courrier en bloc indésirable** : de nombreux systèmes de protection permettent aux utilisateurs d’autoriser ou de bloquer eux-mêmes les e-mails en bloc. Ces paramètres ne migrent pas facilement vers Microsoft 365. Vous devez donc envisager de travailler avec des adresses IP virtuelles et leur personnel pour recréer leurs configurations existantes dans Microsoft 365.

  Aujourd’hui, Microsoft 365 considère que certains messages en bloc (par exemple, les bulletins d’informations) sont sécurisés en fonction de la source du message. Le courrier provenant de ces sources « sûres » n’est actuellement pas marqué comme étant en bloc (le niveau de réclamation en bloc ou BCL est égal à 0 ou 1), il est donc difficile de bloquer globalement le courrier provenant de ces sources. Pour la plupart des utilisateurs, la solution consiste à leur demander de se désabonner individuellement de ces messages en bloc ou d’utiliser Outlook pour bloquer l’expéditeur. Toutefois, certains utilisateurs n’aimeront pas bloquer ou annuler l’abonnement aux messages en bloc eux-mêmes.

  Les règles de flux de messagerie qui filtrent les e-mails en bloc peuvent être utiles lorsque les utilisateurs d’adresses IP virtuelles ne souhaitent pas gérer cela eux-mêmes. Pour plus d’informations, consultez [Utiliser des règles de flux de courrier pour filtrer les e-mails en bloc](/exchange/security-and-compliance/mail-flow-rules/use-rules-to-filter-bulk-mail).

## <a name="identify-and-designate-priority-accounts"></a>Identifier et désigner des comptes prioritaires

Si la fonctionnalité est disponible, les **comptes de priorité** et **les balises utilisateur** peuvent vous aider à identifier vos utilisateurs Microsoft 365 importants afin qu’ils se distinguent dans les rapports. Pour plus d’informations, consultez [les balises utilisateur dans Microsoft Defender pour Office 365](user-tags.md) et [gérer et surveiller les comptes prioritaires](/microsoft-365/admin/setup/priority-accounts).

## <a name="next-step"></a>Étape suivante

**Félicitations**! Vous avez terminé la phase **de préparation** de votre [migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process) !

- Passez à la [phase 2 : configuration](migrate-to-defender-for-office-365-setup.md).
