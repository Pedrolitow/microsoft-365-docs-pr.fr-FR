---
title: Référence des conseils de stratégie de prévention contre la perte de données
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: reference
ms.service: O365-seccomp
ms.localizationpriority: medium
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
recommendations: false
description: Découvrez comment ajouter un conseil de stratégie à une stratégie de protection contre la perte de données (DLP) pour informer un utilisateur qu’il travaille avec du contenu en conflit avec une stratégie DLP.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 04743bdabba4089a7cfdbb46fbb25d427927f6c0
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66638342"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Référence des conseils de stratégie de prévention contre la perte de données

Les conseils de stratégie DLP dans Outlook Web Access sont pris en charge pour toutes les conditions, exceptions et actions applicables à la charge de travail Exchange dans une stratégie DLP, à l’exception des suivantes :

**Conditions:**

- Le destinataire est membre de
- L’en-tête contient des mots ou des expressions
- L’en-tête correspond aux modèles
- Le type de message est
- Le jeu de caractères de contenu contient des mots
- L’expéditeur a remplacé l’info-bulle de stratégie
- La taille du message est égale ou supérieure à
- L’attribut AD de l’expéditeur contient des mots ou des expressions
- L’attribut AD de l’expéditeur correspond aux modèles
- Plages d’adresses IP de l’expéditeur
- L’attribut AD du destinataire contient des mots ou des expressions
- L’attribut AD du destinataire correspond aux modèles
- Le nom du document contient des mots ou des expressions
- Le nom du document correspond aux modèles
- Le contenu du document contient des mots ou des expressions
- Le contenu du document correspond aux modèles

**Actions:**

- Transférer le message pour approbation au responsable de l’expéditeur
- Transférer le message pour approbation à des approbateurs spécifiques
- Rediriger le message vers des utilisateurs spécifiques
- Ajouter des destinataires à la zone À
- Ajouter des destinataires à la zone Cc
- Ajouter des destinataires à la zone Cci
- Ajouter le gestionnaire de l’expéditeur en tant que destinataire
- Ajouter une clause d’exclusion de responsabilité HTML
- Ajouter l’objet de l’e-mail
- Supprimer le chiffrement des messages O365 et la protection des droits

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 et versions ultérieures prend en charge l’affichage de conseils de stratégie pour certaines conditions et exceptions uniquement

Actuellement, Outlook 2013 et versions ultérieures prennent en charge l’affichage de conseils de stratégie pour les stratégies qui ne contiennent aucune condition ou exception en dehors des conditions mentionnées ci-dessous et des exceptions correspondantes :

- Contenu contenu (fonctionne uniquement pour les types d’informations sensibles. Les étiquettes de confidentialité ne sont pas prises en charge)
- Le contenu est partagé

Notez que toutes les conditions fonctionnent pour les e-mails créés dans l’application cliente Outlook, où elles correspondent au contenu et appliquent des actions de protection sur le contenu. Toutefois, l’affichage des conseils de stratégie aux utilisateurs n’est pas pris en charge pour les conditions utilisées en dehors de celles mentionnées ci-dessus.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Prise en charge d’Outlook 2013 et versions ultérieures et des applications Office sur Le Bureau montrant des conseils de stratégie pour certains types d’informations sensibles uniquement

La liste des types d’informations sensibles qui seront détectés pour l’affichage des conseils de stratégie DLP dans Outlook sur Le Bureau (2013 et versions ultérieures) et les applications Office (Word, Excel, PowerPoint) sur Desktop sont les suivantes :

- Numéro de routage ABA
- Numéro d’identité nationale (DNI) pour l’Argentine
- Numéro de compte bancaire Australie
- Numéro de dossier médical Australie
- Numéro de passeport Australie
- Numéro de dossier fiscal Australie
- Clé d’authentification Azure DocumentDB  
- Chaîne de connexion de base de données Azure IAAS et chaîne de connexion Azure SQL  
- Chaîne de connexion Azure IoT  
- Mot de passe du paramètre De publication Azure  
- Chaîne de connexion du cache Redis Azure  
- Azure SAS  
- chaîne de connexion Azure Service Bus  
- Clé de compte de stockage Azure  
- Clé de compte de stockage Azure (générique)  
- Numéro national belge
- Numéro CPF Brésil
- Numéro d’entité juridique (CNPJ) Brésil
- 	Brazil National ID Card (RG)
- Numéro de compte bancaire Canada
- Numéro de permis de conduire Canada
- Numéro de service de santé Canada
- Numéro de passeport Canada
- NIMP (numéro d’identification médicale personnel) Canada
- Numéro d'assurance sociale Canada
- 	Numéro de carte d’identité Chili
- 	Numéro de carte d’identité de résident Chine (RPC)
- Numéro de carte de crédit
- Numéro de carte d’identité croate  
- Numéro d’identification personnelle croate (OIB)  
- Numéro d’identité personnelle tchèque  
- Numéro d’identification personnelle danois
- Numéro de la Drug Enforcement Agency (DEA)
- Numéro de carte de crédit de l'U.E.
- Numéro de permis de conduire de l’UE  
- Numéro d’identification nationale de l’UE  
- Numéro de passeport de l’UE  
- Numéro de sécurité sociale de l’UE (SSN) ou ID équivalent  
- Numéro d’identification fiscale de l’UE (TIN)  
- Numéro d'identification national finlandais
- Numéro de passeport finlandais
- Numéro de permis de conduire français
- Carte nationale d'identité (CNI) française
- Numéro de passeport français
- Numéro de sécurité sociale (INSEE) français
- Numéro de permis de conduire allemand
- Numéro de passeport allemand
- Numéro de carte d’identité allemand
- Carte d’identité nationale grecque  
- Numéro de carte d’identité (HKID) Hong Kong
- Numéro de compte permanent Inde
- Numéro d’identification unique (Aadhaar) Inde
- Numéro de carte d’identité (KTP) Indonésie
- Numéro de compte international (IBAN)
- Classification internationale des maladies (ICD-10-CM)  
- Classification internationale des maladies (ICD-9-CM)  
- Adresse IP
- Numéro personnel pour le service public irlandais (PPS) 
- Numéro de compte bancaire Israël
- Carte nationale d’identité Israël
- Numéro de permis de conduire Italie
- Numéro de compte bancaire Japon
- Numéro de permis de conduire Japon
- Numéro de passeport Japon
- Matricule de résident Japon
- Numéro d’assurance sociale Japon
- Numéro de carte de résidence japonaise
- Numéro de carte d’identité malaisienne
- Numéro de service du citoyen (BSN) néerlandais  
- Numéro du Ministère de la santé Nouvelle-Zélande
- Numéro d’identité norvégien  
- Numéro d’identification multifonction unifié Philippines
- Carte d'identité polonaise
- Numéro d'identification national polonais (PESEL)
- Numéro de passeport polonais
- Numéro de carte de citoyen portugais
- ID national Arabie saoudite
- Numéro de carte d’identité d’enregistrement national (NRIC) Singapour
- Numéro d’identification Afrique du Sud  
- Matricule de résident Corée du Sud
- Numéro de sécurité sociale (N° S.S.) espagnol
- chaîne de connexion SQL Server  
- ID national suédois
- Numéro de passeport suédois
- Code SWIFT
- ID national à Taïwan
- 	Numéro de passeport Taïwan
- Certificat de résident taïwanais (ARC/TARC)
- Code d’identification de la population thaïlandaise
- Numéro d’identification nationale turque
- Numéro de permis de conduire du Royaume-Uni
- Numéro de liste électorale du Royaume-Uni
- Numéro du service de santé national (NHS) du Royaume-Uni
- Numéro d'assurance national (NINO) du Royaume-Uni
- États-Unis / Royaume-Uni Numéro de passeport
- Numéro de compte bancaire États-Unis
- Numéro de permis de conduire États-Unis
- Numéro d’identification fiscale individuel (ITIN) États-Unis
- Numéro de sécurité sociale (SSN) États-Unis

Notez que les types d’informations sensibles personnalisés sont également pris en charge pour les conseils de stratégie DLP en plus des types d’informations sensibles out-of-the-box ci-dessus.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>La protection contre la perte de données sur les appareils de point de terminaison prend en charge les conseils de stratégie pour certains types d’informations sensibles uniquement

La liste des types d’informations sensibles qui seront détectés dans les documents résidant sur des appareils de point de terminaison est la suivante :

- Numéro de routage ABA 
- Numéro d’identité nationale (DNI) pour l’Argentine 
- Numéro de compte bancaire Australie 
- Numéro de dossier médical Australie 
- Numéro de passeport Australie 
- Numéro de dossier fiscal Australie 
- Numéro d’entreprise australien 
- Numéro de la société australienne 
- Numéro de permis de conduire en Autriche 
- Carte d’identité d’Autriche 
- Numéro de passeport en Autriche 
- Numéro de sécurité sociale en Autriche 
- Numéro d’identification fiscale en Autriche 
- Numéro de taxe sur la valeur ajoutée (TVA) en Autriche 
- Clé d’authentification Azure DocumentDB 
- Chaîne de connexion de base de données Azure IAAS et chaîne de connexion Azure SQL 
- Chaîne de connexion Azure IoT 
- Mot de passe du paramètre De publication Azure 
- Chaîne de connexion du cache Redis Azure 
- Azure SAS 
- chaîne de connexion Azure Service Bus 
- Clé de compte de stockage Azure 
- Clé de compte de stockage Azure (générique) 
- Numéro de permis de conduire en Belgique 
- Numéro national belge 
- Numéro de passeport en Belgique 
- Numéro de taxe sur la valeur ajoutée en Belgique 
- Numéro CPF Brésil 
- Numéro d’entité juridique (CNPJ) Brésil 
- 	Brazil National ID Card (RG) 
- Numéro de permis de conduire en Bulgarie 
- Numéro de passeport en Bulgarie 
- Numéro civil uniforme en Bulgarie 
- Numéro de compte bancaire Canada 
- Numéro de permis de conduire Canada 
- Numéro de service de santé Canada 
- Numéro de passeport Canada 
- NIMP (numéro d’identification médicale personnel) Canada 
- Numéro d'assurance sociale Canada 
- 	Numéro de carte d’identité Chili 
- 	Numéro de carte d’identité de résident Chine (RPC) 
- Numéro de carte de crédit 
- Numéro de permis de conduire en Croatie 
- Numéro de carte d’identité croate 
- Numéro de carte d’identité nationale croate 
- Numéro de passeport en Croatie 
- Numéro d’identification personnelle croate (OIB) 
- Signature d’accès partagé du compte de stockage Azure CSCAN-AZURE0060 
- Clé symétrique générale CSCAN-GENERAL0140 
- Numéro de permis de conduire de Chypre 
- Carte d’identité de Chypre 
- Numéro de passeport de Chypre 
- Numéro d’identification fiscale de Chypre 
- Numéro de permis de conduire tchèque 
- Numéro d’identité personnelle tchèque 
- Numéro de passeport de la République tchèque 
- Numéro de permis de conduire au Danemark 
- Numéro de passeport du Danemark 
- Numéro d’identification personnelle danois 
- Numéro de la Drug Enforcement Agency (DEA) 
- Numéro de permis de conduire estonien 
- Numéro de passeport estonien 
- Code d’identification personnelle de l’Estonie 
- Numéro de carte de crédit de l'U.E. 
- Numéro de permis de conduire de l’UE 
- Numéro d’identification nationale de l’UE 
- Numéro de passeport de l’UE 
- Numéro de sécurité sociale de l’UE (SSN) ou ID équivalent 
- Numéro d’identification fiscale de l’UE (TIN) 
- Numéro de permis de conduire en Finlande 
- Numéro d’assurance maladie européen en Finlande 
- Numéro d'identification national finlandais 
- Numéro de passeport finlandais 
- Numéro de permis de conduire français 
- Numéro d’assurance maladie en France 
- Carte nationale d'identité (CNI) française 
- Numéro de passeport français 
- Numéro de sécurité sociale (INSEE) français 
- Numéro d’identification fiscale en France (numéro SPI.) 
- Numéro de taxe sur la valeur ajoutée en France 
- Numéro de permis de conduire allemand 
- Numéro de passeport allemand 
- Numéro de carte d’identité allemand 
- Numéro d’identification fiscale en Allemagne 
- Numéro de taxe sur la valeur ajoutée en Allemagne 
- Numéro de permis de conduire en Grèce 
- Carte d’identité nationale grecque 
- Numéro de passeport en Grèce 
- Numéro de sécurité sociale en Grèce (AMKA) 
- Numéro d’identification fiscale grecque 
- Numéro de carte d’identité (HKID) Hong Kong 
- Numéro de sécurité sociale hongrois (TAJ) 
- Numéro d’impôt hongrois sur la valeur ajoutée 
- Numéro de permis de conduire en Hongrie 
- Numéro de passeport en Hongrie 
- Numéro d’identification personnelle en Hongrie 
- Numéro d’identification fiscale en Hongrie 
- Numéro de compte permanent Inde 
- Numéro d’identification unique (Aadhaar) Inde 
- Numéro de carte d’identité (KTP) Indonésie 
- Numéro de compte international (IBAN) 
- Classification internationale des maladies (ICD-10-CM) 
- Classification internationale des maladies (ICD-9-CM) 
- Adresse IP 
- Numéro de permis de conduire en Irlande 
- Numéro de passeport en Irlande 
- Numéro personnel pour le service public irlandais (PPS) 
- Numéro de compte bancaire Israël 
- Carte nationale d’identité Israël 
- Numéro de permis de conduire Italie 
- Code fiscal de l’Italie 
- Numéro de passeport en Italie 
- Numéro de taxe sur la valeur ajoutée en Italie 
- Numéro de compte bancaire Japon 
- Numéro de permis de conduire Japon 
- Numéro de passeport Japon 
- Matricule de résident Japon 
- Numéro d’assurance sociale Japon 
- Japonais Mon numéro d’entreprise 
- Japonais Mon numéro personnel 
- Numéro de carte de résidence japonaise 
- Numéro de permis de conduire letton 
- Numéro de passeport letton 
- Code personnel letton 
- Numéro de permis de conduire en Lituanie 
- Numéro de passeport en Lituanie 
- Code personnel lituanien 
- Numéro de permis de conduire du Luxemburg 
- Numéro d’identification national du Luxembourg (personnes physiques) 
- Numéro d’identification national du Luxembourg (personnes non naturelles) 
- Numéro de passeport de Luxemburg 
- Numéro de carte d’identité malaisienne 
- Numéro de permis de conduire de Malte 
- Numéro de carte d’identité de Malte 
- Numéro de passeport maltais 
- Numéro d’ID fiscal de Malte 
- Numéro de service du citoyen (BSN) néerlandais 
- Numéro de permis de conduire aux Pays-Bas 
- Numéro de passeport des Pays-Bas 
- Numéro d’identification fiscale aux Pays-Bas 
- Numéro de taxe sur la valeur ajoutée aux Pays-Bas 
- Numéro de compte bancaire en Nouvelle-Zélande 
- Numéro de permis de conduire en Nouvelle-Zélande 
- Chiffre d’affaires intérieur de la Nouvelle-Zélande 
- Numéro du Ministère de la santé Nouvelle-Zélande 
- Numéro de l’aide sociale néo-zélandaise 
- Numéro d’identité norvégien 
- Numéro d’identification multifonction unifié Philippines 
- Numéro de permis de conduire en Pologne 
- Carte d'identité polonaise 
- Numéro d'identification national polonais (PESEL) 
- Numéro de passeport polonais 
- Numéro d’identification fiscale en Pologne 
- Numéro REGON polonais 
- Numéro de carte de citoyen portugais 
- Numéro de permis de conduire au Portugal 
- Numéro de passeport du Portugal 
- Numéro d’identification fiscale du Portugal 
- Numéro de permis de conduire en Roumanie 
- Numéro de passeport en Roumanie 
- Code numérique personnel roumain (CNP) 
- Numéro de passeport russe (intérieur) 
- Numéro de passeport russe (international) 
- ID national Arabie saoudite 
- Numéro de carte d’identité d’enregistrement national (NRIC) Singapour 
- Numéro de permis de conduire en Slovaquie 
- Numéro de passeport en Slovaquie 
- Numéro personnel en Slovaquie 
- Numéro de permis de conduire en Slovénie 
- Numéro de passeport en Slovénie 
- Numéro d’identification fiscale en Slovénie 
- Slovénie Unique Master Citizen Number 
- Numéro d’identification Afrique du Sud 
- Matricule de résident Corée du Sud 
- Espagne DNI 
- Numéro de permis de conduire en Espagne 
- Numéro de passeport en Espagne 
- Numéro de sécurité sociale (N° S.S.) espagnol 
- Numéro d’identification fiscale en Espagne 
- chaîne de connexion SQL Server 
- Numéro de permis de conduire en Suède 
- ID national suédois 
- Numéro de passeport suédois 
- Numéro d’identification fiscale en Suède 
- Code SWIFT 
- Numéro de sécurité sociale suisse AHV 
- ID national à Taïwan 
- 	Numéro de passeport Taïwan 
- Certificat de résident taïwanais (ARC/TARC) 
- Code d’identification de la population thaïlandaise 
- Numéro d’identification nationale turque 
- Numéro de permis de conduire du Royaume-Uni 
- Numéro de liste électorale du Royaume-Uni 
- Numéro du service de santé national (NHS) du Royaume-Uni 
- Numéro d'assurance national (NINO) du Royaume-Uni 
- ROYAUME-UNI. Numéro de référence unique du contribuable 
- États-Unis / Royaume-Uni Numéro de passeport 
- Numéro de compte bancaire États-Unis 
- Numéro de permis de conduire États-Unis 
- Numéro d’identification fiscale individuel (ITIN) États-Unis 
- Numéro de sécurité sociale (SSN) États-Unis 
- Numéro de passeport de l’Ukraine (intérieur) 
- Numéro de passeport de l’Ukraine (international) 
 
Notez que les types d’informations sensibles personnalisés seront également détectés en plus des types d’informations sensibles out-of-the-box ci-dessus.

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Tableau de prise en charge pour les conseils de stratégie DLP dans les applications Microsoft

|**Application et plateforme**|**Prise en charge des conseils de stratégie DLP**|**Types d’informations sensibles pris en charge**|**Prédicats et actions pris en charge**|**Commentaires**|
|:--|:--|:--|:--|:--|
|**Outlook sur le web**|:::image type="icon" source="../media/rightmrk.png" border="false":::|tout|Sous-ensemble||
|**Outlook Win32 (version 2105 14026.20000 et canal semi-annuel ver. 2102 build 13801.20862)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Sous-ensemble|Sous-ensemble|Consultez [Outlook 2013 et versions ultérieures pour afficher des conseils de stratégie uniquement pour certaines conditions et exceptions](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) et [Outlook 2013 et versions ultérieures, et les applications Office sur le Bureau qui affichent des conseils de stratégie pour certains types d’informations sensibles uniquement](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) pour plus d’informations sur la prise en charge des types d’informations sensibles et les conditions DLP et les actions prises en charge pour afficher des conseils de stratégie DLP sur Outlook Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|none|none|Les conseils de stratégie DLP ne sont pas pris en charge sur Outlook Mobile|
|**Client Web SharePoint Online/OneDrive Entreprise**|:::image type="icon" source="../media/rightmrk.png" border="false":::|tout|tous les prédicats et actions SPO/ODB dans DLP||
|**Client SharePoint Win32/ OneDrive Entreprise Win32**|:::image type="icon" source="../media/crsmrk.png" border="false":::|none|none|Les conseils de stratégie DLP ne sont pas pris en charge sur les applications clientes de bureau SharePoint ou OneDrive|
|**Word, Excel, PowerPoint Web Client**|:::image type="icon" source="../media/rightmrk.png" border="false":::|tout|tous les prédicats et actions SPO/ODB dans DLP|L’info-bulle de stratégie DLP est prise en charge si le document est hébergé sur l’application web SPO ou ODB et que la stratégie DLP est déjà marquée.|
|**Word, Excel, PowerPoint Mobile Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|none|none|Les conseils de stratégie DLP ne sont pas pris en charge dans les applications mobiles pour Office.|
|**Teams Web/ Teams Desktop/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|tout|tous les prédicats Teams dans la stratégie DLP|Les conseils de stratégie s’affichent lorsqu’un message est marqué comme « Ce message a été marqué. Que puis-je faire ? Lorsque vous cliquez sur le lien, l’utilisateur peut passer en revue les types d’informations sensibles détectés et remplacer ou signaler un problème si autorisé par l’administrateur. Notez qu’aucun conseil de stratégie n’est affiché pour les fichiers. Lorsque le destinataire tente d’accéder au document, il peut être refusé s’il n’est pas autorisé.|
|**Appareils de point de terminaison Win32**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Sous-ensemble|tous les prédicats et actions DLP de point de terminaison dans la stratégie DLP|Consultez [La protection contre la perte de données sur le point de terminaison prend en charge les conseils de stratégie pour certains types d’informations sensibles uniquement](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**appareils macOS**|conseils par défaut uniquement|tout|Sous-ensemble|Les stratégies de protection contre la perte de données sont applicables sur les appareils macOS. Les conseils de stratégie personnalisés ne sont pas pris en charge.|
|**Applications cloud tierces**|:::image type="icon" source="../media/crsmrk.png" border="false":::|none|none|Les conseils de stratégie de protection contre la perte de données ne sont pas pris en charge sur les applications cloud tierces|
|**Local**|:::image type="icon" source="../media/crsmrk.png" border="false":::|none|none||
|**Word, Excel, PowerPoint Win32 Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Sous-ensemble|Sous-ensemble|Consultez [Outlook 2013 et versions ultérieures, ainsi que la prise en charge des applications Office sur le Bureau qui affichent des conseils de stratégie pour certains types d’informations sensibles uniquement](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) pour la liste des types d’informations sensibles pris en charge</br></br>Les conseils de stratégie pour les applications clientes WXP fonctionnent pour les documents stockés sur SharePoint Online ou les sites OneDrive Entreprise pour toutes les stratégies DLP qui ont exactement les conditions ou actions ci-dessous ou un sous-ensemble dans la stratégie DLP :</br> <ul><li>Le contenu contient des types d’informations sensibles</li><li>Étendue d’accès (le contenu est partagé en interne/externe)</li><li>Notifier l’utilisateur (conseils de stratégie/notifications utilisateur)</li><li>Bloquer tout le monde</li><li>Rapports d’incident</li></ul></br> Si une autre condition ou action est présente, le conseil de stratégie DLP pour cette stratégie n’apparaît pas dans les applications de bureau de Word, Excel ou PowerPoint.</br>Pour plus d’informations[, consultez les conseils de stratégie dans Excel, PowerPoint et Word](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word)|
||||||
