---
title: Ajouter la marque de votre organisation à vos messages chiffrés
f1.keywords:
- NOCSH
ms.author: krowley
author: kccross
manager: laurawi
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
ms.date: 4/1/2020
search.appverid:
- MET150
- MOE150
ms.assetid: 7a29260d-2959-42aa-8916-feceff6ee51d
ms.collection:
- Strat_O365_IP
- M365-security-compliance
ms.custom:
- seo-marvel-apr2020
- seo-marvel-jun2020
description: Découvrez comment Office 365 administrateurs globaux peuvent appliquer la marque de votre organisation aux messages électroniques chiffrés & contenu du portail de chiffrement.
ms.openlocfilehash: 35fc440b6ae8f973dac6ce1fa5216829b4a966f8d00d763969bc03d1a5216c59
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53836938"
---
# <a name="add-your-organizations-brand-to-your-microsoft-365-for-business-message-encryption-encrypted-messages"></a>Ajouter la marque de votre organisation à votre Microsoft 365 chiffrement de messages pour les entreprises

Vous pouvez appliquer la personnalisation de votre entreprise pour personnaliser l’apparence des messages électroniques de votre organisation et du portail de chiffrement. Vous devez appliquer des autorisations d’administrateur général à votre compte scolaire ou scolaire avant de commencer. Une fois que vous avez ces autorisations, utilisez les cmdlets Get-OMEConfiguration et Set-OMEConfiguration Windows PowerShell pour personnaliser ces parties des messages électroniques chiffrés :
  
- Texte d’introduction

- Disclaimer text

- URL de la déclaration de confidentialité de votre organisation

- Texte dans le portail OME

- Logo qui apparaît dans le message électronique et le portail OME, ou s’il faut utiliser un logo

- Couleur d’arrière-plan dans le message électronique et le portail OME

Vous pouvez également rétablir l’apparence par défaut à tout moment.

Si vous souhaitez plus de contrôle, utilisez Chiffrement avancé de messages Office 365 pour créer plusieurs modèles pour les messages électroniques chiffrés provenant de votre organisation. Utilisez ces modèles pour contrôler des parties de l’expérience de l’utilisateur final. Par exemple, spécifiez si les destinataires peuvent utiliser les comptes Google, Yahoo et Microsoft pour se connectent au portail de chiffrement. Utilisez des modèles pour répondre à plusieurs cas d’utilisation, tels que :

- Services individuels, tels que Finance, Ventes, etc.

- Différents produits

- Régions géographiques ou pays différents

- Si vous souhaitez autoriser la révocation des e-mails

- Indique si vous souhaitez que les e-mails envoyés à des destinataires externes expirent après un nombre de jours spécifié.

Une fois que vous avez créé les modèles, vous pouvez les appliquer aux e-mails chiffrés à l’aide Exchange règles de flux de messagerie. Si vous avez Chiffrement avancé de messages Office 365, vous pouvez révoquer les messages électroniques que vous avez personnalisés à l’aide de ces modèles.

## <a name="work-with-ome-branding-templates"></a>Utiliser des modèles de branding OME

Vous pouvez modifier plusieurs fonctionnalités dans un modèle de branding. Vous pouvez modifier, mais pas supprimer, le modèle par défaut. Si vous avez un chiffrement de messages avancé, vous pouvez également créer, modifier et supprimer des modèles personnalisés. Utilisez Windows PowerShell pour utiliser un modèle de branding à la fois.

- [Set-OMEConfiguration](/powershell/module/exchange/set-omeconfiguration) : modifier le modèle de personnalisation par défaut ou un modèle de personnalisation que vous avez créé.
- [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) : créer un modèle de branding, Chiffrement de messages avancé uniquement.
- [Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration) : supprimer un modèle de personnalisation, chiffrement de messages avancé uniquement. Vous ne pouvez pas supprimer le modèle de branding par défaut.
  
## <a name="modify-an-ome-branding-template"></a>Modifier un modèle de branding OME

Utilisez Windows PowerShell pour modifier un modèle de branding à la fois. Si vous avez un chiffrement de messages avancé, vous pouvez également créer, modifier et supprimer des modèles personnalisés.

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez la cmdlet Set-OMEConfiguration comme décrit dans [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration) ou utilisez le graphique et le tableau suivants pour obtenir des conseils.

![Composants e-mail personnalisables](../media/ome-template-breakout.png)

|**Pour personnaliser cette fonctionnalité de l’expérience de chiffrement**|**Utilisez ces commandes**|
|:-----|:-----|
|Couleur d’arrière-plan|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <br/> Pour plus d’informations sur les couleurs d’arrière-plan, voir la section [Couleurs](#background-color-reference) d’arrière-plan plus loin dans cet article.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -Image (Get-Content "C:\Temp\contosologo.png" -Encoding byte)` <br/> Formats de fichier pris en charge : .png, .jpg, .bmp ou .tiff  <br/> Taille optimale de fichier de logo : moins de 40 ko  <br/> Taille optimale de l’image du logo : 170 x 70 pixels. Si votre image dépasse ces dimensions, le service re dimensione votre logo pour l’afficher dans le portail. Le service ne modifie pas le fichier graphique lui-même. Pour obtenir de meilleurs résultats, utilisez la taille optimale.|
|Texte en face du nom et de l’adresse e-mail de l’expéditeur|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Texte qui apparaît sur le bouton « Lire le message »|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|Texte qui apparaît sous le bouton « Lire le message »|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|URL du lien déclaration de confidentialité|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Pour activer ou désactiver l’authentification avec un code de passe unique pour ce modèle personnalisé|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <br/> **Exemples :** <br/>Pour activer les codes secret à usage unique pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <br/> Pour désactiver les codes secret à usage unique pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Pour activer ou désactiver l’authentification avec les identités Microsoft, Google ou Yahoo pour ce modèle personnalisé|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <br/> **Exemples :** <br/>Pour activer les ID sociaux pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <br/> Pour désactiver les ID sociaux pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>Créer un modèle de branding OME (chiffrement de messages avancé)

Si vous avez Chiffrement avancé de messages Office 365, vous pouvez créer des modèles de personnalisation pour votre organisation à l’aide de l’cmdlet [New-OMEConfiguration.](/powershell/module/exchange/new-omeconfiguration) Une fois que vous avez créé le modèle, vous modifiez le modèle à l’aide de l'Set-OMEConfiguration, comme décrit dans Modifier un modèle de [branding OME.](#modify-an-ome-branding-template) Vous pouvez créer plusieurs modèles.

Pour créer un modèle de personnalisation :

1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez la cmdlet [New-OMEConfiguration](/powershell/module/exchange/new-omeconfiguration) pour créer un modèle.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   Par exemple :

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Renvoyer le modèle de marque par défaut à ses valeurs d’origine

Pour supprimer toutes les modifications du modèle par défaut, y compris les personnalisations de marque, et ainsi de suite, effectuer les étapes suivantes :
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez la cmdlet **Set-OMEConfiguration** comme décrit dans [Set-OMEConfiguration](/powershell/module/exchange/Set-OMEConfiguration). Pour supprimer les personnalisations de votre organisation des valeurs DisclaimerText, EmailText et PortalText, définissez la valeur sur une chaîne `""` vide. Pour toutes les valeurs d’image, telles que Logo, définissez la valeur sur  `"$null"` .

   Le tableau suivant décrit les valeurs par défaut de l’option de personnalisation du chiffrement.

   |Pour annuler cette fonctionnalité de chiffrement et rétablir le texte et l’image par défaut|Utilisez ces commandes|
   |:-----|:-----|
   |Texte par défaut qui est livré avec des messages électroniques chiffrés.  Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <br/> **Exemple de retour à la valeur par défaut :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <br/> **Exemple de retour à la valeur par défaut :** <br/>  `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Couleur d’arrière-plan|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <br/> **Exemple de retour à la valeur par défaut :** <br/> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Supprimer un modèle de personnalisation (chiffrement de messages avancé)

Vous pouvez uniquement supprimer ou supprimer des modèles de branding que vous avez créés. Vous ne pouvez pas supprimer le modèle de branding par défaut.

Pour supprimer un modèle de personnalisation :
  
1. À l’aide d’un compte scolaire ou scolaire qui dispose d’autorisations d’administrateur général dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell).

2. Utilisez la cmdlet **Remove-OMEConfiguration** comme suit :

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   Par exemple :

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Pour plus d’informations, [voir Remove-OMEConfiguration](/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Créer une règle Exchange flux de messagerie qui applique votre personnalisation aux e-mails chiffrés

> [!IMPORTANT]
> Les applications tierces qui analysent et modifient le courrier électronique peuvent empêcher l’application correcte de la marque OME.

Après avoir modifié le modèle par défaut ou créé de nouveaux modèles de personnalisation, vous pouvez créer des règles de flux de messagerie Exchange pour appliquer votre personnalisation en fonction de certaines conditions. Une telle règle appliquera une personnalisation dans les scénarios suivants :

- Si le courrier électronique a été chiffré manuellement par l’utilisateur final à l’aide de Outlook ou Outlook sur le web, anciennement Outlook Web App

- Si le courrier a été automatiquement chiffré par une règle de flux Exchange de messagerie ou une stratégie de protection contre la perte de données

Pour plus d’informations sur la création d’une règle Exchange de flux de messagerie qui applique le chiffrement, voir Définir des règles de flux de messagerie pour chiffrer les messages électroniques [dans Office 365](define-mail-flow-rules-to-encrypt-email.md).

1. Dans un navigateur web, à l’aide d’un compte scolaire ou scolaire qui a reçu des autorisations d’administrateur général, connectez-vous [Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Sélectionnez la **vignette** Administrateur.

3. In the Centre d’administration Microsoft 365, choose **Admin centers** \> **Exchange**.

4. Dans le EAC, sélectionnez Règles de **flux de** messagerie et sélectionnez Nouvelle icône \>  Créer une  ![ ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \> **règle.** Pour plus d’informations sur l’utilisation du Centre d’administration Exchange, [voir](/exchange/exchange-admin-center)Exchange Online .

5. In **Name**, type a name for the rule, such as Branding for sales department.

6. In **Apply this rule if**, select the condition The **sender is located inside the organization** and other conditions you want from the list of available conditions. Par exemple, vous pouvez appliquer un modèle de branding particulier à :

   - Tous les e-mails chiffrés envoyés par des membres du service financier
   - Messages électroniques chiffrés envoyés avec un certain mot clé, tel que « Externe » ou « Partenaire »
   - Messages électroniques chiffrés envoyés à un domaine particulier

7. Dans **l’exemple suivant,** **sélectionnez Modifier la sécurité des messages** Appliquer une \> **personnalisation aux messages OME.** Ensuite, dans la baisse, sélectionnez un modèle de branding.

8. (Facultatif) Vous pouvez configurer la règle de flux de messagerie pour appliquer le chiffrement et la personnalisation. Dans **l’exemple suivant,** **sélectionnez Modifier la** sécurité des messages, puis sélectionnez Appliquer chiffrement de messages Office 365 protection des **droits.** Sélectionnez un modèle RMS dans la liste, **sélectionnez Enregistrer,** puis **ok.**
  
   La liste des modèles inclut les modèles et options par défaut, ainsi que les modèles personnalisés que vous créez. Si la liste est vide, assurez-vous que vous avez chiffrement de messages Office 365 avec les nouvelles fonctionnalités. Pour obtenir des instructions, voir [Configurer de chiffrement de messages Office 365 nouvelles fonctionnalités.](set-up-new-message-encryption-capabilities.md) Pour plus d’informations sur les modèles par défaut, voir [Configuration et gestion des modèles pour Azure Information Protection.](/information-protection/deploy-use/configure-policy-templates) Pour plus d’informations **sur l’option** Ne pas forwarder, consultez [l’option Ne pas forwarder pour les e-mails.](/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails) Pour plus d’informations sur **l’option chiffrer uniquement,** voir [l’option Chiffrer uniquement pour les e-mails.](/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails)

   Choisissez **ajouter une action** si vous souhaitez spécifier une autre action.

## <a name="background-color-reference"></a>Référence de couleur d’arrière-plan

Les noms de couleur que vous pouvez utiliser pour la couleur d’arrière-plan sont limités. Au lieu d’un nom de couleur, vous pouvez utiliser une valeur de code hexadée (#RRGGBB). Vous pouvez utiliser une valeur de code hexas qui correspond à un nom de couleur, ou vous pouvez utiliser une valeur de code hexadée personnalisée. N’oubliez pas de mettre la valeur de code hexa entre guillemets (par exemple, `"#f0f8ff"` ).

Les noms de couleur d’arrière-plan disponibles et les valeurs de code hexades correspondantes sont décrits dans le tableau suivant.

|**Nom de la couleur**|**Code couleur**|
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
