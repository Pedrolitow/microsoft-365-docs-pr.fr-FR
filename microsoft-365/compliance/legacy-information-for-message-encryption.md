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
- purview-compliance
- tier3
ms.custom:
- seo-marvel-apr2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Découvrez comment migrer des fichiers hérités vers Office 365 Chiffrement des messages (OME) pour votre organisation.
ms.openlocfilehash: ef6dd13ee42d83a671486a502667b4ccaa9fea39
ms.sourcegitcommit: a88aadf5786f1bd9e5bae763f603a2b690473322
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2022
ms.locfileid: "68817589"
---
# <a name="legacy-information-for-office-365-message-encryption"></a>Informations héritées pour le chiffrement de messages Office 365

Si vous n’avez pas encore déplacé votre organisation vers Chiffrement de messages Microsoft Purview, mais que vous avez déjà déployé OME, les informations contenues dans cet article s’appliquent à votre organisation. Microsoft vous recommande de planifier le passage à Chiffrement de messages Microsoft Purview dès que cela est raisonnable pour votre organisation. Pour obtenir des instructions, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Si vous souhaitez en savoir plus sur la façon dont le nouveau chiffrement de message commence, consultez [Chiffrement des messages](ome.md). Le reste de cet article fait référence au comportement OME avant la publication de Chiffrement de messages Microsoft Purview.

Avec chiffrement de messages Office 365, votre organisation peur envoyer et recevoir des messages chiffrés entre des personnes à l’intérieur et à l’extérieur de votre organisation. Office 365 Message Encryption fonctionne avec Outlook.com, Yahoo, Gmail et d’autres services de messagerie. Le chiffrement de messages vous permet de vous assurer que seuls les destinataires prévus peuvent afficher le contenu des courriers.

Voici quelques exemples :

- Un employé de la banque envoie des relevés de carte de crédit aux clients
- Un représentant d’une compagnie d’assurance fournit les détails de la police aux clients
- Un courtier en prêts hypothécaires demande des informations financières à un client pour une demande de prêt
- Un fournisseur de soins de santé envoie des informations sur les soins de santé aux patients
- Un avocat envoie des informations confidentielles à un client ou à un autre avocat

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="how-office-365-message-encryption-works-without-the-new-capabilities"></a>Fonctionnement de Office 365 chiffrement des messages sans les nouvelles fonctionnalités

Office 365 Message Encryption est un service en ligne basé sur Microsoft Azure Rights Management (Azure RMS). Avec Azure RMS, les administrateurs peuvent définir des règles de flux de messagerie pour déterminer les conditions de chiffrement. Par exemple, une règle peut exiger le chiffrement de tous les messages adressés à un destinataire spécifique.

Lorsqu’une personne envoie un message électronique dans Exchange Online qui correspond à une règle de chiffrement, le message est envoyé avec une pièce jointe HTML. Le destinataire ouvre la pièce jointe HTML et suit les instructions pour afficher le message chiffré sur le portail Office 365 Message Encryption. Le destinataire peut choisir d’afficher le message en se connectant avec un compte Microsoft ou un établissement professionnel ou scolaire associé à Office 365, ou en utilisant un code de passe à usage unique. Les deux options vous permettent de vous assurer que seul le destinataire voulu peut afficher le message chiffré. Ce processus est très différent pour Chiffrement de messages Microsoft Purview.

Le diagramme suivant résume le passage d’un message électronique dans le processus de chiffrement et de déchiffrement.

![Diagramme montrant le chemin d’un e-mail chiffré.](../media/O365-Office365MessageEncryption-Concept.png)

Pour plus d’informations, consultez [Informations de service pour le chiffrement de messages Office 365 hérité avant la publication de Chiffrement de messages Microsoft Purview](legacy-information-for-message-encryption.md#LegacyServiceInfo).

## <a name="defining-mail-flow-rules-for-office-365-message-encryption-that-dont-use-microsoft-purview-message-encryption"></a>Définition de règles de flux de courrier pour Office 365 chiffrement des messages qui n’utilisent pas Chiffrement de messages Microsoft Purview

Pour activer Office 365 chiffrement des messages sans les nouvelles fonctionnalités, les administrateurs Exchange Online et Exchange Online Protection définissent des règles de flux de messagerie Exchange. Ces règles déterminent dans quelles conditions les messages électroniques doivent être chiffrés, ainsi que les conditions de suppression du chiffrement des messages. Lorsqu’une action de chiffrement est définie pour une règle, le service effectue l’action sur tous les messages qui correspondent aux conditions de la règle avant d’envoyer les messages.

Les règles de flux de courrier sont flexibles, ce qui vous permet de combiner des conditions afin de pouvoir répondre à des exigences de sécurité spécifiques dans une seule règle. Par exemple, vous pouvez créer une règle pour chiffrer tous les messages qui contiennent les mots-clés spécifiés et adressés à des destinataires externes. Le chiffrement de messages Office 365 chiffre également les réponses des destinataires des messages chiffrés, et vous pouvez créer une règle qui déchiffre ces réponses pour la commodité de vos utilisateurs de messagerie. De cette façon, les utilisateurs de votre organisation n’auront pas à se connecter au portail de chiffrement pour afficher les réponses.

Pour plus d’informations sur la création de règles de flux de messagerie Exchange, consultez [Définir des règles pour Office 365 chiffrement des messages](define-mail-flow-rules-to-encrypt-email.md).

### <a name="use-the-eac-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-microsoft-purview-message-encryption"></a>Utilisez le CENTRE d’administration Exchange pour créer une règle de flux de courrier pour chiffrer les messages électroniques sans Chiffrement de messages Microsoft Purview

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administration**.

3. Dans le Centre d'administration Microsoft 365, choisissez **Administration centres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. Dans le Centre d’administration Exchange, accédez à **Règles** de **flux** \> de courrier et sélectionnez **Nouvelle icône Nouveau**![.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation du Centre [d’administration Exchange, consultez Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par exemple Chiffrer le courrier pour DrToniRamos@hotmail.com.

6. Dans l’option **Appliquer cette règle si**, sélectionnez une condition, puis entrez une valeur si nécessaire. Par exemple, pour chiffrer les messages adressés à DrToniRamos@hotmail.com :

   1. Dans **Appliquer cette règle si**, sélectionnez **le destinataire est**.

   2. Choisissez un nom existant dans la liste de contacts ou entrez une nouvelle adresse de messagerie dans la zone **vérifier les noms**.

      - Pour sélectionner un nom existant, sélectionnez-le dans la liste et cliquez sur **OK**.

      - Pour entrer un nouveau nom, tapez une adresse e-mail dans la case **à cocher noms** , puis sélectionnez **Vérifier les noms** \> **OK**.

7. Pour ajouter d’autres conditions, choisissez **Plus d’options** , puis sélectionnez **Ajouter une condition** et sélectionnez dans la liste.

   Par exemple, pour appliquer la règle uniquement si le destinataire est en dehors de votre organisation, sélectionnez **Ajouter une condition** , puis sélectionnez **Le destinataire est externe/interne** \> **En dehors de l’organisation** \> **OK**.

8. Pour activer le chiffrement sans utiliser les nouvelles fonctionnalités OME, dans **Procédez comme suit**, sélectionnez **Modifier la sécurité** \> **des messages Appliquer la version précédente d’OME**, puis choisissez **Enregistrer**.

   Si vous recevez une erreur indiquant que la gestion des licences IRM n’est pas activée, vous n’utilisez pas OME hérité.

9. (Facultatif) Choisissez **Ajouter une action** pour spécifier une autre action.

### <a name="use-exchange-online-powershell-to-create-a-mail-flow-rule-for-encrypting-email-messages-without-the-new-ome-capabilities"></a>Utiliser Exchange Online PowerShell pour créer une règle de flux de courrier pour chiffrer les messages électroniques sans les nouvelles fonctionnalités OME

1. Connectez-vous à Exchange Online PowerShell. Pour plus d'informations, reportez-vous à [Connexion à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

2. Créez une règle à l’aide de l’applet **de commande New-TransportRule** et _définissez le paramètre ApplyOME_ sur .`$true`

   Cet exemple nécessite que tous les messages électroniques envoyés à DrToniRamos@hotmail.com soient chiffrés.

   ```powershell
   New-TransportRule -Name "Encrypt rule for Dr Toni Ramos" -SentTo "DrToniRamos@hotmail.com" -SentToScope "NotinOrganization" -ApplyOME $true
   ```

   où :

   - Le nom unique de la nouvelle règle est « Encrypt rule for Dr Toni Ramos ».
   - Le paramètre _SentTo_ spécifie les destinataires du message (identifiés par le nom, l’adresse e-mail, le nom unique, etc.). Dans cet exemple, le destinataire est identifié par l’adresse e-mail « DrToniRamos@hotmail.com ».
   - Le paramètre _SentToScope_ spécifie l’emplacement des destinataires du message. Dans cet exemple, la boîte aux lettres du destinataire se trouve dans hotmail et ne fait pas partie de l’organisation. La valeur `NotInOrganization` est donc utilisée.

   Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](/powershell/module/exchange/New-TransportRule).

### <a name="remove-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Supprimer le chiffrement des réponses par e-mail chiffrées sans Chiffrement de messages Microsoft Purview

Lorsque vos utilisateurs de messagerie envoient des messages chiffrés, les destinataires de ces messages peuvent y répondre par des réponses chiffrées. Vous pouvez créer des règles de flux de courrier pour supprimer automatiquement le chiffrement des réponses afin que les utilisateurs de courrier de votre organisation n’aient pas à se connecter au portail de chiffrement pour les afficher. Vous pouvez utiliser le CAE ou Exchange Online applets de commande PowerShell pour définir ces règles. Vous pouvez déchiffrer les messages envoyés à partir de votre organisation ou les messages qui sont des réponses aux messages envoyés à partir de votre organisation. Vous ne pouvez pas déchiffrer les messages chiffrés provenant de l’extérieur de votre organisation.

#### <a name="use-the-eac-to-create-a-rule-for-removing-encryption-from-email-replies-encrypted-without-microsoft-purview-message-encryption"></a>Utilisez le CAE pour créer une règle permettant de supprimer le chiffrement des réponses aux e-mails chiffrées sans Chiffrement de messages Microsoft Purview

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administration**.

3. Dans le Centre d'administration Microsoft 365, choisissez **Administration centres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=2059104" target="_blank">**Exchange**</a>.

4. Dans le Centre d’administration Exchange, accédez à **Règles** de **flux** \> de courrier et sélectionnez **Nouvelle icône Nouveau**![.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation du Centre [d’administration Exchange, consultez Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par exemple Supprimer le chiffrement du courrier entrant.

6. Dans **Appliquer cette règle, sélectionnez** les conditions dans lesquelles le chiffrement doit être supprimé des messages, par exemple **Le destinataire se trouve à** \> **l’intérieur de l’organisation**.

7. Dans **Procédez comme suit**, sélectionnez **Modifier la sécurité** \> du message **Supprimer la version précédente d’OME**.

8. Sélectionnez **Enregistrer**.

#### <a name="use-exchange-online-powershell-to-create-a-rule-to-remove-encryption-from-email-replies-encrypted-without-the-new-ome-capabilities"></a>Utiliser Exchange Online PowerShell pour créer une règle pour supprimer le chiffrement des réponses aux e-mails chiffrées sans les nouvelles fonctionnalités OME

1. Connectez-vous à Exchange Online PowerShell. Pour plus d'informations, reportez-vous à [Connexion à Exchange Online](/powershell/exchange/connect-to-exchange-online-powershell).

2. Créez une règle à l’aide de l’applet **de commande New-TransportRule** et définissez le paramètre _RemoveOME_ sur `$true`.

   Cet exemple supprime le chiffrement de tous les messages envoyés aux destinataires de l’organisation.

   ```powershell
   New-TransportRule -Name "Remove encryption from incoming mail" -SentToScope "InOrganization" -RemoveOME $true
   ```

   où :

   - Le nom unique de la nouvelle règle est « Supprimer le chiffrement du courrier entrant ».
   - Le paramètre _SentToScope_ spécifie l’emplacement des destinataires du message. Dans cet exemple, la `InOrganization` valeur est utilisée, ce qui indique l’un des éléments suivants :
     - Le destinataire est une boîte aux lettres, un utilisateur de messagerie, un groupe ou un dossier public à extension messagerie dans votre organisation.
     - L’adresse e-mail du destinataire se trouve dans un domaine accepté configuré en tant que domaine faisant autorité ou domaine de relais interne dans votre organisation, _et_ le message a été envoyé ou reçu via une connexion authentifiée.

Pour obtenir des informations détaillées sur la syntaxe et les paramètres, voir [New-TransportRule](/powershell/module/exchange/New-TransportRule).

## <a name="sending-viewing-and-replying-to-messages-encrypted-without-the-new-capabilities"></a>Envoi, affichage et réponse aux messages chiffrés sans les nouvelles fonctionnalités

Avec Office 365 chiffrement des messages, les messages électroniques sont chiffrés automatiquement, en fonction de règles définies par l’administrateur. Un e-mail contenant un message chiffré arrive dans la boîte de réception du destinataire avec un fichier HTML joint.

Les destinataires suivent les instructions du message pour ouvrir la pièce jointe et s’authentifier à l’aide d’un compte Microsoft ou d’un compte professionnel ou scolaire associé à Office 365. Si les destinataires n’ont aucun compte, ils sont invités à créer un compte Microsoft qui leur permettra de se connecter pour afficher le message chiffré. Les destinataires peuvent également choisir d’obtenir un code de passe à usage unique pour afficher le message. Après s’être connectés ou à l’aide d’un code de passe à usage unique, les destinataires peuvent afficher le message déchiffré et envoyer une réponse chiffrée.

## <a name="customize-encrypted-messages-with-office-365-message-encryption"></a>Personnaliser les messages chiffrés avec Office 365 chiffrement des messages

En tant qu’administrateur Exchange Online et Exchange Online Protection, vous pouvez personnaliser vos messages chiffrés. Par exemple, vous pouvez ajouter la marque et le logo de votre entreprise, spécifier une introduction et ajouter un texte d’exclusion de responsabilité dans les messages chiffrés et dans le portail où les destinataires affichent vos messages chiffrés. À l’aide Exchange Online applets de commande PowerShell, vous pouvez personnaliser les aspects suivants de l’expérience d’affichage pour les destinataires de messages électroniques chiffrés :

- Le texte d’introduction du message électronique contenant le message chiffré
- Le texte d’exclusion de responsabilité du message électronique contentant le message chiffré
- Le texte du portail qui apparaîtra dans le portail d’affichage des messages
- Le logo qui apparaîtra dans le message électronique et le portail d’affichage

Vous pouvez également rétablir l’apparence par défaut à tout moment.

L’exemple suivant montre un logo personnalisé pour ContosoPharma dans la pièce jointe d’un message électronique :

> [!div class="mx-imgBorder"]
> ![Exemple de la page afficher les messages chiffrés.](../media/TA-OME-3attachment2.jpg)

### <a name="to-customize-encryption-email-messages-and-the-encryption-portal-with-your-organizations-brand"></a>Pour personnaliser les messages électroniques de chiffrement et le portail de chiffrement avec la marque de votre organisation

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet de commande Set-OMEConfiguration comme décrit ici : [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) ou utilisez le tableau suivant pour obtenir des conseils.

   **Options de personnalisation du chiffrement**

   |Pour personnaliser cette fonctionnalité de l’expérience de chiffrement|Utiliser ces commandes Exchange Online PowerShell|
   |---|---|
   |Texte par défaut qui accompagne les messages électroniques chiffrés <p> Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<string of up to 1024 characters>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system"`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<your disclaimer statement, string of up to 1024 characters>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText "This message is confidential for the use of the addressee only"`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<text for your portal, string of up to 128 characters>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal"`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <Byte[]>` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME configuration" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Formats de fichier pris en charge : .png, .jpg, .bmp ou .tiff <p> Taille optimale du fichier de logo : moins de 40 Ko <p> Taille optimale de l’image de logo : 170x70 pixels|

### <a name="to-remove-brand-customizations-from-encryption-email-messages-and-the-encryption-portal"></a>Pour supprimer les personnalisations de marque des messages électroniques de chiffrement et du portail de chiffrement

1. [Connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet de commande Set-OMEConfiguration comme décrit ici : [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration). Pour supprimer les personnalisations personnalisées de votre organisation des valeurs DisclaimerText, EmailText et PortalText, définissez la valeur sur une chaîne vide, `""`. Pour toutes les valeurs d’image, telles que Logo, définissez la valeur sur `"$null"`.

   **Options de personnalisation du chiffrement**

   |Pour annuler cette fonctionnalité de chiffrement et rétablir le texte et l’image par défaut|Utiliser ces commandes Exchange Online PowerShell|
   |---|---|
   |Texte par défaut qui accompagne les messages électroniques chiffrés <p> Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -EmailText "<empty string>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré <p> |`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> DisclaimerText "<empty string>"` <p> **Exemple :** `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -PortalText "<empty string>"` <p> **Exemple de rétablissement de la valeur par défaut :** `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity <OMEConfigurationIdParameter> -Image <"$null">` <p> **Exemple de rétablissement de la valeur par défaut :** `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|

## <a name="service-information-for-legacy-office-365-message-encryption-prior-to-the-release-of-the-new-ome-capabilities"></a>Informations de service pour le chiffrement de messages Office 365 hérité avant la publication des nouvelles fonctionnalités OME
<a name="LegacyServiceInfo"> </a>

Le tableau suivant fournit des détails techniques pour le service de chiffrement de messages Office 365 avant la publication de Chiffrement de messages Microsoft Purview.

|Détails du service|Description|
|---|---|
|Exigences relatives aux périphériques client|Les messages chiffrés peuvent être affichés sur tous les périphériques client, tant que la pièce jointe HTML peut être ouverte dans un navigateur moderne qui prend en charge la publication de formulaire.|
|Algorithme de chiffrement et conformité aux normes FIPS (Federal Information Processing Standards)|Le chiffrement de messages Office 365 utilise les mêmes clés de chiffrement que la gestion des droits relatifs à l’information (IRM) de Windows Azure et prend en charge le mode de chiffrement 2 (clé 2K pour RSA et clé 256 bits pour les systèmes SHA-1). Pour plus d’informations sur les modes de chiffrement IRM sous-jacents, consultez [Modes de chiffrement AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).|
|Types de messages pris en charge|Le chiffrement de messages Office 365 est uniquement pris en charge pour les éléments avec un ID de classe de message **IPM.Note**. Pour plus d’informations, consultez [Types d’éléments et classes de messages](/office/vba/outlook/Concepts/Forms/item-types-and-message-classes).|
|Tailles limites des messages|Le chiffrement de messages Office 365 permet de chiffrer des messages d’une taille maximale de 25 Mo. Pour plus d’informations sur les limites de taille des messages, consultez [limites Exchange Online](/office365/servicedescriptions/exchange-online-service-description/exchange-online-limits).|
|Exchange Online stratégies de rétention des e-mails|Exchange Online ne stocke pas les messages chiffrés.|
|Prise en charge linguistique pour le chiffrement de messages Office 365|Office 365 Chiffrement des messages prend en charge les langues Microsoft 365, comme suit : <p> Les messages électroniques entrants et les fichiers HTML joints sont localisés en fonction des paramètres de langue de l’expéditeur. <p> Le portail d’affichage est localisé en fonction des paramètres de navigateur du destinataire. <p> Le corps (contenu) du message chiffré n’est pas localisé.|
|Informations de confidentialité pour le portail OME et l’application Visionneuse OME|La [Office 365 Messaging Encryption Portal privacy statement](https://privacy.microsoft.com/privacystatement) fournit des informations détaillées sur ce que fait et ne fait pas Microsoft avec vos informations privées.|

## <a name="frequently-asked-questions-about-legacy-ome"></a>Questions fréquentes (FAQ) sur OME hérité
<a name="LegacyServiceInfo"> </a>

Vous avez des questions sur Office 365 chiffrement des messages ? Voici les réponses à certaines questions fréquemment posées. Si vous ne trouvez pas ce dont vous avez besoin, consultez les [forums Microsoft Tech Community pour Office 365](https://techcommunity.microsoft.com/t5/Office-365/ct-p/Office365).

 **Q. Mes utilisateurs envoient des messages électroniques chiffrés à des destinataires extérieurs à notre organisation. Y a-t-il quelque chose que les destinataires externes doivent faire pour lire et répondre aux messages électroniques chiffrés avec Office 365 chiffrement des messages ?**

Les destinataires extérieurs à votre organisation qui reçoivent des messages chiffrés Microsoft 365 peuvent les afficher de l’une des deux manières suivantes :

- En vous connectant avec un compte Microsoft ou un compte professionnel ou scolaire associé à Office 365.

- En utilisant un code de passe à usage unique.

 **Q. Les messages chiffrés Microsoft 365 sont-ils stockés dans le cloud ou sur des serveurs Microsoft ?**

Non, les messages chiffrés sont conservés sur le système de messagerie du destinataire et, lorsque le destinataire ouvre le message, il est temporairement publié pour affichage sur les serveurs Microsoft. Les messages électroniques n’y sont pas stockés.

 **Q. Puis-je personnaliser les messages chiffrés avec ma marque ?**

Oui. Vous pouvez utiliser Exchange Online applets de commande PowerShell pour personnaliser le texte par défaut qui apparaît en haut des messages électroniques chiffrés, le texte d’exclusion de responsabilité et le logo que vous souhaitez utiliser pour le message électronique et le portail de chiffrement. Cette fonctionnalité est désormais disponible dans OMEv2. Pour plus d’informations, voir [Add branding to encrypted messages](add-your-organization-brand-to-encrypted-messages.md).

 **Q. Le service exige-t-il une licence pour chaque utilisateur de mon organisation ?**

Une licence est obligatoire pour chaque utilisateur de l’organisation qui envoie des messages chiffrés.

 **Q. Les destinataires externes exigent-ils des abonnements ?**

Non, les destinataires externes n’ont pas besoin d’un abonnement pour lire ou répondre à des messages chiffrés.

 **Q. En quoi Office 365 chiffrement des messages diffère-t-il de Rights Management Services (RMS) ?**

RMS fournit des fonctionnalités de protection des droits relatifs à l’information pour les e-mails internes d’une organisation en fournissant des modèles intégrés, tels que : Ne pas transférer et Confidentialité de l’entreprise. Le chiffrement de messages Office 365 prend en charge le chiffrement des messages électroniques pour ceux envoyés à des destinataires externes et internes.

 **Q. En quoi Office 365 chiffrement de message est-il différent de S/MIME ?**

S/MIME est essentiellement une technologie de chiffrement côté client et exige une gestion de certificats et une infrastructure de publication complexes. Office 365 Chiffrement des messages utilise des règles de flux de messagerie (également appelées règles de transport) et ne dépend pas de la publication de certificat.

 **Q. Puis-je lire les messages chiffrés sur des appareils mobiles ?**

Oui, vous pouvez afficher les messages sur Android et iOS en téléchargeant les applications OME Viewer à partir du Google Play Store et de l’Apple App Store. Ouvrez la pièce jointe HTML dans l’application OME Viewer, puis suivez les instructions pour ouvrir votre message chiffré. Pour les autres appareils mobiles, vous pouvez ouvrir la pièce jointe HTML à condition que votre client de messagerie prenne en charge la publication de formulaire.

 **Q. Les réponses et les messages transférés sont-ils chiffrés ?**

Oui. Les réponses restent chiffrées pendant toute la durée du thread.

 **Q. Le chiffrement des messages Office 365 assure-t-il la localisation ?**

Incoming email and HTML content is localized based on sender email settings. The viewing portal is localized based on recipient's browser settings. However, the actual body (content) of encrypted message isn't localized.

 **Q. Quelle méthode de chiffrement est utilisée pour Office 365 chiffrement des messages ?**

Office 365 Message Encryption utilise les services RMS (Rights Management Services) comme infrastructure de chiffrement. La méthode de chiffrement utilisée dépend de l’endroit où vous obtenez les clés RMS servant à chiffrer et déchiffrer les messages.

- Si vous utilisez Microsoft Azure RMS pour obtenir les clés, le mode de chiffrement 2 est utilisé. Le mode de chiffrement 2 est un processus de chiffrement AD RMS amélioré et mis à jour. Il prend en charge RSA 2048 pour la signature et le chiffrement, et SHA 256 pour la signature.

- If you use Active Directory (AD) RMS to obtain the keys, either Cryptographic Mode 1 or Cryptographic Mode 2 is used. The method used depends on your on-premises AD RMS deployment. Cryptographic Mode 1 is the original AD RMS cryptographic implementation. It supports RSA 1024 for signature and encryption, and supports SHA-1 for signature. This mode continues to be supported by all current versions of RMS.

Pour plus d’informations, consultez [Modes de chiffrement AD RMS](/previous-versions/windows/it-pro/windows-server-2008-R2-and-2008/hh867439(v=ws.10)).

**Q. Pourquoi certains messages chiffrés disent-ils provenir de** Office365@messaging.microsoft.com ?

When an encrypted reply is sent from the encryption portal or through the OME Viewer app, the sending email address is set to Office365@messaging.microsoft.com because the encrypted message is sent through a Microsoft endpoint. This helps to prevent encrypted messages from being marked as spam. The displayed name on the email and the address within the encryption portal aren't changed because of this labeling. Also, this labeling only applies to messages sent through the portal, not through any other email client.

 **Q. Je suis abonné à Exchange Hosted Encryption (EHE). Où puis-je en savoir plus sur la mise à niveau vers Office 365 chiffrement des messages ?**

Tous les clients EHE ont été mis à niveau vers le chiffrement de messages Office 365. Pour plus d’informations, consultez le [Centre de mise à niveau du chiffrement hébergé Exchange](../security/office-365-security/exchange-online-protection-overview.md).

 **Q. Dois-je ouvrir des URL, des adresses IP ou des ports dans le pare-feu de mon organisation pour prendre en charge Office 365 chiffrement des messages ?**

Oui. Vous devez ajouter des URL à la liste d’adresses autorisées pour Exchange Online afin que votre organisation permette l’authentification des messages chiffrés par Office 365. Pour obtenir la liste des URL Exchange Online, consultez [URL microsoft 365 et plages d’adresses IP](../enterprise/urls-and-ip-address-ranges.md).

 **Q. Combien de destinataires puis-je envoyer un message chiffré Microsoft 365 ?**

La limite de destinataires est de 500 destinataires par message ou, en cas de combinaison après l’extension de la liste de distribution, de 11 980 caractères dans le champ **À** du message, selon la première fois.

 **Q : Est-il possible de révoquer un message envoyé à un destinataire particulier ?**

Non. Vous ne pouvez pas révoquer un message à une personne particulière après son envoi.

 **Q : Puis-je afficher un rapport des messages chiffrés qui ont été reçus et lus ?**

Il n’existe pas de rapport indiquant si un message chiffré a été affiché, mais il existe des rapports Microsoft 365 disponibles que vous pouvez utiliser pour déterminer le nombre de messages correspondant à une règle de flux de courrier spécifique (également appelée règle de transport), par exemple.

 **Q. Que fait Microsoft des informations que je fournis par le biais du portail OME et de l’application Visionneuse OME ?**

La [déclaration de confidentialité Office 365 Messaging Encryption Portal](https://privacy.microsoft.com/privacystatement) fournit des informations détaillées sur ce que Microsoft fait et ne fait pas avec vos informations privées.

**Q. Que dois-je faire si je ne reçois pas le code de passe à usage unique après l’avoir demandé ?**

Tout d’abord, vérifiez le dossier courrier indésirable ou courrier indésirable dans votre client de messagerie. Les paramètres DKIM et DMARC de votre organisation peuvent entraîner le filtrage de ces e-mails en tant que courrier indésirable.

Ensuite, vérifiez la mise en quarantaine dans le portail de conformité Microsoft Purview. Souvent, les messages contenant un code de passe à usage unique, en particulier les premiers reçus par votre organisation, se retrouvent en quarantaine.
