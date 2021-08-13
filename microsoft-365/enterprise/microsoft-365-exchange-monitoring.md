---
title: Déployer Exchange Online pour Microsoft 365 Éducation
ms.author: josephd
author: JoeDavies-MSFT
manager: laurawi
ms.date: 12/03/2020
audience: Admin
ms.topic: conceptual
ms.service: o365-administration
localization_priority: Priority
search.appverid:
- MET150
ms.collection:
- Ent_O365
- Strat_O365_Enterprise
f1.keywords:
- NOCSH
description: Si vous souhaitez en savoir plus sur les incidents d’e-mail ou les conseils dans Microsoft 365, utilisez la surveillance d’Exchange Online.
ms.openlocfilehash: fd0e71a33a502f21e9a072a43cbe35dc76582a31def8f7a6ca1e9d2f2ad2592e
ms.sourcegitcommit: a1b66e1e80c25d14d67a9b46c79ec7245d88e045
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/05/2021
ms.locfileid: "53807433"
---
# <a name="exchange-online-monitoring-for-microsoft-365"></a>Déployer Exchange Online pour Microsoft 365 Éducation

La surveillance d’Exchange Online dans le Centre d’administration Microsoft 365 vous permet de surveiller l’état d’intégrité du service Exchange pour l’abonnement Microsoft 365 de votre organisation. La surveillance d’Exchange Online fournit des informations sur les incidents et les conseils collectés dans les catégories suivantes :

- **Infrastructure** : le programme détecte un problème dans l’infrastructure Microsoft 365 détenue par Microsoft pour fournir des mises à jour régulières et résoudre le problème. Par exemple, les utilisateurs ne peuvent pas accéder à Exchange Online en raison de problèmes liés à Exchange ou à une autre infrastructure cloud Microsoft 365.
- **Infrastructure tierce** : le programme détecte un problème dans une infrastructure tierce sur laquelle votre organisation a pris une dépendance. Votre organisation doit alors effectuer l’action nécessaire pour résoudre le problème. Par exemple, un fournisseur de services d’émission de jeton de sécurité (STS) tiers limite les transactions d’authentification utilisateur et empêche les utilisateurs de se connecter à Exchange Online.
- **Infrastructure cliente** : le programme détecte un problème dans l’infrastructure de votre organisation. Celle-ci doit alors effectuer l’action nécessaire pour résoudre le problème. Par exemple, les utilisateurs ne peuvent pas accéder à Exchange Online, car ils ne peuvent pas obtenir de jeton d’authentification via un fournisseur STS hébergé par votre organisation en raison d’un certificat arrivé à expiration.

Voici un exemple de la page **Intégrité des services** dans le Centre d’administration Microsoft 365, disponible via **Intégrité > Intégrité des services**.

![Page Intégrité des services dans le Centre d’administration Microsoft 365](../media/microsoft-365-exchange-monitoring/service-health-dashboard-example.png)

La valeur de la colonne **État** indique si le service est intègre, s’il comporte des conseils ou des incidents sur la base des services cloud gérés par Microsoft. 

La valeur de la colonne **Vos problèmes liés à votre organisation et à des tiers** indique que l’infrastructure de votre organisation ou un logiciel tiers a une incidence sur l’expérience de vos utilisateurs en matière d’intégrité des services avec Exchange Online. Les conseils ou incidents nécessitent *vos* actions pour résoudre le problème.

Voici un exemple de la page de surveillance **Exchange Online** dans le Centre d’administration Microsoft 365, disponible via **Intégrité > Intégrité des services > Exchange Online**.

![Page de surveillance Exchange Online dans le Centre d’administration Microsoft 365](../media/microsoft-365-exchange-monitoring/exhange-monitoring-example.png)

La page de surveillance **Exchange Online** indique si le service Exchange Online est intègre ou non, et si des incidents ou conseils associés sont présents. Avec la surveillance Exchange Online, vous pouvez consulter l’état d’intégrité des services pour des scénarios d’e-mails spécifiques. Vous pouvez également consulter des signaux en temps réel pour déterminer l’impact par scénario. 

## <a name="requirements"></a>Configuration requise

Cette préversion est activée pour les clients qui répondent aux exigences suivantes : 

- Votre organisation doit avoir un nombre de licences d’au moins 5 000, soit une combinaison de ces produits : Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. 

  Par exemple, votre organisation peut avoir 3 000 licences Office 365 E3 et 2 500 Microsoft 365 E5, pour un total de 5 500 licences provenant des produits éligibles.

- Votre organisation doit avoir au moins 50 utilisateurs Exchange Online actifs par mois.

La surveillance d’Exchange Online vous permet de consulter l’état d’intégrité des clients de courrier suivants sur la base de l’activité de lecture des e-mails :

- Version de bureau d’Outlook
- Outlook sur le web
- Clients de messagerie natifs d’iOS et Android 
- Application Outlook Mobile pour iOS et Android 
- Client Outlook Mac

Pour ces clients, vous pouvez connaître le nombre d’utilisateurs actifs au cours des 30 dernières minutes en fonction des utilisateurs qui lisent un e-mail, ainsi que le nombre d’incidents et de conseils dans le tableau de bord. Le programme compare ces données au même intervalle pour la semaine précédente afin de déterminer si un problème s’est produit. 

>[!Note]
> Le programme détermine le nombre d’utilisateurs actifs selon une activité unique. Par exemple, lorsqu’un utilisateur lit un e-mail. Il rend compte seulement des 30 dernières minutes d’activité.
>

Vous pouvez également surveiller l’intégrité d’Exchange Online pour les scénarios suivants :

- **Flux de courriers** : nombre de messages remis correctement dans une boîte aux lettres sans délai une fois le message arrivé sur le réseau Microsoft 365. 
- **Authentification de base et authentification moderne** : nombre d’utilisateurs correctement validés dans le service Exchange Online.

![Exemple de surveillance de l’intégrité d’Exchange pour la livraison des e-mails](../media/microsoft-365-exchange-monitoring/exhange-monitoring-scenario-example.png)

Dans tous ces scénarios, les chiffres clés s’appliquent aux 30 dernières minutes dans le tableau de bord principal. Les affichages détaillés pour chacun de ces scénarios illustrent la tendance quasiment en temps réel pendant sept jours avec un agrégat de 30 minutes comparé à la semaine précédente. 

## <a name="send-us-feedback"></a>Nous envoyer des commentaires

Vous pouvez envoyer vos commentaires de deux manières :

- Utilisez l’option **Envoyer des commentaires** disponible sur chaque page du Centre d’administration Microsoft 365.
- Envoyez vos commentaires à l’aide du lien **Cette publication est-elle utile ?** pour un incident ou un conseil spécifique.

![Lien « Cette publication est-elle utile ? » pour un incident ou un conseil spécifique](../media/microsoft-365-exchange-monitoring/exhange-monitoring-example-incident-feedback.png)

## <a name="frequently-asked-questions"></a>Foire aux questions

#### <a name="1-why-dont-i-see-exchange-online-monitoring-under-health-in-the-microsoft-365-admin-center"></a>1. Pourquoi la mention « Surveillance Exchange Online » n’apparaît-elle pas dans le Centre d’administration Microsoft 365 ? 

Tout d’abord, vérifiez que vous avez activé le nouveau Centre d’administration sur la page **Accueil** du Centre d’administration Microsoft 365. 

Vérifiez que vous remplissez les deux conditions suivantes : 

- Votre organisation doit avoir un nombre de licences d’au moins 5 000, soit une combinaison de ces produits : Office 365 E3, Microsoft 365 E3, Office 365 E5, Microsoft 365 E5. 
- Votre organisation doit avoir au moins 50 utilisateurs Exchange Online actifs par mois.

Si le nombre de licences de votre organisation est inférieur à 5 000 utilisateurs et que le nombre d’utilisateurs actifs par mois passe au-dessous des 50, la surveillance Exchange Online ne sera pas activée tant que ces conditions ne seront pas remplies.

#### <a name="2-the-active-user-count-in-the-dashboard-for-each-client-appears-to-be-low-we-have-a-lot-of-active-licenses-assigned-to-users-what-does-this-mean"></a>2. Le nombre d’utilisateurs actifs dans le tableau de bord pour chaque client semble faible. Nous avons attribué un grand nombre de licences actives à des utilisateurs. Qu’est-ce que cela signifie ? 

Le nombre d’utilisateurs actifs indiqué dans la surveillance est basé sur une période de 30 minutes au cours de laquelle les utilisateurs ont effectué l’activité indiquée dans la fonctionnalité. Ce nombre est différent des nombres d’utilisations. Pour afficher les nombres d’utilisation, utilisez les rapports d’activité dans le Centre d’administration Microsoft 365 (**Rapports > Utilisation**).

#### <a name="3-will-there-be-other-monitoring-scenarios-for-other-services-such-as-teams-and-sharepoint"></a>3. D’autres scénarios de surveillances seront-ils présents pour d’autres services tels que Teams et SharePoint ? 

Microsoft a intégré cette expérience directement dans le tableau de bord Intégrité des services du Centre d’administration Microsoft 365. Microsoft pourra ainsi étendre les scénarios de surveillance à d’autres services qui figureront dans les prochaines actualités à partager. 

#### <a name="4-what-is-the-plan-for-general-availability-of-this-experience"></a>4. Quelle est l’offre prévue pour la disponibilité générale de cette expérience ? 

Microsoft a intégré la surveillance Exchange Online directement dans le tableau de bord **Intégrité des services** du Centre d’administration Microsoft 365. 

Grâce à cette nouvelle expérience intégrée, Microsoft envisage de recueillir vos commentaires, puis de définir notre offre en faveur de la disponibilité générale.

#### <a name="5-is-this-a-free-included-or-paid-extra-feature"></a>5. Cette fonctionnalité est-elle gratuite (incluse) ou payante (comme supplément) ? 

Cette fonctionnalité est en préversion publique et uniquement disponible pour les clients répondant aux critères de la question 1.

<!--
>[!Note]
>INTERNAL: That decision is pending
>
--> 

#### <a name="6-how-do-i-provide-feedback"></a>6. Comment faire part de mes commentaires ? 

Pour vos commentaires généraux, utilisez l’icône **Envoyer des commentaires** en bas à droite de la page de surveillance **Exchange Online**. 

Pour des commentaires sur les incidents ou les conseils, utilisez le lien **Cette publication est-elle utile ?**.

#### <a name="7-where-is-the-data-instrumented-for-the-scenarios-that-show-activity-trends"></a>7. Où les données sont-elles instrumentées pour les scénarios qui montrent des tendances des activités ?

Les données sont instrumentées dans le service Exchange Online. S’il y a un problème qui se produit avant que la requête n’arrive à Exchange Online ou qu’une erreur s’est produite dans Exchange Online, le signal d’activité s’affiche.
