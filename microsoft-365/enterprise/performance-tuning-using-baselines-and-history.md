---
title: Optimisation des performances d’Office 365 à l’aide de lignes de référence et de l’historique des performances
ms.author: tracyp
author: MSFTTracyP
manager: scotv
ms.date: 07/08/2021
audience: Admin
ms.topic: conceptual
ms.service: microsoft-365-enterprise
ms.localizationpriority: medium
f1.keywords:
- CSH
ms.custom:
- Adm_O365
- seo-marvel-apr2020
search.appverid:
- MET150
- MOE150
- BCS160
ms.assetid: 1492cb94-bd62-43e6-b8d0-2a61ed88ebae
ms.collection:
- M365-security-compliance
- Ent_O365
- SPO_Content
description: Découvrez comment vérifier l’historique des connexions de votre ordinateur client pour vous aider à détecter rapidement les problèmes émergents.
ms.openlocfilehash: 2a4d904fe0b5a09851da5dc83ca238eb70638f9a
ms.sourcegitcommit: 437461fa1d38ff9bb95dd8a1c5f0b94e8111ada2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2022
ms.locfileid: "67670496"
---
# <a name="office-365-performance-tuning-using-baselines-and-performance-history"></a>Optimisation des performances d’Office 365 à l’aide de lignes de référence et de l’historique des performances

Il existe quelques moyens simples de vérifier les performances de connexion entre Office 365 et votre entreprise qui vous permettront d’établir une base de référence approximative de votre connectivité. Connaître l’historique des performances de vos connexions d’ordinateur client peut vous aider à détecter rapidement les problèmes émergents, à identifier et à prédire les problèmes.
  
Si vous n’avez pas l’habitude de travailler sur des problèmes de performances, cet article est conçu pour vous aider à prendre en compte certaines questions courantes. Comment savez-vous que le problème que vous rencontrez est un problème de performances et non un incident de service Office 365 ? Comment pouvez-vous planifier de bonnes performances à long terme ? Comment pouvez-vous garder un œil sur les performances ? Si votre équipe ou vos clients constatent des performances lentes lors de l’utilisation de Office 365 et que vous vous interrogez sur l’une de ces questions, lisez la suite.
  
> [!IMPORTANT]
> **Avez-vous un problème de performances entre votre client et Office 365 en ce moment ?** Suivez les étapes décrites dans le [plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md). 
    
## <a name="something-you-should-know-about-office-365-performance"></a>Quelque chose que vous devez savoir sur Office 365 performances

Office 365 vit à l’intérieur d’un réseau Microsoft dédié et à haute capacité qui est surveillé par l’automatisation et des personnes réelles. Une partie de la maintenance du cloud Office 365 est le réglage des performances et la rationalisation dans la cas où cela est possible. Étant donné que les clients du cloud Office 365 doivent se connecter via Internet, des efforts continus sont nécessaires pour optimiser les performances des services Office 365.

Les améliorations des performances ne s’arrêtent jamais vraiment dans le cloud. Par conséquent, l’expérience de maintien du cloud est saine et rapide. Si vous rencontrez un problème de performances lors de la connexion de votre emplacement à Office 365, il est préférable de ne pas commencer ou d’attendre un cas de support. Au lieu de cela, vous devez commencer à examiner le problème de « l’intérieur ». Autrement dit, commencez à l’intérieur de votre réseau et travaillez pour Office 365. Avant d’ouvrir un cas avec le support technique, vous pouvez collecter des données et prendre des mesures pour explorer et résoudre le problème.
  
> [!IMPORTANT]
> Tenez compte de la planification de la capacité et des limites dans Office 365. Ces informations vous placeront en avance lors de la tentative de résolution d’un problème de performances. Voici un lien vers les [descriptions des services Microsoft 365 et Office 365](/office365/servicedescriptions/office-365-service-descriptions-technet-library). Il s’agit d’un hub central, et tous les services offerts par Office 365 ont un lien vers leurs propres descriptions de service à partir d’ici. Cela signifie que, si vous avez besoin de voir les limites standard pour SharePoint Online, par exemple, vous pouvez cliquer sur [Description du service SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-service-description) et localiser sa [section Limites SharePoint Online](/office365/servicedescriptions/sharepoint-online-service-description/sharepoint-online-limits).
  
Assurez-vous d’aller dans votre résolution des problèmes en comprenant que les performances sont une échelle glissante. Il ne s’agit pas d’atteindre une valeur idéalisée et de la maintenir définitivement. Les tâches occasionnelles à bande passante élevée comme l’intégration d’un grand nombre d’utilisateurs ou l’exécution de migrations de données volumineuses sont stressantes. *Planifiez* donc les impacts sur les performances. Vous devez avoir une idée approximative de vos objectifs de performances, mais de nombreuses variables jouent sur les performances, de sorte que les performances varient.
  
La résolution des problèmes de performances ne concerne pas la réalisation d’objectifs spécifiques et la maintenance indéfinie de ces nombres, mais l’amélioration des activités existantes, compte tenu de toutes les variables. 
  
## <a name="okay-what-does-a-performance-problem-look-like"></a>À quoi ressemble un problème de performances ?

Tout d’abord, vous devez vous assurer que ce que vous rencontrez est effectivement un problème de performances et non un incident de service. Un problème de performances est différent d’un incident de service dans Office 365. Voici comment les distinguer.
  
Les incidents de service se produisent lorsque le service Office 365 lui-même rencontre des problèmes. Vous pouvez voir des icônes rouges ou jaunes sous **Intégrité actuelle** dans le Centre d'administration Microsoft 365. Vous remarquerez peut-être que les performances sur les ordinateurs clients qui se connectent à Office 365 sont lentes. Par exemple, si Current Health signale une icône rouge et que vous voyez **l’examen** en regard d’Exchange, vous pouvez également recevoir des appels de personnes de votre organisation qui se plaignent que les boîtes aux lettres client utilisant Exchange Online sont lentes. Dans ce cas, il est raisonnable de supposer que votre Exchange Online rendement a été victime de problèmes de service.
  
![Tableau de bord Office 365 Health avec toutes les charges de travail en vert, à l’exception d’Exchange, qui affiche service restauré.](../media/ec7f0325-9e61-4e1a-bec0-64b87f4469be.PNG)
  
À ce stade, vous, l’administrateur Office 365, devez vérifier **l’intégrité actuelle**, puis **afficher les détails et l’historique**, souvent, pour rester à jour sur la maintenance sur le système. Le tableau de bord **d’intégrité actuel** a été effectué pour vous mettre à jour sur les modifications apportées au service et les problèmes rencontrés. Les notes et les explications écrites dans l’historique d’intégrité, administrateur à administrateur, sont là pour vous aider à évaluer et à vous tenir informé du travail en cours.
  
![Image du tableau de bord d’intégrité Office 365 expliquant que le service Exchange Online a été restauré et pourquoi.](../media/66609554-426a-4448-8be6-ea09817f41ba.PNG)
  
Un problème de performances n’est pas un incident de service, même si les incidents peuvent entraîner des performances lentes. Un problème de performances se présente comme suit :
  
- Un problème de performances se produit, quel que soit l’état **d’intégrité actuel** du centre d’administration pour le service.
    
-  Un comportement utilisé pour le flux prend beaucoup de temps ou ne se termine jamais.
    
- Vous pouvez également répliquer le problème ou savoir qu’il se produira si vous effectuez la bonne série d’étapes.
    
-  Si le problème est intermittent, il peut toujours y avoir un modèle. Par exemple, vous savez qu’à 10h00, vous aurez des appels d’utilisateurs qui ne peuvent pas toujours accéder à Office 365. Les appels se termineront vers midi.
    
Cette liste semble probablement familière; peut-être trop familier. Une fois que vous savez qu’il s’agit d’un problème de performances, la question se pose : « Que faites-vous ensuite ? » Le reste de cet article vous aide à déterminer exactement cela.
  
## <a name="how-to-define-and-test-the-performance-problem"></a>Comment définir et tester le problème de performances

Les problèmes de performances apparaissent souvent au fil du temps. Il peut donc être difficile de définir le problème réel. Créez une instruction de problème correcte avec une bonne idée du contexte de problème, puis vous devez répéter les étapes de test. Voici quelques exemples d’instructions de problèmes qui ne fournissent pas suffisamment d’informations :
  
- Passer de ma boîte de réception à mon calendrier était quelque chose que je n’ai pas remarqué, et maintenant c’est une pause-café. Pouvez-vous le faire agir comme avant ?
    
- Le chargement de mes fichiers sur SharePoint Online prend une éternité. Pourquoi est-il lent dans l’après-midi, mais n’importe quel autre temps, il est rapide? Ça ne peut pas être rapide ?
    
Les énoncés ci-dessus posent plusieurs grands défis. Plus précisément, trop d’ambiguïtés à gérer. Par exemple :
  
- Il n’est pas clair comment le basculement entre la boîte de réception et le calendrier était utilisé pour agir sur l’ordinateur portable.
    
- Quand l’utilisateur dit « Ne peut-il pas simplement être rapide », qu’est-ce qui est « rapide » ?
    
- Combien de temps est « forever » ? C’est plusieurs secondes ? Ou plusieurs minutes ? Ou l’utilisateur peut-il prendre le déjeuner et l’action se terminerait 10 minutes après son retour ?
    
L’administrateur et l’utilitaire de résolution des problèmes ne peuvent pas connaître *les détails* du problème à partir d’instructions générales comme celles-ci. Par exemple, ils ne savent pas quand le problème a commencé. L’utilitaire de résolution des problèmes peut ne pas savoir que l’utilisateur travaille à domicile et ne voit que le changement lent sur son réseau domestique. Ou que l’utilisateur exécute d’autres applications intensives en RAM sur le client local. Les administrateurs peuvent ne pas savoir que l’utilisateur exécute un système d’exploitation plus ancien ou qu’il n’a pas exécuté de mises à jour récentes.
  
Lorsque les utilisateurs signalent un problème de performances, il y a beaucoup d’informations à collecter. L’obtention et l’enregistrement d’informations s’appellent l’étendue du problème. Voici une liste d’étendue de base que vous pouvez utiliser pour collecter des informations sur les problèmes de performances. Cette liste n’est pas exhaustive, mais c’est un point de départ :
  
- À quelle date le problème s’est-il produit et à quelle heure du jour ou de la nuit?
    
- Quel type d’ordinateur client utilisiez-vous et comment se connectez-vous au réseau d’entreprise (VPN, câblé, sans fil) ?
    
- Travaillez-vous à distance ou étiez-vous au bureau ?
    
- Avez-vous essayé les mêmes actions sur un autre ordinateur et avez-vous vu le même comportement ?
    
- Suivez les étapes qui vous donnent le problème afin de pouvoir écrire les actions que vous effectuez.
    
- Les performances sont-elles lentes en secondes ou en minutes ?
    
- Où vous situez-vous dans le monde ?
    
Certaines de ces questions sont plus évidentes que d’autres. La plupart des utilisateurs comprendront qu’un utilitaire de résolution des problèmes a besoin des étapes exactes pour reproduire le problème. Après tout, comment pouvez-vous enregistrer ce qui ne va pas et comment tester si le problème est résolu ? Les choses moins évidentes sont les suivantes : « Quelle date et quelle heure avez-vous vu le problème ? » et « Où se trouve-t-on dans le monde ? », informations qui peuvent être utilisées en tandem. Selon le moment où l’utilisateur travaillait, quelques heures de décalage horaire peuvent signifier que la maintenance est déjà en cours sur certaines parties du réseau de votre entreprise. Par exemple, votre entreprise dispose d’une implémentation hybride, telle qu’une recherche SharePoint hybride, qui peut interroger des index de recherche dans SharePoint Online et une instance SharePoint Server 2013 locale, des mises à jour peuvent être en cours dans la batterie de serveurs locale. Si votre entreprise se trouve dans le cloud, la maintenance du système peut inclure l’ajout ou la suppression de matériel réseau, le déploiement de mises à jour à l’échelle de l’entreprise ou l’apport de modifications à DNS ou à une autre infrastructure principale.
  
Lorsque vous résolvez un problème de performance, c’est un peu comme une scène de crime, vous devez être précis et observateur pour tirer des conclusions à partir des preuves. Pour ce faire, vous devez obtenir une bonne déclaration de problème en recueillant des preuves. Il doit inclure le contexte de l’ordinateur, le contexte de l’utilisateur, le moment où le problème a commencé et les étapes exactes qui ont exposé le problème de performances. Cette instruction de problème doit être, et rester, la page la plus en haut dans vos notes. En parcourant à nouveau la déclaration du problème après avoir résolu le problème, vous effectuez les étapes nécessaires pour tester et prouver si les actions que vous effectuez ont résolu le problème. C’est essentiel pour savoir quand votre travail, là, est terminé.
  
## <a name="do-you-know-how-performance-used-to-look-when-it-was-good"></a>Savez-vous à quoi ressemblent les performances quand elles étaient bonnes ?

Si tu n’es pas chanceux, personne ne le sait. Personne n’avait de chiffres. Cela signifie que personne ne peut répondre à la question simple « Combien de secondes a-t-il fallu pour mettre en place une boîte de réception dans Office 365 ? », ou « Combien de temps prenait-il lorsque les cadres avaient une réunion Lync Online ? », ce qui est un scénario courant pour de nombreuses entreprises.
  
Qu’est-ce qui manque ici est une base de référence des performances ?
  
Les lignes de base vous donnent un contexte pour vos performances. Vous devez prendre une base de référence occasionnellement à fréquemment, en fonction des besoins de votre entreprise. Si vous êtes une grande entreprise, votre équipe des opérations peut déjà prendre des bases de référence pour votre environnement local. Par exemple, si vous corrigez tous les serveurs Exchange le premier lundi du mois et tous vos serveurs SharePoint le troisième lundi, votre équipe Des opérations a probablement une liste de tâches et de scénarios qu’elle exécute après la mise à jour corrective, pour prouver que les fonctions critiques sont opérationnelles. Par exemple, ouvrir la boîte de réception, cliquer sur Envoyer/Recevoir et vérifier que les dossiers sont mis à jour, ou, dans SharePoint, parcourir la page principale du site, accéder à la page de recherche d’entreprise et effectuer une recherche qui retourne des résultats.
  
Si vos applications sont dans Office 365, certaines des bases de référence les plus fondamentales, vous pouvez prendre la mesure du temps (en millisecondes) d’un ordinateur client à l’intérieur de votre réseau, à un point de sortie, ou au point où vous quittez votre réseau et sortez vers Office 365. Voici quelques lignes de base utiles que vous pouvez examiner et enregistrer :
  
- Identifiez les appareils entre votre ordinateur client et votre point de sortie, par exemple, votre serveur proxy.
    
  - Vous devez connaître vos appareils afin d’avoir un contexte (adresses IP, type d’appareil, etc.) pour les problèmes de performances qui surviennent.
    
  - Les serveurs proxy étant des points de sortie courants, vous pouvez vérifier votre navigateur web pour voir le serveur proxy qu’il doit utiliser, le cas échéant.
    
  - Il existe des outils tiers qui peuvent découvrir et mapper votre réseau, mais le moyen le plus sûr de connaître vos appareils consiste à demander à un membre de votre équipe réseau.
    
- Identifiez votre fournisseur de services Internet (ISP), notez leurs informations de contact et demandez le nombre de circuits de bande passante dont vous disposez.
    
- Au sein de votre entreprise, identifiez les ressources pour les appareils entre votre client et le point de sortie, ou identifiez un contact d’urgence pour parler des problèmes de mise en réseau.
    
Voici quelques lignes de base que les tests simples avec des outils peuvent calculer pour vous :
  
- Temps entre votre ordinateur client et votre point de sortie en millisecondes
    
- Le temps de votre sortie pointe vers Office 365 en millisecondes
    
- Emplacement dans le monde du serveur qui résout les URL de Office 365 lorsque vous parcourez
    
- Vitesse de résolution DNS de votre fournisseur de services Internet en millisecondes, incohérences dans l’arrivée des paquets (gigue réseau), temps de chargement et de téléchargement en millisecondes
    
Si vous n’êtes pas familiarisé avec la façon d’effectuer ces étapes, nous allons entrer plus en détail dans cet article. 
  
## <a name="what-is-a-baseline"></a>Qu’est-ce qu’une ligne de base ?

Vous connaîtrez l’impact quand il se passe mal, mais si vous ne connaissez pas vos données de performances historiques, il n’est pas possible d’avoir un contexte pour la façon dont il peut être devenu mauvais, et quand. Donc, sans ligne de base, il vous manque l’indice clé pour résoudre le puzzle: l’image sur la boîte de puzzle. Dans la résolution des problèmes de performances, vous avez besoin d’un point de  *comparaison*. Les lignes de base de performances simples ne sont pas difficiles à prendre. Votre équipe des opérations peut être chargée d’effectuer ces opérations selon un calendrier. Par exemple, supposons que votre connexion ressemble à ceci : 
  
![Graphique réseau de base montrant le client, le proxy et le cloud Office 365.](../media/c6ca7140-09f9-4c2d-a775-dbf2820eaa0c.PNG)
  
Cela signifie que vous avez vérifié auprès de votre équipe réseau et découvert que vous quittez votre entreprise pour Internet via un serveur proxy, et que le proxy gère toutes les demandes que votre ordinateur client envoie au cloud. Dans ce cas, vous devez dessiner une version simplifiée de votre connexion qui répertorie tous les appareils intervenants. À présent, insérez des outils que vous pouvez utiliser pour tester les performances entre le client, le point de sortie (où vous quittez votre réseau pour Internet) et le cloud Office 365.
  
![Réseau de base avec client, proxy et cloud, et suggestions d’outils PSPing, TraceTCP et traces réseau.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
Les options sont répertoriées comme **simples** et **avancées** en raison de la quantité d’expertise dont vous avez besoin pour trouver les données de performances. Une trace réseau prend beaucoup de temps, par rapport à l’exécution d’outils en ligne de commande tels que PsPing et TraceTCP. Ces deux outils en ligne de commande ont été choisis parce qu’ils n’utilisent pas de paquets ICMP, qui seront bloqués par Office 365, et parce qu’ils donnent le temps en millisecondes nécessaire pour quitter l’ordinateur client ou le serveur proxy (si vous avez accès) et arrivent à Office 365. Chaque saut individuel d’un ordinateur à l’autre se retrouvera avec une valeur de temps, et c’est parfait pour les lignes de base! Tout aussi important, ces outils en ligne de commande vous permettent d’ajouter un numéro de port à la commande, ce qui est utile, car Office 365 communique via le port 443, qui est le port utilisé par SSL (Secure Sockets Layer and Transport Layer Security) (SSL et TLS). Toutefois, d’autres outils tiers peuvent être de meilleures solutions pour votre situation. Microsoft ne prend pas en charge tous ces outils. Par conséquent, si, pour une raison quelconque, vous ne pouvez pas faire fonctionner PsPing et TraceTCP, passez à une trace réseau avec un outil comme Netmon. 
  
Vous pouvez prendre une ligne de base avant les heures de bureau, de nouveau pendant une utilisation intensive, puis de nouveau après les heures. Cela signifie que vous pouvez avoir une structure de dossiers qui ressemble un peu à ceci à la fin :
  
![Graphique proposant un moyen d’organiser vos données de performances dans des dossiers.](../media/13e01ffa-f0f2-4d10-b89d-d5980ec89fae.png)
  
Vous devez également choisir une convention de nommage de vos fichiers. Voici quelques exemples :
  
- Feb_09_2015_9amPST_PerfBaseline_Netmon_ClientToEgress_Normal
    
- Jan_10_2015_3pmCST_PerfBaseline_PsPing_ClientToO365_bypassProxy_SLOW
    
- Feb_08_2015_2pmEST_PerfBaseline_BADPerf
    
- Feb_08_2015_8-30amEST_PerfBaseline_GoodPerf
    
Il existe de nombreuses façons de procéder, mais l’utilisation du format **\<dateTime\>\<what's happening in the test\>** est un bon point de départ. Être diligent à ce sujet aidera beaucoup quand vous essayez de résoudre les problèmes plus tard. Plus tard, vous pourrez dire : « J’ai pris deux traces le 8 février, l’une a montré de bonnes performances et l’autre a été mauvaise, afin que nous puissions les comparer ». Cela est utile pour la résolution des problèmes. 
  
Vous devez disposer d’un moyen organisé pour conserver vos bases de référence historiques. Dans cet exemple, les méthodes simples ont produit trois sorties de ligne de commande et les résultats ont été collectés sous forme de captures d’écran, mais vous pouvez avoir des fichiers de capture réseau à la place. Utilisez la méthode qui vous convient le mieux. Stockez vos bases de référence historiques et faites-les référence aux points où vous remarquez des modifications dans le comportement de services en ligne. 
  
## <a name="why-collect-performance-data-during-a-pilot"></a>Pourquoi collecter des données de performances pendant un pilote ?

Il n’y a pas de meilleur moment pour commencer à créer des lignes de base que pendant un pilote du service Office 365. Votre bureau peut avoir des milliers d’utilisateurs, des centaines de milliers, ou il peut en avoir cinq, mais même avec quelques utilisateurs, vous pouvez effectuer des tests pour mesurer les fluctuations des performances. Dans le cas d’une grande entreprise, un échantillon représentatif de plusieurs centaines d’utilisateurs qui pilotent des Office 365 peut être projeté vers plusieurs milliers afin de savoir où des problèmes peuvent survenir avant qu’ils ne se produisent.
  
Dans le cas d’une petite entreprise, où l’intégration signifie que tous les utilisateurs se rendent au service en même temps et qu’il n’y a pas de pilote, conservez des mesures de performances afin que vous ayez des données à montrer à toute personne susceptible d’avoir à résoudre les problèmes d’une opération mal exécutée. Par exemple, si vous remarquez que tout d’un coup, vous pouvez parcourir votre bâtiment dans le temps nécessaire pour charger un graphique de taille moyenne où il se produisait rapidement.
  
## <a name="how-to-collect-baselines"></a>Comment collecter des bases de référence

Pour tous les plans de dépannage, vous devez identifier ces éléments au minimum :
  
- L’ordinateur client que vous utilisez (le type d’ordinateur ou d’appareil, une adresse IP et les actions à l’origine du problème)
    
- Emplacement de l’ordinateur client dans le monde (par exemple, si cet utilisateur sur un VPN vers le réseau, travaille à distance ou sur l’intranet de l’entreprise)
    
- Point de sortie utilisé par l’ordinateur client à partir de votre réseau (point auquel le trafic quitte votre entreprise pour un fournisseur de services Internet ou Internet)
    
 Vous pouvez trouver la disposition de votre réseau auprès de l’administrateur réseau. Si vous êtes sur un petit réseau, examinez les appareils qui vous connectent à Internet et appelez votre fournisseur de services Internet si vous avez des questions sur la disposition. Créez un graphique de la disposition finale pour votre référence. 
  
Cette section est divisée en outils et méthodes en ligne de commande simples, et en options d’outils plus avancées. Nous aborderons d’abord les méthodes simples. Toutefois, si vous rencontrez un problème de performances en ce moment, vous devez passer aux méthodes avancées et essayer l’exemple de plan d’action de résolution des problèmes de performances.
  
### <a name="simple-methods"></a>Méthodes simples

L’objectif de ces méthodes simples est d’apprendre à prendre, comprendre et stocker correctement des bases de référence de performances simples au fil du temps afin d’être informé de Office 365 performances. Voici le diagramme simple pour des raisons simples, comme vous l’avez vu précédemment :
  
![Réseau de base avec client, proxy et cloud, et suggestions d’outils PSPing, TraceTCP et traces réseau.](../media/627bfb77-abf7-4ef1-bbe8-7f8cbe48e1d2.png)
  
> [!NOTE]
> TraceTCP est inclus dans cette capture d’écran, car il s’agit d’un outil utile pour afficher, en millisecondes, le temps nécessaire au traitement d’une demande et le nombre de tronçons réseau, ou connexions d’un ordinateur à l’autre, que la demande prend pour atteindre une destination. TraceTCP peut également donner les noms des serveurs utilisés pendant les tronçons, ce qui peut être utile pour un Microsoft Office 365 dépannage dans support. > commandes TraceTCP peuvent être très simples, par exemple : >  `tracetcp.exe outlook.office365.com:443`> N’oubliez pas d’inclure le numéro de port dans la commande ! > [TraceTCP](https://simulatedsimian.github.io/tracetcp_download.html) est un téléchargement gratuit, mais s’appuie sur Wincap. Wincap est un outil qui est également utilisé et installé par Netmon. Nous utilisons également Netmon dans la section Méthodes avancées. 
  
 Si vous avez plusieurs bureaux, vous devez également conserver un ensemble de données à partir d’un client dans chacun de ces emplacements. Ce test mesure la latence, qui, dans ce cas, est une valeur numérique qui décrit la durée entre un client qui envoie une demande à Office 365 et Office 365 répondre à la demande. Les tests proviennent de votre domaine sur un ordinateur client et cherchent à mesurer un aller-retour à partir de votre réseau, à travers un point de sortie, à travers Internet pour Office 365 et retour. 
  
Il existe plusieurs façons de gérer le point de sortie, dans ce cas, le serveur proxy. Vous pouvez tracer de 1 à 2, puis de 2 à 3, puis ajouter les nombres en millisecondes pour obtenir un total final à la périphérie de votre réseau. Vous pouvez également configurer la connexion pour contourner le proxy pour Office 365 adresses. Dans un réseau plus grand avec un pare-feu, un proxy inverse ou une combinaison des deux, vous devrez peut-être effectuer des exceptions sur le serveur proxy qui permettront au trafic de passer un grand nombre d’URL. Pour obtenir la liste des points de terminaison utilisés par Office 365, consultez [Office 365 URL et plages d’adresses IP](https://support.office.com/article/8548a211-3fe7-47cb-abb1-355ea5aa88a2). Si vous disposez d’un proxy d’authentification, commencez par tester les exceptions pour les éléments suivants :
  
- Ports 80 et 443
    
- TCP et HTTPs
    
- Connexions sortantes vers l’une de ces URL :
    
- \*.microsoftonline.com
    
- \*.microsoftonline-p.com
    
- \*.sharepoint.com
    
- \*.outlook.com
    
- \*.lync.com
    
- osub.microsoft.com
    
Tous les utilisateurs doivent être autorisés à accéder à ces adresses sans interférence de proxy ni authentification. Sur un réseau plus petit, vous devez les ajouter à votre liste de contournement de proxy dans votre navigateur web. 
  
Pour les ajouter à votre liste de contournement de proxy dans Internet Explorer, accédez à **Outils** \> **Internet Options** \> **Connections** \> **LAN settings** \> **Advanced**. L’onglet Avancé est également l’endroit où vous trouverez votre serveur proxy et le port du serveur proxy. Vous devrez peut-être cliquer sur la case à cocher **Utiliser un serveur proxy pour votre réseau** local pour accéder au bouton **Avancé** . Vous devez vous assurer que **le serveur proxy de contournement pour les adresses locales** est vérifié. Une fois que vous avez cliqué sur **Avancé**, vous verrez une zone de texte dans laquelle vous pouvez entrer des exceptions. Séparez les URL génériques répertoriées ci-dessus par des points-virgules, par exemple :
  
\*.microsoftonline.com; \*.sharepoint.com
  
Une fois que vous avez contourné votre proxy, vous devez être en mesure d’utiliser ping ou PsPing directement sur une URL de Office 365. L’étape suivante consiste à tester les **outlook.office365.com** ping. Ou, si vous utilisez PsPing ou un autre outil qui vous permet de fournir un numéro de port à la commande, PsPing par **rapport à portal.microsoftonline.com:443** pour voir le temps aller-retour moyen en millisecondes. 
  
Le temps aller-retour, ou RTT, est une valeur numérique qui mesure le temps nécessaire pour envoyer une requête HTTP à un serveur comme outlook.office365.com et obtenir une réponse qui reconnaît que le serveur sait que vous l’avez fait. Vous verrez parfois cet abréviation comme RTT. Ce délai doit être relativement court.
  
Pour effectuer ce test, vous devez utiliser [PSPing](/sysinternals/downloads/psping) ou un autre outil qui n’utilise pas de paquets ICMP bloqués par Office 365. 
  
 **Comment utiliser PsPing pour obtenir un temps aller-retour global en millisecondes directement à partir d’une URL Office 365**
  
1. Exécutez une invite de commandes avec élévation de privilèges en effectuant les étapes suivantes :
    
1. Cliquez sur **Démarrer**.
    
2. Dans la zone **Démarrer la recherche, tapez** cmd, puis appuyez sur Ctrl+Maj+Entrée.
    
3. Si la boîte de dialogue **Contrôle de compte d'utilisateur** apparaît, confirmez que l'action affichée est celle que vous souhaitez, puis cliquez sur **Continue** r.
    
2. Accédez au dossier dans lequel l’outil (dans ce cas, PsPing) est installé et testez ces URL Office 365 :
    
  - psping admin.microsoft.com:443
    
  - psping microsoft-my.sharepoint.com:443
    
  - psping outlook.office365.com:443
    
  - psping www.yammer.com:443
    
    ![La commande PSPing va microsoft-my.sharepoint.com port 443.](../media/3258f620-4513-4e82-95c9-06b387fc3a82.PNG)
  
Veillez à inclure le numéro de port 443. N’oubliez pas que Office 365 fonctionne sur un canal chiffré. Si vous utilisez PsPing sans le numéro de port, votre demande échoue. Une fois que vous avez effectué un test ping sur votre liste courte, recherchez la durée moyenne en millisecondes (ms). C’est ce que vous voulez enregistrer!
  
![Graphique montrant une illustration du client au proxy PSPing avec un temps aller-retour de 2,8 millisecondes.](../media/96901aea-1093-4f1b-b5a3-6078e9035e6c.png)
  
Si vous n’êtes pas familiarisé avec le contournement du proxy et que vous préférez effectuer les opérations pas à pas, vous devez d’abord connaître le nom de votre serveur proxy. Dans Internet Explorer, accédez à **Outils** \> **Internet Options** \> **Connections** \> **LAN settings** \> **Advanced**. L’onglet **Avancé** est l’endroit où votre serveur proxy apparaît. Effectuez un test ping sur ce serveur proxy à l’invite de commandes en effectuant cette tâche : 
  
 **Pour effectuer un test ping sur le serveur proxy et obtenir une valeur aller-retour en millisecondes pour la phase 1 à 2**
  
1. Exécutez une invite de commandes avec élévation de privilèges en effectuant les étapes suivantes :
    
1. Cliquez sur **Démarrer**.
    
2. Dans la zone **Démarrer la recherche, tapez** cmd, puis appuyez sur Ctrl+Maj+Entrée.
    
3. Si la boîte de dialogue **Contrôle de compte d'utilisateur** apparaît, confirmez que l'action affichée est celle que vous souhaitez, puis cliquez sur **Continue** r.
    
2. Tapez ping \<the name of the proxy server your browser uses, or the IP address of the proxy server\> , puis appuyez sur Entrée. Si vous avez installé PsPing ou un autre outil, vous pouvez choisir d’utiliser cet outil à la place. 
    
    Votre commande peut ressembler à l’un des exemples suivants : 
    
  - ping ourproxy.ourdomain.industry.business.com
    
  - ping 155.55.121.55
    
  - ping ourproxy
    
  - psping ourproxy.ourdomain.industry.business.com:80
    
  - psping 155.55.121.55:80
    
  - psping ourproxy:80
    
3. Lorsque la trace cesse d’envoyer des paquets de test, vous obtenez un petit résumé qui répertorie une moyenne, en millisecondes, et c’est la valeur que vous cherchez. Prenez une capture d’écran de l’invite et enregistrez-la à l’aide de votre convention d’affectation de noms. À ce stade, il peut également aider à remplir le diagramme avec la valeur.
    
Vous avez peut-être pris une trace tôt le matin, et votre client peut accéder rapidement au proxy (ou à tout autre serveur de sortie qui quitte Internet). Dans ce cas, vos nombres peuvent ressembler à ceci :
  
![Graphique qui montre l’heure aller-retour d’un client à un proxy de 2,8 millisecondes.](../media/1bd03544-23fc-47d4-bbae-c1feb466a5d8.PNG)
  
Si votre ordinateur client est l’un des rares à avoir accès au serveur proxy (ou sortant), vous pouvez exécuter la prochaine étape du test en vous connectant à distance à cet ordinateur, en exécutant l’invite de commandes sur PsPing à une URL Office 365 à partir de là. Si vous n’avez pas accès à cet ordinateur, vous pouvez contacter vos ressources réseau pour obtenir de l’aide sur la prochaine étape et obtenir des numéros exacts de cette façon. Si ce n’est pas possible, prenez un PsPing par rapport à l’URL Office 365 en question et comparez-la au temps PsPing ou Ping sur votre serveur proxy. 
  
Par exemple, si vous avez 51,84 millisecondes entre le client et l’URL Office 365 et que vous avez 2,8 millisecondes entre le client et le proxy (ou le point de sortie), vous avez 49,04 millisecondes de la sortie vers Office 365. De même, si vous avez une PsPing de 12,25 millisecondes entre le client et le proxy pendant la hauteur de la journée et 62,01 millisecondes entre le client et l’URL Office 365, votre valeur moyenne pour la sortie du proxy vers l’URL Office 365 est de 49,76 millisecondes.
  
![Graphique supplémentaire qui montre le ping en millisecondes du client au proxy à côté du client pour Office 365 afin que les valeurs puissent être soustraites.](../media/cd764e77-5154-44ba-a5cd-443a628eb2d9.PNG)
  
Pour ce qui est de la résolution des problèmes, il se peut que vous trouviez quelque chose d’intéressant simplement en conservant ces lignes de base. Par exemple, si vous constatez que vous avez généralement entre 40 millisecondes et 59 millisecondes de latence entre le proxy ou le point de sortie vers l’URL Office 365 et que vous avez un client vers proxy ou une latence de point de sortie d’environ 3 millisecondes à 7 millisecondes (en fonction de la quantité de trafic réseau que vous voyez pendant cette période de la journée), vous saurez sûrement que quelque chose est problématique si vos trois dernières lignes de base de proxy ou de sortie montrent latence de 45 millisecondes.
  
### <a name="advanced-methods"></a>Méthodes avancées

Si vous voulez vraiment savoir ce qui se passe avec vos demandes Internet à Office 365, vous devez vous familiariser avec les traces réseau. Peu importe les outils que vous préférez pour ces traces, HTTPWatch, Netmon, Message Analyzer, Wireshark, Fiddler, l’outil Tableau de bord du développeur ou tout autre outil le fera tant que cet outil peut capturer et filtrer le trafic réseau. Vous verrez dans cette section qu’il est utile d’exécuter plusieurs de ces outils pour obtenir une image plus complète du problème. Lorsque vous effectuez des tests, certains de ces outils agissent également en tant que proxys à part entière. Les outils utilisés dans l’article complémentaire, [plan de résolution des problèmes de performances pour Office 365](performance-troubleshooting-plan.md), incluent [Netmon 3.4](https://www.microsoft.com/download/details.aspx?id=4865), [HTTPWatch](https://www.httpwatch.com/download/) ou [WireShark](https://www.wireshark.org/).
  
L’exécution d’une ligne de base de performances est la partie la plus simple de cette méthode, et la plupart des étapes sont les mêmes que lorsque vous résolvez un problème de performances. Les méthodes plus avancées de création de lignes de base pour les performances nécessitent que vous preniez et stockiez des traces réseau. La plupart des exemples de cet article utilisent SharePoint Online, mais vous devez développer une liste d’actions courantes dans les services Office 365 auxquels vous vous abonnez pour tester et enregistrer. Voici un exemple de base de référence :
  
- Liste de référence pour l’objet SPO - ** Étape 1 : ** Parcourez la page d’accueil du site web SPO et effectuez une trace réseau. Enregistrez la trace. 
    
- Liste de référence pour l’objet SPO - **Étape 2 :** recherchez un terme (par exemple, le nom de votre entreprise) via La recherche d’entreprise et effectuez une trace réseau. Enregistrez la trace. 
    
- Liste de référence pour l’objet SPO - **Étape 3 :** charger un fichier volumineux dans une bibliothèque de documents SharePoint Online et effectuer une trace réseau. Enregistrez la trace. 
    
- Liste de référence pour l’objet SPO - **Étape 4 :** parcourir la page d’accueil du site web OneDrive et effectuer une trace réseau. Enregistrez la trace. 
    
Cette liste doit inclure les actions courantes les plus importantes que les utilisateurs prennent contre SharePoint Online. Notez que la dernière étape, à suivre en allant à OneDrive Entreprise, génère une comparaison entre la charge de la page d’accueil SharePoint Online (qui est souvent personnalisée par les entreprises) et OneDrive Entreprise page d’accueil, qui est rarement personnalisée. Il s’agit d’un test de base lorsqu’il s’agit d’un site SharePoint Online à chargement lent. Vous pouvez créer un enregistrement de cette différence dans vos tests.
  
Si vous êtes au milieu d’un problème de performances, la plupart des étapes sont les mêmes que lorsque vous effectuez une ligne de base. Les traces réseau deviennent critiques. Nous allons donc gérer la  *façon*  de suivre les traces importantes. 
  
Pour résoudre un problème de performances, pour le  *moment*, vous devez effectuer une trace au moment où vous rencontrez le problème de performances. Vous devez disposer des outils appropriés pour collecter les journaux d’activité, et vous avez besoin d’un plan d’action, c’est-à-dire d’une liste des actions de dépannage à entreprendre pour recueillir les meilleures informations possibles. La première chose à faire est d’enregistrer la date et l’heure du test afin que les fichiers puissent être enregistrés dans un dossier qui reflète le minutage. Ensuite, réduisez les étapes du problème elles-mêmes. Voici les étapes exactes que vous allez utiliser pour le test. N’oubliez pas les principes de base : si le problème concerne uniquement Outlook, veillez à enregistrer que le comportement du problème se produit dans un seul service Office 365. La réduction de l’étendue de ce problème vous aidera à vous concentrer sur quelque chose que vous pouvez résoudre. 
  
## <a name="see-also"></a>Voir aussi

[Gestion des points de terminaison Office 365](https://support.office.com/article/99cab9d4-ef59-4207-9f2b-3728eb46bf9a)