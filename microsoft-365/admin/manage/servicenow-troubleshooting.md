---
title: Résoudre les problèmes d’intégration de la prise en charge Microsoft 365 avec ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
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
ms.openlocfilehash: bac3981b728ac997839e7ac99a9411a8da244add
ms.sourcegitcommit: bdd6ffc6ebe4e6cb212ab22793d9513dae6d798c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/08/2022
ms.locfileid: "63324940"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>Résoudre les problèmes d’intégration de la prise en charge Microsoft 365 avec ServiceNow

| \#  | Problème  | Action diagnostics     |
|-----|--------------------------------|----------------------|
| 1   | Ne peut pas voir l Microsoft 365 **de prise en charge**                                                                                                                                                                                    | Vérifier l’affichage actuel et **tous les journaux système** &gt; **avec le** filtre xmiomsm365assit\_\_\_                        |
| 2   | **Sélectionnez les solutions recommandées par Microsoft**, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                                                      | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 3   | **Sélectionnez les solutions recommandées par Microsoft**, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».                                                                | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 4   | Tapez le problème dans la zone de recherche et sélectionnez les **solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                   | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 5   | Tapez le problème dans la zone de recherche et sélectionnez les **solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».                                 | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 6    | **Sélectionnez Contacter le support Microsoft**, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                                                       | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 7    | **Sélectionnez Contacter le support Microsoft**, mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui de terminer l’étape finale de mise en place de l’application ».                                                                 | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 8    | **Sélectionnez Contacter le support Microsoft**, mais obtenez l’erreur « {EmailAddress} n’est pas un compte d’administrateur Microsoft 365 valide. Vous devez Microsoft 365'administrateur pour ouvrir une demande de service. Dans l’application, lier le compte d’administrateur. » | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 9    | **Sélectionnez les solutions recommandées par Microsoft**, mais rien ne s’affiche                                                                                                                                                            | Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com |
| 10  | Sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter le support de l’application ».                                                                                                                                     | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 11  | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais rien ne s’affiche                                                                                                                             | Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com |
| 12   | Tapez un problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter le support de l’application ».                                                                                                      | Vérifier le message d’erreur en haut du formulaire et tous les journaux **système** &gt; avec filter xmiomsm365assit \_\_\_     |
| 13  | L’utilisateur sélectionne **contacter le support Microsoft**, mais rien ne se produit                                                                                                                                                            | Vérifier **les journaux système : journaux HTTP sortants** avec filtres login.microsoftonline.com et connector.rave.microsoft.com |
| 14   | Can’t see Microsoft recommended solution after reopening the incident                                                                                                                                                      | Vérifier **tous les journaux système** &gt; avec le filtre xmiomsm365assit \_\_\_                                              |
| 15   | Can’t see Microsoft cases when reopening the incident that was transferred to Microsoft support                                                                                                                            | Vérifier **tous les journaux système** &gt; avec le filtre xmiomsm365assit \_\_\_                                              |
| 16  | Impossible d’enregistrer les détails du ticket, obtenez l’erreur « Impossible d’enregistrer les détails du ticket. Veuillez contacter le support technique de l’application. »                                                                                                                          | Vérifier le message d’erreur en haut du formulaire                                                                            |
