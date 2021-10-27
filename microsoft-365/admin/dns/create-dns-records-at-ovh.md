---
title: Connecter vos enregistrements DNS sur OVH pour Microsoft 365
f1.keywords:
- CSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ROBOTS: NOINDEX, NOFOLLOW
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- BCS160
- MET150
- MOE150
ms.assetid: 5176feef-36dc-4d84-842f-1f2b5a21ba96
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online et les autres services sur OVH pour Microsoft.
ms.openlocfilehash: 7da9094a5d4cff2f93ab87251b29fc81bedc51ca
ms.sourcegitcommit: da11ffdf7a09490313dfc603355799f80b0c60f9
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/26/2021
ms.locfileid: "60587004"
---
# <a name="connect-your-dns-records-at-ovh-to-microsoft-365"></a>Connecter vos enregistrements DNS sur OVH pour Microsoft 365

[Consultez les FAQ des domaines](../setup/domains-faq.yml) si vous ne trouvez pas ce que vous recherchez. 
  
Si OVH est votre fournisseur d'hébergement DNS, procédez de la manière décrite dans cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
    
Une fois ces enregistrements ajoutés sur OVH, votre domaine est configuré pour utiliser les services Microsoft.

> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.

    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)

1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajoutez une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Sélectionnez **TXT**
    
    ![OvH sélectionnez l’entrée TXT.](../../media/3aaa9dae-0b1d-436b-a980-b67a970f31a9.png)
  
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 
    
    |**Type d’enregistrement**|**Sous-domaine**|**TTL**|**Value (Valeur)**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |(laissez vide)  <br/> |3600 secondes  <br/> |MS=msXXXXXXXX  <br/> **Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |
   
1. Sélectionnez **Suivant**.

1. Sélectionner **Confirmer**. 
    
    ![OvH confirm TXT for verification.](../../media/bde45596-9a55-4634-b5e7-16d7cde6e1b8.png)
  
1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié.
 
Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
1. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.** 

    :::image type="content" source="../../media/dns-IONOS/IONOS-DomainConnects-2.png" alt-text="Sélectionnez Démarrer l’installation.":::

1. Cliquez sur **Continuer**.
  
1. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
>  L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.
    
    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajoutez une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Sélectionnez **MX**.
    
    ![Type d’enregistrement OVH MX.](../../media/29b5e54e-440a-41f2-9eb9-3de573922ddf.png)
  
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 
    
    > [!NOTE]
    > Par défaut, OVH utilise une notation relative pour localiser la cible. Celle-ci s’ajoute au nom de domaine à la fin de l’enregistrement cible. Pour utiliser une notation absolue, ajoutez un point à l’enregistrement cible, ainsi que montré dans le tableau ci-dessous. 
  
    |**Sous-domaine**|**TTL (Durée de vie)**|**Priority (Priorité)**|**Cible**|
    |:-----|:-----|:-----|:-----|
    |(laissez vide)  <br/> |3600 secondes  <br/> |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> |\<domain-key\>.mail.protection.outlook.com  <br/> **Remarque :** Obtenez votre *\<domain-key\>* depuis votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)  |
   
    ![Enregistrement MX OVH pour le courrier.](../../media/6e2f5655-93e2-4620-8f19-c452e7edf8f0.png)
  
1. Sélectionnez **Suivant**.
    
    ![L’enregistrement MX OVH sélectionnez Suivant.](../../media/4db62d07-0dc4-49f6-bd19-2b4a07fd764a.png)
  
1. Sélectionner **Confirmer**.
    
    ![Enregistrement MX OVH sélectionnez Confirmer.](../../media/090bfb11-a753-4af0-8982-582a4069a169.png)

1. Supprimez tous les autres enregistrements MX de la liste sur la **page de zone DNS.** Sélectionnez chaque enregistrement et, dans la colonne **Actions,** sélectionnez l’icône **Supprimer de corbeille.** 
    
    ![L’ovh supprime l’enregistrement MX.](../../media/892b328b-7057-4828-b8c5-fe26284dc8c2.png)
  
1. Sélectionner **Confirmer**.
    
## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.
    
    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajoutez une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Sélectionnez **CNAME**.
    
    ![OVH Ajouter un type d’enregistrement CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 
    
    |**Sous-domaine**|**TTL (Durée de vie)**|**Cible**|
    |:-----|:-----|:-----|
    |autodiscover  <br/> |3600 secondes  <br/> |autodiscover.outlook.com.  <br/> |
   
    ![Enregistrement CNAME OVH.](../../media/516938b3-0b12-4736-a631-099e12e189f5.png)
  
1. Sélectionnez **Suivant**.
    
    ![OVH Ajoutez des valeurs CNAME et sélectionnez Suivant.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Sélectionner **Confirmer**.
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel de manière à n’avoir *qu’un seul* enregistrement SPF incluant les deux ensembles de valeurs. 
  
1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.
    
    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajoutez une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Sélectionnez **TXT**.
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 
    
    |**Sous-domaine**|**TTL**|**Value (Valeur)**|
    |:-----|:-----|:-----|
    |(laissez vide)  <br/> |3600 secondes  <br/> |v=spf1 include:spf.protection.outlook.com -all <br/**Remarque** : nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correct.           |
   
    ![OVH Ajouter un enregistrement TXT pour SPF.](../../media/f50466e9-1557-4548-8a39-e98978a5ee2e.png)
  
7. Sélectionnez **Suivant**.
    
    ![OVH Ajouter un enregistrement TXT pour SPF et sélectionner Suivant.](../../media/7937eb7c-114f-479f-a916-bcbe476d6108.png)
  
8. Sélectionner **Confirmer**.
    
    ![OVH Ajouter un enregistrement TXT pour SPF et Confirm.](../../media/649eefeb-3227-49e3-98a0-1ce19c42fa54.png)
  
## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis
    
1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.
    
    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajoutez une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **SRV**.
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 
    
    |**Sous-domaine**|**TTL (Seconds) (Durée de vie (secondes))**| **Priority (Priorité)** | **Weight (Poids)** | **Port (Port)**|**Target (Cible)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip._tls|3600 (s.) |100 |  1  | 443 |sipdir.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**><br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. | 
    |_sipfederationtls._tcp| 3600 (s.)|100 | 1 | 5061 | sipfed.online.lync.com. **Cette valeur DOIT se terminer par un point (.)**<br> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte.    | 
  
7. Pour ajouter l’autre enregistrement SRV, sélectionnez Ajouter un autre **enregistrement,** créez un enregistrement à l’aide des valeurs de la ligne suivante du tableau, puis sélectionnez Créer **des enregistrements.** 
    
> [!NOTE]
> Généralement, les modifications DNS sont appliquées dans les 15 minutes. Il peut toutefois arriver que la répercussion d’une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des difficultés avec le flux de courrier ou d’autres problèmes suite à l’ajout des enregistrements DNS, consultez la page [Rechercher et corriger les problèmes suite à l’ajout de votre domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 
    
1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.
    
    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajoutez une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)

1. Sélectionnez **CNAME**.
    
    ![OVH Ajouter un type d’enregistrement CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 

    |**Sous-domaine**| **TTL (Durée de vie)** | **Cible** | 
    |:-----|:-----|:-----|
    |sip  <br/> | 3600 (s.)  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |lyncdiscover  <br/> |3600 (s.) |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/>  |
  
1. Sélectionnez **Suivant**.
    
    ![OVH Ajoutez des valeurs CNAME et sélectionnez Suivant.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Sélectionner **Confirmer**.

1. Ajoutez l’autre enregistrement CNAME.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite deux enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. Pour commencer, accédez à la page de vos domaines sur le site d’OVH en utilisant [ce lien](https://www.ovh.com/manager/). Vous serez invité à vous connecter.
    
    ![Connexion OVH.](../../media/1424cc15-720d-49d1-b99b-8ba63b216238.png)
  
1. Sur la page d’accueil du tableau de bord, sous Afficher toutes **mes** activités, sélectionnez le nom du domaine à modifier.
  
1. Sélectionnez **zone DNS**.
    
    ![OVH Sélectionnez la zone DNS.](../../media/45218cbe-f3f8-4804-87f9-cfcef89ea113.png)
  
1. Sélectionnez **Ajouter une entrée**.
    
    ![OVH Ajouter une entrée.](../../media/13ded54b-9e48-4c98-8e1b-8c4a99633bc0.png)
  
1. Sélectionnez **CNAME**.
    
    ![OVH Ajouter un type d’enregistrement CNAME.](../../media/33c7ac74-18d7-4ae1-9e27-1c0f9773a3c3.png)
    
1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant. Pour affecter une valeur TTL, choisissez **Personnalisé** dans la liste de listes listes, puis tapez la valeur dans la zone de texte. 
  
    |**Sous-domaine**| **TTL (Durée de vie)** | **Cible** | 
    |:-----|:-----|:-----|
    |enterpriseregistration  <br/>| 3600 (s.)  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |
    |enterpriseenrollment  <br/>  |3600 (s.) |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/>|

1. Sélectionnez **Suivant**.
    
    ![OVH Ajouter des valeurs CNAME et sélectionner Suivant.](../../media/f9481cb1-559d-4da1-9643-9cacb0d80d29.png)
  
1. Sélectionner **Confirmer**.

1. Ajoutez l’autre enregistrement CNAME.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md).



  
