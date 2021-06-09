---
title: Scheduler for Microsoft 365 FAQs
ms.author: v-aiyengar
author: AshaIyengar21
manager: serdars
audience: Admin
ms.topic: article
ms.service: scheduler
localization_priority: Normal
description: Scheduler for Microsoft 365 FAQs
ms.openlocfilehash: d4cedf420dd605d04328b7f1edeabbd4e1bb5ac7
ms.sourcegitcommit: e1e275eb88153bafddf93327adf8f82318913a8d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/08/2021
ms.locfileid: "52809164"
---
# <a name="scheduler-for-microsoft-365-faqs"></a>Scheduler for Microsoft 365 FAQs

**Question :** Comment scheduler s’intègre-t-il à d’autres fonctionnalités de Cortana, telles que *Cortana pour Windows,* e-mail *Briefing* quotidien et *Lire mes e-mails*?</br>
Scheduler est un service indépendant des autres fonctionnalités de Cortana. D’autres fonctionnalités de Cortana peuvent être désactivées au niveau du client, et le Scheduler peut toujours être activé à l’aide de l cortana@yourdomain.com de messagerie. Actuellement, les utilisateurs ne peuvent interagir avec le Scheduler que par courrier électronique.

**Question :** Cela fonctionne-t-il uniquement avec Outlook ? D’autres produits de messagerie sont-ils pris en charge ?</br>
Tant que vous avez une licence, autres que les trois exigences ci-dessus, les utilisateurs peuvent envoyer des cortana@yourdomain.com à partir de n’importe quel client de messagerie sur n’importe quel appareil.

**Question :** Les contacts peuvent-ils se trouver dans une liste de contacts personnelle sur Outlook la liste d’Outlook la liste d’attente ou une autre liste d’coordonnées équivalente à la société ?</br>
Les participants à la réunion peuvent être n’importe qui ayant une adresse de messagerie à l’intérieur ou à l’extérieur de l’entreprise. Malheureusement, scheduler ne peut pas traduire automatiquement les noms en adresses e-mail /alias en le regardant dans la liste d’adresses gal aujourd’hui.

**Question :** Puis-je utiliser Scheduler avec ma version installée (sur site) de Outlook ?</br>
Le programme de planification nécessite Exchange Online. Ne fonctionne pas avec Exchange Server (sur place). Fonctionne avec n’importe quel client de messagerie, Outlook bureau, OWA, iOS, android, gmail, etc.

**Question :** Est Outlook doit être ouvert en arrière-plan ?</br>
Outlook n’a pas besoin d’être ouvert en arrière-plan. Il vous suffit d’envoyer un courrier électronique à Cortana et de vous en appuyer pour faire l’essentiel du travail.

## <a name="frequently-asked-trust-and-privacy-questions"></a>Questions fréquemment posées sur la confidentialité et la confidentialité

**Question :** Comment fonctionne le Scheduler ?</br>
Le programme de planification utilise Scheduling Intelligence (IA) enrichi d’assistants humains. Si les modèles d’IA génèrent un besoin de prise en charge dans le langage naturel de communication avec Cortana, la demande de réunion passe à l’état humain pour révision et achèvement.

**Question : Qui** les humains qui examinent les demandes réexamorées ? </br>
Les assistants de planification sont la SSPA (Microsoft Supplier Security and Privacy Assurance) certifiée pour les informations personnelles et hautement confidentielles. 

**Question :** Que peuvent afficher les Assistants SSPA ?</br>
Le scheduleur et les assistants de la SSPA peuvent afficher les messages électroniques adressés à Cortana. Dans un échange de courriers électroniques à thread, seuls les e-mails qui incluent l’adresse de messagerie de Cortana seront traitées, et non les messages électroniques précédents dans le thread avant l’ajout de Cortana.   

**Question :** Les données client sont-elles conservées dans la base de données du Flow ? </br>
Le programme de planification stocke tout le contenu client dans les limites du client et conserve les données conformément aux directives du R GDPR, aux stratégies de confidentialité Microsoft 365 & de confiance et aux stratégies de messagerie du client.

**Question :** Comment le Scheduler traitera-t-il les données de libre/occupé des participants internes ? </br>
L’automatisation du scheduler utilise le service *findMeetingTimes* pour identifier les heures qui sont mutuellement disponibles pour les participants et l’organisateur. Ce service alimente d’Outlook expériences telles que *les* heures suggérées dans Outlook formulaire de réunion. Les informations de participant de la période de libre/occupé ne sont pas consommées explicitement en tant que blocs de libre/occupé. 

**Question :** Scheduler est-il conforme au R GDPR ? </br>
Oui.

**Question : Qui** a-t-il accès à la boîte aux lettres Cortana ? </br>
Le programme de planification traite les demandes de réunion et les e-mails associés qui sont envoyés à la boîte aux lettres Cortana de votre client. Microsoft n’a aucun autre accès à la boîte aux lettres Cortana, sauf par le biais de l’approbation de Lockbox à la demande de l’administrateur client.  

**Question :** Les données client sont-elles utilisées pour les modèles d’IA de formation ?</br>
Aucun contenu client de Scheduler pour Microsoft 365 ne peut être utilisé pour les jeux de formation sur les données. Tout le contenu client réside dans le client.  

**Question :** Le programme de planification traitera-t-il le courrier chiffré ?</br>
Non, le courrier chiffré sera rejeté par le flux de travail du scheduler. 




