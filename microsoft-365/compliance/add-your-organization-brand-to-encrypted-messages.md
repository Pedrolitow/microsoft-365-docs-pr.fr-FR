---
title: Ajouter votre marque aux messages chiffrés
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
ms.localizationpriority: medium
ms.date: 10/14/2022
search.appverid:
- MET150
- MOE150
ms.assetid: 7a29260d-2959-42aa-8916-feceff6ee51d
ms.collection:
- tier1
- purview-compliance
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
- admindeeplinkMAC
- admindeeplinkEXCHANGE
description: Découvrez comment les administrateurs généraux de Microsoft 365 peuvent appliquer la personnalisation de votre organisation aux messages électroniques chiffrés & contenu du portail de chiffrement.
ms.openlocfilehash: ec15a4d6c284293074cebf7c4ba49510d60e3f1c
ms.sourcegitcommit: 0d8fb571024f134d7480fe14cffc5e31a687d356
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/20/2022
ms.locfileid: "68624750"
---
# <a name="add-your-organizations-brand-to-your-microsoft-purview-message-encryption-encrypted-messages"></a>Ajouter la marque de votre organisation à vos messages chiffrés Chiffrement de messages Microsoft Purview

Appliquez la personnalisation de votre entreprise pour personnaliser l’apparence des messages électroniques de votre organisation et du portail de chiffrement. Vous devez appliquer des autorisations d’administrateur général à votre compte professionnel ou scolaire avant de commencer. Utilisez les applets de commande Get-OMEConfiguration et Set-OMEConfiguration dans Exchange Online PowerShell pour personnaliser ces parties des messages électroniques chiffrés :

- Texte d’introduction
- Disclaimer text
- URL de la déclaration de confidentialité de votre organisation
- Texte dans le portail des messages chiffrés
- Logo qui s’affiche dans le message électronique et le portail des messages chiffrés, ou s’il faut utiliser un logo
- Couleur d’arrière-plan dans le message électronique et le portail des messages chiffrés

Vous pouvez également rétablir l’apparence par défaut à tout moment.

Si vous souhaitez plus de contrôle, utilisez Microsoft Purview Advanced Message Encryption pour créer plusieurs modèles pour les e-mails chiffrés provenant de votre organisation. Utilisez ces modèles pour contrôler certaines parties de l’expérience utilisateur final. Par exemple, spécifiez si les destinataires peuvent utiliser les comptes Google, Yahoo et Microsoft pour se connecter au portail de chiffrement. Utilisez des modèles pour traiter plusieurs cas d’usage, tels que :

- Des services individuels, tels que les finances, les ventes, etc.
- Différents produits
- Régions géographiques ou pays différents
- Indique si vous souhaitez autoriser la révocation des e-mails
- Indiquez si vous souhaitez que les e-mails envoyés à des destinataires externes expirent après un nombre spécifié de jours.

Une fois que vous avez créé les modèles, appliquez-les aux e-mails chiffrés envoyés à partir de votre boîte aux lettres en ligne à l’aide de règles de flux de messagerie Exchange. Si vous avez Microsoft Purview Advanced Message Encryption, vous pouvez révoquer tout e-mail que vous avez marqué.

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="work-with-branding-templates"></a>Utiliser des modèles de personnalisation

Vous pouvez modifier plusieurs fonctionnalités dans un modèle de personnalisation et modifier, mais pas supprimer, le modèle par défaut. Si vous disposez d’Advanced Message Encryption, vous pouvez également créer, modifier et supprimer des modèles personnalisés. Utilisez Exchange Online PowerShell pour travailler avec un modèle de personnalisation à la fois.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) : modifiez le modèle de personnalisation par défaut ou un modèle de personnalisation personnalisé que vous avez créé.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) : créez un modèle de personnalisation, Advanced Message Encryption uniquement.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) - Supprimer un modèle de personnalisation personnalisé, Advanced Message Encryption uniquement. Vous ne pouvez pas supprimer le modèle de personnalisation par défaut.

## <a name="modify-a-branding-template"></a>Modifier un modèle de personnalisation

Utilisez Exchange Online PowerShell pour modifier un modèle de personnalisation à la fois. Si vous disposez d’Advanced Message Encryption, vous pouvez également créer, modifier et supprimer des modèles personnalisés.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet de commande Set-OMEConfiguration comme décrit dans [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) ou utilisez le graphique et le tableau suivants pour obtenir des conseils.

![Composants d’e-mail personnalisables.](../media/ome-template-breakout.png)

|Pour personnaliser cette fonctionnalité de l’expérience de chiffrement|Utiliser ces commandes|
|---|---|
|Couleur d’arrière-plan|`Set-OMEConfiguration -Identity "<ConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <p> Pour plus d’informations sur les couleurs d’arrière-plan, consultez la section [Couleurs d’arrière-plan](#background-color-reference) plus loin dans cet article.|
|Logo|`Set-OMEConfiguration -Identity "<ConfigurationName>" -Image <Byte[]>` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -Image ([System.IO.File]::ReadAllBytes('C:\Temp\contosologo.png'))` <p> Formats de fichier pris en charge : .png, .jpg, .bmp ou .tiff <p> Taille optimale de fichier de logo : moins de 40 ko <p> Taille optimale de l’image du logo : 170 x 70 pixels. Si votre image dépasse ces dimensions, le service redimensionnera votre logo pour l’afficher dans le portail. Le service ne modifie pas le fichier graphique lui-même. Pour de meilleurs résultats, utilisez la taille optimale.|
|Texte en regard du nom et de l’adresse e-mail de l’expéditeur|`Set-OMEConfiguration -Identity "<ConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Texte qui s’affiche sur le bouton « Lire le message »|`Set-OMEConfiguration -Identity "<ConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -ReadButtonText "Read Secure Message."`|
|Texte qui s’affiche sous le bouton « Lire le message »|`Set-OMEConfiguration -Identity "<ConfigurationName>" -EmailText "<String up to 1024 characters>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|URL du lien Déclaration de confidentialité|`Set-OMEConfiguration -Identity "<ConfigurationName>" -PrivacyStatementURL "<URL>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Message encryption cfonfiguration" -PortalText "ContosoPharma secure email portal."`|
|Pour activer ou désactiver l’authentification avec un code de passe unique pour ce modèle personnalisé|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <p> **Exemples :** <br/>Pour activer des codes secrets uniques pour ce modèle personnalisé <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <p> Pour désactiver les codes secrets uniques pour ce modèle personnalisé <p> `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Pour activer ou désactiver l’authentification avec des identités Microsoft, Google ou Yahoo pour ce modèle personnalisé|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <p> **Exemples :** <br/>Pour activer les ID sociaux pour ce modèle personnalisé <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <p> Pour désactiver les ID sociaux pour ce modèle personnalisé <p> `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|

## <a name="create-an-encrypted-message-branding-template-advanced-message-encryption"></a>Créer un modèle de personnalisation de message chiffré (Advanced Message Encryption)

Si vous avez Microsoft Purview Advanced Message Encryption, vous pouvez créer des modèles de personnalisation personnalisés pour votre organisation à l’aide de l’applet de commande [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) . Une fois que vous avez créé le modèle, vous modifiez le modèle à l’aide de l’applet de commande Set-OMEConfiguration comme décrit dans [Modifier un modèle de personnalisation](#modify-a-branding-template). Vous pouvez créer plusieurs modèles.

Pour créer un modèle de personnalisation personnalisé :

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet [de commande New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) pour créer un modèle.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Par exemple :

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Renvoyer le modèle de personnalisation par défaut à ses valeurs d’origine

Pour supprimer toutes les modifications du modèle par défaut, y compris les personnalisations de marque, et ainsi de suite, procédez comme suit :

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, connectez-vous à Exchange Online PowerShell. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet de commande **Set-OMEConfiguration** comme décrit dans [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). Pour supprimer les personnalisations de marque de votre organisation des valeurs DisclaimerText, EmailText et PortalText, définissez la valeur sur une chaîne vide. `""` Pour toutes les valeurs d’image, telles que Logo, définissez la valeur sur `"$null"`.

   Le tableau suivant décrit les valeurs par défaut de l’option de personnalisation de chiffrement.

   |Pour annuler cette fonctionnalité de chiffrement et rétablir le texte et l’image par défaut|Utiliser ces commandes|
   |:-----|:-----|
   |Texte par défaut fourni avec des messages électroniques chiffrés. Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -EmailText ""`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <p> **Exemple :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -DisclaimerText ""`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <p> **Exemple de retour à la valeur par défaut :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <p> **Exemple de retour à la valeur par défaut :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -Image $null`|
   |Couleur d’arrière-plan|`Set-OMEConfiguration -Identity "<ConfigurationName>" -BackgroundColor "$null">` <p> **Exemple de retour à la valeur par défaut :** <p> `Set-OMEConfiguration -Identity "Message encryption configuration" -BackgroundColor $null`|

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Supprimer un modèle de personnalisation personnalisé (Advanced Message Encryption)

Vous pouvez uniquement supprimer ou supprimer les modèles de personnalisation que vous avez créés. Vous ne pouvez pas supprimer le modèle de personnalisation par défaut.

Pour supprimer un modèle de personnalisation :

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur général dans votre organisation, [connectez-vous à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez l’applet **de commande Remove-OMEConfiguration** comme suit :

   ```powershell
   Remove-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Par exemple :

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Pour plus d’informations, consultez [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails-sent-from-your-online-organization-to-external-recipients"></a>Créer une règle de flux de messagerie Exchange qui applique votre personnalisation aux e-mails chiffrés envoyés de votre organisation en ligne à des destinataires externes

> [!IMPORTANT]
> Les applications tierces qui analysent et modifient le courrier peuvent empêcher l’application correcte de la personnalisation.

Après avoir modifié le modèle par défaut ou créé de nouveaux modèles de personnalisation, vous pouvez créer des règles de flux de messagerie Exchange pour appliquer votre personnalisation en fonction de certaines conditions. Plus important encore, l’e-mail doit être chiffré. Une telle règle applique la personnalisation aux messages envoyés à partir de votre boîte aux lettres en ligne dans les scénarios suivants :

- Si l’e-mail a été chiffré manuellement par l’utilisateur final à l’aide d’Outlook ou de Outlook sur le web, anciennement Outlook Web App
- Si l’e-mail a été automatiquement chiffré par une règle de flux de messagerie Exchange ou une stratégie de Protection contre la perte de données Microsoft Purview

Pour vous assurer Chiffrement de messages Microsoft Purview appliquez votre personnalisation, configurez une règle de flux de messagerie pour chiffrer vos messages. La priorité de la règle de chiffrement doit être supérieure à la règle de personnalisation afin que la règle de chiffrement soit traitée en premier. Par défaut, si vous créez la règle de chiffrement avant la règle de personnalisation, la règle de chiffrement aura une priorité plus élevée. Pour plus d’informations, consultez [Définir des règles de flux de courrier pour chiffrer les messages électroniques dans Office 365](define-mail-flow-rules-to-encrypt-email.md). Pour plus d’informations sur la définition de la priorité d’une règle de flux de messagerie, consultez [Gérer les règles de flux de courrier](/exchange/security-and-compliance/mail-flow-rules/manage-mail-flow-rules#set-the-priority-of-a-mail-flow-rule).

1. Dans un navigateur web, à l’aide d’un compte professionnel ou scolaire qui a reçu des autorisations d’administrateur général, [connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Choisissez la vignette **Administration**.

3. Dans le Centre d'administration Microsoft 365, choisissez **Administration centres** \> **Exchange**.

4. Dans le CENTRE, accédez aux **règles** de **flux** \> de messagerie et sélectionnez **l’icône Nouveau** ![nouveau.](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \>**Créez une règle**. Pour plus d’informations sur l’utilisation de la CAE, consultez [le Centre d’administration Exchange dans Exchange Online](/exchange/exchange-admin-center).

5. Dans **Nom**, tapez un nom pour la règle, par exemple **Personnalisation pour le service des ventes**.

6. Dans **Appliquer cette règle si**, sélectionnez la condition **L’expéditeur se trouve dans l’organisation** et les autres conditions souhaitées dans la liste des conditions disponibles. Par exemple, vous pouvez appliquer un modèle de personnalisation particulier à :

   - Tous les e-mails chiffrés envoyés par les membres du service financier
   - E-mails chiffrés envoyés avec un certain mot clé tel que « Externe » ou « Partenaire »
   - E-mails chiffrés envoyés à un domaine particulier

7. Si vous avez déjà défini une règle de flux de messagerie pour appliquer le chiffrement, ignorez cette étape. Sinon, pour configurer la règle de flux de messagerie afin d’appliquer **le** chiffrement, sélectionnez **Modifier la sécurité des messages**, puis **appliquer Office 365 chiffrement des messages et la protection des droits**. Sélectionnez un modèle RmS (Rights Management Service) dans la liste, puis sélectionnez **Ajouter une action**.

   La liste des modèles inclut les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous créez. Si la liste est vide, vérifiez que vous avez configuré Chiffrement de messages Microsoft Purview. Pour obtenir des instructions, consultez [Configurer Chiffrement de messages Microsoft Purview](set-up-new-message-encryption-capabilities.md). Pour plus d’informations sur les modèles par défaut, consultez [Configuration et gestion des modèles pour Azure Information Protection](/information-protection/deploy-use/configure-policy-templates). Pour plus d’informations sur l’option **Ne pas transférer** , consultez [l’option Ne pas transférer pour les e-mails](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Pour plus d’informations sur l’option **Chiffrer uniquement** , consultez [l’option Chiffrer uniquement pour les e-mails](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

8. Dans **Faire ce qui suit**, sélectionnez **Modifier la sécurité** \> des messages **Appliquer la personnalisation aux messages OME**. Ensuite, dans la liste déroulante, sélectionnez un modèle de personnalisation.

   Sélectionnez **Ajouter une action** si vous souhaitez spécifier une autre action, ou **sélectionnez Enregistrer**, puis sélectionnez **OK**.

## <a name="background-color-reference"></a>Référence de couleur d’arrière-plan

Les noms de couleur que vous pouvez utiliser pour la couleur d’arrière-plan sont limités. Au lieu d’un nom de couleur, vous pouvez utiliser une valeur de code hexadécimal (`#RRGGBB`). Vous pouvez utiliser une valeur de code hexadécimal qui correspond à un nom de couleur, ou vous pouvez utiliser une valeur de code hexadécimal personnalisée. Veillez à placer la valeur de code hexadécimal entre guillemets (par exemple, `"#f0f8ff"`).

Les noms de couleurs d’arrière-plan disponibles et leurs valeurs de code hexadécimal correspondantes sont décrits dans le tableau suivant.

|Nom de la couleur|Code de couleur|
|---|---|
|`aliceblue`|#f0f8ff|
|`antiquewhite`|#faebd7|
|`aqua`|#00ffff|
|`aquamarine`|#7fffd4|
|`azure`|#f0ffff|
|`beige`|#f5f5dc|
|`bisque`|#ffe4c4|
|`black`|#000000|
|`blanchedalmond`|#ffebcd|
|`blue`|#0000ff|
|`blueviolet`|#8a2be2|
|`brown`|#a52a2a|
|`burlywood`|#deb887|
|`cadetblue`|#5f9ea0|
|`chartreuse`|#7fff00|
|`chocolate`|#d2691e|
|`coral`|#ff7f50|
|`cornflowerblue`|#6495ed|
|`cornsilk`|#fff8dc|
|`crimson`|#dc143c|
|`cyan`|#00ffff|
|`darkblue`|#00008b|
|`darkcyan`|#008b8b|
|`darkgoldenrod`|#b8860b|
|`darkgray`|#a9a9a9|
|`darkgreen`|#006400|
|`darkkhaki`|#bdb76b|
|`darkmagenta`|#8b008b|
|`darkolivegreen`|#556b2f|
|`darkorange`|#ff8c00|
|`darkorchid`|#9932cc|
|`darkred`|#8b0000|
|`darksalmon`|#e9967a|
|`darkseagreen`|#8fbc8f|
|`darkslateblue`|#483d8b|
|`darkslategray`|#2f4f4f|
|`darkturquoise`|#00ced1|
|`darkviolet`|#9400d3|
|`deeppink`|#ff1493|
|`deepskyblue`|#00bfff|
|`dimgray`|#696969|
|`dodgerblue`|#1e90ff|
|`firebrick`|#b22222|
|`floralwhite`|#fffaf0|
|`forestgreen`|#228b22|
|`fuchsia`|#ff00ff|
|`gainsboro`|#dcdcdc|
|`ghostwhite`|#f8f8ff|
|`gold`|#ffd700|
|`goldenrod`|#daa520|
|`gray`|#808080|
|`green`|#008000|
|`greenyellow`|#adff2f|
|`honeydew`|#f0fff0|
|`hotpink`|#ff69b4|
|`indianred`|#cd5c5c|
|`indigo`|#4b0082|
|`ivory`|#fffff0|
|`khaki`|#f0e68c|
|`lavender`|#e6e6fa|
|`lavenderblush`|#fff0f5|
|`lawngreen`|#7cfc00|
|`lemonchiffon`|#fffacd|
|`lightblue`|#add8e6|
|`lightcoral`|#f08080|
|`lightcyan`|#e0ffff|
|`lightgoldenrodyellow`|#fafad2|
|`lightgray`|#d3d3d3|
|`lightgrey`|#d3d3d3|
|`lightgreen`|#90ee90|
|`lightpink`|#ffb6c1|
|`lightsalmon`|#ffa07a|
|`lightseagreen`|#20b2aa|
|`lightskyblue`|#87cefa|
|`lightslategray`|#778899|
|`lightsteelblue`|#b0c4de|
|`lightyellow`|#ffffe0|
|`lime`|#00ff00|
|`limegreen`|#32cd32|
|`linen`|#faf0e6|
|`magenta`|#ff00ff|
|`maroon`|#800000|
|`mediumaquamarine`|#66cdaa|
|`mediumblue`|#0000cd|
|`mediumorchid`|#ba55d3|
|`mediumpurple`|#9370db|
|`mediumseagreen`|#3cb371|
|`mediumslateblue`|#7b68ee|
|`mediumspringgreen`|#00fa9a|
|`mediumturquoise`|#48d1cc|
|`mediumvioletred`|#c71585|
|`midnightblue`|#191970|
|`mintcream`|#f5fffa|
|`mistyrose`|#ffe4e1|
|`moccasin`|#ffe4b5|
|`navajowhite`|#ffdead|
|`navy`|#000080|
|`oldlace`|#fdf5e6|
|`olive`|#808000|
|`olivedrab`|#6b8e23|
|`orange`|#ffa500|
|`orangered`|#ff4500|
|`orchid`|#da70d6|
|`palegoldenrod`|#eee8aa|
|`palegreen`|#98fb98|
|`paleturquoise`|#afeeee|
|`palevioletred`|#db7093|
|`papayawhip`|#ffefd5|
|`peachpuff`|#ffdab9|
|`peru`|#cd853f|
|`pink`|#ffc0cb|
|`plum`|#dda0dd|
|`powderblue`|#b0e0e6|
|`purple`|#800080|
|`red`|#ff0000|
|`rosybrown`|#bc8f8f|
|`royalblue`|#4169e1|
|`saddlebrown`|#8b4513|
|`salmon`|#fa8072|
|`sandybrown`|#f4a460|
|`seagreen`|#00ff00|
|`seashell`|#fff5ee|
|`sienna`|#a0522d|
|`silver`|#c0c0c0|
|`skyblue`|#87ceeb|
|`slateblue`|#6a5acd|
|`slategray`|#708090|
|`snow`|#fffafa|
|`springgreen`|#00ff7f|
|`steelblue`|#4682b4|
|`tan`|#d2b48c|
|`teal`|#008080|
|`thistle`|#d8bfd8|
|`tomato`|#ff6347|
|`turquoise`|#40e0d0|
|`violet`|#ee82ee|
|`wheat`|#f5deb3|
|`white`|#ffffff|
|`whitesmoke`|#f5f5f5|
|`yellow`|#ffff00|
|`yellowgreen`|#9acd32|
