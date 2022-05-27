---
title: Ce que les modèles de stratégie DLP incluent
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: 6/29/2018
audience: Admin
ms.topic: reference
f1_keywords:
- ms.o365.cc.DLPNewPolicyFromTemplate
ms.service: O365-seccomp
ms.collection:
- M365-security-compliance
ms.localizationpriority: medium
search.appverid:
- MOE150
- MET150
ms.custom:
- seo-marvel-apr2020
recommendations: false
description: Découvrez ce que les modèles de stratégie de protection contre la perte de données (DLP) dans le portail de conformité Microsoft Purview incluent.
ms.openlocfilehash: 145f5b2a180023811afa8b5795bfa8b9d24f82f5
ms.sourcegitcommit: 6a981ca15bac84adbbed67341c89235029aad476
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/27/2022
ms.locfileid: "65753500"
---
# <a name="what-the-dlp-policy-templates-include"></a>Ce qu’incluent les modèles de stratégie DLP

[!include[Purview banner](../includes/purview-rebrand-banner.md)]

Protection contre la perte de données Microsoft Purview (DLP) dans le portail de conformité Microsoft Purview inclut des modèles de stratégie prêts à l’emploi qui répondent aux exigences de conformité courantes, comme vous aider à protéger les informations sensibles soumises à l’intégrité des États-Unis Loi sur l’assurance (HIPAA), U.S. Gramm-Leach-Bliley Act (GLBA), ou U.S. Patriot Act. Cet article répertorie tous les modèles de stratégie, les types d’informations sensibles qu’ils recherchent et les conditions et actions par défaut. Cet article n’inclut pas tous les détails de la façon dont chaque modèle de stratégie est configuré ; Au lieu de cela, l’article vous présente suffisamment d’informations pour vous aider à déterminer quel modèle est le meilleur point de départ pour votre scénario. N’oubliez pas que vous pouvez personnaliser ces modèles de stratégie pour répondre à vos besoins spécifiques.
  
## <a name="australia-financial-data"></a>Données financières en Australie

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour l’Australie : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de fichier fiscal australien - Nombre minimal 1, nombre maximal de 9  <br/>  Numéro de compte bancaire en Australie - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour l’Australie : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de fichier fiscal australien - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de compte bancaire de l’Australie - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="australia-health-records-act-hrip-act"></a>Australia Health Records Act (HRIP Act)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi HRIP australienne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de fichier fiscal australien - Nombre minimal 1, nombre maximal de 9  <br/>  Numéro de compte médical en Australie - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi HRIP australienne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de fichier fiscal australien - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de compte médical en Australie - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="australia-personally-identifiable-information-pii-data"></a>Australia Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour l’Australie : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de fichier fiscal australien - Nombre minimal 1, nombre maximal de 9  <br/>  Numéro de permis de conduire australie - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour l’Australie : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de fichier fiscal australien - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de permis de conduire de l’Australie - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="australia-privacy-act"></a>Australia Privacy Act

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Protection des données pour l’Australie : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire australie - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de passeport de l’Australie - Nombre minimal 1, Nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Protection des données pour l’Australie : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire de l’Australie - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de passeport australie - Nombre minimal de 10, nombre maximal de 500 <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-financial-data"></a>Données financières au Canada

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour le Canada : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour le Canada : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire du Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-health-information-act-hia"></a>Canada Health Information Act (HIA)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi HIA canadienne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de passeport canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Canada Service de contrôle d'intégrité Nombre - Nombre minimal 1, Nombre maximal 9  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi HIA canadienne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de passeport canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Nombre Service de contrôle d'intégrité Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-personal-health-act-phipa---ontario"></a>Canada Personal Health Act (PHIPA) - Ontario

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi LPRPS canadienne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de passeport canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Canada Service de contrôle d'intégrité Nombre - Nombre minimal 1, Nombre maximal 9  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi LPRPS canadienne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de passeport canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Nombre Service de contrôle d'intégrité Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-personal-health-information-act-phia---manitoba"></a>Canada Personal Health Information Act (PHIA) - Manitoba

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi LRMP canadienne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Canada Service de contrôle d'intégrité Nombre - Nombre minimal 1, Nombre maximal 9  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi LRMP canadienne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Nombre Service de contrôle d'intégrité Canada - Nombre minimal 10, nombre maximal de 500 <br/>  Canada Personal Health Identification Number (PHIN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-personal-information-protection-act-pipa"></a>Canada Personal Information Protection Act (PIPA)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi PIPA canadienne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de passeport canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Canada Service de contrôle d'intégrité Nombre - Nombre minimal 1, Nombre maximal 9  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi PIPA canadienne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de passeport canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Nombre Service de contrôle d'intégrité Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-personal-information-protection-act-pipeda"></a>Canada Personal Information Protection and Electronic Documents Act (PIPEDA)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi LPRPDE canadienne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire au Canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de passeport canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Canada Service de contrôle d'intégrité Nombre - Nombre minimal 1, Nombre maximal 9  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi LPRPDE canadienne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire au Canada - Nombre minimal de 10, nombre maximal de 500 <br/>  Numéro de compte bancaire du Canada - Nombre minimal 10, nombre maximal de 500 <br/>  Numéro de passeport canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Nombre Service de contrôle d'intégrité Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 10, Max count 500 <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="canada-personally-identifiable-information-pii-data"></a>Canada Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour le Canada : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire au Canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de passeport canada - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal 1, nombre maximal 9  <br/>  Canada Service de contrôle d'intégrité Nombre - Nombre minimal 1, Nombre maximal 9  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour le Canada : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire au Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire du Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de passeport canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Canada - Nombre minimal de 10, nombre maximal de 500  <br/>  Nombre Service de contrôle d'intégrité Canada - Nombre minimal 10, nombre maximal de 500  <br/>  Canada Personal Health Identification Number (PHIN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="france-data-protection-act"></a>Loi informatique et liberté en France

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi sur la protection des données pour la France : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Carte nationale d’ID de France (CNI) - Nombre minimal 1, nombre maximal de 9  <br/>  Numéro de sécurité sociale en France (INSEE) - Nombre minimal 1, nombre maximal de 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi sur la protection des données pour la France : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Carte nationale d’ID de France (CNI) - Min count 10, Max count 500  <br/>  Numéro de sécurité sociale en France (INSEE) - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="france-financial-data"></a>Données financières en France

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour la France : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de carte de débit de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour la France : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de carte de débit de l’UE - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="france-personally-identifiable-information-pii-data"></a>France Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour la France : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de sécurité sociale en France (INSEE) - Nombre minimal 1, nombre maximal de 9  <br/>  Numéro de permis de conduire france - Nombre minimal 1, nombre maximal de 9  <br/>  Numéro de passeport france - Nombre minimal 1, nombre maximal 9  <br/>  Carte nationale d’ID de France (CNI) - Nombre minimal 1, nombre maximal de 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour la France : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de sécurité sociale en France (INSEE) - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de permis de conduire france - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de passeport france - Nombre minimal de 10, nombre maximal de 500  <br/>  Carte nationale d’ID de France (CNI) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="general-data-protection-regulation-gdpr"></a>Règlement général sur la protection des données (RGPD)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Contenu sensible à l’UE à faible volume trouvé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de débit de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de permis de conduire de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’identification nationale de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de passeport de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de sécurité sociale de l’UE (SSN) ou ID équivalent - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’identification fiscale de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer des rapports d’incident à l’administrateur  <br/> |
|Volume élevé de contenu sensible de l’UE trouvé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de débit de l’UE - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de permis de conduire de l’UE - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’identification nationale de l’UE - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de passeport de l’UE - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de sécurité sociale de l’UE (SSN) ou ID équivalent - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro d’identification fiscale de l’UE - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Restreindre l’accès au contenu pour utilisateurs externe  <br/>  Informer les utilisateurs à l’aide de courriers électroniques et de conseils de stratégie  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer des rapports d’incident à l’administrateur  <br/> |
   
## <a name="germany-financial-data"></a>Données financières en Allemagne

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour l’Allemagne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de carte de débit de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour l’Allemagne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de carte de débit de l’UE - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="germany-personally-identifiable-information-pii-data"></a>Germany Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour l’Allemagne : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire allemand - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de passeport allemand - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour l’Allemagne : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de permis de conduire allemand - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de passeport allemand - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="israel-financial-data"></a>Données financières en Israël

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour Israël : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de compte bancaire d’Israël - Min count 1, Max count 9  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour Israël : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de compte bancaire d’Israël - Nombre min 10, Nombre maximal de 500  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="israel-personally-identifiable-information-pii-data"></a>Israel Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour Israël : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Israël National ID - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour Israël : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Israël National ID - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="israel-protection-of-privacy"></a>Israel Protection of Privacy

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Protection des données pour Israël : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Israël National ID - Min count 1, Max count 9  <br/>  Numéro de compte bancaire d’Israël - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Protection des données pour Israël : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Israël National ID - Min count 10, Max count 500  <br/>  Numéro de compte bancaire d’Israël - Nombre min 10, Nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="japan-financial-data"></a>Données financières au Japon

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour le Japon : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de compte bancaire au Japon - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour le Japon : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de compte bancaire au Japon - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="japan-personally-identifiable-information-pii-data"></a>Japan Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour le Japon : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro d’inscription des résidents du Japon - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Japon (SIN) - Nombre min 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour le Japon : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro d’inscription des résidents du Japon - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Japon (SIN) - Nombre min. 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="japan-protection-of-personal-information"></a>Japan Protection of Personal Information

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi PPI pour le Japon : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro d’inscription des résidents du Japon - Nombre minimal 1, nombre maximal 9  <br/>  Numéro d’assurance sociale du Japon (SIN) - Nombre min 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi PPI pour le Japon : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro d’inscription des résidents du Japon - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro d’assurance sociale du Japon (SIN) - Nombre min. 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="pci-data-security-standard-pci-dss"></a>PCI Data Security Standard (PCI DSS)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Norme PCI DSS : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Norme PCI DSS : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="saudi-arabia---anti-cyber-crime-law"></a>Saudi Arabia - Anti-Cyber Crime Law

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|ACC pour l’Arabie Saoudite : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire international (IBAN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|ACC pour l’Arabie Saoudite : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de compte bancaire international (IBAN) - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="saudi-arabia-financial-data"></a>Données financières en Arabie Saoudite

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour l’Arabie Saoudite : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire international (IBAN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour l’Arabie Saoudite : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de compte bancaire international (IBAN) - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="saudi-arabia-personally-identifiable-information-pii-data"></a>Saudi Arabia Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour l’Arabie Saoudite : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Saudi Arabia National ID - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour l’Arabie Saoudite : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Saudi Arabia National ID - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="uk-access-to-medical-reports-act"></a>U.K. Access to Medical Reports Act

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi AMRA pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Nombre national Service de contrôle d'intégrité - Nombre minimal 1, nombre maximal 9  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi AMRA pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Nombre national Service de contrôle d'intégrité - Nombre minimal 10, nombre maximal de 500  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="uk-data-protection-act"></a>U.K. Data Protection Act

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|DPA pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal 1, nombre maximal 9  <br/>  États-Unis / Royaume-Uni Numéro de passeport - Nombre minimal 1, nombre maximal 9  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|DPA pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal de 10, nombre maximal de 500  <br/>  États-Unis / Royaume-Uni Numéro de passeport - Nombre minimal de 10, nombre maximal de 500  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="uk-financial-data"></a>Données financières R.U.

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de carte de débit de l’UE - Nombre minimal 1, nombre maximal 9  <br/>  Code SWIFT -Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de carte de débit de l’UE - Nombre minimal de 10, nombre maximal de 500  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="uk-personal-information-online-code-of-practice-piocp"></a>U.K. Personal Information Online Code of Practice (PIOCP)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PIOCP pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal 1, nombre maximal 9  <br/>  ROYAUME-UNI. Nombre national Service de contrôle d'intégrité - Nombre minimal 1, nombre maximal 9  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PIOCP pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal de 10, nombre maximal de 500  <br/>  ROYAUME-UNI. Nombre national Service de contrôle d'intégrité - Nombre minimal 10, nombre maximal de 500  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="uk-personally-identifiable-information-pii-data"></a>U.K. Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal 1, nombre maximal 9  <br/>  États-Unis / Royaume-Uni Numéro de passeport - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  ROYAUME-UNI. Numéro d’assurance nationale (NINO) - Nombre minimal de 10, nombre maximal de 500  <br/>  États-Unis / Royaume-Uni Numéro de passeport - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="uk-privacy-and-electronic-communications-regulations"></a>U.K. Privacy and Electronic Communications Regulations

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PECR pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Code SWIFT - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PECR pour le Royaume-Uni : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Code SWIFT - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-federal-trade-commission-ftc-consumer-rules"></a>U.S. Federal Trade Commission (FTC) Consumer Rules

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Règles de protection des consommateurs du FTC pour les États-Unis : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire des États-Unis - Nombre minimal 1, nombre maximal 9  <br/>  Nombre de routage ABA - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Règles de protection des consommateurs du FTC pour les États-Unis : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire américain - Nombre minimal 10, nombre maximal de 500  <br/>  Nombre de routage ABA - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-financial-data"></a>Données financières US

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Données financières pour les États-Unis : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire des États-Unis - Nombre minimal 1, nombre maximal 9  <br/>  Nombre de routage ABA - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Données financières pour les États-Unis : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire américain - Nombre minimal 10, nombre maximal de 500  <br/>  Nombre de routage ABA - Nombre minimal 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-gramm-leach-bliley-act-glba"></a>U.S. Gramm-Leach-Bliley Act (GLBA)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi GLBA américaine : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire des États-Unis - Nombre minimal 1, nombre maximal 9  <br/>  U.S. Individual Taxpayer Identification Number (ITIN) - Min count 1, Max count 9  <br/>  U.S. Social Security Number (SSN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi GLBA américaine : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire américain - Nombre minimal 10, nombre maximal de 500  <br/>  U.S. Individual Taxpayer Identification Number (ITIN) - Min count 10, Max count 500  <br/>  U.S. Social Security Number (SSN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-health-insurance-act-hipaa"></a>U.S. Health Insurance Act (HIPAA)

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Le contenu correspond à l’HIPAA des États-Unis  <br/> | Contient l’une des informations sensibles suivantes :  <br/>  U.S. Social Security Number (SSN) - Min count 1, Max count any  <br/>  Drug Enforcement Agency (DEA) Number - Min count 1, Max count any  <br/> **AND** <br/>  Le contenu contient l’un des termes suivants :  <br/>  Classification internationale des maladies (ICD-9-CM) - Nombre minimal 1, nombre maximal  <br/>  Classification internationale des maladies (ICD-10-CM) - Nombre minimal 1, nombre maximal  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
   
## <a name="us-patriot-act"></a>U.S. Patriot Act

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Loi USA Patriot Act américaine : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire des États-Unis - Nombre minimal 1, nombre maximal 9  <br/>  U.S. Individual Taxpayer Identification Number (ITIN) - Min count 1, Max count 9  <br/>  U.S. Social Security Number (SSN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Loi USA Patriot Act américaine : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire américain - Nombre minimal 10, nombre maximal de 500  <br/>  U.S. Individual Taxpayer Identification Number (ITIN) - Min count 10, Max count 500  <br/>  U.S. Social Security Number (SSN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-personally-identifiable-information-pii-data"></a>U.S. Personally Identifiable Information (PII) Data

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|PII pour les États-Unis : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  U.S. Individual Taxpayer Identification Number (ITIN) - Min count 1, Max count 9  <br/>  U.S. Social Security Number (SSN) - Min count 1, Max count 9  <br/>  États-Unis / Royaume-Uni Numéro de passeport - Nombre minimal 1, nombre maximal 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|PII pour les États-Unis : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  U.S. Individual Taxpayer Identification Number (ITIN) - Min count 10, Max count 500  <br/>  U.S. Social Security Number (SSN) - Min count 10, Max count 500  <br/>  États-Unis / Royaume-Uni Numéro de passeport - Nombre minimal de 10, nombre maximal de 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-state-breach-notification-laws"></a>U.S. State Breach Notification Laws

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Lois américaines sur les violations de la sécurité : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de compte bancaire des États-Unis - Nombre minimal 1, nombre maximal 9  <br/>  Numéro de permis de conduire américain - Nombre minimal 1, nombre maximal 9  <br/>  U.S. Social Security Number (SSN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Lois américaines sur les violations de la sécurité : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  Numéro de carte de crédit - Nombre minimal de 10, nombre maximal de 500  <br/>  Numéro de compte bancaire américain - Nombre minimal 10, nombre maximal de 500  <br/>  Numéro de permis de conduire des États-Unis - Nombre minimal 10, nombre maximal de 500  <br/>  U.S. Social Security Number (SSN) - Min count 10, Max count 500 <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   
## <a name="us-state-social-security-number-confidentiality-laws"></a>U.S. State Social Security Number Confidentiality Laws

|**Nom de la règle**|**Conditions  <br/> (y compris les types d’informations sensibles)**|**Actions**|
|:-----|:-----|:-----|
|Lois SSN américaines : analyser le contenu partagé hors de l’organisation - faible nombre  <br/> | Le contenu contient des informations sensibles :  <br/>  U.S. Social Security Number (SSN) - Min count 1, Max count 9  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> |Envoyer une notification  <br/> |
|Lois SSN américaines : analyser le contenu partagé hors de l’organisation - nombre élevé  <br/> | Le contenu contient des informations sensibles :  <br/>  U.S. Social Security Number (SSN) - Min count 10, Max count 500  <br/>  Le contenu est partagé avec :  <br/>  Des personnes extérieures à mon organisation  <br/> | Bloquer l’accès au contenu  <br/>  Envoyer une notification  <br/>  Autoriser le remplacement  <br/>  Exiger une justification professionnelle  <br/>  Envoyer un rapport d’incident  <br/> |
   

