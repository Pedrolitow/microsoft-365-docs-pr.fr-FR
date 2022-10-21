---
title: Comparer des modèles personnalisés dans Microsoft Syntex
ms.author: chucked
author: chuckedmonson
manager: pamgreen
ms.reviewer: lauris
audience: admin
ms.topic: article
ms.service: microsoft-syntex
search.appverid: ''
ms.collection:
- enabler-strategic
- m365initiative-syntex
ms.localizationpriority: medium
description: Découvrez les principales différences entre les modèles personnalisés dans Microsoft Syntex.
ms.openlocfilehash: 63d6d444fad48da993413b15943bffda7b175ad1
ms.sourcegitcommit: 87283bb02ca750286f7c069f811b788730ed5832
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/21/2022
ms.locfileid: "68660090"
---
# <a name="compare-custom-models-in-microsoft-syntex"></a>Comparer des modèles personnalisés dans Microsoft Syntex 

Utilisez le tableau suivant pour voir les différences dans les modèles personnalisés afin d’identifier le modèle le plus approprié à utiliser pour vos besoins.

| Fonctionnalité | Traitement de documents non structurés | Traitement de documents en forme libre | Traitement de document structuré |
| ------- | ------- | ------- | ------- |
| Utiliser pour ce type de contenu | Formats de fichiers non structurés ou semi-structurés, par exemple des documents Office où il existe des différences dans la disposition, mais des informations similaires à extraire. | Formats de fichiers non structurés et de forme libre, par exemple des documents qui n’ont pas de structure définie, comme des lettres, des contrats et des instructions de travail. | Formats de fichiers structurés et semi-structurés, par exemple des fichiers PDF pour le contenu des formulaires tels que des factures ou des bons de commande dont la disposition et la mise en forme sont similaires. |
| Création de modèles | Modèle créé dans SharePoint dans un nouveau site, le centre de contenu.  | Modèle créé dans [AI Builder](/ai-builder/overview) avec un accès transparent à partir de la bibliothèque de documents SharePoint.| Modèle créé dans [AI Builder](/ai-builder/overview) avec un accès transparent à partir de la bibliothèque de documents SharePoint. |
| Type de classification | Classifieur pouvant être formé avec des extracteurs facultatifs utilisant l’apprentissage automatique pour attribuer l’emplacement du document aux données à extraire. | Non applicable | Non applicable |
| Emplacements | Peut être appliqué à plusieurs bibliothèques. | Formé pour une seule bibliothèque de documents. | Formé pour une seule bibliothèque de documents. |
| Types de fichiers pris en charge | Effectuez l’apprentissage sur les fichiers 5-10 .pdf, Office ou e-mail, y compris des exemples négatifs.<br>Les fichiers Office sont tronqués à 64 000 caractères. Les fichiers numérisés par OCR sont limités à 20 pages. Prend en charge plus de 20 types de fichiers. Consultez Types [de fichiers pris en charge](requirements-and-limitations.md#unstructured-document-processing).  | Effectuer l’apprentissage au format .pdf, .jpg ou .png, total de 50 Mo et 500 pages. | Effectuer l’apprentissage au format .pdf, .jpg ou .png, total de 50 Mo et 500 pages. |
| Intégrer avec des métadonnées managées | Oui, par l’extracteur de l’entité de formation qui fait référence à un champ de métadonnées gérées configurée. | Non | Non |
| Intégration des fonctionnalités de conformité à Protection des données Microsoft Purview | Définir des étiquettes de rétention publiées.<br>Définir des étiquettes de confidentialité publiées. | Définir des étiquettes de rétention est à venir. <br>Définir des étiquettes de confidentialité est à venir. | Définir des étiquettes de rétention publiées. <br>Définir des étiquettes de confidentialité est à venir. |
| Régions prises en charge| Disponible dans toutes les régions. | S’appuie sur Power Platform. Pour plus d’informations sur la disponibilité globale de la plateforme Power et du Générateur d’intelligence artificielle, consultez [Disponibilité de la plateforme Power](https://dynamics.microsoft.com/geographic-availability/). | S’appuie sur Power Platform. Pour plus d’informations sur la disponibilité globale de la plateforme Power et du Générateur d’intelligence artificielle, consultez [Disponibilité de la plateforme Power](https://dynamics.microsoft.com/geographic-availability/). |
| Coût transactionnel | Non applicable | Utilise des crédits de générateur d’intelligence artificielle.<br>3 500 crédits sont inclus pour chaque licence Syntex par mois.<br>1 million de crédits permettra le traitement de 2 000 pages de fichiers. | Utilise des crédits de générateur d’intelligence artificielle.<br>3 500 crédits sont inclus pour chaque licence Syntex par mois.<br>1 million de crédits permettra le traitement de 2 000 pages de fichiers. |
| Capacité | Aucune restriction de capacité. | Utilise l’environnement de plateforme Power par défaut (environnements personnalisés pris en charge par la base de données de dataverse). | Utilise l’environnement de plateforme Power par défaut (environnements personnalisés pris en charge par la base de données de dataverse). |
| Langues prises en charge| Les modèles fonctionnent sur toutes les langues de l’alphabet latin. En plus de l’anglais : l’allemand, le suédois, le Français, l’espagnol, l’italien et le portugais. | La prise en charge linguistique actuelle est pour l’anglais. | Prise en charge linguistique pour [73 langues](/ai-builder/form-processing-model-requirements.md#languages-supported). |

## <a name="see-also"></a>Voir aussi

[Formation : Améliorer les performances de votre entreprise avec AI Builder](/training/paths/improve-business-performance-ai-builder/?source=learn)


