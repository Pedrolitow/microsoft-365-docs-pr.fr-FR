---
title: Définir des règles de flux de messagerie pour chiffrer les messages électroniques
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- MET150
- MOE150
ms.assetid: 9b7daf19-d5f2-415b-bc43-a0f5f4a585e8
ms.collection:
- M365-security-compliance
description: Les administrateurs peuvent apprendre à créer des règles de flux de messagerie (règles de transport) pour chiffrer et déchiffrer des messages à l’aide du chiffrement de messages Office 365.
ms.openlocfilehash: 63b1b0ba3b13f5beecd049a8ef81d6355855626f
ms.sourcegitcommit: 956176ed7c8b8427fdc655abcd1709d86da9447e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/23/2021
ms.locfileid: "51051936"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Définir des règles de flux de messagerie pour chiffrer les messages électroniques

En tant qu’administrateur qui gère Exchange Online, vous pouvez créer des règles de flux de messagerie (également appelées règles de transport) pour protéger les messages électroniques que vous envoyez et recevez. Vous pouvez configurer des règles pour chiffrer les messages électroniques sortants et supprimer le chiffrement des messages chiffrés provenant de l’intérieur de votre organisation ou des réponses aux messages chiffrés envoyés à partir de votre organisation. Vous pouvez utiliser le Centre d’administration Exchange (EAC) ou Exchange Online PowerShell pour créer ces règles. En plus des règles de chiffrement globales, vous pouvez également choisir d’activer ou de désactiver des options de chiffrement des messages individuels pour les utilisateurs finaux.

Vous ne pouvez pas chiffrer le courrier entrant provenant d’expéditeurs extérieurs à votre organisation.

Si vous avez récemment migré d’Active Directory RMS vers Azure Information Protection, vous devez passer en revue vos règles de flux de messagerie existantes pour vous assurer qu’elles continuent de fonctionner dans votre nouvel environnement. En outre, si vous souhaitez tirer parti des nouvelles fonctionnalités de chiffrement de messages Office 365 (OME) disponibles via Azure Information Protection, vous devez mettre à jour vos règles de flux de messagerie existantes. Dans le cas contraire, vos utilisateurs continueront à recevoir des messages chiffrés qui utilisent le format de pièce jointe HTML précédent au lieu de la nouvelle expérience OME transparente. Si vous n’avez pas encore installé OME, consultez Configurer les nouvelles fonctionnalités de chiffrement de messages [Office 365](set-up-new-message-encryption-capabilities.md) pour plus d’informations.

Pour plus d’informations sur les composants qui font les règles de flux de messagerie et sur le fonctionnement des règles de flux de messagerie, voir Règles de flux de messagerie [(règles de transport) dans Exchange Online.](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules) Pour plus d’informations sur le fonctionnement des règles de flux de messagerie avec Azure Information Protection, voir [Configuring Exchange Online mail flow rules for Azure Information Protection labels](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> Pour les environnements Exchange hybrides, les utilisateurs locaux peuvent envoyer et recevoir des messages chiffrés à l’aide d’OME uniquement si le courrier est acheminé via Exchange Online. Pour configurer OME dans un environnement Exchange hybride, vous devez d’abord configurer un environnement hybride à l’aide de l’Assistant [Configuration](/Exchange/exchange-hybrid) hybride, puis configurer le flux de messagerie de [Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) vers votre serveur de messagerie et configurer le flux de messagerie de votre serveur de messagerie vers [Office 365.](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365) Une fois que vous avez configuré le flux de messagerie via Office 365, vous pouvez configurer des règles de flux de messagerie pour OME à l’aide de ces instructions.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-the-new-ome-capabilities"></a>Créer des règles de flux de messagerie pour chiffrer les messages électroniques avec les nouvelles fonctionnalités OME

Vous pouvez définir des règles de flux de messagerie pour déclencher le chiffrement des messages avec les nouvelles fonctionnalités OME à l’aide du EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-the-new-ome-capabilities"></a>Utiliser le EAC pour créer une règle de chiffrement des messages électroniques avec les nouvelles fonctionnalités OME

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous [à Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Choisissez la **vignette** Administrateur.

3. Dans le Centre d’administration Microsoft 365, sélectionnez **Centres d’administration** \> **Exchange**.

4. Dans le EAC, sélectionnez Règles de **flux de** messagerie et \>  **sélectionnez Nouvelle** icône Créer une ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \> **règle.** Pour plus d’informations sur l’utilisation du CENTRE d’administration Exchange, consultez le Centre [d’administration Exchange dans Exchange Online.](/exchange/exchange-admin-center)

5. In **Name**, type a name for the rule, such as Encrypt mail for DrToniRamos@hotmail.com.

6. Dans **Appliquer cette règle si**, sélectionnez une condition et entrez une valeur si nécessaire. Par exemple, pour chiffrer les messages adressés à DrToniRamos@hotmail.com :

   1. Dans **Appliquer cette règle si**, sélectionnez **le destinataire est**.

   2. Choisissez un nom existant dans la liste de contacts ou entrez une nouvelle adresse de messagerie dans la zone **vérifier les noms**.

      - Pour sélectionner un nom existant, sélectionnez-le dans la liste et cliquez sur **OK**.

      - Pour entrer un nouveau nom, tapez une adresse de messagerie dans la case à cocher **noms,** puis sélectionnez **vérifier les noms** \> **OK.**

7. Pour ajouter d’autres conditions, sélectionnez **Plus d’options,** puis **ajoutez une condition** et sélectionnez-la dans la liste.

   Par exemple, pour appliquer la règle uniquement si le destinataire est en dehors de votre organisation, sélectionnez Ajouter **une condition,** puis sélectionnez Le destinataire est **externe/interne** à l’extérieur de \> **l’organisation** \> **OK**.

8. Pour activer le chiffrement à l’aide des nouvelles fonctionnalités OME, dans La suite des **choses,** sélectionnez Modifier la sécurité des **messages,** puis appliquez le chiffrement de messages Office **365** et la protection des droits. Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer,** puis **ok.**
  
  La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, assurez-vous que vous avez bien installé le chiffrement de messages Office 365 avec les nouvelles fonctionnalités décrites dans Configurer les nouvelles fonctionnalités de chiffrement de messages [Office 365.](set-up-new-message-encryption-capabilities.md) Pour plus d’informations sur les modèles par défaut, voir [Configuration et gestion des modèles pour Azure Information Protection.](/information-protection/deploy-use/configure-policy-templates) Pour plus d’informations **sur l’option** Ne pas forwarder, consultez [l’option Ne pas forwarder pour les e-mails.](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) Pour plus d’informations **sur l’option chiffrer uniquement,** voir [l’option Chiffrer uniquement pour les e-mails.](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

  Vous pouvez choisir **d’ajouter une action** si vous souhaitez spécifier une autre action.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-the-new-ome-capabilities"></a>Utiliser le EAC pour mettre à jour une règle de flux de messagerie existante afin d’utiliser les nouvelles fonctionnalités OME

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous [à Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Choisissez la **vignette** Administrateur.

3. Dans le Centre d’administration Microsoft 365, sélectionnez **Centres d’administration** \> **Exchange**.

4. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

5. Dans la liste des règles de flux de messagerie, sélectionnez la règle à modifier pour utiliser les nouvelles fonctionnalités OME, puis sélectionnez **Modifier** ![ l’icône ](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif) Modifier.

6. Pour activer le chiffrement à l’aide des nouvelles fonctionnalités OME, dans l’exemple **suivant,** choisissez Modifier la sécurité des **messages,** puis appliquez le chiffrement de messages **Office 365** et la protection des droits. Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer,** puis **OK.**

   La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, assurez-vous que vous avez installé le chiffrement de messages Office 365 avec les nouvelles fonctionnalités décrites dans Configurer les nouvelles fonctionnalités de chiffrement de messages [Office 365](set-up-new-message-encryption-capabilities.md)intégrées à Azure Information Protection. Pour plus d’informations sur les modèles par défaut, voir [Configuration et gestion des modèles pour Azure Information Protection.](/information-protection/deploy-use/configure-policy-templates) Pour plus d’informations sur l’option Ne pas forwarder, consultez [l’option Ne pas forwarder pour les e-mails.](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) Pour plus d’informations sur l’option chiffrer uniquement, voir [l’option Chiffrer uniquement pour les e-mails.](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

   Vous pouvez choisir **d’ajouter une action** si vous souhaitez spécifier une autre action.

7. Dans la **liste Faire la liste** suivante, supprimez toutes les actions affectées à Modifier la sécurité du **message** Appliquer la version précédente \> **d’OME**.

8. Cliquez sur **Enregistrer**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-the-new-ome-capabilities"></a>Créer des règles de flux de messagerie pour supprimer le chiffrement des messages électroniques avec les nouvelles fonctionnalités OME

Vous pouvez définir des règles de flux de messagerie pour déclencher la suppression du chiffrement des messages avec les nouvelles fonctionnalités OME à l’aide du EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-the-new-ome-capabilities"></a>Utiliser le EAC pour créer une règle pour supprimer le chiffrement des messages électroniques avec les nouvelles fonctionnalités OME

Vous pouvez supprimer le chiffrement accessible par votre organisation. Cela signifie tout courrier avec chiffrement appliqué par l’organisation ou tout courrier protégé par des restrictions de chiffrement uniquement.

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous [à Office 365.](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser)

2. Choisissez la **vignette** Administrateur.

3. Dans le Centre d’administration Microsoft 365, sélectionnez **Centres d’administration** \> **Exchange**.

4. Dans le EAC, sélectionnez Règles de **flux de** messagerie et \>  **sélectionnez Nouvelle** icône Créer une ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \> **règle.** Pour plus d’informations sur l’utilisation du CENTRE d’administration Exchange, consultez le Centre [d’administration Exchange dans Exchange Online.](/exchange/exchange-admin-center)

5. In **Name**, type a name for the rule, such as Remove encryption from outgoing mail.

6. Dans **Appliquer cette règle si**, sélectionnez les conditions dans laquelle le chiffrement doit être supprimé des messages. Ajoutez **l’expéditeur se trouve à l’intérieur** de l’organisation \>  _ou_ **le destinataire se trouve à** \> **l’intérieur de l’organisation.**

7. In **Do the following**, select Modify the message **security** Remove \> **Office 365 Message Encryption and rights protection**.

8. Sélectionnez **Enregistrer**.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-the-new-capabilities"></a>Créer des règles de flux de messagerie pour le chiffrement de messages Office 365 sans les nouvelles fonctionnalités

Si vous n’avez pas encore déplacé votre organisation vers les nouvelles fonctionnalités OME, Microsoft vous recommande de prendre un plan pour passer aux nouvelles fonctionnalités OME dès que cela est raisonnable pour votre organisation. Pour obtenir des instructions, voir Configurer les nouvelles fonctionnalités de chiffrement de messages [Office 365](set-up-new-message-encryption-capabilities.md)intégrées à Azure Information Protection. Dans le cas contraire, voir Définir des règles de flux de messagerie pour le chiffrement de messages Office 365 qui n’utilisent pas les nouvelles [fonctionnalités OME.](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities)

## <a name="related-topics"></a>Voir aussi

[Chiffrement dans Office 365](encryption.md)

[Configurer les nouvelles fonctionnalités de chiffrement de messages Office 365](set-up-new-message-encryption-capabilities.md)

[Personnaliser les messages chiffrés](add-your-organization-brand-to-encrypted-messages.md)

[Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)

[Règles de flux de messagerie (règles de transport) dans Exchange Online Protection](../security/defender-365-security/mail-flow-rules-transport-rules-0.md)
