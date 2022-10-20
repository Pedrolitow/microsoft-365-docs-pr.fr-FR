---
title: Définir des règles de flux de courrier pour chiffrer les courriers électroniques
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
- purview-compliance
- tier2
ms.custom:
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Les administrateurs peuvent apprendre à créer des règles de flux de courrier (règles de transport) pour chiffrer et déchiffrer des messages à l’aide de Chiffrement de messages Microsoft Purview.
ms.openlocfilehash: b244cd1847d46f80bd56ec5a9aec09eadc6781cd
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68620720"
---
# <a name="define-mail-flow-rules-to-encrypt-email-messages"></a>Définir des règles de flux de courrier pour chiffrer les courriers électroniques

En tant qu’administrateur qui gère Exchange Online, vous pouvez créer des règles de flux de courrier (également appelées règles de transport) pour protéger les messages électroniques que vous envoyez et recevez. Vous pouvez configurer des règles pour chiffrer les messages électroniques sortants et supprimer le chiffrement des messages chiffrés provenant de votre organisation ou des réponses aux messages chiffrés envoyés par votre organisation. Vous pouvez utiliser le <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">Centre d’administration Exchange (EAC)</a> ou Exchange Online PowerShell pour créer ces règles. En plus des règles de chiffrement globales, vous pouvez également choisir d’activer ou de désactiver des options de chiffrement des messages individuels pour les utilisateurs finaux.

Vous ne pouvez pas chiffrer les messages entrants provenant d’expéditeurs extérieurs à votre organisation.

Si vous avez récemment migré d’Active Directory RMS vers Azure Information Protection, vous devez passer en revue vos règles de flux de messagerie existantes pour vous assurer qu’elles continuent à fonctionner dans votre nouvel environnement. En outre, pour utiliser Chiffrement de messages Microsoft Purview avec Azure Information Protection, vous devez mettre à jour vos règles de flux de messagerie existantes. Sinon, vos utilisateurs continueront à recevoir des messages chiffrés qui utilisent le format de pièce jointe HTML précédent au lieu de la nouvelle expérience transparente. Si vous n’avez pas encore configuré le chiffrement des messages, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md) pour plus d’informations.

Pour plus d’informations sur les composants qui composent les règles de flux de messagerie et le fonctionnement des règles de flux de courrier, consultez [les règles de flux de courrier (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules). Pour plus d’informations sur le fonctionnement des règles de flux de messagerie avec Azure Information Protection, consultez [Configuration des règles de flux de messagerie Exchange Online pour les étiquettes Azure Information Protection](/azure/information-protection/deploy-use/configure-exo-rules).

> [!IMPORTANT]
> Pour les environnements Exchange hybrides, les utilisateurs locaux peuvent envoyer et recevoir des messages chiffrés à l’aide du chiffrement des messages uniquement si les e-mails sont acheminés via Exchange Online. Pour configurer le chiffrement des messages dans un environnement Exchange hybride, vous devez d’abord [configurer l’environnement hybride à l’aide de l’Assistant Configuration hybride](/Exchange/exchange-hybrid), puis [configurer le courrier pour qu’il transite de Office 365 vers votre serveur de messagerie](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-1-configure-mail-to-flow-from-office-365-to-your-on-premises-email-server) et [configurer le flux de courrier de votre serveur de messagerie vers Office 365](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/set-up-connectors-to-route-mail#part-2-configure-mail-to-flow-from-your-email-server-to-office-365). Une fois que vous avez configuré la messagerie pour qu’elle transite par Office 365, vous pouvez configurer des règles de flux de messagerie pour le chiffrement des messages à l’aide de ces conseils.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="create-mail-flow-rules-to-encrypt-email-messages-with-microsoft-purview-message-encryption"></a>Créer des règles de flux de courrier pour chiffrer les messages électroniques avec Chiffrement de messages Microsoft Purview

Vous pouvez définir des règles de flux de messagerie pour déclencher le chiffrement des messages à l’aide du centre d’administration des messages électroniques.

### <a name="use-the-eac-to-create-a-rule-for-encrypting-email-messages-with-microsoft-purview-message-encryption"></a>Utilisez le CAE pour créer une règle de chiffrement des messages électroniques avec Chiffrement de messages Microsoft Purview

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administration**.

3. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, choisissez **Administration centres** \> **Exchange**.

4. Dans le CENTRE, accédez aux **règles** de **flux** \> de messagerie et sélectionnez **l’icône Nouveau** ![nouveau.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation de la CAE, consultez [le Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par exemple Chiffrer le courrier pour DrToniRamos@hotmail.com.

6. Dans **Appliquer cette règle si**, sélectionnez une condition et entrez une valeur si nécessaire. Par exemple, pour chiffrer les messages adressés à DrToniRamos@hotmail.com :

   1. Dans **Appliquer cette règle si**, sélectionnez **le destinataire est**.

   2. Choisissez un nom existant dans la liste de contacts ou entrez une nouvelle adresse de messagerie dans la zone **vérifier les noms**.

      - Pour sélectionner un nom existant, sélectionnez-le dans la liste et cliquez sur **OK**.

      - Pour entrer un nouveau nom, tapez une adresse e-mail dans la case **à cocher des noms** , puis **cochez les noms** \> **OK**.

7. Pour ajouter d’autres conditions, choisissez **Autres options** , puis **ajoutez une condition** , puis sélectionnez dans la liste.

   Par exemple, pour appliquer la règle uniquement si le destinataire est en dehors de votre organisation, sélectionnez **Ajouter une condition** , puis sélectionnez **Le destinataire est externe/interne** \> **en dehors de l’organisation** \> **OK**.

8. Pour activer **le** chiffrement des messages, sélectionnez **Modifier la sécurité des messages**, puis **appliquez Office 365 chiffrement des messages et protection des droits**. Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer**, puis **choisissez OK**.
  
  La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, vérifiez que vous avez configuré Chiffrement de messages Microsoft Purview comme décrit dans [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Pour plus d’informations sur les modèles par défaut, consultez [Configuration et gestion des modèles pour Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Pour plus d’informations sur l’option **Ne pas transférer** , consultez [l’option Ne pas transférer pour les e-mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Pour plus d’informations sur l’option **chiffrer uniquement** , consultez [l’option Chiffrer uniquement pour les e-mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

  Vous pouvez choisir **d’ajouter une action** si vous souhaitez spécifier une autre action.

### <a name="use-the-eac-to-update-an-existing-mail-flow-rule-to-use-microsoft-purview-message-encryption"></a>Utilisez le CAE pour mettre à jour une règle de flux de messagerie existante afin d’utiliser Chiffrement de messages Microsoft Purview

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administration**.

3. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, choisissez **Administration centres** \> **Exchange**.

4. Dans le CAE, accédez à **Flux de messagerie** \> **Règles**.

5. Dans la liste des règles de flux de courrier, sélectionnez la règle que vous souhaitez modifier pour l’utiliser avec Chiffrement de messages Microsoft Purview, puis choisissez **l’icône Modifier**![.](../media/ebd260e4-3556-4fb0-b0bb-cc489773042c.gif)

6. Pour activer le chiffrement à l’aide **de Chiffrement de messages Microsoft Purview**, choisissez **Modifier la sécurité des messages**, puis **appliquer Office 365 chiffrement des messages et protection des droits**. Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer** , puis **choisissez OK**.

   La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, vérifiez que vous avez configuré Chiffrement de messages Microsoft Purview comme décrit dans [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Pour plus d’informations sur les modèles par défaut, consultez [Configuration et gestion des modèles pour Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Pour plus d’informations sur l’option Ne pas transférer, consultez [l’option Ne pas transférer pour les e-mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Pour plus d’informations sur l’option chiffrer uniquement, consultez [l’option Chiffrer uniquement pour les e-mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Vous pouvez choisir **d’ajouter une action** si vous souhaitez spécifier une autre action.

7. Dans la liste **Do the following** , supprimez toutes les actions affectées à **Modify the message security** \> **Apply the previous version of OME**.

8. Cliquez sur **Enregistrer**.

## <a name="create-mail-flow-rules-to-remove-encryption-for-email-messages-with-microsoft-purview-message-encryption"></a>Créer des règles de flux de messagerie pour supprimer le chiffrement des messages électroniques avec Chiffrement de messages Microsoft Purview

Vous pouvez définir des règles de flux de messagerie pour supprimer le chiffrement des messages avec Chiffrement de messages Microsoft Purview à l’aide de la caE.

### <a name="use-the-eac-to-create-a-rule-to-remove-encryption-from-email-messages-with-microsoft-purview-message-encryption"></a>Utilisez le CAE pour créer une règle pour supprimer le chiffrement des messages électroniques avec Chiffrement de messages Microsoft Purview

Vous pouvez supprimer le chiffrement des messages qui ont été appliqués par votre organisation. Vous pouvez également supprimer le chiffrement de toutes les pièces jointes chiffrées pour vous assurer que l’intégralité du message électronique est sans aucune protection.

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administration**.

3. Dans le <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">Centre d'administration Microsoft 365</a>, choisissez **Administration centres** \> **Exchange**.

4. Dans le CENTRE, accédez aux **règles** de **flux** \> de messagerie et sélectionnez **l’icône Nouveau** ![nouveau.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation de la CAE, consultez [le Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par `Remove encryption from outgoing mail`exemple .

6. Dans **Appliquer cette règle si**, sélectionnez les conditions dans lesquelles le chiffrement doit être supprimé des messages. Ajouter **L’expéditeur se trouve** \> **à l’intérieur de l’organisation** pour l’envoi de courrier _ou_ **le destinataire se trouve** \> **à l’intérieur de l’organisation** pour la réception du courrier.

7. Dans **Faire ce qui suit**, sélectionnez **Modifier la sécurité** \> **des messages Supprimer Office 365 chiffrement des messages et protection des droits appliquée par l’organisation**.

8. (Facultatif) Dans **Faire ce qui suit**, sélectionnez **Modifier la protection de sécurité** \> **des messages Supprimer les droits de pièce jointe appliquée par l’organisation**.

Enregistrez la règle.

## <a name="create-mail-flow-rules-for-office-365-message-encryption-without-microsoft-purview-message-encryption"></a>Créer des règles de flux de messagerie pour Office 365 Chiffrement des messages sans Chiffrement de messages Microsoft Purview

Si vous n’avez pas encore déplacé votre organisation vers Chiffrement de messages Microsoft Purview, Microsoft vous recommande d’établir un plan de déplacement dès qu’il est raisonnable pour votre organisation. Pour obtenir des instructions, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Sinon, consultez [Définition des règles de flux de messagerie pour Office 365 chiffrement des messages qui n’utilisent pas Chiffrement de messages Microsoft Purview](legacy-information-for-message-encryption.md#defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption).

## <a name="related-content"></a>Contenu associé

[Chiffrement dans Office 365](encryption.md)

[Configurer le chiffrement des messages Microsoft Purview](set-up-new-message-encryption-capabilities.md)

[Personnaliser les messages chiffrés](add-your-organization-brand-to-encrypted-messages.md)

[Règles de flux de messagerie (règles de transport) dans Exchange Online](/exchange/security-and-compliance/mail-flow-rules/mail-flow-rules)
