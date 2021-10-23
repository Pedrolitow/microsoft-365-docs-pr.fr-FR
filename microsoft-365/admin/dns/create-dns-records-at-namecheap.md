---
title: Connecter vos enregistrements DNS chez Namecheap pour Microsoft 365
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
ms.assetid: 54ae2002-b38e-43a1-82fa-3e49d78fda56
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype Entreprise Online et d’autres services sur Namecheap pour Microsoft.
ms.openlocfilehash: 5cc3a961e30e482b35c1646791eec9e03a065fbc
ms.sourcegitcommit: 3140e2866de36d57a27d27f70d47e8167c9cc907
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/23/2021
ms.locfileid: "60556637"
---
# <a name="connect-your-dns-records-at-namecheap-to-microsoft-365"></a>Connecter vos enregistrements DNS chez Namecheap pour Microsoft 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.yml)** si vous ne trouvez pas ce que vous recherchez. 
  
Si Namecheap est votre fournisseur d’hébergement DNS, suivez les étapes de cet article pour vérifier votre domaine et configurer les enregistrements DNS pour le courrier, Skype Entreprise Online, etc.
  
Une fois ces enregistrements ajoutés sur Namecheap, votre domaine est installé pour fonctionner avec services Microsoft.
  
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-a-txt-record-for-verification"></a>Ajouter un enregistrement TXT à des fins de vérification

Avant que vous puissiez utiliser votre domaine avec Microsoft, nous devons vérifier qu’il vous appartient. Votre capacité à vous connecter à votre compte auprès de votre bureau d’enregistrement de domaines et à créer l’enregistrement DNS prouve à Microsoft que le domaine vous appartient.
  
> [!NOTE]
> Cet enregistrement sert uniquement à vérifier que vous êtes propriétaire du domaine. Vous pouvez éventuellement le supprimer ultérieurement. 
  
1. To get started, go to your domains page at Namecheap by using [this link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You’ll be prompted to Sign in and Continue.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Sur la page d’accueil, sous **Compte,** choisissez **Liste** des domaines dans la liste. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste de domaines dans la liste de listes listes.":::

1. Dans la page Liste des domaines, sélectionnez le domaine à modifier, puis sélectionnez **Gérer.**

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé.**

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS HÔTES,** **sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.**

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la **baisse Type,** sélectionnez **Enregistrement TXT.**
    
    > [!NOTE]
    > La **drop-down** Type s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT.** 

     :::image type="content" source="../../media/a5b40973-19b5-4c32-8e1b-1521aa971836.png" alt-text="Sélectionnez Enregistrement TXT.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (Choisissez la **valeur TTL** dans la liste.) 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |MS=ms *XXXXXXXX*  <br/>**Remarque :** il s'agit d'un exemple. Utilisez votre valeur spécifique d’**Adresse de destination ou de pointage** ici, à partir du tableau.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md) |30 min  <br/> |

     :::image type="content" source="../../media/fe75c0fd-f85c-4bef-8068-edaf9779b7f1.png" alt-text="Copiez et collez les valeurs du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications** (coche). 

     :::image type="content" source="../../media/b48d2c67-66b5-4aa4-8e59-0c764f236fac.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Patientez quelques minutes, le temps que l'enregistrement que vous venez de créer soit mis à jour sur Internet.
    
L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement. Lorsque Microsoft trouve l’enregistrement TXT approprié, votre domaine est vérifié. 

Pour vérifier l’enregistrement dans Microsoft 365 :
  
1. Dans le Centre d’administration, go to the **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">**Domains**</a>.
    
2. Dans la page Domaines, sélectionnez le domaine que vous vérifiez, puis sélectionnez **Démarrer la configuration.**   
  
3. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="add-an-mx-record-so-email-for-your-domain-will-come-to-microsoft"></a>Ajouter un enregistrement MX afin que les courriers électroniques pour votre domaine soient transférés vers Microsoft
  
1. To get started, go to your domains page at Namecheap by using [this link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You’ll be prompted to Sign in and Continue.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Sur la page d’accueil, sous **Compte,** choisissez **Liste** des domaines dans la liste. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste de domaines dans la liste.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine à modifier, puis sélectionnez **Gérer.**

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé.**

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **PARAMÈTRES DU COURRIER,** sélectionnez  **MX personnalisé** dans la liste de listes de listes bas de courrier. 
    
    (Vous devrez peut-être faire défiler la page vers le bas.)

     :::image type="content" source="../../media/40199e2c-42cf-4c3f-9936-3cbe5d4e81a4.png" alt-text="Sélectionnez MX personnalisé."::: 

1. Sélectionnez **Ajouter un nouvel enregistrement.**

     :::image type="content" source="../../media/8d169b81-ba48-4d51-84ea-a08fa1616457.png" alt-text="AJOUTEZ UN NOUVEL ENREGISTREMENT.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs du tableau suivant.
    
    (La **zone** Priorité est la zone sans nom à droite de la **zone** Valeur. Choisissez la **valeur TTL** dans la liste.) 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**Priorité**|**TTL**|
    |:-----|:-----|:-----|:-----|:-----|
    |MX Record (Enregistrement MX)  <br/> |@  <br/> |\<*domain-key*\>.mail.protection.outlook.com  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> **Remarque :** Obtenez votre *\<domain-key\>* depuis votre compte Microsoft.  [Comment trouver cette valeur ?](../get-help-with-domains/information-for-dns-records.md)          |0  <br/> Pour plus d'informations sur la priorité, voir [Qu'est-ce que la priorité MX ?](../setup/domains-faq.yml). <br/> |30 min  <br/> |

     :::image type="content" source="../../media/f3b76d62-5022-48c1-901b-8615a8571309.png" alt-text="Copiez et collez les valeurs du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications** (coche). 

     :::image type="content" source="../../media/ef4e3112-36d2-47c8-a478-136a565dd71d.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. S'il existe d'autres enregistrements MX, utilisez le processus en deux étapes suivant pour supprimer chacun d'eux :
    
    Tout **d’abord, sélectionnez Supprimer** (corbeille) pour l’enregistrement à supprimer. 

     :::image type="content" source="../../media/7a7a751f-29c2-495f-8f55-98ca37ce555a.png" alt-text="Sélectionnez Supprimer.":::

    Ensuite, **sélectionnez Oui** pour confirmer la suppression. 

     :::image type="content" source="../../media/85ebc0c7-8787-43ee-9e7b-647375b3345c.png" alt-text="Sélectionnez Oui.":::

    Supprimez tous les enregistrements MX à l’exception de celui que vous avez ajouté précédemment dans cette procédure.
  
## <a name="add-the-cname-record-required-for-microsoft"></a>Ajouter l’enregistrement CNAME requis pour Microsoft

1. To get started, go to your domains page at Namecheap by using [this link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You’ll be prompted to Sign in and Continue.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Sur la page d’accueil, sous **Compte,** choisissez **Liste** des domaines dans la liste. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste des domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine à modifier, puis sélectionnez **Gérer.**

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé.**

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS HÔTES,** **sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.**

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la **boîte de** drop-down Type, sélectionnez **Enregistrement CNAME.**
    
    > [!NOTE]
    > La **drop-down** Type s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT.** 

     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Sélectionnez Enregistrement CNAME.":::

1. Dans les zones vides du nouvel enregistrement, sélectionnez le **Type d'enregistrement** **CNAME**, puis tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |autodiscover  <br/> |autodiscover.outlook.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |

     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Copiez et collez les valeurs du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications** (coche). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

> [!IMPORTANT]
> Vous ne pouvez avoir qu’un enregistrement TXT pour SPF pour un domaine. Si votre domaine comporte plusieurs enregistrements SPF, vous rencontrez des erreurs au niveau de la transmission du courrier électronique ainsi que des problèmes de remise du courrier et de classification en tant que courrier indésirable. Si vous avez déjà un enregistrement SPF pour votre domaine, il n’est pas nécessaire d’en créer un nouveau pour Microsoft. Ajoutez plutôt les valeurs Microsoft requises à l’enregistrement actuel afin de n’avoir qu’un seul *enregistrement*  SPF qui inclut les deux ensembles de valeurs. 

1. To get started, go to your domains page at Namecheap by using [this link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You’ll be prompted to Sign in and Continue.
    
1. Sur la page d’accueil, sous **Compte,** choisissez **Liste** des domaines dans la liste. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste des domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine à modifier, puis sélectionnez **Gérer.**

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé.**

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS HÔTES,** **sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.**

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la **baisse Type,** sélectionnez **Enregistrement TXT.**
    
    > [!NOTE]
    > La **drop-down** Type s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT.** 

     :::image type="content" source="../../media/c5d1fddb-28b5-48ec-91c9-3e5d3955ac80.png" alt-text="Sélectionnez Enregistrement TXT.":::

1. Dans les zones du nouvel enregistrement, tapez ou copiez-collez les valeurs suivantes du tableau suivant.
    
    (Choisissez la **valeur TTL** dans la liste.) 
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |TXT  <br/> |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> **Remarque :** nous vous recommandons de copier et coller cette entrée, afin que l’espacement reste correcte. |30 min  <br/> |

     :::image type="content" source="../../media/ea0829f1-990b-424b-b26e-9859468318dd.png" alt-text="Copiez et collez les valeurs du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications** (coche). 

     :::image type="content" source="../../media/f2846c36-ace3-43d8-be5d-a65e2c267619.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

## <a name="advanced-option-skype-for-business"></a>Option avancée : Skype Entreprise

Sélectionnez cette option uniquement si votre organisation utilise Skype Entreprise pour les services de communication en ligne tels que les conversation, les appels de conférence et les appels vidéo, en plus de Microsoft Teams. Skype nécessite 4 enregistrements : 2 enregistrements SRV pour la communication utilisateur à utilisateur et 2 enregistrements CNAME pour se connecter et connecter des utilisateurs au service.

### <a name="add-the-two-required-srv-records"></a>Ajouter les deux enregistrements SRV requis

1. To get started, go to your domains page at Namecheap by using [this link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You'll be prompted to sign in.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Sur la page d’accueil, sous **Compte,** choisissez **Liste** des domaines dans la liste. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Choisissez Liste des domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine à modifier, puis sélectionnez **Gérer.**

     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé.**

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez DNS avancé.":::

1. Dans la section **ENREGISTREMENTS HÔTES,** **sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.**

     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la **drop-down Type,** sélectionnez **Enregistrement SRV.**
    
    > [!NOTE]
    > La **drop-down** Type s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT.** 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Sélectionnez le type d’enregistrement SRV.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau suivant.
    
    |**Service**|**Protocol (Protocole)**|**Priority (Priorité)**|**Weight (Poids)**|**Port (Port)**|**Target (Cible)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |_tls  <br/> |100  <br/> |1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |
    |_sipfederationtls  <br/> |_tcp  <br/> |100  <br/> |1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |
       
     :::image type="content" source="../../media/ff9566ea-0096-4b7f-873c-027080a23b56.png" alt-text="Copiez et collez les valeurs du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications** (coche). 

     :::image type="content" source="../../media/48a8dee4-c66d-449d-8759-9e9784c82b13.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Ajoutez l’autre enregistrement SRV en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis 
  
1. Dans la section **ENREGISTREMENTS HÔTES,** **sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.**
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEAU NOM.":::

1. Dans la **boîte de** drop-down Type, sélectionnez **CNAME**.
    
    > [!NOTE]
    > La **drop-down** Type s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT.** 

     :::image type="content" source="../../media/fd55cd7c-2243-4de1-8d39-2c3f7ea3ae51.png" alt-text="Sélectionnez CNAME.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau.
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |sip  <br/> |sipdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |
    |CNAME  <br/> |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Copiez et collez les valeurs CNAME du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications** (coche). 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 
  
## <a name="advanced-option-intune-and-mobile-device-management-for-microsoft-365"></a>Option avancée : Intune et gestion des périphériques mobiles pour Microsoft 365

Ce service vous permet de sécuriser et de gérer à distance les appareils mobiles qui se connectent à votre domaine. La gestion des périphériques mobiles nécessite deux enregistrements CNAME afin que les utilisateurs peuvent inscrire des appareils au service.

### <a name="add-the-two-required-cname-records"></a>Ajouter les deux enregistrements CNAME requis

1. To get started, go to your domains page at Namecheap by using [this link](https://www.namecheap.com/myaccount/login.aspx?ReturnUrl=%2f). You'll be prompted to sign in.

     :::image type="content" source="../../media/1827f9fc-4dc9-4f9d-a392-7817c47b00b3.png" alt-text="Connectez-vous à Namecheap.":::

1. Sur la page d’accueil, sous **Compte,** choisissez **Liste** des domaines dans la liste. 

     :::image type="content" source="../../media/3f457d64-4589-422c-ae34-fc24b0e819eb.png" alt-text="Sélectionnez Liste des domaines.":::

1. Dans la page **Liste des** domaines, sélectionnez le domaine à modifier, puis sélectionnez **Gérer.**
    
     :::image type="content" source="../../media/fb2020d8-707c-4148-835e-304ac6244d66.png" alt-text="Sélectionnez Gérer.":::

1. Sélectionnez **DNS avancé.**

     :::image type="content" source="../../media/05a4f0b9-1d27-448e-9954-2b23304c5f65.png" alt-text="Sélectionnez Gérer les enregistrements DNS dans la liste liste.":::

1. Dans la section **ENREGISTREMENTS HÔTES,** **sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.**
    
     :::image type="content" source="../../media/8849abfe-deb6-4f6a-b56d-e69be9a28b0f.png" alt-text="Sélectionnez AJOUTER UN NOUVEL ENREGISTREMENT.":::

1. Dans la **boîte de** drop-down Type, sélectionnez **Enregistrement CNAME.**
    
    > [!NOTE]
    > La **drop-down** Type s’affiche automatiquement lorsque vous sélectionnez **AJOUTER UN NOUVEL ENREGISTREMENT.** 
  
     :::image type="content" source="../../media/0898f3b2-06ab-4364-a86a-a603a25b39f4.png" alt-text="Sélectionnez Enregistrement CNAME.":::

1. Dans les zones vides des nouveaux enregistrements, tapez ou copiez-collez les valeurs de la première ligne du tableau.
    
    |**Type**|**Host (Hôte)**|**Valeur**|**TTL**|
    |:-----|:-----|:-----|:-----|
    |CNAME  <br/> |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |
    |CNAME  <br/> |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> **Cette valeur DOIT se terminer par un point (.)** <br/> |Automatique  <br/> |
       
     :::image type="content" source="../../media/f79c5679-34eb-4544-8517-caa2e8a4111a.png" alt-text="Copiez et collez les valeurs du tableau.":::

1. Sélectionnez **le contrôle Enregistrer les modifications.** 

     :::image type="content" source="../../media/91a5cce4-ca41-41ec-b976-aafe681a4d68.png" alt-text="Sélectionnez le contrôle Enregistrer les modifications.":::

1. Ajoutez l’autre enregistrement CNAME en choisissant les valeurs de la deuxième ligne du tableau.
    
> [!NOTE]
> L'application des enregistrements DNS modifiés prend généralement 15 minutes. Il peut toutefois arriver que la répercussion d'une modification dans le système DNS sur Internet prenne davantage de temps. Si vous rencontrez des problèmes avec le flux de messages ou d'autres problèmes suite à l'ajout des enregistrements DNS, voir [Résolution des problèmes suite à la modification de votre nom de domaine ou des enregistrements DNS](../get-help-with-domains/find-and-fix-issues.md). 


