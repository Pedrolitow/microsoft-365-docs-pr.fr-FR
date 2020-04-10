---
title: Créer des enregistrements DNS sur easyDNS pour Office 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
search.appverid:
- MET150
- MOE150
ms.assetid: 446babfe-2e08-4cc2-bbfb-c05b854933ac
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur easyDNS pour Office 365.
ms.openlocfilehash: 9d48896de8f841863e25929a46b2f1d2e1b3ced2
ms.sourcegitcommit: 4a34b48584071e0c43c920bb35025e34cb4f5d15
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/09/2020
ms.locfileid: "43210551"
---
# <a name="create-dns-records-at-easydns-for-office-365"></a>Créer des enregistrements DNS sur easyDNS pour Office 365

[Consultez le Forum aux questions sur les domaines](../setup/domains-faq.md) si vous ne trouvez pas ce que vous recherchez. 
  
Vous devrez ajouter tous les enregistrements DNS suivants sur le site Web de votre registraire pour acheminer le courrier vers Office 365, utiliser votre domaine pour teams et Skype entreprise, et ainsi de suite.
  
Remarque : les enregistrements SRV ne sont actuellement pas disponibles dans tous les packages de service easyDNS. Vous devrez peut-être effectuer une mise à niveau vers un niveau de service supérieur avec easyDNS pour ajouter des enregistrements SRV requis pour Office 365 Skype entreprise.
  
## <a name="verify-that-you-own-the-domain-with-a-txt-record"></a>Vérifier que vous êtes propriétaire du domaine avec un enregistrement TXT

1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **txt Records (enregistrements TXT** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**Host**|**Text**|
    |:-----|:-----|
    |@  <br/> |MS = msXXXXXXXX (utilisez la valeur fournie dans la page domaines du centre d’administration)  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    
7. Patientez quelques minutes avant de poursuivre, afin que l’enregistrement que vous venez de créer puisse se propager sur Internet et soit détecté par Office 365.
    
8. L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez à Office 365 et demandez à Office 365 de rechercher l’enregistrement.
    
9. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
10. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
11. Sur la page **installation** , sélectionnez **Démarrer l’installation.**
    
12. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**. 
    
## <a name="add-an-mx-record-to-route-email-to-office-365"></a>Ajouter un enregistrement MX pour acheminer le courrier électronique vers Office 365

1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **MX Records (enregistrements MX** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**COURRIER POUR LA ZONE**|**SERVEUR DE MESSAGERIE**|**PRÉFÉRENCES**|
    |:-----|:-----|:-----|
    |@  <br/> |\<Key\>. mail.protection.Outlook.com (obtenir votre \<valeur de clé\> de domaine à partir de la page domaines du centre d’administration)  <br/> |0  <br/> |
   
2. Si vous souhaitez enregistrer vos autres enregistrements MX à des fins de sauvegarde, copiez-les quelque part. Avant de poursuivre, supprimez tous les autres enregistrements MX ici.
    
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    
## <a name="add-the-required-cname-records"></a>Ajouter les enregistrements CNAMe requis

1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous le titre **CNAME/alias Records** , cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :


    |**HOST (HÔTE)**|**Address (doit se terminer par un « . »)**|
    |:-----|:-----|
    |autodiscover  <br/> |autodiscover.outlook.com.  <br/> |
    |sip  <br/> |sipdir.online.lync.com.  <br/> |
    |lyncdiscover  <br/> |webdir.online.lync.com.  <br/> |
    |enterpriseregistration  <br/> |enterpriseregistration.windows.net.  <br/> |
    |enterpriseenrollment  <br/> |enterpriseenrollment-s.manage.microsoft.com.  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    
## <a name="add-a-txt-record-for-spf-to-help-prevent-email-spam"></a>Ajoutez un enregistrement TXT pour SPF afin d'éviter le courrier indésirable

1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **txt Records (enregistrements TXT** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**Host**|**Text**|
    |:-----|:-----|
    |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    
## <a name="add-the-two-srv-records-that-are-required-for-office-365"></a>Ajoutez les 2 enregistrements SRV requis pour Office 365

Remarque : les enregistrements SRV ne sont actuellement pas disponibles dans easyDNS’domaine plus niveau de service. Vous devrez peut-être effectuer une mise à niveau vers un niveau de service supérieur avec easyDNS pour ajouter des enregistrements SRV 
  
1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **SRV Records (enregistrements SRV** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**SERVICE**|**DEST**|**HOST (HÔTE)**|**PRI**|**WGT**|**PORT**|**CIBLE (doit se terminer par un « . »)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |TLS  <br/> |@  <br/> |100  <br/> |0,1  <br/> |443  <br/> |sipdir.online.lync.com.  <br/> |1800  <br/> |
    |_sipfederationtls  <br/> |TCP  <br/> |@  <br/> |100  <br/> |0,1  <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> |1800  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    

