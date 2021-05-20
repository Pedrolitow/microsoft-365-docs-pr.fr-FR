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
description: Dans cet article, vous apprendrez à créer, tester et régler une stratégie DLP en fonction de vos besoins organisationnels.
ms.openlocfilehash: 3b7f74605c8a825bb03244f3a861ad3cca8f550d
ms.sourcegitcommit: 0936f075a1205b8f8a71a7dd7761a2e2ce6167b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/19/2021
ms.locfileid: "52572572"
---
# <a name="create-test-and-tune-a-dlp-policy"></a>Création, test et réglage d’une stratégie DLP

La prévention des pertes de données (DLP) vous aide à prévenir le partage involontaire ou accidentel d’informations sensibles.

DLP examine les messages électroniques et les fichiers pour obtenir des informations sensibles, comme un numéro de carte de crédit. À l’aide de DLP, vous pouvez détecter des informations sensibles et prendre des mesures telles que :

- Enregistrez l’événement à des fins d’audit
- Affichez un avertissement à l’utilisateur final qui envoie l’e-mail ou partage le fichier
- Bloquer activement le partage d’e-mails ou de fichiers

## <a name="permissions"></a>Autorisations

Les membres de votre équipe de mise en conformité qui créeront des stratégies DLP ont besoin des autorisations d’accès au Centre de conformité. Par défaut, votre administrateur locataire aura accès peut donner accès aux agents de conformité et à d’autres personnes. Procédez comme suit :
  
1. Créer un groupe dans Microsoft 365 et d’y ajouter des responsables de la mise en conformité.
    
2. Créer un groupe de rôles sur la page **Autorisations** du Centre de sécurité et de conformité. 

3. Lors de la création du groupe de rôle, utilisez la section **Choisir** les rôles pour ajouter le rôle suivant au groupe de rôle : **Gestion de la conformité du DLP.**
    
4. Utilisez la section **Choisir des membres** pour ajouter le groupe Microsoft 365 que vous avez créé précédemment au groupe de rôles.

Utilisez le **rôle de gestion de la conformité du DLP** uniquement pour créer un groupe de rôle avec des privilèges de vue uniquement aux politiques DLP et aux rapports DLP.

Pour plus d’informations, voir [Give users access to the Office 365 Compliance Center](../security/office-365-security/grant-access-to-the-security-and-compliance-center.md).
  
Ces autorisations sont nécessaires pour créer et appliquer une stratégie DLP et non pour faire respecter les politiques.

## <a name="how-sensitive-information-is-detected-by-dlp"></a>Comment les informations sensibles sont détectées par DLP

DLP trouve des informations sensibles par correspondance de modèle d’expression régulière (RegEx), en combinaison avec d’autres indicateurs tels que la proximité de certains mots clés avec les modèles correspondants. Par exemple, un numéro de carte de crédit VISA a 16 chiffres. Mais, ces chiffres peuvent être écrits de différentes façons, comme 1111-1111-1111-1111, 1111 1111 1111 1111, ou 111111111111111111111.

N’importe quelle chaîne à 16 chiffres n’est pas nécessairement un numéro de carte de crédit, il peut s’agir d’un numéro de billet provenant d’un système de service d’assistance ou d’un numéro de série d’un morceau de matériel. Pour faire la différence entre un numéro de carte de crédit et une chaîne inoffensive à 16 chiffres, un calcul est effectué (checksum) pour confirmer que les numéros correspondent à un modèle connu des différentes marques de cartes de crédit.

Si DLP trouve des mots clés tels que « VISA » ou « AMEX », valeurs proches de la date qui pourraient être la date d’expiration de la carte de crédit, DLP utilise également ces données pour l’aider à décider si la chaîne est un numéro de carte de crédit ou non.

En d’autres termes, DLP est assez intelligent pour reconnaître la différence entre ces deux chaînes de texte dans un e-mail:

- « Pouvez-vous me commander un nouvel ordinateur portable. Utilisez mon numéro visa 1111-1111-1111-1111, expiration 11/22, et envoyez-moi la date de livraison estimée quand vous l’avez.
- « Mon numéro de série d’ordinateur portable est 2222-2222-2222-2222 et il a été acheté le 11/2010. Soit dit en passant, mon visa de voyage est-il encore approuvé?

Consultez les [définitions d’entités de type d’information](sensitive-information-type-entity-definitions.md) sensible qui expliquent comment chaque type d’information est détecté.

## <a name="where-to-start-with-data-loss-prevention"></a>Par où commencer par la prévention des pertes de données

Lorsque les risques de fuite de données ne sont pas tout à fait évidents, il est difficile de déterminer où exactement vous devriez commencer par implémenter DLP. Heureusement, les stratégies DLP peuvent être exécutés en « mode test », ce qui vous permet d’évaluer leur efficacité et leur précision avant de les activer.

Les stratégies DLP pour Exchange Online peuvent être gérées par l’intermédiaire du Exchange’administration. Mais vous pouvez configurer des stratégies DLP pour toutes les charges de travail via le Security & Compliance Center, c’est donc ce que je vais utiliser pour les démonstrations dans cet article. Dans le Security & Compliance Center, vous trouverez les stratégies DLP dans le cadre de la politique **de prévention des pertes de**  >  **données**. Choisissez **Créer une stratégie** pour commencer.

Microsoft 365 fournit une gamme de modèles [de stratégie DLP que vous](what-the-dlp-policy-templates-include.md) pouvez utiliser pour créer des stratégies. Disons que vous êtes une entreprise australienne. Vous pouvez filtrer les modèles sur l’Australie, et choisir financière, médicale et de santé, et la vie privée.

![Option pour choisir le pays ou la région](../media/DLP-create-test-tune-choose-country.png)

Pour cette démonstration, je vais choisir australien personnellement identifiables informations (PII) Données, qui comprend les types d’informations de numéro de fichier fiscal australien (TFN) et numéro de permis de conduire.

![Option pour choisir un modèle de stratégie](../media/DLP-create-test-tune-choose-policy-template.png)

Donnez un nom à votre nouvelle politique DLP. Le nom par défaut correspondra au modèle de stratégie DLP, mais vous devez choisir votre propre nom plus descriptif, car plusieurs stratégies peuvent être créées à partir du même modèle.

![Possibilité de nommer votre police](../media/DLP-create-test-tune-name-policy.png)

Choisissez les emplacements sur qui la politique s’appliquera. Les stratégies DLP peuvent s’appliquer Exchange Online, SharePoint en ligne et OneDrive Entreprise. Je vais laisser cette politique configurée pour s’appliquer à tous les emplacements.

![Possibilité de choisir tous les emplacements](../media/DLP-create-test-tune-choose-locations.png)

Lors de la première **étape de Paramètres,** il suffit d’accepter les défauts pour l’instant. Vous pouvez personnaliser les stratégies DLP, mais les valeurs par défaut sont un bon point de départ.

![Options pour personnaliser le type de contenu à protéger](../media/DLP-create-test-tune-default-customization-settings.png)

Après avoir cliqué sur Suivant,** vous serez présenté avec une page plus **de stratégie Paramètres** avec plus d’options de personnalisation. Pour une stratégie que vous testez, voici où vous pouvez commencer à faire quelques ajustements.

- J’ai désactivé les conseils de politique pour l’instant, ce qui est une étape raisonnable à prendre si vous êtes juste tester les choses et ne veulent pas afficher quoi que ce soit aux utilisateurs encore. Les conseils de stratégie affichent des avertissements aux utilisateurs qu’ils sont sur le point de violer une stratégie DLP. Par exemple, un utilisateur Outlook verra un avertissement que le fichier qu’il a joint contient des numéros de carte de crédit et fera rejeter son e-mail. Le but des conseils de stratégie est d’arrêter le comportement non conforme avant qu’il ne se produise.
- J’ai également réduit le nombre d’instances de 10 à 1, de sorte que cette politique détectera tout partage de données PII australiennes, pas seulement le partage en vrac des données.
- J’ai également ajouté un autre destinataire à l’e-mail rapport d’incident.

![Paramètres de stratégie supplémentaires](../media/DLP-create-test-tune-more-policy-settings.png)

Enfin, j’ai configuré cette stratégie pour exécuter en mode test initialement. Notez qu’il ya aussi une option ici pour désactiver les conseils de stratégie tout en mode test. Cela vous donne la flexibilité d’avoir des conseils de stratégie activés dans la stratégie, mais ensuite décider s’il faut les afficher ou les supprimer pendant votre test.

![Option pour tester la politique d’abord](../media/DLP-create-test-tune-test-mode.png)

Sur l’écran d’examen final, cliquez **sur Créer** pour terminer la création de la stratégie.

## <a name="test-a-dlp-policy"></a>Testez une stratégie DLP

Votre nouvelle politique DLP commencera à prendre effet dans un délai d’environ 1 heure. Vous pouvez vous asseoir et attendre qu’il soit déclenché par l’activité normale de l’utilisateur, ou vous pouvez essayer de le déclencher vous-même. Plus tôt, j’ai [lié à des définitions d’entité de type d’information](sensitive-information-type-entity-definitions.md)sensible , qui vous fournit des informations sur la façon de déclencher des correspondances DLP.

À titre d’exemple, la politique du DLP que j’ai créée pour cet article détectera les numéros de fichiers fiscaux australiens (TFN). Selon la documentation, la correspondance est basée sur les critères suivants.

![Documentation sur le numéro de fichier fiscal de l’Australie](../media/DLP-create-test-tune-Australia-Tax-File-Number-doc.png)
 
Pour démontrer la détection TFN d’une manière plutôt brutale, un e-mail avec les mots « numéro de fichier fiscal » et une chaîne à neuf chiffres à proximité naviguera à travers sans aucun problème. La raison pour laquelle il ne déclenche pas la politique DLP est que la chaîne à neuf chiffres doit passer le checksum qui indique qu’il s’agit d’un TFN valide et pas seulement une chaîne inoffensive de nombres.

![Numéro de fichier fiscal de l’Australie qui ne passe pas checksum](../media/DLP-create-test-tune-email-test1.png)

En comparaison, un e-mail avec les mots « numéro de fichier fiscal » et un TFN valide qui passe le checksum déclenchera la politique. Pour la petite histoire ici, le TFN que j’utilise a été tiré d’un site Web qui génère valide, mais pas authentique, TFNs. Ces sites sont utiles parce que l’une des erreurs les plus courantes lors de l’essai d’une stratégie DLP est l’utilisation d’un faux numéro qui n’est pas valide et ne passera pas le checksum (et ne déclenchera donc pas la stratégie).

![Numéro de fichier fiscal de l’Australie qui passe le chèque](../media/DLP-create-test-tune-email-test2.png)

Le courriel du rapport d’incident comprend le type d’informations sensibles qui ont été détectées, le nombre d’instances détectées et le niveau de confiance de la détection.

![Rapport d’incident montrant le numéro de fichier fiscal détecté](../media/DLP-create-test-tune-email-incident-report.png)

Si vous laissez votre stratégie DLP en mode test et analysez les e-mails de rapport d’incident, vous pouvez commencer à avoir une idée de l’exactitude de la stratégie DLP et de son efficacité lorsqu’elle sera appliquée. En plus des rapports d’incident, vous pouvez [utiliser les rapports DLP pour](view-the-dlp-reports.md) afficher une vue agrégée des correspondances de stratégie entre votre locataire.

## <a name="tune-a-dlp-policy"></a>Régler une stratégie DLP

Lorsque vous analysez vos résultats de stratégie, vous voudrez peut-être apporter quelques ajustements au comportement des stratégies. À titre d’exemple simple, vous pouvez déterminer qu’un TFN dans un e-mail n’est pas un problème (je pense qu’il est toujours, mais allons-y pour des raisons de démonstration), mais deux cas ou plus sont un problème. Plusieurs cas peuvent être un scénario risqué, comme un employé qui envoyant un envoi par courriel d’une base de données RH à une partie externe, par exemple un service comptable externe. Certainement quelque chose que vous préférez détecter et bloquer.

Dans le centre de conformité, vous pouvez modifier une stratégie existante pour ajuster le comportement.

![Possibilité de modifier la stratégie](../media/DLP-create-test-tune-edit-policy.png)
 
Vous pouvez ajuster les paramètres de localisation de sorte que la stratégie ne soit appliquée qu’à des charges de travail spécifiques, ou à des sites et comptes spécifiques.

![Options pour choisir des emplacements spécifiques](../media/DLP-create-test-tune-edit-locations.png)

Vous pouvez également ajuster les paramètres de stratégie et modifier les règles pour mieux répondre à vos besoins.

![Option de modification de la règle](../media/DLP-create-test-tune-edit-rule.png)

Lors de l’édition d’une règle dans une stratégie DLP, vous pouvez modifier :

- Les conditions, y compris le type et le nombre d’instances de données sensibles qui déclencheront la règle.
- Les mesures prises, telles que la restriction de l’accès au contenu.
- Notifications d’utilisateurs, qui sont des conseils de stratégie qui sont affichés à l’utilisateur dans leur client de messagerie ou navigateur Web.
- Les dérogations de l’utilisateur déterminent si les utilisateurs peuvent choisir de procéder à leur e-mail ou partage de fichiers de toute façon.
- Rapports d’incident, pour aviser les administrateurs.

![Options pour modifier des parties d’une règle](../media/DLP-create-test-tune-editing-options.png)

Pour cette démonstration, j’ai ajouté des notifications utilisateur à la politique (attention à le faire sans formation adéquate de sensibilisation des utilisateurs), et a permis aux utilisateurs de passer outre la politique avec une justification d’entreprise ou en la signalant comme un faux positif. Vous pouvez également personnaliser le texte des conseils d’e-mail et de stratégie si vous souhaitez inclure des informations supplémentaires sur les politiques de votre organisation, ou inciter les utilisateurs à contacter le support s’ils ont des questions.

![Options pour les notifications et les dérogations des utilisateurs](../media/DLP-create-test-tune-user-notifications.png)

La stratégie contient deux règles pour le traitement du volume élevé et du faible volume, alors assurez-vous de modifier les deux avec les actions que vous voulez. C’est l’occasion de traiter les cas différemment selon leurs caractéristiques. Par exemple, vous pouvez autoriser les dérogations pour les violations de faible volume, mais ne pas autoriser les dérogations pour les violations de volume élevé.

![Une règle pour un volume élevé et une règle pour un faible volume](../media/DLP-create-test-tune-two-rules.png)

En outre, si vous souhaitez réellement bloquer ou restreindre l’accès au contenu qui est en violation de la stratégie, vous devez configurer une action sur la règle pour le faire.

![Possibilité de restreindre l’accès au contenu](../media/DLP-create-test-tune-restrict-access-action.png)

Après avoir sauve ces modifications dans les paramètres de stratégie, j’ai également besoin de revenir à la page paramètres principaux de la stratégie et permettre la possibilité d’afficher des conseils de stratégie aux utilisateurs pendant que la stratégie est en mode de test. Il s’agit d’un moyen efficace d’introduire des politiques DLP à vos utilisateurs finaux, et de faire de la formation de sensibilisation des utilisateurs, sans risquer trop de faux positifs qui ont un impact sur leur productivité.

![Possibilité d’afficher des conseils de stratégie en mode test](../media/DLP-create-test-tune-show-policy-tips.png)

Du côté serveur (ou côté cloud si vous préférez), la modification peut ne pas prendre effet immédiatement, en raison de divers intervalles de traitement. Si vous modifiez une stratégie DLP qui affichera de nouveaux conseils de stratégie à un utilisateur, il se peut que les modifications ne prennent pas effet immédiatement dans son client Outlook, qui vérifie les modifications apportées à la stratégie toutes les 24 heures. Si vous souhaitez accélérer les choses pour les tests, vous pouvez utiliser ce correctif de registre pour [effacer le dernier horodatage de téléchargement de la clé PolicyNudges](https://support.microsoft.com/en-au/help/2823261/changes-to-a-data-loss-prevention-policy-don-t-take-effect-in-outlook?__hstc=18650278.46377037dc0a82baa8a30f0ef07a7b2f.1538687978676.1538693509953.1540315763430.3&__hssc=18650278.1.1540315763430&__hsfp=3446956451). Outlook télécharger les dernières informations de politique la prochaine fois que vous les redémarrez et commencerez à composer un message électronique.

Si vous avez activé des conseils de stratégie, l’utilisateur commencera à voir les conseils dans Outlook, et peut vous signaler de faux positifs lorsqu’ils se produisent.

![Conseil de politique avec option pour signaler les faux positifs](../media/DLP-create-test-tune-policy-tip-in-outlook.png)

## <a name="investigate-false-positives"></a>Enquêter sur les faux positifs

Les modèles de stratégie DLP ne sont pas parfaits tout droit sortis de la boîte. Il est probable que vous trouverez quelques faux positifs qui se produisent dans votre environnement, c’est pourquoi il est si important de faciliter votre chemin dans un déploiement DLP, en prenant le temps de tester et d’accorder adéquatement vos politiques.

Voici un exemple de faux positif. Cet e-mail est tout à fait inoffensif. L’utilisateur fournit son numéro de téléphone mobile à quelqu’un, y compris sa signature e-mail.

![E-mail montrant de fausses informations positives](../media/DLP-create-test-tune-false-positive-email.png)
 
Mais l’utilisateur voit un conseil de stratégie les avertissant que l’e-mail contient des informations sensibles, en particulier, un numéro de permis de conduire australien.

![Possibilité de signaler un faux positif dans le conseil de politique](../media/DLP-create-test-tune-policy-tip-closeup.png)

L’utilisateur peut signaler le faux positif, et l’administrateur peut examiner pourquoi il s’est produit. Dans le courriel du rapport d’incident, l’e-mail est signalé comme un faux positif.

![Rapport d’incident montrant faux positif](../media/DLP-create-test-tune-false-positive-incident-report.png)

Ce cas de permis de conduire est un bon exemple à creuser. La raison pour laquelle ce faux positif s’est produit est que le type « Australian Driver’s License » sera déclenché par n’importe quelle chaîne à 9 chiffres (même celle qui fait partie d’une chaîne à 10 chiffres), dans un rayon de 300 caractères à proximité des mots clés « Sydney nsw » (pas sensible au cas). Donc, il est déclenché par le numéro de téléphone et la signature e-mail, seulement parce que l’utilisateur se trouve être à Sydney.


Une option consiste à supprimer le type d’information sur le permis de conduire australien de la police. C’est là parce que cela fait partie du modèle de politique DLP, mais nous ne sommes pas obligés de l’utiliser. Si vous êtes seulement intéressé par les numéros de fichiers fiscaux et non pas les permis de conduire, vous pouvez simplement le supprimer. Par exemple, vous pouvez le supprimer de la règle du faible volume dans la stratégie, mais le laisser dans la règle du volume élevé de sorte que les listes de permis de conduire multiples sont toujours détectées.
 
Une autre option consiste à augmenter le nombre d’instances, de sorte qu’un faible volume de permis de conduire n’est détecté que lorsqu’il y a plusieurs instances.

![Possibilité de modifier le nombre d’instances](../media/DLP-create-test-tune-edit-instance-count.png)

En plus de modifier le nombre d’instances, vous pouvez également ajuster la précision du match (ou le niveau de confiance). Si votre type d’information sensible a plusieurs modèles, vous pouvez ajuster la précision de correspondance dans votre règle, de sorte que votre règle ne correspond qu’à des modèles spécifiques. Par exemple, pour aider à réduire les faux positifs, vous pouvez définir l’exactitude de correspondance de votre règle de sorte qu’elle corresponde uniquement au modèle avec le niveau de confiance le plus élevé. Pour plus d’informations sur les niveaux de confiance, [voir Comment utiliser le niveau de confiance pour régler vos règles](data-loss-prevention-policies.md#match-accuracy).

Enfin, si vous voulez obtenir encore un peu plus avancé, vous pouvez personnaliser n’importe quel type d’information sensible - par exemple, vous pouvez supprimer « Sydney NSW » de la liste des mots clés pour le numéro de [permis de conduire de l’Australie](sensitive-information-type-entity-definitions.md#australia-drivers-license-number), pour éliminer le faux positif déclenché ci-dessus. Pour apprendre à le faire en utilisant XML et PowerShell, consultez [la personnalisation d’un type d’information sensible intégré.](customize-a-built-in-sensitive-information-type.md)

## <a name="turn-on-a-dlp-policy"></a>Activer une politique DLP

Lorsque vous êtes heureux que votre stratégie DLP détecte avec précision et efficacité les types d’informations sensibles, et que vos utilisateurs finaux sont prêts à faire face aux stratégies en place, alors vous pouvez activer la stratégie.

![Option pour activer la politique](../media/DLP-create-test-tune-turn-on-policy.png)
 
Si vous attendez de voir quand la stratégie entrera en vigueur, [Connecter à Security & Compliance Center PowerShell](/powershell/exchange/connect-to-scc-powershell) et [exécutez le cmdlet Get-DlpCompliancePolicy](/powershell/module/exchange/get-dlpcompliancepolicy) pour voir le DistributionStatus.

![Cmdlet en cours d’exécution dans PowerShell](../media/DLP-create-test-tune-PowerShell.png)

Après avoir mis en place la stratégie DLP, vous devez effectuer vos propres tests finaux pour vous assurer que les mesures politiques attendues se produisent. Si vous essayez de tester des choses comme les données de carte de crédit, il existe des sites Web en ligne avec des informations sur la façon de générer des exemples de carte de crédit ou d’autres informations personnelles qui passeront des chèques et déclencheront vos politiques.

Les stratégies qui permettent aux utilisateurs de passer outre présenteront cette option à l’utilisateur dans le cadre de la pointe de stratégie.

![Conseil de stratégie qui permet à l’utilisateur de passer outre](../media/DLP-create-test-tune-override-option.png)

Les stratégies qui restreignent le contenu présenteront l’avertissement à l’utilisateur dans le cadre de la pointe de stratégie et l’empêcheront d’envoyer l’e-mail.

![Conseil de stratégie selon qui le contenu est restreint](../media/DLP-create-test-tune-restrict-warning.png)

## <a name="summary"></a>Résumé

Les politiques de prévention des pertes de données sont utiles pour les organisations de tous types. Tester certaines stratégies DLP est un exercice à faible risque en raison du contrôle que vous avez sur des choses comme des conseils de stratégie, des remplacements d’utilisateurs finaux et des rapports d’incident. Vous pouvez tester discrètement certaines stratégies DLP pour voir quel type de violations se produisent déjà dans votre organisation, puis élaborer des politiques avec de faibles taux de faux positifs, éduquer vos utilisateurs sur ce qui est autorisé et non autorisé, puis déployer vos politiques DLP à l’organisation.