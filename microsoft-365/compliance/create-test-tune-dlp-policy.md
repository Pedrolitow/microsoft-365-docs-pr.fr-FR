---
title: Création, test et réglage d’une stratégie DLP
f1.keywords:
- NOCSH
ms.author: chrfox
author: chrfox
manager: laurawi
audience: Admin
ms.topic: article
f1_keywords:
- ms.o365.cc.NewPolicyFromTemplate
ms.service: O365-seccomp
localization_priority: Normal
ms.collection:
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
ms.assetid: 59414438-99f5-488b-975c-5023f2254369
description: Dans cet article, vous allez découvrir comment créer, tester et régler une stratégie DLP en fonction des besoins de votre organisation.
ms.openlocfilehash: 3b7f74605c8a825bb03244f3a861ad3cca8f550d
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572572"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Création, test et réglage d’une stratégie DLP

La protection contre la perte de données (DLP) vous permet d’éviter le partage involontaire ou accidentel d’informations sensibles.

DLP examine les messages électroniques et les fichiers à la recherche d’informations sensibles, telles qu’un numéro de carte de crédit. À l’aide de la DLP, vous pouvez détecter les informations sensibles et prendre des mesures telles que :

- Journal de l’événement à des fins d’audit
- Afficher un avertissement à l’utilisateur final qui envoie l’e-mail ou partage le fichier
- Empêcher activement le partage de fichiers ou de courriers électroniques

## <a name="permissions"></a>Autorisations

Les membres de votre équipe de mise en conformité qui créeront des stratégies DLP ont besoin des autorisations d’accès au Centre de conformité. Par défaut, votre administrateur client aura accès aux responsables de la mise en conformité et à d’autres personnes. Procédez comme suit :
  
1. Créer un groupe dans Microsoft 365 et d’y ajouter des responsables de la mise en conformité.
    
2. Créer un groupe de rôles sur la page **Autorisations** du Centre de sécurité et de conformité. 

3. Lors de la création du groupe de rôles, utilisez la **section** Choisir des rôles pour ajouter le rôle suivant au groupe de rôles : **DLP Compliance Management**.
    
4. Utilisez la section **Choisir des membres** pour ajouter le groupe Microsoft 365 que vous avez créé précédemment au groupe de rôles.

Utilisez le rôle Gestion de la conformité **DLP** en affichage seul pour créer un groupe de rôles avec des privilèges d’affichage seul pour les stratégies DLP et les rapports DLP.

Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Ces autorisations sont nécessaires pour créer et appliquer une stratégie DLP afin de ne pas appliquer de stratégies.

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Détection des informations sensibles par DLP

DLP trouve des informations sensibles par correspondance de modèle d’expression régulière (RegEx), en combinaison avec d’autres indicateurs tels que la proximité de certains mots clés avec les modèles correspondants. Par exemple, un numéro de carte de crédit VISA a 16 chiffres. Toutefois, ces chiffres peuvent être écrits de différentes manières, par exemple 1111-1111-1111-1111, 1111 1111 1111 1111 ou 111111111111111111111.

Toute chaîne à 16 chiffres n’est pas nécessairement un numéro de carte de crédit, il peut s’agit d’un numéro de ticket provenant d’un système de service d’aide ou d’un numéro de série d’un élément matériel. Pour faire la différence entre un numéro de carte de crédit et une chaîne à 16 chiffres sans danger, un calcul est effectué (checksum) pour vérifier que les numéros correspondent à un modèle connu des différentes marques de carte de crédit.

Si DLP trouve des mots clés tels que « VISA » ou « AMEX », des valeurs proches qui peuvent être la date d’expiration de la carte de crédit, DLP utilise également ces données pour l’aider à déterminer si la chaîne est un numéro de carte de crédit ou non.

En d’autres termes, la DLP est suffisamment intelligente pour reconnaître la différence entre ces deux chaînes de texte dans un e-mail :

- « Pouvez-vous me commander un nouvel ordinateur portable ? Utilisez mon numéro VISA 1111-1111-1111-1111, arrivant à expiration le 22/11 et envoyez-moi la date de remise estimée lorsque vous l’avez. »
- « Le numéro de série de mon ordinateur portable est 2222-2222-2222-2222 et il a été acheté le 11/11/2010. En fait, mon visa de voyage est-il encore approuvé ? »

Voir [les définitions d’entités](sensitive-information-type-entity-definitions.md) de type Informations sensibles qui expliquent comment chaque type d’informations est détecté.

## <a name="where-to-start-with-data-loss-prevention"></a>Où commencer avec la protection contre la perte de données

Lorsque les risques de fuite de données ne sont pas entièrement évidents, il est difficile de savoir exactement où vous devez commencer avec l’implémentation de la protection contre la perte de données. Heureusement, les stratégies DLP peuvent être exécutés en « mode test », ce qui vous permet d’évaluer leur efficacité et leur précision avant de les activer.

Les stratégies DLP pour Exchange Online peuvent être gérées par le biais Exchange centre d’administration. Toutefois, vous pouvez configurer des stratégies DLP pour toutes les charges de travail via le Centre de sécurité & conformité. C’est donc ce que je vais utiliser pour les démonstrations de cet article. Dans le Centre de sécurité & conformité, vous trouverez les stratégies DLP sous Stratégie de protection contre la perte **de**  >  **données**. Choisissez **Créer une stratégie à** démarrer.

Microsoft 365 fournit une gamme de modèles de stratégie [DLP](what-the-dlp-policy-templates-include.md) que vous pouvez utiliser pour créer des stratégies. Supposons que vous êtes une entreprise australien. Vous pouvez filtrer les modèles sur l’Australie et choisir Financial, Medical and Health et Privacy.

![Option de choix du pays ou de la région](../media/DLP-create-test-tune-choose-country.png)

Pour cette démonstration, je choisirai les données d’informations d’identification personnelle (PII) de l’Australie, qui incluent les types d’informations du numéro de fichier fiscal australien (TFN) et du numéro de permis de conduire.

![Option de choix d’un modèle de stratégie](../media/DLP-create-test-tune-choose-policy-template.png)

Nommez votre nouvelle stratégie DLP. Le nom par défaut correspond au modèle de stratégie DLP, mais vous devez choisir un nom plus descriptif, car plusieurs stratégies peuvent être créées à partir du même modèle.

![Option de nom de votre stratégie](../media/DLP-create-test-tune-name-policy.png)

Choisissez les emplacements à appliquer à la stratégie. Les stratégies DLP peuvent s’appliquer Exchange Online, SharePoint Online et OneDrive Entreprise. Je vais laisser cette stratégie configurée pour s’appliquer à tous les emplacements.

![Option de choix de tous les emplacements](../media/DLP-create-test-tune-choose-locations.png)

À la première étape **Paramètres** stratégie, acceptez simplement les valeurs par défaut pour le moment. Vous pouvez personnaliser les stratégies DLP, mais les valeurs par défaut sont un bon endroit pour commencer.

![Options de personnalisation du type de contenu à protéger](../media/DLP-create-test-tune-default-customization-settings.png)

Après avoir cliqué sur Suivant,** vous verrez une page de stratégie **Paramètres** avec d’autres options de personnalisation. Pour une stratégie que vous testez simplement, voici où vous pouvez commencer à effectuer quelques ajustements.

- J’ai désactivé les conseils de stratégie pour le moment, ce qui est une étape raisonnable à suivre si vous testez simplement les choses et que vous ne souhaitez rien afficher pour le moment pour les utilisateurs. Les conseils de stratégie affichent des avertissements aux utilisateurs qu’ils sont sur le point d’enfreindre une stratégie DLP. Par exemple, un utilisateur Outlook voit un avertissement signalant que le fichier qu’il a joint contient des numéros de carte de crédit et entraîne le rejet de son courrier électronique. L’objectif des conseils de stratégie est d’arrêter le comportement non conforme avant qu’il ne se produise.
- J’ai également réduit le nombre d’instances de 10 à 1, afin que cette stratégie détecte tout partage de données piI australiens, et pas seulement le partage en bloc des données.
- J’ai également ajouté un autre destinataire à l’e-mail du rapport d’incident.

![Paramètres de stratégie supplémentaires](../media/DLP-create-test-tune-more-policy-settings.png)

Enfin, j’ai configuré cette stratégie pour qu’elle s’exécute en mode test initialement. Notez qu’il existe également une option ici pour désactiver les conseils de stratégie en mode test. Cela vous donne la possibilité d’activer des conseils de stratégie dans la stratégie, puis de décider s’il faut les afficher ou les supprimer lors de vos tests.

![Option de test de la stratégie en premier](../media/DLP-create-test-tune-test-mode.png)

Dans l’écran de révision final, cliquez sur **Créer** pour terminer la création de la stratégie.

## <a name="test-a-dlp-policy"></a>Tester une stratégie DLP

Votre nouvelle stratégie DLP commencera à prendre effet dans un délai d’environ 1 heure. Vous pouvez patienter et attendre qu’elle soit déclenchée par l’activité normale de l’utilisateur, ou vous pouvez essayer de la déclencher vous-même. Précédemment, j’ai lié les définitions d’entités de type Informations [sensibles,](sensitive-information-type-entity-definitions.md)qui vous fournit des informations sur la façon de déclencher des correspondances DLP.

Par exemple, la stratégie DLP que j’ai créée pour cet article détectera les numéros de fichiers fiscaux australiens (TFN). Selon la documentation, la correspondance est basée sur les critères suivants.

![Documentation sur le numéro de fichier fiscal australien](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
Pour faire la démonstration de la détection du TFN de manière assez discrète, un message électronique avec le mot « Numéro de fichier fiscal » et une chaîne à neuf chiffres à proximité se fera sans problème. La raison pour laquelle elle ne déclenche pas la stratégie DLP est que la chaîne à neuf chiffres doit transmettre la sommes de contrôle qui indique qu’il s’agit d’un TFN valide et non seulement d’une chaîne de nombres sans danger.

![Numéro de fichier fiscal australien ne réussissant pas la sommes de contrôle](../media/DLP-create-test-tune-email-test1.png)

En comparaison, un e-mail avec les mots « Numéro de fichier fiscal » et un numéro TFN valide qui réussit la liste de contrôle déclenche la stratégie. Pour l’enregistrement ici, le TFN que j’utilise a été tiré d’un site web qui génère des TFN valides, mais pas authentiques. Ces sites sont utiles car l’une des erreurs les plus courantes lors du test d’une stratégie DLP consiste à utiliser un nombre factice qui n’est pas valide et qui ne réussira pas la sommes de contrôle (et par conséquent ne déclenchera pas la stratégie).

![Numéro de fichier fiscal australien qui passe le total de contrôle](../media/DLP-create-test-tune-email-test2.png)

Le courrier électronique du rapport d’incident inclut le type d’informations sensibles qui ont été détectées, le nombre d’instances détectées et le niveau de confiance de la détection.

![Rapport d’incident montrant le numéro de fichier fiscal détecté](../media/DLP-create-test-tune-email-incident-report.png)

Si vous laissez votre stratégie DLP en mode test et analysez les e-mails de rapport d’incident, vous pouvez commencer à avoir une bonne impression de la précision de la stratégie DLP et de son efficacité lorsqu’elle est appliquée. Outre les rapports d’incident, vous pouvez utiliser les rapports [DLP](view-the-dlp-reports.md) pour afficher une vue agrégée des correspondances de stratégie au sein de votre client.

## <a name="tune-a-dlp-policy"></a>Régler une stratégie DLP

Lorsque vous analysez vos accès aux stratégies, vous souhaitez peut-être apporter quelques ajustements au comportement des stratégies. À titre d’exemple simple, vous pouvez déterminer qu’un seul nom de la partie TFN d’un e-mail n’est pas un problème (je pense que c’est toujours le cas, mais nous allons l’witht pour des raisons de démonstration), mais deux ou plusieurs instances sont un problème. Plusieurs instances peuvent être un scénario risqué, par exemple un employé qui envoie par courrier électronique une exportation CSV de la base de données RH à une partie externe, par exemple un service de comptabilité externe. Absolument quelque chose que vous préférez détecter et bloquer.

Dans le Centre de conformité, vous pouvez modifier une stratégie existante pour ajuster le comportement.

![Option de modification de stratégie](../media/DLP-create-test-tune-edit-policy.png)
 
Vous pouvez ajuster les paramètres d’emplacement afin que la stratégie soit appliquée uniquement à des charges de travail spécifiques ou à des sites et des comptes spécifiques.

![Options pour choisir des emplacements spécifiques](../media/DLP-create-test-tune-edit-locations.png)

Vous pouvez également ajuster les paramètres de stratégie et modifier les règles en fonction de vos besoins.

![Option de modification de la règle](../media/DLP-create-test-tune-edit-rule.png)

Lorsque vous modifiez une règle au sein d’une stratégie DLP, vous pouvez modifier :

- Les conditions, y compris le type et le nombre d’instances de données sensibles qui déclenchent la règle.
- Actions entreprises, telles que la restriction de l’accès au contenu.
- Les notifications des utilisateurs, qui sont des conseils de stratégie qui s’affichent à l’utilisateur dans leur client de messagerie ou navigateur web.
- Les substitutions utilisateur déterminent si les utilisateurs peuvent choisir de continuer à partager leurs messages électroniques ou fichiers.
- Rapports d’incident, pour avertir les administrateurs.

![Options pour modifier des parties d’une règle](../media/DLP-create-test-tune-editing-options.png)

Pour cette démonstration, j’ai ajouté des notifications utilisateur à la stratégie (faites attention sans formation adéquate aux utilisateurs) et j’ai autorisé les utilisateurs à remplacer la stratégie par une justification professionnelle ou en la signalant comme faux positif. Vous pouvez également personnaliser le texte du message électronique et du conseil de stratégie si vous souhaitez inclure des informations supplémentaires sur les stratégies de votre organisation ou invitez les utilisateurs à contacter le support technique s’ils ont des questions.

![Options pour les notifications et remplacements utilisateur](../media/DLP-create-test-tune-user-notifications.png)

La stratégie contient deux règles pour la gestion du volume élevé et du volume faible, donc n’oubliez pas de modifier les deux avec les actions que vous souhaitez. Il s’agit d’une opportunité de traiter les cas différemment en fonction de leurs caractéristiques. Par exemple, vous pouvez autoriser les remplacements pour les violations de volume faible, mais pas les remplacements pour les violations de volume élevées.

![Une règle pour un volume élevé et une règle pour un volume faible](../media/DLP-create-test-tune-two-rules.png)

En outre, si vous souhaitez bloquer ou restreindre l’accès au contenu en violation de la stratégie, vous devez configurer une action sur la règle pour le faire.

![Option pour restreindre l’accès au contenu](../media/DLP-create-test-tune-restrict-access-action.png)

Après avoir enregistrer ces modifications dans les paramètres de stratégie, je dois également revenir à la page de paramètres principale de la stratégie et activer l’option permettant d’afficher des conseils de stratégie aux utilisateurs pendant que la stratégie est en mode test. Il s’agit d’un moyen efficace d’introduire des stratégies DLP à vos utilisateurs finaux et de former les utilisateurs à la sensibilisation, sans risque de trop de faux positifs qui ont une incidence sur leur productivité.

![Option d’afficher les conseils de stratégie en mode test](../media/DLP-create-test-tune-show-policy-tips.png)

Côté serveur (ou côté cloud si vous préférez), la modification peut ne pas prendre effet immédiatement, en raison de différents intervalles de traitement. Si vous modifiez une stratégie DLP qui affiche de nouveaux conseils de stratégie pour un utilisateur, il se peut que les modifications ne prennent pas effet immédiatement dans son client Outlook, qui recherche les modifications de stratégie toutes les 24 heures. Si vous souhaitez accélérer les choses pour les tests, vous pouvez utiliser ce correctif du Registre pour effacer l’horodat de dernier téléchargement à partir de la clé [PolicyNudges](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook téléchargez les dernières informations de stratégie la prochaine fois que vous les redémarrez et commencez à composer un message électronique.

Si vous avez activé les conseils de stratégie, l’utilisateur commence à voir les conseils dans Outlook et peut vous signaler les faux positifs lorsqu’ils se produisent.

![Conseil de stratégie avec option pour signaler le faux positif](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Examiner les faux positifs

Les modèles de stratégie DLP ne sont pas parfaits. Il est probable que certains faux positifs se produisent dans votre environnement, c’est pourquoi il est important de faciliter votre passage à un déploiement DLP, en prenant le temps de tester et d’affiner correctement vos stratégies.

Voici un exemple de faux positif. Cet e-mail est relativement dangereux. L’utilisateur fournit son numéro de téléphone mobile à une personne, ainsi que sa signature électronique.

![Courrier électronique affichant des informations fausses positives](../media/DLP-create-test-tune-false-positive-email.png)
 
Mais l’utilisateur voit un conseil de stratégie l’avertissant que le courrier électronique contient des informations sensibles, notamment un numéro de permis de conduire australien.

![Option de signalement de faux positif dans le conseil de stratégie](../media/DLP-create-test-tune-policy-tip-closeup.png)

L’utilisateur peut signaler le faux positif et l’administrateur peut se demander pourquoi il s’est produit. Dans l’e-mail du rapport d’incident, l’e-mail est marqué comme faux positif.

![Rapport d’incident indiquant un faux positif](../media/DLP-create-test-tune-false-positive-incident-report.png)

Ce cas de permis de conduire est un bon exemple à prendre en compte. La raison pour laquelle ce faux positif s’est produit est que le type « Permis de conduire australien » est déclenché par n’importe quelle chaîne à 9 chiffres (même celle qui fait partie d’une chaîne à 10 chiffres), à 300 caractères près des mots clés « Sydney nsw » (ne sensible à la cas). Il est donc déclenché par le numéro de téléphone et la signature électronique, uniquement parce que l’utilisateur se trouve à Sydney.


Une option consiste à supprimer le type d’informations de permis de conduire australien de la stratégie. Il est là, car il fait partie du modèle de stratégie DLP, mais nous ne sommes pas obligés de l’utiliser. Si vous êtes intéressé uniquement par les numéros de fichiers fiscaux et non par les permis de conduire, vous pouvez simplement le supprimer. Par exemple, vous pouvez la supprimer de la règle de faible volume dans la stratégie, mais la laisser dans la règle de volume élevé afin que les listes de plusieurs licences de pilotes soient toujours détectées.
 
Une autre option consiste à augmenter le nombre d’instances afin qu’un faible volume de permis de conduire soit détecté uniquement lorsqu’il existe plusieurs instances.

![Option de modification du nombre d’instances](../media/DLP-create-test-tune-edit-instance-count.png)

En plus de modifier le nombre d’instances, vous pouvez également ajuster la précision de correspondance (ou le niveau de confiance). Si votre type d’informations sensibles possède plusieurs modèles, vous pouvez ajuster la précision de correspondance dans votre règle, afin que votre règle ne corresponde qu’à des modèles spécifiques. Par exemple, pour réduire les faux positifs, vous pouvez définir la précision de correspondance de votre règle afin qu’elle corresponde uniquement au modèle ayant le niveau de confiance le plus élevé. Pour plus d’informations sur les niveaux de confiance, voir comment utiliser le niveau [de confiance pour régler vos règles.](data-loss-prevention-policies.md#match-accuracy)

Enfin, si vous souhaitez obtenir encore un peu plus d’informations avancées, vous pouvez personnaliser n’importe quel type [d’informations](sensitive-information-type-entity-definitions.md#australia-drivers-license-number)sensibles : par exemple, vous pouvez supprimer « Sydney NSW » de la liste des mots clés pour le numéro de permis de conduire australien, afin d’éliminer le faux positif déclenché ci-dessus. Pour savoir comment faire à l’aide de XML et PowerShell, voir la personnalisation d’un [type d’informations sensibles intégré.](customize-a-built-in-sensitive-information-type.md)

## <a name="turn-on-a-dlp-policy"></a>Activer une stratégie DLP

Lorsque vous êtes satisfait que votre stratégie DLP détecte précisément et efficacement les types d’informations sensibles et que vos utilisateurs finaux sont prêts à gérer les stratégies en place, vous pouvez activer la stratégie.

![Option pour activer la stratégie](../media/DLP-create-test-tune-turn-on-policy.png)
 
Si vous attendez de voir à quel moment la stratégie prendra effet, Connecter au Centre de sécurité & conformité [PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez la [cmdlet Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy) pour voir DistributionStatus.

![Exécution de l’cmdlet dans PowerShell](../media/DLP-create-test-tune-PowerShell.png)

Après avoir exécuté la stratégie DLP, vous devez effectuer vos propres tests final pour vous assurer que les actions de stratégie attendues se produisent. Si vous essayez de tester des éléments tels que des données de carte de crédit, il existe des sites web en ligne avec des informations sur la façon de générer des exemples de carte de crédit ou d’autres informations personnelles qui passeront des sommes de contrôle et déclencheront vos stratégies.

Les stratégies qui autorisent les substitutions utilisateur présentent cette option à l’utilisateur dans le cadre du conseil de stratégie.

![Conseil de stratégie permettant le remplacement par l’utilisateur](../media/DLP-create-test-tune-override-option.png)

Les stratégies qui restreignent le contenu présentent l’avertissement à l’utilisateur dans le cadre du conseil de stratégie et l’empêchent d’envoyer le courrier électronique.

![Conseil de stratégie pour limiter le contenu](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Résumé

Les stratégies de protection contre la perte de données sont utiles pour les organisations de tous types. Le test de certaines stratégies DLP est un exercice à faible risque en raison du contrôle que vous exercez sur des éléments tels que des conseils de stratégie, des remplacements d’utilisateur final et des rapports d’incident. Vous pouvez tester en mode silencieux certaines stratégies DLP pour voir le type de violations qui se produisent déjà dans votre organisation, puis élaborer des stratégies avec de faibles taux de faux positifs, informer vos utilisateurs sur ce qui est autorisé et non autorisé, puis déployer vos stratégies DLP à l’organisation.