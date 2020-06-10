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
description: Appliquez la personnalisation de votre organisation aux messages électroniques chiffrés de votre organisation et au contenu du portail de chiffrement.
ms.openlocfilehash: 86636b319151a96e9ec827f85cc943282c30f63c
ms.sourcegitcommit: 584e2e9db8c541fe32624acdca5e12ee327fdb63
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/10/2020
ms.locfileid: "44679108"
---
# <a name="add-your-organizations-brand-to-your-encrypted-messages"></a>Ajouter la marque de votre organisation à vos messages chiffrés

En tant qu’administrateur Exchange Online ou Exchange Online Protection, vous pouvez appliquer la personnalisation de votre entreprise pour personnaliser l’apparence des messages électroniques de chiffrement des messages Microsoft 365 pour votre organisation et le contenu du portail de chiffrement. À l’aide des applets de commande Windows PowerShell Get-OMEConfiguration et Set-OMEConfiguration, vous pouvez personnaliser les aspects suivants de l’expérience d’affichage pour les destinataires de messages électroniques chiffrés :
  
- Le texte d’introduction du message électronique contenant le message chiffré

- Le texte d’exclusion de responsabilité du message électronique contentant le message chiffré

- URL de la déclaration de confidentialité de votre organisation

- Texte qui apparaît dans le portail OME

- Logo qui apparaît dans le message électronique et dans le portail OME, ou s’il faut utiliser un logo du tout

- Couleur d’arrière-plan dans le message électronique et le portail OME

Vous pouvez également rétablir l’apparence par défaut à tout moment.

Si vous souhaitez davantage de contrôle, vous pouvez utiliser le chiffrement de messages avancé Office 365 et créer plusieurs modèles pour les messages électroniques chiffrés provenant de votre organisation. Ces modèles vous permettent de contrôler plus que l’apparence des messages électroniques, mais aussi de contrôler les éléments de l’expérience de l’utilisateur final. Par exemple, vous pouvez spécifier si les destinataires de messages auxquels ce modèle est appliqué et ceux qui utilisent Google, Yahoo et les comptes Microsoft peuvent utiliser ces comptes pour se connecter au portail de chiffrement de messages Office 365. Vous pouvez utiliser des modèles pour répondre à plusieurs cas d’utilisation, par exemple :

- Modèles pour chaque service, tels que finance, ventes, etc.

- Modèles pour différents produits

- Modèles pour différentes régions géographiques ou pays

- Si vous souhaitez autoriser la révocation des courriers électroniques

- Si vous souhaitez que les e-mails envoyés à des destinataires externes expirent après un nombre de jours spécifié.

Une fois que vous avez créé les modèles, vous pouvez les appliquer à des messages électroniques chiffrés à l’aide de règles de flux de messagerie Exchange. Si vous disposez d’Office 365 Advanced message Encryption, vous pouvez révoquer tous les messages que vous avez personnalisés à l’aide de ces modèles.

## <a name="work-with-ome-branding-templates"></a>Utiliser des modèles de personnalisation OME

Vous pouvez modifier plusieurs fonctionnalités dans un modèle de personnalisation. Vous pouvez modifier, mais pas supprimer, le modèle par défaut. Si vous disposez d’un chiffrement de messages avancé, vous pouvez également créer, modifier et supprimer des modèles personnalisés. Utilisez Windows PowerShell pour utiliser un modèle de personnalisation à la fois. Vous aurez besoin d’un compte professionnel ou scolaire disposant des autorisations d’administrateur général dans votre organisation pour pouvoir utiliser ces applets de commande.

- [Set-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/set-omeconfiguration) -modifiez le modèle de personnalisation par défaut ou un modèle de personnalisation que vous avez créé.
- [New-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/new-omeconfiguration) -créer un modèle de personnalisation, le chiffrement de messages avancé uniquement.
- [Remove-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/remove-omeconfiguration) -supprimer un modèle de personnalisation personnalisé, chiffrement de message avancé uniquement. Vous ne pouvez pas supprimer le modèle de personnalisation par défaut.
  
## <a name="modify-an-ome-branding-template"></a>Modifier un modèle de personnalisation OME

Utilisez Windows PowerShell pour modifier un modèle de personnalisation à la fois. Si vous disposez d’un chiffrement de messages avancé, vous pouvez également créer, modifier et supprimer des modèles personnalisés.

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur globales dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](https://aka.ms/exopowershell).

2. Modifiez le modèle à l’aide de la cmdlet Set-OMEConfiguration comme décrit dans [Set-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/Set-OMEConfiguration) ou utilisez le graphique et le tableau ci-dessous pour obtenir des instructions.

![Composants de messagerie personnalisables](../media/ome-template-breakout.png)

|**Pour personnaliser cette fonctionnalité de l’expérience de chiffrement**|**Utilisez ces commandes**|
|:-----|:-----|
|Couleur d’arrière-plan|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "<#RRGGBB hexadecimal color code or name value>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -BackgroundColor "#ffffff"` <br/> Pour plus d’informations sur les couleurs d’arrière-plan, voir la section [couleurs d’arrière-plan](#background-color-reference) plus loin dans cette rubrique.|
|Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <Byte[]>` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -Image (Get-Content "C:\Temp\contosologo.png" -Encoding byte)` <br/> Formats de fichier pris en charge : .png, .jpg, .bmp ou .tiff  <br/> Taille optimale de fichier de logo : moins de 40 ko  <br/> Taille optimale de l’image de logo : 170x70 pixels. Si votre image dépasse ces dimensions, le service redimensionne votre logo pour qu’il s’affiche dans le portail. Le service ne modifie pas le fichier graphique lui-même. Pour obtenir de meilleurs résultats, utilisez la taille optimale.|
|Texte en regard du nom et de l’adresse de messagerie de l’expéditeur|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -IntroductionText "<String up to 1024 characters>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -IntroductionText "has sent you a secure message."`|
|Texte qui apparaît sur le bouton « Lire le message »|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -ReadButtonText "<String up to 1024 characters>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -ReadButtonText "Read Secure Message."`|
|Texte qui apparaît sous le bouton « Lire le message »|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<String up to 1024 characters>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -EmailText "Encrypted message from ContosoPharma secure messaging system."`|
|URL du lien déclaration de confidentialité|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PrivacyStatementURL "<URL>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -PrivacyStatementURL "https://contoso.com/privacystatement.html"`|
|Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -DisclaimerText "<Disclaimer statement. String of up to 1024 characters.>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -DisclaimerText "This message is confidential for the use of the addressee only."`|
|Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<Text for your portal. String of up to 128 characters.>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -PortalText "ContosoPharma secure email portal."`|
|Pour activer ou désactiver l’authentification avec un code d’accès unique pour ce modèle personnalisé|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -OTPEnabled <$true|$false>` <br/> **Exemples :** <br/>Pour activer les codes secrets à usage unique pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $true` <br/> Pour désactiver les codes secrets à usage unique pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -OTPEnabled $false`|
|Pour activer ou désactiver l’authentification avec des identités Microsoft, Google ou Yahoo pour ce modèle personnalisé|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -SocialIdSignIn <$true|$false>` <br/> **Exemples :** <br/>Pour activer les ID de mise en réseau pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $true` <br/> Pour désactiver les ID de mise en réseau pour ce modèle personnalisé <br/>  `Set-OMEConfiguration -Identity "Branding Template 1" -SocialIdSignIn $false`|

## <a name="create-an-ome-branding-template-advanced-message-encryption"></a>Créer un modèle de personnalisation OME (chiffrement avancé des messages)

Si vous disposez d’Office 365 Advanced message Encryption, vous pouvez créer des modèles de personnalisation pour votre organisation à l’aide de la cmdlet [New-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/new-omeconfiguration) . Une fois que vous avez créé le modèle, vous pouvez modifier le modèle à l’aide de la cmdlet Set-OMEConfiguration comme décrit dans [modifier un modèle de personnalisation OME](#modify-an-ome-branding-template). Vous pouvez créer plusieurs modèles.

Pour créer un modèle de personnalisation :

1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur globales dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](https://aka.ms/exopowershell).

2. Utilisez la cmdlet [New-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/new-omeconfiguration) pour créer un nouveau modèle.

   ```powershell
   New-OMEConfiguration -Identity "<OMEConfigurationName>"
   ```

   For example,

   ```powershell
   New-OMEConfiguration -Identity "Custom branding template"
   ```

## <a name="return-the-default-branding-template-to-its-original-values"></a>Rétablir les valeurs d’origine du modèle de personnalisation par défaut

Pour supprimer toutes les modifications apportées au modèle par défaut, y compris les personnalisations de la marque, et ainsi de suite, effectuez les étapes suivantes :
  
1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur globales dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](https://aka.ms/exopowershell).

2. Utilisez la cmdlet **Set-OMEConfiguration** comme décrit dans [Set-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/Set-OMEConfiguration). Pour supprimer les personnalisations personnalisées de votre organisation des valeurs DisclaimerText, EmailText et PortalText, définissez la valeur sur une chaîne vide, `""` . Pour toutes les valeurs d’image, telles que logo, définissez la valeur sur `"$null"` .

   Le tableau suivant décrit les valeurs par défaut de l’option de personnalisation du chiffrement.

   **Pour annuler cette fonctionnalité de chiffrement et rétablir le texte et l’image par défaut**|**Utilisez ces commandes**|
   |:-----|:-----|
   |Texte par défaut qui accompagne les messages électroniques chiffrés  <br/> Texte par défaut qui s’affiche au-dessus des instructions relatives à l’affichage des messages chiffrés|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -EmailText "<empty string>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -EmailText ""`|
   |Déclaration de non-responsabilité du message électronique qui contient le message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" DisclaimerText "<empty string>"` <br/> **Exemple :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -DisclaimerText ""`|
   |Texte qui s’affiche en haut du portail d’affichage du message chiffré|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -PortalText "<empty string>"` <br/> **Exemple de rétablissement de la valeur par défaut :** <br/>  `Set-OMEConfiguration -Identity "OME Configuration" -PortalText ""`|
   |Logo|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -Image <"$null">` <br/> **Exemple de rétablissement de la valeur par défaut :** <br/>  `Set-OMEConfiguration -Identity "OME configuration" -Image $null`|
   |Couleur d’arrière-plan|`Set-OMEConfiguration -Identity "<OMEConfigurationName>" -BackgroundColor "$null">` <br/> **Exemple de rétablissement de la valeur par défaut :** <br/> `Set-OMEConfiguration -Identity "OME configuration" -BackgroundColor $null`|
   |

## <a name="remove-a-custom-branding-template-advanced-message-encryption"></a>Supprimer un modèle de personnalisation (chiffrement de message avancé)

Vous pouvez uniquement supprimer ou supprimer des modèles de personnalisation que vous avez créés. Vous ne pouvez pas supprimer le modèle de personnalisation par défaut.

Pour supprimer un modèle de personnalisation :
  
1. À l’aide d’un compte professionnel ou scolaire disposant d’autorisations d’administrateur globales dans votre organisation, démarrez une session Windows PowerShell et connectez-vous à Exchange Online. Pour obtenir des instructions, voir [Connexion à Exchange Online PowerShell](https://aka.ms/exopowershell).

2. Utilisez la cmdlet **Remove-OMEConfiguration** comme suit :

   ```powershell
   Remove-OMEConfiguration -Identity ""<OMEConfigurationName>"
   ```

   For example,

   ```powershell
   Remove-OMEConfiguration -Identity "Branding template 1"
   ```

   Pour plus d’informations, consultez la rubrique [Remove-OMEConfiguration](https://docs.microsoft.com/powershell/module/exchange/remove-omeconfiguration).

## <a name="create-an-exchange-mail-flow-rule-that-applies-your-custom-branding-to-encrypted-emails"></a>Créer une règle de flux de messagerie Exchange qui applique votre personnalisation aux courriers chiffrés

Une fois que vous avez modifié le modèle par défaut ou créé des modèles de personnalisation, vous pouvez créer des règles de flux de messagerie Exchange pour appliquer votre personnalisation personnalisée en fonction de certaines conditions. Une telle règle applique une personnalisation personnalisée dans les scénarios suivants :

- Si le message a été chiffré manuellement par l’utilisateur final à partir des clients Outlook ou Outlook sur le Web (anciennement appelé Outlook Web App)

- Si le courrier électronique a été automatiquement chiffré par une règle de flux de messagerie Exchange ou une stratégie de protection contre la perte de données

Pour plus d’informations sur la création d’une règle de flux de messagerie Exchange qui applique le chiffrement, voir [définir des règles de flux de messagerie pour chiffrer des messages électroniques dans Office 365](define-mail-flow-rules-to-encrypt-email.md).

1. Dans un navigateur Web, à l’aide d’un compte professionnel ou scolaire auquel des autorisations d’administrateur général ont été accordées, [Connectez-vous à Office 365](https://support.office.com/article/b9582171-fd1f-4284-9846-bdd72bb28426#ID0EAABAAA=Web_browser).

2. Sélectionnez la vignette **admin** .

3. Dans le centre d’administration 365 de Microsoft, sélectionnez **centres** d’administration \> **Exchange**.

4. Dans le centre d’administration Exchange, accédez à règles de **flux de messagerie** \> **Rules** et sélectionnez **nouvelle** ![ icône ](../media/457cd93f-22c2-4571-9f83-1b129bcfb58e.gif) \> **créer une nouvelle règle**. Pour plus d’informations sur l’utilisation du centre d’administration Exchange, consultez la rubrique [Exchange Admin Center in Exchange Online](https://docs.microsoft.com/exchange/exchange-admin-center).

5. Dans **nom**, tapez un nom pour la règle, par exemple, personnalisation pour le service des ventes.

6. Dans **appliquer cette règle si**, sélectionnez la condition que **l’expéditeur se trouve à l’intérieur de l’organisation** , ainsi que d’autres conditions de votre choix dans la liste des conditions disponibles. Par exemple, vous pouvez appliquer un modèle de personnalisation particulier à :

   - Tous les messages chiffrés envoyés par les membres du service financier
   - Messages chiffrés envoyés avec un mot clé tel que « externe » ou « partenaire »
   - Messages chiffrés envoyés à un domaine particulier

7. Dans **effectuer les opérations suivantes**, sélectionnez **modifier la sécurité des messages appliquer la**personnalisation  >  **aux messages OME**. Ensuite, dans la liste déroulante, sélectionnez un modèle de personnalisation parmi ceux que vous avez créés ou modifiés.

8. Module Si vous souhaitez que la règle de flux de messagerie applique le chiffrement en plus de la personnalisation, dans **effectuer les opérations suivantes**, sélectionnez **modifier la sécurité des messages**, puis **appliquer le chiffrement de messages Office 365 et protection des droits**. Sélectionnez un modèle RMS dans la liste, cliquez sur **Enregistrer**, puis choisissez **OK**.
  
   La liste des modèles inclut tous les modèles et options par défaut, ainsi que tous les modèles personnalisés que vous avez créés pour être utilisés par Office 365. Si la liste est vide, vérifiez que vous avez configuré le chiffrement de messages Office 365 avec les nouvelles fonctionnalités, comme décrit dans la rubrique [set up New Office 365 message Encryption Capabilities](set-up-new-message-encryption-capabilities.md). Pour plus d’informations sur les modèles par défaut, reportez-vous à la rubrique [Configuring and Managing Templates for Azure information protection](https://docs.microsoft.com/information-protection/deploy-use/configure-policy-templates). Pour plus d’informations sur l’option **ne pas transférer** , reportez-vous à l' [option ne pas transférer pour les messages électroniques](https://docs.microsoft.com/information-protection/deploy-use/configure-usage-rights#do-not-forward-option-for-emails). Pour plus d’informations sur l’option **chiffrer uniquement** , reportez-vous à la rubrique [chiffrer uniquement](https://docs.microsoft.com/information-protection/deploy-use/configure-usage-rights#encrypt-only-option-for-emails).

   Sélectionnez **Ajouter une action** si vous souhaitez spécifier une autre action.

## <a name="background-color-reference"></a>Référence de couleur d’arrière-plan

Les noms de couleur que vous pouvez utiliser pour la couleur d’arrière-plan sont limités. Au lieu d’un nom de couleur, vous pouvez utiliser une valeur de code hexadécimal (#RRGGBB). Vous pouvez utiliser une valeur de code hexadécimal correspondant à un nom de couleur, ou vous pouvez utiliser une valeur de code hexadécimal personnalisée. Veillez à placer la valeur de code hexadécimal entre guillemets (par exemple, `"#f0f8ff"` ).

Les noms de couleur d’arrière-plan disponibles et les valeurs de code hexadécimal correspondantes sont décrits dans le tableau suivant.

|||
|---|---|
|**Nom de la couleur**|**Code de couleur**|
|aliceblue|#f0f8ff|
|antiquewhite|#faebd7|
|cyan|#00ffff|
|vert eau marine|#7fffd4|
|bleu|#f0ffff|
|boîtier|#f5f5dc|
|bisque|#ffe4c4|
|black|#000000|
|blanchedalmond|#ffebcd|
|blue|#0000ff|
|blueviolet|#8a2be2|
|marron|#a52a2a|
|burlywood|#deb887|
|cadetblue|#5f9ea0|
|chartreuse|#7fff00|
|chocolat|#d2691e|
|Rail|#ff7f50|
|cornflowerblue|#6495ed|
|cornsilk|#fff8dc|
|Crimson|#dc143c|
|encre|#00ffff|
|darkblue|#00008b|
|darkcyan|#008b8b|
|darkgoldenrod|#b8860b|
|darkgray|#a9a9a9|
|darkgreen|#006400|
|darkkhaki|#bdb76b|
|darkmagenta|#8b008b|
|darkolivegreen|#556b2f|
|darkorange|#ff8c00|
|darkorchid|#9932cc|
|darkred|#8b0000|
|darksalmon|#e9967a|
|darkseagreen|#8fbc8f|
|darkslateblue|#483d8b|
|darkslategray|#2f4f4f|
|darkturquoise|#00ced1|
|darkviolet|#9400d3|
|deeppink|#ff1493|
|deepskyblue|#00bfff|
|dimgray|#696969|
|dodgerblue|#1e90ff|
|firebrick|#b22222|
|floralwhite|#fffaf0|
|forestgreen|#228b22|
|magenta|#ff00ff|
|gainsboro|#dcdcdc|
|ghostwhite|#f8f8ff|
|vert|#ffd700|
|jaune paille|#daa520|
|quadrichromiques|#808080|
|green|#008000|
|greenyellow|#adff2f|
|honeydew|#f0fff0|
|hotpink|#ff69b4|
|indianred|#cd5c5c|
|Indigo|#4b0082|
|ivoir|#fffff0|
|kaki|#f0e68c|
|lavande|#e6e6fa|
|lavenderblush|#fff0f5|
|lawngreen|#7cfc00|
|lemonchiffon|#fffacd|
|lightblue|#add8e6|
|lightcoral|#f08080|
|lightcyan|#e0ffff|
|lightgoldenrodyellow|#fafad2|
|lightgray|#d3d3d3|
|lightgrey|#d3d3d3|
|lightgreen|#90ee90|
|lightpink|#ffb6c1|
|lightsalmon|#ffa07a|
|lightseagreen|#20b2aa|
|lightskyblue|#87cefa|
|lightslategray|#778899|
|lightsteelblue|#b0c4de|
|lightyellow|#ffffe0|
|chaux|#00ff00|
|limegreen|#32cd32|
|Lin|#faf0e6|
|marron|#ff00ff|
|rouge foncé|#800000|
|mediumaquamarine|#66cdaa|
|mediumblue|#0000cd|
|mediumorchid|#ba55d3|
|mediumpurple|#9370db|
|mediumseagreen|#3cb371|
|mediumslateblue|#7b68ee|
|mediumspringgreen|#00fa9a|
|mediumturquoise|#48d1cc|
|mediumvioletred|#c71585|
|midnightblue|#191970|
|mintcream|#f5fffa|
|mistyrose|#ffe4e1|
|moccasin|#ffe4b5|
|navajowhite|#ffdead|
|bleu foncé|#000080|
|oldlace|#fdf5e6|
|vert olive|#808000|
|olivedrab|#6b8e23|
|orange|#ffa500|
|orangered|#ff4500|
|violet|#da70d6|
|palegoldenrod|#eee8aa|
|palegreen|#98fb98|
|paleturquoise|#afeeee|
|palevioletred|#db7093|
|papayawhip|#ffefd5|
|peachpuff|#ffdab9|
|Pérou|#cd853f|
|pink|#ffc0cb|
|séché|#dda0dd|
|powderblue|#b0e0e6|
|purple|#800080|
|red|#ff0000|
|rosybrown|#bc8f8f|
|royalblue|#4169e1|
|saddlebrown|#8b4513|
|saumon|#fa8072|
|sandybrown|#f4a460|
|vert|
|seashell|#fff5ee|
|Sienne|#a0522d|
|clair|#c0c0c0|
|skyblue|#87ceeb|
|slateblue|#6a5acd|
|slategray|#708090|
|bonhomme|#fffafa|
|springgreen|#00ff7f|
|steelblue|#4682b4|
|Tan|#d2b48c|
|teal|#008080|
|thistle|#d8bfd8|
|destinés|#ff6347|
|cyan|#40e0d0|
|asperge|#ee82ee|
|chaume|#f5deb3|
|white|#ffffff|
|whitesmoke|#f5f5f5|
|yellow|#ffff00|
|yellowgreen|#9acd32|
