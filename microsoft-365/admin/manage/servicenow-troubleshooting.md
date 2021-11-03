---
title: Résolution des problèmes Microsoft 365 l’intégration avec ServiceNow
f1.keywords:
- NOCSH
ms.author: pebaum
author: pebaum
manager: scotv
audience: Admin
ms.topic: article
ms.service: o365-administration
ms.localizationpriority: medium
ms.collection:
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide de configuration et d’installation d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: 24813fe0d0705d9404fa465420e3b0344f43f953
ms.sourcegitcommit: bf3965b46487f6f8cf900dd9a3af8b213a405989
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/02/2021
ms.locfileid: "60661762"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>Résolution des problèmes Microsoft 365 l’intégration avec ServiceNow

| \#  | Problème  | Action de diagnostic     |
|-----|--------------------------------|----------------------|
| 1   | Ne peut pas voir **l’onglet Microsoft 365 prise en charge**                                                                                                                                                                                    | Vérifier l’affichage actuel et **tous les** journaux système avec filtre x &gt;  \_ mioms \_ m365 \_ assit                        |
| 2   | Sélectionnez **les solutions recommandées par Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                                                      | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 3   | Sélectionnez **les solutions recommandées par Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».                                                                | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 4    | Tapez le problème dans la zone de recherche et sélectionnez les **solutions recommandées** par Microsoft, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                   | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 5   | Tapez le problème dans la zone de recherche et sélectionnez les **solutions recommandées** par Microsoft, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».                                 | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 6    | Sélectionnez **Contacter le support Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                                                       | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 7    | Sélectionnez **Contacter le support Microsoft,** mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».                                                                 | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 8    | Sélectionnez **Contacter le support Microsoft,** mais obtenez l’erreur « {EmailAddress} n’est pas un compte d’administrateur Microsoft 365 valide. Vous devez Microsoft 365'administrateur pour ouvrir une demande de service. Dans l’application, lier le compte d’administrateur. » | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 9    | Sélectionnez **les solutions recommandées par Microsoft,** mais rien ne s’affiche                                                                                                                                                            | Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com |
| 10  | Sélectionnez **les solutions recommandées par Microsoft,** mais obtenez l’erreur « Veuillez contacter le support de l’application ».                                                                                                                                     | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 11  | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées** par Microsoft, mais rien ne s’affiche                                                                                                                             | Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com |
| 12   | Tapez un problème dans la zone de recherche et sélectionnez **les solutions recommandées** par Microsoft, mais obtenez l’erreur « Veuillez contacter le support de l’application ».                                                                                                      | Vérifier le message d’erreur  en haut du formulaire et tous les journaux système avec &gt;  filtre x \_ mioms \_ m365 \_ assit     |
| 13  | L’utilisateur sélectionne **contacter le support Microsoft,** mais rien ne se produit                                                                                                                                                            | Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com |
| 14   | Can’t see Microsoft recommended solution after reopening the incident                                                                                                                                                      | Vérifier **tous les journaux** &gt; **système** avec filtre x \_ mioms \_ m365 \_ assit                                              |
| 15   | Can’t see Microsoft cases when reopening the incident that was transferred to Microsoft support                                                                                                                            | Vérifier **tous les journaux** &gt; **système** avec filtre x \_ mioms \_ m365 \_ assit                                              |
| 16  | Impossible d’enregistrer les détails du ticket, obtenez l’erreur « Impossible d’enregistrer les détails du ticket. Veuillez contacter le support technique de l’application. »                                                                                                                          | Vérifier le message d’erreur en haut du formulaire                                                                            |
