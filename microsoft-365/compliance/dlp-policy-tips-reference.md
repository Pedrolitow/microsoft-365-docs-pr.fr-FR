---
title: Référence des conseils de stratégie de prévention contre la perte de données
f1.keywords: CSH
ms.author: chrfox
author: chrfox
manager: laurawi
ms.date: ''
audience: Admin
ms.topic: article
ms.service: O365-seccomp
localization_priority: Normal
search.appverid:
- SPO160
- MET150
ms.assetid: 6501b5ef-6bf7-43df-b60d-f65781847d6c
ms.collection:
- M365-security-compliance
- SPO_Content
description: Découvrez comment ajouter un conseil de stratégie à une stratégie de protection contre la perte de données (DLP) pour informer un utilisateur qu'il travaille avec du contenu en conflit avec une stratégie DLP.
ms.custom: seo-marvel-apr2021
ms.openlocfilehash: 36e4d4f96146b51e0b31731c9e93222eed767045
ms.sourcegitcommit: 13ce4b31303a1a21ca53700a54bcf8d91ad2f8c1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/20/2021
ms.locfileid: "51903801"
---
# <a name="data-loss-prevention-policy-tips-reference"></a>Référence des conseils de stratégie de prévention contre la perte de données

Les conseils de stratégie DLP dans Outlook Web Access sont pris en charge pour toutes les conditions, exceptions et actions applicables sur la charge de travail Exchange dans une stratégie DLP, sauf les suivantes :

**Conditions :**

- L'expéditeur est
- Le domaine de l'expéditeur est
- Le destinataire est membre de
- L'en-tête contient des mots ou des expressions
- L'en-tête correspond aux modèles
- La taille du document est égale ou supérieure à
- Le type de message est
- L'importance du message est
- Le jeu de caractères de contenu contient des mots
- L'objet ou le corps contient des mots ou des expressions
- L'objet ou le corps correspond aux modèles
- Le jeu de caractères de contenu contient des mots
- Le contenu est reçu de
- L'expéditeur a-t-il surchargé le conseil de stratégie
- La taille du message est égale ou supérieure à
- L'attribut AD de l'expéditeur contient des mots ou des expressions
- L'attribut AD de l'expéditeur correspond aux modèles
- Le contenu du document contient des mots ou des expressions
- Le contenu du document correspond aux modèles

**Actions :**

- Transmettre le message pour approbation au responsable de l'expéditeur
- Transmettre le message pour approbation à des approuveurs spécifiques
- Rediriger le message vers des utilisateurs spécifiques
- Ajouter des destinataires à la zone À
- Ajouter des destinataires à la zone Cc
- Ajouter des destinataires à la zone Bcc
- Ajouter le responsable de l'expéditeur en tant que destinataire
- Ajouter une clause d'exclusion de responsabilité HTML
- Prédépender l'objet de l'e-mail
- Supprimer le chiffrement de messages O365 et la protection des droits

## <a name="outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions"></a>Outlook 2013 et les ultérieures prend en charge l'affichage de conseils de stratégie uniquement pour certaines conditions et exceptions

Actuellement, Outlook 2013 et les ultérieures prend en charge l'affichage de conseils de stratégie pour les stratégies qui ne contiennent aucune condition ou exception à part les conditions mentionnées ci-dessous et les exceptions correspondantes :

- Le contenu contient (fonctionne uniquement pour les types d'informations sensibles. Les étiquettes de niveau de sensibilité ne sont pas pris en charge)
- Le contenu est partagé

Notez que toutes les conditions fonctionnent pour les e-mails rédigés dans l'application cliente Outlook, où ils correspondent au contenu et appliquent des actions de protection sur le contenu. Toutefois, l'affichage de conseils de stratégie aux utilisateurs n'est pas pris en charge pour toutes les conditions qui sont utilisées en dehors de celle mentionnée ci-dessus.

## <a name="outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types"></a>Prise en charge d’Outlook 2013 et version ultérieure et des applications Office sur bureau affichant des conseils de stratégie pour certains types d’informations sensibles uniquement

La liste des types d’informations sensibles pré-détectés pour l’affichage des conseils de stratégie DLP dans Outlook sur bureau (2013 et version ultérieure) et les applications Office (Word, Excel, PowerPoint) sur ordinateur de bureau sont les suivantes :

- Numéro de routage ABA
- Numéro d’identité nationale (DNI) pour l’Argentine
- Numéro de compte bancaire Australie
- Numéro de dossier médical Australie
- Numéro de passeport Australie
- Numéro de dossier fiscal Australie
- Clé d’th Azure DocumentDB  
- Chaîne de connexion de base de données IAAS Azure et chaîne SQL connexion Azure  
- Chaîne de connexion Azure IoT  
- Mot de passe de paramètre de publication Azure  
- Chaîne de connexion du cache Azure Redis  
- Azure SAS  
- Chaîne de connexion Azure Service Bus  
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
- Numéro d’identité personnel tchèque  
- Numéro d’identification personnelle danois
- Numéro de la Drug Enforcement Agency (DEA)
- Numéro de carte de crédit de l'U.E.
- Numéro de permis de conduire de l’UE  
- Numéro d’identification national de l’UE  
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
- Classification internationale des maladie (ICD-10-CM)  
- Classification internationale des maladie (ICD-9-CM)  
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
- Numéro de carte de résidence (japonais)
- Numéro de carte d’identité Malaisie
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
- SQL Server Connection String  
- ID national suédois
- Numéro de passeport suédois
- Code SWIFT
- ID national à Taïwan
- 	Numéro de passeport Taïwan
- Certificat de résident Taïwan (ARC/TARC)
- Code d’identification de population thaï
- Numéro d’identification nationale turc
- Numéro de permis de conduire du Royaume-Uni
- Numéro de liste électorale du Royaume-Uni
- Numéro du service de santé national (NHS) du Royaume-Uni
- Numéro d'assurance national (NINO) du Royaume-Uni
- États-Unis/Royaume-Uni Numéro de passeport
- Numéro de compte bancaire États-Unis
- Numéro de permis de conduire États-Unis
- Numéro d’identification fiscale individuel (ITIN) États-Unis
- Numéro de sécurité sociale (SSN) États-Unis

Notez que les types d’informations sensibles personnalisés sont également pris en charge pour les conseils de stratégie DLP en plus des types d’informations sensibles pré-personnalisés ci-dessus.

## <a name="data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types"></a>La protection contre la perte de données sur les appareils de point de terminaison prend en charge les conseils de stratégie pour certains types d’informations sensibles uniquement

La liste des types d’informations sensibles pré-utilisés qui seront détectés dans les documents résidant sur des appareils de point de terminaison est la suivante :

- Numéro de routage ABA 
- Numéro d’identité nationale (DNI) pour l’Argentine 
- Numéro de compte bancaire Australie 
- Numéro de dossier médical Australie 
- Numéro de passeport Australie 
- Numéro de dossier fiscal Australie 
- Numéro d’entreprise australien 
- Numéro de société australien 
- Numéro de permis de conduire Autriche 
- Carte d’identité Autriche 
- Numéro de passeport Autriche 
- Numéro de sécurité sociale d’Autriche 
- Numéro d’identification fiscale autrichen 
- Numéro de TVA (Austria Value Added Tax) 
- Clé d’th Azure DocumentDB 
- Chaîne de connexion de base de données IAAS Azure et chaîne SQL connexion Azure 
- Chaîne de connexion Azure IoT 
- Mot de passe de paramètre de publication Azure 
- Chaîne de connexion du cache Azure Redis 
- Azure SAS 
- Chaîne de connexion Azure Service Bus 
- Clé de compte de stockage Azure 
- Clé de compte de stockage Azure (générique) 
- Numéro de permis de conduire belgique 
- Numéro national belge 
- Numéro de passeport belgique 
- Numéro de taxe sur la valeur ajoutée en Belgique 
- Numéro CPF Brésil 
- Numéro d’entité juridique (CNPJ) Brésil 
- 	Brazil National ID Card (RG) 
- Numéro de permis de conduire bulgare 
- Numéro de passeport bulgare 
- Numéro civile uniforme de Bulgarie 
- Numéro de compte bancaire Canada 
- Numéro de permis de conduire Canada 
- Numéro de service de santé Canada 
- Numéro de passeport Canada 
- NIMP (numéro d’identification médicale personnel) Canada 
- Numéro d'assurance sociale Canada 
- 	Numéro de carte d’identité Chili 
- 	Numéro de carte d’identité de résident Chine (RPC) 
- Numéro de carte de crédit 
- Numéro de permis de conduire Croate 
- Numéro de carte d’identité croate 
- Numéro de carte d’identité nationale croate 
- Numéro de passeport croate 
- Numéro d’identification personnelle croate (OIB) 
- CSCAN-AZURE0060 Azure Storage Account Shared Access Signature 
- Clé symétrique générale CSCAN-GENERAL0140 
- Numéro de permis de conduire de Chypre 
- Carte d’identité Chypre 
- Numéro de passeport de Chypre 
- Numéro d’identification fiscale à Chypre 
- Numéro de permis de conduire tchèque 
- Numéro d’identité personnel tchèque 
- Numéro de passeport de la République tchèque 
- Numéro de permis de conduire danemark 
- Numéro de passeport danemark 
- Numéro d’identification personnelle danois 
- Numéro de la Drug Enforcement Agency (DEA) 
- Numéro de permis de conduire Estonie 
- Numéro de passeport estonien 
- Code d’identification personnelle estonien 
- Numéro de carte de crédit de l'U.E. 
- Numéro de permis de conduire de l’UE 
- Numéro d’identification national de l’UE 
- Numéro de passeport de l’UE 
- Numéro de sécurité sociale de l’UE (SSN) ou ID équivalent 
- Numéro d’identification fiscale de l’UE (TIN) 
- Numéro de permis de conduire Finlande 
- Numéro d’assurance santé européen (Finlande) 
- Numéro d'identification national finlandais 
- Numéro de passeport finlandais 
- Numéro de permis de conduire français 
- Numéro d’assurance maladie Français 
- Carte nationale d'identité (CNI) française 
- Numéro de passeport français 
- Numéro de sécurité sociale (INSEE) français 
- Numéro d’identification fiscale français (numéro SPI.) 
- Numéro de taxe sur la valeur ajoutée en France 
- Numéro de permis de conduire allemand 
- Numéro de passeport allemand 
- Numéro de carte d’identité allemand 
- Numéro d’identification fiscale allemand 
- Numéro de taxe sur la valeur ajoutée en Allemagne 
- Numéro de permis de conduire Grec 
- Carte d’identité nationale grecque 
- Numéro de passeport Grec 
- Numéro de sécurité sociale grec (AMKA) 
- Numéro d’identification fiscale grec 
- Numéro de carte d’identité (HKID) Hong Kong 
- Numéro de sécurité sociale hongrois (TAJ) 
- Numéro de taxe sur la valeur ajoutée hongrois 
- Numéro de permis de conduire hongrie 
- Numéro de passeport hongrois 
- Numéro d’identification personnel en Hongrie 
- Numéro d’identification fiscale hongrie 
- Numéro de compte permanent Inde 
- Numéro d’identification unique (Aadhaar) Inde 
- Numéro de carte d’identité (KTP) Indonésie 
- Numéro de compte international (IBAN) 
- Classification internationale des maladie (ICD-10-CM) 
- Classification internationale des maladie (ICD-9-CM) 
- Adresse IP 
- Numéro de permis de conduire Irlande 
- Numéro de passeport irlande 
- Numéro personnel pour le service public irlandais (PPS) 
- Numéro de compte bancaire Israël 
- Carte nationale d’identité Israël 
- Numéro de permis de conduire Italie 
- Code fiscal italien 
- Numéro de passeport Italie 
- Numéro de taxe sur la valeur ajoutée italie 
- Numéro de compte bancaire Japon 
- Numéro de permis de conduire Japon 
- Numéro de passeport Japon 
- Matricule de résident Japon 
- Numéro d’assurance sociale Japon 
- Japonais Mon numéro d’entreprise 
- Japonais Mon numéro personnel 
- Numéro de carte de résidence (japonais) 
- Numéro de permis de conduire letton 
- Numéro de passeport letton 
- Code personnel letton 
- Numéro de permis de conduire lituanien 
- Numéro de passeport lituanien 
- Code personnel lituanien 
- Numéro de permis de conduire De Qu’est-ce que vous avez ? 
- Numéro d’identification national (personnes physiques) 
- Numéro d’identification national (personnes non physiques) 
- Numéro de passeport Dem passport 
- Numéro de carte d’identité Malaisie 
- Numéro de permis de conduire de Malte 
- Numéro de carte d’identité Malte 
- Numéro de passeport de Malte 
- Numéro d’ID fiscal de Malte 
- Numéro de service du citoyen (BSN) néerlandais 
- Numéro de permis de conduire néerlandais 
- Numéro de passeport néerlandais 
- Numéro d’identification fiscale pays-Bas 
- Numéro de taxe sur la valeur ajoutée des Pays-Bas 
- Numéro de compte bancaire nouvelle-Zélande 
- Numéro de permis de conduire nouvelle-Zélande 
- Numéro de revenu pour les Pays-Bas (Nouvelle-Zélande) 
- Numéro du Ministère de la santé Nouvelle-Zélande 
- Numéro de réseau social de La Nouvelle-Zélande 
- Numéro d’identité norvégien 
- Numéro d’identification multifonction unifié Philippines 
- Numéro de permis de conduire polonais 
- Carte d'identité polonaise 
- Numéro d'identification national polonais (PESEL) 
- Numéro de passeport polonais 
- Numéro d’identification fiscale polonais 
- Numéro POLONAIS REGON 
- Numéro de carte de citoyen portugais 
- Numéro de permis de conduire Portugal 
- Numéro de passeport portugais 
- Numéro d’identification fiscale portugais 
- Numéro de permis de conduire roumain 
- Numéro de passeport roumain 
- Code numérique personnel (CNP) roumain 
- Numéro de passeport russe (national) 
- Numéro de passeport russe (international) 
- ID national Arabie saoudite 
- Numéro de carte d’identité d’enregistrement national (NRIC) Singapour 
- Numéro de permis de conduire slovaque 
- Numéro de passeport slovaque 
- Numéro personnel slovaque 
- Numéro de permis de conduire slovène 
- Numéro de passeport slovène 
- Numéro d’identification fiscale slovénien 
- Numéro de citoyen maître unique de Slovénie 
- Numéro d’identification Afrique du Sud 
- Matricule de résident Corée du Sud 
- DNI (Espagne) 
- Numéro de permis de conduire Espagnol 
- Numéro de passeport Espagnol 
- Numéro de sécurité sociale (N° S.S.) espagnol 
- Numéro d’identification fiscale Espagnol 
- SQL Server Connection String 
- Numéro de permis de conduire suédois 
- ID national suédois 
- Numéro de passeport suédois 
- Numéro d’identification fiscale suédois 
- Code SWIFT 
- Numéro de sécurité sociale suisse AHV 
- ID national à Taïwan 
- 	Numéro de passeport Taïwan 
- Certificat de résident Taïwan (ARC/TARC) 
- Code d’identification de population thaï 
- Numéro d’identification nationale turc 
- Numéro de permis de conduire du Royaume-Uni 
- Numéro de liste électorale du Royaume-Uni 
- Numéro du service de santé national (NHS) du Royaume-Uni 
- Numéro d'assurance national (NINO) du Royaume-Uni 
- Royaume-Uni Numéro de référence du contribuable unique 
- États-Unis/Royaume-Uni Numéro de passeport 
- Numéro de compte bancaire États-Unis 
- Numéro de permis de conduire États-Unis 
- Numéro d’identification fiscale individuel (ITIN) États-Unis 
- Numéro de sécurité sociale (SSN) États-Unis 
- Numéro de passeport Ukrainien (national) 
- Numéro de passeport ukrainien (international) 
 
Notez que des types d’informations sensibles personnalisés seront également détectés en plus des types d’informations sensibles pré-personnalisés ci-dessus.

## <a name="support-matrix-for-dlp-policy-tips-across-microsoft-apps"></a>Matrice de prise en charge des conseils de stratégie DLP dans les applications Microsoft

|**Application et plateforme**|**Prise en charge des conseils de stratégie DLP**|**Types d'informations sensibles pris en charge**|**Prédicats et actions pris en charge**|**Commentaires**|
|:--|:--|:--|:--|:--|
|**Outlook Web Access**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tous|Subset|Voir la [référence des conseils de stratégie de protection contre la perte de données](#data-loss-prevention-policy-tips-reference)|
|**Outlook Win32 (Outlook 2013 et au-delà)**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Subset|Subset|Consultez Outlook [2013](#outlook-2013-and-later-supports-showing-policy-tips-for-only-some-conditions-and-exceptions) et les ultérieures prend en charge l'affichage de conseils de stratégie uniquement pour certaines conditions et exceptions et la prise en charge [d'Outlook 2013](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) et des applications Office sur bureau affichant des conseils de stratégie pour certains types d'informations sensibles uniquement pour plus d'informations sur la prise en charge des types d'informations sensibles et des conditions et actions DLP prises en charge pour afficher les conseils de stratégie DLP sur Outlook Win32.|
|**Outlook Mobile (iOS, Android)/Outlook Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Aucun|Aucun|Les conseils de stratégie DLP ne sont pas pris en charge sur Outlook Mobile|
|**Client Web Sharepoint Online/One Drive for Business**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tous|Tous les prédicats et actions SPO/ODB dans DLP||
|**Client Win32 Sharepoint/ One Drive pour entreprise**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Aucun|Aucun|Les conseils de stratégie DLP ne sont pas pris en charge sur les applications clientes de bureau SharePoint ou OneDrive|
|**Word, Excel, PowerPoint Web Client**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tous|Tous les prédicats et actions SPO/ODB dans DLP|Le conseil de stratégie DLP est pris en charge si le document est hébergé sur SPO ou l'application web ODB et que la stratégie DLP est déjà estampillée.|
|**Word, Excel, PowerPoint Mobile Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Aucun|Aucun|Les conseils de stratégie DLP ne sont pas pris en charge dans les applications mobiles pour Office.|
|**Teams Web/ Teams Desktop/ Teams Mobile/ Teams Mac**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Tous|Tous les prédicats Teams dans la stratégie DLP|Les conseils de stratégie s'afficheront lorsqu'un message est marqué comme « Ce message a été marqué. Que puis-je faire ? Lorsque vous cliquez sur le lien, l'utilisateur peut passer en revue les types d'informations sensibles détectés et remplacer ou signaler un problème si autorisé par l'administrateur. Notez qu'aucun conseil de stratégie n'est affiché pour les fichiers. Lorsque le destinataire tente d'accéder au document, il se peut qu'il obtienne un accès refusé s'il n'est pas autorisé.|
|**Appareils de point de terminaison Win32**|:::image type="icon" source="../media/rightmrk.png" border="false":::|Subset|Tous les prédicats et actions DLP de point de terminaison dans la stratégie DLP|Voir Protection [contre la perte de données sur le point de terminaison prend en charge les conseils de stratégie pour certains types d'informations sensibles uniquement](#data-loss-prevention-on-endpoint-devices-supports-policy-tips-for-only-some-sensitive-information-types)|
|**Appareils Mac**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Aucun|Aucun|Les stratégies de protection contre la perte de données ne sont pas actuellement appliquées sur les appareils Mac|
|**Applications cloud tierces**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Aucun|Aucun|Les conseils de stratégie de protection contre la perte de données ne sont pas pris en charge sur les applications cloud tierces|
|**Sur place**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Aucun|Aucun||
|**Word, Excel, PowerPoint Win32 Client**|:::image type="icon" source="../media/crsmrk.png" border="false":::|Subset|Subset|Consultez [outlook 2013](#outlook-2013-and-later-and-office-apps-on-desktop-support-showing-policy-tips-for-only-some-sensitive-information-types) et version ultérieure et la prise en charge des applications Office sur bureau affichant des conseils de stratégie pour certains types d'informations sensibles uniquement pour la liste des types d'informations sensibles pris en charge</br></br>Les conseils de stratégie pour les applications clientes WXP fonctionnent pour les documents stockés sur Sharepoint Online ou one drive for Business Sites pour toutes les stratégies DLP qui ont exactement les conditions ou actions ci-dessous ou un sous-ensemble de conditions ou d'actions dans la stratégie DLP :</br> <ul><li>Le contenu contient des types d'informations sensibles</li><li>Étendue d'accès (le contenu est partagé en interne/en externe)</li><li>Avertir l'utilisateur (conseils de stratégie/notifications utilisateur)</li><li>Bloquer tout le monde</li><li>Rapports d’incident</li></ul></br> Si une autre condition ou action est présente, le conseil de stratégie DLP pour cette stratégie n'apparaîtra pas dans les applications de bureau de Word, Excel ou PowerPoint.</br>Voir [les conseils de stratégie dans Excel, PowerPoint et Word](use-notifications-and-policy-tips.md#policy-tips-in-excel-powerpoint-and-word) pour plus d'informations|
||||||
