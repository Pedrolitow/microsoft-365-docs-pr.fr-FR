---
title: Ajouter un domaine à Microsoft 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
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
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 6383f56d-3d09-4dcb-9b41-b5f5a5efd611
description: Ajoutez votre domaine à Microsoft 365 dans le centre d’administration Microsoft 365 en ajoutant un enregistrement DNS au niveau de votre hôte DNS. L’Assistant installation vous guide tout au long du processus.
ms.openlocfilehash: 3e7463bd4cf6b7836a9770421e0b8ce597524a67
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49658050"
---
# <a name="add-a-domain-to-microsoft-365"></a>Ajouter un domaine à Microsoft 365

::: moniker range="o365-21vianet"

> [!NOTE]
> Le centre d’administration change. Si votre expérience ne correspond pas aux informations présentées ici, voir [À propos du nouveau centre d’administration Microsoft 365](https://docs.microsoft.com/microsoft-365/admin/microsoft-365-admin-center-preview?view=o365-21vianet).

::: moniker-end

 **[Consultez les Forums aux questions sur les domaines](domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
 *Pour ajouter, modifier ou supprimer des domaines, vous **devez** être **administrateur général** d’un [plan d’entreprise ou d’entreprise](https://products.office.com/business/office). Ces modifications affectent l’ensemble du client, les *administrateurs personnalisés* ou *les utilisateurs réguliers* ne peuvent pas effectuer ces modifications.*  

 Procédez comme suit pour ajouter, configurer ou continuer à configurer un domaine. 

::: moniker range="o365-worldwide"
  
::: moniker-end

::: moniker range="o365-germany"

> [!VIDEO https://www.microsoft.com/videoplayer/embed/dda6df6d-37b0-41ff-905b-089448355a31?autoplay=false]
  
::: moniker-end

::: moniker range="o365-worldwide"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a>.

::: moniker-end
::: moniker range="o365-germany"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=848041" target="_blank">https://portal.office.de/adminportal</a>.

::: moniker-end

::: moniker range="o365-21vianet"

1. Accédez au Centre d’administration à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=850627" target="_blank">https://portal.partner.microsoftonline.cn</a>.

::: moniker-end
    
2. Accédez à la page **paramètres** des  >  **domaines** . 

3. Sélectionnez **Ajouter un domaine**.
    
4. Entrez le nom du domaine que vous souhaitez ajouter, puis cliquez sur **suivant**.
    
5. Choisissez la manière dont vous souhaitez vérifier que vous êtes propriétaire du domaine.
    
    1. Si votre bureau d’enregistrement de domaines utilise la [connexion au domaine](#domain-connect-registrars-integrating-with-microsoft-365), Microsoft [configure automatiquement vos enregistrements](../get-help-with-domains/domain-connect.md) en vous connectant à votre serveur d’inscriptions et en confirmant la connexion à Microsoft 365. Vous serez redirigé vers le centre d’administration et Microsoft vérifiera automatiquement votre domaine.
    2. Vous pouvez utiliser un enregistrement TXT pour vérifier votre domaine. Sélectionnez-le et cliquez sur **suivant** pour obtenir des instructions sur la façon d’ajouter cet enregistrement DNS au site Web de votre registraire. La vérification peut prendre jusqu’à 30 minutes après l’ajout de l’enregistrement. 
    3. Vous pouvez ajouter un fichier texte sur le site Web de votre domaine. Sélectionnez et téléchargez le fichier. txt à partir de l’Assistant Installation, puis téléchargez le fichier dans le dossier de niveau supérieur de votre site Web. Le chemin d’accès au fichier doit ressembler à ce qui suit : `http://mydomain.com/ms39978200.txt` . Nous vous confirmons que vous êtes propriétaire du domaine en trouvant le fichier sur votre site Web.
    
6. Choisissez comment vous souhaitez effectuer les modifications DNS requises pour que Microsoft utilise votre domaine.
    
    1. Sélectionnez **Ajouter les enregistrements DNS pour moi si votre serveur d'** inscriptions prend en charge la [connexion au domaine](#domain-connect-registrars-integrating-with-microsoft-365)et que Microsoft [configurera automatiquement vos enregistrements](../get-help-with-domains/domain-connect.md) en vous connectant à votre bureau d’enregistrement et en confirmant la connexion à Microsoft 365.
    2. Sélectionnez **j’aurai ajouté les enregistrements DNS moi-même** si vous souhaitez joindre uniquement des services Microsoft 365 spécifiques à votre domaine ou si vous souhaitez ignorer cette opération pour le moment et effectuer cette opération plus tard. **Choisissez cette option si vous savez exactement ce que vous faites.**

7. Si vous décidez d' *Ajouter des enregistrements DNS vous-même*  , sélectionnez **suivant** et vous verrez une page contenant tous les enregistrements que vous devez ajouter à votre site Web des registres pour configurer votre domaine. 

    Si le portail ne reconnaît pas votre bureau d'enregistrement, vous pouvez [suivre ces instructions générales](../get-help-with-domains/create-dns-records-at-any-dns-hosting-provider.md).
    
    Consultez notre liste d’[instructions spécifiques selon l’hôte](https://docs.microsoft.com/microsoft-365/admin/get-help-with-domains/set-up-your-domain-host-specific-instructions) pour rechercher votre hôte et suivre les étapes d’ajout des enregistrements dont vous avez besoin. 
    
    Si vous ne connaissez pas le fournisseur d'hébergement DNS ou le bureau d'enregistrement pour votre domaine, voir [Rechercher mon bureau d'enregistrement de domaines ou mon fournisseur d'hébergement DNS](../get-help-with-domains/find-your-domain-registrar.md).
    
    Si vous souhaitez attendre plus tard, désélectionnez tous les services et cliquez sur **Continuer**, ou dans l’étape connexion au domaine précédent, choisissez **plus d’options** et sélectionnez **Ignorer pour le moment**.
    
8. Sélectionnez **Terminer** -vous avez terminé !

## <a name="add-or-edit-custom-dns-records"></a>Ajouter ou modifier des enregistrements DNS personnalisés

Suivez les étapes ci-dessous pour ajouter un enregistrement personnalisé pour un site Web ou un service tiers.

1. Connectez-vous au centre d’administration Microsoft à l’adresse <a href="https://go.microsoft.com/fwlink/p/?linkid=2024339" target="_blank">https://admin.microsoft.com</a> .

2. Accédez à la page **paramètres** des   >  **domaines** .

3. Dans la page **Domaines**, sélectionnez un domaine. 
    
4. Sous **paramètres DNS**, sélectionnez **enregistrements personnalisés**; Ensuite, sélectionnez **nouvel enregistrement personnalisé**.

5. Sélectionnez le type d’enregistrement DNS que vous souhaitez ajouter et tapez les informations pour le nouvel enregistrement.
    
6. Sélectionnez **Enregistrer**.

## <a name="registrars-with-domain-connect"></a>Bureaux d’inscriptions avec connexion au domaine

Les bureaux d’accès activés pour la [connexion au domaine](https://www.domainconnect.org/) vous permettent d’ajouter votre domaine à Microsoft 365 dans un processus en trois étapes qui prend quelques minutes. 
  
Dans l’Assistant, nous confirmons que vous êtes propriétaire du domaine, puis vous configurez automatiquement les enregistrements de votre domaine, de sorte que le courrier électronique est envoyé à Microsoft 365 et d’autres services Microsoft 365, comme Teams, travaillez avec votre domaine.
  
> [!NOTE]
> Veillez à désactiver les bloqueurs de fenêtres contextuelles dans votre navigateur avant de démarrer l'Assistant de configuration.
  
### <a name="domain-connect-registrars-integrating-with-microsoft-365"></a>Bureaux de connexion au domaine intégration à Microsoft 365

- [1 &amp; 1 Ionos](https://www.1and1.com/)
- [EuroDNS](https://www.eurodns.com/)
- [Cloudflare](https://www.cloudflare.com/)
- [GoDaddy](https://www.godaddy.com/)
- [WordPress.com](https://wordpress.com/)
- [Plesk](https://www.plesk.com/)
- [MediaTemple](https://mediatemple.net/)
- SecureServer ou WildWestDomains (revendeurs GoDaddy utilisant SecureServer hébergement DNS)
    - Exemples :
        - [DomainsPricedRight](https://www.domainspricedright.com/products/domain-registration)
        - [DomainRightNow](https://www.domainrightnow.com/)

### <a name="what-happens-to-my-email-and-website"></a>Qu’arrive-t-il à mon courrier électronique et à mon site Web ?

Une fois que vous avez terminé l’installation, l’enregistrement MX de votre domaine est mis à jour pour pointer vers Microsoft 365 et tous les messages électroniques pour votre domaine vont débuter vers Microsoft 365. Assurez-vous que vous avez ajouté des utilisateurs et configuré des boîtes aux lettres dans Microsoft 365 pour toutes les personnes qui récupèrent du courrier électronique sur votre domaine !
  
Si vous avez un site web que vous utilisez dans le cadre de votre activité, il continuera à fonctionner là où il se trouve. Les étapes de configuration de la connexion au domaine n’affectent pas votre site Web.

## <a name="related-articles"></a>Articles connexes

[Foire aux questions domaines](domains-faq.yml)

[Qu’est-ce qu’un domaine ?](../get-help-with-domains/what-is-a-domain.md)

[Acheter un nom de domaine dans Microsoft 365](../get-help-with-domains/buy-a-domain-name.md)

[Configurer votre domaine (instructions spécifiques de l’hôte)](../get-help-with-domains/set-up-your-domain-host-specific-instructions.md)
