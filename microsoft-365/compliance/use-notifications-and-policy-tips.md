---
title: Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP
f1.keywords:
- CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.UnifiedDLPRuleNotifyUser
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
- SPO_Content
search.appverid:
- MOE150
- MET150
ms.custom: seo-marvel-apr2020
description: Découvrez comment ajouter un conseil de stratégie à une stratégie de protection contre la perte de données (DLP) pour informer un utilisateur qu'il travaille avec du contenu en conflit avec une stratégie DLP.
ms.openlocfilehash: c9756c9ebfc39427d665a6fc83d73070f8cdf52d
ms.sourcegitcommit: 05f40904f8278f53643efa76a907968b5c662d9a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/30/2021
ms.locfileid: "52114350"
---
# <a name="send-email-notifications-and-show-policy-tips-for-dlp-policies"></a>Envoi des notifications et affichage des conseils de stratégie pour les stratégies DLP

Vous pouvez utiliser une stratégie de protection contre la perte de données (DLP) pour identifier, surveiller et protéger les informations sensibles dans Office 365. Vous souhaitez que les membres de votre organisation qui travaillent avec ces informations sensibles restent conformes à vos stratégies DLP, mais vous ne voulez pas les empêcher inutilement de faire leur travail. C'est là que les notifications par courrier électronique et les conseils de stratégie peuvent vous aider.
  
![La barre des messages affiche le conseil de stratégie dans Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)
  
Un conseil de stratégie est une notification ou un avertissement qui s'affiche lorsqu'une personne travaille avec du contenu qui entre en conflit avec une stratégie DLP, par exemple, du contenu tel qu'un classez Excel sur un site OneDrive Entreprise qui contient des informations d'identification personnelle (PII) et qui est partagé avec un utilisateur externe.
  
Vous pouvez utiliser des notifications par courrier électronique et des conseils de stratégie pour mieux sensibiliser les personnes aux stratégies de votre organisation. Vous pouvez également donner aux personnes la possibilité de remplacer la stratégie, afin qu'elles ne sont pas bloquées s'ils ont des besoins commerciaux valides ou si la stratégie détecte un faux positif.
  
Dans le Centre de conformité de sécurité, lorsque vous créez une stratégie DLP, vous pouvez configurer les notifications utilisateur pour &amp; :
  
- Envoyez une notification par courrier électronique aux personnes de votre choix qui décrivent le problème.
    
- Affichez un conseil de stratégie pour le contenu en conflit avec la stratégie DLP :
    
  - Pour les messages électroniques dans Outlook sur le web et Outlook 2013 et ultérieurs, le conseil de stratégie apparaît en haut d'un message au-dessus des destinataires pendant la composition du message.
    
  - Pour les documents d'un OneDrive Entreprise ou d'un site SharePoint Online, le conseil de stratégie est indiqué par une icône d'avertissement qui apparaît sur l'élément. Pour afficher plus d'informations, vous  pouvez sélectionner un élément, puis choisir l'icône du volet Informations dans le coin supérieur droit de la page pour ouvrir le volet ![ ](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) d'informations. 
    
  - Pour les documents Excel, PowerPoint et Word stockés sur un site OneDrive Entreprise ou SharePoint Online inclus dans la stratégie DLP, le conseil de stratégie apparaît dans la barre des messages et le affichage Backstage **(** Informations sur le menu Fichier \> ).
    
## <a name="add-user-notifications-to-a-dlp-policy"></a>Ajouter des notifications utilisateur à une stratégie DLP

Lorsque vous créez une stratégie DLP, vous pouvez activer les **notifications utilisateur.** Lorsque les notifications utilisateur sont activées, Microsoft 365 envoie des notifications par courrier électronique et des conseils de stratégie. Vous pouvez personnaliser les personnes à qui les e-mails de notification sont envoyés, le texte du message électronique et le texte du conseil de stratégie.
  
1. Accédez à [https://protection.office.com](https://protection.office.com).
    
2. Connectez-vous à l’aide de votre compte scolaire ou professionnel. Vous êtes maintenant dans le Centre de conformité &amp; de sécurité.
    
3. Dans le Centre de conformité de sécurité navigation gauche Stratégie de protection contre la perte &amp; \> \> **de** \>  \> **données + Créer une stratégie**.
    
    ![Créer un bouton de stratégie](../media/b1e48a08-92e2-47ca-abdc-4341694ddc7c.png)
  
4. Choisissez le modèle de stratégie DLP qui protège les types d'informations sensibles dont vous avez \> besoin.
    
    Pour commencer avec un modèle vide, sélectionnez **Stratégie** \> **personnalisée personnalisée** \> **suivante.**
    
5. Nommez la stratégie \> **Suivant**.
    
6. Pour choisir les emplacements que la stratégie DLP doit protéger, faites l'une des choses suivantes :
    
   - Choose **All locations in Office 365** \> **Next**.
    
   - Choose **Let me choose specific locations** \> **Next**.
    
   Pour inclure ou exclure un emplacement entier tel que tous les e-mails  Exchange ou tous les comptes OneDrive, mettez l'état de cet emplacement sur ou hors service. 
    
   Pour inclure uniquement des sites SharePoint ou des comptes OneDrive  spécifiques, sélectionnez État,  puis cliquez sur les liens sous Inclure pour choisir des sites ou des comptes spécifiques. 
    
7. Choose **Use advanced settings** \> **Next**.
    
8. Sélectionnez **+ Nouvelle règle**.
    
9. Dans l'éditeur de règles, sous **Notifications de l'utilisateur,** basculez l'état sur.
    
    ![Section Notifications utilisateur de l'éditeur de règles](../media/47705927-c60b-4054-a072-ab914f33d15d.png)

> [!NOTE]
> Les stratégies DLP s'appliquent à tous les documents qui correspondent à la stratégie, que ces documents soient nouveaux ou existants. Toutefois, une notification par courrier électronique est générée uniquement lorsque le nouveau contenu correspond à une stratégie DLP existante. Le contenu existant est protégé, mais ne génère pas de notification de l'utilisateur par courrier électronique.
  
## <a name="options-for-configuring-email-notifications"></a>Options de configuration des notifications par courrier électronique

Pour chaque règle d'une stratégie DLP, vous pouvez :
  
- Envoyez la notification aux personnes de votre choix. Ces personnes peuvent inclure le propriétaire du contenu, la personne qui a modifié le contenu en dernier, le propriétaire du site où le contenu est stocké ou un utilisateur spécifique.
    
- Personnalisez le texte inclus dans la notification à l'aide de code HTML ou de jetons. Consultez la rubrique ci-dessous pour plus d’informations.
    
> [!NOTE]
>  Les notifications par courrier électronique peuvent être envoyées uniquement à des destinataires individuels, et non à des groupes ou des listes de distribution. Seul le nouveau contenu déclenche une notification par courrier électronique. La modification du contenu existant déclenche des conseils de stratégie, mais pas une notification par courrier électronique. 
  
![Options de notification par courrier électronique](../media/4e7b9500-2a78-44e6-9067-09f4bfd50301.png)
  
### <a name="default-email-notification"></a>Notification par défaut par courrier électronique

Les notifications ont une ligne d'objet qui commence par l'action prise, telle que « Notification », « Message bloqué » pour le courrier électronique ou « Accès bloqué » pour les documents. Si la notification concerne un document, le corps du message de notification inclut un lien qui vous permet d'accès au site où le document est stocké et ouvre le conseil de stratégie pour le document, où vous pouvez résoudre les problèmes (voir la section ci-dessous sur les conseils de stratégie). Si la notification concerne un message, la notification inclut en tant que pièce jointe le message qui correspond à une stratégie DLP.
  
![Message de notification](../media/35813d40-5fd8-425f-9624-55655e74fa6b.png)
  
Par défaut, les notifications affichent un texte semblable à ce qui suit pour un élément sur un site. Le texte de notification est configuré séparément pour chaque règle, de sorte que le texte affiché diffère en fonction de la règle qui correspond.

|**Si la règle de stratégie DLP le fait...**|**La notification par défaut pour SharePoint ou OneDrive Entreprise documents indique alors ceci...**|**La notification par défaut pour Outlook messages indique alors ceci...**|
|:-----|:-----|:-----|
|Envoie une notification, mais n'autorise pas le remplacement  <br/> |Cet élément est en conflit avec une stratégie de votre organisation.  <br/> |Votre message électronique est en conflit avec une stratégie de votre organisation.  <br/> |
|Bloque l'accès, envoie une notification et autorise le remplacement  <br/> |Cet élément est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l'accès à ce fichier peut être bloqué.  <br/> |Votre message électronique est en conflit avec une stratégie de votre organisation. Le message n'a pas été remis à tous les destinataires.  <br/> |
|Bloque l'accès et envoie une notification  <br/> |Cet élément est en conflit avec une stratégie de votre organisation. L'accès à cet élément est bloqué pour tout le monde sauf son propriétaire, son dernier modificateur et l'administrateur principal de la collection de sites.  <br/> |Votre message électronique est en conflit avec une stratégie de votre organisation. Le message n'a pas été remis à tous les destinataires.  <br/> |
   
### <a name="custom-email-notification"></a>Notification par courrier électronique personnalisé

Vous pouvez créer une notification par courrier électronique personnalisée au lieu d'envoyer la notification par courrier électronique par défaut à vos utilisateurs finaux ou administrateurs. La notification par courrier électronique personnalisé prend en charge le code HTML et présente une limite de 5 000 caractères. Vous pouvez utiliser du code HTML pour inclure des images, la mise en forme et d'autres marques dans la notification.
  
Vous pouvez également utiliser les jetons suivants pour vous aider à personnaliser la notification par courrier électronique. Ces jetons sont des variables qui sont remplacées par des informations spécifiques dans la notification envoyée.

|**Jeton**|**Description**|
|:-----|:-----|
|%%AppliedActions%%  <br/> |Actions appliquées au contenu.  <br/> |
|%%ContentURL%%  <br/> |URL du document sur le site SharePoint Online ou OneDrive Entreprise site.  <br/> |
|%%MatchedConditions%%  <br/> |Conditions qui ont été en correspondance avec le contenu. Utilisez ce jeton pour informer les utilisateurs des problèmes éventuels avec le contenu.  <br/> |
   
![Message de notification indiquant où apparaissent les jetons](../media/cd3f36b3-40db-4f30-99e4-190750bd1955.png)
  
## <a name="options-for-configuring-policy-tips"></a>Options de configuration des conseils de stratégie

Pour chaque règle d'une stratégie DLP, vous pouvez configurer des conseils de stratégie pour :
  
- Il suffit d'informer la personne que le contenu est en conflit avec une stratégie DLP, afin qu'elle puisse prendre des mesures pour résoudre le conflit. Vous pouvez utiliser le texte par défaut (voir les tableaux ci-dessous) ou entrer du texte personnalisé sur les stratégies spécifiques de votre organisation.
    
- Autorisez la personne à remplacer la stratégie DLP. Si vous le souhaitez, vous pouvez :
    
  - Exiger que la personne entre une justification professionnelle pour le remplacement de la stratégie. Ces informations sont consignées et vous pouvez les afficher dans les rapports DLP de la section **Rapports** du Centre de conformité &amp; de sécurité. 
    
  - Autorisez la personne à signaler un faux positif et à remplacer la stratégie DLP. Ces informations sont également enregistrées pour les rapports, afin que vous pouvez utiliser des faux positifs pour affiner vos règles.
    
![Options des conseils de stratégie](../media/0d2f2c68-028a-4900-afe6-1d9fce5303ef.png)
  
Par exemple, il se peut qu'une stratégie DLP soit appliquée aux sites OneDrive Entreprise qui détectent des informations d'identification personnelle (PII) et que cette stratégie possède trois règles :
  
1. Première règle : si moins de cinq instances de ces informations sensibles sont détectées dans un document et que le document est partagé avec des personnes au sein de l'organisation, l'action Envoyer une **notification** affiche un conseil de stratégie. Pour les conseils de stratégie, aucune option de remplacement n'est nécessaire, car cette règle consiste simplement à avertir les personnes et à ne pas bloquer l'accès. 
    
2. Deuxième règle : si plus de cinq instances de ces informations sensibles sont détectées dans  un document et que le document est partagé avec des personnes au sein de l'organisation, l'action Bloquer l'accès au contenu restreint les autorisations pour le fichier et l'action Envoyer une **notification** permet aux utilisateurs de remplacer les actions de cette règle en fournissant une justification professionnelle. L'entreprise de votre organisation nécessite parfois que des personnes internes partagent des données piI, et vous ne souhaitez pas que votre stratégie DLP bloque ce travail. 
    
3. Troisième règle : si plus de cinq instances de ces informations sensibles sont détectées dans  un document et que le document est partagé avec des personnes extérieures à l'organisation, l'action Bloquer l'accès au contenu limite les autorisations pour le fichier et l'action Envoyer une **notification** ne permet pas aux utilisateurs de remplacer les actions de cette règle, car les informations sont partagées en externe. En aucun cas les membres de votre organisation ne doivent être autorisés à partager des données d'informations personnelles à l'extérieur de l'organisation. 
    
Voici quelques points à comprendre sur l'utilisation d'un conseil de stratégie pour remplacer une règle :
  
- L'option de remplacement est par règle et elle remplace toutes les actions de la règle (à l'exception de l'envoi d'une notification, qui ne peut pas être substituer).
    
- Il est possible que le contenu corresponde à plusieurs règles dans une stratégie DLP, mais seul le conseil de stratégie de la règle la plus restrictive et la plus prioritaire s'affiche. Par exemple, un conseil de stratégie à partir d’une règle qui bloque l’accès au contenu est affiché sur un conseil de stratégie à partir d’une règle qui envoie simplement une notification. Cela évite que les personnes voient une cascade de conseils de stratégie.
    
- Si les conseils de stratégie de la règle la plus restrictive autorisent les utilisateurs à remplacer la règle, toute autre règle également mise en correspondance avec le contenu est aussi remplacée.
    
## <a name="policy-tips-on-onedrive-for-business-sites-and-sharepoint-online-sites"></a>Conseils de stratégie sur OneDrive Entreprise sites et sites SharePoint Online

Lorsqu'un document sur un site OneDrive Entreprise ou SharePoint Online correspond à une règle dans une stratégie DLP et que cette règle utilise des conseils de stratégie, les conseils de stratégie affichent des icônes spéciales dans le document :
  
1. Si la règle envoie une notification sur le fichier, l'icône d'avertissement s'affiche.
    
2. Si la règle bloque l'accès au document, l'icône bloquée s'affiche.
    
   ![Icônes de conseil de stratégie sur les documents dans un OneDrive de stratégie](../media/d3e9f772-03f9-4d28-82f8-3064784332a2.png)
  
Pour agir sur un document, vous pouvez sélectionner un élément en sélectionnant l'icône du volet Informations dans le coin supérieur droit de la page pour ouvrir le conseil de stratégie d'affichage du volet \>  ![ ](../media/50b6d51b-92b4-4c5f-bb4b-4ca2d4aa3d04.png) \> **d'informations.**
  
Le conseil de stratégie répertorie les problèmes avec le contenu, et si les  conseils de stratégie  sont configurés avec ces options, vous pouvez choisir **Résoudre,** puis remplacer le conseil de stratégie ou signaler un faux positif. 
  
![Volet d'informations affichant un conseil de stratégie](../media/0a191e70-80f0-4702-90f4-7a5b7aabcaab.png)
  
![Conseil de stratégie avec l’option de remplacement](../media/e250bff9-41d5-4ce4-82ea-1dc2d043fab1.png)
  
Les stratégies DLP sont synchronisées avec les sites et le contenu est évalué par rapport à ces derniers régulièrement et de manière asynchrone, de sorte qu'il peut y avoir un court délai entre le moment où vous créez la stratégie DLP et le moment où vous commencez à voir les conseils de stratégie. Il peut y avoir un délai similaire entre le moment où vous résolvez ou remplacez un conseil de stratégie jusqu'à la fin de l'icône du document sur le site.
  
### <a name="default-text-for-policy-tips-on-sites"></a>Texte par défaut pour les conseils de stratégie sur les sites

Par défaut, les conseils de stratégie affichent un texte semblable à ce qui suit pour un élément sur un site. Le texte de notification est configuré séparément pour chaque règle, de sorte que le texte affiché diffère en fonction de la règle qui correspond.

|**Si la règle de stratégie DLP le fait...**|**Ensuite, le conseil de stratégie par défaut indique ceci...**|
|:-----|:-----|
|Envoie une notification, mais n'autorise pas le remplacement  <br/> |Cet élément est en conflit avec une stratégie de votre organisation.  <br/> |
|Bloque l'accès, envoie une notification et autorise le remplacement  <br/> |Cet élément est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l'accès à ce fichier peut être bloqué.  <br/> |
|Bloque l'accès et envoie une notification  <br/> |Cet élément est en conflit avec une stratégie de votre organisation. L'accès à cet élément est bloqué pour tout le monde sauf son propriétaire, son dernier modificateur et l'administrateur principal de la collection de sites.  <br/> |
   
### <a name="custom-text-for-policy-tips-on-sites"></a>Texte personnalisé pour les conseils de stratégie sur les sites

Vous pouvez personnaliser le texte des conseils de stratégie séparément de la notification par courrier électronique. Contrairement au texte personnalisé pour les notifications par courrier électronique (voir la section ci-dessus), le texte personnalisé pour les conseils de stratégie n'accepte pas le code HTML ou les jetons. Au lieu de cela, le texte personnalisé pour les conseils de stratégie est du texte simple uniquement avec une limite de 256 caractères.
  
## <a name="policy-tips-in-outlook-on-the-web-and-outlook-2013-and-later"></a>Conseils de stratégie Outlook sur le web et Outlook 2013 et ultérieures

Lorsque vous rédigez un nouveau courrier électronique dans Outlook sur le web et Outlook 2013 et les ultérieures, vous verrez un conseil de stratégie si vous ajoutez du contenu qui correspond à une règle dans une stratégie DLP et que cette règle utilise des conseils de stratégie. Le conseil de stratégie apparaît en haut du message, au-dessus des destinataires, pendant que le message est composé.
  
![Conseil de stratégie en haut d'un message en cours de composition](../media/9b3b6b74-17c5-4562-82d5-d17ecaaa8d95.png)
  
Les conseils de stratégie fonctionnent si les informations sensibles apparaissent dans le corps du message, la ligne d'objet ou même une pièce jointe de message, comme illustré ici.
  
![Conseil de stratégie indiquant qu'une pièce jointe est en conflit avec une stratégie DLP](../media/59ae6655-215f-47d9-ad1d-39c0d1e61740.png)
  
Si les conseils de stratégie sont configurés pour autoriser le remplacement, vous pouvez choisir Afficher le remplacement des **détails** et entrer une justification professionnelle ou signaler un remplacement \>  \> faux \> **positif.**
  
![Conseil de stratégie dans le message développé pour afficher l'option Remplacer](../media/28bfb997-48a6-41f0-8682-d5e62488458a.png)
  
![Boîte de dialogue Conseil de stratégie dans laquelle vous pouvez remplacer le conseil de stratégie](../media/f97e836c-04bd-44b4-aec6-ed9526ea31f8.png)
  
Notez que lorsque vous ajoutez des informations sensibles à un e-mail, il peut y avoir une latence entre le moment où les informations sensibles sont ajoutées et le moment où le conseil de stratégie s'affiche.

### <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions"></a>Outlook 2013 et les ultérieures prend en charge l'affichage des conseils de stratégie uniquement pour certaines conditions

Actuellement, Outlook 2013 et les ultérieures ne prend en charge l'affichage des conseils de stratégie que pour les conditions suivantes :

- Le contenu contient
- Le contenu est partagé

Notez que les exceptions sont considérées comme des conditions et que toutes ces conditions fonctionnent dans Outlook, où elles correspondent au contenu et appliquent des actions de protection sur le contenu. Toutefois, l'affichage des conseils de stratégie aux utilisateurs n'est pas encore pris en charge. 
  
### <a name="policy-tips-in-the-exchange-admin-center-vs-the-security-amp-compliance-center"></a>Conseils de stratégie dans Exchange centre d'administration et le Centre de &amp; conformité de sécurité

Les conseils de stratégie peuvent fonctionner avec les stratégies DLP et les règles de flux de messagerie créées dans le Centre d'administration Exchange, ou avec les stratégies DLP créées dans le Centre de conformité de sécurité, mais pas les &amp; deux. En effet, ces stratégies sont stockées à différents emplacements, mais les conseils de stratégie ne peuvent dessiner qu'à partir d'un seul emplacement.
  
Si vous avez configuré des conseils de stratégie dans le Centre d'administration Exchange, les conseils de stratégie que vous configurez dans le Centre de conformité de sécurité n'apparaîtront pas pour les utilisateurs de Outlook sur le web et Outlook 2013 et ultérieurs tant que vous n'avez pas éteint les conseils du Centre d'administration &amp; Exchange. Cela garantit que vos règles de flux Exchange de messagerie (également appelées règles de transport) continueront de fonctionner jusqu'à ce que vous choisissiez de basculer vers le Centre de conformité de &amp; sécurité.
  
Notez que bien que les conseils de stratégie ne peuvent dessiner qu'à partir d'un seul emplacement, les notifications par courrier électronique sont toujours envoyées, même si vous utilisez des stratégies DLP à la fois dans le Centre de conformité de sécurité et le Centre d'administration &amp; Exchange.
  
### <a name="default-text-for-policy-tips-in-email"></a>Texte par défaut pour les conseils de stratégie dans le courrier électronique

Par défaut, les conseils de stratégie affichent un texte semblable à ce qui suit pour le courrier électronique.

|**Si la règle de stratégie DLP le fait...**|**Ensuite, le conseil de stratégie par défaut indique ceci...**|
|:-----|:-----|
|Envoie une notification, mais n'autorise pas le remplacement  <br/> |Votre courrier électronique est en conflit avec une stratégie de votre organisation.  <br/> |
|Bloque l'accès, envoie une notification et autorise le remplacement  <br/> |Votre courrier électronique est en conflit avec une stratégie de votre organisation.  <br/> |
|Bloque l'accès et envoie une notification  <br/> |Votre courrier électronique est en conflit avec une stratégie de votre organisation.  <br/> |
   
## <a name="policy-tips-in-excel-powerpoint-and-word"></a>Conseils de stratégie Excel, PowerPoint et Word

Lorsque des personnes travaillent avec du contenu sensible dans les versions de bureau de Excel, PowerPoint et Word, les conseils de stratégie peuvent les avertir en temps réel que le contenu entre en conflit avec une stratégie DLP. Cela nécessite que :
  
- Le Office document est stocké sur un site OneDrive Entreprise ou un site SharePoint Online.
    
- Le site est inclus dans une stratégie DLP configurée pour utiliser des conseils de stratégie.
    
Office programmes de bureau synchronisent automatiquement les stratégies DLP directement à partir de Office 365, puis analysent vos documents pour vous assurer qu'ils ne sont pas en conflit avec vos stratégies DLP et affichent des conseils de stratégie en temps réel.

> [!NOTE]
> Office applications de bureau analysent les documents eux-mêmes pour déterminer si les conseils de stratégie DLP doivent être affichés ; ils n'indiquent pas de conseils de stratégie SharePoint sites en ligne ou OneDrive Entreprise sites ont déjà déterminé qu'ils doivent être affichés sur un fichier. Par conséquent, un conseil de stratégie DLP n'est pas toujours visible dans les applications de bureau que vous voyez sur les sites SharePoint Online ou OneDrive Entreprise sites. En revanche, les applications Office sur le web n'indiquent que les conseils de stratégie DLP que les sites SharePoint Online ou les sites OneDrive Entreprise ont déjà déterminés doivent être affichés.
  
Selon la façon dont vous configurez les conseils de stratégie dans la stratégie DLP, les personnes peuvent choisir d'ignorer simplement le conseil de stratégie, de remplacer la stratégie avec ou sans justification professionnelle ou de signaler un faux positif.
  
Les conseils de stratégie apparaissent dans la barre des messages.
  
![La barre des messages affiche le conseil de stratégie dans Excel 2016](../media/7002ff54-1656-4a6c-993f-37427d6508c8.png)
  
Les conseils de stratégie apparaissent également en mode Backstage (sous **l'onglet** Fichier). 
  
![Le mode Backstage affiche les conseils de stratégie dans Excel 2016](../media/44c561f6-8f3f-4878-b1b0-b7543f8a4120.png)
  
Si les conseils de stratégie dans la stratégie DLP  sont configurés avec ces options, vous pouvez choisir Résoudre pour remplacer un conseil de stratégie ou signaler **un** faux positif.  
  
![Options relatives aux conseils de stratégie en mode Backstage dans Excel 2016](../media/5b3857ba-907e-456e-ae43-888b594c049c.png)
  
Dans chacun de ces Office de bureau, les utilisateurs peuvent choisir de désactiver les conseils de stratégie. Si ce paramètre est désactivé, les conseils de stratégie qui sont des notifications simples n'apparaissent pas dans la barre des messages ou en mode Backstage (sous **l'onglet** Fichier). Toutefois, les conseils de stratégie sur le blocage et le remplacement s'affichent toujours et ils reçoivent toujours la notification par courrier électronique. En outre, la non-application de conseils de stratégie n'exempte pas le document des stratégies DLP qui lui ont été appliquées. 
  
### <a name="default-text-for-policy-tips-in-excel-2016-powerpoint-2016-and-word-2016"></a>Texte par défaut pour les conseils de stratégie Excel 2016, PowerPoint 2016 et Word 2016

Par défaut, les conseils de stratégie affichent un texte semblable à ce qui suit dans la barre des messages et le mode Backstage d'un document ouvert. Le texte de notification est configuré séparément pour chaque règle, de sorte que le texte affiché diffère en fonction de la règle qui correspond.

|**Si la règle de stratégie DLP le fait...**|**Ensuite, le conseil de stratégie par défaut indique ceci...**|
|:-----|:-----|
|Envoie une notification, mais n'autorise pas le remplacement  <br/> |Ce fichier est en conflit avec une stratégie de votre organisation. Pour plus **d'informations,** voir le menu Fichier.  <br/> |
|Bloque l'accès, envoie une notification et autorise le remplacement  <br/> |Ce fichier est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l'accès à ce fichier peut être bloqué. Pour plus **d'informations,** voir le menu Fichier.  <br/> |
|Bloque l'accès et envoie une notification  <br/> |Ce fichier est en conflit avec une stratégie de votre organisation. Si vous ne résolvez pas ce conflit, l'accès à ce fichier peut être bloqué. Pour plus **d'informations,** voir le menu Fichier.  <br/> |
   
### <a name="custom-text-for-policy-tips-in-excel-powerpoint-and-word"></a>Texte personnalisé pour les conseils de stratégie dans Excel, PowerPoint et Word

Vous pouvez personnaliser le texte des conseils de stratégie séparément de la notification par courrier électronique. Contrairement au texte personnalisé pour les notifications par courrier électronique (voir la section ci-dessus), le texte personnalisé pour les conseils de stratégie n'accepte pas le code HTML ou les jetons. Au lieu de cela, le texte personnalisé pour les conseils de stratégie est du texte simple uniquement avec une limite de 256 caractères.
  
## <a name="more-information"></a>Plus d’informations

- [En savoir plus sur la protection contre la perte de données](dlp-learn-about-dlp.md)    
- [Création d’une stratégie DLP à partir d’un modèle](create-a-dlp-policy-from-a-template.md)
- [Conditions, exceptions et actions de stratégie DLP (aperçu)](./dlp-microsoft-teams.md) 
- [Créer une stratégie DLP pour protéger les documents avec l’ICF ou d’autres propriétés](protect-documents-that-have-fci-or-other-properties.md)
- [Contenu des modèles de stratégie DLP](what-the-dlp-policy-templates-include.md)
- [Définitions d’entités des types d’informations sensibles](sensitive-information-type-entity-definitions.md)