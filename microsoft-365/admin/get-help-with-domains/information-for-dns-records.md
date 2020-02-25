---
title: Recueillez les informations nécessaires pour créer des enregistrements DNS Office 365
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: mnirkhe
audience: Admin
ms.topic: get-started-article
ms.service: o365-administration
localization_priority: Normal
ms.collection:
- M365-subscription-management
- Adm_O365
- Adm_TOC
- Adm_O365_Setup
search.appverid:
- BCS160
- MET150
- MOE150
- GEA150
ms.assetid: 77f90d4a-dc7f-4f09-8972-c1b03ea85a67
description: 'Découvrez comment trouver les valeurs/informations dont vous avez besoin pour créer des enregistrements DNS pour Office 365. '
ms.custom: okr_smb
ms.openlocfilehash: 7b995aedc21305367e4a6621781e138d0d60efd1
ms.sourcegitcommit: ca2b58ef8f5be24f09e73620b74a1ffcf2d4c290
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/24/2020
ms.locfileid: "42252917"
---
# <a name="gather-the-information-you-need-to-create-office-365-dns-records"></a>Recueillez les informations nécessaires pour créer des enregistrements DNS Office 365

 **[Consultez les Forums aux questions sur les domaines](../setup/domains-faq.md)** si vous ne trouvez pas ce que vous recherchez. 
  
### <a name="step-1-find-the-txt-record-value-and-verify"></a>Étape 1 : Rechercher la valeur de l’enregistrement TXT et vérifier

1. Dans le centre d’administration Microsoft 365, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> **d’installation** \> .
    
    Si vous utilisez Office 365 Germany, accédez à la page de ces <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> . 
    
    Si vous utilisez Office 365 géré par 21Vianet, accédez à la page de ce <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaine</a> .
    
2. Sur la page **domaines** , sélectionnez votre domaine, puis **Démarrer le programme d’installation**. Revenez à l'Assistant de configuration de domaines pour afficher la valeur spécifique que vous devez ajouter.
    
3. Sur la page **vérifier le domaine** , sélectionnez **Ajouter un enregistrement txt**à la place, puis sélectionnez **suivant**.
    
4. Copiez la **valeur txt** affichée. Il se présente comme ceci : **MS = msXXXXXXXX**. 
    
5. Accédez à [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS](create-dns-records-at-any-dns-hosting-provider.md)et sélectionnez votre hôte DNS dans la liste des bureaux d’enregistrement pour voir les instructions pas à pas.
    
6. Suivez les étapes permettant de créer l'enregistrement TXT (ou l'enregistrement MX) auprès de votre hôte DNS, puis vérifiez le domaine dans Office 365.

7. Supprimez l’enregistrement TXT (ou l’enregistrement MX) de votre hôte DNS une fois le domaine vérifié dans Office 365.
    
### <a name="step-2-find-the-mx-record-value-for-email-and-more"></a>Étape 2 : trouver la valeur de l’enregistrement MX pour la messagerie électronique et plus

1. Dans le centre d’administration Microsoft 365, accédez à la page <a href="https://go.microsoft.com/fwlink/p/?linkid=834818" target="_blank">domaines</a> **d’installation** \> .
    
    Si vous utilisez Office 365 Germany, accédez à la page de ces <a href="https://go.microsoft.com/fwlink/p/?linkid=854615" target="_blank">domaines</a> . 
    
    Si vous utilisez Office 365 géré par 21Vianet, accédez à la page de ce <a href="https://go.microsoft.com/fwlink/p/?linkid=2007048" target="_blank">domaine</a> .
    
2. Dans la page **Domaines**, sélectionnez votre domaine. 
    
3. Les enregistrements DNS à ajouter se trouvent sous **Paramètres DNS requis**.
    
    Il est recommandé de conserver ces informations disponibles tandis que vous apportez des modifications à votre hôte DNS, pour que vous puissiez copier et coller les valeurs.
    
    Les groupes d'enregistrements DNS figurant dans cette page dépendent des choix disponibles sous **Intention de domaine**.
    
4. Accédez à [créer des enregistrements DNS auprès d’un fournisseur d’hébergement DNS](create-dns-records-at-any-dns-hosting-provider.md), puis sélectionnez votre hôte DNS dans la liste des bureaux d’enregistrement pour voir les instructions pas à pas pour ajouter des enregistrements sur le site Web de l’hôte DNS.
    
5. Suivez la procédure de création des enregistrements auprès de votre hôte DNS.
