---
title: Notification de violation
description: Découvrez comment les services Microsoft assurent une protection contre les violations de données personnelles, et comment Microsoft réagit et envoie des notifications en cas de violation.
keywords: Microsoft 365, Microsoft 365 Éducation, documentation Microsoft 365, RGPD
localization_priority: Priority
ms.prod: microsoft-365-enterprise
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
titleSuffix: Microsoft GDPR
ms.openlocfilehash: a671fc9234f76c63ff7336369c87e680a4432cc3
ms.sourcegitcommit: d7975c391e03eeb96e29c1d02e77d2a1433ea67c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/05/2020
ms.locfileid: "48920288"
---
# <a name="gdpr-breach-notification"></a>Notification de violation RGPD

The General Data Protection Regulation (GDPR) introduces new rules for organizations that offer goods and services to people in the European Union (EU), or that collect and analyze data for EU residents no matter where you or your enterprise are located. Additional details can be found in the [GDPR Summary topic](gdpr.md). This document leads you to information on the completion of Breach Notifications under the GDPR using Microsoft products and services.

## <a name="what-constitute-a-breach-of-personal-data-under-the-gdpr"></a>Selon le RGPD, qu’est-ce qu’une violation de données personnelles ?

Personal data means any information related to an individual that can be used to identify them directly or indirectly. A personal data breach is 'a breach of security leading to the accidental or unlawful destruction, loss, alteration, unauthorized disclosure of, or access to, personal data transmitted, stored, or otherwise processed'.

## <a name="terminology"></a>Terminologie

Définitions utiles pour les termes RGPD utilisés dans ce document :

- *Contrôleur de données (contrôleur)*  : la personne morale, l’autorité publique, le service ou tout autre organisme qui, seul ou conjointement avec d’autres entités, détermine les finalités et les moyens de traitement des données personnelles.  
- *Données personnelles* et *personne concernée*  : toutes les informations relatives à une personne physique identifiée ou identifiable (personne concernée); une personne physique identifiable est une personne qui peut être identifiée, directement ou indirectement.  
- *Responsable du traitement* : la personne physique ou morale, l’autorité publique, le service ou tout autre organisme qui traite des données à caractère personnel pour le compte de l’entité de contrôle.  
- *Données client*  : les données produites et stockées dans les opérations quotidiennes dans le cadre du fonctionnement de votre entreprise.

## <a name="microsoft-and-breach-notification"></a>Microsoft et Notification de violation

Microsoft takes its obligations under the General Data Protection Regulation (GDPR) seriously. A security incident/data breach refers to events such as unlawful access to customer's data stored on Microsoft equipment or in Microsoft facilities, or unauthorized access to such that has the potential to result in the loss, disclosure, or alteration of customer data.

As a data processor, Microsoft ensures that service customers are able to meet the GDPR's breach notification requirements as data controllers. Our notification provides the information needed to make that assessment. Microsoft notifies customers of any personal data breach, except for those cases where personal data is confirmed to be unintelligible (for example, encrypted data where integrity of the keys is confirmed).

Data controllers are responsible for assessing risks to data privacy and determining whether a breach requires notification of a customer's DPA. Microsoft provides the information needed, along with your GDPR compliance policy, to make that assessment.

Initial notification includes a description of the nature of the breach, approximate user impact, and mitigation steps (if applicable). If our investigation is not complete at the time of initial notification, we will indicate next steps and timelines for subsequent communication. For more information about how Microsoft detects and responds to a breach of personal data, see [Data Breach Notification Under the GDPR](https://servicetrust.microsoft.com/ViewPage/GDPRBreach) in the Service Trust Portal.

Les détails relatifs à la notification de violation de certains produits et services Microsoft sont indiqués ci-dessous.
  
1. **[Office 365](gdpr-breach-Office365.md)**  
    Microsoft invests extensively in systems, processes, and personnel to reduce the likelihood of personal data breach and to quickly detect and mitigate consequence of breach if it does occur. Additional details can be read at [Office 365 Investments in Data Security](https://docs.microsoft.com/microsoft-365/compliance/gdpr-breach-office365#office-365-investments-in-data-security).

    A customer may become aware of a breach and wish to contact Microsoft. In this case, notify Microsoft Support, which will then interface with engineering teams for more information.

2. **[Azure et Dynamics 365](gdpr-breach-azure-dynamics.md)**  
    Microsoft met à disposition un service de réponse mondial aux incidents fonctionnant 24 heures sur 24 et 7 jours sur 7 qui permet d’atténuer les effets des attaques contre Microsoft Azure et Dynamics 365.

    - *Détection des infractions* : puisque Microsoft et le client ont des obligations en matière de sécurité, les services Azure utilisent un seul et même modèle de responsabilité pour définir la sécurité et les responsabilités opérationnels. Microsoft ne surveille ni ne répond aux incidents de sécurité dans le domaine de responsabilité du client. Les réponses aux incidents clients peuvent impliquer une collaboration avec Azure [le support client](https://azure.microsoft.com/support/options/), en fonction de contrats de service appropriés. Microsoft Azure offre également d’autres services (par exemple, [Azure Defender](https://azure.microsoft.com/services/security-center/)) que les clients peuvent utiliser pour développer et gérer les réponses aux incidents de sécurité.

        For a list of events that trigger a breach investigation in Microsoft Azure, see [Detection of Potential Breaches](https://docs.microsoft.com/microsoft-365/compliance/gdpr-breach-azure-dynamics#detection-of-potential-breaches). [Azure and Breach Notification under the GDPR](gdpr-breach-azure-dynamics.md) further details how Microsoft investigates, manages, and responds to security incidents within Azure.

    - *Data Breach Response* : Microsoft determines appropriate priority and severity levels of a breach by investigating the functional impact, recoverability, and information impact of the incident. Priority and severity may change over the course of the investigation, based on new findings and conclusions. Microsoft's security response team works closely with global legal advisors to help ensure that forensics are performed in accordance with legal obligations and commitments to customers. These processes are detailed in [Azure's Data Breach Response](https://docs.microsoft.com/microsoft-365/compliance/gdpr-breach-azure-dynamics#azures-data-breach-response).

    - *Customer Notification* : Microsoft Azure notifies customers and regulatory authorities of data breaches as required. Customer notices are delivered in no more than 72 hours from the time we declared a breach except for the following circumstances:

        - Microsoft estime que l’envoi d’une notification augmente le risque pour d’autres clients.
        - The 72-hour timeline may leave some incident details available. These details will be provided to you as the investigation proceeds.

        Pour plus d’informations, consultez la [Notification du client](https://docs.microsoft.com/microsoft-365/compliance/gdpr-breach-azure-dynamics#customer-notification).

3. **[Support Microsoft et services professionnels](gdpr-breach-Microsoft-Support-Professional-Services.md)**  
    The nature of professional services means that some data protection incidents may fall within the customer's realm of responsibility. When Microsoft Professional Services identifies a data protection incident, it follows documented industry standard response plan as outlined in [Scope & Limits of Data Protection Incident Response Process](https://docs.microsoft.com/microsoft-365/compliance/gdpr-breach-microsoft-support-professional-services#scope--limits-of-data-protection-incident-response-process).

## <a name="breach-notification-admin-tools"></a>Outils d’administration de la notification de violation

- **Définir le contact de votre organisation en matière de confidentialité** Les administrateurs de locataire peuvent utiliser le [portail d’administration Azure Active Directory](https://go.microsoft.com/fwlink/p/?linkid=2052736) pour définir le contact de confidentialité de votre organisation dont Microsoft a besoin pour communiquer avec eux.

## <a name="learn-more"></a>En savoir plus

- [Centre de gestion de la confidentialité Microsoft](https://www.microsoft.com/trust-center/privacy/gdpr-overview)
