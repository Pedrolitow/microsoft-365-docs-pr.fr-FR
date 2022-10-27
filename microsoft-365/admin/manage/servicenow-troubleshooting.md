---
title: Résoudre les problèmes d’intégration de la prise en charge Microsoft 365 avec ServiceNow
f1.keywords:
- NOCSH
ms.author: efrene
author: efrene
manager: scotv
audience: Admin
ms.topic: article
ms.service: microsoft-365-business
ms.localizationpriority: medium
ms.collection:
- Tier2
- scotvorg
- M365-subscription-management
- Adm_TOC
ms.custom: AdminSurgePortfolio
ROBOTS: NOINDEX, NOFOLLOW
search.appverid:
- MET150
description: Guide d’installation et de configuration d’applications certifiées étendues pour ServiceNow.
ms.openlocfilehash: f0972b937c864191ba5f6d2eb5689c879d1d5d5e
ms.sourcegitcommit: 181a0aff54842dcbafd834647c6e9ee47304d10f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/27/2022
ms.locfileid: "68734316"
---
# <a name="troubleshooting-microsoft-365-support-integration-with-servicenow"></a>Résoudre les problèmes d’intégration de la prise en charge Microsoft 365 avec ServiceNow

| \#  | Problème  | Action de diagnostic     |
|-----|--------------------------------|----------------------|
| 1   | Onglet Prise en **charge de Microsoft 365** introuvable                                                                                                                                                                                    | Vérifier la vue actuelle et **tous les** **journaux** &gt; système avec le filtre x\_mioms\_m365\_assit                        |
| 2   | Sélectionnez les **solutions recommandées par Microsoft** , mais obtenez l’erreur « Contactez votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                                                      | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 3   | Sélectionnez les **solutions recommandées par Microsoft** , mais obtenez l’erreur « Contactez votre administrateur ServiceNow et demandez-lui d’effectuer l’étape de configuration finale de l’application ».                                                                | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 4   | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Contactez votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                   | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 5   | Tapez le problème dans la zone de recherche et sélectionnez **solutions recommandées par Microsoft** , mais obtenez l’erreur « Veuillez contacter votre administrateur ServiceNow et demandez-lui d’effectuer l’étape de configuration finale pour l’application ».                                 | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 6   | Sélectionnez **Contacter le support Microsoft**, mais obtenez l’erreur « Contactez votre administrateur ServiceNow et demandez-lui d’effectuer les étapes de configuration de l’application ».                                                                       | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 7    | Sélectionnez **Contacter le support Microsoft**, mais obtenez l’erreur « Contactez votre administrateur ServiceNow et demandez-lui d’effectuer l’étape de configuration finale de l’application ».                                                                 | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 8    | Sélectionnez **Contacter le support Microsoft** , mais obtenez l’erreur « {EmailAddress} n’est pas un compte d’administrateur Microsoft 365 valide. Vous avez besoin de privilèges d’administrateur Microsoft 365 pour ouvrir une demande de service. Dans l’application, liez le compte administrateur. » | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 9    | Sélectionnez les **solutions recommandées par Microsoft** , mais rien ne s’affiche                                                                                                                                                            | Vérifier **les journaux système – Journaux HTTP sortants** avec filtre login.microsoftonline.com et connector.rave.microsoft.com |
| 10  | Sélectionnez **les solutions recommandées par Microsoft** , mais obtenez l’erreur « Contactez le support de l’application ».                                                                                                                                     | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 11  | Tapez le problème dans la zone de recherche et sélectionnez **les solutions recommandées par Microsoft** , mais rien ne s’affiche                                                                                                                             | Vérifier **les journaux système – Journaux HTTP sortants** avec filtre login.microsoftonline.com et connector.rave.microsoft.com |
| 12   | Tapez le problème dans la zone de recherche et sélectionnez **solutions recommandées par Microsoft** , mais obtenez l’erreur « Contactez le support de l’application ».                                                                                                      | Vérifiez le message d’erreur en haut du formulaire et des **journaux** &gt; système **tous** avec le filtre x\_mioms\_m365\_assit     |
| 13  | L’utilisateur sélectionne **Contacter le support Microsoft**, mais rien ne se passe                                                                                                                                                            | Vérifier **les journaux système – Journaux HTTP sortants** avec filtre login.microsoftonline.com et connector.rave.microsoft.com |
| 14  | Impossible de voir la solution recommandée par Microsoft après la réouverture de l’incident                                                                                                                                                      | Vérifier **tous les** **journaux** &gt; système avec le filtre x\_mioms\_m365\_assit                                              |
| 15  | Impossible de voir les cas Microsoft lors de la réouverture de l’incident qui a été transféré au support Microsoft                                                                                                                            | Vérifier **tous les** **journaux** &gt; système avec le filtre x\_mioms\_m365\_assit                                              |
| 16  | Impossible d’enregistrer les détails du ticket, obtenir l’erreur « Impossible d’enregistrer les détails du ticket. Contactez le support technique de l’application. »                                                                                                                          | Vérifier le message d’erreur en haut du formulaire                                                                            |
