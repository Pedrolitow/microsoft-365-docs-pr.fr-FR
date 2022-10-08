---
title: Considérations et forum aux questions sur le déploiement de la formation de simulation d’attaque
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: ITPro
ms.topic: how-to
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.assetid: ''
ms.collection: m365-security
ms.custom:
- seo-marvel-apr2020
description: Les administrateurs peuvent en savoir plus sur les considérations relatives au déploiement et poser fréquemment des questions sur la simulation d’attaque et la formation dans les organisations Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2.
ms.subservice: mdo
ms.service: microsoft-365-security
ms.openlocfilehash: 75dfa3281785dc06906ed66384e63d3867f617b2
ms.sourcegitcommit: 12af9e8e3a6eaa090fda9e98ccb831dff65863a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/27/2022
ms.locfileid: "68088704"
---
# <a name="attack-simulation-training-deployment-considerations-and-faq"></a>Considérations et forum aux questions sur le déploiement de la formation de simulation d’attaque

[!INCLUDE [MDO Trial banner](../includes/mdo-trial-banner.md)]

**S’applique à**
- [Microsoft Defender pour Office 365 Plan 2](defender-for-office-365.md)

Exercice de simulation d'attaque permet aux organisations Microsoft 365 E5 ou Microsoft Defender pour Office 365 Plan 2 de mesurer et de gérer les risques d’ingénierie sociale en autorisant la création et la gestion de simulations de hameçonnage alimentées par le monde réel, charges utiles d’hameçonnage d’armes. La formation hyper-ciblée, dispensée en partenariat avec la sécurité Terranova, permet d’améliorer les connaissances et de modifier le comportement des employés.

Pour plus d’informations sur la prise en main de Exercice de simulation d'attaque, consultez [Prise en main de Exercice de simulation d'attaque](attack-simulation-training-get-started.md).

Bien que toute l’expérience de création et de planification de simulation ait été conçue pour être fluide et sans friction, l’exécution de simulations à l’échelle de l’entreprise nécessite souvent une planification. Cet article aide à relever des défis spécifiques que nous voyons lorsque nos clients exécutent des simulations dans leurs propres environnements.

## <a name="issues-with-end-user-experiences"></a>Problèmes liés aux expériences des utilisateurs finaux

### <a name="phishing-simulation-urls-blocked-by-google-safe-browsing"></a>URL de simulation d’hameçonnage bloquées par Google Safe Browsing

Un service de réputation d’URL peut identifier une ou plusieurs URL utilisées par Exercice de simulation d'attaque comme non sécurisées. Google Safe Browsing dans Google Chrome bloque certaines DES URL de hameçonnage simulées avec un **message de site trompeur** . Bien que nous travaillions avec de nombreux fournisseurs de réputation d’URL pour toujours autoriser nos URL de simulation, nous n’avons pas toujours une couverture complète.

:::image type="content" source="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png" alt-text="Avertissement du site trompeur dans Google Chrome" lightbox="../../media/attack-sim-training-faq-chrome-deceptive-site-message.png":::

Notez que ce problème n’affecte pas Microsoft Edge.

Dans le cadre de la phase de planification, veillez à vérifier la disponibilité de l’URL dans vos navigateurs web pris en charge avant d’utiliser l’URL dans une campagne de hameçonnage. Si les URL sont bloquées par Google Safe Browsing, [suivez ces instructions](https://support.google.com/chrome/a/answer/7532419) de Google pour autoriser l’accès aux URL.

[Reportez-vous à La](attack-simulation-training-get-started.md) prise en main de Exercice de simulation d'attaque pour obtenir la liste des URL actuellement utilisées par Exercice de simulation d'attaque.

### <a name="phishing-simulation-and-admin-urls-blocked-by-network-proxy-solutions-and-filter-drivers"></a>Simulation d’hameçonnage et URL d’administrateur bloquées par des solutions de proxy réseau et des pilotes de filtre

Les URL de simulation d’hameçonnage et les URL d’administrateur peuvent être bloquées ou supprimées par vos filtres ou appareils de sécurité intermédiaires. Par exemple :

- Pare-feu
- solutions Web Application Firewall (WAF)
- Pilotes de filtre tiers (par exemple, filtres en mode noyau)

Bien que nous ayons vu peu de clients bloqués à cette couche, cela se produit. Si vous rencontrez des problèmes, envisagez de configurer les URL suivantes pour contourner l’analyse par vos appareils de sécurité ou filtres en fonction des besoins :

- URL de hameçonnage simulées, comme décrit dans [Prise en main à l’aide de Exercice de simulation d'attaque](attack-simulation-training-get-started.md).
- <https://security.microsoft.com/attacksimulator>
- <https://security.microsoft.com/attacksimulationreport>
- <https://security.microsoft.com/trainingassignments>

### <a name="simulation-messages-not-delivered-to-all-targeted-users"></a>Messages de simulation non remis à tous les utilisateurs ciblés

Il est possible que le nombre d’utilisateurs qui reçoivent réellement les messages électroniques de simulation soit inférieur au nombre d’utilisateurs ciblés par la simulation. Les types d’utilisateurs suivants seront exclus dans le cadre de la validation cible :

- Adresses e-mail de destinataire non valides.
- Utilisateurs invités.
- Utilisateurs qui ne sont plus actifs dans Azure Active Directory (Azure AD).

Seuls les utilisateurs valides et non invités avec une boîte aux lettres valide seront inclus dans les simulations. Si vous utilisez des groupes de distribution ou des groupes de sécurité à extension messagerie pour cibler des utilisateurs, vous pouvez utiliser l’applet de commande [Get-DistributionGroupMember](/powershell/module/exchange/get-distributiongroupmember) dans [Exchange Online PowerShell](/powershell/exchange/connect-to-exchange-online-powershell) pour afficher et valider les membres du groupe de distribution.

## <a name="issues-with-attack-simulation-training-reporting"></a>Problèmes liés à la création de rapports Exercice de simulation d'attaque

### <a name="attack-simulation-training-reports-do-not-contain-any-activity-details"></a>Exercice de simulation d'attaque rapports ne contiennent aucun détail d’activité

Exercice de simulation d'attaque est fourni avec des insights riches et exploitables qui vous tiennent informé de la progression de la préparation aux menaces de vos employés. Si Exercice de simulation d'attaque rapports ne sont pas renseignés avec des données, vérifiez que la recherche dans le journal d’audit est activée dans votre organisation (elle est activée par défaut).

La recherche dans le journal d’audit est requise par Exercice de simulation d'attaque afin que les événements puissent être capturés, enregistrés et lus. La désactivation de la recherche dans les journaux d’audit a les conséquences suivantes pour Exercice de simulation d'attaque :

- Les données de création de rapports ne sont pas disponibles dans tous les rapports. Les rapports s’affichent vides.
- Les affectations d’entraînement sont bloquées, car les données ne sont pas disponibles.

Pour activer ou désactiver la recherche dans le journal d’audit, consultez [Activer ou désactiver la recherche de journal d’audit](../../compliance/turn-audit-log-search-on-or-off.md).

> [!NOTE]
> Les détails de l’activité vide peuvent également être causés par l’absence de licences E5 attribuées aux utilisateurs. Vérifiez qu’au moins une licence E5 est affectée à un utilisateur actif pour vous assurer que les événements de création de rapports sont capturés et enregistrés.

### <a name="simulation-reports-are-not-updated-immediately"></a>Les rapports de simulation ne sont pas mis à jour immédiatement

Les rapports de simulation détaillés ne sont pas mis à jour immédiatement après le lancement d’une campagne. Ne vous inquiétez pas; ce comportement est attendu.

Chaque campagne de simulation a un cycle de vie. Lors de la première création, la simulation est dans l’état **Planifié** . Lorsque la simulation démarre, elle passe à l’état **en cours** . Une fois l’opération terminée, la simulation passe à l’état **Terminé** .

Bien qu’une simulation soit dans l’état **Planifié** , les rapports de simulation sont principalement vides. Au cours de cette étape, le moteur de simulation résout les adresses e-mail des utilisateurs cibles, étend les groupes de distribution, supprime les utilisateurs invités de la liste, etc. :

:::image type="content" source="../../media/attack-sim-training-faq-scheduled-state.png" alt-text="Détails de la simulation montrant la simulation dans l’état Planifié" lightbox="../../media/attack-sim-training-faq-scheduled-state.png":::

Une fois la simulation entrée dans l’étape **En cours** , vous remarquerez que des informations commencent à s’introduire dans la création de rapports :

:::image type="content" source="../../media/attack-sim-training-faq-in-progress-state.png" alt-text="Détails de la simulation montrant la simulation dans l’état en cours" lightbox="../../media/attack-sim-training-faq-in-progress-state.png":::

La mise à jour des rapports de simulation individuels peut prendre jusqu’à 30 minutes après la transition vers l’état **En cours** . Les données de rapport continuent de se générer jusqu’à ce que la simulation atteigne l’état **Terminé** . Les mises à jour de rapports se produisent aux intervalles suivants :

- Toutes les 10 minutes pendant les 60 premières minutes.
- Toutes les 15 minutes après 60 minutes jusqu’à 2 jours.
- Toutes les 30 minutes après 2 jours jusqu’à 7 jours.
- Toutes les 60 minutes après 7 jours.

Les widgets de la page **Vue d’ensemble** fournissent un instantané rapide de la posture de sécurité basée sur la simulation de votre organisation au fil du temps. Étant donné que ces widgets reflètent votre posture de sécurité globale et votre parcours au fil du temps, ils sont mis à jour une fois chaque campagne de simulation terminée.

> [!NOTE]
> Vous pouvez utiliser l’option **Exporter** sur les différentes pages de création de rapports pour extraire des données.

### <a name="messages-reported-as-phishing-by-users-arent-appearing-in-simulation-reports"></a>Les messages signalés comme hameçonnage par les utilisateurs n’apparaissent pas dans les rapports de simulation

Les rapports de simulation dans l’entraînement du simulateur d’attaque fournissent des détails sur l’activité des utilisateurs. Par exemple :

- Utilisateurs qui ont cliqué sur le lien dans le message.
- Utilisateurs qui ont abandonné leurs informations d’identification.
- Utilisateurs qui ont signalé le message comme hameçonnage.

Si les messages signalés par les utilisateurs comme hameçonnage ne sont pas capturés dans Exercice de simulation d'attaque rapports de simulation, il peut y avoir une règle de flux de messagerie Exchange (également appelée règle de transport) qui bloque la remise des messages signalés à Microsoft. Vérifiez que les règles de flux de courrier ne bloquent pas la remise aux adresses de messagerie suivantes :

- junk@office365.microsoft.com
- abuse@messaging.microsoft.com
- phish@office365.microsoft.com
- pas\_junk@office365.microsoft.com

### <a name="users-are-assigned-training-after-they-report-a-simulated-message"></a>L’entraînement est attribué aux utilisateurs après qu’ils signalent un message simulé

Si une formation est attribuée aux utilisateurs après avoir déclaré un message de simulation d’hameçonnage, vérifiez si votre organisation dispose d’une **boîte aux lettres personnalisée** configurée dans votre **stratégie de soumission d’utilisateur**. Lors de la configuration d’une **boîte aux lettres personnalisée**, cette boîte aux lettres doit être exclue des stratégies Liens sécurisés et Pièces jointes sécurisées conformément aux [prérequis de la boîte aux lettres personnalisée](user-submission.md).

Si votre organisation dispose d’une **boîte aux lettres personnalisée** configurée et n’a pas configuré les exclusions requises, ces messages peuvent être détonés, ce qui entraîne des affectations de formation.

## <a name="other-frequently-asked-questions"></a>Autres questions fréquemment posées

### <a name="q-what-is-the-recommended-method-to-target-users-for-simulation-campaigns"></a>Q : Quelle est la méthode recommandée pour cibler les utilisateurs pour les campagnes de simulation ?

R : Plusieurs options sont disponibles pour les utilisateurs cibles :

- Incluez tous les utilisateurs (actuellement disponibles pour les organisations de moins de 40 000 utilisateurs).
- Choisissez des utilisateurs spécifiques.
- Sélectionnez des utilisateurs dans un fichier CSV (une adresse e-mail par ligne).
- Ciblage basé sur un groupe Azure AD.

Nous avons constaté que les campagnes où les utilisateurs ciblés sont identifiés par des groupes Azure AD sont généralement plus faciles à gérer.

### <a name="q-are-there-any-limits-in-targeting-users-while-importing-from-a-csv-or-adding-users"></a>Q : Existe-t-il des limites dans le ciblage des utilisateurs lors de l’importation à partir d’un CSV ou de l’ajout d’utilisateurs ?

R : La limite pour importer des destinataires à partir d’un fichier CSV ou ajouter des destinataires individuels à une simulation est de 40 000.

Un destinataire peut être un utilisateur individuel ou un groupe. Un groupe peut contenir des centaines ou des milliers de destinataires, de sorte qu’une limite réelle n’est pas placée sur le nombre d’utilisateurs individuels.

La gestion d’un fichier CSV volumineux ou l’ajout de nombreux destinataires individuels peut être fastidieuse. L’utilisation de groupes Azure AD simplifie la gestion globale de la simulation.

### <a name="q-does-microsoft-provide-payloads-in-other-languages"></a>Q : Microsoft fournit-il des charges utiles dans d’autres langues ?

R : Actuellement, plus de 40 charges utiles localisées sont disponibles dans plus de 10 langues : chinois (simplifié), chinois (traditionnel), anglais, Français, allemand, italien, japonais, coréen, portugais, russe, espagnol et néerlandais. Nous avons remarqué que toute traduction directe ou automatique de charges utiles existantes vers d’autres langues entraînerait des inexactitudes et une diminution de la pertinence.

Cela dit, vous pouvez créer votre propre charge utile dans le langage de votre choix à l’aide de l’expérience de création de charge utile personnalisée. Nous vous recommandons également vivement de collecter les charges utiles existantes qui ont été utilisées pour cibler les utilisateurs dans une zone géographique spécifique. En d’autres termes, laissez les attaquants localiser le contenu pour vous.

### <a name="q-how-can-i-switch-to-other-languages-for-my-admin-portal-and-training-experience"></a>Q : Comment puis-je passer à d’autres langues pour mon portail d’administration et mon expérience de formation ?

R : Dans Microsoft 365 ou Office 365, la configuration du langage est spécifique et centralisée pour chaque compte d’utilisateur. Pour obtenir des instructions sur la modification de votre paramètre de langue, consultez [Modifier votre langue d’affichage et votre fuseau horaire dans Microsoft 365 Entreprise](https://support.microsoft.com/office/6f238bff-5252-441e-b32b-655d5d85d15b).

Notez que la synchronisation de la modification de configuration peut prendre jusqu’à 30 minutes sur tous les services.

### <a name="q-can-i-trigger-a-test-simulation-to-understand-what-it-looks-like-prior-to-launching-a-full-fledged-campaign"></a>Q : Puis-je déclencher une simulation de test pour comprendre à quoi elle ressemble avant de lancer une campagne à part entière ?

R: Oui, vous pouvez! Dans la toute dernière page **De la simulation** de révision de l’Assistant pour créer une simulation, il existe une option permettant d’envoyer **un test**. Cette option envoie un exemple de message de simulation d’hameçonnage à l’utilisateur actuellement connecté. Après avoir validé le message d’hameçonnage dans votre boîte de réception, vous pouvez envoyer la simulation.

:::image type="content" source="../../media/attack-sim-training-simulations-review-simulation.png" alt-text="Bouton Envoyer un test dans la page Vérifier la simulation" lightbox="../../media/attack-sim-training-simulations-review-simulation.png":::

### <a name="q-can-i-target-users-that-belong-to-a-different-tenant-as-part-of-the-same-simulation-campaign"></a>Q : Puis-je cibler des utilisateurs appartenant à un autre locataire dans le cadre de la même campagne de simulation ?

R : Non. Actuellement, les simulations entre locataires ne sont pas prises en charge. Vérifiez que tous vos utilisateurs ciblés se trouvent dans le même locataire. Tous les utilisateurs interlocataires ou invités seront exclus de la campagne de simulation.

### <a name="q-how-does-region-aware-delivery-work"></a>Q : Comment fonctionne la livraison tenant compte de la région ?

R : La remise en fonction de la région utilise l’attribut TimeZone de la boîte aux lettres de l’utilisateur ciblé et la logique « pas avant » pour déterminer quand remettre le message. Par exemple, envisagez le scénario suivant :

- À 7h00 dans le fuseau horaire pacifique (UTC-8), un administrateur crée et planifie une campagne pour démarrer à 9h00 le même jour.
- UserA se trouve dans le fuseau horaire est (UTC-5).
- UserB se trouve également dans le fuseau horaire pacifique.

Le même jour, à 9h00, le message de simulation est envoyé à UserB. Avec la remise en fonction de la région, le message n’est pas envoyé à UserA le même jour, car 9h00 heure du Pacifique est 12h00 heure de l’Est. Au lieu de cela, le message est envoyé à UserA à 9h00 heure de l’Est le lendemain.

Ainsi, lors de l’exécution initiale d’une campagne avec la remise prenant en charge la région activée, il peut sembler que le message de simulation a été envoyé uniquement aux utilisateurs dans un fuseau horaire spécifique. Toutefois, à mesure que le temps passe et que de plus en plus d’utilisateurs entrent dans l’étendue, les utilisateurs ciblés augmentent.


### <a name="q-does-microsoft-collect-or-store-any-information-that-users-enter-at-the-credential-harvest-sign-in-page-used-in-the-credential-harvest-simulation-technique"></a>Q : Microsoft collecte-t-il ou stocke-t-il les informations que les utilisateurs entrent dans la page de connexion de la collecte des informations d’identification, utilisée dans la technique de simulation de collecte des informations d’identification ?

R : Non. Toutes les informations entrées dans la page de connexion de collecte des informations d’identification sont ignorées en mode silencieux. Seul le « clic » est enregistré pour capturer l’événement de compromission. Microsoft ne collecte, ne journalise ni ne stocke les détails que les utilisateurs entrent à cette étape.
