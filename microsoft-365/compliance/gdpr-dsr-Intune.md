---
title: Demandes des données Intune des personnes concernées pour le RGPD et le CCPA
description: Découvrez comment trouver des données personnelles et agir sur celles-ci, et de répondre aux demandes DSR et CCPA par des clients à l’aide de Microsoft Intune.
keywords: Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365, RGPD, CCPA
localization_priority: Priority
ms.prod: Microsoft-365-enterprise
ms.topic: article
f1.keywords:
- NOCSH
ms.author: robmazz
author: robmazz
manager: laurawi
audience: itpro
ms.collection:
- GDPR
- M365-security-compliance
ms.custom:
- seo-marvel-mar2020
hideEdit: true
titleSuffix: Microsoft GDPR
ms.openlocfilehash: a9dd161edd740aa97e97afa02a6c53933a6ac211
ms.sourcegitcommit: 973f5449784cb70ce5545bc3cf57bf1ce5209218
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/19/2020
ms.locfileid: "44817653"
---
# <a name="intune-data-subject-requests-for-the-gdpr-and-ccpa"></a>Demandes des données Intune des personnes concernées pour le RGPD et le CCPA

The European Union [General Data Protection Regulation (GDPR)](https://ec.europa.eu/justice/data-protection/reform/index_en.htm) gives rights to people (known in the regulation as *data subjects*) to manage the personal data that has been collected by an employer or other type of agency or organization (known as the *data controller* or just *controller*). Personal data is defined very broadly under the GDPR as any data that relates to an identified or identifiable natural person. The GDPR gives data subjects specific rights to their personal data; these rights include obtaining copies of personal data, requesting corrections to it, restricting the processing of it, deleting it, or receiving it in an electronic format so it can be moved to another controller. A formal request by a data subject to a controller to take an action on their personal data is called a *Data Subject Request* or DSR.

De même, le CCPA (California Consumer Privacy Act), prévoit des droits de confidentialité et des obligations pour les consommateurs de la Californie, y compris des droits similaires aux droits des personnes concernées du RGPD, tels que le droit de supprimer, d’accéder et de recevoir (portabilité) leurs informations personnelles.  Le CCPA prévoit également des publications d’informations, des protections contre la discrimination des personnes faisant usage de leurs droits et la possibilité d’opter pour ou contre certains transferts de données classés en tant que « ventes ». Les ventes sont largement définies pour inclure le partage de données à des fins importantes. Pour plus d’informations sur le CCPA, voir le [California Consumer Privacy Act](offering-ccpa.md) et le [Forum aux questions California Consumer Privacy Act](ccpa-faq.md).

Le guide explique comment utiliser les produits, services et outils d’administration Microsoft pour aider les clients de notre entité de contrôle à rechercher des données personnelles et à prendre des mesures pour répondre aux DPC. Plus précisément, il explique comment rechercher des données ou des informations personnelles qui sont stockées dans le cloud Microsoft, comment y accéder et comment entreprendre une action sur ces données. Voici un aperçu rapide des processus présentés dans ce guide :

- **Découvrir** : utilisez les outils de recherche et de détection pour rechercher plus facilement les données du client qui peuvent faire l’objet d’une demande DPC. Une fois que vous avez collecté les documents susceptibles de répondre à la demande, vous pouvez effectuer une ou plusieurs des actions DPC décrites ci-après. Vous pouvez également décider que la demande ne satisfait pas aux directives de votre organisation en termes de réponse à une demande DPC.
- **Accéder :** récupérez des données à caractère personnel qui résident dans le cloud Microsoft et, si nécessaire, effectuez-en une copie pour la personne concernée.
- **Rectifier :** modifiez ou mettez en œuvre d’autres actions demandées sur les données à caractère personnel, le cas échéant.
- **Limiter** : limiter le traitement des données personnelles en supprimant les licences de différents services Azure ou en désactivant les services souhaités lorsque c’est possible. Vous pouvez également supprimer les données du cloud Microsoft et les conserver localement ou à un autre emplacement.
- **Supprimer :** supprimez définitivement des données à caractère personnel qui résidaient dans le cloud Microsoft.
- **Exporter/Recevoir (Portabilité) :** fournit une copie électronique (dans un format lisible par un ordinateur) des données ou des informations personnelles à la personne concernée. Les informations à caractère personnel sous CCPA englobent toutes les informations relatives à une personne identifiée ou identifiable. Aucune distinction n’est faite entre les rôles privé, public et professionnel d’une personne. Le terme défini « informations personnelles » est à peu près aligné sur celui de « données personnelles » dans le RGPD. Toutefois, le CCPA inclut également les données relatives à la famille et au foyer. Pour plus d’informations sur le CCPA, voir le [California Consumer Privacy Act](offering-ccpa.md) et le [Forum aux questions California Consumer Privacy Act](ccpa-faq.md).

Chaque section de ce guide décrit les procédures techniques qu’une organisation étant une entité de contrôle des données peut suivre pour répondre à une DPC pour des données personnelles dans le cloud Microsoft.

#### <a name="terminology"></a>Terminologie

Vous trouverez ci-dessous des définitions de termes utilisés dans ce guide.

- **Responsable du traitement des données :** la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui, seul ou conjointement avec d’autres, détermine les finalités et les moyens du traitement des données à caractère personnel ; lorsque les finalités et les moyens du traitement sont déterminés par la législation de l’Union ou des États membres, le responsable du traitement peut être désigné, ou les critères spécifiques relatifs à sa nomination être définis, par la législation de l’Union ou des États membres.
- **Données personnelles et personne concernée par le traitement des données :** informations relatives à une personne physique identifiée ou identifiable (« la personne concernée par le traitement des données ») ; une personne physique identifiable est une personne qui peut être identifiée, directement ou indirectement, notamment par référence à un identificateur par exemple, un nom, un numéro d’identification, des données de localisation, un identificateur en ligne, ou un ou plusieurs facteurs spécifiques de l’identité physique, physiologique, génétique, mentale, économique, culturelle ou sociale de cette personne physique.
- **Sous-traitant de données :** la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui traite des données à caractère personnel pour le compte du responsable du traitement.
- **Données client :** toutes les données, y compris tous les fichiers texte, son, vidéo ou image et les logiciels qui ont été fournis à Microsoft par le client ou pour son compte dans le cadre du service d’entreprise. Les données client incluent à la fois les (1) informations d’identification personnelle des utilisateurs finaux (par exemple, les noms d’utilisateur et les informations de contact dans Azure Active Directory) et le Contenu Client chargé ou créé par un client dans des services spécifiques (par exemple, le contenu client dans un compte de stockage Azure, le contenu client d’une base de données Azure SQL ou l’image de la machine virtuelle d’un client dans des machines virtuelles Azure).
- **Journaux générés par le système :** journaux et données associées générés par Microsoft qui permettent à Microsoft de fournir des services d’entreprise aux utilisateurs. Les journaux générés par le système contiennent essentiellement des données pseudonymes, généralement un numéro généré par le système qui ne permet pas, en soi, d’identifier une personne individuelle, mais qui est utilisé pour fournir les services d’entreprise aux utilisateurs. Les journaux générés par le système peuvent également contenir des informations d’identification personnelle sur les utilisateurs finaux, telles qu’un nom d’utilisateur.

#### <a name="how-to-use-this-guide"></a>Comment utiliser ce guide

Ce guide est composé de deux parties :

- **Partie 1 : Répondre aux demandes des personnes concernées pour des données client** : la première partie de ce guide explique comment rectifier, limiter, supprimer et exporter des données dans des applications dans lesquelles vous avez créé des données, et comment y accéder.  Cette section explique en détail comment exécuter des DPC par rapport à un contenu client et des informations d’identification personnelle d’utilisateurs finaux.
- **Partie 2 : répondre aux demandes de personnes concernées pour les journaux générés par le système** : lorsque vous utilisez les services d’entreprise de Microsoft, Microsoft génère des informations appelées Journaux générés par le système, pour fournir le service.  La deuxième partie de ce guide explique comment supprimer et exporter ces informations pour Azure, et comment y accéder.

### <a name="understanding-dsrs-for-azure-active-directory-and-microsoft-intune"></a>Présentation des DPC pour Azure Active Directory et Microsoft Intune

When considering services provided to enterprise customers, execution of DSRs must always be understood within the context of a specific Azure Active Directory (AAD) tenant. Notably, DSRs are always executed within a given AAD tenant. If a user is participating in multiple tenants, it is important to emphasize that a given DSR is *only* executed within the context of the specific tenant the request was received within. This is critical to understand as it means the execution of a DSR by one enterprise customer **will not** impact the data of an adjacent enterprise customer.

The same also applies for Microsoft Intune provided to an enterprise customer: execution of a DSR against an Intune account *associated with an AAD tenant* **will only** pertain to data within the tenant. In addition, it is important to understand the following when handling Intune accounts within a tenant:

- If an Intune user creates an Azure subscription, the subscription will be handled as if it were an AAD tenant. Consequently, DSRs are scoped within the tenant as described above.
- If an Azure subscription created via an Intune account is deleted, **it will not affect** the actual Intune account. Again, as noted above, DSRs executing within the Azure subscription are limited to the scope of the tenant itself.

DSRs against an Intune account itself, **outside a given tenant**, are executed via the Consumer Privacy Dashboard. Please refer to the Windows Data Subject Request Guide for further details.

## <a name="part-1-dsr-guide-for-customer-data"></a>Partie 1 : Guide des DSR pour les données client

### <a name="executing-dsrs-against-customer-data"></a>Exécution des DPC par rapport aux données client

Microsoft provides the ability to access, delete, and export certain Customer Data through the Azure Portal and also directly via pre-existing application programming interfaces (APIs) or user interfaces (UIs) for specific services (also referred to as *in-product experiences*). Details regarding such in-product experiences are described in the respective services' reference documentation.

>[!IMPORTANT]  
>Services supporting in-product DSRs require direct usage of the service's application programming interface (API) or user interface (UI), describing applicable CRUD (create, read, update, delete) operations. Consequently, execution of DSRs within a given service must be done in addition to execution of a DSR within the Azure Portal in order to complete a full request for a given data subject. Please refer to specific services' reference documentation for further details.

### <a name="step-1-discover"></a>Étape 1 : Découvrir

The first step in responding to a DSR is to find the personal data that is the subject of the request. This first step - finding and reviewing the personal data at issue - will help you determine whether a DSR meets your organization's requirements for honoring or declining a DSR. For example, after finding and reviewing the personal data at issue, you may determine the request doesn't meet your organization's requirements because doing so may adversely affect the rights and freedoms of others.

After you find the data, you can then perform the specific action to satisfy the request by the data subject. For details, see the following:

- [Collecte de données](https://docs.microsoft.com/intune/privacy-data-collect)
- [Traitement et stockage des données](https://docs.microsoft.com/intune/privacy-data-store-process)
- [Afficher les données personnelles](https://docs.microsoft.com/intune/privacy-data-view-correct#view-personal-data)

### <a name="step-2-access"></a>Étape 2 : Accéder

After you've found Customer Data containing personal data that is potentially responsive to a DSR, it is up to you and your organization to decide which data to provide to the data subject. You can provide them with a copy of the actual document, an appropriately redacted version, or a screenshot of the portions you have deemed appropriate to share. For each of these responses to an access request, you will have to retrieve a copy of the document or other item that contains the responsive data.

Lorsque vous fournissez une copie à la personne concernée, vous devrez peut-être supprimer ou modifier des informations personnelles sur d’autres personnes concernées et des informations confidentielles.

La section suivante explique comment obtenir une copie de données pour répondre à la demande d’accès d’une DPC.

#### <a name="azure-active-directory"></a>Azure Active Directory

Microsoft offre un portail et des expériences intégrées au produit permettant à l’administrateur client de l’entreprise cliente de gérer les demandes d’accès de personne concernée. Les demandes d’accès de personne concernée autorisent l’accès aux données à caractère personnel de l’utilisateur, à savoir : (a) les informations identifiables sur un utilisateur final et (b) les journaux générés par le service.

#### <a name="service-specific-interfaces"></a>Interfaces propres au service

Microsoft Intune permet de [découvrir des données client](#step-1-discover) directement via les interfaces utilisateur (IU) ou les interfaces de programmation d’applications préexistantes (API).

### <a name="step-3-rectify"></a>Étape 3 : Rectifier

If a data subject has asked you to rectify the personal data that resides in your organization's data, you and your organization will have to determine whether it's appropriate to honor the request. Rectifying the data may include taking actions such as editing, redacting, or removing personal data from a document or other type or item.

As a data processor, Microsoft does not offer the ability to correct system-generated logs as it reflects factual activities and constitutes a historical record of events within Microsoft services. With respect to Intune, admins can't update device or app specific information. If an end user wants to correct any personal data (like the device name), they must do so directly on their device. Such changes are synchronized the next time they connect to Intune.

### <a name="step-4-restrict"></a>Étape 4 : Restreindre

Les personnes concernées peuvent vous demander de restreindre le traitement de leurs données à caractère personnel. Nous fournissons le portail Azure et les interfaces de programmation d’applications (API) ou interfaces utilisateur (UI) préexistantes. Ces expériences permettent à l’administrateur client de l’entreprise cliente de gérer ces DPC via une combinaison d’exportation et de suppression de données. Pour plus d’informations, voir [traitement de données personnelles](https://docs.microsoft.com/intune/privacy-data-store-process#processing-personal-data).

### <a name="step-5-delete"></a>Étape 5 : Supprimer

The "right to erasure" by the removal of personal data from an organization's Customer Data is a key protection in the GDPR. Removing personal data includes removing all personal data and system-generated logs, except audit log information. For details, see [Delete end user personal data](https://docs.microsoft.com/intune/privacy-data-audit-export-delete#delete-end-user-personal-data).

## <a name="part-2-system-generated-logs"></a>Partie 2 : Journaux générés par le système

Audit logs provide tenant admins with a record of activities that generate a change in Microsoft Intune. Audit logs are available for many manage activities and typically create, update (edit), delete, and assign actions. Remote tasks that generate audit events can also be reviewed. These audit logs may contain personal data from users whose devices are enrolled in Intune. Admins can't delete audit logs. For details, see [Audit personal data](https://docs.microsoft.com/intune/privacy-data-audit-export-delete#audit-personal-data).

## <a name="notify-about-exporting-or-deleting-issues"></a>Notification des problèmes d’exportation ou de suppression

Si vous rencontrez des problèmes lorsque vous exportez ou supprimez des données sur le portail Azure, accédez au panneau **Aide + Support** du portail Azure et envoyez un nouveau ticket sous **Gestion des abonnements > Autre demande de conformité et de sécurité > Confidentialité et demandes dans le cadre du RGPD**.

## <a name="learn-more"></a>En savoir plus

- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trust-center/privacy/gdpr-overview)
