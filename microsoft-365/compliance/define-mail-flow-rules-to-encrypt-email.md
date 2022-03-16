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
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: 9b7daf19-d5f2-415b-bc43-a0f5f4a585e8
ms.collection:
- M365-security-compliance
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Les administrateurs peuvent apprendre à créer des règles de flux de messagerie (règles de transport) pour chiffrer et déchiffrer des messages à l’aide chiffrement de messages Office 365.
ms.openlocfilehash: bb50ed5d2b22fd74d4a6f88eba29f82d10be1f50
ms.sourcegitcommit: a216617d6ff27fe7d3089a047fbeaac5d72fd25c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2022
ms.locfileid: "63512809"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Définir des règles de flux de messagerie pour chiffrer les messages électroniques

En tant qu’administrateur qui gère Exchange Online, vous pouvez créer des règles de flux de messagerie (également appelées règles de transport) pour protéger les messages électroniques que vous envoyez et recevez. Vous pouvez configurer des règles pour chiffrer les messages électroniques sortants et supprimer le chiffrement des messages chiffrés provenant de l’intérieur de votre organisation ou des réponses aux messages chiffrés envoyés à partir de votre organisation. Vous pouvez utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre Exchange d’administration (EAC)</a> ou Exchange Online PowerShell pour créer ces règles. En plus des règles de chiffrement globales, vous pouvez également choisir d’activer ou de désactiver des options de chiffrement des messages individuels pour les utilisateurs finaux.

Vous ne pouvez pas chiffrer le courrier entrant provenant d’expéditeurs extérieurs à votre organisation.

Si vous avez récemment migré d’Active Directory RMS vers Azure Information Protection, vous devez passer en revue vos règles de flux de messagerie existantes pour vous assurer qu’elles continuent de fonctionner dans votre nouvel environnement. En outre, si vous souhaitez tirer parti des nouvelles fonctionnalités chiffrement de messages Office 365 (OME) disponibles via Azure Information Protection, vous devez mettre à jour vos règles de flux de messagerie existantes. Dans le cas contraire, vos utilisateurs continueront à recevoir des messages chiffrés qui utilisent le format de pièce jointe HTML précédent au lieu de la nouvelle expérience OME transparente. Si vous n’avez pas encore installé OME, voir Configurer les nouvelles fonctionnalités [chiffrement de messages Office 365 pour](set-up-new-message-encryption-capabilities.md) plus d’informations.

Pour plus d’informations sur les composants qui constituant les règles de flux de messagerie et sur le fonctionnement des règles de flux de messagerie, voir Règles de flux de messagerie (règles de [transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). Pour plus d’informations sur le fonctionnement des règles de flux de messagerie avec Azure Information Protection, voir [Configuring Exchange Online mail flow rules for Azure Information Protection labels](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> Pour les environnements Exchange hybrides, les utilisateurs locaux peuvent envoyer et recevoir des messages chiffrés à l’aide d’OME uniquement si le courrier électronique est acheminé via Exchange Online. Pour configurer OME dans un environnement Exchange hybride, vous devez d’abord configurer l’environnement hybride à l’aide de l’Assistant [Configuration](/Exchange/exchange-hybrid) hybride, puis configurer le flux de messagerie de [Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) vers votre serveur de messagerie et configurer le flux de messagerie de votre serveur de messagerie vers [Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). Une fois que vous avez configuré le flux de messagerie Office 365, vous pouvez configurer des règles de flux de messagerie pour OME à l’aide de ces instructions.

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-the-new-ome-capabilities"></a>Créer des règles de flux de messagerie pour chiffrer les messages électroniques avec les nouvelles fonctionnalités OME

Vous pouvez définir des règles de flux de messagerie pour déclencher le chiffrement des messages avec les nouvelles fonctionnalités OME à l’aide du EAC.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-the-new-ome-capabilities"></a>Utiliser le EAC pour créer une règle de chiffrement des messages électroniques avec les nouvelles fonctionnalités OME

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la **vignette** Administrateur.

3. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, sélectionnez **Centres d’administration** \> **Exchange**.

4. Dans le EAC, sélectionnez **Règles de flux de** \> messagerie et **sélectionnez Nouvelle** ![icône.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation du Centre d’administration Exchange, [consultez](/exchange/exchange-admin-center) la Exchange Online.

5. Dans **Nom**, tapez un nom pour la règle, tel que Chiffrer le courrier électronique DrToniRamos@hotmail.com.

6. Dans **Appliquer cette règle si**, sélectionnez une condition et entrez une valeur si nécessaire. Par exemple, pour chiffrer les messages adressés à DrToniRamos@hotmail.com :

   1. Dans **Appliquer cette règle si**, sélectionnez **le destinataire est**.

   2. Choisissez un nom existant dans la liste de contacts ou entrez une nouvelle adresse de messagerie dans la zone **vérifier les noms**.

      - Pour sélectionner un nom existant, sélectionnez-le dans la liste et cliquez sur **OK**.

      - Pour entrer un nouveau nom, tapez une adresse de messagerie dans la case à cocher **noms** , puis **sélectionnez Vérifier les noms** \> **OK**.

7. Pour ajouter d’autres conditions, sélectionnez **Plus d’options** , puis **ajoutez une condition** et sélectionnez-la dans la liste.

   Par exemple, pour appliquer la règle uniquement si le destinataire est en dehors de votre organisation, sélectionnez Ajouter **une condition** , puis sélectionnez Le destinataire est externe **/interne** \> à l’extérieur de **l’organisation** \> **OK**.

8. Pour activer le chiffrement à l’aide des nouvelles fonctionnalités **OME, dans** l’exemple suivant, sélectionnez Modifier la sécurité des **messages**, puis sélectionnez Appliquer **chiffrement de messages Office 365 protection des** droits. Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer**, puis **OK**.
  
  La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, assurez-vous que vous avez chiffrement de messages Office 365 avec les nouvelles fonctionnalités, comme décrit dans Configurer de [chiffrement de messages Office 365 nouvelles fonctionnalités](set-up-new-message-encryption-capabilities.md). Pour plus d’informations sur les modèles par défaut, voir [Configuration et gestion des modèles pour Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Pour plus d’informations **sur l’option Ne pas forwarder** , consultez [l’option Ne pas forwarder pour les e-mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Pour plus d’informations **sur l’option chiffrer uniquement** , voir [l’option Chiffrer uniquement pour les e-mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Vous pouvez choisir **d’ajouter une action** si vous souhaitez spécifier une autre action.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-the-new-ome-capabilities"></a>Utiliser le EAC pour mettre à jour une règle de flux de messagerie existante afin d’utiliser les nouvelles fonctionnalités OME

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la **vignette** Administrateur.

3. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, sélectionnez **Centres d’administration** \> **Exchange**.

4. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

5. Dans la liste des règles de flux de messagerie, sélectionnez la règle à modifier pour utiliser les nouvelles fonctionnalités OME,  ![puis sélectionnez Modifier l’icône Modifier.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

6. Pour activer le chiffrement à l’aide des nouvelles fonctionnalités **OME, dans** l’exemple suivant, sélectionnez Modifier la sécurité des **messages**, puis appliquer chiffrement de messages Office 365 protection **des** droits. Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer** , puis **OK**.

   La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, assurez-vous que vous avez installé chiffrement de messages Office 365 avec les nouvelles fonctionnalités décrites dans Configurer de nouvelles fonctionnalités chiffrement de messages Office 365 intégrées à [Azure Information Protection](set-up-new-message-encryption-capabilities.md). Pour plus d’informations sur les modèles par défaut, voir [Configuration et gestion des modèles pour Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Pour plus d’informations sur l’option Ne pas forwarder, consultez [l’option Ne pas forwarder pour les e-mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Pour plus d’informations sur l’option chiffrer uniquement, voir [l’option Chiffrer uniquement pour les e-mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Vous pouvez choisir **d’ajouter une action** si vous souhaitez spécifier une autre action.

7. Dans la **liste Faire,** supprimez toutes les actions affectées à Modifier la sécurité **des** \> messages **Appliquer la version précédente d’OME**.

8. Cliquez sur **Enregistrer**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-the-new-ome-capabilities"></a>Créer des règles de flux de messagerie pour supprimer le chiffrement des messages électroniques avec les nouvelles fonctionnalités OME

Vous pouvez définir des règles de flux de messagerie pour déclencher la suppression du chiffrement des messages avec les nouvelles fonctionnalités OME à l’aide du EAC.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-the-new-ome-capabilities"></a>Utiliser le EAC pour créer une règle pour supprimer le chiffrement des messages électroniques avec les nouvelles fonctionnalités OME

Vous pouvez supprimer le chiffrement des messages appliqués par votre organisation. Vous pouvez également supprimer le chiffrement de toutes les pièces jointes chiffrées pour vous assurer que l’intégralité du message électronique est sans aucune protection.

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la **vignette** Administrateur.

3. Dans la <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, sélectionnez **Centres d’administration** \> **Exchange**.

4. Dans le EAC, sélectionnez **Règles de flux de** \> messagerie et **sélectionnez Nouvelle** ![icône.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation du Centre d’administration Exchange, [consultez](/exchange/exchange-admin-center) la Exchange Online.

5. Dans **Nom**, tapez un nom pour la règle, tel que Supprimer le chiffrement du courrier sortant.

6. Dans **Appliquer cette règle si**, sélectionnez les conditions dans laquelle le chiffrement doit être supprimé des messages. Ajouter **L’expéditeur se trouve à l’intérieur** \> de  **l’organisation** pour l’envoi de messages _ou_ \> Le destinataire se trouve à l’intérieur de l’organisation **pour la** réception du courrier électronique.

7. Dans **Faire les choses suivantes**, **sélectionnez Modifier** la sécurité des messages \> **Chiffrement de messages Office 365 protection des droits appliquée par l’organisation**.

8. (Facultatif) Dans **Faire ce qui suit**, **sélectionnez Modifier** la sécurité des messages \> Supprimer la protection des droits de pièce jointe **appliquée par l’organisation**.

Enregistrez la règle.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-the-new-capabilities"></a>Créer des règles de flux de messagerie chiffrement de messages Office 365 sans les nouvelles fonctionnalités

Si vous n’avez pas encore déplacé votre organisation vers les nouvelles fonctionnalités OME, Microsoft vous recommande de prendre un plan pour passer aux nouvelles fonctionnalités OME dès que cela est raisonnable pour votre organisation. Pour obtenir des instructions, voir [Configurer de chiffrement de messages Office 365 nouvelles fonctionnalités intégrées à Azure Information Protection](set-up-new-message-encryption-capabilities.md). Dans le cas contraire, voir [Définition des règles de flux de messagerie pour chiffrement de messages Office 365 qui n’utilisent pas les nouvelles fonctionnalités OME](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-the-new-ome-capabilities).

## <a name="related-content"></a>Contenu associé

[Chiffrement dans Office 365](encryption.md)

[Configurer les nouvelles fonctionnalités de chiffrement de messages Office 365](set-up-new-message-encryption-capabilities.md)

[Personnaliser les messages chiffrés](add-your-organization-brand-to-encrypted-messages.md)

[Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
