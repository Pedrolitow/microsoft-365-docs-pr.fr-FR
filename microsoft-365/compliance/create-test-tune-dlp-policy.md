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
ms.localizationpriority: medium
ms.collection:
- tier1
- purview-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
ms.assetid: 59414438-99f5-488b-975c-5023f2254369
description: Dans cet article, vous allez apprendre à créer, tester et paramétrer une stratégie DLP en fonction des besoins de votre organisation.
ms.openlocfilehash: f1a18f52646682f1e196dfa455b88f28c89526db
ms.sourcegitcommit: 21548843708d80bc861f03ffae41457252492bb6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2022
ms.locfileid: "68793981"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Création, test et réglage d’une stratégie DLP

Protection contre la perte de données Microsoft Purview (DLP) vous permet d’empêcher le partage involontaire ou accidentel d’informations sensibles.

DLP examine les messages électroniques et les fichiers à la recherche d’informations sensibles, comme un numéro de carte de crédit. À l’aide de DLP, vous pouvez détecter des informations sensibles et prendre des mesures telles que :

- Journaliser l’événement à des fins d’audit
- Afficher un avertissement à l’utilisateur final qui envoie l’e-mail ou partage le fichier
- Bloquer activement le partage d’e-mails ou de fichiers

[!INCLUDE [purview-preview](../includes/purview-preview.md)]

## <a name="permissions"></a>Autorisations

Les membres de votre équipe de mise en conformité qui créeront des stratégies DLP ont besoin des autorisations d’accès au Centre de conformité. Par défaut, l’administrateur de votre locataire disposera d’un accès pouvant donner accès aux responsables de la conformité et à d’autres personnes. Procédez comme suit :
  
1. Créer un groupe dans Microsoft 365 et d’y ajouter des responsables de la mise en conformité.
    
2. Créez un groupe de rôles dans la page **Autorisations** du portail de conformité Microsoft Purview. 

3. Lors de la création du groupe de rôles, utilisez la section **Choisir des rôles** pour ajouter le rôle suivant au groupe de rôles : **Gestion de la conformité DLP**.
    
4. Utilisez la section **Choisir des membres** pour ajouter le groupe Microsoft 365 que vous avez créé précédemment au groupe de rôles.

Utilisez le rôle **View-Only DLP Compliance Management (Gestion de la conformité DLP** uniquement) pour créer un groupe de rôles avec des privilèges d’affichage uniquement pour les stratégies DLP et les rapports DLP.

Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Ces autorisations sont nécessaires pour créer et appliquer une stratégie DLP et non pour appliquer des stratégies.

### <a name="roles-and-role-groups-in-preview"></a>Rôles et groupes de rôles en préversion

Il existe des rôles et des groupes de rôles en préversion que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles applicables qui sont en préversion. Pour en savoir plus à leur sujet, consultez [Autorisations dans la portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

- Administrateur Information Protection
- Analyste Information Protection
- Enquêteur Information Protection
- Lecteur Information Protection

Voici une liste des groupes de rôles applicables en préversion. Pour plus d’informations, consultez [Autorisations dans la portail de conformité Microsoft Purview](microsoft-365-compliance-center-permissions.md).

- Protection des informations
- Administrateurs Information Protection
- Analystes Information Protection
- Enquêteurs Information Protection
- Lecteurs Information Protection

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Détection des informations sensibles par DLP

DLP recherche des informations sensibles par la correspondance de modèle d’expression régulière (RegEx), en combinaison avec d’autres indicateurs tels que la proximité de certains mots clés aux modèles de correspondance. Par exemple, un numéro de carte de crédit VISA comporte 16 chiffres. Toutefois, ces chiffres peuvent être écrits de différentes manières, par exemple 1111-1111-1111-1111, 1111 1111 1111 1111 ou 1111111111111111.

Toute chaîne à 16 chiffres n’est pas nécessairement un numéro de carte de crédit, il peut s’agir d’un numéro de ticket provenant d’un système de support technique ou d’un numéro de série d’une pièce matérielle. Pour faire la différence entre un numéro de carte de crédit et une chaîne inoffensive à 16 chiffres, un calcul est effectué (somme de contrôle) pour confirmer que les numéros correspondent à un modèle connu des différentes marques de carte de crédit.

Si DLP trouve des mots clés tels que « VISA » ou « AMEX », des valeurs de date proches qui peuvent être la date d’expiration de la carte de crédit, DLP utilise également ces données pour l’aider à décider si la chaîne est un numéro de carte de crédit ou non.

En d’autres termes, la DLP est suffisamment intelligente pour reconnaître la différence entre ces deux chaînes de texte dans un e-mail :

- « Pouvez-vous me commander un nouvel ordinateur portable. Utilisez mon numéro de VISA 1111-1111-1111-1111, date d’expiration 11/22, et envoyez-moi la date de livraison estimée quand vous l’avez.
- « Mon numéro de série d’ordinateur portable est 2222-2222-2222-2222 et il a été acheté le 11/2010. Au fait, mon visa de voyage est-il encore approuvé? »

Consultez [Définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md) qui explique comment chaque type d’informations est détecté.

## <a name="where-to-start-with-data-loss-prevention"></a>Par où commencer avec la protection contre la perte de données

Lorsque les risques de fuite de données ne sont pas tout à fait évidents, il est difficile de déterminer exactement où commencer avec l’implémentation de DLP. Heureusement, les stratégies DLP peuvent être exécutées en « mode test », ce qui vous permet d’évaluer leur efficacité et leur précision avant de les activer.

Les stratégies DLP pour Exchange Online peuvent être gérées via le Centre d’administration Exchange. Toutefois, vous pouvez configurer des stratégies DLP pour toutes les charges de travail via le portail de conformité Microsoft Purview, c’est ce que je vais utiliser pour les démonstrations dans cet article. Dans la portail de conformité Microsoft Purview, vous trouverez les stratégies DLP sous **Stratégie de protection contre la** >  perte **de** données. Choisissez **Créer une stratégie** pour démarrer.

Microsoft 365 fournit une gamme de [modèles de stratégie DLP](what-the-dlp-policy-templates-include.md) que vous pouvez utiliser pour créer des stratégies. Disons que vous êtes une entreprise australienne. Vous pouvez filtrer les modèles sur l’Australie, puis choisir Financier, Médical et Santé, et Confidentialité.

![Option permettant de choisir un pays ou une région.](../media/DLP-create-test-tune-choose-country.png)

Pour cette démonstration, je vais choisir les données d’identification personnelle (PII) australiennes, qui incluent les types d’informations du numéro de fichier fiscal australien (TFN) et du numéro de permis de conduire.

![Option permettant de choisir un modèle de stratégie.](../media/DLP-create-test-tune-choose-policy-template.png)

Donnez un nom à votre nouvelle stratégie DLP. Le nom par défaut correspond au modèle de stratégie DLP, mais vous devez choisir un nom plus descriptif, car plusieurs stratégies peuvent être créées à partir du même modèle.

![Option permettant de nommer votre stratégie.](../media/DLP-create-test-tune-name-policy.png)

Choisissez les emplacements auxquels la stratégie s’appliquera. Les stratégies DLP peuvent s’appliquer à Exchange Online, SharePoint Online et OneDrive Entreprise. Je vais laisser cette stratégie configurée pour s’appliquer à tous les emplacements.

![Option permettant de choisir tous les emplacements.](../media/DLP-create-test-tune-choose-locations.png)

À la première étape **des paramètres de** stratégie, acceptez simplement les valeurs par défaut pour l’instant. Vous pouvez personnaliser les stratégies DLP, mais les valeurs par défaut sont un bon point de départ.

![Options permettant de personnaliser le type de contenu à protéger.](../media/DLP-create-test-tune-default-customization-settings.png)

Après avoir cliqué sur Suivant,** **une page paramètres** de stratégie supplémentaire s’affiche avec d’autres options de personnalisation. Pour une stratégie que vous venez de tester, voici l’endroit où vous pouvez commencer à apporter des ajustements.

- J’ai désactivé les conseils de stratégie pour l’instant, ce qui est une étape raisonnable à prendre si vous testez simplement des choses et ne voulez pas encore afficher quoi que ce soit aux utilisateurs. Les conseils de stratégie affichent des avertissements aux utilisateurs indiquant qu’ils sont sur le point de violer une stratégie DLP. Par exemple, un utilisateur Outlook verra un avertissement indiquant que le fichier qu’il a joint contient des numéros de carte de crédit et entraînera le rejet de son e-mail. L’objectif des conseils de stratégie est d’arrêter le comportement non conforme avant qu’il ne se produise.
- J’ai également réduit le nombre d’instances de 10 à 1, afin que cette stratégie détecte tout partage de données d’informations personnelles australiennes, et pas seulement le partage en bloc des données.
- J’ai également ajouté un autre destinataire à l’e-mail du rapport d’incident.

![Paramètres de stratégie supplémentaires.](../media/DLP-create-test-tune-more-policy-settings.png)

Enfin, j’ai configuré cette stratégie pour qu’elle s’exécute en mode test initialement. Notez qu’il existe également une option ici pour désactiver les conseils de stratégie en mode test. Cela vous donne la possibilité d’activer les conseils de stratégie dans la stratégie, mais de décider ensuite de les afficher ou de les supprimer pendant vos tests.

![Option permettant de tester d’abord la stratégie.](../media/DLP-create-test-tune-test-mode.png)

Dans l’écran de révision finale, cliquez sur **Créer** pour terminer la création de la stratégie.

## <a name="test-a-dlp-policy"></a>Tester une stratégie DLP

Vous pouvez vous asseoir et attendre que la stratégie soit déclenchée par l’activité normale de l’utilisateur, ou vous pouvez essayer de la déclencher vous-même. J’ai précédemment lié aux [définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md), qui vous fournit des informations sur la façon de déclencher des correspondances DLP.

Par exemple, la stratégie DLP que j’ai créée pour cet article détecte les numéros de fichier fiscaux australiens (TFN). Selon la documentation, la correspondance est basée sur les critères suivants.

![Documentation sur le numéro de fichier fiscal en Australie.](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
Pour illustrer la détection tfn d’une manière plutôt directe, un e-mail avec les mots « Numéro de dossier fiscal » et une chaîne à neuf chiffres à proximité vous permettra de naviguer sans aucun problème. La raison pour laquelle elle ne déclenche pas la stratégie DLP est que la chaîne de neuf chiffres doit passer la somme de contrôle qui indique qu’il s’agit d’un TFN valide et pas seulement d’une chaîne de nombres inoffensive.

![Numéro de fichier fiscal australie qui ne passe pas la somme de contrôle.](../media/DLP-create-test-tune-email-test1.png)

En comparaison, un e-mail avec les mots « Numéro de fichier fiscal » et un TFN valide qui transmet la somme de contrôle déclenchent la stratégie. Pour mémoire, le TFN que j’utilise a été extrait d’un site web qui génère des TFN valides, mais pas authentiques. Ces sites sont utiles, car l’une des erreurs les plus courantes lors du test d’une stratégie DLP est l’utilisation d’un faux numéro qui n’est pas valide et ne passera pas la somme de contrôle (et ne déclenche donc pas la stratégie).

![Numéro de fichier fiscal australien qui passe la somme de contrôle.](../media/DLP-create-test-tune-email-test2.png)

L’e-mail de rapport d’incident inclut le type d’informations sensibles détectées, le nombre d’instances détectées et le niveau de confiance de la détection.

![Rapport d’incident montrant le numéro de fichier fiscal détecté.](../media/DLP-create-test-tune-email-incident-report.png)

Si vous laissez votre stratégie DLP en mode test et analysez les e-mails de rapport d’incident, vous pouvez commencer à avoir une idée de la précision de la stratégie DLP et de son efficacité quand elle sera appliquée. En plus des rapports d’incident, vous pouvez [utiliser les rapports DLP](view-the-dlp-reports.md) pour afficher une vue agrégée des correspondances de stratégie dans votre locataire.

## <a name="tune-a-dlp-policy"></a>Régler une stratégie DLP

Au fur et à mesure que vous analysez vos résultats de stratégie, vous souhaiterez peut-être apporter des ajustements au comportement des stratégies. Par exemple, vous pouvez déterminer qu’un tfn dans un e-mail n’est pas un problème (je pense que c’est toujours le cas, mais allons-y pour la démonstration), mais deux instances ou plus sont un problème. Plusieurs instances peuvent être un scénario risqué, tel qu’un employé envoyant par e-mail une exportation CSV de la base de données RH à un tiers externe, par exemple un service de comptabilité externe. Certainement quelque chose que vous préféreriez détecter et bloquer.

Dans le Centre de conformité, vous pouvez modifier une stratégie existante pour ajuster le comportement.

![Option de modification de la stratégie.](../media/DLP-create-test-tune-edit-policy.png)
 
Vous pouvez ajuster les paramètres d’emplacement afin que la stratégie soit appliquée uniquement à des charges de travail spécifiques, ou à des sites et comptes spécifiques.

![Options permettant de choisir des emplacements spécifiques.](../media/DLP-create-test-tune-edit-locations.png)

Vous pouvez également ajuster les paramètres de stratégie et modifier les règles en fonction de vos besoins.

![Option permettant de modifier la règle.](../media/DLP-create-test-tune-edit-rule.png)

Lorsque vous modifiez une règle au sein d’une stratégie DLP, vous pouvez modifier :

- Les conditions, y compris le type et le nombre d’instances de données sensibles qui déclencheront la règle.
- Actions effectuées, telles que la restriction de l’accès au contenu.
- Notifications utilisateur, qui sont des conseils de stratégie qui sont affichés à l’utilisateur dans son client de messagerie ou son navigateur web.
- Les remplacements utilisateur déterminent si les utilisateurs peuvent choisir de poursuivre leur messagerie ou leur partage de fichiers de toute façon.
- Rapports d’incidents, pour avertir les administrateurs.

![Options permettant de modifier des parties d’une règle.](../media/DLP-create-test-tune-editing-options.png)

Pour cette démonstration, j’ai ajouté des notifications utilisateur à la stratégie (veillez à le faire sans formation adéquate de sensibilisation des utilisateurs) et autorisé les utilisateurs à remplacer la stratégie par une justification professionnelle ou en la signalant comme un faux positif. Vous pouvez également personnaliser le message électronique et le texte de conseil de stratégie si vous souhaitez inclure des informations supplémentaires sur les stratégies de votre organisation, ou inviter les utilisateurs à contacter le support technique s’ils ont des questions.

![Options pour les notifications utilisateur et les remplacements.](../media/DLP-create-test-tune-user-notifications.png)

La stratégie contient deux règles pour la gestion du volume élevé et du faible volume. Veillez donc à modifier les deux avec les actions souhaitées. C’est l’occasion de traiter les cas différemment en fonction de leurs caractéristiques. Par exemple, vous pouvez autoriser les remplacements pour les violations à faible volume, mais pas les remplacements pour les violations à volume élevé.

![Une règle pour le volume élevé et une règle pour le faible volume.](../media/DLP-create-test-tune-two-rules.png)

En outre, si vous souhaitez réellement bloquer ou restreindre l’accès au contenu qui enfreint la stratégie, vous devez configurer une action sur la règle pour ce faire.

![Option permettant de restreindre l’accès au contenu.](../media/DLP-create-test-tune-restrict-access-action.png)

Après avoir enregistré ces modifications dans les paramètres de stratégie, je dois également revenir à la page de paramètres principale de la stratégie et activer l’option permettant d’afficher des conseils de stratégie aux utilisateurs lorsque la stratégie est en mode test. Il s’agit d’un moyen efficace d’introduire des stratégies DLP à vos utilisateurs finaux et d’effectuer une formation de sensibilisation des utilisateurs, sans risquer trop de faux positifs qui ont un impact sur leur productivité.

![Option permettant d’afficher les conseils de stratégie en mode test.](../media/DLP-create-test-tune-show-policy-tips.png)

Côté serveur (ou côté cloud si vous préférez), la modification peut ne pas prendre effet immédiatement, en raison de différents intervalles de traitement. Si vous apportez une modification de stratégie DLP qui affiche de nouveaux conseils de stratégie à un utilisateur, il se peut que l’utilisateur ne voit pas les modifications prendre effet immédiatement dans son client Outlook, qui vérifie les modifications de stratégie toutes les 24 heures. Si vous souhaitez accélérer les tests, vous pouvez utiliser ce correctif de Registre pour [effacer l’horodatage du dernier téléchargement de la clé PolicyNudges](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook télécharge les informations de stratégie les plus récentes la prochaine fois que vous le redémarrez et commencez à composer un e-mail.

Si vous avez activé des conseils de stratégie, l’utilisateur commence à voir les conseils dans Outlook et peut vous signaler les faux positifs lorsqu’ils se produisent.

![Conseil de stratégie avec l’option de signalement de faux positifs.](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Examiner les faux positifs

Les modèles de stratégie DLP ne sont pas parfaits tout de suite. Il est probable que vous trouviez des faux positifs dans votre environnement, c’est pourquoi il est si important de faciliter votre chemin dans un déploiement DLP, en prenant le temps de tester et de paramétrer correctement vos stratégies.

Voici un exemple de faux positif. Cet e-mail est inoffensif. L’utilisateur fournit son numéro de téléphone mobile à une personne et inclut sa signature par e-mail.

![Email afficher des informations de faux positifs.](../media/DLP-create-test-tune-false-positive-email.png)
 
Mais l’utilisateur voit un conseil de stratégie l’avertissant que l’e-mail contient des informations sensibles, en particulier un numéro de permis de conduire australien.

![Option permettant de signaler un faux positif dans le conseil de stratégie.](../media/DLP-create-test-tune-policy-tip-closeup.png)

L’utilisateur peut signaler le faux positif et l’administrateur peut examiner la raison pour laquelle il s’est produit. Dans l’e-mail du rapport d’incident, l’e-mail est marqué comme faux positif.

![Rapport d’incident montrant un faux positif.](../media/DLP-create-test-tune-false-positive-incident-report.png)

Ce cas de permis de conduire est un bon exemple à explorer. La raison pour laquelle ce faux positif s’est produit est que le type « Permis de conduire australien » est déclenché par n’importe quelle chaîne à 9 chiffres (même une qui fait partie d’une chaîne à 10 chiffres), à moins de 300 caractères à proximité des mots clés « Sydney nsw » (ne respectant pas la casse). Il est donc déclenché par le numéro de téléphone et la signature de l’e-mail, uniquement parce que l’utilisateur se trouve à Sydney.


Une option consiste à supprimer le type d’informations de permis de conduire australien de la stratégie. Il est là- bas, car il fait partie du modèle de stratégie DLP, mais nous ne sommes pas obligés de l’utiliser. Si vous n’êtes intéressé que par les numéros de fichier fiscaux et non par les permis de conduire, vous pouvez simplement le supprimer. Par exemple, vous pouvez la supprimer de la règle de faible volume dans la stratégie, mais la laisser dans la règle de volume élevé afin que les listes de plusieurs permis de conduire soient toujours détectées.
 
Une autre option consiste à augmenter le nombre d’instances, afin qu’un faible volume de permis de conduire ne soit détecté que lorsqu’il y a plusieurs instances.

![Option permettant de modifier le nombre d’instances.](../media/DLP-create-test-tune-edit-instance-count.png)

En plus de modifier le nombre d’instances, vous pouvez également ajuster la précision de la correspondance (ou le niveau de confiance). Si votre type d’informations sensibles a plusieurs modèles, vous pouvez ajuster la précision des correspondances dans votre règle afin que votre règle ne corresponde qu’à des modèles spécifiques. Par exemple, pour réduire les faux positifs, vous pouvez définir la précision de correspondance de votre règle afin qu’elle corresponde uniquement au modèle avec le niveau de confiance le plus élevé. Pour plus d’informations sur les niveaux de confiance, consultez [Comment utiliser le niveau de confiance pour paramétrer vos règles](data-loss-prevention-policies.md#match-accuracy).

Enfin, si vous souhaitez obtenir un peu plus avancé, vous pouvez personnaliser n’importe quel type d’informations sensibles. Par exemple, vous pouvez supprimer « Sydney NSW » de la liste des mots clés pour le [numéro de permis de conduire en Australie](sit-defn-australia-drivers-license-number.md), afin d’éliminer les faux positifs déclenchés ci-dessus. Pour savoir comment effectuer cette opération à l’aide de XML et de PowerShell, consultez [Personnalisation d’un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md).

## <a name="turn-on-a-dlp-policy"></a>Activer une stratégie DLP

Lorsque vous êtes satisfait que votre stratégie DLP détecte avec précision et efficacité les types d’informations sensibles et que vos utilisateurs finaux sont prêts à gérer les stratégies en place, vous pouvez activer la stratégie.

![Option permettant d’activer la stratégie.](../media/DLP-create-test-tune-turn-on-policy.png)
 
Si vous attendez de voir quand la stratégie prendra effet, [connectez-vous à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) et exécutez [l’applet de commande Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy) pour voir distributionStatus.

 ```powershell
 Get-DlpCompliancePolicy "Testing -Australia PII" -DistributionDetail | Select distributionstatus
 ```
Après avoir activé la stratégie DLP, vous devez exécuter vos propres tests finaux pour vous assurer que les actions de stratégie attendues se produisent. Si vous essayez de tester des éléments tels que les données de carte de crédit, il existe des sites web en ligne avec des informations sur la façon de générer des exemples de carte de crédit ou d’autres informations personnelles qui réussissent des sommes de contrôle et déclenchent vos stratégies.

Les stratégies qui autorisent les substitutions utilisateur présentent cette option à l’utilisateur dans le cadre du conseil de stratégie.

![Conseil de stratégie qui autorise le remplacement par l’utilisateur.](../media/DLP-create-test-tune-override-option.png)

Les stratégies qui limitent le contenu présentent l’avertissement à l’utilisateur dans le cadre du conseil de stratégie et l’empêchent d’envoyer l’e-mail.

![Conseil de stratégie indiquant que le contenu est restreint.](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Résumé

Les stratégies de protection contre la perte de données sont utiles pour les organisations de tous types. Le test de certaines stratégies DLP est un exercice à faible risque en raison du contrôle que vous avez sur des éléments tels que les conseils de stratégie, les remplacements des utilisateurs finaux et les rapports d’incident. Vous pouvez tester silencieusement certaines stratégies DLP pour voir quel type de violations se produisent déjà dans votre organisation, puis créer des stratégies avec des taux de faux positifs faibles, informer vos utilisateurs sur ce qui est autorisé et non autorisé, puis déployer vos stratégies DLP dans l’organisation.
