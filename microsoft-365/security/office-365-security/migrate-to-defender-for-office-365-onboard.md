---
title: 'Migrer vers Microsoft Defender pour Office 365 Phase 3 : Intégration'
f1.keywords:
- NOCSH
ms.author: chrisda
author: chrisda
manager: dansimp
audience: Admin
ms.date: ''
ms.topic: conceptual
ms.localizationpriority: medium
search.appverid:
- MET150
- MOE150
ms.collection:
- M365-security-compliance
- m365initiative-defender-office365
ms.custom: migrationguides
description: Effectuer les étapes de migration d’un service ou d’un appareil de protection tiers vers Microsoft Defender pour Office 365 protection.
ms.technology: mdo
ms.prod: m365-security
ms.openlocfilehash: a40ee22ee843d250c90a8b03526ab61fe3ad56f6
ms.sourcegitcommit: e110f00dc6949a7a1345187375547beeb64225b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/06/2021
ms.locfileid: "60804640"
---
# <a name="migrate-to-microsoft-defender-for-office-365---phase-3-onboard"></a>Migrer vers Microsoft Defender pour Office 365 - Phase 3 : Intégration

**S’applique à**
- [Microsoft Defender pour Office 365 : offre 1 et offre 2](defender-for-office-365.md)

<br>

|[![Phase 1 : Préparer.](../../media/phase-diagrams/prepare.png)](migrate-to-defender-for-office-365-prepare.md) <br> [Phase 1 : préparation](migrate-to-defender-for-office-365-prepare.md)|[![Phase 2 : Configurer.](../../media/phase-diagrams/setup.png)](migrate-to-defender-for-office-365-setup.md) <br> [Phase 2 : configuration](migrate-to-defender-for-office-365-setup.md)|![Phase 3 : Intégration.](../../media/phase-diagrams/onboard.png) <br> Phase 3 : intégration|
|---|---|---|
|||*Vous êtes là !*|

Bienvenue dans **la phase 3 : intégration de** votre migration vers Microsoft Defender pour **[Office 365](migrate-to-defender-for-office-365.md#the-migration-process)**! Cette phase de migration comprend les étapes suivantes :

1. [Commencer l’intégration de la sécurité Teams](#step-1-begin-onboarding-security-teams)
2. [(Facultatif) Exempter les utilisateurs pilotes du filtrage par votre service de protection existant](#step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service)
3. [Régler la veille contre l’usurpation d’informations](#step-3-tune-spoof-intelligence)
4. [Régler la protection contre l’emprunt d’identité et l’intelligence des boîtes aux lettres](#step-4-tune-impersonation-protection-and-mailbox-intelligence)
5. [Utiliser les données des envois d’utilisateurs pour mesurer et ajuster](#step-5-use-data-from-user-submissions-to-measure-and-adjust)
6. [(Facultatif) Ajouter d’autres utilisateurs à votre projet pilote et itérer](#step-6-optional-add-more-users-to-your-pilot-and-iterate)
7. [Étendre Microsoft 365 protection à tous les utilisateurs et désactiver la règle de flux de messagerie SCL=-1](#step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule)
8. [Changer vos enregistrements MX](#step-8-switch-your-mx-records)

## <a name="step-1-begin-onboarding-security-teams"></a>Étape 1 : commencer l’intégration de la sécurité Teams

Si votre organisation dispose d’une équipe de réponse à la sécurité, il est maintenant temps de commencer à intégrer Microsoft Defender pour Office 365 dans vos processus de réponse, y compris les systèmes de gestion des tickets. Il s’agit d’un sujet entier en lui-même, mais il est parfois ignoré. Si l’équipe de réponse à la sécurité est impliquée tôt, votre organisation est prête à gérer les menaces lorsque vous changez d’enregistrement MX. La réponse aux incidents doit être bien équipé pour gérer les tâches suivantes :

- Découvrez les nouveaux outils et intégrez-les aux flux existants. Par exemple :
  - La gestion par l’administrateur des messages mis en quarantaine est importante. Pour obtenir des instructions, voir Gérer les messages et fichiers mis en [quarantaine en tant qu’administrateur.](manage-quarantined-messages-and-files.md)
  - Le suivi des messages vous permet de voir ce qui est arrivé aux messages à mesure qu’ils entrent ou quittent Microsoft 365. Pour plus d’informations, voir suivi des messages dans [le centre d’administration Exchange moderne dans Exchange Online](/exchange/monitoring/trace-an-email-message/message-trace-modern-eac).
- Identifiez les risques qui ont pu être laissés dans l’organisation.
- Régler et personnaliser les [alertes pour](../../compliance/alert-policies.md) les processus organisationnels.
- Gérez la file d’attente des incidents et remédiez aux risques potentiels.

Si votre organisation a acheté Microsoft Defender pour Office 365 Plan 2, elle doit commencer à se familiariser et à utiliser des fonctionnalités telles que l’Explorateur de menaces, la recherche avancée et les incidents. Pour obtenir des formations pertinentes, voir <https://aka.ms/mdoninja> .

Si votre équipe de réponse à la sécurité collecte et analyse les messages non filtrés, vous pouvez configurer une boîte aux lettres SecOps pour recevoir ces messages non filtrés. Pour obtenir des instructions, voir Configurer les boîtes aux lettres [SecOps dans la stratégie de remise avancée.](configure-advanced-delivery.md#use-the-microsoft-365-defender-portal-to-configure-secops-mailboxes-in-the-advanced-delivery-policy)

### <a name="siemsoar"></a>SIEM/SOUS-GROUPE

Pour plus d’informations sur l’intégration à votre SIEM/CASER, consultez les articles suivants :

- [Vue d’ensemble des API Microsoft 365 Defender](/microsoft-365/security/defender/api-overview)
- [API de diffusion en continu](/microsoft-365/security/defender/streaming-api)
- [API de recherche avancée de menaces](/microsoft-365/security/defender/api-advanced-hunting)
- [API d’incidents](/microsoft-365/security/defender/api-incident)

Si votre organisation ne dispose pas d’une équipe de réponse à la sécurité ou de flux de processus existants, vous pouvez utiliser ce moment pour vous familiariser avec les fonctionnalités de recherche et de réponse de base dans Defender pour Office 365. Pour plus d’informations, voir [Examen des menaces et réponse.](office-365-ti.md)

### <a name="rbac-roles"></a>Rôles RBAC

Les autorisations dans Defender pour Office 365 sont basées sur le contrôle d’accès basé sur un rôle (RBAC) et sont expliquées dans autorisations dans le [portail Microsoft 365 Defender.](permissions-microsoft-365-security-center.md) Voici les points importants à garder à l’esprit :

- Azure AD donnent des autorisations à toutes **les charges** de travail dans Microsoft 365. Par exemple, si vous ajoutez un utilisateur à l’administrateur de sécurité dans le portail Azure, il a des autorisations d’administrateur de sécurité partout.
- Les & de collaboration dans le portail Microsoft 365 Defender donnent des autorisations sur le portail Microsoft 365 Defender, le Centre de conformité Microsoft 365 et l’ancien Centre de sécurité & conformité. Par exemple, si vous ajoutez un utilisateur à l’administrateur de  sécurité dans le portail Microsoft 365 Defender, il n’a accès qu’au portail Microsoft 365 Defender, au Centre de conformité Microsoft 365 et au Centre de conformité des & de sécurité.
- De nombreuses fonctionnalités du portail Microsoft 365 Defender sont basées sur des cmdlets PowerShell Exchange Online et nécessitent donc l’appartenance à un groupe de rôles dans les rôles correspondants (techniquement, les groupes de rôles) dans Exchange Online (en particulier, pour l’accès au Exchange Online Cmdlets PowerShell).
- Il existe des rôles de collaboration de & de messagerie dans le portail Microsoft 365 Defender qui n’ont pas d’équivalent aux rôles Azure AD et qui sont importants pour les opérations de sécurité (par exemple, le rôle Aperçu et le rôle Recherche et purge).

En règle générale, seul un sous-ensemble de personnel de sécurité a besoin de droits supplémentaires pour télécharger des messages directement à partir des boîtes aux lettres des utilisateurs. Cela nécessite une autorisation supplémentaire que le lecteur de sécurité n’a pas par défaut.

## <a name="step-2-optional-exempt-pilot-users-from-filtering-by-your-existing-protection-service"></a>Étape 2 : (Facultatif) Exempter les utilisateurs pilotes du filtrage par votre service de protection existant

Bien que cette étape ne soit pas obligatoire, vous devez envisager de configurer vos utilisateurs pilotes pour qu’ils contournent le filtrage par votre service de protection existant. Cette action permet à Defender pour  Office 365 gérer toutes les tâches de filtrage et de protection des utilisateurs pilotes. Si vous n’exemptez pas vos utilisateurs pilotes de votre service de protection existant, Defender pour Office 365 fonctionne efficacement uniquement en cas d’erreurs de l’autre service (filtrage des messages qui ont déjà été filtrés).

> [!NOTE]
> Cette étape est explicitement requise si votre service de protection actuel fournit l’habillage de liens, mais que vous souhaitez piloter Coffre de liens. Le double habillage de liens n’est pas pris en charge.

## <a name="step-3-tune-spoof-intelligence"></a>Étape 3 : Régler la veille contre l’usurpation d’informations

Vérifiez [les](learn-about-spoof-intelligence.md) informations sur l’usurpation d’informations sur l’usurpation d’informations pour voir ce qui est autorisé ou bloqué comme usurpation d’informations, et pour déterminer si vous devez remplacer le verdict du système pour l’usurpation d’informations. Certaines sources de vos e-mails critiques peuvent avoir des enregistrements d’authentification de courrier électronique configurés de manière incorrecte dans DNS (SPF, DKIM et DMARC) et vous pouvez utiliser des remplacements dans votre service de protection existant pour masquer leurs problèmes de domaine.

La veille contre l’usurpation d’identité peut envoyer des messages électroniques à partir de domaines sans enregistrements d’authentification de courrier appropriés dans DNS, mais la fonctionnalité a parfois besoin d’aide pour distinguer une bonne usurpation d’identité de l’usurpation d’identité. Concentrez-vous sur les types de sources de messages suivants :

- Sources de messages en dehors des plages d’adresses IP définies dans [le filtrage amélioré pour les connecteurs.](/exchange/mail-flow-best-practices/use-connectors-to-configure-mail-flow/enhanced-filtering-for-connectors)
- Sources de messages qui ont le plus grand nombre de messages.
- Sources de messages qui ont l’impact le plus élevé sur votre organisation.

La veille contre l’usurpation d’informations se réglera une fois que vous aurez configuré les soumissions d’utilisateurs, il n’est donc pas nécessaire de s’en occuper.

## <a name="step-4-tune-impersonation-protection-and-mailbox-intelligence"></a>Étape 4 : Régler la protection contre l’emprunt d’identité et l’intelligence des boîtes aux lettres

Une fois que vous avez eu suffisamment de temps pour observer les résultats de la protection contre **l’emprunt d’identité** dans Ne pas appliquer de mode d’action, vous pouvez activer individuellement chaque action de protection contre l’emprunt d’identité dans les stratégies anti-hameçonnage :

- Protection contre l’usurpation d’identité d’utilisateur **: mettre en quarantaine le message** pour Standard et Strict.
- Protection contre l’emprunt d’identité de domaine **: mettre en quarantaine le message** pour Standard et Strict.
- Protection de l’intelligence des boîtes aux lettres : déplacer le message vers les **dossiers Courrier indésirable** des destinataires pour Standard ; **Mettre le message en quarantaine** pour Strict.

Plus vous surveillez les résultats de la protection contre l’emprunt d’identité sans agir sur les messages, plus vous devez identifier les données qui peuvent être requises. Envisagez d’utiliser un délai entre chaque protection qui est suffisamment significative pour permettre l’observation et l’ajustement.

> [!NOTE]
> Il est important d’assurer une surveillance et un réglage fréquents et continus de ces protections. Si vous suspectez un faux positif, examinez la cause et utilisez les remplacements uniquement si nécessaire et uniquement pour la fonctionnalité de détection qui l’exige.

### <a name="tune-mailbox-intelligence"></a>Régler l’intelligence des boîtes aux lettres

Bien que la veille de boîte aux lettres ait été configurée pour ne prendre aucune mesure sur les messages qui ont été déterminés comme des [tentatives](impersonation-insight.md)d’emprunt d’identité, elle a été en cours et a appris les modèles d’envoi et de réception des messages électroniques des utilisateurs pilotes. Si un utilisateur externe est en contact avec l’un de vos utilisateurs pilotes, les messages de cet utilisateur externe ne sont pas identifiés comme des tentatives d’emprunt d’identité par l’intelligence des boîtes aux lettres (réduisant ainsi les faux positifs).

Lorsque vous êtes prêt, faites les étapes suivantes pour autoriser l’intelligence des boîtes aux lettres à agir sur les messages détectés comme des tentatives d’emprunt d’identité :

- Dans la stratégie anti-hameçonnage avec les paramètres  de protection standard, modifiez la valeur si l’intelligence de boîte aux lettres détecte un utilisateur dont l’identité est usurpée pour déplacer le message vers les dossiers Courrier indésirable des **destinataires.**

- Dans la stratégie anti-hameçonnage avec les paramètres de protection strict, modifiez la valeur de **Si** l’intelligence de boîte aux lettres détecte et usurpe l’identité de l’utilisateur pour mettre **le message en quarantaine.**

Pour modifier les stratégies, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Après avoir observé les résultats et effectué des ajustements, passer à la section suivante pour mettre en quarantaine les messages détectés par l’emprunt d’identité d’utilisateur.

### <a name="tune-user-impersonation-protection"></a>Régler la protection contre l’emprunt d’identité d’utilisateur

Dans vos deux stratégies anti-hameçonnage basées sur les paramètres Standard et Strict, modifiez la valeur si le **message** est détecté comme un utilisateur dont l’identité est usurpée pour mettre le **message** en quarantaine.

Vérifiez [l’aperçu de l’emprunt](impersonation-insight.md) d’identité pour voir ce qui est bloqué en tant que tentatives d’emprunt d’identité d’utilisateur.

Pour modifier les stratégies, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Après avoir observé les résultats et effectué des ajustements, passer à la section suivante pour mettre en quarantaine les messages détectés par l’emprunt d’identité de domaine.

### <a name="tune-domain-impersonation-protection"></a>Régler la protection contre l’emprunt d’identité de domaine

Dans vos deux stratégies anti-hameçonnage basées sur les paramètres Standard et Strict, modifiez la valeur si le **message** est détecté comme un domaine dont l’identité est usurpée pour mettre le message en **quarantaine.**

Vérifiez [l’aperçu de l’emprunt](impersonation-insight.md) d’identité pour voir ce qui est bloqué en tant que tentatives d’emprunt d’identité de domaine.

Pour modifier les stratégies, voir [Configurer des stratégies anti-hameçonnage dans Defender pour Office 365](configure-mdo-anti-phishing-policies.md).

Observez les résultats et ajustez-les si nécessaire.

## <a name="step-5-use-data-from-user-submissions-to-measure-and-adjust"></a>Étape 5 : Utiliser les données des soumissions d’utilisateurs pour mesurer et ajuster

Comme vos utilisateurs pilotes signalent des faux positifs et des faux négatifs, les messages s’affichent sur la [page Soumissions du portail Microsoft 365 Defender.](admin-submission.md) Vous pouvez signaler les messages non identifiés à Microsoft pour analyse et utiliser les informations pour ajuster les paramètres et les exceptions dans vos polices pilotes si nécessaire.

Utilisez les fonctionnalités suivantes pour surveiller et itérer les paramètres de protection dans Defender pour Office 365 :

- [Mise en quarantaine](manage-quarantined-messages-and-files.md)
- [Threat Explorer](email-security-in-microsoft-defender.md)
- [Rapports de sécurité de messagerie](view-email-security-reports.md)
- [Rapports Defender for Office 365](view-reports-for-mdo.md)
- [Informations sur le flux de messagerie](/exchange/monitoring/mail-flow-insights/mail-flow-insights)
- [Rapports de flux de messagerie](/exchange/monitoring/mail-flow-reports/mail-flow-reports)

Si votre organisation utilise un service tiers pour les rapports utilisateur, vous pouvez intégrer ces données dans votre boucle de commentaires.

## <a name="step-6-optional-add-more-users-to-your-pilot-and-iterate"></a>Étape 6 : (Facultatif) Ajouter d’autres utilisateurs à votre projet pilote et itérer

Lorsque vous trouvez et corrigez des problèmes, vous pouvez ajouter d’autres utilisateurs aux groupes pilotes (et en conséquence exempter ces nouveaux utilisateurs pilotes de l’analyse par votre service de protection existant, le cas échéant). Plus vous faites de tests maintenant, moins vous devrez gérer de problèmes d’utilisateur par la suite. Cette approche « cascade » permet d’ajuster les équipes de sécurité à des parties plus importantes de l’organisation et de s’adapter aux nouveaux outils et processus.

- Microsoft 365 génère des alertes lorsque les messages de hameçonnage à haut niveau de confiance sont autorisés par les stratégies organisationnelles. Pour identifier ces messages, vous avez les options suivantes :
  - Remplacements dans le rapport d’état [de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)
  - Filtre dans l’Explorateur de menaces pour identifier les messages.
  - Filtre dans la recherche avancée pour identifier les messages.

  Signalez les faux positifs à Microsoft dès que possible via les soumissions d’administrateurs, utilisez la fonctionnalité Liste d’adresses client [autoriser/bloquer](tenant-allow-block-list.md) pour configurer des remplacements sécurisés pour ces faux positifs.

- Il est également bon d’examiner les remplacements inutiles. En d’autres termes, regardez les verdicts que Microsoft 365 auraient fournis sur les messages. Si Microsoft365 a rendu le verdict correct, le besoin de remplacement est considérablement réduit ou éliminé.

## <a name="step-7-extend-microsoft-365-protection-to-all-users-and-turn-off-the-scl-1-mail-flow-rule"></a>Étape 7 : étendre Microsoft 365 protection à tous les utilisateurs et désactiver la règle de flux de messagerie SCL=-1

Faites les étapes de cette section lorsque vous êtes prêt à changer vos enregistrements MX pour qu’ils pointent vers Microsoft 365.

1. Étendre les stratégies pilotes à l’ensemble de l’organisation. Fondamentalement, il existe différentes façons de le faire :
   - Utilisez [des stratégies de sécurité](preset-security-policies.md) prédéfines et divisez vos utilisateurs entre le profil de protection standard et le profil de protection stricte (assurez-vous que tout le monde est couvert). Les stratégies de sécurité prédéfines sont appliquées avant les stratégies personnalisées que vous avez créées ou les stratégies par défaut. Vous pouvez désactiver vos stratégies pilotes sans les supprimer.

     L’inconvénient des stratégies de sécurité prédéfines est que vous ne pouvez pas modifier la plupart des paramètres importants après les avoir créés.

   - Modifiez l’étendue des stratégies que vous avez créées et ajustées pendant le projet pilote pour inclure tous les utilisateurs (par exemple, tous les destinataires dans tous les domaines). N’oubliez pas que si plusieurs stratégies du même type (par exemple, des stratégies anti-hameçonnage) s’appliquent au même utilisateur (individuellement, par appartenance au groupe ou domaine de messagerie), seuls les paramètres de la stratégie ayant la priorité la plus élevée (numéro de priorité le plus bas) sont appliqués et le traitement s’arrête pour ce type de stratégie.

2. Désactiver la règle de flux de messagerie SCL=-1 (vous pouvez la désactiver sans la supprimer).

3. Vérifiez que les modifications précédentes ont pris effet et que Defender pour Office 365 est désormais correctement activé pour tous les utilisateurs. À ce stade, toutes les fonctionnalités de protection de Defender pour Office 365 sont désormais autorisées à agir sur le courrier électronique pour tous les destinataires, mais ce courrier a déjà été analysé par votre service de protection existant.

Vous pouvez suspendre à ce stade pour l’enregistrement et le réglage des données à plus grande échelle.

## <a name="step-8-switch-your-mx-records"></a>Étape 8 : Changer vos enregistrements MX

> [!NOTE]
>
> - Lorsque vous basculez l’enregistrement MX de votre domaine, la propagation des modifications sur Internet peut prendre jusqu’à 48 heures.
>
> - Nous vous recommandons de réduire la valeur TTL de vos enregistrements DNS pour permettre une réponse plus rapide et une possible récupération (si nécessaire). Vous pouvez revenir à la valeur TTL d’origine une fois le basculement terminé et vérifié.
>
> - Vous devez envisager de commencer par modifier les domaines qui sont utilisés moins fréquemment. Vous pouvez suspendre et surveiller avant de passer à des domaines plus importants. Toutefois, même si vous le faites, vous devez vous assurer que tous les utilisateurs et domaines sont couverts par les stratégies, car les domaines SMTP secondaires sont résolus en domaines principaux avant l’application de stratégie.
>   
> - Plusieurs enregistrements MX pour un seul domaine fonctionnent techniquement, ce qui vous permet d’avoir un routage fractioné, à condition que vous suiviez toutes les instructions de cet article. Plus précisément, vous devez vous assurer que les stratégies sont appliquées à tous les utilisateurs, que la règle de flux de messagerie SCL=-1 est appliquée uniquement aux messages qui transitent par votre service de protection existant, comme décrit à l’étape d’installation 3 : Gérer ou créer la règle de flux de messagerie [SCL=-1](migrate-to-defender-for-office-365-setup.md#step-3-maintain-or-create-the-scl-1-mail-flow-rule). Toutefois, cette configuration introduit un comportement qui rend la résolution des problèmes beaucoup plus difficile, et par conséquent, nous ne le recommandons généralement pas, en particulier pour des périodes de temps prolongées.
>
> - Avant de changer vos enregistrements MX, vérifiez que les paramètres suivants ne sont pas activés sur le connecteur entrant du service de protection vers Microsoft 365. En règle générale, un ou plusieurs des paramètres suivants sont configurés pour le connecteur :
>
>   - et exiger que le nom du sujet sur le certificat que le partenaire utilise pour s’authentifier **auprès de Office 365 corresponde** à ce nom de domaine (*RestrictDomainsToCertificate*)
>   - **Rejeter les messages électroniques s’ils ne sont pas** envoyés à partir de cette plage d’adresses IP (*RestrictDomainsToIPAddresses*)
>
>   Si le type de connecteur est **Partenaire** et que l’un de ces paramètres est allumé, la remise du courrier à vos domaines échouera après le basculement de vos enregistrements MX. Vous devez désactiver ces paramètres avant de continuer. Si le connecteur est un connecteur local utilisé pour l’hybride, vous n’avez pas besoin de modifier le connecteur local. Toutefois, vous pouvez toujours vérifier la présence d’un **connecteur** partenaire.
>   
> - Si votre passerelle de messagerie actuelle fournit également la validation des destinataires, vous pouvez vérifier que le domaine est configuré comme faisant autorité dans Microsoft 365. [](/exchange/mail-flow-best-practices/manage-accepted-domains/manage-accepted-domains) Cela permet d’éviter les messages de non-rebond inutiles.

Lorsque vous êtes prêt, basculez l’enregistrement MX de vos domaines. Vous pouvez migrer tous vos domaines en même temps. Sinon, vous pouvez d’abord migrer les domaines moins fréquemment utilisés, puis migrer les autres ultérieurement.

N’hésitez pas à suspendre et évaluer ici à tout moment. Mais n’oubliez pas : une fois que vous avez éteint la règle de flux de messagerie SCL=-1, les utilisateurs peuvent avoir deux expériences différentes pour vérifier les faux positifs. Plus vite vous pourrez fournir une expérience unique et cohérente, plus vos utilisateurs et vos équipes de service d’aide seront satisfaits lorsqu’ils devront résoudre les problèmes d’un message manquant.

## <a name="next-steps"></a>Étapes suivantes

Félicitations ! Vous avez terminé votre [migration vers Microsoft Defender pour Office 365](migrate-to-defender-for-office-365.md#the-migration-process)! Étant donné que vous avez suivi les étapes de ce guide de migration, les premiers jours où le courrier est remis directement dans Microsoft 365 doivent être beaucoup plus fluides.

Maintenant, vous commencez le fonctionnement normal et la maintenance de Defender pour Office 365. Surveillez et surveillez les problèmes semblables à ceux que vous avez expérimentés au cours du projet pilote, mais à plus grande échelle. Les [informations sur l’usurpation](learn-about-spoof-intelligence.md) d’identité et l’emprunt d’identité seront très utiles, mais envisagez de rendre les activités suivantes une occurrence régulière : [](impersonation-insight.md)

- Examinez les soumissions d’utilisateurs, en [particulier les messages de hameçonnage signalés par l’utilisateur.](/microsoft-365/security/office-365-security/automated-investigation-response-office.md#example-a-user-reported-phish-message-launches-an-investigation-playbook)
- Passer en revue les remplacements dans le rapport [d’état de la protection contre les menaces.](view-email-security-reports.md#threat-protection-status-report)
- Utilisez [des requêtes de recherche](/microsoft-365/security/defender/advanced-hunting-example) avancée pour rechercher des opportunités de réglage et des messages à risque.
