---
title: Ajouter un domaine à Microsoft 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_O365_Setup
- Adm_O365
- Adm_TOC
ms.custom:
- TopSMBIssues
- SaRA
- MSStore_Link
- okr_smb
- AdminSurgePortfolio
- AdminTemplateSet
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: Utilisez l’Assistant Installation pour ajouter votre domaine à Microsoft 365 dans le Centre d'administration Microsoft 365 en ajoutant un enregistrement DNS à votre hôte DNS.
ms.openlocfilehash: 7bb853e777ee0377ac0fb6ec6f7de453d4c4d4c7
ms.sourcegitcommit: 0ee2dabe402d44fecb6856af98a2ef7720d25189
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/09/2021
ms.locfileid: "61373235"
---
# <a name="add-a-domain-to-microsoft-365"></a>Ajouter un domaine à Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
## <a name="before-you-begin"></a>Avant de commencer

Pour ajouter, modifier ou supprimer des domaines, vous **devez** être administrateur **général** d’un [plan d’entreprise ou d’entreprise.](https://products.office.com/business/office) Ces modifications affectent l’ensemble du client . *Les administrateurs personnalisés* *ou* les utilisateurs réguliers ne pourront pas apporter ces modifications.

## <a name="watch-add-a-domain"></a>Regarder : Ajouter un domaine

> [!VIDEO https://www.microsoft.com/videoplayer/embed/RE4dN8c?autoplay=false]

Votre entreprise peut avoir besoin de plusieurs noms de domaine à des fins différentes. Par exemple, vous souhaitez peut-être ajouter une orthographe différente du nom de votre société, car les clients l’utilisent déjà et leurs communications n’ont pas pu vous joindre.

1. In the Centre d'administration Microsoft 365, choose <a href="https://go.microsoft.com/fwlink/p/?linkid=2171997" target="_blank">**Setup**</a>.
1. Under **Get your custom domain set up**, select **View**  >  **Manage**  >  **Add domain**.
1. Entrez le nouveau nom de domaine à ajouter, puis sélectionnez **Suivant.**
1. Connectez-vous à votre bureau d’enregistrement de domaines, puis sélectionnez **Suivant.**
1. Choisissez les services pour votre nouveau domaine.
1. Select **Next**  >  **Authorize**  >  **Next,** and then **Finish**. Votre nouveau domaine a été ajouté.

## <a name="add-a-domain"></a>Ajouter un domaine

Suivez ces étapes pour ajouter, configurer ou poursuivre la configuration d’un domaine. 

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Go to the **Paramètres**  >  **Domains** page. 

3. Sélectionnez **Ajouter un domaine**.
    
4. Entrez le nom du domaine que vous souhaitez ajouter, puis sélectionnez **Suivant**.
    
5. Choisissez la façon dont vous souhaitez vérifier que vous êtes propriétaire du domaine.
    
    1. Si votre bureau d’enregistrement de domaines utilise [domain Connecter](#domain-connect-registrars-integrating-with-microsoft-365), [Microsoft](../get-help-with-domains/domain-connect.md) configurera automatiquement vos enregistrements en vous connectant à votre bureau d’enregistrement et en confirmant la connexion à Microsoft 365. Vous serez renvoyé au Centre d’administration et Microsoft vérifiera ensuite automatiquement votre domaine.
    2. Vous pouvez utiliser un enregistrement TXT pour vérifier votre domaine. Sélectionnez ceci et **sélectionnez Suivant** pour voir les instructions d’ajout de cet enregistrement DNS au site web de votre bureau d’enregistrement. La vérification peut prendre jusqu’à 30 minutes après l’ajout de l’enregistrement. 
    3. Vous pouvez ajouter un fichier texte au site web de votre domaine. Sélectionnez et téléchargez le .txt à partir de l’Assistant Installation, puis téléchargez le fichier dans le dossier de niveau supérieur de votre site web. Le chemin d’accès au fichier doit ressembler à : `http://mydomain.com/ms39978200.txt` . Nous vous confirmerons que vous êtes propriétaire du domaine en trouvant le fichier sur votre site web.
    
6. Choisissez la façon dont vous souhaitez apporter les modifications DNS requises pour que Microsoft utilise votre domaine.
    
    1. Choisissez Ajouter les enregistrements **DNS** pour moi si votre bureau d’enregistrement prend en charge [domain Connecter](#domain-connect-registrars-integrating-with-microsoft-365)et [Microsoft](../get-help-with-domains/domain-connect.md) configurera vos enregistrements automatiquement en vous connectant à votre bureau d’enregistrement et en confirmant la connexion à Microsoft 365.
    2. Choisissez **J’ajouterai** les enregistrements DNS moi-même si vous souhaitez joindre uniquement des services Microsoft 365 spécifiques à votre domaine ou si vous souhaitez ignorer cette étape pour le moment et le faire ultérieurement. **Choisissez cette option si vous savez exactement ce que vous faites.**

7. Si vous avez choisi d’ajouter vous-même des enregistrements *DNS,*  sélectionnez **Suivant** et vous verrez une page avec tous les enregistrements que vous devez ajouter à votre site web de bureau d’enregistrement pour configurer votre domaine. 

    Si le portail ne reconnaît pas votre bureau d'enregistrement, vous pouvez [suivre ces instructions générales](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
    
    Si vous ne connaissez pas le fournisseur d'hébergement DNS ou le bureau d'enregistrement pour votre domaine, voir [Rechercher mon bureau d'enregistrement de domaines ou mon fournisseur d'hébergement DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    Si vous souhaitez attendre plus tard, désélectionnez tous les services et cliquez sur **Continuer,** ou à l’étape précédente de connexion de domaine, sélectionnez Plus **d’options** et sélectionnez Ignorer cette option **pour le moment.**
    
8. Select **Finish** - you’re done!

## <a name="add-or-edit-custom-dns-records"></a>Ajouter ou modifier des enregistrements DNS personnalisés

Suivez les étapes ci-dessous pour ajouter un enregistrement personnalisé pour un site web ou un service tiers.

1. Connectez-vous au Centre d’administration Microsoft à <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> l’adresse .

2. Go to the **Paramètres**   >  **Domains** page.

3. Dans la page **Domaines**, sélectionnez un domaine. 
    
4. Sous **paramètres DNS**, sélectionnez **Enregistrements personnalisés**; puis **sélectionnez Nouvel enregistrement personnalisé.**

5. Sélectionnez le type d’enregistrement DNS à ajouter et tapez les informations du nouvel enregistrement.
    
6. Cliquez sur **Enregistrer**.

## <a name="registrars-with-domain-connect"></a>Bureaux d’enregistrement avec Connecter

[Les Connecter](https://www.domainconnect.org/) bureaux d’enregistrement activés vous permettent d’ajouter votre domaine à Microsoft 365 dans un processus en trois étapes qui prend quelques minutes. 
  
Dans l’Assistant, nous allons simplement confirmer que vous êtes propriétaire du domaine, puis configurer automatiquement les enregistrements de votre domaine, afin que le courrier électronique soit envoyé à Microsoft 365 et d’autres services Microsoft 365, tels que Teams, fonctionnent avec votre domaine.
  
> [!NOTE]
> Veillez à désactiver les bloqueurs de fenêtres contextuelles dans votre navigateur avant de démarrer l'Assistant de configuration.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Intégration Connecter bureaux d’enregistrement de domaines Microsoft 365

- [1 &amp; 1 IONOS](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Iquésk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer ou WildWestDomains (revendeurs GoDaddy utilisant l’hébergement DNS SecureServer)
    - Exemples :
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>Qu’advient-il de mon courrier électronique et de mon site web ?

Une fois l’installation terminé, l’enregistrement MX de votre domaine est mis à jour pour pointer vers Microsoft 365 et tous les e-mails de votre domaine commenceront à Microsoft 365. Assurez-vous d’avoir ajouté des utilisateurs et de configurer des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui reçoit du courrier électronique sur votre domaine !
  
Si vous avez un site web que vous utilisez dans le cadre de votre activité, il continuera à fonctionner là où il se trouve. Les étapes de Connecter domaine n’affectent pas votre site web.

## <a name="related-content"></a>Contenu associé

[Forum aux questions sur les](domains-faq.yml) domaines (article) [Qu’est-ce qu’un domaine ?](../get-help-with-domains/what-is-a-domain.md) (article) [Acheter un nom de domaine dans Microsoft 365](../get-help-with-domains/buy-a-domain-name.md) (article)\
[Ajouter des enregistrements DNS pour connecter](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md) votre domaine (article) [Modifier](../get-help-with-domains/change-nameservers-at-any-domain-registrar.md) les serveurs de noms pour configurer Microsoft 365 avec n’importe quel bureau d’enregistrement de domaines (article)