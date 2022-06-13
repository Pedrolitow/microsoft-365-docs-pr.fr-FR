---
title: Informations héritées pour le chiffrement de messages Office 365
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
ms.date: 05/22/2020
audience: ITPro
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: ''
search.appverid:
- MET150
ms.assetid: 5986b9e1-c824-4f8f-9b7d-a2b0ae2a7fe9
ms.collection:
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Découvrez comment effectuer la transition des fichiers hérités vers Office 365 chiffrement des messages (OME) pour votre organisation.
ms.openlocfilehash: 2d994e2c521f11a70c6946e2f1a9a3a1a5766ba3
ms.sourcegitcommit: 133bf9097785309da45df6f374a712a48b33f8e9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2022
ms.locfileid: "66014903"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Informations héritées pour le chiffrement de messages Office 365

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Si vous n’avez pas encore déplacé votre organisation vers Microsoft Purview Message Encryption, mais que vous avez déjà déployé OME, les informations contenues dans cet article s’appliquent à votre organisation. Microsoft vous recommande de planifier le passage à Microsoft Purview Message Encryption dès qu’il est raisonnable pour votre organisation. Pour obtenir des instructions, consultez [Configurer Microsoft Purview Message Encryption](set-up-new-message-encryption-capabilities.md). Si vous souhaitez en savoir plus sur la façon dont le nouveau chiffrement des messages commence par s’afficher, consultez [Chiffrement des messages](ome.md). Le reste de cet article fait référence au comportement OME avant la publication de Microsoft Purview Message Encryption.

Avec chiffrement de messages Office 365, votre organisation peur envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Office 365 Chiffrement des messages fonctionne avec Outlook.com, Yahoo, Gmail et d’autres services de messagerie. Le chiffrement des messages électroniques permet de s’assurer que seuls les destinataires prévus peuvent afficher le contenu des messages.

Voici quelques exemples :

- Un employé de banque envoie des relevés de carte de crédit aux clients
- Un représentant d’une compagnie d’assurance fournit les détails de la stratégie aux clients
- Un courtier hypothécaire demande des informations financières à un client pour une demande de prêt
- Un fournisseur de soins de santé envoie des informations sur les soins de santé aux patients
- Un avocat envoie des informations confidentielles à un client ou à un autre avocat

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Fonctionnement Office 365 Message Encryption sans les nouvelles fonctionnalités

Office 365 Message Encryption est un service en ligne basé sur Microsoft Azure Rights Management (Azure RMS). Avec Azure RMS, les administrateurs peuvent définir des règles de flux de messagerie pour déterminer les conditions de chiffrement. Par exemple, une règle peut exiger le chiffrement de tous les messages adressés à un destinataire spécifique.

Lorsqu’une personne envoie un e-mail dans Exchange Online qui correspond à une règle de chiffrement, le message est envoyé avec une pièce jointe HTML. Le destinataire ouvre la pièce jointe HTML et suit les instructions pour afficher le message chiffré sur le portail Office 365 Message Encryption. Le destinataire peut choisir d’afficher le message en se connectant avec un compte Microsoft ou un établissement professionnel ou scolaire associé à Office 365, ou à l’aide d’un code de passe unique. Les deux options vous permettent de vous assurer que seul le destinataire voulu peut afficher le message chiffré. Ce processus est très différent pour Le chiffrement des messages Microsoft Purview.

Le diagramme suivant résume le passage d’un message électronique dans le processus de chiffrement et de déchiffrement.

![Diagramme montrant le chemin d’accès d’un e-mail chiffré.](../media/O365-Office365MessageEncryption-Concept.png)

Pour plus d’informations, consultez [les informations de service pour les Office 365 chiffrement des messages hérités avant la publication de Microsoft Purview Message Encryption](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption"></a>Définition de règles de flux de messagerie pour Office 365 chiffrement des messages qui n’utilisent pas microsoft Purview Message Encryption

Pour activer Office 365 chiffrement des messages sans les nouvelles fonctionnalités, les administrateurs Exchange Online et Exchange Online Protection définissent Exchange règles de flux de messagerie. Ces règles déterminent dans quelles conditions les messages électroniques doivent être chiffrés, ainsi que les conditions de suppression du chiffrement des messages. Lorsqu’une action de chiffrement est définie pour une règle, le service effectue l’action sur tous les messages qui correspondent aux conditions de règle avant d’envoyer les messages.

Les règles de flux de messagerie sont flexibles, ce qui vous permet de combiner des conditions afin de répondre à des exigences de sécurité spécifiques dans une seule règle. Par exemple, vous pouvez créer une règle pour chiffrer tous les messages qui contiennent les mots-clés spécifiés et adressés à des destinataires externes. Le chiffrement de messages Office 365 chiffre également les réponses des destinataires des messages chiffrés, et vous pouvez créer une règle qui déchiffre ces réponses pour la commodité de vos utilisateurs de messagerie. De cette façon, les utilisateurs de votre organisation n’auront pas à se connecter au portail de chiffrement pour afficher les réponses.

Pour plus d’informations sur la création de règles de flux de messagerie Exchange, consultez [Définir des règles pour Office 365 chiffrement](define-mail-flow-rules-to-encrypt-email.md) des messages.

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-microsoft-purview-message-encryption"></a>Utiliser le centre d’administration pour créer une règle de flux de courrier pour chiffrer les messages électroniques sans Chiffrement des messages Microsoft Purview

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administrateur** .

3. Dans le Centre d'administration Microsoft 365, choisissez **Centres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**d’administration Exchange**</a>.

4. Dans le CENTRE, accédez aux **règles** de **flux** \> de messagerie et sélectionnez **l’icône Nouveau** ![nouveau.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation de la CAE, consultez [Exchange centre d’administration dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par exemple Chiffrer le courrier pour DrToniRamos@hotmail.com.

6. Dans l’option **Appliquer cette règle si**, sélectionnez une condition, puis entrez une valeur si nécessaire. Par exemple, pour chiffrer les messages adressés à DrToniRamos@hotmail.com :

   1. Dans **Appliquer cette règle si**, sélectionnez **le destinataire est**.

   2. Choisissez un nom existant dans la liste de contacts ou entrez une nouvelle adresse de messagerie dans la zone **vérifier les noms**.

      - Pour sélectionner un nom existant, sélectionnez-le dans la liste et cliquez sur **OK**.

      - Pour entrer un nouveau nom, tapez une adresse e-mail dans la case **à cocher des noms** , puis **cochez les noms** \> **OK**.

7. Pour ajouter d’autres conditions, choisissez **Plus d’options** , puis sélectionnez **Ajouter une condition** , puis sélectionnez dans la liste.

   Par exemple, pour appliquer la règle uniquement si le destinataire est en dehors de votre organisation, sélectionnez **Ajouter une condition** , puis sélectionnez **Le destinataire est externe/interne** \> **en dehors de l’organisation** \> **OK**.

8. Pour activer le chiffrement sans utiliser les nouvelles fonctionnalités OME, dans **Faire ce qui suit**, sélectionnez **Modifier la sécurité** \> **des messages Appliquer la version précédente d’OME**, puis **sélectionnez Enregistrer**.

   Si vous recevez une erreur indiquant que les licences IRM ne sont pas activées, vous n’utilisez pas OME hérité.

9. (Facultatif) Choisissez **ajouter une action** pour spécifier une autre action.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Utilisez Exchange Online PowerShell pour créer une règle de flux de messagerie pour chiffrer les messages électroniques sans les nouvelles fonctionnalités OME

1. Connectez-vous à Exchange Online PowerShell. Pour plus d'informations, reportez-vous à [Connexion à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

2. Créez une règle à l’aide de l’applet de commande **New-TransportRule** et _définissez_ le paramètre `$true`ApplyOME sur .

   Cet exemple nécessite que tous les e-mails envoyés à DrToniRamos@hotmail.com doivent être chiffrés.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   où :

   - Le nom unique de la nouvelle règle est « Encrypt rule for Dr Toni Sergio ».
   - Le paramètre _SentTo_ spécifie les destinataires du message (identifiés par nom, adresse e-mail, nom unique, etc.). Dans cet exemple, le destinataire est identifié par l’adresse e-mail « DrToniRamos@hotmail.com ».
   - Le paramètre _SentToScope_ spécifie l’emplacement des destinataires du message. Dans cet exemple, la boîte aux lettres du destinataire se trouve dans hotmail et ne fait pas partie de l’organisation. La valeur `NotInOrganization` est donc utilisée.

   Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Supprimer le chiffrement des réponses par e-mail chiffrées sans chiffrement de message Microsoft Purview

Lorsque vos utilisateurs de messagerie envoient des messages chiffrés, les destinataires de ces messages peuvent y répondre par des réponses chiffrées. Vous pouvez créer des règles de flux de messagerie pour supprimer automatiquement le chiffrement des réponses afin que les utilisateurs de messagerie de votre organisation n’aient pas à se connecter au portail de chiffrement pour les afficher. Vous pouvez utiliser les applets de commande EAC ou Exchange Online PowerShell pour définir ces règles. Vous pouvez déchiffrer les messages envoyés à partir de votre organisation ou les messages qui sont des réponses aux messages envoyés à partir de votre organisation. Vous ne pouvez pas déchiffrer les messages chiffrés provenant de l’extérieur de votre organisation.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Utiliser le centre d’administration pour créer une règle de suppression du chiffrement des réponses par e-mail chiffrées sans chiffrement de message Microsoft Purview

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administrateur** .

3. Dans le Centre d'administration Microsoft 365, choisissez **Centres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**d’administration Exchange**</a>.

4. Dans le CENTRE, accédez aux **règles** de **flux** \> de messagerie et sélectionnez **l’icône Nouveau** ![nouveau.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation de la CAE, consultez [Exchange centre d’administration dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par exemple Supprimer le chiffrement du courrier entrant.

6. Dans **Appliquer cette règle, si** vous sélectionnez les conditions dans lesquelles le chiffrement doit être supprimé des messages, telles que **le destinataire se trouve** \> **à l’intérieur de l’organisation**.

7. Dans **Faire ce qui suit**, sélectionnez **Modifier la sécurité** \> du message **Supprimer la version précédente d’OME**.

8. Sélectionnez **Enregistrer**.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Utiliser Exchange Online PowerShell pour créer une règle pour supprimer le chiffrement des réponses par e-mail chiffrées sans les nouvelles fonctionnalités OME

1. Connectez-vous à Exchange Online PowerShell. Pour plus d'informations, reportez-vous à [Connexion à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

2. Créez une règle à l’aide de l’applet de commande **New-TransportRule** et _définissez le paramètre RemoveOME_ sur `$true`.

   Cet exemple montre comment supprimer le chiffrement de tous les messages envoyés aux destinataires de l’organisation.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   où :

   - Le nom unique de la nouvelle règle est « Supprimer le chiffrement du courrier entrant ».
   - Le paramètre _SentToScope_ spécifie l’emplacement des destinataires du message. Dans cet exemple, la `InOrganization` valeur est utilisée, ce qui indique l’une des valeurs suivantes :
     - Le destinataire est une boîte aux lettres, un utilisateur de messagerie, un groupe ou un dossier public à extension messagerie dans votre organisation.
     - L’adresse e-mail du destinataire se trouve dans un domaine accepté configuré en tant que domaine faisant autorité ou domaine de relais interne dans votre organisation, _et_ le message a été envoyé ou reçu via une connexion authentifiée.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Envoi, affichage et réponse à des messages chiffrés sans les nouvelles fonctionnalités

Avec Office 365 chiffrement des messages, les messages électroniques sont chiffrés automatiquement, en fonction des règles définies par l’administrateur. Un e-mail contenant un message chiffré arrive dans la boîte de réception du destinataire avec un fichier HTML joint.

Les destinataires suivent les instructions du message pour ouvrir la pièce jointe et s’authentifier à l’aide d’un compte Microsoft ou d’un établissement professionnel ou scolaire associé à Office 365. Si les destinataires n’ont aucun compte, ils sont invités à créer un compte Microsoft qui leur permettra de se connecter pour afficher le message chiffré. Les destinataires peuvent également choisir d’obtenir un code de passe unique pour afficher le message. Après la connexion ou l’utilisation d’un code de passe unique, les destinataires peuvent afficher le message déchiffré et envoyer une réponse chiffrée.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Personnaliser des messages chiffrés avec Office 365 chiffrement des messages

En tant qu’administrateur Exchange Online et Exchange Online Protection, vous pouvez personnaliser vos messages chiffrés. Par exemple, vous pouvez ajouter la marque et le logo de votre entreprise, spécifier une introduction et ajouter du texte d’exclusion de responsabilité dans les messages chiffrés et dans le portail où les destinataires voient vos messages chiffrés. À l’aide Exchange Online applets de commande PowerShell, vous pouvez personnaliser les aspects suivants de l’expérience d’affichage pour les destinataires de messages électroniques chiffrés :

- Le texte d’introduction du message électronique contenant le message chiffré
- Le texte d’exclusion de responsabilité du message électronique contentant le message chiffré
- Le texte du portail qui apparaîtra dans le portail d’affichage des messages
- Le logo qui apparaîtra dans le message électronique et le portail d’affichage

Vous pouvez également rétablir l’apparence par défaut à tout moment.

L’exemple suivant montre un logo personnalisé pour ContosoPharma dans la pièce jointe d’un message électronique :

> [!div class="mx-imgBorder"]
> ![Exemple de la page de messages chiffrés d’affichage.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Pour personnaliser les messages électroniques de chiffrement et le portail de chiffrement avec la marque de votre organisation

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet de commande Set-OMEConfiguration comme décrit ici : [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) ou utilisez le tableau suivant pour obtenir des conseils.

   **Options de personnalisation du chiffrement**

   |Pour personnaliser cette fonctionnalité de l’expérience de chiffrement|Utiliser ces commandes PowerShell Exchange Online|
   |---|---|
   |Texte par défaut qui accompagne les messages électroniques chiffrés <p> Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Formats de fichier pris en charge : .png, .jpg, .bmp ou .tiff <p> Taille optimale du fichier de logo : moins de 40 Ko <p> Taille optimale de l’image de logo : 170x70 pixels|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Pour supprimer les personnalisations de marque des messages électroniques de chiffrement et du portail de chiffrement

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet de commande Set-OMEConfiguration comme décrit ici : [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). Pour supprimer les personnalisations de marque de votre organisation des valeurs DisclaimerText, EmailText et PortalText, définissez la valeur sur une chaîne vide. `""` Pour toutes les valeurs d’image, telles que Logo, définissez la valeur sur `"$null"`.

   **Options de personnalisation du chiffrement**

   |Pour annuler cette fonctionnalité de chiffrement et rétablir le texte et l’image par défaut|Utiliser ces commandes PowerShell Exchange Online|
   |---|---|
   |Texte par défaut qui accompagne les messages électroniques chiffrés <p> Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Exemple de retour à la valeur par défaut :** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Exemple de retour à la valeur par défaut :** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Informations de service pour le chiffrement des messages Office 365 hérité avant la publication des nouvelles fonctionnalités OME
<a name="LegacyServiceInfo"> </a>

Le tableau suivant fournit des détails techniques pour le service Office 365 Message Encryption avant la publication de Microsoft Purview Message Encryption.

|Détails du service|Description|
|---|---|
|Exigences relatives aux périphériques client|Les messages chiffrés peuvent être affichés sur tous les périphériques client, tant que la pièce jointe HTML peut être ouverte dans un navigateur moderne qui prend en charge la publication de formulaire.|
|Algorithme de chiffrement et conformité aux normes FIPS (Federal Information Processing Standards)|Le chiffrement de messages Office 365 utilise les mêmes clés de chiffrement que la gestion des droits relatifs à l’information (IRM) de Windows Azure et prend en charge le mode de chiffrement 2 (clé 2K pour RSA et clé 256 bits pour les systèmes SHA-1). Pour plus d’informations sur les modes de chiffrement IRM sous-jacents, consultez [Modes de chiffrement AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Types de messages pris en charge|Le chiffrement de messages Office 365 est uniquement pris en charge pour les éléments avec un ID de classe de message **IPM.Note**. Pour plus d’informations, consultez [Types d’éléments et classes de message](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Tailles limites des messages|Le chiffrement de messages Office 365 permet de chiffrer des messages d’une taille maximale de 25 Mo. Pour plus d’informations sur les limites de taille des messages, consultez [Exchange Online Limites](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|Exchange Online stratégies de rétention des e-mails|Exchange Online ne stocke pas les messages chiffrés.|
|Prise en charge linguistique pour le chiffrement de messages Office 365|Office 365 Chiffrement des messages prend en charge Microsoft 365 langues, comme suit : <p> Les messages électroniques entrants et les fichiers HTML joints sont localisés en fonction des paramètres de langue de l’expéditeur. <p> Le portail d’affichage est localisé en fonction des paramètres de navigateur du destinataire. <p> Le corps (contenu) du message chiffré n’est pas localisé.|
|Informations de confidentialité pour le portail OME et l’application Visionneuse OME|La [Office 365 Messaging Encryption Portal privacy statement](https://privacy.microsoft.com/privacystatement) fournit des informations détaillées sur ce que fait et ne fait pas Microsoft avec vos informations privées.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Forum aux questions sur l’OME hérité
<a name="LegacyServiceInfo"> </a>

Vous avez des questions sur Office 365 chiffrement des messages ? Voici les réponses à certaines questions fréquemment posées. Si vous ne trouvez pas ce dont vous avez besoin, consultez les [forums Microsoft Tech Community pour Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **Q. Mes utilisateurs envoient des messages électroniques chiffrés à des destinataires extérieurs à notre organisation. Les destinataires externes ont-ils quelque chose à faire pour lire et répondre aux messages électroniques chiffrés avec Office 365 Chiffrement des messages ?**

Les destinataires extérieurs à votre organisation qui reçoivent Microsoft 365 messages chiffrés peuvent les afficher de l’une des deux manières suivantes :

- En vous connectant avec un compte Microsoft ou un compte professionnel ou scolaire associé à Office 365.

- À l’aide d’un code de passe unique.

 **Q. Les messages chiffrés Microsoft 365 sont-ils stockés dans le cloud ou sur des serveurs Microsoft ?**

Non, les messages chiffrés sont conservés sur le système de messagerie du destinataire, et lorsque le destinataire ouvre le message, il est temporairement publié pour être affiché sur les serveurs Microsoft. Les messages électroniques n’y sont pas stockés.

 **Q. Puis-je personnaliser les messages chiffrés avec ma marque ?**

Oui. Vous pouvez utiliser Exchange Online applets de commande PowerShell pour personnaliser le texte par défaut qui apparaît en haut des messages électroniques chiffrés, le texte d’exclusion de responsabilité et le logo que vous souhaitez utiliser pour le message électronique et le portail de chiffrement. Cette fonctionnalité est désormais disponible dans OMEv2. Pour plus d’informations, voir [Add branding to encrypted messages](add-your-organization-brand-to-encrypted-messages.md).

 **Q. Le service exige-t-il une licence pour chaque utilisateur de mon organisation ?**

Une licence est obligatoire pour chaque utilisateur de l’organisation qui envoie des messages chiffrés.

 **Q. Les destinataires externes exigent-ils des abonnements ?**

Non, les destinataires externes n’ont pas besoin d’un abonnement pour lire ou répondre à des messages chiffrés.

 **Q. En quoi le chiffrement des messages Office 365 est-il différent de Rights Management Services (RMS) ?**

RMS fournit des fonctionnalités de protection des droits relatifs à l’information pour les e-mails internes d’une organisation en fournissant des modèles intégrés, tels que : Ne pas transférer et Confidentiel de l’entreprise. Le chiffrement de messages Office 365 prend en charge le chiffrement des messages électroniques pour ceux envoyés à des destinataires externes et internes.

 **Q. En quoi le chiffrement des messages Office 365 est-il différent de S/MIME ?**

S/MIME est essentiellement une technologie de chiffrement côté client et exige une gestion de certificats et une infrastructure de publication complexes. Office 365 Chiffrement des messages utilise des règles de flux de messagerie (également appelées règles de transport) et ne dépend pas de la publication de certificats.

 **Q. Puis-je lire les messages chiffrés sur des appareils mobiles ?**

Oui, vous pouvez afficher les messages sur Android et iOS en téléchargeant les applications OME Viewer à partir du Google Play Store et de l’Apple App Store. Ouvrez la pièce jointe HTML dans l’application OME Viewer, puis suivez les instructions pour ouvrir votre message chiffré. Pour les autres appareils mobiles, vous pouvez ouvrir la pièce jointe HTML à condition que votre client de messagerie prenne en charge la publication de formulaire.

 **Q. Les réponses et les messages transférés sont-ils chiffrés ?**

Oui. Les réponses restent chiffrées pendant toute la durée du thread.

 **Q. Office 365 chiffrement des messages assure-t-il la localisation ?**

Le contenu HTML et les messages électroniques entrants sont localisés en fonction des paramètres de messagerie de l’expéditeur. Le portail d’affichage est localisé en fonction des paramètres de navigateur du destinataire. Cependant, le corps réel (le contenu) du message chiffré n’est pas localisé.

 **Q. Quelle méthode de chiffrement est utilisée pour Office 365 chiffrement des messages ?**

Office 365 Message Encryption utilise Rights Management Services (RMS) comme infrastructure de chiffrement. La méthode de chiffrement utilisée dépend de l’endroit où vous obtenez les clés RMS servant à chiffrer et déchiffrer les messages.

- Si vous utilisez Microsoft Azure RMS pour obtenir les clés, le mode de chiffrement 2 est utilisé. Le mode de chiffrement 2 est un processus de chiffrement AD RMS amélioré et mis à jour. Il prend en charge RSA 2048 pour la signature et le chiffrement, et SHA 256 pour la signature.

- Si vous utilisez Active Directory (AD) RMS pour obtenir les clés, le mode de chiffrement 1 ou 2 est utilisé. La méthode utilisée dépend de votre déploiement AD RMS local. Le mode de chiffrement 1 est le processus de chiffrement d’origine AD RMS. Il prend en charge RSA 1024 pour la signature et le chiffrement, et SHA-1 pour la signature. Ce mode est encore pris en charge par toutes les versions actuelles de RMS.

Pour plus d’informations, consultez [Modes de chiffrement AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**Q. Pourquoi certains messages chiffrés disent-ils provenir de** Office365@messaging.microsoft.com ?

Lorsqu’une réponse chiffrée est envoyée à partir du portail de chiffrement ou via l’application Visionneuse OME, l’adresse de messagerie de l’expéditeur est définie sur Office365@messaging.microsoft.com, car le message chiffré est envoyé par le biais d’un point de terminaison Microsoft. Cela permet d’éviter que les messages chiffrés soient marqués comme courrier indésirable. Le nom affiché dans le message électronique et l’adresse dans le portail de chiffrement ne sont pas modifiés en raison de cet étiquetage. En outre, cet étiquetage s’applique uniquement aux messages envoyés via le portail, et non par le biais de n’importe quel autre client de messagerie.

 **Q. Je suis abonné Exchange chiffrement hébergé (EHE). Où puis-je en savoir plus sur la mise à niveau vers Office 365 Chiffrement des messages ?**

Tous les clients EHE ont été mis à niveau vers le chiffrement de messages Office 365. Pour plus d’informations, visitez le [Exchange Centre de mise à niveau du chiffrement hébergé](../security/office-365-security/exchange-online-protection-overview.md).

 **Q. Dois-je ouvrir des URL, des adresses IP ou des ports dans le pare-feu de mon organisation pour prendre en charge Office 365 chiffrement des messages ?**

Oui. Vous devez ajouter des URL à la liste d’adresses autorisées pour Exchange Online afin que votre organisation permette l’authentification des messages chiffrés par Office 365. Pour obtenir la liste des URL Exchange Online, consultez [Microsoft 365 URL et plages d’adresses IP](../enterprise/urls-and-ip-address-ranges.md).

 **Q. À combien de destinataires puis-je envoyer un message chiffré Microsoft 365 ?**

La limite de destinataires est de 500 destinataires par message, ou, lorsqu’elle est combinée après l’extension de la liste de distribution, 11 980 caractères dans le champ **À** du message, selon la première.

 **Q : Est-il possible de révoquer un message envoyé à un destinataire particulier ?**

Non. Vous ne pouvez pas révoquer un message à une personne particulière après son envoi.

 **Q : Puis-je afficher un rapport des messages chiffrés qui ont été reçus et lus ?**

Il n’existe pas de rapport qui indique si un message chiffré a été affiché, mais il existe Microsoft 365 rapports disponibles que vous pouvez utiliser pour déterminer le nombre de messages correspondant à une règle de flux de courrier spécifique (également appelée règle de transport), par exemple.

 **Q. Que fait Microsoft des informations que je fournis par le biais du portail OME et de l’application Visionneuse OME ?**

La [déclaration de confidentialité du portail de chiffrement de messagerie Office 365](https://privacy.microsoft.com/privacystatement) fournit des informations détaillées sur ce que Microsoft fait et ne fait pas avec vos informations privées.

**Q. Que dois-je faire si je ne reçois pas le code de passe unique après l’avoir demandé ?**

Tout d’abord, vérifiez le dossier courrier indésirable ou courrier indésirable dans votre client de messagerie. Les paramètres DKIM et DMARC de votre organisation peuvent entraîner le filtrage de ces e-mails en tant que courrier indésirable.

Ensuite, vérifiez la quarantaine dans le Centre de sécurité & conformité. Souvent, les messages contenant un code de passe unique, en particulier les premiers que votre organisation reçoit, se retrouvent en quarantaine.
