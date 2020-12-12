---
title: Créer des enregistrements DNS sur easyDNS pour Microsoft
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
- Adm_O365
- Adm_NonTOC
- Adm_O365_Setup
ms.custom: AdminSurgePortfolio
search.appverid:
- MET150
- MOE150
ms.assetid: 446babfe-2e08-4cc2-bbfb-c05b854933ac
description: Découvrez comment vérifier votre domaine et configurer les enregistrements DNS pour la messagerie, Skype entreprise Online et d’autres services sur easyDNS pour Microsoft.
ms.openlocfilehash: a971a722f071ef5df9ce0fba387cfacfeb409f5b
ms.sourcegitcommit: 0a8b0186cc041db7341e57f375d0d010b7682b7d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "49656818"
---
# <a name="create-dns-records-at-easydns-for-microsoft"></a>Créer des enregistrements DNS sur easyDNS pour Microsoft

[Consultez le Forum aux questions sur les domaines ](../setup/domains-faq.yml) si vous ne trouvez pas ce que vous recherchez. 
  
Vous devrez ajouter tous les enregistrements DNS suivants sur le site Web de votre registraire pour acheminer le courrier vers Microsoft, utiliser votre domaine pour teams et Skype entreprise, et ainsi de suite.
  
Remarque : les enregistrements SRV ne sont actuellement pas disponibles dans tous les packages de service easyDNS. Vous devrez peut-être effectuer une mise à niveau vers un niveau de service supérieur avec easyDNS pour ajouter des enregistrements SRV qui sont requis pour Skype entreprise.
  
## <a name="verify-that-you-own-the-domain-with-a-txt-record"></a>Vérifier que vous êtes propriétaire du domaine avec un enregistrement TXT

1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **txt Records (enregistrements TXT** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**Host**|**Texte**|
    |:-----|:-----|
    |@  <br/> |MS = msXXXXXXXX (utilisez la valeur fournie dans la page domaines du centre d’administration)  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    
7. Patientez quelques minutes avant de poursuivre, afin que l’enregistrement que vous venez de créer puisse se propager sur Internet et soit détecté par Microsoft.
    
8. L’enregistrement étant désormais ajouté sur le site de votre bureau d’enregistrement de domaines, revenez sur Microsoft et demandez l’enregistrement.
    
9. Dans le centre d’administration, accédez à la page **Paramètres** \> <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">Domaines</a>.
    
10. Dans la page **Domaines**, sélectionnez le domaine que vous vérifiez. 
    
11. Sur la page **installation** , sélectionnez **Démarrer l’installation.**
    
12. Dans la page **Vérifier le domaine**, sélectionnez **Vérifier**. 
    
## <a name="add-an-mx-record-to-route-email-to-microsoft"></a>Ajouter un enregistrement MX pour acheminer le courrier électronique vers Microsoft

1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **MX Records (enregistrements MX** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**COURRIER POUR LA ZONE**|**SERVEUR DE MESSAGERIE**|**PRÉFÉRENCES**|
    |:-----|:-----|:-----|
    |@  <br/> |\<domain-key\>. mail.protection.outlook.com (obtenir votre \<domain-key\> valeur à partir de la page domaines du centre d’administration)  <br/> |0  <br/> |
   
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
    
    |**Host**|**Texte**|
    |:-----|:-----|
    |@  <br/> |v=spf1 include:spf.protection.outlook.com -all  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    
## <a name="add-the-two-srv-records-that-are-required-for-microsoft"></a>Ajoutez les deux enregistrements SRV requis pour Microsoft

Remarque : les enregistrements SRV ne sont actuellement pas disponibles dans easyDNS’domaine plus niveau de service. Vous devrez peut-être effectuer une mise à niveau vers un niveau de service supérieur avec easyDNS pour ajouter des enregistrements SRV 
  
1. Accédez à [https://cp.easydns.com/manage/domains/](https://cp.easydns.com/manage/domains/) et connectez-vous avec vos informations d’identification. 
    
2. Sous l’en-tête **tous les domaines** , sélectionnez **DNS.**
    
3. Sous l’en-tête **SRV Records (enregistrements SRV** ), cliquez sur le bouton modifier (icône de clé). 
    
4. Entrez les enregistrements suivants dans les champs de texte :
    
    |**SERVICE**|**DEST**|**HOST (HÔTE)**|**PRI**|**WGT**|**PORT**|**CIBLE (doit se terminer par un « . »)**|**TTL (Durée de vie)**|
    |:-----|:-----|:-----|:-----|:-----|:-----|:-----|:-----|
    |_sip  <br/> |TLS  <br/> |@  <br/> |100  <br/> |1   <br/> |443  <br/> |sipdir.online.lync.com.  <br/> |1800  <br/> |
    |_sipfederationtls  <br/> |TCP  <br/> |@  <br/> |100  <br/> |1   <br/> |5061  <br/> |sipfed.online.lync.com.  <br/> |1800  <br/> |
   
5. Sélectionnez **suivant**. 
    
6. Vérifiez que l’enregistrement est correct, puis sélectionnez **confirmer**. 
    

