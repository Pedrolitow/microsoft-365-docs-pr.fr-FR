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
- M365-security-compliance
search.appverid:
- MET150
ms.custom:
- seo-marvel-mar2020
ms.assetid: 59414438-99f5-488b-975c-5023f2254369
description: Dans cet article, vous allez apprendre à créer, tester et paramétrer une stratégie DLP en fonction des besoins de votre organisation.
ms.openlocfilehash: dff47d07a582be807d877471fb7621960b776f24
ms.sourcegitcommit: c29fc9d7477c3985d02d7a956a9f4b311c4d9c76
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/06/2022
ms.locfileid: "66624728"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Création, test et réglage d’une stratégie DLP

Protection contre la perte de données Microsoft Purview (DLP) vous permet d’éviter le partage involontaire ou accidentel d’informations sensibles.

DLP examine les messages électroniques et les fichiers à la recherche d’informations sensibles, telles qu’un numéro de carte de crédit. À l’aide de DLP, vous pouvez détecter les informations sensibles et prendre des mesures telles que :

- Consigner l’événement à des fins d’audit
- Afficher un avertissement à l’utilisateur final qui envoie l’e-mail ou partage le fichier
- Empêcher activement le partage d’e-mails ou de fichiers d’avoir lieu

## <a name="permissions"></a>Autorisations

Les membres de votre équipe de mise en conformité qui créeront des stratégies DLP ont besoin des autorisations d’accès au Centre de conformité. Par défaut, votre administrateur client aura accès à des agents de conformité et à d’autres personnes. Procédez comme suit :
  
1. Créer un groupe dans Microsoft 365 et d’y ajouter des responsables de la mise en conformité.
    
2. Créez un groupe de rôles sur la page **Autorisations** du portail de conformité Microsoft Purview. 

3. Lors de la création du groupe de rôles, utilisez la section **Choisir des rôles** pour ajouter le rôle suivant au groupe de rôles : **Gestion de la conformité DLP**.
    
4. Utilisez la section **Choisir des membres** pour ajouter le groupe Microsoft 365 que vous avez créé précédemment au groupe de rôles.

Utilisez le rôle **Gestion de la conformité DLP en mode affichage uniquement** pour créer un groupe de rôles avec des privilèges d’affichage uniquement pour les stratégies DLP et les rapports DLP.

Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Ces autorisations sont nécessaires pour créer et appliquer une stratégie DLP pour ne pas appliquer de stratégies.

### <a name="roles-and-role-groups-in-preview"></a>Rôles et groupes de rôles en préversion

Il existe des rôles et des groupes de rôles en préversion que vous pouvez tester pour affiner vos contrôles d’accès.

Voici une liste des rôles applicables qui sont en préversion. Pour en savoir plus sur ces rôles, consultez [Rôles dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#roles-in-the-security--compliance-center)

- Administrateur Information Protection
- Analyste Information Protection
- Enquêteur Information Protection
- Lecteur Information Protection

Voici une liste des groupes de rôles applicables en préversion. Pour en savoir plus sur ces groupes, consultez [Groupes de rôles dans le Centre de sécurité et de conformité](../security/office-365-security/permissions-in-the-security-and-compliance-center.md#role-groups-in-the-security--compliance-center)

- Protection des informations
- Administrateurs Information Protection
- Analystes Information Protection
- Enquêteurs Information Protection
- Lecteurs Information Protection

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Comment les informations sensibles sont détectées par DLP

DLP recherche des informations sensibles par correspondance de modèle d’expression régulière (RegEx), en combinaison avec d’autres indicateurs tels que la proximité de certains mots clés avec les modèles correspondants. Par exemple, un numéro de carte de crédit VISA comporte 16 chiffres. Toutefois, ces chiffres peuvent être écrits de différentes manières, par exemple 1111-1111-1111-1111, 1111 1111 1111 1111 ou 1111111111111111.

Toute chaîne à 16 chiffres n’est pas nécessairement un numéro de carte de crédit, il peut s’agir d’un numéro de ticket d’un système de support technique ou d’un numéro de série d’un morceau de matériel. Pour faire la différence entre un numéro de carte de crédit et une chaîne inoffensive à 16 chiffres, un calcul est effectué (somme de contrôle) pour confirmer que les nombres correspondent à un modèle connu des différentes marques de carte de crédit.

Si DLP trouve des mots clés tels que « VISA » ou « AMEX », valeurs de date proche qui peuvent être la date d’expiration de la carte de crédit, DLP utilise également ces données pour l’aider à déterminer si la chaîne est un numéro de carte de crédit ou non.

En d’autres termes, DLP est suffisamment intelligent pour reconnaître la différence entre ces deux chaînes de texte dans un e-mail :

- « Pouvez-vous me commander un nouvel ordinateur portable. Utilisez mon numéro visa 1111-1111-1111-1111, expiration 11/22, et envoyez-moi la date de livraison estimée quand vous l’avez.
- « Mon numéro de série portable est 2222-2222-2222-2222 et il a été acheté le 11/2010. D’ailleurs, est-ce que mon visa de voyage est encore approuvé?

Consultez [les définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md) qui expliquent comment chaque type d’informations est détecté.

## <a name="where-to-start-with-data-loss-prevention"></a>Par où commencer avec la protection contre la perte de données

Lorsque les risques de fuite de données ne sont pas entièrement évidents, il est difficile de déterminer exactement où vous devez commencer par implémenter DLP. Heureusement, les stratégies DLP peuvent être exécutées en « mode test », ce qui vous permet d’évaluer leur efficacité et leur précision avant de les activer.

Les stratégies DLP pour Exchange Online peuvent être gérées via le Centre d’administration Exchange. Toutefois, vous pouvez configurer des stratégies DLP pour toutes les charges de travail via le portail de conformité Microsoft Purview, c’est ce que je vais utiliser pour les démonstrations de cet article. Dans le portail de conformité Microsoft Purview, vous trouverez les stratégies DLP sous la stratégie **de protection contre la perte de** >  données **.** Choisissez **Créer une stratégie** pour démarrer.

Microsoft 365 fournit une gamme de [modèles de stratégie DLP](what-the-dlp-policy-templates-include.md) que vous pouvez utiliser pour créer des stratégies. Supposons que vous êtes une entreprise australienne. Vous pouvez filtrer les modèles sur l’Australie et choisir Finances, Santé et Santé, et Confidentialité.

![Option permettant de choisir le pays ou la région.](../media/DLP-create-test-tune-choose-country.png)

Pour cette démonstration, je vais choisir australian Personally Identifiable Information (PII) Data, qui inclut les types d’informations du numéro de fichier fiscal australien (TFN) et le numéro de permis de conduire.

![Option permettant de choisir un modèle de stratégie.](../media/DLP-create-test-tune-choose-policy-template.png)

Donnez un nom à votre nouvelle stratégie DLP. Le nom par défaut correspond au modèle de stratégie DLP, mais vous devez choisir un nom plus descriptif, car plusieurs stratégies peuvent être créées à partir du même modèle.

![Option pour nommer votre stratégie.](../media/DLP-create-test-tune-name-policy.png)

Choisissez les emplacements auxquels la stratégie s’appliquera. Les stratégies DLP peuvent s’appliquer à Exchange Online, SharePoint Online et OneDrive Entreprise. Je vais laisser cette stratégie configurée pour s’appliquer à tous les emplacements.

![Option permettant de choisir tous les emplacements.](../media/DLP-create-test-tune-choose-locations.png)

À la première étape **des paramètres** de stratégie, acceptez simplement les valeurs par défaut pour l’instant. Vous pouvez personnaliser les stratégies DLP, mais les valeurs par défaut sont un bon point de départ.

![Options permettant de personnaliser le type de contenu à protéger.](../media/DLP-create-test-tune-default-customization-settings.png)

Après avoir cliqué sur Suivant**, une page plus **de paramètres** de stratégie s’affiche avec plus d’options de personnalisation. Pour une stratégie que vous testez simplement, voici où vous pouvez commencer à effectuer des ajustements.

- J’ai désactivé les conseils de stratégie pour l’instant, ce qui est une étape raisonnable à prendre si vous ne faites que tester les choses et ne voulez pas afficher quoi que ce soit pour les utilisateurs encore. Les conseils de stratégie affichent des avertissements aux utilisateurs indiquant qu’ils sont sur le point de violer une stratégie DLP. Par exemple, un utilisateur Outlook voit un avertissement indiquant que le fichier qu’il a joint contient des numéros de carte de crédit et entraîne le rejet de son e-mail. L’objectif des conseils de stratégie est d’arrêter le comportement non conforme avant qu’il ne se produise.
- J’ai également réduit le nombre d’instances de 10 à 1, de sorte que cette stratégie détectera tout partage de données pii australiennes, pas seulement le partage en bloc des données.
- J’ai également ajouté un autre destinataire à l’e-mail du rapport d’incident.

![Paramètres de stratégie supplémentaires.](../media/DLP-create-test-tune-more-policy-settings.png)

Enfin, j’ai configuré cette stratégie pour qu’elle s’exécute initialement en mode test. Notez qu’il existe également une option ici pour désactiver les conseils de stratégie en mode test. Cela vous donne la possibilité d’activer les conseils de stratégie dans la stratégie, puis de décider de les afficher ou de les supprimer pendant votre test.

![Option permettant de tester d’abord la stratégie.](../media/DLP-create-test-tune-test-mode.png)

Dans l’écran de révision finale, cliquez sur **Créer** pour terminer la création de la stratégie.

## <a name="test-a-dlp-policy"></a>Tester une stratégie DLP

Vous pouvez attendre que la stratégie soit déclenchée par une activité utilisateur normale, ou vous pouvez essayer de la déclencher vous-même. Précédemment, j’ai lié à [des définitions d’entité de type d’informations sensibles](sensitive-information-type-entity-definitions.md), qui vous fournissent des informations sur la façon de déclencher des correspondances DLP.

Par exemple, la stratégie DLP que j’ai créée pour cet article détectera les numéros de fichier fiscal australiens (TFN). Selon la documentation, la correspondance est basée sur les critères suivants.

![Documentation sur le numéro de fichier fiscal australien.](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
Pour illustrer la détection TFN de manière assez simple, un e-mail contenant les mots « Numéro de fichier fiscal » et une chaîne à neuf chiffres à proximité naviguera sans problème. La raison pour laquelle elle ne déclenche pas la stratégie DLP est que la chaîne à neuf chiffres doit passer la somme de contrôle qui indique qu’il s’agit d’un TFN valide et pas seulement d’une chaîne de nombres inoffensif.

![Numéro de fichier fiscal australien qui ne passe pas la somme de contrôle.](../media/DLP-create-test-tune-email-test1.png)

En comparaison, un e-mail avec les mots « Numéro de fichier fiscal » et un TFN valide qui passe la somme de contrôle déclenche la stratégie. Pour l’enregistrement ici, le TFN que j’utilise a été tiré d’un site web qui génère des TFN valides, mais pas authentiques. Ces sites sont utiles, car l’une des erreurs les plus courantes lors du test d’une stratégie DLP est d’utiliser un nombre faux qui n’est pas valide et ne passe pas la somme de contrôle (et par conséquent ne déclenchera pas la stratégie).

![Numéro de fichier fiscal australien qui passe la somme de contrôle.](../media/DLP-create-test-tune-email-test2.png)

L’e-mail du rapport d’incident inclut le type d’informations sensibles détectées, le nombre d’instances détectées et le niveau de confiance de la détection.

![Rapport d’incident montrant le numéro de fichier fiscal détecté.](../media/DLP-create-test-tune-email-incident-report.png)

Si vous laissez votre stratégie DLP en mode test et analysez les e-mails de rapport d’incident, vous pouvez commencer à avoir une idée de la précision de la stratégie DLP et de son efficacité lorsqu’elle sera appliquée. En plus des rapports d’incident, vous pouvez [utiliser les rapports DLP](view-the-dlp-reports.md) pour afficher une vue agrégée des correspondances de stratégie dans votre locataire.

## <a name="tune-a-dlp-policy"></a>Régler une stratégie DLP

Lorsque vous analysez vos résultats de stratégie, vous souhaiterez peut-être apporter des ajustements au comportement des stratégies. En guise d’exemple simple, vous pouvez déterminer qu’un TFN dans un e-mail n’est pas un problème (je pense qu’il l’est toujours, mais nous allons l’utiliser pour la démonstration), mais deux instances ou plus sont un problème. Plusieurs instances peuvent être un scénario risqué, tel qu’un employé qui envoie par e-mail une exportation CSV de la base de données RH à une partie externe, par exemple un service de comptabilité externe. Certainement quelque chose que vous préféreriez détecter et bloquer.

Dans le Centre de conformité, vous pouvez modifier une stratégie existante pour ajuster le comportement.

![Option permettant de modifier la stratégie.](../media/DLP-create-test-tune-edit-policy.png)
 
Vous pouvez ajuster les paramètres d’emplacement afin que la stratégie soit appliquée uniquement à des charges de travail spécifiques ou à des sites et comptes spécifiques.

![Options permettant de choisir des emplacements spécifiques.](../media/DLP-create-test-tune-edit-locations.png)

Vous pouvez également ajuster les paramètres de stratégie et modifier les règles pour mieux répondre à vos besoins.

![Option permettant de modifier la règle.](../media/DLP-create-test-tune-edit-rule.png)

Lorsque vous modifiez une règle dans une stratégie DLP, vous pouvez modifier :

- Conditions, notamment le type et le nombre d’instances de données sensibles qui déclencheront la règle.
- Actions effectuées, telles que la restriction de l’accès au contenu.
- Notifications utilisateur, qui sont des conseils de stratégie qui sont affichés à l’utilisateur dans son client de messagerie ou navigateur web.
- Les remplacements d’utilisateur déterminent si les utilisateurs peuvent choisir de continuer le partage de leurs e-mails ou fichiers de toute façon.
- Rapports d’incident, pour avertir les administrateurs.

![Options permettant de modifier des parties d’une règle.](../media/DLP-create-test-tune-editing-options.png)

Pour cette démonstration, j’ai ajouté des notifications utilisateur à la stratégie (faites attention de le faire sans formation adéquate de sensibilisation des utilisateurs) et j’ai permis aux utilisateurs de remplacer la stratégie par une justification métier ou en la signalant comme un faux positif. Vous pouvez également personnaliser le texte de l’e-mail et du conseil de stratégie si vous souhaitez inclure des informations supplémentaires sur les stratégies de votre organisation, ou inviter les utilisateurs à contacter le support technique s’ils ont des questions.

![Options pour les notifications et remplacements d’utilisateurs.](../media/DLP-create-test-tune-user-notifications.png)

La stratégie contient deux règles pour la gestion des volumes élevés et des volumes faibles. Veillez donc à modifier les deux avec les actions souhaitées. Il s’agit d’une occasion de traiter les cas différemment en fonction de leurs caractéristiques. Par exemple, vous pouvez autoriser les remplacements pour les violations de volume faible, mais pas les remplacements pour les violations de volume élevé.

![Une règle pour un volume élevé et une règle pour un faible volume.](../media/DLP-create-test-tune-two-rules.png)

En outre, si vous souhaitez bloquer ou restreindre l’accès au contenu qui est en violation de la stratégie, vous devez configurer une action sur la règle pour ce faire.

![Option permettant de restreindre l’accès au contenu.](../media/DLP-create-test-tune-restrict-access-action.png)

Après avoir enregistré ces modifications dans les paramètres de stratégie, je dois également revenir à la page des paramètres principaux de la stratégie et activer l’option permettant d’afficher des conseils de stratégie aux utilisateurs pendant que la stratégie est en mode test. Il s’agit d’un moyen efficace d’introduire des stratégies DLP à vos utilisateurs finaux et d’effectuer une formation de sensibilisation des utilisateurs, sans risquer trop de faux positifs qui ont un impact sur leur productivité.

![Option permettant d’afficher les conseils de stratégie en mode test.](../media/DLP-create-test-tune-show-policy-tips.png)

Côté serveur (ou côté cloud si vous préférez), la modification peut ne pas prendre effet immédiatement, en raison de différents intervalles de traitement. Si vous apportez une modification de stratégie DLP qui affichera de nouveaux conseils de stratégie à un utilisateur, l’utilisateur risque de ne pas voir les modifications prendre effet immédiatement dans son client Outlook, qui vérifie les modifications de stratégie toutes les 24 heures. Si vous souhaitez accélérer les tests, vous pouvez utiliser ce correctif de Registre pour [effacer le dernier horodatage de téléchargement de la clé PolicyNudges](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook télécharge les dernières informations de stratégie la prochaine fois que vous le redémarrez et commencez à composer un e-mail.

Si vous avez activé les conseils de stratégie, l’utilisateur commence à voir les conseils dans Outlook et peut vous signaler des faux positifs lorsqu’ils se produisent.

![Conseil de stratégie avec option pour signaler un faux positif.](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Examiner les faux positifs

Les modèles de stratégie DLP ne sont pas parfaits dès le départ. Il est probable que vous trouverez des faux positifs qui se produisent dans votre environnement, c’est pourquoi il est si important de faciliter votre chemin dans un déploiement DLP, en prenant le temps de tester et de paramétrer correctement vos stratégies.

Voici un exemple de faux positif. Cet e-mail est inoffensif. L’utilisateur fournit son numéro de téléphone mobile à une personne et inclut sa signature par e-mail.

![E-mail montrant des informations de faux positifs.](../media/DLP-create-test-tune-false-positive-email.png)
 
Mais l’utilisateur voit un conseil de stratégie l’avertissant que l’e-mail contient des informations sensibles, plus précisément, un numéro de permis de conduire australien.

![Option permettant de signaler un faux positif dans l’info-bulle de stratégie.](../media/DLP-create-test-tune-policy-tip-closeup.png)

L’utilisateur peut signaler le faux positif et l’administrateur peut examiner pourquoi il s’est produit. Dans l’e-mail du rapport d’incident, l’e-mail est marqué comme un faux positif.

![Rapport d’incident montrant un faux positif.](../media/DLP-create-test-tune-false-positive-incident-report.png)

Ce cas de permis de conduire est un bon exemple à explorer. La raison pour laquelle ce faux positif s’est produit est que le type « Australian Driver’s License » est déclenché par n’importe quelle chaîne à 9 chiffres (même si elle fait partie d’une chaîne à 10 chiffres), dans un délai de 300 caractères à proximité des mots clés « Sydney nsw » (non sensible à la casse). Il est donc déclenché par le numéro de téléphone et la signature électronique, uniquement parce que l’utilisateur se trouve à Sydney.


L’une des options consiste à supprimer le type d’informations sur le permis de conduire australien de la stratégie. Il est là-bas, car il fait partie du modèle de stratégie DLP, mais nous ne sommes pas obligés de l’utiliser. Si vous ne vous intéressez qu’aux numéros de fichier fiscal et non aux permis de conduire, vous pouvez simplement le supprimer. Par exemple, vous pouvez la supprimer de la règle de faible volume dans la stratégie, mais la laisser dans la règle de volume élevé afin que les listes de plusieurs licences de pilotes soient toujours détectées.
 
Une autre option consiste à augmenter le nombre d’instances afin qu’un faible volume de licences de pilote soit détecté uniquement lorsqu’il existe plusieurs instances.

![Option permettant de modifier le nombre d’instances.](../media/DLP-create-test-tune-edit-instance-count.png)

En plus de modifier le nombre d’instances, vous pouvez également ajuster la précision de la correspondance (ou le niveau de confiance). Si votre type d’informations sensibles a plusieurs modèles, vous pouvez ajuster la précision de la correspondance dans votre règle afin que votre règle corresponde uniquement à des modèles spécifiques. Par exemple, pour réduire les faux positifs, vous pouvez définir la précision de correspondance de votre règle afin qu’elle corresponde uniquement au modèle avec le niveau de confiance le plus élevé. Pour plus d’informations sur les niveaux de confiance, consultez [Comment utiliser le niveau de confiance pour régler vos règles](data-loss-prevention-policies.md#match-accuracy).

Enfin, si vous souhaitez obtenir encore un peu plus d’avancées, vous pouvez personnaliser n’importe quel type d’informations sensibles . Par exemple, vous pouvez supprimer « Sydney NSW » de la liste des mots clés pour le [numéro de licence du pilote australien, afin d’éliminer](sensitive-information-type-entity-definitions.md#australia-drivers-license-number) le faux positif déclenché ci-dessus. Pour savoir comment procéder à l’aide de XML et PowerShell, consultez [la personnalisation d’un type d’informations sensibles intégré](customize-a-built-in-sensitive-information-type.md).

## <a name="turn-on-a-dlp-policy"></a>Activer une stratégie DLP

Lorsque vous êtes heureux que votre stratégie DLP détecte avec précision et efficacité les types d’informations sensibles et que vos utilisateurs finaux sont prêts à gérer les stratégies en place, vous pouvez activer la stratégie.

![Option permettant d’activer la stratégie.](../media/DLP-create-test-tune-turn-on-policy.png)
 
Si vous attendez de voir quand la stratégie prendra effet, [connectez-vous à Security & Compliance PowerShell](/powershell/exchange/connect-to-scc-powershell) et [exécutez l’applet de commande Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy) pour voir DistributionStatus.

 ```powershell
 Get-DlpCompliancePolicy "Testing -Australia PII" -DistributionDetail | Select distributionstatus
 ```
Après avoir activé la stratégie DLP, vous devez exécuter vos propres tests finaux pour vous assurer que les actions de stratégie attendues se produisent. Si vous essayez de tester des éléments tels que les données de carte de crédit, il existe des sites web en ligne avec des informations sur la façon de générer des exemples de carte de crédit ou d’autres informations personnelles qui passent des sommes de contrôle et déclenchent vos stratégies.

Les stratégies qui autorisent les remplacements d’utilisateur présentent cette option à l’utilisateur dans le cadre de l’info-bulle de stratégie.

![Conseil de stratégie qui autorise le remplacement par l’utilisateur.](../media/DLP-create-test-tune-override-option.png)

Les stratégies qui limitent le contenu présentent l’avertissement à l’utilisateur dans le cadre de l’info-bulle de stratégie et l’empêchent d’envoyer l’e-mail.

![Conseil de stratégie indiquant que le contenu est restreint.](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Résumé

Les stratégies de protection contre la perte de données sont utiles pour les organisations de tous types. Le test de certaines stratégies DLP est un exercice à faible risque en raison du contrôle que vous avez sur des éléments tels que les conseils de stratégie, les remplacements d’utilisateurs finaux et les rapports d’incidents. Vous pouvez tester tranquillement certaines stratégies DLP pour voir quel type de violations se produisent déjà dans votre organisation, puis élaborer des stratégies avec de faibles taux de faux positifs, informer vos utilisateurs sur ce qui est autorisé et non autorisé, puis déployer vos stratégies DLP auprès de l’organisation.
